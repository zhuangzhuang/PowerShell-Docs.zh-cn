---
title: 关于 switch 语句的各项须知内容
description: PowerShell 中的 switch 语句提供了其他语言没有的功能。
ms.date: 03/01/2021
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: f6baa624285557452a2b95150b2c4de1ab274f27
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686009"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="05bea-103">关于 switch 语句的各项须知内容</span><span class="sxs-lookup"><span data-stu-id="05bea-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="05bea-104">与许多其他语言一样，PowerShell 具有用于控制脚本内执行流的命令。</span><span class="sxs-lookup"><span data-stu-id="05bea-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="05bea-105">其中一个语句是 [switch][] 语句，在 PowerShell 中，它提供了其他语言没有的功能。</span><span class="sxs-lookup"><span data-stu-id="05bea-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="05bea-106">今天，我们将深入探讨如何使用 PowerShell `switch`。</span><span class="sxs-lookup"><span data-stu-id="05bea-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="05bea-107">本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。</span><span class="sxs-lookup"><span data-stu-id="05bea-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="05bea-108">PowerShell 团队感谢 Kevin 与我们分享这篇文章。</span><span class="sxs-lookup"><span data-stu-id="05bea-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="05bea-109">请前往 [PowerShellExplained.com][] 访问他的博客。</span><span class="sxs-lookup"><span data-stu-id="05bea-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="05bea-110">`if` 语句</span><span class="sxs-lookup"><span data-stu-id="05bea-110">The `if` statement</span></span>

<span data-ttu-id="05bea-111">你最先学习的语句之一是 `if` 语句。</span><span class="sxs-lookup"><span data-stu-id="05bea-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="05bea-112">如果语句为 `$true`，则允许执行脚本块。</span><span class="sxs-lookup"><span data-stu-id="05bea-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="05bea-113">可以通过使用 `elseif` 和 `else` 语句来获得更复杂的逻辑。</span><span class="sxs-lookup"><span data-stu-id="05bea-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="05bea-114">下面是一个示例：我有一个星期的数字值，想要获取字符串形式的名称。</span><span class="sxs-lookup"><span data-stu-id="05bea-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="05bea-115">事实证明，这是一种常见模式，可以通过多种方法来实现。</span><span class="sxs-lookup"><span data-stu-id="05bea-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="05bea-116">其中一种方法是使用 `switch`。</span><span class="sxs-lookup"><span data-stu-id="05bea-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="05bea-117">Switch 语句</span><span class="sxs-lookup"><span data-stu-id="05bea-117">Switch statement</span></span>

<span data-ttu-id="05bea-118">`switch` 语句允许你提供一个变量和一列可能值。</span><span class="sxs-lookup"><span data-stu-id="05bea-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="05bea-119">如果值与变量匹配，则将执行其脚本块。</span><span class="sxs-lookup"><span data-stu-id="05bea-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="05bea-120">在本例中，`$day` 的值与其中一个数值匹配，然后正确的名称即会分配给 `$result`。</span><span class="sxs-lookup"><span data-stu-id="05bea-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="05bea-121">我们在本例中只进行了变量赋值，但任何 PowerShell 都可以在这些脚本块中执行。</span><span class="sxs-lookup"><span data-stu-id="05bea-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="05bea-122">给变量赋值</span><span class="sxs-lookup"><span data-stu-id="05bea-122">Assign to a variable</span></span>

<span data-ttu-id="05bea-123">我们可以通过另一种方法编写上一个示例。</span><span class="sxs-lookup"><span data-stu-id="05bea-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="05bea-124">我们将该值置于 PowerShell 管道上，并将其赋给 `$result`。</span><span class="sxs-lookup"><span data-stu-id="05bea-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="05bea-125">可以使用 `if` 和 `foreach` 语句执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="05bea-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="05bea-126">默认</span><span class="sxs-lookup"><span data-stu-id="05bea-126">Default</span></span>

<span data-ttu-id="05bea-127">我们可以使用 `default` 关键字来确定没有匹配项时应发生的情况。</span><span class="sxs-lookup"><span data-stu-id="05bea-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="05bea-128">默认情况下，返回值 `Unknown`。</span><span class="sxs-lookup"><span data-stu-id="05bea-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="05bea-129">字符串</span><span class="sxs-lookup"><span data-stu-id="05bea-129">Strings</span></span>

<span data-ttu-id="05bea-130">我在上述几个示例中匹配的都是数字，但你也可以匹配字符串。</span><span class="sxs-lookup"><span data-stu-id="05bea-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="05bea-131">我决定在这里不把 `Component`、`Role` 和 `Location` 匹配项括在引号中，以突出它们是可选的。</span><span class="sxs-lookup"><span data-stu-id="05bea-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="05bea-132">在大多数情况下，`switch` 会将它们视为字符串。</span><span class="sxs-lookup"><span data-stu-id="05bea-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="05bea-133">数组</span><span class="sxs-lookup"><span data-stu-id="05bea-133">Arrays</span></span>

<span data-ttu-id="05bea-134">PowerShell `switch` 的一项优异功能体现在处理数组的方式上。</span><span class="sxs-lookup"><span data-stu-id="05bea-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="05bea-135">如果向数组提供一个 `switch`，它会处理集合中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="05bea-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="05bea-136">如果数组中有重复项，则相应的部分会对它们进行多次匹配。</span><span class="sxs-lookup"><span data-stu-id="05bea-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="05bea-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="05bea-137">PSItem</span></span>

<span data-ttu-id="05bea-138">可以使用 `$PSItem` 或 `$_` 来引用已处理的当前项。</span><span class="sxs-lookup"><span data-stu-id="05bea-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="05bea-139">当我们执行简单匹配时，`$PSItem` 是我们要匹配的值。</span><span class="sxs-lookup"><span data-stu-id="05bea-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="05bea-140">在下一部分中使用这个变量时，我将执行一些高级匹配。</span><span class="sxs-lookup"><span data-stu-id="05bea-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="05bea-141">参数</span><span class="sxs-lookup"><span data-stu-id="05bea-141">Parameters</span></span>

<span data-ttu-id="05bea-142">PowerShell `switch` 的一项独特特性是它有许多可更改其执行方式的开关参数。</span><span class="sxs-lookup"><span data-stu-id="05bea-142">A unique feature of the PowerShell `switch` is that it has a number of switch parameters that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="05bea-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="05bea-143">-CaseSensitive</span></span>

<span data-ttu-id="05bea-144">默认情况下，匹配项不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="05bea-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="05bea-145">如果需要区分大小写，可以使用 `-CaseSensitive`。</span><span class="sxs-lookup"><span data-stu-id="05bea-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="05bea-146">这可以与其他开关参数结合使用。</span><span class="sxs-lookup"><span data-stu-id="05bea-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="05bea-147">-Wildcard</span><span class="sxs-lookup"><span data-stu-id="05bea-147">-Wildcard</span></span>

<span data-ttu-id="05bea-148">可以使用 `-wildcard` 开关启用通配符支持。</span><span class="sxs-lookup"><span data-stu-id="05bea-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="05bea-149">这会使用与 `-like` 运算符相同的通配符逻辑来执行每次匹配。</span><span class="sxs-lookup"><span data-stu-id="05bea-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="05bea-150">在这里我们正处理一条消息，然后根据内容将其输出到不同的流中。</span><span class="sxs-lookup"><span data-stu-id="05bea-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="05bea-151">-Regex</span><span class="sxs-lookup"><span data-stu-id="05bea-151">-Regex</span></span>

<span data-ttu-id="05bea-152">switch 语句支持正则表达式匹配，就像支持通配符一样。</span><span class="sxs-lookup"><span data-stu-id="05bea-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="05bea-153">在我撰写的另一篇文章中有更多使用正则表达式的示例：[使用正则表达式的多种方式][]。</span><span class="sxs-lookup"><span data-stu-id="05bea-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="05bea-154">-File</span><span class="sxs-lookup"><span data-stu-id="05bea-154">-File</span></span>

<span data-ttu-id="05bea-155">switch 语句的一个鲜为人知的功能是，它可以使用 `-File` 参数处理文件。</span><span class="sxs-lookup"><span data-stu-id="05bea-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="05bea-156">将 `-file` 与文件路径结合使用，而不是向其提供变量表达式。</span><span class="sxs-lookup"><span data-stu-id="05bea-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="05bea-157">它的工作方式就像处理数组一样。</span><span class="sxs-lookup"><span data-stu-id="05bea-157">It works just like processing an array.</span></span> <span data-ttu-id="05bea-158">在本例中，我将它与通配符匹配结合使用，并使用了 `$PSItem`。</span><span class="sxs-lookup"><span data-stu-id="05bea-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="05bea-159">这会处理日志文件，并根据正则表达式匹配情况将其转换为警告消息和错误消息。</span><span class="sxs-lookup"><span data-stu-id="05bea-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="05bea-160">高级详细信息</span><span class="sxs-lookup"><span data-stu-id="05bea-160">Advanced details</span></span>

<span data-ttu-id="05bea-161">现在，你已经了解了所有这些记录在案的功能，我们可以在更高级处理的上下文中使用它们。</span><span class="sxs-lookup"><span data-stu-id="05bea-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="05bea-162">表达式</span><span class="sxs-lookup"><span data-stu-id="05bea-162">Expressions</span></span>

<span data-ttu-id="05bea-163">`switch` 可以在表达式上，而不是变量上。</span><span class="sxs-lookup"><span data-stu-id="05bea-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="05bea-164">表达式的计算结果均为用于匹配的值。</span><span class="sxs-lookup"><span data-stu-id="05bea-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="05bea-165">多个匹配</span><span class="sxs-lookup"><span data-stu-id="05bea-165">Multiple matches</span></span>

<span data-ttu-id="05bea-166">你可能已经了解了这一点，但 `switch` 可以匹配多个条件。</span><span class="sxs-lookup"><span data-stu-id="05bea-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="05bea-167">当使用 `-wildcard` 或 `-regex` 匹配时，尤其如此。</span><span class="sxs-lookup"><span data-stu-id="05bea-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="05bea-168">可以多次添加同一条件，且所有条件都会被触发。</span><span class="sxs-lookup"><span data-stu-id="05bea-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="05bea-169">这三个语句都会触发。</span><span class="sxs-lookup"><span data-stu-id="05bea-169">All three of these statements are fired.</span></span> <span data-ttu-id="05bea-170">这表明每个条件都处于选中状态（按顺序）。</span><span class="sxs-lookup"><span data-stu-id="05bea-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="05bea-171">这适用于处理每个项检查每个条件的数组。</span><span class="sxs-lookup"><span data-stu-id="05bea-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="05bea-172">继续</span><span class="sxs-lookup"><span data-stu-id="05bea-172">Continue</span></span>

<span data-ttu-id="05bea-173">通常，我会在这里介绍 `break` 语句，但最好先了解如何使用 `continue`。</span><span class="sxs-lookup"><span data-stu-id="05bea-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="05bea-174">正如 `foreach` 循环一样，`continue` 会继续进行到集合中的下一项，如果没有其他项，则会退出 `switch`。</span><span class="sxs-lookup"><span data-stu-id="05bea-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="05bea-175">我们可以使用 continue 语句重写上一个示例，以便仅执行一个语句。</span><span class="sxs-lookup"><span data-stu-id="05bea-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="05bea-176">匹配第一个项，然后 switch 继续处理下一个值，而不是匹配所有三个项。</span><span class="sxs-lookup"><span data-stu-id="05bea-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="05bea-177">由于没有要处理的值了，因此 switch 将退出。</span><span class="sxs-lookup"><span data-stu-id="05bea-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="05bea-178">下一个示例演示通配符如何与多个项匹配。</span><span class="sxs-lookup"><span data-stu-id="05bea-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="05bea-179">因为输入文件中的一行可能同时包含单词 `Error` 和 `Warning`，所以我们只希望执行第一个，然后继续处理文件。</span><span class="sxs-lookup"><span data-stu-id="05bea-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="05bea-180">中断</span><span class="sxs-lookup"><span data-stu-id="05bea-180">Break</span></span>

<span data-ttu-id="05bea-181">`break` 语句可退出 switch。</span><span class="sxs-lookup"><span data-stu-id="05bea-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="05bea-182">这与 `continue` 对单个值的行为表现相同。</span><span class="sxs-lookup"><span data-stu-id="05bea-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="05bea-183">差异会在处理数组时显示出来。</span><span class="sxs-lookup"><span data-stu-id="05bea-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="05bea-184">`break` 会停止 switch 中的所有处理，而 `continue` 会继续进行到下一项。</span><span class="sxs-lookup"><span data-stu-id="05bea-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="05bea-185">在这种情况下，如果点击以 `Error` 开头的任何行，则会出现错误，并且 switch 将停止。</span><span class="sxs-lookup"><span data-stu-id="05bea-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="05bea-186">这就是 `break` 语句的作用。</span><span class="sxs-lookup"><span data-stu-id="05bea-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="05bea-187">如果在字符串内（而不只是在开头）找到 `Error`，则将其编写为警告。</span><span class="sxs-lookup"><span data-stu-id="05bea-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="05bea-188">对于 `Warning` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="05bea-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="05bea-189">一行中可能同时包含单词 `Error` 和 `Warning`，但我们只需处理一个。</span><span class="sxs-lookup"><span data-stu-id="05bea-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="05bea-190">这就是 `continue` 语句的作用。</span><span class="sxs-lookup"><span data-stu-id="05bea-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="05bea-191">中断标签</span><span class="sxs-lookup"><span data-stu-id="05bea-191">Break labels</span></span>

<span data-ttu-id="05bea-192">`switch` 语句支持 `break/continue` 标签，就像 `foreach` 一样。</span><span class="sxs-lookup"><span data-stu-id="05bea-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="05bea-193">我个人不喜欢使用中断标签，之所以提及的原因是，如果你之前从未见过它们，可能会感到困惑。</span><span class="sxs-lookup"><span data-stu-id="05bea-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="05bea-194">如果有多个嵌套的 `switch` 或 `foreach` 语句，则可能需要中断的不只是最内层的项。</span><span class="sxs-lookup"><span data-stu-id="05bea-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="05bea-195">可以在 `switch` 上放置一个标签，作为 `break` 的目标。</span><span class="sxs-lookup"><span data-stu-id="05bea-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="05bea-196">枚举</span><span class="sxs-lookup"><span data-stu-id="05bea-196">Enum</span></span>

<span data-ttu-id="05bea-197">PowerShell 5.0 为我们提供了可以在 switch 中使用的枚举。</span><span class="sxs-lookup"><span data-stu-id="05bea-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="05bea-198">如果要将所有内容保持为强类型枚举，则可以将其放在圆括号中。</span><span class="sxs-lookup"><span data-stu-id="05bea-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="05bea-199">此处需要圆括号，以便 switch 不会将值 `[Context]::Location` 视为文本字符串。</span><span class="sxs-lookup"><span data-stu-id="05bea-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="05bea-200">脚本块</span><span class="sxs-lookup"><span data-stu-id="05bea-200">ScriptBlock</span></span>

<span data-ttu-id="05bea-201">如果需要，我们可以使用脚本块来执行匹配的计算。</span><span class="sxs-lookup"><span data-stu-id="05bea-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="05bea-202">这会增加复杂性，并且会使 `switch` 很难读。</span><span class="sxs-lookup"><span data-stu-id="05bea-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="05bea-203">在大多数情况下，使用类似语句时，最好使用 `if` 和 `elseif` 语句。</span><span class="sxs-lookup"><span data-stu-id="05bea-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="05bea-204">如果已经有一个较大的 switch，并且需要两个项来命中同一计算块，我会考虑使用这个。</span><span class="sxs-lookup"><span data-stu-id="05bea-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="05bea-205">我认为有助于增强可读性的一点是，将脚本块放在圆括号内。</span><span class="sxs-lookup"><span data-stu-id="05bea-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="05bea-206">它仍以相同的方式执行，并在快速查看时提供更好的视觉中断。</span><span class="sxs-lookup"><span data-stu-id="05bea-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="05bea-207">正则表达式 $matches</span><span class="sxs-lookup"><span data-stu-id="05bea-207">Regex $matches</span></span>

<span data-ttu-id="05bea-208">我们需要重新讨论正则表达式，以触及一些不太明显的内容。</span><span class="sxs-lookup"><span data-stu-id="05bea-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="05bea-209">使用正则表达式可填充 `$matches` 变量。</span><span class="sxs-lookup"><span data-stu-id="05bea-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="05bea-210">当我谈到[使用正则表达式的多种方式][]时，我确实更多地谈到了 `$matches` 的使用。</span><span class="sxs-lookup"><span data-stu-id="05bea-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="05bea-211">下面是一个快速示例，演示了使用命名匹配项时的情况。</span><span class="sxs-lookup"><span data-stu-id="05bea-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="05bea-212">$null</span><span class="sxs-lookup"><span data-stu-id="05bea-212">$null</span></span>

<span data-ttu-id="05bea-213">你可以匹配一个不一定是默认值的 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="05bea-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="05bea-214">对于空字符串也是如此。</span><span class="sxs-lookup"><span data-stu-id="05bea-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="05bea-215">常数表达式</span><span class="sxs-lookup"><span data-stu-id="05bea-215">Constant expression</span></span>

<span data-ttu-id="05bea-216">Lee Dailey 指出，我们可以使用恒定的 `$true` 表达式来计算 `[bool]` 项。</span><span class="sxs-lookup"><span data-stu-id="05bea-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="05bea-217">假设我们需要进行几个布尔值检查。</span><span class="sxs-lookup"><span data-stu-id="05bea-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="05bea-218">这是对若干个布尔字段的状态进行计算和执行操作的简便方法。</span><span class="sxs-lookup"><span data-stu-id="05bea-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="05bea-219">这样做的好处是，可以让一个匹配翻转尚未计算的值的状态。</span><span class="sxs-lookup"><span data-stu-id="05bea-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="05bea-220">在本例中，将 `$isEnabled` 设置为 `$true` 可确保 `$isVisible` 也设置为 `$true`。</span><span class="sxs-lookup"><span data-stu-id="05bea-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="05bea-221">然后，在计算 `$isVisible` 时，将调用其脚本块。</span><span class="sxs-lookup"><span data-stu-id="05bea-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="05bea-222">这有点违反直觉，但却是对机制的巧妙使用。</span><span class="sxs-lookup"><span data-stu-id="05bea-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="05bea-223">$switch 自动变量</span><span class="sxs-lookup"><span data-stu-id="05bea-223">$switch automatic variable</span></span>

<span data-ttu-id="05bea-224">当 `switch` 处理其值时，将创建枚举器并称其为 `$switch`。</span><span class="sxs-lookup"><span data-stu-id="05bea-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="05bea-225">这是由 PowerShell 创建的自动变量，你可以直接对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="05bea-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

<span data-ttu-id="05bea-226">这会为你提供以下结果：</span><span class="sxs-lookup"><span data-stu-id="05bea-226">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="05bea-227">向前移动枚举器，`switch` 不会处理下一项，但你可以直接访问该值。</span><span class="sxs-lookup"><span data-stu-id="05bea-227">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="05bea-228">我称之为发疯。</span><span class="sxs-lookup"><span data-stu-id="05bea-228">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="05bea-229">其他模式</span><span class="sxs-lookup"><span data-stu-id="05bea-229">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="05bea-230">哈希表</span><span class="sxs-lookup"><span data-stu-id="05bea-230">Hashtables</span></span>

<span data-ttu-id="05bea-231">我最受欢迎的文章之一是关于[哈希表][]的。</span><span class="sxs-lookup"><span data-stu-id="05bea-231">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="05bea-232">`hashtable` 的用例之一是作为查找表使用。</span><span class="sxs-lookup"><span data-stu-id="05bea-232">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="05bea-233">这是 `switch` 语句通常处理的常见模式的一种替代方法。</span><span class="sxs-lookup"><span data-stu-id="05bea-233">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="05bea-234">如果只是将 `switch` 用作查找，那么我通常会改用 `hashtable`。</span><span class="sxs-lookup"><span data-stu-id="05bea-234">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="05bea-235">枚举</span><span class="sxs-lookup"><span data-stu-id="05bea-235">Enum</span></span>

<span data-ttu-id="05bea-236">PowerShell 5.0 引入了 `Enum`，在这种情况下，它也是一个选项。</span><span class="sxs-lookup"><span data-stu-id="05bea-236">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="05bea-237">我们会一直寻找不同的方法来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="05bea-237">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="05bea-238">我只是想确定你知道你拥有选择。</span><span class="sxs-lookup"><span data-stu-id="05bea-238">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="05bea-239">结束语</span><span class="sxs-lookup"><span data-stu-id="05bea-239">Final words</span></span>

<span data-ttu-id="05bea-240">switch 语句表面上看起来很简单，但它提供了一些大多数人都不知道的高级功能。</span><span class="sxs-lookup"><span data-stu-id="05bea-240">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="05bea-241">这些功能结合在一起使它非常强大。</span><span class="sxs-lookup"><span data-stu-id="05bea-241">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="05bea-242">我希望你学到了一些之前不知道的内容。</span><span class="sxs-lookup"><span data-stu-id="05bea-242">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[使用正则表达式的多种方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[哈希表]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
