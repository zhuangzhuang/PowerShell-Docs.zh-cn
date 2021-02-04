---
description: 介绍数据部分，这些区域将文本字符串和其他只读数据与脚本逻辑隔离开来。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: bf86d8aeec1094205ace1a64fdf584f5be000313
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879212"
---
# <a name="about-data-sections"></a><span data-ttu-id="8da41-104">关于数据部分</span><span class="sxs-lookup"><span data-stu-id="8da41-104">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="8da41-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="8da41-105">Short Description</span></span>
<span data-ttu-id="8da41-106">介绍数据部分，这些区域将文本字符串和其他只读数据与脚本逻辑隔离开来。</span><span class="sxs-lookup"><span data-stu-id="8da41-106">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="8da41-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="8da41-107">Long Description</span></span>

<span data-ttu-id="8da41-108">为 PowerShell 设计的脚本可以包含一个或多个只包含数据的数据节。</span><span class="sxs-lookup"><span data-stu-id="8da41-108">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="8da41-109">可以在任何脚本、函数或高级函数中包含一个或多个数据节。</span><span class="sxs-lookup"><span data-stu-id="8da41-109">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="8da41-110">Data 部分的内容仅限于 PowerShell 脚本语言的指定子集。</span><span class="sxs-lookup"><span data-stu-id="8da41-110">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="8da41-111">通过将数据与代码逻辑分离，可以更轻松地标识和管理逻辑和数据。</span><span class="sxs-lookup"><span data-stu-id="8da41-111">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="8da41-112">它允许您为文本提供单独的字符串资源文件，例如错误消息和帮助字符串。</span><span class="sxs-lookup"><span data-stu-id="8da41-112">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="8da41-113">它还隔离了代码逻辑，从而促进了安全性和验证测试。</span><span class="sxs-lookup"><span data-stu-id="8da41-113">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="8da41-114">在 PowerShell 中，Data 部分用于支持脚本国际化。</span><span class="sxs-lookup"><span data-stu-id="8da41-114">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="8da41-115">您可以使用数据部分来更轻松地隔离、查找和处理转换为多个用户界面 (UI) 语言的字符串。</span><span class="sxs-lookup"><span data-stu-id="8da41-115">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="8da41-116">Data 部分是一项 PowerShell 2.0 功能。</span><span class="sxs-lookup"><span data-stu-id="8da41-116">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="8da41-117">如果脚本中包含数据节，则不会在没有修订版的 PowerShell 1.0 中运行。</span><span class="sxs-lookup"><span data-stu-id="8da41-117">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="8da41-118">语法</span><span class="sxs-lookup"><span data-stu-id="8da41-118">Syntax</span></span>

<span data-ttu-id="8da41-119">数据部分的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8da41-119">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="8da41-120">Data 关键字是必需的。</span><span class="sxs-lookup"><span data-stu-id="8da41-120">The Data keyword is required.</span></span> <span data-ttu-id="8da41-121">此名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="8da41-121">It is not case-sensitive.</span></span> <span data-ttu-id="8da41-122">允许的内容仅限于以下元素：</span><span class="sxs-lookup"><span data-stu-id="8da41-122">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="8da41-123">所有 PowerShell 操作员，除外 `-match`</span><span class="sxs-lookup"><span data-stu-id="8da41-123">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="8da41-124">`If`、 `Else` 和 `ElseIf` 语句</span><span class="sxs-lookup"><span data-stu-id="8da41-124">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="8da41-125">以下自动变量： `$PsCulture` 、 `$PsUICulture` 、 `$True` 、 `$False` 和 `$Null`</span><span class="sxs-lookup"><span data-stu-id="8da41-125">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="8da41-126">注释</span><span class="sxs-lookup"><span data-stu-id="8da41-126">Comments</span></span>
- <span data-ttu-id="8da41-127">管道</span><span class="sxs-lookup"><span data-stu-id="8da41-127">Pipelines</span></span>
- <span data-ttu-id="8da41-128">用分号分隔的语句 (`;`) </span><span class="sxs-lookup"><span data-stu-id="8da41-128">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="8da41-129">文本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8da41-129">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="8da41-130">数据部分中允许的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8da41-130">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="8da41-131">默认情况下，只 `ConvertFrom-StringData` 允许使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8da41-131">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="8da41-132">使用参数在数据部分中允许的 cmdlet `-SupportedCommand` 。</span><span class="sxs-lookup"><span data-stu-id="8da41-132">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="8da41-133">当你在 `ConvertFrom-StringData` Data 节中使用 cmdlet 时，可以将键/值对括在单个带引号的字符串或带双引号的字符串中，或者用单引号或双引号括起来。</span><span class="sxs-lookup"><span data-stu-id="8da41-133">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="8da41-134">但是，包含变量和子表达式的字符串必须用单引号括起来，或用单引号字符串括起来，这样就不会扩展变量，并且子表达式不能执行。</span><span class="sxs-lookup"><span data-stu-id="8da41-134">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="8da41-135">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="8da41-135">-SupportedCommand</span></span>

<span data-ttu-id="8da41-136">`-SupportedCommand`参数用于指示 cmdlet 或函数仅生成数据。</span><span class="sxs-lookup"><span data-stu-id="8da41-136">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="8da41-137">它旨在允许用户在编写或测试的数据部分中包含 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="8da41-137">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="8da41-138">的值 `-SupportedCommand` 是一个或多个 cmdlet 或函数名的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="8da41-138">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="8da41-139">例如，以下 data 节包含用户编写的 cmdlet， `Format-Xml` 用于设置 XML 文件中的数据的格式：</span><span class="sxs-lookup"><span data-stu-id="8da41-139">For example, the following data section includes a user-written cmdlet, `Format-Xml`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="8da41-140">使用数据部分</span><span class="sxs-lookup"><span data-stu-id="8da41-140">Using a Data Section</span></span>

<span data-ttu-id="8da41-141">若要使用 Data 节的内容，请将其分配给变量并使用变量表示法来访问内容。</span><span class="sxs-lookup"><span data-stu-id="8da41-141">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="8da41-142">例如，以下 data 节包含一个 `ConvertFrom-StringData` 命令，该命令将此处的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="8da41-142">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="8da41-143">将哈希表分配给该 `$TextMsgs` 变量。</span><span class="sxs-lookup"><span data-stu-id="8da41-143">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="8da41-144">`$TextMsgs`变量不是 data 节的一部分。</span><span class="sxs-lookup"><span data-stu-id="8da41-144">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="8da41-145">若要在中访问哈希表中的键和值 `$TextMsgs` ，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="8da41-145">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="8da41-146">或者，您可以将变量名称放在数据节的定义中。</span><span class="sxs-lookup"><span data-stu-id="8da41-146">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="8da41-147">例如：</span><span class="sxs-lookup"><span data-stu-id="8da41-147">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="8da41-148">结果与前面的示例相同。</span><span class="sxs-lookup"><span data-stu-id="8da41-148">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="8da41-149">示例</span><span class="sxs-lookup"><span data-stu-id="8da41-149">Examples</span></span>

<span data-ttu-id="8da41-150">简单的数据字符串。</span><span class="sxs-lookup"><span data-stu-id="8da41-150">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="8da41-151">包含允许的变量的字符串。</span><span class="sxs-lookup"><span data-stu-id="8da41-151">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="8da41-152">使用 cmdlet 的单引用字符串 `ConvertFrom-StringData` ：</span><span class="sxs-lookup"><span data-stu-id="8da41-152">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="8da41-153">使用 cmdlet 的一个用双引号引起来的字符串 `ConvertFrom-StringData` ：</span><span class="sxs-lookup"><span data-stu-id="8da41-153">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="8da41-154">一个数据部分，其中包含生成数据的用户编写的 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="8da41-154">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="8da41-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8da41-155">See Also</span></span>

[<span data-ttu-id="8da41-156">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="8da41-156">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="8da41-157">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="8da41-157">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="8da41-158">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="8da41-158">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="8da41-159">about_If</span><span class="sxs-lookup"><span data-stu-id="8da41-159">about_If</span></span>](about_If.md)

[<span data-ttu-id="8da41-160">about_Operators</span><span class="sxs-lookup"><span data-stu-id="8da41-160">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="8da41-161">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="8da41-161">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="8da41-162">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="8da41-162">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="8da41-163">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="8da41-163">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="8da41-164">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="8da41-164">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

