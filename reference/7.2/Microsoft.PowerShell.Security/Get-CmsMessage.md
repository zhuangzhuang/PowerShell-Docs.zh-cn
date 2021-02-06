---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 421b49139f4750787b6c1c04d8a41a624755109a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598268"
---
# Get-CmsMessage

## 摘要
获取已使用加密消息语法格式进行加密的内容。

## SYNTAX

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## DESCRIPTION

该 `Get-CmsMessage` cmdlet 将获取已使用加密消息语法 (CMS) 格式进行加密的内容。

CMS cmdlet 支持使用 IETF 格式对内容进行加密和解密，如 [RFC5652](https://tools.ietf.org/html/rfc5652)所述。

CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（公匙）和用来解密内容的密匙（私匙）是分离的。 公匙可以广泛共享，它不是敏感数据。 如果用此公匙加密了任何内容，只有你的私匙可以解密它。 有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。

`Get-CmsMessage` 获取已加密为 CMS 格式的内容。 它不会对内容进行解密或取消保护。 可以运行此 cmdlet 来获取通过运行 cmdlet 加密的内容 `Protect-CmsMessage` 。 可以指定要解密为字符串的内容或旁通到加密内容。 你可以通过管道将结果传递给 `Get-CmsMessage` `Unprotect-CmsMessage` ，以便解密内容，前提是你有用于加密内容的文档加密证书的相关信息。

PowerShell 7.1 中添加了对 Linux 和 macOS 的支持。

## 示例

### 示例 1：获取加密的内容

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

此命令获取位于 C:\Users\Test\Documents\PowerShell\Future_Plans.txt 的加密内容。

### 示例 2：通过管道将加密内容传递到 Unprotect-CmsMessage

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

此命令通过管道将 `Get-CmsMessage` 示例1中的 cmdlet 结果 `Unprotect-CmsMessage` 传递给，以便对消息进行解密并以纯文本形式进行读取。 在此例中，To 参数的值是加密证书的主题行的值。 解密后的消息“尝试新的 Break All 命令”是结果。

## PARAMETERS

### -Content

指定加密字符串或包含加密字符串的变量。

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定要获取的加密内容的路径。 不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径包括转义符，请将每个路径括在单引号中。
单引号告诉 PowerShell 不要将包含的字符解释为转义符。

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

### -Path

指定要解密的加密内容的路径。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

## 注释

## 相关链接

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Protect-CmsMessage](Protect-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)

