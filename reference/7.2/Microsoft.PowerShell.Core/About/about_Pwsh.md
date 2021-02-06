---
description: 说明如何使用 `pwsh` 命令行界面。 显示命令行参数并描述语法。
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: b31563dd7058d85eb76f34c61d9bff5558a786b0
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "99596828"
---
# <a name="about-pwsh"></a>关于 pwsh

## <a name="short-description"></a>简短说明
说明如何使用 `pwsh` 命令行界面。 显示命令行参数并描述语法。

## <a name="long-description"></a>详细说明

## <a name="syntax"></a>语法

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a>参数

所有参数都不区分大小写。

### <a name="-file---f"></a>-File |-f

如果的值 `File` 为 `-` ，则从标准输入读取命令文本。
运行时 `pwsh -File -` 不使用重定向标准输入会启动常规会话。 这与根本不指定 `File` 参数相同。

如果不存在任何参数，但命令行中存在值，则这是默认参数。 指定的脚本在本地作用域中运行 ( "点端" ) ，以便脚本创建的函数和变量在当前会话中可用。 输入脚本文件路径和任何参数。 File 必须是命令中的最后一个参数，因为在文件参数名称后键入的所有字符都会被解释为后跟脚本参数的脚本文件路径。

通常，将包括或忽略脚本的开关参数。
例如，以下命令使用 Get-Script.ps1 脚本文件的 All 参数： `-File .\Get-Script.ps1 -All`

在极少数情况下，可能需要为开关参数提供一个 **布尔** 值。 若要在 **File** 参数的值中为开关参数提供 **布尔** 值，请使用后面紧跟冒号和布尔值的参数，如下所示： `-File .\Get-Script.ps1 -All:$False` 。

传递给脚本的参数作为文字字符串（在当前 shell 的解释后）传递。 例如，如果你在中， `cmd.exe` 并且想要传递环境变量值，则应使用 `cmd.exe` 语法： `pwsh -File .\test.ps1 -TestParam %windir%`

相反，在脚本中运行将 `pwsh -File .\test.ps1 -TestParam $env:windir` `cmd.exe` 导致接收文本字符串， `$env:windir` 因为它对当前 shell 没有特殊意义 `cmd.exe` 。 `$env:windir`_可以_ 在 **命令** 参数中使用环境变量引用的样式，因为它被解释为 PowerShell 代码。

同样，如果您想要从 _批处理脚本_ 执行相同的命令，则可以使用 `%~dp0` 而不是 `.\` 或 `$PSScriptRoot` 来表示当前执行目录： `pwsh -File %~dp0test.ps1 -TestParam %windir%` 。 如果你使用 `.\test.ps1` ，则 PowerShell 将引发错误，因为它无法找到文本路径 `.\test.ps1`

当脚本文件以命令结束时 `exit` ，进程退出代码将设置为与命令一起使用的数值参数 `exit` 。 如果正常终止，则始终会出现退出代码 `0` 。

类似于 `-Command` ，当发生脚本终止错误时，退出代码将设置为 `1` 。 不过，与不同的 `-Command` 是，在通过<kbd>Ctrl</kbd>C 中断执行时， - <kbd></kbd>退出代码为 `0` 。

### <a name="-command---c"></a>-Command |-c

执行指定的命令 (和任何) 参数，如同在 PowerShell 命令提示符下键入一样，然后退出，除非 `NoExit` 指定了参数。

**Command** 的值可以是 `-` 、脚本块或字符串。 如果 **command** 的值为，则将 `-` 从标准输入读取命令文本。

仅当 **命令** 参数可以将传递给 **Command** 的值识别为 **ScriptBlock** 类型时，才接受脚本块执行。 _仅_ 当 `pwsh` 从另一个 PowerShell 主机运行时，才可能出现这种情况。 **ScriptBlock** 类型可能包含在从表达式返回的现有变量中，或由 PowerShell 主机分析为括在大括号中的文本脚本块 (`{}`) ，然后再传递到 `pwsh` 。

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

在中 `cmd.exe` ，没有脚本块 (或 **ScriptBlock** 类型) ，因此传递给 **Command** 的值 _始终_ 为字符串。 可以在字符串中编写一个脚本块，但它不会被执行，该脚本块的行为与你在典型 PowerShell 提示符中键入它的行为完全相同，即将脚本块内容输出出来返还给你。

传递给 **命令** 的字符串仍作为 PowerShell 代码执行，因此，在从运行时，在第一位置通常不需要脚本块大括号 `cmd.exe` 。 要执行在字符串中定义的内联脚本块，可以使用[调用操作符](about_operators.md#special-operators) `&`：

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

如果 **command** 的值为字符串，则 **command** 必须是 pwsh 的最后一个参数，因为其后面的所有参数都将解释为要执行的命令的一部分。

从现有 PowerShell 会话内调用时，结果将作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。 对于其他 shell，结果将作为字符串返回。

如果 **command** 的值为，则将 `-` 从标准输入读取命令文本。 使用带有标准输入的 **命令** 参数时，必须重定向标准输入。 例如：

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

该示例产生下面的输出：

```Output
in
hi there
out
```

进程退出代码由脚本块内最后 (执行) 命令的状态确定。 退出代码为 `0` 时为 `$?` `$true` 或 `1` 何时为时 `$?` `$false` 。 如果最后一个命令是外部程序或 PowerShell 脚本，它显式设置除或之外的退出代码 `0` `1` ，则会将该退出代码转换为以 `1` 处理退出代码。 若要保留特定退出代码，请将添加 `exit $LASTEXITCODE` 到命令字符串或脚本块。

同样，当脚本终止 (运行空间终止) 错误（如或）时，将返回值1， `throw` `-ErrorAction Stop` 或在使用<kbd>Ctrl</kbd> - <kbd>C</kbd>中断执行时进行。

### <a name="-configurationname---config"></a>-ConfigurationName |-config

指定运行 PowerShell 的配置终结点。 这可以是在本地计算机上注册的任何终结点，包括默认 PowerShell 远程处理终结点或具有特定用户角色功能的自定义终结点。

示例： `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

指定用于调试的额外 IPC 服务器 (命名管道) 使用的名称，以及其他跨进程通信。 这提供了一种可预测的连接到其他 PowerShell 实例的机制。 通常与上的 **CustomPipeName** 参数一起使用 `Enter-PSHostProcess` 。

此参数是在 PowerShell 6.2 中引入的。

例如：

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand |-e |-ec

接受命令的 Base64 编码字符串版本。 使用此参数将命令提交到需要复杂的嵌套引号的 PowerShell。 Base64 表示形式必须为 UTF-16LE 编码的字符串。

例如：

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-Set-executionpolicy |-ex |-ep

为当前会话设置默认执行策略，并将其保存在 `$env:PSExecutionPolicyPreference` 环境变量中。 此参数不会更改永久配置的执行策略。

此参数仅适用于 Windows 计算机。 `$env:PSExecutionPolicyPreference`环境变量在非 Windows 平台上不存在。

### <a name="-inputformat---inp---if"></a>-InputFormat |-sct.inp |-如果

描述发送到 PowerShell 的数据格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

### <a name="-interactive---i"></a>-Interactive |-i

向用户显示交互式提示。 非交互式参数的反向。

### <a name="-login---l"></a>-Login |-l

在 Linux 和 macOS 上，启动 PowerShell 作为登录 shell，使用/bin/sh 执行登录配置文件，例如/etc/profile 和 ~/.profile。
在 Windows 上，此开关不会执行任何操作。

> [!IMPORTANT]
> 此参数必须首先作为登录 shell 启动 PowerShell。
> 在另一个位置传递此参数将被忽略。

`pwsh`在类似于 UNIX 的操作系统上将设置为登录 shell：

- 验证下面列出了的完整绝对路径 `pwsh``/etc/shells`
  - 此路径通常类似于 `/usr/bin/pwsh` Linux 或 macOS 上的内容。 `/usr/local/bin/pwsh`
  - 对于某些安装方法，将在安装时自动添加此项
  - 如果 `pwsh` 在中不存在 `/etc/shells` ，请使用编辑器将路径追加到 `pwsh` 最后一行。 这需要提升的权限才能进行编辑。
- 使用 [chsh](https://linux.die.net/man/1/chsh) 实用工具将当前用户的 shell 设置为 `pwsh` ：

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> `pwsh`当前在适用于 Linux 的 Windows 子系统 (WSL) 上不支持设置为登录 shell，因此尝试将设置 `pwsh` 为登录 shell 可能会导致无法以交互方式启动 WSL。

### <a name="-mta"></a>-MTA

使用多线程单元启动 PowerShell。 此开关仅在 Windows 上可用。

### <a name="-noexit---noe"></a>-NoExit |-noe

运行启动命令后不退出。

示例： `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-NoLogo |-nol

交互式会话启动时隐藏版权横幅。

### <a name="-noninteractive---noni"></a>-非交互式 |-noni

不向用户显示交互式提示。 尝试使用交互式功能（如 `Read-Host` 或确认提示）会导致语句终止错误。

### <a name="-noprofile---nop"></a>-NoProfile |-nop

不加载 PowerShell 配置文件。

### <a name="-outputformat---o---of"></a>-OutputFormat |-o |-of

确定 PowerShell 输出内容的格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

示例： `pwsh -o XML -c Get-Date`

在 PowerShell 会话限调用时，会将反序列化的对象作为输出而不是纯字符串获取。 从其他 shell 调用时，输出是格式为 EXPORT-CLIXML 文本的字符串数据。

### <a name="-settingsfile---settings"></a>-SettingsFile |-设置

替代会话的系统范围 `powershell.config.json` 设置文件。 默认情况下，系统范围内的设置将从 `powershell.config.json` 目录中的中读取 `$PSHOME` 。

请注意，参数指定的终结点不使用这些设置 `-ConfigurationName` 。

示例： `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode |-sshs

用于在 sshd_config 中将 PowerShell 作为 SSH 子系统运行。 对于任何其他用途，不建议使用或支持。

### <a name="-sta"></a>-STA

使用单线程单元启动 PowerShell。 这是默认设置。 此开关仅在 Windows 上可用。

### <a name="-version---v"></a>-版本 |-v

显示 PowerShell 的版本。 其他参数将被忽略。

### <a name="-windowstyle---w"></a>-WindowStyle |-w

为会话设置窗口样式。 有效值包括 Normal、Minimized、Maximized 和 Hidden。

### <a name="-workingdirectory---wd"></a>-WorkingDirectory |-wd

设置在启动时执行的初始工作目录。 支持任何有效的 PowerShell 文件路径。

若要在主目录中启动 PowerShell，请使用： `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>-Help、-?、/?

显示的帮助 `pwsh` 。 如果要在 PowerShell 中键入 pwsh 命令，请在命令参数前面添加连字符 (`-`) ，而不是 () 的正斜杠 `/` 。
