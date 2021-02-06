---
description: 描述可用于根据一个或多个条件测试的结果运行语句列表的语言命令。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 04c610af36e17c02d2440ab79b7de5330e5063ab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597259"
---
# <a name="about-if"></a><span data-ttu-id="8cf65-103">关于 If</span><span class="sxs-lookup"><span data-stu-id="8cf65-103">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="8cf65-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="8cf65-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8cf65-105">描述可用于根据一个或多个条件测试的结果运行语句列表的语言命令。</span><span class="sxs-lookup"><span data-stu-id="8cf65-105">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="8cf65-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="8cf65-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="8cf65-107">`If`如果指定的条件测试的计算结果为 true，则可以使用语句来运行代码块。</span><span class="sxs-lookup"><span data-stu-id="8cf65-107">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="8cf65-108">如果所有之前的测试的计算结果都为 false，则还可以指定要运行的一个或多个附加条件测试。</span><span class="sxs-lookup"><span data-stu-id="8cf65-108">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="8cf65-109">最后，你可以指定一个其他代码块，如果没有其他任何之前的条件测试计算为 true，则会运行该代码块。</span><span class="sxs-lookup"><span data-stu-id="8cf65-109">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="8cf65-110">语法</span><span class="sxs-lookup"><span data-stu-id="8cf65-110">Syntax</span></span>

<span data-ttu-id="8cf65-111">下面的示例显示了 `If` 语句语法：</span><span class="sxs-lookup"><span data-stu-id="8cf65-111">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="8cf65-112">运行 `If` 语句时，PowerShell 会将 `<test1>` 条件表达式计算为 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="8cf65-112">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="8cf65-113">如果 `<test1>` 为 true，则 `<statement list 1>` 运行，并且 PowerShell 将退出 `If` 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-113">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="8cf65-114">如果 `<test1>` 为 false，则 PowerShell 将计算由条件语句指定的条件 `<test2>` 。</span><span class="sxs-lookup"><span data-stu-id="8cf65-114">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="8cf65-115">如果 `<test2>` 为 true，则 `<statement list 2>` 运行，并且 PowerShell 将退出 `If` 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-115">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="8cf65-116">如果 `<test1>` 和 `<test2>` 的计算结果都为 false，则 `<statement list 3`> 代码块运行，并且 PowerShell 将退出 If 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-116">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="8cf65-117">可以使用多个 Elseif 语句来链接一系列条件测试。</span><span class="sxs-lookup"><span data-stu-id="8cf65-117">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="8cf65-118">因此，仅当前面的所有测试都为 false 时，才会运行每个测试。</span><span class="sxs-lookup"><span data-stu-id="8cf65-118">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="8cf65-119">如果需要创建 `If` 包含多个 Elseif 语句的语句，请考虑改为使用 Switch 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-119">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="8cf65-120">示例:</span><span class="sxs-lookup"><span data-stu-id="8cf65-120">Examples:</span></span>

<span data-ttu-id="8cf65-121">最简单的 `If` 语句包含一个命令，不包含任何 Elseif 语句或任何 Else 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-121">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="8cf65-122">下面的示例显示了语句的最简单形式 `If` ：</span><span class="sxs-lookup"><span data-stu-id="8cf65-122">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="8cf65-123">在此示例中，如果 $a 变量大于2，则条件的计算结果为 true，并且语句列表将运行。</span><span class="sxs-lookup"><span data-stu-id="8cf65-123">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="8cf65-124">但是，如果 $a 小于或等于2或者不是现有的变量，则该语句不 `If` 显示消息。</span><span class="sxs-lookup"><span data-stu-id="8cf65-124">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="8cf65-125">通过添加 Else 语句，当 $a 小于或等于2时，将显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="8cf65-125">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="8cf65-126">如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="8cf65-126">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="8cf65-127">若要进一步优化此示例，可以使用 Elseif 语句在 $a 的值等于2时显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="8cf65-127">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="8cf65-128">如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="8cf65-128">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a><span data-ttu-id="8cf65-129">使用三元运算符语法</span><span class="sxs-lookup"><span data-stu-id="8cf65-129">Using the ternary operator syntax</span></span>

<span data-ttu-id="8cf65-130">PowerShell 7.0 使用三元运算符引入了新的语法。</span><span class="sxs-lookup"><span data-stu-id="8cf65-130">PowerShell 7.0 introduced a new syntax using the ternary operator.</span></span> <span data-ttu-id="8cf65-131">它遵循 c # 三元运算符语法：</span><span class="sxs-lookup"><span data-stu-id="8cf65-131">It follows the C# ternary operator syntax:</span></span>

```Syntax
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="8cf65-132">三元运算符的行为类似于简化 `if-else` 语句。</span><span class="sxs-lookup"><span data-stu-id="8cf65-132">The ternary operator behaves like the simplified `if-else` statement.</span></span> <span data-ttu-id="8cf65-133">`<condition>`计算表达式，并将结果转换为布尔值，以确定下一次应计算哪个分支：</span><span class="sxs-lookup"><span data-stu-id="8cf65-133">The `<condition>` expression is evaluated and the result is converted to a boolean to determine which branch should be evaluated next:</span></span>

- <span data-ttu-id="8cf65-134">如果 `<condition>` 表达式为 true，则执行 `<if-true>` 表达式</span><span class="sxs-lookup"><span data-stu-id="8cf65-134">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="8cf65-135">如果 `<condition>` 表达式为 false，则执行 `<if-false>` 表达式</span><span class="sxs-lookup"><span data-stu-id="8cf65-135">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="8cf65-136">例如：</span><span class="sxs-lookup"><span data-stu-id="8cf65-136">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="8cf65-137">在此示例中，的值在 `$message` 返回时为 "Path exists" `Test-Path` `$true` 。</span><span class="sxs-lookup"><span data-stu-id="8cf65-137">In this example, the value of `$message` is "Path exists" when `Test-Path` returns `$true`.</span></span> <span data-ttu-id="8cf65-138">当 `Test-Path` 返回时 `$false` ，的值 `$message` 为 "找不到路径"。</span><span class="sxs-lookup"><span data-stu-id="8cf65-138">When `Test-Path` returns `$false`, the value of `$message` is "Path not found".</span></span>

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

<span data-ttu-id="8cf65-139">在此示例中，如果服务正在运行，它将停止，如果其状态为 "未在 **运行**"，则启动该服务。</span><span class="sxs-lookup"><span data-stu-id="8cf65-139">In this example, if the service is running, it is stopped, and if its status is not **Running**, it is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cf65-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cf65-140">SEE ALSO</span></span>

[<span data-ttu-id="8cf65-141">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="8cf65-141">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="8cf65-142">about_Switch</span><span class="sxs-lookup"><span data-stu-id="8cf65-142">about_Switch</span></span>](about_Switch.md)

