---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 角色功能
description: 角色功能是一个带 .psrc 扩展名的 PowerShell 数据文件，其中列出了向连接用户提供的所有 cmdlet、函数、提供程序和外部程序。
ms.openlocfilehash: 233d9081f4a8f977f0959addb5573c4566f885d0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92499988"
---
# <a name="jea-role-capabilities"></a>JEA 角色功能

创建 JEA 终结点时，需要定义一个或多个角色功能，它们描述了用户可在 JEA 会话中执行哪些操作。 角色功能是一个带 `.psrc` 扩展名的 PowerShell 数据文件其中列出了向连接用户提供的所有 cmdlet、函数、提供程序和外部程序。

## <a name="determine-which-commands-to-allow"></a>确定要允许的命令

创建角色功能文件时，首先要考虑用户需要访问哪些内容。 此需求收集过程可能需要一段时间，但很必要。 如果用户具有访问权限的 cmdlet 和函数太少，则会阻碍他们完成工作。 如果允许访问的 cmdlet 和函数太多，则用户能够执行比预期多的操作，从而削弱你的安全状况。

你如何执行此过程由你的组织和目标而定。 以下提示可帮助确保你正确选择。

1. **标识** 用户用于完成工作的命令。 这可能需要调查 IT 员工、检查自动化脚本，或者分析 PowerShell 会话脚本和日志。
2. 将命令行工具改为使用 PowerShell 等效工具（若可能），实现最佳的审核和 JEA 自定义体验。 不可将外部程序限制为与本机 PowerShell cmdlet 和 JEA 中的函数一样精细。
3. 将 cmdlet 的范围限制为仅允许特定参数或参数值。 如果用户只该管理系统的一部分，则这尤其重要。
4. 创建自定义函数，替换复杂的命令或很难在 JEA 中进行约束的命令。 封装了复杂命令或应用其他验证逻辑的简单函数可提供额外的掌控力，简化管理员和最终用户的操作。
5. 通过用户或自动化服务测试允许命令的范围列表，并根据需要进行调整。

### <a name="examples-of-potentially-dangerous-commands"></a>可能存在危险的命令示例

有必要仔细选择命令，确保 JEA 终结点不允许用户提升其权限。

> [!IMPORTANT]
> JEA 会话中用户 successCommands 所需的基本信息通常以提升的权限运行。

下表包含在不受约束的状态下允许使用时可能被恶意使用的命令示例。 此列表并非全面详尽，应在开始时谨慎使用。

|                                            风险                                            |                                示例                                |                                                                              相关命令                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 向连接用户授予管理员特权以绕过 JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| 运行任意代码（如恶意软件、攻击或自定义脚本）以绕过保护 | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>创建角色功能文件

可使用 [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile) cmdlet 创建新的 PowerShell 角色功能文件。

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

应编辑生成的角色功能文件，以允许角色所需的命令。 PowerShell 帮助文档包括文件配置方式的多个示例。

### <a name="allowing-powershell-cmdlets-and-functions"></a>允许 PowerShell cmdlet 和函数

若要授权用户运行 PowerShell cmdlet 或函数，请将 cmdlet 或函数名称添加到 VisibleCmdlets 或 VisibleFunctions 字段。 如果不确定命令是 cmdlet 还是函数，可运行 `Get-Command <name>` 并查看输出中的 CommandType 属性。

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

有时，特定 cmdlet 或函数的作用域对用户需求而言过于宽泛。 例如，DNS 管理员可能只需进行访问来重启 DNS 服务。 在多租户环境中，租户可访问自助服务管理工具。 应将租户限制为管理其自己的资源。 对于这些情况，可限制 cmdlet 或函数中公开的参数。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

在更高级的场景中，可能还需要限制用户面向这些参数使用的值。 通过角色功能，可定义一组值，也可定义一种正则表达式模式来确定允许哪些输入。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> 即使限制可用参数，仍始终允许使用[常用 PowerShell 参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)。
> 不可在参数字段中明确列出这些参数。

下表介绍自定义可见 cmdlet 或函数的各种方式。
可在 VisibleCmdlets 字段中将以下任何内容进行组合和配对。

|                                           示例                                           |                                                             使用案例                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` 或 `@{ Name = 'My-Func' }`                                                      | 允许用户运行 `My-Func` 且不限制参数。                                                      |
| `'MyModule\My-Func'`                                                                        | 允许用户通过模块 `MyModule` 运行 `My-Func` 且不限制参数。                           |
| `'My-*'`                                                                                    | 允许用户使用谓词 `My` 运行任意 cmdlet 或函数。                                                                 |
| `'*-Func'`                                                                                  | 允许用户使用名词 `Func` 运行任意 cmdlet 或函数。                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | 允许用户使用 `Param1` 和 `Param2` 参数运行 `My-Func`。 可向参数提供任何值。          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | 允许用户使用 `Param1` 参数运行 `My-Func`。 仅可向该参数提供“Value1”和“Value2”。        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | 允许用户使用 `Param1` 参数运行 `My-Func`。 可向参数提供以“contoso”开头的任意值。 |

> [!WARNING]
> 最佳的安全做法是，建议在定义可见 cmdlet 或函数时不要使用通配符。 相反，应明确列出每个受信任的命令，确保共享同一命名方案的其他命令均未在无意中获得授权。

无法向同一 cmdlet 或函数同时应用 ValidatePattern 和 ValidateSet。

若如此操作，ValidatePattern 会覆盖 ValidateSet。

有关 ValidatePattern 的详细信息，请参阅[“你好，脚本专家”博文](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 正则表达式](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)参考内容。

### <a name="allowing-external-commands-and-powershell-scripts"></a>允许使用外部命令和 PowerShell 脚本

要使用户能在 JEA 会话中运行可执行文件和 PowerShell 脚本 (.ps1)，必须在 VisibleExternalCommands 字段中添加每个程序的完整路径。

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

如果可能，建议使用你授权的任意外部可执行文件的 PowerShell cmdlet 或函数等效项，因为你可控制允许 PowerShell cmdlet 和函数使用哪些参数。

通过很多可执行文件，可读取当前状态，随后再通过提供其他参数来更改它。

例如，考虑使用文件服务器管理员的角色，它可管理系统托管的网络共享。 管理共享的一种方法是使用 `net share`。 但是，允许 net.exe 会带来风险，因为用户可使用该命令获取 `net group Administrators unprivilegedjeauser /add` 的管理员权限。 更安全的选项是允许使用 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)，该命令可实现相同的结果，但范围更受限制。

使外部命令可供用户在 JEA 会话中使用时，始终指定可执行文件的完整路径。 这可防止执行位于系统上其他位置的同名潜在恶意程序。

### <a name="allowing-access-to-powershell-providers"></a>允许访问 PowerShell 提供程序

默认情况下，PowerShell 提供程序均不适用于 JEA 会话。 这可降低向连接用户泄漏敏感信息和配置设置的风险。

必要时，可使用 `VisibleProviders` 命令允许访问 PowerShell 提供程序。 有关提供程序的完整列表，请运行 `Get-PSProvider`。

```powershell
VisibleProviders = 'Registry'
```

对于需要访问文件系统、注册表、证书存储或其他敏感提供程序的简单任务，可考虑编写将代表用户使用提供程序的自定义函数。 JEA 会话中可用的函数、cmdlet 和外部程序所遵循的约束与 JEA 不同。 默认情况下，它们可访问任意提供程序。 如果需要将文件复制到 JEA 终结点或从中复制文件，还可考虑使用[用户驱动器](session-configurations.md#user-drive)。

### <a name="creating-custom-functions"></a>创建自定义函数

可在角色功能文件中创作自定义函数，简化最终用户的复杂任务。 如果需要 cmdlet 参数值的高级验证逻辑时，自定义函数也很有用。 可在 **FunctionDefinitions** 字段中编写简单函数：

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> 不要忘记向 **VisibleFunctions** 字段添加自定义函数的名称，使其可由 JEA 用户运行。

自定义函数的主体（脚本块）在系统的默认语言模式下运行，不受 JEA 的语言约束。 这意味着函数可访问文件系统和注册表，并可运行角色功能文件中隐藏的命令。 请注意避免在使用参数时运行任意代码。 避免将用户输入直接传输到 `Invoke-Expression` 等 cmdlet。

在上例中，可注意到使用的是完全限定的模块名称 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而非速记 `Select-Object`。
角色功能文件中定义的函数仍受限于 JEA 会话的作用域，这包括 JEA 创建用于约束现有命令的代理函数。

默认情况下，`Select-Object` 是所有 JEA 会话中受约束的 cmdlet，不允许选择对象的任意属性。 若要在函数中使用不受约束的 `Select-Object`，必须使用 FQMN 显式请求完整的实现。 通过函数调用 JEA 会话中任何受约束的 cmdlet 时，它都具有相同的约束。 有关详细信息，请参阅 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)。

如果正在编写多个自定义函数，将其放到 PowerShell 脚本模块中可能更方便。 与使用内置模块和第三方模块时一样，可使用 VisibleFunctions 字段使这些函数在 JEA 会话中可见。

为了使 tab 自动补全在 JEA 会话中正常工作，必须在 VisibleFunctions 列表中包含内置函数 `tabexpansion2`。

## <a name="make-the-role-capabilities-available-to-a-configuration"></a>让角色功能可用于配置

在 PowerShell 6 之前的版本中，必须将角色功能文件存储在 PowerShell 模块的“RoleCapabilities”文件夹中，PowerShell 才能找到它。 此模块可存储在 `$env:PSModulePath` 环境变量内附的任何文件夹中，但不得放在 `$env:SystemRoot\System32` 中，也不得放到允许不受信任的用户修改其中文件的文件夹内。

下面的示例在 `$env:ProgramFiles` 路径中创建名为“ContosoJEA”的 PowerShell 脚本模块，用于托管角色功能文件。

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

有关 PowerShell 模块的详细信息，请参阅[了解 PowerShell 模块](/powershell/scripting/developer/windows-powershell)。

自 PowerShell 6 起，RoleDefinitions 属性已添加到会话配置文件中。 借助此属性，可以指定角色定义的角色配置文件的位置。 请参阅 [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile) 中的示例。

## <a name="updating-role-capabilities"></a>更新角色功能

可编辑角色功能文件，以便随时更新设置。 角色功能更新后启动的任意新 JEA 会话均可反映出修订后的功能。

这就是有必要控制角色功能文件夹的访问权限的原因。 只能允许高度受信任的管理员更改角色功能文件。 如果不受信任的用户可更改角色功能文件，则其可轻松向自己授予 cmdlet 访问权限，便于提升自身权限。

对于想要锁定角色功能访问权限的管理员，请确保本地系统具有角色功能文件的访问权限且包含相关模块。

## <a name="how-role-capabilities-are-merged"></a>如何合并角色功能

用户进入 JEA 会话时，获得访问[会话配置文件](session-configurations.md)中所有匹配的角色功能的权限。 JEA 尝试为用户提供所有角色允许的最宽松的命令集。

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets 和 VisibleFunctions

最复杂的合并逻辑会影响 cmdlet 和函数，会在 JEA 中限制其参数和参数值。

规则如下：

1. 如果 cmdlet 仅在一个角色中可见，其对具有任意适用参数约束的用户可见。
2. 如果 cmdlet 在多个角色中可见，并且每个角色在该 cmdlet 上具有相同的约束，则该 cmdlet 对具有这些约束的用户可见。
3. 如果 cmdlet 在多个角色中可见，并且每个角色允许使用一组不同的参数，则该 cmdlet 及其在每个角色中定义的所有参数都对用户可见。
   如果一个角色没有参数约束，则允许使用所有参数。
4. 如果一个角色定义 cmdlet 参数的验证集或验证模式，另一角色允许使用该参数但不约束参数值，则忽略此验证集或验证模式。
5. 如果在多个角色中定义了同一个 cmdlet 参数的验证集，则所有验证集中的所有值均可用。
6. 如果在多个角色中定义了同一个 cmdlet 参数的验证模式，则与任何模式匹配的任何值均可用。
7. 如果在一个或多个角色中定义验证集，在另一角色中定义相同 cmdlet 参数的验证模式，则将忽略应用于剩余验证模式的验证集和规则 (6)。

以下是如何根据这些规则合并角色的示例：

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands、VisibleAliases、VisibleProviders 和 ScriptsToProcess

角色功能文件中的所有其他字段均添加到一组集中，其中包含可允许使用的外部命令、别名、提供程序和启动脚本。 一个角色功能中提供的任何命令、别名、提供程序或脚本均可供 JEA 用户使用。

请务必确保在某角色功能的提供程序和另一角色功能的 cmdlet/函数/命令共同构成的组合集中，禁止用户意外访问系统资源。
例如，如果一个角色允许使用 `Remove-Item` cmdlet，而另一角色允许 `FileSystem` 提供程序，则 JEA 用户可能会删除计算机上的任意文件。 要详细了解如何确定用户的有效权限，可参阅[审核 JEA](audit-and-report.md) 一文。

## <a name="next-steps"></a>后续步骤

[创建会话配置文件](session-configurations.md)
