---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 051f02b00144805569d5130686a51a0f42b64b00
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584627"
---
# Write-EventLog

## 摘要
将事件写入事件日志。

## SYNTAX

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Write-EventLog`Cmdlet 将事件写入事件日志。

若要将事件写入事件日志，则计算机上必须存在该事件日志，并且必须为该事件日志注册来源。

 (**eventlog** Cmdlet 包含 **eventlog** 名词的 cmdlet) 仅适用于经典事件日志。 若要从使用 windows Vista 和更高版本的 windows 操作系统中的 Windows 事件日志技术的日志中获取事件，请使用 `Get-WinEvent` cmdlet。

## 示例

### 示例1：向应用程序事件日志写入事件

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

此命令将一个事件从 MyApp 源写入应用程序事件日志。

### 示例2：向远程计算机的应用程序事件日志写入事件

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

此命令将一个事件从 MyApp 源写入远程计算机 Server01 上的应用程序事件日志。

## PARAMETERS

### -Category

指定事件的任务类别。 请输入一个与事件日志的类别消息文件中的字符串相关联的整数。

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定远程计算机。 默认为本地计算机。

键入远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。

此参数不依赖于 Windows PowerShell 远程处理。  `Get-EventLog` 即使你的计算机未配置为运行远程命令，你也可以使用该 cmdlet 的 ComputerName 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EntryType

指定事件的条目类型。 此参数可接受的值包括： Error、Warning、Information、SuccessAudit 和 FailureAudit。 默认值为 Information。

有关值的说明，请参阅 [System.diagnostics.eventlogentrytype 枚举](/dotnet/api/system.diagnostics.eventlogentrytype)。

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventId

指定事件标识符。 此参数是必需的。 **EventId** 参数的最大值为65535。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

指定要向其中写入事件的日志的名称。 输入日志名称。 日志名称是 **log** 属性的值，而不是 **LogDisplayName**。 不允许使用通配符。
此参数是必需的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

指定事件消息。 此参数是必需的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData

指定与事件关联的二进制数据，以字节为单位。

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定事件来源，这通常是将事件写入日志的应用程序的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Diagnostics.EventLogEntry

此 cmdlet 将返回表示日志中的事件的对象。

## 注释

对于某些 Windows 事件日志，写入事件需要管理员权限。 你必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。

## 相关链接

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
