---
description: 描述在 PowerShell 中比较值的运算符。
Locale: en-US
ms.date: 02/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: bab5ec020a51584572d1a3e4e3731bcf9bee6732
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685994"
---
# <a name="about-comparison-operators"></a>关于比较运算符

## <a name="short-description"></a>简短说明

PowerShell 中的比较运算符可以将集合的两个值或筛选元素与输入值进行比较。

## <a name="long-description"></a>长说明

比较运算符使您可以比较值或查找与指定模式匹配的值。 PowerShell 包含以下比较运算符：

|    类型     |   运算符   |              比较测试              |
| ----------- | ------------ | ----------------------------------------- |
| 等式    | -eq          | equals                                    |
|             | -ne          | 不等于                                |
|             | -gt          | 大于                              |
|             | -ge          | 大于或等于                     |
|             | -lt          | 小于                                 |
|             | -le          | 小于或等于                        |
| Matching    | -like        | 字符串与通配符模式匹配           |
|             | -notlike     | 字符串不匹配通配符模式    |
|             | -match       | 字符串匹配正则表达式模式              |
|             | -notmatch    | 字符串不匹配 regex 模式       |
| 替代功能 | -replace     | 替换匹配正则表达式模式的字符串 |
| Containment | -contains    | 集合包含值               |
|             | -notcontains | 集合不包含值       |
|             | -in          | 值在集合中                  |
|             | -notin       | 值不在集合中              |
| 类型        | -为          | 这两个对象属于同一类型            |
|             | -isnot       | 对象的类型不同         |

## <a name="common-features"></a>常用功能

默认情况下，所有比较运算符都不区分大小写。 若要使比较运算符区分大小写，请在 `c` 后面添加一个 `-` 。 例如， `-ceq` 是的区分大小写的版本 `-eq` 。 若要进行不区分大小写的显式，请 `i` 在前面添加 `-` 。 例如， `-ieq` 是的显式不区分大小写的版本 `-eq` 。

当运算符的输入是标量值时，运算符将返回一个 **布尔** 值。 当输入为集合时，运算符将返回与表达式的右侧值匹配的集合的元素。
如果集合中没有匹配项，则比较运算符返回空数组。 例如：

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

有几个例外情况：

- 包含和类型运算符始终返回 **布尔** 值
- `-replace`运算符返回替换结果
- `-match`和 `-notmatch` 运算符还填充 `$Matches` 自动变量

## <a name="equality-operators"></a>相等运算符

### <a name="-eq-and--ne"></a>-eq 和 -ne

左侧为标量时， `-eq` 如果右侧是完全匹配，则返回 **True** ，否则返回 `-eq` **False**。 `-ne` 相反;当双方均匹配时，它将返回 **False** ;否则， `-ne` 返回 True。

示例：

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

如果左侧是集合，则 `-eq` 返回与右侧匹配的成员，同时对 `-ne` 其进行筛选。

示例：

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

这些运算符处理集合的所有元素。 示例：

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

相等运算符接受任意两个对象，而不只是标量或集合。
但不保证比较结果对于最终用户有意义。
下面的示例演示了该问题。

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

在此示例中，我们创建了两个具有相同属性的对象。 然而，相等性测试结果为 **False** ，因为它们是不同的对象。 若要创建可比较类，需要在类中实现[IEquatable \<T> ][2] 。 下面的示例演示了实现 [IEquatable \<T>][2]的 **MyFileInfoSet** 类的分部实现，它具有两个属性：**文件** 和 **大小**。 `Equals()`如果两个 **MyFileInfoSet** 对象的文件和大小属性相同，则该方法返回 True。

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

比较任意对象的一个明显示例就是找出这些对象是否为 null。 但如果需要确定变量是否为 `$null` ，则必须将置于 `$null` 相等运算符的左侧。 将其放在右侧不会执行所需的操作。

例如，假设 `$a` 数组包含 null 元素：

```powershell
$a = 1, 2, $null, 4, $null, 6
```

以下 `$a` 不为空的测试。

```powershell
$null -ne $a
```

```output
True
```

不过，以下是从以下文件中注销所有 null 元素 `$a` ：

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a>-gt、-ge、-lt 和-le

`-gt`、 `-ge` 、 `-lt` 和的 `-le` 行为与此类似。 当双方都为标量时，它们会返回 **True** 或 **False** ，具体取决于两个边的比较方式：

| 运算符 | 当 .。。                   |
| -------- | -------------------------------------- |
| -gt      | 左侧更大          |
| -ge      | 左侧大于或等于 |
| -lt      | 左侧更小          |
| -le      | 左侧小于或等于 |

在下面的示例中，所有语句都返回 True。

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> 在大多数编程语言中，大于运算符为 `>` 。 在 PowerShell 中，此字符用于重定向。 有关详细信息，请参阅 [about_Redirection][3]。

如果左侧是集合，则这些运算符会将集合的每个成员与右侧进行比较。 根据其逻辑，它们可以保留或丢弃成员。

示例：

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

这些运算符可用于实现 [system.icomparable][1]的任何类。

示例：

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

下面的示例演示在美国标准键盘上没有符号，该键盘在 "a" 后进行排序。 它将包含所有此类符号的集馈送到 `-gt` 运算符，以将它们与 "a" 进行比较。 输出为空数组。

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

如果两个运算符的两边不合理，则这些运算符将引发非终止错误。

## <a name="matching-operators"></a>匹配运算符

匹配运算符 (`-like` 、 `-notlike` 、 `-match` 和 `-notmatch`) 查找匹配或与指定模式不匹配的元素。 和的模式 `-like` `-notlike` 是包含 `*` 、和)  (通配符表达式 `?` `[ ]` ， `-match` 并 `-notmatch` 接受正则表达式 (正则表达式) 。

语法为：

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

当这些运算符的输入是标量值时，它们将返回一个 **布尔** 值。 当输入是值的集合时，运算符返回任何匹配的成员。 如果集合中没有匹配项，则运算符将返回空数组。

### <a name="-like-and--notlike"></a>-like 和-notlike

`-like` 和 `-notlike` 的行为与 `-eq` 和类似 `-ne` ，但右侧可以是包含 [通配符](about_Wildcards.md)的字符串。

示例：

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a>-match 和-notmatch

`-match` 和 `-notmatch` 使用正则表达式搜索左侧值中的模式。 正则表达式可以匹配复杂模式，如电子邮件地址、UNC 路径或格式化电话号码。 右侧字符串必须符合 [正则表达式](about_Regular_Expressions.md) 规则。

标量示例：

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

如果输入是集合，则运算符将返回该集合的匹配成员。

集合示例：

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

`-match` 和 `-notmatch` 支持 regex 捕获组。 每次运行时，它们将覆盖 `$Matches` 自动变量。 当 `<input>` 是集合时， `$Matches` 变量是 `$null` 。 `$Matches` 是始终具有名为 "0" 的键的 **哈希表** ，它存储整个匹配项。 如果正则表达式包含捕获组，则 `$Matches` 包含每个组的其他键。

示例：

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

有关详细信息，请参阅 [about_Regular_Expressions](about_Regular_Expressions.md)。

## <a name="replacement-operator"></a>替换运算符

### <a name="replacement-with-regular-expressions"></a>用正则表达式替换

与类似 `-match` ， `-replace` 运算符使用正则表达式查找指定的模式。 但与不同的 `-match` 是，它将匹配项替换为另一个指定的值。

语法：

```
<input> -replace <regular-expression>, <substitute>
```

使用正则表达式将运算符替换为指定值的全部或部分值。 对于许多管理任务（如重命名文件），都可以使用运算符。 例如，以下命令将所有文件的文件扩展名更改 `.txt` 为 `.log` ：

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

默认情况下， `-replace` 运算符不区分大小写。 若要区分大小写，请使用 `-creplace` 。 若要使它显式不区分大小写，请使用 `-ireplace` 。

示例：

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a>正则表达式替换

还可以使用正则表达式，使用捕获组和替换动态替换文本。 可以 `<substitute>` 使用分组标识符之前的美元符号 () 字符，在字符串中引用捕获组 `$` 。

在下面的示例中， `-replace` 运算符接受格式为的用户名， `DomainName\Username` 并将转换为以下 `Username@DomainName` 格式：

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> 该 `$` 字符具有 PowerShell 和正则表达式中的 syntatic 角色：
>
> - 在 PowerShell 中，在双引号之间，它指定变量并充当子表达式运算符。
> - 在正则表达式搜索字符串中，它表示行的结尾
> - 在 Regex 替换字符串中，它表示捕获的组。请确保将正则表达式放在单引号之间，或 `` ` `` 在它们之前插入反撇号 () 字符。

例如：

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

`$$` 在正则表达式中表示文字 `$` 。 此 `$$` 在替换字符串中，以 `$` 在生成的替换中包含文本。 例如：

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

若要了解详细信息，请参阅[正则表达式中的][4] [about_Regular_Expressions](about_Regular_Expressions.md)和替换。

### <a name="substituting-in-a-collection"></a>在集合中替换

如果 `<input>` 到运算符为 `-replace` 集合，则 PowerShell 会将替换应用于集合中的每个值。 例如：

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a>使用脚本块替换

在 PowerShell 6 及更高版本中， `-replace` 操作员还接受执行替换的脚本块。 脚本块为每个匹配项运行一次。

语法：

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

在脚本块中，使用 `$_` 自动变量来访问被替换的输入文本和其他有用的信息。 此变量的类类型为 [system.text.regularexpressions][2]。

下面的示例将三个数字的每个序列替换为等效字符。 脚本块针对需要替换的三个数字组运行。

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a>包含运算符

包含运算符 (`-contains` 、 `-notcontains` 、 `-in` 和 `-notin`) 与相等运算符类似，不同之处在于它们始终返回一个 **布尔** 值，即使输入是集合也是如此。 这些运算符在检测到第一个匹配项后会立即停止比较，而相等运算符则计算所有输入成员。 在非常大的集合中，这些运算符返回的速度比相等运算符更快。

语法：

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a>-contains 和-notcontains

这些运算符用于判断集是否包含特定元素。 `-contains` 当右侧 (测试对象) 与集中的元素之一匹配时，返回 True。 `-notcontains` 改为返回 False。 如果测试对象是集合，则这些运算符使用引用相等性，即，它们检查其中一个集合的元素是否为测试对象的相同实例。

示例：

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

更复杂的示例：

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a>-in 和-notin

`-in`和- `notin` 运算符在 PowerShell 3 中引入，作为和运算符的语法反转 `contains` `-notcontain` 。 `-in`当左侧 `<test-object>` 与集中的元素之一匹配时，返回 True。 `-notin` 改 **为返回 False** 。 如果测试对象是一个集，则这些运算符使用引用相等性来检查该集的一个元素是否为该测试对象的相同实例。

下面的示例执行与示例相同的操作 `-contain` `-notcontain` ，但它们是用和编写的 `-in` `-notin` 。

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

更复杂的示例：

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a>类型比较

 (和) 的类型比较运算符 `-is` `-isnot` 用于确定对象是否为特定类型。

语法：

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

例如：

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a>另请参阅

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-对象](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
