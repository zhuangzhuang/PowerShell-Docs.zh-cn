---
ms.date: 01/04/2021
ms.topic: reference
title: 如何编写 PowerShell 模块清单
description: 如何编写 PowerShell 模块清单
ms.openlocfilehash: 0270b9b3745b7ffd187f2089414ea7759515d96b
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563309"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何编写 PowerShell 模块清单

编写 PowerShell 模块后，可以添加一个可选模块清单，其中包含有关该模块的信息。 例如，您可以描述该作者，在模块中指定文件 (如嵌套的模块) ，运行脚本以自定义用户的环境、加载类型和格式设置文件、定义系统要求以及限制模块导出的成员。

## <a name="creating-a-module-manifest"></a>创建模块清单

**模块清单** 是一种 PowerShell 数据文件 (`.psd1`) ，用于描述模块的内容并确定如何处理模块。 清单文件是一个文本文件，其中包含键和值的哈希表。 您可以通过将清单文件命名为与模块相同的方式并将清单存储在模块的根目录中，将清单文件链接到模块。

对于只包含单个 `.psm1` 或二元程序集的简单模块，模块清单是可选的。 但建议尽可能使用模块清单，因为它们有助于您组织代码和维护版本信息。 并且，需要使用模块清单来导出 [全局程序集缓存](/dotnet/framework/app-domains/gac)中安装的程序集。 支持可更新帮助功能的模块还需要模块清单。 可更新帮助使用模块清单中的 **HelpInfoUri** 键来查找帮助信息 (HelpInfo XML) 文件，其中包含模块的已更新帮助文件的位置。 有关可更新帮助的详细信息，请参阅 [支持可更新帮助](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>创建和使用模块清单

1. 创建模块清单的最佳做法是使用 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet。 可以使用参数指定一个或多个清单的默认键和值。 唯一的要求是对文件进行命名。 `New-ModuleManifest` 使用指定的值创建模块清单，并包含剩余的键及其默认值。 如果需要创建多个模块，请使用 `New-ModuleManifest` 创建可针对不同模块进行修改的模块清单模板。 有关默认模块清单的示例，请参阅 [示例模块清单](#sample-module-manifest)。

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   一种替代方法是使用 **ModuleVersion** 中所需的最少信息手动创建模块清单的哈希表。 使用与模块相同的名称保存文件，然后使用 `.psd1` 文件扩展名。 然后，可以编辑该文件并添加适当的键和值。

1. 在清单文件中添加所需的任何其他元素。

   若要编辑清单文件，请使用你喜欢的任何文本编辑器。 但是，清单文件是包含代码的脚本文件，因此你可能想要在脚本或开发环境（例如 Visual Studio Code）中进行编辑。 清单文件的所有元素都是可选的，但 **ModuleVersion** 编号除外。

   有关可包含在模块清单中的键和值的说明，请参阅 [模块清单元素](#module-manifest-elements) 表。 有关详细信息，请参阅 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 中的参数说明。

1. 若要解决基本模块清单元素可能未涵盖的任何方案，可以选择将其他代码添加到模块清单中。

   出于安全考虑，PowerShell 仅在模块清单文件中运行一小部分可用操作。 通常，可以使用 `if` 语句、算术运算符和比较运算符以及基本 PowerShell 数据类型。

1. 创建模块清单后，可以对其进行测试，以确认清单中描述的任何路径都是正确的。 若要测试模块清单，请使用 [new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)。

   `Test-ModuleManifest myModuleName.psd1`

1. 请确保模块清单位于包含模块的目录的顶层。

   将模块复制到系统并将其导入时，PowerShell 将使用模块清单来导入模块。

1. 或者，您可以通过以点为模型的方式 [调用 import-module，](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 直接测试模块清单。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模块清单元素

下表描述了可在模块清单中包含的元素。

|元素|默认|说明|
|-------------|-------------|-----------------|
|**RootModule**<br /> 类型：`String`|`<empty string>`|与此清单关联的脚本模块或二进制模块文件。 以前版本的 PowerShell 调用此元素为 **ModuleToProcess**。<br /> 根模块的可能类型可以是空的，这会创建 **清单** 模块、脚本模块的名称 (`.psm1`) ，或者二进制模块 (`.exe` 或) 的名称 `.dll` 。 在此元素中将模块清单的名称 (`.psd1`) 或脚本文件 (`.ps1`) 会导致错误。 <br /> 示例： `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> 类型：`Version`|`'0.0.1'`|此模块的版本号。 如果未指定值， `New-ModuleManifest`   将使用默认值。 例如，该字符串必须能够转换为类型 `Version` `#.#.#.#` 。 `Import-Module` 加载它在与该名称匹配的 **$PSModulePath** 上找到的第一个模块，其中至少有一个 **ModuleVersion** 作为 **MinimumVersion** 参数。 若要导入特定版本，请使用 `Import-Module` cmdlet 的 **RequiredVersion** 参数。<br /> 示例： `ModuleVersion = '1.0'`|
|**GUID**<br /> 类型：`GUID`|`'<GUID>'`|用于唯一标识此模块的 ID。 如果未指定值， `New-ModuleManifest` 则将值自动生成。 当前无法按 **GUID** 导入模块。 <br /> 示例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**作者**<br /> 类型：`String`|`'<Current user>'`|此模块的作者。 如果未指定值，则 `New-ModuleManifest` 将使用当前用户。 <br /> 示例： `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> 类型：`String`|`'Unknown'`|此模块的公司或供应商。 如果未指定值， `New-ModuleManifest` 将使用默认值。<br /> 示例： `CompanyName = 'Fabrikam'`|
|**版权**<br /> 类型：`String`|`'(c) <Author>. All rights reserved.'`| 此模块的版权声明。 如果未指定值，则 `New-ModuleManifest` 使用当前用户作为的默认值 `<Author>` 。 若要指定作者，请使用 **author** 参数。 <br /> 示例： `Copyright = '2019 AuthorName. All rights reserved.'`|
|**说明**<br /> 类型：`String`|`<empty string>`|此模块提供的功能的说明。<br /> 示例： `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> 类型：`Version`|`<empty string>`|此模块所需的最小 PowerShell 引擎版本。 有效值为1.0、2.0、3.0、4.0、5.0、5.1、6.0、6.1、6.2、7.0 和7.1。<br /> 示例： `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> 类型：`String`|`<empty string>`|此模块所需的 PowerShell 主机的名称。 此名称由 PowerShell 提供。 若要查找主机程序的名称，请在 "程序" 中键入： `$host.name` 。<br /> 示例： `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> 类型：`Version`|`<empty string>`|此模块所需的最小 PowerShell 主机版本。<br /> 示例： `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> 类型：`Version`|`<empty string>`|此模块所需的 Microsoft .NET Framework 的最低版本。 此先决条件仅适用于 PowerShell 桌面版，如 PowerShell 5.1。<br /> 示例： `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> 类型：`Version`|`<empty string>`|此模块所需 (CLR) 的公共语言运行时的最低版本。 此先决条件仅适用于 PowerShell 桌面版，如 PowerShell 5.1。<br /> 示例： `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> 类型：`ProcessorArchitecture`|`<empty string>`|此模块需要的处理器体系结构 (无、X86、Amd64) 。 有效值为 x86、AMD64、Arm、IA64、MSIL 和 None (未知或未指定的) 。<br /> 示例： `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> 类型：`Object[]`|`@()`|在导入此模块之前，必须导入到全局环境中的模块。 这会加载列出的任何模块，除非已将其加载。 例如，一些模块可能已由其他模块加载。 可以使用而不是来指定要加载的特定版本 `RequiredVersion` `ModuleVersion` 。 使用时， `ModuleVersion` 它将加载最新版本，最小为指定版本。 可以将字符串和哈希表组合到参数值中。<br /> 示例：`RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> 示例：`RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> 类型：`String[]`|`@()`|必须在导入此模块之前加载的程序集。 指定模块所需的程序集 (`.dll`) 文件名。<br /> PowerShell 在更新类型或格式、导入嵌套模块或导入在 RootModule 项的值中指定的模块文件之前加载指定的程序集。 使用此参数可列出模块所需的所有程序集。<br /> 示例： `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> 类型：`String[]`|`@()`|脚本 (`.ps1` 在导入模块时，在调用方的会话状态中运行) 文件。 这可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 您可以使用这些脚本来准备环境，就像您可以在脚本中使用一样。<br /> 在加载清单中列出的任何模块之前，将运行这些脚本。 <br /> 示例： `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> 类型：`String[]`|`@()`|`.ps1xml`导入此模块时) 要加载 (类型文件。 <br /> 示例： `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> 类型：`String[]`|`@()`|`.ps1xml`导入此模块时要加载 () 的格式化文件。 <br /> 示例： `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> 类型：`Object[]`|`@()`|要作为 **RootModule** 中指定的模块的嵌套模块导入的模块 (Alias：**ModuleToProcess**) 。<br /> 向此元素添加模块名称类似于 `Import-Module` 从脚本或程序集代码中调用。 使用清单文件的主要区别是，可以更方便地查看正在加载的内容。 而且，如果模块未能加载，则尚未加载您的实际模块。<br /> 除了其他模块以外，还可以在此处加载脚本 (`.ps1`) 文件。 这些文件将在根模块的上下文中执行。 这等效于根模块中的脚本。 <br /> 示例： `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> 类型：`String[]`|`@()`|指定要从此模块导出的函数。为了获得最佳性能，请不要使用通配符，不要删除该项，如果没有要导出的函数，请使用空数组。 默认情况下，不导出任何函数。 您可以使用此键列出模块导出的函数。<br /> 模块将函数导出到调用方的会话状态。 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有函数都将导出到全局会话状态，除非该链中的模块使用 **FunctionsToExport** 键限制该函数。<br /> 如果清单导出函数的别名，则此键可以删除其别名在 **AliasesToExport** 项中列出的函数，但此键无法向列表中添加函数别名。 <br /> 示例： `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> 类型：`String[]`|`@()`|指定要从此模块导出的 cmdlet。为了获得最佳性能，请不要使用通配符，不要删除该项，如果没有要导出的 cmdlet，请使用空数组。 默认情况下，不导出任何 cmdlet。 你可以使用此密钥列出模块导出的 cmdlet。<br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有 cmdlet 都将导出到全局会话状态，除非该链中的模块使用 **CmdletsToExport** 键限制该 cmdlet。<br /> 如果清单导出 cmdlet 的别名，此密钥可以删除 **AliasesToExport** 密钥中列出其别名的 cmdlet，但此密钥不能将 cmdlet 别名添加到该列表中。 <br /> 示例： `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> 类型：`String[]`|`'*'`|指定模块导出到调用方的会话状态的变量。 允许使用通配符。 默认情况下， `'*'` 将导出 () 的所有变量。 您可以使用此密钥来限制由模块导出的变量。<br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有变量都将被导出到全局会话状态，除非该链中的模块使用 **VariablesToExport** 键限制了该变量。<br /> 如果清单还导出变量的别名，则此键可以删除在 **AliasesToExport** 项中列出其别名的变量，但此键不能将变量别名添加到该列表中。 <br /> 示例： `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> 类型：`String[]`|`@()`|指定要从此模块导出的别名。为了获得最佳性能，请不要使用通配符，不要删除该项，如果没有要导出的别名，请使用空数组。 默认情况下，不导出任何别名。 您可以使用此密钥列出模块导出的别名。<br /> 模块将别名导出到调用方的会话状态。 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有别名最终都将导出到全局会话状态，除非该链中的模块使用 **AliasesToExport** 键限制该别名。 <br /> 示例： `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> 类型：`String[]`|`@()`|指定要从此模块导出的 DSC 资源。 允许使用通配符。 <br /> 示例： `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> 类型：`Object[]`|`@()`|指定与此模块一起打包的所有模块。 可以按名称、以逗号分隔的字符串或使用 **ModuleName** 和 **GUID** 密钥的哈希表的形式输入这些模块。 哈希表还可以具有可选的 **ModuleVersion** 键。 **ModuleList** 键旨在充当模块清单。 这些模块不会自动处理。 <br /> 示例： `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**文件列表**<br /> 类型：`String[]`|`@()`|与此模块一起打包的所有文件的列表。 与 **ModuleList** 一样， **FileList** 是一个清单列表，并不以其他方式处理。 <br /> 示例： `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> 类型：`Object`|`@{...}`|指定任何需要传递到由 **RootModule** (Alias： **ModuleToProcess**) 键指定的根模块的专用数据。 **PrivateData** 是一个哈希表，其中包含多个元素： **标记**、 **LicenseUri**、 **ProjectURI**、 **IconUri**、 **ReleaseNotes**、 **预** 发布、 **RequireLicenseAcceptance** 和 **ExternalModuleDependencies**。 |
|**标记** <br /> 类型：`String[]` |`@()`| 标记有助于联机库中的模块发现。 <br /> 示例： `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> 类型：`Uri` |`<empty string>`| 此模块的许可证的 URL。 <br /> 示例： `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> 类型：`Uri` |`<empty string>`| 此项目的主网站的 URL。 <br /> 示例： `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> 类型：`Uri` |`<empty string>`| 表示此模块的图标的 URL。 <br /> 示例： `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> 类型：`String` |`<empty string>`| 指定模块的发行说明。 <br /> 示例： `ReleaseNotes = 'The release notes provide information about the module.`|
|**早期**<br /> 类型：`String` |`<empty string>`| 在 PowerShellGet 1.6.6 中添加了此参数。 将模块标识为联机库中的预发行版本的 **预发行** 版本字符串。 <br /> 示例： `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> 类型：`Boolean`|`$true`| 在 PowerShellGet 1.5 中添加了此参数。 一个标志，用于指示该模块是否需要显式用户接受安装、更新或保存。 <br /> 示例： `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> 类型：`String[]` |`@()`| 在 PowerShellGet v2 中添加了此参数。 此模块依赖的外部模块的列表。 <br /> 示例： `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> 类型：`String`|`<empty string>`|此模块的 HelpInfo URI。 <br /> 示例： `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> 类型：`String`|`<empty string>`|从此模块导出的命令的默认前缀。 使用重写默认前缀 `Import-Module -Prefix` 。 <br /> 示例： `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>示例模块清单

以下示例模块清单是 `New-ModuleManifest` 在 PowerShell 7 中创建的，其中包含默认的键和值。

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

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
        RequireLicenseAcceptance = $true

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

## <a name="see-also"></a>另请参阅

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[全局程序集缓存](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
