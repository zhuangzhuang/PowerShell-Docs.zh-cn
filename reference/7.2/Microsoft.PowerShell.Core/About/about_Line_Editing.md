---
description: 描述如何在 PowerShell 命令提示符处编辑命令。
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 2b9a320b92bc0a61efc9f9ed75078b17cdd9cbc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599055"
---
# <a name="about-line-editing"></a>关于行编辑

## <a name="short-description"></a>简短说明

描述如何在 PowerShell 命令提示符处编辑命令。

## <a name="long-description"></a>长说明

PowerShell 控制台提供了一些有用的键盘快捷方式，可帮助你在 PowerShell 命令提示符下编辑命令。

### <a name="add-a-line"></a>添加线条

若要添加行，请按<kbd>Shift</kbd> + <kbd>enter</kbd>。

您可以添加多个行。 每增加一行都以开头 `>>` ，即继续提示。 按 <kbd>enter</kbd> 执行该命令。

### <a name="move-left-and-right"></a>向左和向右移动

若要将光标左移一个字符，请按 <kbd>向左键</kbd>。

若要将光标左移一个字，请按<kbd>Ctrl</kbd> + <kbd>向左键</kbd>。

若要将光标向右移动一个字符，请按 <kbd>向右箭头</kbd>。

若要将光标向右移动一个单词，请按<kbd>Ctrl</kbd> + <kbd>向右箭头</kbd>。

### <a name="move-to-a-lines-beginning-or-end"></a>移到行的开头或结尾

若要移动到行首，请按 <kbd>Home</kbd>。

若要移动到行尾，请按 <kbd>end</kbd>。

如果已添加行，请按 <kbd>Home</kbd> 或 <kbd>end</kbd> 两次，移动到行的开头或结尾。

### <a name="delete-characters"></a>删除字符

若要删除光标位置后面的字符，请按 <kbd>Backspace</kbd>。

若要删除光标位置的字符，请按 <kbd>delete</kbd>。

### <a name="delete-characters-from-a-line"></a>删除行中的字符

若要删除从光标位置到行尾的所有字符，请按<kbd>Ctrl</kbd> + <kbd>end</kbd>。

若要删除从光标位置到行首的所有字符，请按<kbd>Ctrl</kbd> + <kbd>Home</kbd>。

如果已添加行，则从当前行和已添加的行中删除字符。

### <a name="insert-and-overstrike-mode"></a>Insert 和替换模式

若要更改为覆盖模式，请按 <kbd>Insert</kbd>。 若要返回到插入模式，请再次按 <kbd>insert</kbd> 。

### <a name="tab-completion"></a>Tab 自动补全

若要完成 cmdlet 名称、参数或路径，请按 <kbd>tab</kbd> 键。 若要在值列表中滚动，请再次按 <kbd>tab</kbd> 键。

## <a name="see-also"></a>请参阅

[about_Command_Syntax](about_Command_Syntax.md)

[about_Path_Syntax](about_Path_Syntax.md)

[about_PSReadline](../../PSReadline/About/about_PSReadline.md)

