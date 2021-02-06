---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597853"
---
# <span data-ttu-id="63a6e-102">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-102">Get-PSBreakpoint</span></span>

## <span data-ttu-id="63a6e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="63a6e-103">SYNOPSIS</span></span>
<span data-ttu-id="63a6e-104">获取在当前会话中设置的断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-104">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="63a6e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63a6e-105">SYNTAX</span></span>

### <span data-ttu-id="63a6e-106">脚本 (默认值) </span><span class="sxs-lookup"><span data-stu-id="63a6e-106">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="63a6e-107">变量</span><span class="sxs-lookup"><span data-stu-id="63a6e-107">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="63a6e-108">命令</span><span class="sxs-lookup"><span data-stu-id="63a6e-108">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="63a6e-109">类型</span><span class="sxs-lookup"><span data-stu-id="63a6e-109">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="63a6e-110">ID</span><span class="sxs-lookup"><span data-stu-id="63a6e-110">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="63a6e-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="63a6e-111">DESCRIPTION</span></span>

<span data-ttu-id="63a6e-112">**Set-psbreakpoint** cmdlet 获取在当前会话中设置的断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-112">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="63a6e-113">可以使用该 cmdlet 参数获取特定断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-113">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="63a6e-114">断点是命令或脚本中的一个点，在该点处将暂时停止执行，以便你可以检查指令。</span><span class="sxs-lookup"><span data-stu-id="63a6e-114">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="63a6e-115">**Set-psbreakpoint** 是为调试 PowerShell 脚本和命令而设计的几个 cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="63a6e-115">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="63a6e-116">有关 PowerShell 调试器的详细信息，请参阅 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="63a6e-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="63a6e-117">示例</span><span class="sxs-lookup"><span data-stu-id="63a6e-117">EXAMPLES</span></span>

### <span data-ttu-id="63a6e-118">示例1：获取所有脚本和函数的所有断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-118">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="63a6e-119">此命令获取在当前会话中所有脚本和函数上设置的所有断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-119">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="63a6e-120">示例2：按 ID 获取断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-120">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="63a6e-121">此命令获取断点 ID 为 2 的断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-121">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="63a6e-122">示例3：通过管道将 ID 发送到 Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-122">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="63a6e-123">这些命令演示如何通过将断点 ID 通过管道传递给 **set-psbreakpoint** 来获取断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-123">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="63a6e-124">第一个命令使用 Set-PSBreakpoint cmdlet 在 Sample.ps1 脚本中的 Increment 函数上创建断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-124">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="63a6e-125">它将断点对象保存在 $B 变量中。</span><span class="sxs-lookup"><span data-stu-id="63a6e-125">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="63a6e-126">第二个命令使用点运算符 ( ) 获取 $B 变量中断点对象的 Id 属性。</span><span class="sxs-lookup"><span data-stu-id="63a6e-126">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="63a6e-127">它使用管道运算符 (|) 将 ID 发送到 **set-psbreakpoint** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63a6e-127">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="63a6e-128">因此， **set-psbreakpoint** 将获取具有指定 ID 的断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-128">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="63a6e-129">示例4：获取指定脚本文件中的断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-129">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="63a6e-130">此命令获取 Sample.ps1 和 SupportScript.ps1 文件中的所有断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-130">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="63a6e-131">此命令不会获取可能在会话中的其他脚本或函数上设置的其他断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-131">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="63a6e-132">示例5：在指定的 cmdlet 中获取断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-132">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="63a6e-133">此命令获取在 Sample.ps1 文件中的 Read-Host 或 Write-Host 命令上设置的所有 Command 断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-133">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="63a6e-134">示例6：在指定的文件中获取命令断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-134">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="63a6e-135">此命令获取 Sample.ps1 文件中的所有 Command 断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-135">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="63a6e-136">示例7：按变量获取断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-136">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="63a6e-137">此命令获取在当前会话中的 $Index 和 $Swap 变量上设置的断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-137">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="63a6e-138">示例8：获取文件中的所有行断点和变量断点</span><span class="sxs-lookup"><span data-stu-id="63a6e-138">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="63a6e-139">此命令获取 Sample.ps1 脚本中的所有行断点和变量断点。</span><span class="sxs-lookup"><span data-stu-id="63a6e-139">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="63a6e-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63a6e-140">PARAMETERS</span></span>

### <span data-ttu-id="63a6e-141">-Command</span><span class="sxs-lookup"><span data-stu-id="63a6e-141">-Command</span></span>

<span data-ttu-id="63a6e-142">指定在指定命令名称上设置的命令断点的数组。</span><span class="sxs-lookup"><span data-stu-id="63a6e-142">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="63a6e-143">输入命令名称，例如 cmdlet 或函数的名称。</span><span class="sxs-lookup"><span data-stu-id="63a6e-143">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63a6e-144">-Id</span><span class="sxs-lookup"><span data-stu-id="63a6e-144">-Id</span></span>

<span data-ttu-id="63a6e-145">指定此 cmdlet 获取的断点 Id。</span><span class="sxs-lookup"><span data-stu-id="63a6e-145">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="63a6e-146">将 ID 输入以逗号分隔的列表中。</span><span class="sxs-lookup"><span data-stu-id="63a6e-146">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="63a6e-147">还可以通过管道将断点 Id 传递给 **set-psbreakpoint**。</span><span class="sxs-lookup"><span data-stu-id="63a6e-147">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63a6e-148">-Script</span><span class="sxs-lookup"><span data-stu-id="63a6e-148">-Script</span></span>

<span data-ttu-id="63a6e-149">指定包含断点的脚本数组。</span><span class="sxs-lookup"><span data-stu-id="63a6e-149">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="63a6e-150">输入一个或多个脚本文件的路径 (可选) 和名称。</span><span class="sxs-lookup"><span data-stu-id="63a6e-150">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="63a6e-151">如果省略路径，则默认位置为当前目录。</span><span class="sxs-lookup"><span data-stu-id="63a6e-151">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63a6e-152">-Type</span><span class="sxs-lookup"><span data-stu-id="63a6e-152">-Type</span></span>

<span data-ttu-id="63a6e-153">指定此 cmdlet 获取的断点类型的数组。</span><span class="sxs-lookup"><span data-stu-id="63a6e-153">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="63a6e-154">输入一个或多个类型。</span><span class="sxs-lookup"><span data-stu-id="63a6e-154">Enter one or more types.</span></span>
<span data-ttu-id="63a6e-155">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="63a6e-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="63a6e-156">折线图</span><span class="sxs-lookup"><span data-stu-id="63a6e-156">Line</span></span>
- <span data-ttu-id="63a6e-157">命令</span><span class="sxs-lookup"><span data-stu-id="63a6e-157">Command</span></span>
- <span data-ttu-id="63a6e-158">变量</span><span class="sxs-lookup"><span data-stu-id="63a6e-158">Variable</span></span>

<span data-ttu-id="63a6e-159">还可以通过管道将断点类型传递给 **set-psbreakpoint**。</span><span class="sxs-lookup"><span data-stu-id="63a6e-159">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63a6e-160">-Variable</span><span class="sxs-lookup"><span data-stu-id="63a6e-160">-Variable</span></span>

<span data-ttu-id="63a6e-161">指定在指定变量名称上设置的变量断点数组。</span><span class="sxs-lookup"><span data-stu-id="63a6e-161">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="63a6e-162">输入不带美元符号的变量名称。</span><span class="sxs-lookup"><span data-stu-id="63a6e-162">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63a6e-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63a6e-163">CommonParameters</span></span>

<span data-ttu-id="63a6e-164">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="63a6e-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63a6e-165">有关详细信息，请参阅 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216) 。</span><span class="sxs-lookup"><span data-stu-id="63a6e-165">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63a6e-166">输入</span><span class="sxs-lookup"><span data-stu-id="63a6e-166">INPUTS</span></span>

### <span data-ttu-id="63a6e-167">System.object、BreakpointType 的命令</span><span class="sxs-lookup"><span data-stu-id="63a6e-167">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="63a6e-168">可以通过管道将断点 Id 和断点类型传递给 **set-psbreakpoint**。</span><span class="sxs-lookup"><span data-stu-id="63a6e-168">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="63a6e-169">输出</span><span class="sxs-lookup"><span data-stu-id="63a6e-169">OUTPUTS</span></span>

### <span data-ttu-id="63a6e-170">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-170">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="63a6e-171">**Set-psbreakpoint** 返回表示会话中的断点的对象。</span><span class="sxs-lookup"><span data-stu-id="63a6e-171">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="63a6e-172">注释</span><span class="sxs-lookup"><span data-stu-id="63a6e-172">NOTES</span></span>

* <span data-ttu-id="63a6e-173">可以使用 **set-psbreakpoint** 或其别名 "gbp"。</span><span class="sxs-lookup"><span data-stu-id="63a6e-173">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="63a6e-174">相关链接</span><span class="sxs-lookup"><span data-stu-id="63a6e-174">RELATED LINKS</span></span>

[<span data-ttu-id="63a6e-175">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-175">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="63a6e-176">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-176">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="63a6e-177">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="63a6e-177">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="63a6e-178">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-178">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="63a6e-179">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="63a6e-179">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

