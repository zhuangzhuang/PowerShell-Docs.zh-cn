---
description: 运行一个或多个语句列表，并根据时间或截止时间。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596657"
---
# <a name="about-do"></a>关于 Do

## <a name="short-description"></a>简短说明
运行一个或多个语句列表，并根据时间或截止时间。

## <a name="long-description"></a>详细说明

Do 关键字适用于 While 关键字或 Until 关键字，用于运行脚本块中的语句（根据条件）。 与相关的 While 循环不同，Do 循环中的脚本块始终运行至少一次。

**Do** 循环是各种 While 循环。 在 **Do** 循环中，将在运行脚本块后计算条件。 与 While 循环一样，只要条件的计算结果为 true，就会重复脚本块。

与 **do** 循环一样， **do Until** 循环始终在计算条件之前至少运行一次。 但是，仅当条件为 false 时，才运行脚本块。

*Continue* 和 *Break* 流控制关键字可以用在 **do** 循环或 **do Until** 循环中。

### <a name="syntax"></a>语法

下面显示了 **Do** 语句的语法：

```powershell
do {<statement list>} while (<condition>)
```

下面显示了 **Do Until** 语句的语法：

```powershell
do {<statement list>} until (<condition>)
```

语句列表包含一个或多个在每次输入或重复循环时运行的语句。

语句的条件部分解析为 true 或 false。

### <a name="example"></a>示例

下面的 Do 语句示例计算数组中的项，直到到达值为0的项。

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

下面的示例使用 Until 关键字。 请注意， () 不等于运算符 `-ne` () 替换为等于运算符 `-eq` 。

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

下面的示例将写入数组的所有值，并跳过任何小于零的值。

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>另请参阅

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

