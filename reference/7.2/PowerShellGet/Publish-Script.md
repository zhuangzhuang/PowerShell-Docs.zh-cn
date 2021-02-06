---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 344a789c9daced51b549d562b7fd74677fe403dc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598668"
---
# <span data-ttu-id="0a045-102">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-102">Publish-Script</span></span>

## <span data-ttu-id="0a045-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0a045-103">SYNOPSIS</span></span>
<span data-ttu-id="0a045-104">发布脚本。</span><span class="sxs-lookup"><span data-stu-id="0a045-104">Publishes a script.</span></span>

## <span data-ttu-id="0a045-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a045-105">SYNTAX</span></span>

### <span data-ttu-id="0a045-106">PathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="0a045-106">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0a045-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="0a045-107">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0a045-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0a045-108">DESCRIPTION</span></span>

<span data-ttu-id="0a045-109">`Publish-Script`Cmdlet 可将指定的脚本发布到联机库。</span><span class="sxs-lookup"><span data-stu-id="0a045-109">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="0a045-110">示例</span><span class="sxs-lookup"><span data-stu-id="0a045-110">EXAMPLES</span></span>

### <span data-ttu-id="0a045-111">示例1：创建一个脚本文件，向其中添加内容并将其发布</span><span class="sxs-lookup"><span data-stu-id="0a045-111">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="0a045-112">`New-ScriptFileInfo`Cmdlet 将创建一个名为的脚本文件 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="0a045-112">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="0a045-113">`Get-Content` 显示的内容 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="0a045-113">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="0a045-114">`Add-Content`Cmdlet 可向添加函数和工作流 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="0a045-114">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="0a045-115">Cmdlet 将进行 `Test-ScriptFileInfo` 验证 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="0a045-115">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="0a045-116">`Publish-Script`Cmdlet 将脚本发布到 **LocalRepo1** 存储库。</span><span class="sxs-lookup"><span data-stu-id="0a045-116">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="0a045-117">最后，</span><span class="sxs-lookup"><span data-stu-id="0a045-117">Finally.</span></span> <span data-ttu-id="0a045-118">`Find-Script` 用于 `Demo-Script.ps1` 在 **LocalRepo1** 存储库中搜索。</span><span class="sxs-lookup"><span data-stu-id="0a045-118">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="0a045-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a045-119">PARAMETERS</span></span>

### <span data-ttu-id="0a045-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0a045-120">-Confirm</span></span>

<span data-ttu-id="0a045-121">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="0a045-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0a045-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="0a045-122">-Credential</span></span>

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

### <span data-ttu-id="0a045-123">-Force</span><span class="sxs-lookup"><span data-stu-id="0a045-123">-Force</span></span>

<span data-ttu-id="0a045-124">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="0a045-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0a045-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0a045-125">-LiteralPath</span></span>

<span data-ttu-id="0a045-126">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="0a045-126">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0a045-127">与 **Path** 参数不同， **LiteralPath** 参数的值完全按输入方式使用。</span><span class="sxs-lookup"><span data-stu-id="0a045-127">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="0a045-128">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="0a045-128">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0a045-129">如果路径包含转义符，请将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="0a045-129">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="0a045-130">单引号会告知 Windows PowerShell 不要将所有字符都解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="0a045-130">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0a045-131">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="0a045-131">-NuGetApiKey</span></span>

<span data-ttu-id="0a045-132">指定要用于将脚本发布到联机库的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="0a045-132">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="0a045-133">API 密钥是你的个人资料中的配置文件的一部分。</span><span class="sxs-lookup"><span data-stu-id="0a045-133">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="0a045-134">有关详细信息，请参阅 [管理 API 密钥](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)。</span><span class="sxs-lookup"><span data-stu-id="0a045-134">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="0a045-135">-Path</span><span class="sxs-lookup"><span data-stu-id="0a045-135">-Path</span></span>

<span data-ttu-id="0a045-136">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="0a045-136">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0a045-137">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="0a045-137">Wildcards are permitted.</span></span> <span data-ttu-id="0a045-138">默认位置为当前目录。</span><span class="sxs-lookup"><span data-stu-id="0a045-138">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0a045-139">-Repository</span><span class="sxs-lookup"><span data-stu-id="0a045-139">-Repository</span></span>

<span data-ttu-id="0a045-140">指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="0a045-140">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="0a045-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0a045-141">-WhatIf</span></span>

<span data-ttu-id="0a045-142">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="0a045-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0a045-143">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="0a045-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0a045-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a045-144">CommonParameters</span></span>

<span data-ttu-id="0a045-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0a045-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a045-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0a045-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a045-147">输入</span><span class="sxs-lookup"><span data-stu-id="0a045-147">INPUTS</span></span>

### <span data-ttu-id="0a045-148">System.String</span><span class="sxs-lookup"><span data-stu-id="0a045-148">System.String</span></span>

### <span data-ttu-id="0a045-149">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="0a045-149">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="0a045-150">输出</span><span class="sxs-lookup"><span data-stu-id="0a045-150">OUTPUTS</span></span>

### <span data-ttu-id="0a045-151">System.Object</span><span class="sxs-lookup"><span data-stu-id="0a045-151">System.Object</span></span>

## <span data-ttu-id="0a045-152">注释</span><span class="sxs-lookup"><span data-stu-id="0a045-152">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a045-153">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="0a045-153">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0a045-154">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="0a045-154">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0a045-155">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="0a045-155">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0a045-156">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="0a045-156">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0a045-157">相关链接</span><span class="sxs-lookup"><span data-stu-id="0a045-157">RELATED LINKS</span></span>

[<span data-ttu-id="0a045-158">Find-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-158">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="0a045-159">Install-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-159">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0a045-160">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-160">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0a045-161">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-161">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0a045-162">Update-Script</span><span class="sxs-lookup"><span data-stu-id="0a045-162">Update-Script</span></span>](Update-Script.md)
