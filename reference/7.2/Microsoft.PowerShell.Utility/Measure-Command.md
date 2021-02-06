---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0c2346dc7177e091c0921cd4775422938305e2be
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99596621"
---
# <span data-ttu-id="5d46b-102">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="5d46b-102">Measure-Command</span></span>

## <span data-ttu-id="5d46b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5d46b-103">SYNOPSIS</span></span>
<span data-ttu-id="5d46b-104">测量运行脚本块和 cmdlet 所需的时间。</span><span class="sxs-lookup"><span data-stu-id="5d46b-104">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="5d46b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d46b-105">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="5d46b-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5d46b-106">DESCRIPTION</span></span>

<span data-ttu-id="5d46b-107">该 `Measure-Command` cmdlet 在内部运行脚本块或 cmdlet，执行操作的时间，并返回执行时间。</span><span class="sxs-lookup"><span data-stu-id="5d46b-107">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="5d46b-108">运行脚本块的方式是 `Measure-Command` 在当前范围内运行，而不是子范围。</span><span class="sxs-lookup"><span data-stu-id="5d46b-108">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="5d46b-109">示例</span><span class="sxs-lookup"><span data-stu-id="5d46b-109">EXAMPLES</span></span>

### <span data-ttu-id="5d46b-110">示例1：度量命令</span><span class="sxs-lookup"><span data-stu-id="5d46b-110">Example 1: Measure a command</span></span>

<span data-ttu-id="5d46b-111">此示例测量运行 `Get-EventLog` 命令（用于获取 Windows PowerShell 事件日志中的事件）所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="5d46b-111">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="5d46b-112">示例2：比较 Measure-Command 的两个输出</span><span class="sxs-lookup"><span data-stu-id="5d46b-112">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="5d46b-113">第一个命令测量处理 `Get-ChildItem` 使用 **Path** 参数仅获取 `.txt` `C:\Windows` 目录及其子目录中的文件的递归命令所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="5d46b-113">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="5d46b-114">第二个命令测量处理 `Get-ChildItem` 使用特定于访问接口的 "参数的递归命令所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="5d46b-114">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="5d46b-115">这些命令显示了在 PowerShell 命令中使用特定于提供程序的筛选器的值。</span><span class="sxs-lookup"><span data-stu-id="5d46b-115">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="5d46b-116">示例3：将输入管道到 Measure-Command</span><span class="sxs-lookup"><span data-stu-id="5d46b-116">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="5d46b-117">通过管道传递到的对象 `Measure-Command` 可用于传递给 **Expression** 参数的脚本块。</span><span class="sxs-lookup"><span data-stu-id="5d46b-117">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="5d46b-118">对于管道上的每个对象，将执行一次脚本块。</span><span class="sxs-lookup"><span data-stu-id="5d46b-118">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="5d46b-119">示例4：显示已测量命令的输出</span><span class="sxs-lookup"><span data-stu-id="5d46b-119">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="5d46b-120">若要在中显示表达式的输出 `Measure-Command` ，可以使用管道 `Out-Default` 。</span><span class="sxs-lookup"><span data-stu-id="5d46b-120">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="5d46b-121">示例5：测量子作用域中的执行</span><span class="sxs-lookup"><span data-stu-id="5d46b-121">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="5d46b-122">`Measure-Command` 运行当前范围内的脚本块，因此脚本块可以修改当前范围中的值。</span><span class="sxs-lookup"><span data-stu-id="5d46b-122">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="5d46b-123">若要避免对当前范围的更改，必须将脚本块 (括在大括号中， `{}`) 并使用调用运算符 (`&`) 来执行子范围中的块。</span><span class="sxs-lookup"><span data-stu-id="5d46b-123">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="5d46b-124">有关调用运算符的详细信息，请参阅 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)。</span><span class="sxs-lookup"><span data-stu-id="5d46b-124">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="5d46b-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5d46b-125">PARAMETERS</span></span>

### <span data-ttu-id="5d46b-126">-Expression</span><span class="sxs-lookup"><span data-stu-id="5d46b-126">-Expression</span></span>

<span data-ttu-id="5d46b-127">指定要测量时间的表达式。</span><span class="sxs-lookup"><span data-stu-id="5d46b-127">Specifies the expression that is being timed.</span></span> <span data-ttu-id="5d46b-128">将表达式括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="5d46b-128">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d46b-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5d46b-129">-InputObject</span></span>

<span data-ttu-id="5d46b-130">绑定到 **InputObject** 参数的对象是传递给 **Expression** 参数的脚本块的可选输入。</span><span class="sxs-lookup"><span data-stu-id="5d46b-130">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="5d46b-131">在脚本块中， `$_` 可用于引用管道中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="5d46b-131">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

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

### <span data-ttu-id="5d46b-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d46b-132">CommonParameters</span></span>

<span data-ttu-id="5d46b-133">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5d46b-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d46b-134">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5d46b-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d46b-135">输入</span><span class="sxs-lookup"><span data-stu-id="5d46b-135">INPUTS</span></span>

### <span data-ttu-id="5d46b-136">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="5d46b-136">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5d46b-137">可以通过管道将对象传递给 `Measure-Command` 。</span><span class="sxs-lookup"><span data-stu-id="5d46b-137">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="5d46b-138">输出</span><span class="sxs-lookup"><span data-stu-id="5d46b-138">OUTPUTS</span></span>

### <span data-ttu-id="5d46b-139">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="5d46b-139">System.TimeSpan</span></span>

<span data-ttu-id="5d46b-140">`Measure-Command` 返回一个表示结果的时间跨度对象。</span><span class="sxs-lookup"><span data-stu-id="5d46b-140">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="5d46b-141">注释</span><span class="sxs-lookup"><span data-stu-id="5d46b-141">NOTES</span></span>

## <span data-ttu-id="5d46b-142">相关链接</span><span class="sxs-lookup"><span data-stu-id="5d46b-142">RELATED LINKS</span></span>

[<span data-ttu-id="5d46b-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="5d46b-143">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="5d46b-144">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="5d46b-144">Trace-Command</span></span>](Trace-Command.md)

