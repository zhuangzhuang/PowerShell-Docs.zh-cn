---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: 96f4385c899a50a361fb6df55b40d1ce77225a5b
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196299"
---
# <span data-ttu-id="314d3-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="314d3-102">Join-String</span></span>

## <span data-ttu-id="314d3-103">摘要</span><span class="sxs-lookup"><span data-stu-id="314d3-103">SYNOPSIS</span></span>
<span data-ttu-id="314d3-104">将管道中的对象合并为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="314d3-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="314d3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="314d3-105">SYNTAX</span></span>

### <span data-ttu-id="314d3-106">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="314d3-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="314d3-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="314d3-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="314d3-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="314d3-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="314d3-109">格式</span><span class="sxs-lookup"><span data-stu-id="314d3-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="314d3-110">说明</span><span class="sxs-lookup"><span data-stu-id="314d3-110">DESCRIPTION</span></span>

<span data-ttu-id="314d3-111">`Join-String`Cmdlet 将管道对象中的文本联接或组合成单个字符串。</span><span class="sxs-lookup"><span data-stu-id="314d3-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="314d3-112">如果未指定任何参数，则管道对象将转换为字符串，并使用默认分隔符进行联接 `$OFS` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="314d3-113">通过指定属性名称，将属性的值转换为字符串，并将其联接到字符串中。</span><span class="sxs-lookup"><span data-stu-id="314d3-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="314d3-114">可以使用脚本块，而不是属性名称。</span><span class="sxs-lookup"><span data-stu-id="314d3-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="314d3-115">脚本块的结果在联接之前将转换为字符串，以形成结果。</span><span class="sxs-lookup"><span data-stu-id="314d3-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="314d3-116">它可以将对象的属性的文本或已转换为字符串的对象的结果合并在一起。</span><span class="sxs-lookup"><span data-stu-id="314d3-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="314d3-117">此 cmdlet 是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="314d3-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="314d3-118">示例</span><span class="sxs-lookup"><span data-stu-id="314d3-118">EXAMPLES</span></span>

### <span data-ttu-id="314d3-119">示例1：联接目录名称</span><span class="sxs-lookup"><span data-stu-id="314d3-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="314d3-120">此示例将目录名称连接起来，用双引号将输出进行包装，并使用逗号和空格分隔目录名称 (`, `) 。</span><span class="sxs-lookup"><span data-stu-id="314d3-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="314d3-121">输出是一个字符串对象。</span><span class="sxs-lookup"><span data-stu-id="314d3-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="314d3-122">`Get-ChildItem` 使用 **Directory** 参数获取驱动器的所有目录名称 `C:\` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="314d3-123">对象将向下发送到 `Join-String` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="314d3-124">**Property** 参数指定目录名称。</span><span class="sxs-lookup"><span data-stu-id="314d3-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="314d3-125">**DoubleQuote** 参数将目录名称用双引号引起来。</span><span class="sxs-lookup"><span data-stu-id="314d3-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="314d3-126">**Separator** 参数指定使用逗号和空格 (`, `) 分隔目录名称。</span><span class="sxs-lookup"><span data-stu-id="314d3-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="314d3-127">`Get-ChildItem`对象为 **DirectoryInfo** ，并 `Join-String` 将对象转换为 **system.string**。</span><span class="sxs-lookup"><span data-stu-id="314d3-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String**.</span></span>

### <span data-ttu-id="314d3-128">示例2：使用属性子字符串来联接目录名称</span><span class="sxs-lookup"><span data-stu-id="314d3-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="314d3-129">此示例使用 substring 方法获取目录名称的前四个字母，将输出包装在单引号内，并用分号分隔目录名称 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="314d3-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="314d3-130">`Get-ChildItem` 使用 **Directory** 参数获取驱动器的所有目录名称 `C:\` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="314d3-131">对象将向下发送到 `Join-String` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="314d3-132">**属性** 参数脚本块使用自动变量 (`$_`) 来指定每个对象的 **Name** 属性子字符串。</span><span class="sxs-lookup"><span data-stu-id="314d3-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="314d3-133">子字符串获取每个目录名称的前四个字母。</span><span class="sxs-lookup"><span data-stu-id="314d3-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="314d3-134">子字符串指定字符的开始位置和结束位置。</span><span class="sxs-lookup"><span data-stu-id="314d3-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="314d3-135">**SingleQuote** 参数将目录名称用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="314d3-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="314d3-136">**Separator** 参数指定使用分号 (`;`) 来分隔目录名称。</span><span class="sxs-lookup"><span data-stu-id="314d3-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="314d3-137">有关自动变量和子字符串的详细信息，请参阅 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 和 [Substring](/dotnet/api/system.string.substring)。</span><span class="sxs-lookup"><span data-stu-id="314d3-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="314d3-138">示例3：在单独的行上显示联接输出</span><span class="sxs-lookup"><span data-stu-id="314d3-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="314d3-139">此示例将服务名称与每个服务联接在单独的行上，并通过选项卡进行缩进。</span><span class="sxs-lookup"><span data-stu-id="314d3-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="314d3-140">`Get-Service` 将 **Name** 参数与结合使用来指定以开头的服务 `se*` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="314d3-141">星号 (`*`) 是任何字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="314d3-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="314d3-142">对象通过管道向下发送 `Join-String` ，后者使用 **Property** 参数来指定服务名称。</span><span class="sxs-lookup"><span data-stu-id="314d3-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="314d3-143">**Separator** 参数指定三个特殊字符，这些字符表示 (`` `r ``) 、换行符 (`` `n ``) 和制表符 () 的回车符 `` `t `` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="314d3-144">**OutputPrefix** 插入标签 **服务：** 在输出的第一行之前添加新行和制表符。</span><span class="sxs-lookup"><span data-stu-id="314d3-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="314d3-145">有关特殊字符的详细信息，请参阅 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)。</span><span class="sxs-lookup"><span data-stu-id="314d3-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="314d3-146">示例4：从对象创建类定义</span><span class="sxs-lookup"><span data-stu-id="314d3-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="314d3-147">此示例使用现有对象作为模板生成 PowerShell 类定义。</span><span class="sxs-lookup"><span data-stu-id="314d3-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="314d3-148">此代码示例使用展开缩短行长度，提高可读性。</span><span class="sxs-lookup"><span data-stu-id="314d3-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="314d3-149">有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="314d3-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="314d3-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="314d3-150">PARAMETERS</span></span>

### <span data-ttu-id="314d3-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="314d3-151">-DoubleQuote</span></span>

<span data-ttu-id="314d3-152">用双引号将每个管道对象的字符串值括起来。</span><span class="sxs-lookup"><span data-stu-id="314d3-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-153">-格式字符串</span><span class="sxs-lookup"><span data-stu-id="314d3-153">-FormatString</span></span>

<span data-ttu-id="314d3-154">指定如何设置每个项的格式的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="314d3-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="314d3-155">-InputObject</span></span>

<span data-ttu-id="314d3-156">指定要联接的文本。</span><span class="sxs-lookup"><span data-stu-id="314d3-156">Specifies the text to be joined.</span></span> <span data-ttu-id="314d3-157">输入包含文本的变量，或键入获取要联接到字符串中的对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="314d3-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="314d3-158">-OutputPrefix</span></span>

<span data-ttu-id="314d3-159">在输出字符串之前插入的文本。</span><span class="sxs-lookup"><span data-stu-id="314d3-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="314d3-160">字符串可以包含特殊字符，如回车符 (`` `r ``) 、换行符 (`` `n ``) 和制表符 (`` `t ``) 。</span><span class="sxs-lookup"><span data-stu-id="314d3-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="314d3-161">-OutputSuffix</span></span>

<span data-ttu-id="314d3-162">追加到输出字符串的文本。</span><span class="sxs-lookup"><span data-stu-id="314d3-162">Text that's appended to the output string.</span></span> <span data-ttu-id="314d3-163">字符串可以包含特殊字符，如回车符 (`` `r ``) 、换行符 (`` `n ``) 和制表符 (`` `t ``) 。</span><span class="sxs-lookup"><span data-stu-id="314d3-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-164">-Property</span><span class="sxs-lookup"><span data-stu-id="314d3-164">-Property</span></span>

<span data-ttu-id="314d3-165">将管道对象投影到文本的属性名称或属性表达式。</span><span class="sxs-lookup"><span data-stu-id="314d3-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-166">-Separator</span><span class="sxs-lookup"><span data-stu-id="314d3-166">-Separator</span></span>

<span data-ttu-id="314d3-167">在每个管道对象的文本之间插入的文本或字符，如逗号或分号。</span><span class="sxs-lookup"><span data-stu-id="314d3-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="314d3-168">-SingleQuote</span></span>

<span data-ttu-id="314d3-169">用单引号将每个管道对象的字符串值包装。</span><span class="sxs-lookup"><span data-stu-id="314d3-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314d3-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="314d3-170">-UseCulture</span></span>

<span data-ttu-id="314d3-171">将当前区域性的列表分隔符用作项分隔符。</span><span class="sxs-lookup"><span data-stu-id="314d3-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="314d3-172">若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="314d3-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="314d3-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="314d3-173">CommonParameters</span></span>

<span data-ttu-id="314d3-174">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="314d3-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="314d3-175">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="314d3-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="314d3-176">输入</span><span class="sxs-lookup"><span data-stu-id="314d3-176">INPUTS</span></span>

### <span data-ttu-id="314d3-177">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="314d3-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="314d3-178">输出</span><span class="sxs-lookup"><span data-stu-id="314d3-178">OUTPUTS</span></span>

### <span data-ttu-id="314d3-179">System.String</span><span class="sxs-lookup"><span data-stu-id="314d3-179">System.String</span></span>

## <span data-ttu-id="314d3-180">注释</span><span class="sxs-lookup"><span data-stu-id="314d3-180">NOTES</span></span>

## <span data-ttu-id="314d3-181">相关链接</span><span class="sxs-lookup"><span data-stu-id="314d3-181">RELATED LINKS</span></span>

[<span data-ttu-id="314d3-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="314d3-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="314d3-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="314d3-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="314d3-184">个子</span><span class="sxs-lookup"><span data-stu-id="314d3-184">Substring</span></span>](/dotnet/api/system.string.substring)

