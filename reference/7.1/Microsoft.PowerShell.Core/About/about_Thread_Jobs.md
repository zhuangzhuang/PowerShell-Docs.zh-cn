---
description: 提供有关基于 PowerShell 线程的作业的信息。 线程作业是一种后台作业，它在当前会话进程中的单独线程中运行命令或表达式。
Locale: en-US
ms.date: 11/11/2020
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 67f3fc585a8c2d1c3ca98c7336a7e367ed6c66c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194242"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="338be-104">关于线程作业</span><span class="sxs-lookup"><span data-stu-id="338be-104">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="338be-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="338be-105">Short description</span></span>

<span data-ttu-id="338be-106">提供有关基于 PowerShell 线程的作业的信息。</span><span class="sxs-lookup"><span data-stu-id="338be-106">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="338be-107">线程作业是一种后台作业，它在当前会话进程中的单独线程中运行命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="338be-107">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="338be-108">长说明</span><span class="sxs-lookup"><span data-stu-id="338be-108">Long description</span></span>

<span data-ttu-id="338be-109">PowerShell 通过作业并发运行命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="338be-109">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="338be-110">PowerShell 提供三种作业类型来支持并发。</span><span class="sxs-lookup"><span data-stu-id="338be-110">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="338be-111">`RemoteJob` -命令和脚本在远程会话中运行。</span><span class="sxs-lookup"><span data-stu-id="338be-111">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="338be-112">有关信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="338be-112">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="338be-113">`BackgroundJob` -命令和脚本在本地计算机上的单独进程中运行。</span><span class="sxs-lookup"><span data-stu-id="338be-113">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="338be-114">有关详细信息，请参阅 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="338be-114">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="338be-115">`PSTaskJob` 或 `ThreadJob` -命令和脚本在本地计算机上的同一进程内的单独线程中运行。</span><span class="sxs-lookup"><span data-stu-id="338be-115">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="338be-116">基于线程的作业不像远程和后台作业那样可靠，因为它们在不同线程上的同一进程中运行。</span><span class="sxs-lookup"><span data-stu-id="338be-116">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="338be-117">如果一个作业发生了导致进程崩溃的严重错误，则会终止该进程中的所有其他作业。</span><span class="sxs-lookup"><span data-stu-id="338be-117">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="338be-118">但是，基于线程的作业需要更少的开销。</span><span class="sxs-lookup"><span data-stu-id="338be-118">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="338be-119">它们不使用远程层或序列化。</span><span class="sxs-lookup"><span data-stu-id="338be-119">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="338be-120">结果对象作为对当前会话中活动对象的引用返回。</span><span class="sxs-lookup"><span data-stu-id="338be-120">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="338be-121">如果没有此开销，基于线程的作业运行速度更快，使用的资源比其他作业类型少。</span><span class="sxs-lookup"><span data-stu-id="338be-121">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="338be-122">创建作业的父会话还会监视作业状态和收集管道数据。</span><span class="sxs-lookup"><span data-stu-id="338be-122">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="338be-123">作业到达完成状态后，父进程终止了作业子进程。</span><span class="sxs-lookup"><span data-stu-id="338be-123">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="338be-124">如果终止了父会话，则所有正在运行的子作业都将与其子进程一起终止。</span><span class="sxs-lookup"><span data-stu-id="338be-124">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="338be-125">可通过两种方法解决此问题：</span><span class="sxs-lookup"><span data-stu-id="338be-125">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="338be-126">用于 `Invoke-Command` 创建在断开连接的会话中运行的作业。</span><span class="sxs-lookup"><span data-stu-id="338be-126">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="338be-127">有关详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="338be-127">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="338be-128">使用 `Start-Process` 创建新进程，而不是作业。</span><span class="sxs-lookup"><span data-stu-id="338be-128">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="338be-129">有关详细信息，请参阅 [开始处理](xref:Microsoft.PowerShell.Management.Start-Process)。</span><span class="sxs-lookup"><span data-stu-id="338be-129">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="338be-130">如何启动和管理基于线程的作业</span><span class="sxs-lookup"><span data-stu-id="338be-130">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="338be-131">可以通过两种方法启动基于线程的作业：</span><span class="sxs-lookup"><span data-stu-id="338be-131">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="338be-132">`Start-ThreadJob` -从 **ThreadJob** 模块</span><span class="sxs-lookup"><span data-stu-id="338be-132">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="338be-133">`ForEach-Object -Parallel -AsJob` -已在 PowerShell 7.0 中添加并行功能</span><span class="sxs-lookup"><span data-stu-id="338be-133">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="338be-134">使用 [about_Jobs](about_Jobs.md)中所述的相同 **作业** cmdlet 来管理基于线程的作业。</span><span class="sxs-lookup"><span data-stu-id="338be-134">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="338be-135">使用 `Start-ThreadJob`</span><span class="sxs-lookup"><span data-stu-id="338be-135">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="338be-136">**ThreadJob** 模块首次随附于 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="338be-136">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="338be-137">还可以从 Windows PowerShell 5.1 PowerShell 库安装。</span><span class="sxs-lookup"><span data-stu-id="338be-137">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="338be-138">若要在本地计算机上启动线程作业，请使用 `Start-ThreadJob` 带有括在大括号中的命令或脚本的 cmdlet (`{ }`) 。</span><span class="sxs-lookup"><span data-stu-id="338be-138">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="338be-139">下面的示例启动一个 `Get-Process` 在本地计算机上运行命令的线程作业。</span><span class="sxs-lookup"><span data-stu-id="338be-139">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="338be-140">该 `Start-ThreadJob` 命令将返回一个 `ThreadJob` 对象，该对象表示正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="338be-140">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="338be-141">作业对象包含有关作业的有用信息，包括作业的当前运行状态。</span><span class="sxs-lookup"><span data-stu-id="338be-141">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="338be-142">它在生成结果时收集作业的结果。</span><span class="sxs-lookup"><span data-stu-id="338be-142">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="338be-143">使用 `ForEach-Object -Parallel -AsJob`</span><span class="sxs-lookup"><span data-stu-id="338be-143">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="338be-144">PowerShell 7.0 向 cmdlet 添加了一个新参数集 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="338be-144">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="338be-145">新参数允许你将并行线程中的脚本块作为 PowerShell 作业运行。</span><span class="sxs-lookup"><span data-stu-id="338be-145">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="338be-146">可以通过管道将数据传递给 `ForEach-Object -Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="338be-146">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="338be-147">数据将传递到并行运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="338be-147">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="338be-148">`-AsJob`参数为每个并行线程创建作业对象。</span><span class="sxs-lookup"><span data-stu-id="338be-148">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="338be-149">下面的命令启动一个作业，该作业包含向命令传递的每个输入值的子作业。</span><span class="sxs-lookup"><span data-stu-id="338be-149">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="338be-150">每个子作业都将 `Write-Output` 使用一个管道输入值作为参数来运行该命令。</span><span class="sxs-lookup"><span data-stu-id="338be-150">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="338be-151">该 `ForEach-Object -Parallel` 命令将返回一个 `PSTaskJob` 对象，该对象包含每个管道输入值的子作业。</span><span class="sxs-lookup"><span data-stu-id="338be-151">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="338be-152">作业对象包含有关子作业运行状态的有用信息。</span><span class="sxs-lookup"><span data-stu-id="338be-152">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="338be-153">它在生成结果时收集子作业的结果。</span><span class="sxs-lookup"><span data-stu-id="338be-153">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="338be-154">如何等待作业完成并检索作业结果</span><span class="sxs-lookup"><span data-stu-id="338be-154">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="338be-155">你可以使用 PowerShell 作业 cmdlet （如 `Wait-Job` 和） `Receive-Job` 等待作业完成，然后返回作业生成的所有结果。</span><span class="sxs-lookup"><span data-stu-id="338be-155">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="338be-156">下面的命令启动一个运行命令的线程作业 `Get-Process` ，然后等待该命令完成，最后返回该命令生成的所有数据结果。</span><span class="sxs-lookup"><span data-stu-id="338be-156">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="338be-157">下面的命令启动一个作业，该作业 `Write-Output` 对每个管道输入运行一个命令，然后等待所有子作业完成，最后返回子作业生成的所有数据结果。</span><span class="sxs-lookup"><span data-stu-id="338be-157">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="338be-158">`Receive-Job`Cmdlet 返回子作业的结果。</span><span class="sxs-lookup"><span data-stu-id="338be-158">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="338be-159">由于每个子作业都是并行运行的，因此不保证生成的结果的顺序。</span><span class="sxs-lookup"><span data-stu-id="338be-159">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="338be-160">线程作业性能</span><span class="sxs-lookup"><span data-stu-id="338be-160">Thread job performance</span></span>

<span data-ttu-id="338be-161">与其他类型的作业相比，线程作业的权重更快且更轻。</span><span class="sxs-lookup"><span data-stu-id="338be-161">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="338be-162">但与作业正在进行的工作相比，它们的开销可能会很大。</span><span class="sxs-lookup"><span data-stu-id="338be-162">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="338be-163">PowerShell 在会话中运行命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="338be-163">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="338be-164">会话中一次只能运行一个命令或脚本。</span><span class="sxs-lookup"><span data-stu-id="338be-164">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="338be-165">因此，在运行多个作业时，每个作业都在单独的会话中运行。</span><span class="sxs-lookup"><span data-stu-id="338be-165">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="338be-166">每个会话都可提供开销。</span><span class="sxs-lookup"><span data-stu-id="338be-166">Each session contributes to the overhead.</span></span>

<span data-ttu-id="338be-167">当执行的工作大于用于运行作业的会话的开销时，线程作业可提供最佳性能。</span><span class="sxs-lookup"><span data-stu-id="338be-167">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="338be-168">满足此条件的情况有两种情况。</span><span class="sxs-lookup"><span data-stu-id="338be-168">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="338be-169">工作是计算密集型-在多个线程作业上运行脚本可充分利用多个处理器核心并更快完成。</span><span class="sxs-lookup"><span data-stu-id="338be-169">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="338be-170">工作包括大量等待时间的脚本，该脚本花费时间等待 i/o 或远程调用结果。</span><span class="sxs-lookup"><span data-stu-id="338be-170">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="338be-171">并行运行通常比按顺序运行快。</span><span class="sxs-lookup"><span data-stu-id="338be-171">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

<span data-ttu-id="338be-172">上面的第一个示例显示了一个 foreach 循环，该循环创建1000线程作业来编写简单的字符串。</span><span class="sxs-lookup"><span data-stu-id="338be-172">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="338be-173">由于作业开销，需要超过36秒钟才能完成。</span><span class="sxs-lookup"><span data-stu-id="338be-173">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="338be-174">第二个示例运行 `ForEach` cmdlet 来执行相同的1000操作。</span><span class="sxs-lookup"><span data-stu-id="338be-174">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="338be-175">这次 `ForEach-Object` 在单个线程上按顺序运行，无需任何作业开销。</span><span class="sxs-lookup"><span data-stu-id="338be-175">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="338be-176">它只会在7毫秒内完成。</span><span class="sxs-lookup"><span data-stu-id="338be-176">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="338be-177">在以下示例中，最多可为10个单独的系统日志收集5000个条目。</span><span class="sxs-lookup"><span data-stu-id="338be-177">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="338be-178">由于脚本涉及到读取多个日志，因此有必要并行执行操作。</span><span class="sxs-lookup"><span data-stu-id="338be-178">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

<span data-ttu-id="338be-179">脚本在并行运行作业的一半时间内完成。</span><span class="sxs-lookup"><span data-stu-id="338be-179">The script completes in half the time when the jobs are run in parallel.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="338be-180">线程作业和变量</span><span class="sxs-lookup"><span data-stu-id="338be-180">Thread jobs and variables</span></span>

<span data-ttu-id="338be-181">可以通过多种方法将值传递到基于线程的作业中。</span><span class="sxs-lookup"><span data-stu-id="338be-181">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="338be-182">`Start-ThreadJob` 可以接受通过管道传递给脚本块的、通过关键字传递到脚本块的变量， `$using` 也可以通过 **ArgumentList** 参数传入。</span><span class="sxs-lookup"><span data-stu-id="338be-182">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="338be-183">`ForEach-Object -Parallel` 接受通过关键字直接传递到脚本块的变量和变量 `$using` 。</span><span class="sxs-lookup"><span data-stu-id="338be-183">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="338be-184">由于线程作业在同一进程中运行，因此必须仔细对待传入作业的任何变量引用类型。</span><span class="sxs-lookup"><span data-stu-id="338be-184">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="338be-185">如果它不是线程安全对象，则绝不应将其分配给，并且永远不应在其上调用方法和属性。</span><span class="sxs-lookup"><span data-stu-id="338be-185">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="338be-186">下面的示例将一个线程安全的 .NET `ConcurrentDictionary` 对象传递给所有子作业，以收集唯一命名的进程对象。</span><span class="sxs-lookup"><span data-stu-id="338be-186">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="338be-187">由于它是线程安全对象，因此可以安全地使用该对象，同时在进程中同时运行作业。</span><span class="sxs-lookup"><span data-stu-id="338be-187">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a><span data-ttu-id="338be-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="338be-188">See also</span></span>

- [<span data-ttu-id="338be-189">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="338be-189">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="338be-190">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="338be-190">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="338be-191">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="338be-191">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="338be-192">about_Remote</span><span class="sxs-lookup"><span data-stu-id="338be-192">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="338be-193">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="338be-193">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="338be-194">Start-Job</span><span class="sxs-lookup"><span data-stu-id="338be-194">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="338be-195">Get-Job</span><span class="sxs-lookup"><span data-stu-id="338be-195">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="338be-196">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="338be-196">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="338be-197">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="338be-197">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="338be-198">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="338be-198">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="338be-199">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="338be-199">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
