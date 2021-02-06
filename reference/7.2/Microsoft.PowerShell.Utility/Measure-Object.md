---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 594837b2f85f4d5d5d4125d3f7c63ad2c8a16153
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597464"
---
# Measure-Object

## 摘要
计算对象的数值属性，以及字符串对象（如文本文件）中的字符、单词和行。

## SYNTAX

### GenericMeasure（默认值）

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## DESCRIPTION

`Measure-Object`Cmdlet 计算特定类型的对象的属性值。
`Measure-Object` 执行三种类型的度量，具体取决于命令中的参数。

`Measure-Object`Cmdlet 对对象的属性值执行计算。 您可以使用 `Measure-Object` 来对对象进行计数，或使用指定 **属性** 对对象计数。 还可以使用 `Measure-Object` 来计算数值的 **最小** 值、 **最大** 值、 **总和**、 **StandardDeviation** 值和 **平均值** 。 对于 **字符串** 对象，还可以使用 `Measure-Object` 来计算行数、字数和字符数。

## 示例

### 示例 1：计数目录中的文件和文件夹

此命令对当前目录中的文件和文件夹进行计数。

```powershell
Get-ChildItem | Measure-Object
```

### 示例 2：度量目录中的文件

此命令显示当前目录中所有文件的大小的 **最小值**、 **最大** 值和 **总和** ，以及目录中的文件的平均大小。

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### 示例 3：度量文本文件中的文本

此命令显示 Text.txt 文件中的字符数、字数和行数。
如果没有 **Raw** 参数，则会 `Get-Content` 将文件作为行的数组输出。

第一个命令使用 `Set-Content` 将一些默认文本添加到文件。

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### 示例4：度量值对象包含指定属性

此示例对具有 **DisplayName** 属性的对象的数目进行计数。 前两个命令检索本地计算机上的所有服务和进程。 第三个命令对服务和进程的组合数量进行计数。 最后一个命令将结果与结果组合在一起 `Measure-Object` 。

" **System.object** " 对象没有 **DisplayName** 属性，并且不在最终的计数中。

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### 示例 5：度量 CSV 文件的内容

此命令计算一家公司雇员的平均服务年限。

该 `ServiceYrs.csv` 文件是一个 CSV 文件，其中包含每个员工的员工人数和年服务。 表中的第一行是 **EmpNo**， **年** 的标题行。

当你使用 `Import-Csv` 导入文件时，结果将是 **PSCustomObject** ，其便笺属性为 **EmpNo** 和 **年**。
您可以使用 `Measure-Object` 来计算这些属性的值，就像对象的任何其他属性一样。

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### 示例 6：度量布尔值

此示例演示如何 `Measure-Object` 测量布尔值。
在这种情况下，它使用 **PSIsContainer** **布尔** 值属性来测量当前目录中 () 文件夹的发生情况。

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### 示例7：度量值字符串

下面的示例测量行数，首先是单个字符串，然后是多个字符串。 换行符将 <code>`n</code> 字符串分隔为多个行。

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### 示例8：度量所有值

从 PowerShell 6 开始，的 **AllStats** 参数 `Measure-Object` 允许你将所有统计信息一起测量。

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### 示例9：使用 scriptblock 属性测量

从 PowerShell 6 开始， `Measure-Object` 支持 **ScriptBlock** 属性。 下面的示例演示如何使用 **ScriptBlock** 属性来确定目录中所有文件的大小（以 Mb 为单位）。

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### 示例10：度量值哈希表

从 PowerShell 6 开始， `Measure-Object` 支持度量 **哈希表** 输入。 下面的示例确定 `num` 3 个 **哈希表** 对象的键的最大值。

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### 示例11：度量标准偏差

从 PowerShell 6 开始， `Measure-Object` 支持 `-StandardDeviation` 参数。 下面的示例确定所有进程使用的 CPU 的 *标准偏差* 。 较大的偏差将指示占用最多 CPU 的少量进程。

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### 示例12：使用通配符度量值

从 PowerShell 6 开始， `Measure-Object` 支持在属性名称中使用通配符对对象进行度量。 下面的示例确定一组进程中任何类型的分页内存使用量的最大值。

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## PARAMETERS

### -Average

指示该 cmdlet 显示指定属性的平均值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Character

指示该 cmdlet 对输入对象中的字符数进行计数。

> [!NOTE]
> 每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。 请参阅示例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

指示 cmdlet 忽略字符计数中的空格。
默认情况下，不忽略空格。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要测量的对象。
输入一个包含对象的变量，或键入可获取对象的命令或表达式。

当你将 **inputobject** 参数与一起使用时 `Measure-Object` ， `Measure-Object` **inputobject** 值将被视为单个对象，而不是管道将命令结果传递给。

`Measure-Object`如果要根据对象是否在定义的属性中具有特定值，则建议在管道中使用。

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

### -Line

指示该 cmdlet 对输入对象中的行数进行计数。

> [!NOTE]
> 每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。 请参阅示例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Maximum

指示该 cmdlet 显示指定属性的最大值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

指示该 cmdlet 显示指定属性的最小值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定要度量的一个或多个属性。 如果未指定任何其他度量值，则 `Measure-Object` 会计算具有指定属性的对象。

**Property** 参数的值可以是新的计算属性。 计算属性必须是脚本块。 有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -StandardDeviation

指示该 cmdlet 显示指定属性的值的标准偏差。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sum

指示该 cmdlet 显示指定属性的值的总和。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllStats

指示该 cmdlet 显示指定属性的所有统计信息。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Word

指示该 cmdlet 对输入对象中的单词进行计数。

> [!NOTE]
> 每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。 请参阅示例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
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

可以通过管道将对象传递给 `Measure-Object` 。

## 输出

### GenericMeasureInfo。

### TextMeasureInfo。

如果使用 **Word** 参数，则 `Measure-Object` 返回 **TextMeasureInfo** 对象。
否则，它返回 **GenericMeasureInfo** 对象。

## 注释

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
