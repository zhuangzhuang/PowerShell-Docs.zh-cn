---
description: 按优先顺序列出 PowerShell 运算符。
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d4031a9d9a67340470d5418a9c2d3e33c5caed13
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595617"
---
# <a name="about-operator-precedence"></a>关于运算符优先级

## <a name="short-description"></a>简短说明
按优先顺序列出 PowerShell 运算符。

## <a name="long-description"></a>详细说明

PowerShell 运算符使你可以构建简单但功能强大的表达式。 本主题按优先顺序列出运算符。 优先顺序是指当多个运算符出现在同一表达式中时，PowerShell 计算操作员的顺序。

如果运算符具有相同的优先级，则 PowerShell 会在表达式中出现时从左到右进行计算。 赋值运算符、强制转换运算符和求反运算符 (`!` 、 `-not` `-bnot`) （从右到左计算）。

可以使用箱（如括号）来替代标准优先顺序，并强制 PowerShell 在 unenclosed 部分之前计算表达式中包含的部分。

在下面的列表中，运算符按其计算顺序列出。 同一行或同一组中的运算符具有相同的优先级。

Operator 列列出运算符。 "引用" 列列出了用于描述操作员的 PowerShell 帮助主题。 若要显示该主题，请键入 `get-help <topic-name>` 。

|         OPERATOR         |           参考            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | [about_Operators][]            |
| `. ?.` (成员访问)    | [about_Operators][]            |
| `::` (静态)             | [about_Operators][]            |
| `[0] ?[0]` (索引运算符)  | [about_Operators][]         |
| `[int]` (cast 运算符)  | [about_Operators][]            |
| `-split` (一元)          | [about_Split][]                |
| `-join` (一元)           | [about_Join][]                 |
| `,` (逗号运算符)      | [about_Operators][]            |
| `++ --`                  | [about_Assignment_Operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (范围运算符)     | [about_Operators][]            |
| `-f` (格式运算符)    | [about_Operators][]            |
| `-` (一元/负)      | [about_Arithmetic_Operators][] |
| `* / %`                  | [about_Arithmetic_Operators][] |
| `+ -`                    | [about_Arithmetic_Operators][] |

下面的运算符组具有相同的优先级。 它们区分大小写和不区分大小写的变量具有相同的优先级。

|         OPERATOR          |           参考            |
| ------------------------- | ------------------------------ |
| `-split` (二进制)          | [about_Split][]                |
| `-join` (二进制)           | [about_Join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

列表按优先级顺序在此处恢复：

|                OPERATOR                 |           参考            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_Arithmetic_Operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

以下各项不是真正的运算符。 它们是 PowerShell 命令语法的一部分，而不是表达式语法的一部分。 赋值始终是执行的最后一个操作。

|                SYNTAX                   |           参考            |
| --------------------------------------- | ------------------------------ |
| `.` (点-源)                         | [about_Operators][]            |
| `&` (调用)                               | [about_Operators][]            |
| `? <if-true> : <if-false>` (三元运算符)  | [about_Operators][]      |
| `??` (coalese 运算符)             | [about_Operators][]            |
| <code>&#124;</code> (管道运算符)  | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| <code>&& &#124;&#124;</code> (管道链运算符)  | [about_Operators][] |
| `= += -= *= /= %= ??=`                  | [about_Assignment_Operators][] |

## <a name="examples"></a>示例

以下两个命令显示算术运算符，以及使用括号强制 PowerShell 首先计算表达式中包含的部分的效果。

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

下面的示例从本地目录中获取只读文本文件，并将其保存在 `$read_only` 变量中。

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

它等效于以下示例。

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

由于管道运算符 (`|`) 的优先级高于赋值运算符 () ，因此在 `=` `Get-ChildItem` 将 cmdlet 获取的文件分配给该变量之前，会将其发送到 `Where-Object` cmdlet 进行筛选 `$read_only` 。

下面的示例演示索引运算符优先于强制转换运算符。

此表达式创建一个包含三个字符串的数组。 然后，它将索引运算符与值0一起使用，以选择数组中的第一个对象，这是第一个字符串。 最后，它将所选对象强制转换为字符串。 在这种情况下，转换不起作用。

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

此表达式使用括号强制执行强制转换操作，然后再进行索引选择。 因此，整个数组将转换为 (单个) 字符串。 然后，索引运算符选择字符串数组中的第一项，即第一个字符。

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

在下面的示例中，由于 `-gt` (大于) 运算符的优先级高于 `-and` (逻辑 AND) 运算符，因此表达式的结果为 FALSE。

```powershell
PS> 2 -gt 4 -and 1
False
```

它等效于下面的表达式。

```powershell
PS> (2 -gt 4) -and 1
False
```

如果-和运算符具有较高的优先级，则回答为 TRUE。

```powershell
PS> 2 -gt (4 -and 1)
True
```

但是，此示例演示了管理操作员优先级的重要原则。 如果某个表达式难以解释，则使用括号来强制求值顺序，即使它强制使用默认运算符优先级也是如此。 圆括号使您的意图对阅读和维护您的脚本的人很清楚。

## <a name="see-also"></a>另请参阅

[about_Operators][]

[about_Assignment_Operators][]

[about_Comparison_Operators][]

[about_Arithmetic_Operators][]

[about_Join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
