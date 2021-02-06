---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 0b71d59175ed56e7aad6a24035d1eff5503e4d88
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596824"
---
# Get-Uptime

## 摘要
获取自上次启动以来的时间 **跨度** 。

## SYNTAX

### Timespan (默认值) 

```
Get-Uptime [<CommonParameters>]
```

### 因此

```
Get-Uptime [-Since] [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 将返回自上次启动操作系统后所经过的时间。

`Get-Uptime`Cmdlet 是在 PowerShell 6.0 中引入的。

## 示例

### 示例 1-显示自上次启动以来的时间

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### 示例 2-显示上次启动的时间

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETERS

### -自

导致 cmdlet 返回表示操作系统上次启动时间的 **DateTime** 对象。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
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

### 无

## 输出

### System.TimeSpan

这是未使用任何参数时的默认返回类型。

### System.DateTime

使用 **自** 参数时返回此类型。

> [!NOTE]
> 如果启用了 Windows 快速启动，则 Windows 不会更新存储在 **LastBootUpTime** 中的值。 若要禁用快速启动，请运行以下命令： `Powercfg -h off` 。
>
> 有关 Windows 快速启动的详细信息，请参阅将 [快速启动从休眠状态中唤醒](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)。

## 注释

在 Windows 上，返回的值与 WMI 中 **Win32_OperatingSystem** 类的 **LastBootUpTime** 属性相同。

## 相关链接

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

