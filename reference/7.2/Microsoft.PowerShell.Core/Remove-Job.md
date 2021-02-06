---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603817"
---
# Remove-Job

## 摘要
删除 PowerShell 后台作业。

## SYNTAX

### SessionIdParameterSet（默认值）

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-Job`Cmdlet 会删除由 `Start-Job` cmdlet 或 cmdlet （如 `Invoke-Command` 支持 **AsJob** 参数）启动的 PowerShell 后台作业。

您可以使用 `Remove-Job` 删除所有作业或删除所选作业。 作业由其 **名称**、 **ID**、 **实例 ID**、 **命令** 或 **状态** 标识。 或者，作业对象可以向下发送到 `Remove-Job` 。 如果没有参数或参数值，则无效 `Remove-Job` 。

由于 PowerShell 3.0， `Remove-Job` 可以删除自定义作业类型，例如计划作业和工作流作业。 例如， `Remove-Job` 删除计划作业、磁盘上计划作业的所有实例，以及所有触发的作业实例的结果。

如果尝试删除正在运行的作业，将 `Remove-Job` 失败。 使用 `Stop-Job` cmdlet 可停止正在运行的作业。 或者，使用 `Remove-Job` **Force** 参数删除正在运行的作业。

作业将保留在全局作业缓存中，直到删除后台作业或关闭 PowerShell 会话。

## 示例

### 示例1：使用作业名称删除作业

此示例使用变量和管道按名称删除作业。

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job` 使用 **Name** 参数来指定作业 **BatchJob**。 作业对象存储在 `$batch` 变量中。 中的对象 `$batch` 将向下发送到 `Remove-Job` 。

一种替代方法是使用 **作业** 参数，如 `Remove-Job -Job $batch` 。

### 示例2：删除会话中的所有作业

在此示例中，将删除当前 PowerShell 会话中的所有作业。

```powershell
Get-job | Remove-Job
```

`Get-Job` 获取当前 PowerShell 会话中的所有作业。 作业对象将向下发送到 `Remove-Job` 。

### 示例3：删除 NotStarted 作业

此示例将从当前 PowerShell 会话中删除尚未启动的所有作业。

```powershell
Remove-Job -State NotStarted
```

`Remove-Job` 使用 **State** 参数指定作业状态。

### 示例4：使用友好名称删除作业

此示例将从当前会话中删除具有以 * batch * * 结尾的友好名称的所有作业，包括正在运行的作业。

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job` 使用 **Name** 参数来指定作业名称模式。 此模式包含星号 (`*`) 通配符，以查找以 **批处理** 结尾的所有作业名称。 **Force** 参数删除运行的作业。

### 示例5：删除 Invoke-Command 创建的作业

此示例将使用 `Invoke-Command` 带有 **AsJob** 参数的远程计算机上删除已启动的作业。

由于该示例使用了 **AsJob** 参数，因此在本地计算机上创建了作业对象。
但该作业在远程计算机上运行。 因此，你可以使用本地命令来管理作业。

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command` 在 **Server01** 计算机上运行作业。 **AsJob** 参数将 **ScriptBlock** 作为后台作业运行。 作业对象存储在 `$job` 变量中。 `$job`变量对象将向下发送到 `Remove-Job` 。

### 示例6：删除由 Invoke-Command 和 Start-Job 创建的作业

此示例演示如何删除使用运行的启动的远程计算机上的作业 `Invoke-Command` `Start-Job` 。 在远程计算机上创建作业对象，并使用远程命令来管理该作业。 运行远程命令时需要持续连接 `Start-Job` 。

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession`创建与 **Server01** 计算机的 **PSSession**（持久连接）。 该连接保存在变量中 `$S` 。

`Invoke-Command` 连接到保存在中的会话 `$S` 。 **ScriptBlock** 使用 `Start-Job` 来启动远程作业。 作业运行 `Get-Process` 命令，并使用 **Name** 参数指定友好的作业名称 **MyJob**。

`Invoke-Command` 使用 `$S` 会话并运行 `Remove-Job` 。 **Name** 参数指定已删除名为 **MyJob** 的作业。

### 示例7：通过使用其实例 Id 删除作业

此示例根据作业的 **InstanceId** 删除作业。

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 启动一个后台作业，该作业对象保存在变量中 `$job` 。

中的对象 `$job` 将向下发送到 `Format-List` 。 **Property** 参数使用星号 (`*`) 来指定对象的所有属性都显示在列表中。

`Remove-Job` 使用 **InstanceId** 参数指定要删除的作业。

## PARAMETERS

### -Command

删除命令中包含指定的词的作业。 可以输入以逗号分隔的数组。

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在运行之前提示你进行确认 `Remove-Job` 。

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

### -Filter

删除满足在关联的哈希表中建立的所有条件的作业。 输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。

此参数仅适用于自定义作业类型，例如工作流作业和计划作业。 它不适用于标准后台作业，例如通过使用创建的作业 `Start-Job` 。

此参数是在 PowerShell 3.0 中引入的。

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

即使作业的状态为 **正在运行**，也会删除该作业。 如果未指定 **Force** 参数，则 `Remove-Job` 不会删除正在运行的作业。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

删除具有指定 **Id** 的后台作业。可以输入以逗号分隔的数组。 作业的 **Id** 是用于标识当前会话中的作业的唯一整数。

若要查找作业的 **Id**，请使用 `Get-Job` 不带参数的。

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

删除具有指定 **InstanceId** 的作业。 可以输入以逗号分隔的数组。 **InstanceId** 是用于标识作业的唯一 GUID。

若要查找作业的 **InstanceId**，请使用 `Get-Job` 。

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

指定要删除的作业。 请输入一个包含作业的变量，或一个可获取作业的命令。 可以输入以逗号分隔的数组。

可以将作业对象向下发送到 `Remove-Job` 。

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

仅删除具有指定友好名称的作业。 允许使用通配符。 可以输入以逗号分隔的数组。

作业的友好名称并不保证在 PowerShell 会话中是唯一的。 按名称删除文件时，请使用 **WhatIf** 和 **Confirm** 参数。

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

### -State

仅删除具有指定状态的作业。 若要删除状态为 " **正在运行**" 的作业，请使用 **Force** 参数。

接受的值：

- AtBreakpoint
- 已阻止
- 已完成
- 已断开连接
- Failed
- NotStarted
- 运行
- 已停止
- 正在停止
- 已挂起
- 正在暂停

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

显示运行时将发生 `Remove-Job` 的情况。 cmdlet 未运行。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.Job

可以将作业对象向下发送到 `Remove-Job` 。

## 输出

### 无

`Remove-Job` 不会生成任何输出。

## 注释

PowerShell 作业创建一个新进程。 作业完成后，进程将退出。 当 `Remove-Job` 运行时，作业的状态将被删除。

如果作业在完成之前停止并且其进程尚未退出，则会强行终止进程。

## 相关链接

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

