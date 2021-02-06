---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 86a4370caccb43edf62af75337afb15f3fb63d7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597058"
---
# New-Event

## 摘要
创建新事件。

## SYNTAX

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`New-Event`Cmdlet 创建新的自定义事件。

你可以使用自定义事件通知用户你程序中的状态更改以及你的程序可以检测到的任何更改，包括硬件或系统状况、应用程序状态、磁盘状态、网络状态或后台作业的完成。

每次引发自定义事件时，它们都会自动添加到会话中的事件队列；你无需订阅这些事件。 但是，如果要将事件转发到本地会话或指定操作来响应事件，请使用 `Register-EngineEvent` cmdlet 订阅自定义事件。

订阅自定义事件时，会向会话中添加事件订阅服务器。 如果通过使用 cmdlet 取消事件订阅，将 `Unregister-Event` 从会话中删除事件订阅服务器和自定义事件。 如果不订阅自定义事件，若要删除事件，必须更改程序条件或关闭 PowerShell 会话。

## 示例

### 示例1：在事件队列中创建新事件

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

此命令在 PowerShell 事件队列中创建一个新事件。 它使用 **Windows Timer** 对象发送事件。

### 示例2：引发事件以响应另一个事件

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

此示例函数使用 `New-Event` cmdlet 引发事件以响应另一个事件。 该命令使用 `Register-ObjectEvent` cmdlet 来订阅创建新进程时引发的 (WMI) 事件的 Windows Management Instrumentation。 该命令使用 cmdlet 的 **Action** 参数来调用 `New-Event` cmdlet，该 cmdlet 将创建新的事件。

由于引发的事件会 `New-Event` 自动添加到 PowerShell 事件队列，因此你不需要注册该事件。

## PARAMETERS

### -EventArguments

指定包含事件选项的对象。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
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
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -发送方

指定引发事件的对象。 默认值为 PowerShell 引擎。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定新事件的名称。 此参数是必需的，并且在会话中必须是唯一的。

此参数的值显示在事件的 **SourceIdentifier** 属性中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.PSEventArgs

## 注释

Linux 或 macOS 平台上没有可用的事件源。

新自定义事件、事件订阅和事件队列仅存在于当前会话中。
如果关闭当前会话，将丢弃事件队列并取消事件订阅。

## 相关链接

[Get-Event](Get-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
