---
description: 描述使用 Microsoft .NET 类型的运算符。
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 66687a2282cfd321146888daad92fef40ef6cb0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598079"
---
# <a name="about-type-operators"></a>关于类型运算符

## <a name="short-description"></a>简短说明
描述使用 Microsoft .NET 类型的运算符。

## <a name="long-description"></a>详细说明

布尔类型运算符 (`-is` 和 `-isNot`) 指示对象是否为指定 .net 类型的实例。 `-is`如果类型匹配并且值为 FALSE，则运算符返回 **TRUE** ; 否则返回 **FALSE** 。 `-isNot`如果类型匹配并且值为 **TRUE** ，则运算符将返回值 **FALSE** 。

`-as`运算符尝试将输入对象转换为指定的 .net 类型。 如果成功，则返回转换后的对象。 如果失败，则返回 `$null`。 它不会返回错误。

下表列出了 PowerShell 中的类型运算符。

|操作员|说明                |示例                          |
|--------|---------------------------|---------------------------------|
|`-is`   |当输入|`(get-date) -is [DateTime]`      |
|        |是的一个实例。      |`True`                           |
|        |指定的 .NET 类型。       |                                 |
|`-isNot`|当输入|`(get-date) -isNot [DateTime]`   |
|        |不是的实例     |`False`                          |
|        |specified.NET 类型。        |                                 |
|`-as`   |将输入转换为  |`"5/7/07" -as [DateTime]`        |
|        |指定的 .NET 类型。       |`Monday, May 7, 2007 12:00:00 AM`|

类型运算符的语法如下所示：

```powershell
<input> <operator> [.NET type]
```

你还可以使用以下语法：

```powershell
<input> <operator> ".NET type"
```

.NET 类型可以在括号中编写为类型名称，也可以作为字符串写入，如 `[DateTime]` 或 `"DateTime"` 。  如果类型不在 system 命名空间的根中，则指定该对象类型的完整名称。 您可以省略 "System."。 例如，若 **要指定 system.exception，请输入** `[System.Diagnostics.Process]` 、 `[Diagnostics.Process]` 或 `"Diagnostics.Process"` 。

类型运算符始终作为一个整体对输入对象进行操作。 也就是说，如果输入对象是集合，则它是所测试的 _集合_ 类型，而不是集合的 _元素_ 的类型。

### <a name="-isisnot-operators"></a>-is/isNot 运算符

**布尔** 类型运算符 (`-is` 和 `-isNot`) 总是返回一个 **布尔** 值，即使输入是对象的集合。

如果 `<input>` 是与 .Net 类型相同或 _派生_ 自 .net 类型的类型，则 `-is` 运算符返回 `$True` 。

例如， **DirectoryInfo** 类型派生自 **FileSystemInfo** 类型。 因此，这两个示例都返回 **True**。

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

`-is`如果在 `<input>` 比较中实现了接口，则运算符还可以匹配接口。 在此示例中，输入是一个数组。 数组实现了 **system.object** 接口。

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>-as 运算符

`-as`运算符尝试将输入对象转换为指定的 .net 类型。 如果成功，则返回转换后的对象。 如果失败，它将返回 `$null` 。 它不会返回错误。

如果 `<input>` 是 _派生_ 自 .net 类型的类型，则 `-as` _通过_ 返回的输入对象保持不变。 例如， **DirectoryInfo** 类型派生自 **FileSystemInfo** 类型。 因此，在以下示例中，对象类型保持不变：

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>转换 DateTime 类型区分区域性

与类型强制转换不同， `[DateTime]` 使用运算符转换为类型 `-as` 仅适用于根据当前区域性的规则进行格式设置的字符串。

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

若要查找对象的 .NET 类型，请使用 `Get-Member` cmdlet。 或者，将所有对象的 **GetType** 方法与此方法的 **FullName** 属性一起使用。 例如，下面的语句获取命令的返回值的类型 `Get-Culture` ：

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>示例

下面的示例演示类型运算符的一些用法：

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

下面的示例演示当输入为对象的集合时，匹配类型为集合的 .NET 类型，而不是集合中各个对象的类型。

在此示例中，尽管 `Get-Culture` 和 `Get-UICulture` cmdlet 都返回 **system.object** 对象，但这些对象的集合是一个 system.object 数组。

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

下面的示例演示如何使用 `-as` 运算符。

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

下面的示例演示当 `-as` 运算符不能将输入对象转换为 .net 类型时，它将返回 `$null` 。

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>另请参阅

[about_Operators](about_Operators.md)
