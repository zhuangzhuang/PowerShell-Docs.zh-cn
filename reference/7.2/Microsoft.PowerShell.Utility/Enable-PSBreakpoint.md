---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 28cda7a2fa4435092b647e43a250222a852114b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597457"
---
# <span data-ttu-id="b7ff5-102">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-102">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="b7ff5-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b7ff5-103">SYNOPSIS</span></span>
<span data-ttu-id="b7ff5-104">启用当前控制台中的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-104">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="b7ff5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7ff5-105">SYNTAX</span></span>

### <span data-ttu-id="b7ff5-106">ID（默认值）</span><span class="sxs-lookup"><span data-stu-id="b7ff5-106">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b7ff5-107">断点</span><span class="sxs-lookup"><span data-stu-id="b7ff5-107">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b7ff5-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7ff5-108">DESCRIPTION</span></span>

<span data-ttu-id="b7ff5-109">`Enable-PSBreakpoint`Cmdlet 可重新启用已禁用的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-109">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="b7ff5-110">您可以通过提供断点对象或 Id，使用它来启用所有断点或特定断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-110">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="b7ff5-111">断点是脚本中的一个点，其中的执行暂时停止，以便您可以检查脚本的状态。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-111">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="b7ff5-112">新创建的断点将自动启用，但可以使用禁用 `Disable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-112">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="b7ff5-113">在技术上，此 cmdlet 将断点对象的 **Enabled** 属性值更改为 **True**。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-113">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="b7ff5-114">`Enable-PSBreakpoint` 是旨在调试 PowerShell 脚本的多个 cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-114">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="b7ff5-115">有关 PowerShell 调试器的详细信息，请参阅 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-115">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="b7ff5-116">示例</span><span class="sxs-lookup"><span data-stu-id="b7ff5-116">EXAMPLES</span></span>

### <span data-ttu-id="b7ff5-117">示例1：启用所有断点</span><span class="sxs-lookup"><span data-stu-id="b7ff5-117">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="b7ff5-118">此示例将启用当前会话中的所有断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-118">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="b7ff5-119">使用别名，此示例可以缩写为 `gbp | ebp` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-119">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="b7ff5-120">示例2：按 ID 启用断点</span><span class="sxs-lookup"><span data-stu-id="b7ff5-120">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="b7ff5-121">此示例使用断点 Id 启用多个断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-121">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="b7ff5-122">示例3：启用已禁用的断点</span><span class="sxs-lookup"><span data-stu-id="b7ff5-122">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="b7ff5-123">此示例将重新启用已禁用的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-123">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="b7ff5-124">`Set-PSBreakpoint` 在脚本中的 **名称** 变量上创建一个断点，该断点将 `Sample.ps1` 断点对象保存在 `$B` 变量中。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-124">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="b7ff5-125">**PassThru** 参数显示断点的 **Enabled** 属性的值为 **False**。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-125">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="b7ff5-126">`Enable-PSBreakpoint` 重新启用断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-126">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="b7ff5-127">再次强调，使用 **PassThru** 参数会看到 **Enabled** 属性的值为 **True**。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-127">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="b7ff5-128">示例4：使用变量启用断点</span><span class="sxs-lookup"><span data-stu-id="b7ff5-128">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="b7ff5-129">此示例使用断点对象启用一组断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-129">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="b7ff5-130">`Get-PSBreakpoint` 获取断点，并将它们保存在 `$B` 变量中。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-130">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="b7ff5-131">使用 **断点** 参数 `Enable-PSBreakpoint` 启用断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-131">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="b7ff5-132">此示例等效于运行 `Enable-PSBreakpoint -Id 3, 5` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-132">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="b7ff5-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7ff5-133">PARAMETERS</span></span>

### <span data-ttu-id="b7ff5-134">-Breakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-134">-Breakpoint</span></span>

<span data-ttu-id="b7ff5-135">指定要启用的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-135">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="b7ff5-136">提供一个包含断点的变量或一个可获取断点对象的命令，例如 `Get-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-136">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="b7ff5-137">还可以通过管道将断点对象传递给 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-137">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b7ff5-138">-Id</span><span class="sxs-lookup"><span data-stu-id="b7ff5-138">-Id</span></span>

<span data-ttu-id="b7ff5-139">指定要启用的断点的 **Id** 号。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-139">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="b7ff5-140">默认值为所有断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-140">The default value is all breakpoints.</span></span>
<span data-ttu-id="b7ff5-141">按数字或变量提供 **Id** 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-141">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="b7ff5-142">不能通过管道将 **Id** 号传递给 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-142">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="b7ff5-143">若要查找断点的 **Id** ，请使用 `Get-PSBreakpoint` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-143">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7ff5-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b7ff5-144">-PassThru</span></span>

<span data-ttu-id="b7ff5-145">返回一个对象，该对象表示正在启用的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-145">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="b7ff5-146">默认情况下，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-146">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="b7ff5-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b7ff5-147">-Confirm</span></span>

<span data-ttu-id="b7ff5-148">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b7ff5-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b7ff5-149">-WhatIf</span></span>

<span data-ttu-id="b7ff5-150">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b7ff5-151">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-151">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b7ff5-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7ff5-152">CommonParameters</span></span>

<span data-ttu-id="b7ff5-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7ff5-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7ff5-155">输入</span><span class="sxs-lookup"><span data-stu-id="b7ff5-155">INPUTS</span></span>

### <span data-ttu-id="b7ff5-156">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-156">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="b7ff5-157">可以通过管道将断点对象传递给 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-157">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="b7ff5-158">输出</span><span class="sxs-lookup"><span data-stu-id="b7ff5-158">OUTPUTS</span></span>

### <span data-ttu-id="b7ff5-159">无或 System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-159">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="b7ff5-160">当使用 **PassThru** 参数时，将 `Enable-PSBreakpoint` 返回一个断点对象，该对象表示已启用的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-160">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="b7ff5-161">否则，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-161">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="b7ff5-162">注释</span><span class="sxs-lookup"><span data-stu-id="b7ff5-162">NOTES</span></span>

- <span data-ttu-id="b7ff5-163">`Enable-PSBreakpoint`如果尝试启用已启用的断点，则该 cmdlet 不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-163">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="b7ff5-164">因此，即使仅有少数断点处于禁用状态，你也可以启用所有断点而不发生错误。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-164">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="b7ff5-165">使用 cmdlet 创建断点时，会启用断点 `Set-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-165">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="b7ff5-166">不需要启用新创建的断点。</span><span class="sxs-lookup"><span data-stu-id="b7ff5-166">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="b7ff5-167">相关链接</span><span class="sxs-lookup"><span data-stu-id="b7ff5-167">RELATED LINKS</span></span>

[<span data-ttu-id="b7ff5-168">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-168">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="b7ff5-169">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-169">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="b7ff5-170">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="b7ff5-170">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="b7ff5-171">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-171">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="b7ff5-172">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b7ff5-172">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

