---
description: 介绍 PowerShell 提供程序如何提供对在命令行中无法轻松访问的数据和组件的访问。 数据以类似于文件系统驱动器的一致格式显示。
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 6073ef13a6d0a02cded69073d7ffaef903a807ea
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596012"
---
# <a name="about-providers"></a><span data-ttu-id="9537c-104">关于提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-104">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="9537c-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="9537c-105">Short description</span></span>
<span data-ttu-id="9537c-106">介绍 PowerShell 提供程序如何提供对在命令行中无法轻松访问的数据和组件的访问。</span><span class="sxs-lookup"><span data-stu-id="9537c-106">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="9537c-107">数据以类似于文件系统驱动器的一致格式显示。</span><span class="sxs-lookup"><span data-stu-id="9537c-107">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="9537c-108">长说明</span><span class="sxs-lookup"><span data-stu-id="9537c-108">Long description</span></span>

<span data-ttu-id="9537c-109">PowerShell 提供程序是 .NET 程序，可提供对专用数据存储区的访问权限，便于查看和管理。</span><span class="sxs-lookup"><span data-stu-id="9537c-109">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="9537c-110">数据显示在驱动器中，你可以访问路径中的数据，就像在硬盘驱动器上访问数据一样。</span><span class="sxs-lookup"><span data-stu-id="9537c-110">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="9537c-111">你可以使用提供程序支持的任何内置 cmdlet 来管理提供程序驱动器中的数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-111">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="9537c-112">而且，你可以使用专为数据设计的自定义 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9537c-112">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="9537c-113">提供程序还可以向内置 cmdlet 添加动态参数。</span><span class="sxs-lookup"><span data-stu-id="9537c-113">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="9537c-114">仅当你将 cmdlet 与提供程序数据结合使用时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="9537c-114">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="9537c-115">内置提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-115">Built-in providers</span></span>

<span data-ttu-id="9537c-116">PowerShell 包含一组内置提供程序，可用于访问不同类型的数据存储区。</span><span class="sxs-lookup"><span data-stu-id="9537c-116">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="9537c-117">提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-117">Provider</span></span>   |   <span data-ttu-id="9537c-118">驱动器 () </span><span class="sxs-lookup"><span data-stu-id="9537c-118">Drive(s)</span></span>  |<span data-ttu-id="9537c-119">OutputType</span><span class="sxs-lookup"><span data-stu-id="9537c-119">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="9537c-120">Alias</span><span class="sxs-lookup"><span data-stu-id="9537c-120">Alias</span></span>       |<span data-ttu-id="9537c-121">Alias:</span><span class="sxs-lookup"><span data-stu-id="9537c-121">Alias:</span></span>       |<span data-ttu-id="9537c-122">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="9537c-122">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="9537c-123">证书</span><span class="sxs-lookup"><span data-stu-id="9537c-123">Certificate</span></span> |<span data-ttu-id="9537c-124">Cert:</span><span class="sxs-lookup"><span data-stu-id="9537c-124">Cert:</span></span>        |<span data-ttu-id="9537c-125">Microsoft.powershell.commands.x509storelocation。</span><span class="sxs-lookup"><span data-stu-id="9537c-125">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="9537c-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="9537c-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="9537c-127">环境</span><span class="sxs-lookup"><span data-stu-id="9537c-127">Environment</span></span> |<span data-ttu-id="9537c-128">Env:</span><span class="sxs-lookup"><span data-stu-id="9537c-128">Env:</span></span>         |<span data-ttu-id="9537c-129">DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="9537c-129">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="9537c-130">FileSystem</span><span class="sxs-lookup"><span data-stu-id="9537c-130">FileSystem</span></span>  |<span data-ttu-id="9537c-131">C： ( \* ) </span><span class="sxs-lookup"><span data-stu-id="9537c-131">C: (\*)</span></span>       |<span data-ttu-id="9537c-132">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="9537c-132">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="9537c-133">System.IO.DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="9537c-133">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="9537c-134">函数</span><span class="sxs-lookup"><span data-stu-id="9537c-134">Function</span></span>    |<span data-ttu-id="9537c-135">函数：</span><span class="sxs-lookup"><span data-stu-id="9537c-135">Function:</span></span>    |<span data-ttu-id="9537c-136">System.web. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="9537c-136">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="9537c-137">注册表</span><span class="sxs-lookup"><span data-stu-id="9537c-137">Registry</span></span>    |<span data-ttu-id="9537c-138">HKLM： HKCU：</span><span class="sxs-lookup"><span data-stu-id="9537c-138">HKLM: HKCU:</span></span>  |<span data-ttu-id="9537c-139">。 RegistryKey</span><span class="sxs-lookup"><span data-stu-id="9537c-139">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="9537c-140">变量</span><span class="sxs-lookup"><span data-stu-id="9537c-140">Variable</span></span>    |<span data-ttu-id="9537c-141">Variable:</span><span class="sxs-lookup"><span data-stu-id="9537c-141">Variable:</span></span>    |<span data-ttu-id="9537c-142">System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="9537c-142">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="9537c-143">WSMan</span><span class="sxs-lookup"><span data-stu-id="9537c-143">WSMan</span></span>       |<span data-ttu-id="9537c-144">WSMan：</span><span class="sxs-lookup"><span data-stu-id="9537c-144">WSMan:</span></span>       |<span data-ttu-id="9537c-145">WSManConfigContainerElement。</span><span class="sxs-lookup"><span data-stu-id="9537c-145">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="9537c-146"> (\ * ) 文件系统驱动器在每个系统上各不相同。</span><span class="sxs-lookup"><span data-stu-id="9537c-146">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="9537c-147">您还可以创建自己的 PowerShell 提供程序，并可以安装其他人开发的提供程序。</span><span class="sxs-lookup"><span data-stu-id="9537c-147">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="9537c-148">若要列出会话中可用的提供程序，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-148">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="9537c-149">安装和删除提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-149">Installing and removing providers</span></span>

<span data-ttu-id="9537c-150">提供程序通常通过 PowerShell 模块进行安装。</span><span class="sxs-lookup"><span data-stu-id="9537c-150">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="9537c-151">导入模块会将提供程序加载到会话中。</span><span class="sxs-lookup"><span data-stu-id="9537c-151">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="9537c-152">无法卸载内置提供程序。</span><span class="sxs-lookup"><span data-stu-id="9537c-152">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="9537c-153">你可以卸载其他模块加载的提供程序。</span><span class="sxs-lookup"><span data-stu-id="9537c-153">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="9537c-154">可以使用 cmdlet 从当前会话中卸载提供程序 `Remove-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9537c-154">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="9537c-155">此 cmdlet 不会卸载提供程序，但它会使提供程序在会话中不可用。</span><span class="sxs-lookup"><span data-stu-id="9537c-155">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="9537c-156">你还可以使用 `Remove-PSDrive` cmdlet 从当前会话中删除任何驱动器。</span><span class="sxs-lookup"><span data-stu-id="9537c-156">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="9537c-157">驱动器上的这些数据不受影响，但该驱动器在该会话中不再可用。</span><span class="sxs-lookup"><span data-stu-id="9537c-157">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="9537c-158">查看提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-158">Viewing providers</span></span>

<span data-ttu-id="9537c-159">若要查看计算机上的 PowerShell 提供程序，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-159">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="9537c-160">输出会列出内置提供程序以及添加到会话中的提供程序。</span><span class="sxs-lookup"><span data-stu-id="9537c-160">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="9537c-161">提供程序 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-161">The provider cmdlets</span></span>

<span data-ttu-id="9537c-162">以下 cmdlet 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-162">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9537c-163">您可以使用相同的 cmdlet 来管理提供程序公开的不同类型的数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-163">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="9537c-164">了解管理一个提供程序的数据后，可以对任何提供程序的数据使用相同的过程。</span><span class="sxs-lookup"><span data-stu-id="9537c-164">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="9537c-165">例如，cmdlet 会 `New-Item` 创建一个新项。</span><span class="sxs-lookup"><span data-stu-id="9537c-165">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="9537c-166">在 `C:` **FileSystem** 提供程序支持的驱动器中，可以使用 `New-Item` 来创建新的文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="9537c-166">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="9537c-167">在 **注册表** 提供程序支持的驱动器中，可以使用 `New-Item` 来创建新的注册表项。</span><span class="sxs-lookup"><span data-stu-id="9537c-167">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="9537c-168">在 `Alias:` 驱动器中，可以使用 `New-Item` 创建新别名。</span><span class="sxs-lookup"><span data-stu-id="9537c-168">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="9537c-169">有关以下任何 cmdlet 的详细信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-169">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="9537c-170">Get-childitem cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-170">ChildItem cmdlets</span></span>

- [<span data-ttu-id="9537c-171">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9537c-171">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="9537c-172">内容 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-172">Content Cmdlets</span></span>

- [<span data-ttu-id="9537c-173">Add-Content</span><span class="sxs-lookup"><span data-stu-id="9537c-173">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="9537c-174">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="9537c-174">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="9537c-175">Get-Content</span><span class="sxs-lookup"><span data-stu-id="9537c-175">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="9537c-176">Set-Content</span><span class="sxs-lookup"><span data-stu-id="9537c-176">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="9537c-177">项 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-177">Item Cmdlets</span></span>

- [<span data-ttu-id="9537c-178">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-178">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="9537c-179">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-179">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="9537c-180">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-180">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="9537c-181">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-181">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="9537c-182">Move-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-182">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="9537c-183">New-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-183">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="9537c-184">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-184">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="9537c-185">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-185">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="9537c-186">Set-Item</span><span class="sxs-lookup"><span data-stu-id="9537c-186">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="9537c-187">Set-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-187">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="9537c-188">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-188">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="9537c-189">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-189">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="9537c-190">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-190">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="9537c-191">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-191">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="9537c-192">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-192">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="9537c-193">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-193">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="9537c-194">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-194">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="9537c-195">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9537c-195">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="9537c-196">位置 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-196">Location cmdlets</span></span>

- [<span data-ttu-id="9537c-197">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9537c-197">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="9537c-198">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="9537c-198">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="9537c-199">Push-Location</span><span class="sxs-lookup"><span data-stu-id="9537c-199">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="9537c-200">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9537c-200">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="9537c-201">路径 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-201">Path cmdlets</span></span>

- [<span data-ttu-id="9537c-202">Join-Path</span><span class="sxs-lookup"><span data-stu-id="9537c-202">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="9537c-203">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="9537c-203">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="9537c-204">Split-Path</span><span class="sxs-lookup"><span data-stu-id="9537c-204">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="9537c-205">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="9537c-205">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="9537c-206">Test-Path</span><span class="sxs-lookup"><span data-stu-id="9537c-206">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="9537c-207">New-psdrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-207">PSDrive cmdlets</span></span>

- [<span data-ttu-id="9537c-208">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9537c-208">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="9537c-209">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9537c-209">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="9537c-210">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9537c-210">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="9537c-211">PSProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9537c-211">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="9537c-212">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="9537c-212">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="9537c-213">查看提供程序数据</span><span class="sxs-lookup"><span data-stu-id="9537c-213">Viewing provider data</span></span>

<span data-ttu-id="9537c-214">提供程序的主要优点是，它以一种熟悉且一致的方式公开其数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-214">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="9537c-215">数据显示模型是文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="9537c-215">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="9537c-216">提供程序允许您查看、导航和更改数据存储中的项，就好像它们是文件系统中的数据一样。</span><span class="sxs-lookup"><span data-stu-id="9537c-216">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="9537c-217">数据存储区由它所支持的驱动器的名称访问。</span><span class="sxs-lookup"><span data-stu-id="9537c-217">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="9537c-218">此驱动器在 cmdlet 的默认显示中列出 `Get-PSProvider` ，但你可以使用 cmdlet 获取有关提供程序驱动器的信息 `Get-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="9537c-218">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="9537c-219">例如，若要获取 Function：驱动器的所有属性，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-219">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="9537c-220">与在文件系统驱动器上一样，你可以在提供程序驱动器中查看和移动数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-220">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="9537c-221">若要查看提供程序驱动器的内容，请使用 Get-Item 或 Get-ChildItem cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9537c-221">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="9537c-222">键入驱动器名称后跟一个冒号 (： ) 。</span><span class="sxs-lookup"><span data-stu-id="9537c-222">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="9537c-223">例如，若要查看 Alias：驱动器的内容，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-223">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="9537c-224">可以通过在路径中包括驱动器名称，从另一个驱动器查看和管理任何驱动器中的数据。</span><span class="sxs-lookup"><span data-stu-id="9537c-224">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="9537c-225">例如，若要查看其他驱动器中的 HKLM：驱动器中的 HKLM\Software 注册表项，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-225">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="9537c-226">若要打开驱动器，请使用 Set-Location cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9537c-226">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="9537c-227">指定驱动器路径时，请记住冒号。</span><span class="sxs-lookup"><span data-stu-id="9537c-227">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="9537c-228">例如，若要将你的位置更改为 Cert：驱动器的根目录，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-228">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="9537c-229">然后，若要查看 Cert：驱动器的内容，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-229">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="9537c-230">通过分层数据移动</span><span class="sxs-lookup"><span data-stu-id="9537c-230">Moving through hierarchical data</span></span>

<span data-ttu-id="9537c-231">与硬盘驱动器一样，你可以通过提供商驱动器进行移动。</span><span class="sxs-lookup"><span data-stu-id="9537c-231">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="9537c-232">如果数据排列在项中项的层次结构中，请使用反斜杠 (`\`) 来指示子项。</span><span class="sxs-lookup"><span data-stu-id="9537c-232">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="9537c-233">使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="9537c-233">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="9537c-234">例如，若要将你的位置更改为 HKLM\Software 注册表项，请键入 Set-Location 命令，例如：</span><span class="sxs-lookup"><span data-stu-id="9537c-234">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="9537c-235">如果完全限定名称中的任何元素包含空格，则必须将名称用双引号引起来 (`"`) 。</span><span class="sxs-lookup"><span data-stu-id="9537c-235">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="9537c-236">下面的示例显示了包含空格的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="9537c-236">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="9537c-237">还可以对位置使用相对引用。</span><span class="sxs-lookup"><span data-stu-id="9537c-237">You can also use relative references to locations.</span></span> <span data-ttu-id="9537c-238">一个点 (`.`) 表示当前位置。</span><span class="sxs-lookup"><span data-stu-id="9537c-238">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="9537c-239">例如，如果你在 `HKLM:\Software\Microsoft` 注册表项中，并且想要列出注册表项中的注册表子项 `HKLM:\Software\Microsoft\PowerShell` ，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="9537c-239">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="9537c-240">另外，双点 (`..`) 是指直接位于当前位置上方的目录或容器。</span><span class="sxs-lookup"><span data-stu-id="9537c-240">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="9537c-241">您可以使用双点 (`..`) 在提供程序层次结构中导航。</span><span class="sxs-lookup"><span data-stu-id="9537c-241">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="9537c-242">提供商主页</span><span class="sxs-lookup"><span data-stu-id="9537c-242">Provider Home</span></span>

<span data-ttu-id="9537c-243">提供程序还具有 **主** 位置。</span><span class="sxs-lookup"><span data-stu-id="9537c-243">Providers also have a **Home** location.</span></span>  <span data-ttu-id="9537c-244">此位置由提供程序所支持的全部共享 `PSDrives` 。</span><span class="sxs-lookup"><span data-stu-id="9537c-244">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="9537c-245">可以通过查看提供程序的 **Home** 属性来检索它。</span><span class="sxs-lookup"><span data-stu-id="9537c-245">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="9537c-246">**FileSystem** 提供程序是唯一具有 **Home** 默认值的提供程序。</span><span class="sxs-lookup"><span data-stu-id="9537c-246">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="9537c-247">它的值与相同 `$Home` 。</span><span class="sxs-lookup"><span data-stu-id="9537c-247">It's the same value as `$Home`.</span></span> <span data-ttu-id="9537c-248">有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9537c-248">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="9537c-249">你可以使用其属性为当前会话设置提供程序的 **主** 目录。</span><span class="sxs-lookup"><span data-stu-id="9537c-249">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="9537c-250">`~`字符可用于表示提供程序的主目录。</span><span class="sxs-lookup"><span data-stu-id="9537c-250">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="9537c-251">如果提供程序没有设置 **主** 位置，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="9537c-251">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="9537c-252">查找动态参数</span><span class="sxs-lookup"><span data-stu-id="9537c-252">Finding dynamic parameters</span></span>

<span data-ttu-id="9537c-253">动态参数是由提供程序添加到 cmdlet 的 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="9537c-253">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="9537c-254">这些参数仅在 cmdlet 与添加它们的提供程序一起使用时才可用。</span><span class="sxs-lookup"><span data-stu-id="9537c-254">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="9537c-255">例如， `Cert:` 驱动器将 **CodeSigningCert** 参数添加到 `Get-Item` 和 `Get-ChildItem` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9537c-255">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="9537c-256">仅当在驱动器中使用或时，才可以使用此参数 `Get-Item` `Get-ChildItem` `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="9537c-256">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="9537c-257">有关提供程序支持的动态参数的列表，请参阅提供程序的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="9537c-257">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="9537c-258">类型：</span><span class="sxs-lookup"><span data-stu-id="9537c-258">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="9537c-259">例如：</span><span class="sxs-lookup"><span data-stu-id="9537c-259">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="9537c-260">了解提供程序</span><span class="sxs-lookup"><span data-stu-id="9537c-260">Learning about providers</span></span>

<span data-ttu-id="9537c-261">尽管所有提供程序数据都显示在驱动器中，并且你使用相同的方法在这些数据中移动，但相似性却停止了。</span><span class="sxs-lookup"><span data-stu-id="9537c-261">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="9537c-262">提供程序公开的数据存储可能与 Active Directory 位置和 Microsoft Exchange Server 邮箱不同。</span><span class="sxs-lookup"><span data-stu-id="9537c-262">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="9537c-263">有关各个 PowerShell 提供程序的信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-263">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="9537c-264">例如：</span><span class="sxs-lookup"><span data-stu-id="9537c-264">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="9537c-265">有关提供程序的帮助主题的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="9537c-265">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="9537c-266">请参阅</span><span class="sxs-lookup"><span data-stu-id="9537c-266">See also</span></span>

[<span data-ttu-id="9537c-267">about_Locations</span><span class="sxs-lookup"><span data-stu-id="9537c-267">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="9537c-268">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="9537c-268">about_Path_Syntax</span></span>](about_Path_Syntax.md)

