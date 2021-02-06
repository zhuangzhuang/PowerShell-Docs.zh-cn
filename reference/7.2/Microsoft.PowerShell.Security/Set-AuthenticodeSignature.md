---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 831f40e9bd24cee20eeae54a41e0b022dc6300da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595831"
---
# <span data-ttu-id="cac9a-102">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="cac9a-102">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="cac9a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cac9a-103">SYNOPSIS</span></span>
<span data-ttu-id="cac9a-104">将 [Authenticode](/windows-hardware/drivers/install/authenticode) 签名添加到 PowerShell 脚本或其他文件中。</span><span class="sxs-lookup"><span data-stu-id="cac9a-104">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="cac9a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cac9a-105">SYNTAX</span></span>

### <span data-ttu-id="cac9a-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="cac9a-106">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cac9a-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="cac9a-107">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cac9a-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="cac9a-108">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cac9a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cac9a-109">DESCRIPTION</span></span>

<span data-ttu-id="cac9a-110">`Set-AuthenticodeSignature`Cmdlet 将验证码签名添加到支持主题界面包 (SIP) 的任何文件。</span><span class="sxs-lookup"><span data-stu-id="cac9a-110">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="cac9a-111">在 PowerShell 脚本文件中，该签名采用文本块的形式，它指示在脚本中执行的说明的结束。</span><span class="sxs-lookup"><span data-stu-id="cac9a-111">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="cac9a-112">如果在此 cmdlet 运行时文件中有签名，则该签名被删除。</span><span class="sxs-lookup"><span data-stu-id="cac9a-112">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="cac9a-113">示例</span><span class="sxs-lookup"><span data-stu-id="cac9a-113">EXAMPLES</span></span>

### <span data-ttu-id="cac9a-114">示例 1-使用本地证书存储中的证书对脚本进行签名</span><span class="sxs-lookup"><span data-stu-id="cac9a-114">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="cac9a-115">这些命令从 PowerShell 证书提供程序检索代码签名证书，并使用它对 PowerShell 脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-115">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="cac9a-116">第一个命令使用 `Get-ChildItem` cmdlet 和 PowerShell 证书提供程序来获取 `Cert:\CurrentUser\My` 证书存储区中的证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-116">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="cac9a-117">`Cert:`驱动器是由证书提供程序公开的驱动器。</span><span class="sxs-lookup"><span data-stu-id="cac9a-117">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="cac9a-118">仅证书提供程序支持的 **CodeSigningCert** 参数将检索到的证书限制为具有代码签名颁发机构的证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-118">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="cac9a-119">该命令将结果存储在 `$cert` 变量中。</span><span class="sxs-lookup"><span data-stu-id="cac9a-119">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="cac9a-120">第二个命令使用 `Set-AuthenticodeSignature` cmdlet 对脚本进行签名 `PSTestInternet2.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-120">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="cac9a-121">它使用 **FilePath** 参数来指定脚本的名称，并使用 **certificate** 参数来指定在变量中存储证书 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-121">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="cac9a-122">使用 **CodeSigningCert** 参数 `Get-ChildItem` 只返回具有代码签名颁发机构并包含私钥的证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-122">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="cac9a-123">如果没有私钥，则不能使用证书进行签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-123">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="cac9a-124">示例 2-使用 PFX 文件中的证书对脚本进行签名</span><span class="sxs-lookup"><span data-stu-id="cac9a-124">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="cac9a-125">这些命令使用 `Get-PfxCertificate` cmdlet 加载代码签名证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-125">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="cac9a-126">然后，使用它对 PowerShell 脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-126">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="cac9a-127">第一个命令使用 `Get-PfxCertificate` cmdlet 将 C:\Test\MySign.pfx 证书加载到 `$cert` 变量中。</span><span class="sxs-lookup"><span data-stu-id="cac9a-127">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="cac9a-128">第二个命令使用 `Set-AuthenticodeSignature` 对脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-128">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="cac9a-129">的 **FilePath** 参数 `Set-AuthenticodeSignature` 指定要签名的脚本文件的路径， **Cert** 参数将 `$cert` 包含证书的变量传递到 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-129">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="cac9a-130">如果证书文件受密码保护，则 PowerShell 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="cac9a-130">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="cac9a-131">示例 3-添加包含根证书颁发机构的签名</span><span class="sxs-lookup"><span data-stu-id="cac9a-131">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="cac9a-132">此命令添加数字签名，它包括信任链中的根证书颁发机构，并由第三方时间戳服务器对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-132">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="cac9a-133">该命令使用 **FilePath** 参数来指定要签名的脚本，并使用 **Certificate** 参数来指定在变量中保存的证书 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-133">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="cac9a-134">它使用 **IncludeChain** 参数来包括信任链中的所有签名，包括根证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="cac9a-134">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="cac9a-135">它还使用 **TimeStampServer** 参数将时间戳添加到签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-135">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="cac9a-136">这会阻止脚本在证书过期时失败。</span><span class="sxs-lookup"><span data-stu-id="cac9a-136">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="cac9a-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cac9a-137">PARAMETERS</span></span>

### <span data-ttu-id="cac9a-138">-Certificate</span><span class="sxs-lookup"><span data-stu-id="cac9a-138">-Certificate</span></span>

<span data-ttu-id="cac9a-139">指定将用来对脚本或文件进行签名的证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-139">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="cac9a-140">输入存储对象的变量，该对象表示证书或获取证书的表达式。</span><span class="sxs-lookup"><span data-stu-id="cac9a-140">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="cac9a-141">若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书驱动器中的 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-141">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="cac9a-142">如果证书无效或没有 `code-signing` 权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="cac9a-142">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-143">-FilePath</span><span class="sxs-lookup"><span data-stu-id="cac9a-143">-FilePath</span></span>

<span data-ttu-id="cac9a-144">指定正进行签名的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="cac9a-144">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-145">-Force</span><span class="sxs-lookup"><span data-stu-id="cac9a-145">-Force</span></span>

<span data-ttu-id="cac9a-146">允许该 cmdlet 将签名追加到只读文件。</span><span class="sxs-lookup"><span data-stu-id="cac9a-146">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="cac9a-147">即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="cac9a-147">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="cac9a-148">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="cac9a-148">-HashAlgorithm</span></span>

<span data-ttu-id="cac9a-149">指定 Windows 用来计算文件的数字签名的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="cac9a-149">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="cac9a-150">对于 PowerShell 3.0，默认值为 SHA256，它是 Windows 默认哈希算法。</span><span class="sxs-lookup"><span data-stu-id="cac9a-150">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="cac9a-151">对于 PowerShell 2.0，默认值为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="cac9a-151">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="cac9a-152">使用不同的哈希算法进行签名的文件可能无法在其他系统上识别。</span><span class="sxs-lookup"><span data-stu-id="cac9a-152">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="cac9a-153">支持哪些算法取决于操作系统的版本。</span><span class="sxs-lookup"><span data-stu-id="cac9a-153">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="cac9a-154">有关可能值的列表，请参阅 [HashAlgorithmName 结构](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)。</span><span class="sxs-lookup"><span data-stu-id="cac9a-154">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-155">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="cac9a-155">-IncludeChain</span></span>

<span data-ttu-id="cac9a-156">确定证书信任链中的哪些证书包含在数字签名中。</span><span class="sxs-lookup"><span data-stu-id="cac9a-156">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="cac9a-157">默认值为 **NotRoot** 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-157">**NotRoot** is the default.</span></span>

<span data-ttu-id="cac9a-158">有效值是：</span><span class="sxs-lookup"><span data-stu-id="cac9a-158">Valid values are:</span></span>

- <span data-ttu-id="cac9a-159">签名者：仅包括签名者的证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-159">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="cac9a-160">NotRoot：包括证书链中的所有证书，根颁发机构除外。</span><span class="sxs-lookup"><span data-stu-id="cac9a-160">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="cac9a-161">所有：包括证书链中的所有证书。</span><span class="sxs-lookup"><span data-stu-id="cac9a-161">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-162">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="cac9a-162">-TimestampServer</span></span>

<span data-ttu-id="cac9a-163">使用指定的时间戳服务器将时间戳添加到签名。</span><span class="sxs-lookup"><span data-stu-id="cac9a-163">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="cac9a-164">以字符串的形式键入时间戳服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="cac9a-164">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="cac9a-165">时间戳表示将证书添加到文件的确切时间。</span><span class="sxs-lookup"><span data-stu-id="cac9a-165">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="cac9a-166">如果证书过期，时间戳可阻止脚本失败，因为用户和程序可以验证在签名时证书有效。</span><span class="sxs-lookup"><span data-stu-id="cac9a-166">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

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

### <span data-ttu-id="cac9a-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cac9a-167">-LiteralPath</span></span>

<span data-ttu-id="cac9a-168">指定正进行签名的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="cac9a-168">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="cac9a-169">与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="cac9a-169">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="cac9a-170">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="cac9a-170">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="cac9a-171">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="cac9a-171">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="cac9a-172">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="cac9a-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-173">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="cac9a-173">-SourcePathOrExtension</span></span>

<span data-ttu-id="cac9a-174">要添加数字签名的内容的文件或文件类型的路径。</span><span class="sxs-lookup"><span data-stu-id="cac9a-174">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="cac9a-175">此参数用于将文件内容作为字节数组传递的 **内容** 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-175">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-176">-Content</span><span class="sxs-lookup"><span data-stu-id="cac9a-176">-Content</span></span>

<span data-ttu-id="cac9a-177">文件内容作为为其添加数字签名的字节数组。</span><span class="sxs-lookup"><span data-stu-id="cac9a-177">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="cac9a-178">此参数必须与 **SourcePathOrExtension** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="cac9a-178">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="cac9a-179">文件的内容必须采用 Unicode 格式 (UTF-16LE) 格式。</span><span class="sxs-lookup"><span data-stu-id="cac9a-179">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cac9a-180">-Confirm</span></span>

<span data-ttu-id="cac9a-181">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cac9a-181">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cac9a-182">-WhatIf</span></span>

<span data-ttu-id="cac9a-183">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cac9a-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cac9a-184">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cac9a-184">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cac9a-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cac9a-185">CommonParameters</span></span>

<span data-ttu-id="cac9a-186">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cac9a-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cac9a-187">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cac9a-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cac9a-188">输入</span><span class="sxs-lookup"><span data-stu-id="cac9a-188">INPUTS</span></span>

### <span data-ttu-id="cac9a-189">System.String</span><span class="sxs-lookup"><span data-stu-id="cac9a-189">System.String</span></span>

<span data-ttu-id="cac9a-190">可以通过管道将包含文件路径的字符串传递给 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="cac9a-190">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="cac9a-191">输出</span><span class="sxs-lookup"><span data-stu-id="cac9a-191">OUTPUTS</span></span>

### <span data-ttu-id="cac9a-192">System.Management.Automation.Signature</span><span class="sxs-lookup"><span data-stu-id="cac9a-192">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="cac9a-193">注释</span><span class="sxs-lookup"><span data-stu-id="cac9a-193">NOTES</span></span>

<span data-ttu-id="cac9a-194">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="cac9a-194">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="cac9a-195">相关链接</span><span class="sxs-lookup"><span data-stu-id="cac9a-195">RELATED LINKS</span></span>

[<span data-ttu-id="cac9a-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="cac9a-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="cac9a-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="cac9a-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="cac9a-198">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="cac9a-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="cac9a-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="cac9a-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="cac9a-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="cac9a-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="cac9a-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="cac9a-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
