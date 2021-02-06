---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 4f00450257178cac72d03303358150fd9f5cd26b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596009"
---
# <span data-ttu-id="a421d-102">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a421d-102">Update-ModuleManifest</span></span>

## <span data-ttu-id="a421d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a421d-103">SYNOPSIS</span></span>
<span data-ttu-id="a421d-104">更新模块清单文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-104">Updates a module manifest file.</span></span>

## <span data-ttu-id="a421d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a421d-105">SYNTAX</span></span>

### <span data-ttu-id="a421d-106">全部</span><span class="sxs-lookup"><span data-stu-id="a421d-106">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a421d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a421d-107">DESCRIPTION</span></span>

<span data-ttu-id="a421d-108">`Update-ModuleManifest`Cmdlet () 文件更新模块清单 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-108">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="a421d-109">示例</span><span class="sxs-lookup"><span data-stu-id="a421d-109">EXAMPLES</span></span>

### <span data-ttu-id="a421d-110">示例1：更新模块清单</span><span class="sxs-lookup"><span data-stu-id="a421d-110">Example 1: Update a module manifest</span></span>

<span data-ttu-id="a421d-111">此示例更新现有的模块清单文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-111">This example updates an existing module manifest file.</span></span> <span data-ttu-id="a421d-112">展开用于将参数值传递给 `Update-ModuleManifest` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-112">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="a421d-113">有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="a421d-113">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="a421d-114">`$Parms` 是存储 **路径**、 **作者**、 **公司名称** 和 **版权** 的参数值的 splat。</span><span class="sxs-lookup"><span data-stu-id="a421d-114">`$Parms` is a splat that stores the parameter values for **Path**, **Author**, **CompanyName**, and **Copyright**.</span></span> <span data-ttu-id="a421d-115">`Update-ModuleManifest` 从获取参数值， `@Parms` 并更新 **TestManifest.psd1** 的模块清单。</span><span class="sxs-lookup"><span data-stu-id="a421d-115">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="a421d-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a421d-116">PARAMETERS</span></span>

### <span data-ttu-id="a421d-117">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="a421d-117">-AliasesToExport</span></span>

<span data-ttu-id="a421d-118">指定模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="a421d-118">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="a421d-119">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-119">Wildcards are permitted.</span></span>

<span data-ttu-id="a421d-120">使用此参数来限制由模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="a421d-120">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="a421d-121">**AliasesToExport** 可以从导出的别名列表中删除别名，但不能将别名添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="a421d-121">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a421d-122">-作者</span><span class="sxs-lookup"><span data-stu-id="a421d-122">-Author</span></span>

<span data-ttu-id="a421d-123">指定模块作者。</span><span class="sxs-lookup"><span data-stu-id="a421d-123">Specifies the module author.</span></span>

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

### <span data-ttu-id="a421d-124">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="a421d-124">-ClrVersion</span></span>

<span data-ttu-id="a421d-125">指定模块需要的 Microsoft .NET Framework 的公共语言运行时 (CLR) 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a421d-125">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-126">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="a421d-126">-CmdletsToExport</span></span>

<span data-ttu-id="a421d-127">指定模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a421d-127">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="a421d-128">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-128">Wildcards are permitted.</span></span>

<span data-ttu-id="a421d-129">使用此参数来限制由模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a421d-129">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="a421d-130">**CmdletsToExport** 可以从导出的 cmdlet 列表中删除 cmdlet，但不能将 cmdlet 添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="a421d-130">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a421d-131">-公司名称</span><span class="sxs-lookup"><span data-stu-id="a421d-131">-CompanyName</span></span>

<span data-ttu-id="a421d-132">指定创建该模块的公司或供应商。</span><span class="sxs-lookup"><span data-stu-id="a421d-132">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="a421d-133">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="a421d-133">-CompatiblePSEditions</span></span>

<span data-ttu-id="a421d-134">指定模块的兼容 **PSEditions** 。</span><span class="sxs-lookup"><span data-stu-id="a421d-134">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="a421d-135">有关 **PSEdition** 的信息，请参阅 [具有兼容的 PowerShell 版本的模块](/powershell/scripting/gallery/concepts/module-psedition-support)。</span><span class="sxs-lookup"><span data-stu-id="a421d-135">For information about **PSEdition**, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a421d-136">-Confirm</span></span>

<span data-ttu-id="a421d-137">在运行之前提示你进行确认 `Update-ModuleManifest` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-137">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="a421d-138">-版权所有</span><span class="sxs-lookup"><span data-stu-id="a421d-138">-Copyright</span></span>

<span data-ttu-id="a421d-139">指定模块的版权声明。</span><span class="sxs-lookup"><span data-stu-id="a421d-139">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="a421d-140">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="a421d-140">-DefaultCommandPrefix</span></span>

<span data-ttu-id="a421d-141">指定默认命令前缀。</span><span class="sxs-lookup"><span data-stu-id="a421d-141">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="a421d-142">-Description</span><span class="sxs-lookup"><span data-stu-id="a421d-142">-Description</span></span>

<span data-ttu-id="a421d-143">指定模块的说明。</span><span class="sxs-lookup"><span data-stu-id="a421d-143">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="a421d-144">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="a421d-144">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="a421d-145">指定模块需要的 Microsoft .NET Framework 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a421d-145">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-146">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="a421d-146">-DscResourcesToExport</span></span>

<span data-ttu-id="a421d-147">指定模块导出 (DSC) 资源的所需状态配置。</span><span class="sxs-lookup"><span data-stu-id="a421d-147">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="a421d-148">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a421d-149">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="a421d-149">-ExternalModuleDependencies</span></span>

<span data-ttu-id="a421d-150">指定外部模块依赖项的数组。</span><span class="sxs-lookup"><span data-stu-id="a421d-150">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="a421d-151">-FileList</span><span class="sxs-lookup"><span data-stu-id="a421d-151">-FileList</span></span>

<span data-ttu-id="a421d-152">指定模块中包括的所有项。</span><span class="sxs-lookup"><span data-stu-id="a421d-152">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="a421d-153">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="a421d-153">-FormatsToProcess</span></span>

<span data-ttu-id="a421d-154">指定 `.ps1xml` 导入模块时运行)  (格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-154">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="a421d-155">导入模块时，PowerShell 将 `Update-FormatData` 使用指定的文件运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a421d-155">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="a421d-156">由于格式设置文件没有作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="a421d-156">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="a421d-157">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="a421d-157">-FunctionsToExport</span></span>

<span data-ttu-id="a421d-158">指定模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="a421d-158">Specifies the functions that the module exports.</span></span> <span data-ttu-id="a421d-159">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-159">Wildcards are permitted.</span></span>

<span data-ttu-id="a421d-160">使用此参数来限制由模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="a421d-160">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="a421d-161">**FunctionsToExport** 可以从导出的别名列表中删除函数，但不能将函数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="a421d-161">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a421d-162">-Guid</span><span class="sxs-lookup"><span data-stu-id="a421d-162">-Guid</span></span>

<span data-ttu-id="a421d-163">指定模块的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="a421d-163">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="a421d-164">可以使用 GUID 来区分名称相同的模块。</span><span class="sxs-lookup"><span data-stu-id="a421d-164">The GUID can be used to distinguish among modules with the same name.</span></span>

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

### <span data-ttu-id="a421d-165">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="a421d-165">-HelpInfoUri</span></span>

<span data-ttu-id="a421d-166">指定模块的 **HELPINFO XML** 文件的 internet 地址。</span><span class="sxs-lookup"><span data-stu-id="a421d-166">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="a421d-167">输入以 **http** 或 **HTTPS** 开头 (URI) 的统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="a421d-167">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="a421d-168">**HELPINFO XML** 文件支持 PowerShell 版本3.0 中引入的可更新帮助功能。</span><span class="sxs-lookup"><span data-stu-id="a421d-168">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="a421d-169">它包含有关该模块的可下载帮助文件的位置，以及每个支持的区域设置最新帮助文件的版本号的信息。</span><span class="sxs-lookup"><span data-stu-id="a421d-169">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="a421d-170">有关可更新帮助的信息，请参阅 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="a421d-170">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="a421d-171">有关 **HELPINFO XML** 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。</span><span class="sxs-lookup"><span data-stu-id="a421d-171">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="a421d-172">-IconUri</span><span class="sxs-lookup"><span data-stu-id="a421d-172">-IconUri</span></span>

<span data-ttu-id="a421d-173">指定模块的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="a421d-173">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="a421d-174">指定的图标显示在模块的库网页上。</span><span class="sxs-lookup"><span data-stu-id="a421d-174">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="a421d-175">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="a421d-175">-LicenseUri</span></span>

<span data-ttu-id="a421d-176">指定模块的许可条款 URL。</span><span class="sxs-lookup"><span data-stu-id="a421d-176">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="a421d-177">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="a421d-177">-ModuleList</span></span>

<span data-ttu-id="a421d-178">指定模块中包含的模块的数组。</span><span class="sxs-lookup"><span data-stu-id="a421d-178">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="a421d-179">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="a421d-179">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="a421d-180">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="a421d-180">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="a421d-181">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="a421d-181">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="a421d-182">此键专门用于充当模块清单。</span><span class="sxs-lookup"><span data-stu-id="a421d-182">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="a421d-183">不会自动处理此键的值中列出的模块。</span><span class="sxs-lookup"><span data-stu-id="a421d-183">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="a421d-184">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="a421d-184">-ModuleVersion</span></span>

<span data-ttu-id="a421d-185">指定模块的版本。</span><span class="sxs-lookup"><span data-stu-id="a421d-185">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-186">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="a421d-186">-NestedModules</span></span>

<span data-ttu-id="a421d-187">指定脚本模块 (`.psm1` `.dll` 导入模块的会话状态中 () 的) 和二进制模块。</span><span class="sxs-lookup"><span data-stu-id="a421d-187">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="a421d-188">**NestedModules** 键中的文件按照其在值中的列出顺序运行。</span><span class="sxs-lookup"><span data-stu-id="a421d-188">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="a421d-189">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="a421d-189">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="a421d-190">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="a421d-190">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="a421d-191">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="a421d-191">You can combine strings and hash tables in the parameter value.</span></span>

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

### <span data-ttu-id="a421d-192">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="a421d-192">-PackageManagementProviders</span></span>

<span data-ttu-id="a421d-193">指定包管理提供程序的数组。</span><span class="sxs-lookup"><span data-stu-id="a421d-193">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="a421d-194">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a421d-194">-PassThru</span></span>

<span data-ttu-id="a421d-195">返回一个对象，该对象表示正在处理的项。</span><span class="sxs-lookup"><span data-stu-id="a421d-195">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="a421d-196">默认情况下， `Update-ModuleManifest` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="a421d-196">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="a421d-197">-Path</span><span class="sxs-lookup"><span data-stu-id="a421d-197">-Path</span></span>

<span data-ttu-id="a421d-198">指定模块清单的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="a421d-198">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="a421d-199">输入文件扩展名为的路径和文件名 `.psd1` ，例如 `$PSHOME\Modules\MyModule\MyModule.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-199">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="a421d-200">如果指定了现有文件的路径，则将 `Update-ModuleManifest` 替换该文件而不发出警告，除非该文件具有只读属性。</span><span class="sxs-lookup"><span data-stu-id="a421d-200">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="a421d-201">清单应位于模块的目录中，清单文件的名称应与模块目录名称相同，但具有 `.psd1` 扩展名。</span><span class="sxs-lookup"><span data-stu-id="a421d-201">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="a421d-202">不能使用变量（如 `$PSHOME` 或 `$HOME` ）来响应 **Path** 参数值的提示。</span><span class="sxs-lookup"><span data-stu-id="a421d-202">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="a421d-203">若要使用变量，请将 **Path** 参数包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="a421d-203">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="a421d-204">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="a421d-204">-PowerShellHostName</span></span>

<span data-ttu-id="a421d-205">指定模块所需的 PowerShell 主机程序的名称。</span><span class="sxs-lookup"><span data-stu-id="a421d-205">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="a421d-206">输入主机程序的名称，例如 PowerShell ISE Host 或 ConsoleHost。</span><span class="sxs-lookup"><span data-stu-id="a421d-206">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="a421d-207">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-207">Wildcards aren't permitted.</span></span>

<span data-ttu-id="a421d-208">若要查找主机程序的名称，请在 "程序" 中键入 `$Host.Name` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-208">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="a421d-209">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="a421d-209">-PowerShellHostVersion</span></span>

<span data-ttu-id="a421d-210">指定适用于该模块的 PowerShell 主机程序的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a421d-210">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="a421d-211">输入版本号，例如 1.1。</span><span class="sxs-lookup"><span data-stu-id="a421d-211">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-212">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="a421d-212">-PowerShellVersion</span></span>

<span data-ttu-id="a421d-213">指定将用于此模块的 PowerShell 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a421d-213">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="a421d-214">例如，可以将3.0、4.0 或5.0 指定为此参数的值。</span><span class="sxs-lookup"><span data-stu-id="a421d-214">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-215">-预发行版</span><span class="sxs-lookup"><span data-stu-id="a421d-215">-Prerelease</span></span>

<span data-ttu-id="a421d-216">指示模块为预发行版。</span><span class="sxs-lookup"><span data-stu-id="a421d-216">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="a421d-217">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="a421d-217">-PrivateData</span></span>

<span data-ttu-id="a421d-218">指定导入模块时传递给模块的数据。</span><span class="sxs-lookup"><span data-stu-id="a421d-218">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-219">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="a421d-219">-ProcessorArchitecture</span></span>

<span data-ttu-id="a421d-220">指定模块需要的处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="a421d-220">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="a421d-221">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="a421d-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a421d-222">Amd64</span><span class="sxs-lookup"><span data-stu-id="a421d-222">Amd64</span></span>
- <span data-ttu-id="a421d-223">Arm</span><span class="sxs-lookup"><span data-stu-id="a421d-223">Arm</span></span>
- <span data-ttu-id="a421d-224">IA64</span><span class="sxs-lookup"><span data-stu-id="a421d-224">IA64</span></span>
- <span data-ttu-id="a421d-225">MSIL</span><span class="sxs-lookup"><span data-stu-id="a421d-225">MSIL</span></span>
- <span data-ttu-id="a421d-226">无 (未知或未指定的) </span><span class="sxs-lookup"><span data-stu-id="a421d-226">None (unknown or unspecified)</span></span>
- <span data-ttu-id="a421d-227">X86</span><span class="sxs-lookup"><span data-stu-id="a421d-227">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a421d-228">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="a421d-228">-ProjectUri</span></span>

<span data-ttu-id="a421d-229">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="a421d-229">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="a421d-230">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="a421d-230">-ReleaseNotes</span></span>

<span data-ttu-id="a421d-231">指定一个字符串数组，其中包含要用于此版本的脚本的发行说明或注释。</span><span class="sxs-lookup"><span data-stu-id="a421d-231">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="a421d-232">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="a421d-232">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="a421d-233">指定模块需要接受许可证。</span><span class="sxs-lookup"><span data-stu-id="a421d-233">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="a421d-234">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="a421d-234">-RequiredAssemblies</span></span>

<span data-ttu-id="a421d-235">指定模块需要的程序集 (`.dll`) 文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-235">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="a421d-236">输入程序集文件名。</span><span class="sxs-lookup"><span data-stu-id="a421d-236">Enter the assembly file names.</span></span>
<span data-ttu-id="a421d-237">PowerShell 在更新类型或格式、导入嵌套模块或导入在 **RootModule** 项的值中指定的模块文件之前加载指定的程序集。</span><span class="sxs-lookup"><span data-stu-id="a421d-237">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="a421d-238">使用此参数可指定模块所需的所有程序集，包括必须加载以便更新 **FormatsToProcess** 或 **TypesToProcess** 键中列出的任何格式设置或类型文件的程序集，即使这些程序集也在 **NestedModules** 项中作为二进制模块列出也是如此。</span><span class="sxs-lookup"><span data-stu-id="a421d-238">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="a421d-239">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="a421d-239">-RequiredModules</span></span>

<span data-ttu-id="a421d-240">指定必须处于全局会话状态的模块。</span><span class="sxs-lookup"><span data-stu-id="a421d-240">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="a421d-241">如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="a421d-241">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="a421d-242">如果所需模块不可用，则该 `Import-Module` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="a421d-242">If the required modules aren't available, the `Import-Module` command fails.</span></span>

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

### <span data-ttu-id="a421d-243">-RootModule</span><span class="sxs-lookup"><span data-stu-id="a421d-243">-RootModule</span></span>

<span data-ttu-id="a421d-244">指定模块的主文件或根文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-244">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="a421d-245">输入脚本的文件名 (`.ps1`) 、脚本模块 (`.psm1`) 、模块清单 () `.psd1` 、程序集 (`.dll`) 、cmdlet 定义 XML 文件 (`.cdxml`) 或 () 工作流 `.xaml` 。</span><span class="sxs-lookup"><span data-stu-id="a421d-245">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="a421d-246">导入模块时，从根模块文件导出的成员将导入到调用方的会话状态中。</span><span class="sxs-lookup"><span data-stu-id="a421d-246">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="a421d-247">如果某个模块具有清单文件，并且未在 **RootModule** 项中指定任何根文件，则该清单将成为该模块的主文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-247">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="a421d-248">而且，模块将成为清单模块 (ModuleType = Manifest) 。</span><span class="sxs-lookup"><span data-stu-id="a421d-248">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="a421d-249">若要从 `.psm1` `.dll` 具有清单的模块中的或文件中导出成员，必须在清单中的 **RootModule** 或 **NestedModules** 键的值中指定这些文件的名称。</span><span class="sxs-lookup"><span data-stu-id="a421d-249">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="a421d-250">否则，不会导出它们的成员。</span><span class="sxs-lookup"><span data-stu-id="a421d-250">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="a421d-251">在 PowerShell 2.0 中，此密钥称为 **ModuleToProcess**。</span><span class="sxs-lookup"><span data-stu-id="a421d-251">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="a421d-252">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="a421d-252">-ScriptsToProcess</span></span>

<span data-ttu-id="a421d-253">指定 `.ps1` 导入模块时，在调用方的会话状态中运行的脚本 () 文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-253">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="a421d-254">可以像使用登录脚本一样使用这些脚本来准备环境。</span><span class="sxs-lookup"><span data-stu-id="a421d-254">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="a421d-255">若要指定在模块的会话状态中运行的脚本，请使用 **NestedModules** 键。</span><span class="sxs-lookup"><span data-stu-id="a421d-255">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="a421d-256">-Tags</span><span class="sxs-lookup"><span data-stu-id="a421d-256">-Tags</span></span>

<span data-ttu-id="a421d-257">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="a421d-257">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="a421d-258">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="a421d-258">-TypesToProcess</span></span>

<span data-ttu-id="a421d-259">指定 `.ps1xml` 导入模块时运行)  (类型文件。</span><span class="sxs-lookup"><span data-stu-id="a421d-259">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="a421d-260">导入模块时，PowerShell 将运行 `Update-TypeData` 具有指定文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a421d-260">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="a421d-261">由于类型文件不作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="a421d-261">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="a421d-262">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="a421d-262">-VariablesToExport</span></span>

<span data-ttu-id="a421d-263">指定模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="a421d-263">Specifies the variables that the module exports.</span></span> <span data-ttu-id="a421d-264">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a421d-264">Wildcards are permitted.</span></span>

<span data-ttu-id="a421d-265">使用此参数来限制由模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="a421d-265">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="a421d-266">**VariablesToExport** 可以从导出的变量列表中删除变量，但不能将变量添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="a421d-266">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a421d-267">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a421d-267">-WhatIf</span></span>

<span data-ttu-id="a421d-268">显示运行时将发生 `Update-ModuleManifest` 的情况。</span><span class="sxs-lookup"><span data-stu-id="a421d-268">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="a421d-269">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="a421d-269">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a421d-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a421d-270">CommonParameters</span></span>

<span data-ttu-id="a421d-271">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a421d-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a421d-272">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a421d-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a421d-273">输入</span><span class="sxs-lookup"><span data-stu-id="a421d-273">INPUTS</span></span>

### <span data-ttu-id="a421d-274">System.String</span><span class="sxs-lookup"><span data-stu-id="a421d-274">System.String</span></span>

## <span data-ttu-id="a421d-275">输出</span><span class="sxs-lookup"><span data-stu-id="a421d-275">OUTPUTS</span></span>

### <span data-ttu-id="a421d-276">System.Object</span><span class="sxs-lookup"><span data-stu-id="a421d-276">System.Object</span></span>

## <span data-ttu-id="a421d-277">注释</span><span class="sxs-lookup"><span data-stu-id="a421d-277">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a421d-278">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="a421d-278">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a421d-279">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="a421d-279">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a421d-280">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="a421d-280">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a421d-281">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="a421d-281">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a421d-282">相关链接</span><span class="sxs-lookup"><span data-stu-id="a421d-282">RELATED LINKS</span></span>
