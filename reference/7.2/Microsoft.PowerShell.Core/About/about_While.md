---
description: 描述一个语言语句，您可以使用该语句根据条件测试的结果运行命令块。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595826"
---
# <a name="about-while"></a>关于 While

## <a name="short-description"></a>简短说明
描述一个语言语句，您可以使用该语句根据条件测试的结果运行命令块。

## <a name="long-description"></a>详细说明

While 语句 (也称为 While 循环) 是一种用于创建循环的语言构造，只要条件测试的计算结果为 true，就会在命令块中运行命令。 While 语句的构造比 For 语句更简单，因为它的语法不够复杂。 此外，它比 Foreach 语句更灵活，因为您在 While 语句中指定条件测试来控制循环运行的次数。

下面显示了 While 语句语法：

```powershell
while (<condition>){<statement list>}
```

运行 While 语句时，PowerShell 会 `<condition>` 在输入节之前计算语句的部分 `<statement list>` 。 语句的条件部分解析为 true 或 false。 只要条件保持为 true，PowerShell 将重新运行该 `<statement list>` 部分。

`<statement list>`语句的部分包含一个或多个命令，这些命令在每次输入或重复循环时都会运行。

例如，如果未创建 $val 变量，或者 $val 变量已创建并初始化为0，则以下 While 语句将显示数字1到3。

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

在此示例中，条件 ($val 在 $val \= 0、1、2时不等于 3) 为 true。 每次通过循环时，使用 \+ \+ 一元增量运算符 ($val) 递增 1 $val \+ \+ 。 上次循环的时间，$val \= 3。 如果 $val 等于3，则 condition 语句的计算结果为 false，并且循环将退出。

若要在 PowerShell 命令提示符下轻松写入此命令，可以按以下方式输入：

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

请注意，分号将添加1的第一个命令与向控制台写入 $val 的第二个命令中的 $val 隔开。

## <a name="see-also"></a>另请参阅

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)

