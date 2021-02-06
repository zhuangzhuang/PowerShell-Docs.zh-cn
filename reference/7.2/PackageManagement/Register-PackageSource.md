---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: 76b3bd49f81f42cc80f4127f4b549acddcd1d906
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597460"
---
# <span data-ttu-id="cc0a6-102">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="cc0a6-102">Register-PackageSource</span></span>

## <span data-ttu-id="cc0a6-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cc0a6-103">SYNOPSIS</span></span>
<span data-ttu-id="cc0a6-104">为指定的包提供程序添加包源。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-104">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="cc0a6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cc0a6-105">SYNTAX</span></span>

### <span data-ttu-id="cc0a6-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="cc0a6-106">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="cc0a6-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="cc0a6-107">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="cc0a6-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="cc0a6-108">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="cc0a6-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cc0a6-109">DESCRIPTION</span></span>

<span data-ttu-id="cc0a6-110">`Register-PackageSource`Cmdlet 为指定的包提供程序添加包源。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-110">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="cc0a6-111">包源始终由包提供程序进行管理。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-111">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="cc0a6-112">如果包提供程序无法添加或替换包源，则提供程序会生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-112">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="cc0a6-113">示例</span><span class="sxs-lookup"><span data-stu-id="cc0a6-113">EXAMPLES</span></span>

### <span data-ttu-id="cc0a6-114">示例 1：为 NuGet 提供程序注册包源</span><span class="sxs-lookup"><span data-stu-id="cc0a6-114">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="cc0a6-115">此命令向 **NuGet** 提供程序的基于 web 的位置注册包源。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-115">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="cc0a6-116">默认情况下，源不受信任。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-116">By default, sources aren't trusted.</span></span> <span data-ttu-id="cc0a6-117">安装包之前，系统将提示你确认源是否受信任。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-117">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="cc0a6-118">若要重写默认值，请使用 `-Trusted` 参数。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-118">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="cc0a6-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc0a6-119">PARAMETERS</span></span>

### <span data-ttu-id="cc0a6-120">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="cc0a6-120">-ConfigFile</span></span>

<span data-ttu-id="cc0a6-121">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-121">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="cc0a6-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="cc0a6-122">-Credential</span></span>

<span data-ttu-id="cc0a6-123">指定有权访问经过身份验证的位置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-123">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="cc0a6-124">-Force</span><span class="sxs-lookup"><span data-stu-id="cc0a6-124">-Force</span></span>

<span data-ttu-id="cc0a6-125">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cc0a6-126">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="cc0a6-126">-ForceBootstrap</span></span>

<span data-ttu-id="cc0a6-127">指示此 cmdlet 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-127">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="cc0a6-128">-Location</span><span class="sxs-lookup"><span data-stu-id="cc0a6-128">-Location</span></span>

<span data-ttu-id="cc0a6-129">指定包源位置。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-129">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc0a6-130">-Name</span><span class="sxs-lookup"><span data-stu-id="cc0a6-130">-Name</span></span>

<span data-ttu-id="cc0a6-131">指定要注册的包源的名称。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-131">Specifies the name of the package source to register.</span></span>

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

### <span data-ttu-id="cc0a6-132">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="cc0a6-132">-PackageManagementProvider</span></span>

<span data-ttu-id="cc0a6-133">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-133">Specifies the Package Management provider.</span></span>

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

### <span data-ttu-id="cc0a6-134">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="cc0a6-134">-ProviderName</span></span>

<span data-ttu-id="cc0a6-135">指定包提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-135">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="cc0a6-136">-Proxy</span><span class="sxs-lookup"><span data-stu-id="cc0a6-136">-Proxy</span></span>

<span data-ttu-id="cc0a6-137">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-137">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="cc0a6-138">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="cc0a6-138">-ProxyCredential</span></span>

<span data-ttu-id="cc0a6-139">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-139">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="cc0a6-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="cc0a6-140">-PublishLocation</span></span>

<span data-ttu-id="cc0a6-141">指定发布位置。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-141">Specifies the publish location.</span></span>

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

### <span data-ttu-id="cc0a6-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="cc0a6-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="cc0a6-143">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="cc0a6-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="cc0a6-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="cc0a6-145">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="cc0a6-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="cc0a6-146">-SkipValidate</span></span>

<span data-ttu-id="cc0a6-147">跳过验证包源凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="cc0a6-148">-Trusted</span><span class="sxs-lookup"><span data-stu-id="cc0a6-148">-Trusted</span></span>

<span data-ttu-id="cc0a6-149">指示信任包源。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-149">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="cc0a6-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cc0a6-150">-Confirm</span></span>

<span data-ttu-id="cc0a6-151">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cc0a6-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cc0a6-152">-WhatIf</span></span>

<span data-ttu-id="cc0a6-153">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cc0a6-154">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cc0a6-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc0a6-155">CommonParameters</span></span>

<span data-ttu-id="cc0a6-156">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc0a6-157">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc0a6-158">输入</span><span class="sxs-lookup"><span data-stu-id="cc0a6-158">INPUTS</span></span>

## <span data-ttu-id="cc0a6-159">输出</span><span class="sxs-lookup"><span data-stu-id="cc0a6-159">OUTPUTS</span></span>

## <span data-ttu-id="cc0a6-160">注释</span><span class="sxs-lookup"><span data-stu-id="cc0a6-160">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc0a6-161">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-161">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="cc0a6-162">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-162">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="cc0a6-163">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="cc0a6-163">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="cc0a6-164">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="cc0a6-164">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="cc0a6-165">相关链接</span><span class="sxs-lookup"><span data-stu-id="cc0a6-165">RELATED LINKS</span></span>

[<span data-ttu-id="cc0a6-166">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="cc0a6-166">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="cc0a6-167">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="cc0a6-167">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="cc0a6-168">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="cc0a6-168">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="cc0a6-169">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="cc0a6-169">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
