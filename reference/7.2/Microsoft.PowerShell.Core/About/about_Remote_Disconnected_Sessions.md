---
description: 说明如何断开连接并重新连接到 PowerShell 会话 (PSSession) 。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 0756e110b1058915f6280e2ea59ee915bedb2c75
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598450"
---
# <a name="about-remote-disconnected-sessions"></a>关于远程断开连接的会话

## <a name="short-description"></a>简短说明

说明如何断开连接并重新连接到 PowerShell 会话 (PSSession) 。

## <a name="long-description"></a>长说明

从 PowerShell 3.0 开始，你可以断开与 PSSession 的连接，然后重新连接到同一台计算机或不同计算机上的 PSSession。 当会话断开连接时，将维护会话状态，并且 PSSession 中的命令将继续运行。

仅当远程计算机运行 PowerShell 3.0 或更高版本时，"断开连接的会话" 功能才可用。

使用 "断开连接的会话" 功能，可以关闭在其中创建 PSSession 的会话，甚至可以关闭 PowerShell 并关闭计算机，而不会中断在 PSSession 中运行的命令。 断开连接的会话适用于运行需要延长时间完成的命令，并提供 IT 专业人员所需的时间和设备灵活性。

不能从使用 cmdlet 启动的交互式会话断开连接 `Enter-PSSession` 。

你可以使用断开连接的会话来管理由于计算机或网络中断而无意间断开连接的 Pssession。

在实际使用中，通过 "断开连接的会话" 功能，您可以开始解决问题，将注意力转换为更高的优先级问题，然后在解决方案上恢复工作，即使在不同的计算机上的其他位置也是如此。

## <a name="disconnected-session-cmdlets"></a>断开连接的会话 cmdlet

以下 cmdlet 支持 "断开连接的会话" 功能：

- `Connect-PSSession`：连接到断开连接的 PSSession。
- `Disconnect-PSSession`：断开 PSSession 的连接。
- `Get-PSSession`：获取本地计算机或远程计算机上的 Pssession。
- `Receive-PSSession`：获取在断开连接的会话中运行的命令的结果。
- `Invoke-Command`： **InDisconnectedSession** 参数创建 PSSession 并立即断开连接。

## <a name="how-the-disconnected-sessions-feature-works"></a>断开连接的会话功能的工作原理

从 PowerShell 3.0 开始，Pssession 独立于创建它们的会话。 活动的 Pssession 在连接的远程计算机或 **服务器端** 保持，即使在其中创建 PSSession 的会话已关闭，并且源计算机已关闭或断开与网络的连接。

在 PowerShell 2.0 中，当从远程计算机断开连接时，该 PSSession 将从远程计算机中删除，或从该会话中创建的会话结束。

断开 PSSession 的连接时，PSSession 将保持活动状态并在远程计算机上维护。 会话状态从 " **正在运行** " 更改为 "已 **断开连接**"。 可以从当前会话或同一计算机上的其他会话或其他计算机重新连接到断开连接的 PSSession。 维护会话的远程计算机必须正在运行并连接到网络。

断开连接的 PSSession 中的命令将继续在远程计算机上无中断运行，直到命令完成或输出缓冲区已满。 若要防止完整输出缓冲区暂停命令，请使用 `Disconnect-PSSession` 、 `New-PSSessionOption` 或 cmdlet 的 OutputBufferingMode 参数 `New-PSTransportOption` 。

断开连接的会话在远程计算机上保持为断开连接状态。 它们可用于重新连接，直到你删除 PSSession （如使用 `Remove-PSSession` cmdlet）或直到 PSSession 的空闲超时过期。 你可以使用 、  `Disconnect-PSSession` `New-PSSessionOption` 或 cmdlet 的 IdleTimeoutSec 或 IdleTimeout 参数调整 PSSession 的空闲超时 `New-PSTransportOption` 。

其他用户可以连接到你创建的 Pssession，但前提是这些用户可以提供用于创建会话的凭据，或使用 `RunAs` 会话配置的凭据。

## <a name="how-to-get-pssessions"></a>如何获取 Pssession

从 PowerShell 3.0 开始，该 `Get-PSSession` cmdlet 将获取本地计算机和远程计算机上的 pssession。 它还可获取在当前会话中创建的 Pssession。

若要在本地计算机或远程计算机上获取 Pssession，请使用 **ComputerName** 或 **ConnectionUri** 参数。 如果没有参数，则 `Get-PSSession` 将获取在本地会话中创建的 PSSession，而不考虑它们终止的位置。

获取 Pssession 时，请记住在维护它们的计算机（即远程计算机或 **服务器端** 计算机）上查找它们。

例如，如果创建 Server01 计算机的 PSSession，请从 Server01 计算机获取会话。 如果从另一台计算机向本地计算机创建 PSSession，请从本地计算机获取会话。

以下命令序列显示了如何 `Get-PSSession` 工作。

第一个命令创建一个与 Server01 计算机的会话。 该会话驻留在 Server01 计算机上。

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

若要获取会话，请使用值为 Server01 的 **ComputerName** 参数 `Get-PSSession` 。

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

如果的 **ComputerName** 参数的值 `Get-PSSession` 为 localhost，将 `Get-PSSession` 获取在本地计算机上维护并在其上维护的 pssession。 即使它们是在本地计算机上启动的，它也不会在 Server01 计算机上 Pssession。

```powershell
Get-PSSession -ComputerName localhost
```

若要获取在当前会话中创建的会话，请使用 `Get-PSSession` 不带参数的 cmdlet。 在此示例中， `Get-PSSession` 将获取在当前会话中创建的 PSSession 并连接到 Server01 计算机。

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>如何断开会话连接

若要断开 PSSession 的连接，请使用 `Disconnect-PSSession` cmdlet。 若要标识 PSSession，请使用 **Session** 参数，或从 `New-PSSession` 或 cmdlet 到的管道 `Get-PSSession` `Disconnect-PSSession` 。

以下命令将 PSSession 断开连接到 Server01 计算机。
请注意， **State** 属性的值已 **断开连接** ，并且 **可用性** 为 **None**。

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

若要创建断开连接的会话，请使用 cmdlet 的 **InDisconnectedSession** 参数 `Invoke-Command` 。 它将创建一个会话，启动命令，并立即断开连接，然后该命令才能返回任何输出。

以下命令 `Get-WinEvent` 在 Server02 远程计算机上的已断开连接的会话中运行命令。

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>如何连接到断开连接的会话

可以从在其中创建 PSSession 的会话或本地计算机或其他计算机上的其他会话连接到任何可用的断开连接的 PSSession。

你可以创建 PSSession，在 PSSession 中运行命令，断开与 PSSession 的连接，关闭 PowerShell，然后关闭计算机。 小时之后，您可以打开另一台计算机，获取 PSSession，连接到该计算机，并获得在连接断开连接时在 PSSession 中运行的命令的结果。 然后，你可以在该会话中运行更多命令。

若要连接已断开连接的 PSSession，请使用 `Connect-PSSession` cmdlet。 使用 **ComputerName** 或 **ConnectionUri** 参数来标识 pssession，或从到的 pssession 管道 `Get-PSSession` `Connect-PSSession` 。

以下命令获取 Server02 计算机上的会话。 输出包括两个断开连接的会话，两者都可用。

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

以下命令将连接到 Session2。 PSSession 现在已打开且可用。

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>如何获取结果

若要获取在断开连接的 PSSession 中运行的命令的结果，请使用 `Receive-PSSession` cmdlet。

你可以使用 `Receive-PSSession` 而不是使用 `Connect-PSSession` cmdlet。 如果会话已重新连接，则 `Receive-PSSession` 获取在断开会话连接时运行的命令的结果。 如果 PSSession 仍处于断开连接状态，则 `Receive-PSSession` 连接到它，然后获取断开连接时运行的命令的结果。

`Receive-PSSession` 可以 (异步方式将结果返回到) 或 (同步) 到主机程序。 使用 **OutTarget** 参数选择 " **作业** " 或 " **主机**"。 默认值为 **Host**。 但是，如果正在接收的命令在当前会话中作为 **作业** 启动，则默认情况下，它作为 **作业** 返回。

以下命令使用 `Receive-PSSession` cmdlet 连接到 Server02 计算机上的 PSSession，并获取 `Get-WinEvent` 在 Session3 会话中运行的命令的结果。 该命令使用 **OutTarget** 参数来获取 **作业** 中的结果。

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

若要获取作业结果，请使用 `Receive-Job` cmdlet。

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>状态和可用性属性

断开连接的 PSSession 的 " **状态** " 和 " **可用性** " 属性告诉你是否可以重新连接到该会话。

当 PSSession 连接到当前会话时，它的状态为 "已 **打开** "，并 **提供** 其可用性。 当断开与 PSSession 的连接时，PSSession 状态将 **断开连接** ，并且其可用性为 **None**。

**State** 属性的值是相对于当前会话的。 如果值为 "已 **断开连接** "，则意味着 PSSession 未连接到当前会话。 但这并不意味着 PSSession 会与所有会话断开连接。 它可能连接到另一个会话。

若要确定是否可以连接或重新连接到 PSSession，请使用 **Availability** 属性。 如果值为 " **无** "，则指示你可以连接到会话。 值为 " **忙碌** " 表示无法连接到 PSSession，因为它已连接到另一个会话。

下面的示例在同一台计算机上的两个 PowerShell 会话中运行。
请注意，当 PSSession 断开连接并重新连接时，每个会话中的 " **状态** " 和 " **可用性** " 属性值会发生变化。

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

断开连接的会话将一直保留在远程计算机上，直到你将其删除（如使用 `Remove-PSSession` cmdlet）或超时。PSSession 的 **IdleTimeout** 属性确定已断开连接的会话在被删除之前保留多长时间。

当 **检测信号线程** 未收到响应时，pssession 处于空闲状态。
断开会话后，即使已断开连接的会话中的命令仍在运行，它也会使其处于空闲状态并启动 **IdleTimeout** 时钟。 PowerShell 将断开连接的会话视为处于活动状态，但处于空闲状态。

当创建和断开连接会话时，请验证 PSSession 中的空闲超时是否足够长，以根据需要维护会话，但不太长，因为它会在远程计算机上使用不必要的资源。

会话配置的 **IdleTimeoutMs** 属性确定使用会话配置的会话的默认空闲超时。 您可以重写默认值，但使用的值不能超过会话配置的 **MaxIdleTimeoutMs** 属性。

若要查找会话配置的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 值，请使用以下命令格式。

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

您可以覆盖会话配置中的默认值，并在创建 PSSession 和断开连接时设置 PSSession 的空闲超时。

如果你是远程计算机上 Administrators 组的成员，则可以创建和更改会话配置的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 属性。

## <a name="idle-timeout-values"></a>空闲超时值

会话配置和会话选项的空闲超时值以毫秒为单位。 会话和会话配置选项的空闲超时值以秒为单位。

您可以在创建 PSSession (时设置 PSSession 的空闲超时 `New-PSSession` ， `Invoke-Command`) 并在从其 () 时断开连接 `Disconnect-PSSession` 。 但是，在连接到 PSSession  (`Connect-PSSession`) 或 () 获取结果时，无法更改 IdleTimeout 值 `Receive-PSSession` 。

`Connect-PSSession`和 `Receive-PSSession` Cmdlet 具有 **SessionOption** 参数，该参数采用 **SessionOption** 对象，例如 cmdlet 返回的对象 `New-PSSessionOption` 。 **SessionOption** 对象中的 **idletimeout** 值和首选项变量中的 **idletimeout** 值 `$PSSessionOption` 不会更改或命令中 PSSession 的 **idletimeout** 值 `Connect-PSSession` `Receive-PSSession` 。

若要创建具有特定空闲超时值的 PSSession，请创建一个 `$PSSessionOption` 首选项变量。 将 **IdleTimeout** 属性的值设置为所需的值 (以毫秒为单位) 。

当您创建 Pssession 时，变量中的值 `$PSSessionOption` 优先于会话配置中的值。

例如，以下命令会将空闲超时设置为48小时：

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

若要创建具有特定空闲超时值的 PSSession，请使用 cmdlet 的 **IdleTimeoutMSec** 参数 `New-PSSessionOption` 。 然后，在或 cmdlet 的 **SessionOption** 参数的值中使用 session 选项 `New-PSSession` `Invoke-Command` 。

创建会话时设置的值优先于 `$PSSessionOption` 首选项变量和会话配置中设置的值。

例如：

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

若要在断开连接时更改 PSSession 的空闲超时，请使用 cmdlet 的 **IdleTimeoutSec** 参数 `Disconnect-PSSession` 。

例如：

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

若要创建具有特定空闲超时和最大空闲超时的会话配置，请使用 cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 参数 `New-PSTransportOption` 。 然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Register-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

若要更改会话配置的默认空闲超时和最大空闲超时时间，请使用 cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 参数 `New-PSTransportOption` 。 然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Set-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>输出缓冲模式

PSSession 的输出缓冲模式决定当 PSSession 的输出缓冲区已满时如何管理命令输出。

在断开连接的会话中，输出缓冲模式可以有效地确定当会话断开连接时该命令是否继续运行。

有效值如下：

- **块**。 当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。 默认值。
- **删除**。 当输出缓冲区已满时，执行将继续。 随着新输出的生成，会丢弃最早的输出。

**块** 保留数据，但可能会中断命令。 值 **Drop** 允许命令完成，但是可能会丢失数据。 当使用 **Drop** 值时，请将命令输出重定向到磁盘上的文件。 对于断开连接的会话，建议使用此值。

会话配置的 **OutputBufferingMode** 属性确定使用会话配置的会话的默认输出缓冲模式。

若要查找会话配置的 **OutputBufferingMode** 值，可以使用以下任一命令格式：

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

您可以重写会话配置中的默认值，并在创建 PSSession、断开连接以及重新连接时设置 PSSession 的输出缓冲模式。

如果你是远程计算机上 Administrators 组的成员，则可以创建和更改会话配置的输出缓冲模式。

若要创建具有 **drop** 的输出缓冲模式的 PSSession，请创建一个 `$PSSessionOption` 首选项变量，其中 **OutputBufferingMode** 属性的值将被 **删除**。

当您创建 Pssession 时，变量中的值 `$PSSessionOption` 优先于会话配置中的值。

例如：

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

若要创建具有 **drop** 的输出缓冲模式的 PSSession，请使用 Cmdlet 的 **OutputBufferingMode** 参数 `New-PSSessionOption` 创建具有 **drop** 值的 session 选项。 然后，在或 cmdlet 的 **SessionOption** 参数的值中使用 session 选项 `New-PSSession` `Invoke-Command` 。

创建会话时设置的值优先于 `$PSSessionOption` 首选项变量和会话配置中设置的值。

例如：

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

若要在断开连接时更改 PSSession 的输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `Disconnect-PSSession` 。

例如：

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

若要在重新连接时更改 PSSession 的输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `New-PSSessionOption` 创建具有 **Drop** 值的 session 选项。 然后，在或的 **SessionOption** 参数的值中使用 session 选项 `Connect-PSSession` `Receive-PSSession` 。

例如：

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

若要创建具有 **drop** 的默认输出缓冲模式的会话配置，请使用 Cmdlet 的 **OutputBufferingMode** 参数 `New-PSTransportOption` 创建具有 **drop** 值的传输选项对象。 然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Register-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

若要更改会话配置的默认输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `New-PSTransportOption` 创建具有 **Drop** 值的传输选项。 然后，在的 **SessionOption** 参数的值中使用 Transport 选项 `Set-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>断开环回会话连接

环回会话（或本地会话）是在同一台计算机上发起和终止的 Pssession。 与其他 Pssession 一样，活动环回会话在连接的远程端上的计算机上保持 (本地计算机) ，因此你可以断开与环回会话的连接并重新连接到环回会话。

默认情况下，使用网络安全令牌创建环回会话，该令牌不允许在会话中运行命令来访问其他计算机。 你可以从本地计算机或远程计算机上的任何会话中重新连接到具有网络安全令牌的环回会话。

但是，如果使用、或 cmdlet 的 **EnableNetworkAccess** 参数 `New-PSSession` ，则将 `Enter-PSSession` `Invoke-Command` 使用交互式安全令牌创建环回会话。 交互式令牌允许在环回会话中运行的命令从其他计算机中获取数据。

可以将环回会话与交互式令牌断开连接，然后从同一台计算机上的同一会话或不同会话重新连接到这些会话。
但是，若要防止恶意访问，你可以使用交互式令牌仅从创建它们的计算机重新连接到环回会话。

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>在断开连接的会话中等待作业

该 `Wait-Job` cmdlet 将等待作业完成，然后返回到命令提示符或下一个命令。 默认情况下， `Wait-Job` 如果正在运行作业的会话断开连接，则返回。 若要指示 `Wait-Job` cmdlet 等到会话重新连接，请在 "已 **打开** " 状态中使用 **Force** 参数。 有关详细信息，请参阅 [等待作业](xref:Microsoft.PowerShell.Core.Wait-Job)。

## <a name="robust-sessions-and-unintentional-disconnection"></a>可靠会话和无意断开连接

由于计算机故障或网络中断，PSSession 可能会无意中断开连接。 PowerShell 尝试恢复 PSSession，但其成功与否取决于原因的严重性和持续时间。

无意间断开连接的 PSSession 的状态可能会 **断开** 或 **关闭**，但也可能会 **断开连接**。 如果 " **状态** " 的值为 "已 **断开连接**"，则可以使用相同的方法来管理 PSSession，就像在有意断开会话的情况下一样。 例如，你可以使用 `Connect-PSSession` cmdlet 重新连接到会话和 `Receive-PSSession` cmdlet，以获取在断开会话时运行的命令的结果。

如果关闭 (exit) 在 PSSession 中运行命令时创建了 PSSession 的会话，则 PowerShell 会在远程计算机上以 **断开连接** 状态维护 pssession。 如果关闭了 (exit) 在其中创建了 PSSession 的会话，但未在 PSSession 中运行命令，则 PowerShell 不会尝试维护 PSSession。

## <a name="see-also"></a>请参阅

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Receive-PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

