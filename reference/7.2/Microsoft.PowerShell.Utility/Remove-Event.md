---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 3193de9020f2f54795bde9d5cce1bb86c4431ef9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598661"
---
# Remove-Event

## 摘要
从事件队列中删除事件。

## SYNTAX

### BySource（默认值）

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-Event`Cmdlet 从当前会话中的事件队列中删除事件。

此 cmdlet 仅删除当前位于队列中的事件。 若要取消事件注册或取消订阅，请使用 `Unregister-Event` cmdlet。

## 示例

### 示例1：按源标识符删除事件

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

此命令从事件队列中删除源标识符为 "进程" 的事件。

### 示例2：按事件标识符删除事件

```
PS C:\> Remove-Event -EventIdentifier 30
```

此命令从事件队列中删除事件 ID 为 30 的事件。

### 示例3：删除所有事件

```
PS C:\> Get-Event | Remove-Event
```

此命令从事件队列中删除所有事件。

## PARAMETERS

### -EventIdentifier

指定 cmdlet 删除的事件标识符。 每个命令中都需要 **EventIdentifier** 或 **SourceIdentifier** 参数。

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

指定此 cmdlet 从中删除事件的源标识符。 不允许使用通配符。 每个命令中都需要 **EventIdentifier** 或 **SourceIdentifier** 参数。

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
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

### System.Management.Automation.PSEventArgs

可以通过管道将事件传递 `Get-Event` 给 `Remove-Event` 。

## 输出

### 无

该 cmdlet 不生成任何输出。

## 注释

Linux 或 macOS 平台上没有可用的事件源。

事件、事件订阅和事件队列仅存在于当前会话中。 如果关闭当前会话，将丢弃事件队列并取消事件订阅。

## 相关链接

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
