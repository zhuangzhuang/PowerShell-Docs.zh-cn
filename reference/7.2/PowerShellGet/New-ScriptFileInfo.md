---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: d3e3c0ec257bd9c405accaf3051abd1ae4501f0f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598699"
---
# <span data-ttu-id="93f70-102">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="93f70-102">New-ScriptFileInfo</span></span>

## <span data-ttu-id="93f70-103">摘要</span><span class="sxs-lookup"><span data-stu-id="93f70-103">SYNOPSIS</span></span>
<span data-ttu-id="93f70-104">使用元数据创建脚本文件。</span><span class="sxs-lookup"><span data-stu-id="93f70-104">Creates a script file with metadata.</span></span>

## <span data-ttu-id="93f70-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93f70-105">SYNTAX</span></span>

### <span data-ttu-id="93f70-106">全部</span><span class="sxs-lookup"><span data-stu-id="93f70-106">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="93f70-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="93f70-107">DESCRIPTION</span></span>

<span data-ttu-id="93f70-108">`New-ScriptFileInfo`Cmdlet 将创建一个 PowerShell 脚本文件，包括有关该脚本的元数据。</span><span class="sxs-lookup"><span data-stu-id="93f70-108">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="93f70-109">这些示例使用展开将参数传递给 `New-ScriptFileInfo` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93f70-109">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="93f70-110">有关详细信息，请参阅 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="93f70-110">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="93f70-111">示例</span><span class="sxs-lookup"><span data-stu-id="93f70-111">EXAMPLES</span></span>

### <span data-ttu-id="93f70-112">示例1：创建脚本文件并指定其版本、作者和说明</span><span class="sxs-lookup"><span data-stu-id="93f70-112">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="93f70-113">在此示例中，将创建一个脚本文件，并在 PowerShell 控制台中显示其内容。</span><span class="sxs-lookup"><span data-stu-id="93f70-113">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

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

.PRIVATEDATA

#>

<#

.DESCRIPTION
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="93f70-114">`New-ScriptFileInfo`Cmdlet 使用展开为脚本配置多个参数。</span><span class="sxs-lookup"><span data-stu-id="93f70-114">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="93f70-115">**路径** 设置脚本的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="93f70-115">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="93f70-116">**版本** 指定脚本的版本号。</span><span class="sxs-lookup"><span data-stu-id="93f70-116">**Version** specifies the script's version number.</span></span> <span data-ttu-id="93f70-117">**Author** 是创建脚本的人员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="93f70-117">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="93f70-118">**说明** 说明了该脚本的用途。</span><span class="sxs-lookup"><span data-stu-id="93f70-118">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="93f70-119">创建脚本后， `Get-Content` 使用 **Path** 参数查找该脚本。</span><span class="sxs-lookup"><span data-stu-id="93f70-119">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="93f70-120">该脚本的内容将显示在 PowerShell 控制台中。</span><span class="sxs-lookup"><span data-stu-id="93f70-120">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="93f70-121">示例2：测试脚本文件</span><span class="sxs-lookup"><span data-stu-id="93f70-121">Example 2: Test a script file</span></span>

<span data-ttu-id="93f70-122">在此示例中，对在 **示例 1** 中创建的脚本的元数据进行测试。</span><span class="sxs-lookup"><span data-stu-id="93f70-122">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="93f70-123">`Test-ScriptFileInfo`Cmdlet 使用 **Path** 参数指定脚本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="93f70-123">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="93f70-124">示例3：创建包含所有元数据属性的脚本文件</span><span class="sxs-lookup"><span data-stu-id="93f70-124">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="93f70-125">此示例使用展开创建一个名为的脚本文件 `New-ScriptFile.ps1` ，其中包含所有元数据属性。</span><span class="sxs-lookup"><span data-stu-id="93f70-125">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="93f70-126">**Verbose** 参数指定在创建脚本时显示详细输出。</span><span class="sxs-lookup"><span data-stu-id="93f70-126">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="93f70-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93f70-127">PARAMETERS</span></span>

### <span data-ttu-id="93f70-128">-作者</span><span class="sxs-lookup"><span data-stu-id="93f70-128">-Author</span></span>

<span data-ttu-id="93f70-129">指定脚本作者。</span><span class="sxs-lookup"><span data-stu-id="93f70-129">Specifies the script author.</span></span>

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

### <span data-ttu-id="93f70-130">-公司名称</span><span class="sxs-lookup"><span data-stu-id="93f70-130">-CompanyName</span></span>

<span data-ttu-id="93f70-131">指定创建脚本的公司或供应商。</span><span class="sxs-lookup"><span data-stu-id="93f70-131">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="93f70-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93f70-132">-Confirm</span></span>

<span data-ttu-id="93f70-133">提示你在运行之前进行确认 `New-ScriptFileInfo` 。</span><span class="sxs-lookup"><span data-stu-id="93f70-133">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="93f70-134">-版权所有</span><span class="sxs-lookup"><span data-stu-id="93f70-134">-Copyright</span></span>

<span data-ttu-id="93f70-135">指定脚本的版权声明。</span><span class="sxs-lookup"><span data-stu-id="93f70-135">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="93f70-136">-Description</span><span class="sxs-lookup"><span data-stu-id="93f70-136">-Description</span></span>

<span data-ttu-id="93f70-137">指定脚本的描述。</span><span class="sxs-lookup"><span data-stu-id="93f70-137">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93f70-138">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="93f70-138">-ExternalModuleDependencies</span></span>

<span data-ttu-id="93f70-139">指定外部模块依赖项的数组。</span><span class="sxs-lookup"><span data-stu-id="93f70-139">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="93f70-140">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="93f70-140">-ExternalScriptDependencies</span></span>

<span data-ttu-id="93f70-141">指定外部脚本依赖项的数组。</span><span class="sxs-lookup"><span data-stu-id="93f70-141">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="93f70-142">-Force</span><span class="sxs-lookup"><span data-stu-id="93f70-142">-Force</span></span>

<span data-ttu-id="93f70-143">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="93f70-143">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="93f70-144">-Guid</span><span class="sxs-lookup"><span data-stu-id="93f70-144">-Guid</span></span>

<span data-ttu-id="93f70-145">指定脚本的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="93f70-145">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="93f70-146">-IconUri</span><span class="sxs-lookup"><span data-stu-id="93f70-146">-IconUri</span></span>

<span data-ttu-id="93f70-147">指定脚本的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="93f70-147">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="93f70-148">指定的图标将显示在该脚本的库网页上。</span><span class="sxs-lookup"><span data-stu-id="93f70-148">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="93f70-149">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="93f70-149">-LicenseUri</span></span>

<span data-ttu-id="93f70-150">指定许可条款的 URL。</span><span class="sxs-lookup"><span data-stu-id="93f70-150">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="93f70-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="93f70-151">-PassThru</span></span>

<span data-ttu-id="93f70-152">返回一个对象，该对象表示正在处理的项。</span><span class="sxs-lookup"><span data-stu-id="93f70-152">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="93f70-153">默认情况下， `New-ScriptFileInfo` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="93f70-153">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="93f70-154">-Path</span><span class="sxs-lookup"><span data-stu-id="93f70-154">-Path</span></span>

<span data-ttu-id="93f70-155">指定保存脚本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="93f70-155">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93f70-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="93f70-156">-PrivateData</span></span>

<span data-ttu-id="93f70-157">指定脚本的专用数据。</span><span class="sxs-lookup"><span data-stu-id="93f70-157">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="93f70-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="93f70-158">-ProjectUri</span></span>

<span data-ttu-id="93f70-159">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="93f70-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="93f70-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="93f70-160">-ReleaseNotes</span></span>

<span data-ttu-id="93f70-161">指定一个字符串数组，其中包含此版本的脚本的用户要使用的发行说明或注释。</span><span class="sxs-lookup"><span data-stu-id="93f70-161">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="93f70-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="93f70-162">-RequiredModules</span></span>

<span data-ttu-id="93f70-163">指定必须处于全局会话状态的模块。</span><span class="sxs-lookup"><span data-stu-id="93f70-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="93f70-164">如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="93f70-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="93f70-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="93f70-165">-RequiredScripts</span></span>

<span data-ttu-id="93f70-166">指定所需脚本的数组。</span><span class="sxs-lookup"><span data-stu-id="93f70-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="93f70-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="93f70-167">-Tags</span></span>

<span data-ttu-id="93f70-168">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="93f70-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="93f70-169">-Version</span><span class="sxs-lookup"><span data-stu-id="93f70-169">-Version</span></span>

<span data-ttu-id="93f70-170">指定脚本的版本。</span><span class="sxs-lookup"><span data-stu-id="93f70-170">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="93f70-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93f70-171">-WhatIf</span></span>

<span data-ttu-id="93f70-172">显示运行时将发生 `New-ScriptFileInfo` 的情况。</span><span class="sxs-lookup"><span data-stu-id="93f70-172">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="93f70-173">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="93f70-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="93f70-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93f70-174">CommonParameters</span></span>

<span data-ttu-id="93f70-175">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="93f70-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93f70-176">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="93f70-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93f70-177">输入</span><span class="sxs-lookup"><span data-stu-id="93f70-177">INPUTS</span></span>

### <span data-ttu-id="93f70-178">System.String</span><span class="sxs-lookup"><span data-stu-id="93f70-178">System.String</span></span>

## <span data-ttu-id="93f70-179">输出</span><span class="sxs-lookup"><span data-stu-id="93f70-179">OUTPUTS</span></span>

### <span data-ttu-id="93f70-180">System.Object</span><span class="sxs-lookup"><span data-stu-id="93f70-180">System.Object</span></span>

## <span data-ttu-id="93f70-181">注释</span><span class="sxs-lookup"><span data-stu-id="93f70-181">NOTES</span></span>

## <span data-ttu-id="93f70-182">相关链接</span><span class="sxs-lookup"><span data-stu-id="93f70-182">RELATED LINKS</span></span>

[<span data-ttu-id="93f70-183">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="93f70-183">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="93f70-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="93f70-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="93f70-185">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="93f70-185">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

