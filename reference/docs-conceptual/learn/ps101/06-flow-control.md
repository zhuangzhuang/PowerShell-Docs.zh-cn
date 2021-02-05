---
title: 流量控制
description: PowerShell 提供了一些方法，用于创建循环、制定决策以及以逻辑方式控制脚本中的代码流。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 74595f8c6a5d4a49b05e72dd6bde1441fd2b464e
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598043"
---
# <a name="chapter-6---flow-control"></a>第 6 章 - 流控制

## <a name="scripting"></a>脚本编写

当你从编写 PowerShell 单行命令转为编写脚本时，实际复杂程度没有想象的那么高。 脚本只是在 PowerShell 控制台中以交互方式运行的相同或类似命令，只不过它们保存为 `.PS1` 文件。 可以使用一些脚本构造，如 `foreach` 循环，而不是 `ForEach-Object` cmdlet。 对于初学者来说，这种差异可能会令人困惑，特别是当你认为 `foreach` 既是脚本构造，又是 `ForEach-Object` cmdlet 的别名时。

## <a name="looping"></a>循环

PowerShell 的一大优势是，确定了如何为某个项执行某些操作后，就可以很容易地为数百个项执行相同的任务。 只需使用 PowerShell 中多种不同类型的循环之一循环访问这些项即可。

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object` 是用于循环访问管道中的项的 cmdlet，例如使用 PowerShell 单行命令。 `ForEach-Object` 通过管道流式处理对象。

虽然 `Get-Command` 的 Module 参数接受作为字符串的多个值，但仅通过管道输入按属性名称或通过参数输入接受这些值。 在下面的情形中，如果我想通过管道将两个字符串按值传递到 `Get-Command`，以便与 Module 参数一起使用，则需要使用 `ForEach-Object` cmdlet。

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

在前面的示例中，`$_` 为当前对象。 从 PowerShell 版本 3.0 开始，可以使用 `$PSItem` 而不是 `$_`。 但我发现，大多数经验丰富的 PowerShell 用户仍更喜欢使用 `$_`，因为它向后兼容，需要输入的内容更少。

使用 `foreach` 关键字时，必须先将所有项存储在内存中，然后才能循环访问这些项，如果不知道要处理的项数，此操作可能会很困难。

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

很多时候都需要 `foreach` 或 `ForEach-Object` 等循环。 否则，你将收到一条错误消息。

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

在其他情况下，可以在完全消除循环的情况下得到相同的结果。 请参阅 cmdlet 帮助以了解你的选项。

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

如前面的示例所示，`Get-ADComputer` 的 Identity 参数仅接受通过参数输入提供的单个值，但通过管道输入提供时，它允许多个项。

### <a name="for"></a>For

当指定的条件为 true 时，`for` 循环会进行循环访问。 我并未经常使用 `for` 循环，但它确实有它的用处。

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

在前面的示例中，循环从数字 1 开始循环访问 4 次，并在计数器变量 `$i` 小于 5 时继续循环访问。 休眠时间共计 10 秒。

### <a name="do"></a>要求事项

PowerShell 中有两个不同的 `do` 循环。 指定的条件为 false 时，`Do Until` 运行。

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

前面的示例是一个数字游戏，在你猜测的值等于 `Get-Random` cmdlet 生成的相同数字时游戏结束。

`Do While` 正好相反。 只要指定条件的计算结果为 true，它就会运行。

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

通过将测试条件反转为不等于，使用 `Do While` 循环可实现相同的结果。

`Do` 循环始终运行至少一次，因为将在循环结束时计算条件的结果。

### <a name="while"></a>While

与 `Do While` 循环类似，只要指定的条件为 true，`While` 循环就会运行。 但差别在于，`While` 循环会在运行任何代码之前，计算循环顶部条件的结果。 如果条件计算结果为 false，它就不会运行。

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

前面的示例计算了美国的感恩节是哪一天。 它始终是 11 月的第 4 个星期四。 因此循环从 11 月 22 日开始，并在当天不是星期四时增加一天。 如果 22 日是星期四，则循环根本不会运行。

## <a name="break-continue-and-return"></a>Break、Continue 和 Return

`Break` 旨在中断循环。 它通常与 `switch` 语句一起使用。

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

上一示例中所示的 `break` 语句导致循环在第一次迭代时退出。

Continue 旨在跳到循环的下一次迭代。

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

前面的示例将输出数字 1、2、4 和 5。 它跳过数字 3，并继续执行循环的下一次迭代。 与 `break` 类似，`continue` 将中断除当前迭代以外的循环。 Execution 将继续进行下一次迭代，而不是中断循环并停止。

Return 旨在退出现有作用域。

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

请注意，在上面的示例中，return 输出第一个结果，然后退出循环。 可以在我的一篇博客文章中找到有关结果语句的更详尽说明：[“PowerShell return 关键字”][]。

## <a name="summary"></a>总结

本章介绍了 PowerShell 中存在的不同类型的循环。

## <a name="review"></a>审阅

1. `ForEach-Object` cmdlet 和 foreach 脚本构造之间有何区别？
1. 使用 While 循环而不使用 Do While 或 Do Until 循环的主要优点是什么。
1. Break 和 continue 语句有何不同？

## <a name="recommended-reading"></a>推荐阅读的主题

- [ForEach-Object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[“PowerShell return 关键字”]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
