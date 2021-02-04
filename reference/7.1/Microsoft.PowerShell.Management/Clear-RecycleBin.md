---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 6ac35c698cc1b4f2571becdee48b1f73f21249e7
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098713"
---
# Clear-RecycleBin

## 摘要
清除回收站的内容。

## SYNTAX

### 全部

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Clear-RecycleBin`Cmdlet 删除计算机回收站的内容。 此操作类似于使用 Windows **空回收站**。

此 cmdlet 已在 PowerShell 7 中 readded。

## 示例

### 1：清除所有回收站

在此示例中，所有本地计算机的回收站都将被清除。

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`Clear-RecycleBin` 提示用户确认是否要清除本地计算机上的所有回收站。

### 2：清除指定的回收站

此示例将为指定驱动器号清除回收站。

```powershell
Clear-RecycleBin -DriveLetter C
```

`Clear-RecycleBin` 使用 **驱动器号** 参数在 **C** 卷上指定回收站。 系统将提示用户进行确认以运行该命令。

### 3：清除所有回收站而不进行确认

此示例不会提示确认是否要清除本地计算机的回收站。

```powershell
Clear-RecycleBin -Force
```

`Clear-RecycleBin` 使用 **Force** 参数，而不提示用户确认清除本地计算机上的所有回收站。

替代方法是将替换 `-Force` 为 `-Confirm:$false` 。

## PARAMETERS

### -驱动器号

指定为单个驱动器号或驱动器号数组清除的回收站。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

指定不提示用户确认是否要清除回收站。 **Force** 参数还会替代 **WhatIf** 和 **Confirm** 参数。

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

### -Confirm

在运行 cmdlet 之前提示用户进行确认。 即使未指定 **Confirm** 参数，也会提示用户进行确认。

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

显示运行时将发生 `Clear-RecycleBin` 的情况。 cmdlet 未运行。

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

## 输出

### 无

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接
