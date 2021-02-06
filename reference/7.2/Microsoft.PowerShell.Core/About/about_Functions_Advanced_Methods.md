---
description: 描述指定属性的函数如何 `CmdletBinding` 使用可用于已编译 cmdlet 的方法和属性。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596858"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="c52aa-103">关于函数的高级方法</span><span class="sxs-lookup"><span data-stu-id="c52aa-103">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="c52aa-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="c52aa-104">Short description</span></span>

<span data-ttu-id="c52aa-105">描述指定属性的函数如何 `CmdletBinding` 使用可用于已编译 cmdlet 的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="c52aa-105">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="c52aa-106">长说明</span><span class="sxs-lookup"><span data-stu-id="c52aa-106">Long description</span></span>

<span data-ttu-id="c52aa-107">指定特性的函数 `CmdletBinding` 可以通过变量访问多种方法和属性 `$PSCmdlet` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-107">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="c52aa-108">这些方法包括以下方法：</span><span class="sxs-lookup"><span data-stu-id="c52aa-108">These methods include the following methods:</span></span>

- <span data-ttu-id="c52aa-109">已编译的 cmdlet 用于完成其工作的输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-109">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="c52aa-110">`ShouldProcess`用于在 `ShouldContinue` 执行操作之前获取用户反馈的和方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-110">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="c52aa-111">`ThrowTerminatingError`用于生成错误记录的方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-111">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="c52aa-112">`Write`返回不同输出类型的几种方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-112">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="c52aa-113">**PSCmdlet** 类的所有方法和属性都可用于高级函数。</span><span class="sxs-lookup"><span data-stu-id="c52aa-113">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="c52aa-114">有关详细信息，请参阅 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-114">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="c52aa-115">有关属性的详细信息 `CmdletBinding` ，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-115">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="c52aa-116">有关 **CmdletBindingAttribute** 类的详细，请参阅 [CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-116">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="c52aa-117">输入处理方法</span><span class="sxs-lookup"><span data-stu-id="c52aa-117">Input processing methods</span></span>

<span data-ttu-id="c52aa-118">本节中所述的方法称为输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-118">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="c52aa-119">对于函数，这三种方法由函数的 `Begin` 、 `Process` 和 `End` 块表示。</span><span class="sxs-lookup"><span data-stu-id="c52aa-119">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="c52aa-120">不需要在函数中使用这些块中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="c52aa-120">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="c52aa-121">这些块还可用于不使用属性的函数 `CmdletBinding` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-121">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="c52aa-122">开始</span><span class="sxs-lookup"><span data-stu-id="c52aa-122">Begin</span></span>

<span data-ttu-id="c52aa-123">此块用于为函数提供可选的一次性预处理。</span><span class="sxs-lookup"><span data-stu-id="c52aa-123">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="c52aa-124">PowerShell 运行时对管道中的每个函数实例使用一次此块中的代码。</span><span class="sxs-lookup"><span data-stu-id="c52aa-124">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="c52aa-125">过程</span><span class="sxs-lookup"><span data-stu-id="c52aa-125">Process</span></span>

<span data-ttu-id="c52aa-126">此块用于为函数提供按记录处理。</span><span class="sxs-lookup"><span data-stu-id="c52aa-126">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="c52aa-127">您可以使用 `Process` 块，而无需定义其他块。</span><span class="sxs-lookup"><span data-stu-id="c52aa-127">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="c52aa-128">`Process`块执行的次数取决于使用函数的方式和函数接收的输入。</span><span class="sxs-lookup"><span data-stu-id="c52aa-128">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="c52aa-129">自动变量 `$_` 或 `$PSItem` 包含管道中用于块的当前对象 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-129">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="c52aa-130">`$input`自动变量包含一个仅可用于函数和脚本块的枚举器。</span><span class="sxs-lookup"><span data-stu-id="c52aa-130">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="c52aa-131">有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-131">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="c52aa-132">在管道的开头或外部调用函数时，将执行此 `Process` 块一次。</span><span class="sxs-lookup"><span data-stu-id="c52aa-132">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="c52aa-133">在管道中， `Process` 块针对每个到达函数的输入对象执行一次。</span><span class="sxs-lookup"><span data-stu-id="c52aa-133">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="c52aa-134">如果到达函数的管道输入为空，则 `Process` **不会** 执行块。</span><span class="sxs-lookup"><span data-stu-id="c52aa-134">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="c52aa-135">`Begin`和 `End` 块仍在执行。</span><span class="sxs-lookup"><span data-stu-id="c52aa-135">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c52aa-136">如果将某个函数参数设置为接受管道输入，但 `Process` 未定义块，记录记录处理将失败。</span><span class="sxs-lookup"><span data-stu-id="c52aa-136">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="c52aa-137">在这种情况下，无论输入如何，函数都将只执行一次。</span><span class="sxs-lookup"><span data-stu-id="c52aa-137">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="c52aa-138">结束</span><span class="sxs-lookup"><span data-stu-id="c52aa-138">End</span></span>

<span data-ttu-id="c52aa-139">此块用于为函数提供可选的一次性后续处理。</span><span class="sxs-lookup"><span data-stu-id="c52aa-139">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="c52aa-140">下面的示例演示了一个函数的轮廓，该函数包含 `Begin` 一个用于一次性预处理的块、一个 `Process` 用于处理多个记录的块和 `End` 一个用于处理一次性后处理的块。</span><span class="sxs-lookup"><span data-stu-id="c52aa-140">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="c52aa-141">使用 `Begin` 或 `End` 块需要定义所有三个块。</span><span class="sxs-lookup"><span data-stu-id="c52aa-141">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="c52aa-142">使用全部三个块时，所有 PowerShell 代码必须位于一个块内。</span><span class="sxs-lookup"><span data-stu-id="c52aa-142">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="c52aa-143">确认方法</span><span class="sxs-lookup"><span data-stu-id="c52aa-143">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="c52aa-144">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="c52aa-144">ShouldProcess</span></span>

<span data-ttu-id="c52aa-145">在函数执行将更改系统的操作之前，调用此方法来请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="c52aa-145">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="c52aa-146">函数可根据方法返回的布尔值继续。</span><span class="sxs-lookup"><span data-stu-id="c52aa-146">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="c52aa-147">只能从函数块内调用此方法 `Process{}` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-147">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="c52aa-148">`CmdletBinding`特性还必须声明函数支持 `ShouldProcess` (，如前面的示例) 中所示。</span><span class="sxs-lookup"><span data-stu-id="c52aa-148">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="c52aa-149">有关此方法的详细信息，请参阅 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-149">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="c52aa-150">有关如何请求确认的详细信息，请参阅 [请求确认](/powershell/scripting/developer/cmdlet/requesting-confirmation)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-150">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="c52aa-151">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="c52aa-151">ShouldContinue</span></span>

<span data-ttu-id="c52aa-152">调用此方法以请求另一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-152">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="c52aa-153">当方法返回时，应调用此 `ShouldProcess` 方法 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-153">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="c52aa-154">有关此方法的详细信息，请参阅 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-154">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="c52aa-155">错误方法</span><span class="sxs-lookup"><span data-stu-id="c52aa-155">Error methods</span></span>

<span data-ttu-id="c52aa-156">当发生错误时，函数可以调用两种不同的方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-156">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="c52aa-157">当发生非终止错误时，函数应调用 `WriteError` 方法，方法部分对此进行了说明 `Write` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-157">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="c52aa-158">当发生终止错误并且函数无法继续时，它应调用 `ThrowTerminatingError` 方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-158">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="c52aa-159">你还可以使用 `Throw` 语句来终止错误，并使用 [写错误](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet 来实现非终止错误。</span><span class="sxs-lookup"><span data-stu-id="c52aa-159">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="c52aa-160">有关详细信息，请参阅 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-160">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="c52aa-161">写入方法</span><span class="sxs-lookup"><span data-stu-id="c52aa-161">Write methods</span></span>

<span data-ttu-id="c52aa-162">函数可以调用以下方法来返回不同类型的输出。</span><span class="sxs-lookup"><span data-stu-id="c52aa-162">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="c52aa-163">请注意，并非所有输出都转到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="c52aa-163">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="c52aa-164">你还可以使用各种 `Write` cmdlet，例如 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="c52aa-164">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="c52aa-165">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="c52aa-165">WriteCommandDetail</span></span>

<span data-ttu-id="c52aa-166">有关方法的信息 `WriteCommandDetails` ，请参阅 [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-166">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="c52aa-167">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="c52aa-167">WriteDebug</span></span>

<span data-ttu-id="c52aa-168">若要提供可用于排查函数问题的信息，请使函数调用 `WriteDebug` 方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-168">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="c52aa-169">`WriteDebug`方法向用户显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-169">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="c52aa-170">有关详细信息，请参阅 [WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-170">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="c52aa-171">WriteError</span><span class="sxs-lookup"><span data-stu-id="c52aa-171">WriteError</span></span>

<span data-ttu-id="c52aa-172">当发生非终止错误并且函数旨在继续处理记录时，函数应调用此方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-172">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="c52aa-173">有关详细信息，请参阅 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-173">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="c52aa-174">如果发生终止错误，则函数应调用 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-174">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="c52aa-175">WriteObject</span><span class="sxs-lookup"><span data-stu-id="c52aa-175">WriteObject</span></span>

<span data-ttu-id="c52aa-176">`WriteObject`方法允许函数将对象发送到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="c52aa-176">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="c52aa-177">在大多数情况下， `WriteObject` 是在函数返回数据时要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="c52aa-177">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="c52aa-178">有关详细信息，请参阅 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-178">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="c52aa-179">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="c52aa-179">WriteProgress</span></span>

<span data-ttu-id="c52aa-180">对于包含需要很长时间才能完成的操作的函数，此方法允许函数调用方法以 `WriteProgress` 显示进度信息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-180">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="c52aa-181">例如，可以显示已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="c52aa-181">For example, you can display the percent completed.</span></span>
<span data-ttu-id="c52aa-182">有关详细信息，请参阅 [PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-182">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="c52aa-183">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="c52aa-183">WriteVerbose</span></span>

<span data-ttu-id="c52aa-184">若要提供有关函数正在执行的操作的详细信息，请将函数调用 `WriteVerbose` 为向用户显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-184">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="c52aa-185">默认情况下，不显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-185">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="c52aa-186">有关详细信息，请参阅 [PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-186">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="c52aa-187">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="c52aa-187">WriteWarning</span></span>

<span data-ttu-id="c52aa-188">若要提供有关可能会导致意外结果的情况的信息，请使函数调用 WriteWarning 方法来向用户显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-188">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="c52aa-189">默认情况下，会显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-189">By default, warning messages are displayed.</span></span> <span data-ttu-id="c52aa-190">有关详细信息，请参阅 [PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-190">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="c52aa-191">还可以通过配置 `$WarningPreference` 变量或使用 `Verbose` 和 `Debug` 命令行选项来显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="c52aa-191">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="c52aa-192">有关变量的详细信息 `$WarningPreference` ，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-192">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="c52aa-193">其他方法和属性</span><span class="sxs-lookup"><span data-stu-id="c52aa-193">Other methods and properties</span></span>

<span data-ttu-id="c52aa-194">有关可以通过变量访问的其他方法和属性的信息 `$PSCmdlet` ，请参阅 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。</span><span class="sxs-lookup"><span data-stu-id="c52aa-194">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="c52aa-195">例如， [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 属性允许您查看正在使用的参数集。</span><span class="sxs-lookup"><span data-stu-id="c52aa-195">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="c52aa-196">参数集允许您创建一个函数，该函数根据运行函数时指定的参数执行不同的任务。</span><span class="sxs-lookup"><span data-stu-id="c52aa-196">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="c52aa-197">请参阅</span><span class="sxs-lookup"><span data-stu-id="c52aa-197">See also</span></span>

[<span data-ttu-id="c52aa-198">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c52aa-198">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="c52aa-199">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c52aa-199">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="c52aa-200">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="c52aa-200">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="c52aa-201">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="c52aa-201">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="c52aa-202">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c52aa-202">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="c52aa-203">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="c52aa-203">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="c52aa-204">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c52aa-204">about_Preference_Variables</span></span>](about_Preference_Variables.md)

