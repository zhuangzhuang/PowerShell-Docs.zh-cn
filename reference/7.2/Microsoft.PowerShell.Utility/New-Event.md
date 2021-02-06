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
# <span data-ttu-id="0f9ff-102">New-Event</span><span class="sxs-lookup"><span data-stu-id="0f9ff-102">New-Event</span></span>

## <span data-ttu-id="0f9ff-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0f9ff-103">SYNOPSIS</span></span>
<span data-ttu-id="0f9ff-104">创建新事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-104">Creates a new event.</span></span>

## <span data-ttu-id="0f9ff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0f9ff-105">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="0f9ff-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0f9ff-106">DESCRIPTION</span></span>

<span data-ttu-id="0f9ff-107">`New-Event`Cmdlet 创建新的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-107">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="0f9ff-108">你可以使用自定义事件通知用户你程序中的状态更改以及你的程序可以检测到的任何更改，包括硬件或系统状况、应用程序状态、磁盘状态、网络状态或后台作业的完成。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-108">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="0f9ff-109">每次引发自定义事件时，它们都会自动添加到会话中的事件队列；你无需订阅这些事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-109">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="0f9ff-110">但是，如果要将事件转发到本地会话或指定操作来响应事件，请使用 `Register-EngineEvent` cmdlet 订阅自定义事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-110">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="0f9ff-111">订阅自定义事件时，会向会话中添加事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-111">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="0f9ff-112">如果通过使用 cmdlet 取消事件订阅，将 `Unregister-Event` 从会话中删除事件订阅服务器和自定义事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-112">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="0f9ff-113">如果不订阅自定义事件，若要删除事件，必须更改程序条件或关闭 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-113">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="0f9ff-114">示例</span><span class="sxs-lookup"><span data-stu-id="0f9ff-114">EXAMPLES</span></span>

### <span data-ttu-id="0f9ff-115">示例1：在事件队列中创建新事件</span><span class="sxs-lookup"><span data-stu-id="0f9ff-115">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="0f9ff-116">此命令在 PowerShell 事件队列中创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-116">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="0f9ff-117">它使用 **Windows Timer** 对象发送事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-117">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="0f9ff-118">示例2：引发事件以响应另一个事件</span><span class="sxs-lookup"><span data-stu-id="0f9ff-118">Example 2: Raise an event in response to another event</span></span>

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

<span data-ttu-id="0f9ff-119">此示例函数使用 `New-Event` cmdlet 引发事件以响应另一个事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-119">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="0f9ff-120">该命令使用 `Register-ObjectEvent` cmdlet 来订阅创建新进程时引发的 (WMI) 事件的 Windows Management Instrumentation。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-120">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="0f9ff-121">该命令使用 cmdlet 的 **Action** 参数来调用 `New-Event` cmdlet，该 cmdlet 将创建新的事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-121">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="0f9ff-122">由于引发的事件会 `New-Event` 自动添加到 PowerShell 事件队列，因此你不需要注册该事件。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-122">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="0f9ff-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0f9ff-123">PARAMETERS</span></span>

### <span data-ttu-id="0f9ff-124">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="0f9ff-124">-EventArguments</span></span>

<span data-ttu-id="0f9ff-125">指定包含事件选项的对象。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-125">Specifies an object that contains options for the event.</span></span>

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

### <span data-ttu-id="0f9ff-126">-MessageData</span><span class="sxs-lookup"><span data-stu-id="0f9ff-126">-MessageData</span></span>

<span data-ttu-id="0f9ff-127">指定与事件关联的其他数据。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-127">Specifies additional data associated with the event.</span></span> <span data-ttu-id="0f9ff-128">此参数的值显示在事件对象的 **MessageData** 属性中。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-128">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

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

### <span data-ttu-id="0f9ff-129">-发送方</span><span class="sxs-lookup"><span data-stu-id="0f9ff-129">-Sender</span></span>

<span data-ttu-id="0f9ff-130">指定引发事件的对象。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-130">Specifies the object that raises the event.</span></span> <span data-ttu-id="0f9ff-131">默认值为 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-131">The default is the PowerShell engine.</span></span>

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

### <span data-ttu-id="0f9ff-132">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="0f9ff-132">-SourceIdentifier</span></span>

<span data-ttu-id="0f9ff-133">指定新事件的名称。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-133">Specifies a name for the new event.</span></span> <span data-ttu-id="0f9ff-134">此参数是必需的，并且在会话中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-134">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="0f9ff-135">此参数的值显示在事件的 **SourceIdentifier** 属性中。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-135">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

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

### <span data-ttu-id="0f9ff-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0f9ff-136">CommonParameters</span></span>

<span data-ttu-id="0f9ff-137">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0f9ff-138">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0f9ff-139">输入</span><span class="sxs-lookup"><span data-stu-id="0f9ff-139">INPUTS</span></span>

### <span data-ttu-id="0f9ff-140">无</span><span class="sxs-lookup"><span data-stu-id="0f9ff-140">None</span></span>

<span data-ttu-id="0f9ff-141">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0f9ff-142">输出</span><span class="sxs-lookup"><span data-stu-id="0f9ff-142">OUTPUTS</span></span>

### <span data-ttu-id="0f9ff-143">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="0f9ff-143">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="0f9ff-144">注释</span><span class="sxs-lookup"><span data-stu-id="0f9ff-144">NOTES</span></span>

<span data-ttu-id="0f9ff-145">Linux 或 macOS 平台上没有可用的事件源。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-145">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="0f9ff-146">新自定义事件、事件订阅和事件队列仅存在于当前会话中。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-146">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="0f9ff-147">如果关闭当前会话，将丢弃事件队列并取消事件订阅。</span><span class="sxs-lookup"><span data-stu-id="0f9ff-147">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="0f9ff-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="0f9ff-148">RELATED LINKS</span></span>

[<span data-ttu-id="0f9ff-149">Get-Event</span><span class="sxs-lookup"><span data-stu-id="0f9ff-149">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="0f9ff-150">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="0f9ff-150">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="0f9ff-151">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="0f9ff-151">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="0f9ff-152">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="0f9ff-152">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="0f9ff-153">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="0f9ff-153">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="0f9ff-154">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="0f9ff-154">Wait-Event</span></span>](Wait-Event.md)
