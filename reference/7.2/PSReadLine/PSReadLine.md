---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193908"
---
# PSReadLine 模块

## 描述

PSReadLine 模块包含可用于在 PowerShell 中自定义命令行编辑环境的 cmdlet。 这些文章介绍了 PSReadLine v 2.2.0 的当前 beta 版本。

> [!NOTE]
> 从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。 目前，PSReadLine 不能与屏幕阅读器很好地配合使用。 Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。 如有必要，可以手动加载模块。

## PSReadLine Cmdlet

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
PSReadLine 的主入口点。

### [PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)
获取 PSReadLine 模块的绑定键函数。

### [PSReadLineOption](Get-PSReadLineOption.md)
获取可配置的选项的值。

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
此函数是 PSReadLine 的主要入口点。

### [PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)
删除键绑定。

### [PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。

### [PSReadLineOption](Set-PSReadLineOption.md)
自定义 **PSReadLine** 中命令行编辑的行为。

