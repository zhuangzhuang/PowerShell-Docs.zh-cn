---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 9da204513ed4a17eb8dc20481b878a4a783534f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598458"
---
# <span data-ttu-id="56e42-102">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="56e42-102">Export-Alias</span></span>

## <span data-ttu-id="56e42-103">摘要</span><span class="sxs-lookup"><span data-stu-id="56e42-103">SYNOPSIS</span></span>
<span data-ttu-id="56e42-104">将有关当前定义的别名的信息导出到文件中。</span><span class="sxs-lookup"><span data-stu-id="56e42-104">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="56e42-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56e42-105">SYNTAX</span></span>

### <span data-ttu-id="56e42-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="56e42-106">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56e42-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="56e42-107">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="56e42-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="56e42-108">DESCRIPTION</span></span>

<span data-ttu-id="56e42-109">`Export-Alias`Cmdlet 将当前会话中的别名导出到文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-109">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="56e42-110">如果输出文件不存在，则该 cmdlet 将创建它。</span><span class="sxs-lookup"><span data-stu-id="56e42-110">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="56e42-111">`Export-Alias` 可以导出特定作用域或所有作用域中的别名，它可以生成 CSV 格式的数据，或者作为一系列可添加到会话或 PowerShell 配置文件的 Set-Alias 命令生成数据。</span><span class="sxs-lookup"><span data-stu-id="56e42-111">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="56e42-112">示例</span><span class="sxs-lookup"><span data-stu-id="56e42-112">EXAMPLES</span></span>

### <span data-ttu-id="56e42-113">示例1：导出别名</span><span class="sxs-lookup"><span data-stu-id="56e42-113">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="56e42-114">此命令将当前的别名信息导出到当前目录中名为 Alias.csv 的文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-114">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="56e42-115">示例2：除非导出文件已存在，否则导出别名</span><span class="sxs-lookup"><span data-stu-id="56e42-115">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="56e42-116">此命令将当前会话中的别名导出到 Alias.csv 文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-116">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="56e42-117">由于指定了 **NoClobber** 参数，因此如果 Alias.csv 文件已存在于当前目录中，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="56e42-117">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="56e42-118">示例3：将别名追加到文件</span><span class="sxs-lookup"><span data-stu-id="56e42-118">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="56e42-119">此命令将当前会话中的别名附加到 Alias.csv 文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-119">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="56e42-120">此命令使用 **description** 参数将描述添加到文件顶部的注释。</span><span class="sxs-lookup"><span data-stu-id="56e42-120">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="56e42-121">该命令还使用 **Force** 参数覆盖任何现有 Alias.csv 文件，即使它们具有只读属性也是如此。</span><span class="sxs-lookup"><span data-stu-id="56e42-121">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="56e42-122">示例4：将别名导出为脚本</span><span class="sxs-lookup"><span data-stu-id="56e42-122">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="56e42-123">此示例演示如何使用生成的脚本文件格式 `Export-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="56e42-123">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="56e42-124">第一个命令将会话中的别名导出到 Alias.ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-124">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="56e42-125">它将 **As** 参数与 Script 值一起使用，以生成包含每个别名的 Set-Alias 命令的文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-125">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="56e42-126">第二个命令将 Alias.ps1 文件中的别名添加到 CurrentUser-CurrentHost 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="56e42-126">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="56e42-127">配置文件的路径保存在 `$Profile` 变量中。</span><span class="sxs-lookup"><span data-stu-id="56e42-127">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="56e42-128">该命令使用 `Get-Content` cmdlet 来获取 Alias.ps1 文件中的别名，并使用 `Add-Content` cmdlet 将它们添加到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="56e42-128">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="56e42-129">有关详细信息，请参阅 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="56e42-129">For more information, see about_Profiles.</span></span>

<span data-ttu-id="56e42-130">第三个和第四个命令将 Alias.ps1 文件中的别名添加到 Server01 计算机上的远程会话。</span><span class="sxs-lookup"><span data-stu-id="56e42-130">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="56e42-131">第三个命令使用 `New-PSSession` cmdlet 来创建会话。</span><span class="sxs-lookup"><span data-stu-id="56e42-131">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="56e42-132">第四个命令使用 cmdlet 的 **FilePath** 参数 `Invoke-Command` 在新会话中运行 Alias.ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-132">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="56e42-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56e42-133">PARAMETERS</span></span>

### <span data-ttu-id="56e42-134">-Append</span><span class="sxs-lookup"><span data-stu-id="56e42-134">-Append</span></span>

<span data-ttu-id="56e42-135">指示此 cmdlet 将输出追加到指定的文件，而不是覆盖该文件的现有内容。</span><span class="sxs-lookup"><span data-stu-id="56e42-135">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="56e42-136">-As</span><span class="sxs-lookup"><span data-stu-id="56e42-136">-As</span></span>

<span data-ttu-id="56e42-137">指定输出格式。</span><span class="sxs-lookup"><span data-stu-id="56e42-137">Specifies the output format.</span></span>
<span data-ttu-id="56e42-138">CSV 是默认值。</span><span class="sxs-lookup"><span data-stu-id="56e42-138">CSV is the default.</span></span>
<span data-ttu-id="56e42-139">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="56e42-139">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="56e42-140">CSV</span><span class="sxs-lookup"><span data-stu-id="56e42-140">CSV.</span></span>
<span data-ttu-id="56e42-141">以逗号分隔值 (CSV) 格式。</span><span class="sxs-lookup"><span data-stu-id="56e42-141">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="56e42-142">脚本。</span><span class="sxs-lookup"><span data-stu-id="56e42-142">Script.</span></span>
<span data-ttu-id="56e42-143">`Set-Alias`为每个导出的别名创建一个命令。</span><span class="sxs-lookup"><span data-stu-id="56e42-143">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="56e42-144">如果你使用 .ps1 文件扩展命名输出文件，则可以将它作为脚本运行，以将别名添加到任何会话中。</span><span class="sxs-lookup"><span data-stu-id="56e42-144">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56e42-145">-Description</span><span class="sxs-lookup"><span data-stu-id="56e42-145">-Description</span></span>

<span data-ttu-id="56e42-146">指定导出文件的说明。</span><span class="sxs-lookup"><span data-stu-id="56e42-146">Specifies the description of the exported file.</span></span>
<span data-ttu-id="56e42-147">该描述显示为该文件顶部的注释，位于标头信息之后。</span><span class="sxs-lookup"><span data-stu-id="56e42-147">The description appears as a comment at the top of the file, following the header information.</span></span>

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

### <span data-ttu-id="56e42-148">-Force</span><span class="sxs-lookup"><span data-stu-id="56e42-148">-Force</span></span>

<span data-ttu-id="56e42-149">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="56e42-149">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="56e42-150">即使在文件上设置了只读属性，也将覆盖输出文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-150">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="56e42-151">默认情况下， `Export-Alias` 除非设置了只读或隐藏属性，或者命令中使用了 **NoClobber** 参数，否则，将在不发出警告的情况下覆盖文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-151">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="56e42-152">当命令中同时使用 **NoClobber** 参数时，该参数优先于 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="56e42-152">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="56e42-153">**Force** 参数不能强制 `Export-Alias` 覆盖具有隐藏特性的文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-153">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="56e42-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="56e42-154">-LiteralPath</span></span>

<span data-ttu-id="56e42-155">指定输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="56e42-155">Specifies the path to the output file.</span></span>
<span data-ttu-id="56e42-156">与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="56e42-156">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="56e42-157">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="56e42-157">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="56e42-158">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="56e42-158">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="56e42-159">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="56e42-159">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="56e42-160">-Name</span><span class="sxs-lookup"><span data-stu-id="56e42-160">-Name</span></span>

<span data-ttu-id="56e42-161">将名称指定为要导出的别名的数组。</span><span class="sxs-lookup"><span data-stu-id="56e42-161">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="56e42-162">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="56e42-162">Wildcards are permitted.</span></span>

<span data-ttu-id="56e42-163">默认情况下， `Export-Alias` 将导出会话或作用域中的所有别名。</span><span class="sxs-lookup"><span data-stu-id="56e42-163">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="56e42-164">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="56e42-164">-NoClobber</span></span>

<span data-ttu-id="56e42-165">指示此 cmdlet 防止 `Export-Alias` 覆盖任何文件，即使在该命令中使用了 **Force** 参数也是如此。</span><span class="sxs-lookup"><span data-stu-id="56e42-165">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="56e42-166">如果省略 **NoClobber** 参数，则 `Export-Alias` 将覆盖现有文件而不发出警告，除非在该文件上设置了只读特性。</span><span class="sxs-lookup"><span data-stu-id="56e42-166">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="56e42-167">*NoClobber* 优先于 **Force** 参数，这将允许 `Export-Alias` 使用只读属性覆盖文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-167">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="56e42-168">*NoClobber* 不会阻止 **Append** 参数将内容添加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-168">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

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

### <span data-ttu-id="56e42-169">-PassThru</span><span class="sxs-lookup"><span data-stu-id="56e42-169">-PassThru</span></span>

<span data-ttu-id="56e42-170">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="56e42-170">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="56e42-171">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="56e42-171">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="56e42-172">-Path</span><span class="sxs-lookup"><span data-stu-id="56e42-172">-Path</span></span>

<span data-ttu-id="56e42-173">指定输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="56e42-173">Specifies the path to the output file.</span></span>
<span data-ttu-id="56e42-174">允许使用通配符，但所得到的路径值必须解析为单个文件名称。</span><span class="sxs-lookup"><span data-stu-id="56e42-174">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="56e42-175">-Scope</span><span class="sxs-lookup"><span data-stu-id="56e42-175">-Scope</span></span>

<span data-ttu-id="56e42-176">指定应从其导出别名的作用域。</span><span class="sxs-lookup"><span data-stu-id="56e42-176">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="56e42-177">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="56e42-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="56e42-178">全球</span><span class="sxs-lookup"><span data-stu-id="56e42-178">Global</span></span>
- <span data-ttu-id="56e42-179">本地</span><span class="sxs-lookup"><span data-stu-id="56e42-179">Local</span></span>
- <span data-ttu-id="56e42-180">Script</span><span class="sxs-lookup"><span data-stu-id="56e42-180">Script</span></span>
- <span data-ttu-id="56e42-181">一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父级) </span><span class="sxs-lookup"><span data-stu-id="56e42-181">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="56e42-182">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="56e42-182">The default value is Local.</span></span>
<span data-ttu-id="56e42-183">有关详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="56e42-183">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="56e42-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="56e42-184">-Confirm</span></span>

<span data-ttu-id="56e42-185">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="56e42-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="56e42-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="56e42-186">-WhatIf</span></span>

<span data-ttu-id="56e42-187">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="56e42-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="56e42-188">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="56e42-188">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="56e42-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56e42-189">CommonParameters</span></span>

<span data-ttu-id="56e42-190">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="56e42-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56e42-191">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="56e42-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56e42-192">输入</span><span class="sxs-lookup"><span data-stu-id="56e42-192">INPUTS</span></span>

### <span data-ttu-id="56e42-193">无。</span><span class="sxs-lookup"><span data-stu-id="56e42-193">None.</span></span>

<span data-ttu-id="56e42-194">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56e42-194">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="56e42-195">输出</span><span class="sxs-lookup"><span data-stu-id="56e42-195">OUTPUTS</span></span>

### <span data-ttu-id="56e42-196">无或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="56e42-196">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="56e42-197">当使用 **Passthru** 参数时，将 `Export-Alias` 返回一个表示别名的 **system.management.automation.aliasinfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="56e42-197">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="56e42-198">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="56e42-198">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="56e42-199">注释</span><span class="sxs-lookup"><span data-stu-id="56e42-199">NOTES</span></span>

* <span data-ttu-id="56e42-200">可以仅将别名导出到文件。</span><span class="sxs-lookup"><span data-stu-id="56e42-200">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="56e42-201">相关链接</span><span class="sxs-lookup"><span data-stu-id="56e42-201">RELATED LINKS</span></span>

[<span data-ttu-id="56e42-202">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="56e42-202">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="56e42-203">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="56e42-203">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="56e42-204">New-Alias</span><span class="sxs-lookup"><span data-stu-id="56e42-204">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="56e42-205">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="56e42-205">Set-Alias</span></span>](Set-Alias.md)

