---
description: 变量
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variable 提供程序
ms.openlocfilehash: f93e58c24fdfc085983459d214db931274e164e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598672"
---
# <a name="variable-provider"></a><span data-ttu-id="6384f-103">变量提供程序</span><span class="sxs-lookup"><span data-stu-id="6384f-103">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="6384f-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="6384f-104">Provider name</span></span>
<span data-ttu-id="6384f-105">变量</span><span class="sxs-lookup"><span data-stu-id="6384f-105">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="6384f-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="6384f-106">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="6384f-107">功能</span><span class="sxs-lookup"><span data-stu-id="6384f-107">Capabilities</span></span>

<span data-ttu-id="6384f-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="6384f-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="6384f-109">简短说明</span><span class="sxs-lookup"><span data-stu-id="6384f-109">Short description</span></span>

<span data-ttu-id="6384f-110">提供对 PowerShell 变量及其值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="6384f-110">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="6384f-111">详细说明</span><span class="sxs-lookup"><span data-stu-id="6384f-111">Detailed description</span></span>

<span data-ttu-id="6384f-112">PowerShell **变量** 提供程序可让你获取、添加、更改、清除和删除当前控制台中的 PowerShell 变量。</span><span class="sxs-lookup"><span data-stu-id="6384f-112">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="6384f-113">PowerShell **变量** 提供程序支持 powershell 创建的变量，包括自动变量、首选项变量以及你创建的变量。</span><span class="sxs-lookup"><span data-stu-id="6384f-113">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="6384f-114">**变量** 驱动器是仅包含变量对象的平面命名空间。</span><span class="sxs-lookup"><span data-stu-id="6384f-114">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="6384f-115">这些变量没有子项。</span><span class="sxs-lookup"><span data-stu-id="6384f-115">The variables have no child items.</span></span>

<span data-ttu-id="6384f-116">**变量** 提供程序支持以下 cmdlet，这将在本文中介绍。</span><span class="sxs-lookup"><span data-stu-id="6384f-116">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="6384f-117">Get-Location</span><span class="sxs-lookup"><span data-stu-id="6384f-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="6384f-118">Set-Location</span><span class="sxs-lookup"><span data-stu-id="6384f-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="6384f-119">Get-Item</span><span class="sxs-lookup"><span data-stu-id="6384f-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="6384f-120">New-Item</span><span class="sxs-lookup"><span data-stu-id="6384f-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="6384f-121">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="6384f-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="6384f-122">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="6384f-122">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="6384f-123">PowerShell 还包括一组专门用于查看和更改变量的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6384f-123">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="6384f-124">使用 **可变** cmdlet 时，无需 `Variable:` 在名称中指定驱动器。</span><span class="sxs-lookup"><span data-stu-id="6384f-124">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="6384f-125">本文不介绍如何使用 **可变** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6384f-125">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="6384f-126">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="6384f-126">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="6384f-127">New-Variable</span><span class="sxs-lookup"><span data-stu-id="6384f-127">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="6384f-128">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="6384f-128">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="6384f-129">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="6384f-129">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="6384f-130">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="6384f-130">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="6384f-131">你还可以使用 PowerShell 表达式分析器来创建、查看和更改变量的值，而无需使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6384f-131">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="6384f-132">直接使用变量时，请使用美元符号 (`$`) 将该名称标识为变量，并将赋值运算符 (`=`) 以建立和更改其值。</span><span class="sxs-lookup"><span data-stu-id="6384f-132">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="6384f-133">例如， `$p = Get-Process` 创建 `p` 变量，并将命令的结果存储 `Get-Process` 在该变量中。</span><span class="sxs-lookup"><span data-stu-id="6384f-133">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="6384f-134">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="6384f-134">Types exposed by this provider</span></span>

<span data-ttu-id="6384f-135">变量可以是多种不同类型中的一种。</span><span class="sxs-lookup"><span data-stu-id="6384f-135">Variables can be one of several different types.</span></span> <span data-ttu-id="6384f-136">大多数变量都是类的实例 `PSVariable` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-136">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="6384f-137">下面列出了其他变量及其类型。</span><span class="sxs-lookup"><span data-stu-id="6384f-137">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="6384f-138">`?`变量是类的实例 `QuestionMarkVariable` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-138">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="6384f-139">`null`变量是类的实例 `NullVariable` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-139">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="6384f-140">最大计数变量是类的实例 `SessionStateCapacityVariable` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-140">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="6384f-141">`LocalVariable` 实例包含有关当前执行的信息，例如：</span><span class="sxs-lookup"><span data-stu-id="6384f-141">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="6384f-142">导航可变驱动器</span><span class="sxs-lookup"><span data-stu-id="6384f-142">Navigating the Variable drives</span></span>

<span data-ttu-id="6384f-143">**变量** 提供程序在驱动器中公开其数据存储 `Variable:` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-143">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="6384f-144">若要使用变量，可以将位置更改为 `Variable:` 驱动器 (`Set-Location Variable:`) ，也可以从任何其他 PowerShell 驱动器进行操作。</span><span class="sxs-lookup"><span data-stu-id="6384f-144">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="6384f-145">若要从其他位置引用变量，请在路径中使用驱动器名称 (`Variable:`) 。</span><span class="sxs-lookup"><span data-stu-id="6384f-145">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="6384f-146">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="6384f-146">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="6384f-147">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="6384f-147">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="6384f-148">还可以从任何其他 PowerShell 驱动器使用 **变量** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6384f-148">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="6384f-149">若要从其他位置引用变量，请 `Variable:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="6384f-149">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="6384f-150">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="6384f-150">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="6384f-151">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="6384f-151">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="6384f-152">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="6384f-152">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="6384f-153">显示变量的值</span><span class="sxs-lookup"><span data-stu-id="6384f-153">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="6384f-154">获取当前会话中的所有变量</span><span class="sxs-lookup"><span data-stu-id="6384f-154">Get all variables in the current session</span></span>

<span data-ttu-id="6384f-155">此命令将获取当前会话中所有变量及其值的列表。</span><span class="sxs-lookup"><span data-stu-id="6384f-155">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="6384f-156">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="6384f-156">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="6384f-157">使用其提供程序路径获取变量</span><span class="sxs-lookup"><span data-stu-id="6384f-157">Get a variable using its provider path</span></span>

<span data-ttu-id="6384f-158">此命令使用其提供程序路径检索变量值，其提供程序路径以美元符号 () 为前缀 `$` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-158">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="6384f-159">这与用美元符号 () 的变量名的前缀相同 `$` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-159">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="6384f-160">使用通配符获取变量</span><span class="sxs-lookup"><span data-stu-id="6384f-160">Get variables using wildcards</span></span>

<span data-ttu-id="6384f-161">此命令将获取名称以“max”开头的变量。</span><span class="sxs-lookup"><span data-stu-id="6384f-161">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="6384f-162">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="6384f-162">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="6384f-163">获取的值？</span><span class="sxs-lookup"><span data-stu-id="6384f-163">Get the value of the ?</span></span> <span data-ttu-id="6384f-164">可变</span><span class="sxs-lookup"><span data-stu-id="6384f-164">variable</span></span>

<span data-ttu-id="6384f-165">此命令使用 `-LiteralPath` [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的参数获取 `?` 驱动器中的变量的值 `Variable:` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-165">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="6384f-166">`?`是路径中的通配符，但不 `Get-ChildItem` 尝试解析参数值中的任何通配符 `-LiteralPath` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-166">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="6384f-167">获取 ReadOnly 和常量变量</span><span class="sxs-lookup"><span data-stu-id="6384f-167">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="6384f-168">此命令将获取 `ReadOnly` `Constant` 其 **Options** 属性的值为或的变量。</span><span class="sxs-lookup"><span data-stu-id="6384f-168">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="6384f-169">创建变量</span><span class="sxs-lookup"><span data-stu-id="6384f-169">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="6384f-170">创建新变量</span><span class="sxs-lookup"><span data-stu-id="6384f-170">Create a new variable</span></span>

<span data-ttu-id="6384f-171">此命令创建 `services` 变量，并将命令的结果存储 `Get-Service` 在该变量中。</span><span class="sxs-lookup"><span data-stu-id="6384f-171">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="6384f-172">由于当前位置位于驱动器中，因此 `Variable:` 参数的值 `-Path` 是一个点 (`.`) ，表示当前位置。</span><span class="sxs-lookup"><span data-stu-id="6384f-172">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="6384f-173">命令两边的括号 `Get-Service` 可确保在创建变量之前执行该命令。</span><span class="sxs-lookup"><span data-stu-id="6384f-173">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="6384f-174">如果没有圆括号，则新变量的值将为“Get-Service”字符串。</span><span class="sxs-lookup"><span data-stu-id="6384f-174">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="6384f-175">使用绝对路径创建变量</span><span class="sxs-lookup"><span data-stu-id="6384f-175">Create a variable using an absolute path</span></span>

<span data-ttu-id="6384f-176">此命令创建 `services` 变量，并将命令的结果存储 `Get-Service` 在该变量中。</span><span class="sxs-lookup"><span data-stu-id="6384f-176">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="6384f-177">若要创建不含值的变量，请省略赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="6384f-177">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="6384f-178">更改变量</span><span class="sxs-lookup"><span data-stu-id="6384f-178">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="6384f-179">重命名变量</span><span class="sxs-lookup"><span data-stu-id="6384f-179">Rename a variable</span></span>

<span data-ttu-id="6384f-180">此命令使用 `Rename-Item` cmdlet 将变量的名称更改 `a` 为 `processes` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-180">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="6384f-181">更改变量的值</span><span class="sxs-lookup"><span data-stu-id="6384f-181">Change the value of a variable</span></span>

<span data-ttu-id="6384f-182">此命令使用 `Set-Item` cmdlet 将该变量的值更改 `ErrorActionPreference` 为 "Stop"。</span><span class="sxs-lookup"><span data-stu-id="6384f-182">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="6384f-183">复制变量</span><span class="sxs-lookup"><span data-stu-id="6384f-183">Copy a variable</span></span>

<span data-ttu-id="6384f-184">此命令使用 `Copy-Item` cmdlet 将 `processes` 变量复制到 `old_processes` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-184">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="6384f-185">这将创建一个名为的新变量，该变量 `old_processes` 的值与变量的值相同 `processes` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-185">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="6384f-186">删除变量</span><span class="sxs-lookup"><span data-stu-id="6384f-186">Delete a variable</span></span>

<span data-ttu-id="6384f-187">此命令 `serv` 从当前会话中删除变量。</span><span class="sxs-lookup"><span data-stu-id="6384f-187">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="6384f-188">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="6384f-188">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="6384f-189">使用-Force 参数删除变量</span><span class="sxs-lookup"><span data-stu-id="6384f-189">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="6384f-190">此命令从当前会话中删除所有变量，但其 **Options** 属性值为的变量除外 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-190">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="6384f-191">如果没有 `-Force` 参数，则该命令不会删除其 **Options** 属性值为的变量 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="6384f-191">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="6384f-192">将变量的值设置为 NULL</span><span class="sxs-lookup"><span data-stu-id="6384f-192">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="6384f-193">此命令使用 `Clear-Item` cmdlet 将该变量的值更改 `processes` 为 NULL。</span><span class="sxs-lookup"><span data-stu-id="6384f-193">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="6384f-194">使用管道</span><span class="sxs-lookup"><span data-stu-id="6384f-194">Using the pipeline</span></span>

<span data-ttu-id="6384f-195">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="6384f-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="6384f-196">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="6384f-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="6384f-197">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="6384f-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="6384f-198">获取帮助</span><span class="sxs-lookup"><span data-stu-id="6384f-198">Getting help</span></span>

<span data-ttu-id="6384f-199">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="6384f-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="6384f-200">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="6384f-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="6384f-201">请参阅</span><span class="sxs-lookup"><span data-stu-id="6384f-201">See also</span></span>

[<span data-ttu-id="6384f-202">about_Variables</span><span class="sxs-lookup"><span data-stu-id="6384f-202">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="6384f-203">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="6384f-203">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="6384f-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6384f-204">about_Providers</span></span>](../About/about_Providers.md)

