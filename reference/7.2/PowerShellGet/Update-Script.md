---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 0fa537e463464fe055ea14aeab05cbb3ac5d1012
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603382"
---
# <span data-ttu-id="bd2e4-102">Update-Script</span><span class="sxs-lookup"><span data-stu-id="bd2e4-102">Update-Script</span></span>

## <span data-ttu-id="bd2e4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="bd2e4-103">SYNOPSIS</span></span>
<span data-ttu-id="bd2e4-104">更新脚本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-104">Updates a script.</span></span>

## <span data-ttu-id="bd2e4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd2e4-105">SYNTAX</span></span>

### <span data-ttu-id="bd2e4-106">全部</span><span class="sxs-lookup"><span data-stu-id="bd2e4-106">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bd2e4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bd2e4-107">DESCRIPTION</span></span>

<span data-ttu-id="bd2e4-108">`Update-Script`Cmdlet 可更新安装在本地计算机上的脚本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-108">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="bd2e4-109">已更新的脚本将从与安装的版本相同的存储库中下载。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-109">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="bd2e4-110">示例</span><span class="sxs-lookup"><span data-stu-id="bd2e4-110">EXAMPLES</span></span>

### <span data-ttu-id="bd2e4-111">示例1：更新指定的脚本</span><span class="sxs-lookup"><span data-stu-id="bd2e4-111">Example 1: Update the specified script</span></span>

<span data-ttu-id="bd2e4-112">此示例将更新已安装的脚本，并显示更新后的版本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-112">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="bd2e4-113">`Update-Script` 使用 **Name** 参数来指定要更新的脚本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-113">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="bd2e4-114">**RequiredVersion** 参数指定脚本版本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-114">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="bd2e4-115">`Get-InstalledScript` 显示脚本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-115">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="bd2e4-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd2e4-116">PARAMETERS</span></span>

### <span data-ttu-id="bd2e4-117">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="bd2e4-117">-AcceptLicense</span></span>

<span data-ttu-id="bd2e4-118">如果包需要许可协议，则在安装过程中自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-118">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="bd2e4-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="bd2e4-119">-AllowPrerelease</span></span>

<span data-ttu-id="bd2e4-120">允许使用标记为预发行版本的更新脚本来更新脚本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-120">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="bd2e4-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bd2e4-121">-Confirm</span></span>

<span data-ttu-id="bd2e4-122">在运行之前提示你进行确认 `Update-Script` 。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-122">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="bd2e4-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="bd2e4-123">-Credential</span></span>

<span data-ttu-id="bd2e4-124">指定有权更新脚本的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-124">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="bd2e4-125">-Force</span><span class="sxs-lookup"><span data-stu-id="bd2e4-125">-Force</span></span>

<span data-ttu-id="bd2e4-126">强制 `Update-Script` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-126">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="bd2e4-127">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="bd2e4-127">-MaximumVersion</span></span>

<span data-ttu-id="bd2e4-128">指定要更新的最大或最新版本的脚本。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-128">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="bd2e4-129">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-129">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="bd2e4-130">-Name</span><span class="sxs-lookup"><span data-stu-id="bd2e4-130">-Name</span></span>

<span data-ttu-id="bd2e4-131">指定一个脚本名称或要更新的脚本名称数组。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-131">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="bd2e4-132">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bd2e4-132">-PassThru</span></span>

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

### <span data-ttu-id="bd2e4-133">-Proxy</span><span class="sxs-lookup"><span data-stu-id="bd2e4-133">-Proxy</span></span>

<span data-ttu-id="bd2e4-134">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-134">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="bd2e4-135">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="bd2e4-135">-ProxyCredential</span></span>

<span data-ttu-id="bd2e4-136">指定有权使用 **代理** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-136">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="bd2e4-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bd2e4-137">-RequiredVersion</span></span>

<span data-ttu-id="bd2e4-138">指定要更新的脚本的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-138">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="bd2e4-139">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-139">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="bd2e4-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bd2e4-140">-WhatIf</span></span>

<span data-ttu-id="bd2e4-141">显示运行时将发生 `Update-Script` 的情况。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-141">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="bd2e4-142">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-142">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="bd2e4-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd2e4-143">CommonParameters</span></span>

<span data-ttu-id="bd2e4-144">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd2e4-145">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd2e4-146">输入</span><span class="sxs-lookup"><span data-stu-id="bd2e4-146">INPUTS</span></span>

### <span data-ttu-id="bd2e4-147">System.String[]</span><span class="sxs-lookup"><span data-stu-id="bd2e4-147">System.String[]</span></span>

### <span data-ttu-id="bd2e4-148">System.String</span><span class="sxs-lookup"><span data-stu-id="bd2e4-148">System.String</span></span>

### <span data-ttu-id="bd2e4-149">System.Uri</span><span class="sxs-lookup"><span data-stu-id="bd2e4-149">System.Uri</span></span>

### <span data-ttu-id="bd2e4-150">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="bd2e4-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="bd2e4-151">输出</span><span class="sxs-lookup"><span data-stu-id="bd2e4-151">OUTPUTS</span></span>

### <span data-ttu-id="bd2e4-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="bd2e4-152">System.Object</span></span>

## <span data-ttu-id="bd2e4-153">注释</span><span class="sxs-lookup"><span data-stu-id="bd2e4-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd2e4-154">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="bd2e4-155">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="bd2e4-156">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="bd2e4-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="bd2e4-157">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="bd2e4-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="bd2e4-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="bd2e4-158">RELATED LINKS</span></span>

[<span data-ttu-id="bd2e4-159">Find-Script</span><span class="sxs-lookup"><span data-stu-id="bd2e4-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="bd2e4-160">Install-Script</span><span class="sxs-lookup"><span data-stu-id="bd2e4-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="bd2e4-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="bd2e4-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="bd2e4-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="bd2e4-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="bd2e4-163">卸载-脚本</span><span class="sxs-lookup"><span data-stu-id="bd2e4-163">Uninstall-Script</span></span>](Uninstall-Script.md)
