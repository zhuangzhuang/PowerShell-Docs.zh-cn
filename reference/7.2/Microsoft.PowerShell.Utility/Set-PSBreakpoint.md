---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597070"
---
# Set-PSBreakpoint

## 摘要
在行、命令或变量上设置断点。

## SYNTAX

### 行 (默认值) 

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### 命令

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### 变量

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## DESCRIPTION

`Set-PSBreakpoint`Cmdlet 在当前会话中的脚本或任何命令运行中设置断点。 在 `Set-PSBreakpoint` 执行脚本或运行命令之前，或在调试期间，如果在另一个断点处停止，则可以使用来设置断点。

`Set-PSBreakpoint` 无法在远程计算机上设置断点。 若要在远程计算机上调试脚本，请将该脚本复制到本地计算机，然后从本地进行调试。

每个 `Set-PSBreakpoint` 命令都创建以下三种类型的断点之一：

- 行断点-在特定的行坐标和列坐标处设置断点。
- 命令断点-在命令和函数上设置断点。
- 变量断点-设置变量的断点。

可以在单个命令中设置多个行、命令或变量的断点 `Set-PSBreakpoint` ，但每个 `Set-PSBreakpoint` 命令仅设置一种类型的断点。

在断点处，PowerShell 暂时停止执行，并向调试器提供控制。 命令提示符将更改为 `DBG\>` ，并且一组调试器命令可供使用。 但是，你可以使用 **Action** 参数指定备用响应，例如断点的条件或执行其他任务（如日志记录或诊断）的说明。

`Set-PSBreakpoint`Cmdlet 是专门用于调试 PowerShell 脚本的多个 cmdlet 之一。
有关 PowerShell 调试器的详细信息，请参阅 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。

## 示例

### 示例1：在行上设置断点

此示例在 Sample.ps1 脚本中的第5行设置一个断点。 脚本运行时，执行将在第5行执行之前立即停止。

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

当你按行号设置新断点时，该 `Set-PSBreakpoint` cmdlet 将生成一个 () 的行断点对象，其中包括断点 ID 和命中次数。

### 示例2：在函数上设置断点

此示例在 Sample.ps1 cmdlet 中的函数上创建命令断点 `Increment` 。 该脚本在每次调用指定函数前立即停止执行。

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

结果是命令断点对象。 在运行脚本之前， **点击次数** 属性的值为0。

### 示例3：在变量上设置断点

此示例在 Sample.ps1 脚本中的 **服务器** 变量上设置断点。 它使用值为 **ReadWrite** 的 **Mode** 参数在读取变量的值并刚好在值更改之前停止执行。

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### 示例4：在以指定文本开头的每个命令上设置断点

此示例在 Sample.ps1 脚本中每个以 "write" 开头的命令上设置断点，例如 `Write-Host` 。

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### 示例5：根据变量的值设置断点

`DiskTest`仅当变量的值大于2时，此示例才会在 Test.ps1 脚本中的函数处停止执行 `$Disk` 。

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

**操作** 的值是一个脚本块，可测试 `$Disk` 函数中变量的值。

如果满足条件，则该操作将使用 `break` 关键字停止执行。 备用 (和默认) 会 **继续**。

### 示例6：在函数上设置断点

此示例在函数上设置断点 `CheckLog` 。 由于该命令未指定脚本，因此将在当前会话中运行的任何内容上设置断点。 当调用该函数（而不是声明它）时，调试器将中断。

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### 示例7：在多行上设置断点

此示例在 Sample.ps1 脚本中设置三个行断点。 它将在脚本中每个指定行上的第 2 列处设置断点。 **操作** 参数中指定的操作适用于所有断点。

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETERS

### -Action

指定在每个断点处运行的命令，而不是中断。 输入包含这些命令的脚本块。 可以使用此参数设置条件断点或执行其他任务，例如测试或记录。

如果省略此参数，或未指定任何操作，则执行在断点处停止，并且调试器将启动。

使用 **action** 参数时，操作脚本块将在每个断点处运行。 除非脚本块包含 Break 关键字，否则执行不会停止。 如果在脚本块中使用 Continue 关键字，则执行将继续，直到下一个断点。

有关详细信息，请参阅 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md)、 [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)和 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Column

指定执行停止的脚本文件中的列的列号。 仅输入一个列号。 默认值为列 1。

列值与 **Line** 参数的值一起用于指定断点。 如果 **Line** 参数指定了多个行，则 **Column** 参数将在每个指定行的指定列处设置断点。 PowerShell 在包含指定行和列位置的字符的语句或表达式前停止执行。

列从左上方边沿以列号 1（而不是 0）开始计数。 如果指定了脚本中不存在的列，则不会声明错误，但是永远不会执行断点。

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

设置命令断点。 输入 cmdlet 名称，如 `Get-Process` 或函数名称。 允许使用通配符。

执行正好在执行每个命令的每个实例之前停止。 如果该命令是一个函数，则执行在每次调用该函数时以及在每个开始、过程和结束部分上停止。

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Line

在脚本中设置行断点。 输入一个或多个行号，用逗号分隔。 PowerShell 在执行从每个指定的行上开始的语句前立即停止。

行从脚本文件的左上方边沿以行号 1（而不是 0）开始计数。
如果指定空行，则执行将在下一个非空行之前停止。 如果行不在范围内，则永远不会命中断点。

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mode

指定触发变量断点的访问模式。 默认值为 **Write**。

仅当命令中使用了 **Variable** 参数时，此参数才有效。 此模式适用于命令中设置的所有断点。 此参数的可接受值为：

- **写入** -在将新值写入变量前立即停止执行。
- **读-在** 读取变量时执行，即，当访问变量值时，将被分配、显示或使用。 在读取模式下，当变量的值发生更改时，执行不会停止。
- **ReadWrite** -读取或写入变量时停止执行。

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script

指定此 cmdlet 在其中设置断点的脚本文件的数组。 输入一个或多个脚本文件的路径和文件名称。 如果文件在当前目录中，则可以省略该路径。
允许使用通配符。

默认情况下，将在当前会话中运行的任何命令上设置变量断点和命令断点。 仅当设置行断点时，此参数才是必需的。

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定此 cmdlet 在其上设置断点的变量数组。 输入一个逗号分隔的变量列表，其中不含美元符号 (`$`) 。

使用 **Mode** 参数确定触发断点的访问模式。 默认模式 Write 会在新值写入变量前停止执行。

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无
不能通过管道将输入传递给 `Set-PSBreakpoint` 。

## 输出

###  (System.management.automation.linebreakpoint、VariableBreakpoint、CommandBreakpoint) 断点对象的断点对象。，则为。

`Set-PSBreakpoint` 返回表示它所设置的每个断点的对象。

## 注释

- `Set-PSBreakpoint` 无法在远程计算机上设置断点。 若要在远程计算机上调试脚本，请将该脚本复制到本地计算机，然后从本地进行调试。
- 在多行、命令或变量上设置断点时，将 `Set-PSBreakpoint` 为每个项生成一个断点对象。
- 当在命令提示符下在函数或变量上设置断点时，你可以在创建函数或变量之前或之后设置断点。

## 相关链接

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

