---
description: 描述使用 Microsoft .NET 类型的运算符。
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 66687a2282cfd321146888daad92fef40ef6cb0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598079"
---
# <a name="about-type-operators"></a><span data-ttu-id="4f24d-103">关于类型运算符</span><span class="sxs-lookup"><span data-stu-id="4f24d-103">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="4f24d-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="4f24d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="4f24d-105">描述使用 Microsoft .NET 类型的运算符。</span><span class="sxs-lookup"><span data-stu-id="4f24d-105">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="4f24d-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="4f24d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="4f24d-107">布尔类型运算符 (`-is` 和 `-isNot`) 指示对象是否为指定 .net 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="4f24d-107">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="4f24d-108">`-is`如果类型匹配并且值为 FALSE，则运算符返回 **TRUE** ; 否则返回 **FALSE** 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-108">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="4f24d-109">`-isNot`如果类型匹配并且值为 **TRUE** ，则运算符将返回值 **FALSE** 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-109">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="4f24d-110">`-as`运算符尝试将输入对象转换为指定的 .net 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-110">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="4f24d-111">如果成功，则返回转换后的对象。</span><span class="sxs-lookup"><span data-stu-id="4f24d-111">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="4f24d-112">如果失败，则返回 `$null`。</span><span class="sxs-lookup"><span data-stu-id="4f24d-112">If it fails, it returns `$null`.</span></span> <span data-ttu-id="4f24d-113">它不会返回错误。</span><span class="sxs-lookup"><span data-stu-id="4f24d-113">It does not return an error.</span></span>

<span data-ttu-id="4f24d-114">下表列出了 PowerShell 中的类型运算符。</span><span class="sxs-lookup"><span data-stu-id="4f24d-114">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="4f24d-115">操作员</span><span class="sxs-lookup"><span data-stu-id="4f24d-115">Operator</span></span>|<span data-ttu-id="4f24d-116">说明</span><span class="sxs-lookup"><span data-stu-id="4f24d-116">Description</span></span>                |<span data-ttu-id="4f24d-117">示例</span><span class="sxs-lookup"><span data-stu-id="4f24d-117">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="4f24d-118">当输入</span><span class="sxs-lookup"><span data-stu-id="4f24d-118">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="4f24d-119">是的一个实例。</span><span class="sxs-lookup"><span data-stu-id="4f24d-119">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="4f24d-120">指定的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-120">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="4f24d-121">当输入</span><span class="sxs-lookup"><span data-stu-id="4f24d-121">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="4f24d-122">不是的实例</span><span class="sxs-lookup"><span data-stu-id="4f24d-122">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="4f24d-123">specified.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-123">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="4f24d-124">将输入转换为</span><span class="sxs-lookup"><span data-stu-id="4f24d-124">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="4f24d-125">指定的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-125">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="4f24d-126">类型运算符的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f24d-126">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="4f24d-127">你还可以使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4f24d-127">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="4f24d-128">.NET 类型可以在括号中编写为类型名称，也可以作为字符串写入，如 `[DateTime]` 或 `"DateTime"` 。 </span><span class="sxs-lookup"><span data-stu-id="4f24d-128">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime**.</span></span> <span data-ttu-id="4f24d-129">如果类型不在 system 命名空间的根中，则指定该对象类型的完整名称。</span><span class="sxs-lookup"><span data-stu-id="4f24d-129">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="4f24d-130">您可以省略 "System."。</span><span class="sxs-lookup"><span data-stu-id="4f24d-130">You can omit "System.".</span></span> <span data-ttu-id="4f24d-131">例如，若 **要指定 system.exception，请输入** `[System.Diagnostics.Process]` 、 `[Diagnostics.Process]` 或 `"Diagnostics.Process"` 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-131">For example, to specify **System.Diagnostics.Process**, enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="4f24d-132">类型运算符始终作为一个整体对输入对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="4f24d-132">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="4f24d-133">也就是说，如果输入对象是集合，则它是所测试的 _集合_ 类型，而不是集合的 _元素_ 的类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-133">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_.</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="4f24d-134">-is/isNot 运算符</span><span class="sxs-lookup"><span data-stu-id="4f24d-134">-is/isNot operators</span></span>

<span data-ttu-id="4f24d-135">**布尔** 类型运算符 (`-is` 和 `-isNot`) 总是返回一个 **布尔** 值，即使输入是对象的集合。</span><span class="sxs-lookup"><span data-stu-id="4f24d-135">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="4f24d-136">如果 `<input>` 是与 .Net 类型相同或 _派生_ 自 .net 类型的类型，则 `-is` 运算符返回 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-136">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="4f24d-137">例如， **DirectoryInfo** 类型派生自 **FileSystemInfo** 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-137">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="4f24d-138">因此，这两个示例都返回 **True**。</span><span class="sxs-lookup"><span data-stu-id="4f24d-138">Therefore, both of these examples return **True**.</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="4f24d-139">`-is`如果在 `<input>` 比较中实现了接口，则运算符还可以匹配接口。</span><span class="sxs-lookup"><span data-stu-id="4f24d-139">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="4f24d-140">在此示例中，输入是一个数组。</span><span class="sxs-lookup"><span data-stu-id="4f24d-140">In this example, the input is an array.</span></span> <span data-ttu-id="4f24d-141">数组实现了 **system.object** 接口。</span><span class="sxs-lookup"><span data-stu-id="4f24d-141">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="4f24d-142">-as 运算符</span><span class="sxs-lookup"><span data-stu-id="4f24d-142">-as operator</span></span>

<span data-ttu-id="4f24d-143">`-as`运算符尝试将输入对象转换为指定的 .net 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-143">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="4f24d-144">如果成功，则返回转换后的对象。</span><span class="sxs-lookup"><span data-stu-id="4f24d-144">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="4f24d-145">如果失败，它将返回 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-145">It if fails, it returns `$null`.</span></span> <span data-ttu-id="4f24d-146">它不会返回错误。</span><span class="sxs-lookup"><span data-stu-id="4f24d-146">It does not return an error.</span></span>

<span data-ttu-id="4f24d-147">如果 `<input>` 是 _派生_ 自 .net 类型的类型，则 `-as` _通过_ 返回的输入对象保持不变。</span><span class="sxs-lookup"><span data-stu-id="4f24d-147">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="4f24d-148">例如， **DirectoryInfo** 类型派生自 **FileSystemInfo** 类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-148">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="4f24d-149">因此，在以下示例中，对象类型保持不变：</span><span class="sxs-lookup"><span data-stu-id="4f24d-149">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="4f24d-150">转换 DateTime 类型区分区域性</span><span class="sxs-lookup"><span data-stu-id="4f24d-150">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="4f24d-151">与类型强制转换不同， `[DateTime]` 使用运算符转换为类型 `-as` 仅适用于根据当前区域性的规则进行格式设置的字符串。</span><span class="sxs-lookup"><span data-stu-id="4f24d-151">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

<span data-ttu-id="4f24d-152">若要查找对象的 .NET 类型，请使用 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f24d-152">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="4f24d-153">或者，将所有对象的 **GetType** 方法与此方法的 **FullName** 属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="4f24d-153">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="4f24d-154">例如，下面的语句获取命令的返回值的类型 `Get-Culture` ：</span><span class="sxs-lookup"><span data-stu-id="4f24d-154">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="4f24d-155">示例</span><span class="sxs-lookup"><span data-stu-id="4f24d-155">EXAMPLES</span></span>

<span data-ttu-id="4f24d-156">下面的示例演示类型运算符的一些用法：</span><span class="sxs-lookup"><span data-stu-id="4f24d-156">The following examples show some uses of the Type operators:</span></span>

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

<span data-ttu-id="4f24d-157">下面的示例演示当输入为对象的集合时，匹配类型为集合的 .NET 类型，而不是集合中各个对象的类型。</span><span class="sxs-lookup"><span data-stu-id="4f24d-157">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="4f24d-158">在此示例中，尽管 `Get-Culture` 和 `Get-UICulture` cmdlet 都返回 **system.object** 对象，但这些对象的集合是一个 system.object 数组。</span><span class="sxs-lookup"><span data-stu-id="4f24d-158">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

<span data-ttu-id="4f24d-159">下面的示例演示如何使用 `-as` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4f24d-159">The following examples show how to use the `-as` operator.</span></span>

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

<span data-ttu-id="4f24d-160">下面的示例演示当 `-as` 运算符不能将输入对象转换为 .net 类型时，它将返回 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="4f24d-160">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="4f24d-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f24d-161">SEE ALSO</span></span>

[<span data-ttu-id="4f24d-162">about_Operators</span><span class="sxs-lookup"><span data-stu-id="4f24d-162">about_Operators</span></span>](about_Operators.md)
