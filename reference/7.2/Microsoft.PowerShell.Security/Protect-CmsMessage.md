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
# <span data-ttu-id="2946c-102">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="2946c-102">Protect-CmsMessage</span></span>

## <span data-ttu-id="2946c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2946c-103">SYNOPSIS</span></span>
<span data-ttu-id="2946c-104">使用加密消息语法格式加密内容。</span><span class="sxs-lookup"><span data-stu-id="2946c-104">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="2946c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2946c-105">SYNTAX</span></span>

### <span data-ttu-id="2946c-106">ByContent（默认值）</span><span class="sxs-lookup"><span data-stu-id="2946c-106">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="2946c-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="2946c-107">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="2946c-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="2946c-108">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="2946c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2946c-109">DESCRIPTION</span></span>

<span data-ttu-id="2946c-110">`Protect-CmsMessage`Cmdlet 使用加密消息语法 (CMS) 格式对内容进行加密。</span><span class="sxs-lookup"><span data-stu-id="2946c-110">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="2946c-111">CMS cmdlet 使用 [RFC5652](https://tools.ietf.org/html/rfc5652.html)记录的 IETF 格式支持内容的加密和解密。</span><span class="sxs-lookup"><span data-stu-id="2946c-111">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="2946c-112">CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（公匙）和用来解密内容的密匙（私匙）是分离的。</span><span class="sxs-lookup"><span data-stu-id="2946c-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="2946c-113">公匙可以广泛共享，它不是敏感数据。</span><span class="sxs-lookup"><span data-stu-id="2946c-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="2946c-114">如果用此公匙加密了任何内容，只有你的私匙可以解密它。</span><span class="sxs-lookup"><span data-stu-id="2946c-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="2946c-115">有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。</span><span class="sxs-lookup"><span data-stu-id="2946c-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="2946c-116">`Protect-CmsMessage`必须先设置加密证书，然后才能运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2946c-116">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="2946c-117">若要在 PowerShell 中进行识别，加密证书需要唯一的扩展密钥用法 ([EKU](/windows/desktop/SecCrypto/eku)) ID，以将它们标识为数据加密证书 (如代码签名和加密邮件) 的 id。</span><span class="sxs-lookup"><span data-stu-id="2946c-117">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="2946c-118">有关适用于文档加密的证书的示例，请参阅本主题中的示例 1。</span><span class="sxs-lookup"><span data-stu-id="2946c-118">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

<span data-ttu-id="2946c-119">PowerShell 7.1 中添加了对 Linux 和 macOS 的支持。</span><span class="sxs-lookup"><span data-stu-id="2946c-119">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="2946c-120">示例</span><span class="sxs-lookup"><span data-stu-id="2946c-120">EXAMPLES</span></span>

### <span data-ttu-id="2946c-121">示例 1：创建证书以用于加密内容</span><span class="sxs-lookup"><span data-stu-id="2946c-121">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="2946c-122">`Protect-CmsMessage`必须先创建加密证书，然后才能运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2946c-122">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="2946c-123">使用以下文本，将 "主题" 行中的名称更改为你的姓名、电子邮件或其他标识符，并将证书保存到 (的文件中，如 `DocumentEncryption.inf` 本示例中所示) 。</span><span class="sxs-lookup"><span data-stu-id="2946c-123">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

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

### <span data-ttu-id="2946c-124">示例 2：加密通过电子邮件发送的消息</span><span class="sxs-lookup"><span data-stu-id="2946c-124">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="2946c-125">在下面的示例中，通过将消息通过管道传递给 cmdlet 来加密消息 "Hello World"， `Protect-CmsMessage` 然后将加密的消息保存到变量中。</span><span class="sxs-lookup"><span data-stu-id="2946c-125">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="2946c-126">To 参数使用证书中 Subject 行的值。</span><span class="sxs-lookup"><span data-stu-id="2946c-126">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="2946c-127">示例 3：查看文档加密证书</span><span class="sxs-lookup"><span data-stu-id="2946c-127">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="2946c-128">若要在证书提供程序中查看文档加密证书，可以添加 [get-childitem](../Microsoft.PowerShell.Management/Get-ChildItem.md)的 **DocumentEncryptionCert** 动态参数，仅在加载证书提供程序时可用。</span><span class="sxs-lookup"><span data-stu-id="2946c-128">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="2946c-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2946c-129">PARAMETERS</span></span>

### <span data-ttu-id="2946c-130">-Content</span><span class="sxs-lookup"><span data-stu-id="2946c-130">-Content</span></span>

<span data-ttu-id="2946c-131">指定一个 **PSObject** ，其中包含要加密的内容。</span><span class="sxs-lookup"><span data-stu-id="2946c-131">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="2946c-132">例如，可以加密事件消息的内容，然后使用包含消息 (的变量 `$Event` ，在此示例中) 为 **content** 参数的值： `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` 。</span><span class="sxs-lookup"><span data-stu-id="2946c-132">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="2946c-133">你还可以使用 `Get-Content` cmdlet 来获取文件的内容（例如 Microsoft Word 文档），并将内容保存到用作 **content** 参数值的变量中。</span><span class="sxs-lookup"><span data-stu-id="2946c-133">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

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

### <span data-ttu-id="2946c-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2946c-134">-LiteralPath</span></span>

<span data-ttu-id="2946c-135">指定要加密的内容的路径。</span><span class="sxs-lookup"><span data-stu-id="2946c-135">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="2946c-136">不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="2946c-136">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2946c-137">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="2946c-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2946c-138">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="2946c-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2946c-139">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="2946c-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="2946c-140">-OutFile</span><span class="sxs-lookup"><span data-stu-id="2946c-140">-OutFile</span></span>

<span data-ttu-id="2946c-141">指定要将加密内容发送到的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="2946c-141">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

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

### <span data-ttu-id="2946c-142">-Path</span><span class="sxs-lookup"><span data-stu-id="2946c-142">-Path</span></span>

<span data-ttu-id="2946c-143">指定要加密的内容的路径。</span><span class="sxs-lookup"><span data-stu-id="2946c-143">Specifies the path to content that you want to encrypt.</span></span>

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

### <span data-ttu-id="2946c-144">-To</span><span class="sxs-lookup"><span data-stu-id="2946c-144">-To</span></span>

<span data-ttu-id="2946c-145">指定一个或多个 CMS 消息收件人，以下列任意格式标识：</span><span class="sxs-lookup"><span data-stu-id="2946c-145">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="2946c-146">实际证书（从证书提供程序检索到的）。</span><span class="sxs-lookup"><span data-stu-id="2946c-146">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="2946c-147">指向包含证书的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="2946c-147">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="2946c-148">指向包含证书的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="2946c-148">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="2946c-149">证书的指纹（用于在证书存储中查找）。</span><span class="sxs-lookup"><span data-stu-id="2946c-149">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="2946c-150">证书的使用者名称（用于在证书存储中查找）。</span><span class="sxs-lookup"><span data-stu-id="2946c-150">Subject name of the certificate (used to look in the certificate store).</span></span>

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

### <span data-ttu-id="2946c-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2946c-151">CommonParameters</span></span>

<span data-ttu-id="2946c-152">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="2946c-152">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2946c-153">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2946c-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2946c-154">输入</span><span class="sxs-lookup"><span data-stu-id="2946c-154">INPUTS</span></span>

## <span data-ttu-id="2946c-155">输出</span><span class="sxs-lookup"><span data-stu-id="2946c-155">OUTPUTS</span></span>

## <span data-ttu-id="2946c-156">注释</span><span class="sxs-lookup"><span data-stu-id="2946c-156">NOTES</span></span>

## <span data-ttu-id="2946c-157">相关链接</span><span class="sxs-lookup"><span data-stu-id="2946c-157">RELATED LINKS</span></span>

[<span data-ttu-id="2946c-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2946c-158">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2946c-159">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="2946c-159">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="2946c-160">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="2946c-160">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
