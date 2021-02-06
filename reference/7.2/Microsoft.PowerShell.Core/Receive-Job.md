---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598898"
---
# Receive-Job

## 摘要
获取当前会话中 PowerShell 后台作业的结果。

## SYNTAX

### Location（默认值）

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### 计算机名

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### 会话

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

该 `Receive-Job` cmdlet 将获取 PowerShell 后台作业的结果，如使用 `Start-Job` cmdlet 或任何 Cmdlet 的 **AsJob** 参数启动的作业。
你可以获取所有作业的结果，或通过作业的名称、ID、实例 ID、计算机名称、位置或会话或者通过提交作业对象来标识作业。

启动 PowerShell 后台作业时，该作业将启动，但是结果不会立即显示。 而该命令将返回一个表示该后台作业的对象。
该作业对象包含有关该作业的有用信息，但是不包含结果。
此方法允许你在作业运行的同时继续在会话中工作。
有关 PowerShell 中的后台作业的详细信息，请参阅 [about_Jobs](./About/about_Jobs.md)。

该 `Receive-Job` cmdlet 将获取 `Receive-Job` 提交命令后生成的结果。
如果尚未完成结果，你可以运行其他 `Receive-Job` 命令来获取剩余结果。

默认情况下，作业结果将在你收到它们时从系统中删除，但是你可以使用 **Keep** 参数来保存这些结果，以便可以再次收到它们。
若要删除作业结果，请在 `Receive-Job` 不使用 **Keep** 参数的情况下再次运行该命令，关闭会话，或使用 `Remove-Job` cmdlet 从会话中删除该作业。

从 Windows PowerShell 3.0 开始， `Receive-Job` 还获取自定义作业类型的结果，如工作流作业和计划作业的实例。
若要使 `Receive-Job` 能够获取自定义作业类型的结果，请在运行命令之前将支持自定义作业类型的模块导入到会话中 `Receive-Job` ，方法是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。
有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。

## 示例

### 示例1：获取特定作业的结果

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

这些命令使用的 **作业** 参数 `Receive-Job` 来获取特定作业的结果。

第一个命令使用启动一个作业 `Start-Job` ，并将该作业对象存储在 `$job` 变量中。

第二个命令使用 `Receive-Job` cmdlet 来获取作业的结果。
它使用 **Job** 参数来指定作业。

### 示例2：使用 Keep 参数

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

此示例在变量中存储作业 `$job` ，并通过管道将作业传递给 `Receive-Job` cmdlet。 `-Keep`参数还用于允许在第一次查看之后再次检索聚合流数据。

### 示例3：获取多个后台作业的结果

使用的 **AsJob** 参数 `Invoke-Command` 启动作业时，将在本地计算机上创建作业对象，即使该作业在远程计算机上运行也是如此。
因此，你可以使用本地命令来管理作业。

此外，当你使用 **AsJob** 时，PowerShell 将返回一个作业对象，其中包含已启动的每个作业的子作业。 在此示例中，该作业对象包含三个子作业，分别对应于每台远程计算机上的每个作业。

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### 示例4：获取多台远程计算机上的后台作业的结果

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

此示例显示了如何获取在三台远程计算机上运行的后台作业的结果。
与前面的示例不同，使用 `Invoke-Command` 运行 `Start-Job` 命令实际上是在三台计算机上的每一台计算机上启动了三个独立的作业。 因此，该命令返回了三个作业对象，以表示在三台不同的计算机上本地运行的三个作业。

> [!NOTE]
> 在最后一个命令中，由于 `$j` 是局部变量，因此脚本块使用 **Using** 作用域修饰符来标识 `$j` 变量。 有关 **Using** 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](./About/about_Remote_Variables.md)。

### 示例5：访问子作业

`-Keep`参数保留作业的聚合流的状态，以便可以再次查看。 如果没有此参数，则当接收到作业时，所有聚合流数据都将被清除。 有关详细信息，请参阅 [about_Job_Details](About/about_Job_Details.md#child-jobs)

> [!NOTE]
> 聚合流包括所有子作业的流。 你仍可以通过作业对象和子作业对象访问单个数据流。

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETERS

### -AutoRemoveJob

指示此 cmdlet 在返回作业结果后删除该作业。
如果作业有更多结果，则仍将删除该作业，但会 `Receive-Job` 显示一条消息。

此参数仅适用于自定义作业类型。
它专门用于保存会话之外的作业或类型的作业类型的实例，例如计划作业的实例。

不能在缺少 **Wait** 参数的情况下使用此参数。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -ComputerName

指定计算机的名称数组。

此参数从存储在本地计算机的作业结果中进行选择。
它不会获取在远程计算机上运行的作业的数据。
若要获取存储在远程计算机上的作业结果，请使用 `Invoke-Command` cmdlet 远程运行 `Receive-Job` 命令。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

指示当作业处于 **挂起** 或 **断开连接** 状态时，此 cmdlet 将继续等待。 默认情况下，  `Receive-Job` 当作业处于以下状态之一时，的 wait 参数将返回或终止等待：

- 已完成
- 已失败
- 已停止
- 已挂起
- 已断开连接。

仅当命令中也使用 **Wait** 参数时，**Force** 参数才有效。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -Id

指定一个 ID 数组。
此 cmdlet 将获取具有指定 Id 的作业的结果。

ID 是一个整数，用于唯一标识当前会话中的作业。
它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。 你可以键入一个或多个 Id （以逗号分隔）。
若要查找作业的 ID，请使用 `Get-Job` 。

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

指定实例 ID 的数组。
此 cmdlet 将获取具有指定实例 Id 的作业的结果。

实例 ID 是一个 GUID，用于在计算机上唯一标识作业。
若要查找作业的实例 ID，请使用 `Get-Job` cmdlet。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

指定要检索其结果的作业。

请输入一个包含作业的变量，或一个可获取作业的命令。
还可以通过管道将作业对象传递给 `Receive-Job` 。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Keep

指示此 cmdlet 将聚合流数据保存在系统中，即使在收到这些数据后也是如此。 默认情况下，在使用查看后将清除聚合流数据 `Receive-Job` 。

关闭会话，或删除具有 cmdlet 的作业 `Remove-Job` 也会删除聚合的流数据。

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

### -Location

指定位置的数组。
此 cmdlet 仅获取指定位置中的作业的结果。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定一个友好名称数组。
此 cmdlet 将获取具有指定名称的作业的结果。
支持使用通配符。

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

### -NoRecurse

指示此 cmdlet 仅获取指定作业中的结果。
默认情况下， `Receive-Job` 还会获取指定作业的所有子作业的结果。

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

### -Session

指定会话的数组。
此 cmdlet 将获取 (**PSSession**) 在指定的 PowerShell 会话中运行的作业的结果。
输入包含 **pssession** 的变量或获取 **pssession** 的命令（如 `Get-PSSession` 命令）。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait

指示此 cmdlet 禁止显示命令提示符，直到收到所有作业结果。
默认情况下，会 `Receive-Job` 立即返回可用结果。

默认情况下，**Wait** 参数将等待作业处于以下状态之一：

- 已完成
- 已失败
- 已停止
- 已挂起
- 已断开连接。

若要指示 **wait** 参数继续等待作业状态为 "已挂起" 还是 "已断开连接"，请将 **Force** 参数与 **Wait** 参数一起使用。

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

### -WriteEvents

指示此 cmdlet 在等待作业完成时报告作业状态的更改。

仅当在命令中使用 **Wait** 参数并且省略 **Keep** 参数时，此参数才有效。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -WriteJobInResults

指示此 cmdlet 返回后跟结果的作业对象。

仅当在命令中使用 **Wait** 参数并且省略 **Keep** 参数时，此参数才有效。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。

## 输入

### System.Management.Automation.Job

可以通过管道将作业对象传递给此 cmdlet。

## 输出

### PSObject

此 cmdlet 将返回作业中命令的结果。

## 注释

## 相关链接

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

