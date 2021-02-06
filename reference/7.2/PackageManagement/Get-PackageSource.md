---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8b91c5b950e0e16c4ce0821ee2f96b830dab1fc2
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595613"
---
# <span data-ttu-id="367f9-102">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="367f9-102">Get-PackageSource</span></span>

## <span data-ttu-id="367f9-103">摘要</span><span class="sxs-lookup"><span data-stu-id="367f9-103">SYNOPSIS</span></span>
<span data-ttu-id="367f9-104">获取为包提供程序注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="367f9-104">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="367f9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="367f9-105">SYNTAX</span></span>

### <span data-ttu-id="367f9-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="367f9-106">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="367f9-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="367f9-107">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="367f9-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="367f9-108">DESCRIPTION</span></span>

<span data-ttu-id="367f9-109">该 `Get-PackageSource` cmdlet 将获取在本地计算机上向 **PackageManagement** 注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="367f9-109">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="367f9-110">如果指定包提供程序，则 `Get-PackageSource` 仅获取与指定的提供程序关联的那些源。</span><span class="sxs-lookup"><span data-stu-id="367f9-110">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="367f9-111">否则，该命令将返回已注册到 **PackageManagement** 的所有包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-111">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="367f9-112">示例</span><span class="sxs-lookup"><span data-stu-id="367f9-112">EXAMPLES</span></span>

### <span data-ttu-id="367f9-113">示例1：获取所有包源</span><span class="sxs-lookup"><span data-stu-id="367f9-113">Example 1: Get all package sources</span></span>

<span data-ttu-id="367f9-114">该 `Get-PackageSource` cmdlet 将获取在本地计算机上注册到 **PackageManagement** 的所有包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-114">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="367f9-115">示例2：获取特定提供程序的所有包源</span><span class="sxs-lookup"><span data-stu-id="367f9-115">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="367f9-116">此命令将获取为特定提供程序注册的包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-116">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="367f9-117">`Get-PackageSource` 使用 **ProviderName** 参数获取为 **NuGet** 提供程序注册的包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-117">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="367f9-118">示例3：从包提供程序获取源</span><span class="sxs-lookup"><span data-stu-id="367f9-118">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="367f9-119">此命令使用包提供程序获取包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-119">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="367f9-120">`Get-PackageProvider` 使用 **Name** 参数指定提供程序名称（ **NuGet**）。</span><span class="sxs-lookup"><span data-stu-id="367f9-120">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="367f9-121">将对象向下发送到 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="367f9-121">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="367f9-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="367f9-122">PARAMETERS</span></span>

### <span data-ttu-id="367f9-123">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="367f9-123">-ConfigFile</span></span>

<span data-ttu-id="367f9-124">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="367f9-124">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-125">-Force</span><span class="sxs-lookup"><span data-stu-id="367f9-125">-Force</span></span>

<span data-ttu-id="367f9-126">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="367f9-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="367f9-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="367f9-127">-ForceBootstrap</span></span>

<span data-ttu-id="367f9-128">指示此 cmdlet 强制 **PackageManagement** 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="367f9-128">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="367f9-129">-Location</span><span class="sxs-lookup"><span data-stu-id="367f9-129">-Location</span></span>

<span data-ttu-id="367f9-130">指定包管理源或存储库的位置。</span><span class="sxs-lookup"><span data-stu-id="367f9-130">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="367f9-131">-Name</span><span class="sxs-lookup"><span data-stu-id="367f9-131">-Name</span></span>

<span data-ttu-id="367f9-132">指定包管理源的名称。</span><span class="sxs-lookup"><span data-stu-id="367f9-132">Specifies the name of a package management source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="367f9-133">-PackageManagementProvider</span></span>

<span data-ttu-id="367f9-134">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="367f9-134">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="367f9-135">-ProviderName</span></span>

<span data-ttu-id="367f9-136">指定一个或多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="367f9-136">Specifies one or more package provider names.</span></span> <span data-ttu-id="367f9-137">用逗号分隔多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="367f9-137">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="367f9-138">使用 `Get-PackageProvider` 获取可用包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="367f9-138">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-139">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="367f9-139">-PublishLocation</span></span>

<span data-ttu-id="367f9-140">指定包源的发布位置。</span><span class="sxs-lookup"><span data-stu-id="367f9-140">Specifies the publish location for the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-141">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="367f9-141">-ScriptPublishLocation</span></span>

<span data-ttu-id="367f9-142">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="367f9-142">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-143">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="367f9-143">-ScriptSourceLocation</span></span>

<span data-ttu-id="367f9-144">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="367f9-144">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-145">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="367f9-145">-SkipValidate</span></span>

<span data-ttu-id="367f9-146">跳过验证包源凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="367f9-146">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="367f9-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="367f9-147">CommonParameters</span></span>

<span data-ttu-id="367f9-148">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="367f9-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="367f9-149">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="367f9-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="367f9-150">输入</span><span class="sxs-lookup"><span data-stu-id="367f9-150">INPUTS</span></span>

## <span data-ttu-id="367f9-151">输出</span><span class="sxs-lookup"><span data-stu-id="367f9-151">OUTPUTS</span></span>

### <span data-ttu-id="367f9-152">Register-packagesource []</span><span class="sxs-lookup"><span data-stu-id="367f9-152">PackageSource[]</span></span>

<span data-ttu-id="367f9-153">指定一个或多个包源。</span><span class="sxs-lookup"><span data-stu-id="367f9-153">Specifies one or more package sources.</span></span>

## <span data-ttu-id="367f9-154">注释</span><span class="sxs-lookup"><span data-stu-id="367f9-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="367f9-155">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="367f9-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="367f9-156">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="367f9-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="367f9-157">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="367f9-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="367f9-158">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="367f9-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="367f9-159">相关链接</span><span class="sxs-lookup"><span data-stu-id="367f9-159">RELATED LINKS</span></span>

[<span data-ttu-id="367f9-160">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="367f9-160">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="367f9-161">Find-Package</span><span class="sxs-lookup"><span data-stu-id="367f9-161">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="367f9-162">Get-Package</span><span class="sxs-lookup"><span data-stu-id="367f9-162">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="367f9-163">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="367f9-163">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="367f9-164">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="367f9-164">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="367f9-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="367f9-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="367f9-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="367f9-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
