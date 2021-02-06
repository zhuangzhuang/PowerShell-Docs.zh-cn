---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 4aed8db557b2d623aba4cd7218524af9957674c9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596414"
---
# Get-Counter

## 摘要
从本地和远程计算机获取性能计数器数据。

## SYNTAX

### GetCounterSet（默认值）

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Counter`Cmdlet 直接从 Windows 操作系统系列中的 "性能监视" 检测获取性能计数器数据。 `Get-Counter` 从本地计算机或远程计算机获取性能数据。

您可以使用 `Get-Counter` 参数指定一台或多台计算机，列出性能计数器集及其包含的实例，设置采样间隔，并指定最大样本数。 如果没有参数， `Get-Counter` 则获取一组系统计数器的性能计数器数据。

许多计数器集受 (ACL) 的访问控制列表保护。 若要查看所有计数器集，请以 "以 **管理员身份运行** " 选项打开 PowerShell。

此 cmdlet 已在 PowerShell 7 中引入。

## 示例

### 示例1：获取计数器集列表

此示例将获取本地计算机的计数器集列表。

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter` 使用带有星号 () 的 **ListSet** 参数 `*` 来获取计数器集列表。
`.` **MachineName** 列中)  (点表示本地计算机。

### 示例2：指定 SampleInterval 和 MaxSamples

此示例将获取本地计算机上的所有处理器的计数器数据。 数据将以两秒为间隔收集，直到有三个示例。

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter` 使用 **counter** 参数来指定计数器路径 `\Processor(_Total)\% Processor Time` 。 **SampleInterval** 参数设置一个2秒的间隔以检查计数器。 **MaxSamples** 确定三是检查计数器的最大次数。

### 示例3：获取计数器的连续示例

此示例每秒获取计数器的连续样本数。 若要停止该命令，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。 若要指定样本之间的更长时间间隔，请使用 **SampleInterval** 参数。

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter` 使用 **counter** 参数来指定 `\Processor\% Processor Time` 计数器。
**连续** 参数指定每秒获取样本，直到命令通过 <kbd>CTRL</kbd> + <kbd>C</kbd>停止。

### 示例4：计数器集的按字母顺序排列的列表

此示例使用管道获取计数器列表集，然后按字母顺序对列表进行排序。

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

`Get-Counter` 使用带有星号 () 的 **ListSet** 参数 `*` 获取完整的计数器集列表。 **CounterSet** 对象沿管道向下发送。 `Sort-Object` 使用 **Property** 参数来指定按 **CounterSetName** 对对象进行排序。 对象将向下发送到 `Format-Table` 。 **AutoSize** 参数调整列宽以尽可能减少截断。

`.` **MachineName** 列中)  (点表示本地计算机。

### 示例5：运行后台作业以获取计数器数据

在此示例中，在 `Start-Job` `Get-Counter` 本地计算机上将命令作为后台作业运行。
若要查看作业的性能计数器输出，请使用 `Receive-Job` cmdlet。

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job` 使用 **ScriptBlock** 参数运行 `Get-Counter` 命令。 `Get-Counter` 使用 **counter** 参数来指定计数器路径 `\LogicalDisk(_Total)\% Free Space` 。 **MaxSamples** 参数指定获取计数器的1000示例。

### 示例6：从多台计算机获取计数器数据

此示例使用变量从两台计算机获取性能计数器数据。

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

`$DiskReads`变量存储 `\LogicalDisk(C:)\Disk Reads/sec` 计数器路径。 将 `$DiskReads` 变量向下发送到 `Get-Counter` 。 **计数器** 是第一个位置参数，接受存储在中的路径 `$DiskReads` 。 **ComputerName** 指定两台计算机， **MaxSamples** 指定从每台计算机获取10个样本。

### 示例7：从多个随机计算机获取计数器的实例值

此示例获取企业中的50随机远程计算机上的性能计数器的值。 **ComputerName** 参数使用存储在变量中的随机计算机名称。 若要更新变量中的计算机名，请重新创建变量。

**ComputerName** 参数中服务器名称的替代方法是使用文本文件。 例如：

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

计数器路径包含 `*` 实例名称中的星号 () ，以获取每台远程计算机的处理器的数据。

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

`Get-Random`Cmdlet 使用 `Get-Content` 从文件中选择50随机计算机名称 `Servers.txt` 。 远程计算机的名称存储在变量中 `$Servers` 。 `\Processor(*)\% Processor Time`计数器的路径存储在 `$Counter` 变量中。 `Get-Counter` 使用 **Counter** 参数来指定变量中的计数器 `$Counter` 。 **ComputerName** 参数指定变量中的计算机名称 `$Servers` 。

### 示例8：使用 Path 属性获取格式化的路径名称

此示例使用计数器集的 **path** 属性来查找性能计数器的格式化路径名称。

管道与 cmdlet 一起用于 `Where-Object` 查找路径名称的子集。 若要查找计数器，请设置计数器路径的完整列表， (`|`) 和命令中删除管道 `Where-Object` 。

`$_`是管道中的当前对象的自动变量。
有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter` 使用 **ListSet** 参数来指定 **内存** 计数器集。 命令括在括号中，以便 **Paths** 属性以字符串的形式返回每个路径。 对象将向下发送到 `Where-Object` 。 `Where-Object` 使用变量 `$_` 来处理每个对象，并使用 `-like` 运算符查找该字符串的匹配项 `*Cache*` 。 星号 (`*`) 是任何字符的通配符。

### 示例9：使用 PathsWithInstances 属性获取格式化的路径名称

此示例获取包含 **PhysicalDisk** 性能计数器的实例的格式化路径名称。

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter` 使用 **ListSet** 参数来指定 **PhysicalDisk** 计数器集。 命令括在括号中，以便 **PathsWithInstances** 属性将每个路径实例作为字符串返回。

### 示例10：获取计数器集中每个计数器的单个值

在此示例中，将为本地计算机的 **内存** 计数器集中的每个性能计数器返回单个值。

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter` 使用 **ListSet** 参数来指定 **内存** 计数器集。 命令括在括号中，以便 **Paths** 属性以字符串的形式返回每个路径。 路径存储在 `$MemCounters` 变量中。 `Get-Counter` 使用 **counter** 参数来指定变量中的计数器路径 `$MemCounters` 。

### 示例11：显示对象的属性值

**PerformanceCounterSample** 对象中的属性值表示每个数据样本。 在此示例中，我们使用 **CounterSamples** 对象的属性来检查、选择、排序和分组数据。

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

计数器路径存储在 `$Counter` 变量中。 `Get-Counter` 获取计数器值的一个样本，并将结果存储在 `$Data` 变量中。 `$Data`变量使用 **CounterSamples** 属性获取该对象的属性。 将对象向下发送到 `Format-List` 。 **Property** 参数使用) 通配符 (星号 `*` 来选择所有属性。

### 示例12：性能计数器数组值

在此示例中，变量存储每个性能计数器。 **CounterSamples** 属性是可显示特定计数器值的数组。

若要显示每个计数器示例，请使用 `$Counter.CounterSamples` 。

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter` 使用 **counter** 参数来指定计数器 `\Processor(*)\% Processor Time` 。 值存储在 `$Counter` 变量中。
`$Counter.CounterSamples[0]` 显示第一个计数器值的数组值。

### 示例13：比较性能计数器值

此示例查找本地计算机上每个处理器使用的处理器时间量。 **CounterSamples** 属性用于将计数器数据与指定值进行比较。

若要显示每个计数器示例，请使用 `$Counter.CounterSamples` 。

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter` 使用 **counter** 参数来指定计数器 `\Processor(*)\% Processor Time` 。 值存储在 `$Counter` 变量中。 存储在中的对象 `$Counter.CounterSamples` 会沿管道向下发送。 `Where-Object` 使用脚本块将每个对象的值与指定的值20进行比较。 `$_.CookedValue`是管道中的当前对象的变量。 显示 **CookedValue** 小于20的计数器。

### 示例14：对性能计数器数据进行排序

此示例演示如何对性能计数器数据进行排序。 该示例在示例中查找正在使用处理器时间最多的计算机上的进程。

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter` 使用 **counter** 参数为 `\Process(*)\% Processor Time` 本地计算机上的所有进程指定计数器。 结果存储在 `$Procs` 变量中。 `$Procs`带有 **CounterSamples** 属性的变量将 **PerformanceCounterSample** 对象向下发送管道。 `Sort-Object` 使用 **Property** 参数按 **CookedValue** 按 **降序** 对对象进行排序。 `Format-Table` 使用 **Property** 参数来选择输出的列。 **AutoSize** 参数调整列宽以尽可能减少截断。

## PARAMETERS

### -ComputerName

指定一个计算机名称或以逗号分隔的 **远程** 计算机名称的数组。 使用 NetBIOS 名称、IP 地址或计算机的完全限定的域名。

若要从 **本地** 计算机获取性能计数器数据，请排除 **ComputerName** 参数。
对于包含 **MachineName** 列的输出（如 **ListSet** ），) 点 (`.` 表示本地计算机。

`Get-Counter` 不依赖于 PowerShell 远程处理。 即使你的计算机未配置为运行远程命令，你也可以使用 **ComputerName** 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Continuous

指定 **连续** 后，将 `Get-Counter` 获取示例，直到按下 <kbd>CTRL</kbd> + <kbd>C</kbd>。 每秒为每个指定的性能计数器获取样本。 使用 **SampleInterval** 参数可增加连续样本之间的间隔。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Counter

指定一个或多个计数器路径的路径。 路径作为以逗号分隔的数组、变量或文本文件中的值输入。 可以将计数器路径字符串沿管道向下发送到 `Get-Counter` 。

计数器路径使用以下语法：

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

例如：

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

在 `\\ComputerName` 性能计数器路径中是可选的。 如果该计数器路径不包含计算机名称，则 `Get-Counter` 使用本地计算机。

`*`实例中) 星号 (为获取计数器所有实例的通配符。

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ListSet

列出计算机上的性能计数器集。 使用星号 (`*`) 指定所有计数器集。 输入一个名称或以逗号分隔的计数器集名称字符串。 可以向下发送计数器集名称。

若要获取计数器集的格式计数器路径，请使用 **ListSet** 参数。 每个计数器集的 **Paths** 和 **PathsWithInstances** 属性都包含格式化为字符串的单个计数器路径。

可以将计数器路径字符串保存在变量中，或使用管道将该字符串发送到其他 `Get-Counter` 命令。

例如，将每个 **处理器** 计数器路径发送到 `Get-Counter` ：

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> 在 PowerShell 7 中， `Get-Counter` 无法检索计数器集的 **Description** 属性。 **说明** 设置为 `$null` 。

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

指定从每个指定的性能计数器获取的样本数。 若要获取样本的常量流，请使用 **连续** 参数。

如果未指定 **MaxSamples** 参数，则 `Get-Counter` 只为每个指定的计数器获取一个样本。

若要收集大型数据集，请将 `Get-Counter` 作为 PowerShell 后台作业运行。 有关详细信息，请参阅 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)。

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

指定每个指定性能计数器的样本之间的秒数。 如果未指定 **SampleInterval** 参数，则 `Get-Counter` 使用一秒的间隔。

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

`Get-Counter` 接受计数器路径和计数器集名称的管道输入。

## 输出

### Microsoft.PowerShell.Commands.GetCounter.CounterSet、Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet、Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample

若要查看对象的属性，请向下将输出发送到 `Get-Member` 。 输出的对象类型如下所示：

**ListSet** 参数： **microsoft.powershell.commands.getcounter.counterset** 的参数

**计数器** 参数： **microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet**

**CounterSamples** 属性： **microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSample**

## 注释

如果未指定任何参数，则 `Get-Counter` 为每个指定的性能计数器获取一个样本。 使用 **MaxSamples** 和 **连续** 参数获取更多示例。

`Get-Counter` 在样本之间使用一秒的间隔。 使用 **SampleInterval** 参数增加间隔。

**MaxSamples** 和 **SampleInterval** 值适用于命令中每台计算机上的所有计数器。 若要为不同的计数器设置不同的值，请输入单独的 `Get-Counter` 命令。

在 PowerShell 7 中，使用 **ListSet** 参数时， `Get-Counter` 无法检索计数器集的 **Description** 属性。 **说明** 设置为 `$null` 。

## 相关链接

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-Object](..//Microsoft.PowerShell.Core/Where-Object.md)

