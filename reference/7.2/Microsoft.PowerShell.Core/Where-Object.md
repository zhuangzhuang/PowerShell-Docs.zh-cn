---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 667a503d67ac9a9a0f41187cbac079d946247618
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596826"
---
# <span data-ttu-id="daf61-102">Where-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-102">Where-Object</span></span>

## <span data-ttu-id="daf61-103">摘要</span><span class="sxs-lookup"><span data-stu-id="daf61-103">SYNOPSIS</span></span>
<span data-ttu-id="daf61-104">根据属性值从集合中选择对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-104">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="daf61-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="daf61-105">SYNTAX</span></span>

### <span data-ttu-id="daf61-106">EqualSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="daf61-106">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-107">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="daf61-107">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="daf61-108">MatchSet</span><span class="sxs-lookup"><span data-stu-id="daf61-108">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-109">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-109">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-110">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-110">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-111">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-111">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-112">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="daf61-112">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-113">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="daf61-113">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-114">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="daf61-114">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-115">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="daf61-115">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-116">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-116">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-117">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-117">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-118">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-118">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-119">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="daf61-119">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-120">LikeSet</span><span class="sxs-lookup"><span data-stu-id="daf61-120">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-121">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="daf61-121">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-122">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="daf61-122">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-123">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="daf61-123">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-124">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="daf61-124">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-125">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="daf61-125">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-126">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="daf61-126">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-127">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="daf61-127">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-128">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="daf61-128">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-129">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="daf61-129">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-130">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="daf61-130">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-131">嵌入</span><span class="sxs-lookup"><span data-stu-id="daf61-131">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-132">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="daf61-132">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-133">NotInSet</span><span class="sxs-lookup"><span data-stu-id="daf61-133">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-134">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="daf61-134">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-135">IsSet</span><span class="sxs-lookup"><span data-stu-id="daf61-135">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-136">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="daf61-136">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="daf61-137">Not</span><span class="sxs-lookup"><span data-stu-id="daf61-137">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="daf61-138">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="daf61-138">DESCRIPTION</span></span>

<span data-ttu-id="daf61-139">`Where-Object`Cmdlet 从传递给它的对象集合中选择具有特定属性值的对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-139">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="daf61-140">例如，你可以使用 `Where-Object` cmdlet 来选择在特定日期之后创建的文件、具有特定 ID 的事件，或使用特定版本的 Windows 的计算机。</span><span class="sxs-lookup"><span data-stu-id="daf61-140">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="daf61-141">从 Windows PowerShell 3.0 开始，可以使用两种不同的方法来构造 `Where-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="daf61-141">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="daf61-142">**脚本块**。</span><span class="sxs-lookup"><span data-stu-id="daf61-142">**Script block**.</span></span> <span data-ttu-id="daf61-143">你可以使用脚本块指定属性名称、比较运算符和属性值。</span><span class="sxs-lookup"><span data-stu-id="daf61-143">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="daf61-144">`Where-Object` 返回脚本块语句为 true 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-144">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="daf61-145">例如，下面的命令获取一般优先级类中的进程，即 **PriorityClass** 属性的值等于 Normal 的进程。</span><span class="sxs-lookup"><span data-stu-id="daf61-145">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="daf61-146">所有 PowerShell 比较运算符在脚本块格式中都有效。</span><span class="sxs-lookup"><span data-stu-id="daf61-146">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="daf61-147">有关比较运算符的详细信息，请参阅 [about_Comparison_Operators](./About/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="daf61-147">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="daf61-148">**比较语句**。</span><span class="sxs-lookup"><span data-stu-id="daf61-148">**Comparison statement**.</span></span> <span data-ttu-id="daf61-149">你还可以编写比较语句，它更像自然语言。</span><span class="sxs-lookup"><span data-stu-id="daf61-149">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="daf61-150">Windows PowerShell 3.0 中引入了比较语句。</span><span class="sxs-lookup"><span data-stu-id="daf61-150">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="daf61-151">例如，以下命令还获取优先级为 Normal 的进程。</span><span class="sxs-lookup"><span data-stu-id="daf61-151">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="daf61-152">这些命令是等效的，因此可以互换使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-152">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="daf61-153">从 Windows PowerShell 3.0 开始， `Where-Object` 将比较运算符作为参数添加到 `Where-Object` 命令中。</span><span class="sxs-lookup"><span data-stu-id="daf61-153">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="daf61-154">除非另有指定，否则所有运算符都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-154">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="daf61-155">在 Windows PowerShell 3.0 之前，PowerShell 语言中的比较运算符仅可在脚本块中使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-155">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="daf61-156">向提供单个 **属性** 时 `Where-Object` ，属性的值将被视为布尔表达式。</span><span class="sxs-lookup"><span data-stu-id="daf61-156">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="daf61-157">当 **Length** 的值不为零时，表达式的计算结果为 **True**。</span><span class="sxs-lookup"><span data-stu-id="daf61-157">When the value of **Length** is not zero, the expression evaluates to **True**.</span></span> <span data-ttu-id="daf61-158">例如： `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="daf61-158">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="daf61-159">上一示例在功能上等效于：</span><span class="sxs-lookup"><span data-stu-id="daf61-159">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="daf61-160">示例</span><span class="sxs-lookup"><span data-stu-id="daf61-160">EXAMPLES</span></span>

### <span data-ttu-id="daf61-161">示例1：获取已停止的服务</span><span class="sxs-lookup"><span data-stu-id="daf61-161">Example 1: Get stopped services</span></span>

<span data-ttu-id="daf61-162">这些命令将获取当前已停止的所有服务的列表。</span><span class="sxs-lookup"><span data-stu-id="daf61-162">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="daf61-163">`$_`自动变量表示传递到 cmdlet 的每个对象 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-163">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="daf61-164">第一个命令使用脚本块格式，第二个命令使用比较语句格式。</span><span class="sxs-lookup"><span data-stu-id="daf61-164">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="daf61-165">这两个命令是等效的，因此可以互换使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-165">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="daf61-166">示例2：基于工作集获取进程</span><span class="sxs-lookup"><span data-stu-id="daf61-166">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="daf61-167">这些命令列出了工作集大于 250 mb (KB) 的进程。</span><span class="sxs-lookup"><span data-stu-id="daf61-167">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="daf61-168">Scriptblock 和语句语法是等效的，可互换使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-168">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="daf61-169">示例3：基于进程名称获取进程</span><span class="sxs-lookup"><span data-stu-id="daf61-169">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="daf61-170">这些命令将获取 **ProcessName** 属性值以字母开头的进程 `p` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-170">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="daf61-171">**Match** 运算符使你可以使用正则表达式匹配。</span><span class="sxs-lookup"><span data-stu-id="daf61-171">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="daf61-172">Scriptblock 和语句语法是等效的，可互换使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-172">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="daf61-173">示例4：使用比较语句格式</span><span class="sxs-lookup"><span data-stu-id="daf61-173">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="daf61-174">此示例演示如何使用 cmdlet 的新比较语句格式 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-174">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="daf61-175">第一个命令使用比较语句格式。</span><span class="sxs-lookup"><span data-stu-id="daf61-175">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="daf61-176">在此命令中，未使用别名，并且所有参数都包含参数名称。</span><span class="sxs-lookup"><span data-stu-id="daf61-176">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="daf61-177">第二个命令是比较命令格式的更自然的用法。</span><span class="sxs-lookup"><span data-stu-id="daf61-177">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="daf61-178">该 `where` 别名替换为 `Where-Object` cmdlet 名称，并且省略了所有可选参数名称。</span><span class="sxs-lookup"><span data-stu-id="daf61-178">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="daf61-179">示例5：获取基于属性的命令</span><span class="sxs-lookup"><span data-stu-id="daf61-179">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="daf61-180">此示例演示如何编写可返回项（true 或 false）的命令或具有指定属性的任意值的命令。</span><span class="sxs-lookup"><span data-stu-id="daf61-180">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="daf61-181">每个示例显示该命令的脚本块和比较语句格式。</span><span class="sxs-lookup"><span data-stu-id="daf61-181">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="daf61-182">示例6：使用多个条件</span><span class="sxs-lookup"><span data-stu-id="daf61-182">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="daf61-183">此示例演示如何创建 `Where-Object` 具有多个条件的命令。</span><span class="sxs-lookup"><span data-stu-id="daf61-183">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="daf61-184">此命令可获取用于支持可更新帮助功能的非核心模块。</span><span class="sxs-lookup"><span data-stu-id="daf61-184">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="daf61-185">该命令使用 cmdlet 的 **ListAvailable** 参数 `Get-Module` 来获取计算机上的所有模块。</span><span class="sxs-lookup"><span data-stu-id="daf61-185">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="daf61-186">管道运算符 (`|`) 将模块发送到 `Where-Object` cmdlet，该 cmdlet 将获取名称不以 MICROSOFT 或 PS 开头的模块，并为 **HelpInfoURI** 属性提供一个值，该值指示 PowerShell 在何处找到该模块的更新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="daf61-186">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="daf61-187">比较语句由 **和** 逻辑运算符连接。</span><span class="sxs-lookup"><span data-stu-id="daf61-187">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="daf61-188">该示例使用脚本块命令格式。</span><span class="sxs-lookup"><span data-stu-id="daf61-188">The example uses the script block command format.</span></span> <span data-ttu-id="daf61-189">逻辑运算符（如 **and** 和 **Or**）仅在脚本块中有效。</span><span class="sxs-lookup"><span data-stu-id="daf61-189">Logical operators, such as **And** and **Or**, are valid only in script blocks.</span></span> <span data-ttu-id="daf61-190">不能以命令的比较语句格式使用它们 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-190">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="daf61-191">有关 PowerShell 逻辑运算符的详细信息，请参阅 [about_Logical_Operators](./About/about_logical_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="daf61-191">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="daf61-192">有关可更新帮助功能的详细信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="daf61-192">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="daf61-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="daf61-193">PARAMETERS</span></span>

### <span data-ttu-id="daf61-194">-包含</span><span class="sxs-lookup"><span data-stu-id="daf61-194">-CContains</span></span>

<span data-ttu-id="daf61-195">指示如果对象的属性值与指定值完全匹配，此 cmdlet 将从集合中获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-195">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="daf61-196">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-196">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-197">例如： `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="daf61-197">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="daf61-198">**包含** 引用值的集合，如果集合包含与指定值完全匹配的项，则为 true。</span><span class="sxs-lookup"><span data-stu-id="daf61-198">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="daf61-199">如果输入是单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-199">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-200">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-201">-CEQ</span><span class="sxs-lookup"><span data-stu-id="daf61-201">-CEQ</span></span>

<span data-ttu-id="daf61-202">指示此 cmdlet 获取对象（如果属性值与指定的值相同）。</span><span class="sxs-lookup"><span data-stu-id="daf61-202">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="daf61-203">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-203">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-204">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-205">-CGE</span><span class="sxs-lookup"><span data-stu-id="daf61-205">-CGE</span></span>

<span data-ttu-id="daf61-206">指示此 cmdlet 获取对象（如果属性值大于或等于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-206">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="daf61-207">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-207">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-208">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-209">-CGT</span><span class="sxs-lookup"><span data-stu-id="daf61-209">-CGT</span></span>

<span data-ttu-id="daf61-210">指示此 cmdlet 获取对象（如果属性值大于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-210">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="daf61-211">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-211">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-212">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-213">-CIn</span><span class="sxs-lookup"><span data-stu-id="daf61-213">-CIn</span></span>

<span data-ttu-id="daf61-214">指示此 cmdlet 在属性值包含指定值时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-214">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="daf61-215">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-215">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-216">例如： `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="daf61-216">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="daf61-217">**CIn** 类似于 **包含**，只不过属性和值位置是相反的。</span><span class="sxs-lookup"><span data-stu-id="daf61-217">**CIn** resembles **CContains**, except that the property and value positions are reversed.</span></span> <span data-ttu-id="daf61-218">例如，以下语句都为 true。</span><span class="sxs-lookup"><span data-stu-id="daf61-218">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="daf61-219">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-219">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-220">-CLE</span><span class="sxs-lookup"><span data-stu-id="daf61-220">-CLE</span></span>

<span data-ttu-id="daf61-221">指示在属性值小于或等于指定值的情况下，此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-221">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="daf61-222">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-222">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-223">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-223">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-224">-CLike</span><span class="sxs-lookup"><span data-stu-id="daf61-224">-CLike</span></span>

<span data-ttu-id="daf61-225">指示此 cmdlet 在属性值与包含通配符的值匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-225">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="daf61-226">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-226">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-227">例如： `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="daf61-227">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="daf61-228">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-229">-CLT</span><span class="sxs-lookup"><span data-stu-id="daf61-229">-CLT</span></span>

<span data-ttu-id="daf61-230">指示此 cmdlet 获取对象（如果属性值小于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-230">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="daf61-231">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-231">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-232">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-233">-CMatch</span><span class="sxs-lookup"><span data-stu-id="daf61-233">-CMatch</span></span>

<span data-ttu-id="daf61-234">指示此 cmdlet 在属性值与指定的正则表达式匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-234">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="daf61-235">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-235">This operation is case-sensitive.</span></span> <span data-ttu-id="daf61-236">当输入是标量时，匹配的值将保存在 `$Matches` 自动变量中。</span><span class="sxs-lookup"><span data-stu-id="daf61-236">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="daf61-237">例如： `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="daf61-237">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="daf61-238">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-239">-CNE</span><span class="sxs-lookup"><span data-stu-id="daf61-239">-CNE</span></span>

<span data-ttu-id="daf61-240">指示此 cmdlet 获取对象（如果属性值不同于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-240">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="daf61-241">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-241">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-242">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-243">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="daf61-243">-CNotContains</span></span>

<span data-ttu-id="daf61-244">指示如果对象的属性值与指定的值不完全匹配，则此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-244">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="daf61-245">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-245">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-246">例如： `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="daf61-246">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="daf61-247">**NotContains** 和 **CNotContains** 引用值的集合，并且在集合不包含与指定值完全匹配的任何项时为 true。</span><span class="sxs-lookup"><span data-stu-id="daf61-247">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="daf61-248">如果输入是单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-248">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-249">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-250">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="daf61-250">-CNotIn</span></span>

<span data-ttu-id="daf61-251">指示此 cmdlet 获取对象（如果属性值不是指定值的完全匹配项）。</span><span class="sxs-lookup"><span data-stu-id="daf61-251">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="daf61-252">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-252">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-253">例如： `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="daf61-253">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="daf61-254">**NotIn** 和 **CNotIn** 运算符类似于 **NotContains** 和 **CNotContains**，只不过属性和值位置是相反的。</span><span class="sxs-lookup"><span data-stu-id="daf61-254">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains**, except that the property and value positions are reversed.</span></span> <span data-ttu-id="daf61-255">例如，以下语句为 true。</span><span class="sxs-lookup"><span data-stu-id="daf61-255">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-256">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="daf61-256">-CNotLike</span></span>

<span data-ttu-id="daf61-257">指示如果属性值与包含通配符的值不匹配，则此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-257">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="daf61-258">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-258">This operation is case-sensitive.</span></span>

<span data-ttu-id="daf61-259">例如： `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="daf61-259">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="daf61-260">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-261">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="daf61-261">-CNotMatch</span></span>

<span data-ttu-id="daf61-262">指示此 cmdlet 在属性值与指定的正则表达式不匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-262">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="daf61-263">此操作区分大小写。</span><span class="sxs-lookup"><span data-stu-id="daf61-263">This operation is case-sensitive.</span></span> <span data-ttu-id="daf61-264">当输入是标量时，匹配的值将保存在 `$Matches` 自动变量中。</span><span class="sxs-lookup"><span data-stu-id="daf61-264">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="daf61-265">例如： `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="daf61-265">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="daf61-266">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-267">-Contains</span><span class="sxs-lookup"><span data-stu-id="daf61-267">-Contains</span></span>

<span data-ttu-id="daf61-268">指示如果对象的属性值中的任何项与指定值完全匹配，则此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-268">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="daf61-269">例如： `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="daf61-269">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="daf61-270">如果属性值包含单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-270">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-271">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-272">-EQ</span><span class="sxs-lookup"><span data-stu-id="daf61-272">-EQ</span></span>

<span data-ttu-id="daf61-273">指示此 cmdlet 获取对象（如果属性值与指定的值相同）。</span><span class="sxs-lookup"><span data-stu-id="daf61-273">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="daf61-274">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-275">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="daf61-275">-FilterScript</span></span>

<span data-ttu-id="daf61-276">指定用于筛选对象的脚本块。</span><span class="sxs-lookup"><span data-stu-id="daf61-276">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="daf61-277">将脚本块括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="daf61-277">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="daf61-278">参数 name （ **FilterScript**）是可选的。</span><span class="sxs-lookup"><span data-stu-id="daf61-278">The parameter name, **FilterScript**, is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-279">-GE</span><span class="sxs-lookup"><span data-stu-id="daf61-279">-GE</span></span>

<span data-ttu-id="daf61-280">指示此 cmdlet 获取对象（如果属性值大于或等于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-280">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="daf61-281">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-282">-GT</span><span class="sxs-lookup"><span data-stu-id="daf61-282">-GT</span></span>

<span data-ttu-id="daf61-283">指示此 cmdlet 获取对象（如果属性值大于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-283">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="daf61-284">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-285">-在中</span><span class="sxs-lookup"><span data-stu-id="daf61-285">-In</span></span>

<span data-ttu-id="daf61-286">指示此 cmdlet 获取对象（如果属性值与任何指定值匹配）。</span><span class="sxs-lookup"><span data-stu-id="daf61-286">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="daf61-287">例如：</span><span class="sxs-lookup"><span data-stu-id="daf61-287">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="daf61-288">如果 **value** 参数的值是单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-288">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-289">如果对象的属性值是一个数组，则 PowerShell 将使用引用相等性来确定匹配项。</span><span class="sxs-lookup"><span data-stu-id="daf61-289">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="daf61-290">`Where-Object` 仅当 **Property** 参数的值和 **value** 的任何值都是对象的相同实例时才返回对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-290">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="daf61-291">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-292">-InputObject</span><span class="sxs-lookup"><span data-stu-id="daf61-292">-InputObject</span></span>

<span data-ttu-id="daf61-293">指定要筛选的对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-293">Specifies the objects to be filtered.</span></span> <span data-ttu-id="daf61-294">还可以通过管道将对象传递给 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-294">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="daf61-295">当你将 **inputobject** 参数与一起使用时 `Where-Object` ， `Where-Object` **inputobject** 值将被视为单个对象，而不是管道将命令结果传递给。</span><span class="sxs-lookup"><span data-stu-id="daf61-295">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="daf61-296">即使该值是作为命令结果的集合（如），也是如此 `-InputObject (Get-Process)` 。</span><span class="sxs-lookup"><span data-stu-id="daf61-296">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="daf61-297">由于 **InputObject** 无法从数组或对象的集合返回各个属性，因此，如果您使用 `Where-Object` 筛选在定义的属性中具有特定值的那些对象的对象集合，则建议在管道中使用 `Where-Object` ，如本主题的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="daf61-297">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-298">-为</span><span class="sxs-lookup"><span data-stu-id="daf61-298">-Is</span></span>

<span data-ttu-id="daf61-299">指示此 cmdlet 获取对象（如果属性值为指定 .NET 类型的实例）。</span><span class="sxs-lookup"><span data-stu-id="daf61-299">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="daf61-300">将类型名称括在方括号中。</span><span class="sxs-lookup"><span data-stu-id="daf61-300">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="daf61-301">例如，`Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="daf61-301">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="daf61-302">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-302">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-303">-IsNot</span><span class="sxs-lookup"><span data-stu-id="daf61-303">-IsNot</span></span>

<span data-ttu-id="daf61-304">指示此 cmdlet 获取对象（如果属性值不是指定 .NET 类型的实例）。</span><span class="sxs-lookup"><span data-stu-id="daf61-304">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="daf61-305">例如，`Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="daf61-305">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="daf61-306">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-306">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-307">-LE</span><span class="sxs-lookup"><span data-stu-id="daf61-307">-LE</span></span>

<span data-ttu-id="daf61-308">指示此 cmdlet 在属性值小于或等于指定值时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-308">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="daf61-309">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-309">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-310">-Like</span><span class="sxs-lookup"><span data-stu-id="daf61-310">-Like</span></span>

<span data-ttu-id="daf61-311">指示此 cmdlet 在属性值与包含通配符的值匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-311">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="daf61-312">例如： `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="daf61-312">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="daf61-313">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-313">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-314">-LT</span><span class="sxs-lookup"><span data-stu-id="daf61-314">-LT</span></span>

<span data-ttu-id="daf61-315">指示此 cmdlet 获取对象（如果属性值小于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-315">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="daf61-316">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-317">-Match</span><span class="sxs-lookup"><span data-stu-id="daf61-317">-Match</span></span>

<span data-ttu-id="daf61-318">指示此 cmdlet 在属性值与指定的正则表达式匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-318">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="daf61-319">当输入是标量时，匹配的值将保存在 `$Matches` 自动变量中。</span><span class="sxs-lookup"><span data-stu-id="daf61-319">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="daf61-320">例如： `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="daf61-320">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="daf61-321">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-322">-NE</span><span class="sxs-lookup"><span data-stu-id="daf61-322">-NE</span></span>

<span data-ttu-id="daf61-323">指示此 cmdlet 获取对象（如果属性值不同于指定值）。</span><span class="sxs-lookup"><span data-stu-id="daf61-323">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="daf61-324">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-325">-Not</span><span class="sxs-lookup"><span data-stu-id="daf61-325">-Not</span></span>

<span data-ttu-id="daf61-326">指示此 cmdlet 获取对象（如果属性不存在）或值为 null 或 false。</span><span class="sxs-lookup"><span data-stu-id="daf61-326">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="daf61-327">例如： `Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="daf61-327">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="daf61-328">此参数是在 Windows PowerShell 6.1 中引入的。</span><span class="sxs-lookup"><span data-stu-id="daf61-328">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-329">-NotContains</span><span class="sxs-lookup"><span data-stu-id="daf61-329">-NotContains</span></span>

<span data-ttu-id="daf61-330">指示如果属性值中的任何项都不是指定值的完全匹配项，则此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-330">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="daf61-331">例如： `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="daf61-331">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="daf61-332">**NotContains** 引用值的集合，如果该集合不包含任何与指定值完全匹配的项，则为 true。</span><span class="sxs-lookup"><span data-stu-id="daf61-332">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="daf61-333">如果输入是单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-333">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-334">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-334">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-335">-NotIn</span><span class="sxs-lookup"><span data-stu-id="daf61-335">-NotIn</span></span>

<span data-ttu-id="daf61-336">指示此 cmdlet 获取对象（如果属性值不与任何指定值完全匹配）。</span><span class="sxs-lookup"><span data-stu-id="daf61-336">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="daf61-337">例如： `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="daf61-337">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="daf61-338">如果 **value** 的值是单个对象，则 PowerShell 会将其转换为一个对象的集合。</span><span class="sxs-lookup"><span data-stu-id="daf61-338">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="daf61-339">如果对象的属性值是一个数组，则 PowerShell 将使用引用相等性来确定匹配项。</span><span class="sxs-lookup"><span data-stu-id="daf61-339">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="daf61-340">`Where-Object` 仅当 **属性** 的值和 **值** 的任何值都不是对象的相同实例时才返回对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-340">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="daf61-341">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-341">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-342">-NotLike</span><span class="sxs-lookup"><span data-stu-id="daf61-342">-NotLike</span></span>

<span data-ttu-id="daf61-343">指示如果属性值与包含通配符的值不匹配，则此 cmdlet 将获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-343">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="daf61-344">例如： `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="daf61-344">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="daf61-345">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-345">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-346">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="daf61-346">-NotMatch</span></span>

<span data-ttu-id="daf61-347">指示此 cmdlet 在属性值与指定的正则表达式不匹配时获取对象。</span><span class="sxs-lookup"><span data-stu-id="daf61-347">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="daf61-348">当输入是标量时，匹配的值将保存在 `$Matches` 自动变量中。</span><span class="sxs-lookup"><span data-stu-id="daf61-348">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="daf61-349">例如： `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="daf61-349">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="daf61-350">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-350">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-351">-Property</span><span class="sxs-lookup"><span data-stu-id="daf61-351">-Property</span></span>

<span data-ttu-id="daf61-352">指定对象属性的名称。</span><span class="sxs-lookup"><span data-stu-id="daf61-352">Specifies the name of an object property.</span></span> <span data-ttu-id="daf61-353">参数名称、 **属性** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="daf61-353">The parameter name, **Property**, is optional.</span></span>

<span data-ttu-id="daf61-354">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-354">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="daf61-355">-Value</span><span class="sxs-lookup"><span data-stu-id="daf61-355">-Value</span></span>

<span data-ttu-id="daf61-356">指定属性值。</span><span class="sxs-lookup"><span data-stu-id="daf61-356">Specifies a property value.</span></span> <span data-ttu-id="daf61-357">参数名称， **值** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="daf61-357">The parameter name, **Value**, is optional.</span></span> <span data-ttu-id="daf61-358">与以下比较参数一起使用时，此参数可接受通配符：</span><span class="sxs-lookup"><span data-stu-id="daf61-358">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="daf61-359">**CLike**</span><span class="sxs-lookup"><span data-stu-id="daf61-359">**CLike**</span></span>
- <span data-ttu-id="daf61-360">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="daf61-360">**CNotLike**</span></span>
- <span data-ttu-id="daf61-361">**外观**</span><span class="sxs-lookup"><span data-stu-id="daf61-361">**Like**</span></span>
- <span data-ttu-id="daf61-362">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="daf61-362">**NotLike**</span></span>

<span data-ttu-id="daf61-363">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="daf61-363">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="daf61-364">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="daf61-364">CommonParameters</span></span>

<span data-ttu-id="daf61-365">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="daf61-365">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="daf61-366">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="daf61-366">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="daf61-367">输入</span><span class="sxs-lookup"><span data-stu-id="daf61-367">INPUTS</span></span>

### <span data-ttu-id="daf61-368">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="daf61-368">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="daf61-369">可以通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="daf61-369">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="daf61-370">输出</span><span class="sxs-lookup"><span data-stu-id="daf61-370">OUTPUTS</span></span>

### <span data-ttu-id="daf61-371">对象</span><span class="sxs-lookup"><span data-stu-id="daf61-371">Object</span></span>

<span data-ttu-id="daf61-372">此 cmdlet 将返回输入对象集中的选定项。</span><span class="sxs-lookup"><span data-stu-id="daf61-372">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="daf61-373">注释</span><span class="sxs-lookup"><span data-stu-id="daf61-373">NOTES</span></span>

<span data-ttu-id="daf61-374">从 Windows PowerShell 4.0 开始， `Where` `ForEach` 添加了方法以与集合一起使用。</span><span class="sxs-lookup"><span data-stu-id="daf61-374">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="daf61-375">可在此处阅读有关这些新方法的详细信息 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="daf61-375">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="daf61-376">相关链接</span><span class="sxs-lookup"><span data-stu-id="daf61-376">RELATED LINKS</span></span>

[<span data-ttu-id="daf61-377">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-377">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="daf61-378">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-378">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="daf61-379">Group-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-379">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="daf61-380">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-380">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="daf61-381">New-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-381">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="daf61-382">Select-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-382">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="daf61-383">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-383">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="daf61-384">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="daf61-384">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)

