---
description: 提供有关 PowerShell 后台作业如何在后台运行命令或表达式，而不与当前会话交互的信息。
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 862fbf54b927bb70c68e4b3cc43c564f178f9db5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598862"
---
# <a name="about-jobs"></a>关于作业

## <a name="short-description"></a>简短说明
提供有关 PowerShell 后台作业如何在后台运行命令或表达式，而不与当前会话交互的信息。

## <a name="long-description"></a>长说明

PowerShell 通过作业并发运行命令和脚本。 PowerShell 提供三种作业类型来支持并发。

- `RemoteJob` -命令和脚本在远程会话上运行。 有关信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。
- `BackgroundJob` -命令和脚本在本地计算机上的单独进程中运行。
- `PSTaskJob` 或 `ThreadJob` -命令和脚本在本地计算机上的同一进程内的单独线程中运行。 有关详细信息，请参阅 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。

在单独的计算机上或在单独的进程中远程运行脚本可提供强大的隔离。 远程作业中发生的任何错误都不会影响其他正在运行的作业或启动作业的父会话。 但是，远程处理层增加了开销，包括对象序列化。 所有对象都将进行序列化和反序列化，因为在父会话与远程 (作业) 会话之间传递它们。 大型复杂数据对象的序列化会消耗大量的计算和内存资源，并跨网络传输大量数据。

基于线程的作业不像远程和后台作业那样可靠，因为它们在不同线程上的同一进程中运行。 如果一个作业发生了导致进程崩溃的严重错误，则会终止该进程中的所有其他作业。

但是，基于线程的作业需要更少的开销。 它们不使用远程层或序列化。 结果对象作为对当前会话中活动对象的引用返回。 如果没有此开销，基于线程的作业运行速度更快，使用的资源比其他作业类型少。

> [!IMPORTANT]
> 创建作业的父会话还会监视作业状态和收集管道数据。 作业到达完成状态后，父进程终止了作业子进程。 如果终止了父会话，则所有正在运行的子作业都将与其子进程一起终止。

可通过两种方法解决此问题：

1. 用于 `Invoke-Command` 创建在断开连接的会话中运行的作业。 有关详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。
1. 使用 `Start-Process` 创建新进程，而不是作业。 有关详细信息，请参阅 [开始处理](xref:Microsoft.PowerShell.Management.Start-Process)。

## <a name="the-job-cmdlets"></a>作业 cmdlet

|Cmdlet          |说明                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |在本地计算机上启动后台作业。           |
|`Get-Job`       |获取在中启动的后台作业      |
|                |当前会话。                                       |
|`Receive-Job`   |获取后台作业的结果。                   |
|`Stop-Job`      |停止后台作业。                                |
|`Wait-Job`      |禁止显示命令提示符，直到其中一个或所有作业都为|
|                |完成.                                              |
|`Remove-Job`    |删除后台作业。                              |
|`Invoke-Command`|**AsJob** 参数在上创建后台作业  |
|                |远程计算机。 你可以使用 `Invoke-Command` 运行   |
|                |任何远程作业命令，包括 `Start-Job` 。       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>如何在本地计算机上启动作业

若要在本地计算机上启动后台作业，请使用 `Start-Job` cmdlet。

若要编写 `Start-Job` 命令，请将作业运行的命令括在大括号中， (`{}`) 。 使用 **ScriptBlock** 参数来指定命令。

下面的命令启动在 `Get-Process` 本地计算机上运行命令的后台作业。

```powershell
Start-Job -ScriptBlock {Get-Process}
```

启动后台作业时，命令提示符会立即返回，即使作业需要很长时间才能完成。 当该作业运行时，你可以继续在此会话中工作而不会发生中断。

`Start-Job`命令返回一个表示作业的对象。 作业对象包含有关该作业的有用信息，但是不包含作业结果。

可以将作业对象保存在变量中，然后将其与其他 **作业** cmdlet 一起使用来管理后台作业。 下面的命令启动作业对象并将生成的作业对象保存在 `$job` 变量中。

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

从 PowerShell 6.0 开始，可以使用 `&` 管道末尾 () 后台运算符来启动后台作业。 有关详细信息，请参阅 [背景运算符](about_Operators.md#background-operator-)。

使用 background 运算符在功能上等效于 `Start-Job` 在上一示例中使用 cmdlet。

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a>正在获取作业对象

`Get-Job`Cmdlet 返回对象，这些对象表示在当前会话中启动的后台作业。 如果没有参数，则 `Get-Job` 返回在当前会话中启动的所有作业。

```powershell
Get-Job
```

作业对象包含作业的状态，该状态指示作业是否已完成。 已完成的作业的状态为 " **完成** " 或 " **失败**"。 作业也可能被 **阻止** 或 **正在运行**。

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

可以将作业对象保存在变量中，并在后面的命令中使用它来表示作业。 以下命令获取 ID 为1的作业，并将其保存在 `$job` 变量中。

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>获取作业的结果

运行后台作业时，结果不会立即显示。 若要获取后台作业的结果，请使用 `Receive-Job` cmdlet。

下面的示例 `Receive-Job` 使用变量中的作业对象获取作业的结果 `$job` 。

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

可以将作业的结果保存在变量中。 以下命令将变量中的作业结果保存 `$job` 到 `$results` 变量中。

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>获取并保留部分作业结果

`Receive-Job`Cmdlet 将获取后台作业的结果。 如果作业已完成，则 `Receive-Job` 获取所有作业结果。 如果作业仍在运行，将 `Receive-Job` 获取迄今为止生成的结果。 可以再次运行 `Receive-Job` 命令来获取剩余结果。

默认情况下， `Receive-Job` 会从缓存中删除存储作业结果的结果。 再次运行时 `Receive-Job` ，只会获得首次运行后收到的新结果。

以下命令显示在 `Receive-Job` 作业完成之前运行的命令的结果。

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

使用 **Keep** 参数防止 `Receive-Job` 删除返回的作业结果。 以下命令显示对尚未完成的作业使用 **Keep** 参数的效果。

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a>正在等待结果

如果运行需要很长时间才能完成的命令，则可以使用作业对象的属性来确定作业的完成时间。 以下命令使用 `Get-Job` 对象获取当前会话中的所有后台作业。

```powershell
Get-Job
```

结果将显示在表中。 作业的状态显示在 " **状态** " 列中。

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

在这种情况下，" **状态** " 属性显示 "作业 2" 仍在运行。 如果你 `Receive-Job` 现在使用 cmdlet 来获取作业结果，结果将不完整。 可以重复使用此 `Receive-Job` cmdlet 来获取所有结果。 使用 **State** 属性来确定作业的完成时间。

你还可以使用该 cmdlet 的 **Wait** 参数 `Receive-Job` 。 如果使用此参数，则在作业完成并且所有结果都可用之前，cmdlet 不会返回命令提示符。

你还可以使用 `Wait-Job` cmdlet 等待作业的任何或所有结果。 `Wait-Job` 允许你等待一个或多个特定作业或所有作业。
以下命令使用 `Wait-Job` cmdlet 等待 **ID** 为的作业
10.

```powershell
Wait-Job -ID 10
```

因此，在作业完成之前，会禁止 PowerShell 提示。

还可以等待预先确定的时间段。 此命令使用 **Timeout** 参数将等待时间限制为120秒。 当时间到期时，命令提示符会返回，但作业将继续在后台运行。

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>停止作业

若要停止后台作业，请使用 `Stop-Job` cmdlet。 下面的命令启动一个作业以获取系统事件日志中的每个条目。 它将作业对象保存在 `$job` 变量中。

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

以下命令停止作业。 它使用管道运算符 (`|`) 将变量中的作业发送 `$job` 到 `Stop-Job` 。

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>删除作业

若要删除后台作业，请使用 `Remove-Job` cmdlet。 以下命令删除变量中的作业 `$job` 。

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>调查失败的作业

作业可能会因多种原因而失败。 作业对象包含 **Reason** 属性，其中包含有关失败原因的信息。

下面的示例启动一个作业，该作业没有所需的凭据。

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

检查 **原因** 属性以找到导致作业失败的错误。

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

在这种情况下，作业失败，因为远程计算机需要显式凭据才能运行该命令。 **Reason** 属性包含以下消息：

> 连接到远程服务器失败，出现以下错误消息： "访问被拒绝"。

## <a name="see-also"></a>请参阅

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
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
