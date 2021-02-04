---
description: 描述在 PowerShell 中使用单引号和双引号的规则。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 27d5909c1381c0d221690b353a308680643ecad5
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490748"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="c3f13-103">关于报价规则</span><span class="sxs-lookup"><span data-stu-id="c3f13-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="c3f13-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="c3f13-104">Short description</span></span>
<span data-ttu-id="c3f13-105">描述在 PowerShell 中使用单引号和双引号的规则。</span><span class="sxs-lookup"><span data-stu-id="c3f13-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c3f13-106">长说明</span><span class="sxs-lookup"><span data-stu-id="c3f13-106">Long description</span></span>

<span data-ttu-id="c3f13-107">引号用于指定文本字符串。</span><span class="sxs-lookup"><span data-stu-id="c3f13-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="c3f13-108">可以用单引号将字符串括起来 (`'`) 或双引号 (`"`) 。</span><span class="sxs-lookup"><span data-stu-id="c3f13-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="c3f13-109">引号还用于创建 _此处字符串_。</span><span class="sxs-lookup"><span data-stu-id="c3f13-109">Quotation marks are also used to create a _here-string_.</span></span> <span data-ttu-id="c3f13-110">此处-字符串是用单引号或双引号括起来的字符串，其中的引号按原义解释。</span><span class="sxs-lookup"><span data-stu-id="c3f13-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="c3f13-111">此处的字符串可以跨多个行。</span><span class="sxs-lookup"><span data-stu-id="c3f13-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="c3f13-112">此处字符串中的所有行都被解释为字符串，即使它们没有用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="c3f13-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="c3f13-113">在远程计算机的命令中，引号定义在远程计算机上运行的命令的各个部分。</span><span class="sxs-lookup"><span data-stu-id="c3f13-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="c3f13-114">在远程会话中，引号还确定命令中的变量是在本地计算机上还是在远程计算机上首先解释。</span><span class="sxs-lookup"><span data-stu-id="c3f13-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

## <a name="single-and-double-quoted-strings"></a><span data-ttu-id="c3f13-115">单引号和双引号字符串</span><span class="sxs-lookup"><span data-stu-id="c3f13-115">Single and double-quoted strings</span></span>

<span data-ttu-id="c3f13-116">用双引号引起来的字符串是一个 _可扩展_ 字符串。</span><span class="sxs-lookup"><span data-stu-id="c3f13-116">A string enclosed in double quotation marks is an _expandable_ string.</span></span> <span data-ttu-id="c3f13-117">前面带有美元符号 () 的变量名称 `$` 将替换为该变量的值，然后将该字符串传递到命令进行处理。</span><span class="sxs-lookup"><span data-stu-id="c3f13-117">Variable names preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="c3f13-118">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="c3f13-119">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="c3f13-120">此外，在带双引号的字符串中，将计算表达式，并将结果插入字符串中。</span><span class="sxs-lookup"><span data-stu-id="c3f13-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="c3f13-121">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="c3f13-122">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="c3f13-123">用单引号括起来的字符串是 _原义_ 字符串。</span><span class="sxs-lookup"><span data-stu-id="c3f13-123">A string enclosed in single-quotation marks is a _verbatim_ string.</span></span> <span data-ttu-id="c3f13-124">当你键入内容时，字符串将传递给命令。</span><span class="sxs-lookup"><span data-stu-id="c3f13-124">The string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="c3f13-125">不执行任何替换。</span><span class="sxs-lookup"><span data-stu-id="c3f13-125">No substitution is performed.</span></span>
<span data-ttu-id="c3f13-126">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-126">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="c3f13-127">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-127">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="c3f13-128">同样，不计算用单引号字符串括起来的表达式。</span><span class="sxs-lookup"><span data-stu-id="c3f13-128">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="c3f13-129">它们被解释为文本。</span><span class="sxs-lookup"><span data-stu-id="c3f13-129">They are interpreted as literals.</span></span> <span data-ttu-id="c3f13-130">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-130">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="c3f13-131">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-131">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="c3f13-132">若要防止用双引号替换变量值，请使用反撇号字符 (`` ` ``) # B2 ASCII 96) ，这是 PowerShell 转义符。</span><span class="sxs-lookup"><span data-stu-id="c3f13-132">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="c3f13-133">在下面的示例中，第一个变量之前的反撇号字符 `$i` 会阻止 PowerShell 将变量名称替换为其值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-133">In the following example, the backtick character that precedes the first `$i` variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="c3f13-134">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-134">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="c3f13-135">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-135">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="c3f13-136">若要使双引号出现在字符串中，请将整个字符串用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="c3f13-136">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="c3f13-137">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-137">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="c3f13-138">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-138">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="c3f13-139">还可以在带引号的字符串中包含单引号字符串。</span><span class="sxs-lookup"><span data-stu-id="c3f13-139">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="c3f13-140">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-140">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="c3f13-141">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-141">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="c3f13-142">或者，用双引号将引号括起来。</span><span class="sxs-lookup"><span data-stu-id="c3f13-142">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="c3f13-143">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-143">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="c3f13-144">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-144">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="c3f13-145">若要在单引号字符串中包含单引号，请使用第二个连续的单引号。</span><span class="sxs-lookup"><span data-stu-id="c3f13-145">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="c3f13-146">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-146">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="c3f13-147">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-147">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="c3f13-148">若要强制 PowerShell 按字面解释双引号，请使用反撇号字符。</span><span class="sxs-lookup"><span data-stu-id="c3f13-148">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="c3f13-149">这会阻止 PowerShell 将引号解释为字符串分隔符。</span><span class="sxs-lookup"><span data-stu-id="c3f13-149">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="c3f13-150">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-150">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="c3f13-151">由于单引号字符串的内容按原义解释，因此，反撇号字符被视为文本字符并显示在输出中。</span><span class="sxs-lookup"><span data-stu-id="c3f13-151">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

## <a name="here-strings"></a><span data-ttu-id="c3f13-152">此处-字符串</span><span class="sxs-lookup"><span data-stu-id="c3f13-152">Here-strings</span></span>

<span data-ttu-id="c3f13-153">此处的引号规则与字符串略有不同。</span><span class="sxs-lookup"><span data-stu-id="c3f13-153">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="c3f13-154">此处-字符串是用单引号或双引号括起来的字符串，其中的引号按原义解释。</span><span class="sxs-lookup"><span data-stu-id="c3f13-154">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="c3f13-155">此处的字符串可以跨多个行。</span><span class="sxs-lookup"><span data-stu-id="c3f13-155">A here-string can span multiple lines.</span></span> <span data-ttu-id="c3f13-156">此处字符串中的所有行都被解释为字符串，即使它们没有用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="c3f13-156">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="c3f13-157">与规则字符串一样，变量在此处用双引号引起来。</span><span class="sxs-lookup"><span data-stu-id="c3f13-157">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="c3f13-158">在此处使用单引号的字符串中，变量的值不会被替换。</span><span class="sxs-lookup"><span data-stu-id="c3f13-158">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="c3f13-159">对于任何文本，您可以使用此处的字符串，但对于以下类型的文本特别有用：</span><span class="sxs-lookup"><span data-stu-id="c3f13-159">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="c3f13-160">包含文本引号的文本</span><span class="sxs-lookup"><span data-stu-id="c3f13-160">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="c3f13-161">多行文本，如 HTML 或 XML 中的文本</span><span class="sxs-lookup"><span data-stu-id="c3f13-161">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="c3f13-162">脚本或函数文档的帮助文本</span><span class="sxs-lookup"><span data-stu-id="c3f13-162">The Help text for a script or function document</span></span>

<span data-ttu-id="c3f13-163">此处的字符串可以采用以下两种格式之一，其中 `<Enter>` 表示按下 <kbd>enter</kbd> 键时添加的换行符或换行符。</span><span class="sxs-lookup"><span data-stu-id="c3f13-163">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="c3f13-164">双引号：</span><span class="sxs-lookup"><span data-stu-id="c3f13-164">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="c3f13-165">单引号：</span><span class="sxs-lookup"><span data-stu-id="c3f13-165">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="c3f13-166">无论采用哪种格式，右引号都必须是行中的第一个字符。</span><span class="sxs-lookup"><span data-stu-id="c3f13-166">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="c3f13-167">此处-字符串包含两个隐藏字符之间的所有文本。</span><span class="sxs-lookup"><span data-stu-id="c3f13-167">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="c3f13-168">在此处字符串中，所有引号都按原义解释。</span><span class="sxs-lookup"><span data-stu-id="c3f13-168">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="c3f13-169">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-169">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="c3f13-170">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-170">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="c3f13-171">使用此处字符串可简化在命令中使用字符串的情况。</span><span class="sxs-lookup"><span data-stu-id="c3f13-171">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="c3f13-172">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-172">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="c3f13-173">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-173">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="c3f13-174">在此处用单引号括起来的字符串中，变量按原义解释和重现。</span><span class="sxs-lookup"><span data-stu-id="c3f13-174">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="c3f13-175">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-175">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="c3f13-176">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-176">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="c3f13-177">在后面加双引号的字符串中，变量被替换为其值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-177">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="c3f13-178">例如：</span><span class="sxs-lookup"><span data-stu-id="c3f13-178">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="c3f13-179">此命令的输出为：</span><span class="sxs-lookup"><span data-stu-id="c3f13-179">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="c3f13-180">此处-通常使用字符串将多个行分配给一个变量。</span><span class="sxs-lookup"><span data-stu-id="c3f13-180">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="c3f13-181">例如，下面的字符串将一个 XML 页分配给 $page 变量。</span><span class="sxs-lookup"><span data-stu-id="c3f13-181">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="c3f13-182">此处-对于向 cmdlet 进行的输入，字符串也是一种方便的格式，这种格式会 `ConvertFrom-StringData` 将字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="c3f13-182">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="c3f13-183">有关详细信息，请参阅 `ConvertFrom-StringData`。</span><span class="sxs-lookup"><span data-stu-id="c3f13-183">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3f13-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3f13-184">See also</span></span>

[<span data-ttu-id="c3f13-185">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="c3f13-185">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="c3f13-186">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="c3f13-186">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
