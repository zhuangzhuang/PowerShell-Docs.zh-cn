---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 2561d569fa773d279e1e54561d6005e3eef7f7e3
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692790"
---
# <span data-ttu-id="f3d9a-102">Set-Content</span><span class="sxs-lookup"><span data-stu-id="f3d9a-102">Set-Content</span></span>

## <span data-ttu-id="f3d9a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f3d9a-103">SYNOPSIS</span></span>
<span data-ttu-id="f3d9a-104">写入新内容或替换文件中的现有内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-104">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="f3d9a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f3d9a-105">SYNTAX</span></span>

### <span data-ttu-id="f3d9a-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="f3d9a-106">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="f3d9a-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f3d9a-107">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="f3d9a-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f3d9a-108">DESCRIPTION</span></span>

<span data-ttu-id="f3d9a-109">`Set-Content` 是一个字符串处理 cmdlet，用于写入新内容或替换文件中的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-109">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="f3d9a-110">`Set-Content` 替换现有内容，不同于将 `Add-Content` 内容追加到文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-110">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="f3d9a-111">若要将内容发送到 `Set-Content` ，可以在命令行上使用 **Value** 参数或通过管道发送内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-111">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="f3d9a-112">如果需要为以下示例创建文件或目录，请参阅 " [新建项](New-Item.md)"。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="f3d9a-113">示例</span><span class="sxs-lookup"><span data-stu-id="f3d9a-113">EXAMPLES</span></span>

### <span data-ttu-id="f3d9a-114">示例1：替换目录中多个文件的内容</span><span class="sxs-lookup"><span data-stu-id="f3d9a-114">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="f3d9a-115">此示例替换当前目录中多个文件的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-115">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="f3d9a-116">`Get-ChildItem`Cmdlet 使用 **Path** 参数列出以当前目录开头的 **.txt** 文件。 `Test*`</span><span class="sxs-lookup"><span data-stu-id="f3d9a-116">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="f3d9a-117">`Set-Content`Cmdlet 使用 **Path** 参数指定 `Test*.txt` 文件。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-117">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="f3d9a-118">**Value** 参数提供替换每个文件中的现有内容的文本字符串 **Hello、World** 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-118">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="f3d9a-119">`Get-Content`Cmdlet 使用 **Path** 参数指定 `Test*.txt` 文件，并在 PowerShell 控制台中显示每个文件的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="f3d9a-120">示例2：创建新文件并写入内容</span><span class="sxs-lookup"><span data-stu-id="f3d9a-120">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="f3d9a-121">此示例将创建一个新文件，并将当前日期和时间写入文件。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-121">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="f3d9a-122">`Set-Content` 使用 **Path** 和 **Value** 参数在当前目录中创建一个名为 **DateTime.txt** 的新文件。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-122">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="f3d9a-123">**值** 参数用于 `Get-Date` 获取当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-123">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="f3d9a-124">`Set-Content` 将 **DateTime** 对象作为字符串写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-124">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="f3d9a-125">`Get-Content`Cmdlet 使用 **Path** 参数在 PowerShell 控制台中显示 **DateTime.txt** 的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-125">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="f3d9a-126">示例 3：在文件中替换文本</span><span class="sxs-lookup"><span data-stu-id="f3d9a-126">Example 3: Replace text in a file</span></span>

<span data-ttu-id="f3d9a-127">此命令替换现有文件中的所有 word 实例。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-127">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="f3d9a-128">`Get-Content`Cmdlet 使用 **Path** 参数来指定当前目录中的 **Notice.txt** 文件。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-128">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="f3d9a-129">`Get-Content`命令用括号括起来，以便命令在管道下发送前完成。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-129">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="f3d9a-130">**Notice.txt** 文件的内容将通过管道向下发送到 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-130">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="f3d9a-131">`ForEach-Object`使用自动变量 `$_` ，并将每次出现的警告替换为警告。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-131">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="f3d9a-132">对象通过管道向下发送到 `Set-Content` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-132">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="f3d9a-133">`Set-Content` 使用 **Path** 参数指定 **Notice.txt** 文件，并将更新的内容写入文件。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-133">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="f3d9a-134">最后一个 `Get-Content` cmdlet 在 PowerShell 控制台中显示更新的文件内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-134">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="f3d9a-135">示例4：使用筛选器与 Set-Content</span><span class="sxs-lookup"><span data-stu-id="f3d9a-135">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="f3d9a-136">可以为 cmdlet 指定筛选器 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-136">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="f3d9a-137">使用筛选器限定 **路径** 参数时，需要包含一个尾随星号 (`*`) ，以指示路径的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-137">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="f3d9a-138">以下命令将目录中的所有文件的内容设置 `*.txt` `C:\Temp` 为空 **值** 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-138">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="f3d9a-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f3d9a-139">PARAMETERS</span></span>

### <span data-ttu-id="f3d9a-140">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="f3d9a-140">-AsByteStream</span></span>

<span data-ttu-id="f3d9a-141">指定应以字节流的形式读取内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-141">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="f3d9a-142">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-142">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="f3d9a-143">将 **AsByteStream** 参数与 **Encoding** 参数一起使用时，将出现警告。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-143">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="f3d9a-144">**AsByteStream** 参数将忽略任何编码，并以字节流的形式返回输出。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-144">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="f3d9a-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="f3d9a-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f3d9a-146">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f3d9a-147">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f3d9a-148">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f3d9a-148">-Encoding</span></span>

<span data-ttu-id="f3d9a-149">指定目标文件的编码类型。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-149">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="f3d9a-150">默认值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-150">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="f3d9a-151">Encoding 是 FileSystem 提供程序添加到的动态参数 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-151">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="f3d9a-152">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-152">This parameter works only in file system drives.</span></span>

<span data-ttu-id="f3d9a-153">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3d9a-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f3d9a-154">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-154">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f3d9a-155">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-155">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="f3d9a-156">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-156">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="f3d9a-157">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-157">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="f3d9a-158">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-158">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="f3d9a-159">`utf8`：以 UTF-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-159">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="f3d9a-160">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="f3d9a-160">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f3d9a-161">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="f3d9a-161">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f3d9a-162">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-162">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="f3d9a-163">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-163">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="f3d9a-164">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)</span><span class="sxs-lookup"><span data-stu-id="f3d9a-164">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3d9a-165">-Exclude</span><span class="sxs-lookup"><span data-stu-id="f3d9a-165">-Exclude</span></span>

<span data-ttu-id="f3d9a-166">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-166">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f3d9a-167">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-167">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f3d9a-168">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-168">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f3d9a-169">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="f3d9a-170">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-170">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f3d9a-171">-Filter</span><span class="sxs-lookup"><span data-stu-id="f3d9a-171">-Filter</span></span>

<span data-ttu-id="f3d9a-172">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-172">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f3d9a-173">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-173">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="f3d9a-174">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-174">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="f3d9a-175">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-175">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f3d9a-176">-Force</span><span class="sxs-lookup"><span data-stu-id="f3d9a-176">-Force</span></span>

<span data-ttu-id="f3d9a-177">强制该 cmdlet 设置文件内容（即使该文件是只读的）。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-177">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="f3d9a-178">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-178">Implementation varies from provider to provider.</span></span> <span data-ttu-id="f3d9a-179">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="f3d9a-180">**Force** 参数不会覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-180">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="f3d9a-181">-Include</span><span class="sxs-lookup"><span data-stu-id="f3d9a-181">-Include</span></span>

<span data-ttu-id="f3d9a-182">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-182">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f3d9a-183">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-183">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f3d9a-184">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-184">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="f3d9a-185">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-185">Wildcard characters are permitted.</span></span> <span data-ttu-id="f3d9a-186">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-186">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f3d9a-187">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f3d9a-187">-LiteralPath</span></span>

<span data-ttu-id="f3d9a-188">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-188">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f3d9a-189">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-189">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="f3d9a-190">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-190">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f3d9a-191">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-191">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f3d9a-192">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-192">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f3d9a-193">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-193">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="f3d9a-194">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="f3d9a-194">-NoNewline</span></span>

<span data-ttu-id="f3d9a-195">输入对象的字符串表示形式连接起来以形成输出。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-195">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="f3d9a-196">不会在输出字符串之间插入空格或换行符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-196">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="f3d9a-197">在最后一个输出字符串之后不添加任何行。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-197">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="f3d9a-198">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f3d9a-198">-PassThru</span></span>

<span data-ttu-id="f3d9a-199">返回一个表示内容的对象。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-199">Returns an object that represents the content.</span></span> <span data-ttu-id="f3d9a-200">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-200">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f3d9a-201">-Path</span><span class="sxs-lookup"><span data-stu-id="f3d9a-201">-Path</span></span>

<span data-ttu-id="f3d9a-202">指定接受内容的项的路径。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-202">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="f3d9a-203">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-203">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f3d9a-204">-Stream</span><span class="sxs-lookup"><span data-stu-id="f3d9a-204">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="f3d9a-205">此参数仅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-205">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="f3d9a-206">指定内容的备用数据流。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-206">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="f3d9a-207">如果该流不存在，则此 cmdlet 将创建它。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-207">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="f3d9a-208">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-208">Wildcard characters are not supported.</span></span>

<span data-ttu-id="f3d9a-209">**Stream** 是 **FileSystem** 提供程序添加到的动态参数 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-209">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="f3d9a-210">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-210">This parameter works only in file system drives.</span></span>

<span data-ttu-id="f3d9a-211">你可以使用 `Set-Content` cmdlet 来创建或更新任何备用数据流的内容，例如 `Zone.Identifier` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-211">You can use the `Set-Content` cmdlet to create or update the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="f3d9a-212">但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-212">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="f3d9a-213">如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-213">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="f3d9a-214">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-214">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f3d9a-215">-Value</span><span class="sxs-lookup"><span data-stu-id="f3d9a-215">-Value</span></span>

<span data-ttu-id="f3d9a-216">为项指定新的内容。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-216">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="f3d9a-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f3d9a-217">-Confirm</span></span>

<span data-ttu-id="f3d9a-218">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f3d9a-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f3d9a-219">-WhatIf</span></span>

<span data-ttu-id="f3d9a-220">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-220">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f3d9a-221">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f3d9a-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f3d9a-222">CommonParameters</span></span>

<span data-ttu-id="f3d9a-223">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f3d9a-224">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f3d9a-225">输入</span><span class="sxs-lookup"><span data-stu-id="f3d9a-225">INPUTS</span></span>

### <span data-ttu-id="f3d9a-226">System.Object</span><span class="sxs-lookup"><span data-stu-id="f3d9a-226">System.Object</span></span>

<span data-ttu-id="f3d9a-227">可以通过管道将包含项的新值的对象传递给 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-227">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="f3d9a-228">输出</span><span class="sxs-lookup"><span data-stu-id="f3d9a-228">OUTPUTS</span></span>

### <span data-ttu-id="f3d9a-229">None 或 System.String</span><span class="sxs-lookup"><span data-stu-id="f3d9a-229">None or System.String</span></span>

<span data-ttu-id="f3d9a-230">当使用 **PassThru** 参数时，将 `Set-Content` 生成表示内容的 **system.string** 对象。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-230">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="f3d9a-231">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f3d9a-232">注释</span><span class="sxs-lookup"><span data-stu-id="f3d9a-232">NOTES</span></span>

- <span data-ttu-id="f3d9a-233">还可以 `Set-Content` 通过其内置别名来引用 `sc` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-233">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="f3d9a-234">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-234">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="f3d9a-235">`Set-Content` 用于字符串处理。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-235">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="f3d9a-236">如果将非字符串对象通过管道传递给 `Set-Content` ，它会在写入之前将对象转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-236">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="f3d9a-237">若要将对象写入文件，请使用 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-237">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="f3d9a-238">`Set-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-238">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f3d9a-239">若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-239">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="f3d9a-240">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d9a-240">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f3d9a-241">相关链接</span><span class="sxs-lookup"><span data-stu-id="f3d9a-241">RELATED LINKS</span></span>

[<span data-ttu-id="f3d9a-242">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="f3d9a-242">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="f3d9a-243">about_Automatic_Variables md</span><span class="sxs-lookup"><span data-stu-id="f3d9a-243">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="f3d9a-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f3d9a-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="f3d9a-245">Add-Content</span><span class="sxs-lookup"><span data-stu-id="f3d9a-245">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="f3d9a-246">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="f3d9a-246">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="f3d9a-247">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f3d9a-247">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="f3d9a-248">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f3d9a-248">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="f3d9a-249">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f3d9a-249">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="f3d9a-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="f3d9a-250">New-Item</span></span>](New-Item.md)
