---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 08107eecce316c3799315b1d91a0e7cdab64579f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596644"
---
# <span data-ttu-id="90585-102">Join-Path</span><span class="sxs-lookup"><span data-stu-id="90585-102">Join-Path</span></span>

## <span data-ttu-id="90585-103">摘要</span><span class="sxs-lookup"><span data-stu-id="90585-103">SYNOPSIS</span></span>
<span data-ttu-id="90585-104">将路径和子路径合并到单个路径中。</span><span class="sxs-lookup"><span data-stu-id="90585-104">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="90585-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90585-105">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="90585-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="90585-106">DESCRIPTION</span></span>

<span data-ttu-id="90585-107">`Join-Path`Cmdlet 将路径和子路径合并到单个路径中。</span><span class="sxs-lookup"><span data-stu-id="90585-107">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="90585-108">提供程序将提供路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="90585-108">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="90585-109">示例</span><span class="sxs-lookup"><span data-stu-id="90585-109">EXAMPLES</span></span>

### <span data-ttu-id="90585-110">示例1：将路径与子路径组合</span><span class="sxs-lookup"><span data-stu-id="90585-110">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="90585-111">此命令使用 `Join-Path` 将路径与 childpath 进行组合。</span><span class="sxs-lookup"><span data-stu-id="90585-111">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="90585-112">由于命令是从 `FileSystem` 提供程序执行的，因此提供了 `\` 分隔符来联接路径。</span><span class="sxs-lookup"><span data-stu-id="90585-112">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="90585-113">示例2：合并已包含目录分隔符的路径</span><span class="sxs-lookup"><span data-stu-id="90585-113">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="90585-114">现有的目录分隔符 `\` 和已处理，因此与之间只有一个分隔符 `Path``ChildPath`</span><span class="sxs-lookup"><span data-stu-id="90585-114">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="90585-115">示例3：通过将路径与子路径联接来显示文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="90585-115">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="90585-116">此命令显示通过联接 C:\Win \* 路径和系统子路径而引用的文件和文件夹 \* 。</span><span class="sxs-lookup"><span data-stu-id="90585-116">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="90585-117">它显示与相同的文件和文件夹 `Get-ChildItem` ，但它显示每个项目的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="90585-117">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="90585-118">在此命令中， `Path` 省略了和 `ChildPath` 可选的参数名称。</span><span class="sxs-lookup"><span data-stu-id="90585-118">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="90585-119">示例4：将 Join-Path 与 PowerShell 注册表提供程序一起使用</span><span class="sxs-lookup"><span data-stu-id="90585-119">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="90585-120">此命令显示注册表子项中包含的注册表项 `HKLM\System` `ControlSet` 。</span><span class="sxs-lookup"><span data-stu-id="90585-120">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="90585-121">`Resolve`参数尝试解析联接的路径，包括当前提供程序路径中的通配符`HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="90585-121">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="90585-122">示例5：将多个路径根与一个子路径组合在一起</span><span class="sxs-lookup"><span data-stu-id="90585-122">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="90585-123">此命令使用 `Join-Path` 将多个路径根与一个子路径组合在一起。</span><span class="sxs-lookup"><span data-stu-id="90585-123">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="90585-124">指定的驱动器 `Path` 必须存在，否则该条目的联接将失败。</span><span class="sxs-lookup"><span data-stu-id="90585-124">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="90585-125">示例6：合并带有子路径的文件系统驱动器的根</span><span class="sxs-lookup"><span data-stu-id="90585-125">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="90585-126">此命令将控制台中每个 PowerShell 文件系统驱动器的根与 Subdir 子路径组合在一起。</span><span class="sxs-lookup"><span data-stu-id="90585-126">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="90585-127">该命令使用 `Get-PSDrive` cmdlet 来获取 FileSystem 提供程序支持的 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="90585-127">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="90585-128">`ForEach-Object`语句仅选择对象的根属性 `PSDriveInfo` ，并将其与指定的子路径组合在一起。</span><span class="sxs-lookup"><span data-stu-id="90585-128">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="90585-129">输出显示计算机上的 PowerShell 驱动器包含映射到 C:\Program Files 目录的驱动器。</span><span class="sxs-lookup"><span data-stu-id="90585-129">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="90585-130">示例7：合并无数个路径</span><span class="sxs-lookup"><span data-stu-id="90585-130">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="90585-131">`AdditionalChildPath`参数允许联接无限数量的路径。</span><span class="sxs-lookup"><span data-stu-id="90585-131">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="90585-132">在此示例中，不使用任何参数名称，因此 "a" 将绑定到，将 " `Path` b" 绑定到，将 `ChildPath` "c-g" 绑定到 `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="90585-132">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="90585-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90585-133">PARAMETERS</span></span>

### <span data-ttu-id="90585-134">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="90585-134">-AdditionalChildPath</span></span>

<span data-ttu-id="90585-135">指定要追加到 *Path* 参数值的其他元素。</span><span class="sxs-lookup"><span data-stu-id="90585-135">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="90585-136">`ChildPath`参数仍是必需的，并且还必须指定。</span><span class="sxs-lookup"><span data-stu-id="90585-136">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="90585-137">此参数是使用属性指定的，该 `ValueFromRemainingArguments` 属性允许联接无限数量的路径。</span><span class="sxs-lookup"><span data-stu-id="90585-137">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="90585-138">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="90585-138">-ChildPath</span></span>

<span data-ttu-id="90585-139">指定要追加到参数值的元素 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="90585-139">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="90585-140">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="90585-140">Wildcards are permitted.</span></span>
<span data-ttu-id="90585-141">`ChildPath`参数是必需的，但参数名称 ( "ChildPath" ) 是可选的。</span><span class="sxs-lookup"><span data-stu-id="90585-141">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="90585-142">-Credential</span><span class="sxs-lookup"><span data-stu-id="90585-142">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="90585-143">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="90585-143">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="90585-144">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="90585-144">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="90585-145">-Path</span><span class="sxs-lookup"><span data-stu-id="90585-145">-Path</span></span>

<span data-ttu-id="90585-146">指定子路径追加到的主路径。</span><span class="sxs-lookup"><span data-stu-id="90585-146">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="90585-147">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="90585-147">Wildcards are permitted.</span></span>

<span data-ttu-id="90585-148">的值 `Path` 确定哪些提供程序联接路径并添加路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="90585-148">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="90585-149">`Path`尽管参数名称 ( "Path" ) 是可选的，但参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="90585-149">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="90585-150">-Resolve</span><span class="sxs-lookup"><span data-stu-id="90585-150">-Resolve</span></span>

<span data-ttu-id="90585-151">指示此 cmdlet 应尝试解析来自当前提供程序的联接路径。</span><span class="sxs-lookup"><span data-stu-id="90585-151">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="90585-152">如果使用通配符，则该 cmdlet 将返回与联接路径匹配的所有路径。</span><span class="sxs-lookup"><span data-stu-id="90585-152">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="90585-153">如果 **不使用通配符，** 则如果路径不存在，则该 cmdlet 将出错。</span><span class="sxs-lookup"><span data-stu-id="90585-153">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="90585-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90585-154">CommonParameters</span></span>

<span data-ttu-id="90585-155">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="90585-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90585-156">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="90585-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90585-157">输入</span><span class="sxs-lookup"><span data-stu-id="90585-157">INPUTS</span></span>

### <span data-ttu-id="90585-158">System.String</span><span class="sxs-lookup"><span data-stu-id="90585-158">System.String</span></span>

<span data-ttu-id="90585-159">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90585-159">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="90585-160">输出</span><span class="sxs-lookup"><span data-stu-id="90585-160">OUTPUTS</span></span>

### <span data-ttu-id="90585-161">System.String</span><span class="sxs-lookup"><span data-stu-id="90585-161">System.String</span></span>

<span data-ttu-id="90585-162">此 cmdlet 将返回包含生成的路径的字符串。</span><span class="sxs-lookup"><span data-stu-id="90585-162">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="90585-163">注释</span><span class="sxs-lookup"><span data-stu-id="90585-163">NOTES</span></span>

<span data-ttu-id="90585-164">在路径 cmdlet (包含 Path 名词的 cmdlet) 操作路径名，并以所有 PowerShell 提供程序可解释的简明格式返回名称。</span><span class="sxs-lookup"><span data-stu-id="90585-164">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="90585-165">这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。</span><span class="sxs-lookup"><span data-stu-id="90585-165">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="90585-166">你可以像使用 Dirname、Normpath、Realpath、Join 或其他路径操作程序那样使用这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90585-166">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="90585-167">可以将路径 cmdlet 用于多个提供程序，包括 `FileSystem` 、 `Registry` 和 `Certificate` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="90585-167">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="90585-168">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="90585-168">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="90585-169">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="90585-169">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="90585-170">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="90585-170">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="90585-171">相关链接</span><span class="sxs-lookup"><span data-stu-id="90585-171">RELATED LINKS</span></span>

[<span data-ttu-id="90585-172">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="90585-172">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="90585-173">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="90585-173">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="90585-174">Split-Path</span><span class="sxs-lookup"><span data-stu-id="90585-174">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="90585-175">Test-Path</span><span class="sxs-lookup"><span data-stu-id="90585-175">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="90585-176">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="90585-176">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="90585-177">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="90585-177">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="90585-178">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="90585-178">Get-PSDrive</span></span>](Get-PSDrive.md)

