---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3d23f76dbf8e1c9a21805a4914038c8c4f319852
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597463"
---
# <span data-ttu-id="33be4-102">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="33be4-102">Write-Debug</span></span>

## <span data-ttu-id="33be4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="33be4-103">SYNOPSIS</span></span>
<span data-ttu-id="33be4-104">将调试消息写入控制台。</span><span class="sxs-lookup"><span data-stu-id="33be4-104">Writes a debug message to the console.</span></span>

## <span data-ttu-id="33be4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33be4-105">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="33be4-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="33be4-106">DESCRIPTION</span></span>

<span data-ttu-id="33be4-107">该 `Write-Debug` cmdlet 从脚本或命令中将调试消息写入主机。</span><span class="sxs-lookup"><span data-stu-id="33be4-107">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="33be4-108">默认情况下，调试消息不会显示在控制台中，但可以使用 **debug** 参数或变量显示它们 `$DebugPreference` 。</span><span class="sxs-lookup"><span data-stu-id="33be4-108">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="33be4-109">示例</span><span class="sxs-lookup"><span data-stu-id="33be4-109">EXAMPLES</span></span>

### <span data-ttu-id="33be4-110">示例 1：了解 $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="33be4-110">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="33be4-111">此示例编写调试消息。</span><span class="sxs-lookup"><span data-stu-id="33be4-111">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="33be4-112">的默认值 `$DebugPreference` 为 **SilentlyContinue**。</span><span class="sxs-lookup"><span data-stu-id="33be4-112">The default value of `$DebugPreference` is **SilentlyContinue**.</span></span> <span data-ttu-id="33be4-113">因此，该消息不会显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="33be4-113">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="33be4-114">示例2：更改 $DebugPreference 的值</span><span class="sxs-lookup"><span data-stu-id="33be4-114">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="33be4-115">此示例演示更改变量的值的效果 `$DebugPreference` 。</span><span class="sxs-lookup"><span data-stu-id="33be4-115">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="33be4-116">首先，我们显示的当前值 `$DebugPreference` ，并尝试编写调试消息。</span><span class="sxs-lookup"><span data-stu-id="33be4-116">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="33be4-117">然后，将的值更改 `$DebugPreference` 为 **Continue**，这允许显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="33be4-117">Then we change the value of `$DebugPreference` to **Continue**, which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="33be4-118">有关的详细信息 `$DebugPreference` ，请参阅 [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)。</span><span class="sxs-lookup"><span data-stu-id="33be4-118">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="33be4-119">示例3：使用 Debug 参数覆盖 $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="33be4-119">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="33be4-120">`Test-Debug`函数将变量的值写入 `$DebugPreference` PowerShell 主机和调试流。</span><span class="sxs-lookup"><span data-stu-id="33be4-120">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="33be4-121">在此示例中，我们使用 **Debug** 参数重写 `$DebugPreference` 该值。</span><span class="sxs-lookup"><span data-stu-id="33be4-121">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="33be4-122">请注意， `$DebugPreference` 当你使用 **Debug** 参数时，的值将更改。</span><span class="sxs-lookup"><span data-stu-id="33be4-122">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="33be4-123">此更改只影响函数的作用域。</span><span class="sxs-lookup"><span data-stu-id="33be4-123">This change only affects the scope of the function.</span></span> <span data-ttu-id="33be4-124">此值在函数之外不受影响。</span><span class="sxs-lookup"><span data-stu-id="33be4-124">The value is not affected outside the function.</span></span>

<span data-ttu-id="33be4-125">有关 **Debug** 通用参数的详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="33be4-125">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33be4-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33be4-126">PARAMETERS</span></span>

### <span data-ttu-id="33be4-127">-Message</span><span class="sxs-lookup"><span data-stu-id="33be4-127">-Message</span></span>

<span data-ttu-id="33be4-128">指定要发送到控制台的调试消息。</span><span class="sxs-lookup"><span data-stu-id="33be4-128">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33be4-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33be4-129">CommonParameters</span></span>

<span data-ttu-id="33be4-130">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="33be4-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33be4-131">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="33be4-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33be4-132">输入</span><span class="sxs-lookup"><span data-stu-id="33be4-132">INPUTS</span></span>

### <span data-ttu-id="33be4-133">System.String</span><span class="sxs-lookup"><span data-stu-id="33be4-133">System.String</span></span>

<span data-ttu-id="33be4-134">可以通过管道将包含调试消息的字符串传递给 `Write-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="33be4-134">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="33be4-135">输出</span><span class="sxs-lookup"><span data-stu-id="33be4-135">OUTPUTS</span></span>

### <span data-ttu-id="33be4-136">无</span><span class="sxs-lookup"><span data-stu-id="33be4-136">None</span></span>

<span data-ttu-id="33be4-137">`Write-Debug` 仅写入到调试流。</span><span class="sxs-lookup"><span data-stu-id="33be4-137">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="33be4-138">它不会将任何对象写入管道。</span><span class="sxs-lookup"><span data-stu-id="33be4-138">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="33be4-139">注释</span><span class="sxs-lookup"><span data-stu-id="33be4-139">NOTES</span></span>

## <span data-ttu-id="33be4-140">相关链接</span><span class="sxs-lookup"><span data-stu-id="33be4-140">RELATED LINKS</span></span>

[<span data-ttu-id="33be4-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="33be4-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="33be4-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="33be4-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="33be4-143">Write-Error</span><span class="sxs-lookup"><span data-stu-id="33be4-143">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="33be4-144">Write-Host</span><span class="sxs-lookup"><span data-stu-id="33be4-144">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="33be4-145">Write-Output</span><span class="sxs-lookup"><span data-stu-id="33be4-145">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="33be4-146">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="33be4-146">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="33be4-147">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="33be4-147">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="33be4-148">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="33be4-148">Write-Warning</span></span>](Write-Warning.md)
