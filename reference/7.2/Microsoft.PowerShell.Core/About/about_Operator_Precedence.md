---
description: 按优先顺序列出 PowerShell 运算符。
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d4031a9d9a67340470d5418a9c2d3e33c5caed13
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595617"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="deae8-103">关于运算符优先级</span><span class="sxs-lookup"><span data-stu-id="deae8-103">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="deae8-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="deae8-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="deae8-105">按优先顺序列出 PowerShell 运算符。</span><span class="sxs-lookup"><span data-stu-id="deae8-105">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="deae8-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="deae8-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="deae8-107">PowerShell 运算符使你可以构建简单但功能强大的表达式。</span><span class="sxs-lookup"><span data-stu-id="deae8-107">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="deae8-108">本主题按优先顺序列出运算符。</span><span class="sxs-lookup"><span data-stu-id="deae8-108">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="deae8-109">优先顺序是指当多个运算符出现在同一表达式中时，PowerShell 计算操作员的顺序。</span><span class="sxs-lookup"><span data-stu-id="deae8-109">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="deae8-110">如果运算符具有相同的优先级，则 PowerShell 会在表达式中出现时从左到右进行计算。</span><span class="sxs-lookup"><span data-stu-id="deae8-110">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="deae8-111">赋值运算符、强制转换运算符和求反运算符 (`!` 、 `-not` `-bnot`) （从右到左计算）。</span><span class="sxs-lookup"><span data-stu-id="deae8-111">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="deae8-112">可以使用箱（如括号）来替代标准优先顺序，并强制 PowerShell 在 unenclosed 部分之前计算表达式中包含的部分。</span><span class="sxs-lookup"><span data-stu-id="deae8-112">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="deae8-113">在下面的列表中，运算符按其计算顺序列出。</span><span class="sxs-lookup"><span data-stu-id="deae8-113">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="deae8-114">同一行或同一组中的运算符具有相同的优先级。</span><span class="sxs-lookup"><span data-stu-id="deae8-114">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="deae8-115">Operator 列列出运算符。</span><span class="sxs-lookup"><span data-stu-id="deae8-115">The Operator column lists the operators.</span></span> <span data-ttu-id="deae8-116">"引用" 列列出了用于描述操作员的 PowerShell 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="deae8-116">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="deae8-117">若要显示该主题，请键入 `get-help <topic-name>` 。</span><span class="sxs-lookup"><span data-stu-id="deae8-117">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="deae8-118">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="deae8-118">OPERATOR</span></span>         |           <span data-ttu-id="deae8-119">参考</span><span class="sxs-lookup"><span data-stu-id="deae8-119">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | <span data-ttu-id="deae8-120">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-120">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-121">`. ?.` (成员访问) </span><span class="sxs-lookup"><span data-stu-id="deae8-121">`. ?.` (member access)</span></span>   | <span data-ttu-id="deae8-122">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-122">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-123">`::` (静态) </span><span class="sxs-lookup"><span data-stu-id="deae8-123">`::` (static)</span></span>            | <span data-ttu-id="deae8-124">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-124">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-125">`[0] ?[0]` (索引运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-125">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="deae8-126">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-126">[about_Operators][]</span></span>         |
| <span data-ttu-id="deae8-127">`[int]` (cast 运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-127">`[int]` (cast operators)</span></span> | <span data-ttu-id="deae8-128">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-128">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-129">`-split` (一元) </span><span class="sxs-lookup"><span data-stu-id="deae8-129">`-split` (unary)</span></span>         | <span data-ttu-id="deae8-130">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="deae8-130">[about_Split][]</span></span>                |
| <span data-ttu-id="deae8-131">`-join` (一元) </span><span class="sxs-lookup"><span data-stu-id="deae8-131">`-join` (unary)</span></span>          | <span data-ttu-id="deae8-132">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="deae8-132">[about_Join][]</span></span>                 |
| <span data-ttu-id="deae8-133">`,` (逗号运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-133">`,` (comma operator)</span></span>     | <span data-ttu-id="deae8-134">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-134">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="deae8-135">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-135">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="deae8-136">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-136">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="deae8-137">`..` (范围运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-137">`..` (range operator)</span></span>    | <span data-ttu-id="deae8-138">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-138">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-139">`-f` (格式运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-139">`-f` (format operator)</span></span>   | <span data-ttu-id="deae8-140">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-140">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-141">`-` (一元/负) </span><span class="sxs-lookup"><span data-stu-id="deae8-141">`-` (unary/negative)</span></span>     | <span data-ttu-id="deae8-142">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-142">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="deae8-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-143">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="deae8-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-144">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="deae8-145">下面的运算符组具有相同的优先级。</span><span class="sxs-lookup"><span data-stu-id="deae8-145">The following group of operators have equal precedence.</span></span> <span data-ttu-id="deae8-146">它们区分大小写和不区分大小写的变量具有相同的优先级。</span><span class="sxs-lookup"><span data-stu-id="deae8-146">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="deae8-147">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="deae8-147">OPERATOR</span></span>          |           <span data-ttu-id="deae8-148">参考</span><span class="sxs-lookup"><span data-stu-id="deae8-148">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="deae8-149">`-split` (二进制) </span><span class="sxs-lookup"><span data-stu-id="deae8-149">`-split` (binary)</span></span>         | <span data-ttu-id="deae8-150">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="deae8-150">[about_Split][]</span></span>                |
| <span data-ttu-id="deae8-151">`-join` (二进制) </span><span class="sxs-lookup"><span data-stu-id="deae8-151">`-join` (binary)</span></span>          | <span data-ttu-id="deae8-152">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="deae8-152">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="deae8-153">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-153">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="deae8-154">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-154">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="deae8-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-155">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="deae8-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-156">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="deae8-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-157">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="deae8-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-158">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="deae8-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-159">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="deae8-160">列表按优先级顺序在此处恢复：</span><span class="sxs-lookup"><span data-stu-id="deae8-160">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="deae8-161">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="deae8-161">OPERATOR</span></span>                 |           <span data-ttu-id="deae8-162">参考</span><span class="sxs-lookup"><span data-stu-id="deae8-162">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="deae8-163">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-163">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="deae8-164">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-164">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="deae8-165">以下各项不是真正的运算符。</span><span class="sxs-lookup"><span data-stu-id="deae8-165">The following items are not true operators.</span></span> <span data-ttu-id="deae8-166">它们是 PowerShell 命令语法的一部分，而不是表达式语法的一部分。</span><span class="sxs-lookup"><span data-stu-id="deae8-166">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="deae8-167">赋值始终是执行的最后一个操作。</span><span class="sxs-lookup"><span data-stu-id="deae8-167">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="deae8-168">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="deae8-168">SYNTAX</span></span>                   |           <span data-ttu-id="deae8-169">参考</span><span class="sxs-lookup"><span data-stu-id="deae8-169">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="deae8-170">`.` (点-源) </span><span class="sxs-lookup"><span data-stu-id="deae8-170">`.` (dot-source)</span></span>                        | <span data-ttu-id="deae8-171">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-171">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-172">`&` (调用) </span><span class="sxs-lookup"><span data-stu-id="deae8-172">`&` (call)</span></span>                              | <span data-ttu-id="deae8-173">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-173">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-174">`? <if-true> : <if-false>` (三元运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-174">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="deae8-175">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-175">[about_Operators][]</span></span>      |
| <span data-ttu-id="deae8-176">`??` (coalese 运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-176">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="deae8-177">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-177">[about_Operators][]</span></span>            |
| <span data-ttu-id="deae8-178"><code>&#124;</code> (管道运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-178"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="deae8-179">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-179">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="deae8-180">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="deae8-180">[about_Redirection][]</span></span>          |
| <span data-ttu-id="deae8-181"><code>&& &#124;&#124;</code> (管道链运算符) </span><span class="sxs-lookup"><span data-stu-id="deae8-181"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="deae8-182">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-182">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="deae8-183">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-183">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="deae8-184">示例</span><span class="sxs-lookup"><span data-stu-id="deae8-184">EXAMPLES</span></span>

<span data-ttu-id="deae8-185">以下两个命令显示算术运算符，以及使用括号强制 PowerShell 首先计算表达式中包含的部分的效果。</span><span class="sxs-lookup"><span data-stu-id="deae8-185">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="deae8-186">下面的示例从本地目录中获取只读文本文件，并将其保存在 `$read_only` 变量中。</span><span class="sxs-lookup"><span data-stu-id="deae8-186">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="deae8-187">它等效于以下示例。</span><span class="sxs-lookup"><span data-stu-id="deae8-187">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="deae8-188">由于管道运算符 (`|`) 的优先级高于赋值运算符 () ，因此在 `=` `Get-ChildItem` 将 cmdlet 获取的文件分配给该变量之前，会将其发送到 `Where-Object` cmdlet 进行筛选 `$read_only` 。</span><span class="sxs-lookup"><span data-stu-id="deae8-188">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="deae8-189">下面的示例演示索引运算符优先于强制转换运算符。</span><span class="sxs-lookup"><span data-stu-id="deae8-189">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="deae8-190">此表达式创建一个包含三个字符串的数组。</span><span class="sxs-lookup"><span data-stu-id="deae8-190">This expression creates an array of three strings.</span></span> <span data-ttu-id="deae8-191">然后，它将索引运算符与值0一起使用，以选择数组中的第一个对象，这是第一个字符串。</span><span class="sxs-lookup"><span data-stu-id="deae8-191">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="deae8-192">最后，它将所选对象强制转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="deae8-192">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="deae8-193">在这种情况下，转换不起作用。</span><span class="sxs-lookup"><span data-stu-id="deae8-193">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="deae8-194">此表达式使用括号强制执行强制转换操作，然后再进行索引选择。</span><span class="sxs-lookup"><span data-stu-id="deae8-194">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="deae8-195">因此，整个数组将转换为 (单个) 字符串。</span><span class="sxs-lookup"><span data-stu-id="deae8-195">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="deae8-196">然后，索引运算符选择字符串数组中的第一项，即第一个字符。</span><span class="sxs-lookup"><span data-stu-id="deae8-196">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="deae8-197">在下面的示例中，由于 `-gt` (大于) 运算符的优先级高于 `-and` (逻辑 AND) 运算符，因此表达式的结果为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="deae8-197">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="deae8-198">它等效于下面的表达式。</span><span class="sxs-lookup"><span data-stu-id="deae8-198">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="deae8-199">如果-和运算符具有较高的优先级，则回答为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="deae8-199">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="deae8-200">但是，此示例演示了管理操作员优先级的重要原则。</span><span class="sxs-lookup"><span data-stu-id="deae8-200">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="deae8-201">如果某个表达式难以解释，则使用括号来强制求值顺序，即使它强制使用默认运算符优先级也是如此。</span><span class="sxs-lookup"><span data-stu-id="deae8-201">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="deae8-202">圆括号使您的意图对阅读和维护您的脚本的人很清楚。</span><span class="sxs-lookup"><span data-stu-id="deae8-202">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="deae8-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="deae8-203">SEE ALSO</span></span>

<span data-ttu-id="deae8-204">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-204">[about_Operators][]</span></span>

<span data-ttu-id="deae8-205">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-205">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="deae8-206">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-206">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="deae8-207">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-207">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="deae8-208">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="deae8-208">[about_Join][]</span></span>

<span data-ttu-id="deae8-209">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="deae8-209">[about_Redirection][]</span></span>

<span data-ttu-id="deae8-210">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="deae8-210">[about_Scopes][]</span></span>

<span data-ttu-id="deae8-211">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="deae8-211">[about_Split][]</span></span>

<span data-ttu-id="deae8-212">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="deae8-212">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
