---
description: 描述处理终止错误的关键字。
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 30b03235cbc2338de3786e37416d1c1ce1d660e3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596221"
---
# <a name="about-trap"></a>关于陷阱

## <a name="short-description"></a>简短说明

描述处理终止错误的关键字。

## <a name="long-description"></a>长说明

终止错误阻止语句运行。 如果 PowerShell 未以某种方式处理终止错误，则 PowerShell 还会停止在当前管道中运行该函数或脚本。 在其他语言（如 c #）中，终止错误称为 "异常"。

`trap`关键字指定发生终止错误时要运行的语句的列表。 `trap` 语句按以下方式处理终止错误：

- 在处理语句块后显示错误 `trap` ，并继续执行包含的脚本或函数 `trap` 。 这是默认行为。

- 显示错误并中止语句中包含 using 的脚本或函数的 `trap` 执行 `break` `trap` 。

- 为此错误静音，但 `trap` 使用语句中的来继续执行包含的脚本或函数 `continue` `trap` 。

的语句列表 `trap` 可以包含多个条件或函数调用。 `trap`可以编写日志、测试条件，甚至可以运行其他程序。

### <a name="syntax"></a>语法

`trap`语句具有以下语法：

```powershell
trap [[<error type>]] {<statement list>}
```

`trap`语句包括在发生终止错误时要运行的语句的列表。 `trap`语句包含 `trap` 关键字，后面可以跟类型表达式，包含在捕获错误时要运行的语句的列表。 类型表达式精炼了捕获的错误类型 `trap` 。

脚本或命令可以包含多个 `trap` 语句。 `trap` 语句可以出现在脚本或命令中的任意位置。

### <a name="trapping-all-terminating-errors"></a>捕获所有终止错误

当发生终止错误时，如果在脚本或命令中未以其他方式进行处理，则 PowerShell 会检查是否有 `trap` 处理错误的语句。 如果 `trap` 有语句，则 PowerShell 将继续运行语句中的脚本或命令 `trap` 。

下面的示例是一个非常简单的 `trap` 语句：

```powershell
trap {"Error found."}
```

此 `trap` 语句捕获任何终止错误。

在下面的示例中，函数包含导致运行时错误的有意义的字符串。

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

运行此函数将返回以下内容：

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

下面的示例包含 `trap` 使用自动变量显示错误的语句 `$_` ：

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

运行此版本的函数将返回以下内容：

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` 语句可以在给定范围内的任何位置定义，但始终应用于该范围内的所有语句。 在运行时，将在 `trap` 执行任何其他语句之前定义块中的语句。 在 JavaScript 中，这称为 [提升](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)。 这意味着， `trap` 即使执行操作未提前过定义的点，语句也适用于该块中的所有语句。 例如， `trap` 在脚本末尾定义，并在第一个语句中引发错误仍将触发 `trap` 。

### <a name="trapping-specific-errors"></a>捕获特定错误

脚本或命令可以包含多个 `trap` 语句。 `trap`可以定义来处理特定的错误。

以下示例是 `trap` 捕获特定错误 **system.management.automation.commandnotfoundexception** 的语句：

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

当函数或脚本遇到与已知命令不匹配的字符串时，此 `trap` 语句将显示 "命令错误捕获" 字符串。
运行 `trap` 语句列表后，PowerShell 将错误对象写入错误流，然后继续运行脚本。

PowerShell 使用 .NET 异常类型。 下面 **的示例指定了 system.exception** 错误类型：

```powershell
trap [System.Exception] {"An error trapped"}
```

**System.management.automation.commandnotfoundexception** 错误类型继承自 **system.object** 类型。 此语句捕获未知命令创建的错误。 它还捕获其他错误类型。

一个脚本中可以有多个 `trap` 语句。 每个错误类型只能用一条语句来捕获 `trap` 。 当发生终止错误时，PowerShell 会 `trap` 在当前的执行范围内搜索具有最特定匹配的。

下面的脚本示例包含错误。 该脚本包含一个 `trap` 用于捕获任何终止错误和 `trap` 指定 **system.management.automation.commandnotfoundexception** 类型的特定语句的常规语句。

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

运行此脚本会生成以下结果：

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

由于 PowerShell 无法将 "nonsenseString" 识别为 cmdlet 或其他项，因此它将返回 **system.management.automation.commandnotfoundexception** 错误。 此终止错误由特定的语句捕获 `trap` 。

下面的脚本示例包含 `trap` 具有不同错误的相同语句：

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

运行此脚本会生成以下结果：

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

尝试除以零不会造成 **system.management.automation.commandnotfoundexception** 错误。 相反，此错误由另一语句捕获 `trap` ，后者捕获任何终止错误。

### <a name="trapping-errors-and-scope"></a>捕获错误和范围

如果终止错误发生在语句所在的作用域内 `trap` ，则 PowerShell 将运行由定义的语句列表 `trap` 。 错误之后的语句将继续执行。 如果 `trap` 语句不同于错误的作用域，则执行将在语句所在的下一个语句中继续执行 `trap` 。

例如，如果某个函数中出现错误，并且该 `trap` 语句在函数中，则该脚本将继续执行下一条语句。 下面的脚本包含错误和 `trap` 语句：

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

运行此脚本会生成以下结果：

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

`trap`函数中的语句捕获错误。 显示消息后，PowerShell 将继续运行函数。 请注意， `Function1` 已完成。

将此与以下包含相同错误和语句的示例进行比较 `trap` 。 在此示例中， `trap` 语句发生在函数的外部：

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

运行 `Function2` 函数会生成以下结果：

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

在此示例中，"function2 已完成" 命令未运行。 在这两个示例中，终止错误发生在函数内。 但在此示例中， `trap` 语句位于函数之外。 运行语句后，PowerShell 不会返回函数 `trap` 。

> [!CAUTION]
> 为同一个错误条件定义多个陷阱时，将 `trap` 使用范围) 中的第一个已定义的词法 (最高。

在下面的示例中，仅 `trap` 运行带 "了 1" 的。

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> Trap 语句的作用域限定为它的编译位置。 如果在 `trap` 函数或带句点的脚本中有语句，则当函数或点即点脚本退出时， `trap` 将删除中的所有语句。

### <a name="using-the-break-and-continue-keywords"></a>使用 break 和 continue 关键字

可以 `break` `continue` 在语句中使用和关键字， `trap` 以确定在终止错误之后脚本或命令是否继续运行。

如果在 `break` 语句列表中包含语句 `trap` ，则 PowerShell 将停止该函数或脚本。 下面的示例函数 `break` 在语句中使用关键字 `trap` ：

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

由于 `trap` 语句包含 `break` 关键字，因此该函数不会继续运行，并且不会运行 "函数已完成" 行。

如果在 `continue` 语句中包含关键字 `trap` ，则 PowerShell 会在导致错误的语句之后恢复，就像没有 `break` 或一样 `continue` 。 但使用 `continue` 关键字时，PowerShell 不会将错误写入错误流。

下面的示例函数 `continue` 在语句中使用关键字 `trap` ：

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

函数在捕获错误后恢复，并且 "函数已完成" 语句将运行。 不会将错误写入错误流。

## <a name="notes"></a>说明

`trap` 语句提供一种简单的方法来广泛地确保处理范围内的所有终止错误。 若要进行更细化的错误处理，请使用 `try` / `catch` 使用语句定义陷阱的块 `catch` 。 `catch`语句仅适用于关联语句中的代码 `try` 。 有关详细信息，请参阅 [about_Try_Catch_Finally](about_Try_Catch_Finally.md)。

## <a name="see-also"></a>请参阅

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
