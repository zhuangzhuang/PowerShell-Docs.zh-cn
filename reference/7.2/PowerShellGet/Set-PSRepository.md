---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: d6f3901ba389ff910dcc808d2e4296032617052c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597036"
---
# <span data-ttu-id="702fc-102">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="702fc-102">Set-PSRepository</span></span>

## <span data-ttu-id="702fc-103">摘要</span><span class="sxs-lookup"><span data-stu-id="702fc-103">SYNOPSIS</span></span>
<span data-ttu-id="702fc-104">为已注册的存储库设置值。</span><span class="sxs-lookup"><span data-stu-id="702fc-104">Sets values for a registered repository.</span></span>

## <span data-ttu-id="702fc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="702fc-105">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="702fc-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="702fc-106">DESCRIPTION</span></span>

<span data-ttu-id="702fc-107">`Set-PSRepository`Cmdlet 为已注册的模块存储库设置值。</span><span class="sxs-lookup"><span data-stu-id="702fc-107">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="702fc-108">这些设置对于当前用户是永久性的，适用于为该用户安装的所有版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="702fc-108">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="702fc-109">示例</span><span class="sxs-lookup"><span data-stu-id="702fc-109">EXAMPLES</span></span>

### <span data-ttu-id="702fc-110">示例1：设置存储库的安装策略</span><span class="sxs-lookup"><span data-stu-id="702fc-110">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="702fc-111">此命令将 **myInternalSource** 存储库的安装策略设置为 " **受信任**"，以便在从此源安装模块之前不会进行提示。</span><span class="sxs-lookup"><span data-stu-id="702fc-111">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="702fc-112">示例2：设置存储库的源位置和发布位置</span><span class="sxs-lookup"><span data-stu-id="702fc-112">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="702fc-113">此命令将 **myInternalSource** 的源位置和发布位置设置为指定的 uri。</span><span class="sxs-lookup"><span data-stu-id="702fc-113">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="702fc-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="702fc-114">PARAMETERS</span></span>

### <span data-ttu-id="702fc-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="702fc-115">-Credential</span></span>

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

### <span data-ttu-id="702fc-116">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="702fc-116">-InstallationPolicy</span></span>

<span data-ttu-id="702fc-117">指定安装策略。</span><span class="sxs-lookup"><span data-stu-id="702fc-117">Specifies the installation policy.</span></span> <span data-ttu-id="702fc-118">有效值为： **可信**、 **不受** 信任。</span><span class="sxs-lookup"><span data-stu-id="702fc-118">Valid values are: **Trusted**, **Untrusted**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="702fc-119">-Name</span><span class="sxs-lookup"><span data-stu-id="702fc-119">-Name</span></span>

<span data-ttu-id="702fc-120">指定存储库的名称。</span><span class="sxs-lookup"><span data-stu-id="702fc-120">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="702fc-121">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="702fc-121">-PackageManagementProvider</span></span>

<span data-ttu-id="702fc-122">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="702fc-122">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="702fc-123">-Proxy</span><span class="sxs-lookup"><span data-stu-id="702fc-123">-Proxy</span></span>

<span data-ttu-id="702fc-124">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="702fc-124">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="702fc-125">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="702fc-125">-ProxyCredential</span></span>

<span data-ttu-id="702fc-126">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="702fc-126">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="702fc-127">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="702fc-127">-PublishLocation</span></span>

<span data-ttu-id="702fc-128">指定发布位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="702fc-128">Specifies the URI of the publish location.</span></span> <span data-ttu-id="702fc-129">例如，对于基于 NuGet 的存储库，发布位置类似于 `https://someNuGetUrl.com/api/v2/Packages` 。</span><span class="sxs-lookup"><span data-stu-id="702fc-129">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="702fc-130">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="702fc-130">-ScriptPublishLocation</span></span>

<span data-ttu-id="702fc-131">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="702fc-131">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="702fc-132">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="702fc-132">-ScriptSourceLocation</span></span>

<span data-ttu-id="702fc-133">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="702fc-133">Specifies the script source location.</span></span>

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

### <span data-ttu-id="702fc-134">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="702fc-134">-SourceLocation</span></span>

<span data-ttu-id="702fc-135">指定用于发现和安装此存储库中的模块的 URI。</span><span class="sxs-lookup"><span data-stu-id="702fc-135">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="702fc-136">例如，对于基于 NuGet 的存储库，源位置类似于 `https://someNuGetUrl.com/api/v2` 。</span><span class="sxs-lookup"><span data-stu-id="702fc-136">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="702fc-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="702fc-137">CommonParameters</span></span>

<span data-ttu-id="702fc-138">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="702fc-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="702fc-139">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="702fc-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="702fc-140">输入</span><span class="sxs-lookup"><span data-stu-id="702fc-140">INPUTS</span></span>

### <span data-ttu-id="702fc-141">System.String</span><span class="sxs-lookup"><span data-stu-id="702fc-141">System.String</span></span>

### <span data-ttu-id="702fc-142">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="702fc-142">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="702fc-143">System.Uri</span><span class="sxs-lookup"><span data-stu-id="702fc-143">System.Uri</span></span>

## <span data-ttu-id="702fc-144">输出</span><span class="sxs-lookup"><span data-stu-id="702fc-144">OUTPUTS</span></span>

### <span data-ttu-id="702fc-145">System.Object</span><span class="sxs-lookup"><span data-stu-id="702fc-145">System.Object</span></span>

## <span data-ttu-id="702fc-146">注释</span><span class="sxs-lookup"><span data-stu-id="702fc-146">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="702fc-147">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="702fc-147">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="702fc-148">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="702fc-148">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="702fc-149">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="702fc-149">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="702fc-150">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="702fc-150">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="702fc-151">相关链接</span><span class="sxs-lookup"><span data-stu-id="702fc-151">RELATED LINKS</span></span>

[<span data-ttu-id="702fc-152">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="702fc-152">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="702fc-153">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="702fc-153">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="702fc-154">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="702fc-154">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
