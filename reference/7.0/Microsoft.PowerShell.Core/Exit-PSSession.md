---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 7947855afa08bc3301d02e64fcb2ad8bb6b59db7
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975118"
---
# Exit-PSSession

## 摘要
结束与远程计算机的交互式会话。

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## 说明

`Exit-PSSession`Cmdlet 可结束使用 cmdlet 启动的交互式会话 `Enter-PSSession` 。

你还可以使用 `exit` 关键字来结束交互式会话。 此效果与使用相同 `Exit-PSSession` 。

## 示例

### 示例1：启动和停止交互式会话

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

这些命令启动与 Server01 远程计算机的交互式会话，然后停止该会话。

### 示例2：使用 PSSession 对象启动和停止交互式会话

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

这些命令启动和停止与使用 PowerShell 会话 (**PSSession**) 的 Server01 计算机的交互式会话。

由于交互式会话是使用 PowerShell 会话启动的，因此当交互式会话结束时， **PSSession** 仍然可用。 如果使用 _ComputerName_ 参数，则将 `Enter-PSSession` 创建一个在交互式会话结束时关闭的临时会话。

第一个命令使用 `New-PSSession` cmdlet 在 Server01 计算机上创建 **PSSession** 。 该命令将 **PSSession** 保存在 `$s` 变量中。

第二个命令使用 `Enter-PSSession` 在中使用 **PSSession** 启动交互式会话 `$s` 。

第三个命令使用 `Exit-PSSession` 来停止交互会话。

最后一个命令显示变量中的 PSSession `$s` 。 **State** 属性显示 **PSSession** 仍处于打开状态并可供使用。

### 示例3：使用 Exit 关键字停止会话

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

此示例使用 `exit` 关键字来停止使用启动的交互式会话 `Enter-PSSession` 。 `exit`关键字与使用的效果相同 `Exit-PSSession` 。

## parameters

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 说明

此 cmdlet 仅提取通用参数。

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
