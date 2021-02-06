---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 16c61b1fd442eb68c458c3b524a8fc55d5eedcb6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603612"
---
# <span data-ttu-id="34fb4-102">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="34fb4-102">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="34fb4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="34fb4-103">SYNOPSIS</span></span>
<span data-ttu-id="34fb4-104">获取有关文件的 Authenticode 签名的信息。</span><span class="sxs-lookup"><span data-stu-id="34fb4-104">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="34fb4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34fb4-105">SYNTAX</span></span>

### <span data-ttu-id="34fb4-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="34fb4-106">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="34fb4-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="34fb4-107">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="34fb4-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="34fb4-108">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="34fb4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="34fb4-109">DESCRIPTION</span></span>

<span data-ttu-id="34fb4-110">`Get-AuthenticodeSignature`Cmdlet 获取有关作为字节数组的文件或文件内容的 Authenticode 签名信息。</span><span class="sxs-lookup"><span data-stu-id="34fb4-110">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="34fb4-111">如果文件未签名，则将检索信息，但字段为空。</span><span class="sxs-lookup"><span data-stu-id="34fb4-111">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="34fb4-112">示例</span><span class="sxs-lookup"><span data-stu-id="34fb4-112">EXAMPLES</span></span>

### <span data-ttu-id="34fb4-113">示例 1：获取文件的 Authenticode 签名</span><span class="sxs-lookup"><span data-stu-id="34fb4-113">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="34fb4-114">此命令将获取有关 NewScript.ps1 文件中 Authenticode 签名的信息。</span><span class="sxs-lookup"><span data-stu-id="34fb4-114">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="34fb4-115">它使用 **FilePath** 参数指定文件。</span><span class="sxs-lookup"><span data-stu-id="34fb4-115">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="34fb4-116">示例 2：获取多个文件的 Authenticode 签名</span><span class="sxs-lookup"><span data-stu-id="34fb4-116">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="34fb4-117">此命令获取有关命令行中列出的四个文件的 Authenticode 签名的信息。</span><span class="sxs-lookup"><span data-stu-id="34fb4-117">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="34fb4-118">在此示例中，省略了 FilePath 参数（可选）的名称。</span><span class="sxs-lookup"><span data-stu-id="34fb4-118">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="34fb4-119">示例 3：仅获取多个文件的有效 Authenticode 签名</span><span class="sxs-lookup"><span data-stu-id="34fb4-119">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="34fb4-120">此命令列出 `$PSHOME` 目录中具有有效 Authenticode 签名的所有文件。</span><span class="sxs-lookup"><span data-stu-id="34fb4-120">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="34fb4-121">`$PSHOME`自动变量包含 PowerShell 安装目录的路径。</span><span class="sxs-lookup"><span data-stu-id="34fb4-121">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="34fb4-122">该命令使用 `Get-ChildItem` cmdlet 来获取目录中的文件 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="34fb4-122">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="34fb4-123">它使用 *.* 模式</span><span class="sxs-lookup"><span data-stu-id="34fb4-123">It uses a pattern of *.*</span></span> <span data-ttu-id="34fb4-124">来排除目录（尽管它还将排除文件名中没有句点的文件）。</span><span class="sxs-lookup"><span data-stu-id="34fb4-124">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="34fb4-125">该命令使用管道运算符 (`|`) 将文件发送 `$PSHOME` 到 `ForEach-Object` cmdlet，其中 `Get-AuthenticodeSignature` 为每个文件调用。</span><span class="sxs-lookup"><span data-stu-id="34fb4-125">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="34fb4-126">命令的结果 `Get-AuthenticodeSignature` 将发送到一个 `Where-Object` 命令，该命令仅选择状态为 "有效" 的签名对象。</span><span class="sxs-lookup"><span data-stu-id="34fb4-126">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="34fb4-127">示例4：获取指定为字节数组的文件内容的 Authenticode 签名</span><span class="sxs-lookup"><span data-stu-id="34fb4-127">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="34fb4-128">此命令获取有关文件内容的 Authenticode 签名的信息。</span><span class="sxs-lookup"><span data-stu-id="34fb4-128">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="34fb4-129">在此示例中，文件扩展名与文件内容一起指定。</span><span class="sxs-lookup"><span data-stu-id="34fb4-129">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="34fb4-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34fb4-130">PARAMETERS</span></span>

### <span data-ttu-id="34fb4-131">-Content</span><span class="sxs-lookup"><span data-stu-id="34fb4-131">-Content</span></span>

<span data-ttu-id="34fb4-132">文件内容作为要为其检索 Authenticode 签名的字节数组。</span><span class="sxs-lookup"><span data-stu-id="34fb4-132">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="34fb4-133">此参数必须与 **SourcePathOrExtension** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="34fb4-133">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="34fb4-134">文件的内容必须采用 Unicode 格式 (UTF-16LE) 格式。</span><span class="sxs-lookup"><span data-stu-id="34fb4-134">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="34fb4-135">-FilePath</span><span class="sxs-lookup"><span data-stu-id="34fb4-135">-FilePath</span></span>

<span data-ttu-id="34fb4-136">指定要检查的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="34fb4-136">Specifies the path to the file to examine.</span></span> <span data-ttu-id="34fb4-137">允许使用通配符，但它们必须指向单个文件。</span><span class="sxs-lookup"><span data-stu-id="34fb4-137">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="34fb4-138">为此参数指定值时，无需在命令行中键入 **FilePath** 。</span><span class="sxs-lookup"><span data-stu-id="34fb4-138">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="34fb4-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34fb4-139">-LiteralPath</span></span>

<span data-ttu-id="34fb4-140">指定要检查的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="34fb4-140">Specifies the path to the file being examined.</span></span> <span data-ttu-id="34fb4-141">与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="34fb4-141">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="34fb4-142">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="34fb4-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="34fb4-143">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="34fb4-143">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="34fb4-144">单引号告诉 PowerShell 不要将任何字符解释为转义符。</span><span class="sxs-lookup"><span data-stu-id="34fb4-144">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="34fb4-145">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="34fb4-145">-SourcePathOrExtension</span></span>

<span data-ttu-id="34fb4-146">要为其检索 Authenticode 签名的内容的文件或文件类型的路径。</span><span class="sxs-lookup"><span data-stu-id="34fb4-146">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="34fb4-147">此参数用于将文件内容作为字节数组传递的 **内容** 。</span><span class="sxs-lookup"><span data-stu-id="34fb4-147">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="34fb4-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34fb4-148">CommonParameters</span></span>

<span data-ttu-id="34fb4-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="34fb4-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34fb4-150">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="34fb4-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="34fb4-151">输入</span><span class="sxs-lookup"><span data-stu-id="34fb4-151">INPUTS</span></span>

### <span data-ttu-id="34fb4-152">System.String</span><span class="sxs-lookup"><span data-stu-id="34fb4-152">System.String</span></span>

<span data-ttu-id="34fb4-153">可以通过管道将包含文件路径的字符串传递给 `Get-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="34fb4-153">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="34fb4-154">输出</span><span class="sxs-lookup"><span data-stu-id="34fb4-154">OUTPUTS</span></span>

### <span data-ttu-id="34fb4-155">System.Management.Automation.Signature</span><span class="sxs-lookup"><span data-stu-id="34fb4-155">System.Management.Automation.Signature</span></span>

<span data-ttu-id="34fb4-156">`Get-AuthenticodeSignature` 为获取的每个签名返回一个签名对象。</span><span class="sxs-lookup"><span data-stu-id="34fb4-156">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="34fb4-157">注释</span><span class="sxs-lookup"><span data-stu-id="34fb4-157">NOTES</span></span>

<span data-ttu-id="34fb4-158">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="34fb4-158">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="34fb4-159">有关 PowerShell 中 Authenticode 签名的信息，请参阅 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="34fb4-159">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="34fb4-160">相关链接</span><span class="sxs-lookup"><span data-stu-id="34fb4-160">RELATED LINKS</span></span>

[<span data-ttu-id="34fb4-161">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="34fb4-161">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="34fb4-162">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="34fb4-162">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="34fb4-163">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="34fb4-163">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="34fb4-164">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="34fb4-164">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="34fb4-165">about_Signing</span><span class="sxs-lookup"><span data-stu-id="34fb4-165">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
