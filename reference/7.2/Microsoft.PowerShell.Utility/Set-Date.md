---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 0f35eea0dfca76b535aad3bdb663d55c224a11d2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595603"
---
# Set-Date

## 摘要
将计算机上的系统时间更改为你指定的时间。

## SYNTAX

### Date（默认值）

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Adjust

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Date`Cmdlet 将计算机上的系统日期和时间更改为指定的日期和时间。
可以通过键入字符串或将 **DateTime** 或 **TimeSpan** 对象传递到来指定新的日期和/或时间 `Set-Date` 。 若要指定新的日期或时间，请使用 **date** 参数。
若要指定更改间隔，请使用 " **调整** " 参数。

## 示例

### 示例1：向系统日期加上三天

此命令将在当前系统日期上加上三天。
它不影响时间。
此命令使用 **date** 参数来指定日期。

`Get-Date`Cmdlet 将当前日期返回为 **DateTime** 对象。 **DateTime** 对象的 **AddDays** 方法将指定的天数 (3) 添加到当前 **DateTime** 对象。

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### 示例2：将系统时钟改回10分钟

此示例将当前系统时间设置为10分钟。

使用 " **调整** " 参数可以指定区域设置的标准时间格式的更改间隔 (减去十分钟) 。

**DisplayHint** 参数指示 PowerShell 仅显示时间，但不影响返回的 **DateTime** 对象 `Set-Date` 。

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### 示例3：将日期和时间设置为变量值

这些命令将本地计算机上的系统日期和时间更改为保存在变量中的日期和时间 `$T` 。 第一个命令获取日期并将其存储在中 `$T` 。

第二个命令使用 **Date** 参数将 **DateTime** 对象传递 `$T` 给 `Set-Date` cmdlet。

```powershell
$T = Get-Date
Set-Date -Date $T
```

### 示例4：将90分钟添加到系统时钟

这些命令将本地计算机上的系统时间前调 90 分钟。

第一个命令使用 `New-TimeSpan` cmdlet 创建一个具有90分钟间隔的 **TimeSpan** 对象，并将其保存在 `$90mins` 变量中。

第二个命令使用的 **调整** 参数 `Set-Date` ，通过变量中的 **TimeSpan** 对象值来调整日期 `$90mins` 。

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMETERS

### -Adjust

指定此 cmdlet 在当前日期和时间中添加或减去的值。
可以在标准日期和时间格式中键入区域设置的调整，或使用 " **调整** " 参数将 **TimeSpan** 对象从传递 `New-TimeSpan` 到 `Set-Date` 。

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Date

将日期和时间更改为指定值。
你可以采用短日期格式键入新日期，并以你的区域设置的标准时间格式键入时间。 或者，您可以从传递 **日期时间** 对象 `Get-Date` 。

如果指定日期，但不指定时间，则会将 `Set-Date` 时间更改为指定日期的午夜。 如果仅指定了时间，则不会更改日期。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

指定显示日期和时间的哪些元素。此参数可接受的值包括：

- **日期** -仅显示日期。
- **时间** -仅显示时间。
- **DateTime** -显示日期和时间。

此参数仅影响显示内容。
它不会影响检索的 **DateTime** 对象 `Get-Date` 。

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.DateTime

可以通过管道将日期传递给 `Set-Date` 。

## 输出

### System.DateTime

`Set-Date` 返回一个对象，该对象表示其设置的日期。

## 注释

- 更改计算机上的日期和时间时，请慎重使用此 cmdlet。 此更改可能会使计算机无法接收由日期或时间触发的系统范围内的事件和更新。 使用 **WhatIf** 和 **Confirm** 参数可避免出现错误。
- 可以将标准 .NET 方法用于与一起使用的 **DateTime** 和 **TimeSpan** 对象 `Set-Date` ，例如 **AddDays**、 **AddMonths** 和 **FromFileTime**。 有关详细信息，请参阅 [DateTime 方法](/dotnet/api/system.datetime) 和

  .NET SDK 中的[TimeSpan 方法](/dotnet/api/system.timespan)。

## 相关链接

[获取日期](Get-Date.md)

[New-TimeSpan](New-TimeSpan.md)
