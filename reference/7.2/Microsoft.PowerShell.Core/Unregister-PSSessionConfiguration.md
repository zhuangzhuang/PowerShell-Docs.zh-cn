---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 4ac7605ada0fdb682e9df31c2422d368d6e64f57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598250"
---
# Unregister-PSSessionConfiguration

## 摘要
从计算机中删除已注册的会话配置。

## SYNTAX

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Unregister-PSSessionConfiguration`Cmdlet 将从计算机中删除已注册的会话配置。 此 cmdlet 旨在供系统管理员管理用户的自定义会话配置。

若要使更改生效，请 `Unregister-PSSessionConfiguration` 重新启动 **WinRM** 服务。 若要防止重启，请指定 NoServiceRestart 参数。

如果意外删除 **了默认的** **microsoft.powershell32** 会话配置，请使用 `Enable-PSRemoting` cmdlet 来还原它们。 有关详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 示例

### 示例 1：删除会话配置

此示例将从计算机中删除 **MaintenanceShell** 会话配置。

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### 示例 2：删除会话配置并重启 WinRM 服务

在此示例中，我们将删除 **MaintenanceShell** 配置并重新启动 WinRM 服务。 **Force** 参数取消所有用户消息，以便在不提示的情况下重新启动 **WinRM** 服务。

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### 示例 3：删除所有会话配置

此示例显示了删除计算机上的所有会话配置的两种方法。 这两个命令具有相同的效果，并且可以互换使用。

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### 示例 4：注销（不重启）

此示例显示了使用 **NoServiceRestart** 参数防止服务重新启动，从而中断计算机上的任何会话的影响。

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

`Unregister-PSSessionConfiguration`删除 **MaintenanceShell** 会话配置。
但是，因为该命令使用 NoServiceRestart 参数，所以不会重启 **WinRM** 服务，而且更改尚未完全起效。

接下来， `Get-PSSessionConfiguration` 尝试获取 **MaintenanceShell** 会话。 由于已从 WS-Management 资源表中删除该会话，因此 `Get-PSSessionConfiguration` 无法将其返回。

`New-PSSession`Cmdlet 使用 **MaintenanceShell** 配置创建会话。 该命令执行成功。 接下来，重新启动 **WinRM** 服务。

最后，该 `New-PSSession` cmdlet 会尝试创建使用 **MaintenanceShell** 配置的会话。 这次会话失败，因为在重新启动 WinRM 服务时已删除 **MaintenanceShell** 配置。

## PARAMETERS

### -Force

指示 cmdlet 不提示进行确认，并且将在无提示的情况下重启 **WinRM** 服务。 重新启动服务可使配置更改生效。

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

### -Name

指定要删除的会话配置的名称。 输入一个会话配置名称或配置名称模式。 允许使用通配符。 此参数是必需的。

还可以通过管道将会话配置传递给 `Unregister-PSSessionConfiguration` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

指示此 cmdlet 不重启 **WinRM** 服务，并且禁止提示重启该服务。

默认情况下，当你运行 `Unregister-PSSessionConfiguration` 命令时，系统将提示你重新启动 **WinRM** 服务以使更改生效。 在重新启动 **WinRM** 服务之前，用户仍然可以使用未注册的会话配置，即使 `Get-PSSessionConfiguration` 找不到它。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration

你可以通过管道将会话配置对象传递 `Get-PSSessionConfiguration` 给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

若要运行此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

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

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
