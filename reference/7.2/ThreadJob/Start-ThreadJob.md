---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: d08f883b232abadeacb445e5ba542b4b1fae023b
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "99603785"
---
# <span data-ttu-id="2ed52-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="2ed52-102">Start-ThreadJob</span></span>

## <span data-ttu-id="2ed52-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2ed52-103">SYNOPSIS</span></span>
<span data-ttu-id="2ed52-104">创建类似于 cmdlet 的后台作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="2ed52-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ed52-105">SYNTAX</span></span>

### <span data-ttu-id="2ed52-106">脚本块</span><span class="sxs-lookup"><span data-stu-id="2ed52-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### <span data-ttu-id="2ed52-107">文件路径</span><span class="sxs-lookup"><span data-stu-id="2ed52-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## <span data-ttu-id="2ed52-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2ed52-108">DESCRIPTION</span></span>

<span data-ttu-id="2ed52-109">`Start-ThreadJob` 创建类似于 cmdlet 的后台作业 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="2ed52-110">主要区别在于，创建的作业在本地进程中的单独线程中运行。</span><span class="sxs-lookup"><span data-stu-id="2ed52-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="2ed52-111">默认情况下，作业使用启动了作业的调用方的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="2ed52-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="2ed52-112">该 cmdlet 还支持 **ThrottleLimit** 参数，限制一次运行的作业数。</span><span class="sxs-lookup"><span data-stu-id="2ed52-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="2ed52-113">随着多个作业的启动，它们会排队等待，直到当前的作业数低于限制限制。</span><span class="sxs-lookup"><span data-stu-id="2ed52-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="2ed52-114">示例</span><span class="sxs-lookup"><span data-stu-id="2ed52-114">EXAMPLES</span></span>

### <span data-ttu-id="2ed52-115">示例 1-创建线程数限制为2的后台作业</span><span class="sxs-lookup"><span data-stu-id="2ed52-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="2ed52-116">示例 2-比较 Start-Job 和 Start-ThreadJob 的性能</span><span class="sxs-lookup"><span data-stu-id="2ed52-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="2ed52-117">此示例显示与之间的 `Start-Job` 差异 `Start-ThreadJob` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="2ed52-118">作业运行 `Start-Sleep` cmdlet 1 秒。</span><span class="sxs-lookup"><span data-stu-id="2ed52-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="2ed52-119">由于作业是并行运行的，因此总执行时间大约为1秒，并包括创建作业所需的任何时间。</span><span class="sxs-lookup"><span data-stu-id="2ed52-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="2ed52-120">在将执行时间减1秒后，可以看到， `Start-Job` 大约需要4.8 秒来创建五个作业。</span><span class="sxs-lookup"><span data-stu-id="2ed52-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="2ed52-121">`Start-ThreadJob` 速度快8倍，创建五个作业大约需要0.6 秒。</span><span class="sxs-lookup"><span data-stu-id="2ed52-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="2ed52-122">您的环境中的结果可能会有所不同，但相对改进应该是相同的。</span><span class="sxs-lookup"><span data-stu-id="2ed52-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="2ed52-123">示例 3-使用 InputObject 创建作业</span><span class="sxs-lookup"><span data-stu-id="2ed52-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="2ed52-124">在此示例中，脚本块使用 `$input` 变量接收来自 **InputObject** 参数的输入。</span><span class="sxs-lookup"><span data-stu-id="2ed52-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="2ed52-125">此操作也可以通过管道将对象传递给 `Start-ThreadJob` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### <span data-ttu-id="2ed52-126">示例 4-将作业输出流到父主机</span><span class="sxs-lookup"><span data-stu-id="2ed52-126">Example 4 - Stream job output to parent host</span></span>

<span data-ttu-id="2ed52-127">使用 **StreamingHost** 参数可以将所有主机输出定向到特定主机。</span><span class="sxs-lookup"><span data-stu-id="2ed52-127">Using the **StreamingHost** parameter you can tell a job to direct all host output to a specific host.</span></span> <span data-ttu-id="2ed52-128">如果没有此参数，输出将转到作业数据流集合，而不会在主机控制台中显示，直到收到作业的输出。</span><span class="sxs-lookup"><span data-stu-id="2ed52-128">Without this parameter the output goes to the job data stream collection and doesn't appear in a host console until you receive the output from the job.</span></span>

<span data-ttu-id="2ed52-129">在此示例中，当前主机 `Start-ThreadJob` 使用自动变量传递给 `$Host` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-129">For this example, the current host is passed to `Start-ThreadJob` using the `$Host` automatic variable.</span></span>

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

<span data-ttu-id="2ed52-130">请注意， `Read-Host` 会显示的提示，并且您可以键入 input。</span><span class="sxs-lookup"><span data-stu-id="2ed52-130">Notice that the prompt from `Read-Host` is displayed and you are able to type input.</span></span> <span data-ttu-id="2ed52-131">然后，将显示来自的消息 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-131">Then, the message from `Write-Warning` is displayed.</span></span> <span data-ttu-id="2ed52-132">该 `Receive-Job` cmdlet 将返回作业的所有输出。</span><span class="sxs-lookup"><span data-stu-id="2ed52-132">The `Receive-Job` cmdlet returns all the output from the job.</span></span>

## <span data-ttu-id="2ed52-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2ed52-133">PARAMETERS</span></span>

### <span data-ttu-id="2ed52-134">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="2ed52-134">-ArgumentList</span></span>

<span data-ttu-id="2ed52-135">指定由 **FilePath** 或 **ScriptBlock** 参数指定的脚本的参数数组或参数值。</span><span class="sxs-lookup"><span data-stu-id="2ed52-135">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="2ed52-136">**ArgumentList** 必须是命令行上的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="2ed52-136">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="2ed52-137">参数名称后面的所有值都是参数列表中的解释值。</span><span class="sxs-lookup"><span data-stu-id="2ed52-137">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-138">-FilePath</span><span class="sxs-lookup"><span data-stu-id="2ed52-138">-FilePath</span></span>

<span data-ttu-id="2ed52-139">指定要作为后台作业运行的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="2ed52-139">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="2ed52-140">输入脚本的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="2ed52-140">Enter the path and filename of the script.</span></span> <span data-ttu-id="2ed52-141">脚本必须位于本地计算机上或本地计算机可以访问的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2ed52-141">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="2ed52-142">使用此参数时，PowerShell 会将指定脚本文件的内容转换为脚本块，并将该脚本块作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="2ed52-142">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-143">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="2ed52-143">-InitializationScript</span></span>

<span data-ttu-id="2ed52-144">指定在作业开始前运行的命令。</span><span class="sxs-lookup"><span data-stu-id="2ed52-144">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="2ed52-145">将命令括在大括号中， (`{}`) 创建脚本块。</span><span class="sxs-lookup"><span data-stu-id="2ed52-145">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="2ed52-146">使用此参数可以准备运行作业的会话。</span><span class="sxs-lookup"><span data-stu-id="2ed52-146">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="2ed52-147">例如，可以使用它将函数和模块添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="2ed52-147">For example, you can use it to add functions and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2ed52-148">-InputObject</span></span>

<span data-ttu-id="2ed52-149">指定用作脚本块输入的对象。</span><span class="sxs-lookup"><span data-stu-id="2ed52-149">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="2ed52-150">它还允许管道输入。</span><span class="sxs-lookup"><span data-stu-id="2ed52-150">It also allows for pipeline input.</span></span> <span data-ttu-id="2ed52-151">使用 `$input` 脚本块中的自动变量来访问输入对象。</span><span class="sxs-lookup"><span data-stu-id="2ed52-151">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-152">-Name</span><span class="sxs-lookup"><span data-stu-id="2ed52-152">-Name</span></span>

<span data-ttu-id="2ed52-153">为新作业指定一个友好名称。</span><span class="sxs-lookup"><span data-stu-id="2ed52-153">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="2ed52-154">你可以使用该名称来确定其他作业 cmdlet （如 cmdlet）的作业 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="2ed52-154">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="2ed52-155">默认友好名称为 "Job #"，其中 "#" 是针对每个作业递增的序号。</span><span class="sxs-lookup"><span data-stu-id="2ed52-155">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-156">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="2ed52-156">-ScriptBlock</span></span>

<span data-ttu-id="2ed52-157">指定要在后台作业中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="2ed52-157">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="2ed52-158">将命令括在大括号中， (`{}`) 创建脚本块。</span><span class="sxs-lookup"><span data-stu-id="2ed52-158">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="2ed52-159">使用 `$Input` 自动变量访问 **InputObject** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="2ed52-159">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="2ed52-160">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="2ed52-160">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-161">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="2ed52-161">-StreamingHost</span></span>

<span data-ttu-id="2ed52-162">此参数提供一个线程安全的方式，以允许 `Write-Host` 输出直接进入传入的 **PSHost** 对象。</span><span class="sxs-lookup"><span data-stu-id="2ed52-162">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="2ed52-163">如果没有此方法， `Write-Host` 输出将转到作业信息数据流集合，而不会在主机控制台中显示，直到作业完成运行。</span><span class="sxs-lookup"><span data-stu-id="2ed52-163">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-164">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2ed52-164">-ThrottleLimit</span></span>

<span data-ttu-id="2ed52-165">此参数限制一次运行的作业数。</span><span class="sxs-lookup"><span data-stu-id="2ed52-165">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="2ed52-166">当作业启动时，它们将排队等待，并等待线程池中的线程可用来运行作业。</span><span class="sxs-lookup"><span data-stu-id="2ed52-166">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="2ed52-167">默认限制为5个线程。</span><span class="sxs-lookup"><span data-stu-id="2ed52-167">The default limit is 5 threads.</span></span>

<span data-ttu-id="2ed52-168">线程池大小在 PowerShell 会话中是全局性的。</span><span class="sxs-lookup"><span data-stu-id="2ed52-168">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="2ed52-169">在一个调用中指定 **ThrottleLimit** 将设置同一会话中后续调用的限制。</span><span class="sxs-lookup"><span data-stu-id="2ed52-169">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed52-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ed52-170">CommonParameters</span></span>

<span data-ttu-id="2ed52-171">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2ed52-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ed52-172">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2ed52-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ed52-173">输入</span><span class="sxs-lookup"><span data-stu-id="2ed52-173">INPUTS</span></span>

### <span data-ttu-id="2ed52-174">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="2ed52-174">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="2ed52-175">输出</span><span class="sxs-lookup"><span data-stu-id="2ed52-175">OUTPUTS</span></span>

### <span data-ttu-id="2ed52-176">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="2ed52-176">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="2ed52-177">注释</span><span class="sxs-lookup"><span data-stu-id="2ed52-177">NOTES</span></span>

## <span data-ttu-id="2ed52-178">相关链接</span><span class="sxs-lookup"><span data-stu-id="2ed52-178">RELATED LINKS</span></span>

[<span data-ttu-id="2ed52-179">Start-Job</span><span class="sxs-lookup"><span data-stu-id="2ed52-179">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="2ed52-180">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="2ed52-180">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="2ed52-181">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="2ed52-181">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
