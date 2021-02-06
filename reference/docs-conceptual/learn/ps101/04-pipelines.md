---
title: 准确描述和管道
description: PowerShell 单行命令是一个用于完成单个任务的连续管道，其中包含多个命令。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 1483ec6b76d17c3dd081356ecff85a929fc43e2c
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99603573"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="6018b-103">第 4 章 - 单行命令和管道</span><span class="sxs-lookup"><span data-stu-id="6018b-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="6018b-104">当我第一次开始学习 PowerShell 时，如果无法使用 PowerShell 单行命令完成任务，我会回到 GUI。</span><span class="sxs-lookup"><span data-stu-id="6018b-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="6018b-105">随着时间的推移，我逐渐掌握了编写脚本、函数和模块的技能。</span><span class="sxs-lookup"><span data-stu-id="6018b-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="6018b-106">不要因在 Internet 上看到的一些更高级示例而不知所措。</span><span class="sxs-lookup"><span data-stu-id="6018b-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="6018b-107">没有人一开始就会使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6018b-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="6018b-108">我们都曾是初学者。</span><span class="sxs-lookup"><span data-stu-id="6018b-108">We were all beginners at one time.</span></span>

<span data-ttu-id="6018b-109">对于那些仍然使用 GUI 进行管理的人，我有一些建议：在管理工作站上安装管理工具，并远程管理服务器。</span><span class="sxs-lookup"><span data-stu-id="6018b-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="6018b-110">这样，服务器运行的是 GUI 还是操作系统的 Server Core 安装就无关紧要了。</span><span class="sxs-lookup"><span data-stu-id="6018b-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="6018b-111">它将帮助你准备使用 PowerShell 远程管理服务器。</span><span class="sxs-lookup"><span data-stu-id="6018b-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="6018b-112">与上一章一样，请确保在 Windows 10 实验室环境计算机上继续操作。</span><span class="sxs-lookup"><span data-stu-id="6018b-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="6018b-113">单行命令</span><span class="sxs-lookup"><span data-stu-id="6018b-113">One-Liners</span></span>

<span data-ttu-id="6018b-114">PowerShell one 命令是一种连续管道，不一定是一条物理线路上的命令。</span><span class="sxs-lookup"><span data-stu-id="6018b-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that's on one physical line.</span></span> <span data-ttu-id="6018b-115">并非一个物理行上的所有命令都是单行命令。</span><span class="sxs-lookup"><span data-stu-id="6018b-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="6018b-116">即使以下命令位于多个物理行上，它也是 PowerShell 单行命令，因为它是一个连续管道。</span><span class="sxs-lookup"><span data-stu-id="6018b-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="6018b-117">它可以写在一个物理行上，但我已选择在管道符号处换行。</span><span class="sxs-lookup"><span data-stu-id="6018b-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="6018b-118">管道符号是 PowerShell 中允许自然换行处的某个字符。</span><span class="sxs-lookup"><span data-stu-id="6018b-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="6018b-119">自然换行可以出现在常用字符处，包括逗号 (`,`) 和方左括号 (`[`)、大括号 (`{`) 和圆括号 (`(`)。</span><span class="sxs-lookup"><span data-stu-id="6018b-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="6018b-120">其他不太常见的字符包括分号 (`;`)、等于号 (`=`) 以及左单引号和双引号（`'`、`"`）。</span><span class="sxs-lookup"><span data-stu-id="6018b-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="6018b-121">将反引号 (`` ` ``) 或重音符用作续行符是一个有争议的话题。</span><span class="sxs-lookup"><span data-stu-id="6018b-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="6018b-122">建议尽量避免这样做。</span><span class="sxs-lookup"><span data-stu-id="6018b-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="6018b-123">我经常会看到使用反引号编写的 PowerShell 命令紧跟在自然换行符之后。</span><span class="sxs-lookup"><span data-stu-id="6018b-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="6018b-124">没有理由把它放在那里。</span><span class="sxs-lookup"><span data-stu-id="6018b-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="6018b-125">上面两个示例中所示的命令在 PowerShell 控制台中正常工作。</span><span class="sxs-lookup"><span data-stu-id="6018b-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="6018b-126">但如果尝试在 PowerShell ISE 的控制台窗格中运行它们，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="6018b-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="6018b-127">PowerShell ISE 的控制台窗格不会等待命令的其余部分在下一行（如 PowerShell 控制台）中输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="6018b-128">要避免 PowerShell ISE 的控制台窗格中出现此问题，请使用 <kbd>Shift</kbd>+<kbd>Enter</kbd>，而不是只是在继续执行另一行上的命令时按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="6018b-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="6018b-129">下一个示例不是 PowerShell 单行命令，因为它不是一个连续管道。</span><span class="sxs-lookup"><span data-stu-id="6018b-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="6018b-130">它是一行上的两个单独命令，用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="6018b-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="6018b-131">许多编程和脚本语言要求在每一行的末尾使用分号。</span><span class="sxs-lookup"><span data-stu-id="6018b-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="6018b-132">尽管可以在 PowerShell 中以这种方法使用它们，但不建议这样做，因为它们不是必需的。</span><span class="sxs-lookup"><span data-stu-id="6018b-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="6018b-133">筛选左侧</span><span class="sxs-lookup"><span data-stu-id="6018b-133">Filtering Left</span></span>

<span data-ttu-id="6018b-134">本章中所示的命令结果已筛选为一个子集。</span><span class="sxs-lookup"><span data-stu-id="6018b-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="6018b-135">例如，`Get-Service` 与 Name 参数一起使用，筛选返回的服务列表，以仅显示 Windows 时间服务。</span><span class="sxs-lookup"><span data-stu-id="6018b-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="6018b-136">在管道中，你始终希望尽快将结果筛选为你要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="6018b-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="6018b-137">可使用第一个命令或最左侧命令的参数来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="6018b-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="6018b-138">这有时称为“筛选左侧”。</span><span class="sxs-lookup"><span data-stu-id="6018b-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="6018b-139">下面的示例使用 `Get-Service` 的 Name 参数来立即筛选结果，以仅显示 Windows 时间服务。</span><span class="sxs-lookup"><span data-stu-id="6018b-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="6018b-140">通过管道将命令传递到 `Where-Object` 来执行筛选的例子很常见。</span><span class="sxs-lookup"><span data-stu-id="6018b-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="6018b-141">第一个示例筛选源，只返回 Windows 时间服务的结果。</span><span class="sxs-lookup"><span data-stu-id="6018b-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="6018b-142">第二个示例返回所有服务，然后通过管道将它们传递到另一个命令来执行筛选。</span><span class="sxs-lookup"><span data-stu-id="6018b-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="6018b-143">虽然在本例中这似乎不是什么大问题，但是想象一下，如果你正在查询 Active Directory 用户列表。</span><span class="sxs-lookup"><span data-stu-id="6018b-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="6018b-144">你真的想要从 Active Directory 返回数千个用户帐户的信息，而只是通过管道将它们传递到另一个命令，从而筛选出一个很小的子集吗？</span><span class="sxs-lookup"><span data-stu-id="6018b-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="6018b-145">我的建议是始终筛选左侧，即使它似乎并不重要。</span><span class="sxs-lookup"><span data-stu-id="6018b-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="6018b-146">你会非常习惯它，并在真正需要时自动筛选左侧。</span><span class="sxs-lookup"><span data-stu-id="6018b-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="6018b-147">曾有人告诉我，指定的命令顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="6018b-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="6018b-148">这与事实相差甚远。</span><span class="sxs-lookup"><span data-stu-id="6018b-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="6018b-149">执行筛选时，指定命令的顺序确实很重要。</span><span class="sxs-lookup"><span data-stu-id="6018b-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="6018b-150">例如，假设你使用 `Select-Object` 仅选择几个属性，并使用 `Where-Object` 筛选不在选择内容中的属性。</span><span class="sxs-lookup"><span data-stu-id="6018b-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="6018b-151">在这种情况下，必须首先进行筛选，否则在尝试执行筛选时，该属性将不存在于管道中。</span><span class="sxs-lookup"><span data-stu-id="6018b-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="6018b-152">上一示例中的命令不会返回任何结果，因为当 `Select-Object` 的结果通过管道传递到 `Where-Object` 时，CanStopAndContinue 属性不存在。</span><span class="sxs-lookup"><span data-stu-id="6018b-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="6018b-153">该特定属性未被“选定”。</span><span class="sxs-lookup"><span data-stu-id="6018b-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="6018b-154">从本质上讲，它已被筛除了。反转 `Select-Object` 和 `Where-Object` 的顺序将产生所需结果。</span><span class="sxs-lookup"><span data-stu-id="6018b-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="6018b-155">管道</span><span class="sxs-lookup"><span data-stu-id="6018b-155">The Pipeline</span></span>

<span data-ttu-id="6018b-156">正如你在本书迄今为止展示的许多示例中所看到的那样，很多时候，一个命令的输出可以用作另一个命令的输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="6018b-157">在第 3 章中，`Get-Member` 用于确定命令所生成的对象类型。</span><span class="sxs-lookup"><span data-stu-id="6018b-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="6018b-158">第 3 章还介绍了如何使用 `Get-Command` 的 ParameterType 参数来确定哪些命令接受该类型的输入，尽管不一定是通过管道输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="6018b-159">根据命令提供帮助的程度，它可能包含 INPUTS 和 OUTPUTS 部分 。</span><span class="sxs-lookup"><span data-stu-id="6018b-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="6018b-160">之前的结果中只显示了帮助的相关部分。</span><span class="sxs-lookup"><span data-stu-id="6018b-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="6018b-161">正如你所看到的，INPUTS 部分表明，ServiceController 或 String 对象可以通过管道传递到 `Stop-Service` cmdlet  。</span><span class="sxs-lookup"><span data-stu-id="6018b-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="6018b-162">它不会告诉你哪些参数接受该类型的输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="6018b-163">确定该信息的最简单方法之一是查看完整版本的 `Stop-Service` cmdlet 帮助中的不同参数。</span><span class="sxs-lookup"><span data-stu-id="6018b-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="6018b-164">同样，我仅在以前的结果集中显示了帮助的相关部分。</span><span class="sxs-lookup"><span data-stu-id="6018b-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="6018b-165">请注意，DisplayName 参数不接受管道输入，InputObject 参数按 ServiceController 对象的值接受管道输入，而 Name 参数按 String 对象的值接受管道输入      。</span><span class="sxs-lookup"><span data-stu-id="6018b-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="6018b-166">它还按属性名称接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="6018b-167">当参数按属性名称和按值接受管道输入时，将始终首先尝试按值接受。</span><span class="sxs-lookup"><span data-stu-id="6018b-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="6018b-168">如果按值接受管道输入失败，则会尝试按属性名称接受管道输入 。</span><span class="sxs-lookup"><span data-stu-id="6018b-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="6018b-169">按值接受管道输入会产生误导。</span><span class="sxs-lookup"><span data-stu-id="6018b-169">**By value** is a little misleading.</span></span> <span data-ttu-id="6018b-170">我更喜欢按类型调用它。</span><span class="sxs-lookup"><span data-stu-id="6018b-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="6018b-171">这意味着，如果通过管道将生成 ServiceController 对象类型的命令结果传递到 `Stop-Service`，则会将该输入绑定到 InputObject 参数 。</span><span class="sxs-lookup"><span data-stu-id="6018b-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="6018b-172">但如果通过管道将生成 String 输出的命令结果传递到 `Stop-Service`，则将其绑定到 Name 参数 。</span><span class="sxs-lookup"><span data-stu-id="6018b-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="6018b-173">如果通过管道将不生成 ServiceController 或 String 对象的命令结果传递到 `Stop-Service`，但该命令确实生成了包含名为 Name 的属性的输出，则它会将输出的 Name 属性绑定到 `Stop-Service` 的 Name 参数    。</span><span class="sxs-lookup"><span data-stu-id="6018b-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="6018b-174">确定 `Get-Service` 命令生成的输出类型。</span><span class="sxs-lookup"><span data-stu-id="6018b-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="6018b-175">`Get-Service` 生成 ServiceController 对象类型。</span><span class="sxs-lookup"><span data-stu-id="6018b-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="6018b-176">正如你之前在帮助中看到的那样，`Stop-Service` 的 InputObject 参数通过管道按值（按类型）接受 ServiceController 对象  。</span><span class="sxs-lookup"><span data-stu-id="6018b-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="6018b-177">这意味着，当 `Get-Service` cmdlet 的结果通过管道传递到 `Stop-Service` 时，这些结果将绑定到 `Stop-Service` 的 InputObject 参数。</span><span class="sxs-lookup"><span data-stu-id="6018b-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="6018b-178">现在，尝试字符串输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-178">Now to try string input.</span></span> <span data-ttu-id="6018b-179">通过管道将 `w32time` 传递到 `Get-Member`，以确认它是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="6018b-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="6018b-180">如前面的帮助中所示，通过管道将字符串传递到 `Stop-Service` 会将其按值绑定到 `Stop-Service` 的 Name 参数 。</span><span class="sxs-lookup"><span data-stu-id="6018b-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="6018b-181">通过管道将 `w32time` 传递到 `Stop-Service`，以进行测试。</span><span class="sxs-lookup"><span data-stu-id="6018b-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="6018b-182">请注意，在上面的示例中，我在字符串 `w32time` 两侧使用了单引号。</span><span class="sxs-lookup"><span data-stu-id="6018b-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="6018b-183">在 PowerShell 中，应始终使用单引号而不是双引号，除非带引号的字符串的内容包含需要扩展为其实际值的变量。</span><span class="sxs-lookup"><span data-stu-id="6018b-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="6018b-184">通过使用单引号，PowerShell 不必分析引号中包含的内容，因此可稍微加快代码运行速度。</span><span class="sxs-lookup"><span data-stu-id="6018b-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="6018b-185">按 `Stop-Service` 的 Name 参数的属性名称创建自定义对象，以测试管道输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

<span data-ttu-id="6018b-186">CustomObject 变量的内容是 PSCustomObject 对象类型，并且它包含名为 Name 的属性  。</span><span class="sxs-lookup"><span data-stu-id="6018b-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="6018b-187">如果要在 `$CustomObject` 变量两边使用引号，则需要使用双引号。</span><span class="sxs-lookup"><span data-stu-id="6018b-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="6018b-188">否则，如果使用单引号，则会将文本字符串 `$CustomObject` 通过管道传递到 `Get-Member`，而不是传递变量包含的值。</span><span class="sxs-lookup"><span data-stu-id="6018b-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="6018b-189">尽管将 `$CustomObject` 的内容通过管道传递到 `Stop-Service` cmdlet 会将该内容绑定到 Name 参数，但这次它会按属性名称绑定，而不是按值，因为 `$CustomObject` 的内容是一个具有名为 Name 的属性的对象   。</span><span class="sxs-lookup"><span data-stu-id="6018b-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="6018b-190">在此示例中，我使用其他属性名称（如 Service）创建了另一个自定义对象。</span><span class="sxs-lookup"><span data-stu-id="6018b-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="6018b-191">尝试通过管道将 `$CustomObject` 传递到 `Stop-Service` 时，会产生错误，因为它不会生成 ServiceController 或 String 对象，并且没有名为 Name 的属性  。</span><span class="sxs-lookup"><span data-stu-id="6018b-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="6018b-192">如果一个命令的输出与另一个命令的管道输入选项不相符，则可以使用 `Select-Object` 重命名属性，以便正确地配置属性。</span><span class="sxs-lookup"><span data-stu-id="6018b-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="6018b-193">在此示例中，使用 `Select-Object` 将 Service 属性重命名为名为 Name 的属性 。</span><span class="sxs-lookup"><span data-stu-id="6018b-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="6018b-194">此示例的语法最初看来可能有点复杂。</span><span class="sxs-lookup"><span data-stu-id="6018b-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="6018b-195">我所认识到的是，永远都无法通过复制和粘贴代码学会语法。</span><span class="sxs-lookup"><span data-stu-id="6018b-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="6018b-196">花些时间键入代码。</span><span class="sxs-lookup"><span data-stu-id="6018b-196">Take the time to type the code in.</span></span> <span data-ttu-id="6018b-197">多试几次之后，就可成为第二天性。</span><span class="sxs-lookup"><span data-stu-id="6018b-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="6018b-198">拥有多个显示器是一项巨大的优势，因为你可以在一个屏幕上显示示例代码，然后在另一个屏幕上键入该代码。</span><span class="sxs-lookup"><span data-stu-id="6018b-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="6018b-199">有时，你可能需要使用不接受管道输入的参数。</span><span class="sxs-lookup"><span data-stu-id="6018b-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="6018b-200">下面的示例演示如何使用一个命令的输出作为另一个命令的输入。</span><span class="sxs-lookup"><span data-stu-id="6018b-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="6018b-201">首先将几个 Windows 服务的显示名称保存到一个文本文件中。</span><span class="sxs-lookup"><span data-stu-id="6018b-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="6018b-202">可以运行命令，在括号中提供所需输出，作为需要输入的命令的参数值。</span><span class="sxs-lookup"><span data-stu-id="6018b-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="6018b-203">这就像代数中的运算顺序（如果你还记得其运算方式）。</span><span class="sxs-lookup"><span data-stu-id="6018b-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="6018b-204">括号内的命令始终在外部的命令之前运行。</span><span class="sxs-lookup"><span data-stu-id="6018b-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="6018b-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6018b-205">PowerShellGet</span></span>

<span data-ttu-id="6018b-206">PowerShellGet 是一个 PowerShell 模块，其中包含用于向/从 NuGet 存储库发现、安装、发布和更新 PowerShell 模块（以及其他项目）的命令。</span><span class="sxs-lookup"><span data-stu-id="6018b-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="6018b-207">PowerShellGet 随 PowerShell 版本 5.0 及更高版本提供。</span><span class="sxs-lookup"><span data-stu-id="6018b-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="6018b-208">对于 PowerShell 版本 3.0 及更高版本，它可以作为单独的下载提供。</span><span class="sxs-lookup"><span data-stu-id="6018b-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="6018b-209">Microsoft 托管称为 [PowerShell 库][]的联机 NuGet 存储库。</span><span class="sxs-lookup"><span data-stu-id="6018b-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="6018b-210">尽管此存储库由 Microsoft 托管，但存储库中包含的大多数模块不是由 Microsoft 编写的。</span><span class="sxs-lookup"><span data-stu-id="6018b-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="6018b-211">对于从 PowerShell 库获取的任何代码，应先在独立的测试环境中对其进行全面的评审，然后再考虑其是否适用于生产环境。</span><span class="sxs-lookup"><span data-stu-id="6018b-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="6018b-212">大多数公司都需要托管自己的内部专用 NuGet 存储库，在这些存储库中，他们可以发布仅供内部使用的模块以及从其他源下载的模块（已验证其并非恶意模块）。</span><span class="sxs-lookup"><span data-stu-id="6018b-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="6018b-213">使用 PowerShellGet 模块中包含的 `Find-Module` cmdlet，在 PowerShell 库中查找我编写的名为 MrToolkit 的模块。</span><span class="sxs-lookup"><span data-stu-id="6018b-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="6018b-214">第一次使用 PowerShellGet 模块中的某个命令时，系统将提示你安装 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6018b-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="6018b-215">要安装 MrToolkit 模块，请将上一条命令通过管道传递到 `Install-Module`。</span><span class="sxs-lookup"><span data-stu-id="6018b-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="6018b-216">由于 PowerShell 库是不受信任的存储库，因此系统会提示你同意安装该模块。</span><span class="sxs-lookup"><span data-stu-id="6018b-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="6018b-217">查找管道输入的简单方法</span><span class="sxs-lookup"><span data-stu-id="6018b-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="6018b-218">MrToolkit 模块包含一个名为 `Get-MrPipelineInput` 的函数。</span><span class="sxs-lookup"><span data-stu-id="6018b-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="6018b-219">此 cmdlet 可用于轻松确定接受管道输入的命令参数、接受的对象类型，以及是按值还是按属性名称接受管道输入 。</span><span class="sxs-lookup"><span data-stu-id="6018b-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="6018b-220">正如你所看到的那样，我们先前通过筛选帮助内容确定的信息可借助此函数轻松确定。</span><span class="sxs-lookup"><span data-stu-id="6018b-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="6018b-221">总结</span><span class="sxs-lookup"><span data-stu-id="6018b-221">Summary</span></span>

<span data-ttu-id="6018b-222">在本章中，你已了解 PowerShell 单行命令。</span><span class="sxs-lookup"><span data-stu-id="6018b-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="6018b-223">你已经了解到，命令占据的物理行数与它是否是 PowerShell 单行命令无关。</span><span class="sxs-lookup"><span data-stu-id="6018b-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="6018b-224">还了解了筛选左侧、管道和 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="6018b-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="6018b-225">审阅</span><span class="sxs-lookup"><span data-stu-id="6018b-225">Review</span></span>

1. <span data-ttu-id="6018b-226">PowerShell 单行命令是什么？</span><span class="sxs-lookup"><span data-stu-id="6018b-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="6018b-227">在 PowerShell 中，自然换行处的字符有哪些？</span><span class="sxs-lookup"><span data-stu-id="6018b-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="6018b-228">为什么要筛选左侧？</span><span class="sxs-lookup"><span data-stu-id="6018b-228">Why should you filter left?</span></span>
1. <span data-ttu-id="6018b-229">PowerShell 命令接受管道输入的两种方式是什么？</span><span class="sxs-lookup"><span data-stu-id="6018b-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="6018b-230">为什么不应信任 PowerShell 库中找到的命令？</span><span class="sxs-lookup"><span data-stu-id="6018b-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="6018b-231">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="6018b-231">Recommended Reading</span></span>

- <span data-ttu-id="6018b-232">[about_pipelines][]</span><span class="sxs-lookup"><span data-stu-id="6018b-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="6018b-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="6018b-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="6018b-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="6018b-234">[about_Parameters][]</span></span>
- <span data-ttu-id="6018b-235">[PowerShellGet：发现、安装和更新 PowerShell 模块的简单方法][psget]</span><span class="sxs-lookup"><span data-stu-id="6018b-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell 库]: https://www.powershellgallery.com/
[PowerShell Gallery]: https://www.powershellgallery.com/
