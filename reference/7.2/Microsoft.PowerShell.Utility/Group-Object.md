---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 6198964f01a4c0dc70584cdb3e5c0e13f3965934
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598468"
---
# Group-Object

## 摘要
包含相同指定属性的值的组对象。

## SYNTAX

### 散

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## DESCRIPTION

该 `Group-Object` cmdlet 根据指定属性的值在组中显示对象。
`Group-Object` 返回一个表，其中每个属性值对应一行，列显示具有该值的项的数目。

如果指定多个属性，则 `Group-Object` 先按第一个属性的值对它们进行分组，然后在每个属性组内按下一个属性的值进行分组。

从 PowerShell 7 开始， `Group-Object` 可以结合 **CaseSensitive** 和 **AsHashtable** 参数来创建区分大小写的哈希表。 哈希表键使用区分大小写的比较并输出一个 **system.object** 对象。

## 示例

### 示例1：按扩展名对文件进行分组

此示例以递归方式获取下的文件 `$PSHOME` ，并按文件扩展名对其进行分组。 输出将发送到 `Sort-Object` cmdlet，该 cmdlet 会按给定扩展的计数文件进行排序。 空 **名称** 表示目录。

此示例使用 **NoElement** 参数来省略该组的成员。

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### 示例2：按几率和能够对整数分组

此示例演示如何将脚本块用作 **Property** 参数的值。 此命令显示1到20之间的整数，并按可能性甚至进行分组。

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### 示例3：按 EntryType 对事件日志事件进行分组

此示例在系统事件日志中显示1000的最新条目，按 **EntryType** 分组。

在输出中， **Count** 列表示每个组中的条目数。 **Name** 列表示定义组 **的类型名称值。** **组** 列表示每个组中的对象。

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### 示例4：按优先级类对进程分组

此示例演示了 **NoElement** 参数的效果。 这些命令按优先级对计算机上的进程进行分组。

第一个命令使用 `Get-Process` cmdlet 来获取计算机上的进程，并沿管道向下发送对象。 `Group-Object`按进程的 **PriorityClass** 属性的值对对象进行分组。

第二个示例使用 **NoElement** 参数从输出中删除组的成员。 结果为仅具有 **Count** 和 **Name** 属性值的表。

结果显示在下面的示例输出中。

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### 示例5：按名称对进程分组

下面的示例使用 `Group-Object` 对本地计算机上运行的多个进程实例进行分组。 `Where-Object` 显示具有多个实例的进程。

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### 示例6：将对象分组到哈希表中

此示例使用 **AsHashTable** 和 **AsString** 参数以键-值对集合的形式返回哈希表中的组。

在生成的哈希表中，每个属性值都是一个键，组元素是值。
因为每个键都是哈希表对象的一个属性，所以你可以使用点表示法来显示这些值。

第一个命令获取 `Get` `Set` 会话中的和 cmdlet、按谓词对其进行分组、以哈希表的形式返回组，并将哈希表保存在 `$A` 变量中。

第二个命令显示中的哈希表 `$A` 。 有两个键-值对，一个用于 `Get` cmdlet，一个用于 `Set` cmdlet。

第三个命令使用点表示法， `$A.Get` 在中显示 " **获取** 密钥" 的值 `$A` 。 这些值是 **CmdletInfo** 对象。 **AsString** 参数不会将组中的对象转换为字符串。

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### 示例7：创建区分大小写的哈希表

此示例合并了 **CaseSensitive** 和 **AsHashTable** 参数，以创建区分大小写的哈希表。 该示例中的文件的扩展名为 `.txt` 和 `.TXT` 。

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

`$hash`变量存储了 **system.object** 对象。 `Get-ChildItem` 获取目录中的文件名 `C:\Files` ，并沿管道向下发送 **FileInfo** 对象。 `Group-Object` 使用 **属性** 值 **扩展** 对对象进行分组。 **CaseSensitive** 和 **AsHashTable** 参数创建哈希表，并使用区分大小写的键和对键进行 `.txt` 分组 `.TXT` 。

## PARAMETERS

### -AsHashTable

指示此 cmdlet 将组作为哈希表返回。 哈希表的键是作为对象分组依据的属性值。 哈希表的值是具有该属性值的对象。

**AsHashTable** 参数本身返回每个哈希表，其中每个键都是一个分组对象的实例。 与 **AsString** 参数一起使用时，哈希表中的键是字符串。

从 PowerShell 7 开始，若要创建区分大小写的哈希表，请在命令中包含 **CaseSensitive** 和 **AsHashtable** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

指示此 cmdlet 将哈希表键转换为字符串。 默认情况下，哈希表键是分组对象的实例。 此参数仅在与 **AsHashTable** 参数一起使用时才有效。

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

### -CaseSensitive

指示此 cmdlet 使分组区分大小写。 在没有此参数的情况下，组中对象的属性值可能有不同的大小写。

从 PowerShell 7 开始，若要创建区分大小写的哈希表，请在命令中包含 **CaseSensitive** 和 **AsHashtable** 。

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

指定要在比较字符串时使用的区域性。

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

### -InputObject

指定要分组的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

使用 **InputObject** 参数将对象集合提交到时 `Group-Object` ，会 `Group-Object` 收到一个表示集合的对象。 因此，它将创建一个组并将该对象用作其成员。

若要对集合中的对象进行分组，请通过管道将对象传递给 `Group-Object` 。

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

### -NoElement

指示此 cmdlet 省略结果中组的成员。

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

指定用于分组的属性。 根据指定属性的值将对象排列成组。

**Property** 参数的值可以是新的计算属性。 计算属性可以是脚本块，也可以是哈希表。 有效的键-值对为：

- Expression `<string>` 或 `<script block>`

有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Group-Object` 。

## 输出

### Microsoft.PowerShell.Commands.GroupInfo 或 System.Collections.Hashtable

当你使用 **AsHashTable** 参数时，将 `Group-Object` 返回一个 **哈希表** 对象。
否则，它将返回 **GroupInfo** 对象。

## 注释

您可以使用格式设置 cmdlet （例如和）的 **GroupBy** 参数 `Format-Table` `Format-List` 对对象进行分组。 与 `Group-Object` （这会创建一个表，其中每个属性值对应一行）不同， **GroupBy** 参数为每个属性值创建一个表，每个属性值对应于具有属性值的每个项。

`Group-Object` 不要求分组的对象具有相同的 Microsoft .NET 核心类型。 分组不同 .NET Core 类型的对象时， `Group-Object` 将使用以下规则：

- 相同的属性名和类型。

  如果对象具有具有指定名称的属性，并且属性值具有相同的 .NET Core 类型，则将使用与同一类型的对象相同的规则对属性值进行分组。

- 相同的属性名称和不同类型。

  如果对象具有具有指定名称的属性，但属性值在不同的对象中具有不同的 .NET Core 类型，则使用该属性的 `Group-Object` 第一个匹配项的 .Net 核心类型作为该属性组的 .Net core 类型。 当对象具有不同类型的属性时，会将属性值转换为该组的类型。 如果类型转换失败，则不会将该对象包含在组中。

- 缺少属性。

  不能对没有指定属性的对象进行分组。 未分组的对象会出现在名为的组中的最终 **GroupInfo** 对象输出中 `AutomationNull.Value` 。

## 相关链接

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
