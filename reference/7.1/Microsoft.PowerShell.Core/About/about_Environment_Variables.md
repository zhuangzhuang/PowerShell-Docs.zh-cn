---
description: 介绍如何在 PowerShell 中访问 Windows 环境变量。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 4b5894822f4436f127ed4789fd8008a0e7f2f2df
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584648"
---
# <a name="about-environment-variables"></a>关于环境变量

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中访问 Windows 环境变量。

## <a name="long-description"></a>详细说明

环境变量存储有关操作系统环境的信息。 此信息包括各种详细信息，如操作系统路径、操作系统使用的处理器数量以及临时文件夹的位置。

环境变量存储操作系统和其他程序使用的数据。 例如， `WINDIR` 环境变量包含 Windows 安装目录的位置。 程序可以查询此变量的值，以确定 Windows 操作系统文件所在的位置。

PowerShell 可以访问和管理任何受支持的操作系统平台中的环境变量。 PowerShell 环境提供程序可以轻松地查看和更改环境变量，从而简化了此过程。

与 PowerShell 中其他类型的变量不同，环境变量由子进程继承，如本地后台作业和模块成员运行的会话。 这使得环境变量非常适合存储在父进程和子进程中所需的值。

## <a name="using-and-changing-environment-variables"></a>使用和更改环境变量

在 Windows 上，可以在三个作用域中定义环境变量：

- 计算机 (或系统) 范围
- 用户范围
- 进程范围

_进程_ 范围包含当前进程或 PowerShell 会话中可用的环境变量。 此变量列表继承自父进程，并由 _计算机_ 和 _用户_ 作用域中的变量构造。 基于 Unix 的平台仅具有 _进程_ 范围。

可以通过将变量语法与环境提供程序结合使用来显示和更改环境变量的值，而无需使用 cmdlet。 若要显示环境变量的值，请使用以下语法：

```
$Env:<variable-name>
```

例如，若要显示环境变量的值 `WINDIR` ，请在 PowerShell 命令提示符下键入以下命令：

```powershell
$Env:windir
```

在此语法中，美元符号 (`$`) 表示一个变量， () 的驱动器名称 `Env:` 表示一个环境变量后跟变量名称 (`windir`) 。

更改 PowerShell 中的环境变量时，更改只会影响当前会话。 此行为类似于 `Set` Windows 命令行界面中的命令行为和 `Setenv` 基于 UNIX 的环境中的命令。 若要更改计算机或用户作用域中的值，则必须使用 **system.web** 类的方法。

若要更改计算机范围的变量，还必须具有权限。 如果尝试在没有足够权限的情况下更改值，则该命令将失败，并且 PowerShell 将显示错误。

您可以更改变量的值，而无需使用以下语法：

```powershell
$Env:<variable-name> = "<new-value>"
```

例如，若要将附加 `;c:\temp` 到 `Path` 环境变量的值，请使用以下语法：

```powershell
$Env:Path += ";c:\temp"
```

在 Linux 或 macOS 上，命令中的冒号 (`:`) 将新路径与列表中其前面的路径分隔开。

```powershell
$Env:PATH += ":/usr/local/temp"
```

你还可以使用项 cmdlet （如 `Set-Item` 、和） `Remove-Item` `Copy-Item` 来更改环境变量的值。 例如，若要使用 `Set-Item` cmdlet 追加 `;c:\temp` 到 `Path` 环境变量的值，请使用以下语法：

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

在此命令中，值括在括号中，以便将其解释为一个单元。

## <a name="environment-variables-that-store-preferences"></a>存储首选项的环境变量

PowerShell 功能可以使用环境变量来存储用户首选项。
这些变量的工作方式类似于首选项变量，但它们由创建它们的会话的子会话继承。 有关首选项变量的详细信息，请参阅 [about_preference_variables](about_Preference_Variables.md)。

存储首选项的环境变量包括：

- PSExecutionPolicyPreference

  存储为当前会话设置的执行策略。 仅当为单一会话设置执行策略时，才存在此环境变量。
  可以通过两种不同的方式来实现此目的。

  - 使用 **set-executionpolicy** 参数从命令行启动会话，以便为会话设置执行策略。

  - 使用 `Set-ExecutionPolicy` cmdlet。 使用值为 "Process" 的作用域参数。

    有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

- PSModuleAnalysisCachePath

  PowerShell 提供对文件的控制，该文件用于缓存有关模块及其 cmdlet 的数据。 缓存将在启动时读取，并在导入模块后在后台线程上写入。

  缓存的默认位置为：

  - Windows PowerShell 5.1：`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - PowerShell 6.0 和更高版本： `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - 非 Windows 默认值： `~/.cache/powershell`

  缓存的默认文件名为 `ModuleAnalysisCache` 。 如果安装了多个 PowerShell 实例，则文件名包含十六进制后缀，以便每次安装时都有唯一的文件名。

  > [!NOTE]
  > 如果命令发现不能正常运行，例如 Intellisense 显示了不存在的命令，则可以删除缓存文件。 下次启动 PowerShell 时，将重新创建缓存。

  若要更改缓存的默认位置，请在启动 PowerShell 之前设置环境变量。 对此环境变量所做的更改只会影响子进程。 值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。

  若要禁用文件缓存，请将此值设置为无效位置，例如：

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  这会设置 **NUL** 设备的路径。 PowerShell 不能写入路径，但不会返回任何错误。 您可以查看使用跟踪器报告的错误：

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  编写模块分析缓存时，PowerShell 会检查不再存在的模块，以避免不必要的大型缓存。 有时不需要这些检查，在这种情况下，您可以通过将此环境变量值设置为来关闭它们 `1` 。

  设置此环境变量将在当前进程中立即生效。

- PSModulePath

  `$env:PSModulePath`环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。

  默认情况下，分配到的有效位置 `$env:PSModulePath` 为：

  - 系统范围的位置：这些文件夹包含 PowerShell 附带的模块。 模块存储在 `$PSHOME\Modules` 位置。 此外，这是安装 Windows 管理模块的位置。

  - 用户安装的模块：这些是用户安装的模块。
    `Install-Module` 具有 **作用域** 参数，该参数可用于指定是为当前用户还是为所有用户安装该模块。 有关详细信息，请参阅 [Install-Module](xref:PowerShellGet.Install-Module)。

    - 在 Windows 上，特定于用户的 **CurrentUser** 范围是 `$HOME\Documents\PowerShell\Modules` 文件夹。 **AllUsers** 作用域的位置为 `$env:ProgramFiles\PowerShell\Modules` 。
    - 在非 Windows 系统上，特定于用户的 **CurrentUser** 范围是 `$HOME/.local/share/powershell/Modules` 文件夹。 **AllUsers** 作用域的位置为 `/usr/local/share/powershell/Modules` 。

  此外，在其他目录中安装模块的安装程序（如 Program Files 目录）可以将它们的位置附加到的值 `$env:PSModulePath` 。

  有关详细信息，请参阅 [about_PSModulePath](about_PSModulePath.md)。

## <a name="managing-environment-variables"></a>管理环境变量

PowerShell 提供了几种不同的方法来管理环境变量。

- 环境提供程序驱动器
- 项 cmdlet
- .NET **system.web** 类
- 在 Windows 上，系统控制面板

### <a name="using-the-environment-provider"></a>使用环境提供程序

每个环境变量由 **DictionaryEntry** 类的实例表示。 在每个 **DictionaryEntry** 对象中，环境变量的名称是字典键。 变量的值是字典值。

若要在 PowerShell 中显示表示环境变量的对象的属性和方法，请使用 `Get-Member` cmdlet。 例如，若要显示驱动器中所有对象的方法和属性 `Env:` ，请键入：

```powershell
Get-Item -Path Env:* | Get-Member
```

PowerShell 环境提供程序允许你访问 PowerShell 驱动器中的环境变量， (`Env:` 驱动器) 。 此驱动器非常类似于文件系统驱动器。 若要前往 `Env:` 驱动器，请键入：

```powershell
Set-Location Env:
```

使用 Content cmdlet 获取或设置环境变量的值。

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

你可以 `Env:` 从任何其他 PowerShell 驱动器查看驱动器中的环境变量，并且可以进入 `Env:` 驱动器以查看和更改环境变量。

### <a name="using-item-cmdlets"></a>使用项 cmdlet

引用环境变量时，键入 `Env:` 驱动器名称，后跟变量的名称。 例如，若要显示环境变量的值 `COMPUTERNAME` ，请键入：

```powershell
Get-ChildItem Env:Computername
```

若要显示所有环境变量的值，请键入：

```powershell
Get-ChildItem Env:
```

由于环境变量没有子项，因此和的输出 `Get-Item` `Get-ChildItem` 是相同的。

默认情况下，PowerShell 按其检索环境变量的顺序显示这些环境变量。 若要按变量名称对环境变量的列表进行排序，请通过管道将命令的输出传递 `Get-ChildItem` 给 `Sort-Object` cmdlet。 例如，在任何 PowerShell 驱动器上，键入：

```powershell
Get-ChildItem Env: | Sort Name
```

你还可以 `Env:` 使用 cmdlet 进入驱动器 `Set-Location` ：

```powershell
Set-Location Env:
```

如果位于 `Env:` 驱动器中，则可以省略路径中的 `Env:` 驱动器名称。 例如，若要显示所有环境变量，请键入：

```powershell
PS Env:\> Get-ChildItem
```

若要显示 `COMPUTERNAME` 驱动器中变量的值 `Env:` ，请键入：

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>保存对环境变量所做的更改

若要对 Windows 上的环境变量进行持久更改，请使用系统控制面板。 选择 " **高级系统设置**"。 在 " **高级** " 选项卡上，单击 " **环境变量 ...**"。你可以在 **用户** 和 **系统** (计算机) 范围中添加或编辑现有环境变量。 Windows 将这些值写入注册表，以便它们在会话和系统重启之间保持不变。

或者，可以在 PowerShell 配置文件中添加或更改环境变量。 此方法适用于任何受支持平台上的任何版本的 PowerShell。

### <a name="using-systemenvironment-methods"></a>使用 System.object 方法

**System.web** 类提供 **GetEnvironmentVariable** 和 **SetEnvironmentVariable** 方法，使你可以指定变量的作用域。

下面的示例使用 **GetEnvironmentVariable** 方法来获取的计算机设置 `PSModulePath` ，并使用 **SetEnvironmentVariable** 方法将 `C:\Program Files\Fabrikam\Modules` 路径添加到值中。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

有关 **system.web** 类的方法的详细信息，请参阅 [环境方法](/dotnet/api/system.environment)。

## <a name="see-also"></a>另请参阅

- [环境 (提供程序) ](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)

