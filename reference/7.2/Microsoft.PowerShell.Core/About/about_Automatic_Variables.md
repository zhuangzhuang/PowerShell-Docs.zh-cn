---
description: 描述存储 PowerShell 的状态信息的变量。 这些变量由 PowerShell 创建和维护。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: a8959129cc72968ed6e7fcde3587de0d57dbc0e9
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/16/2020
ms.locfileid: "99597068"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="3f194-104">关于自动变量</span><span class="sxs-lookup"><span data-stu-id="3f194-104">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="3f194-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="3f194-105">Short description</span></span>

<span data-ttu-id="3f194-106">描述存储 PowerShell 的状态信息的变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-106">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="3f194-107">这些变量由 PowerShell 创建和维护。</span><span class="sxs-lookup"><span data-stu-id="3f194-107">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3f194-108">长说明</span><span class="sxs-lookup"><span data-stu-id="3f194-108">Long description</span></span>

<span data-ttu-id="3f194-109">从概念上讲，这些变量被视为只读。</span><span class="sxs-lookup"><span data-stu-id="3f194-109">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="3f194-110">即使 **可** 将它们写入到中，但 **不应** 将其写入到后向兼容性。</span><span class="sxs-lookup"><span data-stu-id="3f194-110">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="3f194-111">下面是 PowerShell 中自动变量的列表：</span><span class="sxs-lookup"><span data-stu-id="3f194-111">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="3f194-112">包含会话收到的最后一行中的最后一个标记。</span><span class="sxs-lookup"><span data-stu-id="3f194-112">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="3f194-113">$?</span><span class="sxs-lookup"><span data-stu-id="3f194-113">$?</span></span>

<span data-ttu-id="3f194-114">包含最后一个命令的执行状态。</span><span class="sxs-lookup"><span data-stu-id="3f194-114">Contains the execution status of the last command.</span></span> <span data-ttu-id="3f194-115">如果最后一个命令成功，则 **为 True;** 否则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="3f194-115">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="3f194-116">对于在管道中的多个阶段（例如在和块中）运行的 cmdlet 和高级函数，在 `process` `end` `this.WriteError()` 任何点调用或分别调用或 `$PSCmdlet.WriteError()` 分别将设置 `$?` 为 **False**，就像 `this.ThrowTerminatingError()` 和 `$PSCmdlet.ThrowTerminatingError()` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-116">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False**, as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="3f194-117">`Write-Error`Cmdlet 始终在 `$?` 执行后立即设置为 **false** ，但不会 `$?` 对调用它的函数设置为 **false** ：</span><span class="sxs-lookup"><span data-stu-id="3f194-117">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="3f194-118">对于后一种用途， `$PSCmdlet.WriteError()` 应改为使用。</span><span class="sxs-lookup"><span data-stu-id="3f194-118">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="3f194-119">对于 (可执行文件) 的本机命令， `$?` 当为0时，将设置为 **True** `$LASTEXITCODE` ，如果 `$LASTEXITCODE` 为任何其他值，则设置为 False。</span><span class="sxs-lookup"><span data-stu-id="3f194-119">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="3f194-120">在 PowerShell 7 中，在括号内包含语句后 `(...)` ，子表达式语法 `$(...)` 或数组表达式 `@(...)` 始终重置 `$?` 为 **True**，因此 `(Write-Error)` 显示 `$?` 为 **true**。</span><span class="sxs-lookup"><span data-stu-id="3f194-120">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True**, so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="3f194-121">此操作在 PowerShell 7 中已更改，因此 `$?` 将始终反映在这些表达式中运行的最后一个命令的实际成功。</span><span class="sxs-lookup"><span data-stu-id="3f194-121">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="3f194-122">包含会话收到的最后一行中的第一个标记。</span><span class="sxs-lookup"><span data-stu-id="3f194-122">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="3f194-123">$_</span><span class="sxs-lookup"><span data-stu-id="3f194-123">$_</span></span>

<span data-ttu-id="3f194-124">与 `$PSItem` 相同。</span><span class="sxs-lookup"><span data-stu-id="3f194-124">Same as `$PSItem`.</span></span> <span data-ttu-id="3f194-125">包含管道对象中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-125">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="3f194-126">可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-126">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="3f194-127">$args</span><span class="sxs-lookup"><span data-stu-id="3f194-127">$args</span></span>

<span data-ttu-id="3f194-128">包含传递给函数、脚本或脚本块的未声明参数的值数组。</span><span class="sxs-lookup"><span data-stu-id="3f194-128">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="3f194-129">创建函数时，可以使用 `param` 关键字或在函数名称后的括号中添加以逗号分隔的参数列表，来声明参数。</span><span class="sxs-lookup"><span data-stu-id="3f194-129">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="3f194-130">在事件操作中， `$Args` 变量包含表示正在处理的事件的事件参数的对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-130">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="3f194-131">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-131">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="3f194-132">此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceArgs** 属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-132">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="3f194-133">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="3f194-133">$ConsoleFileName</span></span>

<span data-ttu-id="3f194-134">包含 `.psc1` 会话中最近使用的控制台文件 () 的路径。</span><span class="sxs-lookup"><span data-stu-id="3f194-134">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="3f194-135">使用 **PSConsoleFile** 参数启动 PowerShell 或使用 `Export-Console` cmdlet 将管理单元名称导出到控制台文件时，将填充此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-135">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="3f194-136">使用 `Export-Console` 不带参数的 cmdlet 时，它会自动更新会话中最近使用的控制台文件。</span><span class="sxs-lookup"><span data-stu-id="3f194-136">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="3f194-137">您可以使用此自动变量来确定将更新哪个文件。</span><span class="sxs-lookup"><span data-stu-id="3f194-137">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="3f194-138">$Error</span><span class="sxs-lookup"><span data-stu-id="3f194-138">$Error</span></span>

<span data-ttu-id="3f194-139">包含错误对象的数组，这些对象表示最近的错误。</span><span class="sxs-lookup"><span data-stu-id="3f194-139">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="3f194-140">最近的错误是数组中第一个错误对象 `$Error[0]` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-140">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="3f194-141">若要防止将错误添加到 `$Error` 数组，请使用值为 **Ignore** 的 **ErrorAction** 通用参数。</span><span class="sxs-lookup"><span data-stu-id="3f194-141">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="3f194-142">有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-142">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="3f194-143">$Event</span><span class="sxs-lookup"><span data-stu-id="3f194-143">$Event</span></span>

<span data-ttu-id="3f194-144">包含表示正在处理的事件的 **PSEventArgs** 对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-144">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="3f194-145">此变量仅在 `Action` 事件注册命令块中填充，例如 `Register-ObjectEvent` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-145">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="3f194-146">此变量的值与 cmdlet 返回的对象相同 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-146">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="3f194-147">因此，可以 `Event` `$Event.TimeGenerated` 在脚本块中使用该变量的属性，例如 `Action` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-147">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="3f194-148">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="3f194-148">$EventArgs</span></span>

<span data-ttu-id="3f194-149">包含一个对象，该对象表示从正在处理的事件的 **EventArgs** 派生的第一个事件参数。</span><span class="sxs-lookup"><span data-stu-id="3f194-149">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="3f194-150">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-150">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="3f194-151">此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceEventArgs** 属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-151">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="3f194-152">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="3f194-152">$EventSubscriber</span></span>

<span data-ttu-id="3f194-153">包含一个 **PSEventSubscriber** 对象，该对象表示正在处理的事件的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="3f194-153">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="3f194-154">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-154">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="3f194-155">此变量的值与 cmdlet 返回的对象相同 `Get-EventSubscriber` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-155">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="3f194-156">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="3f194-156">$ExecutionContext</span></span>

<span data-ttu-id="3f194-157">包含一个 **EngineIntrinsics** 对象，该对象表示 PowerShell 主机的执行上下文。</span><span class="sxs-lookup"><span data-stu-id="3f194-157">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="3f194-158">您可以使用此变量来查找可用于 cmdlet 的执行对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-158">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="3f194-159">$false</span><span class="sxs-lookup"><span data-stu-id="3f194-159">$false</span></span>

<span data-ttu-id="3f194-160">包含 **False**。</span><span class="sxs-lookup"><span data-stu-id="3f194-160">Contains **False**.</span></span> <span data-ttu-id="3f194-161">可以在命令和脚本中使用此变量来表示 **False** ，而不是使用字符串 "False"。</span><span class="sxs-lookup"><span data-stu-id="3f194-161">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="3f194-162">如果字符串被转换为非空字符串或非零整数，则可以将该字符串解释为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="3f194-162">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="3f194-163">$foreach</span><span class="sxs-lookup"><span data-stu-id="3f194-163">$foreach</span></span>

<span data-ttu-id="3f194-164">包含枚举器 (不是 [ForEach](about_ForEach.md) 循环) 的结果值。</span><span class="sxs-lookup"><span data-stu-id="3f194-164">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="3f194-165">此 `$ForEach` 变量仅在 `ForEach` 循环运行时存在; 在循环完成后将其删除。</span><span class="sxs-lookup"><span data-stu-id="3f194-165">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="3f194-166">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-166">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3f194-167">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="3f194-167">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="3f194-168">$HOME</span><span class="sxs-lookup"><span data-stu-id="3f194-168">$HOME</span></span>

<span data-ttu-id="3f194-169">包含用户的主目录的完整路径。</span><span class="sxs-lookup"><span data-stu-id="3f194-169">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="3f194-170">通常，此变量等效于 `"$env:homedrive$env:homepath"` Windows 环境变量 `C:\Users\<UserName>` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-170">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="3f194-171">$Host</span><span class="sxs-lookup"><span data-stu-id="3f194-171">$Host</span></span>

<span data-ttu-id="3f194-172">包含表示 PowerShell 的当前主机应用程序的对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-172">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="3f194-173">您可以使用此变量来表示命令中的当前宿主，或者显示或更改主机的属性，例如 `$Host.version` 或 `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-173">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="3f194-174">$input</span><span class="sxs-lookup"><span data-stu-id="3f194-174">$input</span></span>

<span data-ttu-id="3f194-175">包含枚举传递到函数的所有输入的枚举器。</span><span class="sxs-lookup"><span data-stu-id="3f194-175">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="3f194-176">此 `$input` 变量仅适用于) 为未命名函数 (函数和脚本块。</span><span class="sxs-lookup"><span data-stu-id="3f194-176">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="3f194-177">在没有 `Begin` 、或块的函数中 `Process` `End` ， `$input` 变量枚举函数的所有输入的集合。</span><span class="sxs-lookup"><span data-stu-id="3f194-177">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="3f194-178">在 `Begin` 块中， `$input` 变量不包含任何数据。</span><span class="sxs-lookup"><span data-stu-id="3f194-178">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="3f194-179">在 `Process` 块中， `$input` 变量包含管道中当前的对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-179">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="3f194-180">在 `End` 块中， `$input` 变量枚举函数的所有输入的集合。</span><span class="sxs-lookup"><span data-stu-id="3f194-180">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3f194-181">不能 `$input` 在同一函数或脚本块中的进程块和结束块中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-181">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="3f194-182">由于 `$input` 是一个枚举器，因此访问它的任何属性都将导致 `$input` 不再可用。</span><span class="sxs-lookup"><span data-stu-id="3f194-182">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="3f194-183">可以 `$input` 在另一个变量中存储以重用 `$input` 属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-183">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="3f194-184">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-184">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3f194-185">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="3f194-185">For more information, see [Using Enumerators](#using-enumerators).</span></span>

<span data-ttu-id="3f194-186">`$input` `-Command` `pwsh` 当从命令行调用时，该变量也可用于由的参数指定的命令。</span><span class="sxs-lookup"><span data-stu-id="3f194-186">The `$input` variable is also available to the command specified by the `-Command` parameter of `pwsh` when invoked from the command line.</span></span> <span data-ttu-id="3f194-187">下面的示例从 Windows 命令行界面运行。</span><span class="sxs-lookup"><span data-stu-id="3f194-187">The following example is run from the Windows Command shell.</span></span>

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a><span data-ttu-id="3f194-188">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="3f194-188">$IsCoreCLR</span></span>

<span data-ttu-id="3f194-189">包含 `$True` 当前会话是否在 .Net Core 运行时上运行 (CoreCLR) 。</span><span class="sxs-lookup"><span data-stu-id="3f194-189">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="3f194-190">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-190">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="3f194-191">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="3f194-191">$IsLinux</span></span>

<span data-ttu-id="3f194-192">包含 `$True` 当前会话是否在 Linux 操作系统上运行。</span><span class="sxs-lookup"><span data-stu-id="3f194-192">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="3f194-193">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-193">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="3f194-194">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="3f194-194">$IsMacOS</span></span>

<span data-ttu-id="3f194-195">包含 `$True` 当前会话是否在 MacOS 操作系统上运行的。</span><span class="sxs-lookup"><span data-stu-id="3f194-195">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="3f194-196">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-196">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="3f194-197">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="3f194-197">$IsWindows</span></span>

<span data-ttu-id="3f194-198">`$TRUE`如果当前会话正在 Windows 操作系统上运行，则包含。</span><span class="sxs-lookup"><span data-stu-id="3f194-198">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="3f194-199">否则包含 `$FALSE` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-199">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="3f194-200">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="3f194-200">$LastExitCode</span></span>

<span data-ttu-id="3f194-201">包含上一次运行的基于 Windows 的程序的退出代码。</span><span class="sxs-lookup"><span data-stu-id="3f194-201">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="3f194-202">$Matches</span><span class="sxs-lookup"><span data-stu-id="3f194-202">$Matches</span></span>

<span data-ttu-id="3f194-203">`Matches`变量与 `-match` and 运算符一起使用 `-notmatch` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-203">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="3f194-204">当你将标量输入提交给 `-match` or `-notmatch` 运算符，并且其中一个检测到匹配时，它们将返回一个布尔值，并 `$Matches` 使用匹配的任何字符串值的哈希表填充自动变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-204">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="3f194-205">在 `$Matches` 将正则表达式用于运算符时，还可以使用捕获来填充哈希表 `-match` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-205">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="3f194-206">有关运算符的详细信息 `-match` ，请参阅 [about_Comparison_Operators](about_comparison_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-206">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="3f194-207">有关正则表达式的详细信息，请参阅 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-207">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="3f194-208">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="3f194-208">$MyInvocation</span></span>

<span data-ttu-id="3f194-209">包含有关当前命令的信息，如名称、参数、参数值和有关如何启动、调用或调用命令的信息，例如调用当前命令的脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="3f194-209">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="3f194-210">`$MyInvocation` 仅填充脚本、函数和脚本块。</span><span class="sxs-lookup"><span data-stu-id="3f194-210">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="3f194-211">您可以使用在当前脚本中返回的 **InvocationInfo** 对象中的信息 `$MyInvocation` ，例如脚本 () 的路径和文件名， `$MyInvocation.MyCommand.Path` 或函数的名称 (`$MyInvocation.MyCommand.Name`) 以标识当前命令。</span><span class="sxs-lookup"><span data-stu-id="3f194-211">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="3f194-212">这对于查找当前脚本的名称特别有用。</span><span class="sxs-lookup"><span data-stu-id="3f194-212">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="3f194-213">从 PowerShell 3.0 开始， `MyInvocation` 具有以下新属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-213">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

- <span data-ttu-id="3f194-214">**PSScriptRoot** -包含调用当前命令的脚本的完整路径。</span><span class="sxs-lookup"><span data-stu-id="3f194-214">**PSScriptRoot** - Contains the full path to the script that invoked the current command.</span></span> <span data-ttu-id="3f194-215">仅当调用方为脚本时，才填充此属性的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-215">The value of this property is populated only when the caller is a script.</span></span>
- <span data-ttu-id="3f194-216">**PSCommandPath** -包含调用当前命令的脚本的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="3f194-216">**PSCommandPath** - Contains the full path and file name of the script that invoked the current command.</span></span> <span data-ttu-id="3f194-217">仅当调用方为脚本时，才填充此属性的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-217">The value of this property is populated only when the caller is a script.</span></span>

<span data-ttu-id="3f194-218">与自动变量不同 `$PSScriptRoot` `$PSCommandPath` ，自动变量的 **PSScriptRoot** 和 **PSCommandPath** 属性 `$MyInvocation` 包含有关调用程序或调用脚本的信息，而不是当前脚本。</span><span class="sxs-lookup"><span data-stu-id="3f194-218">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="3f194-219">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="3f194-219">$NestedPromptLevel</span></span>

<span data-ttu-id="3f194-220">包含当前提示符级别。</span><span class="sxs-lookup"><span data-stu-id="3f194-220">Contains the current prompt level.</span></span> <span data-ttu-id="3f194-221">值0表示原始提示级别。</span><span class="sxs-lookup"><span data-stu-id="3f194-221">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="3f194-222">当您输入嵌套级别时，该值会递增，并且在您退出时将递增。</span><span class="sxs-lookup"><span data-stu-id="3f194-222">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="3f194-223">例如，使用方法时，PowerShell 会显示嵌套的命令提示符 `$Host.EnterNestedPrompt` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-223">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="3f194-224">当你到达 PowerShell 调试器中的断点时，PowerShell 还会显示嵌套的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="3f194-224">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="3f194-225">输入嵌套提示符时，PowerShell 将暂停当前命令，保存执行上下文，并递增变量的值 `$NestedPromptLevel` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-225">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="3f194-226">若要创建其他嵌套的命令提示 (最多128级别) 或返回到原始命令提示符，请完成命令或键入 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-226">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="3f194-227">`$NestedPromptLevel`变量有助于跟踪提示级别。</span><span class="sxs-lookup"><span data-stu-id="3f194-227">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="3f194-228">你可以创建一个包含此值的备用 PowerShell 命令提示符，以使其始终可见。</span><span class="sxs-lookup"><span data-stu-id="3f194-228">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="3f194-229">$null</span><span class="sxs-lookup"><span data-stu-id="3f194-229">$null</span></span>

<span data-ttu-id="3f194-230">`$null` 是包含 **null** 值或空值的自动变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-230">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="3f194-231">您可以使用此变量来表示命令和脚本中缺少的值或未定义的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-231">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="3f194-232">PowerShell 将视为 `$null` 具有值的对象（即，作为显式占位符），因此可以使用 `$null` 来表示一系列值中的空值。</span><span class="sxs-lookup"><span data-stu-id="3f194-232">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="3f194-233">例如，当 `$null` 包含在集合中时，会将其计为一个对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-233">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="3f194-234">如果通过管道将 `$null` 变量传递给 `ForEach-Object` cmdlet，它会为生成一个值 `$null` ，就像对其他对象执行此方法一样。</span><span class="sxs-lookup"><span data-stu-id="3f194-234">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="3f194-235">因此，不能使用 `$null` 来表示 **没有参数值**。</span><span class="sxs-lookup"><span data-stu-id="3f194-235">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="3f194-236">参数值 `$null` 覆盖默认参数值。</span><span class="sxs-lookup"><span data-stu-id="3f194-236">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="3f194-237">但是，因为 PowerShell 将 `$null` 变量视为占位符，所以可以在脚本中使用它，如果忽略，这将不起作用 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-237">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="3f194-238">$PID</span><span class="sxs-lookup"><span data-stu-id="3f194-238">$PID</span></span>

<span data-ttu-id="3f194-239">包含承载当前 PowerShell 会话的进程的进程标识符 (PID) 。</span><span class="sxs-lookup"><span data-stu-id="3f194-239">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="3f194-240">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="3f194-240">$PROFILE</span></span>

<span data-ttu-id="3f194-241">包含当前用户和当前主机应用程序的 PowerShell 配置文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="3f194-241">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="3f194-242">您可以使用此变量来表示命令中的配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f194-242">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="3f194-243">例如，你可以在命令中使用它来确定是否已创建配置文件：</span><span class="sxs-lookup"><span data-stu-id="3f194-243">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="3f194-244">或者，你可以在命令中使用它来创建配置文件：</span><span class="sxs-lookup"><span data-stu-id="3f194-244">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="3f194-245">可以在命令中使用它在 **notepad.exe** 中打开配置文件：</span><span class="sxs-lookup"><span data-stu-id="3f194-245">You can use it in a command to open the profile in **notepad.exe**:</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="3f194-246">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="3f194-246">$PSBoundParameters</span></span>

<span data-ttu-id="3f194-247">包含传递给脚本或函数的参数的字典及其当前值。</span><span class="sxs-lookup"><span data-stu-id="3f194-247">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="3f194-248">此变量仅在声明参数的作用域（如脚本或函数）中具有值。</span><span class="sxs-lookup"><span data-stu-id="3f194-248">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="3f194-249">您可以使用它显示或更改参数的当前值，或者将参数值传递给其他脚本或函数。</span><span class="sxs-lookup"><span data-stu-id="3f194-249">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="3f194-250">在此示例中， **Test2** 函数将传递 `$PSBoundParameters` 给 **Test1** 函数。</span><span class="sxs-lookup"><span data-stu-id="3f194-250">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="3f194-251">`$PSBoundParameters`以 **键** 和 **值** 的格式显示。</span><span class="sxs-lookup"><span data-stu-id="3f194-251">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="3f194-252">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="3f194-252">$PSCmdlet</span></span>

<span data-ttu-id="3f194-253">包含一个对象，该对象表示正在运行的 cmdlet 或高级函数。</span><span class="sxs-lookup"><span data-stu-id="3f194-253">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="3f194-254">你可以使用 cmdlet 或函数代码中的对象的属性和方法来响应使用情况。</span><span class="sxs-lookup"><span data-stu-id="3f194-254">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="3f194-255">例如， **ParameterSetName** 属性包含所使用的参数集的名称， **ShouldProcess** 方法会动态地将 **WhatIf** 和 **Confirm** 参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f194-255">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="3f194-256">有关自动变量的详细信息 `$PSCmdlet` ，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-256">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="3f194-257">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="3f194-257">$PSCommandPath</span></span>

<span data-ttu-id="3f194-258">包含正在运行的脚本的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="3f194-258">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="3f194-259">此变量在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="3f194-259">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="3f194-260">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="3f194-260">$PSCulture</span></span>

<span data-ttu-id="3f194-261">从 PowerShell 7 开始， `$PSCulture` 反映当前 PowerShell 运行空间的区域性 (会话) 。</span><span class="sxs-lookup"><span data-stu-id="3f194-261">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="3f194-262">如果在 PowerShell 运行空间中更改了区域性，则将 `$PSCulture` 更新该运行空间的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-262">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="3f194-263">区域性确定项的显示格式（例如数字、货币和日期），并将其存储在 **system.exception 对象中。**</span><span class="sxs-lookup"><span data-stu-id="3f194-263">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="3f194-264">用于 `Get-Culture` 显示计算机的区域性。</span><span class="sxs-lookup"><span data-stu-id="3f194-264">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="3f194-265">`$PSCulture` 包含 **名称** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-265">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="3f194-266">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="3f194-266">$PSDebugContext</span></span>

<span data-ttu-id="3f194-267">调试时，此变量包含有关调试环境的信息。</span><span class="sxs-lookup"><span data-stu-id="3f194-267">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="3f194-268">否则，它将包含 **null** 值。</span><span class="sxs-lookup"><span data-stu-id="3f194-268">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="3f194-269">因此，你可以使用它来指示调试器是否具有控件。</span><span class="sxs-lookup"><span data-stu-id="3f194-269">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="3f194-270">填充后，它将包含一个 **PsDebugContext** 对象，该对象具有 **断点** 和 **InvocationInfo** 属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-270">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="3f194-271">**InvocationInfo** 属性具有多个有用的属性，包括 **Location** 属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-271">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="3f194-272">**Location** 属性指示正在调试的脚本的路径。</span><span class="sxs-lookup"><span data-stu-id="3f194-272">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="3f194-273">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="3f194-273">$PSHOME</span></span>

<span data-ttu-id="3f194-274">包含适用于 PowerShell 的安装目录的完整路径，通常是 `$env:windir\System32\PowerShell\v1.0` 在 Windows 系统中。</span><span class="sxs-lookup"><span data-stu-id="3f194-274">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="3f194-275">可以在 PowerShell 文件的路径中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-275">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="3f194-276">例如，下面的命令在概念帮助主题中搜索 word **变量**：</span><span class="sxs-lookup"><span data-stu-id="3f194-276">For example, the following command searches the conceptual Help topics for the word **variable**:</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="3f194-277">$PSItem</span><span class="sxs-lookup"><span data-stu-id="3f194-277">$PSItem</span></span>

<span data-ttu-id="3f194-278">与 `$_` 相同。</span><span class="sxs-lookup"><span data-stu-id="3f194-278">Same as `$_`.</span></span> <span data-ttu-id="3f194-279">包含管道对象中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-279">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="3f194-280">可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-280">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="3f194-281">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="3f194-281">$PSScriptRoot</span></span>

<span data-ttu-id="3f194-282">包含正在从中运行脚本的目录。</span><span class="sxs-lookup"><span data-stu-id="3f194-282">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="3f194-283">在 PowerShell 2.0 中，此变量仅在) 的脚本模块中有效 (`.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-283">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="3f194-284">从 PowerShell 3.0 开始，它在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="3f194-284">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="3f194-285">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="3f194-285">$PSSenderInfo</span></span>

<span data-ttu-id="3f194-286">包含有关启动 PSSession 的用户的信息，其中包括源计算机的用户标识和时区。</span><span class="sxs-lookup"><span data-stu-id="3f194-286">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="3f194-287">此变量仅在 Pssession 中可用。</span><span class="sxs-lookup"><span data-stu-id="3f194-287">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="3f194-288">此 `$PSSenderInfo` 变量包含一个用户可配置的属性 **ApplicationArguments**，默认情况下，该属性仅包含 `$PSVersionTable` 来自原始会话的。</span><span class="sxs-lookup"><span data-stu-id="3f194-288">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments**, that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="3f194-289">若要将数据添加到 **ApplicationArguments** 属性，请使用 Cmdlet 的 **ApplicationArguments** 参数 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-289">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psstyle"></a><span data-ttu-id="3f194-290">$PSStyle</span><span class="sxs-lookup"><span data-stu-id="3f194-290">$PSStyle</span></span>

> [!NOTE]
> <span data-ttu-id="3f194-291">此变量仅在 `PSAnsiRendering` 实验功能 ia 启用时可用。</span><span class="sxs-lookup"><span data-stu-id="3f194-291">This variable is only available when the `PSAnsiRendering` experimental feature ia enabled.</span></span> <span data-ttu-id="3f194-292">有关详细信息，请参阅 [about_Experimental_Features](about_Experimental_Features.md) 和 [使用实验性功能](/powershell/scripting/learn/experimental-features)。</span><span class="sxs-lookup"><span data-stu-id="3f194-292">For more information, see [about_Experimental_Features](about_Experimental_Features.md) and [Using experimental features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="3f194-293">从 PowerShell 7.2 开始，你现在可以访问 `$PSStyle` 自动变量以查看和更改 ANSI 字符串输出的呈现。</span><span class="sxs-lookup"><span data-stu-id="3f194-293">As of PowerShell 7.2 you can now access the `$PSStyle` automatic variable to view and change the rendering of ANSI string output.</span></span> <span data-ttu-id="3f194-294">变量包含以下属性：</span><span class="sxs-lookup"><span data-stu-id="3f194-294">The variable contains the following properties:</span></span>

- <span data-ttu-id="3f194-295">**重置** -关闭所有修饰</span><span class="sxs-lookup"><span data-stu-id="3f194-295">**Reset** - Turns off all decorations</span></span>
- <span data-ttu-id="3f194-296">用于控制背景颜色的 **背景** 嵌套对象</span><span class="sxs-lookup"><span data-stu-id="3f194-296">**Background** - Nested object to control background coloring</span></span>
- <span data-ttu-id="3f194-297">**闪烁** -闪烁</span><span class="sxs-lookup"><span data-stu-id="3f194-297">**Blink** - Turns Blink on</span></span>
- <span data-ttu-id="3f194-298">**BlinkOff** -关闭闪烁</span><span class="sxs-lookup"><span data-stu-id="3f194-298">**BlinkOff** - Turns Blink off</span></span>
- <span data-ttu-id="3f194-299">**加粗** -打开粗体</span><span class="sxs-lookup"><span data-stu-id="3f194-299">**Bold** - Turns Bold on</span></span>
- <span data-ttu-id="3f194-300">**BoldOff** -关闭粗体</span><span class="sxs-lookup"><span data-stu-id="3f194-300">**BoldOff** - Turns Bold off</span></span>
- <span data-ttu-id="3f194-301">用于控制前景颜色的 **前景** 嵌套对象</span><span class="sxs-lookup"><span data-stu-id="3f194-301">**Foreground** - Nested object to control foreground coloring</span></span>
- <span data-ttu-id="3f194-302">**格式设置** -控制输出流的默认格式设置</span><span class="sxs-lookup"><span data-stu-id="3f194-302">**Formatting** - Controls default formatting for output streams</span></span>
- <span data-ttu-id="3f194-303">**隐藏** -打开隐藏</span><span class="sxs-lookup"><span data-stu-id="3f194-303">**Hidden** - Turns Hidden on</span></span>
- <span data-ttu-id="3f194-304">**HiddenOff** -关闭隐藏</span><span class="sxs-lookup"><span data-stu-id="3f194-304">**HiddenOff** - Turns Hidden off</span></span>
- <span data-ttu-id="3f194-305">**OutputRendering** -在使用输出呈现时进行控制</span><span class="sxs-lookup"><span data-stu-id="3f194-305">**OutputRendering** - Control when output rendering is used</span></span>
- <span data-ttu-id="3f194-306">**反向** 转换</span><span class="sxs-lookup"><span data-stu-id="3f194-306">**Reverse** - Turns Reverse on</span></span>
- <span data-ttu-id="3f194-307">**ReverseOff** -关闭反转</span><span class="sxs-lookup"><span data-stu-id="3f194-307">**ReverseOff** - Turns Reverse off</span></span>
- <span data-ttu-id="3f194-308">**斜体** -打开斜体</span><span class="sxs-lookup"><span data-stu-id="3f194-308">**Italic** - Turns Italic on</span></span>
- <span data-ttu-id="3f194-309">**ItalicOff** -关闭斜体</span><span class="sxs-lookup"><span data-stu-id="3f194-309">**ItalicOff** - Turns Italic off</span></span>
- <span data-ttu-id="3f194-310">**下划线** -启用下划线</span><span class="sxs-lookup"><span data-stu-id="3f194-310">**Underline** - Turns underlining on</span></span>
- <span data-ttu-id="3f194-311">**UnderlineOff** -关闭下划线</span><span class="sxs-lookup"><span data-stu-id="3f194-311">**UnderlineOff** - Turns underlining off</span></span>

<span data-ttu-id="3f194-312">基成员会返回映射到其名称的 ANSI 转义序列的字符串。</span><span class="sxs-lookup"><span data-stu-id="3f194-312">The base members return strings of ANSI escape sequences mapped to their names.</span></span>
<span data-ttu-id="3f194-313">值可设置为允许自定义。</span><span class="sxs-lookup"><span data-stu-id="3f194-313">The values are settable to allow customization.</span></span> <span data-ttu-id="3f194-314">例如，可以将粗体更改为带下划线。</span><span class="sxs-lookup"><span data-stu-id="3f194-314">For example, you could change bold to underlined.</span></span> <span data-ttu-id="3f194-315">属性名称使你可以更轻松地使用 tab 自动补全创建修饰字符串：</span><span class="sxs-lookup"><span data-stu-id="3f194-315">The property names makes it easier for you to create decorated strings using tab completion:</span></span>

```powershell
"$($PSStyle.Background.LightCyan)Power$($PSStyle.Underline)$($PSStyle.Bold)Shell$($PSStyle.Reset)"
```

<span data-ttu-id="3f194-316">`$PSStyle.Background`和 `$PSStyle.Foreground` 成员是包含16种标准控制台颜色的 ANSI 转义序列的字符串，以及 `Rgb()` 用于指定24位颜色的方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-316">The `$PSStyle.Background` and `$PSStyle.Foreground` members are strings that contain the ANSI escape sequences for the 16 standard console colors as well as an `Rgb()` method to specify 24-bit color.</span></span> <span data-ttu-id="3f194-317">这些值是可设置的，可以包含任意数量的 ANSI 转义序列。</span><span class="sxs-lookup"><span data-stu-id="3f194-317">The values are settable and can contain any number of ANSI escape sequences.</span></span>

<span data-ttu-id="3f194-318">`$PSStyle.Formatting` 是一个嵌套对象，用于控制调试、错误、详细和警告消息的默认格式设置。</span><span class="sxs-lookup"><span data-stu-id="3f194-318">`$PSStyle.Formatting` is a nested object to control default formatting of debug, error, verbose, and warning messages.</span></span> <span data-ttu-id="3f194-319">还可以控制粗体和下划线等属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-319">You can also control attributes like bolding and underlining.</span></span> <span data-ttu-id="3f194-320">它将替换 `$Host.PrivateData` 为用于管理格式呈现的颜色的方式。</span><span class="sxs-lookup"><span data-stu-id="3f194-320">It replaces `$Host.PrivateData` as the way to manage colors for formatting rendering.</span></span> <span data-ttu-id="3f194-321">`$Host.PrivateData` 继续存在，以实现向后兼容，但不连接到 `$PSStyle.Formatting` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-321">`$Host.PrivateData` continues to exist for backwards compatibility but is not connected to `$PSStyle.Formatting`.</span></span>

<span data-ttu-id="3f194-322">`$PSStyle.OutputRendering` 是 `System.Management.Automation.OutputRendering` 具有以下值的枚举：</span><span class="sxs-lookup"><span data-stu-id="3f194-322">`$PSStyle.OutputRendering` is a `System.Management.Automation.OutputRendering` enum with the values:</span></span>

- <span data-ttu-id="3f194-323">**自动**：这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="3f194-323">**Automatic**: This is the default.</span></span> <span data-ttu-id="3f194-324">如果主机支持 VirtualTerminal，则 ANSI 始终按原样传递，否则为纯文本</span><span class="sxs-lookup"><span data-stu-id="3f194-324">If the host supports VirtualTerminal, then ANSI is always passed as-is, otherwise plaintext</span></span>
- <span data-ttu-id="3f194-325">**Ansi**： ansi 始终按原样传递</span><span class="sxs-lookup"><span data-stu-id="3f194-325">**ANSI**: ANSI is always passed through as-is</span></span>
- <span data-ttu-id="3f194-326">**纯** 文本：始终去除 ANSI 转义序列，使其只是纯文本</span><span class="sxs-lookup"><span data-stu-id="3f194-326">**PlainText**: ANSI escape sequences are always stripped so that it is only plain text</span></span>
- <span data-ttu-id="3f194-327">**HostOnly**：这是 macOS 行为，其中 ANSI 转义序列在重定向或管道输出中被删除。</span><span class="sxs-lookup"><span data-stu-id="3f194-327">**HostOnly**: This would be the macOS behavior where the ANSI escape sequences are removed in redirected or piped output.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="3f194-328">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="3f194-328">$PSUICulture</span></span>

<span data-ttu-id="3f194-329">包含操作系统中当前正在使用的 (UI) 区域性的用户界面的名称。</span><span class="sxs-lookup"><span data-stu-id="3f194-329">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="3f194-330">UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。</span><span class="sxs-lookup"><span data-stu-id="3f194-330">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="3f194-331">这是系统的 **System.Globalization.CultureInfo.CurrentUICulture.Name** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-331">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="3f194-332">若要获取 **系统的 system.servicemodel 对象，** 请使用 `Get-UICulture` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f194-332">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="3f194-333">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="3f194-333">$PSVersionTable</span></span>

<span data-ttu-id="3f194-334">包含一个只读的哈希表，该表显示有关当前会话中正在运行的 PowerShell 版本的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3f194-334">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="3f194-335">该表包含以下各项：</span><span class="sxs-lookup"><span data-stu-id="3f194-335">The table includes the following items:</span></span>

- <span data-ttu-id="3f194-336">**PSVersion** -PowerShell 版本号</span><span class="sxs-lookup"><span data-stu-id="3f194-336">**PSVersion** - The PowerShell version number</span></span>
- <span data-ttu-id="3f194-337">**PSEdition** -此属性具有适用于 powershell 4 和更低版本的 "Desktop" 的值，以及适用于功能完备的 Windows 版本的 powershell 5.1。</span><span class="sxs-lookup"><span data-stu-id="3f194-337">**PSEdition** - This property has the value of 'Desktop' for PowerShell 4 and below as well as PowerShell 5.1 on full-featured Windows editions.</span></span> <span data-ttu-id="3f194-338">此属性的值为 PowerShell 6 及更高版本，以及 Windows Nano Server 或 Windows IoT 等减少的占用空间版本上的 PowerShell PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="3f194-338">This property has the value of 'Core' for PowerShell 6 and above as well as PowerShell PowerShell 5.1 on reduced-footprint editions like Windows Nano Server or Windows IoT.</span></span>
- <span data-ttu-id="3f194-339">**GitCommitId** -源文件（GitHub）中的提交 Id</span><span class="sxs-lookup"><span data-stu-id="3f194-339">**GitCommitId** - The commit Id of the source files, in GitHub,</span></span>
- <span data-ttu-id="3f194-340">**OS** -运行 PowerShell 的操作系统的描述。</span><span class="sxs-lookup"><span data-stu-id="3f194-340">**OS** - Description of the operating system that PowerShell is running on.</span></span>
- <span data-ttu-id="3f194-341">运行操作系统的 **平台** 平台。</span><span class="sxs-lookup"><span data-stu-id="3f194-341">**Platform** - Platform that the operating system is running on.</span></span> <span data-ttu-id="3f194-342">Linux 和 macOS 上的值为 **Unix**。</span><span class="sxs-lookup"><span data-stu-id="3f194-342">The value on Linux and macOS is **Unix**.</span></span> <span data-ttu-id="3f194-343">请参见 `$IsMacOs` 和 `$IsLinux`。</span><span class="sxs-lookup"><span data-stu-id="3f194-343">See `$IsMacOs` and `$IsLinux`.</span></span>
- <span data-ttu-id="3f194-344">**PSCompatibleVersions** -与当前版本兼容的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="3f194-344">**PSCompatibleVersions** - Versions of PowerShell that are compatible with the current version</span></span>
- <span data-ttu-id="3f194-345">**PSRemotingProtocolVersion** -PowerShell 远程管理协议的版本。</span><span class="sxs-lookup"><span data-stu-id="3f194-345">**PSRemotingProtocolVersion** - The version of the PowerShell remote management protocol.</span></span>
- <span data-ttu-id="3f194-346">**SerializationVersion** -序列化方法的版本</span><span class="sxs-lookup"><span data-stu-id="3f194-346">**SerializationVersion** - The version of the serialization method</span></span>
- <span data-ttu-id="3f194-347">**WSManStackVersion** -WS-Management 堆栈的版本号</span><span class="sxs-lookup"><span data-stu-id="3f194-347">**WSManStackVersion** - The version number of the WS-Management stack</span></span>

### <a name="pwd"></a><span data-ttu-id="3f194-348">$PWD</span><span class="sxs-lookup"><span data-stu-id="3f194-348">$PWD</span></span>

<span data-ttu-id="3f194-349">包含表示当前目录的完整路径的路径对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-349">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="3f194-350">$Sender</span><span class="sxs-lookup"><span data-stu-id="3f194-350">$Sender</span></span>

<span data-ttu-id="3f194-351">包含生成此事件的对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-351">Contains the object that generated this event.</span></span> <span data-ttu-id="3f194-352">此变量仅在事件注册命令的操作块中进行填充。</span><span class="sxs-lookup"><span data-stu-id="3f194-352">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="3f194-353">此变量的值还可在返回的 **PSEventArgs** 对象的发送方属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-353">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="3f194-354">$ShellId</span><span class="sxs-lookup"><span data-stu-id="3f194-354">$ShellId</span></span>

<span data-ttu-id="3f194-355">包含当前 shell 的标识符。</span><span class="sxs-lookup"><span data-stu-id="3f194-355">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="3f194-356">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="3f194-356">$StackTrace</span></span>

<span data-ttu-id="3f194-357">包含最新错误的堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="3f194-357">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="3f194-358">$switch</span><span class="sxs-lookup"><span data-stu-id="3f194-358">$switch</span></span>

<span data-ttu-id="3f194-359">包含枚举器，而不包含语句的结果值 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-359">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="3f194-360">`$switch`仅当语句正在运行时，才存在该变量 `Switch` ; 当语句完成执行时，该变量会被删除 `switch` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-360">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="3f194-361">有关详细信息，请参阅 [about_Switch](about_Switch.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-361">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="3f194-362">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-362">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3f194-363">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="3f194-363">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="3f194-364">$this</span><span class="sxs-lookup"><span data-stu-id="3f194-364">$this</span></span>

<span data-ttu-id="3f194-365">在定义脚本属性或脚本方法的脚本块中， `$this` 变量引用要扩展的对象。</span><span class="sxs-lookup"><span data-stu-id="3f194-365">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="3f194-366">在自定义类中， `$this` 变量引用类对象本身，以允许访问类中定义的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-366">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="3f194-367">$true</span><span class="sxs-lookup"><span data-stu-id="3f194-367">$true</span></span>

<span data-ttu-id="3f194-368">包含 **True**。</span><span class="sxs-lookup"><span data-stu-id="3f194-368">Contains **True**.</span></span> <span data-ttu-id="3f194-369">可以在命令和脚本中使用此变量来表示 **True** 。</span><span class="sxs-lookup"><span data-stu-id="3f194-369">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="3f194-370">使用枚举器</span><span class="sxs-lookup"><span data-stu-id="3f194-370">Using Enumerators</span></span>

<span data-ttu-id="3f194-371">`$input`、 `$foreach` 和 `$switch` 变量是所有枚举器，用于循环访问由其包含代码块处理的值。</span><span class="sxs-lookup"><span data-stu-id="3f194-371">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="3f194-372">枚举器包含可用于提前或重置迭代或检索迭代值的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-372">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="3f194-373">直接操作枚举器并不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3f194-373">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="3f194-374">在循环中，应首选流控制关键字 " [中断](about_Break.md) 并 [继续](about_Continue.md) "。</span><span class="sxs-lookup"><span data-stu-id="3f194-374">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="3f194-375">在接受管道输入的函数中，最佳做法是将参数与 **ValueFromPipeline** 或 **ValueFromPipelineByPropertyName** 属性结合使用。</span><span class="sxs-lookup"><span data-stu-id="3f194-375">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="3f194-376">有关详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3f194-376">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="3f194-377">MoveNext</span><span class="sxs-lookup"><span data-stu-id="3f194-377">MoveNext</span></span>

<span data-ttu-id="3f194-378">[MoveNext](/dotnet/api/system.collections.ienumerator.movenext)方法将枚举器推进到集合的下一个元素。</span><span class="sxs-lookup"><span data-stu-id="3f194-378">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="3f194-379">如果枚举器已成功进行高级，则 **MoveNext** 返回 **True** ; 如果枚举数已越过集合的末尾，则返回 **False** 。</span><span class="sxs-lookup"><span data-stu-id="3f194-379">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="3f194-380">返回的 **布尔** 值会将我的 **MoveNext** 发送到输出流。</span><span class="sxs-lookup"><span data-stu-id="3f194-380">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="3f194-381">可以通过将输出 typecasting 为 `[void]` 或将其传送到 [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null)来禁止输出。</span><span class="sxs-lookup"><span data-stu-id="3f194-381">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="3f194-382">重置</span><span class="sxs-lookup"><span data-stu-id="3f194-382">Reset</span></span>

<span data-ttu-id="3f194-383">[Reset](/dotnet/api/system.collections.ienumerator.reset)方法将枚举器设置为其初始位置，该位置位于集合中第一个元素 **之前**。</span><span class="sxs-lookup"><span data-stu-id="3f194-383">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="3f194-384">当前</span><span class="sxs-lookup"><span data-stu-id="3f194-384">Current</span></span>

<span data-ttu-id="3f194-385">[当前](/dotnet/api/system.collections.ienumerator.current)属性获取集合中的元素或管道中的枚举器的当前位置。</span><span class="sxs-lookup"><span data-stu-id="3f194-385">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="3f194-386">**当前** 属性将继续返回相同的属性，直到调用 **MoveNext** 。</span><span class="sxs-lookup"><span data-stu-id="3f194-386">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="3f194-387">示例</span><span class="sxs-lookup"><span data-stu-id="3f194-387">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="3f194-388">示例1：使用 $input 变量</span><span class="sxs-lookup"><span data-stu-id="3f194-388">Example 1: Using the $input variable</span></span>

<span data-ttu-id="3f194-389">在下面的示例中，访问 `$input` 变量将清除变量，直到下一次执行进程块。</span><span class="sxs-lookup"><span data-stu-id="3f194-389">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="3f194-390">使用 **Reset** 方法会将变量重置 `$input` 为当前管道值。</span><span class="sxs-lookup"><span data-stu-id="3f194-390">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="3f194-391">即使不访问变量，进程块也会自动推进该 `$input` 变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-391">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="3f194-392">示例2：在进程块外使用 $input</span><span class="sxs-lookup"><span data-stu-id="3f194-392">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="3f194-393">在进程块外，该 `$input` 变量表示通过管道传递到函数中的所有值。</span><span class="sxs-lookup"><span data-stu-id="3f194-393">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="3f194-394">访问 `$input` 变量将清除所有值。</span><span class="sxs-lookup"><span data-stu-id="3f194-394">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="3f194-395">**Reset** 方法重置整个集合。</span><span class="sxs-lookup"><span data-stu-id="3f194-395">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="3f194-396">从未填充 **当前** 属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-396">The **Current** property is never populated.</span></span>
- <span data-ttu-id="3f194-397">**MoveNext** 方法返回 false，因为集合不能为高级。</span><span class="sxs-lookup"><span data-stu-id="3f194-397">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="3f194-398">调用 **MoveNext** 会清除该 `$input` 变量。</span><span class="sxs-lookup"><span data-stu-id="3f194-398">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="3f194-399">示例3：使用 $input。当前属性</span><span class="sxs-lookup"><span data-stu-id="3f194-399">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="3f194-400">通过使用 **当前** 属性，可以多次访问当前管道值，而无需使用 **Reset** 方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-400">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="3f194-401">进程块不会自动调用 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-401">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="3f194-402">除非显式调用 **MoveNext**，否则不会填充 **当前** 属性。</span><span class="sxs-lookup"><span data-stu-id="3f194-402">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="3f194-403">**当前** 属性可以在进程块内多次访问，而无需清除其值。</span><span class="sxs-lookup"><span data-stu-id="3f194-403">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="3f194-404">示例4：使用 $foreach 变量</span><span class="sxs-lookup"><span data-stu-id="3f194-404">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="3f194-405">与 `$input` 变量不同，在 `$foreach` 直接访问时，变量始终表示集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="3f194-405">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="3f194-406">使用 **current** 属性可以访问当前集合元素，使用 **Reset** 和 **MoveNext** 方法可以更改其值。</span><span class="sxs-lookup"><span data-stu-id="3f194-406">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="3f194-407">循环的每次迭代 `foreach` 都将自动调用 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-407">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="3f194-408">以下循环只执行两次。</span><span class="sxs-lookup"><span data-stu-id="3f194-408">The following loop only executes twice.</span></span> <span data-ttu-id="3f194-409">在第二次迭代中，在迭代完成之前，将集合移动到第三个元素。</span><span class="sxs-lookup"><span data-stu-id="3f194-409">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="3f194-410">在第二次迭代后，现在没有更多值可供迭代，循环将终止。</span><span class="sxs-lookup"><span data-stu-id="3f194-410">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="3f194-411">**MoveNext** 属性不影响所选择的用于循环访问集合的变量 (`$Num`) 。</span><span class="sxs-lookup"><span data-stu-id="3f194-411">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="3f194-412">使用 **Reset** 方法重置集合中的当前元素。</span><span class="sxs-lookup"><span data-stu-id="3f194-412">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="3f194-413">下面的示例循环遍历前两个元素 **两次** ，因为调用 **Reset** 方法。</span><span class="sxs-lookup"><span data-stu-id="3f194-413">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="3f194-414">在前两个循环之后， `if` 语句将失败，并且循环会正常地循环访问所有三个元素。</span><span class="sxs-lookup"><span data-stu-id="3f194-414">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f194-415">这可能会导致无限循环。</span><span class="sxs-lookup"><span data-stu-id="3f194-415">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="3f194-416">示例5：使用 $switch 变量</span><span class="sxs-lookup"><span data-stu-id="3f194-416">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="3f194-417">`$switch`变量与变量具有完全相同的规则 `$foreach` 。</span><span class="sxs-lookup"><span data-stu-id="3f194-417">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="3f194-418">下面的示例演示了所有枚举器概念。</span><span class="sxs-lookup"><span data-stu-id="3f194-418">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="3f194-419">请注意， 即使在 `break` **MoveNext** 方法后面没有语句，也不会执行 NotEvaluated 事例。</span><span class="sxs-lookup"><span data-stu-id="3f194-419">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="3f194-420">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f194-420">See also</span></span>

[<span data-ttu-id="3f194-421">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3f194-421">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="3f194-422">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="3f194-422">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="3f194-423">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="3f194-423">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="3f194-424">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="3f194-424">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="3f194-425">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="3f194-425">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="3f194-426">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="3f194-426">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="3f194-427">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="3f194-427">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="3f194-428">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="3f194-428">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="3f194-429">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="3f194-429">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="3f194-430">about_Variables</span><span class="sxs-lookup"><span data-stu-id="3f194-430">about_Variables</span></span>](about_Variables.md)

