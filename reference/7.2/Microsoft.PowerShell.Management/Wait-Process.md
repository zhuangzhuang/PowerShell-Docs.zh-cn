---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: c469a4e9cf17b03a33bc8b9ff9b06aa95773fc02
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603393"
---
# Wait-Process

## 摘要
等到进程停止后再接受更多输入。

## SYNTAX

### Name（默认值）

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### ID

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### InputObject

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## DESCRIPTION

**Wait-Process** cmdlet 等到一个或多个运行的进程停止后再接受输入。
在 PowerShell 控制台中，此 cmdlet 禁止显示命令提示符，直到进程停止。
可以通过进程名称或进程 ID (PID) 来指定进程，也可以通过管道将进程对象传递给 **Wait-Process**。

**Wait-Process** 仅对在本地计算机上运行的进程有效。

## 示例

### 示例 1：停止进程并等待

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

此示例停止 Notepad 进程，然后等到该进程停止后，再继续下一个命令。

第一个命令使用 **Get-Process** cmdlet 获取 Notepad 进程的 ID。
它将 ID 存储在 $nid 变量中。

第二个命令使用 Stop-Process cmdlet 停止具有存储在 $nid 中的 ID 的进程。

第三个命令使用 **Wait-Process** 等待 Notepad 进程停止。
它使用 **Wait-Process** 的 ID 参数标识该进程。

### 示例 2：指定进程

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

这些命令演示了为 **Wait-Process** 指定进程的三种不同方法。
第一个命令获取 Notepad 进程并将它存储在 $p 变量中。

第二个命令使用 Id 参数，第三个命令使用 Name 参数，第四个命令使用 InputObject 参数。

这些命令的结果相同，因此可以互换。

### 示例 3：在指定时间内等待进程

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

此命令用 30 秒的时间等待 Outlook 和 Winword 进程停止。
如果这两个进程均未停止，则该 cmdlet 会显示非终止错误以及命令提示符。

## PARAMETERS

### -Id

指定进程的进程 ID。
若要指定多个 ID，请使用逗号分隔 ID。
若要查找进程的 PID，请键入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

通过提交进程对象来指定进程。
输入包含进程对象的变量，或键入获取进程对象的命令或表达式（如 Get-Process cmdlet）。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定进程的进程名称。
若要指定多个名称，请使用逗号分隔这些名称。
不支持通配符。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

指定此 cmdlet 等待指定进程停止的最长时间，以秒为单位。
当此时间间隔到期时，该命令会显示一个非终止错误（列出仍在运行的进程）并结束等待。
默认情况下没有任何超时。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Diagnostics.Process

可以将进程对象通过管道传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

只有 Windows 平台支持 cmdlet。

此 cmdlet 使用 WaitForExit 类的方法 **。**

## 相关链接

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
