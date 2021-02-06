---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: f4fcf349c439baf4813c37af4bf56c26a46c7877
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596651"
---
# Install-Module

## 摘要
从存储库中下载一个或多个模块，并将其安装在本地计算机上。

## SYNTAX

### NameParameterSet（默认值）

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Install-Module`Cmdlet 从联机存储库中获取一个或多个满足指定条件的模块。 Cmdlet 验证搜索结果是否为有效的模块，并将模块文件夹复制到安装位置。 安装后，不会自动导入已安装的模块。
您可以根据指定模块的最小、最大和确切版本来筛选安装的模块。

如果正在安装的模块具有相同的名称或版本，或包含现有模块中的命令，则会显示警告消息。 确认要安装该模块并覆盖警告后，请使用 `-Force` 和 `-AllowClobber` 参数。 取决于存储库设置，你可能需要回答提示以继续安装模块。

这些示例使用 [PowerShell 库](https://www.powershellgallery.com/) 作为仅已注册的存储库。 `Get-PSRepository` 显示已注册的存储库。 如果有多个已注册的存储库，请使用 `-Repository` 参数指定存储库的名称。

## 示例

### 示例1：查找和安装模块

此示例查找存储库中的模块并安装该模块。

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

`Find-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。 默认情况下，将从存储库下载模块的最新版本。 对象通过管道向下发送到 `Install-Module` cmdlet。 `Install-Module` 为中的所有用户安装该模块 `$env:ProgramFiles\PowerShell\Modules` 。

### 示例2：按名称安装模块

在此示例中，将安装 **PowerShellGet** 模块的最新版本。

```powershell
Install-Module -Name PowerShellGet
```

`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。 默认情况下，将从存储库下载并安装最新版本的模块。

### 示例3：使用最低版本安装模块

在此示例中，将安装 **PowerShellGet** 模块的最低版本。 **MinimumVersion** 参数指定应安装的模块的最低版本。 如果模块的更新版本可用，则会为所有用户下载并安装该版本。

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。 **MinimumVersion** 参数指定从存储库下载并安装版本 **2.0.1** 。 由于版本 **2.0.4** 可用，因此会为所有用户下载和安装该版本。

### 示例4：安装特定版本的模块

在此示例中，安装了 **PowerShellGet** 模块的特定版本。

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。 **RequiredVersion** 参数指定为所有用户下载和安装版本 **2.0.0** 。

### 示例5：仅为当前用户安装模块

此示例仅为当前用户下载并安装最新版本的模块。

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。
`Install-Module` 下载最新版本的 **PowerShellGet** 并将其安装到当前用户的目录中 `$home\Documents\PowerShell\Modules` 。

## PARAMETERS

### -AcceptLicense

对于需要许可证的模块， **AcceptLicense** 会在安装过程中自动接受许可协议。 有关详细信息，请参阅 [需要接受许可证的模块](/powershell/scripting/gallery/concepts/module-license-acceptance)。

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

### -AllowClobber

覆盖有关计算机上的现有命令的安装冲突的警告消息。
覆盖与模块安装的命令同名的现有命令。
在命令中，可以将 **AllowClobber** 和 **Force** 一起使用 `Install-Module` 。

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

### -AllowPrerelease

允许你安装标记为预发行版的模块。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认 `Install-Module` 。

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

指定有权为指定的包提供程序或源安装模块的用户帐户。

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

### -Force

安装模块并覆盖有关模块安装冲突的警告消息。 如果计算机上已存在具有相同名称的模块，则 **强制** 允许安装多个版本。 如果存在具有相同名称和版本的现有模块，则 **强制** 覆盖该版本。 在命令中，可以将 **Force** 和 **AllowClobber** 一起使用 `Install-Module` 。

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

### -InputObject

用于管道输入。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

指定要安装的单个模块的最高版本。 安装的版本必须小于或等于 **MaximumVersion**。 如果要安装多个模块，则不能使用 **MaximumVersion**。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** `Install-Module` 。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要安装的单个模块的最低版本。 安装的版本必须大于或等于 **MinimumVersion**。 如果模块的更新版本可用，则会安装较新版本。 如果要安装多个模块，则不能使用 **MinimumVersion**。
不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** `Install-Module` 。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要从联机库中安装的模块的确切名称。 接受以逗号分隔的模块名称列表。 模块名称必须与存储库中的模块名称匹配。 使用 `Find-Module` 获取模块名称的列表。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

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

### -Proxy

为请求指定代理服务器，而不是直接连接到 Internet 资源。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。

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

### -Repository

使用 **存储库** 参数可指定用于下载和安装模块的存储库。 当注册多个存储库时使用。 在命令中指定已注册的存储库的名称 `Install-Module` 。 若要注册存储库，请使用 `Register-PSRepository` 。
若要显示已注册的存储库，请使用 `Get-PSRepository` 。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定要安装的单个模块的确切版本。 如果指定版本的存储库中没有匹配项，则会显示错误。 如果要安装多个模块，则不能使用 **RequiredVersion**。 对于 `Install-Module` **MinimumVersion** 或 **MaximumVersion**，不能在同一命令中使用 RequiredVersion。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定模块的安装范围。 此参数可接受的值为 **AllUsers** 和 **CurrentUser**。

**AllUsers** 作用域在计算机的所有用户都可以访问的位置中安装模块：

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 在只能由计算机的当前用户访问的位置中安装模块。 例如：

`$home\Documents\PowerShell\Modules`

如果未定义 **作用域** ，则将根据 PowerShellGet 版本设置默认值。

- 在 PowerShellGet 版本2.0.0 及更高版本中，默认值为 **CurrentUser**，无需进行提升即可安装。
- 在 PowerShellGet 1.x 版本中，默认值为 **AllUsers**，这需要提升才能进行安装。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

允许您安装计算机上已存在的较新版本的模块。 例如，如果现有模块由受信任的发布者进行数字签名，但新版本不由受信任的发布者进行数字签名。

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

### -WhatIf

显示运行命令时将发生的情况 `Install-Module` 。 此 cmdlet 未运行。

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

### PSRepositoryItemInfo

`Find-Module` 创建可通过管道向下发送的 **PSRepositoryItemInfo** 对象 `Install-Module` 。

### System.String[]

### System.web. system.exception []

### System.String

### System.Management.Automation.PSCredential

### System.Uri

## 输出

### PSRepositoryItemInfo。

当使用 **PassThru** 参数时， `Install-Module` 输出该模块的 **PSRepositoryItemInfo** 对象。 这与你从 cmdlet 获取的信息相同 `Find-Module` 。

## 注释

`Install-Module` 在 Windows 7 或 Windows 2008 R2 及更高版本的 Windows 上的 PowerShell 5.0 或更高版本上运行。

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

作为最佳安全方案，请在首次运行任何 cmdlet 或函数之前评估模块的代码。 为防止运行包含恶意代码的模块，安装后不会自动导入已安装的模块。

如果存储库中不存在 **name** 参数指定的模块名称，则会 `Install-Module` 返回错误。

若要安装多个模块，请使用 **Name** 参数，并指定一个逗号分隔的模块名称数组。 如果指定多个模块名称，则不能使用 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion**。 `Find-Module` 创建可通过管道向下发送的 **PSRepositoryItemInfo** 对象 `Install-Module` 。 管道是在单个命令中指定要安装的多个模块的另一种方法。

默认情况下， **AllUsers** 作用域的模块安装在中 `$env:ProgramFiles\PowerShell\Modules` 。 默认情况下，在 (DSC) 资源中安装 PowerShell Desired State Configuration 时，会造成混淆。

如果模块安装失败，并且在该 `.psm1` `.psd1` 文件夹内没有相同名称的、或，则无法导入 `.dll` 。 使用 **Force** 参数安装模块。

如果现有模块的版本与 **name** 参数指定的名称相匹配，并且未使用 **MinimumVersion** 或 **RequiredVersion** 参数，则将以 `Install-Module` 无提示方式继续，但不会安装该模块。

如果现有模块的版本大于 **MinimumVersion** 参数的值，或者等于 **RequiredVersion** 参数的值，则会以静默方式继续， `Install-Module` 但不会安装该模块。

如果现有模块与 **MinimumVersion** 或 **RequiredVersion** 参数指定的值不匹配，则会在命令中出现错误 `Install-Module` 。 例如，如果现有的已安装模块的版本低于 **MinimumVersion** 值或不等于 **RequiredVersion** 值。

模块安装还将安装模块发布程序所需的任何指定的相关模块。
发布者将在模块清单中指定必需的模块及其版本。

## 相关链接

[Find-Module](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[Import-Module](../Microsoft.PowerShell.Core/Import-Module.md)

[Publish-Module](Publish-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)
