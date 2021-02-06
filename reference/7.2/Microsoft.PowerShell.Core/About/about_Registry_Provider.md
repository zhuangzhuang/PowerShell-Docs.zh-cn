---
description: 注册表
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Registry 提供程序
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598859"
---
# <a name="registry-provider"></a>注册表提供程序

## <a name="provider-name"></a>提供程序名称

注册表

## <a name="drives"></a>驱动器

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>功能

**ShouldProcess**、 **UseTransactions**

## <a name="short-description"></a>简短说明

提供对 PowerShell 中的注册表项、条目和值的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **注册表** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的注册表项、条目和值。

**注册表** 驱动器是包含计算机上的注册表项和子项的分层命名空间。 注册表条目和注册表值不是该层次结构的组成部分。 而是每个注册表项的属性。

**注册表** 提供程序支持以下 cmdlet，本文将对此进行介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

注册表项表示为 [Microsoft. RegistryKey](/dotnet/api/microsoft.win32.registrykey) 类的实例。 注册表项表示为 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 类的实例。

## <a name="navigating-the-registry-drives"></a>导航注册表驱动器

**注册表** 提供程序将其数据存储公开为两个默认驱动器。 注册表位置 HKEY_LOCAL_MACHINE 映射到 `HKLM:` 驱动器，HKEY_CURRENT_USER 映射到 `HKCU:` 驱动器。 若要使用注册表，可以使用以下命令将位置更改为 `HKLM:` 驱动器。

```powershell
Set-Location HKLM:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

还可以从任何其他 PowerShell 驱动器使用 **注册表** 提供程序。 若要从其他位置引用注册表项，请在路径中使用驱动器名称 (`HKLM:` ， `HKCU:`) 。 使用反斜杠 (\\) 或正斜杠 (/) 来指示 **注册表** 驱动器的级别。

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [集位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名， `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

最后一个示例显示了另一种可以用来导航 **注册表** 提供程序的路径语法。 此语法使用提供程序名称，后跟两个冒号 `::` 。 此语法允许使用完整的 HIVE 名称，而不是映射的驱动器名称 `HKLM` 。

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>显示注册表项的内容

注册表分为多个键、子项和项。 有关注册表结构的详细信息，请参阅 [注册表的结构](/windows/desktop/sysinfo/structure-of-the-registry)。

在 **注册表** 驱动器中，每个密钥都是一个容器。 键可以包含任意数量的键。 具有父键的注册表项称为 "子项"。 你可以使用 `Get-ChildItem` 查看注册表项并 `Set-Location` 导航到密钥路径。

注册表值是注册表项的属性。 在 **注册表** 驱动器中，它们被称为 " **项目属性**"。 注册表项可以同时具有子键和项属性。

在此示例中，显示了和之间的差异 `Get-Item` `Get-ChildItem` 。 当你 `Get-Item` 在 "后台处理程序" 注册表项上使用时，你可以查看其属性。

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

每个注册表项也可以具有子项。 使用 `Get-Item` 注册表项时，不显示子项。 该 `Get-ChildItem` cmdlet 将显示 "后台处理程序" 键的子项，其中包括每个子项的属性。 使用时，不会显示父键属性 `Get-ChildItem` 。

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

此 `Get-Item` cmdlet 还可用于当前位置。 下面的示例导航到 "后台处理程序" 注册表项并获取项属性。
点 `.` 用于指示当前位置。

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

有关本部分中所述 cmdlet 的详细信息，请参阅以下文章。

-[获取项](xref:Microsoft.PowerShell.Management.Get-Item) 
-[Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>查看注册表项值

注册表项值存储为每个注册表项的属性。 `Get-ItemProperty`Cmdlet 将使用指定的名称查看注册表项属性。 结果为 **PSCustomObject** ，其中包含指定的属性。

下面的示例使用 `Get-ItemProperty` cmdlet 查看所有属性。 如果将生成的对象存储在变量中，则可以访问所需的属性值。

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

指定参数的值 `-Name` 会选择指定的属性，并返回 **PSCustomObject**。  下面的示例演示使用参数时的输出差异 `-Name` 。

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

从 PowerShell 5.0 开始， `Get-ItemPropertyValue` cmdlet 仅返回指定属性的值。

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。

- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>更改注册表项值

`Set-ItemProperty`Cmdlet 将设置注册表项的属性。 下面的示例使用将 `Set-ItemProperty` 后台处理程序服务启动类型更改为 "手动"。 该示例使用 cmdlet 将 **StartType** 更改回 *自动* `Set-Service` 。

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

每个注册表项都有一个 *默认* 值。 您可以使用或更改注册表项的 *默认* 值 `Set-Item` `Set-ItemProperty` 。

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>创建注册表项和值

该 `New-Item` cmdlet 将创建具有你提供的名称的注册表项。
你还可以使用 `mkdir` 函数 `New-Item` 在内部调用 cmdlet。

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

可以使用 `New-ItemProperty` cmdlet 在指定的注册表项中创建值。 下面的示例在 ContosoCompany 注册表项上创建新的 DWORD 值。

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> 有关其他允许的类型值，请查看本文中的动态参数部分。

有关详细的 cmdlet 用法，请参阅 [set-itemproperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)。

## <a name="copying-registry-keys-and-values"></a>复制注册表项和值

在 **注册表** 提供程序中，使用 `Copy-Item` cmdlet 复制注册表项和值。 使用 `Copy-ItemProperty` cmdlet 仅复制注册表值。
以下命令将 "Contoso" 注册表项及其属性复制到指定位置 "HKLM： \ Software\Fabrikam"。

`Copy-Item` 如果目标项不存在，则创建它。 如果目标项存在，则会将源键的 `Copy-Item` 副本创建为子项， (目标键的子项) 。

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

以下命令使用 cmdlet 将 " `Copy-ItemProperty` Server" 值从 "Contoso" 密钥复制到 "Fabrikam" 密钥。

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。

- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>移动注册表项和值

`Move-Item`和 `Move-ItemProperty` cmdlet 的行为类似于其 "复制" 对应项。 如果目标存在，则 `Move-Item` 将源键移动到目标项的下方。 如果目标项不存在，则会将源键移动到目标路径。

以下命令将 "Contoso" 键移动到路径 "HKLM： \ SOFTWARE\Fabrikam"。

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

此命令将所有属性从 "HKLM： \ SOFTWARE\ContosoCompany" 移动到 "HKLM： \ SOFTWARE\Fabrikam"。

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。

- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>重命名注册表项和值

你可以像对文件和文件夹一样重命名注册表项和值。
`Rename-Item` 重命名注册表项，同时 `Rename-ItemProperty` 重命名注册表值。

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>更改安全描述符

你可以使用和 cmdlet 限制对注册表项的访问 `Get-Acl` `Set-Acl` 。 下面的示例将具有 "完全控制" 的新用户添加到 "HKLM： \ SOFTWARE\Contoso" 注册表项。

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。

- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>删除和清除注册表项和值

您可以通过使用 **Remove item** 删除包含的项，但如果项包含任何其他内容，系统将提示您确认删除。 以下示例尝试删除密钥 "HKLM： \ SOFTWARE\Contoso"。

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

若要在不提示的情况下删除包含的项，请指定 `-Recurse` 参数。

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

如果要删除 "HKLM： \ SOFTWARE\Contoso" 内的所有项，而不是 "HKLM： \ SOFTWARE\Contoso" 本身，请使用后面跟有通配符的尾随反斜杠 `\` 。

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

此命令从 "HKLM： \ SOFTWARE\Contoso" 注册表项中删除 "ContosoTest" 注册表值。

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` 清除所有注册表项的注册表值。 下面的示例将清除 "HKLM： \ SOFTWARE\Contoso" 注册表项中的所有值。 若要仅清除特定属性，请使用 `Clear-ItemProperty` 。

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。

### <a name="type-microsoftwin32registryvaluekind"></a>键入 <RegistryValueKind>

建立或更改注册表值的数据类型。 默认值为 `String` (REG_SZ) 。

此参数可用于 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet。 此外，还可以在注册表驱动器中用于 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet，但它不起作用。

|值 | 说明 |
| ---- | ----------- |
| `String` | 指定以 null 结尾的字符串。 等效于 REG_SZ。 |
| `ExpandString` | 指定以 null 结尾的字符串，该字符串包含未展开的 |
|                | 引用扩展时扩展的环境变量 |
|                | 检索值。 等效于 REG_EXPAND_SZ。 |
| `Binary` | 指定采用任意格式的二进制数据。 等效于 REG_BINARY。 |
| `DWord` | 指定一个 32 位的二进制数字。 等效于 REG_DWORD。 |
| `MultiString` | 指定以 null 结尾的字符串的数组，由终止 |
|               | 两个 null 字符。 等效于 REG_MULTI_SZ。 |
| `QWord` | 指定一个 64 位的二进制数字。 等效于 REG_QWORD。 |
| `Unknown` | 指示不受支持的注册表数据类型，例如 |
|           | REG_RESOURCE_LIST。 |

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>使用管道

提供程序 cmdlet 接受管道输入。 可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。 若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。

## <a name="getting-help"></a>获取帮助

从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。

若要获取针对文件系统驱动器进行自定义的帮助主题，请 `Get-Help` 在文件系统驱动器中运行命令，或使用 **Path** 参数指定文件系统驱动器。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>请参阅

 [about_Providers](../About/about_Providers.md)

