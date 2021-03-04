---
title: 关于异常的各项须知内容
description: 错误处理只是编写代码时的一部分工作。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 589e5d1decff7aa49ce36e10908e4464a768758d
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685510"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>关于异常的各项须知内容

错误处理只是编写代码时的一部分工作。 我们通常可以检查并验证预期行为的条件。 发生意外情况时，我们会转向异常处理。 你可以轻松处理他人的代码生成的异常，也可以自己生成一些异常让他人去处理。

> [!NOTE]
> 本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。 PowerShell 团队感谢 Kevin 与我们分享这篇文章。 请前往 [PowerShellExplained.com][] 访问他的博客。

## <a name="basic-terminology"></a>基本术语

在进入正题之前，我们需要介绍一些基本术语。

### <a name="exception"></a>异常

异常就是常规错误处理程序无法处理问题时创建的事件。
尝试将数字除以零或内存不足等都会造成异常。 有时，你使用的代码的作者会在某些问题发生时为它们创建异常。

### <a name="throw-and-catch"></a>Throw 和 Catch

发生异常时，我们会说一个异常被引发。 若要处理引发的异常，需要将其捕获。 如果异常被引发但未被捕获，则脚本将停止执行。

### <a name="the-call-stack"></a>调用堆栈

调用堆栈是相互调用的函数的列表。 当调用一个函数时，它将被添加到堆栈或列表的顶部。 当函数退出或返回时，它将从堆栈中移除。

当引发异常时，将检查该调用堆栈，以便异常处理程序捕获异常。

### <a name="terminating-and-non-terminating-errors"></a>终止和非终止错误

异常通常是终止错误。 引发的异常要么被捕获要么会终止当前执行程序。 默认情况下，`Write-Error` 会生成一个非终止错误，并将错误添加到输出流，而不引发异常。

我指出这一点，是因为 `Write-Error` 和其他非终止错误不会触发 `catch`。

### <a name="swallowing-an-exception"></a>忽略异常

在这种情况下，捕获错误只是为了抑制它。 这样做时要谨慎，因为它会使故障排除变得非常困难。

## <a name="basic-command-syntax"></a>基本命令语法

下面简要概述了 PowerShell 中使用的基本异常处理语法。

### <a name="throw"></a>Throw

若要创建自己的异常事件，请使用 `throw` 关键字引发异常。

```powershell
function Start-Something
{
    throw "Bad thing happened"
}
```

这会创建一个属于终止错误的运行时异常。 它由调用函数中的 `catch` 进行处理，或者退出脚本，并显示如下消息：

```powershell
PS> Start-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Write-Error -ErrorAction Stop

我提到过，默认情况下 `Write-Error` 不会引发终止错误。 如果指定 `-ErrorAction Stop`，`Write-Error` 会生成一个可使用 `catch` 处理的终止错误。

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

感谢 Lee Dailey 提醒我可以这样使用 `-ErrorAction Stop`。

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet -ErrorAction Stop

如果在任何高级函数或 cmdlet 上指定 `-ErrorAction Stop`，它会把所有 `Write-Error` 语句转为终止错误，这些错误会使执行停止或可由 `catch` 处理。

```powershell
Start-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/Catch

PowerShell（以及许多其他语言）中的异常处理方式是，先对一部分代码执行 `try`，如果引发错误，则对其执行 `catch`。 下面是一个简单的例子。

```powershell
try
{
    Start-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Start-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

`catch` 脚本仅在出现终止错误时才会运行。 如果 `try` 正确执行，则会跳过 `catch`。

### <a name="tryfinally"></a>Try/Finally

有时，你不需要处理错误，但无论异常是否发生，仍需要执行一些代码。 `finally` 脚本正是做的这一点。

请看下面的示例：

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

无论何时打开或连接到资源，都应将其关闭。 如果 `ExecuteNonQuery()` 引发异常，则连接不会关闭。 下面是 `try/finally` 块内的相同代码。

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

在本例中，如果出现错误，则连接关闭。 如果没有错误，也会将其关闭。 每次都会运行 `finally` 脚本。

由于未捕获异常，它仍会在调用堆栈中向上传播。

### <a name="trycatchfinally"></a>Try/Catch/Finally

同时使用 `catch` 和 `finally` 是非常有效的。 大多数情况下，你将使用其中一个，但也可能会有两种都使用的情况。

## <a name="psitem"></a>$PSItem

现在我们已经了解了基本知识，下面可以更深入地了解。

在 `catch` 块内，有一个类型为 `ErrorRecord` 的自动变量（`$PSItem` 或 `$_`），其中包含有关异常的详细信息。 下面是一些关键属性的简要概述。

对于这些示例，我在 `ReadAllText` 中使用了一个无效路径来生成此异常。

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem.ToString()

这为你提供了最简洁的消息来用于日志记录和常规输出。 如果将 `$PSItem` 放在字符串中，将自动调用 `ToString()`。

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem.InvocationInfo

此属性包含 PowerShell 收集的有关引发异常的函数或脚本的其他信息。 下面是我创建的示例异常中的 `InvocationInfo`。

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

此处的重要详细信息显示了 `ScriptName`、代码 `Line` 和调用开始时的 `ScriptLineNumber`。

### <a name="psitemscriptstacktrace"></a>$PSItem.ScriptStackTrace

此属性显示函数调用顺序，这些函数调用会将你带到生成异常的代码。

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Start-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

我只调用同一脚本中的函数，但如果涉及多个脚本，则会跟踪调用。

### <a name="psitemexception"></a>$PSItem.Exception

这是实际引发的异常。

#### <a name="psitemexceptionmessage"></a>$PSItem.Exception.Message

这是描述异常的一般消息，在进行故障排除时，这是一个很好的起点。 大多数异常都有默认消息，但也可以在引发异常时设置自定义消息。

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

这也是在调用 `$PSItem.ToString()` 时返回的消息（如果未在 `ErrorRecord` 中设置）。

#### <a name="psitemexceptioninnerexception"></a>$PSItem.Exception.InnerException

异常可能包含内部异常。 当调用的代码捕获异常并引发其他异常时，通常会发生这种情况。 原始异常放置在新异常中。

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

稍后讨论重新引发异常时我会回顾此内容。

#### <a name="psitemexceptionstacktrace"></a>$PSItem.Exception.StackTrace

这是面向异常的 `StackTrace`。 我在上文展示了 `ScriptStackTrace`，但这个属性适用于对托管代码的调用。

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

仅当从托管代码引发事件时，才会获取此堆栈跟踪。 我直接调用了 .NET Framework 函数，因此这就是我们在本例中可以看到的所有内容。 通常，当你查看堆栈跟踪时，你是在寻找代码停止以及系统调用开始的位置。

## <a name="working-with-exceptions"></a>处理异常

除了基本语法和异常属性以外，异常还有很有内容。

### <a name="catching-typed-exceptions"></a>捕获类型化异常

你可以有选择地处理捕获的异常。 异常具有类型，你可以指定要捕获的异常类型。

```powershell
try
{
    Start-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

针对每个 `catch` 块检查异常类型，直到找到与你的异常匹配的块。
必须认识到，异常可继承自其他异常。 在上面的示例中，`FileNotFoundException` 继承自 `IOException`。 因此，如果 `IOException` 在前，则会改为调用它。 即使有多个匹配项，也只调用一个 catch 块。

如果有 `System.IO.PathTooLongException`，则 `IOException` 会匹配，但如果有 `InsufficientMemoryException`，则不会捕获到它，它会向上传播堆栈。

### <a name="catch-multiple-types-at-once"></a>一次捕获多种类型

可以用相同的 `catch` 语句来捕获多个异常类型。

```powershell
try
{
    Start-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

感谢 `/u/Sheppard_Ra` 建议添加此内容。

### <a name="throwing-typed-exceptions"></a>引发类型化异常

可以在 PowerShell 中引发类型化异常。 不要使用字符串调用 `throw`：

```powershell
throw "Could not find: $path"
```

使用如下所示的异常加速器：

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

但在这样做时必须指定一条消息。

你还可以创建要引发的异常的新实例。 这样做时，消息是可选的，因为系统对所有内置异常都有默认消息。

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

如果未使用 PowerShell 5.0 或更高版本，则必须使用较旧的 `New-Object` 方法。

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

通过使用类型化异常，你（或其他人）可以按上一部分提到的类型捕获异常。

#### <a name="write-error--exception"></a>Write-Error -Exception

我们可以将这些类型化异常添加到 `Write-Error` 中，我们仍然可以按异常类型来 `catch` 错误。 使用 `Write-Error`，如以下示例所示：

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

接下来，我们可以像这样捕获它：

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>.NET 异常大列表

在 [Reddit/r/PowerShell 社区][]的帮助下，我编译了一个包含数百个 .NET 异常的总览表，作为对本文的补充。

- [.NET 异常大列表][]

我首先在列表中搜索那些感觉适合我当前情况的异常。 你应尝试在基本 `System` 命名空间中使用异常。

### <a name="exceptions-are-objects"></a>异常为对象

当你开始大量使用类型化异常时，请记住它们是对象。 不同的异常具有不同的构造函数和属性。 如果查看 [FileNotFoundException][] 文档中的 `System.IO.FileNotFoundException`，我们就会知道可以传入消息和文件路径。

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

它具有公开该文件路径的 `FileName` 属性。

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

若要了解其他构造函数和对象属性，应参阅 [.NET 文档][]。

### <a name="re-throwing-an-exception"></a>重新引发异常

如果在 `catch` 块中要做的只是 `throw` 同一个异常，那么就不要 `catch` 它。 在发生异常时，应仅对计划处理的异常执行 `catch` 或某些操作。

有时，你需要对异常执行操作，但要重新引发异常，以便下游能够处理该异常。 我们可以在发现问题的位置附近编写消息或记录问题，但在堆栈的更上层处理问题。

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

有趣的是，我们可以从 `catch` 内调用 `throw`，它会重新引发当前异常。

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

我们想要重新引发异常，以保留原始执行信息，如源脚本和行号。 如果此时引发新异常，它将隐藏异常开始的位置。

#### <a name="re-throwing-a-new-exception"></a>重新引发新异常

如果捕获到一个异常，但想要引发另一个异常，则应将原始异常嵌套在新异常内。 这样一来，堆栈下游的人就可以将其作为 `$PSItem.Exception.InnerException` 进行访问。

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet.ThrowTerminatingError()

我不喜欢对原始异常使用 `throw` 的一个原因是，错误消息指向 `throw` 语句，并指示该行是问题所在。

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```

让错误消息告诉我脚本已损坏，因为我在第 31 行调用了 `throw`，这对于你的脚本用户来说是一个坏消息。 它没有提供任何有用的内容。

Dexter Dhami 指出，我可以使用 `ThrowTerminatingError()` 来纠正此问题。

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

如果假定在名为 `Get-Resource` 的函数中调用了 `ThrowTerminatingError()`，那么以下就是我们将会看到的错误。

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

你是否明白它如何指向 `Get-Resource` 函数作为问题来源？ 这会告诉用户一些有用的信息。

由于 `$PSItem` 是 `ErrorRecord`，因此还可以使用 `ThrowTerminatingError` 以这种方式重新引发。

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

这会将错误源更改为 Cmdlet，并向 Cmdlet 用户隐藏函数内部信息。

## <a name="try-can-create-terminating-errors"></a>Try 可能会创建终止错误

Kirk Munro 指出，某些异常仅在 `try/catch` 块内执行时为终止错误。 下面是他为我提供的一个示例，其中生成了一个除以零的运行时异常。

```powershell
function Start-Something { 1/(1-1) }
```

然后像这样调用它，可以看到它生成错误并仍然输出消息。

```powershell
&{ Start-Something; Write-Output "We did it. Send Email" }
```

但通过在 `try/catch` 中放置相同代码，我们可以看到发生了一些别的情况。

```powershell
try
{
    &{ Start-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```

我们看到错误变成终止错误，且没有输出第一条消息。 我不喜欢这个的原因是，你可以在函数中使用此代码，如果用户使用 `try/catch`，则其行为方式会不同。

我自己尚未遇到这方面的问题，但这是需要注意的极端情况。

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet.ThrowTerminatingError() inside try/catch

`$PSCmdlet.ThrowTerminatingError()` 的一项细微差别在于，它在 Cmdlet 中创建了一个终止错误，但会在离开 Cmdlet 后变成非终止错误。 这就把决定如何处理错误的负担留给了函数调用者。 它们可以通过使用 `-ErrorAction Stop` 或从 `try{...}catch{...}` 中进行调用来将其转换回终止错误。

### <a name="public-function-templates"></a>公共函数模板

我与 Kirk Munro 谈论的最后一个要点是，他在所有高级函数的每个 `begin`、`process` 和 `end` 块周围放置了 `try{...}catch{...}`。 在这些泛型 catch 块中，他使用 `$PSCmdlet.ThrowTerminatingError($PSItem)` 作为单个行来处理所有离开函数的异常。

```powershell
function Start-Something
{
    [CmdletBinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSItem)
        }
    }
}
```

由于所有内容都位于其函数内的 `try` 语句中，因此所有内容的行为一致。 这还会向最终用户提供简洁的错误信息，对生成的错误隐藏内部代码。

## <a name="trap"></a>Trap

我将重点放在了异常的 `try/catch` 方面。 但在结束之前，我需要提到一项旧功能。

将 `trap` 放置在脚本或函数中，可捕获在该作用域内发生的所有异常。 发生异常时，将执行 `trap` 中的代码，然后继续执行正常代码。 如果发生多个异常，则会反复调用 trap。

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

我个人从未用过这种方法，但我可以在记录任何和所有异常的管理员或控制器脚本中看到该值，然后仍继续执行。

## <a name="closing-remarks"></a>结束语

向脚本添加适当的异常处理不仅使其更稳定，还可以让你更轻松地对异常进行故障排除。

我花了很多时间来谈论 `throw`，因为这是异常处理的一个核心概念。 PowerShell 还向我们提供了 `Write-Error`，它可处理要使用 `throw` 的所有情况。 所以，在阅读本文后，不要认为你需要使用 `throw`。

现在，我已经花了一些时间详述了异常处理，接下来将转换话题，探讨使用 `Write-Error -Stop` 在代码中生成错误。 我还将采纳 Kirk 的建议，将 `ThrowTerminatingError` 设为针对每个函数的必备异常处理程序。

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[原始版本]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/PowerShell 社区]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[.NET 异常大列表]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: /dotnet/api/System.IO.FileNotFoundException
[.NET 文档]: /dotnet/api
