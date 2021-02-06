---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597860"
---
# <span data-ttu-id="3198b-102">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3198b-102">Import-PackageProvider</span></span>

## <span data-ttu-id="3198b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3198b-103">SYNOPSIS</span></span>
<span data-ttu-id="3198b-104">将包管理包提供程序添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="3198b-104">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="3198b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3198b-105">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="3198b-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3198b-106">DESCRIPTION</span></span>

<span data-ttu-id="3198b-107">`Import-PackageProvider`Cmdlet 可将一个或多个包提供程序添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="3198b-107">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="3198b-108">必须在本地计算机上安装导入的提供程序。</span><span class="sxs-lookup"><span data-stu-id="3198b-108">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="3198b-109">若要获取可用提供程序的列表，请运行 `Get-PackageProvider -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="3198b-109">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="3198b-110">请注意，包提供程序名称可以与其模块名称不同。</span><span class="sxs-lookup"><span data-stu-id="3198b-110">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="3198b-111">出于安全原因， **PackageManagement** 要求基于 c # 的提供程序包含 `provider.manifest` 。</span><span class="sxs-lookup"><span data-stu-id="3198b-111">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="3198b-112">有关如何使用注入的生成提供程序的详细信息 `provider.manifest` ，请参阅 `.csproj` 上的项目文件 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) 。</span><span class="sxs-lookup"><span data-stu-id="3198b-112">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="3198b-113">示例</span><span class="sxs-lookup"><span data-stu-id="3198b-113">EXAMPLES</span></span>

### <span data-ttu-id="3198b-114">示例1：从本地计算机导入包提供程序</span><span class="sxs-lookup"><span data-stu-id="3198b-114">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="3198b-115">此命令在 Nuget 提供程序安装在本地计算机上后导入它。</span><span class="sxs-lookup"><span data-stu-id="3198b-115">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="3198b-116">示例2：导入特定版本的包提供程序</span><span class="sxs-lookup"><span data-stu-id="3198b-116">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="3198b-117">此命令查找、安装和导入特定版本的 Nuget 包提供程序。</span><span class="sxs-lookup"><span data-stu-id="3198b-117">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="3198b-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3198b-118">PARAMETERS</span></span>

### <span data-ttu-id="3198b-119">-Force</span><span class="sxs-lookup"><span data-stu-id="3198b-119">-Force</span></span>

<span data-ttu-id="3198b-120">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="3198b-120">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="3198b-121">重新导入包提供程序。</span><span class="sxs-lookup"><span data-stu-id="3198b-121">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="3198b-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3198b-122">-ForceBootstrap</span></span>

<span data-ttu-id="3198b-123">指示此 cmdlet 强制包管理自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="3198b-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="3198b-124">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3198b-124">-MaximumVersion</span></span>

<span data-ttu-id="3198b-125">指定要导入的包提供程序的最大允许版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-125">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="3198b-126">如果未添加此参数，则将 `Import-PackageProvider` 导入提供程序的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-126">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3198b-127">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3198b-127">-MinimumVersion</span></span>

<span data-ttu-id="3198b-128">指定要导入的包提供程序的最小允许版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-128">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="3198b-129">如果未添加此参数，则将 `Import-PackageProvider` 导入同时满足使用 *MaximumVersion* 参数指定的任何最高版本的包的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-129">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3198b-130">-Name</span><span class="sxs-lookup"><span data-stu-id="3198b-130">-Name</span></span>

<span data-ttu-id="3198b-131">指定一个或多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="3198b-131">Specifies one or more package provider names.</span></span> <span data-ttu-id="3198b-132">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3198b-132">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3198b-133">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3198b-133">-RequiredVersion</span></span>

<span data-ttu-id="3198b-134">指定要导入的包提供程序的确切版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-134">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="3198b-135">如果未添加此参数，则将 `Import-PackageProvider` 导入最高可用版本的提供程序，该版本还满足使用 **MaximumVersion** 参数指定的任何最高版本。</span><span class="sxs-lookup"><span data-stu-id="3198b-135">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3198b-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3198b-136">CommonParameters</span></span>

<span data-ttu-id="3198b-137">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3198b-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3198b-138">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3198b-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3198b-139">输入</span><span class="sxs-lookup"><span data-stu-id="3198b-139">INPUTS</span></span>

### <span data-ttu-id="3198b-140">Install-packageprovider。</span><span class="sxs-lookup"><span data-stu-id="3198b-140">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="3198b-141">可以通过管道将返回的 **install-packageprovider** 对象传递 `Get-PackageProvider` 给 `Import-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="3198b-141">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="3198b-142">输出</span><span class="sxs-lookup"><span data-stu-id="3198b-142">OUTPUTS</span></span>

## <span data-ttu-id="3198b-143">注释</span><span class="sxs-lookup"><span data-stu-id="3198b-143">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3198b-144">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="3198b-144">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="3198b-145">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="3198b-145">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="3198b-146">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="3198b-146">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="3198b-147">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="3198b-147">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="3198b-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="3198b-148">RELATED LINKS</span></span>

[<span data-ttu-id="3198b-149">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3198b-149">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3198b-150">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3198b-150">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="3198b-151">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3198b-151">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3198b-152">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3198b-152">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="3198b-153">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3198b-153">Get-PackageProvider</span></span>](Get-PackageProvider.md)
