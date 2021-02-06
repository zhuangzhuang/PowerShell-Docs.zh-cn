---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 479c099d2d5daf1cc50c5c645be053ff4ae02bdc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595629"
---
# <span data-ttu-id="06f7b-102">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-102">Stop-Job</span></span>

## <span data-ttu-id="06f7b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="06f7b-103">SYNOPSIS</span></span>
<span data-ttu-id="06f7b-104">停止 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-104">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="06f7b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06f7b-105">SYNTAX</span></span>

### <span data-ttu-id="06f7b-106">SessionIdParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="06f7b-106">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06f7b-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="06f7b-107">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06f7b-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="06f7b-108">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06f7b-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="06f7b-109">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06f7b-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="06f7b-110">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="06f7b-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="06f7b-111">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="06f7b-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="06f7b-112">DESCRIPTION</span></span>

<span data-ttu-id="06f7b-113">`Stop-Job`Cmdlet 可停止正在进行的 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-113">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="06f7b-114">您可以使用此 cmdlet 停止所有作业，或者基于作业的名称、ID、实例 ID 或状态停止所选作业，或者通过将作业对象传递到来停止这些作业 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-114">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="06f7b-115">你可以使用 `Stop-Job` 来停止后台作业，如使用 `Start-Job` cmdlet 或任何 Cmdlet 的 **AsJob** 参数启动的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-115">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="06f7b-116">停止后台作业时，PowerShell 将完成该作业队列中挂起的所有任务，然后结束该作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-116">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="06f7b-117">提交此命令后，将不会有新任务添加到队列。</span><span class="sxs-lookup"><span data-stu-id="06f7b-117">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="06f7b-118">此 cmdlet 不删除后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-118">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="06f7b-119">若要删除作业，请使用 `Remove-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06f7b-119">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="06f7b-120">从 Windows PowerShell 3.0 开始， `Stop-Job` 还将停止自定义作业类型，例如工作流作业和计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="06f7b-120">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="06f7b-121">若要启用 `Stop-Job` 以停止具有自定义作业类型的作业，请在运行命令之前将支持自定义作业类型的模块导入到会话中，方法 `Stop-Job` 是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06f7b-121">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="06f7b-122">有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。</span><span class="sxs-lookup"><span data-stu-id="06f7b-122">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="06f7b-123">示例</span><span class="sxs-lookup"><span data-stu-id="06f7b-123">EXAMPLES</span></span>

### <span data-ttu-id="06f7b-124">示例1：使用 Invoke-Command 停止远程计算机上的作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-124">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="06f7b-125">此示例演示如何使用 `Stop-Job` cmdlet 停止在远程计算机上运行的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-125">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="06f7b-126">由于该作业是通过使用 `Invoke-Command` cmdlet 远程运行命令来启动的 `Start-Job` ，因此该作业对象存储在远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="06f7b-126">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="06f7b-127">您必须使用另一个 `Invoke-Command` 命令来 `Stop-Job` 远程运行命令。</span><span class="sxs-lookup"><span data-stu-id="06f7b-127">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="06f7b-128">有关远程后台作业的详细信息，请参阅 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="06f7b-128">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="06f7b-129">第一个命令在 Server01 计算机上创建 (**PSSession**) 的 PowerShell 会话，然后将该会话对象存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="06f7b-129">The first command creates a PowerShell session (**PSSession**) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="06f7b-130">该命令使用某个域管理员的凭据。</span><span class="sxs-lookup"><span data-stu-id="06f7b-130">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="06f7b-131">第二个命令使用 `Invoke-Command` cmdlet `Start-Job` 在会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="06f7b-131">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="06f7b-132">作业中的此命令将获取系统事件日志中的所有事件。</span><span class="sxs-lookup"><span data-stu-id="06f7b-132">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="06f7b-133">生成的作业对象存储在变量中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-133">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="06f7b-134">第三个命令停止作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-134">The third command stops the job.</span></span> <span data-ttu-id="06f7b-135">它使用 `Invoke-Command` cmdlet 在 `Stop-Job` Server01 上的 **PSSession** 中运行命令。</span><span class="sxs-lookup"><span data-stu-id="06f7b-135">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="06f7b-136">由于作业对象存储在 `$j` 本地计算机上的变量中，因此该命令将使用 Using 作用域修饰符来标识 `$j` 为局部变量。</span><span class="sxs-lookup"><span data-stu-id="06f7b-136">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="06f7b-137">有关 Using 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](about/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="06f7b-137">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="06f7b-138">命令完成后，作业将停止，中的 **PSSession** 可供 `$s` 使用。</span><span class="sxs-lookup"><span data-stu-id="06f7b-138">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="06f7b-139">示例2：停止后台作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-139">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="06f7b-140">此命令停止 Job1 后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-140">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="06f7b-141">示例3：停止多个后台作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-141">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="06f7b-142">此命令停止三个作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-142">This command stops three jobs.</span></span>
<span data-ttu-id="06f7b-143">它将通过 ID 来标识作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-143">It identifies them by their IDs.</span></span>

### <span data-ttu-id="06f7b-144">示例4：停止所有后台作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-144">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="06f7b-145">此命令停止当前会话中的所有后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-145">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="06f7b-146">示例5：停止所有阻止的后台作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-146">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="06f7b-147">此命令停止阻止的所有作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-147">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="06f7b-148">示例6：使用实例 ID 停止作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-148">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="06f7b-149">这些命令显示了如何根据作业的实例 ID 来停止作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-149">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="06f7b-150">第一个命令使用 `Get-Job` cmdlet 来获取当前会话中的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-150">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="06f7b-151">该命令使用管道运算符 (`|`) 将作业发送到 `Format-Table` 命令，该命令显示每个作业的指定属性的表。</span><span class="sxs-lookup"><span data-stu-id="06f7b-151">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="06f7b-152">该表包括每个作业的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="06f7b-152">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="06f7b-153">它使用计算属性来显示作业状态。</span><span class="sxs-lookup"><span data-stu-id="06f7b-153">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="06f7b-154">第二个命令使用 `Stop-Job` 带有 **InstanceID** 参数的命令停止选定的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-154">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="06f7b-155">示例7：停止远程计算机上的作业</span><span class="sxs-lookup"><span data-stu-id="06f7b-155">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="06f7b-156">此示例演示如何使用 `Stop-Job` cmdlet 停止在远程计算机上运行的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-156">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="06f7b-157">由于作业是使用 cmdlet 的 **AsJob** 参数启动的，因此 `Invoke-Command` 作业对象位于本地计算机上，即使作业运行在远程计算机上也是如此。</span><span class="sxs-lookup"><span data-stu-id="06f7b-157">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="06f7b-158">因此，你可以使用本地 `Stop-Job` 命令来停止作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-158">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="06f7b-159">第一个命令使用 `Invoke-Command` cmdlet 在 Server01 计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-159">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="06f7b-160">该命令使用 **AsJob** 参数将远程命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="06f7b-160">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="06f7b-161">此命令返回一个作业对象，该对象是 cmdlet 返回的相同作业对象 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-161">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="06f7b-162">该命令将作业对象保存在 `$j` 变量中。</span><span class="sxs-lookup"><span data-stu-id="06f7b-162">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="06f7b-163">第二个命令使用管道运算符将变量中的作业发送 `$j` 到 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-163">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="06f7b-164">该命令使用 **PassThru** 参数来指示 `Stop-Job` 返回作业对象。</span><span class="sxs-lookup"><span data-stu-id="06f7b-164">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="06f7b-165">作业对象显示确认作业的状态为 "已停止"。</span><span class="sxs-lookup"><span data-stu-id="06f7b-165">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="06f7b-166">有关远程后台作业的详细信息，请参阅 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="06f7b-166">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="06f7b-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06f7b-167">PARAMETERS</span></span>

### <span data-ttu-id="06f7b-168">-Filter</span><span class="sxs-lookup"><span data-stu-id="06f7b-168">-Filter</span></span>

<span data-ttu-id="06f7b-169">指定条件的哈希表。</span><span class="sxs-lookup"><span data-stu-id="06f7b-169">Specifies a hash table of conditions.</span></span> <span data-ttu-id="06f7b-170">此 cmdlet 将停止满足所有条件的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-170">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="06f7b-171">输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。</span><span class="sxs-lookup"><span data-stu-id="06f7b-171">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="06f7b-172">此参数仅适用于自定义作业类型，例如工作流作业和计划作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-172">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="06f7b-173">它不适用于标准后台作业，如使用 cmdlet 创建的作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-173">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="06f7b-174">有关支持此参数的信息，请参阅作业类型的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="06f7b-174">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="06f7b-175">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="06f7b-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06f7b-176">-Id</span><span class="sxs-lookup"><span data-stu-id="06f7b-176">-Id</span></span>

<span data-ttu-id="06f7b-177">指定此 cmdlet 停止的作业的 Id。</span><span class="sxs-lookup"><span data-stu-id="06f7b-177">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="06f7b-178">默认值为当前会话中的所有作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-178">The default is all jobs in the current session.</span></span>

<span data-ttu-id="06f7b-179">ID 是一个整数，用于唯一标识当前会话中的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-179">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="06f7b-180">它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="06f7b-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="06f7b-181">你可以键入一个或多个 Id （以逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="06f7b-181">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="06f7b-182">若要查找作业的 ID，请键入 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-182">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="06f7b-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="06f7b-183">-InstanceId</span></span>

<span data-ttu-id="06f7b-184">指定此 cmdlet 停止的作业的实例 Id。</span><span class="sxs-lookup"><span data-stu-id="06f7b-184">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="06f7b-185">默认值为所有作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-185">The default is all jobs.</span></span>

<span data-ttu-id="06f7b-186">实例 ID 是一个 GUID，用于在计算机上唯一标识作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="06f7b-187">若要查找作业的实例 ID，请使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="06f7b-187">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="06f7b-188">-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-188">-Job</span></span>

<span data-ttu-id="06f7b-189">指定此 cmdlet 停止的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-189">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="06f7b-190">请输入一个包含作业的变量，或一个可获取作业的命令。</span><span class="sxs-lookup"><span data-stu-id="06f7b-190">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="06f7b-191">你还可以使用管道运算符将作业提交到 `Stop-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06f7b-191">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="06f7b-192">默认情况下， `Stop-Job` 删除在当前会话中启动的所有作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-192">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="06f7b-193">-Name</span><span class="sxs-lookup"><span data-stu-id="06f7b-193">-Name</span></span>

<span data-ttu-id="06f7b-194">指定此 cmdlet 停止的作业的友好名称。</span><span class="sxs-lookup"><span data-stu-id="06f7b-194">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="06f7b-195">以逗号分隔的列表形式输入作业名称，或使用通配符 (\*) 来输入作业名称模式。</span><span class="sxs-lookup"><span data-stu-id="06f7b-195">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="06f7b-196">默认情况下， `Stop-Job` 停止在当前会话中创建的所有作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-196">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="06f7b-197">由于不能保证友好名称是唯一的，因此在按名称停止作业时，请使用 **WhatIf** 和 **Confirm** 参数。</span><span class="sxs-lookup"><span data-stu-id="06f7b-197">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="06f7b-198">-PassThru</span><span class="sxs-lookup"><span data-stu-id="06f7b-198">-PassThru</span></span>

<span data-ttu-id="06f7b-199">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="06f7b-199">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="06f7b-200">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="06f7b-200">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="06f7b-201">-State</span><span class="sxs-lookup"><span data-stu-id="06f7b-201">-State</span></span>

<span data-ttu-id="06f7b-202">指定作业状态。</span><span class="sxs-lookup"><span data-stu-id="06f7b-202">Specifies a job state.</span></span> <span data-ttu-id="06f7b-203">此 cmdlet 仅停止处于指定状态的作业。</span><span class="sxs-lookup"><span data-stu-id="06f7b-203">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="06f7b-204">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="06f7b-204">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="06f7b-205">NotStarted</span><span class="sxs-lookup"><span data-stu-id="06f7b-205">NotStarted</span></span>
- <span data-ttu-id="06f7b-206">正在运行</span><span class="sxs-lookup"><span data-stu-id="06f7b-206">Running</span></span>
- <span data-ttu-id="06f7b-207">已完成</span><span class="sxs-lookup"><span data-stu-id="06f7b-207">Completed</span></span>
- <span data-ttu-id="06f7b-208">已失败</span><span class="sxs-lookup"><span data-stu-id="06f7b-208">Failed</span></span>
- <span data-ttu-id="06f7b-209">已停止</span><span class="sxs-lookup"><span data-stu-id="06f7b-209">Stopped</span></span>
- <span data-ttu-id="06f7b-210">已阻止</span><span class="sxs-lookup"><span data-stu-id="06f7b-210">Blocked</span></span>
- <span data-ttu-id="06f7b-211">Suspended</span><span class="sxs-lookup"><span data-stu-id="06f7b-211">Suspended</span></span>
- <span data-ttu-id="06f7b-212">已断开连接</span><span class="sxs-lookup"><span data-stu-id="06f7b-212">Disconnected</span></span>
- <span data-ttu-id="06f7b-213">正在暂停</span><span class="sxs-lookup"><span data-stu-id="06f7b-213">Suspending</span></span>
- <span data-ttu-id="06f7b-214">正在停止</span><span class="sxs-lookup"><span data-stu-id="06f7b-214">Stopping</span></span>

<span data-ttu-id="06f7b-215">有关作业状态的详细信息，请参阅 [JobState 枚举](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="06f7b-215">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="06f7b-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="06f7b-216">-Confirm</span></span>

<span data-ttu-id="06f7b-217">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="06f7b-217">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="06f7b-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="06f7b-218">-WhatIf</span></span>

<span data-ttu-id="06f7b-219">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="06f7b-219">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="06f7b-220">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="06f7b-220">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="06f7b-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06f7b-221">CommonParameters</span></span>

<span data-ttu-id="06f7b-222">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="06f7b-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06f7b-223">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="06f7b-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06f7b-224">输入</span><span class="sxs-lookup"><span data-stu-id="06f7b-224">INPUTS</span></span>

### <span data-ttu-id="06f7b-225">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="06f7b-225">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="06f7b-226">可以通过管道将作业对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06f7b-226">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="06f7b-227">输出</span><span class="sxs-lookup"><span data-stu-id="06f7b-227">OUTPUTS</span></span>

### <span data-ttu-id="06f7b-228">PSRemotingJob （无）</span><span class="sxs-lookup"><span data-stu-id="06f7b-228">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="06f7b-229">如果指定 **PassThru** 参数，则此 cmdlet 将返回一个作业对象。</span><span class="sxs-lookup"><span data-stu-id="06f7b-229">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="06f7b-230">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="06f7b-230">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="06f7b-231">注释</span><span class="sxs-lookup"><span data-stu-id="06f7b-231">NOTES</span></span>

## <span data-ttu-id="06f7b-232">相关链接</span><span class="sxs-lookup"><span data-stu-id="06f7b-232">RELATED LINKS</span></span>

[<span data-ttu-id="06f7b-233">Get-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-233">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="06f7b-234">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="06f7b-234">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="06f7b-235">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="06f7b-236">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="06f7b-237">Start-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="06f7b-238">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="06f7b-238">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="06f7b-239">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="06f7b-239">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="06f7b-240">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="06f7b-240">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="06f7b-241">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="06f7b-241">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="06f7b-242">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="06f7b-242">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="06f7b-243">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="06f7b-243">about_Scopes</span></span>](About/about_scopes.md)
