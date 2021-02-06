---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 70ef5033c3c5d37ed00a88abfb0d1353f5d10854
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "99598687"
---
# <span data-ttu-id="6e257-102">Add-Content</span><span class="sxs-lookup"><span data-stu-id="6e257-102">Add-Content</span></span>

## <span data-ttu-id="6e257-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6e257-103">SYNOPSIS</span></span>
<span data-ttu-id="6e257-104">向指定的项中添加内容，如向文件中添加字词。</span><span class="sxs-lookup"><span data-stu-id="6e257-104">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="6e257-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6e257-105">SYNTAX</span></span>

### <span data-ttu-id="6e257-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="6e257-106">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="6e257-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6e257-107">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="6e257-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6e257-108">DESCRIPTION</span></span>

<span data-ttu-id="6e257-109">`Add-Content`Cmdlet 将内容追加到指定项或文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-109">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="6e257-110">可以通过在命令中键入内容或通过指定包含内容的对象来指定内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-110">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="6e257-111">如果需要为以下示例创建文件或目录，请参阅 " [新建项](New-Item.md)"。</span><span class="sxs-lookup"><span data-stu-id="6e257-111">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="6e257-112">示例</span><span class="sxs-lookup"><span data-stu-id="6e257-112">EXAMPLES</span></span>

### <span data-ttu-id="6e257-113">示例1：向所有文本文件添加字符串，但出现异常</span><span class="sxs-lookup"><span data-stu-id="6e257-113">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="6e257-114">此示例将一个值附加到当前目录中的文本文件，但基于文件的文件名排除文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-114">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="6e257-115">**Path** 参数指定 `.txt` 当前目录中的所有文件，但 **Exclude** 参数将忽略与指定模式匹配的文件名。</span><span class="sxs-lookup"><span data-stu-id="6e257-115">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="6e257-116">**值** 参数指定写入文件的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="6e257-116">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="6e257-117">示例2：将日期添加到指定文件的末尾</span><span class="sxs-lookup"><span data-stu-id="6e257-117">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="6e257-118">此示例将日期附加到当前目录中的文件，并在 PowerShell 控制台中显示日期。</span><span class="sxs-lookup"><span data-stu-id="6e257-118">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="6e257-119">`Add-Content`Cmdlet 将在当前目录中创建两个新文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-119">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="6e257-120">**Value** 参数包含 cmdlet 的输出 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-120">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="6e257-121">**PassThru** 参数将添加的内容输出到管道。</span><span class="sxs-lookup"><span data-stu-id="6e257-121">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="6e257-122">由于没有其他 cmdlet 接收输出，因此它显示在 PowerShell 控制台中。</span><span class="sxs-lookup"><span data-stu-id="6e257-122">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="6e257-123">`Get-Content`Cmdlet 将显示更新后的文件 `DateTimeFile1.log` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-123">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="6e257-124">示例3：将指定文件的内容添加到另一个文件</span><span class="sxs-lookup"><span data-stu-id="6e257-124">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="6e257-125">此示例从文件中获取内容，并将内容存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="6e257-125">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="6e257-126">变量用于将内容追加到另一个文件中。</span><span class="sxs-lookup"><span data-stu-id="6e257-126">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="6e257-127">`Get-Content`Cmdlet 将获取的内容 `CopyFromFile.txt` ，并将内容存储在 `$From` 变量中。</span><span class="sxs-lookup"><span data-stu-id="6e257-127">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="6e257-128">`Add-Content`Cmdlet `CopyToFile.txt` 使用变量的内容更新文件 `$From` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-128">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="6e257-129">`Get-Content`Cmdlet 将显示 CopyToFile.txt。</span><span class="sxs-lookup"><span data-stu-id="6e257-129">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="6e257-130">示例4：使用管道将指定文件的内容添加到另一个文件</span><span class="sxs-lookup"><span data-stu-id="6e257-130">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="6e257-131">此示例从文件中获取内容并将其传递给 `Add-Content` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e257-131">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="6e257-132">`Get-Content`Cmdlet 将获取的内容 `CopyFromFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-132">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="6e257-133">结果将通过管道传递给 `Add-Content` cmdlet，后者会更新 `CopyToFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-133">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="6e257-134">最后一个 `Get-Content` cmdlet 显示 `CopyToFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-134">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="6e257-135">示例5：创建新文件并复制内容</span><span class="sxs-lookup"><span data-stu-id="6e257-135">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="6e257-136">此示例将创建一个新文件，并将现有文件的内容复制到新文件中。</span><span class="sxs-lookup"><span data-stu-id="6e257-136">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="6e257-137">`Add-Content`Cmdlet 使用 **Path** 和 **Value** 参数在当前目录中创建一个新文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-137">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="6e257-138">该 `Get-Content` cmdlet 将获取现有文件的内容， `CopyFromFile.txt` 并将其传递给 **Value** 参数。</span><span class="sxs-lookup"><span data-stu-id="6e257-138">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="6e257-139">Cmdlet 两边的括号 `Get-Content` 可确保命令在命令开始前完成 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-139">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="6e257-140">`Get-Content`Cmdlet 将显示新文件的内容 `NewFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-140">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="6e257-141">示例6：向只读文件中添加内容</span><span class="sxs-lookup"><span data-stu-id="6e257-141">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="6e257-142">即使 **IsReadOnly** 文件属性设置为 **True**，此命令也会向该文件添加一个值。</span><span class="sxs-lookup"><span data-stu-id="6e257-142">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True**.</span></span>
<span data-ttu-id="6e257-143">示例中包含创建只读文件的步骤。</span><span class="sxs-lookup"><span data-stu-id="6e257-143">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="6e257-144">`New-Item`Cmdlet 使用 **Path** 和 **ItemType** 参数 `IsReadOnlyTextFile.txt` 在当前目录中创建文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-144">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="6e257-145">`Set-ItemProperty`Cmdlet 使用 **Name** 和 **Value** 参数将文件的 **IsReadOnly** 属性更改为 True。</span><span class="sxs-lookup"><span data-stu-id="6e257-145">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="6e257-146">该 `Get-ChildItem` cmdlet 显示文件为空 (0) 并且 () 具有只读属性 `r` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-146">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="6e257-147">`Add-Content`Cmdlet 使用 **Path** 参数指定文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-147">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="6e257-148">**Value** 参数包含要追加到文件中的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="6e257-148">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="6e257-149">**Force** 参数将文本写入只读文件。</span><span class="sxs-lookup"><span data-stu-id="6e257-149">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="6e257-150">`Get-Content`Cmdlet 使用 **Path** 参数显示文件的内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-150">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="6e257-151">若要删除只读属性，请使用命令， `Set-ItemProperty` 并将 **Value** 参数设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-151">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="6e257-152">示例7：使用筛选器与 Add-Content</span><span class="sxs-lookup"><span data-stu-id="6e257-152">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="6e257-153">可以为 cmdlet 指定筛选器 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-153">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="6e257-154">使用筛选器限定 **路径** 参数时，需要包含一个尾随星号 (`*`) ，以指示路径的内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-154">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="6e257-155">以下命令将目录中所有文件的内容添加到 "完成" 一词 `*.txt` `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-155">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="6e257-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e257-156">PARAMETERS</span></span>

### <span data-ttu-id="6e257-157">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="6e257-157">-AsByteStream</span></span>

<span data-ttu-id="6e257-158">指定应以字节流的形式读取内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-158">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="6e257-159">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="6e257-159">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="6e257-160">将 **AsByteStream** 参数与 **Encoding** 参数一起使用时，将出现警告。</span><span class="sxs-lookup"><span data-stu-id="6e257-160">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="6e257-161">**AsByteStream** 参数将忽略任何编码，并以字节流的形式返回输出。</span><span class="sxs-lookup"><span data-stu-id="6e257-161">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="6e257-162">-Credential</span><span class="sxs-lookup"><span data-stu-id="6e257-162">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="6e257-163">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="6e257-163">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="6e257-164">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="6e257-164">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e257-165">-Encoding</span><span class="sxs-lookup"><span data-stu-id="6e257-165">-Encoding</span></span>

<span data-ttu-id="6e257-166">指定目标文件的编码类型。</span><span class="sxs-lookup"><span data-stu-id="6e257-166">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="6e257-167">默认值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="6e257-167">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="6e257-168">Encoding 是 FileSystem 提供程序添加到 cmdlet 的动态参数 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-168">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="6e257-169">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="6e257-169">This parameter works only in file system drives.</span></span>

<span data-ttu-id="6e257-170">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="6e257-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="6e257-171">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-171">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="6e257-172">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-172">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6e257-173">`bigendianutf32`：使用大字节序字节顺序编码为32格式。</span><span class="sxs-lookup"><span data-stu-id="6e257-173">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6e257-174">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="6e257-175">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="6e257-176">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="6e257-177">`utf8`：以 UTF-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="6e257-178">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="6e257-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6e257-179">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="6e257-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6e257-180">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="6e257-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="6e257-181">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="6e257-182">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)</span><span class="sxs-lookup"><span data-stu-id="6e257-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="6e257-183">不建议使用 **utf-7** _ _。</span><span class="sxs-lookup"><span data-stu-id="6e257-183">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="6e257-184">在 PowerShell 7.1 中，如果 `utf7` 为 _ *Encoding*\* 参数指定，则会写入警告。</span><span class="sxs-lookup"><span data-stu-id="6e257-184">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e257-185">-Exclude</span><span class="sxs-lookup"><span data-stu-id="6e257-185">-Exclude</span></span>

<span data-ttu-id="6e257-186">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="6e257-186">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="6e257-187">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="6e257-187">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6e257-188">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="6e257-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="6e257-189">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6e257-189">Wildcard characters are permitted.</span></span> <span data-ttu-id="6e257-190">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-190">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6e257-191">-Filter</span><span class="sxs-lookup"><span data-stu-id="6e257-191">-Filter</span></span>

<span data-ttu-id="6e257-192">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="6e257-192">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="6e257-193">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6e257-193">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="6e257-194">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="6e257-194">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="6e257-195">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="6e257-195">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6e257-196">-Force</span><span class="sxs-lookup"><span data-stu-id="6e257-196">-Force</span></span>

<span data-ttu-id="6e257-197">覆盖只读属性，从而允许你向只读文件中添加内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-197">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="6e257-198">例如，**Force** 将覆盖只读属性或创建目录来完成文件路径，但它不会尝试更改文件权限。</span><span class="sxs-lookup"><span data-stu-id="6e257-198">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="6e257-199">-Include</span><span class="sxs-lookup"><span data-stu-id="6e257-199">-Include</span></span>

<span data-ttu-id="6e257-200">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="6e257-200">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="6e257-201">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="6e257-201">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6e257-202">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="6e257-202">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="6e257-203">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6e257-203">Wildcard characters are permitted.</span></span> <span data-ttu-id="6e257-204">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-204">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6e257-205">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6e257-205">-LiteralPath</span></span>

<span data-ttu-id="6e257-206">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="6e257-206">Specifies a path to one or more locations.</span></span> <span data-ttu-id="6e257-207">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="6e257-207">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="6e257-208">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="6e257-208">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6e257-209">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="6e257-209">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6e257-210">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="6e257-210">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="6e257-211">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="6e257-211">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e257-212">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="6e257-212">-NoNewline</span></span>

<span data-ttu-id="6e257-213">指示此 cmdlet 不会将新的行或回车添加到内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-213">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="6e257-214">输入对象的字符串表示形式连接起来以形成输出。</span><span class="sxs-lookup"><span data-stu-id="6e257-214">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="6e257-215">不会在输出字符串之间插入空格或换行符。</span><span class="sxs-lookup"><span data-stu-id="6e257-215">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="6e257-216">在最后一个输出字符串之后不添加任何行。</span><span class="sxs-lookup"><span data-stu-id="6e257-216">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="6e257-217">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6e257-217">-PassThru</span></span>

<span data-ttu-id="6e257-218">返回一个表示所添加内容的对象。</span><span class="sxs-lookup"><span data-stu-id="6e257-218">Returns an object representing the added content.</span></span> <span data-ttu-id="6e257-219">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="6e257-219">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6e257-220">-Path</span><span class="sxs-lookup"><span data-stu-id="6e257-220">-Path</span></span>

<span data-ttu-id="6e257-221">指定用于接收其他内容的项的路径。</span><span class="sxs-lookup"><span data-stu-id="6e257-221">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="6e257-222">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6e257-222">Wildcard characters are permitted.</span></span>
<span data-ttu-id="6e257-223">此路径必须是指向该项的路径，而不是容器的路径。</span><span class="sxs-lookup"><span data-stu-id="6e257-223">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="6e257-224">例如，必须指定一个或多个文件的路径，而不是目录的路径。</span><span class="sxs-lookup"><span data-stu-id="6e257-224">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="6e257-225">如果指定多个路径，请使用逗号分隔这些路径。</span><span class="sxs-lookup"><span data-stu-id="6e257-225">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6e257-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="6e257-226">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="6e257-227">此参数仅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="6e257-227">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="6e257-228">指定内容的备用数据流。</span><span class="sxs-lookup"><span data-stu-id="6e257-228">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="6e257-229">如果该流不存在，则此 cmdlet 将创建它。</span><span class="sxs-lookup"><span data-stu-id="6e257-229">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="6e257-230">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="6e257-230">Wildcard characters are not supported.</span></span>

<span data-ttu-id="6e257-231">**Stream** 是 FileSystem 提供程序添加到的动态参数 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-231">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="6e257-232">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="6e257-232">This parameter works only in file system drives.</span></span>

<span data-ttu-id="6e257-233">可以使用 `Add-Content` cmdlet 更改任何备用数据流的内容，例如 `Zone.Identifier` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-233">You can use the `Add-Content` cmdlet to change the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="6e257-234">但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。</span><span class="sxs-lookup"><span data-stu-id="6e257-234">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="6e257-235">如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e257-235">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="6e257-236">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="6e257-236">This parameter was introduced in PowerShell 3.0.</span></span>  <span data-ttu-id="6e257-237">在 PowerShell 7.2 中， `Add-Content` 可以针对文件和目录进行备用数据流。</span><span class="sxs-lookup"><span data-stu-id="6e257-237">As of PowerShell 7.2, `Add-Content` can target alternative data streams on both files and directories.</span></span>


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

### <span data-ttu-id="6e257-238">-Value</span><span class="sxs-lookup"><span data-stu-id="6e257-238">-Value</span></span>

<span data-ttu-id="6e257-239">指定要添加的内容。</span><span class="sxs-lookup"><span data-stu-id="6e257-239">Specifies the content to be added.</span></span> <span data-ttu-id="6e257-240">键入带引号的字符串，如 **此数据仅供内部使用**，或指定包含内容的对象，例如生成的 **DateTime** 对象 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-240">Type a quoted string, such as **This data is for internal use only**, or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="6e257-241">不能通过键入文件路径来指定文件内容，因为路径只是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="6e257-241">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="6e257-242">您可以使用 `Get-Content` 命令获取内容并将其传递给 **Value** 参数。</span><span class="sxs-lookup"><span data-stu-id="6e257-242">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6e257-243">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6e257-243">-Confirm</span></span>

<span data-ttu-id="6e257-244">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="6e257-244">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6e257-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6e257-245">-WhatIf</span></span>

<span data-ttu-id="6e257-246">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="6e257-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6e257-247">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="6e257-247">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6e257-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e257-248">CommonParameters</span></span>

<span data-ttu-id="6e257-249">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6e257-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e257-250">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6e257-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e257-251">输入</span><span class="sxs-lookup"><span data-stu-id="6e257-251">INPUTS</span></span>

### <span data-ttu-id="6e257-252">System.web、System.web 和 System.object</span><span class="sxs-lookup"><span data-stu-id="6e257-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="6e257-253">可以通过管道将值、路径或凭据传递给 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="6e257-254">输出</span><span class="sxs-lookup"><span data-stu-id="6e257-254">OUTPUTS</span></span>

### <span data-ttu-id="6e257-255">None 或 System.String</span><span class="sxs-lookup"><span data-stu-id="6e257-255">None or System.String</span></span>

<span data-ttu-id="6e257-256">当使用 **PassThru** 参数时，将 `Add-Content` 生成表示内容的 **system.string** 对象。</span><span class="sxs-lookup"><span data-stu-id="6e257-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="6e257-257">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="6e257-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6e257-258">注释</span><span class="sxs-lookup"><span data-stu-id="6e257-258">NOTES</span></span>

- <span data-ttu-id="6e257-259">将对象通过管道传递给时 `Add-Content` ，对象会在添加到项之前转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="6e257-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="6e257-260">对象类型决定字符串格式，但该格式可能不同于该对象的默认显示。</span><span class="sxs-lookup"><span data-stu-id="6e257-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="6e257-261">若要控制字符串格式，请使用发送 cmdlet 的格式设置参数。</span><span class="sxs-lookup"><span data-stu-id="6e257-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="6e257-262">还可以 `Add-Content` 通过其内置别名来引用 `ac` 。</span><span class="sxs-lookup"><span data-stu-id="6e257-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="6e257-263">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="6e257-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="6e257-264">`Add-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="6e257-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="6e257-265">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="6e257-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="6e257-266">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="6e257-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="6e257-267">相关链接</span><span class="sxs-lookup"><span data-stu-id="6e257-267">RELATED LINKS</span></span>

[<span data-ttu-id="6e257-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="6e257-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="6e257-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6e257-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="6e257-270">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="6e257-270">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="6e257-271">Get-Content</span><span class="sxs-lookup"><span data-stu-id="6e257-271">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="6e257-272">Get-Item</span><span class="sxs-lookup"><span data-stu-id="6e257-272">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="6e257-273">New-Item</span><span class="sxs-lookup"><span data-stu-id="6e257-273">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="6e257-274">Set-Content</span><span class="sxs-lookup"><span data-stu-id="6e257-274">Set-Content</span></span>](Set-Content.md)
