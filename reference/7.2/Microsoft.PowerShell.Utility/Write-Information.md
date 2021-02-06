---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: f15902c1c6c298dd02db3edf061d56e1446ecb1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596633"
---
# Write-Information

## 摘要

指定 PowerShell 如何处理命令的信息流数据。

## SYNTAX

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Write-Information`Cmdlet 指定 PowerShell 如何处理命令的信息流数据。

Windows PowerShell 5.0 引入了一个新的结构化信息流。 您可以使用此流在脚本和其调用方或主机应用程序之间传输结构化数据。
`Write-Information` 允许你将信息性消息添加到流，并指定 PowerShell 如何处理命令的信息流数据。 信息流也适用于 `PowerShell.Streams` 、作业和计划任务。

> [!NOTE]
> 信息流不遵循标准约定，其消息的前缀为 "[Stream Name]："。 这适用于简洁和直观的 cleanliness。

`$InformationPreference`首选项变量值确定所提供的消息是否在 `Write-Information` 脚本操作中的预期点显示。 由于此变量的默认值为 `SilentlyContinue` ，因此默认情况下不显示信息性消息。 如果你不想更改的值 `$InformationPreference` ，则可以通过将 `InformationAction` common 参数添加到你的命令来重写其值。 有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 和 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

> [!NOTE]
> 从 Windows PowerShell 5.0 开始， `Write-Host` 是的包装器， `Write-Information` 它允许你使用 `Write-Host` 向信息流发出输出。 这样就可以 **捕获** 或 **抑制** 使用编写的数据， `Write-Host` 同时保留向后兼容性。 有关详细信息，请参阅 [写入主机](Write-Host.md)

`Write-Information` 在 PowerShell 1.x 中也是受支持的工作流活动。

## 示例

### 示例 1：为 Get- results 写入信息

在此示例中，将显示一条信息性消息 "获取功能！"，并在运行该 `Get-WindowsFeature` 命令以查找名称值以 "p" 开头的所有功能。
由于 `$InformationPreference` 变量仍设置为其默认值，因此 `SilentlyContinue` ，您将添加 `InformationAction` 参数以重写 `$InformationPreference` 该值，并显示消息。 `InformationAction`该值将继续，这意味着会显示你的消息，但脚本或命令会继续（如果尚未完成）。

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### 示例 2：写入信息并进行标记

在此示例中，你将使用 `Write-Information` 来让用户知道他们在运行完当前命令后需要运行另一个命令。 该示例将标记 Instructions 添加到信息性消息。 运行此命令之后，如果在信息流中搜索使用 Instructions 标记的消息，则此处指定的消息会处于结果中。

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### 示例 3：将信息写入文件

在此示例中，使用代码将函数中的信息流重定向到。 `Info.txt` `6>` 打开该文件时 `Info.txt` ，你会看到文本 "你想要"。

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### 示例4：传递对象以写入信息

在此示例中，你可以使用 `Write-Information` 从 `Get-Process` 已通过多个管道的对象输出写入前10个最高的 CPU 使用率进程。

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## PARAMETERS

### -MessageData

指定要在用户运行脚本或命令时向他们显示的信息性消息。 为获得最佳结果，请将信息性消息用引号引起来。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Tags

指定一个简单的字符串，该字符串可用于对已添加到信息流的消息进行排序和筛选 `Write-Information` 。 此参数的工作方式类似于中的 **标记** 参数 `New-ModuleManifest` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Object

`Write-Information` 接受要传递到信息流的管道对象。

## 输出

### System.Management.Automation.InformationRecord

## 注释

## 相关链接

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

[Write-Output](Write-Output.md)
