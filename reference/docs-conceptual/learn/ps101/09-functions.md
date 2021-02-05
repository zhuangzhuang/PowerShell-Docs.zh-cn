---
title: 函数
description: 通过 PowerShell 函数，你可以创建可在脚本中重用的工具。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e4734b556a78f67c54152dad93eada536dd1c928
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596613"
---
# <a name="chapter-9---functions"></a>第 9 章 - 函数

如果你正在编写 PowerShell 单行程序或脚本，并发现你经常需要针对不同的场景对其进行修改，则可以考虑将其转换为可重用的函数。

只要有可能，我更喜欢编写函数，因为它们更具有工具导向性。 我可以将函数放在脚本模块中，将该模块放在 `$env:PSModulePath` 中，然后调用这些函数，而无需查找它们的实际保存位置。 使用 PowerShellGet 模块，可以轻松地在 NuGet 存储库中共享这些模块。 PowerShellGet 随 PowerShell 版本 5.0 及更高版本提供。 对于 PowerShell 版本 3.0 及更高版本，它可以作为单独的下载提供。

不要将事情复杂化。 保持简单，并使用最直接的方式完成任务。 避免在重用的任何代码中使用别名和位置参数。 设置代码的格式以提高可读性。 不要对值进行硬编码；使用参数和变量。 不要编写不必要的代码，即使它不会造成任何损害。 它增加了不必要的复杂性。 编写任何 PowerShell 代码时，请注意细节。

## <a name="naming"></a>命名

在 PowerShell 中命名函数时，结合使用[帕斯卡拼写法][]名称和已批准的谓词和单数名词。 我还建议在名词前面加上前缀。 例如：`<ApprovedVerb>-<Prefix><SingularNoun>`。

PowerShell 中有一个批准的谓词的特定列表，可通过运行 `Get-Verb` 获取这些谓词。

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

在前面的示例中，我已按照“谓词”列对结果进行排序。 通过“组”列，你可以了解这些谓词的用法。 将函数添加到模块时，请务必在 PowerShell 中选择一个批准的谓词。 如果选择未批准的谓词，模块将在加载时生成警告消息。 该警告消息使函数看起来不专业。 未批准的谓词还会限制函数的可发现性。

## <a name="a-simple-function"></a>简单函数

PowerShell 中的函数使用函数关键字声明，后面依次跟函数名称、左大括号和右大括号。 函数将执行的代码包含在这些大括号中。

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

显示的函数是返回 PowerShell 版本的简单示例。

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

名称很可能与名称类似于 `Get-Version` 的函数以及 PowerShell 中的默认命令或其他人可能编写的命令发生冲突。 因此，我建议为函数的名词部分加上前缀以防止命名冲突。 在下面的示例中，我将使用前缀“PS”。

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

除了名称外，此函数与上一个函数相同。

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

即使在名词前面加上前缀（如 PS），仍可能出现名称冲突。 我通常使用我的姓名缩写作为函数名词的前缀。 制定标准并坚持遵循。

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

此函数与前两个函数没有什么不同，唯一区别是它使用更合理的名称，以防止与其他 PowerShell 命令发生命名冲突。

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

加载到内存后，可在函数 PSDrive 上查看函数。

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

如果要从当前会话中删除这些函数，则必须从函数 PSDrive 中将其删除，或关闭之后再重新打开 PowerShell。

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

验证是否确实删除了函数。

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

如果函数是作为模块的一部分加载的，则可以卸载模块以删除它们。

```powershell
Remove-Module -Name <ModuleName>
```

`Remove-Module` cmdlet 从当前 PowerShell 会话中的内存中删除模块，不会从系统或磁盘中删除模块。

## <a name="parameters"></a>参数

请勿静态分配值！ 使用参数和变量。 命名参数时，请尽可能使用与默认 cmdlet 相同的名称作为参数名称。

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

我为什么使用 ComputerName 而不是 Computer、ServerName 或 Host 作为参数名称   ？ 这是因为我希望函数像默认 cmdlet 一样标准化。

我将创建一个函数，用于查询系统上的所有命令并返回具有特定参数名称的命令数量。

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

正如下面的结果所示，有 39 个命令具有 ComputerName 参数。 没有任何 cmdlet 具有 Computer、ServerName、Host 或 Machine 这样的参数   。

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

我还建议对参数名称使用与默认 cmdlet 相同的大小写。 使用 `ComputerName`，而不是 `computername`。 这会使你的函数看起来像默认 cmdlet。 已经熟悉 PowerShell 的用户会感到得心应手。

`param`语句允许您定义一个或多个参数。 参数定义由逗号分隔 (`,`) 。 有关详细信息，请参阅 [about_Functions_Advanced_Parameters][]。

## <a name="advanced-functions"></a>高级函数

将 PowerShell 中的函数转换为高级函数非常简单。 函数与高级函数之间的一个区别是，高级函数具有多个自动添加到函数的通用参数。 这些通用参数包括 Verbose 和 Debug 。

我将从上一部分中使用的 `Test-MrParameter` 函数开始介绍。

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

请注意，`Test-MrParameter` 函数没有任何通用参数。 可以通过多种不同的方法来查看通用参数。 其中一种方法是使用 `Get-Command` 查看语法。

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

另一种方法是通过 `Get-Command` 向下钻取参数。

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

添加 `CmdletBinding` 以将函数转换为高级函数。

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

添加 `CmdletBinding` 会自动添加通用参数。 `CmdletBinding` 需要一个 `param` 块，但 `param` 块可以为空。

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

通过 `Get-Command` 向下钻取参数会显示实际参数名称，包括常见参数名称。

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` 会添加 WhatIf 和 Confirm 参数 。 只有做出更改的命令需要这些参数。

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

请注意，现在有 WhatIf 和 Confirm 参数 。

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

同样，还可以使用 `Get-Command` 返回实际参数名称列表，其中包括常见参数名称以及 WhatIf 和 Confirm。

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>参数验证

尽早验证输入。 如果不可能在没有有效输入的情况下运行代码，那为什么允许代码在某路径上继续运行？

始终键入要用于参数的变量（指定数据类型）。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

在前面的示例中，我指定了 String 作为 ComputerName 参数的数据类型 。 这将导致它只允许指定一个计算机名。 如果通过以逗号分隔的列表指定了多个计算机名，则会生成错误。

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

当前定义的问题在于省略 ComputerName 参数的值是有效的，但需要一个值才能成功完成该函数。 这时 `Mandatory` 参数属性就发挥作用了。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

前面的示例中使用的语法为 PowerShell 版本 3.0 及更高兼容版本。
可以改为指定 `[Parameter(Mandatory=$true)]`，以使函数与 PowerShell 版本 2.0 及更高版本兼容。 现在 ComputerName 是必需的，如果未指定，该函数将提示输入名称。

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

如果要允许 ComputerName 参数具有多个值，请使用 String 数据类型，但应向该数据类型添加左方括号和右方括号以允许字符串数组 。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

也许你想为 ComputerName 参数指定一个默认值（如果未指定）。
问题在于，默认值不能与必需参数一起使用。 你需要将 `ValidateNotNullOrEmpty` 参数验证属性与默认值一起使用。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

即使在设置默认值时，也不要使用静态值。 在上面的示例中，`$env:COMPUTERNAME` 用作默认值，如果未提供值，该默认值将自动转换为本地计算机名。

## <a name="verbose-output"></a>详细输出

尽管内联注释非常有用（尤其是在编写一些复杂的代码时），但用户不会看到这些注释，除非他们查看代码本身。

下面的示例中显示的函数在 `foreach` 循环中具有内联注释。 虽然这种特定注释可能并不难找到，但如果函数包含数百个代码行，就很麻烦。

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

一种更好的选择是使用 `Write-Verbose` 而不是内联注释。

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

如果在没有 Verbose 参数的情况下调用函数，则不会显示详细输出。

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

通过 Verbose 参数调用函数时，会显示详细输出。

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>管道输入

如果希望函数接受管道输入，则需要进行一些额外的编码。 如本书前面所述，命令可以接受按值（按类型）或按属性名称显示的管道输入 。 可以像编写本机命令那样编写函数，以便它们接受其中一种或两种类型的输入。

若要接受按值显示管道输入，请为该特定参数指定 `ValueFromPipeline` 参数属性。 请记住，只能接受每种数据类型中按值显示的管道输入。 例如，如果有两个接受字符串输入的参数，则只有其中一个参数可以接受按值显示的管道输入，因为如果为两个字符串参数都指定了管道输入，则该管道输入不知道该绑定到哪个参数。 这就是我调用此类型的按类型显示的管道输入（而不是按值显示的管道输入）的另一个原因。

管道输入一次输入一个项，这类似于在 `foreach` 循环中处理项的方式。
如果要接受数组作为输入，则至少需要一个 `process` 块才能处理所有项。 如果只接受单个值作为输入，则不需要 `process` 块，但仍建议指定它以保持一致性。

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

接受按属性名称显示的管道输入是类似的，但它是使用 `ValueFromPipelineByPropertyName` 参数属性指定的，并且可为任意数量的参数指定该输入，无需考虑数据类型。 关键在于，通过管道传送的命令输出必须具有与参数名称或函数的参数别名匹配的属性名称。

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN` 和 `END` 块是可选的。 `BEGIN` 在 `PROCESS` 块之前指定，用于在从管道接收项之前执行任何初始工作。 了解这一点很重要。 在 `BEGIN` 块中无法访问通过管道传入的值。 `END` 块将在 `PROCESS` 块之后指定，用于在处理完通过管道传入的所有值之后进行清理。

## <a name="error-handling"></a>错误处理

当无法联系计算机时，以下示例中显示的函数会生成未经处理的异常。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

可采用多种不同的方法在 PowerShell 中处理错误。 `Try/Catch` 是处理错误的较新式的方法。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

尽管上面的示例中显示的函数使用错误处理，但它也会生成未经处理的异常，因为该命令不会生成终止错误。 了解这一点也很重要。 仅捕获终止错误。 将 ErrorAction 参数的值指定为 Stop，将非终止错误转换为终止错误 。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

除非确实有必要，否则请勿修改全局 `$ErrorActionPreference` 变量。 如果直接从 PowerShell 函数内使用 .NET 之类的内容，则不能针对命令本身指定 ErrorAction。 在这种情况下，你可能需要更改全局 `$ErrorActionPreference` 变量，但如果确实要更改它，请在尝试执行命令后立即将其更改回来。

## <a name="comment-based-help"></a>基于注释的帮助

最佳做法是将基于注释的帮助添加到函数，以便你与之共享函数的人知道如何使用它们。

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

如果将基于注释的帮助添加到函数，可以像默认的内置命令一样为他们检索帮助。

用于在 PowerShell 中编写函数的所有语法似乎过于复杂，尤其是对于刚入门的用户。 通常，如果我不记得语法的某些内容，我会在单独的监视器上打开 ISE 的第二个副本，并在键入函数代码时查看“Cmdlet (高级函数) - 完成”代码片段。 可以使用 <kbd>Ctrl</kbd>+<kbd>J</kbd> 组合键在 PowerShell ISE 中访问代码片段。

## <a name="summary"></a>总结

在本章中，你已了解有关在 PowerShell 中编写函数的基本知识，其中包括如何将函数转变为高级函数，以及在编写 PowerShell 函数（如参数验证、详细输出、管道输入、错误处理和基于注释的帮助）时应考虑的一些较重要的要素。

## <a name="review"></a>审阅

1. 如何在 PowerShell 中获取批准的谓词的列表？
1. 如何将 PowerShell 函数转换为高级函数？
1. 应在何时将 WhatIf 和 Confirm 参数添加到 PowerShell 函数 ？
1. 如何将非终止错误转换为终止错误？
1. 为什么应该将基于注释的帮助添加到函数？

## <a name="recommended-reading"></a>推荐阅读的主题

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [视频：使用高级函数和脚本模块的 PowerShell 工具制作][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[视频：使用高级函数和脚本模块的 PowerShell 工具制作]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[帕斯卡拼写法]: /dotnet/standard/design-guidelines/capitalization-conventions
