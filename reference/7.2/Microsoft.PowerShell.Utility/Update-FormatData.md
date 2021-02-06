---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597668"
---
# <span data-ttu-id="efcba-102">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="efcba-102">Update-FormatData</span></span>

## <span data-ttu-id="efcba-103">摘要</span><span class="sxs-lookup"><span data-stu-id="efcba-103">SYNOPSIS</span></span>
<span data-ttu-id="efcba-104">更新当前会话中的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-104">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="efcba-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="efcba-105">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="efcba-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="efcba-106">DESCRIPTION</span></span>

<span data-ttu-id="efcba-107">Cmdlet 将格式设置 `Update-FormatData` 文件中的格式设置数据重新加载到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="efcba-107">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="efcba-108">此 cmdlet 允许你更新格式设置数据而无需重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="efcba-108">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="efcba-109">如果没有参数， `Update-FormatData` 将重新加载它先前加载的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-109">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="efcba-110">您可以使用的参数 `Update-FormatData` 将新的格式化文件添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="efcba-110">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="efcba-111">格式设置文件是 XML 格式的文本文件，其 `format.ps1xml` 文件扩展名为。</span><span class="sxs-lookup"><span data-stu-id="efcba-111">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="efcba-112">文件中的格式设置数据定义了会话中 Microsoft .NET Framework 对象的显示。</span><span class="sxs-lookup"><span data-stu-id="efcba-112">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="efcba-113">当 PowerShell 启动时，它会从 PowerShell 源代码加载格式数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-113">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="efcba-114">但是，您可以创建自定义 format.ps1xml 文件，以更新当前会话中的格式设置。</span><span class="sxs-lookup"><span data-stu-id="efcba-114">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="efcba-115">你可以使用 `Update-FormatData` 将格式设置数据重新加载到当前会话中，而无需重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="efcba-115">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="efcba-116">当你已添加或更改格式设置文件，但不希望中断会话时，这将非常有用。</span><span class="sxs-lookup"><span data-stu-id="efcba-116">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="efcba-117">有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="efcba-117">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="efcba-118">示例</span><span class="sxs-lookup"><span data-stu-id="efcba-118">EXAMPLES</span></span>

### <span data-ttu-id="efcba-119">示例 1：重新加载以前加载的格式设置文件</span><span class="sxs-lookup"><span data-stu-id="efcba-119">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="efcba-120">此命令将重新加载它先前加载的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-120">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="efcba-121">示例 2：重新加载格式设置文件以及跟踪和记录格式设置文件</span><span class="sxs-lookup"><span data-stu-id="efcba-121">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="efcba-122">此命令将格式设置文件重新加载到会话中，包括两个新文件：Trace.format.ps1xml 和 Log.format.ps1xml。</span><span class="sxs-lookup"><span data-stu-id="efcba-122">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="efcba-123">由于该命令使用了 AppendPath 参数，因此新文件中的格式设置数据将在内置文件的格式设置数据之后加载。</span><span class="sxs-lookup"><span data-stu-id="efcba-123">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="efcba-124">使用 AppendPath 参数是因为新文件中包含内置文件中未引用的用于对象的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-124">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="efcba-125">示例 3：编辑格式文件并重新加载它</span><span class="sxs-lookup"><span data-stu-id="efcba-125">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="efcba-126">此示例演示如何在编辑格式设置文件之后重新加载该文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-126">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="efcba-127">第一个命令将 NewFiles.format.ps1xml 文件添加到会话。</span><span class="sxs-lookup"><span data-stu-id="efcba-127">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="efcba-128">它使用 PrependPath 参数，因为该文件包含在内置文件中引用的对象的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-128">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="efcba-129">在添加 NewFiles.format.ps1xml 文件并在这些会话中对该文件进行测试之后，作者可编辑该文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-129">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="efcba-130">第二个命令使用 `Update-FormatData` cmdlet 来重新加载格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-130">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="efcba-131">由于之前已加载 NewFiles.format.ps1xml 文件，因此 `Update-FormatData` 会自动重新加载该文件，而不使用参数。</span><span class="sxs-lookup"><span data-stu-id="efcba-131">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="efcba-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efcba-132">PARAMETERS</span></span>

### <span data-ttu-id="efcba-133">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="efcba-133">-AppendPath</span></span>

<span data-ttu-id="efcba-134">指定此 cmdlet 添加到会话的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-134">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="efcba-135">在 PowerShell 加载内置的格式设置文件后加载这些文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-135">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="efcba-136">在对 .NET 对象进行格式设置时，PowerShell 将使用它为每个 .NET 类型找到的第一个格式设置定义。</span><span class="sxs-lookup"><span data-stu-id="efcba-136">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="efcba-137">如果使用 **AppendPath** 参数，则 PowerShell 将在遇到你要添加的格式设置数据之前，先从内置文件中搜索数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-137">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="efcba-138">使用此参数可添加一个文件，该文件用于对内置格式设置文件中未引用的 .NET 对象进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="efcba-138">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="efcba-139">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="efcba-139">-PrependPath</span></span>

<span data-ttu-id="efcba-140">指定此 cmdlet 添加到会话的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-140">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="efcba-141">在 PowerShell 加载内置的格式设置文件之前加载这些文件。</span><span class="sxs-lookup"><span data-stu-id="efcba-141">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="efcba-142">在对 .NET 对象进行格式设置时，PowerShell 将使用它为每个 .NET 类型找到的第一个格式设置定义。</span><span class="sxs-lookup"><span data-stu-id="efcba-142">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="efcba-143">如果使用 **PrependPath** 参数，则 PowerShell 将在遇到内置文件中的格式设置数据之前，先从要添加的文件中搜索数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-143">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="efcba-144">使用此参数可添加一个文件，该文件用于对也在内置格式设置文件中引用的 .NET 对象进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="efcba-144">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efcba-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="efcba-145">-Confirm</span></span>

<span data-ttu-id="efcba-146">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="efcba-146">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="efcba-147">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="efcba-147">-WhatIf</span></span>

<span data-ttu-id="efcba-148">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="efcba-148">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="efcba-149">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="efcba-149">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="efcba-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efcba-150">CommonParameters</span></span>

<span data-ttu-id="efcba-151">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="efcba-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efcba-152">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="efcba-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efcba-153">输入</span><span class="sxs-lookup"><span data-stu-id="efcba-153">INPUTS</span></span>

### <span data-ttu-id="efcba-154">System.String</span><span class="sxs-lookup"><span data-stu-id="efcba-154">System.String</span></span>

<span data-ttu-id="efcba-155">可以通过管道将包含追加路径的字符串传递给 `Update-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="efcba-155">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="efcba-156">输出</span><span class="sxs-lookup"><span data-stu-id="efcba-156">OUTPUTS</span></span>

### <span data-ttu-id="efcba-157">无</span><span class="sxs-lookup"><span data-stu-id="efcba-157">None</span></span>

<span data-ttu-id="efcba-158">该 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="efcba-158">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="efcba-159">注释</span><span class="sxs-lookup"><span data-stu-id="efcba-159">NOTES</span></span>

- <span data-ttu-id="efcba-160">`Update-FormatData` 还会更新会话中从模块导入的命令的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-160">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="efcba-161">如果模块的格式化文件发生更改，则可以运行 `Update-FormatData` 命令来更新导入命令的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="efcba-161">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="efcba-162">不需要再次导入该模块。</span><span class="sxs-lookup"><span data-stu-id="efcba-162">You do not need to import the module again.</span></span>

## <span data-ttu-id="efcba-163">相关链接</span><span class="sxs-lookup"><span data-stu-id="efcba-163">RELATED LINKS</span></span>

[<span data-ttu-id="efcba-164">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="efcba-164">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="efcba-165">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="efcba-165">Export-FormatData</span></span>](Export-FormatData.md)
