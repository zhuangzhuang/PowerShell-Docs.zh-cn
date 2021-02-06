---
description: 描述 PowerShell 如何分析命令。
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597077"
---
# <a name="about-parsing"></a><span data-ttu-id="2aca2-103">关于分析</span><span class="sxs-lookup"><span data-stu-id="2aca2-103">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="2aca2-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="2aca2-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2aca2-105">描述 PowerShell 如何分析命令。</span><span class="sxs-lookup"><span data-stu-id="2aca2-105">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="2aca2-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="2aca2-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2aca2-107">当你在命令提示符下输入命令时，PowerShell 会将命令文本分为一系列称为 _令牌_ 的段，然后确定如何解释每个标记。</span><span class="sxs-lookup"><span data-stu-id="2aca2-107">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="2aca2-108">例如，如果键入：</span><span class="sxs-lookup"><span data-stu-id="2aca2-108">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="2aca2-109">PowerShell 将命令分成两个令牌 `Write-Host` ：和 `book` ，并使用两种主要分析模式之一（表达式模式和参数模式）单独解释每个标记。</span><span class="sxs-lookup"><span data-stu-id="2aca2-109">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="2aca2-110">PowerShell 分析命令输入会尝试将命令名称解析为 cmdlet 或本机可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2aca2-110">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="2aca2-111">如果命令名称没有完全匹配项，则 PowerShell 会将 `Get-` 命令作为默认谓词前面预置到该命令。</span><span class="sxs-lookup"><span data-stu-id="2aca2-111">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="2aca2-112">例如，PowerShell 分析 `Process` 为 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="2aca2-112">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="2aca2-113">不建议使用此功能，原因如下：</span><span class="sxs-lookup"><span data-stu-id="2aca2-113">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="2aca2-114">这是低效的。</span><span class="sxs-lookup"><span data-stu-id="2aca2-114">It's inefficient.</span></span> <span data-ttu-id="2aca2-115">这会导致 PowerShell 多次搜索。</span><span class="sxs-lookup"><span data-stu-id="2aca2-115">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="2aca2-116">首先解析同名的外部程序，因此不能执行所需的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2aca2-116">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="2aca2-117">`Get-Help` 并且 `Get-Command` 不要识别不带谓词的名称。</span><span class="sxs-lookup"><span data-stu-id="2aca2-117">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="2aca2-118">表达式模式</span><span class="sxs-lookup"><span data-stu-id="2aca2-118">Expression mode</span></span>

<span data-ttu-id="2aca2-119">表达式模式适用于组合表达式，这是脚本语言中的值操作所必需的。</span><span class="sxs-lookup"><span data-stu-id="2aca2-119">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="2aca2-120">表达式是 PowerShell 语法中值的表示形式，可以是简单或复合，例如：</span><span class="sxs-lookup"><span data-stu-id="2aca2-120">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="2aca2-121">文本表达式是其值的直接表示形式：</span><span class="sxs-lookup"><span data-stu-id="2aca2-121">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="2aca2-122">变量表达式携带它们引用的变量的值：</span><span class="sxs-lookup"><span data-stu-id="2aca2-122">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="2aca2-123">运算符将其他表达式组合在一起以进行计算：</span><span class="sxs-lookup"><span data-stu-id="2aca2-123">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="2aca2-124">_字符串文本_ 必须包含在引号中。</span><span class="sxs-lookup"><span data-stu-id="2aca2-124">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="2aca2-125">_数字_ 被视为数值，而不是作为一系列字符，除非转义)  (。</span><span class="sxs-lookup"><span data-stu-id="2aca2-125">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="2aca2-126">_运算符_（包括和等一元运算符） `-` `-not` `+` `-gt` 被解释为运算符，并将其各自的操作应用于它们的参数 (操作数) 。</span><span class="sxs-lookup"><span data-stu-id="2aca2-126">_Operators_, including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="2aca2-127">_特性和转换表达式_ 被分析为表达式并应用于从属表达式， `[int] '7'` 例如。</span><span class="sxs-lookup"><span data-stu-id="2aca2-127">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="2aca2-128">_变量引用_ 被计算为它们的值，但 _展开_ (也就是说，将预填充的参数集粘贴) 将被禁止，并导致分析器错误。</span><span class="sxs-lookup"><span data-stu-id="2aca2-128">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="2aca2-129">其他任何内容都将被视为要调用的命令。</span><span class="sxs-lookup"><span data-stu-id="2aca2-129">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="2aca2-130">参数模式</span><span class="sxs-lookup"><span data-stu-id="2aca2-130">Argument mode</span></span>

<span data-ttu-id="2aca2-131">在分析时，PowerShell 首先会将输入解释为表达式。</span><span class="sxs-lookup"><span data-stu-id="2aca2-131">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="2aca2-132">但当遇到命令调用时，分析将在参数模式下继续。</span><span class="sxs-lookup"><span data-stu-id="2aca2-132">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="2aca2-133">自变量模式旨在分析 shell 环境中命令的参数和参数。</span><span class="sxs-lookup"><span data-stu-id="2aca2-133">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="2aca2-134">所有输入都被视为可扩充字符串，除非它使用以下语法之一：</span><span class="sxs-lookup"><span data-stu-id="2aca2-134">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="2aca2-135">美元符号 (`$`) 仅在其后跟有效的变量名称时才开始使用变量引用 (; 否则，它将被解释为可扩充字符串) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="2aca2-135">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="2aca2-136">引号 (`'` 和 `"`) 开始字符串值</span><span class="sxs-lookup"><span data-stu-id="2aca2-136">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="2aca2-137">圆括号 (`(` 和 `)`) 为新表达式划分界限。</span><span class="sxs-lookup"><span data-stu-id="2aca2-137">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="2aca2-138">子表达式运算符 (`$(` `)`) 划分嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="2aca2-138">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="2aca2-139">大括号 (`{` 和 `}`) 为新脚本块划分界限。</span><span class="sxs-lookup"><span data-stu-id="2aca2-139">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="2aca2-140">初始 at 符号 (`@`) 开始表达式语法，如展开 (`@args`) ，数组 () `@(1,2,3)` 和哈希表 (`@{a=1;b=2}`) 。</span><span class="sxs-lookup"><span data-stu-id="2aca2-140">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="2aca2-141">逗号 (`,`) 引入作为数组传递的列表，但要调用的命令是本机应用程序，在这种情况下，它们将被解释为可扩充字符串的一部分。</span><span class="sxs-lookup"><span data-stu-id="2aca2-141">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="2aca2-142">不支持初始、连续或尾随逗号。</span><span class="sxs-lookup"><span data-stu-id="2aca2-142">Initial, consecutive or trailing commas are not supported.</span></span>

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="2aca2-143">嵌入式表达式的值将转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="2aca2-143">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="2aca2-144">下表提供了在表达式模式和参数模式下处理的值的几个示例以及这些值的计算结果。</span><span class="sxs-lookup"><span data-stu-id="2aca2-144">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="2aca2-145">假设变量的值 `a` 为 `4` 。</span><span class="sxs-lookup"><span data-stu-id="2aca2-145">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="2aca2-146">示例</span><span class="sxs-lookup"><span data-stu-id="2aca2-146">Example</span></span>        |    <span data-ttu-id="2aca2-147">模型</span><span class="sxs-lookup"><span data-stu-id="2aca2-147">Mode</span></span>    |      <span data-ttu-id="2aca2-148">结果</span><span class="sxs-lookup"><span data-stu-id="2aca2-148">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="2aca2-149">表达式</span><span class="sxs-lookup"><span data-stu-id="2aca2-149">Expression</span></span> | <span data-ttu-id="2aca2-150">2 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-150">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="2aca2-151">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-151">Expression</span></span> | <span data-ttu-id="2aca2-152">"2" (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-152">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="2aca2-153">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-153">Expression</span></span> | <span data-ttu-id="2aca2-154">2 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-154">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="2aca2-155">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-155">Expression</span></span> | <span data-ttu-id="2aca2-156">4 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-156">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="2aca2-157">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-157">Argument</span></span>   | <span data-ttu-id="2aca2-158">"2 + 2" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-158">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="2aca2-159">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-159">Expression</span></span> | <span data-ttu-id="2aca2-160">4 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-160">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="2aca2-161">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-161">Expression</span></span> | <span data-ttu-id="2aca2-162">4 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-162">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="2aca2-163">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-163">Expression</span></span> | <span data-ttu-id="2aca2-164">4 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-164">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="2aca2-165">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-165">Expression</span></span> | <span data-ttu-id="2aca2-166">6 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-166">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="2aca2-167">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-167">Argument</span></span>   | <span data-ttu-id="2aca2-168">4 + 2 (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-168">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="2aca2-169">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-169">Argument</span></span>   | <span data-ttu-id="2aca2-170">"$-" (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-170">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="2aca2-171">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-171">Argument</span></span>   | <span data-ttu-id="2aca2-172">"$-" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-172">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="2aca2-173">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-173">Expression</span></span> | <span data-ttu-id="2aca2-174">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-174">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="2aca2-175">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-175">Argument</span></span>   | <span data-ttu-id="2aca2-176">"a4" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-176">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="2aca2-177">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-177">Expression</span></span> | <span data-ttu-id="2aca2-178">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-178">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="2aca2-179">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-179">Argument</span></span>   | <span data-ttu-id="2aca2-180">"a $ a" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-180">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="2aca2-181">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-181">Expression</span></span> | <span data-ttu-id="2aca2-182">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-182">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="2aca2-183">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-183">Argument</span></span>   | <span data-ttu-id="2aca2-184">"a4" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-184">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="2aca2-185">Expression</span><span class="sxs-lookup"><span data-stu-id="2aca2-185">Expression</span></span> | <span data-ttu-id="2aca2-186">"a $ (2) " (命令) </span><span class="sxs-lookup"><span data-stu-id="2aca2-186">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="2aca2-187">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-187">Argument</span></span>   | <span data-ttu-id="2aca2-188">"a2" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-188">"a2" (string)</span></span>     |

<span data-ttu-id="2aca2-189">每个令牌都可解释为某种类型的对象类型，例如布尔型或 string 类型。</span><span class="sxs-lookup"><span data-stu-id="2aca2-189">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="2aca2-190">PowerShell 尝试从表达式中确定对象类型。</span><span class="sxs-lookup"><span data-stu-id="2aca2-190">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="2aca2-191">对象类型取决于命令所需的参数类型，以及 PowerShell 是否知道如何将参数转换为正确的类型。</span><span class="sxs-lookup"><span data-stu-id="2aca2-191">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="2aca2-192">下表显示了分配给表达式返回的值的类型的几个示例。</span><span class="sxs-lookup"><span data-stu-id="2aca2-192">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="2aca2-193">示例</span><span class="sxs-lookup"><span data-stu-id="2aca2-193">Example</span></span>          |    <span data-ttu-id="2aca2-194">模型</span><span class="sxs-lookup"><span data-stu-id="2aca2-194">Mode</span></span>    |     <span data-ttu-id="2aca2-195">结果</span><span class="sxs-lookup"><span data-stu-id="2aca2-195">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="2aca2-196">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-196">argument</span></span>   | <span data-ttu-id="2aca2-197">"！ 1" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-197">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="2aca2-198">表达式</span><span class="sxs-lookup"><span data-stu-id="2aca2-198">expression</span></span> | <span data-ttu-id="2aca2-199">False (布尔) </span><span class="sxs-lookup"><span data-stu-id="2aca2-199">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="2aca2-200">表达式</span><span class="sxs-lookup"><span data-stu-id="2aca2-200">expression</span></span> | <span data-ttu-id="2aca2-201">2 (整数) </span><span class="sxs-lookup"><span data-stu-id="2aca2-201">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="2aca2-202">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-202">argument</span></span>   | <span data-ttu-id="2aca2-203"> (数组的 "A"、"B") </span><span class="sxs-lookup"><span data-stu-id="2aca2-203">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="2aca2-204">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-204">argument</span></span>   | <span data-ttu-id="2aca2-205">"A，B" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-205">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="2aca2-206">表达式</span><span class="sxs-lookup"><span data-stu-id="2aca2-206">expression</span></span> | <span data-ttu-id="2aca2-207"> (数组的 "A"、"B") </span><span class="sxs-lookup"><span data-stu-id="2aca2-207">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="2aca2-208">参数</span><span class="sxs-lookup"><span data-stu-id="2aca2-208">argument</span></span>   | <span data-ttu-id="2aca2-209">"： A B" (字符串) </span><span class="sxs-lookup"><span data-stu-id="2aca2-209">':A B' (string)</span></span> |

<span data-ttu-id="2aca2-210">PowerShell 3.0 中引入的 "停止分析" 符号 (`--%`) ，定向 PowerShell 避免将输入解释为 powershell 命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="2aca2-210">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="2aca2-211">在 PowerShell 中调用可执行程序时，将停止解析符号置于程序参数之前。</span><span class="sxs-lookup"><span data-stu-id="2aca2-211">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="2aca2-212">此方法比使用转义符来防止解释误解要容易得多。</span><span class="sxs-lookup"><span data-stu-id="2aca2-212">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="2aca2-213">遇到停止分析符号时，PowerShell 会将行中的剩余字符视为文本。</span><span class="sxs-lookup"><span data-stu-id="2aca2-213">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="2aca2-214">它所执行的唯一解释是使用标准的 Windows 表示法（如）来替换环境变量的值 `%USERPROFILE%` 。</span><span class="sxs-lookup"><span data-stu-id="2aca2-214">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="2aca2-215">停止分析符号仅在下一个换行符或管道字符之前有效。</span><span class="sxs-lookup"><span data-stu-id="2aca2-215">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="2aca2-216">不能使用继续符 (`` ` ``) 来扩展其效果，或使用命令分隔符 (`;`) 终止其效果。</span><span class="sxs-lookup"><span data-stu-id="2aca2-216">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="2aca2-217">例如，以下命令将调用 **Icacls** 程序。</span><span class="sxs-lookup"><span data-stu-id="2aca2-217">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="2aca2-218">若要在 PowerShell 2.0 中运行此命令，必须使用转义符来阻止 PowerShell 错误解释圆括号。</span><span class="sxs-lookup"><span data-stu-id="2aca2-218">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="2aca2-219">从 PowerShell 3.0 开始，可以使用停止分析符号。</span><span class="sxs-lookup"><span data-stu-id="2aca2-219">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="2aca2-220">PowerShell 会将以下命令字符串发送到 **Icacls** 程序：</span><span class="sxs-lookup"><span data-stu-id="2aca2-220">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="2aca2-221">停止分析符号仅适用于在 Windows 平台上使用。</span><span class="sxs-lookup"><span data-stu-id="2aca2-221">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="2aca2-222">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2aca2-222">SEE ALSO</span></span>

[<span data-ttu-id="2aca2-223">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="2aca2-223">about_Command_Syntax</span></span>](about_Command_Syntax.md)
