---
description: PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于 PSReadLine
ms.openlocfilehash: b0c5950b2af6a866d0ffcfdd6ce7ad92a1763778
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500206"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>简短说明

PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。

## <a name="long-description"></a>详细说明

PSReadLine 2.2 为 PowerShell 控制台提供了强大的命令行编辑体验。 提供以下功能：

- 命令行的语法着色
- 语法错误的直观指示
-  (编辑和历史记录的更好的多行体验) 
- 自定义键绑定
- Cmd 和 Emacs 模式
- 许多配置选项
- 在 Cmd 模式下，Bash 样式完成 (可选，默认值为 Emacs 模式) 
- Emacs yank/kill 循环
- 基于 PowerShell 令牌的 "word" 移动和终止
- 预测 IntelliSense

PSReadLine 2.2.0 添加了两种新的预测 IntelliSense 功能：

- 添加了 **PredictionViewStyle** 参数，以允许选择新的 `ListView` 。
- 将 PSReadLine 连接到 `CommandPrediction` PS 7.1 中引入的 api 后，用户便可以导入可呈现自定义源的建议的预测器模块。

PSReadLine 需要 PowerShell 3.0 或更高版本。 PSReadLine 使用默认控制台主机、Visual Studio Code 和窗口终端。 它在 PowerShell ISE 中不起作用。

PSReadLine 2.2.0 随 PowerShell 7.2 一起提供，并在所有支持的 PowerShell 版本中受支持。 它可从 PowerShell 库安装。
若要在支持的 PowerShell 版本中安装 PSReadLine 2.2.0，请运行以下命令。

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> 从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。 目前，PSReadLine 不能与屏幕阅读器很好地配合使用。 Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。 如有必要，可以手动加载模块。

## <a name="predictive-intellisense"></a>预测 IntelliSense

预测 IntelliSense 是选项卡完成的补充，可帮助用户成功完成命令。 它使用户能够基于用户历史记录和其他域特定插件中的匹配预测来发现、编辑和执行完整命令。

### <a name="enable-predictive-intellisense"></a>启用预测 IntelliSense

默认情况下，禁用预测 IntelliSense。 若要启用预测，只需运行以下命令：

```powershell
Set-PSReadLineOption -PredictionSource History
```

**PredictionSource** 参数还可以接受插件特定于域和自定义的要求。

若要禁用预测 IntelliSense，只需运行：

```powershell
Set-PSReadLineOption -PredictionSource None
```

类 **[PSConsoleReadLine]** 中提供了以下函数。

## <a name="basic-editing-functions"></a>基本编辑函数

### <a name="abort"></a>中止

中止当前操作，例如增量历史记录搜索。

- Emacs `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

尝试执行当前输入。 如果可以 (如 AcceptLine) 执行，则在下一次调用 ReadLine 时，从历史记录中撤回下一项。

- Emacs `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

尝试执行当前输入。 如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。

- Cmd：`<Enter>`
- Emacs `<Enter>`
- Vi 插入模式： `<Enter>`

### <a name="addline"></a>AddLine

继续提示显示在下一行，PSReadLine 将等待键编辑当前输入。 这可用于将多行输入作为单个命令输入，即使单个行自动完成输入也是如此。

- Cmd：`<Shift+Enter>`
- Emacs `<Shift+Enter>`
- Vi 插入模式： `<Shift+Enter>`
- Vi 命令模式： `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

删除光标前面的字符。

- Cmd： `<Backspace>` ， `<Ctrl+h>`
- Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`
- Vi 插入模式： `<Backspace>`
- Vi 命令模式： `<X>` ， `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

与 BackwardKillLine 一样，从点到行的开头删除文本，但不会将删除的文本放入 kill 循环中。

- Cmd：`<Ctrl+Home>`
- Vi 插入模式： `<Ctrl+u>` ， `<Ctrl+Home>`
- Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

删除上一个词。

- Vi 命令模式： `<Ctrl+w>` ， `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

清除输入从输入开始到光标。 清除的文本会置于 kill 循环中。

- Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

清除从当前单词开头到光标的输入。 如果光标位于单词之间，则会从上一个字的开头到光标清除输入。 清除的文本会置于 kill 循环中。

- Cmd： `<Ctrl+Backspace>` ， `<Ctrl+w>`
- Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`
- Vi 插入模式： `<Ctrl+Backspace>`
- Vi 命令模式： `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

取消当前输入，将输入保留在屏幕上，但返回到主机以便再次计算提示。

- Vi 插入模式： `<Ctrl+c>`
- Vi 命令模式： `<Ctrl+c>`

### <a name="copy"></a>复制

将所选区域复制到系统剪贴板。 如果未选择区域，则复制整行。

- Cmd：`<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

如果选择了文本，请将其复制到剪贴板，否则取消该行。

- Cmd：`<Ctrl+c>`
- Emacs `<Ctrl+c>`

### <a name="cut"></a>剪切

删除所选区域将删除的文本放入系统剪贴板。

- Cmd：`<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

删除光标下的字符。

- Cmd：`<Delete>`
- Emacs `<Delete>`
- Vi 插入模式： `<Delete>`
- Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Spacebar>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

删除光标下的字符; 如果行为空，则退出该过程。

- Emacs `<Ctrl+d>`

### <a name="deleteendofbuffer"></a>DeleteEndOfBuffer

删除到多行缓冲区的末尾。

- Vi 命令模式： `<d,G>`

### <a name="deleteendofword"></a>DeleteEndOfWord

删除到单词的结尾。

- Vi 命令模式： `<d,e>`

### <a name="deleteline"></a>Deleteline.invoke

删除多行缓冲区的当前逻辑行，启用 "撤消"。

- Vi 命令模式： `<d,d>` ， `<d,_>`

### <a name="deletepreviouslines"></a>DeletePreviousLines

删除多行缓冲区中以前请求的逻辑行和当前逻辑行。

- Vi 命令模式： `<d,k>`

### <a name="deleterelativelines"></a>DeleteRelativeLines

从缓冲区的开头删除到多行缓冲区中的当前逻辑行。

作为最多 Vi 命令，该 `<d,g,g>` 命令可以用一个指定绝对行号的数值参数预置，这一数字参数与当前行号一起构成了要删除的行范围。
如果未指定，则数值参数默认为1，这表示多行缓冲区中的第一个逻辑行。

要从多行删除的实际行数将计算为当前逻辑行号和指定数值参数之间的差值，这可能是负数。 因此，方法名称的 _相关_ 部分。

- Vi 命令模式： `<d,g,g>`

### <a name="deletenextlines"></a>DeleteNextLines

删除多行缓冲区中的当前逻辑行和下一个请求的逻辑行。

- Vi 命令模式： `<d,j>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

删除多行缓冲区中当前逻辑行的第一个非空白字符。

- Vi 命令模式： `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

删除到行的末尾。

- Vi 命令模式： `<D>` ， `<d,$>`

### <a name="deleteword"></a>DeleteWord

删除下一个词。

- Vi 命令模式： `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

与 ForwardKillLine 一样，从点到行尾删除文本，但不会将删除的文本放入 kill 循环中。

- Cmd：`<Ctrl+End>`
- Vi 插入模式： `<Ctrl+End>`
- Vi 命令模式： `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

在当前行的上方创建新的空行，而不考虑光标在当前行上的位置。 光标移动到新行的开头。

- Cmd：`<Ctrl+Enter>`

### <a name="insertlinebelow"></a>InsertLineBelow

在当前行下方创建新的空行，而不考虑光标在当前行上的位置。 光标移动到新行的开头。

- Cmd：`<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

反转当前字符的大小写，并移到下一个字符。

- Vi 命令模式： `<~>`

### <a name="killline"></a>KillLine

清除从光标到输入末尾的输入。 清除的文本会置于 kill 循环中。

- Emacs `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

终止光标和标记之间的文本。

- 函数未绑定。

### <a name="killword"></a>KillWord

清除从光标到当前单词末尾的输入。 如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。 清除的文本会置于 kill 循环中。

- Cmd： `<Alt+d>` ， `<Ctrl+Delete>`
- Emacs： `<Alt+d>` ， `<Escape,d>`
- Vi 插入模式： `<Ctrl+Delete>`
- Vi 命令模式： `<Ctrl+Delete>`

### <a name="paste"></a>粘贴

粘贴系统剪贴板中的文本。

- Cmd： `<Ctrl+v>` ， `<Shift+Insert>`
- Vi 插入模式： `<Ctrl+v>`
- Vi 命令模式： `<Ctrl+v>`

> [!IMPORTANT]
> 使用 **Paste** 函数时，剪贴板缓冲区的全部内容将粘贴到 PSReadLine 的输入缓冲区中。 然后，将输入缓冲区传递到 PowerShell 分析器。 使用控制台应用程序的 **右键单击** 粘贴方法粘贴的输入会一次复制到输入缓冲区中的一个字符。 复制换行符时，输入缓冲区会传递到分析器。 因此，每次对输入进行一次分析。 Paste 方法之间的区别导致了不同的执行行为。

### <a name="pasteafter"></a>PasteAfter

在光标后面粘贴剪贴板，并将光标移动到粘贴文本的末尾。

- Vi 命令模式： `<p>`

### <a name="pastebefore"></a>PasteBefore

将剪贴板粘贴到光标之前，并将光标移动到粘贴文本的末尾。

- Vi 命令模式： `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

预置 "#" 并接受该行。

- Vi 命令模式： `<#>`

### <a name="redo"></a>重做

撤消撤消。

- Cmd：`<Ctrl+y>`
- Vi 插入模式： `<Ctrl+y>`
- Vi 命令模式： `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

重复最后一次文本修改。

- Vi 命令模式： `<.>`

### <a name="revertline"></a>RevertLine

将所有输入还原为当前输入。

- Cmd：`<Escape>`
- Emacs： `<Alt+r>` ， `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

清除从当前单词开头到光标的输入。 如果光标位于单词之间，则会从上一个字的开头到光标清除输入。 清除的文本会置于 kill 循环中。

函数未绑定。

### <a name="shellkillword"></a>ShellKillWord

清除从光标到当前单词末尾的输入。 如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。 清除的文本会置于 kill 循环中。

函数未绑定。

### <a name="swapcharacters"></a>SwapCharacters

交换当前字符和该字符之前的字符。

- Emacs `<Ctrl+t>`
- Vi 插入模式： `<Ctrl+t>`
- Vi 命令模式： `<Ctrl+t>`

### <a name="undo"></a>撤消

撤消上一个编辑。

- Cmd：`<Ctrl+z>`
- Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`
- Vi 插入模式： `<Ctrl+z>`
- Vi 命令模式： `<Ctrl+z>` ， `<u>`

### <a name="undoall"></a>UndoAll

撤消对行的所有以前的编辑。

- Vi 命令模式： `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

清除从当前单词开头到光标的输入。 如果光标位于单词之间，则会从上一个字的开头到光标清除输入。 清除的文本会置于 kill 循环中。

- Emacs `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

尝试执行当前输入。 如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。

- Emacs `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

接受行并切换到插入模式。

- Vi 命令模式： `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

与 Emacs 模式下的 DeleteCharOrExit 类似，但接受行而不是删除字符。

- Vi 插入模式： `<Ctrl+d>`
- Vi 命令模式： `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

新行插入到当前行的下方。

- Vi 命令模式： `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

删除上一个词，只使用空格作为单词分隔符。

- Vi 命令模式： `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

将光标移回上一个词的开头，仅使用空格作为分隔符。

- Vi 命令模式： `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

查找匹配的大括号、圆括号或方括号，并删除其中的所有内容，包括大括号。

- Vi 命令模式： `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

删除到单词的结尾。

- Vi 命令模式： `<d,E>`

### <a name="videleteglob"></a>ViDeleteGlob

删除下一个 glob (空格分隔的单词) 。

- Vi 命令模式： `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

删除到给定的字符。

- Vi 命令模式： `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

删除到给定的字符。

- Vi 命令模式： `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

删除到给定的字符。

- Vi 命令模式： `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

向后删除到给定的字符。

- Vi 命令模式： `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

切换到插入模式，并将光标置于行首。

- Vi 命令模式： `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

切换到插入模式，并将光标置于行的末尾。

- Vi 命令模式： `<A>`

### <a name="viinsertline"></a>ViInsertLine

在当前行的上方插入新行。

- Vi 命令模式： `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

从当前行位置追加。

- Vi 命令模式： `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

删除当前字符并切换到插入模式。

- Vi 命令模式： `<s>`

### <a name="vijoinlines"></a>ViJoinLines

联接当前行和下一行。

- Vi 命令模式： `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

擦除整个命令行。

- Vi 命令模式： `<S>` ， `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

替换到给定的字符。

- Vi 命令模式： `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

替换到给定的字符。

- Vi 命令模式： `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

删除到给定的字符。

- Vi 命令模式： `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

替换到给定的字符。

- Vi 命令模式： `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

从缓冲区的开头到游标的 Yank。

- Vi 命令模式： `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

从光标 Yank 到单词 (s) 的末尾。

- Vi 命令模式： `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

从光标 Yank 到单词 (s) 的末尾。

- Vi 命令模式： `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

Yank 字符 (s) 光标左侧。

- Vi 命令模式： `<y,h>`

### <a name="viyankline"></a>ViYankLine

Yank 整个缓冲区。

- Vi 命令模式： `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

Yank 从 cursor 到下一个单词 () 的开头。

- Vi 命令模式： `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

Yank 在游标后) 的单词 (。

- Vi 命令模式： `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

Yank 匹配的大括号。

- Vi 命令模式： `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

从单词 (开始，) 到游标。

- Vi 命令模式： `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

Yank 在游标前)  (s。

- Vi 命令模式： `<y,b>`

### <a name="viyankright"></a>ViYankRight

Yank 字符 (s) 光标右侧和右侧。

- Vi 命令模式： `<y,l>` ， `<y,Spacebar>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

Yank 从游标到缓冲区的末尾。

- Vi 命令模式： `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

从第一个非空白字符 Yank 到游标。

- Vi 命令模式： `<y,^>`

### <a name="yank"></a>Yank

将最近终止的文本添加到输入中。

- Emacs `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

Yank 上一个历史记录行中的最后一个参数。 如果使用参数，则第一次调用时，其行为就像 YankNthArg。 如果多次调用，则会循环访问历史记录，而 arg 会将方向设置 (负反转方向。 ) 

- Cmd：`<Alt+.>`
- Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

Yank 从上一历史记录行) 命令后 (第一个参数。
对于参数，yank 从 0) 开始 (第 n 个参数，如果参数为负数，则从最后一个参数开始。

- Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

如果上一操作是 Yank 或 YankPop，则将以前的拔掉文本替换为下一个终止的文本。

- Emacs： `<Alt+y>` ， `<Escape,y>`

## <a name="cursor-movement-functions"></a>游标移动函数

### <a name="backwardchar"></a>BackwardChar

将光标向左移动一个字符。 这可以将光标移到多行输入的上一行。

- Cmd：`<LeftArrow>`
- Emacs： `<LeftArrow>` ， `<Ctrl+b>`

### <a name="backwardword"></a>BackwardWord

将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。 字边界由一组可配置的字符集定义。

- Cmd：`<Ctrl+LeftArrow>`
- Emacs： `<Alt+b>` ， `<Escape,b>`
- Vi 插入模式： `<Ctrl+LeftArrow>`
- Vi 命令模式： `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

如果输入具有多个行，则移动到当前行的开头，或者，如果已位于行首，则移动到输入的开头。 如果输入具有单行，则移动到输入的开头。

- Cmd：`<Home>`
- Emacs： `<Home>` ， `<Ctrl+a>`
- Vi 插入模式： `<Home>`
- Vi 命令模式： `<Home>`

### <a name="endofline"></a>EndOfLine

如果输入包含多行，则移动到当前行的末尾，或者，如果已位于行尾，则转到输入的结尾。 如果输入具有单行，则移动到输入的末尾。

- Cmd：`<End>`
- Emacs： `<End>` ， `<Ctrl+e>`
- Vi 插入模式： `<End>`

### <a name="forwardchar"></a>ForwardChar

将光标向右移动一个字符。 这可能会将光标移到下一行的多行输入。

- Cmd：`<RightArrow>`
- Emacs： `<RightArrow>` ， `<Ctrl+f>`

### <a name="forwardword"></a>ForwardWord

将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。 字边界由一组可配置的字符集定义。

- Emacs： `<Alt+f>` ， `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

中转到匹配的大括号、圆括号或方括号。

- Cmd：`<Ctrl+]>`
- Vi 插入模式： `<Ctrl+]>`
- Vi 命令模式： `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

转到 arg 指示的列。

- Vi 命令模式： `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

将光标移动到行中的第一个非空白字符。

- Vi 命令模式： `<^>` ， `<_>`

### <a name="movetoendofline"></a>MoveToEndOfLine

将光标移到输入的末尾。

- Vi 命令模式： `<End>` ， `<$>`

### <a name="nextline"></a>NextLine

将光标移到下一行。

- 函数未绑定。

### <a name="nextword"></a>NextWord

将光标向前移动到下一个单词的开头。 字边界由一组可配置的字符集定义。

- Cmd：`<Ctrl+RightArrow>`
- Vi 插入模式： `<Ctrl+RightArrow>`
- Vi 命令模式： `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。 字边界由一组可配置的字符集定义。

- Vi 命令模式： `<e>`

### <a name="previousline"></a>PreviousLine

将光标移到上一行。

- 函数未绑定。

### <a name="shellbackwardword"></a>ShellBackwardWord

将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。 Word 边界由 PowerShell 令牌定义。

- 函数未绑定。

### <a name="shellforwardword"></a>ShellForwardWord

将光标向前移动到下一个单词的开头。 Word 边界由 PowerShell 令牌定义。

- 函数未绑定。

### <a name="shellnextword"></a>ShellNextWord

将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。 Word 边界由 PowerShell 令牌定义。

- 函数未绑定。

### <a name="vibackwardchar"></a>ViBackwardChar

在 Vi 编辑模式下将光标左移一个字符。 这可以将光标移到多行输入的上一行。

- Vi 插入模式： `<LeftArrow>`
- Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`

### <a name="vibackwardword"></a>ViBackwardWord

将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。 字边界由一组可配置的字符集定义。

- Vi 命令模式： `<b>`

### <a name="viforwardchar"></a>ViForwardChar

在 Vi 编辑模式下将光标向右移动一个字符。 这可能会将光标移到下一行的多行输入。

- Vi 插入模式： `<RightArrow>`
- Vi 命令模式： `<RightArrow>` 、 `<Spacebar>` 、 `<l>`

### <a name="viendofglob"></a>ViEndOfGlob

将光标移到单词的末尾，只使用空格作为分隔符。

- Vi 命令模式： `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

移到上一个词的末尾，只使用空格作为单词分隔符。

- 函数未绑定。

### <a name="vigotobrace"></a>ViGotoBrace

类似于 GotoBrace，但基于字符，而不是基于标记。

- Vi 命令模式： `<%>`

### <a name="vinextglob"></a>ViNextGlob

移到下一个单词，只使用空格作为单词分隔符。

- Vi 命令模式： `<W>`

### <a name="vinextword"></a>ViNextWord

将光标向前移动到下一个单词的开头。 字边界由一组可配置的字符集定义。

- Vi 命令模式： `<w>`

## <a name="history-functions"></a>历史记录函数

### <a name="beginningofhistory"></a>BeginningOfHistory

移到历史记录中的第一项。

- Emacs `<Alt+<>`

### <a name="clearhistory"></a>ClearHistory

清除 PSReadLine 中的历史记录。 这不会影响 PowerShell 历史记录。

- Cmd：`<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

移到历史记录中 (当前输入) 的最后一项。

- Emacs `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

通过历史记录执行增量向前搜索。

- Cmd：`<Ctrl+s>`
- Emacs `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

将当前输入替换为 PSReadLine 历史记录中的 "previous" 项，该匹配项与开始与输入和光标之间的字符匹配。

- Cmd：`<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

将当前输入替换为 PSReadLine 历史记录中与 start 与 input 和 cursor 之间的字符相匹配的 "next" 项。

- Cmd：`<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

将当前输入替换为 PSReadLine 历史记录中的 "next" 项。

- Cmd：`<DownArrow>`
- Emacs： `<DownArrow>` ， `<Ctrl+n>`
- Vi 插入模式： `<DownArrow>`
- Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`

### <a name="previoushistory"></a>PreviousHistory

将当前输入替换为 PSReadLine 历史记录中的 "previous" 项。

- Cmd：`<UpArrow>`
- Emacs： `<UpArrow>` ， `<Ctrl+p>`
- Vi 插入模式： `<UpArrow>`
- Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

通过历史记录执行增量向后搜索。

- Cmd：`<Ctrl+r>`
- Emacs `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

提示输入搜索字符串并在 AcceptLine 上开始搜索。

- Vi 插入模式： `<Ctrl+r>`
- Vi 命令模式： `</>` ， `<Ctrl+r>`

## <a name="completion-functions"></a>完成函数

### <a name="complete"></a>完成

尝试对光标周围的文本执行完成。 如果有多个可能的完成，则使用最长的明确前缀完成。 如果尝试完成最长的明确完成，则会显示一个可能的完成列表。

- Emacs `<Tab>`

### <a name="menucomplete"></a>MenuComplete

尝试对光标周围的文本执行完成。 如果有多个可能的完成，则使用最长的明确前缀完成。 如果尝试完成最长的明确完成，则会显示一个可能的完成列表。

- Cmd： `<Ctrl+@>` ， `<Ctrl+Spacebar>`
- Emacs `<Ctrl+Spacebar>`

### <a name="possiblecompletions"></a>PossibleCompletions

显示可能的完成列表。

- Emacs `<Alt+=>`
- Vi 插入模式： `<Ctrl+Spacebar>`
- Vi 命令模式： `<Ctrl+Spacebar>`

### <a name="tabcompletenext"></a>TabCompleteNext

尝试使用下一个可用完成来完成光标周围的文本。

- Cmd：`<Tab>`
- Vi 命令模式： `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

尝试使用以前的可用完成功能完成光标周围的文本。

- Cmd：`<Shift+Tab>`
- Vi 命令模式： `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

结束当前编辑组（如果需要），并调用 TabCompleteNext。

- Vi 插入模式： `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

结束当前编辑组（如果需要），并调用 TabCompletePrevious。

- Vi 插入模式： `<Shift+Tab>`

## <a name="prediction-functions"></a>预测函数

### <a name="acceptnextsuggestionword"></a>AcceptNextSuggestionWord

使用 `InlineView` 作为预测的视图样式时，请接受 "内联建议" 的下一个单词。

- 函数未绑定。

### <a name="acceptsuggestion"></a>AcceptSuggestion

使用 `InlineView` 作为预测的视图样式时，请接受当前内联建议。

- 函数未绑定。

### <a name="nextsuggestion"></a>NextSuggestion

使用 `ListView` 作为预测的视图样式时，导航到列表中的下一个建议。

- 函数未绑定。

### <a name="previoussuggestion"></a>PreviousSuggestion

使用 `ListView` 作为预测的视图样式时，导航到列表中的上一个建议。

- 函数未绑定。

### <a name="switchpredictionview"></a>SwitchPredictionView

切换与之间的预测的视图 `InlineView` 样式 `ListView` 。

- Cmd：`<F2>`

## <a name="miscellaneous-functions"></a>杂项函数

### <a name="capturescreen"></a>CaptureScreen

启动交互屏幕捕获-向上/向下箭头选择 "线条"，将选定文本作为文本和 html 复制到剪贴板。

- 函数未绑定。

### <a name="clearscreen"></a>ClearScreen

清除屏幕并在屏幕的顶部绘制当前线条。

- Cmd：`<Ctrl+l>`
- Emacs `<Ctrl+l>`
- Vi 插入模式： `<Ctrl+l>`
- Vi 命令模式： `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

启动新的数字参数，使其传递到其他函数。

- Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`
- Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`
- Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` 、 `<7>` 、 `<8>` 、 `<9>`

### <a name="invokeprompt"></a>InvokePrompt

清除当前提示符并调用 prompt 函数以重新显示提示符。 适用于更改状态的自定义密钥处理程序，例如更改当前目录。

- 函数未绑定。

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

将显示向下滚动一个屏幕。

- Cmd：`<PageDown>`
- Emacs `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

将显示向下滚动一行。

- Cmd：`<Ctrl+PageDown>`
- Emacs `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

将显示滚动到光标处。

- Emacs `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

向顶部滚动显示。

- Emacs `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

将显示向上滚动一屏。

- Cmd：`<PageUp>`
- Emacs `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

将显示向上滚动一行。

- Cmd：`<Ctrl+PageUp>`
- Emacs `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

插入密钥。

- 函数未绑定。

### <a name="showcommandhelp"></a>ShowCommandHelp

提供有关使用来自 **Microsoft PowerShell** 的页导航的替代屏幕缓冲区的完整 cmdlet 帮助视图。

- Cmd：`<F1>`
- Emacs `<F1>`
- Vi 插入模式： `<F1>`
- Vi 命令模式： `<F1>`

### <a name="showkeybindings"></a>ShowKeyBindings

显示所有绑定键。

- Cmd：`<Ctrl+Alt+?>`
- Emacs `<Ctrl+Alt+?>`
- Vi 插入模式： `<Ctrl+Alt+?>`

### <a name="showparameterhelp"></a>ShowParameterHelp

提供参数的动态帮助，方法是将其显示在当前命令行（如）下面 `MenuComplete` 。

- Cmd：`<Alt+h>`
- Emacs `<Alt+h>`
- Vi 插入模式： `<Alt+h>`
- Vi 命令模式： `<Alt+h>`

### <a name="vicommandmode"></a>ViCommandMode

将当前运行模式从 Vi-Insert 切换到 Vi-Command。

- Vi 插入模式： `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

启动新的数字参数，将其传递给其他函数，同时使用 vi 的鼠标左键之一。

- 函数未绑定。

### <a name="vieditvisually"></a>ViEditVisually

在 $env： EDITOR 或 $env：视觉对象指定的文本编辑器中编辑命令行。

- Emacs `<Ctrl+x,Ctrl+e>`
- Vi 命令模式： `<v>`

### <a name="viexit"></a>ViExit

退出 shell。

- 函数未绑定。

### <a name="viinsertmode"></a>ViInsertMode

切换到插入模式。

- Vi 命令模式： `<i>`

### <a name="whatiskey"></a>WhatIsKey

阅读密钥，并告诉我密钥的绑定内容。

- Cmd：`<Alt+?>`
- Emacs `<Alt+?>`

## <a name="selection-functions"></a>选择函数

### <a name="exchangepointandmark"></a>ExchangePointAndMark

将光标置于标记的位置，并将标记移到光标所在的位置。

- Emacs `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll

选择整行。

- Cmd：`<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

调整当前选定内容以包括前一个字符。

- Cmd：`<Shift+LeftArrow>`
- Emacs `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

调整当前所选内容，使其包括从光标到行的开头。

- Cmd：`<Shift+Home>`
- Emacs `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

调整当前所选内容以包含上一个词。

- Cmd：`<Shift+Ctrl+LeftArrow>`
- Emacs `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

调整当前所选内容以包含下一个字符。

- Cmd：`<Shift+RightArrow>`
- Emacs `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

使用 ForwardWord 调整当前所选内容以包含下一个单词。

- Emacs `<Alt+F>`

### <a name="selectline"></a>SelectLine

调整当前所选内容，使其包括从光标到行尾的内容。

- Cmd：`<Shift+End>`
- Emacs `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

调整当前所选内容以包含下一个单词。

- Cmd：`<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

使用 ShellBackwardWord 调整当前所选内容，使其包含前一词。

- 函数未绑定。

### <a name="selectshellforwardword"></a>SelectShellForwardWord

使用 ShellForwardWord 调整当前所选内容以包含下一个单词。

- 函数未绑定。

### <a name="selectshellnextword"></a>SelectShellNextWord

使用 ShellNextWord 调整当前所选内容以包含下一个单词。

- 函数未绑定。

### <a name="setmark"></a>SetMark

标记光标的当前位置，以供后续编辑命令使用。

- Emacs `<Ctrl+@>`

## <a name="predictive-intellisense-functions"></a>预测 IntelliSense 函数

> [!NOTE]
> 需要启用预测 IntelliSense 才能使用这些功能。

### <a name="acceptnextwordsuggestion"></a>AcceptNextWordSuggestion

接受预测 IntelliSense 中的下一个内嵌建议词。
此函数可以<kbd></kbd> + 通过运行以下命令与 Ctrl<kbd>F</kbd>绑定。

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a>AcceptSuggestion

当光标位于当前行的末尾时，通过按 <kbd>右箭头</kbd> ，接受预测 IntelliSense 中的当前内联建议。

## <a name="search-functions"></a>搜索函数

### <a name="charactersearch"></a>CharacterSearch

读取字符并向前搜索该字符的下一个匹配项。
如果指定了参数，则向前搜索 (或向后) 对于第 n 个匹配项为负。

- Cmd：`<F3>`
- Emacs `<Ctrl+]>`
- Vi 插入模式： `<F3>`
- Vi 命令模式： `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

读取字符并向后搜索该字符的下一个匹配项。 如果指定了参数，则在第 n 个匹配项) 反向搜索时 (或转发。

- Cmd：`<Shift+F3>`
- Emacs `<Ctrl+Alt+]>`
- Vi 插入模式： `<Shift+F3>`
- Vi 命令模式： `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

重复上次记录的字符搜索。

- Vi 命令模式： `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

重复上次记录的字符搜索，但采用相反方向。

- Vi 命令模式： `<,>`

### <a name="repeatsearch"></a>RepeatSearch

像以前一样，重复最后一个搜索。

- Vi 命令模式： `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

像以前一样，重复最后一个搜索。

- Vi 命令模式： `<N>`

### <a name="searchchar"></a>SearchChar

阅读下一个字符，然后查找、前进，然后再返回一个字符。 这适用于 "t" 功能。

- Vi 命令模式： `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

读取下一个字符，然后查找它，向后移动，然后再返回一个字符。 这适用于 "t" 功能。

- Vi 命令模式： `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

读取下一个字符，然后查找它，向后移动，然后再返回一个字符。 这适用于 "t" 功能。

- Vi 命令模式： `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

阅读下一个字符，然后查找、前进，然后再返回一个字符。 这适用于 "t" 功能。

- Vi 命令模式： `<t>`

### <a name="searchforward"></a>SearchForward

提示输入搜索字符串并在 AcceptLine 上开始搜索。

- Vi 插入模式： `<Ctrl+s>`
- Vi 命令模式： `<?>` ， `<Ctrl+s>`

## <a name="custom-key-bindings"></a>自定义键绑定

PSReadLine 支持使用 cmdlet 的自定义键绑定 `Set-PSReadLineKeyHandler` 。 大多数自定义键绑定调用上述函数之一，例如

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

可以将 ScriptBlock 绑定到密钥。 ScriptBlock 可以执行任何所需的操作。 一些有用的示例包括

- 编辑命令行
- 打开新窗口 (例如，帮助) 
- 更改目录而不更改命令行

ScriptBlock 接收两个参数：

- `$key` -一个作为触发自定义绑定的密钥的 **[ConsoleKeyInfo]** 对象。 如果将相同的 ScriptBlock 绑定到多个键，并且需要根据关键字执行不同的操作，则可以选中 $key。 许多自定义绑定会忽略此参数。

- `$arg` -任意参数。 大多数情况下，这将是用户从键绑定 DigitArgument 传递的整数参数。 如果绑定不接受参数，则忽略此参数是合理的。

我们来看一个示例，该示例将一个命令行添加到历史记录中，而不执行它。 如果您认为您忘记了某些事情，但又不想重新输入您已经输入的命令行，这会很有用。

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

你可以在 PSReadLine 模块文件夹中安装的文件中查看更多示例 `SamplePSReadLineProfile.ps1` 。

大多数键绑定使用一些 helper 函数来编辑命令行。
下一节将介绍这些 Api。

## <a name="custom-key-binding-support-apis"></a>自定义键绑定支持 Api

以下函数是 PSConsoleReadLine 中的公共函数，但不能直接绑定到密钥。 大多数在自定义键绑定中很有用。

```csharp
void AddToHistory(string command)
```

向历史记录中添加一个命令行而不执行它。

```csharp
void ClearKillRing()
```

清除终止环。  这主要用于测试。

```csharp
void Delete(int start, int length)
```

从开始删除长度字符。  此操作支持撤消/重做。

```csharp
void Ding()
```

根据用户首选项执行 Ding 操作。

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

这两个函数检索有关输入缓冲区的当前状态的有用信息。  第一种方案更常见用于简单情况。  如果绑定使用 Ast 执行更高级的操作，则会使用第二个。

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

这两个函数由使用 `Get-PSReadLineKeyHandler` 。 第一个用于获取所有键绑定。 第二个用于获取特定的键绑定。

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

此函数由 Get-PSReadLineOption 使用，并可能在自定义键绑定中不太有用。

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

如果未在命令行上进行选择，则将在 "开始" 和 "长度" 中返回-1。 如果命令行上有选择，则返回选定内容的开始和长度。

```csharp
void Insert(char c)
void Insert(string s)
```

在光标处插入字符或字符串。  此操作支持撤消/重做。

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

这是 PSReadLine 的主要入口点。 它不支持递归，因此在自定义键绑定中不起作用。

```csharp
void RemoveKeyHandler(string[] key)
```

此函数由 Remove-PSReadLineKeyHandler 使用，并可能在自定义键绑定中不太有用。

```csharp
void Replace(int start, int length, string replacement)
```

替换部分输入。 此操作支持撤消/重做。 这优先于删除后再执行 Insert，因为它被视为单个操作来撤消。

```csharp
void SetCursorPosition(int cursor)
```

将光标移动到给定偏移量。 不跟踪游标移动以便撤消。

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

此函数是 cmdlet PSReadLineOption 使用的帮助器方法，但可能对要临时更改设置的自定义密钥绑定很有用。

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

此帮助器方法用于接受 DigitArgument 的自定义绑定。 典型调用如下所示

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a>说明

### <a name="command-history"></a>命令历史记录

PSReadLine 维护一个历史记录文件，其中包含在命令行中输入的所有命令和数据。 这可能包含敏感数据（包括密码）。 例如，如果使用 cmdlet，则 `ConvertTo-SecureString` 密码将作为纯文本记录到历史记录文件中。 历史记录文件是一个名为的文件 `$($host.Name)_history.txt` 。 在 Windows 系统上，历史记录文件存储在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。 在非 Windows 系统上，历史记录文件存储在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或上 `$env:HOME/.local/share/powershell/PSReadLine` 。

### <a name="feedback--contributing-to-psreadline"></a>参与 PSReadLine 的反馈 &

[GitHub 上的 PSReadLine](https://github.com/PowerShell/PSReadLine)

可在 GitHub 页上随意提交拉取请求或提交反馈。

## <a name="see-also"></a>另请参阅

PSReadLine 会受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 库的严重影响。
