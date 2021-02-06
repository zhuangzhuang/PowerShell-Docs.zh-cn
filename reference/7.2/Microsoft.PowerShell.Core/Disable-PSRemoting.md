---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 4410c8f41fffcaae9c9f447af246f335033d53a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597045"
---
# Disable-PSRemoting

## 摘要
阻止 PowerShell 终结点接收远程连接。

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

该 `Disable-PSRemoting` cmdlet 会阻止远程访问本地计算机上所有 PowerShell 版本6和更高版本的会话终结点配置。 它不会影响 Windows PowerShell 终结点配置。 若要禁用 Windows PowerShell 会话终结点配置，请 `Disable-PSRemoting` 在 Windows powershell 会话中运行命令。

若要重新启用对所有 PowerShell 版本6和更高版本的会话终结点配置的远程访问，请使用 `Enable-PSRemoting` cmdlet。 若要重新启用对所有 Windows PowerShell 会话终结点配置的远程访问，请 `Enable-PSRemoting` 从 Windows powershell 会话中运行。

> [!NOTE]
> 如果要禁用对本地 Windows 计算机的所有 PowerShell 远程访问，必须在 PowerShell 版本6或更高版本的会话中以及从 Windows PowerShell 会话中运行此命令。 默认情况下，所有 Windows 计算机上都安装了 windows PowerShell。

若要禁用和重新启用对特定会话终结点配置的远程访问，请使用 `Enable-PSSessionConfiguration` 和 `Disable-PSSessionConfiguration` cmdlet。 若要设置单个终结点的特定访问配置，请将 `Set-PSSessionConfiguration` cmdlet 与 **AccessMode** 参数一起使用。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

> [!NOTE]
> 即使在运行后 `Disable-PSRemoting` ，仍可在本地计算机上进行环回连接。 环回连接是源自并连接到同一台本地计算机的 PowerShell 远程会话。 来自外部源的远程会话将保持阻止。 对于环回连接，必须使用 **EnableNetworkAccess** 参数的隐式凭据。 有关环回连接的详细信息，请参阅 [新的 PSSession](New-PSSession.md)。

此 cmdlet 仅在 Windows 平台上可用。 它在 Linux 或 macOS 版本的 PowerShell 中不可用。 若要运行此 cmdlet，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。

## 示例

### 示例1：阻止远程访问所有 PowerShell 会话配置

此示例阻止远程访问计算机上的所有 PowerShell 会话终结点配置。

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 示例2：在没有确认提示的情况下禁止远程访问所有 PowerShell 会话配置

此示例阻止远程访问计算机上的所有 PowerShell 会话终结点配置，而不会提示。

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 示例3：运行此 cmdlet 的效果

此示例演示如何使用 `Disable-PSRemoting` cmdlet。 若要运行此命令序列，请用 "以 **管理员身份运行** " 选项启动 PowerShell。

禁用会话配置后，该 `New-PSSession` cmdlet 会尝试创建到本地计算机的远程会话 (也称为 "环回" ) 。 由于在本地计算机上禁用远程访问，因此该命令将失败。

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### 示例4：运行此 cmdlet 和 Enable-PSRemoting 的效果

此示例演示了使用和 cmdlet 对会话配置的影响 `Disable-PSRemoting` `Enable-PSRemoting` 。

`Disable-PSRemoting` 用于禁止远程访问所有 PowerShell 会话终结点配置。 **Force** 参数取消了所有用户提示。 `Get-PSSessionConfiguration`和 `Format-Table` cmdlet 显示计算机上的会话配置。

此输出显示，具有网络令牌的所有远程用户均被拒绝访问终结点配置。 允许本地计算机上的管理员组访问终结点配置，只要它们本地连接 (也称为环回) 并使用隐式凭据。

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

`Enable-PSRemoting`Cmdlet 可重新启用对计算机上所有 PowerShell 会话终结点配置的远程访问。 **Force** 参数取消所有用户提示，并在不提示的情况下重新启动 WinRM 服务。 新的输出显示已从所有会话配置中删除 **AccessDenied** 安全描述符。

### 示例5：具有已禁用会话终结点配置的环回连接

此示例演示如何禁用终结点配置，并演示如何成功连接到已禁用的终结点。 `Disable-PSRemoting` 禁用所有 PowerShell 会话终结点配置。

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

第一次使用 `New-PSSession` 尝试创建到本地计算机的远程会话。 **ConfigurationName** 参数用于指定已禁用的 PowerShell 终结点。 凭据通过 **Credential** 参数显式传递给命令。 这种类型的连接会通过网络堆栈，并且不是环回。 因此，尝试连接到已禁用的终结点失败，并出现 " **拒绝访问** " 错误。

第二次使用时， `New-PSSession` 也会尝试创建到本地计算机的远程会话。
在这种情况下，它会成功，因为它是绕过网络堆栈的环回连接。

当满足以下条件时，将创建环回连接：

- 要连接到的计算机名称为 "localhost"。
- 未传入凭据。 当前登录的用户 (用于连接的隐式凭据) 。
- 使用 **EnableNetworkAccess** 开关参数。

有关环回连接的详细信息，请参阅 [新的 PSSession](New-PSSession.md) 文档。

### 示例6：禁用所有 PowerShell 远程处理终结点配置

此示例演示如何运行 `Disable-PSRemoting` 命令不会影响 Windows PowerShell 终结点配置。 `Get-PSSessionConfiguration` 在 Windows PowerShell 中运行显示所有终结点配置。 我们发现 Windows PowerShell 终结点配置未禁用。

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

若要禁用这些终结点配置， `Disable-PSRemoting` 必须从 Windows PowerShell 会话中运行该命令。 现在，在 `Get-PSSessionConfiguration` Windows PowerShell 中运行会显示禁用所有终结点配置。

### 示例7：阻止远程访问具有自定义安全描述符的会话配置

此示例演示 `Disable-PSRemoting` cmdlet 禁用对所有会话配置的远程访问，包括具有自定义安全描述符的会话配置。

`Register-PSSessionConfiguration` 创建 **测试** 会话配置。 **FilePath** 参数指定自定义会话的会话配置文件。 **ShowSecurityDescriptorUI** 参数显示为会话配置设置权限的对话框。 在 "权限" 对话框中，为指定的用户创建自定义的完全访问权限。

`Get-PSSessionConfiguration`和 `Format-Table` cmdlet 显示会话配置及其属性。 此输出显示 **测试** 会话配置允许所指示的用户的交互式访问和特殊权限。

`Disable-PSRemoting` 禁用对所有会话配置的远程访问。

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

现在 `Get-PSSessionConfiguration` ，和 `Format-Table` cmdlet 显示将所有网络用户的 **AccessDenied** 安全描述符添加到所有会话配置，包括 **测试** 会话配置。 尽管其他安全描述符不会更改，但 "network_deny_all" 安全描述符优先。 尝试使用 `New-PSSession` 连接到 **测试** 会话配置时，将对此进行说明。

### 示例8：重新启用对选定会话配置的远程访问

此示例演示如何重新启用仅到选定会话配置的远程访问。 禁用所有会话配置后，将重新启用特定会话。

`Set-PSSessionConfiguration`Cmdlet 用于更改 **PowerShell. 6** 会话配置。 如果 **AccessMode** 参数的值为 **remote** ，则启用对配置的远程访问。

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

不能通过管道将任何对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- 禁用会话配置不会撤消由或 cmdlet 进行的所有更改 `Enable-PSRemoting` `Enable-PSSessionConfiguration` 。 你可能需要手动撤消以下更改。

  1. 停止并禁用 WinRM 服务。
  2. 删除接受任何 IP 地址上的请求的侦听器。
  3. 禁用 WS-Management 通信的防火墙例外。
  4. 将 LocalAccountTokenFilterPolicy 的值还原为 0，这将限制对计算机上 Administrators 组成员的远程访问。

- 会话终结点配置是一组定义会话环境的设置。
  连接到计算机的每个会话必须使用在计算机上注册的某个会话终结点配置。 通过拒绝对所有会话终结点配置的远程访问，你可以有效地阻止远程用户建立连接到计算机的会话。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
