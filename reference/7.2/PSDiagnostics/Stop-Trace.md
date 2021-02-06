---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597436"
---
# Stop-Trace

## 摘要
停止事件跟踪日志记录会话。

## SYNTAX

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 将停止一个 Windows 事件跟踪日志记录会话。

以下 cmdlet 使用此 cmdlet：

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

必须从提升的 PowerShell 会话中运行此 cmdlet。

## 示例

### 示例1：停止 WSMan 跟踪日志记录会话

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## PARAMETERS

### -ETS
直接将命令发送到事件跟踪会话，无需保存或计划。

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

### -SessionName
要停止的事件跟踪会话的名称。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

## 输出

### 无

## 注释

## 相关链接

[事件跟踪](/windows/desktop/ETW/event-tracing-portal)

[Start-Trace](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)

