---
ms.date: 09/13/2016
ms.topic: reference
title: 参数属性声明
description: 参数属性声明
ms.openlocfilehash: 24a49406b1493a7f8c23bca798ddb3e73a901111
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500223"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="faed9-103">参数属性声明</span><span class="sxs-lookup"><span data-stu-id="faed9-103">Parameter Attribute Declaration</span></span>

<span data-ttu-id="faed9-104">参数属性将 cmdlet 类的公共属性标识为 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-104">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="faed9-105">语法</span><span class="sxs-lookup"><span data-stu-id="faed9-105">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="faed9-106">parameters</span><span class="sxs-lookup"><span data-stu-id="faed9-106">Parameters</span></span>

<span data-ttu-id="faed9-107">`Mandatory` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-107">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="faed9-108">`True` 指示 cmdlet 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="faed9-108">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="faed9-109">如果在调用 cmdlet 时未提供所需的参数，则 Windows PowerShell 会提示用户输入参数值。</span><span class="sxs-lookup"><span data-stu-id="faed9-109">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="faed9-110">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="faed9-110">The default is `false`.</span></span>

<span data-ttu-id="faed9-111">`ParameterSetName` ([system.string](/dotnet/api/System.String)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-111">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="faed9-112">指定此 cmdlet 参数所属的参数集。</span><span class="sxs-lookup"><span data-stu-id="faed9-112">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="faed9-113">如果未指定参数集，则参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="faed9-113">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="faed9-114">`Position` ([system.object](/dotnet/api/System.Int32)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-114">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="faed9-115">指定参数在 Windows PowerShell 命令中的位置。</span><span class="sxs-lookup"><span data-stu-id="faed9-115">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="faed9-116">`ValueFromPipeline` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-116">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="faed9-117">`True` 指示 cmdlet 参数从管道对象获取其值。</span><span class="sxs-lookup"><span data-stu-id="faed9-117">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="faed9-118">如果 cmdlet 访问完整对象，而不仅仅是对象的属性，请指定此关键字。</span><span class="sxs-lookup"><span data-stu-id="faed9-118">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="faed9-119">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="faed9-119">The default is `false`.</span></span>

<span data-ttu-id="faed9-120">`ValueFromPipelineByPropertyName` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-120">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="faed9-121">`True` 指示 cmdlet 参数从管道对象的属性中获取其值，该对象具有与此参数相同的名称或别名。</span><span class="sxs-lookup"><span data-stu-id="faed9-121">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="faed9-122">例如，如果该 cmdlet 具有 `Name` 参数并且管道对象还具有一个 `Name` 属性，则该属性的值将 `Name` 分配给该 cmdlet 的 `Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-122">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="faed9-123">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="faed9-123">The default is `false`.</span></span>

<span data-ttu-id="faed9-124">`ValueFromRemainingArguments` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-124">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="faed9-125">`True` 指示 cmdlet 参数接受传递到 cmdlet 的所有剩余参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-125">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="faed9-126">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="faed9-126">The default is `false`.</span></span>

<span data-ttu-id="faed9-127">`HelpMessage` 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-127">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="faed9-128">指定参数的简短说明。</span><span class="sxs-lookup"><span data-stu-id="faed9-128">Specifies a short description of the parameter.</span></span> <span data-ttu-id="faed9-129">运行 cmdlet 时，Windows PowerShell 会显示此消息，未指定必需的参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-129">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="faed9-130">`HelpMessageBaseName` 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-130">`HelpMessageBaseName` Optional named parameter.</span></span> <span data-ttu-id="faed9-131">指定资源标识符驻留的位置。</span><span class="sxs-lookup"><span data-stu-id="faed9-131">Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="faed9-132">例如，此参数可以指定包含要本地化的帮助消息的资源程序集。</span><span class="sxs-lookup"><span data-stu-id="faed9-132">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="faed9-133">`HelpMessageResourceId` 可选的命名参数。指定帮助消息的资源标识符。</span><span class="sxs-lookup"><span data-stu-id="faed9-133">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="faed9-134">备注</span><span class="sxs-lookup"><span data-stu-id="faed9-134">Remarks</span></span>

- <span data-ttu-id="faed9-135">有关如何声明此属性的详细信息，请参阅 [如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="faed9-135">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="faed9-136">Cmdlet 可以有任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-136">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="faed9-137">但是，为了获得更好的用户体验，请限制参数的数目。</span><span class="sxs-lookup"><span data-stu-id="faed9-137">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="faed9-138">必须对公共非静态字段或属性声明参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-138">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="faed9-139">应在属性上声明参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-139">Parameters should be declared on properties.</span></span> <span data-ttu-id="faed9-140">该属性必须具有公共集访问器，如果指定了 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 关键字，则该属性必须具有公共 get 访问器。</span><span class="sxs-lookup"><span data-stu-id="faed9-140">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="faed9-141">当指定位置参数时，请将参数集中的位置参数数目限制为小于5。</span><span class="sxs-lookup"><span data-stu-id="faed9-141">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="faed9-142">和，位置参数不必是连续的。</span><span class="sxs-lookup"><span data-stu-id="faed9-142">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="faed9-143">位置5、100和250的工作方式与位置0、1和2相同。</span><span class="sxs-lookup"><span data-stu-id="faed9-143">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="faed9-144">如果 `Position` 未指定关键字，则必须按其名称引用 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-144">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="faed9-145">使用参数集时，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="faed9-145">When you use parameter sets, note the following:</span></span>

  - <span data-ttu-id="faed9-146">每个参数集必须至少具有一个唯一参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-146">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="faed9-147">良好的 cmdlet 设计指明此唯一参数应该也是必需的（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="faed9-147">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="faed9-148">如果你的 cmdlet 设计为不带参数运行，则 unique 参数不是必需的。</span><span class="sxs-lookup"><span data-stu-id="faed9-148">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

  - <span data-ttu-id="faed9-149">参数集应包含多个具有相同位置的位置参数。</span><span class="sxs-lookup"><span data-stu-id="faed9-149">No parameter set should contain more than one positional parameter with the same position.</span></span>

  - <span data-ttu-id="faed9-150">参数集中只应声明一个参数 `ValueFromPipeline = true` 。</span><span class="sxs-lookup"><span data-stu-id="faed9-150">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span>

  - <span data-ttu-id="faed9-151">可以定义多个参数 `ValueFromPipelineByPropertyName = true` 。</span><span class="sxs-lookup"><span data-stu-id="faed9-151">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="faed9-152">有关参数名称的准则的详细信息，请参阅 [Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)。</span><span class="sxs-lookup"><span data-stu-id="faed9-152">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="faed9-153">参数属性是由 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 类定义的。</span><span class="sxs-lookup"><span data-stu-id="faed9-153">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="faed9-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="faed9-154">See Also</span></span>

[<span data-ttu-id="faed9-155">System.web. Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="faed9-155">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="faed9-156">Cmdlet 参数名称</span><span class="sxs-lookup"><span data-stu-id="faed9-156">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="faed9-157">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="faed9-157">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
