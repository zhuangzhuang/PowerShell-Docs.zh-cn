---
description: 介绍如何在 PowerShell 中创建和使用函数。
Locale: en-US
ms.date: 02/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: d51c4d0bbf728bb23b4a5452d5192a262b722758
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595412"
---
# <a name="about-functions"></a>关于 Functions

## <a name="short-description"></a>简短说明

介绍如何在 PowerShell 中创建和使用函数。

## <a name="long-description"></a>长说明

函数是包含您分配的名称的 PowerShell 语句的列表。 运行函数时，请键入函数名称。 如果在命令提示符下键入语句，则列表中的语句将运行。

函数可以非常简单，如下所示：

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

函数也可以作为 cmdlet 或应用程序的复杂性。

与 cmdlet 一样，函数也可以具有参数。 参数可以是命名的、位置的、开关或动态参数。 函数参数可以从命令行或从管道中读取。

函数可以返回可以显示、赋给变量或传递给其他函数或 cmdlet 的值。 你还可以使用关键字指定返回值 `return` 。 `return`关键字不会影响或禁止从函数返回的其他输出。 不过， `return` 关键字将退出该函数。 有关详细信息，请参阅 [about_Return](about_Return.md)。

函数的语句列表可以包含具有关键字、和的不同类型的语句 `Begin` 列表 `Process` `End` 。 这些语句以不同方式列出管道中的处理输入。

筛选器是一种使用关键字的特殊函数 `Filter` 。

函数也可以像 cmdlet 一样操作。 你可以创建一个函数，该函数的工作方式与 cmdlet 相同，无需使用 `C#` 编程。 有关详细信息，请参阅 [about_Functions_Advanced](about_Functions_Advanced.md)。

## <a name="syntax"></a>语法

下面是函数的语法：

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

函数包含以下项：

- `Function`关键字
- 范围 (可选) 
- 你选择的名称
- 任意数量的命名参数 (可选) 
- 括在大括号中的一个或多个 PowerShell 命令 `{}`

有关 `Dynamicparam` 函数中关键字和动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

## <a name="simple-functions"></a>简单函数

函数不必太复杂，很有用。 最简单的函数具有以下格式：

```
function <function-name> {statements}
```

例如，以下函数通过 "以管理员身份运行" 选项启动 PowerShell。

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

若要使用函数，请键入： `Start-PSAdmin`

若要向函数添加语句，请在单独的行中键入每个语句，或使用分号 `;` 分隔这些语句。

例如，以下函数将查找在 `.jpg` 开始日期之后更改的当前用户目录中的所有文件。

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

您可以创建有用的小型函数的工具箱。 将这些函数添加到 PowerShell 配置文件，如本主题 [about_Profiles](about_Profiles.md) 和后面所述。

## <a name="function-names"></a>函数名称

可以为函数分配任何名称，但与其他人共享的函数应遵循为所有 PowerShell 命令建立的命名规则。

函数名称应包含动词-名词对，其中谓词标识函数执行的操作，名词标识该 cmdlet 执行其操作的项。

函数应使用已为所有 PowerShell 命令批准的标准谓词。 这些谓词可帮助我们使命令名称变得简单、一致和易于理解。

有关标准 PowerShell 谓词的详细信息，请参阅 Microsoft Docs 中的 [批准的动词](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 。

## <a name="functions-with-parameters"></a>带参数的函数

可以将参数用于函数，包括命名参数、位置参数、开关参数和动态参数。 有关函数中的动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="named-parameters"></a>命名的参数

可以定义任意数量的命名参数。 可以包含命名参数的默认值，如本主题后面所述。

可以使用关键字在大括号内定义参数 `Param` ，如下面的示例语法所示：

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

你还可以在不带关键字的大括号外定义参数 `Param` ，如下面的示例语法所示：

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

下面是此替代语法的示例。

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

尽管第一种方法是首选方法，但这两种方法之间没有区别。

运行函数时，为参数提供的值将分配给包含参数名的变量。 可在函数中使用该变量的值。

下面的示例是一个名为的函数 `Get-SmallFiles` 。 此函数有一个 `$Size` 参数。 函数显示小于参数值的所有文件 `$Size` ，并排除目录：

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

在函数中，可以使用 `$Size` 变量，该变量是为参数定义的名称。

若要使用此函数，请键入以下命令：

```powershell
Get-SmallFiles -Size 50
```

你还可以在没有参数名称的情况下为命名参数输入值。
例如，以下命令提供的结果与为 **Size** 参数命名的命令相同：

```powershell
Get-SmallFiles 50
```

若要定义参数的默认值，请在参数名称后面键入一个等号和值，如下面的示例中所示 `Get-SmallFiles` ：

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

如果键入的 `Get-SmallFiles` 值不包含任何值，则函数会将100赋给 `$size` 。 如果提供值，该函数将使用该值。

或者，您可以通过将 **PSDefaultValue** 特性添加到参数说明，并指定 **PSDefaultValue** 的 **help** 属性，来提供描述参数的默认值的简短帮助字符串。 若要提供描述函数中 **Size** 参数 (100) 默认值的帮助字符串 `Get-SmallFiles` ，请添加 **PSDefaultValue** 属性，如以下示例中所示。

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

有关 **PSDefaultValue** 特性类的详细信息，请参阅 [PSDefaultValue 特性成员](/dotnet/api/system.management.automation.psdefaultvalueattribute)。

### <a name="positional-parameters"></a>位置参数

位置参数是没有参数名称的参数。 PowerShell 使用参数值顺序将每个参数值与函数中的参数相关联。

使用位置参数时，请在函数名称后面键入一个或多个值。 位置参数值将分配给 `$args` 数组变量。
函数名称后面的值将分配给数组中的第一个位置 `$args` `$args[0]` 。

以下 `Get-Extension` 函数将 `.txt` 文件扩展名添加到提供的文件名：

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>开关参数

开关是不需要值的参数。 而是键入函数名称，后跟开关参数的名称。

若要定义开关参数，请在 `[switch]` 参数名称前面指定类型，如下面的示例中所示：

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

在 `On` 函数名后键入 switch 参数时，该函数将显示 "开关 on"。 如果没有开关参数，它将显示 "切换为关闭"。

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

你还可以在运行函数时向开关分配一个 **布尔** 值，如下面的示例中所示：

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>使用展开表示命令参数

可以使用展开来表示命令的参数。 此功能是在 Windows PowerShell 3.0 中引入的。

在调用会话中的命令的函数中使用此方法。 不需要声明或枚举命令参数，也不需要在命令参数更改时更改函数。

下面的示例函数调用 `Get-Command` cmdlet。 命令使用 `@Args` 来表示的参数 `Get-Command` 。

```powershell
function Get-MyCommand { Get-Command @Args }
```

调用函数时，可以使用的所有参数 `Get-Command` `Get-MyCommand` 。 参数和参数值使用传递到命令 `@Args` 。

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

此 `@Args` 功能使用 `$Args` 自动参数，该参数表示未声明的 cmdlet 参数和来自剩余参数的值。

有关展开的详细信息，请参阅 [about_Splatting](about_Splatting.md)。

## <a name="piping-objects-to-functions"></a>管道对象到函数

任何函数都可以从管道中获取输入。 您可以使用 `Begin` 、和关键字控制函数处理管道输入的方式 `Process` `End` 。 下面的语法示例显示了三个关键字：

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

`Begin`语句列表仅在函数的开始处运行一次。

> [!IMPORTANT]
> 如果函数定义了 `Begin` `Process` 或 `End` 块，则所有代码必须位于这些块内。 如果定义了任何块，则不会在块之外识别 *任何* 代码。

`Process`语句列表对管道中的每个对象运行一次。
当 `Process` 块正在运行时，每个管道对象将分配给 `$_` 自动变量，一次分配一个管道对象。

函数收到管道中的所有对象后， `End` 语句列表将运行一次。 如果未 `Begin` `Process` 使用、或 `End` 关键字，则将所有语句视为 `End` 语句列表。

下面的函数使用 `Process` 关键字。 函数显示管道中的示例：

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

若要演示此函数，请输入用逗号分隔的数字列表，如下面的示例中所示：

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

在管道中使用函数时，将向该函数传递的对象将分配给 `$input` 自动变量。 函数在任何对象来自管道之前，运行带有关键字的语句 `Begin` 。 函数在 `End` 从管道接收到所有对象之后，使用关键字运行语句。

下面的示例演示 `$input` 带有 and 关键字的自动变量 `Begin` `End` 。

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

如果使用管道运行此函数，则将显示以下结果：

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

当 `Begin` 语句运行时，该函数不具有管道的输入。 `End`语句在函数具有值后运行。

如果函数具有 `Process` 关键字，则中的每个对象 `$input` 都将从中移除 `$input` 并被分配给 `$_` 。 下面的示例包含一个 `Process` 语句列表：

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

在此示例中，向函数发出管道的每个对象都发送到 `Process` 语句列表。 `Process`语句在每个对象上运行（一次一个对象）。 `$input`当函数到达关键字时，自动变量为空 `End` 。

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

有关详细信息，请参阅[使用枚举](about_Automatic_Variables.md#using-enumerators)器

## <a name="filters"></a>筛选器

筛选器是在管道中的每个对象上运行的函数类型。 筛选器类似于函数，其中的所有语句都位于 `Process` 块中。

筛选器的语法如下所示：

```
filter [<scope:>]<name> {<statement list>}
```

以下筛选器从管道中获取日志条目，然后显示整个条目或仅显示条目的消息部分：

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>函数范围

函数存在于创建它的作用域中。

如果函数是脚本的一部分，则该函数可用于该脚本中的语句。 默认情况下，在命令提示符下不能使用脚本中的函数。

可以指定函数的作用域。 例如，在以下示例中，将函数添加到全局范围：

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

当函数在全局范围中时，可以在脚本中、在函数中使用函数，并在命令行中使用函数。

函数通常会创建一个作用域。 在函数中创建的项（如变量）仅存在于函数作用域中。

有关 PowerShell 中的作用域的详细信息，请参阅 [about_Scopes](about_Scopes.md)。

## <a name="finding-and-managing-functions-using-the-function-drive"></a>使用函数查找和管理函数：驱动器

PowerShell 中的所有函数和筛选器都将自动存储在 `Function:` 驱动器中。 此驱动器由 PowerShell **函数** 提供程序公开。

在引用驱动器时 `Function:` ，请在 **函数** 后面键入一个冒号，就像引用计算机的或驱动器时所做的那样 `C` `D` 。

以下命令显示 PowerShell 的当前会话中的所有函数：

```powershell
Get-ChildItem function:
```

函数中的命令以脚本块的形式存储在函数的定义属性中。 例如，若要显示 PowerShell 附带的帮助函数中的命令，请键入：

```powershell
(Get-ChildItem function:help).Definition
```

你还可以使用以下语法。

```powershell
$function:help
```

有关驱动器的详细信息 `Function:` ，请参阅 **函数** 提供程序的帮助主题。 键入 `Get-Help Function`。

## <a name="reusing-functions-in-new-sessions"></a>在新会话中重用函数

在 PowerShell 命令提示符下键入函数时，该函数将成为当前会话的一部分。 直到会话结束时，此功能才可用。

若要在所有 PowerShell 会话中使用函数，请将函数添加到 PowerShell 配置文件。 有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

你还可以将函数保存在 PowerShell 脚本文件中。 在文本文件中键入函数，然后使用文件扩展名保存该文件 `.ps1` 。

## <a name="writing-help-for-functions"></a>编写函数的帮助

`Get-Help`Cmdlet 可获取有关函数以及 cmdlet、提供程序和脚本的帮助。 若要获取有关函数的帮助，请键入 `Get-Help` 后跟函数名称。

例如，若要获取有关该函数的帮助 `Get-MyDisks` ，请键入：

```powershell
Get-Help Get-MyDisks
```

您可以使用以下两种方法之一来编写函数的帮助：

- 函数 Comment-Based 帮助

  在注释中使用特殊关键字创建帮助主题。 若要为函数创建基于注释的帮助，注释必须位于函数体的开头或末尾，或者位于 function 关键字之前的行中。 有关基于注释的帮助的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。

- 函数 XML-Based 帮助

  创建基于 XML 的帮助主题，如通常为 cmdlet 创建的类型。 如果要将帮助主题本地化为多种语言，则必须提供基于 XML 的帮助。

  若要将函数与基于 XML 的帮助主题相关联，请使用 `.ExternalHelp` 基于注释的帮助关键字。 如果没有此关键字，则找 `Get-Help` 不到函数帮助主题，并且对的调用将 `Get-Help` 仅返回自动生成的帮助。

  有关关键字的详细信息 `ExternalHelp` ，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。 有关基于 XML 的帮助的详细信息，请参阅 [如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。

## <a name="see-also"></a>请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)
