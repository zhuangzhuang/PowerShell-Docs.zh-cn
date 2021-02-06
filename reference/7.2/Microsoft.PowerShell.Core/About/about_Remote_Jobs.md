---
description: 描述如何在远程计算机上运行作业。
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 93e1d3aba1f4037cc3c5c18386488bf321fc2a64
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598449"
---
# <a name="about-remote-jobs"></a>关于远程作业

## <a name="short-description"></a>简短说明
描述如何在远程计算机上运行后台作业。

## <a name="detailed-description"></a>详细说明

PowerShell 通过作业并发运行命令和脚本。 PowerShell 提供三种作业类型来支持并发。

- `RemoteJob` -命令和脚本在远程会话中运行。
- `BackgroundJob` -命令和脚本在本地计算机上的单独进程中运行。 有关详细信息，请参阅 [about_Jobs](about_Jobs.md)。
- `PSTaskJob` 或 `ThreadJob` -命令和脚本在本地计算机上的同一进程内的单独线程中运行。 有关详细信息，请参阅 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。

在单独的计算机上或在单独的进程中远程运行脚本可提供强大的隔离。 远程作业中发生的任何错误都不会影响其他正在运行的作业或启动作业的父会话。 但是，远程处理层增加了开销，包括对象序列化。 所有对象都将进行序列化和反序列化，因为在父会话与远程 (作业) 会话之间传递它们。 大型复杂数据对象的序列化会消耗大量的计算和内存资源，并跨网络传输大量数据。

> [!IMPORTANT]
> 创建作业的父会话还会监视作业状态和收集管道数据。 作业到达完成状态后，父进程终止了作业子进程。 如果终止了父会话，则所有正在运行的子作业都将与其子进程一起终止。

可通过两种方法解决此问题：

1. 用于 `Invoke-Command` 创建在断开连接的会话中运行的作业。 请参阅本文中的 [分离进程](#how-to-run-as-a-detached-process) 部分。
1. 使用 `Start-Process` 创建新进程，而不是作业。 有关详细信息，请参阅 [开始处理](xref:Microsoft.PowerShell.Management.Start-Process)。

## <a name="remote-jobs"></a>远程作业

您可以使用三种不同的方法在远程计算机上运行作业。

- 在远程计算机上启动交互式会话。 然后在交互式会话中启动作业。 尽管所有操作都是在远程计算机上执行的，但过程与运行本地作业相同。

- 在将其结果返回到本地计算机的远程计算机上运行作业。 如果要收集作业的结果并在本地计算机上的一个中心位置维护这些作业的结果，请使用此方法。

- 在远程计算机上运行作业，该作业在远程计算机上维护其结果。 在源计算机上更安全地维护作业数据时使用此方法。

### <a name="start-a-job-in-an-interactive-session"></a>在交互式会话中启动作业

您可以启动与远程计算机的交互式会话，然后在交互式会话过程中启动作业。 有关交互式会话的详细信息，请参阅 about_Remote，并参阅 `Enter-PSSession` 。

在交互式会话中启动作业的过程与在本地计算机上启动后台作业的过程几乎相同。 但是，所有操作都在远程计算机上执行，而不是在本地计算机上进行。

1. 使用 `Enter-PSSession` cmdlet 来启动与远程计算机的交互式会话。 您可以使用 ComputerName 参数 `Enter-PSSession` 为交互式会话建立临时连接。 或者，可以使用 Session 参数 (PSSession) 在 PowerShell 会话中运行交互式会话。

   以下命令在 Server01 计算机上启动交互式会话。

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   命令提示符更改为显示你现在已连接到 Server01 计算机。

   ```
   Server01\C:>
   ```

1. 若要在会话中启动远程作业，请使用 `Start-Job` cmdlet。 以下命令运行远程作业，该作业获取 Server01 计算机上的 Windows PowerShell 事件日志中的事件。 `Start-Job`Cmdlet 将返回表示作业的对象。

   此命令将作业对象保存在 `$job` 变量中。

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   作业运行时，可以使用交互式会话来运行其他命令，包括其他作业。 但是，必须在作业完成之前使交互式会话保持打开状态。 如果结束该会话，则该作业将中断，结果将丢失。

1. 若要查看作业是否已完成，请显示变量的值 `$job` ，或使用 `Get-Job` cmdlet 来获取作业。 以下命令使用 `Get-Job` cmdlet 来显示作业。

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   `Get-Job`此输出显示作业正在 "localhost" 计算机上运行，因为该作业已在同一台计算机上运行， (在这种情况下，Server01) 。

1. 若要获取作业结果，请使用 `Receive-Job` cmdlet。 可以在交互式会话中显示结果，也可以将结果保存到远程计算机上的文件中。 下面的命令获取 $job 变量中的作业的结果。 该命令使用重定向运算符 (`>`) 将作业结果保存到 Server01 计算机上的 PsLog.txt 文件中。

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. 若要结束交互式会话，请使用 `Exit-PSSession` cmdlet。 命令提示符将更改为显示您返回到本地计算机上的原始会话中。

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. 若要随时查看 `PsLog.txt` Server01 计算机上文件的内容，请启动另一交互式会话或运行远程命令。 如果要使用多个命令来调查和管理文件中的数据，这种类型的命令最好在 PSSession (持久性连接) 中运行 `PsLog.txt` 。 有关 Pssession 的详细信息，请参阅 [about_PSSessions](about_PSSessions.md)。

   以下命令使用 `New-PSSession` cmdlet 创建连接到 Server01 计算机的 **PSSession** ，并使用 `Invoke-Command` cmdlet `Get-Content` 在 pssession 中运行命令，以查看文件的内容。

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>启动将结果返回到本地计算机的远程作业 (AsJob) 

若要在将命令结果返回到本地计算机的远程计算机上启动作业，请使用 cmdlet 的 **AsJob** 参数，如 `Invoke-Command` cmdlet。

使用 **AsJob** 参数时，实际上会在本地计算机上创建作业对象，即使该作业在远程计算机上运行也是如此。 完成作业后，结果将返回到本地计算机。

你可以使用包含 job 名词的 cmdlet (作业 cmdlet) 管理任何 cmdlet 创建的任何作业。 许多具有 **AsJob** 参数的 cmdlet 不使用 PowerShell 远程处理，因此您甚至可以在未配置为进行远程处理并且不满足远程处理要求的计算机上使用它们。

1. 以下命令使用的 **AsJob** 参数 `Invoke-Command` 在 Server01 计算机上启动作业。 作业运行 `Get-Eventlog` 可获取系统日志中的事件的命令。 可以使用 JobName 参数为作业指定显示名称。

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   命令的结果类似于以下示例输出。

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   使用 **AsJob** 参数时， `Invoke-Command` 将返回返回的相同类型的作业对象 `Start-Job` 。 可以将作业对象保存在变量中，也可以使用 `Get-Job` 命令来获取作业。

   请注意，Location 属性的值显示作业在 Server01 计算机上运行。

1. 若要管理使用 cmdlet 的 **AsJob** 参数启动的作业 `Invoke-Command` ，请使用作业 cmdlet。 由于表示远程作业的作业对象位于本地计算机上，因此无需运行远程命令来管理该作业。

   若要确定作业是否已完成，请使用 `Get-Job` 命令。 以下命令将获取在当前会话中启动的所有作业。

   ```powershell
   Get-Job
   ```

   由于远程作业是在当前会话中启动的，因此本地 `Get-Job` 命令会获取该作业。 作业对象的 State 属性显示该命令已成功完成。

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. 若要获取作业结果，请使用 `Receive-Job` cmdlet。 由于作业结果会自动返回到作业对象所在的计算机，因此你可以使用本地命令获取结果 `Receive-Job` 。

   以下命令使用 `Receive-Job` cmdlet 来获取作业的结果。 它使用会话 ID 来标识作业。 此命令将作业结果保存在 $results 变量中。 你还可以将结果重定向到文件。

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>启动远程作业以在远程计算机上保留结果

若要在远程计算机上启动将命令结果保存在远程计算机上的作业，请使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。 您可以使用此方法在多台计算机上运行作业。

远程运行命令时 `Start-Job` ，将在远程计算机上创建作业对象，并在远程计算机上维护作业结果。
从作业的角度来看，所有操作都是本地的。 你只需远程运行命令来管理远程计算机上的本地作业。

1. 使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。

   此命令需要 PSSession (持久性连接) 。 如果使用 ComputerName 参数 `Invoke-Command` 来建立临时连接，则在 `Invoke-Command` 返回作业对象时，该命令被视为已完成。 因此，临时连接将关闭，并且该作业将被取消。

   以下命令使用 `New-PSSession` cmdlet 创建连接到 Server01 计算机的 PSSession。 该命令将 PSSession 保存在 `$s` 变量中。

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   下一个命令使用 `Invoke-Command` cmdlet `Start-Job` 在 PSSession 中运行命令。 `Start-Job`命令和 `Get-Eventlog` 命令括在大括号中。

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   结果类似于以下示例输出。

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   远程运行命令时 `Start-Job` ， `Invoke-Command` 将返回返回的相同类型的作业对象 `Start-Job` 。 可以将作业对象保存在变量中，也可以使用 `Get-Job` 命令来获取作业。

   请注意， **Location** 属性的值显示作业在本地计算机上运行，也称为 "LocalHost"，即使该作业在 Server01 计算机上运行也是如此。 由于作业对象是在 Server01 计算机上创建的，并且作业在同一台计算机上运行，因此将其视为本地后台作业。

1. 若要管理远程作业，请使用 **作业** cmdlet。 由于作业对象位于远程计算机上，因此您需要运行远程命令来获取、停止、等待或检索作业结果。

   若要查看作业是否已完成，请使用 `Invoke-Command` 命令 `Get-Job` 在连接到 Server01 计算机的 PSSession 中运行命令。

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   该命令返回一个作业对象。 作业对象的 **State** 属性显示该命令已成功完成。

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. 若要获取作业结果，请使用 `Invoke-Command` cmdlet `Receive-Job` 在已连接到 Server01 计算机的 PSSession 中运行命令。

   以下命令使用 `Receive-Job` cmdlet 来获取作业的结果。 它使用会话 ID 来标识作业。 此命令将作业结果保存在 `$results` 变量中。 它使用 Keep 参数将 `Receive-Job` 结果保存在远程计算机上的作业缓存中。

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   你还可以将结果重定向到本地或远程计算机上的文件。
   以下命令使用重定向运算符将结果保存到 Server01 计算机上的文件中。

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>如何作为分离的进程运行

如前所述，当终止父会话时，所有正在运行的子作业都将与其子进程一起终止。 你可以使用本地计算机上的远程处理来运行未附加到当前 PowerShell 会话的作业。

在本地计算机上创建新的 PowerShell 会话。 用于 `Invoke-Command` 在此会话中启动作业的。 `Invoke-Command` 允许您断开远程会话的连接，并终止父会话。 稍后，可以启动新的 PowerShell 会话并连接到之前断开连接的会话，以恢复监视作业。 但是，当终止该会话时，返回到原始 PowerShell 会话的任何数据都将丢失。 重新连接后，只会返回断开连接后生成的新数据对象。

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

在此示例中，作业仍附加到父 PowerShell 会话。
但是，父会话并不是运行的原始 PowerShell 会话 `Invoke-Command` 。

## <a name="see-also"></a>请参阅

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
