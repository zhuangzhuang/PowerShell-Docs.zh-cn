---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: a24d66aa1ce9e353e41cc7a686ee9f910a7106fc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596417"
---
# <span data-ttu-id="26510-102">Find-Command</span><span class="sxs-lookup"><span data-stu-id="26510-102">Find-Command</span></span>

## <span data-ttu-id="26510-103">摘要</span><span class="sxs-lookup"><span data-stu-id="26510-103">SYNOPSIS</span></span>
<span data-ttu-id="26510-104">查找模块中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="26510-104">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="26510-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26510-105">SYNTAX</span></span>

### <span data-ttu-id="26510-106">全部</span><span class="sxs-lookup"><span data-stu-id="26510-106">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="26510-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26510-107">DESCRIPTION</span></span>

<span data-ttu-id="26510-108">`Find-Command`Cmdlet 将查找 cmdlet、别名、函数和工作流等 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="26510-108">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="26510-109">`Find-Command` 搜索已注册存储库中的模块。</span><span class="sxs-lookup"><span data-stu-id="26510-109">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="26510-110">对于找到的每个命令 `Find-Command` ，将返回一个 **PSGetCommandInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="26510-110">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="26510-111">可以通过管道将 **PSGetCommandInfo** 对象发送到 `Install-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26510-111">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="26510-112">`Install-Module` 安装包含命令的模块。</span><span class="sxs-lookup"><span data-stu-id="26510-112">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="26510-113">示例</span><span class="sxs-lookup"><span data-stu-id="26510-113">EXAMPLES</span></span>

### <span data-ttu-id="26510-114">示例 1：在指定存储库中查找所有命令</span><span class="sxs-lookup"><span data-stu-id="26510-114">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="26510-115">`Find-Command`Cmdlet 将在已注册的存储库中搜索模块。</span><span class="sxs-lookup"><span data-stu-id="26510-115">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="26510-116">`Find-Command` 使用 **存储** 库参数指定已注册的存储库的名称。</span><span class="sxs-lookup"><span data-stu-id="26510-116">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="26510-117">对象沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="26510-117">The objects are sent down the pipeline.</span></span> <span data-ttu-id="26510-118">`Select-Object` 接收对象，并使用 **第** 一个参数来显示前10个结果。</span><span class="sxs-lookup"><span data-stu-id="26510-118">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="26510-119">示例 2：按名称查找命令</span><span class="sxs-lookup"><span data-stu-id="26510-119">Example 2: Find a command by name</span></span>

<span data-ttu-id="26510-120">`Find-Command` 可以使用命令名称在存储库中查找模块。</span><span class="sxs-lookup"><span data-stu-id="26510-120">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="26510-121">命令名称可能存在于多个 **ModuleNames** 中。</span><span class="sxs-lookup"><span data-stu-id="26510-121">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="26510-122">`Find-Command` 使用 **存储库** 参数搜索 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="26510-122">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="26510-123">**Name** 参数指定命令 **test-targetresource**。</span><span class="sxs-lookup"><span data-stu-id="26510-123">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="26510-124">示例3：按名称查找命令并安装模块</span><span class="sxs-lookup"><span data-stu-id="26510-124">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="26510-125">`Find-Command` 可以找到命令和模块，然后将对象发送到 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="26510-125">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="26510-126">如果在多个模块中包含一个命令，请使用 `Find-Command` Cmdlet **Module-Name** 参数。</span><span class="sxs-lookup"><span data-stu-id="26510-126">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="26510-127">否则，可能会安装不希望安装的模块。</span><span class="sxs-lookup"><span data-stu-id="26510-127">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="26510-128">`Find-Command` 使用 **Name** 参数指定命令 **test-targetresource**。</span><span class="sxs-lookup"><span data-stu-id="26510-128">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="26510-129">**存储库** 参数搜索 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="26510-129">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="26510-130">**ModuleName** 参数指定要安装的模块 **SystemLocaleDsc**。</span><span class="sxs-lookup"><span data-stu-id="26510-130">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="26510-131">将对象向下发送到 `Install-Module` ，并安装该模块。</span><span class="sxs-lookup"><span data-stu-id="26510-131">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="26510-132">安装完成后，可以使用 `Get-InstalledModule` 来显示结果。</span><span class="sxs-lookup"><span data-stu-id="26510-132">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="26510-133">示例 4：查找命令并保存其模块</span><span class="sxs-lookup"><span data-stu-id="26510-133">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="26510-134">`Find-Command`使用 **Name** 和 **Repository** 参数在 **PSGallery** 存储库中搜索命令 **ScriptAnalyzer** 。</span><span class="sxs-lookup"><span data-stu-id="26510-134">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="26510-135">将对象向下发送到 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="26510-135">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="26510-136">**Path** 参数确定保存模块的位置。</span><span class="sxs-lookup"><span data-stu-id="26510-136">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="26510-137">"**详细**" 是一个可选参数，但在 PowerShell 控制台中显示状态输出。</span><span class="sxs-lookup"><span data-stu-id="26510-137">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="26510-138">详细输出对于故障排除非常有用。</span><span class="sxs-lookup"><span data-stu-id="26510-138">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="26510-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26510-139">PARAMETERS</span></span>

### <span data-ttu-id="26510-140">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="26510-140">-AllowPrerelease</span></span>

<span data-ttu-id="26510-141">在结果中包括标记为预发行的模块。</span><span class="sxs-lookup"><span data-stu-id="26510-141">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="26510-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="26510-142">-AllVersions</span></span>

<span data-ttu-id="26510-143">指示此 cmdlet 获取模块的所有版本。</span><span class="sxs-lookup"><span data-stu-id="26510-143">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="26510-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="26510-144">-Filter</span></span>

<span data-ttu-id="26510-145">基于 **PackageManagement** 提供程序的搜索语法查找模块。</span><span class="sxs-lookup"><span data-stu-id="26510-145">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="26510-146">例如，指定要在 **ModuleName** 和 **Description** 属性内搜索的字词。</span><span class="sxs-lookup"><span data-stu-id="26510-146">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="26510-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="26510-147">-MaximumVersion</span></span>

<span data-ttu-id="26510-148">指定要包含在结果中的模块的最高版本。</span><span class="sxs-lookup"><span data-stu-id="26510-148">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="26510-149">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="26510-149">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="26510-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="26510-150">-MinimumVersion</span></span>

<span data-ttu-id="26510-151">指定要包括在结果中的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="26510-151">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="26510-152">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="26510-152">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="26510-153">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="26510-153">-ModuleName</span></span>

<span data-ttu-id="26510-154">指定要在其中搜索命令的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="26510-154">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="26510-155">默认值为所有模块。</span><span class="sxs-lookup"><span data-stu-id="26510-155">The default is all modules.</span></span>

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

### <span data-ttu-id="26510-156">-Name</span><span class="sxs-lookup"><span data-stu-id="26510-156">-Name</span></span>

<span data-ttu-id="26510-157">指定要在存储库中搜索的命令名。</span><span class="sxs-lookup"><span data-stu-id="26510-157">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="26510-158">使用逗号分隔命令名称的数组。</span><span class="sxs-lookup"><span data-stu-id="26510-158">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="26510-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="26510-159">-Proxy</span></span>

<span data-ttu-id="26510-160">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="26510-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="26510-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="26510-161">-ProxyCredential</span></span>

<span data-ttu-id="26510-162">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="26510-162">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="26510-163">-Repository</span><span class="sxs-lookup"><span data-stu-id="26510-163">-Repository</span></span>

<span data-ttu-id="26510-164">指定用于搜索命令的存储库。</span><span class="sxs-lookup"><span data-stu-id="26510-164">Specifies the repository to search for commands.</span></span> <span data-ttu-id="26510-165">使用逗号分隔存储库名称数组。</span><span class="sxs-lookup"><span data-stu-id="26510-165">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="26510-166">默认值为所有存储库。</span><span class="sxs-lookup"><span data-stu-id="26510-166">The default is all repositories.</span></span>

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

### <span data-ttu-id="26510-167">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="26510-167">-RequiredVersion</span></span>

<span data-ttu-id="26510-168">指定要包括在结果中的模块的版本。</span><span class="sxs-lookup"><span data-stu-id="26510-168">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="26510-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="26510-169">-Tag</span></span>

<span data-ttu-id="26510-170">指定对存储库中的模块进行分类的标记。</span><span class="sxs-lookup"><span data-stu-id="26510-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="26510-171">使用逗号分隔标记数组。</span><span class="sxs-lookup"><span data-stu-id="26510-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="26510-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26510-172">CommonParameters</span></span>

<span data-ttu-id="26510-173">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26510-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26510-174">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26510-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26510-175">输入</span><span class="sxs-lookup"><span data-stu-id="26510-175">INPUTS</span></span>

## <span data-ttu-id="26510-176">输出</span><span class="sxs-lookup"><span data-stu-id="26510-176">OUTPUTS</span></span>

### <span data-ttu-id="26510-177">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="26510-177">PSGetCommandInfo</span></span>

<span data-ttu-id="26510-178">`Find-Command` 输出 **PSGetCommandInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="26510-178">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="26510-179">注释</span><span class="sxs-lookup"><span data-stu-id="26510-179">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26510-180">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="26510-180">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="26510-181">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="26510-181">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="26510-182">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="26510-182">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="26510-183">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="26510-183">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="26510-184">相关链接</span><span class="sxs-lookup"><span data-stu-id="26510-184">RELATED LINKS</span></span>

[<span data-ttu-id="26510-185">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="26510-185">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="26510-186">Install-Module</span><span class="sxs-lookup"><span data-stu-id="26510-186">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="26510-187">Save-Module</span><span class="sxs-lookup"><span data-stu-id="26510-187">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="26510-188">Select-Object</span><span class="sxs-lookup"><span data-stu-id="26510-188">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="26510-189">Uninstall-模块</span><span class="sxs-lookup"><span data-stu-id="26510-189">Uninstall-Module</span></span>](Uninstall-Module.md)
