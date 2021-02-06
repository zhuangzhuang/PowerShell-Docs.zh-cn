---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 525b123d48b0f88ca3eef85a3f95cc303a981ca3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598883"
---
# ConvertFrom-Json

## 摘要
将 JSON 格式的字符串转换为自定义对象或哈希表。

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-Json`Cmdlet 将 JavaScript 对象表示法 (json) 格式的字符串转换为自定义 **PSCustomObject** 对象，该对象具有 JSON 字符串中每个字段的属性。 JSON 通常可供网站使用，以提供对象的文本表示形式。 JSON 标准不禁止使用 **PSCustomObject** 禁止使用。 例如，如果 JSON 字符串包含重复的键，则此 cmdlet 仅使用最后一个密钥。 请参阅下面的其他示例。

若要从任何对象生成 JSON 字符串，请使用 `ConvertTo-Json` cmdlet。

此 cmdlet 是在 PowerShell 3.0 中引入的。

> [!NOTE]
> 从 PowerShell 6 开始，此 cmdlet 支持包含注释的 JSON。 接受的注释以两个正斜杠开始 (`//`) 。 注释不会在数据中表示出来，并且可以在文件中写入，而不会损坏数据，也不会引发错误，就像在 PowerShell 5.1 中那样。

## 示例

### 示例1：将 DateTime 对象转换为 JSON 对象

此命令使用 `ConvertTo-Json` 和 `ConvertFrom-Json` Cmdlet 将 **DateTime** 对象从 cmdlet 转换为 JSON 对象，然后将其转换 `Get-Date` 为 **PSCustomObject**。

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

该示例使用 `Select-Object` cmdlet 来获取 **DateTime** 对象的所有属性。 它使用 `ConvertTo-Json` cmdlet 将 **DateTime** 对象转换为设置为 json 对象格式的字符串，并使用 `ConvertFrom-Json` cmdlet 将 JSON 格式的字符串转换为 **PSCustomObject** 对象。

### 示例2：从 web 服务获取 JSON 字符串，并将其转换为 PowerShell 对象

此命令使用 `Invoke-WebRequest` cmdlet 从 web 服务获取 json 字符串，然后使用 `ConvertFrom-Json` CMDLET 将 json 内容转换为可在 PowerShell 中管理的对象。

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

你还可以使用 `Invoke-RestMethod` cmdlet，它会自动将 JSON 内容转换为对象。

### 示例3：将 JSON 字符串转换为自定义对象

此示例演示如何使用 `ConvertFrom-Json` cmdlet 将 JSON 文件转换为 PowerShell 自定义对象。

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

该命令使用 Get-Content cmdlet 获取 JSON 文件中的字符串。 然后，它使用管道运算符将分隔的字符串发送到 `ConvertFrom-Json` cmdlet，该 cmdlet 会将其转换为自定义对象。

### 示例4：将 JSON 字符串转换为哈希表

此命令显示一个示例，在该示例中， `-AsHashtable` 开关可以克服命令的限制。

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

JSON 字符串包含两个键值对，键仅在大小写方面存在差异。 如果不使用开关，则该命令将引发错误。

### 示例5：往返单个元素数组

此命令显示一个示例，在该示例中， `-NoEnumerate` 开关用于往返单个元素 JSON 数组。

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

JSON 字符串包含一个具有单个元素的数组。 在没有开关的情况下，将 JSON 转换为 PSObject，然后使用 `ConvertTo-Json` 命令结果将其转换回单个整数。

## PARAMETERS

### -AsHashtable

将 JSON 转换为哈希表对象。 此开关是在 PowerShell 6.0 中引入的。 在某些情况下，它可以克服 cmdlet 的某些限制 `ConvertFrom-Json` 。

- 如果 JSON 包含具有仅大小写不同的键的列表。 如果没有交换机，这些密钥将被视为相同的键，因此仅使用最后一个键。
- 如果 JSON 包含空字符串，则为。 如果不使用开关，该 cmdlet 将引发错误，因为不 `PSCustomObject` 允许这样做，但哈希表会这样做。 这种情况的一个示例用例是 `project.lock.json` 文件。
- 对于某些数据结构，可以更快地处理哈希表。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

获取或设置允许 JSON 输入具有的最大深度。 默认情况下，它是1024。

此参数是在 PowerShell 6.2 中引入的。

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

### -InputObject

指定要转换为 JSON 对象的 JSON 字符串。 输入一个包含字符串的变量，或键入可获取字符串的命令或表达式。 还可以通过管道将字符串传递给 `ConvertFrom-Json` 。

**InputObject** 参数是必需的，但其值可以是空字符串。 当输入对象为空字符串时，不 `ConvertFrom-Json` 会生成任何输出。 **InputObject** 值不能为 `$null` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoEnumerate

指定不枚举输出。

设置此参数会导致将数组作为单个对象发送，而不是分别发送每个元素。 这可以保证 JSON 可以通过往返 `ConvertTo-Json` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将 JSON 字符串传递给 `ConvertFrom-Json` 。

## 输出

### PSCustomObject

### System.Collections.Hashtable

## 注释

此 cmdlet 是使用 [newtonsoft.json Json.NET](https://www.newtonsoft.com/json)实现的。

从 PowerShell 6 开始， `ConvertTo-Json` 尝试将格式化为时间戳的字符串转换为 **DateTime** 值。 转换后的值是 `[datetime]` 具有属性设置的实例， `Kind` 如下所示：

- `Unspecified`如果输入字符串中没有时区信息，则为。
- `Utc`如果时区信息为后缀，则为 `Z` 。
- `Local`如果将时区信息指定为与类似的尾随 UTC _偏移量_ ，则为 `+02:00` 。 偏移量正确转换为调用方配置的时区。 默认输出格式不表示原始时区偏移量。

## 相关链接

[JavaScript 和 .NET 中的 JavaScript 对象表示法 (JSON) 简介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
