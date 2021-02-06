---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 57213b72bee5733f6e8089ff7dcbb9be82104d8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603404"
---
# Protect-CmsMessage

## 摘要
使用加密消息语法格式加密内容。

## SYNTAX

### ByContent（默认值）

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`Protect-CmsMessage`Cmdlet 使用加密消息语法 (CMS) 格式对内容进行加密。

CMS cmdlet 使用 [RFC5652](https://tools.ietf.org/html/rfc5652.html)记录的 IETF 格式支持内容的加密和解密。

CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（公匙）和用来解密内容的密匙（私匙）是分离的。 公匙可以广泛共享，它不是敏感数据。 如果用此公匙加密了任何内容，只有你的私匙可以解密它。 有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。

`Protect-CmsMessage`必须先设置加密证书，然后才能运行 cmdlet。
若要在 PowerShell 中进行识别，加密证书需要唯一的扩展密钥用法 ([EKU](/windows/desktop/SecCrypto/eku)) ID，以将它们标识为数据加密证书 (如代码签名和加密邮件) 的 id。 有关适用于文档加密的证书的示例，请参阅本主题中的示例 1。

PowerShell 7.1 中添加了对 Linux 和 macOS 的支持。

## 示例

### 示例 1：创建证书以用于加密内容

`Protect-CmsMessage`必须先创建加密证书，然后才能运行 cmdlet。 使用以下文本，将 "主题" 行中的名称更改为你的姓名、电子邮件或其他标识符，并将证书保存到 (的文件中，如 `DocumentEncryption.inf` 本示例中所示) 。

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### 示例 2：加密通过电子邮件发送的消息

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

在下面的示例中，通过将消息通过管道传递给 cmdlet 来加密消息 "Hello World"， `Protect-CmsMessage` 然后将加密的消息保存到变量中。 To 参数使用证书中 Subject 行的值。

### 示例 3：查看文档加密证书

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

若要在证书提供程序中查看文档加密证书，可以添加 [get-childitem](../Microsoft.PowerShell.Management/Get-ChildItem.md)的 **DocumentEncryptionCert** 动态参数，仅在加载证书提供程序时可用。

## PARAMETERS

### -Content

指定一个 **PSObject** ，其中包含要加密的内容。 例如，可以加密事件消息的内容，然后使用包含消息 (的变量 `$Event` ，在此示例中) 为 **content** 参数的值： `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` 。 你还可以使用 `Get-Content` cmdlet 来获取文件的内容（例如 Microsoft Word 文档），并将内容保存到用作 **content** 参数值的变量中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定要加密的内容的路径。 不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutFile

指定要将加密内容发送到的文件的路径和文件名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要加密的内容的路径。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

指定一个或多个 CMS 消息收件人，以下列任意格式标识：

- 实际证书（从证书提供程序检索到的）。
- 指向包含证书的文件的路径。
- 指向包含证书的目录的路径。
- 证书的指纹（用于在证书存储中查找）。
- 证书的使用者名称（用于在证书存储中查找）。

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

## 输出

## 注释

## 相关链接

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)
