---
description: 描述语句如何 `continue` 立即将程序流返回到程序循环、 `switch` 语句或语句的顶部 `trap` 。
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 618ebee65d0407751e443fd957ab008d35c5375b
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195606"
---
# <a name="about-continue"></a>关于继续

## <a name="short-description"></a>简短说明

描述语句如何 `continue` 立即将程序流返回到程序循环、 `switch` 语句或语句的顶部 `trap` 。

## <a name="long-description"></a>长说明

`continue`语句提供一种退出当前控制块但继续执行的方法，而不是完全退出。 语句支持标签。
标签是为脚本中的语句分配的名称。

## <a name="using-continue-in-loops"></a>在循环中使用 continue

未标记的 `continue` 语句会立即将程序流返回到由 `for` 、 `foreach` 、 `do` 或语句控制的最内层循环的顶部 `while` 。 循环的当前迭代已终止，循环将继续进行下一次迭代。

在以下示例中， `while` 如果变量等于5，则程序流返回到循环的顶部 `$ctr` 。 因此，会显示1到10之间的所有数字，但5除外：

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

使用循环时 `for` ，将继续执行 `<Repeat>` 语句，然后执行 `<Condition>` 测试。 在下面的示例中，不会发生无限循环，因为减量 `$i` 发生在关键字之后 `continue` 。

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>在循环中使用标签为 continue

标记 `continue` 语句终止迭代的执行，并将控制权移交给目标封闭迭代或 `switch` 语句标签。

在下面的示例中， `for` 当为 True 时，最内层终止， `$condition` 迭代将在处继续执行第二个 `for` 循环 `labelB` 。

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>在 switch 语句中使用 continue

中的未标记 `continue` 语句 `switch` 终止当前迭代的执行 `switch` ，并将控制转移到的顶部 `switch` 以获取下一个输入项。

当存在单个输入项时，将 `continue` 退出整个 `switch` 语句。
当 `switch` 输入为集合时，会 `switch` 测试集合中的每个元素。 `continue`退出当前迭代，并 `switch` 继续下一个元素。

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>在 trap 语句中使用 continue

如果在正文中执行的最后一条语句 `trap` 是语句 `continue` ，则捕获错误将以无提示方式忽略，并继续执行导致发生的语句 `trap` 。

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>请勿在循环、开关或陷阱外使用 continue

如果在 `continue` 直接支持 (循环、) 的构造之外使用，则 `switch` `trap` PowerShell 将查找封闭构造 _的调用堆栈_ 。 如果找不到封闭构造，则当前的运行空间将不知不觉地终止。

这意味着，如果函数和脚本无意中使用了 `continue` 支持它的封闭构造之外的，则可能会无意中终止其 _调用方_。

在 `continue` 管道内使用（如 `ForEach-Object` 脚本块），不仅会退出管道，还可能终止整个运行空间。

## <a name="see-also"></a>另请参阅

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
