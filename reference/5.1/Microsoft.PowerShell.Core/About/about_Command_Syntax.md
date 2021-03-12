---
description: 描述在 PowerShell 中使用的语法关系图。
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: ff7a243a584ee336c0356200f5ba68fde55e0836
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194621"
---
# <a name="about-command-syntax"></a><span data-ttu-id="b8b41-103">关于命令语法</span><span class="sxs-lookup"><span data-stu-id="b8b41-103">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="b8b41-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="b8b41-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b8b41-105">描述在 PowerShell 中使用的语法关系图。</span><span class="sxs-lookup"><span data-stu-id="b8b41-105">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b8b41-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="b8b41-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b8b41-107">[Get-help](xref:Microsoft.PowerShell.Core.Get-Help)和[get-help](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet 显示语法关系图，有助于正确构造命令。</span><span class="sxs-lookup"><span data-stu-id="b8b41-107">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="b8b41-108">本主题说明如何解释语法关系图。</span><span class="sxs-lookup"><span data-stu-id="b8b41-108">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="b8b41-109">语法关系图</span><span class="sxs-lookup"><span data-stu-id="b8b41-109">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="b8b41-110">命令语法关系图中的每个段落均表示命令的有效格式。</span><span class="sxs-lookup"><span data-stu-id="b8b41-110">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="b8b41-111">若要构造命令，请从左到右跟踪语法关系图。</span><span class="sxs-lookup"><span data-stu-id="b8b41-111">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="b8b41-112">从可选参数中选择，并提供占位符的值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-112">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="b8b41-113">对于语法关系图，PowerShell 使用以下表示法。</span><span class="sxs-lookup"><span data-stu-id="b8b41-113">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="b8b41-114">下面是 [新别名](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet 的语法。</span><span class="sxs-lookup"><span data-stu-id="b8b41-114">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="b8b41-115">语法为可读性，但 PowerShell 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b8b41-115">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="b8b41-116">语法关系图包含以下元素。</span><span class="sxs-lookup"><span data-stu-id="b8b41-116">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="b8b41-117">命令名称</span><span class="sxs-lookup"><span data-stu-id="b8b41-117">Command name</span></span>

<span data-ttu-id="b8b41-118">命令始终以命令名称开头，例如 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-118">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="b8b41-119">键入命令名称或其别名，如的 "gcm" `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-119">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="b8b41-120">Parameters</span><span class="sxs-lookup"><span data-stu-id="b8b41-120">Parameters</span></span>

<span data-ttu-id="b8b41-121">命令的参数是确定命令用途的选项。</span><span class="sxs-lookup"><span data-stu-id="b8b41-121">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="b8b41-122">某些参数采用一个 "值"，它是命令的用户输入。</span><span class="sxs-lookup"><span data-stu-id="b8b41-122">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="b8b41-123">例如，该 `Get-Help` 命令有一个 **name** 参数，可让你指定显示帮助的主题的名称。</span><span class="sxs-lookup"><span data-stu-id="b8b41-123">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="b8b41-124">主题名称是 **name** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-124">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="b8b41-125">在 PowerShell 命令中，参数名称始终以连字符开头。</span><span class="sxs-lookup"><span data-stu-id="b8b41-125">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="b8b41-126">连字符告诉 PowerShell：命令中的项是参数名称。</span><span class="sxs-lookup"><span data-stu-id="b8b41-126">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="b8b41-127">例如，若要使用的 Name 参数 `New-Alias` ，请键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="b8b41-127">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="b8b41-128">参数可以是必需的或可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-128">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="b8b41-129">在语法关系图中，可选项括在括号中 `[ ]` 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-129">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="b8b41-130">有关参数的详细信息，请参阅 [about_Parameters](about_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b41-130">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="b8b41-131">参数值</span><span class="sxs-lookup"><span data-stu-id="b8b41-131">Parameter Values</span></span>

<span data-ttu-id="b8b41-132">参数值是参数所采用的输入。</span><span class="sxs-lookup"><span data-stu-id="b8b41-132">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="b8b41-133">由于 Windows PowerShell 基于 Microsoft .NET 框架，因此参数值按其 .NET 类型在语法关系图中表示。</span><span class="sxs-lookup"><span data-stu-id="b8b41-133">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="b8b41-134">例如，的名称参数 `Get-Help` 采用 "String" 值，这是一个文本字符串，如一个词或用引号引起来的多个单词。</span><span class="sxs-lookup"><span data-stu-id="b8b41-134">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="b8b41-135">参数值的 .NET 类型括在尖括号中， `< >` 以指示它是值的占位符，而不是在命令中键入的文本的占位符。</span><span class="sxs-lookup"><span data-stu-id="b8b41-135">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="b8b41-136">若要使用参数，请将 .NET 类型占位符替换为具有指定 .NET 类型的对象。</span><span class="sxs-lookup"><span data-stu-id="b8b41-136">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="b8b41-137">例如，若要使用 **Name** 参数，请键入 "-Name" 后跟一个字符串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8b41-137">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="b8b41-138">无值的参数</span><span class="sxs-lookup"><span data-stu-id="b8b41-138">Parameters with no values</span></span>

<span data-ttu-id="b8b41-139">有些参数不接受输入，因此它们没有参数值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-139">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="b8b41-140">不带值的参数称为 "开关参数"，因为它们的工作方式类似于打开/关闭开关。</span><span class="sxs-lookup"><span data-stu-id="b8b41-140">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="b8b41-141">你将它们包含在) 中 (或者将其从命令 (关闭) 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-141">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="b8b41-142">若要使用开关参数，只需键入参数名称（前面带有连字符）。</span><span class="sxs-lookup"><span data-stu-id="b8b41-142">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="b8b41-143">例如，若要使用 cmdlet 的 **WhatIf** 参数 `New-Alias` ，请键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="b8b41-143">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="b8b41-144">参数集</span><span class="sxs-lookup"><span data-stu-id="b8b41-144">Parameter Sets</span></span>

<span data-ttu-id="b8b41-145">命令的参数在 "参数集" 中列出。</span><span class="sxs-lookup"><span data-stu-id="b8b41-145">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="b8b41-146">参数集类似于语法关系图的段落。</span><span class="sxs-lookup"><span data-stu-id="b8b41-146">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="b8b41-147">`New-Alias`Cmdlet 设置了一个参数，但许多 cmdlet 具有多个参数集。</span><span class="sxs-lookup"><span data-stu-id="b8b41-147">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="b8b41-148">某些 cmdlet 参数对于参数集是唯一的，而其他参数则出现在多个参数集内。</span><span class="sxs-lookup"><span data-stu-id="b8b41-148">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="b8b41-149">每个参数集都表示有效命令的格式。</span><span class="sxs-lookup"><span data-stu-id="b8b41-149">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="b8b41-150">参数集仅包含可在命令中一起使用的参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-150">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="b8b41-151">如果不能在同一命令中使用参数，则它们将显示在单独的参数集内。</span><span class="sxs-lookup"><span data-stu-id="b8b41-151">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="b8b41-152">例如， [获取随机](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet 具有以下参数集：</span><span class="sxs-lookup"><span data-stu-id="b8b41-152">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="b8b41-153">返回一个随机数的第一个参数集具有 **最小** 和 **最大** 参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-153">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="b8b41-154">第二个参数集返回一组对象中随机选择的对象，其中包括 **InputObject** 和 **Count** 参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-154">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="b8b41-155">这两个参数集都具有 **SetSeed** 参数和通用参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-155">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="b8b41-156">这些参数集指示你可以在同一命令中使用 **InputObject** 和 **count** 参数，但不能在同一命令中使用 **最大值** 和 **计数** 参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-156">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="b8b41-157">您可以通过使用该参数集中的参数来指示要使用的参数集。</span><span class="sxs-lookup"><span data-stu-id="b8b41-157">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="b8b41-158">但是，每个 cmdlet 还具有一个默认参数集。</span><span class="sxs-lookup"><span data-stu-id="b8b41-158">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="b8b41-159">如果未指定参数集独有的参数，则使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="b8b41-159">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="b8b41-160">例如，如果使用 `Get-Random` 不带参数的，则 Windows PowerShell 假设你使用的是 **数字** 参数集，并且它将返回一个随机数字。</span><span class="sxs-lookup"><span data-stu-id="b8b41-160">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="b8b41-161">在每个参数集中，参数按位置顺序显示。</span><span class="sxs-lookup"><span data-stu-id="b8b41-161">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="b8b41-162">仅当省略可选参数名称时，命令中的参数顺序才有意义。</span><span class="sxs-lookup"><span data-stu-id="b8b41-162">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="b8b41-163">省略参数名称时，PowerShell 会按位置和类型将值分配给参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-163">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="b8b41-164">有关参数位置的详细信息，请参阅 `about_Parameters` 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-164">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="b8b41-165">语法关系图中的符号</span><span class="sxs-lookup"><span data-stu-id="b8b41-165">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="b8b41-166">语法关系图列出了命令名称、命令参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-166">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="b8b41-167">它还使用符号说明如何构造有效的命令。</span><span class="sxs-lookup"><span data-stu-id="b8b41-167">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="b8b41-168">语法关系图使用以下符号：</span><span class="sxs-lookup"><span data-stu-id="b8b41-168">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="b8b41-169">连字符 `-` 表示参数名称。</span><span class="sxs-lookup"><span data-stu-id="b8b41-169">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="b8b41-170">在命令中，在参数名称前面直接键入连字符，不包含空格，如语法关系图中所示。</span><span class="sxs-lookup"><span data-stu-id="b8b41-170">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="b8b41-171">例如，若要使用的 **Name** 参数 `New-Alias` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="b8b41-171">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="b8b41-172">尖括号 `<>` 表示占位符文本。</span><span class="sxs-lookup"><span data-stu-id="b8b41-172">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="b8b41-173">不在命令中键入尖括号或占位符文本。</span><span class="sxs-lookup"><span data-stu-id="b8b41-173">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="b8b41-174">而是将其替换为它所描述的项。</span><span class="sxs-lookup"><span data-stu-id="b8b41-174">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="b8b41-175">尖括号用于标识参数所采用的值的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="b8b41-175">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="b8b41-176">例如，若要使用 cmdlet 的 **Name** 参数，请将 `New-Alias` 替换为 `<string>` 字符串，该字符串是一个单词或用引号引起来的一组单词。</span><span class="sxs-lookup"><span data-stu-id="b8b41-176">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="b8b41-177">方括号 `[ ]` 表示可选项。</span><span class="sxs-lookup"><span data-stu-id="b8b41-177">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="b8b41-178">参数及其值可以是可选的，或者必需参数的名称可以是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-178">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="b8b41-179">例如，的 **Description** 参数 `New-Alias` 及其值括在括号中，因为它们都是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-179">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="b8b41-180">方括号还指示 Name 参数值 `<string>` 是必需的，但参数名称 "name" 是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-180">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="b8b41-181">追加到 .NET 类型的右括号和左括号 `[]` 指示参数可以接受该类型的一个或多个值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-181">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="b8b41-182">以逗号分隔的列表形式输入值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-182">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="b8b41-183">例如，cmdlet 的 **name** 参数 `New-Alias` 仅采用一个字符串，但 [获取进程](xref:Microsoft.PowerShell.Management.Get-Process)的 **name** 参数可以采用一个或多个字符串。</span><span class="sxs-lookup"><span data-stu-id="b8b41-183">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="b8b41-184">大括号 `{}` 指示一个 "枚举"，它是参数的有效值集。</span><span class="sxs-lookup"><span data-stu-id="b8b41-184">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="b8b41-185">大括号中的值由竖线分隔 `|` 。</span><span class="sxs-lookup"><span data-stu-id="b8b41-185">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="b8b41-186">这些条形表示 "专用" 或 "选择"，这意味着只能从大括号内列出的一组值中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-186">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="b8b41-187">例如，cmdlet 的语法 `New-Alias` 包括 **选项** 参数的以下值枚举：</span><span class="sxs-lookup"><span data-stu-id="b8b41-187">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="b8b41-188">大括号和竖线指示你可以为 **选项** 参数选择列出的任何一个值，例如 "ReadOnly" 或 "AllScope"。</span><span class="sxs-lookup"><span data-stu-id="b8b41-188">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="b8b41-189">可选项</span><span class="sxs-lookup"><span data-stu-id="b8b41-189">Optional Items</span></span>

<span data-ttu-id="b8b41-190">方括号将 `[]` 可选项括起来。</span><span class="sxs-lookup"><span data-stu-id="b8b41-190">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="b8b41-191">例如，在 `New-Alias` cmdlet 语法说明中， **Scope** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-191">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="b8b41-192">在语法中，参数名称和类型的两侧括在语法中：</span><span class="sxs-lookup"><span data-stu-id="b8b41-192">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="b8b41-193">以下两个示例都是 cmdlet 的正确用法 `New-Alias` ：</span><span class="sxs-lookup"><span data-stu-id="b8b41-193">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="b8b41-194">即使参数的值是必需的，参数名称也可以是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-194">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="b8b41-195">在语法中，参数名称两边的括号中指出了这一点，而不是参数类型，如以下 cmdlet 所示 `New-Alias` ：</span><span class="sxs-lookup"><span data-stu-id="b8b41-195">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="b8b41-196">以下命令正确使用 `New-Alias` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8b41-196">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="b8b41-197">这些命令产生的结果相同。</span><span class="sxs-lookup"><span data-stu-id="b8b41-197">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="b8b41-198">如果在语句中不包含参数名，则 Windows PowerShell 将尝试使用参数的位置将这些值分配给参数。</span><span class="sxs-lookup"><span data-stu-id="b8b41-198">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="b8b41-199">以下示例不完整：</span><span class="sxs-lookup"><span data-stu-id="b8b41-199">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="b8b41-200">此 cmdlet 需要 **Name** 和 **Value** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="b8b41-200">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="b8b41-201">在语法示例中，括号还用于命名和强制转换为 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="b8b41-201">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="b8b41-202">在此上下文中，方括号不指示元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="b8b41-202">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b41-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8b41-203">SEE ALSO</span></span>

- [<span data-ttu-id="b8b41-204">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="b8b41-204">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="b8b41-205">Get-Command</span><span class="sxs-lookup"><span data-stu-id="b8b41-205">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="b8b41-206">Get-Help</span><span class="sxs-lookup"><span data-stu-id="b8b41-206">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)
