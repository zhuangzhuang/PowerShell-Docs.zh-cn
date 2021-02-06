---
description: 描述在 PowerShell 中连接语句的运算符。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595604"
---
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>简短说明
描述在 PowerShell 中连接语句的运算符。

## <a name="long-description"></a>详细说明

PowerShell 逻辑运算符连接表达式和语句，允许使用单个表达式来测试多个条件。

例如，下面的语句使用 and 运算符和 or 运算符连接三个条件语句。 仅当 $a 的值大于 $b 的值并且 $a 或 $b 小于时，语句才为 true
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

PowerShell 支持以下逻辑运算符。

|操作员|说明                        |示例                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |逻辑 AND。 如果两者都为 TRUE        |`(1 -eq 1) -and (1 -eq 2)`|
|        |语句为 TRUE。               |`False`                   |
|`-or`   |逻辑 OR。 如果为 TRUE       |`(1 -eq 1) -or (1 -eq 2)` |
|        |语句为 TRUE。                 |`True`                    |
|`-xor`  |逻辑异或。 如果    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |只有一个语句为 TRUE         |`False`                   |
|`-not`  |逻辑非。 对语句求反 |`-not (1 -eq 1)`          |
|        |如下所示。                      |`False`                   |
|`!`     |与 `-not` 相同                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 注意：

前面的示例还使用了等于比较运算符 `-eq` 。 有关详细信息，请参阅 [about_Comparison_Operators](about_Comparison_Operators.md)。 这些示例还使用整数的布尔值。 整数0的值为 FALSE。 所有其他整数的值均为 TRUE。

逻辑运算符的语法如下所示：

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

使用逻辑运算符的语句将返回布尔值 (TRUE 或 FALSE) 值。

PowerShell 逻辑运算符只计算确定语句的真假值所需的语句。 如果包含 and 运算符的语句中的左操作数为 FALSE，则不计算右操作数。
如果包含或语句的语句中的左操作数为 TRUE，则不计算右操作数。 因此，您可以使用这些语句，与使用语句的方式相同 `If` 。

## <a name="see-also"></a>另请参阅

[about_Operators](about_Operators.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)

