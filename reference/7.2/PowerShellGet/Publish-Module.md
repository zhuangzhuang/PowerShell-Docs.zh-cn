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
# Publish-Module

## 摘要
将指定模块从本机计算机发布到联机库。

## SYNTAX

### ModuleNameParameterSet (默认值) 

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

该 `Publish-Module` cmdlet 通过使用 API 密钥（存储在库中的用户配置文件的一部分），将模块发布到基于 NuGet 的联机库。 可根据模块的名称或包含模块的文件夹路径指定要发布的模块。

按名称指定模块时，将 `Publish-Module` 发布通过运行找到的第一个模块 `Get-Module -ListAvailable <Name>` 。 如果您指定要发布的模块的最低版本，将 `Publish-Module` 发布第一个版本大于或等于您指定的最低版本的模块。

发布模块需要在库页面显示的模块的元数据。 所需元数据包括模块名称、版本、说明和作者。 尽管大多数元数据都是从模块清单获取的，但必须在参数中指定某些元数据（如 `Publish-Module` **标记**、 **ReleaseNote**、 **IconUri**、 **ProjectUri** 和 **LicenseUri**），因为这些参数与基于 NuGet 的库中的字段匹配。

## 示例

### 示例1：发布模块

在此示例中，使用 API 密钥将 MyDscModule 发布到联机库，以指示模块所有者的联机库帐户。 如果 MyDscModule 不是指定名称、版本、说明和作者的有效清单模块，则会发生错误。

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### 示例2：使用库元数据发布模块

在此示例中，使用 API 密钥将 MyDscModule 发布到联机库，以指示模块所有者的库帐户。 提供的其他元数据将显示在库中模块的网页上。 所有者添加了两个用于模块的搜索标记，并将其与 Active Directory 相关联。已添加简短的发行说明。 如果 MyDscModule 不是指定名称、版本、说明和作者的有效清单模块，则会发生错误。

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETERS

### -AllowPrerelease

允许发布标记为预发行的模块。

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

### -Confirm

提示你在运行之前进行确认 `Publish-Module` 。

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

### -Credential

指定有权为指定的包提供程序或源发布模块的用户帐户。

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

### -Exclude

定义要从已发布的模块中排除的文件。

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

### -Force

强制运行命令而不要求用户确认。

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

### -FormatVersion

仅接受 **ValidateSet** 属性指定的有效值。

有关详细信息，请参阅 [ValidateSet 特性声明](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 和 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)。

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

指定要发布的模块的许可条款 URL。

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

### -Name

指定要发布的模块的名称。 `Publish-Module` 在中搜索指定的模块名称 `$Env:PSModulePath` 。

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

### -NuGetApiKey

指定要用于将模块发布到联机库的 API 密钥。 API 密钥是你的个人资料中的配置文件的一部分，可以在库中的用户帐户页面上找到。 API 密钥是 NuGet 特定的功能。

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

### -Path

指定要发布的模块的路径。 此参数接受包含模块的文件夹的路径。

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

指定一个字符串，该字符串包含此版本的模块的用户要使用的发行说明或注释。

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

### -Repository

指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。 存储库必须具有 **PublishLocation**，这是一个有效的 NuGet URI。
可以通过运行来设置 **PublishLocation** `Set-PSRepository` 。

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

### -RequiredVersion

指定要发布的单个模块的确切版本。

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

### -SkipAutomaticTags

删除作为标记包含的命令和资源。 跳过自动向模块添加标记。

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

### -Tags

将一个或多个标记添加到要发布的模块。 示例标记包括 DesiredStateConfiguration、DSC、DSCResourceKit 或 PSModule。 用逗号分隔多个标记。

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

### -WhatIf

显示运行时将发生的情况 `Publish-Module` 。 此 cmdlet 未运行。

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

### System.Management.Automation.PSCredential

## 输出

### System.Object

## 注释

`Publish-Module` 在 Windows 7 或 Windows 2008 R2 及更高版本的 Windows 上的 powershell 3.0 或更高版本上运行。

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

发布模块需要在库页面显示的模块的元数据。 所需元数据包括模块名称、版本、说明和作者。 大多数元数据都是从模块清单获取的，但是可以在参数中指定某些元数据， `Publish-Module` 例如 **标记**、 **ReleaseNote**、 **IconUri**、 **ProjectUri** 和 **LicenseUri**。 有关详细信息，请参阅 [影响 POWERSHELL 库 UI 的包清单值](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)。

## 相关链接

[Find-Module](Find-Module.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)
