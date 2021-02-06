---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595397"
---
# <span data-ttu-id="98734-102">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="98734-102">Get-PackageProvider</span></span>

## <span data-ttu-id="98734-103">摘要</span><span class="sxs-lookup"><span data-stu-id="98734-103">SYNOPSIS</span></span>
<span data-ttu-id="98734-104">返回连接到包管理的包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="98734-104">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="98734-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98734-105">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="98734-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="98734-106">DESCRIPTION</span></span>

<span data-ttu-id="98734-107">**Install-packageprovider** cmdlet 将返回连接到包管理的包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="98734-107">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="98734-108">这些提供程序的示例包括 PSModule、NuGet 和 Chocolatey。</span><span class="sxs-lookup"><span data-stu-id="98734-108">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="98734-109">你可以根据一个或多个提供程序名称的全部或部分来筛选结果。</span><span class="sxs-lookup"><span data-stu-id="98734-109">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="98734-110">示例</span><span class="sxs-lookup"><span data-stu-id="98734-110">EXAMPLES</span></span>

### <span data-ttu-id="98734-111">示例1：获取所有当前加载的包提供程序</span><span class="sxs-lookup"><span data-stu-id="98734-111">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="98734-112">此命令将获取当前在本地计算机上加载的所有包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="98734-112">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="98734-113">示例2：获取所有可用的包提供程序</span><span class="sxs-lookup"><span data-stu-id="98734-113">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="98734-114">此命令将获取本地计算机上可用的所有包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="98734-114">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="98734-115">示例3：动态获取包提供程序</span><span class="sxs-lookup"><span data-stu-id="98734-115">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="98734-116">如果你的计算机未安装 Chocolatey 提供程序，则此命令将自动安装 Chocolatey 提供程序。</span><span class="sxs-lookup"><span data-stu-id="98734-116">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="98734-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98734-117">PARAMETERS</span></span>

### <span data-ttu-id="98734-118">-Force</span><span class="sxs-lookup"><span data-stu-id="98734-118">-Force</span></span>

<span data-ttu-id="98734-119">指示此 cmdlet 强制执行可强制执行的所有其他操作。</span><span class="sxs-lookup"><span data-stu-id="98734-119">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="98734-120">在 **install-packageprovider** 中，这意味着 *Force* 参数的作用与 *ForceBootstrap* 参数相同。</span><span class="sxs-lookup"><span data-stu-id="98734-120">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98734-121">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="98734-121">-ForceBootstrap</span></span>

<span data-ttu-id="98734-122">指示此 cmdlet 强制包管理自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="98734-122">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98734-123">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="98734-123">-ListAvailable</span></span>

<span data-ttu-id="98734-124">获取所有已安装的提供程序。</span><span class="sxs-lookup"><span data-stu-id="98734-124">Gets all installed providers.</span></span>
<span data-ttu-id="98734-125">**Install-packageprovider** 获取 **PSModulePath** 环境变量中列出的路径中的提供程序，以及包提供程序程序集文件夹：</span><span class="sxs-lookup"><span data-stu-id="98734-125">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="98734-126">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env： LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="98734-126">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="98734-127">如果没有此参数， **install-packageprovider** 仅获取当前会话中加载的提供程序。</span><span class="sxs-lookup"><span data-stu-id="98734-127">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98734-128">-Name</span><span class="sxs-lookup"><span data-stu-id="98734-128">-Name</span></span>

<span data-ttu-id="98734-129">指定一个或多个提供程序名称或部分提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="98734-129">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="98734-130">用逗号分隔多个提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="98734-130">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="98734-131">此参数的有效值包括已与包一起安装的提供程序的名称;PackageManagement 附带一组默认提供程序，其中包括 **PSModule** 和 **MSI** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="98734-131">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98734-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98734-132">CommonParameters</span></span>

<span data-ttu-id="98734-133">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="98734-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98734-134">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="98734-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98734-135">输入</span><span class="sxs-lookup"><span data-stu-id="98734-135">INPUTS</span></span>

## <span data-ttu-id="98734-136">输出</span><span class="sxs-lookup"><span data-stu-id="98734-136">OUTPUTS</span></span>

### <span data-ttu-id="98734-137">Install-packageprovider []</span><span class="sxs-lookup"><span data-stu-id="98734-137">PackageProvider[]</span></span>

## <span data-ttu-id="98734-138">注释</span><span class="sxs-lookup"><span data-stu-id="98734-138">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98734-139">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="98734-139">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="98734-140">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="98734-140">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="98734-141">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="98734-141">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="98734-142">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="98734-142">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="98734-143">相关链接</span><span class="sxs-lookup"><span data-stu-id="98734-143">RELATED LINKS</span></span>

[<span data-ttu-id="98734-144">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="98734-144">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="98734-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98734-145">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="98734-146">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98734-146">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="98734-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98734-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
