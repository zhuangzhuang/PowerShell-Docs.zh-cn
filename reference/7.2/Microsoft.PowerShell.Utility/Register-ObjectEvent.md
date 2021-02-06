---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: 89f4d30df0dbc1b74ba28604ed686cad64a3a594
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596820"
---
# Register-ObjectEvent

## 摘要
订阅由 Microsoft .NET Framework 对象生成的事件。

## SYNTAX

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## DESCRIPTION

`Register-ObjectEvent`Cmdlet 订阅由本地计算机或远程计算机上的 .net 对象生成的事件。

当引发已订阅的事件时，它将添加到你的会话中的事件队列。 若要获取事件队列中的事件，请使用 `Get-Event` cmdlet。

您可以使用的参数 `Register-ObjectEvent` 来指定可帮助您在队列中标识事件的事件的属性值。 你还可以使用 **Action** 参数指定在引发订阅事件时要执行的操作，以及用于将远程事件发送到本地会话中的事件队列的 **转发** 参数。

订阅事件时，会向会话中添加一个事件订阅服务器。 若要获取会话中的事件订阅程序，请使用 `Get-EventSubscriber` cmdlet。 若要取消订阅，请使用 `Unregister-Event` cmdlet，该 cmdlet 将从会话中删除事件订阅程序。

## 示例

### 示例1：在新进程启动时订阅事件

此示例订阅新进程启动时生成的事件。

该命令使用 **ManagementEventWatcher** 对象获取 **EventArrived** 事件。 查询对象指定事件是 **Win32_Process** 类的实例创建事件。

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### 示例2：指定响应事件的操作

当你指定某项操作时，引发的事件不会添加到事件队列。 相反，操作将响应该事件。 在此示例中，当引发指示新进程已启动的实例创建事件时，将引发新的 **ProcessCreated** 事件。

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

操作使用 `$Sender` `$EventArgs` 仅为事件操作填充的和自动变量。

该 `Register-ObjectEvent` 命令返回一个作业对象，该对象表示作为后台作业运行的操作。 可以使用作业 cmdlet （如 `Get-Job` 和 `Receive-Job` ）来管理后台作业。 有关详细信息，请参阅 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)。

### 示例3：订阅远程计算机上的对象事件

此示例演示如何订阅远程计算机上的对象事件。 此示例使用 `Enable-ProcessCreationEvent` 在脚本文件中定义的函数 `ProcessCreationEvent.ps1` 。 此脚本可用于此示例中的所有计算机。

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

第一种方法是在两台远程计算机上创建 **pssession** ，并将其保存在 `$S` 变量中。 接下来，该 cmdlet 将在 `Invoke-Command` `ProcessCreationEvent.ps1` 中的每个 pssession 中运行该脚本 `$S` 。 此操作会 `Enable-ProcessCreationEvent` 在远程会话中创建函数。
最后，我们 `Enable-ProcessCreationEvent` 在远程会话中运行该函数。

 函数包含一个 `Register-ObjectEvent` 命令，该命令通过 **ManagementEventWatcher** 对象及其 **EventArrived** 事件订阅 **Win32_Process** 对象上的实例创建事件。

### 示例4：使用 PSEventJob 对象中的动态模块

此示例演示如何使用在事件注册中包含 **操作** 时创建的 **PSEventJob** 对象中的动态模块。 首先，我们 createand 并启用计时器对象，然后将计时器的间隔设置为 500 (毫秒) 。 `Register-ObjectEvent`Cmdlet 注册 timer 对象的已 **用** 事件。 **PSEventJob** 对象保存在 `$Job` 变量中，并在事件订阅服务器的 **Action** 属性中提供。 有关详细信息，请参阅 [get-eventsubscriber](Get-EventSubscriber.md)。

每当计时器时间间隔过后，将引发一个事件并执行该操作。 在这种情况下，该 `Get-Random` cmdlet 将生成0到100之间的一个随机数，并将其保存在 `$Random` 变量中。

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

**PSEventJob** 有一个 **Module** 属性，该属性包含实现该操作的动态脚本模块。 使用 call 运算符 (`&`) ，我们将在模块中调用命令以显示变量的值 `$Random` 。

有关模块的详细信息，请参阅 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

## PARAMETERS

### -Action

指定用于处理事件的命令。 **Action** 中的命令在引发事件时运行，而不是将该事件发送到事件队列。 用大括号 ({ }) 括起命令以形成脚本块。

**操作** 参数的值可以包括 `$Event` 、 `$EventSubscriber` 、、 `$Sender` `$EventArgs` 和 `$Args` 自动变量。 这些变量向 **操作** 脚本块提供有关事件的信息。 有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

指定操作时， `Register-ObjectEvent` 将返回表示该操作的事件作业对象。 你可以使用 Job cmdlet 来管理事件作业。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventName

指定要订阅的事件。

此参数的值必须是 .NET 对象公开的事件的名称。 例如， **ManagementEventWatcher** 类具有名为 **EventArrived** 的事件并已 **停止**。 若要查找事件的事件名称，请使用 `Get-Member` cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

指示该 cmdlet 将此订阅的事件发送到远程会话。 如果要在远程计算机或远程会话中注册事件，可使用此参数。

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

### -InputObject

指定生成事件的 .NET 对象。 输入包含该对象的变量，或键入获取该对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

指定可触发事件的最大次数。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

指定将与此事件订阅关联的任何额外数据。 此参数的值出现在与此订阅关联的所有事件的 MessageData 属性中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定你为订阅选择的名称。 你选择的名称必须在当前会话中唯一。 默认值为 PowerShell 分配的 GUID。

此参数的值出现在订阅服务器对象的 **SourceIdentifier** 属性的值中，以及与此订阅关联的所有事件对象。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

指示该 cmdlet 隐藏事件订阅。 当当前订阅是更复杂的事件注册机制的一部分并且不应单独发现时，请使用此参数。

若要查看或取消使用 **SupportEvent** 参数创建的订阅，请使用和 Cmdlet 的 **Force** 参数 `Get-EventSubscriber` `Unregister-Event` 。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给 `Register-ObjectEvent` 。

## 输出

### 无或 System.Management.Automation.PSEventJob

使用 **Action** 参数时，将 `Register-ObjectEvent` 返回 **PSEventJob** 对象。 否则，将不生成任何输出。

## 注释

事件、事件订阅和事件队列仅存在于当前会话中。 如果关闭当前会话，将丢弃事件队列并取消事件订阅。

## 相关链接

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

