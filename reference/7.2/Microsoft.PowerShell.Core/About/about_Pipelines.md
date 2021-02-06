---
description: 在 PowerShell 中将命令合并到管道中
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: e4ae85fbbfe5232048a90e1fe4f62db3e95e5f1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603828"
---
# <a name="about-pipelines"></a>关于管道

## <a name="short-description"></a>简短说明

在 PowerShell 中将命令合并到管道中

## <a name="long-description"></a>长说明

管道是一系列由管道运算符连接的命令 (`|`)  (ASCII 124) 。 每个管道运算符将前一个命令的结果发送到下一个命令。

可以发送第一个命令的输出，作为第二个命令的输入进行处理。 还可以将输出发送到另一个命令。 结果是一个复杂的命令链或 _管道_ ，由一系列简单的命令组成。

例如，应用于对象的

```powershell
Command-1 | Command-2 | Command-3
```

在此示例中，发出的对象将 `Command-1` 发送到 `Command-2` 。
`Command-2` 处理对象并将其发送到 `Command-3` 。 `Command-3` 处理对象并将其沿管道向下发送。 由于管道中没有更多命令，因此结果将显示在控制台上。

在管道中，按从左到右的顺序处理命令。 处理将作为单个操作进行处理，并在生成时显示输出。

下面是一个简单的示例。 以下命令将获取记事本进程，然后将其停止。

例如，应用于对象的

```powershell
Get-Process notepad | Stop-Process
```

第一个命令使用 `Get-Process` cmdlet 来获取表示记事本进程的对象。 它使用管道运算符 (`|`) 将进程对象发送到 `Stop-Process` cmdlet，后者将停止记事本进程。 请注意，该 `Stop-Process` 命令没有 **Name** 或 **ID** 参数来指定进程，因为指定的进程是通过管道提交的。

此管道示例获取当前目录中的文本文件，只选择长度超过10000个字节的文件，按长度对它们进行排序，并在表中显示每个文件的名称和长度。

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

此管道按指定顺序包含四个命令。 下图显示了每个命令的输出，因为它将传递到管道中的下一个命令。

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>使用管道

大多数 PowerShell cmdlet 都设计为支持管道。 在大多数情况下，你可以通过 _管道_ 将 **Get** cmdlet 的结果传递给相同名词的另一个 cmdlet。
例如，可以通过管道将 cmdlet 的输出传递 `Get-Service` 给 `Start-Service` 或 `Stop-Service` cmdlet。

此示例管道在计算机上启动 WMI 服务：

```powershell
Get-Service wmi | Start-Service
```

再例如，你可以通过管道将 `Get-Item` `Get-ChildItem` PowerShell 注册表提供程序的输出传递给 `New-ItemProperty` cmdlet。 此示例将值为 **8124** 的新注册表项 **NoOfEmployees** 添加到 **MyCompany** 注册表项。

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

许多实用工具 cmdlet （如、、、 `Get-Member` `Where-Object` 和） `Sort-Object` `Group-Object` `Measure-Object` 几乎只是在管道中使用。 可以通过管道将任何对象类型传递给这些 cmdlet。 此示例显示了如何按每个进程中打开的句柄数对计算机上的所有进程进行排序。

```powershell
Get-Process | Sort-Object -Property handles
```

可以通过管道将对象传递给格式设置、导出和输出 cmdlet，例如 `Format-List` 、、、 `Format-Table` `Export-Clixml` `Export-CSV` 和 `Out-File` 。

此示例演示如何使用 `Format-List` cmdlet 显示进程对象的属性列表。

```powershell
Get-Process winlogon | Format-List -Property *
```

使用几个实践，你会发现将简单命令合并到管道可节省时间和键入内容，并使你的脚本更有效。

## <a name="how-pipelines-work"></a>管道的工作方式

本部分介绍如何将输入对象绑定到 cmdlet 参数并在管道执行期间进行处理。

### <a name="accepts-pipeline-input"></a>接受管道输入

若要支持流水线，接收 cmdlet 必须具有接受管道输入的参数。 使用 `Get-Help` 带有 **Full** 或 **Parameter** 选项的命令来确定 cmdlet 接受管道输入的参数。

例如，若要确定 cmdlet 的哪些参数 `Start-Service` 接受管道输入，请键入：

```powershell
Get-Help Start-Service -Full
```

或

```powershell
Get-Help Start-Service -Parameter *
```

Cmdlet 的帮助 `Start-Service` 显示：只有 **InputObject** 和 **Name** 参数接受管道输入。

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

当你通过管道将对象发送到时 `Start-Service` ，PowerShell 会尝试将对象与 **InputObject** 和 **Name** 参数相关联。

### <a name="methods-of-accepting-pipeline-input"></a>接受管道输入的方法

Cmdlet 参数可采用以下两种不同方式之一接受管道输入：

- **ByValue**：参数接受与所需的 .net 类型匹配或可转换为该类型的值。

  例如，的 **Name** 参数 `Start-Service` 接受按值的管道输入。 它可以接受可以转换为字符串的字符串对象或对象。

- **ByPropertyName**：仅当输入对象具有与参数名称相同的属性时，此参数才接受输入。

  例如，的 Name 参数 `Start-Service` 可以接受具有 **Name** 属性的对象。 若要列出某个对象的属性，请将其传递到 `Get-Member` 。

一些参数可以通过值或属性名称接受对象，使从管道中获取输入变得更加容易。

### <a name="parameter-binding"></a>参数绑定

当你通过管道将对象从一个命令传递给另一个命令时，PowerShell 会尝试将管道对象与接收 cmdlet 的参数相关联。

PowerShell 的参数绑定组件根据以下条件将输入对象与 cmdlet 参数关联：

- 参数必须接受来自管道的输入。
- 参数必须接受要发送的对象的类型或可转换为预期类型的类型。
- 命令中未使用参数。

例如， `Start-Service` cmdlet 具有多个参数，但其中只有两个参数、 **名称** 和 **InputObject** 接受管道输入。 **Name** 参数使用字符串， **InputObject** 参数使用服务对象。 因此，可以通过管道字符串、服务对象和具有可转换为字符串或服务对象的属性的对象。

PowerShell 会尽可能有效地管理参数绑定。 不能建议或强制 PowerShell 绑定到特定参数。 如果 PowerShell 无法绑定管道对象，则该命令将失败。

有关排除绑定错误的详细信息，请参阅本文后面的 [调查管道错误](#investigating-pipeline-errors) 。

### <a name="one-at-a-time-processing"></a>一次一次性处理

通过管道将对象传递给命令与使用命令的参数来提交对象非常类似。 让我们看一看管道示例。 在此示例中，我们使用管道来显示服务对象表。

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

在功能上，这与使用的 **InputObject** 参数 `Format-Table` 来提交对象集合类似。

例如，我们可以将服务集合保存到使用 **InputObject** 参数传递的变量。

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

或者，可以将该命令嵌入到 **InputObject** 参数中。

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

但有一个重要的差异。 通过管道将多个对象传递给命令时，PowerShell 会一次将对象发送到命令。 使用命令参数时，对象将作为单个数组对象发送。 这种次要差别会产生重大后果。

执行管道时，PowerShell 会自动枚举任何实现接口的类型 `IEnumerable` ，并一次通过管道发送成员。 异常是 `[hashtable]` ，这需要调用 `GetEnumerator()` 方法。

在下面的示例中，将向 cmdlet 传递一个数组和一个哈希表， `Measure-Object` 以计算从管道接收的对象数。 该数组具有多个成员，并且哈希表具有多个键值对。 一次只枚举一个数组。

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

同样，如果你通过管道将多个进程对象传递 `Get-Process` 给 `Get-Member` cmdlet，则 PowerShell 会将每个进程对象一次发送到 `Get-Member` 。 `Get-Member` 显示 (类型的 .NET 类) 进程对象及其属性和方法。

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` 消除重复项，因此，如果所有对象都属于同一类型，则它只显示一种对象类型。

但是，如果使用的 **InputObject** 参数 `Get-Member` ，则会将 `Get-Member` **system.object** 对象的数组作为单个单元接收。 它显示对象数组的属性。  (记下 array 符号 (在 `[]` **system.object** 类型名称后面) 。 ) 

例如，应用于对象的

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

此结果可能不是你所期望的结果。 但在理解后，就可以使用它了。 例如，所有数组对象都具有 **Count** 属性。 可以使用它来计算计算机上运行的进程数。

例如，应用于对象的

```powershell
(Get-Process).count
```

请务必记住，在管道中发送的对象每次传递一次。

## <a name="investigating-pipeline-errors"></a>调查管道错误

当 PowerShell 无法将管道对象与接收 cmdlet 的参数关联时，该命令将失败。

在下面的示例中，我们尝试将注册表项从一个注册表项移到另一个注册表项。 该 `Get-Item` cmdlet 将获取目标路径，然后将该路径传递给 `Move-ItemProperty` cmdlet。 `Move-ItemProperty`命令指定要移动的注册表项的当前路径和名称。

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

命令失败，PowerShell 将显示以下错误消息：

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

若要进行调查，请使用 `Trace-Command` cmdlet 跟踪 PowerShell 的参数绑定组件。 下面的示例跟踪管道的执行过程中的参数绑定。 **PSHost** 参数将跟踪结果显示在控制台中， **FilePath** 参数会将跟踪结果发送到 `debug.txt` 文件，供以后参考。

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

跟踪的结果很长，但会显示绑定到 cmdlet 的值，然后显示 `Get-Item` 绑定到 cmdlet 的命名值 `Move-ItemProperty` 。

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

最后，它显示尝试将路径绑定到的 **目标** 参数 `Move-ItemProperty` 失败。

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

使用 `Get-Help` cmdlet 查看 **目标** 参数的属性。

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

结果显示 **目标** 仅按属性名称获取管道输入。 因此，管道对象必须具有一个名为 " **Destination**" 的属性。

使用 `Get-Member` 可查看来自的对象的属性 `Get-Item` 。

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

输出显示该项目是没有 **目标** 属性的 **Microsoft. Win32** 对象。 这说明了命令失败的原因。

**Path** 参数按名称或值接受管道输入。

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

若要修复此命令，必须在 cmdlet 中指定目标 `Move-ItemProperty` ，并使用 `Get-Item` 获取要移动的项的 **路径** 。

例如，应用于对象的

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>内部续行符

正如前面所讨论的，管道是一系列由管道运算符连接的命令 (`|`) ，通常在一行上写入。 但是，为了提高可读性，PowerShell 允许跨多个行拆分管道。
当管道运算符是行上的最后一个标记时，PowerShell 分析器会将下一行连接到当前命令以继续构造管道。

例如，以下单行管道：

```powershell
Command-1 | Command-2 | Command-3
```

可以编写为：

```powershell
Command-1 |
  Command-2 |
    Command-3
```

后续行中的前导空格并不重要。 缩进增强了可读性。

PowerShell 7 增加了对管道的延续的支持，并在行的开头提供管道字符。 下面的示例演示如何使用此新功能。

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> 在 shell 中以交互方式工作时，仅当使用<kbd>Ctrl</kbd> + <kbd>V</kbd>粘贴时，才将代码粘贴到行的开头。
> 右键单击 "粘贴操作"，一次插入一个行。 因为行不以管道字符结尾，所以 PowerShell 会将输入视为已完成，并按输入执行该行。

## <a name="see-also"></a>另请参阅

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)

