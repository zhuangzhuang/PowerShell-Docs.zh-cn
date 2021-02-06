---
description: 函数
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Function 提供程序
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598282"
---
# <a name="function-provider"></a><span data-ttu-id="d3a72-103">函数提供程序</span><span class="sxs-lookup"><span data-stu-id="d3a72-103">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="d3a72-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="d3a72-104">Provider name</span></span>
<span data-ttu-id="d3a72-105">函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-105">Function</span></span>

## <a name="drives"></a><span data-ttu-id="d3a72-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="d3a72-106">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="d3a72-107">功能</span><span class="sxs-lookup"><span data-stu-id="d3a72-107">Capabilities</span></span>

<span data-ttu-id="d3a72-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="d3a72-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="d3a72-109">简短说明</span><span class="sxs-lookup"><span data-stu-id="d3a72-109">Short description</span></span>

<span data-ttu-id="d3a72-110">提供对在 PowerShell 中定义的函数的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d3a72-110">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="d3a72-111">详细说明</span><span class="sxs-lookup"><span data-stu-id="d3a72-111">Detailed description</span></span>

<span data-ttu-id="d3a72-112">PowerShell **函数** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的函数和筛选器。</span><span class="sxs-lookup"><span data-stu-id="d3a72-112">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="d3a72-113">函数是用于执行某项操作的命名的代码块。</span><span class="sxs-lookup"><span data-stu-id="d3a72-113">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="d3a72-114">在键入函数名称后，将运行该函数中的代码。</span><span class="sxs-lookup"><span data-stu-id="d3a72-114">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="d3a72-115">筛选器是用于建立操作条件的命名的代码块。</span><span class="sxs-lookup"><span data-stu-id="d3a72-115">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="d3a72-116">您可以键入筛选器的名称来代替条件，例如在 `Where-Object` 命令中。</span><span class="sxs-lookup"><span data-stu-id="d3a72-116">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="d3a72-117">**函数** 驱动器是只包含函数和筛选器对象的平面命名空间。</span><span class="sxs-lookup"><span data-stu-id="d3a72-117">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="d3a72-118">函数和筛选器都没有子项。</span><span class="sxs-lookup"><span data-stu-id="d3a72-118">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="d3a72-119">**函数** 提供程序支持以下 cmdlet，这将在本文中介绍。</span><span class="sxs-lookup"><span data-stu-id="d3a72-119">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="d3a72-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="d3a72-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="d3a72-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="d3a72-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="d3a72-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="d3a72-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="d3a72-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="d3a72-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="d3a72-126">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="d3a72-126">Types exposed by this provider</span></span>

<span data-ttu-id="d3a72-127">每个函数都是 [FunctionInfo](/dotnet/api/system.management.automation.functioninfo) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="d3a72-127">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="d3a72-128">每个筛选器都是 [都是 system.management.automation.filterinfo](/dotnet/api/system.management.automation.filterinfo) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="d3a72-128">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="d3a72-129">导航函数驱动器</span><span class="sxs-lookup"><span data-stu-id="d3a72-129">Navigating the Function drive</span></span>

<span data-ttu-id="d3a72-130">**函数** 提供程序在驱动器中公开其数据存储区 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-130">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="d3a72-131">若要使用函数，你可以将你的位置更改为 `Function:` 驱动器 (`Set-Location Function:`) 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-131">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="d3a72-132">或者，你可以从另一个 PowerShell 驱动器进行工作。</span><span class="sxs-lookup"><span data-stu-id="d3a72-132">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="d3a72-133">若要从其他位置引用函数，请在路径中使用驱动器名称 (`Function:`) 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-133">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="d3a72-134">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="d3a72-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="d3a72-135">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="d3a72-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="d3a72-136">你还可以从任何其他 PowerShell 驱动器使用该 **函数** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d3a72-136">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="d3a72-137">若要从其他位置引用函数，请 `Function:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="d3a72-137">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="d3a72-138">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="d3a72-138">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="d3a72-139">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="d3a72-139">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="d3a72-140">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="d3a72-140">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="d3a72-141">获取函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-141">Getting functions</span></span>

<span data-ttu-id="d3a72-142">此命令将获取当前会话中所有函数的列表。</span><span class="sxs-lookup"><span data-stu-id="d3a72-142">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="d3a72-143">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="d3a72-143">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="d3a72-144">函数提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-144">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="d3a72-145">可以通过访问 **定义** 属性来检索函数的定义，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d3a72-145">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="d3a72-146">还可以使用以美元符号 () 前缀的提供程序路径来检索函数的定义 `$` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-146">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="d3a72-147">正在获取选定函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-147">Getting selected functions</span></span>

<span data-ttu-id="d3a72-148">此命令获取 `man` 驱动器中的函数 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-148">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="d3a72-149">它使用 `Get-Item` cmdlet 来获取函数。</span><span class="sxs-lookup"><span data-stu-id="d3a72-149">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="d3a72-150">管道运算符 (`|` 将结果发送到) `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-150">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="d3a72-151">`-Wrap`参数将不适合行的文本定向到下一行。</span><span class="sxs-lookup"><span data-stu-id="d3a72-151">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="d3a72-152">`-Autosize`参数调整表列的大小以容纳文本。</span><span class="sxs-lookup"><span data-stu-id="d3a72-152">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="d3a72-153">使用函数提供程序路径</span><span class="sxs-lookup"><span data-stu-id="d3a72-153">Working with Function provider paths</span></span>

<span data-ttu-id="d3a72-154">这些命令均获取名为的函数 `c:` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-154">These commands both get the function named `c:`.</span></span> <span data-ttu-id="d3a72-155">第一个命令可在任何驱动器中使用。</span><span class="sxs-lookup"><span data-stu-id="d3a72-155">The first command can be used in any drive.</span></span> <span data-ttu-id="d3a72-156">第二个命令在驱动器中使用 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-156">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="d3a72-157">由于名称以冒号结束（这是驱动器的语法），因此必须使用驱动器名称来限定路径。</span><span class="sxs-lookup"><span data-stu-id="d3a72-157">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="d3a72-158">在 `Function:` 驱动器中，可以使用任何一种格式。</span><span class="sxs-lookup"><span data-stu-id="d3a72-158">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="d3a72-159">在第二个命令中，点 (`.`) 表示当前位置。</span><span class="sxs-lookup"><span data-stu-id="d3a72-159">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="d3a72-160">创建函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-160">Creating a function</span></span>

<span data-ttu-id="d3a72-161">此命令使用 `New-Item` cmdlet 创建名为的函数 `Win32:` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-161">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="d3a72-162">大括号中的表达式是以函数名称表示的脚本块。</span><span class="sxs-lookup"><span data-stu-id="d3a72-162">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="d3a72-163">还可以通过在 PowerShell 命令行中键入函数来创建该函数。</span><span class="sxs-lookup"><span data-stu-id="d3a72-163">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="d3a72-164">例如，tpe `Function:Win32: {Set-Location C:\Windows\System32}` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-164">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="d3a72-165">如果在 `Function:` 驱动器中，则可以省略驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="d3a72-165">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="d3a72-166">删除函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-166">Deleting a function</span></span>

<span data-ttu-id="d3a72-167">此命令 `more:` 从当前会话中删除该函数。</span><span class="sxs-lookup"><span data-stu-id="d3a72-167">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="d3a72-168">更改函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-168">Changing a function</span></span>

<span data-ttu-id="d3a72-169">此命令使用 `Set-Item` cmdlet 来更改函数， `prompt` 使其在路径之前显示时间。</span><span class="sxs-lookup"><span data-stu-id="d3a72-169">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="d3a72-170">重命名函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-170">Rename a function</span></span>

<span data-ttu-id="d3a72-171">此命令使用 `Rename-Item` cmdlet 将函数的名称更改 `help` 为 `gh` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-171">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="d3a72-172">复制函数</span><span class="sxs-lookup"><span data-stu-id="d3a72-172">Copying a function</span></span>

<span data-ttu-id="d3a72-173">此命令将 `prompt` 函数复制到 `oldPrompt` ，从而为与 prompt 函数相关联的脚本块有效地创建一个新名称。</span><span class="sxs-lookup"><span data-stu-id="d3a72-173">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="d3a72-174">如果计划更改原始 prompt 函数，你可以使用此命令来保存该函数。</span><span class="sxs-lookup"><span data-stu-id="d3a72-174">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="d3a72-175">新函数的 **Options** 属性的值为 `None` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-175">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="d3a72-176">若要更改 **Options** 属性的值，请使用 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-176">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="d3a72-177">动态参数</span><span class="sxs-lookup"><span data-stu-id="d3a72-177">Dynamic parameters</span></span>

<span data-ttu-id="d3a72-178">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="d3a72-178">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="d3a72-179">选项 < [ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="d3a72-179">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="d3a72-180">确定函数的 **Options** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d3a72-180">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="d3a72-181">`None`：无选项。</span><span class="sxs-lookup"><span data-stu-id="d3a72-181">`None`: No options.</span></span> <span data-ttu-id="d3a72-182">`None` 为默认值。</span><span class="sxs-lookup"><span data-stu-id="d3a72-182">`None` is the default.</span></span>
- <span data-ttu-id="d3a72-183">`Constant`：无法删除该函数，并且无法更改其属性。</span><span class="sxs-lookup"><span data-stu-id="d3a72-183">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="d3a72-184">`Constant` 仅在创建函数时才可用。</span><span class="sxs-lookup"><span data-stu-id="d3a72-184">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="d3a72-185">不能将现有函数的选项更改为 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-185">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="d3a72-186">`Private`：该函数仅在当前范围内可见</span><span class="sxs-lookup"><span data-stu-id="d3a72-186">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="d3a72-187"> (子范围) 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-187">(not in child scopes).</span></span>
- <span data-ttu-id="d3a72-188">`ReadOnly`：除使用参数外，不能更改函数的属性 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="d3a72-188">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="d3a72-189">您可以使用 `Remove-Item` 删除函数。</span><span class="sxs-lookup"><span data-stu-id="d3a72-189">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="d3a72-190">`AllScope`：该函数将复制到任何创建的新作用域。</span><span class="sxs-lookup"><span data-stu-id="d3a72-190">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="d3a72-191">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d3a72-191">Cmdlets supported</span></span>

- [<span data-ttu-id="d3a72-192">New-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-192">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="d3a72-193">Set-Item</span><span class="sxs-lookup"><span data-stu-id="d3a72-193">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="d3a72-194">使用管道</span><span class="sxs-lookup"><span data-stu-id="d3a72-194">Using the pipeline</span></span>

<span data-ttu-id="d3a72-195">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="d3a72-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="d3a72-196">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="d3a72-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="d3a72-197">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="d3a72-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="d3a72-198">获取帮助</span><span class="sxs-lookup"><span data-stu-id="d3a72-198">Getting help</span></span>

<span data-ttu-id="d3a72-199">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="d3a72-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="d3a72-200">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="d3a72-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="d3a72-201">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3a72-201">See also</span></span>

[<span data-ttu-id="d3a72-202">about_Functions</span><span class="sxs-lookup"><span data-stu-id="d3a72-202">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="d3a72-203">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d3a72-203">about_Providers</span></span>](../About/about_Providers.md)

