---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 660d2b4845df8091ff8b69b28c4e7695af557122
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597669"
---
# Debug-Process

## 摘要
调试在本地计算机上运行的一个或多个进程。

## SYNTAX

### Name（默认值）

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ID

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Debug-Process`Cmdlet 可将调试程序附加到本地计算机上的一个或多个正在运行的进程。
可以通过进程名称或进程 ID (PID) 来指定进程，也可以将进程对象通过管道传送给此 cmdlet。

此 cmdlet 将附加当前为该进程注册的调试程序。 使用此 cmdlet 之前，请先验证调试程序是否已下载并正确配置。

## 示例

### 示例 1：将调试程序附加到计算机上的进程

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

此命令将调试程序附加到计算机上的 PowerShell 进程。

### 示例 2：将调试程序附加到以指定字符串开头的所有进程

```
PS C:\> Debug-Process -Name "SQL*"
```

此命令将调试程序附加到名称以 SQL 开头的所有进程。

### 示例 3：将调试程序附加到多个进程

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

此命令将调试程序附加到 Winlogon、Explorer 和 Outlook 进程。

### 示例 4：将调试程序附加到多个进程 ID

```
PS C:\> Debug-Process -Id 1132, 2028
```

此命令将调试程序附加到进程 ID 为 1132 和 2028 的进程。

### 示例 5：使用 Get-Process 获取进程，然后将调试程序附加到它

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

此命令将调试程序附加到计算机上的 PowerShell 进程。 它使用 `Get-Process` cmdlet 获取计算机上的 PowerShell 进程，并使用管道操作员 (`|`) 将进程发送到 `Debug-Process` cmdlet。

若要指定特定的 PowerShell 进程，请使用的 ID 参数 `Get-Process` 。

### 示例 6：将调试程序附加到本地计算机上的当前进程

```
PS C:\> $PID | Debug-Process
```

此命令将调试程序附加到计算机上的当前 PowerShell 进程。

该命令使用 `$PID` 自动变量，其中包含当前 PowerShell 进程的进程 ID。 然后，它使用管道运算符 (`|`) 将进程 ID 发送到 `Debug-Process` cmdlet。

有关自动变量的详细信息 `$PID` ，请参阅 about_Automatic_Variables。

### 示例7：将调试程序附加到使用 InputObject 参数的进程

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

此命令将调试程序附加到本地计算机上的 PowerShell 进程。

第一个命令使用 `Get-Process` cmdlet 来获取计算机上的 PowerShell 进程。 它将生成的进程对象保存在变量中 `$P` 。

第二个命令使用 cmdlet 的 **InputObject** 参数 `Debug-Process` 来提交变量中的进程对象 `$P` 。

## PARAMETERS

### -Id

指定要调试的进程的进程 ID。 Id 参数名为可选项。

要查找进程的进程 ID，请键入 `Get-Process`。

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

指定表示要调试的进程的进程对象。 输入包含进程对象的变量或获取进程对象的命令（如 `Get-Process` cmdlet）。 还可以将进程对象通过管道传送给此 cmdlet。

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

指定要调试的进程的名称。 如果存在多个同名进程，则此 cmdlet 会将调试程序附加到所有该名称的进程。 **Name** 参数是可选的。

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

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Int32、System.Diagnostics.Process、System.String

可以通过管道将进程 ID (Int32)、进程对象 (System.Diagnostics.Process) 或进程名称 (String) 传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 使用 Windows Management Instrumentation (WMI) Win32_Process 类的 AttachDebugger 方法。 有关此方法的详细信息，请参阅 MSDN library 中的 [AttachDebugger 方法](https://go.microsoft.com/fwlink/?LinkId=143640) 。

## 相关链接

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
