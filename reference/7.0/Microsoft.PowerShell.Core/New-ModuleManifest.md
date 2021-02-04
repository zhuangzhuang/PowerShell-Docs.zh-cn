---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 9bb687aa7f497dbf2c07633abddf4e1a17a9622e
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879195"
---
# <span data-ttu-id="7b452-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="7b452-103">New-ModuleManifest</span></span>

## <span data-ttu-id="7b452-104">摘要</span><span class="sxs-lookup"><span data-stu-id="7b452-104">SYNOPSIS</span></span>
<span data-ttu-id="7b452-105">创建新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="7b452-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b452-106">SYNTAX</span></span>

### <span data-ttu-id="7b452-107">全部</span><span class="sxs-lookup"><span data-stu-id="7b452-107">All</span></span>

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

## <span data-ttu-id="7b452-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7b452-108">DESCRIPTION</span></span>

<span data-ttu-id="7b452-109">`New-ModuleManifest`Cmdlet 将 () 文件创建新的模块清单 `.psd1` ，并填充其值，并将清单文件保存在指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="7b452-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="7b452-110">模块作者可以使用此 cmdlet 来为其模块创建清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="7b452-111">模块清单是 `.psd1` 包含哈希表的文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="7b452-112">哈希表中的键和值用于描述该模块的内容和属性、定义先决条件以及确定如何处理组件。</span><span class="sxs-lookup"><span data-stu-id="7b452-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="7b452-113">模块不需要清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="7b452-114">`New-ModuleManifest` 创建一个包含所有常用清单键的清单，以便您可以使用默认输出作为清单模板。</span><span class="sxs-lookup"><span data-stu-id="7b452-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="7b452-115">若要添加或更改值，或者添加此 cmdlet 未添加的模块键，请在文本编辑器中打开生成的文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="7b452-116">除了 **Path** 和 **PassThru** 以外，每个参数都将创建一个模块清单键及其值。</span><span class="sxs-lookup"><span data-stu-id="7b452-116">Each parameter, except for **Path** and **PassThru**, creates a module manifest key and its value.</span></span>
<span data-ttu-id="7b452-117">在模块清单中，仅 **ModuleVersion** 键是必需的。</span><span class="sxs-lookup"><span data-stu-id="7b452-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="7b452-118">除非在参数说明中指定，否则，如果从命令中省略某个参数，则将 `New-ModuleManifest` 为关联值创建一个不起作用的注释字符串。</span><span class="sxs-lookup"><span data-stu-id="7b452-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="7b452-119">在 PowerShell 2.0 中，系统将 `New-ModuleManifest` 提示你输入未在命令中指定的常用参数的值，以及所需的参数值。</span><span class="sxs-lookup"><span data-stu-id="7b452-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="7b452-120">从 PowerShell 3.0 开始， `New-ModuleManifest` 仅在未指定必需的参数值时提示。</span><span class="sxs-lookup"><span data-stu-id="7b452-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="7b452-121">如果计划在 PowerShell 库中发布模块，则清单必须包含特定属性的值。</span><span class="sxs-lookup"><span data-stu-id="7b452-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="7b452-122">有关详细信息，请参阅库文档中 [发布到 PowerShell 库的项的必需元数据](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 。</span><span class="sxs-lookup"><span data-stu-id="7b452-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="7b452-123">示例</span><span class="sxs-lookup"><span data-stu-id="7b452-123">EXAMPLES</span></span>

### <span data-ttu-id="7b452-124">示例 1-创建新的模块清单</span><span class="sxs-lookup"><span data-stu-id="7b452-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="7b452-125">此示例在 **Path** 参数指定的文件中创建一个新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="7b452-126">**PassThru** 参数将输出发送到管道和文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="7b452-127">该输出显示清单中的所有键的默认值。</span><span class="sxs-lookup"><span data-stu-id="7b452-127">The output shows the default values of all keys in the manifest.</span></span>

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

### <span data-ttu-id="7b452-128">示例 2-使用一些预填充的设置创建新清单</span><span class="sxs-lookup"><span data-stu-id="7b452-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="7b452-129">此示例将创建一个新的模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-129">This example creates a new module manifest.</span></span> <span data-ttu-id="7b452-130">它使用 **PowerShellVersion** 和 **AliasesToExport** 参数将值添加到相应的清单键。</span><span class="sxs-lookup"><span data-stu-id="7b452-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="7b452-131">示例 3-创建需要其他模块的清单</span><span class="sxs-lookup"><span data-stu-id="7b452-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="7b452-132">此示例使用字符串格式指定 **BitsTransfer** 模块的名称，使用哈希表格式指定 **PSScheduledJob** 模块的名称、 **GUID** 和版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID**, and a version of the **PSScheduledJob** module.</span></span>

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

<span data-ttu-id="7b452-133">此示例演示如何使用 **ModuleList**、 **RequiredModules** 和 **NestedModules** 参数的字符串和哈希表格式。</span><span class="sxs-lookup"><span data-stu-id="7b452-133">This example shows how to use the string and hash table formats of the **ModuleList**, **RequiredModules**, and **NestedModules** parameter.</span></span> <span data-ttu-id="7b452-134">可以将字符串和哈希表组合到同一参数值中。</span><span class="sxs-lookup"><span data-stu-id="7b452-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="7b452-135">示例 4-创建支持可更新帮助的清单</span><span class="sxs-lookup"><span data-stu-id="7b452-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="7b452-136">此示例使用 **HelpInfoUri** 参数在模块清单中创建 **HelpInfoUri** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="7b452-137">参数和密钥的值必须以 **http** 或 **https** 开头。</span><span class="sxs-lookup"><span data-stu-id="7b452-137">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="7b452-138">此值会向可更新帮助系统指示该模块的 HelpInfo XML 可更新帮助信息文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7b452-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="7b452-139">有关可更新帮助的信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="7b452-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="7b452-140">有关 HelpInfo XML 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。</span><span class="sxs-lookup"><span data-stu-id="7b452-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="7b452-141">示例 5-获取模块信息</span><span class="sxs-lookup"><span data-stu-id="7b452-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="7b452-142">此示例演示如何获取模块的配置值。</span><span class="sxs-lookup"><span data-stu-id="7b452-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="7b452-143">模块清单中的值反映在 module 对象的属性值中。</span><span class="sxs-lookup"><span data-stu-id="7b452-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="7b452-144">`Get-Module`Cmdlet 用于获取使用 **List** 参数的 **Microsoft PowerShell 诊断** 模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="7b452-145">命令将模块发送到 `Format-List` cmdlet，以显示 module 对象的所有属性和值。</span><span class="sxs-lookup"><span data-stu-id="7b452-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

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

## <span data-ttu-id="7b452-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b452-146">PARAMETERS</span></span>

### <span data-ttu-id="7b452-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="7b452-147">-AliasesToExport</span></span>

<span data-ttu-id="7b452-148">指定模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="7b452-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="7b452-149">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-149">Wildcards are permitted.</span></span>

<span data-ttu-id="7b452-150">可以使用此参数来限制由模块导出的别名。</span><span class="sxs-lookup"><span data-stu-id="7b452-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="7b452-151">它可以从导出的别名列表中删除别名，但不能将别名添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="7b452-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="7b452-152">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **AliasesToExport** 键 `*` ，这意味着该模块中定义的所有别名都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="7b452-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="7b452-153">-作者</span><span class="sxs-lookup"><span data-stu-id="7b452-153">-Author</span></span>

<span data-ttu-id="7b452-154">指定模块作者。</span><span class="sxs-lookup"><span data-stu-id="7b452-154">Specifies the module author.</span></span>

<span data-ttu-id="7b452-155">如果省略此参数，则将 `New-ModuleManifest` 创建具有当前用户名称的 **Author** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

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

### <span data-ttu-id="7b452-156">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="7b452-156">-ClrVersion</span></span>

<span data-ttu-id="7b452-157">指定模块需要的 Microsoft .NET Framework 的公共语言运行时 (CLR) 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-157">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="7b452-158">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="7b452-158">-CmdletsToExport</span></span>

<span data-ttu-id="7b452-159">指定模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b452-159">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="7b452-160">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-160">Wildcards are permitted.</span></span>

<span data-ttu-id="7b452-161">可以使用此参数来限制由模块导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b452-161">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="7b452-162">它可以从导出的 cmdlet 列表中删除 cmdlet，但不能将 cmdlet 添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="7b452-162">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="7b452-163">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **CmdletsToExport** 键 `*` ，这意味着该模块中定义的所有 cmdlet 都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="7b452-163">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="7b452-164">-公司名称</span><span class="sxs-lookup"><span data-stu-id="7b452-164">-CompanyName</span></span>

<span data-ttu-id="7b452-165">标识创建了该模块的公司或供应商。</span><span class="sxs-lookup"><span data-stu-id="7b452-165">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="7b452-166">如果省略此参数，则将 `New-ModuleManifest` 创建值为 "Unknown" 的 " **公司名称** " 密钥。</span><span class="sxs-lookup"><span data-stu-id="7b452-166">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

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

### <span data-ttu-id="7b452-167">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="7b452-167">-CompatiblePSEditions</span></span>

<span data-ttu-id="7b452-168">指定模块的兼容 PSEditions。</span><span class="sxs-lookup"><span data-stu-id="7b452-168">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="7b452-169">有关 PSEdition 的信息，请参阅 [具有兼容的 PowerShell 版本的模块](/powershell/scripting/gallery/concepts/module-psedition-support)。</span><span class="sxs-lookup"><span data-stu-id="7b452-169">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="7b452-170">-版权所有</span><span class="sxs-lookup"><span data-stu-id="7b452-170">-Copyright</span></span>

<span data-ttu-id="7b452-171">指定模块的版权声明。</span><span class="sxs-lookup"><span data-stu-id="7b452-171">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="7b452-172">如果省略此参数，则 `New-ModuleManifest` 将创建值为的 **版权** 密钥， `(c) <year> <username>. All rights reserved.` 其中 `<year>` 为当前年份， `<username>` 是 **作者** 密钥的值。</span><span class="sxs-lookup"><span data-stu-id="7b452-172">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

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

### <span data-ttu-id="7b452-173">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="7b452-173">-DefaultCommandPrefix</span></span>

<span data-ttu-id="7b452-174">指定在将模块中的所有命令导入到会话中时在该模块中的所有命令的名词前面预置的前缀。</span><span class="sxs-lookup"><span data-stu-id="7b452-174">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="7b452-175">输入前缀字符串。</span><span class="sxs-lookup"><span data-stu-id="7b452-175">Enter a prefix string.</span></span> <span data-ttu-id="7b452-176">前缀可防止用户会话中的命令名称发生冲突。</span><span class="sxs-lookup"><span data-stu-id="7b452-176">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="7b452-177">模块用户可以通过指定 cmdlet 的 **prefix** 参数来重写此前缀 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-177">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="7b452-178">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="7b452-178">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7b452-179">-Description</span><span class="sxs-lookup"><span data-stu-id="7b452-179">-Description</span></span>

<span data-ttu-id="7b452-180">描述模块的内容。</span><span class="sxs-lookup"><span data-stu-id="7b452-180">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="7b452-181">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="7b452-181">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="7b452-182">指定模块需要的 Microsoft .NET Framework 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-182">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="7b452-183">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="7b452-183">-DscResourcesToExport</span></span>

<span data-ttu-id="7b452-184">指定模块导出 (DSC) 资源的所需状态配置。</span><span class="sxs-lookup"><span data-stu-id="7b452-184">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="7b452-185">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-185">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="7b452-186">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="7b452-186">-ExternalModuleDependencies</span></span>

<span data-ttu-id="7b452-187">此模块所依赖的外部模块的列表。</span><span class="sxs-lookup"><span data-stu-id="7b452-187">A list of external modules that this module is depends on.</span></span>

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

### <span data-ttu-id="7b452-188">-FileList</span><span class="sxs-lookup"><span data-stu-id="7b452-188">-FileList</span></span>

<span data-ttu-id="7b452-189">指定模块中包括的所有项。</span><span class="sxs-lookup"><span data-stu-id="7b452-189">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="7b452-190">此键专门用于充当模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-190">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="7b452-191">当发布模块时，将包含该键中列出的文件，但不会自动导出任何函数。</span><span class="sxs-lookup"><span data-stu-id="7b452-191">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="7b452-192">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="7b452-192">-FormatsToProcess</span></span>

<span data-ttu-id="7b452-193">指定 `.ps1xml` 导入模块时运行)  (格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-193">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="7b452-194">导入模块时，PowerShell 将 `Update-FormatData` 使用指定的文件运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b452-194">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="7b452-195">由于格式设置文件没有作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-195">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="7b452-196">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="7b452-196">-FunctionsToExport</span></span>

<span data-ttu-id="7b452-197">指定模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="7b452-197">Specifies the functions that the module exports.</span></span> <span data-ttu-id="7b452-198">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-198">Wildcards are permitted.</span></span>

<span data-ttu-id="7b452-199">可以使用此参数来限制由模块导出的函数。</span><span class="sxs-lookup"><span data-stu-id="7b452-199">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="7b452-200">它可以从导出的别名列表中删除函数，但不能将函数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="7b452-200">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="7b452-201">如果省略此参数，则将 `New-ModuleManifest` 创建一个值为 (all) 的 **FunctionsToExport** 键 `*` ，这意味着该模块中定义的所有函数都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="7b452-201">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="7b452-202">-Guid</span><span class="sxs-lookup"><span data-stu-id="7b452-202">-Guid</span></span>

<span data-ttu-id="7b452-203">指定模块的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="7b452-203">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="7b452-204">可以使用 **GUID** 来区分名称相同的模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-204">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="7b452-205">如果省略此参数，则 `New-ModuleManifest` 在清单中创建 **guid** 密钥并为值生成 **guid** 。</span><span class="sxs-lookup"><span data-stu-id="7b452-205">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="7b452-206">若要在 PowerShell 中创建新的 **GUID** ，请键入 `[guid]::NewGuid()` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-206">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="7b452-207">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="7b452-207">-HelpInfoUri</span></span>

<span data-ttu-id="7b452-208">指定模块的 HelpInfo XML 文件的 internet 地址。</span><span class="sxs-lookup"><span data-stu-id="7b452-208">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="7b452-209">输入以 **http** 或 **HTTPS** 开头 (URI) 的统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="7b452-209">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="7b452-210">HelpInfo XML 文件支持 PowerShell 3.0 中引入的可更新帮助功能。</span><span class="sxs-lookup"><span data-stu-id="7b452-210">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="7b452-211">它包含有关该模块的可下载帮助文件的位置，以及每个支持的区域设置的最新帮助文件的版本号的信息。</span><span class="sxs-lookup"><span data-stu-id="7b452-211">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="7b452-212">有关可更新帮助的信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="7b452-212">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="7b452-213">有关 HelpInfo XML 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。</span><span class="sxs-lookup"><span data-stu-id="7b452-213">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="7b452-214">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="7b452-214">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7b452-215">-IconUri</span><span class="sxs-lookup"><span data-stu-id="7b452-215">-IconUri</span></span>

<span data-ttu-id="7b452-216">指定模块的图标的 URL。</span><span class="sxs-lookup"><span data-stu-id="7b452-216">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="7b452-217">指定的图标显示在模块的库网页上。</span><span class="sxs-lookup"><span data-stu-id="7b452-217">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="7b452-218">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="7b452-218">-LicenseUri</span></span>

<span data-ttu-id="7b452-219">指定模块的许可条款 URL。</span><span class="sxs-lookup"><span data-stu-id="7b452-219">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="7b452-220">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="7b452-220">-ModuleList</span></span>

<span data-ttu-id="7b452-221">列出此模块中包括的所有模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-221">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="7b452-222">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="7b452-222">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="7b452-223">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-223">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="7b452-224">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="7b452-224">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="7b452-225">此键专门用于充当模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-225">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="7b452-226">不会自动处理此键的值中列出的模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-226">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="7b452-227">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="7b452-227">-ModuleVersion</span></span>

<span data-ttu-id="7b452-228">指定模块的版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-228">Specifies the module's version.</span></span>

<span data-ttu-id="7b452-229">此参数不是必需的，但清单中需要 **ModuleVersion** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-229">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="7b452-230">如果省略此参数，则将 `New-ModuleManifest` 创建值为1.0 的 **ModuleVersion** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-230">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

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

### <span data-ttu-id="7b452-231">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="7b452-231">-NestedModules</span></span>

<span data-ttu-id="7b452-232">指定脚本模块 (`.psm1` `.dll` 导入模块的会话状态中 () 的) 和二进制模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-232">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="7b452-233">**NestedModules** 键中的文件按照其在值中的列出顺序运行。</span><span class="sxs-lookup"><span data-stu-id="7b452-233">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="7b452-234">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="7b452-234">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="7b452-235">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-235">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="7b452-236">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="7b452-236">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="7b452-237">通常情况下，嵌套模块包含根模块需用于内部处理的命令。</span><span class="sxs-lookup"><span data-stu-id="7b452-237">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="7b452-238">默认情况下，嵌套模块中的命令将从模块的会话状态导出到调用方的会话状态中，但根模块可以限制它导出的命令。</span><span class="sxs-lookup"><span data-stu-id="7b452-238">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="7b452-239">例如，使用 `Export-ModuleMember` 命令。</span><span class="sxs-lookup"><span data-stu-id="7b452-239">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="7b452-240">模块会话状态中的嵌套模块可用于根模块，但 `Get-Module` 在调用方的会话状态中，命令不会返回这些模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-240">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="7b452-241">`.ps1` **NestedModules** 键中列出的脚本 () 在模块的会话状态中运行，而不是在调用方的会话状态中运行。</span><span class="sxs-lookup"><span data-stu-id="7b452-241">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="7b452-242">若要在调用方的会话状态中运行脚本，请在清单的 **ScriptsToProcess** 键的值中列出脚本文件名。</span><span class="sxs-lookup"><span data-stu-id="7b452-242">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="7b452-243">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7b452-243">-PassThru</span></span>

<span data-ttu-id="7b452-244">将生成的模块清单写入控制台并创建 `.psd1` 文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-244">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="7b452-245">默认情况下，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="7b452-245">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="7b452-246">-Path</span><span class="sxs-lookup"><span data-stu-id="7b452-246">-Path</span></span>

<span data-ttu-id="7b452-247">指定新模块清单的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="7b452-247">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="7b452-248">输入文件扩展名为的路径和文件名 `.psd1` ，例如 `$pshome\Modules\MyModule\MyModule.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-248">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="7b452-249">**Path** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="7b452-249">The **Path** parameter is required.</span></span>

<span data-ttu-id="7b452-250">如果指定了现有文件的路径，则将 `New-ModuleManifest` 替换该文件而不发出警告，除非该文件具有只读属性。</span><span class="sxs-lookup"><span data-stu-id="7b452-250">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="7b452-251">清单应位于模块的目录中，清单文件的名称应与模块目录名称相同，但具有 `.psd1` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="7b452-251">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="7b452-252">不能使用变量（如 `$PSHOME` 或 `$HOME` ）来响应 **Path** 参数值的提示。</span><span class="sxs-lookup"><span data-stu-id="7b452-252">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="7b452-253">若要使用变量，请将 **Path** 参数包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="7b452-253">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="7b452-254">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="7b452-254">-PowerShellHostName</span></span>

<span data-ttu-id="7b452-255">指定模块所需的 PowerShell 主机程序的名称。</span><span class="sxs-lookup"><span data-stu-id="7b452-255">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="7b452-256">输入主机程序的名称，例如 **Windows PowerShell ISE host** or **ConsoleHost**。</span><span class="sxs-lookup"><span data-stu-id="7b452-256">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="7b452-257">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-257">Wildcards aren't permitted.</span></span>

<span data-ttu-id="7b452-258">若要查找主机程序的名称，请在 "程序" 中键入 `$Host.Name` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-258">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="7b452-259">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="7b452-259">-PowerShellHostVersion</span></span>

<span data-ttu-id="7b452-260">指定适用于该模块的 PowerShell 主机程序的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-260">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="7b452-261">输入版本号，例如 1.1。</span><span class="sxs-lookup"><span data-stu-id="7b452-261">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="7b452-262">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="7b452-262">-PowerShellVersion</span></span>

<span data-ttu-id="7b452-263">指定适用于此模块的 PowerShell 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-263">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="7b452-264">例如，可以输入1.0、2.0 或3.0 作为参数的值。</span><span class="sxs-lookup"><span data-stu-id="7b452-264">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span> <span data-ttu-id="7b452-265">它必须采用 X. X 格式。</span><span class="sxs-lookup"><span data-stu-id="7b452-265">It must be in an X.X format.</span></span> <span data-ttu-id="7b452-266">例如，如果你提交 `5` ，则 PowerShell 将引发错误。</span><span class="sxs-lookup"><span data-stu-id="7b452-266">For example, if you submit `5`, PowerShell will throw an error.</span></span>

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

### <span data-ttu-id="7b452-267">-预发行版</span><span class="sxs-lookup"><span data-stu-id="7b452-267">-Prerelease</span></span>

<span data-ttu-id="7b452-268">此模块的预发行版本字符串。</span><span class="sxs-lookup"><span data-stu-id="7b452-268">Prerelease string of this module.</span></span> <span data-ttu-id="7b452-269">添加预发布字符串会将模块标识为预发行版本。</span><span class="sxs-lookup"><span data-stu-id="7b452-269">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="7b452-270">在将模块发布到 PowerShell 库时，将使用此数据来标识预发行包。</span><span class="sxs-lookup"><span data-stu-id="7b452-270">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="7b452-271">若要从库中获取预发行包，必须在 PowerShellGet 命令中使用 **AllowPrerelease** 参数 `Find-Module` ： `Install-Module` 、 `Update-Module` 和 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-271">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="7b452-272">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="7b452-272">-PrivateData</span></span>

<span data-ttu-id="7b452-273">指定导入模块时传递给模块的数据。</span><span class="sxs-lookup"><span data-stu-id="7b452-273">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="7b452-274">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="7b452-274">-ProcessorArchitecture</span></span>

<span data-ttu-id="7b452-275">指定模块需要的处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="7b452-275">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="7b452-276">有效值为 x86、AMD64、IA64、MSIL 和 None (未知或未指定的) 。</span><span class="sxs-lookup"><span data-stu-id="7b452-276">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="7b452-277">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="7b452-277">-ProjectUri</span></span>

<span data-ttu-id="7b452-278">指定有关此项目的网页的 URL。</span><span class="sxs-lookup"><span data-stu-id="7b452-278">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="7b452-279">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="7b452-279">-ReleaseNotes</span></span>

<span data-ttu-id="7b452-280">指定发行说明。</span><span class="sxs-lookup"><span data-stu-id="7b452-280">Specifies release notes.</span></span>

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

### <span data-ttu-id="7b452-281">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="7b452-281">-RequiredAssemblies</span></span>

<span data-ttu-id="7b452-282">指定模块需要的程序集 (`.dll`) 文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-282">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="7b452-283">输入程序集文件名。</span><span class="sxs-lookup"><span data-stu-id="7b452-283">Enter the assembly file names.</span></span>
<span data-ttu-id="7b452-284">PowerShell 在更新类型或格式、导入嵌套模块或导入在 **RootModule** 项的值中指定的模块文件之前加载指定的程序集。</span><span class="sxs-lookup"><span data-stu-id="7b452-284">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="7b452-285">使用此参数可列出模块所需要的所有程序集，包括必须加载以更新在 **FormatsToProcess** 或 **TypesToProcess** 键中列出的任何格式设置文件或类型文件的程序集，即使另将这些程序集列为 **NestedModules** 键中的二进制模块也是如此。</span><span class="sxs-lookup"><span data-stu-id="7b452-285">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="7b452-286">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="7b452-286">-RequiredModules</span></span>

<span data-ttu-id="7b452-287">指定必须处于全局会话状态的模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-287">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="7b452-288">如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="7b452-288">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="7b452-289">如果所需模块不可用，则该 `Import-Module` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="7b452-289">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="7b452-290">以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。</span><span class="sxs-lookup"><span data-stu-id="7b452-290">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="7b452-291">哈希表也可能具有一个可选的 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-291">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="7b452-292">可以将字符串和哈希表组合到参数值中。</span><span class="sxs-lookup"><span data-stu-id="7b452-292">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="7b452-293">在 PowerShell 2.0 中， `Import-Module` 不会自动导入所需的模块。</span><span class="sxs-lookup"><span data-stu-id="7b452-293">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="7b452-294">它只会验证所需模块是否处于全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-294">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="7b452-295">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="7b452-295">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="7b452-296">一个标志，用于指示该模块是否需要显式用户接受安装、更新、orsave。</span><span class="sxs-lookup"><span data-stu-id="7b452-296">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="7b452-297">-RootModule</span><span class="sxs-lookup"><span data-stu-id="7b452-297">-RootModule</span></span>

<span data-ttu-id="7b452-298">指定模块的主文件或根文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-298">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="7b452-299">输入脚本的文件名 (`.ps1`) 、脚本模块 (`.psm1`) 、模块清单 () `.psd1` 、程序集 (`.dll`) 、cmdlet 定义 XML 文件 (`.cdxml`) 或 () 工作流 `.xaml` 。</span><span class="sxs-lookup"><span data-stu-id="7b452-299">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="7b452-300">导入模块时，从根模块文件导出的成员将导入到调用方的会话状态中。</span><span class="sxs-lookup"><span data-stu-id="7b452-300">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="7b452-301">如果某个模块具有清单文件，并且未在 **RootModule** 项中指定任何根文件，则该清单将成为该模块的主文件，并且该模块将成为清单模块 (ModuleType = manifest) 。</span><span class="sxs-lookup"><span data-stu-id="7b452-301">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="7b452-302">若要从 `.psm1` `.dll` 具有清单的模块中的或文件中导出成员，必须在清单中的 **RootModule** 或 **NestedModules** 键的值中指定这些文件的名称。</span><span class="sxs-lookup"><span data-stu-id="7b452-302">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="7b452-303">否则，不会导出它们的成员。</span><span class="sxs-lookup"><span data-stu-id="7b452-303">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="7b452-304">在 PowerShell 2.0 中，此密钥称为 **ModuleToProcess**。</span><span class="sxs-lookup"><span data-stu-id="7b452-304">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="7b452-305">可以使用 **RootModule** 参数名称或其 **ModuleToProcess** 别名。</span><span class="sxs-lookup"><span data-stu-id="7b452-305">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

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

### <span data-ttu-id="7b452-306">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="7b452-306">-ScriptsToProcess</span></span>

<span data-ttu-id="7b452-307">指定 `.ps1` 导入模块时，在调用方的会话状态中运行的脚本 () 文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-307">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="7b452-308">可以像使用登录脚本一样使用这些脚本来准备环境。</span><span class="sxs-lookup"><span data-stu-id="7b452-308">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="7b452-309">若要指定在模块的会话状态中运行的脚本，请使用 **NestedModules** 键。</span><span class="sxs-lookup"><span data-stu-id="7b452-309">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="7b452-310">-Tags</span><span class="sxs-lookup"><span data-stu-id="7b452-310">-Tags</span></span>

<span data-ttu-id="7b452-311">指定标记的数组。</span><span class="sxs-lookup"><span data-stu-id="7b452-311">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="7b452-312">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="7b452-312">-TypesToProcess</span></span>

<span data-ttu-id="7b452-313">指定 `.ps1xml` 导入模块时运行)  (类型文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-313">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="7b452-314">导入模块时，PowerShell 将运行 `Update-TypeData` 具有指定文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b452-314">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="7b452-315">由于类型文件不作用域，因此它们会影响会话中的所有会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-315">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="7b452-316">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="7b452-316">-VariablesToExport</span></span>

<span data-ttu-id="7b452-317">指定模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="7b452-317">Specifies the variables that the module exports.</span></span> <span data-ttu-id="7b452-318">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7b452-318">Wildcards are permitted.</span></span>

<span data-ttu-id="7b452-319">可以使用此参数来限制由模块导出的变量。</span><span class="sxs-lookup"><span data-stu-id="7b452-319">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="7b452-320">它可以从导出的变量列表中删除变量，但不能将变量添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="7b452-320">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="7b452-321">如果省略此参数，则将 `New-ModuleManifest` 创建值为 (所有) 的 **VariablesToExport** 键 `*` ，这意味着该模块中定义的所有变量都将由清单导出。</span><span class="sxs-lookup"><span data-stu-id="7b452-321">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="7b452-322">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7b452-322">-Confirm</span></span>

<span data-ttu-id="7b452-323">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="7b452-323">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7b452-324">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7b452-324">-WhatIf</span></span>

<span data-ttu-id="7b452-325">显示运行时将发生 `New-ModuleManifest` 的情况。</span><span class="sxs-lookup"><span data-stu-id="7b452-325">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="7b452-326">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="7b452-326">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7b452-327">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b452-327">CommonParameters</span></span>

<span data-ttu-id="7b452-328">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7b452-328">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b452-329">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7b452-329">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b452-330">输入</span><span class="sxs-lookup"><span data-stu-id="7b452-330">INPUTS</span></span>

### <span data-ttu-id="7b452-331">无</span><span class="sxs-lookup"><span data-stu-id="7b452-331">None</span></span>

<span data-ttu-id="7b452-332">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b452-332">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7b452-333">输出</span><span class="sxs-lookup"><span data-stu-id="7b452-333">OUTPUTS</span></span>

### <span data-ttu-id="7b452-334">None 或 System.String</span><span class="sxs-lookup"><span data-stu-id="7b452-334">None or System.String</span></span>

<span data-ttu-id="7b452-335">默认情况下， `New-ModuleManifest` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="7b452-335">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="7b452-336">但是，如果使用 **PassThru** 参数，则它将生成表示该模块清单的 **system.string** 对象。</span><span class="sxs-lookup"><span data-stu-id="7b452-336">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="7b452-337">注释</span><span class="sxs-lookup"><span data-stu-id="7b452-337">NOTES</span></span>

<span data-ttu-id="7b452-338">`New-ModuleManifest` 在 Windows 和非 Windows 平台上运行时，会创建 (`.psd1`) 文件编码为 **UTF8NoBOM** 的模块清单。</span><span class="sxs-lookup"><span data-stu-id="7b452-338">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="7b452-339">模块清单通常是可选的。</span><span class="sxs-lookup"><span data-stu-id="7b452-339">Module manifests are usually optional.</span></span> <span data-ttu-id="7b452-340">但是，若要导出安装在全局程序集缓存中的程序集，则模块清单是必需的。</span><span class="sxs-lookup"><span data-stu-id="7b452-340">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="7b452-341">若要在目录中添加或更改文件 `$pshome\Modules` ，请以 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7b452-341">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="7b452-342">从 PowerShell 6.2 开始，PowerShell 将尝试加载在模块清单的 **FileList** 属性中列出的所有 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="7b452-342">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="7b452-343">本机 Dll 在进程中无法加载 **FileList** ，将忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="7b452-343">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="7b452-344">所有托管的 Dll 都加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="7b452-344">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="7b452-345">此行为已在 PowerShell 7.1 中被删除。</span><span class="sxs-lookup"><span data-stu-id="7b452-345">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="7b452-346">在 PowerShell 2.0 中，许多参数 `New-ModuleManifest` 都是必需的，即使它们在模块清单中不是必需的。</span><span class="sxs-lookup"><span data-stu-id="7b452-346">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="7b452-347">从 PowerShell 3.0 开始，只有 **Path** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="7b452-347">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="7b452-348">会话是 PowerShell 执行环境的一个实例。</span><span class="sxs-lookup"><span data-stu-id="7b452-348">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="7b452-349">一个会话可以具有一个或多个会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-349">A session can have one or more session states.</span></span> <span data-ttu-id="7b452-350">默认情况下，会话仅具有全局会话状态，但每个导入的模块都具有其自己的会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-350">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="7b452-351">会话状态允许模块中的命令在不影响全局会话状态的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="7b452-351">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="7b452-352">调用方的会话状态是要将模块导入到其中的会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-352">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="7b452-353">通常，它是指全局会话状态，但当某个模块导入嵌套模块时，调用方是该模块，而调用方的会话状态为模块的会话状态。</span><span class="sxs-lookup"><span data-stu-id="7b452-353">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="7b452-354">相关链接</span><span class="sxs-lookup"><span data-stu-id="7b452-354">RELATED LINKS</span></span>

[<span data-ttu-id="7b452-355">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="7b452-355">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="7b452-356">Get-Module</span><span class="sxs-lookup"><span data-stu-id="7b452-356">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="7b452-357">Import-Module</span><span class="sxs-lookup"><span data-stu-id="7b452-357">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="7b452-358">New-Module</span><span class="sxs-lookup"><span data-stu-id="7b452-358">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="7b452-359">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="7b452-359">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="7b452-360">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="7b452-360">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="7b452-361">about_Modules</span><span class="sxs-lookup"><span data-stu-id="7b452-361">about_Modules</span></span>](./About/about_Modules.md)
