---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 4bc7ba3a8129dd332b13bee30e386dd459d92226
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596436"
---
# Receive-PSSession

## 摘要

获取断开连接的会话中的命令的结果

## SYNTAX

### 会话（默认）

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ID

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### SessionName

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

该 `Receive-PSSession` cmdlet 将获取已断开连接 (**PSSession**) 在 PowerShell 会话中运行的命令的结果。 如果会话当前已连接，则 `Receive-PSSession` 获取在断开会话连接时正在运行的命令的结果。 如果会话仍处于断开连接状态，将 `Receive-PSSession` 连接到该会话，恢复已挂起的任何命令，并获取在该会话中运行的命令的结果。

此 cmdlet 是在 PowerShell 3.0 中引入的。

除命令外，还可以使用 `Receive-PSSession` 或而不是 `Connect-PSSession` 命令。
`Receive-PSSession` 可以连接到在其他会话中或在其他计算机上启动的任何断开连接或重新连接的会话。

`Receive-PSSession`适用于使用 `Disconnect-PSSession` cmdlet 或 `Invoke-Command` **InDisconnectedSession** 参数故意断开连接的 pssession。 或无意中断开了网络中断。

如果使用 `Receive-PSSession` cmdlet 连接到没有运行或挂起的命令的会话，将 `Receive-PSSession` 连接到该会话，但不会返回任何输出或错误。

有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。

一些示例使用展开缩短行长度，提高可读性。 有关详细信息，请参阅 [about_Splatting](./About/about_Splatting.md)。

## 示例

### 示例1：连接到 PSSession

此示例连接到远程计算机上的会话，并获取正在会话中运行的命令的结果。

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

`Receive-PSSession`用 **ComputerName** 参数指定远程计算机。 **Name** 参数标识 Server01 计算机上的 ITTask 会话。 该示例获取在 ITTask 会话中运行的命令的结果。

由于该命令不使用 **OutTarget** 参数，因此结果将显示在命令行上。

### 示例2：获取断开连接的会话上的所有命令的结果

此示例获取在两台远程计算机上的所有已断开连接的会话中运行的所有命令的结果。

如果任何会话未断开连接或未运行命令，则 `Receive-PSSession` 不会连接到会话，并且不会返回任何输出或错误。

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession` 使用 **ComputerName** 参数来指定远程计算机。 对象将向下发送到 `Receive-PSSession` 。

### 示例3：获取会话中运行的脚本的结果

此示例使用 `Receive-PSSession` cmdlet 获取在远程计算机的会话中运行的脚本的结果。

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

该命令使用 **ComputerName** 和 **Name** 参数来标识断开连接的会话。
它将 **OutTarget** 参数与的值一起使用，以指示将 `Receive-PSSession` 结果作为作业返回。 **JobName** 参数在重新连接的会话中指定作业的名称。
**Credential** 参数 `Receive-PSSession` 使用域管理员的权限运行命令。

输出显示将 `Receive-PSSession` 结果作为作业返回到当前会话中。 若要获取作业结果，请使用 `Receive-Job` 命令

### 示例4：在网络中断后获取结果

此示例在 `Receive-PSSession` 网络中断中断会话连接后，使用 cmdlet 来获取作业的结果。 PowerShell 会在接下来的4分钟内自动尝试重新连接会话一次，并且仅当四分钟时间间隔内的所有尝试均失败时，才放弃工作。

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

`New-PSSession`Cmdlet 在 Server01 计算机上创建会话，并将会话保存在变量中 `$s` 。 `$s`变量显示 **状态** 为已打开且 **可用性** 可用。 这些值表明你已连接到该会话，并且可以在该会话中运行命令。

Cmdlet 在该 `Invoke-Command` 变量的会话中运行脚本 `$s` 。 该脚本开始运行并返回数据，但如果出现网络故障，可能会中断该会话。 用户必须退出该会话并重新启动本地计算机。

当计算机重新启动时，用户启动 PowerShell 并运行 `Get-PSSession` 命令来获取 Server01 计算机上的会话。 此输出显示 **AD** 会话仍存在于 Server01 计算机上。 该 **状态** 指示 **AD** 会话已断开连接。 "无" 的 **可用性** 值指示该会话未连接到任何客户端会话。

`Receive-PSSession`Cmdlet 可重新连接到 **AD** 会话，并获取在该会话中运行的脚本的结果。 该命令使用 **OutTarget** 参数来请求名为 **ADJob** 的作业中的结果。 该命令返回一个作业对象，输出指示该脚本仍在运行。

`Get-PSSession`Cmdlet 用于检查作业状态。 输出确认 `Receive-PSSession` cmdlet 已重新连接到 **AD** 会话，后者现在已打开且可用于命令。 而且，该脚本将继续执行并获得脚本结果。

### 示例5：重新连接到断开连接的会话

此示例使用 `Receive-PSSession` cmdlet 重新连接到有意断开连接的会话，并获取正在会话中运行的作业的结果。

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

`Invoke-Command`Cmdlet 在三台远程计算机上运行脚本。 由于该脚本收集并汇总多个数据库中的数据，因此它通常会延长脚本的时间。 该命令使用 **InDisconnectedSession** 参数，该参数可启动脚本，然后立即断开会话连接。 **SessionOption** 参数扩展已断开连接的会话的 **IdleTimeout** 值。 断开连接的会话在断开连接后被视为处于空闲状态。 务必将空闲超时设置为足够长的时间，以便这些命令可以完成，你可以重新连接到该会话。 仅当你创建 **PSSession** 并在断开连接时进行更改时才可以设置 **IdleTimeout** 。 当你连接到 **PSSession** 或接收其结果时，无法更改 **IdleTimeout** 值。 运行该命令后，用户将退出 PowerShell 并关闭计算机。

接下来，用户恢复 Windows，启动 PowerShell，并使用 `Get-PSSession` 来获取运行脚本的会话。 此命令通过计算机名称、会话名称和会话配置的名称来标识会话，并将会话保存在 `$s` 变量中。 将显示变量的值， `$s` 并显示会话已断开连接，但不会处于繁忙状态。

`Receive-PSSession`Cmdlet 连接到变量中的会话 `$s` 并获取其结果。
该命令将结果保存在 `$Results` 变量中。 将 `$s` 显示变量，并显示会话已连接并且可用于命令。

在 `$Results` PowerShell 控制台中显示变量中的脚本结果。 如果任何结果是意外的，则用户可以在会话中运行命令来调查根本原因。

### 示例6：在断开连接的会话中运行作业

此示例显示在断开连接的会话中运行的作业会发生的情况。

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

`New-PSSession`Cmdlet 在 Server01 计算机上创建测试会话。 该命令将该会话保存在 `$s` 变量中。

`Invoke-Command`Cmdlet 在该变量的会话中运行命令 `$s` 。 该命令使用 **AsJob** 参数将命令作为作业运行，并在当前会话中创建作业对象。
命令返回保存在变量中的作业对象 `$j` 。 `$j`变量显示作业对象。

变量中的 session 对象 `$s` 会向下发送到管道 `Disconnect-PSSession` ，并且会话将断开连接。

将 `$j` 显示变量并显示断开变量中的作业对象的影响 `$j` 。 现在，该作业状态为“Disconnected”。

对 `Receive-Job` 变量中的作业运行 `$j` 。 输出显示作业开始在会话之前返回输出，而作业已断开连接。

`Connect-PSSession`Cmdlet 在同一客户端会话中运行。 命令重新连接到 Server01 计算机上的测试会话，并将会话保存在 `$s2` 变量中。

`Receive-PSSession`Cmdlet 可获取会话中正在运行的作业的结果。 由于此命令在同一会话中运行，因此 `Receive-PSSession` 默认情况下会将结果作为作业返回，并重复使用同一作业对象。 该命令将作业保存在 `$j2` 变量中。 `Receive-Job`Cmdlet 将获取该作业在变量中的结果 `$j` 。

## PARAMETERS

### -AllowRedirection

指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。

使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。 默认情况下，PowerShell 不会重定向连接，但你可以使用此参数使其重定向连接。

你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。 使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置首选项变量的 **MaximumConnectionRedirectionCount** 属性 `$PSSessionOption` 。 默认值为 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定应用程序。 此 cmdlet 仅连接到使用指定应用程序的会话。

输入连接 URI 的应用程序名称段。 例如，在以下连接 URI 中，WSMan 为应用程序名称： `http://localhost:5985/WSMAN` 。

会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。

参数的值用于选择和筛选会话。 它不会更改会话使用的应用程序。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
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
> 凭据安全支持提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权连接到断开连接的会话的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请 `Get-Item` `Get-ChildItem` 在 PowerShell 驱动器中使用或命令 `Cert:` 。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定在其中存储断开连接的会话的计算机。 会话存储在位于服务器端或接收到连接的计算机上的计算机上。 默认为本地计算机。

键入一台计算机 (FQDN) 的 NetBIOS 名称、IP 地址或完全限定的域名。
不允许使用通配符。 若要指定本地计算机，请键入计算机名、点 (`.`) 、 `$env:COMPUTERNAME` 或 localhost。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

指定会话配置的名称。 此 cmdlet 仅连接到使用指定会话配置的会话。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则将在其前面预置以下架构 URI：

`http://schemas.microsoft.com/powershell`.

会话的配置名称存储在该会话的 **ConfigurationName** 属性中。

参数的值用于选择和筛选会话。 它不会更改会话使用的会话配置。

有关会话配置的详细信息，请参阅 [about_Session_Configurations](./About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定一个 URI，该 URI 定义用于重新连接到断开连接的会话的连接终结点。

URI 必须完全限定。 此字符串的格式如下所示：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

默认值如下：

`http://localhost:5985/WSMAN`

如果未指定连接 URI，则可以使用 **UseSSL**、 **ComputerName**、 **Port** 和 **ApplicationName** 参数来指定连接 uri 值。

URI 的 **Transport** 段的有效值为 HTTP 和 HTTPS。 如果使用传输段指定连接 URI，但未指定端口，则将使用标准端口80创建会话，并使用标准端口（用于 HTTP）和443（用于 HTTPS）。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权连接到断开连接的会话的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定断开连接的会话的 ID。 仅当断开连接的会话之前已连接到当前会话时， **Id** 参数才有效。

如果会话存储在本地计算机上，但未连接到当前会话，则此参数有效但无效。

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

指定断开连接的会话的实例 ID。 实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识 **PSSession** 。 实例 ID 存储在 **PSSession** 的 **InstanceID** 属性中。

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName

为返回的作业指定一个友好名称 `Receive-PSSession` 。

`Receive-PSSession` 如果 **OutTarget** 参数的值为作业，或在断开连接的会话中运行的作业已在当前会话中启动，则返回一个作业。

如果在断开连接的会话中运行的作业已在当前会话中启动，则 PowerShell 将重用会话中的原始作业对象，并忽略 **JobName** 参数的值。

如果在断开连接的会话中运行的作业已在其他会话中启动，则 PowerShell 会创建一个新的作业对象。 它使用默认名称，但你可以使用此参数来更改名称。

如果 **OutTarget** 参数的默认值或显式值不是 "作业"，则该命令将成功，但 **JobName** 参数不起作用。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定断开连接的会话的友好名称。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutTarget

确定如何返回会话结果。 此参数的可接受值为：

- **作业**。 在作业对象中异步返回结果。 你可以使用 **JobName** 参数来指定作业的名称或新名称。
- **主机**。 将结果返回到命令行（同步）。 如果正在恢复该命令或者结果由大量对象组成，则可能会延迟响应。

**OutTarget** 参数的默认值为 Host。 如果在断开连接的会话中接收的命令是在当前会话中启动的，则 **OutTarget** 参数的默认值是命令的启动形式。 如果命令作为作业启动，则默认情况下，它作为作业返回。 否则，默认情况下，它将返回到主机程序。

通常，主机程序会立即在命令行中显示返回的对象，但是此行为会有所不同。

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定用于重新连接到会话的远程计算机的网络端口。 若要连接到远程计算机，它必须侦听连接使用的端口。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用备用端口之前，必须在远程计算机上配置 WinRM 侦听器，以便侦听该端口。 若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

除非有必要，否则不要使用 **Port** 参数。 命令中设置的端口适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定断开连接的会话。 输入包含 **pssession** 的变量或者创建或获取 **pssession** 的命令（如 `Get-PSSession` 命令）。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
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

有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。 有关 **$PSSessionOption** 首选项变量的信息，请参阅 [about_Preference_Variables](./About/about_Preference_Variables.md)。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](./About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指示此 cmdlet 使用安全套接字层 (SSL) 协议连接到断开连接的会话。 默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。

如果使用此参数，并且 SSL 在用于命令的端口上不可用，则该命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
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

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

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

你可以通过管道将会话对象传递给此 cmdlet，例如 cmdlet 返回的对象 `Get-PSSession` 。

### System.Int32

可以将会话 Id 通过管道传递给此 cmdlet。

### System.Guid

可以通过管道将会话的实例 Id 传递给此 cmdlet。

### System.String

可以通过管道将会话名称传递给此 cmdlet。

## 输出

### System.web、或 PSObject

此 cmdlet 将返回在断开连接的会话中运行的命令的结果（如果有）。 如果 **OutTarget** 参数的值或默认值为 job，则 `Receive-PSSession` 返回一个作业对象。 否则，它将返回表示命令结果的对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

`Receive-PSSession` 仅从已断开连接的会话中获取结果。 只有连接到或终止运行 PowerShell 3.0 或更高版本的计算机的会话才能断开和重新连接。

如果在断开连接的会话中运行的命令未生成结果，或结果已返回到另一个会话，则 `Receive-PSSession` 不会生成任何输出。

会话的输出缓冲模式确定会话断开连接时会话中的命令如何管理输出。 当删除会话的 **OutputBufferingMode** 选项的值并且输出缓冲区已满时，该命令将开始删除输出。 `Receive-PSSession` 无法恢复此输出。 有关输出缓冲模式选项的详细信息，请参阅 [PSSessionOption](New-PSSessionOption.md) 和 [new-pstransportoption](New-PSTransportOption.md) cmdlet 的帮助文章。

当你连接到 **pssession** 或接收结果时，你无法更改 **PSSession** 的空闲超时值。 的 **SessionOption** 参数 `Receive-PSSession` 采用具有 **IdleTimeout** 值的 **SessionOption** 对象。 但是，在   `$PSSessionOption` 连接到 **PSSession** 或接收结果时，将忽略 SessionOption 对象的 idletimeout 值和该变量的 idletimeout 值。

- 您可以在创建 **pssession** 时，通过使用 `New-PSSession` 或 `Invoke-Command` cmdlet 以及从 **Pssession** 断开连接来设置和更改 pssession 的空闲超时。
- **PSSession** 的 **IdleTimeout** 属性对断开连接的会话至关重要，因为它确定断开连接的会话在远程计算机上保留的时间。 断开连接的会话从其断开连接的时刻起就被视为空闲，即使命令正在断开连接的会话中运行也是如此。

如果使用 cmdlet 的 **AsJob** 参数在远程会话中启动作业 `Invoke-Command` ，则会在当前会话中创建作业对象，即使该作业在远程会话中运行也是如此。 如果断开与远程会话的连接，则当前会话中的作业对象会断开与该作业的连接。 作业对象包含返回给它的任何结果，但不会从已断开连接的会话中的作业接收到新结果。

如果其他客户端连接到包含正在运行的作业的会话，则在新连接的会话中，传递给原始会话中的原始作业对象的结果不可用。 在重新连接的会话中只能使用未传递给原始作业对象的结果。

同样，如果在会话中启动脚本，然后断开与该会话的连接，则该脚本在断开连接之前传递给该会话的所有结果都不能用于连接到该会话的其他客户端。

若要防止要断开连接的会话中的数据丢失，请使用 cmdlet 的 **InDisconnectedSession** 参数 `Invoke-Command` 。 由于此参数会阻止结果返回到当前会话，因此在重新连接该会话后所有结果均可用。

还可以通过使用 `Invoke-Command` cmdlet `Start-Job` 在远程会话中运行命令来防止数据丢失。 在此情况下，将在远程会话中创建作业对象。 不能使用 `Receive-PSSession` cmdlet 来获取作业结果。 请改用 `Connect-PSSession` cmdlet 连接到会话，然后使用 `Invoke-Command` cmdlet `Receive-Job` 在会话中运行命令。

当包含正在运行的作业的会话断开连接，然后重新连接后，仅当该作业断开连接并重新连接到同一会话时才会重新使用原始作业对象，并且用于重新连接的命令不指定新的作业名称。 如果会话重新连接到其他客户端会话或者指定了新的作业名称，PowerShell 将为新会话创建一个新的作业对象。

断开 **PSSession** 的连接时，会话状态将断开连接，并且可用性为 None。

- **State** 属性的值是相对于当前会话的。 如果值为 "已断开连接"，则意味着 **PSSession** 未连接到当前会话。 但是，它并不意味着 **PSSession** 会与所有会话断开连接。 它可能连接到另一个会话。
  若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。
- **Availability** 的 None 值指示可连接会话。 值为 "忙碌" 表示无法连接到 **PSSession** ，因为它已连接到另一个会话。
- 有关会话 **状态** 属性的值的详细信息，请参阅 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)。
- 有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相关链接

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
