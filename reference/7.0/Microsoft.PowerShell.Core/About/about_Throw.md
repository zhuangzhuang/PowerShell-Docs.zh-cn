---
description: 介绍 Throw 关键字，用于生成终止错误。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: 2984e0a9e5f470594dd1e5987b69b92f91ce4913
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193949"
---
# <a name="about-throw"></a>关于 Throw

## <a name="short-description"></a>简短说明
介绍 Throw 关键字，用于生成终止错误。

## <a name="long-description"></a>长说明

Throw 关键字导致终止错误。 可以使用 Throw 关键字停止对命令、函数或脚本的处理。

例如，可以在 If 语句的脚本块中使用 Throw 关键字来响应某个条件，或在 try-catch Finally 语句的 Catch 块中使用 Throw 关键字。 还可以在参数声明中使用 Throw 关键字，使函数参数成为必需的。

Throw 关键字可以引发任何对象，例如用户消息字符串或导致错误的对象。

## <a name="syntax"></a>语法

Throw 关键字的语法如下所示：

```powershell
throw [<expression>]
```

Throw 语法中的表达式是可选的。 如果 Throw 语句未出现在 Catch 块中，并且它不包含表达式，则会生成一个 ScriptHalted 错误。

```powershell
C:\PS> throw

Exception: ScriptHalted
```

如果在没有表达式的 Catch 块中使用 Throw 关键字，将再次引发当前的 RuntimeException。 有关详细信息，请参阅 about_Try_Catch_Finally。

## <a name="throwing-a-string"></a>引发字符串

Throw 语句中的可选表达式可以是字符串，如下面的示例中所示：

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a>引发其他对象

表达式还可以是一个对象，该对象引发表示 PowerShell 进程的对象，如以下示例中所示：

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

您可以使用 $error 自动变量中 ErrorRecord 对象的 TargetObject 属性来检查错误。

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

还可以引发 ErrorRecord 对象或 .NET 异常。 下面的示例使用 Throw 关键字来引发 FormatException 对象。

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a>产生的错误

Throw 关键字可以生成 ErrorRecord 对象。 ErrorRecord 对象的 Exception 属性包含 RuntimeException 对象。 ErrorRecord 对象和 RuntimeException 对象的其余部分将与 Throw 关键字引发的对象不同。

RunTimeException 对象包装在 ErrorRecord 对象中，ErrorRecord 对象自动保存在 $Error 自动变量中。

## <a name="using-throw-to-create-a-mandatory-parameter"></a>使用 Throw 创建强制参数

不同于以前版本的 PowerShell，不要将 Throw 关键字用于参数验证。 请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) 。

## <a name="see-also"></a>另请参阅

- [about_Break](about_Break.md)
- [about_Continue](about_Continue.md)
- [about_Scopes](about_Scopes.md)
- [about_Trap](about_Trap.md)
- [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
