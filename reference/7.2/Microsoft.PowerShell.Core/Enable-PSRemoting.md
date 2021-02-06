---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: a3d9506a0fd2adbb9cc093fb24f99e922dc8a938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595833"
---
# Enable-PSRemoting

## 摘要
将计算机配置为接收远程命令。

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Enable-PSRemoting`Cmdlet 将计算机配置为接收使用 WS-Management 技术发送的 PowerShell 远程命令。 目前仅在 Windows 平台上支持基于 WS-Management 的 PowerShell 远程处理。

默认情况下，在 Windows Server 平台上启用 PowerShell 远程处理。 可以使用 `Enable-PSRemoting` 在其他受支持的 Windows 版本上启用 PowerShell 远程处理，并在禁用远程处理后重新启用它。

只需在将接收命令的每台计算机上运行一次此命令。 不需要在仅发送命令的计算机上运行它。 由于配置启动侦听器来接受远程连接，因此，只需在需要的位置运行侦听器。

如果计算机位于公用网络上时，在客户端版本的 Windows 上启用 PowerShell 远程处理通常是不允许的，但你可以使用 **SkipNetworkProfileCheck** 参数跳过此限制。 有关详细信息，请参阅 **SkipNetworkProfileCheck** 参数的说明。

一台计算机上可以并行存在多个 PowerShell 安装。 运行 `Enable-PSRemoting` 将为运行 cmdlet 的特定安装版本配置远程处理终结点。 因此，如果在 `Enable-PSRemoting` 运行 powershell 6.2 时运行，则将配置运行 powershell 6.2 的远程处理终结点。 如果运行 `Enable-PSRemoting` powershell 7-preview 时运行，则将配置一个运行 powershell 7-preview 的远程处理终结点。

`Enable-PSRemoting` 根据需要创建两个远程处理终结点配置。 如果终结点配置已存在，则只需确保启用。 创建的配置是相同的，但具有不同的名称。 一个将具有与承载会话的 PowerShell 版本对应的简单名称。 其他配置名称包含有关托管会话的 PowerShell 版本的详细信息。 例如， `Enable-PSRemoting` 在 PowerShell 6.2 中运行时，将获取名为 **6.2.2** 的两个已配置的终结点。
这允许你使用简单名称 **powershell. 6** 创建到最新 PowerShell 6 主机版本的连接。 或者，你可以使用更长的名称 **6.2.2** 连接到特定的 PowerShell 主机版本。

若要使用新启用的远程处理终结点，则在使用 `Invoke-Command` 、 `New-PSSession` 、cmdlet 创建远程连接时，必须使用 ConfigurationName 参数按名称指定它们 `Enter-PSSession` 。 有关详细信息，请参阅示例4。

`Enable-PSRemoting`Cmdlet 执行以下操作：

- 运行 [set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet，该 cmdlet 将执行以下任务：
  - 启动 WinRM 服务。
  - 将 WinRM 服务上的启动类型设置为自动。
  - 创建一个可接受任何 IP 地址上的请求的侦听器。
  - 启用 WS-Management 通信的防火墙例外。
  - 如果需要，创建简单名称会话终结点配置。
  - 启用所有会话配置。
  - 将所有会话配置的安全描述符更改为允许远程访问。
- 重新启动 WinRM 服务以使上述更改生效。

若要在 Windows 平台上运行此 cmdlet，请使用 "以管理员身份运行" 选项启动 PowerShell。 此 cmdlet 不能在 Linux 或 MacOS 版本的 PowerShell 上使用。

> [!CAUTION]
> 此 cmdlet 不会影响 Windows PowerShell 创建的远程终结点配置。
> 它仅影响在 PowerShell 版本6和更高版本中创建的终结点。 若要启用和禁用 Windows PowerShell 承载的 PowerShell 远程处理终结点，请 `Enable-PSRemoting` 从 Windows powershell 会话中运行 cmdlet。

## 示例

### 示例1：将计算机配置为接收远程命令

此命令将计算机配置为接收远程命令。

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### 示例2：将计算机配置为在没有确认提示的情况下接收远程命令

此命令将计算机配置为接收远程命令。
**Force** 参数取消用户提示。

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### 示例3：允许在客户端上进行远程访问

此示例演示如何允许在客户端版本的 Windows 操作系统上从公共网络进行远程访问。 不同版本的 Windows 的防火墙规则名称可能不同。
使用 `Get-NetFirewallRule` 可查看规则列表。 启用防火墙规则之前，请查看规则中的安全设置，以验证配置是否适合您的环境。

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

默认情况下， `Enable-PSRemoting` 会创建允许从专用网络和域网络进行远程访问的网络规则。 该命令使用 **SkipNetworkProfileCheck** 参数来允许来自相同本地子网中的公用网络的远程访问。 命令指定 **Force** 参数以禁止显示确认消息。

**SkipNetworkProfileCheck** 参数不影响 Windows 操作系统的服务器版本，默认情况下，它允许从同一本地子网中的公共网络进行远程访问。

`Set-NetFirewallRule` **NetSecurity** 模块中的 cmdlet 添加一个防火墙规则，该规则允许从任何远程位置从公用网络进行远程访问。 这包括不同子网中的位置。

### 示例4：创建到新启用的终结点配置的远程会话

此示例演示如何在计算机上启用 PowerShell 远程处理，查找已配置的终结点名称，并创建到一个终结点的远程会话。

第一个命令在计算机上启用 PowerShell 远程处理。

第二个命令列出终结点配置。

第三个命令将创建与同一计算机的远程 PowerShell 会话，并按名称指定一个 **powershell。** 远程会话将托管 (6.2.2) 的最新 PowerShell 6 版本。

最后一个命令访问 `$PSVersionTable` 远程会话中的变量，以显示托管会话的 PowerShell 版本。

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> 防火墙规则的名称可能不同，具体取决于 Windows 的版本。 使用 `Get-NetFirewallRule` cmdlet 列出系统上规则的名称。

## PARAMETERS

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

### -Force

强制运行命令而不要求用户确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

指示当计算机位于公用网络上时，此 cmdlet 将在客户端版本的 Windows 操作系统上启用远程处理。 此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。

此参数不会影响 Windows 操作系统的服务器版本，默认情况下，它具有公用网络的本地子网防火墙规则。 如果在服务器版本上禁用了本地子网防火墙规则， `Enable-PSRemoting` 则无论此参数的值是什么，都将其重新启用。

若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 **NetSecurity** 模块中使用 cmdlet。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.String

此 cmdlet 将返回描述其结果的字符串。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

在 Windows 操作系统的服务器版本上， `Enable-PSRemoting` 为允许远程访问的专用和域网络创建防火墙规则，并为公用网络创建防火墙规则，该规则仅允许来自同一本地子网中的计算机的远程访问。

在 Windows 操作系统的客户端版本上， `Enable-PSRemoting` 为允许无限制远程访问的私有和域网络创建防火墙规则。 若要为公用网络创建防火墙规则，以允许来自相同本地子网的远程访问，请使用 **SkipNetworkProfileCheck** 参数。

在 Windows 操作系统的客户端或服务器版本上，若要为公用网络创建防火墙规则，以便删除本地子网限制并允许远程访问，请使用 `Set-NetFirewallRule` NetSecurity 模块中的 cmdlet 来运行以下命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

`Enable-PSRemoting` 通过将所有会话配置的 " **已启用** " 属性的值设置为来启用所有会话配置 `$True` 。

`Enable-PSRemoting` 删除 **Deny_All** 和 **Network_Deny_All** 设置。 这可以远程访问保留供本地使用的会话配置。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)
