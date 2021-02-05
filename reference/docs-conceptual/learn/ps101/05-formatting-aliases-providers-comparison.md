---
title: 格式设置, 别名, 提供程序, 比较
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: 本章介绍输出格式设置、命令别名、提供程序和比较操作的概念。
ms.openlocfilehash: 5573ca58601af0c6af15736b772a9792d8d77a79
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596004"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>第 5 章 - 格式设置、别名、提供程序、比较

## <a name="requirements"></a>要求

本章所述的某些示例需要 SQL Server PowerShell 模块。 此模块作为 [SQL Server Management Studio (SMSS)][SMSS] 的一部分安装。 后续章节也会使用此模块。 将它下载并安装在 Windows 10 实验室环境计算机上。

## <a name="format-right"></a>右对齐格式

在第 4 章中，你已了解如何尽可能靠左侧进行筛选。 手动设置命令输出的格式的规则类似于该规则，不同之处在于它需要尽可能出现在右侧。

最常见的格式命令是 `Format-Table` 和 `Format-List`。 还可以使用 `Format-Wide` 和 `Format-Custom`，但不太常见。

如第 3 章所述，除非使用自定义格式设置，否则返回超过四个属性的命令默认为列表。

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

使用 `Format-Table` cmdlet 手动替代格式设置，并在表中而不是在列表中显示输出。

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

`Get-Service` 的默认输出是表中的三个属性。

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

使用 `Format-List` cmdlet 替代默认格式设置，并在列表中返回结果。

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

请注意，仅通过管道将 `Get-Service` 传送到 `Format-List` 会使其返回其他属性。 并非每个命令都会出现这种情况，因为特定命令的格式是在后台设置的。

使用 cmdlet 格式时，首先需要注意的是，它们生成的格式对象与 PowerShell 中的普通对象不同。

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

这意味着无法通过管道将格式命令传送给大多数其他命令。 可以将格式命令通过管道传送给一些 `Out-*` 命令，但仅此而已。 因此，建议在行尾执行任何格式设置（右对齐格式）。

## <a name="aliases"></a>别名

PowerShell 的别名是命令的较短名称。 PowerShell 包含一组内置别名，你也可以定义自己的别名。

`Get-Alias` cmdlet 用于查找别名。 如果你已知道命令的别名，则 Name 参数用于确定与该别名关联的命令。

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

可以为 Name 参数的值指定多个别名。

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

你会经常看到 Name 参数被忽略，因为它是位置参数。

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

如果要查找命令的别名，需要使用 Definition 参数。

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

不能按位置使用 Definition 参数，因此必须指定它。

使用别名可以减少按键次数，并且在将命令输入到控制台时也可行。
它们不应在脚本或任何要保存或与他人共享的代码中使用。 如本书前面所述，使用完整的 cmdlet 和参数名称是自文档化，并且更易于理解。

创建自己的别名时要小心，因为它们将仅存在于计算机上的当前 PowerShell 会话中。

## <a name="providers"></a>提供程序

PowerShell 中的提供程序是一种允许文件系统访问数据存储的接口。 PowerShell 中提供了许多内置提供程序。

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

如上面的结果所示，存在用于注册表、别名、环境变量、文件系统、函数、变量、证书和 WSMan 的内置提供程序。

这些提供程序用于公开其数据存储的实际驱动器可使用 `Get-PSDrive` cmdlet 确定。 `Get-PSDrive` cmdlet 不仅显示由提供程序公开的驱动器，而且还显示 Windows 逻辑驱动器，其中包括映射到网络共享的驱动器。

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

第三方模块（例如 Active Directory PowerShell 模块和 SQL Server PowerShell 模块）都添加了自己的 PowerShell 提供程序和 PSDrive。

导入 Active Directory 和 SQL Server PowerShell 模块。

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

检查以确定是否添加了任何其他 PowerShell 提供程序。

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

请注意，在前面的结果集中，现在存在两个新的 PowerShell 提供程序，一个用于 Active Directory，另一个用于 SQL Server。

此外，还为每个模块添加了一个 PSDrive。

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

可以像访问传统文件系统一样访问 PSDrive。

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>比较运算符

PowerShell 包含许多比较运算符，用于比较值或查找与特定模式匹配的值。 表 5-1 包含 PowerShell 中的比较运算符的列表。

|    操作员    |                          定义                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | 等于                                                     |
| `-ne`          | 不等于                                                 |
| `-gt`          | 大于                                                 |
| `-ge`          | 大于或等于                                     |
| `-lt`          | 小于                                                    |
| `-le`          | 小于或等于                                        |
| `-Like`        | 使用 `*` 通配符进行匹配                       |
| `-NotLike`     | 不使用 `*` 通配符进行匹配              |
| `-Match`       | 匹配指定的正则表达式                     |
| `-NotMatch`    | 不匹配指定的正则表达式              |
| `-Contains`    | 确定集合中是否包含指定的值        |
| `-NotContains` | 确定集合是否不包含特定值 |
| `-In`          | 确定指定的值是否在集合中           |
| `-NotIn`       | 确定指定的值是否不在集合中       |
| `-Replace`     | 替换指定的值                                 |

表 5-1 中列出的所有运算符都不区分大小写。 将 `c` 放置在表 5-1 中列出的运算符之前，使其区分大小写。 例如，`-ceq` 是区分大小写的 `-eq` 比较运算符。

首字母大写的“PowerShell”等效于使用等于比较运算符的小写的“powershell”。

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

使用区分大小写的等于比较运算符时，不等效。

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

不等于比较运算符反转条件。

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

大于、大于或等于、小于和小于或等于均可用于字符串或数值。

```powershell
5 -gt 5
```

```Output
False
```

在上一个示例中，使用大于或等于而不是大于，会返回布尔值 true，因为 5 等于 5。

```powershell
5 -ge 5
```

```Output
True
```

根据上述两个示例中的结果，你可能会猜到使用小于和小于或等于的情况。

```powershell
5 -lt 10
```

```Output
True
```

即使对于经验丰富的 PowerShell 用户，`-Like` 和 `-Match` 运算符也可能会造成混淆。 `-Like` 与通配符 `*` 和 `?` 结合使用，以执行“like”匹配。

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` 使用正则表达式执行匹配。

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

使用范围运算符将数字 1 到 10 存储在变量中。

```powershell
$Numbers = 1..10
```

```Output
```

确定 `$Numbers` 变量是否包含 15。

```powershell
$Numbers -contains 15
```

```Output
False
```

确定它是否包含数字 10。

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` 反转逻辑，以查看 `$Numbers` 变量是否不包含值。

```powershell
$Numbers -notcontains 15
```

```Output
True
```

前面的示例返回布尔值 true，因为 `$Numbers` 变量不包含 15。 但它包含数字 10，因此在进行测试时，结果为 false。

```powershell
$Numbers -notcontains 10
```

```Output
False
```

PowerShell 版本 3.0 首次引入了“in”比较运算符。 它用于确定某个值是否“位于”数组中。 `$Numbers` 变量是数组，因为它包含多个值。

```powershell
15 -in $Numbers
```

```Output
False
```

换言之，`-in` 执行与 contains 比较运算符相同的测试，不过方向相反。

```powershell
10 -in $Numbers
```

```Output
True
```

15 不在 `$Numbers` 数组中，因此在下面的示例中返回 false。

```powershell
15 -in $Numbers
```

```Output
False
```

与 `-contains` 运算符一样，`not` 反转 `-in` 运算符的逻辑。

```powershell
10 -notin $Numbers
```

```Output
False
```

上面的示例返回 false，因为 `$Numbers` 数组包含 10，并且条件进行了测试以确定它是否不包含 10。

15“不位于”`$Numbers` 数组中，因此它返回布尔值 true。

```powershell
15 -notin $Numbers
```

```Output
True
```

`-replace` 运算符所执行的操作和你想象的一样。 它用于替换内容。 如果指定一个值，则会将该值替换为空值。 在下面的示例中，我将“Shell”替换为空值。

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

如果要将值替换为其他值，请在要替换的模式之后指定新值。 SQL Saturday in Baton Rouge is an event that I try to speak at every year. 在下面的示例中，我将“Saturday”这个词替换为缩写“Sat”。

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

还有一些可用于替换内容的方法（如 Replace()），其工作原理类似于替换运算符。 但是，默认情况下，`-Replace` 运算符不区分大小写，而 Replace() 方法区分大小写。

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

请注意，上述示例中未替换“Saturday”一词。 这是因为所指定的大小写格式与原始格式不同。 当指定的“Saturday”的大小写格式与原始格式相同时，Replace() 方法会按预期替换它。

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

使用方法转换数据时要小心，因为可能会遇到无法预料的问题，例如 Turkey Test 失败。 有关示例，请参阅标题为[使用 Pester 测试具有其他区域性的 PowerShell 代码][]的博客文章。 我建议尽量使用运算符而不是方法，以避免这些类型的问题。

尽管可以像前面的示例中所示使用比较运算符，但我通常将它们与 `Where-Object` cmdlet 一起使用来执行某种类型的筛选。

## <a name="summary"></a>总结

在本章中，你已了解了多个不同的主题，其中包含右对齐格式设置、别名、提供程序和比较运算符。

## <a name="review"></a>审阅

1. 为什么有必要尽可能靠右侧执行格式设置？
1. 如何确定 `%` 别名的实际 cmdlet 是什么？
1. 为什么不应在保存的脚本或与其他人共享的代码中使用别名？
1. 在与其中某个注册表提供程序相关联的驱动器上执行目录列表。
1. 使用替换运算符而不是替换方法的其中一个主要好处是什么？

## <a name="recommended-reading"></a>推荐阅读的主题

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[使用 Pester 测试具有其他区域性的 PowerShell 代码]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
