---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c3c3c0bbb0436ef2e6857adc35f83e627d03f4b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595819"
---
# Set-PSSessionConfiguration

## 摘要
更改已注册会话配置的属性。

## SYNTAX

### NameParameterSet（默认值）

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Set-PSSessionConfiguration`Cmdlet 更改本地计算机上的会话配置的属性。

使用 **Name** 参数标识要更改的会话配置。 使用其他参数为会话配置的属性指定新值。 若要从配置中删除属性值并使用默认值，请输入空字符串 ( "" ) 或 `$Null` 相应参数的值。

从 PowerShell 3.0 开始，你可以使用会话配置文件来定义会话配置。 此功能提供了一种简单且易于发现的方法，可用于设置和更改使用会话配置的会话的属性。 若要指定会话配置文件，请使用的 **Path** 参数 `Set-PSSessionConfiguration` 。 有关会话配置文件的信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。
有关如何创建和修改会话配置文件的信息，请参阅 `New-PSSessionConfigurationFile` cmdlet。

会话配置定义连接到本地计算机 (**pssession**) 的远程会话的环境。 每个 **PSSession** 都使用会话配置。 会话配置确定 **PSSession** 的功能，例如会话中可用的模块、允许运行的 cmdlet、语言模式、配额和超时。 会话配置的安全描述符确定哪些用户可以使用会话配置连接到本地计算机。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

若要查看会话配置的属性，请使用 `Get-PSSessionConfiguration` cmdlet 或 WSMan 提供程序。 有关 WSMan 提供程序的详细信息，请键入 `Get-Help WSMan` 。

## 示例

### 示例1：创建和更改会话配置

此示例演示如何从配置中添加和删除启动脚本。

第一个命令创建 **AdminShell** 配置。 第二个命令将此 `AdminConfig.ps1` 脚本添加到配置。 重新启动 **WinRM** 后，更改才有效。
第三个命令 `AdminConfig.ps1` 从配置中删除该脚本。

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### 示例2：显示结果

此示例将 **MaximumReceivedObjectSizeMB** 属性的值增加到20。 此命令还会提示你重新启动 **WinRM** 服务。 在重新启动 **WinRM** 服务之前，更改不会生效。

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### 示例3：以不同的方式显示结果

在此示例中，将 `Set-PSSessionConfiguration` **MaintenanceShell** 会话配置中的启动脚本更改为 `Maintenance.ps1` 。 输出显示更改并提示你重新启动 **WinRM** 服务。 响应是“y”（是）。

`Get-PSSessionConfiguration` 获取 **MaintenanceShell** 会话配置。 管道运算符 (|) 将命令的结果发送到 `Format-List` ，后者将在列表中显示配置对象的所有属性。 接下来，使用 WSMan 提供程序查看 **MaintenanceShell** 配置的初始化参数。 `Get-ChildItem` (别名 `dir`) 获取 **MaintenanceShell** 插件的 **InitializationParameters** 节点中的子项目。 有关 WSMan 提供程序的详细信息，请键入 `Get-Help wsman` 。

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMETERS

### -AccessMode

启用和禁用会话配置，并确定它是否可以用于计算机上的远程或本地会话。 此参数的可接受值为：

- 已禁用。 禁用会话配置。 它不能用于对计算机的远程或本地访问。 此值将会话配置的 **Enabled** 属性设置 (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) 设置为 **False**。
- Local。 将 **Network_Deny_All** 条目添加到会话配置的安全描述符。
  本地计算机的用户可以使用会话配置在同一台计算机上创建本地环回会话，但会拒绝远程用户访问。
- 远程. 从会话配置的安全描述符中删除 **Deny_All** 和 **Network_Deny_All** 条目。 本地和远程计算机的用户都可以使用会话配置来创建会话，并在此计算机上运行命令。

默认值为 " **远程**"。

其他 cmdlet 稍后可以重写此参数的值。 例如，该 `Enable-PSRemoting` cmdlet 将启用计算机上的所有会话配置并允许远程访问这些配置，并且该 `Disable-PSRemoting` cmdlet 只允许对计算机上的所有会话配置进行本地访问。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationBase

指定 \* 在 **AssemblyName** 参数的值中指定的程序集文件 () 的路径。

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

指定程序集名称。 此 cmdlet 将基于在程序集中定义的类来创建会话配置。

输入定义会话配置的程序集 .dll 文件的文件名或完整路径。 如果只输入文件名，则可以在 **ApplicationBase** 参数的值中输入路径。

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

指定在 **AssemblyName** 参数的程序集中定义的会话配置的类型。 指定的类型必须实现 **System.Management.Automation.Remoting.PSSessionConfiguration** 类。

在指定程序集名称时需要此参数。

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

禁止显示所有用户提示，并在不提示的情况下重新启动 **WinRM** 服务。 重新启动服务可使配置更改生效。

若要阻止重新启动并取消重新启动提示，请使用 **NoServiceRestart** 参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedDataSizePerCommandMB

指定在任何单个远程命令中可以发送到此计算机的数据量限制。 输入数据大小（以兆字节 (MB) 为单位）。 默认值为 50 MB。

如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义了数据大小限制，则使用配置类型中的限制。 忽略此参数的值。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

指定在任何单个对象中可以发送到此计算机的数据量的限制。
输入数据大小（以 mb 为单位）。 默认值为 10 MB。

如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义了对象大小限制，则使用配置类型中的限制。 忽略此参数的值。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定自动导入使用该会话配置的会话的模块和管理单元。 输入模块和管理单元名称。

默认情况下，只会将 **Microsoft. Core** 管理单元导入到会话中，但除非排除 cmdlet，否则可以使用 `Import-Module` 和 Add-PSSnapin cmdlet 将模块和管理单元添加到会话中。

此参数值中指定的模块将导入到会话配置文件 () 中指定的模块中 `New-PSSessionConfigurationFile` 。 但是，会话配置文件中的设置可以隐藏模块所导出的命令或阻止用户使用它们。

此参数值中指定的模块将替换使用 cmdlet 的 **ModulesToImport** 参数指定的模块列表 `Register-PSSessionConfiguration` 。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要更改的会话配置的名称。

不能使用此参数更改会话配置的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

不会重新启动 **WinRM** 服务，而会禁止提示重新启动该服务。

默认情况下，当你运行时 `Set-PSSessionConfiguration` ，系统将提示你重新启动 **WinRM** 服务以使新的会话配置生效。 在重新启动 **WinRM** 服务之前，新的会话配置不会生效。

若要在不提示的情况下重新启动 **WinRM** 服务，请使用 **Force** 参数。 若要手动重新启动 **WinRM** 服务，请使用 `Restart-Service` cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定会话配置文件的路径 ( .pssc) ，如 cmdlet 创建的文件。 `New-PSSessionConfigurationFile` 如果省略路径，则默认路径为当前目录。

有关如何修改会话配置文件的信息，请参阅 cmdlet 的帮助主题 `New-PSSessionConfigurationFile` 。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

指定使用此会话配置的会话中的 PowerShell 版本。

此参数的值优先于会话配置文件中 **PowerShellVersion** 键的值。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

指定会话中的命令的凭据。 默认情况下，在当前用户授权下运行命令。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

为配置指定其他安全描述符定义语言 (SDDL) 字符串。

此字符串确定使用新的会话配置所需的权限。 若要在会话中使用会话配置，用户必须至少对配置执行 (调用) 权限。

若要使用配置的默认安全描述符，请输入空字符串 ( "" ) 或值 `$Null` 。 默认为 WSMan: 驱动器中的根 SDDL。

如果安全描述符很复杂，请考虑使用 **ShowSecurityDescriptorUI** 参数而不是此描述符。 不能在同一命令中同时使用这两个参数。

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

### -SessionTypeOption

指定会话配置的特定于类型的选项。 输入会话类型选项对象，如 cmdlet 返回的 **new-psworkflowexecutionoption** 对象 `New-PSWorkflowExecutionOption` 。

使用会话配置的会话选项由会话选项和会话配置选项的值确定。 除非指定，否则在会话中设置的选项（如使用 `New-PSSessionOption` cmdlet）优先于在会话配置中设置的选项。 但是，会话选项的值不能超过在会话配置中设置的最大值。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

指示此 cmdlet 是可帮助你为会话配置创建新 SDDL 的属性表。 运行该命令后，将显示属性表 `Set-PSSessionConfiguration` ，然后重新启动 **WinRM** 服务。

在设置配置的权限时，请记住，用户必须至少具有 "执行 (调用") 权限才能使用会话中的会话配置。

不能在同一命令中使用 **SecurityDescriptorSDDL** 参数和此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupScript

指定配置的启动脚本。 输入 PowerShell 脚本的完全限定路径。 指定的脚本在使用会话配置的新会话中运行。

若要从会话配置中删除启动脚本，请输入空字符串 ( "" ) 或值 `$Null` 。

你可以使用启动脚本进一步配置用户会话。 如果脚本生成错误，甚至是一个非终止错误，则不会创建会话，并且该 `New-PSSession` 命令将失败。

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

### -ThreadOptions

指定配置中的线程选项设置。 此设置定义在会话中执行命令时如何创建和使用线程。 此参数的可接受值为：

- 默认
- ReuseThread
- UseCurrentThread
- UseNewThread

默认值为 **UseCurrentThread**。

有关详细信息，请参阅 [PSThreadOptions 枚举](/dotnet/api/system.management.automation.runspaces.psthreadoptions)。

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

指定会话配置的传输选项。 输入传输选项对象，如 cmdlet 返回的 **WSManConfigurationOption** 对象 `New-PSTransportOption` 。

使用会话配置的会话选项由会话选项和会话配置选项的值确定。 除非指定，否则在会话中设置的选项（如使用 `New-PSSessionOption` cmdlet）优先于在会话配置中设置的选项。 但是，会话选项的值不能超过在会话配置中设置的最大值。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

仅使用一个进程来托管由同一用户启动的所有会话，并使用相同的会话配置。 默认情况下，每个会话都托管在其自身进程中。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThreadApartmentState

指定要使用的线程模块的单元状态。 可接受的值为：

- Unknown
- MTA
- STA

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### WSManConfigLeafElement。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

若要运行此 cmdlet，请使用 "以管理员身份运行" 选项启动 PowerShell。

`Set-PSSessionConfiguration`Cmdlet 不会更改配置名称，并且 **WSMan** 提供程序不支持 `Rename-Item` cmdlet。 若要更改会话配置的名称，请使用 `Unregister-PSSessionConfiguration` cmdlet 删除该配置，然后使用 `Register-PSSessionConfiguration` cmdlet 创建并注册新的会话配置。

你可以使用 `Set-PSSessionConfiguration` cmdlet 更改默认的 microsoft.powershell32 会话配置。 这些会话配置不受保护。 要恢复为默认会话配置的原始版本，请使用 `Unregister-PSSessionConfiguration` cmdlet 删除默认会话配置，然后使用 `Enable-PSRemoting` cmdlet 将其还原。

会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。 此外，使用会话配置文件的会话配置还具有其他属性。

你可以使用 WSMan: 驱动器中的命令来更改会话配置的属性。
但是，不能使用 PowerShell 2.0 中的 WSMan：驱动器来更改 PowerShell 3.0 中引入的会话配置属性，如 **OutputBufferingMode**。 Windows PowerShell 2.0 命令不会生成错误，但它们是无效的。 若要更改 PowerShell 3.0 中引入的属性，请使用 PowerShell 3.0 中的 WSMan：驱动器。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
