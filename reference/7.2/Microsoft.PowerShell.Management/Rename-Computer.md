---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 070a428530f4f3eecceb0ae3f520ad565097c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598475"
---
# Rename-Computer

## 摘要
重命名计算机。

## SYNTAX

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

该 `Rename-Computer` cmdlet 将重命名本地计算机或远程计算机。
在一个命令中可重命名一台计算机。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例1：重命名本地计算机

此命令将本地计算机重命名为 `Server044` ，然后重新启动它以使更改生效。

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### 示例2：重命名远程计算机

此命令将计算机重命名 `Srv01` 为 `Server001` 。 计算机不会重新启动。

**DomainCredential** 参数指定有权对域中的计算机进行重命名的用户的凭据。

**Force** 参数取消显示确认提示。

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETERS

### -ComputerName

重命名指定的远程计算机。
默认为本地计算机。

键入远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。
若要指定本地计算机，请键入计算机名、点 (`.`) 或 `localhost` 。

此参数不依赖于 PowerShell 远程处理。
 `Rename-Computer` 即使你的计算机未配置为运行远程命令，你也可以使用 ComputerName 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

指定有权连接到域的用户帐户。
需要显式凭据才可重命名加入到域的计算机。

键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。

键入用户名时，此 cmdlet 会提示输入密码。

若要指定有权连接到由 **ComputerName** 参数指定的计算机的用户帐户，请使用 **LocalCredential** 参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### -LocalCredential

指定有权连接到由 **ComputerName** 参数指定的计算机的用户帐户。 默认为当前用户。

键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。

键入用户名时，此 cmdlet 会提示输入密码。

若要指定有权连接到域的用户帐户，请使用 **DomainCredential** 参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

为计算机指定一个新名称。
此参数是必需的。

标准名称可能包含 (`a-z`) 、 (`A-Z`) 、数字 (`0-9`)  (和连字符) 的字母，但不 () `-` 空格或句点 `.` 。 名称不能完全由数字组成，且长度不得超过63个字符

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

返回命令的结果。
否则，此 cmdlet 将不生成任何输出。

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

### -Restart

指示此 cmdlet 重启已重命名的计算机。
若要更改生效，通常需要重新启动。

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

### -WsmanAuthentication

指定此 cmdlet 使用 WSMan 协议时用于对用户的凭据进行身份验证的机制。 此参数的可接受值为：

- **基本**
- CredSSP
- **默认**
- 摘要式
- **Kerberos**
- **Negotiate**

默认值为 **Default**。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!WARNING]
> 凭据安全服务提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。
> 此机制增加了远程操作的安全风险。
> 如果远程计算机被泄露，则传递到该计算机的凭据可用于控制网络会话 >。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### 无

此 cmdlet 不具有按值获取输入的参数。 但是，你可以通过管道将对象的 **ComputerName** 和 **NewName** 属性的值传递给此 cmdlet。

## 输出

### Microsoft.PowerShell.Commands.ComputerChangeInfo

如果指定 **PassThru** 参数，则此 cmdlet 将返回 **ComputerChangeInfo** 对象。
否则，将不返回任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
