---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2e5d68c2a75ea3040fd3998d2dc469200c054e58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596034"
---
# Set-WSManInstance

## 摘要
修改与某个资源相关的管理信息。

## SYNTAX

### ComputerName（默认值）

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## DESCRIPTION

Set-WSManInstance cmdlet 可修改与某个资源相关的管理信息。

此 cmdlet 使用 WinRM 连接/传输层来修改这些信息。

## 示例

### 示例1：禁用本地计算机上的侦听器

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

此命令可禁用本地计算机上的 https 侦听器。

重要提示：当匹配指定的属性时， *ValueSet* 参数区分大小写。

例如，在此命令中，

这会失败： `-ValueSet @{enabled="False"}`

这会成功： `-ValueSet @{Enabled="False"}`

### 示例2：在本地计算机上设置最大信封大小

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

此命令在本地计算机上将 MaxEnvelopeSizekb 值设置为 200。

重要信息：在与指定的属性进行匹配时，ValueSet 参数区分大小写。

例如，使用上面的命令时，

这会失败：-ValueSet @ {MaxEnvelopeSizeKB = "200"}

这会成功：-ValueSet @ {MaxEnvelopeSizekb = "200"}

### 示例3：禁用远程计算机上的侦听器

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

此命令可禁用远程计算机 SERVER02 上的 https 侦听器。

重要信息：在与指定的属性进行匹配时，ValueSet 参数区分大小写。

例如，使用上面的命令时，

这会失败：-ValueSet @ {enabled = "False"}

这会成功：-ValueSet @ {Enabled = "False"}

## PARAMETERS

### -ApplicationName

指定连接中的应用程序名称。
ApplicationName 参数的默认值为“WSMAN”。
远程终结点的完整标识符采用以下格式：

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

例如：

`http://server01:8080/WSMAN`

托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。
默认设置“WSMAN”适用于大多数使用情况。
当有许多计算机建立了与运行 Windows PowerShell 的一台计算机的远程连接时，需要使用此参数。
在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定服务器上要使用的身份验证机制。
可能的值有：

- Basic：Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。
- Default：使用由 WS-Management 协议实现的身份验证方法。 这是默认设置。
- Digest：Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。
- Kerberos：客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。
- Negotiate：Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。 例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。
- CredSSP：使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。 此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。

注意：CredSSP 将用户的凭据从本地计算机委派给远程计算机。
此做法增加了远程操作的安全风险。
如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

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
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

指定连接终结点。
此字符串的格式为：

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

以下字符串是此参数的格式正确的值：

`http://Server01:8080/WSMAN`

该 URI 必须完全限定。

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。
默认为当前用户。
键入用户名，如 "User01"、"Domain01\User01" 或 " User@Domain.com "。
或者，输入 PSCredential 对象，例如由 Get-Credential cmdlet 返回的对象。
键入用户名时，将会提示你输入密码。

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

### -Dialect

指定要在筛选器谓词中使用的方言。
这可以是远程服务支持的任何方言。
以下别名可用于方言 URI：

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- 选取 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- 关联 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定用于更新管理资源的文件的路径。
通过使用 ResourceURI 参数和 SelectorSet 参数来指定管理资源。
例如，以下命令使用 FilePath 参数：

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

此命令通过使用来自文件的输入对后台处理程序服务调用 StopService 方法。
文件 Input.xml 包含以下内容：

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Fragment

指定实例内要针对指定操作更新或检索的部分。
例如，若要获取后台处理程序服务的状态，请指定“-Fragment Status”。

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

### -OptionSet

将一组开关传递到某个服务以修改或优化请求的性质。
这些开关与命令行 shell 中使用的开关相似，因为它们也是特定于服务的。
可以指定任何数量的选项。

以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：

-OptionSet @{a=1;b=2;c=3}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定要在客户端连接到 WinRM 服务时使用的端口。
当传输为 HTTP 时，默认端口为 80。
当传输为 HTTPS 时，默认端口为 443。
当你使用 HTTPS 作为传输协议时，ComputerName 参数的值必须与服务器的证书公用名 (CN) 匹配。
但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。
SkipCNCheck 参数应该仅用于受信任的计算机。

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceURI

包含资源类或实例的统一资源标识符 (URI)。
URI 用于标识计算机上特定类型的资源，例如磁盘或进程。

URI 由前缀和指向资源的路径组成。
例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet

指定一组用于选择特定管理资源实例的值对。
当相应资源存在多个实例时，将使用 SelectorSet 参数。
SelectorSet 参数的值必须为哈希表。
以下示例显示如何为此参数输入值：

-SelectorSet @{Name="WinRM";ID="yyy"}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

为 WS-Management 会话定义一组扩展选项。
输入你使用 New-WSManSessionOption cmdlet 创建的 SessionOption 对象。
有关可用选项的详细信息，请参阅 New-WSManSessionOption。

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指定应使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。
默认情况下，不使用 SSL。

WS-Management 对通过网络传输的所有 Windows PowerShell 内容进行加密。
利用 UseSSL 参数，你可以指定 HTTPS（而非 HTTP）的额外保护措施。
如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueSet

指定可帮助修改管理资源的哈希表。
通过使用 ResourceURI 参数和 SelectorSet 参数来指定管理资源。
ValueSet 参数的值必须为哈希表。

```yaml
Type: System.Collections.Hashtable
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

此 cmdlet 不接受任何输入。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

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

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

