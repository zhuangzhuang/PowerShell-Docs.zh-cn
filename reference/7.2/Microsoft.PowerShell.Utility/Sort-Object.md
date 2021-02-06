---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: fead3b3d109a79186bc82f3c9f212f11f7b0bc57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597048"
---
# Sort-Object

## 摘要
按照属性值对对象进行排序。

## SYNTAX

### Default（默认值）

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### TOP

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### 下

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## DESCRIPTION

该 `Sort-Object` cmdlet 根据对象属性值按升序或降序对对象进行排序。 如果命令中未包含 sort 属性，则 PowerShell 将使用第一个输入对象的默认排序属性。 如果输入对象的类型没有默认的排序属性，则 PowerShell 会尝试比较对象本身。 有关详细信息，请参阅 " [备注](#notes) " 部分。

可以按单个属性或多个属性对对象进行排序。 多个属性使用哈希表按升序、降序或排序顺序的组合进行排序。 属性被排序为区分大小写或不区分大小写。 使用 **Unique** 参数从输出中消除重复项。

## 示例

### 示例 1：按名称对当前目录进行排序

此示例对目录中的文件和子目录进行排序。

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

`Get-ChildItem`Cmdlet 从 **Path** 参数 **C:\Test** 指定的目录中获取文件和子目录。 对象通过管道向下发送到 `Sort-Object` cmdlet。
`Sort-Object` 未指定属性，因此输出按默认排序属性 " **名称**" 排序。

### 示例 2：按文件长度对当前目录进行排序

此命令以升序显示当前目录中的文件。

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

`Get-ChildItem`Cmdlet 将从 **Path** 参数所指定的目录中获取文件。
**File** 参数指定 `Get-ChildItem` 仅获取文件对象。 对象通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 使用 **length** 参数以升序对文件进行排序。

### 示例3：按内存使用情况对进程排序

此示例根据 (WS) 大小的工作集显示具有最高内存使用率的进程。

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

`Get-Process`Cmdlet 将获取计算机上正在运行的进程的列表。 进程对象将通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 使用 **属性** 参数按 **WS** 对对象进行排序。 对象通过管道向下发送到 `Select-Object` cmdlet。
`Select-Object` 使用 **最后一个** 参数来指定最后五个对象，这些对象是具有最高 **WS** 使用量的对象。

在 PowerShell 6 中， `Sort-Object` 参数 **底端** 是的替代方法 `Select-Object` 。 例如，`Get-Process | Sort-Object -Property WS -Bottom 5`。

### 示例4：按 Id 对 HistoryInfo 对象进行排序

此命令使用 **Id** 属性对 PowerShell 会话的 **HistoryInfo** 对象进行排序。 每个 PowerShell 会话都有自己的命令历史记录。

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

`Get-History`Cmdlet 从当前 PowerShell 会话中获取历史记录对象。 对象通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 使用 **属性** 参数按 **Id** 对对象进行排序。 **降序** 参数按从最新到最旧的命令历史记录进行排序。

### 示例5：使用哈希表按升序和降序对属性进行排序

此示例使用两个属性对对象、 **状态** 和 **DisplayName** 进行排序。 **状态** 按降序排序， **DisplayName** 按升序排序。

哈希表用于指定 **属性** 参数的值。 哈希表使用表达式来指定属性名称和排序顺序。 有关哈希表的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

哈希表中使用的 **Status** 属性是一个枚举属性。
有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

`Get-Service`Cmdlet 将获取计算机上的服务列表。 服务对象将通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 将 **property** 参数与哈希表一起使用，以指定属性名称和排序顺序。 **属性** 参数按两个 **属性进行排序，按** 降序 **排列，按** 升序排序。

**状态** 为枚举属性。 已 **停止** 的值为 **1** ，并且 **运行** 的值为 **4**。 **降序** 参数设置为， `$True` 以便在 **停止** 进程之前显示 **正在运行** 的进程。 **DisplayName** 将 **降序** 参数设置为 `$False` ，以按字母顺序对显示名称进行排序。

### 示例 6：按时间跨度对文本文件进行排序

此命令按 **CreationTime** 和 **LastWriteTime** 之间的时间跨度以降序对文本文件进行排序。

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 **C:\Test** 以及所有 `*.txt` 文件。 对象通过管道向下发送到 `Sort-Object` cmdlet。
`Sort-Object` 将 **Property** 参数与哈希表一起使用，以确定每个文件在 **CreationTime** 与 **LastWriteTime** 之间的时间跨度。 **降序** 参数将设置为 `$False` ，以便按最长到最短时间跨度的顺序进行排序。

### 示例 7：对文本文件中的名称进行排序

此示例演示如何对文本文件中的列表进行排序。 原始文件显示为未排序的列表。 `Sort-Object` 对内容进行排序，然后用删除重复项的 **唯一** 参数对内容进行排序。

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

`Get-Content`Cmdlet 使用 **Path** 参数来指定目录和文件名。 文件 **ServerNames.txt** 包含计算机名称的未排序列表。

`Get-Content`Cmdlet 使用 **Path** 参数来指定目录和文件名。 文件 **ServerNames.txt** 包含计算机名称的未排序列表。 对象通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 按默认顺序升序排序列表。

`Get-Content`Cmdlet 使用 **Path** 参数来指定目录和文件名。 文件 **ServerNames.txt** 包含计算机名称的未排序列表。 对象通过管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 使用 **Unique** 参数删除重复的计算机名称。 列表按默认顺序升序排序。

### 示例8：将字符串作为整数排序

此示例演示如何对包含字符串对象的文本文件进行排序。 可以将每个命令向下发送到管道， `Get-Member` 并验证对象是否为字符串而不是整数。 对于这些示例， `ProductId.txt` 文件包含未排序的产品编号列表。

在第一个示例中， `Get-Content` 获取该 cmdlet 的文件和管道的内容 `Sort-Object` 。 `Sort-Object` 按升序对字符串对象进行排序。

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

在第二个示例中， `Get-Content` 获取该 cmdlet 的文件和管道的内容 `Sort-Object` 。 `Sort-Object` 使用脚本块将字符串转换为整数。 在示例代码中， `[int]` 将字符串转换为整数，并 `$_` 表示每个字符串在管道中出现。 整数对象通过管道向下发送到 `Sort-Object` cmdlet。
`Sort-Object` 按数值顺序对整数对象进行排序。

### 示例9：使用稳定排序

使用 **Top、Top** 或 **稳定** 参数时，排序的对象将按其接收顺序传递（  `Sort-Object` 当排序条件相等时）。 在此示例中，我们将按1到20的值对数字进行排序。 取模值的范围为0到2。

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

第一次排序的输出按模数值正确分组，但各个项未在模数范围内进行排序。 第二个排序使用 **稳定** 选项来返回稳定排序。

## PARAMETERS

### -底部

指定从已排序对象数组的末尾处获取的对象数。 这会导致稳定的排序。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

指示排序区分大小写。 默认情况下，排序不区分大小写。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

指定用于排序的区域性配置。 用于 `Get-Culture` 显示系统的区域性配置。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Descending

指示按 `Sort-Object` 降序对对象进行排序。 默认值为升序。

若要使用不同的排序顺序对多个属性进行排序，请使用哈希表。 例如，使用哈希表，可以按升序对一个属性进行排序，而按降序对另一个属性进行排序。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

若要对对象进行排序，请将其向下发送到 `Sort-Object` 。 如果使用 **InputObject** 参数提交项的集合，则将 `Sort-Object` 接收一个表示该集合的对象。 由于无法对一个对象进行排序，因此 `Sort-Object` 返回未更改的整个集合。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Property

指定用于对 `Sort-Object` 对象进行排序的属性名称。 允许使用通配符。
根据属性值对对象进行排序。 如果未指定属性，则会 `Sort-Object` 根据对象类型或对象本身的默认属性进行排序。

多个属性可以按升序、降序或排序顺序的组合进行排序。 如果指定多个属性，则按第一个属性对对象进行排序。 如果有多个对象的第一个属性的值相同，则按第二个属性对这些对象进行排序。 此过程将一直继续，直到不存在其他指的定属性或没有对象组。

**属性** 参数的值可以是计算属性。 若要创建计算属性，请使用哈希表。

哈希表的有效键如下所示：

- `expression` - `<string>` 或 `<script block>`
- `ascending` 或 `descending` - `<boolean>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### -Top

指定从已排序对象数组的开头开始获取的对象数。 这会导致稳定的排序。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Unique

指示 `Sort-Object` 消除重复项并仅返回集合中的唯一成员。 唯一值的第一个实例包括在已排序的输出中。

**Unique** 不区分大小写。 只有字符大小写不同的字符串被视为相同。
例如，字符和字符。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -稳定

排序的对象按排序条件相等时接收的顺序传递。

此参数是在 PowerShell v 6.2.0 中添加的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
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

### System.Management.Automation.PSObject

可以通过管道将要排序的对象传递给 `Sort-Object` 。

## 输出

### System.Management.Automation.PSObject

`Sort-Object` 返回已排序的对象。

## 注释

该 `Sort-Object` cmdlet 根据命令中指定的属性或对象类型的默认排序属性来对对象进行排序。 使用 `PropertySet` 文件中指定的来定义默认的排序属性 `DefaultKeyPropertySet` `types.ps1xml` 。 有关详细信息，请参阅 [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)。

如果对象不具有指定的属性之一，则会将该对象的属性值解释 `Sort-Object` 为 **Null** ，并将其放置在排序顺序的末尾。

如果没有可用的排序属性，则 PowerShell 会尝试比较对象本身。
`Sort-Object` 对每个属性使用 **Compare** 方法。 如果某个属性未实现 **IComparable**，则该 cmdlet 会将属性值转换为字符串，并将 **Compare** 方法用于 **system.string**。 有关详细信息，请参阅 [CompareTo (Object) 方法](/dotnet/api/system.management.automation.psobject.compareto)。

如果对枚举属性（如 **状态**）进行排序，则 `Sort-Object` 按枚举值排序。 对于 Windows 服务，"已 **停止** " 的值为 **1** ，并且 **运行** 的值为 **4**。
由于枚举值的原因，**停止** 在 **运行** 前进行排序。 有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

执行稳定排序时，排序算法的性能较慢。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Tee-Object](Tee-Object.md)
