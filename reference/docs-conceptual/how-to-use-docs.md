---
ms.date: 07/29/2020
keywords: powershell,cmdlet
ms.topic: how-to
title: 如何使用 PowerShell 文档
description: 本文介绍如何使用此站点的功能，包括搜索筛选和版本选择。
ms.openlocfilehash: 4779e6e4b17c461d71e9d613d1184b9ce2e7ab7b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216076"
---
# <a name="how-to-use-the-powershell-documentation"></a>如何使用 PowerShell 文档

欢迎使用 PowerShell 联机文档。 此站点包含以下 PowerShell 版本的 cmdlet 参考：

- PowerShell 7.2（预发行版）
- PowerShell 7.1（当前版本）
- PowerShell 7.0 (LTS)
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>查找文章并选择版本

有两种方法可以搜索 Docs 中的内容。最简单的方法是使用版本选取器下的筛选器框。 只需输入文章标题中出现的字词即可。 该页面显示匹配文章的列表。 还可以从该列表中选择用于搜索整个站点的选项。

默认情况下，此站点显示最新版本的 PowerShell 的文档。 一些 cmdlet 在不同版本的 PowerShell 中的工作方式有所不同。 确保查看所使用的 PowerShell 版本的文档。

使用页面顶部的版本选取器来选择所需的 PowerShell 版本。

![使用版本选取器](media/how-to-use-docs/version-search.gif)

可以通过查看 `$PSversionTable.PSVersion` 值来验证所使用的 PowerShell 版本。 下面的示例演示 Windows PowerShell 5.1 的输出。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

如果你还不熟悉 PowerShell，并需要有关理解命令语法方面的帮助，请参阅 [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)。

## <a name="finding-articles-for-previous-versions"></a>在文章中查找历史版本

旧版 PowerShell 的相关文档已存档到我们的[历史版本](https://aka.ms/PSLegacyDocs)网站中。

此网站包含下列主题的文档：

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- PowerShell 6
- PowerShell 工作流
- PowerShell Web 访问
