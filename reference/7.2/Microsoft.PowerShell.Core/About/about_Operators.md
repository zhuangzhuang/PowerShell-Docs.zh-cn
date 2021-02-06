---
description: 描述 PowerShell 支持的运算符。
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: c3884c7fc6c45e52ac9bccbe6c016908c242b8ef
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597433"
---
# <a name="about-operators"></a>关于运算符

## <a name="short-description"></a>简短说明
描述 PowerShell 支持的运算符。

## <a name="long-description"></a>长说明

运算符是可在命令或表达式中使用的语言元素。
PowerShell 支持多种类型的运算符来帮助您操作值。

### <a name="arithmetic-operators"></a>算术运算符

使用算术运算符 (`+` 、 `-` 、 `*` 、 `/` `%`) 计算命令或表达式中的值。 使用这些运算符，可以添加、减、乘或相除值，计算除法运算的余数 (模数) 。

加法运算符用于连接元素。 乘法运算符返回每个元素的指定数量的副本。 可以对任何实现它们的 .net 类型使用算术运算符，例如： `Int` 、 `String` 、 `DateTime` 、 `Hashtable` 和数组。

按位运算符 (`-band` 、、、、 `-bor` `-bxor` `-bnot` `-shl` `-shr`) 处理值中的位模式。

有关详细信息，请参阅 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)。

### <a name="assignment-operators"></a>赋值运算符

使用赋值运算符 (`=` 、 `+=` 、 `-=` 、 `*=` 、 `/=` 、 `%=`) 将值分配给变量或将值追加到变量。 可以将算术运算符与赋值结合使用，将算术运算的结果分配给变量。

有关详细信息，请参阅 [about_Assignment_Operators](about_Assignment_Operators.md)。

### <a name="comparison-operators"></a>比较运算符

使用比较运算符 (`-eq` 、、、、、 `-ne` `-gt` `-lt` `-le` `-ge`) 比较值和测试条件。 例如，可以比较两个字符串值，以确定它们是否相等。

比较运算符还包括用于在文本中查找或替换模式的运算符。  (`-match` 、 `-notmatch` `-replace`) 运算符使用正则表达式和 (`-like` ， `-notlike`) 使用通配符 `*` 。

包含比较运算符确定测试值是出现在引用集中， (，，， `-in` `-notin` `-contains` `-notcontains`) 。

类型比较运算符 (`-is` ， `-isnot`) 确定对象是否为给定类型。

有关详细信息，请参阅 [about_Comparison_Operators](about_Comparison_Operators.md)。

### <a name="logical-operators"></a>逻辑运算符

使用逻辑运算符 (`-and` 、 `-or` 、 `-xor` 、 `-not` `!`) 将条件语句连接到单个复杂条件。 例如，可以使用逻辑 `-and` 运算符创建具有两个不同条件的对象筛选器。

有关详细信息，请参阅 [about_Logical_Operators](about_logical_operators.md)。

### <a name="redirection-operators"></a>重定向运算符

使用重定向运算符 (`>` 、 `>>` 、 `2>` 、 `2>>` 和 `2>&1`) 将命令或表达式的输出发送到文本文件。 重定向运算符的工作方式类似于 `Out-File` 不带参数的 cmdlet () 但是，它们还允许你将错误输出重定向到指定的文件。 你还可以使用 `Tee-Object` cmdlet 来重定向输出。

有关详细信息，请参阅 [about_Redirection](about_Redirection.md)

### <a name="split-and-join-operators"></a>拆分和联接运算符

`-split`和 `-join` 运算符划分并组合子字符串。 `-split`运算符将字符串拆分为子字符串。 `-join`运算符将多个字符串串联为一个字符串。

有关详细信息，请参阅 [about_Split](about_Split.md) 和 [about_Join](about_Join.md)。

### <a name="type-operators"></a>类型运算符

使用 (，) 的类型运算符 `-is` `-isnot` `-as` 查找或更改对象的 .NET Framework 类型。

有关详细信息，请参阅 [about_Type_Operators](about_Type_Operators.md)。

### <a name="unary-operators"></a>一元运算符

使用一元运算符来递增或递减变量或对象属性，并将整数设置为正数或负数。 例如，若要将变量 `$a` 从增加 `9` 到 `10` ，请键入 `$a++` 。

### <a name="special-operators"></a>特殊运算符

特殊运算符具有不适合任何其他操作员组的特定用例。 例如，使用特殊运算符可运行命令、更改值的数据类型或从数组中检索元素。

#### <a name="grouping-operator--"></a>分组运算符 `( )`

与其他语言一样， `(...)` 用于重写表达式中的运算符优先级。 例如： `(1 + 2) / 3`

但是，在 PowerShell 中还有其他行为。

- `(...)` 允许您允许 _命令_ 的输出参与表达式。 例如：

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- 当用作管道的第一段时，用括号将命令或表达式括起来会导致表达式结果的 _枚举_ 。 如果括号环绕 _命令_，则在通过管道发送结果之前，将使用 _内存中收集_ 的所有输出运行完成。

#### <a name="subexpression-operator--"></a>子表达式运算符 `$( )`

返回一个或多个语句的结果。 对于单个结果，返回一个标量。 对于多个结果，将返回一个数组。 如果要在另一个表达式内使用表达式，请使用此表达式。 例如，要在字符串表达式中嵌入命令的结果。

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Array 子表达式运算符 `@( )`

以数组形式返回一个或多个语句的结果。 如果只有一个项，则数组只包含一个成员。

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a>哈希表文本语法 `@{}`

与 array 子表达式类似，此语法用于声明哈希表。
有关详细信息，请参阅 [about_Hash_Tables](about_Hash_Tables.md)。

#### <a name="call-operator-"></a>Call 运算符 `&`

运行命令、脚本或脚本块。 Call 运算符（也称为 "调用运算符"）允许您运行存储在变量中并由字符串或脚本块表示的命令。 调用运算符在子范围内执行。 有关范围的详细信息，请参阅 [about_Scopes](about_Scopes.md)。

此示例将命令存储在字符串中，并使用 call 运算符执行该命令。

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

调用运算符不分析字符串。 这意味着，在使用 call 运算符时，不能使用字符串中的命令参数。

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

[调用表达式](xref:Microsoft.PowerShell.Utility.Invoke-Expression)cmdlet 可执行在使用 call 运算符时导致分析错误的代码。

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

可以使用 call 运算符来执行使用其文件名的脚本。 下面的示例显示了包含空格的脚本文件名。 当你尝试执行脚本时，PowerShell 将显示包含文件名的带引号的字符串的内容。 Call 运算符用于执行包含文件名的字符串的内容。

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

有关脚本块的详细信息，请参阅 [about_Script_Blocks](about_Script_Blocks.md)。

#### <a name="background-operator-"></a>后台运算符 `&`

在 PowerShell 作业中，在后台运行管道。 此运算符的行为类似于 UNIX control 运算符 and (`&`) ，它在 subshell 中以异步方式运行命令作为作业。

此运算符在功能上等效于 `Start-Job` 。 默认情况下，后台运算符启动启动并行任务的调用方的当前工作目录中的作业。 下面的示例演示后台作业运算符的基本用法。

```powershell
Get-Process -Name pwsh &
```

此命令在功能上等同于以下用法 `Start-Job` ：

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

就像一样 `Start-Job` ， `&` 后台运算符返回 `Job` 对象。 此对象可与和一起 `Receive-Job` 使用 `Remove-Job` ，就像你已使用 `Start-Job` 来启动该作业一样。

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

`&`后台运算符也是语句终止符，就像)  (的 UNIX 控件运算符 "and" `&` 。 这允许您在后台运算符之后调用其他命令 `&` 。 下面的示例演示如何在后台运算符之后调用其他命令 `&` 。

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

这等效于以下脚本：

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

如果要运行多个命令，每个命令都在其自己的后台进程中，但全部在一行上，只需在 `&` 每个命令前后放置。

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

有关 PowerShell 作业的详细信息，请参阅 [about_Jobs](about_Jobs.md)。

#### <a name="cast-operator--"></a>Cast 运算符 `[ ]`

将对象转换或限制为指定的类型。 如果无法转换对象，PowerShell 会生成错误。

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

使用 [强制转换表示法](about_Variables.md)赋值时，还可以执行强制转换。

#### <a name="comma-operator-"></a>逗号运算符 `,`

作为二元运算符，逗号创建数组或追加到所创建的数组。 在表达式模式下，作为一元运算符，逗号创建只包含一个成员的数组。 将逗号置于成员前面。

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

由于 `Write-Object` 需要参数，因此必须将表达式放在括号中。

#### <a name="dot-sourcing-operator-"></a>网点采购运算符 `.`

在当前作用域中运行脚本，以便将脚本创建的所有函数、别名和变量添加到当前作用域中，并覆盖现有作用域。 脚本声明的参数成为变量。 未为其提供值的参数将成为没有值的变量。 但是， `$args` 会保留自动变量。

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> 点采购运算符后跟一个空格。 使用空格将点与表示当前目录的点 (`.`) 符号区分开来。
>
> 在下面的示例中，当前目录中的 Sample.ps1 脚本在当前作用域中运行。
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Format 运算符 `-f`

使用字符串对象的 format 方法格式化字符串。 在运算符的左侧输入格式字符串，并在运算符右侧输入要设置格式的对象。

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

如果需要 `{}` 在带格式的字符串中保留大括号 () ，可以通过将大括号加倍来对它们进行转义。

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

有关详细信息，请参阅 [字符串格式](/dotnet/api/system.string.format) 方法和 [复合格式设置](/dotnet/standard/base-types/composite-formatting)。

#### <a name="index-operator--"></a>Index 运算符 `[ ]`

从索引集合中选择对象，如数组和哈希表。 数组索引是从零开始的，因此第一个对象的索引为 `[0]` 。 对于仅)  (数组，还可以使用负索引来获取最后一个值。 哈希表按键值编制索引。

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a>管道运算符 `|`

将 ( "管道" ) 命令的输出发送到其后的命令。 如果输出中包含一个 "集合" )  (多个对象，则管道运算符每次发送一个对象。

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a>管道链运算符 `&&` 和 `||`

根据左侧管道的成功，有条件地执行右侧管道。

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

有关详细信息，请参阅 [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)。

#### <a name="range-operator-"></a>范围运算符 `..`

表示整数数组中的顺序整数（给定上下限）。

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

您还可以按相反的顺序创建范围。

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

从 PowerShell 6 开始，range 运算符使用 **字符** 和 **整数**。

若要创建字符范围，请将边界字符括在引号中。

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a>成员访问运算符 `.`

访问对象的属性和方法。 成员名称可以是表达式。

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>静态成员运算符 `::`

调用 .NET Framework 类的静态属性和方法。 若要查找对象的静态属性和方法，请使用 cmdlet 的静态参数 `Get-Member` 。  成员名称可以是表达式。

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a>三元运算符 `? <if-true> : <if-false>`

在简单的条件情况下，可以使用三元运算符替换 `if-else` 语句。

有关详细信息，请参阅 [about_If](about_If.md)。

#### <a name="null-coalescing-operator-"></a>Null 合并运算符 `??`

如果 null 合并运算符 `??` 不为 null，则它返回其左操作数的值。 否则，它将计算右操作数并返回其结果。 如果左操作数的计算结果为非 null，则 `??` 运算符不会计算其右操作数。

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

在下面的示例中，不会计算右侧的操作数。

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a>Null 合并赋值运算符 `??=`

`??=`如果左操作数的计算结果为 null，则 null 合并赋值运算符仅将其右操作数的值分配给其左操作数。 如果左操作数的计算结果为非 null，则 `??=` 运算符不会计算其右操作数。

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

在下面的示例中，不会计算右侧的操作数。

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a>Null 条件运算符 `?.` 和 `?[]`

> [!NOTE]
> 此功能已从实验迁移到 PowerShell 7.1 中的主流。

`?.`只有当操作数的计算结果为非 null 时，null 条件运算符才会将成员访问、或元素访问权限应用于 `?[]` 其操作数; 否则，它将返回 null。

由于 PowerShell 允许 `?` 作为变量名称的一部分，因此使用这些运算符需要变量名称的形式规范。 因此，使用 `{}` 将变量名称括起来（如 `${a}`）或 `?` 是变量名称 `${a?}` 的一部分时需要形式规范。

在下面的示例中，将返回 **PropName** 的值。

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

下面的示例将返回 null，而不会尝试访问成员名称 **PropName**。

```powershell
$a = $null
${a}?.PropName
```

同样，将返回元素的值。

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

如果操作数为 null，则不会访问该元素，并返回 null。

```PowerShell
$a = $null
${a}?[0]
```

> [!NOTE]
> 由于 PowerShell 允许 `?` 作为变量名称的一部分，因此使用这些运算符需要变量名称的形式规范。 因此，使用 `{}` 将变量名称括起来（如 `${a}`）或 `?` 是变量名称 `${a?}` 的一部分时需要形式规范。
>
> 的变量名语法 `${<name>}` 不应与 `$()` 子表达式运算符混淆。 有关详细信息，请参阅 [about_Variables](about_Variables.md#variable-names-that-include-special-characters)的变量名称部分。

## <a name="see-also"></a>请参阅

[about_Arithmetic_Operators](about_Arithmetic_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Pipeline_Chain_Operators](about_Pipeline_Chain_Operators.md)

[about_Split](about_Split.md)

[about_Join](about_Join.md)

[about_Redirection](about_Redirection.md)
