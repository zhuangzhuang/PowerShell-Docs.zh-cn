---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: b8f55770770fa9077f654d382818386cc480c638
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598267"
---
# Get-EventSubscriber

## 摘要
获取当前会话中的事件订阅服务器。

## SYNTAX

### BySource（默认值）

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### ById

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## DESCRIPTION

**Get-eventsubscriber** cmdlet 获取当前会话中的事件订阅服务器。

当你使用 Register 事件 cmdlet 订阅事件时，会将事件订阅者添加到 PowerShell 会话，并在每次引发事件时将你订阅的事件添加到事件队列中。
若要取消事件订阅，请使用 Unregister-Event cmdlet 删除事件订阅服务器。

## 示例

### 示例1：获取计时器事件的事件订阅者

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

此示例使用 **get-eventsubscriber** 命令获取计时器事件的事件订阅服务器。

第一个命令使用 New-Object cmdlet 创建计时器对象的实例。
它将新的计时器对象保存在 $Timer 变量中。

第二个命令使用 Get-Member cmdlet 来显示可用于计时器对象的事件。
该命令使用具有事件值的 **获取成员** Cmdlet 的类型参数。

第三个命令使用 Register-ObjectEvent cmdlet 注册计时器对象上的已用时间事件。

第四个命令使用 **get-eventsubscriber** cmdlet 获取已用事件的事件订阅服务器。

### 示例2：在事件订阅服务器的 Action 属性中使用 PSEventJob 中的动态模块

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

此示例演示如何使用事件订阅服务器的 Action 属性中的 **PSEventJob** 对象中的动态模块。

第一个命令使用 New-Object cmdlet 创建计时器对象。
第二个命令将计时器的间隔设置为 500（毫秒）。

第三个命令使用 Register-ObjectEvent cmdlet 注册计时器对象上的已用时间事件。
该命令包含处理事件的操作。
每当计时器时间间隔过后，将引发一个事件，而且运行操作中的命令。
在这种情况下，Get-Random cmdlet 将生成0到100之间的一个随机数，并将其保存在 $Random 变量中。
该事件的源标识符是 Timer.Random。

当你在 **register-objectevent** 命令中使用 *Action* 参数时，该命令将返回表示该操作的 **PSEventJob** 对象。

第四个命令启用计时器。

第五个命令使用 **get-eventsubscriber** cmdlet 来获取计时器的事件订阅服务器。随机事件。
它将事件订阅服务器对象保存在 $Subscriber 的变量中。

第六个命令显示事件订阅服务器对象的 Action 属性包含 **PSEventJob** 对象。
事实上，它包含 **register-objectevent** 命令返回的 **PSEventJob** 对象。

第七个命令使用 Format-List cmdlet 显示列表中 Action 属性中的 **PSEventJob** 对象的所有属性。
结果显示， **PSEventJob** 对象具有 Module 属性，该属性包含实现该操作的动态脚本模块。

剩余的命令使用调用运算符 ( # A0) 来调用模块中的命令，并显示 $Random 变量的值。
可以使用调用运算符来调用模块中的任何命令，包括未导出的命令。
在这种情况下，这些命令显示当已用时间事件发生时生成的随机数字。

有关模块的详细信息，请参阅 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

## PARAMETERS

### -Force

指示此 cmdlet 获取所有事件订阅服务器，包括使用 Register-objectevent、Register-wmievent 和 Register-engineevent 的 *SupportEvent* 参数隐藏的事件的订阅服务器。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定仅获取事件订阅服务器的 **SourceIdentifier** 属性值。
默认情况下， **get-eventsubscriber** 将获取会话中的所有事件订阅服务器。
不允许使用通配符。
此参数区分大小写。

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

### -SubscriptionId

指定此 cmdlet 获取的订阅标识符。
默认情况下， **get-eventsubscriber** 将获取会话中的所有事件订阅服务器。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.PSEventSubscriber

**Get-eventsubscriber** 返回表示每个事件订阅服务器的对象。

## 注释

* New-Event cmdlet 创建自定义事件，不生成订阅服务器。 因此， **get-eventsubscriber** cmdlet 将找不到这些事件的订阅服务器对象。 但是，如果使用 Register-EngineEvent cmdlet 订阅自定义事件 (以便转发事件或指定操作) ，则 **get-eventsubscriber** 将找到 **register-engineevent** 生成的订阅服务器。

  事件、事件订阅和事件队列仅存在于当前会话中。
如果关闭当前会话，将丢弃事件队列并取消事件订阅。

*

## 相关链接

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

