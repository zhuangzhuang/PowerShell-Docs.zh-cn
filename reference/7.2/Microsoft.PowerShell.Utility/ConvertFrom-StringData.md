---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: c95ebca6307d58668c31faf3e492617f49ddebf4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598882"
---
# <span data-ttu-id="e0f70-102">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="e0f70-102">ConvertFrom-StringData</span></span>

## <span data-ttu-id="e0f70-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e0f70-103">SYNOPSIS</span></span>
<span data-ttu-id="e0f70-104">将包含一个或多个键-值对的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="e0f70-104">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="e0f70-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0f70-105">SYNTAX</span></span>

### <span data-ttu-id="e0f70-106">全部</span><span class="sxs-lookup"><span data-stu-id="e0f70-106">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## <span data-ttu-id="e0f70-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0f70-107">DESCRIPTION</span></span>

<span data-ttu-id="e0f70-108">`ConvertFrom-StringData`Cmdlet 将包含一个或多个键和值对的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="e0f70-108">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="e0f70-109">由于每个键-值对都必须位于单独的行上，因此，通常使用字符串作为输入格式。</span><span class="sxs-lookup"><span data-stu-id="e0f70-109">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="e0f70-110">默认情况下，必须将该 **密钥** 与 **值** 之间用等号分隔 (`=`) 字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-110">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="e0f70-111">该 `ConvertFrom-StringData` cmdlet 被视为可在脚本或函数的部分中使用的安全 cmdlet `DATA` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-111">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="e0f70-112">当在节中使用时 `DATA` ，字符串的内容必须符合数据部分的规则。</span><span class="sxs-lookup"><span data-stu-id="e0f70-112">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="e0f70-113">有关详细信息，请参阅 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f70-113">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="e0f70-114">`ConvertFrom-StringData` 支持传统机器翻译工具允许的转义字符序列。</span><span class="sxs-lookup"><span data-stu-id="e0f70-114">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="e0f70-115">也就是说，该 cmdlet 可以 `\` 使用 [Unescape 方法](/dotnet/api/system.text.regularexpressions.regex.unescape)解释字符串数据中) 转义符 (反斜杠，而不是使用 PowerShell 反撇号字符 (\`) 通常会在脚本中发出行的结尾。</span><span class="sxs-lookup"><span data-stu-id="e0f70-115">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="e0f70-116">在 here-string 中，反撇号字符无效。</span><span class="sxs-lookup"><span data-stu-id="e0f70-116">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="e0f70-117">还可以通过使用前面的反斜杠对其进行转义，使结果保留在结果中，如下所示： `\\` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-117">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="e0f70-118">未转义的反斜杠字符（例如那些通常用在文件路径中的反斜杠字符）可以在结果中呈现为非法的转义序列。</span><span class="sxs-lookup"><span data-stu-id="e0f70-118">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

<span data-ttu-id="e0f70-119">PowerShell 7 添加了 **分隔符** 参数。</span><span class="sxs-lookup"><span data-stu-id="e0f70-119">PowerShell 7 adds the **Delimiter** parameter.</span></span>

## <span data-ttu-id="e0f70-120">示例</span><span class="sxs-lookup"><span data-stu-id="e0f70-120">EXAMPLES</span></span>

### <span data-ttu-id="e0f70-121">示例1：将此处的单引用字符串转换为哈希表</span><span class="sxs-lookup"><span data-stu-id="e0f70-121">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="e0f70-122">此示例将用户消息的单引用字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="e0f70-122">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="e0f70-123">在带单引号的字符串中，不能使用变量和无法计算的表达式来代替其值。</span><span class="sxs-lookup"><span data-stu-id="e0f70-123">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="e0f70-124">`ConvertFrom-StringData`Cmdlet 将变量中的值转换 `$Here` 为哈希表。</span><span class="sxs-lookup"><span data-stu-id="e0f70-124">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="e0f70-125">示例2：使用不同的分隔符转换字符串数据</span><span class="sxs-lookup"><span data-stu-id="e0f70-125">Example 2: Convert string data using a different delimiter</span></span>

<span data-ttu-id="e0f70-126">此示例演示如何转换使用其他字符作为分隔符的字符串数据。</span><span class="sxs-lookup"><span data-stu-id="e0f70-126">This example shows how to convert string data that uses a different character as a delimiter.</span></span> <span data-ttu-id="e0f70-127">在此示例中，字符串数据使用管道字符 (`|`) 作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-127">In this example the string data is using the pipe character (`|`) as the delimiter.</span></span>

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### <span data-ttu-id="e0f70-128">示例3：在此处转换包含注释的字符串</span><span class="sxs-lookup"><span data-stu-id="e0f70-128">Example 3: Convert a here-string containing a comment</span></span>

<span data-ttu-id="e0f70-129">此示例将包含注释和多个键/值对的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="e0f70-129">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="e0f70-130">**Convertfrom-stringdata** 参数的值是一个字符串，而不是包含此字符串的变量。</span><span class="sxs-lookup"><span data-stu-id="e0f70-130">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="e0f70-131">两种格式都有效。</span><span class="sxs-lookup"><span data-stu-id="e0f70-131">Either format is valid.</span></span> <span data-ttu-id="e0f70-132">here-string 包括有关某字符串的注释。</span><span class="sxs-lookup"><span data-stu-id="e0f70-132">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="e0f70-133">`ConvertFrom-StringData` 忽略单行注释，但该 `#` 字符必须是行中的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-133">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="e0f70-134">忽略后行中的所有字符 `#` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-134">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="e0f70-135">示例4：将字符串转换为哈希表</span><span class="sxs-lookup"><span data-stu-id="e0f70-135">Example 4: Convert a string to a hash table</span></span>

<span data-ttu-id="e0f70-136">下面的示例将一个用双引号括起来的规则)  (转换为哈希表，并将其保存在 `$A` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e0f70-136">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="e0f70-137">为了满足每个键/值对必须位于一个单独的行上的条件，该字符串使用 PowerShell 换行符 (\` n) 来分隔配对。</span><span class="sxs-lookup"><span data-stu-id="e0f70-137">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="e0f70-138">示例5：使用脚本的 DATA 节中的 ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="e0f70-138">Example 5: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="e0f70-139">此示例演示 `ConvertFrom-StringData` 脚本的数据部分中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="e0f70-139">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="e0f70-140">DATA 节下面的语句向用户显示该文本。</span><span class="sxs-lookup"><span data-stu-id="e0f70-140">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="e0f70-141">由于文本包括变量名称，所以必须用单引号将它括起来，以便按照字义解释变量，而不是展开它。</span><span class="sxs-lookup"><span data-stu-id="e0f70-141">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="e0f70-142">不允许在 **DATA** 节中使用变量。</span><span class="sxs-lookup"><span data-stu-id="e0f70-142">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="e0f70-143">示例6：使用管道运算符传递字符串</span><span class="sxs-lookup"><span data-stu-id="e0f70-143">Example 6: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="e0f70-144">此示例演示可以使用管道运算符 (`|`) 将字符串发送到 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-144">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="e0f70-145">变量的值将通过 `$Here` 管道传递给 `ConvertFrom-StringData` ，并将结果放入 `$Hash` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e0f70-145">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="e0f70-146">示例7：使用转义字符添加新行和返回字符</span><span class="sxs-lookup"><span data-stu-id="e0f70-146">Example 7: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="e0f70-147">此示例演示如何使用转义字符创建新行并返回源数据中的字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-147">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="e0f70-148">转义序列 `\n` 用于在与生成的哈希表中的名称或项关联的文本块中创建新行。</span><span class="sxs-lookup"><span data-stu-id="e0f70-148">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="e0f70-149">示例8：使用反斜杠转义字符正确呈现文件路径</span><span class="sxs-lookup"><span data-stu-id="e0f70-149">Example 8: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="e0f70-150">此示例演示如何使用字符串数据中的反斜杠转义字符，以允许在生成的哈希表中正确呈现文件路径 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-150">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="e0f70-151">双反斜杠可确保文本反斜杠字符正确呈现在哈希表输出中。</span><span class="sxs-lookup"><span data-stu-id="e0f70-151">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="e0f70-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0f70-152">PARAMETERS</span></span>

### <span data-ttu-id="e0f70-153">-StringData</span><span class="sxs-lookup"><span data-stu-id="e0f70-153">-StringData</span></span>

<span data-ttu-id="e0f70-154">指定要转换的字符串。</span><span class="sxs-lookup"><span data-stu-id="e0f70-154">Specifies the string to be converted.</span></span> <span data-ttu-id="e0f70-155">可以使用此参数或通过管道将字符串传递给 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-155">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="e0f70-156">参数名为可选项。</span><span class="sxs-lookup"><span data-stu-id="e0f70-156">The parameter name is optional.</span></span>

<span data-ttu-id="e0f70-157">此参数的值必须是包含一个或多个键/值对的字符串。</span><span class="sxs-lookup"><span data-stu-id="e0f70-157">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="e0f70-158">每个键/值对必须位于单独的行上，或每个对必须由换行符分隔 (\` n) 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-158">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="e0f70-159">您可以在字符串中包含注释，但是注释不能与键值对在同一行上。</span><span class="sxs-lookup"><span data-stu-id="e0f70-159">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="e0f70-160">`ConvertFrom-StringData` 忽略单行注释。</span><span class="sxs-lookup"><span data-stu-id="e0f70-160">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="e0f70-161">该 `#` 字符必须是行中的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-161">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="e0f70-162">忽略后行中的所有字符 `#` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-162">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="e0f70-163">哈希表中不包括注释。</span><span class="sxs-lookup"><span data-stu-id="e0f70-163">The comments are not included in the hash table.</span></span>

<span data-ttu-id="e0f70-164">这是一个字符串，包含一行或多行。</span><span class="sxs-lookup"><span data-stu-id="e0f70-164">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="e0f70-165">在此处字符串中的引号将按原义解释为字符串数据的一部分。</span><span class="sxs-lookup"><span data-stu-id="e0f70-165">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="e0f70-166">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f70-166">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f70-167">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="e0f70-167">-Delimiter</span></span>

<span data-ttu-id="e0f70-168">用于在要转换的字符串的 **值** 数据中分隔 **键** 的字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-168">The character used to separate the **key** from the **value** data in the string being converted.</span></span>
<span data-ttu-id="e0f70-169">默认分隔符为等于符号 (`=`) 字符。</span><span class="sxs-lookup"><span data-stu-id="e0f70-169">The default delimiter is the equals sign (`=`) character.</span></span> <span data-ttu-id="e0f70-170">此参数是在 PowerShell 7 中添加的。</span><span class="sxs-lookup"><span data-stu-id="e0f70-170">This parameter was added in PowerShell 7.</span></span>

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0f70-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0f70-171">CommonParameters</span></span>

<span data-ttu-id="e0f70-172">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e0f70-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0f70-173">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f70-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e0f70-174">输入</span><span class="sxs-lookup"><span data-stu-id="e0f70-174">INPUTS</span></span>

### <span data-ttu-id="e0f70-175">System.String</span><span class="sxs-lookup"><span data-stu-id="e0f70-175">System.String</span></span>

<span data-ttu-id="e0f70-176">可以通过管道将包含键/值对的字符串传递给 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="e0f70-176">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="e0f70-177">输出</span><span class="sxs-lookup"><span data-stu-id="e0f70-177">OUTPUTS</span></span>

### <span data-ttu-id="e0f70-178">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="e0f70-178">System.Collections.Hashtable</span></span>

<span data-ttu-id="e0f70-179">此 cmdlet 将返回一个哈希表，该哈希表是从键/值对创建的。</span><span class="sxs-lookup"><span data-stu-id="e0f70-179">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="e0f70-180">注释</span><span class="sxs-lookup"><span data-stu-id="e0f70-180">NOTES</span></span>

<span data-ttu-id="e0f70-181">here-string 是由一行或多行组成的字符串，在其中，按照字义解释引号。</span><span class="sxs-lookup"><span data-stu-id="e0f70-181">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="e0f70-182">此 cmdlet 可用于以多种语言显示用户消息的脚本。</span><span class="sxs-lookup"><span data-stu-id="e0f70-182">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="e0f70-183">可使用字典风格的哈希表来从代码中隔离文本字符串（如在资源文件中），并为文本字符串设置格式以便在转换工具中使用。</span><span class="sxs-lookup"><span data-stu-id="e0f70-183">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="e0f70-184">相关链接</span><span class="sxs-lookup"><span data-stu-id="e0f70-184">RELATED LINKS</span></span>

