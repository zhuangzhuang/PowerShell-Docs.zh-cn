---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: a84dee14872ad5a7d0f7bac8e0057dc527855074
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596217"
---
# <span data-ttu-id="a2ca4-102">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a2ca4-102">Find-RoleCapability</span></span>

## <span data-ttu-id="a2ca4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a2ca4-103">SYNOPSIS</span></span>
<span data-ttu-id="a2ca4-104">在模块中查找角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-104">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="a2ca4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a2ca4-105">SYNTAX</span></span>

### <span data-ttu-id="a2ca4-106">全部</span><span class="sxs-lookup"><span data-stu-id="a2ca4-106">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a2ca4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a2ca4-107">DESCRIPTION</span></span>

<span data-ttu-id="a2ca4-108">`Find-RoleCapability`Cmdlet 可搜索已注册的存储库，以便查找 PowerShell 角色功能和模块。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-108">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="a2ca4-109">对于找到的每个角色功能 `Find-RoleCapability` ，都将返回 **PSGetRoleCapabilityInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-109">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="a2ca4-110">可以通过管道将 **PSGetRoleCapabilityInfo** 对象发送到 `Install-Module` 或 `Save-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-110">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="a2ca4-111">PowerShell 角色功能定义 (JEA) 终结点上的足够管理的用户可使用哪些命令和应用程序。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-111">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="a2ca4-112">角色功能由扩展名为的文件定义 `.psrc` 。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-112">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="a2ca4-113">示例</span><span class="sxs-lookup"><span data-stu-id="a2ca4-113">EXAMPLES</span></span>

### <span data-ttu-id="a2ca4-114">示例1：查找角色功能</span><span class="sxs-lookup"><span data-stu-id="a2ca4-114">Example 1: Find role capabilities</span></span>

<span data-ttu-id="a2ca4-115">`Find-RoleCapability` 查找每个已注册存储库中的角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-115">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="a2ca4-116">若要搜索特定存储库，请使用 **存储库** 参数。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-116">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="a2ca4-117">示例2：按名称查找角色功能</span><span class="sxs-lookup"><span data-stu-id="a2ca4-117">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="a2ca4-118">`Find-RoleCapability` 按名称查找角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-118">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="a2ca4-119">使用逗号分隔名称数组。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-119">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="a2ca4-120">示例3：查找并保存角色功能的模块</span><span class="sxs-lookup"><span data-stu-id="a2ca4-120">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="a2ca4-121">`Find-RoleCapability`Cmdlet 查找角色功能，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-121">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="a2ca4-122">`Save-Module` 将角色功能的模块保存到文件系统。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-122">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="a2ca4-123">`Get-ChildItem` 显示模块目录的内容。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-123">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="a2ca4-124">`Find-RoleCapability` 使用 **Name** 参数指定 **一般的 Lev1** 角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-124">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="a2ca4-125">对象沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-125">The object is sent down the pipeline.</span></span> <span data-ttu-id="a2ca4-126">`Save-Module` 使用文件系统位置的 **Path** 参数保存模块。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-126">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="a2ca4-127">保存该模块后，将 `Get-ChildItem` 指定该模块的 **路径** 并显示 **JeaExamples** 模块的目录的内容。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-127">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="a2ca4-128">示例4：查找和安装角色功能的模块</span><span class="sxs-lookup"><span data-stu-id="a2ca4-128">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="a2ca4-129">`Find-RoleCapability` 查找模块并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-129">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="a2ca4-130">`Install-Module` 安装模块。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-130">`Install-Module` installs the module.</span></span> <span data-ttu-id="a2ca4-131">安装后，请使用 `Get-InstalledModule` 查看结果。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-131">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="a2ca4-132">`Find-RoleCapability` 使用 **Name** 参数指定 **一般的 Lev1** 角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-132">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="a2ca4-133">对象沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-133">The object is sent down the pipeline.</span></span> <span data-ttu-id="a2ca4-134">`Install-Module` 使用 **Verbose** 参数显示安装过程中的状态消息。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-134">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="a2ca4-135">安装完成后， `Get-InstalledModule` 输出确认已安装 **JeaExamples** 模块。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-135">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="a2ca4-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a2ca4-136">PARAMETERS</span></span>

### <span data-ttu-id="a2ca4-137">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a2ca4-137">-AllowPrerelease</span></span>

<span data-ttu-id="a2ca4-138">在结果中包括标记为预发行的资源。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-138">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="a2ca4-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a2ca4-139">-AllVersions</span></span>

<span data-ttu-id="a2ca4-140">指示此 cmdlet 获取模块的所有版本。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-140">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="a2ca4-141">**AllVersions** 参数显示模块的每个可用版本。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-141">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="a2ca4-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="a2ca4-142">-Filter</span></span>

<span data-ttu-id="a2ca4-143">基于 **PackageManagement** 提供程序的搜索语法查找资源。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-143">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="a2ca4-144">例如，指定要在 **ModuleName** 和 **Description** 属性内搜索的字词。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-144">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="a2ca4-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a2ca4-145">-MaximumVersion</span></span>

<span data-ttu-id="a2ca4-146">指定要包含在结果中的模块的最高版本。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-146">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="a2ca4-147">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-147">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a2ca4-148">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a2ca4-148">-MinimumVersion</span></span>

<span data-ttu-id="a2ca4-149">指定要包括在结果中的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-149">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="a2ca4-150">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-150">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a2ca4-151">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="a2ca4-151">-ModuleName</span></span>

<span data-ttu-id="a2ca4-152">指定要在其中搜索角色功能的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-152">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="a2ca4-153">默认值为所有模块。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-153">The default is all modules.</span></span>

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

### <span data-ttu-id="a2ca4-154">-Name</span><span class="sxs-lookup"><span data-stu-id="a2ca4-154">-Name</span></span>

<span data-ttu-id="a2ca4-155">指定角色功能的名称。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-155">Specifies the name of a role capability.</span></span> <span data-ttu-id="a2ca4-156">默认值为所有角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-156">The default is all role capabilities.</span></span> <span data-ttu-id="a2ca4-157">使用逗号分隔资源名称的数组。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-157">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="a2ca4-158">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a2ca4-158">-Proxy</span></span>

<span data-ttu-id="a2ca4-159">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-159">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="a2ca4-160">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a2ca4-160">-ProxyCredential</span></span>

<span data-ttu-id="a2ca4-161">指定有权使用 **代理** 参数中指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-161">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a2ca4-162">-Repository</span><span class="sxs-lookup"><span data-stu-id="a2ca4-162">-Repository</span></span>

<span data-ttu-id="a2ca4-163">指定用于搜索角色功能的存储库。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-163">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="a2ca4-164">使用逗号分隔存储库名称数组。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-164">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="a2ca4-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a2ca4-165">-RequiredVersion</span></span>

<span data-ttu-id="a2ca4-166">指定要包含在结果中的模块的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-166">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="a2ca4-167">无法在同一命令中使用 **RequiredVersion** 和 **MinimumVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-167">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a2ca4-168">-Tag</span><span class="sxs-lookup"><span data-stu-id="a2ca4-168">-Tag</span></span>

<span data-ttu-id="a2ca4-169">指定对存储库中的模块进行分类的标记。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-169">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="a2ca4-170">使用逗号分隔标记数组。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-170">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="a2ca4-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2ca4-171">CommonParameters</span></span>

<span data-ttu-id="a2ca4-172">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a2ca4-173">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a2ca4-174">输入</span><span class="sxs-lookup"><span data-stu-id="a2ca4-174">INPUTS</span></span>

### <span data-ttu-id="a2ca4-175">System.Uri</span><span class="sxs-lookup"><span data-stu-id="a2ca4-175">System.Uri</span></span>

### <span data-ttu-id="a2ca4-176">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="a2ca4-176">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="a2ca4-177">输出</span><span class="sxs-lookup"><span data-stu-id="a2ca4-177">OUTPUTS</span></span>

### <span data-ttu-id="a2ca4-178">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="a2ca4-178">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="a2ca4-179">`Find-RoleCapability`Cmdlet 将返回 **PSGetRoleCapabilityInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-179">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="a2ca4-180">注释</span><span class="sxs-lookup"><span data-stu-id="a2ca4-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2ca4-181">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a2ca4-182">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a2ca4-183">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="a2ca4-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a2ca4-184">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="a2ca4-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a2ca4-185">相关链接</span><span class="sxs-lookup"><span data-stu-id="a2ca4-185">RELATED LINKS</span></span>

[<span data-ttu-id="a2ca4-186">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a2ca4-186">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="a2ca4-187">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a2ca4-187">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="a2ca4-188">Install-Module</span><span class="sxs-lookup"><span data-stu-id="a2ca4-188">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="a2ca4-189">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="a2ca4-189">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="a2ca4-190">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a2ca4-190">Save-Module</span></span>](Save-Module.md)
