---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: d08f883b232abadeacb445e5ba542b4b1fae023b
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "99603785"
---
# Start-ThreadJob

## 摘要
创建类似于 cmdlet 的后台作业 `Start-Job` 。

## SYNTAX

### 脚本块

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### 文件路径

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## DESCRIPTION

`Start-ThreadJob` 创建类似于 cmdlet 的后台作业 `Start-Job` 。 主要区别在于，创建的作业在本地进程中的单独线程中运行。 默认情况下，作业使用启动了作业的调用方的当前工作目录。

该 cmdlet 还支持 **ThrottleLimit** 参数，限制一次运行的作业数。 随着多个作业的启动，它们会排队等待，直到当前的作业数低于限制限制。

## 示例

### 示例 1-创建线程数限制为2的后台作业

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### 示例 2-比较 Start-Job 和 Start-ThreadJob 的性能

此示例显示与之间的 `Start-Job` 差异 `Start-ThreadJob` 。 作业运行 `Start-Sleep` cmdlet 1 秒。 由于作业是并行运行的，因此总执行时间大约为1秒，并包括创建作业所需的任何时间。

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

在将执行时间减1秒后，可以看到， `Start-Job` 大约需要4.8 秒来创建五个作业。 `Start-ThreadJob` 速度快8倍，创建五个作业大约需要0.6 秒。 您的环境中的结果可能会有所不同，但相对改进应该是相同的。

### 示例 3-使用 InputObject 创建作业

在此示例中，脚本块使用 `$input` 变量接收来自 **InputObject** 参数的输入。 此操作也可以通过管道将对象传递给 `Start-ThreadJob` 。

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### 示例 4-将作业输出流到父主机

使用 **StreamingHost** 参数可以将所有主机输出定向到特定主机。 如果没有此参数，输出将转到作业数据流集合，而不会在主机控制台中显示，直到收到作业的输出。

在此示例中，当前主机 `Start-ThreadJob` 使用自动变量传递给 `$Host` 。

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

请注意， `Read-Host` 会显示的提示，并且您可以键入 input。 然后，将显示来自的消息 `Write-Warning` 。 该 `Receive-Job` cmdlet 将返回作业的所有输出。

## PARAMETERS

### -ArgumentList

指定由 **FilePath** 或 **ScriptBlock** 参数指定的脚本的参数数组或参数值。

**ArgumentList** 必须是命令行上的最后一个参数。 参数名称后面的所有值都是参数列表中的解释值。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定要作为后台作业运行的脚本文件。 输入脚本的路径和文件名。 脚本必须位于本地计算机上或本地计算机可以访问的文件夹中。

使用此参数时，PowerShell 会将指定脚本文件的内容转换为脚本块，并将该脚本块作为后台作业运行。

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

指定在作业开始前运行的命令。 将命令括在大括号中， (`{}`) 创建脚本块。

使用此参数可以准备运行作业的会话。 例如，可以使用它将函数和模块添加到会话中。

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

### -InputObject

指定用作脚本块输入的对象。 它还允许管道输入。 使用 `$input` 脚本块中的自动变量来访问输入对象。

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

### -Name

为新作业指定一个友好名称。 你可以使用该名称来确定其他作业 cmdlet （如 cmdlet）的作业 `Stop-Job` 。

默认友好名称为 "Job #"，其中 "#" 是针对每个作业递增的序号。

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

### -ScriptBlock

指定要在后台作业中运行的命令。 将命令括在大括号中， (`{}`) 创建脚本块。 使用 `$Input` 自动变量访问 **InputObject** 参数的值。 此参数是必需的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StreamingHost

此参数提供一个线程安全的方式，以允许 `Write-Host` 输出直接进入传入的 **PSHost** 对象。 如果没有此方法， `Write-Host` 输出将转到作业信息数据流集合，而不会在主机控制台中显示，直到作业完成运行。

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

此参数限制一次运行的作业数。 当作业启动时，它们将排队等待，并等待线程池中的线程可用来运行作业。 默认限制为5个线程。

线程池大小在 PowerShell 会话中是全局性的。 在一个调用中指定 **ThrottleLimit** 将设置同一会话中后续调用的限制。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

## 输出

### ThreadJob.ThreadJob

## 注释

## 相关链接

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Stop-Job](../Microsoft.PowerShell.Core/Stop-Job.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)
