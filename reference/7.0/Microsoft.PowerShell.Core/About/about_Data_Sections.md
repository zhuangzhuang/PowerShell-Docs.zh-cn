---
description: 介绍数据部分，这些区域将文本字符串和其他只读数据与脚本逻辑隔离开来。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: b24ab9c47697ec62e1799784d4f0a3ae57351f2a
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879246"
---
# <a name="about-data-sections"></a>关于数据部分

## <a name="short-description"></a>简短说明
介绍数据部分，这些区域将文本字符串和其他只读数据与脚本逻辑隔离开来。

## <a name="long-description"></a>详细说明

为 PowerShell 设计的脚本可以包含一个或多个只包含数据的数据节。 可以在任何脚本、函数或高级函数中包含一个或多个数据节。 Data 部分的内容仅限于 PowerShell 脚本语言的指定子集。

通过将数据与代码逻辑分离，可以更轻松地标识和管理逻辑和数据。 它允许您为文本提供单独的字符串资源文件，例如错误消息和帮助字符串。 它还隔离了代码逻辑，从而促进了安全性和验证测试。

在 PowerShell 中，Data 部分用于支持脚本国际化。
您可以使用数据部分来更轻松地隔离、查找和处理转换为多个用户界面 (UI) 语言的字符串。

Data 部分是一项 PowerShell 2.0 功能。 如果脚本中包含数据节，则不会在没有修订版的 PowerShell 1.0 中运行。

### <a name="syntax"></a>语法

数据部分的语法如下所示：

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

Data 关键字是必需的。 此名称不区分大小写。 允许的内容仅限于以下元素：

- 所有 PowerShell 操作员，除外 `-match`
- `If`、 `Else` 和 `ElseIf` 语句
- 以下自动变量： `$PsCulture` 、 `$PsUICulture` 、 `$True` 、 `$False` 和 `$Null`
- 注释
- 管道
- 用分号分隔的语句 (`;`) 
- 文本，如下所示：

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

- 数据部分中允许的 cmdlet。 默认情况下，只 `ConvertFrom-StringData` 允许使用 cmdlet。
- 使用参数在数据部分中允许的 cmdlet `-SupportedCommand` 。

当你在 `ConvertFrom-StringData` Data 节中使用 cmdlet 时，可以将键/值对括在单个带引号的字符串或带双引号的字符串中，或者用单引号或双引号括起来。 但是，包含变量和子表达式的字符串必须用单引号括起来，或用单引号字符串括起来，这样就不会扩展变量，并且子表达式不能执行。

### <a name="-supportedcommand"></a>-SupportedCommand

`-SupportedCommand`参数用于指示 cmdlet 或函数仅生成数据。 它旨在允许用户在编写或测试的数据部分中包含 cmdlet 和函数。

的值 `-SupportedCommand` 是一个或多个 cmdlet 或函数名的逗号分隔列表。

例如，以下 data 节包含用户编写的 cmdlet， `Format-Xml` 用于设置 XML 文件中的数据的格式：

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>使用数据部分

若要使用 Data 节的内容，请将其分配给变量并使用变量表示法来访问内容。

例如，以下 data 节包含一个 `ConvertFrom-StringData` 命令，该命令将此处的字符串转换为哈希表。 将哈希表分配给该 `$TextMsgs` 变量。

`$TextMsgs`变量不是 data 节的一部分。

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

若要在中访问哈希表中的键和值 `$TextMsgs` ，请使用以下命令。

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

或者，您可以将变量名称放在数据节的定义中。 例如：

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

结果与前面的示例相同。

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>示例

简单的数据字符串。

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

包含允许的变量的字符串。

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

使用 cmdlet 的单引用字符串 `ConvertFrom-StringData` ：

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

使用 cmdlet 的一个用双引号引起来的字符串 `ConvertFrom-StringData` ：

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

一个数据部分，其中包含生成数据的用户编写的 cmdlet：

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>另请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
