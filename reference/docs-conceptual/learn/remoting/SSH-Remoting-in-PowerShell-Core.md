---
title: 通过 SSH 进行 PowerShell 远程处理
ms.date: 10/19/2020
description: 介绍如何为 PowerShell 远程处理设置 SSH 协议。
ms.openlocfilehash: c3373ac30fd915d42e8c9fb7f1eae348a2aee7f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501331"
---
# <a name="powershell-remoting-over-ssh"></a>通过 SSH 进行 PowerShell 远程处理

## <a name="overview"></a>概述

PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。 SSH 现在可用于 Linux 和 Windows 平台，并允许进行真正的多平台 PowerShell 远程处理。

WinRM 为 PowerShell 远程会话提供可靠的托管模型。 基于 SSH 的远程处理目前不支持远程终结点配置和 Just Enough Administration (JEA)。

通过 SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。 SSH 远程处理在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。 最终，我们将实现常规托管模型（类似于 WinRM）以支持终结点配置和 JEA。

`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` cmdlet 现具有新的参数集，以支持这个新的远程处理连接。

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

若要创建远程会话，请使用 HostName 参数指定目标计算机，并通过 UserName 提供用户名 。 当以交互方式运行 cmdlet 时，系统会提示输入密码。 还可以通过包含 KeyFilePath 参数的私钥文件来使用 SSH 密钥身份验证。 为 SSH 身份验证创建密钥的操作因平台而异。

## <a name="general-setup-information"></a>常规安装信息

必须在所有计算机上安装 PowerShell 6 或更高版本，以及 SSH。 安装 SSH 客户端 (`ssh.exe`) 和服务器 (`sshd.exe`)，以便对计算机进行远程处理或从计算机进行远程处理。 OpenSSH for Windows 现已在 Windows 10 内部版本 1809 和 Windows Server 2019 中可用。 有关详细信息，请参阅[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)。 对于 Linux，请安装适用于平台的 SSH（包括 sshd 服务器）。 此外，还需要从 GitHub 安装 PowerShell 以获取 SSH 远程处理功能。 必须配置 SSH 服务器以创建 SSH 子系统来托管远程计算机上的 PowerShell 进程。 还必须启用 **密码** 或 **基于密钥的** 身份验证。

## <a name="set-up-on-a-windows-computer"></a>在 Windows 计算机上设置

1. 安装最新版本的 PowerShell。 有关详细信息，请参阅[在 Windows 上安装 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)。

   可通过列出 `New-PSSession` 参数集来确认 PowerShell 具有 SSH 远程处理支持。 你会注意到存在以 **SSH** 开头的参数集名称。 这些参数集包括 **SSH** 参数。

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. 安装最新 Win32 OpenSSH。 有关安装说明，请参阅 [OpenSSH 入门](/windows-server/administration/openssh/openssh_install_firstuse)。

   > [!NOTE]
   > 如果要将 PowerShell 设置为 OpenSSH 的默认 shell，请参阅[为 OpenSSH 配置 Windows](/windows-server/administration/openssh/openssh_server_configuration)。

1. 编辑位于 `$env:ProgramData\ssh` 的 `sshd_config` 文件。

   确保已启用密码身份验证：

   ```
   PasswordAuthentication yes
   ```

   创建托管远程计算机上的 PowerShell 进程的 SSH 子系统：

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo
   ```

   > [!NOTE]
   > PowerShell 可执行文件的默认位置是 `c:/progra~1/powershell/7/pwsh.exe`。 该位置可能因 PowerShell 安装方式而有所不同。
   >
   > 对于包含空格的任何文件路径，必须使用 8.3 短名称。 OpenSSH for Windows 中存在一个 bug，使空格在子系统可执行路径中无效。 有关详细信息，请参阅此 [GitHub 问题](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。
   >
   > Windows 中的 `Program Files` 文件夹的 8.3 短名称通常为 `Progra~1`。 但是，可以使用以下命令来确保：
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   启用密钥身份验证（可选）：

   ```
   PubkeyAuthentication yes
   ```

   有关详细信息，请参阅[管理 OpenSSH 密钥](/windows-server/administration/openssh/openssh_keymanagement)。

1. 重启 **sshd** 服务。

   ```powershell
   Restart-Service sshd
   ```

1. 将 OpenSSH 的安装路径添加到 Path 环境变量。 例如，`C:\Program Files\OpenSSH\` 。 通过此条目可找到 `ssh.exe`。

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>在 Ubuntu 16.04 Linux 计算机上设置

1. 安装最新版本的 PowerShell，请参阅[在 Linux 上安装 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)。
1. 安装 [Ubuntu OpenSSH 服务器](https://help.ubuntu.com/lts/serverguide/openssh-server.html)。

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. 编辑 `/etc/ssh` 位置中的 `sshd_config` 文件。

   确保已启用密码身份验证：

   ```
   PasswordAuthentication yes
   ```

   启用密钥身份验证（可选）：

   ```
   PubkeyAuthentication yes
   ```

   有关在 Ubuntu 上创建 SSH 密钥的详细信息，请参阅 [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html) 的手册页。

   添加 PowerShell 子系统条目：

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > PowerShell 可执行文件的默认位置是 `/usr/bin/pwsh`。 该位置可能因 PowerShell 安装方式而有所不同。

   启用密钥身份验证（可选）：

   ```
   PubkeyAuthentication yes
   ```

1. 重启 ssh 服务。

   ```bash
   sudo service ssh restart
   ```

## <a name="set-up-on-a-macos-computer"></a>在 macOS 计算机上设置

1. 安装最新版本的 PowerShell。 有关详细信息，请参阅[在 macOS 上安装 PowerShell Core](../../install/installing-powershell-core-on-macos.md)。

   按照以下步骤确保已启用 SSH 远程处理：

   1. 打开 `System Preferences`。
   1. 单击 `Sharing`。
   1. 选中 `Remote Login` 以设置 `Remote Login: On`。
   1. 允许相应用户访问。

1. 编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件。

   打开文本编辑器，例如 **nano**：

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   确保已启用密码身份验证：

   ```
   PasswordAuthentication yes
   ```

   添加 PowerShell 子系统条目：

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > PowerShell 可执行文件的默认位置是 `/usr/local/bin/pwsh`。 该位置可能因 PowerShell 安装方式而有所不同。

   启用密钥身份验证（可选）：

   ```
   PubkeyAuthentication yes
   ```

1. 重启 **sshd** 服务。

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>身份验证

通过 SSH 进行 PowerShell 远程处理依赖于 SSH 客户端和 SSH 服务之间的身份验证交换，并且本身不实现任何身份验证方案。 这使得任何配置的身份验证方案（包括多重身份验证）都由 SSH 处理，并且独立于 PowerShell。 例如，可以将 SSH 服务配置为需要公钥身份验证以及一次性密码，从而增加安全性。 多重身份验证的配置不在本文档的讨论范围。 若要了解如何正确配置多重身份验证，请参阅相关的 SSH 文档，并在尝试将其用于 PowerShell 远程处理之前先在 PowerShell 之外验证它的运行效果。

> [!NOTE]
> 用户在远程会话中具有相同的权限。 这意味着，管理员有权访问提升的 shell，而普通用户将无法访问。

## <a name="powershell-remoting-example"></a>PowerShell 远程处理示例

测试远程处理最简单的方法是在单个计算机上进行测试。 在本示例中，我们创建返回到同一 Linux 计算机上的远程会话。 我们交互式使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机并要求提供密码。 可以在 Windows 计算机上执行相同的操作以确保远程处理正常工作。 然后，通过更改主机名在计算机之间进行远程处理。

```powershell
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="limitations"></a>限制

- **sudo** 命令对 Linux 计算机上的远程会话不起作用。

- 通过 SSH 进行 PowerShell 远程处理不支持配置文件，并且无法访问 `$PROFILE`。 进入会话后，可以通过完整文件路径并使用点来获取配置文件来源，以加载该配置文件。 这与 SSH 配置文件无关。 可以将 SSH 服务器配置为使用 PowerShell 作为默认 shell，并通过 SSH 加载配置文件。 有关详细信息，请参阅 SSH 文档。

- 在 PowerShell 7.1 之前，通过 SSH 进行远程处理不支持第二个跃点的远程会话。 此功能仅限于使用 WinRM 的会话。 PowerShell 7.1 允许 `Enter-PSSession` 和 `Enter-PSHostProcess` 在任何交互式远程会话中工作。

## <a name="see-also"></a>另请参阅

[在 Linux 上安装 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[在 macOS 上安装 PowerShell Core](../../install/installing-powershell-core-on-macos.md)

[在 Windows 上安装 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)

[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)

[管理 OpenSSH 密钥](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
