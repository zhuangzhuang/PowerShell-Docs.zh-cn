---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: d20a348f3f5ba193eb85e0f9d0e2cc11ad083b47
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595832"
---
# Remove-PSDrive

## 摘要
删除临时 PowerShell 驱动器并断开映射的网络驱动器的连接。

## SYNTAX

### Name（默认值）

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralName

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-PSDrive`Cmdlet 删除使用 cmdlet 创建的临时 PowerShell 驱动器 `New-PSDrive` 。

从 Windows PowerShell 3.0 开始， `Remove-PSDrive` 还会断开映射的网络驱动器（包括但不限于）使用的参数创建的驱动器 `Persist` `New-PSDrive` 。

`Remove-PSDrive` 无法删除 Windows 物理或逻辑驱动器。

从 Windows PowerShell 3.0 开始，当外部驱动器连接到计算机时，PowerShell 会自动将 New-psdrive 添加到代表新驱动器的文件系统中。
不需要重新启动 PowerShell。
同样，当外部驱动器与计算机断开连接时，PowerShell 会自动删除表示已删除驱动器的 New-psdrive。

## 示例

### 示例 1：删除文件系统驱动器

此命令删除一个名为“smp”的临时文件系统驱动器。

```powershell
Remove-PSDrive -Name smp
```

### 示例 2：删除映射的网络驱动器

此命令使用 `Remove-PSDrive` 断开 X：和 S：映射网络驱动器的连接。

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETERS

### -Force

删除当前 PowerShell 驱动器。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralName

指定驱动器的名称。

**LiteralName** 的值严格按照所键入的形式使用。
不会将任何字符解释为通配符。
如果名称包括转义符，请将其括在单引号 (') 中。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要删除的驱动器的名称。
请不要在驱动器名称后面键入冒号 (:)。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

指定 **PSProvider** 对象的数组。
此 cmdlet 将删除与指定的 PowerShell 提供程序关联的所有驱动器并断开连接。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定驱动器的作用域。
此参数的可接受值为： Global、Local、Script 或相对于当前作用域的数字。 范围号0到范围数。 当前作用域编号为0，其父级为1。
有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
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
此 cmdlet 未运行。

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

### System.Management.Automation.PSDriveInfo

可以通过管道将驱动器对象（例如 `Get-PSDrive` cmdlet）传递给 `Remove-PSDrive` cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

- `Remove-PSDrive`Cmdlet 设计用于处理由任何 PowerShell 提供程序公开的数据。 若要列出会话中的提供程序，请使用 `Get-PSProvider` cmdlet。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

