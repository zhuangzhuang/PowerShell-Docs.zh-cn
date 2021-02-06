---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d42b108d469ed8989628a6c0b4214af4afc0db00
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603584"
---
# <span data-ttu-id="2b00d-102">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="2b00d-102">Export-FormatData</span></span>

## <span data-ttu-id="2b00d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2b00d-103">SYNOPSIS</span></span>
<span data-ttu-id="2b00d-104">将当前会话中的格式设置数据保存在格式设置文件中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-104">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="2b00d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b00d-105">SYNTAX</span></span>

### <span data-ttu-id="2b00d-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="2b00d-106">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="2b00d-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="2b00d-107">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="2b00d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2b00d-108">DESCRIPTION</span></span>

<span data-ttu-id="2b00d-109">`Export-FormatData`Cmdlet 从当前会话中的格式对象 ( # B0 xml) 创建 PowerShell 格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-109">The `Export-FormatData` cmdlet creates PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="2b00d-110">它获取返回的 **ExtendedTypeDefinition** 对象 `Get-FormatData` ，并将其保存到 XML 格式的文件中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-110">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="2b00d-111">PowerShell 使用 ( # B0 xml) 格式设置文件中的数据来生成会话中 Microsoft .NET 框架对象的默认显示。</span><span class="sxs-lookup"><span data-stu-id="2b00d-111">PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="2b00d-112">你可以查看和编辑这些格式设置文件，并使用 Update-FormatData cmdlet 将格式设置数据添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-112">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="2b00d-113">有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2b00d-113">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="2b00d-114">示例</span><span class="sxs-lookup"><span data-stu-id="2b00d-114">EXAMPLES</span></span>

### <span data-ttu-id="2b00d-115">示例1：导出会话格式数据</span><span class="sxs-lookup"><span data-stu-id="2b00d-115">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="2b00d-116">此命令将会话中的所有格式数据导出到 AllFormat.ps1xml 文件中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-116">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="2b00d-117">该命令使用 `Get-FormatData` cmdlet 来获取会话中的格式数据。</span><span class="sxs-lookup"><span data-stu-id="2b00d-117">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="2b00d-118">如果为 `*` **TypeName** 参数 (所有) ，则值为，指示该 cmdlet 获取会话中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="2b00d-118">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="2b00d-119">该命令使用管道运算符 (`|`) 将格式数据从 `Get-FormatData` 命令发送到 `Export-FormatData` cmdlet，后者将格式数据导出到 AllFormat.ps1 文件中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-119">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="2b00d-120">该 `Export-FormatData` 命令使用 **IncludeScriptBlock** 参数将脚本块包含在文件中的格式数据。</span><span class="sxs-lookup"><span data-stu-id="2b00d-120">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="2b00d-121">示例2：导出类型的格式数据</span><span class="sxs-lookup"><span data-stu-id="2b00d-121">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="2b00d-122">这些命令将 **HelpInfoShort** 类型的格式数据导出到 Help.format.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-122">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="2b00d-123">第一个命令使用 `Get-FormatData` cmdlet 来获取 **HelpInfoShort** 类型的格式数据，并将其保存在 `$F` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-123">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="2b00d-124">第二个命令使用 cmdlet 的 **InputObject** 参数 `Export-FormatData` 来输入保存在变量中的格式数据 `$F` 。</span><span class="sxs-lookup"><span data-stu-id="2b00d-124">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="2b00d-125">它还使用 **IncludeScriptBlock** 参数将脚本块包括在输出中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-125">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="2b00d-126">示例3：在不使用脚本块的情况下导出格式数据</span><span class="sxs-lookup"><span data-stu-id="2b00d-126">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="2b00d-127">此示例演示省略命令中的 **IncludeScriptBlock** 参数的效果 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="2b00d-127">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="2b00d-128">第一个命令使用 `Get-FormatData` cmdlet 来获取 Get-Process cmdlet 返回的 **system.object** 对象的格式数据。</span><span class="sxs-lookup"><span data-stu-id="2b00d-128">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="2b00d-129">该命令使用管道运算符 (`|`) 将格式设置数据发送到 `Export-FormatData` cmdlet，该 cmdlet 将其导出到当前目录中的 Process.format.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-129">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="2b00d-130">在这种情况下，该 `Export-FormatData` 命令不使用 **IncludeScriptBlock** 参数。</span><span class="sxs-lookup"><span data-stu-id="2b00d-130">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="2b00d-131">第二个命令使用 `Update-FormatData` cmdlet 将 Process.format.ps1xml 文件添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-131">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="2b00d-132">该命令使用 **PrependPath** 参数来确保在进程对象的标准格式设置数据之前找到 Process.format.ps1xml 文件中的进程对象的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="2b00d-132">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="2b00d-133">第三个命令显示此更改的效果。</span><span class="sxs-lookup"><span data-stu-id="2b00d-133">The third command shows the effects of this change.</span></span> <span data-ttu-id="2b00d-134">该命令使用 `Get-Process` cmdlet 来获取名称以 P 开头的进程。此输出显示，显示中缺少使用脚本块计算的属性值。</span><span class="sxs-lookup"><span data-stu-id="2b00d-134">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="2b00d-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b00d-135">PARAMETERS</span></span>

### <span data-ttu-id="2b00d-136">-Force</span><span class="sxs-lookup"><span data-stu-id="2b00d-136">-Force</span></span>

<span data-ttu-id="2b00d-137">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="2b00d-137">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2b00d-138">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="2b00d-138">-IncludeScriptBlock</span></span>

<span data-ttu-id="2b00d-139">指示是否导出格式数据中的脚本块。</span><span class="sxs-lookup"><span data-stu-id="2b00d-139">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="2b00d-140">因为脚本块包含代码且可被恶意使用，所以在默认情况下不导出它们。</span><span class="sxs-lookup"><span data-stu-id="2b00d-140">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

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

### <span data-ttu-id="2b00d-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2b00d-141">-InputObject</span></span>

<span data-ttu-id="2b00d-142">指定要导出的格式数据对象。</span><span class="sxs-lookup"><span data-stu-id="2b00d-142">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="2b00d-143">输入包含对象的变量或获取对象的命令（如 `Get-FormatData` 命令）。</span><span class="sxs-lookup"><span data-stu-id="2b00d-143">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="2b00d-144">还可以通过管道将对象传递 `Get-FormatData` 给 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="2b00d-144">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2b00d-145">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2b00d-145">-LiteralPath</span></span>

<span data-ttu-id="2b00d-146">指定输出文件的位置。</span><span class="sxs-lookup"><span data-stu-id="2b00d-146">Specifies a location for the output file.</span></span> <span data-ttu-id="2b00d-147">与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="2b00d-147">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2b00d-148">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="2b00d-148">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2b00d-149">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-149">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2b00d-150">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="2b00d-150">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b00d-151">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="2b00d-151">-NoClobber</span></span>

<span data-ttu-id="2b00d-152">指示该 cmdlet 不会覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-152">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="2b00d-153">默认情况下， `Export-FormatData` 除非文件具有只读属性，否则将覆盖文件而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="2b00d-153">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="2b00d-154">若要指示 `Export-FormatData` 覆盖只读文件，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="2b00d-154">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b00d-155">-Path</span><span class="sxs-lookup"><span data-stu-id="2b00d-155">-Path</span></span>

<span data-ttu-id="2b00d-156">指定输出文件的位置。</span><span class="sxs-lookup"><span data-stu-id="2b00d-156">Specifies a location for the output file.</span></span>
<span data-ttu-id="2b00d-157">输入路径（可选）和具有 format.ps1xml 文件扩展名的文件名。</span><span class="sxs-lookup"><span data-stu-id="2b00d-157">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="2b00d-158">如果省略路径，则将 `Export-FormatData` 在当前目录中创建文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-158">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="2b00d-159">如果使用 types.ps1xml 之外的文件扩展名，则该 `Update-FormatData` cmdlet 将不会识别该文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-159">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="2b00d-160">如果指定了现有文件，则将 `Export-FormatData` 覆盖该文件而不发出警告，除非该文件具有只读属性。</span><span class="sxs-lookup"><span data-stu-id="2b00d-160">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="2b00d-161">若要覆盖只读文件，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="2b00d-161">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="2b00d-162">若要防止文件被覆盖，请使用 **NoClobber** 参数。</span><span class="sxs-lookup"><span data-stu-id="2b00d-162">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b00d-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b00d-163">CommonParameters</span></span>

<span data-ttu-id="2b00d-164">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2b00d-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b00d-165">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2b00d-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b00d-166">输入</span><span class="sxs-lookup"><span data-stu-id="2b00d-166">INPUTS</span></span>

### <span data-ttu-id="2b00d-167">System.Management.Automation.ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="2b00d-167">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="2b00d-168">可以通过管道将 **ExtendedTypeDefinition** 对象发送 `Get-FormatData` 到 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="2b00d-168">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="2b00d-169">输出</span><span class="sxs-lookup"><span data-stu-id="2b00d-169">OUTPUTS</span></span>

### <span data-ttu-id="2b00d-170">无</span><span class="sxs-lookup"><span data-stu-id="2b00d-170">None</span></span>

<span data-ttu-id="2b00d-171">`Export-FormatData` 不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="2b00d-171">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="2b00d-172">它将生成一个文件并将其保存在指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="2b00d-172">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="2b00d-173">注释</span><span class="sxs-lookup"><span data-stu-id="2b00d-173">NOTES</span></span>

- <span data-ttu-id="2b00d-174">若要使用任何格式设置文件（包括已导出的格式设置文件），会话的执行策略必须允许运行脚本和配置文件。</span><span class="sxs-lookup"><span data-stu-id="2b00d-174">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="2b00d-175">有关详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="2b00d-175">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="2b00d-176">相关链接</span><span class="sxs-lookup"><span data-stu-id="2b00d-176">RELATED LINKS</span></span>

[<span data-ttu-id="2b00d-177">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="2b00d-177">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="2b00d-178">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="2b00d-178">Update-FormatData</span></span>](Update-FormatData.md)
