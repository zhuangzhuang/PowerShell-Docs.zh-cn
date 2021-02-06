---
description: 介绍如何在 PowerShell 中创建和使用函数。
Locale: en-US
ms.date: 02/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: d51c4d0bbf728bb23b4a5452d5192a262b722758
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595412"
---
# <a name="about-functions"></a><span data-ttu-id="93a04-103">关于 Functions</span><span class="sxs-lookup"><span data-stu-id="93a04-103">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="93a04-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="93a04-104">Short description</span></span>

<span data-ttu-id="93a04-105">介绍如何在 PowerShell 中创建和使用函数。</span><span class="sxs-lookup"><span data-stu-id="93a04-105">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="93a04-106">长说明</span><span class="sxs-lookup"><span data-stu-id="93a04-106">Long description</span></span>

<span data-ttu-id="93a04-107">函数是包含您分配的名称的 PowerShell 语句的列表。</span><span class="sxs-lookup"><span data-stu-id="93a04-107">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="93a04-108">运行函数时，请键入函数名称。</span><span class="sxs-lookup"><span data-stu-id="93a04-108">When you run a function, you type the function name.</span></span> <span data-ttu-id="93a04-109">如果在命令提示符下键入语句，则列表中的语句将运行。</span><span class="sxs-lookup"><span data-stu-id="93a04-109">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="93a04-110">函数可以非常简单，如下所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-110">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="93a04-111">函数也可以作为 cmdlet 或应用程序的复杂性。</span><span class="sxs-lookup"><span data-stu-id="93a04-111">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="93a04-112">与 cmdlet 一样，函数也可以具有参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-112">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="93a04-113">参数可以是命名的、位置的、开关或动态参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-113">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="93a04-114">函数参数可以从命令行或从管道中读取。</span><span class="sxs-lookup"><span data-stu-id="93a04-114">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="93a04-115">函数可以返回可以显示、赋给变量或传递给其他函数或 cmdlet 的值。</span><span class="sxs-lookup"><span data-stu-id="93a04-115">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="93a04-116">你还可以使用关键字指定返回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-116">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="93a04-117">`return`关键字不会影响或禁止从函数返回的其他输出。</span><span class="sxs-lookup"><span data-stu-id="93a04-117">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="93a04-118">不过， `return` 关键字将退出该函数。</span><span class="sxs-lookup"><span data-stu-id="93a04-118">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="93a04-119">有关详细信息，请参阅 [about_Return](about_Return.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-119">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="93a04-120">函数的语句列表可以包含具有关键字、和的不同类型的语句 `Begin` 列表 `Process` `End` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-120">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="93a04-121">这些语句以不同方式列出管道中的处理输入。</span><span class="sxs-lookup"><span data-stu-id="93a04-121">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="93a04-122">筛选器是一种使用关键字的特殊函数 `Filter` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-122">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="93a04-123">函数也可以像 cmdlet 一样操作。</span><span class="sxs-lookup"><span data-stu-id="93a04-123">Functions can also act like cmdlets.</span></span> <span data-ttu-id="93a04-124">你可以创建一个函数，该函数的工作方式与 cmdlet 相同，无需使用 `C#` 编程。</span><span class="sxs-lookup"><span data-stu-id="93a04-124">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="93a04-125">有关详细信息，请参阅 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-125">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="93a04-126">语法</span><span class="sxs-lookup"><span data-stu-id="93a04-126">Syntax</span></span>

<span data-ttu-id="93a04-127">下面是函数的语法：</span><span class="sxs-lookup"><span data-stu-id="93a04-127">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="93a04-128">函数包含以下项：</span><span class="sxs-lookup"><span data-stu-id="93a04-128">A function includes the following items:</span></span>

- <span data-ttu-id="93a04-129">`Function`关键字</span><span class="sxs-lookup"><span data-stu-id="93a04-129">A `Function` keyword</span></span>
- <span data-ttu-id="93a04-130">范围 (可选) </span><span class="sxs-lookup"><span data-stu-id="93a04-130">A scope (optional)</span></span>
- <span data-ttu-id="93a04-131">你选择的名称</span><span class="sxs-lookup"><span data-stu-id="93a04-131">A name that you select</span></span>
- <span data-ttu-id="93a04-132">任意数量的命名参数 (可选) </span><span class="sxs-lookup"><span data-stu-id="93a04-132">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="93a04-133">括在大括号中的一个或多个 PowerShell 命令 `{}`</span><span class="sxs-lookup"><span data-stu-id="93a04-133">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="93a04-134">有关 `Dynamicparam` 函数中关键字和动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-134">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="93a04-135">简单函数</span><span class="sxs-lookup"><span data-stu-id="93a04-135">Simple Functions</span></span>

<span data-ttu-id="93a04-136">函数不必太复杂，很有用。</span><span class="sxs-lookup"><span data-stu-id="93a04-136">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="93a04-137">最简单的函数具有以下格式：</span><span class="sxs-lookup"><span data-stu-id="93a04-137">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="93a04-138">例如，以下函数通过 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93a04-138">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="93a04-139">若要使用函数，请键入： `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="93a04-139">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="93a04-140">若要向函数添加语句，请在单独的行中键入每个语句，或使用分号 `;` 分隔这些语句。</span><span class="sxs-lookup"><span data-stu-id="93a04-140">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="93a04-141">例如，以下函数将查找在 `.jpg` 开始日期之后更改的当前用户目录中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="93a04-141">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="93a04-142">您可以创建有用的小型函数的工具箱。</span><span class="sxs-lookup"><span data-stu-id="93a04-142">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="93a04-143">将这些函数添加到 PowerShell 配置文件，如本主题 [about_Profiles](about_Profiles.md) 和后面所述。</span><span class="sxs-lookup"><span data-stu-id="93a04-143">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="93a04-144">函数名称</span><span class="sxs-lookup"><span data-stu-id="93a04-144">Function Names</span></span>

<span data-ttu-id="93a04-145">可以为函数分配任何名称，但与其他人共享的函数应遵循为所有 PowerShell 命令建立的命名规则。</span><span class="sxs-lookup"><span data-stu-id="93a04-145">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="93a04-146">函数名称应包含动词-名词对，其中谓词标识函数执行的操作，名词标识该 cmdlet 执行其操作的项。</span><span class="sxs-lookup"><span data-stu-id="93a04-146">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="93a04-147">函数应使用已为所有 PowerShell 命令批准的标准谓词。</span><span class="sxs-lookup"><span data-stu-id="93a04-147">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="93a04-148">这些谓词可帮助我们使命令名称变得简单、一致和易于理解。</span><span class="sxs-lookup"><span data-stu-id="93a04-148">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="93a04-149">有关标准 PowerShell 谓词的详细信息，请参阅 Microsoft Docs 中的 [批准的动词](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 。</span><span class="sxs-lookup"><span data-stu-id="93a04-149">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="93a04-150">带参数的函数</span><span class="sxs-lookup"><span data-stu-id="93a04-150">Functions with Parameters</span></span>

<span data-ttu-id="93a04-151">可以将参数用于函数，包括命名参数、位置参数、开关参数和动态参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-151">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="93a04-152">有关函数中的动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-152">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="93a04-153">命名的参数</span><span class="sxs-lookup"><span data-stu-id="93a04-153">Named Parameters</span></span>

<span data-ttu-id="93a04-154">可以定义任意数量的命名参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-154">You can define any number of named parameters.</span></span> <span data-ttu-id="93a04-155">可以包含命名参数的默认值，如本主题后面所述。</span><span class="sxs-lookup"><span data-stu-id="93a04-155">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="93a04-156">可以使用关键字在大括号内定义参数 `Param` ，如下面的示例语法所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-156">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="93a04-157">你还可以在不带关键字的大括号外定义参数 `Param` ，如下面的示例语法所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-157">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="93a04-158">下面是此替代语法的示例。</span><span class="sxs-lookup"><span data-stu-id="93a04-158">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="93a04-159">尽管第一种方法是首选方法，但这两种方法之间没有区别。</span><span class="sxs-lookup"><span data-stu-id="93a04-159">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="93a04-160">运行函数时，为参数提供的值将分配给包含参数名的变量。</span><span class="sxs-lookup"><span data-stu-id="93a04-160">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="93a04-161">可在函数中使用该变量的值。</span><span class="sxs-lookup"><span data-stu-id="93a04-161">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="93a04-162">下面的示例是一个名为的函数 `Get-SmallFiles` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-162">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="93a04-163">此函数有一个 `$Size` 参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-163">This function has a `$Size` parameter.</span></span> <span data-ttu-id="93a04-164">函数显示小于参数值的所有文件 `$Size` ，并排除目录：</span><span class="sxs-lookup"><span data-stu-id="93a04-164">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="93a04-165">在函数中，可以使用 `$Size` 变量，该变量是为参数定义的名称。</span><span class="sxs-lookup"><span data-stu-id="93a04-165">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="93a04-166">若要使用此函数，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="93a04-166">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="93a04-167">你还可以在没有参数名称的情况下为命名参数输入值。</span><span class="sxs-lookup"><span data-stu-id="93a04-167">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="93a04-168">例如，以下命令提供的结果与为 **Size** 参数命名的命令相同：</span><span class="sxs-lookup"><span data-stu-id="93a04-168">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="93a04-169">若要定义参数的默认值，请在参数名称后面键入一个等号和值，如下面的示例中所示 `Get-SmallFiles` ：</span><span class="sxs-lookup"><span data-stu-id="93a04-169">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="93a04-170">如果键入的 `Get-SmallFiles` 值不包含任何值，则函数会将100赋给 `$size` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-170">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="93a04-171">如果提供值，该函数将使用该值。</span><span class="sxs-lookup"><span data-stu-id="93a04-171">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="93a04-172">或者，您可以通过将 **PSDefaultValue** 特性添加到参数说明，并指定 **PSDefaultValue** 的 **help** 属性，来提供描述参数的默认值的简短帮助字符串。</span><span class="sxs-lookup"><span data-stu-id="93a04-172">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="93a04-173">若要提供描述函数中 **Size** 参数 (100) 默认值的帮助字符串 `Get-SmallFiles` ，请添加 **PSDefaultValue** 属性，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="93a04-173">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="93a04-174">有关 **PSDefaultValue** 特性类的详细信息，请参阅 [PSDefaultValue 特性成员](/dotnet/api/system.management.automation.psdefaultvalueattribute)。</span><span class="sxs-lookup"><span data-stu-id="93a04-174">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="93a04-175">位置参数</span><span class="sxs-lookup"><span data-stu-id="93a04-175">Positional Parameters</span></span>

<span data-ttu-id="93a04-176">位置参数是没有参数名称的参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-176">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="93a04-177">PowerShell 使用参数值顺序将每个参数值与函数中的参数相关联。</span><span class="sxs-lookup"><span data-stu-id="93a04-177">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="93a04-178">使用位置参数时，请在函数名称后面键入一个或多个值。</span><span class="sxs-lookup"><span data-stu-id="93a04-178">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="93a04-179">位置参数值将分配给 `$args` 数组变量。</span><span class="sxs-lookup"><span data-stu-id="93a04-179">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="93a04-180">函数名称后面的值将分配给数组中的第一个位置 `$args` `$args[0]` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-180">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="93a04-181">以下 `Get-Extension` 函数将 `.txt` 文件扩展名添加到提供的文件名：</span><span class="sxs-lookup"><span data-stu-id="93a04-181">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="93a04-182">开关参数</span><span class="sxs-lookup"><span data-stu-id="93a04-182">Switch Parameters</span></span>

<span data-ttu-id="93a04-183">开关是不需要值的参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-183">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="93a04-184">而是键入函数名称，后跟开关参数的名称。</span><span class="sxs-lookup"><span data-stu-id="93a04-184">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="93a04-185">若要定义开关参数，请在 `[switch]` 参数名称前面指定类型，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-185">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="93a04-186">在 `On` 函数名后键入 switch 参数时，该函数将显示 "开关 on"。</span><span class="sxs-lookup"><span data-stu-id="93a04-186">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="93a04-187">如果没有开关参数，它将显示 "切换为关闭"。</span><span class="sxs-lookup"><span data-stu-id="93a04-187">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="93a04-188">你还可以在运行函数时向开关分配一个 **布尔** 值，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-188">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="93a04-189">使用展开表示命令参数</span><span class="sxs-lookup"><span data-stu-id="93a04-189">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="93a04-190">可以使用展开来表示命令的参数。</span><span class="sxs-lookup"><span data-stu-id="93a04-190">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="93a04-191">此功能是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93a04-191">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="93a04-192">在调用会话中的命令的函数中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="93a04-192">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="93a04-193">不需要声明或枚举命令参数，也不需要在命令参数更改时更改函数。</span><span class="sxs-lookup"><span data-stu-id="93a04-193">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="93a04-194">下面的示例函数调用 `Get-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93a04-194">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="93a04-195">命令使用 `@Args` 来表示的参数 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-195">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="93a04-196">调用函数时，可以使用的所有参数 `Get-Command` `Get-MyCommand` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-196">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="93a04-197">参数和参数值使用传递到命令 `@Args` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-197">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="93a04-198">此 `@Args` 功能使用 `$Args` 自动参数，该参数表示未声明的 cmdlet 参数和来自剩余参数的值。</span><span class="sxs-lookup"><span data-stu-id="93a04-198">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="93a04-199">有关展开的详细信息，请参阅 [about_Splatting](about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-199">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="93a04-200">管道对象到函数</span><span class="sxs-lookup"><span data-stu-id="93a04-200">Piping Objects to Functions</span></span>

<span data-ttu-id="93a04-201">任何函数都可以从管道中获取输入。</span><span class="sxs-lookup"><span data-stu-id="93a04-201">Any function can take input from the pipeline.</span></span> <span data-ttu-id="93a04-202">您可以使用 `Begin` 、和关键字控制函数处理管道输入的方式 `Process` `End` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-202">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="93a04-203">下面的语法示例显示了三个关键字：</span><span class="sxs-lookup"><span data-stu-id="93a04-203">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="93a04-204">`Begin`语句列表仅在函数的开始处运行一次。</span><span class="sxs-lookup"><span data-stu-id="93a04-204">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93a04-205">如果函数定义了 `Begin` `Process` 或 `End` 块，则所有代码必须位于这些块内。</span><span class="sxs-lookup"><span data-stu-id="93a04-205">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="93a04-206">如果定义了任何块，则不会在块之外识别 *任何* 代码。</span><span class="sxs-lookup"><span data-stu-id="93a04-206">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="93a04-207">`Process`语句列表对管道中的每个对象运行一次。</span><span class="sxs-lookup"><span data-stu-id="93a04-207">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="93a04-208">当 `Process` 块正在运行时，每个管道对象将分配给 `$_` 自动变量，一次分配一个管道对象。</span><span class="sxs-lookup"><span data-stu-id="93a04-208">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="93a04-209">函数收到管道中的所有对象后， `End` 语句列表将运行一次。</span><span class="sxs-lookup"><span data-stu-id="93a04-209">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="93a04-210">如果未 `Begin` `Process` 使用、或 `End` 关键字，则将所有语句视为 `End` 语句列表。</span><span class="sxs-lookup"><span data-stu-id="93a04-210">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="93a04-211">下面的函数使用 `Process` 关键字。</span><span class="sxs-lookup"><span data-stu-id="93a04-211">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="93a04-212">函数显示管道中的示例：</span><span class="sxs-lookup"><span data-stu-id="93a04-212">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="93a04-213">若要演示此函数，请输入用逗号分隔的数字列表，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-213">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="93a04-214">在管道中使用函数时，将向该函数传递的对象将分配给 `$input` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="93a04-214">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="93a04-215">函数在任何对象来自管道之前，运行带有关键字的语句 `Begin` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-215">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="93a04-216">函数在 `End` 从管道接收到所有对象之后，使用关键字运行语句。</span><span class="sxs-lookup"><span data-stu-id="93a04-216">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="93a04-217">下面的示例演示 `$input` 带有 and 关键字的自动变量 `Begin` `End` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-217">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="93a04-218">如果使用管道运行此函数，则将显示以下结果：</span><span class="sxs-lookup"><span data-stu-id="93a04-218">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="93a04-219">当 `Begin` 语句运行时，该函数不具有管道的输入。</span><span class="sxs-lookup"><span data-stu-id="93a04-219">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="93a04-220">`End`语句在函数具有值后运行。</span><span class="sxs-lookup"><span data-stu-id="93a04-220">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="93a04-221">如果函数具有 `Process` 关键字，则中的每个对象 `$input` 都将从中移除 `$input` 并被分配给 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-221">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="93a04-222">下面的示例包含一个 `Process` 语句列表：</span><span class="sxs-lookup"><span data-stu-id="93a04-222">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="93a04-223">在此示例中，向函数发出管道的每个对象都发送到 `Process` 语句列表。</span><span class="sxs-lookup"><span data-stu-id="93a04-223">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="93a04-224">`Process`语句在每个对象上运行（一次一个对象）。</span><span class="sxs-lookup"><span data-stu-id="93a04-224">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="93a04-225">`$input`当函数到达关键字时，自动变量为空 `End` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-225">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="93a04-226">有关详细信息，请参阅[使用枚举](about_Automatic_Variables.md#using-enumerators)器</span><span class="sxs-lookup"><span data-stu-id="93a04-226">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="93a04-227">筛选器</span><span class="sxs-lookup"><span data-stu-id="93a04-227">Filters</span></span>

<span data-ttu-id="93a04-228">筛选器是在管道中的每个对象上运行的函数类型。</span><span class="sxs-lookup"><span data-stu-id="93a04-228">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="93a04-229">筛选器类似于函数，其中的所有语句都位于 `Process` 块中。</span><span class="sxs-lookup"><span data-stu-id="93a04-229">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="93a04-230">筛选器的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="93a04-230">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="93a04-231">以下筛选器从管道中获取日志条目，然后显示整个条目或仅显示条目的消息部分：</span><span class="sxs-lookup"><span data-stu-id="93a04-231">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="93a04-232">函数范围</span><span class="sxs-lookup"><span data-stu-id="93a04-232">Function Scope</span></span>

<span data-ttu-id="93a04-233">函数存在于创建它的作用域中。</span><span class="sxs-lookup"><span data-stu-id="93a04-233">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="93a04-234">如果函数是脚本的一部分，则该函数可用于该脚本中的语句。</span><span class="sxs-lookup"><span data-stu-id="93a04-234">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="93a04-235">默认情况下，在命令提示符下不能使用脚本中的函数。</span><span class="sxs-lookup"><span data-stu-id="93a04-235">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="93a04-236">可以指定函数的作用域。</span><span class="sxs-lookup"><span data-stu-id="93a04-236">You can specify the scope of a function.</span></span> <span data-ttu-id="93a04-237">例如，在以下示例中，将函数添加到全局范围：</span><span class="sxs-lookup"><span data-stu-id="93a04-237">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="93a04-238">当函数在全局范围中时，可以在脚本中、在函数中使用函数，并在命令行中使用函数。</span><span class="sxs-lookup"><span data-stu-id="93a04-238">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="93a04-239">函数通常会创建一个作用域。</span><span class="sxs-lookup"><span data-stu-id="93a04-239">Functions normally create a scope.</span></span> <span data-ttu-id="93a04-240">在函数中创建的项（如变量）仅存在于函数作用域中。</span><span class="sxs-lookup"><span data-stu-id="93a04-240">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="93a04-241">有关 PowerShell 中的作用域的详细信息，请参阅 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-241">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="93a04-242">使用函数查找和管理函数：驱动器</span><span class="sxs-lookup"><span data-stu-id="93a04-242">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="93a04-243">PowerShell 中的所有函数和筛选器都将自动存储在 `Function:` 驱动器中。</span><span class="sxs-lookup"><span data-stu-id="93a04-243">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="93a04-244">此驱动器由 PowerShell **函数** 提供程序公开。</span><span class="sxs-lookup"><span data-stu-id="93a04-244">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="93a04-245">在引用驱动器时 `Function:` ，请在 **函数** 后面键入一个冒号，就像引用计算机的或驱动器时所做的那样 `C` `D` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-245">When referring to the `Function:` drive, type a colon after **Function**, just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="93a04-246">以下命令显示 PowerShell 的当前会话中的所有函数：</span><span class="sxs-lookup"><span data-stu-id="93a04-246">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="93a04-247">函数中的命令以脚本块的形式存储在函数的定义属性中。</span><span class="sxs-lookup"><span data-stu-id="93a04-247">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="93a04-248">例如，若要显示 PowerShell 附带的帮助函数中的命令，请键入：</span><span class="sxs-lookup"><span data-stu-id="93a04-248">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="93a04-249">你还可以使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="93a04-249">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="93a04-250">有关驱动器的详细信息 `Function:` ，请参阅 **函数** 提供程序的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="93a04-250">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="93a04-251">键入 `Get-Help Function`。</span><span class="sxs-lookup"><span data-stu-id="93a04-251">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="93a04-252">在新会话中重用函数</span><span class="sxs-lookup"><span data-stu-id="93a04-252">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="93a04-253">在 PowerShell 命令提示符下键入函数时，该函数将成为当前会话的一部分。</span><span class="sxs-lookup"><span data-stu-id="93a04-253">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="93a04-254">直到会话结束时，此功能才可用。</span><span class="sxs-lookup"><span data-stu-id="93a04-254">It is available until the session ends.</span></span>

<span data-ttu-id="93a04-255">若要在所有 PowerShell 会话中使用函数，请将函数添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="93a04-255">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="93a04-256">有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-256">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="93a04-257">你还可以将函数保存在 PowerShell 脚本文件中。</span><span class="sxs-lookup"><span data-stu-id="93a04-257">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="93a04-258">在文本文件中键入函数，然后使用文件扩展名保存该文件 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="93a04-258">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="93a04-259">编写函数的帮助</span><span class="sxs-lookup"><span data-stu-id="93a04-259">Writing Help for Functions</span></span>

<span data-ttu-id="93a04-260">`Get-Help`Cmdlet 可获取有关函数以及 cmdlet、提供程序和脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="93a04-260">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="93a04-261">若要获取有关函数的帮助，请键入 `Get-Help` 后跟函数名称。</span><span class="sxs-lookup"><span data-stu-id="93a04-261">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="93a04-262">例如，若要获取有关该函数的帮助 `Get-MyDisks` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="93a04-262">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="93a04-263">您可以使用以下两种方法之一来编写函数的帮助：</span><span class="sxs-lookup"><span data-stu-id="93a04-263">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="93a04-264">函数 Comment-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="93a04-264">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="93a04-265">在注释中使用特殊关键字创建帮助主题。</span><span class="sxs-lookup"><span data-stu-id="93a04-265">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="93a04-266">若要为函数创建基于注释的帮助，注释必须位于函数体的开头或末尾，或者位于 function 关键字之前的行中。</span><span class="sxs-lookup"><span data-stu-id="93a04-266">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="93a04-267">有关基于注释的帮助的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-267">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="93a04-268">函数 XML-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="93a04-268">XML-Based Help for Functions</span></span>

  <span data-ttu-id="93a04-269">创建基于 XML 的帮助主题，如通常为 cmdlet 创建的类型。</span><span class="sxs-lookup"><span data-stu-id="93a04-269">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="93a04-270">如果要将帮助主题本地化为多种语言，则必须提供基于 XML 的帮助。</span><span class="sxs-lookup"><span data-stu-id="93a04-270">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="93a04-271">若要将函数与基于 XML 的帮助主题相关联，请使用 `.ExternalHelp` 基于注释的帮助关键字。</span><span class="sxs-lookup"><span data-stu-id="93a04-271">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="93a04-272">如果没有此关键字，则找 `Get-Help` 不到函数帮助主题，并且对的调用将 `Get-Help` 仅返回自动生成的帮助。</span><span class="sxs-lookup"><span data-stu-id="93a04-272">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="93a04-273">有关关键字的详细信息 `ExternalHelp` ，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="93a04-273">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="93a04-274">有关基于 XML 的帮助的详细信息，请参阅 [如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="93a04-274">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="see-also"></a><span data-ttu-id="93a04-275">请参阅</span><span class="sxs-lookup"><span data-stu-id="93a04-275">See also</span></span>

[<span data-ttu-id="93a04-276">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="93a04-276">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="93a04-277">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="93a04-277">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="93a04-278">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="93a04-278">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="93a04-279">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="93a04-279">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="93a04-280">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="93a04-280">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="93a04-281">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="93a04-281">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="93a04-282">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="93a04-282">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="93a04-283">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="93a04-283">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="93a04-284">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="93a04-284">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="93a04-285">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="93a04-285">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="93a04-286">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="93a04-286">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="93a04-287">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="93a04-287">about_Function_provider</span></span>](about_Function_provider.md)
