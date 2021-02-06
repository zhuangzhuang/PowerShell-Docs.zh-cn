---
description: 描述在 PowerShell 中执行算术的运算符。
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 174b3cb72f6b5eb1cc39c4974613d9b9c8dd81a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597681"
---
# <a name="about-arithmetic-operators"></a>关于算术运算符

## <a name="short-description"></a>简短说明
描述在 PowerShell 中执行算术的运算符。

## <a name="long-description"></a>详细说明

算术运算符计算数字值。 您可以使用一个或多个算术运算符对值进行加法、减、乘和除运算，计算除法运算的余数 (模数) 。

此外，加法运算符 (`+`) 和乘法运算符 (`*`) 也操作字符串、数组和哈希表。 加法运算符用于连接输入。 乘法运算符返回输入的多个副本。 甚至可以在算术语句中混合使用对象类型。 用于计算语句的方法由表达式中最左侧的对象的类型确定。

从 PowerShell 2.0 开始，所有算术运算符都适用于64位数字。

从 PowerShell 3.0 开始， `-shr` 添加了 (向右) 和 `-shl` (向左) ，以便在 PowerShell 中支持按位算法。

PowerShell 支持以下算术运算符：

|操作员|说明                       |示例                      |
|--------|----------------------------------|-----------------------------|
| +      |添加整数;各个       |`6 + 2`                      |
|        |字符串、数组和哈希表。 |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |从一个值中减去另一个值  |`6 - 2`                      |
|        |value                             |                             |
| -      |使数字成为负数  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |数字或复制字符串相乘  |`6 * 2`                      |
|        |和数组指定的数字   |`@("!") * 4`                 |
|        |次。                         |`"!" * 3`                    |
| /      |两个值相除。               |`6 / 2`                      |
| %      |取模-返回剩余的|`7 % 2`                      |
|        |除法运算。             |                             |
|-带   |位与                       |`5 -band 3`                  |
|-bnot   |按位“非”                       |`-bnot 5`                    |
|-bor    |按位“或”                        |`5 -bor 0x03`                |
|-bxor   |按位“异或”                       |`5 -bxor 3`                  |
|-shl    |将位向左移动           |`102 -shl 2`                 |
|-shr    |将位向右移位          |`102 -shr 2`                 |

按位运算符仅适用于整数类型。

## <a name="operator-precedence"></a>运算符优先级

PowerShell 按以下顺序处理算术运算符：

|优先级|操作员          |说明                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |括号                            |
|2         | `-`              |对于负数或一元运算符|
|3         | `*`, `/`, `%`    |对于乘法和除法        |
|4         | `+`, `-`         |对于加法和减法           |
|5         | `-band`, `-bnot` |对于按位运算                 |
|5         | `-bor`, `-bxor`  |对于按位运算                 |
|5         | `-shr`, `-shl`   |对于按位运算                 |

根据优先级规则，PowerShell 从左到右处理表达式。 以下示例显示了优先规则的效果：

|表达式 |结果|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

PowerShell 计算表达式的顺序可能不同于你使用的其他编程和脚本语言。 下面的示例演示了复杂的赋值语句。

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

在此示例中，对表达式 `$a++` 进行计算 `$b[$a]` 。
在 `$a++` `$a` 语句中使用之后，计算更改的值， `$c[$a++]` 但在中使用它之前 `$b[$a]` 。 中的 `$a` 变量 `$b[$a]` 等于 `1` ，而不是 `0` ; 因此，语句将值赋给 `$b[1]` ，而不是 `$b[0]` 。

上述代码等效于：

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>相除和舍入

当除法运算的商是整数时，PowerShell 会将值舍入到最接近的整数。 如果值为 `.5` ，则它将舍入到最接近的偶数。

下面的示例演示舍入到最接近的偶数的效果。

|表达式      |结果|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

请注意 **_5/2_ = 2.5** 舍入到 **2** 的方式。 但 **_7/2_ = 3.5** 舍入为 **4**。

您可以使用 `[Math]` 类来获取不同的舍入行为。

|                          表达式                          | 结果 |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

有关详细信息，请参阅 [Math](/dotnet/api/system.math.round) 方法。

## <a name="adding-and-multiplying-non-numeric-types"></a>添加非数值类型和相乘

可以添加数字、字符串、数组和哈希表。 而且，您可以将数字、字符串和数组相乘。 但是，不能将哈希表相乘。

添加字符串、数组或哈希表时，这些元素将连接在一起。 当连接集合（如数组或哈希表）时，将创建一个新的对象，该对象包含两个集合中的对象。 如果尝试连接具有相同键的哈希表，则操作将失败。

例如，下面的命令创建两个数组，然后添加它们：

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

您还可以对不同类型的对象执行算术运算。
PowerShell 执行的操作由操作中最左边对象的 Microsoft .NET 框架类型决定。 PowerShell 尝试将操作中的所有对象转换为第一个对象的 .NET Framework 类型。 如果它成功转换了对象，它将执行适用于第一个对象的 .NET Framework 类型的操作。 如果无法转换任何对象，操作将失败。

下面的示例演示加法和乘法运算符的用法;在包含不同对象类型的操作中。 假定 `$array = 1,2,3` ：

|表达式       |结果                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

因为用于计算语句的方法由最左端的对象确定，所以 PowerShell 中的加法和乘法并不完全是可交换的。 例如，并不 `(a + b)` 总是相等 `(b + a)` ，并且不 `(ab)` 始终相等 `(ba)` 。

下面的示例演示了这一原则：

|表达式   |结果                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "file"                                       |

哈希表的大小写略有不同。 您可以将哈希表添加到另一个哈希表，前提是已添加的哈希表没有重复键。

下面的示例演示如何向彼此添加哈希表。

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

下面的示例引发错误，因为这两个哈希表中的一个键重复。

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

此外，还可以将哈希表添加到数组;而且，整个哈希表将成为数组中的项。

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

但是，不能将任何其他类型添加到哈希表。

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

虽然加法运算符非常有用，但使用赋值运算符将元素添加到哈希表和数组。 有关详细信息，请参阅 [about_assignment_operators](about_Assignment_Operators.md)。 下面的示例使用 `+=` 赋值运算符将项添加到数组中：

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>用于容纳结果的类型转换

PowerShell 会自动选择最能表达结果的 .NET Framework 数值类型，而不会丢失精度。 例如：

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

如果操作的结果对于类型太大，则结果的类型会扩大以容纳结果，如以下示例中所示：

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

结果的类型不一定与操作数之一相同。 在下面的示例中，负值不能转换为无符号整数，且无符号整数太大，无法强制转换为 `Int32` ：

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

在此示例中， `Int64` 可以同时容纳这两种类型。

`System.Decimal`类型为异常。 如果任一操作数具有 Decimal 类型，则结果将为 Decimal 类型。 如果结果对 Decimal 类型来说太大，则不会将其强制转换为 Double 类型。 相反，会产生错误。

|表达式               |结果                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>算术运算符和变量

还可以对变量使用算术运算符。 运算符作用于变量的值。 下面的示例演示如何对变量使用算术运算符：

| 表达式                                    |结果      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>算术运算符和命令

通常，可以在表达式中使用数字、字符串和数组的算术运算符。 但是，还可以将算术运算符与命令返回的对象以及这些对象的属性一起使用。

下面的示例演示如何在表达式中通过 PowerShell 命令使用算术运算符：

```powershell
(get-date) + (new-timespan -day 1)
```

圆括号运算符 `get-date` 按顺序强制对 cmdlet 和 cmdlet 表达式的计算进行计算 `new-timespan -day 1` 。 然后使用运算符添加两个结果 `+` 。

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

在上述表达式中， () 的每个进程工作空间 `$_.ws` 都将乘以 `2` ; 与结果相比， `50mb` 它们是否大于该值。

## <a name="bitwise-operators"></a>位运算符

PowerShell 支持标准按位运算符，包括按位与 (`-bAnd`) 、 (和) 的非独占和独占按位或运算符 `-bOr` 和 `-bXor` 以及按位 "非 () `-bNot` 。

从 PowerShell 2.0 开始，所有位运算符都适用于64位整数。

从 PowerShell 3.0 开始， `-shr` 会引入 (向右) 和 `-shl` (左移) ，以支持在 PowerShell 中进行按位运算。

PowerShell 支持以下按位运算符。

| 操作员 | 说明            | 表达式   | 结果 |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | 位与            | `10 -band 3` | 2      |
| `-bor`   | 按位 OR (包含)  | `10 -bor 3`  | 11     |
| `-bxor`  | 按位或 (独占)  | `10 -bxor 3` | 9      |
| `-bnot`  | 按位“非”            | `-bNot 10`   | -11    |
| `-shl`   | 左移             | `102 -shl 2` | 408    |
| `-shr`   | 向右移动            | `102 -shr 1` | 51     |

位运算符作用于值的二进制格式。 例如，数字10的位结构为 00001010 (基于1个字节) ，数字3的位结构是00000011。 当使用位运算符将10与3进行比较时，将比较每个字节中的单个位。

在按位 "与" 运算中，只有当两个输入位均为1时，才将生成的位设置为1。

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

在按位 "或" (包含) "操作中，如果其中一个或两个输入位均为1，则生成的位将设置为1。 仅当两个输入位均设置为0时，结果位设置为0。

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

在按位或 (独占) 操作中，仅当一个输入位为1时，结果位将设置为1。

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

按位 "非" 运算符是一个一元运算符，该运算符产生值的二进制补码。 1的位设置为0，位0设置为1。

例如，0的二进制反码为-1，最大无符号整数 (0xffffffff) ，二进制补码-1 为0。

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

在按位左移操作时，所有位都向左移动 "n"，其中 "n" 是右操作数的值。 在一个位置插入零。

当左操作数是一个整数 (32 位) 值时，右操作数的下5位将确定左操作数的位移位数。

当左操作数为长 (64 位) 值时，右操作数的低6位确定左操作数的偏移量。

|表达式 |结果|二进制结果|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

在按位右移操作中，所有位都将 "n" 向右移动，其中 "n" 由右操作数指定。 向右移动运算符 (-shr) 在将正或无符号值向右移位时，将在最左侧插入零。

当左操作数是一个整数 (32 位) 值时，右操作数的下5位将确定左操作数的位移位数。

当左操作数为长 (64 位) 值时，右操作数的低6位确定左操作数的偏移量。

|表达式              |结果      |二进制     |Hex         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| -1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | 0xFFFFFFFF |

## <a name="see-also"></a>另请参阅

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [获取日期](xref:Microsoft.PowerShell.Utility.Get-Date)
- [New-TimeSpan](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
