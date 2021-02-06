---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: 64d927907f995613d3e2260e5476b406949bc1aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596851"
---
# Register-EngineEvent

## 摘要
订阅由 PowerShell 引擎和 cmdlet 生成的事件 `New-Event` 。

## SYNTAX

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Register-EngineEvent`Cmdlet 订阅由 PowerShell 引擎和 cmdlet 生成的事件 `New-Event` 。 使用 **SourceIdentifier** 参数来指定事件。

可以使用此 cmdlet 订阅由 cmdlet 生成的 **现有** 引擎事件和事件 `New-Event` 。 将这些事件自动添加到你的会话中的事件队列，而无需订阅。 但是，订阅可以转发事件、指定操作来响应事件，以及取消订阅。

当引发已订阅的事件时，它将添加到你的会话中的事件队列。 若要获取事件队列中的事件，请使用 `Get-Event` cmdlet。

当你订阅事件时，会向会话中添加一个事件订阅服务器。 若要获取会话中的事件订阅程序，请使用 `Get-EventSubscriber` cmdlet。 若要取消订阅，请使用 `Unregister-Event` cmdlet，该 cmdlet 将从会话中删除事件订阅程序。

## 示例

### 示例 1：在远程计算机上注册 PowerShell 引擎事件

此示例将在两台远程计算机上注册 PowerShell 引擎事件。

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S {
Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward
}
```

`New-PSSession` 在每台远程计算机上创建用户管理的会话 (PSSession) 。 `Invoke-Command` Cmdlet `Register-EngineEvent` 在远程会话中运行命令。
`Register-EngineEvent` 使用 **SourceIdentifier** 参数标识事件。 **Forward** 参数通知引擎将事件从远程会话转发到本地会话。

### 示例 2：Exiting 事件发生时执行指定的操作

此示例演示如何运行 `Register-EngineEvent` ，以便在发生 **PowerShell** 时执行特定的操作。

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

添加 SupportEvent 参数以隐藏事件订阅。 PowerShell 退出时，在这种情况下，退出会话中的命令历史记录将导出用户目录中的 XML 文件 `$Home` 。

### 示例3：创建并订阅用户定义的事件

此示例为源 **MyEventSource** 中的事件创建订阅。 这是一个用于监视作业进度的任意来源。 `Register-EngineEvent` 用于创建订阅。 **操作** 参数的脚本块会将事件数据记录到文本文件中。

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` 已创建作业 Id 18。 `Start-Job` 已创建作业 Id 19。 例如 #4 中，我们将删除事件订阅和作业，然后检查日志文件。

### 示例4：注销事件并清理作业

这是示例3的继续符。 在此示例中，我们将等待10秒钟，让几个事件发生。 然后取消注册事件订阅。

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

`Unregister-Event`Cmdlet 将停止与事件订阅关联的作业 (作业 Id 18) 。 作业 Id 19 仍在运行并创建新的事件。 我们使用 **作业** cmdlet 来停止作业并删除不需要的作业对象。 `Get-Content` 显示日志文件的内容。

## PARAMETERS

### -Action

指定用于处理事件的命令。 **Action** 中的命令在引发事件时运行，而不是将该事件发送到事件队列。 用大括号 ({ }) 括起命令以形成脚本块。

**操作** 参数的值可以包括 `$Event` 、 `$EventSubscriber` 、、 `$Sender` `$EventArgs` 和 `$Args` 自动变量，这些变量向 **操作** 脚本块提供有关事件的信息。 有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

指定操作时， `Register-EngineEvent` 将返回表示该操作的事件作业对象。 你可以使用 Job cmdlet 来管理事件作业。

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

### -Forward

指示该 cmdlet 将此订阅的事件发送到本地计算机上的会话。
如果要在远程计算机或远程会话中注册事件，可使用此参数。

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

### -MaxTriggerCount

指定为事件订阅执行操作的最大次数。

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

指定与事件关联的其他数据。 此参数的值显示在事件对象的 **MessageData** 属性中。

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

指定要订阅的事件的源标识符。 源标识符必须在当前会话中唯一。 此参数是必需的。

此参数的值显示在订阅服务器对象以及与此订阅关联的所有事件对象的 **SourceIdentifier** 属性值中。

该值特定于事件的源。 这可以是你创建的用于 cmdlet 的任意值 `New-Event` 。 PowerShell 引擎支持 **register-engineevent** 值 **PowerShell。正在退出** 和 **powershell**。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

指示该 cmdlet 隐藏事件订阅。 在当前订阅是更复杂的事件注册机制的一部分并且不应单独发现它时，添加此参数。

若要查看或取消使用 **SupportEvent** 参数创建的订阅，请将 **Force** 参数添加到 `Get-EventSubscriber` 或 `Unregister-Event` cmdlet。

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

不能通过管道将输入传递给 `Register-EngineEvent` 。

## 输出

### 无或 System.Management.Automation.PSEventJob

如果使用 **Action** 参数，则将 `Register-EngineEvent` 返回 **PSEventJob** 对象。 否则，将不生成任何输出。

## 注释

Linux 或 macOS 平台上没有可用的事件源。

事件、事件订阅和事件队列仅存在于当前会话中。 如果关闭当前会话，将丢弃事件队列并取消事件订阅。

## 相关链接

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
