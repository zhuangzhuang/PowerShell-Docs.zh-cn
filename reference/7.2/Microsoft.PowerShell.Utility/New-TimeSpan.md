---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597877"
---
# New-TimeSpan

## 摘要
创建 TimeSpan 对象。

## SYNTAX

### Date（默认值）

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### 时间

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`New-TimeSpan`Cmdlet 可创建表示时间间隔的 **TimeSpan** 对象。
可以使用 **TimeSpan** 对象在 **DateTime** 对象中加减时间。

如果没有参数，则 `New-TimeSpan` 命令将返回表示时间间隔零的 **TimeSpan** 对象。

## 示例

### 示例 1：创建指定持续时间的 TimeSpan 对象

此命令将创建一个持续时间为1小时25分钟的 **TimeSpan** 对象，并将其存储在一个名为的变量中 `$TimeSpan` 。 它将显示 **TimeSpan** 对象的表示形式。

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### 示例 2：创建时间间隔的 TimeSpan 对象

此示例将创建一个新的 **TimeSpan** 对象，用于表示从运行该命令到 2010 年 1 月 1 日之间的时间间隔。

此命令不需要 Start 参数，因为 Start 参数的默认值为当前日期和时间。

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### 示例 3：获取从当前日期起 90 天的日期

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

这些命令将返回当前日期之后的 90 天的日期。

### 示例 4：发现自更新文件以后的 TimeSpan

此命令告诉您自上次更新 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 帮助文件以来该文件的持续时间。
可以在任何文件或任何其他具有 **LastWriteTime** 属性的对象上使用此命令格式。

此命令有效，因为的 **Start** 参数的 `New-TimeSpan` 别名为 **LastWriteTime**。 当你通过管道将具有 **LastWriteTime** 属性的对象传递给时 `New-TimeSpan` ，PowerShell 会将 **LastWriteTime** 属性的值用作 **Start** 参数的值。

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETERS

### -Days

指定时间跨度（以天为单位）。
默认值为 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

指定时间跨度的结束时间。
默认值为当前日期和时间。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Hours

指定时间跨度（以小时为单位）。
默认值为零。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minutes

指定时间跨度（以分钟为单位）。
默认值为 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Seconds

指定时间跨度的长度（以秒为单位）。
默认值为 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Start

指定时间跨度的开始时间。
输入一个表示日期和时间的字符串，例如 "3/15/09" 或日期 **时间** 对象，例如命令中的一个 `Get-Date` 。 默认值为当前日期和时间。

你可以使用 **Start** 或其别名 **LastWriteTime**。
**LastWriteTime** 别名使你可以通过管道将具有 **LastWriteTime** 属性的对象（如文件系统中的文件 `[System.Io.FileIO]` ）传递给的 **启动** 参数 `New-TimeSpan` 。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.DateTime

可以通过管道将表示开始时间的 **DateTime** 对象传递给 `New-TimeSpan` 。

## 输出

### System.TimeSpan

`New-TimeSpan` 返回一个表示时间跨度的对象。

## 注释

## 相关链接

[获取日期](Get-Date.md)

[Set-Date](Set-Date.md)

