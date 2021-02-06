---
description: 介绍脚本国际化功能，这些功能使脚本可以轻松地在用户界面中向用户显示消息和说明 (UI) 语言。
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 283ea6788e76b481c912fc5672350efd2e8bafaa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596446"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="0a86a-103">关于脚本国际化</span><span class="sxs-lookup"><span data-stu-id="0a86a-103">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="0a86a-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="0a86a-104">Short Description</span></span>
<span data-ttu-id="0a86a-105">介绍脚本国际化功能，这些功能使脚本可以轻松地在用户界面中向用户显示消息和说明 (UI) 语言。</span><span class="sxs-lookup"><span data-stu-id="0a86a-105">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a86a-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="0a86a-106">Long Description</span></span>

<span data-ttu-id="0a86a-107">使用 PowerShell 脚本国际化功能，您可以通过以用户的语言显示帮助和用户消息来更好地为世界各地的用户提供服务。</span><span class="sxs-lookup"><span data-stu-id="0a86a-107">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="0a86a-108">脚本国际化功能在执行过程中查询操作系统的 UI 区域性，导入适当的翻译文本字符串，并将其显示给用户。</span><span class="sxs-lookup"><span data-stu-id="0a86a-108">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="0a86a-109">Data 节使你可以存储与代码分开的文本字符串，以便能够轻松地识别和提取它们。</span><span class="sxs-lookup"><span data-stu-id="0a86a-109">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="0a86a-110">新的 cmdlet `ConvertFrom-StringData` 将文本字符串转换为类似字典的哈希表，以方便转换。</span><span class="sxs-lookup"><span data-stu-id="0a86a-110">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="0a86a-111">为支持国际帮助文本，PowerShell 包含以下功能：</span><span class="sxs-lookup"><span data-stu-id="0a86a-111">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="0a86a-112">用于分隔文本字符串与代码说明的数据部分。</span><span class="sxs-lookup"><span data-stu-id="0a86a-112">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="0a86a-113">有关 Data 部分的详细信息，请参阅 [about_Data_Sections](about_Data_Sections.md)。</span><span class="sxs-lookup"><span data-stu-id="0a86a-113">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="0a86a-114">新的自动变量、 `$PSCulture` 和 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="0a86a-114">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="0a86a-115">`$PSCulture` 将系统上使用的 UI 语言的名称存储到元素，例如日期、时间和货币。</span><span class="sxs-lookup"><span data-stu-id="0a86a-115">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="0a86a-116">`$PSUICulture`变量存储用于用户界面元素（如菜单和文本字符串）的系统 UI 语言的名称。</span><span class="sxs-lookup"><span data-stu-id="0a86a-116">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="0a86a-117">Cmdlet， `ConvertFrom-StringData` 它将文本字符串转换为类似字典的哈希表以便于翻译。</span><span class="sxs-lookup"><span data-stu-id="0a86a-117">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="0a86a-118">有关详细信息，请参阅 [convertfrom-csv-convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)。</span><span class="sxs-lookup"><span data-stu-id="0a86a-118">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="0a86a-119">新的文件类型， `.psd1` 用于存储已翻译的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="0a86a-119">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="0a86a-120">`.psd1`文件存储在脚本目录的特定于语言的子目录中。</span><span class="sxs-lookup"><span data-stu-id="0a86a-120">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="0a86a-121">Cmdlet， `Import-LocalizedData` 它在运行时将指定语言的已翻译文本字符串导入脚本。</span><span class="sxs-lookup"><span data-stu-id="0a86a-121">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="0a86a-122">此 cmdlet 识别并导入任意 Windows 支持的语言的字符串。</span><span class="sxs-lookup"><span data-stu-id="0a86a-122">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="0a86a-123">有关详细信息，请参阅 [import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)。</span><span class="sxs-lookup"><span data-stu-id="0a86a-123">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="0a86a-124">Data 部分：存储默认字符串</span><span class="sxs-lookup"><span data-stu-id="0a86a-124">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="0a86a-125">使用脚本中的数据部分以默认语言存储文本字符串。</span><span class="sxs-lookup"><span data-stu-id="0a86a-125">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="0a86a-126">在此处字符串中的键/值对中排列字符串。</span><span class="sxs-lookup"><span data-stu-id="0a86a-126">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="0a86a-127">每个键/值对必须位于单独的行上。</span><span class="sxs-lookup"><span data-stu-id="0a86a-127">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="0a86a-128">如果包含注释，则注释必须位于单独的行上。</span><span class="sxs-lookup"><span data-stu-id="0a86a-128">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="0a86a-129">该 `ConvertFrom-StringData` cmdlet 将在此处字符串中的键/值对转换为类似字典的哈希表，该哈希表存储在 Data 节变量的值中。</span><span class="sxs-lookup"><span data-stu-id="0a86a-129">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="0a86a-130">在下面的示例中，脚本的数据部分 `World.ps1` 包含 English-United 状态 (en-us) 脚本的提示消息集。</span><span class="sxs-lookup"><span data-stu-id="0a86a-130">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="0a86a-131">`ConvertFrom-StringData`Cmdlet 将字符串转换为哈希表，并将其存储在 `$msgtable` 变量中。</span><span class="sxs-lookup"><span data-stu-id="0a86a-131">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="0a86a-132">有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="0a86a-132">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="0a86a-133">PSD1 文件：存储已转换的字符串</span><span class="sxs-lookup"><span data-stu-id="0a86a-133">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="0a86a-134">将每个 UI 语言的脚本消息保存在单独的文本文件中，并将其名称与脚本和 `.psd1` 文件扩展名相同。</span><span class="sxs-lookup"><span data-stu-id="0a86a-134">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="0a86a-135">将文件存储在具有以下格式的区域性名称的脚本目录子目录中：</span><span class="sxs-lookup"><span data-stu-id="0a86a-135">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="0a86a-136">示例： de DE、ar-SA 和 zh-chs-Hans</span><span class="sxs-lookup"><span data-stu-id="0a86a-136">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="0a86a-137">例如，如果该 `World.ps1` 脚本存储在 `C:\Scripts` 目录中，则会创建类似于以下内容的文件目录结构：</span><span class="sxs-lookup"><span data-stu-id="0a86a-137">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="0a86a-138">`World.psd1`脚本目录的 de 子目录中的文件可能包含以下语句：</span><span class="sxs-lookup"><span data-stu-id="0a86a-138">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="0a86a-139">同样， `World.psd1` 脚本目录的 ar-SA 子目录中的文件可能包含以下语句：</span><span class="sxs-lookup"><span data-stu-id="0a86a-139">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="0a86a-140">Import-localizeddata：动态检索转换字符串</span><span class="sxs-lookup"><span data-stu-id="0a86a-140">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="0a86a-141">若要检索当前用户的 UI 语言的字符串，请使用 `Import-LocalizedData` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0a86a-141">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="0a86a-142">`Import-LocalizedData` 查找自动变量的值 `$PSUICulture` ，并导入 `<script-name>.psd1` 子目录中与该值匹配的文件的内容 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="0a86a-142">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="0a86a-143">然后，它将导入的内容保存在由 **BindingVariable** 参数的值所指定的变量中。</span><span class="sxs-lookup"><span data-stu-id="0a86a-143">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="0a86a-144">例如，如果 `Import-LocalizedData` 命令出现在 `C:\Scripts\World.ps1` 脚本中并且的值 `$PSUICulture` 为 "ar-SA"，则 `Import-LocalizedData` 查找以下文件：</span><span class="sxs-lookup"><span data-stu-id="0a86a-144">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="0a86a-145">然后，它会将阿拉伯语文本字符串从文件导入到 `$msgTable` 变量，替换可能在脚本的 Data 节中定义的任何默认字符串 `World.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="0a86a-145">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="0a86a-146">因此，当脚本使用 `$msgTable` 变量显示用户消息时，消息将显示为阿拉伯语。</span><span class="sxs-lookup"><span data-stu-id="0a86a-146">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="0a86a-147">例如，以下脚本将显示阿拉伯语中的 "请输入您的用户名" 消息：</span><span class="sxs-lookup"><span data-stu-id="0a86a-147">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="0a86a-148">如果 `Import-LocalizedData` 找不到 `.psd1` 与的值匹配的文件 `$PSUIculture` ， `$msgTable` 则不会替换的值，并且调用将 `$msgTable.promptMsg` 显示回退 en-us 字符串。</span><span class="sxs-lookup"><span data-stu-id="0a86a-148">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="0a86a-149">示例</span><span class="sxs-lookup"><span data-stu-id="0a86a-149">Examples</span></span>

<span data-ttu-id="0a86a-150">此示例演示如何在脚本中使用脚本国际化功能，以将一周中的某一天显示给在计算机上设置的语言的用户。</span><span class="sxs-lookup"><span data-stu-id="0a86a-150">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="0a86a-151">下面是 Sample1.ps1 脚本文件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="0a86a-151">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="0a86a-152">该脚本以名为 Day ($Day 包含命令的) 数据部分开始 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="0a86a-152">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="0a86a-153">提交到的表达式 `ConvertFrom-StringData` 是一个字符串，其中包含默认 UI 区域性中的天名称（在键/值对中）。</span><span class="sxs-lookup"><span data-stu-id="0a86a-153">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="0a86a-154">`ConvertFrom-StringData`Cmdlet 将此处字符串中的键/值对转换为哈希表，然后将其保存在变量的值中 `$Day` 。</span><span class="sxs-lookup"><span data-stu-id="0a86a-154">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="0a86a-155">`Import-LocalizedData`命令将导入 `.psd1` 目录中与自动变量的值匹配的文件内容， `$PSUICulture` 然后将其保存在变量中，并 `$Day` 替换 `$Day` Data 节中定义的值。</span><span class="sxs-lookup"><span data-stu-id="0a86a-155">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="0a86a-156">其余的命令将字符串加载到数组中并显示它们。</span><span class="sxs-lookup"><span data-stu-id="0a86a-156">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="0a86a-157">`.psd1`支持脚本的文件保存在脚本目录的子目录中，名称与 `$PSUICulture` 值匹配。</span><span class="sxs-lookup"><span data-stu-id="0a86a-157">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="0a86a-158">下面是完整的列表 `.\de-DE\sample1.psd1` ：</span><span class="sxs-lookup"><span data-stu-id="0a86a-158">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="0a86a-159">因此，当您在值为的系统上运行 Sample.ps1 时 `$PSUICulture` ，脚本的输出为：</span><span class="sxs-lookup"><span data-stu-id="0a86a-159">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="0a86a-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a86a-160">See also</span></span>

- [<span data-ttu-id="0a86a-161">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="0a86a-161">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="0a86a-162">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0a86a-162">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="0a86a-163">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="0a86a-163">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="0a86a-164">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="0a86a-164">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="0a86a-165">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="0a86a-165">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="0a86a-166">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="0a86a-166">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

