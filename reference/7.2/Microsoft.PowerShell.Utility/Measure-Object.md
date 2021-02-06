---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 594837b2f85f4d5d5d4125d3f7c63ad2c8a16153
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597464"
---
# <span data-ttu-id="2dcf6-102">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-102">Measure-Object</span></span>

## <span data-ttu-id="2dcf6-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2dcf6-103">SYNOPSIS</span></span>
<span data-ttu-id="2dcf6-104">计算对象的数值属性，以及字符串对象（如文本文件）中的字符、单词和行。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-104">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="2dcf6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2dcf6-105">SYNTAX</span></span>

### <span data-ttu-id="2dcf6-106">GenericMeasure（默认值）</span><span class="sxs-lookup"><span data-stu-id="2dcf6-106">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="2dcf6-107">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="2dcf6-107">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="2dcf6-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2dcf6-108">DESCRIPTION</span></span>

<span data-ttu-id="2dcf6-109">`Measure-Object`Cmdlet 计算特定类型的对象的属性值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-109">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="2dcf6-110">`Measure-Object` 执行三种类型的度量，具体取决于命令中的参数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-110">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="2dcf6-111">`Measure-Object`Cmdlet 对对象的属性值执行计算。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-111">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="2dcf6-112">您可以使用 `Measure-Object` 来对对象进行计数，或使用指定 **属性** 对对象计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-112">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="2dcf6-113">还可以使用 `Measure-Object` 来计算数值的 **最小** 值、 **最大** 值、 **总和**、 **StandardDeviation** 值和 **平均值** 。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-113">You can also use `Measure-Object` to calculate the **Minimum**, **Maximum**, **Sum**, **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="2dcf6-114">对于 **字符串** 对象，还可以使用 `Measure-Object` 来计算行数、字数和字符数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-114">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="2dcf6-115">示例</span><span class="sxs-lookup"><span data-stu-id="2dcf6-115">EXAMPLES</span></span>

### <span data-ttu-id="2dcf6-116">示例 1：计数目录中的文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="2dcf6-116">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="2dcf6-117">此命令对当前目录中的文件和文件夹进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-117">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="2dcf6-118">示例 2：度量目录中的文件</span><span class="sxs-lookup"><span data-stu-id="2dcf6-118">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="2dcf6-119">此命令显示当前目录中所有文件的大小的 **最小值**、 **最大** 值和 **总和** ，以及目录中的文件的平均大小。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-119">This command displays the **Minimum**, **Maximum**, and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="2dcf6-120">示例 3：度量文本文件中的文本</span><span class="sxs-lookup"><span data-stu-id="2dcf6-120">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="2dcf6-121">此命令显示 Text.txt 文件中的字符数、字数和行数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-121">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="2dcf6-122">如果没有 **Raw** 参数，则会 `Get-Content` 将文件作为行的数组输出。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-122">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="2dcf6-123">第一个命令使用 `Set-Content` 将一些默认文本添加到文件。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-123">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="2dcf6-124">示例4：度量值对象包含指定属性</span><span class="sxs-lookup"><span data-stu-id="2dcf6-124">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="2dcf6-125">此示例对具有 **DisplayName** 属性的对象的数目进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-125">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="2dcf6-126">前两个命令检索本地计算机上的所有服务和进程。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-126">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="2dcf6-127">第三个命令对服务和进程的组合数量进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-127">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="2dcf6-128">最后一个命令将结果与结果组合在一起 `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-128">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="2dcf6-129">" **System.object** " 对象没有 **DisplayName** 属性，并且不在最终的计数中。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-129">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="2dcf6-130">示例 5：度量 CSV 文件的内容</span><span class="sxs-lookup"><span data-stu-id="2dcf6-130">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="2dcf6-131">此命令计算一家公司雇员的平均服务年限。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-131">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="2dcf6-132">该 `ServiceYrs.csv` 文件是一个 CSV 文件，其中包含每个员工的员工人数和年服务。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-132">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="2dcf6-133">表中的第一行是 **EmpNo**， **年** 的标题行。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-133">The first row in the table is a header row of **EmpNo**, **Years**.</span></span>

<span data-ttu-id="2dcf6-134">当你使用 `Import-Csv` 导入文件时，结果将是 **PSCustomObject** ，其便笺属性为 **EmpNo** 和 **年**。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-134">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="2dcf6-135">您可以使用 `Measure-Object` 来计算这些属性的值，就像对象的任何其他属性一样。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-135">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="2dcf6-136">示例 6：度量布尔值</span><span class="sxs-lookup"><span data-stu-id="2dcf6-136">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="2dcf6-137">此示例演示如何 `Measure-Object` 测量布尔值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-137">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="2dcf6-138">在这种情况下，它使用 **PSIsContainer** **布尔** 值属性来测量当前目录中 () 文件夹的发生情况。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-138">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="2dcf6-139">示例7：度量值字符串</span><span class="sxs-lookup"><span data-stu-id="2dcf6-139">Example 7: Measure strings</span></span>

<span data-ttu-id="2dcf6-140">下面的示例测量行数，首先是单个字符串，然后是多个字符串。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-140">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="2dcf6-141">换行符将 <code>\`n</code> 字符串分隔为多个行。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-141">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### <span data-ttu-id="2dcf6-142">示例8：度量所有值</span><span class="sxs-lookup"><span data-stu-id="2dcf6-142">Example 8: Measure all the values</span></span>

<span data-ttu-id="2dcf6-143">从 PowerShell 6 开始，的 **AllStats** 参数 `Measure-Object` 允许你将所有统计信息一起测量。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-143">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### <span data-ttu-id="2dcf6-144">示例9：使用 scriptblock 属性测量</span><span class="sxs-lookup"><span data-stu-id="2dcf6-144">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="2dcf6-145">从 PowerShell 6 开始， `Measure-Object` 支持 **ScriptBlock** 属性。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-145">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="2dcf6-146">下面的示例演示如何使用 **ScriptBlock** 属性来确定目录中所有文件的大小（以 Mb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-146">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="2dcf6-147">示例10：度量值哈希表</span><span class="sxs-lookup"><span data-stu-id="2dcf6-147">Example 10: Measure hashtables</span></span>

<span data-ttu-id="2dcf6-148">从 PowerShell 6 开始， `Measure-Object` 支持度量 **哈希表** 输入。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-148">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="2dcf6-149">下面的示例确定 `num` 3 个 **哈希表** 对象的键的最大值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-149">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### <span data-ttu-id="2dcf6-150">示例11：度量标准偏差</span><span class="sxs-lookup"><span data-stu-id="2dcf6-150">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="2dcf6-151">从 PowerShell 6 开始， `Measure-Object` 支持 `-StandardDeviation` 参数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-151">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="2dcf6-152">下面的示例确定所有进程使用的 CPU 的 *标准偏差* 。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-152">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="2dcf6-153">较大的偏差将指示占用最多 CPU 的少量进程。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-153">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### <span data-ttu-id="2dcf6-154">示例12：使用通配符度量值</span><span class="sxs-lookup"><span data-stu-id="2dcf6-154">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="2dcf6-155">从 PowerShell 6 开始， `Measure-Object` 支持在属性名称中使用通配符对对象进行度量。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-155">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="2dcf6-156">下面的示例确定一组进程中任何类型的分页内存使用量的最大值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-156">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## <span data-ttu-id="2dcf6-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dcf6-157">PARAMETERS</span></span>

### <span data-ttu-id="2dcf6-158">-Average</span><span class="sxs-lookup"><span data-stu-id="2dcf6-158">-Average</span></span>

<span data-ttu-id="2dcf6-159">指示该 cmdlet 显示指定属性的平均值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-159">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-160">-Character</span><span class="sxs-lookup"><span data-stu-id="2dcf6-160">-Character</span></span>

<span data-ttu-id="2dcf6-161">指示该 cmdlet 对输入对象中的字符数进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-161">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf6-162">每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-162">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="2dcf6-163">请参阅示例7。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-163">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-164">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="2dcf6-164">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="2dcf6-165">指示 cmdlet 忽略字符计数中的空格。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-165">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="2dcf6-166">默认情况下，不忽略空格。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-166">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2dcf6-167">-InputObject</span></span>

<span data-ttu-id="2dcf6-168">指定要测量的对象。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-168">Specifies the objects to be measured.</span></span>
<span data-ttu-id="2dcf6-169">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-169">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="2dcf6-170">当你将 **inputobject** 参数与一起使用时 `Measure-Object` ， `Measure-Object` **inputobject** 值将被视为单个对象，而不是管道将命令结果传递给。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-170">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="2dcf6-171">`Measure-Object`如果要根据对象是否在定义的属性中具有特定值，则建议在管道中使用。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-171">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="2dcf6-172">-Line</span><span class="sxs-lookup"><span data-stu-id="2dcf6-172">-Line</span></span>

<span data-ttu-id="2dcf6-173">指示该 cmdlet 对输入对象中的行数进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-173">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf6-174">每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-174">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="2dcf6-175">请参阅示例7。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-175">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-176">-Maximum</span><span class="sxs-lookup"><span data-stu-id="2dcf6-176">-Maximum</span></span>

<span data-ttu-id="2dcf6-177">指示该 cmdlet 显示指定属性的最大值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-177">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-178">-Minimum</span><span class="sxs-lookup"><span data-stu-id="2dcf6-178">-Minimum</span></span>

<span data-ttu-id="2dcf6-179">指示该 cmdlet 显示指定属性的最小值。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-179">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-180">-Property</span><span class="sxs-lookup"><span data-stu-id="2dcf6-180">-Property</span></span>

<span data-ttu-id="2dcf6-181">指定要度量的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-181">Specifies one or more properties to measure.</span></span> <span data-ttu-id="2dcf6-182">如果未指定任何其他度量值，则 `Measure-Object` 会计算具有指定属性的对象。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-182">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="2dcf6-183">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-183">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="2dcf6-184">计算属性必须是脚本块。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-184">The calculated property must be a script block.</span></span> <span data-ttu-id="2dcf6-185">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-185">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2dcf6-186">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="2dcf6-186">-StandardDeviation</span></span>

<span data-ttu-id="2dcf6-187">指示该 cmdlet 显示指定属性的值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-187">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-188">-Sum</span><span class="sxs-lookup"><span data-stu-id="2dcf6-188">-Sum</span></span>

<span data-ttu-id="2dcf6-189">指示该 cmdlet 显示指定属性的值的总和。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-189">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-190">-AllStats</span><span class="sxs-lookup"><span data-stu-id="2dcf6-190">-AllStats</span></span>

<span data-ttu-id="2dcf6-191">指示该 cmdlet 显示指定属性的所有统计信息。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-191">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-192">-Word</span><span class="sxs-lookup"><span data-stu-id="2dcf6-192">-Word</span></span>

<span data-ttu-id="2dcf6-193">指示该 cmdlet 对输入对象中的单词进行计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-193">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf6-194">每 *个输入对象内以及输入* 对象 *中* 的 **单词**、**字符** 和 **行** 开关均计数。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-194">The **Word**, **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="2dcf6-195">请参阅示例7。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-195">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dcf6-196">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dcf6-196">CommonParameters</span></span>

<span data-ttu-id="2dcf6-197">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-197">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2dcf6-198">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-198">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2dcf6-199">输入</span><span class="sxs-lookup"><span data-stu-id="2dcf6-199">INPUTS</span></span>

### <span data-ttu-id="2dcf6-200">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="2dcf6-200">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2dcf6-201">可以通过管道将对象传递给 `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-201">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="2dcf6-202">输出</span><span class="sxs-lookup"><span data-stu-id="2dcf6-202">OUTPUTS</span></span>

### <span data-ttu-id="2dcf6-203">GenericMeasureInfo。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-203">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="2dcf6-204">TextMeasureInfo。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-204">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="2dcf6-205">如果使用 **Word** 参数，则 `Measure-Object` 返回 **TextMeasureInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-205">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="2dcf6-206">否则，它返回 **GenericMeasureInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="2dcf6-206">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="2dcf6-207">注释</span><span class="sxs-lookup"><span data-stu-id="2dcf6-207">NOTES</span></span>

## <span data-ttu-id="2dcf6-208">相关链接</span><span class="sxs-lookup"><span data-stu-id="2dcf6-208">RELATED LINKS</span></span>

[<span data-ttu-id="2dcf6-209">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="2dcf6-209">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="2dcf6-210">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-210">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="2dcf6-211">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-211">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="2dcf6-212">Group-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-212">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="2dcf6-213">New-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-213">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="2dcf6-214">Select-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-214">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="2dcf6-215">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-215">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="2dcf6-216">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-216">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="2dcf6-217">Where-Object</span><span class="sxs-lookup"><span data-stu-id="2dcf6-217">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
