---
description: 描述 PowerShell 如何使用字符串数据的输入和输出的字符编码。
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 3b47a528b0beae5e8142157454cbc676ffd7e795
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "99597466"
---
# <a name="about_character_encoding"></a><span data-ttu-id="64017-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="64017-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="64017-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="64017-104">Short description</span></span>
<span data-ttu-id="64017-105">描述 PowerShell 如何使用字符串数据的输入和输出的字符编码。</span><span class="sxs-lookup"><span data-stu-id="64017-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="64017-106">长说明</span><span class="sxs-lookup"><span data-stu-id="64017-106">Long description</span></span>

<span data-ttu-id="64017-107">Unicode 是一种全球字符编码标准。</span><span class="sxs-lookup"><span data-stu-id="64017-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="64017-108">系统仅将 Unicode 用于字符和字符串操作。</span><span class="sxs-lookup"><span data-stu-id="64017-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="64017-109">有关 Unicode 的所有方面的详细说明，请参阅 [Unicode 标准](https://www.unicode.org/standard/standard.html)。</span><span class="sxs-lookup"><span data-stu-id="64017-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="64017-110">Windows 支持 Unicode 和传统字符集。</span><span class="sxs-lookup"><span data-stu-id="64017-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="64017-111">传统字符集（如 Windows 代码页）使用8位值或8位值的组合来表示特定语言或地理区域设置中使用的字符。</span><span class="sxs-lookup"><span data-stu-id="64017-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="64017-112">默认情况下，PowerShell 使用 Unicode 字符集。</span><span class="sxs-lookup"><span data-stu-id="64017-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="64017-113">但是，有几个 cmdlet 具有可为不同字符集指定编码的 **编码** 参数。</span><span class="sxs-lookup"><span data-stu-id="64017-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="64017-114">此参数允许你选择与其他系统和应用程序的互操作性所需的特定字符编码。</span><span class="sxs-lookup"><span data-stu-id="64017-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="64017-115">以下 cmdlet 具有 **Encoding** 参数：</span><span class="sxs-lookup"><span data-stu-id="64017-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="64017-116">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="64017-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="64017-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="64017-117">Add-Content</span></span>
  - <span data-ttu-id="64017-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="64017-118">Get-Content</span></span>
  - <span data-ttu-id="64017-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="64017-119">Set-Content</span></span>
- <span data-ttu-id="64017-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="64017-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="64017-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="64017-121">Export-Clixml</span></span>
  - <span data-ttu-id="64017-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="64017-122">Export-Csv</span></span>
  - <span data-ttu-id="64017-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="64017-123">Export-PSSession</span></span>
  - <span data-ttu-id="64017-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="64017-124">Format-Hex</span></span>
  - <span data-ttu-id="64017-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="64017-125">Import-Csv</span></span>
  - <span data-ttu-id="64017-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="64017-126">Out-File</span></span>
  - <span data-ttu-id="64017-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="64017-127">Select-String</span></span>
  - <span data-ttu-id="64017-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="64017-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="64017-129">字节顺序标记</span><span class="sxs-lookup"><span data-stu-id="64017-129">The byte-order-mark</span></span>

<span data-ttu-id="64017-130">字节顺序标记 (BOM) 是文件或文本流的前几个字节中的 _Unicode 签名_ ，指示用于数据的 unicode 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="64017-131">有关详细信息，请参阅 [字节顺序标记](/globalization/encoding/byte-order-mark) 文档。</span><span class="sxs-lookup"><span data-stu-id="64017-131">For more information, see the [Byte order mark](/globalization/encoding/byte-order-mark) documentation.</span></span>

<span data-ttu-id="64017-132">在 Windows PowerShell 中，除之外的任何 Unicode 编码 `UTF7` 都将始终创建 BOM。</span><span class="sxs-lookup"><span data-stu-id="64017-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="64017-133">所有文本输出的 PowerShell Core 默认值为 `utf8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="64017-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="64017-134">为了获得最佳的整体兼容性，请避免在 UTF-8 文件中使用 Bom。</span><span class="sxs-lookup"><span data-stu-id="64017-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="64017-135">在 Windows 平台上还使用的 unix 平台和 Unix 的遗产保护实用工具不支持 Bom。</span><span class="sxs-lookup"><span data-stu-id="64017-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="64017-136">同样， `UTF7` 应避免编码。</span><span class="sxs-lookup"><span data-stu-id="64017-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="64017-137">UTF-7 不是标准的 Unicode 编码，并且在所有版本的 PowerShell 中都不使用 BOM 来编写。</span><span class="sxs-lookup"><span data-stu-id="64017-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="64017-138">在类似于 Unix 的平台上或在 Windows 上使用跨平台编辑器（如 Visual Studio Code）创建 PowerShell 脚本会导致使用对文件进行编码 `UTF8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="64017-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="64017-139">这些文件在 PowerShell Core 上运行正常，但如果文件包含非 Ascii 字符，则可能会在 Windows PowerShell 中中断。</span><span class="sxs-lookup"><span data-stu-id="64017-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="64017-140">如果需要在脚本中使用非 Ascii 字符，请使用 BOM 将它们另存为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="64017-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="64017-141">如果没有 BOM，Windows PowerShell 会将脚本 misinterprets 为在旧的 "ANSI" 代码页中编码。</span><span class="sxs-lookup"><span data-stu-id="64017-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="64017-142">相反，具有 UTF-8 BOM 的文件在类似 Unix 的平台上可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="64017-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="64017-143">许多 Unix 工具（如 `cat` 、 `sed` 、 `awk` 和一些编辑器）（如 `gedit` 不知道如何处理 BOM）。</span><span class="sxs-lookup"><span data-stu-id="64017-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="64017-144">Windows PowerShell 中的字符编码</span><span class="sxs-lookup"><span data-stu-id="64017-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="64017-145">在 PowerShell 5.1 中， **Encoding** 参数支持以下值：</span><span class="sxs-lookup"><span data-stu-id="64017-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="64017-146">`Ascii` 使用 Ascii (7 位) 字符集。</span><span class="sxs-lookup"><span data-stu-id="64017-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="64017-147">`BigEndianUnicode` 使用带有大 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="64017-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="64017-148">`BigEndianUTF32` 使用带有大字节序字节顺序的 32 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="64017-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="64017-149">`Byte` 将一组字符编码为一个字节序列。</span><span class="sxs-lookup"><span data-stu-id="64017-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="64017-150">`Default` 使用与系统的活动代码页相对应的编码 (通常为 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="64017-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="64017-151">`Oem` 使用与系统的当前 OEM 代码页相对应的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="64017-152">`String` 与 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="64017-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="64017-153">`Unicode` 使用带有小 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="64017-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="64017-154">`Unknown` 与 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="64017-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="64017-155">`UTF32` 使用带有小 endian 字节顺序的 32 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="64017-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="64017-156">`UTF7` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="64017-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="64017-157">`UTF8` 对 BOM) 使用 UTF-8 (。</span><span class="sxs-lookup"><span data-stu-id="64017-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="64017-158">通常，默认情况下，Windows PowerShell 使用 Unicode [utf-16le](https://wikipedia.org/wiki/UTF-16) 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="64017-159">但是，Windows PowerShell 中的 cmdlet 使用的默认编码是不一致的。</span><span class="sxs-lookup"><span data-stu-id="64017-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="64017-160">使用除之外的任何 Unicode 编码 `UTF7` 都将始终创建 BOM。</span><span class="sxs-lookup"><span data-stu-id="64017-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="64017-161">对于将输出写入文件的 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="64017-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="64017-162">`Out-File` 和重定向运算符， `>` 并 `>>` 创建 utf-16le，这一点与和不同 `Set-Content` `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="64017-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="64017-163">`New-ModuleManifest``Export-CliXml`还会创建 utf-16le 文件。</span><span class="sxs-lookup"><span data-stu-id="64017-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="64017-164">当目标文件为空或不存在时， `Set-Content` `Add-Content` 使用 `Default` 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="64017-165">`Default` 是由活动系统区域设置的 ANSI 旧版代码页指定的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="64017-166">`Export-Csv` 创建 `Ascii` 文件，但使用 **追加** 参数时使用不同的编码 (参见下面的) 。</span><span class="sxs-lookup"><span data-stu-id="64017-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="64017-167">`Export-PSSession` 默认情况下，使用 BOM 创建 UTF-8 文件。</span><span class="sxs-lookup"><span data-stu-id="64017-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="64017-168">`New-Item -Type File -Value` 创建不带 BOM 的 UTF-8 文件。</span><span class="sxs-lookup"><span data-stu-id="64017-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="64017-169">`Send-MailMessage``Default`默认情况下使用编码。</span><span class="sxs-lookup"><span data-stu-id="64017-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="64017-170">`Start-Transcript``Utf8`使用 BOM 创建文件。</span><span class="sxs-lookup"><span data-stu-id="64017-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="64017-171">使用 **Append** 参数时，编码可能不同 (参见下面) 。</span><span class="sxs-lookup"><span data-stu-id="64017-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="64017-172">对于追加到现有文件的命令：</span><span class="sxs-lookup"><span data-stu-id="64017-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="64017-173">`Out-File -Append``>>`重定向运算符不会尝试匹配现有目标文件内容的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="64017-174">相反，它们使用默认编码，除非使用 **编码** 参数。</span><span class="sxs-lookup"><span data-stu-id="64017-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="64017-175">追加内容时，必须使用原始编码文件。</span><span class="sxs-lookup"><span data-stu-id="64017-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="64017-176">如果没有显式 **编码** 参数，将检测到 `Add-Content` 现有编码，并将其自动应用于新内容。</span><span class="sxs-lookup"><span data-stu-id="64017-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="64017-177">如果现有内容没有 BOM， `Default` 则使用 ANSI 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="64017-178">`Add-Content`在 PowerShell Core (v6 和更高) 版本中，的行为相同，不同之处在于默认编码为 `Utf8` 。</span><span class="sxs-lookup"><span data-stu-id="64017-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="64017-179">`Export-Csv -Append` 当目标文件包含 BOM 时，匹配现有编码。</span><span class="sxs-lookup"><span data-stu-id="64017-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="64017-180">如果没有 BOM，则使用 `Utf8` 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="64017-181">`Start-Transcript -Append` 匹配包含 BOM 的文件的现有编码。</span><span class="sxs-lookup"><span data-stu-id="64017-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="64017-182">如果没有 BOM，则默认为 `Ascii` 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="64017-183">当脚本中的数据包含多字节字符时，此编码可能会导致数据丢失或字符损坏。</span><span class="sxs-lookup"><span data-stu-id="64017-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="64017-184">对于读取缺少 BOM 的字符串数据的 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="64017-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="64017-185">`Get-Content` 和 `Import-PowerShellDataFile` 使用 `Default` ANSI 编码。</span><span class="sxs-lookup"><span data-stu-id="64017-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="64017-186">在从文件读取源代码时，它也是 PowerShell 引擎使用的内容。</span><span class="sxs-lookup"><span data-stu-id="64017-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="64017-187">`Import-Csv`、 `Import-CliXml` 和 `Select-String` 假设 `Utf8` 缺少 BOM。</span><span class="sxs-lookup"><span data-stu-id="64017-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="64017-188">PowerShell Core 中的字符编码</span><span class="sxs-lookup"><span data-stu-id="64017-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="64017-189">在 PowerShell Core (v6 和更高版本中) ， **Encoding** 参数支持以下值：</span><span class="sxs-lookup"><span data-stu-id="64017-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="64017-190">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="64017-191">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="64017-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="64017-192">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="64017-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="64017-193">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="64017-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="64017-194">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="64017-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="64017-195">`utf8`：以 UTF-8 格式编码 (不) BOM。</span><span class="sxs-lookup"><span data-stu-id="64017-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="64017-196">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="64017-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="64017-197">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="64017-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="64017-198">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="64017-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="64017-199">对于所有输出，PowerShell Core 默认值为 `utf8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="64017-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="64017-200">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="64017-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="64017-201">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage)</span><span class="sxs-lookup"><span data-stu-id="64017-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="64017-202">更改默认编码</span><span class="sxs-lookup"><span data-stu-id="64017-202">Changing the default encoding</span></span>

<span data-ttu-id="64017-203">PowerShell 具有两个可用于更改默认编码行为的默认变量。</span><span class="sxs-lookup"><span data-stu-id="64017-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="64017-204">有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="64017-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="64017-205">从 PowerShell 5.1 开始，重定向操作员 (`>` 和 `>>`) 调用 `Out-File` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64017-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="64017-206">因此，你可以使用首选项变量设置其默认编码， `$PSDefaultParameterValues` 如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="64017-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="64017-207">使用以下语句来更改具有 **encoding** 参数的所有 cmdlet 的默认编码。</span><span class="sxs-lookup"><span data-stu-id="64017-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="64017-208">在 PowerShell 配置文件中放置此命令可使首选项成为会话全局设置，该设置会影响未显式指定编码的所有命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="64017-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="64017-209">同样，你应该将此类命令包含在你希望以相同方式运行的脚本或模块中。</span><span class="sxs-lookup"><span data-stu-id="64017-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="64017-210">使用这些命令可确保 cmdlet 的行为方式与其他用户在其他计算机上运行或在不同版本的 PowerShell 中运行时的行为相同。</span><span class="sxs-lookup"><span data-stu-id="64017-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="64017-211">自动变量 `$OutputEncoding` 会影响 PowerShell 用于与外部程序通信的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="64017-212">它不会影响输出重定向运算符和 PowerShell cmdlet 用于保存到文件的编码。</span><span class="sxs-lookup"><span data-stu-id="64017-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="64017-213">请参阅</span><span class="sxs-lookup"><span data-stu-id="64017-213">See also</span></span>

- [<span data-ttu-id="64017-214">.NET 中的字符编码简介</span><span class="sxs-lookup"><span data-stu-id="64017-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="64017-215">代码页-Win32 应用</span><span class="sxs-lookup"><span data-stu-id="64017-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="64017-216">Unicode 标准</span><span class="sxs-lookup"><span data-stu-id="64017-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="64017-217">编码。代码页</span><span class="sxs-lookup"><span data-stu-id="64017-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="64017-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="64017-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="64017-219">字节顺序标记</span><span class="sxs-lookup"><span data-stu-id="64017-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="64017-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="64017-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)
