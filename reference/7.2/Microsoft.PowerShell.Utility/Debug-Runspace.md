---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 3f01b7624ffcbca472b09bdb83a7440f3526db43
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596230"
---
# Debug-Runspace

## 摘要
启动与运行空间的交互式调试会话。

## SYNTAX

### RunspaceParameterSet (默认值) 

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Debug-Runspace`Cmdlet 可启动与本地或远程活动运行空间之间的交互式调试会话。 你可以查找要通过先运行来进行调试的运行空间， `Get-Process` 以查找与 PowerShell 关联的进程，然后 `Enter-PSHostProcess` 使用 **id** 参数中指定的进程 ID 附加到进程，然后 `Get-Runspace` 列出 PowerShell 主机进程内的运行空间。

选择要调试的运行空间后，如果运行空间当前正在运行命令或脚本，或者脚本已在断点处停止，则 PowerShell 将为运行空间打开远程调试器会话。 可以采用与调试远程会话脚本相同的方式来调试运行空间脚本。

如果你是运行进程的计算机上的管理员，或者正在运行要调试的脚本，则只能附加到 PowerShell 主机进程。 此外，不能输入运行当前 PowerShell 会话的主机进程。 只能输入运行不同 PowerShell 会话的主机进程。

## 示例

### 示例1：调试远程运行空间

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

在此示例中，调试在远程计算机上打开的运行空间 WS10TestServer。 在该命令的第一行中，你在 `Get-Process` 远程计算机上运行，并筛选 Windows PowerShell 主机进程。 在此示例中，你想要调试进程 ID 1152，Windows PowerShell ISE 主机进程。

在第二个命令中，运行 `Enter-PSSession` 以打开 WS10TestServer 上的远程会话。 在第三个命令中，通过运行连接到在远程服务器上运行的 Windows PowerShell ISE 主机进程 `Enter-PSHostProcess` ，并指定在第一个命令1152中获取的主机进程的 ID。

在第四个命令中，可以通过运行来列出进程 ID 1152 的可用运行空间 `Get-Runspace` 。
记下繁忙运行空间的 ID 号;它正在运行您要调试的脚本。

在最后一个命令中，通过添加 Id 参数，开始调试正在运行脚本的打开的运行空间，TestWFVar1.ps1，通过运行 `Debug-Runspace` ，并按 id 2 标识运行空间。  由于脚本中存在断点，因此将打开调试器。

## PARAMETERS

### -Id

指定运行空间的 ID 号。 您可以运行 `Get-Runspace` 来显示运行空间 id。

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

按其实例 ID 指定运行空间，可通过运行显示该 GUID `Get-Runspace` 。

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

按名称指定运行空间。 您可以运行 `Get-Runspace` 来显示运行空间的名称。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -运行空间

指定运行空间对象。 为此参数提供值的最简单方法是指定包含筛选命令的结果的变量 `Get-Runspace` 。

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Default value: True
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
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -BreakAll

{{填充 BreakAll 说明}}

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.web. Management。

可以通过管道将命令结果传递 `Get-Runspace` 给 **调试-运行空间。**

## 输出

## 注释

`Debug-Runspace` 适用于处于打开状态的运行空间。 如果运行空间状态从 "已打开" 更改为其他状态，则将自动从正在运行的列表中删除该运行空间。 只有满足以下条件时，才能将运行空间添加到正在运行的列表。

- 如果它来自调用命令，则为;也就是说，它具有 `Invoke-Command` GUID ID。
- 如果它来自，则为 `Debug-Runspace` ，它具有 `Debug-Runspace` GUID ID。
- 如果它来自 PowerShell 工作流，并且其工作流作业 ID 与当前的活动调试器工作流作业 ID 相同，则为。

## 相关链接

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Debug-Job](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-Runspace](Get-Runspace.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Enter-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

