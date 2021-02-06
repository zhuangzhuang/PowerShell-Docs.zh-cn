---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596011"
---
# Format-Custom

## 摘要
使用自定义的视图来设置输出格式。

## SYNTAX

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION

`Format-Custom`Cmdlet 将命令的输出格式设置为替代视图中的定义。
`Format-Custom` 旨在显示不只是表格或只是列表的视图。 你可以使用在 PowerShell 中定义的视图，也可以在新文件中创建你自己的视图， `format.ps1xml` 并使用 `Update-FormatData` cmdlet 将它们添加到 PowerShell。

## 示例

### 示例1：使用自定义视图设置输出格式

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

此命令使用 `Start-Transcript` MyView 视图（用户创建的自定义视图）定义的格式设置有关 cmdlet 的信息的格式。 若要成功运行此命令，必须首先创建一个新的 TYPES.PS1XML 文件，定义 **MyView** 视图，然后使用 `Update-FormatData` 命令将 types.ps1xml 文件添加到 PowerShell。

### 示例2：用默认视图设置输出格式

```powershell
Get-Process Winlogon | Format-Custom
```

此命令设置有关其他自定义视图中 **Winlogon** 进程的信息的格式。
由于该命令不使用 **View** 参数，因此将 `Format-Custom` 使用默认的自定义视图来设置数据的格式。

### 示例3：疑难解答格式错误

下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -Depth

指定显示中的列数。

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

### -DisplayError

在命令行中显示错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-Custom` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

设置集合对象以及集合中的对象的格式。 此参数旨在设置支持 **system.object** 接口的对象的格式。 默认值为 **EnumOnly**。

有效值是：

- EnumOnly：显示集合中的对象的属性。
- CoreOnly：显示集合对象的属性。
- Both：显示集合对象和集合中对象的属性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示 cmdlet 显示所有错误信息。 与 **DisplayError** 或 **ShowError** 参数一起使用。 默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。

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

基于共享属性或值设置组中输出的格式。 请输入表达式或输出的属性。

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

如果省略此参数，则屏幕上显示的属性取决于要显示的对象。 参数 name **属性** 是可选的。 不能在同一命令中使用 **Property** 和 **View** 参数。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- Expression `<string>` 或 `<script block>`
- 长度 `<int32>`

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

通过管道发送错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-Custom` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

指定替代格式或视图的名称。 如果省略此参数，则 `Format-Custom` 使用默认的自定义视图。 不能在同一命令中使用 **Property** 和 **View** 参数。

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

可以通过管道将任何对象传递给 `Format-Custom` 。

## 输出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Custom` 返回表示显示的格式对象。

## 注释

`Format-Custom` 旨在显示不只是表格或只是列表的视图。 若要显示替代表视图，请使用 `Format-Table` 。 若要显示替代列表视图，请使用 `Format-List` 。

还可以 `Format-Custom` 通过其内置别名来引用 `fc` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

**GroupBy** 参数假定对象已排序。 使用对 `Format-Custom` 对象进行分组之前，请使用对 `Sort-Object` 它们进行排序。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
