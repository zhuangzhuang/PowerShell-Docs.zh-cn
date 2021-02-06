---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: ebb79f16447aef2dd194505d805a34353f710e69
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597449"
---
# <span data-ttu-id="fdfac-102">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-102">Invoke-Item</span></span>

## <span data-ttu-id="fdfac-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fdfac-103">SYNOPSIS</span></span>
<span data-ttu-id="fdfac-104">对指定项执行默认操作。</span><span class="sxs-lookup"><span data-stu-id="fdfac-104">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="fdfac-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fdfac-105">SYNTAX</span></span>

### <span data-ttu-id="fdfac-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="fdfac-106">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fdfac-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fdfac-107">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fdfac-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fdfac-108">DESCRIPTION</span></span>

<span data-ttu-id="fdfac-109">`Invoke-Item`Cmdlet 对指定项执行默认操作。</span><span class="sxs-lookup"><span data-stu-id="fdfac-109">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="fdfac-110">例如，它运行可执行文件或在与某一文档文件类型关联的应用程序中打开该文档文件。</span><span class="sxs-lookup"><span data-stu-id="fdfac-110">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="fdfac-111">默认操作依赖于项的类型，由提供数据访问的 PowerShell 提供程序确定。</span><span class="sxs-lookup"><span data-stu-id="fdfac-111">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="fdfac-112">示例</span><span class="sxs-lookup"><span data-stu-id="fdfac-112">EXAMPLES</span></span>

### <span data-ttu-id="fdfac-113">示例 1：打开文件</span><span class="sxs-lookup"><span data-stu-id="fdfac-113">Example 1: Open a file</span></span>

<span data-ttu-id="fdfac-114">此命令在 Microsoft Office Word 中打开文件 "aliasApr04.doc"。</span><span class="sxs-lookup"><span data-stu-id="fdfac-114">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="fdfac-115">在这种情况下，在 Word 中打开是 ".doc" 文件的默认操作。</span><span class="sxs-lookup"><span data-stu-id="fdfac-115">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="fdfac-116">示例 2：打开特定类型的所有文件</span><span class="sxs-lookup"><span data-stu-id="fdfac-116">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="fdfac-117">此命令打开文件夹中的所有 Microsoft Office Excel 电子表格 `C:\Documents and
Settings\Lister\My Documents` 。</span><span class="sxs-lookup"><span data-stu-id="fdfac-117">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="fdfac-118">每个电子表格均在 Excel 的新实例中打开。</span><span class="sxs-lookup"><span data-stu-id="fdfac-118">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="fdfac-119">在这种情况下，在 Excel 中打开是文件的默认操作 `.xls` 。</span><span class="sxs-lookup"><span data-stu-id="fdfac-119">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="fdfac-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fdfac-120">PARAMETERS</span></span>

### <span data-ttu-id="fdfac-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="fdfac-121">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fdfac-122">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="fdfac-122">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fdfac-123">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="fdfac-123">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="fdfac-124">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fdfac-124">-Exclude</span></span>

<span data-ttu-id="fdfac-125">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="fdfac-125">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fdfac-126">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fdfac-126">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fdfac-127">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="fdfac-127">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fdfac-128">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fdfac-128">Wildcard characters are permitted.</span></span> <span data-ttu-id="fdfac-129">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="fdfac-129">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fdfac-130">-Filter</span><span class="sxs-lookup"><span data-stu-id="fdfac-130">-Filter</span></span>

<span data-ttu-id="fdfac-131">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="fdfac-131">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fdfac-132">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="fdfac-132">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fdfac-133">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="fdfac-133">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fdfac-134">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="fdfac-134">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="fdfac-135">-Include</span><span class="sxs-lookup"><span data-stu-id="fdfac-135">-Include</span></span>

<span data-ttu-id="fdfac-136">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="fdfac-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fdfac-137">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fdfac-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fdfac-138">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="fdfac-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fdfac-139">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fdfac-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="fdfac-140">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="fdfac-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fdfac-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fdfac-141">-LiteralPath</span></span>

<span data-ttu-id="fdfac-142">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="fdfac-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fdfac-143">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="fdfac-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="fdfac-144">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="fdfac-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fdfac-145">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="fdfac-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fdfac-146">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="fdfac-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fdfac-147">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="fdfac-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="fdfac-148">-Path</span><span class="sxs-lookup"><span data-stu-id="fdfac-148">-Path</span></span>

<span data-ttu-id="fdfac-149">指定所选项的路径。</span><span class="sxs-lookup"><span data-stu-id="fdfac-149">Specifies the path to the selected item.</span></span>
<span data-ttu-id="fdfac-150">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fdfac-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fdfac-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fdfac-151">-Confirm</span></span>

<span data-ttu-id="fdfac-152">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="fdfac-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fdfac-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fdfac-153">-WhatIf</span></span>

<span data-ttu-id="fdfac-154">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="fdfac-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fdfac-155">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fdfac-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fdfac-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fdfac-156">CommonParameters</span></span>

<span data-ttu-id="fdfac-157">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="fdfac-157">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fdfac-158">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fdfac-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fdfac-159">输入</span><span class="sxs-lookup"><span data-stu-id="fdfac-159">INPUTS</span></span>

### <span data-ttu-id="fdfac-160">System.String</span><span class="sxs-lookup"><span data-stu-id="fdfac-160">System.String</span></span>

<span data-ttu-id="fdfac-161">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fdfac-161">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="fdfac-162">输出</span><span class="sxs-lookup"><span data-stu-id="fdfac-162">OUTPUTS</span></span>

### <span data-ttu-id="fdfac-163">无</span><span class="sxs-lookup"><span data-stu-id="fdfac-163">None</span></span>

<span data-ttu-id="fdfac-164">此命令不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="fdfac-164">The command does not generate any output.</span></span>
<span data-ttu-id="fdfac-165">但它调用的项可能会产生输出。</span><span class="sxs-lookup"><span data-stu-id="fdfac-165">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="fdfac-166">注释</span><span class="sxs-lookup"><span data-stu-id="fdfac-166">NOTES</span></span>

<span data-ttu-id="fdfac-167">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="fdfac-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fdfac-168">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="fdfac-168">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fdfac-169">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="fdfac-169">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fdfac-170">相关链接</span><span class="sxs-lookup"><span data-stu-id="fdfac-170">RELATED LINKS</span></span>

[<span data-ttu-id="fdfac-171">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-171">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="fdfac-172">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-172">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="fdfac-173">Get-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-173">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="fdfac-174">Move-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-174">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="fdfac-175">New-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-175">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="fdfac-176">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-176">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="fdfac-177">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-177">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="fdfac-178">Set-Item</span><span class="sxs-lookup"><span data-stu-id="fdfac-178">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="fdfac-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fdfac-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

