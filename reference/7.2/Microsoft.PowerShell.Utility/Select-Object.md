---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 80882d27c9c8fa2d7f9e1c8ca00a02cf73ae94e6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597651"
---
# Select-Object

## 摘要
选择对象或对象属性。

## SYNTAX

### DefaultParameter (默认值) 

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### SkipIndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## DESCRIPTION

`Select-Object`Cmdlet 可选择对象或对象集的指定属性。 它还可以从数组中选择唯一对象、指定数目的对象或指定位置中的对象。

若要从集合中选择对象，请使用 **First**、**Last**、**Unique**、**Skip** 和 **Index** 参数。 若要选择对象属性，请使用 **Property** 参数。 选择 "属性" 时， `Select-Object` 将返回只具有指定属性的新对象。

从 Windows PowerShell 3.0 开始， `Select-Object` 包含一项优化功能，可防止命令创建和处理未使用的对象。

如果在 `Select-Object` 命令管道中包含带有 **第一个** 或 **索引** 参数的命令，则在生成所选数目的对象之后，PowerShell 将停止生成对象，即使生成对象的命令出现在 `Select-Object` 管道中的命令之前。 若要禁用此优化行为，请使用 **Wait** 参数。

## 示例

### 示例1：按属性选择对象

此示例将创建具有进程对象的 **Name**、 **ID** 和工作集 (**WS**) 属性的对象。

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### 示例2：按属性选择对象并设置结果格式

此示例将获取有关计算机上的进程所使用的模块的信息。 它使用 `Get-Process` cmdlet 来获取计算机上的进程。

它使用 `Select-Object` cmdlet 输出实例的数组， `[System.Diagnostics.ProcessModule]` 该数组包含在每个实例输出的 **模块** 属性中 `System.Diagnostics.Process` `Get-Process` 。

Cmdlet 的 **Property** 参数 `Select-Object` 选择进程名称。 这会将 `ProcessName` **NoteProperty** 添加到每个 `[System.Diagnostics.ProcessModule]` 实例中，并用当前进程的 **ProcessName** 属性的值填充该实例。

最后， `Format-List` 使用 cmdlet 在列表中显示每个进程的名称和模块。

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### 示例3：选择使用最多内存的进程

此示例获取使用最多内存的五个进程。 `Get-Process`Cmdlet 将获取计算机上的进程。 该 `Sort-Object` cmdlet 根据内存 (工作集) 使用情况对进程进行排序，并且该 `Select-Object` cmdlet 仅选择生成的对象数组的最后五个成员。

包含 cmdlet 的命令中不需要 **Wait** 参数， `Sort-Object` 因为 `Sort-Object` 处理所有对象，然后返回集合。 `Select-Object`优化仅可用于在处理对象时单独返回对象的命令。

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### 示例4：选择数组中的唯一字符

此示例使用的 **唯一** 参数 `Select-Object` 从字符数组中获取唯一字符。

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### 示例5：选择事件日志中的最新和最旧的事件

此示例获取 Windows PowerShell 事件日志中的第一个 (最新) 和最后一个 (最早的) 事件。

`Get-EventLog` 获取 Windows PowerShell 日志中的所有事件，并将其保存在 `$a` 变量中。
然后， `$a` 将管道传递给 `Select-Object` cmdlet。 该 `Select-Object` 命令使用 **Index** 参数从变量中的事件数组中选择事件 `$a` 。 第一个事件的索引为 0。 最后一个事件的索引为减1中的项数 `$a` 。

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### 示例6：选择除第一个对象之外的所有对象

此示例在 Servers.txt 文件中列出的每台计算机上创建新的 PSSession，第一台计算机除外。

`Select-Object` 选择计算机名称列表中除第一台计算机之外的所有计算机。 生成的计算机列表被设置为该 cmdlet 的 **ComputerName** 参数的值 `New-PSSession` 。

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### 示例7：重命名文件并选择多个进行审阅

此示例将 "-ro" 后缀添加到具有只读属性的文本文件的基名称中，然后显示前五个文件，以便用户可以看到该效果的示例。

`Get-ChildItem` 使用 **ReadOnly** 动态参数获取只读文件。 生成的文件将通过管道传输到 `Rename-Item` cmdlet，这会重命名该文件。 它使用的 **Passthru** 参数将 `Rename-Item` 重命名的文件发送到 `Select-Object` cmdlet，后者将选择前5个进行显示。

的 **Wait** 参数 `Select-Object` 可防止 PowerShell 在 `Get-ChildItem` 获取前五个只读文本文件后停止该 cmdlet。 如果不使用此参数，则只有前五个只读文件会被重命名。

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### 示例8：演示-ExpandProperty 参数的复杂性

此示例演示了 **ExpandProperty** 参数的复杂性。

请注意，生成的输出是实例的数组 `[System.Int32]` 。 实例符合 **输出视图** 的标准格式设置规则。 对于 *扩展* 的属性，这是正确的。 如果输出对象具有特定的标准格式，则扩展属性可能不可见。

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### 示例9：在对象上创建自定义属性

下面的示例演示如何使用 `Select-Object` 将自定义属性添加到任何对象。
如果指定不存在的属性名称，则会 `Select-Object` 在传递的每个对象上将该属性创建为 **NoteProperty** 。

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### 示例10：为每个 InputObject 创建计算属性

此示例演示如何使用向 `Select-Object` 输入添加计算属性。 将 **ScriptBlock** 传递给 **属性** 参数会导致 `Select-Object` 计算每个传递对象的表达式，并将结果添加到输出。 在 **ScriptBlock** 内，可以使用 `$_` 变量来引用管道中的当前对象。

默认情况下， `Select-Object` 将使用 **ScriptBlock** 字符串作为属性的名称。 使用 **哈希表**，你可以将 **ScriptBlock** 的输出标记为添加到每个对象的自定义属性。 您可以向传递到的每个对象添加多个计算属性 `Select-Object` 。

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETERS

### -ExcludeProperty

指定此 cmdlet 从操作中排除的属性。 允许使用通配符。

从 PowerShell 6 开始，不再需要包含 **Property** 参数即可使用 **ExcludeProperty** 。

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExpandProperty

指定要选择的属性，并指示应当尝试展开该属性。

- 如果指定的属性是数组，则数组的每个值都包含在输出中。
- 如果指定的属性是一个对象，则为每个 **InputObject** 展开对象属性

在任一情况下，输出的对象 **类型** 都将与扩展属性的 **类型** 匹配。

如果指定了 **Property** 参数， `Select-Object` 将尝试将每个选定的属性作为 **NoteProperty** 添加到每个输出对象。

> [!WARNING]
> 如果收到错误： Select：无法处理属性，因为属性 `<PropertyName>` 已经存在，请注意以下事项。
> 请注意，使用时 `-ExpandProperty` ， `Select-Object` 不能替换现有属性。
> 这意味着：
>
> - 如果展开的对象具有相同名称的属性，则会发生错误。
> - 如果 *所选* 对象的属性与 *展开* 的对象属性的名称相同，则会发生错误。

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -第一个

指定要从输入对象的数组的开头选择的对象数。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

基于对象的索引值从数组中选择对象。 以逗号分隔的列表形式输入索引。 数组中的索引从 0 开始，0 表示第一个值，(n-1) 表示最后一个值。

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要通过管道发送到 cmdlet 的对象。 此参数使你能够将对象传递给 `Select-Object` 。

将对象传递到 **inputobject** 参数时，不使用管道将 `Select-Object` **InputObject** 视为单个对象，即使该值是集合也是如此。 建议在将集合传递到时使用管道 `Select-Object` 。

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

### -Last

指定要从输入对象的数组的末尾选择的对象数。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定要选择的属性。 这些属性作为 **NoteProperty** 成员添加到输出对象。 允许使用通配符。

**Property** 参数的值可以是新的计算属性。 若要创建计算属性，请使用哈希表。

有效键包括：

- 名称 (或标签) - `<string>`
- Expression `<string>` 或 `<script block>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Skip

跳过（不选择）指定数目的项目。 默认情况下， **Skip** 参数会从数组或对象列表的开头开始计数，但如果命令使用 **最后一个** 参数，则会从列表或数组的末尾开始计数。

与从 0 开始计数的 **Index** 参数不同，**Skip** 参数从 1 开始计数。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

跳过 (不选择从列表或数组的末尾) 指定数目的项。 的工作方式与结合使用 **Skip** 和 **Last** 参数相同。

与从0开始计数的 **Index** 参数不同， **SkipLast** 参数从1开始计数。

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Unique

指定如果输入对象的子集有相同的属性和值，则只选择该子集的一个成员。

此参数区分大小写。 因此，会将仅大小写不同的字符串视为唯一项。

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

### -Wait

指示该 cmdlet 禁用优化。 PowerShell 会按照命令在命令管道中出现的顺序运行命令，并允许它们生成所有对象。 默认情况下，如果在 `Select-Object` 命令管道中包含带有 **第一个** 或 **索引** 参数的命令，则在生成所选数量的对象之后，PowerShell 会立即停止生成对象的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipIndex

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Select-Object` 。

## 输出

### System.Management.Automation.PSObject

## 注释

- 还可以 `Select-Object` 通过其内置别名来引用 cmdlet `select` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

- 的优化功能 `Select-Object` 仅适用于在处理管道时将对象写入管道的命令。 它对用于缓冲处理的对象并将其作为集合写入的命令不起作用。 立即写入对象是 cmdlet 设计的最佳做法。 有关详细信息，请参阅 [强烈建议开发指南](/powershell/scripting/developer/windows-powershell)中 _的将单个记录写入管道_。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Group-Object](Group-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
