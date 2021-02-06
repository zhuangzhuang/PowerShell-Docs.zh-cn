---
description: 提供有关本地和远程计算机上的后台作业的详细信息。
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 1ceb0be9cc140b69afdebaaf336dad75e482aa22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597078"
---
# <a name="about-job-details"></a><span data-ttu-id="82c10-103">关于作业详细信息</span><span class="sxs-lookup"><span data-stu-id="82c10-103">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="82c10-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="82c10-104">Short description</span></span>
<span data-ttu-id="82c10-105">提供有关本地和远程计算机上的后台作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="82c10-105">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="82c10-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="82c10-106">Detailed description</span></span>

<span data-ttu-id="82c10-107">本主题介绍后台作业的概念，并提供有关后台作业在 PowerShell 中的工作原理的技术信息。</span><span class="sxs-lookup"><span data-stu-id="82c10-107">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="82c10-108">本主题是对 [about_Jobs](about_Jobs.md)、 [about_Thread_Jobs](about_Thread_Jobs.md)和 [about_Remote_Jobs](about_Remote_Jobs.md) 主题的补充。</span><span class="sxs-lookup"><span data-stu-id="82c10-108">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="82c10-109">关于后台作业</span><span class="sxs-lookup"><span data-stu-id="82c10-109">About background jobs</span></span>

<span data-ttu-id="82c10-110">后台作业异步运行命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="82c10-110">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="82c10-111">它可以运行 cmdlet、函数、脚本或任何其他基于命令的任务。</span><span class="sxs-lookup"><span data-stu-id="82c10-111">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="82c10-112">它旨在运行长时间运行的命令，但你可以使用它在后台运行任何命令。</span><span class="sxs-lookup"><span data-stu-id="82c10-112">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="82c10-113">同步命令运行时，会禁止 PowerShell 命令提示符，直到命令完成。</span><span class="sxs-lookup"><span data-stu-id="82c10-113">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="82c10-114">但后台作业不会显示 PowerShell 提示。</span><span class="sxs-lookup"><span data-stu-id="82c10-114">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="82c10-115">用于启动后台作业的命令返回一个作业对象。</span><span class="sxs-lookup"><span data-stu-id="82c10-115">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="82c10-116">提示符会立即返回，以便在后台作业运行时可以处理其他任务。</span><span class="sxs-lookup"><span data-stu-id="82c10-116">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="82c10-117">但在启动后台作业时，即使作业运行速度很快，也不会立即获得结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-117">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="82c10-118">返回的作业对象包含有关该作业的有用信息，但不包含作业结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-118">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="82c10-119">必须运行单独的命令来获取作业结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-119">You must run a separate command to get the job results.</span></span> <span data-ttu-id="82c10-120">你还可以运行命令来停止作业，等待作业完成，并删除作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-120">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="82c10-121">为了使后台作业的时间与其他命令无关，每个后台作业都在其自己的 PowerShell 会话中运行。</span><span class="sxs-lookup"><span data-stu-id="82c10-121">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="82c10-122">但是，这可能是只是为了运行作业而创建的临时连接，然后将其销毁，或者可以使用永久性 **PSSession** 来运行多个相关的作业或命令。</span><span class="sxs-lookup"><span data-stu-id="82c10-122">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="82c10-123">使用作业 cmdlet</span><span class="sxs-lookup"><span data-stu-id="82c10-123">Using the job cmdlets</span></span>

<span data-ttu-id="82c10-124">使用 `Start-Job` 命令在本地计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-124">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="82c10-125">`Start-Job` 返回一个作业对象。</span><span class="sxs-lookup"><span data-stu-id="82c10-125">`Start-Job` returns a job object.</span></span> <span data-ttu-id="82c10-126">你还可以使用 cmdlet 来获取表示在本地计算机上启动的作业的对象 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="82c10-126">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="82c10-127">若要获取作业结果，请使用 `Receive-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="82c10-127">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="82c10-128">如果作业未完成，则 `Receive-Job` 返回部分结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-128">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="82c10-129">你还可以使用 `Wait-Job` cmdlet 来禁止显示命令提示符，直到在会话中启动的一个或所有作业完成为止。</span><span class="sxs-lookup"><span data-stu-id="82c10-129">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="82c10-130">若要停止后台作业，请使用 `Stop-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-130">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="82c10-131">若要删除作业，请使用 `Remove-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-131">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="82c10-132">有关 cmdlet 的工作原理的详细信息，请参阅每个 cmdlet 的帮助主题，并参阅 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="82c10-132">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="82c10-133">在远程计算机上启动后台作业</span><span class="sxs-lookup"><span data-stu-id="82c10-133">Starting background jobs on remote computers</span></span>

<span data-ttu-id="82c10-134">可以在本地或远程计算机上创建和管理后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-134">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="82c10-135">若要远程运行后台作业，请使用 cmdlet （如）的 **AsJob** 参数 `Invoke-Command` ，或使用 `Invoke-Command` cmdlet `Start-Job` 远程运行命令。</span><span class="sxs-lookup"><span data-stu-id="82c10-135">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="82c10-136">你还可以在交互式会话中启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-136">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="82c10-137">有关远程后台作业的详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="82c10-137">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="82c10-138">子作业</span><span class="sxs-lookup"><span data-stu-id="82c10-138">Child jobs</span></span>

<span data-ttu-id="82c10-139">每个后台作业都包含一个父作业和一个或多个子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-139">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="82c10-140">在使用 `Start-Job` 或的 **AsJob** 参数启动的作业中 `Invoke-Command` ，父作业是执行程序。</span><span class="sxs-lookup"><span data-stu-id="82c10-140">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="82c10-141">它不会运行任何命令，也不会返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-141">It does not run any commands or return any results.</span></span> <span data-ttu-id="82c10-142">命令实际上由子作业运行。</span><span class="sxs-lookup"><span data-stu-id="82c10-142">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="82c10-143">使用其他 cmdlet 启动的作业的工作方式可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="82c10-143">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="82c10-144">子作业存储在父作业对象的 **ChildJobs** 属性中。</span><span class="sxs-lookup"><span data-stu-id="82c10-144">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="82c10-145">**ChildJobs** 属性可以包含一个或多个子作业对象。</span><span class="sxs-lookup"><span data-stu-id="82c10-145">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="82c10-146">子作业对象具有与父作业不同的 **名称**、 **ID** 和 **InstanceId** ，以便您可以单独或作为一个单元管理父作业和子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-146">The child job objects have a **Name**, **ID**, and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="82c10-147">若要获取作业的父作业和子作业，请使用 cmdlet 的 **IncludeChildJobs** 参数 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="82c10-147">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="82c10-148">**IncludeChildJob** 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="82c10-148">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="82c10-149">若要获取父作业和仅具有特定 **状态** 值的子作业，请使用 Cmdlet 的 **ChildJobState** 参数 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="82c10-149">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="82c10-150">**ChildJobState** 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="82c10-150">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="82c10-151">若要获取所有版本的 PowerShell 上作业的子作业，请使用父作业的 **ChildJob** 属性。</span><span class="sxs-lookup"><span data-stu-id="82c10-151">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="82c10-152">你还可以 `Get-Job` 对子作业使用命令，如以下命令中所示：</span><span class="sxs-lookup"><span data-stu-id="82c10-152">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="82c10-153">子作业的配置取决于用于启动作业的命令。</span><span class="sxs-lookup"><span data-stu-id="82c10-153">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="82c10-154">当你使用在 `Start-Job` 本地计算机上启动作业时，该作业包含一个执行程序父作业和一个运行该命令的子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-154">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="82c10-155">使用的 **AsJob** 参数 `Invoke-Command` 启动一台或多台计算机上的作业时，该作业将包含执行程序父作业和每台计算机上运行的每个作业的子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-155">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="82c10-156">当您使用 `Invoke-Command` `Start-Job` 在一台或多台远程计算机上运行命令时，其结果与在每台远程计算机上运行的本地命令相同。</span><span class="sxs-lookup"><span data-stu-id="82c10-156">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="82c10-157">此命令为每台计算机返回一个作业对象。</span><span class="sxs-lookup"><span data-stu-id="82c10-157">The command returns a job object for each computer.</span></span> <span data-ttu-id="82c10-158">作业对象由一个运行命令的执行程序父作业和一个子作业组成。</span><span class="sxs-lookup"><span data-stu-id="82c10-158">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="82c10-159">父作业表示所有子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-159">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="82c10-160">管理父作业时，还会管理关联的子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-160">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="82c10-161">例如，如果停止父作业，则会停止所有子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-161">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="82c10-162">如果获取父作业的结果，则会获得所有子作业的结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-162">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="82c10-163">但是，你还可以单独管理子作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-163">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="82c10-164">当你希望调查某个作业的问题，或者只获取使用 **AsJob** 参数启动的多个子作业之一的结果时，这非常有用 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="82c10-164">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="82c10-165">以下命令使用的 **AsJob** 参数在 `Invoke-Command` 本地计算机和两台远程计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-165">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="82c10-166">该命令将作业保存在 `$j` 变量中。</span><span class="sxs-lookup"><span data-stu-id="82c10-166">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="82c10-167">当你在中显示作业的 Name 和 **ChildJob** 属性时 `$j` ，它会显示该命令返回一个作业对象，其中包含三个子作业，每台计算机一个。</span><span class="sxs-lookup"><span data-stu-id="82c10-167">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="82c10-168">显示父作业时，它会显示作业失败。</span><span class="sxs-lookup"><span data-stu-id="82c10-168">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="82c10-169">但在运行 `Get-Job` 获取子作业的命令时，输出会显示只有一个子作业失败。</span><span class="sxs-lookup"><span data-stu-id="82c10-169">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="82c10-170">若要获取所有子作业的结果，请使用 `Receive-Job` cmdlet 获取父作业的结果。</span><span class="sxs-lookup"><span data-stu-id="82c10-170">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="82c10-171">但也可以获取特定子作业的结果，如以下命令中所示。</span><span class="sxs-lookup"><span data-stu-id="82c10-171">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="82c10-172">PowerShell 后台作业的子作业功能使你可以更好地控制你运行的作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-172">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="82c10-173">作业类型</span><span class="sxs-lookup"><span data-stu-id="82c10-173">Job types</span></span>

<span data-ttu-id="82c10-174">对于不同任务，PowerShell 支持不同类型的作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-174">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="82c10-175">从 Windows PowerShell 3.0 开始，开发人员可以编写 "作业源适配器"，将新作业类型添加到 PowerShell，并在模块中包含作业源适配器。</span><span class="sxs-lookup"><span data-stu-id="82c10-175">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="82c10-176">导入模块时，你可以在会话中使用新作业类型。</span><span class="sxs-lookup"><span data-stu-id="82c10-176">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="82c10-177">例如，PSScheduledJob 模块添加了计划作业，PSWorkflow 模块添加了工作流作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-177">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="82c10-178">自定义作业类型与标准 PowerShell 后台作业可能有明显差异。</span><span class="sxs-lookup"><span data-stu-id="82c10-178">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="82c10-179">例如，计划作业保存在磁盘上;它们不存在于特定的会话中。</span><span class="sxs-lookup"><span data-stu-id="82c10-179">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="82c10-180">可以挂起和恢复工作流作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-180">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="82c10-181">用于管理自定义作业的 cmdlet 依赖于作业类型。</span><span class="sxs-lookup"><span data-stu-id="82c10-181">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="82c10-182">对于某些情况，请使用标准作业 cmdlet，例如 `Get-Job` 和 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="82c10-182">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="82c10-183">其他人附带了专门的 cmdlet，只管理特定类型的作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-183">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="82c10-184">有关自定义作业类型的详细信息，请参阅有关作业类型的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="82c10-184">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="82c10-185">若要查找作业的作业类型，请使用 `Get-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-185">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="82c10-186">`Get-Job` 为不同类型的作业返回不同的作业对象。</span><span class="sxs-lookup"><span data-stu-id="82c10-186">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="82c10-187">返回的作业对象的 **PSJobTypeName** 属性值 `Get-Job` 指示作业类型。</span><span class="sxs-lookup"><span data-stu-id="82c10-187">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="82c10-188">下表列出了 PowerShell 附带的作业类型。</span><span class="sxs-lookup"><span data-stu-id="82c10-188">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="82c10-189">作业类型</span><span class="sxs-lookup"><span data-stu-id="82c10-189">Job Type</span></span>    |                       <span data-ttu-id="82c10-190">说明</span><span class="sxs-lookup"><span data-stu-id="82c10-190">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="82c10-191">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="82c10-191">BackgroundJob</span></span>  | <span data-ttu-id="82c10-192">已开始使用 `Start-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-192">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="82c10-193">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="82c10-193">RemoteJob</span></span>      | <span data-ttu-id="82c10-194">已开始使用的 **AsJob** 参数</span><span class="sxs-lookup"><span data-stu-id="82c10-194">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="82c10-195">`Invoke-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-195">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="82c10-196">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="82c10-196">PSWorkflowJob</span></span>  | <span data-ttu-id="82c10-197">已开始使用工作流的 **AsJob** 参数。</span><span class="sxs-lookup"><span data-stu-id="82c10-197">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="82c10-198">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c10-198">PSScheduledJob</span></span> | <span data-ttu-id="82c10-199">作业触发器启动的计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="82c10-199">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="82c10-200">CIMJob</span><span class="sxs-lookup"><span data-stu-id="82c10-200">CIMJob</span></span>         | <span data-ttu-id="82c10-201">已开始使用 cmdlet 的 **AsJob** 参数</span><span class="sxs-lookup"><span data-stu-id="82c10-201">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="82c10-202">CDXML 模块。</span><span class="sxs-lookup"><span data-stu-id="82c10-202">CDXML module.</span></span>                                            |
| <span data-ttu-id="82c10-203">WMIJob</span><span class="sxs-lookup"><span data-stu-id="82c10-203">WMIJob</span></span>         | <span data-ttu-id="82c10-204">已开始使用 cmdlet 的 **AsJob** 参数</span><span class="sxs-lookup"><span data-stu-id="82c10-204">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="82c10-205">WMI 模块。</span><span class="sxs-lookup"><span data-stu-id="82c10-205">WMI module.</span></span>                                              |
| <span data-ttu-id="82c10-206">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="82c10-206">PSEventJob</span></span>     | <span data-ttu-id="82c10-207">使用创建 `Register-ObjectEvent` 并指定</span><span class="sxs-lookup"><span data-stu-id="82c10-207">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="82c10-208">**操作参数的** 操作。</span><span class="sxs-lookup"><span data-stu-id="82c10-208">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="82c10-209">注意：使用 `Get-Job` cmdlet 获取特定类型的作业之前，请验证添加作业类型的模块是否已导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="82c10-209">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="82c10-210">否则，不 `Get-Job` 会获取该类型的作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-210">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="82c10-211">示例</span><span class="sxs-lookup"><span data-stu-id="82c10-211">Examples</span></span>

<span data-ttu-id="82c10-212">以下命令将创建本地后台作业、远程后台作业、工作流作业和计划作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-212">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="82c10-213">然后，它使用 `Get-Job` cmdlet 来获取作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-213">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="82c10-214">`Get-Job` 不会获得计划作业，但会获取计划作业的任何已启动实例。</span><span class="sxs-lookup"><span data-stu-id="82c10-214">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="82c10-215">在本地计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-215">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="82c10-216">启动在远程计算机上运行的后台作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-216">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="82c10-217">创建计划作业</span><span class="sxs-lookup"><span data-stu-id="82c10-217">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="82c10-218">创建工作流。</span><span class="sxs-lookup"><span data-stu-id="82c10-218">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="82c10-219">以作业形式运行工作流。</span><span class="sxs-lookup"><span data-stu-id="82c10-219">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="82c10-220">获取作业。</span><span class="sxs-lookup"><span data-stu-id="82c10-220">Get the jobs.</span></span> <span data-ttu-id="82c10-221">此 `Get-Job` 命令不会获取计划作业，但会获取已启动的计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="82c10-221">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="82c10-222">若要获取计划作业，请使用 `Get-ScheduledJob` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82c10-222">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="82c10-223">请参阅</span><span class="sxs-lookup"><span data-stu-id="82c10-223">See also</span></span>

- [<span data-ttu-id="82c10-224">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="82c10-224">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="82c10-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="82c10-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="82c10-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="82c10-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="82c10-227">about_Remote</span><span class="sxs-lookup"><span data-stu-id="82c10-227">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="82c10-228">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="82c10-228">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="82c10-229">Start-Job</span><span class="sxs-lookup"><span data-stu-id="82c10-229">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="82c10-230">Get-Job</span><span class="sxs-lookup"><span data-stu-id="82c10-230">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="82c10-231">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="82c10-231">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="82c10-232">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="82c10-232">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="82c10-233">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="82c10-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="82c10-234">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="82c10-234">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="82c10-235">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="82c10-235">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="82c10-236">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="82c10-236">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
