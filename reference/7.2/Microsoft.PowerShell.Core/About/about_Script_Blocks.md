---
description: 定义脚本块的定义，并说明如何在 PowerShell 编程语言中使用脚本块。
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596238"
---
# <a name="about-script-blocks"></a><span data-ttu-id="c98bc-103">关于脚本块</span><span class="sxs-lookup"><span data-stu-id="c98bc-103">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="c98bc-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="c98bc-104">Short description</span></span>

<span data-ttu-id="c98bc-105">定义脚本块的定义，并说明如何在 PowerShell 编程语言中使用脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-105">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="c98bc-106">长说明</span><span class="sxs-lookup"><span data-stu-id="c98bc-106">Long description</span></span>

<span data-ttu-id="c98bc-107">在 PowerShell 编程语言中，脚本块是可用作单个单元的语句或表达式的集合。</span><span class="sxs-lookup"><span data-stu-id="c98bc-107">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="c98bc-108">脚本块可以接受参数并返回值。</span><span class="sxs-lookup"><span data-stu-id="c98bc-108">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="c98bc-109">从语法上讲，脚本块是括在大括号中的语句列表，如下面的语法所示：</span><span class="sxs-lookup"><span data-stu-id="c98bc-109">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="c98bc-110">脚本块以单个对象或数组形式返回脚本块中所有命令的输出。</span><span class="sxs-lookup"><span data-stu-id="c98bc-110">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="c98bc-111">你还可以使用关键字指定返回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-111">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="c98bc-112">`return`关键字不会影响或禁止从脚本块返回的其他输出。</span><span class="sxs-lookup"><span data-stu-id="c98bc-112">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="c98bc-113">不过， `return` 关键字退出该脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-113">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="c98bc-114">有关详细信息，请参阅 [about_Return](about_Return.md)。</span><span class="sxs-lookup"><span data-stu-id="c98bc-114">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="c98bc-115">与函数一样，脚本块可以包含参数。</span><span class="sxs-lookup"><span data-stu-id="c98bc-115">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="c98bc-116">使用 Param 关键字分配命名参数，如以下语法所示：</span><span class="sxs-lookup"><span data-stu-id="c98bc-116">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="c98bc-117">在脚本块中，与函数不同，不能在大括号之外指定参数。</span><span class="sxs-lookup"><span data-stu-id="c98bc-117">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="c98bc-118">与函数一样，脚本块可以包含 `DynamicParam` 、 `Begin` 、 `Process` 和 `End` 关键字。</span><span class="sxs-lookup"><span data-stu-id="c98bc-118">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="c98bc-119">有关详细信息，请参阅 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="c98bc-119">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="c98bc-120">使用脚本块</span><span class="sxs-lookup"><span data-stu-id="c98bc-120">Using Script Blocks</span></span>

<span data-ttu-id="c98bc-121">脚本块是 Microsoft .NET 框架类型的实例 `System.Management.Automation.ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-121">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="c98bc-122">命令可以具有脚本块参数值。</span><span class="sxs-lookup"><span data-stu-id="c98bc-122">Commands can have script block parameter values.</span></span> <span data-ttu-id="c98bc-123">例如， `Invoke-Command` cmdlet 具有一个 `ScriptBlock` 采用脚本块值的参数，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="c98bc-123">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="c98bc-124">`Invoke-Command` 还可以执行具有参数块的脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-124">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="c98bc-125">使用 **ArgumentList** 参数按位置分配参数。</span><span class="sxs-lookup"><span data-stu-id="c98bc-125">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="c98bc-126">前面的示例中的脚本块使用 `param` 关键字创建参数 `$p1` 和 `$p2` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-126">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="c98bc-127">字符串 "First" 绑定到)  (第一个参数 `$p1` ，而 "Second" 绑定到 (`$p2`) 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-127">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="c98bc-128">有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="c98bc-128">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="c98bc-129">您可以使用变量来存储和执行脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-129">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="c98bc-130">下面的示例将一个脚本块存储在一个变量中，并将其传递给 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-130">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="c98bc-131">Call 运算符是执行存储在变量中的脚本块的另一种方法。</span><span class="sxs-lookup"><span data-stu-id="c98bc-131">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="c98bc-132">与一样 `Invoke-Command` ，调用运算符执行子范围中的脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-132">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="c98bc-133">调用运算符可使你更轻松地将参数用于脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-133">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="c98bc-134">您可以使用赋值将脚本块中的输出存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="c98bc-134">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="c98bc-135">有关调用运算符的详细信息，请参阅 [about_Operators](about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="c98bc-135">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="c98bc-136">将延迟绑定脚本块与参数一起使用</span><span class="sxs-lookup"><span data-stu-id="c98bc-136">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="c98bc-137">一个类型化参数，该参数接受管道输入 (`by Value`) 或 (`by PropertyName`) 允许在参数上使用 **延迟绑定** 脚本块。</span><span class="sxs-lookup"><span data-stu-id="c98bc-137">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="c98bc-138">在 **延迟绑定** 脚本块中，可以使用管道变量引用对象中的管道 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-138">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="c98bc-139">在更复杂的 cmdlet 中，延迟绑定脚本块允许在对象中重复使用一个管道来填充其他参数。</span><span class="sxs-lookup"><span data-stu-id="c98bc-139">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="c98bc-140">延迟时 **的说明-** 将脚本块绑定为参数：</span><span class="sxs-lookup"><span data-stu-id="c98bc-140">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="c98bc-141">您必须显式指定任何用于 **延迟绑定** 脚本块的参数名称。</span><span class="sxs-lookup"><span data-stu-id="c98bc-141">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="c98bc-142">参数不能是非类型化的，并且参数的类型不能为 `[scriptblock]` 或 `[object]` 。</span><span class="sxs-lookup"><span data-stu-id="c98bc-142">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="c98bc-143">如果在不提供管道输入的情况下使用 **延迟绑定** 脚本块，会收到错误。</span><span class="sxs-lookup"><span data-stu-id="c98bc-143">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="c98bc-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c98bc-144">See Also</span></span>

[<span data-ttu-id="c98bc-145">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c98bc-145">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="c98bc-146">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="c98bc-146">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="c98bc-147">about_Operators</span><span class="sxs-lookup"><span data-stu-id="c98bc-147">about_Operators</span></span>](about_Operators.md)

