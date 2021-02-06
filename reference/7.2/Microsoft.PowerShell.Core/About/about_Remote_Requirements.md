---
description: 描述在 PowerShell 中运行远程命令的系统要求和配置要求。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 4a994ded51195e5932af7bb4af0b2e6fb3a67857
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597847"
---
# <a name="about-remote-requirements"></a>关于远程要求

## <a name="short-description"></a>简短说明
描述在 PowerShell 中运行远程命令的系统要求和配置要求。

## <a name="long-description"></a>详细说明

本主题介绍在 PowerShell 中建立远程连接和运行远程命令的系统要求、用户要求和资源要求。 它还提供了有关配置远程操作的说明。

注意：许多 cmdlet (包括 Get-help、Get-wmiobject 和 Get-WinEvent cmdlet，) 从远程计算机获取对象，方法是使用 Microsoft .NET Framework 方法检索这些对象。 它们不使用 PowerShell 远程处理基础结构。 本文档中的要求不适用于这些 cmdlet。

若要查找具有 ComputerName 参数但不使用 PowerShell 远程处理的 cmdlet，请阅读 cmdlet 的 ComputerName 参数说明。

## <a name="system-requirements"></a>系统要求

若要在 Windows PowerShell 3.0 上运行远程会话，本地计算机和远程计算机必须具有以下各项：

- Windows PowerShell 3.0 或更高版本
- Microsoft .NET Framework 4 或更高版本
- Windows 远程管理3。0

若要在 Windows PowerShell 2.0 上运行远程会话，本地计算机和远程计算机必须具有以下各项：

- Windows PowerShell 2.0 或更高版本
- Microsoft .NET Framework 2.0 或更高版本
- Windows 远程管理2。0

可以在运行 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的计算机之间创建远程会话。 但是，仅在 Windows PowerShell 3.0 上运行的功能（如断开连接和重新连接到会话的能力）仅在两台计算机都运行 Windows PowerShell 3.0 时才可用。

若要查找已安装的 PowerShell 版本的版本号，请使用 $PSVersionTable 自动变量。

Windows 8、Windows Server 2012 和更新版本的 Windows 操作系统中都包含了 Windows 远程管理 (WinRM) 3.0 和 Microsoft .NET Framework 4。 对于较早版本的操作系统，Windows Management Framework 3.0 中包含 WinRM 3.0。 如果计算机不具有所需的 WinRM 版本或 Microsoft .NET 框架，则安装将失败。

## <a name="user-permissions"></a>用户权限

若要创建远程会话并运行远程命令，则默认情况下，当前用户必须是远程计算机上 Administrators 组的成员，或者提供管理员凭据。 否则，该命令将失败。

在远程计算机上创建会话和运行命令所需的权限 (或本地计算机上的远程会话中) 由会话配置建立， (在该会话连接到的远程计算机上也称为 "终结点" ) 。 具体而言，会话配置上的安全描述符确定谁有权访问会话配置，哪些用户可以使用它来进行连接。

默认会话配置、Microsoft.powershell32 和 Microsoft PowerShell 上的安全描述符允许仅访问 Administrators 组的成员的访问权限。

如果当前用户没有使用会话配置的权限，则运行命令 (使用临时会话) 或在远程计算机上创建持久会话的命令将失败。 用户可以使用 cmdlet 的 ConfigurationName 参数来创建会话，以选择不同的会话配置（如果有）。

计算机上 Administrators 组的成员可以通过更改默认会话配置上的安全描述符，并通过使用不同的安全描述符创建新的会话配置来确定有权远程连接到计算机的人员。

有关会话配置的详细信息，请参阅 [about_Session_Configurations](about_Session_Configurations.md)。

## <a name="windows-network-locations"></a>WINDOWS 网络位置

从 Windows PowerShell 3.0 开始，Enable-PSRemoting cmdlet 可在专用、域和公用网络上的 Windows 客户端和服务器版本上启用远程处理。

在具有专用网络和域网络的 Windows server 版本中，Enable-PSRemoting cmdlet 将创建允许无限制远程访问的防火墙规则。 它还为公用网络创建防火墙规则，该规则仅允许来自同一本地子网中的计算机进行远程访问。 默认情况下，在公用网络上的 Windows 服务器版本上会启用此本地子网防火墙规则，但 Enable-PSRemoting 会在更改或删除规则的情况下重新应用该规则。

对于具有专用网络和域网络的 Windows 的客户端版本，默认情况下，Enable-PSRemoting cmdlet 将创建允许无限制远程访问的防火墙规则。

若要在具有公用网络的 Windows 的客户端版本上启用远程处理，请使用 Enable-PSRemoting cmdlet 的 SkipNetworkProfileCheck 参数。 它创建一个防火墙规则，该规则仅允许来自同一本地子网中的计算机进行远程访问。

若要删除公用网络上的本地子网限制并允许从 Windows 客户端和服务器版本上的所有位置进行远程访问，请在 NetSecurity 模块中使用 Set-NetFirewallRule cmdlet。 运行以下命令：

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

在 Windows PowerShell 2.0 中，在 Windows 的服务器版本上 Enable-PSRemoting 创建允许在所有网络上进行远程访问的防火墙规则。

在 Windows PowerShell 2.0 中，在 Windows 的客户端版本上，Enable-PSRemoting 仅在专用网络和域网络上创建防火墙规则。 如果网络位置是公共的，Enable-PSRemoting 会失败。

## <a name="run-as-administrator"></a>以管理员身份运行

以下远程处理操作需要管理员权限：

- 建立与本地计算机的远程连接。 这通常称为 "环回" 方案。

- 管理本地计算机上的会话配置。

- 查看和更改本地计算机上的 WS-Management 设置。 这些是 WSMAN：驱动器的 LocalHost 节点中的设置。

若要执行这些任务，必须使用 "以管理员身份运行" 选项启动 PowerShell，即使您是本地计算机上 Administrators 组的成员也是如此。

在 Windows 7 和 Windows Server 2008 R2 中，通过 "以管理员身份运行" 选项启动 Windows PowerShell：

1. 依次单击 "开始"、"所有程序"、"附件"，然后单击 "Windows PowerShell" 文件夹。
2. 右键单击 "Windows PowerShell"，然后单击 "以管理员身份运行"。

若要通过 "以管理员身份运行" 选项启动 Windows PowerShell：

1. 依次单击 "开始"、"所有程序"，然后单击 "Windows PowerShell" 文件夹。
2. 右键单击 "Windows PowerShell"，然后单击 "以管理员身份运行"。

Windows PowerShell 的其他 Windows 资源管理器项（包括快捷方式）中也提供了 "以管理员身份运行" 选项。 只需右键单击该项目，然后单击 "以管理员身份运行" 即可。

从其他程序（如 Cmd.exe）启动 Windows PowerShell 时，请使用 "以管理员身份运行" 选项启动程序。

## <a name="how-to-configure-your-computer-for-remoting"></a>如何将计算机配置为进行远程处理

运行所有受支持的 Windows 版本的计算机无需任何配置即可在 PowerShell 中建立远程连接和运行远程命令。 但是，若要接收连接以及允许用户创建本地和远程用户管理的 PowerShell 会话 ( "Pssession" ) 并在本地计算机上运行命令，则必须在计算机上启用 PowerShell 远程处理。

默认情况下，为 PowerShell 远程处理启用 windows server 2012 和更新版本的 Windows Server。 如果更改了设置，则可以通过运行 Enable-PSRemoting cmdlet 来还原默认设置。

在所有其他受支持的 Windows 版本上，需要运行 Enable-PSRemoting cmdlet 来启用 PowerShell 远程处理。

WinRM 服务支持 PowerShell 的远程处理功能，这是用于管理的 Web 服务 (WS-MANAGEMENT) 协议的 Microsoft 实现。 启用 PowerShell 远程处理时，将更改 WS-Management 的默认配置，并添加允许用户连接到 WS-MANAGEMENT 的系统配置。

将 PowerShell 配置为接收远程命令：

1. 以 "以管理员身份运行" 选项启动 PowerShell。
2. 在命令提示符处，键入：`Enable-PSRemoting`

若要验证远程处理是否已正确配置，请运行以下命令（如）在本地计算机上创建远程会话的测试命令。

```powershell
New-PSSession
```

如果远程处理配置正确，则该命令将在本地计算机上创建一个会话，并返回表示该会话的对象。 输出应类似于以下示例输出：

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

如果命令失败，请参阅 [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)。

## <a name="understand-policies"></a>了解策略

远程工作时，可以使用 PowerShell 的两个实例，一个实例在本地计算机上，另一个位于远程计算机上。 因此，你的工作会受到本地和远程计算机上的 Windows 策略和 PowerShell 策略的影响。

通常，在连接之前以及建立连接时，本地计算机上的策略是有效的。 使用连接时，远程计算机上的策略生效。

## <a name="basic-authentication-limitations-on-linux-and-macos"></a>Linux 和 macOS 上的基本身份验证限制

从 Linux 或 macOS 系统连接到 Windows 时，不支持通过 HTTP 进行基本身份验证。 通过在目标服务器上安装证书，可以通过 HTTPS 使用基本身份验证。 证书必须具有与主机名匹配的 CN 名称，未过期或已被吊销。 自签名证书可用于测试目的。

有关更多详细信息，请参阅 [如何：配置 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) 。

以下命令在已提升权限的命令提示符下运行，将使用已安装的证书配置 Windows 上的 HTTPS 侦听器。

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

在 Linux 或 macOS 端，选择 "基本" 作为 "身份验证" 和-"UseSSl"。

> 注意：基本身份验证不能与域帐户一起使用;需要一个本地帐户，并且该帐户必须在 Administrators 组中。

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

通过 HTTPS 进行的基本身份验证的替代方法是协商。 这会导致客户端和服务器之间的 NTLM 身份验证，并且有效负载是通过 HTTP 加密的。

下面的示例演示如何将 Negotiate 与新的-PSSession 结合使用：

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> Windows Server 需要额外的注册表设置，以允许管理员（而非内置管理员）使用 NTLM 进行连接。
> 请参阅在[远程连接的身份验证](/windows/win32/winrm/authentication-for-remote-connections)中协商身份验证中的 LocalAccountTokenFilterPolicy 注册表设置

## <a name="see-also"></a>另请参阅

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

