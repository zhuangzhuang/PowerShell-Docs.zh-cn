---
description: 说明如何使用 Split 运算符将一个或多个字符串拆分为子字符串。
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: c7944c710ae3b6803772de77f50b639de4953340
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598494"
---
# <a name="about-split"></a>关于 Split

## <a name="short-description"></a>简短说明
说明如何使用 Split 运算符将一个或多个字符串拆分为子字符串。

## <a name="long-description"></a>详细说明

Split 运算符将一个或多个字符串拆分为子字符串。 您可以更改 Split 操作的以下元素：

- 后面. 默认值为空格，但您可以指定字符、字符串、模式或指定分隔符的脚本块。 PowerShell 中的 Split 运算符使用分隔符中的正则表达式，而不是简单字符。
- 子字符串的最大数目。 默认值为返回所有子字符串。 如果指定的数字小于子字符串的数目，则剩余的子字符串将连接到最后一个子字符串。
- 用于指定匹配分隔符的条件的选项，如 SimpleMatch 和多行。

## <a name="syntax"></a>SYNTAX

下图显示了-split 运算符的语法。

参数名称不会出现在命令中。 仅包括参数值。 值必须以语法关系图中指定的顺序出现。

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

可以 `-iSplit` `-cSplit` `-split` 在任何二进制 split 语句中替换或， (包含分隔符或脚本块的 Split 语句) 。 `-iSplit`和 `-split` 运算符不区分大小写。 `-cSplit`运算符区分大小写，这意味着在应用分隔符规则时将考虑大小写。

## <a name="parameters"></a>PARAMETERS

### <a name="string-or-string"></a>\<String\> 或 \<String[]\>

指定一个或多个要拆分的字符串。 如果提交多个字符串，则所有字符串都将使用相同的分隔符规则进行拆分。

例如：

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

标识子字符串末尾的字符。 默认分隔符为空白，包括空格和不可打印的字符，如换行符 (\` n) 和制表符 (\` t) 。 拆分字符串后，将从所有子字符串中省略分隔符。 例如：

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

默认情况下，结果中省略了分隔符。 若要保留全部或部分分隔符，请将要保留的部分括在括号中。
如果 \<Max-substrings\> 添加了参数，则当命令拆分集合时，此参数将优先。 如果选择将分隔符作为输出的一部分包含，则该命令会将分隔符作为输出的一部分返回;但是，如果将字符串拆分为作为输出的一部分返回，则不计为拆分。

示例:

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

在下面的示例中， \<Max-substrings\> 设置为3。 这会生成三个字符串值的拆分，但生成的输出中总共有5个字符串;分隔符包含在拆分后，直到达到三个子字符串的最大值。 最后一个子字符串中的其他分隔符将成为子字符串的一部分。

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

指定一个字符串被拆分的最大次数。 默认值为所有子字符串除以分隔符。 如果有多个子字符串，则它们将连接到最后一个子字符串。 如果子字符串较少，则返回所有子字符串。 值0返回所有子字符串。 负值返回从输入字符串末尾开始请求的子字符串量。

> [!NOTE]
> PowerShell 7 中添加了对负值的支持。

**Max-子字符串** 未指定返回的最大对象数。 其值等于拆分字符串的最大次数。
如果将多个字符串 (一个字符串数组提交) 到 `-split` 运算符，则 **最大子** 字符串限制将分别应用于每个字符串。

例如：

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

一个表达式，指定用于应用分隔符的规则。 表达式的计算结果必须为 $true 或 $false。 将脚本块括在大括号中。

例如：

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

将选项名称用引号引起来。 仅当在 \<Max-substrings\> 语句中使用参数时，这些选项才有效。

Options 参数的语法为：

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

SimpleMatch 选项包括：

- **SimpleMatch**：计算分隔符时使用简单的字符串比较。 不能与 RegexMatch 一起使用。
- **Regexoptions.ignorecase**：强制不区分大小写的匹配，即使指定了-cSplit 运算符。

RegexMatch 选项包括：

- **RegexMatch**：使用正则表达式匹配计算分隔符。 这是默认行为。 不能与 SimpleMatch 一起使用。
- **Regexoptions.ignorecase**：强制不区分大小写的匹配，即使指定了-cSplit 运算符。
- **Regexoptions.cultureinvariant**：用来评估分隔符时忽略语言中的区域性差异。 仅对 RegexMatch 有效。
- **IgnorePatternWhitespace**：忽略用数字符号标记的非转义空格和注释 ( # ) 。 仅对 RegexMatch 有效。
- **多** 行模式强制 `^` 并 `$` 匹配每行的开头，而不是输入字符串的开头和结尾。
- **Regexoptions.singleline**： regexoptions.singleline 模式将输入字符串视为 *regexoptions.singleline*。
  它强制 `.` 字符匹配每个字符 (包括换行符) ，而不是与除换行符之外的每个字符匹配 `\n` 。
- **Regexoptions.explicitcapture**：忽略不命名的匹配组，以便仅在结果列表中返回显式捕获组。 仅对 RegexMatch 有效。

## <a name="unary-and-binary-split-operators"></a>一元和二元拆分运算符

一元 split 运算符 (`-split <string>`) 的优先级高于逗号。 因此，如果您将逗号分隔的字符串列表提交给一元 split 运算符，则在第一个逗号) 之前仅 (第一个字符串被拆分。

使用下列模式之一拆分多个字符串：

- 使用二进制拆分运算符 (\<string[]\> 拆分 \<delimiter\>) 
- 将所有字符串括在括号中
- 将字符串存储在变量中，然后将变量提交给 split 运算符

请看下面的示例：

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>示例

下面的语句在空格处拆分字符串。

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

以下语句以任意逗号拆分字符串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

下面的语句以 "er" 模式拆分字符串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

以下语句执行区分大小写的字母 "N"。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

下面的语句在 "e" 和 "t" 处拆分字符串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

下面的语句在 "e" 和 "r" 处拆分字符串，但将生成的子字符串限制为六个子字符串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

下面的语句将字符串拆分为三个子字符串。

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

下面的语句将字符串拆分为从字符串末尾开始的三个子字符串。

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

下面的语句将两个字符串拆分为三个子字符串。
 (此限制分别应用于每个字符串。 ) 

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

下面的语句在第一个数字处拆分了此处字符串中的每一行。 它使用多行选项来识别每个行和字符串的开头。

0表示 Max 子字符串参数的 "返回所有" 值。 仅当指定了 Max 子字符串值时，才可以使用诸如多行的选项。

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

以下语句使用反斜杠字符来转义 ( ) 分隔符。

默认值为 RegexMatch，用引号引起来的点 ( "。) 被解释为匹配除换行符外的任何字符。 因此，Split 语句为除换行符之外的每个字符返回一个空行。

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

下面的语句使用 SimpleMatch 选项来指示-split 运算符解释点 (。 ) 分隔符。

0表示 Max 子字符串参数的 "返回所有" 值。 仅当指定了 Max 子字符串值时，才能使用 SimpleMatch 等选项。

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

下面的语句根据变量的值，将字符串拆分为两个分隔符之一。

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>另请参阅

[Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Join](about_Join.md)

