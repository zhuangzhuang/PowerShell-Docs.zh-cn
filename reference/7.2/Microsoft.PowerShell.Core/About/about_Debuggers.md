---
description: 介绍 PowerShell 调试器。
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 46914937cebdf8cf3559371f354bf14cd6706115
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598082"
---
# <a name="about-debuggers"></a>关于调试器

## <a name="short-description"></a>简短说明
介绍 PowerShell 调试器。

## <a name="long-description"></a>详细说明

调试是检查正在运行的脚本的过程，用于识别和更正脚本指令中的错误。 PowerShell 调试器可帮助你检查和确定脚本、函数、命令、PowerShell Desired State Configuration (DSC) 配置或表达式中的错误和低效。

从 PowerShell 5.0 开始，已更新 PowerShell 调试器，以调试在远程计算机上的控制台或 Windows PowerShell ISE 中运行的脚本、函数、命令、配置或表达式。 您可以运行 `Enter-PSSession` 以启动交互式远程 PowerShell 会话，在该会话中，您可以在远程计算机上设置断点以及调试脚本文件和命令。 `Enter-PSSession` 已更新功能，使你可以重新连接到并进入远程计算机上运行脚本或命令的断开连接的会话。 如果正在运行的脚本命中了断点，则客户端会话会自动启动调试器。 如果运行脚本的断开连接的会话已命中断点，并在断点处停止， `Enter-PSSession` 则在重新连接到该会话之后，将自动启动命令行调试器。

使用 PowerShell 调试器的功能，可以在 PowerShell 脚本、函数、命令或表达式运行时对其进行检查。 PowerShell 调试器包含一组 cmdlet，可用于设置断点、管理断点和查看调用堆栈。

## <a name="debugger-cmdlets"></a>调试器 Cmdlet

PowerShell 调试器包含以下 cmdlet 集：

- `Set-PSBreakpoint`：对行、变量和命令设置断点。
- `Get-PSBreakpoint`：获取当前会话中的断点。
- `Disable-PSBreakpoint`：关闭当前会话中的断点。
- `Enable-PSBreakpoint`：在当前会话中重新启用断点。
- `Remove-PSBreakpoint`：从当前会话中删除断点。
- `Get-PSCallStack`：显示当前的调用堆栈。

## <a name="starting-and-stopping-the-debugger"></a>启动和停止调试器

若要启动调试器，请设置一个或多个断点。 然后，运行要调试的脚本、命令或函数。

到达断点时，将停止执行，并将控制权转变成调试器。

若要停止调试器，请运行脚本、命令或函数，直到完成。 或者，键入 `stop` 或 `t` 。

### <a name="debugger-commands"></a>调试器命令

在 PowerShell 控制台中使用调试程序时，请使用以下命令来控制执行。 在 Windows PowerShell ISE 中，使用 "调试" 菜单上的命令。

注意：有关如何在其他宿主应用程序中使用调试器的信息，请参阅宿主应用程序文档。

- `s`， `StepInto` ：执行下一个语句，然后停止。

- `v`， `StepOver` ：执行下一语句，但跳过函数和调用。 将执行跳过的语句，但不会单步遍历。

- `Ctrl+Break`： (将 ISE 中的所有项全部中断) 在 PowerShell 控制台内进入正在运行的脚本，或者 Windows PowerShell ISE。 请注意<kbd></kbd>， + 在 Windows PowerShell 2.0、3.0 和4.0 中的 Ctrl<kbd>Break</kbd>会关闭程序。 全部中断都适用于本地和远程运行的脚本。

- `o`， `StepOut` ：跳出当前函数; 如果嵌套，则为一级。 如果在主体中，它将继续到末尾或下一个断点。 将执行跳过的语句，但不会单步遍历。

- `c``Continue`：将继续运行，直到脚本完成，或者到达下一个断点。 将执行跳过的语句，但不会单步遍历。

- `l``List`：显示正在执行的脚本部分。 默认情况下，它显示当前行、前面的五行和10个后续行。
  若要继续列出脚本，请按 ENTER。

- `l <m>``List`：显示以指定的行号开头的16行脚本 `<m>` 。

- `l <m> <n>``List`：显示 `<n>` 脚本的行，以指定的行号开头 `<m>` 。

- `q`、 `Stop` 、 `Exit` ：停止执行脚本，并退出调试器。 如果正在通过运行 cmdlet 调试作业 `Debug-Job` ，则该命令将 `Exit` 分离调试器，并允许作业继续运行。

- `k``Get-PsCallStack`：显示当前调用堆栈。

- `<Enter>`：如果为 Step (s) 、跨距 (v) 或 List (l) ，则重复最后一个命令。 否则，表示提交操作。

- `?``h`：显示调试器命令帮助。

若要退出调试器，可以使用 Stop (q) 。

从 PowerShell 5.0 开始，可以运行 Exit 命令，以退出通过运行或启动的嵌套调试会话 `Debug-Job` `Debug-Runspace` 。

通过使用这些调试程序命令，你可以运行脚本，在关注点时停止，检查变量的值和系统状态，然后继续运行脚本，直到发现问题为止。

注意：如果单步执行包含重定向运算符（如 ">"）的语句，则 PowerShell 调试器会逐过程执行该脚本中的所有剩余语句。

显示脚本变量的值

在调试器中时，还可以在命令行中输入命令、显示变量值、使用 cmdlet 和运行脚本。

除了以下自动变量以外，你还可以在正在调试的脚本中显示所有变量的当前值：

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

如果你尝试显示这些变量中的任何一个的值，你将获取调试器使用的内部管道中变量的值，而不是脚本中变量的值。

若要为正在调试的脚本显示这些变量的值，请在脚本中，将自动变量的值分配给一个新变量。 然后，可以显示新变量的值。

例如，应用于对象的

```powershell
$scriptArgs = $Args
$scriptArgs
```

在本主题的示例中，变量的值 `$MyInvocation` 是重新分配的，如下所示：

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>调试器环境

到达断点时，将进入调试器环境。 命令提示符将发生更改，使其以 "[DBG]：" 开头。

有关自定义提示的详细信息，请参阅 [about_Prompts](about_prompts.md)。

此外，在某些主机应用程序（例如 PowerShell 控制台）中， (但不在 Windows PowerShell 集成脚本环境 [ISE] ) 中，会打开一个嵌套提示来进行调试。 您可以通过在命令提示符下出现 (ASCII 62) 的重复大于字符来检测嵌套提示。

例如，以下是 PowerShell 控制台中的默认调试提示：

```
[DBG]: PS (get-location)>>>
```

您可以通过使用自动变量来查找嵌套级别 `$NestedPromptLevel` 。

此外，自动变量 `$PSDebugContext` 在本地范围中定义。 您可以使用变量的状态 `$PsDebugContext` 来确定是否在调试器中。

例如：

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

您可以 `$PSDebugContext` 在调试中使用变量的值。

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>调试和作用域

中断调试器不会更改您在其中运行的范围，但当您在脚本中到达断点时，将移动到脚本范围。 脚本作用域是运行调试器的作用域的子级。

若要查找在脚本作用域中定义的变量和别名，请使用或 cmdlet 的作用域参数 `Get-Alias` `Get-Variable` 。

例如，以下命令将获取本地 (脚本) 范围中的变量：

```powershell
Get-Variable -scope 0
```

可以将命令缩写为：

```powershell
gv -s 0
```

这是一种非常有用的方法，用于仅查看您在脚本中定义的变量以及在调试时定义的变量。

在命令行调试

设置变量断点或命令断点时，只能在脚本文件中设置断点。 但是，默认情况下，将在当前会话中运行的任何内容上设置断点。

例如，如果您在变量上设置了断点 `$name` ，则调试器将在 `$name` 您禁用或删除断点之前运行的任何脚本、命令、函数、脚本 cmdlet 或表达式中的任何变量上中断。

这使您可以在一个更现实的上下文中调试脚本，这些脚本可能会受到会话中和用户配置文件中的函数、变量和其他脚本的影响。

行断点特定于脚本文件，因此它们只在脚本文件中进行设置。

## <a name="debugging-functions"></a>调试函数

在具有、和部分的函数上设置断点 `Begin` 时 `Process` `End` ，调试器会在每个部分的第一行处中断。

例如：

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a>调试远程脚本

从 PowerShell 5.0 开始，你可以在远程会话、控制台或 Windows PowerShell ISE 中运行 PowerShell 调试器。
`Enter-PSSession` 已更新功能，使你可以重新连接到并输入远程计算机上运行的断开连接的会话，并且当前正在运行脚本。 如果正在运行的脚本命中了断点，则客户端会话会自动启动调试器。

下面是一个示例，演示了如何工作，并在脚本的第6、11、22和25行中设置了断点。 请注意，在该示例中，当调试器启动时，有两个标识提示：正在运行会话的计算机的名称，以及可让您了解处于调试模式的 DBG 提示。

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a>示例

此测试脚本检测操作系统的版本，并显示系统相应的消息。 它包括函数、函数调用和变量。

以下命令显示测试脚本文件的内容：

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

若要开始，请在脚本中的相关点设置断点，例如行、命令、变量或函数。

首先在当前目录中 Test.ps1 脚本的第一行上创建行断点。

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

可将此命令缩写为：

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

命令返回 (**system.management.automation.linebreakpoint**) 的行断点对象。

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

现在，启动脚本。

```powershell
PS C:\ps-test> .\test.ps1
```

当脚本到达第一个断点时，断点消息指示调试器处于活动状态。 它描述断点并预览脚本的第一行（即函数声明）。 命令提示符还会发生更改，以指示调试器具有控制。

预览行包括脚本名称和预览命令的行号。

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

使用 Step 命令 (s) 执行脚本中的第一条语句并预览下一条语句。 下一条语句使用 `$MyInvocation` 自动变量将该变量的值设置 `$scriptName` 为该脚本文件的路径和文件名。

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

此时， `$scriptName` 不会填充变量，但可以通过显示变量值来验证变量的值。 在本例中，该值为 `$null`。

```powershell
DBG> $scriptname
# DBG>
```

使用另一个步骤命令 (s) 执行当前语句并预览脚本中的下一个语句。 下一条语句将调用 PsVersion 函数。

```powershell
DBG> s
test.ps1:12  psversion
```

此时，将 `$scriptName` 填充变量，但通过显示变量值来验证变量的值。 在这种情况下，值设置为脚本路径。

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

使用另一个步骤命令执行函数调用。 按 ENTER，或键入 "s" 进行步骤。

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

调试消息包括函数中语句的预览。 若要执行此语句并预览函数中的下一条语句，可以使用 `Step` 命令。 但在这种情况下，请使用 (o) 的 StepOut 命令。 它将完成函数的执行 (除非该函数到达断点) 并执行该脚本中的下一条语句。

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

由于我们在脚本中的最后一个语句上，因此 "Step"、"StepOut" 和 "Continue" 命令具有相同的效果。 在这种情况下，请使用 StepOut (o) 。

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

StepOut 命令执行最后一个命令。 标准命令提示符指示调试器已退出并返回到命令处理器。

现在，再次运行调试器。 首先，若要删除当前断点，请使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` cmdlet。  (如果你认为可能重复使用该断点，则使用 `Disable-PsBreakpoint` cmdlet 而不是 `Remove-PsBreakpoint` 。 ) 

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

可将此命令缩写为：

```powershell
PS C:\ps-test> gbp | rbp
```

或者，通过编写函数来运行命令，如以下函数：

```powershell
function delbr { gbp | rbp }
```

现在，请在变量上创建断点 `$scriptname` 。

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

可以将命令缩写为：

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

现在，启动脚本。 脚本将到达变量断点。 默认模式是 "写入"，因此，在更改变量的值的语句之前，执行将停止。

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

显示变量的当前值 `$scriptName` ，即 `$null` 。

```powershell
DBG> $scriptName
# DBG>
```

使用步骤命令 (s) 执行填充变量的语句。
然后，显示变量的新值 `$scriptName` 。

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

下一条语句是对 PsVersion 函数的调用。 若要跳过函数但仍执行该函数，请使用跨距命令 (v) 。 如果使用跨距时已在该函数中，则无效。 将显示函数调用，但不执行它。

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

跨距命令执行该函数，并预览脚本中的下一条语句，该语句将输出最后一行。

使用 Stop 命令 (t) 退出调试器。 命令提示符会恢复为标准命令提示符。

```powershell
C:\ps-test>
```

若要删除断点，请使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` cmdlet。

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

在 PsVersion 函数上创建新的命令断点。

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

可以将此命令缩写为：

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

现在，运行该脚本。

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

脚本在函数调用时到达断点。 此时，尚未调用函数。 这使您有机会使用的操作参数 `Set-PSBreakpoint` 设置断点的执行条件，或执行准备或诊断任务，如启动日志或调用诊断或安全脚本。

若要设置操作，请使用 Continue 命令 (c) 退出脚本，并使用 `Remove-PsBreakpoint` 命令删除当前断点。  (断点是只读的，因此无法将操作添加到当前断点。 ) 

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

现在，使用操作创建新的命令断点。 下面的命令使用 `$scriptName` 在调用函数时记录变量值的操作设置命令断点。 由于操作中未使用 Break 关键字，因此执行不会停止。  (反撇号 (') 为行继续符。 ) 

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

你还可以添加为断点设置条件的操作。 在下面的命令中，仅当执行策略设置为 RemoteSigned （仍允许运行脚本的最严格的策略）时，才执行命令断点。  (反撇号 (") 是继续符。 ) 

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

操作中的 Break 关键字指示调试器执行断点。
你还可以使用 Continue 关键字指示调试器无中断地执行。 由于 default 关键字为 Continue，因此必须指定 Break 来停止执行。

现在，运行该脚本。

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

由于执行策略设置为 **RemoteSigned**，因此会在函数调用处停止执行。

此时，你可能需要检查调用堆栈。 使用 `Get-PsCallStack` cmdlet 或 `Get-PsCallStack` 调试器命令 (k) 。 以下命令将获取当前调用堆栈。

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

此示例演示了使用 PowerShell 调试器的多种方法中的几种方法。

有关调试器 cmdlet 的详细信息，请键入以下命令：

```powershell
help <cmdlet-name> -full
```

例如，键入：

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>PowerShell 中的其他调试功能

除了 PowerShell 调试程序外，PowerShell 还包括可用于调试脚本和函数的多个其他功能。

- Windows PowerShell ISE 包含交互式图形调试器。 有关详细信息，请启动 Windows PowerShell ISE 并按 F1。

- `Set-PSDebug`Cmdlet 提供了非常基本的脚本调试功能，包括单步执行和跟踪。

- 使用 `Set-StrictMode` cmdlet 来检测对未初始化的变量的引用、对对象的不存在属性的引用以及函数无效的语法。

- 将诊断语句添加到脚本，例如显示变量值的语句、从命令行读取输入的语句或报告当前说明的语句。 使用包含此任务的写入谓词的 cmdlet，例如 `Write-Host` 、、 `Write-Debug` `Write-Warning` 和 `Write-Verbose` 。

## <a name="see-also"></a>另请参阅

- [Set-psbreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [Set-psbreakpoint](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [Set-psbreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get-pscallstack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [Set-psbreakpoint](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

