---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595601"
---
# Get-WSManCredSSP

## 摘要
获取客户端与凭据安全支持提供程序相关的配置。

## SYNTAX

```
Get-WSManCredSSP [<CommonParameters>]
```

## DESCRIPTION
**Enable-wsmancredssp** cmdlet 将获取客户端和服务器的与凭据安全支持提供程序相关的配置。
输出将指示凭据安全支持提供程序 (CredSSP) 身份验证已启用还是已禁用。
此 cmdlet 还显示 CredSSP 的 **AllowFreshCredentials** 策略的配置信息。

使用 CredSSP 身份验证时，用户凭据将传递给要进行身份验证的远程计算机。
此类型的身份验证旨在用于从一个远程会话创建另一个远程会话的命令。
例如，若要在远程计算机上运行后台作业，可以使用此类型的身份验证。

该 cmdlet 将执行以下操作：

- 获取客户端 (**\<localhost|computername\> \Client\Auth\CredSSP**) 上的 WS-Management CredSSP 设置。
- 获取 Windows CredSSP 策略设置 **AllowFreshCredentials**。
- 获取服务器上的 WS-Management CredSSP 设置 (**\<localhost|computername\> \Service\Auth\CredSSP**) 。

注意：CredSSP 身份验证将用户凭据从本地计算机委派给远程计算机。
此做法增加了远程操作的安全风险。
如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。

## 示例

### 示例1：显示 CredSSP 配置

```
PS C:\> Get-WSManCredSSP
```

此命令将显示客户端和服务器的 CredSSP 配置信息。

输出将标识此计算机是否针对 CredSSP 进行了配置。

如果计算机针对 CredSSP 进行了配置，则输出如下：

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

如果计算机未针对 CredSSP 进行配置，则输出如下：

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETERS

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无
此 cmdlet 不接受任何输入。

## 输出

### 无
此 cmdlet 将不生成任何输出。

## 注释

* 若要禁用 CredSSP 身份验证，请使用 Disable-WSManCredSSP cmdlet。 若要启用 CredSSP 身份验证，请使用 Enable-WSManCredSSP cmdlet。

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

