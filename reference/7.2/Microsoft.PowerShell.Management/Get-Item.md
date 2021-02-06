---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "99596225"
---
# <span data-ttu-id="9a44d-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-102">Get-Item</span></span>

## <span data-ttu-id="9a44d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9a44d-103">SYNOPSIS</span></span>
<span data-ttu-id="9a44d-104">获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="9a44d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a44d-105">SYNTAX</span></span>

### <span data-ttu-id="9a44d-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="9a44d-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="9a44d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9a44d-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9a44d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a44d-108">DESCRIPTION</span></span>

<span data-ttu-id="9a44d-109">`Get-Item`Cmdlet 将获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="9a44d-110">除非使用通配符 (`*`) 请求该项的所有内容，否则它不会获取位于该位置的项的内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="9a44d-111">PowerShell 提供程序使用此 cmdlet 在不同类型的数据存储中导航。</span><span class="sxs-lookup"><span data-stu-id="9a44d-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="9a44d-112">示例</span><span class="sxs-lookup"><span data-stu-id="9a44d-112">EXAMPLES</span></span>

### <span data-ttu-id="9a44d-113">示例1：获取当前目录</span><span class="sxs-lookup"><span data-stu-id="9a44d-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="9a44d-114">此示例获取当前目录。</span><span class="sxs-lookup"><span data-stu-id="9a44d-114">This example gets the current directory.</span></span> <span data-ttu-id="9a44d-115">点 ( ".") 表示当前位置 (的项，而不) 内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="9a44d-116">示例2：获取当前目录中的所有项</span><span class="sxs-lookup"><span data-stu-id="9a44d-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="9a44d-117">此示例将获取当前目录中的所有项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="9a44d-118">通配符 (`*`) 表示当前项的所有内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="9a44d-119">示例3：获取驱动器的当前目录</span><span class="sxs-lookup"><span data-stu-id="9a44d-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="9a44d-120">此示例获取驱动器的当前目录 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="9a44d-121">检索到的对象仅表示目录，而不表示其内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="9a44d-122">示例4：获取指定驱动器中的项</span><span class="sxs-lookup"><span data-stu-id="9a44d-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="9a44d-123">此示例获取驱动器中的项 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="9a44d-124">通配符 (`*`) 表示容器中的所有项，而不仅仅是容器。</span><span class="sxs-lookup"><span data-stu-id="9a44d-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="9a44d-125">在 PowerShell 中，使用单个星号 (`*`) 来获取内容，而不是使用传统的 `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="9a44d-126">格式按原义解释，因此 `*.*` 不会检索不带句点的目录或文件名。</span><span class="sxs-lookup"><span data-stu-id="9a44d-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="9a44d-127">示例5：获取指定目录中的属性</span><span class="sxs-lookup"><span data-stu-id="9a44d-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="9a44d-128">此示例获取目录的 **LastAccessTime** 属性 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="9a44d-129">**LastAccessTime** 只是文件系统目录的一个属性。</span><span class="sxs-lookup"><span data-stu-id="9a44d-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="9a44d-130">若要查看目录的所有属性，请键入 `(Get-Item <directory-name>) | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="9a44d-131">示例6：显示注册表项的内容</span><span class="sxs-lookup"><span data-stu-id="9a44d-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="9a44d-132">此示例显示了 **Microsoft PowerShell** 注册表项的内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="9a44d-133">可以将此 cmdlet 与 PowerShell 注册表提供程序结合使用来获取注册表项和子项，但必须使用 `Get-ItemProperty` cmdlet 来获取注册表值和数据。</span><span class="sxs-lookup"><span data-stu-id="9a44d-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="9a44d-134">示例7：获取目录中具有排除项的项</span><span class="sxs-lookup"><span data-stu-id="9a44d-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="9a44d-135">此示例获取 Windows 目录中名称中包含点 () 的项 `.` ，但不以开头 `w*` 。此示例仅在以下情况下有效：该路径包括 () 的通配符 `*` ，以指定项的内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="9a44d-136">示例8：获取硬链接信息</span><span class="sxs-lookup"><span data-stu-id="9a44d-136">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="9a44d-137">在 PowerShell 6.2 中，添加了一个替代视图来获取硬链接信息。</span><span class="sxs-lookup"><span data-stu-id="9a44d-137">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="9a44d-138">若要获取硬链接信息，请通过管道将输出传递给 `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="9a44d-138">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="9a44d-139">示例9：非 Windows 操作系统的输出</span><span class="sxs-lookup"><span data-stu-id="9a44d-139">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="9a44d-140">在 Unix 系统上的 PowerShell 7.1 中， `Get-Item` cmdlet 提供类似于 unix 的输出：</span><span class="sxs-lookup"><span data-stu-id="9a44d-140">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="9a44d-141">现在作为输出的一部分的新属性包括：</span><span class="sxs-lookup"><span data-stu-id="9a44d-141">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="9a44d-142">**UnixMode** 是 Unix 系统上表示的文件权限</span><span class="sxs-lookup"><span data-stu-id="9a44d-142">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="9a44d-143">**用户** 是文件所有者</span><span class="sxs-lookup"><span data-stu-id="9a44d-143">**User** is the file owner</span></span>
- <span data-ttu-id="9a44d-144">**组** 是组的所有者</span><span class="sxs-lookup"><span data-stu-id="9a44d-144">**Group** is the group owner</span></span>
- <span data-ttu-id="9a44d-145">**Size** 是在 Unix 系统上表示的文件或目录的大小</span><span class="sxs-lookup"><span data-stu-id="9a44d-145">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="9a44d-146">此功能已从实验迁移到 PowerShell 7.1 中的主流。</span><span class="sxs-lookup"><span data-stu-id="9a44d-146">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="9a44d-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a44d-147">PARAMETERS</span></span>

### <span data-ttu-id="9a44d-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="9a44d-148">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="9a44d-149">此参数仅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="9a44d-149">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="9a44d-150">从文件中获取指定的备用数据流。</span><span class="sxs-lookup"><span data-stu-id="9a44d-150">Gets the specified alternative data stream from the file.</span></span> <span data-ttu-id="9a44d-151">输入流名称。</span><span class="sxs-lookup"><span data-stu-id="9a44d-151">Enter the stream name.</span></span> <span data-ttu-id="9a44d-152">支持通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-152">Wildcards are supported.</span></span> <span data-ttu-id="9a44d-153">若要获取所有流，请使用星号 (`*`) 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-153">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="9a44d-154">此参数在目录中有效，但请注意，默认情况下目录不具有数据流。</span><span class="sxs-lookup"><span data-stu-id="9a44d-154">This parameter is valid on directories, but note that directories do not have data streams by default.</span></span>

<span data-ttu-id="9a44d-155">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="9a44d-155">This parameter was introduced in PowerShell 3.0.</span></span>  <span data-ttu-id="9a44d-156">从 PowerShell 7.2 开始， `Get-Item` 可以从目录和文件获取备用数据流。</span><span class="sxs-lookup"><span data-stu-id="9a44d-156">As of PowerShell 7.2, `Get-Item` can get alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="9a44d-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="9a44d-157">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9a44d-158">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="9a44d-158">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9a44d-159">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="9a44d-159">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9a44d-160">-Exclude</span><span class="sxs-lookup"><span data-stu-id="9a44d-160">-Exclude</span></span>

<span data-ttu-id="9a44d-161">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-161">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9a44d-162">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="9a44d-162">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9a44d-163">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="9a44d-163">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9a44d-164">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-164">Wildcard characters are permitted.</span></span> <span data-ttu-id="9a44d-165">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-165">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9a44d-166">-Filter</span><span class="sxs-lookup"><span data-stu-id="9a44d-166">-Filter</span></span>

<span data-ttu-id="9a44d-167">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="9a44d-167">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9a44d-168">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一安装的支持筛选器的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="9a44d-168">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="9a44d-169">筛选器比其他参数更有效。</span><span class="sxs-lookup"><span data-stu-id="9a44d-169">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="9a44d-170">当 cmdlet 获取对象时，提供程序将应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="9a44d-170">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="9a44d-171">筛选器字符串将传递给 .NET API 以枚举文件。</span><span class="sxs-lookup"><span data-stu-id="9a44d-171">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="9a44d-172">API 仅支持 `*` 和 `?` 通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-172">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="9a44d-173">-Force</span><span class="sxs-lookup"><span data-stu-id="9a44d-173">-Force</span></span>

<span data-ttu-id="9a44d-174">指示此 cmdlet 将获取不能访问的项，如隐藏项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-174">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="9a44d-175">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="9a44d-175">Implementation varies from provider to provider.</span></span> <span data-ttu-id="9a44d-176">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9a44d-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="9a44d-177">即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="9a44d-177">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="9a44d-178">-Include</span><span class="sxs-lookup"><span data-stu-id="9a44d-178">-Include</span></span>

<span data-ttu-id="9a44d-179">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="9a44d-179">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9a44d-180">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="9a44d-180">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9a44d-181">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="9a44d-181">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9a44d-182">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="9a44d-183">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-183">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9a44d-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9a44d-184">-LiteralPath</span></span>

<span data-ttu-id="9a44d-185">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="9a44d-185">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9a44d-186">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="9a44d-186">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="9a44d-187">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-187">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9a44d-188">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="9a44d-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9a44d-189">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="9a44d-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9a44d-190">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="9a44d-190">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="9a44d-191">-Path</span><span class="sxs-lookup"><span data-stu-id="9a44d-191">-Path</span></span>

<span data-ttu-id="9a44d-192">指定项的路径。</span><span class="sxs-lookup"><span data-stu-id="9a44d-192">Specifies the path to an item.</span></span> <span data-ttu-id="9a44d-193">此 cmdlet 获取位于指定位置的项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-193">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="9a44d-194">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9a44d-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="9a44d-195">此参数是必需的，但参数名称 **路径** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="9a44d-195">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="9a44d-196">使用点)  (`.` 指定当前位置。</span><span class="sxs-lookup"><span data-stu-id="9a44d-196">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="9a44d-197">使用通配符 (`*`) 来指定当前位置中的所有项。</span><span class="sxs-lookup"><span data-stu-id="9a44d-197">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="9a44d-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a44d-198">CommonParameters</span></span>

<span data-ttu-id="9a44d-199">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9a44d-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a44d-200">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9a44d-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a44d-201">输入</span><span class="sxs-lookup"><span data-stu-id="9a44d-201">INPUTS</span></span>

### <span data-ttu-id="9a44d-202">System.String</span><span class="sxs-lookup"><span data-stu-id="9a44d-202">System.String</span></span>

<span data-ttu-id="9a44d-203">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a44d-203">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="9a44d-204">输出</span><span class="sxs-lookup"><span data-stu-id="9a44d-204">OUTPUTS</span></span>

### <span data-ttu-id="9a44d-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="9a44d-205">System.Object</span></span>

<span data-ttu-id="9a44d-206">此 cmdlet 将返回它所获取的对象。</span><span class="sxs-lookup"><span data-stu-id="9a44d-206">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="9a44d-207">类型由路径中的对象的类型确定。</span><span class="sxs-lookup"><span data-stu-id="9a44d-207">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="9a44d-208">注释</span><span class="sxs-lookup"><span data-stu-id="9a44d-208">NOTES</span></span>

<span data-ttu-id="9a44d-209">此 cmdlet 不具有 **递归** 参数，因为它只获取项，而不获取其内容。</span><span class="sxs-lookup"><span data-stu-id="9a44d-209">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="9a44d-210">若要以递归方式获取项的内容，请使用 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="9a44d-210">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="9a44d-211">若要在注册表中导航，请使用此 cmdlet 获取注册表项，并使用 `Get-ItemProperty` 来获取注册表值和数据。</span><span class="sxs-lookup"><span data-stu-id="9a44d-211">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="9a44d-212">注册表值被视为注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="9a44d-212">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="9a44d-213">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="9a44d-213">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9a44d-214">若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="9a44d-214">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="9a44d-215">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9a44d-215">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9a44d-216">相关链接</span><span class="sxs-lookup"><span data-stu-id="9a44d-216">RELATED LINKS</span></span>

[<span data-ttu-id="9a44d-217">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-217">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="9a44d-218">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-218">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="9a44d-219">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-219">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="9a44d-220">Move-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-220">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="9a44d-221">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-221">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="9a44d-222">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-222">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="9a44d-223">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-223">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="9a44d-224">Set-Item</span><span class="sxs-lookup"><span data-stu-id="9a44d-224">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="9a44d-225">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9a44d-225">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="9a44d-226">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9a44d-226">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="9a44d-227">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="9a44d-227">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="9a44d-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9a44d-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

