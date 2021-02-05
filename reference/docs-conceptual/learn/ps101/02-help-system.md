---
title: 帮助系统
description: 掌握帮助系统是成功使用 PowerShell 的关键。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cfb12f57b7bb6c514f4e19a93dfe9c77245bd977
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598659"
---
# <a name="chapter-2---the-help-system"></a>第 2 章 - 帮助系统

两组 IT 专业人员在没有使用计算机的情况下参加了笔试，目的是确定他们的 PowerShell 技能水平。 PowerShell 初学者归为一个组，专家归为另一个组。
根据测试结果来看，两组人员掌握的技能水平似乎并没有太大差异。 两组人员又参加了第二个测试，该测试与第一个测试类似。 这次，允许他们使用安装了 PowerShell 的计算机，但计算机无法访问 Internet。 第二次测试的结果显示两组人员之间的技能水平存在巨大差异。 专家不一定总是知道答案，但是他们知道如何得到答案。

这两个组之间第一次测试和第二次测试得出的结果有何不同？

这两个测试的结果之间的差异是因为专家不会记忆如何在 PowerShell 中使用数千个命令。 他们了解如何在 PowerShell 中很好地利用帮助系统。
这样，他们就可以在需要时找到必要的命令，在找到这些命令后，也知道如何使用它们。

我听闻 PowerShell 的发明者 Jeffrey Snover 讲过多次类似的故事。

掌握帮助系统是成功使用 PowerShell 的关键。

## <a name="discoverability"></a>可发现性

PowerShell 中的编译命令称为 cmdlet。 Cmdlet 的发音为“command-let”（而不是 CMD-let）。 Cmdlet 名称采用单数形式的“动词-名词”命令形式，这样更易于被发现。 例如，用于确定正在运行哪些进程的 cmdlet 是 `Get-Process`，而用于检索服务及其状态的列表的 cmdlet 是 `Get-Service`。 PowerShell 中还有其他类型的命令（例如别名和函数），本书后面部分将对其进行介绍。 术语 PowerShell 命令是一个通用术语，通常用于指代 PowerShell 中任何类型的命令，不管是 cmdlet、函数还是别名。

## <a name="the-three-core-cmdlets-in-powershell"></a>PowerShell 中的三个核心 Cmdlet

- `Get-Command`
- `Get-Help`
- `Get-Member`（在第 3 章中介绍此内容）

我经常被问到的一个问题是如何确定 PowerShell 中的命令是什么？ `Get-Command` 和 `Get-Help` 均可用于确定命令。

## <a name="get-help"></a>Get-Help

`Get-Help` 是多用途命令。 `Get-Help` 帮助你了解找到命令后如何使用它们。 `Get-Help` 也可用于帮助查找命令，但与 `Get-Command` 相比，它采用不同且较为间接的方式。

使用 `Get-Help` 查找命令时，它首先根据提供的输入来搜索命令名称的通配符匹配项。 如果找不到匹配项，它将搜索帮助主题本身；如果还找不到匹配项，则返回错误。 与通常的看法相反，`Get-Help` 可用于查找没有帮助主题的命令。

关于 PowerShell 中的帮助系统，首先需要了解如何使用 `Get-Help` cmdlet。 以下命令用于显示 `Get-Help` 的帮助主题。

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

从 PowerShell 版本 3 开始，操作系统不随附 PowerShell 帮助功能。 第一次为命令运行 `Get-Help` 时，系统将显示上一条消息。 如果使用的是 `help` 函数或 `man` 别名（而不是 `Get-Help` cmdlet），则不会收到此提示。

若要回答“是”，请按 <kbd>Y</kbd> 以运行 `Update-Help` cmdlet，默认情况下该 cmdlet 需要 Internet 访问权限。 可以大写或小写形式指定 `Y`。

下载帮助并完成更新后，将为指定的命令返回帮助主题：

```powershell
Get-Help -Name Get-Help
```

花几分钟在计算机上运行该示例，查看输出，并注意信息的分组方式：

- 名称
- 摘要
- SYNTAX
- DESCRIPTION
- 相关链接
- REMARKS

如你所见，帮助主题可能包含大量的信息，而这甚至不是全部的帮助主题。

虽然参数不是特定于 PowerShell 的，但也是向命令提供输入的一种方式。 `Get-Help` 具有许多参数，可以指定这些参数，使结果中返回整个帮助主题或其子集。

上一组结果中显示的帮助主题的语法部分列出了 `Get-Help` 的所有参数。 乍一看，似乎在六个不同的地方列出了相同的参数。 语法部分中的每个不同的块都是参数集。 这意味着 `Get-Help` cmdlet 具有六个不同的参数集。 如果仔细研究，就会发现每个参数集中至少有一个不同的参数。

参数集是互斥的。 一旦使用了其中某个参数集中独有的某个参数，就只能使用该参数集中包含的参数。 例如，无法同时指定 Full 和 Detailed 参数，因为它们位于不同的参数集中 。

以下每个参数都位于不同的参数集中：

- 完全
- 详细信息
- 示例
- 联机
- 参数
- ShowWindow

语法部分中的所有晦涩的语法（例如方括号和尖括号）均具有某些含义，本书的附录 A 中对此进行介绍。 尽管这些语法很重要，但对于不熟悉 PowerShell 且日常不使用它的人来说，通常难以记住这些晦涩的语法。

若要详细了解如何更好地理解晦涩的语法，请参阅[附录 A][]。

对于初学者而言，可以通过一种更简单的方法来获取相同的信息（纯语言内容除外）。

指定 `Get-Help` 的 Full 参数后，可返回整个帮助主题。

```powershell
Get-Help -Name Get-Help -Full
```

花几分钟在计算机上运行该示例，查看输出，并注意信息的分组方式：

- 名称
- 摘要
- SYNTAX
- DESCRIPTION
- PARAMETERS
- 输入
- 输出
- 注释
- 示例
- 相关链接

请注意，使用 Full 参数返回了几个额外部分，其中一个部分是 PARAMETERS 部分，该部分提供的信息比晦涩的 SYNTAX 部分还要多。

Full 参数是一个开关参数。 不需要值的参数称为开关参数。 如果指定了某个开关参数，其值为 true；否则为 false。

如果已在 PowerShell 控制台中学完了本章，你会注意到屏幕上掠过了上一个显示 `Get-Help` 的完整帮助主题的命令，但快到你无法阅读该命令。 还有更好的办法。

`Help` 是一个函数，它通过管道将 `Get-Help` 传递给名为 `more` 的函数，后者是 Windows 中 `more.com` 可执行文件的包装器。 在 PowerShell 控制台中，`help` 一次提供一页帮助信息。 在 ISE 中，其工作方式与 `Get-Help` 相同。 建议使用 `help` 函数，而不使用 `Get-Help` cmdlet，因为前者提供了更好的体验，而且需要键入的内容更少。

不过，减少键入的内容有时并非是好事。 如果要将命令另存为脚本或与他人共享命令，请确保使用完整的 cmdlet 和参数名称。 完整名称是自描述名称，这使它们更易于理解。 请考虑下一个需要阅读和理解你的命令的人。 也许这个人就是你自己。 你的同事和将来的你自己将感谢你。

尝试在 Windows 10 实验环境计算机上的 PowerShell 控制台中运行以下命令。

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

在 Windows 10 实验环境计算机上运行这些命令时，是否注意到上述命令的输出存在任何差异？

除了最后两个选项每次返回一页以外，结果都一样。
使用 `Help` 函数时，可使用<kbd>空格键</kbd>显示下一页内容，可使用 <kbd>Ctrl</kbd>+<kbd>C</kbd> 取消在 PowerShell 控制台中运行的命令。

第一个示例使用 `Get-Help` cmdlet，第二个示例使用 `Help` 函数，第三个示例在使用 `Help` 函数时省略了 Name 参数。 Name 是一个位置参数，在该示例中按位置使用该参数。 这意味着只要在正确的位置指定值本身，就可以在不指定参数名称的情况下指定值。 如何知晓在哪个位置指定值？ 可通过阅读帮助信息来了解，如以下示例所示。

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

请注意，在前面的示例中，将 Parameter 参数与 Help 函数一起使用，以便仅返回 Name 参数的帮助主题中的信息 。 与手动筛选帮助主题内容（有时可能超过一百页）相比，这样做会方便许多。

根据这些结果，可以看到 Name 参数是位置参数，并且在按位置使用时必须在位置零（第一个位置）处指定。 如果指定了参数名称，则参数名称的指定顺序无关紧要。

另一条重要的信息是，Name 参数的值的预期数据类型是单个字符串，该字符串由 `<String>` 表示。 如果它接受多个字符串，则数据类型将列为 `<String[]>`。

有时，你不想显示命令的整个帮助主题。 除了 Full 之外，还有许多其他参数可以用 `Get-Help` 或 `Help` 指定。 尝试在 Windows 10 实验环境计算机上运行以下命令：

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

我通常将 `help <command name>` 与 Full 或 Online 参数一起使用 。 如果只对示例感兴趣，可使用 Examples 参数；如果只对特定参数感兴趣，可使用 Parameter 参数 。 ShowWindow 参数在单独的可搜索窗口中打开帮助主题，如果有多个监视器，还可以在其他监视器上显示该窗口。 我没有使用 ShowWindow 参数，因为存在不显示整个帮助主题的已知 bug。

如果需要在单独的窗口中显示帮助，建议使用 Online 参数或 Full 参数，并通过管道将结果传递给 `Out-GridView`，如以下示例所示 。

```powershell
help Get-Command -Full | Out-GridView
```

`Out-GridView` cmdlet，以及 `Get-Help` cmdlet 的 ShowWindow 参数都需要具有 GUI（图形用户界面）的操作系统。 如果尝试在使用服务器核心（不带 GUI）安装选项安装的 Windows Server 上使用其中任意一个，会生成一条错误消息。

要使用 `Get-Help` 查找命令，请对 Name 参数使用星号 (`*`) 通配符。 指定搜索命令时使用的字词，作为 Name 参数的值，如以下示例中所示。

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

在前面的示例中，不需要 `*` 通配符，如果省略它们，得到的结果相同。 `Get-Help` 自动在无提示的情况下添加通配符。

```powershell
help process
```

上一条命令生成的结果与在进程的两头指定 `*` 通配符得到的结果相同。

我喜欢添加这些通配符，因为这样可以始终得到一致的结果。 另外，这些通配符仅在某些方案中需要。 在值中间添加通配符后，将不再以自动添加的方式将通配符添加到指定的值上。

```powershell
help pr*cess
```

除非将 `*` 通配符添加到 `pr*cess` 的开头，或开头和结尾，否则该命令不返回任何结果。

如果指定的值以破折号开头，则会生成错误，因为 PowerShell 将其解释为参数名称，但 `Get-Help` cmdlet 不存在此类参数名称。

```powershell
help -process
```

如果要查找的是以 `-process` 结尾的命令，则只需将 `*` 通配符添加到值的开头即可。

```powershell
help *-process
```

使用 `Get-Help` 搜索 PowerShell 命令时，使用更宽泛而不是更具体的搜索信息。

之前搜索 `process` 时只找到名称中包含 `process` 的命令，并且只返回了那些结果。 使用 `Get-Help` 搜索 `processes` 时，它找不到命令名称的任何匹配项，因此它将搜索系统中 PowerShell 中的每个帮助主题，并返回找到的所有匹配项。 这使其返回大量结果。

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

使用 `Help` 搜索 `process` 返回了 10 个结果，而使用该命令搜索 `processes` 返回了 68 个结果。 如果只找到一个结果，将显示帮助主题本身，而不显示命令列表。

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

现在来破除一个误区，即 PowerShell 中的 `Help` 只能找到具有帮助主题的命令。

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

请注意，在前面的示例中，`more` 没有帮助主题，但 PowerShell 中的 `Help` 系统仍可以找到它。 它只找到一个匹配项，并返回了基本的语法信息，如果命令没有帮助主题，就会看到这些信息。

PowerShell 包含大量的概念性（关于）帮助主题。 以下命令可用于返回系统上所有“关于”帮助主题的列表。

```powershell
help About_*
```

将结果限制为单个“关于”帮助主题会显示实际的帮助主题内容，而不是返回一个列表。

```powershell
help about_Updatable_Help
```

必须更新 PowerShell 中的帮助系统，才能显示“关于”帮助主题。 如果由于某种原因计算机上的帮助系统的初始更新失败，则在成功运行 `Update-Help` cmdlet 之前，文件将不可用。

## <a name="get-command"></a>Get-Command

`Get-Command` 的作用是帮助查找命令。 运行不带任何参数的 `Get-Command` 会返回系统上所有命令的列表。 以下示例演示使用 `Get-Command` cmdlet 确定存在的用于处理进程的命令：

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

请注意，在前面运行了 `Get-Command` 的示例中，使用了 Noun 参数，并且将 `Process` 指定为 Noun 参数的值 。 如果不知道如何使用 `Get-Command` cmdlet，该怎么办？ 可以使用 `Get-Help` 显示 `Get-Command` 的帮助主题。

Name、Noun 和 Verb 参数均接受通配符  。 下面的示例演示与 Name 参数一起使用的通配符：

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

我不喜欢将通配符与 `Get-Command` 的 Name 参数一起使用，因为它还返回不是本机 PowerShell 命令的可执行文件。

如果要在 Name 参数中使用通配符，建议使用 CommandType 参数来限定结果 。

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

更好的选择是使用 Verb 或/和 Noun 参数，因为只有 PowerShell 命令同时具有谓词和名词 。

发现帮助主题中存在问题？ 好消息是，PowerShell 的帮助主题是开放源代码主题，可以在 GitHub 上的 [PowerShell-Docs][] 存储库中找到。 将帮助主题公开，不仅可以为自己解决错误信息，还可以帮助其他所有人解决错误信息。 只需在 GitHub 上创建 PowerShell 文档存储库的分支、更新帮助主题以及提交拉取请求。
接受拉取请求后，所有人都可以使用更正后的文档。

## <a name="updating-help"></a>更新帮助

PowerShell 帮助主题的本地副本之前已更新了关于某个请求的命令的首次帮助信息。 建议定期更新帮助系统，因为可能会不时更新帮助内容。 `Update-Help` cmdlet 用于更新帮助主题。
默认情况下，它需要访问 Internet，并且你需要以管理员身份运行提升的 PowerShell。

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

几个模块返回了错误，这种情况很常见。 如果计算机无法访问 Internet，则可以在另一台可以访问互联网的机器上使用 `Save-Help` cmdlet，首先将更新后的帮助信息保存到网络上的文件共享中，然后使用 `Update-Help` 的 SourcePath 参数为帮助主题指定此网络位置。

考虑在 PowerShell 中设置计划任务或向配置文件脚本添加一些逻辑，以定期更新计算机上的帮助内容。 下一章将介绍配置文件脚本。

## <a name="summary"></a>总结

在本章中，你了解了如何使用 `Get-Help` 和 `Get-Command` 来查找命令。 你了解了如何使用帮助系统来搞清楚在找到命令后如何使用这些命令。 你还了解了有可用更新时如何更新帮助主题的内容。

我对你的要求是每天学习一个 PowerShell 命令。

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>审阅

1. `Get-Service` 的 DisplayName 参数是否是按位置使用的参数？
1. `Get-Process` cmdlet 有多少个参数集？
1. 存在哪些用于处理事件日志的 PowerShell 命令？
1. 哪个 PowerShell 命令可以返回计算机上运行的 PowerShell 进程的列表？
1. 如何更新存储在计算机上的 PowerShell 帮助内容？

## <a name="recommended-reading"></a>推荐阅读的主题

如果想详细了解本章介绍的主题，建议阅读以下 PowerShell 帮助主题。

- [Get-Help][]
- [Get-Command][]
- [Update-Help][]
- [Save-Help][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

在下一章中，你将了解 `Get-Member` cmdlet 以及对象、属性和方法。

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[附录 A]: appendix-a.md
