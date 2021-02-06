---
description: 退出当前作用域，它可以是函数、脚本或脚本块。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596664"
---
# <a name="about-return"></a><span data-ttu-id="61d02-103">关于返回</span><span class="sxs-lookup"><span data-stu-id="61d02-103">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="61d02-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="61d02-104">Short description</span></span>

<span data-ttu-id="61d02-105">退出当前作用域，它可以是函数、脚本或脚本块。</span><span class="sxs-lookup"><span data-stu-id="61d02-105">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="61d02-106">长说明</span><span class="sxs-lookup"><span data-stu-id="61d02-106">Long description</span></span>

<span data-ttu-id="61d02-107">`return`关键字退出函数、脚本或脚本块。</span><span class="sxs-lookup"><span data-stu-id="61d02-107">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="61d02-108">它可用于在特定点退出范围、返回值，或指示已到达范围的末尾的。</span><span class="sxs-lookup"><span data-stu-id="61d02-108">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="61d02-109">熟悉 C 或 C 语言的用户 \# 可能想要使用 `return` 关键字来使范围的逻辑成为显式的。</span><span class="sxs-lookup"><span data-stu-id="61d02-109">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="61d02-110">在 PowerShell 中，每个语句的结果作为输出返回，即使没有包含 Return 关键字的语句也是如此。</span><span class="sxs-lookup"><span data-stu-id="61d02-110">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="61d02-111">C 或 C 等语言 \# 仅返回由关键字指定的一个或哪些值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="61d02-111">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="61d02-112">从 PowerShell 5.0 开始，使用正式语法为定义类添加了用于定义类的语言。</span><span class="sxs-lookup"><span data-stu-id="61d02-112">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="61d02-113">在 PowerShell 类的上下文中，无需从方法输出，只是使用语句指定的内容 `return` 。</span><span class="sxs-lookup"><span data-stu-id="61d02-113">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="61d02-114">可以在 [about_Classes](about_Classes.md)中阅读有关 PowerShell 类的详细信息。</span><span class="sxs-lookup"><span data-stu-id="61d02-114">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="61d02-115">语法</span><span class="sxs-lookup"><span data-stu-id="61d02-115">Syntax</span></span>

<span data-ttu-id="61d02-116">关键字的语法如下所示 `return` ：</span><span class="sxs-lookup"><span data-stu-id="61d02-116">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="61d02-117">`return`关键字可以单独显示，也可以后跟值或表达式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="61d02-117">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="61d02-118">示例</span><span class="sxs-lookup"><span data-stu-id="61d02-118">Examples</span></span>

<span data-ttu-id="61d02-119">下面的示例使用 `return` 关键字在满足条件时在特定的时间点退出函数。</span><span class="sxs-lookup"><span data-stu-id="61d02-119">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="61d02-120">不会将奇数相乘，因为 return 语句会在执行该语句之前退出。</span><span class="sxs-lookup"><span data-stu-id="61d02-120">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

<span data-ttu-id="61d02-121">在 PowerShell 中，即使未使用关键字，也可以返回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="61d02-121">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="61d02-122">返回每个语句的结果。</span><span class="sxs-lookup"><span data-stu-id="61d02-122">The results of each statement are returned.</span></span> <span data-ttu-id="61d02-123">例如，下面的语句返回变量的值 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="61d02-123">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="61d02-124">以下语句还返回值 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="61d02-124">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="61d02-125">下面的示例包含一个语句，该语句用于使用户知道函数正在执行计算：</span><span class="sxs-lookup"><span data-stu-id="61d02-125">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="61d02-126">"请等待。</span><span class="sxs-lookup"><span data-stu-id="61d02-126">The "Please wait.</span></span> <span data-ttu-id="61d02-127">正在处理计算 ... "不显示字符串。</span><span class="sxs-lookup"><span data-stu-id="61d02-127">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="61d02-128">相反，会将其分配给 `$a` 变量，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="61d02-128">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="61d02-129">该函数返回信息性字符串和计算结果，并将其分配给 `$a` 变量。</span><span class="sxs-lookup"><span data-stu-id="61d02-129">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="61d02-130">如果要在函数中显示一条消息，从 PowerShell 5.0 开始，可以使用 `Information` 流。</span><span class="sxs-lookup"><span data-stu-id="61d02-130">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="61d02-131">下面的代码通过将 `Write-Information` cmdlet 用于 `InformationAction` **Continue** 来更正上面的示例。</span><span class="sxs-lookup"><span data-stu-id="61d02-131">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="61d02-132">返回值和管道</span><span class="sxs-lookup"><span data-stu-id="61d02-132">Return values and the Pipeline</span></span>

<span data-ttu-id="61d02-133">从脚本块或函数返回集合时，PowerShell 会自动 unrolls 成员，并通过管道一次传递一个成员。</span><span class="sxs-lookup"><span data-stu-id="61d02-133">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="61d02-134">这是因为 PowerShell 的一次性处理。</span><span class="sxs-lookup"><span data-stu-id="61d02-134">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="61d02-135">有关详细信息，请参阅 [about_pipelines](about_pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="61d02-135">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="61d02-136">下面的示例函数阐释了此概念，该函数返回数字的数组。</span><span class="sxs-lookup"><span data-stu-id="61d02-136">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="61d02-137">函数的输出通过管道传递给 cmdlet， `Measure-Object` 后者对管道中的对象数量进行计数。</span><span class="sxs-lookup"><span data-stu-id="61d02-137">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="61d02-138">若要强制脚本块或函数将集合作为单个对象返回到管道，请使用以下两种方法之一：</span><span class="sxs-lookup"><span data-stu-id="61d02-138">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="61d02-139">一元数组表达式</span><span class="sxs-lookup"><span data-stu-id="61d02-139">Unary array expression</span></span>

  <span data-ttu-id="61d02-140">利用一元表达式，你可以将返回值作为单个对象发送到管道，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="61d02-140">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- <span data-ttu-id="61d02-141">`Write-Output` with **NoEnumerate** 参数。</span><span class="sxs-lookup"><span data-stu-id="61d02-141">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="61d02-142">你还可以将 `Write-Output` cmdlet 与 **NoEnumerate** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="61d02-142">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="61d02-143">下面的示例使用 `Measure-Object` cmdlet 来计算由关键字从示例函数发送到管道的对象 `return` 。</span><span class="sxs-lookup"><span data-stu-id="61d02-143">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a><span data-ttu-id="61d02-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="61d02-144">See also</span></span>

[<span data-ttu-id="61d02-145">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="61d02-145">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="61d02-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="61d02-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="61d02-147">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="61d02-147">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="61d02-148">about_Classes</span><span class="sxs-lookup"><span data-stu-id="61d02-148">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="61d02-149">Write-Information</span><span class="sxs-lookup"><span data-stu-id="61d02-149">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="61d02-150">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="61d02-150">about_Script_Blocks</span></span>](about_Script_Blocks.md)

