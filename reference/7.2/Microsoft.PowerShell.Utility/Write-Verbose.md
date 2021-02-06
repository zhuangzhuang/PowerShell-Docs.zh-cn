---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 177e32106f37c59593bbecac13843f6603327cc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598894"
---
# Write-Verbose

## 摘要
将文本写入详细消息流。

## SYNTAX

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

`Write-Verbose`Cmdlet 将文本写入 PowerShell 中的详细消息流。 通常，详细消息流用于传递有关命令处理的详细信息。

默认情况下，不显示详细消息流，但你可以通过更改变量的值 `$VerbosePreference` 或在任何命令中使用 **verbose** 通用参数来显示它。

## 示例

### 示例1：编写状态消息

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

这些命令使用 `Write-Verbose` cmdlet 来显示状态消息。 默认情况下，不显示此消息。

第二个命令使用 **verbose** 通用参数，该参数显示任何详细消息，而不考虑变量的值 `$VerbosePreference` 。

### 示例2：设置 $VerbosePreference 并写入状态消息

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

这些命令使用 `Write-Verbose` cmdlet 来显示状态消息。 默认情况下，不显示此消息。

第一个命令将 "Continue" 的值分配给 `$VerbosePreference` 首选项变量。 默认值 `SilentlyContinue` 禁止详细消息。 第二个命令写入详细消息。

## PARAMETERS

### -Message

指定要显示的消息。 此参数是必需的。 还可以通过管道将消息字符串传递给 `Write-Verbose` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含消息的字符串传递给 `Write-Verbose` 。

## 输出

### 无

`Write-Verbose` 仅写入详细消息流。

## 注释

- 仅在该命令使用 **Verbose** 通用参数时才返回详细消息。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。
- 在 Windows PowerShell 后台作业和远程命令中， `$VerbosePreference` 作业会话和远程会话中的变量确定默认情况下是否显示详细消息。
  有关变量的详细信息 `$VerbosePreference` ，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

## 相关链接

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Warning](Write-Warning.md)
