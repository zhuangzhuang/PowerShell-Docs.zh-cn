---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 0d4e5e26184558055a17f99bd5321aaf3f3789f7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597675"
---
# PowerShellGet 模块

## 说明

PowerShellGet 是一个模块，其中包含用于发现、安装、更新和发布 PowerShell 项目（如模块、DSC 资源、角色功能和脚本）的命令。

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## PowerShellGet Cmdlets

### [Find-Command](Find-Command.md)
查找模块中的 PowerShell 命令。

### [Find-DscResource](Find-DscResource.md)
 (DSC) 资源中查找所需的状态配置。

### [Find-Module](Find-Module.md)
查找存储库中与指定条件匹配的模块。

### [Find-RoleCapability](Find-RoleCapability.md)
在模块中查找角色功能。

### [Find-Script](Find-Script.md)
查找脚本。

### [Get-InstalledModule](Get-InstalledModule.md)
获取由 PowerShellGet 安装的计算机上的模块列表。

### [Get-InstalledScript](Get-InstalledScript.md)
获取已安装的脚本。

### [Get-PSRepository](Get-PSRepository.md)
获取 PowerShell 存储库。

### [Install-Module](Install-Module.md)
从存储库中下载一个或多个模块，并将其安装在本地计算机上。

### [Install-Script](Install-Script.md)
安装脚本。

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
使用元数据创建脚本文件。

### [Publish-Module](Publish-Module.md)
将指定模块从本机计算机发布到联机库。

### [Publish-Script](Publish-Script.md)
发布脚本。

### [Register-PSRepository](Register-PSRepository.md)
注册 PowerShell 存储库。

### [Save-Module](Save-Module.md)
将模块及其依赖项保存在本地计算机上，但不会安装该模块。

### [Save-Script](Save-Script.md)
保存脚本。

### [Set-PSRepository](Set-PSRepository.md)
为已注册的存储库设置值。

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
验证脚本的注释块。

### [Uninstall-Module](Uninstall-Module.md)
卸载模块。

### [Uninstall-Script](Uninstall-Script.md)
卸载脚本。

### [Unregister-PSRepository](Unregister-PSRepository.md)
取消注册存储库。

### [Update-Module](Update-Module.md)
从联机库中下载指定模块的最新版本，并将其安装到本地计算机。

### [Update-ModuleManifest](Update-ModuleManifest.md)
更新模块清单文件。

### [Update-Script](Update-Script.md)
更新脚本。

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
更新脚本的信息。
