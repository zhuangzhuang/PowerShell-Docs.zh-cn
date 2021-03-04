---
title: 关于哈希表的各项须知内容
description: 哈希表在 PowerShell 中非常重要，因此最好对它们进行全面深入的了解。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: a471c0fe2c48820d6c1d152e2850b1e431d28f23
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686067"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>关于哈希表的各项须知内容

我想回过头来讲讲[哈希表][]。 我现在一直在用它们。 在昨晚的用户组会议后，我给一个人教了哈希表的知识，我发现他现在对哈希表的困惑正是我以前经历过的。 哈希表在 PowerShell 中非常重要，因此最好对它们进行全面深入的了解。

> [!NOTE]
> 本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。 PowerShell 团队感谢 Kevin 与我们分享这篇文章。 请前往 [PowerShellExplained.com][] 访问他的博客。

## <a name="hashtable-as-a-collection-of-things"></a>哈希表作为一种集合

从哈希表的传统定义来说，我希望你首先将哈希表视为一个集合。 此定义使你在以后将它们用于更高级的内容时对其工作原理有一个基本了解。 缺乏这种了解通常是产生困惑的根源。

## <a name="what-is-an-array"></a>什么是数组？

在开始介绍哈希表之前，我要先提一下[数组][]。 在本讨论中，数组是值或对象的列表或集合。

```powershell
$array = @(1,2,3,5,7,11)
```

将项放入数组后，可以使用 `foreach` 来循环访问该列表，或者使用索引访问数组中的各个元素。

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

还可以使用索引以相同方式更新值。

```powershell
$array[2] = 13
```

刚刚只是说了数组的一点皮毛，但在继续介绍哈希表之前，这是必备的背景知识。

## <a name="what-is-a-hashtable"></a>什么是哈希表？

在介绍 PowerShell 使用哈希表的其他方式之前，我将首先介绍一般意义上哈希表的基本技术描述。

哈希表是一种数据结构，与数组非常相似，只不过是使用键存储每个值（对象）。 它是一个基本的键/值存储。 首先，我们创建一个空哈希表。

```powershell
$ageList = @{}
```

请注意，使用大括号（而不是圆括号）定义哈希表。 然后，使用键添加项，如下所示：

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

人员的名称为键，其年龄是我想要保存的值。

## <a name="using-the-brackets-for-access"></a>使用方括号进行访问

将值添加到哈希表后，可以使用相同的键（而不是像对数组那样使用数字索引）拉回这些值。

```powershell
$ageList['Kevin']
$ageList['Alex']
```

如果需要 Kevin 的年龄，我会使用他的名字来访问。 我们也可以使用此方法将值添加或更新到哈希表中。 这与使用上述 `add()` 函数相同。

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

还可以使用另一个语法来访问和更新值，我将在后面的部分中介绍。 如果你是从另一种语言转到 PowerShell 的，那么这些示例应该与你之前使用哈希表的方式相符。

### <a name="creating-hashtables-with-values"></a>用值创建哈希表

到目前为止，我已经为这些示例创建了一个空哈希表。 你可以在创建键和值时预先填充它们。

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>作为查找表

此类型哈希表的实际值可用作查找表。 下面是一个简单的示例。

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

在本例中，你为 `$env` 变量指定了环境，它会选择正确的服务器。 你可以使用 `switch($env){...}` 来实现这样的选择，但哈希表是个不错的选择。

当你动态构建查找表以供以后使用时，这样会更好。 因此，当你需要交叉引用时，请考虑使用这种方法。 我认为，如果 PowerShell 不擅长使用 `Where-Object` 在管道上进行筛选，我们会看到更多这样的情况。 如果遇到性能问题，则需要考虑使用此方法。

我不会说它速度更快，但它确实符合一条原则：[如果性能很重要，请对其进行测试][]。

#### <a name="multiselection"></a>多选

通常，可以将哈希表视为键/值对，你在其中提供一个键并获得一个值。 PowerShell 允许提供一个键数组来获取多个值。

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

在本例中，我使用与上文相同的查找哈希表，并提供三个不同的数组样式来获取匹配项。 这是 PowerShell 中的隐藏 gem，大多数人都不知道。

## <a name="iterating-hashtables"></a>循环访问哈希表

由于哈希表是键/值对的集合，因此，对其进行循环访问的方式与对数组或普通项列表的方式有所不同。

首先要注意的是，如果你使用管道传输哈希表，管道会将其视为一个对象。

```powershell
PS> $ageList | Measure-Object
count : 1
```

即使 `.count` 属性告诉你它包含了多少个值。

```powershell
PS> $ageList.count
2
```

如果需要的只是值，可以使用 `.values` 属性来解决这个问题。

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

通常更有用的是，枚举键并使用它们来访问值。

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

下面是同一个示例使用 `foreach(){...}` 循环的情况。

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

我们正在遍历哈希表中的每个键，然后使用它来访问值。 当将哈希表作为集合使用时，这是一种常见模式。

### <a name="getenumerator"></a>GetEnumerator()

接下来，我们将使用 `GetEnumerator()` 来循环访问哈希表。

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

枚举器依次为你提供每个键/值对。 它专为此用例而设计。 感谢 [Mark Kraus](https://get-PowerShellblog.blogspot.com) 提醒我这一点。

### <a name="badenumeration"></a>BadEnumeration

一个重要的细节是，哈希表在枚举时无法修改。 如果我们从基本的 `$environments` 示例开始：

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

尝试将每个键设置为相同的服务器值将会失败。

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

这样也会失败，即使它看起来应该是好的：

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

应对这种情况的技巧是在执行枚举之前克隆键。

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>哈希表作为属性集合

到目前为止，我们在哈希表中放置的对象类型都属于同一对象类型。 我在所有这些示例中使用的是年龄，键是人员的名字。 如果对象集合中每个对象都有一个名称，这会是一个查看它的好方法。 在 PowerShell 中使用哈希表的另一种常见方法是保留属性集合，其中键是属性名称。 在下一个示例中，我将深入探讨这一点。

### <a name="property-based-access"></a>基于属性的访问

使用基于属性的访问会更改哈希表的动态，以及其在 PowerShell 中的使用方式。 这是我们上面常见的例子，在其中键被视为属性。

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

与上面的例子一样，在本例中，如果哈希表中不存在这些键，那么将添加它们。 根据你如何定义键和值，这可能有点奇怪，也可能完全合适。 到目前为止，年龄列表的例子运行良好。 我们需要一个新的示例来保持这种良好态势。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

我们可以像这样在 `$person` 上添加和访问属性。

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

此哈希表的外观和行为突然变得与对象一样。 它仍是事项的集合，因此以上所有示例仍适用。 我们只是从不同的角度来处理它。

### <a name="checking-for-keys-and-values"></a>检查键和值

在大多数情况下，只需按如下所示测试值：

```powershell
if( $person.age ){...}
```

这很简单，但对我来说曾是众多 bug 的源头，因为我在逻辑中忽视了一个重要的细节。 我开始使用它来测试键是否存在。 如果值为 `$false` 或零，则该语句将意外返回 `$false`。

```powershell
if( $person.age -ne $null ){...}
```

这会解决此零值问题，但不能解决 $null 与键不存在的问题。 大多数情况不需要进行这种区分，但当你这么做时有一些函数供你使用。

```powershell
if( $person.ContainsKey('age') ){...}
```

还有一个 `ContainsValue()`适用于在不知道键或循环访问整个集合的条件下测试值的情况。

### <a name="removing-and-clearing-keys"></a>删除和清除键

可以使用 `.Remove()` 函数删除键。

```powershell
$person.remove('age')
```

向它们赋值 `$null` 后只会留下一个具有 `$null` 值的键。

清除哈希表的常用方法是将其初始化为空哈希表。

```powershell
$person = @{}
```

虽然这样做确实有用，但请尝试改用 `clear()` 函数。

```powershell
$person.clear()
```

这是使用该函数创建自文档化代码的实例之一，它使代码的意图非常清晰。

## <a name="all-the-fun-stuff"></a>所有趣味内容

### <a name="ordered-hashtables"></a>排序哈希表

默认情况下，哈希表不进行排序（或排列）。 在传统的上下文中，当你始终使用键来访问值时，顺序并不重要。 你可能会发现，你希望属性保持你为它们定义的顺序。 令人欣慰的是，有一种方法可以使用 `ordered` 关键字实现此目的。

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

现在，当你枚举键和值时，它们会保持该顺序。

### <a name="inline-hashtables"></a>内联哈希表

在一行上定义哈希表时，可以用分号分隔键/值对。

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

如果要在管道上创建它们，这会很方便。

### <a name="custom-expressions-in-common-pipeline-commands"></a>常见管道命令中的自定义表达式

有一些 cmdlet 支持使用哈希表创建自定义属性或计算属性。 常见的例子是 `Select-Object` 和 `Format-Table`。 这些哈希表有一个特殊的语法，在完全展开时就像下面这样。

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

该 cmdlet 会将列标记为 `name`。 `expression` 则是一个脚本块，它会在管道上对象的值是 `$_` 时执行。 下面是实际的脚本：

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Property name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

我将它放在一个变量中，但它可以很容易地在内联中定义，并且你可以顺便将 `name` 缩写为 `n`，将 `expression` 缩写为 `e`。

```powershell
$drives | Select-Object -property name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

我个人不喜欢命令执行的时间太长，而且它经常会引发一些我不会涉及的不良行为。 我更有可能使用所需的所有字段和属性创建新的哈希表或 `pscustomobject`，而不是在脚本中使用这种方法。 但有很多代码可以做到这一点，希望你能了解。 稍后我会讨论如何创建 `pscustomobject`。

### <a name="custom-sort-expression"></a>自定义排序表达式

如果对象具有你想要排序的数据，则可以很容易地对集合进行排序。 可以在排序之前将数据添加到对象，或者为 `Sort-Object` 创建自定义表达式。

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

在本例中，我将使用一列用户，并使用一些自定义 cmdlet 获取更多有关排序的信息。

#### <a name="sort-a-list-of-hashtables"></a>对一列哈希表排序

如果你有一列想要排序的哈希表，你会发现 `Sort-Object` 不会将键视为属性。 我们可以通过使用自定义排序表达式来解决。

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>在执行 cmdlet 时展开哈希表

这是我最喜欢哈希表的地方之一，很多人以前都没有发现这一点。
其思路是，无需在一行上向 cmdlet 提供所有属性，而是先将它们打包为一个哈希表。 然后，你可以通过一种特殊方式将哈希表赋予函数。
下面是以常规方式创建 DHCP 作用域的示例。

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

如果不使用[展开][]，则需要在一行上定义所有这些内容。 它会在屏幕上滚动或自动换行。 现在把它与使用展开的命令进行比较。

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

使用 `@` 符号而非 `$` 会调用展开操作。

看看这个例子多么易读。 它们是具有所有相同值的完全相同的命令。 第二个更易于理解和保持下去。

我会在命令太长时使用展开。 我定义得太长，导致窗口向右滚动。 如果我找到某个函数的三个属性，则有可能会使用展开哈希表来重写它。

### <a name="splatting-for-optional-parameters"></a>针对可选参数的展开

我使用展开的最常见方式之一是处理来自脚本中其他地方的可选参数。 假设有一个函数，该函数包装了内含可选 `$Credential` 参数的 `Get-CIMInstance` 调用。

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

首先，使用常见参数创建我的哈希表。 然后添加 `$Credential`（如果存在）。
因为我在这里使用展开，所以我只需在代码中调用一次 `Get-CIMInstance`。 此设计模式非常整洁，可以轻松地处理许多可选参数。

公平起见，你可以编写允许参数值为 `$null` 的命令。 你只是不能一直控制你在调用的其他命令。

### <a name="multiple-splats"></a>多次展开

可以将多个哈希表展开到同一个 cmdlet。 如果我们回到最初的展开示例：

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

当我有一组要传递给许多命令的通用参数时，我会使用这个方法。

### <a name="splatting-for-clean-code"></a>展开可获得干净代码

如果可以使代码更简洁，那么展开单个参数没有什么问题。

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>展开可执行文件

展开也适用于某些使用 `/param:value` 语法的可执行文件。 例如，`Robocopy.exe` 具有一些如下所示的参数。

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

我不知道这是不是都有用，但我发现它很有趣。

## <a name="adding-hashtables"></a>添加哈希表

哈希表支持通过加法运算符来合并两个哈希表。

```powershell
$person += @{Zip = '78701'}
```

这仅适用于两个哈希表不共享键的情况。

## <a name="nested-hashtables"></a>嵌套哈希表

我们可以将多个哈希表用作一个哈希表中的值。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

我从一个包含两个键的基本哈希表开始。 我添加了一个名为 `location` 的键和一个空哈希表。 然后，我将上两项添加到 `location` 哈希表。 我们也可以用内联的方式完成此操作。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

这会创建与上面看到的相同哈希表，并可以通过相同的方式访问属性。

```powershell
$person.location.city
Austin
```

可以通过多种方式处理对象的结构。 下面是查看嵌套哈希表的另一种方法。

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

这混合了使用哈希表作为对象集合和属性集合的概念。 即使使用你喜欢的任何方法嵌套这些值，仍然可以轻松地访问它们。

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

当我把它当作属性时，我倾向于使用点属性。 这些通常是我在代码中静态定义的内容，我对它们非常了解。 如果我需要遍历列表或以编程方式访问键，我会使用方括号提供键名。

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

能够嵌套哈希表为你提供了很多灵活性和选项。

### <a name="looking-at-nested-hashtables"></a>查看嵌套的哈希表

一旦开始嵌套哈希表，你将需要一种简单的方法来从控制台中查看它们。 如果我获得最后一个哈希表，则会得到如下所示的输出，它只包含这些内容：

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

我查看这些内容的首选命令是 `ConvertTo-JSON`，因为它非常简洁，对于其他内容我经常使用 JSON。

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

即使你不知道 JSON，也应该能够看到你要查找的内容。 对于类似于这样的结构化数据，还有一个 `Format-Custom` 命令，但我还是更喜欢 JSON 视图。

## <a name="creating-objects"></a>创建对象

有时，只需有一个对象，而使用哈希表保存属性无法达到目的。 最常见的情况是，你想要将键视为列名。 `pscustomobject` 会让这变得简单。

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

即使最初并未将其创建为 `pscustomobject`，也可以在以后需要时对其进行强制转换。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

我已经为 [pscustomobject][] 撰写了详细的内容，你可以在读完本文后阅读。 它建立在我们在这里学习的很多内容之上。

## <a name="reading-and-writing-hashtables-to-file"></a>在文件中读取和写入哈希表

### <a name="saving-to-csv"></a>保存到 CSV

将哈希表保存到 CSV 是我上面提到的难题之一。 将哈希表转换为 `pscustomobject`，它将正确保存到 CSV。 如果你从 `pscustomobject` 开始，这会很有帮助，这样可以保留列顺序。 但如果需要，可以将其强制转换为 `pscustomobject` 内联。

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

同样，请查看我撰写的关于使用 [pscustomobject][] 的文章。

### <a name="saving-a-nested-hashtable-to-file"></a>将嵌套哈希表保存到文件

如果需要将嵌套哈希表保存到文件，然后再次将其读入，我会使用 JSON cmdlet。

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

此方法有两个重要方面。 首先，JSON 采用多行编写，因此我需要使用 `-Raw` 选项将其读回到单个字符串中。 其次，导入的对象不再是 `[hashtable]`。 它现在是 `[pscustomobject]`，如果你不希望是这样，可能会导致问题。

观察深度嵌套的哈希表。 将其转换为 JSON 时，可能无法获得预期结果。

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

使用 Depth 参数，确保已展开所有嵌套的哈希表。

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

如果需要在导入时为 `[hashtable]`，则需要使用 `Export-CliXml` 和 `Import-CliXml` 命令。

### <a name="converting-json-to-hashtable"></a>将 JSON 转换为哈希表

如果需要将 JSON 转换为 `[hashtable]`，我知道有一种方法可以使用 .NET 中的 [JavaScriptSerializer][] 实现此目的。

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

从 PowerShell v6 开始，JSON 支持使用了 NewtonSoft JSON.NET ，并添加了哈希表支持。

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

PowerShell 6.2 向 `ConvertFrom-Json` 添加了 Depth 参数。 Depth 的默认值为 1024。

### <a name="reading-directly-from-a-file"></a>直接从文件读取

如果你有一个使用 PowerShell 语法包含哈希表的文件，那么可以直接导入它。

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

它会将文件的内容导入 `scriptblock`，然后在执行之前进行检查以确保它没有任何其他 PowerShell 命令。

在这种情况下，你是否知道模块清单（psd1 文件）只是一个哈希表？

## <a name="keys-can-be-any-object"></a>键可以是任何对象

大多数情况下，键只是字符串。 这样，我们就可以给任何内容加上引号，并使其成为一个键。

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

可以做一些你可能没意识到你可以做的奇怪操作。

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

仅仅因为你能做某事，并不意味着你应该去做。 最后一个看起来就像是一个等待发生的 bug，很容易被读你代码的人误解。

从技术上说，你的键不一定是字符串，但如果你只使用字符串，就更容易考虑。 但是，索引不适合用于复杂的键。

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

按值的键访问哈希表中的值并非始终适用。 例如：

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

如果键为数组，则必须将 `$key` 变量包装在子表达式中，使其可与成员访问 (`.`) 表示法一起使用。 也可使用数组索引 (`[]`) 表示法。

## <a name="use-in-automatic-variables"></a>在自动变量中使用

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters][] 是只存在于函数上下文中的自动变量。
它包含调用函数时所用的所有参数。 这并不是确切的哈希表，但足够接近，可以将其视为一个哈希表。

这包括删除键并将其展开到其他函数。 如果你发现自己正在编写代理函数，请仔细查看这个函数。

有关更多详细信息，请参阅 [about_Automatic_Variables][]。

### <a name="psboundparameters-gotcha"></a>PSBoundParameters 难点

需要注意的一个重要事项是，它只包括作为参数传入的值。 如果你还具有使用默认值但不是由调用方传入的参数，则 `$PSBoundParameters` 不包含这些值。 这一点通常会被忽略。

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

使用这个自动变量可以将默认值分配给任何 cmdlet，而无需更改 cmdlet。
请查看下面的例子。

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

这会将一个条目添加到 `$PSDefaultParameterValues` 哈希表中，该哈希表将 `UTF8` 设置为 `Out-File -Encoding` 参数的默认值。 这是特定于会话的，因此应将其放在 `$profile` 中。

我经常使用此变量来预分配我经常键入的值。

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

此变量也接受通配符，以便你可以批量设置值。 下面是一些可以使用的方法：

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

有关更深入的详细信息，请参阅 [Michael Sorens][] 撰写的关于[自动默认值][]的精彩文章。

## <a name="regex-matches"></a>正则表达式 $Matches

使用 `-match` 运算符时，将创建一个名为 `$matches` 的自动变量，其中包含匹配项的结果。 如果正则表达式中包含任何子表达式，还会列出这些子匹配项。

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>命名匹配项

这是我最喜欢的功能之一，但大多数人却不知道。 如果使用命名正则表达式匹配项，则可以按名称对匹配项进行访问。

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

在上面的示例中，`(?<Name>.*)` 是一个命名的子表达式。 然后，此值将被放入 `$Matches.Name` 属性。

## <a name="group-object--ashashtable"></a>Group-Object -AsHashtable

`Group-Object` 的一个鲜为人知的功能是，它可以将一些数据集转换为哈希表。

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

这会将每一行都添加到哈希表中，并使用指定的属性作为键来访问它。

## <a name="copying-hashtables"></a>复制哈希表

需要注意的一个重要事项是哈希表是对象。 每个变量只是对对象的引用。 这意味着，生成哈希表的有效副本需要完成更多的工作。

### <a name="assigning-reference-types"></a>分配引用类型

如果有一个哈希表并将其分配给第二个变量，则这两个变量都指向同一哈希表。

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

这强调了它们是相同的，因为更改一个哈希表中的值也会更改另一个中的值。 这也适用于将哈希表传递到其他函数的情况。 如果这些函数对该哈希表进行了更改，则原始哈希表也会更改。

### <a name="shallow-copies-single-level"></a>卷影副本，单一级别

如果我们有一个上例所示的简单哈希表，则可以使用 `.Clone()` 进行卷影复制。

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

这样，我们就可以对其中一个进行一些基本更改而不影响另一个。

### <a name="shallow-copies-nested"></a>卷影副本，嵌套

之所以称为卷影副本是因为它只复制基本级别的属性。 如果其中一个属性是引用类型（如其他哈希表），则这些嵌套对象仍将指向彼此。

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

你可以看到，即使克隆了哈希表，也不会克隆对 `person` 的引用。 我们需要进行深层复制，确保第二个哈希表未链接到第一个哈希表。

### <a name="deep-copies"></a>深层副本

可以通过几种方式来生成哈希表的深层副本（并将其保存为哈希表）。 下面是使用 PowerShell 以递归方式创建深层副本的函数：

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

它不会处理任何其他引用类型或数组，但它是一个很好的起点。

另一种方法是使用 .Net 对其进行反序列化，方法是使用 CliXml，如此函数中所示：

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

对于非常大的哈希表，反序列化函数的速度更快，因为它横向扩展。然而，使用此方法时需要考虑一些事项。 由于它使用 CliXml，因此会占用大量内存，如果克隆大型哈希表，这可能是一个问题。 CliXml 的另一个限制是深度限制为 48。 也就是说，如果你有一个包含 48 层嵌套哈希表的哈希表，则克隆将失败，并且根本不会输出任何哈希表。

## <a name="anything-else"></a>任何其他内容？

我已经快速介绍了很多内容。 希望你每次阅读本文时都能学到新知识或有新的理解。 因为我介绍了此功能的全部内容，所以有些方面现在可能不适合你。 这完全正常并且是意料之中，具体况取决于你对 PowerShell 的使用程度。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[哈希表]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[数组]: /powershell/module/microsoft.powershell.core/about/about_arrays
[如果性能很重要，请对其进行测试]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[展开]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[自动默认值]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
