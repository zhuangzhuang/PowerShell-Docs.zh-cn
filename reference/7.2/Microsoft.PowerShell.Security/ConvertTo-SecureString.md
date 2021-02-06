---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 0f95f66bdd13fd57f71823f2d44a28a1323d0d15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597440"
---
# <span data-ttu-id="f0043-102">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="f0043-102">ConvertTo-SecureString</span></span>

## <span data-ttu-id="f0043-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f0043-103">SYNOPSIS</span></span>
<span data-ttu-id="f0043-104">将纯文本或加密字符串转换为安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-104">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="f0043-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0043-105">SYNTAX</span></span>

### <span data-ttu-id="f0043-106">Secure（默认值）</span><span class="sxs-lookup"><span data-stu-id="f0043-106">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="f0043-107">PlainText</span><span class="sxs-lookup"><span data-stu-id="f0043-107">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="f0043-108">打开</span><span class="sxs-lookup"><span data-stu-id="f0043-108">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="f0043-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f0043-109">DESCRIPTION</span></span>

<span data-ttu-id="f0043-110">`ConvertTo-SecureString`Cmdlet 将加密的标准字符串转换为安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-110">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="f0043-111">它还可以将纯文本转换为安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-111">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="f0043-112">它与和一起 `ConvertFrom-SecureString` 使用 `Read-Host` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-112">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="f0043-113">Cmdlet 创建的安全字符串可与需要类型为 **SecureString** 的参数的 cmdlet 或函数一起使用。</span><span class="sxs-lookup"><span data-stu-id="f0043-113">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="f0043-114">安全字符串可以使用 cmdlet 转换回加密的标准字符串 `ConvertFrom-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-114">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="f0043-115">这使它能够存储在文件中以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="f0043-115">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="f0043-116">如果使用指定的密钥对要转换的标准字符串进行了加密 `ConvertFrom-SecureString` ，则必须将同一密钥作为 cmdlet 的 **Key** 或 **SecureKey** 参数的值提供 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-116">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f0043-117">请注意，在非 Windows 系统上，每个 [DotNet](/dotnet/api/system.security.securestring#remarks)不会加密 SecureString 的内容。</span><span class="sxs-lookup"><span data-stu-id="f0043-117">Note that per [DotNet](/dotnet/api/system.security.securestring#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="f0043-118">示例</span><span class="sxs-lookup"><span data-stu-id="f0043-118">EXAMPLES</span></span>

### <span data-ttu-id="f0043-119">示例1：将安全字符串转换为加密字符串</span><span class="sxs-lookup"><span data-stu-id="f0043-119">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="f0043-120">此示例显示了从用户输入创建安全字符串、将安全字符串转换为加密的标准字符串，然后将加密的标准字符串重新转换为安全字符串的方式。</span><span class="sxs-lookup"><span data-stu-id="f0043-120">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="f0043-121">第一个命令使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 创建安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-121">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="f0043-122">输入该命令后，你键入的任何字符都将转换为安全字符串，然后保存在变量中 `$Secure` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-122">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="f0043-123">第二个命令显示变量的内容 `$Secure` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-123">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="f0043-124">由于 `$Secure` 变量包含安全字符串，因此 PowerShell 仅显示 **SecureString** 类型。</span><span class="sxs-lookup"><span data-stu-id="f0043-124">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="f0043-125">第三个命令使用 `ConvertFrom-SecureString` cmdlet 将变量中的安全字符串转换为 `$Secure` 加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-125">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="f0043-126">它将结果保存在 `$Encrypted` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f0043-126">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="f0043-127">第四个命令显示变量值中的加密字符串 `$Encrypted` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-127">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="f0043-128">第五个命令使用 `ConvertTo-SecureString` cmdlet 将变量中的加密的标准字符串转换 `$Encrypted` 回安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-128">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="f0043-129">它将结果保存在 `$Secure2` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f0043-129">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="f0043-130">第六个命令显示变量的值 `$Secure2` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-130">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="f0043-131">SecureString 类型指示命令已成功。</span><span class="sxs-lookup"><span data-stu-id="f0043-131">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="f0043-132">示例2：从文件中的加密字符串创建安全字符串</span><span class="sxs-lookup"><span data-stu-id="f0043-132">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="f0043-133">此示例显示了如何从保存在文件中的加密的标准字符串中创建安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-133">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="f0043-134">第一个命令使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 创建安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-134">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="f0043-135">输入该命令后，你键入的任何字符都将转换为安全字符串，然后保存在变量中 `$Secure` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-135">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="f0043-136">第二个命令使用 `ConvertFrom-SecureString` cmdlet，通过使用指定的键将变量中的安全字符串转换为 `$Secure` 加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-136">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="f0043-137">内容保存在 `$Encrypted` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f0043-137">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="f0043-138">第三个命令使用管道运算符 (`|`) 将变量的值发送 `$Encrypted` 到 `Set-Content` cmdlet，这会将值保存在 Encrypted.txt 文件中。</span><span class="sxs-lookup"><span data-stu-id="f0043-138">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="f0043-139">第四个命令使用 `Get-Content` cmdlet 来获取 Encrypted.txt 文件中的加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-139">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="f0043-140">该命令使用管道运算符将加密字符串发送到 `ConvertTo-SecureString` cmdlet，该 cmdlet 使用指定的密钥将其转换为安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-140">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="f0043-141">结果保存在 `$Secure2` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f0043-141">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="f0043-142">示例3：将纯文本字符串转换为安全字符串</span><span class="sxs-lookup"><span data-stu-id="f0043-142">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="f0043-143">此命令将纯文本字符串转换为 `P@ssW0rD!` 安全字符串，并将结果存储在 `$Secure_String_Pwd` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f0043-143">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="f0043-144">若要使用 **AsPlainText** 参数，还必须将 **Force** 参数包含在该命令中。</span><span class="sxs-lookup"><span data-stu-id="f0043-144">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="f0043-145">应避免在脚本或命令行中使用纯文本字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-145">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="f0043-146">纯文本可以显示在事件日志和命令历史记录日志中。</span><span class="sxs-lookup"><span data-stu-id="f0043-146">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="f0043-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0043-147">PARAMETERS</span></span>

### <span data-ttu-id="f0043-148">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="f0043-148">-AsPlainText</span></span>

<span data-ttu-id="f0043-149">指定要转换为安全字符串的纯文本字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-149">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="f0043-150">安全字符串 cmdlet 有助于保护机密文本。</span><span class="sxs-lookup"><span data-stu-id="f0043-150">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="f0043-151">为保护隐私，应对文本进行加密，并在使用后将其从计算机内存中删除。</span><span class="sxs-lookup"><span data-stu-id="f0043-151">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="f0043-152">如果你使用此参数来提供纯文本作为输入，则系统无法采用此方式保护该输入。</span><span class="sxs-lookup"><span data-stu-id="f0043-152">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="f0043-153">若要使用此参数，还必须指定 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="f0043-153">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0043-154">-Force</span><span class="sxs-lookup"><span data-stu-id="f0043-154">-Force</span></span>

<span data-ttu-id="f0043-155">确认你了解使用 **AsPlainText** 参数的含义并仍要使用它。</span><span class="sxs-lookup"><span data-stu-id="f0043-155">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0043-156">-Key</span><span class="sxs-lookup"><span data-stu-id="f0043-156">-Key</span></span>

<span data-ttu-id="f0043-157">指定用于将原始安全字符串转换为加密的标准字符串的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="f0043-157">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="f0043-158">有效的密钥长度为16、24和32字节。</span><span class="sxs-lookup"><span data-stu-id="f0043-158">Valid key lengths are 16, 24 and 32 bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0043-159">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="f0043-159">-SecureKey</span></span>

<span data-ttu-id="f0043-160">指定用于将原始安全字符串转换为加密的标准字符串的加密密钥。</span><span class="sxs-lookup"><span data-stu-id="f0043-160">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="f0043-161">必须采用安全字符串的格式提供密钥。</span><span class="sxs-lookup"><span data-stu-id="f0043-161">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="f0043-162">安全字符串将转换为字节数组，以用作键。</span><span class="sxs-lookup"><span data-stu-id="f0043-162">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="f0043-163">有效的安全密钥长度为8、12和16个码位。</span><span class="sxs-lookup"><span data-stu-id="f0043-163">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0043-164">-String</span><span class="sxs-lookup"><span data-stu-id="f0043-164">-String</span></span>

<span data-ttu-id="f0043-165">指定要转换为安全字符串的字符串。</span><span class="sxs-lookup"><span data-stu-id="f0043-165">Specifies the string to convert to a secure string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f0043-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0043-166">CommonParameters</span></span>

<span data-ttu-id="f0043-167">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f0043-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0043-168">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f0043-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0043-169">输入</span><span class="sxs-lookup"><span data-stu-id="f0043-169">INPUTS</span></span>

### <span data-ttu-id="f0043-170">System.String</span><span class="sxs-lookup"><span data-stu-id="f0043-170">System.String</span></span>

<span data-ttu-id="f0043-171">可以通过管道将标准加密字符串传递给 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="f0043-171">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="f0043-172">输出</span><span class="sxs-lookup"><span data-stu-id="f0043-172">OUTPUTS</span></span>

### <span data-ttu-id="f0043-173">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="f0043-173">System.Security.SecureString</span></span>

<span data-ttu-id="f0043-174">`ConvertTo-SecureString` 返回 **SecureString** 对象。</span><span class="sxs-lookup"><span data-stu-id="f0043-174">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="f0043-175">注释</span><span class="sxs-lookup"><span data-stu-id="f0043-175">NOTES</span></span>

<span data-ttu-id="f0043-176">一些字符（如图释）对应于包含它们的字符串中的几个码位。</span><span class="sxs-lookup"><span data-stu-id="f0043-176">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="f0043-177">避免使用这些字符，因为在密码中使用时，它们可能会导致问题和误解。</span><span class="sxs-lookup"><span data-stu-id="f0043-177">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="f0043-178">相关链接</span><span class="sxs-lookup"><span data-stu-id="f0043-178">RELATED LINKS</span></span>

[<span data-ttu-id="f0043-179">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="f0043-179">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="f0043-180">Read-Host</span><span class="sxs-lookup"><span data-stu-id="f0043-180">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
