---
description: 介绍如何创建和使用引用类型变量。 您可以使用引用类型变量来允许函数更改传递给它的变量的值。
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 5b966816c8ac1ef91e03c78378f57fa20b5697de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595627"
---
# <a name="about-ref"></a>关于 Ref

## <a name="short-description"></a>简短说明
介绍如何创建和使用引用类型变量。 您可以使用引用类型变量来允许函数更改传递给它的变量的值。

## <a name="long-description"></a>长说明

可以 *通过引用* 或 *值* 将变量传递给函数。

*通过值* 传递变量时，将传递数据的副本。

在下面的示例中，函数更改传递给它的变量的值。 在 PowerShell 中，整数是值类型，因此按值传递它们。
因此，的值在 `$var` 函数作用域之外保持不变。

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

在下面的示例中，将包含的变量 `Hashtable` 传递到函数。 `Hashtable` 对象类型，因此默认情况下，它 *通过引用* 传递给函数。

当 *通过引用* 传递变量时，函数可以更改数据，并且更改会在函数执行后保持不变。

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

函数添加新的键/值对，它保留在函数范围之外。

### <a name="writing-functions-to-accept-reference-parameters"></a>编写函数以接受引用参数

无论传递的数据类型如何，都可以将函数编码为采用参数作为参考。 这需要将参数类型指定为 `System.Management.Automation.PSReference` 或 `[ref]` 。

使用引用时，必须使用类型的 `Value` 属性 `System.Management.Automation.PSReference` 来访问数据。

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

若要将变量传递给需要引用的参数，必须键入 cast 作为引用。

> [!NOTE]
> 需要括号和括号。

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>向 .NET 方法传递引用

某些 .NET 方法可能要求您将变量作为引用传递。 当方法的定义在 `in` 参数上使用关键字、 `out` 或时 `ref` ，它需要引用。

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

此 `TryParse` 方法尝试将字符串分析为一个整数。 如果该方法成功，则返回 `$true` ，并将结果存储在 **通过引用** 传递的变量中。

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>引用和范围

引用允许在子作用域内更改父作用域中的变量的值。

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

仅更改了引用类型的变量。

## <a name="see-also"></a>请参阅

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)

