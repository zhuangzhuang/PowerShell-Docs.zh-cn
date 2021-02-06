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
# <a name="about-numeric-literals"></a><span data-ttu-id="12838-103">关于数字文本</span><span class="sxs-lookup"><span data-stu-id="12838-103">About numeric literals</span></span>

<span data-ttu-id="12838-104">有两种类型的数值：整数和实数。</span><span class="sxs-lookup"><span data-stu-id="12838-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="12838-105">两者都可以具有类型和乘数后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="12838-106">整数文本</span><span class="sxs-lookup"><span data-stu-id="12838-106">Integer literals</span></span>

<span data-ttu-id="12838-107">整数文本可以用十进制、十六进制或二进制表示法来编写。</span><span class="sxs-lookup"><span data-stu-id="12838-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="12838-108">十六进制文本的前面加上前缀 `0x` ，二进制文本带有前缀， `0b` 以将它们与十进制数区分开来。</span><span class="sxs-lookup"><span data-stu-id="12838-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="12838-109">整数文本可以具有类型后缀和乘数后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="12838-110">Suffix</span><span class="sxs-lookup"><span data-stu-id="12838-110">Suffix</span></span> |            <span data-ttu-id="12838-111">含义</span><span class="sxs-lookup"><span data-stu-id="12838-111">Meaning</span></span>             |          <span data-ttu-id="12838-112">注意</span><span class="sxs-lookup"><span data-stu-id="12838-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="12838-113">y</span><span class="sxs-lookup"><span data-stu-id="12838-113">y</span></span>      | <span data-ttu-id="12838-114">带符号字节数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-114">signed byte data type</span></span>          | <span data-ttu-id="12838-115">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-116">uy</span><span class="sxs-lookup"><span data-stu-id="12838-116">uy</span></span>     | <span data-ttu-id="12838-117">无符号 byte 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-117">unsigned byte data type</span></span>        | <span data-ttu-id="12838-118">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-119">s</span><span class="sxs-lookup"><span data-stu-id="12838-119">s</span></span>      | <span data-ttu-id="12838-120">Short 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-120">short data type</span></span>                | <span data-ttu-id="12838-121">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-122">us</span><span class="sxs-lookup"><span data-stu-id="12838-122">us</span></span>     | <span data-ttu-id="12838-123">无符号 short 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-123">unsigned short data type</span></span>       | <span data-ttu-id="12838-124">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-125">l</span><span class="sxs-lookup"><span data-stu-id="12838-125">l</span></span>      | <span data-ttu-id="12838-126">long 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-126">long data type</span></span>                 |                         |
| <span data-ttu-id="12838-127">u</span><span class="sxs-lookup"><span data-stu-id="12838-127">u</span></span>      | <span data-ttu-id="12838-128">无符号 int 或 long 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-128">unsigned int or long data type</span></span> | <span data-ttu-id="12838-129">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-130">ul</span><span class="sxs-lookup"><span data-stu-id="12838-130">ul</span></span>     | <span data-ttu-id="12838-131">无符号 long 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-131">unsigned long data type</span></span>        | <span data-ttu-id="12838-132">在 PowerShell 6.2 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="12838-133">n</span><span class="sxs-lookup"><span data-stu-id="12838-133">n</span></span>      | <span data-ttu-id="12838-134">BigInteger 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-134">BigInteger data type</span></span>           | <span data-ttu-id="12838-135">在 PowerShell 7.0 中添加</span><span class="sxs-lookup"><span data-stu-id="12838-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="12838-136">kb</span><span class="sxs-lookup"><span data-stu-id="12838-136">kb</span></span>     | <span data-ttu-id="12838-137">kb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="12838-138">mb</span><span class="sxs-lookup"><span data-stu-id="12838-138">mb</span></span>     | <span data-ttu-id="12838-139">兆字节乘数</span><span class="sxs-lookup"><span data-stu-id="12838-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="12838-140">内存</span><span class="sxs-lookup"><span data-stu-id="12838-140">gb</span></span>     | <span data-ttu-id="12838-141">千兆字节乘数</span><span class="sxs-lookup"><span data-stu-id="12838-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="12838-142">tb</span><span class="sxs-lookup"><span data-stu-id="12838-142">tb</span></span>     | <span data-ttu-id="12838-143">tb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="12838-144">容量</span><span class="sxs-lookup"><span data-stu-id="12838-144">pb</span></span>     | <span data-ttu-id="12838-145">pb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="12838-146">整数文本的类型由其值、类型后缀和数值乘数后缀确定。</span><span class="sxs-lookup"><span data-stu-id="12838-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="12838-147">对于无类型后缀的整数文本：</span><span class="sxs-lookup"><span data-stu-id="12838-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="12838-148">如果值可以通过类型表示 `[int]` ，则为其类型。</span><span class="sxs-lookup"><span data-stu-id="12838-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="12838-149">否则，如果该值可以由类型表示 `[long]` ，则为其类型。</span><span class="sxs-lookup"><span data-stu-id="12838-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="12838-150">否则，如果该值可以由类型表示 `[decimal]` ，则为其类型。</span><span class="sxs-lookup"><span data-stu-id="12838-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="12838-151">否则，它由类型表示 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="12838-152">对于类型为后缀的整数文本：</span><span class="sxs-lookup"><span data-stu-id="12838-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="12838-153">如果类型后缀为 `u` ，并且值可由类型表示， `[uint]` 则其类型为 `[uint]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="12838-154">如果类型后缀为 `u` ，并且值可由类型表示， `[ulong]` 则其类型为 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="12838-155">如果其值可由指定的类型表示，则为其类型。</span><span class="sxs-lookup"><span data-stu-id="12838-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="12838-156">否则，该文本的格式不正确。</span><span class="sxs-lookup"><span data-stu-id="12838-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="12838-157">真实文本</span><span class="sxs-lookup"><span data-stu-id="12838-157">Real literals</span></span>

<span data-ttu-id="12838-158">实际文本只能用十进制符号编写。</span><span class="sxs-lookup"><span data-stu-id="12838-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="12838-159">此表示法可以在小数点后包含小数值，使用指数部分包括科学记数法。</span><span class="sxs-lookup"><span data-stu-id="12838-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="12838-160">指数部分包含一个 "e"，后跟一个可选符号 (+/-) 和一个表示指数的数字。</span><span class="sxs-lookup"><span data-stu-id="12838-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="12838-161">例如，文本值 `1e2` 等于数值100。</span><span class="sxs-lookup"><span data-stu-id="12838-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="12838-162">真实文本可以具有类型后缀和乘数后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="12838-163">Suffix</span><span class="sxs-lookup"><span data-stu-id="12838-163">Suffix</span></span> |       <span data-ttu-id="12838-164">含义</span><span class="sxs-lookup"><span data-stu-id="12838-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="12838-165">d</span><span class="sxs-lookup"><span data-stu-id="12838-165">d</span></span>      | <span data-ttu-id="12838-166">decimal 数据类型</span><span class="sxs-lookup"><span data-stu-id="12838-166">decimal data type</span></span>   |
| <span data-ttu-id="12838-167">kb</span><span class="sxs-lookup"><span data-stu-id="12838-167">kb</span></span>     | <span data-ttu-id="12838-168">kb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="12838-169">mb</span><span class="sxs-lookup"><span data-stu-id="12838-169">mb</span></span>     | <span data-ttu-id="12838-170">兆字节乘数</span><span class="sxs-lookup"><span data-stu-id="12838-170">megabyte multiplier</span></span> |
| <span data-ttu-id="12838-171">内存</span><span class="sxs-lookup"><span data-stu-id="12838-171">gb</span></span>     | <span data-ttu-id="12838-172">千兆字节乘数</span><span class="sxs-lookup"><span data-stu-id="12838-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="12838-173">tb</span><span class="sxs-lookup"><span data-stu-id="12838-173">tb</span></span>     | <span data-ttu-id="12838-174">tb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-174">terabyte multiplier</span></span> |
| <span data-ttu-id="12838-175">容量</span><span class="sxs-lookup"><span data-stu-id="12838-175">pb</span></span>     | <span data-ttu-id="12838-176">pb 乘数</span><span class="sxs-lookup"><span data-stu-id="12838-176">petabyte multiplier</span></span> |

<span data-ttu-id="12838-177">有两种类型的真实文本： double 和 decimal。</span><span class="sxs-lookup"><span data-stu-id="12838-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="12838-178">它们分别由一个或两个 decimal 类型的后缀表示。</span><span class="sxs-lookup"><span data-stu-id="12838-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="12838-179">PowerShell 不支持值的文本表示形式 `[float]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="12838-180">双实型文本具有类型 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="12838-181">Decimal 实型文本具有类型 `[decimal]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="12838-182">Decimal 实文字的小数部分的尾随零非常重要。</span><span class="sxs-lookup"><span data-stu-id="12838-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="12838-183">如果实际文本中指数部分的数字值 `[double]` 小于支持的最小值，则该 `[double]` 实数文本的值为0。</span><span class="sxs-lookup"><span data-stu-id="12838-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="12838-184">如果实际文本中指数部分的数字值 `[decimal]` 小于所支持的最小值，则该文本的格式不正确。</span><span class="sxs-lookup"><span data-stu-id="12838-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="12838-185">如果指数部分的数字或真实文本中的数字 `[double]` `[decimal]` 大于所支持的最大值，则该文本的格式不正确。</span><span class="sxs-lookup"><span data-stu-id="12838-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="12838-186">语法允许双实型文本具有长类型的后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="12838-187">PowerShell 将此事例视为一个整数文本，其值由类型表示 `[long]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="12838-188">保留此功能是为了向后兼容早期版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="12838-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="12838-189">但是，不鼓励程序员使用此窗体的整数文本，因为它们可以轻松地遮蔽文本的实际值。</span><span class="sxs-lookup"><span data-stu-id="12838-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="12838-190">例如， `1.2L` 值为1，值为12，值为 `1.2345e1L` `1.2345e-5L` 0，则不会立即出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="12838-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="12838-191">数值乘数</span><span class="sxs-lookup"><span data-stu-id="12838-191">Numeric multipliers</span></span>

<span data-ttu-id="12838-192">为方便起见，整数和真实文本可以包含数值乘数，这表示一组常用的一组2的幂。</span><span class="sxs-lookup"><span data-stu-id="12838-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="12838-193">数值乘数可以用大写或小写字母的任意组合来编写。</span><span class="sxs-lookup"><span data-stu-id="12838-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="12838-194">乘数后缀可与任何类型后缀结合使用，但必须出现在类型后缀之后。</span><span class="sxs-lookup"><span data-stu-id="12838-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="12838-195">例如，文字的 `100gbL` 格式不正确，但文字 `100Lgb` 有效。</span><span class="sxs-lookup"><span data-stu-id="12838-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="12838-196">如果乘数创建的值超出了该后缀指定的数值类型的可能值，则该文本的格式不正确。</span><span class="sxs-lookup"><span data-stu-id="12838-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="12838-197">例如，文本的 `1usgb` 格式不正确，因为值大于 `1gb` 后缀指定的类型所允许的值 `[ushort]` `us` 。</span><span class="sxs-lookup"><span data-stu-id="12838-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="12838-198">乘数示例</span><span class="sxs-lookup"><span data-stu-id="12838-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="12838-199">数值类型加速器</span><span class="sxs-lookup"><span data-stu-id="12838-199">Numeric type accelerators</span></span>

<span data-ttu-id="12838-200">PowerShell 支持以下类型加速器：</span><span class="sxs-lookup"><span data-stu-id="12838-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="12838-201">加速器</span><span class="sxs-lookup"><span data-stu-id="12838-201">Accelerator</span></span> |         <span data-ttu-id="12838-202">注意</span><span class="sxs-lookup"><span data-stu-id="12838-202">Note</span></span>         |           <span data-ttu-id="12838-203">说明</span><span class="sxs-lookup"><span data-stu-id="12838-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="12838-204">字节 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="12838-205">字节 (有符号) </span><span class="sxs-lookup"><span data-stu-id="12838-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="12838-206">16 位整数</span><span class="sxs-lookup"><span data-stu-id="12838-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="12838-207">别名 `[int16]`</span><span class="sxs-lookup"><span data-stu-id="12838-207">alias for `[int16]`</span></span>  | <span data-ttu-id="12838-208">16 位整数</span><span class="sxs-lookup"><span data-stu-id="12838-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="12838-209">16位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="12838-210">别名 `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="12838-210">alias for `[uint16]`</span></span> | <span data-ttu-id="12838-211">16位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="12838-212">32-bit integer</span><span class="sxs-lookup"><span data-stu-id="12838-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="12838-213">别名 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="12838-213">alias for `[int32]`</span></span>  | <span data-ttu-id="12838-214">32-bit integer</span><span class="sxs-lookup"><span data-stu-id="12838-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="12838-215">32位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="12838-216">别名 `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="12838-216">alias for `[uint32]`</span></span> | <span data-ttu-id="12838-217">32位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="12838-218">64 位整数</span><span class="sxs-lookup"><span data-stu-id="12838-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="12838-219">别名 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="12838-219">alias for `[int64]`</span></span>  | <span data-ttu-id="12838-220">64 位整数</span><span class="sxs-lookup"><span data-stu-id="12838-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="12838-221">64位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="12838-222">别名 `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="12838-222">alias for `[uint64]`</span></span> | <span data-ttu-id="12838-223">64位整数 (无符号) </span><span class="sxs-lookup"><span data-stu-id="12838-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="12838-224">请参阅 [BigInteger 结构][bigint]</span><span class="sxs-lookup"><span data-stu-id="12838-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="12838-225">单精度浮点</span><span class="sxs-lookup"><span data-stu-id="12838-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="12838-226">别名 `[single]`</span><span class="sxs-lookup"><span data-stu-id="12838-226">alias for `[single]`</span></span> | <span data-ttu-id="12838-227">单精度浮点</span><span class="sxs-lookup"><span data-stu-id="12838-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="12838-228">双精度浮点</span><span class="sxs-lookup"><span data-stu-id="12838-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="12838-229">128位浮点</span><span class="sxs-lookup"><span data-stu-id="12838-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="12838-230">PowerShell 6.2 中添加了以下类型加速器： `[short]` 、 `[ushort]` 、 `[uint]` 和 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="12838-231">示例</span><span class="sxs-lookup"><span data-stu-id="12838-231">Examples</span></span>

<span data-ttu-id="12838-232">下表包含几个数字文本示例，并列出它们的类型和值：</span><span class="sxs-lookup"><span data-stu-id="12838-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="12838-233">数字</span><span class="sxs-lookup"><span data-stu-id="12838-233">Number</span></span>    |    <span data-ttu-id="12838-234">类型</span><span class="sxs-lookup"><span data-stu-id="12838-234">Type</span></span>    |    <span data-ttu-id="12838-235">值</span><span class="sxs-lookup"><span data-stu-id="12838-235">Value</span></span>     |
| ----------: | ---------- | -----------: |
|         <span data-ttu-id="12838-236">100</span><span class="sxs-lookup"><span data-stu-id="12838-236">100</span></span> | <span data-ttu-id="12838-237">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-237">Int32</span></span>      |          <span data-ttu-id="12838-238">100</span><span class="sxs-lookup"><span data-stu-id="12838-238">100</span></span> |
|        <span data-ttu-id="12838-239">100u</span><span class="sxs-lookup"><span data-stu-id="12838-239">100u</span></span> | <span data-ttu-id="12838-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="12838-240">UInt32</span></span>     |          <span data-ttu-id="12838-241">100</span><span class="sxs-lookup"><span data-stu-id="12838-241">100</span></span> |
|        <span data-ttu-id="12838-242">100D</span><span class="sxs-lookup"><span data-stu-id="12838-242">100D</span></span> | <span data-ttu-id="12838-243">小数</span><span class="sxs-lookup"><span data-stu-id="12838-243">Decimal</span></span>    |          <span data-ttu-id="12838-244">100</span><span class="sxs-lookup"><span data-stu-id="12838-244">100</span></span> |
|        <span data-ttu-id="12838-245">100l</span><span class="sxs-lookup"><span data-stu-id="12838-245">100l</span></span> | <span data-ttu-id="12838-246">Int64</span><span class="sxs-lookup"><span data-stu-id="12838-246">Int64</span></span>      |          <span data-ttu-id="12838-247">100</span><span class="sxs-lookup"><span data-stu-id="12838-247">100</span></span> |
|       <span data-ttu-id="12838-248">100uL</span><span class="sxs-lookup"><span data-stu-id="12838-248">100uL</span></span> | <span data-ttu-id="12838-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="12838-249">UInt64</span></span>     |          <span data-ttu-id="12838-250">100</span><span class="sxs-lookup"><span data-stu-id="12838-250">100</span></span> |
|       <span data-ttu-id="12838-251">100us</span><span class="sxs-lookup"><span data-stu-id="12838-251">100us</span></span> | <span data-ttu-id="12838-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="12838-252">UInt16</span></span>     |          <span data-ttu-id="12838-253">100</span><span class="sxs-lookup"><span data-stu-id="12838-253">100</span></span> |
|       <span data-ttu-id="12838-254">100uy</span><span class="sxs-lookup"><span data-stu-id="12838-254">100uy</span></span> | <span data-ttu-id="12838-255">Byte</span><span class="sxs-lookup"><span data-stu-id="12838-255">Byte</span></span>       |          <span data-ttu-id="12838-256">100</span><span class="sxs-lookup"><span data-stu-id="12838-256">100</span></span> |
|        <span data-ttu-id="12838-257">100y</span><span class="sxs-lookup"><span data-stu-id="12838-257">100y</span></span> | <span data-ttu-id="12838-258">SByte</span><span class="sxs-lookup"><span data-stu-id="12838-258">SByte</span></span>      |          <span data-ttu-id="12838-259">100</span><span class="sxs-lookup"><span data-stu-id="12838-259">100</span></span> |
|         <span data-ttu-id="12838-260">1e2</span><span class="sxs-lookup"><span data-stu-id="12838-260">1e2</span></span> | <span data-ttu-id="12838-261">Double</span><span class="sxs-lookup"><span data-stu-id="12838-261">Double</span></span>     |          <span data-ttu-id="12838-262">100</span><span class="sxs-lookup"><span data-stu-id="12838-262">100</span></span> |
|        <span data-ttu-id="12838-263">1. e2</span><span class="sxs-lookup"><span data-stu-id="12838-263">1.e2</span></span> | <span data-ttu-id="12838-264">Double</span><span class="sxs-lookup"><span data-stu-id="12838-264">Double</span></span>     |          <span data-ttu-id="12838-265">100</span><span class="sxs-lookup"><span data-stu-id="12838-265">100</span></span> |
|       <span data-ttu-id="12838-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="12838-266">0x1e2</span></span> | <span data-ttu-id="12838-267">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-267">Int32</span></span>      |          <span data-ttu-id="12838-268">482</span><span class="sxs-lookup"><span data-stu-id="12838-268">482</span></span> |
|      <span data-ttu-id="12838-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="12838-269">0x1e2L</span></span> | <span data-ttu-id="12838-270">Int64</span><span class="sxs-lookup"><span data-stu-id="12838-270">Int64</span></span>      |          <span data-ttu-id="12838-271">482</span><span class="sxs-lookup"><span data-stu-id="12838-271">482</span></span> |
|      <span data-ttu-id="12838-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="12838-272">0x1e2D</span></span> | <span data-ttu-id="12838-273">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-273">Int32</span></span>      |         <span data-ttu-id="12838-274">7725</span><span class="sxs-lookup"><span data-stu-id="12838-274">7725</span></span> |
|        <span data-ttu-id="12838-275">482D</span><span class="sxs-lookup"><span data-stu-id="12838-275">482D</span></span> | <span data-ttu-id="12838-276">小数</span><span class="sxs-lookup"><span data-stu-id="12838-276">Decimal</span></span>    |          <span data-ttu-id="12838-277">482</span><span class="sxs-lookup"><span data-stu-id="12838-277">482</span></span> |
|       <span data-ttu-id="12838-278">482gb</span><span class="sxs-lookup"><span data-stu-id="12838-278">482gb</span></span> | <span data-ttu-id="12838-279">Int64</span><span class="sxs-lookup"><span data-stu-id="12838-279">Int64</span></span>      | <span data-ttu-id="12838-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="12838-280">517543559168</span></span> |
|      <span data-ttu-id="12838-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="12838-281">482ngb</span></span> | <span data-ttu-id="12838-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="12838-282">BigInteger</span></span> | <span data-ttu-id="12838-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="12838-283">517543559168</span></span> |
|    <span data-ttu-id="12838-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="12838-284">0x1e2lgb</span></span> | <span data-ttu-id="12838-285">Int64</span><span class="sxs-lookup"><span data-stu-id="12838-285">Int64</span></span>      | <span data-ttu-id="12838-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="12838-286">517543559168</span></span> |
|   <span data-ttu-id="12838-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="12838-287">0b1011011</span></span> | <span data-ttu-id="12838-288">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-288">Int32</span></span>      |           <span data-ttu-id="12838-289">91</span><span class="sxs-lookup"><span data-stu-id="12838-289">91</span></span> |
|     <span data-ttu-id="12838-290">0xFFFFs</span><span class="sxs-lookup"><span data-stu-id="12838-290">0xFFFFs</span></span> | <span data-ttu-id="12838-291">Int16</span><span class="sxs-lookup"><span data-stu-id="12838-291">Int16</span></span>      |           <span data-ttu-id="12838-292">-1</span><span class="sxs-lookup"><span data-stu-id="12838-292">-1</span></span> |
|  <span data-ttu-id="12838-293">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="12838-293">0xFFFFFFFF</span></span> | <span data-ttu-id="12838-294">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-294">Int32</span></span>      |           <span data-ttu-id="12838-295">-1</span><span class="sxs-lookup"><span data-stu-id="12838-295">-1</span></span> |
| <span data-ttu-id="12838-296">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="12838-296">-0xFFFFFFFF</span></span> | <span data-ttu-id="12838-297">Int32</span><span class="sxs-lookup"><span data-stu-id="12838-297">Int32</span></span>      |            <span data-ttu-id="12838-298">1</span><span class="sxs-lookup"><span data-stu-id="12838-298">1</span></span> |
| <span data-ttu-id="12838-299">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="12838-299">0xFFFFFFFFu</span></span> | <span data-ttu-id="12838-300">UInt32</span><span class="sxs-lookup"><span data-stu-id="12838-300">UInt32</span></span>     |   <span data-ttu-id="12838-301">4294967295</span><span class="sxs-lookup"><span data-stu-id="12838-301">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="12838-302">使用二进制或十六进制数字</span><span class="sxs-lookup"><span data-stu-id="12838-302">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="12838-303">如果和仅当指定了后缀，则很大的二进制或十六进制文本可以返回， `[bigint]` 而不是分析失败 `n` 。</span><span class="sxs-lookup"><span data-stu-id="12838-303">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="12838-304">即使是范围，也仍会考虑符号位 `[decimal]` ，但是：</span><span class="sxs-lookup"><span data-stu-id="12838-304">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="12838-305">如果二进制字符串是8位长的整数，则将最高位视为符号位。</span><span class="sxs-lookup"><span data-stu-id="12838-305">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="12838-306">如果十六进制字符串的长度为8的倍数，则其第一个数字等于8或更高，则该数字被视为负值。</span><span class="sxs-lookup"><span data-stu-id="12838-306">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="12838-307">在二进制和十六进制文本上指定无符号后缀将忽略符号位。</span><span class="sxs-lookup"><span data-stu-id="12838-307">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="12838-308">例如， `0xFFFFFFFF` 返回 `-1` ，但 `0xFFFFFFFFu` 返回 `[uint]::MaxValue` 4294967295 的。</span><span class="sxs-lookup"><span data-stu-id="12838-308">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="12838-309">在 PowerShell 7.1 中，在十六进制文本上使用类型后缀现在将返回该类型的带符号值。</span><span class="sxs-lookup"><span data-stu-id="12838-309">In PowerShell 7.1, using a type suffix on a hex literal now returns a signed value of that type.</span></span> <span data-ttu-id="12838-310">例如，在 PowerShell 7.0 中，表达式将 `0xFFFFs` 返回错误，因为正值对于类型太大 `[int16]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-310">For example, in PowerShell 7.0 the expression `0xFFFFs` returns an error because the positive value is too large for an `[int16]` type.</span></span>
<span data-ttu-id="12838-311">PowerShell 7.1 将此解释为 `-1` `[int16]` 类型。</span><span class="sxs-lookup"><span data-stu-id="12838-311">PowerShell 7.1 interprets this as `-1` that is an `[int16]` type.</span></span>

<span data-ttu-id="12838-312">使用将文本作为前缀 `0` 将绕过此，并被视为无符号。</span><span class="sxs-lookup"><span data-stu-id="12838-312">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="12838-313">例如：`0b011111111`。</span><span class="sxs-lookup"><span data-stu-id="12838-313">For example: `0b011111111`.</span></span> <span data-ttu-id="12838-314">当使用范围中的文本时，这可能是必需 `[bigint]` 的，因为 `u` 和 `n` 后缀不能组合在一起。</span><span class="sxs-lookup"><span data-stu-id="12838-314">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="12838-315">还可以使用前缀来否定二进制和十六进制文本 `-` 。</span><span class="sxs-lookup"><span data-stu-id="12838-315">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="12838-316">这可能会导致正数，因为允许使用符号位。</span><span class="sxs-lookup"><span data-stu-id="12838-316">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="12838-317">对于 BigInteger 的数字，将接受符号位：</span><span class="sxs-lookup"><span data-stu-id="12838-317">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="12838-318">BigInteger 后缀 hex 将任何文本的高位（长度为8个字符，长度为8个字符）视为符号位。</span><span class="sxs-lookup"><span data-stu-id="12838-318">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="12838-319">长度不包括 `0x` 前缀或任何后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-319">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="12838-320">BigInteger 后缀后缀接受96和128个字符的符号位，并在之后每隔8个字符。</span><span class="sxs-lookup"><span data-stu-id="12838-320">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="12838-321">类似于数字文本的命令</span><span class="sxs-lookup"><span data-stu-id="12838-321">Commands that look like numeric literals</span></span>

<span data-ttu-id="12838-322">任何类似于有效数字文本的命令都必须使用 call 运算符 (`&`) 执行，否则它将被解释为数值。</span><span class="sxs-lookup"><span data-stu-id="12838-322">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="12838-323">格式不正确的文本与类似的语法 `1usgb` 将导致以下错误：</span><span class="sxs-lookup"><span data-stu-id="12838-323">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="12838-324">但是，包含无效语法的格式不正确的文本 `1gbus` 将被解释为标准的 bare 字符串，可以在可以调用命令的上下文中将其解释为有效的命令名。</span><span class="sxs-lookup"><span data-stu-id="12838-324">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="12838-325">访问数字对象的属性和方法</span><span class="sxs-lookup"><span data-stu-id="12838-325">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="12838-326">若要访问数字文本的成员，需要将文本括在括号中。</span><span class="sxs-lookup"><span data-stu-id="12838-326">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="12838-327">文本不具有小数点</span><span class="sxs-lookup"><span data-stu-id="12838-327">The literal does not have a decimal point</span></span>
- <span data-ttu-id="12838-328">小数点后的文本不包含任何数字</span><span class="sxs-lookup"><span data-stu-id="12838-328">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="12838-329">文本没有后缀</span><span class="sxs-lookup"><span data-stu-id="12838-329">The literal does not have a suffix</span></span>

<span data-ttu-id="12838-330">例如，下面的示例将失败：</span><span class="sxs-lookup"><span data-stu-id="12838-330">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="12838-331">下面的示例工作：</span><span class="sxs-lookup"><span data-stu-id="12838-331">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="12838-332">前两个示例在不将文本值括在括号中的情况下工作，因为 PowerShell 分析器可以确定数字文本的结束位置和 **GetType** 方法的启动位置。</span><span class="sxs-lookup"><span data-stu-id="12838-332">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="12838-333">PowerShell 如何分析数字文本</span><span class="sxs-lookup"><span data-stu-id="12838-333">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="12838-334">PowerShell 7.0 7.0 更改了对数字文本进行分析的方式，以实现新功能。</span><span class="sxs-lookup"><span data-stu-id="12838-334">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="12838-335">分析真实数值</span><span class="sxs-lookup"><span data-stu-id="12838-335">Parsing real numeric literals</span></span>

<span data-ttu-id="12838-336">如果文字包含小数点或电子表示法，则会分析文本字符串的实数。</span><span class="sxs-lookup"><span data-stu-id="12838-336">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="12838-337">如果存在小数点后缀，则直接放入 `[decimal]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-337">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="12838-338">否则，分析为， `[Double]` 并对值应用乘数。</span><span class="sxs-lookup"><span data-stu-id="12838-338">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="12838-339">然后检查类型后缀并尝试强制转换为适当的类型。</span><span class="sxs-lookup"><span data-stu-id="12838-339">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="12838-340">如果字符串没有类型后缀，则分析为 `[Double]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-340">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="12838-341">配对整数数值</span><span class="sxs-lookup"><span data-stu-id="12838-341">Paring integer numeric literals</span></span>

<span data-ttu-id="12838-342">使用以下步骤对整数类型文本进行分析：</span><span class="sxs-lookup"><span data-stu-id="12838-342">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="12838-343">确定基数格式</span><span class="sxs-lookup"><span data-stu-id="12838-343">Determine the radix format</span></span>
   - <span data-ttu-id="12838-344">对于二进制格式，分析为 `[BigInteger]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-344">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="12838-345">对于十六进制格式， `[BigInteger]` 当值在或范围中时，分析为使用特殊的 casies 以保留原始行为 `[int]` `[long]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-345">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="12838-346">如果二进制或十六进制都不是，则通常作为进行分析 `[BigInteger]` 。</span><span class="sxs-lookup"><span data-stu-id="12838-346">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="12838-347">在尝试任何强制转换之前应用乘数值，以确保可以正确检查类型界限而不溢出。</span><span class="sxs-lookup"><span data-stu-id="12838-347">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="12838-348">检查类型后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-348">Check type suffixes.</span></span>
   - <span data-ttu-id="12838-349">检查类型限制并尝试对该类型进行分析。</span><span class="sxs-lookup"><span data-stu-id="12838-349">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="12838-350">如果未使用任何后缀，则值将按以下顺序进行边界检查，从而导致第一次成功测试确定数字的类型。</span><span class="sxs-lookup"><span data-stu-id="12838-350">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="12838-351">`[decimal]` 仅 (以10为底的文本) </span><span class="sxs-lookup"><span data-stu-id="12838-351">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="12838-352">`[double]` 仅 (以10为底的文本) </span><span class="sxs-lookup"><span data-stu-id="12838-352">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="12838-353">如果值不在 `[long]` 十六进制和二进制数的范围内，则分析将失败。</span><span class="sxs-lookup"><span data-stu-id="12838-353">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="12838-354">如果值不在 `[double]` 以10为底的整数范围内，则分析将失败。</span><span class="sxs-lookup"><span data-stu-id="12838-354">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="12838-355">必须使用后缀显式写入较高的值 `n` ，以将文本分析为 `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="12838-355">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="12838-356">分析大值文本</span><span class="sxs-lookup"><span data-stu-id="12838-356">Parsing large value literals</span></span>

<span data-ttu-id="12838-357">以前，在强制转换为任何其他类型之前，更高的整数值被分析为双精度值。</span><span class="sxs-lookup"><span data-stu-id="12838-357">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="12838-358">这会导致更高范围内的精度丢失。</span><span class="sxs-lookup"><span data-stu-id="12838-358">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="12838-359">例如：</span><span class="sxs-lookup"><span data-stu-id="12838-359">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="12838-360">若要避免此问题，你必须以字符串形式编写值，然后转换这些值：</span><span class="sxs-lookup"><span data-stu-id="12838-360">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="12838-361">在 PowerShell 7.0 中，必须使用 `N` 后缀。</span><span class="sxs-lookup"><span data-stu-id="12838-361">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="12838-362">还 `[ulong]::MaxValue` `[decimal]::MaxValue` 应使用小数点后缀表示和之间的值 `D` 以保持准确性。</span><span class="sxs-lookup"><span data-stu-id="12838-362">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="12838-363">如果没有此后缀，则这些值将 `[Double]` 使用实际分析模式进行分析。</span><span class="sxs-lookup"><span data-stu-id="12838-363">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
