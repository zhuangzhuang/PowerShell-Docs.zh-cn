---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603579"
---
# Remove-CimSession

## 摘要
删除一个或多个 CIM 会话。

## SYNTAX

### CimSessionSet (默认值) 

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameSet

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-CimSession`Cmdlet 从本地 PowerShell 会话中删除一个或多个 CIM 会话对象。

## 示例

### 示例1：删除所有 CIM 会话

此示例使用 [CimSession](Get-CimSession.md) cmdlet 检索本地计算机上的所有可用 CIM 会话，并使用将其删除 `Remove-CimSession` 。

```powershell
Get-CimSession | Remove-CimSession
```

### 示例2：删除特定 CIM 会话

此示例将删除 **Id** 值为5的 CIM 会话。

```powershell
Remove-CimSession -Id 5
```

### 示例3：使用 WhatIf 参数显示要删除的 CIM 会话的列表

此示例使用常见的参数 **WhatIf** 来指定不应执行删除操作，但仅输出完成后会发生的情况。

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETERS

### -CimSession

指定要关闭的 CIM 会话的会话对象。

输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 [`New-CimSession`](New-CimSession.md) 或 [`Get-CimSession`](Get-CimSession.md) cmdlet）。
有关详细信息，请参阅 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

指定计算机的名称数组。 删除连接到指定计算机的会话。 可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

指定要删除的 CIM 会话的 ID。 指定一个或多个 Id （以逗号分隔），或使用范围运算符 (`..`) 来指定 id 的范围。 **Id** 是一个整数，用于在当前 PowerShell 会话中唯一标识 CIM 会话。

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

指定要删除的 CIM 会话的实例 ID。 **InstanceId** 是唯一标识 CIM 会话 (GUID) 的全局唯一标识符。 即使在 PowerShell 中运行多个会话， **InstanceId** 也是唯一的。

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

指定要删除的 CIM 会话的友好名称。 可以将通配符用于此参数。

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

### 无

此 cmdlet 不接受输入对象。

## 输出

### System.Object

此 cmdlet 将返回包含 CIM 会话信息的对象。

## 注释

## 相关链接

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

