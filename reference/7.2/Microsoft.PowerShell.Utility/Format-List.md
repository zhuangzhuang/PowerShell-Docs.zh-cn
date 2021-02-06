---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603398"
---
# <span data-ttu-id="623a7-102">Format-List</span><span class="sxs-lookup"><span data-stu-id="623a7-102">Format-List</span></span>

## <span data-ttu-id="623a7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="623a7-103">SYNOPSIS</span></span>
<span data-ttu-id="623a7-104">将输出的格式设置为属性列表，其中每个属性都显示在一个新行上。</span><span class="sxs-lookup"><span data-stu-id="623a7-104">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="623a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="623a7-105">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="623a7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="623a7-106">DESCRIPTION</span></span>

<span data-ttu-id="623a7-107">`Format-List`Cmdlet 将命令输出的格式设置为属性列表，其中每个属性都显示在单独的行上。</span><span class="sxs-lookup"><span data-stu-id="623a7-107">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="623a7-108">您可以使用 `Format-List` 将对象的全部或所选属性的格式设置为列表 (格式列表 \* ) 。</span><span class="sxs-lookup"><span data-stu-id="623a7-108">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="623a7-109">由于列表中的每个项都有更多可用空间，因此 PowerShell 将在列表中显示该对象的更多属性，并且属性值不太可能被截断。</span><span class="sxs-lookup"><span data-stu-id="623a7-109">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="623a7-110">示例</span><span class="sxs-lookup"><span data-stu-id="623a7-110">EXAMPLES</span></span>

### <span data-ttu-id="623a7-111">示例1：格式化计算机服务</span><span class="sxs-lookup"><span data-stu-id="623a7-111">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="623a7-112">此命令将计算机上服务的相关信息的格式设置为列表。</span><span class="sxs-lookup"><span data-stu-id="623a7-112">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="623a7-113">默认情况下，将这些服务的格式设置为表。</span><span class="sxs-lookup"><span data-stu-id="623a7-113">By default, the services are formatted as a table.</span></span> <span data-ttu-id="623a7-114">`Get-Service`Cmdlet 将获取表示计算机上的服务的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-114">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="623a7-115">管道运算符 (|) 通过管道将结果传递给 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-115">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="623a7-116">然后，该 `Format-List` 命令将服务信息的格式设置为列表，并将其发送到默认的输出 cmdlet 以供显示。</span><span class="sxs-lookup"><span data-stu-id="623a7-116">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="623a7-117">示例2：格式化 TYPES.PS1XML 文件</span><span class="sxs-lookup"><span data-stu-id="623a7-117">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="623a7-118">这些命令以列表的形式显示有关 PowerShell 目录中的 TYPES.PS1XML 文件的信息。</span><span class="sxs-lookup"><span data-stu-id="623a7-118">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="623a7-119">第一个命令获取表示文件的对象，并将其存储在 `$A` 变量中。</span><span class="sxs-lookup"><span data-stu-id="623a7-119">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="623a7-120">第二个命令使用 `Format-List` 来设置有关存储在中的对象的信息的格式 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-120">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="623a7-121">此命令使用 **InputObject** 参数将该变量传递给 `Format-List` ，后者随后会将格式化输出发送到默认的输出 cmdlet 以供显示。</span><span class="sxs-lookup"><span data-stu-id="623a7-121">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="623a7-122">示例3：按名称设置进程属性的格式</span><span class="sxs-lookup"><span data-stu-id="623a7-122">Example 3: Format process properties by name</span></span>

<span data-ttu-id="623a7-123">此命令将显示计算机上每个进程的名称、基本优先级和优先级类。</span><span class="sxs-lookup"><span data-stu-id="623a7-123">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="623a7-124">它使用 `Get-Process` cmdlet 来获取表示每个进程的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-124">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="623a7-125">管道运算符 (|) 将进程对象通过管道传递给 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-125">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="623a7-126">`Format-List` 将进程的格式设置为指定属性的列表。</span><span class="sxs-lookup"><span data-stu-id="623a7-126">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="623a7-127">*属性* 参数名称是可选的，因此可以省略它。</span><span class="sxs-lookup"><span data-stu-id="623a7-127">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="623a7-128">示例4：设置进程的所有属性的格式</span><span class="sxs-lookup"><span data-stu-id="623a7-128">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="623a7-129">此命令显示 Winlogon 进程的所有属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-129">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="623a7-130">它使用 Get-Process cmdlet 来获取表示 Winlogon 进程的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-130">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="623a7-131">管道运算符 (|) 通过管道将 Winlogon 进程对象传递给 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-131">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="623a7-132">该命令使用 *Property* 参数来指定属性，并使用 \* 来指示所有属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-132">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="623a7-133">因为 *属性* 参数的名称是可选的，所以可以省略它，然后将命令键入为 `Format-List *` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-133">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="623a7-134">`Format-List` 自动将结果发送到默认的输出 cmdlet 以供显示。</span><span class="sxs-lookup"><span data-stu-id="623a7-134">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="623a7-135">示例5：排查格式错误</span><span class="sxs-lookup"><span data-stu-id="623a7-135">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="623a7-136">下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。</span><span class="sxs-lookup"><span data-stu-id="623a7-136">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="623a7-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="623a7-137">PARAMETERS</span></span>

### <span data-ttu-id="623a7-138">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="623a7-138">-DisplayError</span></span>

<span data-ttu-id="623a7-139">指示此 cmdlet 在命令行中显示错误。</span><span class="sxs-lookup"><span data-stu-id="623a7-139">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="623a7-140">此参数很少使用，但当你在命令中设置表达式的格式 `Format-List` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="623a7-140">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="623a7-141">-Expand</span><span class="sxs-lookup"><span data-stu-id="623a7-141">-Expand</span></span>

<span data-ttu-id="623a7-142">指定格式化的集合对象以及集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-142">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="623a7-143">此参数旨在用于设置支持 ICollection (System.Collections) 接口的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="623a7-143">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="623a7-144">默认值为 EnumOnly。</span><span class="sxs-lookup"><span data-stu-id="623a7-144">The default value is EnumOnly.</span></span> <span data-ttu-id="623a7-145">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="623a7-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="623a7-146">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="623a7-146">EnumOnly.</span></span> <span data-ttu-id="623a7-147">显示集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-147">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="623a7-148">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="623a7-148">CoreOnly.</span></span> <span data-ttu-id="623a7-149">显示集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-149">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="623a7-150">两者。</span><span class="sxs-lookup"><span data-stu-id="623a7-150">Both.</span></span> <span data-ttu-id="623a7-151">显示集合对象的属性以及集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-151">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="623a7-152">-Force</span><span class="sxs-lookup"><span data-stu-id="623a7-152">-Force</span></span>

<span data-ttu-id="623a7-153">指示此 cmdlet 显示所有错误信息。</span><span class="sxs-lookup"><span data-stu-id="623a7-153">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="623a7-154">与 **DisplayError** 或 **ShowError** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="623a7-154">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="623a7-155">默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。</span><span class="sxs-lookup"><span data-stu-id="623a7-155">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="623a7-156">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="623a7-156">-GroupBy</span></span>

<span data-ttu-id="623a7-157">基于共享属性或值指定组中的输出。</span><span class="sxs-lookup"><span data-stu-id="623a7-157">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="623a7-158">请输入表达式或输出的属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-158">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="623a7-159">**GroupBy** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-159">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="623a7-160">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="623a7-160">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="623a7-161">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="623a7-161">Valid key-value pairs are:</span></span>

- <span data-ttu-id="623a7-162">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="623a7-162">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="623a7-163">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="623a7-163">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="623a7-164">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="623a7-164">FormatString - `<string>`</span></span>

<span data-ttu-id="623a7-165">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="623a7-165">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="623a7-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="623a7-166">-InputObject</span></span>

<span data-ttu-id="623a7-167">指定要设置格式的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-167">Specifies the objects to be formatted.</span></span> <span data-ttu-id="623a7-168">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="623a7-168">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="623a7-169">-Property</span><span class="sxs-lookup"><span data-stu-id="623a7-169">-Property</span></span>

<span data-ttu-id="623a7-170">指定要在屏幕上显示的对象属性及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="623a7-170">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="623a7-171">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="623a7-171">Wildcards are permitted.</span></span>

<span data-ttu-id="623a7-172">如果省略此参数，则屏幕上显示的属性取决于要显示的对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-172">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="623a7-173">参数名称 "Property" 是可选的。</span><span class="sxs-lookup"><span data-stu-id="623a7-173">The parameter name "Property" is optional.</span></span> <span data-ttu-id="623a7-174">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="623a7-174">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="623a7-175">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="623a7-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="623a7-176">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="623a7-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="623a7-177">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="623a7-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="623a7-178">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="623a7-178">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="623a7-179">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="623a7-179">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="623a7-180">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="623a7-180">FormatString - `<string>`</span></span>

<span data-ttu-id="623a7-181">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="623a7-181">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="623a7-182">-ShowError</span><span class="sxs-lookup"><span data-stu-id="623a7-182">-ShowError</span></span>

<span data-ttu-id="623a7-183">指示 cmdlet 通过管道发送错误。</span><span class="sxs-lookup"><span data-stu-id="623a7-183">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="623a7-184">此参数很少使用，但当你在命令中设置表达式的格式 `Format-List` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="623a7-184">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="623a7-185">-View</span><span class="sxs-lookup"><span data-stu-id="623a7-185">-View</span></span>

<span data-ttu-id="623a7-186">指定替代列表格式或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="623a7-186">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="623a7-187">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="623a7-187">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="623a7-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="623a7-188">CommonParameters</span></span>

<span data-ttu-id="623a7-189">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="623a7-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="623a7-190">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="623a7-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="623a7-191">输入</span><span class="sxs-lookup"><span data-stu-id="623a7-191">INPUTS</span></span>

### <span data-ttu-id="623a7-192">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="623a7-192">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="623a7-193">可以通过管道将任何对象传递给 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-193">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="623a7-194">输出</span><span class="sxs-lookup"><span data-stu-id="623a7-194">OUTPUTS</span></span>

### <span data-ttu-id="623a7-195">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="623a7-195">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="623a7-196">`Format-List` 返回表示列表的格式对象。</span><span class="sxs-lookup"><span data-stu-id="623a7-196">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="623a7-197">注释</span><span class="sxs-lookup"><span data-stu-id="623a7-197">NOTES</span></span>

<span data-ttu-id="623a7-198">你还可以通过其内置别名 FL 来引用 Format-List。</span><span class="sxs-lookup"><span data-stu-id="623a7-198">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="623a7-199">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="623a7-199">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="623a7-200">格式 cmdlet （例如 `Format-List` ）用于排列要显示的数据，但不显示。</span><span class="sxs-lookup"><span data-stu-id="623a7-200">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="623a7-201">数据由 PowerShell 的输出功能以及包含 out cmdlet (Out) （如或）的 cmdlet 显示 `Out-Host` `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-201">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="623a7-202">如果未使用格式 cmdlet，则 PowerShell 会将其显示的每个对象应用默认格式。</span><span class="sxs-lookup"><span data-stu-id="623a7-202">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="623a7-203">**GroupBy** 参数假定对象已排序。</span><span class="sxs-lookup"><span data-stu-id="623a7-203">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="623a7-204">使用 Sort-Object，然后使用 `Format-List` 将对象分组。</span><span class="sxs-lookup"><span data-stu-id="623a7-204">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="623a7-205">使用 **View** 参数可以指定表的替代格式。</span><span class="sxs-lookup"><span data-stu-id="623a7-205">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="623a7-206">你可以使用 PowerShell 目录的文件中定义的视图 `*.format.PS1XML` ，也可以在新的 types.ps1xml 文件中创建你自己的视图，并使用 Update-FormatData cmdlet 将它们包含在 powershell 中。</span><span class="sxs-lookup"><span data-stu-id="623a7-206">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="623a7-207">**View** 参数的替代视图必须使用列表格式，否则，该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="623a7-207">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="623a7-208">如果替代视图是一个表，则使用 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-208">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="623a7-209">如果替代视图不是列表或表，请使用 `Format-Custom` 。</span><span class="sxs-lookup"><span data-stu-id="623a7-209">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="623a7-210">相关链接</span><span class="sxs-lookup"><span data-stu-id="623a7-210">RELATED LINKS</span></span>

[<span data-ttu-id="623a7-211">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="623a7-211">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="623a7-212">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="623a7-212">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="623a7-213">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="623a7-213">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="623a7-214">Format-Table</span><span class="sxs-lookup"><span data-stu-id="623a7-214">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="623a7-215">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="623a7-215">Format-Wide</span></span>](Format-Wide.md)
