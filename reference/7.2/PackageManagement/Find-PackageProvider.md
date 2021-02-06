---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: cca73714cebf8f0d527c669358458f8509b80a90
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596014"
---
# Find-PackageProvider

## 摘要
返回可供安装的包管理包提供程序的列表。

## SYNTAX

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## DESCRIPTION

**Install-packageprovider** cmdlet 查找匹配的 PackageManagement 提供程序，这些提供程序在使用 PowerShellGet 注册的包源中可用。
这些包提供程序都能用 Install-PackageProvider cmdlet 直接进行安装。
默认情况下，这包括在使用 **PackageManagement** 和 **提供程序** 标记的 PowerShell 库中可用的模块。

**Install-packageprovider** 还查找包管理 Azure Blob 存储中提供的匹配包管理提供程序。
使用引导程序提供程序查找并安装它们。

## 示例

### 示例1：查找所有可用的包提供程序

```
PS C:\> Find-PackageProvider
```

此命令获取包管理支持的存储库中可用的所有包提供程序的列表。
默认情况下，这些包提供程序在 PowerShell 库上提供，并使用包管理引导应用程序。

### 示例2：查找提供程序的所有版本

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

此命令将查找名为 Nuget 的包提供程序的所有版本。

### 示例3：从指定的源查找提供程序

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

此命令使用指定的包源查找可用的包提供程序。

## PARAMETERS

### -AllVersions

指示此 cmdlet 返回包提供程序的所有可用版本。
默认情况下， **install-packageprovider** 仅返回最新的可用版本。

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

指定有权搜索包提供程序的用户帐户。

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

### -Force

强制运行命令而不要求用户确认。
目前，这等效于 *ForceBootstrap* 参数。

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

指示此 cmdlet 强制包管理自动安装包提供程序。

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

### -IncludeDependencies

指示此 cmdlet 包含依赖项。

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

### -MaximumVersion

指定要查找的包提供程序的最大允许版本。
如果未添加此参数，则 **install-packageprovider** 将查找提供程序的最高可用版本。

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

### -MinimumVersion

指定要查找的包提供程序的最小允许版本。
如果未添加此参数，则 **install-packageprovider** 将查找同时满足 *MaximumVersion* 参数指定的任何最大指定版本的包的最高可用版本。

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

### -Name

指定一个或多个包提供程序模块名称或提供程序名称和通配符。
用逗号分隔多个包名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

指定要查找的包提供程序的确切允许版本。
如果未添加此参数，则 **install-packageprovider** 将查找同时满足 *MaximumVersion* 参数指定的任何最高版本的提供程序的最高可用版本。

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

### -Source

指定一个或多个包源。
可以通过使用 Get-PackageSource cmdlet 获取可用包源的列表。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

### Softwareidentity.revisionnumber。

此 cmdlet 将返回 **softwareidentity.revisionnumber** 对象。
可以通过管道将 **softwareidentity.revisionnumber** 对象传递到 **install-packageprovider** 中，以安装 **install-packageprovider** 的结果。

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Install-PackageProvider](Install-PackageProvider.md)
