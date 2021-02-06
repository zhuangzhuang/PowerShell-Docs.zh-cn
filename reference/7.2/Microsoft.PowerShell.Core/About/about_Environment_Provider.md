---
description: 环境
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Environment 提供程序
ms.openlocfilehash: f50558ba23d21b5ca145a06086c1c6d9b1fcd3bf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597268"
---
# <a name="environment-provider"></a><span data-ttu-id="9443b-103">环境提供程序</span><span class="sxs-lookup"><span data-stu-id="9443b-103">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="9443b-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="9443b-104">Provider name</span></span>
<span data-ttu-id="9443b-105">环境</span><span class="sxs-lookup"><span data-stu-id="9443b-105">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="9443b-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="9443b-106">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="9443b-107">功能</span><span class="sxs-lookup"><span data-stu-id="9443b-107">Capabilities</span></span>

<span data-ttu-id="9443b-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="9443b-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="9443b-109">简短说明</span><span class="sxs-lookup"><span data-stu-id="9443b-109">Short description</span></span>

<span data-ttu-id="9443b-110">提供对 Windows 环境变量的访问权限。</span><span class="sxs-lookup"><span data-stu-id="9443b-110">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="9443b-111">详细说明</span><span class="sxs-lookup"><span data-stu-id="9443b-111">Detailed description</span></span>

<span data-ttu-id="9443b-112">PowerShell **环境** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的环境变量和值。</span><span class="sxs-lookup"><span data-stu-id="9443b-112">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="9443b-113">**环境** 变量是动态命名的变量，用于描述程序运行的环境。</span><span class="sxs-lookup"><span data-stu-id="9443b-113">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="9443b-114">Windows 和 PowerShell 使用环境变量来存储影响系统和进程执行的持久性信息。</span><span class="sxs-lookup"><span data-stu-id="9443b-114">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="9443b-115">与 PowerShell 变量不同，环境变量不服从范围约束。</span><span class="sxs-lookup"><span data-stu-id="9443b-115">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="9443b-116">**环境** 驱动器是一个平面命名空间，其中包含特定于当前用户的会话的环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-116">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="9443b-117">环境变量没有子项。</span><span class="sxs-lookup"><span data-stu-id="9443b-117">The environment variables have no child items.</span></span>

<span data-ttu-id="9443b-118">**环境** 提供程序支持以下 cmdlet，这将在本文中介绍。</span><span class="sxs-lookup"><span data-stu-id="9443b-118">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="9443b-119">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9443b-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="9443b-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9443b-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="9443b-121">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9443b-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="9443b-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="9443b-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="9443b-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9443b-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="9443b-124">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9443b-124">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="9443b-125">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="9443b-125">Types exposed by this provider</span></span>

<span data-ttu-id="9443b-126">每个环境变量都是 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="9443b-126">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="9443b-127">变量的名称是字典键。</span><span class="sxs-lookup"><span data-stu-id="9443b-127">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="9443b-128">环境变量的值是字典值。</span><span class="sxs-lookup"><span data-stu-id="9443b-128">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="9443b-129">导航环境驱动器</span><span class="sxs-lookup"><span data-stu-id="9443b-129">Navigating the Environment drive</span></span>

<span data-ttu-id="9443b-130">**环境** 提供程序在驱动器中公开其数据存储 `Env:` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-130">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="9443b-131">若要使用环境变量，请将你的位置更改为 `Env:` 驱动器 (`Set-Location Env:`) 或从另一个 PowerShell 驱动器工作。</span><span class="sxs-lookup"><span data-stu-id="9443b-131">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="9443b-132">若要从其他位置引用环境变量，请 `Env:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="9443b-132">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="9443b-133">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="9443b-133">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="9443b-134">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="9443b-134">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="9443b-135">你还可以从任何其他 PowerShell 驱动器使用该 **环境** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="9443b-135">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="9443b-136">若要从其他位置引用环境变量，请 `Env:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="9443b-136">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="9443b-137">**环境** 提供程序还使用的变量前缀公开环境变量 `$env:` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-137">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="9443b-138">以下命令将查看 **ProgramFiles** 环境变量的内容。</span><span class="sxs-lookup"><span data-stu-id="9443b-138">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="9443b-139">`$env:`可以在任何 PowerShell 驱动器中使用变量前缀。</span><span class="sxs-lookup"><span data-stu-id="9443b-139">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="9443b-140">还可以使用变量前缀来更改环境变量的值 `$env:` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-140">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="9443b-141">只要活动有效，所做的任何更改仅适用于当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="9443b-141">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="9443b-142">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="9443b-142">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="9443b-143">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="9443b-143">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="9443b-144">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="9443b-144">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="9443b-145">获取环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-145">Getting environment variables</span></span>

<span data-ttu-id="9443b-146">此命令列出当前会话中的所有环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-146">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="9443b-147">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="9443b-147">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="9443b-148">环境提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-148">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="9443b-149">获取选定的环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-149">Get a selected environment variable</span></span>

<span data-ttu-id="9443b-150">此命令获取 `WINDIR` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-150">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="9443b-151">还可以使用变量前缀格式。</span><span class="sxs-lookup"><span data-stu-id="9443b-151">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="9443b-152">创建环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-152">Create an environment variable</span></span>

<span data-ttu-id="9443b-153">此命令创建 `USERMODE` 值为 "非管理员" 的环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-153">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="9443b-154">`-Path`参数值在驱动器中创建新项 `Env:` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-154">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="9443b-155">仅在当前 PowerShell 会话中可使用新的环境变量，前提是它处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="9443b-155">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="9443b-156">更改环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-156">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="9443b-157">重命名环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-157">Rename an environment variable</span></span>

<span data-ttu-id="9443b-158">此命令使用 `Rename-Item` cmdlet 将创建的环境变量的名称更改 `USERMODE` 为 `USERROLE` 。</span><span class="sxs-lookup"><span data-stu-id="9443b-158">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="9443b-159">不要更改系统所使用的环境变量的名称。</span><span class="sxs-lookup"><span data-stu-id="9443b-159">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="9443b-160">尽管这些更改仅影响当前会话，但它们可能会导致系统或程序无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="9443b-160">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="9443b-161">更改环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-161">Change an environment variable</span></span>

<span data-ttu-id="9443b-162">此命令使用 `Set-Item` cmdlet 将环境变量的值更改 `USERROLE` 为 "Administrator"。</span><span class="sxs-lookup"><span data-stu-id="9443b-162">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="9443b-163">复制环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-163">Copy an environment variable</span></span>

<span data-ttu-id="9443b-164">此命令将环境变量的值复制 `USERROLE` 到 `USERROLE2` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-164">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="9443b-165">删除环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-165">Remove an environment variable</span></span>

<span data-ttu-id="9443b-166">此命令 `USERROLE2` 从当前会话中删除环境变量。</span><span class="sxs-lookup"><span data-stu-id="9443b-166">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="9443b-167">删除具有 Clear-Item 的环境变量</span><span class="sxs-lookup"><span data-stu-id="9443b-167">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="9443b-168">此命令 `USERROLE` 通过清除环境变量的值来删除它。</span><span class="sxs-lookup"><span data-stu-id="9443b-168">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="9443b-169">使用管道</span><span class="sxs-lookup"><span data-stu-id="9443b-169">Using the pipeline</span></span>

<span data-ttu-id="9443b-170">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="9443b-170">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="9443b-171">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="9443b-171">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="9443b-172">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="9443b-172">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="9443b-173">获取帮助</span><span class="sxs-lookup"><span data-stu-id="9443b-173">Getting help</span></span>

<span data-ttu-id="9443b-174">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="9443b-174">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="9443b-175">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="9443b-175">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="9443b-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="9443b-176">See also</span></span>

[<span data-ttu-id="9443b-177">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9443b-177">about_Providers</span></span>](../About/about_Providers.md)

