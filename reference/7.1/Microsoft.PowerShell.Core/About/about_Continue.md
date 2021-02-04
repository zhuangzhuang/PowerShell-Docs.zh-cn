---
description: 描述语句如何 `continue` 立即将程序流返回到程序循环、 `switch` 语句或语句的顶部 `trap` 。
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 2b299726b3fe75e5d13e91bbde7564705d3e2112
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614109"
---
# <a name="about-continue"></a><span data-ttu-id="fa361-104">关于继续</span><span class="sxs-lookup"><span data-stu-id="fa361-104">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="fa361-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="fa361-105">Short description</span></span>

<span data-ttu-id="fa361-106">描述语句如何 `continue` 立即将程序流返回到程序循环、 `switch` 语句或语句的顶部 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-106">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa361-107">长说明</span><span class="sxs-lookup"><span data-stu-id="fa361-107">Long description</span></span>

<span data-ttu-id="fa361-108">`continue`语句提供一种退出当前控制块但继续执行的方法，而不是完全退出。</span><span class="sxs-lookup"><span data-stu-id="fa361-108">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="fa361-109">语句支持标签。</span><span class="sxs-lookup"><span data-stu-id="fa361-109">The statement supports labels.</span></span>
<span data-ttu-id="fa361-110">标签是为脚本中的语句分配的名称。</span><span class="sxs-lookup"><span data-stu-id="fa361-110">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="fa361-111">在循环中使用 continue</span><span class="sxs-lookup"><span data-stu-id="fa361-111">Using continue in loops</span></span>

<span data-ttu-id="fa361-112">未标记的 `continue` 语句会立即将程序流返回到由 `for` 、 `foreach` 、 `do` 或语句控制的最内层循环的顶部 `while` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-112">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="fa361-113">循环的当前迭代已终止，循环将继续进行下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="fa361-113">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="fa361-114">在以下示例中， `while` 如果变量等于5，则程序流返回到循环的顶部 `$ctr` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-114">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="fa361-115">因此，会显示1到10之间的所有数字，但5除外：</span><span class="sxs-lookup"><span data-stu-id="fa361-115">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="fa361-116">使用循环时 `for` ，将继续执行 `<Repeat>` 语句，然后执行 `<Condition>` 测试。</span><span class="sxs-lookup"><span data-stu-id="fa361-116">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="fa361-117">在下面的示例中，不会发生无限循环，因为减量 `$i` 发生在关键字之后 `continue` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-117">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="fa361-118">在循环中使用标签为 continue</span><span class="sxs-lookup"><span data-stu-id="fa361-118">Using a labeled continue in a loop</span></span>

<span data-ttu-id="fa361-119">标记 `continue` 语句终止迭代的执行，并将控制权移交给目标封闭迭代或 `switch` 语句标签。</span><span class="sxs-lookup"><span data-stu-id="fa361-119">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="fa361-120">在下面的示例中， `for` 当为 True 时，最内层终止， `$condition` 迭代将在处继续执行第二个 `for` 循环 `labelB` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-120">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="fa361-121">在 switch 语句中使用 continue</span><span class="sxs-lookup"><span data-stu-id="fa361-121">Using continue in a switch statement</span></span>

<span data-ttu-id="fa361-122">中的未标记 `continue` 语句 `switch` 终止当前迭代的执行 `switch` ，并将控制转移到的顶部 `switch` 以获取下一个输入项。</span><span class="sxs-lookup"><span data-stu-id="fa361-122">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="fa361-123">当存在单个输入项时，将 `continue` 退出整个 `switch` 语句。</span><span class="sxs-lookup"><span data-stu-id="fa361-123">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="fa361-124">当 `switch` 输入为集合时，会 `switch` 测试集合中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="fa361-124">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="fa361-125">`continue`退出当前迭代，并 `switch` 继续下一个元素。</span><span class="sxs-lookup"><span data-stu-id="fa361-125">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="fa361-126">在 trap 语句中使用 continue</span><span class="sxs-lookup"><span data-stu-id="fa361-126">Using continue in a trap statement</span></span>

<span data-ttu-id="fa361-127">如果在正文中执行的最后一条语句 `trap` 是语句 `continue` ，则捕获错误将以无提示方式忽略，并继续执行导致发生的语句 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="fa361-127">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="fa361-128">请勿在循环、开关或陷阱外使用 continue</span><span class="sxs-lookup"><span data-stu-id="fa361-128">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="fa361-129">如果在 `continue` 直接支持 (循环、) 的构造之外使用，则 `switch` `trap` PowerShell 将查找封闭构造 _的调用堆栈_ 。</span><span class="sxs-lookup"><span data-stu-id="fa361-129">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="fa361-130">如果找不到封闭构造，则当前的运行空间将不知不觉地终止。</span><span class="sxs-lookup"><span data-stu-id="fa361-130">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="fa361-131">这意味着，如果函数和脚本无意中使用了 `continue` 支持它的封闭构造之外的，则可能会无意中终止其 _调用方_。</span><span class="sxs-lookup"><span data-stu-id="fa361-131">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="fa361-132">在 `continue` 管道内使用（如 `ForEach-Object` 脚本块），不仅会退出管道，还可能终止整个运行空间。</span><span class="sxs-lookup"><span data-stu-id="fa361-132">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa361-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa361-133">See also</span></span>

[<span data-ttu-id="fa361-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="fa361-134">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="fa361-135">about_For</span><span class="sxs-lookup"><span data-stu-id="fa361-135">about_For</span></span>](about_For.md)

[<span data-ttu-id="fa361-136">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="fa361-136">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="fa361-137">about_Throw</span><span class="sxs-lookup"><span data-stu-id="fa361-137">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="fa361-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="fa361-138">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="fa361-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="fa361-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
