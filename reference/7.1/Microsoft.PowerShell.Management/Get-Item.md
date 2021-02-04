---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: d034baf42f064149696f54a198dc97d7ee4e8fe7
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693079"
---
# <span data-ttu-id="d09f4-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-103">Get-Item</span></span>

## <span data-ttu-id="d09f4-104">摘要</span><span class="sxs-lookup"><span data-stu-id="d09f4-104">SYNOPSIS</span></span>
<span data-ttu-id="d09f4-105">获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="d09f4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d09f4-106">SYNTAX</span></span>

### <span data-ttu-id="d09f4-107">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="d09f4-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d09f4-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d09f4-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d09f4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d09f4-109">DESCRIPTION</span></span>

<span data-ttu-id="d09f4-110">`Get-Item`Cmdlet 将获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="d09f4-111">除非使用通配符 (`*`) 请求该项的所有内容，否则它不会获取位于该位置的项的内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="d09f4-112">PowerShell 提供程序使用此 cmdlet 在不同类型的数据存储中导航。</span><span class="sxs-lookup"><span data-stu-id="d09f4-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="d09f4-113">示例</span><span class="sxs-lookup"><span data-stu-id="d09f4-113">EXAMPLES</span></span>

### <span data-ttu-id="d09f4-114">示例1：获取当前目录</span><span class="sxs-lookup"><span data-stu-id="d09f4-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="d09f4-115">此示例获取当前目录。</span><span class="sxs-lookup"><span data-stu-id="d09f4-115">This example gets the current directory.</span></span> <span data-ttu-id="d09f4-116">点 ( ".") 表示当前位置 (的项，而不) 内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="d09f4-117">示例2：获取当前目录中的所有项</span><span class="sxs-lookup"><span data-stu-id="d09f4-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="d09f4-118">此示例将获取当前目录中的所有项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="d09f4-119">通配符 (`*`) 表示当前项的所有内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="d09f4-120">示例3：获取驱动器的当前目录</span><span class="sxs-lookup"><span data-stu-id="d09f4-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="d09f4-121">此示例获取驱动器的当前目录 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="d09f4-122">检索到的对象仅表示目录，而不表示其内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="d09f4-123">示例4：获取指定驱动器中的项</span><span class="sxs-lookup"><span data-stu-id="d09f4-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="d09f4-124">此示例获取驱动器中的项 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="d09f4-125">通配符 (`*`) 表示容器中的所有项，而不仅仅是容器。</span><span class="sxs-lookup"><span data-stu-id="d09f4-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="d09f4-126">在 PowerShell 中，使用单个星号 (`*`) 来获取内容，而不是使用传统的 `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="d09f4-127">格式按原义解释，因此 `*.*` 不会检索不带句点的目录或文件名。</span><span class="sxs-lookup"><span data-stu-id="d09f4-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="d09f4-128">示例5：获取指定目录中的属性</span><span class="sxs-lookup"><span data-stu-id="d09f4-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="d09f4-129">此示例获取目录的 **LastAccessTime** 属性 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="d09f4-130">**LastAccessTime** 只是文件系统目录的一个属性。</span><span class="sxs-lookup"><span data-stu-id="d09f4-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="d09f4-131">若要查看目录的所有属性，请键入 `(Get-Item <directory-name>) | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="d09f4-132">示例6：显示注册表项的内容</span><span class="sxs-lookup"><span data-stu-id="d09f4-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="d09f4-133">此示例显示了 **Microsoft PowerShell** 注册表项的内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="d09f4-134">可以将此 cmdlet 与 PowerShell 注册表提供程序结合使用来获取注册表项和子项，但必须使用 `Get-ItemProperty` cmdlet 来获取注册表值和数据。</span><span class="sxs-lookup"><span data-stu-id="d09f4-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="d09f4-135">示例7：获取目录中具有排除项的项</span><span class="sxs-lookup"><span data-stu-id="d09f4-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="d09f4-136">此示例获取 Windows 目录中名称中包含点 () 的项 `.` ，但不以开头 `w*` 。此示例仅在以下情况下有效：该路径包括 () 的通配符 `*` ，以指定项的内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="d09f4-137">示例8：获取硬链接信息</span><span class="sxs-lookup"><span data-stu-id="d09f4-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="d09f4-138">在 PowerShell 6.2 中，添加了一个替代视图来获取硬链接信息。</span><span class="sxs-lookup"><span data-stu-id="d09f4-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="d09f4-139">若要获取硬链接信息，请通过管道将输出传递给 `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="d09f4-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="d09f4-140">示例9：非 Windows 操作系统的输出</span><span class="sxs-lookup"><span data-stu-id="d09f4-140">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="d09f4-141">在 Unix 系统上的 PowerShell 7.1 中， `Get-Item` cmdlet 提供类似于 unix 的输出：</span><span class="sxs-lookup"><span data-stu-id="d09f4-141">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="d09f4-142">现在作为输出的一部分的新属性包括：</span><span class="sxs-lookup"><span data-stu-id="d09f4-142">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="d09f4-143">**UnixMode** 是 Unix 系统上表示的文件权限</span><span class="sxs-lookup"><span data-stu-id="d09f4-143">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="d09f4-144">**用户** 是文件所有者</span><span class="sxs-lookup"><span data-stu-id="d09f4-144">**User** is the file owner</span></span>
- <span data-ttu-id="d09f4-145">**组** 是组的所有者</span><span class="sxs-lookup"><span data-stu-id="d09f4-145">**Group** is the group owner</span></span>
- <span data-ttu-id="d09f4-146">**Size** 是在 Unix 系统上表示的文件或目录的大小</span><span class="sxs-lookup"><span data-stu-id="d09f4-146">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="d09f4-147">此功能已从实验迁移到 PowerShell 7.1 中的主流。</span><span class="sxs-lookup"><span data-stu-id="d09f4-147">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="d09f4-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d09f4-148">PARAMETERS</span></span>

### <span data-ttu-id="d09f4-149">-Stream</span><span class="sxs-lookup"><span data-stu-id="d09f4-149">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="d09f4-150">此参数仅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="d09f4-150">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="d09f4-151">从文件获取指定的备用 NTFS 文件流。</span><span class="sxs-lookup"><span data-stu-id="d09f4-151">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="d09f4-152">输入流名称。</span><span class="sxs-lookup"><span data-stu-id="d09f4-152">Enter the stream name.</span></span> <span data-ttu-id="d09f4-153">支持通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-153">Wildcards are supported.</span></span> <span data-ttu-id="d09f4-154">若要获取所有流，请使用星号 (`*`) 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-154">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="d09f4-155">此参数在文件夹上无效。</span><span class="sxs-lookup"><span data-stu-id="d09f4-155">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="d09f4-156">**Stream** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-156">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="d09f4-157">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="d09f4-157">This parameter works only in file system drives.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d09f4-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="d09f4-158">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d09f4-159">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="d09f4-159">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d09f4-160">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="d09f4-160">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d09f4-161">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d09f4-161">-Exclude</span></span>

<span data-ttu-id="d09f4-162">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-162">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="d09f4-163">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="d09f4-163">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d09f4-164">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="d09f4-164">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="d09f4-165">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-165">Wildcard characters are permitted.</span></span> <span data-ttu-id="d09f4-166">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-166">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d09f4-167">-Filter</span><span class="sxs-lookup"><span data-stu-id="d09f4-167">-Filter</span></span>

<span data-ttu-id="d09f4-168">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d09f4-168">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="d09f4-169">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一安装的支持筛选器的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d09f4-169">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="d09f4-170">筛选器比其他参数更有效。</span><span class="sxs-lookup"><span data-stu-id="d09f4-170">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="d09f4-171">当 cmdlet 获取对象时，提供程序将应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="d09f4-171">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="d09f4-172">筛选器字符串将传递给 .NET API 以枚举文件。</span><span class="sxs-lookup"><span data-stu-id="d09f4-172">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="d09f4-173">API 仅支持 `*` 和 `?` 通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-173">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="d09f4-174">-Force</span><span class="sxs-lookup"><span data-stu-id="d09f4-174">-Force</span></span>

<span data-ttu-id="d09f4-175">指示此 cmdlet 将获取不能访问的项，如隐藏项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-175">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="d09f4-176">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="d09f4-176">Implementation varies from provider to provider.</span></span> <span data-ttu-id="d09f4-177">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="d09f4-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="d09f4-178">即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="d09f4-178">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="d09f4-179">-Include</span><span class="sxs-lookup"><span data-stu-id="d09f4-179">-Include</span></span>

<span data-ttu-id="d09f4-180">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="d09f4-180">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="d09f4-181">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="d09f4-181">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d09f4-182">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="d09f4-182">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="d09f4-183">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-183">Wildcard characters are permitted.</span></span> <span data-ttu-id="d09f4-184">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-184">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d09f4-185">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d09f4-185">-LiteralPath</span></span>

<span data-ttu-id="d09f4-186">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="d09f4-186">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d09f4-187">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="d09f4-187">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="d09f4-188">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-188">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d09f4-189">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="d09f4-189">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d09f4-190">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="d09f4-190">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="d09f4-191">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="d09f4-191">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d09f4-192">-Path</span><span class="sxs-lookup"><span data-stu-id="d09f4-192">-Path</span></span>

<span data-ttu-id="d09f4-193">指定项的路径。</span><span class="sxs-lookup"><span data-stu-id="d09f4-193">Specifies the path to an item.</span></span> <span data-ttu-id="d09f4-194">此 cmdlet 获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-194">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="d09f4-195">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d09f4-195">Wildcard characters are permitted.</span></span> <span data-ttu-id="d09f4-196">此参数是必需的，但参数名称 **路径** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="d09f4-196">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="d09f4-197">使用点)  (`.` 指定当前位置。</span><span class="sxs-lookup"><span data-stu-id="d09f4-197">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="d09f4-198">使用通配符 (`*`) 来指定当前位置中的所有项。</span><span class="sxs-lookup"><span data-stu-id="d09f4-198">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="d09f4-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d09f4-199">CommonParameters</span></span>

<span data-ttu-id="d09f4-200">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d09f4-201">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="d09f4-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d09f4-202">输入</span><span class="sxs-lookup"><span data-stu-id="d09f4-202">INPUTS</span></span>

### <span data-ttu-id="d09f4-203">System.String</span><span class="sxs-lookup"><span data-stu-id="d09f4-203">System.String</span></span>

<span data-ttu-id="d09f4-204">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d09f4-204">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="d09f4-205">输出</span><span class="sxs-lookup"><span data-stu-id="d09f4-205">OUTPUTS</span></span>

### <span data-ttu-id="d09f4-206">System.Object</span><span class="sxs-lookup"><span data-stu-id="d09f4-206">System.Object</span></span>

<span data-ttu-id="d09f4-207">此 cmdlet 将返回它所获取的对象。</span><span class="sxs-lookup"><span data-stu-id="d09f4-207">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="d09f4-208">类型由路径中的对象的类型确定。</span><span class="sxs-lookup"><span data-stu-id="d09f4-208">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="d09f4-209">注释</span><span class="sxs-lookup"><span data-stu-id="d09f4-209">NOTES</span></span>

<span data-ttu-id="d09f4-210">此 cmdlet 不具有 **递归** 参数，因为它只获取项，而不获取其内容。</span><span class="sxs-lookup"><span data-stu-id="d09f4-210">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="d09f4-211">若要以递归方式获取项的内容，请使用 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="d09f4-211">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="d09f4-212">若要在注册表中导航，请使用此 cmdlet 获取注册表项，并使用 `Get-ItemProperty` 来获取注册表值和数据。</span><span class="sxs-lookup"><span data-stu-id="d09f4-212">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="d09f4-213">注册表值被视为注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="d09f4-213">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="d09f4-214">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="d09f4-214">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d09f4-215">若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="d09f4-215">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="d09f4-216">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="d09f4-216">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d09f4-217">相关链接</span><span class="sxs-lookup"><span data-stu-id="d09f4-217">RELATED LINKS</span></span>

[<span data-ttu-id="d09f4-218">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-218">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="d09f4-219">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-219">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="d09f4-220">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-220">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="d09f4-221">Move-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-221">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="d09f4-222">New-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-222">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="d09f4-223">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-223">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="d09f4-224">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-224">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="d09f4-225">Set-Item</span><span class="sxs-lookup"><span data-stu-id="d09f4-225">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="d09f4-226">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d09f4-226">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="d09f4-227">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d09f4-227">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d09f4-228">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d09f4-228">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="d09f4-229">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d09f4-229">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

