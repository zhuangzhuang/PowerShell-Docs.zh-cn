---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 7e0c958201dbd1b42d1f4c4ee286b8aca1f8595a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598676"
---
# Write-Output

## 摘要
将指定的对象发送到管道中的下一个命令。 如果该命令是管道中的最后一个命令，则这些对象将在控制台中显示。

## SYNTAX

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## DESCRIPTION

`Write-Output`Cmdlet 将指定的对象沿管道向下发送到下一个命令。
如果该命令是管道中的最后一个命令，则该对象将在控制台中显示。

`Write-Output` 沿主要管道（也称为 "输出流" 或 "成功管道"）向下发送对象。 若要通过错误管道向下发送错误对象，请使用 Write-Error。

此 cmdlet 通常在脚本中使用，以在控制台上显示字符串和其他对象。 的内置别名之一是，与 `Write-Output` 使用的 `echo` 其他 shell 类似 `echo` ，默认行为是在管道末尾显示输出。 在 PowerShell 中，通常不需要在默认情况下显示输出的实例中使用 cmdlet。 例如，`Get-Process | Write-Output` 等效于 `Get-Process`。 或 `echo "Home directory: $HOME"` 可以写入 `"Home directory: $HOME"` 。

默认情况下，会 `Write-Output` 枚举提供给 cmdlet 的集合。 但是， `Write-Output` 还可用于将集合作为带有 **NoEnumerate** 参数的单个对象向下传递到管道。

## 示例

### 示例1：获取对象并将它们写入控制台

```powershell
$P = Get-Process
Write-Output $P
```

第一个命令获取在计算机上运行的进程，并将其存储在 `$P` 变量中。

第二个和第三个命令在控制台上显示中的进程对象 `$P` 。

### 示例2：将输出传递给另一个 cmdlet

```powershell
Write-Output "test output" | Get-Member
```

此命令通过管道将 "测试输出" 字符串传递给 `Get-Member` cmdlet，该 cmdlet 将显示 **system.object** 类的成员，并演示该字符串是沿管道传递的。

### 示例3：在输出中取消枚举

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

此命令添加 **NoEnumerate** 参数以将集合或数组视为通过管道的单个对象。

## PARAMETERS

### -InputObject

指定要通过管道向下发送的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoEnumerate

默认情况下，该 `Write-Output` cmdlet 始终枚举其输出。 **NoEnumerate** 参数取消默认行为，并阻止 `Write-Output` 枚举输出。 如果将命令括在括号中，则 **NoEnumerate** 参数不起作用，因为括号会强制执行枚举。 例如， `(Write-Output 1,2,3)` 仍枚举数组。

> [!NOTE]
> 此开关仅适用于 PowerShell Core 6.2 和更高版本。 在较旧版本的 PowerShell Core 上，即使使用此开关，也仍会枚举该集合。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将对象传递给 `Write-Output` 。

## 输出

### System.Management.Automation.PSObject

`Write-Output` 返回作为输入提交的对象。

## 注释

## 相关链接

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Tee-Object](Tee-Object.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
