---
description: 介绍如何使用 `Try` 、 `Catch` 和 `Finally` 块处理终止错误。
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596631"
---
# <a name="about-try-catch-finally"></a>关于 Try Catch Finally

## <a name="short-description"></a>简短说明
介绍如何使用 `Try` 、 `Catch` 和 `Finally` 块处理终止错误。

## <a name="long-description"></a>详细说明

使用 `Try` 、 `Catch` 和 `Finally` 块来响应或处理脚本中的终止错误。 `Trap`语句还可用于处理脚本中的终止错误。 有关详细信息，请参阅 [about_Trap](about_Trap.md)。

终止错误阻止语句运行。 如果 PowerShell 在某种程度上未处理终止错误，则 PowerShell 还会停止使用当前管道运行函数或脚本。 在其他语言（如 C）中， \# 终止错误称为 "异常"。

使用 " `Try` 块" 定义脚本中您希望 PowerShell 监视错误的部分。 当在块中发生错误时 `Try` ，该错误首先保存到 `$Error` 自动变量。 然后，PowerShell 会搜索 `Catch` 块以处理错误。 如果该 `Try` 语句没有匹配的 `Catch` 块，则 PowerShell 将继续 `Catch` 在父范围内搜索适当的块或 `Trap` 语句。 `Catch`块完成后，或者如果找不到适当的 `Catch` 块或 `Trap` 语句，则 `Finally` 运行该块。 如果无法处理错误，则会将错误写入错误流。

`Catch`块可以包含用于跟踪错误或恢复预期流的命令。 `Catch`块可以指定它所捕获的错误类型。 `Try` `Catch` 对于不同类型的错误，语句可以包含多个块。

`Finally`块可用于释放脚本不再需要的任何资源。

`Try`、 `Catch` 和与 `Finally` `Try` `Catch` `Finally` C 编程语言中使用的、和关键字类似 \# 。

### <a name="syntax"></a>SYNTAX

`Try`语句包含 `Try` 块、零个或多个 `Catch` 块以及零个或一个 `Finally` 块。 `Try`语句必须至少具有一个 `Catch` 块或一个 `Finally` 块。

下面显示了 `Try` 块语法：

```powershell
try {<statement list>}
```

`Try`关键字后跟括在大括号中的语句列表。 如果在语句列表中的语句正在运行时出现终止错误，则该脚本会将错误对象从块传递 `Try` 到适当的 `Catch` 块。

下面显示了 `Catch` 块语法：

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

错误类型出现在括号中。 最外面的括号指示元素是可选的。

`Catch`关键字后跟一个可选的错误类型规范列表和一个语句列表。 如果块中发生终止错误 `Try` ，则 PowerShell 会搜索适当的 `Catch` 块。 如果找到，则执行块中的语句 `Catch` 。

`Catch`块可以指定一个或多个错误类型。 错误类型是 Microsoft .NET 框架异常或派生自 .NET Framework 异常的异常。 `Catch`块处理指定 .NET Framework 异常类或从指定类派生的任何类的错误。

如果 `Catch` 块指定错误类型，则该 `Catch` 块将处理该类型的错误。 如果 `Catch` 块未指定错误类型，则该块 `Catch` 处理在块中遇到的任何错误 `Try` 。 `Try`语句可以包含 `Catch` 不同指定错误类型的多个块。

下面显示了 `Finally` 块语法：

```powershell
finally {<statement list>}
```

`Finally`关键字后跟在每次运行脚本时都运行的语句列表，即使该语句在运行时 `Try` 没有错误或语句中捕获到错误 `Catch` 。

请注意，按<kbd>CTRL</kbd> + <kbd>C</kbd>将停止管道。 发送到管道的对象将不会显示为输出。 因此，如果包括要显示的语句（如 "Finally block 已运行"），则在按下<kbd>CTRL</kbd>C 后将不会显示该语句（ + <kbd></kbd>即使该 `Finally` 块已运行）。

### <a name="catching-errors"></a>捕获错误

下面的示例脚本显示了一个块 `Try` `Catch` ：

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

`Catch`关键字必须紧跟在 `Try` 块或其他块之后 `Catch` 。

PowerShell 无法将 "NonsenseString" 识别为 cmdlet 或其他项。
运行此脚本将返回以下结果：

```powershell
An error occurred.
```

当脚本遇到 "NonsenseString" 时，会导致终止错误。 `Catch`块通过在块内运行语句列表来处理错误。

### <a name="using-multiple-catch-statements"></a>使用多个 CATCH 语句

`Try`语句可以有任意数量的 `Catch` 块。 例如，以下脚本有一个下载的 `Try` 块 `MyDoc.doc` ，其中包含两个 `Catch` 块：

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

第一个 `Catch` 块处理 **系统 WebException** 和 **IOException** 类型的错误。 第二个 `Catch` 块未指定错误类型。 第二个 `Catch` 块处理发生的任何其他终止错误。

PowerShell 通过继承匹配错误类型。 `Catch`块处理指定 .NET Framework 异常类或从指定类派生的任何类的错误。 下面的示例包含 `Catch` 捕获 "找不到命令" 错误的块：

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

指定的错误类型 **system.management.automation.commandnotfoundexception** 继承自 **System.SystemException** 类型。 以下示例还捕获了 "找不到命令" 错误：

```powershell
catch [System.SystemException] {"Base Exception" }
```

此 `Catch` 块处理 "找不到命令" 错误以及从 **SystemException** 类型继承的其他错误。

如果指定错误类及其派生类之一，请将 `Catch` 派生类的块放在 `Catch` 常规类的块之前。

### <a name="using-traps-in-a-try-catch"></a>在 Try Catch 中使用陷阱

如果终止错误发生在块中 `Try` 定义的块中 `Trap` `Try` ，即使存在匹配的 `Catch` 块， `Trap` 语句也会获得控制权。

如果在 `Trap` 较高的块上存在 `Try` ，并且在当前范围内不存在匹配的 `Catch` 块，则 `Trap` 即使任何父作用域具有匹配的 `Catch` 块，也不会进行控制。

### <a name="accessing-exception-information"></a>访问异常信息

在 `Catch` 块中，可以使用访问当前错误 `$_` ，这也称为 `$PSItem` 。 对象的类型为 **ErrorRecord**。

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

运行此脚本将返回以下结果：

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

还可以访问其他属性，例如 **ScriptStackTrace**、 **Exception** 和 **ErrorDetails**。  例如，如果将脚本更改为以下内容：

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

结果将类似于：

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>使用 FINALLY 释放资源

若要释放脚本使用的资源，请在 `Finally` 和块后面添加块 `Try` `Catch` 。 `Finally`不管 `Try` 块是否遇到终止错误，block 语句都将运行。 PowerShell 在 `Finally` 脚本终止之前或在当前块超出范围之前运行块。

`Finally`即使使用<kbd>CTRL</kbd> + <kbd>C</kbd>来停止脚本，块也会运行。 `Finally`如果 Exit 关键字从块内停止脚本，也会运行块 `Catch` 。

### <a name="see-also"></a>另请参阅

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

