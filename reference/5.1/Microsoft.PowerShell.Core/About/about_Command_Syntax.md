---
description: 描述在 PowerShell 中使用的语法关系图。
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: ff7a243a584ee336c0356200f5ba68fde55e0836
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194621"
---
# <a name="about-command-syntax"></a>关于命令语法

## <a name="short-description"></a>简短说明

描述在 PowerShell 中使用的语法关系图。

## <a name="long-description"></a>详细说明

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help)和[get-help](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet 显示语法关系图，有助于正确构造命令。 本主题说明如何解释语法关系图。

## <a name="syntax-diagrams"></a>语法关系图

命令语法关系图中的每个段落均表示命令的有效格式。

若要构造命令，请从左到右跟踪语法关系图。 从可选参数中选择，并提供占位符的值。

对于语法关系图，PowerShell 使用以下表示法。

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

下面是 [新别名](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet 的语法。

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

语法为可读性，但 PowerShell 不区分大小写。

语法关系图包含以下元素。

## <a name="command-name"></a>命令名称

命令始终以命令名称开头，例如 `New-Alias` 。 键入命令名称或其别名，如的 "gcm" `Get-Command` 。

## <a name="parameters"></a>Parameters

命令的参数是确定命令用途的选项。
某些参数采用一个 "值"，它是命令的用户输入。

例如，该 `Get-Help` 命令有一个 **name** 参数，可让你指定显示帮助的主题的名称。 主题名称是 **name** 参数的值。

在 PowerShell 命令中，参数名称始终以连字符开头。
连字符告诉 PowerShell：命令中的项是参数名称。

例如，若要使用的 Name 参数 `New-Alias` ，请键入以下内容：

```powershell
-Name
```

参数可以是必需的或可选的。 在语法关系图中，可选项括在括号中 `[ ]` 。

有关参数的详细信息，请参阅 [about_Parameters](about_Parameters.md)。

## <a name="parameter-values"></a>参数值

参数值是参数所采用的输入。 由于 Windows PowerShell 基于 Microsoft .NET 框架，因此参数值按其 .NET 类型在语法关系图中表示。

例如，的名称参数 `Get-Help` 采用 "String" 值，这是一个文本字符串，如一个词或用引号引起来的多个单词。

```powershell
[-Name] <string>
```

参数值的 .NET 类型括在尖括号中， `< >` 以指示它是值的占位符，而不是在命令中键入的文本的占位符。

若要使用参数，请将 .NET 类型占位符替换为具有指定 .NET 类型的对象。

例如，若要使用 **Name** 参数，请键入 "-Name" 后跟一个字符串，如下所示：

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>无值的参数

有些参数不接受输入，因此它们没有参数值。
不带值的参数称为 "开关参数"，因为它们的工作方式类似于打开/关闭开关。 你将它们包含在) 中 (或者将其从命令 (关闭) 。

若要使用开关参数，只需键入参数名称（前面带有连字符）。

例如，若要使用 cmdlet 的 **WhatIf** 参数 `New-Alias` ，请键入以下内容：

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>参数集

命令的参数在 "参数集" 中列出。 参数集类似于语法关系图的段落。

`New-Alias`Cmdlet 设置了一个参数，但许多 cmdlet 具有多个参数集。 某些 cmdlet 参数对于参数集是唯一的，而其他参数则出现在多个参数集内。 每个参数集都表示有效命令的格式。 参数集仅包含可在命令中一起使用的参数。 如果不能在同一命令中使用参数，则它们将显示在单独的参数集内。

例如， [获取随机](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet 具有以下参数集：

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

返回一个随机数的第一个参数集具有 **最小** 和 **最大** 参数。 第二个参数集返回一组对象中随机选择的对象，其中包括 **InputObject** 和 **Count** 参数。 这两个参数集都具有 **SetSeed** 参数和通用参数。

这些参数集指示你可以在同一命令中使用 **InputObject** 和 **count** 参数，但不能在同一命令中使用 **最大值** 和 **计数** 参数。

您可以通过使用该参数集中的参数来指示要使用的参数集。

但是，每个 cmdlet 还具有一个默认参数集。 如果未指定参数集独有的参数，则使用默认参数集。 例如，如果使用 `Get-Random` 不带参数的，则 Windows PowerShell 假设你使用的是 **数字** 参数集，并且它将返回一个随机数字。

在每个参数集中，参数按位置顺序显示。 仅当省略可选参数名称时，命令中的参数顺序才有意义。 省略参数名称时，PowerShell 会按位置和类型将值分配给参数。 有关参数位置的详细信息，请参阅 `about_Parameters` 。

## <a name="symbols-in-syntax-diagrams"></a>语法关系图中的符号

语法关系图列出了命令名称、命令参数和参数值。 它还使用符号说明如何构造有效的命令。

语法关系图使用以下符号：

- 连字符 `-` 表示参数名称。 在命令中，在参数名称前面直接键入连字符，不包含空格，如语法关系图中所示。

  例如，若要使用的 **Name** 参数 `New-Alias` ，请键入：

  ```powershell
  -Name
  ```

- 尖括号 `<>` 表示占位符文本。 不在命令中键入尖括号或占位符文本。 而是将其替换为它所描述的项。

  尖括号用于标识参数所采用的值的 .NET 类型。 例如，若要使用 cmdlet 的 **Name** 参数，请将 `New-Alias` 替换为 `<string>` 字符串，该字符串是一个单词或用引号引起来的一组单词。

- 方括号 `[ ]` 表示可选项。 参数及其值可以是可选的，或者必需参数的名称可以是可选的。

  例如，的 **Description** 参数 `New-Alias` 及其值括在括号中，因为它们都是可选的。

  ```powershell
  [-Description <string>]
  ```

  方括号还指示 Name 参数值 `<string>` 是必需的，但参数名称 "name" 是可选的。

  ```powershell
  [-Name] <string>
  ```

- 追加到 .NET 类型的右括号和左括号 `[]` 指示参数可以接受该类型的一个或多个值。 以逗号分隔的列表形式输入值。

  例如，cmdlet 的 **name** 参数 `New-Alias` 仅采用一个字符串，但 [获取进程](xref:Microsoft.PowerShell.Management.Get-Process)的 **name** 参数可以采用一个或多个字符串。

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- 大括号 `{}` 指示一个 "枚举"，它是参数的有效值集。

  大括号中的值由竖线分隔 `|` 。 这些条形表示 "专用" 或 "选择"，这意味着只能从大括号内列出的一组值中选择一个值。

  例如，cmdlet 的语法 `New-Alias` 包括 **选项** 参数的以下值枚举：

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  大括号和竖线指示你可以为 **选项** 参数选择列出的任何一个值，例如 "ReadOnly" 或 "AllScope"。

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>可选项

方括号将 `[]` 可选项括起来。 例如，在 `New-Alias` cmdlet 语法说明中， **Scope** 参数是可选的。 在语法中，参数名称和类型的两侧括在语法中：

```powershell
[-Scope <string>]
```

以下两个示例都是 cmdlet 的正确用法 `New-Alias` ：

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

即使参数的值是必需的，参数名称也可以是可选的。 在语法中，参数名称两边的括号中指出了这一点，而不是参数类型，如以下 cmdlet 所示 `New-Alias` ：

```powershell
[-Name] <string> [-Value] <string>
```

以下命令正确使用 `New-Alias` cmdlet。 这些命令产生的结果相同。

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

如果在语句中不包含参数名，则 Windows PowerShell 将尝试使用参数的位置将这些值分配给参数。

以下示例不完整：

```powershell
New-Alias utd
```

此 cmdlet 需要 **Name** 和 **Value** 参数的值。

在语法示例中，括号还用于命名和强制转换为 .NET Framework 类型。 在此上下文中，方括号不指示元素是可选的。

## <a name="see-also"></a>另请参阅

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)
