---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597050"
---
# Get-UICulture

## 摘要
获取操作系统中的当前 UI 区域性设置。

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## DESCRIPTION

`Get-UICulture`Cmdlet 将获取有关 Windows (UI) 区域性设置的当前用户界面的信息。
UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。

你还可以使用 `Get-Culture` cmdlet 来获取系统上的当前区域性。
区域性确定项的显示格式，例如数字、货币和日期。

## 示例

### 示例1：获取 UI 区域性

```powershell
Get-UICulture
```

此命令获取当前 UI 区域性信息。

### 示例2：获取 UI 区域性并设置结果格式

```powershell
Get-UICulture | Format-List *
```

此命令在列表中显示当前 UI 区域性的所有属性的值。

### 示例3：获取 Calendar 属性的值

```powershell
(Get-UICulture).Calendar
```

此命令显示当前 UI 区域性的 **Calendar** 属性的当前值。
Calendar 只是 UI 区域性的一个属性。
若要查看所有属性，请键入 `Get-UICulture | Get-Member` 。

### 示例4：获取短日期模式

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

此命令显示当前 UI 区域性的短日期模式。
若要查看 UI 区域性的 **DateTimeFormat** 属性的所有子属性，请键入 `(Get-UICulture).DateTimeFormat | gm` 。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Globalization.CultureInfo、Microsoft.PowerShell.VistaCultureInfo

`Get-UICulture` 返回表示当前 UI 区域性的对象。
在 Windows PowerShell 3.0 中，它返回 **CultureInfo** 对象。
在 Windows PowerShell 2.0 中，它返回 **VistaCultureInfo** 对象。

## 注释

- 你还可以使用 `$PsCulture` 和 `$PsUICulture` 变量。 `$PsCulture`变量存储当前区域性的名称， `$PsUICulture` 变量存储当前 UI 区域性的名称。

## 相关链接

