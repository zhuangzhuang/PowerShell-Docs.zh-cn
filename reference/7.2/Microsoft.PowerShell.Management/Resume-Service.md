---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597255"
---
# Resume-Service

## 摘要
恢复一项或多项挂起（暂停的）服务。

## SYNTAX

### InputObject（默认值）

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 默认

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Resume-Service`Cmdlet 为每个指定的服务向 Windows 服务控制器发送一条恢复消息。 如果服务已挂起，则会恢复。 如果当前正在运行，则忽略该消息。 你可以通过服务名称或显示名称来指定服务，也可以使用 **InputObject** 参数传递表示要恢复的服务的服务对象。

## 示例

### 示例1：在本地计算机上恢复服务

```
PS C:\> Resume-Service "sens"
```

此命令在本地计算机上恢复系统事件通知服务。 服务名称在命令中由 sens 表示。 该命令使用 **name** 参数来指定服务的服务名称，但该命令省略了参数名称，因为参数名称是可选的。

### 示例2：恢复所有挂起的服务

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

此命令恢复计算机上所有挂起的服务。 `Get-Service`Cmdlet 命令获取计算机上的所有服务。 管道运算符 (`|`) 将结果传递给 `Where-Object` cmdlet，后者选择 **状态** 属性为 "已暂停" 的服务。 下一个管道运算符将结果发送到 `Resume-Service` ，后者将恢复暂停的服务。

在实际操作中，你将使用 **WhatIf** 参数来确定该命令的影响，然后再运行该命令。

## PARAMETERS

### -DisplayName

指定要恢复的服务的显示名称。
允许使用通配符。

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

### -Include

指定要恢复的服务。 此参数的值限定 **Name** 参数。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

指定表示要恢复的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

指定要恢复的服务的服务名称。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
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

如果指定 **PassThru** 参数，则此 cmdlet 将生成表示已恢复服务的 **ServiceController** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- 已暂停的服务的状态为 "已暂停"。 当服务恢复后，其状态为 "正在运行"。
- `Resume-Service` 仅当当前用户有权执行此操作时，才能控制服务。 如果某个命令不能正常工作，则可能你不具有所需的权限。
- 若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。
  服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
