---
description: 描述存储 PowerShell 的状态信息的变量。 这些变量由 PowerShell 创建和维护。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 8a2410dd2adcc1679ab203293b4c4e712b960278
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975135"
---
# <a name="about-automatic-variables"></a>关于自动变量

## <a name="short-description"></a>简短说明

描述存储 PowerShell 的状态信息的变量。 这些变量由 PowerShell 创建和维护。

## <a name="long-description"></a>长说明

从概念上讲，这些变量被视为只读。 即使 **可** 将它们写入到中，但 **不应** 将其写入到后向兼容性。

下面是 PowerShell 中自动变量的列表：

### <a name=""></a>$$

包含会话收到的最后一行中的最后一个标记。

### <a name=""></a>$?

包含最后一个命令的执行状态。 如果最后一个命令成功，则 **为 True;** 否则为 **False** 。

对于在管道中的多个阶段（例如在和块中）运行的 cmdlet 和高级函数，在 `process` `end` `this.WriteError()` 任何点调用或分别调用或 `$PSCmdlet.WriteError()` 分别将设置 `$?` 为 **False**，就像 `this.ThrowTerminatingError()` 和 `$PSCmdlet.ThrowTerminatingError()` 。

`Write-Error`Cmdlet 始终在 `$?` 执行后立即设置为 **false** ，但不会 `$?` 对调用它的函数设置为 **false** ：

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

对于后一种用途， `$PSCmdlet.WriteError()` 应改为使用。

对于 (可执行文件) 的本机命令， `$?` 当为0时，将设置为 **True** `$LASTEXITCODE` ，如果 `$LASTEXITCODE` 为任何其他值，则设置为 False。

> [!NOTE]
> 在 PowerShell 7 中，在括号内包含语句后 `(...)` ，子表达式语法 `$(...)` 或数组表达式 `@(...)` 始终重置 `$?` 为 **True**，因此 `(Write-Error)` 显示 `$?` 为 **true**。
> 此操作在 PowerShell 7 中已更改，因此 `$?` 将始终反映在这些表达式中运行的最后一个命令的实际成功。

### <a name=""></a>$^

包含会话收到的最后一行中的第一个标记。

### <a name="_"></a>$_

与 `$PSItem` 相同。 包含管道对象中的当前对象。 可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。

### <a name="args"></a>$args

包含传递给函数、脚本或脚本块的未声明参数的值数组。 创建函数时，可以使用 `param` 关键字或在函数名称后的括号中添加以逗号分隔的参数列表，来声明参数。

在事件操作中， `$args` 变量包含表示正在处理的事件的事件参数的对象。 仅在 `Action` 事件注册命令块内填充此变量。
此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceArgs** 属性中找到 `Get-Event` 。

### <a name="consolefilename"></a>$ConsoleFileName

包含 `.psc1` 会话中最近使用的控制台文件 () 的路径。 使用 **PSConsoleFile** 参数启动 PowerShell 或使用 `Export-Console` cmdlet 将管理单元名称导出到控制台文件时，将填充此变量。

使用 `Export-Console` 不带参数的 cmdlet 时，它会自动更新会话中最近使用的控制台文件。 您可以使用此自动变量来确定将更新哪个文件。

### <a name="error"></a>$Error

包含错误对象的数组，这些对象表示最近的错误。
最近的错误是数组中第一个错误对象 `$Error[0]` 。

若要防止将错误添加到 `$Error` 数组，请使用值为 **Ignore** 的 **ErrorAction** 通用参数。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

### <a name="event"></a>$Event

包含表示正在处理的事件的 **PSEventArgs** 对象。 此变量仅在 `Action` 事件注册命令块中填充，例如 `Register-ObjectEvent` 。 此变量的值与 cmdlet 返回的对象相同 `Get-Event` 。 因此，可以 `Event` `$Event.TimeGenerated` 在脚本块中使用该变量的属性，例如 `Action` 。

### <a name="eventargs"></a>$EventArgs

包含一个对象，该对象表示从正在处理的事件的 **EventArgs** 派生的第一个事件参数。 仅在 `Action` 事件注册命令块内填充此变量。
此变量的值还可在返回的 **PSEventArgs** 对象的 **SourceEventArgs** 属性中找到 `Get-Event` 。

### <a name="eventsubscriber"></a>$EventSubscriber

包含一个 **PSEventSubscriber** 对象，该对象表示正在处理的事件的事件订阅服务器。 仅在 `Action` 事件注册命令块内填充此变量。 此变量的值与 cmdlet 返回的对象相同 `Get-EventSubscriber` 。

### <a name="executioncontext"></a>$ExecutionContext

包含一个 **EngineIntrinsics** 对象，该对象表示 PowerShell 主机的执行上下文。 您可以使用此变量来查找可用于 cmdlet 的执行对象。

### <a name="false"></a>$false

包含 **False**。 可以在命令和脚本中使用此变量来表示 **False** ，而不是使用字符串 "False"。 如果字符串被转换为非空字符串或非零整数，则可以将该字符串解释为 **True** 。

### <a name="foreach"></a>$foreach

包含枚举器 (不是 [ForEach](about_ForEach.md) 循环) 的结果值。 此 `$ForEach` 变量仅在 `ForEach` 循环运行时存在; 在循环完成后将其删除。

枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。 有关详细信息，请参阅 [使用枚举](#using-enumerators)器。

### <a name="home"></a>$HOME

包含用户的主目录的完整路径。 通常，此变量等效于 `"$env:homedrive$env:homepath"` Windows 环境变量 `C:\Users\<UserName>` 。

### <a name="host"></a>$Host

包含表示 PowerShell 的当前主机应用程序的对象。 您可以使用此变量来表示命令中的当前宿主，或者显示或更改主机的属性，例如 `$Host.version` 或 `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` 。

### <a name="input"></a>$input

包含枚举传递到函数的所有输入的枚举器。 此 `$input` 变量仅适用于) 为未命名函数 (函数和脚本块。

- 在没有 `Begin` 、或块的函数中 `Process` `End` ， `$input` 变量枚举函数的所有输入的集合。

- 在 `Begin` 块中， `$input` 变量不包含任何数据。

- 在 `Process` 块中， `$input` 变量包含管道中当前的对象。

- 在 `End` 块中， `$input` 变量枚举函数的所有输入的集合。

  > [!NOTE]
  > 不能 `$input` 在同一函数或脚本块中的进程块和结束块中使用该变量。

由于 `$input` 是一个枚举器，因此访问它的任何属性都将导致 `$input` 不再可用。 可以 `$input` 在另一个变量中存储以重用 `$input` 属性。

枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。 有关详细信息，请参阅 [使用枚举](#using-enumerators)器。

`$input` `-Command` `pwsh` 当从命令行调用时，该变量也可用于由的参数指定的命令。 下面的示例从 Windows 命令行界面运行。

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a>$IsCoreCLR

包含 `$True` 当前会话是否在 .Net Core 运行时上运行 (CoreCLR) 。 否则包含 `$False` 。

### <a name="islinux"></a>$IsLinux

包含 `$True` 当前会话是否在 Linux 操作系统上运行。
否则包含 `$False` 。

### <a name="ismacos"></a>$IsMacOS

包含 `$True` 当前会话是否在 MacOS 操作系统上运行的。
否则包含 `$False` 。

### <a name="iswindows"></a>$IsWindows

`$TRUE`如果当前会话正在 Windows 操作系统上运行，则包含。 否则包含 `$FALSE` 。

### <a name="lastexitcode"></a>$LastExitCode

包含上一次运行的基于 Windows 的程序的退出代码。

### <a name="matches"></a>$Matches

`Matches`变量与 `-match` and 运算符一起使用 `-notmatch` 。
当你将标量输入提交给 `-match` or `-notmatch` 运算符，并且其中一个检测到匹配时，它们将返回一个布尔值，并 `$Matches` 使用匹配的任何字符串值的哈希表填充自动变量。 在 `$Matches` 将正则表达式用于运算符时，还可以使用捕获来填充哈希表 `-match` 。

有关运算符的详细信息 `-match` ，请参阅 [about_Comparison_Operators](about_comparison_operators.md)。 有关正则表达式的详细信息，请参阅 [about_Regular_Expressions](about_Regular_Expressions.md)。

### <a name="myinvocation"></a>$MyInvocation

包含有关当前命令的信息，如名称、参数、参数值和有关如何启动、调用或调用命令的信息，例如调用当前命令的脚本的名称。

`$MyInvocation` 仅填充脚本、函数和脚本块。 您可以使用在当前脚本中返回的 **InvocationInfo** 对象中的信息 `$MyInvocation` ，例如脚本 () 的路径和文件名， `$MyInvocation.MyCommand.Path` 或函数的名称 (`$MyInvocation.MyCommand.Name`) 以标识当前命令。 这对于查找当前脚本的名称特别有用。

从 PowerShell 3.0 开始， `MyInvocation` 具有以下新属性。

| 属性      | 说明                                         |
| ------------- | --------------------------------------------------- |
| **PSScriptRoot**  | 包含调用的脚本的完整路径   |
|               | 当前命令。 此属性的值为  |
|               | 仅当调用方为脚本时才填充。         |
| **PSCommandPath** | 包含脚本的完整路径和文件名  |
|               | 调用当前命令的。 此的值 |
|               | 仅当调用方是     |
|               | 脚本。                                             |

与自动变量不同 `$PSScriptRoot` `$PSCommandPath` ，自动变量的 **PSScriptRoot** 和 **PSCommandPath** 属性 `$MyInvocation` 包含有关调用程序或调用脚本的信息，而不是当前脚本。

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

包含当前提示符级别。 值0表示原始提示级别。 当您输入嵌套级别时，该值会递增，并且在您退出时将递增。

例如，使用方法时，PowerShell 会显示嵌套的命令提示符 `$Host.EnterNestedPrompt` 。 当你到达 PowerShell 调试器中的断点时，PowerShell 还会显示嵌套的命令提示符。

输入嵌套提示符时，PowerShell 将暂停当前命令，保存执行上下文，并递增变量的值 `$NestedPromptLevel` 。 若要创建其他嵌套的命令提示 (最多128级别) 或返回到原始命令提示符，请完成命令或键入 `exit` 。

`$NestedPromptLevel`变量有助于跟踪提示级别。 你可以创建一个包含此值的备用 PowerShell 命令提示符，以使其始终可见。

### <a name="null"></a>$null

`$null` 是包含 **null** 值或空值的自动变量。 您可以使用此变量来表示命令和脚本中缺少的值或未定义的值。

PowerShell 将视为 `$null` 具有值的对象（即，作为显式占位符），因此可以使用 `$null` 来表示一系列值中的空值。

例如，当 `$null` 包含在集合中时，会将其计为一个对象。

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

如果通过管道将 `$null` 变量传递给 `ForEach-Object` cmdlet，它会为生成一个值 `$null` ，就像对其他对象执行此方法一样。

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

因此，不能使用 `$null` 来表示 **没有参数值**。 参数值 `$null` 覆盖默认参数值。

但是，因为 PowerShell 将 `$null` 变量视为占位符，所以可以在脚本中使用它，如果忽略，这将不起作用 `$null` 。

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

包含承载当前 PowerShell 会话的进程的进程标识符 (PID) 。

### <a name="profile"></a>$PROFILE

包含当前用户和当前主机应用程序的 PowerShell 配置文件的完整路径。 您可以使用此变量来表示命令中的配置文件。 例如，你可以在命令中使用它来确定是否已创建配置文件：

```powershell
Test-Path $PROFILE
```

或者，你可以在命令中使用它来创建配置文件：

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

可以在命令中使用它在 **notepad.exe** 中打开配置文件：

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

包含传递给脚本或函数的参数的字典及其当前值。 此变量仅在声明参数的作用域（如脚本或函数）中具有值。 您可以使用它显示或更改参数的当前值，或者将参数值传递给其他脚本或函数。

在此示例中， **Test2** 函数将传递 `$PSBoundParameters` 给 **Test1** 函数。 `$PSBoundParameters`以 **键** 和 **值** 的格式显示。

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

包含一个对象，该对象表示正在运行的 cmdlet 或高级函数。

你可以使用 cmdlet 或函数代码中的对象的属性和方法来响应使用情况。 例如， **ParameterSetName** 属性包含所使用的参数集的名称， **ShouldProcess** 方法会动态地将 **WhatIf** 和 **Confirm** 参数添加到 cmdlet。

有关自动变量的详细信息 `$PSCmdlet` ，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。

### <a name="pscommandpath"></a>$PSCommandPath

包含正在运行的脚本的完整路径和文件名。 此变量在所有脚本中都有效。

### <a name="psculture"></a>$PSCulture

从 PowerShell 7 开始， `$PSCulture` 反映当前 PowerShell 运行空间的区域性 (会话) 。 如果在 PowerShell 运行空间中更改了区域性，则将 `$PSCulture` 更新该运行空间的值。

区域性确定项的显示格式（例如数字、货币和日期），并将其存储在 **system.exception 对象中。** 用于 `Get-Culture` 显示计算机的区域性。 `$PSCulture` 包含 **名称** 属性的值。

### <a name="psdebugcontext"></a>$PSDebugContext

调试时，此变量包含有关调试环境的信息。 否则，它将包含 **null** 值。 因此，你可以使用它来指示调试器是否具有控件。 填充后，它将包含一个 **PsDebugContext** 对象，该对象具有 **断点** 和 **InvocationInfo** 属性。 **InvocationInfo** 属性具有多个有用的属性，包括 **Location** 属性。 **Location** 属性指示正在调试的脚本的路径。

### <a name="pshome"></a>$PSHOME

包含适用于 PowerShell 的安装目录的完整路径，通常是 `$env:windir\System32\PowerShell\v1.0` 在 Windows 系统中。 可以在 PowerShell 文件的路径中使用此变量。 例如，下面的命令在概念帮助主题中搜索 word **变量**：

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

与 `$_` 相同。 包含管道对象中的当前对象。 可以在对每个对象或管道中的选定对象执行操作的命令中使用此变量。

### <a name="psscriptroot"></a>$PSScriptRoot

包含正在从中运行脚本的目录。

在 PowerShell 2.0 中，此变量仅在) 的脚本模块中有效 (`.psm1` 。
从 PowerShell 3.0 开始，它在所有脚本中都有效。

### <a name="pssenderinfo"></a>$PSSenderInfo

包含有关启动 PSSession 的用户的信息，其中包括源计算机的用户标识和时区。 此变量仅在 Pssession 中可用。

此 `$PSSenderInfo` 变量包含一个用户可配置的属性 **ApplicationArguments**，默认情况下，该属性仅包含 `$PSVersionTable` 来自原始会话的。 若要将数据添加到 **ApplicationArguments** 属性，请使用 Cmdlet 的 **ApplicationArguments** 参数 `New-PSSessionOption` 。

### <a name="psuiculture"></a>$PSUICulture

包含操作系统中当前正在使用的 (UI) 区域性的用户界面的名称。 UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。 这是系统的 **System.Globalization.CultureInfo.CurrentUICulture.Name** 属性的值。 若要获取 **系统的 system.servicemodel 对象，** 请使用 `Get-UICulture` cmdlet。

### <a name="psversiontable"></a>$PSVersionTable

包含一个只读的哈希表，该表显示有关当前会话中正在运行的 PowerShell 版本的详细信息。 该表包含以下各项：

| 属性                  | 说明                                   |
| ------------------------- | --------------------------------------------- |
| **PSVersion**             | PowerShell 版本号                 |
| **PSEdition**             | 此属性的值为 "Desktop"  |
|                           | PowerShell 4 及更低  |
|                           | 5.1 功能齐全的 Windows 版本。        |
|                           | 此属性的值为 "Core"     |
|                           | PowerShell 6 及更高版本以及 PowerShell  |
|                           | 精简版的小型版本上的 PowerShell 5。1  |
|                           | 类似于 Windows Nano Server 或 Windows IoT。      |
| **GitCommitId**           | GitHub 中的源文件的提交 Id |
| **OS**                    | 操作系统的说明      |
|                           | PowerShell 正在上运行。                     |
| **平台**              | 操作系统正在运行的平台 |
|                           | 如果 Linux 和 macOS 上的值为 **Unix**。 |
|                           | 请参见 `$IsMacOs` 和 `$IsLinux`。                |
| **PSCompatibleVersions**  | 兼容的 PowerShell 版本    |
|                           | 与当前版本                      |
| **PSRemotingProtocolVersion** | PowerShell 远程的版本      |
|                           | 管理协议。                          |
| **SerializationVersion**  | 序列化方法的版本       |
| **WSManStackVersion**     | WS-Management 堆栈的版本号 |

### <a name="pwd"></a>$PWD

包含表示当前目录的完整路径的路径对象。

### <a name="sender"></a>$Sender

包含生成此事件的对象。 此变量仅在事件注册命令的操作块中进行填充。 此变量的值还可在返回的 **PSEventArgs** 对象的发送方属性中找到 `Get-Event` 。

### <a name="shellid"></a>$ShellId

包含当前 shell 的标识符。

### <a name="stacktrace"></a>$StackTrace

包含最新错误的堆栈跟踪。

### <a name="switch"></a>$switch

包含枚举器，而不包含语句的结果值 `Switch` 。 `$switch`仅当语句正在运行时，才存在该变量 `Switch` ; 当语句完成执行时，该变量会被删除 `switch` 。 有关详细信息，请参阅 [about_Switch](about_Switch.md)。

枚举器包含可用于检索循环值和更改当前循环迭代的属性和方法。 有关详细信息，请参阅 [使用枚举](#using-enumerators)器。

### <a name="this"></a>$this

在定义脚本属性或脚本方法的脚本块中， `$this` 变量引用要扩展的对象。

在自定义类中， `$this` 变量引用类对象本身，以允许访问类中定义的属性和方法。

### <a name="true"></a>$true

包含 **True**。 可以在命令和脚本中使用此变量来表示 **True** 。

## <a name="using-enumerators"></a>使用枚举器

`$input`、 `$foreach` 和 `$switch` 变量是所有枚举器，用于循环访问由其包含代码块处理的值。

枚举器包含可用于提前或重置迭代或检索迭代值的属性和方法。 直接操作枚举器并不是最佳做法。

- 在循环中，应首选流控制关键字 " [中断](about_Break.md) 并 [继续](about_Continue.md) "。
- 在接受管道输入的函数中，最佳做法是将参数与 **ValueFromPipeline** 或 **ValueFromPipelineByPropertyName** 属性结合使用。

  有关详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="movenext"></a>MoveNext

[MoveNext](/dotnet/api/system.collections.ienumerator.movenext)方法将枚举器推进到集合的下一个元素。 如果枚举器已成功进行高级，则 **MoveNext** 返回 **True** ; 如果枚举数已越过集合的末尾，则返回 **False** 。

> [!NOTE]
> 返回的 **布尔** 值会将我的 **MoveNext** 发送到输出流。
> 可以通过将输出 typecasting 为 `[void]` 或将其传送到 [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null)来禁止输出。
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>重置

[Reset](/dotnet/api/system.collections.ienumerator.reset)方法将枚举器设置为其初始位置，该位置位于集合中第一个元素 **之前**。

### <a name="current"></a>当前

[当前](/dotnet/api/system.collections.ienumerator.current)属性获取集合中的元素或管道中的枚举器的当前位置。

**当前** 属性将继续返回相同的属性，直到调用 **MoveNext** 。

## <a name="examples"></a>示例

### <a name="example-1-using-the-input-variable"></a>示例1：使用 $input 变量

在下面的示例中，访问 `$input` 变量将清除变量，直到下一次执行进程块。 使用 **Reset** 方法会将变量重置 `$input` 为当前管道值。

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

即使不访问变量，进程块也会自动推进该 `$input` 变量。

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>示例2：在进程块外使用 $input

在进程块外，该 `$input` 变量表示通过管道传递到函数中的所有值。

- 访问 `$input` 变量将清除所有值。
- **Reset** 方法重置整个集合。
- 从未填充 **当前** 属性。
- **MoveNext** 方法返回 false，因为集合不能为高级。
  - 调用 **MoveNext** 会清除该 `$input` 变量。

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>示例3：使用 $input。当前属性

通过使用 **当前** 属性，可以多次访问当前管道值，而无需使用 **Reset** 方法。 进程块不会自动调用 **MoveNext** 方法。

除非显式调用 **MoveNext**，否则不会填充 **当前** 属性。 **当前** 属性可以在进程块内多次访问，而无需清除其值。

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>示例4：使用 $foreach 变量

与 `$input` 变量不同，在 `$foreach` 直接访问时，变量始终表示集合中的所有项。 使用 **current** 属性可以访问当前集合元素，使用 **Reset** 和 **MoveNext** 方法可以更改其值。

> [!NOTE]
> 循环的每次迭代 `foreach` 都将自动调用 **MoveNext** 方法。

以下循环只执行两次。 在第二次迭代中，在迭代完成之前，将集合移动到第三个元素。 在第二次迭代后，现在没有更多值可供迭代，循环将终止。

**MoveNext** 属性不影响所选择的用于循环访问集合的变量 (`$Num`) 。

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

使用 **Reset** 方法重置集合中的当前元素。 下面的示例循环遍历前两个元素 **两次** ，因为调用 **Reset** 方法。 在前两个循环之后， `if` 语句将失败，并且循环会正常地循环访问所有三个元素。

> [!IMPORTANT]
> 这可能会导致无限循环。

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>示例5：使用 $switch 变量

`$switch`变量与变量具有完全相同的规则 `$foreach` 。
下面的示例演示了所有枚举器概念。

> [!NOTE]
> 请注意， 即使在 `break` **MoveNext** 方法后面没有语句，也不会执行 NotEvaluated 事例。

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>另请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

