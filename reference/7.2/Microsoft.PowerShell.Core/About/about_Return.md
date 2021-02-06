---
description: 退出当前作用域，它可以是函数、脚本或脚本块。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596664"
---
# <a name="about-return"></a>关于返回

## <a name="short-description"></a>简短说明

退出当前作用域，它可以是函数、脚本或脚本块。

## <a name="long-description"></a>长说明

`return`关键字退出函数、脚本或脚本块。 它可用于在特定点退出范围、返回值，或指示已到达范围的末尾的。

熟悉 C 或 C 语言的用户 \# 可能想要使用 `return` 关键字来使范围的逻辑成为显式的。

在 PowerShell 中，每个语句的结果作为输出返回，即使没有包含 Return 关键字的语句也是如此。 C 或 C 等语言 \# 仅返回由关键字指定的一个或哪些值 `return` 。

> [!NOTE]
> 从 PowerShell 5.0 开始，使用正式语法为定义类添加了用于定义类的语言。  在 PowerShell 类的上下文中，无需从方法输出，只是使用语句指定的内容 `return` 。 可以在 [about_Classes](about_Classes.md)中阅读有关 PowerShell 类的详细信息。

### <a name="syntax"></a>语法

关键字的语法如下所示 `return` ：

```
return [<expression>]
```

`return`关键字可以单独显示，也可以后跟值或表达式，如下所示：

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>示例

下面的示例使用 `return` 关键字在满足条件时在特定的时间点退出函数。 不会将奇数相乘，因为 return 语句会在执行该语句之前退出。

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

在 PowerShell 中，即使未使用关键字，也可以返回值 `return` 。
返回每个语句的结果。 例如，下面的语句返回变量的值 `$a` ：

```powershell
$a
return
```

以下语句还返回值 `$a` ：

```powershell
return $a
```

下面的示例包含一个语句，该语句用于使用户知道函数正在执行计算：

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

"请等待。 正在处理计算 ... "不显示字符串。 相反，会将其分配给 `$a` 变量，如以下示例中所示：

```
PS> $a
Please wait. Working on calculation...
87
```

该函数返回信息性字符串和计算结果，并将其分配给 `$a` 变量。

如果要在函数中显示一条消息，从 PowerShell 5.0 开始，可以使用 `Information` 流。 下面的代码通过将 `Write-Information` cmdlet 用于 `InformationAction` **Continue** 来更正上面的示例。

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>返回值和管道

从脚本块或函数返回集合时，PowerShell 会自动 unrolls 成员，并通过管道一次传递一个成员。 这是因为 PowerShell 的一次性处理。 有关详细信息，请参阅 [about_pipelines](about_pipelines.md)。

下面的示例函数阐释了此概念，该函数返回数字的数组。 函数的输出通过管道传递给 cmdlet， `Measure-Object` 后者对管道中的对象数量进行计数。

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

若要强制脚本块或函数将集合作为单个对象返回到管道，请使用以下两种方法之一：

- 一元数组表达式

  利用一元表达式，你可以将返回值作为单个对象发送到管道，如以下示例中所示。

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output` with **NoEnumerate** 参数。

  你还可以将 `Write-Output` cmdlet 与 **NoEnumerate** 参数一起使用。 下面的示例使用 `Measure-Object` cmdlet 来计算由关键字从示例函数发送到管道的对象 `return` 。

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>请参阅

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Classes](about_Classes.md)

[Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)

