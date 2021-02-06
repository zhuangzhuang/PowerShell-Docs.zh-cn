---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: de138a27ed9425057406dc6120a8354b72a3b8a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597894"
---
# <span data-ttu-id="0d9a2-102">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d9a2-102">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="0d9a2-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0d9a2-103">SYNOPSIS</span></span>
<span data-ttu-id="0d9a2-104">更新脚本的信息。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-104">Updates information for a script.</span></span>

## <span data-ttu-id="0d9a2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0d9a2-105">SYNTAX</span></span>

### <span data-ttu-id="0d9a2-106">PathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="0d9a2-106">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0d9a2-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="0d9a2-107">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0d9a2-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0d9a2-108">DESCRIPTION</span></span>

<span data-ttu-id="0d9a2-109">`Update-ScriptFileInfo`Cmdlet 将更新脚本的属性值。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-109">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="0d9a2-110">例如，"版本"、"作者" 或 "说明" 的值。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-110">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="0d9a2-111">示例</span><span class="sxs-lookup"><span data-stu-id="0d9a2-111">EXAMPLES</span></span>

### <span data-ttu-id="0d9a2-112">示例1：更新脚本文件的版本</span><span class="sxs-lookup"><span data-stu-id="0d9a2-112">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="0d9a2-113">在此示例中，使用新属性值更新现有脚本文件。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-113">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="0d9a2-114">展开用于将参数传递给 `Update-ScriptFileInfo` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-114">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="0d9a2-115">有关详细信息，请参阅 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-115">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

<span data-ttu-id="0d9a2-116">`$Parms` 存储 **路径**、 **版本**、 **作者**、 **公司名称** 和 **说明** 的参数值。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-116">`$Parms` stores the parameter values for **Path**, **Version**, **Author**, **CompanyName**, and **Description**.</span></span> <span data-ttu-id="0d9a2-117">`Update-ScriptFileInfo` 从获取参数值 `@Parms` ，并更新脚本。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-117">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="0d9a2-118">**PassThru** 参数显示 PowerShell 控制台中的脚本内容。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-118">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="0d9a2-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d9a2-119">PARAMETERS</span></span>

### <span data-ttu-id="0d9a2-120">-作者</span><span class="sxs-lookup"><span data-stu-id="0d9a2-120">-Author</span></span>

<span data-ttu-id="0d9a2-121">指定脚本作者。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-121">Specifies the script author.</span></span>

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

### <span data-ttu-id="0d9a2-122">-公司名称</span><span class="sxs-lookup"><span data-stu-id="0d9a2-122">-CompanyName</span></span>

<span data-ttu-id="0d9a2-123">指定创建脚本的公司或供应商。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-123">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="0d9a2-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0d9a2-124">-Confirm</span></span>

<span data-ttu-id="0d9a2-125">在运行之前提示你进行确认 `Update-ScriptFileInfo` 。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-125">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="0d9a2-126">-版权所有</span><span class="sxs-lookup"><span data-stu-id="0d9a2-126">-Copyright</span></span>

<span data-ttu-id="0d9a2-127">指定脚本的版权声明。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-127">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="0d9a2-128">-Description</span><span class="sxs-lookup"><span data-stu-id="0d9a2-128">-Description</span></span>

<span data-ttu-id="0d9a2-129">指定脚本的描述。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-129">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="0d9a2-130">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="0d9a2-130">-ExternalModuleDependencies</span></span>

<span data-ttu-id="0d9a2-131">指定外部模块依赖项的数组。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-131">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="0d9a2-132">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="0d9a2-132">-ExternalScriptDependencies</span></span>

<span data-ttu-id="0d9a2-133">指定外部脚本依赖项的数组。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-133">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="0d9a2-134">-Force</span><span class="sxs-lookup"><span data-stu-id="0d9a2-134">-Force</span></span>

<span data-ttu-id="0d9a2-135">强制 `Update-ScriptFileInfo` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-135">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0d9a2-136">-Guid</span><span class="sxs-lookup"><span data-stu-id="0d9a2-136">-Guid</span></span>

<span data-ttu-id="0d9a2-137">指定脚本的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-137">Specifies a unique ID for a script.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d9a2-138">-IconUri</span><span class="sxs-lookup"><span data-stu-id="0d9a2-138">-IconUri</span></span>

<span data-ttu-id="0d9a2-139">指定脚本的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-139">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="0d9a2-140">指定的图标将显示在该脚本的库网页上。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-140">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="0d9a2-141">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="0d9a2-141">-LicenseUri</span></span>

<span data-ttu-id="0d9a2-142">指定许可条款的 URL。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-142">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="0d9a2-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0d9a2-143">-LiteralPath</span></span>

<span data-ttu-id="0d9a2-144">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0d9a2-145">**LiteralPath** 参数的值完全按输入方式使用。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-145">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="0d9a2-146">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0d9a2-147">如果路径包含转义符，请将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-147">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="0d9a2-148">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d9a2-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0d9a2-149">-PassThru</span></span>

<span data-ttu-id="0d9a2-150">返回一个对象，该对象表示正在处理的项。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-150">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="0d9a2-151">默认情况下， `Update-ScriptFileInfo` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-151">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="0d9a2-152">-Path</span><span class="sxs-lookup"><span data-stu-id="0d9a2-152">-Path</span></span>

<span data-ttu-id="0d9a2-153">指定脚本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-153">Specifies the script file's location.</span></span> <span data-ttu-id="0d9a2-154">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-154">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0d9a2-155">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="0d9a2-155">-PrivateData</span></span>

<span data-ttu-id="0d9a2-156">指定脚本的专用数据。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-156">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="0d9a2-157">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="0d9a2-157">-ProjectUri</span></span>

<span data-ttu-id="0d9a2-158">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-158">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="0d9a2-159">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="0d9a2-159">-ReleaseNotes</span></span>

<span data-ttu-id="0d9a2-160">指定一个字符串数组，其中包含要用于此版本的脚本的发行说明或注释。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-160">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="0d9a2-161">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="0d9a2-161">-RequiredModules</span></span>

<span data-ttu-id="0d9a2-162">指定必须处于全局会话状态的模块。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-162">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="0d9a2-163">如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-163">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d9a2-164">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="0d9a2-164">-RequiredScripts</span></span>

<span data-ttu-id="0d9a2-165">指定所需脚本的数组。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-165">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="0d9a2-166">-Tags</span><span class="sxs-lookup"><span data-stu-id="0d9a2-166">-Tags</span></span>

<span data-ttu-id="0d9a2-167">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-167">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="0d9a2-168">-Version</span><span class="sxs-lookup"><span data-stu-id="0d9a2-168">-Version</span></span>

<span data-ttu-id="0d9a2-169">指定脚本的版本。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-169">Specifies the script's version.</span></span>

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

### <span data-ttu-id="0d9a2-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0d9a2-170">-WhatIf</span></span>

<span data-ttu-id="0d9a2-171">显示运行时将发生 `Update-ScriptFileInfo` 的情况。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-171">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="0d9a2-172">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-172">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0d9a2-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d9a2-173">CommonParameters</span></span>

<span data-ttu-id="0d9a2-174">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0d9a2-175">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0d9a2-176">输入</span><span class="sxs-lookup"><span data-stu-id="0d9a2-176">INPUTS</span></span>

### <span data-ttu-id="0d9a2-177">System.String</span><span class="sxs-lookup"><span data-stu-id="0d9a2-177">System.String</span></span>

## <span data-ttu-id="0d9a2-178">输出</span><span class="sxs-lookup"><span data-stu-id="0d9a2-178">OUTPUTS</span></span>

### <span data-ttu-id="0d9a2-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="0d9a2-179">System.Object</span></span>

## <span data-ttu-id="0d9a2-180">注释</span><span class="sxs-lookup"><span data-stu-id="0d9a2-180">NOTES</span></span>

<span data-ttu-id="0d9a2-181">使用 `Test-ScriptFileInfo` cmdlet 验证脚本的元数据。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-181">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="0d9a2-182">脚本必须包含版本、GUID、说明和作者的值。</span><span class="sxs-lookup"><span data-stu-id="0d9a2-182">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="0d9a2-183">相关链接</span><span class="sxs-lookup"><span data-stu-id="0d9a2-183">RELATED LINKS</span></span>

[<span data-ttu-id="0d9a2-184">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d9a2-184">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="0d9a2-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d9a2-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

