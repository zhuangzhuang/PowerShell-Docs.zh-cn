---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 54a2ca8a28d54bfe1d9676acdaace4592f62620f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599057"
---
# New-CimSessionOption

## 摘要
指定 New-CimSession cmdlet 的高级选项。

## SYNTAX

### ProtocolTypeSet (默认值) 

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## DESCRIPTION

`New-CimSessionOption`Cmdlet 可创建 CIM 会话选项对象的实例。 使用 CIM 会话选项对象作为 cmdlet 的输入 `New-CimSession` 来指定 CIM 会话的选项。

此 cmdlet 具有两个参数集，一个用于 WsMan 选项，一个用于分布式组件对象模型 (DCOM) 选项。 根据你使用的参数，该 cmdlet 将返回 DCOM 会话选项的实例，或返回 WsMan 会话选项。

## 示例

### 示例1：为 DCOM 创建 CIM 会话选项对象

此示例为 DCOM 协议创建一个 CIM 会话选项对象，并将其存储在一个名为的变量中 `$so` 。 然后，将变量的内容传递给 `New-CimSession` cmdlet。
`New-CimSession` 然后，使用变量中定义的选项，使用名为 Server01 的远程服务器创建一个新的 CIM 会话。

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### 示例2：为 WsMan 创建 CIM 会话选项对象

此示例为 WsMan 协议创建 CIM 会话选项对象。 对象包含 **ProxyAuthentication** 参数所指定的 **Kerberos** 身份验证模式的配置、 **ProxyCredential** 参数指定的凭据，并指定该命令将跳过 CA 检查，跳过 CN 检查并使用 SSL。

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### 示例3：使用指定的区域性创建 CIM 会话选项对象

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

此示例指定用于 CIM 会话的区域性。 默认情况下，在执行操作时将使用客户端的区域性。 但是，可以使用 **culture** 参数重写默认区域性。

## PARAMETERS

### -Culture

指定要用于 CIM 会话的用户界面区域性。 使用以下格式之一指定此参数的值：

- 格式为的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 "en-us"。
- 包含 **CultureInfo** 对象的变量。
- 用于获取 **CultureInfo** 对象的命令，如 [获取区域性](../Microsoft.PowerShell.Utility/Get-Culture.md)

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

指示 Kerberos 连接连接到其服务主体名称 (SPN) 包含服务端口号的服务。 这种类型的连接不常用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

指定用于 WsMan 协议的编码。 此参数的可接受值为： **Default**、 **Utf8** 或 **Utf16**。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

指定计算机名称和端口号后面的 HTTP URL 部分。 更改此情况并不常见。 默认情况下，此参数的值为 **/wsman**。

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Impersonation

使用模拟 Windows Management Instrumentation (WMI) 创建 DCOM 会话。

此参数的有效值是：

- 默认： DCOM 可以使用其常规安全协商算法选择模拟级别。
- 无：客户端对于服务器是匿名的。 服务器进程可以模拟客户端，但模拟标记不包含任何信息，因此不能使用。
- 标识：允许对象查询调用方的凭据。
- 模拟：允许对象使用调用方的凭据。
- 委托：允许对象允许其他对象使用调用方的凭据。

如果未指定 **模拟** ，则 `New-CimSession` cmdlet 将使用值 " **模拟**"。

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

指定任一方向的 WsMan XML 消息的大小限制。

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoEncryption

指定禁用数据加密。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

指定创建到 WMI 的 DCOM 会话使用组件对象模型 (COM) _PacketIntegrity_ 功能。 默认情况下，使用 DCOM 创建的所有 CIM 会话都将 **PacketIntegrity** 参数设置为 **True**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

使用 COM _PacketPrivacy_ 创建到 WMI 的 DCOM 会话。 默认情况下，使用 DCOM 创建的所有 CIM 会话都将 **PacketPrivacy** 参数设置为 **true**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

指定要使用的协议。 此参数可接受的值包括： **DCOM**、 **默认** 或 **Wsman**。

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

指定用于代理解析的身份验证方法。 此参数可接受的值包括： **Default**、 **Digest**、 **Negotiate**、 **Basic**、 **Kerberos**、 **NtlmDomain** 或 **CredSsp**。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

指定用于代理身份验证的用户帐户的 (x.509) 数字公钥证书。
输入证书的证书指纹。 在基于客户端证书的身份验证中使用证书。 它们只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或 cmdlet。

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

指定用于代理身份验证的凭据。 输入下列项之一：

- 包含 PSCredential 对象的变量。
- 用于获取 PSCredential 对象的命令，例如 `Get-Credential`

如果未设置此选项，则不能指定任何凭据。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

指定要使用的主机名解析机制。 此参数的可接受值为： **None**、 **WinHttp**、 **Auto** 或 **microsoft-windows-ie-internetexplorer**。

此参数的默认值为 **microsoft-windows-ie-internetexplorer**。

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

指示当通过 HTTPS 进行连接时，客户端不会验证服务器证书是否由受信任的证书颁发机构签名 (CA) 。

仅在使用其他机制信任远程计算机时（例如，当远程计算机是物理安全和隔离的网络的一部分，或者当远程计算机在 WinRM 配置中列为受信任的主机时）才使用此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

指示服务器 (CN) 的证书公用名无需与服务器的主机名匹配。 此参数仅适用于使用 HTTPS 协议的受信任计算机的远程操作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

指示跳过对服务器证书的吊销检查。 仅对受信任的计算机使用此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UICulture

指定要用于 CIM 会话的用户界面区域性。 使用以下格式之一指定此参数的值：

- 格式为的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 "en-us"。
- 包含 CultureInfo 对象的变量。
- 用于获取 CultureInfo 对象的命令，例如 `Get-Culture` 。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

指示应使用 SSL 建立与远程计算机的连接。 默认情况下，不使用 SSL。 WsMan 会对通过网络传输的所有内容进行加密，即使在使用 HTTP 时也是如此。

此参数可用于指定对 HTTPS （而非 HTTP）的额外保护。 如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。

建议仅在未指定 **PacketPrivacy** 参数时使用此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

此 cmdlet 不接受输入对象。

## 输出

### CIMSessionOption

此 cmdlet 将返回包含 CIM 会话选项信息的对象。

## 注释

## 相关链接

[Get-ChildItem](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-Culture](../microsoft.powershell.utility/get-culture.md)

[Get-Item](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)

