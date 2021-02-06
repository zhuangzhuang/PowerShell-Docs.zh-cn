---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: d2c0abb0e6742de3e316fe964d5945375591ef4d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598459"
---
# Add-History

## 摘要
向会话历史记录附加条目。

## SYNTAX

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## DESCRIPTION

`Add-History`Cmdlet 将条目添加到会话历史记录的末尾，即在当前会话期间输入的命令的列表。

会话历史记录是在会话期间输入的命令的列表。 会话历史记录表示命令的执行顺序、状态以及开始和结束时间。 当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。 有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。

会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。
在加载 **PSReadLine** 的会话中提供两个历史记录。 此 cmdlet 仅适用于会话历史记录。 有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

你可以使用 `Get-History` cmdlet 来获取命令并将其传递到 `Add-History` ，也可以将命令导出到 CSV 或 XML 文件，然后导入命令，然后将导入的文件传递给 `Add-History` 。 可以使用此 cmdlet 向历史记录添加特定命令，或创建单个历史记录文件以保存来自多个会话的命令。

## 示例

### 示例1：向其他会话的历史记录添加命令

此示例将在一个 PowerShell 会话中键入的命令添加到不同 PowerShell 会话的历史记录中。

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

第一个命令获取表示历史记录中的命令的对象，并将其导出到 `History.csv` 文件。

第二个命令是在另一个会话的命令行中键入的。 它使用 `Import-Csv` cmdlet 导入文件中的对象 `History.csv` 。 管道运算符 (`|`) 将对象传递给 `Add-History` cmdlet，后者将表示文件中的命令的对象添加 `History.csv` 到当前会话历史记录。

### 示例2：导入和运行命令

此示例从文件导入命令 `History.xml` ，将这些命令添加到当前会话历史记录，然后在合并的历史记录中运行命令。

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

第一个命令使用 `Import-Clixml` cmdlet 导入已导出到文件中的命令历史记录 `History.xml` 。 管道运算符将命令传递给 `Add-History` cmdlet，这会将命令添加到当前会话历史记录。 **PassThru** 参数将表示所添加命令的对象沿管道向下传递。

然后，该命令使用 `ForEach-Object` cmdlet 将命令应用于 `Invoke-History` 合并的历史记录中的每个命令。 该 `Invoke-History` 命令的格式为脚本块，括在大括号中 (`{}`) ，这是 Cmdlet 的 **Process** 参数所要求的 `ForEach-Object` 。

### 示例3：在历史记录中将命令添加到历史记录的末尾

此示例将历史记录中前五个命令添加到历史记录列表的末尾。

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

该 `Get-History` cmdlet 将获取以命令5结尾的五个命令。 管道运算符将其传递给 `Add-History` cmdlet，后者将它们追加到当前历史记录中。 此 `Add-History` 命令不包括任何参数，但 PowerShell 将通过管道传递的对象与的 **InputObject** 参数相关联 `Add-History` 。

### 示例4：将 .csv 文件中的命令添加到当前历史记录

此示例将文件中的命令添加 `History.csv` 到当前会话历史记录。

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

`Import-Csv`Cmdlet 将导入文件中的命令 `History.csv` ，并将其内容存储在变量中 `$a` 。

第二个命令使用 `Add-History` cmdlet 将中的命令添加 `History.csv` 到当前会话历史记录。 它使用 **InputObject** 参数来指定 `$a` 变量，使用 **PassThru** 参数来生成要在命令行中显示的对象。 如果没有 **PassThru** 参数，该 `Add-History` cmdlet 不会生成任何输出。

### 示例5：将 .xml 文件中的命令添加到当前历史记录

此示例将文件中的命令添加 `history.xml` 到当前会话历史记录。

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

**InputObject** 参数将括号中命令的结果传递给 `Add-History` cmdlet。 首先执行括号中的命令，将文件导入 `history.xml` PowerShell。 然后，该 `Add-History` cmdlet 会将该文件中的命令添加到会话历史记录。

## PARAMETERS

### -InputObject

指定一个条目数组，以将其作为 **HistoryInfo** 对象添加到会话历史记录。
你可以使用此参数将 **HistoryInfo** 对象（例如，、或 cmdlet 返回的对象）提交 `Get-History` `Import-Clixml` `Import-Csv` 到 `Add-History` 。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Passthru

指示此 cmdlet 为每个历史记录条目返回一个 **HistoryInfo** 对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### Microsoft.PowerShell.Commands.HistoryInfo

可以通过管道将 **HistoryInfo** 对象传递给此 cmdlet。

## 输出

### 无或 Microsoft.PowerShell.Commands.HistoryInfo

如果指定 **PassThru** 参数，则此 cmdlet 将返回 **HistoryInfo** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

会话历史记录是在会话期间与 ID 一起输入的命令的列表。 会话历史记录表示命令的执行顺序、状态以及开始和结束时间。 当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。 有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。

若要指定要添加到历史记录中的命令，请使用 **InputObject** 参数。 `Add-History`命令只接受 **HistoryInfo** 对象，例如由 cmdlet 为每个命令返回的对象 `Get-History` 。 不能向其传递路径和文件名，也不能传递命令列表。

可以使用 **InputObject** 参数将 **HistoryInfo** 对象的文件传递给 `Add-History` 。 为此，请 `Get-History` 使用或 cmdlet 将命令的结果导出到文件， `Export-Csv` `Export-Clixml` 然后使用或 cmdlet 导入文件 `Import-Csv` `Import-Clixml` 。 然后，可以 `Add-History` 通过管道或变量将导入的 HistoryInfo 对象的文件传递给。 有关详细信息，请参阅示例。

传递给 cmdlet 的 **HistoryInfo** 对象的文件 `Add-History` 必须包含类型信息、列标题和 **HistoryInfo** 对象的所有属性。 如果打算将对象传递回 `Add-History` ，请不要使用 cmdlet 的 **NoTypeInformation** 参数，也不要 `Export-Csv` 删除文件中的类型信息、列标题或任何字段。

若要修改会话历史记录，请将会话导出到 CSV 或 XML 文件，修改文件，导入文件，然后使用 `Add-History` 将其追加到当前会话历史记录。

## 相关链接

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)

