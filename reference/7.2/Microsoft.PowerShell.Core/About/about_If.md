---
description: 描述可用于根据一个或多个条件测试的结果运行语句列表的语言命令。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 04c610af36e17c02d2440ab79b7de5330e5063ab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597259"
---
# <a name="about-if"></a>关于 If

## <a name="short-description"></a>简短说明
描述可用于根据一个或多个条件测试的结果运行语句列表的语言命令。

## <a name="long-description"></a>详细说明

`If`如果指定的条件测试的计算结果为 true，则可以使用语句来运行代码块。 如果所有之前的测试的计算结果都为 false，则还可以指定要运行的一个或多个附加条件测试。 最后，你可以指定一个其他代码块，如果没有其他任何之前的条件测试计算为 true，则会运行该代码块。

### <a name="syntax"></a>语法

下面的示例显示了 `If` 语句语法：

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

运行 `If` 语句时，PowerShell 会将 `<test1>` 条件表达式计算为 true 或 false。 如果 `<test1>` 为 true，则 `<statement list 1>` 运行，并且 PowerShell 将退出 `If` 语句。 如果 `<test1>` 为 false，则 PowerShell 将计算由条件语句指定的条件 `<test2>` 。

如果 `<test2>` 为 true，则 `<statement list 2>` 运行，并且 PowerShell 将退出 `If` 语句。 如果 `<test1>` 和 `<test2>` 的计算结果都为 false，则 `<statement list 3`> 代码块运行，并且 PowerShell 将退出 If 语句。

可以使用多个 Elseif 语句来链接一系列条件测试。 因此，仅当前面的所有测试都为 false 时，才会运行每个测试。
如果需要创建 `If` 包含多个 Elseif 语句的语句，请考虑改为使用 Switch 语句。

示例:

最简单的 `If` 语句包含一个命令，不包含任何 Elseif 语句或任何 Else 语句。 下面的示例显示了语句的最简单形式 `If` ：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

在此示例中，如果 $a 变量大于2，则条件的计算结果为 true，并且语句列表将运行。 但是，如果 $a 小于或等于2或者不是现有的变量，则该语句不 `If` 显示消息。

通过添加 Else 语句，当 $a 小于或等于2时，将显示一条消息。 如下面的示例所示：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

若要进一步优化此示例，可以使用 Elseif 语句在 $a 的值等于2时显示一条消息。 如下面的示例所示：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a>使用三元运算符语法

PowerShell 7.0 使用三元运算符引入了新的语法。 它遵循 c # 三元运算符语法：

```Syntax
<condition> ? <if-true> : <if-false>
```

三元运算符的行为类似于简化 `if-else` 语句。 `<condition>`计算表达式，并将结果转换为布尔值，以确定下一次应计算哪个分支：

- 如果 `<condition>` 表达式为 true，则执行 `<if-true>` 表达式
- 如果 `<condition>` 表达式为 false，则执行 `<if-false>` 表达式

例如：

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

在此示例中，的值在 `$message` 返回时为 "Path exists" `Test-Path` `$true` 。 当 `Test-Path` 返回时 `$false` ，的值 `$message` 为 "找不到路径"。

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

在此示例中，如果服务正在运行，它将停止，如果其状态为 "未在 **运行**"，则启动该服务。

## <a name="see-also"></a>另请参阅

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)

