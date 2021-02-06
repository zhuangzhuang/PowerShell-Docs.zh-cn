---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 82721b3d079c795e0ce6fcae1fba0eab93344b52
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597244"
---
# Get-Help

## 摘要
显示有关 PowerShell 命令和概念的信息。

## SYNTAX

### AllUsersView（默认值）

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 示例

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### parameters

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 联机

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## DESCRIPTION

`Get-Help`Cmdlet 显示有关 PowerShell 概念和命令（包括 cmdlet、函数、通用信息模型 (CIM) 命令、工作流、提供程序、别名和脚本）的信息。

若要获取 PowerShell cmdlet 的帮助，请键入 `Get-Help` 后跟 cmdlet 名称，如： `Get-Help Get-Process` 。

PowerShell 中的概念性帮助文章从 **about_** 开始，如 **about_Comparison_Operators**。 若要查看所有 **about_** 项目，请键入 `Get-Help about_*` 。 若要查看特定项目，请键入 `Get-Help about_<article-name>` ，例如 `Get-Help about_Comparison_Operators` 。

若要获取 PowerShell 提供程序的帮助，请键入， `Get-Help` 后跟提供程序名称。 例如，若要获取有关证书提供程序的帮助，请键入 `Get-Help Certificate` 。

您还可以键入 `help` 或 `man` ，这将一次显示一屏文本。 或， `<cmdlet-name> -?` 这等同于 `Get-Help` ，但仅适用于 cmdlet。

`Get-Help` 从计算机上的帮助文件中获取它显示的帮助内容。 如果没有帮助文件， `Get-Help` 只显示有关 cmdlet 的基本信息。 某些 PowerShell 模块包括帮助文件。 从 PowerShell 3.0 开始，Windows 操作系统附带的模块不包含帮助文件。 若要下载或更新 PowerShell 3.0 中某个模块的帮助文件，请使用 `Update-Help` cmdlet。

你还可以在 Microsoft Docs 中联机查看 PowerShell 帮助文档。若要获取帮助文件的联机版本，请使用 **online** 参数，例如： `Get-Help Get-Process -Online` 。 若要阅读所有 PowerShell 文档，请参阅 Microsoft Docs [Powershell 文档](/powershell)。

如果键入的 `Get-Help` 名称后跟帮助文章的确切名称，或按帮助文章的唯一名称键入 `Get-Help` 内容，将显示该文章的内容。 如果指定命令别名的确切名称，则会 `Get-Help` 显示原始命令的帮助。 如果输入在多个帮助文章标题中出现的单词或单词模式， `Get-Help` 则将显示匹配标题的列表。 如果输入未出现在任何帮助文章标题中的任何文本， `Get-Help` 将显示项目列表，其中包含其内容中的文本。

`Get-Help` 可以获取所有支持的语言和区域设置的帮助文章。 `Get-Help` 首先在设置为 Windows 的区域设置中查找帮助文件，然后在父区域设置中查找， **例如 pt** **-BR**，然后在备用区域中。 从 PowerShell 3.0 开始，如果在 `Get-Help` 回退区域设置中找不到帮助，它将在返回错误消息或显示自动生成的帮助之前，查找英语、 **en-us** 中的帮助文章。

有关 `Get-Help` 命令语法关系图中显示的符号的信息，请参阅 [about_Command_Syntax](./About/about_Command_Syntax.md)。
有关参数属性（例如 **Required** 和 **Position**）的信息，请参阅 [about_Parameters](./About/about_Parameters.md)。

>[!NOTE]
> 在 PowerShell 3.0 和 PowerShell 4.0 中， `Get-Help` 除非将模块导入到当前会话中，否则无法在模块中找到 **相关** 项目。 这是一个已知问题。 若要 **获取模块** 中的项目，请使用 `Import-Module` cmdlet 或通过运行模块中包含的 cmdlet 来导入模块。

## 示例

### 示例1：显示有关 cmdlet 的基本帮助信息

这些示例显示有关 cmdlet 的基本帮助信息 `Format-Table` 。

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` 是 cmdlet 的最简单和默认的语法 `Get-Help` 。 您可以省略 **Name** 参数。

语法 `<cmdlet-name> -?` 仅适用于 cmdlet。

### 示例2：每次显示一页的基本信息

这些示例每次显示有关 cmdlet 的基本帮助信息 `Format-Table` 。

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` 是在 `Get-Help` 内部运行 cmdlet 并每次显示一页结果的函数。

`man` 是函数的别名 `help` 。

`Get-Help Format-Table` 沿管道向下发送对象。 `Out-Host -Paging` 接收管道的输出，一次显示一个页面。 有关详细信息，请参阅 [托管主机](Out-Host.md)。

### 示例3：显示 cmdlet 的详细信息

这些示例显示有关 cmdlet 的更详细的帮助信息 `Format-Table` 。

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

**详细** 参数显示了帮助文章的详细视图，其中包括参数说明和示例。

**Full** 参数显示帮助文章的完整视图，其中包括参数说明、示例、输入和输出对象类型以及其他说明。

对于在计算机上安装了帮助文件的命令， **详细** 参数和 **完整** 参数仅有效。 这些参数对于概念 (**about_**) 帮助文章不起作用。

### 示例4：使用参数显示 cmdlet 的选定部分

这些示例显示了 cmdlet 帮助的选定部分 `Format-Table` 。

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

**示例** 参数显示帮助文件的 **名称** 和 **摘要** 部分以及所有示例。 无法指定示例编号，因为 **示例** 参数是一个开关参数。

**Parameter** 参数只显示指定参数的描述。 如果仅指定星号 (`*`) 通配符，则它将显示所有参数的描述。
当 **参数** 指定参数名称（如 **GroupBy**）时，将显示有关该参数的信息。

这些参数对于概念 (**about_**) 帮助文章无效。

### 示例5：显示帮助的联机版本

此示例将 `Format-Table` 在默认 web 浏览器中显示该 cmdlet 的帮助文章的联机版本。

```powershell
Get-Help Format-Table -Online
```

### 示例6：显示有关帮助系统的帮助

`Get-Help`不带参数的 cmdlet 显示有关 PowerShell 帮助系统的信息。

```powershell
Get-Help
```

### 示例7：显示可用的帮助文章

此示例显示了计算机上可用的所有帮助文章的列表。

```powershell
Get-Help *
```

### 示例8：显示概念项目的列表

此示例显示 PowerShell 帮助中包含的概念文章的列表。 所有这些文章都以 **about_** 的字符开头。 若要显示特定的帮助文件，请键入 `Get-Help \<about_article-name\>` ，例如 `Get-Help about_Signing` 。

仅显示在计算机上安装了帮助文件的概念文章。 有关在 PowerShell 3.0 中下载和安装帮助文件的信息，请参阅 [Update-help](Update-Help.md)。

```powershell
Get-Help about_*
```

### 示例9：在 cmdlet 帮助中搜索字词

此示例演示如何搜索 cmdlet 帮助文章中的单词。

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` 使用 **Full** 参数获取的帮助信息 `Add-Member` 。 **MamlCommandHelpInfo** 对象沿管道向下发送。 `Out-String` 使用 **Stream** 参数将对象转换为字符串。 `Select-String` 使用 **Pattern** 参数在字符串中搜索 **export-clixml**。

### 示例10：显示包含单词的项目列表

此示例显示包含 word **远程处理** 的项目列表。

输入未出现在任何文章标题中的单词时，会 `Get-Help` 显示包含该单词的项目列表。

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### 示例11：显示特定于提供程序的帮助

此示例演示了获取特定于提供程序的帮助的两种方法 `Get-Item` 。 这些命令将获取有关如何 `Get-Item` 在 PowerShell SQL Server 提供程序的 **DataCollection** 节点中使用 cmdlet 的帮助。

第一个示例使用 `Get-Help` **Path** 参数来指定 SQL Server 提供程序的路径。
由于指定了提供程序的路径，因此可以从任何路径位置运行该命令。

第二个示例使用 `Set-Location` 导航到 SQL Server 提供程序的路径。 在该位置，无需 **路径** 参数 `Get-Help` 即可获取特定于提供程序的帮助。

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### 示例12：显示脚本的帮助

此示例获取有关的帮助 `MyScript.ps1 script` 。 有关如何为函数和脚本编写帮助的信息，请参阅 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)。

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETERS

### -Category

只显示指定类别及其别名中的项的帮助。 " **帮助** " 类别中有概念文章。

此参数可接受的值如下所示：

- Alias
- Cmdlet
- 提供程序
- 常规
- 常见问题解答
- 术语表
- HelpFile
- ScriptCommand
- 函数
- 筛选器
- ExternalScript
- 全部
- DefaultHelp
- 工作流
- DscResource
- 实例
- Configuration

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Component

显示具有指定组件值（如 **Exchange**）的命令。 输入组件名称。
允许使用通配符。 此参数对概念 (**About_**) 帮助的显示没有影响。

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

### -Detailed

将参数说明和示例添加到基本帮助显示。 仅当计算机上安装了帮助文件时，此参数才有效。 它不会影响概念性 (**About_**) 帮助的显示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Examples

只显示名称、摘要和示例。 若要仅显示示例，请键入 `(Get-Help \<cmdlet-name\>).Examples` 。

仅当计算机上安装了帮助文件时，此参数才有效。 它不会影响概念性 (**About_**) 帮助的显示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

显示 cmdlet 的整个帮助文章。 **Full** 包含参数说明和属性、示例、输入和输出对象类型以及其他说明。

仅当计算机上安装了帮助文件时，此参数才有效。 它不会影响概念性 (**About_**) 帮助的显示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Functionality

显示具有指定功能的项的帮助。 输入功能。 允许使用通配符。 此参数对概念 (**About_**) 帮助的显示没有影响。

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

### -Name

获取有关指定命令或概念的帮助。 输入 cmdlet、函数、提供程序、脚本或工作流的名称，如 `Get-Member` 概念项目名称（如 `about_Objects` ）或别名（例如） `ls` 。 允许在 cmdlet 和提供程序名称中使用通配符，但不能使用通配符来查找函数帮助和脚本帮助文章的名称。

若要获取不在环境变量中列出的路径中的脚本的帮助 `$env:Path` ，请键入该脚本的路径和文件名。

如果输入了帮助文章的确切名称，则会 `Get-Help` 显示项目内容。

如果输入在多个帮助文章标题中出现的单词或单词模式， `Get-Help` 则将显示匹配标题的列表。

如果输入的任何文本与任何帮助文章标题都不匹配，则会 `Get-Help` 显示项目列表，其中包含其内容中的文本。

概念文章的名称（例如 `about_Objects` ）必须以英语输入，即使在非英语版本的 PowerShell 中也是如此。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Online

在默认浏览器中显示帮助文章的联机版本。 此参数仅对 cmdlet、函数、工作流和脚本帮助文章有效。 不能 `Get-Help` 在远程会话中将 Online 参数与一起使用。

有关在你编写的帮助文章中支持此功能的信息，请参阅 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)和 [支持联机帮助](/powershell/scripting/developer/module/supporting-online-help)以及 [为 PowerShell cmdlet 编写帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parameter

只显示指定参数的详细说明。 允许使用通配符。 此参数对概念 (**About_**) 帮助的显示没有影响。

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

获取说明 cmdlet 在指定的提供程序路径中的工作方式的帮助。 输入 PowerShell 提供程序路径。

此参数获取自定义版本的 cmdlet 帮助文章，其中介绍了 cmdlet 在指定的 PowerShell 提供程序路径中的工作方式。 此参数仅对有关提供程序 cmdlet 的帮助有效，并且仅当提供程序在其帮助文件中包含提供程序 cmdlet 帮助项目的自定义版本时才有效。 若要使用此参数，请安装包含该提供程序的模块的帮助文件。

若要查看提供程序路径的自定义 cmdlet 帮助，请访问提供程序路径位置并输入 `Get-Help` 命令，或从任意路径位置使用 **path** 参数 `Get-Help` 来指定提供程序路径。 你还可以在 "帮助" 文章的 "提供程序帮助" 部分中找到 "自定义 cmdlet 帮助"。

有关 PowerShell 提供程序的详细信息，请参阅 [about_Providers](./About/about_Providers.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Role

显示为指定的用户角色自定义的帮助。 输入角色。 允许使用通配符。

输入用户在组织中所扮演的角色。 某些 cmdlet 将在其帮助文件中显示不同的文本，具体取决于此参数的值。 此参数对核心 cmdlet 的帮助不起作用。

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

### -ShowWindow

在窗口中显示帮助主题以便于阅读。 该窗口包括 " **查找** " 搜索功能和 " **设置** " 框，使用该功能可以设置显示的选项，包括只显示帮助主题的选定部分的选项。

**ShowWindow** 参数支持 (cmdlet、函数、CIM 命令、脚本) 的帮助主题以及 **有关** 项目的概念。 它不支持提供程序帮助。

此参数已被引入 PowerShell 7.0。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能将对象向下发送到 `Get-Help` 。

## 输出

### ExtendedCmdletHelpInfo

如果在没有 `Get-Help` 帮助文件的命令上运行，则将 `Get-Help` 返回表示自动生成的帮助的 **ExtendedCmdletHelpInfo** 对象。

### System.String

如果你获取了概念性帮助文章，则 `Get-Help` 会将其作为字符串返回。

### MamlCommandHelpInfo

如果收到包含帮助文件的命令，则 `Get-Help` 返回 **MamlCommandHelpInfo** 对象。

## 注释

PowerShell 3.0 不包含帮助文件。 若要下载并安装读取的帮助文件 `Get-Help` ，请使用 `Update-Help` cmdlet。 可以使用 `Update-Help` cmdlet 下载和安装 PowerShell 附带的核心命令的帮助文件，以及安装的任何模块的帮助文件。 还可以使用它来更新帮助文件，以使计算机上的帮助永不过时。

你还可以阅读有关 PowerShell online 附带的命令的帮助文章，从 [Windows PowerShell 入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)开始。

`Get-Help` 显示针对 Windows 操作系统的区域设置或该区域设置的回退语言中的帮助。 如果没有主区域设置或回退区域设置的帮助文件，则 `Get-Help` 的行为就好像计算机上没有帮助文件。 若要获取有关不同区域设置的帮助，请使用 "控制面板" 中的 " **区域** 和 **语言** " 来更改设置。 在 Windows 10 上， **设置**， **时间 & 语言**。

帮助的完整视图包括有关参数的信息表。 该表包括以下字段：

- “必需”。 指示参数是必需的 (true) 还是可选的 (false)。

- **位置**。 指示参数是命名参数还是位置 (数值) 。 位置参数必须出现在命令中的指定位置。

- **命名** 指示参数名称是必需的，但参数可以出现在命令中的任意位置。

- **数值** 指示参数名称是可选的，但当省略名称时，该参数必须位于由该数字指定的位置。 例如， `2` 指示当省略参数名称时，该参数必须是命令中的第二个或唯一一个未命名的参数。 当使用了参数名称时，该参数可以出现在命令中的任意位置。

- **默认值**。 如果未在命令中包含参数，则 PowerShell 使用的参数值或默认行为。

- 接受管道输入。 指示是否可以 (true) 或不能 (false) 通过管道将对象发送到参数。 **按属性名称** 表示，流水线对象必须具有与参数名称相同的属性。

- **接受通配符**。 指示参数的值是否可以包括通配符，如星号 (`*`) 或问号 (`?`) 。

## 相关链接

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[支持可更新帮助](/powershell/scripting/developer/module/supporting-updatable-help)

[Update-Help](Update-Help.md)

[编写基于注释的帮助主题](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[编写针对 PowerShell Cmdlet 的帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

