---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: d598fe2b1aefdae046b0f1a0893bf4fc407fa7a7
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "99598072"
---
# ConvertTo-Json

## 摘要
将对象转换为 JSON 格式的字符串。

## SYNTAX

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-Json`Cmdlet 将任何 .net 对象转换为 JavaScript 对象表示法 (JSON) 格式的字符串。 这些属性将转换为字段名称，字段名称将转换为属性值，并将删除这些方法。

然后，可以使用 `ConvertFrom-Json` cmdlet 将 json 格式的字符串转换为 json 对象，该对象可在 PowerShell 中轻松管理。

许多网站使用 JSON（而不是 XML）来序列化用于在服务器和基于 Web 的应用之间进行通信的数据。

在 PowerShell 7.2 中， `ConvertTo-Json` 如果输入对象的深度超过了为命令指定的深度，将发出警告。 这可以防止在转换对象时出现不必要的数据丢失。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例 1

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

此命令使用 `ConvertTo-Json` cmdlet 将 GregorianCalendar 对象转换为 JSON 格式的字符串。

### 示例 2

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

此示例显示 cmdlet 的输出， `ConvertTo-Json` 以及不带 **AsArray** 开关参数的和。 您可以看到输出的第二部分包装在数组方括号中。

### 示例 3

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

此命令显示使用的 **压缩** 参数的效果 `ConvertTo-Json` 。 压缩仅影响字符串的外观，而不会影响其有效性。

### 示例 4

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

此示例使用 `ConvertTo-Json` cmdlet 将 **system.object** 对象从 `Get-Date` cmdlet 转换为 JSON 格式的字符串。 该命令使用 `Select-Object` cmdlet 来获取 `*` **DateTime** 对象属性的所有 () 。 输出显示返回的 JSON 字符串 `ConvertTo-Json` 。

### 示例 5

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

此示例演示如何使用 `ConvertTo-Json` 和 `ConvertFrom-Json` cmdlet 将对象转换为 json 字符串和 json 对象。

## PARAMETERS

### -AsArray

将对象输出到数组括号中，即使输入是单个对象也是如此。

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

### -Compress

省略输出字符串中的空格和缩进格式。

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

### -Depth

指定 JSON 表示形式中包括多少级别的已包含对象。 默认值为 2。 在 PowerShell 7.2 中， `ConvertTo-Json` 如果输入对象中的级别数超过此数，将发出警告。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnumsAsStrings

提供一个替代序列化选项，该选项将所有枚举转换为其字符串表示形式。

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

### -EscapeHandling

控制在生成的 JSON 输出中转义某些字符的方式。 默认情况下，只会转义 (如换行符) 的控制字符。

可接受的值为：

- 仅对默认的控制字符进行转义。
- EscapeNonAscii-所有非 ASCII 和控制字符都将被转义。
- EscapeHtml- (`<` 、、 `>` 、 `&` `'` 、 `"`) 和控制字符进行转义。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要转换为 JSON 格式的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 还可以通过管道将对象传递给 `ConvertTo-Json` 。

**InputObject** 参数是必需的，但其值可以为 null (`$null`) 或空字符串。
当输入对象为时 `$null` ，不 `ConvertTo-Json` 会生成任何输出。 当输入对象是空字符串时，将 `ConvertTo-Json` 返回一个空字符串。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.Object

可以通过管道将任何对象传递给 `ConvertTo-Json` 。

## 输出

### System.String

## 注释

`ConvertTo-Json`Cmdlet 是使用[newtonsoft.json Json.NET](https://www.newtonsoft.com/json)实现的。

## 相关链接

[JavaScript 和 .NET 中的 JavaScript 对象表示法 (JSON) 简介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

[NewtonSoft.Js。StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
