---
description: 介绍如何创建和使用 PowerShell 配置文件。
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 65920fd9f11a1d9206ba3dbe899831ffe2ced5be
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194165"
---
# <a name="about-profiles"></a>关于配置文件

## <a name="short-description"></a>简短说明
介绍如何创建和使用 PowerShell 配置文件。

## <a name="long-description"></a>详细说明

可以创建 PowerShell 配置文件以自定义环境，并向启动的每个 PowerShell 会话中添加特定于会话的元素。

PowerShell 配置文件是在 PowerShell 启动时运行的脚本。 你可以使用配置文件作为登录脚本来自定义环境。 可以添加命令、别名、函数、变量、管理单元、模块和 PowerShell 驱动器。 你还可以将其他特定于会话的元素添加到你的配置文件中，以便它们可在每个会话中使用，而无需导入或重新创建它们。

PowerShell 支持多个用户和主机程序配置文件。 但是，它不会为你创建配置文件。 本主题介绍了配置文件，并介绍了如何在计算机上创建和维护配置文件。

它说明了如何使用 PowerShell 控制台的 **NoProfile** 参数 (PowerShell.exe) 在不使用任何配置文件的情况下启动 powershell。 而且，它还说明了 PowerShell 执行策略对配置文件的影响。

## <a name="the-profile-files"></a>配置文件

PowerShell 支持多个配置文件。 此外，PowerShell 主机程序还可以支持其自己的特定于主机的配置文件。

例如，PowerShell 控制台支持以下基本配置文件。 配置文件按优先级顺序列出。 第一个配置文件的优先级最高。

|说明               | 路径                                          |
|--------------------------|-----------------------------------------------|
|所有用户，所有主机      |$PSHOME \\Profile.ps1                           |
|所有用户，当前主机   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|当前用户，所有主机   |$Home \\ [My] Documents \\ WindowsPowerShell \\Profile.ps1 |
|当前用户、当前主机|$Home \\ [My] Documents \\ WindowsPowerShell\\<br>Microsoft.PowerShell_profile.ps1 |

配置文件路径包含以下变量：

- `$PSHOME`变量，存储 PowerShell 的安装目录
- `$Home`变量，用于存储当前用户的主目录

此外，托管 PowerShell 的其他程序可以支持其自己的配置文件。 例如， (ISE) 的 PowerShell 集成脚本环境支持以下特定于主机的配置文件。

|说明               | 路径                                       |
|--------------------------|--------------------------------------------|
|所有用户，当前主机   |$PSHOME \\Microsoft.PowerShellISE_profile.ps1|
|当前用户、当前主机|$Home \\ [My] Documents \\ WindowsPowerShell\\<br>Microsoft.PowerShellISE_profile.ps1 |

在 PowerShell 帮助中，"CurrentUser，Current Host" 配置文件是最常称为 "你的 PowerShell 配置文件" 的配置文件。

## <a name="the-profile-variable"></a>$PROFILE 变量

`$PROFILE`自动变量存储当前会话中可用的 PowerShell 配置文件的路径。

若要查看配置文件路径，请显示变量的值 `$PROFILE` 。 你还可以使用 `$PROFILE` 命令中的变量来表示路径。

`$PROFILE`变量存储 "当前用户，当前主机" 配置文件的路径。 其他配置文件保存在变量的 "注意" 属性中 `$PROFILE` 。

例如，在 `$PROFILE` Windows PowerShell 控制台中，变量具有以下值。

|描述                |名称                              |
|---------------------------|----------------------------------|
|当前用户、当前主机 |`$PROFILE`                        |
|当前用户、当前主机 |`$PROFILE.CurrentUserCurrentHost` |
|当前用户，所有主机    |`$PROFILE.CurrentUserAllHosts`    |
|所有用户，当前主机    |`$PROFILE.AllUsersCurrentHost`    |
|所有用户，所有主机       |`$PROFILE.AllUsersAllHosts`       |

由于变量的值会 `$PROFILE` 随每个用户和每个主机应用程序更改，因此请确保在使用的每个 PowerShell 主机应用程序中显示配置文件变量的值。

若要查看变量的当前值 `$PROFILE` ，请键入：

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

可以 `$PROFILE` 在许多命令中使用该变量。 例如，以下命令将在记事本中打开 "当前用户、当前主机" 配置文件：

```powershell
notepad $PROFILE
```

以下命令确定是否已在本地计算机上创建 "所有用户，所有主机" 配置文件：

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>如何创建配置文件

若要创建 PowerShell 配置文件，请使用以下命令格式：

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

例如，若要在当前 PowerShell 主机应用程序中创建当前用户的配置文件，请使用以下命令：

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

在此命令中， `If` 语句阻止你覆盖现有的配置文件。 将占位符的值替换 \<profile-path\> 为要创建的配置文件的路径。

> [!NOTE]
> 若要在 Windows Vista 和更高版本的 Windows 中创建 "所有用户" 配置文件，请以 "以 **管理员身份运行** " 选项启动 PowerShell。

## <a name="how-to-edit-a-profile"></a>如何编辑配置文件

可以在文本编辑器（例如记事本）中打开任何 PowerShell 配置文件。

若要在 "记事本" 中打开当前 PowerShell 主机应用程序中当前用户的配置文件，请键入：

```powershell
notepad $PROFILE
```

若要打开其他配置文件，请指定配置文件名称。 例如，若要打开所有主机应用程序的所有用户的配置文件，请键入：

```powershell
notepad $PROFILE.AllUsersAllHosts
```

若要应用更改，请保存配置文件，然后重新启动 PowerShell。

## <a name="how-to-choose-a-profile"></a>如何选择配置文件

如果使用多个主机应用程序，请将在所有主机应用程序中使用的项放入 `$PROFILE.CurrentUserAllHosts` 配置文件中。 将特定于宿主应用程序的项（如用于设置宿主应用程序的背景色的命令）放置在特定于该宿主应用程序的配置文件中。

如果你是为多个用户自定义 PowerShell 的管理员，请遵循以下准则：

- 将常见项存储在 `$PROFILE.AllUsersAllHosts` 配置文件中
- 在 `$PROFILE.AllUsersCurrentHost` 特定于宿主应用程序的配置文件中存储特定于宿主应用程序的项
- 为特定用户存储特定于用户的配置文件的项

务必查看主机应用程序文档，了解 PowerShell 配置文件的任何特殊实现。

## <a name="how-to-use-a-profile"></a>如何使用配置文件

在 PowerShell 中创建的许多项和运行的大多数命令只会影响当前会话。 结束会话时，将删除这些项。

特定于会话的命令和项包括变量、首选项变量、别名、函数、命令 (除了 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) 之外，还包括添加到会话中的 PowerShell 模块。

若要保存这些项目并使其在将来的所有会话中可用，请将它们添加到 PowerShell 配置文件中。

配置文件的另一个常见用途是保存常用的函数、别名和变量。 在配置文件中保存项时，可以在任何适用的会话中使用它们，而无需重新创建它们。

## <a name="how-to-start-a-profile"></a>如何启动配置文件

打开配置文件时，它是空白的。 不过，你可以使用经常使用的变量、别名和命令来填充它。

下面是几个入门建议。

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>添加使你可以轻松地打开配置文件的命令

如果你使用的配置文件不是 "当前用户"、"当前主机" 配置文件，则此方法特别有用。 例如，添加以下命令：

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>添加一个函数，该函数列出任何 cmdlet 的别名

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>自定义控制台

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>添加自定义 PowerShell 提示符

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

有关 PowerShell 提示符的详细信息，请参阅 [about_Prompts](about_Prompts.md)。

## <a name="the-noprofile-parameter"></a>NoProfile 参数

若要在不使用配置文件的情况下启动 PowerShell，请使用 **PowerShell.exe** 的 **NoProfile** 参数，该程序启动 PowerShell。

若要开始，请打开可启动 PowerShell 的程序，例如 Cmd.exe 或 PowerShell 本身。 你还可以使用 Windows 中的 "运行" 对话框。

类型：

```
PowerShell -NoProfile
```

有关 PowerShell.exe 的参数的完整列表，请键入：

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>配置文件和执行策略

PowerShell 执行策略确定是否可以运行脚本并加载配置文件（包括配置文件）。 默认情况下， **限制** 执行策略为。 它将阻止所有脚本运行，包括配置文件。 如果你使用 "受限" 策略，则不会运行配置文件，并且不会应用其内容。

`Set-ExecutionPolicy`命令设置并更改您的执行策略。 这是适用于所有 PowerShell 会话的几个命令之一，因为该值保存在注册表中。 不需要在打开控制台时进行设置，也不必 `Set-ExecutionPolicy` 在配置文件中存储命令。

## <a name="profiles-and-remote-sessions"></a>配置文件和远程会话

PowerShell 配置文件不会自动在远程会话中运行，因此配置文件添加的命令不会出现在远程会话中。 此外，在 `$PROFILE` 远程会话中不填充自动变量。

若要在会话中运行配置文件，请使用 [命令调用](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet。

例如，以下命令在的会话中从本地计算机运行 "当前用户，当前主机" 配置文件 `$s` 。

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

以下命令在的会话中从远程计算机运行 "当前用户，当前主机" 配置文件 `$s` 。 由于 `$PROFILE` 未填充变量，因此该命令使用配置文件的显式路径。 我们使用点采购运算符，使配置文件在远程计算机上的当前作用域中运行，而不是在其自身的作用域中执行。

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

运行此命令后，配置文件添加到会话中的命令在中可用 `$s` 。

## <a name="see-also"></a>另请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
