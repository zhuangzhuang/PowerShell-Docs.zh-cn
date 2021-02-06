---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: f88e07e36ec7c6adf7f24e2c6e57ae5864eb1a60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596426"
---
# Restart-Service

## 摘要
停止并接着启动一个或更多服务。

## SYNTAX

### InputObject（默认值）

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 默认

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Restart-Service`Cmdlet 向 Windows 服务控制器发送一条停止消息，然后将一条消息发送到指定的服务。 如果一项服务已经停止，则它将启动而不通知你已发生了错误。 可以通过服务名称或显示名称来指定服务，也可以使用 **InputObject** 参数传递一个对象，该对象表示要重新启动的每个服务。

## 示例

### 示例1：在本地计算机上重新启动服务

```powershell
PS C:\> Restart-Service -Name winmgmt
```

此命令在本地计算机上重新启动 Windows Management Instrumentation 服务 (WinMgmt)。

### 示例2：排除服务

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

此命令重新启动显示名称以 "Net" 开头的服务，"Net Logon" 服务除外。

### 示例3：启动所有停止的网络服务

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

此命令启动计算机上所有停止的网络服务。

此命令使用 `Get-Service` cmdlet 来获取对象，这些对象表示服务名称以 "net" 开头的服务。 管道运算符 (`|`) 将服务对象发送给 `Where-Object` cmdlet，后者仅选择状态为 "已停止" 的服务。 另一个管道运算符将选定的服务发送到 `Restart-Service` 。

在实际操作中，你将使用 **WhatIf** 参数来确定该命令的影响，然后再运行该命令。

## PARAMETERS

### -DisplayName

指定要重新启动的服务的显示名称。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

指定此 cmdlet 省略的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

### -Include

指定此 cmdlet 重新启动的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

### -InputObject

指定表示要重新启动的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要重新启动的服务的服务名称。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PassThru

返回一个表示服务的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### System.ServiceProcess.ServiceController、System.String

可以通过管道将服务对象或包含服务名称的字符串传递给此 cmdlet。

## 输出

### 无、System.ServiceProcess.ServiceController

如果指定 **PassThru** 参数，则此 cmdlet 将生成表示重新启动的服务的 **system.serviceprocess. ServiceController** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- `Restart-Service` 仅当当前用户有权执行此操作时，才能控制服务。 如果某个命令不能正常工作，则可能你不具有所需的权限。
- 若要在系统中查找服务名称并显示服务名称，请键入 `Get-Service` ""。
  服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
