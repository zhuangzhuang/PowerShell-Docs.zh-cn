---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3260c88d57e98c0072af8621600a02901c561acb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596849"
---
# Disable-WSManCredSSP

## 摘要
在计算机上禁用 CredSSP 身份验证。

## SYNTAX

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## DESCRIPTION
**Disable-WSManCredSSP** cmdlet 在客户端或服务器计算机上禁用凭据安全支持提供程序 (CredSSP) 身份验证。
当使用 CredSSP 身份验证时，用户凭据将传递给要进行身份验证的远程计算机。

此 cmdlet 通过在 Role 参数中指定 Client 来禁用客户端上的 CredSSP。
该 cmdlet 将执行以下操作：

- 禁用客户端上的 CredSSP。 此 cmdlet 将 WS-Management 设置 **\<localhost|computername\> \Client\Auth\CredSSP** 设置为 false。
- 从客户端上的 Windows CredSSP 策略 **AllowFreshCredentials** 中删除任何 WSMan/* 设置。

通过在 Role 中指定 Server 使用该 cmdlet 禁用服务器上的 CredSSP。
该 cmdlet 将执行以下操作：

- 禁用服务器上的 CredSSP。 此 cmdlet 将 WS-Management 设置 **\<localhost|computername\> \Service\Auth\CredSSP** 设置为 false。

注意：CredSSP 身份验证将用户凭据从本地计算机委派给远程计算机。
此做法增加了远程操作的安全风险。
如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。

## 示例

### 示例 1：禁用客户端上的 CredSSP

```
PS C:\> Disable-WSManCredSSP -Role Client
```

此命令禁用客户端上的 CredSSP，这会阻止到服务器的委派。

### 示例 2：禁用服务器上的 CredSSP

```
PS C:\> Disable-WSManCredSSP -Role Server
```

此命令禁用服务器上的 CredSSP，这会阻止从客户端委派。

## PARAMETERS

### -Role
指定以客户端还是服务器的形式禁用 CredSSP。
此参数的可接受的值是：Client 和 Server。

如果指定 Client，该 cmdlet 将执行以下操作：

- 禁用客户端上的 CredSSP。 此 cmdlet 将 WS-Management 设置 **\<localhost|computername\> \Client\Auth\CredSSP** 设置为 false。
- 从客户端上的 Windows CredSSP 策略 **AllowFreshCredentials** 中删除任何 WSMan/* 设置。

如果指定 Server，则该 cmdlet 将执行以下操作：

- 禁用服务器上的 CredSSP。 此 cmdlet 将 WS-Management 设置 **\<localhost|computername\> \Service\Auth\CredSSP** 设置为 false。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无
此 cmdlet 不接受任何输入。

## 输出

### 无
此 cmdlet 将不生成任何输出。

## 注释

* 若要启用 CredSSP 身份验证，请使用 Enable-WSManCredSSP cmdlet。

*

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

