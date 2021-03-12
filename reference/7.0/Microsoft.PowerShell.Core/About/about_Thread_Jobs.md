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
ms.locfileid: "103193973"
---
# <a name="about-thread-jobs"></a>关于线程作业

## <a name="short-description"></a>简短说明

提供有关基于 PowerShell 线程的作业的信息。 线程作业是一种后台作业，它在当前会话进程中的单独线程中运行命令或表达式。

## <a name="long-description"></a>长说明

PowerShell 通过作业并发运行命令和脚本。 PowerShell 提供三种作业类型来支持并发。

- `RemoteJob` -命令和脚本在远程会话中运行。 有关信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。
- `BackgroundJob` -命令和脚本在本地计算机上的单独进程中运行。 有关详细信息，请参阅 [about_Jobs](about_Jobs.md)。
- `PSTaskJob` 或 `ThreadJob` -命令和脚本在本地计算机上的同一进程内的单独线程中运行。

基于线程的作业不像远程和后台作业那样可靠，因为它们在不同线程上的同一进程中运行。 如果一个作业发生了导致进程崩溃的严重错误，则会终止该进程中的所有其他作业。

但是，基于线程的作业需要更少的开销。 它们不使用远程层或序列化。 结果对象作为对当前会话中活动对象的引用返回。 如果没有此开销，基于线程的作业运行速度更快，使用的资源比其他作业类型少。

> [!IMPORTANT]
> 创建作业的父会话还会监视作业状态和收集管道数据。 作业到达完成状态后，父进程终止了作业子进程。 如果终止了父会话，则所有正在运行的子作业都将与其子进程一起终止。

可通过两种方法解决此问题：

1. 用于 `Invoke-Command` 创建在断开连接的会话中运行的作业。 有关详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。
1. 使用 `Start-Process` 创建新进程，而不是作业。 有关详细信息，请参阅 [开始处理](xref:Microsoft.PowerShell.Management.Start-Process)。

## <a name="how-to-start-and-manage-thread-based-jobs"></a>如何启动和管理基于线程的作业

可以通过两种方法启动基于线程的作业：

- `Start-ThreadJob` -从 **ThreadJob** 模块
- `ForEach-Object -Parallel -AsJob` -已在 PowerShell 7.0 中添加并行功能

使用 [about_Jobs](about_Jobs.md)中所述的相同 **作业** cmdlet 来管理基于线程的作业。

### <a name="using-start-threadjob"></a>使用 `Start-ThreadJob`

**ThreadJob** 模块首次随附于 PowerShell 6。 还可以从 Windows PowerShell 5.1 PowerShell 库安装。

若要在本地计算机上启动线程作业，请使用 `Start-ThreadJob` 带有括在大括号中的命令或脚本的 cmdlet (`{ }`) 。

下面的示例启动一个 `Get-Process` 在本地计算机上运行命令的线程作业。

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

该 `Start-ThreadJob` 命令将返回一个 `ThreadJob` 对象，该对象表示正在运行的作业。 作业对象包含有关作业的有用信息，包括作业的当前运行状态。 它在生成结果时收集作业的结果。

### <a name="using-foreach-object--parallel--asjob"></a>使用 `ForEach-Object -Parallel -AsJob`

PowerShell 7.0 向 cmdlet 添加了一个新参数集 `ForEach-Object` 。 新参数允许你将并行线程中的脚本块作为 PowerShell 作业运行。

可以通过管道将数据传递给 `ForEach-Object -Parallel` 。 数据将传递到并行运行的脚本块。 `-AsJob`参数为每个并行线程创建作业对象。

下面的命令启动一个作业，该作业包含向命令传递的每个输入值的子作业。 每个子作业都将 `Write-Output` 使用一个管道输入值作为参数来运行该命令。

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

该 `ForEach-Object -Parallel` 命令将返回一个 `PSTaskJob` 对象，该对象包含每个管道输入值的子作业。 作业对象包含有关子作业运行状态的有用信息。 它在生成结果时收集子作业的结果。

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>如何等待作业完成并检索作业结果

你可以使用 PowerShell 作业 cmdlet （如 `Wait-Job` 和） `Receive-Job` 等待作业完成，然后返回作业生成的所有结果。

下面的命令启动一个运行命令的线程作业 `Get-Process` ，然后等待该命令完成，最后返回该命令生成的所有数据结果。

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

下面的命令启动一个作业，该作业 `Write-Output` 对每个管道输入运行一个命令，然后等待所有子作业完成，最后返回子作业生成的所有数据结果。

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

`Receive-Job`Cmdlet 返回子作业的结果。

```powershell
1
3
2
4
5
```

由于每个子作业都是并行运行的，因此不保证生成的结果的顺序。

## <a name="thread-job-performance"></a>线程作业性能

与其他类型的作业相比，线程作业的权重更快且更轻。 但与作业正在进行的工作相比，它们的开销可能会很大。

PowerShell 在会话中运行命令和脚本。 会话中一次只能运行一个命令或脚本。 因此，在运行多个作业时，每个作业都在单独的会话中运行。 每个会话都可提供开销。

当执行的工作大于用于运行作业的会话的开销时，线程作业可提供最佳性能。 满足此条件的情况有两种情况。

- 工作是计算密集型-在多个线程作业上运行脚本可充分利用多个处理器核心并更快完成。

- 工作包括大量等待时间的脚本，该脚本花费时间等待 i/o 或远程调用结果。 并行运行通常比按顺序运行快。

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

上面的第一个示例显示了一个 foreach 循环，该循环创建1000线程作业来编写简单的字符串。 由于作业开销，需要超过36秒钟才能完成。

第二个示例运行 `ForEach` cmdlet 来执行相同的1000操作。
这次 `ForEach-Object` 在单个线程上按顺序运行，无需任何作业开销。 它只会在7毫秒内完成。

在以下示例中，最多可为10个单独的系统日志收集5000个条目。 由于脚本涉及到读取多个日志，因此有必要并行执行操作。

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

脚本在并行运行作业的一半时间内完成。

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

## <a name="thread-jobs-and-variables"></a>线程作业和变量

可以通过多种方法将值传递到基于线程的作业中。

`Start-ThreadJob` 可以接受通过管道传递给脚本块的、通过关键字传递到脚本块的变量， `$using` 也可以通过 **ArgumentList** 参数传入。

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` 接受通过关键字直接传递到脚本块的变量和变量 `$using` 。

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

由于线程作业在同一进程中运行，因此必须仔细对待传入作业的任何变量引用类型。 如果它不是线程安全对象，则绝不应将其分配给，并且永远不应在其上调用方法和属性。

下面的示例将一个线程安全的 .NET `ConcurrentDictionary` 对象传递给所有子作业，以收集唯一命名的进程对象。 由于它是线程安全对象，因此可以安全地使用该对象，同时在进程中同时运行作业。

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

## <a name="see-also"></a>另请参阅

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
