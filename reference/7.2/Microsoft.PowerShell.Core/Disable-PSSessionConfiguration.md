---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603802"
---
# Disable-PSSessionConfiguration

## 摘要
禁用本地计算机上的会话配置。

## SYNTAX

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Disable-PSSessionConfiguration`Cmdlet 可禁用本地计算机上的会话配置，从而防止所有用户使用会话配置创建用户管理的会话， (本地计算机上的 **pssession**) 。 这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。

从 PowerShell 3.0 开始， `Disable-PSSessionConfiguration` cmdlet 将会话配置的 **已启用** 设置 () 设置 `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` 为 False。

在 PowerShell 2.0 中， `Disable-PSSessionConfiguration` cmdlet 会将 **Deny_All** 条目添加到一个或多个已注册会话配置的安全描述符中。

如果没有参数， `Disable-PSSessionConfiguration` 则将禁用用于会话的默认配置。 除非用户指定其他配置，否则这将有效阻止本地和远程用户创建任何连接到计算机的会话。

若要禁用计算机上的所有会话配置，请使用 `Disable-PSRemoting` 。

## 示例

### 示例 1：禁用默认配置

此示例禁用了 Microsoft PowerShell 会话配置。

```powershell
Disable-PSSessionConfiguration
```

### 示例 2：禁用所有已注册的会话配置

此示例将禁用计算机上所有已注册的会话配置。

```powershell
Disable-PSSessionConfiguration -Name *
```

### 示例 3：按名称禁用会话配置

此示例将禁用名称以 Microsoft 开头的所有会话配置。 **Force** 参数取消了 cmdlet 中的所有用户提示。

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### 示例 4：通过使用管道禁用会话配置

此示例将禁用 **MaintenanceShell** 和 **AdminShell** 会话配置。 管道运算符 (|) 将的结果发送 `Get-PSSessionConfiguration` 到 `Disable-PSSessionConfiguration` 。

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### 示例 5：禁用会话配置的效果

此示例显示在运行之前和之后的权限 `Disable-PSSessionConfiguration` 以及禁用会话配置的效果。

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> 禁用该配置不会阻止你使用 cmdlet 更改配置 `Set-PSSessionConfiguration` 。 它仅阻止使用该配置。

## PARAMETERS

### -Force

强制运行命令而不要求用户确认。

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

指定要禁用的会话配置的名称数组。 输入一个或多个配置名称。 允许使用通配符。 还可以通过管道将包含配置名称或会话配置对象的字符串传递给 `Disable-PSSessionConfiguration` 。

如果省略此参数，则 `Disable-PSSessionConfiguration` 将禁用 Microsoft PowerShell 会话配置。

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

用于阻止重新启动 WSMan 服务。 不需要重新启动服务来禁用配置。

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

若要运行此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

## 相关链接

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
