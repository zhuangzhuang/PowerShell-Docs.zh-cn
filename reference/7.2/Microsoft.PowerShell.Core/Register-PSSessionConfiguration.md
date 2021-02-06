---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 0ec31d32ef73108b53b18b529cc93aa80787fe25
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603408"
---
# Register-PSSessionConfiguration

## 摘要
创建并注册新的会话配置。

## SYNTAX

### NameParameterSet（默认值）

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Register-PSSessionConfiguration`Cmdlet 在本地计算机上创建并注册新的会话配置。 这是一个高级 cmdlet，可用于为远程用户创建自定义会话。

每个 PowerShell 会话 (**PSSession**) 使用会话配置（也称为终结点）。
当用户创建连接到计算机的会话时，他们可以选择一个会话配置，或使用在启用 PowerShell 远程处理时注册的默认会话配置。
用户还可以设置 $PSSessionConfigurationName 首选项变量，它指定在当前会话中创建的远程会话的默认配置。

会话配置可定义远程会话的环境。 此配置可以确定会话中可使用哪些命令和语言元素，它可以包含用于保护计算机的设置，如用于限制单个对象或命令中会话可以远程接收的数据量的设置。 会话配置的安全描述符将确定哪些用户有权使用会话配置。

通过使用可实现新的配置类的程序集以及在会话中运行的脚本，可以定义配置的元素。 从 PowerShell 3.0 开始，还可以使用会话配置文件来定义会话配置。

有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。
有关会话配置文件的信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

## 示例

### 示例1：注册 NewShell 会话配置

在此示例中，我们将注册 **NewShell** 会话配置。 **AssemblyName** 和 **ApplicationBase** 参数指定 **MyShell.dll** 文件的位置，该位置指定会话配置中的 cmdlet 和提供程序。 **ConfigurationTypeName** 参数指定要从程序集使用的配置类。

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

若要使用此配置，请键入 `New-PSSession -ConfigurationName newshell` 。

### 示例2：注册 MaintenanceShell 会话配置

此示例在本地计算机上注册 **MaintenanceShell** 会话配置。 **StartupScript** 参数指定 `Maintenance.ps1` 脚本。

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

当用户使用 `New-PSSession` 命令并选择 **MaintenanceShell** 配置时，该脚本将 `Maintenance.ps1` 在新的会话中运行。 该脚本可以配置会话。 这包括导入模块和设置会话的执行策略。 如果脚本生成任何错误，包括非终止错误，则该 `New-PSSession` 命令将失败。

### 示例3：注册会话配置

此示例将注册 **AdminShell** 会话配置。

`$sessionParams`变量是包含所有参数值的哈希表。 使用 PowerShell 展开将此哈希表传递给 cmdlet。 该 `Register-PSSessionConfiguration` 命令使用 **SecurityDescritorSDDL** 参数在变量的值中指定 SDDL `$sddl` ，并使用 **MaximumReceivedObjectSizeMB** 参数来增加对象大小限制。 它还使用 **StartupScript** 参数来指定用于配置会话的脚本。

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### 示例4：返回配置容器元素

此示例演示如何注册 **MaintenanceShell** 配置。
`Register-PSSessionConfiguration` 返回存储在变量中的 **WSManConfigContainerElement** 对象 `$s` 。 `Format-List` 显示返回对象的所有属性。 **PSPath** 属性显示该对象存储在 WSMan: 驱动器的目录中。 `Get-ChildItem` (别名 `dir`) 显示路径中的项 `WSMan:\LocalHost\PlugIn` 。 其中包括新的 **MaintenanceShell** 配置和 PowerShell 附带的两个默认配置。

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### 示例5：使用启动脚本注册会话配置

在此示例中，我们将创建并注册 **WithProfile** 会话配置。 **StartupScript** 参数指示 PowerShell 为任何使用会话配置的会话运行指定的脚本。

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

该脚本包含单个命令，该命令使用点 (.) 来获得来源，以在会话的当前作用域中运行用户的 **CurrentUserAllHosts** 配置文件。

有关配置文件的详细信息，请参阅 [about_Profiles](./About/about_Profiles.md)。 有关使用点 (.) 来获得来源的详细信息，请参阅 [about_Scopes](./About/about_Scopes.md)。

## PARAMETERS

### -AccessMode

启用和禁用会话配置，并确定它是否可以用于计算机上的远程或本地会话。 此参数的可接受值为：

- 已禁用。 禁用会话配置。 它不能用于对计算机的远程或本地访问。
- Local。 允许本地计算机的用户使用会话配置在同一台计算机上创建本地环回会话，但拒绝远程用户的访问。
- 远程. 允许本地和远程用户使用会话配置创建会话并在此计算机上运行命令。

默认值为 "远程"。

其他 cmdlet 稍后可以重写此参数的值。 例如， `Enable-PSRemoting` cmdlet 允许远程访问所有会话配置， `Enable-PSSessionConfiguration` cmdlet 启用会话配置，并且该 `Disable-PSRemoting` cmdlet 阻止对所有会话配置的远程访问。

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

指定 \* 在 **AssemblyName** 参数的值中指定的程序集文件 () 的路径。 如果 **AssemblyName** 参数的值不包括路径，则使用此参数。 默认为当前目录。

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

指定 \* 在其中定义配置类型 () 程序集文件的名称。 可以在此参数或 **ApplicationBase** 参数的值中指定 .dll 的路径。

当指定 **ConfigurationTypeName** 参数时，此参数是必需的。

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

指定用于此配置的 Microsoft .NET Framework 类型的完全限定的名称。 指定的类型必须实现 **System.Management.Automation.Remoting.PSSessionConfiguration** 类。

若要指定 \* 实现配置类型 () 的程序集文件，请指定 **AssemblyName** 和 **ApplicationBase** 参数。

通过创建类型，可以控制会话配置的更多方面，如公开或隐藏 cmdlet 的某些参数，或设置用户无法重写的数据大小和对象大小限制。

如果省略此参数，则 **DefaultRemotePowerShellConfiguration** 类将用于会话配置。

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

若要防止重新启动并取消重新启动提示，请指定 **NoServiceRestart** 参数。

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

如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义数据大小限制，则将使用配置类型中的限制并忽略此参数的值。

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

如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义对象大小限制，则将使用配置类型中的限制并忽略此参数的值。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定自动导入到使用会话配置的会话中的模块。

默认情况下，仅将 **Microsoft** 导入到会话中。 除非排除 cmdlet，否则可以使用 `Import-Module` 将模块添加到会话中。

在此参数值中指定的模块将导入到由 **SessionType** 参数指定的模块中，以及会话配置文件中的 **ModulesToImport** 键中列出的模块 (`New-PSSessionConfigurationFile`) 。 但是，会话配置文件中的设置可以隐藏模块所导出的命令或阻止用户使用它们。

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

指定会话配置的名称。 此参数是必需的。

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

默认情况下，当你运行 `Register-PSSessionConfiguration` 命令时，系统将提示你重新启动 **WinRM** 服务以使新的会话配置生效。 在重新启动 **WinRM** 服务之前，新的会话配置不会生效。

若要在无提示的情况下重启 **WinRM** 服务，请指定 Force 参数。 若要手动重新启动 **WinRM** 服务，请使用 `Restart-Service` cmdlet。

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

指定会话配置文件的路径和文件名 ( .pssc) ，如创建的文件 `New-PSSessionConfigurationFile` 。 如果省略路径，则默认路径为当前目录。

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

### -ProcessorArchitecture

确定在使用此会话配置的会话中是否启动了 PowerShell 进程的32位或64位版本。 此参数可接受的值包括： x86 (32 位) 和 AMD64 () 64。 默认值由托管该会话配置的计算机的处理器体系结构确定。

可使用此参数在 64 位计算机上创建 32 位会话。 尝试在 32 位计算机上创建 64 位进程将失败。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
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

指定用于配置的安全描述符定义语言 (SDDL) 字符串。

此字符串确定使用新的会话配置所需的权限。 若要在会话中使用会话配置，用户必须至少对配置执行 (调用) 权限。

如果安全描述符较复杂，请考虑使用 **ShowSecurityDescriptorUI** 参数，而不是此参数。 不能在同一命令中同时使用这两个参数。

如果省略此参数，则会将 **WinRM** 服务的根 SDDL 用于此配置。
若要查看或更改根 SDDL，请使用 WSMan 提供程序。 例如，`Get-Item wsman:\localhost\service\rootSDDL`。 有关 WSMan 提供程序的详细信息，请键入 `Get-Help wsman` 。

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

指示此 cmdlet 显示可帮助你创建会话配置的 SDDL 的属性表。 输入该命令后，将显示属性表 `Register-PSSessionConfiguration` ，然后重新启动 **WinRM** 服务。

在设置配置的权限时，请记住，用户必须至少执行 (调用) 权限才能在会话中使用会话配置。

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

指定 PowerShell 脚本的完全限定路径。 指定的脚本在使用会话配置的新会话中运行。

你可以使用脚本来额外配置会话。 如果脚本生成错误，甚至是一个非终止错误，则不会创建会话，并且该 `New-PSSession` 命令将失败。

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

指定在会话中运行命令时如何创建和使用线程。 此参数的可接受值为：

- 默认
- ReuseThread
- UseCurrentThread
- UseNewThread

默认值为 **UseCurrentThread**。

有关详细信息，请参阅 [PSThreadOptions 枚举](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)。

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

指定传输选项。

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

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

### WSManConfigContainerElement。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

若要运行此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

此 cmdlet 将生成表示 Web Services for Management (WS-MANAGEMENT) 插件配置的 XML，并将该 XML 发送到 WS-MANAGEMENT，后者将在本地计算机上注册该插件 (`New-Item wsman:\localhost\plugin`) 。

会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。 此外，使用会话配置文件的会话配置还具有其他属性。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
