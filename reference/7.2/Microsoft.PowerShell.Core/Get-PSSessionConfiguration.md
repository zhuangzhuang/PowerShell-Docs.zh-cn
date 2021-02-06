---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: a5aa70521841b3b05d34623ff92ebbf9e3471fd1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599075"
---
# Get-PSSessionConfiguration

## 摘要
获取计算机上已注册的会话配置。

## SYNTAX

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-PSSessionConfiguration` cmdlet 将获取已在本地计算机上注册的会话配置。 这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。

从 PowerShell 3.0 开始，你可以使用会话配置 (. .pssc) 文件来定义会话配置的属性。 此功能允许你创建自定义和受限制的会话，而无需编写计算机程序。 有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此外，从 PowerShell 3.0 开始，已将新的备注属性添加到了返回的会话配置对象中 `Get-PSSessionConfiguration` 。 这些属性使用户和会话配置作者可以更轻松地检查和比较会话配置。

若要创建和注册会话配置，请使用 `Register-PSSessionConfiguration` cmdlet。
有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 示例

### 示例 1-获取本地计算机上的会话配置

```powershell
Get-PSSessionConfiguration
```

### 示例 2-获取两个默认会话配置

命令使用的 **Name** 参数 `Get-PSSessionConfiguration` 仅获取名称以 "Microsoft" 开头的会话配置。

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### 示例 3-获取会话配置的属性和值

本示例显示了使用会话配置文件创建的会话配置的属性和属性值。

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

该示例使用 `Get-PSSessionConfiguration` cmdlet 来获取完整的会话配置。 管道运算符将完整会话配置发送到 `Format-List` cmdlet。 如果 **Property** 参数的值为 `*` (all) ，则 `Format-List` 指示在列表中显示该对象的所有属性和值。

输出包含有用的信息，包括会话配置的作者、会话类型、语言模式和通过此会话配置创建的会话的执行策略、会话配额和会话配置文件的完整路径。

会话配置的此视图适用于包括会话配置文件的会话。
有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

### 示例 4-查看会话配置的另一种方法

此示例使用 `Get-ChildItem` `dir` WSMan： provider 驱动器中的 cmdlet (别名) 来查看插件节点的内容。 这是在计算机上查看会话配置的另一种方式。

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

" **插件** " 节点包含 **ContainerElement** 对象 (WSManConfigContainerElement) ，这些对象表示已注册的 POWERSHELL 会话配置以及 ws-management 的其他插件。

### 示例 6-查看远程计算机上的会话配置

本示例显示了如何使用 WSMan 提供程序在远程计算机上查看会话配置。 此方法并不提供任何信息作为 `Get-PSSessionConfiguration` 命令，但用户无需成为 Administrators 组的成员即可运行此 cmdlet。

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

`Connect-WSMan`Cmdlet 连接到 Server01 远程计算机上的 WinRM 服务。 `Get-ChildItem`WSMan：驱动器的 cmdlet (别名 `dir`) 获取 **Server01\Plugin** 路径中的项。 该输出将显示 Server01 计算机上 Plugin 目录中的项。 这些项包括会话配置（WSMan 插件的一种类型）以及计算机上的其他插件类型。

### 示例 7-从远程计算机获取详细的会话配置

此示例演示如何 `Get-PSSessionConfiguration` 在远程计算机上运行命令。 该命令要求在本地计算机上的客户端设置和远程计算机的服务设置中启用 CredSSP 委派。

若要运行此示例中的命令，您必须是本地计算机和远程计算机上的 Administrators 组的成员，并且您必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

`Enable-WSManCredSSP`Cmdlet 可在本地计算机上的 Server01 上启用 **CredSSP** 委托。 `Connect-WSMan`Cmdlet 连接到 Server02 计算机。 此操作会将 Server02 的节点添加到本地计算机上的 WSMan：驱动器中，以便查看和更改 Server02 计算机上的 WS-Management 设置。 `Set-Item`Cmdlet 将 Server02 计算机的 Service 节点中的 **CredSSP** 项的值更改为 **True**。 这会在远程计算机上配置服务设置。 `Invoke-Command`Cmdlet `Get-PSSessionConfiguration` 在 Server02 计算机上运行命令。 该命令使用 **Credential** 参数，并使用值为 **CredSSP** 的 **Authentication** 参数。 该输出显示 Server02 远程计算机上的会话配置。

### 示例 8-获取会话配置的资源 URI

此示例适用于设置 `$PSSessionConfigurationName` 首选项变量的值，后者采用资源 URI。

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

`$PSSessionConfigurationName`变量指定在创建会话时使用的默认配置。 此变量是在本地计算机上设置的，但是它可指定远程计算机上的配置。 有关变量的详细信息 `$PSSessionConfiguration` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

## PARAMETERS

### -Force

如果该服务尚未运行，请取消显示提示以重新启动 WinRM 服务。

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

### -Name

仅获取具有指定名称或名称模式的会话配置。 输入一个或多个会话配置名称。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration

## 注释

- 若要运行此 cmdlet，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。

- 若要查看计算机上的会话配置，你必须是计算机上 Administrators 组的成员。

- 若要 `Get-PSSessionConfiguration` 在远程计算机上运行命令，则必须在本地计算机上的客户端设置中启用凭据安全服务提供程序 (CredSSP) 身份验证 (通过在 `Enable-WSManCredSSP` 远程计算机上使用 cmdlet) 和服务设置。 此外，在建立远程会话时，必须使用 **Authentication** 参数的 **CredSSP** 值。 否则，访问将被拒绝。

- `Get-PSSessionConfiguration`仅当对象具有值时，才会在该对象上显示该对象的注解属性。 只有使用会话配置文件创建的会话配置具有所有已定义的属性。

- 会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。 此外，使用会话配置文件的会话配置还具有其他属性。

- 你可以使用 WSMan: 驱动器中的命令来更改会话配置的属性。
  但是，不能使用 PowerShell 2.0 中的 WSMan：驱动器来更改 PowerShell 3.0 中引入的会话配置属性，如 **OutputBufferingMode**。 PowerShell 2.0 命令不会生成错误，但它们是无效的。 若要更改 PowerShell 3.0 中引入的属性，请使用 PowerShell 3.0 中的 WSMan：驱动器。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

