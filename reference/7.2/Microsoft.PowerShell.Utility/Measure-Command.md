---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0c2346dc7177e091c0921cd4775422938305e2be
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99596621"
---
# Measure-Command

## 摘要
测量运行脚本块和 cmdlet 所需的时间。

## SYNTAX

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## DESCRIPTION

该 `Measure-Command` cmdlet 在内部运行脚本块或 cmdlet，执行操作的时间，并返回执行时间。

> [!NOTE]
> 运行脚本块的方式是 `Measure-Command` 在当前范围内运行，而不是子范围。

## 示例

### 示例1：度量命令

此示例测量运行 `Get-EventLog` 命令（用于获取 Windows PowerShell 事件日志中的事件）所花费的时间。

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### 示例2：比较 Measure-Command 的两个输出

第一个命令测量处理 `Get-ChildItem` 使用 **Path** 参数仅获取 `.txt` `C:\Windows` 目录及其子目录中的文件的递归命令所花费的时间。

第二个命令测量处理 `Get-ChildItem` 使用特定于访问接口的 "参数的递归命令所花费的时间。

这些命令显示了在 PowerShell 命令中使用特定于提供程序的筛选器的值。

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### 示例3：将输入管道到 Measure-Command

通过管道传递到的对象 `Measure-Command` 可用于传递给 **Expression** 参数的脚本块。 对于管道上的每个对象，将执行一次脚本块。

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### 示例4：显示已测量命令的输出

若要在中显示表达式的输出 `Measure-Command` ，可以使用管道 `Out-Default` 。

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### 示例5：测量子作用域中的执行

`Measure-Command` 运行当前范围内的脚本块，因此脚本块可以修改当前范围中的值。 若要避免对当前范围的更改，必须将脚本块 (括在大括号中， `{}`) 并使用调用运算符 (`&`) 来执行子范围中的块。

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

有关调用运算符的详细信息，请参阅 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)。

## PARAMETERS

### -Expression

指定要测量时间的表达式。 将表达式括在大括号中， (`{}`) 。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

绑定到 **InputObject** 参数的对象是传递给 **Expression** 参数的脚本块的可选输入。 在脚本块中， `$_` 可用于引用管道中的当前对象。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将对象传递给 `Measure-Command` 。

## 输出

### System.TimeSpan

`Measure-Command` 返回一个表示结果的时间跨度对象。

## 注释

## 相关链接

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Trace-Command](Trace-Command.md)

