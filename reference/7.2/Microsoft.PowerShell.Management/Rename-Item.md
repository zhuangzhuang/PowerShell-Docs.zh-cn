---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: dec5c2c905486110e4885f29d236ab41d945fb96
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597256"
---
# <span data-ttu-id="1ada1-102">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-102">Rename-Item</span></span>

## <span data-ttu-id="1ada1-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1ada1-103">SYNOPSIS</span></span>
<span data-ttu-id="1ada1-104">重命名 PowerShell 提供程序命名空间中的项。</span><span class="sxs-lookup"><span data-stu-id="1ada1-104">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="1ada1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ada1-105">SYNTAX</span></span>

### <span data-ttu-id="1ada1-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="1ada1-106">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="1ada1-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1ada1-107">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="1ada1-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1ada1-108">DESCRIPTION</span></span>

<span data-ttu-id="1ada1-109">`Rename-Item`Cmdlet 更改指定项的名称。</span><span class="sxs-lookup"><span data-stu-id="1ada1-109">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="1ada1-110">此 cmdlet 不影响正被重命名的项的内容。</span><span class="sxs-lookup"><span data-stu-id="1ada1-110">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="1ada1-111">不能使用 `Rename-Item` 移动项，例如通过指定路径和新名称来移动项。</span><span class="sxs-lookup"><span data-stu-id="1ada1-111">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="1ada1-112">若要移动和重命名项，请使用 `Move-Item` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1ada1-112">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="1ada1-113">示例</span><span class="sxs-lookup"><span data-stu-id="1ada1-113">EXAMPLES</span></span>

### <span data-ttu-id="1ada1-114">示例1：重命名文件</span><span class="sxs-lookup"><span data-stu-id="1ada1-114">Example 1: Rename a file</span></span>

<span data-ttu-id="1ada1-115">此命令将文件重命名 `daily_file.txt` 为 `monday_file.txt` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-115">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="1ada1-116">示例2：重命名和移动项</span><span class="sxs-lookup"><span data-stu-id="1ada1-116">Example 2: Rename and move an item</span></span>

<span data-ttu-id="1ada1-117">不能 `Rename-Item` 同时使用重命名和移动项。</span><span class="sxs-lookup"><span data-stu-id="1ada1-117">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="1ada1-118">具体来说，不能为 **NewName** 参数的值提供路径，除非该路径与 **path** 参数中指定的路径相同。</span><span class="sxs-lookup"><span data-stu-id="1ada1-118">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="1ada1-119">在其他情况下，仅允许输入新名称。</span><span class="sxs-lookup"><span data-stu-id="1ada1-119">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="1ada1-120">此示例尝试将 `project.txt` 当前目录中的文件重命名为 `old-project.txt` 目录中的 `D:\Archive` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-120">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="1ada1-121">结果将在输出中显示错误。</span><span class="sxs-lookup"><span data-stu-id="1ada1-121">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="1ada1-122">示例3：重命名注册表项</span><span class="sxs-lookup"><span data-stu-id="1ada1-122">Example 3: Rename a registry key</span></span>

<span data-ttu-id="1ada1-123">此示例将注册表项从 " **广告** " 重命名为 " **营销**"。</span><span class="sxs-lookup"><span data-stu-id="1ada1-123">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="1ada1-124">当该命令完成时，将重命名该注册表项，但该注册表项中的注册表条目保持不变。</span><span class="sxs-lookup"><span data-stu-id="1ada1-124">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="1ada1-125">示例4：重命名多个文件</span><span class="sxs-lookup"><span data-stu-id="1ada1-125">Example 4: Rename multiple files</span></span>

<span data-ttu-id="1ada1-126">此示例将当前目录中的所有文件都重命名 `*.txt` 为 `*.log` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-126">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="1ada1-127">该 `Get-ChildItem` cmdlet 将获取当前文件夹中具有文件扩展名的所有文件， `.txt` 然后将其传递给 `Rename-Item` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-127">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="1ada1-128">**Newname** 的值是在将值提交到 **NewName** 参数之前运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="1ada1-128">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="1ada1-129">在脚本块中， `$_` 自动变量表示通过管道传递给命令时的每个文件对象。</span><span class="sxs-lookup"><span data-stu-id="1ada1-129">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="1ada1-130">脚本块使用 `-replace` 运算符将每个文件的文件扩展名替换为 `.log` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-130">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="1ada1-131">请注意，使用运算符的匹配 `-replace` 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="1ada1-131">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="1ada1-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1ada1-132">PARAMETERS</span></span>

### <span data-ttu-id="1ada1-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="1ada1-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1ada1-134">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="1ada1-134">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="1ada1-135">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1ada1-136">-Force</span><span class="sxs-lookup"><span data-stu-id="1ada1-136">-Force</span></span>

<span data-ttu-id="1ada1-137">强制 cmdlet 重命名无法以其他方式更改的项，如隐藏文件或只读文件，或者只读别名或变量。</span><span class="sxs-lookup"><span data-stu-id="1ada1-137">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="1ada1-138">该 cmdlet 不能更改常量别名或变量。</span><span class="sxs-lookup"><span data-stu-id="1ada1-138">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="1ada1-139">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="1ada1-139">Implementation varies from provider to provider.</span></span> <span data-ttu-id="1ada1-140">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="1ada1-141">即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="1ada1-141">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="1ada1-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1ada1-142">-LiteralPath</span></span>

<span data-ttu-id="1ada1-143">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="1ada1-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1ada1-144">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="1ada1-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1ada1-145">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="1ada1-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1ada1-146">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="1ada1-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1ada1-147">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="1ada1-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1ada1-148">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="1ada1-149">-NewName</span><span class="sxs-lookup"><span data-stu-id="1ada1-149">-NewName</span></span>

<span data-ttu-id="1ada1-150">指定项的新名称。</span><span class="sxs-lookup"><span data-stu-id="1ada1-150">Specifies the new name of the item.</span></span> <span data-ttu-id="1ada1-151">请仅输入名称，而不是路径加名称。</span><span class="sxs-lookup"><span data-stu-id="1ada1-151">Enter only a name, not a path and name.</span></span> <span data-ttu-id="1ada1-152">如果输入的路径与 **path** 参数中指定的路径不同，则会 `Rename-Item` 生成错误。</span><span class="sxs-lookup"><span data-stu-id="1ada1-152">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="1ada1-153">若要重命名和移动项，请使用 `Move-Item` 。</span><span class="sxs-lookup"><span data-stu-id="1ada1-153">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="1ada1-154">不能在 **NewName** 参数的值中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1ada1-154">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="1ada1-155">若要为多个文件指定名称，请在正则表达式中使用 **Replace** 运算符。</span><span class="sxs-lookup"><span data-stu-id="1ada1-155">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="1ada1-156">有关 Replace 运算符的详细信息，请参阅 [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-156">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1ada1-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1ada1-157">-PassThru</span></span>

<span data-ttu-id="1ada1-158">返回一个对象，该对象表示管道中的项。</span><span class="sxs-lookup"><span data-stu-id="1ada1-158">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="1ada1-159">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="1ada1-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1ada1-160">-Path</span><span class="sxs-lookup"><span data-stu-id="1ada1-160">-Path</span></span>

<span data-ttu-id="1ada1-161">指定要重命名的项的路径。</span><span class="sxs-lookup"><span data-stu-id="1ada1-161">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1ada1-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1ada1-162">-Confirm</span></span>

<span data-ttu-id="1ada1-163">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="1ada1-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1ada1-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1ada1-164">-WhatIf</span></span>

<span data-ttu-id="1ada1-165">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="1ada1-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1ada1-166">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1ada1-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1ada1-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ada1-167">CommonParameters</span></span>

<span data-ttu-id="1ada1-168">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1ada1-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ada1-169">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-169">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1ada1-170">输入</span><span class="sxs-lookup"><span data-stu-id="1ada1-170">INPUTS</span></span>

### <span data-ttu-id="1ada1-171">System.String</span><span class="sxs-lookup"><span data-stu-id="1ada1-171">System.String</span></span>

<span data-ttu-id="1ada1-172">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1ada1-172">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="1ada1-173">输出</span><span class="sxs-lookup"><span data-stu-id="1ada1-173">OUTPUTS</span></span>

### <span data-ttu-id="1ada1-174">无或表示已重命名项的对象。</span><span class="sxs-lookup"><span data-stu-id="1ada1-174">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="1ada1-175">如果指定 **PassThru** 参数，则此 cmdlet 将生成一个表示已重命名的项的对象。</span><span class="sxs-lookup"><span data-stu-id="1ada1-175">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="1ada1-176">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="1ada1-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1ada1-177">注释</span><span class="sxs-lookup"><span data-stu-id="1ada1-177">NOTES</span></span>

<span data-ttu-id="1ada1-178">`Rename-Item` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="1ada1-178">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="1ada1-179">若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="1ada1-179">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="1ada1-180">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1ada1-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1ada1-181">相关链接</span><span class="sxs-lookup"><span data-stu-id="1ada1-181">RELATED LINKS</span></span>

[<span data-ttu-id="1ada1-182">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-182">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="1ada1-183">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-183">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="1ada1-184">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1ada1-184">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="1ada1-185">Get-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="1ada1-186">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-186">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="1ada1-187">Move-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-187">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="1ada1-188">New-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-188">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="1ada1-189">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-189">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="1ada1-190">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1ada1-190">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="1ada1-191">Set-Item</span><span class="sxs-lookup"><span data-stu-id="1ada1-191">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="1ada1-192">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1ada1-192">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

