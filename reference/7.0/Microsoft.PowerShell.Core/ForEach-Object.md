---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 584ca877cedfe1494f8386af75f9f1911a5b8f15
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685652"
---
# ForEach-Object

## 摘要
针对输入对象集合中的每个项执行操作。

## 语法

### ScriptBlockSet（默认值）

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ParallelParameterSet

```
ForEach-Object [-InputObject <PSObject>] -Parallel <ScriptBlock> [-ThrottleLimit <Int32>]
 [-TimeoutSeconds <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 说明

`ForEach-Object`Cmdlet 对输入对象集合中的每个项执行操作。 可以通过管道将输入对象传递给 cmdlet，或使用 **InputObject** 参数指定。

从 Windows PowerShell 3.0 开始，可以使用两种不同的方法来构造 `ForEach-Object` 命令。

- **脚本块**。 你可以使用某个脚本块来指定操作。 在脚本块中，使用 `$_` 变量来表示当前对象。 脚本块是 **Process** 参数的值。 脚本块可以包含任何 PowerShell 脚本。

  例如，以下命令将获取计算机上每个进程的 **ProcessName** 属性值。

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` 支持 `begin` 、 `process` 和块， `end` 如 [about_functions](about/about_functions.md#piping-objects-to-functions)中所述。

  > [!NOTE]
  > 脚本块在调用方的作用域中运行。 因此，这些块有权访问该范围内的变量，并且可以创建在 cmdlet 完成后在该范围内持久保留的新变量。

- **操作语句**。 你还可以编写操作语句，它更像自然语言。 你可以使用该操作语句来指定属性值或调用方法。 Windows PowerShell 3.0 中引入了操作语句。

  例如，以下命令还将获取计算机上每个进程的 **ProcessName** 属性值。

  `Get-Process | ForEach-Object ProcessName`

- **并行运行的脚本块**。 从 PowerShell 7.0 开始，第三个参数集可用于并行运行每个脚本块。 **ThrottleLimit** 参数限制一次运行的并行脚本的数量。 与前面一样，使用 `$_` 变量表示脚本块中的当前输入对象。 使用 `$using:` 关键字可将变量引用传递给正在运行的脚本。

  在 PowerShell 7 中，为每个循环迭代创建新的运行空间，以确保最大程度的隔离。
  如果要执行的工作比创建新的运行空间少，或者有大量迭代执行重要的工作，则这可能会造成较大的性能和资源的损失。

  默认情况下，并行 scriptblocks 使用启动并行任务的调用方的当前工作目录。

  如果在并行运行的 scriptblocks 中发生了非终止错误，则会将这些错误写入到 cmdlet 错误流中。 由于无法确定并行 scriptblock 执行顺序，错误流中出现错误的顺序是随机的。 同样，写入其他数据流的消息（如警告、详细或信息）将按不确定的顺序写入这些数据流。

  终止错误（如异常）将终止发生 scriptblocks 的单个并行实例。 一个 scriptblocks 中的终止错误不会导致 `Foreach-Object` cmdlet 终止。 同时运行的其他 scriptblocks 将继续运行，除非它们也遇到终止错误。 终止错误将作为 **ErrorRecord** ，以 **FullyQualifiedErrorId** 的形式写入错误数据流 `PSTaskException` 。
  使用 PowerShell try/catch 块或 catch 块可将终止错误转换为非终止错误。

## 示例

### 示例1：分割数组中的整数

此示例使用一个包含三个整数的数组，并将每个整数除以1024。

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### 示例2：获取目录中所有文件的长度

此示例处理 PowerShell 安装目录中的文件和目录 `$PSHOME` 。

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

如果该对象不是一个目录，则脚本块将获取该文件的名称，将其 **Length** 属性的值除以1024，并添加一个空格 ( "" ) 以便将它与下一项隔开。 Cmdlet 使用 **PSISContainer** 属性来确定对象是否为目录。

### 示例3：对最新系统事件进行操作

此示例将系统事件日志中的最新事件1000写入文本文件。 当前时间在处理事件之前和之后显示。

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` 获取系统事件日志中的最新事件1000，并将其存储在 `$Events` 变量中。 `$Events` 然后，将管道传递给 `ForEach-Object` cmdlet。 **Begin** 参数将显示当前日期和时间。 接下来， **Process** 参数使用 `Out-File` cmdlet 创建一个名为 events.txt 的文本文件，并将每个事件的消息属性存储在该文件中。 最后，在完成所有处理之后，使用 **End** 参数显示日期和时间。

### 示例4：更改注册表项的值

此示例将 "密钥" 下的所有子项中的 **RemotePath** 注册表项的值更改 `HKCU:\Network` 为大写文本。

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

可以使用此格式更改注册表条目值的形式或内容。

**网络** 密钥中的每个子项表示在登录时重新连接的映射网络驱动器。 **RemotePath** 项包含连接的驱动器的 UNC 路径。 例如，如果将 E：驱动器映射到 `\\Server\Share` ，则会在中创建一个 **e** 子项， `HKCU:\Network` 并将 **RemotePath** 注册表值设置为 `\\Server\Share` 。

该命令使用 `Get-ItemProperty` cmdlet 来获取 **网络** 密钥的所有子项，并使用 `Set-ItemProperty` cmdlet 来更改每个密钥中的 **RemotePath** 注册表项的值。
在 `Set-ItemProperty` 命令中，路径是注册表项的 **PSPath** 属性的值。 这是表示注册表项的 Microsoft .NET Framework 对象的属性，而不是注册表项。 该命令使用 **RemotePath** 值的 **ToUpper ()** 方法，该方法是 REG_SZ) 的字符串 (。

由于 `Set-ItemProperty` 正在更改每个键的属性，因此 `ForEach-Object` 需要使用 cmdlet 来访问属性。

### 示例5：使用 $Null 自动变量

此示例演示如何通过管道将 `$Null` 自动变量传递给 `ForEach-Object` cmdlet。

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

因为 PowerShell 将 null 视为显式占位符，所以该 `ForEach-Object` cmdlet 会生成一个值 `$Null` ，就像对管道传递给它的其他对象一样。

### 示例6：获取属性值

此示例通过使用 cmdlet 的 **成员名称** 参数获取所有已安装的 PowerShell 模块的 **Path** 属性的值 `ForEach-Object` 。

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

第二个命令等效于第一个命令。 它使用 `Foreach` cmdlet 的别名， `ForEach-Object` 并忽略 **成员** 名称参数的名称，此参数是可选的。

此 `ForEach-Object` cmdlet 对于获取属性值非常有用，因为它在不更改类型的情况下获取值， 而不是更改 `Select-Object` 属性值类型。

### 示例7：将模块名称拆分为组件名称

此示例显示了将两个以句点分隔的模块名称拆分为其组件名称的三种方法。

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

这些命令调用字符串的 **Split** 方法。 这三个命令使用不同的语法，但它们是等效且可互换的。

第一个命令使用传统语法，包括脚本块和当前的对象运算符 `$_` 。 它使用句点语法来指定该方法，并使用括号将分隔符参数括起来。

第二个命令使用 **MemberName** 参数来指定 **Split** 方法，并使用 **ArgumentName** 参数将句点 (".") 标识为拆分分隔符。

第三个命令使用 cmdlet 的 **Foreach** 别名， `ForEach-Object` 并省略 **成员** 名称和 **ArgumentList** 参数的名称，这些参数是可选的。

### 示例8：将 ForEach-Object 用于两个脚本块

在此示例中，我们传递两个脚本块按位置。 所有脚本块都绑定到 **Process** 参数。 但是，它们被视为已传递到 **Begin** 和 **Process** 参数。

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### 示例9：使用包含两个以上脚本块的 ForEach-Object

在此示例中，我们传递两个脚本块按位置。 所有脚本块都绑定到 **Process** 参数。 但是，它们被视为已传递到 **Begin**、 **Process** 和 **End** 参数。

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> 第一个脚本块始终映射到 `begin` 块，最后一个块映射到 `end` 块，中间的块全部映射到 `process` 块。

### 示例10：运行每个管道项的多个脚本块

如前面的示例所示，使用 **Process** 参数传递的多个脚本块将映射到 **Begin** 和 **End** 参数。 若要避免此映射，必须为 **Begin** 和 **End** 参数提供显式值。

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### 示例11：并行运行缓慢脚本

此示例运行一个简单的脚本块，该脚本块可计算字符串并休眠一秒钟。

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

**ThrottleLimit** 参数值设置为4，以便按四个批处理对输入进行处理。
`$using:`关键字用于将 `$Message` 变量传递到每个并行脚本块中。

### 示例12：并行检索日志条目

此示例从本地 Windows 计算机上的5个系统日志中检索50000日志条目。

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

Parallel 参数指定为每个输入日志名称并行运行的脚本块。 **ThrottleLimit** 参数可确保同时运行所有五个脚本块。

### 示例13：作为作业并行运行

此示例将并行运行简单的脚本块，同时创建两个后台作业。

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

`$job`变量接收收集输出数据并监视正在运行状态的作业对象。
作业对象 `Receive-Job` 与 **Wait** 开关参数一起传递给。 这会流输出到控制台，就好像是在 `ForEach-Object -Parallel` 没有 **AsJob** 的情况下运行一样。

### 示例14：使用线程安全变量引用

此示例将并行调用脚本块以收集唯一命名的进程对象。

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

**ConcurrentDictionary** 对象的单个实例会传递给每个脚本块，以收集对象。 由于 **ConcurrentDictionary** 是线程安全的，因此可以安全地通过每个并行脚本进行修改。 在此处使用非线程安全的对象（如 **system.object**）将是不安全的。

> [!NOTE]
> 此示例非常低效地使用了 **并行** 参数。 此脚本只是将输入对象添加到并发字典对象。 这种方法很简单，不值得在单独的线程中调用每个脚本的系统开销。 `ForEach-Object`在没有 **并行** 交换机的情况下正常运行更高效、更快。 此示例仅用于演示如何使用线程安全变量。

### 示例15：编写并行执行的错误

此示例将并行写入错误流，其中写入错误的顺序是随机的。

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### 示例16：在并行执行中终止错误

此示例演示一个并行运行的 scriptblock 中的终止错误。

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

`Output: 3` 永远不会编写，因为该迭代的并行 scriptblock 已终止。

### 示例17：在嵌套并行脚本中传递变量 ScriptBlockSet

可以在作用域的 scriptblock 之外创建变量 `Foreach-Object -Parallel` ，并在 scriptblock 中使用 `$using` 关键字。

```powershell
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
}
```

```Output
TestA
TestA
```

```powershell
# You CANNOT create a variable inside a scoped scriptblock
# to be used in a nested foreach parallel scriptblock.
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
    $test2 = 'TestB'
    1..2 | Foreach-Object -Parallel {
        $using:test2
    }
}
```

```Output
Line |
   2 |  1..2 | Foreach-Object -Parallel {
     |         ~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The value of the using variable '$using:test2' cannot be retrieved because it has not been set in the local session.
```

嵌套的 scriptblock 无法访问该 `$test2` 变量，并引发错误。

## 参数

### -ArgumentList

指定方法调用的参数数组。 有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Begin

指定在此 cmdlet 处理任何输入对象之前运行的脚本块。 此脚本块仅对整个管道运行一次。 有关块的详细信息 `begin` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

指定在此 cmdlet 处理所有输入对象之后运行的脚本块。 此脚本块仅对整个管道运行一次。 有关块的详细信息 `end` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定输入对象。 `ForEach-Object` 在每个输入对象上运行脚本块或操作语句。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

当你将 **inputobject** 参数与一起使用时 `ForEach-Object` ， `ForEach-Object` **inputobject** 值将被视为单个对象，而不是管道将命令结果传递给。 即使该值是作为命令结果的集合（如），也是如此 `-InputObject (Get-Process)` 。
由于 **InputObject** 无法从数组或对象的集合返回各个属性，因此，如果您使用在 `ForEach-Object` 已定义的属性中具有特定值的那些对象的对象集合上执行操作，则建议您 `ForEach-Object` 在管道中使用，如本主题的示例中所示。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberName

指定要获取的属性或要调用的方法。

允许使用通配符，但仅在生成的字符串解析为唯一值时才有效。
例如，如果运行 `Get-Process | ForEach -MemberName *Name` ，通配符模式将匹配多个成员，导致命令失败。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Process

指定对每个输入对象所执行的操作。 为管道中的每个对象运行此脚本块。 有关块的详细信息 `process` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

向 **Process** 参数提供多个脚本块时，第一个脚本块将始终映射到 `begin` 块。 如果只有两个脚本块，则第二个块映射到 `process` 块。 如果有三个或更多脚本块，则第一个脚本块始终映射到 `begin` 块，最后一个块映射到块 `end` ，而介于之间的块全部映射到 `process` 块。

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

指定 **进程** 参数不会使用的所有脚本块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parallel

指定要用于对输入对象进行并行处理的脚本块。 输入描述该操作的脚本块。

此参数是在 PowerShell 7.0 中引入的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定并行的脚本块的数量。 在正在运行的脚本块计数低于 **ThrottleLimit** 之前，输入对象将被阻止。 默认值为 `5`。

此参数是在 PowerShell 7.0 中引入的。

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

指定以并行方式处理所有输入所等待的秒数。 在指定的超时时间后，将停止所有正在运行的脚本。 以及要处理的其余输入对象将被忽略。 默认值为 `0` "禁用超时"， `ForEach-Object -Parallel` 可以无限期运行。 <kbd></kbd> + 在命令行中键入 Ctrl<kbd>C</kbd>会停止正在运行的 `ForEach-Object -Parallel` 命令。 此参数不能与 **AsJob** 参数一起使用。

此参数是在 PowerShell 7.0 中引入的。

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

导致并行调用作为 PowerShell 作业运行。 返回一个作业对象，而不是运行的脚本块的输出。 作业对象包含运行的每个并行脚本块的子作业。 所有 PowerShell 作业 cmdlet 都可以使用作业对象来监视正在运行的状态和检索数据。

此参数是在 PowerShell 7.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

你可以通过管道将任何对象传递给此 cmdlet。

## Outputs

### System.Management.Automation.PSObject

此 cmdlet 将返回由输入确定的对象。

## 说明

- 此 `ForEach-Object` cmdlet 的工作方式与 **foreach** 语句非常相似，不同之处在于你不能通过管道将输入传递给 **foreach** 语句。 有关 **Foreach** 语句的详细信息，请参阅 [about_Foreach](./About/about_Foreach.md)。

- 从 PowerShell 4.0 开始， `Where` `ForEach` 添加了方法以与集合一起使用。 可在此处阅读有关这些新方法的详细信息 [about_arrays](./About/about_Arrays.md)

- `ForEach-Object -Parallel`参数集使用 PowerShell 的内部 API 来运行每个脚本块。 这比 `ForEach-Object` 以顺序处理正常运行的开销要大得多。 与脚本块执行的工作相比 **，并行运行** 的开销很小，这一点很重要。 例如：

  - 多核计算机上的计算密集型脚本
  - 花费时间等待结果或执行文件操作的脚本

  使用 **Parallel** 参数可能会导致脚本的运行速度慢于正常。 尤其是当并行脚本很简单时。 进行 **并行** 试验，以发现它的好处。

  > [!IMPORTANT]
  > `ForEach-Object -Parallel`参数集在单独的进程线程上并行运行脚本块。 `$using:`关键字允许将来自 cmdlet 调用线程的变量引用传递到每个正在运行的脚本块线程。 由于脚本块在不同的线程中运行，因此必须安全地使用由引用传递的对象变量。 通常，可以安全地从不会更改的引用对象中进行读取。 但如果对象状态正在修改，则必须使用线程安全对象， **如 .net system.string** 类型 (参见示例 11) 。

## 相关链接

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
