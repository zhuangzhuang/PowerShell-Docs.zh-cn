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
# <a name="about-switch"></a><span data-ttu-id="9687f-103">关于交换机</span><span class="sxs-lookup"><span data-stu-id="9687f-103">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="9687f-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="9687f-104">Short description</span></span>
<span data-ttu-id="9687f-105">说明如何使用开关来处理多个 `If` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-105">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="9687f-106">长说明</span><span class="sxs-lookup"><span data-stu-id="9687f-106">Long description</span></span>

<span data-ttu-id="9687f-107">若要检查脚本或函数中的条件，请使用 `If` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-107">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="9687f-108">`If`语句可以检查多种类型的条件，包括变量的值和对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9687f-108">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="9687f-109">若要检查多个条件，请使用 `Switch` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-109">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="9687f-110">`Switch`语句等效于一系列 `If` 语句，但它更简单。</span><span class="sxs-lookup"><span data-stu-id="9687f-110">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="9687f-111">`Switch`语句列出每个条件和一个可选操作。</span><span class="sxs-lookup"><span data-stu-id="9687f-111">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="9687f-112">如果条件获得，则执行该操作。</span><span class="sxs-lookup"><span data-stu-id="9687f-112">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="9687f-113">`Switch`语句可以使用 `$_` 和 `$switch` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="9687f-113">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="9687f-114">有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9687f-114">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="9687f-115">基本 `Switch` 语句具有以下格式：</span><span class="sxs-lookup"><span data-stu-id="9687f-115">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="9687f-116">例如，下面的 `Switch` 语句将测试值3与每个条件进行比较。</span><span class="sxs-lookup"><span data-stu-id="9687f-116">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="9687f-117">如果测试值与条件匹配，则执行操作。</span><span class="sxs-lookup"><span data-stu-id="9687f-117">When the test value matches the condition, the action is performed.</span></span>

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

<span data-ttu-id="9687f-118">在这个简单的示例中，将值与列表中的每个条件进行比较，即使存在值3的匹配项。</span><span class="sxs-lookup"><span data-stu-id="9687f-118">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="9687f-119">以下 `Switch` 语句的值为3的两个条件。</span><span class="sxs-lookup"><span data-stu-id="9687f-119">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="9687f-120">它说明默认情况下，测试所有条件。</span><span class="sxs-lookup"><span data-stu-id="9687f-120">It demonstrates that, by default, all conditions are tested.</span></span>

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

<span data-ttu-id="9687f-121">若要指示在 `Switch` 匹配后停止比较，请使用 `Break` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-121">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="9687f-122">`Break`语句终止 `Switch` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-122">The `Break` statement terminates the `Switch` statement.</span></span>

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

<span data-ttu-id="9687f-123">如果测试值是一个集合（如数组），则集合中的每一项都按其出现的顺序进行计算。</span><span class="sxs-lookup"><span data-stu-id="9687f-123">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="9687f-124">下面的示例计算4，then 2。</span><span class="sxs-lookup"><span data-stu-id="9687f-124">The following examples evaluates 4 and then 2.</span></span>

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

<span data-ttu-id="9687f-125">任何 `Break` 语句都适用于集合，而不是每个值，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9687f-125">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="9687f-126">`Switch`语句由 `Break` 值4的条件中的语句终止。</span><span class="sxs-lookup"><span data-stu-id="9687f-126">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

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

### <a name="syntax"></a><span data-ttu-id="9687f-127">语法</span><span class="sxs-lookup"><span data-stu-id="9687f-127">Syntax</span></span>

<span data-ttu-id="9687f-128">完整的 `Switch` 语句语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="9687f-128">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="9687f-129">或</span><span class="sxs-lookup"><span data-stu-id="9687f-129">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="9687f-130">如果未使用任何参数， `Switch` 行为与使用 **确切** 参数相同。</span><span class="sxs-lookup"><span data-stu-id="9687f-130">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="9687f-131">它对值执行不区分大小写的匹配。</span><span class="sxs-lookup"><span data-stu-id="9687f-131">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="9687f-132">如果值是集合，则按其显示顺序对每个元素进行计算。</span><span class="sxs-lookup"><span data-stu-id="9687f-132">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="9687f-133">`Switch`语句必须包含至少一个条件语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-133">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="9687f-134">`Default`当值与任何条件都不匹配时，将触发子句。</span><span class="sxs-lookup"><span data-stu-id="9687f-134">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="9687f-135">它等效于 `Else` 语句中的子句 `If` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-135">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="9687f-136">`Default`每个语句中只允许使用一个子句 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-136">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="9687f-137">`Switch` 具有以下参数：</span><span class="sxs-lookup"><span data-stu-id="9687f-137">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="9687f-138">**通配符** -指示条件为通配符字符串。</span><span class="sxs-lookup"><span data-stu-id="9687f-138">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="9687f-139">如果 match 子句不是字符串，则忽略该参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-139">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="9687f-140">比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9687f-140">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9687f-141">**Exact** -指示 match 子句（如果它是字符串）必须完全匹配。</span><span class="sxs-lookup"><span data-stu-id="9687f-141">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="9687f-142">如果 match 子句不是字符串，则忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-142">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="9687f-143">比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9687f-143">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9687f-144">**CaseSensitive** -执行区分大小写的匹配。</span><span class="sxs-lookup"><span data-stu-id="9687f-144">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="9687f-145">如果 match 子句不是字符串，则忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-145">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="9687f-146">**File**-从文件而不是值语句获取输入。</span><span class="sxs-lookup"><span data-stu-id="9687f-146">**File**- Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="9687f-147">如果包括多个 **文件** 参数，则只使用最后一个。</span><span class="sxs-lookup"><span data-stu-id="9687f-147">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="9687f-148">该文件的每一行都由语句读取和计算 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-148">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="9687f-149">比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9687f-149">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9687f-150">**Regex** -执行与条件的值的正则表达式匹配。</span><span class="sxs-lookup"><span data-stu-id="9687f-150">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="9687f-151">如果 match 子句不是字符串，则忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-151">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="9687f-152">比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9687f-152">The comparison is case-insensitive.</span></span> <span data-ttu-id="9687f-153">`$matches`自动变量可在匹配语句块中使用。</span><span class="sxs-lookup"><span data-stu-id="9687f-153">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="9687f-154">指定冲突的值（如 **Regex** 和 **通配符**）时，最后指定的参数优先，并忽略所有冲突参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-154">When specifying conflicting values, like **Regex** and **Wildcard**, the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="9687f-155">还允许使用多个参数实例。</span><span class="sxs-lookup"><span data-stu-id="9687f-155">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="9687f-156">但是，只有最后使用的参数才有效。</span><span class="sxs-lookup"><span data-stu-id="9687f-156">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="9687f-157">在此示例中，不是字符串或数字数据的对象将传递到 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-157">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="9687f-158">对 `Switch` 对象执行字符串强制，并计算结果。</span><span class="sxs-lookup"><span data-stu-id="9687f-158">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

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

<span data-ttu-id="9687f-159">在此示例中，没有匹配大小写，因此没有任何输出。</span><span class="sxs-lookup"><span data-stu-id="9687f-159">In this example, there is no matching case so there is no output.</span></span>

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

<span data-ttu-id="9687f-160">通过添加 `Default` 子句，可以在没有其他条件成功时执行操作。</span><span class="sxs-lookup"><span data-stu-id="9687f-160">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

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

<span data-ttu-id="9687f-161">若要使词 "十四" 匹配大小写，必须使用 `-Wildcard` 或 `-Regex` 参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-161">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

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

<span data-ttu-id="9687f-162">下面的示例使用 `-Regex` 参数。</span><span class="sxs-lookup"><span data-stu-id="9687f-162">The following example uses the `-Regex` parameter.</span></span>

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

<span data-ttu-id="9687f-163">Switch 语句条件可以是：</span><span class="sxs-lookup"><span data-stu-id="9687f-163">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="9687f-164">其值与输入值进行比较的表达式</span><span class="sxs-lookup"><span data-stu-id="9687f-164">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="9687f-165">满足条件时应返回的脚本块 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-165">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="9687f-166">`$_`自动变量包含传递给 switch 语句的值，可用于在 condition 语句的范围内进行计算和使用。</span><span class="sxs-lookup"><span data-stu-id="9687f-166">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="9687f-167">每个条件的操作与其他条件中的操作无关。</span><span class="sxs-lookup"><span data-stu-id="9687f-167">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="9687f-168">下面的示例演示如何将脚本块用作 `Switch` 语句条件。</span><span class="sxs-lookup"><span data-stu-id="9687f-168">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

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

<span data-ttu-id="9687f-169">如果该值与多个条件匹配，则将执行每个条件的操作。</span><span class="sxs-lookup"><span data-stu-id="9687f-169">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="9687f-170">若要更改此行为，请使用 `Break` 或 `Continue` 关键字。</span><span class="sxs-lookup"><span data-stu-id="9687f-170">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="9687f-171">`Break`关键字将停止处理并退出 `Switch` 语句。</span><span class="sxs-lookup"><span data-stu-id="9687f-171">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="9687f-172">`Continue`关键字将停止处理当前值，但会继续处理所有后续值。</span><span class="sxs-lookup"><span data-stu-id="9687f-172">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="9687f-173">下面的示例处理一个数字数组，如果它们是奇数或偶数，则显示它。</span><span class="sxs-lookup"><span data-stu-id="9687f-173">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="9687f-174">将跳过带有关键字的负数 `Continue` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-174">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="9687f-175">如果遇到非数字，则使用关键字终止执行 `Break` 。</span><span class="sxs-lookup"><span data-stu-id="9687f-175">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9687f-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="9687f-176">See also</span></span>

[<span data-ttu-id="9687f-177">about_Break</span><span class="sxs-lookup"><span data-stu-id="9687f-177">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="9687f-178">about_Continue</span><span class="sxs-lookup"><span data-stu-id="9687f-178">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="9687f-179">about_If</span><span class="sxs-lookup"><span data-stu-id="9687f-179">about_If</span></span>](about_If.md)

[<span data-ttu-id="9687f-180">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="9687f-180">about_Script_Blocks</span></span>](about_Script_Blocks.md)
