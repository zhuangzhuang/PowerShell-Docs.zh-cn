---
description: 描述存储 PowerShell 的状态信息的变量。 这些变量由 PowerShell 创建和维护。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 8a2410dd2adcc1679ab203293b4c4e712b960278
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975135"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="0006e-104">关于自动变量</span><span class="sxs-lookup"><span data-stu-id="0006e-104">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="0006e-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="0006e-105">Short description</span></span>

<span data-ttu-id="0006e-106">描述存储 PowerShell 的状态信息的变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-106">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="0006e-107">这些变量由 PowerShell 创建和维护。</span><span class="sxs-lookup"><span data-stu-id="0006e-107">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0006e-108">长说明</span><span class="sxs-lookup"><span data-stu-id="0006e-108">Long description</span></span>

<span data-ttu-id="0006e-109">从概念上讲，这些变量被视为只读。</span><span class="sxs-lookup"><span data-stu-id="0006e-109">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="0006e-110">即使 **可** 将它们写入到中，但 **不应** 将其写入到后向兼容性。</span><span class="sxs-lookup"><span data-stu-id="0006e-110">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="0006e-111">下面是 PowerShell 中自动变量的列表：</span><span class="sxs-lookup"><span data-stu-id="0006e-111">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="0006e-112">包含会话收到的最后一行中的最后一个标记。</span><span class="sxs-lookup"><span data-stu-id="0006e-112">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="0006e-113">$?</span><span class="sxs-lookup"><span data-stu-id="0006e-113">$?</span></span>

<span data-ttu-id="0006e-114">包含最后一个命令的执行状态。</span><span class="sxs-lookup"><span data-stu-id="0006e-114">Contains the execution status of the last command.</span></span> <span data-ttu-id="0006e-115">如果最后一个命令成功，则 **为 True;** 否则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="0006e-115">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="0006e-116">对于在管道中的多个阶段（例如在和块中）运行的 cmdlet 和高级函数，在 `process` `end` `this.WriteError()` 任何点调用或分别调用或 `$PSCmdlet.WriteError()` 分别将设置 `$?` 为 **False**，就像 `this.ThrowTerminatingError()` 和 `$PSCmdlet.ThrowTerminatingError()` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-116">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False**, as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="0006e-117">`Write-Error`Cmdlet 始终在 `$?` 执行后立即设置为 **false** ，但不会 `$?` 对调用它的函数设置为 **false** ：</span><span class="sxs-lookup"><span data-stu-id="0006e-117">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="0006e-118">对于后一种用途， `$PSCmdlet.WriteError()` 应改为使用。</span><span class="sxs-lookup"><span data-stu-id="0006e-118">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="0006e-119">对于 (可执行文件) 的本机命令， `$?` 当为0时，将设置为 **True** `$LASTEXITCODE` ，如果 `$LASTEXITCODE` 为任何其他值，则设置为 False。</span><span class="sxs-lookup"><span data-stu-id="0006e-119">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="0006e-120">在 PowerShell 7 中，在括号内包含语句后 `(...)` ，子表达式语法 `$(...)` 或数组表达式 `@(...)` 始终重置 `$?` 为 **True**，因此 `(Write-Error)` 显示 `$?` 为 **true**。</span><span class="sxs-lookup"><span data-stu-id="0006e-120">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True**, so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="0006e-121">此操作在 PowerShell 7 中已更改，因此 `$?` 将始终反映在这些表达式中运行的最后一个命令的实际成功。</span><span class="sxs-lookup"><span data-stu-id="0006e-121">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="0006e-122">包含会话收到的最后一行中的第一个标记。</span><span class="sxs-lookup"><span data-stu-id="0006e-122">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="0006e-123">$_</span><span class="sxs-lookup"><span data-stu-id="0006e-123">$_</span></span>

<span data-ttu-id="0006e-124">与 `$PSItem` 相同。</span><span class="sxs-lookup"><span data-stu-id="0006e-124">Same as `$PSItem`.</span></span> <span data-ttu-id="0006e-125">包含管道对象中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-125">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="0006e-126">可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-126">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="0006e-127">$args</span><span class="sxs-lookup"><span data-stu-id="0006e-127">$args</span></span>

<span data-ttu-id="0006e-128">包含传递给函数、脚本或脚本块的未声明参数的值数组。</span><span class="sxs-lookup"><span data-stu-id="0006e-128">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="0006e-129">创建函数时，可以使用 `param` 关键字或在函数名称后的括号中添加以逗号分隔的参数列表，来声明参数。</span><span class="sxs-lookup"><span data-stu-id="0006e-129">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="0006e-130">在事件操作中， `$args` 变量包含表示正在处理的事件的事件参数的对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-130">In an event action, the `$args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="0006e-131">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-131">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="0006e-132">此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceArgs** 属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-132">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="0006e-133">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="0006e-133">$ConsoleFileName</span></span>

<span data-ttu-id="0006e-134">包含 `.psc1` 会话中最近使用的控制台文件 () 的路径。</span><span class="sxs-lookup"><span data-stu-id="0006e-134">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="0006e-135">使用 **PSConsoleFile** 参数启动 PowerShell 或使用 `Export-Console` cmdlet 将管理单元名称导出到控制台文件时，将填充此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-135">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="0006e-136">使用 `Export-Console` 不带参数的 cmdlet 时，它会自动更新会话中最近使用的控制台文件。</span><span class="sxs-lookup"><span data-stu-id="0006e-136">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="0006e-137">您可以使用此自动变量来确定将更新哪个文件。</span><span class="sxs-lookup"><span data-stu-id="0006e-137">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="0006e-138">$Error</span><span class="sxs-lookup"><span data-stu-id="0006e-138">$Error</span></span>

<span data-ttu-id="0006e-139">包含错误对象的数组，这些对象表示最近的错误。</span><span class="sxs-lookup"><span data-stu-id="0006e-139">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="0006e-140">最近的错误是数组中第一个错误对象 `$Error[0]` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-140">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="0006e-141">若要防止将错误添加到 `$Error` 数组，请使用值为 **Ignore** 的 **ErrorAction** 通用参数。</span><span class="sxs-lookup"><span data-stu-id="0006e-141">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="0006e-142">有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-142">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="0006e-143">$Event</span><span class="sxs-lookup"><span data-stu-id="0006e-143">$Event</span></span>

<span data-ttu-id="0006e-144">包含表示正在处理的事件的 **PSEventArgs** 对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-144">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="0006e-145">此变量仅在 `Action` 事件注册命令块中填充，例如 `Register-ObjectEvent` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-145">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="0006e-146">此变量的值与 cmdlet 返回的对象相同 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-146">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="0006e-147">因此，可以 `Event` `$Event.TimeGenerated` 在脚本块中使用该变量的属性，例如 `Action` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-147">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="0006e-148">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="0006e-148">$EventArgs</span></span>

<span data-ttu-id="0006e-149">包含一个对象，该对象表示从正在处理的事件的 **EventArgs** 派生的第一个事件参数。</span><span class="sxs-lookup"><span data-stu-id="0006e-149">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="0006e-150">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-150">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="0006e-151">此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceEventArgs** 属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-151">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="0006e-152">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="0006e-152">$EventSubscriber</span></span>

<span data-ttu-id="0006e-153">包含一个 **PSEventSubscriber** 对象，该对象表示正在处理的事件的事件订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0006e-153">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="0006e-154">仅在 `Action` 事件注册命令块内填充此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-154">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="0006e-155">此变量的值与 cmdlet 返回的对象相同 `Get-EventSubscriber` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-155">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="0006e-156">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="0006e-156">$ExecutionContext</span></span>

<span data-ttu-id="0006e-157">包含一个 **EngineIntrinsics** 对象，该对象表示 PowerShell 主机的执行上下文。</span><span class="sxs-lookup"><span data-stu-id="0006e-157">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="0006e-158">您可以使用此变量来查找可用于 cmdlet 的执行对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-158">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="0006e-159">$false</span><span class="sxs-lookup"><span data-stu-id="0006e-159">$false</span></span>

<span data-ttu-id="0006e-160">包含 **False**。</span><span class="sxs-lookup"><span data-stu-id="0006e-160">Contains **False**.</span></span> <span data-ttu-id="0006e-161">可以在命令和脚本中使用此变量来表示 **False** ，而不是使用字符串 "False"。</span><span class="sxs-lookup"><span data-stu-id="0006e-161">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="0006e-162">如果字符串被转换为非空字符串或非零整数，则可以将该字符串解释为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="0006e-162">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="0006e-163">$foreach</span><span class="sxs-lookup"><span data-stu-id="0006e-163">$foreach</span></span>

<span data-ttu-id="0006e-164">包含枚举器 (不是 [ForEach](about_ForEach.md) 循环) 的结果值。</span><span class="sxs-lookup"><span data-stu-id="0006e-164">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="0006e-165">此 `$ForEach` 变量仅在 `ForEach` 循环运行时存在; 在循环完成后将其删除。</span><span class="sxs-lookup"><span data-stu-id="0006e-165">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="0006e-166">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-166">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="0006e-167">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="0006e-167">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="0006e-168">$HOME</span><span class="sxs-lookup"><span data-stu-id="0006e-168">$HOME</span></span>

<span data-ttu-id="0006e-169">包含用户的主目录的完整路径。</span><span class="sxs-lookup"><span data-stu-id="0006e-169">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="0006e-170">通常，此变量等效于 `"$env:homedrive$env:homepath"` Windows 环境变量 `C:\Users\<UserName>` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-170">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="0006e-171">$Host</span><span class="sxs-lookup"><span data-stu-id="0006e-171">$Host</span></span>

<span data-ttu-id="0006e-172">包含表示 PowerShell 的当前主机应用程序的对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-172">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="0006e-173">您可以使用此变量来表示命令中的当前宿主，或者显示或更改主机的属性，例如 `$Host.version` 或 `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-173">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="0006e-174">$input</span><span class="sxs-lookup"><span data-stu-id="0006e-174">$input</span></span>

<span data-ttu-id="0006e-175">包含枚举传递到函数的所有输入的枚举器。</span><span class="sxs-lookup"><span data-stu-id="0006e-175">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="0006e-176">此 `$input` 变量仅适用于) 为未命名函数 (函数和脚本块。</span><span class="sxs-lookup"><span data-stu-id="0006e-176">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="0006e-177">在没有 `Begin` 、或块的函数中 `Process` `End` ， `$input` 变量枚举函数的所有输入的集合。</span><span class="sxs-lookup"><span data-stu-id="0006e-177">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="0006e-178">在 `Begin` 块中， `$input` 变量不包含任何数据。</span><span class="sxs-lookup"><span data-stu-id="0006e-178">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="0006e-179">在 `Process` 块中， `$input` 变量包含管道中当前的对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-179">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="0006e-180">在 `End` 块中， `$input` 变量枚举函数的所有输入的集合。</span><span class="sxs-lookup"><span data-stu-id="0006e-180">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0006e-181">不能 `$input` 在同一函数或脚本块中的进程块和结束块中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-181">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="0006e-182">由于 `$input` 是一个枚举器，因此访问它的任何属性都将导致 `$input` 不再可用。</span><span class="sxs-lookup"><span data-stu-id="0006e-182">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="0006e-183">可以 `$input` 在另一个变量中存储以重用 `$input` 属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-183">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="0006e-184">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-184">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="0006e-185">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="0006e-185">For more information, see [Using Enumerators](#using-enumerators).</span></span>

<span data-ttu-id="0006e-186">`$input` `-Command` `pwsh` 当从命令行调用时，该变量也可用于由的参数指定的命令。</span><span class="sxs-lookup"><span data-stu-id="0006e-186">The `$input` variable is also available to the command specified by the `-Command` parameter of `pwsh` when invoked from the command line.</span></span> <span data-ttu-id="0006e-187">下面的示例从 Windows 命令行界面运行。</span><span class="sxs-lookup"><span data-stu-id="0006e-187">The following example is run from the Windows Command shell.</span></span>

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a><span data-ttu-id="0006e-188">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="0006e-188">$IsCoreCLR</span></span>

<span data-ttu-id="0006e-189">包含 `$True` 当前会话是否在 .Net Core 运行时上运行 (CoreCLR) 。</span><span class="sxs-lookup"><span data-stu-id="0006e-189">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="0006e-190">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-190">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="0006e-191">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="0006e-191">$IsLinux</span></span>

<span data-ttu-id="0006e-192">包含 `$True` 当前会话是否在 Linux 操作系统上运行。</span><span class="sxs-lookup"><span data-stu-id="0006e-192">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="0006e-193">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-193">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="0006e-194">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="0006e-194">$IsMacOS</span></span>

<span data-ttu-id="0006e-195">包含 `$True` 当前会话是否在 MacOS 操作系统上运行的。</span><span class="sxs-lookup"><span data-stu-id="0006e-195">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="0006e-196">否则包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-196">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="0006e-197">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="0006e-197">$IsWindows</span></span>

<span data-ttu-id="0006e-198">`$TRUE`如果当前会话正在 Windows 操作系统上运行，则包含。</span><span class="sxs-lookup"><span data-stu-id="0006e-198">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="0006e-199">否则包含 `$FALSE` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-199">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="0006e-200">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="0006e-200">$LastExitCode</span></span>

<span data-ttu-id="0006e-201">包含上一次运行的基于 Windows 的程序的退出代码。</span><span class="sxs-lookup"><span data-stu-id="0006e-201">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="0006e-202">$Matches</span><span class="sxs-lookup"><span data-stu-id="0006e-202">$Matches</span></span>

<span data-ttu-id="0006e-203">`Matches`变量与 `-match` and 运算符一起使用 `-notmatch` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-203">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="0006e-204">当你将标量输入提交给 `-match` or `-notmatch` 运算符，并且其中一个检测到匹配时，它们将返回一个布尔值，并 `$Matches` 使用匹配的任何字符串值的哈希表填充自动变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-204">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="0006e-205">在 `$Matches` 将正则表达式用于运算符时，还可以使用捕获来填充哈希表 `-match` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-205">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="0006e-206">有关运算符的详细信息 `-match` ，请参阅 [about_Comparison_Operators](about_comparison_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-206">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="0006e-207">有关正则表达式的详细信息，请参阅 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-207">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="0006e-208">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="0006e-208">$MyInvocation</span></span>

<span data-ttu-id="0006e-209">包含有关当前命令的信息，如名称、参数、参数值和有关如何启动、调用或调用命令的信息，例如调用当前命令的脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="0006e-209">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="0006e-210">`$MyInvocation` 仅填充脚本、函数和脚本块。</span><span class="sxs-lookup"><span data-stu-id="0006e-210">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="0006e-211">您可以使用在当前脚本中返回的 **InvocationInfo** 对象中的信息 `$MyInvocation` ，例如脚本 () 的路径和文件名， `$MyInvocation.MyCommand.Path` 或函数的名称 (`$MyInvocation.MyCommand.Name`) 以标识当前命令。</span><span class="sxs-lookup"><span data-stu-id="0006e-211">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="0006e-212">这对于查找当前脚本的名称特别有用。</span><span class="sxs-lookup"><span data-stu-id="0006e-212">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="0006e-213">从 PowerShell 3.0 开始， `MyInvocation` 具有以下新属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-213">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="0006e-214">属性</span><span class="sxs-lookup"><span data-stu-id="0006e-214">Property</span></span>      | <span data-ttu-id="0006e-215">说明</span><span class="sxs-lookup"><span data-stu-id="0006e-215">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="0006e-216">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="0006e-216">**PSScriptRoot**</span></span>  | <span data-ttu-id="0006e-217">包含调用的脚本的完整路径</span><span class="sxs-lookup"><span data-stu-id="0006e-217">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="0006e-218">当前命令。</span><span class="sxs-lookup"><span data-stu-id="0006e-218">the current command.</span></span> <span data-ttu-id="0006e-219">此属性的值为</span><span class="sxs-lookup"><span data-stu-id="0006e-219">The value of this property is</span></span>  |
|               | <span data-ttu-id="0006e-220">仅当调用方为脚本时才填充。</span><span class="sxs-lookup"><span data-stu-id="0006e-220">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="0006e-221">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="0006e-221">**PSCommandPath**</span></span> | <span data-ttu-id="0006e-222">包含脚本的完整路径和文件名</span><span class="sxs-lookup"><span data-stu-id="0006e-222">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="0006e-223">调用当前命令的。</span><span class="sxs-lookup"><span data-stu-id="0006e-223">that invoked the current command.</span></span> <span data-ttu-id="0006e-224">此的值</span><span class="sxs-lookup"><span data-stu-id="0006e-224">The value of this</span></span> |
|               | <span data-ttu-id="0006e-225">仅当调用方是</span><span class="sxs-lookup"><span data-stu-id="0006e-225">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="0006e-226">脚本。</span><span class="sxs-lookup"><span data-stu-id="0006e-226">script.</span></span>                                             |

<span data-ttu-id="0006e-227">与自动变量不同 `$PSScriptRoot` `$PSCommandPath` ，自动变量的 **PSScriptRoot** 和 **PSCommandPath** 属性 `$MyInvocation` 包含有关调用程序或调用脚本的信息，而不是当前脚本。</span><span class="sxs-lookup"><span data-stu-id="0006e-227">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="0006e-228">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="0006e-228">$NestedPromptLevel</span></span>

<span data-ttu-id="0006e-229">包含当前提示符级别。</span><span class="sxs-lookup"><span data-stu-id="0006e-229">Contains the current prompt level.</span></span> <span data-ttu-id="0006e-230">值0表示原始提示级别。</span><span class="sxs-lookup"><span data-stu-id="0006e-230">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="0006e-231">当您输入嵌套级别时，该值会递增，并且在您退出时将递增。</span><span class="sxs-lookup"><span data-stu-id="0006e-231">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="0006e-232">例如，使用方法时，PowerShell 会显示嵌套的命令提示符 `$Host.EnterNestedPrompt` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-232">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="0006e-233">当你到达 PowerShell 调试器中的断点时，PowerShell 还会显示嵌套的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="0006e-233">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="0006e-234">输入嵌套提示符时，PowerShell 将暂停当前命令，保存执行上下文，并递增变量的值 `$NestedPromptLevel` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-234">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="0006e-235">若要创建其他嵌套的命令提示 (最多128级别) 或返回到原始命令提示符，请完成命令或键入 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-235">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="0006e-236">`$NestedPromptLevel`变量有助于跟踪提示级别。</span><span class="sxs-lookup"><span data-stu-id="0006e-236">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="0006e-237">你可以创建一个包含此值的备用 PowerShell 命令提示符，以使其始终可见。</span><span class="sxs-lookup"><span data-stu-id="0006e-237">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="0006e-238">$null</span><span class="sxs-lookup"><span data-stu-id="0006e-238">$null</span></span>

<span data-ttu-id="0006e-239">`$null` 是包含 **null** 值或空值的自动变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-239">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="0006e-240">您可以使用此变量来表示命令和脚本中缺少的值或未定义的值。</span><span class="sxs-lookup"><span data-stu-id="0006e-240">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="0006e-241">PowerShell 将视为 `$null` 具有值的对象（即，作为显式占位符），因此可以使用 `$null` 来表示一系列值中的空值。</span><span class="sxs-lookup"><span data-stu-id="0006e-241">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="0006e-242">例如，当 `$null` 包含在集合中时，会将其计为一个对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-242">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="0006e-243">如果通过管道将 `$null` 变量传递给 `ForEach-Object` cmdlet，它会为生成一个值 `$null` ，就像对其他对象执行此方法一样。</span><span class="sxs-lookup"><span data-stu-id="0006e-243">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="0006e-244">因此，不能使用 `$null` 来表示 **没有参数值**。</span><span class="sxs-lookup"><span data-stu-id="0006e-244">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="0006e-245">参数值 `$null` 覆盖默认参数值。</span><span class="sxs-lookup"><span data-stu-id="0006e-245">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="0006e-246">但是，因为 PowerShell 将 `$null` 变量视为占位符，所以可以在脚本中使用它，如果忽略，这将不起作用 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-246">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

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

### <a name="pid"></a><span data-ttu-id="0006e-247">$PID</span><span class="sxs-lookup"><span data-stu-id="0006e-247">$PID</span></span>

<span data-ttu-id="0006e-248">包含承载当前 PowerShell 会话的进程的进程标识符 (PID) 。</span><span class="sxs-lookup"><span data-stu-id="0006e-248">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="0006e-249">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="0006e-249">$PROFILE</span></span>

<span data-ttu-id="0006e-250">包含当前用户和当前主机应用程序的 PowerShell 配置文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="0006e-250">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="0006e-251">您可以使用此变量来表示命令中的配置文件。</span><span class="sxs-lookup"><span data-stu-id="0006e-251">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="0006e-252">例如，你可以在命令中使用它来确定是否已创建配置文件：</span><span class="sxs-lookup"><span data-stu-id="0006e-252">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="0006e-253">或者，你可以在命令中使用它来创建配置文件：</span><span class="sxs-lookup"><span data-stu-id="0006e-253">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="0006e-254">可以在命令中使用它在 **notepad.exe** 中打开配置文件：</span><span class="sxs-lookup"><span data-stu-id="0006e-254">You can use it in a command to open the profile in **notepad.exe**:</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="0006e-255">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="0006e-255">$PSBoundParameters</span></span>

<span data-ttu-id="0006e-256">包含传递给脚本或函数的参数的字典及其当前值。</span><span class="sxs-lookup"><span data-stu-id="0006e-256">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="0006e-257">此变量仅在声明参数的作用域（如脚本或函数）中具有值。</span><span class="sxs-lookup"><span data-stu-id="0006e-257">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="0006e-258">您可以使用它显示或更改参数的当前值，或者将参数值传递给其他脚本或函数。</span><span class="sxs-lookup"><span data-stu-id="0006e-258">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="0006e-259">在此示例中， **Test2** 函数将传递 `$PSBoundParameters` 给 **Test1** 函数。</span><span class="sxs-lookup"><span data-stu-id="0006e-259">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="0006e-260">`$PSBoundParameters`以 **键** 和 **值** 的格式显示。</span><span class="sxs-lookup"><span data-stu-id="0006e-260">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

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

### <a name="pscmdlet"></a><span data-ttu-id="0006e-261">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="0006e-261">$PSCmdlet</span></span>

<span data-ttu-id="0006e-262">包含一个对象，该对象表示正在运行的 cmdlet 或高级函数。</span><span class="sxs-lookup"><span data-stu-id="0006e-262">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="0006e-263">你可以使用 cmdlet 或函数代码中的对象的属性和方法来响应使用情况。</span><span class="sxs-lookup"><span data-stu-id="0006e-263">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="0006e-264">例如， **ParameterSetName** 属性包含所使用的参数集的名称， **ShouldProcess** 方法会动态地将 **WhatIf** 和 **Confirm** 参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0006e-264">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="0006e-265">有关自动变量的详细信息 `$PSCmdlet` ，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-265">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="0006e-266">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="0006e-266">$PSCommandPath</span></span>

<span data-ttu-id="0006e-267">包含正在运行的脚本的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="0006e-267">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="0006e-268">此变量在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="0006e-268">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="0006e-269">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="0006e-269">$PSCulture</span></span>

<span data-ttu-id="0006e-270">从 PowerShell 7 开始， `$PSCulture` 反映当前 PowerShell 运行空间的区域性 (会话) 。</span><span class="sxs-lookup"><span data-stu-id="0006e-270">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="0006e-271">如果在 PowerShell 运行空间中更改了区域性，则将 `$PSCulture` 更新该运行空间的值。</span><span class="sxs-lookup"><span data-stu-id="0006e-271">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="0006e-272">区域性确定项的显示格式（例如数字、货币和日期），并将其存储在 **system.exception 对象中。**</span><span class="sxs-lookup"><span data-stu-id="0006e-272">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="0006e-273">用于 `Get-Culture` 显示计算机的区域性。</span><span class="sxs-lookup"><span data-stu-id="0006e-273">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="0006e-274">`$PSCulture` 包含 **名称** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="0006e-274">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="0006e-275">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="0006e-275">$PSDebugContext</span></span>

<span data-ttu-id="0006e-276">调试时，此变量包含有关调试环境的信息。</span><span class="sxs-lookup"><span data-stu-id="0006e-276">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="0006e-277">否则，它将包含 **null** 值。</span><span class="sxs-lookup"><span data-stu-id="0006e-277">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="0006e-278">因此，你可以使用它来指示调试器是否具有控件。</span><span class="sxs-lookup"><span data-stu-id="0006e-278">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="0006e-279">填充后，它将包含一个 **PsDebugContext** 对象，该对象具有 **断点** 和 **InvocationInfo** 属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-279">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="0006e-280">**InvocationInfo** 属性具有多个有用的属性，包括 **Location** 属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-280">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="0006e-281">**Location** 属性指示正在调试的脚本的路径。</span><span class="sxs-lookup"><span data-stu-id="0006e-281">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="0006e-282">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="0006e-282">$PSHOME</span></span>

<span data-ttu-id="0006e-283">包含适用于 PowerShell 的安装目录的完整路径，通常是 `$env:windir\System32\PowerShell\v1.0` 在 Windows 系统中。</span><span class="sxs-lookup"><span data-stu-id="0006e-283">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="0006e-284">可以在 PowerShell 文件的路径中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-284">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="0006e-285">例如，下面的命令在概念帮助主题中搜索 word **变量**：</span><span class="sxs-lookup"><span data-stu-id="0006e-285">For example, the following command searches the conceptual Help topics for the word **variable**:</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="0006e-286">$PSItem</span><span class="sxs-lookup"><span data-stu-id="0006e-286">$PSItem</span></span>

<span data-ttu-id="0006e-287">与 `$_` 相同。</span><span class="sxs-lookup"><span data-stu-id="0006e-287">Same as `$_`.</span></span> <span data-ttu-id="0006e-288">包含管道对象中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-288">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="0006e-289">可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-289">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="0006e-290">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="0006e-290">$PSScriptRoot</span></span>

<span data-ttu-id="0006e-291">包含正在从中运行脚本的目录。</span><span class="sxs-lookup"><span data-stu-id="0006e-291">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="0006e-292">在 PowerShell 2.0 中，此变量仅在) 的脚本模块中有效 (`.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-292">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="0006e-293">从 PowerShell 3.0 开始，它在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="0006e-293">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="0006e-294">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="0006e-294">$PSSenderInfo</span></span>

<span data-ttu-id="0006e-295">包含有关启动 PSSession 的用户的信息，其中包括源计算机的用户标识和时区。</span><span class="sxs-lookup"><span data-stu-id="0006e-295">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="0006e-296">此变量仅在 Pssession 中可用。</span><span class="sxs-lookup"><span data-stu-id="0006e-296">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="0006e-297">此 `$PSSenderInfo` 变量包含一个用户可配置的属性 **ApplicationArguments**，默认情况下，该属性仅包含 `$PSVersionTable` 来自原始会话的。</span><span class="sxs-lookup"><span data-stu-id="0006e-297">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments**, that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="0006e-298">若要将数据添加到 **ApplicationArguments** 属性，请使用 Cmdlet 的 **ApplicationArguments** 参数 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-298">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="0006e-299">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="0006e-299">$PSUICulture</span></span>

<span data-ttu-id="0006e-300">包含操作系统中当前正在使用的 (UI) 区域性的用户界面的名称。</span><span class="sxs-lookup"><span data-stu-id="0006e-300">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="0006e-301">UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。</span><span class="sxs-lookup"><span data-stu-id="0006e-301">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="0006e-302">这是系统的 **System.Globalization.CultureInfo.CurrentUICulture.Name** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="0006e-302">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="0006e-303">若要获取 **系统的 system.servicemodel 对象，** 请使用 `Get-UICulture` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0006e-303">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="0006e-304">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="0006e-304">$PSVersionTable</span></span>

<span data-ttu-id="0006e-305">包含一个只读的哈希表，该表显示有关当前会话中正在运行的 PowerShell 版本的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0006e-305">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="0006e-306">该表包含以下各项：</span><span class="sxs-lookup"><span data-stu-id="0006e-306">The table includes the following items:</span></span>

| <span data-ttu-id="0006e-307">属性</span><span class="sxs-lookup"><span data-stu-id="0006e-307">Property</span></span>                  | <span data-ttu-id="0006e-308">说明</span><span class="sxs-lookup"><span data-stu-id="0006e-308">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="0006e-309">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="0006e-309">**PSVersion**</span></span>             | <span data-ttu-id="0006e-310">PowerShell 版本号</span><span class="sxs-lookup"><span data-stu-id="0006e-310">The PowerShell version number</span></span>                 |
| <span data-ttu-id="0006e-311">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="0006e-311">**PSEdition**</span></span>             | <span data-ttu-id="0006e-312">此属性的值为 "Desktop"</span><span class="sxs-lookup"><span data-stu-id="0006e-312">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="0006e-313">PowerShell 4 及更低</span><span class="sxs-lookup"><span data-stu-id="0006e-313">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="0006e-314">5.1 功能齐全的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="0006e-314">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="0006e-315">此属性的值为 "Core"</span><span class="sxs-lookup"><span data-stu-id="0006e-315">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="0006e-316">PowerShell 6 及更高版本以及 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0006e-316">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="0006e-317">精简版的小型版本上的 PowerShell 5。1</span><span class="sxs-lookup"><span data-stu-id="0006e-317">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="0006e-318">类似于 Windows Nano Server 或 Windows IoT。</span><span class="sxs-lookup"><span data-stu-id="0006e-318">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="0006e-319">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="0006e-319">**GitCommitId**</span></span>           | <span data-ttu-id="0006e-320">GitHub 中的源文件的提交 Id</span><span class="sxs-lookup"><span data-stu-id="0006e-320">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="0006e-321">**OS**</span><span class="sxs-lookup"><span data-stu-id="0006e-321">**OS**</span></span>                    | <span data-ttu-id="0006e-322">操作系统的说明</span><span class="sxs-lookup"><span data-stu-id="0006e-322">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="0006e-323">PowerShell 正在上运行。</span><span class="sxs-lookup"><span data-stu-id="0006e-323">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="0006e-324">**平台**</span><span class="sxs-lookup"><span data-stu-id="0006e-324">**Platform**</span></span>              | <span data-ttu-id="0006e-325">操作系统正在运行的平台</span><span class="sxs-lookup"><span data-stu-id="0006e-325">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="0006e-326">如果</span><span class="sxs-lookup"><span data-stu-id="0006e-326">on.</span></span> <span data-ttu-id="0006e-327">Linux 和 macOS 上的值为 **Unix**。</span><span class="sxs-lookup"><span data-stu-id="0006e-327">The value on Linux and macOS is **Unix**.</span></span> |
|                           | <span data-ttu-id="0006e-328">请参见 `$IsMacOs` 和 `$IsLinux`。</span><span class="sxs-lookup"><span data-stu-id="0006e-328">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="0006e-329">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="0006e-329">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="0006e-330">兼容的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="0006e-330">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="0006e-331">与当前版本</span><span class="sxs-lookup"><span data-stu-id="0006e-331">with the current version</span></span>                      |
| <span data-ttu-id="0006e-332">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="0006e-332">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="0006e-333">PowerShell 远程的版本</span><span class="sxs-lookup"><span data-stu-id="0006e-333">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="0006e-334">管理协议。</span><span class="sxs-lookup"><span data-stu-id="0006e-334">management protocol.</span></span>                          |
| <span data-ttu-id="0006e-335">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="0006e-335">**SerializationVersion**</span></span>  | <span data-ttu-id="0006e-336">序列化方法的版本</span><span class="sxs-lookup"><span data-stu-id="0006e-336">The version of the serialization method</span></span>       |
| <span data-ttu-id="0006e-337">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="0006e-337">**WSManStackVersion**</span></span>     | <span data-ttu-id="0006e-338">WS-Management 堆栈的版本号</span><span class="sxs-lookup"><span data-stu-id="0006e-338">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="0006e-339">$PWD</span><span class="sxs-lookup"><span data-stu-id="0006e-339">$PWD</span></span>

<span data-ttu-id="0006e-340">包含表示当前目录的完整路径的路径对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-340">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="0006e-341">$Sender</span><span class="sxs-lookup"><span data-stu-id="0006e-341">$Sender</span></span>

<span data-ttu-id="0006e-342">包含生成此事件的对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-342">Contains the object that generated this event.</span></span> <span data-ttu-id="0006e-343">此变量仅在事件注册命令的操作块中进行填充。</span><span class="sxs-lookup"><span data-stu-id="0006e-343">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="0006e-344">此变量的值还可在返回的 **PSEventArgs** 对象的发送方属性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-344">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="0006e-345">$ShellId</span><span class="sxs-lookup"><span data-stu-id="0006e-345">$ShellId</span></span>

<span data-ttu-id="0006e-346">包含当前 shell 的标识符。</span><span class="sxs-lookup"><span data-stu-id="0006e-346">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="0006e-347">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="0006e-347">$StackTrace</span></span>

<span data-ttu-id="0006e-348">包含最新错误的堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="0006e-348">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="0006e-349">$switch</span><span class="sxs-lookup"><span data-stu-id="0006e-349">$switch</span></span>

<span data-ttu-id="0006e-350">包含枚举器，而不包含语句的结果值 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-350">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="0006e-351">`$switch`仅当语句正在运行时，才存在该变量 `Switch` ; 当语句完成执行时，该变量会被删除 `switch` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-351">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="0006e-352">有关详细信息，请参阅 [about_Switch](about_Switch.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-352">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="0006e-353">枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-353">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="0006e-354">有关详细信息，请参阅 [使用枚举](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="0006e-354">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="0006e-355">$this</span><span class="sxs-lookup"><span data-stu-id="0006e-355">$this</span></span>

<span data-ttu-id="0006e-356">在定义脚本属性或脚本方法的脚本块中， `$this` 变量引用要扩展的对象。</span><span class="sxs-lookup"><span data-stu-id="0006e-356">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="0006e-357">在自定义类中， `$this` 变量引用类对象本身，以允许访问类中定义的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-357">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="0006e-358">$true</span><span class="sxs-lookup"><span data-stu-id="0006e-358">$true</span></span>

<span data-ttu-id="0006e-359">包含 **True**。</span><span class="sxs-lookup"><span data-stu-id="0006e-359">Contains **True**.</span></span> <span data-ttu-id="0006e-360">可以在命令和脚本中使用此变量来表示 **True** 。</span><span class="sxs-lookup"><span data-stu-id="0006e-360">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="0006e-361">使用枚举器</span><span class="sxs-lookup"><span data-stu-id="0006e-361">Using Enumerators</span></span>

<span data-ttu-id="0006e-362">`$input`、 `$foreach` 和 `$switch` 变量是所有枚举器，用于循环访问由其包含代码块处理的值。</span><span class="sxs-lookup"><span data-stu-id="0006e-362">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="0006e-363">枚举器包含可用于提前或重置迭代或检索迭代值的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-363">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="0006e-364">直接操作枚举器并不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="0006e-364">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="0006e-365">在循环中，应首选流控制关键字 " [中断](about_Break.md) 并 [继续](about_Continue.md) "。</span><span class="sxs-lookup"><span data-stu-id="0006e-365">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="0006e-366">在接受管道输入的函数中，最佳做法是将参数与 **ValueFromPipeline** 或 **ValueFromPipelineByPropertyName** 属性结合使用。</span><span class="sxs-lookup"><span data-stu-id="0006e-366">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="0006e-367">有关详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0006e-367">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="0006e-368">MoveNext</span><span class="sxs-lookup"><span data-stu-id="0006e-368">MoveNext</span></span>

<span data-ttu-id="0006e-369">[MoveNext](/dotnet/api/system.collections.ienumerator.movenext)方法将枚举器推进到集合的下一个元素。</span><span class="sxs-lookup"><span data-stu-id="0006e-369">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="0006e-370">如果枚举器已成功进行高级，则 **MoveNext** 返回 **True** ; 如果枚举数已越过集合的末尾，则返回 **False** 。</span><span class="sxs-lookup"><span data-stu-id="0006e-370">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="0006e-371">返回的 **布尔** 值会将我的 **MoveNext** 发送到输出流。</span><span class="sxs-lookup"><span data-stu-id="0006e-371">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="0006e-372">可以通过将输出 typecasting 为 `[void]` 或将其传送到 [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null)来禁止输出。</span><span class="sxs-lookup"><span data-stu-id="0006e-372">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="0006e-373">重置</span><span class="sxs-lookup"><span data-stu-id="0006e-373">Reset</span></span>

<span data-ttu-id="0006e-374">[Reset](/dotnet/api/system.collections.ienumerator.reset)方法将枚举器设置为其初始位置，该位置位于集合中第一个元素 **之前**。</span><span class="sxs-lookup"><span data-stu-id="0006e-374">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="0006e-375">当前</span><span class="sxs-lookup"><span data-stu-id="0006e-375">Current</span></span>

<span data-ttu-id="0006e-376">[当前](/dotnet/api/system.collections.ienumerator.current)属性获取集合中的元素或管道中的枚举器的当前位置。</span><span class="sxs-lookup"><span data-stu-id="0006e-376">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="0006e-377">**当前** 属性将继续返回相同的属性，直到调用 **MoveNext** 。</span><span class="sxs-lookup"><span data-stu-id="0006e-377">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="0006e-378">示例</span><span class="sxs-lookup"><span data-stu-id="0006e-378">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="0006e-379">示例1：使用 $input 变量</span><span class="sxs-lookup"><span data-stu-id="0006e-379">Example 1: Using the $input variable</span></span>

<span data-ttu-id="0006e-380">在下面的示例中，访问 `$input` 变量将清除变量，直到下一次执行进程块。</span><span class="sxs-lookup"><span data-stu-id="0006e-380">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="0006e-381">使用 **Reset** 方法会将变量重置 `$input` 为当前管道值。</span><span class="sxs-lookup"><span data-stu-id="0006e-381">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

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

<span data-ttu-id="0006e-382">即使不访问变量，进程块也会自动推进该 `$input` 变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-382">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

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

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="0006e-383">示例2：在进程块外使用 $input</span><span class="sxs-lookup"><span data-stu-id="0006e-383">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="0006e-384">在进程块外，该 `$input` 变量表示通过管道传递到函数中的所有值。</span><span class="sxs-lookup"><span data-stu-id="0006e-384">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="0006e-385">访问 `$input` 变量将清除所有值。</span><span class="sxs-lookup"><span data-stu-id="0006e-385">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="0006e-386">**Reset** 方法重置整个集合。</span><span class="sxs-lookup"><span data-stu-id="0006e-386">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="0006e-387">从未填充 **当前** 属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-387">The **Current** property is never populated.</span></span>
- <span data-ttu-id="0006e-388">**MoveNext** 方法返回 false，因为集合不能为高级。</span><span class="sxs-lookup"><span data-stu-id="0006e-388">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="0006e-389">调用 **MoveNext** 会清除该 `$input` 变量。</span><span class="sxs-lookup"><span data-stu-id="0006e-389">Calling **MoveNext** clears out the `$input` variable.</span></span>

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

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="0006e-390">示例3：使用 $input。当前属性</span><span class="sxs-lookup"><span data-stu-id="0006e-390">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="0006e-391">通过使用 **当前** 属性，可以多次访问当前管道值，而无需使用 **Reset** 方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-391">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="0006e-392">进程块不会自动调用 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-392">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="0006e-393">除非显式调用 **MoveNext**，否则不会填充 **当前** 属性。</span><span class="sxs-lookup"><span data-stu-id="0006e-393">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="0006e-394">**当前** 属性可以在进程块内多次访问，而无需清除其值。</span><span class="sxs-lookup"><span data-stu-id="0006e-394">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

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

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="0006e-395">示例4：使用 $foreach 变量</span><span class="sxs-lookup"><span data-stu-id="0006e-395">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="0006e-396">与 `$input` 变量不同，在 `$foreach` 直接访问时，变量始终表示集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="0006e-396">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="0006e-397">使用 **current** 属性可以访问当前集合元素，使用 **Reset** 和 **MoveNext** 方法可以更改其值。</span><span class="sxs-lookup"><span data-stu-id="0006e-397">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="0006e-398">循环的每次迭代 `foreach` 都将自动调用 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-398">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="0006e-399">以下循环只执行两次。</span><span class="sxs-lookup"><span data-stu-id="0006e-399">The following loop only executes twice.</span></span> <span data-ttu-id="0006e-400">在第二次迭代中，在迭代完成之前，将集合移动到第三个元素。</span><span class="sxs-lookup"><span data-stu-id="0006e-400">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="0006e-401">在第二次迭代后，现在没有更多值可供迭代，循环将终止。</span><span class="sxs-lookup"><span data-stu-id="0006e-401">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="0006e-402">**MoveNext** 属性不影响所选择的用于循环访问集合的变量 (`$Num`) 。</span><span class="sxs-lookup"><span data-stu-id="0006e-402">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

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

<span data-ttu-id="0006e-403">使用 **Reset** 方法重置集合中的当前元素。</span><span class="sxs-lookup"><span data-stu-id="0006e-403">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="0006e-404">下面的示例循环遍历前两个元素 **两次** ，因为调用 **Reset** 方法。</span><span class="sxs-lookup"><span data-stu-id="0006e-404">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="0006e-405">在前两个循环之后， `if` 语句将失败，并且循环会正常地循环访问所有三个元素。</span><span class="sxs-lookup"><span data-stu-id="0006e-405">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0006e-406">这可能会导致无限循环。</span><span class="sxs-lookup"><span data-stu-id="0006e-406">This could result in an infinite loop.</span></span>

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

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="0006e-407">示例5：使用 $switch 变量</span><span class="sxs-lookup"><span data-stu-id="0006e-407">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="0006e-408">`$switch`变量与变量具有完全相同的规则 `$foreach` 。</span><span class="sxs-lookup"><span data-stu-id="0006e-408">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="0006e-409">下面的示例演示了所有枚举器概念。</span><span class="sxs-lookup"><span data-stu-id="0006e-409">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="0006e-410">请注意， 即使在 `break` **MoveNext** 方法后面没有语句，也不会执行 NotEvaluated 事例。</span><span class="sxs-lookup"><span data-stu-id="0006e-410">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0006e-411">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0006e-411">See also</span></span>

[<span data-ttu-id="0006e-412">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0006e-412">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="0006e-413">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="0006e-413">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="0006e-414">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="0006e-414">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="0006e-415">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="0006e-415">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="0006e-416">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="0006e-416">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="0006e-417">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="0006e-417">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="0006e-418">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="0006e-418">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="0006e-419">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="0006e-419">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="0006e-420">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="0006e-420">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="0006e-421">about_Variables</span><span class="sxs-lookup"><span data-stu-id="0006e-421">about_Variables</span></span>](about_Variables.md)

