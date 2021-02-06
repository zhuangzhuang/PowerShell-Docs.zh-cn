---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: a29a9ef1e35f0c0f802952b99d853c617614a97b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597025"
---
# Test-WSMan

## 摘要
测试 WinRM 服务是否正在本地或远程计算机上运行。

## SYNTAX

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## DESCRIPTION

**Test-WSMan** 将提交一个标识请求，此请求可确定 WinRM 服务是否正在本地或远程计算机上运行。
如果接受测试的计算机正在运行该服务，则该 cmdlet 将显示被测服务的 WS-Management 标识架构、协议版本、产品供应商以及产品版本。

## 示例

### 示例 1：确定 WinRM 服务的状态

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

此命令确定 WinRM 服务是否正在本地计算机或远程计算机上运行。

### 示例 2：确定远程计算机上 WinRM 服务的状态

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

此命令确定 WinRM 服务是否正在 server01 计算机上运行。

### 示例 3：确定 WinRM 服务的状态和操作系统版本

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

此命令将使用 authentication 参数进行测试以了解 WS-Management (WinRM) 服务是否正在本地计算机上运行。

使用 authentication 参数可允许 **Test-WSMan** 返回操作系统版本。

### 示例 4：确定远程计算机上 WinRM 服务的状态和操作系统版本

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

此命令将使用 authentication 参数进行测试以了解 WS-Management (WinRM) 服务是否正在名为 server01 的计算机上运行。

使用 authentication 参数可允许 **Test-WSMan** 返回操作系统版本。

## PARAMETERS

### -ApplicationName

指定连接中的应用程序名称。
*ApplicationName* 参数的默认值为 WSMAN。
远程终结点的完整标识符采用以下格式：

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

例如： `http://server01:8080/WSMAN`

托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。
默认设置 WSMAN 适用于大多数使用情况。
如果许多计算机建立了与运行 PowerShell 的一台计算机的远程连接，则可以使用此参数。
在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定服务器上要使用的身份验证机制。
此参数的可接受值为：

- 基本。
Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。
- 默认。
使用由 WS-Management 协议实现的身份验证方法。
这是默认设置。
- 摘要。
Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。
- Kerberos。
客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。
- Negotiate。
Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。
例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。
- CredSSP。
使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。
此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。

注意：CredSSP 将用户凭据从本地计算机委派给远程计算机。
此做法增加了远程操作的安全风险。
如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。

重要提示：如果不指定 *Authentication* 参数，则以匿名方式（不使用身份验证）将 **Test-WSMan** 请求发送到远程计算机。
如果以匿名方式发出请求，不会返回特定于操作系统版本的信息。
相反，此 cmdlet 会将操作系统版本和 Service Pack 级别显示为空值（操作系统：0.0.0 SP：0.0）。

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权执行此操作的用户帐户的数字公钥证书 (X509)。
输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。
证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要对其运行管理操作的计算机。
该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。
使用本地计算机名称、localhost 或点 (.) 指定本地计算机。
默认值为本地计算机。
当远程计算机与用户位于不同的域时，必须使用完全限定的域名。
可以通过管道将此参数的值传递给 cmdle。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。
默认为当前用户。
键入用户名，如 User01、Domain01\User01 或 User@Domain.com 。
或者输入一个 PSCredential 对象，例如 Get-Credential cmdlet 返回的一个 **PSCredential** 对象。
键入用户名时，此 cmdlet 会提示输入密码。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定要在客户端连接到 WinRM 服务时使用的端口。
当传输为 HTTP 时，默认端口为 80。
当传输为 HTTPS 时，默认端口为 443。

使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。
默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。
*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。
如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

此 cmdlet 不接受任何输入。

## 输出

### 无

此 cmdlet 将不生成任何输出对象。

## 注释

* 默认情况下，**Test-WSMan** cmdlet 在不使用身份验证的情况下查询 WinRM 服务，并且它不会返回特定于操作系统版本的信息。 相反，它会将操作系统版本和 Service Pack 级别显示为空值（操作系统：0.0.0 SP：0.0）。

*

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

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

