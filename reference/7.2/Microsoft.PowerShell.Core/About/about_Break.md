---
description: 描述可用于立即退出、、、、 `foreach` `for` `while` `do` `switch` 或 `trap` 语句的语句。
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 3c418f5bae11f957880c8b53ee0bcf2fb44515ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598083"
---
# <a name="about-break"></a>关于中断

## <a name="short-description"></a>简短说明

描述可用于立即退出、、、、 `foreach` `for` `while` `do` `switch` 或 `trap` 语句的语句。

## <a name="long-description"></a>长说明

`break`语句提供退出当前控制块的方法。
继续执行控制块后的下一条语句。 语句支持标签。 标签是为脚本中的语句分配的名称。

## <a name="using-break-in-loops"></a>在循环中使用 break

如果 `break` 语句出现在循环中，如 `foreach` 、 `for` 、 `do` 或循环，则 PowerShell 会 `while` 立即退出该循环。

`break`语句可以包含一个标签，使您可以退出嵌入循环。 标签可以在脚本中指定任意循环关键字，如 `foreach` 、 `for` 或 `while` 。

下面的示例演示如何使用 `break` 语句退出 `for` 语句：

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

在此示例中， `break` `for` 如果变量等于1，语句将退出循环 `$i` 。 尽管语句的 `for` 计算结果为 **True** ，但直到 `$i` 大于10，否则，PowerShell 将在第一次运行循环时到达 break 语句 `for` 。

`break`在必须满足内部条件的循环中使用语句更为常见。 请看下面的 `foreach` 语句示例：

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

在此示例中， `foreach` 语句将循环访问 `$varB` 数组。 `if`语句的计算结果为 False，即循环运行的前两次，变量 `$i` 递增1。 第三次运行循环时， `$i` 等于2， `$val` 变量等于30。 此时， `break` 语句将运行，并且 `foreach` 循环将退出。

### <a name="using-a-labeled-break-in-a-loop"></a>在循环中使用带标记的中断

`break`语句可以包含标签。 如果对标签使用 `break` 关键字，则 PowerShell 会退出标记的循环，而不是退出当前循环。
标签是一个冒号，后跟您分配的名称。 标签必须是语句中的第一个标记，并且必须后跟循环关键字，如 `while` 。

`break` 将执行移出标记循环。 在嵌入循环中，此方法的结果与 `break` 关键字本身使用时的结果不同。 此示例包含 `while` 带有语句的语句 `for` ：

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

如果条件2的计算结果为 **True**，则脚本的执行将向下跳到标记的循环后的语句。 在此示例中，执行再次与语句一起开始 `$a = $c` 。

可以嵌套多个标记的循环，如以下示例中所示。

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

如果 `$b` 变量的计算结果为 True，则脚本的执行将在标记为 "red" 的循环后恢复。 如果 `$c` 变量的计算结果为 True，则脚本控件的执行将在标记为 "黄色" 的循环后恢复。

如果 `$a` 变量的计算结果为 True，则执行将在最内层循环后恢复。 不需要标签。

PowerShell 不会限制标签可继续执行的程度。 标签甚至可以在脚本和函数调用边界之间传递控制。

## <a name="using-break-in-a-switch-statement"></a>在 switch 语句中使用 break

在 `switch` 构造中， `break` 导致 PowerShell 退出 `switch` 代码块。

`break`关键字用于离开 `switch` 构造。 例如，下面的 `switch` 语句使用 `break` 语句来测试最具体的条件：

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

在此示例中，将 `$var` 创建变量并将其初始化为的字符串值 `word2` 。 `switch`语句使用 **Regex** 类将变量值首先与字词进行匹配 `word2` 。 由于变量值和语句中的第一个测试 `switch` 匹配，因此语句中的第一个代码块将 `switch` 运行。

当 PowerShell 到达第一 `break` 条语句时， `switch` 语句将退出。 如果删除了该示例中的四个 `break` 语句，则满足所有四个条件。 此示例使用 `break` 语句在满足最特定的条件时显示结果。

## <a name="using-break-in-a-trap-statement"></a>在 trap 语句中使用 break

如果在语句体中执行的最后一条语句 `trap` 是 `break` ，则会取消错误对象，并重新引发异常。

下面的示例创建一个使用语句捕获的 **system.dividebyzeroexception** 异常 `trap` 。

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

请注意，执行在出现异常时停止。 永远不会 `After loop` 到达。
执行后，将重新引发异常 `trap` 。

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>不要在循环、开关或陷阱的外部使用 break

如果在 `break` 直接支持 (循环、) 的构造之外使用，则 `switch` `trap` PowerShell 将查找封闭构造 _的调用堆栈_ 。 如果找不到封闭构造，则当前的运行空间将不知不觉地终止。

这意味着，不小心在支持它的封闭构造之外使用的函数和脚本 `break` 可能会意外终止其 _调用方_。

在 `break` 管道内使用（ `break` 如 `ForEach-Object` 脚本块），不仅会退出管道，还可能终止整个运行空间。

## <a name="see-also"></a>请参阅

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
