---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597450"
---
# Get-TimeZone

## 摘要
获取当前时区或可用时区的列表。

## SYNTAX

### Name（默认值）

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### ID

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### ListAvailable

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## DESCRIPTION

**获取时区** cmdlet 获取当前时区或可用时区的列表。

## 示例

### 示例1：获取当前时区

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

此命令获取当前时区。

### 示例2：获取与指定的字符串匹配的时区

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

此命令将获取与指定的通配符匹配的所有时区。

### 示例3：获取所有可用时区

```
PS C:\> Get-TimeZone -ListAvailable
```

此命令将获取所有可用时区。

## PARAMETERS

### -Id

指定为字符串数组，此 cmdlet 获取的时区的 ID 或 id。

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

指示此 cmdlet 获取所有可用时区。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

以字符串数组的形式指定此 cmdlet 获取的时区的名称。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

## 输出

### TimeZoneInfo []

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[Set-TimeZone](Set-TimeZone.md)
