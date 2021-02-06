---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: b9fcd7b7be4dab6f4ccd0c2c1ccab1d27a332d57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597232"
---
# Register-CimIndicationEvent

## 摘要
使用筛选表达式或查询表达式订阅指示。

## SYNTAX

### ClassNameComputerSet (默认值) 

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Register-CimIndicationEvent`Cmdlet 使用指示类名称或查询表达式订阅指示。 使用 **SourceIdentifier** 参数为订阅指定名称。

此 cmdlet 将返回 **EventSubscription** 对象。 此对象可用于取消订阅。

## 示例

### 示例1：注册由类生成的事件

此示例订阅名为 **Win32_ProcessStartTrace** 的类生成的事件。 只要进程启动，此类就会引发一个事件。

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

`Get-Event`Cmdlet 将获取具有 **ProcessStarted** 订阅的事件。 有关详细信息，请参阅 [获取-事件](../Microsoft.PowerShell.Utility/Get-Event.md)。

> [!NOTE]
> 对于本示例，必须以管理员身份运行 PowerShell。

### 示例2：使用查询注册事件

此示例使用查询来订阅在名为 **Win32_LocalTime** 的类的实例中发生更改时生成的事件。

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### 示例3：在事件到达时运行脚本

此示例演示如何使用操作来响应事件。 变量 `$action` 保存用于 **操作** 的脚本块，该脚本块使用 `$event` 变量来访问从 CIM 收到的事件。

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

有关详细信息，请参阅 [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace)。

### 示例4：在远程计算机上注册事件

此示例订阅名为 **Server01** 的远程计算机上的事件。 从 CIM 服务器接收的事件存储在当前 PowerShell 会话中的事件队列中，然后运行本地 `Get-Event` 以检索事件。

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETERS

### -Action

指定用于处理事件的命令。 此参数指定的命令在引发事件时运行，而不是将事件发送到事件队列。 将命令括在大括号中， (`{}`) 创建脚本块。

通过 " **操作** " 指定的脚本块包括 `$Event` 、 `$EventSubscriber` 、 `$Sender` 、 `$SourceEventArgs` 和 `$SourceArgs` 自动变量，这些变量向 **操作** 脚本块提供有关事件的信息。 有关详细信息，请参阅 [关于自动变量](../microsoft.powershell.core/about/about_automatic_variables.md)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

使用指定的 CIM 会话运行该命令。 输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。 有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

指定您要订阅的指示类。 您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要在其上运行 CIM 操作的计算机的名称。 可以指定完全限定的域名 (FQDN) 、NetBIOS 名称或 IP 地址。

如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。 如果未指定此参数，则 cmdlet 将使用组件对象模型 (COM) 在本地系统上执行操作。

如果在同一台计算机上执行多个操作，请使用 CIM 会话进行连接以获得更好的性能。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

指示将订阅的事件转发到本地计算机上的会话。 如果要在远程计算机或远程会话中注册事件，可使用此参数。

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

### -MaxTriggerCount

一个参数，用于指示在指定的时间后应自动取消注册订阅服务器。 如果值等于或小于零，则不会对在未注册事件的情况下触发事件的次数没有限制。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

指定与此事件订阅关联的任何其他数据。 此参数的值出现在与此订阅关联的所有事件的 **MessageData** 属性中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定 CIM 操作的命名空间。 默认命名空间为 **root/cimv2**。 您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeoutSec

指定 cmdlet 等待计算机响应的时间量。 默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。

如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

指定要在 CIM 服务器上运行的查询。 如果指定的值包含双引号 `"` 、单引号 `'` 或反斜杠 `\` ，则必须通过在它们前面加上反斜杠字符来对这些字符进行转义。 如果指定的值使用 WQL LIKE 运算符，则必须通过将以下字符括在方括号中来对其进行转义 `[]` ：百分比 `%` 、下划线 `_` 或左方括号 `[` 。

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

指定用于 **查询** 参数的查询语言。 此参数的可接受值为： **WQL** 或 **CQL**。 默认值为 **WQL**。

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定订阅的名称。 指定的名称在当前会话中必须是唯一的。 默认值是 PowerShell 指定的 GUID。 此值出现在订阅者对象的 **SourceIdentifier** 属性值中，以及与此订阅关联的所有事件对象的值中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

指示事件订阅处于隐藏状态。 在当前订阅是更复杂的事件注册机制的一部分并且不应单独发现时，可使用此参数。

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

### 无

此 cmdlet 不接受输入对象。

## 输出

### System.Object

此 cmdlet 将输出一个 **EventSubscription** 对象。

## 注释

## 相关链接

[Get-Event](../microsoft.powershell.utility/get-event.md)

[Remove-Event](../microsoft.powershell.utility/remove-event.md)

[Unregister-Event](../microsoft.powershell.utility/unregister-event.md)

[Write-Host](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

