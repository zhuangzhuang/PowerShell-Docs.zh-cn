---
description: 介绍用于控制 PowerShell 如何解释序列中的下一个字符的特殊字符序列。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 7e0ea9298dd85627c08298917464cb005f4f37ff
ms.sourcegitcommit: 364c3fe46b2069b810107d840be59fe519ea7b4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100727"
---
# <a name="about-special-characters"></a>关于特殊字符

## <a name="short-description"></a>简短说明

介绍用于控制 PowerShell 如何解释序列中的下一个字符的特殊字符序列。

## <a name="long-description"></a>长说明

PowerShell 支持使用一组特殊字符序列来表示不属于标准字符集的字符。 序列通常称为 " _转义序列_"。

转义序列以反撇号字符开头，称为抑音符 (ASCII 96) ，区分大小写。 反撇号字符也可以称为 _转义字符_。

仅当转义序列包含在带双引号的 () 字符串中时，才会进行解释 `"` 。

PowerShell 可识别以下转义序列：

|  序列   |       说明       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | 警报                   |
| `` `b ``    | Backspace               |
| `` `f ``    | 换页               |
| `` `n ``    | 换行                |
| `` `r ``    | 回车         |
| `` `t ``    | 水平制表符          |
| `` `v ``    | 垂直制表符            |

PowerShell 还具有一个特殊的标记，用于标记要停止分析的位置。 跟在此标记后面的所有字符都用作未解释的文本值。

特殊分析令牌：

| 序列 |            说明             |
| -------- | ---------------------------------- |
| `--%`    | 停止分析下面的任何内容 |

## <a name="null-0"></a>Null ("0) 

Null (`` `0 ``) 字符在 PowerShell 输出中显示为空白区域。
此功能允许你使用 PowerShell 读取和处理使用空字符的文本文件，如字符串终止或记录终止指示器。 Null 特殊字符不等效于 `$null` 存储 **null** 值的变量。

## <a name="alert-a"></a>警报 ("a) 

警报 (`` `a ``) 字符将嘟嘟声信号发送到计算机的扬声器。
您可以使用此字符警告用户即将执行的操作。 下面的示例向本地计算机的扬声器发送两条嘟嘟声信号。

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>Backspace ("b) 

Backspace (`` `b ``) 字符将光标向后移动一个字符，但不会删除任何字符。

该示例将写入单词 **backup** ，然后将光标向后移动两次。
然后，在新位置写入一个空格，后跟单词 **out**。

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="form-feed-f"></a>换页符 ("f) 

 () 字符的窗体馈送 `` `f `` 是一种打印指令，用于弹出当前页面并继续在下一页上打印。 窗体馈送字符只影响打印文档。 它不会影响屏幕输出。

## <a name="new-line-n"></a>新行 (' n) 

新行 (`` `n ``) 字符直接在字符后面插入一个换行符。

此示例演示如何在命令中使用新行字符创建分行符 `Write-Host` 。

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>回车 (r) 

回车 (`` `r ``) 字符将输出光标移动到当前行的开头，并继续写入。 当前行上的任何字符都将被覆盖。

在此示例中，将覆盖回车符前的文本。

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

请注意，不会删除字符之前的文本 `` `r `` ，它会被覆盖。

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>水平选项卡 (不) 

"水平" 选项卡 (`` `t ``) 字符前进到下一个制表位，并在该点继续写入。 默认情况下，PowerShell 控制台每隔8个空格都有一个制表位。

此示例在每个列之间插入两个制表符。

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="vertical-tab-v"></a>垂直选项卡 ("v) 

"垂直" 选项卡 (`` `v ``) 字符前进到下一个垂直制表位，并在该点写入剩余的输出。 垂直选项卡的呈现是设备和终端相关的。

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

下面的示例演示了某些常见环境中的垂直选项卡的呈现输出。

Windows 控制台主机应用程序将 (`` `v ``) 解释为特殊字符，无需添加额外的间距。

```Output
There is a vertical tab♂between the words.
```

[Windows 终端](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701)将垂直制表符呈现为回车符和换行。 输出的其余部分将打印在下一行的开头。

```Output
There is a vertical tab
between the words.
```

在打印机上或基于 unix 的控制台中，垂直制表符前进到下一行，并在该点写入剩余的输出。

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>停止分析标记 (--% ) 

停止分析 (`--%`) 标记阻止 powershell 将字符串解释为 powershell 命令和表达式。 这允许将这些字符串传递到其他程序进行解释。

将停止解析标记放在程序名之后、可能导致错误的程序参数之前。

在此示例中，该 `Icacls` 命令使用了停止分析标记。

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell 将以下字符串发送到 `Icacls` 。

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

以下是另一个示例。 **ShowArgs** 函数输出传递给它的值。 在此示例中，我们将名为的变量传递 `$HOME` 到函数两次。

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

你可以在输出中看到，对于第一个参数，该变量 `$HOME` 由 PowerShell 进行解释，以便将该变量的值传递到函数。 的第二次使用 `$HOME` 出现在停止分析令牌之后，因此字符串 "$HOME" 将传递给函数，而不会被解释。

```Output
$args = C:\Users\username|--%|$HOME
```

有关停止分析令牌的详细信息，请参阅 [about_Parsing](about_Parsing.md)。

## <a name="see-also"></a>另请参阅

[about_Quoting_Rules](about_Quoting_Rules.md)
