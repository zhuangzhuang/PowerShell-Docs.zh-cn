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
# <span data-ttu-id="771f0-102">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="771f0-102">Get-CmsMessage</span></span>

## <span data-ttu-id="771f0-103">摘要</span><span class="sxs-lookup"><span data-stu-id="771f0-103">SYNOPSIS</span></span>
<span data-ttu-id="771f0-104">获取已使用加密消息语法格式进行加密的内容。</span><span class="sxs-lookup"><span data-stu-id="771f0-104">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="771f0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="771f0-105">SYNTAX</span></span>

### <span data-ttu-id="771f0-106">ByContent</span><span class="sxs-lookup"><span data-stu-id="771f0-106">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="771f0-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="771f0-107">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="771f0-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="771f0-108">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="771f0-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="771f0-109">DESCRIPTION</span></span>

<span data-ttu-id="771f0-110">该 `Get-CmsMessage` cmdlet 将获取已使用加密消息语法 (CMS) 格式进行加密的内容。</span><span class="sxs-lookup"><span data-stu-id="771f0-110">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="771f0-111">CMS cmdlet 支持使用 IETF 格式对内容进行加密和解密，如 [RFC5652](https://tools.ietf.org/html/rfc5652)所述。</span><span class="sxs-lookup"><span data-stu-id="771f0-111">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="771f0-112">CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（公匙）和用来解密内容的密匙（私匙）是分离的。</span><span class="sxs-lookup"><span data-stu-id="771f0-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="771f0-113">公匙可以广泛共享，它不是敏感数据。</span><span class="sxs-lookup"><span data-stu-id="771f0-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="771f0-114">如果用此公匙加密了任何内容，只有你的私匙可以解密它。</span><span class="sxs-lookup"><span data-stu-id="771f0-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="771f0-115">有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。</span><span class="sxs-lookup"><span data-stu-id="771f0-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="771f0-116">`Get-CmsMessage` 获取已加密为 CMS 格式的内容。</span><span class="sxs-lookup"><span data-stu-id="771f0-116">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="771f0-117">它不会对内容进行解密或取消保护。</span><span class="sxs-lookup"><span data-stu-id="771f0-117">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="771f0-118">可以运行此 cmdlet 来获取通过运行 cmdlet 加密的内容 `Protect-CmsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="771f0-118">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="771f0-119">可以指定要解密为字符串的内容或旁通到加密内容。</span><span class="sxs-lookup"><span data-stu-id="771f0-119">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="771f0-120">你可以通过管道将结果传递给 `Get-CmsMessage` `Unprotect-CmsMessage` ，以便解密内容，前提是你有用于加密内容的文档加密证书的相关信息。</span><span class="sxs-lookup"><span data-stu-id="771f0-120">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

<span data-ttu-id="771f0-121">PowerShell 7.1 中添加了对 Linux 和 macOS 的支持。</span><span class="sxs-lookup"><span data-stu-id="771f0-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="771f0-122">示例</span><span class="sxs-lookup"><span data-stu-id="771f0-122">EXAMPLES</span></span>

### <span data-ttu-id="771f0-123">示例 1：获取加密的内容</span><span class="sxs-lookup"><span data-stu-id="771f0-123">Example 1: Get encrypted content</span></span>

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

<span data-ttu-id="771f0-124">此命令获取位于 C:\Users\Test\Documents\PowerShell\Future_Plans.txt 的加密内容。</span><span class="sxs-lookup"><span data-stu-id="771f0-124">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="771f0-125">示例 2：通过管道将加密内容传递到 Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="771f0-125">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="771f0-126">此命令通过管道将 `Get-CmsMessage` 示例1中的 cmdlet 结果 `Unprotect-CmsMessage` 传递给，以便对消息进行解密并以纯文本形式进行读取。</span><span class="sxs-lookup"><span data-stu-id="771f0-126">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="771f0-127">在此例中，To 参数的值是加密证书的主题行的值。</span><span class="sxs-lookup"><span data-stu-id="771f0-127">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="771f0-128">解密后的消息“尝试新的 Break All 命令”是结果。</span><span class="sxs-lookup"><span data-stu-id="771f0-128">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="771f0-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="771f0-129">PARAMETERS</span></span>

### <span data-ttu-id="771f0-130">-Content</span><span class="sxs-lookup"><span data-stu-id="771f0-130">-Content</span></span>

<span data-ttu-id="771f0-131">指定加密字符串或包含加密字符串的变量。</span><span class="sxs-lookup"><span data-stu-id="771f0-131">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="771f0-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="771f0-132">-LiteralPath</span></span>

<span data-ttu-id="771f0-133">指定要获取的加密内容的路径。</span><span class="sxs-lookup"><span data-stu-id="771f0-133">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="771f0-134">不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="771f0-134">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="771f0-135">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="771f0-135">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="771f0-136">如果路径包括转义符，请将每个路径括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="771f0-136">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="771f0-137">单引号告诉 PowerShell 不要将包含的字符解释为转义符。</span><span class="sxs-lookup"><span data-stu-id="771f0-137">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="771f0-138">-Path</span><span class="sxs-lookup"><span data-stu-id="771f0-138">-Path</span></span>

<span data-ttu-id="771f0-139">指定要解密的加密内容的路径。</span><span class="sxs-lookup"><span data-stu-id="771f0-139">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="771f0-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="771f0-140">CommonParameters</span></span>

<span data-ttu-id="771f0-141">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="771f0-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="771f0-142">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="771f0-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="771f0-143">输入</span><span class="sxs-lookup"><span data-stu-id="771f0-143">INPUTS</span></span>

## <span data-ttu-id="771f0-144">输出</span><span class="sxs-lookup"><span data-stu-id="771f0-144">OUTPUTS</span></span>

## <span data-ttu-id="771f0-145">注释</span><span class="sxs-lookup"><span data-stu-id="771f0-145">NOTES</span></span>

## <span data-ttu-id="771f0-146">相关链接</span><span class="sxs-lookup"><span data-stu-id="771f0-146">RELATED LINKS</span></span>

[<span data-ttu-id="771f0-147">about_Providers</span><span class="sxs-lookup"><span data-stu-id="771f0-147">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="771f0-148">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="771f0-148">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="771f0-149">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="771f0-149">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)

