---
description: FileSystem
Locale: en-US
ms.date: 11/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem 提供程序
ms.openlocfilehash: cfe074475cc1304243dfd4b2245e4eec44c25244
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597455"
---
# <a name="filesystem-provider"></a><span data-ttu-id="f8c44-103">FileSystem 提供程序</span><span class="sxs-lookup"><span data-stu-id="f8c44-103">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="f8c44-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="f8c44-104">Provider name</span></span>

<span data-ttu-id="f8c44-105">FileSystem</span><span class="sxs-lookup"><span data-stu-id="f8c44-105">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="f8c44-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="f8c44-106">Drives</span></span>

<span data-ttu-id="f8c44-107">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="f8c44-107">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="f8c44-108">功能</span><span class="sxs-lookup"><span data-stu-id="f8c44-108">Capabilities</span></span>

<span data-ttu-id="f8c44-109">**Filter**、 **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="f8c44-109">**Filter**, **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="f8c44-110">简短说明</span><span class="sxs-lookup"><span data-stu-id="f8c44-110">Short description</span></span>

<span data-ttu-id="f8c44-111">提供对文件和目录的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f8c44-111">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="f8c44-112">详细说明</span><span class="sxs-lookup"><span data-stu-id="f8c44-112">Detailed description</span></span>

<span data-ttu-id="f8c44-113">PowerShell **FileSystem** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的文件和目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-113">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="f8c44-114">**文件系统** 驱动器是包含计算机上的目录和文件的分层命名空间。</span><span class="sxs-lookup"><span data-stu-id="f8c44-114">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="f8c44-115">**FileSystem** 驱动器可以是逻辑或物理驱动器、目录或映射的网络共享。</span><span class="sxs-lookup"><span data-stu-id="f8c44-115">A **FileSystem** drive can be a logical or physical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="f8c44-116">名为的驱动器 `TEMP:` 将映射到用户的临时目录路径。</span><span class="sxs-lookup"><span data-stu-id="f8c44-116">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="f8c44-117">TEMP：驱动器中的内容不会由 PowerShell 自动删除，并且由用户或操作系统进行管理。</span><span class="sxs-lookup"><span data-stu-id="f8c44-117">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span> <span data-ttu-id="f8c44-118">此功能已从 PowerShell 版本7.0 中的实验功能中移出</span><span class="sxs-lookup"><span data-stu-id="f8c44-118">This Feature was moved out of experimental features in PowerShell Version 7.0</span></span>

<span data-ttu-id="f8c44-119">**FileSystem** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="f8c44-119">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="f8c44-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="f8c44-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="f8c44-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="f8c44-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="f8c44-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="f8c44-123">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-123">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="f8c44-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-124">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="f8c44-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-125">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="f8c44-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-126">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="f8c44-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-127">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f8c44-128">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f8c44-128">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="f8c44-129">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f8c44-129">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="f8c44-130">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-130">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="f8c44-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f8c44-131">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="f8c44-132">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-132">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f8c44-133">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f8c44-133">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="f8c44-134">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="f8c44-134">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="f8c44-135">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="f8c44-135">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="f8c44-136">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="f8c44-136">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="f8c44-137">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="f8c44-137">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="f8c44-138">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="f8c44-138">Types exposed by this provider</span></span>

<span data-ttu-id="f8c44-139">文件是 [FileInfo](/dotnet/api/system.io.fileinfo) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f8c44-139">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span> <span data-ttu-id="f8c44-140">目录是 [DirectoryInfo](/dotnet/api/system.io.directoryinfo) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f8c44-140">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="f8c44-141">导航 FileSystem 驱动器</span><span class="sxs-lookup"><span data-stu-id="f8c44-141">Navigating the FileSystem drives</span></span>

<span data-ttu-id="f8c44-142">**FileSystem** 提供程序通过将计算机上的所有逻辑驱动器映射为 PowerShell 驱动器来公开其数据存储。</span><span class="sxs-lookup"><span data-stu-id="f8c44-142">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="f8c44-143">若要使用 **FileSystem** 驱动器，可使用驱动器名称后跟冒号 () ，将位置更改为驱动器 `:` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-143">To work with a **FileSystem** drive you can change your location to a drive using the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="f8c44-144">你还可以从任何其他 PowerShell 驱动器使用 **FileSystem** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="f8c44-144">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="f8c44-145">若要从其他位置引用文件或目录，请 `C:` 在路径中使用驱动器名称 (， `D:` ) 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-145">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c44-146">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="f8c44-146">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="f8c44-147">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="f8c44-147">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="f8c44-148">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="f8c44-148">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="f8c44-149">获取文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-149">Getting files and directories</span></span>

<span data-ttu-id="f8c44-150">`Get-ChildItem`Cmdlet 将返回当前位置中的所有文件和目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-150">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="f8c44-151">您可以指定不同的路径进行搜索，并使用内置参数来筛选和控制递归深度。</span><span class="sxs-lookup"><span data-stu-id="f8c44-151">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="f8c44-152">若要详细了解 cmdlet 的用法，请参阅 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)。</span><span class="sxs-lookup"><span data-stu-id="f8c44-152">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="f8c44-153">复制文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-153">Copying files and directories</span></span>

<span data-ttu-id="f8c44-154">`Copy-Item`Cmdlet 将文件和目录复制到指定的位置。</span><span class="sxs-lookup"><span data-stu-id="f8c44-154">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="f8c44-155">参数可用于筛选和递归，类似于 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-155">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="f8c44-156">以下命令将 "C：\temp" 路径下的所有文件和目录复制 \" 到文件夹 "C:\Windows\Temp"。</span><span class="sxs-lookup"><span data-stu-id="f8c44-156">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="f8c44-157">`Copy-Item` 覆盖目标目录中的文件，而不提示确认。</span><span class="sxs-lookup"><span data-stu-id="f8c44-157">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="f8c44-158">此命令将 `a.txt` 目录中的文件复制 `C:\a` 到 `C:\a\bb` 目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-158">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="f8c44-159">将目录中的所有目录和文件复制 `C:\a` 到 `C:\c` 目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-159">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="f8c44-160">如果要复制的所有目录已存在于目标目录中，则除非指定 Force 参数，否则此命令将会失败。</span><span class="sxs-lookup"><span data-stu-id="f8c44-160">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="f8c44-161">有关详细信息，请参阅 [复制项](xref:Microsoft.PowerShell.Management.Copy-Item)。</span><span class="sxs-lookup"><span data-stu-id="f8c44-161">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="f8c44-162">移动文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-162">Moving files and directories</span></span>

<span data-ttu-id="f8c44-163">此命令将 `c.txt` 目录中的文件移动 `C:\a` 到 `C:\a\aa` 目录：</span><span class="sxs-lookup"><span data-stu-id="f8c44-163">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="f8c44-164">该命令将不会自动覆盖现有的同名文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-164">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="f8c44-165">若要强制该 cmdlet 覆盖现有文件，请指定 Force 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-165">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="f8c44-166">无法移动当前所在的目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-166">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="f8c44-167">当你使用在 `Move-Item` 当前位置移动目录时，你会看到此错误。</span><span class="sxs-lookup"><span data-stu-id="f8c44-167">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="f8c44-168">管理文件内容</span><span class="sxs-lookup"><span data-stu-id="f8c44-168">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="f8c44-169">获取文件内容</span><span class="sxs-lookup"><span data-stu-id="f8c44-169">Get the content of a file</span></span>

<span data-ttu-id="f8c44-170">此命令将获取 "Test.txt" 文件的内容，并将其显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="f8c44-170">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="f8c44-171">你可以通过管道将文件内容传递给其他 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8c44-171">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="f8c44-172">例如，下面的命令读取文件的内容 `Test.txt` ，然后将其作为输入提供给 [convertto-html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet：</span><span class="sxs-lookup"><span data-stu-id="f8c44-172">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="f8c44-173">还可以通过在其提供程序路径前面加上美元符号 () 来检索文件的内容 `$` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-173">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="f8c44-174">由于变量命名限制，路径必须括在大括号中。</span><span class="sxs-lookup"><span data-stu-id="f8c44-174">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="f8c44-175">有关详细信息，请参阅 [about_Variables](about_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c44-175">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="f8c44-176">向文件添加内容</span><span class="sxs-lookup"><span data-stu-id="f8c44-176">Add content to a file</span></span>

<span data-ttu-id="f8c44-177">此命令将 "test content" 字符串追加到 `Test.txt` 文件中：</span><span class="sxs-lookup"><span data-stu-id="f8c44-177">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="f8c44-178">`Test.txt`不会删除文件中的现有内容。</span><span class="sxs-lookup"><span data-stu-id="f8c44-178">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="f8c44-179">替换文件的内容</span><span class="sxs-lookup"><span data-stu-id="f8c44-179">Replace the content of a file</span></span>

<span data-ttu-id="f8c44-180">此命令将文件的内容替换 `Test.txt` 为 "测试内容" 字符串：</span><span class="sxs-lookup"><span data-stu-id="f8c44-180">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="f8c44-181">它将覆盖的内容 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-181">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="f8c44-182">在创建文件时，可以使用 [新项](xref:Microsoft.PowerShell.Management.New-Item)Cmdlet 的 **Value** 参数将内容添加到文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-182">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="f8c44-183">遍历文件的内容</span><span class="sxs-lookup"><span data-stu-id="f8c44-183">Loop through the contents of a file</span></span>

<span data-ttu-id="f8c44-184">默认情况下，该 `Get-Content` cmdlet 使用行尾字符作为分隔符，因此它将以字符串集合的形式获取文件，每行都作为文件中的一个字符串。</span><span class="sxs-lookup"><span data-stu-id="f8c44-184">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="f8c44-185">可以使用 `-Delimiter` 参数来指定备用分隔符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-185">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="f8c44-186">如果将该分隔符设置为表示一个部分的结尾或下一部分开头的字符，则可以将该文件拆分为多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="f8c44-186">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="f8c44-187">第一个命令获取 `Employees.txt` 文件并将其拆分为多个部分，其中每个部分均以单词 "End Of Employee Record" 结尾，并将其保存在 `$e` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f8c44-187">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="f8c44-188">第二个命令使用数组表示法来获取中的集合中的第一项 `$e` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-188">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="f8c44-189">它使用的索引为0，因为 PowerShell 数组是从零开始的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-189">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="f8c44-190">有关 cmdlet 的详细信息 `Get-Content` ，请参阅 [获取内容](xref:Microsoft.PowerShell.Management.Get-Content)的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="f8c44-190">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="f8c44-191">有关数组的详细信息，请参阅 [about_Arrays](../About/about_Arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c44-191">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="f8c44-192">管理安全描述符</span><span class="sxs-lookup"><span data-stu-id="f8c44-192">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="f8c44-193">查看文件的 ACL</span><span class="sxs-lookup"><span data-stu-id="f8c44-193">View the ACL for a file</span></span>

<span data-ttu-id="f8c44-194">此命令返回 [accesscontrol-namespace. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 对象：</span><span class="sxs-lookup"><span data-stu-id="f8c44-194">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="f8c44-195">有关此对象的详细信息，请通过管道将命令传递给 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8c44-195">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="f8c44-196">或者，请参阅 [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 类。</span><span class="sxs-lookup"><span data-stu-id="f8c44-196">Or, see [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="f8c44-197">修改文件的 ACL</span><span class="sxs-lookup"><span data-stu-id="f8c44-197">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="f8c44-198">创建和设置文件的 ACL</span><span class="sxs-lookup"><span data-stu-id="f8c44-198">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="f8c44-199">创建文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-199">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="f8c44-200">创建目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-200">Create a directory</span></span>

<span data-ttu-id="f8c44-201">此命令 `logfiles` 在驱动器上创建目录 `C` ：</span><span class="sxs-lookup"><span data-stu-id="f8c44-201">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="f8c44-202">PowerShell 还包括一个 `mkdir` 函数 (别名 `md`) ，该函数使用 [新项](xref:Microsoft.PowerShell.Management.New-Item) cmdlet 来创建新的目录。</span><span class="sxs-lookup"><span data-stu-id="f8c44-202">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="f8c44-203">创建文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-203">Create a file</span></span>

<span data-ttu-id="f8c44-204">此命令 `log2.txt` 在目录中创建文件 `C:\logfiles` ，然后将 "test log" 字符串添加到该文件中：</span><span class="sxs-lookup"><span data-stu-id="f8c44-204">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="f8c44-205">创建具有内容的文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-205">Create a file with content</span></span>

<span data-ttu-id="f8c44-206">在目录中创建一个名为的文件 `log2.txt` `C:\logfiles` ，并将字符串 "test log" 添加到该文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-206">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="f8c44-207">重命名文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-207">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="f8c44-208">重命名文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-208">Rename a file</span></span>

<span data-ttu-id="f8c44-209">此命令将 `a.txt` 目录中的文件重命名 `C:\a` 为 `b.txt` ：</span><span class="sxs-lookup"><span data-stu-id="f8c44-209">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="f8c44-210">重命名目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-210">Rename a directory</span></span>

<span data-ttu-id="f8c44-211">此命令将目录重命名 `C:\a\cc` 为 `C:\a\dd` ：</span><span class="sxs-lookup"><span data-stu-id="f8c44-211">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="f8c44-212">删除文件和目录</span><span class="sxs-lookup"><span data-stu-id="f8c44-212">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="f8c44-213">删除文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-213">Delete a file</span></span>

<span data-ttu-id="f8c44-214">此命令删除 `Test.txt` 当前目录中的文件：</span><span class="sxs-lookup"><span data-stu-id="f8c44-214">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="f8c44-215">使用通配符删除文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-215">Delete files using wildcards</span></span>

<span data-ttu-id="f8c44-216">此命令删除当前目录中文件扩展名为的所有文件 `.xml` ：</span><span class="sxs-lookup"><span data-stu-id="f8c44-216">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="f8c44-217">通过调用关联文件启动程序</span><span class="sxs-lookup"><span data-stu-id="f8c44-217">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="f8c44-218">调用文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-218">Invoke a file</span></span>

<span data-ttu-id="f8c44-219">第一个命令使用 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet 来获取有关本地服务的信息。</span><span class="sxs-lookup"><span data-stu-id="f8c44-219">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="f8c44-220">它通过管道将信息传递给 [导出 Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet，然后将该信息存储在 `Services.csv` 文件中。</span><span class="sxs-lookup"><span data-stu-id="f8c44-220">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="f8c44-221">第二个命令使用 [调用项](xref:Microsoft.PowerShell.Management.Invoke-Item) `services.csv` 在与扩展关联的程序中打开文件 `.csv` ：</span><span class="sxs-lookup"><span data-stu-id="f8c44-221">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="f8c44-222">获取具有指定属性的文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="f8c44-222">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="f8c44-223">获取系统文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-223">Get System files</span></span>

<span data-ttu-id="f8c44-224">此命令将获取当前目录及其子目录中的系统文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-224">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="f8c44-225">它使用 `-File` 参数仅获取 (不是目录) 的文件，并使用 `-System` 参数仅获取具有 "system" 属性的项。</span><span class="sxs-lookup"><span data-stu-id="f8c44-225">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="f8c44-226">它使用 `-Recurse` 参数获取当前目录和所有子目录中的项。</span><span class="sxs-lookup"><span data-stu-id="f8c44-226">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="f8c44-227">获取隐藏文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-227">Get Hidden files</span></span>

<span data-ttu-id="f8c44-228">此命令将获取当前目录中的所有文件，其中包括隐藏文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-228">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="f8c44-229">它使用具有两个值的 **属性** 参数， `!Directory+Hidden` 这些值可获取隐藏的文件，并 `!Directory` 可获取所有其他文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-229">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="f8c44-230">`dir -att !d,!d+h` 等效于此命令。</span><span class="sxs-lookup"><span data-stu-id="f8c44-230">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="f8c44-231">获取压缩和加密的文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-231">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="f8c44-232">此命令将获取当前目录中已压缩或加密的文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-232">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="f8c44-233">它使用 `-Attributes` 具有两个值的参数 `Compressed` 和 `Encrypted` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-233">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="f8c44-234">值用逗号分隔， `,` 表示 "OR" 运算符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-234">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="f8c44-235">动态参数</span><span class="sxs-lookup"><span data-stu-id="f8c44-235">Dynamic parameters</span></span>

<span data-ttu-id="f8c44-236">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="f8c44-236">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="f8c44-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="f8c44-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="f8c44-238">指定文件编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-238">Specifies the file encoding.</span></span> <span data-ttu-id="f8c44-239">默认值为 ASCII。</span><span class="sxs-lookup"><span data-stu-id="f8c44-239">The default is ASCII.</span></span>

- <span data-ttu-id="f8c44-240">**Ascii**：使用 ascii (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-240">**ASCII**:  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f8c44-241">**BigEndianUnicode**：使用大字节序字节顺序对 utf-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-241">**BigEndianUnicode**:  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="f8c44-242">**String**：对字符串使用编码类型。</span><span class="sxs-lookup"><span data-stu-id="f8c44-242">**String**:  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="f8c44-243">**Unicode**：使用小 endian 字节顺序对 utf-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-243">**Unicode**:  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="f8c44-244">**UTF7**：用 Utf-7 格式编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-244">**UTF7**:   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="f8c44-245">**UTF8**：以 utf-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-245">**UTF8**:  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="f8c44-246">**UTF8BOM**：采用 Utf-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="f8c44-246">**UTF8BOM**: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f8c44-247">**UF8NOBOM**：用无字节顺序标记的 Utf-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="f8c44-247">**UF8NOBOM**: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f8c44-248">**UTF32**：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-248">**UTF32**:  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="f8c44-249">**默认**：在默认的安装代码页中进行编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-249">**Default**: Encodes in the default installed code page.</span></span>
- <span data-ttu-id="f8c44-250">**OEM**：对 MS-DOS 和控制台程序使用默认编码。</span><span class="sxs-lookup"><span data-stu-id="f8c44-250">**OEM**: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="f8c44-251">**未知**：编码类型未知或无效。</span><span class="sxs-lookup"><span data-stu-id="f8c44-251">**Unknown**:  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="f8c44-252">数据可作为二进制处理。</span><span class="sxs-lookup"><span data-stu-id="f8c44-252">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-253">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-253">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-254">Add-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-254">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="f8c44-255">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-255">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="f8c44-256">Set-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-256">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="f8c44-257">Delimiter \<System.String\></span><span class="sxs-lookup"><span data-stu-id="f8c44-257">Delimiter \<System.String\></span></span>

<span data-ttu-id="f8c44-258">指定 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 用于在读取文件时将该文件划分为对象的分隔符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-258">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="f8c44-259">默认值为 `\n` 行尾字符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-259">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="f8c44-260">读取文本文件时， [获取内容](xref:Microsoft.PowerShell.Management.Get-Content) 将返回 string 对象的集合，其中每个对象都以分隔符字符结尾。</span><span class="sxs-lookup"><span data-stu-id="f8c44-260">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="f8c44-261">输入文件中不存在的分隔符， [获取内容](xref:Microsoft.PowerShell.Management.Get-Content) 将整个文件作为单个未分隔的对象返回。</span><span class="sxs-lookup"><span data-stu-id="f8c44-261">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="f8c44-262">你可以使用此参数将大文件拆分为较小的文件，方法是指定文件分隔符（例如“End of Example”）作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-262">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="f8c44-263">分隔符将被保留（不会被丢弃），并且成为每个文件部分中的最后一项。</span><span class="sxs-lookup"><span data-stu-id="f8c44-263">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c44-264">目前，当参数的值 `-Delimiter` 为空字符串时， [get-help](xref:Microsoft.PowerShell.Management.Get-Content) 不会返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="f8c44-264">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="f8c44-265">这是一个已知问题。</span><span class="sxs-lookup"><span data-stu-id="f8c44-265">This is a known issue.</span></span> <span data-ttu-id="f8c44-266">若要强制执行 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 以将整个文件作为单个的未分隔字符串返回，请输入文件中不存在的值。</span><span class="sxs-lookup"><span data-stu-id="f8c44-266">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-267">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-267">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-268">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-268">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-269">Wait \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-269">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-270">等待要追加到文件的内容。</span><span class="sxs-lookup"><span data-stu-id="f8c44-270">Waits for content to be appended to the file.</span></span> <span data-ttu-id="f8c44-271">如果已追加内容，则返回追加的内容。</span><span class="sxs-lookup"><span data-stu-id="f8c44-271">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="f8c44-272">如果已更改内容，则返回整个文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-272">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="f8c44-273">在等待过程中，[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 将每秒检查一次文件，直到你中断该操作（例如通过按 CTRL+C）。</span><span class="sxs-lookup"><span data-stu-id="f8c44-273">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-274">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-274">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-275">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-275">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="f8c44-276">Attributes \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="f8c44-276">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="f8c44-277">获取具有指定属性的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="f8c44-277">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="f8c44-278">此参数支持所有属性，并且允许你指定复杂的属性组合。</span><span class="sxs-lookup"><span data-stu-id="f8c44-278">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="f8c44-279">此 `-Attributes` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-279">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-280">`-Attributes`参数支持以下属性：</span><span class="sxs-lookup"><span data-stu-id="f8c44-280">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="f8c44-281">**存档**</span><span class="sxs-lookup"><span data-stu-id="f8c44-281">**Archive**</span></span>
- <span data-ttu-id="f8c44-282">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="f8c44-282">**Compressed**</span></span>
- <span data-ttu-id="f8c44-283">**设备**</span><span class="sxs-lookup"><span data-stu-id="f8c44-283">**Device**</span></span>
- <span data-ttu-id="f8c44-284">**Directory**</span><span class="sxs-lookup"><span data-stu-id="f8c44-284">**Directory**</span></span>
- <span data-ttu-id="f8c44-285">**已加密**</span><span class="sxs-lookup"><span data-stu-id="f8c44-285">**Encrypted**</span></span>
- <span data-ttu-id="f8c44-286">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="f8c44-286">**Hidden**</span></span>
- <span data-ttu-id="f8c44-287">**正常**</span><span class="sxs-lookup"><span data-stu-id="f8c44-287">**Normal**</span></span>
- <span data-ttu-id="f8c44-288">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="f8c44-288">**NotContentIndexed**</span></span>
- <span data-ttu-id="f8c44-289">**断开**</span><span class="sxs-lookup"><span data-stu-id="f8c44-289">**Offline**</span></span>
- <span data-ttu-id="f8c44-290">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="f8c44-290">**ReadOnly**</span></span>
- <span data-ttu-id="f8c44-291">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="f8c44-291">**ReparsePoint**</span></span>
- <span data-ttu-id="f8c44-292">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="f8c44-292">**SparseFile**</span></span>
- <span data-ttu-id="f8c44-293">**系统**</span><span class="sxs-lookup"><span data-stu-id="f8c44-293">**System**</span></span>
- <span data-ttu-id="f8c44-294">**临时**</span><span class="sxs-lookup"><span data-stu-id="f8c44-294">**Temporary**</span></span>

<span data-ttu-id="f8c44-295">有关这些属性的说明，请参阅 [FileAttributes](/dotnet/api/system.io.fileattributes) 枚举。</span><span class="sxs-lookup"><span data-stu-id="f8c44-295">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="f8c44-296">使用以下运算符合并属性。</span><span class="sxs-lookup"><span data-stu-id="f8c44-296">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="f8c44-297">`!` -NOT</span><span class="sxs-lookup"><span data-stu-id="f8c44-297">`!` - NOT</span></span>
- <span data-ttu-id="f8c44-298">`+` -和</span><span class="sxs-lookup"><span data-stu-id="f8c44-298">`+` - AND</span></span>
- <span data-ttu-id="f8c44-299">`,` -或</span><span class="sxs-lookup"><span data-stu-id="f8c44-299">`,` - OR</span></span>

<span data-ttu-id="f8c44-300">运算符与其属性之间不允许有空格。</span><span class="sxs-lookup"><span data-stu-id="f8c44-300">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="f8c44-301">但是，在逗号之前允许有空格。</span><span class="sxs-lookup"><span data-stu-id="f8c44-301">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-302">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-302">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-303">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-303">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-304">Directory \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-304">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-305">获取目录（文件夹）。</span><span class="sxs-lookup"><span data-stu-id="f8c44-305">Gets directories (folders).</span></span>

<span data-ttu-id="f8c44-306">此 `-Directory` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-306">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-307">若要仅获取目录，请使用 `-Directory` 参数并省略 `-File` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-307">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="f8c44-308">若要排除目录，请使用 `-File` 参数并省略 `-Directory` 参数，或使用 `-Attributes` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-308">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-309">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-309">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-310">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-310">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-311">File \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-311">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-312">获取文件。</span><span class="sxs-lookup"><span data-stu-id="f8c44-312">Gets files.</span></span>

<span data-ttu-id="f8c44-313">此 `-File` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-313">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-314">若要仅获取文件，请使用 `-File` 参数并省略 `-Directory` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-314">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="f8c44-315">若要排除文件，请使用 `-Directory` 参数并省略 `-File` 参数，或使用 `-Attributes` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-315">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-316">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-316">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-317">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-317">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-318">Hidden \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-318">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-319">仅获取隐藏的文件和目录（文件夹）。</span><span class="sxs-lookup"><span data-stu-id="f8c44-319">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="f8c44-320">默认情况下， [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 仅获取非隐藏项。</span><span class="sxs-lookup"><span data-stu-id="f8c44-320">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="f8c44-321">此 `-Hidden` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-321">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-322">若要仅获取隐藏项，请使用 `-Hidden` 参数、其 `h` 或 `ah` 别名或参数的 **隐藏** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-322">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="f8c44-323">若要排除隐藏项，请省略 `-Hidden` 参数或使用 `-Attributes` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-323">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-324">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-324">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-327">仅获取只读文件和目录（文件夹）。</span><span class="sxs-lookup"><span data-stu-id="f8c44-327">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="f8c44-328">此 `-ReadOnly` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-328">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-329">若要仅获取只读项，请使用 `-ReadOnly` 参数、其 `ar` 别名或参数的 **ReadOnly** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-329">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="f8c44-330">若要排除只读项，请使用 `-Attributes` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-330">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-331">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-331">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-332">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-332">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="f8c44-333">System \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-333">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="f8c44-334">仅获取系统文件和目录（文件夹）。</span><span class="sxs-lookup"><span data-stu-id="f8c44-334">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="f8c44-335">此 `-System` 参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f8c44-335">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f8c44-336">若要仅获取系统文件和文件夹，请使用参数 `-System` 、其 `as` 别名或参数的 **系统** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-336">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="f8c44-337">若要排除系统文件和文件夹，请使用 `-Attributes` 参数。</span><span class="sxs-lookup"><span data-stu-id="f8c44-337">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-338">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-338">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-339">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f8c44-339">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="f8c44-340">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="f8c44-340">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="f8c44-341">`$True`当文件的 `LastWriteTime` 值大于指定的日期时返回。</span><span class="sxs-lookup"><span data-stu-id="f8c44-341">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="f8c44-342">否则，它将返回 `$False`。</span><span class="sxs-lookup"><span data-stu-id="f8c44-342">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="f8c44-343">输入日期 [时间](/dotnet/api/system.datetime) 对象（例如 [获取 Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet 返回的对象），或者输入一个可转换为 [DateTime](/dotnet/api/system.datetime) 对象的字符串（例如） `"August 10, 2011 2:00 PM"` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-343">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-344">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-344">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-345">Test-Path</span><span class="sxs-lookup"><span data-stu-id="f8c44-345">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="f8c44-346">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="f8c44-346">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="f8c44-347">`$True`当文件的 `LastWriteTime` 值小于指定日期时返回。</span><span class="sxs-lookup"><span data-stu-id="f8c44-347">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="f8c44-348">否则，它将返回 `$False`。</span><span class="sxs-lookup"><span data-stu-id="f8c44-348">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="f8c44-349">输入日期 [时间](/dotnet/api/system.datetime) 对象（例如 [获取 Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet 返回的对象），或者输入一个可转换为 [DateTime](/dotnet/api/system.datetime) 对象的字符串（例如） `"August 10, 2011 2:00 PM"` 。</span><span class="sxs-lookup"><span data-stu-id="f8c44-349">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-350">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-350">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-351">Test-Path</span><span class="sxs-lookup"><span data-stu-id="f8c44-351">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="f8c44-352">Stream \<System.String\></span><span class="sxs-lookup"><span data-stu-id="f8c44-352">Stream \<System.String\></span></span>

<span data-ttu-id="f8c44-353">管理备用数据流。</span><span class="sxs-lookup"><span data-stu-id="f8c44-353">Manages alternate data streams.</span></span> <span data-ttu-id="f8c44-354">输入流名称。</span><span class="sxs-lookup"><span data-stu-id="f8c44-354">Enter the stream name.</span></span> <span data-ttu-id="f8c44-355">仅允许在文件系统驱动器中 [获取项](xref:Microsoft.PowerShell.Management.Get-Item) 和 [删除项](xref:Microsoft.PowerShell.Management.Remove-Item) 命令的通配符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-355">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-356">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-356">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-357">Add-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-357">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="f8c44-358">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-358">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="f8c44-359">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-359">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="f8c44-360">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-360">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="f8c44-361">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-361">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f8c44-362">Set-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-362">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="f8c44-363">Raw \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="f8c44-363">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="f8c44-364">忽略换行符。</span><span class="sxs-lookup"><span data-stu-id="f8c44-364">Ignores newline characters.</span></span> <span data-ttu-id="f8c44-365">返回作为单个项的内容。</span><span class="sxs-lookup"><span data-stu-id="f8c44-365">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-366">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-366">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-367">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f8c44-367">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="f8c44-368">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="f8c44-368">ItemType \<String\></span></span>

<span data-ttu-id="f8c44-369">此参数允许你指定要创建的项目的 tye `New-Item`</span><span class="sxs-lookup"><span data-stu-id="f8c44-369">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="f8c44-370">此参数的可用值取决于当前使用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="f8c44-370">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="f8c44-371">在 `FileSystem` 驱动器中，允许使用以下值：</span><span class="sxs-lookup"><span data-stu-id="f8c44-371">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="f8c44-372">文件</span><span class="sxs-lookup"><span data-stu-id="f8c44-372">File</span></span>
- <span data-ttu-id="f8c44-373">Directory</span><span class="sxs-lookup"><span data-stu-id="f8c44-373">Directory</span></span>
- <span data-ttu-id="f8c44-374">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="f8c44-374">SymbolicLink</span></span>
- <span data-ttu-id="f8c44-375">交接点</span><span class="sxs-lookup"><span data-stu-id="f8c44-375">Junction</span></span>
- <span data-ttu-id="f8c44-376">硬</span><span class="sxs-lookup"><span data-stu-id="f8c44-376">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="f8c44-377">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c44-377">Cmdlets supported</span></span>

- [<span data-ttu-id="f8c44-378">New-Item</span><span class="sxs-lookup"><span data-stu-id="f8c44-378">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="f8c44-379">使用管道</span><span class="sxs-lookup"><span data-stu-id="f8c44-379">Using the pipeline</span></span>

<span data-ttu-id="f8c44-380">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="f8c44-380">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="f8c44-381">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="f8c44-381">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="f8c44-382">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="f8c44-382">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="f8c44-383">获取帮助</span><span class="sxs-lookup"><span data-stu-id="f8c44-383">Getting help</span></span>

<span data-ttu-id="f8c44-384">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="f8c44-384">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="f8c44-385">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="f8c44-385">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="f8c44-386">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8c44-386">See also</span></span>

[<span data-ttu-id="f8c44-387">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f8c44-387">about_Providers</span></span>](../About/about_Providers.md)
