---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 0e531b3cc072b7cc1efe0ef06fb741326bf3a72b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595611"
---
# Get-CimSession

## 摘要
获取当前会话中的 CIM 会话对象。

## SYNTAX

### ComputerNameSet（默认值）

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### NameSet

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## DESCRIPTION

默认情况下，该 cmdlet 将获取在当前 PowerShell 会话中创建的所有 CIM 会话。 你可以使用的参数 `Get-CimSession` 获取特定计算机的会话，也可以通过其名称或其他标识符来识别会话。 `Get-CimSession` 不会获取在其他 PowerShell 会话中创建的或在其他计算机上创建的 CIM 会话。

有关 CIM 会话的详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

## 示例

### 示例1：从当前 PowerShell 会话获取 CIM 会话

此示例使用 [CimSession](New-CimSession.md)创建 cim 会话，然后使用获取 cim 会话 `Get-CimSession` 。

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 示例2：获取特定计算机的 CIM 会话

此示例将获取连接到名为 **Server02** 的计算机的 CIM 会话。

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 示例3：获取 CIM 会话列表，然后设置该列表的格式

此示例获取当前 PowerShell 会话中的所有 CIM 会话，并显示仅包含 **ComputerName** 和 **InstanceID** 属性的表。

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### 示例4：获取具有特定名称的所有 CIM 会话

此示例获取名称以 **serv** 开头的所有 CIM 会话。

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 示例5：获取特定 CIM 会话

此示例将获取 **Id** 为2的 CIM 会话。

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETERS

### -ComputerName

指定计算机的名称以获取连接到的 CIM 会话。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

指定要获取的 CIM 会话的标识符。 对于多个 Id，请使用逗号分隔 Id 或使用范围运算符 (`..`) 来指定 id 的范围。 **Id** 是一个整数，用于在当前 PowerShell 会话中唯一标识 CIM 会话。

有关范围运算符的详细信息，请参阅 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定要获取的 CIM 会话的实例 Id。

**InstanceId** 是唯一标识 CIM 会话 (GUID) 的全局唯一标识符。 即使在 PowerShell 中运行多个会话， **InstanceId** 也是唯一的。

**Instanceid** 存储在表示 CIM 会话的对象的 **InstanceId** 属性中。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

获取一个或多个包含指定友好名称的 CIM 会话。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

## 输出

### Microsoft.Management.Infrastructure.CimSession

## 注释

## 相关链接

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

