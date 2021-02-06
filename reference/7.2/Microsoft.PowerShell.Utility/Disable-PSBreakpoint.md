---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2bd1a48d2075950cdb337063a100bf31534ac6fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599066"
---
# <span data-ttu-id="cea0b-102">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-102">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="cea0b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cea0b-103">SYNOPSIS</span></span>
<span data-ttu-id="cea0b-104">禁用当前控制台中的断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-104">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="cea0b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cea0b-105">SYNTAX</span></span>

### <span data-ttu-id="cea0b-106">Breakpoint（默认值）</span><span class="sxs-lookup"><span data-stu-id="cea0b-106">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cea0b-107">ID</span><span class="sxs-lookup"><span data-stu-id="cea0b-107">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cea0b-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cea0b-108">DESCRIPTION</span></span>

<span data-ttu-id="cea0b-109">**Set-psbreakpoint** cmdlet 禁用断点，以确保在脚本运行时不会命中断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-109">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="cea0b-110">可使用它来禁用所有断点，或者可通过提交断点对象或断点 ID 来指定断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-110">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="cea0b-111">在技术上，该 cmdlet 将断点对象的 Enabled 属性值更改为 False。</span><span class="sxs-lookup"><span data-stu-id="cea0b-111">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="cea0b-112">若要重新启用断点，请使用 Enable-PSBreakpoint cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cea0b-112">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="cea0b-113">当使用 Set-PSBreakpoint cmdlet 来创建断点时，将默认启用断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-113">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="cea0b-114">断点是脚本中的一个点，将在其中暂时停止执行脚本，从而使你可以检查脚本中的指令。</span><span class="sxs-lookup"><span data-stu-id="cea0b-114">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="cea0b-115">**Set-psbreakpoint** 是设计用于调试 PowerShell 脚本的多个 cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="cea0b-115">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="cea0b-116">有关 PowerShell 调试器的详细信息，请参阅 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="cea0b-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="cea0b-117">示例</span><span class="sxs-lookup"><span data-stu-id="cea0b-117">EXAMPLES</span></span>

### <span data-ttu-id="cea0b-118">示例1：设置断点并禁用它</span><span class="sxs-lookup"><span data-stu-id="cea0b-118">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="cea0b-119">这些命令禁用新创建的断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-119">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="cea0b-120">第一个命令使用 Set-PSBreakpoint cmdlet 在 Sample.ps1 脚本中的 *Name* 变量上创建断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="cea0b-121">然后，它将断点对象保存在 $B 变量中。</span><span class="sxs-lookup"><span data-stu-id="cea0b-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="cea0b-122">第二个命令使用 **set-psbreakpoint** cmdlet 来禁用新断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-122">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="cea0b-123">它使用管道运算符 (|) 将 $B 中的断点对象发送到 **set-psbreakpoint** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cea0b-123">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="cea0b-124">此命令的结果是，$B 中的断点对象的 Enabled 属性的值为 False。</span><span class="sxs-lookup"><span data-stu-id="cea0b-124">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="cea0b-125">示例2：禁用断点</span><span class="sxs-lookup"><span data-stu-id="cea0b-125">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="cea0b-126">此命令禁用断点 ID 为 0 的断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-126">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="cea0b-127">示例3：创建已禁用的断点</span><span class="sxs-lookup"><span data-stu-id="cea0b-127">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="cea0b-128">此命令创建新断点，在你启用该断点之前，该断点将一直禁用。</span><span class="sxs-lookup"><span data-stu-id="cea0b-128">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="cea0b-129">它使用 **set-psbreakpoint** cmdlet 禁用断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-129">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="cea0b-130">*断点* 参数的值是一个 Set-PSBreakpoint 命令，该命令设置新断点，生成一个断点对象，并将该对象保存在 $B 变量中。</span><span class="sxs-lookup"><span data-stu-id="cea0b-130">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="cea0b-131">Cmdlet 参数将对象用作值，可接受包含对象的变量或者可获取或生成对象的命令。</span><span class="sxs-lookup"><span data-stu-id="cea0b-131">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="cea0b-132">在这种情况下，因为 **Set-psbreakpoint 将** 生成一个断点对象，所以它可用作 *断点* 参数的值。</span><span class="sxs-lookup"><span data-stu-id="cea0b-132">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="cea0b-133">第二个命令在 $B 变量的值中显示断点对象。</span><span class="sxs-lookup"><span data-stu-id="cea0b-133">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="cea0b-134">示例4：禁用当前控制台中的所有断点</span><span class="sxs-lookup"><span data-stu-id="cea0b-134">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="cea0b-135">此命令禁用当前控制台中的所有断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-135">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="cea0b-136">可将此命令缩写为：“gbp | dbp”。</span><span class="sxs-lookup"><span data-stu-id="cea0b-136">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="cea0b-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cea0b-137">PARAMETERS</span></span>

### <span data-ttu-id="cea0b-138">-Breakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-138">-Breakpoint</span></span>

<span data-ttu-id="cea0b-139">指定要禁用的断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-139">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="cea0b-140">输入一个包含断点对象的变量，或可获取断点对象的命令（如 Get-PSBreakpoint 命令）。</span><span class="sxs-lookup"><span data-stu-id="cea0b-140">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="cea0b-141">还可以通过管道将断点对象传递到 **set-psbreakpoint** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cea0b-141">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

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

### <span data-ttu-id="cea0b-142">-Id</span><span class="sxs-lookup"><span data-stu-id="cea0b-142">-Id</span></span>

<span data-ttu-id="cea0b-143">禁用具有指定断点 ID 的断点。</span><span class="sxs-lookup"><span data-stu-id="cea0b-143">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="cea0b-144">输入 ID 或包含 ID 的变量。</span><span class="sxs-lookup"><span data-stu-id="cea0b-144">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="cea0b-145">不能通过管道将 Id 传递到 **set-psbreakpoint**。</span><span class="sxs-lookup"><span data-stu-id="cea0b-145">You cannot pipe IDs to **Disable-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="cea0b-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cea0b-146">-PassThru</span></span>

<span data-ttu-id="cea0b-147">返回表示已启用的断点的对象。</span><span class="sxs-lookup"><span data-stu-id="cea0b-147">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="cea0b-148">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="cea0b-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cea0b-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cea0b-149">-Confirm</span></span>

<span data-ttu-id="cea0b-150">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cea0b-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cea0b-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cea0b-151">-WhatIf</span></span>

<span data-ttu-id="cea0b-152">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cea0b-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cea0b-153">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cea0b-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cea0b-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cea0b-154">CommonParameters</span></span>

<span data-ttu-id="cea0b-155">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cea0b-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cea0b-156">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cea0b-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cea0b-157">输入</span><span class="sxs-lookup"><span data-stu-id="cea0b-157">INPUTS</span></span>

### <span data-ttu-id="cea0b-158">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-158">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="cea0b-159">可以通过管道将断点对象传递给 **set-psbreakpoint**。</span><span class="sxs-lookup"><span data-stu-id="cea0b-159">You can pipe a breakpoint object to **Disable-PSBreakpoint**.</span></span>

## <span data-ttu-id="cea0b-160">输出</span><span class="sxs-lookup"><span data-stu-id="cea0b-160">OUTPUTS</span></span>

### <span data-ttu-id="cea0b-161">无或 System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-161">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="cea0b-162">当使用 *PassThru* 参数时， **set-psbreakpoint** 将返回一个表示已禁用的断点的对象。</span><span class="sxs-lookup"><span data-stu-id="cea0b-162">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="cea0b-163">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="cea0b-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cea0b-164">注释</span><span class="sxs-lookup"><span data-stu-id="cea0b-164">NOTES</span></span>

## <span data-ttu-id="cea0b-165">相关链接</span><span class="sxs-lookup"><span data-stu-id="cea0b-165">RELATED LINKS</span></span>

[<span data-ttu-id="cea0b-166">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-166">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="cea0b-167">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-167">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="cea0b-168">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="cea0b-168">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="cea0b-169">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-169">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="cea0b-170">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cea0b-170">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

