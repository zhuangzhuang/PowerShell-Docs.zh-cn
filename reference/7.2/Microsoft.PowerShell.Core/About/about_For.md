---
description: 描述可用于根据条件测试运行语句的语言命令。
Locale: en-US
ms.date: 03/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 3f86505d60837e8e5fa4938092a48eeb10833560
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597666"
---
# <a name="about-for"></a>关于

## <a name="short-description"></a>简短说明
描述可用于根据条件测试运行语句的语言命令。

## <a name="long-description"></a>长说明

`For`语句 (也称为 `For` 循环) 是一种语言构造，可用于创建在指定条件的计算结果为时在命令块中运行命令的循环 `$true` 。

循环的典型用途 `For` 是循环访问值的数组，并对这些值的子集进行运算。 在大多数情况下，如果要对数组中的所有值进行迭代，请考虑使用 `Foreach` 语句。

### <a name="syntax"></a>语法

下面显示了 `For` 语句语法。

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

**Init** 占位符表示在循环开始之前运行的一个或多个命令。 通常使用语句的 **Init** 部分来创建和初始化具有起始值的变量。

然后，此变量将成为该语句的下一部分中要测试的条件的基础 `For` 。

**条件** 占位符表示 `For` 语句中解析为 `$true` 或 `$false` **布尔** 值的部分。 PowerShell 将在每次循环运行时评估条件 `For` 。 如果语句为 `$true` ，则命令块中的命令将运行，并再次计算语句。 如果条件仍为 `$true` ， **语句列表** 中的命令将再次运行。 循环将重复，直到该条件变为 `$false` 。

**重复** 占位符表示一个或多个以逗号分隔的命令，这些命令在每次循环重复时执行。 通常，这用于修改在语句的 **条件** 部分内测试的变量。

**语句列表** 占位符表示在每次输入或重复循环时运行的一个或多个命令集。 **语句列表** 的内容括在大括号中。

### <a name="support-for-multiple-operations"></a>支持多个操作

**Init** 语句中的多个赋值操作支持以下语法：

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

**重复** 语句中的多个赋值操作支持以下语法：

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> 除 pre 或 post 以外的其他操作可能不适用于所有语法。

对于多个 **条件** 使用逻辑运算符，如下面的示例所示。

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

有关详细信息，请参阅 [about_Logical_Operators](about_Logical_Operators.md)。

### <a name="examples"></a>示例

至少，语句要求在语句的 `For` 语句列表部分中，语句的 **Init**、 **Condition** 和 **Repeat** 部分以及括在语句的 **语句列表** 部分中的命令使用括号。

请注意，即将出现的示例有意显示语句外部的代码 `For` 。 在后面的示例中，代码集成到 `For` 语句中。

例如，下面的 `For` 语句持续显示变量的值， `$i` 直到你通过按 CTRL + C 手动跳出命令。

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

您可以向语句列表中添加其他命令 `$i` ，以便每次运行该循环时，的值递增1，如下面的示例所示。

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

在您通过按 CTRL + C 跳出命令之前，此语句将持续显示变量的值， `$i` 因为每次运行该循环时，它将递增1。

`For`您可以改为使用语句的 **重复** 部分，而不是在语句的语句列表部分中更改变量的值， `For` 如下所示。

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

此语句仍会无限重复，直到你通过按 CTRL + C 退出命令。

您可以 `For` 使用 *条件* 终止循环。 您可以使用语句的 **条件** 部分来放置条件 `For` 。 `For`当条件的计算结果为时，循环将终止 `$false` 。

在下面的示例中， `For` 当的值 `$i` 小于或等于10时，将运行循环。

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

`For`您可以 `For` 使用语句的 **Init** 部分在循环内执行此任务，而不是在语句外部创建和初始化变量 `For` 。

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

您可以使用回车符而不是分号来分隔语句的 **Init**、 **Condition** 和 **Repeat** 部分 `For` 。 下面的示例演示一个 `For` 使用此替代语法的。

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

该语句的这种替代形式 `For` 适用于 powershell 脚本文件和 powershell 命令提示符。 但是，在 `For` 命令提示符下输入交互命令时，使用带有分号的语句语法会更容易。

`For`循环比循环更灵活， `Foreach` 因为它允许您通过使用模式来递增数组或集合中的值。 在下面的示例中，在 `$i` 语句的 **重复** 部分，变量递增 2 `For` 。

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

`For`还可以在一行上写入循环，如以下示例中所示。

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>另请参阅

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)

