---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 93ec8264bad588e38554daddcdf5dc9befce053e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599068"
---
# <span data-ttu-id="d8434-102">Save-Package</span><span class="sxs-lookup"><span data-stu-id="d8434-102">Save-Package</span></span>

## <span data-ttu-id="d8434-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d8434-103">SYNOPSIS</span></span>
<span data-ttu-id="d8434-104">将包保存到本地计算机，但不安装它们。</span><span class="sxs-lookup"><span data-stu-id="d8434-104">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="d8434-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8434-105">SYNTAX</span></span>

### <span data-ttu-id="d8434-106">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="d8434-106">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d8434-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="d8434-107">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d8434-108">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="d8434-108">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="d8434-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="d8434-109">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="d8434-110">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="d8434-110">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="d8434-111">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d8434-111">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="d8434-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8434-112">DESCRIPTION</span></span>

<span data-ttu-id="d8434-113">`Save-Package`Cmdlet 可将包保存到本地计算机，但不会安装包。</span><span class="sxs-lookup"><span data-stu-id="d8434-113">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="d8434-114">此 cmdlet 将保存包的最新版本，除非指定了 **RequiredVerion**。</span><span class="sxs-lookup"><span data-stu-id="d8434-114">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="d8434-115">**路径** 和 **LiteralPath** 参数是互斥的，不能添加到同一个命令中。</span><span class="sxs-lookup"><span data-stu-id="d8434-115">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="d8434-116">示例</span><span class="sxs-lookup"><span data-stu-id="d8434-116">EXAMPLES</span></span>

### <span data-ttu-id="d8434-117">示例1：将包保存到本地计算机</span><span class="sxs-lookup"><span data-stu-id="d8434-117">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="d8434-118">此示例将包的最新版本保存到本地计算机上的目录中。</span><span class="sxs-lookup"><span data-stu-id="d8434-118">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="d8434-119">包的依赖项与包一起下载。</span><span class="sxs-lookup"><span data-stu-id="d8434-119">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d8434-120">`Save-Package` 使用 **Name** 参数指定包。</span><span class="sxs-lookup"><span data-stu-id="d8434-120">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="d8434-121">包从 **ProviderName** 参数指定的存储库下载。</span><span class="sxs-lookup"><span data-stu-id="d8434-121">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="d8434-122">**Path** 参数确定包的保存位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-122">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="d8434-123">示例2：保存特定包版本</span><span class="sxs-lookup"><span data-stu-id="d8434-123">Example 2: Save a specific package version</span></span>

<span data-ttu-id="d8434-124">此示例指定包版本，并将其保存到本地计算机上的目录中。</span><span class="sxs-lookup"><span data-stu-id="d8434-124">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d8434-125">`Save-Package` 使用 **Name** 参数指定包。</span><span class="sxs-lookup"><span data-stu-id="d8434-125">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="d8434-126">**RequiredVersion** 指示特定的包版本。</span><span class="sxs-lookup"><span data-stu-id="d8434-126">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="d8434-127">包从 **ProviderName** 参数指定的存储库下载。</span><span class="sxs-lookup"><span data-stu-id="d8434-127">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="d8434-128">**Path** 参数确定包的保存位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-128">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="d8434-129">示例3：使用 Find-Package 保存包</span><span class="sxs-lookup"><span data-stu-id="d8434-129">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="d8434-130">此命令使用 `Find-Package` 定位包的最新版本，并将对象发送到 `Save-Package` 。</span><span class="sxs-lookup"><span data-stu-id="d8434-130">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="d8434-131">`Find-Package` 使用 **Name** 参数指定包。</span><span class="sxs-lookup"><span data-stu-id="d8434-131">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="d8434-132">包从 **ProviderName** 参数指定的存储库下载。</span><span class="sxs-lookup"><span data-stu-id="d8434-132">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="d8434-133">将对象向下发送到 `Save-Package` 。</span><span class="sxs-lookup"><span data-stu-id="d8434-133">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="d8434-134">**Path** 参数确定包的保存位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-134">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="d8434-135">示例4：保存并安装包</span><span class="sxs-lookup"><span data-stu-id="d8434-135">Example 4: Save and install the package</span></span>

<span data-ttu-id="d8434-136">包及其依赖项的最新版本会在本地计算机上下载并安装。</span><span class="sxs-lookup"><span data-stu-id="d8434-136">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="d8434-137">`Save-Package` 将包文件及其依赖项下载到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="d8434-137">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="d8434-138">`Install-Package` 从指定目录安装包和依赖项。</span><span class="sxs-lookup"><span data-stu-id="d8434-138">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="d8434-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8434-139">PARAMETERS</span></span>

### <span data-ttu-id="d8434-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="d8434-140">-AcceptLicense</span></span>

<span data-ttu-id="d8434-141">如果包需要许可协议，则在安装过程中自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="d8434-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-142">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="d8434-142">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="d8434-143">允许保存标记为预发布的包。</span><span class="sxs-lookup"><span data-stu-id="d8434-143">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-144">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d8434-144">-AllVersions</span></span>

<span data-ttu-id="d8434-145">指示此 cmdlet 保存包的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="d8434-145">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="d8434-146">-Command</span><span class="sxs-lookup"><span data-stu-id="d8434-146">-Command</span></span>

<span data-ttu-id="d8434-147">指定包含在包中的一个或多个命令。</span><span class="sxs-lookup"><span data-stu-id="d8434-147">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-148">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="d8434-148">-ConfigFile</span></span>

<span data-ttu-id="d8434-149">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="d8434-149">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-150">-Contains</span><span class="sxs-lookup"><span data-stu-id="d8434-150">-Contains</span></span>

<span data-ttu-id="d8434-151">`Save-Package` 如果对象的属性值中的任何项与指定值完全匹配，则获取对象。</span><span class="sxs-lookup"><span data-stu-id="d8434-151">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="d8434-152">-Credential</span></span>

<span data-ttu-id="d8434-153">指定有权从指定的包提供程序或源保存包的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d8434-153">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-154">-DscResource</span><span class="sxs-lookup"><span data-stu-id="d8434-154">-DscResource</span></span>

<span data-ttu-id="d8434-155">为包 (DSC) 资源指定一个或多个所需状态配置。</span><span class="sxs-lookup"><span data-stu-id="d8434-155">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-156">-Filter</span><span class="sxs-lookup"><span data-stu-id="d8434-156">-Filter</span></span>

<span data-ttu-id="d8434-157">指定包的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d8434-157">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-158">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="d8434-158">-FilterOnTag</span></span>

<span data-ttu-id="d8434-159">指定筛选结果的标记。</span><span class="sxs-lookup"><span data-stu-id="d8434-159">Specifies the tag that filters the results.</span></span> <span data-ttu-id="d8434-160">排除不包含指定标记的结果。</span><span class="sxs-lookup"><span data-stu-id="d8434-160">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-161">-Force</span><span class="sxs-lookup"><span data-stu-id="d8434-161">-Force</span></span>

<span data-ttu-id="d8434-162">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="d8434-162">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d8434-163">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d8434-163">-ForceBootstrap</span></span>

<span data-ttu-id="d8434-164">指示 `Save-Package` 强制 **PackageManagement** 为指定的包自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="d8434-164">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="d8434-165">-标头</span><span class="sxs-lookup"><span data-stu-id="d8434-165">-Headers</span></span>

<span data-ttu-id="d8434-166">指定包的标头。</span><span class="sxs-lookup"><span data-stu-id="d8434-166">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-167">-Includes</span><span class="sxs-lookup"><span data-stu-id="d8434-167">-Includes</span></span>

<span data-ttu-id="d8434-168">指示包包含的资源。</span><span class="sxs-lookup"><span data-stu-id="d8434-168">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8434-169">-InputObject</span></span>

<span data-ttu-id="d8434-170">表示要保存的包的软件 ID 对象。</span><span class="sxs-lookup"><span data-stu-id="d8434-170">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="d8434-171">软件 Id 是 cmdlet 结果的一部分 `Find-Package` 。</span><span class="sxs-lookup"><span data-stu-id="d8434-171">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d8434-172">-LiteralPath</span></span>

<span data-ttu-id="d8434-173">指定要将包保存到的文本路径。</span><span class="sxs-lookup"><span data-stu-id="d8434-173">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="d8434-174">不能将此参数和 **Path** 参数添加到同一个命令中。</span><span class="sxs-lookup"><span data-stu-id="d8434-174">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="d8434-175">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d8434-175">-MaximumVersion</span></span>

<span data-ttu-id="d8434-176">指定要保存的包的最大版本。</span><span class="sxs-lookup"><span data-stu-id="d8434-176">Specifies the maximum version of the package that you want to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-177">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d8434-177">-MinimumVersion</span></span>

<span data-ttu-id="d8434-178">指定要查找的包的最低版本。</span><span class="sxs-lookup"><span data-stu-id="d8434-178">Specifies the minimum version of the package that you want to find.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-179">-Name</span><span class="sxs-lookup"><span data-stu-id="d8434-179">-Name</span></span>

<span data-ttu-id="d8434-180">指定一个或多个包名称。</span><span class="sxs-lookup"><span data-stu-id="d8434-180">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-181">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d8434-181">-PackageManagementProvider</span></span>

<span data-ttu-id="d8434-182">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="d8434-182">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-183">-Path</span><span class="sxs-lookup"><span data-stu-id="d8434-183">-Path</span></span>

<span data-ttu-id="d8434-184">指定本地计算机上用于存储包的位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-184">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="d8434-185">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d8434-185">-ProviderName</span></span>

<span data-ttu-id="d8434-186">指定一个或多个提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="d8434-186">Specifies one or more provider names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-187">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d8434-187">-Proxy</span></span>

<span data-ttu-id="d8434-188">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="d8434-188">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d8434-189">-ProxyCredential</span></span>

<span data-ttu-id="d8434-190">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d8434-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-191">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d8434-191">-PublishLocation</span></span>

<span data-ttu-id="d8434-192">指定发布位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-192">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d8434-193">-RequiredVersion</span></span>

<span data-ttu-id="d8434-194">指定要保存的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="d8434-194">Specifies the exact version of the package to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-195">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="d8434-195">-RoleCapability</span></span>

<span data-ttu-id="d8434-196">指定角色功能的数组。</span><span class="sxs-lookup"><span data-stu-id="d8434-196">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-197">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d8434-197">-ScriptPublishLocation</span></span>

<span data-ttu-id="d8434-198">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-198">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-199">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d8434-199">-ScriptSourceLocation</span></span>

<span data-ttu-id="d8434-200">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="d8434-200">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-201">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d8434-201">-SkipValidate</span></span>

<span data-ttu-id="d8434-202">跳过验证包凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="d8434-202">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-203">-Source</span><span class="sxs-lookup"><span data-stu-id="d8434-203">-Source</span></span>

<span data-ttu-id="d8434-204">指定一个或多个包源。</span><span class="sxs-lookup"><span data-stu-id="d8434-204">Specifies one or more package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-205">-Tag</span><span class="sxs-lookup"><span data-stu-id="d8434-205">-Tag</span></span>

<span data-ttu-id="d8434-206">指定要在包元数据中搜索的标记。</span><span class="sxs-lookup"><span data-stu-id="d8434-206">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-207">-Type</span><span class="sxs-lookup"><span data-stu-id="d8434-207">-Type</span></span>

<span data-ttu-id="d8434-208">指定是使用模块、脚本还是搜索包。</span><span class="sxs-lookup"><span data-stu-id="d8434-208">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8434-209">-Confirm</span></span>

<span data-ttu-id="d8434-210">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="d8434-210">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8434-211">-WhatIf</span></span>

<span data-ttu-id="d8434-212">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="d8434-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d8434-213">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="d8434-213">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8434-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8434-214">CommonParameters</span></span>

<span data-ttu-id="d8434-215">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8434-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8434-216">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8434-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8434-217">输入</span><span class="sxs-lookup"><span data-stu-id="d8434-217">INPUTS</span></span>

### <span data-ttu-id="d8434-218">`Save-Package` 接受管道中的对象。</span><span class="sxs-lookup"><span data-stu-id="d8434-218">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="d8434-219">输出</span><span class="sxs-lookup"><span data-stu-id="d8434-219">OUTPUTS</span></span>

### <span data-ttu-id="d8434-220">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="d8434-220">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d8434-221">注释</span><span class="sxs-lookup"><span data-stu-id="d8434-221">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8434-222">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="d8434-222">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d8434-223">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="d8434-223">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d8434-224">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="d8434-224">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d8434-225">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="d8434-225">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d8434-226">相关链接</span><span class="sxs-lookup"><span data-stu-id="d8434-226">RELATED LINKS</span></span>

[<span data-ttu-id="d8434-227">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d8434-227">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d8434-228">Get-Package</span><span class="sxs-lookup"><span data-stu-id="d8434-228">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="d8434-229">Install-Package</span><span class="sxs-lookup"><span data-stu-id="d8434-229">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="d8434-230">Save-Package</span><span class="sxs-lookup"><span data-stu-id="d8434-230">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="d8434-231">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="d8434-231">Uninstall-Package</span></span>](Uninstall-Package.md)
