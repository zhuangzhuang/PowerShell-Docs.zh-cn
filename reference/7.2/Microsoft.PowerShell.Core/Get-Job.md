---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 7df3375d547b696d67c44462142d592e6047ac63
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603386"
---
# Get-Job

## 摘要
获取当前会话中正在运行的 PowerShell 后台作业。

## SYNTAX

### SessionIdParameterSet（默认值）

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

`Get-Job`Cmdlet 可获取表示在当前会话中启动的后台作业的对象。 你可以使用 `Get-Job` 来获取通过使用 `Start-Job` cmdlet 或通过使用任何 Cmdlet 的 **AsJob** 参数启动的作业。

如果没有参数，则 `Get-Job` 命令将获取当前会话中的所有作业。 您可以使用的参数 `Get-Job` 来获取特定作业。

返回的作业对象 `Get-Job` 包含有关该作业的有用信息，但不包含作业结果。 若要获取结果，请使用 `Receive-Job` cmdlet。

Windows PowerShell 后台作业是在后台运行的命令，不与当前会话交互。 通常，可以使用后台作业来运行需要很长时间才能完成的复杂命令。 有关 Windows PowerShell 中的后台作业的详细信息，请参阅 [about_Jobs](./about/about_Jobs.md)。

从 Windows PowerShell 3.0 开始， `Get-Job` cmdlet 还获取自定义作业类型，例如工作流作业和计划作业的实例。 若要查找作业的作业类型，请使用该作业的 **PSJobTypeName** 属性。

若要允许 `Get-Job` 获取自定义作业类型，请在运行命令之前将支持自定义作业类型的模块导入到会话中 `Get-Job` ，方法是使用 `Import-Module` cmdlet 或通过使用或在模块中获取 cmdlet。 有关特定的自定义作业类型的信息，请参阅自定义作业类型功能的文档。

## 示例

### 示例1：获取当前会话中启动的所有后台作业

此命令将获取在当前会话中启动的所有后台作业。 它不包括在其他会话中创建的作业，即使这些作业是在本地计算机上运行的也是如此。

```
PS C:\> Get-Job
```

### 示例2：使用实例 ID 停止作业

这些命令演示如何获取作业的实例 ID，然后用它来停止作业。 与非唯一的作业名称不同，实例 ID 是唯一的。

第一个命令使用 `Get-Job` cmdlet 来获取作业。 它使用 **Name** 参数来标识作业。 此命令存储 `Get-Job` 在变量中返回的作业对象 `$j` 。 在此示例中，只有一个作业具有指定的名称。 第二个命令获取变量中的对象的 **InstanceId** 属性 `$j` ，并将其存储在 `$ID` 变量中。 第三个命令显示变量的值 `$ID` 。 第四个命令使用 `Stop-Job` cmdlet 来停止作业。
它使用 **InstanceId** 参数来标识作业，使用 `$ID` 变量来表示作业的实例 ID。

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### 示例3：获取包含特定命令的作业

此命令获取系统中包含命令的作业 `Get-Process` 。 命令使用的 **命令** 参数 `Get-Job` 来限制检索的作业数。 该命令使用通配符 (`*`) 来获取 `Get-Process` 在命令字符串中的任意位置包含一个命令的作业。

```
PS C:\> Get-Job -Command "*get-process*"
```

### 示例4：使用管道获取包含特定命令的作业

与上一示例中的命令一样，此命令获取系统中包含命令的作业 `Get-Process` 。 该命令使用管道运算符 (`|`) 将字符串（在引号中）发送到 `Get-Job` cmdlet。 它等效于之前的命令。

```
PS C:\> "*get-process*" | Get-Job
```

### 示例5：获取尚未启动的作业

此命令只获取那些已创建的但尚未启动的作业。 这包括计划要在将来运行的作业和尚未计划的作业。

```
PS C:\> Get-Job -State NotStarted
```

### 示例6：获取未分配名称的作业

此命令获取作业名称以 job 开头的所有作业。 由于 `job<number>` 是作业的默认名称，因此此命令将获取没有显式分配的名称的所有作业。

```
PS C:\> Get-Job -Name Job*
```

### 示例7：在命令中使用作业对象来表示作业

此示例演示如何使用 `Get-Job` 来获取作业对象，并演示如何在命令中使用作业对象来表示作业。

第一个命令使用 `Start-Job` cmdlet 来启动在 `Get-Process` 本地计算机上运行命令的后台作业。 该命令使用的 **Name** 参数 `Start-Job` 为作业指定一个友好名称。 第二个命令使用 `Get-Job` 来获取作业。 它使用的 **Name** 参数 `Get-Job` 来标识作业。 该命令将生成的作业对象保存在 `$j` 变量中。 第三个命令显示变量中的作业对象的值 `$j` 。 " **状态** " 属性的值显示作业已完成。 **HasMoreData** 属性的值显示尚未检索的作业中存在可检索的结果。 第四个命令使用 `Receive-Job` cmdlet 来获取作业的结果。 它使用变量中的作业对象 `$j` 来表示作业。 你还可以使用管道运算符将作业对象发送到 `Receive-Job` 。

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### 示例8：获取所有作业，包括其他方法启动的作业

此示例演示该 `Get-Job` cmdlet 可获取在当前会话中启动的所有作业，即使这些作业是使用不同的方法启动的。

第一个命令使用 `Start-Job` cmdlet 在本地计算机上启动作业。 第二个命令使用 cmdlet 的 **AsJob** 参数 `Invoke-Command` 在 S1 计算机上启动作业。 虽然作业中的命令在远程计算机上运行，但该作业对象是在本地计算机上创建的，所以应使用本地命令来管理该作业。 第三个命令使用 `Invoke-Command` cmdlet `Start-Job` 在 S2 计算机上运行命令。 通过使用此方法，将在远程计算机上创建作业对象，因此你可以使用远程命令来管理该作业。 第四个命令使用 `Get-Job` 来获取存储在本地计算机上的作业。 Windows PowerShell 3.0 中引入的作业的 **PSJobTypeName** 属性显示，使用 cmdlet 启动的本地作业 `Start-Job` 是后台作业，使用 cmdlet 在远程会话中启动的作业 `Invoke-Command` 是远程作业。 第五个命令使用 `Invoke-Command` `Get-Job` 在 S2 计算机上运行命令。示例输出显示了该命令的结果 `Get-Job` 。 在 S2 计算机上，该作业看起来像是本地作业。 计算机名称为 localhost，作业类型为后台作业。有关如何在远程计算机上运行后台作业的详细信息，请参阅 [about_Remote_Jobs](./about/about_Remote_Jobs.md)。

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### 示例9：调查失败的作业

此命令演示如何使用返回的作业对象 `Get-Job` 来调查作业失败的原因。
此命令还显示了如何获取每个作业的子作业。

第一个命令使用 `Start-Job` cmdlet 在本地计算机上启动作业。 返回的作业对象 `Start-Job` 显示作业失败。 **State** 属性的值失败。

第二个命令使用 `Get-Job` cmdlet 来获取作业。 该命令使用点法获取对象的 **JobStateInfo** 属性的值。 它使用管道运算符将 **JobStateInfo** 属性中的对象发送给 `Format-List` cmdlet，该 cmdlet 将对象的所有属性的格式设置为 `*` 列表中的)  (。此命令的结果 `Format-List` 显示作业的 " **原因** " 属性值为空。

第三个命令调查更多。 它使用 `Get-Job` 命令获取作业，然后使用管道运算符将整个作业对象发送给 `Format-List` cmdlet，该 cmdlet 将在列表中显示作业的所有属性。作业对象中所有属性的显示显示作业包含一个名为 Job2 的子作业。

第四个命令使用 `Get-Job` 获取表示 Job2 子作业的作业对象。 命令实际在该作业中运行。 它使用点方法获取 **JobStateInfo** 属性的 **原因** 属性。结果显示作业由于拒绝访问错误而失败。 在这种情况下，用户会忘记使用 Windows PowerShell 的 "以管理员身份运行" 选项。因为后台作业使用 Windows PowerShell 的远程处理功能，所以必须将计算机配置为进行远程处理以运行作业，即使该作业在本地计算机上运行也是如此。有关 Windows PowerShell 中的远程处理要求的信息，请参阅 [about_Remote_Requirements](./about/about_Remote_Requirements.md)。 有关疑难解答提示，请参阅 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md)。

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### 示例10：获取筛选的结果

此示例显示如何使用 **Filter** 参数获取工作流作业。 在 Windows PowerShell 3.0 中引入的 **Filter** 参数仅在自定义作业类型（例如工作流作业和计划作业）上有效。

第一个命令使用 **workflow** 关键字创建 WFProcess 工作流。 第二个命令使用 WFProcess 工作流的 **AsJob** 参数将工作流作为后台作业运行。 该命令使用工作流的 **JobName** 参数为作业指定名称，并使用工作流的 **PSPrivateMetadata** 参数指定自定义 ID。 第三个命令使用的 **筛选器** 参数 `Get-Job` 通过在 **PSPrivateMetadata** 参数中指定的自定义 ID 获取作业。

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### 示例11：获取有关子作业的信息

此示例演示使用 cmdlet 的 **IncludeChildJob** 和 **ChildJobState** 参数的效果 `Get-Job` 。

第一个命令获取当前会话中的作业。 输出包括一个后台作业、一个远程作业和一个计划作业的几个实例。 远程作业 Job4 显示为已失败。
第二个命令使用的 **IncludeChildJob** 参数 `Get-Job` 。 输出添加具有子作业的所有作业的子作业。在这种情况下，修改后的输出显示只有 Job4 的 Job5 子作业失败。 第三个命令使用值为 "Failed" 的 **ChildJobState** 参数。输出中包括所有父作业和失败的子作业。 第五个命令使用作业的 **JobStateInfo** 属性及其 **Reason** 属性来发现 Job5 失败的原因。

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

有关详细信息，请参阅 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) 帮助主题。

## PARAMETERS

### -After

获取在指定日期和时间后结束完成的作业。 输入一个 **DateTime** 对象，如 cmdlet 返回的一个 `Get-Date` 或可转换为 **DateTime** 对象的字符串（例如或） `Dec 1, 2012 2:00 AM` `11/06` 。

此参数仅适用于具有 **EndTime** 属性的自定义作业类型（例如工作流作业和计划作业）。 它不适用于标准后台作业，如使用 cmdlet 创建的作业 `Start-Job` 。 有关支持此参数的信息，请参阅作业类型的帮助主题。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Before

获取在指定日期和时间前结束前完成的作业。 输入 **DateTime** 对象。

此参数仅适用于具有 **EndTime** 属性的自定义作业类型（例如工作流作业和计划作业）。 它不适用于标准后台作业，如使用 cmdlet 创建的作业 `Start-Job` 。 有关支持此参数的信息，请参阅作业类型的帮助主题。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

只获取具有指定状态的子作业。 此参数的可接受值为：

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

默认情况下，不 `Get-Job` 获取子作业。 使用 **IncludeChildJob** 参数 `Get-Job` 获取所有子作业。 如果使用 **ChildJobState** 参数，则 **IncludeChildJob** 参数将不起作用。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

将命令数组指定为字符串。 此 cmdlet 将获取包含指定命令的作业。 默认值为所有作业。 您可以使用通配符来指定命令模式。

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

指定条件的哈希表。 此 cmdlet 将获取满足所有条件的作业。
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

### -HasMoreData

指示此 cmdlet 是否仅获取具有指定的 **HasMoreData** 属性值的作业。
**HasMoreData** 属性指示当前会话中是否已接收所有作业结果。 若要获取具有更多结果的作业，请将值指定为 `$True` 。 若要获取没有更多结果的作业，请将值指定为 `$False` 。

若要获取作业结果，请使用 `Receive-Job` cmdlet。

当使用 cmdlet 时 `Receive-Job` ，它会将其返回的结果从其内存中的特定于会话的存储中删除。 在当前会话中返回作业的所有结果后，它会将作业的 **HasMoreData** 属性的值设置为 `$False`) ，以指示它在当前会话中没有更多的作业结果。 使用 **Keep** 参数 `Receive-Job` 禁止 `Receive-Job` 删除结果并更改 **HasMoreData** 属性的值。
要了解详情，请键入 `Get-Help Receive-Job`。

**HasMoreData** 属性特定于当前会话。 如果自定义作业类型的结果保存在会话之外（例如计划作业类型，这会将作业结果保存在磁盘上），则可以使用 `Receive-Job` 其他会话中的 cmdlet 再次获取作业结果，即使 **HasMoreData** 的值为 `$False` 。 有关详细信息，请参阅自定义作业类型的帮助主题。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 cmdlet 获取的作业 Id 的数组。

ID 是一个整数，用于唯一标识当前会话中的作业。 它比实例 ID 更容易记住和键入，但它仅在当前会话中是唯一的。 你可以键入一个或多个 Id （以逗号分隔）。 若要查找作业的 ID，请键入（ `Get-Job` 不带参数）。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

指示除了父作业，此 cmdlet 还将返回子作业。

此参数对于调查工作流作业（其 `Get-Job` 返回容器父作业和作业失败）特别有用，因为失败的原因保存在子作业的属性中。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

指定此 cmdlet 获取的作业的实例 Id 的数组。 默认值为所有作业。

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

### -Name

指定此 cmdlet 获取的实例的友好名称的数组。 输入作业名称，或使用通配符输入作业名称模式。 默认情况下， `Get-Job` 获取当前会话中的所有作业。

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

### -Newest

指定要获取的作业数。 此 cmdlet 将获取最近结束的作业。

**Newest** 参数不会按结束时间的顺序对输出进行排序或返回最新的作业。 若要对输出进行排序，请使用 `Sort-Object` cmdlet。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State

指定作业状态。 此 cmdlet 仅获取处于指定状态的作业。 此参数的可接受值为：

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

默认情况下， `Get-Job` 获取当前会话中的所有作业。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.RemotingJob

此 cmdlet 将返回表示会话中的作业的对象。

## 注释

作业的 **PSJobTypeName** 属性指示作业的作业类型。 该属性值由作业类型的作者确定。 以下列表显示了常见作业类型。

- **BackgroundJob**。 使用启动的本地作业 `Start-Job` 。
- **RemoteJob**。 使用 cmdlet 的 **AsJob** 参数在 **PSSession** 中启动作业 `Invoke-Command` 。
- **PSWorkflowJob**。 通过使用工作流的 **AsJob** 通用参数启动的作业。

## 相关链接

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)
