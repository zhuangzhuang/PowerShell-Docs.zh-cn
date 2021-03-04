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
# <a name="about-scheduled-jobs-troubleshooting"></a>关于计划作业故障排除

## <a name="short-description"></a>简短说明

说明如何解决计划作业的问题

## <a name="long-description"></a>长说明

本文档介绍了使用 PowerShell 的计划作业功能时可能会遇到的一些问题，并建议解决这些问题。

使用 PowerShell 计划作业之前，请参阅 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 和相关的计划作业。

有关 **PSScheduledJob** 模块中包含的 cmdlet 的详细信息，请参阅 [PSScheduledJob](xref:PSScheduledJob)。

## <a name="cant-find-job-results"></a>找不到作业结果

### <a name="basic-method-for-getting-job-results-in-powershell"></a>在 PowerShell 中获取作业结果的基本方法

当计划作业运行时，它会创建计划作业的实例。 若要查看、管理和获取计划作业实例的结果，请使用作业 cmdlet。

> [!NOTE]
> 若要在计划作业的实例上使用作业 cmdlet，则必须将 **PSScheduledJob** 模块导入到会话中。 若要导入 **PSScheduledJob** 模块，请键入 `Import-Module PSScheduledJob` 或使用任何计划的作业 cmdlet，例如 `Get-ScheduledJob` 。

若要获取某个计划作业的所有实例的列表，请使用 `Get-Job` cmdlet。

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

`Get-Job`Cmdlet 将 **ProcessJob** 对象向下发送管道。 `Format-Table`Cmdlet 将在表中显示计划作业实例的 **Name**、 **ID** 和 **PSBeginTime** 属性。

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

若要获取某个计划作业的实例的结果，请使用 `Receive-Job` cmdlet。 以下命令获取 ProcessJob (ID = 50) 的最新实例的结果。

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>在磁盘上查找作业结果的基本方法

若要管理计划作业，请使用作业 cmdlet，例如 `Get-Job` 和 `Receive-Job` 。

如果 `Get-Job` 未获取作业实例或 `Receive-Job` 未获取作业结果，你可以在磁盘上搜索作业的执行历史记录文件。
执行历史记录包含所有触发的作业实例的记录。

验证目录中是否存在用于以下路径中的计划作业的时间戳的目录：

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

例如：

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

例如，该 `Get-ChildItem` cmdlet 将获取 **ProcessJob** 计划作业的磁盘上执行历史记录。

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

每个时间戳的目录都表示一个作业实例。 每个作业实例的结果保存在时间戳命名目录中的 **Results.xml** 文件中。

例如，以下命令将获取 **ProcessJob** 计划作业的每个已保存实例的 **Results.xml** 文件。 如果缺少 **Results.xml** 文件，则 PowerShell 无法返回或显示作业结果。

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

由于 **PSScheduledJob** 模块未导入到会话中，作业 cmdlet 可能无法获取计划的作业实例或其结果。

> [!NOTE]
> 在计划的作业实例上使用 job cmdlet 之前，请验证会话中是否包含 **PSScheduledJob** 模块。 如果没有 **PSScheduledJob** 模块，作业 cmdlet 无法获取计划的作业实例或其结果。

导入 **PSScheduledJob** 模块：

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>Receive-Job cmdlet 可能已返回结果

如果不 `Receive-Job` 返回作业实例结果，则可能是因为 `Receive-Job` 在没有 **Keep** 参数的情况下，已在当前会话中为该作业实例运行了一个命令。

在不使用 `Receive-Job` **Keep** 参数的情况下，将 `Receive-Job` 返回作业结果，并将作业实例的 **HasMoreData** 属性设置为 **False**。 **False** 值表示 `Receive-Job` 返回了作业的结果，并且实例没有更多要返回的结果。 此设置适用于标准后台作业，但不适用于保存在磁盘上的计划作业的实例。

若要再次获取作业实例结果，请通过键入启动新的 PowerShell 会话 `PowerShell` 。 导入 **PSScheduledJob** 模块，然后重试该 `Receive-Job` 命令。

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

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>使用 Keep 参数在一个会话中多次获得结果

若要在一个会话中多次获取某一作业实例的结果，请使用该 cmdlet 的 **Keep** 参数 `Receive-Job` 。

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

### <a name="the-scheduled-job-might-be-corrupted"></a>计划的作业可能已损坏

如果计划的作业损坏，PowerShell 将删除已损坏的计划作业及其结果。 不能恢复已损坏的计划作业的结果。

若要确定计划的作业是否仍存在，请使用 `Get-ScheduledJob` cmdlet。

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>结果数可能已超过 ExecutionHistoryLength

计划作业的 **ExecutionHistoryLength** 属性决定将多少作业实例及其结果保存到磁盘。 默认值为 32。
当计划作业的实例数超过此值时，PowerShell 会删除最旧的作业实例，为每个新作业实例腾出空间。

若要获取某个计划作业的 **ExecutionHistoryLength** 属性的值，请使用以下命令格式：

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

例如，以下命令获取 **ProcessJob** 计划作业的 **ExecutionHistoryLength** 属性的值。

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

若要设置或更改 **ExecutionHistoryLength** 属性的值，请使用和 Cmdlet 的 **MaxResultCount** 参数 `Register-ScheduledJob` `Set-ScheduledJob` 。

以下命令将 **ExecutionHistoryLength** 属性的值增加到50。

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>作业实例结果可能已被删除

Cmdlet 的 **ClearExecutionHistory** 参数 `Set-ScheduledJob` 删除作业的执行历史记录。 您可以使用此功能释放磁盘空间或删除不需要的结果，或者删除在不同位置分析或保存的结果。

若要删除计划作业的执行历史记录，请使用该计划作业的 **ClearExecutionHistory** 参数。

以下命令删除 **ProcessJob** 计划作业的执行历史记录。

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

此外，cmdlet 还会 `Remove-Job` 删除作业结果。 当你使用 `Remove-Job` 删除计划的作业时，它将删除磁盘上的所有作业实例，包括执行历史记录和所有作业结果。

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>使用 Start-Job cmdlet 启动的作业不会保存到磁盘

当使用 `Start-Job` 启动计划作业时，将 `Start-Job` 启动标准后台作业，而不是使用作业触发器。 后台作业及其结果不存储在磁盘上作业的执行历史记录中。

你可以使用 `Get-Job` cmdlet 来获取作业和 `Receive-Job` cmdlet 以获取作业结果，但只有在收到这些结果后，才可使用该 cmdlet，除非你使用 Cmdlet 的 Keep 参数 `Receive-Job` 。

此外，后台作业及其结果都是特定于会话的;它们只存在于创建它们的会话中。 如果删除了该作业 `Remove-Job` ，请关闭会话或关闭 PowerShell，然后删除该作业实例及其结果。

## <a name="scheduled-job-doesnt-run"></a>计划的作业不运行

如果作业触发或计划作业处于禁用状态，则计划作业不会自动运行。

使用 `Get-ScheduledJob` cmdlet 来获取计划作业。 验证计划作业的 **Enabled** 属性的值是否为 **True**。

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

使用 `Get-JobTrigger` cmdlet 可获取计划作业的作业触发器。
验证作业触发器的 **Enabled** 属性的值是否为 **True**。

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

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>如果作业触发器无效，则计划作业不会自动运行

例如，作业触发器可以指定过去的日期或不会发生的日期，如月份的第五个星期一。

如果未满足作业触发器或作业选项的条件，则计划作业不会自动运行。

例如，仅当特定用户登录到计算机时才会运行的计划作业不会运行（如果该用户未登录或仅远程连接）。

检查计划作业的选项，并确保满足这些选项。
例如，需要计算机处于空闲状态或需要网络连接的计划作业，或者永远不会运行长 **IdleDuration** 或短暂的 **IdleTimeout** 。

使用 `Get-ScheduledJobOption` cmdlet 检查作业选项及其值。

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

有关计划作业选项的说明，请参阅 [get-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)。

### <a name="the-scheduled-job-instance-might-have-failed"></a>计划的作业实例可能已失败

如果计划作业命令失败，则 PowerShell 会通过生成错误消息立即报告它。 但是，如果作业在任务计划程序尝试运行它时失败，则 PowerShell 将无法使用此错误。

使用以下方法来检测和更正作业故障：

检查任务计划程序事件日志中是否存在错误。 若要查看日志，请使用事件查看器或 PowerShell 命令，如下所示：

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

在任务计划程序中检查作业记录。 PowerShell 计划作业存储在下列任务计划文件夹中：

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>由于权限不足，计划作业可能无法运行

计划作业使用创建作业的用户的权限运行，或使用或命令中的 **Credential** 参数指定的权限运行 `Register-ScheduledJob` `Set-ScheduledJob` 。

如果该用户没有运行命令或脚本的权限，则该作业将失败。

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>无法获取计划作业或计划作业已损坏

在极少数情况下，计划作业可能会损坏或包含无法解析的内部矛盾。 通常，当手动编辑计划作业的 XML 文件时，会出现这种情况，从而导致无效的 XML。

如果计划的作业损坏，则 PowerShell 将尝试从磁盘删除计划作业、其执行历史记录和结果。

如果无法删除计划的作业，则每次运行该 cmdlet 时，都将收到损坏的作业错误消息 `Get-ScheduledJob` 。

若要删除已损坏的计划作业，请使用以下方法之一：

删除 `<ScheduledJobName>` 计划作业的目录。 请勿删除 **get-scheduledjob** 目录。

目录的位置：

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

例如：

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

使用任务计划程序删除计划的作业。 PowerShell 计划任务出现在以下任务计划程序路径中：

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>作业 cmdlet 无法一致地查找计划作业

当 **PSScheduledJob** 模块不在当前会话中时，作业 cmdlet 无法获取计划作业、启动作业或获取其结果。

若要导入 **PSScheduledJob** 模块，请键入 `Import-Module PSScheduledJob` 或运行或获取该模块中的任何 cmdlet，如 `Get-ScheduledJob` cmdlet。
从 PowerShell 3.0 开始，当你获取或使用模块中的任何 cmdlet 时，模块会自动导入。

当 **PSScheduledJob** 模块不在当前会话中时，可以执行以下命令序列。

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

之所以发生此行为，是因为该 `Get-ScheduledJob` 命令会自动导入 **PSScheduledJob** 模块，然后运行命令。

## <a name="see-also"></a>另请参阅

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[PSScheduledJob](xref:PSScheduledJob) 模块 cmdlet

[任务计划程序](/windows/desktop/TaskSchd/task-scheduler-reference)
