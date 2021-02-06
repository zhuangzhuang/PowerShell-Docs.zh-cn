---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 4b275d489984f85aea401b781e38c80fbc4b2177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603593"
---
# Get-Event

## 摘要
获取事件队列中的事件。

## SYNTAX

### BySource（默认值）

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### ById

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Event` cmdlet 将获取当前会话的 PowerShell 事件队列中的事件。 可以获取所有事件，也可以使用 EventIdentifier 或 SourceIdentifier 参数指定事件。

当发生某个事件时，会将其添加到事件队列中。 事件队列包括已注册的事件、使用 cmdlet 创建的事件 `New-Event` ，以及 PowerShell 退出时引发的事件。 您可以使用 `Get-Event` 或 `Wait-Event` 来获取事件。

此 cmdlet 不会从“事件查看器”日志获取事件。 若要获取这些事件，请使用 `Get-WinEvent` 或 `Get-EventLog` 。

## 示例

### 示例 1：获取所有事件

```
PS C:\> Get-Event
```

此命令将获取事件队列中的所有事件。

### 示例 2：按源标识符获取事件

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

此命令将获取 SourceIdentifier 属性的值为 PowerShell.ProcessCreated 的事件。

### 示例 3：基于事件的生成时间获取事件

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

此示例显示了如何通过使用属性（而不是 SourceIdentifier）来获取事件。

第一个命令将获取事件队列中的所有事件，并将它们保存在 `$Events` 变量中。

第二个命令使用数组表示法来获取变量中数组的第一个 (0 索引) 事件 `$Events` 。 该命令使用管道运算符 (`|`) 将事件发送到 `Format-List` 命令，该命令将在列表中显示该事件的所有属性。 这使你可以检查事件对象的属性。

第三个命令演示如何使用 `Where-Object` cmdlet 来基于生成事件的时间获取事件。

### 示例 4：按标识符获取事件

```
PS C:\> Get-Event -EventIdentifier 2
```

此命令将获取事件标识符为 2 的事件。

## PARAMETERS

### -EventIdentifier

指定此 cmdlet 可为其获取事件的事件标识符。

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

指定此 cmdlet 可为其获取事件的源标识符。 默认值为事件队列中的所有事件。 不允许使用通配符。

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.PSEventArgs

`Get-Event` 返回每个事件的 **PSEventArgs** 对象。 若要查看此对象的说明，请键入 `Get-Help Get-Event -Full`，并查看帮助主题的“注释”部分。

## 注释

Linux 或 macOS 平台上没有可用的事件源。

事件、事件订阅和事件队列仅存在于当前会话中。 如果关闭当前会话，将丢弃事件队列并取消事件订阅。

`Get-Event`Cmdlet 将返回具有以下属性的 **PSEventArgs** 对象 (**PSEventArgs**) ：

- ComputerName。 发生该事件的计算机的名称。 仅当从远程计算机转发事件时，才填充此属性值。

- RunspaceId。 一个 GUID，用于唯一标识该事件发生时所在的会话。 仅当从远程计算机转发事件时，才填充此属性值。

- EventIdentifier。 一个整数 (Int32)，用于唯一标识当前会话中的事件通知。

- Sender。 生成该事件的对象。 在 **Action** 参数的值中， `$Sender` 自动变量包含发件人对象。

- SourceEventArgs。 派生自 EventArgs 的第一个参数（如果存在）。 例如，在计时器已使用事件中，签名的形式为对象发送方 **timers.elapsedeventargs** e， **SourceEventArgs** 属性将包含 **timers.elapsedeventargs**。 在 **Action** 参数的值中， `$EventArgs` 自动变量包含此值。

- SourceArgs。 原始事件签名的所有参数。 对于标准事件签名， `$Args[0]` 表示发送方， `$Args[1]` 表示 **SourceEventArgs**。 在 **Action** 参数的值中， `$Args` 自动变量包含此值。

- SourceIdentifier。 用于标识事件订阅的字符串。 在 **Action** 参数的值中，自动变量的 **SourceIdentifier** 属性 `$Event` 包含此值。

- TimeGenerated。 一个 **DateTime** 对象，用于表示事件的生成时间。
  在 **Action** 参数的值中，自动变量的 **TimeGenerated** 属性 `$Event` 包含此值。

- MessageData. 与事件订阅关联的数据。 当用户注册事件时，将指定此数据。 在 **Action** 参数的值中，自动变量的 **MessageData** 属性 `$Event` 包含此值。

## 相关链接

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
