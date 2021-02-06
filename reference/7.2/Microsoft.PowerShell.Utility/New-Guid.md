---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: df7f9000cf66cebce83e3146cd5c95a7d1a78bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595408"
---
# New-Guid

## 摘要
创建 GUID。

## SYNTAX

```
New-Guid [<CommonParameters>]
```

## DESCRIPTION

Guid **)** (guid 创建随机全局唯一标识符。
如果需要在脚本中使用唯一的 ID，可以根据需要创建一个 GUID。

## 示例

### 示例1：创建 GUID

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

此命令创建随机 GUID。
或者，你可以将此 cmdlet 的输出存储在一个变量中，以在脚本中的其他位置使用。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

### System.Guid

此 cmdlet 将返回 GUID。

## 注释

## 相关链接

