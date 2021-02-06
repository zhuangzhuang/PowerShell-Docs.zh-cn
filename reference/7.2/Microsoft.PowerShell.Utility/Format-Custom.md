---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596011"
---
# <span data-ttu-id="e63ab-102">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e63ab-102">Format-Custom</span></span>

## <span data-ttu-id="e63ab-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e63ab-103">SYNOPSIS</span></span>
<span data-ttu-id="e63ab-104">使用自定义的视图来设置输出格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-104">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="e63ab-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e63ab-105">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="e63ab-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e63ab-106">DESCRIPTION</span></span>

<span data-ttu-id="e63ab-107">`Format-Custom`Cmdlet 将命令的输出格式设置为替代视图中的定义。</span><span class="sxs-lookup"><span data-stu-id="e63ab-107">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="e63ab-108">`Format-Custom` 旨在显示不只是表格或只是列表的视图。</span><span class="sxs-lookup"><span data-stu-id="e63ab-108">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="e63ab-109">你可以使用在 PowerShell 中定义的视图，也可以在新文件中创建你自己的视图， `format.ps1xml` 并使用 `Update-FormatData` cmdlet 将它们添加到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e63ab-109">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="e63ab-110">示例</span><span class="sxs-lookup"><span data-stu-id="e63ab-110">EXAMPLES</span></span>

### <span data-ttu-id="e63ab-111">示例1：使用自定义视图设置输出格式</span><span class="sxs-lookup"><span data-stu-id="e63ab-111">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="e63ab-112">此命令使用 `Start-Transcript` MyView 视图（用户创建的自定义视图）定义的格式设置有关 cmdlet 的信息的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-112">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="e63ab-113">若要成功运行此命令，必须首先创建一个新的 TYPES.PS1XML 文件，定义 **MyView** 视图，然后使用 `Update-FormatData` 命令将 types.ps1xml 文件添加到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e63ab-113">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="e63ab-114">示例2：用默认视图设置输出格式</span><span class="sxs-lookup"><span data-stu-id="e63ab-114">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="e63ab-115">此命令设置有关其他自定义视图中 **Winlogon** 进程的信息的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-115">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="e63ab-116">由于该命令不使用 **View** 参数，因此将 `Format-Custom` 使用默认的自定义视图来设置数据的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-116">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="e63ab-117">示例3：疑难解答格式错误</span><span class="sxs-lookup"><span data-stu-id="e63ab-117">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="e63ab-118">下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。</span><span class="sxs-lookup"><span data-stu-id="e63ab-118">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="e63ab-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e63ab-119">PARAMETERS</span></span>

### <span data-ttu-id="e63ab-120">-Depth</span><span class="sxs-lookup"><span data-stu-id="e63ab-120">-Depth</span></span>

<span data-ttu-id="e63ab-121">指定显示中的列数。</span><span class="sxs-lookup"><span data-stu-id="e63ab-121">Specifies the number of columns in the display.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e63ab-122">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="e63ab-122">-DisplayError</span></span>

<span data-ttu-id="e63ab-123">在命令行中显示错误。</span><span class="sxs-lookup"><span data-stu-id="e63ab-123">Displays errors at the command line.</span></span> <span data-ttu-id="e63ab-124">此参数很少使用，但当你在命令中设置表达式的格式 `Format-Custom` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="e63ab-124">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="e63ab-125">-Expand</span><span class="sxs-lookup"><span data-stu-id="e63ab-125">-Expand</span></span>

<span data-ttu-id="e63ab-126">设置集合对象以及集合中的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-126">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="e63ab-127">此参数旨在设置支持 **system.object** 接口的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-127">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="e63ab-128">默认值为 **EnumOnly**。</span><span class="sxs-lookup"><span data-stu-id="e63ab-128">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="e63ab-129">有效值是：</span><span class="sxs-lookup"><span data-stu-id="e63ab-129">Valid values are:</span></span>

- <span data-ttu-id="e63ab-130">EnumOnly：显示集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-130">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="e63ab-131">CoreOnly：显示集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-131">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="e63ab-132">Both：显示集合对象和集合中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-132">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e63ab-133">-Force</span><span class="sxs-lookup"><span data-stu-id="e63ab-133">-Force</span></span>

<span data-ttu-id="e63ab-134">指示 cmdlet 显示所有错误信息。</span><span class="sxs-lookup"><span data-stu-id="e63ab-134">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="e63ab-135">与 **DisplayError** 或 **ShowError** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="e63ab-135">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="e63ab-136">默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。</span><span class="sxs-lookup"><span data-stu-id="e63ab-136">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="e63ab-137">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="e63ab-137">-GroupBy</span></span>

<span data-ttu-id="e63ab-138">基于共享属性或值设置组中输出的格式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-138">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="e63ab-139">请输入表达式或输出的属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-139">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="e63ab-140">**GroupBy** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-140">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="e63ab-141">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="e63ab-141">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e63ab-142">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="e63ab-142">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e63ab-143">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="e63ab-143">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="e63ab-144">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e63ab-144">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="e63ab-145">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="e63ab-145">FormatString - `<string>`</span></span>

<span data-ttu-id="e63ab-146">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e63ab-146">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e63ab-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e63ab-147">-InputObject</span></span>

<span data-ttu-id="e63ab-148">指定要设置格式的对象。</span><span class="sxs-lookup"><span data-stu-id="e63ab-148">Specifies the objects to be formatted.</span></span> <span data-ttu-id="e63ab-149">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="e63ab-149">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e63ab-150">-Property</span><span class="sxs-lookup"><span data-stu-id="e63ab-150">-Property</span></span>

<span data-ttu-id="e63ab-151">指定要在屏幕上显示的对象属性及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="e63ab-151">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="e63ab-152">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="e63ab-152">Wildcards are permitted.</span></span>

<span data-ttu-id="e63ab-153">如果省略此参数，则屏幕上显示的属性取决于要显示的对象。</span><span class="sxs-lookup"><span data-stu-id="e63ab-153">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="e63ab-154">参数 name **属性** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="e63ab-154">The parameter name **Property** is optional.</span></span> <span data-ttu-id="e63ab-155">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="e63ab-155">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="e63ab-156">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="e63ab-156">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e63ab-157">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="e63ab-157">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e63ab-158">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="e63ab-158">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e63ab-159">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e63ab-159">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="e63ab-160">长度 `<int32>`</span><span class="sxs-lookup"><span data-stu-id="e63ab-160">Depth - `<int32>`</span></span>

<span data-ttu-id="e63ab-161">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e63ab-161">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e63ab-162">-ShowError</span><span class="sxs-lookup"><span data-stu-id="e63ab-162">-ShowError</span></span>

<span data-ttu-id="e63ab-163">通过管道发送错误。</span><span class="sxs-lookup"><span data-stu-id="e63ab-163">Sends errors through the pipeline.</span></span> <span data-ttu-id="e63ab-164">此参数很少使用，但当你在命令中设置表达式的格式 `Format-Custom` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="e63ab-164">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="e63ab-165">-View</span><span class="sxs-lookup"><span data-stu-id="e63ab-165">-View</span></span>

<span data-ttu-id="e63ab-166">指定替代格式或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="e63ab-166">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="e63ab-167">如果省略此参数，则 `Format-Custom` 使用默认的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="e63ab-167">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="e63ab-168">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="e63ab-168">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="e63ab-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e63ab-169">CommonParameters</span></span>

<span data-ttu-id="e63ab-170">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e63ab-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e63ab-171">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e63ab-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e63ab-172">输入</span><span class="sxs-lookup"><span data-stu-id="e63ab-172">INPUTS</span></span>

### <span data-ttu-id="e63ab-173">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="e63ab-173">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e63ab-174">可以通过管道将任何对象传递给 `Format-Custom` 。</span><span class="sxs-lookup"><span data-stu-id="e63ab-174">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="e63ab-175">输出</span><span class="sxs-lookup"><span data-stu-id="e63ab-175">OUTPUTS</span></span>

### <span data-ttu-id="e63ab-176">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="e63ab-176">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="e63ab-177">`Format-Custom` 返回表示显示的格式对象。</span><span class="sxs-lookup"><span data-stu-id="e63ab-177">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="e63ab-178">注释</span><span class="sxs-lookup"><span data-stu-id="e63ab-178">NOTES</span></span>

<span data-ttu-id="e63ab-179">`Format-Custom` 旨在显示不只是表格或只是列表的视图。</span><span class="sxs-lookup"><span data-stu-id="e63ab-179">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="e63ab-180">若要显示替代表视图，请使用 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="e63ab-180">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="e63ab-181">若要显示替代列表视图，请使用 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="e63ab-181">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="e63ab-182">还可以 `Format-Custom` 通过其内置别名来引用 `fc` 。</span><span class="sxs-lookup"><span data-stu-id="e63ab-182">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="e63ab-183">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="e63ab-183">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="e63ab-184">**GroupBy** 参数假定对象已排序。</span><span class="sxs-lookup"><span data-stu-id="e63ab-184">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="e63ab-185">使用对 `Format-Custom` 对象进行分组之前，请使用对 `Sort-Object` 它们进行排序。</span><span class="sxs-lookup"><span data-stu-id="e63ab-185">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="e63ab-186">相关链接</span><span class="sxs-lookup"><span data-stu-id="e63ab-186">RELATED LINKS</span></span>

[<span data-ttu-id="e63ab-187">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e63ab-187">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e63ab-188">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="e63ab-188">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="e63ab-189">Format-List</span><span class="sxs-lookup"><span data-stu-id="e63ab-189">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="e63ab-190">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e63ab-190">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="e63ab-191">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e63ab-191">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="e63ab-192">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e63ab-192">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
