---
description: 介绍如何在命令历史记录中获取和运行命令。
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 44e03bd37b0b2c5928fb3aa850f3f5b554ccf123
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597888"
---
# <a name="about-history"></a>关于历史记录

## <a name="short-description"></a>简短说明
介绍如何在命令历史记录中获取和运行命令。

## <a name="long-description"></a>详细说明

当你在命令提示符下输入命令时，PowerShell 会将命令保存在命令历史记录中。 你可以使用历史记录中的命令作为你的工作记录。 而且，您可以从命令历史记录中调用并运行命令。

PowerShell 具有两个不同的历史记录提供程序：内置历史记录和 **PSReadLine** 模块管理的历史记录。 历史记录是分开管理的，但这两个历史记录均可用于加载 **PSReadLine** 的会话中。

## <a name="using-the-psreadline-history"></a>使用 PSReadLine 历史记录

PSReadLine 历史记录跟踪所有 PowerShell 会话中使用的命令。
历史记录将写入每个主机的中心文件。 该历史记录文件可供所有会话使用，并包含所有过去的历史记录。 会话结束时不会删除历史记录。 此外，这些 cmdlet 无法管理该历史记录 `*-History` 。 有关详细信息，请参阅 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。

## <a name="using-the-built-in-session-history"></a>使用内置会话历史记录

内置历史记录只跟踪当前会话中使用的命令。 历史记录不能用于其他会话，在会话结束时将被删除。

### <a name="history-cmdlets"></a>历史记录 Cmdlet

PowerShell 包含一组用于管理命令历史记录的 cmdlet。

| Cmdlet           | Alias  | 说明                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | 获取命令历史记录。                  |
| `Invoke-History` | `r`    | 在命令历史记录中运行命令。     |
| `Add-History`    |        | 将命令添加到命令历史记录。     |
| `Clear-History`  | `clhy` | 从命令历史记录中删除命令。 |

### <a name="keyboard-shortcuts-for-managing-history"></a>用于管理历史记录的键盘快捷方式

在 PowerShell 控制台中，可以使用以下快捷方式管理命令历史记录。

- <kbd>向上键</kbd> -显示上一个命令。
- <kbd>向下键</kbd> -显示下一个命令。
- <kbd>F7</kbd> -显示命令历史记录。
- <kbd>ESC</kbd> -隐藏历史记录。
- <kbd>F8</kbd> -查找命令。 键入一个或多个字符，然后按 <kbd>F8</kbd>。 再次按 <kbd>F8</kbd> 。
- <kbd>F9</kbd> -按历史记录 ID 查找命令。 键入历史记录 ID，然后按 <kbd>F9</kbd>。 按 <kbd>F7</kbd> 查找 ID。
- <kbd>#</kbd>`<string>`</kbd><kbd>选项卡</kbd> -搜索历史记录 `*<string>*` ，并返回最近的匹配项。 如果重复按 <kbd>tab</kbd> 键，则会循环遍历历史记录中的匹配项。

> [!NOTE]
> 这些密钥绑定由控制台主机应用程序实现。 其他应用程序（如 Visual Studio Code 或 Windows 终端）可以具有不同的键绑定。 绑定可由 PSReadLine 模块重写。 启动 PowerShell 会话时，PSReadLine 会自动加载。
> 在加载 PSReadLine 的情况下， <kbd>F7</kbd> 和 <kbd>F9</kbd> 未绑定到任何函数。 PSReadLine 未提供等效功能。 有关详细信息，请参阅 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。

### <a name="maximumhistorycount"></a>MaximumHistoryCount

`$MaximumHistoryCount`首选项变量确定 PowerShell 在命令历史记录中保存的最大命令数。 默认值为
4096.

例如，以下命令将减少 `$MaximumHistoryCount` 到100命令：

```powershell
$MaximumHistoryCount = 100
```

若要应用设置，请重新启动 PowerShell。

若要为所有 PowerShell 会话保存新的变量值，请将赋值语句添加到 PowerShell 配置文件中。 有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

有关 `$MaximumHistoryCount` 首选项变量的详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

### <a name="order-of-commands-in-the-history"></a>历史记录中的命令顺序

命令完成执行时（而不是在输入命令时），会将命令添加到历史记录中。 如果命令需要一些时间才能完成，或命令在嵌套提示符下执行，则这些命令在历史记录中的显示顺序可能会不按顺序显示。 仅当退出提示级别时，才会完成在嵌套提示中执行的命令。

## <a name="see-also"></a>另请参阅

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

