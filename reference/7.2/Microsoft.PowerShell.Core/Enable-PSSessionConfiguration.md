---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 86650f33f376ccb7d1428836c9d0070e749cf0ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597670"
---
# Enable-PSSessionConfiguration

## 摘要
启用本地计算机上的会话配置。

## SYNTAX

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Enable-PSSessionConfiguration`Cmdlet 可启用已禁用的已注册会话配置，例如通过使用 `Disable-PSSessionConfiguration` 或 `Disable-PSRemoting` Cmdlet 或的 **AccessMode** 参数 `Register-PSSessionConfiguration` 。 这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。

如果没有参数，则将 `Enable-PSSessionConfiguration` 启用 " **Microsoft PowerShell** 配置"，这是用于会话的默认配置。

`Enable-PSSessionConfiguration` 从受影响的会话配置的安全描述符中删除 **Deny_All** 设置，启用接受任何 IP 地址上的请求的侦听器，并重新启动 WinRM 服务。 从 PowerShell 3.0 开始， `Enable-PSSessionConfiguration` 还将会话配置的 **Enabled** 属性的值 (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) 设置为 True。 但是，不 `Enable-PSSessionConfiguration` 会删除或更改 **Network_Deny_All** (`AccessMode=Local`) 安全描述符设置，只允许本地计算机的用户使用该会话配置。

## 示例

### 示例1：重新启用默认会话

此示例将在计算机上重新启用 **Microsoft PowerShell** 默认会话配置。

```powershell
Enable-PSSessionConfiguration
```

### 示例2：重新启用指定的会话

此示例将重新启用计算机上的 **MaintenanceShell** 和 **AdminShell** 会话配置。

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### 示例3：重新启用所有会话

此示例将重新启用计算机上的所有会话配置。 这些命令是等效的。
因此，您可以使用这两种方法。

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` 如果启用已启用的会话配置，则不会生成错误。

### 示例4：重新启用会话并指定新的安全描述符

此示例将重新启用 **MaintenanceShell** 会话配置，并为该配置指定新的安全描述符。

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETERS

### -Force

指示 cmdlet 不提示进行确认，并且将在无提示的情况下重启 WinRM 服务。 重新启动服务可使配置更改生效。

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

指定要启用的会话配置的名称。 输入一个或多个配置名称。
允许使用通配符。

还可以通过管道将包含配置名称或会话配置对象的字符串传递给 `Enable-PSSessionConfiguration` 。

如果省略此参数，则 `Enable-PSSessionConfiguration` 启用 **Microsoft PowerShell** 会话配置。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoServiceRestart

指示该 cmdlet 不会重新启动该服务。

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

### -SecurityDescriptorSddl

指定一个安全描述符，此 cmdlet 用来替换会话配置上的安全描述符。

如果省略此参数，则 `Enable-PSSessionConfiguration` 仅从安全描述符中删除 "拒绝所有" 项。

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

### -SkipNetworkProfileCheck

指示当计算机位于公用网络上时，此 cmdlet 将启用会话配置。 此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。 默认情况下， `Enable-PSSessionConfiguration` 在公用网络上失败。

此参数适用于 Windows 操作系统的客户端版本。 Windows 操作系统的服务器版本具有适用于公用网络的本地子网防火墙规则。 但是，如果在 Windows 操作系统的服务器版本上禁用了本地子网防火墙规则，则此参数将重新启用它。

若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 NetSecurity 模块中使用 cmdlet。 有关详细信息，请参阅 `Enable-PSRemoting`。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String

可以通过管道将会话配置对象或包含会话配置名称的字符串传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

若要使用此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

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
