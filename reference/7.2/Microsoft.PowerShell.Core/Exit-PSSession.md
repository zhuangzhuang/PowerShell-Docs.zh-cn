---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b76f7dc87105318285c930b6cd2ae4ae10c2b0e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599062"
---
# Exit-PSSession

## 摘要
结束与远程计算机的交互式会话。

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## DESCRIPTION

**Exit-PSSession** cmdlet 结束使用 Enter-PSSession cmdlet 启动的交互式会话。

你还可以使用 **Exit** 关键字来结束交互式会话。
其效果与使用 **Exit-PSSession** 相同。

## 示例

### 示例1：启动和停止交互式会话

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

这些命令启动与 Server01 远程计算机的交互式会话，然后停止该会话。

### 示例2：使用 PSSession 对象启动和停止交互式会话

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

这些命令启动和停止与使用 PowerShell 会话 (**PSSession**) 的 Server01 计算机的交互式会话。

由于交互式会话是使用 PowerShell 会话启动的，因此当交互式会话结束时， **PSSession** 仍然可用。
如果使用 *ComputerName* 参数，则 **输入-PSSession** 会创建一个临时会话，当交互式会话结束时，该会话将关闭。

第一个命令使用 New-PSSession cmdlet 在 Server01 计算机上创建 **PSSession** 。
该命令将 **PSSession** 保存在 $s 的变量中。

第二个命令使用 **Enter-PSSession** 在 $s 中使用 **PSSession** 启动交互式会话。

第三个命令使用 **Exit-PSSession** 来停止交互会话。

最后一个命令显示 $s 变量中的 **PSSession** 。
**State** 属性显示 **PSSession** 仍处于打开状态并可供使用。

### 示例3：使用 Exit 关键字停止会话

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

此示例使用 **Exit** 关键字来停止使用 **Enter-PSSession** 启动的交互式会话。
**Exit** 关键字与使用 **exit-PSSession** 具有相同的效果。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

* 此 cmdlet 仅提取通用参数。

*

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

