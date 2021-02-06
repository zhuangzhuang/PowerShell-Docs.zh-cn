---
description: 整数和实数可以具有类型和乘数后缀。
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于数字文本
ms.openlocfilehash: 0e4081c7601928ce9b74010ea3c86762902ca97a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598869"
---
# <a name="about-numeric-literals"></a>关于数字文本

有两种类型的数值：整数和实数。 两者都可以具有类型和乘数后缀。

## <a name="integer-literals"></a>整数文本

整数文本可以用十进制、十六进制或二进制表示法来编写。
十六进制文本的前面加上前缀 `0x` ，二进制文本带有前缀， `0b` 以将它们与十进制数区分开来。

整数文本可以具有类型后缀和乘数后缀。

| Suffix |            含义             |          注意           |
| ------ | ------------------------------ | ----------------------- |
| y      | 带符号字节数据类型          | 在 PowerShell 6.2 中添加 |
| uy     | 无符号 byte 数据类型        | 在 PowerShell 6.2 中添加 |
| s      | Short 数据类型                | 在 PowerShell 6.2 中添加 |
| us     | 无符号 short 数据类型       | 在 PowerShell 6.2 中添加 |
| l      | long 数据类型                 |                         |
| u      | 无符号 int 或 long 数据类型 | 在 PowerShell 6.2 中添加 |
| ul     | 无符号 long 数据类型        | 在 PowerShell 6.2 中添加 |
| n      | BigInteger 数据类型           | 在 PowerShell 7.0 中添加 |
| kb     | kb 乘数            |                         |
| mb     | 兆字节乘数            |                         |
| 内存     | 千兆字节乘数            |                         |
| tb     | tb 乘数            |                         |
| 容量     | pb 乘数            |                         |

整数文本的类型由其值、类型后缀和数值乘数后缀确定。

对于无类型后缀的整数文本：

- 如果值可以通过类型表示 `[int]` ，则为其类型。
- 否则，如果该值可以由类型表示 `[long]` ，则为其类型。
- 否则，如果该值可以由类型表示 `[decimal]` ，则为其类型。
- 否则，它由类型表示 `[double]` 。

对于类型为后缀的整数文本：

- 如果类型后缀为 `u` ，并且值可由类型表示， `[uint]` 则其类型为 `[uint]` 。
- 如果类型后缀为 `u` ，并且值可由类型表示， `[ulong]` 则其类型为 `[ulong]` 。
- 如果其值可由指定的类型表示，则为其类型。
- 否则，该文本的格式不正确。

## <a name="real-literals"></a>真实文本

实际文本只能用十进制符号编写。 此表示法可以在小数点后包含小数值，使用指数部分包括科学记数法。

指数部分包含一个 "e"，后跟一个可选符号 (+/-) 和一个表示指数的数字。 例如，文本值 `1e2` 等于数值100。

真实文本可以具有类型后缀和乘数后缀。

| Suffix |       含义       |
| ------ | ------------------- |
| d      | decimal 数据类型   |
| kb     | kb 乘数 |
| mb     | 兆字节乘数 |
| 内存     | 千兆字节乘数 |
| tb     | tb 乘数 |
| 容量     | pb 乘数 |

有两种类型的真实文本： double 和 decimal。 它们分别由一个或两个 decimal 类型的后缀表示。 PowerShell 不支持值的文本表示形式 `[float]` 。 双实型文本具有类型 `[double]` 。 Decimal 实型文本具有类型 `[decimal]` 。
Decimal 实文字的小数部分的尾随零非常重要。

如果实际文本中指数部分的数字值 `[double]` 小于支持的最小值，则该 `[double]` 实数文本的值为0。 如果实际文本中指数部分的数字值 `[decimal]` 小于所支持的最小值，则该文本的格式不正确。 如果指数部分的数字或真实文本中的数字 `[double]` `[decimal]` 大于所支持的最大值，则该文本的格式不正确。

> [!NOTE]
> 语法允许双实型文本具有长类型的后缀。
> PowerShell 将此事例视为一个整数文本，其值由类型表示 `[long]` 。 保留此功能是为了向后兼容早期版本的 PowerShell。 但是，不鼓励程序员使用此窗体的整数文本，因为它们可以轻松地遮蔽文本的实际值。 例如， `1.2L` 值为1，值为12，值为 `1.2345e1L` `1.2345e-5L` 0，则不会立即出现这种情况。

## <a name="numeric-multipliers"></a>数值乘数

为方便起见，整数和真实文本可以包含数值乘数，这表示一组常用的一组2的幂。 数值乘数可以用大写或小写字母的任意组合来编写。

乘数后缀可与任何类型后缀结合使用，但必须出现在类型后缀之后。 例如，文字的 `100gbL` 格式不正确，但文字 `100Lgb` 有效。

如果乘数创建的值超出了该后缀指定的数值类型的可能值，则该文本的格式不正确。 例如，文本的 `1usgb` 格式不正确，因为值大于 `1gb` 后缀指定的类型所允许的值 `[ushort]` `us` 。

### <a name="multiplier-examples"></a>乘数示例

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>数值类型加速器

PowerShell 支持以下类型加速器：

| 加速器 |         注意         |           说明            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | 字节 (无符号)                   |
| `[sbyte]`   |                      | 字节 (有符号)                     |
| `[Int16]`   |                      | 16 位整数                   |
| `[short]`   | 别名 `[int16]`  | 16 位整数                   |
| `[UInt16]`  |                      | 16位整数 (无符号)         |
| `[ushort]`  | 别名 `[uint16]` | 16位整数 (无符号)         |
| `[Int32]`   |                      | 32-bit integer                   |
| `[int]`     | 别名 `[int32]`  | 32-bit integer                   |
| `[UInt32]`  |                      | 32位整数 (无符号)         |
| `[uint]`    | 别名 `[uint32]` | 32位整数 (无符号)         |
| `[Int64]`   |                      | 64 位整数                   |
| `[long]`    | 别名 `[int64]`  | 64 位整数                   |
| `[UInt64]`  |                      | 64位整数 (无符号)         |
| `[ulong]`   | 别名 `[uint64]` | 64位整数 (无符号)         |
| `[bigint]`  |                      | 请参阅 [BigInteger 结构][bigint]  |
| `[single]`  |                      | 单精度浮点  |
| `[float]`   | 别名 `[single]` | 单精度浮点  |
| `[double]`  |                      | 双精度浮点  |
| `[decimal]` |                      | 128位浮点           |

> [!NOTE]
> PowerShell 6.2 中添加了以下类型加速器： `[short]` 、 `[ushort]` 、 `[uint]` 和 `[ulong]` 。

## <a name="examples"></a>示例

下表包含几个数字文本示例，并列出它们的类型和值：

|   数字    |    类型    |    值     |
| ----------: | ---------- | -----------: |
|         100 | Int32      |          100 |
|        100u | UInt32     |          100 |
|        100D | 小数    |          100 |
|        100l | Int64      |          100 |
|       100uL | UInt64     |          100 |
|       100us | UInt16     |          100 |
|       100uy | Byte       |          100 |
|        100y | SByte      |          100 |
|         1e2 | Double     |          100 |
|        1. e2 | Double     |          100 |
|       0x1e2 | Int32      |          482 |
|      0x1e2L | Int64      |          482 |
|      0x1e2D | Int32      |         7725 |
|        482D | 小数    |          482 |
|       482gb | Int64      | 517543559168 |
|      482ngb | BigInteger | 517543559168 |
|    0x1e2lgb | Int64      | 517543559168 |
|   0b1011011 | Int32      |           91 |
|     0xFFFFs | Int16      |           -1 |
|  0xFFFFFFFF | Int32      |           -1 |
| -0xFFFFFFFF | Int32      |            1 |
| 0xFFFFFFFFu | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>使用二进制或十六进制数字

如果和仅当指定了后缀，则很大的二进制或十六进制文本可以返回， `[bigint]` 而不是分析失败 `n` 。 即使是范围，也仍会考虑符号位 `[decimal]` ，但是：

- 如果二进制字符串是8位长的整数，则将最高位视为符号位。
- 如果十六进制字符串的长度为8的倍数，则其第一个数字等于8或更高，则该数字被视为负值。

在二进制和十六进制文本上指定无符号后缀将忽略符号位。 例如， `0xFFFFFFFF` 返回 `-1` ，但 `0xFFFFFFFFu` 返回 `[uint]::MaxValue` 4294967295 的。

在 PowerShell 7.1 中，在十六进制文本上使用类型后缀现在将返回该类型的带符号值。 例如，在 PowerShell 7.0 中，表达式将 `0xFFFFs` 返回错误，因为正值对于类型太大 `[int16]` 。
PowerShell 7.1 将此解释为 `-1` `[int16]` 类型。

使用将文本作为前缀 `0` 将绕过此，并被视为无符号。
例如：`0b011111111`。 当使用范围中的文本时，这可能是必需 `[bigint]` 的，因为 `u` 和 `n` 后缀不能组合在一起。

还可以使用前缀来否定二进制和十六进制文本 `-` 。 这可能会导致正数，因为允许使用符号位。

对于 BigInteger 的数字，将接受符号位：

- BigInteger 后缀 hex 将任何文本的高位（长度为8个字符，长度为8个字符）视为符号位。 长度不包括 `0x` 前缀或任何后缀。
- BigInteger 后缀后缀接受96和128个字符的符号位，并在之后每隔8个字符。

### <a name="commands-that-look-like-numeric-literals"></a>类似于数字文本的命令

任何类似于有效数字文本的命令都必须使用 call 运算符 (`&`) 执行，否则它将被解释为数值。 格式不正确的文本与类似的语法 `1usgb` 将导致以下错误：

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

但是，包含无效语法的格式不正确的文本 `1gbus` 将被解释为标准的 bare 字符串，可以在可以调用命令的上下文中将其解释为有效的命令名。

### <a name="access-properties-and-methods-of-numeric-objects"></a>访问数字对象的属性和方法

若要访问数字文本的成员，需要将文本括在括号中。

- 文本不具有小数点
- 小数点后的文本不包含任何数字
- 文本没有后缀

例如，下面的示例将失败：

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

下面的示例工作：

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

前两个示例在不将文本值括在括号中的情况下工作，因为 PowerShell 分析器可以确定数字文本的结束位置和 **GetType** 方法的启动位置。

## <a name="how-powershell-parses-numeric-literals"></a>PowerShell 如何分析数字文本

PowerShell 7.0 7.0 更改了对数字文本进行分析的方式，以实现新功能。

### <a name="parsing-real-numeric-literals"></a>分析真实数值

如果文字包含小数点或电子表示法，则会分析文本字符串的实数。

- 如果存在小数点后缀，则直接放入 `[decimal]` 。
- 否则，分析为， `[Double]` 并对值应用乘数。 然后检查类型后缀并尝试强制转换为适当的类型。
- 如果字符串没有类型后缀，则分析为 `[Double]` 。

### <a name="paring-integer-numeric-literals"></a>配对整数数值

使用以下步骤对整数类型文本进行分析：

1. 确定基数格式
   - 对于二进制格式，分析为 `[BigInteger]` 。
   - 对于十六进制格式， `[BigInteger]` 当值在或范围中时，分析为使用特殊的 casies 以保留原始行为 `[int]` `[long]` 。
   - 如果二进制或十六进制都不是，则通常作为进行分析 `[BigInteger]` 。
2. 在尝试任何强制转换之前应用乘数值，以确保可以正确检查类型界限而不溢出。
3. 检查类型后缀。
   - 检查类型限制并尝试对该类型进行分析。
   - 如果未使用任何后缀，则值将按以下顺序进行边界检查，从而导致第一次成功测试确定数字的类型。
     - `[int]`
     - `[long]`
     - `[decimal]` 仅 (以10为底的文本) 
     - `[double]` 仅 (以10为底的文本) 
   - 如果值不在 `[long]` 十六进制和二进制数的范围内，则分析将失败。
   - 如果值不在 `[double]` 以10为底的整数范围内，则分析将失败。
   - 必须使用后缀显式写入较高的值 `n` ，以将文本分析为 `BigInteger` 。

### <a name="parsing-large-value-literals"></a>分析大值文本

以前，在强制转换为任何其他类型之前，更高的整数值被分析为双精度值。 这会导致更高范围内的精度丢失。 例如：

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

若要避免此问题，你必须以字符串形式编写值，然后转换这些值：

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

在 PowerShell 7.0 中，必须使用 `N` 后缀。

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

还 `[ulong]::MaxValue` `[decimal]::MaxValue` 应使用小数点后缀表示和之间的值 `D` 以保持准确性。 如果没有此后缀，则这些值将 `[Double]` 使用实际分析模式进行分析。

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
