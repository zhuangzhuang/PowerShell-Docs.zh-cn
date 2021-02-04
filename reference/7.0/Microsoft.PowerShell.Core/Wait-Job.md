---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 591d418c47cddc7dc1c9dd055d6bd0698a2245b0
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098697"
---
# <span data-ttu-id="e31c1-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-103">Wait-Job</span></span>

## <span data-ttu-id="e31c1-104">摘要</span><span class="sxs-lookup"><span data-stu-id="e31c1-104">SYNOPSIS</span></span>
<span data-ttu-id="e31c1-105">等待在会话中运行的一个或所有 PowerShell 作业处于终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-105">Waits until one or all of the PowerShell jobs running in the session are in a terminating state.</span></span>

## <span data-ttu-id="e31c1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e31c1-106">SYNTAX</span></span>

### <span data-ttu-id="e31c1-107">SessionIdParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="e31c1-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="e31c1-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="e31c1-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="e31c1-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="e31c1-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e31c1-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e31c1-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="e31c1-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="e31c1-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="e31c1-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="e31c1-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="e31c1-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e31c1-113">DESCRIPTION</span></span>

<span data-ttu-id="e31c1-114">`Wait-Job`Cmdlet 会等待作业处于终止状态，然后再继续执行。</span><span class="sxs-lookup"><span data-stu-id="e31c1-114">The `Wait-Job` cmdlet waits for a job to be in a terminating state before continuing execution.</span></span>
<span data-ttu-id="e31c1-115">终止状态为：</span><span class="sxs-lookup"><span data-stu-id="e31c1-115">The terminating states are:</span></span>

- <span data-ttu-id="e31c1-116">已完成</span><span class="sxs-lookup"><span data-stu-id="e31c1-116">Completed</span></span>
- <span data-ttu-id="e31c1-117">已失败</span><span class="sxs-lookup"><span data-stu-id="e31c1-117">Failed</span></span>
- <span data-ttu-id="e31c1-118">已停止</span><span class="sxs-lookup"><span data-stu-id="e31c1-118">Stopped</span></span>
- <span data-ttu-id="e31c1-119">Suspended</span><span class="sxs-lookup"><span data-stu-id="e31c1-119">Suspended</span></span>
- <span data-ttu-id="e31c1-120">已断开连接</span><span class="sxs-lookup"><span data-stu-id="e31c1-120">Disconnected</span></span>

<span data-ttu-id="e31c1-121">可以等待指定的作业，或者所有作业都处于终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-121">You can wait until a specified job, or all jobs are in a terminating state.</span></span> <span data-ttu-id="e31c1-122">你还可以使用 **Timeout** 参数为作业设置最长等待时间，或使用 **Force** 参数等待或状态下的作业 `Suspended` `Disconnected` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-122">You can also set a maximum wait time for the job using the **Timeout** parameter, or use the **Force** parameter to wait for a job in the `Suspended` or `Disconnected` states.</span></span>

<span data-ttu-id="e31c1-123">当作业中的命令完成时， `Wait-Job` 将返回一个作业对象，并继续执行。</span><span class="sxs-lookup"><span data-stu-id="e31c1-123">When the commands in the job are complete, `Wait-Job` returns a job object and continues execution.</span></span>

<span data-ttu-id="e31c1-124">可以使用 cmdlet `Wait-Job` 等待使用 cmdlet `Start-Job` 或 Cmdlet 的 **AsJob** 参数启动的作业 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-124">You can use the `Wait-Job` cmdlet to wait for jobs started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e31c1-125">有关作业的详细信息，请参阅 [about_Jobs](./about/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="e31c1-125">For more information about jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="e31c1-126">从 Windows PowerShell 3.0 开始， `Wait-Job` cmdlet 还会等待自定义作业类型，例如工作流作业和计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="e31c1-126">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="e31c1-127">若要使 `Wait-Job` 能够等待特定类型的作业，请在运行 cmdlet 之前将支持自定义作业类型的模块导入到会话中，方法 `Get-Job` 是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e31c1-127">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="e31c1-128">有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。</span><span class="sxs-lookup"><span data-stu-id="e31c1-128">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="e31c1-129">示例</span><span class="sxs-lookup"><span data-stu-id="e31c1-129">EXAMPLES</span></span>

### <span data-ttu-id="e31c1-130">示例1：等待所有作业</span><span class="sxs-lookup"><span data-stu-id="e31c1-130">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="e31c1-131">此命令等待在会话中运行的所有作业完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-131">This command waits for all of the jobs running in the session to finish.</span></span>

### <span data-ttu-id="e31c1-132">示例2：使用 Start-Job 等待远程计算机上启动的作业</span><span class="sxs-lookup"><span data-stu-id="e31c1-132">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="e31c1-133">此示例显示了如何 `Wait-Job` 通过 cmdlet 将 cmdlet 用于远程计算机上启动的作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-133">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="e31c1-134">`Start-Job` `Wait-Job` 使用 cmdlet 将和命令提交到远程计算机 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-134">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="e31c1-135">此示例使用 `Wait-Job` 来确定 `Get-Date` 在三台不同计算机上作为作业运行的命令是否完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-135">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a job on three different computers is finished.</span></span>

<span data-ttu-id="e31c1-136">第一个命令在三台远程计算机的每台计算机上创建一个 (**PSSession**) 的 Windows PowerShell 会话，并将其存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-136">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="e31c1-137">第二个命令使用在 `Invoke-Command` `Start-Job` 中的三个会话中运行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-137">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="e31c1-138">所有作业都命名为 Date1。</span><span class="sxs-lookup"><span data-stu-id="e31c1-138">All of the jobs are named Date1.</span></span>

<span data-ttu-id="e31c1-139">第三个命令使用 `Invoke-Command` 来运行 `Wait-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-139">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="e31c1-140">此命令等待 `Date1` 每台计算机上的作业完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-140">This command waits for the `Date1` jobs on each computer to finish.</span></span> <span data-ttu-id="e31c1-141">它将生成的集合存储 (**数组** 中的 **作业** 对象) `$done` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-141">It stores the resulting collection (**array**) of **job** objects in the `$done` variable.</span></span>

<span data-ttu-id="e31c1-142">第四个命令使用变量中的作业对象数组的 **Count** 属性 `$done` 来确定完成的作业数。</span><span class="sxs-lookup"><span data-stu-id="e31c1-142">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="e31c1-143">示例3：确定第一个作业完成的时间</span><span class="sxs-lookup"><span data-stu-id="e31c1-143">Example 3: Determine when the first job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="e31c1-144">此示例使用的 **Any** 参数 `Wait-Job` 来确定在当前会话中运行的多个作业的第一个处于终止状态的时间。</span><span class="sxs-lookup"><span data-stu-id="e31c1-144">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many jobs running in the current session are in a terminating state.</span></span> <span data-ttu-id="e31c1-145">它还演示了如何使用 `Wait-Job` cmdlet 等待远程作业完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-145">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="e31c1-146">第一个命令在 Machines.txt 文件中列出的每台计算机上创建 **pssession** ，并将 **pssession** 对象存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-146">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="e31c1-147">该命令使用 `Get-Content` cmdlet 来获取文件的内容。</span><span class="sxs-lookup"><span data-stu-id="e31c1-147">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="e31c1-148">`Get-Content`命令括在括号中，以确保它在命令之前运行 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-148">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="e31c1-149">第二个命令将 `Get-EventLog` 命令字符串用引号引起来 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-149">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="e31c1-150">第三个命令使用 `Invoke-Command` cmdlet `Start-Job` 在中的每个会话中运行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-150">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="e31c1-151">`Start-Job`命令启动一个作业，该作业 `Get-EventLog` 在变量中运行该命令 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-151">The `Start-Job` command starts a job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="e31c1-152">该命令使用 **Using** 作用域修饰符来指示该 `$c` 变量是在本地计算机上定义的。</span><span class="sxs-lookup"><span data-stu-id="e31c1-152">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="e31c1-153">在 Windows PowerShell 3.0 中引入了 **Using** 作用域修饰符。</span><span class="sxs-lookup"><span data-stu-id="e31c1-153">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="e31c1-154">有关 **Using** 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](./about/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e31c1-154">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="e31c1-155">第四个命令使用 `Invoke-Command` `Wait-Job` 在会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="e31c1-155">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="e31c1-156">它使用 **Any** 参数等待，直到远程计算机上的第一个作业终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-156">It uses the **Any** parameter to wait until the first job on the remote computers is terminating state.</span></span>

### <span data-ttu-id="e31c1-157">示例4：设置远程计算机上的作业的等待时间</span><span class="sxs-lookup"><span data-stu-id="e31c1-157">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

<span data-ttu-id="e31c1-158">此示例演示如何使用的 **Timeout** 参数设置在 `Wait-Job` 远程计算机上运行的作业的最长等待时间。</span><span class="sxs-lookup"><span data-stu-id="e31c1-158">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="e31c1-159">第一个命令在 (Server01、Server02 和 Server03) 的三台远程计算机上创建 **pssession** ，然后将 **pssession** 对象存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-159">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="e31c1-160">第二个命令使用在 `Invoke-Command` `Start-Job` 中的每个 **PSSession** 对象中运行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-160">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="e31c1-161">它将生成的作业对象存储在 `$jobs` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-161">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="e31c1-162">第三个命令使用 `Invoke-Command` `Wait-Job` 在中的每个会话中运行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-162">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="e31c1-163">`Wait-Job`命令确定所有命令是否在30秒内完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-163">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="e31c1-164">它使用值为30的 **Timeout** 参数来建立最长等待时间，然后将命令的结果存储在 `$done` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-164">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="e31c1-165">在此示例中，30 秒后，只有 Server02 计算机上的命令完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-165">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="e31c1-166">`Wait-Job` 结束等待，返回表示已完成作业的对象，然后显示命令提示符。</span><span class="sxs-lookup"><span data-stu-id="e31c1-166">`Wait-Job` ends the wait, returns the object that represents the job that was completed, and displays the command prompt.</span></span>

<span data-ttu-id="e31c1-167">`$done`变量包含一个作业对象，该对象表示在 Server02 上运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-167">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="e31c1-168">示例5：等待多个作业中的一个完成</span><span class="sxs-lookup"><span data-stu-id="e31c1-168">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="e31c1-169">此命令按 Id 标识三个作业，并等待其中任何一个作业处于终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-169">This command identifies three jobs by their IDs and waits until any one of them are in a terminating state.</span></span> <span data-ttu-id="e31c1-170">当第一个作业完成时，执行将继续。</span><span class="sxs-lookup"><span data-stu-id="e31c1-170">Execution continues when the first job finishes.</span></span>

### <span data-ttu-id="e31c1-171">示例6：等待一段时间，然后允许作业在后台继续</span><span class="sxs-lookup"><span data-stu-id="e31c1-171">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="e31c1-172">此命令120等待 DailyLog 作业 (两分钟) ，直到完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-172">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="e31c1-173">如果作业未在接下来的两分钟内完成，则执行将继续，并且作业继续在后台运行。</span><span class="sxs-lookup"><span data-stu-id="e31c1-173">If the job does not finish in the next two minutes, execution continues, and the job continues to run in the background.</span></span>

### <span data-ttu-id="e31c1-174">示例7：按名称等待作业</span><span class="sxs-lookup"><span data-stu-id="e31c1-174">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="e31c1-175">此命令使用作业名称来标识要等待的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-175">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="e31c1-176">示例8：等待本地计算机上的作业开始 Start-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-176">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="e31c1-177">此示例演示如何 `Wait-Job` 通过使用将 cmdlet 用于本地计算机上启动的作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-177">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="e31c1-178">这些命令启动一个可获取在上一周添加或更新的 Windows PowerShell 脚本文件的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-178">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="e31c1-179">第一个命令使用 `Start-Job` 在本地计算机上启动作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-179">The first command uses `Start-Job` to start a job on the local computer.</span></span> <span data-ttu-id="e31c1-180">作业运行一个 `Get-ChildItem` 命令，该命令获取在上周添加或更新的文件扩展名为 ps1 的所有文件。</span><span class="sxs-lookup"><span data-stu-id="e31c1-180">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="e31c1-181">第三个命令使用 `Wait-Job` 等待直到作业处于终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-181">The third command uses `Wait-Job` to wait until the job is in a terminating state.</span></span> <span data-ttu-id="e31c1-182">作业完成后，该命令将显示作业对象，该对象包含有关作业的信息。</span><span class="sxs-lookup"><span data-stu-id="e31c1-182">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="e31c1-183">示例9：使用 Invoke-Command 等待远程计算机上启动的作业</span><span class="sxs-lookup"><span data-stu-id="e31c1-183">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="e31c1-184">此示例演示如何 `Wait-Job` 通过使用的 **AsJob** 参数，将用于远程计算机上启动的作业 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-184">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="e31c1-185">使用 **AsJob** 时，将在本地计算机上创建作业，并自动将结果返回到本地计算机，即使作业运行在远程计算机上也是如此。</span><span class="sxs-lookup"><span data-stu-id="e31c1-185">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="e31c1-186">此示例使用 `Wait-Job` 来确定 `Get-Process` 三台远程计算机上的会话中运行的命令是否处于终止状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-186">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is in a terminating state.</span></span>

<span data-ttu-id="e31c1-187">第一个命令在三台计算机上创建 **PSSession** 对象并将其存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-187">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="e31c1-188">第二个命令使用在 `Invoke-Command` `Get-Process` 中的三个会话中运行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-188">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="e31c1-189">该命令使用 **AsJob** 参数以异步方式将命令作为作业运行。</span><span class="sxs-lookup"><span data-stu-id="e31c1-189">The command uses the **AsJob** parameter to run the command asynchronously as a job.</span></span> <span data-ttu-id="e31c1-190">命令返回一个作业对象，就像使用启动的作业一样， `Start-Job` 作业对象存储在 `$j` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e31c1-190">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="e31c1-191">第三个命令使用管道运算符 (`|`) 将作业对象发送 `$j` 到 `Wait-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e31c1-191">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="e31c1-192">`Invoke-Command`在这种情况下，不需要使用命令，因为作业驻留在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="e31c1-192">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="e31c1-193">示例10：等待 ID 为的作业</span><span class="sxs-lookup"><span data-stu-id="e31c1-193">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="e31c1-194">此命令等待 ID 值为 1 的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-194">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="e31c1-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e31c1-195">PARAMETERS</span></span>

### <span data-ttu-id="e31c1-196">-Any</span><span class="sxs-lookup"><span data-stu-id="e31c1-196">-Any</span></span>

<span data-ttu-id="e31c1-197">指示此 cmdlet 返回作业对象并在任何作业完成时继续执行。</span><span class="sxs-lookup"><span data-stu-id="e31c1-197">Indicates that this cmdlet returns the job object and continues execution when any job finishes.</span></span> <span data-ttu-id="e31c1-198">默认情况下，将 `Wait-Job` 一直等待，直到所有指定的作业完成后才显示提示。</span><span class="sxs-lookup"><span data-stu-id="e31c1-198">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="e31c1-199">-Filter</span><span class="sxs-lookup"><span data-stu-id="e31c1-199">-Filter</span></span>

<span data-ttu-id="e31c1-200">指定条件的哈希表。</span><span class="sxs-lookup"><span data-stu-id="e31c1-200">Specifies a hash table of conditions.</span></span> <span data-ttu-id="e31c1-201">此 cmdlet 将等待满足哈希表中所有条件的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-201">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="e31c1-202">输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。</span><span class="sxs-lookup"><span data-stu-id="e31c1-202">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="e31c1-203">此参数仅适用于自定义作业类型，例如工作流作业和计划作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-203">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="e31c1-204">它不适用于标准作业，如使用 cmdlet 创建的作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-204">It does not work on standard jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="e31c1-205">有关支持此参数的信息，请参阅作业类型的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="e31c1-205">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="e31c1-206">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="e31c1-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-207">-Force</span><span class="sxs-lookup"><span data-stu-id="e31c1-207">-Force</span></span>

<span data-ttu-id="e31c1-208">指示此 cmdlet 继续等待处于 "挂起" 或 "已断开连接" 状态的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-208">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="e31c1-209">默认情况下， `Wait-Job` 当作业处于以下状态之一时，将返回或结束等待：</span><span class="sxs-lookup"><span data-stu-id="e31c1-209">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="e31c1-210">已完成</span><span class="sxs-lookup"><span data-stu-id="e31c1-210">Completed</span></span>
- <span data-ttu-id="e31c1-211">已失败</span><span class="sxs-lookup"><span data-stu-id="e31c1-211">Failed</span></span>
- <span data-ttu-id="e31c1-212">已停止</span><span class="sxs-lookup"><span data-stu-id="e31c1-212">Stopped</span></span>
- <span data-ttu-id="e31c1-213">Suspended</span><span class="sxs-lookup"><span data-stu-id="e31c1-213">Suspended</span></span>
- <span data-ttu-id="e31c1-214">已断开连接</span><span class="sxs-lookup"><span data-stu-id="e31c1-214">Disconnected</span></span>

<span data-ttu-id="e31c1-215">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="e31c1-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e31c1-216">-Id</span><span class="sxs-lookup"><span data-stu-id="e31c1-216">-Id</span></span>

<span data-ttu-id="e31c1-217">指定此 cmdlet 等待的作业的 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="e31c1-217">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="e31c1-218">ID 是一个整数，用于唯一标识当前会话中的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-218">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="e31c1-219">它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e31c1-219">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="e31c1-220">你可以键入一个或多个 Id （以逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="e31c1-220">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="e31c1-221">若要查找作业的 ID，请键入 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-221">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-222">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e31c1-222">-InstanceId</span></span>

<span data-ttu-id="e31c1-223">指定此 cmdlet 等待的作业的实例 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="e31c1-223">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="e31c1-224">默认值为所有作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-224">The default is all jobs.</span></span>

<span data-ttu-id="e31c1-225">实例 ID 是一个 GUID，用于在计算机上唯一标识作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-225">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="e31c1-226">若要查找作业的实例 ID，请使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e31c1-226">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-227">-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-227">-Job</span></span>

<span data-ttu-id="e31c1-228">指定此 cmdlet 要等待的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-228">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="e31c1-229">输入一个包含作业对象的变量或可获取作业对象的命令。</span><span class="sxs-lookup"><span data-stu-id="e31c1-229">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="e31c1-230">你还可以使用管道运算符将作业对象发送到 `Wait-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e31c1-230">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="e31c1-231">默认情况下， `Wait-Job` 将等待在当前会话中创建的所有作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-231">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-232">-Name</span><span class="sxs-lookup"><span data-stu-id="e31c1-232">-Name</span></span>

<span data-ttu-id="e31c1-233">指定此 cmdlet 等待的作业的友好名称。</span><span class="sxs-lookup"><span data-stu-id="e31c1-233">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-234">-State</span><span class="sxs-lookup"><span data-stu-id="e31c1-234">-State</span></span>

<span data-ttu-id="e31c1-235">指定作业状态。</span><span class="sxs-lookup"><span data-stu-id="e31c1-235">Specifies a job state.</span></span> <span data-ttu-id="e31c1-236">此 cmdlet 仅等待处于指定状态的作业。</span><span class="sxs-lookup"><span data-stu-id="e31c1-236">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="e31c1-237">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="e31c1-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e31c1-238">NotStarted</span><span class="sxs-lookup"><span data-stu-id="e31c1-238">NotStarted</span></span>
- <span data-ttu-id="e31c1-239">正在运行</span><span class="sxs-lookup"><span data-stu-id="e31c1-239">Running</span></span>
- <span data-ttu-id="e31c1-240">已完成</span><span class="sxs-lookup"><span data-stu-id="e31c1-240">Completed</span></span>
- <span data-ttu-id="e31c1-241">已失败</span><span class="sxs-lookup"><span data-stu-id="e31c1-241">Failed</span></span>
- <span data-ttu-id="e31c1-242">已停止</span><span class="sxs-lookup"><span data-stu-id="e31c1-242">Stopped</span></span>
- <span data-ttu-id="e31c1-243">已阻止</span><span class="sxs-lookup"><span data-stu-id="e31c1-243">Blocked</span></span>
- <span data-ttu-id="e31c1-244">Suspended</span><span class="sxs-lookup"><span data-stu-id="e31c1-244">Suspended</span></span>
- <span data-ttu-id="e31c1-245">已断开连接</span><span class="sxs-lookup"><span data-stu-id="e31c1-245">Disconnected</span></span>
- <span data-ttu-id="e31c1-246">正在暂停</span><span class="sxs-lookup"><span data-stu-id="e31c1-246">Suspending</span></span>
- <span data-ttu-id="e31c1-247">正在停止</span><span class="sxs-lookup"><span data-stu-id="e31c1-247">Stopping</span></span>

<span data-ttu-id="e31c1-248">有关作业状态的详细信息，请参阅 [JobState 枚举](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="e31c1-248">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-249">-Timeout</span><span class="sxs-lookup"><span data-stu-id="e31c1-249">-Timeout</span></span>

<span data-ttu-id="e31c1-250">指定每个作业的最长等待时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="e31c1-250">Specifies the maximum wait time for each job, in seconds.</span></span> <span data-ttu-id="e31c1-251">默认值为-1，指示该 cmdlet 将等待直到作业完成。</span><span class="sxs-lookup"><span data-stu-id="e31c1-251">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="e31c1-252">提交命令时将开始计时 `Wait-Job` ，而不是 `Start-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="e31c1-252">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="e31c1-253">如果超过此时间，则等待结束，并继续执行，即使作业仍在运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="e31c1-253">If this time is exceeded, the wait ends and execution continues, even if the job is still running.</span></span>
<span data-ttu-id="e31c1-254">此命令不会显示任何错误消息。</span><span class="sxs-lookup"><span data-stu-id="e31c1-254">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e31c1-255">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e31c1-255">CommonParameters</span></span>

<span data-ttu-id="e31c1-256">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e31c1-256">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e31c1-257">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e31c1-257">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e31c1-258">输入</span><span class="sxs-lookup"><span data-stu-id="e31c1-258">INPUTS</span></span>

### <span data-ttu-id="e31c1-259">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="e31c1-259">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="e31c1-260">可以通过管道将作业对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e31c1-260">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="e31c1-261">输出</span><span class="sxs-lookup"><span data-stu-id="e31c1-261">OUTPUTS</span></span>

### <span data-ttu-id="e31c1-262">System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="e31c1-262">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="e31c1-263">此 cmdlet 将返回表示处于终止状态的作业的作业对象。</span><span class="sxs-lookup"><span data-stu-id="e31c1-263">This cmdlet returns job objects that represent the jobs in a terminating state.</span></span> <span data-ttu-id="e31c1-264">如果等待由于超过 **Timeout** 参数的值而结束，则 `Wait-Job` 不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="e31c1-264">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="e31c1-265">注释</span><span class="sxs-lookup"><span data-stu-id="e31c1-265">NOTES</span></span>

<span data-ttu-id="e31c1-266">默认情况下， `Wait-Job` 当作业处于以下状态之一时，将返回或结束等待：</span><span class="sxs-lookup"><span data-stu-id="e31c1-266">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="e31c1-267">已完成</span><span class="sxs-lookup"><span data-stu-id="e31c1-267">Completed</span></span>
- <span data-ttu-id="e31c1-268">已失败</span><span class="sxs-lookup"><span data-stu-id="e31c1-268">Failed</span></span>
- <span data-ttu-id="e31c1-269">已停止</span><span class="sxs-lookup"><span data-stu-id="e31c1-269">Stopped</span></span>
- <span data-ttu-id="e31c1-270">已挂起</span><span class="sxs-lookup"><span data-stu-id="e31c1-270">Suspended</span></span>
- <span data-ttu-id="e31c1-271">断开连接以 `Wait-Job` 继续等待挂起和断开连接的作业，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="e31c1-271">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="e31c1-272">相关链接</span><span class="sxs-lookup"><span data-stu-id="e31c1-272">RELATED LINKS</span></span>

[<span data-ttu-id="e31c1-273">Get-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-273">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="e31c1-274">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e31c1-274">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e31c1-275">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-275">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="e31c1-276">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-276">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="e31c1-277">Start-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-277">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="e31c1-278">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="e31c1-278">Stop-Job</span></span>](Stop-Job.md)
