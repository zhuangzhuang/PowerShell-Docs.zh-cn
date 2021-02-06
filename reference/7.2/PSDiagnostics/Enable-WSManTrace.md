---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595619"
---
# Enable-WSManTrace

## 摘要
启动启用了 WSMan 提供程序的日志记录会话。

## SYNTAX

```
Enable-WSManTrace [<CommonParameters>]
```

## DESCRIPTION
此 cmdlet 将启动启用了 WSMan 提供程序的日志记录会话。 启用以下事件提供程序：

- 事件转发
- IpmiDrv
- IPMIPrv
- WinRM
- WinrsCmd
- WinrsExe
- WinrsMgr
- WSManProvHost

会话名为 "wsmlog"。

此 cmdlet 使用 `Start-Trace` cmdlet。

必须从提升的 PowerShell 会话中运行此 cmdlet。

## 示例

### 示例1：启动 WSMan 日志记录会话。

```powershell
Enable-WSManTrace
```

## PARAMETERS

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

[Disable-WSManTrace](Disable-WSManTrace.md)

