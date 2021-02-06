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
# Update-ModuleManifest

## 摘要
更新模块清单文件。

## SYNTAX

### 全部

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

## DESCRIPTION

`Update-ModuleManifest`Cmdlet () 文件更新模块清单 `.psd1` 。

## 示例

### 示例1：更新模块清单

此示例更新现有的模块清单文件。 展开用于将参数值传递给 `Update-ModuleManifest` 。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` 是存储 **路径**、 **作者**、 **公司名称** 和 **版权** 的参数值的 splat。 `Update-ModuleManifest` 从获取参数值， `@Parms` 并更新 **TestManifest.psd1** 的模块清单。

## PARAMETERS

### -AliasesToExport

指定模块导出的别名。 允许使用通配符。

使用此参数来限制由模块导出的别名。 **AliasesToExport** 可以从导出的别名列表中删除别名，但不能将别名添加到该列表中。

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

### -作者

指定模块作者。

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

### -ClrVersion

指定模块需要的 Microsoft .NET Framework 的公共语言运行时 (CLR) 的最低版本。

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

### -CmdletsToExport

指定模块导出的 cmdlet。 允许使用通配符。

使用此参数来限制由模块导出的 cmdlet。 **CmdletsToExport** 可以从导出的 cmdlet 列表中删除 cmdlet，但不能将 cmdlet 添加到该列表中。

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

### -公司名称

指定创建该模块的公司或供应商。

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

### -CompatiblePSEditions

指定模块的兼容 **PSEditions** 。 有关 **PSEdition** 的信息，请参阅 [具有兼容的 PowerShell 版本的模块](/powershell/scripting/gallery/concepts/module-psedition-support)。

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

### -Confirm

在运行之前提示你进行确认 `Update-ModuleManifest` 。

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

### -版权所有

指定模块的版权声明。

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

### -DefaultCommandPrefix

指定默认命令前缀。

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

### -Description

指定模块的说明。

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

### -DotNetFrameworkVersion

指定模块需要的 Microsoft .NET Framework 的最低版本。

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

### -DscResourcesToExport

指定模块导出 (DSC) 资源的所需状态配置。 允许使用通配符。

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

### -ExternalModuleDependencies

指定外部模块依赖项的数组。

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

### -FileList

指定模块中包括的所有项。

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

### -FormatsToProcess

指定 `.ps1xml` 导入模块时运行)  (格式设置文件。

导入模块时，PowerShell 将 `Update-FormatData` 使用指定的文件运行 cmdlet。
由于格式设置文件没有作用域，因此它们会影响会话中的所有会话状态。

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

### -FunctionsToExport

指定模块导出的函数。 允许使用通配符。

使用此参数来限制由模块导出的函数。 **FunctionsToExport** 可以从导出的别名列表中删除函数，但不能将函数添加到列表。

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

### -Guid

指定模块的唯一标识符。 可以使用 GUID 来区分名称相同的模块。

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

### -HelpInfoUri

指定模块的 **HELPINFO XML** 文件的 internet 地址。 输入以 **http** 或 **HTTPS** 开头 (URI) 的统一资源标识符。

**HELPINFO XML** 文件支持 PowerShell 版本3.0 中引入的可更新帮助功能。 它包含有关该模块的可下载帮助文件的位置，以及每个支持的区域设置最新帮助文件的版本号的信息。

有关可更新帮助的信息，请参阅 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)。
有关 **HELPINFO XML** 文件的信息，请参阅 [支持可更新的帮助](/powershell/scripting/developer/module/supporting-updatable-help)。

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

### -IconUri

指定模块的图标的 URL。 指定的图标显示在模块的库网页上。

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

### -LicenseUri

指定模块的许可条款 URL。

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

### -ModuleList

指定模块中包含的模块的数组。

以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。 哈希表也可能具有一个可选的 **GUID** 键。 可以将字符串和哈希表组合到参数值中。

此键专门用于充当模块清单。 不会自动处理此键的值中列出的模块。

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

### -ModuleVersion

指定模块的版本。

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

### -NestedModules

指定脚本模块 (`.psm1` `.dll` 导入模块的会话状态中 () 的) 和二进制模块。 **NestedModules** 键中的文件按照其在值中的列出顺序运行。

以字符串形式或具有 **ModuleName** 和 **ModuleVersion** 键的哈希表形式输入每个模块名称。 哈希表也可能具有一个可选的 **GUID** 键。 可以将字符串和哈希表组合到参数值中。

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

### -PackageManagementProviders

指定包管理提供程序的数组。

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

### -PassThru

返回一个对象，该对象表示正在处理的项。 默认情况下， `Update-ModuleManifest` 不会生成任何输出。

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

### -Path

指定模块清单的路径和文件名。 输入文件扩展名为的路径和文件名 `.psd1` ，例如 `$PSHOME\Modules\MyModule\MyModule.psd1` 。

如果指定了现有文件的路径，则将 `Update-ModuleManifest` 替换该文件而不发出警告，除非该文件具有只读属性。

清单应位于模块的目录中，清单文件的名称应与模块目录名称相同，但具有 `.psd1` 扩展名。

不能使用变量（如 `$PSHOME` 或 `$HOME` ）来响应 **Path** 参数值的提示。 若要使用变量，请将 **Path** 参数包含在命令中。

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

### -PowerShellHostName

指定模块所需的 PowerShell 主机程序的名称。 输入主机程序的名称，例如 PowerShell ISE Host 或 ConsoleHost。 不允许使用通配符。

若要查找主机程序的名称，请在 "程序" 中键入 `$Host.Name` 。

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

### -PowerShellHostVersion

指定适用于该模块的 PowerShell 主机程序的最低版本。 输入版本号，例如 1.1。

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

### -PowerShellVersion

指定将用于此模块的 PowerShell 的最低版本。 例如，可以将3.0、4.0 或5.0 指定为此参数的值。

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

### -预发行版

指示模块为预发行版。

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

### -PrivateData

指定导入模块时传递给模块的数据。

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

### -ProcessorArchitecture

指定模块需要的处理器体系结构。

此参数的可接受值为：

- Amd64
- Arm
- IA64
- MSIL
- 无 (未知或未指定的) 
- X86

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

### -ProjectUri

指定有关此项目的网页的 URL。

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

### -ReleaseNotes

指定一个字符串数组，其中包含要用于此版本的脚本的发行说明或注释。

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

### -RequireLicenseAcceptance

指定模块需要接受许可证。

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

### -RequiredAssemblies

指定模块需要的程序集 (`.dll`) 文件。 输入程序集文件名。
PowerShell 在更新类型或格式、导入嵌套模块或导入在 **RootModule** 项的值中指定的模块文件之前加载指定的程序集。

使用此参数可指定模块所需的所有程序集，包括必须加载以便更新 **FormatsToProcess** 或 **TypesToProcess** 键中列出的任何格式设置或类型文件的程序集，即使这些程序集也在 **NestedModules** 项中作为二进制模块列出也是如此。

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

### -RequiredModules

指定必须处于全局会话状态的模块。 如果所需模块未处于全局会话状态，则 PowerShell 会将其导入。 如果所需模块不可用，则该 `Import-Module` 命令将失败。

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

### -RootModule

指定模块的主文件或根文件。 输入脚本的文件名 (`.ps1`) 、脚本模块 (`.psm1`) 、模块清单 () `.psd1` 、程序集 (`.dll`) 、cmdlet 定义 XML 文件 (`.cdxml`) 或 () 工作流 `.xaml` 。 导入模块时，从根模块文件导出的成员将导入到调用方的会话状态中。

如果某个模块具有清单文件，并且未在 **RootModule** 项中指定任何根文件，则该清单将成为该模块的主文件。 而且，模块将成为清单模块 (ModuleType = Manifest) 。

若要从 `.psm1` `.dll` 具有清单的模块中的或文件中导出成员，必须在清单中的 **RootModule** 或 **NestedModules** 键的值中指定这些文件的名称。 否则，不会导出它们的成员。

在 PowerShell 2.0 中，此密钥称为 **ModuleToProcess**。

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

### -ScriptsToProcess

指定 `.ps1` 导入模块时，在调用方的会话状态中运行的脚本 () 文件。
可以像使用登录脚本一样使用这些脚本来准备环境。

若要指定在模块的会话状态中运行的脚本，请使用 **NestedModules** 键。

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

### -Tags

指定标记的数组。

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

### -TypesToProcess

指定 `.ps1xml` 导入模块时运行)  (类型文件。

导入模块时，PowerShell 将运行 `Update-TypeData` 具有指定文件的 cmdlet。
由于类型文件不作用域，因此它们会影响会话中的所有会话状态。

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

### -VariablesToExport

指定模块导出的变量。 允许使用通配符。

使用此参数来限制由模块导出的变量。 **VariablesToExport** 可以从导出的变量列表中删除变量，但不能将变量添加到该列表中。

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

### -WhatIf

显示运行时将发生 `Update-ModuleManifest` 的情况。 cmdlet 未运行。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

## 输出

### System.Object

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接
