---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: e2456e1da866929d60c36cc0e09990399b41614b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595801"
---
# Invoke-WSManAction

## 摘要
对由资源 URI 和选择器指定的对象调用操作。

## SYNTAX

### URI (默认值) 

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### 计算机名

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## DESCRIPTION
**Invoke-wsmanaction** 对 RESOURCE_URI 指定的对象运行操作，其中的参数由键值对指定。

此 cmdlet 使用 WSMan 连接/传输层来运行操作。

## 示例

### 示例1：调用方法

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令调用对应于后台处理程序服务 Win32_Service WMI 类实例的 **StartService** 方法。

返回值指示操作是否成功。
在这种情况下，返回值 0 指示成功。
返回值 5 指示该服务已启动。

### 示例2：调用方法

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令通过使用来自文件的输入对后台处理程序服务调用 **StopService** 方法。
文件 Input.xml 包含以下内容：

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### 示例3：使用指定的参数值调用方法

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

此命令调用 Win32_Process 类的 **Create** 方法。
它将方法传递两个参数值，Notepad.exe 和 C:\
因此，将创建一个新进程来运行记事本，新进程的当前目录将设置为 C:\。

### 示例4：在远程计算机上调用方法

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令调用对应于后台处理程序服务 Win32_Service WMI 类实例的 **StartService** 方法。
由于指定了 *ComputerName* 参数，因此该命令针对远程 server01 计算机运行。

## PARAMETERS

### -Action
指定要在由 ResourceURI 和选择器指定的管理对象上运行的方法。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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
Parameter Sets: ComputerName
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
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
指定连接终结点。
此字符串的格式如下：

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

以下字符串是此参数的格式正确的值：

`http://Server01:8080/WSMAN`

URI 必须完全限定。

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -FilePath
指定用于更新管理资源的文件的路径。
通过使用 *ResourceURI* 参数和 *SelectorSet* 参数来指定管理资源。
例如，以下命令使用 *FilePath* 参数：

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

此命令通过使用来自文件的输入对 **后台处理程序** 服务调用 **StopService** 方法。
文件 Input.xml 包含以下内容：

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OptionSet
将一组开关指定到某个服务以修改或优化请求的性质。
这些开关类似于命令行 shell 中使用的开关，因为它们也特定于服务。
可以指定任何数量的选项。

以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Port
指定要在客户端连接到 WinRM 服务时使用的端口。
当传输为 HTTP 时，默认端口为 80。
当传输为 HTTPS 时，默认端口为 443。

使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。
但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。
SkipCNCheck 参数应仅用于受信任的计算机。

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
指定资源类或实例的 URI。
URI 用于标识计算机上特定类型的资源，例如磁盘或进程。

URI 由资源的前缀和路径组成。
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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SelectorSet
指定一组用于选择特定管理资源实例的值对。
当存在多个资源实例时，将使用 *SelectorSet* 。
SelectorSet 的值必须为哈希表。

以下示例显示如何为此参数输入值：

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption
为 WS-Management 会话指定扩展选项。
输入使用 New-WSManSessionOption cmdlet 创建的 **SessionOption** 对象。
有关可用选项的详细信息，请键入 `Get-Help New-WSManSessionOption`。

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
指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。
默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。
*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。
如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueSet
指定可帮助修改管理资源的哈希表。
使用 *ResourceURI* 和 *SelectorSet* 指定管理资源。
*ValueSet* 参数的值必须为哈希表。

```yaml
Type: System.Collections.Hashtable
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
此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

