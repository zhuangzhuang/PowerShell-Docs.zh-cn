---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: ba61c2d24d85256c55a7409fc368de4407aad5a9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598865"
---
# Format-Wide

## 摘要
将对象格式设置为宽表，此表仅显示每个对象的一个属性。

## SYNTAX

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## DESCRIPTION

该 `Format-Wide` cmdlet 将对象格式设置为宽表，只显示每个对象的一个属性。 您可以使用 **property** 参数来确定显示哪个属性。

## 示例

### 示例1：格式化当前目录中文件的名称

此命令将在屏幕上的三个列中显示当前目录中的文件的名称。

```powershell
Get-ChildItem | Format-Wide -Column 3
```

Get-ChildItem cmdlet 将获取表示目录中的每个对象的对象。 管道运算符 (|) 将文件对象通过管道传递到 `Format-Wide` ，这会将它们格式化为输出。 **Column** 参数指定列数。

### 示例2：格式化注册表项的名称

此命令显示 HKEY_CURRENT_USER\Software\Microsoft 项中的注册表项的名称。

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

Get-ChildItem cmdlet 将获取表示这些注册表项的对象。 路径指定为 HKCU：、PowerShell 注册表提供程序公开的驱动器之一，后跟密钥路径。 管道运算符 (|) 通过管道将注册表项对象传递到 `Format-Wide` ，后者将它们格式化为输出。 **Property** 参数指定属性的名称，而 **AutoSize** 参数调整列以提高可读性。

### 示例3：疑难解答格式错误

下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

基于数据的宽度来调整列的大小和数量。 默认情况下，列大小和数量由视图确定。 不能在同一命令中使用 **AutoSize** 和 **Column** 参数。

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

### -Column

指定显示中的列数。 不能在同一命令中使用 **AutoSize** 和 **Column** 参数。

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

在命令行中显示错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-Wide` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

设置集合对象以及集合中的对象的格式。 此参数旨在用于设置支持 ICollection (System.Collections) 接口的对象的格式。 默认值为 **EnumOnly**。

有效值是：

- EnumOnly：显示集合中的对象的属性。
- CoreOnly：显示集合对象的属性。
- Both：显示集合对象的属性以及集合中的对象的属性。

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

指示此 cmdlet 将覆盖阻止命令成功的限制，因此更改不会危及安全性。 例如，**Force** 将覆盖只读属性或创建目录来完成文件路径，但它不会尝试更改文件权限。

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

如果省略此参数，则屏幕上显示的属性取决于要显示的对象。 参数名称 "Property" 是可选的。 不能在同一命令中使用 **Property** 和 **View** 参数。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- Expression `<string>` 或 `<script block>`
- 说明符 `<string>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

通过管道发送错误。 此参数很少使用，但当你在命令中设置表达式的格式 `Format-Wide` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。

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

指定替代表格式或视图的名称。 不能在同一命令中使用 **Property** 和 **View** 参数。

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

可以通过管道将任何对象传递给 `Format-Wide` 。

## 输出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Wide` 返回表示表的格式对象。

## 注释

还可以 `Format-Wide` 通过其内置别名来引用 `fw` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

**GroupBy** 参数假定对象已排序。 使用 `Sort-Object` `Format-Custom` 来对对象进行分组之前，请使用。

使用 **View** 参数可以指定表的替代格式。 你可以使用 PowerShell 目录的文件中定义的视图 `*.format.PS1XML` ，也可以在新的 types.ps1xml 文件中创建自己的视图，并使用 `Update-FormatData` cmdlet 将它们包含在 powershell 中。

**View** 参数的替代视图必须使用表格式;否则，该命令将失败。 如果替代视图是一个列表，请使用 `Format-List` 。 如果替代视图既不是列表也不是表格，请使用 Format-Custom。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)
