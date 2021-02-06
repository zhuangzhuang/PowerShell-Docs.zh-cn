---
description: 提供有关本地和远程计算机上的后台作业的详细信息。
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 1ceb0be9cc140b69afdebaaf336dad75e482aa22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597078"
---
# <a name="about-job-details"></a>关于作业详细信息

## <a name="short-description"></a>简短说明
提供有关本地和远程计算机上的后台作业的详细信息。

## <a name="detailed-description"></a>详细说明

本主题介绍后台作业的概念，并提供有关后台作业在 PowerShell 中的工作原理的技术信息。

本主题是对 [about_Jobs](about_Jobs.md)、 [about_Thread_Jobs](about_Thread_Jobs.md)和 [about_Remote_Jobs](about_Remote_Jobs.md) 主题的补充。

### <a name="about-background-jobs"></a>关于后台作业

后台作业异步运行命令或表达式。 它可以运行 cmdlet、函数、脚本或任何其他基于命令的任务。 它旨在运行长时间运行的命令，但你可以使用它在后台运行任何命令。

同步命令运行时，会禁止 PowerShell 命令提示符，直到命令完成。 但后台作业不会显示 PowerShell 提示。 用于启动后台作业的命令返回一个作业对象。
提示符会立即返回，以便在后台作业运行时可以处理其他任务。

但在启动后台作业时，即使作业运行速度很快，也不会立即获得结果。 返回的作业对象包含有关该作业的有用信息，但不包含作业结果。 必须运行单独的命令来获取作业结果。 你还可以运行命令来停止作业，等待作业完成，并删除作业。

为了使后台作业的时间与其他命令无关，每个后台作业都在其自己的 PowerShell 会话中运行。 但是，这可能是只是为了运行作业而创建的临时连接，然后将其销毁，或者可以使用永久性 **PSSession** 来运行多个相关的作业或命令。

### <a name="using-the-job-cmdlets"></a>使用作业 cmdlet

使用 `Start-Job` 命令在本地计算机上启动后台作业。
`Start-Job` 返回一个作业对象。 你还可以使用 cmdlet 来获取表示在本地计算机上启动的作业的对象 `Get-Job` 。

若要获取作业结果，请使用 `Receive-Job` 命令。 如果作业未完成，则 `Receive-Job` 返回部分结果。 你还可以使用 `Wait-Job` cmdlet 来禁止显示命令提示符，直到在会话中启动的一个或所有作业完成为止。

若要停止后台作业，请使用 `Stop-Job` cmdlet。 若要删除作业，请使用 `Remove-Job` cmdlet。

有关 cmdlet 的工作原理的详细信息，请参阅每个 cmdlet 的帮助主题，并参阅 [about_Jobs](about_Jobs.md)。

### <a name="starting-background-jobs-on-remote-computers"></a>在远程计算机上启动后台作业

可以在本地或远程计算机上创建和管理后台作业。 若要远程运行后台作业，请使用 cmdlet （如）的 **AsJob** 参数 `Invoke-Command` ，或使用 `Invoke-Command` cmdlet `Start-Job` 远程运行命令。 你还可以在交互式会话中启动后台作业。

有关远程后台作业的详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。

### <a name="child-jobs"></a>子作业

每个后台作业都包含一个父作业和一个或多个子作业。 在使用 `Start-Job` 或的 **AsJob** 参数启动的作业中 `Invoke-Command` ，父作业是执行程序。 它不会运行任何命令，也不会返回任何结果。 命令实际上由子作业运行。 使用其他 cmdlet 启动的作业的工作方式可能会有所不同。

子作业存储在父作业对象的 **ChildJobs** 属性中。 **ChildJobs** 属性可以包含一个或多个子作业对象。
子作业对象具有与父作业不同的 **名称**、 **ID** 和 **InstanceId** ，以便您可以单独或作为一个单元管理父作业和子作业。

若要获取作业的父作业和子作业，请使用 cmdlet 的 **IncludeChildJobs** 参数 `Get-Job` 。 **IncludeChildJob** 参数是在 Windows PowerShell 3.0 中引入的。

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

若要获取父作业和仅具有特定 **状态** 值的子作业，请使用 Cmdlet 的 **ChildJobState** 参数 `Get-Job` 。 **ChildJobState** 参数是在 Windows PowerShell 3.0 中引入的。

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

若要获取所有版本的 PowerShell 上作业的子作业，请使用父作业的 **ChildJob** 属性。

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

你还可以 `Get-Job` 对子作业使用命令，如以下命令中所示：

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

子作业的配置取决于用于启动作业的命令。

- 当你使用在 `Start-Job` 本地计算机上启动作业时，该作业包含一个执行程序父作业和一个运行该命令的子作业。

- 使用的 **AsJob** 参数 `Invoke-Command` 启动一台或多台计算机上的作业时，该作业将包含执行程序父作业和每台计算机上运行的每个作业的子作业。

- 当您使用 `Invoke-Command` `Start-Job` 在一台或多台远程计算机上运行命令时，其结果与在每台远程计算机上运行的本地命令相同。 此命令为每台计算机返回一个作业对象。 作业对象由一个运行命令的执行程序父作业和一个子作业组成。

父作业表示所有子作业。 管理父作业时，还会管理关联的子作业。 例如，如果停止父作业，则会停止所有子作业。 如果获取父作业的结果，则会获得所有子作业的结果。

但是，你还可以单独管理子作业。 当你希望调查某个作业的问题，或者只获取使用 **AsJob** 参数启动的多个子作业之一的结果时，这非常有用 `Invoke-Command` 。

以下命令使用的 **AsJob** 参数在 `Invoke-Command` 本地计算机和两台远程计算机上启动后台作业。 该命令将作业保存在 `$j` 变量中。

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

当你在中显示作业的 Name 和 **ChildJob** 属性时 `$j` ，它会显示该命令返回一个作业对象，其中包含三个子作业，每台计算机一个。

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

显示父作业时，它会显示作业失败。

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

但在运行 `Get-Job` 获取子作业的命令时，输出会显示只有一个子作业失败。

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

若要获取所有子作业的结果，请使用 `Receive-Job` cmdlet 获取父作业的结果。 但也可以获取特定子作业的结果，如以下命令中所示。

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

PowerShell 后台作业的子作业功能使你可以更好地控制你运行的作业。

### <a name="job-types"></a>作业类型

对于不同任务，PowerShell 支持不同类型的作业。 从 Windows PowerShell 3.0 开始，开发人员可以编写 "作业源适配器"，将新作业类型添加到 PowerShell，并在模块中包含作业源适配器。
导入模块时，你可以在会话中使用新作业类型。

例如，PSScheduledJob 模块添加了计划作业，PSWorkflow 模块添加了工作流作业。

自定义作业类型与标准 PowerShell 后台作业可能有明显差异。 例如，计划作业保存在磁盘上;它们不存在于特定的会话中。 可以挂起和恢复工作流作业。

用于管理自定义作业的 cmdlet 依赖于作业类型。 对于某些情况，请使用标准作业 cmdlet，例如 `Get-Job` 和 `Start-Job` 。 其他人附带了专门的 cmdlet，只管理特定类型的作业。 有关自定义作业类型的详细信息，请参阅有关作业类型的帮助主题。

若要查找作业的作业类型，请使用 `Get-Job` cmdlet。 `Get-Job` 为不同类型的作业返回不同的作业对象。 返回的作业对象的 **PSJobTypeName** 属性值 `Get-Job` 指示作业类型。

下表列出了 PowerShell 附带的作业类型。

|    作业类型    |                       说明                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | 已开始使用 `Start-Job` cmdlet。                    |
| RemoteJob      | 已开始使用的 **AsJob** 参数             |
|                | `Invoke-Command` cmdlet。                                 |
| PSWorkflowJob  | 已开始使用工作流的 **AsJob** 参数。     |
| PSScheduledJob | 作业触发器启动的计划作业的实例。 |
| CIMJob         | 已开始使用 cmdlet 的 **AsJob** 参数 |
|                | CDXML 模块。                                            |
| WMIJob         | 已开始使用 cmdlet 的 **AsJob** 参数 |
|                | WMI 模块。                                              |
| PSEventJob     | 使用创建 `Register-ObjectEvent` 并指定    |
|                | **操作参数的** 操作。                    |

注意：使用 `Get-Job` cmdlet 获取特定类型的作业之前，请验证添加作业类型的模块是否已导入到当前会话中。
否则，不 `Get-Job` 会获取该类型的作业。

## <a name="examples"></a>示例

以下命令将创建本地后台作业、远程后台作业、工作流作业和计划作业。 然后，它使用 `Get-Job` cmdlet 来获取作业。 `Get-Job` 不会获得计划作业，但会获取计划作业的任何已启动实例。

在本地计算机上启动后台作业。

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

启动在远程计算机上运行的后台作业。

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

创建计划作业

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

创建工作流。

```powershell
PS> workflow Test-Workflow {Get-Process}
```

以作业形式运行工作流。

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

获取作业。 此 `Get-Job` 命令不会获取计划作业，但会获取已启动的计划作业的实例。

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

若要获取计划作业，请使用 `Get-ScheduledJob` cmdlet。

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>请参阅

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Remote](about_Remote.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
