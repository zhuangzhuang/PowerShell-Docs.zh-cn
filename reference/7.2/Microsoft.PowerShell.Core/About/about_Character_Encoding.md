---
description: 描述 PowerShell 如何使用字符串数据的输入和输出的字符编码。
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 3b47a528b0beae5e8142157454cbc676ffd7e795
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "99597466"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>简短说明
描述 PowerShell 如何使用字符串数据的输入和输出的字符编码。

## <a name="long-description"></a>长说明

Unicode 是一种全球字符编码标准。 系统仅将 Unicode 用于字符和字符串操作。 有关 Unicode 的所有方面的详细说明，请参阅 [Unicode 标准](https://www.unicode.org/standard/standard.html)。

Windows 支持 Unicode 和传统字符集。 传统字符集（如 Windows 代码页）使用8位值或8位值的组合来表示特定语言或地理区域设置中使用的字符。

默认情况下，PowerShell 使用 Unicode 字符集。 但是，有几个 cmdlet 具有可为不同字符集指定编码的 **编码** 参数。 此参数允许你选择与其他系统和应用程序的互操作性所需的特定字符编码。

以下 cmdlet 具有 **Encoding** 参数：

- Microsoft.PowerShell.Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>字节顺序标记

字节顺序标记 (BOM) 是文件或文本流的前几个字节中的 _Unicode 签名_ ，指示用于数据的 unicode 编码。 有关详细信息，请参阅 [字节顺序标记](/globalization/encoding/byte-order-mark) 文档。

在 Windows PowerShell 中，除之外的任何 Unicode 编码 `UTF7` 都将始终创建 BOM。 所有文本输出的 PowerShell Core 默认值为 `utf8NoBOM` 。

为了获得最佳的整体兼容性，请避免在 UTF-8 文件中使用 Bom。 在 Windows 平台上还使用的 unix 平台和 Unix 的遗产保护实用工具不支持 Bom。

同样， `UTF7` 应避免编码。 UTF-7 不是标准的 Unicode 编码，并且在所有版本的 PowerShell 中都不使用 BOM 来编写。

在类似于 Unix 的平台上或在 Windows 上使用跨平台编辑器（如 Visual Studio Code）创建 PowerShell 脚本会导致使用对文件进行编码 `UTF8NoBOM` 。 这些文件在 PowerShell Core 上运行正常，但如果文件包含非 Ascii 字符，则可能会在 Windows PowerShell 中中断。

如果需要在脚本中使用非 Ascii 字符，请使用 BOM 将它们另存为 UTF-8。 如果没有 BOM，Windows PowerShell 会将脚本 misinterprets 为在旧的 "ANSI" 代码页中编码。 相反，具有 UTF-8 BOM 的文件在类似 Unix 的平台上可能会出现问题。 许多 Unix 工具（如 `cat` 、 `sed` 、 `awk` 和一些编辑器）（如 `gedit` 不知道如何处理 BOM）。

## <a name="character-encoding-in-windows-powershell"></a>Windows PowerShell 中的字符编码

在 PowerShell 5.1 中， **Encoding** 参数支持以下值：

- `Ascii` 使用 Ascii (7 位) 字符集。
- `BigEndianUnicode` 使用带有大 endian 字节顺序的 UTF-16。
- `BigEndianUTF32` 使用带有大字节序字节顺序的 32 UTF-8。
- `Byte` 将一组字符编码为一个字节序列。
- `Default` 使用与系统的活动代码页相对应的编码 (通常为 ANSI) 。
- `Oem` 使用与系统的当前 OEM 代码页相对应的编码。
- `String` 与 `Unicode` 相同。
- `Unicode` 使用带有小 endian 字节顺序的 UTF-16。
- `Unknown` 与 `Unicode` 相同。
- `UTF32` 使用带有小 endian 字节顺序的 32 UTF-8。
- `UTF7` 使用 UTF-8。
- `UTF8` 对 BOM) 使用 UTF-8 (。

通常，默认情况下，Windows PowerShell 使用 Unicode [utf-16le](https://wikipedia.org/wiki/UTF-16) 编码。 但是，Windows PowerShell 中的 cmdlet 使用的默认编码是不一致的。

> [!NOTE]
> 使用除之外的任何 Unicode 编码 `UTF7` 都将始终创建 BOM。

对于将输出写入文件的 cmdlet：

- `Out-File` 和重定向运算符， `>` 并 `>>` 创建 utf-16le，这一点与和不同 `Set-Content` `Add-Content` 。

- `New-ModuleManifest``Export-CliXml`还会创建 utf-16le 文件。

- 当目标文件为空或不存在时， `Set-Content` `Add-Content` 使用 `Default` 编码。 `Default` 是由活动系统区域设置的 ANSI 旧版代码页指定的编码。

- `Export-Csv` 创建 `Ascii` 文件，但使用 **追加** 参数时使用不同的编码 (参见下面的) 。

- `Export-PSSession` 默认情况下，使用 BOM 创建 UTF-8 文件。

- `New-Item -Type File -Value` 创建不带 BOM 的 UTF-8 文件。

- `Send-MailMessage``Default`默认情况下使用编码。

- `Start-Transcript``Utf8`使用 BOM 创建文件。 使用 **Append** 参数时，编码可能不同 (参见下面) 。

对于追加到现有文件的命令：

- `Out-File -Append``>>`重定向运算符不会尝试匹配现有目标文件内容的编码。 相反，它们使用默认编码，除非使用 **编码** 参数。 追加内容时，必须使用原始编码文件。

- 如果没有显式 **编码** 参数，将检测到 `Add-Content` 现有编码，并将其自动应用于新内容。 如果现有内容没有 BOM， `Default` 则使用 ANSI 编码。 `Add-Content`在 PowerShell Core (v6 和更高) 版本中，的行为相同，不同之处在于默认编码为 `Utf8` 。

- `Export-Csv -Append` 当目标文件包含 BOM 时，匹配现有编码。 如果没有 BOM，则使用 `Utf8` 编码。

- `Start-Transcript -Append` 匹配包含 BOM 的文件的现有编码。 如果没有 BOM，则默认为 `Ascii` 编码。 当脚本中的数据包含多字节字符时，此编码可能会导致数据丢失或字符损坏。

对于读取缺少 BOM 的字符串数据的 cmdlet：

- `Get-Content` 和 `Import-PowerShellDataFile` 使用 `Default` ANSI 编码。 在从文件读取源代码时，它也是 PowerShell 引擎使用的内容。

- `Import-Csv`、 `Import-CliXml` 和 `Select-String` 假设 `Utf8` 缺少 BOM。

## <a name="character-encoding-in-powershell-core"></a>PowerShell Core 中的字符编码

在 PowerShell Core (v6 和更高版本中) ， **Encoding** 参数支持以下值：

- `ascii`：使用 ASCII (7 位) 字符集的编码。
- `bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。
- `oem`：使用 MS-DOS 和控制台程序的默认编码。
- `unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。
- `utf7`：以 UTF-7 格式进行编码。
- `utf8`：以 UTF-8 格式编码 (不) BOM。
- `utf8BOM`：以 UTF-8 格式编码 (BOM) 
- `utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) 
- `utf32`：以32格式编码。

对于所有输出，PowerShell Core 默认值为 `utf8NoBOM` 。

从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。 有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage)

## <a name="changing-the-default-encoding"></a>更改默认编码

PowerShell 具有两个可用于更改默认编码行为的默认变量。

- `$PSDefaultParameterValues`
- `$OutputEncoding`

有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

从 PowerShell 5.1 开始，重定向操作员 (`>` 和 `>>`) 调用 `Out-File` cmdlet。 因此，你可以使用首选项变量设置其默认编码， `$PSDefaultParameterValues` 如以下示例中所示：

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

使用以下语句来更改具有 **encoding** 参数的所有 cmdlet 的默认编码。

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> 在 PowerShell 配置文件中放置此命令可使首选项成为会话全局设置，该设置会影响未显式指定编码的所有命令和脚本。
>
> 同样，你应该将此类命令包含在你希望以相同方式运行的脚本或模块中。 使用这些命令可确保 cmdlet 的行为方式与其他用户在其他计算机上运行或在不同版本的 PowerShell 中运行时的行为相同。

自动变量 `$OutputEncoding` 会影响 PowerShell 用于与外部程序通信的编码。 它不会影响输出重定向运算符和 PowerShell cmdlet 用于保存到文件的编码。

## <a name="see-also"></a>请参阅

- [.NET 中的字符编码简介](/dotnet/standard/base-types/character-encoding-introduction)
- [代码页-Win32 应用](/windows/win32/intl/code-pages)
- [Unicode 标准](https://www.unicode.org/standard/standard.html)
- [编码。代码页](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [字节顺序标记](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
