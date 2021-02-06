---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598461"
---
# PackageManagement 模块

## 说明

本主题显示包管理 Cmdlet 的帮助主题。

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## PackageManagement Cmdlet

### [Find-Package](Find-Package.md)
在可用包源中查找软件包。

### [Find-PackageProvider](Find-PackageProvider.md)
返回可供安装的包管理包提供程序的列表。

### [Get-Package](Get-Package.md)
返回使用 **PackageManagement** 安装的所有软件包的列表。

### [Get-PackageProvider](Get-PackageProvider.md)
返回连接到包管理的包提供程序的列表。

### [Get-PackageSource](Get-PackageSource.md)
获取为包提供程序注册的包源的列表。

### [Import-PackageProvider](Import-PackageProvider.md)
将包管理包提供程序添加到当前会话中。

### [Install-Package](Install-Package.md)
安装一个或多个软件包。

### [Install-PackageProvider](Install-PackageProvider.md)
安装一个或多个包管理包提供程序。

### [Register-PackageSource](Register-PackageSource.md)
为指定的包提供程序添加包源。

### [Save-Package](Save-Package.md)
将包保存到本地计算机，但不安装它们。

### [Set-PackageSource](Set-PackageSource.md)
替换指定包提供程序的包源。

### [Uninstall-Package](Uninstall-Package.md)
卸载一个或多个软件包。

### [Unregister-PackageSource](Unregister-PackageSource.md)
删除已注册的包源。
