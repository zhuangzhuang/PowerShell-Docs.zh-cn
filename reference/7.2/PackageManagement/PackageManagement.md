---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598461"
---
# <span data-ttu-id="8abd6-102">PackageManagement 模块</span><span class="sxs-lookup"><span data-stu-id="8abd6-102">PackageManagement Module</span></span>

## <span data-ttu-id="8abd6-103">说明</span><span class="sxs-lookup"><span data-stu-id="8abd6-103">Description</span></span>

<span data-ttu-id="8abd6-104">本主题显示包管理 Cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="8abd6-104">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8abd6-105">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="8abd6-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8abd6-106">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="8abd6-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8abd6-107">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="8abd6-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8abd6-108">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="8abd6-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8abd6-109">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8abd6-109">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="8abd6-110">Find-Package</span><span class="sxs-lookup"><span data-stu-id="8abd6-110">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="8abd6-111">在可用包源中查找软件包。</span><span class="sxs-lookup"><span data-stu-id="8abd6-111">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="8abd6-112">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="8abd6-112">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="8abd6-113">返回可供安装的包管理包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="8abd6-113">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="8abd6-114">Get-Package</span><span class="sxs-lookup"><span data-stu-id="8abd6-114">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="8abd6-115">返回使用 **PackageManagement** 安装的所有软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="8abd6-115">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="8abd6-116">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="8abd6-116">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="8abd6-117">返回连接到包管理的包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="8abd6-117">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="8abd6-118">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="8abd6-118">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="8abd6-119">获取为包提供程序注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="8abd6-119">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="8abd6-120">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="8abd6-120">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="8abd6-121">将包管理包提供程序添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="8abd6-121">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="8abd6-122">Install-Package</span><span class="sxs-lookup"><span data-stu-id="8abd6-122">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="8abd6-123">安装一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="8abd6-123">Installs one or more software packages.</span></span>

### [<span data-ttu-id="8abd6-124">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="8abd6-124">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="8abd6-125">安装一个或多个包管理包提供程序。</span><span class="sxs-lookup"><span data-stu-id="8abd6-125">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="8abd6-126">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="8abd6-126">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="8abd6-127">为指定的包提供程序添加包源。</span><span class="sxs-lookup"><span data-stu-id="8abd6-127">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="8abd6-128">Save-Package</span><span class="sxs-lookup"><span data-stu-id="8abd6-128">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="8abd6-129">将包保存到本地计算机，但不安装它们。</span><span class="sxs-lookup"><span data-stu-id="8abd6-129">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="8abd6-130">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="8abd6-130">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="8abd6-131">替换指定包提供程序的包源。</span><span class="sxs-lookup"><span data-stu-id="8abd6-131">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="8abd6-132">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="8abd6-132">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="8abd6-133">卸载一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="8abd6-133">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="8abd6-134">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="8abd6-134">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="8abd6-135">删除已注册的包源。</span><span class="sxs-lookup"><span data-stu-id="8abd6-135">Removes a registered package source.</span></span>
