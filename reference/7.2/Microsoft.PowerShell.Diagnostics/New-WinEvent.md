---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 5b4b150a1c02e5d0689b44db9b2a984e297db766
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596037"
---
# New-WinEvent

## 摘要
为指定的事件提供程序创建一个新的 Windows 事件。

## SYNTAX

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## DESCRIPTION

**New-WinEvent** cmdlet 可为事件提供程序创建 Windows 事件跟踪 (ETW) 事件。
可以使用此 cmdlet 将事件从 PowerShell 添加到 ETW 通道。

## 示例

### 示例 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

此命令使用 **New-WinEvent** cmdlet 为 Microsoft-Windows-PowerShell 提供程序创建事件 45090。

## PARAMETERS

### -Id

指定通过检测清单注册的事件 ID。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Payload

指定事件的消息。 当事件写入事件日志后，负载将存储在事件对象的 **Message** 属性中。

当指定的负载与事件定义中的负载不匹配时，PowerShell 会生成一个警告，但命令仍会成功。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定将事件写入事件日志的事件提供程序，例如“Microsoft-Windows-PowerShell”。 ETW 事件提供程序是将事件写入 ETW 会话的逻辑实体。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

指定事件的版本号。 键入事件数。 PowerShell 将数字转换为所需的字节类型。

如果为同一事件定义了不同版本，则可以使用此参数指定事件。

```yaml
Type: System.Byte
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

此 cmdlet 不通过管道接受输入。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

* 在提供程序将甚至写入到 eventlog 后，可以使用 Get-WinEvent cmdlet 从事件日志中获取事件。

## 相关链接

[Get-WinEvent](Get-WinEvent.md)

