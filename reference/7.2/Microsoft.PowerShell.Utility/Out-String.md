---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 59e5b728604ce37f27b56ebe62e1a22d6af8a966
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "99597251"
---
# Out-String

## 摘要
将输入对象输出为字符串。

## 语法

### NoNewLineFormatting (默认值) 

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## 说明

`Out-String`Cmdlet 将输入对象转换为字符串。 默认情况下， `Out-String` 累积字符串并将它们作为单个字符串返回，但你可以使用 **Stream** 参数定向 `Out-String` 到一次返回一行或创建字符串数组。 此 cmdlet 用于在对象操作不太方便时像在传统 shell 中一样搜索和操作字符串输出。

## 示例

### 示例1：获取当前区域性并将数据转换为字符串

此示例获取当前用户的区域设置，并将对象数据转换为字符串。

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

`$C`变量存储 **Selected.System。全球化 CultureInfo** 对象。 对象是将 `Get-Culture` 管道的输出发送到的结果 `Select-Object` 。 **Property** 参数使用星号 (`*`) 通配符来指定对象中包含的所有属性。

`Out-String` 使用 **InputObject** 参数指定存储在变量中的 **CultureInfo** 对象 `$C` 。 中的对象 `$C` 将转换为字符串。

> [!NOTE]
> 若要查看 `Out-String` 数组，请将输出存储到变量中，并使用数组索引来查看元素。 有关数组索引的详细信息，请参阅 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)。
>
> `$str = Out-String -InputObject $C -Width 100`

### 示例2：使用对象

此示例演示了使用对象和使用字符串之间的差异。 该命令显示一个别名，其中包含文本 **gcm**（的别名） `Get-Command` 。

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` 获取每个别名的 **system.management.automation.aliasinfo** 对象，并沿管道向下发送对象。 `Out-String` 使用 **Stream** 参数将每个对象转换为字符串，而不是将所有对象连接到一个字符串。 **系统** 对象将沿管道向下发送，并 `Select-String` 使用 **Pattern** 参数查找文本 **gcm** 的匹配项。

> [!NOTE]
> 如果省略 **Stream** 参数，则该命令将显示所有别名，因为 `Select-String` 在返回的单个字符串中查找文本 gcm `Out-String` 。

### 示例3：使用 Width 参数防止截断。

虽然中的大部分输出 `Out-String` 都被包装到下一行，但在某些情况下，输出在传递到之前会被格式化系统截断 `Out-String` 。 使用 **Width** 参数可避免截断。

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETERS

### -InputObject

指定要写入字符串的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

### -NoNewline

从 PowerShell 格式化程序生成的输出中删除所有换行符。 保留作为字符串对象一部分的换行符。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

默认情况下，将 `Out-String` 输出单个字符串的格式，如您在控制台中所看到的那样，其中包括任何空白标头或尾随换行符。 **Stream** 参数使 `Out-String` 能够逐个输出每一行。 唯一的例外是多行字符串。 在这种情况下， `Out-String` 仍会将字符串输出为单个多行字符串。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width

指定输出的每一行中的字符数。 任何其他字符将换行到下一行，或根据所使用的格式化程序 cmdlet 进行截断。 **Width** 参数仅适用于正在设置格式的对象。 如果省略此参数，则由主机程序的特征确定宽度。 在终端 (console) windows 中，当前窗口宽度用作默认值。 默认情况下，在安装时，PowerShell 控制台 windows 的宽度为80个字符。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以将对象向下发送到 `Out-String` 。

## 输出

### System.String

`Out-String` 返回它通过输入对象创建的字符串。

## 注释

包含谓词的 cmdlet `Out` 不设置对象的格式。 `Out`Cmdlet 将对象发送到指定的显示目标的格式化程序。

## 相关链接

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-File](Out-File.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-printer](Out-Printer.md)
