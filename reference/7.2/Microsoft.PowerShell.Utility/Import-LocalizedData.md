---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: fa5de857b70ec05d30c42fbf8e51a9411d823018
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597865"
---
# <span data-ttu-id="5117d-102">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="5117d-102">Import-LocalizedData</span></span>

## <span data-ttu-id="5117d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5117d-103">SYNOPSIS</span></span>
<span data-ttu-id="5117d-104">基于针对操作系统所选择的 UI 区域性，将特定于语言的数据导入脚本和函数。</span><span class="sxs-lookup"><span data-stu-id="5117d-104">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="5117d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5117d-105">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5117d-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5117d-106">DESCRIPTION</span></span>

<span data-ttu-id="5117d-107">该 `Import-LocalizedData` cmdlet 会动态地从其名称与为操作系统的当前用户设置的 UI 语言的子目录中检索字符串。</span><span class="sxs-lookup"><span data-stu-id="5117d-107">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="5117d-108">它专门用于使脚本可以使用当前用户选择的 UI 语言来显示用户消息。</span><span class="sxs-lookup"><span data-stu-id="5117d-108">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="5117d-109">`Import-LocalizedData` 从 `.psd1` 脚本目录的特定于语言的子目录中的文件导入数据，并将其保存在命令中指定的本地变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-109">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="5117d-110">该 cmdlet 根据自动变量的值选择子目录和文件 `$PSUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-110">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="5117d-111">当你使用脚本中的局部变量显示用户消息时，将以用户的 UI 语言显示该消息。</span><span class="sxs-lookup"><span data-stu-id="5117d-111">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="5117d-112">您可以使用的参数 `Import-LocalizedData` 来指定替换的 UI 区域性、路径和文件名，以添加受支持的命令，以及禁止在找不到文件时显示的错误消息 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-112">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="5117d-113">`Import-LocalizedData`Cmdlet 支持 Windows PowerShell 2.0 中引入的脚本国际化计划。</span><span class="sxs-lookup"><span data-stu-id="5117d-113">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="5117d-114">此计划旨在通过使脚本更易于使用当前用户的 UI 语言显示用户消息，来为全球用户提供更好的服务。</span><span class="sxs-lookup"><span data-stu-id="5117d-114">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="5117d-115">有关此文件和文件格式的详细信息 `.psd1` ，请参阅 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="5117d-115">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="5117d-116">示例</span><span class="sxs-lookup"><span data-stu-id="5117d-116">EXAMPLES</span></span>

### <span data-ttu-id="5117d-117">示例 1：导入文本字符串</span><span class="sxs-lookup"><span data-stu-id="5117d-117">Example 1: Import text strings</span></span>

<span data-ttu-id="5117d-118">此示例将文本字符串导入到 `$Messages` 变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-118">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="5117d-119">它使用其他所有 cmdlet 参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="5117d-119">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="5117d-120">如果该命令包含在目录中的 Archives.ps1 脚本中 `C:\Test` ，并且 `$PsUICulture` 自动变量的值为 ZH-CHS-CN，则会将 `Import-LocalizedData` `Archives.psd1` 该目录中的文件导入 `C:\test\zh-CN` 到 `$Messages` 变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-120">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="5117d-121">示例 2：导入本地化数据字符串</span><span class="sxs-lookup"><span data-stu-id="5117d-121">Example 2: Import localized data strings</span></span>

<span data-ttu-id="5117d-122">此示例在命令行中运行，而不是在脚本中运行。</span><span class="sxs-lookup"><span data-stu-id="5117d-122">This example is run at the command line not in a script.</span></span> <span data-ttu-id="5117d-123">它从 Test.psd1 文件中获取本地化的数据字符串，并将它们显示在命令行中。</span><span class="sxs-lookup"><span data-stu-id="5117d-123">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="5117d-124">由于未在脚本中使用该命令，因此 **FileName** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="5117d-124">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="5117d-125">该命令使用 UICuture 参数指定 en-US 区域性。</span><span class="sxs-lookup"><span data-stu-id="5117d-125">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="5117d-126">`Import-LocalizedData` 返回一个包含本地化的数据字符串的哈希表。</span><span class="sxs-lookup"><span data-stu-id="5117d-126">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="5117d-127">示例 3：导入 UI 区域性字符串</span><span class="sxs-lookup"><span data-stu-id="5117d-127">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="5117d-128">此命令将文本字符串导入 `$MsgTbl` 脚本的变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-128">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="5117d-129">它使用 **UICulture** 参数定向 cmdlet，以从的 `Simple.psd1` 子目录中的文件导入数据 `ar-SA` `C:\Data\Localized` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-129">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="5117d-130">示例 4：将本地化数据导入脚本</span><span class="sxs-lookup"><span data-stu-id="5117d-130">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="5117d-131">此示例显示如何在简单脚本中使用本地化数据。</span><span class="sxs-lookup"><span data-stu-id="5117d-131">This example shows how to use localized data in a simple script.</span></span>

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="5117d-132">该示例的第一部分显示了该文件的内容 `Test.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-132">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="5117d-133">它包含 `ConvertFrom-StringData` 可将一系列命名文本字符串转换为哈希表的命令。</span><span class="sxs-lookup"><span data-stu-id="5117d-133">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="5117d-134">此 `Test.psd1` 文件位于包含该脚本的目录的 en-us 子目录中 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-134">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="5117d-135">该示例的第二部分显示脚本的内容 `Test.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-135">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="5117d-136">它包含将 `Import-LocalizedData` 匹配文件中的数据导入到变量的命令， `.psd1` `$Messages` 以及将 `Write-Host` 变量中的消息之一写入 `$Messages` 主机程序的命令。</span><span class="sxs-lookup"><span data-stu-id="5117d-136">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="5117d-137">示例的最后一部分将运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="5117d-137">The last part of the example runs the script.</span></span> <span data-ttu-id="5117d-138">输出显示，它使用为操作系统的当前用户设置的 UI 语言显示正确的用户消息。</span><span class="sxs-lookup"><span data-stu-id="5117d-138">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="5117d-139">示例 5：替换脚本中的默认文本字符串</span><span class="sxs-lookup"><span data-stu-id="5117d-139">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="5117d-140">此示例演示如何使用 `Import-LocalizedData` 替换在脚本的 DATA 节中定义的默认文本字符串。</span><span class="sxs-lookup"><span data-stu-id="5117d-140">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="5117d-141">在此示例中，TestScript.ps1 脚本的 DATA 节包含一个 `ConvertFrom-StringData` 命令，该命令将数据部分的内容转换为哈希表，并将该变量的值存储在 `$UserMessages` 变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-141">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="5117d-142">此脚本还包括一个 `Import-LocalizedData` 命令，该命令从变量值指定的子目录中的 TestScript.psd1 文件导入已翻译文本字符串的哈希表 `$PsUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-142">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="5117d-143">如果命令找到该 `.psd1` 文件，它会将文件中的已翻译字符串保存为同一变量的值 `$UserMessages` ，并覆盖数据部分逻辑保存的哈希表。</span><span class="sxs-lookup"><span data-stu-id="5117d-143">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="5117d-144">第三个命令显示变量中的第一条消息 `$UserMessages` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-144">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="5117d-145">如果 `Import-LocalizedData` 命令找到了 `.psd1` 该语言的文件，则该变量的值将包含已 `$PsUICulture` `$UserMessages` 翻译的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="5117d-145">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="5117d-146">如果出于任何原因命令失败，则该命令将显示在脚本的 DATA 节中定义的默认文本字符串。</span><span class="sxs-lookup"><span data-stu-id="5117d-146">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="5117d-147">示例 6：在找不到 UI 区域性时取消显示错误消息</span><span class="sxs-lookup"><span data-stu-id="5117d-147">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="5117d-148">此示例演示如何禁止显示当找 `Import-LocalizedData` 不到与用户的 UI 区域性匹配的目录时出现的错误消息，或者找不到 `.psd1` 这些目录中的脚本的文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-148">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="5117d-149">可以使用值为 SilentlyContinue 的 ErrorAction 通用参数取消显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="5117d-149">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="5117d-150">当你已使用默认或回退语言提供用户消息并且不需要错误消息时，此方法特别有用。</span><span class="sxs-lookup"><span data-stu-id="5117d-150">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="5117d-151">此示例比较两个脚本 `Day1.ps1` 和 Day2.ps1，其中包含一个 `Import-LocalizedData` 命令。</span><span class="sxs-lookup"><span data-stu-id="5117d-151">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="5117d-152">脚本完全相同，只不过 Day2.ps1 使用值为的 **ErrorAction** 通用参数 `SilentlyContinue` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-152">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="5117d-153">示例输出显示了当 UI 区域性设置为 `fr-BE` ，并且该 ui 区域性没有匹配的文件或目录时，运行这两个脚本的结果。</span><span class="sxs-lookup"><span data-stu-id="5117d-153">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="5117d-154">`Day1.ps1` 显示错误消息和英语输出。</span><span class="sxs-lookup"><span data-stu-id="5117d-154">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="5117d-155">`Day2.ps1` 只显示英语输出。</span><span class="sxs-lookup"><span data-stu-id="5117d-155">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="5117d-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5117d-156">PARAMETERS</span></span>

### <span data-ttu-id="5117d-157">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="5117d-157">-BaseDirectory</span></span>

<span data-ttu-id="5117d-158">指定文件所在的基目录 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-158">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="5117d-159">默认值是脚本所在的目录。</span><span class="sxs-lookup"><span data-stu-id="5117d-159">The default is the directory where the script is located.</span></span> <span data-ttu-id="5117d-160">`Import-LocalizedData``.psd1`在基目录的特定于语言的子目录中搜索脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-160">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5117d-161">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="5117d-161">-BindingVariable</span></span>

<span data-ttu-id="5117d-162">指定文本字符串要导入的变量。</span><span class="sxs-lookup"><span data-stu-id="5117d-162">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="5117d-163">输入一个不带美元符号的变量名称 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="5117d-163">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="5117d-164">在 Windows PowerShell 2.0 中，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="5117d-164">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="5117d-165">在 Windows PowerShell 3.0 中，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="5117d-165">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="5117d-166">如果省略此参数，则 `Import-LocalizedData` 返回文本字符串的哈希表。</span><span class="sxs-lookup"><span data-stu-id="5117d-166">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="5117d-167">此哈希表将沿着管道传递或在命令行中显示。</span><span class="sxs-lookup"><span data-stu-id="5117d-167">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="5117d-168">当使用 `Import-LocalizedData` 替代在脚本的 data 节中指定的默认文本字符串时，请将数据部分分配给一个变量，并在 **BindingVariable** 参数的值中输入数据节变量的名称。</span><span class="sxs-lookup"><span data-stu-id="5117d-168">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="5117d-169">然后， `Import-LocalizedData` 将导入的内容保存到 **BindingVariable** 中时，导入的数据将替换默认文本字符串。</span><span class="sxs-lookup"><span data-stu-id="5117d-169">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable**, the imported data will replace the default text strings.</span></span> <span data-ttu-id="5117d-170">如果你不指定默认的文本字符串，则可以选择任何变量名称。</span><span class="sxs-lookup"><span data-stu-id="5117d-170">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5117d-171">-FileName</span><span class="sxs-lookup"><span data-stu-id="5117d-171">-FileName</span></span>

<span data-ttu-id="5117d-172">指定要导入 (的数据文件的名称 `.psd1)` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-172">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="5117d-173">输入文件名。</span><span class="sxs-lookup"><span data-stu-id="5117d-173">Enter a file name.</span></span> <span data-ttu-id="5117d-174">您可以指定不包括 `.psd1` 文件扩展名的文件名，也可以指定包含 `.psd1` 文件扩展名的文件名。</span><span class="sxs-lookup"><span data-stu-id="5117d-174">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="5117d-175">数据文件应保存为 Unicode 或 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="5117d-175">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="5117d-176"> `Import-LocalizedData` 不在脚本中使用时，FileName 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="5117d-176">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="5117d-177">否则，该参数是可选的，并且默认值是脚本的基名称。</span><span class="sxs-lookup"><span data-stu-id="5117d-177">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="5117d-178">可以使用此参数定向 `Import-LocalizedData` 到搜索其他 `.psd1` 文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-178">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="5117d-179">例如，如果省略 **文件名** 且脚本名称为 FindFiles.ps1，则 `Import-LocalizedData` 搜索 FindFiles.psd1 数据文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-179">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5117d-180">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="5117d-180">-SupportedCommand</span></span>

<span data-ttu-id="5117d-181">指定仅生成数据的 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="5117d-181">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="5117d-182">使用此参数以包含已写入或已测试的 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="5117d-182">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="5117d-183">有关详细信息，请参阅 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="5117d-183">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5117d-184">-UICulture</span><span class="sxs-lookup"><span data-stu-id="5117d-184">-UICulture</span></span>

<span data-ttu-id="5117d-185">指定替代 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="5117d-185">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="5117d-186">默认值为自动变量的值 `$PsUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-186">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="5117d-187">输入格式的 UI 区域性 `<language>-<region>` ，例如 `en-US` 、 `de-DE` 或 `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-187">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="5117d-188">**UICulture** 参数的值确定基目录) 中特定于语言的子目录 (`Import-LocalizedData` 获取 `.psd1` 脚本的文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-188">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="5117d-189">Cmdlet 将搜索名称与 **UICulture** 参数或自动变量的值相同的子目录 `$PsUICulture` ，例如 `de-DE` 或 `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-189">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="5117d-190">如果它找不到该目录或该目录不包含 `.psd1` 该脚本的文件，它将搜索带有语言代码名称的子目录，如 de 或 ar。</span><span class="sxs-lookup"><span data-stu-id="5117d-190">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="5117d-191">如果找不到子目录或 `.psd1` 文件，则该命令将失败，并且数据将以脚本中指定的默认语言显示。</span><span class="sxs-lookup"><span data-stu-id="5117d-191">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5117d-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5117d-192">CommonParameters</span></span>

<span data-ttu-id="5117d-193">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5117d-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5117d-194">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5117d-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5117d-195">输入</span><span class="sxs-lookup"><span data-stu-id="5117d-195">INPUTS</span></span>

### <span data-ttu-id="5117d-196">无</span><span class="sxs-lookup"><span data-stu-id="5117d-196">None</span></span>

<span data-ttu-id="5117d-197">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5117d-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5117d-198">输出</span><span class="sxs-lookup"><span data-stu-id="5117d-198">OUTPUTS</span></span>

### <span data-ttu-id="5117d-199">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="5117d-199">System.Collections.Hashtable</span></span>

<span data-ttu-id="5117d-200">`Import-LocalizedData` 将哈希表保存在由 **BindingVariable** 参数的值指定的变量中。</span><span class="sxs-lookup"><span data-stu-id="5117d-200">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="5117d-201">注释</span><span class="sxs-lookup"><span data-stu-id="5117d-201">NOTES</span></span>

- <span data-ttu-id="5117d-202">使用之前 `Import-LocalizedData` ，请对用户消息进行本地化。</span><span class="sxs-lookup"><span data-stu-id="5117d-202">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="5117d-203">在键/值对的哈希表中，设置每个区域设置的消息 (UI 区域性) ，并将哈希表保存在与脚本名称相同的文件和 `.psd1` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="5117d-203">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="5117d-204">在脚本目录下为每个受支持的 UI 区域性创建一个目录，然后 `.psd1` 使用 ui 区域性名称保存目录中每个 ui 区域性的文件。</span><span class="sxs-lookup"><span data-stu-id="5117d-204">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="5117d-205">例如，对 de-DE 区域设置对应的用户消息进行本地化并在哈希表中对其进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="5117d-205">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="5117d-206">将哈希表保存在一个 `<ScriptName>.psd1` 文件中。</span><span class="sxs-lookup"><span data-stu-id="5117d-206">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="5117d-207">然后在 `de-DE` 脚本目录下创建一个子目录，并将德语 `<ScriptName\>.psd1` 文件保存在 `de-DE` 子目录中。</span><span class="sxs-lookup"><span data-stu-id="5117d-207">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="5117d-208">为你支持的每个区域设置重复此方法。</span><span class="sxs-lookup"><span data-stu-id="5117d-208">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="5117d-209">`Import-LocalizedData` 为脚本的本地化用户消息执行结构化搜索。</span><span class="sxs-lookup"><span data-stu-id="5117d-209">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="5117d-210">`Import-LocalizedData` 在脚本文件所在的目录中开始搜索 (或 **BaseDirectory** 参数的值) 。</span><span class="sxs-lookup"><span data-stu-id="5117d-210">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="5117d-211">然后在基目录中搜索与该变量的值相同的子目录 `$PsUICulture` ， (或 **UICulture** 参数的值) ，例如 `de-DE` 或 `ar-SA` 。</span><span class="sxs-lookup"><span data-stu-id="5117d-211">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="5117d-212">然后，它在该子目录中搜索 `.psd1` 与脚本同名的文件 (或 **FileName** 参数的值) 。</span><span class="sxs-lookup"><span data-stu-id="5117d-212">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="5117d-213">如果找 `Import-LocalizedData` 不到具有 UI 区域性名称的子目录，或子目录不包含 `.psd1` 该脚本的文件，它将 `.psd1` 在子目录中搜索带有语言代码名称的脚本文件，如 de 或 ar。</span><span class="sxs-lookup"><span data-stu-id="5117d-213">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="5117d-214">如果它找不到子目录或 `.psd1` 文件，则该命令将失败，并显示一条错误消息，说明数据无法导入。</span><span class="sxs-lookup"><span data-stu-id="5117d-214">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="5117d-215">若要取消显示该消息并无声地指示失败，请使用值为 SilentlyContinue 的 ErrorAction 通用参数。</span><span class="sxs-lookup"><span data-stu-id="5117d-215">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="5117d-216">如果 `Import-LocalizedData` 找到子目录和 `.psd1` 文件，它会将用户消息的哈希表导入命令中 **BindingVariable** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="5117d-216">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="5117d-217">然后，当你显示来自变量中的哈希表的消息时，将显示已本地化的消息。</span><span class="sxs-lookup"><span data-stu-id="5117d-217">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="5117d-218">有关详细信息，请参阅 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="5117d-218">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="5117d-219">相关链接</span><span class="sxs-lookup"><span data-stu-id="5117d-219">RELATED LINKS</span></span>

[<span data-ttu-id="5117d-220">Write-Host</span><span class="sxs-lookup"><span data-stu-id="5117d-220">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="5117d-221">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="5117d-221">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)

