---
description: 介绍如何使用运算符为变量赋值。
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 4e21c9d0f2b0a47cd4db10ee515ceb07548eb971
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598488"
---
# <a name="about-assignment-operators"></a>关于赋值运算符

## <a name="short-description"></a>简短说明
介绍如何使用运算符为变量赋值。

## <a name="long-description"></a>长说明

赋值运算符将一个或多个值分配给变量。 它们可以对赋值前的值执行数字运算。

PowerShell 支持以下赋值运算符。

|操作员|说明                                                  |
|--------|-------------------------------------------------------------|
|=       |将变量的值设置为指定值。         |
|+=      |将变量的值增加指定的值，或 |
|        |将指定值追加到现有值。           |
|-=      |将变量的值降低指定的值。    |
|*=      |将变量的值乘以指定的值，或|
|        |将指定值追加到现有值。           |
|/=      |将变量的值除以指定值。      |
|%=      |将变量的值除以指定的值并   |
|        |然后，将余数 (取模) 赋给该变量。        |
|++      |增加变量、可赋值属性的值，或   |
|        |数组元素1。                                          |
|--      |减小变量、可赋值属性的值，或   |
|        |数组元素1。                                          |

## <a name="syntax"></a>语法

赋值运算符的语法如下所示：

`<assignable-expression>` `<assignment-operator>` `<value>`

可赋值表达式包含变量和属性。 该值可以是单个值、值的数组，也可以是命令、表达式或语句。

递增和递减运算符是一元运算符。 每个都具有前缀和后缀版本。

`<assignable-expression><operator>`
`<operator><assignable-expression>`

可分配的表达式必须是数字，或者必须可以转换为数字。

## <a name="assigning-values"></a>赋值

变量称为存储值的内存空间。 使用赋值运算符将值存储在变量中 `=` 。 新值可以替换变量的现有值，也可以将新值追加到现有值。

基本赋值运算符是等号 `=` `(ASCII 61)` 。 例如，下面的语句将值 PowerShell 赋给 `$MyShell` 变量：

```powershell
$MyShell = "PowerShell"
```

在 PowerShell 中为变量分配值时，如果该变量尚不存在，则将创建它。 例如，以下两个赋值语句中的第一个语句将创建 `$a` 变量，并将值6赋给 `$a` 。 第二个赋值语句将值12赋给 `$a` 。 第一个语句创建新变量。 第二个语句仅更改其值：

```powershell
$a = 6
$a = 12
```

PowerShell 中的变量不具有特定的数据类型，除非你强制转换它们。
当变量只包含一个对象时，该变量将采用该对象的数据类型。 当变量包含一个对象集合时，该变量的数据类型为 System.object。 因此，可以将任何类型的对象分配给集合。 下面的示例演示可以将进程对象、服务对象、字符串和整数添加到变量中，而不会生成错误：

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

由于赋值运算符的 `=` 优先级低于管道运算符 `|` ，因此不需要使用括号将命令管道的结果分配给变量。 例如，以下命令将对计算机上的服务进行排序，然后将已排序的服务分配给 `$a` 变量：

```powershell
$a = Get-Service | Sort-Object -Property name
```

还可以将语句创建的值分配给变量，如下面的示例所示：

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

`$a`如果的值小于零，则此示例将零赋给该变量 `$b` 。 `$b` `$a` 如果的值不小于零，则它将的值分配给 `$b` 。

### <a name="the-assignment-operator"></a>赋值运算符

赋值运算符将 `=` 值分配给变量。 如果该变量已经具有值，则赋值运算符将 `=` 替换该值，而不会发出警告。

以下语句将整数值6赋给 `$a` 变量：

```powershell
$a = 6
```

若要为变量赋值，请将字符串值用引号引起来，如下所示：

```powershell
$a = "baseball"
```

若要将数组 (多个值) 赋给一个变量，请使用逗号分隔这些值，如下所示：

```powershell
$a = "apple", "orange", "lemon", "grape"
```

若要为变量分配哈希表，请在 PowerShell 中使用标准哈希表表示法。 键入一个 at 符号， `@` 后跟用分号分隔的键/值对， `;` 并将其括在大括号中 `{ }` 。 例如，若要为该变量分配一个哈希表 `$a` ，请键入：

```powershell
$a = @{one=1; two=2; three=3}
```

若要为变量指定十六进制值，请在值前面加上 `0x` 。
PowerShell 将 (0x10) 的十六进制值转换为十进制值 (在本例中为 16) 并将该值分配给 `$a` 变量。 例如，若要将0x10 的值分配给 `$a` 变量，请键入：

```powershell
$a = 0x10
```

若要为某个变量分配一个指数值，请键入该根号码、字母 `e` 和一个表示10的倍数的数字。 例如，若要将3.1415 的1000幂赋值给 `$a` 变量，请键入：

```powershell
$a = 3.1415e3
```

PowerShell 还可以将千字节 `KB` 、兆字节 `MB` 和 gb 数转换为 `GB` 字节。 例如，若要为该变量分配 10 kb 值 `$a` ，请键入：

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>赋值 by 加法运算符

加法运算符赋值会 `+=` 递增变量的值，或将指定值追加到现有值。 操作取决于变量是否具有数值类型或字符串类型，以及变量是否包含单个值 (标量) 或 (集合) 的多个值。

`+=`运算符组合了两个操作。 首先，它添加，然后分配。
因此，以下语句是等效的：

```powershell
$a += 2
$a = ($a + 2)
```

当变量包含单个数值时， `+=` 运算符会按运算符右侧的量递增现有值。 然后，运算符将生成的值分配给变量。 下面的示例演示如何使用 `+=` 运算符增加变量的值：

```powershell
$a = 4
$a += 2
$a
```

```
6
```

当变量的值是一个字符串时，运算符右侧的值将追加到字符串，如下所示：

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

当变量的值为数组时， `+=` 运算符将运算符右侧的值追加到数组中。 除非通过强制转换来显式键入数组，否则可将任何类型的值追加到数组，如下所示：

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

和

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

当变量的值是一个哈希表时， `+=` 运算符将运算符右侧的值追加到哈希表中。 但是，因为可以添加到哈希表中的唯一类型是另一个哈希表，所有其他赋值都将失败。

例如，下面的命令将一个哈希表分配给该 `$a` 变量。
然后，它使用 `+=` 运算符将其他哈希表追加到现有哈希表，从而有效地将新的键/值对添加到现有哈希表中。
此命令成功，如输出中所示：

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

以下命令尝试将整数 "1" 追加到变量中的哈希表 `$a` 。 此命令失败：

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>通过减法运算符赋值

通过减法运算符赋值， `-=` 按运算符右侧指定的值递减变量的值。 此运算符不能与字符串变量一起使用，并且不能用于从集合中移除元素。

`-=`运算符组合了两个操作。 首先，它减去，然后分配。 因此，以下语句是等效的：

```powershell
$a -= 2
$a = ($a - 2)
```

下面的示例演示如何使用 `-=` 运算符来减小变量的值：

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

还可以使用 `-=` 赋值运算符来减小数值数组成员的值。 为此，请指定要更改的数组元素的索引。 在下面的示例中，数组的第三个元素的值 (元素 2) 减1：

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

不能使用 `-=` 运算符来删除变量的值。 若要删除分配给变量的所有值，请使用 " [清除项](xref:Microsoft.PowerShell.Management.Clear-Item) " 或 " [清除变量](xref:Microsoft.PowerShell.Utility.Clear-Variable) " cmdlet 将或的值分配 `$null` 给 `""` 变量。

```powershell
$a = $null
```

若要从数组中删除某个特定值，请使用数组表示法将值分配给 `$null` 特定项。 例如，下面的语句从数组中删除索引位置 1)  (第二个值：

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

若要删除某个变量，请使用 " [删除变量](xref:Microsoft.PowerShell.Utility.Remove-Variable) " cmdlet。 当变量显式转换为特定数据类型，并且您需要非类型化的变量时，此方法非常有用。 以下命令删除 `$a` 变量：

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>乘法运算符赋值

乘法运算符的赋值将 `*=` 数值相乘，或追加变量的字符串值的指定副本数。

当变量包含单个数值时，该值将乘以运算符右侧的值。 例如，下面的示例演示如何使用 `*=` 运算符将变量的值相乘：

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

在这种情况下， `*=` 运算符组合了两个操作。 首先，它将相乘，然后分配。 因此，以下语句是等效的：

```powershell
$a *= 2
$a = ($a * 2)
```

当变量包含字符串值时，PowerShell 会将指定数量的字符串追加到值，如下所示：

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

若要相乘数组的元素，请使用索引来标识要相乘的元素。 例如，以下命令将数组中的第一个元素乘以 (索引位置 0) 2：

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>按除法运算符赋值

按除法运算符赋值 `/=` 可将数值除以运算符右侧指定的值。 运算符不能与字符串变量一起使用。

`/=`运算符组合了两个操作。 首先，它将除以，然后分配。 因此，下面两个语句是等效的：

```powershell
$a /= 2
$a = ($a / 2)
```

例如，下面的命令使用 `/=` 运算符来除以变量的值：

```powershell
$a = 8
$a /=2
$a
```

```
4
```

若要拆分数组的元素，请使用索引来标识要更改的元素。 例如，下面的命令将数组中的第二个元素除以 (索引位置 1) 2：

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>取模运算符赋值

取模运算符赋值会将 `%=` 变量的值除以运算符右边的值。 然后， `%=` 运算符将 (称为取模) 分配给变量。 仅当变量包含单个数值时，才能使用此运算符。 当变量包含字符串变量或数组时，不能使用此运算符。

`%=`运算符组合了两个操作。 首先，它会分割并确定余数，然后将余数赋给该变量。 因此，以下语句是等效的：

```powershell
$a %= 2
$a = ($a % 2)
```

下面的示例演示如何使用 `%=` 运算符保存商的模数：

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>递增和递减运算符

递增运算符将 `++` 变量的值增加1。 在简单语句中使用递增运算符时，不返回任何值。 若要查看结果，请显示变量的值，如下所示：

```powershell
$a = 7
++$a
$a
```

```
8
```

若要强制返回值，请将变量和运算符括在括号中，如下所示：

```powershell
$a = 7
(++$a)
```

```
8
```

递增运算符可以放置在 (前缀) 之前，也可以放在 (后缀) 变量之后。 在语句中使用变量之前，该运算符的前缀版本会递增变量，如下所示：

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

在语句中使用变量值后，该运算符的后缀版本会递增该变量。 在下面的示例中， `$c` 和 `$a` 变量具有不同的值，因为在进行更改之前将值分配给 `$c` `$a` ：

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

减量运算符将 `--` 变量的值减少1。 与递增运算符一样，在简单语句中使用运算符时不返回任何值。 使用括号返回值，如下所示：

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

在语句中使用变量之前，该运算符的前缀版本会递减变量，如下所示：

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

在语句中使用变量值后，该运算符的后缀版本会递减变量。 在下面的示例中， `$d` 和 `$a` 变量具有不同的值，因为在进行更改之前将值分配给 `$d` `$a` ：

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Microsoft .NET Framework 类型

默认情况下，当变量只有一个值时，赋给变量的值将确定该变量的数据类型。 例如，以下命令将创建一个具有 "Integer" () 类型的变量：

```powershell
$a = 6
```

若要查找变量的 .NET Framework 类型，请使用 **GetType** 方法及其 **FullName** 属性，如下所示。 请确保在 **GetType** 方法名称后面加上括号，即使方法调用没有参数：

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

若要创建包含字符串的变量，请为该变量分配一个字符串值。 若要指示值为字符串，请将其括在引号中，如下所示：

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

如果分配给变量的第一个值为字符串，则 PowerShell 会将所有操作视为字符串操作，并将新值转换为字符串。
在以下示例中，会发生这种情况：

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

如果第一个值是整数，则 PowerShell 会将所有操作视为整数操作，并将新值转换为整数。 在以下示例中，会发生这种情况：

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

可以通过将类型名称放在变量名称或第一个赋值值之前的方括号中，将新的标量变量转换为任意 .NET Framework 类型。 转换变量时，可以确定变量中可以存储的数据的类型。 而且，您可以在操作变量时确定变量的行为方式。

例如，以下命令将变量强制转换为字符串类型：

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

下面的示例将转换第一个值，而不是强制转换变量：

```powershell
$a = [string]27
```

将变量强制转换为特定类型时，常见的约定是强制转换变量，而不是转换值。 但是，如果不能将现有变量的值转换为新的数据类型，则不能重塑该变量的数据类型。 若要更改数据类型，必须替换其值，如下所示：

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

此外，在使用数据类型的变量名称前面之前，该变量的类型将被锁定，除非通过指定另一种数据类型显式重写该类型。 如果尝试分配的值与现有的类型不兼容，并且不显式重写该类型，则 PowerShell 会显示错误，如以下示例中所示：

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

在 PowerShell 中，在数组中包含多个项的变量的数据类型的处理方式与包含单个项的变量的数据类型不同。 除非将数据类型专门赋给数组变量，否则数据类型始终为 `System.Object []` 。 此数据类型特定于数组。

有时，可以通过指定其他类型来重写默认类型。 例如，以下命令将变量强制转换为 `string []` 数组类型：

```powershell
[string []] $a = "one", "two", "three"
```

PowerShell 变量可以是任何 .NET Framework 数据类型。 此外，您可以分配在当前过程中可用的任何完全限定的 .NET Framework 数据类型。 例如，以下命令指定了 `System.DateTime` 数据类型：

```powershell
[System.DateTime]$a = "5/31/2005"
```

将为该变量分配一个符合数据类型的值 `System.DateTime` 。 变量的值将 `$a` 如下所示：

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>分配多个变量

在 PowerShell 中，可以使用单个命令将值分配给多个变量。 赋值值的第一个元素分配给第一个变量，第二个元素分配给第二个变量，第三个元素分配给第三个变量，依此类推。 例如，以下命令将值1赋给 `$a` 变量，将值2赋给变量，将值3赋给 `$b` `$c` 变量：

```powershell
$a, $b, $c = 1, 2, 3
```

如果分配值包含的元素多于变量，则所有剩余的值都将分配给最后一个变量。 例如，下面的命令包含三个变量和五个值：

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

因此，PowerShell 将值1赋给 `$a` 变量，将值2赋给该 `$b` 变量。 它将值3、4和5分配给 `$c` 变量。
若要将变量中的值分配 `$c` 给其他三个变量，请使用以下格式：

```powershell
$d, $e, $f = $c
```

此命令将值3赋给 `$d` 变量，将值4赋给变量 `$e` ，将值5赋给该 `$f` 变量。

如果赋值值所包含的元素少于变量，则不会为末尾的所有剩余变量分配任何值。 例如，下面的命令包含三个变量和两个值：

```powershell
$a, $b, $c = 1, 2
```

因此，PowerShell 将值1赋给 `$a` 变量，将值2赋给该 `$b` 变量。 它不会将任何值分配给 `$c` 变量。

还可以通过链接变量将单个值分配给多个变量。 例如，以下命令将值 "3" 赋给所有四个变量：

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>与变量相关的 cmdlet

除了使用赋值运算设置变量值以外，还可以使用 " [变量集](xref:Microsoft.PowerShell.Utility.Set-Variable) " cmdlet。 例如，下面的命令使用将 `Set-Variable` 1，2，3的数组分配给 `$a` 变量。

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>请参阅

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)

