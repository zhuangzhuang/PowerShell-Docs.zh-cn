---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 9f258c3b02064aafdaf272141f2613ff5cbaf5b5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596422"
---
# <span data-ttu-id="c4d1c-102">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4d1c-102">Set-PackageSource</span></span>

## <span data-ttu-id="c4d1c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c4d1c-103">SYNOPSIS</span></span>
<span data-ttu-id="c4d1c-104">替换指定包提供程序的包源。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-104">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="c4d1c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4d1c-105">SYNTAX</span></span>

### <span data-ttu-id="c4d1c-106">SourceBySearch (默认值) </span><span class="sxs-lookup"><span data-stu-id="c4d1c-106">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="c4d1c-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4d1c-107">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c4d1c-108">NuGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4d1c-108">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="c4d1c-109">NuGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="c4d1c-109">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="c4d1c-110">PowerShellGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4d1c-110">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="c4d1c-111">PowerShellGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="c4d1c-111">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="c4d1c-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c4d1c-112">DESCRIPTION</span></span>

<span data-ttu-id="c4d1c-113">`Set-PackageSource`替换指定包提供程序的包源。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-113">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="c4d1c-114">包源始终由包提供程序进行管理。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-114">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="c4d1c-115">示例</span><span class="sxs-lookup"><span data-stu-id="c4d1c-115">EXAMPLES</span></span>

### <span data-ttu-id="c4d1c-116">示例1：更改包源</span><span class="sxs-lookup"><span data-stu-id="c4d1c-116">Example 1: Change a package source</span></span>

<span data-ttu-id="c4d1c-117">此命令更改包源的现有名称。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-117">This command changes the existing name of a package source.</span></span> <span data-ttu-id="c4d1c-118">源设置为 " **受信任**"，这会在安装包时消除用于验证源的提示。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-118">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="c4d1c-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4d1c-119">PARAMETERS</span></span>

### <span data-ttu-id="c4d1c-120">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="c4d1c-120">-ConfigFile</span></span>

<span data-ttu-id="c4d1c-121">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-121">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="c4d1c-122">-Credential</span></span>

<span data-ttu-id="c4d1c-123">指定有权安装包提供程序的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-123">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="c4d1c-124">-Force</span><span class="sxs-lookup"><span data-stu-id="c4d1c-124">-Force</span></span>

<span data-ttu-id="c4d1c-125">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c4d1c-126">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="c4d1c-126">-ForceBootstrap</span></span>

<span data-ttu-id="c4d1c-127">指示 `Set-PackageSource` 强制 **PackageManagement** 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-127">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="c4d1c-128">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c4d1c-128">-InputObject</span></span>

<span data-ttu-id="c4d1c-129">指定表示要更改的包的包源 ID 对象。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-129">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="c4d1c-130">包源 Id 是 cmdlet 结果的一部分 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-130">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-131">-Location</span><span class="sxs-lookup"><span data-stu-id="c4d1c-131">-Location</span></span>

<span data-ttu-id="c4d1c-132">指定当前包的源位置。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-132">Specifies the current package source location.</span></span> <span data-ttu-id="c4d1c-133">该值可以是 URI、文件路径或包提供程序支持的任何其他目标格式。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-133">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-134">-Name</span><span class="sxs-lookup"><span data-stu-id="c4d1c-134">-Name</span></span>

<span data-ttu-id="c4d1c-135">指定包源的名称。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-135">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-136">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="c4d1c-136">-NewLocation</span></span>

<span data-ttu-id="c4d1c-137">指定包源的新位置。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-137">Specifies the new location for a package source.</span></span> <span data-ttu-id="c4d1c-138">该值可以是 URI、文件路径或包提供程序支持的任何其他目标格式。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-138">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="c4d1c-139">-NewName</span><span class="sxs-lookup"><span data-stu-id="c4d1c-139">-NewName</span></span>

<span data-ttu-id="c4d1c-140">指定分配给包源的新名称。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-140">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="c4d1c-141">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="c4d1c-141">-PackageManagementProvider</span></span>

<span data-ttu-id="c4d1c-142">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-142">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-143">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="c4d1c-143">-ProviderName</span></span>

<span data-ttu-id="c4d1c-144">指定提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-144">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-145">-Proxy</span><span class="sxs-lookup"><span data-stu-id="c4d1c-145">-Proxy</span></span>

<span data-ttu-id="c4d1c-146">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-146">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="c4d1c-147">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="c4d1c-147">-ProxyCredential</span></span>

<span data-ttu-id="c4d1c-148">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-148">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="c4d1c-149">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="c4d1c-149">-PublishLocation</span></span>

<span data-ttu-id="c4d1c-150">指定发布位置。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-150">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-151">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="c4d1c-151">-ScriptPublishLocation</span></span>

<span data-ttu-id="c4d1c-152">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-152">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-153">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="c4d1c-153">-ScriptSourceLocation</span></span>

<span data-ttu-id="c4d1c-154">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-154">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-155">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="c4d1c-155">-SkipValidate</span></span>

<span data-ttu-id="c4d1c-156">跳过验证包源凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-156">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4d1c-157">-Trusted</span><span class="sxs-lookup"><span data-stu-id="c4d1c-157">-Trusted</span></span>

<span data-ttu-id="c4d1c-158">指示源是受信任的包提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-158">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="c4d1c-159">受信任的源不会提示验证安装包。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-159">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="c4d1c-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c4d1c-160">-Confirm</span></span>

<span data-ttu-id="c4d1c-161">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c4d1c-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c4d1c-162">-WhatIf</span></span>

<span data-ttu-id="c4d1c-163">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c4d1c-164">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c4d1c-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4d1c-165">CommonParameters</span></span>

<span data-ttu-id="c4d1c-166">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4d1c-167">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4d1c-168">输入</span><span class="sxs-lookup"><span data-stu-id="c4d1c-168">INPUTS</span></span>

### <span data-ttu-id="c4d1c-169">`Set-PackageSource` 不接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-169">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="c4d1c-170">输出</span><span class="sxs-lookup"><span data-stu-id="c4d1c-170">OUTPUTS</span></span>

### <span data-ttu-id="c4d1c-171">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-171">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c4d1c-172">注释</span><span class="sxs-lookup"><span data-stu-id="c4d1c-172">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4d1c-173">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-173">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="c4d1c-174">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-174">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="c4d1c-175">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="c4d1c-175">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="c4d1c-176">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="c4d1c-176">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="c4d1c-177">相关链接</span><span class="sxs-lookup"><span data-stu-id="c4d1c-177">RELATED LINKS</span></span>

[<span data-ttu-id="c4d1c-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c4d1c-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="c4d1c-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4d1c-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="c4d1c-180">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4d1c-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="c4d1c-181">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4d1c-181">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
