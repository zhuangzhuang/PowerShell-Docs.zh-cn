---
description: 介绍数组，数组是设计用于存储项集合的数据结构。
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 15ab7bb28fc9dd9262ba71b5cc1347a609837d9c
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412974"
---
# <a name="about-arrays"></a>关于数组

## <a name="short-description"></a>简短说明
介绍数组，数组是设计用于存储项集合的数据结构。

## <a name="long-description"></a>详细说明

数组是一种数据结构，用于存储项的集合。
项可以是同一类型，也可以是不同的类型。

从 Windows PowerShell 3.0 开始，零个或一个对象的集合具有数组的某些属性。

## <a name="creating-and-initializing-an-array"></a>创建和初始化数组

若要创建并初始化数组，请将多个值分配给一个变量。 存储在数组中的值用逗号分隔，赋值运算符将其与变量名称隔开 (`=`) 。

例如，若要创建一个名为 `$A` 的数组，该数组包含七个数值 (int) 值22、5、10、8、12、9和80，请键入：

```powershell
$A = 22,5,10,8,12,9,80
```

还可以通过将逗号置于单个项之前来初始化单个项数组。

例如，若要创建名为 `$B` 包含单值7的单个项数组，请键入：

```powershell
$B = ,7
```

还可以通过使用范围运算符 () 来创建和初始化数组 `..` 。
下面的示例创建一个包含值5到8的数组。

```powershell
$C = 5..8
```

因此， `$C` 包含四个值：5、6、7和8。

如果未指定数据类型，则 PowerShell 会将每个数组作为对象数组创建 (**system.object []**) 。 若要确定数组的数据类型，请使用 **GetType ()** 方法。 例如，若要确定数组的数据类型 `$A` ，请键入：

```powershell
$A.GetType()
```

若要创建强类型化数组（即，只可包含特定类型的值的数组），请将该变量强制转换为数组类型，如 **string []**、 **long []** 或 **int32 []**。 若要强制转换数组，请在变量名称之前加上括号内的数组类型。 例如，若要创建一个名为的32位整数数组，该数组 `$ia` 包含四个整数 (1500、2230、3350和 4000) ，请键入：

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

因此， `$ia` 数组只能包含整数。

你可以创建在 Microsoft .NET 框架中强制转换为任何支持的类型的数组。 例如， `Get-Process` 检索以表示进程的对象属于 **system.object** 类型。 若要创建进程对象的强类型数组，请输入以下命令：

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>数组子表达式运算符

"数组" 子表达式运算符从它内部的语句创建一个数组。 如果运算符中的语句生成，运算符会将其放在数组中。 即使有零个或一个对象。

数组运算符的语法如下所示：

```syntax
@( ... )
```

可以使用 array 运算符创建零个或一个对象的数组。 例如：

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

当您获取对象时，array 运算符非常有用，但不知道您获取了多少个对象。 例如：

```powershell
$p = @(Get-Process Notepad)
```

有关数组子表达式运算符的详细信息，请参阅 [about_Operators](about_Operators.md)。

## <a name="accessing-and-using-array-elements"></a>访问和使用数组元素

### <a name="reading-an-array"></a>读取数组

可以通过使用数组的变量名称来引用它。 若要显示数组中的所有元素，请键入数组名称。 例如，假设 `$a` 是包含整数0、1、2和9的数组，则键入：

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

从位置0开始，可以使用索引引用数组中的元素。 将索引号括在括号中。 例如，若要显示数组中的第一个元素 `$a` ，请键入：

```powershell
$a[0]
```

```Output
0
```

若要显示数组中的第三个元素 `$a` ，请键入：

```powershell
$a[2]
```

```Output
2
```

您可以使用索引的范围运算符来检索部分数组。 例如，若要检索数组的第二到第五个元素，请键入：

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

负数从数组末尾开始计数。 例如，"-1" 指数组的最后一个元素。 若要显示数组的最后三个元素，请在 "索引升序" 中键入：

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

如果按降序键入负索引，则输出会发生变化。

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

但是，使用此表示法时要格外小心。 表示法从结束边界到数组的开头。

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

此外，一个常见错误是 `$a[0..-2]` 指引用数组的所有元素（最后一个元素除外）。 它引用数组中的第一个、最后一个和第二个元素。

您可以使用加号运算符 (`+`) 将范围与数组中的元素列表组合在一起。 例如，若要在索引位置0、2和4到6显示元素，请键入：

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

此外，若要列出多个范围和单个元素，可以使用加号运算符。 例如，若要列出元素0到2、4到6以及第8个位置的元素，请执行以下操作：

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>数组元素的迭代

你还可以使用循环构造，如 ForEach、For 和 While 循环，以引用数组中的元素。 例如，若要使用 ForEach 循环显示数组中的元素 `$a` ，请键入：

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Foreach 循环会循环访问数组并返回数组中的每个值，直到到达数组的末尾。

当您在检查数组中的元素时递增计数器时，For 循环非常有用。 例如，若要使用 For 循环来返回数组中的每个其他值，请键入：

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

您可以使用 While 循环来显示数组中的元素，直至定义的条件不再为 true 为止。 例如，若要在 `$a` 数组索引小于4的情况下显示数组中的元素，请键入：

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>数组属性

### <a name="count-or-length-or-longlength"></a>Count 或 Length 或 LongLength

若要确定数组中有多少项，请使用 `Length` 属性或其 `Count` 别名。 `Longlength` 如果数组包含的元素超过2147483647，则会很有用。

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>级别

返回数组中的维数。 PowerShell 中的大多数数组仅具有一个维度。 即使您认为生成多维数组，如以下示例中所示：

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

"`$a rank: $($a.Rank)"
"`$a length: $($a.Length)"
"`$a length: $($a.Length)"
"Process `$a[2][1]: $($a[2][1].ProcessName)"
```

在此示例中，您将创建一个包含其他数组的一维数组。 这也称为 _交错数组_。 **Rank** 属性证明这是一维的。 若要访问交错数组中的项，索引必须位于单独的方括号中 (`[]`) 。

```Output
$a rank: 1
$a length: 3
$a[2] length: 348
Process $a[2][1]: AcroRd32
```

多维数组按 [行顺序](https://wikipedia.org/wiki/Row-_and_column-major_order)存储。 下面的示例演示如何创建一个真正的多维数组。

```powershell
[string[,]]$rank2 = [string[,]]::New(3,2)
$rank2.rank
$rank2.Length
$rank2[0,0] = 'a'
$rank2[0,1] = 'b'
$rank2[1,0] = 'c'
$rank2[1,1] = 'd'
$rank2[2,0] = 'e'
$rank2[2,1] = 'f'
$rank2[1,1]
```

```Output
2
6
d
```

若要访问多维数组中的项，请使用逗号分隔索引 (`,`)  () 的一组方括号中 `[]` 。

对多维数组的某些运算（例如复制和串联）要求对数组进行平展。 平展将数组转换为不受约束的类型的一维数组。 生成的数组按行主顺序使用所有元素。 请看下面的示例：

```powershell
$a = "red",$true
$b = (New-Object 'int[,]' 2,2)
$b[0,0] = 10
$b[0,1] = 20
$b[1,0] = 30
$b[1,1] = 40
$c = $a + $b
$a.GetType().Name
$b.GetType().Name
$c.GetType().Name
$c
```

输出显示的 `$c` 是包含和中的项的1维数组， `$a` `$b` 按行主顺序排列。

```output
Object[]
Int32[,]
Object[]
red
True
10
20
30
40
```

## <a name="methods-of-arrays"></a>数组方法

### <a name="clear"></a>清除

将所有元素值设置为数组元素类型的 _默认值_ 。
Clear () 方法不会重置数组的大小。

在下面的示例中 `$a` ，是一个对象数组。

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

在此示例中， `$intA` 显式键入以包含整数。

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

允许遍历数组中的所有元素，并为数组的每个元素执行给定操作。

ForEach 方法具有多个执行不同操作的重载。

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>ForEach (scriptblock 表达式) 

#### <a name="foreachscriptblock-expression-object-arguments"></a>ForEach (scriptblock 表达式，object [] 参数) 

此方法是在 PowerShell v4 中添加的。

> [!NOTE]
> 语法要求使用脚本块。 如果 scriptblock 是唯一的参数，则括号是可选的。 此外，在方法和左括号或大括号之间不得有空格。

下面的示例演示如何使用 foreach 方法。 在此示例中，目的是生成数组中元素的平方值。

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

与的 `-ArgumentList` 参数一样 `ForEach-Object` ， `arguments` 参数允许将参数数组传递到配置为接受它们的脚本块。

有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about_Splatting.md#splatting-with-arrays)。

#### <a name="foreachtype-converttotype"></a>ForEach (类型 convertToType) 

`ForEach`方法可用于快速将元素强制转换为另一种类型; 下面的示例演示如何将字符串日期的列表转换为 `[DateTime]` 类型。

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>ForEach (string propertyName) 

#### <a name="foreachstring-propertyname-object-newvalue"></a>ForEach (string propertyName，object [] newValue) 

`ForEach`方法还可用于快速检索或设置集合中每个项的属性值。

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>ForEach (字符串方法名称) 

#### <a name="foreachstring-methodname-object-arguments"></a>ForEach (string 方法，object [] 参数) 

最后， `ForEach` 可使用方法对集合中的每个项执行方法。

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

与的 `-ArgumentList` 参数一样 `ForEach-Object` ， `arguments` 参数允许将参数数组传递到配置为接受它们的脚本块。

> [!NOTE]
> 从 Windows PowerShell 3.0 中开始，还可以使用 "标量对象和集合的方法" 来完成为集合中的每个项检索属性和执行方法的操作，可以在此处 [about_methods](about_methods.md)获取详细信息。

### <a name="where"></a>Where

允许筛选或选择数组的元素。 脚本的计算结果必须为：零 (0) ，空字符串，或要 `$false` 在 `$null``Where`

此方法有一个定义 `Where` 。

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> 语法要求使用脚本块。 如果 scriptblock 是唯一的参数，则括号是可选的。 此外，在方法和左括号或大括号之间不得有空格。

`Expression`是筛选所需的 scriptblock， `mode` 可选参数允许其他选择功能， `numberToReturn` 可选参数允许限制从筛选器返回的项数。

的可接受值为 `mode` ：

- 默认 (0) -返回所有项
- 第一 (1) -返回第一项
- 最后 (2) -返回最后一项
- 跳到 (3) -跳过项，直到 condition 为 true，返回剩余项
- 到 (4) 之前-返回所有项，直到 condition 为 true
- 拆分 (5) -返回两个元素组成的数组
  - 第一个元素包含匹配项
  - 第二个元素包含剩余项

下面的示例演示如何从数组中选择所有奇数。

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

此示例演示如何选择不为空的字符串。

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>默认

`Default`模式使用 scriptblock 筛选项 `Expression` 。

如果 `numberToReturn` 提供了，则它指定要返回的最大项数。

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> `Default`模式和模式都 `First` 返回第一个 (`numberToReturn`) 项，可以互换使用。

#### <a name="last"></a>上一个

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>跳到

`SkipUntil`模式将跳过集合中的所有对象，直到对象传递脚本块表达式筛选器。 然后，它将返回 **所有** 剩余的集合项而不测试它们。 _仅测试一个传递项_。

这意味着返回的集合包含未经过测试的 _传递_ 和 _非传递_ 项。

通过将值传递给参数，可以限制返回的项数 `numberToReturn` 。

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>生效

`Until`模式反转 `SkipUntil` 模式。  它将返回集合中的 **所有** 项，直到某个项通过脚本块表达式。 在项 _传递_ scriptblock 表达式后，该 `Where` 方法将停止处理项。

这意味着从方法接收第一组 _非传递_ 项 `Where` 。 一项通过 _后_，就不会测试或返回其余的项。

通过将值传递给参数，可以限制返回的项数 `numberToReturn` 。

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> `Until`和 `SkipUntil` 在不测试一批项目的前提下运行。
>
> `Until`返回第一个 _阶段_**之前** 的项。
>
> `SkipUntil`返回第一次 _传递_**后** 的所有项，包括第一次传递项。

#### <a name="split"></a>拆分

`Split`模式将集合项拆分为两个单独的集合。 传递 scriptblock 表达式的和不是的那些表达式。

如果 `numberToReturn` 指定了，则第一个集合包含 _传递_ 项，而不是超过指定的值。

其余的对象（甚至是那些 **传递** 表达式筛选器的对象）在第二个集合中返回。

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>获取数组的成员

若要获取数组的属性和方法（如 Length 属性和 **SetValue** 方法），请使用 Cmdlet 的 **InputObject** 参数 `Get-Member` 。

将数组传递给时 `Get-Member` ，PowerShell 将一次发送一个项并 `Get-Member` 返回数组中每个项的类型 (忽略重复项) 。

当使用 **InputObject** 参数时，将 `Get-Member` 返回数组的成员。

例如，以下命令将获取 `$a` 数组变量的成员。

```powershell
Get-Member -InputObject $a
```

还可以通过在将管道传递给 cmdlet 的值之前键入逗号 )  ( 来获取数组的成员 `Get-Member` 。 逗号使数组成为数组的数组中的第二项。 PowerShell 将每次一个数组传递到数组，并 `Get-Member` 返回数组的成员。 类似于接下来的两个示例。

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>操作数组

您可以更改数组中的元素，将元素添加到数组，并将两个数组中的值合并为第三个数组。

若要更改数组中特定元素的值，请指定要更改的元素的数组名称和索引，然后使用赋值运算符 (`=`) 为该元素指定一个新值。 例如，若要更改数组中第二项的值 `$a` (索引位置 1) 为10，请键入：

```powershell
$a[1] = 10
```

还可以使用数组的 **SetValue** 方法来更改值。 下面的示例将数组的第二个值 (索引位置 1) 更改 `$a` 为500：

```powershell
$a.SetValue(500,1)
```

可以使用 `+=` 运算符将元素添加到数组中。 下面的示例演示如何将元素添加到 `$a` 数组中。

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> 使用 `+=` 运算符时，PowerShell 实际上会创建一个新数组，其中包含原始数组的值和所添加的值。 如果多次重复操作或数组大小太大，则这可能会导致性能问题。

从数组中删除元素并不容易，但你可以创建一个新的数组，其中仅包含现有数组的选定元素。 例如，若要创建数组 `$t` ，其中包含 `$a` 数组中除索引位置2处的值之外的所有元素，请键入：

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

若要将两个数组合并成单个数组，请使用加运算符 (`+`) 。 下面的示例创建两个数组，并将它们组合在一起，然后显示生成的合并数组。

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

因此，该 `$z` 数组包含1、3、5和9。

若要删除数组，请将值分配 `$null` 给数组。 以下命令删除变量中的数组 `$a` 。

`$a = $null`

你还可以使用 `Remove-Item` cmdlet，但赋予的值 `$null` 更快，尤其是对于大型数组。

## <a name="arrays-of-zero-or-one"></a>零或一的数组

从 Windows PowerShell 3.0 开始，零个或一个对象的集合具有 Count 和 Length 属性。 此外，还可以为一个对象的数组编制索引。 此功能可帮助您避免在需要集合的命令获取的项少于两个项时出现脚本错误。

下面的示例演示了此功能。

### <a name="zero-objects"></a>零个对象

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>一个对象

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>对 System.object 对象的索引支持

PowerShell 6.1 添加了对 **元组** 对象的索引访问的支持，类似于数组。
例如：

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

与数组和其他集合对象不同，当通过管道或支持对象数组的参数传递元组对象时，会将 **元组** 对象视为单个对象。

有关详细信息，请参阅 [system.object](/dotnet/api/system.tuple)。

## <a name="see-also"></a>另请参阅

- [about_Assignment_Operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)

