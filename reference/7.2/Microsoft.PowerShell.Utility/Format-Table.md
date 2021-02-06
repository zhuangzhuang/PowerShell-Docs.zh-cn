---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 2db0a8abe8fbd87b077e40655a06a1db45482ebc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595810"
---
# Format-Table

## 摘要
将输出的格式设置为一个表。

## SYNTAX

### 全部

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

该 `Format-Table` cmdlet 将命令输出的格式设置为表，其中每列中的对象的所选属性。 对象类型确定每列中显示的默认布局和属性。 您可以使用 **Property** 参数来选择要显示的属性。

PowerShell 使用默认格式化程序定义对象类型的显示方式。 您可以使用 `.ps1xml` 文件创建显示带有指定属性的输出表的自定义视图。 创建自定义视图后，请使用 **view** 参数显示具有您的自定义视图的表。 有关视图的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

您可以使用哈希表将计算属性添加到对象，然后再显示该对象并指定表中的列标题。 若要添加计算属性，请使用 **property** 或 **GroupBy** 参数。 有关哈希表的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

## 示例

### 示例1：格式化 PowerShell 主机

此示例在表中显示有关 PowerShell 主机程序的信息。

```powershell
Get-Host | Format-Table -AutoSize
```

该 `Get-Host` cmdlet 将获取表示该主机的 **system.management.automation.internal.host.internalhost** 对象，。 对象沿着管道向下发送 `Format-Table` ，并显示在表中。 **AutoSize** 参数调整列宽以尽可能减少截断。

### 示例2：按 BasePriority 设置进程的格式

在此示例中，进程显示在具有相同 **BasePriority** 属性的组中。

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

该 `Get-Process` cmdlet 将获取表示计算机上每个进程的对象，并将它们向下发送到 `Sort-Object` 。 对象按其 **BasePriority** 属性的顺序进行排序。

已排序对象将向下发送到 `Format-Table` 。 **GroupBy** 参数基于其 **BasePriority** 属性的值将流程数据排列成组。 **Wrap** 参数可确保数据不会被截断。

### 示例3：按开始日期设置进程的格式

此示例显示有关在计算机上运行的进程的信息。 对象经过排序，并 `Format-Table` 使用视图按其开始日期对对象进行分组。

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` 获取表示在计算机上运行的进程的 **system.object** 对象。 对象按管道向下发送到 `Sort-Object` ，并根据 **StartTime** 属性对其进行排序。

已排序对象将向下发送到 `Format-Table` 。 **View** 参数指定在 PowerShell  `DotNetTypes.format.ps1xml` 文件中为 **system.object** 对象定义的 StartTime View。 **StartTime** view 将每个进程的开始时间转换为短日期，然后按开始日期对进程进行分组。

此 `DotNetTypes.format.ps1xml` 文件包含进程的 **优先级** 视图。 您可以 `format.ps1xml` 通过自定义视图创建自己的文件。

### 示例4：为表输出使用自定义视图

在此示例中，自定义视图显示目录的内容。 自定义视图将 **CreationTime** 列添加到创建的 **DirectoryInfo** 和 **FileInfo** 对象的表输出中 `Get-ChildItem` 。

此示例中的自定义视图是从 PowerShell 源代码中定义的视图创建的。 有关用于创建此示例视图的视图和代码的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)。

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` 获取当前目录的内容 `C:\Test` 。 **DirectoryInfo** 和 **FileInfo** 对象将沿管道向下发送。
`Format-Table`使用 **View** 参数指定包含 **CreationTime** 列的自定义视图 **mygciview** 。

的默认 `Format-Table` 输出 `Get-ChildItem` 不包括 **CreationTime** 列。

### 示例5：使用表输出的属性

此示例使用 properties **参数在** 两个列表中显示计算机的所有服务，其中显示了 properties **Name** 和 **DependentServices**。

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` 获取计算机上的所有服务，并沿管道向下发送 **ServiceController** 对象。 `Format-Table` 使用 **Property** 参数来指定表中显示的 **Name** 和 **DependentServices** 属性。

**Name** 和 **DependentServices** 是对象类型的两个属性。 若要查看所有属性： `Get-Service | Get-Member -MemberType Properties` 。

### 示例6：设置进程的格式并计算其运行时间

此示例显示一个表，其中包含本地计算机的 **记事本** 进程的进程名称和总运行时间。 总运行时间是通过从当前时间减去每个进程的开始时间而计算出来的。

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` 获取所有本地计算机的 **记事本** 进程，并沿管道向下发送对象。 `Format-Table` 显示一个表，其中包含两个列： **ProcessName**、 `Get-Process` property 和 **TotalRunningTime**，是计算属性。

**TotalRunningTime** 属性由具有两个键（ **Label** 和 **Expression**）的哈希表指定。 **标签** 键指定属性名称。 **表达式** 键指定计算。 表达式获取每个进程对象的 **StartTime** 属性，并从命令的结果中减去该属性 `Get-Date` ，从而获取当前日期和时间。

### 示例7：格式化记事本进程

此示例使用 `Get-CimInstance` 来获取本地计算机上所有 **记事本** 进程的运行时间。 可以 `Get-CimInstance` 与 **ComputerName** 参数一起使用，以从远程计算机获取信息。

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance` 获取 WMI **Win32_Process** 类的实例，该类描述名为 **notepad.exe** 的所有本地计算机的进程。 进程对象存储在 `$Processes` 变量中。

变量中的进程对象 `$Processes` 将沿管道向下发送到 `Format-Table` ，这将显示 **ProcessName** 属性和新的计算属性（ **总运行时间**）。

该命令将新计算属性的名称（ **总运行时间**）分配给 **标签** 键。 **Expression** 键的脚本块将通过从当前日期中减去进程创建日期来计算进程的运行时间。 `Get-Date`Cmdlet 获取当前日期。 创建日期从当前日期中减去。 结果是 **总运行时间** 的值。

### 示例8：疑难解答格式错误

下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## PARAMETERS

### -AutoSize

指示该 cmdlet 基于数据的宽度来调整列的大小和列数。 默认情况下，列大小和数量由视图确定。

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

### -DisplayError

指示该 cmdlet 在命令行中显示错误。 当你在命令中设置表达式的格式 `Format-Table` 并需要对表达式进行故障排除时，可以将此参数用作调试帮助。

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

### -Expand

指定集合对象和集合中的对象的格式。 此参数旨在设置支持 [ICollection](/dotnet/api/system.collections.icollection) [ () ](/dotnet/api/system.collections) 接口的对象的格式。 默认值为 **EnumOnly**。
此参数可接受的值如下所示：

- **EnumOnly**：显示集合中的对象的属性。
- **CoreOnly**：显示集合对象的属性。
- **Both**：显示集合对象的属性和集合中对象的属性。

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

指示 cmdlet 指示 cmdlet 显示所有错误信息。 与 **DisplayError** 或 **ShowError** 参数一起使用。 默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。

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

### -GroupBy

基于属性值在单独的表中指定排序输出。 例如，您可以使用 **GroupBy** 根据其状态在单独的表中列出服务。

输入表达式或属性。 **GroupBy** 参数要求对对象进行排序。
使用 `Sort-Object` cmdlet 将 `Format-Table` 对象分组。

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

### -HideTableHeaders

省略表中的列标题。

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

指定要在屏幕上显示的对象属性及其显示顺序。 键入一个或多个属性名称（以逗号分隔），或使用哈希表显示计算属性。 允许使用通配符。

如果省略此参数，则显示在显示中的属性将取决于第一个对象的属性。 例如，如果第一个对象具有 **PropertyA** 和 **PropertyB** ，但后续对象具有 **PropertyA**、 **PropertyB** 和 **PropertyC**，则只会显示 **PropertyA** 和 **PropertyB** 标头。

**Property** 参数是可选的。 不能在同一命令中使用 **Property** 和 **View** 参数。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- 名称 (或标签) `<string>`
- Expression `<string>` 或 `<script block>`
- 说明符 `<string>`
- Width- `<int32>` -必须大于 `0`
- 对齐值可以是 `Left` 、 `Center` 或 `Right`

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

### -RepeatHeader

在每个屏幕满后重复显示表的标头。 当将输出通过管道传递给页导航（如或）或 `less` `more` 使用屏幕阅读器进行分页时，重复标头很有用。

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

### -ShowError

此参数通过管道发送错误。 当你在命令中设置表达式的格式 `Format-Table` 并需要对表达式进行故障排除时，可以将此参数用作调试帮助。

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

### -View

从 PowerShell 6 开始，默认视图是在 PowerShell 源代码中定义的 `C#` 。 Powershell `*.format.ps1xml` 6 及更高版本中不存在 powershell 5.1 及更早版本中的文件。

使用 **View** 参数可以指定表的替代格式或自定义视图。 可以使用默认的 PowerShell 视图或创建自定义视图。 有关如何创建自定义视图的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

**View** 参数的替代视图和自定义视图必须使用表格式，否则将 `Format-Table` 失败。 如果替代视图是一个列表，请使用 `Format-List` cmdlet。 如果替代视图不是列表或表，请使用 `Format-Custom` cmdlet。

不能在同一命令中使用 **Property** 和 **View** 参数。

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

### -换行

在下一行显示超过列宽的文本。 默认情况下，超过列宽的文本将被截断。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以将任何对象沿管道向下发送到 `Format-Table` 。

## 输出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Table` 返回表示表的格式对象。

## 注释

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Export-FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Get-Member](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Update-FormatData](Update-FormatData.md)
