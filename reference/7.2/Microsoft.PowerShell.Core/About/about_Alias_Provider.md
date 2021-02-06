---
description: Alias
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Alias 提供程序
ms.openlocfilehash: d6bfbaf878a6d971b1e01d963faec8c8ece5d1fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596854"
---
# <a name="alias-provider"></a><span data-ttu-id="aea2d-103">别名提供程序</span><span class="sxs-lookup"><span data-stu-id="aea2d-103">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="aea2d-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="aea2d-104">Provider name</span></span>
<span data-ttu-id="aea2d-105">Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-105">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="aea2d-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="aea2d-106">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="aea2d-107">功能</span><span class="sxs-lookup"><span data-stu-id="aea2d-107">Capabilities</span></span>

<span data-ttu-id="aea2d-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="aea2d-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="aea2d-109">简短说明</span><span class="sxs-lookup"><span data-stu-id="aea2d-109">Short description</span></span>

<span data-ttu-id="aea2d-110">提供对 PowerShell 别名及其所代表的值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="aea2d-110">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="aea2d-111">详细说明</span><span class="sxs-lookup"><span data-stu-id="aea2d-111">Detailed description</span></span>

<span data-ttu-id="aea2d-112">PowerShell **别名** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-112">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="aea2d-113">别名是 cmdlet、函数、可执行文件（包括脚本）的替代名称。</span><span class="sxs-lookup"><span data-stu-id="aea2d-113">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="aea2d-114">PowerShell 包含一组内置别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-114">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="aea2d-115">可以将自己的别名添加到当前会话和 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="aea2d-115">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="aea2d-116">**别名** 驱动器是只包含 Alias 对象的平面命名空间。</span><span class="sxs-lookup"><span data-stu-id="aea2d-116">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="aea2d-117">这些别名没有子项。</span><span class="sxs-lookup"><span data-stu-id="aea2d-117">The aliases have no child items.</span></span>

<span data-ttu-id="aea2d-118">**Alias** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="aea2d-118">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="aea2d-119">Get-Location</span><span class="sxs-lookup"><span data-stu-id="aea2d-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="aea2d-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="aea2d-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="aea2d-121">Get-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="aea2d-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="aea2d-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="aea2d-124">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-124">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="aea2d-125">PowerShell 包括一组用于查看和更改别名的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aea2d-125">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="aea2d-126">使用 **别名** cmdlet 时，无需 `Alias:` 在名称中指定驱动器。</span><span class="sxs-lookup"><span data-stu-id="aea2d-126">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="aea2d-127">本文不介绍如何使用 **别名** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aea2d-127">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="aea2d-128">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-128">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="aea2d-129">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-129">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="aea2d-130">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-130">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="aea2d-131">New-Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-131">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="aea2d-132">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="aea2d-132">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="aea2d-133">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="aea2d-133">Types exposed by this provider</span></span>

<span data-ttu-id="aea2d-134">每个别名都是 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="aea2d-134">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="aea2d-135">导航别名驱动器</span><span class="sxs-lookup"><span data-stu-id="aea2d-135">Navigating the Alias drive</span></span>

<span data-ttu-id="aea2d-136">**别名** 提供程序在驱动器中公开其数据存储 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-136">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="aea2d-137">若要使用别名，可以使用以下命令将位置更改为 `Alias:` 驱动器：</span><span class="sxs-lookup"><span data-stu-id="aea2d-137">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="aea2d-138">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="aea2d-138">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="aea2d-139">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="aea2d-139">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="aea2d-140">还可以从任何其他 PowerShell 驱动器使用别名提供程序。</span><span class="sxs-lookup"><span data-stu-id="aea2d-140">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="aea2d-141">若要从其他位置引用别名，请 `Alias:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="aea2d-141">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="aea2d-142">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="aea2d-142">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="aea2d-143">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-143">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="aea2d-144">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-144">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="aea2d-145">显示别名的内容：驱动器</span><span class="sxs-lookup"><span data-stu-id="aea2d-145">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="aea2d-146">此命令获取当前位置为驱动器时所有别名的列表 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-146">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="aea2d-147">它使用通配符 `*` 来指示当前位置的所有内容。</span><span class="sxs-lookup"><span data-stu-id="aea2d-147">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="aea2d-148">在 `Alias:` 驱动器中，表示当前位置的点， `.` 以及 `*` 表示当前位置中所有项的通配符，具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="aea2d-148">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="aea2d-149">例如， `Get-Item -Path .` 或 `Get-Item \*` 生成相同的结果。</span><span class="sxs-lookup"><span data-stu-id="aea2d-149">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="aea2d-150">别名提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-150">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="aea2d-151">获取所选别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-151">Get a selected alias</span></span>

<span data-ttu-id="aea2d-152">此命令将获取 `ls` 别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-152">This command gets the `ls` alias.</span></span>
<span data-ttu-id="aea2d-153">由于它包括路径，因此可以在任何 PowerShell 驱动器中使用它。</span><span class="sxs-lookup"><span data-stu-id="aea2d-153">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="aea2d-154">如果在 `Alias:` 驱动器中，则可以省略路径中的驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="aea2d-154">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="aea2d-155">还可以通过在提供程序路径前面加上美元符号 () 来检索别名的定义 `$` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-155">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="aea2d-156">获取特定 cmdlet 的所有别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-156">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="aea2d-157">此命令获取与 cmdlet 关联的别名列表 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-157">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="aea2d-158">它使用 **定义** 属性，该属性存储 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="aea2d-158">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="aea2d-159">创建别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-159">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="aea2d-160">从 Alias：驱动器创建别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-160">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="aea2d-161">此命令 `serv` 为 cmdlet 创建别名 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-161">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="aea2d-162">由于当前位置位于驱动器中，因此 `Alias:` `-Path` 不需要参数。</span><span class="sxs-lookup"><span data-stu-id="aea2d-162">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="aea2d-163">此命令还使用 `-Options` dynamic 参数在别名上设置 **AllScope** 选项。</span><span class="sxs-lookup"><span data-stu-id="aea2d-163">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="aea2d-164">`-Options` `New-Item` 仅当位于驱动器中时，此参数才会出现在 cmdlet 中 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-164">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="aea2d-165">点 (`.`) 指示当前目录，即别名驱动器。</span><span class="sxs-lookup"><span data-stu-id="aea2d-165">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="aea2d-166">创建具有绝对路径的别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-166">Create an alias with an absolute path</span></span>

<span data-ttu-id="aea2d-167">你可以为可调用命令的任意项创建别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-167">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="aea2d-168">此命令为创建 `np` 别名 `Notepad.exe` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-168">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="aea2d-169">为新函数创建别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-169">Create an alias to a new function</span></span>

<span data-ttu-id="aea2d-170">你可以为任意函数创建别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-170">You can create an alias for any function.</span></span> <span data-ttu-id="aea2d-171">可使用此功能创建一个包括 cmdlet 及其参数的别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-171">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="aea2d-172">第一个命令创建 `CD32` 函数，该函数将当前目录更改为 `System32` 目录。</span><span class="sxs-lookup"><span data-stu-id="aea2d-172">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="aea2d-173">第二个命令 `go` 为函数创建别名 `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-173">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="aea2d-174">完成该命令后，可以使用 `CD32` 或 `go` 来调用函数。</span><span class="sxs-lookup"><span data-stu-id="aea2d-174">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="aea2d-175">更改别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-175">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="aea2d-176">更改别名选项</span><span class="sxs-lookup"><span data-stu-id="aea2d-176">Change the options of an alias</span></span>

<span data-ttu-id="aea2d-177">可以将 `Set-Item` cmdlet 与 `-Options` 动态参数一起使用来更改别名的属性的值 `-Options` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-177">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="aea2d-178">此命令设置别名的 **AllScope** 和 **ReadOnly** 选项 `dir` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-178">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="aea2d-179">该命令使用 `-Options` cmdlet 的动态参数 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-179">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="aea2d-180">`-Options` `Set-Item` 当你将参数与 **Alias** 或 **Function** 提供程序一起使用时，可在中使用。</span><span class="sxs-lookup"><span data-stu-id="aea2d-180">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="aea2d-181">更改别名引用命令</span><span class="sxs-lookup"><span data-stu-id="aea2d-181">Change an aliases referenced command</span></span>

<span data-ttu-id="aea2d-182">此命令使用 `Set-Item` cmdlet 来更改别名， `gp` 使其表示 `Get-Process` cmdlet 而不是 `Get-ItemProperty` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aea2d-182">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="aea2d-183">`-Force`参数是必需的，因为别名的 **Options** 属性的值 `gp` 设置为 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-183">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="aea2d-184">因为该命令是从驱动器内部提交的 `Alias:` ，所以未在路径中指定该驱动器。</span><span class="sxs-lookup"><span data-stu-id="aea2d-184">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="aea2d-185">更改将影响四个用于定义别名和命令之间的关联的属性。</span><span class="sxs-lookup"><span data-stu-id="aea2d-185">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="aea2d-186">若要查看更改的效果，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="aea2d-186">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="aea2d-187">重命名别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-187">Rename an alias</span></span>

<span data-ttu-id="aea2d-188">此命令使用 `Rename-Item` cmdlet 将 `popd` 别名更改为 `pop` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-188">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="aea2d-189">复制别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-189">Copying an alias</span></span>

<span data-ttu-id="aea2d-190">此命令复制 `pushd` 别名，以便为 `push` cmdlet 创建新别名 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-190">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="aea2d-191">创建新别名后，其 **Description** 属性的值为 null。</span><span class="sxs-lookup"><span data-stu-id="aea2d-191">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="aea2d-192">而且，其 **选项** 属性的值为 `None` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-192">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="aea2d-193">如果命令是从驱动器内部发出的 `Alias:` ，则可以从参数的值中省略驱动器名称 `-Path` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-193">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="aea2d-194">删除别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-194">Deleting an alias</span></span>

<span data-ttu-id="aea2d-195">此命令 `serv` 从当前会话中删除别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-195">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="aea2d-196">可以在任何 PowerShell 驱动器中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="aea2d-196">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="aea2d-197">此命令删除以“s”开头的别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-197">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="aea2d-198">它不会删除只读别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-198">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="aea2d-199">删除只读别名</span><span class="sxs-lookup"><span data-stu-id="aea2d-199">Delete read-only aliases</span></span>

<span data-ttu-id="aea2d-200">此命令从当前会话中删除所有别名，但 `Constant` 其 **Options** 属性的值除外。</span><span class="sxs-lookup"><span data-stu-id="aea2d-200">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="aea2d-201">`-Force`参数允许命令删除其 **Options** 属性值为的别名 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-201">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="aea2d-202">动态参数</span><span class="sxs-lookup"><span data-stu-id="aea2d-202">Dynamic parameters</span></span>

<span data-ttu-id="aea2d-203">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="aea2d-203">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="aea2d-204">选项 [ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="aea2d-204">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="aea2d-205">确定别名的 **Options** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="aea2d-205">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="aea2d-206">**None**：无选项。</span><span class="sxs-lookup"><span data-stu-id="aea2d-206">**None**: No options.</span></span> <span data-ttu-id="aea2d-207">此值为默认值。</span><span class="sxs-lookup"><span data-stu-id="aea2d-207">This value is the default.</span></span>
- <span data-ttu-id="aea2d-208">**常量**：无法删除别名，也无法更改其属性。</span><span class="sxs-lookup"><span data-stu-id="aea2d-208">**Constant**:The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="aea2d-209">**常量** 仅在创建别名时才可用。</span><span class="sxs-lookup"><span data-stu-id="aea2d-209">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="aea2d-210">不能将现有别名的选项更改为 **常量**。</span><span class="sxs-lookup"><span data-stu-id="aea2d-210">You cannot change the option of an existing alias to **Constant**.</span></span>
- <span data-ttu-id="aea2d-211">**Private**：别名仅在当前作用域（而不是子作用域）中可见。</span><span class="sxs-lookup"><span data-stu-id="aea2d-211">**Private**:The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="aea2d-212">**ReadOnly**：除非使用参数，否则无法更改别名的属性 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="aea2d-212">**ReadOnly**:The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="aea2d-213">您可以使用 `Remove-Item` 来删除别名。</span><span class="sxs-lookup"><span data-stu-id="aea2d-213">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="aea2d-214">**AllScope**：将别名复制到任何创建的新作用域。</span><span class="sxs-lookup"><span data-stu-id="aea2d-214">**AllScope**:The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea2d-215">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="aea2d-215">Cmdlets supported</span></span>

- [<span data-ttu-id="aea2d-216">New-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-216">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="aea2d-217">Set-Item</span><span class="sxs-lookup"><span data-stu-id="aea2d-217">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="aea2d-218">使用管道</span><span class="sxs-lookup"><span data-stu-id="aea2d-218">Using the pipeline</span></span>

<span data-ttu-id="aea2d-219">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="aea2d-219">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="aea2d-220">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="aea2d-220">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="aea2d-221">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="aea2d-221">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="aea2d-222">获取帮助</span><span class="sxs-lookup"><span data-stu-id="aea2d-222">Getting help</span></span>

<span data-ttu-id="aea2d-223">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="aea2d-223">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="aea2d-224">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="aea2d-224">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="aea2d-225">请参阅</span><span class="sxs-lookup"><span data-stu-id="aea2d-225">See also</span></span>

[<span data-ttu-id="aea2d-226">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="aea2d-226">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="aea2d-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="aea2d-227">about_Providers</span></span>](../About/about_Providers.md)

