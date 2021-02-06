---
description: 描述 PowerShell 中的正则表达式。
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 4dc6ac670a31cbea4c35ee6540ce3368ad9b02ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598858"
---
# <a name="about-regular-expressions"></a>关于正则表达式

## <a name="short-description"></a>简短说明
描述 PowerShell 中的正则表达式。

## <a name="long-description"></a>长说明

> [!NOTE]
> 本文将介绍在 PowerShell 中使用正则表达式的语法和方法，并非所有语法都进行了讨论。 有关更完整的参考信息，请参阅 [正则表达式语言-快速参考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

正则表达式是用于匹配文本的模式。 它可以由文本字符、运算符和其他构造组成。

本文演示了 PowerShell 中的正则表达式语法。 PowerShell 具有几个使用正则表达式的运算符和 cmdlet。 可以在下面的链接中了解有关其语法和用法的详细信息。

- [Select-String](xref:Microsoft.PowerShell.Utility.Select-String)
- [-match 和-replace 运算符](about_Comparison_Operators.md)
- [-split](about_Split.md)
- [switch 语句替换为-regex 选项](about_Switch.md)

默认情况下，PowerShell 正则表达式不区分大小写。 上面所示的每个方法都有不同的方法来强制区分大小写。

|       方法       |                      区分大小写                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | 使用 `-CaseSensitive` 开关                                |
| `switch` 语句 | 使用 `-casesensitive` 选项                            |
| 运算符          | 前缀为 **"c"** (`-cmatch` 、 `-csplit` 或 `-creplace`)  |

### <a name="character-literals"></a>字符文本

正则表达式可以是文本字符或字符串。 表达式使引擎与指定的文本完全匹配。

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>字符类

虽然在您知道确切的模式的情况下，字符文本有效，但字符类允许您不太具体。

#### <a name="character-groups"></a>字符组

`[character group]` 允许您一次匹配任意数量的字符，而 `[^character group]` 只匹配不在组中的字符。

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

如果要匹配的字符列表包括连字符 (`-`) ，则它必须位于列表的开头或结尾，才能将其与字符范围表达式区分开来。

#### <a name="character-ranges"></a>字符范围

模式也可以是一系列字符。 字符可以是字母 `[A-Z]` 、数字 `[0-9]` ，甚至是基于 ASCII 的 `[ -~]` (所有可打印字符) 。

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>数字

`\d`字符类将匹配任何十进制数字。 相反， `\D` 将与任何非十进制数字匹配。

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>单词字符

`\w`字符类将匹配任何单词字符 `[a-zA-Z_0-9]` 。 若要匹配任何非单词字符，请使用 `\W` 。

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>通配符

句点 (`.`) 是正则表达式中的通配符。 它将匹配除换行 () 之外的任何字符 `\n` 。

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>空格

使用字符类匹配空白 `\s` 。 使用匹配的任何非空白字符 `\S` 。 `' '`还可以使用文本空格字符。

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>数量词

限定符控制输入字符串中应存在的每个元素的实例数。

下面是 PowerShell 中提供的几个限定符：

| 限定符 |                描述                |
| ---------- | ----------------------------------------- |
| `*`        | 零次或多次。                       |
| `+`        | 一次或多次。                        |
| `?`        | 零次或一次。                         |
| `{n,m}`    | 至少 `n` ，但不超过 `m` 次。 |

星号 (`*`) 匹配上一个元素零次或多次。 结果是，即使输入字符串没有元素也是匹配项。

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

加号 (`+`) 匹配上一个元素一次或多次。

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

问号 `?` 匹配上一个元素零次或一次。 与星号类似 `*` ，它甚至会匹配缺少元素的字符串。

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

`{n, m}`限定符可以使用多种不同的方式来允许对限定符进行精细控制。 第二个元素 `m` 和逗号 `,` 是可选的。

| 限定符 |                描述                 |
| ---------- | ------------------------------------------ |
| `{n}`      | 精确匹配 `n` 次数。         |
| `{n,}`     | 匹配至少 `n` 次。        |
| `{n,m}`    | 匹配 `n` 和 `m` 次数。 |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>定位点

定位点允许根据输入字符串中的匹配位置，使匹配成功或失败。

两个常用的定位点为 `^` 和 `$` 。 插入符号 `^` 与字符串的开头匹配，后者与 `$` 字符串的末尾匹配。 定位点允许您在特定位置匹配文本，同时还会丢弃不需要的字符。

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> 定义包含定位点的 regex 时 `$` ，请确保使用单引号将 regex 括起来 (`'`) 而不是双引号 (`"`) 或 PowerShell 将表达式扩展为变量。

在 PowerShell 中使用定位点时，应了解 **regexoptions.singleline** 和 **多行** 正则表达式选项之间的差异。

- **多** 行模式强制 `^` 并 `$` 匹配每行的开头，而不是输入字符串的开头和结尾。
- **Regexoptions.singleline**： regexoptions.singleline 模式将输入字符串视为 **regexoptions.singleline**。
  它强制 `.` 字符匹配每个字符 (包括换行符) ，而不是与除换行符之外的每个字符匹配 `\n` 。

若要了解有关这些选项以及如何使用这些选项的详细信息，请访问 [正则表达式语言-快速参考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

### <a name="escaping-characters"></a>转义字符

反斜杠 (`\`) 用于转义字符，因此正则表达式引擎不会对其进行分析。

保留以下字符： `[]().\^$|?*+{}` 。

需要对模式中的这些字符进行转义，使其与输入字符串中的字符匹配。

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

Regex 类的静态方法可为你转义文本。

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> 这会转义所有保留的正则表达式字符，包括字符类中使用的现有反斜杠。 请确保只在您需要转义的模式部分使用它。

#### <a name="other-character-escapes"></a>其他字符转义

还可以使用保留字符转义来匹配特殊字符类型。

下面是几个常用的字符转义：

|字符转义  |说明  |
|---------|---------|
|`\t`|匹配选项卡|
|`\n`|匹配换行符|
|`\r`|匹配回车符|

### <a name="groups-captures-and-substitutions"></a>组、捕获和替换

分组构造将输入字符串分隔为可捕获或忽略的子字符串。 分组的子字符串称为子字符串。 默认情况下，子表达式是在编号组中捕获的，但也可以为它们指定名称。

分组构造是括在括号中的正则表达式。 捕获由正则表达式匹配的任何文本。 下面的示例将输入文本分成两个捕获组。

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

使用 `$Matches` **哈希表** 自动变量检索捕获的文本。
表示整个匹配项的文本存储在键上 `0` 。

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

捕获以从左到右递增的数值 **整数** 键存储。 捕获 `1` 包含所有文本，直到用户名、捕获 `2` 只包含用户名。

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> `0`该键是一个 **整数**。 您可以使用任何 **哈希表** 方法来访问存储的值。
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a>命名捕获

默认情况下，捕获以升序从左到右的顺序存储。
你还可以为捕获组分配一个 **名称** 。 此 **名称** 将成为 `$Matches` **哈希表** 自动变量上的键。

在捕获组内，使用将 `?<keyname>` 捕获的数据存储在已命名的密钥下。

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

下面的示例在 Windows 安全日志中存储最新的日志条目。
提供的正则表达式从消息中提取用户名和域，并将其存储在 "名称" 下，将其存储在 "域名" 和 " **D** "。

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

有关详细信息，请参阅 [正则表达式中的分组构造](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)。

#### <a name="substitutions-in-regular-expressions"></a>正则表达式中的替代

将正则表达式与运算符一起使用， `-replace` 可以使用捕获的文本动态替换文本。

`<input> -replace <original>, <substitute>`

- `<input>`：要搜索的字符串
- `<original>`：用于搜索输入字符串的正则表达式
- `<substitute>`：用于替换输入字符串中找到的匹配项的正则表达式替换表达式。

> [!NOTE]
> `<original>`和 `<substitute>` 操作数服从正则表达式引擎（如字符转义）的规则。

捕获组可以在字符串中引用 `<substitute>` 。 通过使用 `$` 组标识符前面的字符来完成替换。

引用捕获组的两种方法是按 **编号** 和 **名称**。

- 按 **编号** 捕获组按从左到右的顺序进行编号。

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- 通过 **名称** ，也可以按名称引用捕获组。

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

`$&`表达式表示匹配的所有文本。

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> 由于 `$` 字符是在字符串扩展中使用的，因此您需要将字符串与替换一起使用，或者 `$` 在使用双引号时对字符进行转义。
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> 此外，如果你希望将 `$` 作为文本字符，请使用 `$$` 而不是常规转义字符。 使用双引号时，仍然会转义的所有实例， `$` 以避免不正确的替换。
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

有关详细信息，请参阅 [正则表达式中的替换](/dotnet/standard/base-types/substitutions-in-regular-expressions)。

## <a name="see-also"></a>请参阅

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)

