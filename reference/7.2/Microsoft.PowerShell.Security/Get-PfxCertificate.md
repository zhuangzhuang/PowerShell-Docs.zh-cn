---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597866"
---
# <span data-ttu-id="74a87-102">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="74a87-102">Get-PfxCertificate</span></span>

## <span data-ttu-id="74a87-103">摘要</span><span class="sxs-lookup"><span data-stu-id="74a87-103">SYNOPSIS</span></span>
<span data-ttu-id="74a87-104">获取计算机上的 PFX 证书文件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="74a87-104">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="74a87-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74a87-105">SYNTAX</span></span>

### <span data-ttu-id="74a87-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="74a87-106">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="74a87-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="74a87-107">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="74a87-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a87-108">DESCRIPTION</span></span>

<span data-ttu-id="74a87-109">`Get-PfxCertificate`Cmdlet 可获取表示每个指定的 PFX 证书文件的对象。</span><span class="sxs-lookup"><span data-stu-id="74a87-109">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="74a87-110">PFX 文件包括证书和私钥。</span><span class="sxs-lookup"><span data-stu-id="74a87-110">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="74a87-111">示例</span><span class="sxs-lookup"><span data-stu-id="74a87-111">EXAMPLES</span></span>

### <span data-ttu-id="74a87-112">示例1：获取 PFX 证书</span><span class="sxs-lookup"><span data-stu-id="74a87-112">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="74a87-113">此命令获取有关系统上的 Test .pfx 证书文件的信息。</span><span class="sxs-lookup"><span data-stu-id="74a87-113">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="74a87-114">示例2：从远程计算机获取 PFX 证书</span><span class="sxs-lookup"><span data-stu-id="74a87-114">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="74a87-115">此命令从 Server01 远程计算机获取 PFX 证书文件。</span><span class="sxs-lookup"><span data-stu-id="74a87-115">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="74a87-116">它使用 `Invoke-Command` 来远程运行 `Get-PfxCertificate` 命令。</span><span class="sxs-lookup"><span data-stu-id="74a87-116">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="74a87-117">如果 PFX 证书文件不受密码保护，则的 **Authentication** 参数的值 `Invoke-Command` 必须是 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="74a87-117">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="74a87-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74a87-118">PARAMETERS</span></span>

### <span data-ttu-id="74a87-119">-FilePath</span><span class="sxs-lookup"><span data-stu-id="74a87-119">-FilePath</span></span>

<span data-ttu-id="74a87-120">指定受保护文件的 PFX 文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="74a87-120">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="74a87-121">如果指定此参数的值，则不需要在命令行键入 `-FilePath`。</span><span class="sxs-lookup"><span data-stu-id="74a87-121">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="74a87-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74a87-122">-LiteralPath</span></span>

<span data-ttu-id="74a87-123">受保护文件的 PFX 文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="74a87-123">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="74a87-124">与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="74a87-124">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="74a87-125">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="74a87-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="74a87-126">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="74a87-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="74a87-127">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="74a87-127">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="74a87-128">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="74a87-128">-NoPromptForPassword</span></span>

<span data-ttu-id="74a87-129">禁止提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="74a87-129">Suppresses prompting for a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74a87-130">-Password</span><span class="sxs-lookup"><span data-stu-id="74a87-130">-Password</span></span>

<span data-ttu-id="74a87-131">指定访问证书文件所需的密码 `.pfx` 。</span><span class="sxs-lookup"><span data-stu-id="74a87-131">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="74a87-132">此参数是在 PowerShell 6.1 中引入的。</span><span class="sxs-lookup"><span data-stu-id="74a87-132">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="74a87-133">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="74a87-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74a87-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74a87-134">CommonParameters</span></span>

<span data-ttu-id="74a87-135">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="74a87-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74a87-136">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="74a87-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74a87-137">输入</span><span class="sxs-lookup"><span data-stu-id="74a87-137">INPUTS</span></span>

### <span data-ttu-id="74a87-138">System.String</span><span class="sxs-lookup"><span data-stu-id="74a87-138">System.String</span></span>

<span data-ttu-id="74a87-139">可以通过管道将包含文件路径的字符串传递给 `Get-PfxCertificate` 。</span><span class="sxs-lookup"><span data-stu-id="74a87-139">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="74a87-140">输出</span><span class="sxs-lookup"><span data-stu-id="74a87-140">OUTPUTS</span></span>

### <span data-ttu-id="74a87-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="74a87-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="74a87-142">`Get-PfxCertificate` 为获取的每个证书返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="74a87-142">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="74a87-143">注释</span><span class="sxs-lookup"><span data-stu-id="74a87-143">NOTES</span></span>

<span data-ttu-id="74a87-144">使用 `Invoke-Command` cmdlet `Get-PfxCertificate` 远程运行命令时，如果 PFX 证书文件不受密码保护，则的 **Authentication** 参数的值 `Invoke-Command` 必须是 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="74a87-144">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="74a87-145">相关链接</span><span class="sxs-lookup"><span data-stu-id="74a87-145">RELATED LINKS</span></span>

[<span data-ttu-id="74a87-146">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="74a87-146">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="74a87-147">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="74a87-147">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

