---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: ca12f7f2118a004a6f474ae8174b04f9dbb9444d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596632"
---
# <span data-ttu-id="e88c4-102">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="e88c4-102">Uninstall-Package</span></span>

## <span data-ttu-id="e88c4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e88c4-103">SYNOPSIS</span></span>
<span data-ttu-id="e88c4-104">卸载一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-104">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="e88c4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e88c4-105">SYNTAX</span></span>

### <span data-ttu-id="e88c4-106">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="e88c4-106">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e88c4-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="e88c4-107">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e88c4-108">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="e88c4-108">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="e88c4-109">NuGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="e88c4-109">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="e88c4-110">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="e88c4-110">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="e88c4-111">PowerShellGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="e88c4-111">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="e88c4-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e88c4-112">DESCRIPTION</span></span>

<span data-ttu-id="e88c4-113">`Uninstall-Package`Cmdlet 从本地计算机中卸载一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-113">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="e88c4-114">若要查找已安装的包，请使用 `Get-Package` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e88c4-114">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="e88c4-115">示例</span><span class="sxs-lookup"><span data-stu-id="e88c4-115">EXAMPLES</span></span>

### <span data-ttu-id="e88c4-116">示例1：卸载包</span><span class="sxs-lookup"><span data-stu-id="e88c4-116">Example 1: Uninstall a package</span></span>

<span data-ttu-id="e88c4-117">`Uninstall-Package`Cmdlet 将卸载包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-117">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="e88c4-118">**Name** 参数指定要卸载的包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-118">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="e88c4-119">如果安装了包的多个版本，则会卸载最新版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-119">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="e88c4-120">示例2：使用管道卸载包</span><span class="sxs-lookup"><span data-stu-id="e88c4-120">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="e88c4-121">`Get-Package` 查找特定包，并将 **softwareidentity.revisionnumber** 对象向下发送到 `Uninsall-Package` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e88c4-121">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="e88c4-122">`Get-Package`Cmdlet 使用 **Name** 和 **RequiredVersion** 参数来指定包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-122">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="e88c4-123">**Softwareidentity.revisionnumber** 对象沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="e88c4-123">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="e88c4-124">`Uninstall-Package`Cmdlet 接收对象作为 **InputObject** ，并删除包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-124">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="e88c4-125">作为替代方法，该 `Uninstall-Package` cmdlet 可以为 **InputObject** 参数指定值：</span><span class="sxs-lookup"><span data-stu-id="e88c4-125">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="e88c4-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e88c4-126">PARAMETERS</span></span>

### <span data-ttu-id="e88c4-127">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e88c4-127">-AllowClobber</span></span>

<span data-ttu-id="e88c4-128">替代与现有命令冲突有关的警告消息。</span><span class="sxs-lookup"><span data-stu-id="e88c4-128">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="e88c4-129">覆盖与要安装的命令同名的现有命令。</span><span class="sxs-lookup"><span data-stu-id="e88c4-129">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-130">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="e88c4-130">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="e88c4-131">允许卸载标记为预发布的包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-131">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-132">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e88c4-132">-AllVersions</span></span>

<span data-ttu-id="e88c4-133">指示此 cmdlet 将卸载包的所有版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-133">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="e88c4-134">-Destination</span><span class="sxs-lookup"><span data-stu-id="e88c4-134">-Destination</span></span>

<span data-ttu-id="e88c4-135">指定输入对象的路径的字符串。</span><span class="sxs-lookup"><span data-stu-id="e88c4-135">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-136">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="e88c4-136">-ExcludeVersion</span></span>

<span data-ttu-id="e88c4-137">切换到排除文件夹路径中的版本号。</span><span class="sxs-lookup"><span data-stu-id="e88c4-137">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-138">-Force</span><span class="sxs-lookup"><span data-stu-id="e88c4-138">-Force</span></span>

<span data-ttu-id="e88c4-139">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="e88c4-139">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e88c4-140">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e88c4-140">-ForceBootstrap</span></span>

<span data-ttu-id="e88c4-141">强制 **PackageManagement** 为指定的包自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="e88c4-141">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="e88c4-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e88c4-142">-InputObject</span></span>

<span data-ttu-id="e88c4-143">接受从 cmdlet 指定包的 **softwareidentity.revisionnumber** 对象的管道输入 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="e88c4-143">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="e88c4-144">**InputObject** 接受 **softwareidentity.revisionnumber** 对象作为 `Get-Package` 值或包含该对象的变量。</span><span class="sxs-lookup"><span data-stu-id="e88c4-144">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-145">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="e88c4-145">-InstallUpdate</span></span>

<span data-ttu-id="e88c4-146">指示 `Uninstall-Package` 卸载更新。</span><span class="sxs-lookup"><span data-stu-id="e88c4-146">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e88c4-147">-MaximumVersion</span></span>

<span data-ttu-id="e88c4-148">指定要卸载的允许的最大包版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-148">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="e88c4-149">如果未指定此参数， `Uninstall-Package` 将卸载包的最新版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-149">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="e88c4-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e88c4-150">-MinimumVersion</span></span>

<span data-ttu-id="e88c4-151">指定要卸载的允许的最小包版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-151">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="e88c4-152">如果不添加此参数，则会 `Uninstall-Package` 卸载包的最新版本，该版本满足 **MaximumVersion** 参数指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-152">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="e88c4-153">-Name</span><span class="sxs-lookup"><span data-stu-id="e88c4-153">-Name</span></span>

<span data-ttu-id="e88c4-154">指定一个或多个包名称。</span><span class="sxs-lookup"><span data-stu-id="e88c4-154">Specifies one or more package names.</span></span> <span data-ttu-id="e88c4-155">多个包名称必须用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="e88c4-155">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-156">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="e88c4-156">-NoPathUpdate</span></span>

<span data-ttu-id="e88c4-157">**NoPathUpdate** 仅适用于 `Install-Script` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e88c4-157">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="e88c4-158">**NoPathUpdate** 是由提供程序添加的动态参数，不受支持 `Uninstall-Package` 。</span><span class="sxs-lookup"><span data-stu-id="e88c4-158">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-159">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e88c4-159">-PackageManagementProvider</span></span>

<span data-ttu-id="e88c4-160">指定 **PackageManagement** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="e88c4-160">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-161">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="e88c4-161">-ProviderName</span></span>

<span data-ttu-id="e88c4-162">指定一个或多个包提供程序名称以搜索包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-162">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="e88c4-163">可运行 `Get-PackageProvider` cmdlet 来获取包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="e88c4-163">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="e88c4-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e88c4-164">-RequiredVersion</span></span>

<span data-ttu-id="e88c4-165">指定要卸载的程序包的确切允许版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-165">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="e88c4-166">如果不添加此参数，则会 `Uninstall-Package` 卸载包的最新版本，该版本满足 **MaximumVersion** 参数指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-166">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="e88c4-167">-Scope</span><span class="sxs-lookup"><span data-stu-id="e88c4-167">-Scope</span></span>

<span data-ttu-id="e88c4-168">指定要为其卸载包的作用域。</span><span class="sxs-lookup"><span data-stu-id="e88c4-168">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="e88c4-169">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="e88c4-169">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e88c4-170">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="e88c4-170">CurrentUser</span></span>
- <span data-ttu-id="e88c4-171">AllUsers</span><span class="sxs-lookup"><span data-stu-id="e88c4-171">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-172">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="e88c4-172">-SkipDependencies</span></span>

<span data-ttu-id="e88c4-173">跳过软件依赖项的卸载。</span><span class="sxs-lookup"><span data-stu-id="e88c4-173">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-174">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="e88c4-174">-SkipPublisherCheck</span></span>

<span data-ttu-id="e88c4-175">允许你获取比你安装的版本更新的包版本。</span><span class="sxs-lookup"><span data-stu-id="e88c4-175">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="e88c4-176">例如，由受信任的发布者进行数字签名，但未对新版本进行数字签名的已安装包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-176">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-177">-Type</span><span class="sxs-lookup"><span data-stu-id="e88c4-177">-Type</span></span>

<span data-ttu-id="e88c4-178">指定是否使用模块、脚本或两者搜索包。</span><span class="sxs-lookup"><span data-stu-id="e88c4-178">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="e88c4-179">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="e88c4-179">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e88c4-180">模块</span><span class="sxs-lookup"><span data-stu-id="e88c4-180">Module</span></span>
- <span data-ttu-id="e88c4-181">Script</span><span class="sxs-lookup"><span data-stu-id="e88c4-181">Script</span></span>
- <span data-ttu-id="e88c4-182">全部</span><span class="sxs-lookup"><span data-stu-id="e88c4-182">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e88c4-183">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e88c4-183">-Confirm</span></span>

<span data-ttu-id="e88c4-184">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="e88c4-184">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e88c4-185">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e88c4-185">-WhatIf</span></span>

<span data-ttu-id="e88c4-186">显示在 `Uninstall-Package` 运行 cmdlet 时会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="e88c4-186">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="e88c4-187">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="e88c4-187">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e88c4-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e88c4-188">CommonParameters</span></span>

<span data-ttu-id="e88c4-189">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e88c4-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e88c4-190">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e88c4-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e88c4-191">输入</span><span class="sxs-lookup"><span data-stu-id="e88c4-191">INPUTS</span></span>

### <span data-ttu-id="e88c4-192">`Uninstall-Package` 接受管道中的 **softwareidentity.revisionnumber** 对象作为输入。</span><span class="sxs-lookup"><span data-stu-id="e88c4-192">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="e88c4-193">输出</span><span class="sxs-lookup"><span data-stu-id="e88c4-193">OUTPUTS</span></span>

### <span data-ttu-id="e88c4-194">`Uninstall-Package` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="e88c4-194">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="e88c4-195">注释</span><span class="sxs-lookup"><span data-stu-id="e88c4-195">NOTES</span></span>

<span data-ttu-id="e88c4-196">在命令中包含包提供程序可以使动态参数可用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e88c4-196">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="e88c4-197">动态参数特定于包提供程序。</span><span class="sxs-lookup"><span data-stu-id="e88c4-197">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="e88c4-198">`Get-Help`Cmdlet 列出 cmdlet 的参数集，并包括提供程序的参数集。</span><span class="sxs-lookup"><span data-stu-id="e88c4-198">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="e88c4-199">例如， `Uninstall-Package` 具有 **PowerShellGet** 参数集，其中包括 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="e88c4-199">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="e88c4-200">相关链接</span><span class="sxs-lookup"><span data-stu-id="e88c4-200">RELATED LINKS</span></span>

[<span data-ttu-id="e88c4-201">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e88c4-201">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="e88c4-202">Find-Package</span><span class="sxs-lookup"><span data-stu-id="e88c4-202">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="e88c4-203">Get-Package</span><span class="sxs-lookup"><span data-stu-id="e88c4-203">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="e88c4-204">Install-Package</span><span class="sxs-lookup"><span data-stu-id="e88c4-204">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="e88c4-205">Save-Package</span><span class="sxs-lookup"><span data-stu-id="e88c4-205">Save-Package</span></span>](Save-Package.md)

