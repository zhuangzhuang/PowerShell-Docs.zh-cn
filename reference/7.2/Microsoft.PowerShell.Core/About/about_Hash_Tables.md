---
description: 介绍如何在 PowerShell 中创建、使用和排序哈希表。
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: dec2683acfa4fcf79419beea9e0840387d3d43d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597434"
---
# <a name="about-hash-tables"></a>关于哈希表

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中创建、使用和排序哈希表。

## <a name="long-description"></a>详细说明

哈希表也称为字典或关联数组，是存储一个或多个键/值对的压缩数据结构。 例如，哈希表可能包含一系列 IP 地址和计算机名称，其中 IP 地址是密钥，计算机名称是值，反之亦然。

在 PowerShell 中，每个哈希表都是一个 () 对象的哈希表。 可以在 PowerShell 中使用哈希表对象的属性和方法。

从 PowerShell 3.0 开始，可以使用 [有序] 属性在 PowerShell 中创建一个 () 的排序字典。

顺序字典不同于哈希表，因为键始终按列出它们的顺序出现。 哈希表中的键顺序不确定。

哈希表中的键和值也是 .NET 对象。 它们最常见的是字符串或整数，但它们可以有任何对象类型。 您还可以创建嵌套哈希表，其中键的值为另一个哈希表。

通常使用哈希表，因为它们非常适合用于查找和检索数据。 您可以使用哈希表来存储列表，并在 PowerShell 中创建计算属性。 而且，PowerShell 有一个 cmdlet Convertfrom-csv-Convertfrom-stringdata，它将字符串转换为哈希表。

### <a name="syntax"></a>语法

哈希表的语法如下所示：

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

排序字典的语法如下所示：

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

PowerShell 3.0 中引入了 [有序] 属性。

### <a name="creating-hash-tables"></a>创建哈希表

若要创建哈希表，请遵循以下准则：

- 以 at 符号 ( @ ) 开始哈希表。
- 将哈希表括在大括号中， ({}) 。
- 为哈希表的内容输入一个或多个键/值对。
- 使用等号 (=) 将每个键与其值分隔开。
- 使用分号 (; ) 或换行以分隔键/值对。
- 包含空格的键必须用引号引起来。 值必须是有效的 PowerShell 表达式。 字符串必须用引号引起来，即使它们不包含空格也是如此。
- 若要管理哈希表，请将其保存在变量中。
- 将有序哈希表分配给变量时，请将 [有序] 特性置于 "@" 符号之前。 如果将其放在变量名称之前，则该命令将失败。

若要在 $hash 的值中创建空的哈希表，请键入：

```powershell
$hash = @{}
```

您还可以在创建哈希表时将其添加到哈希表中。 例如，下面的语句创建一个包含三个键的哈希表。

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>创建有序字典

您可以通过添加一个 OrderedDictionary 类型的对象来创建一个排序的字典，但创建排序的字典最简单的方法是使用 [有序] 特性。

PowerShell 3.0 中引入了 [有序] 属性。

紧靠在 "@" 符号前面放置属性。

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

您可以使用按顺序字典的相同方式使用哈希表。
任一类型都可用作参数的值，这些参数采用哈希表或字典 (iDictionary) 。

不能使用 [有序] 特性来转换或强制转换哈希表。 如果将已排序的属性放在变量名称之前，则该命令将失败，并出现以下错误消息。

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

若要更正该表达式，请移动 [有序] 特性。

```powershell
PS C:\> $hash = [ordered]@{}
```

您可以将有序的字典转换为哈希表，但不能恢复已排序的属性，即使您清除该变量并输入新值。 若要重新建立顺序，必须删除并重新创建变量。

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>显示哈希表

若要显示保存在变量中的哈希表，请键入变量名称。
默认情况下，哈希表显示为一个表，其中包含一个键列和一个用于值的列。

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

哈希表具有关键字和值属性。 使用点表示法显示所有键或所有值。

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

每个密钥名称也是哈希表的属性，其值为键-名称属性的值。 使用以下格式来显示属性值。

```powershell
$hashtable.<key>
<value>
```

例如：

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

如果密钥名称与哈希表类型的某个属性名称冲突，则可以使用 `PSBase` 来访问这些属性。 例如，如果密钥名称为， `keys` 并且你想要返回密钥的集合，请使用以下语法：

```powershell
$hashtable.PSBase.Keys
```

哈希表具有一个 Count 属性，该属性指示哈希表中的键/值对的数目。

```powershell
C:\PS> $hash.count
3
```

哈希表表不是数组，因此不能将整数用作哈希表中的索引，但可以使用键名来索引到哈希表中。
如果该密钥是一个字符串值，则将该键名称用引号引起来。

例如：

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>添加和删除键和值

若要将键和值添加到哈希表，请使用以下命令格式。

```powershell
$hash["<key>"] = "<value>"
```

例如，若要将值为 "Now" 的 "Time" 键添加到哈希表，请使用以下语句格式。

```powershell
$hash["Time"] = "Now"
```

还可以通过使用 system.exception 对象的 Add 方法，将键和值添加到哈希表中。 Add 方法具有以下语法：

```powershell
Add(Key, Value)
```

例如，若要将值为 "Now" 的 "Time" 键添加到哈希表，请使用以下语句格式。

```powershell
$hash.Add("Time", "Now")
```

而且，您可以通过使用加法运算符 (+) 向现有哈希表添加一个哈希表来向哈希表添加键和值。 例如，下面的语句将值为 "Now" 的 "Time" 键添加到 $hash 变量的哈希表中。

```powershell
$hash = $hash + @{Time="Now"}
```

您还可以添加变量中存储的值。

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

不能使用减法运算符从哈希表中删除键/值对，但可以使用哈希表对象的 Remove 方法。 Remove 方法使用键作为其值。

Remove 方法具有以下语法：

```
Remove(Key)
```

例如，若要从 $hash 变量的值中的哈希表中删除时间 = Now 键/值对，请键入：

```powershell
$hash.Remove("Time")
```

可以在 PowerShell 中使用哈希表对象的所有属性和方法，包括 Contains、Clear、Clone 和 CopyTo。 有关哈希表对象的详细信息，请参阅 [system.object](/dotnet/api/system.collections.hashtable)。

### <a name="object-types-in-hashtables"></a>哈希表中的对象类型

哈希表中的键和值可具有任何 .NET 对象类型，而单个哈希表可以具有多个类型的键和值。

下面的语句创建进程名称字符串的哈希表和进程对象值，并将其保存在 `$p` 变量中。

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

您可以在中显示哈希表 `$p` ，并使用键名属性来显示这些值。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

哈希表中的键还可以是任意 .NET 类型。 下面的语句将一个键/值对添加到变量中的哈希表 `$p` 。 密钥是表示 WinRM 服务的服务对象，值是该服务的当前状态。

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

您可以使用在哈希表中用于其他对的相同方法来显示和访问新的键/值对。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

哈希表中的键和值也可以是哈希表对象。 下面的语句将键/值对添加到哈希表中的哈希表中，该 `$p` 变量中的键是字符串 Hash2，而值是具有三个键/值对的哈希表。

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

您可以通过使用相同的方法来显示和访问新值。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>对键和值进行排序

哈希表中的项在本质上是无序的。 每次显示键/值对时，它们的显示顺序可能不同。

尽管不能对哈希表进行排序，但可以使用哈希表的 GetEnumerator 方法枚举键和值，然后使用 Sort-Object cmdlet 对要显示的枚举值进行排序。

例如，以下命令枚举变量的哈希表中的键和值 `$p` ，然后按字母顺序对键进行排序。

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

以下命令使用相同的过程来按降序对哈希值进行排序。

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>从哈希表创建对象

从 PowerShell 3.0 开始，可以从属性和属性值的哈希表创建对象。

语法如下：

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

此方法仅适用于具有 null 构造函数（即，没有参数的构造函数）的类。 对象属性必须是公共且可设置的。

有关详细信息，请参阅 [about_Object_Creation](about_Object_Creation.md)。

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

`ConvertFrom-StringData`Cmdlet 将一个字符串或键/值对的字符串转换为哈希表。 可以 `ConvertFrom-StringData` 在脚本的数据部分中安全地使用 cmdlet，并将其与 cmdlet 一起使用， `Import-LocalizedData` 以在用户界面中显示用户消息 (UI) 当前用户的区域性。

此处-当哈希表中的值包含引号时，字符串特别有用。 有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。

下面的示例演示如何在上一个示例中创建用户消息的下一个字符串，以及如何使用将 `ConvertFrom-StringData` 它们从字符串转换为哈希表。

下面的命令创建一个键/值对的字符串，然后将其保存在 \$ 字符串变量中。

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

此命令使用 ConvertFrom-StringData cmdlet 将此处的字符串转换为哈希表。

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。

## <a name="see-also"></a>另请参阅

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System.Collections.Hashtable](/dotnet/api/system.collections.hashtable)
