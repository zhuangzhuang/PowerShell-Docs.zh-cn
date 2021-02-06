---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597070"
---
# <span data-ttu-id="8023f-102">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8023f-102">Set-PSBreakpoint</span></span>

## <span data-ttu-id="8023f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="8023f-103">SYNOPSIS</span></span>
<span data-ttu-id="8023f-104">在行、命令或变量上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-104">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="8023f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8023f-105">SYNTAX</span></span>

### <span data-ttu-id="8023f-106">行 (默认值) </span><span class="sxs-lookup"><span data-stu-id="8023f-106">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="8023f-107">命令</span><span class="sxs-lookup"><span data-stu-id="8023f-107">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8023f-108">变量</span><span class="sxs-lookup"><span data-stu-id="8023f-108">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="8023f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8023f-109">DESCRIPTION</span></span>

<span data-ttu-id="8023f-110">`Set-PSBreakpoint`Cmdlet 在当前会话中的脚本或任何命令运行中设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-110">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="8023f-111">在 `Set-PSBreakpoint` 执行脚本或运行命令之前，或在调试期间，如果在另一个断点处停止，则可以使用来设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-111">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="8023f-112">`Set-PSBreakpoint` 无法在远程计算机上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-112">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="8023f-113">若要在远程计算机上调试脚本，请将该脚本复制到本地计算机，然后从本地进行调试。</span><span class="sxs-lookup"><span data-stu-id="8023f-113">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="8023f-114">每个 `Set-PSBreakpoint` 命令都创建以下三种类型的断点之一：</span><span class="sxs-lookup"><span data-stu-id="8023f-114">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="8023f-115">行断点-在特定的行坐标和列坐标处设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-115">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="8023f-116">命令断点-在命令和函数上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-116">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="8023f-117">变量断点-设置变量的断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-117">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="8023f-118">可以在单个命令中设置多个行、命令或变量的断点 `Set-PSBreakpoint` ，但每个 `Set-PSBreakpoint` 命令仅设置一种类型的断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-118">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="8023f-119">在断点处，PowerShell 暂时停止执行，并向调试器提供控制。</span><span class="sxs-lookup"><span data-stu-id="8023f-119">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="8023f-120">命令提示符将更改为 `DBG\>` ，并且一组调试器命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="8023f-120">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="8023f-121">但是，你可以使用 **Action** 参数指定备用响应，例如断点的条件或执行其他任务（如日志记录或诊断）的说明。</span><span class="sxs-lookup"><span data-stu-id="8023f-121">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="8023f-122">`Set-PSBreakpoint`Cmdlet 是专门用于调试 PowerShell 脚本的多个 cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="8023f-122">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="8023f-123">有关 PowerShell 调试器的详细信息，请参阅 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。</span><span class="sxs-lookup"><span data-stu-id="8023f-123">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="8023f-124">示例</span><span class="sxs-lookup"><span data-stu-id="8023f-124">EXAMPLES</span></span>

### <span data-ttu-id="8023f-125">示例1：在行上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-125">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="8023f-126">此示例在 Sample.ps1 脚本中的第5行设置一个断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-126">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="8023f-127">脚本运行时，执行将在第5行执行之前立即停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-127">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="8023f-128">当你按行号设置新断点时，该 `Set-PSBreakpoint` cmdlet 将生成一个 () 的行断点对象，其中包括断点 ID 和命中次数。</span><span class="sxs-lookup"><span data-stu-id="8023f-128">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object (**System.Management.Automation.LineBreakpoint**) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="8023f-129">示例2：在函数上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-129">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="8023f-130">此示例在 Sample.ps1 cmdlet 中的函数上创建命令断点 `Increment` 。</span><span class="sxs-lookup"><span data-stu-id="8023f-130">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="8023f-131">该脚本在每次调用指定函数前立即停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-131">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="8023f-132">结果是命令断点对象。</span><span class="sxs-lookup"><span data-stu-id="8023f-132">The result is a command breakpoint object.</span></span> <span data-ttu-id="8023f-133">在运行脚本之前， **点击次数** 属性的值为0。</span><span class="sxs-lookup"><span data-stu-id="8023f-133">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="8023f-134">示例3：在变量上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-134">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="8023f-135">此示例在 Sample.ps1 脚本中的 **服务器** 变量上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-135">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="8023f-136">它使用值为 **ReadWrite** 的 **Mode** 参数在读取变量的值并刚好在值更改之前停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-136">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="8023f-137">示例4：在以指定文本开头的每个命令上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-137">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="8023f-138">此示例在 Sample.ps1 脚本中每个以 "write" 开头的命令上设置断点，例如 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="8023f-138">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="8023f-139">示例5：根据变量的值设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-139">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="8023f-140">`DiskTest`仅当变量的值大于2时，此示例才会在 Test.ps1 脚本中的函数处停止执行 `$Disk` 。</span><span class="sxs-lookup"><span data-stu-id="8023f-140">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="8023f-141">**操作** 的值是一个脚本块，可测试 `$Disk` 函数中变量的值。</span><span class="sxs-lookup"><span data-stu-id="8023f-141">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="8023f-142">如果满足条件，则该操作将使用 `break` 关键字停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-142">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="8023f-143">备用 (和默认) 会 **继续**。</span><span class="sxs-lookup"><span data-stu-id="8023f-143">The alternative (and the default) is **Continue**.</span></span>

### <span data-ttu-id="8023f-144">示例6：在函数上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-144">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="8023f-145">此示例在函数上设置断点 `CheckLog` 。</span><span class="sxs-lookup"><span data-stu-id="8023f-145">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="8023f-146">由于该命令未指定脚本，因此将在当前会话中运行的任何内容上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-146">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="8023f-147">当调用该函数（而不是声明它）时，调试器将中断。</span><span class="sxs-lookup"><span data-stu-id="8023f-147">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="8023f-148">示例7：在多行上设置断点</span><span class="sxs-lookup"><span data-stu-id="8023f-148">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="8023f-149">此示例在 Sample.ps1 脚本中设置三个行断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-149">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="8023f-150">它将在脚本中每个指定行上的第 2 列处设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-150">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="8023f-151">**操作** 参数中指定的操作适用于所有断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-151">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="8023f-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8023f-152">PARAMETERS</span></span>

### <span data-ttu-id="8023f-153">-Action</span><span class="sxs-lookup"><span data-stu-id="8023f-153">-Action</span></span>

<span data-ttu-id="8023f-154">指定在每个断点处运行的命令，而不是中断。</span><span class="sxs-lookup"><span data-stu-id="8023f-154">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="8023f-155">输入包含这些命令的脚本块。</span><span class="sxs-lookup"><span data-stu-id="8023f-155">Enter a script block that contains the commands.</span></span> <span data-ttu-id="8023f-156">可以使用此参数设置条件断点或执行其他任务，例如测试或记录。</span><span class="sxs-lookup"><span data-stu-id="8023f-156">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="8023f-157">如果省略此参数，或未指定任何操作，则执行在断点处停止，并且调试器将启动。</span><span class="sxs-lookup"><span data-stu-id="8023f-157">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="8023f-158">使用 **action** 参数时，操作脚本块将在每个断点处运行。</span><span class="sxs-lookup"><span data-stu-id="8023f-158">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="8023f-159">除非脚本块包含 Break 关键字，否则执行不会停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-159">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="8023f-160">如果在脚本块中使用 Continue 关键字，则执行将继续，直到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-160">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="8023f-161">有关详细信息，请参阅 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md)、 [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)和 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)。</span><span class="sxs-lookup"><span data-stu-id="8023f-161">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-162">-Column</span><span class="sxs-lookup"><span data-stu-id="8023f-162">-Column</span></span>

<span data-ttu-id="8023f-163">指定执行停止的脚本文件中的列的列号。</span><span class="sxs-lookup"><span data-stu-id="8023f-163">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="8023f-164">仅输入一个列号。</span><span class="sxs-lookup"><span data-stu-id="8023f-164">Enter only one column number.</span></span> <span data-ttu-id="8023f-165">默认值为列 1。</span><span class="sxs-lookup"><span data-stu-id="8023f-165">The default is column 1.</span></span>

<span data-ttu-id="8023f-166">列值与 **Line** 参数的值一起用于指定断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-166">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="8023f-167">如果 **Line** 参数指定了多个行，则 **Column** 参数将在每个指定行的指定列处设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-167">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="8023f-168">PowerShell 在包含指定行和列位置的字符的语句或表达式前停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-168">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="8023f-169">列从左上方边沿以列号 1（而不是 0）开始计数。</span><span class="sxs-lookup"><span data-stu-id="8023f-169">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="8023f-170">如果指定了脚本中不存在的列，则不会声明错误，但是永远不会执行断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-170">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-171">-Command</span><span class="sxs-lookup"><span data-stu-id="8023f-171">-Command</span></span>

<span data-ttu-id="8023f-172">设置命令断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-172">Sets a command breakpoint.</span></span> <span data-ttu-id="8023f-173">输入 cmdlet 名称，如 `Get-Process` 或函数名称。</span><span class="sxs-lookup"><span data-stu-id="8023f-173">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="8023f-174">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="8023f-174">Wildcards are permitted.</span></span>

<span data-ttu-id="8023f-175">执行正好在执行每个命令的每个实例之前停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-175">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="8023f-176">如果该命令是一个函数，则执行在每次调用该函数时以及在每个开始、过程和结束部分上停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-176">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8023f-177">-Line</span><span class="sxs-lookup"><span data-stu-id="8023f-177">-Line</span></span>

<span data-ttu-id="8023f-178">在脚本中设置行断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-178">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="8023f-179">输入一个或多个行号，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="8023f-179">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="8023f-180">PowerShell 在执行从每个指定的行上开始的语句前立即停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-180">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="8023f-181">行从脚本文件的左上方边沿以行号 1（而不是 0）开始计数。</span><span class="sxs-lookup"><span data-stu-id="8023f-181">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="8023f-182">如果指定空行，则执行将在下一个非空行之前停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-182">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="8023f-183">如果行不在范围内，则永远不会命中断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-183">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-184">-Mode</span><span class="sxs-lookup"><span data-stu-id="8023f-184">-Mode</span></span>

<span data-ttu-id="8023f-185">指定触发变量断点的访问模式。</span><span class="sxs-lookup"><span data-stu-id="8023f-185">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="8023f-186">默认值为 **Write**。</span><span class="sxs-lookup"><span data-stu-id="8023f-186">The default is **Write**.</span></span>

<span data-ttu-id="8023f-187">仅当命令中使用了 **Variable** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="8023f-187">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="8023f-188">此模式适用于命令中设置的所有断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-188">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="8023f-189">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="8023f-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8023f-190">**写入** -在将新值写入变量前立即停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-190">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="8023f-191">**读-在** 读取变量时执行，即，当访问变量值时，将被分配、显示或使用。</span><span class="sxs-lookup"><span data-stu-id="8023f-191">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="8023f-192">在读取模式下，当变量的值发生更改时，执行不会停止。</span><span class="sxs-lookup"><span data-stu-id="8023f-192">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="8023f-193">**ReadWrite** -读取或写入变量时停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-193">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-194">-Script</span><span class="sxs-lookup"><span data-stu-id="8023f-194">-Script</span></span>

<span data-ttu-id="8023f-195">指定此 cmdlet 在其中设置断点的脚本文件的数组。</span><span class="sxs-lookup"><span data-stu-id="8023f-195">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="8023f-196">输入一个或多个脚本文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="8023f-196">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="8023f-197">如果文件在当前目录中，则可以省略该路径。</span><span class="sxs-lookup"><span data-stu-id="8023f-197">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="8023f-198">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="8023f-198">Wildcards are permitted.</span></span>

<span data-ttu-id="8023f-199">默认情况下，将在当前会话中运行的任何命令上设置变量断点和命令断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-199">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="8023f-200">仅当设置行断点时，此参数才是必需的。</span><span class="sxs-lookup"><span data-stu-id="8023f-200">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-201">-Variable</span><span class="sxs-lookup"><span data-stu-id="8023f-201">-Variable</span></span>

<span data-ttu-id="8023f-202">指定此 cmdlet 在其上设置断点的变量数组。</span><span class="sxs-lookup"><span data-stu-id="8023f-202">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="8023f-203">输入一个逗号分隔的变量列表，其中不含美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="8023f-203">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="8023f-204">使用 **Mode** 参数确定触发断点的访问模式。</span><span class="sxs-lookup"><span data-stu-id="8023f-204">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="8023f-205">默认模式 Write 会在新值写入变量前停止执行。</span><span class="sxs-lookup"><span data-stu-id="8023f-205">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8023f-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8023f-206">CommonParameters</span></span>

<span data-ttu-id="8023f-207">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8023f-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8023f-208">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8023f-208">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8023f-209">输入</span><span class="sxs-lookup"><span data-stu-id="8023f-209">INPUTS</span></span>

### <span data-ttu-id="8023f-210">无</span><span class="sxs-lookup"><span data-stu-id="8023f-210">None</span></span>
<span data-ttu-id="8023f-211">不能通过管道将输入传递给 `Set-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="8023f-211">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="8023f-212">输出</span><span class="sxs-lookup"><span data-stu-id="8023f-212">OUTPUTS</span></span>

### <span data-ttu-id="8023f-213"> (System.management.automation.linebreakpoint、VariableBreakpoint、CommandBreakpoint) 断点对象的断点对象。，则为。</span><span class="sxs-lookup"><span data-stu-id="8023f-213">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="8023f-214">`Set-PSBreakpoint` 返回表示它所设置的每个断点的对象。</span><span class="sxs-lookup"><span data-stu-id="8023f-214">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="8023f-215">注释</span><span class="sxs-lookup"><span data-stu-id="8023f-215">NOTES</span></span>

- <span data-ttu-id="8023f-216">`Set-PSBreakpoint` 无法在远程计算机上设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-216">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="8023f-217">若要在远程计算机上调试脚本，请将该脚本复制到本地计算机，然后从本地进行调试。</span><span class="sxs-lookup"><span data-stu-id="8023f-217">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="8023f-218">在多行、命令或变量上设置断点时，将 `Set-PSBreakpoint` 为每个项生成一个断点对象。</span><span class="sxs-lookup"><span data-stu-id="8023f-218">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="8023f-219">当在命令提示符下在函数或变量上设置断点时，你可以在创建函数或变量之前或之后设置断点。</span><span class="sxs-lookup"><span data-stu-id="8023f-219">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="8023f-220">相关链接</span><span class="sxs-lookup"><span data-stu-id="8023f-220">RELATED LINKS</span></span>

[<span data-ttu-id="8023f-221">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8023f-221">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="8023f-222">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8023f-222">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="8023f-223">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8023f-223">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="8023f-224">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="8023f-224">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="8023f-225">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8023f-225">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

