---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 4b40d765002791f45f093c7912b8f9ba58248da9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603415"
---
# New-PSSession

## 摘要
创建与本地或远程计算机的持续性连接。

## SYNTAX

### ComputerName（默认值）

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Uri

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### 会话

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### UseWindowsPowerShellParameterSet

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### SSHHost

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### SSHHostHashParam

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## DESCRIPTION

`New-PSSession`Cmdlet 在本地或远程计算机上 (**PSSession**) 创建 PowerShell 会话。 创建 **PSSession** 时，PowerShell 会建立与远程计算机的持久连接。

使用 **PSSession** 运行共享数据的多个命令，例如函数或变量的值。 若要在 **PSSession** 中运行命令，请使用 `Invoke-Command` cmdlet。 若要使用 **PSSession** 直接与远程计算机交互，请使用 `Enter-PSSession` cmdlet。 有关详细信息，请参阅 [about_PSSessions](about/about_PSSessions.md)。

您可以在远程计算机上运行命令，而无需使用或的 **ComputerName** 参数创建 `Enter-PSSession` PSSession `Invoke-Command` 。 使用 **ComputerName** 参数时，PowerShell 会创建一个临时连接，该连接用于命令，然后关闭。

从 PowerShell 6.0 开始，可以使用安全外壳 (SSH) 建立与远程计算机的连接，并在远程计算机上创建会话，如果本地计算机上有 SSH 并且远程计算机配置了 PowerShell SSH 终结点。 基于 SSH 的 PowerShell 远程会话的优点在于，它可以跨多个平台运行 (Windows、Linux、macOS) 。 对于基于 SSH 的会话，请使用 **HostName** 或 **SSHConnection** 参数集来指定远程计算机和相关的连接信息。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

> [!NOTE]
> 如果使用的是来自 Linux 或 macOS 客户端的 WSMan 远程处理，并且该终结点的服务器证书不受信任 (例如，自签名证书) 。 必须提供 `PSSessionOption` 包含和的， `-SkipCACheck` `-SkipCNCheck` 才能成功建立连接。 仅当你在可以确定服务器证书和目标系统的网络连接的环境中时，才执行此操作。

## 示例

### 示例1：在本地计算机上创建会话

```powershell
$s = New-PSSession
```

此命令在本地计算机上创建新的 **pssession** ，并将 **PSSession** 保存在 `$s` 变量中。

你现在可以使用此 **PSSession** 在本地计算机上运行命令。

### 示例2：在远程计算机上创建会话

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

此命令在 Server01 计算机上创建新的 **PSSession** ，并将其保存在 `$Server01` 变量中。

创建多个 **PSSession** 对象时，将它们分配给具有有用名称的变量。 这将帮助你在后续命令中管理 **PSSession** 对象。

### 示例3：在多台计算机上创建会话

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

此命令在 **ComputerName** 参数指定的每台计算机上创建三个 **PSSession** 对象。

该命令使用赋值运算符 (=) 将新的 **PSSession** 对象分配给变量： `$s1` 、 `$s2` 、 `$s3` 。 它将 Server01 **pssession** 分配给 `$s1` ，将 Server02 **pssession** 分配给 `$s2` ，并将 Server03 **pssession** 分配给 `$s3` 。

将多个对象分配给一系列变量时，PowerShell 会将每个对象分别分配到序列中的变量。 如果对象多于变量，则所有剩余对象都将分配给最后一个变量。 如果变量多于对象，则剩余变量为空 (null)。

### 示例4：使用指定的端口创建会话

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

此命令在 Server01 计算机上创建一个新的 **PSSession** ，该计算机连接到服务器端口8081并使用 SSL 协议。 新的 **PSSession** 使用名为 E12 的备用会话配置。

在设置端口前，你必须将远程计算机上的 WinRM 侦听器配置为侦听端口 8081。 有关详细信息，请参阅 **Port** 参数的描述。

### 示例5：基于现有会话创建会话

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

此命令创建与现有 **pssession** 具有相同属性的 **PSSession** 。 如果现有 **pssession** 的资源耗尽，需要新的 **pssession** 来分担某些需求，则可以使用此命令格式。

该命令使用的 **Session** 参数 `New-PSSession` 来指定保存在变量中的 PSSession `$s` 。 它使用 Domain1\Admin01 用户的凭据来完成命令。

### 示例6：在不同的域中创建具有全局作用域的会话

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

此示例演示如何在不同域中的计算机上创建具有全局作用域的 **PSSession** 。

默认情况下，在命令行创建的 **pssession** 对象是使用本地范围创建的，并且在脚本中创建的 **pssession** 对象具有脚本作用域。

若要创建具有全局作用域的 **pssession** ，请创建一个新的 **pssession** ，然后将该 **pssession** 存储在强制转换为全局作用域的变量中。 在这种情况下， `$s` 变量将强制转换为全局范围。

该命令使用 **ComputerName** 参数指定远程计算机。 由于计算机与用户帐户在不同的域中，因此会将计算机的全名与用户的凭据一起指定。

### 示例7：创建多台计算机的会话

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

此命令在 Servers.txt 文件中列出的每台200计算机上创建 **PSSession** ，并将生成的 **pssession** 存储在 `$rs` 变量中。 **PSSession** 对象的中止值限制为50。

当计算机名称存储在数据库、电子表格、文件文件中或以其他可转换为文本的格式存储时，可以使用此命令格式。

### 示例8：使用 URI 创建会话

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

此命令在 Server01 计算机上创建 **PSSession** ，并将其存储在 `$s` 变量中。 它使用 **URI** 参数指定传输协议、远程计算机、端口和备用会话配置。 它还使用 **Credential** 参数指定有权在远程计算机上创建会话的用户帐户。

### 示例9：在一组会话中运行后台作业

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

这些命令创建一组 **pssession** 对象，然后在每个 **PSSession** 对象中运行一个后台作业。

第一个命令在 Servers.txt 文件中列出的每台计算机上创建一个新的 **PSSession** 。 它使用 `New-PSSession` cmdlet 创建 **PSSession**。 **ComputerName** 参数的值是一个命令，该命令使用 `Get-Content` cmdlet 来获取 Servers.txt 文件的计算机名称的列表。

该命令使用 **Credential** 参数创建具有域管理员权限的 **PSSession** 对象，并使用 **ThrottleLimit** 参数将该命令限制为16个并发连接。 该命令将 **PSSession** 对象保存在 `$s` 变量中。

第二个命令使用 cmdlet 的 **AsJob** 参数 `Invoke-Command` 启动一个后台作业，该作业在 `Get-Process PowerShell` 中的每个 **PSSession** 对象中运行一个命令 `$s` 。

有关 PowerShell 后台作业的详细信息，请参阅 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。

### 示例10：使用其 URI 为计算机创建会话

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

此命令创建连接到由 URI （而不是计算机名称）指定的计算机的 **PSSession** 对象。

### 示例11：创建会话选项

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

此示例演示如何创建 session 选项对象并使用 **SessionOption** 参数。

第一个命令使用 `New-PSSessionOption` cmdlet 来创建会话选项。 它将生成的 **SessionOption** 对象保存在 `$so` 变量中。

第二个命令在新会话中使用该选项。 该命令使用 `New-PSSession` cmdlet 创建新的会话。 SessionOption 参数的值是变量中的 **SessionOption** 对象 `$so` 。

### 示例12：使用 SSH 创建会话

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

此示例演示如何使用安全外壳 (SSH) 创建新的 **PSSession** 。 如果在远程计算机上配置了 SSH 以提示输入密码，则会出现密码提示。 否则，你将需要使用基于 SSH 密钥的用户身份验证。

### 示例13：使用 SSH 创建会话并指定端口和用户身份验证密钥

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

此示例演示如何使用安全外壳 (SSH) 创建 **PSSession** 。 它使用 **port** 参数指定要使用的端口，并使用 **KeyFilePath** 参数来指定用于在远程计算机上标识和验证用户身份的 RSA 密钥。

### 示例14：使用 SSH 创建多个会话

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

此示例演示如何使用安全外壳 (SSH) 和 **SSHConnection** 参数集创建多个会话。 **SSHConnection** 参数采用包含每个会话的连接信息的哈希表数组。 请注意，此示例要求目标远程计算机已配置 SSH 以支持基于密钥的用户身份验证。

## PARAMETERS

### -AllowRedirection

指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。

使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。 默认情况下，PowerShell 不会重定向连接，但你可以使用此参数使其重定向连接。

你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。 使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置 **$PSSessionOption** 首选项变量的 **MaximumConnectionRedirectionCount** 属性。 默认值为 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定连接 URI 的应用程序名称段。 当命令中未使用 **ConnectionURI** 参数时，请使用此参数指定应用程序名称。

默认值为 `$PSSessionApplicationName` 本地计算机上首选项变量的值。 如果未定义此首选项变量，则默认值为 WSMAN。 该值适用于大多数使用情况。 有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

WinRM 服务使用应用程序名称来选择为连接请求提供服务的侦听器。
此参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值匹配。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定用于对用户的凭据进行身份验证的机制。
此参数的可接受值为：

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
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权执行此操作的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或命令。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定计算机的名称数组。 此 cmdlet 创建 (**PSSession**) 到指定计算机的持续性连接。 如果输入多个计算机名称，则会 `New-PSSession` 创建多个 **PSSession** 对象，每台计算机一个。 默认为本地计算机。

键入一台或多台远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。 若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。 当计算机与用户处于不同的域中时，必须使用完全限定的域名。 还可以通过管道将计算机名称传递给 `New-PSSession` 。

若要在 **ComputerName** 参数的值中使用 IP 地址，该命令必须包括 **Credential** 参数。 此外，必须为计算机配置 HTTPS 传输，或者必须在本地计算机上的 WinRM TrustedHosts 列表中包含远程计算机的 IP 地址。 有关将计算机名称添加到 TrustedHosts 列表的说明，请参阅 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)中的 "如何将计算机添加到受信任的主机列表中"。

若要在 **ComputerName** 参数的值中包含本地计算机，请使用 "以管理员身份运行" 选项启动 Windows PowerShell。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

指定用于新的 **PSSession** 的会话配置。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/PowerShell` 。

会话的会话配置位于远程计算机上。 如果远程计算机上不存在指定的会话配置，则该命令会失败。

默认值为 `$PSSessionConfigurationName` 本地计算机上首选项变量的值。 如果未设置此首选项变量，则默认值为 Microsoft.PowerShell。 有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定一个 URI，该 URI 定义会话的连接终结点。 URI 必须完全限定。 此字符串的格式如下：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

默认值如下：

`http://localhost:5985/WSMAN`

如果未指定 **ConnectionURI**，则可以使用 **UseSSL**、**ComputerName**、**Port** 和 **ApplicationName** 参数来指定 **ConnectionURI** 值。

URI 的 Transport 段的有效值为 HTTP 和 HTTPS。 如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的 Id 的数组。 此 cmdlet 将启动与每个指定容器的交互式会话。 使用 `docker ps` 命令获取容器 id 列表。 有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指示此 cmdlet 将交互式安全令牌添加到环回会话。 通过交互式令牌，你可以在环回会话中运行用于获取其他计算机中的数据的命令。 例如，你可以在该会话中运行用于将 XML 文件从远程计算机复制到本地计算机的命令。

环回会话是在同一计算机上开始并终止的 **PSSession**。 若要创建环回会话，请省略 **ComputerName** 参数，或将其值设置为 (. ) 、localhost 或本地计算机的名称。

默认情况下，此 cmdlet 使用网络令牌创建环回会话，该令牌可能不提供足够的权限来向远程计算机进行身份验证。

**EnableNetworkAccess** 参数仅在环回会话中有效。 如果在远程计算机上创建会话时使用 **EnableNetworkAccess** ，则该命令将成功，但会忽略此参数。

你还可以通过使用 **Authentication** 参数的 CredSSP 值，在环回会话中启用远程访问，该参数将会话凭据委派给其他计算机。

若要保护计算机免受恶意访问，已断开连接的具有交互式令牌（使用 **EnableNetworkAccess** 参数创建的令牌）的环回会话只能通过创建该会话的计算机重新连接。 断开连接的使用 CredSSP 身份验证的会话可通过其他计算机重新连接。 有关详细信息，请参阅 `Disconnect-PSSession`。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

指定安全外壳 (基于 SSH) 连接的计算机名称的数组。 这与 ComputerName 参数类似，不同之处在于使用 SSH 而不是 Windows WinRM 建立与远程计算机的连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

指定安全外壳 (SSH) 用于对远程计算机上的用户进行身份验证的密钥文件路径。

SSH 允许通过私有/公共密钥执行用户身份验证，作为基本密码身份验证的替代方法。 如果将远程计算机配置为进行密钥身份验证，则可以使用此参数来提供用于标识用户的密钥。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定 **PSSession** 的友好名称。

使用其他 cmdlet （如和）时，可以使用名称来引用 **PSSession** `Get-PSSession` `Enter-PSSession` 。 对于计算机或当前会话，该名称无需是唯一的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定远程计算机上用于此连接的网络端口。 若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用其他端口之前，必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。 使用以下命令配置侦听器：

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

除非必要，否则不要使用 **Port** 参数。 命令中的端口设置适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

指示 **PSSession** 以管理员身份运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定一个 **PSSession** 对象数组，此 cmdlet 将其用作新 **PSSession** 的模型。 此参数创建与指定的 **pssession** 对象具有相同属性的新 **PSSession** 对象。

输入包含 **pssession** 对象的变量或创建或获取 **pssession** 对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。

生成的 **PSSession** 对象具有相同的计算机名称、应用程序名称、连接 URI、端口、配置名称、中止值和安全套接字层 (SSL) 值作为原始对象，但它们具有不同的显示名称、id 和实例 ID (GUID) 。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

为该会话指定高级选项。 输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。

选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。 否则，通过在会话配置中设置的选项创建默认值。

会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。

有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。 有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

此参数采用哈希表数组，其中每个哈希表都包含一个或多个建立安全外壳 (SSH) 连接 (HostName、Port、UserName、KeyFilePath) 所需的连接参数。

哈希表连接参数与为 **主机名** 参数集定义的参数相同。

**SSHConnection** 参数适用于创建多个会话，其中每个会话需要不同的连接信息。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

指示使用安全外壳 (SSH) 建立远程连接。

默认情况下，PowerShell 使用 Windows WinRM 连接到远程计算机。 此开关强制 PowerShell 使用 HostName 参数集建立基于 SSH 的远程连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定为运行此命令可建立的并发连接的最大数目。
如果省略此参数或输入 0（零）值，则使用默认值 32。

节流限制仅适用于当前命令，而不适用于会话或计算机。

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

指定用于在远程计算机上创建会话的帐户的用户名。 用户身份验证方法取决于如何在远程计算机上配置 (SSH) 安全外壳。

如果 SSH 配置了基本密码身份验证，则系统将提示你输入用户密码。

如果 SSH 配置为基于密钥的用户身份验证，则可以通过 KeyFilePath 参数提供密钥文件路径，并且不会出现密码提示。 请注意，如果客户端用户密钥文件位于 SSH 已知位置，则基于密钥的身份验证不需要 KeyFilePath 参数，并且将根据用户名自动进行用户身份验证。 有关详细信息，请参阅 SSH 文档关于基于密钥的用户身份验证。

这不是必需的参数。 如果未指定用户名参数，则将使用当前登录的用户名作为连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指示此 cmdlet 使用 SSL 协议建立与远程计算机的连接。
默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 参数提供额外的保护，可通过 HTTPS 连接而不是 HTTP 连接来发送数据。

如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

指定虚拟机的 ID 的数组。 此 cmdlet 与每个指定的虚拟机启动交互会话。 若要查看可供你使用的虚拟机，请使用以下命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定一个虚拟机的名称数组。 此 cmdlet 与每个指定的虚拟机启动交互会话。 若要查看可供你使用的虚拟机，请使用 `Get-VM` cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -子系统

指定用于新的 **PSSession** 的 SSH 子系统。

此项指定要在目标上使用的子系统（如 sshd_config 中所定义）。
子系统使用预定义参数启动特定版本的 PowerShell。
如果远程计算机上不存在指定的子系统，则该命令将失败。

如果未使用此参数，则默认值为 "powershell" 子系统。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseWindowsPowerShell

{{填充 UseWindowsPowerShell 说明}}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216) 。

## 输入

### System.object、System.string、System.web. （.）

可以通过管道将 string、URI 或 session 对象传递给此 cmdlet。

## 输出

### System.Management.Automation.Runspaces.PSSession

## 注释

- 此 cmdlet 使用 PowerShell 远程处理基础结构。 若要使用此 cmdlet，必须为本地计算机和任何远程计算机配置 PowerShell 远程处理。 有关详细信息，请参阅 [about_Remote_Requirements](About/about_Remote_Requirements.md)。
- 若要在本地计算机上创建 **PSSession** ，请使用 "以管理员身份运行" 选项启动 PowerShell。
- 使用完 **pssession** 后，请使用 `Remove-PSSession` cmdlet 删除 **pssession** ，并释放其资源。
- 从 PowerShell 6.0 开始， **主机名** 和 **SSHConnection** 参数集已包括在内。
  添加它们是为了提供基于 (SSH) 安全外壳的 PowerShell 远程处理。 SSH 和 PowerShell 在多个平台上都受支持 (Windows、Linux、macOS) ，PowerShell 远程处理将在安装和配置 PowerShell 和 SSH 的这些平台上运行。 这不同于以前仅限 Windows 的基于 WinRM 的远程处理，并且很多 WinRM 特定功能和限制不适用。 例如，目前不支持基于 WinRM 的配额、会话选项、自定义终结点配置和断开/重新连接功能。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

