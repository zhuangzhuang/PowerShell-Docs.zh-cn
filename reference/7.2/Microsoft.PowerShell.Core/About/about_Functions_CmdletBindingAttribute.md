---
description: 描述使函数的工作方式与已编译的 cmdlet 相同的特性。
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: f1463bafc462ae2a266f5b1f6f4d71e3422f5831
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596656"
---
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="bd6e9-103">关于函数 CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="bd6e9-103">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="bd6e9-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="bd6e9-104">Short description</span></span>
<span data-ttu-id="bd6e9-105">描述使函数的工作方式与已编译的 cmdlet 相同的特性。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-105">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="bd6e9-106">长说明</span><span class="sxs-lookup"><span data-stu-id="bd6e9-106">Long description</span></span>

<span data-ttu-id="bd6e9-107">`CmdletBinding`特性是使它们运行的函数的特性，如用 c # 编写的编译 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-107">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="bd6e9-108">它提供对 cmdlet 功能的访问权限。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-108">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="bd6e9-109">PowerShell 绑定具有属性的函数的参数， `CmdletBinding` 其方式与绑定编译 cmdlet 的参数的方式相同。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-109">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="bd6e9-110">`$PSCmdlet`自动变量可用于具有属性的函数 `CmdletBinding` ，但该变量不可用 `$Args` 。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-110">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="bd6e9-111">在具有属性的函数中 `CmdletBinding` ，未知参数和没有匹配位置参数的位置参数会导致参数绑定失败。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-111">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="bd6e9-112">已编译的 cmdlet 使用所需的 `Cmdlet` 属性，该属性类似于 `CmdletBinding` 本主题中描述的属性。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-112">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd6e9-113">语法</span><span class="sxs-lookup"><span data-stu-id="bd6e9-113">Syntax</span></span>

<span data-ttu-id="bd6e9-114">下面的示例演示了一个函数的格式，该函数指定属性的所有可选参数 `CmdletBinding` 。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-114">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="bd6e9-115">此示例的后面是每个参数的简要说明。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-115">A brief description of each argument follows this example.</span></span>

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a><span data-ttu-id="bd6e9-116">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="bd6e9-116">ConfirmImpact</span></span>

<span data-ttu-id="bd6e9-117">**ConfirmImpact** 参数指定通过调用 **ShouldProcess** 方法来确认函数的操作的时间。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-117">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="bd6e9-118">仅当 **ConfirmImpact** 参数等于或大于首选项变量的值时，对 **ShouldProcess** 方法的调用才会显示确认提示 `$ConfirmPreference` 。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-118">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="bd6e9-119"> (自变量的默认值为 **Medium**。 ) 仅在指定了 **SupportsShouldProcess** 参数时才指定此参数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-119">(The default value of the argument is **Medium**.) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="bd6e9-120">有关确认请求的详细信息，请参阅 [请求确认](/powershell/scripting/developer/cmdlet/requesting-confirmation)。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-120">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="bd6e9-121">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="bd6e9-121">DefaultParameterSetName</span></span>

<span data-ttu-id="bd6e9-122">**DefaultParameterSetName** 参数指定 PowerShell 在无法确定要使用哪个参数时将尝试使用的参数集的名称。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-122">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="bd6e9-123">可以通过使每个参数的唯一参数设置一个必需的参数来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-123">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="bd6e9-124">HelpURI</span><span class="sxs-lookup"><span data-stu-id="bd6e9-124">HelpURI</span></span>

<span data-ttu-id="bd6e9-125">**HelpURI** 参数指定描述该函数的帮助主题的联机版本的 internet 地址。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-125">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="bd6e9-126">**HelpURI** 参数的值必须以 "http" 或 "https" 开头。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-126">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="bd6e9-127">**HelpURI** 参数值用于为函数返回的 **CommandInfo** 对象的 **HelpURI** 属性的值 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-127">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="bd6e9-128">但是，当在计算机上安装了帮助文件，并且帮助文件的 **RelatedLinks** 部分中第一个链接的值为 uri，或基于注释的帮助中的第一个指令的值为 `.Link` uri 时，帮助文件中的 uri 将用作函数的 **HelpUri** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-128">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="bd6e9-129">`Get-Help`当命令中指定的 **联机** 参数时，该 Cmdlet 将使用 **HelpURI** 属性的值查找函数帮助主题的联机版本 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-129">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="bd6e9-130">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="bd6e9-130">SupportsPaging</span></span>

<span data-ttu-id="bd6e9-131">**SupportsPaging** 参数将 **第一个**、 **Skip** 和 **IncludeTotalCount** 参数添加到函数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-131">The **SupportsPaging** argument adds the **First**, **Skip**, and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="bd6e9-132">用户可以使用这些参数选择非常大的结果集的输出。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-132">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="bd6e9-133">此参数适用于从支持数据选择的大型数据存储（如 SQL 数据库）中返回数据的 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-133">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="bd6e9-134">此参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-134">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="bd6e9-135">**First**：仅获取前 "n" 个对象。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-135">**First**: Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="bd6e9-136">**Skip**：忽略第一个 "n" 对象，然后获取剩余的对象。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-136">**Skip**:  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="bd6e9-137">**IncludeTotalCount**：报告数据集中的对象数 (整数) 后接对象。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-137">**IncludeTotalCount**: Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="bd6e9-138">如果 cmdlet 无法确定总计数，它将返回 "未知总数"。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-138">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="bd6e9-139">PowerShell 包含 **NewTotalCount**，这是一个帮助器方法，用于获取要返回的总计数值并包含总计值的准确性。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-139">PowerShell includes **NewTotalCount**, a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="bd6e9-140">下面的示例函数演示如何向高级函数添加对分页参数的支持。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-140">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="bd6e9-141">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="bd6e9-141">SupportsShouldProcess</span></span>

<span data-ttu-id="bd6e9-142">**SupportsShouldProcess** 参数将 **Confirm** 和 **WhatIf** 参数添加到函数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-142">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="bd6e9-143">**Confirm** 参数会提示用户，然后在管道中的每个对象上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-143">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="bd6e9-144">**WhatIf** 参数会列出命令所进行的更改，而不是运行命令。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-144">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="bd6e9-145">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="bd6e9-145">PositionalBinding</span></span>

<span data-ttu-id="bd6e9-146">**PositionalBinding** 参数确定函数中的参数在默认情况下是否是位置。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-146">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="bd6e9-147">默认值是 `$True`。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-147">The default value is `$True`.</span></span> <span data-ttu-id="bd6e9-148">可以使用值为的 **PositionalBinding** 参数 `$False` 禁用位置绑定。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-148">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="bd6e9-149">**PositionalBinding** 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-149">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="bd6e9-150">如果参数是位置参数，则参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-150">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="bd6e9-151">根据函数命令中未命名参数值的顺序或位置，PowerShell 将未命名的参数值与函数参数关联。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-151">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="bd6e9-152">如果参数不是位置 (它们分别为 "命名" ) ，则在命令中需要参数名称 (或名称) 的缩写或别名。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-152">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="bd6e9-153">如果 **PositionalBinding** 为 `$True` ，则默认情况下函数参数是位置。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-153">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="bd6e9-154">PowerShell 将位置编号按其在函数中的声明顺序分配给参数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-154">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="bd6e9-155">当 **PositionalBinding** 为时 `$False` ，默认情况下函数参数不是位置。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-155">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="bd6e9-156">除非在参数上声明 **参数** 特性的 **Position** 参数，否则在函数中使用参数时，参数名称 (或别名或缩写) 必须包括在内。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-156">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="bd6e9-157">**参数** 特性的 **Position** 参数优先于 **PositionalBinding** 默认值。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-157">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="bd6e9-158">您可以使用 **position** 参数来指定参数的位置值。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-158">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="bd6e9-159">有关 **Position** 参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-159">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="bd6e9-160">说明</span><span class="sxs-lookup"><span data-stu-id="bd6e9-160">Notes</span></span>

<span data-ttu-id="bd6e9-161">高级函数中不支持 **SupportsTransactions** 参数。</span><span class="sxs-lookup"><span data-stu-id="bd6e9-161">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="bd6e9-162">关键字</span><span class="sxs-lookup"><span data-stu-id="bd6e9-162">Keywords</span></span>

<span data-ttu-id="bd6e9-163">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="bd6e9-163">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="bd6e9-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="bd6e9-164">See also</span></span>

[<span data-ttu-id="bd6e9-165">about_Functions</span><span class="sxs-lookup"><span data-stu-id="bd6e9-165">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="bd6e9-166">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="bd6e9-166">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="bd6e9-167">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="bd6e9-167">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="bd6e9-168">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="bd6e9-168">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="bd6e9-169">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="bd6e9-169">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
