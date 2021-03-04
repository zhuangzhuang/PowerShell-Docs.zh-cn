---
title: 关于 switch 语句的各项须知内容
description: PowerShell 中的 switch 语句提供了其他语言没有的功能。
ms.date: 03/01/2021
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: f6baa624285557452a2b95150b2c4de1ab274f27
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686009"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>关于 switch 语句的各项须知内容

与许多其他语言一样，PowerShell 具有用于控制脚本内执行流的命令。 其中一个语句是 [switch][] 语句，在 PowerShell 中，它提供了其他语言没有的功能。 今天，我们将深入探讨如何使用 PowerShell `switch`。

> [!NOTE]
> 本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。 PowerShell 团队感谢 Kevin 与我们分享这篇文章。 请前往 [PowerShellExplained.com][] 访问他的博客。

## <a name="the-if-statement"></a>`if` 语句

你最先学习的语句之一是 `if` 语句。 如果语句为 `$true`，则允许执行脚本块。

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

可以通过使用 `elseif` 和 `else` 语句来获得更复杂的逻辑。 下面是一个示例：我有一个星期的数字值，想要获取字符串形式的名称。

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

事实证明，这是一种常见模式，可以通过多种方法来实现。 其中一种方法是使用 `switch`。

## <a name="switch-statement"></a>Switch 语句

`switch` 语句允许你提供一个变量和一列可能值。 如果值与变量匹配，则将执行其脚本块。

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

在本例中，`$day` 的值与其中一个数值匹配，然后正确的名称即会分配给 `$result`。 我们在本例中只进行了变量赋值，但任何 PowerShell 都可以在这些脚本块中执行。

### <a name="assign-to-a-variable"></a>给变量赋值

我们可以通过另一种方法编写上一个示例。

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

我们将该值置于 PowerShell 管道上，并将其赋给 `$result`。 可以使用 `if` 和 `foreach` 语句执行相同的操作。

### <a name="default"></a>默认

我们可以使用 `default` 关键字来确定没有匹配项时应发生的情况。

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

默认情况下，返回值 `Unknown`。

### <a name="strings"></a>字符串

我在上述几个示例中匹配的都是数字，但你也可以匹配字符串。

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

我决定在这里不把 `Component`、`Role` 和 `Location` 匹配项括在引号中，以突出它们是可选的。 在大多数情况下，`switch` 会将它们视为字符串。

## <a name="arrays"></a>数组

PowerShell `switch` 的一项优异功能体现在处理数组的方式上。 如果向数组提供一个 `switch`，它会处理集合中的每个元素。

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

如果数组中有重复项，则相应的部分会对它们进行多次匹配。

### <a name="psitem"></a>PSItem

可以使用 `$PSItem` 或 `$_` 来引用已处理的当前项。 当我们执行简单匹配时，`$PSItem` 是我们要匹配的值。 在下一部分中使用这个变量时，我将执行一些高级匹配。

## <a name="parameters"></a>参数

PowerShell `switch` 的一项独特特性是它有许多可更改其执行方式的开关参数。

### <a name="-casesensitive"></a>-CaseSensitive

默认情况下，匹配项不区分大小写。 如果需要区分大小写，可以使用 `-CaseSensitive`。 这可以与其他开关参数结合使用。

### <a name="-wildcard"></a>-Wildcard

可以使用 `-wildcard` 开关启用通配符支持。 这会使用与 `-like` 运算符相同的通配符逻辑来执行每次匹配。

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

在这里我们正处理一条消息，然后根据内容将其输出到不同的流中。

### <a name="-regex"></a>-Regex

switch 语句支持正则表达式匹配，就像支持通配符一样。

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

在我撰写的另一篇文章中有更多使用正则表达式的示例：[使用正则表达式的多种方式][]。

### <a name="-file"></a>-File

switch 语句的一个鲜为人知的功能是，它可以使用 `-File` 参数处理文件。 将 `-file` 与文件路径结合使用，而不是向其提供变量表达式。

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

它的工作方式就像处理数组一样。 在本例中，我将它与通配符匹配结合使用，并使用了 `$PSItem`。 这会处理日志文件，并根据正则表达式匹配情况将其转换为警告消息和错误消息。

## <a name="advanced-details"></a>高级详细信息

现在，你已经了解了所有这些记录在案的功能，我们可以在更高级处理的上下文中使用它们。

### <a name="expressions"></a>表达式

`switch` 可以在表达式上，而不是变量上。

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

表达式的计算结果均为用于匹配的值。

### <a name="multiple-matches"></a>多个匹配

你可能已经了解了这一点，但 `switch` 可以匹配多个条件。 当使用 `-wildcard` 或 `-regex` 匹配时，尤其如此。 可以多次添加同一条件，且所有条件都会被触发。

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

这三个语句都会触发。 这表明每个条件都处于选中状态（按顺序）。 这适用于处理每个项检查每个条件的数组。

### <a name="continue"></a>继续

通常，我会在这里介绍 `break` 语句，但最好先了解如何使用 `continue`。 正如 `foreach` 循环一样，`continue` 会继续进行到集合中的下一项，如果没有其他项，则会退出 `switch`。 我们可以使用 continue 语句重写上一个示例，以便仅执行一个语句。

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

匹配第一个项，然后 switch 继续处理下一个值，而不是匹配所有三个项。 由于没有要处理的值了，因此 switch 将退出。 下一个示例演示通配符如何与多个项匹配。

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

因为输入文件中的一行可能同时包含单词 `Error` 和 `Warning`，所以我们只希望执行第一个，然后继续处理文件。

### <a name="break"></a>中断

`break` 语句可退出 switch。 这与 `continue` 对单个值的行为表现相同。 差异会在处理数组时显示出来。 `break` 会停止 switch 中的所有处理，而 `continue` 会继续进行到下一项。

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

在这种情况下，如果点击以 `Error` 开头的任何行，则会出现错误，并且 switch 将停止。
这就是 `break` 语句的作用。 如果在字符串内（而不只是在开头）找到 `Error`，则将其编写为警告。 对于 `Warning` 也是如此。 一行中可能同时包含单词 `Error` 和 `Warning`，但我们只需处理一个。 这就是 `continue` 语句的作用。

### <a name="break-labels"></a>中断标签

`switch` 语句支持 `break/continue` 标签，就像 `foreach` 一样。

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

我个人不喜欢使用中断标签，之所以提及的原因是，如果你之前从未见过它们，可能会感到困惑。 如果有多个嵌套的 `switch` 或 `foreach` 语句，则可能需要中断的不只是最内层的项。 可以在 `switch` 上放置一个标签，作为 `break` 的目标。

### <a name="enum"></a>枚举

PowerShell 5.0 为我们提供了可以在 switch 中使用的枚举。

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

如果要将所有内容保持为强类型枚举，则可以将其放在圆括号中。

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

此处需要圆括号，以便 switch 不会将值 `[Context]::Location` 视为文本字符串。

### <a name="scriptblock"></a>脚本块

如果需要，我们可以使用脚本块来执行匹配的计算。

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

这会增加复杂性，并且会使 `switch` 很难读。 在大多数情况下，使用类似语句时，最好使用 `if` 和 `elseif` 语句。 如果已经有一个较大的 switch，并且需要两个项来命中同一计算块，我会考虑使用这个。

我认为有助于增强可读性的一点是，将脚本块放在圆括号内。

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

它仍以相同的方式执行，并在快速查看时提供更好的视觉中断。

### <a name="regex-matches"></a>正则表达式 $matches

我们需要重新讨论正则表达式，以触及一些不太明显的内容。 使用正则表达式可填充 `$matches` 变量。 当我谈到[使用正则表达式的多种方式][]时，我确实更多地谈到了 `$matches` 的使用。 下面是一个快速示例，演示了使用命名匹配项时的情况。

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

你可以匹配一个不一定是默认值的 `$null` 值。

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

对于空字符串也是如此。

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>常数表达式

Lee Dailey 指出，我们可以使用恒定的 `$true` 表达式来计算 `[bool]` 项。
假设我们需要进行几个布尔值检查。

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

这是对若干个布尔字段的状态进行计算和执行操作的简便方法。 这样做的好处是，可以让一个匹配翻转尚未计算的值的状态。

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

在本例中，将 `$isEnabled` 设置为 `$true` 可确保 `$isVisible` 也设置为 `$true`。 然后，在计算 `$isVisible` 时，将调用其脚本块。 这有点违反直觉，但却是对机制的巧妙使用。

### <a name="switch-automatic-variable"></a>$switch 自动变量

当 `switch` 处理其值时，将创建枚举器并称其为 `$switch`。 这是由 PowerShell 创建的自动变量，你可以直接对其进行操作。

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

这会为你提供以下结果：

```Output
2
4
```

向前移动枚举器，`switch` 不会处理下一项，但你可以直接访问该值。 我称之为发疯。

## <a name="other-patterns"></a>其他模式

### <a name="hashtables"></a>哈希表

我最受欢迎的文章之一是关于[哈希表][]的。 `hashtable` 的用例之一是作为查找表使用。 这是 `switch` 语句通常处理的常见模式的一种替代方法。

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

如果只是将 `switch` 用作查找，那么我通常会改用 `hashtable`。

### <a name="enum"></a>枚举

PowerShell 5.0 引入了 `Enum`，在这种情况下，它也是一个选项。

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

我们会一直寻找不同的方法来解决此问题。 我只是想确定你知道你拥有选择。

## <a name="final-words"></a>结束语

switch 语句表面上看起来很简单，但它提供了一些大多数人都不知道的高级功能。 这些功能结合在一起使它非常强大。 我希望你学到了一些之前不知道的内容。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[使用正则表达式的多种方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[哈希表]: everything-about-hashtable.md
