---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: ffcd0fba9fae9ed49e7f20fa5a971e6e50fc445f
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99597236"
---
# Wait-Job

## 摘要
等待在会话中运行的一个或所有 PowerShell 作业处于终止状态。

## SYNTAX

### SessionIdParameterSet（默认值）

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

`Wait-Job`Cmdlet 会等待作业处于终止状态，然后再继续执行。
终止状态为：

- 已完成
- 已失败
- 已停止
- Suspended
- 已断开连接

可以等待指定的作业，或者所有作业都处于终止状态。 你还可以使用 **Timeout** 参数为作业设置最长等待时间，或使用 **Force** 参数等待或状态下的作业 `Suspended` `Disconnected` 。

当作业中的命令完成时， `Wait-Job` 将返回一个作业对象，并继续执行。

可以使用 cmdlet `Wait-Job` 等待使用 cmdlet `Start-Job` 或 Cmdlet 的 **AsJob** 参数启动的作业 `Invoke-Command` 。 有关作业的详细信息，请参阅 [about_Jobs](./about/about_Jobs.md)。

从 Windows PowerShell 3.0 开始， `Wait-Job` cmdlet 还会等待自定义作业类型，例如工作流作业和计划作业的实例。 若要使 `Wait-Job` 能够等待特定类型的作业，请在运行 cmdlet 之前将支持自定义作业类型的模块导入到会话中，方法 `Get-Job` 是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。 有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。

## 示例

### 示例1：等待所有作业

```powershell
Get-Job | Wait-Job
```

此命令等待在会话中运行的所有作业完成。

### 示例2：使用 Start-Job 等待远程计算机上启动的作业

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

此示例显示了如何 `Wait-Job` 通过 cmdlet 将 cmdlet 用于远程计算机上启动的作业 `Start-Job` 。 `Start-Job` `Wait-Job` 使用 cmdlet 将和命令提交到远程计算机 `Invoke-Command` 。

此示例使用 `Wait-Job` 来确定 `Get-Date` 在三台不同计算机上作为作业运行的命令是否完成。

第一个命令在三台远程计算机的每台计算机上创建一个 (**PSSession**) 的 Windows PowerShell 会话，并将其存储在 `$s` 变量中。

第二个命令使用在 `Invoke-Command` `Start-Job` 中的三个会话中运行 `$s` 。
所有作业都命名为 Date1。

第三个命令使用 `Invoke-Command` 来运行 `Wait-Job` 。 此命令等待 `Date1` 每台计算机上的作业完成。 它将生成的集合存储 (**数组** 中的 **作业** 对象) `$done` 。

第四个命令使用变量中的作业对象数组的 **Count** 属性 `$done` 来确定完成的作业数。

### 示例3：确定第一个作业完成的时间

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

此示例使用的 **Any** 参数 `Wait-Job` 来确定在当前会话中运行的多个作业的第一个处于终止状态的时间。 它还演示了如何使用 `Wait-Job` cmdlet 等待远程作业完成。

第一个命令在 Machines.txt 文件中列出的每台计算机上创建 **pssession** ，并将 **pssession** 对象存储在 `$s` 变量中。 该命令使用 `Get-Content` cmdlet 来获取文件的内容。 `Get-Content`命令括在括号中，以确保它在命令之前运行 `New-PSSession` 。

第二个命令将 `Get-EventLog` 命令字符串用引号引起来 `$c` 。

第三个命令使用 `Invoke-Command` cmdlet `Start-Job` 在中的每个会话中运行 `$s` 。
`Start-Job`命令启动一个作业，该作业 `Get-EventLog` 在变量中运行该命令 `$c` 。

该命令使用 **Using** 作用域修饰符来指示该 `$c` 变量是在本地计算机上定义的。 在 Windows PowerShell 3.0 中引入了 **Using** 作用域修饰符。 有关 **Using** 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](./about/about_Remote_Variables.md)。

第四个命令使用 `Invoke-Command` `Wait-Job` 在会话中运行命令。 它使用 **Any** 参数等待，直到远程计算机上的第一个作业终止状态。

### 示例4：设置远程计算机上的作业的等待时间

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

此示例演示如何使用的 **Timeout** 参数设置在 `Wait-Job` 远程计算机上运行的作业的最长等待时间。

第一个命令在 (Server01、Server02 和 Server03) 的三台远程计算机上创建 **pssession** ，然后将 **pssession** 对象存储在 `$s` 变量中。

第二个命令使用在 `Invoke-Command` `Start-Job` 中的每个 **PSSession** 对象中运行 `$s` 。 它将生成的作业对象存储在 `$jobs` 变量中。

第三个命令使用 `Invoke-Command` `Wait-Job` 在中的每个会话中运行 `$s` 。 `Wait-Job`命令确定所有命令是否在30秒内完成。 它使用值为30的 **Timeout** 参数来建立最长等待时间，然后将命令的结果存储在 `$done` 变量中。

在此示例中，30 秒后，只有 Server02 计算机上的命令完成。 `Wait-Job` 结束等待，返回表示已完成作业的对象，然后显示命令提示符。

`$done`变量包含一个作业对象，该对象表示在 Server02 上运行的作业。

### 示例5：等待多个作业中的一个完成

```powershell
Wait-Job -id 1,2,5 -Any
```

此命令按 Id 标识三个作业，并等待其中任何一个作业处于终止状态。 当第一个作业完成时，执行将继续。

### 示例6：等待一段时间，然后允许作业在后台继续

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

此命令120等待 DailyLog 作业 (两分钟) ，直到完成。 如果作业未在接下来的两分钟内完成，则执行将继续，并且作业继续在后台运行。

### 示例7：按名称等待作业

```powershell
Wait-Job -Name "Job3"
```

此命令使用作业名称来标识要等待的作业。

### 示例8：等待本地计算机上的作业开始 Start-Job

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

此示例演示如何 `Wait-Job` 通过使用将 cmdlet 用于本地计算机上启动的作业 `Start-Job` 。

这些命令启动一个可获取在上一周添加或更新的 Windows PowerShell 脚本文件的作业。

第一个命令使用 `Start-Job` 在本地计算机上启动作业。 作业运行一个 `Get-ChildItem` 命令，该命令获取在上周添加或更新的文件扩展名为 ps1 的所有文件。

第三个命令使用 `Wait-Job` 等待直到作业处于终止状态。 作业完成后，该命令将显示作业对象，该对象包含有关作业的信息。

### 示例9：使用 Invoke-Command 等待远程计算机上启动的作业

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

此示例演示如何 `Wait-Job` 通过使用的 **AsJob** 参数，将用于远程计算机上启动的作业 `Invoke-Command` 。 使用 **AsJob** 时，将在本地计算机上创建作业，并自动将结果返回到本地计算机，即使作业运行在远程计算机上也是如此。

此示例使用 `Wait-Job` 来确定 `Get-Process` 三台远程计算机上的会话中运行的命令是否处于终止状态。

第一个命令在三台计算机上创建 **PSSession** 对象并将其存储在 `$s` 变量中。

第二个命令使用在 `Invoke-Command` `Get-Process` 中的三个会话中运行 `$s` 。
该命令使用 **AsJob** 参数以异步方式将命令作为作业运行。 命令返回一个作业对象，就像使用启动的作业一样， `Start-Job` 作业对象存储在 `$j` 变量中。

第三个命令使用管道运算符 (`|`) 将作业对象发送 `$j` 到 `Wait-Job` cmdlet。 `Invoke-Command`在这种情况下，不需要使用命令，因为作业驻留在本地计算机上。

### 示例10：等待 ID 为的作业

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

此命令等待 ID 值为 1 的作业。

## PARAMETERS

### -Any

指示此 cmdlet 返回作业对象并在任何作业完成时继续执行。 默认情况下，将 `Wait-Job` 一直等待，直到所有指定的作业完成后才显示提示。

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

### -Filter

指定条件的哈希表。 此 cmdlet 将等待满足哈希表中所有条件的作业。 输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。

此参数仅适用于自定义作业类型，例如工作流作业和计划作业。 它不适用于标准作业，如使用 cmdlet 创建的作业 `Start-Job` 。 有关支持此参数的信息，请参阅作业类型的帮助主题。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -Force

指示此 cmdlet 继续等待处于 "挂起" 或 "已断开连接" 状态的作业。 默认情况下， `Wait-Job` 当作业处于以下状态之一时，将返回或结束等待：

- 已完成
- 已失败
- 已停止
- Suspended
- 已断开连接

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -Id

指定此 cmdlet 等待的作业的 Id 的数组。

ID 是一个整数，用于唯一标识当前会话中的作业。 它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。 你可以键入一个或多个 Id （以逗号分隔）。 若要查找作业的 ID，请键入 `Get-Job` 。

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

### -InstanceId

指定此 cmdlet 等待的作业的实例 Id 的数组。 默认值为所有作业。

实例 ID 是一个 GUID，用于在计算机上唯一标识作业。 若要查找作业的实例 ID，请使用 `Get-Job` 。

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

### -Job

指定此 cmdlet 要等待的作业。 输入一个包含作业对象的变量或可获取作业对象的命令。 你还可以使用管道运算符将作业对象发送到 `Wait-Job` cmdlet。 默认情况下， `Wait-Job` 将等待在当前会话中创建的所有作业。

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

### -Name

指定此 cmdlet 等待的作业的友好名称。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -State

指定作业状态。 此 cmdlet 仅等待处于指定状态的作业。 此参数的可接受值为：

- NotStarted
- 正在运行
- 已完成
- 已失败
- 已停止
- 已阻止
- Suspended
- 已断开连接
- 正在暂停
- 正在停止

有关作业状态的详细信息，请参阅 [JobState 枚举](/dotnet/api/system.management.automation.jobstate)。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

指定每个作业的最长等待时间（以秒为单位）。 默认值为-1，指示该 cmdlet 将等待直到作业完成。 提交命令时将开始计时 `Wait-Job` ，而不是 `Start-Job` 命令。

如果超过此时间，则等待结束，并继续执行，即使作业仍在运行也是如此。
此命令不会显示任何错误消息。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.RemotingJob

可以通过管道将作业对象传递给此 cmdlet。

## 输出

### System.Management.Automation.PSRemotingJob

此 cmdlet 将返回表示处于终止状态的作业的作业对象。 如果等待由于超过 **Timeout** 参数的值而结束，则 `Wait-Job` 不返回任何对象。

## 注释

默认情况下， `Wait-Job` 当作业处于以下状态之一时，将返回或结束等待：

- 已完成
- 已失败
- 已停止
- 已挂起
- 断开连接以 `Wait-Job` 继续等待挂起和断开连接的作业，请使用 **Force** 参数。

## 相关链接

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)
