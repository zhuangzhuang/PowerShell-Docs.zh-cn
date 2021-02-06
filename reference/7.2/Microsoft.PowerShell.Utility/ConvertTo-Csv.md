---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: df41ccf696e39d0bd6c90c118bd715ab83934cf2
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99595830"
---
# <span data-ttu-id="b668f-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="b668f-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="b668f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b668f-103">SYNOPSIS</span></span>
<span data-ttu-id="b668f-104">将 .NET 对象转换为一系列字符分隔值 (CSV) 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-104">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="b668f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b668f-105">SYNTAX</span></span>

### <span data-ttu-id="b668f-106">Delimiter（默认值）</span><span class="sxs-lookup"><span data-stu-id="b668f-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="b668f-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="b668f-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="b668f-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b668f-108">DESCRIPTION</span></span>

<span data-ttu-id="b668f-109">`ConvertTo-CSV`Cmdlet 将返回一系列逗号分隔值 (CSV) 字符串，这些字符串表示你提交的对象。</span><span class="sxs-lookup"><span data-stu-id="b668f-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="b668f-110">然后，可以使用 `ConvertFrom-Csv` cmdlet 从 CSV 字符串重新创建对象。</span><span class="sxs-lookup"><span data-stu-id="b668f-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="b668f-111">从 CSV 转换的对象是包含属性值和没有方法的原始对象的字符串值。</span><span class="sxs-lookup"><span data-stu-id="b668f-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="b668f-112">可以使用 `Export-Csv` cmdlet 将对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="b668f-113">`Export-CSV` 类似于 `ConvertTo-CSV` ，只不过它将 CSV 字符串保存到文件。</span><span class="sxs-lookup"><span data-stu-id="b668f-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="b668f-114">`ConvertTo-CSV`Cmdlet 具有参数以指定逗号以外的分隔符，或使用当前区域性作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="b668f-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="b668f-115">示例</span><span class="sxs-lookup"><span data-stu-id="b668f-115">EXAMPLES</span></span>

### <span data-ttu-id="b668f-116">示例1：将对象转换为 CSV</span><span class="sxs-lookup"><span data-stu-id="b668f-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="b668f-117">此示例将 **进程** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="b668f-118">该 `Get-Process` cmdlet 将获取 **Process** 对象，并使用 **Name** 参数来指定 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="b668f-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="b668f-119">进程对象将通过管道向下发送到 `ConvertTo-CSV` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b668f-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="b668f-120">`ConvertTo-CSV`Cmdlet 可将对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="b668f-121">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="b668f-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="b668f-122">示例2：将 DateTime 对象转换为 CSV</span><span class="sxs-lookup"><span data-stu-id="b668f-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="b668f-123">此示例将 **DateTime** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="b668f-124">该 `Get-Date` cmdlet 将获取 **DateTime** 对象并将其保存在 `$Date` 变量中。</span><span class="sxs-lookup"><span data-stu-id="b668f-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="b668f-125">`ConvertTo-Csv`Cmdlet 将 **DateTime** 对象转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="b668f-126">**InputObject** 参数使用存储在变量中的 **DateTime** 对象 `$Date` 。</span><span class="sxs-lookup"><span data-stu-id="b668f-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="b668f-127">**分隔符** 参数指定用分号分隔字符串值。</span><span class="sxs-lookup"><span data-stu-id="b668f-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="b668f-128">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="b668f-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="b668f-129">示例3：将 PowerShell 事件日志转换为 CSV</span><span class="sxs-lookup"><span data-stu-id="b668f-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="b668f-130">此示例将 PowerShell 的 Windows 事件日志转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="b668f-131">该 `Get-Culture` cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** ，并显示当前区域性的默认列表分隔符。</span><span class="sxs-lookup"><span data-stu-id="b668f-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="b668f-132">该 `Get-WinEvent` cmdlet 将获取事件日志对象，并使用 **LogName** 参数来指定日志文件名。</span><span class="sxs-lookup"><span data-stu-id="b668f-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="b668f-133">事件日志对象通过管道发送到 `ConvertTo-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b668f-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="b668f-134">`ConvertTo-Csv`Cmdlet 将事件日志对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="b668f-135">**UseCulture** 参数使用当前区域性的默认列表分隔符作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="b668f-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="b668f-136">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="b668f-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="b668f-137">示例4：转换为 CSV，并在两列两侧加上引号</span><span class="sxs-lookup"><span data-stu-id="b668f-137">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="b668f-138">此示例将 **DateTime** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-138">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="b668f-139">示例4：仅在需要时才将引号转换为 CSV</span><span class="sxs-lookup"><span data-stu-id="b668f-139">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="b668f-140">此示例将 **DateTime** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-140">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="b668f-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b668f-141">PARAMETERS</span></span>

### <span data-ttu-id="b668f-142">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="b668f-142">-Delimiter</span></span>

<span data-ttu-id="b668f-143">指定分隔 CSV 字符串中的属性值的分隔符。</span><span class="sxs-lookup"><span data-stu-id="b668f-143">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="b668f-144">默认值为逗号 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="b668f-144">The default is a comma (`,`).</span></span> <span data-ttu-id="b668f-145">输入一个字符，例如冒号 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="b668f-145">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="b668f-146">若要指定分号 (`;`) 将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="b668f-146">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-147">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="b668f-147">-IncludeTypeInformation</span></span>

<span data-ttu-id="b668f-148">使用此参数时，输出的第一行将包含 **#TYPE** 后跟对象类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="b668f-148">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="b668f-149">例如， **#TYPE**"。</span><span class="sxs-lookup"><span data-stu-id="b668f-149">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="b668f-150">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="b668f-150">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b668f-151">-InputObject</span></span>

<span data-ttu-id="b668f-152">指定转换为 CSV 字符串的对象。</span><span class="sxs-lookup"><span data-stu-id="b668f-152">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="b668f-153">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="b668f-153">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="b668f-154">还可以通过管道将对象传递给 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="b668f-154">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-155">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="b668f-155">-NoTypeInformation</span></span>

<span data-ttu-id="b668f-156">从输出中删除 **#TYPE** 信息标头。</span><span class="sxs-lookup"><span data-stu-id="b668f-156">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="b668f-157">此参数已成为 PowerShell 6.0 中的默认参数，包含它是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="b668f-157">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-158">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="b668f-158">-UseCulture</span></span>

<span data-ttu-id="b668f-159">将当前区域性的列表分隔符用作项分隔符。</span><span class="sxs-lookup"><span data-stu-id="b668f-159">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="b668f-160">若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="b668f-160">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-161">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="b668f-161">-QuoteFields</span></span>

<span data-ttu-id="b668f-162">指定应括起来的列的名称。</span><span class="sxs-lookup"><span data-stu-id="b668f-162">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="b668f-163">如果使用此参数，则仅将指定的列括起来。</span><span class="sxs-lookup"><span data-stu-id="b668f-163">When this parameter is used only the specified columns are quoted.</span></span> <span data-ttu-id="b668f-164">此参数是在 PowerShell 7.0 中添加的。</span><span class="sxs-lookup"><span data-stu-id="b668f-164">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="b668f-165">-UseQuotes</span></span>

<span data-ttu-id="b668f-166">指定在 CSV 文件中使用引号的时间。</span><span class="sxs-lookup"><span data-stu-id="b668f-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="b668f-167">可能的值有：</span><span class="sxs-lookup"><span data-stu-id="b668f-167">Possible values are:</span></span>

- <span data-ttu-id="b668f-168">从不-不引用任何内容</span><span class="sxs-lookup"><span data-stu-id="b668f-168">Never - don't quote anything</span></span>
- <span data-ttu-id="b668f-169">始终将所有内容都括 (默认行为) </span><span class="sxs-lookup"><span data-stu-id="b668f-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="b668f-170">AsNeeded-仅包含分隔符字符的引号字段</span><span class="sxs-lookup"><span data-stu-id="b668f-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="b668f-171">此参数是在 PowerShell 7.0 中添加的。</span><span class="sxs-lookup"><span data-stu-id="b668f-171">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b668f-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b668f-172">CommonParameters</span></span>

<span data-ttu-id="b668f-173">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b668f-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b668f-174">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b668f-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b668f-175">输入</span><span class="sxs-lookup"><span data-stu-id="b668f-175">INPUTS</span></span>

### <span data-ttu-id="b668f-176">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b668f-176">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b668f-177">可以通过管道将具有扩展类型系统 (ETS) 适配器的任何对象传递给 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="b668f-177">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="b668f-178">输出</span><span class="sxs-lookup"><span data-stu-id="b668f-178">OUTPUTS</span></span>

### <span data-ttu-id="b668f-179">System.String</span><span class="sxs-lookup"><span data-stu-id="b668f-179">System.String</span></span>

<span data-ttu-id="b668f-180">CSV 输出将作为字符串集合返回。</span><span class="sxs-lookup"><span data-stu-id="b668f-180">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="b668f-181">注释</span><span class="sxs-lookup"><span data-stu-id="b668f-181">NOTES</span></span>

<span data-ttu-id="b668f-182">采用 CSV 格式时，通过以逗号分隔的对象属性值列表来表示每个对象。</span><span class="sxs-lookup"><span data-stu-id="b668f-182">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="b668f-183">使用对象的 **ToString ( # B1** 方法将属性值转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="b668f-183">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="b668f-184">字符串由属性值名称表示。</span><span class="sxs-lookup"><span data-stu-id="b668f-184">The strings are represented by the property value name.</span></span> <span data-ttu-id="b668f-185">`ConvertTo-CSV` 不导出对象的方法。</span><span class="sxs-lookup"><span data-stu-id="b668f-185">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="b668f-186">CSV 字符串的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="b668f-186">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="b668f-187">如果使用了 **IncludeTypeInformation** ，则第一个字符串将包含 **#TYPE** 后跟对象类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="b668f-187">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="b668f-188">例如， **#TYPE**"。</span><span class="sxs-lookup"><span data-stu-id="b668f-188">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="b668f-189">如果未使用 **IncludeTypeInformation** ，则第一个字符串包括列标题。</span><span class="sxs-lookup"><span data-stu-id="b668f-189">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="b668f-190">标头以逗号分隔的列表的形式包含第一个对象的属性名称。</span><span class="sxs-lookup"><span data-stu-id="b668f-190">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="b668f-191">其余字符串包含每个对象的属性值的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="b668f-191">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="b668f-192">从 PowerShell 6.0 开始，的默认行为 `ConvertTo-CSV` 是不包括 CSV 中的 **#TYPE** 信息，并且 **NoTypeInformation** 是隐含的。</span><span class="sxs-lookup"><span data-stu-id="b668f-192">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="b668f-193">**IncludeTypeInformation** 可用于包含 **#TYPE** 信息并模拟 `ConvertTo-CSV` PowerShell 6.0 之前的默认行为。</span><span class="sxs-lookup"><span data-stu-id="b668f-193">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="b668f-194">当您将多个对象提交到时 `ConvertTo-CSV` ，将 `ConvertTo-CSV` 根据您提交的第一个对象的属性对字符串进行排序。</span><span class="sxs-lookup"><span data-stu-id="b668f-194">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="b668f-195">如果剩余的对象没有指定的属性之一，则该对象的属性值为 Null，由两个连续的逗号表示。</span><span class="sxs-lookup"><span data-stu-id="b668f-195">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="b668f-196">如果剩余的对象具有其他属性，则忽略这些属性值。</span><span class="sxs-lookup"><span data-stu-id="b668f-196">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="b668f-197">相关链接</span><span class="sxs-lookup"><span data-stu-id="b668f-197">RELATED LINKS</span></span>

[<span data-ttu-id="b668f-198">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="b668f-198">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="b668f-199">导出-Csv</span><span class="sxs-lookup"><span data-stu-id="b668f-199">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="b668f-200">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="b668f-200">Import-Csv</span></span>](Import-Csv.md)
