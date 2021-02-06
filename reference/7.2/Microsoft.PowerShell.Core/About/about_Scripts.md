---
description: 介绍如何在 PowerShell 中运行和编写脚本。
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: 2fc81d1d43b8cdddaacb917deaa5d58536a541cb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597679"
---
# <a name="about-scripts"></a>关于脚本

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中运行和编写脚本。

## <a name="long-description"></a>长说明

脚本是一种纯文本文件，其中包含一个或多个 PowerShell 命令。
PowerShell 脚本具有 `.ps1` 文件扩展名。

运行脚本非常类似于运行 cmdlet。 键入脚本的路径和文件名，并使用参数提交数据并设置选项。 您可以在您的计算机上或在其他计算机上的远程会话中运行脚本。

编写脚本时，将保存一个命令以供以后使用，并使与他人共享。 最重要的是，它只需键入脚本路径和文件名即可运行命令。 脚本可以像文件中的单个命令一样简单，也可以是复杂的程序。

脚本具有其他功能，如 `#Requires` 特殊注释、参数的使用、对数据部分的支持和用于安全设置的数字签名。
你还可以为脚本和脚本中的任何函数编写帮助主题。

## <a name="how-to-run-a-script"></a>如何运行脚本

你需要更改默认 PowerShell 执行策略，然后才能在 Windows 上运行脚本。 执行策略不适用于在非 Windows 平台上运行的 PowerShell。

默认执行策略 `Restricted` 会阻止所有脚本运行，包括在本地计算机上编写的脚本。 有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

执行策略保存在注册表中，因此只需在每台计算机上更改一次。

若要更改执行策略，请使用以下过程。

在命令提示符处，键入：

```powershell
Set-ExecutionPolicy AllSigned
```

或

```powershell
Set-ExecutionPolicy RemoteSigned
```

更改立即生效。

若要运行脚本，请键入该脚本文件的完整名称和完整路径。

例如，若要在 C：\Scripts 目录中运行 Get-ServiceLog.ps1 脚本，请键入：

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

若要在当前目录中运行脚本，请键入当前目录的路径，或使用点表示当前目录，然后使用路径反斜杠 (`.\`) 。

例如，若要在本地目录中运行 ServicesLog.ps1 脚本，请键入：

```powershell
.\Get-ServiceLog.ps1
```

如果脚本中包含参数，请在脚本文件名后面键入参数和参数值。

例如，以下命令使用 Get-ServiceLog 脚本的 ServiceName 参数来请求 WinRM 服务活动的日志。

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

作为一项安全功能，当你在文件资源管理器中双击脚本图标时，或在不使用完整路径的情况下键入脚本名称（即使脚本位于当前目录中时），PowerShell 不会运行脚本。 有关在 PowerShell 中运行命令和脚本的详细信息，请参阅 [about_Command_Precedence](about_Command_Precedence.md)。

### <a name="run-with-powershell"></a>使用 PowerShell 运行

从 PowerShell 3.0 开始，你可以从文件资源管理器运行脚本。

若要使用 "使用 PowerShell 运行" 功能：

运行文件资源管理器，右键单击脚本文件名，然后选择 "用 PowerShell 运行"。

"使用 PowerShell 运行" 功能旨在运行没有必需参数的脚本，不会将输出返回到命令提示符。

有关详细信息，请参阅 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)。

### <a name="running-scripts-on-other-computers"></a>在其他计算机上运行脚本

若要在一台或多台远程计算机上运行脚本，请使用该 cmdlet 的 **FilePath** 参数 `Invoke-Command` 。

输入脚本的路径和文件名作为 **FilePath** 参数的值。 脚本必须位于本地计算机上或者本地计算机能够访问的目录中。

以下命令 `Get-ServiceLog.ps1` 在名为 Server01 和 Server02 的远程计算机上运行该脚本。

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>获取脚本的帮助

Get-Help cmdlet 获取脚本的帮助主题，以及 cmdlet 和其他类型的命令的帮助主题。 若要获取脚本的帮助主题，请键入， `Get-Help` 然后键入脚本的路径和文件名。 如果脚本路径在 `Path` 环境变量中，则可以省略该路径。

例如，若要获取 ServicesLog.ps1 脚本的帮助，请键入：

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>如何编写脚本

脚本可以包含任何有效的 PowerShell 命令，其中包括单个命令、使用管道、函数和控制结构的命令（如 If 语句和 For 循环）。

若要编写脚本，请在文本编辑器中打开一个新文件，键入命令，然后将其保存到文件扩展名为的有效文件名的文件中 `.ps1` 。

下面的示例是一个简单的脚本，用于获取当前系统上运行的服务并将其保存到日志文件中。 将从当前日期创建日志文件名。

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

若要创建此脚本，请打开文本编辑器或脚本编辑器，键入这些命令，然后将其保存到名为的文件中 `ServiceLog.ps1` 。

### <a name="parameters-in-scripts"></a>脚本中的参数

若要在脚本中定义参数，请使用 Param 语句。 `Param`语句必须是脚本中的第一个语句，注释和任何 `#Require` 语句除外。

脚本参数的工作方式类似于函数参数。 参数值可用于脚本中的所有命令。 函数参数的所有功能（包括 Parameter 属性及其命名参数）在脚本中也是有效的。

运行脚本时，脚本用户在脚本名称后键入参数。

下面的示例演示一个 `Test-Remote.ps1` 包含 **ComputerName** 参数的脚本。 这两个脚本函数都可以访问 **ComputerName** 参数值。

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

若要运行此脚本，请在脚本名称后键入参数名称。 例如：

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

有关 Param 语句和函数参数的详细信息，请参阅 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="writing-help-for-scripts"></a>编写脚本的帮助

您可以使用以下两种方法之一来编写脚本的帮助主题：

- 脚本 Comment-Based 帮助

  在注释中使用特殊关键字创建帮助主题。 若要为脚本创建基于注释的帮助，必须在脚本文件的开头或结尾处放置注释。 有关基于注释的帮助的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。

- 脚本 XML-Based 帮助

  创建基于 XML 的帮助主题，如通常为 cmdlet 创建的类型。 如果要将帮助主题转换为多种语言，则必须提供基于 XML 的帮助。

若要将脚本与基于 XML 的帮助主题相关联，请使用。.Externalhelp Help comment 关键字。 有关 .Externalhelp 关键字的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。 有关基于 XML 的帮助的详细信息，请参阅 [如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。

### <a name="returning-an-exit-value"></a>返回退出值

默认情况下，脚本结束时，脚本不返回退出状态。 必须使用 `exit` 语句从脚本返回退出代码。 默认情况下，该 `exit` 语句将返回 `0` 。 您可以提供一个数值来返回不同的退出状态。 非零退出代码通常会发出错误信号。

在 Windows 上，允许使用介于和之间的任何数字 `[int]::MinValue` `[int]::MaxValue` 。

在 Unix 上，只 `[byte]::MinValue` 允许 (0) 和 `[byte]::MaxValue` (255) 之间的正数。 范围内的负数将 `-1` `-255` 通过添加来自动转换为正数
256. 例如， `-2` 将转换为 `254` 。

在 PowerShell 中， `exit` 语句设置变量的值 `$LASTEXITCODE` 。 在 Windows 命令行界面 ( # A0) 中，exit 语句设置环境变量的值 `%ERRORLEVEL%` 。

任何非数字或超出平台特定范围的参数均转换为的值 `0` 。

## <a name="script-scope-and-dot-sourcing"></a>脚本范围和网点源

每个脚本都在其自己的作用域中运行。 脚本中创建的函数、变量、别名和驱动器仅存在于脚本作用域中。 你无法在运行脚本的范围内访问这些项或其值。

若要在不同的作用域中运行脚本，可以指定一个范围（如 Global 或 Local），也可以在脚本中使用点值。

使用 "中点采购" 功能，您可以在当前范围内而不是在脚本范围内运行脚本。 当你运行带点的脚本时，脚本中的命令将按你在命令提示符下键入的那样运行。 脚本创建的函数、变量、别名和驱动器在工作范围内创建。 脚本运行后，可以使用创建的项目并在会话中访问其值。

若要将脚本保存到点源，请在脚本路径之前键入一个点 ( ) 和一个空格。

例如：

```powershell
. C:\scripts\UtilityFunctions.ps1
```

或

```powershell
. .\UtilityFunctions.ps1
```

`UtilityFunctions.ps1`脚本运行后，脚本创建的函数和变量将添加到当前作用域中。

例如，该 `UtilityFunctions.ps1` 脚本会创建 `New-Profile` 函数和 `$ProfileName` 变量。

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

如果在脚本的 `UtilityFunctions.ps1` 脚本作用域中运行该脚本，则 `New-Profile` `$ProfileName` 只有当脚本正在运行时，函数和变量才存在。 脚本退出后，将删除函数和变量，如下面的示例中所示。

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

当你用点来编写脚本并运行它时，脚本将在你的作用域内的会话中创建 `New-Profile` 函数和 `$ProfileName` 变量。 脚本运行后，你可以 `New-Profile` 在会话中使用函数，如下面的示例中所示。

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

有关作用域的详细信息，请参阅 about_Scopes。

## <a name="scripts-in-modules"></a>模块中的脚本

模块是可作为一个单元分发的一组相关 PowerShell 资源。 您可以使用模块来组织您的脚本、函数和其他资源。 你还可以使用模块将代码分发给其他人，并从受信任的源获取代码。

您可以将脚本包含在您的模块中，也可以创建脚本模块，该模块是完全或主要包含脚本和支持资源的模块。 脚本模块只是文件扩展名为 hbase-runner.psm1 的脚本。

有关模块的详细信息，请参阅 [about_Modules](about_Modules.md)。

## <a name="other-script-features"></a>其他脚本功能

PowerShell 提供了许多可在脚本中使用的有用功能。

- `#Requires` -可以使用 `#Requires` 语句阻止脚本在没有指定模块或管理单元和指定版本的 PowerShell 的情况下运行。 有关详细信息，请参阅 about_Requires。

- `$PSCommandPath` -包含正在运行的脚本的完整路径和名称。 此参数在所有脚本中都有效。 此自动变量在 PowerShell 3.0 中引入。

- `$PSScriptRoot` -包含正在从中运行脚本的目录。 在 PowerShell 2.0 中，此变量仅在) 的脚本模块中有效 (`.psm1` 。
  从 PowerShell 3.0 开始，它在所有脚本中都有效。

- `$MyInvocation` - `$MyInvocation` 自动变量包含当前脚本的相关信息，包括有关如何启动或 "调用" 的信息。 您可以使用此变量及其属性来获取有关正在运行的脚本的信息。 例如， `$MyInvocation` 。MyCommand 变量包含脚本的路径和文件名。 `$MyInvocation`.行包含启动脚本的命令，包括所有参数和值。

  从 PowerShell 3.0 开始， `$MyInvocation` 具有两个新属性，这些属性提供有关调用或调用当前脚本的脚本的信息。 仅当调用程序或调用方为脚本时，才填充这些属性的值。

  - **PSCommandPath** 包含调用或调用当前脚本的脚本的完整路径和名称。

  - **PSScriptRoot** 包含调用或调用当前脚本的脚本的目录。

  与 `$PSCommandPath` `$PSScriptRoot` 包含当前脚本相关信息的和自动变量不同，该变量的 **PSCommandPath** 和 **PSScriptRoot** 属性 `$MyInvocation` 包含有关调用当前脚本的脚本的信息。

- 数据部分-可以使用 `Data` 关键字在脚本中将数据与逻辑分离。 数据节还可以更轻松地进行本地化。 有关详细信息，请参阅 [about_Data_Sections](about_Data_Sections.md) 和 [about_Script_Internationalization](about_Script_Internationalization.md)。

- 脚本签名-可以向脚本添加数字签名。 根据执行策略，可以使用数字签名来限制可能包含不安全命令的脚本的运行。 有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md) 和 [about_Signing](about_Signing.md)。

## <a name="see-also"></a>请参阅

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
