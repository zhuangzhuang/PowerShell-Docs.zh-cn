---
ms.date: 01/02/2020
title: Windows PowerShell ISE 的键盘快捷方式
description: 本文列出了在 PowerShell ISE 中使用的键盘快捷方式。
ms.openlocfilehash: 690997524ab90d7581bb03c802f189d1a4b79d3f
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500187"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Windows PowerShell ISE 的键盘快捷方式

使用以下键盘快捷方式在 Windows PowerShell&reg; 集成脚本环境 (ISE) 中执行操作。 Windows PowerShell ISE 可作为 Windows Server 和 Windows 客户端操作系统的一部分，但是也可作为 [Windows Management Framework 4.0 下载包](https://go.microsoft.com/fwlink/?LinkID=293881)的一部分安装在早期的 Windows 操作系统上。

## <a name="keyboard-shortcuts-for-editing-text"></a>编辑文本的键盘快捷方式

编辑文本时可以使用以下键盘快捷方式。

|              操作              |              键盘快捷方式               |                                                                                                                                           用于                                                                                                                                           |
| -------------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **帮助**                         | <kbd>F1</kbd>                                 | 脚本窗格“**重要提示**”：你可以指定 <kbd>F1</kbd> 帮助来自 docs.microsoft.com 还是下载的帮助（请参阅“`Update-Help`”）。 若要选择，请单击“工具”、“选项”，然后在“常规设置”选项卡上，设置或清除“使用本地帮助内容，而不是联机内容”。     |
| **Copy**                         | <kbd>CTRL</kbd>+<kbd>C</kbd>                  | 脚本窗格、命令窗格、输出窗格                                                                                                                                                                                                                                                     |
| **剪切**                          | <kbd>CTRL</kbd>+<kbd>X</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **展开或折叠大纲** | <kbd>CTRL</kbd>+<kbd>M</kbd>                  | 脚本窗格                                                                                                                                                                                                                                                                                |
| **在脚本中查找**               | <kbd>CTRL</kbd>+<kbd>F</kbd>                  | 脚本窗格                                                                                                                                                                                                                                                                                |
| **在脚本中查找下一个**          | <kbd>F3</kbd>                                 | 脚本窗格                                                                                                                                                                                                                                                                                |
| **在脚本中查找上一个**      | <kbd>SHIFT</kbd>+<kbd>F3</kbd>                | 脚本窗格                                                                                                                                                                                                                                                                                |
| **查找匹配的括号**          | <kbd>CTRL</kbd>+<kbd>]</kbd>                  | 脚本窗格                                                                                                                                                                                                                                                                                |
| **粘贴**                        | <kbd>CTRL</kbd>+<kbd>V</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **转换为小写**               | <kbd>CTRL</kbd>+<kbd>U</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **转换为大写**               | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>U</kbd> | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **重做**                         | <kbd>CTRL</kbd>+<kbd>Y</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **在脚本中替换**            | <kbd>CTRL</kbd>+<kbd>H</kbd>                  | 脚本窗格                                                                                                                                                                                                                                                                                |
| **保存**                         | <kbd>CTRL</kbd>+<kbd>S</kbd>                  | 脚本窗格                                                                                                                                                                                                                                                                                |
| **全选**                   | <kbd>CTRL</kbd>+<kbd>A</kbd>                  | 脚本窗格、命令窗格、输出窗格                                                                                                                                                                                                                                                     |
| **显示代码段**                | <kbd>CTRL</kbd>+<kbd>J</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |
| **撤消**                         | <kbd>CTRL</kbd>+<kbd>Z</kbd>                  | 脚本窗格、命令窗格                                                                                                                                                                                                                                                                  |

## <a name="keyboard-shortcuts-for-running-scripts"></a>运行脚本的键盘快捷方式

在脚本窗格中运行脚本时，可使用以下键盘快捷方式。

|            操作            |                                                                                                             键盘快捷方式                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **新建**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                                              |
| **打开**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                                              |
| **运行**                      | <kbd>F5</kbd>                                                                                                                                                                                                                             |
| **运行选定内容**            | <kbd>F8</kbd>                                                                                                                                                                                                                             |
| **停止执行**           | <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。 可以在上下文不明确时（未选定任何文本时）使用 <kbd>CTRL</kbd>+<kbd>C</kbd>。                                                                                              |
| **Tab**（切换到下一个脚本）     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **注意：** 按 Tab 键切换到下一个脚本仅适用于打开一个 Windows PowerShell 选项卡或打开多个 Windows PowerShell 选项卡，但焦点在脚本窗格中的情况。               |
| **Tab**（切换到上一个脚本） | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd> **注意：** 按 Tab 键切换到上一个脚本适用于仅打开一个 Windows PowerShell 选项卡或打开多个 Windows PowerShell 选项卡，但焦点在脚本窗格中的情况。 |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>自定义视图的键盘快捷方式

可以使用以下键盘快捷方式在 Windows PowerShell ISE 中自定义视图。 可从应用程序中的所有窗格对它们进行访问。

|                        操作                         |               键盘快捷方式               |
| ----------------------------------------------------- | --------------------------------------------- |
| **转到命令 (v2) 或控制台（v3 和更高版本）窗格** | <kbd>CTRL</kbd>+<kbd>D</kbd>                  |
| **转到输出窗格（仅 v2）**                       | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>O</kbd> |
| **转到脚本窗格**                                 | <kbd>CTRL</kbd>+<kbd>I</kbd>                  |
| **显示脚本窗格**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **隐藏脚本窗格**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **向上移动脚本窗格**                               | <kbd>CTRL</kbd>+<kbd>1</kbd>                  |
| **向右移动脚本窗格**                            | <kbd>CTRL</kbd>+<kbd>2</kbd>                  |
| **最大化脚本窗格**                              | <kbd>CTRL</kbd>+<kbd>3</kbd>                  |
| **放大**                                           | <kbd>CTRL</kbd>+<kbd>+</kbd>                  |
| **缩小**                                          | <kbd>CTRL</kbd>+<kbd>-</kbd>                  |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>用于调试脚本的键盘快捷方式

调试脚本时，可使用以下键盘快捷方式。

|           操作           |               键盘快捷方式                |                用于                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **运行/继续**           | <kbd>F5</kbd>                                  | 脚本窗格，调试脚本时 |
| **步入**              | <kbd>F11</kbd>                                 | 脚本窗格，调试脚本时 |
| **步越**              | <kbd>F10</kbd>                                 | 脚本窗格，调试脚本时 |
| **步出**               | <kbd>SHIFT</kbd>+<kbd>F11</kbd>                | 脚本窗格，调试脚本时 |
| **显示调用堆栈**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>  | 脚本窗格，调试脚本时 |
| **列出断点**       | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>L</kbd>  | 脚本窗格，调试脚本时 |
| **切换断点**      | <kbd>F9</kbd>                                  | 脚本窗格，调试脚本时 |
| **移除所有断点** | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>F9</kbd> | 脚本窗格，调试脚本时 |
| **停止调试器**          | <kbd>SHIFT</kbd>+<kbd>F5</kbd>                 | 脚本窗格，调试脚本时 |

> [!NOTE]
> 在 Windows PowerShell ISE 中调试脚本时，也可以使用为 Windows PowerShell 控制台而设计的键盘快捷方式。 若要使用这些快捷方式，必须在命令窗格中键入该快捷方式并按 <kbd>ENTER</kbd>。

|                        操作                        | 键盘快捷方式 |                用于                 |
| ---------------------------------------------------- | ----------------- | ------------------------------------- |
| **继续**                                         | `C`               | 控制台窗格，调试脚本时 |
| **步入**                                        | `S`               | 控制台窗格，调试脚本时 |
| **步越**                                        | `V`               | 控制台窗格，调试脚本时 |
| **步出**                                         | `O`               | 控制台窗格，调试脚本时 |
| 重复上一命令（用于步入或步越）  | <kbd>ENTER</kbd>  | 控制台窗格，调试脚本时 |
| **显示调用堆栈**                               | `K`               | 控制台窗格，调试脚本时 |
| **停止调试**                                   | `Q`               | 控制台窗格，调试脚本时 |
| **列出脚本**                                  | `L`               | 控制台窗格，调试脚本时 |
| **显示控制台调试命令**               | `H` 或 `?`        | 控制台窗格，调试脚本时 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 选项卡的键盘快捷方式

使用 Windows PowerShell 选项卡时，可使用以下键盘快捷方式。

|             操作              |                                                        键盘快捷方式                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **关闭 PowerShell 选项卡**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                                                                    |
| **新建 PowerShell 选项卡**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                                                                    |
| **上一个 PowerShell 选项卡**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd>。 此快捷键仅在所有 Windows PowerShell 选项卡上都未打开任何文件时可用。 |
| **下一个 Windows PowerShell 选项卡** | <kbd>CTRL</kbd>+<kbd>TAB</kbd>。 此快捷键仅在所有 Windows PowerShell 选项卡上都未打开任何文件时可用。                  |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>启动和退出的键盘快捷方式

可以使用以下键盘快捷方式来启动 Windows PowerShell 控制台 (PowerShell.exe) 或退出 Windows PowerShell ISE。

|                        操作                        |               键盘快捷方式               |
| ---------------------------------------------------- | --------------------------------------------- |
| **退出**                                             | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| PowerShell.exe  （Windows PowerShell 控制台） | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> |

## <a name="see-also"></a>另请参阅

- [PowerShell 杂志：Windows PowerShell ISE 键盘快捷键的完整列表](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)
