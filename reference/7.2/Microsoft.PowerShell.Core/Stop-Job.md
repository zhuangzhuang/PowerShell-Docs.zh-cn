---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 479c099d2d5daf1cc50c5c645be053ff4ae02bdc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595629"
---
# Stop-Job

## 摘要
停止 PowerShell 后台作业。

## SYNTAX

### SessionIdParameterSet（默认值）

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Stop-Job`Cmdlet 可停止正在进行的 PowerShell 后台作业。 您可以使用此 cmdlet 停止所有作业，或者基于作业的名称、ID、实例 ID 或状态停止所选作业，或者通过将作业对象传递到来停止这些作业 `Stop-Job` 。

你可以使用 `Stop-Job` 来停止后台作业，如使用 `Start-Job` cmdlet 或任何 Cmdlet 的 **AsJob** 参数启动的作业。 停止后台作业时，PowerShell 将完成该作业队列中挂起的所有任务，然后结束该作业。 提交此命令后，将不会有新任务添加到队列。

此 cmdlet 不删除后台作业。 若要删除作业，请使用 `Remove-Job` cmdlet。

从 Windows PowerShell 3.0 开始， `Stop-Job` 还将停止自定义作业类型，例如工作流作业和计划作业的实例。 若要启用 `Stop-Job` 以停止具有自定义作业类型的作业，请在运行命令之前将支持自定义作业类型的模块导入到会话中，方法 `Stop-Job` 是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。 有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。

## 示例

### 示例1：使用 Invoke-Command 停止远程计算机上的作业

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

此示例演示如何使用 `Stop-Job` cmdlet 停止在远程计算机上运行的作业。

由于该作业是通过使用 `Invoke-Command` cmdlet 远程运行命令来启动的 `Start-Job` ，因此该作业对象存储在远程计算机上。 您必须使用另一个 `Invoke-Command` 命令来 `Stop-Job` 远程运行命令。 有关远程后台作业的详细信息，请参阅 about_Remote_Jobs。

第一个命令在 Server01 计算机上创建 (**PSSession**) 的 PowerShell 会话，然后将该会话对象存储在 `$s` 变量中。 该命令使用某个域管理员的凭据。

第二个命令使用 `Invoke-Command` cmdlet `Start-Job` 在会话中运行命令。 作业中的此命令将获取系统事件日志中的所有事件。 生成的作业对象存储在变量中 `$j` 。

第三个命令停止作业。 它使用 `Invoke-Command` cmdlet 在 `Stop-Job` Server01 上的 **PSSession** 中运行命令。 由于作业对象存储在 `$j` 本地计算机上的变量中，因此该命令将使用 Using 作用域修饰符来标识 `$j` 为局部变量。
有关 Using 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](about/about_Remote_Variables.md)。

命令完成后，作业将停止，中的 **PSSession** 可供 `$s` 使用。

### 示例2：停止后台作业

```powershell
Stop-Job -Name "Job1"
```

此命令停止 Job1 后台作业。

### 示例3：停止多个后台作业

```powershell
Stop-Job -Id 1, 3, 4
```

此命令停止三个作业。
它将通过 ID 来标识作业。

### 示例4：停止所有后台作业

```powershell
Get-Job | Stop-Job
```

此命令停止当前会话中的所有后台作业。

### 示例5：停止所有阻止的后台作业

```powershell
Stop-Job -State Blocked
```

此命令停止阻止的所有作业。

### 示例6：使用实例 ID 停止作业

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

这些命令显示了如何根据作业的实例 ID 来停止作业。

第一个命令使用 `Get-Job` cmdlet 来获取当前会话中的作业。 该命令使用管道运算符 (`|`) 将作业发送到 `Format-Table` 命令，该命令显示每个作业的指定属性的表。 该表包括每个作业的实例 ID。 它使用计算属性来显示作业状态。

第二个命令使用 `Stop-Job` 带有 **InstanceID** 参数的命令停止选定的作业。

### 示例7：停止远程计算机上的作业

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

此示例演示如何使用 `Stop-Job` cmdlet 停止在远程计算机上运行的作业。

由于作业是使用 cmdlet 的 **AsJob** 参数启动的，因此 `Invoke-Command` 作业对象位于本地计算机上，即使作业运行在远程计算机上也是如此。 因此，你可以使用本地 `Stop-Job` 命令来停止作业。

第一个命令使用 `Invoke-Command` cmdlet 在 Server01 计算机上启动后台作业。 该命令使用 **AsJob** 参数将远程命令作为后台作业运行。

此命令返回一个作业对象，该对象是 cmdlet 返回的相同作业对象 `Start-Job` 。
该命令将作业对象保存在 `$j` 变量中。

第二个命令使用管道运算符将变量中的作业发送 `$j` 到 `Stop-Job` 。 该命令使用 **PassThru** 参数来指示 `Stop-Job` 返回作业对象。 作业对象显示确认作业的状态为 "已停止"。

有关远程后台作业的详细信息，请参阅 about_Remote_Jobs。

## PARAMETERS

### -Filter

指定条件的哈希表。 此 cmdlet 将停止满足所有条件的作业。
输入一个哈希表，其中的键为作业属性，其中的值为作业属性值。

此参数仅适用于自定义作业类型，例如工作流作业和计划作业。 它不适用于标准后台作业，如使用 cmdlet 创建的作业 `Start-Job` 。 有关支持此参数的信息，请参阅作业类型的帮助主题。

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

### -Id

指定此 cmdlet 停止的作业的 Id。 默认值为当前会话中的所有作业。

ID 是一个整数，用于唯一标识当前会话中的作业。 它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。 你可以键入一个或多个 Id （以逗号分隔）。 若要查找作业的 ID，请键入 `Get-Job` 。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定此 cmdlet 停止的作业的实例 Id。 默认值为所有作业。

实例 ID 是一个 GUID，用于在计算机上唯一标识作业。 若要查找作业的实例 ID，请使用 `Get-Job` 。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

指定此 cmdlet 停止的作业。 请输入一个包含作业的变量，或一个可获取作业的命令。 你还可以使用管道运算符将作业提交到 `Stop-Job` cmdlet。 默认情况下， `Stop-Job` 删除在当前会话中启动的所有作业。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

指定此 cmdlet 停止的作业的友好名称。 以逗号分隔的列表形式输入作业名称，或使用通配符 (*) 来输入作业名称模式。 默认情况下， `Stop-Job` 停止在当前会话中创建的所有作业。

由于不能保证友好名称是唯一的，因此在按名称停止作业时，请使用 **WhatIf** 和 **Confirm** 参数。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

返回一个代表你所处理的项目的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### -State

指定作业状态。 此 cmdlet 仅停止处于指定状态的作业。 此参数的可接受值为：

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
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

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

### System.Management.Automation.RemotingJob

可以通过管道将作业对象传递给此 cmdlet。

## 输出

### PSRemotingJob （无）

如果指定 **PassThru** 参数，则此 cmdlet 将返回一个作业对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
