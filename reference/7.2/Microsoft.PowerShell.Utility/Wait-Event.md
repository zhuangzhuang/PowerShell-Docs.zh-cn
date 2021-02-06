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
# <span data-ttu-id="1e5a7-102">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-102">Wait-Event</span></span>

## <span data-ttu-id="1e5a7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1e5a7-103">SYNOPSIS</span></span>
<span data-ttu-id="1e5a7-104">等待，直到在继续运行之前引发特定事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-104">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="1e5a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e5a7-105">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="1e5a7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1e5a7-106">DESCRIPTION</span></span>

<span data-ttu-id="1e5a7-107">`Wait-Event`Cmdlet 将挂起脚本或函数的执行，直到引发特定事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-107">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="1e5a7-108">在检测到事件后会继续执行。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-108">Execution resumes when the event is detected.</span></span> <span data-ttu-id="1e5a7-109">若要取消等待，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-109">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="1e5a7-110">此功能为事件的轮询提供了一种替代方法。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-110">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="1e5a7-111">它还允许你通过两种不同的方式确定对事件的响应：</span><span class="sxs-lookup"><span data-stu-id="1e5a7-111">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="1e5a7-112">使用事件订阅的 **Action** 参数</span><span class="sxs-lookup"><span data-stu-id="1e5a7-112">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="1e5a7-113">等待事件返回，然后使用操作进行响应</span><span class="sxs-lookup"><span data-stu-id="1e5a7-113">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="1e5a7-114">示例</span><span class="sxs-lookup"><span data-stu-id="1e5a7-114">EXAMPLES</span></span>

### <span data-ttu-id="1e5a7-115">示例1：等待下一个事件</span><span class="sxs-lookup"><span data-stu-id="1e5a7-115">Example 1: Wait for the next event</span></span>

<span data-ttu-id="1e5a7-116">此示例将等待引发的下一个事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-116">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="1e5a7-117">示例2：等待具有指定源标识符的事件</span><span class="sxs-lookup"><span data-stu-id="1e5a7-117">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="1e5a7-118">此示例将等待引发并且源标识符为 ProcessStarted 的下一个事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-118">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="1e5a7-119">示例3：等待计时器已用事件</span><span class="sxs-lookup"><span data-stu-id="1e5a7-119">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="1e5a7-120">此示例使用 `Wait-Event` cmdlet 等待为2000毫秒设置的计时器的计时器事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-120">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

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

### <span data-ttu-id="1e5a7-121">示例4：在指定的超时后等待事件</span><span class="sxs-lookup"><span data-stu-id="1e5a7-121">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="1e5a7-122">此示例为引发并且源标识符为 **ProcessStarted** 的下一个事件等待最长90秒。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-122">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="1e5a7-123">如果达到该指定时间，则等待结束。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-123">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="1e5a7-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e5a7-124">PARAMETERS</span></span>

### <span data-ttu-id="1e5a7-125">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="1e5a7-125">-SourceIdentifier</span></span>

<span data-ttu-id="1e5a7-126">指定此 cmdlet 等待事件的源标识符。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-126">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="1e5a7-127">默认情况下， `Wait-Event` 等待任何事件。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-127">By default, `Wait-Event` waits for any event.</span></span>

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

### <span data-ttu-id="1e5a7-128">-Timeout</span><span class="sxs-lookup"><span data-stu-id="1e5a7-128">-Timeout</span></span>

<span data-ttu-id="1e5a7-129">指定等待事件发生的最长时间（以秒为单位） `Wait-Event` 。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-129">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="1e5a7-130">默认值为 -1，表示无限期地等待。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-130">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="1e5a7-131">提交命令时，将开始计时 `Wait-Event` 。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-131">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="1e5a7-132">如果超过指定时间，则等待结束，并返回命令提示符，即使尚未引发事件也是如此。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-132">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="1e5a7-133">不显示任何错误消息。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-133">No error message is displayed.</span></span>

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

### <span data-ttu-id="1e5a7-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e5a7-134">CommonParameters</span></span>

<span data-ttu-id="1e5a7-135">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e5a7-136">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e5a7-137">输入</span><span class="sxs-lookup"><span data-stu-id="1e5a7-137">INPUTS</span></span>

### <span data-ttu-id="1e5a7-138">System.String</span><span class="sxs-lookup"><span data-stu-id="1e5a7-138">System.String</span></span>

## <span data-ttu-id="1e5a7-139">输出</span><span class="sxs-lookup"><span data-stu-id="1e5a7-139">OUTPUTS</span></span>

### <span data-ttu-id="1e5a7-140">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="1e5a7-140">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="1e5a7-141">注释</span><span class="sxs-lookup"><span data-stu-id="1e5a7-141">NOTES</span></span>

<span data-ttu-id="1e5a7-142">事件、事件订阅和事件队列仅存在于当前会话中。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-142">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="1e5a7-143">如果关闭当前会话，将丢弃事件队列并取消事件订阅。</span><span class="sxs-lookup"><span data-stu-id="1e5a7-143">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="1e5a7-144">相关链接</span><span class="sxs-lookup"><span data-stu-id="1e5a7-144">RELATED LINKS</span></span>

[<span data-ttu-id="1e5a7-145">Get-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-145">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="1e5a7-146">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="1e5a7-146">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="1e5a7-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="1e5a7-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="1e5a7-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="1e5a7-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="1e5a7-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="1e5a7-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="1e5a7-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="1e5a7-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="1e5a7-152">Wait-Event</span></span>](Wait-Event.md)

