---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 58807ba0745a6b09e7956547425c489b427d4f4b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596209"
---
# <span data-ttu-id="0c0d1-102">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="0c0d1-102">Compress-Archive</span></span>

## <span data-ttu-id="0c0d1-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0c0d1-103">SYNOPSIS</span></span>
<span data-ttu-id="0c0d1-104">从指定的文件和目录创建压缩的存档文件或压缩文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-104">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="0c0d1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c0d1-105">SYNTAX</span></span>

### <span data-ttu-id="0c0d1-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="0c0d1-106">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c0d1-107">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="0c0d1-107">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c0d1-108">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="0c0d1-108">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c0d1-109">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="0c0d1-109">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c0d1-110">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="0c0d1-110">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c0d1-111">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0c0d1-111">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0c0d1-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c0d1-112">DESCRIPTION</span></span>

<span data-ttu-id="0c0d1-113">`Compress-Archive`Cmdlet 从一个或多个指定的文件或目录创建压缩文件或压缩文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-113">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="0c0d1-114">存档将多个文件（具有可选压缩）打包到一个压缩文件中，以便于分发和存储。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-114">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="0c0d1-115">可以使用 **CompressionLevel** 参数指定的压缩算法来压缩存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-115">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="0c0d1-116">`Compress-Archive`Cmdlet 使用 MICROSOFT .NET API [System.IO.Compression.Zip存档](/dotnet/api/system.io.compression.ziparchive)来压缩文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-116">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="0c0d1-117">最大文件大小为 2 GB，因为存在基础 API 限制。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-117">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="0c0d1-118">一些示例使用展开来减少代码示例的行长度。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-118">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="0c0d1-119">有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-119">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="0c0d1-120">示例</span><span class="sxs-lookup"><span data-stu-id="0c0d1-120">EXAMPLES</span></span>

### <span data-ttu-id="0c0d1-121">示例1：压缩文件以创建存档文件</span><span class="sxs-lookup"><span data-stu-id="0c0d1-121">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="0c0d1-122">此示例压缩来自不同目录的文件，并创建存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-122">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="0c0d1-123">通配符用于获取具有特定文件扩展名的所有文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-123">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="0c0d1-124">存档文件中没有目录结构，因为该 **路径** 仅指定文件名。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-124">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="0c0d1-125">**Path** 参数接受带有通配符的特定文件名和文件名 `*.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-125">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="0c0d1-126">**路径** 使用以逗号分隔的列表从不同的目录中获取文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-126">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="0c0d1-127">压缩级别是 **最快** 的，可减少处理时间。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-127">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="0c0d1-128">**DestinationPath** 参数指定文件的位置 `Draft.zip` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-128">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="0c0d1-129">`Draft.zip`文件包含扩展名为的文件 `Draftdoc.docx` 以及所有文件 `.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-129">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="0c0d1-130">示例2：使用 LiteralPath 压缩文件</span><span class="sxs-lookup"><span data-stu-id="0c0d1-130">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="0c0d1-131">此示例将压缩特定的命名文件并创建一个新的存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-131">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="0c0d1-132">存档文件中没有目录结构，因为该 **路径** 仅指定文件名。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-132">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="0c0d1-133">使用绝对路径和文件名，因为 **LiteralPath** 参数不接受通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-133">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="0c0d1-134">**路径** 使用以逗号分隔的列表从不同的目录中获取文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-134">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="0c0d1-135">压缩级别是 **最快** 的，可减少处理时间。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-135">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="0c0d1-136">**DestinationPath** 参数指定文件的位置 `Draft.zip` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-136">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="0c0d1-137">`Draft.zip`文件仅包含 `Draftdoc.docx` 和 `diagram2.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-137">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="0c0d1-138">示例3：压缩包含根目录的目录</span><span class="sxs-lookup"><span data-stu-id="0c0d1-138">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="0c0d1-139">此示例将压缩目录，并创建 **包含** 根目录及其所有文件和子目录的存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-139">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="0c0d1-140">存档文件具有目录结构，因为 **路径** 指定了根目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-140">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="0c0d1-141">`Compress-Archive` 使用 **Path** 参数指定根目录 `C:\Reference` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-141">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="0c0d1-142">**DestinationPath** 参数指定存档文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-142">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="0c0d1-143">`Draft.zip`存档包括 `Reference` 根目录及其所有文件和子目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-143">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="0c0d1-144">示例4：压缩排除根目录的目录</span><span class="sxs-lookup"><span data-stu-id="0c0d1-144">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="0c0d1-145">此示例将压缩目录，并创建一个 **排除** 根目录的存档文件，因为 **路径** 使用的星号 (`*`) 通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-145">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="0c0d1-146">存档包含包含根目录文件和子目录的目录结构。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-146">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="0c0d1-147">`Compress-Archive` 使用 **Path** 参数指定根目录， `C:\Reference` 其中星号 (`*`) 通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-147">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="0c0d1-148">**DestinationPath** 参数指定存档文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-148">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="0c0d1-149">`Draft.zip`存档包含根目录的文件和子目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-149">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="0c0d1-150">`Reference`从存档中排除了根目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-150">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="0c0d1-151">示例5：仅压缩根目录中的文件</span><span class="sxs-lookup"><span data-stu-id="0c0d1-151">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="0c0d1-152">此示例仅压缩根目录中的文件，并创建存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-152">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="0c0d1-153">存档中没有目录结构，因为只有文件被压缩。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-153">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="0c0d1-154">`Compress-Archive` 使用 **Path** 参数指定根目录， `C:\Reference` 并将 **星形** (`*.*`) 通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-154">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="0c0d1-155">**DestinationPath** 参数指定存档文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-155">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="0c0d1-156">`Draft.zip`存档只包含 `Reference` 根目录文件，并排除根目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-156">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="0c0d1-157">示例6：使用管道对文件进行存档</span><span class="sxs-lookup"><span data-stu-id="0c0d1-157">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="0c0d1-158">此示例将文件沿管道向下发送，以创建存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-158">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="0c0d1-159">存档文件中没有目录结构，因为该 **路径** 仅指定文件名。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-159">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="0c0d1-160">`Get-ChildItem` 使用 **Path** 参数指定不同目录中的两个文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-160">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="0c0d1-161">每个文件由一个 **FileInfo** 对象表示，并沿管道向下发送到 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-161">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="0c0d1-162">在中存档两个指定的文件 `PipelineFiles.zip` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-162">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="0c0d1-163">示例7：使用管道将目录存档</span><span class="sxs-lookup"><span data-stu-id="0c0d1-163">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="0c0d1-164">此示例向下发送目录，以创建存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-164">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="0c0d1-165">文件作为 **FileInfo** 对象和目录作为 **DirectoryInfo** 对象发送。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-165">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="0c0d1-166">存档的目录结构不包含根目录，但其文件和子目录都包括在存档中。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-166">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="0c0d1-167">`Get-ChildItem` 使用 **Path** 参数指定 `C:\LogFiles` 根目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-167">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="0c0d1-168">每个 **FileInfo** 和 **DirectoryInfo** 对象都沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-168">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="0c0d1-169">`Compress-Archive` 将每个对象添加到 `PipelineDir.zip` 存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-169">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="0c0d1-170">未指定 **Path** 参数，因为管道对象收到参数位置0。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-170">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="0c0d1-171">示例8：递归如何影响存档</span><span class="sxs-lookup"><span data-stu-id="0c0d1-171">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="0c0d1-172">此示例演示递归如何在存档中复制文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-172">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="0c0d1-173">例如，如果将 `Get-ChildItem` 与 **递归** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-173">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="0c0d1-174">作为递归过程，每个 **FileInfo** 和 **DirectoryInfo** 对象都向下发送到该管道并添加到存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-174">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="0c0d1-175">`C:\TestLog`目录不包含任何文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-175">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="0c0d1-176">它包含一个 `testsub` 包含文件的名为的子目录 `testlog.txt` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-176">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="0c0d1-177">`Get-ChildItem` 使用 **Path** 参数指定根目录 `C:\TestLog` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-177">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="0c0d1-178">**递归** 参数处理文件和目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-178">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="0c0d1-179">为 `testsub` 和 **FileInfo** 对象创建 DirectoryInfo 对象 `testlog.txt` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-179">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="0c0d1-180">每个对象都向下发送到 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-180">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="0c0d1-181">**DestinationPath** 指定存档文件的位置。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-181">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="0c0d1-182">未指定 **Path** 参数，因为管道对象收到参数位置0。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-182">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="0c0d1-183">以下摘要说明了 `PipelineRecurse.zip` 包含重复文件的存档内容：</span><span class="sxs-lookup"><span data-stu-id="0c0d1-183">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="0c0d1-184">**DirectoryInfo** 对象创建 `testsub` 目录并包含 `testlog.txt` 文件，该文件反映了原始目录结构。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-184">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="0c0d1-185">**FileInfo** 对象 `testlog.txt` 在存档的根中创建一个重复项。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-185">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="0c0d1-186">由于递归将文件对象发送到，因此会创建重复的文件 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-186">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="0c0d1-187">此行为是预期行为，因为管道下发送的每个对象都会添加到存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-187">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="0c0d1-188">示例9：更新现有存档文件</span><span class="sxs-lookup"><span data-stu-id="0c0d1-188">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="0c0d1-189">此示例将更新目录中的现有存档文件 `Draft.Zip` `C:\Archives` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-189">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="0c0d1-190">在此示例中，现有存档文件包含根目录及其文件和子目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-190">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="0c0d1-191">命令会更新 `Draft.Zip` 目录及其子目录中的现有文件的较新版本 `C:\Reference` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-191">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="0c0d1-192">而且，已添加到 `C:\Reference` 或其子目录中的新文件将包含在更新的 `Draft.Zip` 存档中。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-192">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="0c0d1-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c0d1-193">PARAMETERS</span></span>

### <span data-ttu-id="0c0d1-194">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="0c0d1-194">-CompressionLevel</span></span>

<span data-ttu-id="0c0d1-195">指定创建存档文件时要应用的压缩量。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-195">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="0c0d1-196">较快的压缩需要的文件创建时间较少，但可能导致文件大小较大。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-196">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="0c0d1-197">如果未指定此参数，则该命令将使用默认值 " **最佳**"。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-197">If this parameter isn't specified, the command uses the default value, **Optimal**.</span></span>

<span data-ttu-id="0c0d1-198">以下是此参数可接受的值：</span><span class="sxs-lookup"><span data-stu-id="0c0d1-198">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="0c0d1-199">**最快**。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-199">**Fastest**.</span></span> <span data-ttu-id="0c0d1-200">使用最快的压缩方法可减少处理时间。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-200">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="0c0d1-201">更快的压缩可能导致文件大小较大。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-201">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="0c0d1-202">**NoCompression**。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-202">**NoCompression**.</span></span> <span data-ttu-id="0c0d1-203">不压缩源文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-203">Doesn't compress the source files.</span></span>
- <span data-ttu-id="0c0d1-204">**最佳**：</span><span class="sxs-lookup"><span data-stu-id="0c0d1-204">**Optimal**.</span></span> <span data-ttu-id="0c0d1-205">处理时间取决于文件大小。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-205">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c0d1-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0c0d1-206">-Confirm</span></span>

<span data-ttu-id="0c0d1-207">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0c0d1-208">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="0c0d1-208">-DestinationPath</span></span>

<span data-ttu-id="0c0d1-209">此参数是必需的，它指定存档输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-209">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="0c0d1-210">**DestinationPath** 应包含压缩文件的名称，以及压缩文件的绝对或相对路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-210">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="0c0d1-211">如果 **DestinationPath** 中的文件名没有 `.zip` 文件扩展名，则该 cmdlet 将添加 `.zip` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-211">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c0d1-212">-Force</span><span class="sxs-lookup"><span data-stu-id="0c0d1-212">-Force</span></span>

<span data-ttu-id="0c0d1-213">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-213">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c0d1-214">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0c0d1-214">-LiteralPath</span></span>

<span data-ttu-id="0c0d1-215">指定想要添加到存档压缩文件的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-215">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="0c0d1-216">与 **Path** 参数不同， **LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-216">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="0c0d1-217">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-217">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0c0d1-218">如果路径包含转义符，请将每个转义符括在单引号内，以指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-218">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="0c0d1-219">若要指定多个路径，并将文件包括在输出压缩文件的多个位置中，请使用逗号分隔这些路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-219">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0c0d1-220">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0c0d1-220">-PassThru</span></span>

<span data-ttu-id="0c0d1-221">使 cmdlet 输出一个表示已创建的存档文件的文件对象。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-221">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="0c0d1-222">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-222">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="0c0d1-223">-Path</span><span class="sxs-lookup"><span data-stu-id="0c0d1-223">-Path</span></span>

<span data-ttu-id="0c0d1-224">指定想要添加到存档压缩文件的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-224">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="0c0d1-225">若要指定多个路径，并将文件包含在多个位置，请使用逗号分隔这些路径。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-225">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="0c0d1-226">此参数接受通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-226">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="0c0d1-227">通配符用于将目录中的所有文件添加到存档文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-227">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="0c0d1-228">将通配符用于根目录会影响存档内容：</span><span class="sxs-lookup"><span data-stu-id="0c0d1-228">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="0c0d1-229">若要创建 **包含** 根目录及其所有文件和子目录的存档，请在不带通配符的 **路径** 中指定根目录。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-229">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="0c0d1-230">例如： `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="0c0d1-230">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="0c0d1-231">若要创建 **排除** 根目录的存档，但 zips 所有文件和子目录，请使用星号 (`*`) 通配符。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-231">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="0c0d1-232">例如： `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="0c0d1-232">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="0c0d1-233">若要创建仅 zips 根目录中的文件的存档，请使用) 通配符 (**星形** `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-233">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="0c0d1-234">根中的子目录不包括在存档中。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-234">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="0c0d1-235">例如： `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="0c0d1-235">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0c0d1-236">-Update</span><span class="sxs-lookup"><span data-stu-id="0c0d1-236">-Update</span></span>

<span data-ttu-id="0c0d1-237">通过使用具有相同名称的较新文件版本替换存档中较旧的文件版本来更新指定的存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-237">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="0c0d1-238">此外，还可添加此参数，将文件添加到现有存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-238">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c0d1-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0c0d1-239">-WhatIf</span></span>

<span data-ttu-id="0c0d1-240">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-240">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0c0d1-241">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-241">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0c0d1-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c0d1-242">CommonParameters</span></span>

<span data-ttu-id="0c0d1-243">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c0d1-244">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-244">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c0d1-245">输入</span><span class="sxs-lookup"><span data-stu-id="0c0d1-245">INPUTS</span></span>

### <span data-ttu-id="0c0d1-246">System.String</span><span class="sxs-lookup"><span data-stu-id="0c0d1-246">System.String</span></span>

<span data-ttu-id="0c0d1-247">可以通过管道将包含路径的字符串传递给一个或多个文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-247">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="0c0d1-248">输出</span><span class="sxs-lookup"><span data-stu-id="0c0d1-248">OUTPUTS</span></span>

### <span data-ttu-id="0c0d1-249">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="0c0d1-249">System.IO.FileInfo</span></span>

<span data-ttu-id="0c0d1-250">当使用 **PassThru** 参数时，该 cmdlet 仅返回 **FileInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-250">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="0c0d1-251">注释</span><span class="sxs-lookup"><span data-stu-id="0c0d1-251">NOTES</span></span>

<span data-ttu-id="0c0d1-252">使用递归并沿管道向下发送对象可以在存档中复制文件。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-252">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="0c0d1-253">例如，如果将 `Get-ChildItem` 与 **递归** 参数一起使用，则在管道中发送的每个 **FileInfo** 和 **DirectoryInfo** 对象将添加到存档。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-253">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="0c0d1-254">[ZIP 文件规范](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)未指定对包含非 ASCII 字符的文件名进行编码的标准方法。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-254">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="0c0d1-255">`Compress-Archive`Cmdlet 使用 utf-8 编码。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-255">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="0c0d1-256">其他 ZIP 存档工具可以使用其他编码方案。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-256">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="0c0d1-257">当使用不是使用 UTF-8 编码存储的文件名提取文件时， `Expand-Archive` 将使用存档中找到的原始值。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-257">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="0c0d1-258">这可能会导致文件名不同于存储在存档中的源文件名。</span><span class="sxs-lookup"><span data-stu-id="0c0d1-258">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="0c0d1-259">相关链接</span><span class="sxs-lookup"><span data-stu-id="0c0d1-259">RELATED LINKS</span></span>

[<span data-ttu-id="0c0d1-260">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="0c0d1-260">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="0c0d1-261">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="0c0d1-261">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

