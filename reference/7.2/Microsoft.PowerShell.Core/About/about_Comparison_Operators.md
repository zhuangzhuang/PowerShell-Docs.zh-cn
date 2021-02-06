---
description: 描述在 PowerShell 中比较值的运算符。
Locale: en-US
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 2bd2aa825d09078f37dba1f99fa64584dacd324d
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "99597261"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="e56b9-103">关于比较运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="e56b9-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="e56b9-104">Short description</span></span>

<span data-ttu-id="e56b9-105">PowerShell 中的比较运算符可以将集合的两个值或筛选元素与输入值进行比较。</span><span class="sxs-lookup"><span data-stu-id="e56b9-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="e56b9-106">长说明</span><span class="sxs-lookup"><span data-stu-id="e56b9-106">Long description</span></span>

<span data-ttu-id="e56b9-107">比较运算符使您可以比较值或查找与指定模式匹配的值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="e56b9-108">PowerShell 包含以下比较运算符：</span><span class="sxs-lookup"><span data-stu-id="e56b9-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="e56b9-109">类型</span><span class="sxs-lookup"><span data-stu-id="e56b9-109">Type</span></span>     |   <span data-ttu-id="e56b9-110">运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-110">Operator</span></span>   |              <span data-ttu-id="e56b9-111">比较测试</span><span class="sxs-lookup"><span data-stu-id="e56b9-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="e56b9-112">相等</span><span class="sxs-lookup"><span data-stu-id="e56b9-112">Equality</span></span>    | <span data-ttu-id="e56b9-113">-eq</span><span class="sxs-lookup"><span data-stu-id="e56b9-113">-eq</span></span>          | <span data-ttu-id="e56b9-114">equals</span><span class="sxs-lookup"><span data-stu-id="e56b9-114">equals</span></span>                                    |
|             | <span data-ttu-id="e56b9-115">-ne</span><span class="sxs-lookup"><span data-stu-id="e56b9-115">-ne</span></span>          | <span data-ttu-id="e56b9-116">不等于</span><span class="sxs-lookup"><span data-stu-id="e56b9-116">not equals</span></span>                                |
|             | <span data-ttu-id="e56b9-117">-gt</span><span class="sxs-lookup"><span data-stu-id="e56b9-117">-gt</span></span>          | <span data-ttu-id="e56b9-118">大于</span><span class="sxs-lookup"><span data-stu-id="e56b9-118">greater than</span></span>                              |
|             | <span data-ttu-id="e56b9-119">-ge</span><span class="sxs-lookup"><span data-stu-id="e56b9-119">-ge</span></span>          | <span data-ttu-id="e56b9-120">大于或等于</span><span class="sxs-lookup"><span data-stu-id="e56b9-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="e56b9-121">-lt</span><span class="sxs-lookup"><span data-stu-id="e56b9-121">-lt</span></span>          | <span data-ttu-id="e56b9-122">小于</span><span class="sxs-lookup"><span data-stu-id="e56b9-122">less than</span></span>                                 |
|             | <span data-ttu-id="e56b9-123">-le</span><span class="sxs-lookup"><span data-stu-id="e56b9-123">-le</span></span>          | <span data-ttu-id="e56b9-124">小于或等于</span><span class="sxs-lookup"><span data-stu-id="e56b9-124">less than or equal</span></span>                        |
| <span data-ttu-id="e56b9-125">Matching</span><span class="sxs-lookup"><span data-stu-id="e56b9-125">Matching</span></span>    | <span data-ttu-id="e56b9-126">-like</span><span class="sxs-lookup"><span data-stu-id="e56b9-126">-like</span></span>        | <span data-ttu-id="e56b9-127">字符串与通配符模式匹配</span><span class="sxs-lookup"><span data-stu-id="e56b9-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="e56b9-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="e56b9-128">-notlike</span></span>     | <span data-ttu-id="e56b9-129">字符串不匹配通配符模式</span><span class="sxs-lookup"><span data-stu-id="e56b9-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="e56b9-130">-match</span><span class="sxs-lookup"><span data-stu-id="e56b9-130">-match</span></span>       | <span data-ttu-id="e56b9-131">字符串匹配正则表达式模式</span><span class="sxs-lookup"><span data-stu-id="e56b9-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="e56b9-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="e56b9-132">-notmatch</span></span>    | <span data-ttu-id="e56b9-133">字符串不匹配 regex 模式</span><span class="sxs-lookup"><span data-stu-id="e56b9-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="e56b9-134">Replacement</span><span class="sxs-lookup"><span data-stu-id="e56b9-134">Replacement</span></span> | <span data-ttu-id="e56b9-135">-replace</span><span class="sxs-lookup"><span data-stu-id="e56b9-135">-replace</span></span>     | <span data-ttu-id="e56b9-136">替换匹配正则表达式模式的字符串</span><span class="sxs-lookup"><span data-stu-id="e56b9-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="e56b9-137">Containment</span><span class="sxs-lookup"><span data-stu-id="e56b9-137">Containment</span></span> | <span data-ttu-id="e56b9-138">-contains</span><span class="sxs-lookup"><span data-stu-id="e56b9-138">-contains</span></span>    | <span data-ttu-id="e56b9-139">集合包含值</span><span class="sxs-lookup"><span data-stu-id="e56b9-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="e56b9-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="e56b9-140">-notcontains</span></span> | <span data-ttu-id="e56b9-141">集合不包含值</span><span class="sxs-lookup"><span data-stu-id="e56b9-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="e56b9-142">-in</span><span class="sxs-lookup"><span data-stu-id="e56b9-142">-in</span></span>          | <span data-ttu-id="e56b9-143">值在集合中</span><span class="sxs-lookup"><span data-stu-id="e56b9-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="e56b9-144">-notin</span><span class="sxs-lookup"><span data-stu-id="e56b9-144">-notin</span></span>       | <span data-ttu-id="e56b9-145">值不在集合中</span><span class="sxs-lookup"><span data-stu-id="e56b9-145">value is not in a collection</span></span>              |
| <span data-ttu-id="e56b9-146">类型</span><span class="sxs-lookup"><span data-stu-id="e56b9-146">Type</span></span>        | <span data-ttu-id="e56b9-147">-为</span><span class="sxs-lookup"><span data-stu-id="e56b9-147">-is</span></span>          | <span data-ttu-id="e56b9-148">这两个对象属于同一类型</span><span class="sxs-lookup"><span data-stu-id="e56b9-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="e56b9-149">-isnot</span><span class="sxs-lookup"><span data-stu-id="e56b9-149">-isnot</span></span>       | <span data-ttu-id="e56b9-150">对象的类型不同</span><span class="sxs-lookup"><span data-stu-id="e56b9-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="e56b9-151">常用功能</span><span class="sxs-lookup"><span data-stu-id="e56b9-151">Common features</span></span>

<span data-ttu-id="e56b9-152">默认情况下，所有比较运算符都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e56b9-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="e56b9-153">若要使比较运算符区分大小写，请在 `c` 后面添加一个 `-` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="e56b9-154">例如， `-ceq` 是的区分大小写的版本 `-eq` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="e56b9-155">若要进行不区分大小写的显式，请 `i` 在前面添加 `-` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="e56b9-156">例如， `-ieq` 是的显式不区分大小写的版本 `-eq` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="e56b9-157">当运算符的输入是标量值时，运算符将返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="e56b9-158">当输入为集合时，运算符将返回与表达式的右侧值匹配的集合的元素。</span><span class="sxs-lookup"><span data-stu-id="e56b9-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="e56b9-159">如果集合中没有匹配项，则比较运算符返回空数组。</span><span class="sxs-lookup"><span data-stu-id="e56b9-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="e56b9-160">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="e56b9-161">有几个例外情况：</span><span class="sxs-lookup"><span data-stu-id="e56b9-161">There are a few exceptions:</span></span>

- <span data-ttu-id="e56b9-162">包含和类型运算符始终返回 **布尔** 值</span><span class="sxs-lookup"><span data-stu-id="e56b9-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="e56b9-163">`-replace`运算符返回替换结果</span><span class="sxs-lookup"><span data-stu-id="e56b9-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="e56b9-164">`-match`和 `-notmatch` 运算符还填充 `$Matches` 自动变量</span><span class="sxs-lookup"><span data-stu-id="e56b9-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable</span></span>

## <a name="equality-operators"></a><span data-ttu-id="e56b9-165">相等运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="e56b9-166">-eq 和 -ne</span><span class="sxs-lookup"><span data-stu-id="e56b9-166">-eq and -ne</span></span>

<span data-ttu-id="e56b9-167">左侧为标量时， `-eq` 如果右侧是完全匹配，则返回 **True** ，否则返回 `-eq` **False**。</span><span class="sxs-lookup"><span data-stu-id="e56b9-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="e56b9-168">`-ne` 相反;当双方均匹配时，它将返回 **False** ;否则， `-ne` 返回 True。</span><span class="sxs-lookup"><span data-stu-id="e56b9-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="e56b9-169">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="e56b9-170">如果左侧是集合，则 `-eq` 返回与右侧匹配的成员，同时对 `-ne` 其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="e56b9-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="e56b9-171">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="e56b9-172">这些运算符处理集合的所有元素。</span><span class="sxs-lookup"><span data-stu-id="e56b9-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="e56b9-173">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="e56b9-174">相等运算符接受任意两个对象，而不只是标量或集合。</span><span class="sxs-lookup"><span data-stu-id="e56b9-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="e56b9-175">但不保证比较结果对于最终用户有意义。</span><span class="sxs-lookup"><span data-stu-id="e56b9-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="e56b9-176">下面的示例演示了该问题。</span><span class="sxs-lookup"><span data-stu-id="e56b9-176">The following example demonstrates the issue.</span></span>

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

<span data-ttu-id="e56b9-177">在此示例中，我们创建了两个具有相同属性的对象。</span><span class="sxs-lookup"><span data-stu-id="e56b9-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="e56b9-178">然而，相等性测试结果为 **False** ，因为它们是不同的对象。</span><span class="sxs-lookup"><span data-stu-id="e56b9-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="e56b9-179">若要创建可比较类，需要在类中实现[IEquatable \<T> ][2] 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="e56b9-180">下面的示例演示了实现 [IEquatable \<T>][2]的 **MyFileInfoSet** 类的分部实现，它具有两个属性：**文件** 和 **大小**。</span><span class="sxs-lookup"><span data-stu-id="e56b9-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="e56b9-181">`Equals()`如果两个 **MyFileInfoSet** 对象的文件和大小属性相同，则该方法返回 True。</span><span class="sxs-lookup"><span data-stu-id="e56b9-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

<span data-ttu-id="e56b9-182">比较任意对象的一个明显示例就是找出这些对象是否为 null。</span><span class="sxs-lookup"><span data-stu-id="e56b9-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="e56b9-183">但如果需要确定变量是否为 `$null` ，则必须将置于 `$null` 相等运算符的左侧。</span><span class="sxs-lookup"><span data-stu-id="e56b9-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="e56b9-184">将其放在右侧不会执行所需的操作。</span><span class="sxs-lookup"><span data-stu-id="e56b9-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="e56b9-185">例如，假设 `$a` 数组包含 null 元素：</span><span class="sxs-lookup"><span data-stu-id="e56b9-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="e56b9-186">以下 `$a` 不为空的测试。</span><span class="sxs-lookup"><span data-stu-id="e56b9-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
False
```

<span data-ttu-id="e56b9-187">不过，以下是从以下文件中注销所有 null 元素 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="e56b9-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="e56b9-188">-gt、-ge、-lt 和-le</span><span class="sxs-lookup"><span data-stu-id="e56b9-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="e56b9-189">`-gt`、 `-ge` 、 `-lt` 和的 `-le` 行为与此类似。</span><span class="sxs-lookup"><span data-stu-id="e56b9-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="e56b9-190">当双方都为标量时，它们会返回 **True** 或 **False** ，具体取决于两个边的比较方式：</span><span class="sxs-lookup"><span data-stu-id="e56b9-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="e56b9-191">操作员</span><span class="sxs-lookup"><span data-stu-id="e56b9-191">Operator</span></span> | <span data-ttu-id="e56b9-192">当 .。。</span><span class="sxs-lookup"><span data-stu-id="e56b9-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="e56b9-193">-gt</span><span class="sxs-lookup"><span data-stu-id="e56b9-193">-gt</span></span>      | <span data-ttu-id="e56b9-194">左侧更大</span><span class="sxs-lookup"><span data-stu-id="e56b9-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="e56b9-195">-ge</span><span class="sxs-lookup"><span data-stu-id="e56b9-195">-ge</span></span>      | <span data-ttu-id="e56b9-196">左侧大于或等于</span><span class="sxs-lookup"><span data-stu-id="e56b9-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="e56b9-197">-lt</span><span class="sxs-lookup"><span data-stu-id="e56b9-197">-lt</span></span>      | <span data-ttu-id="e56b9-198">左侧更小</span><span class="sxs-lookup"><span data-stu-id="e56b9-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="e56b9-199">-le</span><span class="sxs-lookup"><span data-stu-id="e56b9-199">-le</span></span>      | <span data-ttu-id="e56b9-200">左侧小于或等于</span><span class="sxs-lookup"><span data-stu-id="e56b9-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="e56b9-201">在下面的示例中，所有语句都返回 True。</span><span class="sxs-lookup"><span data-stu-id="e56b9-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="e56b9-202">在大多数编程语言中，大于运算符为 `>` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="e56b9-203">在 PowerShell 中，此字符用于重定向。</span><span class="sxs-lookup"><span data-stu-id="e56b9-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="e56b9-204">有关详细信息，请参阅 [about_Redirection][3]。</span><span class="sxs-lookup"><span data-stu-id="e56b9-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="e56b9-205">如果左侧是集合，则这些运算符会将集合的每个成员与右侧进行比较。</span><span class="sxs-lookup"><span data-stu-id="e56b9-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="e56b9-206">根据其逻辑，它们可以保留或丢弃成员。</span><span class="sxs-lookup"><span data-stu-id="e56b9-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="e56b9-207">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-207">Example:</span></span>

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

<span data-ttu-id="e56b9-208">这些运算符可用于实现 [system.icomparable][1]的任何类。</span><span class="sxs-lookup"><span data-stu-id="e56b9-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="e56b9-209">示例:</span><span class="sxs-lookup"><span data-stu-id="e56b9-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="e56b9-210">下面的示例演示在美国标准键盘上没有符号，该键盘在 "a" 后进行排序。</span><span class="sxs-lookup"><span data-stu-id="e56b9-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="e56b9-211">它将包含所有此类符号的集馈送到 `-gt` 运算符，以将它们与 "a" 进行比较。</span><span class="sxs-lookup"><span data-stu-id="e56b9-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="e56b9-212">输出为空数组。</span><span class="sxs-lookup"><span data-stu-id="e56b9-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="e56b9-213">如果两个运算符的两边不合理，则这些运算符将引发非终止错误。</span><span class="sxs-lookup"><span data-stu-id="e56b9-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="e56b9-214">匹配运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-214">Matching operators</span></span>

<span data-ttu-id="e56b9-215">匹配运算符 (`-like` 、 `-notlike` 、 `-match` 和 `-notmatch`) 查找匹配或与指定模式不匹配的元素。</span><span class="sxs-lookup"><span data-stu-id="e56b9-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="e56b9-216">和的模式 `-like` `-notlike` 是包含 `*` 、和)  (通配符表达式 `?` `[ ]` ， `-match` 并 `-notmatch` 接受正则表达式 (正则表达式) 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="e56b9-217">语法为：</span><span class="sxs-lookup"><span data-stu-id="e56b9-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="e56b9-218">当这些运算符的输入是标量值时，它们将返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="e56b9-219">当输入是值的集合时，运算符返回任何匹配的成员。</span><span class="sxs-lookup"><span data-stu-id="e56b9-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="e56b9-220">如果集合中没有匹配项，则运算符将返回空数组。</span><span class="sxs-lookup"><span data-stu-id="e56b9-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="e56b9-221">-like 和-notlike</span><span class="sxs-lookup"><span data-stu-id="e56b9-221">-like and -notlike</span></span>

<span data-ttu-id="e56b9-222">`-like` 和 `-notlike` 的行为与 `-eq` 和类似 `-ne` ，但右侧可以是包含 [通配符](about_Wildcards.md)的字符串。</span><span class="sxs-lookup"><span data-stu-id="e56b9-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="e56b9-223">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-223">Example:</span></span>

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a><span data-ttu-id="e56b9-224">-match 和-notmatch</span><span class="sxs-lookup"><span data-stu-id="e56b9-224">-match and -notmatch</span></span>

<span data-ttu-id="e56b9-225">`-match` 和 `-notmatch` 使用正则表达式搜索左侧值中的模式。</span><span class="sxs-lookup"><span data-stu-id="e56b9-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="e56b9-226">正则表达式可以匹配复杂模式，如电子邮件地址、UNC 路径或格式化电话号码。</span><span class="sxs-lookup"><span data-stu-id="e56b9-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="e56b9-227">右侧字符串必须符合 [正则表达式](about_Regular_Expressions.md) 规则。</span><span class="sxs-lookup"><span data-stu-id="e56b9-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="e56b9-228">标量示例：</span><span class="sxs-lookup"><span data-stu-id="e56b9-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="e56b9-229">如果输入是集合，则运算符将返回该集合的匹配成员。</span><span class="sxs-lookup"><span data-stu-id="e56b9-229">If the input is a collection, the operators return the matching members of that collection.</span></span>

<span data-ttu-id="e56b9-230">集合示例：</span><span class="sxs-lookup"><span data-stu-id="e56b9-230">Collection examples:</span></span>

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

<span data-ttu-id="e56b9-231">`-match` 和 `-notmatch` 支持 regex 捕获组。</span><span class="sxs-lookup"><span data-stu-id="e56b9-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="e56b9-232">每次运行时，它们将覆盖 `$Matches` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="e56b9-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="e56b9-233">当 `<input>` 是集合时， `$Matches` 变量是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="e56b9-234">`$Matches` 是始终具有名为 "0" 的键的 **哈希表** ，它存储整个匹配项。</span><span class="sxs-lookup"><span data-stu-id="e56b9-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="e56b9-235">如果正则表达式包含捕获组，则 `$Matches` 包含每个组的其他键。</span><span class="sxs-lookup"><span data-stu-id="e56b9-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="e56b9-236">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-236">Example:</span></span>

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

<span data-ttu-id="e56b9-237">有关详细信息，请参阅 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e56b9-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="e56b9-238">替换运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="e56b9-239">用正则表达式替换</span><span class="sxs-lookup"><span data-stu-id="e56b9-239">Replacement with regular expressions</span></span>

<span data-ttu-id="e56b9-240">与类似 `-match` ， `-replace` 运算符使用正则表达式查找指定的模式。</span><span class="sxs-lookup"><span data-stu-id="e56b9-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="e56b9-241">但与不同的 `-match` 是，它将匹配项替换为另一个指定的值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="e56b9-242">语法：</span><span class="sxs-lookup"><span data-stu-id="e56b9-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="e56b9-243">使用正则表达式将运算符替换为指定值的全部或部分值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="e56b9-244">对于许多管理任务（如重命名文件），都可以使用运算符。</span><span class="sxs-lookup"><span data-stu-id="e56b9-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="e56b9-245">例如，以下命令将所有文件的文件扩展名更改 `.txt` 为 `.log` ：</span><span class="sxs-lookup"><span data-stu-id="e56b9-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="e56b9-246">默认情况下， `-replace` 运算符不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e56b9-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="e56b9-247">若要区分大小写，请使用 `-creplace` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="e56b9-248">若要使它显式不区分大小写，请使用 `-ireplace` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="e56b9-249">示例:</span><span class="sxs-lookup"><span data-stu-id="e56b9-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="e56b9-250">正则表达式替换</span><span class="sxs-lookup"><span data-stu-id="e56b9-250">Regular expressions substitutions</span></span>

<span data-ttu-id="e56b9-251">还可以使用正则表达式，使用捕获组和替换动态替换文本。</span><span class="sxs-lookup"><span data-stu-id="e56b9-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="e56b9-252">可以 `<substitute>` 使用分组标识符之前的美元符号 () 字符，在字符串中引用捕获组 `$` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="e56b9-253">在下面的示例中， `-replace` 运算符接受格式为的用户名， `DomainName\Username` 并将转换为以下 `Username@DomainName` 格式：</span><span class="sxs-lookup"><span data-stu-id="e56b9-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<Username>[\w-.]+)\\(?<DomainName>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="e56b9-254">该 `$` 字符具有 PowerShell 和正则表达式中的 syntatic 角色：</span><span class="sxs-lookup"><span data-stu-id="e56b9-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="e56b9-255">在 PowerShell 中，在双引号之间，它指定变量并充当子表达式运算符。</span><span class="sxs-lookup"><span data-stu-id="e56b9-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="e56b9-256">在正则表达式搜索字符串中，它表示行的结尾</span><span class="sxs-lookup"><span data-stu-id="e56b9-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="e56b9-257">在 Regex 替换字符串中，它表示捕获的组，因此，请务必将正则表达式放在单引号之间，或者在它们之前插入反撇号 (`` ` ``) 字符。</span><span class="sxs-lookup"><span data-stu-id="e56b9-257">In Regex substitution strings, it denotes captured groups As such, be sure to to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="e56b9-258">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="e56b9-259">`$$` 在正则表达式中表示文字 `$` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="e56b9-260">此 `$$` 在替换字符串中，用于在生成的 `$` 替换中包含一个文本。</span><span class="sxs-lookup"><span data-stu-id="e56b9-260">This `$$` in the substitution string to include a a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="e56b9-261">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="e56b9-262">若要了解详细信息，请参阅[正则表达式中的][4] [about_Regular_Expressions](about_Regular_Expressions.md)和替换。</span><span class="sxs-lookup"><span data-stu-id="e56b9-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="e56b9-263">在集合中替换</span><span class="sxs-lookup"><span data-stu-id="e56b9-263">Substituting in a collection</span></span>

<span data-ttu-id="e56b9-264">如果 `<input>` 到运算符为 `-replace` 集合，则 PowerShell 会将替换应用于集合中的每个值。</span><span class="sxs-lookup"><span data-stu-id="e56b9-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="e56b9-265">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a><span data-ttu-id="e56b9-266">使用脚本块替换</span><span class="sxs-lookup"><span data-stu-id="e56b9-266">Replacement with a script block</span></span>

<span data-ttu-id="e56b9-267">在 PowerShell 6 及更高版本中， `-replace` 操作员还接受执行替换的脚本块。</span><span class="sxs-lookup"><span data-stu-id="e56b9-267">In PowerShell 6 and later, the `-replace` operator also accepts a script block that performs the replacement.</span></span> <span data-ttu-id="e56b9-268">脚本块为每个匹配项运行一次。</span><span class="sxs-lookup"><span data-stu-id="e56b9-268">The script block runs once for every match.</span></span>

<span data-ttu-id="e56b9-269">语法：</span><span class="sxs-lookup"><span data-stu-id="e56b9-269">Syntax:</span></span>

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

<span data-ttu-id="e56b9-270">在脚本块中，使用 `$_` 自动变量来访问被替换的输入文本和其他有用的信息。</span><span class="sxs-lookup"><span data-stu-id="e56b9-270">Within the script block, use the `$_` automatic variable to access the input text being replaced and other useful information.</span></span> <span data-ttu-id="e56b9-271">此变量的类类型为 [system.text.regularexpressions][2]。</span><span class="sxs-lookup"><span data-stu-id="e56b9-271">This variable's class type is [System.Text.RegularExpressions.Match][2].</span></span>

<span data-ttu-id="e56b9-272">下面的示例将三个数字的每个序列替换为等效字符。</span><span class="sxs-lookup"><span data-stu-id="e56b9-272">The following example replaces each sequence of three digits with the character equivalents.</span></span> <span data-ttu-id="e56b9-273">脚本块针对需要替换的三个数字组运行。</span><span class="sxs-lookup"><span data-stu-id="e56b9-273">The script block runs for each set of three digits that needs to be replaced.</span></span>

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a><span data-ttu-id="e56b9-274">包含运算符</span><span class="sxs-lookup"><span data-stu-id="e56b9-274">Containment operators</span></span>

<span data-ttu-id="e56b9-275">包含运算符 (`-contains` 、 `-notcontains` 、 `-in` 和 `-notin`) 与相等运算符类似，不同之处在于它们始终返回一个 **布尔** 值，即使输入是集合也是如此。</span><span class="sxs-lookup"><span data-stu-id="e56b9-275">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="e56b9-276">这些运算符在检测到第一个匹配项后会立即停止比较，而相等运算符则计算所有输入成员。</span><span class="sxs-lookup"><span data-stu-id="e56b9-276">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="e56b9-277">在非常大的集合中，这些运算符返回的速度比相等运算符更快。</span><span class="sxs-lookup"><span data-stu-id="e56b9-277">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="e56b9-278">语法：</span><span class="sxs-lookup"><span data-stu-id="e56b9-278">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="e56b9-279">-contains 和-notcontains</span><span class="sxs-lookup"><span data-stu-id="e56b9-279">-contains and -notcontains</span></span>

<span data-ttu-id="e56b9-280">这些运算符用于判断集是否包含特定元素。</span><span class="sxs-lookup"><span data-stu-id="e56b9-280">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="e56b9-281">`-contains` 当右侧 (测试对象) 与集中的元素之一匹配时，返回 True。</span><span class="sxs-lookup"><span data-stu-id="e56b9-281">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="e56b9-282">`-notcontains` 改为返回 False。</span><span class="sxs-lookup"><span data-stu-id="e56b9-282">`-notcontains` returns False instead.</span></span> <span data-ttu-id="e56b9-283">如果测试对象是集合，则这些运算符使用引用相等性，即，它们检查其中一个集合的元素是否为测试对象的相同实例。</span><span class="sxs-lookup"><span data-stu-id="e56b9-283">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="e56b9-284">示例:</span><span class="sxs-lookup"><span data-stu-id="e56b9-284">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="e56b9-285">更复杂的示例：</span><span class="sxs-lookup"><span data-stu-id="e56b9-285">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a><span data-ttu-id="e56b9-286">-in 和-notin</span><span class="sxs-lookup"><span data-stu-id="e56b9-286">-in and -notin</span></span>

<span data-ttu-id="e56b9-287">`-in`和- `notin` 运算符在 PowerShell 3 中引入，作为和运算符的语法反转 `contains` `-notcontain` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-287">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="e56b9-288">`-in`当左侧 `<test-object>` 与集中的元素之一匹配时，返回 True。</span><span class="sxs-lookup"><span data-stu-id="e56b9-288">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="e56b9-289">`-notin` 改 **为返回 False** 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-289">`-notin` returns **False** instead.</span></span> <span data-ttu-id="e56b9-290">如果测试对象是一个集，则这些运算符使用引用相等性来检查该集的一个元素是否为该测试对象的相同实例。</span><span class="sxs-lookup"><span data-stu-id="e56b9-290">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="e56b9-291">下面的示例执行与示例相同的操作 `-contain` `-notcontain` ，但它们是用和编写的 `-in` `-notin` 。</span><span class="sxs-lookup"><span data-stu-id="e56b9-291">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="e56b9-292">更复杂的示例：</span><span class="sxs-lookup"><span data-stu-id="e56b9-292">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a><span data-ttu-id="e56b9-293">类型比较</span><span class="sxs-lookup"><span data-stu-id="e56b9-293">Type comparison</span></span>

<span data-ttu-id="e56b9-294"> (和) 的类型比较运算符 `-is` `-isnot` 用于确定对象是否为特定类型。</span><span class="sxs-lookup"><span data-stu-id="e56b9-294">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="e56b9-295">语法：</span><span class="sxs-lookup"><span data-stu-id="e56b9-295">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="e56b9-296">例如：</span><span class="sxs-lookup"><span data-stu-id="e56b9-296">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="e56b9-297">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e56b9-297">SEE ALSO</span></span>

- [<span data-ttu-id="e56b9-298">about_Operators</span><span class="sxs-lookup"><span data-stu-id="e56b9-298">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="e56b9-299">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="e56b9-299">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="e56b9-300">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="e56b9-300">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="e56b9-301">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e56b9-301">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="e56b9-302">Foreach-对象</span><span class="sxs-lookup"><span data-stu-id="e56b9-302">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="e56b9-303">Where-Object</span><span class="sxs-lookup"><span data-stu-id="e56b9-303">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
