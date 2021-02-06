---
description: 描述变量如何存储可在 PowerShell 中使用的值。
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 8d8c8d3098d33980c9c802bf00846a21e8baeb40
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596415"
---
# <a name="about-variables"></a>关于变量

## <a name="short-description"></a>简短说明

描述变量如何存储可在 PowerShell 中使用的值。

## <a name="long-description"></a>长说明

可以在 PowerShell 变量中存储所有类型的值。 例如，存储命令的结果，并存储命令和表达式中使用的元素，例如名称、路径、设置和值。

变量是存储值的内存单位。 在 PowerShell 中，变量由以美元符号开头的文本字符串表示 (`$`) ，如 `$a` 、 `$process` 或 `$my_var` 。

变量名称不区分大小写，并且可以包含空格和特殊字符。 但是，包含特殊字符和空格的变量名称难以使用，应避免使用。 有关详细信息，请参阅 [包含特殊字符的变量名称](#variable-names-that-include-special-characters)。

在 PowerShell 中有几种不同类型的变量。

- 用户创建的变量：用户创建的变量由用户创建和维护。 默认情况下，在 powershell 命令行中创建的变量仅在 PowerShell 窗口处于打开状态时才存在。 当 PowerShell 窗口关闭时，这些变量将被删除。 若要保存某个变量，请将其添加到 PowerShell 配置文件中。 你还可以在具有全局、脚本或本地范围的脚本中创建变量。

- 自动变量：自动变量存储 PowerShell 的状态。 这些变量由 PowerShell 创建，PowerShell 会根据需要更改它们的值以保持其准确性。 用户不能更改这些变量的值。 例如， `$PSHOME` 变量存储 PowerShell 安装目录的路径。

  有关自动变量的详细信息、列表和说明，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

- 首选项变量：首选项为 PowerShell 存储用户首选项。 这些变量由 PowerShell 创建，并使用默认值进行填充。 用户可以更改这些变量的值。 例如， `$MaximumHistoryCount` 变量确定会话历史记录中的最大项数。

  有关首选项变量的详细信息、列表和说明，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

## <a name="working-with-variables"></a>使用变量

若要创建新变量，请使用赋值语句为变量赋值。 不需要在使用变量之前先对其进行声明。 所有变量的默认值为 `$null` 。

若要获取 PowerShell 会话中所有变量的列表，请键入 `Get-Variable` 。 将显示变量名称，其中不含前面的货币 (`$` 用于引用变量的) 符号。

例如：

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

变量用于存储命令的结果。

例如：

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

若要显示变量的值，请键入变量名称，其前面带有美元符号 (`$`) 。

例如：

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

若要更改变量的值，请将新值分配给该变量。

下面的示例显示变量的值 `$MyVariable` ，更改变量的值，然后显示新值。

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

若要删除变量的值，请使用 `Clear-Variable` cmdlet 或将值更改为 `$null` 。

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

若要删除变量，请使用 " [删除变量](xref:Microsoft.PowerShell.Utility.Remove-Variable) " 或 " [删除项](xref:Microsoft.PowerShell.Management.Remove-Item)"。

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>变量类型

可以在变量中存储任何类型的对象，包括整数、字符串、数组和哈希表。 和表示进程、服务、事件日志和计算机的对象。

PowerShell 变量是松散类型化的，这意味着它们并不限于特定类型的对象。 单个变量甚至可以同时包含不同类型的对象的集合或数组。

变量的数据类型由变量值的 .NET 类型决定。 若要查看变量的对象类型，请使用 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member)。

例如：

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

您可以使用类型属性和强制转换表示法来确保变量只能包含特定的对象类型或可转换为该类型的对象。 如果尝试分配另一个类型的值，则 PowerShell 会尝试将值转换为其类型。 如果无法转换类型，赋值语句将失败。

若要使用强制转换表示法，请在赋值语句左侧)  (的变量名称之前输入类型名称（括在括号中）。 下面的示例创建一个 `$number` 变量，该变量只能包含整数、只能包含字符串的变量 `$words` ，以及只能 `$dates` 包含 **DateTime** 对象的变量。

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>在命令和表达式中使用变量

若要在命令或表达式中使用变量，请键入变量名称，前面加上美元 (`$`) 符号。

如果变量名和美元符号没有用引号引起来，或者它们括在双引号 (`"`) 标记中，则在命令或表达式中使用该变量的值。

如果变量名和美元符号用单引号引起 (`'`) 标记，则在表达式中使用变量名。

有关在 PowerShell 中使用引号的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。

此示例获取变量的值 `$PROFILE` ，它是 powershell 控制台中 powershell 用户配置文件的路径。

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

在此示例中，显示了两个命令，可在 **notepad.exe** 中打开 PowerShell 配置文件。 带有双引号 () 标记的示例 `"` 使用变量的值。

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

下面的示例使用单引号 (将 `'` 变量视为文本的) 标记。

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>包含特殊字符的变量名称

变量名称以美元 (`$`) 符号开头，可以包含字母数字字符和特殊字符。 变量名称长度仅受可用内存的限制。

最佳做法是，变量名称只能包含字母数字字符和下划线 (`_`) 字符。 包含空格和其他特殊字符的变量名称难以使用，应避免使用。

字母数字变量名可以包含以下字符：

- 这些类别中的 Unicode 字符： **Lu**、 **Ll**、 **Lt**、 **Lm**、 **Lo** 或 **Nd**。
- 下划线 (`_`) 字符。
- 问号 (`?`) 字符。

下面的列表包含 Unicode 类别说明。 有关详细信息，请参阅 [system.globalization.unicodecategory](/dotnet/api/system.globalization.unicodecategory)。

- **Lu** -UppercaseLetter
- **Ll** -LowercaseLetter
- **Lt** -TitlecaseLetter
- **Lm** -ModifierLetter
- **Lo** -OtherLetter
- **Nd** -DecimalDigitNumber

若要创建或显示包含空格或特殊字符的变量名称，请使用大括号将该变量名称括 (`{}`) 字符。
大括号直接 PowerShell 将变量名称的字符解释为文本。

特殊字符变量名称可以包含以下字符：

- 任何 Unicode 字符，但以下情况除外：
  - 右大括号 (`}`) 字符 (U + 007D) 。
  - 反撇号 (`` ` ``) 字符 (U + 0060) 。 反撇号用于对 Unicode 字符进行转义，以使它们被视为文本。

PowerShell 包含 `$$` `$?` `$^` `$_` 包含字母数字字符和特殊字符的保留变量，如、、和。 有关详细信息，请参阅 [about_Automatic_Variables](about_automatic_variables.md)。

例如，以下命令将创建名为的变量 `save-items` 。 需要大括号 (`{}`) ，因为变量名称包含连字符 (`-`) 特殊字符。

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

以下命令将获取由环境变量表示的目录中的子项目 `ProgramFiles(x86)` 。

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

若要引用包含大括号的变量名，请将变量名称括在大括号中，并使用反撇号字符来转义大括号。 例如，若要创建名为 type 的变量 `this{value}is` ：

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>变量和范围

默认情况下，变量仅在创建它们的范围内可用。

例如，在函数中创建的变量仅在函数内可用。 在脚本中创建的变量仅在脚本内可用。 如果脚本为点，则将变量添加到当前作用域。 有关详细信息，请参阅 [about_Scopes](about_Scopes.md)。

您可以使用作用域修饰符来更改变量的默认作用域。 下面的表达式创建一个名为的变量 `Computers` 。 尽管变量是在脚本或函数中创建的，但它也具有全局作用域。

```powershell
$Global:Computers = "Server01"
```

对于任何执行进程外的脚本或命令，都需要 `Using` 范围修饰符来嵌入调用会话范围内的变量值，以便使会话代码不能访问它们。

有关详细信息，请参阅 [about_Remote_Variables](about_Remote_Variables.md)。

## <a name="saving-variables"></a>保存变量

你创建的变量仅在创建它们的会话中可用。 关闭会话时，它们会丢失。

若要在启动的每个 PowerShell 会话中创建变量，请将变量添加到 PowerShell 配置文件。

例如，若要 `$VerbosePreference` 在每个 powershell 会话中更改变量的值，请将以下命令添加到 powershell 配置文件中。

```powershell
$VerbosePreference = "Continue"
```

可以通过 `$PROFILE` 在文本编辑器中打开文件（如 **notepad.exe**），将此命令添加到 PowerShell 配置文件。 有关 PowerShell 配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

## <a name="the-variable-drive"></a>变量：驱动器

PowerShell 变量提供程序创建的 `Variable:` 驱动器的外观和行为类似于文件系统驱动器，但它包含会话中的变量及其值。

若要切换到 `Variable:` 驱动器，请使用以下命令：

```powershell
Set-Location Variable:
```

若要列出驱动器中的项和变量 `Variable:` ，请使用 `Get-Item` 或 `Get-ChildItem` cmdlet。

```powershell
Get-ChildItem Variable:
```

若要获取特定变量的值，请使用文件系统表示法指定驱动器名称和变量名称。 例如，若要获取 `$PSCulture` 自动变量，请使用以下命令。

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

若要显示有关 `Variable:` 驱动器和 PowerShell Variable 提供程序的详细信息，请键入：

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>具有提供程序路径的变量语法

你可以为提供程序路径加上前缀 (`$`) 符号，并访问实现 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 接口的任何提供程序的内容。

以下内置 PowerShell 提供程序支持此表示法：

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>变量 cmdlet

PowerShell 包括一组旨在管理变量的 cmdlet。

若要列出这些 cmdlet，请键入：

```powershell
Get-Command -Noun Variable
```

若要获取特定 cmdlet 的帮助，请键入：

```powershell
Get-Help <cmdlet-name>
```

| Cmdlet 名称       | 说明                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | 删除变量的值。           |
| `Get-Variable`    | 获取当前控制台中的变量。 |
| `New-Variable`    | 创建新变量。                    |
| `Remove-Variable` | 删除变量及其值。          |
| `Set-Variable`    | 更改变量的值。           |

## <a name="see-also"></a>请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)

