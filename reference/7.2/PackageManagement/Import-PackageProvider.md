---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597860"
---
# Import-PackageProvider

## 摘要
将包管理包提供程序添加到当前会话中。

## SYNTAX

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## DESCRIPTION

`Import-PackageProvider`Cmdlet 可将一个或多个包提供程序添加到当前会话中。
必须在本地计算机上安装导入的提供程序。

若要获取可用提供程序的列表，请运行 `Get-PackageProvider -ListAvailable` 。
请注意，包提供程序名称可以与其模块名称不同。

出于安全原因， **PackageManagement** 要求基于 c # 的提供程序包含 `provider.manifest` 。 有关如何使用注入的生成提供程序的详细信息 `provider.manifest` ，请参阅 `.csproj` 上的项目文件 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) 。

## 示例

### 示例1：从本地计算机导入包提供程序

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

此命令在 Nuget 提供程序安装在本地计算机上后导入它。

### 示例2：导入特定版本的包提供程序

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

此命令查找、安装和导入特定版本的 Nuget 包提供程序。

## PARAMETERS

### -Force

强制运行命令而不要求用户确认。
重新导入包提供程序。

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

### -MaximumVersion

指定要导入的包提供程序的最大允许版本。 如果未添加此参数，则将 `Import-PackageProvider` 导入提供程序的最高可用版本。

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

指定要导入的包提供程序的最小允许版本。 如果未添加此参数，则将 `Import-PackageProvider` 导入同时满足使用 *MaximumVersion* 参数指定的任何最高版本的包的最高可用版本。

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

指定一个或多个包提供程序名称。 不允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定要导入的包提供程序的确切版本。 如果未添加此参数，则将 `Import-PackageProvider` 导入最高可用版本的提供程序，该版本还满足使用 **MaximumVersion** 参数指定的任何最高版本。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### Install-packageprovider。

可以通过管道将返回的 **install-packageprovider** 对象传递 `Get-PackageProvider` 给 `Import-PackageProvider` 。

## 输出

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

[Get-PackageProvider](Get-PackageProvider.md)
