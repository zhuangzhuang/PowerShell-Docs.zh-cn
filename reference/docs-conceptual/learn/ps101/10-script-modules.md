---
title: 脚本模块
description: 脚本模块是将脚本和函数打包为可重复使用的工具的一种简单方法。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: c557c071bc202a4216a77e7e5ae0bd73b4bc014b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596817"
---
# <a name="chapter-10---script-modules"></a>第 10 章 - 脚本模块

如果要频繁使用，则将 PowerShell 中的单行命令和脚本转换为可重复使用的工具甚至更重要。 在脚本模块中打包函数可让它们看起来更专业，并更容易共享。

## <a name="dot-sourcing-functions"></a>Dot-Sourcing 函数

我们在上一章中未讨论 Dot-Sourcing 函数。 如果脚本中的函数不是模块的一部分，则将其加载到内存中的唯一方法是对保存该脚本的 `.PS1` 文件进行“dot-source”操作。

以下函数已另存为 `Get-MrPSVersion.ps1`。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

运行脚本时，不会发生任何事情。

```powershell
.\Get-MrPSVersion.ps1
```

如果尝试调用函数，则会生成错误消息。

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

可检查函数是否存在于 Function PSDrive 上，以确定函数是否加载到内存中。

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

调用包含函数的脚本时出现的问题是，函数加载到 Script 作用域中。 脚本完成后，将删除该作用域，并随之一起删除该函数。

需要将函数加载到 Global 作用域中。 可通过对包含函数的脚本进行“dot-source”操作来完成此操作。 可使用相对路径。

```powershell
. .\Get-MrPSVersion.ps1
```

也可以使用完全限定的路径。

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

如果部分路径存储在变量中，则它可以与路径的其余部分结合使用。
没有理由使用字符串串联将变量与路径的其余部分组合在一起。

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

现在，当我检查 Function PSDrive 时，存在 `Get-MrPSVersion` 函数。

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>脚本模块

PowerShell 中的脚本模块只是一个文件，其中包含一个或多个保存为 `.PSM1` 文件而不是 `.PS1` 文件的函数。

如何创建脚本模块？ 你可能会猜测使用名称类似于 `New-Module` 的命令。 你的假设是错误的。 虽然 PowerShell 中有一个名为 `New-Module` 的命令，但该命令创建的是一个动态模块，而不是脚本模块。 即使你认为找到了所需命令，也应始终确保阅读命令帮助。

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

在上一章中，我提到函数应使用已批准的谓词，否则在导入模块时，它们将生成一条警告消息。 下面的代码使用 `New-Module` cmdlet 在内存中创建动态模块。 此模块演示未批准的谓词警告。

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

重申一下，虽然在上一示例中使用了 `New-Module` cmdlet，但这不是用于在 PowerShell 中创建脚本模块的命令。

将以下两个函数保存在名为 `MyScriptModule.psm1` 的文件中。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

尝试调用某个函数。

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

一条错误消息随即生成，表明找不到该函数。 你还可以像以前一样检查 Function PSDrive，但会发现它也不存在。

可以用 `Import-Module` cmdlet 手动导入文件。

```powershell
Import-Module C:\MyScriptModule.psm1
```

模块自动加载功能是在 PowerShell 版本 3 中引入的。 要利用模块自动加载，需要将脚本模块保存在与 `.PSM1` 文件具有相同基名称的文件夹中，并保存在 `$env:PSModulePath` 中指定的位置。

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

结果很难读取。 由于路径是用分号分隔的，因此可以拆分结果，在单独的行上返回每个路径。 这样就更容易进行读取。

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

列表中的前三个路径是默认路径。 安装 SQL Server Management Studio 后，会添加最后一个路径。 要使模块自动加载功能正常工作，`MyScriptModule.psm1` 文件需要直接位于其中某个路径内名为 `MyScriptModule` 的文件夹中。

没那么快。 对于我来说，当前用户路径不是列表中的第一个路径。 我几乎从未使用过该路径，因为我用于登录 Windows 的用户名与用于运行 PowerShell 的用户名不同。 这意味着它不在我的标准“文档”文件夹中。

第二个路径是 AllUsers 路径。 这是我存储所有模块的位置。

第三个路径位于 `C:\Windows\System32` 之下。 只有 Microsoft 才应在该位置存储模块，因为它位于操作系统文件夹内。

`.PSM1` 文件位于正确的路径中后，调用某个模块命令时，将自动加载该模块。

## <a name="module-manifests"></a>模块清单

所有模块都应该有一个模块清单。 模块清单包含有关模块的元数据。
模块清单文件的文件扩展名是 `.PSD1`。 并非所有扩展名为 `.PSD1` 的文件都是模块清单。 它们还可用于存储 DSC 配置的环境部分等用途。 `New-ModuleManifest` 用于创建模块清单。 Path 是所需的唯一值。 但是，如果未指定 RootModule，则该模块将不起作用。 如果决定使用 PowerShellGet 将模块上传到 NuGet 存储库，最好指定 Author 和 Description，因为该情况需要这些值 。

不带清单的模块版本为 0.0。 模块没有清单是一个致命的漏洞。

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

可以使用所有建议的信息创建模块清单。

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

如果在模块清单初始创建期间丢失了任何此信息，则可稍后使用 `Update-ModuleManifest` 添加或更新该信息。 已创建清单后，请勿使用 `New-ModuleManifest` 重新创建清单，因为 GUID 将更改。

## <a name="defining-public-and-private-functions"></a>定义公共和专用函数

你可能想要将帮助程序函数用作私有函数，仅允许模块中的其他函数访问， 而不允许模块的用户访问。 可以通过几种不同方法实现此目的。

如果未遵循最佳做法并且只有一个 `.PSM1` 文件，则唯一的选择是使用 `Export-ModuleMember` cmdlet。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

在上面的示例中，只有 `Get-MrPSVersion` 函数可供模块的用户使用，但 `Get-MrComputerName` 函数可供模块本身包含的其他函数使用。

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

如果已将模块清单添加到模块（且应该这样做），建议在模块清单的 FunctionsToExport 部分中指定要导出的各个函数。

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

不需要在 `.PSM1` 文件和模块清单的 FunctionsToExport 部分同时使用两个 `Export-ModuleMember`。 使用其中一个已足够。

## <a name="summary"></a>总结

在本章中，你已了解如何在 PowerShell 中将函数转换为脚本模块。 还了解了一些用于创建脚本模块的最佳做法，例如，为脚本模块创建模块清单。

## <a name="review"></a>审阅

1. 如何在 PowerShell 中创建脚本模块？
1. 为什么函数必须使用已批准的谓词？
1. 如何在 PowerShell 中创建模块清单？
1. 哪两个选项仅用于导出模块中的特定函数？
1. 调用命令时，自动加载模块需要执行哪些操作？

## <a name="recommended-reading"></a>推荐阅读的主题

- [如何创建 PowerShell 脚本模块和模块清单][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Export-ModuleMember][]

<!-- link references -->
[如何创建 PowerShell 脚本模块和模块清单]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
