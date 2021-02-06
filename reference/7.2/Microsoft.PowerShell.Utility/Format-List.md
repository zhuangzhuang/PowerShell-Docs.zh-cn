---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603398"
---
# Format-List

## 摘要
将输出的格式设置为属性列表，其中每个属性都显示在一个新行上。

## SYNTAX

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## DESCRIPTION

`Format-List`Cmdlet 将命令输出的格式设置为属性列表，其中每个属性都显示在单独的行上。 您可以使用 `Format-List` 将对象的全部或所选属性的格式设置为列表 (格式列表 * ) 。

由于列表中的每个项都有更多可用空间，因此 PowerShell 将在列表中显示该对象的更多属性，并且属性值不太可能被截断。

## 示例

### 示例1：格式化计算机服务

```powershell
Get-Service | Format-List
```

此命令将计算机上服务的相关信息的格式设置为列表。 默认情况下，将这些服务的格式设置为表。 `Get-Service`Cmdlet 将获取表示计算机上的服务的对象。 管道运算符 (|) 通过管道将结果传递给 `Format-List` 。
然后，该 `Format-List` 命令将服务信息的格式设置为列表，并将其发送到默认的输出 cmdlet 以供显示。

### 示例2：格式化 TYPES.PS1XML 文件

这些命令以列表的形式显示有关 PowerShell 目录中的 TYPES.PS1XML 文件的信息。

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

第一个命令获取表示文件的对象，并将其存储在 `$A` 变量中。

第二个命令使用 `Format-List` 来设置有关存储在中的对象的信息的格式 `$A` 。 此命令使用 **InputObject** 参数将该变量传递给 `Format-List` ，后者随后会将格式化输出发送到默认的输出 cmdlet 以供显示。

### 示例3：按名称设置进程属性的格式

此命令将显示计算机上每个进程的名称、基本优先级和优先级类。

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

它使用 `Get-Process` cmdlet 来获取表示每个进程的对象。 管道运算符 (|) 将进程对象通过管道传递给 `Format-List` 。 `Format-List` 将进程的格式设置为指定属性的列表。 *属性* 参数名称是可选的，因此可以省略它。

### 示例4：设置进程的所有属性的格式

此命令显示 Winlogon 进程的所有属性。

```powershell
Get-Process winlogon | Format-List -Property *
```

它使用 Get-Process cmdlet 来获取表示 Winlogon 进程的对象。 管道运算符 (|) 通过管道将 Winlogon 进程对象传递给 `Format-List` 。 该命令使用 *Property* 参数来指定属性，并使用 \* 来指示所有属性。
因为 *属性* 参数的名称是可选的，所以可以省略它，然后将命令键入为 `Format-List *` 。 `Format-List` 自动将结果发送到默认的输出 cmdlet 以供显示。

### 示例5：排查格式错误

下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -DisplayError

指示此 cmdlet 在命令行中显示错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-List` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

### -Expand

指定格式化的集合对象以及集合中的对象。 此参数旨在用于设置支持 ICollection (System.Collections) 接口的对象的格式。 默认值为 EnumOnly。 此参数的可接受值为：

- EnumOnly. 显示集合中的对象的属性。
- CoreOnly. 显示集合对象的属性。
- 两者。 显示集合对象的属性以及集合中的对象的属性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示此 cmdlet 显示所有错误信息。 与 **DisplayError** 或 **ShowError** 参数一起使用。 默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。

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

### -GroupBy

基于共享属性或值指定组中的输出。 请输入表达式或输出的属性。

**GroupBy** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- 名称 (或标签) - `<string>`
- Expression `<string>` 或 `<script block>`
- 说明符 `<string>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要设置格式的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Property

指定要在屏幕上显示的对象属性及其显示顺序。
允许使用通配符。

如果省略此参数，则屏幕上显示的属性取决于要显示的对象。 参数名称 "Property" 是可选的。 不能在同一命令中使用 **Property** 和 **View** 参数。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- 名称 (或标签) - `<string>`
- Expression `<string>` 或 `<script block>`
- 说明符 `<string>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

指示 cmdlet 通过管道发送错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-List` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

### -View

指定替代列表格式或视图的名称。 不能在同一命令中使用 **Property** 和 **View** 参数。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Format-List` 。

## 输出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-List` 返回表示列表的格式对象。

## 注释

你还可以通过其内置别名 FL 来引用 Format-List。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

格式 cmdlet （例如 `Format-List` ）用于排列要显示的数据，但不显示。
数据由 PowerShell 的输出功能以及包含 out cmdlet (Out) （如或）的 cmdlet 显示 `Out-Host` `Out-File` 。

如果未使用格式 cmdlet，则 PowerShell 会将其显示的每个对象应用默认格式。

**GroupBy** 参数假定对象已排序。 使用 Sort-Object，然后使用 `Format-List` 将对象分组。

使用 **View** 参数可以指定表的替代格式。 你可以使用 PowerShell 目录的文件中定义的视图 `*.format.PS1XML` ，也可以在新的 types.ps1xml 文件中创建你自己的视图，并使用 Update-FormatData cmdlet 将它们包含在 powershell 中。

**View** 参数的替代视图必须使用列表格式，否则，该命令将失败。 如果替代视图是一个表，则使用 `Format-Table` 。 如果替代视图不是列表或表，请使用 `Format-Custom` 。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
