---
description: 介绍如何创建和使用引用类型变量。 您可以使用引用类型变量来允许函数更改传递给它的变量的值。
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 5b966816c8ac1ef91e03c78378f57fa20b5697de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595627"
---
# <a name="about-ref"></a><span data-ttu-id="ee8bf-104">关于 Ref</span><span class="sxs-lookup"><span data-stu-id="ee8bf-104">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="ee8bf-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="ee8bf-105">Short description</span></span>
<span data-ttu-id="ee8bf-106">介绍如何创建和使用引用类型变量。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-106">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="ee8bf-107">您可以使用引用类型变量来允许函数更改传递给它的变量的值。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-107">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="ee8bf-108">长说明</span><span class="sxs-lookup"><span data-stu-id="ee8bf-108">Long description</span></span>

<span data-ttu-id="ee8bf-109">可以 *通过引用* 或 *值* 将变量传递给函数。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-109">You can pass variables to functions *by reference* or *by value*.</span></span>

<span data-ttu-id="ee8bf-110">*通过值* 传递变量时，将传递数据的副本。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-110">When you pass a variable *by value*, you are passing a copy of the data.</span></span>

<span data-ttu-id="ee8bf-111">在下面的示例中，函数更改传递给它的变量的值。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-111">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="ee8bf-112">在 PowerShell 中，整数是值类型，因此按值传递它们。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-112">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="ee8bf-113">因此，的值在 `$var` 函数作用域之外保持不变。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-113">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="ee8bf-114">在下面的示例中，将包含的变量 `Hashtable` 传递到函数。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-114">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="ee8bf-115">`Hashtable` 对象类型，因此默认情况下，它 *通过引用* 传递给函数。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-115">`Hashtable` is an object type so by default it is passed to the function *by reference*.</span></span>

<span data-ttu-id="ee8bf-116">当 *通过引用* 传递变量时，函数可以更改数据，并且更改会在函数执行后保持不变。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-116">When passing a variable *by reference*, the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="ee8bf-117">函数添加新的键/值对，它保留在函数范围之外。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-117">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="ee8bf-118">编写函数以接受引用参数</span><span class="sxs-lookup"><span data-stu-id="ee8bf-118">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="ee8bf-119">无论传递的数据类型如何，都可以将函数编码为采用参数作为参考。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-119">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="ee8bf-120">这需要将参数类型指定为 `System.Management.Automation.PSReference` 或 `[ref]` 。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-120">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="ee8bf-121">使用引用时，必须使用类型的 `Value` 属性 `System.Management.Automation.PSReference` 来访问数据。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-121">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="ee8bf-122">若要将变量传递给需要引用的参数，必须键入 cast 作为引用。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-122">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="ee8bf-123">需要括号和括号。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-123">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="ee8bf-124">向 .NET 方法传递引用</span><span class="sxs-lookup"><span data-stu-id="ee8bf-124">Passing references to .NET methods</span></span>

<span data-ttu-id="ee8bf-125">某些 .NET 方法可能要求您将变量作为引用传递。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-125">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="ee8bf-126">当方法的定义在 `in` 参数上使用关键字、 `out` 或时 `ref` ，它需要引用。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-126">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="ee8bf-127">此 `TryParse` 方法尝试将字符串分析为一个整数。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-127">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="ee8bf-128">如果该方法成功，则返回 `$true` ，并将结果存储在 **通过引用** 传递的变量中。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-128">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference**.</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="ee8bf-129">引用和范围</span><span class="sxs-lookup"><span data-stu-id="ee8bf-129">References and scopes</span></span>

<span data-ttu-id="ee8bf-130">引用允许在子作用域内更改父作用域中的变量的值。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-130">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="ee8bf-131">仅更改了引用类型的变量。</span><span class="sxs-lookup"><span data-stu-id="ee8bf-131">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee8bf-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee8bf-132">See also</span></span>

[<span data-ttu-id="ee8bf-133">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8bf-133">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="ee8bf-134">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="ee8bf-134">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="ee8bf-135">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ee8bf-135">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="ee8bf-136">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="ee8bf-136">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="ee8bf-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="ee8bf-137">about_Scopes</span></span>](about_scopes.md)

