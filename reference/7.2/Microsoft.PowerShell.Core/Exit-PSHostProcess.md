---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595398"
---
# Exit-PSHostProcess

## 摘要
关闭包含本地进程的交互式会话。

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## DESCRIPTION

`Exit-PSHostProcess`Cmdlet 可通过运行 cmdlet 来关闭与已打开的本地进程的交互式会话 `Enter-PSHostProcess` 。 `Exit-PSHostProcess`完成调试或排查进程内运行的脚本时，可以从进程中运行 cmdlet。 从 PowerShell 6.2 开始，非 Windows 平台上支持此 cmdlet。

## 示例

### 示例1：退出进程

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

在此示例中，你一直在活动进程中，调试在进程的运行空间中运行的脚本，如中所述 `Enter-PSHostProcess` 。 键入 `exit` 命令退出调试程序后，运行 `Exit-PSHostProcess` cmdlet 以关闭与此进程的交互式会话。
Cmdlet 可在进程中关闭会话，并返回到 `PS C:\>` 提示符。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

## 注释

## 相关链接

[Enter-PSHostProcess](Enter-PSHostProcess.md)

