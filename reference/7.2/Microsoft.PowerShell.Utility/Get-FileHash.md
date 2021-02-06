---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599064"
---
# <span data-ttu-id="896ea-102">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="896ea-102">Get-FileHash</span></span>

## <span data-ttu-id="896ea-103">摘要</span><span class="sxs-lookup"><span data-stu-id="896ea-103">SYNOPSIS</span></span>
<span data-ttu-id="896ea-104">通过使用指定的哈希算法，计算文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-104">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="896ea-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="896ea-105">SYNTAX</span></span>

### <span data-ttu-id="896ea-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="896ea-106">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="896ea-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="896ea-107">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="896ea-108">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="896ea-108">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="896ea-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="896ea-109">DESCRIPTION</span></span>

<span data-ttu-id="896ea-110">`Get-FileHash`Cmdlet 通过使用指定的哈希算法来计算文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-110">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="896ea-111">哈希值是对应文件内容的唯一值。</span><span class="sxs-lookup"><span data-stu-id="896ea-111">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="896ea-112">哈希将唯一值分配到文件的内容，而不是通过其文件名、扩展名或其他指定标识文件的内容。</span><span class="sxs-lookup"><span data-stu-id="896ea-112">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="896ea-113">可以更改文件名和扩展名，而无需更改文件的内容，而且无需更改哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-113">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="896ea-114">同样，可以更改文件的内容，而无需更改名称或扩展名。</span><span class="sxs-lookup"><span data-stu-id="896ea-114">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="896ea-115">但是，即使更改文件内容中的单个字符也会更改该文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-115">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="896ea-116">哈希值的用途是提供加密型安全的方式，以验证尚未更改文件的内容。</span><span class="sxs-lookup"><span data-stu-id="896ea-116">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="896ea-117">尽管一些哈希算法（包括 MD5 和 SHA1）不再被认为是安全的，但安全哈希算法的目标是使它无法更改文件的内容，无论是意外发生，还是恶意或未经授权的尝试--并维护相同的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-117">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="896ea-118">你还可以使用哈希值来确定两个不同的文件是否具有完全相同的内容。</span><span class="sxs-lookup"><span data-stu-id="896ea-118">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="896ea-119">如果两个文件的哈希值相同，则文件的内容也相同。</span><span class="sxs-lookup"><span data-stu-id="896ea-119">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="896ea-120">默认情况下，该 `Get-FileHash` cmdlet 使用 SHA256 算法，尽管可以使用目标操作系统支持的任何哈希算法。</span><span class="sxs-lookup"><span data-stu-id="896ea-120">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="896ea-121">示例</span><span class="sxs-lookup"><span data-stu-id="896ea-121">EXAMPLES</span></span>

### <span data-ttu-id="896ea-122">示例1：计算文件的哈希值</span><span class="sxs-lookup"><span data-stu-id="896ea-122">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="896ea-123">此示例使用 `Get-FileHash` cmdlet 来计算文件的哈希值 `/etc/apt/sources.list` 。</span><span class="sxs-lookup"><span data-stu-id="896ea-123">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="896ea-124">使用的哈希算法是默认值 **SHA256**。</span><span class="sxs-lookup"><span data-stu-id="896ea-124">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="896ea-125">将输出通过管道传输到 `Format-List` cmdlet，以将输出的格式设置为列表。</span><span class="sxs-lookup"><span data-stu-id="896ea-125">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="896ea-126">示例2：计算 ISO 文件的哈希值</span><span class="sxs-lookup"><span data-stu-id="896ea-126">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="896ea-127">此示例使用 `Get-FileHash` cmdlet 和 **SHA384** 算法来计算管理员已从 INTERNET 下载的 ISO 文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-127">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="896ea-128">将输出通过管道传输到 `Format-List` cmdlet，以将输出的格式设置为列表。</span><span class="sxs-lookup"><span data-stu-id="896ea-128">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="896ea-129">示例3：计算流的哈希值</span><span class="sxs-lookup"><span data-stu-id="896ea-129">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="896ea-130">在此示例中，我们将使用 **系统 .net. WebClient** 从 [Powershell 版本页](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)下载包。</span><span class="sxs-lookup"><span data-stu-id="896ea-130">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="896ea-131">发布页面还记录每个包文件的 SHA256 哈希。</span><span class="sxs-lookup"><span data-stu-id="896ea-131">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="896ea-132">我们可以将发布的哈希值与我们用计算的哈希值进行比较 `Get-FileHash` 。</span><span class="sxs-lookup"><span data-stu-id="896ea-132">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="896ea-133">示例4：计算字符串的哈希值</span><span class="sxs-lookup"><span data-stu-id="896ea-133">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="896ea-134">PowerShell 不提供 cmdlet 来计算字符串的哈希。</span><span class="sxs-lookup"><span data-stu-id="896ea-134">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="896ea-135">但是，您可以将字符串写入流，并使用的 **InputStream** 参数 `Get-FileHash` 获取哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-135">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="896ea-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="896ea-136">PARAMETERS</span></span>

### <span data-ttu-id="896ea-137">-算法</span><span class="sxs-lookup"><span data-stu-id="896ea-137">-Algorithm</span></span>

<span data-ttu-id="896ea-138">指定用于计算指定文件或流的内容的哈希值的加密哈希函数。</span><span class="sxs-lookup"><span data-stu-id="896ea-138">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="896ea-139">加密哈希函数的属性可以查找具有相同哈希值的两个不同文件。</span><span class="sxs-lookup"><span data-stu-id="896ea-139">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="896ea-140">哈希函数通常与数字签名一起使用并用来保持数据的完整性。</span><span class="sxs-lookup"><span data-stu-id="896ea-140">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="896ea-141">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="896ea-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="896ea-142">SHA1</span><span class="sxs-lookup"><span data-stu-id="896ea-142">SHA1</span></span>
- <span data-ttu-id="896ea-143">SHA256</span><span class="sxs-lookup"><span data-stu-id="896ea-143">SHA256</span></span>
- <span data-ttu-id="896ea-144">SHA384</span><span class="sxs-lookup"><span data-stu-id="896ea-144">SHA384</span></span>
- <span data-ttu-id="896ea-145">SHA512</span><span class="sxs-lookup"><span data-stu-id="896ea-145">SHA512</span></span>
- <span data-ttu-id="896ea-146">MD5</span><span class="sxs-lookup"><span data-stu-id="896ea-146">MD5</span></span>

<span data-ttu-id="896ea-147">如果未指定任何值，或省略了参数，则默认值为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="896ea-147">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="896ea-148">出于安全原因，MD5 和 SHA1（不再认为是安全的）仅应该用于简单的更改验证，而且不应该用于生成要求保护免受攻击或篡改的文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="896ea-148">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="896ea-149">-InputStream</span><span class="sxs-lookup"><span data-stu-id="896ea-149">-InputStream</span></span>

<span data-ttu-id="896ea-150">指定输入流。</span><span class="sxs-lookup"><span data-stu-id="896ea-150">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="896ea-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="896ea-151">-LiteralPath</span></span>

<span data-ttu-id="896ea-152">指定到文件的路径。</span><span class="sxs-lookup"><span data-stu-id="896ea-152">Specifies the path to a file.</span></span> <span data-ttu-id="896ea-153">与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="896ea-153">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="896ea-154">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="896ea-154">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="896ea-155">如果路径包括转义符，则请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="896ea-155">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="896ea-156">单引号指示 PowerShell 不要将字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="896ea-156">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="896ea-157">-Path</span><span class="sxs-lookup"><span data-stu-id="896ea-157">-Path</span></span>

<span data-ttu-id="896ea-158">将一个或多个文件的路径指定为一个数组。</span><span class="sxs-lookup"><span data-stu-id="896ea-158">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="896ea-159">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="896ea-159">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="896ea-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="896ea-160">CommonParameters</span></span>

<span data-ttu-id="896ea-161">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="896ea-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="896ea-162">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="896ea-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="896ea-163">输入</span><span class="sxs-lookup"><span data-stu-id="896ea-163">INPUTS</span></span>

### <span data-ttu-id="896ea-164">System.String</span><span class="sxs-lookup"><span data-stu-id="896ea-164">System.String</span></span>

<span data-ttu-id="896ea-165">可以通过管道将字符串传递给 `Get-FileHash` 包含一个或多个文件的路径的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="896ea-165">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="896ea-166">输出</span><span class="sxs-lookup"><span data-stu-id="896ea-166">OUTPUTS</span></span>

### <span data-ttu-id="896ea-167">Get-filehash。</span><span class="sxs-lookup"><span data-stu-id="896ea-167">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="896ea-168">`Get-FileHash` 返回一个对象，该对象表示指定文件的路径、计算所得的哈希的值以及用于计算哈希值的算法。</span><span class="sxs-lookup"><span data-stu-id="896ea-168">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="896ea-169">注释</span><span class="sxs-lookup"><span data-stu-id="896ea-169">NOTES</span></span>

## <span data-ttu-id="896ea-170">相关链接</span><span class="sxs-lookup"><span data-stu-id="896ea-170">RELATED LINKS</span></span>

[<span data-ttu-id="896ea-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="896ea-171">Format-List</span></span>](Format-List.md)

