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
# Write-Progress

## 摘要
在 PowerShell 命令窗口中显示一个进度栏。

## SYNTAX

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## DESCRIPTION

`Write-Progress`Cmdlet 会在 PowerShell 命令窗口中显示一个进度栏，用于描述正在运行的命令或脚本的状态。 你可以选择进度栏反映的指示器，以及显示在进度栏上方和下方的文本。

## 示例

### 示例1：显示 For 循环的进度

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

此命令将显示一个从 1 数到 100 的 For 循环的进度。

该 `Write-Progress` cmdlet 包含一个状态栏标题 `Activity` 、一个状态行和变量 `$i` (for 循环) 中的计数器，该计数器指示任务的相对完整性。

### 示例2：显示嵌套 For 循环的进度

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

本示例显示两个嵌套的 For 循环的进度，每个循环由一个进度栏表示。

`Write-Progress`第二个进度栏的命令包含用于将其与第一个进度栏进行区分的 **Id** 参数。

如果没有 **Id** 参数，进度条将重叠在一起，而不是显示在另一个上。

### 示例3：在搜索字符串时显示进度

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

此命令将显示一个用于在系统事件日志中查找字符串“bios”的命令的进度。

**百分比** 值的计算方法是：将已处理的事件数除以已 `$I` 检索的事件总数 `$Events.count` ，然后将该结果乘以100。

### 示例4：显示嵌套进程的每个级别的进度

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

在此示例中，可以使用 **ParentId** 参数，使输出显示每个步骤的进度中的父/子关系。

## PARAMETERS

### -Activity

指定状态栏上方标题中的第一行文本。
此文本描述要报告进度的活动。

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

### -Completed

指示进度栏是否可见。
如果省略此参数，则 `Write-Progress` 显示进度信息。

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

### -CurrentOperation

指定进度栏下方的文本行。
此文本描述当前正在进行的操作。

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

### -Id

指定用于区分各个进度栏的 ID。 在单个命令中创建多个进度栏时，请使用此参数。 如果这些进度栏不具有不同的 ID，则它们会重叠起来，而不是连续地显示。

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

### -ParentId

指定当前活动的父活动。
如果当前活动没有父活动，请使用值 -1。

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

### -PercentComplete

指定已完成活动的百分比。
如果完成百分比未知或不适用，请使用值 -1。

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

### -SecondsRemaining

指定预计的在完成活动之前剩余的秒数。
如果剩余秒数未知或不适用，请使用值 -1。

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

### -SourceId

指定记录的源。 你可以使用它来替代 **Id** ，但不能将其与 **ParentId** 等其他参数一起使用。

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

### -Status

指定状态栏上方标题中的第二行文本。
此文本描述活动的当前状态。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### 无

`Write-Progress` 不会生成任何输出。

## 注释

如果未出现进度栏，请检查变量的值 `$ProgressPreference` 。 如果将该值设置为 SilentlyContinue，则不会显示进度栏。 有关 PowerShell 首选项的详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

该 cmdlet 的参数与 **ProgressRecord** 类的属性相对应。 有关详细信息，请参阅 [ProgressRecord 类](/dotnet/api/system.management.automation.progressrecord)。

## 相关链接

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
