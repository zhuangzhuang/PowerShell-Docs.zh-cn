---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596615"
---
# Set-WSManQuickConfig

## 摘要
配置本地计算机以进行远程管理。

## SYNTAX

### 全部

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## DESCRIPTION

`Set-WSManQuickConfig`Cmdlet 将计算机配置为接收使用 Web Services For management (ws-management) 技术发送的 PowerShell 远程命令。

`Set-WSManQuickConfig` 执行以下操作：

- 检查 WinRM 服务是否正在运行。 如果 WinRM 服务未运行，则启动该服务。
- 将 WinRM 服务启动类型设置为自动。
- 创建一个可接受任何 IP 地址上的请求的侦听器。 默认传输为 **HTTP**。
- 为 WinRM 通信启用防火墙例外。

若要运行 `Set-WSManQuickConfig` ，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。

## 示例

### 示例 1：通过 HTTP 启用本地计算机的远程管理

此示例设置所需的配置以启用本地计算机的远程管理。 默认情况下，此命令会在 **HTTP** 上创建 WS-Management 侦听器。

```powershell
Set-WSManQuickConfig
```

### 示例 2：通过 HTTPS 启用本地计算机的远程管理

此示例设置所需的配置以启用本地计算机的远程管理。 **UseSSL** 参数指定使用 **HTTPS** 与计算机通信。

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **HTTPS** 需要手动配置。 有关详细信息，请参阅 **UseSSL** 参数的说明。

## PARAMETERS

### -Force

强制运行命令而不要求用户确认。

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

### -SkipNetworkProfileCheck

当计算机位于公用网络上时，为远程处理配置 Windows 客户端版本。 此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。

此参数对 Windows 的服务器版本不起作用，默认情况下，该参数具有公用网络的本地子网防火墙规则。 如果在 Windows 的服务器版本上禁用了本地子网防火墙规则， `Enable-PSRemoting` 则无论此参数的值是什么，都将其重新启用。

若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 **NetSecurity** 模块中使用 cmdlet。

此参数是在 PowerShell 3.0 中引入的。

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

### -UseSSL

指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。 默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。 如果使用此参数，并且 SSL 在用于连接的端口上不可用，则该命令将失败。

**HTTPS** 需要手动配置 WinRM 和防火墙规则。 有关详细信息，请参阅 [如何：配置 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

此 cmdlet 不接受任何输入。

## 输出

### 无

此 cmdlet 不会生成任何输出。

## 注释

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[如何：配置 WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Test-WSMan](Test-WSMan.md)

