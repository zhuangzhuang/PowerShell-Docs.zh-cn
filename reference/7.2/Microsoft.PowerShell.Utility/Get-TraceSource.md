---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: c196d00359c9b20b5dc1fefc0ab2b94655703f6f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599069"
---
# Get-TraceSource

## 摘要
获取用于跟踪的 PowerShell 组件。

## SYNTAX

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**TraceSource** cmdlet 获取当前正在使用的 PowerShell 组件的跟踪源。
你可以使用数据来确定你可以跟踪哪些 PowerShell 组件。
在跟踪过程中，该组件将生成有关其内部处理过程中每个步骤的详细消息。
开发人员使用跟踪数据来监视数据流、程序执行情况和错误。

跟踪 cmdlet 专为 PowerShell 开发人员而设计，但可供所有用户使用。

## 示例

### 示例1：按名称获取跟踪源

```
PS C:\> Get-TraceSource -Name "*provider*"
```

此命令将获取名称中包含提供程序的所有跟踪源。

### 示例2：获取所有跟踪源

```
PS C:\> Get-TraceSource
```

此命令将获取可以跟踪的所有 PowerShell 组件。

## PARAMETERS

### -Name

指定要获取的跟踪源。
允许使用通配符。
参数名称 *名称* 是可选的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含跟踪源名称的字符串传递给 **TraceSource**。

## 输出

### System.web. System.management.automation.pstracesource

**TraceSource** 返回表示跟踪源的对象。

## 注释

## 相关链接

[Set-TraceSource](Set-TraceSource.md)

[Trace-Command](Trace-Command.md)

