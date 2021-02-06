---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: 65ccc37b1c9122d54f3caf85f4546e1381558ca9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595608"
---
# Invoke-Expression

## 摘要
在本地计算机上运行命令或表达式。

## SYNTAX

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## DESCRIPTION

该 `Invoke-Expression` cmdlet 将指定的字符串作为命令进行计算，并返回表达式或命令的结果。 如果没有，则在 `Invoke-Expression` 命令行提交的字符串将 (回显) 更改。

表达式在当前作用域中计算和运行。 有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

> [!CAUTION]
> 在脚本中使用 cmdlet 时，请采取合理的防范措施 `Invoke-Expression` 。 当使用 `Invoke-Expression` 运行用户输入的命令时，请验证在运行该命令之前，该命令是否可安全运行。 通常，最好将脚本设计为包含预定义的输入选项，而不允许随意输入。

## 示例

### 示例 1：计算表达式

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

此示例演示 `Invoke-Expression` 如何使用来计算表达式。 如果没有 `Invoke-Expression` ，则打印但不计算表达式。

第一个命令将 `Get-Process` () 字符串的值分配给 `$Command` 变量。

第二个命令显示在命令行键入变量名称的效果。 PowerShell 回显该字符串。

第三个命令使用 `Invoke-Expression` 来计算字符串。

### 示例 2：在本地计算机上运行脚本

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

这些命令用于 `Invoke-Expression` 在本地计算机上运行脚本 TestScript.ps1。 这两个命令是等效的。 第一个命令使用 **command** 参数来指定要运行的命令。
第二个使用管道运算符 (`|`) 将命令字符串发送到 `Invoke-Expression` 。

### 示例 3：运行变量中的命令

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

此示例运行保存在变量中的命令字符串 `$Command` 。

命令字符串括在单引号中，因为它包含一个 `$_` 表示当前对象的变量。 如果它用双引号引起来，则在将 `$_` 变量保存到变量之前，该变量将替换为其值 `$Command` 。

### 示例 4：获取并运行 cmdlet 帮助示例

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

此命令检索并运行 cmdlet 帮助主题中的第一个示例 `Get-EventLog` 。

若要运行其他 cmdlet 的示例，请将该变量的值更改 `$Cmdlet_name` 为该 cmdlet 的名称。 将 `$Example_number` 变量更改为要运行的示例编号。 如果示例数字无效，则该命令将失败。

## PARAMETERS

### -Command

指定要运行的命令或表达式。 键入该命令或表达式，或输入包含该命或表达式的变量。 **Command** 参数是必需的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String 或 PSObject

可以通过管道将表示命令的对象传递给 `Invoke-Expression` 。
使用 `$Input` 自动变量来表示命令中的输入对象。

## 输出

### PSObject

返回由调用的命令生成的输出， () 的 **命令** 参数的值。

## 注释

在大多数情况下，使用 PowerShell 调用运算符调用表达式并获得相同的结果。
调用运算符是一种更安全的方法。 有关详细信息，请参阅 [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)。

## 相关链接

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

