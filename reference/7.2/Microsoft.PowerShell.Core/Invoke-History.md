---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596645"
---
# Invoke-History

## 摘要
从会话历史记录中运行命令。

## SYNTAX

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-History`Cmdlet 从会话历史记录中运行命令。 您可以将表示命令的对象从 Get-History 传递到 `Invoke-History` ，也可以通过使用其 **Id** 号来标识当前历史记录中的命令。 若要查找命令的标识号，请使用 `Get-History` cmdlet。

会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。
在加载 **PSReadLine** 的会话中提供两个历史记录。 此 cmdlet 仅适用于会话历史记录。 有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 示例

### 示例1：运行历史记录中的最新命令

此示例在会话历史记录中运行最后一个或最新的命令。 可以将此命令缩写为 `r` 的别名 `Invoke-History` 。

```powershell
Invoke-History
```

### 示例2：运行具有指定 ID 的命令

此示例在 **Id** 为132的会话历史记录中运行命令。 由于 **Id** 参数的名称是可选的，因此可以将此命令缩写为： `Invoke-History 132` 、 `ihy 132` 或 `r 132` 。

```powershell
Invoke-History -Id 132
```

### 示例3：使用命令文本运行最新命令

此示例运行 `Get-Process` 会话历史记录中的最新命令。 键入 **Id** 参数的字符时， `Invoke-History` 会从最新命令开始，运行它发现的与该模式匹配的第一个命令。

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> 模式匹配不区分大小写，但模式与行的开头匹配。

### 示例4：从历史记录中运行命令序列

此示例运行命令16至24。 由于只能列出一个 **id** 值，因此该命令将使用 `ForEach-Object` cmdlet 对 `Invoke-History` 每个 **id** 值运行一次此命令。

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### 示例 5

此示例运行历史记录中以命令 255 (249 到 255) 结束的七个命令。 它使用 `Get-History` cmdlet 检索命令。 由于只能列出一个 **id** 值，因此该命令将使用 `ForEach-Object` cmdlet 对 `Invoke-History` 每个 **id** 值运行一次命令。

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETERS

### -Id

指定历史记录中命令的 **Id** 。 你可以键入命令的 **Id** 号或命令的前几个字符。

如果键入字符，则 `Invoke-History` 先匹配最新的命令。 如果省略此参数，则 `Invoke-History` 运行最后一个或最新的命令。 若要查找命令的 **Id** 号，请使用 `Get-History` cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
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

### System.String

可以通过管道将历史记录 **Id** 传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不会生成任何输出，但输出可能由运行的命令生成 `Invoke-History` 。

## 注释

会话历史记录是在会话期间输入的命令的列表。 会话历史记录表示命令的执行顺序、状态以及开始和结束时间。 当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。 有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。

还可以 `Invoke-History` 通过其内置别名（和）来引用 `r` `ihy` 。 有关详细信息，请参阅 [about_Aliases](About/about_Aliases.md)。

## 相关链接

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)

