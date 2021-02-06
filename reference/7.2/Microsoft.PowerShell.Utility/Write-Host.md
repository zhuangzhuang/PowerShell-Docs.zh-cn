---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 01d045a6254b40161462bf36976fdbf57f205705
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596425"
---
# Write-Host

## 摘要

将自定义的输出写入主机。

## SYNTAX

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## DESCRIPTION

此 `Write-Host` cmdlet 的主要用途是生成 (主机) 只显示输出，例如，在提示用户输入与 [读取主机](Read-Host.md)的输入时打印彩色文本（例如）。
`Write-Host` 使用 [ToString ( # B1 ](/dotnet/api/system.object.tostring) 方法来写入输出。 与此相反，若要将数据输出到管道，请使用 [写入输出](Write-Output.md) 或隐式输出。

可以通过使用参数指定文本颜色 `ForegroundColor` ，也可以使用参数指定背景色 `BackgroundColor` 。 Separator 参数允许你指定用于分隔显示对象的字符串。 具体的结果取决于托管 PowerShell 的程序。

> [!NOTE]
> 从 Windows PowerShell 5.0 开始， `Write-Host` 是的包装器， `Write-Information` 它允许你使用 `Write-Host` 向信息流发出输出。 这样就可以 **捕获** 或 **抑制** 使用编写的数据， `Write-Host` 同时保留向后兼容性。
>
> `$InformationPreference`首选项变量和 `InformationAction` 通用参数不会影响 `Write-Host` 消息。 此规则的例外情况是 `-InformationAction Ignore` ，它可以有效地取消 `Write-Host` 输出。  (参见 "Example 5" ) 

## 示例

### 示例1：写入控制台而不添加新行

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

此命令显示具有参数的字符串 "no 换行符 test" `NoNewline` 。

写入第二个字符串，但该字符串最终与第一个字符串在同一行上，因为缺少分隔字符串的换行符。

### 示例2：写入控制台并包含分隔符

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

此命令显示从2到12的偶数。 **Separator** 参数用于添加字符串 `, +2= ` (逗号、空格、 `+` 、、 `2` `=`) 。

### 示例3：用不同文本和背景色编写

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

此命令显示从2到12的偶数。 它使用 `ForegroundColor` 参数来输出深绿色文本，并使用 `BackgroundColor` 参数来显示白色背景。

### 示例4：用不同文本和背景色编写

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

此命令显示字符串“Red on white text”。 文本为红色，由 `ForegroundColor` 参数定义。 背景为白色，由 `BackgroundColor` 参数定义。

### 示例5：取消 Write-Host 的输出

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

这些命令可以有效地取消 cmdlet 的输出 `Write-Host` 。 第一个 `InformationAction` 参数将参数与值一起使用， `Ignore` 以禁止输出到信息流。
第二个示例将命令的信息流重定向到 `$null` 变量，从而禁止显示。

## PARAMETERS

### -BackgroundColor

指定背景色。 没有默认值。 此参数的可接受值为：

- 黑色
- 深蓝色
- 深绿色
- 深青色
- 深红色
- 深洋红色
- 深黄色
- 灰色
- 深灰色
- 蓝色
- 绿色
- 蓝
- Red
- 洋红色
- Yellow
- White

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

指定文本颜色。 没有默认值。 此参数的可接受值为：

- 黑色
- 深蓝色
- 深绿色
- 深青色
- 深红色
- 深洋红色
- 深黄色
- 灰色
- 深灰色
- 蓝色
- 绿色
- 蓝
- Red
- 洋红色
- Yellow
- White

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

输入对象的字符串表示形式连接起来以形成输出。 不会在输出字符串之间插入空格或换行符。 在最后一个输出字符串之后不添加任何行。

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

### -Object

要在主机中显示的对象。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Separator

指定要在主机显示的对象之间插入的分隔符字符串。

```yaml
Type: System.Object
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

### System.Object

可以通过管道将要写入的对象传递给主机。

## 输出

### 无

`Write-Host` 将对象发送到主机。 它不返回任何对象。 但是，主机 `Write-Host` 会显示发送给它的对象。

## 注释

- 将集合写入主机时，集合中的元素将打印在由单个空格分隔的同一行中。 这可以用 **Separator** 参数重写。

- 非基元数据类型（如具有属性的对象）可能导致意外的结果，而不提供有意义的输出。 例如， `Write-Host @{a = 1; b = 2}` 将打印 `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` 到主机。

## 相关链接

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
