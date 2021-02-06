---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 1b8164be05f011e13945323a6288426bd2d41183
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2020
ms.locfileid: "99598256"
---
# Import-Module

## 摘要
将模块添加到当前会话。

## SYNTAX

### Name（默认值）

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### UseWindowsPowerShell

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### FullyQualifiedNameAndUseWindowsPowerShell

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### 程序集

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## DESCRIPTION

`Import-Module`Cmdlet 可将一个或多个模块添加到当前会话中。 从 PowerShell 3.0 开始，当你使用模块中的任何命令或提供程序时，已安装的模块将自动导入到会话中。 但是，您仍然可以使用 `Import-Module` 命令导入模块。
您可以使用首选项变量来禁用自动模块导入 `$PSModuleAutoloadingPreference` 。 有关变量的详细信息 `$PSModuleAutoloadingPreference` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

模块是一个包，其中包含可在 PowerShell 中使用的成员。 成员包括 cmdlet、提供程序、脚本、函数、变量和其他工具和文件。 导入模块后，你可以在会话中使用模块成员。 有关模块的详细信息，请参阅 [about_Modules](About/about_Modules.md)。

默认情况下， `Import-Module` 导入模块导出的所有成员，但是可以使用 **Alias**、 **Function**、 **Cmdlet** 和 **Variable** 参数来限制导入的成员。 **NoClobber** 参数阻止 `Import-Module` 导入与当前会话中的成员具有相同名称的成员。

`Import-Module` 仅将模块导入到当前会话中。 若要将模块导入到每个新会话中，请将 `Import-Module` 命令添加到 PowerShell 配置文件。 有关配置文件的详细信息，请参阅 [about_Profiles](About/about_Profiles.md)。

你可以通过在远程计算机上创建 **PSSession** 来管理启用了 PowerShell 远程处理的远程 Windows 计算机。 然后，使用的 **PSSession** 参数 `Import-Module` 导入远程计算机上安装的模块。 在当前会话中使用导入的命令时，命令将在远程计算机上隐式运行。

从 Windows PowerShell 3.0 开始，你可以使用 `Import-Module` 导入通用信息模型 (CIM) 模块。 CIM 模块在 Cmdlet 定义 XML (CDXML) 文件中定义 cmdlet。 此功能允许你使用在非托管代码程序集中实现的 cmdlet，如用 c + + 编写的程序集。

对于未启用 PowerShell 远程处理的远程计算机，包括未运行 Windows 操作系统的计算机，可以使用的 **CIMSession** 参数 `Import-Module` 从远程计算机导入 CIM 模块。 导入的命令将在远程计算机上隐式运行。 **CIMSession** 是与远程计算机上的 WMI) Windows Management Instrumentation (的连接。

## 示例

### 示例1：将模块的成员导入到当前会话中

此示例将 **PSDiagnostics** 模块的成员导入到当前会话中。

```powershell
Import-Module -Name PSDiagnostics
```

### 示例2：导入模块路径指定的所有模块

此示例将环境变量指定的路径中的所有可用模块导入 `$env:PSModulePath` 到当前会话中。

```powershell
Get-Module -ListAvailable | Import-Module
```

### 示例3：将多个模块的成员导入到当前会话中

此示例将 **PSDiagnostics** 和 **Dism** 模块的成员导入到当前会话中。

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

该 `Get-Module` cmdlet 将获取 **PSDiagnostics** 和 **Dism** 模块，并将对象保存在 `$m` 变量中。 当你获取尚未导入到会话中的模块时， **ListAvailable** 参数是必需的。

的 **ModuleInfo** 参数 `Import-Module` 用于将模块导入到当前会话中。

### 示例4：导入路径指定的所有模块

此示例使用显式路径来标识要导入的模块。

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

使用 **Verbose** 参数会导致在 `Import-Module` 加载模块时报告进度。
在导入模块时，如果没有 **Verbose**、 **PassThru** 或 **AsCustomObject** 参数， `Import-Module` 则不会生成任何输出。

### 示例5：限制导入到会话中的模块成员

此示例显示了如何限制导入到会话中的模块成员以及此命令对会话的影响。 **函数** 参数限制从模块导入的成员。 你还可以使用 **别名**、 **变量** 和 **Cmdlet** 参数来限制模块导入的其他成员。

`Get-Module`Cmdlet 可获取表示 **PSDiagnostics** 模块的对象。 **ExportedCmdlets** 属性列出模块导出的所有 cmdlet，即使它们并非全部导入。

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

使用 cmdlet 的 **Module** 参数 `Get-Command` 显示从 **PSDiagnostics** 模块导入的命令。 结果确认只 `Disable-PSTrace` 导入了和 `Enable-PSTrace` cmdlet。

### 示例6：导入模块的成员并添加前缀

此示例将 **PSDiagnostics** 模块导入到当前会话中，将前缀添加到成员名称，然后显示前缀成员的名称。 的 **前缀** 参数 `Import-Module` 将 **x** 前缀添加到从模块导入的所有成员。 前缀仅适用于当前会话中的成员。 它不会更改模块。 **PassThru** 参数返回一个 module 对象，该对象表示导入的模块。

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` 获取已从模块导入的成员。 该输出显示模块成员已正确地添加了前缀。

### 示例7：获取并使用自定义对象

此示例演示如何获取和使用由返回的自定义对象 `Import-Module` 。

自定义对象包括表示每个导入的模块成员的合成成员。 例如，模块中的 cmdlet 和函数将转换为自定义对象的脚本方法。

自定义对象在脚本编写中非常有用。 此外，当多个导入的对象具有相同的名称时，它们也非常有用。 使用对象的脚本方法等效于指定已导入成员的完全限定名称（包括其模块名称）。

**AsCustomObject** 参数只能在导入脚本模块时使用。 使用 `Get-Module` 确定哪些可用模块是脚本模块。

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

`Show-Calendar`脚本模块是使用 **AsCustomObject** 参数导入的，用来请求自定义对象，使用 **PassThru** 参数来返回对象。 生成的自定义对象保存在 `$a` 变量中。

将 `$a` 变量传递给 cmdlet 以 `Get-Member` 显示已保存对象的属性和方法。 输出显示 `Show-Calendar` 脚本方法。

若要调用该 `Show-Calendar` 脚本方法，方法名称必须用引号引起来，因为该名称包含连字符。

### 示例8：将模块导入同一会话

此示例演示如何在将 `Import-Module` 模块重新导入到同一会话中时使用 Force 参数。 **Force** 参数将删除已加载的模块，然后再次导入它。

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

第一个命令将导入 **PSDiagnostics** 模块。 第二个命令将再次导入该模块，这一次使用的是 **Prefix** 参数。

如果没有 **Force** 参数，则会话将包含每个 **PSDiagnostics** cmdlet 的两个副本，一个具有标准名称，另一个带有前缀名称。

### 示例9：运行已由导入的命令隐藏的命令

此示例显示了如何运行由导入的命令隐藏的命令。 **TestModule** 模块包括一个名为的函数，该函数 `Get-Date` 返回年份和年份。

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

第一个 `Get-Date` cmdlet 返回具有当前日期的 **DateTime** 对象。 导入 **TestModule** 模块后， `Get-Date` 返回年份和该年的第几天。

使用的 **all** 参数 `Get-Command` 显示 `Get-Date` 会话中的所有命令。 结果显示会话中有两个 `Get-Date` 命令、 **TestModule** 模块中的一个函数和一个来自 **模块的** cmdlet。

由于函数优先于 cmdlet，因此 `Get-Date` **TestModule** 模块中的函数会运行，而不是 `Get-Date` cmdlet。 若要运行的原始版本 `Get-Date` ，必须用模块名称限定命令名称。

有关 PowerShell 中命令优先级的详细信息，请参阅 [about_Command_Precedence](about/about_Command_Precedence.md)。

### 示例10：导入模块的最低版本

此示例导入 **PowerShellGet** 模块。 它使用的 **MinimumVersion** 参数 `Import-Module` 仅导入2.0.0 或更高版本的模块。

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

你还可以使用 **RequiredVersion** 参数导入特定版本的模块，或者使用关键字的 **module** 和 **version** 参数 `#Requires` 来要求在脚本中使用特定版本的模块。

### 示例11：使用完全限定名称导入

此示例使用 FullyQualifiedName 导入特定版本的模块。

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### 示例12：使用完全限定的路径导入

此示例使用完全限定的路径导入模块的特定版本。

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### 示例13：从远程计算机导入模块

此示例演示如何使用 `Import-Module` cmdlet 从远程计算机导入模块。
此命令使用 PowerShell 的隐式远程处理功能。

从另一个会话导入模块时，你可以使用当前会话中的 cmdlet。
但是，使用这些 cmdlet 的命令将在远程会话中运行。

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` (**PSSession**) 创建到 Server01 计算机的远程会话。 **PSSession** 保存在 `$s` 变量中。

`Get-Module`使用 **PSSession** 参数运行时，将显示 **NetSecurity** 模块已安装并在远程计算机上可用。 此命令等效于使用 `Invoke-Command` cmdlet `Get-Module` 在远程会话中运行命令。 例如： (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

`Import-Module`用 **PSSession** 参数运行时，会将远程计算机中的 **NetSecurity** 模块导入到当前会话中。 `Get-Command`Cmdlet 用于获取以 **get** 开头的命令，并将 **防火墙** 包括在 **NetSecurity** 模块中。 输出确认模块及其 cmdlet 已导入到当前会话中。

接下来，该 `Get-NetFirewallRule` cmdlet 将获取 Server01 计算机上 Windows 远程管理防火墙规则。 这等效于使用 `Invoke-Command` cmdlet `Get-NetFirewallRule` 在远程会话中运行。

### 示例14：在没有 Windows 操作系统的情况下管理远程计算机上的存储

在此示例中，计算机的管理员已安装模块发现 WMI 提供程序，该提供程序允许你使用为提供程序设计的 CIM 命令。

`New-CimSession`Cmdlet 在远程计算机上创建一个名为 RSDGF03 的会话。 会话连接到远程计算机上的 WMI 服务。 CIM 会话保存在 `$cs` 变量中。
`Import-Module`使用中的 CIMSESSION `$cs` 从 RSDGF03 计算机中导入 **存储** CIM 模块。

`Get-Command`Cmdlet 将 `Get-Disk` 在 **存储** 模块中显示该命令。 将 CIM 模块导入到本地会话中时，PowerShell 会将每个命令的 CDXML 文件转换为 PowerShell 脚本，这些脚本在本地会话中显示为函数。

尽管 `Get-Disk` 在本地会话中键入，该 cmdlet 会在从中导入它的远程计算机上隐式运行。 此命令将从远程计算机向本地会话返回对象。

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETERS

### -Alias

指定此 cmdlet 从模块导入到当前会话中的别名。 输入以逗号分隔的别名列表。 允许使用通配符。

在导入模块时，某些模块会自动将选定的别名导出到你的会话中。
此参数允许你在导出的别名中进行选择。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ArgumentList

指定在命令期间传递给脚本模块的参数数组或参数值 `Import-Module` 。 仅当你导入脚本模块时，此参数才有效。

还可以通过别名 **的参数引用** **ArgumentList** 参数。 有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

指示此 cmdlet 返回一个自定义对象，该对象具有表示导入的模块成员的成员。 此参数仅对脚本模块有效。

使用 **AsCustomObject** 参数时，会 `Import-Module` 将模块成员导入到会话中，然后返回 **PSCustomObject** 对象，而不是 **PSModuleInfo** 对象。 可以在变量中保存自定义对象，并使用点表示法来调用成员。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Assembly

指定程序集对象的数组。 此 cmdlet 将导入在指定的程序集对象中实现的 cmdlet 和提供程序。 输入包含程序集对象的变量或可创建程序集对象的命令。 还可以通过管道将程序集对象传递给 `Import-Module` 。

使用此参数时，将仅导入由指定的程序集实现的 cmdlet 和提供程序。 如果模块包含其他文件，则不会导入它们，并且你可能会丢失模块的重要成员。 此参数用于调试和测试模块，或者在模块作者指示你使用它时使用。

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

指定可公开 CIM 模块的备用 CIM 提供程序的命名空间。 默认值是模块发现 WMI 提供程序的命名空间。

使用此参数从未运行 Windows 操作系统的计算机和设备导入 CIM 模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

指定 CIM 模块的备用位置。 默认值是远程计算机上模块发现 WMI 提供程序的资源 URI。

使用此参数从未运行 Windows 操作系统的计算机和设备导入 CIM 模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

指定远程计算机上的 CIM 会话。 输入包含 CIM 会话的变量或获取 CIM 会话的命令（如 [CimSession](../CimCmdlets/Get-CimSession.md) 命令）。

`Import-Module` 使用 CIM 会话连接将远程计算机中的模块导入到当前会话中。 在当前会话中使用导入模块中的命令时，这些命令将在远程计算机上运行。

你可以使用此参数从未运行 Windows 操作系统的计算机和设备以及具有 PowerShell 但未启用 PowerShell 远程处理的 Windows 计算机导入模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cmdlet

指定此 cmdlet 从模块导入到当前会话中的 cmdlet 的数组。
允许使用通配符。

在导入模块时，某些模块会自动将选定的 cmdlet 导出到你的会话中。
此参数允许你在导出的 cmdlet 中进行选择。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -DisableNameChecking

指示当你导入的 cmdlet 或函数名称包括未经批准的动词或禁止的字符时，此 cmdlet 将禁止显示警告你的消息。

默认情况下，当导入的模块导出名称中包含未经批准的谓词的 cmdlet 或函数时，PowerShell 将显示以下警告消息：

> 警告：某些导入的命令名称包括未经批准的动词，这可能会使它们更易发现。 请使用 Verbose 参数获取详细信息或者键入 Get-Verb 以查看批准的谓词列表。

此消息只是一个警告。 仍将导入完整的模块，其中包括非一致性的命令。 尽管会向模块用户显示消息，但是模块作者应修复命名问题。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

此参数会使模块加载或重新加载到当前模块的顶部。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

指定模块的完全限定名作为哈希表。 值可以是字符串和哈希表的组合。 此哈希表具有以下键。

- `ModuleName` - **必需** 指定模块名称。
- `GUID` - **可选** 指定模块的 GUID。
- 还 **需要** 指定以下三个键中的一个。 这些密钥不能一起使用。
  - `ModuleVersion` -指定模块的最低可接受版本。
  - `RequiredVersion` -指定模块的准确的必需版本。
  - `MaximumVersion` -指定模块可接受的最大版本。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Function

指定此 cmdlet 从模块导入到当前会话中的函数数组。
允许使用通配符。 在导入模块时，某些模块会自动将选定的函数导出到你的会话中。 此参数允许你在导出的函数中进行选择。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -全局

指示此 cmdlet 将模块导入全局会话状态，以便它们可用于会话中的所有命令。

默认情况下，当 `Import-Module` 从命令提示符、脚本文件或 scriptblock 调用 cmdlet 时，所有命令都将导入全局会话状态。

从另一个模块调用时，cmdlet 会将 `Import-Module` 模块中的命令（包括来自嵌套模块的命令）导入到调用模块的会话状态中。

> [!TIP]
> 应避免 `Import-Module` 从模块中调用。 相反，将目标模块声明为父模块清单中的嵌套模块。 声明嵌套模块可提高依赖项的可发现性。

**Global** 参数等效于值为 **Global** 的 **Scope** 参数。

若要限制模块导出的命令，请 `Export-ModuleMember` 在脚本模块中使用命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定最高版本。 此 cmdlet 仅导入小于或等于指定值的模块版本。 如果没有任何版本合格，则 `Import-Module` 返回一个错误。

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

指定最低版本。 此 cmdlet 仅导入大于或等于指定值的模块版本。 使用 **MinimumVersion** 参数名或它的别名 **Version**。 如果没有合格的版本， `Import-Module` 将生成错误。

若要指定确切的版本，请使用 **RequiredVersion** 参数。 你还可以使用 **#Requires** 关键字的 **module** 和 **Version** 参数来要求在脚本中使用特定版本的模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

指定要导入的模块对象的数组。 输入包含模块对象的变量，或获取模块对象的命令，如以下命令： `Get-Module -ListAvailable` 。 还可以通过管道将模块对象传递给 `Import-Module` 。

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要导入的模块的名称。 输入模块名称或模块中的文件名称，例如 `.psd1` 、、 `.psm1` `.dll` 或 `.ps1` 文件。 文件路径是可选的。 不允许使用通配符。 还可以通过管道将模块名称和文件名传递给 `Import-Module` 。

如果省略路径，则会 `Import-Module` 在环境变量中保存的路径中查找模块 `$env:PSModulePath` 。

在可能的情况下，仅指定模块名称。 指定文件名时，将仅导入在该文件中实现的成员。 如果模块包含其他文件，则不会导入它们，并且你可能会丢失模块的重要成员。

> [!NOTE]
> 尽管可以导入脚本 (`.ps1`) 文件作为模块，但脚本文件通常不像脚本模块文件 () 文件中那样进行结构化 `.psm1` 。 导入脚本文件并不能保证它可用作模块。 有关详细信息，请参阅 [about_Modules](about/about_Modules.md)。

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

禁止导入与当前会话中的现有命令名称相同的命令。 默认情况下，会 `Import-Module` 导入所有导出的模块命令。

具有相同名称的命令可以隐藏或替换会话中的命令。 若要避免会话中出现命令名称冲突，请使用 **Prefix** 或 **NoClobber** 参数。 有关名称冲突和命令优先顺序的详细信息，请参阅 [about_Modules](about/about_Modules.md) 和 [about_Command_Precedence](about/about_Command_Precedence.md) 中的“模块和名称冲突”。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回一个对象，该对象表示正在处理的项。 默认情况下，此 cmdlet 将不产生任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prefix

指定此 cmdlet 添加到导入的模块成员的名称中的名词的前缀。

使用此参数避免当会话中不同的成员具有相同的名称时，可能出现的名称冲突。 此参数不会更改模块，并且不会影响模块导入的、供自己使用的文件。 它们称为嵌套模块。 此 cmdlet 只影响当前会话中成员的名称。

例如，如果指定前缀 UTC，然后导入 `Get-Date` cmdlet，则该 cmdlet 将在会话中称为 `Get-UTCDate` ，而不会与原始 `Get-Date` cmdlet 混淆。

此参数的值将优先于模块的 **DefaultCommandPrefix** 属性，该属性指定默认的前缀。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

指定 (**PSSession**) 的 PowerShell 用户管理的会话，此 cmdlet 从中将模块导入到当前会话中。 输入包含 **pssession** 的变量或获取 **pssession** 的命令（如 `Get-PSSession` 命令）。

将其他会话中的模块导入当前会话中时，你可以在当前会话中使用来自模块的 cmdlet，就像你使用来自本地模块的 cmdlet 一样。 使用远程 cmdlet 的命令在远程会话中运行，但是远程处理详细信息由 PowerShell 在后台进行管理。

此参数使用 PowerShell 的隐式远程处理功能。 它相当于使用 `Import-PSSession` cmdlet 从会话导入特定模块。

`Import-Module` 无法从另一个会话导入 PowerShell Core 模块。 PowerShell Core 模块的名称以 Microsoft PowerShell 开头。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定此 cmdlet 导入的模块的版本。 如果未安装该版本，将 `Import-Module` 生成一个错误。

默认情况下， `Import-Module` 将导入该模块，而不检查版本号。

若要指定最低版本，请使用 **MinimumVersion** 参数。 你还可以使用 **#Requires** 关键字的 **module** 和 **Version** 参数来要求在脚本中使用特定版本的模块。

已在 Windows PowerShell 3.0 中引入了此参数。

使用 **RequiredVersion** 导入现有 windows 操作系统版本随附的模块的脚本不会在将来版本的 windows 操作系统中自动运行。 这是因为 Windows 操作系统未来版本中的 PowerShell 模块版本号高于 Windows 操作系统现有版本中的模块版本号。

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定此 cmdlet 将模块导入到其中的作用域。

此参数的可接受值为：

- **全局**。 可供会话中所有的命令使用。 等效于 **Global** 参数。
- **Local**。 仅在当前作用域中可用。

默认情况下，当 `Import-Module` 从命令提示符、脚本文件或 scriptblock 调用 cmdlet 时，所有命令都将导入全局会话状态。 可以使用参数将 `-Scope Local` 模块内容导入到脚本或 scriptblock 范围。

从另一个模块调用时，cmdlet 会将 `Import-Module` 模块中的命令（包括来自嵌套模块的命令）导入到调用方的会话状态中。 指定 `-Scope Global` 或 `-Global` 指示此 cmdlet 将模块导入全局会话状态，以便它们可用于会话中的所有命令。

**Global** 参数等效于值为 **Global** 的 **Scope** 参数。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定此 cmdlet 从模块导入到当前会话中的变量的数组。
输入变量的列表。 允许使用通配符。

在导入模块时，某些变量会自动将选定的变量导出到你的会话中。
此参数允许你在导出的变量中进行选择。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -SkipEditionCheck

跳过对该字段的检查 `CompatiblePSEditions` 。

当模块不 `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` `Core` 在清单字段中指定时，允许将模块从模块目录加载到 PowerShell Core `CompatiblePSEditions` 。

从另一个路径导入模块时，此开关不会执行任何操作，因为不执行检查。 在 Linux 和 macOS 上，此开关不会执行任何操作。

有关详细信息，请参阅 [about_PowerShell_Editions](About/about_PowerShell_Editions.md)。

> [!WARNING]
> `Import-Module -SkipEditionCheck` 可能无法导入模块。 即使它确实成功，在尝试使用不兼容的 API 时，从模块中调用命令也可能失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedName, FullyQualifiedNameAndPSSession, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseWindowsPowerShell

使用 Windows PowerShell 兼容性功能加载模块。 有关详细信息，请参阅 [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.web、PSModuleInfo、System.string 和程序集。

可以通过管道将模块名称、模块对象或程序集对象传递给此 cmdlet。

## 输出

### "无"、"PSModuleInfo" 或 "PSCustomObject"

默认情况下，不 `Import-Module` 会生成任何输出。 如果指定 **PassThru** 参数，则该 cmdlet 将生成表示该模块的 **PSModuleInfo** 对象。 如果指定 **AsCustomObject** 参数，则会生成 **PSCustomObject** 对象。

## 注释

- 在导入模块之前，必须在本地计算机上安装该模块。 也就是说，必须将模块目录复制到本地计算机可以访问的目录中。 有关详细信息，请参阅 [about_Modules](About/about_Modules.md)。

  你还可以使用 **PSSession** 和 **CIMSession** 参数导入远程计算机上安装的模块。 但是，在这些模块中使用这些 cmdlet 的命令将在远程计算机上的远程会话中运行。

- 如果将具有相同名称和相同类型的成员导入到会话中，则默认情况下，PowerShell 将使用上次导入的成员。 将替换变量和别名，并且原始不可访问。 函数、cmdlet 和提供程序仅由新成员隐藏。 可以通过使用其管理单元、模块或函数路径的名称限定命令名称来访问它们。

- 若要更新已从模块导入的命令的格式设置数据，请使用 `Update-FormatData` cmdlet。 `Update-FormatData` 还会更新会话中从模块导入的命令的格式设置数据。 如果模块的格式化文件发生更改，则可以运行 `Update-FormatData` 命令来更新导入命令的格式设置数据。 不需要再次导入该模块。

- 从 Windows PowerShell 3.0 开始，随 PowerShell 一起安装的核心命令打包在模块中。 在 Windows PowerShell 2.0 和在 PowerShell 的更高版本中创建旧样式会话的主机程序中，核心命令打包在 (**PSSnapins**) 的管理单元中。 **Microsoft.PowerShell.Core** 是例外情况，它始终是一个管理单元。 远程会话（如 cmdlet 启动的会话） `New-PSSession` 是包含核心管理单元的旧样式会话。

  有关 **CreateDefault2** 方法的信息，该方法可创建带有核心模块的更新样式的会话，请参阅 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)。

- 在 Windows PowerShell 2.0 中，在导入模块之前，不会填充 module 对象的某些属性值，例如 **ExportedCmdlets** 和 **NestedModules** 属性值。

- 如果尝试导入的模块包含与 Windows PowerShell 3.0 + 不兼容的混合模式程序集，将 `Import-Module` 返回如下错误消息。

  > Import-Module：混合模式程序集是根据运行时的版本 "2.0.50727" 生成的，无法在4.0 运行时中加载，无需其他配置信息。

  如果为 Windows PowerShell 2.0 设计的模块至少包含一个混合模块程序集，则会出现此错误。 混合模块程序集，其中包括托管和非托管代码，例如 c + + 和 c #。

  若要导入包含混合模式程序集的模块，请使用以下命令启动 Windows PowerShell 2.0，然后重试该 `Import-Module` 命令。

  `PowerShell.exe -Version 2.0`

- 若要使用 CIM 会话功能，远程计算机必须具有 WS-Management 远程处理和 Windows Management Instrumentation (WMI)，后者是通用信息模型 (CIM) 标准的 Microsoft 实现。 计算机还必须具有具有相同基本功能的模拟发现 WMI 提供程序和备用 CIM 提供程序。

  你可以在未运行 Windows 操作系统的计算机上以及在具有 PowerShell 但未启用 PowerShell 远程处理的 Windows 计算机上使用 CIM 会话功能。

  你还可以使用 CIM 参数从启用了 PowerShell 远程处理的计算机（包括本地计算机）中获取 CIM 模块。 在本地计算机上创建 CIM 会话时，PowerShell 将使用 DCOM 而不是 WMI 来创建会话。

- 默认情况下， `Import-Module` 即使从子代范围中调用，也会导入全局范围内的模块。 顶级范围和所有后代范围均有权访问模块的导出元素。

  在后代范围内， `-Scope Local` 将导入限制为该作用域及其所有后代作用域。 父作用域后，看不到导入的成员。

  > [!NOTE]
  > `Get-Module` 显示当前会话中加载的所有模块。 这包括在后代范围本地加载的模块。 使用 `Get-Command -Module modulename` 查看当前范围中加载的成员。

  `Import-Module` 不加载模块中的类和枚举定义。 使用 `using module` 脚本开头的语句。 这会导入模块，包括类和枚举定义。 有关详细信息，请参阅 [about_Using](About/about_Using.md)。

## 相关链接

[about_Modules](about/about_Modules.md)

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
