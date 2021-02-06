---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 713c35b2f9f651d455ac08401aa1f7eb48676174
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "99595417"
---
# <span data-ttu-id="d8595-102">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d8595-102">New-ModuleManifest</span></span>

## <span data-ttu-id="d8595-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d8595-103">SYNOPSIS</span></span>
<span data-ttu-id="d8595-104">创建新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-104">Creates a new module manifest.</span></span>

## <span data-ttu-id="d8595-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8595-105">SYNTAX</span></span>

### <span data-ttu-id="d8595-106">全部</span><span class="sxs-lookup"><span data-stu-id="d8595-106">All</span></span>

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="d8595-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8595-107">DESCRIPTION</span></span>

<span data-ttu-id="d8595-108">`New-ModuleManifest`Cmdlet 将 () 文件创建新的模块清单 `.psd1` ，并填充其值，并将清单文件保存在指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="d8595-108">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="d8595-109">模块作者可以使用此 cmdlet 来为其模块创建清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-109">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="d8595-110">模块清单是 `.psd1` 包含哈希表的文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-110">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="d8595-111">哈希表中的键和值用于描述该模块的内容和属性、定义先决条件以及确定如何处理组件。</span><span class="sxs-lookup"><span data-stu-id="d8595-111">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="d8595-112">模块不需要清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-112">Manifests aren't required for a module.</span></span>

<span data-ttu-id="d8595-113">`New-ModuleManifest` 创建一个包含所有常用清单键的清单，以便您可以使用默认输出作为清单模板。</span><span class="sxs-lookup"><span data-stu-id="d8595-113">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="d8595-114">若要添加或更改值，或者添加此 cmdlet 未添加的模块键，请在文本编辑器中打开生成的文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-114">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="d8595-115">除了 **Path** 和 **PassThru** 以外，每个参数都将创建一个模块清单键及其值。</span><span class="sxs-lookup"><span data-stu-id="d8595-115">Each parameter, except for **Path** and **PassThru**, creates a module manifest key and its value.</span></span>
<span data-ttu-id="d8595-116">在模块清单中，仅 **ModuleVersion** 键是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8595-116">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="d8595-117">除非在参数说明中指定，否则，如果从命令中省略某个参数，则将 `New-ModuleManifest` 为关联值创建一个不起作用的注释字符串。</span><span class="sxs-lookup"><span data-stu-id="d8595-117">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="d8595-118">在 PowerShell 2.0 中，系统将 `New-ModuleManifest` 提示你输入未在命令中指定的常用参数的值，以及所需的参数值。</span><span class="sxs-lookup"><span data-stu-id="d8595-118">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="d8595-119">从 PowerShell 3.0 开始， `New-ModuleManifest` 仅在未指定必需的参数值时提示。</span><span class="sxs-lookup"><span data-stu-id="d8595-119">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="d8595-120">如果计划在 PowerShell 库中发布模块，则清单必须包含特定属性的值。</span><span class="sxs-lookup"><span data-stu-id="d8595-120">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="d8595-121">有关详细信息，请参阅库文档中 [发布到 PowerShell 库的项的必需元数据](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 。</span><span class="sxs-lookup"><span data-stu-id="d8595-121">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="d8595-122">示例</span><span class="sxs-lookup"><span data-stu-id="d8595-122">EXAMPLES</span></span>

### <span data-ttu-id="d8595-123">示例 1-创建新的模块清单</span><span class="sxs-lookup"><span data-stu-id="d8595-123">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="d8595-124">此示例在 **Path** 参数指定的文件中创建一个新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-124">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="d8595-125">**PassThru** 参数将输出发送到管道和文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-125">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="d8595-126">该输出显示清单中的所有键的默认值。</span><span class="sxs-lookup"><span data-stu-id="d8595-126">The output shows the default values of all keys in the manifest.</span></span>

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### <span data-ttu-id="d8595-127">示例 2-使用一些预填充的设置创建新清单</span><span class="sxs-lookup"><span data-stu-id="d8595-127">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="d8595-128">此示例将创建一个新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-128">This example creates a new module manifest.</span></span> <span data-ttu-id="d8595-129">它使用 **PowerShellVersion** 和 **AliasesToExport** 参数将值添加到相应的清单键。</span><span class="sxs-lookup"><span data-stu-id="d8595-129">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="d8595-130">示例 3-创建需要其他模块的清单</span><span class="sxs-lookup"><span data-stu-id="d8595-130">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="d8595-131">此示例使用字符串格式指定 **BitsTransfer** 模块的名称，使用哈希表格式指定 **PSScheduledJob** 模块的名称、 **GUID** 和版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-131">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID**, and a version of the **PSScheduledJob** module.</span></span>

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="d8595-132">此示例演示如何使用 **ModuleList**、 **RequiredModules** 和 **NestedModules** 参数的字符串和哈希表格式。</span><span class="sxs-lookup"><span data-stu-id="d8595-132">This example shows how to use the string and hash table formats of the **ModuleList**, **RequiredModules**, and **NestedModules** parameter.</span></span> <span data-ttu-id="d8595-133">可以将字符串和哈希表组合到同一参数值中。</span><span class="sxs-lookup"><span data-stu-id="d8595-133">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="d8595-134">示例 4-创建支持可更新帮助的清单</span><span class="sxs-lookup"><span data-stu-id="d8595-134">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="d8595-135">此示例使用 **HelpInfoUri** 参数在模块清单中创建 **HelpInfoUri** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-135">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="d8595-136">参数和密钥的值必须以 **http** 或 **https** 开头。</span><span class="sxs-lookup"><span data-stu-id="d8595-136">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="d8595-137">此值会向可更新帮助系统指示该模块的 HelpInfo XML 可更新帮助信息文件的位置。</span><span class="sxs-lookup"><span data-stu-id="d8595-137">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="d8595-138">有关可更新帮助的信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="d8595-138">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="d8595-139">有关 HelpInfo XML 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。</span><span class="sxs-lookup"><span data-stu-id="d8595-139">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="d8595-140">示例 5-获取模块信息</span><span class="sxs-lookup"><span data-stu-id="d8595-140">Example 5 - Getting module information</span></span>

<span data-ttu-id="d8595-141">此示例演示如何获取模块的配置值。</span><span class="sxs-lookup"><span data-stu-id="d8595-141">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="d8595-142">模块清单中的值反映在 module 对象的属性值中。</span><span class="sxs-lookup"><span data-stu-id="d8595-142">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="d8595-143">`Get-Module`Cmdlet 用于获取使用 **List** 参数的 **Microsoft PowerShell 诊断** 模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-143">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="d8595-144">命令将模块发送到 `Format-List` cmdlet，以显示 module 对象的所有属性和值。</span><span class="sxs-lookup"><span data-stu-id="d8595-144">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## <span data-ttu-id="d8595-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8595-145">PARAMETERS</span></span>

### <span data-ttu-id="d8595-146">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="d8595-146">-AliasesToExport</span></span>

<span data-ttu-id="d8595-147">指定模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="d8595-147">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="d8595-148">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-148">Wildcards are permitted.</span></span>

<span data-ttu-id="d8595-149">可以使用此参数来限制由模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="d8595-149">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="d8595-150">它可以从导出的别名列表中删除别名，但不能将别名添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="d8595-150">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="d8595-151">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **AliasesToExport** 键 `*` ，这意味着该模块中定义的所有别名都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="d8595-151">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d8595-152">-作者</span><span class="sxs-lookup"><span data-stu-id="d8595-152">-Author</span></span>

<span data-ttu-id="d8595-153">指定模块作者。</span><span class="sxs-lookup"><span data-stu-id="d8595-153">Specifies the module author.</span></span>

<span data-ttu-id="d8595-154">如果省略此参数，则将 `New-ModuleManifest` 创建具有当前用户名称的 **Author** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-154">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-155">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="d8595-155">-CmdletsToExport</span></span>

<span data-ttu-id="d8595-156">指定模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8595-156">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="d8595-157">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-157">Wildcards are permitted.</span></span>

<span data-ttu-id="d8595-158">可以使用此参数来限制由模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8595-158">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="d8595-159">它可以从导出的 cmdlet 列表中删除 cmdlet，但不能将 cmdlet 添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="d8595-159">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="d8595-160">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **CmdletsToExport** 键 `*` ，这意味着该模块中定义的所有 cmdlet 都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="d8595-160">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d8595-161">-公司名称</span><span class="sxs-lookup"><span data-stu-id="d8595-161">-CompanyName</span></span>

<span data-ttu-id="d8595-162">标识创建了该模块的公司或供应商。</span><span class="sxs-lookup"><span data-stu-id="d8595-162">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="d8595-163">如果省略此参数，则将 `New-ModuleManifest` 创建值为 "Unknown" 的 " **公司名称** " 密钥。</span><span class="sxs-lookup"><span data-stu-id="d8595-163">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-164">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="d8595-164">-CompatiblePSEditions</span></span>

<span data-ttu-id="d8595-165">指定模块的兼容 PSEditions。</span><span class="sxs-lookup"><span data-stu-id="d8595-165">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="d8595-166">有关 PSEdition 的信息，请参阅 [具有兼容的 PowerShell 版本的模块](/powershell/scripting/gallery/concepts/module-psedition-support)。</span><span class="sxs-lookup"><span data-stu-id="d8595-166">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="d8595-167">-版权所有</span><span class="sxs-lookup"><span data-stu-id="d8595-167">-Copyright</span></span>

<span data-ttu-id="d8595-168">指定模块的版权声明。</span><span class="sxs-lookup"><span data-stu-id="d8595-168">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="d8595-169">如果省略此参数，则 `New-ModuleManifest` 将创建值为的 **版权** 密钥， `(c) <year> <username>. All rights reserved.` 其中 `<year>` 为当前年份， `<username>` 是 **作者** 密钥的值。</span><span class="sxs-lookup"><span data-stu-id="d8595-169">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-170">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="d8595-170">-DefaultCommandPrefix</span></span>

<span data-ttu-id="d8595-171">指定在将模块中的所有命令导入到会话中时在该模块中的所有命令的名词前面预置的前缀。</span><span class="sxs-lookup"><span data-stu-id="d8595-171">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="d8595-172">输入前缀字符串。</span><span class="sxs-lookup"><span data-stu-id="d8595-172">Enter a prefix string.</span></span> <span data-ttu-id="d8595-173">前缀可防止用户会话中的命令名称发生冲突。</span><span class="sxs-lookup"><span data-stu-id="d8595-173">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="d8595-174">模块用户可以通过指定 cmdlet 的 **prefix** 参数来重写此前缀 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-174">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="d8595-175">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="d8595-175">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d8595-176">-Description</span><span class="sxs-lookup"><span data-stu-id="d8595-176">-Description</span></span>

<span data-ttu-id="d8595-177">描述模块的内容。</span><span class="sxs-lookup"><span data-stu-id="d8595-177">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="d8595-178">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="d8595-178">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="d8595-179">指定模块需要的 Microsoft .NET Framework 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-179">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="d8595-180">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="d8595-180">-DscResourcesToExport</span></span>

<span data-ttu-id="d8595-181">指定模块导出 (DSC) 资源的所需状态配置。</span><span class="sxs-lookup"><span data-stu-id="d8595-181">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="d8595-182">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-182">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="d8595-183">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="d8595-183">-ExternalModuleDependencies</span></span>

<span data-ttu-id="d8595-184">此模块所依赖的外部模块的列表。</span><span class="sxs-lookup"><span data-stu-id="d8595-184">A list of external modules that this module is depends on.</span></span>

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

### <span data-ttu-id="d8595-185">-FileList</span><span class="sxs-lookup"><span data-stu-id="d8595-185">-FileList</span></span>

<span data-ttu-id="d8595-186">指定模块中包括的所有项。</span><span class="sxs-lookup"><span data-stu-id="d8595-186">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="d8595-187">此键专门用于充当模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-187">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="d8595-188">当发布模块时，将包含该键中列出的文件，但不会自动导出任何函数。</span><span class="sxs-lookup"><span data-stu-id="d8595-188">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="d8595-189">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="d8595-189">-FormatsToProcess</span></span>

<span data-ttu-id="d8595-190">指定 `.ps1xml` 导入模块时运行)  (格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-190">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="d8595-191">导入模块时，PowerShell 将 `Update-FormatData` 使用指定的文件运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8595-191">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="d8595-192">由于格式设置文件没有作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-192">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="d8595-193">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="d8595-193">-FunctionsToExport</span></span>

<span data-ttu-id="d8595-194">指定模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="d8595-194">Specifies the functions that the module exports.</span></span> <span data-ttu-id="d8595-195">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-195">Wildcards are permitted.</span></span>

<span data-ttu-id="d8595-196">可以使用此参数来限制由模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="d8595-196">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="d8595-197">它可以从导出的别名列表中删除函数，但不能将函数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="d8595-197">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="d8595-198">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **FunctionsToExport** 键 `*` ，这意味着该模块中定义的所有函数都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="d8595-198">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d8595-199">-Guid</span><span class="sxs-lookup"><span data-stu-id="d8595-199">-Guid</span></span>

<span data-ttu-id="d8595-200">指定模块的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="d8595-200">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="d8595-201">可以使用 **GUID** 来区分名称相同的模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-201">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="d8595-202">如果省略此参数，则 `New-ModuleManifest` 在清单中创建 **guid** 密钥并为值生成 **guid** 。</span><span class="sxs-lookup"><span data-stu-id="d8595-202">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="d8595-203">若要在 PowerShell 中创建新的 **GUID** ，请键入 `[guid]::NewGuid()` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-203">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-204">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="d8595-204">-HelpInfoUri</span></span>

<span data-ttu-id="d8595-205">指定模块的 HelpInfo XML 文件的 internet 地址。</span><span class="sxs-lookup"><span data-stu-id="d8595-205">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="d8595-206">输入以 **http** 或 **HTTPS** 开头 (URI) 的统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="d8595-206">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="d8595-207">HelpInfo XML 文件支持 PowerShell 3.0 中引入的可更新帮助功能。</span><span class="sxs-lookup"><span data-stu-id="d8595-207">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="d8595-208">它包含有关该模块的可下载帮助文件的位置，以及每个支持的区域设置的最新帮助文件的版本号的信息。</span><span class="sxs-lookup"><span data-stu-id="d8595-208">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="d8595-209">有关可更新帮助的信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="d8595-209">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="d8595-210">有关 HelpInfo XML 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。</span><span class="sxs-lookup"><span data-stu-id="d8595-210">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="d8595-211">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="d8595-211">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d8595-212">-IconUri</span><span class="sxs-lookup"><span data-stu-id="d8595-212">-IconUri</span></span>

<span data-ttu-id="d8595-213">指定模块的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8595-213">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="d8595-214">指定的图标显示在模块的库网页上。</span><span class="sxs-lookup"><span data-stu-id="d8595-214">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="d8595-215">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="d8595-215">-LicenseUri</span></span>

<span data-ttu-id="d8595-216">指定模块的许可条款 URL。</span><span class="sxs-lookup"><span data-stu-id="d8595-216">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="d8595-217">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="d8595-217">-ModuleList</span></span>

<span data-ttu-id="d8595-218">列出此模块中包括的所有模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-218">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="d8595-219">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="d8595-219">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="d8595-220">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-220">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="d8595-221">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="d8595-221">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="d8595-222">此键专门用于充当模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-222">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="d8595-223">不会自动处理此键的值中列出的模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-223">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="d8595-224">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="d8595-224">-ModuleVersion</span></span>

<span data-ttu-id="d8595-225">指定模块的版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-225">Specifies the module's version.</span></span>

<span data-ttu-id="d8595-226">此参数不是必需的，但清单中需要 **ModuleVersion** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-226">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="d8595-227">如果省略此参数，则将 `New-ModuleManifest` 创建值为1.0 的 **ModuleVersion** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-227">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-228">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="d8595-228">-NestedModules</span></span>

<span data-ttu-id="d8595-229">指定脚本模块 (`.psm1` `.dll` 导入模块的会话状态中 () 的) 和二进制模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-229">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="d8595-230">**NestedModules** 键中的文件按照其在值中的列出顺序运行。</span><span class="sxs-lookup"><span data-stu-id="d8595-230">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="d8595-231">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="d8595-231">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="d8595-232">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-232">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="d8595-233">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="d8595-233">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="d8595-234">通常情况下，嵌套模块包含根模块需用于内部处理的命令。</span><span class="sxs-lookup"><span data-stu-id="d8595-234">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="d8595-235">默认情况下，嵌套模块中的命令将从模块的会话状态导出到调用方的会话状态中，但根模块可以限制它导出的命令。</span><span class="sxs-lookup"><span data-stu-id="d8595-235">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="d8595-236">例如，使用 `Export-ModuleMember` 命令。</span><span class="sxs-lookup"><span data-stu-id="d8595-236">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="d8595-237">模块会话状态中的嵌套模块可用于根模块，但 `Get-Module` 在调用方的会话状态中，命令不会返回这些模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-237">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="d8595-238">`.ps1` **NestedModules** 键中列出的脚本 () 在模块的会话状态中运行，而不是在调用方的会话状态中运行。</span><span class="sxs-lookup"><span data-stu-id="d8595-238">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="d8595-239">若要在调用方的会话状态中运行脚本，请在清单的 **ScriptsToProcess** 键的值中列出脚本文件名。</span><span class="sxs-lookup"><span data-stu-id="d8595-239">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="d8595-240">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d8595-240">-PassThru</span></span>

<span data-ttu-id="d8595-241">将生成的模块清单写入控制台并创建 `.psd1` 文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-241">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="d8595-242">默认情况下，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="d8595-242">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="d8595-243">-Path</span><span class="sxs-lookup"><span data-stu-id="d8595-243">-Path</span></span>

<span data-ttu-id="d8595-244">指定新模块清单的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="d8595-244">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="d8595-245">输入文件扩展名为的路径和文件名 `.psd1` ，例如 `$pshome\Modules\MyModule\MyModule.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-245">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="d8595-246">**Path** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8595-246">The **Path** parameter is required.</span></span>

<span data-ttu-id="d8595-247">如果指定了现有文件的路径，则将 `New-ModuleManifest` 替换该文件而不发出警告，除非该文件具有只读属性。</span><span class="sxs-lookup"><span data-stu-id="d8595-247">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="d8595-248">清单应位于模块的目录中，清单文件的名称应与模块目录名称相同，但具有 `.psd1` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="d8595-248">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="d8595-249">不能使用变量（如 `$PSHOME` 或 `$HOME` ）来响应 **Path** 参数值的提示。</span><span class="sxs-lookup"><span data-stu-id="d8595-249">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="d8595-250">若要使用变量，请将 **Path** 参数包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="d8595-250">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-251">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="d8595-251">-PowerShellHostName</span></span>

<span data-ttu-id="d8595-252">指定模块所需的 PowerShell 主机程序的名称。</span><span class="sxs-lookup"><span data-stu-id="d8595-252">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="d8595-253">输入主机程序的名称，例如 **Windows PowerShell ISE host** or **ConsoleHost**。</span><span class="sxs-lookup"><span data-stu-id="d8595-253">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="d8595-254">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-254">Wildcards aren't permitted.</span></span>

<span data-ttu-id="d8595-255">若要查找主机程序的名称，请在 "程序" 中键入 `$Host.Name` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-255">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="d8595-256">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="d8595-256">-PowerShellHostVersion</span></span>

<span data-ttu-id="d8595-257">指定适用于该模块的 PowerShell 主机程序的最低版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-257">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="d8595-258">输入版本号，例如 1.1。</span><span class="sxs-lookup"><span data-stu-id="d8595-258">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="d8595-259">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="d8595-259">-PowerShellVersion</span></span>

<span data-ttu-id="d8595-260">指定适用于此模块的 PowerShell 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-260">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="d8595-261">例如，可以输入1.0、2.0 或3.0 作为参数的值。</span><span class="sxs-lookup"><span data-stu-id="d8595-261">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span> <span data-ttu-id="d8595-262">它必须采用 X. X 格式。</span><span class="sxs-lookup"><span data-stu-id="d8595-262">It must be in an X.X format.</span></span> <span data-ttu-id="d8595-263">例如，如果你提交 `5` ，则 PowerShell 将引发错误。</span><span class="sxs-lookup"><span data-stu-id="d8595-263">For example, if you submit `5`, PowerShell will throw an error.</span></span>

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

### <span data-ttu-id="d8595-264">-预发行版</span><span class="sxs-lookup"><span data-stu-id="d8595-264">-Prerelease</span></span>

<span data-ttu-id="d8595-265">此模块的预发行版本字符串。</span><span class="sxs-lookup"><span data-stu-id="d8595-265">Prerelease string of this module.</span></span> <span data-ttu-id="d8595-266">添加预发布字符串会将模块标识为预发行版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-266">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="d8595-267">在将模块发布到 PowerShell 库时，将使用此数据来标识预发行包。</span><span class="sxs-lookup"><span data-stu-id="d8595-267">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="d8595-268">若要从库中获取预发行包，必须在 PowerShellGet 命令中使用 **AllowPrerelease** 参数 `Find-Module` ： `Install-Module` 、 `Update-Module` 和 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-268">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="d8595-269">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="d8595-269">-PrivateData</span></span>

<span data-ttu-id="d8595-270">指定导入模块时传递给模块的数据。</span><span class="sxs-lookup"><span data-stu-id="d8595-270">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-271">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="d8595-271">-ProcessorArchitecture</span></span>

<span data-ttu-id="d8595-272">指定模块需要的处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="d8595-272">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="d8595-273">有效值为 x86、AMD64、IA64、MSIL 和 None (未知或未指定的) 。</span><span class="sxs-lookup"><span data-stu-id="d8595-273">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="d8595-274">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="d8595-274">-ProjectUri</span></span>

<span data-ttu-id="d8595-275">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="d8595-275">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="d8595-276">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="d8595-276">-ReleaseNotes</span></span>

<span data-ttu-id="d8595-277">指定发行说明。</span><span class="sxs-lookup"><span data-stu-id="d8595-277">Specifies release notes.</span></span>

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

### <span data-ttu-id="d8595-278">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="d8595-278">-RequiredAssemblies</span></span>

<span data-ttu-id="d8595-279">指定模块需要的程序集 (`.dll`) 文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-279">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="d8595-280">输入程序集文件名。</span><span class="sxs-lookup"><span data-stu-id="d8595-280">Enter the assembly file names.</span></span>
<span data-ttu-id="d8595-281">PowerShell 在更新类型或格式、导入嵌套模块或导入在 **RootModule** 项的值中指定的模块文件之前加载指定的程序集。</span><span class="sxs-lookup"><span data-stu-id="d8595-281">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="d8595-282">使用此参数可列出模块所需要的所有程序集，包括必须加载以更新在 **FormatsToProcess** 或 **TypesToProcess** 键中列出的任何格式设置文件或类型文件的程序集，即使另将这些程序集列为 **NestedModules** 键中的二进制模块也是如此。</span><span class="sxs-lookup"><span data-stu-id="d8595-282">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="d8595-283">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="d8595-283">-RequiredModules</span></span>

<span data-ttu-id="d8595-284">指定必须处于全局会话状态的模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-284">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="d8595-285">如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="d8595-285">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="d8595-286">如果所需模块不可用，则该 `Import-Module` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="d8595-286">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="d8595-287">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="d8595-287">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="d8595-288">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-288">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="d8595-289">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="d8595-289">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="d8595-290">在 PowerShell 2.0 中， `Import-Module` 不会自动导入所需的模块。</span><span class="sxs-lookup"><span data-stu-id="d8595-290">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="d8595-291">它只会验证所需模块是否处于全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-291">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="d8595-292">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="d8595-292">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="d8595-293">一个标志，用于指示该模块是否需要显式用户接受安装、更新、orsave。</span><span class="sxs-lookup"><span data-stu-id="d8595-293">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="d8595-294">-RootModule</span><span class="sxs-lookup"><span data-stu-id="d8595-294">-RootModule</span></span>

<span data-ttu-id="d8595-295">指定模块的主文件或根文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-295">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="d8595-296">输入脚本的文件名 (`.ps1`) 、脚本模块 (`.psm1`) 、模块清单 () `.psd1` 、程序集 (`.dll`) 、cmdlet 定义 XML 文件 (`.cdxml`) 或 () 工作流 `.xaml` 。</span><span class="sxs-lookup"><span data-stu-id="d8595-296">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="d8595-297">导入模块时，从根模块文件导出的成员将导入到调用方的会话状态中。</span><span class="sxs-lookup"><span data-stu-id="d8595-297">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="d8595-298">如果某个模块具有清单文件，并且未在 **RootModule** 项中指定任何根文件，则该清单将成为该模块的主文件，并且该模块将成为清单模块 (ModuleType = manifest) 。</span><span class="sxs-lookup"><span data-stu-id="d8595-298">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="d8595-299">若要从 `.psm1` `.dll` 具有清单的模块中的或文件中导出成员，必须在清单中的 **RootModule** 或 **NestedModules** 键的值中指定这些文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d8595-299">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="d8595-300">否则，不会导出它们的成员。</span><span class="sxs-lookup"><span data-stu-id="d8595-300">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="d8595-301">在 PowerShell 2.0 中，此密钥称为 **ModuleToProcess**。</span><span class="sxs-lookup"><span data-stu-id="d8595-301">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="d8595-302">可以使用 **RootModule** 参数名称或其 **ModuleToProcess** 别名。</span><span class="sxs-lookup"><span data-stu-id="d8595-302">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8595-303">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="d8595-303">-ScriptsToProcess</span></span>

<span data-ttu-id="d8595-304">指定 `.ps1` 导入模块时，在调用方的会话状态中运行的脚本 () 文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-304">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="d8595-305">可以像使用登录脚本一样使用这些脚本来准备环境。</span><span class="sxs-lookup"><span data-stu-id="d8595-305">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="d8595-306">若要指定在模块的会话状态中运行的脚本，请使用 **NestedModules** 键。</span><span class="sxs-lookup"><span data-stu-id="d8595-306">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="d8595-307">-Tags</span><span class="sxs-lookup"><span data-stu-id="d8595-307">-Tags</span></span>

<span data-ttu-id="d8595-308">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="d8595-308">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="d8595-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="d8595-309">-TypesToProcess</span></span>

<span data-ttu-id="d8595-310">指定 `.ps1xml` 导入模块时运行)  (类型文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-310">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="d8595-311">导入模块时，PowerShell 将运行 `Update-TypeData` 具有指定文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8595-311">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="d8595-312">由于类型文件不作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-312">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="d8595-313">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="d8595-313">-VariablesToExport</span></span>

<span data-ttu-id="d8595-314">指定模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="d8595-314">Specifies the variables that the module exports.</span></span> <span data-ttu-id="d8595-315">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d8595-315">Wildcards are permitted.</span></span>

<span data-ttu-id="d8595-316">可以使用此参数来限制由模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="d8595-316">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="d8595-317">它可以从导出的变量列表中删除变量，但不能将变量添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="d8595-317">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="d8595-318">如果省略此参数，则将 `New-ModuleManifest` 创建值为 (所有) 的 **VariablesToExport** 键 `*` ，这意味着该模块中定义的所有变量都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="d8595-318">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d8595-319">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8595-319">-Confirm</span></span>

<span data-ttu-id="d8595-320">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="d8595-320">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d8595-321">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8595-321">-WhatIf</span></span>

<span data-ttu-id="d8595-322">显示运行时将发生 `New-ModuleManifest` 的情况。</span><span class="sxs-lookup"><span data-stu-id="d8595-322">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="d8595-323">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="d8595-323">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d8595-324">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="d8595-324">-ClrVersion</span></span>

<span data-ttu-id="d8595-325">指定模块需要的 Microsoft .NET Framework 的公共语言运行时 (CLR) 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="d8595-325">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="d8595-326">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8595-326">CommonParameters</span></span>
<span data-ttu-id="d8595-327">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8595-327">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8595-328">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8595-328">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8595-329">输入</span><span class="sxs-lookup"><span data-stu-id="d8595-329">INPUTS</span></span>

### <span data-ttu-id="d8595-330">无</span><span class="sxs-lookup"><span data-stu-id="d8595-330">None</span></span>

<span data-ttu-id="d8595-331">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8595-331">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d8595-332">输出</span><span class="sxs-lookup"><span data-stu-id="d8595-332">OUTPUTS</span></span>

### <span data-ttu-id="d8595-333">None 或 System.String</span><span class="sxs-lookup"><span data-stu-id="d8595-333">None or System.String</span></span>

<span data-ttu-id="d8595-334">默认情况下， `New-ModuleManifest` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="d8595-334">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="d8595-335">但是，如果使用 **PassThru** 参数，则它将生成表示该模块清单的 **system.string** 对象。</span><span class="sxs-lookup"><span data-stu-id="d8595-335">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="d8595-336">注释</span><span class="sxs-lookup"><span data-stu-id="d8595-336">NOTES</span></span>

<span data-ttu-id="d8595-337">`New-ModuleManifest` 在 Windows 和非 Windows 平台上运行时，会创建 (`.psd1`) 文件编码为 **UTF8NoBOM** 的模块清单。</span><span class="sxs-lookup"><span data-stu-id="d8595-337">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="d8595-338">模块清单通常是可选的。</span><span class="sxs-lookup"><span data-stu-id="d8595-338">Module manifests are usually optional.</span></span> <span data-ttu-id="d8595-339">但是，若要导出安装在全局程序集缓存中的程序集，则模块清单是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8595-339">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="d8595-340">若要在目录中添加或更改文件 `$pshome\Modules` ，请以 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d8595-340">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="d8595-341">从 PowerShell 6.2 开始，PowerShell 将尝试加载在模块清单的 **FileList** 属性中列出的所有 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="d8595-341">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="d8595-342">本机 Dll 在进程中无法加载 **FileList** ，将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="d8595-342">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="d8595-343">所有托管的 Dll 都加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="d8595-343">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="d8595-344">此行为已在 PowerShell 7.1 中被删除。</span><span class="sxs-lookup"><span data-stu-id="d8595-344">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="d8595-345">在 PowerShell 2.0 中，许多参数 `New-ModuleManifest` 都是必需的，即使它们在模块清单中不是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8595-345">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="d8595-346">从 PowerShell 3.0 开始，只有 **Path** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="d8595-346">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="d8595-347">会话是 PowerShell 执行环境的一个实例。</span><span class="sxs-lookup"><span data-stu-id="d8595-347">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="d8595-348">一个会话可以具有一个或多个会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-348">A session can have one or more session states.</span></span> <span data-ttu-id="d8595-349">默认情况下，会话仅具有全局会话状态，但每个导入的模块都具有其自己的会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-349">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="d8595-350">会话状态允许模块中的命令在不影响全局会话状态的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="d8595-350">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="d8595-351">调用方的会话状态是要将模块导入到其中的会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-351">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="d8595-352">通常，它是指全局会话状态，但当某个模块导入嵌套模块时，调用方是该模块，而调用方的会话状态为模块的会话状态。</span><span class="sxs-lookup"><span data-stu-id="d8595-352">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="d8595-353">相关链接</span><span class="sxs-lookup"><span data-stu-id="d8595-353">RELATED LINKS</span></span>

[<span data-ttu-id="d8595-354">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="d8595-354">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="d8595-355">Get-Module</span><span class="sxs-lookup"><span data-stu-id="d8595-355">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="d8595-356">Import-Module</span><span class="sxs-lookup"><span data-stu-id="d8595-356">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="d8595-357">New-Module</span><span class="sxs-lookup"><span data-stu-id="d8595-357">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="d8595-358">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="d8595-358">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="d8595-359">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d8595-359">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="d8595-360">about_Modules</span><span class="sxs-lookup"><span data-stu-id="d8595-360">about_Modules</span></span>](./About/about_Modules.md)
