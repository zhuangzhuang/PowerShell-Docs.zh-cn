---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597846"
---
# Stop-Computer

## 摘要
停止（关闭）本地和远程计算机。

## SYNTAX

### 全部

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 将关闭 `Stop-Computer` 本地计算机和远程计算机。

你可以使用的参数 `Stop-Computer` 来指定身份验证级别和备用凭据，并强制立即关闭。

在 PowerShell 7.1 中， `Stop-Computer` 为 Linux 和 macOS 添加了。 参数在这些平台上不起作用。 该 cmdlet 只调用本机命令 `/sbin/shutdown` 。

## 示例

### 示例 1：关闭本地计算机

此示例关闭本地计算机。

```powershell
Stop-Computer -ComputerName localhost
```

### 示例 2：关闭两台远程计算机和本地计算机

此示例将停止两台远程计算机和本地计算机。

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer` 使用 **ComputerName** 参数指定两台远程计算机和本地计算机。 每台计算机都已关闭。

### 示例 3：关闭远程计算机，作为后台作业运行

在此示例中，在 `Stop-Computer` 两台远程计算机上作为后台作业运行。

后台运算符将 `&` `Stop-Computer` 命令作为后台作业运行。 有关详细信息，请参阅 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)。

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

`Stop-Computer` 使用 **ComputerName** 参数指定两台远程计算机。 `&`后台运算符将命令作为后台作业运行。 作业对象存储在 `$j` 变量中。

变量中的作业对象 `$j` 会向下发送到 `Receive-Job` ，后者将获取作业结果。 这些对象存储在变量中 `$results` 。 此 `$results` 变量在 PowerShell 控制台中显示作业信息。

### 示例 4：关闭远程计算机

此示例使用指定的身份验证关闭远程计算机。

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

`Stop-Computer` 使用 **ComputerName** 参数来指定远程计算机。 **WsmanAuthentication** 参数指定使用 Kerberos 建立远程连接。

### 示例5：关闭域中的计算机

在此示例中，这些命令强制立即关闭指定域中的所有计算机。

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

`Get-Content` 使用 **Path** 参数获取当前目录中包含域计算机列表的文件。 这些对象存储在变量中 `$s` 。

`Get-Credential` 使用 **Credential** 参数指定域管理员的凭据。 凭据存储在 `$c` 变量中。

`Stop-Computer` 关闭在变量中用 **ComputerName** 参数的计算机列表指定的计算机 `$s` 。 **Force** 参数强制立即关闭。 **Credential** 参数提交保存在变量中的凭据 `$c` 。

## PARAMETERS

### -ComputerName

指定要停止的计算机。 默认为本地计算机。

在一个逗号分隔列表中键入一台或多台计算机的 NETBIOS 名称、IP 地址或完全限定的域名。 若要指定本地计算机，请键入计算机名称或“localhost”。

此参数不依赖于 PowerShell 远程处理。 即使你的计算机未配置为运行远程命令，你也可以使用 **ComputerName** 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -Credential

指定有权执行此操作的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

强制立即关闭计算机。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

指定此 cmdlet 使用 WSMan 协议时用于对用户的凭据进行身份验证的机制。 默认值为 **Default**。

此参数的可接受值为：

- 基本
- CredSSP
- 默认
- 摘要
- Kerberos
- Negotiate。

有关此参数的值的详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 凭据安全服务提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
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

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### 无

## 注释

此 cmdlet 使用 **Win32_OperatingSystem** WMI 类的 **Win32Shutdown** 方法。 此方法需要为用于重新启动计算机的用户帐户启用 **SeShutdownPrivilege** 特权。

在 PowerShell 7.1 中， `Stop-Computer` 为 Linux 和 macOS 添加了。 对于这些平台，cmdlet 将调用本机命令 `/sbin/shutdown` 。

## 相关链接

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Test-Connection](Test-Connection.md)

