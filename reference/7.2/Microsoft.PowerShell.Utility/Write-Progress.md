---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 2e2bd5474198745d72ad2b87c3c305695a198f22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597447"
---
# <span data-ttu-id="3d264-102">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="3d264-102">Write-Progress</span></span>

## <span data-ttu-id="3d264-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3d264-103">SYNOPSIS</span></span>
<span data-ttu-id="3d264-104">在 PowerShell 命令窗口中显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="3d264-104">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="3d264-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d264-105">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="3d264-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3d264-106">DESCRIPTION</span></span>

<span data-ttu-id="3d264-107">`Write-Progress`Cmdlet 会在 PowerShell 命令窗口中显示一个进度栏，用于描述正在运行的命令或脚本的状态。</span><span class="sxs-lookup"><span data-stu-id="3d264-107">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="3d264-108">你可以选择进度栏反映的指示器，以及显示在进度栏上方和下方的文本。</span><span class="sxs-lookup"><span data-stu-id="3d264-108">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="3d264-109">示例</span><span class="sxs-lookup"><span data-stu-id="3d264-109">EXAMPLES</span></span>

### <span data-ttu-id="3d264-110">示例1：显示 For 循环的进度</span><span class="sxs-lookup"><span data-stu-id="3d264-110">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="3d264-111">此命令将显示一个从 1 数到 100 的 For 循环的进度。</span><span class="sxs-lookup"><span data-stu-id="3d264-111">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="3d264-112">该 `Write-Progress` cmdlet 包含一个状态栏标题 `Activity` 、一个状态行和变量 `$i` (for 循环) 中的计数器，该计数器指示任务的相对完整性。</span><span class="sxs-lookup"><span data-stu-id="3d264-112">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="3d264-113">示例2：显示嵌套 For 循环的进度</span><span class="sxs-lookup"><span data-stu-id="3d264-113">Example 2: Display the progress of nested For loops</span></span>

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

<span data-ttu-id="3d264-114">本示例显示两个嵌套的 For 循环的进度，每个循环由一个进度栏表示。</span><span class="sxs-lookup"><span data-stu-id="3d264-114">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="3d264-115">`Write-Progress`第二个进度栏的命令包含用于将其与第一个进度栏进行区分的 **Id** 参数。</span><span class="sxs-lookup"><span data-stu-id="3d264-115">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="3d264-116">如果没有 **Id** 参数，进度条将重叠在一起，而不是显示在另一个上。</span><span class="sxs-lookup"><span data-stu-id="3d264-116">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="3d264-117">示例3：在搜索字符串时显示进度</span><span class="sxs-lookup"><span data-stu-id="3d264-117">Example 3: Display the progress while searching for a string</span></span>

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

<span data-ttu-id="3d264-118">此命令将显示一个用于在系统事件日志中查找字符串“bios”的命令的进度。</span><span class="sxs-lookup"><span data-stu-id="3d264-118">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="3d264-119">**百分比** 值的计算方法是：将已处理的事件数除以已 `$I` 检索的事件总数 `$Events.count` ，然后将该结果乘以100。</span><span class="sxs-lookup"><span data-stu-id="3d264-119">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="3d264-120">示例4：显示嵌套进程的每个级别的进度</span><span class="sxs-lookup"><span data-stu-id="3d264-120">Example 4: Display progress for each level of a nested process</span></span>

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

<span data-ttu-id="3d264-121">在此示例中，可以使用 **ParentId** 参数，使输出显示每个步骤的进度中的父/子关系。</span><span class="sxs-lookup"><span data-stu-id="3d264-121">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="3d264-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d264-122">PARAMETERS</span></span>

### <span data-ttu-id="3d264-123">-Activity</span><span class="sxs-lookup"><span data-stu-id="3d264-123">-Activity</span></span>

<span data-ttu-id="3d264-124">指定状态栏上方标题中的第一行文本。</span><span class="sxs-lookup"><span data-stu-id="3d264-124">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="3d264-125">此文本描述要报告进度的活动。</span><span class="sxs-lookup"><span data-stu-id="3d264-125">This text describes the activity whose progress is being reported.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-126">-Completed</span><span class="sxs-lookup"><span data-stu-id="3d264-126">-Completed</span></span>

<span data-ttu-id="3d264-127">指示进度栏是否可见。</span><span class="sxs-lookup"><span data-stu-id="3d264-127">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="3d264-128">如果省略此参数，则 `Write-Progress` 显示进度信息。</span><span class="sxs-lookup"><span data-stu-id="3d264-128">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

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

### <span data-ttu-id="3d264-129">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="3d264-129">-CurrentOperation</span></span>

<span data-ttu-id="3d264-130">指定进度栏下方的文本行。</span><span class="sxs-lookup"><span data-stu-id="3d264-130">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="3d264-131">此文本描述当前正在进行的操作。</span><span class="sxs-lookup"><span data-stu-id="3d264-131">This text describes the operation that is currently taking place.</span></span>

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

### <span data-ttu-id="3d264-132">-Id</span><span class="sxs-lookup"><span data-stu-id="3d264-132">-Id</span></span>

<span data-ttu-id="3d264-133">指定用于区分各个进度栏的 ID。</span><span class="sxs-lookup"><span data-stu-id="3d264-133">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="3d264-134">在单个命令中创建多个进度栏时，请使用此参数。</span><span class="sxs-lookup"><span data-stu-id="3d264-134">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="3d264-135">如果这些进度栏不具有不同的 ID，则它们会重叠起来，而不是连续地显示。</span><span class="sxs-lookup"><span data-stu-id="3d264-135">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-136">-ParentId</span><span class="sxs-lookup"><span data-stu-id="3d264-136">-ParentId</span></span>

<span data-ttu-id="3d264-137">指定当前活动的父活动。</span><span class="sxs-lookup"><span data-stu-id="3d264-137">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="3d264-138">如果当前活动没有父活动，请使用值 -1。</span><span class="sxs-lookup"><span data-stu-id="3d264-138">Use the value -1 if the current activity has no parent activity.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-139">-PercentComplete</span><span class="sxs-lookup"><span data-stu-id="3d264-139">-PercentComplete</span></span>

<span data-ttu-id="3d264-140">指定已完成活动的百分比。</span><span class="sxs-lookup"><span data-stu-id="3d264-140">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="3d264-141">如果完成百分比未知或不适用，请使用值 -1。</span><span class="sxs-lookup"><span data-stu-id="3d264-141">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-142">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="3d264-142">-SecondsRemaining</span></span>

<span data-ttu-id="3d264-143">指定预计的在完成活动之前剩余的秒数。</span><span class="sxs-lookup"><span data-stu-id="3d264-143">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="3d264-144">如果剩余秒数未知或不适用，请使用值 -1。</span><span class="sxs-lookup"><span data-stu-id="3d264-144">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-145">-SourceId</span><span class="sxs-lookup"><span data-stu-id="3d264-145">-SourceId</span></span>

<span data-ttu-id="3d264-146">指定记录的源。</span><span class="sxs-lookup"><span data-stu-id="3d264-146">Specifies the source of the record.</span></span> <span data-ttu-id="3d264-147">你可以使用它来替代 **Id** ，但不能将其与 **ParentId** 等其他参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="3d264-147">You can use this in place of **Id** but cannot be used with other parameters like **ParentId**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d264-148">-Status</span><span class="sxs-lookup"><span data-stu-id="3d264-148">-Status</span></span>

<span data-ttu-id="3d264-149">指定状态栏上方标题中的第二行文本。</span><span class="sxs-lookup"><span data-stu-id="3d264-149">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="3d264-150">此文本描述活动的当前状态。</span><span class="sxs-lookup"><span data-stu-id="3d264-150">This text describes current state of the activity.</span></span>

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

### <span data-ttu-id="3d264-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d264-151">CommonParameters</span></span>

<span data-ttu-id="3d264-152">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3d264-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d264-153">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3d264-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3d264-154">输入</span><span class="sxs-lookup"><span data-stu-id="3d264-154">INPUTS</span></span>

### <span data-ttu-id="3d264-155">无</span><span class="sxs-lookup"><span data-stu-id="3d264-155">None</span></span>

<span data-ttu-id="3d264-156">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d264-156">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3d264-157">输出</span><span class="sxs-lookup"><span data-stu-id="3d264-157">OUTPUTS</span></span>

### <span data-ttu-id="3d264-158">无</span><span class="sxs-lookup"><span data-stu-id="3d264-158">None</span></span>

<span data-ttu-id="3d264-159">`Write-Progress` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="3d264-159">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="3d264-160">注释</span><span class="sxs-lookup"><span data-stu-id="3d264-160">NOTES</span></span>

<span data-ttu-id="3d264-161">如果未出现进度栏，请检查变量的值 `$ProgressPreference` 。</span><span class="sxs-lookup"><span data-stu-id="3d264-161">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="3d264-162">如果将该值设置为 SilentlyContinue，则不会显示进度栏。</span><span class="sxs-lookup"><span data-stu-id="3d264-162">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="3d264-163">有关 PowerShell 首选项的详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3d264-163">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="3d264-164">该 cmdlet 的参数与 **ProgressRecord** 类的属性相对应。</span><span class="sxs-lookup"><span data-stu-id="3d264-164">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="3d264-165">有关详细信息，请参阅 [ProgressRecord 类](/dotnet/api/system.management.automation.progressrecord)。</span><span class="sxs-lookup"><span data-stu-id="3d264-165">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="3d264-166">相关链接</span><span class="sxs-lookup"><span data-stu-id="3d264-166">RELATED LINKS</span></span>

[<span data-ttu-id="3d264-167">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="3d264-167">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="3d264-168">Write-Error</span><span class="sxs-lookup"><span data-stu-id="3d264-168">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="3d264-169">Write-Host</span><span class="sxs-lookup"><span data-stu-id="3d264-169">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="3d264-170">Write-Output</span><span class="sxs-lookup"><span data-stu-id="3d264-170">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="3d264-171">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="3d264-171">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="3d264-172">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="3d264-172">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="3d264-173">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="3d264-173">Write-Warning</span></span>](Write-Warning.md)
