---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 339afab9c817b54a79e2f1b33b7021ecb4fe6a6e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596617"
---
# Select-String

## 摘要
在字符串和文件中查找文本。

## SYNTAX

### File（默认值）

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### ObjectRaw

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### 对象

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### FileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## DESCRIPTION

`Select-String`Cmdlet 将搜索输入字符串和文件中的文本模式和文本模式。 你可以使用 `Select-String` 类似于 UNIX 中的 **Grep** 或 Windows 中的 **findstr.exe** 。

`Select-String` 基于文本行。 默认情况下， `Select-String` 会在每一行中查找第一个匹配项，对于每个匹配项，它将在包含匹配项的行中显示文件名、行号和所有文本。 您可以直接 `Select-String` 查找每行的多个匹配项，在匹配前后显示文本，或显示一个布尔值 (True 或 False) 指示是否找到了匹配项。

`Select-String` 使用正则表达式匹配，但它还可以执行匹配，以便在输入中搜索指定的文本。

`Select-String` 可以在每个输入文件中的第一个匹配项之后显示所有文本匹配项或停止。
`Select-String` 可用于显示与指定模式不匹配的所有文本。

您还可以指定 `Select-String` 应使用特定字符编码，例如搜索 Unicode 文本的文件时。 `Select-String` 使用字节顺序标记 (BOM) 来检测文件的编码格式。 如果文件没有 BOM，则假定编码为 UTF8。

## 示例

### 示例1：查找区分大小写的匹配

此示例对已向下管道发送到 cmdlet 的文本执行区分大小写的匹配 `Select-String` 。

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

文本字符串 **hello** 和 **hello** 会将管道发送到 `Select-String` cmdlet。
`Select-String` 使用 **Pattern** 参数指定 **HELLO**。 **CaseSensitive** 参数指定该事例必须仅与大写模式匹配。 **SimpleMatch** 是一个可选参数，它指定模式中的字符串不会解释为正则表达式。
`Select-String` 在 PowerShell 控制台中显示 " **HELLO** "。

### 示例2：查找文本文件中的匹配项

此命令 `.txt` 在当前目录中搜索文件扩展名为的所有文件。 输出显示这些文件中包含指定字符串的行。

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

在此示例中， `Get-Alias` 和 `Get-Command` 与 cmdlet 一起使用， `Out-File` 以在当前目录中创建两个文本文件， **Alias.txt** 和 **Command.txt**。

`Select-String` 使用带有星号的 **Path** 参数 (`*`) 通配符，搜索当前目录中文件扩展名为的所有文件 `.txt` 。 **Pattern** 参数指定 **要匹配的** 文本。 `Select-String` 在 PowerShell 控制台中显示输出。 文件名和行号位于包含 **Pattern** 参数匹配项的每个内容行之前。

### 示例3：查找模式匹配

在此示例中，搜索多个文件以查找指定模式的匹配项。 此模式使用正则表达式限定符。 有关详细信息，请参阅 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)。

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

`Select-String`Cmdlet 使用两个参数：**路径** 和 **模式**。 **Path** 参数使用 `$PSHOME` 指定 PowerShell 目录的变量。 路径的其余部分包括子目录 **en-us** ，并指定 `*.txt` 该目录中的每个文件。 **Pattern** 参数指定匹配 `?` 每个文件中的问号 () 。 反斜杠 (`\`) 用作转义字符，这是必需的，因为问号 (`?`) 是正则表达式限定符。 `Select-String` 在 PowerShell 控制台中显示输出。 文件名和行号位于包含 **Pattern** 参数匹配项的每个内容行之前。

### 示例4：在函数中使用 Select-String

此示例创建一个函数，用于在 PowerShell 帮助文件中搜索模式。 在此示例中，该函数仅在 PowerShell 会话中存在。 关闭 PowerShell 会话后，将删除该函数。 有关详细信息，请参阅 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)。

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

在 PowerShell 命令行上创建该函数。 该 `Function` 命令使用名称 **搜索-Help**。 按 **enter** 开始向函数添加语句。 在 `>>` 提示符下，添加每个语句并按下 **enter** ，如示例中所示。 添加右括号后，会返回到 PowerShell 提示符。

函数包含两个命令。 `$PSHelp`变量存储 PowerShell 帮助文件的路径。 `$PSHOME` 是具有用于指定目录中的每个文件的子目录 **en-us** 的 PowerShell 安装目录 `*.txt` 。

`Select-String`函数中的命令使用 **路径** 和 **模式** 参数。 **Path** 参数使用 `$PSHelp` 变量来获取路径。 **Pattern** 参数使用字符串 **About_** 作为搜索条件。

若要运行此函数，请键入 `Search-Help` 。 此函数的 `Select-String` 命令显示 PowerShell 控制台中的输出。

### 示例5：在 Windows 事件日志中搜索字符串

此示例在 Windows 事件日志中搜索字符串。 变量 `$_` 表示管道中的当前对象。 有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

`Get-WinEvent`Cmdlet 使用 **LogName** 参数来指定应用程序日志。 **MaxEvents** 参数获取日志中的最新事件50。 日志内容存储在名为的变量中 `$Events` 。

该 `$Events` 变量将通过管道向下发送到 `Select-String` cmdlet。 `Select-String` 使用 **InputObject** 参数。 `$_`变量表示当前对象， `message` 是事件的属性。 物种字符串的 **Pattern** 参数 **失败** ，并在中搜索匹配项 `$_.message` 。 `Select-String` 在 PowerShell 控制台中显示输出。

### 示例6：在子目录中查找字符串

此示例在目录及其所有子目录中搜索特定的文本字符串。

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem` 使用 **Path** 参数指定 **C:\Windows\System32 \***。 **递归** 参数包括子目录。 对象将向下发送到 `Select-String` 。

`Select-String` 使用 **Pattern** 参数，并指定 **Microsoft** 的字符串。 **CaseSensitive** 参数用于匹配字符串的准确大小写。 `Select-String` 在 PowerShell 控制台中显示输出。

> [!NOTE]
> 根据你的权限，你可能会在输出中看到 " **拒绝访问** " 消息。

### 示例7：查找与模式不匹配的字符串

此示例演示如何排除与模式不匹配的数据行。

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

`Get-Command`Cmdlet 将对象向下发送到， `Out-File` 以在当前目录中创建 **Command.txt** 文件。 `Select-String` 使用 **Path** 参数指定 **Command.txt** 文件。 **Pattern** 参数指定 **Get** 和 **Set** 作为搜索模式。 **NotMatch** 参数从结果中排除 **Get** 和 **Set** 。
`Select-String` 在 PowerShell 控制台中显示不包括 **Get** 或 **Set** 的输出。

### 示例8：查找匹配项前后的行

此示例演示如何获取匹配模式前后的行。

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

`Get-Command`Cmdlet 将对象向下发送到， `Out-File` 以在当前目录中创建 **Command.txt** 文件。 `Select-String` 使用 **Path** 参数指定 **Command.txt** 文件。 **Pattern** 参数将 "**获取计算机**" 指定为搜索模式。 **上下文** 参数使用两个值（之前和之后），并在输出中用尖括号标记模式匹配 (`>`) 。 **上下文** 参数输出第一个模式匹配之前的两行以及最后一个模式匹配后的三行。

### 示例9：查找所有模式匹配项

此示例演示 **AllMatches** 参数如何查找文本行中的每个模式匹配项。 默认情况下， `Select-String` 仅在文本行中查找模式的第一个匹配项。 此示例使用通过 cmdlet 找到的对象属性 `Get-Member` 。

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数。 **Path** 参数使用 `$PSHOME` 指定 PowerShell 目录的变量。 路径的其余部分包括子目录 **en-us** ，并指定 `*.txt` 该目录中的每个文件。 这些 `Get-ChildItem` 对象存储在变量中 `$A` 。 该 `$A` 变量将通过管道向下发送到 `Select-String` cmdlet。 `Select-String` 使用 **Pattern** 参数在每个文件中搜索字符串 **PowerShell**。

在 PowerShell 命令行中 `$A` 显示变量内容。 有一行包含字符串 **PowerShell** 的两个匹配项。

`$A.Matches`属性在每一行上列出第一次出现的模式 **PowerShell** 。

`$A.Matches.Length`属性对每个行的第一个匹配项进行计数。

`$B`变量使用相同的 `Get-ChildItem` 和 `Select-String` cmdlet，但会添加 **AllMatches** 参数。 **AllMatches** 在每一行上查找模式 **PowerShell** 的每个匹配项。 和变量中存储的 `$A` 对象 `$B` 是相同的。

`$B.Matches.Length`属性会增加，因为对于每一行，都会对模式 **PowerShell** 的每个匹配项进行计数。

## PARAMETERS

### -AllMatches

指示该 cmdlet 在每个文本行中搜索多个匹配项。 如果没有此参数， `Select-String` 则仅查找每个文本行中的第一个匹配项。

当 `Select-String` 在一个文本行中找到多个匹配项时，它仍然只会为该行发出一个 **MatchInfo** 对象，但 **该** 对象的 match 属性包含所有匹配项。

> [!NOTE]
> 将此参数与 **SimpleMatch** 参数结合使用时，将忽略此参数。 如果希望返回所有匹配项并且要搜索的模式包含正则表达式字符，则必须对这些字符进行转义，而不是使用 **SimpleMatch**。 有关转义正则表达式的详细信息，请参阅 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

指示 cmdlet 匹配区分大小写。 默认情况下，匹配不区分大小写。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Context

捕获与模式匹配的行前后的指定行数。

如果你输入一个数字作为此参数的值，则该数字将确定捕获的匹配项前后的行数。 如果你输入两个数字作为此参数的值，则第一个数字将确定该匹配项前面的行数，第二个数字将确定该匹配项后面的行数。 例如，`-Context 2,3`。

在默认显示中，具有匹配项的行由右尖括号指示 (`>`) 显示的第一列中 (ASCII 62) 。 无标记行是上下文。

**上下文** 参数不会更改所生成的对象的数目 `Select-String` 。
`Select-String` 为每个匹配项生成一个 [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 对象。 上下文在对象的 **context** 属性中存储为字符串数组。

将命令的输出 `Select-String` 发送到另一个 `Select-String` 命令时，接收命令只会搜索匹配行中的文本。 匹配的行是 **MatchInfo** 对象的 **line** 属性的值，而不是上下文行中的文本。 因此， **上下文** 参数对接收 `Select-String` 命令无效。

当上下文包含匹配项时，每个匹配项的 **MatchInfo** 对象都将包括所有的上下文行，但重叠的行仅在显示中出现一次。

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

指定与指定模式匹配的区域性名称。 **Culture** 参数必须与 **SimpleMatch** 参数一起使用。 默认行为使用当前 PowerShell 运行空间的区域性 (会话) 。

若要获取所有受支持的区域性的列表，请使用 `Get-Culture -ListAvailable` 命令。

此外，此参数还接受以下参数：

- CurrentCulture，这是默认值;
- 序数，是非语言二进制比较;
- 固定，这是独立于区域性的比较。

通过 `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` 命令，可以获得最快的二进制比较。

**Culture** 参数使用 tab 自动补全在指定可用区域性的参数列表中滚动。 若要列出所有可用参数，请使用以下命令：

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

有关 .NET CultureInfo.Name 属性的详细信息，请参阅 [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name)。

**Culture** 参数是在 PowerShell 7 中引入的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目标文件的编码类型。 默认值是 `utf8NoBOM`。

此参数可接受的值如下所示：

- `ascii`：使用 ASCII (7 位) 字符集的编码。
- `bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。
- `bigendianutf32`：使用大字节序字节顺序编码为32格式。
- `oem`：使用 MS-DOS 和控制台程序的默认编码。
- `unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。
- `utf7`：以 UTF-7 格式进行编码。
- `utf8`：以 UTF-8 格式进行编码。
- `utf8BOM`：以 UTF-8 格式编码 (BOM) 
- `utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) 
- `utf32`：以32格式编码。

从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。 有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)

> [!NOTE]
> 不建议使用 **utf-7** _ _。 在 PowerShell 7.1 中，如果 `utf7` 为 _ *Encoding** 参数指定，则会写入警告。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

排除指定项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

包括指定项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

指定要搜索的文本。 输入一个包含该文本的变量，或键入可获取该文本的命令或表达式。

使用 **InputObject** 参数不同于将字符串向下发送到 `Select-String` 。

当你将多个字符串传递给 `Select-String` cmdlet 时，它会在每个字符串中搜索指定的文本，并返回包含搜索文本的每个字符串。

当使用 **InputObject** 参数提交字符串集合时，会将 `Select-String` 该集合视为单个组合字符串。 `Select-String` 如果在任何字符串中找到搜索文本，则将这些字符串作为单元返回。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -List

只从每个输入文件返回匹配文本的第一个实例。 这是检索具有与正则表达式匹配的内容的文件列表的最有效方法。

默认情况下，将 `Select-String` 为它找到的每个匹配项返回一个 **MatchInfo** 对象。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定要搜索的文件的路径。 **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。 有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoEmphasis

默认情况下， `Select-String` 将突出显示与你使用 **pattern** 参数搜索的模式匹配的字符串。 **NoEmphasis** 参数禁用突出显示。

强调基于 PowerShell 背景和文本颜色使用负颜色。 例如，如果您的 PowerShell 颜色是带有白色文本的黑色背景。 强调是带有黑色文本的白色背景。

此参数是在 PowerShell 7 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

**NotMatch** 参数查找与指定模式不匹配的文本。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要搜索的文件的路径。 允许使用通配符。 默认位置为本地目录。

指定目录中的文件，例如 `log1.txt` 、 `*.doc` 或 `*.*` 。 如果仅指定一个目录，则该命令将失败。

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Pattern

指定要在每一行上查找的文本。 模式值被视为正则表达式。

若要了解正则表达式，请参阅 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

指示该 cmdlet 将返回一个布尔值， (True 或 False) 而不是 **MatchInfo** 对象。 如果找到该模式，则该值为 True;否则，该值为 False。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Raw

使 cmdlet 仅输出匹配的字符串，而不是 **MatchInfo** 对象。 这是导致最类似于 Unix **grep** 或 Windows **findstr.exe** 命令的行为。

此参数是在 PowerShell 7 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SimpleMatch

指示该 cmdlet 使用简单匹配，而不是正则表达式匹配。 在简单匹配中，在 `Select-String` 输入中搜索 **Pattern** 参数中的文本。 它不会将 **Pattern** 参数的值解释为正则表达式语句。

此外，在使用 **SimpleMatch** 时，返回的 **MatchInfo** 对象的 "**匹配**" 属性为空。

> [!NOTE]
> 将此参数与 **AllMatches** 参数一起使用时，将忽略 **AllMatches** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将具有 **ToString** 方法的任何对象传递给 `Select-String` 。

## 输出

### MatchInfo，System.string，System.string，系统字符串

默认情况下，输出为一组 **MatchInfo** 对象，每个对象对应一个找到的匹配项。 如果使用 **Quiet** 参数，则输出将是一个指示是否找到该模式的 **布尔** 值。
如果使用 **原始** 参数，则输出将是一组与模式匹配的 **字符串** 对象。

## 注释

`Select-String` 类似于 UNIX 中的 **grep** 或 Windows 中的 **findstr.exe** 。

Cmdlet 的 **sls** 别名 `Select-String` 是在 PowerShell 3.0 中引入的。

> [!NOTE]
> 根据 [PowerShell 命令的批准的动词](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)，cmdlet 的官方别名 `Select-*` 为，而 `sc` 不是 `sl` 。 因此，的正确别名 `Select-String` 应为 `scs` ，而不是 `sls` 。 这是此规则的例外情况。

若要使用 `Select-String` ，请键入要查找为 **Pattern** 参数值的文本。 若要指定要搜索的文本，请使用以下条件：

- 在带引号的字符串中键入文本，然后将其传递给 `Select-String` 。
- 将文本字符串存储在变量中，然后将该变量指定为 **InputObject** 参数的值。
- 如果文本存储在文件中，请使用 **path** 参数指定文件的路径。

默认情况下，会将 `Select-String` **Pattern** 参数的值解释为正则表达式。 有关详细信息，请参阅 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。 可以使用 **SimpleMatch** 参数重写正则表达式匹配。 **SimpleMatch** 参数在输入中查找 **Pattern** 参数值的实例。

的默认输出 `Select-String` 是一个 **MatchInfo** 对象，其中包括有关匹配项的详细信息。 当你在文件中搜索文本时，该对象中的信息非常有用，因为 **MatchInfo** 对象具有 **Filename** 和 **Line** 等属性。 如果输入不是来自文件，则这些参数的值为 **InputStream**。

如果不需要 **MatchInfo** 对象中的信息，请使用 **Quiet** 参数。 **Quiet** 参数将返回一个布尔值 (True 或 False) 以指示它是否找到匹配项，而不是 **MatchInfo** 对象。

匹配短语时，将 `Select-String` 使用为系统设置的当前区域性。 若要查找当前区域性，请使用 `Get-Culture` cmdlet。

若要查找 **MatchInfo** 对象的属性，请键入以下命令：

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## 相关链接

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-Alias](Get-Alias.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Get-Member](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Out-File](Out-File.md)

