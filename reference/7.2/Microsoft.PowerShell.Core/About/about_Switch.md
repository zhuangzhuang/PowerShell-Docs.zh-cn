---
description: 说明如何使用开关来处理多个 `If` 语句。
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 5ca12fe1d5052c1589c5dfecca8cf08cf68901e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598080"
---
# <a name="about-switch"></a>关于交换机

## <a name="short-description"></a>简短说明
说明如何使用开关来处理多个 `If` 语句。

## <a name="long-description"></a>长说明

若要检查脚本或函数中的条件，请使用 `If` 语句。 `If`语句可以检查多种类型的条件，包括变量的值和对象的属性。

若要检查多个条件，请使用 `Switch` 语句。 `Switch`语句等效于一系列 `If` 语句，但它更简单。 `Switch`语句列出每个条件和一个可选操作。 如果条件获得，则执行该操作。

`Switch`语句可以使用 `$_` 和 `$switch` 自动变量。 有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

基本 `Switch` 语句具有以下格式：

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

例如，下面的 `Switch` 语句将测试值3与每个条件进行比较。 如果测试值与条件匹配，则执行操作。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

在这个简单的示例中，将值与列表中的每个条件进行比较，即使存在值3的匹配项。 以下 `Switch` 语句的值为3的两个条件。 它说明默认情况下，测试所有条件。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

若要指示在 `Switch` 匹配后停止比较，请使用 `Break` 语句。 `Break`语句终止 `Switch` 语句。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

如果测试值是一个集合（如数组），则集合中的每一项都按其出现的顺序进行计算。 下面的示例计算4，then 2。

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

任何 `Break` 语句都适用于集合，而不是每个值，如下面的示例中所示。 `Switch`语句由 `Break` 值4的条件中的语句终止。

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>语法

完整的 `Switch` 语句语法如下所示：

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

或

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

如果未使用任何参数， `Switch` 行为与使用 **确切** 参数相同。 它对值执行不区分大小写的匹配。 如果值是集合，则按其显示顺序对每个元素进行计算。

`Switch`语句必须包含至少一个条件语句。

`Default`当值与任何条件都不匹配时，将触发子句。 它等效于 `Else` 语句中的子句 `If` 。 `Default`每个语句中只允许使用一个子句 `Switch` 。

`Switch` 具有以下参数：

- **通配符** -指示条件为通配符字符串。 如果 match 子句不是字符串，则忽略该参数。 比较不区分大小写。
- **Exact** -指示 match 子句（如果它是字符串）必须完全匹配。 如果 match 子句不是字符串，则忽略此参数。 比较不区分大小写。
- **CaseSensitive** -执行区分大小写的匹配。 如果 match 子句不是字符串，则忽略此参数。
- **File**-从文件而不是值语句获取输入。 如果包括多个 **文件** 参数，则只使用最后一个。 该文件的每一行都由语句读取和计算 `Switch` 。 比较不区分大小写。
- **Regex** -执行与条件的值的正则表达式匹配。 如果 match 子句不是字符串，则忽略此参数。
  比较不区分大小写。 `$matches`自动变量可在匹配语句块中使用。

> [!NOTE]
> 指定冲突的值（如 **Regex** 和 **通配符**）时，最后指定的参数优先，并忽略所有冲突参数。 还允许使用多个参数实例。 但是，只有最后使用的参数才有效。

在此示例中，不是字符串或数字数据的对象将传递到 `Switch` 。 对 `Switch` 对象执行字符串强制，并计算结果。

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

在此示例中，没有匹配大小写，因此没有任何输出。

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

通过添加 `Default` 子句，可以在没有其他条件成功时执行操作。

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

若要使词 "十四" 匹配大小写，必须使用 `-Wildcard` 或 `-Regex` 参数。

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

下面的示例使用 `-Regex` 参数。

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

Switch 语句条件可以是：

- 其值与输入值进行比较的表达式
- 满足条件时应返回的脚本块 `$true` 。

`$_`自动变量包含传递给 switch 语句的值，可用于在 condition 语句的范围内进行计算和使用。

每个条件的操作与其他条件中的操作无关。

下面的示例演示如何将脚本块用作 `Switch` 语句条件。

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

如果该值与多个条件匹配，则将执行每个条件的操作。 若要更改此行为，请使用 `Break` 或 `Continue` 关键字。

`Break`关键字将停止处理并退出 `Switch` 语句。

`Continue`关键字将停止处理当前值，但会继续处理所有后续值。

下面的示例处理一个数字数组，如果它们是奇数或偶数，则显示它。 将跳过带有关键字的负数 `Continue` 。 如果遇到非数字，则使用关键字终止执行 `Break` 。

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>请参阅

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
