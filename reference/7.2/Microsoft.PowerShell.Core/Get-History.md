---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596216"
---
# Get-History

## 摘要
获取在当前会话过程中输入的命令列表。

## SYNTAX

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-History` cmdlet 将获取会话历史记录，即在当前会话期间输入的命令的列表。

PowerShell 会自动维护每个会话的历史记录。 会话历史记录中的条目数由 `$MaximumHistoryCount` 首选项变量的值确定。 从 Windows PowerShell 3.0 开始，默认值为 `4096` 。 默认情况下，历史记录文件保存在主目录中，但你可以将该文件保存在任何位置。 有关 PowerShell 中的历史记录功能的详细信息，请参阅 [about_History](About/about_History.md)。

会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。
在加载 **PSReadLine** 的会话中提供两个历史记录。 此 cmdlet 仅适用于会话历史记录。 有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 示例

### 示例 1：获取会话历史记录

此示例将获取会话历史记录中的条目。 将默认显示每个命令及其 ID，指示其运行顺序。

```powershell
Get-History
```

### 示例 2：获取包含字符串的条目

此示例将获取命令历史记录中包含字符串服务的条目。 第一个命令获取会话历史记录中的所有条目。 管道运算符 (`|`) 将结果传递给 `Where-Object` cmdlet，后者只选择包含服务的命令。

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### 示例3：导出特定 ID 的历史记录条目

此示例获取以条目7结尾的五个最新历史记录条目。 管道运算符将结果传递给 `Export-Csv` cmdlet，这会将历史记录的格式设置为以逗号分隔的文本，并将其保存在 History.csv 文件中。 该文件包括将历史记录的格式设置为列表时显示的数据。 这包括该命令的状态以及开始和结束时间。

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### 示例 4：显示最新的命令

此示例获取命令历史记录中的最后一个命令。 最后一个命令是最新输入的命令。 此命令使用 Count 参数以仅显示一个命令。 默认情况下， `Get-History` 获取最新命令。 此命令可缩写为“h -c 1”，等效于按向上箭头键。

```powershell
Get-History -Count 1
```

### 示例 5：显示历史记录中的条目的所有属性

此示例显示会话历史记录中条目的所有属性。 管道运算符将命令的结果传递 `Get-History` 给 `Format-List` cmdlet，后者将显示每个历史记录条目的所有属性。 这包括该命令的 ID、状态以及开始和结束时间。

```powershell
Get-History | Format-List -Property *
```

## PARAMETERS

### -Count

指定此 cmdlet 获取的最新历史记录条目数。 默认情况下， `Get-History` 将获取会话历史记录中的所有条目。 如果在命令中同时使用 **Count** 和 **Id** 参数，显示结果将以 **Id** 参数指定的命令结尾。

默认情况下，在 Windows PowerShell 2.0 中， `Get-History` 获取最新的32项。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定会话历史记录中的条目的 ID 数组。 `Get-History` 仅获取指定的项。 如果在命令中同时使用 **Id** 和 **Count** 参数，则将 `Get-History` 获取以 **id** 参数指定的条目结尾的最新条目。

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Int64

可以通过管道将历史记录 ID 传递给此 cmdlet。

## 输出

### Microsoft.PowerShell.Commands.HistoryInfo

此 cmdlet 将返回它所获取的每个历史记录项的历史记录对象。

## 注释

会话历史记录是在会话期间输入的命令的列表。 会话历史记录表示命令的运行顺序、状态以及开始和结束时间。 当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。 有关命令历史记录的详细信息，请参阅 [about_History](About/about_History.md)。

从 Windows PowerShell 3.0 开始， `$MaximumHistoryCount` 首选项变量的默认值为 `4096` 。 在 Windows PowerShell 2.0 中，默认值为 `64` 。 有关变量的详细信息 `$MaximumHistoryCount` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

## 相关链接

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Invoke-History](Invoke-History.md)

[about_History](About/about_History.md)
