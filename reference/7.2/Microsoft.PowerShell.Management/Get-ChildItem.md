---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: dc47a7bc29d93e1784571f9e6b27dafcb8494bae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596028"
---
# <span data-ttu-id="c4fcb-102">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c4fcb-102">Get-ChildItem</span></span>

## <span data-ttu-id="c4fcb-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c4fcb-103">SYNOPSIS</span></span>

<span data-ttu-id="c4fcb-104">获取一个或多个指定位置中的项和子项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-104">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="c4fcb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4fcb-105">SYNTAX</span></span>

### <span data-ttu-id="c4fcb-106">Items（默认值）</span><span class="sxs-lookup"><span data-stu-id="c4fcb-106">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="c4fcb-107">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="c4fcb-107">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="c4fcb-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c4fcb-108">DESCRIPTION</span></span>

<span data-ttu-id="c4fcb-109">`Get-ChildItem`Cmdlet 获取一个或多个指定位置中的项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-109">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="c4fcb-110">如果该项为容器，则此命令将获取容器内的各项（称为子项）。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-110">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="c4fcb-111">可以使用 **递归** 参数获取所有子容器中的项，并使用 **Depth** 参数来限制要递归的级别数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-111">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="c4fcb-112">`Get-ChildItem` 不显示空目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-112">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="c4fcb-113">当 `Get-ChildItem` 命令包含 **深度** 或 **递归** 参数时，输出中不包括空目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-113">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="c4fcb-114">位置 `Get-ChildItem` 由 PowerShell 提供程序向公开。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-114">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="c4fcb-115">位置可以是文件系统目录、注册表配置单元或证书存储区。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-115">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="c4fcb-116">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-116">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c4fcb-117">示例</span><span class="sxs-lookup"><span data-stu-id="c4fcb-117">EXAMPLES</span></span>

### <span data-ttu-id="c4fcb-118">示例1：从文件系统目录获取子项目</span><span class="sxs-lookup"><span data-stu-id="c4fcb-118">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="c4fcb-119">此示例从文件系统目录中获取子项目。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-119">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="c4fcb-120">将显示文件名和子目录的名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-120">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="c4fcb-121">对于空位置，该命令不会返回任何输出，并返回到 PowerShell 提示符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-121">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="c4fcb-122">`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-122">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="c4fcb-123">`Get-ChildItem` 显示 PowerShell 控制台中的文件和目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-123">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="c4fcb-124">默认情况 `Get-ChildItem` 下，会列出模式 (**特性**) 、 **LastWriteTime**、文件大小 (**长度**) 和项的 **名称** 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-124">By default `Get-ChildItem` lists the mode (**Attributes**), **LastWriteTime**, file size (**Length**), and the **Name** of the item.</span></span> <span data-ttu-id="c4fcb-125">**Mode** 属性中的字母可解释如下：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-125">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="c4fcb-126">`l` (链接) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-126">`l` (link)</span></span>
- <span data-ttu-id="c4fcb-127">`d` (目录) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-127">`d` (directory)</span></span>
- <span data-ttu-id="c4fcb-128">`a` (存档) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-128">`a` (archive)</span></span>
- <span data-ttu-id="c4fcb-129">`r` (只读) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-129">`r` (read-only)</span></span>
- <span data-ttu-id="c4fcb-130">`h` (隐藏) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-130">`h` (hidden)</span></span>
- <span data-ttu-id="c4fcb-131">`s` (系统) 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-131">`s` (system).</span></span>

<span data-ttu-id="c4fcb-132">有关模式标志的详细信息，请参阅 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-132">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="c4fcb-133">示例2：获取目录中的子项目名称</span><span class="sxs-lookup"><span data-stu-id="c4fcb-133">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="c4fcb-134">此示例仅列出目录中项的名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-134">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="c4fcb-135">`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-135">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="c4fcb-136">**Name** 参数仅返回指定路径中的文件名或目录名。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-136">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="c4fcb-137">示例3：获取当前目录和子目录中的子项</span><span class="sxs-lookup"><span data-stu-id="c4fcb-137">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="c4fcb-138">此示例显示位于当前目录及其子目录中的 **.txt** 文件。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-138">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="c4fcb-139">`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 `C:\Test\*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-139">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="c4fcb-140">**Path** 使用 `*`) 通配符 (星号来指定具有文件扩展名的所有文件 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-140">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="c4fcb-141">**递归** 参数会搜索 **Path** 目录的子目录，如 **目录：** 标题中所示。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-141">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="c4fcb-142">**Force** 参数显示其模式为 h 的隐藏文件 `hiddenfile.txt` 。 </span><span class="sxs-lookup"><span data-stu-id="c4fcb-142">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h**.</span></span>

### <span data-ttu-id="c4fcb-143">示例4：使用 Include 参数获取子项目</span><span class="sxs-lookup"><span data-stu-id="c4fcb-143">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="c4fcb-144">在此示例中， `Get-ChildItem` 使用 **Include** 参数查找 **Path** 参数所指定的目录中的特定项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-144">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="c4fcb-145">`Get-ChildItem`Cmdlet 使用 **Path** 参数指定目录 **C:\Test**。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-145">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test**.</span></span> <span data-ttu-id="c4fcb-146">**Path** 参数包含一个尾部星号 (`*`) 通配符，以指定目录的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-146">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="c4fcb-147">**Include** 参数使用星号 (`*`) 通配符来指定文件扩展名为 **.txt** 的所有文件。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-147">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt**.</span></span>

<span data-ttu-id="c4fcb-148">当使用 **Include** 参数时， **Path** 参数需要一个尾部星号 (`*`) 通配符，以指定目录的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-148">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="c4fcb-149">例如，`-Path C:\Test\*`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-149">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="c4fcb-150">如果将 **递归** 参数添加到命令中，则 `*` **Path** 参数中) 的尾随星号 (是可选的。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-150">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="c4fcb-151">**递归** 参数从 **路径** 目录及其子目录中获取项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-151">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="c4fcb-152">例如，`-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="c4fcb-152">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="c4fcb-153">如果 `*` **Path** 参数中未包含尾随星号 () ，则该命令不会返回任何输出并返回到 PowerShell 提示符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-153">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="c4fcb-154">例如，`-Path C:\Test\`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-154">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="c4fcb-155">示例5：使用 Exclude 参数获取子项目</span><span class="sxs-lookup"><span data-stu-id="c4fcb-155">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="c4fcb-156">该示例的输出显示目录 **C:\Test\Logs** 的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-156">The example's output shows the contents of the directory **C:\Test\Logs**.</span></span> <span data-ttu-id="c4fcb-157">输出是对使用 **Exclude** 和 **递归** 参数的其他命令的引用。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-157">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="c4fcb-158">`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test\Logs` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-158">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="c4fcb-159">**Exclude** 参数使用星号 (`*`) 通配符来指定以或开头的任何文件或目录， 从输出中排除。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-159">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="c4fcb-160">使用 **Exclude** 参数时， `*` **Path** 参数中)  (后缀星号是可选的。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-160">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="c4fcb-161">例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-161">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="c4fcb-162">如果 `*` **path** 参数中未包含尾随星号 () ，则显示 **path** 参数的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-162">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="c4fcb-163">例外情况是与 **Exclude** 参数的值匹配的文件名或子目录名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-163">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="c4fcb-164">如果 `*` **path** 参数中包含尾随星号 () ，则命令 recurses 到 **path** 参数的子目录中。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-164">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="c4fcb-165">例外情况是与 **Exclude** 参数的值匹配的文件名或子目录名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-165">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="c4fcb-166">如果将 **递归** 参数添加到命令中，则无论 **Path** 参数是否包含尾随星号 () ，递归输出都是相同的 `*` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-166">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="c4fcb-167">示例6：从注册表配置单元获取注册表项</span><span class="sxs-lookup"><span data-stu-id="c4fcb-167">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="c4fcb-168">此示例从获取中的所有注册表项 `HKEY_LOCAL_MACHINE\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-168">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="c4fcb-169">`Get-ChildItem` 使用 **Path** 参数指定注册表项 `HKLM:\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-169">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="c4fcb-170">配置单元的路径和顶级注册表项显示在 PowerShell 控制台中。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-170">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="c4fcb-171">有关详细信息，请参阅 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-171">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="c4fcb-172">第一个命令显示注册表项的内容 `HKLM:\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-172">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="c4fcb-173">**Exclude** 参数指示 `Get-ChildItem` 不返回以开头的任何子项 `D*` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-173">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="c4fcb-174">目前， **Exclude** 参数仅适用于子项，而不是项属性。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-174">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="c4fcb-175">示例7：获取具有代码签名颁发机构的所有证书</span><span class="sxs-lookup"><span data-stu-id="c4fcb-175">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="c4fcb-176">此示例获取 PowerShell **Cert：** 驱动器中具有代码签名颁发机构的每个证书。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-176">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="c4fcb-177">`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 **Cert：** provider。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-177">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="c4fcb-178">**递归** 参数搜索 **路径** 及其子目录指定的目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-178">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="c4fcb-179">**CodeSigningCert** 参数仅获取具有代码签名颁发机构的证书。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-179">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="c4fcb-180">有关证书提供程序和 Cert：驱动器的详细信息，请参阅 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-180">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="c4fcb-181">示例8：使用 Depth 参数获取项</span><span class="sxs-lookup"><span data-stu-id="c4fcb-181">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="c4fcb-182">此示例显示目录及其子目录中的项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-182">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="c4fcb-183">**Depth** 参数确定要包括在递归中的子目录级别数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-183">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="c4fcb-184">空目录将从输出中排除。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-184">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="c4fcb-185">`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 **C:\Parent**。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-185">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent**.</span></span> <span data-ttu-id="c4fcb-186">**Depth** 参数指定两个递归级别。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-186">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="c4fcb-187">`Get-ChildItem` 显示 **Path** 参数所指定的目录的内容和两个子目录级别。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-187">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="c4fcb-188">示例9：获取硬链接信息</span><span class="sxs-lookup"><span data-stu-id="c4fcb-188">Example 9: Getting hard link information</span></span>

<span data-ttu-id="c4fcb-189">在 PowerShell 6.2 中，添加了一个替代视图来获取硬链接信息。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-189">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### <span data-ttu-id="c4fcb-190">示例9：非 Windows 操作系统的输出</span><span class="sxs-lookup"><span data-stu-id="c4fcb-190">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="c4fcb-191">在 Unix 系统上的 PowerShell 7.1 中， `Get-ChildItem` 提供类似于 unix 的输出：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-191">In PowerShell 7.1 on Unix systems, the `Get-ChildItem` provides Unix-like output:</span></span>

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

<span data-ttu-id="c4fcb-192">现在作为输出的一部分的新属性包括：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-192">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="c4fcb-193">**UnixMode** 是 Unix 系统上表示的文件权限</span><span class="sxs-lookup"><span data-stu-id="c4fcb-193">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="c4fcb-194">**用户** 是文件所有者</span><span class="sxs-lookup"><span data-stu-id="c4fcb-194">**User** is the file owner</span></span>
- <span data-ttu-id="c4fcb-195">**组** 是组的所有者</span><span class="sxs-lookup"><span data-stu-id="c4fcb-195">**Group** is the group owner</span></span>
- <span data-ttu-id="c4fcb-196">**Size** 是在 Unix 系统上表示的文件或目录的大小</span><span class="sxs-lookup"><span data-stu-id="c4fcb-196">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="c4fcb-197">此功能已从实验迁移到 PowerShell 7.1 中的主流。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-197">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="c4fcb-198">参数</span><span class="sxs-lookup"><span data-stu-id="c4fcb-198">Parameters</span></span>

### <span data-ttu-id="c4fcb-199">-Attributes</span><span class="sxs-lookup"><span data-stu-id="c4fcb-199">-Attributes</span></span>

<span data-ttu-id="c4fcb-200">获取具有指定属性的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-200">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="c4fcb-201">此参数支持所有属性，并且允许你指定复杂的属性组合。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-201">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="c4fcb-202">例如，若要获取加密或压缩的非系统文件（而不是目录），请键入：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-202">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="c4fcb-203">若要查找具有常用属性的文件和文件夹，请使用 **attributes** 参数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-203">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="c4fcb-204">或参数 **目录**、 **文件**、 **隐藏**、 **只读** 和 **系统**。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-204">Or, the parameters **Directory**, **File**, **Hidden**, **ReadOnly**, and **System**.</span></span>

<span data-ttu-id="c4fcb-205">Properties **参数支持** 以下属性：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-205">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="c4fcb-206">**存档**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-206">**Archive**</span></span>
- <span data-ttu-id="c4fcb-207">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-207">**Compressed**</span></span>
- <span data-ttu-id="c4fcb-208">**设备**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-208">**Device**</span></span>
- <span data-ttu-id="c4fcb-209">**Directory**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-209">**Directory**</span></span>
- <span data-ttu-id="c4fcb-210">**已加密**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-210">**Encrypted**</span></span>
- <span data-ttu-id="c4fcb-211">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-211">**Hidden**</span></span>
- <span data-ttu-id="c4fcb-212">**IntegrityStream**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-212">**IntegrityStream**</span></span>
- <span data-ttu-id="c4fcb-213">**正常**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-213">**Normal**</span></span>
- <span data-ttu-id="c4fcb-214">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-214">**NoScrubData**</span></span>
- <span data-ttu-id="c4fcb-215">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-215">**NotContentIndexed**</span></span>
- <span data-ttu-id="c4fcb-216">**断开**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-216">**Offline**</span></span>
- <span data-ttu-id="c4fcb-217">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-217">**ReadOnly**</span></span>
- <span data-ttu-id="c4fcb-218">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-218">**ReparsePoint**</span></span>
- <span data-ttu-id="c4fcb-219">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-219">**SparseFile**</span></span>
- <span data-ttu-id="c4fcb-220">**系统**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-220">**System**</span></span>
- <span data-ttu-id="c4fcb-221">**临时**</span><span class="sxs-lookup"><span data-stu-id="c4fcb-221">**Temporary**</span></span>

<span data-ttu-id="c4fcb-222">有关这些属性的说明，请参阅 [FileAttributes 枚举](/dotnet/api/system.io.fileattributes)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-222">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="c4fcb-223">若要合并属性，请使用以下运算符：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-223">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="c4fcb-224">`!` (未) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-224">`!` (NOT)</span></span>
- <span data-ttu-id="c4fcb-225">`+` (和) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-225">`+` (AND)</span></span>
- <span data-ttu-id="c4fcb-226">`,` (或) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-226">`,` (OR)</span></span>

<span data-ttu-id="c4fcb-227">运算符与其属性之间不要使用空格。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-227">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="c4fcb-228">逗号后接受空格。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-228">Spaces are accepted after commas.</span></span>

<span data-ttu-id="c4fcb-229">对于常用属性，请使用以下缩写：</span><span class="sxs-lookup"><span data-stu-id="c4fcb-229">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="c4fcb-230">`D` (目录) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-230">`D` (Directory)</span></span>
- <span data-ttu-id="c4fcb-231">`H` (隐藏) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-231">`H` (Hidden)</span></span>
- <span data-ttu-id="c4fcb-232">`R` (只读) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-232">`R` (Read-only)</span></span>
- <span data-ttu-id="c4fcb-233">`S` (系统) </span><span class="sxs-lookup"><span data-stu-id="c4fcb-233">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-234">-Depth</span><span class="sxs-lookup"><span data-stu-id="c4fcb-234">-Depth</span></span>

<span data-ttu-id="c4fcb-235">此参数是在 PowerShell 5.0 中添加的，使你可以控制递归的深度。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-235">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="c4fcb-236">默认情况下， `Get-ChildItem` 显示父目录的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-236">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="c4fcb-237">**深度** 参数确定递归中包含的子目录级别数，并显示内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-237">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="c4fcb-238">例如， `Depth 2` 包括 **Path** 参数的目录、第一级子目录和二级子目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-238">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="c4fcb-239">默认情况下，输出中包含目录名称和文件名。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-239">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="c4fcb-240">在从 PowerShell 或 **cmd.exe** 的 Windows 计算机上，可以使用 **tree.com** 命令显示目录结构的图形视图。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-240">On a Windows computer from PowerShell or **cmd.exe**, you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-241">-Directory</span><span class="sxs-lookup"><span data-stu-id="c4fcb-241">-Directory</span></span>

<span data-ttu-id="c4fcb-242">若要获取目录列表，请使用 **directory** 参数或具有 **Directory** 属性的 **Attributes** 参数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-242">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="c4fcb-243">可以将 **递归** 参数与 **Directory** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-243">You can use the **Recurse** parameter with **Directory**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-244">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c4fcb-244">-Exclude</span></span>

<span data-ttu-id="c4fcb-245">指定为字符串数组，此 cmdlet 从操作中排除的属性或属性。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-245">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="c4fcb-246">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-246">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c4fcb-247">输入路径元素或模式，例如 `*.txt` 或 `A*` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-247">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="c4fcb-248">可接受通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-248">Wildcard characters are accepted.</span></span>

<span data-ttu-id="c4fcb-249">`*` **Path** 参数中)  (后缀星号是可选的。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-249">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="c4fcb-250">例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-250">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="c4fcb-251">如果包含尾随星号 (`*`) ，则命令 recurses 到 **Path** 参数的子目录中。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-251">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="c4fcb-252">如果没有星号 (`*`) ，则显示 **Path** 参数的内容。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-252">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="c4fcb-253">示例5和备注部分中提供了更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-253">More details are included in Example 5 and the Notes section.</span></span>

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

### <span data-ttu-id="c4fcb-254">-File</span><span class="sxs-lookup"><span data-stu-id="c4fcb-254">-File</span></span>

<span data-ttu-id="c4fcb-255">若要获取文件列表，请使用 **File** 参数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-255">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="c4fcb-256">可以将 **递归** 参数用于 **File**。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-256">You can use the **Recurse** parameter with **File**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-257">-Filter</span><span class="sxs-lookup"><span data-stu-id="c4fcb-257">-Filter</span></span>

<span data-ttu-id="c4fcb-258">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-258">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c4fcb-259">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一安装的支持筛选器的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-259">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="c4fcb-260">筛选器比其他参数更有效。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-260">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="c4fcb-261">当 cmdlet 获取对象时，提供程序将应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-261">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="c4fcb-262">筛选器字符串将传递给 .NET API 以枚举文件。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-262">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="c4fcb-263">API 仅支持 `*` 和 `?` 通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-263">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c4fcb-264">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="c4fcb-264">-FollowSymlink</span></span>

<span data-ttu-id="c4fcb-265">默认情况下，该 `Get-ChildItem` cmdlet 显示在递归期间找到的目录的符号链接，但不会对其进行递归。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-265">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="c4fcb-266">使用 **FollowSymlink** 参数可搜索以这些符号链接为目标的目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-266">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="c4fcb-267">**FollowSymlink** 是动态参数，仅 **FileSystem** 提供程序支持。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-267">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="c4fcb-268">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-268">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c4fcb-269">-Force</span><span class="sxs-lookup"><span data-stu-id="c4fcb-269">-Force</span></span>

<span data-ttu-id="c4fcb-270">允许 cmdlet 获取用户不能访问的项，如隐藏文件或系统文件。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-270">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="c4fcb-271">**Force** 参数不会覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-271">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="c4fcb-272">实现提供程序之间的差异。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-272">Implementation varies among providers.</span></span> <span data-ttu-id="c4fcb-273">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-273">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="c4fcb-274">-Hidden</span><span class="sxs-lookup"><span data-stu-id="c4fcb-274">-Hidden</span></span>

<span data-ttu-id="c4fcb-275">若要仅获取隐藏项，请使用 **hidden 参数或** 具有 **Hidden** 属性的 **Attributes** 参数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-275">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="c4fcb-276">默认情况下， `Get-ChildItem` 不会显示隐藏项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-276">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="c4fcb-277">使用 **Force** 参数可获取隐藏项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-277">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-278">-Include</span><span class="sxs-lookup"><span data-stu-id="c4fcb-278">-Include</span></span>

<span data-ttu-id="c4fcb-279">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-279">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c4fcb-280">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-280">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c4fcb-281">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-281">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c4fcb-282">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-282">Wildcard characters are permitted.</span></span> <span data-ttu-id="c4fcb-283">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-283">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c4fcb-284">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c4fcb-284">-LiteralPath</span></span>

<span data-ttu-id="c4fcb-285">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-285">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c4fcb-286">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-286">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="c4fcb-287">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-287">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c4fcb-288">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-288">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c4fcb-289">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-289">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c4fcb-290">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-290">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-291">-Name</span><span class="sxs-lookup"><span data-stu-id="c4fcb-291">-Name</span></span>

<span data-ttu-id="c4fcb-292">仅获取位置中的项的名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-292">Gets only the names of the items in the location.</span></span> <span data-ttu-id="c4fcb-293">输出是一个字符串对象，可将其向下发送到其他命令。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-293">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="c4fcb-294">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-294">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c4fcb-295">-Path</span><span class="sxs-lookup"><span data-stu-id="c4fcb-295">-Path</span></span>

<span data-ttu-id="c4fcb-296">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-296">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c4fcb-297">可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-297">Wildcards are accepted.</span></span> <span data-ttu-id="c4fcb-298">默认位置为当前目录 (`.`) 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-298">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c4fcb-299">-ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c4fcb-299">-ReadOnly</span></span>

<span data-ttu-id="c4fcb-300">若要仅获取只读项，请使用 **readonly** 参数或 **Attributes** 参数 **readonly** 属性。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-300">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-301">-Recurse</span><span class="sxs-lookup"><span data-stu-id="c4fcb-301">-Recurse</span></span>

<span data-ttu-id="c4fcb-302">获取指定位置及其所有子项中的项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-302">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-303">-System</span><span class="sxs-lookup"><span data-stu-id="c4fcb-303">-System</span></span>

<span data-ttu-id="c4fcb-304">仅获取系统文件和目录。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-304">Gets only system files and directories.</span></span> <span data-ttu-id="c4fcb-305">若要仅获取系统文件和文件夹，请使用 **system** 参数或 **Attributes** 参数 **系统** 属性。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-305">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4fcb-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4fcb-306">CommonParameters</span></span>

<span data-ttu-id="c4fcb-307">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4fcb-308">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4fcb-309">输入</span><span class="sxs-lookup"><span data-stu-id="c4fcb-309">INPUTS</span></span>

### <span data-ttu-id="c4fcb-310">System.String</span><span class="sxs-lookup"><span data-stu-id="c4fcb-310">System.String</span></span>

<span data-ttu-id="c4fcb-311">可以通过管道将包含路径的字符串传递给 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-311">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="c4fcb-312">输出</span><span class="sxs-lookup"><span data-stu-id="c4fcb-312">OUTPUTS</span></span>

### <span data-ttu-id="c4fcb-313">System.Object</span><span class="sxs-lookup"><span data-stu-id="c4fcb-313">System.Object</span></span>

<span data-ttu-id="c4fcb-314">返回的对象类型由 `Get-ChildItem` 提供程序驱动器路径中的对象确定。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-314">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="c4fcb-315">System.String</span><span class="sxs-lookup"><span data-stu-id="c4fcb-315">System.String</span></span>

<span data-ttu-id="c4fcb-316">如果使用 **Name** 参数，则 `Get-ChildItem` 以字符串形式返回对象名称。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-316">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="c4fcb-317">注释</span><span class="sxs-lookup"><span data-stu-id="c4fcb-317">NOTES</span></span>

- <span data-ttu-id="c4fcb-318">`Get-ChildItem` 可以使用任何内置的别名、、和来运行 `ls` `dir` `gci` 。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-318">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="c4fcb-319">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-319">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="c4fcb-320">`Get-ChildItem` 默认情况下不会获取隐藏项。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-320">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="c4fcb-321">若要获取隐藏项，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-321">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="c4fcb-322">`Get-ChildItem`Cmdlet 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-322">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c4fcb-323">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-323">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="c4fcb-324">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fcb-324">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c4fcb-325">相关链接</span><span class="sxs-lookup"><span data-stu-id="c4fcb-325">RELATED LINKS</span></span>

[<span data-ttu-id="c4fcb-326">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="c4fcb-326">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="c4fcb-327">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c4fcb-327">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c4fcb-328">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c4fcb-328">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c4fcb-329">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="c4fcb-329">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="c4fcb-330">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c4fcb-330">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="c4fcb-331">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="c4fcb-331">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="c4fcb-332">Get-Item</span><span class="sxs-lookup"><span data-stu-id="c4fcb-332">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c4fcb-333">Get-Location</span><span class="sxs-lookup"><span data-stu-id="c4fcb-333">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="c4fcb-334">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c4fcb-334">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="c4fcb-335">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="c4fcb-335">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="c4fcb-336">Split-Path</span><span class="sxs-lookup"><span data-stu-id="c4fcb-336">Split-Path</span></span>](Split-Path.md)

