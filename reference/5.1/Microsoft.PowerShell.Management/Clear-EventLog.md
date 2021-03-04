---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685911"
---
# Clear-EventLog

## 摘要
清除本地或远程计算机上指定事件日志中的所有条目。

## SYNTAX

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 说明

`Clear-EventLog`Cmdlet 将删除本地计算机或远程计算机上指定事件日志中的所有条目。 若要使用 `Clear-EventLog` ，您必须是受影响计算机上 Administrators 组的成员。

 (EventLog cmdlet 包含 **eventlog** 名词的 cmdlet) 仅适用于经典事件日志。 若要从使用 windows Vista 和更高版本 Windows 中的 Windows 事件日志技术的日志中获取事件，请使用 Get-WinEvent cmdlet。

## 示例

### 示例1：从本地计算机中清除特定的事件日志类型

```powershell
Clear-EventLog "Windows PowerShell"
```

此命令从本地计算机上的 Windows PowerShell 事件日志中清除条目。

### 示例2：清除本地和远程计算机中的特定多个日志类型

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

此命令清除本地计算机和 Server02 远程计算机上 Microsoft Office 诊断 (ODiag) 和 Microsoft Office 会话 (OSession) 日志中的所有条目。

### 示例3：清除指定计算机上的所有日志，然后显示 "事件日志" 列表

```powershell
Clear-EventLog -LogName application, system -confirm
```

此命令将在删除指定事件日志中的条目之前提示你进行确认。

### 示例4：清除指定计算机上的所有日志，然后显示 "事件日志" 列表

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

此函数将清除指定计算机上的所有事件日志，然后显示生成的事件日志列表。

请注意，在清除系统和安全日志之后但在显示它们之前，向其中添加了几个条目。

## PARAMETERS

### -ComputerName

指定远程计算机。 默认为本地计算机。

键入远程计算机的 NetBIOS 名称、Internet 协议 (IP) 地址或完全限定的域名。 若要指定本地计算机，请键入该计算机名称、句点 (.) 或“localhost”。

此参数不依赖于 Windows PowerShell 远程处理。  `Get-EventLog` 即使你的计算机未配置为运行远程命令，你也可以使用 ComputerName 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LogName

指定事件日志。 输入日志名称 (**日志** 属性的值，而不是由逗号分隔的一个或多个事件日志的 **LogDisplayName**) 。 不允许使用通配符。 此参数是必需的。

> [!IMPORTANT]
> 此参数应按属性名称接受管道中的值。 但是，有一个 bug 阻止了此操作。 必须直接使用参数传递值。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

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

显示运行该 cmdlet 时会发生什么情况。
cmdlet 未运行。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### None

不能通过管道将对象传递给 `Clear-EventLog` 。

## 输出

### None

此 cmdlet 将不生成任何输出。

## 注释

- 若要 `Clear-EventLog` 在 Windows Vista 和更高版本的 windows 上使用，请使用 "以管理员身份运行" 选项启动 Windows PowerShell。

## 相关链接

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
