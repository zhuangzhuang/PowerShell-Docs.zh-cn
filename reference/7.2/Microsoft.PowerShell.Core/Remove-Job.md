---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603817"
---
# <span data-ttu-id="e1b5c-102">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-102">Remove-Job</span></span>

## <span data-ttu-id="e1b5c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e1b5c-103">SYNOPSIS</span></span>
<span data-ttu-id="e1b5c-104">删除 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-104">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="e1b5c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1b5c-105">SYNTAX</span></span>

### <span data-ttu-id="e1b5c-106">SessionIdParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="e1b5c-106">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-107">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-108">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-109">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-110">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-110">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-111">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b5c-112">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1b5c-112">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e1b5c-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1b5c-113">DESCRIPTION</span></span>

<span data-ttu-id="e1b5c-114">`Remove-Job`Cmdlet 会删除由 `Start-Job` cmdlet 或 cmdlet （如 `Invoke-Command` 支持 **AsJob** 参数）启动的 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-114">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="e1b5c-115">您可以使用 `Remove-Job` 删除所有作业或删除所选作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-115">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="e1b5c-116">作业由其 **名称**、 **ID**、 **实例 ID**、 **命令** 或 **状态** 标识。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-116">The jobs are identified by their **Name**, **ID**, **Instance ID**, **Command**, or **State**.</span></span> <span data-ttu-id="e1b5c-117">或者，作业对象可以向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-117">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="e1b5c-118">如果没有参数或参数值，则无效 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-118">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="e1b5c-119">由于 PowerShell 3.0， `Remove-Job` 可以删除自定义作业类型，例如计划作业和工作流作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-119">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="e1b5c-120">例如， `Remove-Job` 删除计划作业、磁盘上计划作业的所有实例，以及所有触发的作业实例的结果。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-120">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="e1b5c-121">如果尝试删除正在运行的作业，将 `Remove-Job` 失败。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-121">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="e1b5c-122">使用 `Stop-Job` cmdlet 可停止正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-122">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="e1b5c-123">或者，使用 `Remove-Job` **Force** 参数删除正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-123">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="e1b5c-124">作业将保留在全局作业缓存中，直到删除后台作业或关闭 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-124">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="e1b5c-125">示例</span><span class="sxs-lookup"><span data-stu-id="e1b5c-125">EXAMPLES</span></span>

### <span data-ttu-id="e1b5c-126">示例1：使用作业名称删除作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-126">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="e1b5c-127">此示例使用变量和管道按名称删除作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-127">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="e1b5c-128">`Get-Job` 使用 **Name** 参数来指定作业 **BatchJob**。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-128">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob**.</span></span> <span data-ttu-id="e1b5c-129">作业对象存储在 `$batch` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-129">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="e1b5c-130">中的对象 `$batch` 将向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-130">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="e1b5c-131">一种替代方法是使用 **作业** 参数，如 `Remove-Job -Job $batch` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-131">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="e1b5c-132">示例2：删除会话中的所有作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-132">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="e1b5c-133">在此示例中，将删除当前 PowerShell 会话中的所有作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-133">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="e1b5c-134">`Get-Job` 获取当前 PowerShell 会话中的所有作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-134">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="e1b5c-135">作业对象将向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-135">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="e1b5c-136">示例3：删除 NotStarted 作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-136">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="e1b5c-137">此示例将从当前 PowerShell 会话中删除尚未启动的所有作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-137">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="e1b5c-138">`Remove-Job` 使用 **State** 参数指定作业状态。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-138">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="e1b5c-139">示例4：使用友好名称删除作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-139">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="e1b5c-140">此示例将从当前会话中删除具有以 \* batch \* \* 结尾的友好名称的所有作业，包括正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-140">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="e1b5c-141">`Remove-Job` 使用 **Name** 参数来指定作业名称模式。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-141">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="e1b5c-142">此模式包含星号 (`*`) 通配符，以查找以 **批处理** 结尾的所有作业名称。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-142">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch**.</span></span> <span data-ttu-id="e1b5c-143">**Force** 参数删除运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-143">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="e1b5c-144">示例5：删除 Invoke-Command 创建的作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-144">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="e1b5c-145">此示例将使用 `Invoke-Command` 带有 **AsJob** 参数的远程计算机上删除已启动的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-145">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="e1b5c-146">由于该示例使用了 **AsJob** 参数，因此在本地计算机上创建了作业对象。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-146">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="e1b5c-147">但该作业在远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-147">But, the job runs on a remote computer.</span></span> <span data-ttu-id="e1b5c-148">因此，你可以使用本地命令来管理作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-148">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="e1b5c-149">`Invoke-Command` 在 **Server01** 计算机上运行作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-149">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="e1b5c-150">**AsJob** 参数将 **ScriptBlock** 作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-150">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="e1b5c-151">作业对象存储在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-151">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="e1b5c-152">`$job`变量对象将向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-152">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="e1b5c-153">示例6：删除由 Invoke-Command 和 Start-Job 创建的作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-153">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="e1b5c-154">此示例演示如何删除使用运行的启动的远程计算机上的作业 `Invoke-Command` `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-154">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="e1b5c-155">在远程计算机上创建作业对象，并使用远程命令来管理该作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-155">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="e1b5c-156">运行远程命令时需要持续连接 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-156">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="e1b5c-157">`New-PSSession`创建与 **Server01** 计算机的 **PSSession**（持久连接）。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-157">`New-PSSession` creates a **PSSession**, a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="e1b5c-158">该连接保存在变量中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-158">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="e1b5c-159">`Invoke-Command` 连接到保存在中的会话 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-159">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="e1b5c-160">**ScriptBlock** 使用 `Start-Job` 来启动远程作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-160">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="e1b5c-161">作业运行 `Get-Process` 命令，并使用 **Name** 参数指定友好的作业名称 **MyJob**。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-161">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob**.</span></span>

<span data-ttu-id="e1b5c-162">`Invoke-Command` 使用 `$S` 会话并运行 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-162">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="e1b5c-163">**Name** 参数指定已删除名为 **MyJob** 的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-163">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="e1b5c-164">示例7：通过使用其实例 Id 删除作业</span><span class="sxs-lookup"><span data-stu-id="e1b5c-164">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="e1b5c-165">此示例根据作业的 **InstanceId** 删除作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-165">This example removes a job based on its **InstanceId**.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="e1b5c-166">`Start-Job` 启动一个后台作业，该作业对象保存在变量中 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-166">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="e1b5c-167">中的对象 `$job` 将向下发送到 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-167">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="e1b5c-168">**Property** 参数使用星号 (`*`) 来指定对象的所有属性都显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-168">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="e1b5c-169">`Remove-Job` 使用 **InstanceId** 参数指定要删除的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-169">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="e1b5c-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1b5c-170">PARAMETERS</span></span>

### <span data-ttu-id="e1b5c-171">-Command</span><span class="sxs-lookup"><span data-stu-id="e1b5c-171">-Command</span></span>

<span data-ttu-id="e1b5c-172">删除命令中包含指定的词的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-172">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="e1b5c-173">可以输入以逗号分隔的数组。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-173">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1b5c-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e1b5c-174">-Confirm</span></span>

<span data-ttu-id="e1b5c-175">在运行之前提示你进行确认 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-175">Prompts you for confirmation before `Remove-Job` is run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1b5c-176">-Filter</span><span class="sxs-lookup"><span data-stu-id="e1b5c-176">-Filter</span></span>

<span data-ttu-id="e1b5c-177">删除满足在关联的哈希表中建立的所有条件的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-177">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="e1b5c-178">输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-178">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="e1b5c-179">此参数仅适用于自定义作业类型，例如工作流作业和计划作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-179">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="e1b5c-180">它不适用于标准后台作业，例如通过使用创建的作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-180">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="e1b5c-181">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-181">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e1b5c-182">-Force</span><span class="sxs-lookup"><span data-stu-id="e1b5c-182">-Force</span></span>

<span data-ttu-id="e1b5c-183">即使作业的状态为 **正在运行**，也会删除该作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-183">Deletes a job even if the job's state is **Running**.</span></span> <span data-ttu-id="e1b5c-184">如果未指定 **Force** 参数，则 `Remove-Job` 不会删除正在运行的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-184">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1b5c-185">-Id</span><span class="sxs-lookup"><span data-stu-id="e1b5c-185">-Id</span></span>

<span data-ttu-id="e1b5c-186">删除具有指定 **Id** 的后台作业。可以输入以逗号分隔的数组。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-186">Deletes background jobs with the specified **Id**. You can enter a comma-separated array.</span></span> <span data-ttu-id="e1b5c-187">作业的 **Id** 是用于标识当前会话中的作业的唯一整数。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-187">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="e1b5c-188">若要查找作业的 **Id**，请使用 `Get-Job` 不带参数的。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-188">To find a job's **Id**, use `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="e1b5c-189">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e1b5c-189">-InstanceId</span></span>

<span data-ttu-id="e1b5c-190">删除具有指定 **InstanceId** 的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-190">Deletes jobs with the specified **InstanceId**.</span></span> <span data-ttu-id="e1b5c-191">可以输入以逗号分隔的数组。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-191">You can enter a comma-separated array.</span></span> <span data-ttu-id="e1b5c-192">**InstanceId** 是用于标识作业的唯一 GUID。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-192">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="e1b5c-193">若要查找作业的 **InstanceId**，请使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-193">To find a job's **InstanceId**, use `Get-Job`.</span></span>

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

### <span data-ttu-id="e1b5c-194">-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-194">-Job</span></span>

<span data-ttu-id="e1b5c-195">指定要删除的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-195">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="e1b5c-196">请输入一个包含作业的变量，或一个可获取作业的命令。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-196">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="e1b5c-197">可以输入以逗号分隔的数组。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-197">You can enter a comma-separated array.</span></span>

<span data-ttu-id="e1b5c-198">可以将作业对象向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-198">You can send job objects down the pipeline to `Remove-Job`.</span></span>

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

### <span data-ttu-id="e1b5c-199">-Name</span><span class="sxs-lookup"><span data-stu-id="e1b5c-199">-Name</span></span>

<span data-ttu-id="e1b5c-200">仅删除具有指定友好名称的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-200">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="e1b5c-201">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-201">Wildcards are permitted.</span></span> <span data-ttu-id="e1b5c-202">可以输入以逗号分隔的数组。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-202">You can enter a comma-separated array.</span></span>

<span data-ttu-id="e1b5c-203">作业的友好名称并不保证在 PowerShell 会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-203">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="e1b5c-204">按名称删除文件时，请使用 **WhatIf** 和 **Confirm** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-204">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e1b5c-205">-State</span><span class="sxs-lookup"><span data-stu-id="e1b5c-205">-State</span></span>

<span data-ttu-id="e1b5c-206">仅删除具有指定状态的作业。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-206">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="e1b5c-207">若要删除状态为 " **正在运行**" 的作业，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-207">To delete jobs with a state of **Running**, use the **Force** parameter.</span></span>

<span data-ttu-id="e1b5c-208">接受的值：</span><span class="sxs-lookup"><span data-stu-id="e1b5c-208">Accepted values:</span></span>

- <span data-ttu-id="e1b5c-209">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e1b5c-209">AtBreakpoint</span></span>
- <span data-ttu-id="e1b5c-210">已阻止</span><span class="sxs-lookup"><span data-stu-id="e1b5c-210">Blocked</span></span>
- <span data-ttu-id="e1b5c-211">已完成</span><span class="sxs-lookup"><span data-stu-id="e1b5c-211">Completed</span></span>
- <span data-ttu-id="e1b5c-212">已断开连接</span><span class="sxs-lookup"><span data-stu-id="e1b5c-212">Disconnected</span></span>
- <span data-ttu-id="e1b5c-213">Failed</span><span class="sxs-lookup"><span data-stu-id="e1b5c-213">Failed</span></span>
- <span data-ttu-id="e1b5c-214">NotStarted</span><span class="sxs-lookup"><span data-stu-id="e1b5c-214">NotStarted</span></span>
- <span data-ttu-id="e1b5c-215">运行</span><span class="sxs-lookup"><span data-stu-id="e1b5c-215">Running</span></span>
- <span data-ttu-id="e1b5c-216">已停止</span><span class="sxs-lookup"><span data-stu-id="e1b5c-216">Stopped</span></span>
- <span data-ttu-id="e1b5c-217">正在停止</span><span class="sxs-lookup"><span data-stu-id="e1b5c-217">Stopping</span></span>
- <span data-ttu-id="e1b5c-218">已挂起</span><span class="sxs-lookup"><span data-stu-id="e1b5c-218">Suspended</span></span>
- <span data-ttu-id="e1b5c-219">正在暂停</span><span class="sxs-lookup"><span data-stu-id="e1b5c-219">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1b5c-220">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e1b5c-220">-WhatIf</span></span>

<span data-ttu-id="e1b5c-221">显示运行时将发生 `Remove-Job` 的情况。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-221">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="e1b5c-222">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-222">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1b5c-223">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1b5c-223">CommonParameters</span></span>

<span data-ttu-id="e1b5c-224">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-224">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1b5c-225">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-225">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1b5c-226">输入</span><span class="sxs-lookup"><span data-stu-id="e1b5c-226">INPUTS</span></span>

### <span data-ttu-id="e1b5c-227">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-227">System.Management.Automation.Job</span></span>

<span data-ttu-id="e1b5c-228">可以将作业对象向下发送到 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-228">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="e1b5c-229">输出</span><span class="sxs-lookup"><span data-stu-id="e1b5c-229">OUTPUTS</span></span>

### <span data-ttu-id="e1b5c-230">无</span><span class="sxs-lookup"><span data-stu-id="e1b5c-230">None</span></span>

<span data-ttu-id="e1b5c-231">`Remove-Job` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-231">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="e1b5c-232">注释</span><span class="sxs-lookup"><span data-stu-id="e1b5c-232">NOTES</span></span>

<span data-ttu-id="e1b5c-233">PowerShell 作业创建一个新进程。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-233">A PowerShell job creates a new process.</span></span> <span data-ttu-id="e1b5c-234">作业完成后，进程将退出。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-234">When the job completes, the process exits.</span></span> <span data-ttu-id="e1b5c-235">当 `Remove-Job` 运行时，作业的状态将被删除。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-235">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="e1b5c-236">如果作业在完成之前停止并且其进程尚未退出，则会强行终止进程。</span><span class="sxs-lookup"><span data-stu-id="e1b5c-236">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="e1b5c-237">相关链接</span><span class="sxs-lookup"><span data-stu-id="e1b5c-237">RELATED LINKS</span></span>

[<span data-ttu-id="e1b5c-238">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="e1b5c-238">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="e1b5c-239">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="e1b5c-239">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="e1b5c-240">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="e1b5c-240">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="e1b5c-241">Get-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="e1b5c-242">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e1b5c-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e1b5c-243">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-243">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="e1b5c-244">Start-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-244">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="e1b5c-245">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-245">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="e1b5c-246">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="e1b5c-246">Wait-Job</span></span>](Wait-Job.md)

