---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595626"
---
# Stop-Transcript

## 摘要
停止脚本。

## SYNTAX

```
Stop-Transcript [<CommonParameters>]
```

## DESCRIPTION

`Stop-Transcript`Cmdlet 可停止 cmdlet 启动的脚本 `Start-Transcript` 。
或者，您可以结束会话来停止脚本。

## 示例

### 示例1：停止所有脚本

```powershell
Stop-Transcript
```

此命令停止所有脚本。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.String

此 cmdlet 将返回一个字符串，其中包含状态消息和输出文件的路径。

## 注释

* 如果尚未启动脚本，则该命令将失败。

*

## 相关链接

[Start-Transcript](Start-Transcript.md)

