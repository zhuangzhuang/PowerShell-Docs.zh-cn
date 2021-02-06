---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 683329aac35744697d80e22efff5ec53bae74830
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603411"
---
# Install-PackageProvider

## 摘要
安装一个或多个包管理包提供程序。

## SYNTAX

### PackageBySearch（默认值）

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Install-PackageProvider`Cmdlet 安装在使用 **PowerShellGet** 注册的包源中可用的匹配包管理提供程序。 默认情况下，这包括 Windows PowerShell 库中使用 **PackageManagement** 标记的可用模块。 **PowerShellGet** 包管理提供程序用于查找这些存储库中的提供程序。

此 cmdlet 还会安装可使用包管理引导应用程序进行匹配包管理提供程序。

此 cmdlet 还会安装包管理 Azure Blob 存储中提供的匹配包管理提供程序。 使用引导程序提供程序查找并安装它们。

为了首次执行，PackageManagement 需要 internet 连接才能下载 NuGet 包提供程序。 但是，如果您的计算机没有 internet 连接并且您需要使用 NuGet 或 PowerShellGet 提供程序，则可以将其下载到其他计算机上，然后将它们复制到目标计算机。 使用以下步骤来执行此操作：

1. 运行 `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` 从具有 internet 连接的计算机上安装提供程序。
1. 安装后，可以在或中找到安装的提供 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` 程序 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` 。
1. 将 `<ProviderName>` 该文件夹（在本例中为 NuGet 文件夹）放置在目标计算机上的相应位置。 如果目标计算机是 Nano server，则需要 `Install-PackageProvider` 从 Nano server 运行以下载正确的 NuGet 二进制文件。
1. 重新启动 PowerShell 以自动加载包提供程序。 或者，运行 `Get-PackageProvider -ListAvailable` 以列出计算机上可用的所有包提供程序。
   然后，使用 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 将提供程序导入到当前的 Windows PowerShell 会话。

## 示例

### 示例1：从 PowerShell 库安装包提供程序

此命令从 PowerShell 库安装 GistProvider 包提供程序。

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### 示例2：安装包提供程序的指定版本

此示例将安装 NuGet 包提供程序的指定版本。

第一个命令将查找名为 NuGet 的包提供程序的所有版本。
第二个命令安装 NuGet 包提供程序的指定版本。

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### 示例3：查找提供程序并安装它

此示例使用 `Find-PackageProvider` 和管道搜索 Gist 提供程序并安装它。

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### 示例4：将提供程序安装到当前用户的模块文件夹

此命令将包提供程序安装到， `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` 以便只有当前用户可以使用它。

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## PARAMETERS

### -AllVersions

指示此 cmdlet 安装包提供程序的所有可用版本。 默认情况下， `Install-PackageProvider` 仅返回可用的最高版本。

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

### -Credential

指定有权安装包提供程序的用户帐户。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示此 cmdlet 强制执行可强制执行的与此 cmdlet 的所有操作。 目前，这意味着 **Force** 参数的作用与 **ForceBootstrap** 参数相同。

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

### -ForceBootstrap

指示此 cmdlet 自动安装包提供程序。

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

指定 **softwareidentity.revisionnumber** 对象。 使用 `Find-PackageProvider` cmdlet 获取要通过管道传入的 **softwareidentity.revisionnumber** 对象 `Install-PackageProvider` 。

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

指定要安装的包提供程序的最大允许版本。 如果不添加此参数，则 `Install-PackageProvider` 安装提供程序的最高可用版本。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

指定要安装的包提供程序的最小允许版本。 如果未添加此参数，将 `Install-PackageProvider` 安装包的最高可用版本，同时满足 *MaximumVersion* 参数指定的任何要求。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定一个或多个包提供程序模块名称。 用逗号分隔多个包名称。
不支持通配符。

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
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
Accept pipeline input: False
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定要安装的包提供程序的确切允许版本。 如果不添加此参数，将 `Install-PackageProvider` 安装提供程序的最高可用版本，该版本还满足 **MaximumVersion** 参数指定的任何最高版本。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定提供程序的安装范围。 此参数的可接受值为：

- **AllUsers** -在计算机的所有用户都可以访问的位置中安装提供程序。
  默认情况下，这是 **$env:P rogramfiles\packagemanagement\providerassemblies.**

- **CurrentUser** -在只能由当前用户访问的位置上安装提供程序。 默认情况下，这是 **$env： LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

### -Source

指定一个或多个包源。 使用 `Get-PackageSource` cmdlet 获取可用包源的列表。

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

### Softwareidentity.revisionnumber。

可以通过管道将 **softwareidentity.revisionnumber** 对象传递给此 cmdlet。 用于 `Find-PackageProvider` 获取可通过管道传递到的 **softwareidentity.revisionnumber** 对象 `Install-PackageProvider` 。

## 输出

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
