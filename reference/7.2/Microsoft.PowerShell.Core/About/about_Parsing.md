---
description: 描述 PowerShell 如何分析命令。
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597077"
---
# <a name="about-parsing"></a>关于分析

## <a name="short-description"></a>简短说明
描述 PowerShell 如何分析命令。

## <a name="long-description"></a>详细说明

当你在命令提示符下输入命令时，PowerShell 会将命令文本分为一系列称为 _令牌_ 的段，然后确定如何解释每个标记。

例如，如果键入：

```powershell
Write-Host book
```

PowerShell 将命令分成两个令牌 `Write-Host` ：和 `book` ，并使用两种主要分析模式之一（表达式模式和参数模式）单独解释每个标记。

> [!NOTE]
> PowerShell 分析命令输入会尝试将命令名称解析为 cmdlet 或本机可执行文件。 如果命令名称没有完全匹配项，则 PowerShell 会将 `Get-` 命令作为默认谓词前面预置到该命令。 例如，PowerShell 分析 `Process` 为 `Get-Process` 。 不建议使用此功能，原因如下：
>
> - 这是低效的。 这会导致 PowerShell 多次搜索。
> - 首先解析同名的外部程序，因此不能执行所需的 cmdlet。
> - `Get-Help` 并且 `Get-Command` 不要识别不带谓词的名称。

### <a name="expression-mode"></a>表达式模式

表达式模式适用于组合表达式，这是脚本语言中的值操作所必需的。 表达式是 PowerShell 语法中值的表示形式，可以是简单或复合，例如：

文本表达式是其值的直接表示形式： 

```powershell
'hello', 32
```

变量表达式携带它们引用的变量的值： 

```powershell
$x, $script:path
```
运算符将其他表达式组合在一起以进行计算： 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- _字符串文本_ 必须包含在引号中。
- _数字_ 被视为数值，而不是作为一系列字符，除非转义)  (。
- _运算符_（包括和等一元运算符） `-` `-not` `+` `-gt` 被解释为运算符，并将其各自的操作应用于它们的参数 (操作数) 。
- _特性和转换表达式_ 被分析为表达式并应用于从属表达式， `[int] '7'` 例如。
- _变量引用_ 被计算为它们的值，但 _展开_ (也就是说，将预填充的参数集粘贴) 将被禁止，并导致分析器错误。
- 其他任何内容都将被视为要调用的命令。

### <a name="argument-mode"></a>参数模式

在分析时，PowerShell 首先会将输入解释为表达式。 但当遇到命令调用时，分析将在参数模式下继续。

自变量模式旨在分析 shell 环境中命令的参数和参数。 所有输入都被视为可扩充字符串，除非它使用以下语法之一：

- 美元符号 (`$`) 仅在其后跟有效的变量名称时才开始使用变量引用 (; 否则，它将被解释为可扩充字符串) 的一部分。
- 引号 (`'` 和 `"`) 开始字符串值
- 圆括号 (`(` 和 `)`) 为新表达式划分界限。
- 子表达式运算符 (`$(` `)`) 划分嵌入式表达式。
- 大括号 (`{` 和 `}`) 为新脚本块划分界限。
- 初始 at 符号 (`@`) 开始表达式语法，如展开 (`@args`) ，数组 () `@(1,2,3)` 和哈希表 (`@{a=1;b=2}`) 。
- 逗号 (`,`) 引入作为数组传递的列表，但要调用的命令是本机应用程序，在这种情况下，它们将被解释为可扩充字符串的一部分。 不支持初始、连续或尾随逗号。

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
嵌入式表达式的值将转换为字符串。

下表提供了在表达式模式和参数模式下处理的值的几个示例以及这些值的计算结果。 假设变量的值 `a` 为 `4` 。

|       示例        |    模型    |      结果       |
| -------------------- | ---------- | ----------------- |
| `2`                  | 表达式 | 2 (整数)        |
| `` `2``              | Expression | "2" (命令)      |
| `echo 2`             | Expression | 2 (整数)        |
| `2+2`                | Expression | 4 (整数)        |
| `echo 2+2`           | 参数   | "2 + 2" (字符串)     |
| `echo(2+2)`          | Expression | 4 (整数)        |
| `$a`                 | Expression | 4 (整数)        |
| `echo $a`            | Expression | 4 (整数)        |
| `$a+2`               | Expression | 6 (整数)        |
| `echo $a+2`          | 参数   | 4 + 2 (字符串)       |
| `$-`                 | 参数   | "$-" (命令)     |
| `echo $-`            | 参数   | "$-" (字符串)      |
| `a$a`                | Expression | "a $ a" (命令)    |
| `echo a$a`           | 参数   | "a4" (字符串)      |
| `a'$a'`              | Expression | "a $ a" (命令)    |
| `echo a'$a'`         | 参数   | "a $ a" (字符串)     |
| `a"$a"`              | Expression | "a $ a" (命令)    |
| `echo a"$a"`         | 参数   | "a4" (字符串)      |
| `a$(2)`              | Expression | "a $ (2) " (命令)  |
| `echo a$(2)`         | 参数   | "a2" (字符串)      |

每个令牌都可解释为某种类型的对象类型，例如布尔型或 string 类型。 PowerShell 尝试从表达式中确定对象类型。
对象类型取决于命令所需的参数类型，以及 PowerShell 是否知道如何将参数转换为正确的类型。 下表显示了分配给表达式返回的值的类型的几个示例。

|       示例          |    模型    |     结果      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | 参数   | "！ 1" (字符串)    |
| `Write-Output (!1)`    | 表达式 | False (布尔)  |
| `Write-Output (2)`     | 表达式 | 2 (整数)      |
| `Set-Variable AB A,B`  | 参数   |  (数组的 "A"、"B")  |
| `CMD /CECHO A,B`       | 参数   | "A，B" (字符串)   |
| `CMD /CECHO $AB`       | 表达式 |  (数组的 "A"、"B")  |
| `CMD /CECHO :$AB`      | 参数   | "： A B" (字符串)  |

PowerShell 3.0 中引入的 "停止分析" 符号 (`--%`) ，定向 PowerShell 避免将输入解释为 powershell 命令或表达式。

在 PowerShell 中调用可执行程序时，将停止解析符号置于程序参数之前。 此方法比使用转义符来防止解释误解要容易得多。

遇到停止分析符号时，PowerShell 会将行中的剩余字符视为文本。 它所执行的唯一解释是使用标准的 Windows 表示法（如）来替换环境变量的值 `%USERPROFILE%` 。

停止分析符号仅在下一个换行符或管道字符之前有效。 不能使用继续符 (`` ` ``) 来扩展其效果，或使用命令分隔符 (`;`) 终止其效果。

例如，以下命令将调用 **Icacls** 程序。

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

若要在 PowerShell 2.0 中运行此命令，必须使用转义符来阻止 PowerShell 错误解释圆括号。

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

从 PowerShell 3.0 开始，可以使用停止分析符号。

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell 会将以下命令字符串发送到 **Icacls** 程序：

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> 停止分析符号仅适用于在 Windows 平台上使用。

## <a name="see-also"></a>另请参阅

[about_Command_Syntax](about_Command_Syntax.md)
