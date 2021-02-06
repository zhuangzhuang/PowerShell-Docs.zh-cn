---
description: 介绍如何在 PowerShell 中使用命令参数。
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598707"
---
# <a name="about-parameters"></a><span data-ttu-id="f69d5-103">关于参数</span><span class="sxs-lookup"><span data-stu-id="f69d5-103">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="f69d5-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="f69d5-104">Short description</span></span>
<span data-ttu-id="f69d5-105">介绍如何在 PowerShell 中使用命令参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-105">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f69d5-106">长说明</span><span class="sxs-lookup"><span data-stu-id="f69d5-106">Long description</span></span>

<span data-ttu-id="f69d5-107">大多数 PowerShell 命令（如 cmdlet、函数和脚本）都依赖于参数，以允许用户选择选项或提供输入。</span><span class="sxs-lookup"><span data-stu-id="f69d5-107">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="f69d5-108">参数跟在命令名之后，格式如下：</span><span class="sxs-lookup"><span data-stu-id="f69d5-108">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="f69d5-109">参数的名称前面带有连字符 ( ) ，这向 PowerShell 发出信号，表示连字符后面的单词是参数名称。</span><span class="sxs-lookup"><span data-stu-id="f69d5-109">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="f69d5-110">参数名称和值可以用空格或冒号字符分隔。</span><span class="sxs-lookup"><span data-stu-id="f69d5-110">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="f69d5-111">某些参数不需要或接受参数值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-111">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="f69d5-112">其他参数需要一个值，但是在命令中不需要参数名称。</span><span class="sxs-lookup"><span data-stu-id="f69d5-112">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="f69d5-113">参数的类型和这些参数的要求各不相同。</span><span class="sxs-lookup"><span data-stu-id="f69d5-113">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="f69d5-114">若要查找有关命令的参数的信息，请使用 `Get-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f69d5-114">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="f69d5-115">例如，若要查找有关该 cmdlet 的参数的信息 `Get-ChildItem` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="f69d5-115">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="f69d5-116">若要查找有关脚本的参数的信息，请使用脚本文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="f69d5-116">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="f69d5-117">例如：</span><span class="sxs-lookup"><span data-stu-id="f69d5-117">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="f69d5-118">`Get-Help`Cmdlet 返回有关命令的各种详细信息，包括说明、命令语法、有关参数的信息，以及演示如何在命令中使用参数的示例。</span><span class="sxs-lookup"><span data-stu-id="f69d5-118">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="f69d5-119">你还可以使用 cmdlet 的参数参数 `Get-Help` 查找有关特定参数的信息。</span><span class="sxs-lookup"><span data-stu-id="f69d5-119">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="f69d5-120">或者，可以将 **参数** 参数与通配符 ( ) 值一起使用， `*` 查找有关该命令的所有参数的信息。</span><span class="sxs-lookup"><span data-stu-id="f69d5-120">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="f69d5-121">例如，以下命令将获取有关该 cmdlet 的所有参数的信息 `Get-Member` ：</span><span class="sxs-lookup"><span data-stu-id="f69d5-121">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="f69d5-122">默认参数值</span><span class="sxs-lookup"><span data-stu-id="f69d5-122">Default parameter values</span></span>

<span data-ttu-id="f69d5-123">可选参数具有默认值，该值是在命令中未指定参数时使用或假设的值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-123">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="f69d5-124">例如，许多 cmdlet 的 **ComputerName** 参数的默认值是本地计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="f69d5-124">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="f69d5-125">因此，在命令中使用本地计算机名称，除非指定 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-125">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="f69d5-126">若要查找默认参数值，请参阅 cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="f69d5-126">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="f69d5-127">参数说明应包含默认值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-127">The parameter description should include the default value.</span></span>

<span data-ttu-id="f69d5-128">还可以为 cmdlet 或高级函数的任何参数设置自定义默认值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-128">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="f69d5-129">有关设置自定义默认值的信息，请参阅 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。</span><span class="sxs-lookup"><span data-stu-id="f69d5-129">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="f69d5-130">参数属性表</span><span class="sxs-lookup"><span data-stu-id="f69d5-130">Parameter attribute table</span></span>

<span data-ttu-id="f69d5-131">当你使用 cmdlet 的 **Full**、 **parameter** 或 **Online** 参数时 `Get-Help` ，将 `Get-Help` 显示一个参数属性表，其中包含有关参数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f69d5-131">When you use the **Full**, **Parameter**, or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="f69d5-132">此信息包括你需要知道使用参数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f69d5-132">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="f69d5-133">例如，cmdlet 的帮助主题 `Get-ChildItem` 包含有关其 Path 参数的以下详细信息：</span><span class="sxs-lookup"><span data-stu-id="f69d5-133">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="f69d5-134">参数信息包括参数语法、参数说明和参数特性。</span><span class="sxs-lookup"><span data-stu-id="f69d5-134">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="f69d5-135">以下各节介绍参数特性。</span><span class="sxs-lookup"><span data-stu-id="f69d5-135">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="f69d5-136">必需参数</span><span class="sxs-lookup"><span data-stu-id="f69d5-136">Parameter Required</span></span>

<span data-ttu-id="f69d5-137">此设置指示参数是否是必需的，即是否所有使用此 cmdlet 的命令都必须包含此参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-137">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="f69d5-138">如果值为 **True** ，并且命令中缺少参数，则 PowerShell 将提示你输入参数的值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-138">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="f69d5-139">参数位置</span><span class="sxs-lookup"><span data-stu-id="f69d5-139">Parameter Position</span></span>

<span data-ttu-id="f69d5-140">如果 `Position` 设置设置为正整数，则不需要参数名称。</span><span class="sxs-lookup"><span data-stu-id="f69d5-140">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="f69d5-141">这种类型的参数称为位置参数，数值指示参数必须与其他位置参数出现的位置。</span><span class="sxs-lookup"><span data-stu-id="f69d5-141">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="f69d5-142">命名的参数可以在 cmdlet 名称后的任何位置中列出。</span><span class="sxs-lookup"><span data-stu-id="f69d5-142">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="f69d5-143">如果包含位置参数的参数名称，则可以在 cmdlet 名称后的任何位置中列出参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-143">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="f69d5-144">例如， `Get-ChildItem` cmdlet 具有 Path 和 Exclude 参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-144">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="f69d5-145">`Position`**路径** 的设置为 **0**，这意味着它是一个位置参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-145">The `Position` setting for **Path** is **0**, which means that it is a positional parameter.</span></span> <span data-ttu-id="f69d5-146">`Position`**排除** 的设置 **命名** 为。</span><span class="sxs-lookup"><span data-stu-id="f69d5-146">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="f69d5-147">这意味着该 **路径** 不需要参数名，但其参数值必须是命令中的第一个或唯一一个未命名的参数值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-147">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="f69d5-148">但是，因为 Exclude 参数是命名参数，你可以将其放在命令中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="f69d5-148">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="f69d5-149">由于 `Position` 这两个参数的设置，你可以使用以下任一命令：</span><span class="sxs-lookup"><span data-stu-id="f69d5-149">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="f69d5-150">如果要包含另一个位置参数而不包括参数名称，则该参数必须按设置指定的顺序放置 `Position` 。</span><span class="sxs-lookup"><span data-stu-id="f69d5-150">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="f69d5-151">参数类型</span><span class="sxs-lookup"><span data-stu-id="f69d5-151">Parameter Type</span></span>

<span data-ttu-id="f69d5-152">此设置指定参数值的 Microsoft .NET 框架类型。</span><span class="sxs-lookup"><span data-stu-id="f69d5-152">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="f69d5-153">例如，如果类型为 **Int32**，则参数值必须是整数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-153">For example, if the type is **Int32**, the parameter value must be an integer.</span></span> <span data-ttu-id="f69d5-154">如果类型为 string，则参数值必须为字符串。</span><span class="sxs-lookup"><span data-stu-id="f69d5-154">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="f69d5-155">如果字符串包含空格，则必须用引号将该值引起来，或者必须在空格前面加上转义符 ( ") 。</span><span class="sxs-lookup"><span data-stu-id="f69d5-155">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="f69d5-156">默认值</span><span class="sxs-lookup"><span data-stu-id="f69d5-156">Default Value</span></span>

<span data-ttu-id="f69d5-157">如果未提供其他值，则此设置将指定参数将假设的值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-157">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="f69d5-158">例如，Path 参数的默认值通常为当前目录。</span><span class="sxs-lookup"><span data-stu-id="f69d5-158">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="f69d5-159">必需的参数决不会有默认值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-159">Required parameters never have a default value.</span></span>
<span data-ttu-id="f69d5-160">对于许多可选参数，没有默认值，因为如果不使用参数，则该参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="f69d5-160">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="f69d5-161">接受多个值</span><span class="sxs-lookup"><span data-stu-id="f69d5-161">Accepts Multiple Values</span></span>

<span data-ttu-id="f69d5-162">此设置指示参数是否接受多个参数值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-162">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="f69d5-163">当参数接受多个值时，可以在命令中键入以逗号分隔的列表作为参数的值，或将逗号分隔的列表保存 (数组中的数组) ，然后将该变量指定为参数值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-163">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="f69d5-164">例如，cmdlet 的 ServiceName 参数 `Get-Service` 接受多个值。</span><span class="sxs-lookup"><span data-stu-id="f69d5-164">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="f69d5-165">以下命令都是有效的：</span><span class="sxs-lookup"><span data-stu-id="f69d5-165">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="f69d5-166">接受管道输入</span><span class="sxs-lookup"><span data-stu-id="f69d5-166">Accepts Pipeline Input</span></span>

<span data-ttu-id="f69d5-167">此设置指示是否可以使用管道运算符 ( ) 将 `|` 值发送到参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-167">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="f69d5-168">当参数为 "True (值) " 时，PowerShell 会尝试将任何管道值与该参数相关联，然后再尝试其他方法来解释该命令。</span><span class="sxs-lookup"><span data-stu-id="f69d5-168">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="f69d5-169">例如，仅当值具有一个名为 **name** 的属性时，才能通过管道将值传递给 **name** 参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-169">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="f69d5-170">一个类型化参数，该参数接受管道输入 (`by Value`) 或 (`by PropertyName`) 允许在参数上使用 **延迟绑定** 脚本块。</span><span class="sxs-lookup"><span data-stu-id="f69d5-170">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="f69d5-171">**延迟绑定** 脚本块在 **ParameterBinding** 期间自动运行。</span><span class="sxs-lookup"><span data-stu-id="f69d5-171">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="f69d5-172">结果绑定到参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-172">The result is bound to the parameter.</span></span> <span data-ttu-id="f69d5-173">延迟绑定对于定义为类型或的参数 **不** 起作用 `ScriptBlock` ，不 `System.Object` 调用脚本块。 </span><span class="sxs-lookup"><span data-stu-id="f69d5-173">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="f69d5-174">你可以在此处了解 about_Script_Blocks 的 **延迟绑定** 脚本块 [。](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="f69d5-174">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="f69d5-175">接受通配符</span><span class="sxs-lookup"><span data-stu-id="f69d5-175">Accepts Wildcard Characters</span></span>

<span data-ttu-id="f69d5-176">此设置指示参数的值是否可以包含通配符，使参数值可以与目标容器中的多个现有项匹配。</span><span class="sxs-lookup"><span data-stu-id="f69d5-176">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="f69d5-177">通用参数</span><span class="sxs-lookup"><span data-stu-id="f69d5-177">Common Parameters</span></span>

<span data-ttu-id="f69d5-178">常见参数是可与任何 cmdlet 一起使用的参数。</span><span class="sxs-lookup"><span data-stu-id="f69d5-178">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="f69d5-179">有关常见参数的详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f69d5-179">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f69d5-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="f69d5-180">See also</span></span>

[<span data-ttu-id="f69d5-181">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="f69d5-181">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="f69d5-182">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="f69d5-182">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="f69d5-183">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="f69d5-183">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="f69d5-184">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="f69d5-184">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="f69d5-185">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="f69d5-185">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="f69d5-186">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="f69d5-186">about_Wildcards</span></span>](about_Wildcards.md)

