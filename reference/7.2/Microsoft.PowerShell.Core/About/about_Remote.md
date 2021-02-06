---
description: 描述如何在 PowerShell 中运行远程命令。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: b47efbaaebdd75be5f15be449e194113a0d6ebd7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598664"
---
# <a name="about-remote"></a>关于远程

## <a name="short-description"></a>简短说明
描述如何在 PowerShell 中运行远程命令。

## <a name="long-description"></a>详细说明

您可以通过使用临时或永久连接在一台计算机或多台计算机上运行远程命令。 你还可以使用单台远程计算机启动交互式会话。

本主题提供了一系列示例，说明如何运行不同类型的远程命令。 尝试这些基本命令后，请阅读描述这些命令中使用的每个 cmdlet 的帮助主题。 这些主题提供详细信息，并说明如何修改这些命令以满足你的需求。

注意：若要使用 PowerShell 远程处理，必须为本地和远程计算机配置远程处理。 有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>如何启动交互式会话 (ENTER-PSSESSION) 

运行远程命令的最简单方法是启动与远程计算机的交互式会话。

会话启动时，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。 每个交互会话中只能连接到一台计算机。

若要启动交互式会话，请使用 Enter-PSSession cmdlet。 以下命令将启动与 Server01 计算机的交互式会话：

```powershell
Enter-PSSession Server01
```

命令提示符将发生更改，以指示你已连接到 Server01 计算机。

```
Server01\PS>
```

现在，可以在 Server01 计算机上键入命令。

若要结束交互会话，请键入：

```powershell
Exit-PSSession
```

有关详细信息，请参阅 Enter-PSSession。

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>如何使用具有 COMPUTERNAME 参数的 CMDLET 来获取远程数据

多个 cmdlet 具有 ComputerName 参数，可让你从远程计算机获取对象。

由于这些 cmdlet 不使用基于 WS-MANAGEMENT 的 PowerShell 远程处理，因此可以在任何运行 PowerShell 的计算机上使用这些 cmdlet 的 ComputerName 参数。 无需为 PowerShell 远程处理配置计算机，并且计算机无需满足远程处理的系统要求。

以下 cmdlet 具有 ComputerName 参数：

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

例如，以下命令将获取 Server01 远程计算机上的服务：

```powershell
Get-Service -ComputerName Server01
```

通常，支持无需特殊配置的远程处理的 cmdlet 具有 **ComputerName** 参数，但不具有 **Session** 参数。 若要在会话中查找这些 cmdlet，请键入：

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>如何运行远程命令

若要在远程计算机上运行其他命令，请使用 Invoke-Command cmdlet。

若要运行单个命令或几个不相关的命令，请使用 Invoke-Command 的 ComputerName 参数来指定远程计算机。 使用 ScriptBlock 参数来指定命令。

例如，以下命令在 Server01 计算机上运行 Get-Culture 命令。

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

ComputerName 参数适用于在一台或多台计算机上运行单个命令或多个不相关的命令的情况。 若要建立与远程计算机的持续性连接，请使用 Session 参数。

## <a name="how-to-create-a-persistent-connection-pssession"></a>如何创建 (PSSESSION) 的持久连接

使用 Invoke-Command cmdlet 的 ComputerName 参数时，Windows PowerShell 只为命令建立连接。 然后，在命令完成后，它将关闭该连接。 命令中定义的任何变量或函数都将丢失。

若要创建与远程计算机的持久连接，请使用 New-PSSession cmdlet。 例如，以下命令在 Server01 和 Server02 计算机上创建 Pssession，然后将 Pssession 保存在 $s 的变量中。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>如何在 PSSESSION 中运行命令

使用 PSSession，可运行一系列共享数据的远程命令，如函数、别名和变量的值。 若要在 PSSession 中运行命令，请使用 Invoke-Command cmdlet 的 Session 参数。

例如，以下命令使用 Invoke-Command cmdlet 在 Server01 和 Server02 计算机上的 Pssession 中运行 Get-Process 命令。
该命令将进程保存在每个 PSSession 的 $p 变量中。

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

由于 PSSession 使用持久性连接，因此您可以在使用 $p 变量的同一 PSSession 中运行另一个命令。 以下命令将计算 $p 中保存的进程数。

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>如何在多台计算机上运行远程命令

若要在多台计算机上运行远程命令，请在 Invoke-Command 的 ComputerName 参数的值中键入所有计算机名称。 用逗号分隔名称。

例如，以下命令在三台计算机上运行 Get-Culture 命令：

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

你还可以在多个 Pssession 中运行命令。 以下命令在 Server01、Server02 和 Server03 计算机上创建 Pssession，然后在每个 Pssession 中运行 Get-Culture 命令。

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

若要包含计算机的 "本地计算机" 列表，请键入本地计算机的名称，键入点 ( ) ，或键入 "localhost"。

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>如何在远程计算机上运行脚本

若要在远程计算机上运行本地脚本，请使用 Invoke 命令的 FilePath 参数。

例如，以下命令在 S1 和 S2 计算机上运行 Sample.ps1 脚本：

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

脚本的结果返回到本地计算机。 不需要复制任何文件。

## <a name="how-to-stop-a-remote-command"></a>如何停止远程命令

若要中断命令，请按 CTRL + C。 中断请求会传递到远程计算机，并在该位置终止远程命令。

## <a name="for-more-information"></a>详细信息

- 有关远程处理的系统要求的信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

- 有关设置远程输出格式的帮助，请参阅 [about_Remote_Output](about_Remote_Output.md)。

- 有关远程处理的工作原理、如何管理远程数据、特殊配置、安全问题和其他常见问题的信息，请参阅 [about_Remote_FAQ](about_Remote_FAQ.md)。

- 有关解决远程处理错误的帮助，请参阅 about_Remote_Troubleshooting。

- 有关 Pssession 和持续连接的信息，请参阅 [about_PSSessions](about_PSSessions.md)。

- 有关 PowerShell 后台作业的信息，请参阅 [about_Jobs](about_Jobs.md)。

## <a name="keywords"></a>字

about_Remoting

## <a name="see-also"></a>另请参阅

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

