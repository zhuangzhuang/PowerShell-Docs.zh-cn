---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: 6bed0e8d13cb834fab97dc0265ef7d46a2caea97
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598491"
---
# Compare-Object

## 摘要
将两组对象进行比较。

## 语法

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## 说明

`Compare-Object`Cmdlet 比较两组对象。 一组对象是 **引用**，而另一组对象则是 **不同** 的。

`Compare-Object` 检查比较整个对象的可用方法。 如果找不到合适的方法，它将调用 input 对象的 **ToString ( # B1** 方法，并比较字符串结果。 您可以提供一个或多个用于比较的属性。 当提供属性时，cmdlet 仅比较这些属性的值。

比较的结果将指示属性值是只出现在 **引用** 对象中 (`<=`) 还是仅出现在 **差异** 对象 () 中 `=>` 。 如果使用了 **IncludeEqual** 参数， (`==`) 指示值在两个对象中。

如果 **引用** 或 **差异** 对象为 null (`$null`) ，则 `Compare-Object` 生成终止错误。

一些示例使用展开来减少代码示例的行长度。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 示例

### 示例 1-比较两个文本文件的内容

此示例比较两个文本文件的内容。 该示例使用以下两个文本文件，每个值都在单独的行上。

- `Testfile1.txt` 包含以下值： dog、squirrel 和鸟。
- `Testfile2.txt` 包含值： cat、鸟和 racoon。

输出只显示文件之间的不同行。 `Testfile1.txt`**引用** 对象 (`<=`) ， `Testfile2.txt` 是 () 的 **差异** 对象 `=>` 。 不会显示带有同时出现在这两个文件中的内容的行。

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### 示例 2-比较每个内容行并排除差异

此示例使用 **ExcludeDifferent** 参数比较两个文本文件中的每行内容。

在 PowerShell 7.1 中，使用 **ExcludeDifferent** 参数时， **IncludeEqual** 将被推断出来，并且输出只包含两个文件中包含的行，如 **SideIndicator** (`==`) 所示。

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### 示例 3-显示使用 PassThru 参数时的差异

通常， `Compare-Object` 返回具有以下属性的 **PSCustomObject** 类型：

- 要比较的 **InputObject**
- 显示输出所属的输入对象的 **SideIndicator** 属性

当使用 **PassThru** 参数时，不会更改对象的 **类型**，但返回的对象的实例将添加一个名为 **SideIndicator** 的 **NoteProperty** 。 **SideIndicator** 显示输出所属的输入对象。

下面的示例显示了不同的输出类型。

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

使用 **PassThru** 时，将返回原始对象类型 (**system.object**) 。 请注意，由 **system.exception 对象的** 默认格式显示的输出如何不显示 **SideIndicator** 属性。 但是，返回的 **system.object** 对象具有添加的 **NoteProperty**。

### 示例 4-使用属性比较两个简单对象

在此示例中，比较两个具有相同长度的不同字符串。

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### 示例 5-使用属性比较复杂对象

此示例显示比较复杂对象时的行为。 在此示例中，我们为不同的 PowerShell 实例存储两个不同的进程对象。 这两个变量都包含具有相同名称的进程对象。 如果在不指定 **Property** 参数的情况下比较对象，则该 cmdlet 会将对象视为相等。 请注意， **InputObject** 的值与 **ToString ( # B1** 方法的结果相同。 由于 system.exception **类没有** **IComparable** 接口，因此该 cmdlet 将对象转换为字符串，然后对结果进行比较。

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

指定要比较的属性时，该 cmdlet 将显示差异。

### 示例 6-比较实现 IComparable 的复杂对象

如果对象实现 **IComparable**，则该 cmdlet 会搜索比较对象的方法。如果对象属于不同类型，则 **差异** 对象将转换为 **ReferenceObject** 的类型，然后进行比较。

在此示例中，我们将字符串与 **TimeSpan** 对象进行比较。 在第一种情况下，将字符串转换为 **TimeSpan** ，使对象相等。

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

在第二种情况下， **TimeSpan** 转换为字符串，因此对象不同。

## 参数

### -CaseSensitive

指示比较应区分大小写。

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

### -Culture

指定比较中要使用的区域性。

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

### -DifferenceObject

指定与 **引用** 对象进行比较的对象。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

指示此 cmdlet 仅显示相等的比较对象的特征。 丢弃对象之间的差异。

结合使用 **ExcludeDifferent** 和 **IncludeEqual** ，只显示 **引用** 对象与 **差异** 对象之间的匹配行。

如果未指定 **ExcludeDifferent** ， **则** 没有任何输出。

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

### -IncludeEqual

**IncludeEqual** 显示 **引用** 对象与 **差异** 对象之间的匹配项。

默认情况下，输出还包括 **reference** 对象和 **差异** 对象之间的差异。

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

### -PassThru

当使用 **PassThru** 参数时，将 `Compare-Object` 省略比较的对象周围的 **PSCustomObject** 包装，并返回不变的不同对象。

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

### -Property

指定要比较的 **引用** 对象和 **差异** 对象的属性数组。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- Expression `<string>` 或 `<script block>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

指定用作比较引用的对象数组。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

指定 `Compare-Object` 在对象集合中查找匹配项时所检查的相邻对象的数目。 `Compare-Object` 当相邻对象在集合中的同一位置找不到该对象时，检查它们。 默认值为 `[Int32]::MaxValue` ，这意味着 `Compare-Object` 检查整个对象集合。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以将对象向下发送到 **DifferenceObject** 参数。

## 输出

### 无

如果 **引用** 对象和 **差异** 对象相同，则没有输出，除非使用 **IncludeEqual** 参数。

### System.Management.Automation.PSCustomObject

如果对象不同，则 `Compare-Object` 使用 SideIndicator 属性包装包装中的不同对象， `PSCustomObject` 以引用差异。 

当使用 **PassThru** 参数时，不会更改对象的 **类型**，但返回的对象的实例将添加一个名为 **SideIndicator** 的 **NoteProperty** 。 **SideIndicator** 显示输出所属的输入对象。

## 说明

使用 **PassThru** 参数时，控制台中显示的输出可能不包括 **SideIndicator** 属性。 的对象类型输出的默认格式视图 `Compare-Object` 不包括 **SideIndicator** 属性。 有关详细信息，请参阅本文中的 [示例 3](#ex3) 。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
