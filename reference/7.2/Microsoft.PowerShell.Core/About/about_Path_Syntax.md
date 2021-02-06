---
description: 描述 PowerShell 中的完整和相对路径名称格式。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 9a95865d67dc15bf79762987622b702b14faf6c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596447"
---
# <a name="about-path-syntax"></a><span data-ttu-id="a7e77-103">关于路径语法</span><span class="sxs-lookup"><span data-stu-id="a7e77-103">About Path Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="a7e77-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="a7e77-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a7e77-105">描述 PowerShell 中的完整和相对路径名称格式。</span><span class="sxs-lookup"><span data-stu-id="a7e77-105">Describes the full and relative path name formats in  PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a7e77-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="a7e77-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a7e77-107">可通过 PowerShell 提供程序访问的数据存储区中的所有项都可以通过其路径名称进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="a7e77-107">All items in a data store accessible through a PowerShell provider can be uniquely identified by their path names.</span></span> <span data-ttu-id="a7e77-108">路径名称是项名称、项所在的容器和子容器以及用于访问这些容器的 PowerShell 驱动器的组合。</span><span class="sxs-lookup"><span data-stu-id="a7e77-108">A path name is a combination of the item name, the container and subcontainers in which the item is located, and the PowerShell drive through which the containers are accessed.</span></span>

<span data-ttu-id="a7e77-109">在 PowerShell 中，路径名分为以下两种类型之一：完全限定的名称和相对路径。</span><span class="sxs-lookup"><span data-stu-id="a7e77-109">In PowerShell, path names are divided into one of two types: fully qualified and relative.</span></span> <span data-ttu-id="a7e77-110">完全限定的路径名称包含构成路径的所有元素。</span><span class="sxs-lookup"><span data-stu-id="a7e77-110">A fully qualified path name consists of all elements that make up a path.</span></span> <span data-ttu-id="a7e77-111">以下语法显示了完全限定的路径名称中的元素：</span><span class="sxs-lookup"><span data-stu-id="a7e77-111">The following syntax shows the elements in a fully qualified path name:</span></span>

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

<span data-ttu-id="a7e77-112">\<provider\>占位符指的是用于访问数据存储区的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="a7e77-112">The \<provider\> placeholder refers to the PowerShell provider through which you access the data store.</span></span> <span data-ttu-id="a7e77-113">例如，FileSystem 提供程序允许你访问计算机上的文件和目录。</span><span class="sxs-lookup"><span data-stu-id="a7e77-113">For example, the FileSystem provider allows you to access the files and directories on your computer.</span></span> <span data-ttu-id="a7e77-114">语法的此元素是可选的，并且永远不需要，因为驱动器名称在所有提供程序中都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a7e77-114">This element of the syntax is optional and is never needed because the drive names are unique across all providers.</span></span>

<span data-ttu-id="a7e77-115">\<drive\>占位符指特定 powershell 提供程序支持的 powershell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="a7e77-115">The \<drive\> placeholder refers to the PowerShell drive that is supported by a particular PowerShell provider.</span></span> <span data-ttu-id="a7e77-116">对于 FileSystem 提供程序，PowerShell 驱动器将映射到在系统上配置的 Windows 驱动器。</span><span class="sxs-lookup"><span data-stu-id="a7e77-116">In the case of the FileSystem provider, the PowerShell drives map to the Windows drives that are configured on your system.</span></span> <span data-ttu-id="a7e77-117">例如，如果你的系统包含 A：驱动器和 C：驱动器，则 FileSystem 提供程序会在 PowerShell 中创建相同的驱动器。</span><span class="sxs-lookup"><span data-stu-id="a7e77-117">For example, if your system includes an A: drive and a C: drive, the FileSystem provider creates the same drives in PowerShell.</span></span>

<span data-ttu-id="a7e77-118">指定驱动器后，必须指定包含项的任何容器和子容器。</span><span class="sxs-lookup"><span data-stu-id="a7e77-118">After you have specified the drive, you must specify any containers and subcontainers that contain the item.</span></span> <span data-ttu-id="a7e77-119">容器必须按照其在数据存储中的存在的层次结构顺序来指定。</span><span class="sxs-lookup"><span data-stu-id="a7e77-119">The containers must be specified in the hierarchical order in which they exist in the data store.</span></span> <span data-ttu-id="a7e77-120">换句话说，您必须从父容器开始，然后是该父容器中的子容器，依此类推。</span><span class="sxs-lookup"><span data-stu-id="a7e77-120">In other words, you must start with the parent container, then the child container in that parent container, and so on.</span></span> <span data-ttu-id="a7e77-121">此外，每个容器前面必须加上一个反斜杠。</span><span class="sxs-lookup"><span data-stu-id="a7e77-121">In addition, each container must be preceded by a backslash.</span></span> <span data-ttu-id="a7e77-122"> (请注意，PowerShell 允许使用正斜杠与其他 PowerShells 的兼容性 ) </span><span class="sxs-lookup"><span data-stu-id="a7e77-122">(Note that PowerShell allows you to use forward slashes for compatibility with other PowerShells.)</span></span>

<span data-ttu-id="a7e77-123">指定容器和子容器后，必须提供前面带有反斜杠的项目名称。</span><span class="sxs-lookup"><span data-stu-id="a7e77-123">After the container and subcontainers have been specified, you must provide the item name, preceded by a backslash.</span></span> <span data-ttu-id="a7e77-124">例如，C： Windows System32 目录中 Shell.dll 文件的完全限定路径名称 \\ \\ 如下：</span><span class="sxs-lookup"><span data-stu-id="a7e77-124">For example, the fully qualified path name for the Shell.dll file in the C:\\Windows\\System32 directory is as follows:</span></span>

```powershell
C:\Windows\System32\Shell.dll
```

<span data-ttu-id="a7e77-125">在这种情况下，访问容器所使用的驱动器是 C：驱动器，顶级容器是 Windows，subcontainer 是位于 Windows 容器) 内的 System32 (，该项是 Shell.dll 的。</span><span class="sxs-lookup"><span data-stu-id="a7e77-125">In this case, the drive through which the containers are accessed is the C: drive, the top-level container is Windows, the subcontainer is System32 (located within the Windows container), and the item is Shell.dll.</span></span>

<span data-ttu-id="a7e77-126">在某些情况下，不需要指定完全限定的路径名称，而是可以使用相对路径名称。</span><span class="sxs-lookup"><span data-stu-id="a7e77-126">In some situations, you do not need to specify a fully qualified path name and can instead use a relative path name.</span></span> <span data-ttu-id="a7e77-127">相对路径名称基于当前工作位置。</span><span class="sxs-lookup"><span data-stu-id="a7e77-127">A relative path name is based on the current working location.</span></span> <span data-ttu-id="a7e77-128">PowerShell 允许您根据项相对于当前工作位置的位置来标识项。</span><span class="sxs-lookup"><span data-stu-id="a7e77-128">PowerShell allows you to identify an item based on its location relative to the current working location.</span></span> <span data-ttu-id="a7e77-129">您可以通过使用特殊字符来指定相对路径名称。</span><span class="sxs-lookup"><span data-stu-id="a7e77-129">You can specify relative path names by using special characters.</span></span> <span data-ttu-id="a7e77-130">下表对其中每个字符进行了说明，并提供了相对路径名称和完全限定的路径名称的示例。</span><span class="sxs-lookup"><span data-stu-id="a7e77-130">The following table describes each of these characters and provides examples of relative path names and fully qualified path names.</span></span> <span data-ttu-id="a7e77-131">表中的示例基于要设置为 C:\windows。的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="a7e77-131">The examples in the table are based on the current working directory being set to C:\Windows.</span></span>

|<span data-ttu-id="a7e77-132">符号</span><span class="sxs-lookup"><span data-stu-id="a7e77-132">Symbol</span></span>|<span data-ttu-id="a7e77-133">说明</span><span class="sxs-lookup"><span data-stu-id="a7e77-133">Description</span></span>               |<span data-ttu-id="a7e77-134">相对路径</span><span class="sxs-lookup"><span data-stu-id="a7e77-134">Relative path</span></span>    |<span data-ttu-id="a7e77-135">完整路径</span><span class="sxs-lookup"><span data-stu-id="a7e77-135">Full path</span></span>          |
|------|--------------------------|-----------------|-------------------|
|<span data-ttu-id="a7e77-136">.</span><span class="sxs-lookup"><span data-stu-id="a7e77-136">.</span></span>     |<span data-ttu-id="a7e77-137">当前位置</span><span class="sxs-lookup"><span data-stu-id="a7e77-137">Current location</span></span>          |<span data-ttu-id="a7e77-138">.\\主板</span><span class="sxs-lookup"><span data-stu-id="a7e77-138">.\\System</span></span>        |<span data-ttu-id="a7e77-139">c： \\ Windows \\ 系统</span><span class="sxs-lookup"><span data-stu-id="a7e77-139">c:\\Windows\\System</span></span>|
|<span data-ttu-id="a7e77-140">..</span><span class="sxs-lookup"><span data-stu-id="a7e77-140">..</span></span>    |<span data-ttu-id="a7e77-141">当前位置的父级</span><span class="sxs-lookup"><span data-stu-id="a7e77-141">Parent of current location</span></span>|<span data-ttu-id="a7e77-142">..\\程序文件</span><span class="sxs-lookup"><span data-stu-id="a7e77-142">..\\Program Files</span></span>|<span data-ttu-id="a7e77-143">c： \\ Program 文件</span><span class="sxs-lookup"><span data-stu-id="a7e77-143">c:\\Program Files</span></span>  |
|\     |<span data-ttu-id="a7e77-144">当前的驱动器根</span><span class="sxs-lookup"><span data-stu-id="a7e77-144">Drive root of current</span></span>     |<span data-ttu-id="a7e77-145">\\程序文件</span><span class="sxs-lookup"><span data-stu-id="a7e77-145">\\Program Files</span></span>  |<span data-ttu-id="a7e77-146">c： \\ Program 文件</span><span class="sxs-lookup"><span data-stu-id="a7e77-146">c:\\Program Files</span></span>  |
|      |<span data-ttu-id="a7e77-147">location</span><span class="sxs-lookup"><span data-stu-id="a7e77-147">location</span></span>                  |                 |                   |
|<span data-ttu-id="a7e77-148">内容</span><span class="sxs-lookup"><span data-stu-id="a7e77-148">[none]</span></span>|<span data-ttu-id="a7e77-149">无特殊字符</span><span class="sxs-lookup"><span data-stu-id="a7e77-149">No special characters</span></span>     |<span data-ttu-id="a7e77-150">系统</span><span class="sxs-lookup"><span data-stu-id="a7e77-150">System</span></span>           |<span data-ttu-id="a7e77-151">c： \\ Windows \\ 系统</span><span class="sxs-lookup"><span data-stu-id="a7e77-151">c:\\Windows\\System</span></span>|

<span data-ttu-id="a7e77-152">在命令中使用路径名时，输入该名称的方式与使用完全限定的路径名称或相对路径名称的方式相同。</span><span class="sxs-lookup"><span data-stu-id="a7e77-152">When using a path name in a command, you enter that name in the same way whether you use a fully qualified path name or a relative one.</span></span> <span data-ttu-id="a7e77-153">例如，假设当前工作目录为 C:\windows。</span><span class="sxs-lookup"><span data-stu-id="a7e77-153">For example, suppose that your current working directory is C:\Windows.</span></span> <span data-ttu-id="a7e77-154">以下 Get-ChildItem 命令将检索 C:\Techdocs 目录中的所有项：</span><span class="sxs-lookup"><span data-stu-id="a7e77-154">The following Get-ChildItem command retrieves all items in the C:\Techdocs directory:</span></span>

```powershell
Get-ChildItem \techdocs
```

<span data-ttu-id="a7e77-155">反斜杠指示应该使用当前工作位置的驱动器根目录。</span><span class="sxs-lookup"><span data-stu-id="a7e77-155">The backslash indicates that the drive root of the current working location should be used.</span></span> <span data-ttu-id="a7e77-156">由于工作目录为 C： \\ Windows，因此驱动器根为 c：驱动器。</span><span class="sxs-lookup"><span data-stu-id="a7e77-156">Because the working directory is C:\\Windows, the drive root is the C: drive.</span></span> <span data-ttu-id="a7e77-157">由于 techdocs 目录位于根位置，因此只需指定反斜杠。</span><span class="sxs-lookup"><span data-stu-id="a7e77-157">Because the techdocs directory is located off the root, you need to specify only the backslash.</span></span>

<span data-ttu-id="a7e77-158">可以使用以下命令获得相同的结果：</span><span class="sxs-lookup"><span data-stu-id="a7e77-158">You can achieve the same results by using the following command:</span></span>

```powershell
Get-ChildItem c:\techdocs
```

<span data-ttu-id="a7e77-159">无论是使用完全限定的路径名称还是相对路径名称，路径名都非常重要，因为它会查找项，但它也是唯一标识项，即使该项与其他容器中的另一项共享同一名称也是如此。</span><span class="sxs-lookup"><span data-stu-id="a7e77-159">Regardless of whether you use a fully qualified path name or a relative path name, a path name is important not only because it locates an item but also because it uniquely identifies the item even if that item shares the same name as another item in a different container.</span></span>

<span data-ttu-id="a7e77-160">例如，假设您有两个分别名为 Results.txt 的文件。</span><span class="sxs-lookup"><span data-stu-id="a7e77-160">For instance, suppose that you have two files that are each named Results.txt.</span></span>
<span data-ttu-id="a7e77-161">第一个文件位于名为 C： Techdocs Jan 的目录中 \\ \\ ，第二个文件位于名为 c： Techdocs 的目录中 \\ \\ 。第一个文件 (C： \\ Techdocs \\ JanResults.txt) 的路径名称 \\ ，第二个文件的路径名称 (c： \\ Techdocs \\ 2 月 \\Results.txt) 使你可以清楚地区分这两个文件。</span><span class="sxs-lookup"><span data-stu-id="a7e77-161">The first file is in a directory named C:\\Techdocs\\Jan, and the second file is in a directory named C:\\Techdocs\\Feb. The path name for the first file (C:\\Techdocs\\Jan\\Results.txt) and the path name for the second file (C:\\Techdocs\\Feb\\Results.txt) allow you to clearly distinguish between the two files.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7e77-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7e77-162">SEE ALSO</span></span>

[<span data-ttu-id="a7e77-163">about_Locations</span><span class="sxs-lookup"><span data-stu-id="a7e77-163">about_Locations</span></span>](about_Locations.md)

