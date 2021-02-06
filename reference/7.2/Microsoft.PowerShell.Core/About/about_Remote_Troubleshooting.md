---
description: 介绍如何对 PowerShell 中的远程操作进行故障排除。
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: cedf38f3982f4036aae59a2019ab72b556e50cfd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596405"
---
# <a name="about-remote-troubleshooting"></a>关于远程疑难解答

## <a name="short-description"></a>简短说明
介绍如何对 PowerShell 中的远程操作进行故障排除。

## <a name="long-description"></a>长说明

本部分介绍在使用基于 WS-Management 技术的 PowerShell 的远程处理功能时可能会遇到的一些问题，并建议解决这些问题。

使用 PowerShell 远程处理之前，请参阅 [about_Remote](about_remote.md) 和 [about_Remote_Requirements](about_Remote_Requirements.md) 了解有关配置和基本使用的指南。 此外，每个远程处理 cmdlet 的帮助主题（特别是参数说明）都包含有用的信息，旨在帮助你避免问题。

> [!NOTE]
> 若要查看或更改 WSMan：驱动器中本地计算机的设置（包括对会话配置、受信任的主机、端口或侦听器的更改），请以 "以 **管理员身份运行** " 选项启动 PowerShell。

## <a name="troubleshooting-permission-and-authentication-issues"></a>权限和身份验证问题疑难解答

本部分讨论与用户和计算机权限以及远程处理要求相关的远程处理问题。

### <a name="how-to-run-as-administrator"></a>如何以管理员身份运行

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

若要在本地计算机上启动远程会话，或查看或更改 WSMan：驱动器中本地计算机的设置（包括对会话配置、受信任的主机、端口或侦听器的更改），请使用 "以 **管理员身份运行** " 选项启动 Windows PowerShell。

若要通过 "以 **管理员身份运行** " 选项启动 Windows PowerShell，请执行以下操作：

- 右键单击 Windows PowerShell (或 Windows PowerShell ISE) "图标，然后单击" 以 **管理员身份运行**"。

  在 Windows 7 和 Windows Server 2008 R2 中，用 "以 **管理员身份运行** " 选项启动 windows PowerShell。

- 在 Windows 任务栏中，右键单击 Windows PowerShell 图标，然后单击 "以 **管理员身份运行**"。

  在 Windows Server 2008 R2 中，默认情况下，Windows PowerShell 图标固定到任务栏。

### <a name="how-to-enable-remoting"></a>如何启用远程处理

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

要使计算机能够发送远程命令，无需进行任何配置。
但是，若要接收远程命令，必须在计算机上启用 PowerShell 远程处理。 启用包括：启动 WinRM 服务，将 WinRM 服务的启动类型设置为 "自动"，为 HTTP 和 HTTPS 连接创建侦听器，并创建默认的会话配置。

默认情况下，在 Windows Server 2012 和更新版本的 Windows Server 上启用 windows PowerShell 远程处理。 在所有其他系统上，运行 `Enable-PSRemoting` cmdlet 以启用远程处理。 `Enable-PSRemoting`如果远程处理被禁用，还可以运行 cmdlet，在 Windows server 2012 和更高版本的 windows server 上重新启用远程处理。

若要将计算机配置为接收远程命令，请使用 `Enable-PSRemoting` cmdlet。 以下命令启用所有必需的远程设置，启用会话配置，并重新启动 WinRM 服务以使更改生效。

`Enable-PSRemoting`

若要禁止显示所有用户提示，请键入：

`Enable-PSRemoting -Force`

有关详细信息，请参阅 [enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)。

### <a name="how-to-enable-remoting-in-an-enterprise"></a>如何在企业中启用远程处理

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要使单台计算机能够接收远程 PowerShell 命令并接受连接，请使用 `Enable-PSRemoting` cmdlet。

若要为企业中的多台计算机启用远程处理，可以使用以下扩展选项。

- 若要为远程处理配置侦听器，请启用 " **允许自动配置侦听器** " 组策略。

- 若要在多台计算机上将 Windows 远程管理 (WinRM) 的启动类型设置为 "自动"，请使用 `Set-Service` cmdlet。

- 若要启用防火墙例外，请使用 **Windows 防火墙：允许本地端口例外** 组策略。

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>如何使用组策略启用侦听器

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要为域中的所有计算机配置侦听器，请在以下组策略路径中启用 " **允许自动配置侦听器** 策略"：

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

启用策略并指定 IPv4 和 IPv6 筛选器。 `*`允许使用通配符 () 。

### <a name="how-to-enable-remoting-on-public-networks"></a>如何在公用网络上启用远程处理

```
ERROR:  Unable to check the status of the firewall
```

`Enable-PSRemoting`当本地网络是公共的，并且命令中未使用 **SkipNetworkProfileCheck** 参数时，该 cmdlet 将返回此错误。

在 Windows 的服务器版本上， `Enable-PSRemoting` 在所有网络位置类型上成功。 它创建防火墙规则，以允许远程访问专用和域 ( "Home" 和 "Work" ) 网络。 对于公用网络，它会创建允许来自同一本地子网的远程访问的防火墙规则。

在 Windows 的客户端版本上，会 `Enable-PSRemoting` 在专用网络和域网络上成功。 默认情况下，它在公用网络上失败，但如果使用 **SkipNetworkProfileCheck** 参数，则会 `Enable-PSRemoting` 成功并创建允许来自同一本地子网的流量的防火墙规则。

若要删除公用网络上的本地子网限制并允许从任何位置进行远程访问，请运行以下命令：

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

`Set-NetFirewallRule`Cmdlet 由 NetSecurity 模块导出。

> [!NOTE]
> 在运行 windows server 版本的计算机上，Windows PowerShell 2.0 `Enable-PSRemoting` 创建允许在专用、域和公用网络上进行远程访问的防火墙规则。 在运行 Windows 客户端版本的计算机上， `Enable-PSRemoting` 创建仅允许在专用网络和域网络上进行远程访问的防火墙规则。

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>如何使用组策略启用防火墙例外

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要为域中的所有计算机启用防火墙例外，请在以下组策略路径中启用 " **Windows 防火墙：允许本地端口例外** " 策略：

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

此策略允许计算机上 Administrators 组的成员使用 **控制面板** 中的 " **Windows 防火墙**" 为 Windows 远程管理服务创建防火墙例外。

如果策略配置不正确，可能会收到以下错误：

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

策略中的配置错误导致 **ListeningOn** 属性值为空。 使用以下命令检查值。

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>如何设置 WinRM 服务的启动类型

```
ERROR:  ACCESS IS DENIED
```

PowerShell 远程处理依赖于 (WinRM) 服务的 Windows 远程管理。
必须运行该服务才能支持远程命令。

在服务器版本的 Windows 上，Windows 远程管理 (WinRM) 服务的启动类型为 "自动"。

但是，在客户端版本的 Windows 上，WinRM 服务在默认情况下处于禁用状态。

若要设置远程计算机上的服务的启动类型，请使用 `Set-Service` cmdlet。

若要在多台计算机上运行该命令，可以创建一个文本文件或计算机名称的 CSV 文件。

例如，以下命令从文件中获取计算机名称的列表 `Servers.txt` ，然后将所有计算机上 WinRM 服务的启动类型设置为 " **自动**"。

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

若要查看结果，请将 `Get-WMIObject` cmdlet 与 **Win32_Service** 对象结合使用。 有关详细信息，请参阅 " [设置服务](xref:Microsoft.PowerShell.Management.Set-Service)"。

### <a name="how-to-recreate-the-default-session-configurations"></a>如何重新创建默认会话配置

```
ERROR:  ACCESS IS DENIED
```

若要连接到本地计算机并远程运行命令，本地计算机必须包含用于远程命令的会话配置。

使用时 `Enable-PSRemoting` ，它会在本地计算机上创建默认的会话配置。 远程用户在远程命令不包含 **ConfigurationName** 参数时使用这些会话配置。

如果未注册或删除计算机上的默认配置，请使用 `Enable-PSRemoting` cmdlet 重新创建它们。 可以重复使用此 cmdlet。 如果已配置功能，则不会生成错误。

如果更改了默认会话配置，并且想要还原原始的默认会话配置，请使用 `Unregister-PSSessionConfiguration` cmdlet 删除已更改的会话配置，然后使用 `Enable-PSRemoting` cmdlet 还原它们。
`Enable-PSRemoting` 不会更改现有会话配置。

> [!NOTE]
> 当 `Enable-PSRemoting` 恢复默认会话配置时，它不会为配置创建显式安全描述符。 相反，配置会继承 RootSDDL 的安全描述符，默认情况下，这是安全的。

若要查看 RootSDDL 安全描述符，请键入：

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

若要更改 RootSDDL，请使用 `Set-Item` WSMan：驱动器中的 cmdlet。 若要更改会话配置的安全描述符，请将 `Set-PSSessionConfiguration` cmdlet 与 **SecurityDescriptorSDDL** 或 **ShowSecurityDescriptorUI** 参数一起使用。

有关 WSMan：驱动器的详细信息，请参阅 WSMan 提供程序的帮助主题 ( "Get-help WSMan" ) 。

### <a name="how-to-provide-administrator-credentials"></a>如何提供管理员凭据

```
ERROR:  ACCESS IS DENIED
```

若要在远程计算机上创建 PSSession 或运行命令，则默认情况下，当前用户必须是远程计算机上 Administrators 组的成员。 即使当前用户登录到作为 Administrators 组成员的帐户，也需要使用凭据。

如果当前用户是远程计算机上的 Administrators 组的成员，或者可以提供 Administrators 组的成员的凭据，请使用的 **Credential** 参数 `New-PSSession` 或用于 `Enter-PSSession` `Invoke-Command` 远程连接的 cmdlet。

例如，以下命令提供管理员凭据。

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

有关 **Credential** 参数的详细信息，请参阅 [新的 pssession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 或 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command)。

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>如何为非管理用户启用远程处理

```
ERROR:  ACCESS IS DENIED
```

若要在远程计算机上建立 PSSession 或运行命令，用户必须有权使用远程计算机上的会话配置。

默认情况下，只有计算机上 Administrators 组的成员才有权使用默认的会话配置。 因此，只有 Administrators 组的成员才能远程连接到计算机。

若要允许其他用户连接到本地计算机，请向用户授予对本地计算机上默认会话配置的执行权限。

下面的命令将打开一个属性表，您可以在本地计算机上更改默认的 Microsoft PowerShell 会话配置的安全描述符。

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

有关详细信息，请参阅 [about_Session_Configurations](about_Session_Configurations.md)。

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>如何为其他域中的管理员启用远程处理

```
ERROR:  ACCESS IS DENIED
```

当另一个域中的用户是本地计算机上 Administrators 组的成员时，该用户将无法使用管理员权限远程连接到本地计算机。 默认情况下，来自其他域的远程连接仅使用标准用户特权令牌运行。

但是，你可以使用 **LocalAccountTokenFilterPolicy** 注册表项来更改默认行为，并允许作为 Administrators 组成员的远程用户使用管理员权限运行。

> [!CAUTION]
> **LocalAccountTokenFilterPolicy** 条目禁用用户帐户控制 (UAC) 所有受影响计算机的所有用户的远程限制。 在更改策略之前，请仔细考虑此设置的含义。

若要更改策略，请使用以下命令将 **LocalAccountTokenFilterPolicy** 注册表项的值设置为1。

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>如何在远程命令中使用 ip 地址

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

的 **ComputerName** 参数 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` cmdlet 接受 IP 地址作为有效的值。 但是，由于 Kerberos 身份验证不支持 IP 地址，因此，当你指定 IP 地址时，默认情况下将使用 NTLM 身份验证。

使用 NTLM 身份验证时，需要以下过程进行远程处理。

1. 为 HTTPS 传输配置计算机，或将远程计算机的 IP 地址添加到本地计算机上的 TrustedHosts 列表中。

1. 将 **Credential** 参数用于所有远程命令。

   即使正在提交当前用户的凭据，也是必需的。

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>如何从基于工作组的计算机进行远程连接

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

如果本地计算机不在域中，则需要以下过程进行远程处理。

1. 为 HTTPS 传输配置计算机，或将远程计算机的名称添加到本地计算机上的 TrustedHosts 列表中。

1. 验证在基于工作组的计算机上是否设置了密码。 如果未设置密码或密码值为空，则无法运行远程命令。

   若要设置用户帐户的密码，请使用控制面板中的 "用户帐户"。

1. 将 **Credential** 参数用于所有远程命令。

   即使正在提交当前用户的凭据，也是必需的。

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>如何将计算机添加到受信任的主机列表

TrustedHosts 项可以包含以逗号分隔的计算机名称、IP 地址和完全限定的域名的列表。 允许使用通配符。

若要查看或更改受信任的主机列表，请使用 WSMan：驱动器。 TrustedHost 项在 `WSMan:\localhost\Client` 节点中。

只有计算机上 Administrators 组的成员才有权更改计算机上的受信任主机列表。

警告：为 TrustedHosts 项设置的值会影响计算机的所有用户。

若要查看受信任的主机列表，请使用以下命令：

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

你还可以使用 `Set-Location` cmdlet (alias = cd) 来浏览 WSMan：驱动器到位置。 例如：

```powershell
cd WSMan:\localhost\Client; dir
```

若要将所有计算机添加到受信任的主机列表中，请使用以下命令，该命令将值 * (ComputerName 中的所有) 

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

你还可以使用通配符 (`*`) 将特定域中的所有计算机添加到受信任的主机列表。 例如，以下命令将 Fabrikam 域中的所有计算机添加到受信任的主机列表。

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

若要将特定计算机的名称添加到受信任的主机列表中，请使用以下命令格式：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

其中每个值都 `<ComputerName>` 必须采用以下格式：

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

例如：

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

若要将计算机名称添加到现有的受信任主机列表中，请先将当前值保存在变量中，然后将值设置为包含当前值和新值的逗号分隔列表。

例如，要将 Server01 计算机添加到现有的受信任主机列表，请使用以下命令

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

若要将特定计算机的 IP 地址添加到受信任的主机列表，请使用以下命令格式：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

例如：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

若要将计算机添加到远程计算机的 TrustedHosts 列表，请使用 `Connect-WSMan` cmdlet 将远程计算机的节点添加到本地计算机上的 WSMan：驱动器。 然后，使用 `Set-Item` 命令添加计算机。

有关 cmdlet 的详细信息 `Connect-WSMan` ，请参阅 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)。

## <a name="troubleshooting-computer-configuration-issues"></a>计算机配置问题疑难解答

本部分讨论与计算机、域或企业的特定配置相关的远程处理问题。

### <a name="how-to-configure-remoting-on-alternate-ports"></a>如何在备用端口上配置远程处理

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

默认情况下，PowerShell 远程处理将端口80用于 HTTP 传输。 只要用户未在远程命令中指定 **ConnectionURI** 或 **port** 参数，就会使用默认端口。

若要更改 PowerShell 使用的默认端口，请使用 `Set-Item` WSMan：驱动器中的 cmdlet 来更改侦听器叶节点中的端口值。

例如，以下命令将默认端口更改为8080。

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>如何配置与代理服务器的远程处理

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

由于 PowerShell 远程处理使用 HTTP 协议，因此它受 HTTP 代理设置的影响。 在具有代理服务器的企业中，用户无法直接访问 PowerShell 远程计算机。

若要解决此问题，请使用远程命令中的代理设置选项。 提供了下列设置：

- 对 system.management.automation.remoting.proxyaccesstype
- ProxyAuthentication
- ProxyCredential

若要为特定命令设置这些选项，请使用以下过程：

1. 使用 cmdlet 的 **对 system.management.automation.remoting.proxyaccesstype**、 **ProxyAuthentication** 和 **ProxyCredential** 参数 `New-PSSessionOption` 创建具有企业代理设置的会话选项对象。 Save 选项对象是一个变量。

1. 使用包含选项对象的变量作为 `New-PSSession` 、 `Enter-PSSession` 或命令的 SessionOption 参数的值 `Invoke-Command` 。

例如，以下命令使用代理会话选项创建会话选项对象，然后使用该对象创建远程会话。

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

有关 cmdlet 的详细信息 `New-PSSessionOption` ，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

若要为当前会话中的所有远程命令设置这些选项，请使用 `New-PSSessionOption` 在首选项变量的值中创建的选项对象 `$PSSessionOption` 。 有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

若要在本地计算机上为所有远程命令设置这些选项，请将 `$PSSessionOption` 首选项变量添加到 PowerShell 配置文件中。 有关 PowerShell 配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>如何检测64位计算机上的32位会话

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

如果远程计算机运行的是64位版本的 Windows，并且远程命令使用32位会话配置（如 Microsoft.powershell32），则 Windows 远程管理 (WinRM) 加载 WOW64 进程，Windows 会将对目录的所有引用自动重定向 `$env:Windir\System32` 到 `$env:Windir\SysWOW64` 目录。

因此，如果你尝试使用 System32 目录中的工具，但在 SysWow64 目录中没有相应的工具（如 `Defrag.exe` ），则在目录中找不到这些工具。

若要查找正在会话中使用的处理器体系结构，请使用 **PROCESSOR_ARCHITECTURE** 环境变量的值。 以下命令将查找变量中会话的处理器体系结构 `$s` 。

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

有关会话配置的详细信息，请参阅 [about_Session_Configurations](about_Session_Configurations.md)。

## <a name="troubleshooting-policy-and-preference-issues"></a>策略和首选项问题疑难解答

本部分讨论在本地和远程计算机上设置的策略和首选项相关的远程处理问题。

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>如何更改 Import-PSSession 和 Import-Module 的执行策略

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

`Import-PSSession`和 `Export-PSSession` cmdlet 将创建包含未签名的脚本文件和格式化文件的模块。

若要导入通过使用或创建的模块， `Import-PSSession` `Import-Module` 当前会话中的执行策略不能是受限的，也不能 AllSigned。 有关 PowerShell 执行策略的信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

若要在不更改注册表中设置的本地计算机的执行策略的情况下导入模块，请使用的 **作用域** 参数 `Set-ExecutionPolicy` 为单个进程设置限制性较低的执行策略。

例如，以下命令使用 `RemoteSigned` 执行策略启动进程。 执行策略更改只会影响当前进程，并且不会更改 PowerShell **set-executionpolicy** 注册表设置。

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

你还可以使用的 **set-executionpolicy** 参数 `PowerShell.exe` 来启动具有限制性较低的执行策略的单个会话。

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

有关执行策略的详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。 要了解详情，请键入 `PowerShell.exe -?`。

### <a name="how-to-set-and-change-quotas"></a>如何设置和更改配额

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

您可以使用配额来保护本地计算机和远程计算机的资源使用过度，这两者都是意外的和恶意的。

基本配置中提供以下配额。

- WSMan 提供程序 (WSMan： ) 提供多个配额设置，如节点中的 **MaxEnvelopeSizeKB** 和 **MaxProviderRequests** 设置 `WSMan:<ComputerName>` 以及节点中的 **MaxConcurrentOperations**、 **MaxConcurrentOperationsPerUser** 和 **MaxConnections** 设置 `WSMan:<ComputerName>\Service` 。

- 可以通过使用 cmdlet 的 **MaximumReceivedDataSizePerCommand** 和 **MaximumReceivedObjectSize** 参数 `New-PSSessionOption` 和 `$PSSessionOption` 首选项变量来保护本地计算机。

- 可以通过添加对会话配置的限制来保护远程计算机，例如通过使用 cmdlet 的 **MaximumReceivedDataSizePerCommandMB** 和 **MaximumReceivedObjectSizeMB** 参数 `Register-PSSessionConfiguration` 。

当配额与命令冲突时，PowerShell 会生成错误。

若要解决此错误，请更改远程命令以符合配额要求。 或者，确定配额的来源，然后增加配额以允许命令完成。

例如，以下命令将远程计算机上的 Microsoft PowerShell 会话配置中的对象大小配额增加 10 MB (默认值) 为 11 MB。

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

有关 cmdlet 的详细信息 `New-PSSessionOption` ，请参阅 `New-PSSessionOption` 。

有关 WS-Management 配额的详细信息，请参阅 [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)。

### <a name="how-to-resolve-timeout-errors"></a>如何解决超时错误

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

您可以使用超时来保护本地计算机和远程计算机的资源使用过度，这两者都是意外的和恶意的。 如果在本地计算机和远程计算机上设置了超时，则 PowerShell 将使用最短超时设置。

基本配置中提供以下超时。

- WSMan 提供程序 (WSMan： ) 提供多个客户端和服务端超时设置，如节点中的 **MaxTimeoutms** 设置 `WSMan:<ComputerName>` 以及节点中的 **EnumerationTimeoutms** 和 **MaxPacketRetrievalTimeSeconds** 设置 `WSMan:<ComputerName>\Service` 。

- 可以通过使用 cmdlet 的 **CancelTimeout**、 **IdleTimeout**、 **OpenTimeout** 和 **OperationTimeout** 参数 `New-PSSessionOption` 以及首选项变量来保护本地计算机 `$PSSessionOption` 。

- 还可以通过在会话的会话配置中以编程方式设置超时值来保护远程计算机。

当超时值不允许操作完成时，PowerShell 将终止操作并生成错误。

若要解决此错误，请将命令更改为在超时间隔内完成，或确定超时限制的源，并增加超时间隔以允许命令完成。

例如，以下命令使用 `New-PSSessionOption` cmdlet 来创建 **OperationTimeout** 值为4分钟)  (的会话选项对象，并使用 session 选项对象来创建远程会话。

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

有关 WS-Management 超时的详细信息，请参阅 WSMan 提供程序的帮助主题 (类型 `Get-Help WSMan`) 。

有关 cmdlet 的详细信息 `New-PSSessionOption` ，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

## <a name="troubleshooting-unresponsive-behavior"></a>无响应行为疑难解答

本部分讨论的远程处理问题会阻止命令完成，并防止或延迟 PowerShell 提示符的返回。

### <a name="how-to-interrupt-a-command"></a>如何中断命令

某些本机 Windows 程序（例如具有用户界面的程序、提示输入的控制台应用程序以及使用 Win32 控制台 API 的控制台应用程序）在 PowerShell 远程主机中无法正常运行。

使用这些程序时，可能会出现意外的行为，例如无输出、部分输出或未完成的远程命令。

若要结束无响应的程序，请键入<kbd>CTRL</kbd> + <kbd>C</kbd>。 若要查看可能已报告的任何错误，请键入 `$error` 本地主机和远程会话。

## <a name="how-to-recover-from-an-operation-failure"></a>如何从操作失败中恢复

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

如果操作在完成之前终止，则会返回此错误。
通常，当 WinRM 服务在其他 WinRM 操作正在进行时停止或重新启动时，会发生这种情况。

若要解决此问题，请确认 WinRM 服务正在运行，然后重试该命令。

1. 通过 "以 **管理员身份运行** " 选项启动 PowerShell。
1. 运行以下命令：

   `Start-Service WinRM`

1. 重新运行生成错误的命令。

## <a name="linux-and-macos-limitations"></a>Linux 和 macOS 限制

### <a name="authentication"></a>身份验证

在 macOS 上只使用基本身份验证，尝试使用其他身份验证方案可能会导致进程崩溃。

请参阅 [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) 说明。

## <a name="see-also"></a>另请参阅

[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
