---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596848"
---
# Get-Unique

## 摘要
从排序列表中返回唯一项。

## SYNTAX

### AsString（默认值）

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Unique` cmdlet 将排序列表中的每个项与下一项进行比较，消除重复项并仅返回每个项的一个实例。 必须对该列表进行排序，才能使该 cmdlet 正常运行。

`Get-Unique` 区分大小写。 因此，会将仅大小写不同的字符串视为唯一项。

## 示例

### 示例 1：获取文本文件中的唯一单词

这些命令将查找文本文件中唯一单词的数目。

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

第一个命令获取 File.txt 文件的内容。 它将文本的每一行转换为小写字母，然后在空格处（“ ”）将每个单词拆分到单独的行上。 然后，它将按字母顺序对结果列表进行排序 (默认) 并使用 `Get-Unique` cmdlet 来消除任何重复单词。 结果存储在 `$A` 变量中。

第二个命令使用中的字符串集合的 **Count** 属性 `$A` 来确定中有多少项 `$A` 。

### 示例 2：获取数组中的唯一整数

此命令将查找整数组的唯一成员。

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

第一个命令采用在命令行中键入的整数数组，将它们传递给要 `Sort-Object` 排序的 cmdlet，然后通过管道将其传递到 `Get-Unique` ，从而消除重复项。

### 示例 3：获取目录中的唯一对象类型

此命令使用 `Get-ChildItem` cmdlet 检索本地目录的内容，其中包括文件和目录。

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

管道运算符 (|) 将结果发送到 `Sort-Object` cmdlet。 `$_.GetType()`语句将 **GetType** 方法应用到每个文件或目录。 然后， `Sort-Object` 按类型对项进行排序。 另一个管道运算符将结果发送到 `Get-Unique` 。 **OnType** 参数定向 `Get-Unique` 到仅返回每种类型的一个对象。

### 示例 4：获取唯一进程

此命令将获取在计算机上运行的进程的名称，并消除重复项。

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

此 `Get-Process` 命令获取计算机上的所有进程。 管道运算符 (|) 将结果传递给 `Sort-Object` ，默认情况下，将按 ProcessName 的字母顺序对进程进行排序。 结果将通过管道传递给 `Select-Object` cmdlet，后者只选择每个对象的 ProcessName 属性的值。 然后，将结果输送到 `Get-Unique` 以消除重复项。

**AsString** 参数指示 `Get-Unique` 将 **ProcessName** 值视为字符串。
如果没有此参数，则 `Get-Unique` 将 **ProcessName** 值视为对象，并仅返回对象的一个实例，即列表中的第一个进程名称。

## PARAMETERS

### -AsString

指示此 cmdlet 将数据用作字符串。 如果没有此参数，则数据将被视为对象，因此在将相同类型的对象集合（ `Get-Unique` 如文件集合）提交到时，它只会返回一个 (第一个) 。 可以使用此参数来查找对象属性的唯一值，如文件名。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定的输入 `Get-Unique` 。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

此 cmdlet 将使用 **InputObject** 提交的输入视为集合。 它不枚举集合中的各个项。 因为集合是单个项，所以通过使用 InputObject 提交的输入始终按原样返回。

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

### -OnType

指示此 cmdlet 仅返回每种类型的一个对象。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
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

可以通过管道将任何类型的对象传递给 `Get-Unique` 。

## 输出

### System.Management.Automation.PSObject

返回的对象的类型由 `Get-Unique` 输入确定。

## 注释

还可以 `Get-Unique` 通过其内置别名来引用 `gu` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

若要对列表进行排序，请使用 Sort-Object。 你还可以使用的 **唯一** 参数 `Sort-Object` 在列表中查找唯一项。

## 相关链接

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

