---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598898"
---
# <span data-ttu-id="3ceac-102">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-102">Receive-Job</span></span>

## <span data-ttu-id="3ceac-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3ceac-103">SYNOPSIS</span></span>
<span data-ttu-id="3ceac-104">获取当前会话中 PowerShell 后台作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-104">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="3ceac-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ceac-105">SYNTAX</span></span>

### <span data-ttu-id="3ceac-106">Location（默认值）</span><span class="sxs-lookup"><span data-stu-id="3ceac-106">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="3ceac-107">计算机名</span><span class="sxs-lookup"><span data-stu-id="3ceac-107">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="3ceac-108">会话</span><span class="sxs-lookup"><span data-stu-id="3ceac-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="3ceac-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3ceac-109">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3ceac-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3ceac-110">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3ceac-111">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3ceac-111">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="3ceac-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3ceac-112">DESCRIPTION</span></span>

<span data-ttu-id="3ceac-113">该 `Receive-Job` cmdlet 将获取 PowerShell 后台作业的结果，如使用 `Start-Job` cmdlet 或任何 Cmdlet 的 **AsJob** 参数启动的作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-113">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="3ceac-114">你可以获取所有作业的结果，或通过作业的名称、ID、实例 ID、计算机名称、位置或会话或者通过提交作业对象来标识作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-114">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="3ceac-115">启动 PowerShell 后台作业时，该作业将启动，但是结果不会立即显示。</span><span class="sxs-lookup"><span data-stu-id="3ceac-115">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="3ceac-116">而该命令将返回一个表示该后台作业的对象。</span><span class="sxs-lookup"><span data-stu-id="3ceac-116">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="3ceac-117">该作业对象包含有关该作业的有用信息，但是不包含结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-117">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="3ceac-118">此方法允许你在作业运行的同时继续在会话中工作。</span><span class="sxs-lookup"><span data-stu-id="3ceac-118">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="3ceac-119">有关 PowerShell 中的后台作业的详细信息，请参阅 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="3ceac-119">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="3ceac-120">该 `Receive-Job` cmdlet 将获取 `Receive-Job` 提交命令后生成的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-120">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="3ceac-121">如果尚未完成结果，你可以运行其他 `Receive-Job` 命令来获取剩余结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-121">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="3ceac-122">默认情况下，作业结果将在你收到它们时从系统中删除，但是你可以使用 **Keep** 参数来保存这些结果，以便可以再次收到它们。</span><span class="sxs-lookup"><span data-stu-id="3ceac-122">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="3ceac-123">若要删除作业结果，请在 `Receive-Job` 不使用 **Keep** 参数的情况下再次运行该命令，关闭会话，或使用 `Remove-Job` cmdlet 从会话中删除该作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-123">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="3ceac-124">从 Windows PowerShell 3.0 开始， `Receive-Job` 还获取自定义作业类型的结果，如工作流作业和计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="3ceac-124">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="3ceac-125">若要使 `Receive-Job` 能够获取自定义作业类型的结果，请在运行命令之前将支持自定义作业类型的模块导入到会话中 `Receive-Job` ，方法是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ceac-125">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="3ceac-126">有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。</span><span class="sxs-lookup"><span data-stu-id="3ceac-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="3ceac-127">示例</span><span class="sxs-lookup"><span data-stu-id="3ceac-127">EXAMPLES</span></span>

### <span data-ttu-id="3ceac-128">示例1：获取特定作业的结果</span><span class="sxs-lookup"><span data-stu-id="3ceac-128">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="3ceac-129">这些命令使用的 **作业** 参数 `Receive-Job` 来获取特定作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-129">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="3ceac-130">第一个命令使用启动一个作业 `Start-Job` ，并将该作业对象存储在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="3ceac-130">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="3ceac-131">第二个命令使用 `Receive-Job` cmdlet 来获取作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-131">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="3ceac-132">它使用 **Job** 参数来指定作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-132">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="3ceac-133">示例2：使用 Keep 参数</span><span class="sxs-lookup"><span data-stu-id="3ceac-133">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="3ceac-134">此示例在变量中存储作业 `$job` ，并通过管道将作业传递给 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ceac-134">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3ceac-135">`-Keep`参数还用于允许在第一次查看之后再次检索聚合流数据。</span><span class="sxs-lookup"><span data-stu-id="3ceac-135">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="3ceac-136">示例3：获取多个后台作业的结果</span><span class="sxs-lookup"><span data-stu-id="3ceac-136">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="3ceac-137">使用的 **AsJob** 参数 `Invoke-Command` 启动作业时，将在本地计算机上创建作业对象，即使该作业在远程计算机上运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="3ceac-137">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="3ceac-138">因此，你可以使用本地命令来管理作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-138">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="3ceac-139">此外，当你使用 **AsJob** 时，PowerShell 将返回一个作业对象，其中包含已启动的每个作业的子作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-139">Also, when you use **AsJob**, PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="3ceac-140">在此示例中，该作业对象包含三个子作业，分别对应于每台远程计算机上的每个作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-140">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="3ceac-141">示例4：获取多台远程计算机上的后台作业的结果</span><span class="sxs-lookup"><span data-stu-id="3ceac-141">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="3ceac-142">此示例显示了如何获取在三台远程计算机上运行的后台作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-142">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="3ceac-143">与前面的示例不同，使用 `Invoke-Command` 运行 `Start-Job` 命令实际上是在三台计算机上的每一台计算机上启动了三个独立的作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-143">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="3ceac-144">因此，该命令返回了三个作业对象，以表示在三台不同的计算机上本地运行的三个作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-144">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="3ceac-145">在最后一个命令中，由于 `$j` 是局部变量，因此脚本块使用 **Using** 作用域修饰符来标识 `$j` 变量。</span><span class="sxs-lookup"><span data-stu-id="3ceac-145">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="3ceac-146">有关 **Using** 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](./About/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3ceac-146">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="3ceac-147">示例5：访问子作业</span><span class="sxs-lookup"><span data-stu-id="3ceac-147">Example 5: Access child jobs</span></span>

<span data-ttu-id="3ceac-148">`-Keep`参数保留作业的聚合流的状态，以便可以再次查看。</span><span class="sxs-lookup"><span data-stu-id="3ceac-148">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="3ceac-149">如果没有此参数，则当接收到作业时，所有聚合流数据都将被清除。</span><span class="sxs-lookup"><span data-stu-id="3ceac-149">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="3ceac-150">有关详细信息，请参阅 [about_Job_Details](About/about_Job_Details.md#child-jobs)</span><span class="sxs-lookup"><span data-stu-id="3ceac-150">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="3ceac-151">聚合流包括所有子作业的流。</span><span class="sxs-lookup"><span data-stu-id="3ceac-151">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="3ceac-152">你仍可以通过作业对象和子作业对象访问单个数据流。</span><span class="sxs-lookup"><span data-stu-id="3ceac-152">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="3ceac-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ceac-153">PARAMETERS</span></span>

### <span data-ttu-id="3ceac-154">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="3ceac-154">-AutoRemoveJob</span></span>

<span data-ttu-id="3ceac-155">指示此 cmdlet 在返回作业结果后删除该作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-155">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="3ceac-156">如果作业有更多结果，则仍将删除该作业，但会 `Receive-Job` 显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="3ceac-156">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="3ceac-157">此参数仅适用于自定义作业类型。</span><span class="sxs-lookup"><span data-stu-id="3ceac-157">This parameter works only on custom job types.</span></span>
<span data-ttu-id="3ceac-158">它专门用于保存会话之外的作业或类型的作业类型的实例，例如计划作业的实例。</span><span class="sxs-lookup"><span data-stu-id="3ceac-158">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="3ceac-159">不能在缺少 **Wait** 参数的情况下使用此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-159">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="3ceac-160">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-160">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3ceac-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3ceac-161">-ComputerName</span></span>

<span data-ttu-id="3ceac-162">指定计算机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-162">Specifies an array of names of computers.</span></span>

<span data-ttu-id="3ceac-163">此参数从存储在本地计算机的作业结果中进行选择。</span><span class="sxs-lookup"><span data-stu-id="3ceac-163">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="3ceac-164">它不会获取在远程计算机上运行的作业的数据。</span><span class="sxs-lookup"><span data-stu-id="3ceac-164">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="3ceac-165">若要获取存储在远程计算机上的作业结果，请使用 `Invoke-Command` cmdlet 远程运行 `Receive-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="3ceac-165">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3ceac-166">-Force</span><span class="sxs-lookup"><span data-stu-id="3ceac-166">-Force</span></span>

<span data-ttu-id="3ceac-167">指示当作业处于 **挂起** 或 **断开连接** 状态时，此 cmdlet 将继续等待。</span><span class="sxs-lookup"><span data-stu-id="3ceac-167">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="3ceac-168">默认情况下，  `Receive-Job` 当作业处于以下状态之一时，的 wait 参数将返回或终止等待：</span><span class="sxs-lookup"><span data-stu-id="3ceac-168">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="3ceac-169">已完成</span><span class="sxs-lookup"><span data-stu-id="3ceac-169">Completed</span></span>
- <span data-ttu-id="3ceac-170">已失败</span><span class="sxs-lookup"><span data-stu-id="3ceac-170">Failed</span></span>
- <span data-ttu-id="3ceac-171">已停止</span><span class="sxs-lookup"><span data-stu-id="3ceac-171">Stopped</span></span>
- <span data-ttu-id="3ceac-172">已挂起</span><span class="sxs-lookup"><span data-stu-id="3ceac-172">Suspended</span></span>
- <span data-ttu-id="3ceac-173">已断开连接。</span><span class="sxs-lookup"><span data-stu-id="3ceac-173">Disconnected.</span></span>

<span data-ttu-id="3ceac-174">仅当命令中也使用 **Wait** 参数时，**Force** 参数才有效。</span><span class="sxs-lookup"><span data-stu-id="3ceac-174">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="3ceac-175">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3ceac-176">-Id</span><span class="sxs-lookup"><span data-stu-id="3ceac-176">-Id</span></span>

<span data-ttu-id="3ceac-177">指定一个 ID 数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-177">Specifies an array of IDs.</span></span>
<span data-ttu-id="3ceac-178">此 cmdlet 将获取具有指定 Id 的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-178">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="3ceac-179">ID 是一个整数，用于唯一标识当前会话中的作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-179">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="3ceac-180">它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3ceac-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="3ceac-181">你可以键入一个或多个 Id （以逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="3ceac-181">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="3ceac-182">若要查找作业的 ID，请使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="3ceac-182">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="3ceac-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3ceac-183">-InstanceId</span></span>

<span data-ttu-id="3ceac-184">指定实例 ID 的数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-184">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="3ceac-185">此 cmdlet 将获取具有指定实例 Id 的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-185">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="3ceac-186">实例 ID 是一个 GUID，用于在计算机上唯一标识作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="3ceac-187">若要查找作业的实例 ID，请使用 `Get-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ceac-187">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3ceac-188">-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-188">-Job</span></span>

<span data-ttu-id="3ceac-189">指定要检索其结果的作业。</span><span class="sxs-lookup"><span data-stu-id="3ceac-189">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="3ceac-190">请输入一个包含作业的变量，或一个可获取作业的命令。</span><span class="sxs-lookup"><span data-stu-id="3ceac-190">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="3ceac-191">还可以通过管道将作业对象传递给 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="3ceac-191">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3ceac-192">-Keep</span><span class="sxs-lookup"><span data-stu-id="3ceac-192">-Keep</span></span>

<span data-ttu-id="3ceac-193">指示此 cmdlet 将聚合流数据保存在系统中，即使在收到这些数据后也是如此。</span><span class="sxs-lookup"><span data-stu-id="3ceac-193">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="3ceac-194">默认情况下，在使用查看后将清除聚合流数据 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="3ceac-194">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="3ceac-195">关闭会话，或删除具有 cmdlet 的作业 `Remove-Job` 也会删除聚合的流数据。</span><span class="sxs-lookup"><span data-stu-id="3ceac-195">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="3ceac-196">-Location</span><span class="sxs-lookup"><span data-stu-id="3ceac-196">-Location</span></span>

<span data-ttu-id="3ceac-197">指定位置的数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-197">Specifies an array of locations.</span></span>
<span data-ttu-id="3ceac-198">此 cmdlet 仅获取指定位置中的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-198">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceac-199">-Name</span><span class="sxs-lookup"><span data-stu-id="3ceac-199">-Name</span></span>

<span data-ttu-id="3ceac-200">指定一个友好名称数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-200">Specifies an array of friendly names.</span></span>
<span data-ttu-id="3ceac-201">此 cmdlet 将获取具有指定名称的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-201">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="3ceac-202">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3ceac-202">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="3ceac-203">-NoRecurse</span><span class="sxs-lookup"><span data-stu-id="3ceac-203">-NoRecurse</span></span>

<span data-ttu-id="3ceac-204">指示此 cmdlet 仅获取指定作业中的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-204">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="3ceac-205">默认情况下， `Receive-Job` 还会获取指定作业的所有子作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-205">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="3ceac-206">-Session</span><span class="sxs-lookup"><span data-stu-id="3ceac-206">-Session</span></span>

<span data-ttu-id="3ceac-207">指定会话的数组。</span><span class="sxs-lookup"><span data-stu-id="3ceac-207">Specifies an array of sessions.</span></span>
<span data-ttu-id="3ceac-208">此 cmdlet 将获取 (**PSSession**) 在指定的 PowerShell 会话中运行的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-208">This cmdlet gets the results of jobs that were run in the specified PowerShell session (**PSSession**).</span></span>
<span data-ttu-id="3ceac-209">输入包含 **pssession** 的变量或获取 **pssession** 的命令（如 `Get-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="3ceac-209">Enter a variable that contains the **PSSession** or a command that gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3ceac-210">-Wait</span><span class="sxs-lookup"><span data-stu-id="3ceac-210">-Wait</span></span>

<span data-ttu-id="3ceac-211">指示此 cmdlet 禁止显示命令提示符，直到收到所有作业结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-211">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="3ceac-212">默认情况下，会 `Receive-Job` 立即返回可用结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-212">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="3ceac-213">默认情况下，**Wait** 参数将等待作业处于以下状态之一：</span><span class="sxs-lookup"><span data-stu-id="3ceac-213">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="3ceac-214">已完成</span><span class="sxs-lookup"><span data-stu-id="3ceac-214">Completed</span></span>
- <span data-ttu-id="3ceac-215">已失败</span><span class="sxs-lookup"><span data-stu-id="3ceac-215">Failed</span></span>
- <span data-ttu-id="3ceac-216">已停止</span><span class="sxs-lookup"><span data-stu-id="3ceac-216">Stopped</span></span>
- <span data-ttu-id="3ceac-217">已挂起</span><span class="sxs-lookup"><span data-stu-id="3ceac-217">Suspended</span></span>
- <span data-ttu-id="3ceac-218">已断开连接。</span><span class="sxs-lookup"><span data-stu-id="3ceac-218">Disconnected.</span></span>

<span data-ttu-id="3ceac-219">若要指示 **wait** 参数继续等待作业状态为 "已挂起" 还是 "已断开连接"，请将 **Force** 参数与 **Wait** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="3ceac-219">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="3ceac-220">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3ceac-221">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="3ceac-221">-WriteEvents</span></span>

<span data-ttu-id="3ceac-222">指示此 cmdlet 在等待作业完成时报告作业状态的更改。</span><span class="sxs-lookup"><span data-stu-id="3ceac-222">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="3ceac-223">仅当在命令中使用 **Wait** 参数并且省略 **Keep** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="3ceac-223">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="3ceac-224">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3ceac-225">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="3ceac-225">-WriteJobInResults</span></span>

<span data-ttu-id="3ceac-226">指示此 cmdlet 返回后跟结果的作业对象。</span><span class="sxs-lookup"><span data-stu-id="3ceac-226">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="3ceac-227">仅当在命令中使用 **Wait** 参数并且省略 **Keep** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="3ceac-227">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="3ceac-228">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="3ceac-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3ceac-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ceac-229">CommonParameters</span></span>

<span data-ttu-id="3ceac-230">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3ceac-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ceac-231">有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3ceac-231">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3ceac-232">输入</span><span class="sxs-lookup"><span data-stu-id="3ceac-232">INPUTS</span></span>

### <span data-ttu-id="3ceac-233">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-233">System.Management.Automation.Job</span></span>

<span data-ttu-id="3ceac-234">可以通过管道将作业对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ceac-234">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="3ceac-235">输出</span><span class="sxs-lookup"><span data-stu-id="3ceac-235">OUTPUTS</span></span>

### <span data-ttu-id="3ceac-236">PSObject</span><span class="sxs-lookup"><span data-stu-id="3ceac-236">PSObject</span></span>

<span data-ttu-id="3ceac-237">此 cmdlet 将返回作业中命令的结果。</span><span class="sxs-lookup"><span data-stu-id="3ceac-237">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="3ceac-238">注释</span><span class="sxs-lookup"><span data-stu-id="3ceac-238">NOTES</span></span>

## <span data-ttu-id="3ceac-239">相关链接</span><span class="sxs-lookup"><span data-stu-id="3ceac-239">RELATED LINKS</span></span>

[<span data-ttu-id="3ceac-240">Get-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-240">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="3ceac-241">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3ceac-241">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3ceac-242">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-242">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="3ceac-243">Start-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-243">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="3ceac-244">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-244">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="3ceac-245">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3ceac-245">Wait-Job</span></span>](Wait-Job.md)

