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
# <span data-ttu-id="e3b08-102">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="e3b08-102">Get-EventSubscriber</span></span>

## <span data-ttu-id="e3b08-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e3b08-103">SYNOPSIS</span></span>
<span data-ttu-id="e3b08-104">获取当前会话中的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-104">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="e3b08-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3b08-105">SYNTAX</span></span>

### <span data-ttu-id="e3b08-106">BySource（默认值）</span><span class="sxs-lookup"><span data-stu-id="e3b08-106">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="e3b08-107">ById</span><span class="sxs-lookup"><span data-stu-id="e3b08-107">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="e3b08-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3b08-108">DESCRIPTION</span></span>

<span data-ttu-id="e3b08-109">**Get-eventsubscriber** cmdlet 获取当前会话中的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-109">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="e3b08-110">当你使用 Register 事件 cmdlet 订阅事件时，会将事件订阅者添加到 PowerShell 会话，并在每次引发事件时将你订阅的事件添加到事件队列中。</span><span class="sxs-lookup"><span data-stu-id="e3b08-110">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="e3b08-111">若要取消事件订阅，请使用 Unregister-Event cmdlet 删除事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-111">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="e3b08-112">示例</span><span class="sxs-lookup"><span data-stu-id="e3b08-112">EXAMPLES</span></span>

### <span data-ttu-id="e3b08-113">示例1：获取计时器事件的事件订阅者</span><span class="sxs-lookup"><span data-stu-id="e3b08-113">Example 1: Get the event subscriber for a timer event</span></span>

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

<span data-ttu-id="e3b08-114">此示例使用 **get-eventsubscriber** 命令获取计时器事件的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-114">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="e3b08-115">第一个命令使用 New-Object cmdlet 创建计时器对象的实例。</span><span class="sxs-lookup"><span data-stu-id="e3b08-115">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="e3b08-116">它将新的计时器对象保存在 $Timer 变量中。</span><span class="sxs-lookup"><span data-stu-id="e3b08-116">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="e3b08-117">第二个命令使用 Get-Member cmdlet 来显示可用于计时器对象的事件。</span><span class="sxs-lookup"><span data-stu-id="e3b08-117">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="e3b08-118">该命令使用具有事件值的 **获取成员** Cmdlet 的类型参数。</span><span class="sxs-lookup"><span data-stu-id="e3b08-118">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="e3b08-119">第三个命令使用 Register-ObjectEvent cmdlet 注册计时器对象上的已用时间事件。</span><span class="sxs-lookup"><span data-stu-id="e3b08-119">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="e3b08-120">第四个命令使用 **get-eventsubscriber** cmdlet 获取已用事件的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-120">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="e3b08-121">示例2：在事件订阅服务器的 Action 属性中使用 PSEventJob 中的动态模块</span><span class="sxs-lookup"><span data-stu-id="e3b08-121">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

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

<span data-ttu-id="e3b08-122">此示例演示如何使用事件订阅服务器的 Action 属性中的 **PSEventJob** 对象中的动态模块。</span><span class="sxs-lookup"><span data-stu-id="e3b08-122">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="e3b08-123">第一个命令使用 New-Object cmdlet 创建计时器对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-123">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="e3b08-124">第二个命令将计时器的间隔设置为 500（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="e3b08-124">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="e3b08-125">第三个命令使用 Register-ObjectEvent cmdlet 注册计时器对象上的已用时间事件。</span><span class="sxs-lookup"><span data-stu-id="e3b08-125">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="e3b08-126">该命令包含处理事件的操作。</span><span class="sxs-lookup"><span data-stu-id="e3b08-126">The command includes an action that handles the event.</span></span>
<span data-ttu-id="e3b08-127">每当计时器时间间隔过后，将引发一个事件，而且运行操作中的命令。</span><span class="sxs-lookup"><span data-stu-id="e3b08-127">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="e3b08-128">在这种情况下，Get-Random cmdlet 将生成0到100之间的一个随机数，并将其保存在 $Random 变量中。</span><span class="sxs-lookup"><span data-stu-id="e3b08-128">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="e3b08-129">该事件的源标识符是 Timer.Random。</span><span class="sxs-lookup"><span data-stu-id="e3b08-129">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="e3b08-130">当你在 **register-objectevent** 命令中使用 *Action* 参数时，该命令将返回表示该操作的 **PSEventJob** 对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-130">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="e3b08-131">第四个命令启用计时器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-131">The fourth command enables the timer.</span></span>

<span data-ttu-id="e3b08-132">第五个命令使用 **get-eventsubscriber** cmdlet 来获取计时器的事件订阅服务器。随机事件。</span><span class="sxs-lookup"><span data-stu-id="e3b08-132">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="e3b08-133">它将事件订阅服务器对象保存在 $Subscriber 的变量中。</span><span class="sxs-lookup"><span data-stu-id="e3b08-133">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="e3b08-134">第六个命令显示事件订阅服务器对象的 Action 属性包含 **PSEventJob** 对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-134">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="e3b08-135">事实上，它包含 **register-objectevent** 命令返回的 **PSEventJob** 对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-135">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="e3b08-136">第七个命令使用 Format-List cmdlet 显示列表中 Action 属性中的 **PSEventJob** 对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="e3b08-136">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="e3b08-137">结果显示， **PSEventJob** 对象具有 Module 属性，该属性包含实现该操作的动态脚本模块。</span><span class="sxs-lookup"><span data-stu-id="e3b08-137">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="e3b08-138">剩余的命令使用调用运算符 ( # A0) 来调用模块中的命令，并显示 $Random 变量的值。</span><span class="sxs-lookup"><span data-stu-id="e3b08-138">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="e3b08-139">可以使用调用运算符来调用模块中的任何命令，包括未导出的命令。</span><span class="sxs-lookup"><span data-stu-id="e3b08-139">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="e3b08-140">在这种情况下，这些命令显示当已用时间事件发生时生成的随机数字。</span><span class="sxs-lookup"><span data-stu-id="e3b08-140">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="e3b08-141">有关模块的详细信息，请参阅 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="e3b08-141">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="e3b08-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3b08-142">PARAMETERS</span></span>

### <span data-ttu-id="e3b08-143">-Force</span><span class="sxs-lookup"><span data-stu-id="e3b08-143">-Force</span></span>

<span data-ttu-id="e3b08-144">指示此 cmdlet 获取所有事件订阅服务器，包括使用 Register-objectevent、Register-wmievent 和 Register-engineevent 的 *SupportEvent* 参数隐藏的事件的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-144">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

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

### <span data-ttu-id="e3b08-145">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="e3b08-145">-SourceIdentifier</span></span>

<span data-ttu-id="e3b08-146">指定仅获取事件订阅服务器的 **SourceIdentifier** 属性值。</span><span class="sxs-lookup"><span data-stu-id="e3b08-146">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="e3b08-147">默认情况下， **get-eventsubscriber** 将获取会话中的所有事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-147">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="e3b08-148">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="e3b08-148">Wildcards are not permitted.</span></span>
<span data-ttu-id="e3b08-149">此参数区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e3b08-149">This parameter is case-sensitive.</span></span>

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

### <span data-ttu-id="e3b08-150">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="e3b08-150">-SubscriptionId</span></span>

<span data-ttu-id="e3b08-151">指定此 cmdlet 获取的订阅标识符。</span><span class="sxs-lookup"><span data-stu-id="e3b08-151">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="e3b08-152">默认情况下， **get-eventsubscriber** 将获取会话中的所有事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-152">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

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

### <span data-ttu-id="e3b08-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3b08-153">CommonParameters</span></span>

<span data-ttu-id="e3b08-154">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e3b08-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3b08-155">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e3b08-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3b08-156">输入</span><span class="sxs-lookup"><span data-stu-id="e3b08-156">INPUTS</span></span>

### <span data-ttu-id="e3b08-157">无</span><span class="sxs-lookup"><span data-stu-id="e3b08-157">None</span></span>

<span data-ttu-id="e3b08-158">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e3b08-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e3b08-159">输出</span><span class="sxs-lookup"><span data-stu-id="e3b08-159">OUTPUTS</span></span>

### <span data-ttu-id="e3b08-160">System.Management.Automation.PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="e3b08-160">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="e3b08-161">**Get-eventsubscriber** 返回表示每个事件订阅服务器的对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-161">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="e3b08-162">注释</span><span class="sxs-lookup"><span data-stu-id="e3b08-162">NOTES</span></span>

* <span data-ttu-id="e3b08-163">New-Event cmdlet 创建自定义事件，不生成订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-163">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="e3b08-164">因此， **get-eventsubscriber** cmdlet 将找不到这些事件的订阅服务器对象。</span><span class="sxs-lookup"><span data-stu-id="e3b08-164">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="e3b08-165">但是，如果使用 Register-EngineEvent cmdlet 订阅自定义事件 (以便转发事件或指定操作) ，则 **get-eventsubscriber** 将找到 **register-engineevent** 生成的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b08-165">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="e3b08-166">事件、事件订阅和事件队列仅存在于当前会话中。</span><span class="sxs-lookup"><span data-stu-id="e3b08-166">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="e3b08-167">如果关闭当前会话，将丢弃事件队列并取消事件订阅。</span><span class="sxs-lookup"><span data-stu-id="e3b08-167">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="e3b08-168">相关链接</span><span class="sxs-lookup"><span data-stu-id="e3b08-168">RELATED LINKS</span></span>

[<span data-ttu-id="e3b08-169">Get-Event</span><span class="sxs-lookup"><span data-stu-id="e3b08-169">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="e3b08-170">New-Event</span><span class="sxs-lookup"><span data-stu-id="e3b08-170">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="e3b08-171">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="e3b08-171">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="e3b08-172">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="e3b08-172">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="e3b08-173">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="e3b08-173">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="e3b08-174">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="e3b08-174">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="e3b08-175">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="e3b08-175">Wait-Event</span></span>](Wait-Event.md)

