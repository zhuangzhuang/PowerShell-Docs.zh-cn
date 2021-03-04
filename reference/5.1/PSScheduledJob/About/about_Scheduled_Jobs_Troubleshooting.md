---
description: 说明如何解决计划作业的问题
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: aac2133cee4abdd7e50e7b433104b9578d74b0a8
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685850"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="a11b4-104">关于计划作业故障排除</span><span class="sxs-lookup"><span data-stu-id="a11b4-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="a11b4-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="a11b4-105">Short description</span></span>

<span data-ttu-id="a11b4-106">说明如何解决计划作业的问题</span><span class="sxs-lookup"><span data-stu-id="a11b4-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="a11b4-107">长说明</span><span class="sxs-lookup"><span data-stu-id="a11b4-107">Long description</span></span>

<span data-ttu-id="a11b4-108">本文档介绍了使用 PowerShell 的计划作业功能时可能会遇到的一些问题，并建议解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="a11b4-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="a11b4-109">使用 PowerShell 计划作业之前，请参阅 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 和相关的计划作业。</span><span class="sxs-lookup"><span data-stu-id="a11b4-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="a11b4-110">有关 **PSScheduledJob** 模块中包含的 cmdlet 的详细信息，请参阅 [PSScheduledJob](xref:PSScheduledJob)。</span><span class="sxs-lookup"><span data-stu-id="a11b4-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="a11b4-111">找不到作业结果</span><span class="sxs-lookup"><span data-stu-id="a11b4-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="a11b4-112">在 PowerShell 中获取作业结果的基本方法</span><span class="sxs-lookup"><span data-stu-id="a11b4-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="a11b4-113">当计划作业运行时，它会创建计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="a11b4-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="a11b4-114">若要查看、管理和获取计划作业实例的结果，请使用作业 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11b4-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="a11b4-115">若要在计划作业的实例上使用作业 cmdlet，则必须将 **PSScheduledJob** 模块导入到会话中。</span><span class="sxs-lookup"><span data-stu-id="a11b4-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="a11b4-116">若要导入 **PSScheduledJob** 模块，请键入 `Import-Module PSScheduledJob` 或使用任何计划的作业 cmdlet，例如 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="a11b4-117">若要获取某个计划作业的所有实例的列表，请使用 `Get-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11b4-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="a11b4-118">`Get-Job`Cmdlet 将 **ProcessJob** 对象向下发送管道。</span><span class="sxs-lookup"><span data-stu-id="a11b4-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="a11b4-119">`Format-Table`Cmdlet 将在表中显示计划作业实例的 **Name**、 **ID** 和 **PSBeginTime** 属性。</span><span class="sxs-lookup"><span data-stu-id="a11b4-119">The `Format-Table` cmdlet displays the **Name**, **ID**, and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

<span data-ttu-id="a11b4-120">若要获取某个计划作业的实例的结果，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11b4-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="a11b4-121">以下命令获取 ProcessJob (ID = 50) 的最新实例的结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="a11b4-122">在磁盘上查找作业结果的基本方法</span><span class="sxs-lookup"><span data-stu-id="a11b4-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="a11b4-123">若要管理计划作业，请使用作业 cmdlet，例如 `Get-Job` 和 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="a11b4-124">如果 `Get-Job` 未获取作业实例或 `Receive-Job` 未获取作业结果，你可以在磁盘上搜索作业的执行历史记录文件。</span><span class="sxs-lookup"><span data-stu-id="a11b4-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="a11b4-125">执行历史记录包含所有触发的作业实例的记录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="a11b4-126">验证目录中是否存在用于以下路径中的计划作业的时间戳的目录：</span><span class="sxs-lookup"><span data-stu-id="a11b4-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="a11b4-127">例如：</span><span class="sxs-lookup"><span data-stu-id="a11b4-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="a11b4-128">例如，该 `Get-ChildItem` cmdlet 将获取 **ProcessJob** 计划作业的磁盘上执行历史记录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

<span data-ttu-id="a11b4-129">每个时间戳的目录都表示一个作业实例。</span><span class="sxs-lookup"><span data-stu-id="a11b4-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="a11b4-130">每个作业实例的结果保存在时间戳命名目录中的 **Results.xml** 文件中。</span><span class="sxs-lookup"><span data-stu-id="a11b4-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="a11b4-131">例如，以下命令将获取 **ProcessJob** 计划作业的每个已保存实例的 **Results.xml** 文件。</span><span class="sxs-lookup"><span data-stu-id="a11b4-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="a11b4-132">如果缺少 **Results.xml** 文件，则 PowerShell 无法返回或显示作业结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="a11b4-133">由于 **PSScheduledJob** 模块未导入到会话中，作业 cmdlet 可能无法获取计划的作业实例或其结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="a11b4-134">在计划的作业实例上使用 job cmdlet 之前，请验证会话中是否包含 **PSScheduledJob** 模块。</span><span class="sxs-lookup"><span data-stu-id="a11b4-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="a11b4-135">如果没有 **PSScheduledJob** 模块，作业 cmdlet 无法获取计划的作业实例或其结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="a11b4-136">导入 **PSScheduledJob** 模块：</span><span class="sxs-lookup"><span data-stu-id="a11b4-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="a11b4-137">Receive-Job cmdlet 可能已返回结果</span><span class="sxs-lookup"><span data-stu-id="a11b4-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="a11b4-138">如果不 `Receive-Job` 返回作业实例结果，则可能是因为 `Receive-Job` 在没有 **Keep** 参数的情况下，已在当前会话中为该作业实例运行了一个命令。</span><span class="sxs-lookup"><span data-stu-id="a11b4-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="a11b4-139">在不使用 `Receive-Job` **Keep** 参数的情况下，将 `Receive-Job` 返回作业结果，并将作业实例的 **HasMoreData** 属性设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="a11b4-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False**.</span></span> <span data-ttu-id="a11b4-140">**False** 值表示 `Receive-Job` 返回了作业的结果，并且实例没有更多要返回的结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="a11b4-141">此设置适用于标准后台作业，但不适用于保存在磁盘上的计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="a11b4-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="a11b4-142">若要再次获取作业实例结果，请通过键入启动新的 PowerShell 会话 `PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="a11b4-143">导入 **PSScheduledJob** 模块，然后重试该 `Receive-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="a11b4-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="a11b4-144">使用 Keep 参数在一个会话中多次获得结果</span><span class="sxs-lookup"><span data-stu-id="a11b4-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="a11b4-145">若要在一个会话中多次获取某一作业实例的结果，请使用该 cmdlet 的 **Keep** 参数 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="a11b4-146">计划的作业可能已损坏</span><span class="sxs-lookup"><span data-stu-id="a11b4-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="a11b4-147">如果计划的作业损坏，PowerShell 将删除已损坏的计划作业及其结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="a11b4-148">不能恢复已损坏的计划作业的结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="a11b4-149">若要确定计划的作业是否仍存在，请使用 `Get-ScheduledJob` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11b4-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="a11b4-150">结果数可能已超过 ExecutionHistoryLength</span><span class="sxs-lookup"><span data-stu-id="a11b4-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="a11b4-151">计划作业的 **ExecutionHistoryLength** 属性决定将多少作业实例及其结果保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="a11b4-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="a11b4-152">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="a11b4-152">The default value is 32.</span></span>
<span data-ttu-id="a11b4-153">当计划作业的实例数超过此值时，PowerShell 会删除最旧的作业实例，为每个新作业实例腾出空间。</span><span class="sxs-lookup"><span data-stu-id="a11b4-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="a11b4-154">若要获取某个计划作业的 **ExecutionHistoryLength** 属性的值，请使用以下命令格式：</span><span class="sxs-lookup"><span data-stu-id="a11b4-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="a11b4-155">例如，以下命令获取 **ProcessJob** 计划作业的 **ExecutionHistoryLength** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="a11b4-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="a11b4-156">若要设置或更改 **ExecutionHistoryLength** 属性的值，请使用和 Cmdlet 的 **MaxResultCount** 参数 `Register-ScheduledJob` `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="a11b4-157">以下命令将 **ExecutionHistoryLength** 属性的值增加到50。</span><span class="sxs-lookup"><span data-stu-id="a11b4-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="a11b4-158">作业实例结果可能已被删除</span><span class="sxs-lookup"><span data-stu-id="a11b4-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="a11b4-159">Cmdlet 的 **ClearExecutionHistory** 参数 `Set-ScheduledJob` 删除作业的执行历史记录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="a11b4-160">您可以使用此功能释放磁盘空间或删除不需要的结果，或者删除在不同位置分析或保存的结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="a11b4-161">若要删除计划作业的执行历史记录，请使用该计划作业的 **ClearExecutionHistory** 参数。</span><span class="sxs-lookup"><span data-stu-id="a11b4-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="a11b4-162">以下命令删除 **ProcessJob** 计划作业的执行历史记录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="a11b4-163">此外，cmdlet 还会 `Remove-Job` 删除作业结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="a11b4-164">当你使用 `Remove-Job` 删除计划的作业时，它将删除磁盘上的所有作业实例，包括执行历史记录和所有作业结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="a11b4-165">使用 Start-Job cmdlet 启动的作业不会保存到磁盘</span><span class="sxs-lookup"><span data-stu-id="a11b4-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="a11b4-166">当使用 `Start-Job` 启动计划作业时，将 `Start-Job` 启动标准后台作业，而不是使用作业触发器。</span><span class="sxs-lookup"><span data-stu-id="a11b4-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="a11b4-167">后台作业及其结果不存储在磁盘上作业的执行历史记录中。</span><span class="sxs-lookup"><span data-stu-id="a11b4-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="a11b4-168">你可以使用 `Get-Job` cmdlet 来获取作业和 `Receive-Job` cmdlet 以获取作业结果，但只有在收到这些结果后，才可使用该 cmdlet，除非你使用 Cmdlet 的 Keep 参数 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="a11b4-169">此外，后台作业及其结果都是特定于会话的;它们只存在于创建它们的会话中。</span><span class="sxs-lookup"><span data-stu-id="a11b4-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="a11b4-170">如果删除了该作业 `Remove-Job` ，请关闭会话或关闭 PowerShell，然后删除该作业实例及其结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="a11b4-171">计划的作业不运行</span><span class="sxs-lookup"><span data-stu-id="a11b4-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="a11b4-172">如果作业触发或计划作业处于禁用状态，则计划作业不会自动运行。</span><span class="sxs-lookup"><span data-stu-id="a11b4-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="a11b4-173">使用 `Get-ScheduledJob` cmdlet 来获取计划作业。</span><span class="sxs-lookup"><span data-stu-id="a11b4-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="a11b4-174">验证计划作业的 **Enabled** 属性的值是否为 **True**。</span><span class="sxs-lookup"><span data-stu-id="a11b4-174">Verify that the value of the **Enabled** property of the scheduled job is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="a11b4-175">使用 `Get-JobTrigger` cmdlet 可获取计划作业的作业触发器。</span><span class="sxs-lookup"><span data-stu-id="a11b4-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="a11b4-176">验证作业触发器的 **Enabled** 属性的值是否为 **True**。</span><span class="sxs-lookup"><span data-stu-id="a11b4-176">Verify that the value of the **Enabled** property of the job trigger is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="a11b4-177">如果作业触发器无效，则计划作业不会自动运行</span><span class="sxs-lookup"><span data-stu-id="a11b4-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="a11b4-178">例如，作业触发器可以指定过去的日期或不会发生的日期，如月份的第五个星期一。</span><span class="sxs-lookup"><span data-stu-id="a11b4-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="a11b4-179">如果未满足作业触发器或作业选项的条件，则计划作业不会自动运行。</span><span class="sxs-lookup"><span data-stu-id="a11b4-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="a11b4-180">例如，仅当特定用户登录到计算机时才会运行的计划作业不会运行（如果该用户未登录或仅远程连接）。</span><span class="sxs-lookup"><span data-stu-id="a11b4-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="a11b4-181">检查计划作业的选项，并确保满足这些选项。</span><span class="sxs-lookup"><span data-stu-id="a11b4-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="a11b4-182">例如，需要计算机处于空闲状态或需要网络连接的计划作业，或者永远不会运行长 **IdleDuration** 或短暂的 **IdleTimeout** 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="a11b4-183">使用 `Get-ScheduledJobOption` cmdlet 检查作业选项及其值。</span><span class="sxs-lookup"><span data-stu-id="a11b4-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="a11b4-184">有关计划作业选项的说明，请参阅 [get-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)。</span><span class="sxs-lookup"><span data-stu-id="a11b4-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="a11b4-185">计划的作业实例可能已失败</span><span class="sxs-lookup"><span data-stu-id="a11b4-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="a11b4-186">如果计划作业命令失败，则 PowerShell 会通过生成错误消息立即报告它。</span><span class="sxs-lookup"><span data-stu-id="a11b4-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="a11b4-187">但是，如果作业在任务计划程序尝试运行它时失败，则 PowerShell 将无法使用此错误。</span><span class="sxs-lookup"><span data-stu-id="a11b4-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="a11b4-188">使用以下方法来检测和更正作业故障：</span><span class="sxs-lookup"><span data-stu-id="a11b4-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="a11b4-189">检查任务计划程序事件日志中是否存在错误。</span><span class="sxs-lookup"><span data-stu-id="a11b4-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="a11b4-190">若要查看日志，请使用事件查看器或 PowerShell 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a11b4-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="a11b4-191">在任务计划程序中检查作业记录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="a11b4-192">PowerShell 计划作业存储在下列任务计划文件夹中：</span><span class="sxs-lookup"><span data-stu-id="a11b4-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="a11b4-193">由于权限不足，计划作业可能无法运行</span><span class="sxs-lookup"><span data-stu-id="a11b4-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="a11b4-194">计划作业使用创建作业的用户的权限运行，或使用或命令中的 **Credential** 参数指定的权限运行 `Register-ScheduledJob` `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="a11b4-195">如果该用户没有运行命令或脚本的权限，则该作业将失败。</span><span class="sxs-lookup"><span data-stu-id="a11b4-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="a11b4-196">无法获取计划作业或计划作业已损坏</span><span class="sxs-lookup"><span data-stu-id="a11b4-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="a11b4-197">在极少数情况下，计划作业可能会损坏或包含无法解析的内部矛盾。</span><span class="sxs-lookup"><span data-stu-id="a11b4-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="a11b4-198">通常，当手动编辑计划作业的 XML 文件时，会出现这种情况，从而导致无效的 XML。</span><span class="sxs-lookup"><span data-stu-id="a11b4-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="a11b4-199">如果计划的作业损坏，则 PowerShell 将尝试从磁盘删除计划作业、其执行历史记录和结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="a11b4-200">如果无法删除计划的作业，则每次运行该 cmdlet 时，都将收到损坏的作业错误消息 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="a11b4-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="a11b4-201">若要删除已损坏的计划作业，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="a11b4-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="a11b4-202">删除 `<ScheduledJobName>` 计划作业的目录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="a11b4-203">请勿删除 **get-scheduledjob** 目录。</span><span class="sxs-lookup"><span data-stu-id="a11b4-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="a11b4-204">目录的位置：</span><span class="sxs-lookup"><span data-stu-id="a11b4-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="a11b4-205">例如：</span><span class="sxs-lookup"><span data-stu-id="a11b4-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="a11b4-206">使用任务计划程序删除计划的作业。</span><span class="sxs-lookup"><span data-stu-id="a11b4-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="a11b4-207">PowerShell 计划任务出现在以下任务计划程序路径中：</span><span class="sxs-lookup"><span data-stu-id="a11b4-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="a11b4-208">作业 cmdlet 无法一致地查找计划作业</span><span class="sxs-lookup"><span data-stu-id="a11b4-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="a11b4-209">当 **PSScheduledJob** 模块不在当前会话中时，作业 cmdlet 无法获取计划作业、启动作业或获取其结果。</span><span class="sxs-lookup"><span data-stu-id="a11b4-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="a11b4-210">若要导入 **PSScheduledJob** 模块，请键入 `Import-Module PSScheduledJob` 或运行或获取该模块中的任何 cmdlet，如 `Get-ScheduledJob` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11b4-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="a11b4-211">从 PowerShell 3.0 开始，当你获取或使用模块中的任何 cmdlet 时，模块会自动导入。</span><span class="sxs-lookup"><span data-stu-id="a11b4-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="a11b4-212">当 **PSScheduledJob** 模块不在当前会话中时，可以执行以下命令序列。</span><span class="sxs-lookup"><span data-stu-id="a11b4-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="a11b4-213">之所以发生此行为，是因为该 `Get-ScheduledJob` 命令会自动导入 **PSScheduledJob** 模块，然后运行命令。</span><span class="sxs-lookup"><span data-stu-id="a11b4-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="a11b4-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a11b4-214">See also</span></span>

[<span data-ttu-id="a11b4-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="a11b4-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="a11b4-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="a11b4-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="a11b4-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="a11b4-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="a11b4-218">[PSScheduledJob](xref:PSScheduledJob) 模块 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a11b4-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="a11b4-219">任务计划程序</span><span class="sxs-lookup"><span data-stu-id="a11b4-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
