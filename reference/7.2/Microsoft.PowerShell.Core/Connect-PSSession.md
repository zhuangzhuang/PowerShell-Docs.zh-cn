---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: fda672ba4f6dafc9f955ef8025c386f7732d81bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596427"
---
# Connect-PSSession

## 摘要
重新连接到已断开连接的会话。

## SYNTAX

### Name（默认值）

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 会话

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 计算机名

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ID

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Connect-PSSession` Cmdlet 会重新连接到已断开连接 (**Pssession**) 的用户管理的 PowerShell 会话。 它适用于有意断开连接的会话（例如通过使用 cmdlet `Disconnect-PSSession` 或 cmdlet 的 **InDisconnectedSession** 参数） `Invoke-Command` 以及无意中断开连接的会话（如临时网络中断）。

`Connect-PSSession` 可以连接到由同一用户启动的任何断开连接的会话。 其中包括通过其他计算机上的其他会话启动或断开连接。

但是， `Connect-PSSession` 无法连接到已损坏或已关闭的会话，或使用 cmdlet 启动的交互式会话 `Enter-PSSession` 。 此外，也无法将会话连接到由其他用户启动的会话，除非你能提供创建会话的用户的凭据。

有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例1：重新连接到会话

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

此命令重新连接到 Server01 计算机上的 ITTask 会话。

该输出显示此命令已成功。 此时将打开会话的 **状态** ，并且 **可用性** 可用，这表示你可以在该会话中运行命令。

### 示例2：断开连接和重新连接的影响

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

此示例显示了断开某一会话的连接又重新连接到该会话的效果。

第一个命令使用 `Get-PSSession` cmdlet。 在没有 **ComputerName** 参数的情况下，该命令仅获取已在当前会话中创建的会话。

该输出显示此命令可获取本地计算机上的 Backup 会话。 会话 **状态** 已打开且 **可用性** 可用。

第二个命令使用 `Get-PSSession` cmdlet 获取在当前会话中创建的 **PSSession** 对象，并使用 `Disconnect-PSSession` cmdlet 来断开会话连接。 该输出显示 Backup 会话已断开连接。 会话的 **状态** 为 "已断开连接" 且 **可用性** 为 "无"。

第三个命令使用 `Get-PSSession` cmdlet 获取在当前会话中创建的 **PSSession** 对象，并使用 `Connect-PSSession` cmdlet 来重新连接会话。 该输出显示 Backup 会话已重新连接。 会话 **状态** 已打开且 **可用性** 可用。

如果在 `Connect-PSSession` 未断开连接的会话上使用 cmdlet，则该命令不会影响会话，并且不会生成任何错误。

### 示例3：企业方案中的一系列命令

这一系列命令显示了如何 `Connect-PSSession` 在企业方案中使用 cmdlet。 在此示例中，系统管理员将在远程计算机上的会话中启动长时间运行的作业。 启动该作业后，管理员将断开与该会话的连接，然后下班回家。
在晚上晚，管理员登录到她的家庭计算机，并验证作业是否已完成。

管理员首先在远程计算机上创建会话，并在该会话中运行脚本。第一个命令使用 `New-PSSession` cmdlet 在 Server01 远程计算机上创建 ITTask 会话。 该命令使用 **ConfigurationName** 参数来指定 ITTask 会话配置。 该命令将会话保存在 `$s` 变量中。

第二个命令 `Invoke-Command` cmdlet 用于在变量中的会话中启动后台作业 `$s` 。 它使用 **FilePath** 参数在该后台作业中运行脚本。

第三个命令使用 `Disconnect-PSSession` cmdlet 断开与变量中的会话的连接 `$s` 。 该命令使用值为 Drop 的 **OutputBufferingMode** 参数，以防止通过将输出传递到会话来阻止脚本被阻止。 它使用 **IdleTimeoutSec** 参数将会话超时时间延长至15小时。 完成该命令后，管理员会锁定她的计算机并在家回家。

此后，管理员将启动她的家庭计算机，登录到公司网络，并启动 PowerShell。 第四个命令使用 `Get-PSSession` cmdlet 来获取 Server01 计算机上的会话。 命令查找 ITTask 会话。第五个命令使用 `Connect-PSSession` cmdlet 连接到 ITTask 会话。 该命令将该会话保存在 `$s` 变量中。

第六个命令使用 `Invoke-Command` cmdlet 在 `Get-Job` 变量中的会话中运行命令 `$s` 。 输出显示该作业已成功完成。第七个命令使用 cmdlet 在会话中的 `Invoke-Command` 变量的会话中运行 `Receive-Job` 命令 `$s` 。 该命令将结果保存在 `$BackupSpecs` 变量中。第八个命令使用 `Invoke-Command` cmdlet 在会话中运行另一个脚本。 该命令使用 `$BackupSpecs` 会话中变量的值作为脚本的输入。

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

第九个命令从变量中的会话断开连接 `$s` 。管理员关闭 PowerShell 并关闭计算机。 第二天，她可以通过自己的工作计算机重新连接到该会话，并检查该脚本状态。

## PARAMETERS

### -AllowRedirection

指示此 cmdlet 允许将此连接重定向到备用 URI。

使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。 默认情况下，PowerShell 不会重定向连接，但你可以使用此参数允许它重定向连接。

你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。 使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置 **$PSSessionOption** 首选项变量的 **MaximumConnectionRedirectionCount** 属性。 默认值为 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定应用程序的名称。 此 cmdlet 仅连接到使用指定应用程序的会话。

输入连接 URI 的应用程序名称段。 例如，在以下连接 URI 中，应用程序名称为 WSMan：`http://localhost:5985/WSMAN`。 会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。

此参数的值用于选择和筛选会话。 它不会更改会话使用的应用程序。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定用于对命令中的用户凭据进行身份验证的机制，以便重新连接到断开连接的会话。 此参数的可接受值为：

- 默认
- 基本
- Credssp
- 摘要
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

默认值为 Default。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权连接到断开连接的会话的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 它们只能映射到本地用户帐户。 它们不适用于域帐户。

若要获取证书指纹，请 `Get-Item` `Get-ChildItem` 在 PowerShell Cert：驱动器中使用或命令。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定在其中存储断开连接的会话的计算机。 会话存储在位于连接的服务器端或接收端的计算机上。 默认为本地计算机。

键入计算机的 NetBIOS 名称、IP 地址或完全限定的域名。 不允许使用通配符。 若要指定本地计算机，请键入计算机名称、localhost 或点 (。 ) 

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

只连接到使用指定会话配置的会话。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。 会话的配置名称存储在该会话的 **ConfigurationName** 属性中。

此参数的值用于选择和筛选会话。 它不会更改会话使用的会话配置。

有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

为断开连接的会话指定连接终结点的 Uri。

URI 必须完全限定。 此字符串的格式如下：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

默认值如下：

`http://localhost:5985/WSMAN`

如果未指定连接 URI，则可以使用 **UseSSL** 和 **Port** 参数指定连接 uri 值。

URI 的 **Transport** 段的有效值为 HTTP 和 HTTPS。 如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权连接到断开连接的会话的用户帐户。 默认为当前用户。

键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 `PSCredential` 由 cmdlet 生成的对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定断开连接的会话的 ID。 仅当断开连接的会话之前已连接到当前会话时， **Id** 参数才有效。

如果会话存储在本地计算机上，但未连接到当前会话，则此参数是有效的，但并未生效。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定断开连接的会话的实例 ID。

实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识 **PSSession** 。

实例 ID 存储在 **PSSession** 的 **InstanceID** 属性中。

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定断开连接的会话的友好名称。

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定远程计算机上用于重新连接到会话的网络端口。 若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。 若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

除非必要，否则不要使用 **Port** 参数。 在命令中设置的端口适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定断开连接的会话。 输入包含 **pssession** 对象的变量或创建或获取 **pssession** 对象的命令（如 `Get-PSSession` 命令）。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

为该会话指定高级选项。 输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。

选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。 否则，通过在会话配置中设置的选项创建默认值。

会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。

有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。 有关 **$PSSessionOption** 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定为运行此命令可建立的并发连接的最大数目。
如果省略此参数或输入 0 值，则使用默认值 32。

节流限制仅适用于当前命令，而不适用于会话或计算机。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指示此 cmdlet 使用安全套接字层 (SSL) 协议连接到断开连接的会话。 默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 参数是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。

如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.Runspaces.PSSession

可以通过管道将会话 (**PSSession**) 传递给此 cmdlet。

## 输出

### System.Management.Automation.Runspaces.PSSession

此 cmdlet 将返回一个对象，该对象表示其重新连接到的会话。

## 注释

- 此 cmdlet 仅在 Windows 平台上可用。

- `Connect-PSSession` 仅重新连接到已断开连接的会话，即， **状态** 属性的值为 "已断开连接" 的会话。 只有连接到或结束运行 Windows PowerShell 3.0 或更高版本的计算机的会话才能断开和重新连接。

- 如果 `Connect-PSSession` 在未断开连接的会话上使用，则该命令不会影响会话，并且不会生成错误。

- 与使用 **EnableNetworkAccess** 参数创建的交互式令牌断开连接的环回会话只能通过创建该会话的计算机重新连接。 此限制可使计算机免遭恶意访问。

- **PSSession** 的 **State** 属性值相对于当前会话。
  因此，值 "已 **断开连接** " 意味着 **PSSession** 未连接到当前会话。 但是，它并不意味着 **PSSession** 会与所有会话断开连接。 它可能连接到另一个会话。 若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。

  **Availability** 的 None 值指示可连接会话。 值为 "忙碌" 指示你无法连接到 **PSSession** ，因为它已连接到另一个会话。

  有关会话的 **State** 属性的值的详细信息，请参阅 [RunspaceState 枚举](/dotnet/api/system.management.automation.runspaces.runspacestate)。

  有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate 枚举](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

- 当你连接到 **pssession** 时，你无法更改 **PSSession** 的空闲超时值。 的 **SessionOption** 参数 `Connect-PSSession` 采用具有 **IdleTimeout** 值的 **SessionOption** 对象。 但是，在   `$PSSessionOption` 连接到 **PSSession** 时，将忽略 SessionOption 对象的 idletimeout 值和该变量的 idletimeout 值。

  您可以在创建 **pssession** 时，通过使用 `New-PSSession` 或 `Invoke-Command` cmdlet 以及从 **Pssession** 断开连接来设置和更改 pssession 的空闲超时。

  **PSSession** 的 **IdleTimeout** 属性对断开连接的会话至关重要，因为它确定断开连接的会话在远程计算机上保留的时间。 断开连接的会话从其断开连接的时刻起就被视为空闲，即使命令正在断开连接的会话中运行也是如此。

## 相关链接

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)
