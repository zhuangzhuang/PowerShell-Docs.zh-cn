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
# <a name="about-script-internationalization"></a>关于脚本国际化

## <a name="short-description"></a>简短说明
介绍脚本国际化功能，这些功能使脚本可以轻松地在用户界面中向用户显示消息和说明 (UI) 语言。

## <a name="long-description"></a>详细说明

使用 PowerShell 脚本国际化功能，您可以通过以用户的语言显示帮助和用户消息来更好地为世界各地的用户提供服务。

脚本国际化功能在执行过程中查询操作系统的 UI 区域性，导入适当的翻译文本字符串，并将其显示给用户。 Data 节使你可以存储与代码分开的文本字符串，以便能够轻松地识别和提取它们。 新的 cmdlet `ConvertFrom-StringData` 将文本字符串转换为类似字典的哈希表，以方便转换。

为支持国际帮助文本，PowerShell 包含以下功能：

- 用于分隔文本字符串与代码说明的数据部分。 有关 Data 部分的详细信息，请参阅 [about_Data_Sections](about_Data_Sections.md)。

- 新的自动变量、 `$PSCulture` 和 `$PSUICulture` 。 `$PSCulture` 将系统上使用的 UI 语言的名称存储到元素，例如日期、时间和货币。 `$PSUICulture`变量存储用于用户界面元素（如菜单和文本字符串）的系统 UI 语言的名称。

- Cmdlet， `ConvertFrom-StringData` 它将文本字符串转换为类似字典的哈希表以便于翻译。 有关详细信息，请参阅 [convertfrom-csv-convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)。

- 新的文件类型， `.psd1` 用于存储已翻译的文本字符串。 `.psd1`文件存储在脚本目录的特定于语言的子目录中。

- Cmdlet， `Import-LocalizedData` 它在运行时将指定语言的已翻译文本字符串导入脚本。 此 cmdlet 识别并导入任意 Windows 支持的语言的字符串。 有关详细信息，请参阅 [import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)。

### <a name="the-data-section-storing-default-strings"></a>Data 部分：存储默认字符串

使用脚本中的数据部分以默认语言存储文本字符串。 在此处字符串中的键/值对中排列字符串。 每个键/值对必须位于单独的行上。 如果包含注释，则注释必须位于单独的行上。

该 `ConvertFrom-StringData` cmdlet 将在此处字符串中的键/值对转换为类似字典的哈希表，该哈希表存储在 Data 节变量的值中。

在下面的示例中，脚本的数据部分 `World.ps1` 包含 English-United 状态 (en-us) 脚本的提示消息集。 `ConvertFrom-StringData`Cmdlet 将字符串转换为哈希表，并将其存储在 `$msgtable` 变量中。

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

有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。

### <a name="psd1-files-storing-translated-strings"></a>PSD1 文件：存储已转换的字符串

将每个 UI 语言的脚本消息保存在单独的文本文件中，并将其名称与脚本和 `.psd1` 文件扩展名相同。 将文件存储在具有以下格式的区域性名称的脚本目录子目录中：

`<language>-<region>`

示例： de DE、ar-SA 和 zh-chs-Hans

例如，如果该 `World.ps1` 脚本存储在 `C:\Scripts` 目录中，则会创建类似于以下内容的文件目录结构：

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

`World.psd1`脚本目录的 de 子目录中的文件可能包含以下语句：

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

同样， `World.psd1` 脚本目录的 ar-SA 子目录中的文件可能包含以下语句：

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>Import-localizeddata：动态检索转换字符串

若要检索当前用户的 UI 语言的字符串，请使用 `Import-LocalizedData` cmdlet。

`Import-LocalizedData` 查找自动变量的值 `$PSUICulture` ，并导入 `<script-name>.psd1` 子目录中与该值匹配的文件的内容 `$PSUICulture` 。 然后，它将导入的内容保存在由 **BindingVariable** 参数的值所指定的变量中。

```powershell
Import-LocalizedData -BindingVariable msgTable
```

例如，如果 `Import-LocalizedData` 命令出现在 `C:\Scripts\World.ps1` 脚本中并且的值 `$PSUICulture` 为 "ar-SA"，则 `Import-LocalizedData` 查找以下文件：

`C:\Scripts\ar-SA\World.psd1`

然后，它会将阿拉伯语文本字符串从文件导入到 `$msgTable` 变量，替换可能在脚本的 Data 节中定义的任何默认字符串 `World.ps1` 。

因此，当脚本使用 `$msgTable` 变量显示用户消息时，消息将显示为阿拉伯语。

例如，以下脚本将显示阿拉伯语中的 "请输入您的用户名" 消息：

```powershell
if (!($username)) { $msgTable.promptMsg }
```

如果 `Import-LocalizedData` 找不到 `.psd1` 与的值匹配的文件 `$PSUIculture` ， `$msgTable` 则不会替换的值，并且调用将 `$msgTable.promptMsg` 显示回退 en-us 字符串。

## <a name="examples"></a>示例

此示例演示如何在脚本中使用脚本国际化功能，以将一周中的某一天显示给在计算机上设置的语言的用户。

下面是 Sample1.ps1 脚本文件的完整列表。

该脚本以名为 Day ($Day 包含命令的) 数据部分开始 `ConvertFrom-StringData` 。 提交到的表达式 `ConvertFrom-StringData` 是一个字符串，其中包含默认 UI 区域性中的天名称（在键/值对中）。 `ConvertFrom-StringData`Cmdlet 将此处字符串中的键/值对转换为哈希表，然后将其保存在变量的值中 `$Day` 。

`Import-LocalizedData`命令将导入 `.psd1` 目录中与自动变量的值匹配的文件内容， `$PSUICulture` 然后将其保存在变量中，并 `$Day` 替换 `$Day` Data 节中定义的值。

其余的命令将字符串加载到数组中并显示它们。

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

`.psd1`支持脚本的文件保存在脚本目录的子目录中，名称与 `$PSUICulture` 值匹配。

下面是完整的列表 `.\de-DE\sample1.psd1` ：

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

因此，当您在值为的系统上运行 Sample.ps1 时 `$PSUICulture` ，脚本的输出为：

```Output
Heute ist Freitag
```

## <a name="see-also"></a>请参阅

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

