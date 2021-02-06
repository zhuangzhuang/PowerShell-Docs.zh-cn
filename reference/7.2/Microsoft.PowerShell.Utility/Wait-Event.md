---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: caf2a1c80848d3140e7ad46fdf54dbe71886c633
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597431"
---
# Wait-Event

## 摘要
等待，直到在继续运行之前引发特定事件。

## SYNTAX

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Wait-Event`Cmdlet 将挂起脚本或函数的执行，直到引发特定事件。 在检测到事件后会继续执行。 若要取消等待，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。

此功能为事件的轮询提供了一种替代方法。 它还允许你通过两种不同的方式确定对事件的响应：

- 使用事件订阅的 **Action** 参数
- 等待事件返回，然后使用操作进行响应

## 示例

### 示例1：等待下一个事件

此示例将等待引发的下一个事件。

```powershell
Wait-Event
```

### 示例2：等待具有指定源标识符的事件

此示例将等待引发并且源标识符为 ProcessStarted 的下一个事件。

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### 示例3：等待计时器已用事件

此示例使用 `Wait-Event` cmdlet 等待为2000毫秒设置的计时器的计时器事件。

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### 示例4：在指定的超时后等待事件

此示例为引发并且源标识符为 **ProcessStarted** 的下一个事件等待最长90秒。 如果达到该指定时间，则等待结束。

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETERS

### -SourceIdentifier

指定此 cmdlet 等待事件的源标识符。
默认情况下， `Wait-Event` 等待任何事件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

指定等待事件发生的最长时间（以秒为单位） `Wait-Event` 。 默认值为 -1，表示无限期地等待。 提交命令时，将开始计时 `Wait-Event` 。

如果超过指定时间，则等待结束，并返回命令提示符，即使尚未引发事件也是如此。 不显示任何错误消息。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

## 输出

### System.Management.Automation.PSEventArgs

## 注释

事件、事件订阅和事件队列仅存在于当前会话中。 如果关闭当前会话，将丢弃事件队列并取消事件订阅。

## 相关链接

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

