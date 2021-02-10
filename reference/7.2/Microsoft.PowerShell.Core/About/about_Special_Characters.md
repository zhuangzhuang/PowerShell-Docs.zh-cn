---
description: 介绍用于控制 PowerShell 如何解释序列中的下一个字符的特殊字符序列。
Locale: en-US
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: b21ec1eb5ed0da52cf5eff01eaf3c220d117cf55
ms.sourcegitcommit: 364c3fe46b2069b810107d840be59fe519ea7b4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100710"
---
# <a name="about-special-characters"></a><span data-ttu-id="0d4c2-103">关于特殊字符</span><span class="sxs-lookup"><span data-stu-id="0d4c2-103">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="0d4c2-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="0d4c2-104">Short description</span></span>

<span data-ttu-id="0d4c2-105">介绍用于控制 PowerShell 如何解释序列中的下一个字符的特殊字符序列。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-105">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="0d4c2-106">长说明</span><span class="sxs-lookup"><span data-stu-id="0d4c2-106">Long description</span></span>

<span data-ttu-id="0d4c2-107">PowerShell 支持使用一组特殊字符序列来表示不属于标准字符集的字符。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-107">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="0d4c2-108">序列通常称为 " _转义序列_"。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-108">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="0d4c2-109">转义序列以反撇号字符开头，称为抑音符 (ASCII 96) ，区分大小写。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-109">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="0d4c2-110">反撇号字符也可以称为 _转义字符_。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-110">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="0d4c2-111">仅当转义序列包含在带双引号的 () 字符串中时，才会进行解释 `"` 。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-111">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="0d4c2-112">PowerShell 可识别以下转义序列：</span><span class="sxs-lookup"><span data-stu-id="0d4c2-112">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="0d4c2-113">序列</span><span class="sxs-lookup"><span data-stu-id="0d4c2-113">Sequence</span></span>   |       <span data-ttu-id="0d4c2-114">说明</span><span class="sxs-lookup"><span data-stu-id="0d4c2-114">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="0d4c2-115">Null</span><span class="sxs-lookup"><span data-stu-id="0d4c2-115">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="0d4c2-116">警报</span><span class="sxs-lookup"><span data-stu-id="0d4c2-116">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="0d4c2-117">Backspace</span><span class="sxs-lookup"><span data-stu-id="0d4c2-117">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="0d4c2-118">Escape</span><span class="sxs-lookup"><span data-stu-id="0d4c2-118">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="0d4c2-119">换页</span><span class="sxs-lookup"><span data-stu-id="0d4c2-119">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="0d4c2-120">换行</span><span class="sxs-lookup"><span data-stu-id="0d4c2-120">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="0d4c2-121">回车</span><span class="sxs-lookup"><span data-stu-id="0d4c2-121">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="0d4c2-122">水平制表符</span><span class="sxs-lookup"><span data-stu-id="0d4c2-122">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="0d4c2-123">Unicode 转义序列</span><span class="sxs-lookup"><span data-stu-id="0d4c2-123">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="0d4c2-124">垂直制表符</span><span class="sxs-lookup"><span data-stu-id="0d4c2-124">Vertical tab</span></span>            |

<span data-ttu-id="0d4c2-125">PowerShell 还具有一个特殊的标记，用于标记要停止分析的位置。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-125">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="0d4c2-126">跟在此标记后面的所有字符都用作未解释的文本值。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-126">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="0d4c2-127">特殊分析令牌：</span><span class="sxs-lookup"><span data-stu-id="0d4c2-127">Special parsing token:</span></span>

| <span data-ttu-id="0d4c2-128">序列</span><span class="sxs-lookup"><span data-stu-id="0d4c2-128">Sequence</span></span> |            <span data-ttu-id="0d4c2-129">说明</span><span class="sxs-lookup"><span data-stu-id="0d4c2-129">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="0d4c2-130">停止分析下面的任何内容</span><span class="sxs-lookup"><span data-stu-id="0d4c2-130">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="0d4c2-131">Null ("0) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-131">Null (\`0)</span></span>

<span data-ttu-id="0d4c2-132">Null (`` `0 ``) 字符在 PowerShell 输出中显示为空白区域。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-132">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="0d4c2-133">此功能允许你使用 PowerShell 读取和处理使用空字符的文本文件，如字符串终止或记录终止指示器。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-133">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="0d4c2-134">Null 特殊字符不等效于 `$null` 存储 **null** 值的变量。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-134">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="0d4c2-135">警报 ("a) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-135">Alert (\`a)</span></span>

<span data-ttu-id="0d4c2-136">警报 (`` `a ``) 字符将嘟嘟声信号发送到计算机的扬声器。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-136">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="0d4c2-137">您可以使用此字符警告用户即将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-137">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="0d4c2-138">下面的示例向本地计算机的扬声器发送两条嘟嘟声信号。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-138">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="0d4c2-139">Backspace ("b) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-139">Backspace (\`b)</span></span>

<span data-ttu-id="0d4c2-140">Backspace (`` `b ``) 字符将光标向后移动一个字符，但不会删除任何字符。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-140">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="0d4c2-141">该示例将写入单词 **backup** ，然后将光标向后移动两次。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-141">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="0d4c2-142">然后，在新位置写入一个空格，后跟单词 **out**。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-142">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="0d4c2-143">转义 ("e) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-143">Escape (\`e)</span></span>

<span data-ttu-id="0d4c2-144">转义 (`` `e ``) 字符最常用于指定 (ANSI 转义) 序列的虚拟终端序列，该序列用于修改文本和其他文本属性（例如粗体和下划线）的颜色。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-144">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="0d4c2-145">这些序列还可以用于游标定位和滚动。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-145">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="0d4c2-146">PowerShell 主机必须支持虚拟终端序列。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-146">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="0d4c2-147">您可以检查的布尔值 `$Host.UI.SupportsVirtualTerminal` ，以确定是否支持这些 ANSI 序列。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-147">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="0d4c2-148">有关 ANSI 转义序列的详细信息，请参阅 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-148">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="0d4c2-149">下面的示例使用绿色前景颜色输出文本。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-149">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="0d4c2-150">换页符 ("f) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-150">Form feed (\`f)</span></span>

<span data-ttu-id="0d4c2-151"> () 字符的窗体馈送 `` `f `` 是一种打印指令，用于弹出当前页面并继续在下一页上打印。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-151">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="0d4c2-152">窗体馈送字符只影响打印文档。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-152">The form feed character only affects printed documents.</span></span> <span data-ttu-id="0d4c2-153">它不会影响屏幕输出。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-153">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="0d4c2-154">新行 (' n) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-154">New line (\`n)</span></span>

<span data-ttu-id="0d4c2-155">新行 (`` `n ``) 字符直接在字符后面插入一个换行符。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-155">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="0d4c2-156">此示例演示如何在命令中使用新行字符创建分行符 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-156">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="0d4c2-157">回车 (r) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-157">Carriage return (\`r)</span></span>

<span data-ttu-id="0d4c2-158">回车 (`` `r ``) 字符将输出光标移动到当前行的开头，并继续写入。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-158">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="0d4c2-159">当前行上的任何字符都将被覆盖。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-159">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="0d4c2-160">在此示例中，将覆盖回车符前的文本。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-160">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="0d4c2-161">请注意，不会删除字符之前的文本 `` `r `` ，它会被覆盖。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-161">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="0d4c2-162">水平选项卡 (不) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-162">Horizontal tab (\`t)</span></span>

<span data-ttu-id="0d4c2-163">"水平" 选项卡 (`` `t ``) 字符前进到下一个制表位，并在该点继续写入。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-163">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="0d4c2-164">默认情况下，PowerShell 控制台每隔8个空格都有一个制表位。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-164">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="0d4c2-165">此示例在每个列之间插入两个制表符。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-165">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="0d4c2-166">Unicode 字符 ("u {x} ) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-166">Unicode character (\`u{x})</span></span>

<span data-ttu-id="0d4c2-167">Unicode 转义序列 (`` `u{x} ``) 使你可以通过其码位的十六进制表示形式指定任何 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-167">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="0d4c2-168">这包括基本多语言平面上的 Unicode 字符 ( # A0 `0xFFFF`) 包含表情符号字符（如 **大拇指** (`` `u{1F44D} ``) 字符）。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-168">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="0d4c2-169">Unicode 转义序列需要至少一个十六进制数字，并且最多支持六个十六进制数字。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-169">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="0d4c2-170">序列的最大十六进制值为 `10FFFF` 。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-170">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="0d4c2-171">此示例输出 ( # A0) 符号的 **向上向下箭头** 。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-171">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="0d4c2-172">垂直选项卡 ("v) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-172">Vertical tab (\`v)</span></span>

<span data-ttu-id="0d4c2-173">"垂直" 选项卡 (`` `v ``) 字符前进到下一个垂直制表位，并在该点写入剩余的输出。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-173">The vertical tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="0d4c2-174">垂直选项卡的呈现是设备和终端相关的。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-174">The rendering of the the vertical tab is device and terminal dependent.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="0d4c2-175">下面的示例演示了某些常见环境中的垂直选项卡的呈现输出。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-175">The following examples show the rendered output of the vertical tab in some common environments.</span></span>

<span data-ttu-id="0d4c2-176">Windows 控制台主机应用程序将 (`` `v ``) 解释为特殊字符，无需添加额外的间距。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-176">The Windows Console host application interprets (`` `v ``) as a special character with no extra spacing added.</span></span>

```Output
There is a vertical tab♂between the words.
```

<span data-ttu-id="0d4c2-177">[Windows 终端](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701)将垂直制表符呈现为回车符和换行。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-177">The [Windows Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) renders the vertical tab character as a carriage return and line feed.</span></span> <span data-ttu-id="0d4c2-178">输出的其余部分将打印在下一行的开头。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-178">The rest of the output is printed at the beginning of the next line.</span></span>

```Output
There is a vertical tab
between the words.
```

<span data-ttu-id="0d4c2-179">在打印机上或基于 unix 的控制台中，垂直制表符前进到下一行，并在该点写入剩余的输出。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-179">On printers or in a unix-based consoles, the vertical tab character advances to the next line and writes the remaining output at that point.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="0d4c2-180">停止分析标记 (--% ) </span><span class="sxs-lookup"><span data-stu-id="0d4c2-180">Stop-parsing token (--%)</span></span>

<span data-ttu-id="0d4c2-181">停止分析 (`--%`) 标记阻止 powershell 将字符串解释为 powershell 命令和表达式。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-181">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="0d4c2-182">这允许将这些字符串传递到其他程序进行解释。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-182">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="0d4c2-183">将停止解析标记放在程序名之后、可能导致错误的程序参数之前。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-183">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="0d4c2-184">在此示例中，该 `Icacls` 命令使用了停止分析标记。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-184">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="0d4c2-185">PowerShell 将以下字符串发送到 `Icacls` 。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-185">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="0d4c2-186">以下是另一个示例。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-186">Here is another example.</span></span> <span data-ttu-id="0d4c2-187">**ShowArgs** 函数输出传递给它的值。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-187">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="0d4c2-188">在此示例中，我们将名为的变量传递 `$HOME` 到函数两次。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-188">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

你可以在输出中看到，对于第一个参数，该变量 `$HOME` 由 PowerShell 进行解释，以便将该变量的值传递到函数。 <span data-ttu-id="0d4c2-190">的第二次使用 `$HOME` 出现在停止分析令牌之后，因此字符串 "$HOME" 将传递给函数，而不会被解释。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-190">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="0d4c2-191">有关停止分析令牌的详细信息，请参阅 [about_Parsing](about_Parsing.md)。</span><span class="sxs-lookup"><span data-stu-id="0d4c2-191">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d4c2-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d4c2-192">See also</span></span>

[<span data-ttu-id="0d4c2-193">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="0d4c2-193">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

