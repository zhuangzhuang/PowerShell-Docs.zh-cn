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
# <a name="about-arithmetic-operators"></a><span data-ttu-id="384fa-103">关于算术运算符</span><span class="sxs-lookup"><span data-stu-id="384fa-103">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="384fa-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="384fa-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="384fa-105">描述在 PowerShell 中执行算术的运算符。</span><span class="sxs-lookup"><span data-stu-id="384fa-105">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="384fa-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="384fa-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="384fa-107">算术运算符计算数字值。</span><span class="sxs-lookup"><span data-stu-id="384fa-107">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="384fa-108">您可以使用一个或多个算术运算符对值进行加法、减、乘和除运算，计算除法运算的余数 (模数) 。</span><span class="sxs-lookup"><span data-stu-id="384fa-108">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="384fa-109">此外，加法运算符 (`+`) 和乘法运算符 (`*`) 也操作字符串、数组和哈希表。</span><span class="sxs-lookup"><span data-stu-id="384fa-109">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="384fa-110">加法运算符用于连接输入。</span><span class="sxs-lookup"><span data-stu-id="384fa-110">The addition operator concatenates the input.</span></span> <span data-ttu-id="384fa-111">乘法运算符返回输入的多个副本。</span><span class="sxs-lookup"><span data-stu-id="384fa-111">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="384fa-112">甚至可以在算术语句中混合使用对象类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-112">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="384fa-113">用于计算语句的方法由表达式中最左侧的对象的类型确定。</span><span class="sxs-lookup"><span data-stu-id="384fa-113">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="384fa-114">从 PowerShell 2.0 开始，所有算术运算符都适用于64位数字。</span><span class="sxs-lookup"><span data-stu-id="384fa-114">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="384fa-115">从 PowerShell 3.0 开始， `-shr` 添加了 (向右) 和 `-shl` (向左) ，以便在 PowerShell 中支持按位算法。</span><span class="sxs-lookup"><span data-stu-id="384fa-115">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="384fa-116">PowerShell 支持以下算术运算符：</span><span class="sxs-lookup"><span data-stu-id="384fa-116">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="384fa-117">操作员</span><span class="sxs-lookup"><span data-stu-id="384fa-117">Operator</span></span>|<span data-ttu-id="384fa-118">说明</span><span class="sxs-lookup"><span data-stu-id="384fa-118">Description</span></span>                       |<span data-ttu-id="384fa-119">示例</span><span class="sxs-lookup"><span data-stu-id="384fa-119">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="384fa-120">添加整数;各个</span><span class="sxs-lookup"><span data-stu-id="384fa-120">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="384fa-121">字符串、数组和哈希表。</span><span class="sxs-lookup"><span data-stu-id="384fa-121">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="384fa-122">从一个值中减去另一个值</span><span class="sxs-lookup"><span data-stu-id="384fa-122">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="384fa-123">value</span><span class="sxs-lookup"><span data-stu-id="384fa-123">value</span></span>                             |                             |
| -      |<span data-ttu-id="384fa-124">使数字成为负数</span><span class="sxs-lookup"><span data-stu-id="384fa-124">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="384fa-125">数字或复制字符串相乘</span><span class="sxs-lookup"><span data-stu-id="384fa-125">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="384fa-126">和数组指定的数字</span><span class="sxs-lookup"><span data-stu-id="384fa-126">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="384fa-127">次。</span><span class="sxs-lookup"><span data-stu-id="384fa-127">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="384fa-128">两个值相除。</span><span class="sxs-lookup"><span data-stu-id="384fa-128">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="384fa-129">取模-返回剩余的</span><span class="sxs-lookup"><span data-stu-id="384fa-129">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="384fa-130">除法运算。</span><span class="sxs-lookup"><span data-stu-id="384fa-130">a division operation.</span></span>             |                             |
|<span data-ttu-id="384fa-131">-带</span><span class="sxs-lookup"><span data-stu-id="384fa-131">-band</span></span>   |<span data-ttu-id="384fa-132">位与</span><span class="sxs-lookup"><span data-stu-id="384fa-132">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="384fa-133">-bnot</span><span class="sxs-lookup"><span data-stu-id="384fa-133">-bnot</span></span>   |<span data-ttu-id="384fa-134">按位“非”</span><span class="sxs-lookup"><span data-stu-id="384fa-134">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="384fa-135">-bor</span><span class="sxs-lookup"><span data-stu-id="384fa-135">-bor</span></span>    |<span data-ttu-id="384fa-136">按位“或”</span><span class="sxs-lookup"><span data-stu-id="384fa-136">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="384fa-137">-bxor</span><span class="sxs-lookup"><span data-stu-id="384fa-137">-bxor</span></span>   |<span data-ttu-id="384fa-138">按位“异或”</span><span class="sxs-lookup"><span data-stu-id="384fa-138">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="384fa-139">-shl</span><span class="sxs-lookup"><span data-stu-id="384fa-139">-shl</span></span>    |<span data-ttu-id="384fa-140">将位向左移动</span><span class="sxs-lookup"><span data-stu-id="384fa-140">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="384fa-141">-shr</span><span class="sxs-lookup"><span data-stu-id="384fa-141">-shr</span></span>    |<span data-ttu-id="384fa-142">将位向右移位</span><span class="sxs-lookup"><span data-stu-id="384fa-142">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="384fa-143">按位运算符仅适用于整数类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-143">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="384fa-144">运算符优先级</span><span class="sxs-lookup"><span data-stu-id="384fa-144">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="384fa-145">PowerShell 按以下顺序处理算术运算符：</span><span class="sxs-lookup"><span data-stu-id="384fa-145">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="384fa-146">优先级</span><span class="sxs-lookup"><span data-stu-id="384fa-146">Precedence</span></span>|<span data-ttu-id="384fa-147">操作员</span><span class="sxs-lookup"><span data-stu-id="384fa-147">Operator</span></span>          |<span data-ttu-id="384fa-148">说明</span><span class="sxs-lookup"><span data-stu-id="384fa-148">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="384fa-149">1</span><span class="sxs-lookup"><span data-stu-id="384fa-149">1</span></span>         | `()`             |<span data-ttu-id="384fa-150">括号</span><span class="sxs-lookup"><span data-stu-id="384fa-150">Parentheses</span></span>                            |
|<span data-ttu-id="384fa-151">2</span><span class="sxs-lookup"><span data-stu-id="384fa-151">2</span></span>         | `-`              |<span data-ttu-id="384fa-152">对于负数或一元运算符</span><span class="sxs-lookup"><span data-stu-id="384fa-152">For a negative number or unary operator</span></span>|
|<span data-ttu-id="384fa-153">3</span><span class="sxs-lookup"><span data-stu-id="384fa-153">3</span></span>         | <span data-ttu-id="384fa-154">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="384fa-154">`*`, `/`, `%`</span></span>    |<span data-ttu-id="384fa-155">对于乘法和除法</span><span class="sxs-lookup"><span data-stu-id="384fa-155">For multiplication and division</span></span>        |
|<span data-ttu-id="384fa-156">4</span><span class="sxs-lookup"><span data-stu-id="384fa-156">4</span></span>         | <span data-ttu-id="384fa-157">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="384fa-157">`+`, `-`</span></span>         |<span data-ttu-id="384fa-158">对于加法和减法</span><span class="sxs-lookup"><span data-stu-id="384fa-158">For addition and subtraction</span></span>           |
|<span data-ttu-id="384fa-159">5</span><span class="sxs-lookup"><span data-stu-id="384fa-159">5</span></span>         | <span data-ttu-id="384fa-160">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="384fa-160">`-band`, `-bnot`</span></span> |<span data-ttu-id="384fa-161">对于按位运算</span><span class="sxs-lookup"><span data-stu-id="384fa-161">For bitwise operations</span></span>                 |
|<span data-ttu-id="384fa-162">5</span><span class="sxs-lookup"><span data-stu-id="384fa-162">5</span></span>         | <span data-ttu-id="384fa-163">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="384fa-163">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="384fa-164">对于按位运算</span><span class="sxs-lookup"><span data-stu-id="384fa-164">For bitwise operations</span></span>                 |
|<span data-ttu-id="384fa-165">5</span><span class="sxs-lookup"><span data-stu-id="384fa-165">5</span></span>         | <span data-ttu-id="384fa-166">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="384fa-166">`-shr`, `-shl`</span></span>   |<span data-ttu-id="384fa-167">对于按位运算</span><span class="sxs-lookup"><span data-stu-id="384fa-167">For bitwise operations</span></span>                 |

<span data-ttu-id="384fa-168">根据优先级规则，PowerShell 从左到右处理表达式。</span><span class="sxs-lookup"><span data-stu-id="384fa-168">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="384fa-169">以下示例显示了优先规则的效果：</span><span class="sxs-lookup"><span data-stu-id="384fa-169">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="384fa-170">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-170">Expression</span></span> |<span data-ttu-id="384fa-171">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-171">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="384fa-172">PowerShell 计算表达式的顺序可能不同于你使用的其他编程和脚本语言。</span><span class="sxs-lookup"><span data-stu-id="384fa-172">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="384fa-173">下面的示例演示了复杂的赋值语句。</span><span class="sxs-lookup"><span data-stu-id="384fa-173">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="384fa-174">在此示例中，对表达式 `$a++` 进行计算 `$b[$a]` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-174">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="384fa-175">在 `$a++` `$a` 语句中使用之后，计算更改的值， `$c[$a++]` 但在中使用它之前 `$b[$a]` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-175">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="384fa-176">中的 `$a` 变量 `$b[$a]` 等于 `1` ，而不是 `0` ; 因此，语句将值赋给 `$b[1]` ，而不是 `$b[0]` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-176">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="384fa-177">上述代码等效于：</span><span class="sxs-lookup"><span data-stu-id="384fa-177">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="384fa-178">相除和舍入</span><span class="sxs-lookup"><span data-stu-id="384fa-178">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="384fa-179">当除法运算的商是整数时，PowerShell 会将值舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="384fa-179">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="384fa-180">如果值为 `.5` ，则它将舍入到最接近的偶数。</span><span class="sxs-lookup"><span data-stu-id="384fa-180">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="384fa-181">下面的示例演示舍入到最接近的偶数的效果。</span><span class="sxs-lookup"><span data-stu-id="384fa-181">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="384fa-182">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-182">Expression</span></span>      |<span data-ttu-id="384fa-183">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-183">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="384fa-184">请注意 **_5/2_ = 2.5** 舍入到 **2** 的方式。</span><span class="sxs-lookup"><span data-stu-id="384fa-184">Notice how **_5/2_ = 2.5** gets rounded to **2**.</span></span> <span data-ttu-id="384fa-185">但 **_7/2_ = 3.5** 舍入为 **4**。</span><span class="sxs-lookup"><span data-stu-id="384fa-185">But, **_7/2_ = 3.5** gets rounded to **4**.</span></span>

<span data-ttu-id="384fa-186">您可以使用 `[Math]` 类来获取不同的舍入行为。</span><span class="sxs-lookup"><span data-stu-id="384fa-186">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="384fa-187">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-187">Expression</span></span>                          | <span data-ttu-id="384fa-188">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-188">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="384fa-189">有关详细信息，请参阅 [Math](/dotnet/api/system.math.round) 方法。</span><span class="sxs-lookup"><span data-stu-id="384fa-189">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="384fa-190">添加非数值类型和相乘</span><span class="sxs-lookup"><span data-stu-id="384fa-190">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="384fa-191">可以添加数字、字符串、数组和哈希表。</span><span class="sxs-lookup"><span data-stu-id="384fa-191">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="384fa-192">而且，您可以将数字、字符串和数组相乘。</span><span class="sxs-lookup"><span data-stu-id="384fa-192">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="384fa-193">但是，不能将哈希表相乘。</span><span class="sxs-lookup"><span data-stu-id="384fa-193">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="384fa-194">添加字符串、数组或哈希表时，这些元素将连接在一起。</span><span class="sxs-lookup"><span data-stu-id="384fa-194">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="384fa-195">当连接集合（如数组或哈希表）时，将创建一个新的对象，该对象包含两个集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="384fa-195">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="384fa-196">如果尝试连接具有相同键的哈希表，则操作将失败。</span><span class="sxs-lookup"><span data-stu-id="384fa-196">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="384fa-197">例如，下面的命令创建两个数组，然后添加它们：</span><span class="sxs-lookup"><span data-stu-id="384fa-197">For example, the following commands create two arrays and then add them:</span></span>

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

<span data-ttu-id="384fa-198">您还可以对不同类型的对象执行算术运算。</span><span class="sxs-lookup"><span data-stu-id="384fa-198">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="384fa-199">PowerShell 执行的操作由操作中最左边对象的 Microsoft .NET 框架类型决定。</span><span class="sxs-lookup"><span data-stu-id="384fa-199">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="384fa-200">PowerShell 尝试将操作中的所有对象转换为第一个对象的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-200">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="384fa-201">如果它成功转换了对象，它将执行适用于第一个对象的 .NET Framework 类型的操作。</span><span class="sxs-lookup"><span data-stu-id="384fa-201">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="384fa-202">如果无法转换任何对象，操作将失败。</span><span class="sxs-lookup"><span data-stu-id="384fa-202">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="384fa-203">下面的示例演示加法和乘法运算符的用法;在包含不同对象类型的操作中。</span><span class="sxs-lookup"><span data-stu-id="384fa-203">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="384fa-204">假定 `$array = 1,2,3` ：</span><span class="sxs-lookup"><span data-stu-id="384fa-204">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="384fa-205">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-205">Expression</span></span>       |<span data-ttu-id="384fa-206">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-206">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="384fa-207">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="384fa-207">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="384fa-208">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="384fa-208">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="384fa-209">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="384fa-209">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="384fa-210">因为用于计算语句的方法由最左端的对象确定，所以 PowerShell 中的加法和乘法并不完全是可交换的。</span><span class="sxs-lookup"><span data-stu-id="384fa-210">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="384fa-211">例如，并不 `(a + b)` 总是相等 `(b + a)` ，并且不 `(ab)` 始终相等 `(ba)` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-211">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="384fa-212">下面的示例演示了这一原则：</span><span class="sxs-lookup"><span data-stu-id="384fa-212">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="384fa-213">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-213">Expression</span></span>   |<span data-ttu-id="384fa-214">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-214">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="384fa-215">+ 16 + "file"</span><span class="sxs-lookup"><span data-stu-id="384fa-215">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="384fa-216">哈希表的大小写略有不同。</span><span class="sxs-lookup"><span data-stu-id="384fa-216">Hash tables are a slightly different case.</span></span> <span data-ttu-id="384fa-217">您可以将哈希表添加到另一个哈希表，前提是已添加的哈希表没有重复键。</span><span class="sxs-lookup"><span data-stu-id="384fa-217">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="384fa-218">下面的示例演示如何向彼此添加哈希表。</span><span class="sxs-lookup"><span data-stu-id="384fa-218">The following example show how to add hash tables to each other.</span></span>

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

<span data-ttu-id="384fa-219">下面的示例引发错误，因为这两个哈希表中的一个键重复。</span><span class="sxs-lookup"><span data-stu-id="384fa-219">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

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

<span data-ttu-id="384fa-220">此外，还可以将哈希表添加到数组;而且，整个哈希表将成为数组中的项。</span><span class="sxs-lookup"><span data-stu-id="384fa-220">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

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

<span data-ttu-id="384fa-221">但是，不能将任何其他类型添加到哈希表。</span><span class="sxs-lookup"><span data-stu-id="384fa-221">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="384fa-222">虽然加法运算符非常有用，但使用赋值运算符将元素添加到哈希表和数组。</span><span class="sxs-lookup"><span data-stu-id="384fa-222">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="384fa-223">有关详细信息，请参阅 [about_assignment_operators](about_Assignment_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="384fa-223">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="384fa-224">下面的示例使用 `+=` 赋值运算符将项添加到数组中：</span><span class="sxs-lookup"><span data-stu-id="384fa-224">The following examples use the `+=` assignment operator to add items to an array:</span></span>

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

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="384fa-225">用于容纳结果的类型转换</span><span class="sxs-lookup"><span data-stu-id="384fa-225">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="384fa-226">PowerShell 会自动选择最能表达结果的 .NET Framework 数值类型，而不会丢失精度。</span><span class="sxs-lookup"><span data-stu-id="384fa-226">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="384fa-227">例如：</span><span class="sxs-lookup"><span data-stu-id="384fa-227">For example:</span></span>

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

<span data-ttu-id="384fa-228">如果操作的结果对于类型太大，则结果的类型会扩大以容纳结果，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="384fa-228">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="384fa-229">结果的类型不一定与操作数之一相同。</span><span class="sxs-lookup"><span data-stu-id="384fa-229">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="384fa-230">在下面的示例中，负值不能转换为无符号整数，且无符号整数太大，无法强制转换为 `Int32` ：</span><span class="sxs-lookup"><span data-stu-id="384fa-230">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="384fa-231">在此示例中， `Int64` 可以同时容纳这两种类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-231">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="384fa-232">`System.Decimal`类型为异常。</span><span class="sxs-lookup"><span data-stu-id="384fa-232">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="384fa-233">如果任一操作数具有 Decimal 类型，则结果将为 Decimal 类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-233">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="384fa-234">如果结果对 Decimal 类型来说太大，则不会将其强制转换为 Double 类型。</span><span class="sxs-lookup"><span data-stu-id="384fa-234">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="384fa-235">相反，会产生错误。</span><span class="sxs-lookup"><span data-stu-id="384fa-235">Instead, an error results.</span></span>

|<span data-ttu-id="384fa-236">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-236">Expression</span></span>               |<span data-ttu-id="384fa-237">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-237">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="384fa-238">算术运算符和变量</span><span class="sxs-lookup"><span data-stu-id="384fa-238">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="384fa-239">还可以对变量使用算术运算符。</span><span class="sxs-lookup"><span data-stu-id="384fa-239">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="384fa-240">运算符作用于变量的值。</span><span class="sxs-lookup"><span data-stu-id="384fa-240">The operators act on the values of the variables.</span></span> <span data-ttu-id="384fa-241">下面的示例演示如何对变量使用算术运算符：</span><span class="sxs-lookup"><span data-stu-id="384fa-241">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="384fa-242">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-242">Expression</span></span>                                    |<span data-ttu-id="384fa-243">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-243">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="384fa-244">算术运算符和命令</span><span class="sxs-lookup"><span data-stu-id="384fa-244">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="384fa-245">通常，可以在表达式中使用数字、字符串和数组的算术运算符。</span><span class="sxs-lookup"><span data-stu-id="384fa-245">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="384fa-246">但是，还可以将算术运算符与命令返回的对象以及这些对象的属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="384fa-246">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="384fa-247">下面的示例演示如何在表达式中通过 PowerShell 命令使用算术运算符：</span><span class="sxs-lookup"><span data-stu-id="384fa-247">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="384fa-248">圆括号运算符 `get-date` 按顺序强制对 cmdlet 和 cmdlet 表达式的计算进行计算 `new-timespan -day 1` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-248">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="384fa-249">然后使用运算符添加两个结果 `+` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-249">Both results are then added using the `+` operator.</span></span>

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

<span data-ttu-id="384fa-250">在上述表达式中， () 的每个进程工作空间 `$_.ws` 都将乘以 `2` ; 与结果相比， `50mb` 它们是否大于该值。</span><span class="sxs-lookup"><span data-stu-id="384fa-250">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="384fa-251">位运算符</span><span class="sxs-lookup"><span data-stu-id="384fa-251">Bitwise Operators</span></span>

<span data-ttu-id="384fa-252">PowerShell 支持标准按位运算符，包括按位与 (`-bAnd`) 、 (和) 的非独占和独占按位或运算符 `-bOr` 和 `-bXor` 以及按位 "非 () `-bNot` 。</span><span class="sxs-lookup"><span data-stu-id="384fa-252">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="384fa-253">从 PowerShell 2.0 开始，所有位运算符都适用于64位整数。</span><span class="sxs-lookup"><span data-stu-id="384fa-253">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="384fa-254">从 PowerShell 3.0 开始， `-shr` 会引入 (向右) 和 `-shl` (左移) ，以支持在 PowerShell 中进行按位运算。</span><span class="sxs-lookup"><span data-stu-id="384fa-254">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="384fa-255">PowerShell 支持以下按位运算符。</span><span class="sxs-lookup"><span data-stu-id="384fa-255">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="384fa-256">操作员</span><span class="sxs-lookup"><span data-stu-id="384fa-256">Operator</span></span> | <span data-ttu-id="384fa-257">说明</span><span class="sxs-lookup"><span data-stu-id="384fa-257">Description</span></span>            | <span data-ttu-id="384fa-258">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-258">Expression</span></span>   | <span data-ttu-id="384fa-259">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-259">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="384fa-260">位与</span><span class="sxs-lookup"><span data-stu-id="384fa-260">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="384fa-261">2</span><span class="sxs-lookup"><span data-stu-id="384fa-261">2</span></span>      |
| `-bor`   | <span data-ttu-id="384fa-262">按位 OR (包含) </span><span class="sxs-lookup"><span data-stu-id="384fa-262">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="384fa-263">11</span><span class="sxs-lookup"><span data-stu-id="384fa-263">11</span></span>     |
| `-bxor`  | <span data-ttu-id="384fa-264">按位或 (独占) </span><span class="sxs-lookup"><span data-stu-id="384fa-264">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="384fa-265">9</span><span class="sxs-lookup"><span data-stu-id="384fa-265">9</span></span>      |
| `-bnot`  | <span data-ttu-id="384fa-266">按位“非”</span><span class="sxs-lookup"><span data-stu-id="384fa-266">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="384fa-267">-11</span><span class="sxs-lookup"><span data-stu-id="384fa-267">-11</span></span>    |
| `-shl`   | <span data-ttu-id="384fa-268">左移</span><span class="sxs-lookup"><span data-stu-id="384fa-268">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="384fa-269">408</span><span class="sxs-lookup"><span data-stu-id="384fa-269">408</span></span>    |
| `-shr`   | <span data-ttu-id="384fa-270">向右移动</span><span class="sxs-lookup"><span data-stu-id="384fa-270">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="384fa-271">51</span><span class="sxs-lookup"><span data-stu-id="384fa-271">51</span></span>     |

<span data-ttu-id="384fa-272">位运算符作用于值的二进制格式。</span><span class="sxs-lookup"><span data-stu-id="384fa-272">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="384fa-273">例如，数字10的位结构为 00001010 (基于1个字节) ，数字3的位结构是00000011。</span><span class="sxs-lookup"><span data-stu-id="384fa-273">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="384fa-274">当使用位运算符将10与3进行比较时，将比较每个字节中的单个位。</span><span class="sxs-lookup"><span data-stu-id="384fa-274">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="384fa-275">在按位 "与" 运算中，只有当两个输入位均为1时，才将生成的位设置为1。</span><span class="sxs-lookup"><span data-stu-id="384fa-275">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="384fa-276">在按位 "或" (包含) "操作中，如果其中一个或两个输入位均为1，则生成的位将设置为1。</span><span class="sxs-lookup"><span data-stu-id="384fa-276">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="384fa-277">仅当两个输入位均设置为0时，结果位设置为0。</span><span class="sxs-lookup"><span data-stu-id="384fa-277">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="384fa-278">在按位或 (独占) 操作中，仅当一个输入位为1时，结果位将设置为1。</span><span class="sxs-lookup"><span data-stu-id="384fa-278">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="384fa-279">按位 "非" 运算符是一个一元运算符，该运算符产生值的二进制补码。</span><span class="sxs-lookup"><span data-stu-id="384fa-279">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="384fa-280">1的位设置为0，位0设置为1。</span><span class="sxs-lookup"><span data-stu-id="384fa-280">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="384fa-281">例如，0的二进制反码为-1，最大无符号整数 (0xffffffff) ，二进制补码-1 为0。</span><span class="sxs-lookup"><span data-stu-id="384fa-281">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

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

<span data-ttu-id="384fa-282">在按位左移操作时，所有位都向左移动 "n"，其中 "n" 是右操作数的值。</span><span class="sxs-lookup"><span data-stu-id="384fa-282">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="384fa-283">在一个位置插入零。</span><span class="sxs-lookup"><span data-stu-id="384fa-283">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="384fa-284">当左操作数是一个整数 (32 位) 值时，右操作数的下5位将确定左操作数的位移位数。</span><span class="sxs-lookup"><span data-stu-id="384fa-284">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="384fa-285">当左操作数为长 (64 位) 值时，右操作数的低6位确定左操作数的偏移量。</span><span class="sxs-lookup"><span data-stu-id="384fa-285">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="384fa-286">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-286">Expression</span></span> |<span data-ttu-id="384fa-287">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-287">Result</span></span>|<span data-ttu-id="384fa-288">二进制结果</span><span class="sxs-lookup"><span data-stu-id="384fa-288">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="384fa-289">21</span><span class="sxs-lookup"><span data-stu-id="384fa-289">21</span></span>    |<span data-ttu-id="384fa-290">0001 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-290">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="384fa-291">42</span><span class="sxs-lookup"><span data-stu-id="384fa-291">42</span></span>    |<span data-ttu-id="384fa-292">0010 1010</span><span class="sxs-lookup"><span data-stu-id="384fa-292">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="384fa-293">84</span><span class="sxs-lookup"><span data-stu-id="384fa-293">84</span></span>    |<span data-ttu-id="384fa-294">0101 0100</span><span class="sxs-lookup"><span data-stu-id="384fa-294">0101 0100</span></span>    |

<span data-ttu-id="384fa-295">在按位右移操作中，所有位都将 "n" 向右移动，其中 "n" 由右操作数指定。</span><span class="sxs-lookup"><span data-stu-id="384fa-295">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="384fa-296">向右移动运算符 (-shr) 在将正或无符号值向右移位时，将在最左侧插入零。</span><span class="sxs-lookup"><span data-stu-id="384fa-296">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="384fa-297">当左操作数是一个整数 (32 位) 值时，右操作数的下5位将确定左操作数的位移位数。</span><span class="sxs-lookup"><span data-stu-id="384fa-297">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="384fa-298">当左操作数为长 (64 位) 值时，右操作数的低6位确定左操作数的偏移量。</span><span class="sxs-lookup"><span data-stu-id="384fa-298">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="384fa-299">表达式</span><span class="sxs-lookup"><span data-stu-id="384fa-299">Expression</span></span>              |<span data-ttu-id="384fa-300">结果</span><span class="sxs-lookup"><span data-stu-id="384fa-300">Result</span></span>      |<span data-ttu-id="384fa-301">二进制</span><span class="sxs-lookup"><span data-stu-id="384fa-301">Binary</span></span>     |<span data-ttu-id="384fa-302">Hex</span><span class="sxs-lookup"><span data-stu-id="384fa-302">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="384fa-303">21</span><span class="sxs-lookup"><span data-stu-id="384fa-303">21</span></span>         | <span data-ttu-id="384fa-304">0001 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-304">0001 0101</span></span> | <span data-ttu-id="384fa-305">0x15</span><span class="sxs-lookup"><span data-stu-id="384fa-305">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="384fa-306">10</span><span class="sxs-lookup"><span data-stu-id="384fa-306">10</span></span>         | <span data-ttu-id="384fa-307">0000 1010</span><span class="sxs-lookup"><span data-stu-id="384fa-307">0000 1010</span></span> | <span data-ttu-id="384fa-308">0x0A</span><span class="sxs-lookup"><span data-stu-id="384fa-308">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="384fa-309">5</span><span class="sxs-lookup"><span data-stu-id="384fa-309">5</span></span>          | <span data-ttu-id="384fa-310">0000 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-310">0000 0101</span></span> | <span data-ttu-id="384fa-311">0x05</span><span class="sxs-lookup"><span data-stu-id="384fa-311">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="384fa-312">0</span><span class="sxs-lookup"><span data-stu-id="384fa-312">0</span></span>          | <span data-ttu-id="384fa-313">0000 0000</span><span class="sxs-lookup"><span data-stu-id="384fa-313">0000 0000</span></span> | <span data-ttu-id="384fa-314">0x00</span><span class="sxs-lookup"><span data-stu-id="384fa-314">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="384fa-315">21</span><span class="sxs-lookup"><span data-stu-id="384fa-315">21</span></span>         | <span data-ttu-id="384fa-316">0001 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-316">0001 0101</span></span> | <span data-ttu-id="384fa-317">0x15</span><span class="sxs-lookup"><span data-stu-id="384fa-317">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="384fa-318">21</span><span class="sxs-lookup"><span data-stu-id="384fa-318">21</span></span>         | <span data-ttu-id="384fa-319">0001 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-319">0001 0101</span></span> | <span data-ttu-id="384fa-320">0x15</span><span class="sxs-lookup"><span data-stu-id="384fa-320">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="384fa-321">10</span><span class="sxs-lookup"><span data-stu-id="384fa-321">10</span></span>         | <span data-ttu-id="384fa-322">0000 1010</span><span class="sxs-lookup"><span data-stu-id="384fa-322">0000 1010</span></span> | <span data-ttu-id="384fa-323">0x0A</span><span class="sxs-lookup"><span data-stu-id="384fa-323">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="384fa-324">5</span><span class="sxs-lookup"><span data-stu-id="384fa-324">5</span></span>          | <span data-ttu-id="384fa-325">0000 0101</span><span class="sxs-lookup"><span data-stu-id="384fa-325">0000 0101</span></span> | <span data-ttu-id="384fa-326">0x05</span><span class="sxs-lookup"><span data-stu-id="384fa-326">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="384fa-327">1073741823</span><span class="sxs-lookup"><span data-stu-id="384fa-327">1073741823</span></span> |           | <span data-ttu-id="384fa-328">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="384fa-328">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="384fa-329">-1073741824</span><span class="sxs-lookup"><span data-stu-id="384fa-329">-1073741824</span></span>|           | <span data-ttu-id="384fa-330">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="384fa-330">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="384fa-331">-1</span><span class="sxs-lookup"><span data-stu-id="384fa-331">-1</span></span>         |           | <span data-ttu-id="384fa-332">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="384fa-332">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="384fa-333">另请参阅</span><span class="sxs-lookup"><span data-stu-id="384fa-333">SEE ALSO</span></span>

- [<span data-ttu-id="384fa-334">about_arrays</span><span class="sxs-lookup"><span data-stu-id="384fa-334">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="384fa-335">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="384fa-335">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="384fa-336">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="384fa-336">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="384fa-337">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="384fa-337">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="384fa-338">about_operators</span><span class="sxs-lookup"><span data-stu-id="384fa-338">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="384fa-339">about_variables</span><span class="sxs-lookup"><span data-stu-id="384fa-339">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="384fa-340">获取日期</span><span class="sxs-lookup"><span data-stu-id="384fa-340">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="384fa-341">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="384fa-341">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
