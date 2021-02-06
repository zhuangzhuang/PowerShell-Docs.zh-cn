---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 18c168e894989fea8b26fe000a624f91d7345332
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603812"
---
# Write-Warning

## 摘要
写入一条警告消息。

## SYNTAX

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## DESCRIPTION

`Write-Warning`Cmdlet 将向 PowerShell 主机写入一条警告消息。 对警告的响应取决于用户的 `$WarningPreference` 变量值和 **WarningAction** 通用参数的使用情况。

## 示例

### 示例 1：写入警告消息

此命令显示消息“WARNING: This is only a test warning”。

```powershell
Write-Warning "This is only a test warning."
```

### 示例 2：将字符串传递给 Write-Warning

此命令显示可以使用管道运算符 (`|`) 将字符串发送到 `Write-Warning` 。
你可以将字符串保存在变量中，如下面的命令中所示，或直接通过管道将字符串传递给 `Write-Warning` 。

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### 示例 3：设置 $WarningPreference 变量并写入警告

此示例显示了对命令的值的影响 `$WarningPreference` `Write-Warning` 。

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

第一个命令显示变量的默认值 `$WarningPreference` ，即 `Continue` 。 因此，当你编写一条警告时，将显示警告消息，并且继续执行。

更改变量的值时 `$WarningPreference` ，该命令的效果将 `Write-Warning` 再次更改。 值为将 `SilentlyContinue` 禁止显示警告。 值 `Stop` 显示警告，然后停止执行命令。

有关变量的详细信息 `$WarningPreference` ，请参阅 [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md)。

### 示例 4：设置 WarningAction 参数并写入警告

此示例演示 **WarningAction** 通用参数对命令的影响 `Write-Warning` 。 可以将 **WarningAction** 通用参数与任何 cmdlet 一起使用，以确定 PowerShell 如何响应该命令生成的警告。 **WarningAction** 通用参数会重写 `$WarningPreference` 该特定命令的的值。

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

此命令使用 `Write-Warning` cmdlet 显示警告。 值为 Inquire 的 WarningAction 通用参数指示系统在该命令显示警告时提示用户。

有关 **WarningAction** 通用参数的详细信息，请参阅 [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)。

## PARAMETERS

### -Message
指定警告消息。

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

可以通过管道将包含警告的字符串传递给 `Write-Warning` 。

## 输出

### 无

`Write-Warning` 仅写入到警告流。 它不生成任何其他输出。

## 注释

变量的默认值 `$WarningPreference` 为 `Continue` ，它显示警告，然后继续执行命令。 若要确定首选项变量（如）的有效值 `$WarningPreference` ，请将其设置为随机字符的字符串，例如 "abc"。 生成的错误消息将列出有效值。

## 相关链接

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)
