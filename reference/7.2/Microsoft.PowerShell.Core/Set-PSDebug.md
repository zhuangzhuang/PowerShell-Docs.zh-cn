---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595820"
---
# <span data-ttu-id="f96bc-102">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="f96bc-102">Set-PSDebug</span></span>

## <span data-ttu-id="f96bc-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f96bc-103">SYNOPSIS</span></span>
<span data-ttu-id="f96bc-104">启用和禁用脚本调试功能、设置跟踪级别和切换严格模式。</span><span class="sxs-lookup"><span data-stu-id="f96bc-104">Turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span>

## <span data-ttu-id="f96bc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f96bc-105">SYNTAX</span></span>

### <span data-ttu-id="f96bc-106">on</span><span class="sxs-lookup"><span data-stu-id="f96bc-106">on</span></span>

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### <span data-ttu-id="f96bc-107">关闭</span><span class="sxs-lookup"><span data-stu-id="f96bc-107">off</span></span>

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## <span data-ttu-id="f96bc-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f96bc-108">DESCRIPTION</span></span>

<span data-ttu-id="f96bc-109">此 `Set-PSDebug` cmdlet 将启用和禁用脚本调试功能、设置跟踪级别和切换严格模式。</span><span class="sxs-lookup"><span data-stu-id="f96bc-109">The `Set-PSDebug` cmdlet turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span> <span data-ttu-id="f96bc-110">默认情况下，PowerShell 调试功能处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="f96bc-110">By default, the PowerShell debug features are off.</span></span>

<span data-ttu-id="f96bc-111">如果 **Trace** 参数的值为，则 `1` 会在运行时跟踪脚本的每一行。</span><span class="sxs-lookup"><span data-stu-id="f96bc-111">When the **Trace** parameter has a value of `1`, each line of script is traced as it runs.</span></span> <span data-ttu-id="f96bc-112">当参数的值为时 `2` ，还将跟踪变量赋值、函数调用和脚本调用。</span><span class="sxs-lookup"><span data-stu-id="f96bc-112">When the parameter has a value of `2`, variable assignments, function calls, and script calls are also traced.</span></span> <span data-ttu-id="f96bc-113">如果指定了 **Step** 参数，将在每个脚本行运行之前提示您。</span><span class="sxs-lookup"><span data-stu-id="f96bc-113">If the **Step** parameter is specified, you're prompted before each line of the script runs.</span></span>

## <span data-ttu-id="f96bc-114">示例</span><span class="sxs-lookup"><span data-stu-id="f96bc-114">EXAMPLES</span></span>

### <span data-ttu-id="f96bc-115">示例1：设置跟踪级别</span><span class="sxs-lookup"><span data-stu-id="f96bc-115">Example 1: Set the trace level</span></span>

<span data-ttu-id="f96bc-116">此示例将跟踪级别设置为 `2` ，然后运行一个显示数字1、2和</span><span class="sxs-lookup"><span data-stu-id="f96bc-116">This example sets the trace level to `2`, and then runs a script that displays the numbers 1, 2, and</span></span>
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### <span data-ttu-id="f96bc-117">示例2：打开单步执行</span><span class="sxs-lookup"><span data-stu-id="f96bc-117">Example 2: Turn on stepping</span></span>

<span data-ttu-id="f96bc-118">此示例将启用 "单步执行"，然后运行显示数字1、2和3的脚本。</span><span class="sxs-lookup"><span data-stu-id="f96bc-118">This example turns on stepping, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### <span data-ttu-id="f96bc-119">示例3：使用严格模式</span><span class="sxs-lookup"><span data-stu-id="f96bc-119">Example 3: Use strict mode</span></span>

<span data-ttu-id="f96bc-120">此示例将 PowerShell 置于严格模式下，并尝试访问不具有赋值的变量。</span><span class="sxs-lookup"><span data-stu-id="f96bc-120">This example puts PowerShell in strict mode and attempts to access a variable that doesn't have an assigned value.</span></span>

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### <span data-ttu-id="f96bc-121">示例4：关闭调试功能</span><span class="sxs-lookup"><span data-stu-id="f96bc-121">Example 4: Turn off debug features</span></span>

<span data-ttu-id="f96bc-122">此示例关闭所有调试功能，然后运行一个显示数字1、2和3的脚本。</span><span class="sxs-lookup"><span data-stu-id="f96bc-122">This example turns off all debugging features, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## <span data-ttu-id="f96bc-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f96bc-123">PARAMETERS</span></span>

### <span data-ttu-id="f96bc-124">-Off</span><span class="sxs-lookup"><span data-stu-id="f96bc-124">-Off</span></span>

<span data-ttu-id="f96bc-125">禁用所有脚本调试功能。</span><span class="sxs-lookup"><span data-stu-id="f96bc-125">Turns off all script debugging features.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96bc-126">-Step</span><span class="sxs-lookup"><span data-stu-id="f96bc-126">-Step</span></span>

<span data-ttu-id="f96bc-127">启用脚本步进。</span><span class="sxs-lookup"><span data-stu-id="f96bc-127">Turns on script stepping.</span></span> <span data-ttu-id="f96bc-128">在每行运行之前，PowerShell 会提示你停止、继续或输入新的解释器级别来检查脚本的状态。</span><span class="sxs-lookup"><span data-stu-id="f96bc-128">Before each line runs, PowerShell prompts you to stop, continue, or enter a new interpreter level to inspect the state of the script.</span></span>

<span data-ttu-id="f96bc-129">指定 **Step** 参数会自动将跟踪级别设置为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="f96bc-129">Specifying the **Step** parameter automatically sets a trace level of `1`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96bc-130">-Strict</span><span class="sxs-lookup"><span data-stu-id="f96bc-130">-Strict</span></span>

<span data-ttu-id="f96bc-131">指定在脚本中引用变量之前，必须先为其赋值。</span><span class="sxs-lookup"><span data-stu-id="f96bc-131">Specifies that variables must be assigned a value before being referenced in a script.</span></span> <span data-ttu-id="f96bc-132">如果在分配值之前引用变量，则 PowerShell 将返回异常错误。</span><span class="sxs-lookup"><span data-stu-id="f96bc-132">If a variable is referenced before a value is assigned, PowerShell returns an exception error.</span></span> <span data-ttu-id="f96bc-133">这等效于 `Set-StrictMode -Version 1`。</span><span class="sxs-lookup"><span data-stu-id="f96bc-133">This is equivalent to `Set-StrictMode -Version 1`.</span></span> <span data-ttu-id="f96bc-134">有关详细信息，请参阅 [set-strictmode](Set-StrictMode.md)。</span><span class="sxs-lookup"><span data-stu-id="f96bc-134">For more information, see [Set-StrictMode](Set-StrictMode.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96bc-135">-Trace</span><span class="sxs-lookup"><span data-stu-id="f96bc-135">-Trace</span></span>

<span data-ttu-id="f96bc-136">为脚本中的每一行指定跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="f96bc-136">Specifies the trace level for each line in a script.</span></span> <span data-ttu-id="f96bc-137">每行在运行时都会被跟踪。</span><span class="sxs-lookup"><span data-stu-id="f96bc-137">Each line is traced as it's run.</span></span>

<span data-ttu-id="f96bc-138">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="f96bc-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f96bc-139">0：关闭脚本跟踪。</span><span class="sxs-lookup"><span data-stu-id="f96bc-139">0: Turn script tracing off.</span></span>
- <span data-ttu-id="f96bc-140">1：跟踪运行的脚本行。</span><span class="sxs-lookup"><span data-stu-id="f96bc-140">1: Trace script lines as they run.</span></span>
- <span data-ttu-id="f96bc-141">2：跟踪脚本行、变量赋值、函数调用和脚本。</span><span class="sxs-lookup"><span data-stu-id="f96bc-141">2: Trace script lines, variable assignments, function calls, and scripts.</span></span>

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f96bc-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f96bc-142">CommonParameters</span></span>

<span data-ttu-id="f96bc-143">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f96bc-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f96bc-144">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f96bc-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f96bc-145">输入</span><span class="sxs-lookup"><span data-stu-id="f96bc-145">INPUTS</span></span>

### <span data-ttu-id="f96bc-146">无</span><span class="sxs-lookup"><span data-stu-id="f96bc-146">None</span></span>

<span data-ttu-id="f96bc-147">不能通过管道将输入用于此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f96bc-147">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="f96bc-148">输出</span><span class="sxs-lookup"><span data-stu-id="f96bc-148">OUTPUTS</span></span>

### <span data-ttu-id="f96bc-149">无</span><span class="sxs-lookup"><span data-stu-id="f96bc-149">None</span></span>

<span data-ttu-id="f96bc-150">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="f96bc-150">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="f96bc-151">注释</span><span class="sxs-lookup"><span data-stu-id="f96bc-151">NOTES</span></span>

## <span data-ttu-id="f96bc-152">相关链接</span><span class="sxs-lookup"><span data-stu-id="f96bc-152">RELATED LINKS</span></span>

[<span data-ttu-id="f96bc-153">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="f96bc-153">about_Debuggers</span></span>](./About/about_Debuggers.md)

[<span data-ttu-id="f96bc-154">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="f96bc-154">Debug-Process</span></span>](../Microsoft.PowerShell.Management/Debug-Process.md)

[<span data-ttu-id="f96bc-155">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f96bc-155">Set-PSBreakpoint</span></span>](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[<span data-ttu-id="f96bc-156">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="f96bc-156">Set-StrictMode</span></span>](Set-StrictMode.md)

[<span data-ttu-id="f96bc-157">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="f96bc-157">Write-Debug</span></span>](../Microsoft.PowerShell.Utility/Write-Debug.md)

