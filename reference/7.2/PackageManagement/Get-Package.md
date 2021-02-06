---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c26365eb5b4833c4982fa54e742521cf72307e99
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597240"
---
# <span data-ttu-id="266ee-102">Get-Package</span><span class="sxs-lookup"><span data-stu-id="266ee-102">Get-Package</span></span>

## <span data-ttu-id="266ee-103">摘要</span><span class="sxs-lookup"><span data-stu-id="266ee-103">SYNOPSIS</span></span>
<span data-ttu-id="266ee-104">返回使用 **PackageManagement** 安装的所有软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="266ee-104">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="266ee-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="266ee-105">SYNTAX</span></span>

### <span data-ttu-id="266ee-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="266ee-106">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="266ee-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="266ee-107">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="266ee-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="266ee-108">DESCRIPTION</span></span>

<span data-ttu-id="266ee-109">`Get-Package`Cmdlet 将返回本地计算机上使用 **PackageManagement** 安装的所有软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="266ee-109">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="266ee-110">您可以 `Get-Package` 在远程计算机上运行它，方法是将它作为 `Invoke-Command` 或 `Enter-PSSession` 命令或脚本的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="266ee-110">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="266ee-111">示例</span><span class="sxs-lookup"><span data-stu-id="266ee-111">EXAMPLES</span></span>

### <span data-ttu-id="266ee-112">示例1：获取所有已安装的包</span><span class="sxs-lookup"><span data-stu-id="266ee-112">Example 1: Get all installed packages</span></span>

<span data-ttu-id="266ee-113">该 `Get-Package` cmdlet 将获取在本地计算机上安装的所有包。</span><span class="sxs-lookup"><span data-stu-id="266ee-113">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="266ee-114">示例2：获取远程计算机上安装的包</span><span class="sxs-lookup"><span data-stu-id="266ee-114">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="266ee-115">此命令获取由 **PackageManagement** 在远程计算机上安装的包的列表。</span><span class="sxs-lookup"><span data-stu-id="266ee-115">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="266ee-116">此命令会提示你提供指定用户的密码。</span><span class="sxs-lookup"><span data-stu-id="266ee-116">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="266ee-117">`Invoke-Command` 使用 **ComputerName** 参数指定远程计算机 **Server01**。</span><span class="sxs-lookup"><span data-stu-id="266ee-117">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="266ee-118">**Credential** 参数指定有权在计算机上运行命令的域和用户名。</span><span class="sxs-lookup"><span data-stu-id="266ee-118">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="266ee-119">**ScriptBlock** 参数 `Get-Package` 在远程计算机上运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="266ee-119">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="266ee-120">示例3：获取指定提供程序的包</span><span class="sxs-lookup"><span data-stu-id="266ee-120">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="266ee-121">此命令从特定提供程序获取在本地计算机上安装的软件包。</span><span class="sxs-lookup"><span data-stu-id="266ee-121">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="266ee-122">`Get-Package` 使用 **ProviderName** 参数指定特定提供程序 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="266ee-122">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="266ee-123">" **所有版本** " 参数显示安装的每个版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-123">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="266ee-124">示例4：获取特定包的确切版本</span><span class="sxs-lookup"><span data-stu-id="266ee-124">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="266ee-125">此命令将获取已安装包的特定版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-125">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="266ee-126">可以安装多个版本的包。</span><span class="sxs-lookup"><span data-stu-id="266ee-126">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="266ee-127">`Get-Package` 使用 **Name** 参数指定包名称 **PackageManagement**。</span><span class="sxs-lookup"><span data-stu-id="266ee-127">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="266ee-128">**ProviderName** 参数指定提供程序 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="266ee-128">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="266ee-129">**必需的版本** 参数指定已安装的版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-129">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="266ee-130">示例5：卸载包</span><span class="sxs-lookup"><span data-stu-id="266ee-130">Example 5: Uninstall a package</span></span>

<span data-ttu-id="266ee-131">此示例将获取包信息，然后卸载包。</span><span class="sxs-lookup"><span data-stu-id="266ee-131">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="266ee-132">`Get-Package` 使用 **Name** 参数指定包名称 **posh**。</span><span class="sxs-lookup"><span data-stu-id="266ee-132">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="266ee-133">**RequiredVersion** 参数是包的特定版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-133">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="266ee-134">对象通过管道向下发送到 `Uninstall-Package` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="266ee-134">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="266ee-135">`Uninstall-Package` 删除包。</span><span class="sxs-lookup"><span data-stu-id="266ee-135">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="266ee-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="266ee-136">PARAMETERS</span></span>

### <span data-ttu-id="266ee-137">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="266ee-137">-AllowClobber</span></span>

<span data-ttu-id="266ee-138">替代与现有命令冲突有关的警告消息。</span><span class="sxs-lookup"><span data-stu-id="266ee-138">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="266ee-139">覆盖与模块安装的命令同名的现有命令。</span><span class="sxs-lookup"><span data-stu-id="266ee-139">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-140">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="266ee-140">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="266ee-141">在结果中包括标记为预发行版本的包。</span><span class="sxs-lookup"><span data-stu-id="266ee-141">Includes packages marked as a prerelease in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="266ee-142">-AllVersions</span></span>

<span data-ttu-id="266ee-143">指示 `Get-Package` 返回包的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-143">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="266ee-144">默认情况下， `Get-Package` 仅返回最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-144">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="266ee-145">-Destination</span><span class="sxs-lookup"><span data-stu-id="266ee-145">-Destination</span></span>

<span data-ttu-id="266ee-146">指定包含提取的包文件的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="266ee-146">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="266ee-147">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="266ee-147">-ExcludeVersion</span></span>

<span data-ttu-id="266ee-148">切换到排除文件夹路径中的版本号。</span><span class="sxs-lookup"><span data-stu-id="266ee-148">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="266ee-149">-Force</span><span class="sxs-lookup"><span data-stu-id="266ee-149">-Force</span></span>

<span data-ttu-id="266ee-150">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="266ee-150">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="266ee-151">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="266ee-151">-ForceBootstrap</span></span>

<span data-ttu-id="266ee-152">指示 `Get-Package` 强制 **PackageManagement** 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="266ee-152">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="266ee-153">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="266ee-153">-InstallUpdate</span></span>

<span data-ttu-id="266ee-154">指示此 cmdlet 安装更新。</span><span class="sxs-lookup"><span data-stu-id="266ee-154">Indicates that this cmdlet installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="266ee-155">-MaximumVersion</span></span>

<span data-ttu-id="266ee-156">指定要查找的最大包版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-156">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="266ee-157">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="266ee-157">-MinimumVersion</span></span>

<span data-ttu-id="266ee-158">指定要查找的最小包版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-158">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="266ee-159">如果有更高版本，则返回该版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-159">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="266ee-160">-Name</span><span class="sxs-lookup"><span data-stu-id="266ee-160">-Name</span></span>

<span data-ttu-id="266ee-161">指定一个或多个包名称或包名称，其中包含通配符。</span><span class="sxs-lookup"><span data-stu-id="266ee-161">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="266ee-162">用逗号分隔多个包名称。</span><span class="sxs-lookup"><span data-stu-id="266ee-162">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="266ee-163">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="266ee-163">-NoPathUpdate</span></span>

<span data-ttu-id="266ee-164">**NoPathUpdate** 仅适用于 `Install-Script` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="266ee-164">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="266ee-165">**NoPathUpdate** 是由提供程序添加的动态参数，不受支持 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="266ee-165">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-166">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="266ee-166">-PackageManagementProvider</span></span>

<span data-ttu-id="266ee-167">指定包管理提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="266ee-167">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="266ee-168">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="266ee-168">-ProviderName</span></span>

<span data-ttu-id="266ee-169">指定一个或多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="266ee-169">Specifies one or more package provider names.</span></span> <span data-ttu-id="266ee-170">用逗号分隔多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="266ee-170">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="266ee-171">使用 `Get-PackageProvider` 获取可用包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="266ee-171">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="266ee-172">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="266ee-172">-RequiredVersion</span></span>

<span data-ttu-id="266ee-173">指定要查找的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-173">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="266ee-174">-Scope</span><span class="sxs-lookup"><span data-stu-id="266ee-174">-Scope</span></span>

<span data-ttu-id="266ee-175">指定包的搜索范围。</span><span class="sxs-lookup"><span data-stu-id="266ee-175">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-176">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="266ee-176">-SkipDependencies</span></span>

<span data-ttu-id="266ee-177">指定跳过查找任何包依赖关系的开关。</span><span class="sxs-lookup"><span data-stu-id="266ee-177">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="266ee-178">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="266ee-178">-SkipPublisherCheck</span></span>

<span data-ttu-id="266ee-179">允许你获取比你安装的版本更新的包版本。</span><span class="sxs-lookup"><span data-stu-id="266ee-179">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="266ee-180">例如，由受信任的发布者进行数字签名，但未对新版本进行数字签名的已安装包。</span><span class="sxs-lookup"><span data-stu-id="266ee-180">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-181">-Type</span><span class="sxs-lookup"><span data-stu-id="266ee-181">-Type</span></span>

<span data-ttu-id="266ee-182">指定是使用模块、脚本还是搜索包。</span><span class="sxs-lookup"><span data-stu-id="266ee-182">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="266ee-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="266ee-183">CommonParameters</span></span>

<span data-ttu-id="266ee-184">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="266ee-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="266ee-185">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="266ee-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="266ee-186">输入</span><span class="sxs-lookup"><span data-stu-id="266ee-186">INPUTS</span></span>

## <span data-ttu-id="266ee-187">输出</span><span class="sxs-lookup"><span data-stu-id="266ee-187">OUTPUTS</span></span>

### <span data-ttu-id="266ee-188">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="266ee-188">SoftwareIdentity[]</span></span>

## <span data-ttu-id="266ee-189">注释</span><span class="sxs-lookup"><span data-stu-id="266ee-189">NOTES</span></span>

<span data-ttu-id="266ee-190">在命令中包含包提供程序可以使动态参数可用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="266ee-190">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="266ee-191">动态参数特定于包提供程序。</span><span class="sxs-lookup"><span data-stu-id="266ee-191">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="266ee-192">`Get-Help`Cmdlet 列出 cmdlet 的参数集，并包括提供程序的参数集。</span><span class="sxs-lookup"><span data-stu-id="266ee-192">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="266ee-193">例如， `Get-Package` 具有 **PowerShellGet** 参数集，其中包括 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="266ee-193">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="266ee-194">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="266ee-194">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="266ee-195">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="266ee-195">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="266ee-196">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="266ee-196">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="266ee-197">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="266ee-197">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="266ee-198">相关链接</span><span class="sxs-lookup"><span data-stu-id="266ee-198">RELATED LINKS</span></span>

[<span data-ttu-id="266ee-199">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="266ee-199">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="266ee-200">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="266ee-200">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="266ee-201">Find-Package</span><span class="sxs-lookup"><span data-stu-id="266ee-201">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="266ee-202">Get-Help</span><span class="sxs-lookup"><span data-stu-id="266ee-202">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="266ee-203">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="266ee-203">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="266ee-204">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="266ee-204">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="266ee-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="266ee-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="266ee-206">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="266ee-206">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="266ee-207">Save-Package</span><span class="sxs-lookup"><span data-stu-id="266ee-207">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="266ee-208">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="266ee-208">Uninstall-Package</span></span>](Uninstall-Package.md)
