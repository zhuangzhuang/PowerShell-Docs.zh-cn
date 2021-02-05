---
title: 流量控制
description: PowerShell 提供了一些方法，用于创建循环、制定决策以及以逻辑方式控制脚本中的代码流。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 74595f8c6a5d4a49b05e72dd6bde1441fd2b464e
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598043"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="bfb10-103">第 6 章 - 流控制</span><span class="sxs-lookup"><span data-stu-id="bfb10-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="bfb10-104">脚本编写</span><span class="sxs-lookup"><span data-stu-id="bfb10-104">Scripting</span></span>

<span data-ttu-id="bfb10-105">当你从编写 PowerShell 单行命令转为编写脚本时，实际复杂程度没有想象的那么高。</span><span class="sxs-lookup"><span data-stu-id="bfb10-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="bfb10-106">脚本只是在 PowerShell 控制台中以交互方式运行的相同或类似命令，只不过它们保存为 `.PS1` 文件。</span><span class="sxs-lookup"><span data-stu-id="bfb10-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="bfb10-107">可以使用一些脚本构造，如 `foreach` 循环，而不是 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb10-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="bfb10-108">对于初学者来说，这种差异可能会令人困惑，特别是当你认为 `foreach` 既是脚本构造，又是 `ForEach-Object` cmdlet 的别名时。</span><span class="sxs-lookup"><span data-stu-id="bfb10-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="bfb10-109">循环</span><span class="sxs-lookup"><span data-stu-id="bfb10-109">Looping</span></span>

<span data-ttu-id="bfb10-110">PowerShell 的一大优势是，确定了如何为某个项执行某些操作后，就可以很容易地为数百个项执行相同的任务。</span><span class="sxs-lookup"><span data-stu-id="bfb10-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="bfb10-111">只需使用 PowerShell 中多种不同类型的循环之一循环访问这些项即可。</span><span class="sxs-lookup"><span data-stu-id="bfb10-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="bfb10-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="bfb10-112">ForEach-Object</span></span>

<span data-ttu-id="bfb10-113">`ForEach-Object` 是用于循环访问管道中的项的 cmdlet，例如使用 PowerShell 单行命令。</span><span class="sxs-lookup"><span data-stu-id="bfb10-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="bfb10-114">`ForEach-Object` 通过管道流式处理对象。</span><span class="sxs-lookup"><span data-stu-id="bfb10-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="bfb10-115">虽然 `Get-Command` 的 Module 参数接受作为字符串的多个值，但仅通过管道输入按属性名称或通过参数输入接受这些值。</span><span class="sxs-lookup"><span data-stu-id="bfb10-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="bfb10-116">在下面的情形中，如果我想通过管道将两个字符串按值传递到 `Get-Command`，以便与 Module 参数一起使用，则需要使用 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb10-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="bfb10-117">在前面的示例中，`$_` 为当前对象。</span><span class="sxs-lookup"><span data-stu-id="bfb10-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="bfb10-118">从 PowerShell 版本 3.0 开始，可以使用 `$PSItem` 而不是 `$_`。</span><span class="sxs-lookup"><span data-stu-id="bfb10-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="bfb10-119">但我发现，大多数经验丰富的 PowerShell 用户仍更喜欢使用 `$_`，因为它向后兼容，需要输入的内容更少。</span><span class="sxs-lookup"><span data-stu-id="bfb10-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="bfb10-120">使用 `foreach` 关键字时，必须先将所有项存储在内存中，然后才能循环访问这些项，如果不知道要处理的项数，此操作可能会很困难。</span><span class="sxs-lookup"><span data-stu-id="bfb10-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="bfb10-121">很多时候都需要 `foreach` 或 `ForEach-Object` 等循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="bfb10-122">否则，你将收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="bfb10-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="bfb10-123">在其他情况下，可以在完全消除循环的情况下得到相同的结果。</span><span class="sxs-lookup"><span data-stu-id="bfb10-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="bfb10-124">请参阅 cmdlet 帮助以了解你的选项。</span><span class="sxs-lookup"><span data-stu-id="bfb10-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="bfb10-125">如前面的示例所示，`Get-ADComputer` 的 Identity 参数仅接受通过参数输入提供的单个值，但通过管道输入提供时，它允许多个项。</span><span class="sxs-lookup"><span data-stu-id="bfb10-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="bfb10-126">For</span><span class="sxs-lookup"><span data-stu-id="bfb10-126">For</span></span>

<span data-ttu-id="bfb10-127">当指定的条件为 true 时，`for` 循环会进行循环访问。</span><span class="sxs-lookup"><span data-stu-id="bfb10-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="bfb10-128">我并未经常使用 `for` 循环，但它确实有它的用处。</span><span class="sxs-lookup"><span data-stu-id="bfb10-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="bfb10-129">在前面的示例中，循环从数字 1 开始循环访问 4 次，并在计数器变量 `$i` 小于 5 时继续循环访问。</span><span class="sxs-lookup"><span data-stu-id="bfb10-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="bfb10-130">休眠时间共计 10 秒。</span><span class="sxs-lookup"><span data-stu-id="bfb10-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="bfb10-131">要求事项</span><span class="sxs-lookup"><span data-stu-id="bfb10-131">Do</span></span>

<span data-ttu-id="bfb10-132">PowerShell 中有两个不同的 `do` 循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="bfb10-133">指定的条件为 false 时，`Do Until` 运行。</span><span class="sxs-lookup"><span data-stu-id="bfb10-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="bfb10-134">前面的示例是一个数字游戏，在你猜测的值等于 `Get-Random` cmdlet 生成的相同数字时游戏结束。</span><span class="sxs-lookup"><span data-stu-id="bfb10-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="bfb10-135">`Do While` 正好相反。</span><span class="sxs-lookup"><span data-stu-id="bfb10-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="bfb10-136">只要指定条件的计算结果为 true，它就会运行。</span><span class="sxs-lookup"><span data-stu-id="bfb10-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="bfb10-137">通过将测试条件反转为不等于，使用 `Do While` 循环可实现相同的结果。</span><span class="sxs-lookup"><span data-stu-id="bfb10-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="bfb10-138">`Do` 循环始终运行至少一次，因为将在循环结束时计算条件的结果。</span><span class="sxs-lookup"><span data-stu-id="bfb10-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="bfb10-139">While</span><span class="sxs-lookup"><span data-stu-id="bfb10-139">While</span></span>

<span data-ttu-id="bfb10-140">与 `Do While` 循环类似，只要指定的条件为 true，`While` 循环就会运行。</span><span class="sxs-lookup"><span data-stu-id="bfb10-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="bfb10-141">但差别在于，`While` 循环会在运行任何代码之前，计算循环顶部条件的结果。</span><span class="sxs-lookup"><span data-stu-id="bfb10-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="bfb10-142">如果条件计算结果为 false，它就不会运行。</span><span class="sxs-lookup"><span data-stu-id="bfb10-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="bfb10-143">前面的示例计算了美国的感恩节是哪一天。</span><span class="sxs-lookup"><span data-stu-id="bfb10-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="bfb10-144">它始终是 11 月的第 4 个星期四。</span><span class="sxs-lookup"><span data-stu-id="bfb10-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="bfb10-145">因此循环从 11 月 22 日开始，并在当天不是星期四时增加一天。</span><span class="sxs-lookup"><span data-stu-id="bfb10-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="bfb10-146">如果 22 日是星期四，则循环根本不会运行。</span><span class="sxs-lookup"><span data-stu-id="bfb10-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="bfb10-147">Break、Continue 和 Return</span><span class="sxs-lookup"><span data-stu-id="bfb10-147">Break, Continue, and Return</span></span>

<span data-ttu-id="bfb10-148">`Break` 旨在中断循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="bfb10-149">它通常与 `switch` 语句一起使用。</span><span class="sxs-lookup"><span data-stu-id="bfb10-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="bfb10-150">上一示例中所示的 `break` 语句导致循环在第一次迭代时退出。</span><span class="sxs-lookup"><span data-stu-id="bfb10-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="bfb10-151">Continue 旨在跳到循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="bfb10-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="bfb10-152">前面的示例将输出数字 1、2、4 和 5。</span><span class="sxs-lookup"><span data-stu-id="bfb10-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="bfb10-153">它跳过数字 3，并继续执行循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="bfb10-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="bfb10-154">与 `break` 类似，`continue` 将中断除当前迭代以外的循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="bfb10-155">Execution 将继续进行下一次迭代，而不是中断循环并停止。</span><span class="sxs-lookup"><span data-stu-id="bfb10-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="bfb10-156">Return 旨在退出现有作用域。</span><span class="sxs-lookup"><span data-stu-id="bfb10-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="bfb10-157">请注意，在上面的示例中，return 输出第一个结果，然后退出循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="bfb10-158">可以在我的一篇博客文章中找到有关结果语句的更详尽说明：[“PowerShell return 关键字”][]。</span><span class="sxs-lookup"><span data-stu-id="bfb10-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="bfb10-159">总结</span><span class="sxs-lookup"><span data-stu-id="bfb10-159">Summary</span></span>

<span data-ttu-id="bfb10-160">本章介绍了 PowerShell 中存在的不同类型的循环。</span><span class="sxs-lookup"><span data-stu-id="bfb10-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="bfb10-161">审阅</span><span class="sxs-lookup"><span data-stu-id="bfb10-161">Review</span></span>

1. <span data-ttu-id="bfb10-162">`ForEach-Object` cmdlet 和 foreach 脚本构造之间有何区别？</span><span class="sxs-lookup"><span data-stu-id="bfb10-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="bfb10-163">使用 While 循环而不使用 Do While 或 Do Until 循环的主要优点是什么。</span><span class="sxs-lookup"><span data-stu-id="bfb10-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="bfb10-164">Break 和 continue 语句有何不同？</span><span class="sxs-lookup"><span data-stu-id="bfb10-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="bfb10-165">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="bfb10-165">Recommended Reading</span></span>

- <span data-ttu-id="bfb10-166">[ForEach-Object][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="bfb10-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-167">[about_ForEach][]</span></span>
- <span data-ttu-id="bfb10-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-168">[about_For][]</span></span>
- <span data-ttu-id="bfb10-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-169">[about_Do][]</span></span>
- <span data-ttu-id="bfb10-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-170">[about_While][]</span></span>
- <span data-ttu-id="bfb10-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-171">[about_Break][]</span></span>
- <span data-ttu-id="bfb10-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-172">[about_Continue][]</span></span>
- <span data-ttu-id="bfb10-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="bfb10-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[“PowerShell return 关键字”]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
