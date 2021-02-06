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
# ConvertFrom-StringData

## 摘要
将包含一个或多个键-值对的字符串转换为哈希表。

## SYNTAX

### 全部

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-StringData`Cmdlet 将包含一个或多个键和值对的字符串转换为哈希表。 由于每个键-值对都必须位于单独的行上，因此，通常使用字符串作为输入格式。 默认情况下，必须将该 **密钥** 与 **值** 之间用等号分隔 (`=`) 字符。

该 `ConvertFrom-StringData` cmdlet 被视为可在脚本或函数的部分中使用的安全 cmdlet `DATA` 。 当在节中使用时 `DATA` ，字符串的内容必须符合数据部分的规则。 有关详细信息，请参阅 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)。

`ConvertFrom-StringData` 支持传统机器翻译工具允许的转义字符序列。 也就是说，该 cmdlet 可以 `\` 使用 [Unescape 方法](/dotnet/api/system.text.regularexpressions.regex.unescape)解释字符串数据中) 转义符 (反斜杠，而不是使用 PowerShell 反撇号字符 (\`) 通常会在脚本中发出行的结尾。 在 here-string 中，反撇号字符无效。 还可以通过使用前面的反斜杠对其进行转义，使结果保留在结果中，如下所示： `\\` 。 未转义的反斜杠字符（例如那些通常用在文件路径中的反斜杠字符）可以在结果中呈现为非法的转义序列。

PowerShell 7 添加了 **分隔符** 参数。

## 示例

### 示例1：将此处的单引用字符串转换为哈希表

此示例将用户消息的单引用字符串转换为哈希表。 在带单引号的字符串中，不能使用变量和无法计算的表达式来代替其值。
`ConvertFrom-StringData`Cmdlet 将变量中的值转换 `$Here` 为哈希表。

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

### 示例2：使用不同的分隔符转换字符串数据

此示例演示如何转换使用其他字符作为分隔符的字符串数据。 在此示例中，字符串数据使用管道字符 (`|`) 作为分隔符。

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

### 示例3：在此处转换包含注释的字符串

此示例将包含注释和多个键/值对的字符串转换为哈希表。

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

**Convertfrom-stringdata** 参数的值是一个字符串，而不是包含此字符串的变量。 两种格式都有效。 here-string 包括有关某字符串的注释。
`ConvertFrom-StringData` 忽略单行注释，但该 `#` 字符必须是行中的第一个非空白字符。 忽略后行中的所有字符 `#` 。

### 示例4：将字符串转换为哈希表

下面的示例将一个用双引号括起来的规则)  (转换为哈希表，并将其保存在 `$A` 变量中。

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

为了满足每个键/值对必须位于一个单独的行上的条件，该字符串使用 PowerShell 换行符 (\` n) 来分隔配对。

### 示例5：使用脚本的 DATA 节中的 ConvertFrom-StringData

此示例演示 `ConvertFrom-StringData` 脚本的数据部分中使用的命令。
DATA 节下面的语句向用户显示该文本。

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

由于文本包括变量名称，所以必须用单引号将它括起来，以便按照字义解释变量，而不是展开它。 不允许在 **DATA** 节中使用变量。

### 示例6：使用管道运算符传递字符串

此示例演示可以使用管道运算符 (`|`) 将字符串发送到 `ConvertFrom-StringData` 。 变量的值将通过 `$Here` 管道传递给 `ConvertFrom-StringData` ，并将结果放入 `$Hash` 变量中。

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

### 示例7：使用转义字符添加新行和返回字符

此示例演示如何使用转义字符创建新行并返回源数据中的字符。 转义序列 `\n` 用于在与生成的哈希表中的名称或项关联的文本块中创建新行。

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

### 示例8：使用反斜杠转义字符正确呈现文件路径

此示例演示如何使用字符串数据中的反斜杠转义字符，以允许在生成的哈希表中正确呈现文件路径 `ConvertFrom-StringData` 。 双反斜杠可确保文本反斜杠字符正确呈现在哈希表输出中。

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETERS

### -StringData

指定要转换的字符串。 可以使用此参数或通过管道将字符串传递给 `ConvertFrom-StringData` 。 参数名为可选项。

此参数的值必须是包含一个或多个键/值对的字符串。 每个键/值对必须位于单独的行上，或每个对必须由换行符分隔 (\` n) 。

您可以在字符串中包含注释，但是注释不能与键值对在同一行上。 `ConvertFrom-StringData` 忽略单行注释。 该 `#` 字符必须是行中的第一个非空白字符。 忽略后行中的所有字符 `#` 。 哈希表中不包括注释。

这是一个字符串，包含一行或多行。 在此处字符串中的引号将按原义解释为字符串数据的一部分。 有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。

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

### -Delimiter

用于在要转换的字符串的 **值** 数据中分隔 **键** 的字符。
默认分隔符为等于符号 (`=`) 字符。 此参数是在 PowerShell 7 中添加的。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含键/值对的字符串传递给 `ConvertFrom-StringData` 。

## 输出

### System.Collections.Hashtable

此 cmdlet 将返回一个哈希表，该哈希表是从键/值对创建的。

## 注释

here-string 是由一行或多行组成的字符串，在其中，按照字义解释引号。

此 cmdlet 可用于以多种语言显示用户消息的脚本。 可使用字典风格的哈希表来从代码中隔离文本字符串（如在资源文件中），并为文本字符串设置格式以便在转换工具中使用。

## 相关链接

