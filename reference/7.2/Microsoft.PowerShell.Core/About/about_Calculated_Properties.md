---
description: PowerShell 提供动态添加新属性和更改对象输出到管道的格式的功能。
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1f7470a47a24b7c2b8265d180aac49cfec9031f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598704"
---
# <a name="about-calculated-properties"></a>关于计算属性

## <a name="short-description"></a>简短说明

PowerShell 提供动态添加新属性和更改对象输出到管道的格式的功能。

## <a name="long-description"></a>详细说明

许多 PowerShell cmdlet 使用参数将输入对象转换、聚合或处理到输出对象，这些参数允许向这些输出对象添加新属性。 这些参数可用于基于输入对象的值为输出对象生成新的计算属性。
计算属性由包含键/值对（用于指定新属性的名称）、用于计算值的表达式和可选格式设置 [信息的键](about_hash_tables.md) /值对来定义。

## <a name="supported-cmdlets"></a>受支持的 cmdlet

以下 cmdlet 支持 **属性** 参数的计算属性值。 `Format-*`Cmdlet 还支持 **GroupBy** 参数的计算值。

以下列表列举支持计算属性的 cmdlet 和每个 cmdlet 支持的键值对。

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` -可选 (在 PowerShell 3.x 中添加) 
  - `expression`
  - `width` -可选
  - `alignment` -可选

- `Format-Custom`
  - `expression`
  - `depth` -可选

- `Format-List`
  - `name`/`label` -可选
  - `expression`
  - `formatstring` -可选

  这一组相同的键/值对同样适用于传递到所有 cmdlet 的 **GroupBy** 参数的计算属性值 `Format-*` 。

- `Format-Table`
  - `name`/`label` -可选
  - `expression`
  - `formatstring` -可选
  - `width` -可选
  - `alignment` -可选

- `Format-Wide`
  - `expression`
  - `formatstring` -可选

- `Group-Object`
  - `expression`

- `Measure-Object`
  - 仅支持表达式的脚本块，而不支持哈希表。
  - 在 PowerShell 5.1 和更早版本中不受支持。

- `Select-Object`
  - `name`/`label` -可选
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` -可选

> [!NOTE]
> 的值可以是 `expression` 脚本块，而不是哈希表。 有关详细信息，请参阅 " [备注](#notes) " 部分。

## <a name="hashtable-key-definitions"></a>哈希表键定义

- `name`/`label` -指定正在创建的属性的名称。 您可以使用 `name` 或其别名，可以 `label` 互换。
- `expression` -用于计算新属性值的脚本块。
- `alignment` -由生成表格输出的 cmdlet 用来定义值在列中的显示方式。 值必须为 `'left'` 、 `'center'` 或 `'right'` 。
- `formatstring` -指定一个格式字符串，该字符串定义如何为输出设置值的格式。 有关格式字符串的详细信息，请参阅 [.net 中的格式类型](/dotnet/standard/base-types/formatting-types)。
- `width` -指定显示值时表中的最大宽度列。 该值必须大于 `0` 。
- `depth` -的 **深度** 参数 `Format-Custom` 指定所有属性的展开深度。 `depth`键允许您指定每个属性的展开深度。
- `ascending` / `descending` -用于指定一个或多个属性的排序顺序。 这些值是布尔值。

只要指定的名称前缀明确，哈希表键就不需要拼写。 例如， `n` 可用于代替 `Name` ， `e` 可用于代替 `Expression` 。

## <a name="examples"></a>示例

### <a name="compare-object"></a>Compare-Object

利用计算属性，您可以控制如何对输入对象的属性进行比较。 在此示例中，将值与 2)  (取模运算的结果进行比较，而不是直接比较值。

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` 可以将对象集合转换为 HTML 表。
计算属性允许您控制表的显示方式。

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

此示例将创建一个 HTML 表，其中包含 PowerShell 别名列表和每个别名命令的编号参数。 **ParameterCount** 列的值居中。

### <a name="format-custom"></a>Format-Custom

`Format-Custom` 以类似于类定义的格式提供对象的自定义视图。 更复杂的对象可以包含深度与复杂类型嵌套的成员。 的 **深度** 参数 `Format-Custom` 指定所有属性的展开深度。 `depth`键允许您指定每个属性的展开深度。

在此示例中， `depth` 该键简化了 cmdlet 的自定义输出 `Get-Date` 。 `Get-Date` 返回 **DateTime** 对象。 此对象的 **日期** 属性也是 **DateTime** 对象，因此该对象是嵌套的。

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

在此示例中，我们使用计算属性更改输出的名称和格式 `Get-ChildItem` 。

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

在此示例中，计算属性添加了用于按内容类型对文件进行分类的 **类型** 属性。

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

使用 `Format-Wide` cmdlet 可以将集合中对象的一个属性值显示为多列列表。

在此示例中，我们希望以 kb) 的形式查看文件名和大小 (。 由于不 `Format-Wide` 显示多个属性，因此我们使用计算属性将两个属性的值合并为一个值。

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

该 `Group-Object` cmdlet 根据指定属性的值在组中显示对象。 在此示例中，计算属性计算每种内容类型的文件数。

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

`Measure-Object`Cmdlet 计算对象的数值属性。 在此示例中，我们将使用计算属性来获取计数，该计数是介于1和10之间的数字 (**求和**) ，可被3整除。

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> 与其他 cmdlet 不同的 `Measure-Object` 是，不接受计算属性的哈希表。 必须使用脚本块。

### <a name="select-object"></a>Select-Object

您可以使用计算属性将其他成员添加到使用 cmdlet 输出的对象 `Select-Object` 。 在此示例中，我们列出了以字母开头的 PowerShell 别名 `C` 。 使用 `Select-Object` ，我们输出别名、它映射到的 cmdlet 以及为 cmdlet 定义的参数的数量计数。 使用计算属性，我们可以创建 **ParameterCount** 属性。

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

使用计算属性，可以按属性对数据进行排序。 此示例按 **日期** 以升序顺序对 CSV 文件中的数据进行排序。 但在每个日期中，将按 **UnitsSold** 以降序对行进行排序。

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>说明

- 您可以 _直接_ 指定表达式脚本块作为参数，而不是将其指定为 `Expression` 哈希表中的条目。 例如：

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  此示例对于不需要 (或支持) 通过键命名属性（ `Name` 例如、和）的 cmdlet 非常方便 `Sort-Object` `Group-Object` `Measure-Object` 。

  对于支持命名属性的 cmdlet，脚本块会转换为字符串，并在输出中用作属性的名称。

- `Expression` 脚本块在 _子_ 范围内运行，这意味着调用方的变量不能直接修改。

- 管道逻辑应用于脚本块的输出 `Expression` 。 这意味着输出单个元素数组将导致该数组解包。

- 对于大多数 cmdlet，表达式脚本块中的错误都将不知不觉地忽略。
  对于 `Sort-Object` ，语句终止和脚本终止错误是 _输出_ ，但不会终止语句。

## <a name="see-also"></a>另请参阅

[about_Hash_Tables](about_hash_tables.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Group-Object](xref:Microsoft.PowerShell.Utility.Group-Object)

[Measure-Object](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sort-Object](xref:Microsoft.PowerShell.Utility.Sort-Object)

[.NET 中的格式类型](/dotnet/standard/base-types/formatting-types)
