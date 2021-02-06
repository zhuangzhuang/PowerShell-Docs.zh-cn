---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603810"
---
# <span data-ttu-id="2b108-102">Start-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-102">Start-Job</span></span>

## <span data-ttu-id="2b108-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2b108-103">SYNOPSIS</span></span>
<span data-ttu-id="2b108-104">启动 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-104">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="2b108-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b108-105">SYNTAX</span></span>

### <span data-ttu-id="2b108-106">ComputerName（默认值）</span><span class="sxs-lookup"><span data-stu-id="2b108-106">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="2b108-107">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="2b108-107">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="2b108-108">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="2b108-108">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="2b108-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="2b108-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="2b108-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2b108-110">DESCRIPTION</span></span>

<span data-ttu-id="2b108-111">`Start-Job`Cmdlet 在本地计算机上启动 PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-111">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="2b108-112">PowerShell 后台作业运行命令，而不与当前会话交互。</span><span class="sxs-lookup"><span data-stu-id="2b108-112">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="2b108-113">启动后台作业时，作业对象会立即返回，即使该作业需要很长时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="2b108-113">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="2b108-114">当该作业运行时，你可以继续在此会话中工作而不会发生中断。</span><span class="sxs-lookup"><span data-stu-id="2b108-114">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="2b108-115">作业对象包含有关该作业的有用信息，但不包含作业结果。</span><span class="sxs-lookup"><span data-stu-id="2b108-115">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="2b108-116">作业完成后，使用 `Receive-Job` cmdlet 获取作业的结果。</span><span class="sxs-lookup"><span data-stu-id="2b108-116">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="2b108-117">有关后台作业的详细信息，请参阅 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="2b108-117">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="2b108-118">若要在远程计算机上运行后台作业，请使用多个 cmdlet 上可用的 **AsJob** 参数，或使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-118">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="2b108-119">有关详细信息，请参阅 [about_Remote_Jobs](./About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="2b108-119">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="2b108-120">从 PowerShell 3.0 开始， `Start-Job` 可以启动自定义作业类型的实例，例如计划作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-120">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="2b108-121">有关如何使用 `Start-Job` 来启动具有自定义类型的作业的信息，请参阅作业类型功能的帮助文档。</span><span class="sxs-lookup"><span data-stu-id="2b108-121">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="2b108-122">从 PowerShell 6.0 开始，可以使用 "and" () background "运算符来启动作业 `&` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-122">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="2b108-123">后台运算符的功能类似于 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-123">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="2b108-124">用于启动作业的两种方法都创建 **PSRemotingJob** 作业对象。</span><span class="sxs-lookup"><span data-stu-id="2b108-124">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="2b108-125">有关使用与号 () 的详细信息 `&` ，请参阅 [about_Operators](./about/about_operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="2b108-125">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="2b108-126">PowerShell 7 引入了 **WorkingDirectory** 参数，该参数指定后台作业的初始工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-126">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="2b108-127">如果未指定参数，则 `Start-Job` 默认为启动作业的调用方的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-127">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="2b108-128">在 `Start-Job` 其他应用程序（例如 powershell Azure Functions）中承载 powershell 的情况下，不支持使用创建进程外后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-128">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="2b108-129">这是由设计 `Start-Job` 决定的，因为它依赖于要 `pwsh` 在下提供的可执行 `$PSHOME` 后台作业，但当应用程序托管 powershell 时，它直接使用 powershell NuGet SDK 包，而不会随 `pwsh` 一起提供。</span><span class="sxs-lookup"><span data-stu-id="2b108-129">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="2b108-130">该方案中的替代是 `Start-ThreadJob` 从模块 **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**。</span><span class="sxs-lookup"><span data-stu-id="2b108-130">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span></span>

## <span data-ttu-id="2b108-131">示例</span><span class="sxs-lookup"><span data-stu-id="2b108-131">EXAMPLES</span></span>

### <span data-ttu-id="2b108-132">示例1：启动后台作业</span><span class="sxs-lookup"><span data-stu-id="2b108-132">Example 1: Start a background job</span></span>

<span data-ttu-id="2b108-133">此示例启动在本地计算机上运行的后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-133">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="2b108-134">`Start-Job` 使用 **ScriptBlock** 参数 `Get-Process` 作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-134">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="2b108-135">**Name** 参数指定查找 PowerShell 进程 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-135">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="2b108-136">当作业在后台运行时，将显示作业信息并返回到提示符。</span><span class="sxs-lookup"><span data-stu-id="2b108-136">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="2b108-137">若要查看作业的输出，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b108-137">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2b108-138">例如，`Receive-Job -Id 1`。</span><span class="sxs-lookup"><span data-stu-id="2b108-138">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="2b108-139">示例2：使用后台运算符启动后台作业</span><span class="sxs-lookup"><span data-stu-id="2b108-139">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="2b108-140">此示例使用与号 (`&`) 后台运算符在本地计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-140">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="2b108-141">该作业的结果与 `Start-Job` 示例1中的结果相同。</span><span class="sxs-lookup"><span data-stu-id="2b108-141">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="2b108-142">`Get-Process` 使用 **Name** 参数指定 PowerShell 进程 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-142">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="2b108-143">"与" 符号 (`&`) 将命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-143">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="2b108-144">当作业在后台运行时，将显示作业信息并返回到提示符。</span><span class="sxs-lookup"><span data-stu-id="2b108-144">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="2b108-145">若要查看作业的输出，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b108-145">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2b108-146">例如，`Receive-Job -Id 5`。</span><span class="sxs-lookup"><span data-stu-id="2b108-146">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="2b108-147">示例3：使用 Invoke-Command 启动作业</span><span class="sxs-lookup"><span data-stu-id="2b108-147">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="2b108-148">此示例在多台计算机上运行作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-148">This example runs a job on multiple computers.</span></span> <span data-ttu-id="2b108-149">作业存储在一个变量中，并通过使用 PowerShell 命令行上的变量名称来执行。</span><span class="sxs-lookup"><span data-stu-id="2b108-149">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="2b108-150">将创建一个使用的作业并将其 `Invoke-Command` 存储在 `$jobWRM` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2b108-150">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="2b108-151">`Invoke-Command` 使用 **ComputerName** 参数来指定运行作业的计算机。</span><span class="sxs-lookup"><span data-stu-id="2b108-151">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="2b108-152">`Get-Content` 从文件中获取服务器名称 `C:\Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-152">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="2b108-153">**ScriptBlock** 参数指定用于 `Get-Service` 获取 **WinRM** 服务的命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-153">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="2b108-154">**JobName** 参数指定作业 **WinRM** 的友好名称。</span><span class="sxs-lookup"><span data-stu-id="2b108-154">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="2b108-155">**ThrottleLimit** 参数将并发命令数限制为16。</span><span class="sxs-lookup"><span data-stu-id="2b108-155">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="2b108-156">**AsJob** 参数启动在服务器上运行命令的后台作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-156">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="2b108-157">示例4：获取作业信息</span><span class="sxs-lookup"><span data-stu-id="2b108-157">Example 4: Get job information</span></span>

<span data-ttu-id="2b108-158">此示例将获取有关作业的信息，并显示在本地计算机上运行的已完成作业的结果。</span><span class="sxs-lookup"><span data-stu-id="2b108-158">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="2b108-159">`Start-Job` 使用 **ScriptBlock** 参数来运行命令，该命令指定 `Get-WinEvent` 获取 **系统** 日志。</span><span class="sxs-lookup"><span data-stu-id="2b108-159">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="2b108-160">**Credential** 参数指定有权在计算机上运行作业的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2b108-160">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="2b108-161">作业对象存储在 `$j` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2b108-161">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="2b108-162">变量中的对象将 `$j` 向下发送到 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-162">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="2b108-163">**Property** 参数指定星号 (`*`) 以显示作业对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="2b108-163">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="2b108-164">示例5：将脚本作为后台作业运行</span><span class="sxs-lookup"><span data-stu-id="2b108-164">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="2b108-165">在此示例中，本地计算机上的脚本作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-165">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="2b108-166">`Start-Job` 使用 **FilePath** 参数来指定存储在本地计算机上的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="2b108-166">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="2b108-167">示例6：使用后台作业获取进程</span><span class="sxs-lookup"><span data-stu-id="2b108-167">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="2b108-168">此示例使用后台作业按名称获取指定的进程。</span><span class="sxs-lookup"><span data-stu-id="2b108-168">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="2b108-169">`Start-Job` 使用 **Name** 参数指定友好的作业名称 **PShellJob**。</span><span class="sxs-lookup"><span data-stu-id="2b108-169">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="2b108-170">**ScriptBlock** 参数指定 `Get-Process` 获取名称为 **PowerShell** 的进程。</span><span class="sxs-lookup"><span data-stu-id="2b108-170">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="2b108-171">示例7：使用后台作业收集和保存数据</span><span class="sxs-lookup"><span data-stu-id="2b108-171">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="2b108-172">此示例将启动一个作业，该作业收集大量的地图数据，然后将其保存到 `.tif` 文件中。</span><span class="sxs-lookup"><span data-stu-id="2b108-172">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="2b108-173">`Start-Job` 使用 **Name** 参数指定友好的作业名称 **GetMappingFiles**。</span><span class="sxs-lookup"><span data-stu-id="2b108-173">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="2b108-174">**InitializationScript** 参数运行导入 **MapFunctions** 模块的脚本块。</span><span class="sxs-lookup"><span data-stu-id="2b108-174">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="2b108-175">**ScriptBlock** 参数运行 `Get-Map` 并将 `Set-Content` 数据保存在 **Path** 参数指定的位置。</span><span class="sxs-lookup"><span data-stu-id="2b108-175">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="2b108-176">示例8：将输入传递到后台作业</span><span class="sxs-lookup"><span data-stu-id="2b108-176">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="2b108-177">此示例使用 `$input` 自动变量来处理输入对象。</span><span class="sxs-lookup"><span data-stu-id="2b108-177">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="2b108-178">使用 `Receive-Job` 查看作业的输出。</span><span class="sxs-lookup"><span data-stu-id="2b108-178">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="2b108-179">`Start-Job`使用 `Get-Content` 带有自动变量的 ScriptBlock 参数运行 `$input` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-179">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="2b108-180">`$input`变量从 **InputObject** 参数获取对象。</span><span class="sxs-lookup"><span data-stu-id="2b108-180">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="2b108-181">`Receive-Job` 使用 **Name** 参数指定作业并输出结果。</span><span class="sxs-lookup"><span data-stu-id="2b108-181">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="2b108-182">**Keep** 参数保存作业输出，以便可以在 PowerShell 会话期间再次查看。</span><span class="sxs-lookup"><span data-stu-id="2b108-182">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="2b108-183">示例9：为后台作业设置工作目录</span><span class="sxs-lookup"><span data-stu-id="2b108-183">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="2b108-184">**WorkingDirectory** 允许你为作业指定一个备用目录，你可以从该目录中运行脚本或打开的文件。</span><span class="sxs-lookup"><span data-stu-id="2b108-184">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="2b108-185">在此示例中，后台作业指定的工作目录不同于当前目录位置。</span><span class="sxs-lookup"><span data-stu-id="2b108-185">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="2b108-186">此示例的当前工作目录为 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-186">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="2b108-187">`Start-Job` 使用 **WorkingDirectory** 参数来指定作业的工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-187">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="2b108-188">**ScriptBlock** 参数用于 `$PWD` 显示作业的工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-188">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="2b108-189">`Receive-Job` 显示后台作业的输出。</span><span class="sxs-lookup"><span data-stu-id="2b108-189">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="2b108-190">**AutoRemoveJob** 删除作业并 **等待** 取消命令提示符，直到收到所有结果。</span><span class="sxs-lookup"><span data-stu-id="2b108-190">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="2b108-191">示例10：使用 ArgumentList 参数指定数组</span><span class="sxs-lookup"><span data-stu-id="2b108-191">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="2b108-192">此示例使用 **ArgumentList** 参数来指定参数数组。</span><span class="sxs-lookup"><span data-stu-id="2b108-192">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="2b108-193">数组是以逗号分隔的进程名称列表。</span><span class="sxs-lookup"><span data-stu-id="2b108-193">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="2b108-194">`Start-Job`Cmdlet 使用 **ScriptBlock** 参数运行命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-194">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="2b108-195">`Get-Process` 使用 **Name** 参数来指定自动变量 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-195">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="2b108-196">**ArgumentList** 参数将进程名称数组传递给 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-196">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="2b108-197">进程名称 "powershell"、"pwsh" 和 "记事本" 是在本地计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="2b108-197">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="2b108-198">若要查看作业的输出，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2b108-198">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2b108-199">例如，`Receive-Job -Id 1`。</span><span class="sxs-lookup"><span data-stu-id="2b108-199">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="2b108-200">示例11：在 Windows PowerShell 5.1 中运行作业</span><span class="sxs-lookup"><span data-stu-id="2b108-200">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="2b108-201">此示例使用值为 **5.1** 的 **PSVersion** 参数在 Windows PowerShell 5.1 会话中运行作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-201">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## <span data-ttu-id="2b108-202">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b108-202">PARAMETERS</span></span>

### <span data-ttu-id="2b108-203">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="2b108-203">-ArgumentList</span></span>

<span data-ttu-id="2b108-204">指定由 **FilePath** 参数或使用 **ScriptBlock** 参数指定的命令指定的脚本的参数数组或参数值。</span><span class="sxs-lookup"><span data-stu-id="2b108-204">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="2b108-205">参数必须以单维度数组参数的形式传递给 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="2b108-205">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="2b108-206">例如，以逗号分隔的列表。</span><span class="sxs-lookup"><span data-stu-id="2b108-206">For example, a comma-separated list.</span></span> <span data-ttu-id="2b108-207">有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="2b108-207">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-208">-Authentication</span><span class="sxs-lookup"><span data-stu-id="2b108-208">-Authentication</span></span>

<span data-ttu-id="2b108-209">指定用于对用户凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="2b108-209">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="2b108-210">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b108-210">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2b108-211">默认</span><span class="sxs-lookup"><span data-stu-id="2b108-211">Default</span></span>
- <span data-ttu-id="2b108-212">基本</span><span class="sxs-lookup"><span data-stu-id="2b108-212">Basic</span></span>
- <span data-ttu-id="2b108-213">Credssp</span><span class="sxs-lookup"><span data-stu-id="2b108-213">Credssp</span></span>
- <span data-ttu-id="2b108-214">摘要</span><span class="sxs-lookup"><span data-stu-id="2b108-214">Digest</span></span>
- <span data-ttu-id="2b108-215">Kerberos</span><span class="sxs-lookup"><span data-stu-id="2b108-215">Kerberos</span></span>
- <span data-ttu-id="2b108-216">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2b108-216">Negotiate</span></span>
- <span data-ttu-id="2b108-217">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="2b108-217">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="2b108-218">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="2b108-218">The default value is Default.</span></span>

<span data-ttu-id="2b108-219">CredSSP 身份验证仅在 Windows Vista、Windows Server 2008 和更高版本的 Windows 操作系统中可用。</span><span class="sxs-lookup"><span data-stu-id="2b108-219">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="2b108-220">有关此参数的值的详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="2b108-220">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="2b108-221">在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-221">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="2b108-222">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="2b108-222">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="2b108-223">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="2b108-223">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-224">-Credential</span><span class="sxs-lookup"><span data-stu-id="2b108-224">-Credential</span></span>

<span data-ttu-id="2b108-225">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2b108-225">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="2b108-226">如果未指定 **Credential** 参数，则该命令使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="2b108-226">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="2b108-227">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-227">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2b108-228">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="2b108-228">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2b108-229">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="2b108-229">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2b108-230">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="2b108-230">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-231">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="2b108-231">-DefinitionName</span></span>

<span data-ttu-id="2b108-232">指定此 cmdlet 启动的作业的定义名称。</span><span class="sxs-lookup"><span data-stu-id="2b108-232">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="2b108-233">使用此参数来启动具有定义名称的自定义作业，例如计划作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-233">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="2b108-234">当使用 `Start-Job` 启动计划作业的实例时，将立即启动该作业，而不考虑作业触发器或作业选项。</span><span class="sxs-lookup"><span data-stu-id="2b108-234">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="2b108-235">生成的作业实例是计划作业，但不会将其保存到磁盘上，如触发的计划作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-235">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="2b108-236">不能使用的 **ArgumentList** 参数为 `Start-Job` 在计划作业中运行的脚本的参数提供值。</span><span class="sxs-lookup"><span data-stu-id="2b108-236">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="2b108-237">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2b108-237">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-238">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="2b108-238">-DefinitionPath</span></span>

<span data-ttu-id="2b108-239">指定此 cmdlet 启动的作业的定义路径。</span><span class="sxs-lookup"><span data-stu-id="2b108-239">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="2b108-240">输入定义路径。</span><span class="sxs-lookup"><span data-stu-id="2b108-240">Enter the definition path.</span></span> <span data-ttu-id="2b108-241">**DefinitionPath** 和 **DefinitionName** 参数的值的串联是作业定义的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="2b108-241">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="2b108-242">使用此参数来启动具有定义路径的自定义作业，例如计划作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-242">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="2b108-243">对于计划作业， **DefinitionPath** 参数的值为 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-243">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="2b108-244">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2b108-244">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-245">-FilePath</span><span class="sxs-lookup"><span data-stu-id="2b108-245">-FilePath</span></span>

<span data-ttu-id="2b108-246">指定 `Start-Job` 作为后台作业运行的本地脚本。</span><span class="sxs-lookup"><span data-stu-id="2b108-246">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="2b108-247">输入脚本的路径和文件名，或使用管道将脚本路径发送到 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-247">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="2b108-248">脚本必须位于本地计算机上或本地计算机可以访问的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2b108-248">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="2b108-249">使用此参数时，PowerShell 会将指定脚本文件的内容转换为脚本块，并将该脚本块作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-249">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-250">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="2b108-250">-InitializationScript</span></span>

<span data-ttu-id="2b108-251">指定在作业开始前运行的命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-251">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="2b108-252">若要创建脚本块，请将命令括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="2b108-252">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="2b108-253">使用此参数可以准备运行作业的会话。</span><span class="sxs-lookup"><span data-stu-id="2b108-253">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="2b108-254">例如，可以使用它将函数、管理单元和模块添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="2b108-254">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-255">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2b108-255">-InputObject</span></span>

<span data-ttu-id="2b108-256">指定命令的输入。</span><span class="sxs-lookup"><span data-stu-id="2b108-256">Specifies input to the command.</span></span> <span data-ttu-id="2b108-257">请输入包含对象的变量，或者键入可生成对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="2b108-257">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="2b108-258">在 **ScriptBlock** 参数的值中，使用 `$input` 自动变量来表示输入对象。</span><span class="sxs-lookup"><span data-stu-id="2b108-258">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-259">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2b108-259">-LiteralPath</span></span>

<span data-ttu-id="2b108-260">指定此 cmdlet 作为后台作业运行的本地脚本。</span><span class="sxs-lookup"><span data-stu-id="2b108-260">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="2b108-261">在本地计算机上输入脚本的路径。</span><span class="sxs-lookup"><span data-stu-id="2b108-261">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="2b108-262">`Start-Job` 使用 **LiteralPath** 参数的值，与键入的值完全相同。</span><span class="sxs-lookup"><span data-stu-id="2b108-262">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="2b108-263">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="2b108-263">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="2b108-264">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="2b108-264">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2b108-265">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="2b108-265">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-266">-Name</span><span class="sxs-lookup"><span data-stu-id="2b108-266">-Name</span></span>

<span data-ttu-id="2b108-267">为新作业指定一个友好名称。</span><span class="sxs-lookup"><span data-stu-id="2b108-267">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="2b108-268">你可以使用该名称来确定其他作业 cmdlet （如 cmdlet）的作业 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-268">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="2b108-269">默认友好名称为 `Job#` ，其中 `#` 是每个作业递增的序号。</span><span class="sxs-lookup"><span data-stu-id="2b108-269">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-270">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="2b108-270">-PSVersion</span></span>

<span data-ttu-id="2b108-271">指定用于运行作业的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="2b108-271">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="2b108-272">当 **PSVersion** 的值为 **5.1** 时，作业将在 Windows PowerShell 5.1 会话中运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-272">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="2b108-273">对于任何其他值，将使用当前版本的 PowerShell 运行作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-273">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="2b108-274">此参数已在 PowerShell 7 中添加，并且仅适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="2b108-274">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-275">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="2b108-275">-RunAs32</span></span>

<span data-ttu-id="2b108-276">从 PowerShell 7 开始， **RunAs32** 参数在64位 PowerShell () 上不起作用 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-276">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="2b108-277">如果在64位 PowerShell 中指定了 **RunAs32** ，则会 `Start-Job` 引发终止异常错误。</span><span class="sxs-lookup"><span data-stu-id="2b108-277">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="2b108-278">若要使用 RunAs32 启动32位 PowerShell (`pwsh`) 过程，需要安装32位 powershell。</span><span class="sxs-lookup"><span data-stu-id="2b108-278">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32**, you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="2b108-279">在32位 PowerShell 中， **RunAs32** 强制作业在32位进程中运行，即使在64位操作系统上也是如此。</span><span class="sxs-lookup"><span data-stu-id="2b108-279">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="2b108-280">在64位版本的 Windows 7 和 Windows Server 2008 R2 上，当 `Start-Job` 命令包括 **RunAs32** 参数时，不能使用 **Credential** 参数来指定另一个用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="2b108-280">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-281">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="2b108-281">-ScriptBlock</span></span>

<span data-ttu-id="2b108-282">指定要在后台作业中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="2b108-282">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="2b108-283">若要创建脚本块，请将命令括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="2b108-283">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="2b108-284">使用 `$input` 自动变量访问 **InputObject** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="2b108-284">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="2b108-285">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="2b108-285">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-286">-Type</span><span class="sxs-lookup"><span data-stu-id="2b108-286">-Type</span></span>

<span data-ttu-id="2b108-287">指定由启动的作业的自定义类型 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-287">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="2b108-288">输入自定义作业类型名称，例如 PSScheduledJob（对于计划作业）或 PSWorkflowJob（对于工作流作业）。</span><span class="sxs-lookup"><span data-stu-id="2b108-288">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="2b108-289">此参数对标准后台作业无效。</span><span class="sxs-lookup"><span data-stu-id="2b108-289">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="2b108-290">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2b108-290">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-291">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="2b108-291">-WorkingDirectory</span></span>

<span data-ttu-id="2b108-292">指定后台作业的初始工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-292">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="2b108-293">如果未指定该参数，则从默认位置运行该作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-293">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="2b108-294">默认位置是启动作业的调用方的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="2b108-294">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="2b108-295">此参数是在 PowerShell 7 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2b108-295">This parameter was introduced in PowerShell 7.</span></span>

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b108-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b108-296">CommonParameters</span></span>

<span data-ttu-id="2b108-297">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2b108-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b108-298">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2b108-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b108-299">输入</span><span class="sxs-lookup"><span data-stu-id="2b108-299">INPUTS</span></span>

### <span data-ttu-id="2b108-300">System.String</span><span class="sxs-lookup"><span data-stu-id="2b108-300">System.String</span></span>

<span data-ttu-id="2b108-301">可以使用管道将具有 **name** 属性的对象发送到 **name** 参数。</span><span class="sxs-lookup"><span data-stu-id="2b108-301">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="2b108-302">例如，可以通过管道将 **FileInfo** 对象从管道 `Get-ChildItem` 管道 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2b108-302">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="2b108-303">输出</span><span class="sxs-lookup"><span data-stu-id="2b108-303">OUTPUTS</span></span>

### <span data-ttu-id="2b108-304">System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="2b108-304">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="2b108-305">`Start-Job` 返回一个 **PSRemotingJob** 对象，该对象表示其启动的作业。</span><span class="sxs-lookup"><span data-stu-id="2b108-305">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="2b108-306">注释</span><span class="sxs-lookup"><span data-stu-id="2b108-306">NOTES</span></span>

<span data-ttu-id="2b108-307">若要在后台运行，请 `Start-Job` 在当前会话中自己的会话中运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-307">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="2b108-308">使用 `Invoke-Command` cmdlet 在 `Start-Job` 远程计算机上的会话中运行命令时，将 `Start-Job` 在远程会话的会话中运行。</span><span class="sxs-lookup"><span data-stu-id="2b108-308">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="2b108-309">相关链接</span><span class="sxs-lookup"><span data-stu-id="2b108-309">RELATED LINKS</span></span>

[<span data-ttu-id="2b108-310">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="2b108-310">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="2b108-311">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="2b108-311">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="2b108-312">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="2b108-312">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="2b108-313">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="2b108-313">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="2b108-314">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="2b108-314">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="2b108-315">Get-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-315">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="2b108-316">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2b108-316">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="2b108-317">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-317">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="2b108-318">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-318">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="2b108-319">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-319">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="2b108-320">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="2b108-320">Wait-Job</span></span>](Wait-Job.md)
