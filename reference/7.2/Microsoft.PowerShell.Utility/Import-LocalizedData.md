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
# Import-LocalizedData

## 摘要
基于针对操作系统所选择的 UI 区域性，将特定于语言的数据导入脚本和函数。

## SYNTAX

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## DESCRIPTION

该 `Import-LocalizedData` cmdlet 会动态地从其名称与为操作系统的当前用户设置的 UI 语言的子目录中检索字符串。 它专门用于使脚本可以使用当前用户选择的 UI 语言来显示用户消息。

`Import-LocalizedData` 从 `.psd1` 脚本目录的特定于语言的子目录中的文件导入数据，并将其保存在命令中指定的本地变量中。 该 cmdlet 根据自动变量的值选择子目录和文件 `$PSUICulture` 。 当你使用脚本中的局部变量显示用户消息时，将以用户的 UI 语言显示该消息。

您可以使用的参数 `Import-LocalizedData` 来指定替换的 UI 区域性、路径和文件名，以添加受支持的命令，以及禁止在找不到文件时显示的错误消息 `.psd1` 。

`Import-LocalizedData`Cmdlet 支持 Windows PowerShell 2.0 中引入的脚本国际化计划。 此计划旨在通过使脚本更易于使用当前用户的 UI 语言显示用户消息，来为全球用户提供更好的服务。 有关此文件和文件格式的详细信息 `.psd1` ，请参阅 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。

## 示例

### 示例 1：导入文本字符串

此示例将文本字符串导入到 `$Messages` 变量中。 它使用其他所有 cmdlet 参数的默认值。

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

如果该命令包含在目录中的 Archives.ps1 脚本中 `C:\Test` ，并且 `$PsUICulture` 自动变量的值为 ZH-CHS-CN，则会将 `Import-LocalizedData` `Archives.psd1` 该目录中的文件导入 `C:\test\zh-CN` 到 `$Messages` 变量中。

### 示例 2：导入本地化数据字符串

此示例在命令行中运行，而不是在脚本中运行。 它从 Test.psd1 文件中获取本地化的数据字符串，并将它们显示在命令行中。 由于未在脚本中使用该命令，因此 **FileName** 参数是必需的。 该命令使用 UICuture 参数指定 en-US 区域性。

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

`Import-LocalizedData` 返回一个包含本地化的数据字符串的哈希表。

### 示例 3：导入 UI 区域性字符串

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

此命令将文本字符串导入 `$MsgTbl` 脚本的变量中。

它使用 **UICulture** 参数定向 cmdlet，以从的 `Simple.psd1` 子目录中的文件导入数据 `ar-SA` `C:\Data\Localized` 。

### 示例 4：将本地化数据导入脚本

此示例显示如何在简单脚本中使用本地化数据。

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

该示例的第一部分显示了该文件的内容 `Test.psd1` 。 它包含 `ConvertFrom-StringData` 可将一系列命名文本字符串转换为哈希表的命令。 此 `Test.psd1` 文件位于包含该脚本的目录的 en-us 子目录中 `C:\Test` 。

该示例的第二部分显示脚本的内容 `Test.ps1` 。 它包含将 `Import-LocalizedData` 匹配文件中的数据导入到变量的命令， `.psd1` `$Messages` 以及将 `Write-Host` 变量中的消息之一写入 `$Messages` 主机程序的命令。

示例的最后一部分将运行该脚本。 输出显示，它使用为操作系统的当前用户设置的 UI 语言显示正确的用户消息。

### 示例 5：替换脚本中的默认文本字符串

此示例演示如何使用 `Import-LocalizedData` 替换在脚本的 DATA 节中定义的默认文本字符串。

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

在此示例中，TestScript.ps1 脚本的 DATA 节包含一个 `ConvertFrom-StringData` 命令，该命令将数据部分的内容转换为哈希表，并将该变量的值存储在 `$UserMessages` 变量中。

此脚本还包括一个 `Import-LocalizedData` 命令，该命令从变量值指定的子目录中的 TestScript.psd1 文件导入已翻译文本字符串的哈希表 `$PsUICulture` 。 如果命令找到该 `.psd1` 文件，它会将文件中的已翻译字符串保存为同一变量的值 `$UserMessages` ，并覆盖数据部分逻辑保存的哈希表。

第三个命令显示变量中的第一条消息 `$UserMessages` 。

如果 `Import-LocalizedData` 命令找到了 `.psd1` 该语言的文件，则该变量的值将包含已 `$PsUICulture` `$UserMessages` 翻译的文本字符串。 如果出于任何原因命令失败，则该命令将显示在脚本的 DATA 节中定义的默认文本字符串。

### 示例 6：在找不到 UI 区域性时取消显示错误消息

此示例演示如何禁止显示当找 `Import-LocalizedData` 不到与用户的 UI 区域性匹配的目录时出现的错误消息，或者找不到 `.psd1` 这些目录中的脚本的文件。

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

可以使用值为 SilentlyContinue 的 ErrorAction 通用参数取消显示错误消息。 当你已使用默认或回退语言提供用户消息并且不需要错误消息时，此方法特别有用。

此示例比较两个脚本 `Day1.ps1` 和 Day2.ps1，其中包含一个 `Import-LocalizedData` 命令。 脚本完全相同，只不过 Day2.ps1 使用值为的 **ErrorAction** 通用参数 `SilentlyContinue` 。

示例输出显示了当 UI 区域性设置为 `fr-BE` ，并且该 ui 区域性没有匹配的文件或目录时，运行这两个脚本的结果。 `Day1.ps1` 显示错误消息和英语输出。 `Day2.ps1` 只显示英语输出。

## PARAMETERS

### -BaseDirectory

指定文件所在的基目录 `.psd1` 。 默认值是脚本所在的目录。 `Import-LocalizedData``.psd1`在基目录的特定于语言的子目录中搜索脚本文件。

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

### -BindingVariable

指定文本字符串要导入的变量。 输入一个不带美元符号的变量名称 (`$`) 。

在 Windows PowerShell 2.0 中，此参数是必需的。 在 Windows PowerShell 3.0 中，此参数是必需的。 如果省略此参数，则 `Import-LocalizedData` 返回文本字符串的哈希表。 此哈希表将沿着管道传递或在命令行中显示。

当使用 `Import-LocalizedData` 替代在脚本的 data 节中指定的默认文本字符串时，请将数据部分分配给一个变量，并在 **BindingVariable** 参数的值中输入数据节变量的名称。 然后， `Import-LocalizedData` 将导入的内容保存到 **BindingVariable** 中时，导入的数据将替换默认文本字符串。 如果你不指定默认的文本字符串，则可以选择任何变量名称。

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

### -FileName

指定要导入 (的数据文件的名称 `.psd1)` 。 输入文件名。 您可以指定不包括 `.psd1` 文件扩展名的文件名，也可以指定包含 `.psd1` 文件扩展名的文件名。 数据文件应保存为 Unicode 或 UTF-8。

 `Import-LocalizedData` 不在脚本中使用时，FileName 参数是必需的。
否则，该参数是可选的，并且默认值是脚本的基名称。 可以使用此参数定向 `Import-LocalizedData` 到搜索其他 `.psd1` 文件。

例如，如果省略 **文件名** 且脚本名称为 FindFiles.ps1，则 `Import-LocalizedData` 搜索 FindFiles.psd1 数据文件。

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

### -SupportedCommand

指定仅生成数据的 cmdlet 和函数。

使用此参数以包含已写入或已测试的 cmdlet 和函数。 有关详细信息，请参阅 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)。

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

### -UICulture

指定替代 UI 区域性。
默认值为自动变量的值 `$PsUICulture` 。
输入格式的 UI 区域性 `<language>-<region>` ，例如 `en-US` 、 `de-DE` 或 `ar-SA` 。

**UICulture** 参数的值确定基目录) 中特定于语言的子目录 (`Import-LocalizedData` 获取 `.psd1` 脚本的文件。

Cmdlet 将搜索名称与 **UICulture** 参数或自动变量的值相同的子目录 `$PsUICulture` ，例如 `de-DE` 或 `ar-SA` 。 如果它找不到该目录或该目录不包含 `.psd1` 该脚本的文件，它将搜索带有语言代码名称的子目录，如 de 或 ar。 如果找不到子目录或 `.psd1` 文件，则该命令将失败，并且数据将以脚本中指定的默认语言显示。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Collections.Hashtable

`Import-LocalizedData` 将哈希表保存在由 **BindingVariable** 参数的值指定的变量中。

## 注释

- 使用之前 `Import-LocalizedData` ，请对用户消息进行本地化。 在键/值对的哈希表中，设置每个区域设置的消息 (UI 区域性) ，并将哈希表保存在与脚本名称相同的文件和 `.psd1` 文件扩展名。 在脚本目录下为每个受支持的 UI 区域性创建一个目录，然后 `.psd1` 使用 ui 区域性名称保存目录中每个 ui 区域性的文件。

  例如，对 de-DE 区域设置对应的用户消息进行本地化并在哈希表中对其进行格式设置。
  将哈希表保存在一个 `<ScriptName>.psd1` 文件中。 然后在 `de-DE` 脚本目录下创建一个子目录，并将德语 `<ScriptName\>.psd1` 文件保存在 `de-DE` 子目录中。
  为你支持的每个区域设置重复此方法。

- `Import-LocalizedData` 为脚本的本地化用户消息执行结构化搜索。

  `Import-LocalizedData` 在脚本文件所在的目录中开始搜索 (或 **BaseDirectory** 参数的值) 。 然后在基目录中搜索与该变量的值相同的子目录 `$PsUICulture` ， (或 **UICulture** 参数的值) ，例如 `de-DE` 或 `ar-SA` 。 然后，它在该子目录中搜索 `.psd1` 与脚本同名的文件 (或 **FileName** 参数的值) 。

  如果找 `Import-LocalizedData` 不到具有 UI 区域性名称的子目录，或子目录不包含 `.psd1` 该脚本的文件，它将 `.psd1` 在子目录中搜索带有语言代码名称的脚本文件，如 de 或 ar。 如果它找不到子目录或 `.psd1` 文件，则该命令将失败，并显示一条错误消息，说明数据无法导入。 若要取消显示该消息并无声地指示失败，请使用值为 SilentlyContinue 的 ErrorAction 通用参数。

  如果 `Import-LocalizedData` 找到子目录和 `.psd1` 文件，它会将用户消息的哈希表导入命令中 **BindingVariable** 参数的值。 然后，当你显示来自变量中的哈希表的消息时，将显示已本地化的消息。

  有关详细信息，请参阅 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)。

## 相关链接

[Write-Host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)

