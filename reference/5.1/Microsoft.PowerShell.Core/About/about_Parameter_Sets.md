---
description: 描述如何定义和使用高级函数中的参数集。
title: about_Parameter_Sets
ms.date: 01/05/2021
ms.openlocfilehash: 8f3a33345a8e2fa19810c8ebd527d9a7dca7dec5
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917862"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="ae904-103">关于参数集</span><span class="sxs-lookup"><span data-stu-id="ae904-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="ae904-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="ae904-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ae904-105">描述如何定义和使用高级函数中的参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="ae904-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="ae904-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ae904-107">PowerShell 使用参数集使你可以编写一个函数，该函数可对不同方案执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="ae904-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="ae904-108">参数集使你可以向用户公开不同参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="ae904-109">和，根据用户指定的参数返回不同的信息。</span><span class="sxs-lookup"><span data-stu-id="ae904-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="ae904-110">参数集要求</span><span class="sxs-lookup"><span data-stu-id="ae904-110">Parameter set requirements</span></span>

<span data-ttu-id="ae904-111">以下要求适用于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="ae904-112">每个参数集都必须具有唯一的参数组合。</span><span class="sxs-lookup"><span data-stu-id="ae904-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="ae904-113">如果可能，必须至少有一个唯一参数是必需参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="ae904-114">包含多个位置参数的参数集必须为每个参数定义唯一的位置。</span><span class="sxs-lookup"><span data-stu-id="ae904-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="ae904-115">无两个位置参数可以指定同一位置。</span><span class="sxs-lookup"><span data-stu-id="ae904-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="ae904-116">集内只有一个参数可以 `ValueFromPipeline` 用值声明关键字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ae904-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="ae904-117">多个参数可以 `ValueFromPipelineByPropertyName` 使用值定义关键字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ae904-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="ae904-118">如果未指定参数的参数集，则参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="ae904-119">参数集限制为32。</span><span class="sxs-lookup"><span data-stu-id="ae904-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="ae904-120">默认参数集</span><span class="sxs-lookup"><span data-stu-id="ae904-120">Default parameter sets</span></span>

<span data-ttu-id="ae904-121">如果定义了多个参数集，则 `DefaultParameterSetName` **CmdletBinding** 属性的关键字将指定默认参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="ae904-122">当 PowerShell 无法根据提供给命令的信息确定设置为使用的参数时，将使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="ae904-123">有关 **CmdletBinding** 属性的详细信息，请参阅 [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)。</span><span class="sxs-lookup"><span data-stu-id="ae904-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="ae904-124">声明参数集</span><span class="sxs-lookup"><span data-stu-id="ae904-124">Declaring parameter sets</span></span>

<span data-ttu-id="ae904-125">若要创建参数集，必须 `ParameterSetName` 为参数集中的每个参数指定 **参数** 属性的关键字。</span><span class="sxs-lookup"><span data-stu-id="ae904-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="ae904-126">对于属于多个参数集的参数，请为每个参数集添加一个 **参数** 特性。</span><span class="sxs-lookup"><span data-stu-id="ae904-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="ae904-127">**参数** 特性使你能够以不同的方式为每个参数集定义参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="ae904-128">例如，可以在一组中将参数定义为强制参数，并在另一个集中定义为可选参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="ae904-129">但是，每个参数集必须至少包含一个唯一参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="ae904-130">没有分配的参数集名称的参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="ae904-131">示例</span><span class="sxs-lookup"><span data-stu-id="ae904-131">Example</span></span>

<span data-ttu-id="ae904-132">以下示例函数对文本文件中的行、字符和单词进行计数。</span><span class="sxs-lookup"><span data-stu-id="ae904-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="ae904-133">使用参数可以指定要返回的值以及要度量的文件。</span><span class="sxs-lookup"><span data-stu-id="ae904-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="ae904-134">定义了四个参数集：</span><span class="sxs-lookup"><span data-stu-id="ae904-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="ae904-135">路径</span><span class="sxs-lookup"><span data-stu-id="ae904-135">Path</span></span>
- <span data-ttu-id="ae904-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="ae904-136">PathAll</span></span>
- <span data-ttu-id="ae904-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ae904-137">LiteralPath</span></span>
- <span data-ttu-id="ae904-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="ae904-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="ae904-139">每个参数集都必须具有唯一参数或参数的唯一组合。</span><span class="sxs-lookup"><span data-stu-id="ae904-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="ae904-140">`Path`和 `PathAll` 参数集非常相似，但 **All** 参数对于参数集是唯一的 `PathAll` 。</span><span class="sxs-lookup"><span data-stu-id="ae904-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="ae904-141">对于 `LiteralPath` 和参数集也是如此 `LiteralPathAll` 。</span><span class="sxs-lookup"><span data-stu-id="ae904-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="ae904-142">即使 `PathAll` 和 `LiteralPathAll` 参数均设置了 **All** 参数， **路径** 和 **LiteralPath** 参数也会将它们区分开来。</span><span class="sxs-lookup"><span data-stu-id="ae904-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="ae904-143">使用 `Get-Command -Syntax` 会显示每个参数集的语法。</span><span class="sxs-lookup"><span data-stu-id="ae904-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="ae904-144">但它不显示参数集的名称。</span><span class="sxs-lookup"><span data-stu-id="ae904-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="ae904-145">下面的示例显示了可在每个参数集中使用哪些参数。</span><span class="sxs-lookup"><span data-stu-id="ae904-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="ae904-146">操作中的参数集</span><span class="sxs-lookup"><span data-stu-id="ae904-146">Parameter sets in action</span></span>

<span data-ttu-id="ae904-147">在此示例中，我们使用 `PathAll` 参数集。</span><span class="sxs-lookup"><span data-stu-id="ae904-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
