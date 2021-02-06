---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 59e70f75ac9d822db00419d84055d92a3882c11d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597030"
---
# New-CimSession

## 摘要

创建 CIM 会话。

## SYNTAX

### CredentialParameterSet (默认值) 

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificateParameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## DESCRIPTION

`New-CimSession`Cmdlet 将创建一个 CIM 会话。 CIM 会话是表示与本地计算机或远程计算机的连接的客户端对象。 CIM 会话包含有关连接的信息，例如 **ComputerName**、使用的协议或各种标识符。

此 cmdlet 将返回可供所有其他 CIM cmdlet 使用的 CIM 会话对象。

## 示例

### 示例1：使用默认选项创建 CIM 会话

此示例使用默认选项创建本地 CIM 会话。 如果未指定 **ComputerName** ，则会 `New-CimSession` 创建与本地计算机的 DCOM 会话。

```powershell
New-CimSession
```

### 示例2：创建特定计算机的 CIM 会话

此示例为 **ComputerName** 指定的计算机创建 CIM 会话。
默认情况下， `New-CimSession` 在指定 **ComputerName** 时创建 WSMan 会话。

```powershell
New-CimSession -ComputerName Server01
```

### 示例3：创建多台计算机的 CIM 会话

此示例将在以逗号分隔的列表中为 **ComputerName** 指定的每台计算机创建一个 CIM 会话。

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### 示例4：使用友好名称创建 CIM 会话

此示例将为 **ComputerName** 指定的每台计算机创建一个远程 CIM 会话，以逗号分隔的列表形式创建，并通过指定 **名称** 为新会话分配一个友好名称。

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

可以使用 CIM 会话的友好名称在其他 CIM cmdlet 中引用会话，例如， [CimSession](Get-CimSession.md)。

### 示例5：使用 PSCredential 对象创建到计算机的 CIM 会话

此示例使用由 **Credential** 指定的 **PSCredential** 对象和 **身份验证** 指定的身份验证类型，为 **ComputerName** 指定的计算机创建 CIM 会话。

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

可以使用 cmdlet 创建 **PSCredential** 对象 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。

### 示例6：使用特定端口创建到计算机的 CIM 会话

此示例使用由 **端口** 指定的 TCP 端口，为 **ComputerName** 指定的计算机创建 CIM 会话。

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### 示例7：使用 DCOM 创建 CIM 会话

此示例使用分布式 COM (DCOM) 协议而不是 WSMan 创建 CIM 会话。

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETERS

### -Authentication

指定用于用户凭据的身份验证类型。 此参数的可接受值为：

- 默认
- 摘要
- Negotiate
- 基本
- Kerberos
- NtlmDomain
- CredSsp

不能将 **NtlmDomain** 身份验证类型用于连接到本地计算机。 **CredSSP** 身份验证仅在 windows Vista、windows Server 2008 和更高版本的 windows 中可用。

> [!CAUTION]
> 凭据安全服务提供程序 (CredSSP) 身份验证专用于要求对多个资源（例如访问远程网络共享）进行身份验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权执行此操作的用户帐户的数字公钥证书 (x.509) 。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) PowerShell 证书提供程序中的或 cmdlet。

有关详细信息，请参阅 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

指定要为其创建 CIM 会话的计算机的名称。 指定单个计算机名称或用逗号分隔的多个计算机名称。

如果未指定 **ComputerName** ，则会创建到本地计算机的 CIM 会话。 可以采用以下格式之一指定 "计算机名称" 的值：

- 一个或多个 NetBIOS 名称
- 一个或多个 IP 地址
- 一个或多个完全限定的域名。

如果计算机与用户位于不同的域中，则必须指定完全限定的域名。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 如果未指定 **凭据** ，则使用当前用户帐户。

使用以下格式之一指定 **Credential** 的值：

- 用户名： "User01"
- 域名和用户名： "Domain01\User01"
- 用户主体名称： " User@Domain.com "
- 一个 PSCredential 对象，例如 cmdlet 返回的一个 PSCredential 对象 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。

如果键入用户名，则将提示你输入密码。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定 CIM 会话的友好名称。

使用其他 cmdlet （如 [CimSession](Get-CimSession.md) cmdlet）时，可以使用该名称来引用 CIM 会话。
对于计算机或当前会话，该名称无需是唯一的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet 等待服务器响应的持续时间。

默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。

如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定远程计算机上用于此连接的网络端口。 若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。 使用以下命令配置侦听器：

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

除非必要，否则不要使用 **Port** 参数。 命令中的端口设置适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

为新的 CIM 会话设置高级选项。 输入使用 cmdlet 创建的 **CimSessionOption** 对象的名称 [`New-CimSessionOption`](New-CimSessionOption.md) 。

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

默认情况下，由于 `New-CimSession` 以下两个原因，该 cmdlet 将与远程 WS-Management 终结点建立连接：验证远程服务器是否正在侦听使用 **port** 参数指定的端口号，并验证指定的帐户凭据。 使用标准 WS-Identity 操作完成验证。 如果远程 WS-Management 终结点不能使用 WS 标识，则可以添加 **SkipTestConnection** 开关参数，或减少某些数据传输时间。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### 无

此 cmdlet 不接受输入。

## 输出

### Microsoft.Management.Infrastructure.CimSession

## 注释

## 相关链接

[Get-ChildItem](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-Item](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

