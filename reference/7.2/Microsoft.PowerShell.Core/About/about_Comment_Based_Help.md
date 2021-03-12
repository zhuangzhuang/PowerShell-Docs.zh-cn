---
description: 介绍如何为函数和脚本编写基于注释的帮助主题。
Locale: en-US
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: b676870c5d8879700b84339f9f0b74a18b079692
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195718"
---
# <a name="about-comment-based-help"></a>关于基于注释的帮助

## <a name="short-description"></a>简短说明
介绍如何为函数和脚本编写基于注释的帮助主题。

## <a name="long-description"></a>长说明

您可以使用特殊的帮助注释关键字为函数和脚本编写基于注释的帮助主题。

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet 显示基于注释的帮助，其格式与用于显示 XML 文件中生成的 cmdlet 帮助主题的格式相同。 用户可以使用的所有参数 `Get-Help` ，如 **详细**、 **完整**、 **示例** 和 **联机**，以显示基于注释的帮助的内容。

还可以为函数和脚本编写基于 XML 的帮助文件。 若要使 `Get-Help` cmdlet 能够查找函数或脚本的基于 XML 的帮助文件，请使用 `.ExternalHelp` 关键字。 如果没有此关键字，则 `Get-Help` 无法找到函数或脚本的基于 XML 的帮助主题。

本主题说明如何编写函数和脚本的帮助主题。 有关如何显示有关函数和脚本的帮助主题的信息，请参阅 [get-help](xref:Microsoft.PowerShell.Core.Get-Help)。

[Update-help](xref:Microsoft.PowerShell.Core.Update-Help)和[get-help](xref:Microsoft.PowerShell.Core.Save-Help) CMDLET 仅适用于 XML 文件。 可更新的帮助不支持基于注释的帮助主题。

## <a name="syntax-for-comment-based-help"></a>基于注释的帮助的语法

基于注释的帮助的语法如下所示：

```
# .<help keyword>
# <help content>
```

or

```
<#
.<help keyword>
<help content>
#>
```

基于注释的帮助以一系列注释形式编写。 你可以 `#` 在每个注释行之前键入注释符号，也可以使用 `<#` 和 `#>` 符号来创建注释块。 注释块内的所有行都解释为注释。

基于注释的帮助主题中的所有行都必须是连续的。 如果基于注释的帮助主题遵循的注释不是帮助主题的一部分，则最后一个非帮助注释行与基于注释的帮助的开头之间必须至少有一个空白行。

关键字定义基于注释的帮助的每个部分。 每个基于注释的帮助关键字之前都带有一个点 `.` 。 关键字可以按任意顺序出现。 关键字名称不区分大小写。

例如，关键字在 `.Description` 函数或脚本的说明之前。

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

注释块必须包含至少一个关键字。 某些关键字（如 `.EXAMPLE` ）可以在同一注释块中出现多次。 每个关键字的帮助内容都从关键字后面的行开始，可以跨多行。

## <a name="syntax-for-comment-based-help-in-functions"></a>函数中基于注释的帮助的语法

函数的基于注释的帮助可能出现在以下三个位置之一：

- 函数体的开头。
- 函数体的末尾。
- 关键字之前 `function` 。 函数的最后一行与关键字之间不能有多个空行 `function` 。

例如：

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

或

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

或

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>脚本中基于注释的帮助的语法

脚本的基于注释的帮助可以显示在脚本中的以下两个位置之一。

- 位于脚本文件的开头。 脚本帮助的前面只能是注释和空行。

  如果在 "帮助") 后 (脚本正文中的第一项是函数声明，则脚本的末尾和函数声明之间必须至少有两个空行。 否则，"帮助" 将被解释为该函数的帮助，而不是脚本的帮助。

- 脚本文件末尾。 但是，如果对脚本进行了签名，请在脚本文件的开头放置基于注释的帮助。 脚本的末尾由签名块占用。

例如：

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

或

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>脚本模块中基于注释的帮助的语法

在脚本模块中 `.psm1` ，基于注释的帮助使用函数的语法，而不是脚本的语法。 不能使用脚本语法为脚本模块中定义的所有函数提供帮助。

例如，如果要使用 `.ExternalHelp` 关键字来标识脚本模块中函数的基于 XML 的帮助文件，则必须向 `.ExternalHelp` 每个函数添加注释。

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>基于注释的帮助关键字

下面是有效的基于注释的帮助关键字。 它们按其在帮助主题中通常出现的顺序列出，以及它们的预期用途。 这些关键字可以在基于注释的帮助中以任意顺序出现，它们不区分大小写。

### <a name="synopsis"></a>.概要

函数或脚本的简短说明。 每个主题中只能使用一次此关键字。

### <a name="description"></a>.2008

函数或脚本的详细说明。 每个主题中只能使用一次此关键字。

### <a name="parameter"></a>.参数

参数的说明。 `.PARAMETER`在函数或脚本语法中为每个参数添加关键字。

键入与关键字相同的行中的参数名称 `.PARAMETER` 。 在关键字后面的行上键入参数说明 `.PARAMETER` 。 Windows PowerShell 会将 `.PARAMETER` 行和下一关键字之间的所有文本解释为参数说明的一部分。
说明可以包括分段符。

```
.PARAMETER  <Parameter-Name>
```

参数关键字可以在注释块中以任意顺序出现，但是函数或脚本语法将确定参数 (的顺序及其说明) 出现在帮助主题中。 若要更改顺序，请更改语法。

还可以指定参数说明，方法是将注释放在函数或脚本语法中紧靠在参数变量名称之前。 为此，您还必须具有至少一个关键字的注释块。

如果同时使用语法注释和 `.PARAMETER` 关键字，则使用与关键字关联的说明 `.PARAMETER` ，并忽略语法注释。

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>.实例

使用函数或脚本的示例命令，可选择后跟示例输出和说明。 为每个示例重复此关键字。

### <a name="inputs"></a>.输入

可以通过管道传递给函数或脚本的 .NET 类型的对象。 还可以包括对输入对象的描述。

### <a name="outputs"></a>.输出

Cmdlet 返回的对象的 .NET 类型。 还可以包括返回对象的描述。

### <a name="notes"></a>.本票

有关函数或脚本的其他信息。

### <a name="link"></a>.连接

相关主题的名称。 该值将显示在 "" 下的行中。LINK "关键字和前面必须是注释符号 `#` 或包含在注释块中。

`.LINK`对每个相关主题重复关键字。

此内容显示在帮助主题的 "相关链接" 部分中。

`.Link`关键字内容还可以包含统一资源标识符 (URI) 到同一帮助主题的联机版本。 当你使用的 **联机** 参数时，将打开联机版本 `Get-Help` 。 URI 必须以 "http" 或 "https" 开头。

### <a name="component"></a>.组件

函数或脚本使用或与之相关的技术或功能的名称。 的 **组件** 参数 `Get-Help` 使用此值来筛选返回的搜索结果 `Get-Help` 。

### <a name="role"></a>.职位

帮助主题的用户角色的名称。 的 **Role** 参数 `Get-Help` 使用此值来筛选返回的搜索结果 `Get-Help` 。

### <a name="functionality"></a>.性能

描述函数的预期用途的关键字。 的 **功能** 参数 `Get-Help` 使用此值来筛选返回的搜索结果 `Get-Help` 。

### <a name="forwardhelptargetname"></a>.FORWARDHELPTARGETNAME

重定向到指定命令的帮助主题。 您可以将用户重定向到任何帮助主题，包括函数、脚本、cmdlet 或提供程序的帮助主题。

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>.FORWARDHELPCATEGORY

指定中的项的帮助类别 `.ForwardHelpTargetName` 。 有效值为 `Alias` 、、 `Cmdlet` 、 `HelpFile` `Function` 、 `Provider` 、、 `General` 、、、、 `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` 或 `All` 。 当存在具有相同名称的命令时，请使用此关键字避免冲突。

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>.REMOTEHELPRUNSPACE

指定包含 "帮助" 主题的会话。 输入包含 **PSSession** 对象的变量。 此关键字由 [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet 用于查找有关导出的命令的帮助主题。

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>..EXTERNALHELP

为脚本或函数指定基于 XML 的帮助文件。

```powershell
# .EXTERNALHELP <XML Help File>
```

在 `.ExternalHelp` XML 文件中记录函数或脚本时，需要使用关键字。 如果没有此关键字，则找 `Get-Help` 不到函数或脚本的基于 XML 的帮助文件。

`.ExternalHelp`关键字优先于其他基于注释的帮助关键字。 如果 `.ExternalHelp` 存在，则不 `Get-Help` 会显示基于注释的帮助，即使找不到与关键字的值匹配的帮助主题 `.ExternalHelp` 。

如果函数是由模块导出的，请将关键字的值设置 `.ExternalHelp` 为不带路径的文件名。 `Get-Help` 在模块目录的特定于语言的子目录中查找指定的文件名。 对于函数，不需要提供基于 XML 的帮助文件的名称，但最佳做法是使用以下格式：

```
<ScriptModule.psm1>-help.xml
```

如果该函数未包含在模块中，则包含基于 XML 的帮助文件的路径。 如果值包含路径，并且路径包含 UI 区域性特定的子目录，则会以 `Get-Help` 递归方式搜索包含脚本或函数名称的 XML 文件的子目录，就像在模块目录中那样。

有关 cmdlet 的帮助文件格式的详细信息，请参阅 [如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-comment-based-help-topics)。

## <a name="autogenerated-content"></a>自动生成内容

Cmdlet 自动生成名称、语法、参数列表、参数属性表、通用参数和备注 `Get-Help` 。

### <a name="name"></a>名称

函数帮助主题的 **name** 节取自函数语法中的函数名称。 脚本帮助主题的 **名称** 取自脚本文件名。 若要更改名称或其大小写，请更改函数语法或脚本文件名。

### <a name="syntax"></a>语法

帮助主题的 **语法** 部分是从函数或脚本语法生成的。 若要将详细信息添加到帮助主题语法（如参数的 .NET 类型），请将详细信息添加到语法中。 如果未指定参数类型，则会将该 **对象** 类型作为默认值插入。

### <a name="parameter-list"></a>参数列表

帮助主题中的参数列表是从函数或脚本语法以及使用关键字添加的说明生成的 `.Parameter` 。 函数参数显示在帮助主题的 **parameters** 节中，其顺序与它们在函数或脚本语法中出现的顺序相同。 参数名称的拼写和大小写也是从语法中获取的。 它不受关键字指定的参数名称的影响 `.Parameter` 。

### <a name="common-parameters"></a>通用参数

**公用参数** 将添加到帮助主题的语法和参数列表中，即使它们不起作用也是如此。 有关常见参数的详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

### <a name="parameter-attribute-table"></a>参数属性表

`Get-Help` 生成在使用的 **完整** 参数或 **参数** 参数时显示的参数属性表 `Get-Help` 。 " **必需**"、" **位置**" 和 " **默认** 值" 属性的值取自函数或脚本语法。

即使在函数或脚本中定义了默认值和 " **接受通配符** " 的值，也不会显示在参数属性表中。 若要帮助用户，请在参数说明中提供此信息。

### <a name="remarks"></a>备注

"帮助" 主题的 " **备注** " 部分是从函数或脚本名称自动生成的。 不能更改或影响其内容。

## <a name="examples"></a>示例

### <a name="comment-based-help-for-a-function"></a>函数的基于注释的帮助

以下示例函数包含基于注释的帮助：

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

结果如下所示：

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>函数语法中的参数说明

此示例与上一个示例相同，不同之处在于参数说明插入函数语法。 当说明简短时，此格式最为有用。

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>脚本的基于注释的帮助

下面的示例脚本包含基于注释的帮助。 请注意结束 `#>` 语句和语句之间的空行 `Param` 。 在不包含语句的脚本中 `Param` ，"帮助" 主题中的最后一个注释和第一个函数声明之间必须至少有两个空行。 如果没有这些空白行，请将 `Get-Help` 帮助主题与函数（而不是脚本）相关联。

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

以下命令获取脚本帮助。 由于脚本不在环境变量中列出的目录中，因此 `$env:Path` `Get-Help` 获取脚本帮助的命令必须指定脚本路径。

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>重定向到 XML 文件

您可以为函数和脚本编写基于 XML 的帮助主题。 尽管基于注释的帮助更容易实现，但可更新帮助和提供多种语言的帮助主题需要基于 XML 的帮助。

下面的示例演示 Update-Month.ps1 脚本的前几行。
脚本使用关键字为 `.ExternalHelp` 脚本指定基于 XML 的帮助主题的路径。

请注意，关键字的值与 `.ExternalHelp` 关键字显示在同一行中。 任何其他放置都是无效的。

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

下面的示例在函数中显示了三个有效的 `.ExternalHelp` 关键字位置。

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>重定向到其他帮助主题

下面的代码摘自 PowerShell 中内置帮助函数的开头部分，该函数一次显示一个屏幕帮助文本。
由于 cmdlet 的帮助主题 `Get-Help` 描述了 help 函数，因此 help 函数使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 关键字将用户重定向到 `Get-Help` cmdlet 帮助主题。

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

以下命令使用此功能：

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>另请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[如何编写 Cmdlet 帮助](https://go.microsoft.com/fwlink/?LinkID=123415)
