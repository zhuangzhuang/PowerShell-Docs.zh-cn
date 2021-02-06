---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 2edc05ff660cfcca232af878c593c29de68eb122
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597263"
---
# <span data-ttu-id="5f235-102">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="5f235-102">Publish-Module</span></span>

## <span data-ttu-id="5f235-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5f235-103">SYNOPSIS</span></span>
<span data-ttu-id="5f235-104">将指定模块从本机计算机发布到联机库。</span><span class="sxs-lookup"><span data-stu-id="5f235-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="5f235-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f235-105">SYNTAX</span></span>

### <span data-ttu-id="5f235-106">ModuleNameParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="5f235-106">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5f235-107">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="5f235-107">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5f235-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5f235-108">DESCRIPTION</span></span>

<span data-ttu-id="5f235-109">该 `Publish-Module` cmdlet 通过使用 API 密钥（存储在库中的用户配置文件的一部分），将模块发布到基于 NuGet 的联机库。</span><span class="sxs-lookup"><span data-stu-id="5f235-109">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="5f235-110">可根据模块的名称或包含模块的文件夹路径指定要发布的模块。</span><span class="sxs-lookup"><span data-stu-id="5f235-110">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="5f235-111">按名称指定模块时，将 `Publish-Module` 发布通过运行找到的第一个模块 `Get-Module -ListAvailable <Name>` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-111">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="5f235-112">如果您指定要发布的模块的最低版本，将 `Publish-Module` 发布第一个版本大于或等于您指定的最低版本的模块。</span><span class="sxs-lookup"><span data-stu-id="5f235-112">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="5f235-113">发布模块需要在库页面显示的模块的元数据。</span><span class="sxs-lookup"><span data-stu-id="5f235-113">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="5f235-114">所需元数据包括模块名称、版本、说明和作者。</span><span class="sxs-lookup"><span data-stu-id="5f235-114">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="5f235-115">尽管大多数元数据都是从模块清单获取的，但必须在参数中指定某些元数据（如 `Publish-Module` **标记**、 **ReleaseNote**、 **IconUri**、 **ProjectUri** 和 **LicenseUri**），因为这些参数与基于 NuGet 的库中的字段匹配。</span><span class="sxs-lookup"><span data-stu-id="5f235-115">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**, because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="5f235-116">示例</span><span class="sxs-lookup"><span data-stu-id="5f235-116">EXAMPLES</span></span>

### <span data-ttu-id="5f235-117">示例1：发布模块</span><span class="sxs-lookup"><span data-stu-id="5f235-117">Example 1: Publish a module</span></span>

<span data-ttu-id="5f235-118">在此示例中，使用 API 密钥将 MyDscModule 发布到联机库，以指示模块所有者的联机库帐户。</span><span class="sxs-lookup"><span data-stu-id="5f235-118">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="5f235-119">如果 MyDscModule 不是指定名称、版本、说明和作者的有效清单模块，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="5f235-119">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="5f235-120">示例2：使用库元数据发布模块</span><span class="sxs-lookup"><span data-stu-id="5f235-120">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="5f235-121">在此示例中，使用 API 密钥将 MyDscModule 发布到联机库，以指示模块所有者的库帐户。</span><span class="sxs-lookup"><span data-stu-id="5f235-121">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="5f235-122">提供的其他元数据将显示在库中模块的网页上。</span><span class="sxs-lookup"><span data-stu-id="5f235-122">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="5f235-123">所有者添加了两个用于模块的搜索标记，并将其与 Active Directory 相关联。已添加简短的发行说明。</span><span class="sxs-lookup"><span data-stu-id="5f235-123">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="5f235-124">如果 MyDscModule 不是指定名称、版本、说明和作者的有效清单模块，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="5f235-124">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="5f235-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f235-125">PARAMETERS</span></span>

### <span data-ttu-id="5f235-126">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5f235-126">-AllowPrerelease</span></span>

<span data-ttu-id="5f235-127">允许发布标记为预发行的模块。</span><span class="sxs-lookup"><span data-stu-id="5f235-127">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f235-128">-Confirm</span></span>

<span data-ttu-id="5f235-129">提示你在运行之前进行确认 `Publish-Module` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-129">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="5f235-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="5f235-130">-Credential</span></span>

<span data-ttu-id="5f235-131">指定有权为指定的包提供程序或源发布模块的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="5f235-131">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="5f235-132">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5f235-132">-Exclude</span></span>

<span data-ttu-id="5f235-133">定义要从已发布的模块中排除的文件。</span><span class="sxs-lookup"><span data-stu-id="5f235-133">Defines files to exclude from the published module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-134">-Force</span><span class="sxs-lookup"><span data-stu-id="5f235-134">-Force</span></span>

<span data-ttu-id="5f235-135">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="5f235-135">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-136">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="5f235-136">-FormatVersion</span></span>

<span data-ttu-id="5f235-137">仅接受 **ValidateSet** 属性指定的有效值。</span><span class="sxs-lookup"><span data-stu-id="5f235-137">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="5f235-138">有关详细信息，请参阅 [ValidateSet 特性声明](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 和 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)。</span><span class="sxs-lookup"><span data-stu-id="5f235-138">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="5f235-139">-IconUri</span></span>

<span data-ttu-id="5f235-140">指定模块的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="5f235-140">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="5f235-141">指定的图标显示在模块的库网页上。</span><span class="sxs-lookup"><span data-stu-id="5f235-141">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="5f235-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="5f235-142">-LicenseUri</span></span>

<span data-ttu-id="5f235-143">指定要发布的模块的许可条款 URL。</span><span class="sxs-lookup"><span data-stu-id="5f235-143">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="5f235-144">-Name</span><span class="sxs-lookup"><span data-stu-id="5f235-144">-Name</span></span>

<span data-ttu-id="5f235-145">指定要发布的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="5f235-145">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="5f235-146">`Publish-Module` 在中搜索指定的模块名称 `$Env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-146">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-147">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="5f235-147">-NuGetApiKey</span></span>

<span data-ttu-id="5f235-148">指定要用于将模块发布到联机库的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="5f235-148">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="5f235-149">API 密钥是你的个人资料中的配置文件的一部分，可以在库中的用户帐户页面上找到。</span><span class="sxs-lookup"><span data-stu-id="5f235-149">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="5f235-150">API 密钥是 NuGet 特定的功能。</span><span class="sxs-lookup"><span data-stu-id="5f235-150">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="5f235-151">-Path</span><span class="sxs-lookup"><span data-stu-id="5f235-151">-Path</span></span>

<span data-ttu-id="5f235-152">指定要发布的模块的路径。</span><span class="sxs-lookup"><span data-stu-id="5f235-152">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="5f235-153">此参数接受包含模块的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="5f235-153">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-154">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="5f235-154">-ProjectUri</span></span>

<span data-ttu-id="5f235-155">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="5f235-155">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="5f235-156">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="5f235-156">-ReleaseNotes</span></span>

<span data-ttu-id="5f235-157">指定一个字符串，该字符串包含此版本的模块的用户要使用的发行说明或注释。</span><span class="sxs-lookup"><span data-stu-id="5f235-157">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

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

### <span data-ttu-id="5f235-158">-Repository</span><span class="sxs-lookup"><span data-stu-id="5f235-158">-Repository</span></span>

<span data-ttu-id="5f235-159">指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-159">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="5f235-160">存储库必须具有 **PublishLocation**，这是一个有效的 NuGet URI。</span><span class="sxs-lookup"><span data-stu-id="5f235-160">The repository must have a **PublishLocation**, which is a valid NuGet URI.</span></span>
<span data-ttu-id="5f235-161">可以通过运行来设置 **PublishLocation** `Set-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-161">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="5f235-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5f235-162">-RequiredVersion</span></span>

<span data-ttu-id="5f235-163">指定要发布的单个模块的确切版本。</span><span class="sxs-lookup"><span data-stu-id="5f235-163">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-164">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="5f235-164">-SkipAutomaticTags</span></span>

<span data-ttu-id="5f235-165">删除作为标记包含的命令和资源。</span><span class="sxs-lookup"><span data-stu-id="5f235-165">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="5f235-166">跳过自动向模块添加标记。</span><span class="sxs-lookup"><span data-stu-id="5f235-166">Skips automatically adding tags to a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f235-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="5f235-167">-Tags</span></span>

<span data-ttu-id="5f235-168">将一个或多个标记添加到要发布的模块。</span><span class="sxs-lookup"><span data-stu-id="5f235-168">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="5f235-169">示例标记包括 DesiredStateConfiguration、DSC、DSCResourceKit 或 PSModule。</span><span class="sxs-lookup"><span data-stu-id="5f235-169">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="5f235-170">用逗号分隔多个标记。</span><span class="sxs-lookup"><span data-stu-id="5f235-170">Separate multiple tags with commas.</span></span>

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

### <span data-ttu-id="5f235-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f235-171">-WhatIf</span></span>

<span data-ttu-id="5f235-172">显示运行时将发生的情况 `Publish-Module` 。</span><span class="sxs-lookup"><span data-stu-id="5f235-172">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="5f235-173">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="5f235-173">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f235-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f235-174">CommonParameters</span></span>

<span data-ttu-id="5f235-175">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5f235-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f235-176">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5f235-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f235-177">输入</span><span class="sxs-lookup"><span data-stu-id="5f235-177">INPUTS</span></span>

### <span data-ttu-id="5f235-178">System.String</span><span class="sxs-lookup"><span data-stu-id="5f235-178">System.String</span></span>

### <span data-ttu-id="5f235-179">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="5f235-179">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="5f235-180">输出</span><span class="sxs-lookup"><span data-stu-id="5f235-180">OUTPUTS</span></span>

### <span data-ttu-id="5f235-181">System.Object</span><span class="sxs-lookup"><span data-stu-id="5f235-181">System.Object</span></span>

## <span data-ttu-id="5f235-182">注释</span><span class="sxs-lookup"><span data-stu-id="5f235-182">NOTES</span></span>

<span data-ttu-id="5f235-183">`Publish-Module` 在 Windows 7 或 Windows 2008 R2 及更高版本的 Windows 上的 powershell 3.0 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="5f235-183">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f235-184">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="5f235-184">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5f235-185">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="5f235-185">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5f235-186">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="5f235-186">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5f235-187">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="5f235-187">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="5f235-188">发布模块需要在库页面显示的模块的元数据。</span><span class="sxs-lookup"><span data-stu-id="5f235-188">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="5f235-189">所需元数据包括模块名称、版本、说明和作者。</span><span class="sxs-lookup"><span data-stu-id="5f235-189">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="5f235-190">大多数元数据都是从模块清单获取的，但是可以在参数中指定某些元数据， `Publish-Module` 例如 **标记**、 **ReleaseNote**、 **IconUri**、 **ProjectUri** 和 **LicenseUri**。</span><span class="sxs-lookup"><span data-stu-id="5f235-190">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**.</span></span> <span data-ttu-id="5f235-191">有关详细信息，请参阅 [影响 POWERSHELL 库 UI 的包清单值](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)。</span><span class="sxs-lookup"><span data-stu-id="5f235-191">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="5f235-192">相关链接</span><span class="sxs-lookup"><span data-stu-id="5f235-192">RELATED LINKS</span></span>

[<span data-ttu-id="5f235-193">Find-Module</span><span class="sxs-lookup"><span data-stu-id="5f235-193">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="5f235-194">Install-Module</span><span class="sxs-lookup"><span data-stu-id="5f235-194">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="5f235-195">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5f235-195">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="5f235-196">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5f235-196">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="5f235-197">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="5f235-197">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="5f235-198">Update-Module</span><span class="sxs-lookup"><span data-stu-id="5f235-198">Update-Module</span></span>](Update-Module.md)
