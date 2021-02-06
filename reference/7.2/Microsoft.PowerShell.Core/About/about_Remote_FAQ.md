---
description: 包含有关在 PowerShell 中运行远程命令的问题和解答。
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da3516697c58e3273538ed2ed93a7a54fcd9bb49
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603576"
---
# <a name="about-remote-faq"></a>关于远程 FAQ

## <a name="short-description"></a>简短说明
包含有关在 PowerShell 中运行远程命令的问题和解答。

## <a name="long-description"></a>长说明

远程工作时，可以在一台计算机上的 PowerShell 中键入命令 (称为 "本地计算机" ) ，但这些命令会在另一台计算机上运行， (称为 "远程计算机" ) 。 远程工作的体验应该非常类似于直接在远程计算机上工作。

注意：若要使用 PowerShell 远程处理，必须配置远程计算机以进行远程处理。 有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

### <a name="must-both-computers-have-powershell-installed"></a>这两台计算机都必须安装 PowerShell？

是的。 若要远程工作，本地和远程计算机必须具有 PowerShell、Microsoft .NET 框架和用于管理的 Web 服务 (WS-MANAGEMENT) 协议。 执行特定命令所需的任何文件和其他资源必须位于远程计算机上。

运行 Windows PowerShell 3.0 的计算机和运行 Windows PowerShell 2.0 的计算机可以远程连接到彼此，并运行远程命令。
但是，某些功能（如从会话断开连接并重新连接到它）仅在两台计算机都运行 Windows PowerShell 3.0 时才起作用。

您必须有权连接到远程计算机、运行 PowerShell 的权限，以及访问数据存储区的权限， (如文件和文件夹) 以及远程计算机上的注册表。

有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

### <a name="how-does-remoting-work"></a>远程处理如何工作？

提交远程命令时，该命令将通过网络传输到远程计算机上的 PowerShell 引擎，并在远程计算机上的 PowerShell 客户端中运行。 命令结果被发送回本地计算机，并出现在本地计算机上的 PowerShell 会话中。

为了传输命令和接收输出，PowerShell 使用 WS-Management 协议。 有关 WS-Management 协议的信息，请参阅 Windows 文档中的 [WS-Management 协议](/windows/win32/winrm/ws-management-protocol) 。

从 Windows PowerShell 3.0 开始，远程会话存储在远程计算机上。 这使你可以断开与会话的连接，并从其他会话或其他计算机重新连接，而不会中断命令或失去状态。

### <a name="is-powershell-remoting-secure"></a>PowerShell 远程处理是否安全？

当你连接到远程计算机时，系统将使用本地计算机上的用户名和密码凭据，或者在命令中提供的凭据将你登录到远程计算机。 凭据和传输的其余部分进行加密。

若要添加其他保护，你可以将远程计算机配置为使用安全套接字层 (SSL) 而不是 HTTP 来侦听 Windows 远程管理 (WinRM) 请求。 然后，  `Invoke-Command` `New-PSSession` `Enter-PSSession` 在建立连接时，用户可以使用、和 cmdlet 的 UseSSL 参数。 此选项使用更安全的 HTTPS 通道，而不是 HTTP。

### <a name="do-all-remote-commands-require-powershell-remoting"></a>所有远程命令都需要 PowerShell 远程处理吗？

不能。 多个 cmdlet 具有 **ComputerName** 参数，可让你从远程计算机获取对象。

这些 cmdlet 不使用 PowerShell 远程处理。 因此，你可以在运行 PowerShell 的任何计算机上使用它们，即使计算机未配置为进行 PowerShell 远程处理，或者计算机不满足 PowerShell 远程处理的要求。

这些 cmdlet 包括：

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

若要查找包含 **ComputerName** 参数的所有 cmdlet，请键入：

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

若要确定特定 cmdlet 的 **ComputerName** 参数是否需要 PowerShell 远程处理，请参阅参数说明。 若要显示参数说明，请键入：

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

例如：

```powershell
Get-Help Get-Process -Parameter ComputerName
```

对于所有其他命令，请使用 `Invoke-Command` cmdlet。

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>如何实现在远程计算机上运行命令？

若要在远程计算机上运行命令，请使用 `Invoke-Command` cmdlet。

将命令括在大括号中 `{}` ， () 使其成为脚本块。 使用的 **ScriptBlock** 参数 `Invoke-Command` 指定命令。

您可以使用 **ComputerName** 参数 `Invoke-Command` 来指定远程计算机。 或者，你可以 (会话创建到远程计算机的持续性连接) 然后使用的 **session** 参数 `Invoke-Command` 在该会话中运行该命令。

例如，以下命令 `Get-Process` 远程运行命令。

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

若要中断远程命令，请键入<kbd>CTRL</kbd> + <kbd>C</kbd>。 中断请求会传递到远程计算机，并在其中终止远程命令。

有关远程命令的详细信息，请参阅 about_Remote 和支持远程处理的 cmdlet 的帮助主题。

### <a name="can-i-just-telnet-into-a-remote-computer"></a>我能只是 telnet 到远程计算机上吗？

你可以使用 `Enter-PSSession` cmdlet 来启动与远程计算机的交互式会话。

在 PowerShell 提示符下，键入：

```powershell
Enter-PSSession <ComputerName>
```

命令提示符更改为显示你已连接到远程计算机。

```
<ComputerName>\C:>
```

现在，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。

若要结束交互会话，请键入：

```powershell
Exit-PSSession
```

交互式会话是使用 WS-Management 协议的持久会话。 它与使用 Telnet 不同，但它提供了类似的体验。

有关详细信息，请参阅 `Enter-PSSession`。

### <a name="can-i-create-a-persistent-connection"></a>能否创建持续性连接？

是的。 可以通过指定远程计算机的名称、NetBIOS 名称或 IP 地址来运行远程命令。 或者，你可以通过指定连接到远程计算机 (PSSession) 的 PowerShell 会话来运行远程命令。

当你使用或的 **ComputerName** 参数 `Invoke-Command` 时 `Enter-PSSession` ，PowerShell 将建立一个临时连接。 PowerShell 使用连接来仅运行当前命令，然后关闭连接。 这是一种非常有效的方法，可用于运行单个命令或多个不相关的命令，即使在许多远程计算机上也是如此。

使用 `New-PSSession` cmdlet 创建 pssession 时，PowerShell 将为 pssession 建立持续连接。 然后，可以在 PSSession 中运行多个命令，包括共享数据的命令。

通常，可以创建 PSSession 来运行一系列共享数据的相关命令。 否则， **ComputerName** 参数创建的临时连接就足以满足大多数命令。

有关会话的详细信息，请参阅 about_PSSessions。

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>是否可以一次在多台计算机上运行命令？

是的。 此 cmdlet 的 **ComputerName** 参数 `Invoke-Command` 接受多个计算机名称， **Session** 参数接受多个 pssession。

运行命令时，PowerShell 会在所有指定的 `Invoke-Command` 计算机上或在所有指定的 pssession 中运行命令。

PowerShell 可以管理数百个并发远程连接。 但是，您可以发送的远程命令的数量可能会受到您的计算机的资源和用于建立和维护多个网络连接的容量的限制。

有关详细信息，请参阅帮助主题中的示例 `Invoke-Command` 。

### <a name="where-are-my-profiles"></a>我的配置文件在哪里？

PowerShell 配置文件不会自动在远程会话中运行，因此该配置文件添加的命令不会出现在会话中。 此外，在 `$profile` 远程会话中不填充自动变量。

若要在会话中运行配置文件，请使用 `Invoke-Command` cmdlet。

例如，以下命令在的会话中运行本地计算机的 CurrentUserCurrentHost 配置文件 `$s` 。

```
Invoke-Command -Session $s -FilePath $profile
```

以下命令在的会话中从远程计算机运行 CurrentUserCurrentHost 配置文件 `$s` 。 由于 `$profile` 未填充变量，因此该命令使用配置文件的显式路径。

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

运行此命令后，配置文件添加到会话中的命令在中可用 `$s` 。

你还可以使用会话配置中的启动脚本在使用会话配置的每个远程会话中运行配置文件。

有关 PowerShell 配置文件的详细信息，请参阅 about_Profiles。
有关会话配置的详细信息，请参阅 `Register-PSSessionConfiguration` 。

### <a name="how-does-throttling-work-on-remote-commands"></a>限制如何处理远程命令？

为帮助你管理本地计算机上的资源，PowerShell 包含一个基于命令的限制功能，该功能使你能够限制为每个命令建立的并发远程连接的数量。

默认值为32并发连接，但你可以使用 cmdlet 的 **ThrottleLimit** 参数为特定命令设置自定义限制限制。

使用限制功能时，请记住，它应用于每个命令，而不是应用于整个会话或计算机。 如果在多个会话或 Pssession 中并发运行命令，则并发连接数是所有会话中的并发连接数之和。

若要查找具有 **ThrottleLimit** 参数的 cmdlet，请键入：

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>远程命令的输出是否与本地输出不同？

当你在本地使用 PowerShell 时，将发送和接收 "live" .NET Framework 对象;"实时" 对象是与实际程序或系统组件关联的对象。 在调用方法或更改活动对象的属性时，所做更改会影响实际的程序或组件。 当程序或组件的属性发生更改时，表示它们的对象的属性也会发生更改。

但是，由于大多数实时对象无法通过网络进行传输，因此 PowerShell 会 "序列化" 远程命令中发送的大多数对象，也就是说，它将每个对象转换为 XML [Export-clixml] 中的一系列 XML (约束语言，) 用于传输的数据元素。

当 PowerShell 接收到序列化对象时，它会将 XML 转换为反序列化的对象类型。 反序列化的对象是之前的程序或组件的属性的准确记录，但它不再 "实时"，也就是说，它不再与组件直接关联。 和将删除这些方法，因为它们不再有效。

通常，您可以像使用活动对象一样使用反序列化的对象，但必须知道它们的局限性。 此外，该 cmdlet 返回的对象 `Invoke-Command` 还有其他属性，可帮助你确定命令源。

某些对象类型（如 DirectoryInfo 对象和 Guid）在收到时转换回活动对象。 这些对象不需要任何特殊的处理或格式。

有关解释和格式化远程输出的信息，请参阅 [about_Remote_Output](about_Remote_Output.md)。

### <a name="can-i-run-background-jobs-remotely"></a>可以远程运行后台作业吗？

是的。 PowerShell 后台作业是一个在不与会话交互的情况下异步运行的 PowerShell 命令。 启动后台作业时，命令提示符会立即返回，你可以继续在该会话中运行，即使该作业长时间运行也是如此。

即使其他命令正在运行，也可以启动后台作业，因为后台作业始终在临时会话中以异步方式运行。

可以在本地或远程计算机上运行后台作业。 默认情况下，后台作业在本地计算机上运行。 但是，可以使用 cmdlet 的 **AsJob** 参数将 `Invoke-Command` 任何远程命令作为后台作业运行。 您也可以使用 `Invoke-Command` `Start-Job` 远程运行命令。

有关 PowerShell 中的后台作业的详细信息，请参阅 [about_Jobs (about_Jobs md) ] 和 [about_Remote_Jobs (about_Remote_Jobs。

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>能否在远程计算机上运行 windows 程序？

你可以使用 PowerShell 远程命令在远程计算机上运行基于 Windows 的程序。 例如，你可以 `Shutdown.exe` `Ipconfig.exe` 在远程计算机上运行或。

但是，不能使用 PowerShell 命令打开远程计算机上任何程序的用户界面。

当你启动远程计算机上的 Windows 程序时，该命令不会完成，并且 PowerShell 命令提示符将不会返回，直到该程序完成或按下<kbd>CTRL</kbd> + <kbd>C</kbd>来中断命令。 例如，如果在 `Ipconfig.exe` 远程计算机上运行该程序，则命令提示符直到完成后才会返回 `Ipconfig.exe` 。

如果使用远程命令来启动具有用户界面的程序，程序进程将启动，但不会显示用户界面。 PowerShell 命令未完成，并且在你停止程序进程或按下<kbd>CTRL</kbd>C 之后，命令提示符才会返回， + <kbd></kbd>这会中断命令并停止进程。

例如，如果使用 PowerShell 命令 `Notepad` 在远程计算机上运行，则记事本进程将在远程计算机上启动，但不会显示记事本用户界面。 若要中断该命令并还原命令提示符，请按<kbd>CTRL</kbd>+ + <kbd>C</kbd>。

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>能否限制用户可在我的计算机上远程运行的命令？

是的。 每个远程会话都必须使用远程计算机上的一个会话配置。 你可以管理计算机上的会话配置 (和这些会话配置的权限) 确定哪些用户可以在你的计算机上远程运行命令和可以运行的命令。

会话配置配置会话的环境。 您可以通过使用实现新的配置类的程序集或使用在会话中运行的脚本来定义配置。 此配置可以确定会话中可用的命令。
而且，配置可以包括用于保护计算机的设置，例如，用于限制在单个对象或命令中会话可以远程接收的数据量的设置。 您还可以指定一个安全描述符，以确定使用配置所需的权限。

该 `Enable-PSRemoting` cmdlet 将在你的计算机上创建默认会话配置： microsoft.powershell32 (64 位操作系统仅) 的操作系统。 `Enable-PSRemoting` 设置配置的安全描述符，以只允许计算机上 Administrators 组的成员使用这些配置。

你可以使用会话配置 cmdlet 来编辑默认会话配置、创建新的会话配置，以及更改所有会话配置的安全描述符。

从 Windows PowerShell 3.0 开始， `New-PSSessionConfigurationFile` cmdlet 可让你使用文本文件创建自定义会话配置。 此文件包含用于设置语言模式和指定在使用会话配置的会话中可用的 cmdlet 和模块的选项。

用户使用 `Invoke-Command` 、 `New-PSSession` 或 `Enter-PSSession` cmdlet 时，可以使用 **ConfigurationName** 参数来指示用于会话的会话配置。 而且，他们可以通过更改 `$PSSessionConfigurationName` 会话中首选项变量的值来更改其会话使用的默认配置。

有关会话配置的详细信息，请参阅会话配置 cmdlet 的帮助。 若要查找会话配置 cmdlet，请键入：

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>风扇的配置和扇出配置是什么？

涉及多台计算机的最常见的 PowerShell 远程处理方案是一对多配置，在这种配置中，一台本地计算机 (管理员的计算机) 在许多远程计算机上运行 PowerShell 命令。 这称为 "扇出" 方案。

但是，在某些企业中，配置为多对一，其中许多客户端计算机连接到运行 PowerShell 的单台远程计算机，如文件服务器或展台。 这称为 "扇入" 配置。

PowerShell 远程处理同时支持扇出和扇入配置。

对于扇出配置，PowerShell 使用 Web 服务进行管理 (WS-MANAGEMENT) 协议和 WinRM 服务，后者支持 WS-MANAGEMENT 的 Microsoft 实现。 当本地计算机连接到远程计算机时，WS-Management 会建立一个连接，并使用用于 PowerShell 的插件启动 PowerShell 主机进程， ( 在远程计算机上 # A0) 。 用户可以指定备用端口、备用会话配置以及用于自定义远程连接的其他功能。

为了支持 "扇入" 配置，PowerShell 使用 internet 信息服务 (IIS) 承载 WS-MANAGEMENT、加载 PowerShell 插件以及启动 PowerShell。 在这种情况下，不是在单独的进程中启动每个 PowerShell 会话，而是在同一主机进程中运行所有 PowerShell 会话。

Windows XP 或 Windows Server 2003 不支持 IIS 承载和扇入远程管理。

在扇入配置中，用户可以指定连接 URI 和 HTTP 终结点，包括传输、计算机名称、端口和应用程序名称。
IIS 将具有指定应用程序名称的所有请求转发到应用程序。 默认值为 WS-MANAGEMENT，它可以承载 PowerShell。

还可以指定身份验证机制，并禁止或允许从 HTTP 和 HTTPS 终结点重定向。

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>能否在不在域中的单台计算机上测试远程处理？

是的。 即使本地计算机不在域中，也可以使用 PowerShell 远程处理。 可以使用远程处理功能连接到会话并在同一台计算机上创建会话。 功能的工作方式与连接到远程计算机时的功能相同。

若要在工作组中的计算机上运行远程命令，请在计算机上更改以下 Windows 设置。

注意：这些设置会影响系统上的所有用户，并使系统更易受到恶意攻击。 进行这些更改时请务必小心。

- Windows Vista、Windows 7、Windows 8：

  创建以下注册表项，然后将其值设置为1： LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  你可以使用以下 PowerShell 命令来添加此项：

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003，Windows Server 2008，Windows Server 2012，Windows Server 2012 R2：

  不需要进行任何更改，因为 "网络访问：本地帐户的共享和安全模型" 策略的默认设置为 "经典"。 验证设置是否已更改。

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>是否可以在另一个域中的计算机上运行远程命令？

是的。 通常，命令运行时不会出错，但你可能需要使用、 或 Cmdlet 的 Credential `Invoke-Command` 参数 `New-PSSession` `Enter-PSSession` 提供远程计算机上 Administrators 组的成员的凭据。 即使当前用户是本地和远程计算机上的 Administrators 组的成员，也需要进行这种情况。

但是，如果远程计算机不在本地计算机信任的域中，则远程计算机可能无法对用户的凭据进行身份验证。

若要启用身份验证，请使用以下命令将远程计算机添加到 WinRM 中本地计算机的受信任主机列表。 在 PowerShell 提示符下键入命令。

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

例如，要将 Server01 计算机添加到本地计算机上的受信任主机列表，请在 PowerShell 提示符下键入以下命令：

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a>PowerShell 是否支持通过 SSH 进行远程处理？

是的。 有关详细信息，请参阅 [通过 SSH 进行 PowerShell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

## <a name="see-also"></a>请参阅

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
