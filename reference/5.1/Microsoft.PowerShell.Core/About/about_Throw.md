---
description: 介绍 Throw 关键字，用于生成终止错误。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194179"
---
# <a name="about-throw"></a>关于 Throw

## <a name="short-description"></a>简短说明

介绍 Throw 关键字，用于生成终止错误。

## <a name="long-description"></a>详细说明

Throw 关键字导致终止错误。 可以使用 Throw 关键字停止对命令、函数或脚本的处理。

例如，可以在 If 语句的脚本块中使用 Throw 关键字来响应某个条件，或在 try-catch Finally 语句的 Catch 块中使用 Throw 关键字。 还可以在参数声明中使用 Throw 关键字，使函数参数成为必需的。

Throw 关键字可以引发任何对象，例如用户消息字符串或导致错误的对象。

## <a name="syntax"></a>SYNTAX

Throw 关键字的语法如下所示：

```powershell
throw [<expression>]
```

Throw 语法中的表达式是可选的。 如果 Throw 语句未出现在 Catch 块中，并且它不包含表达式，则会生成一个 ScriptHalted 错误。

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

如果在没有表达式的 Catch 块中使用 Throw 关键字，将再次引发当前的 RuntimeException。 有关详细信息，请参阅 about_Try_Catch_Finally。

## <a name="throwing-a-string"></a>引发字符串

Throw 语句中的可选表达式可以是字符串，如下面的示例中所示：

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>引发其他对象

表达式还可以是一个对象，该对象引发表示 PowerShell 进程的对象，如以下示例中所示：

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

您可以使用 $error 自动变量中 ErrorRecord 对象的 TargetObject 属性来检查错误。

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

还可以引发 ErrorRecord 对象或 Microsoft .NET Framework 异常。 下面的示例使用 Throw 关键字来引发 FormatException 对象。

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>产生的错误

Throw 关键字可以生成 ErrorRecord 对象。 ErrorRecord 对象的 Exception 属性包含 RuntimeException 对象。 ErrorRecord 对象和 RuntimeException 对象的其余部分将与 Throw 关键字引发的对象不同。

RunTimeException 对象包装在 ErrorRecord 对象中，ErrorRecord 对象自动保存在 $Error 自动变量中。

## <a name="using-throw-to-create-a-mandatory-parameter"></a>使用 THROW 创建强制参数

您可以使用 Throw 关键字使函数参数成为必需的。

这是使用 Parameter 关键字的必需参数的替代方法。 使用强制参数时，系统将提示用户输入所需的参数值。 使用 Throw 关键字时，该命令将停止并显示错误记录。

例如，参数子表达式中的 Throw 关键字使 Path 参数成为函数中的必需参数。

在这种情况下，Throw 关键字将引发一个消息字符串，但它是 Throw 关键字的存在，如果未指定 Path 参数，则会生成终止错误。 以下引发的表达式是可选的。

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>另请参阅

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
