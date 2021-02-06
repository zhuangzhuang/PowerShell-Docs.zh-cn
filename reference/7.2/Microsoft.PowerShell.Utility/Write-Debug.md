---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3d23f76dbf8e1c9a21805a4914038c8c4f319852
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597463"
---
# Write-Debug

## 摘要
将调试消息写入控制台。

## SYNTAX

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

该 `Write-Debug` cmdlet 从脚本或命令中将调试消息写入主机。

默认情况下，调试消息不会显示在控制台中，但可以使用 **debug** 参数或变量显示它们 `$DebugPreference` 。

## 示例

### 示例 1：了解 $DebugPreference

此示例编写调试消息。

```powershell
Write-Debug "Cannot open file."
```

的默认值 `$DebugPreference` 为 **SilentlyContinue**。 因此，该消息不会显示在控制台中。

### 示例2：更改 $DebugPreference 的值

此示例演示更改变量的值的效果 `$DebugPreference` 。 首先，我们显示的当前值 `$DebugPreference` ，并尝试编写调试消息。 然后，将的值更改 `$DebugPreference` 为 **Continue**，这允许显示调试消息。

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

有关的详细信息 `$DebugPreference` ，请参阅 [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)。

### 示例3：使用 Debug 参数覆盖 $DebugPreference

`Test-Debug`函数将变量的值写入 `$DebugPreference` PowerShell 主机和调试流。 在此示例中，我们使用 **Debug** 参数重写 `$DebugPreference` 该值。

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

请注意， `$DebugPreference` 当你使用 **Debug** 参数时，的值将更改。 此更改只影响函数的作用域。 此值在函数之外不受影响。

有关 **Debug** 通用参数的详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## PARAMETERS

### -Message

指定要发送到控制台的调试消息。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含调试消息的字符串传递给 `Write-Debug` 。

## 输出

### 无

`Write-Debug` 仅写入到调试流。 它不会将任何对象写入管道。

## 注释

## 相关链接

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
