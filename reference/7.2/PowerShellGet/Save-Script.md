---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 2f672cbb814b0641411bb11ffb17bd1ecef96dda
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603574"
---
# <span data-ttu-id="c485f-102">Save-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-102">Save-Script</span></span>

## <span data-ttu-id="c485f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c485f-103">SYNOPSIS</span></span>
<span data-ttu-id="c485f-104">保存脚本。</span><span class="sxs-lookup"><span data-stu-id="c485f-104">Saves a script.</span></span>

## <span data-ttu-id="c485f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c485f-105">SYNTAX</span></span>

### <span data-ttu-id="c485f-106">NameAndPathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="c485f-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c485f-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c485f-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c485f-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c485f-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c485f-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c485f-109">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c485f-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c485f-110">DESCRIPTION</span></span>

<span data-ttu-id="c485f-111">`Save-Script`Cmdlet 将保存指定的脚本。</span><span class="sxs-lookup"><span data-stu-id="c485f-111">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="c485f-112">示例</span><span class="sxs-lookup"><span data-stu-id="c485f-112">EXAMPLES</span></span>

### <span data-ttu-id="c485f-113">示例1：保存脚本并验证脚本的元数据</span><span class="sxs-lookup"><span data-stu-id="c485f-113">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="c485f-114">在此示例中，存储库中的脚本保存到本地计算机，并验证脚本的元数据。</span><span class="sxs-lookup"><span data-stu-id="c485f-114">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="c485f-115">`Save-Script` 使用 **Name** 参数来指定脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="c485f-115">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="c485f-116">**存储库** 参数指定要查找脚本的位置。</span><span class="sxs-lookup"><span data-stu-id="c485f-116">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="c485f-117">脚本保存在 **Path** 参数指定的位置。</span><span class="sxs-lookup"><span data-stu-id="c485f-117">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="c485f-118">`Test-ScriptFileInfo` 指定 **路径** 并验证脚本的元数据。</span><span class="sxs-lookup"><span data-stu-id="c485f-118">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="c485f-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c485f-119">PARAMETERS</span></span>

### <span data-ttu-id="c485f-120">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c485f-120">-AcceptLicense</span></span>

<span data-ttu-id="c485f-121">如果脚本需要许可协议，则自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="c485f-121">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="c485f-122">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c485f-122">-AllowPrerelease</span></span>

<span data-ttu-id="c485f-123">允许您保存标记为预发行版的脚本。</span><span class="sxs-lookup"><span data-stu-id="c485f-123">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c485f-124">-Confirm</span></span>

<span data-ttu-id="c485f-125">在运行之前提示你进行确认 `Save-Script` 。</span><span class="sxs-lookup"><span data-stu-id="c485f-125">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="c485f-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="c485f-126">-Credential</span></span>

<span data-ttu-id="c485f-127">指定有权保存脚本的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c485f-127">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="c485f-128">-Force</span><span class="sxs-lookup"><span data-stu-id="c485f-128">-Force</span></span>

<span data-ttu-id="c485f-129">强制 `Save-Script` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="c485f-129">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c485f-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c485f-130">-InputObject</span></span>

<span data-ttu-id="c485f-131">接受 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="c485f-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="c485f-132">例如，输出 `Find-Script` 到变量，并将该变量用作 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="c485f-132">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c485f-133">-LiteralPath</span></span>

<span data-ttu-id="c485f-134">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="c485f-134">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c485f-135">**LiteralPath** 参数的值完全按输入方式使用。</span><span class="sxs-lookup"><span data-stu-id="c485f-135">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="c485f-136">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="c485f-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c485f-137">如果路径中包含转义符，请将路径用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="c485f-137">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="c485f-138">PowerShell 不会将括在单引号中的任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="c485f-138">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-139">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c485f-139">-MaximumVersion</span></span>

<span data-ttu-id="c485f-140">指定要保存的最大或最新版本的脚本。</span><span class="sxs-lookup"><span data-stu-id="c485f-140">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="c485f-141">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="c485f-141">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-142">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c485f-142">-MinimumVersion</span></span>

<span data-ttu-id="c485f-143">指定要保存的脚本的最低版本。</span><span class="sxs-lookup"><span data-stu-id="c485f-143">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="c485f-144">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="c485f-144">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-145">-Name</span><span class="sxs-lookup"><span data-stu-id="c485f-145">-Name</span></span>

<span data-ttu-id="c485f-146">指定要保存的脚本名称的数组。</span><span class="sxs-lookup"><span data-stu-id="c485f-146">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-147">-Path</span><span class="sxs-lookup"><span data-stu-id="c485f-147">-Path</span></span>

<span data-ttu-id="c485f-148">指定本地计算机上存储已保存模块的位置。</span><span class="sxs-lookup"><span data-stu-id="c485f-148">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="c485f-149">接受通配符。</span><span class="sxs-lookup"><span data-stu-id="c485f-149">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c485f-150">-Proxy</span><span class="sxs-lookup"><span data-stu-id="c485f-150">-Proxy</span></span>

<span data-ttu-id="c485f-151">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="c485f-151">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="c485f-152">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="c485f-152">-ProxyCredential</span></span>

<span data-ttu-id="c485f-153">指定有权使用 **代理** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c485f-153">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="c485f-154">-Repository</span><span class="sxs-lookup"><span data-stu-id="c485f-154">-Repository</span></span>

<span data-ttu-id="c485f-155">指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="c485f-155">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="c485f-156">用于 `Get-PSRepository` 显示已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="c485f-156">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-157">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c485f-157">-RequiredVersion</span></span>

<span data-ttu-id="c485f-158">指定要保存的脚本的准确版本号。</span><span class="sxs-lookup"><span data-stu-id="c485f-158">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c485f-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c485f-159">-WhatIf</span></span>

<span data-ttu-id="c485f-160">显示运行时将发生 `Save-Script` 的情况。</span><span class="sxs-lookup"><span data-stu-id="c485f-160">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="c485f-161">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="c485f-161">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c485f-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c485f-162">CommonParameters</span></span>

<span data-ttu-id="c485f-163">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c485f-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c485f-164">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c485f-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c485f-165">输入</span><span class="sxs-lookup"><span data-stu-id="c485f-165">INPUTS</span></span>

### <span data-ttu-id="c485f-166">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c485f-166">System.String[]</span></span>

### <span data-ttu-id="c485f-167">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="c485f-167">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="c485f-168">System.String</span><span class="sxs-lookup"><span data-stu-id="c485f-168">System.String</span></span>

### <span data-ttu-id="c485f-169">System.Uri</span><span class="sxs-lookup"><span data-stu-id="c485f-169">System.Uri</span></span>

### <span data-ttu-id="c485f-170">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="c485f-170">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="c485f-171">输出</span><span class="sxs-lookup"><span data-stu-id="c485f-171">OUTPUTS</span></span>

### <span data-ttu-id="c485f-172">System.Object</span><span class="sxs-lookup"><span data-stu-id="c485f-172">System.Object</span></span>

## <span data-ttu-id="c485f-173">注释</span><span class="sxs-lookup"><span data-stu-id="c485f-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c485f-174">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="c485f-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="c485f-175">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="c485f-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="c485f-176">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="c485f-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="c485f-177">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="c485f-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="c485f-178">相关链接</span><span class="sxs-lookup"><span data-stu-id="c485f-178">RELATED LINKS</span></span>

[<span data-ttu-id="c485f-179">Find-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-179">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="c485f-180">Install-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-180">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="c485f-181">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-181">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="c485f-182">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="c485f-182">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="c485f-183">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-183">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="c485f-184">Update-Script</span><span class="sxs-lookup"><span data-stu-id="c485f-184">Update-Script</span></span>](Update-Script.md)
