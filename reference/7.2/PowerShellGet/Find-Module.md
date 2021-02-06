---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: f9cba90ffa69d04df196f4062c8f190d545b9bc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595396"
---
# <span data-ttu-id="628f7-102">Find-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-102">Find-Module</span></span>

## <span data-ttu-id="628f7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="628f7-103">SYNOPSIS</span></span>
<span data-ttu-id="628f7-104">查找存储库中与指定条件匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-104">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="628f7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="628f7-105">SYNTAX</span></span>

### <span data-ttu-id="628f7-106">全部</span><span class="sxs-lookup"><span data-stu-id="628f7-106">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="628f7-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="628f7-107">DESCRIPTION</span></span>

<span data-ttu-id="628f7-108">`Find-Module`Cmdlet 可在存储库中查找与指定条件匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-108">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="628f7-109">`Find-Module` 返回它找到的每个模块的 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="628f7-109">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="628f7-110">这些对象可通过管道向下发送到 cmdlet，例如 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="628f7-110">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="628f7-111">第一次 `Find-Module` 尝试使用存储库时，系统可能会提示您安装更新。</span><span class="sxs-lookup"><span data-stu-id="628f7-111">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="628f7-112">如果存储库源未注册 `Register-PSRepository` 到 cmdlet，则会返回错误。</span><span class="sxs-lookup"><span data-stu-id="628f7-112">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="628f7-113">`Find-Module` 如果未使用限制版本的参数，则返回模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-113">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="628f7-114">若要获取存储库的模块版本的列表，请使用参数 **AllVersions**。</span><span class="sxs-lookup"><span data-stu-id="628f7-114">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="628f7-115">如果指定了 **MinimumVersion** 参数，则将 `Find-Module` 返回等于或大于最小值的模块的版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-115">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="628f7-116">如果存储库中有可用的更新版本，则返回较新版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-116">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="628f7-117">如果指定了 **MaximumVersion** 参数，则将 `Find-Module` 返回最新版本的模块，该模块不超过指定的版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-117">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="628f7-118">如果指定了 **RequiredVersion** 参数，则 `Find-Module` 仅返回与指定版本完全匹配的模块版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-118">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="628f7-119">`Find-Module` 搜索所有可用的模块，因为源之间的名称冲突可能会发生。</span><span class="sxs-lookup"><span data-stu-id="628f7-119">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="628f7-120">下面的示例使用 [PowerShell 库](https://www.powershellgallery.com/) 作为唯一的已注册存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-120">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="628f7-121">`Get-PSRepository` 显示已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-121">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="628f7-122">如果有多个已注册的存储库，请使用 `-Repository` 参数指定存储库的名称。</span><span class="sxs-lookup"><span data-stu-id="628f7-122">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="628f7-123">示例</span><span class="sxs-lookup"><span data-stu-id="628f7-123">EXAMPLES</span></span>

### <span data-ttu-id="628f7-124">示例1：按名称查找模块</span><span class="sxs-lookup"><span data-stu-id="628f7-124">Example 1: Find a module by name</span></span>

<span data-ttu-id="628f7-125">此示例查找默认存储库中的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-125">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="628f7-126">`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-126">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="628f7-127">示例2：查找具有类似名称的模块</span><span class="sxs-lookup"><span data-stu-id="628f7-127">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="628f7-128">此示例使用 `*`) 通配符 (星号来查找具有类似名称的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-128">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="628f7-129">`Find-Module`Cmdlet 将 **Name** 参数与星号一起使用 (`*`) 通配符来查找包含 **PowerShell** 的所有模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-129">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="628f7-130">示例3：按最低版本查找模块</span><span class="sxs-lookup"><span data-stu-id="628f7-130">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="628f7-131">此示例将搜索模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-131">This example searches for a module's minimum version.</span></span> <span data-ttu-id="628f7-132">如果存储库包含较新版本的模块，则返回较新版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-132">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="628f7-133">`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-133">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="628f7-134">**MinimumVersion** 指定版本 **1.6.5**。</span><span class="sxs-lookup"><span data-stu-id="628f7-134">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="628f7-135">`Find-Module` 返回 PowerShellGet 版本 **2.1.0** ，因为它超过最低版本并且是最新版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-135">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="628f7-136">示例4：查找特定版本的模块</span><span class="sxs-lookup"><span data-stu-id="628f7-136">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="628f7-137">此示例将返回一个对象，该对象表示模块的特定版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-137">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="628f7-138">如果找不到指定版本，则会返回错误。</span><span class="sxs-lookup"><span data-stu-id="628f7-138">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="628f7-139">`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-139">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="628f7-140">**RequiredVersion** 参数指定版本 **1.6.5**。</span><span class="sxs-lookup"><span data-stu-id="628f7-140">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="628f7-141">示例5：查找特定存储库中的模块</span><span class="sxs-lookup"><span data-stu-id="628f7-141">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="628f7-142">此示例使用 **存储库** 参数查找特定存储库中的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-142">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="628f7-143">`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-143">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="628f7-144">**存储库** 参数指定搜索 **PSGallery** 存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-144">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="628f7-145">示例6：在多个存储库中查找模块</span><span class="sxs-lookup"><span data-stu-id="628f7-145">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="628f7-146">此示例使用 `Register-PSRepository` 指定存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-146">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="628f7-147">`Find-Module` 使用存储库搜索模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-147">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="628f7-148">`Register-PSRepository`Cmdlet 将注册一个新存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-148">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="628f7-149">**Name** 参数将命名为 **MySource**。</span><span class="sxs-lookup"><span data-stu-id="628f7-149">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="628f7-150">**SourceLocation** 参数指定存储库的地址。</span><span class="sxs-lookup"><span data-stu-id="628f7-150">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="628f7-151">`Find-Module`Cmdlet 将 **Name** 参数与星号一起使用 (`*`) 通配符来指定 **Contoso** 模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-151">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="628f7-152">**存储库** 参数指定搜索两个存储库，即 **PSGallery** 和 **MySource**。</span><span class="sxs-lookup"><span data-stu-id="628f7-152">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="628f7-153">示例7：查找包含 DSC 资源的模块</span><span class="sxs-lookup"><span data-stu-id="628f7-153">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="628f7-154">此命令返回包含 DSC 资源的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-154">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="628f7-155">**包含** 参数具有四个用于搜索存储库的预定义功能。</span><span class="sxs-lookup"><span data-stu-id="628f7-155">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="628f7-156">使用 "选项卡-完成" 显示 **包含** 参数支持的四项功能。</span><span class="sxs-lookup"><span data-stu-id="628f7-156">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="628f7-157">`Find-Module`Cmdlet 使用 **存储** 库参数搜索存储库 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="628f7-157">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="628f7-158">**包含** 参数指定 **get-dscresource**，它是参数可在存储库中搜索的功能。</span><span class="sxs-lookup"><span data-stu-id="628f7-158">The **Includes** parameter specifies **DscResource**, which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="628f7-159">示例8：查找带有筛选器的模块</span><span class="sxs-lookup"><span data-stu-id="628f7-159">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="628f7-160">在此示例中，若要查找模块，请使用筛选器搜索存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-160">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="628f7-161">对于基于 NuGet 的存储库， **筛选器** 参数会搜索参数的名称、说明和标记。</span><span class="sxs-lookup"><span data-stu-id="628f7-161">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="628f7-162">`Find-Module`Cmdlet 使用 **筛选器** 参数在存储库中搜索 **AppDomain**。</span><span class="sxs-lookup"><span data-stu-id="628f7-162">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="628f7-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="628f7-163">PARAMETERS</span></span>

### <span data-ttu-id="628f7-164">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="628f7-164">-AllowPrerelease</span></span>

<span data-ttu-id="628f7-165">包含在标记为预发行版的结果模块中。</span><span class="sxs-lookup"><span data-stu-id="628f7-165">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="628f7-166">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="628f7-166">-AllVersions</span></span>

<span data-ttu-id="628f7-167">指定在结果中包括某个模块的所有版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-167">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="628f7-168">不能将 **AllVersions** 参数与 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="628f7-168">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="628f7-169">-Command</span><span class="sxs-lookup"><span data-stu-id="628f7-169">-Command</span></span>

<span data-ttu-id="628f7-170">指定要在模块中查找的命令数组。</span><span class="sxs-lookup"><span data-stu-id="628f7-170">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="628f7-171">命令可以是函数或工作流。</span><span class="sxs-lookup"><span data-stu-id="628f7-171">A command can be a function or workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="628f7-172">-Credential</span></span>

<span data-ttu-id="628f7-173">指定有权为指定的包提供程序或源安装模块的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="628f7-173">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-174">-DscResource</span><span class="sxs-lookup"><span data-stu-id="628f7-174">-DscResource</span></span>

<span data-ttu-id="628f7-175">指定包含 DSC 资源的模块的名称或名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="628f7-175">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="628f7-176">在提供多个参数时，按 PowerShell 约定执行 **或** 搜索。</span><span class="sxs-lookup"><span data-stu-id="628f7-176">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="628f7-177">-Filter</span></span>

<span data-ttu-id="628f7-178">基于 **PackageManagement** 提供程序特定的搜索语法指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="628f7-178">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="628f7-179">对于 NuGet 模块，此参数等效于使用 [PowerShell 库](https://www.powershellgallery.com/) 网站上的搜索栏进行搜索。</span><span class="sxs-lookup"><span data-stu-id="628f7-179">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="628f7-180">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="628f7-180">-IncludeDependencies</span></span>

<span data-ttu-id="628f7-181">指示此操作包含依赖于在 **Name** 参数中指定的模块的所有模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-181">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="628f7-182">-Includes</span><span class="sxs-lookup"><span data-stu-id="628f7-182">-Includes</span></span>

<span data-ttu-id="628f7-183">仅返回那些包含特定类型的 PowerShell 功能的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-183">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="628f7-184">例如，你可能只想查找包含 **get-dscresource** 的模块。</span><span class="sxs-lookup"><span data-stu-id="628f7-184">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="628f7-185">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="628f7-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="628f7-186">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="628f7-186">Cmdlet</span></span>
- <span data-ttu-id="628f7-187">DscResource</span><span class="sxs-lookup"><span data-stu-id="628f7-187">DscResource</span></span>
- <span data-ttu-id="628f7-188">函数</span><span class="sxs-lookup"><span data-stu-id="628f7-188">Function</span></span>
- <span data-ttu-id="628f7-189">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="628f7-189">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-190">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="628f7-190">-MaximumVersion</span></span>

<span data-ttu-id="628f7-191">指定要包括在搜索结果中的模块的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-191">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="628f7-192">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="628f7-192">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-193">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="628f7-193">-MinimumVersion</span></span>

<span data-ttu-id="628f7-194">指定要包括在结果中的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="628f7-194">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="628f7-195">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="628f7-195">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-196">-Name</span><span class="sxs-lookup"><span data-stu-id="628f7-196">-Name</span></span>

<span data-ttu-id="628f7-197">指定要在存储库中搜索的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="628f7-197">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="628f7-198">接受以逗号分隔的模块名称列表。</span><span class="sxs-lookup"><span data-stu-id="628f7-198">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="628f7-199">可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="628f7-199">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-200">-Proxy</span><span class="sxs-lookup"><span data-stu-id="628f7-200">-Proxy</span></span>

<span data-ttu-id="628f7-201">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="628f7-201">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-202">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="628f7-202">-ProxyCredential</span></span>

<span data-ttu-id="628f7-203">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="628f7-203">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-204">-Repository</span><span class="sxs-lookup"><span data-stu-id="628f7-204">-Repository</span></span>

<span data-ttu-id="628f7-205">使用 " **存储库** " 参数可以指定要搜索模块的存储库。</span><span class="sxs-lookup"><span data-stu-id="628f7-205">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="628f7-206">当注册多个存储库时使用。</span><span class="sxs-lookup"><span data-stu-id="628f7-206">Used when multiple repositories are registered.</span></span> <span data-ttu-id="628f7-207">接受以逗号分隔的存储库列表。</span><span class="sxs-lookup"><span data-stu-id="628f7-207">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="628f7-208">若要注册存储库，请使用 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="628f7-208">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="628f7-209">若要显示已注册的存储库，请使用 `Get-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="628f7-209">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-210">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="628f7-210">-RequiredVersion</span></span>

<span data-ttu-id="628f7-211">指定要包含在结果中的模块的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="628f7-211">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="628f7-212">对于 **MinimumVersion** 或 **MaximumVersion**，不能在同一命令中使用 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="628f7-212">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-213">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="628f7-213">-RoleCapability</span></span>

<span data-ttu-id="628f7-214">指定角色功能的数组。</span><span class="sxs-lookup"><span data-stu-id="628f7-214">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-215">-Tag</span><span class="sxs-lookup"><span data-stu-id="628f7-215">-Tag</span></span>

<span data-ttu-id="628f7-216">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="628f7-216">Specifies an array of tags.</span></span> <span data-ttu-id="628f7-217">示例标记包括 **DesiredStateConfiguration**、 **DSC**、 **DSCResourceKit** 或 **PSModule**。</span><span class="sxs-lookup"><span data-stu-id="628f7-217">Example tags include **DesiredStateConfiguration**, **DSC**, **DSCResourceKit**, or **PSModule**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="628f7-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="628f7-218">CommonParameters</span></span>

<span data-ttu-id="628f7-219">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="628f7-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="628f7-220">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="628f7-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="628f7-221">输入</span><span class="sxs-lookup"><span data-stu-id="628f7-221">INPUTS</span></span>

### <span data-ttu-id="628f7-222">System.String[]</span><span class="sxs-lookup"><span data-stu-id="628f7-222">System.String[]</span></span>

### <span data-ttu-id="628f7-223">System.String</span><span class="sxs-lookup"><span data-stu-id="628f7-223">System.String</span></span>

### <span data-ttu-id="628f7-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="628f7-224">System.Uri</span></span>

### <span data-ttu-id="628f7-225">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="628f7-225">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="628f7-226">输出</span><span class="sxs-lookup"><span data-stu-id="628f7-226">OUTPUTS</span></span>

### <span data-ttu-id="628f7-227">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="628f7-227">PSRepositoryItemInfo</span></span>

<span data-ttu-id="628f7-228">`Find-Module` 创建可通过管道向下发送到 cmdlet （如）的 **PSRepositoryItemInfo** 对象 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="628f7-228">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="628f7-229">注释</span><span class="sxs-lookup"><span data-stu-id="628f7-229">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="628f7-230">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="628f7-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="628f7-231">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="628f7-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="628f7-232">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="628f7-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="628f7-233">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="628f7-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="628f7-234">相关链接</span><span class="sxs-lookup"><span data-stu-id="628f7-234">RELATED LINKS</span></span>

[<span data-ttu-id="628f7-235">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="628f7-235">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="628f7-236">Install-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-236">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="628f7-237">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-237">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="628f7-238">Save-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-238">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="628f7-239">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-239">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="628f7-240">Update-Module</span><span class="sxs-lookup"><span data-stu-id="628f7-240">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="628f7-241">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="628f7-241">Register-PSRepository</span></span>](Register-PSRepository.md)
