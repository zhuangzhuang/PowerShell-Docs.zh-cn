---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 9c08e78d840815a396b55eb26bf8e21d73cb81aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598262"
---
# Enter-PSSession

## 摘要
启动与远程计算机的交互式会话。

## SYNTAX

### ComputerName（默认值）

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### SSHHost

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### 会话

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### Uri

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### ID

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### 名称

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### ContainerId

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## DESCRIPTION

`Enter-PSSession`Cmdlet 可启动与单台远程计算机的交互式会话。
在会话期间，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。 一次只可以进行一个交互式会话。

通常，你可以使用 **ComputerName** 参数来指定远程计算机的名称。
但是，你还可以使用通过 `New-PSSession` cmdlet 为交互式会话创建的会话。 但是，不能使用 `Disconnect-PSSession` 、 `Connect-PSSession` 或 cmdlet 与 `Receive-PSSession` 交互式会话断开连接或重新连接到该会话。

从 PowerShell 6.0 开始，可以使用安全外壳 (SSH) 建立与远程计算机的连接，如果本地计算机上有 SSH 并且远程计算机配置了 PowerShell SSH 终结点。 基于 SSH 的 PowerShell 远程会话的优点在于，它可以跨多个平台 (Windows、Linux、macOS) 。 对于基于 SSH 的远程处理，请使用 **HostName** 参数集指定远程计算机和相关连接信息。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

若要结束交互式会话并断开与远程计算机的连接，请使用 `Exit-PSSession` cmdlet 或类型 `exit` 。

## 示例

### 示例1：启动交互式会话

```
PS> Enter-PSSession
[localhost]: PS>
```

此命令将在本地计算机上启动交互式会话。 命令提示符将发生更改，以指示你现在正在不同的会话中运行命令。

你输入的命令将在该新会话中运行，而结果将以文本形式返回到默认会话中。

### 示例2：使用交互式会话

第一个命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 （远程计算机）的交互式会话。 会话启动时，命令提示符将更改为包含该计算机名称。

第二个命令获取 PowerShell 进程，并将输出重定向到 Process.txt 文件。 该命令将提交到远程计算机，并且该文件将保存在远程计算机上。

第三个命令使用 **Exit** 关键字来结束交互式会话并关闭连接。
第四个命令确认 Process.txt 文件是否位于远程计算机上。 `Get-ChildItem`本地计算机上的 ( "dir" ) 命令找不到该文件。

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

此命令显示了如何在与远程计算机的交互式会话中进行工作。

### 示例3：使用 Session 参数

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

这些命令使用的 **Session** 参数 `Enter-PSSession` 在 (**PSSession**) 的现有 PowerShell 会话中运行交互式会话。

### 示例4：启动交互式会话并指定端口和凭据参数

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

此命令启动与 Server01 计算机的交互式会话。 它使用 **port** 参数指定端口，并使用 **Credential** 参数指定有权连接到远程计算机的用户的帐户。

### 示例5：停止交互式会话

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

此示例显示了如何启动和停止交互式会话。 第一个命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 计算机的交互式会话。

第二个命令使用 `Exit-PSSession` cmdlet 结束会话。 你还可以使用 **Exit** 关键字来结束交互式会话。 `Exit-PSSession` 和 **退出** 具有相同的效果。

### 示例6：使用 SSH 启动交互式会话

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

此示例演示如何使用安全外壳 (SSH) 启动交互式会话。 如果在远程计算机上配置了 SSH 以提示输入密码，则会出现密码提示。
否则，你将需要使用基于 SSH 密钥的用户身份验证。

### 示例7：使用 SSH 启动交互式会话并指定端口和用户身份验证密钥

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

此示例演示如何使用 SSH 启动交互式会话。 它使用 **port** 参数指定要使用的端口，并使用 **KeyFilePath** 参数来指定用于对远程计算机上的用户进行身份验证的 RSA 密钥。

## PARAMETERS

### -AllowRedirection

允许将此连接重定向到备用统一资源标识符 (URI)。 默认情况下，不允许重定向。

使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。 默认情况下，PowerShell 不会重定向连接，但你可以使用此参数允许它重定向连接。

你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。 使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置首选项变量的 **MaximumConnectionRedirectionCount** 属性 `$PSSessionOption` 。 默认值为 5。

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

**WinRM** 服务使用应用程序名称来选择用于处理连接请求的侦听器。 此参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值匹配。

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

指定用于对用户的凭据进行身份验证的机制。 此参数的可接受值为：

- 默认
- 基本
- Credssp
- 摘要
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

默认值为 Default。

CredSSP 身份验证仅在 Windows Vista、Windows Server 2008 和更高版本的 Windows 操作系统中可用。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

警告：凭据安全支持提供程序 (CredSSP) 身份验证，其中用户的凭据将传递给要进行身份验证的远程计算机，其适用于需要在多个资源（例如访问远程网络共享）上进行身份验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

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

指定计算机名称。 此 cmdlet 将启动与指定远程计算机的交互式会话。 仅输入一个计算机名称。 默认为本地计算机。

键入计算机的 NetBIOS 名称、IP 地址或完全限定的域名。 还可以通过管道将计算机名称传递给 `Enter-PSSession` 。

若要在 **ComputerName** 参数的值中使用 IP 地址，该命令必须包括 **Credential** 参数。 此外，必须为计算机配置 HTTPS 传输，或者必须在本地计算机上的 WinRM TrustedHosts 列表中包含远程计算机的 IP 地址。 有关将计算机名称添加到 TrustedHosts 列表的说明，请参阅 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)中的 "如何将计算机添加到受信任的主机列表中"。

注意：在 Windows Vista 和更高版本的 Windows 操作系统中，若要在 **ComputerName** 参数的值中包含本地计算机，你必须以 "以管理员身份运行" 选项启动 PowerShell。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

指定用于交互式会话的会话配置。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。

与 SSH 一起使用时，指定要在目标上使用的子系统，如 sshd_config 中所定义。 SSH 的默认值为 `powershell` 子系统。

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

URI 的 Transport 段的有效值为 HTTP 和 HTTPS。 如果使用传输段指定连接 URI，但未指定端口，则通过使用标准端口80（对于 HTTP 为）创建会话，对 HTTPS 使用443。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的 ID。

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指示此 cmdlet 将交互式安全令牌添加到环回会话。 通过交互式令牌，你可以在环回会话中运行用于获取其他计算机中的数据的命令。 例如，你可以在该会话中运行用于将 XML 文件从远程计算机复制到本地计算机的命令。

环回会话是在同一计算机上开始并终止的 **PSSession**。 若要创建环回会话，请省略 **ComputerName** 参数，或将其值设置为。  (点) 、localhost 或本地计算机的名称。

默认情况下，使用网络令牌创建环回会话，该令牌可能不提供足够的权限对远程计算机进行身份验证。

**EnableNetworkAccess** 参数仅在环回会话中有效。 如果在远程计算机上创建会话时使用 **EnableNetworkAccess** ，则该命令将成功，但会忽略此参数。

通过用于将会话凭据委派给其他计算机的 **CredSSP** 参数的 **Authentication** 值，你还可以在环回会话中进行远程访问。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

指定安全外壳 (基于 SSH) 连接的计算机名称。 这与 **ComputerName** 参数类似，不同之处在于使用 SSH 而不是 Windows WinRM 建立与远程计算机的连接。 此参数支持使用格式将用户名和/或端口指定为主机名称参数值的一部分 `user@hostname:port` 。 指定为主机名一部分的用户名和/或端口优先于 `-UserName` 和 `-Port` 参数（如果已指定）。 这允许将多个计算机名称传递给此参数，其中某些计算机具有特定的用户名和/或端口，而另一些计算机使用和参数中的用户名和/或端口 `-UserName` `-Port` 。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

指定现有会话的 ID。 `Enter-PSSession` 为交互式会话使用指定的会话。

若要查找会话的 ID，请使用 `Get-PSSession` cmdlet。

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定现有会话的实例 ID。 `Enter-PSSession` 为交互式会话使用指定的会话。

实例 ID 是一个 GUID。 若要查找会话的实例 ID，请使用 `Get-PSSession` cmdlet。 你还可以使用 **Session**、 **Name** 或 **ID** 参数来指定现有会话。 或者，可以使用 **ComputerName** 参数来启动临时会话。

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

指定现有会话的友好名称。 `Enter-PSSession` 为交互式会话使用指定的会话。

如果你指定的名称与多个会话相匹配，则该命令会失败。 你还可以使用 **Session**、 **InstanceID** 或 **ID** 参数来指定现有会话。 或者，可以使用 **ComputerName** 参数来启动临时会话。

若要为会话建立友好名称，请使用该 cmdlet 的 **name** 参数 `New-PSSession` 。

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定远程计算机上用于此命令的网络端口。

在 PowerShell 6.0 中，此参数在支持安全外壳 (SSH) 连接的 **HostName** 参数集中包含。

**WinRM (ComputerName 参数集)**

若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。 使用以下命令配置侦听器：

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

除非必要，否则不要使用 **Port** 参数。 命令中的端口设置适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

**SSH (主机名参数集)**

若要连接到远程计算机，远程计算机必须配置有 SSH 服务 (SSHD) ，并且必须侦听连接使用的端口。 SSH 的默认端口是22。

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

指定要用于交互式会话 (**PSSession**) 的 PowerShell 会话。 此参数获取一个会话对象。 你还可以使用 **Name**、 **InstanceID** 或 **ID** 参数来指定 **PSSession**。

输入包含 session 对象的变量或可创建或获取会话对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。 还可以通过管道将会话对象传递给 `Enter-PSSession` 。 使用此参数只能提交一个 **PSSession** 。 如果输入包含多个 **PSSession** 的变量，则该命令将失败。

当你使用 `Exit-PSSession` 或 **EXIT** 关键字时，交互式会话将结束，但你创建的 **PSSession** 仍处于打开状态并可供使用。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

为该会话设置高级选项。 输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。

选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。 否则，通过在会话配置中设置的选项创建默认值。

会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。

有关会话选项（包括默认值）的说明，请参阅 `New-PSSessionOption` 。
有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

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

### -子系统

指定用于新的 **PSSession** 的 SSH 子系统。

此项指定要在目标上使用的子系统（如 sshd_config 中所定义）。 子系统使用预定义参数启动特定版本的 PowerShell。 如果远程计算机上不存在指定的子系统，则该命令将失败。

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

### -UserName

指定用于在远程计算机上创建会话的帐户的用户名。 用户身份验证方法取决于如何在远程计算机上配置 (SSH) 安全外壳。

如果 SSH 配置了基本密码身份验证，则系统将提示你输入用户密码。

如果 SSH 配置为基于密钥的用户身份验证，则可以通过 **KeyFilePath** 参数提供密钥文件路径，并且不会出现密码提示。 请注意，如果客户端用户密钥文件位于 SSH 已知位置，则基于密钥的身份验证不需要 **KeyFilePath** 参数，并且将根据用户名自动进行用户身份验证。 有关详细信息，请参阅 SSH 文档关于基于密钥的用户身份验证。

这不是必需的参数。 如果未指定 **用户名** 参数，则将使用当前登录的用户名作为连接。

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

指示此 cmdlet 使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。 默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 参数是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。

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

指定虚拟机的 ID。

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMName

指定虚拟机的名称。

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.string、System.web. PSSession。

你可以通过管道将计算机名称、字符串或会话对象传递给此 cmdlet。

## 输出

### 无

该 cmdlet 不返回任何输出。

## 注释

若要连接到远程计算机，你必须是该远程计算机上 Administrators 组的成员。 若要在本地计算机上启动交互式会话，你必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

使用时 `Enter-PSSession` ，远程计算机上的用户配置文件用于交互会话。 远程用户配置文件中的命令（包括用于添加 PowerShell 模块和更改命令提示符的命令）将在显示远程提示之前运行。

`Enter-PSSession` 为交互式会话使用本地计算机上的 UI 区域性设置。 若要查找本地 UI 区域性，请使用 `$UICulture` 自动变量。

`Enter-PSSession` 需要 `Get-Command` 、 `Out-Default` 和 `Exit-PSSession` cmdlet。 如果远程计算机上的会话配置中未包含这些 cmdlet，则命令将 `Enter-PSSession` 失败。

不同 `Invoke-Command` 于，它在将命令发送到远程计算机之前对其进行分析和解释， `Enter-PSSession` 将命令直接发送到远程计算机，而不会进行解释。

如果要输入的会话正忙于处理命令，则 PowerShell 对命令的响应可能会有延迟 `Enter-PSSession` 。 会话可用后，就会立即连接。 若要取消 `Enter-PSSession` 命令，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。

**主机名** 参数集包括从 PowerShell 6.0 开始。 添加它是为了提供基于 (SSH) 安全外壳的 PowerShell 远程处理。 SSH 和 PowerShell 在多个平台上都受支持 (Windows、Linux、macOS) ，PowerShell 远程处理将在安装和配置 PowerShell 和 SSH 的这些平台上运行。 这不同于以前仅限 Windows 的基于 WinRM 的远程处理，并且很多 WinRM 特定功能和限制不适用。 例如，目前不支持基于 WinRM 的配额、会话选项、自定义终结点配置和断开/重新连接功能。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

在 PowerShell 7.1 之前，通过 SSH 进行远程处理不支持第二个跃点的远程会话。 此功能仅限于使用 WinRM 的会话。 PowerShell 7.1 允许 `Enter-PSSession` 和 `Enter-PSHostProcess` 在任何交互式远程会话中工作。

## 相关链接

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
