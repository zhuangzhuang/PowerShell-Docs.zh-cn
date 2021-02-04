---
title: 关于 PSCustomObject 的各项须知内容
description: PSCustomObject 是创建结构化数据的一种简单方法。
ms.date: 10/05/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 8086541bf93b4d3f878c9a3f7ca4300dc452a80b
ms.sourcegitcommit: 08c63095f54916013634d6703f2523779815f4b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "99424468"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>关于 PSCustomObject 的各项须知内容

`PSCustomObject` 是一个可添加到 PowerShell 工具包中的绝佳工具。 让我们从基本功能开始，然后深入了解更高级的功能。 使用 `PSCustomObject` 背后的理念是，通过一种简单的方法来创建结构化数据。 查看第一个示例，可以更好地了解其含义。

> [!NOTE]
> 本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。 PowerShell 团队感谢 Kevin 与我们分享这篇文章。 请前往 [PowerShellExplained.com][] 访问他的博客。

## <a name="creating-a-pscustomobject"></a>创建 PSCustomObject

我喜欢在 PowerShell 中使用 `[PSCustomObject]`。 创建可用对象变得前所未有的容易。
因此，我将跳过所有其他创建对象的方法，但需要注意的是，大多数示例都采用 PowerShell v3.0 和更高版本。

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

这种方法非常适合我，因为我几乎把哈希表用到了所有事上。 但有时，我更希望 PowerShell 将哈希表视为一个对象。 当你想要使用 `Format-Table` 或 `Export-CSV` 并且意识到哈希表只是键/值对的集合时，你最先会注意到这种差异。

然后，你可以像访问普通对象一样访问和使用这些值。

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>转换哈希表

在谈到这个主题时，你是否知道你可以这样做：

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

我确实喜欢从头开始创建对象，但有时你必须先使用哈希表。 此示例行得通的原因是，构造函数为对象属性采用了哈希表。 一个重要的注意事项是，虽然此方法有效，但并不完全等同。 最大的区别在于属性的顺序不会得到保留。

### <a name="legacy-approach"></a>传统方法

你可能见过人们使用 `New-Object` 来创建自定义对象。

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

这种方式比较慢，但在 PowerShell 早期版本上可能是最佳选择。

### <a name="saving-to-a-file"></a>保存到文件

我发现将哈希表保存到文件的最佳方法是将其保存为 JSON。 可以将其导入回 `[PSCustomObject]`

```powershell
$myObject | ConvertTo-Json -depth 1 | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

我在[读取和写入文件的多种方式][]一文中介绍了将对象保存到文件的更多方法。

## <a name="working-with-properties"></a>使用属性

### <a name="adding-properties"></a>添加属性

你仍可以使用 `Add-Member` 将新属性添加到 `PSCustomObject`。

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name 'ID' -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>删除属性

你还可以从对象中删除属性。

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject` 是隐藏属性，它允许你访问基对象元数据。

### <a name="enumerating-property-names"></a>枚举属性名称

有时需要对象上所有属性名称的列表。

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

我们也可以从 `psobject` 属性获取此列表。

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>动态访问属性

我曾提到过，你可以直接访问属性值。

```powershell
$myObject.Name
```

你可以使用字符串作为属性名称，它仍可正常工作。

```powershell
$myObject.'Name'
```

我们可以再执行一步，使用变量作为属性名称。

```powershell
$property = 'Name'
$myObject.$property
```

我知道这看起来很奇怪，但确实有效。

### <a name="convert-pscustomobject-into-a-hashtable"></a>将 PSCustomObject 转换为哈希表

要从上一节继续操作，可以动态地遍历属性并从中创建一个哈希表。

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>测试属性

如果需要知道属性是否存在，只需检查该属性是否有值。

```powershell
if( $null -ne $myObject.ID )
```

但如果值可以是 `$null`，则可以通过检查它的 `psobject.properties` 来查看其是否存在。

```powershell
if( $myobject.psobject.properties.match('ID').Count )
```

## <a name="adding-object-methods"></a>添加对象方法

如果需要将脚本方法添加到对象，则可以使用 `Add-Member` 和 `ScriptBlock` 执行此操作。 必须使用 `this` 自动变量引用当前对象。 下面是将对象转换为哈希表的 `scriptblock`。 （上一个示例中的相同代码）

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

然后，将其作为脚本属性添加到对象。

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

接下来，我们可以调用函数，如下所示：

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>对象与值类型

对象和值类型不会以相同的方式处理变量赋值。 如果互相分配值类型，则只有值会复制到新变量。

```powershell
$first = 1
$second = $first
$second = 2
```

在这种情况下，`$first` 为 1，`$second` 为 2。

对象变量具有对实际对象的引用。 将一个对象分配给新变量时，它们仍引用同一个对象。

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

由于 `$third` 和 `$fourth` 引用对象的同一实例，因此 `$third.key` 和 `$fourth.Key` 均为 4。

### <a name="psobjectcopy"></a>psobject.copy()

如果需要对象的真正副本，可以对其进行克隆。

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

通过克隆可创建对象的卷影副本。 它们现在具有不同的实例，在本示例中，`$third.key` 为 3，`$fourth.Key` 为 4。

由于嵌套了对象，我将其称为卷影副本。 （其中，属性包含其他对象）。 仅复制顶级值。 子对象将相互引用。

### <a name="pstypename-for-custom-object-types"></a>自定义对象类型的 PSTypeName

既然我们有了一个对象，我们还可以用它做一些可能不那么显而易见的事情。 第一件事就是为它指定 `PSTypeName`。 以下是我看到的最常用的方法：

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

我最近从 [/u/markekraus 的这篇文章][]中发现了执行此操作的另一种方法。 我进行了一点挖掘，并阅读了 [Adam Bertram][] 和 [Mike Shepard][] 有关此观点的多篇文章，他们在其中谈到了这种允许以内联方式进行定义的方法。

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

这刚好适用于这种语言，我很喜欢。 现在，我们有了一个具有正确类型名称的对象，接下来可以做更多工作。

> [!NOTE]
> 还可以使用 PowerShell 类创建自定义 PowerShell 类型。 有关详细信息，请参阅 [PowerShell 类概述](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes)。

## <a name="using-defaultpropertyset-the-long-way"></a>使用 DefaultPropertySet（绕远路）

PowerShell 为我们决定默认情况下显示哪些属性。 很多本机命令都有一个可以完成所有繁重工作的 `.ps1xml`[格式化文件][]。 [Boe Prox 的文章][]为我们提供了只需使用 PowerShell 即可在自定义对象上执行此操作的另一种方法。 我们可以提供一个 `MemberSet` 供其使用。

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet('DefaultDisplayPropertySet',[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

现在，当我的对象刚好落到 shell 上时，默认情况下它将仅显示这些属性。

### <a name="update-typedata-with-defaultpropertyset"></a>带有 DefaultPropertySet 的 Update-TypeData

这很不错，但我最近在观看 [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged] 时，发现了一种更好的方法。 Jeffrey 使用 [Update-TypeData][] 来指定默认属性。

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

这非常简单，即使我没有此文章作为快速参考，也差不多能记住它。 现在，我可以轻松地创建具有很多属性的对象，并在从 shell 中查看时，为其提供一个干净清爽的视图。 如果需要访问或查看其他属性，也可以在那里看到。

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>带有 ScriptProperty 的 Update-TypeData

我从该视频中还学习到了如何为你的对象创建脚本属性。 借此机会可以指明，这也适用于现有对象。

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

你可以在创建对象之前或之后执行此操作，它仍可正常工作。 这就是将 `Add-Member` 与脚本属性一起使用带来的不同之处。 当你通过我前面提及的方式使用 `Add-Member` 时，它只存在于对象的特定实例上。 此方法适用于具有此 `TypeName` 的所有对象。

## <a name="function-parameters"></a>函数参数

你现在可以在函数和脚本中对参数使用这些自定义类型。 可以让一个函数创建这些自定义对象，然后将它们传递到其他函数。

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell 要求对象是你指定的类型。 如果该类型不能自动匹配，则会引发验证错误，从而省去你在代码中执行测试的步骤。 这是让 PowerShell 充分发挥其优势的一个优秀示例。

### <a name="function-outputtype"></a>函数 OutputType

你还可以为高级函数定义 `OutputType`。

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

OutputType 属性值只是一个文档说明。 它不是从函数代码派生的，也不与实际函数输出进行比较。

使用输出类型的主要原因是，为了让关于函数的元信息反映你的意图。 你的开发环境可以利用 `Get-Command` 和 `Get-Help` 之类。 如果需要详细信息，请查看其帮助：[about_Functions_OutputTypeAttribute][]。

也就是说，如果使用 Pester 对函数进行单元测试，最好验证输出对象与 OutputType 是否匹配。 这可能会捕获那些不应该落入管道的变量。

## <a name="closing-thoughts"></a>结束语

本文的上下文都与 `[PSCustomObject]` 相关，但许多信息都适用于一般对象。

我以前看到过其中的大部分功能，但从未见过它们作为 `PSCustomObject` 上的信息集合呈现。 就在上周，我偶然看到了另一个，我很吃惊之前从未见过它。 我希望将所有这些想法集中在一起，让你有更全面的了解，并在有机会用到它们时能想起来。 希望你学有所获，并能够找到一种方法将其用在自己的脚本中。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox 的文章]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[格式化文件]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[读取和写入文件的多种方式]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[/u/markekraus 的这篇文章]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
