---
description: 列出旨在与 PowerShell 提供程序一起使用的 cmdlet。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 1f023c5a66265f561ef6644afdc45cd0149f35b7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598703"
---
# <a name="about-core-commands"></a><span data-ttu-id="66751-103">关于核心命令</span><span class="sxs-lookup"><span data-stu-id="66751-103">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="66751-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="66751-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="66751-105">列出旨在与 PowerShell 提供程序一起使用的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66751-105">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="66751-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="66751-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="66751-107">PowerShell 包括一组 cmdlet，这些 cmdlet 专门用于管理 PowerShell 提供程序公开的数据存储中的项。</span><span class="sxs-lookup"><span data-stu-id="66751-107">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="66751-108">您可以通过相同的方式使用这些 cmdlet 来管理提供商提供的所有不同类型的数据。</span><span class="sxs-lookup"><span data-stu-id="66751-108">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="66751-109">有关提供程序的详细信息，请键入 "get-help about_providers"。</span><span class="sxs-lookup"><span data-stu-id="66751-109">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="66751-110">例如，你可以使用 Get-ChildItem cmdlet 来列出文件系统目录中的文件、注册表项下的注册表项或你编写或下载的提供程序公开的项。</span><span class="sxs-lookup"><span data-stu-id="66751-110">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="66751-111">下面是专为与提供程序一起使用的 PowerShell cmdlet 列表：</span><span class="sxs-lookup"><span data-stu-id="66751-111">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="66751-112">Get-childitem cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-112">ChildItem cmdlets</span></span>

- <span data-ttu-id="66751-113">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="66751-113">Get-ChildItem</span></span>

<span data-ttu-id="66751-114">内容 cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-114">Content cmdlets</span></span>

- <span data-ttu-id="66751-115">Add-Content</span><span class="sxs-lookup"><span data-stu-id="66751-115">Add-Content</span></span>
- <span data-ttu-id="66751-116">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="66751-116">Clear-Content</span></span>
- <span data-ttu-id="66751-117">Get-Content</span><span class="sxs-lookup"><span data-stu-id="66751-117">Get-Content</span></span>
- <span data-ttu-id="66751-118">Set-Content</span><span class="sxs-lookup"><span data-stu-id="66751-118">Set-Content</span></span>

<span data-ttu-id="66751-119">项 cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-119">Item cmdlets</span></span>

- <span data-ttu-id="66751-120">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="66751-120">Clear-Item</span></span>
- <span data-ttu-id="66751-121">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="66751-121">Copy-Item</span></span>
- <span data-ttu-id="66751-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="66751-122">Get-Item</span></span>
- <span data-ttu-id="66751-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="66751-123">Invoke-Item</span></span>
- <span data-ttu-id="66751-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="66751-124">Move-Item</span></span>
- <span data-ttu-id="66751-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="66751-125">New-Item</span></span>
- <span data-ttu-id="66751-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="66751-126">Remove-Item</span></span>
- <span data-ttu-id="66751-127">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="66751-127">Rename-Item</span></span>
- <span data-ttu-id="66751-128">Set-Item</span><span class="sxs-lookup"><span data-stu-id="66751-128">Set-Item</span></span>

<span data-ttu-id="66751-129">Set-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-129">ItemProperty cmdlets</span></span>

- <span data-ttu-id="66751-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-130">Clear-ItemProperty</span></span>
- <span data-ttu-id="66751-131">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-131">Copy-ItemProperty</span></span>
- <span data-ttu-id="66751-132">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-132">Get-ItemProperty</span></span>
- <span data-ttu-id="66751-133">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-133">Move-ItemProperty</span></span>
- <span data-ttu-id="66751-134">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-134">New-ItemProperty</span></span>
- <span data-ttu-id="66751-135">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-135">Remove-ItemProperty</span></span>
- <span data-ttu-id="66751-136">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-136">Rename-ItemProperty</span></span>
- <span data-ttu-id="66751-137">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="66751-137">Set-ItemProperty</span></span>

<span data-ttu-id="66751-138">位置 cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-138">Location cmdlets</span></span>

- <span data-ttu-id="66751-139">Get-Location</span><span class="sxs-lookup"><span data-stu-id="66751-139">Get-Location</span></span>
- <span data-ttu-id="66751-140">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="66751-140">Pop-Location</span></span>
- <span data-ttu-id="66751-141">Push-Location</span><span class="sxs-lookup"><span data-stu-id="66751-141">Push-Location</span></span>
- <span data-ttu-id="66751-142">Set-Location</span><span class="sxs-lookup"><span data-stu-id="66751-142">Set-Location</span></span>

<span data-ttu-id="66751-143">路径 cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-143">Path cmdlets</span></span>

- <span data-ttu-id="66751-144">Join-Path</span><span class="sxs-lookup"><span data-stu-id="66751-144">Join-Path</span></span>
- <span data-ttu-id="66751-145">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="66751-145">Convert-Path</span></span>
- <span data-ttu-id="66751-146">Split-Path</span><span class="sxs-lookup"><span data-stu-id="66751-146">Split-Path</span></span>
- <span data-ttu-id="66751-147">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="66751-147">Resolve-Path</span></span>
- <span data-ttu-id="66751-148">Test-Path</span><span class="sxs-lookup"><span data-stu-id="66751-148">Test-Path</span></span>

<span data-ttu-id="66751-149">New-psdrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-149">PSDrive cmdlets</span></span>

- <span data-ttu-id="66751-150">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="66751-150">Get-PSDrive</span></span>
- <span data-ttu-id="66751-151">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="66751-151">New-PSDrive</span></span>
- <span data-ttu-id="66751-152">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="66751-152">Remove-PSDrive</span></span>

<span data-ttu-id="66751-153">PSProvider cmdlet</span><span class="sxs-lookup"><span data-stu-id="66751-153">PSProvider cmdlets</span></span>

- <span data-ttu-id="66751-154">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="66751-154">Get-PSProvider</span></span>

<span data-ttu-id="66751-155">有关 cmdlet 的详细信息，请键入 `get-help <cmdlet-name>` 。</span><span class="sxs-lookup"><span data-stu-id="66751-155">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="66751-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66751-156">SEE ALSO</span></span>

[<span data-ttu-id="66751-157">about_Providers</span><span class="sxs-lookup"><span data-stu-id="66751-157">about_Providers</span></span>](about_Providers.md)

