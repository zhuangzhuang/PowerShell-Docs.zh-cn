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
# <a name="chapter-10---script-modules"></a><span data-ttu-id="f5421-103">第 10 章 - 脚本模块</span><span class="sxs-lookup"><span data-stu-id="f5421-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="f5421-104">如果要频繁使用，则将 PowerShell 中的单行命令和脚本转换为可重复使用的工具甚至更重要。</span><span class="sxs-lookup"><span data-stu-id="f5421-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="f5421-105">在脚本模块中打包函数可让它们看起来更专业，并更容易共享。</span><span class="sxs-lookup"><span data-stu-id="f5421-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="f5421-106">Dot-Sourcing 函数</span><span class="sxs-lookup"><span data-stu-id="f5421-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="f5421-107">我们在上一章中未讨论 Dot-Sourcing 函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="f5421-108">如果脚本中的函数不是模块的一部分，则将其加载到内存中的唯一方法是对保存该脚本的 `.PS1` 文件进行“dot-source”操作。</span><span class="sxs-lookup"><span data-stu-id="f5421-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="f5421-109">以下函数已另存为 `Get-MrPSVersion.ps1`。</span><span class="sxs-lookup"><span data-stu-id="f5421-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="f5421-110">运行脚本时，不会发生任何事情。</span><span class="sxs-lookup"><span data-stu-id="f5421-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="f5421-111">如果尝试调用函数，则会生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="f5421-111">If you try to call the function, it generates an error message.</span></span>

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

<span data-ttu-id="f5421-112">可检查函数是否存在于 Function PSDrive 上，以确定函数是否加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="f5421-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

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

<span data-ttu-id="f5421-113">调用包含函数的脚本时出现的问题是，函数加载到 Script 作用域中。</span><span class="sxs-lookup"><span data-stu-id="f5421-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="f5421-114">脚本完成后，将删除该作用域，并随之一起删除该函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="f5421-115">需要将函数加载到 Global 作用域中。</span><span class="sxs-lookup"><span data-stu-id="f5421-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="f5421-116">可通过对包含函数的脚本进行“dot-source”操作来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="f5421-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="f5421-117">可使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="f5421-118">也可以使用完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="f5421-119">如果部分路径存储在变量中，则它可以与路径的其余部分结合使用。</span><span class="sxs-lookup"><span data-stu-id="f5421-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="f5421-120">没有理由使用字符串串联将变量与路径的其余部分组合在一起。</span><span class="sxs-lookup"><span data-stu-id="f5421-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="f5421-121">现在，当我检查 Function PSDrive 时，存在 `Get-MrPSVersion` 函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="f5421-122">脚本模块</span><span class="sxs-lookup"><span data-stu-id="f5421-122">Script Modules</span></span>

<span data-ttu-id="f5421-123">PowerShell 中的脚本模块只是一个文件，其中包含一个或多个保存为 `.PSM1` 文件而不是 `.PS1` 文件的函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="f5421-124">如何创建脚本模块？</span><span class="sxs-lookup"><span data-stu-id="f5421-124">How do you create a script module?</span></span> <span data-ttu-id="f5421-125">你可能会猜测使用名称类似于 `New-Module` 的命令。</span><span class="sxs-lookup"><span data-stu-id="f5421-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="f5421-126">你的假设是错误的。</span><span class="sxs-lookup"><span data-stu-id="f5421-126">Your assumption would be wrong.</span></span> <span data-ttu-id="f5421-127">虽然 PowerShell 中有一个名为 `New-Module` 的命令，但该命令创建的是一个动态模块，而不是脚本模块。</span><span class="sxs-lookup"><span data-stu-id="f5421-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="f5421-128">即使你认为找到了所需命令，也应始终确保阅读命令帮助。</span><span class="sxs-lookup"><span data-stu-id="f5421-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

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

<span data-ttu-id="f5421-129">在上一章中，我提到函数应使用已批准的谓词，否则在导入模块时，它们将生成一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="f5421-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="f5421-130">下面的代码使用 `New-Module` cmdlet 在内存中创建动态模块。</span><span class="sxs-lookup"><span data-stu-id="f5421-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="f5421-131">此模块演示未批准的谓词警告。</span><span class="sxs-lookup"><span data-stu-id="f5421-131">This module demonstrates the unapproved verb warning.</span></span>

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

<span data-ttu-id="f5421-132">重申一下，虽然在上一示例中使用了 `New-Module` cmdlet，但这不是用于在 PowerShell 中创建脚本模块的命令。</span><span class="sxs-lookup"><span data-stu-id="f5421-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="f5421-133">将以下两个函数保存在名为 `MyScriptModule.psm1` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="f5421-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="f5421-134">尝试调用某个函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-134">Try to call one of the functions.</span></span>

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

<span data-ttu-id="f5421-135">一条错误消息随即生成，表明找不到该函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="f5421-136">你还可以像以前一样检查 Function PSDrive，但会发现它也不存在。</span><span class="sxs-lookup"><span data-stu-id="f5421-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="f5421-137">可以用 `Import-Module` cmdlet 手动导入文件。</span><span class="sxs-lookup"><span data-stu-id="f5421-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="f5421-138">模块自动加载功能是在 PowerShell 版本 3 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f5421-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="f5421-139">要利用模块自动加载，需要将脚本模块保存在与 `.PSM1` 文件具有相同基名称的文件夹中，并保存在 `$env:PSModulePath` 中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="f5421-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="f5421-140">结果很难读取。</span><span class="sxs-lookup"><span data-stu-id="f5421-140">The results are difficult to read.</span></span> <span data-ttu-id="f5421-141">由于路径是用分号分隔的，因此可以拆分结果，在单独的行上返回每个路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="f5421-142">这样就更容易进行读取。</span><span class="sxs-lookup"><span data-stu-id="f5421-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="f5421-143">列表中的前三个路径是默认路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="f5421-144">安装 SQL Server Management Studio 后，会添加最后一个路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="f5421-145">要使模块自动加载功能正常工作，`MyScriptModule.psm1` 文件需要直接位于其中某个路径内名为 `MyScriptModule` 的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f5421-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="f5421-146">没那么快。</span><span class="sxs-lookup"><span data-stu-id="f5421-146">Not so fast.</span></span> <span data-ttu-id="f5421-147">对于我来说，当前用户路径不是列表中的第一个路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="f5421-148">我几乎从未使用过该路径，因为我用于登录 Windows 的用户名与用于运行 PowerShell 的用户名不同。</span><span class="sxs-lookup"><span data-stu-id="f5421-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="f5421-149">这意味着它不在我的标准“文档”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f5421-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="f5421-150">第二个路径是 AllUsers 路径。</span><span class="sxs-lookup"><span data-stu-id="f5421-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="f5421-151">这是我存储所有模块的位置。</span><span class="sxs-lookup"><span data-stu-id="f5421-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="f5421-152">第三个路径位于 `C:\Windows\System32` 之下。</span><span class="sxs-lookup"><span data-stu-id="f5421-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="f5421-153">只有 Microsoft 才应在该位置存储模块，因为它位于操作系统文件夹内。</span><span class="sxs-lookup"><span data-stu-id="f5421-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="f5421-154">`.PSM1` 文件位于正确的路径中后，调用某个模块命令时，将自动加载该模块。</span><span class="sxs-lookup"><span data-stu-id="f5421-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="f5421-155">模块清单</span><span class="sxs-lookup"><span data-stu-id="f5421-155">Module Manifests</span></span>

<span data-ttu-id="f5421-156">所有模块都应该有一个模块清单。</span><span class="sxs-lookup"><span data-stu-id="f5421-156">All modules should have a module manifest.</span></span> <span data-ttu-id="f5421-157">模块清单包含有关模块的元数据。</span><span class="sxs-lookup"><span data-stu-id="f5421-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="f5421-158">模块清单文件的文件扩展名是 `.PSD1`。</span><span class="sxs-lookup"><span data-stu-id="f5421-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="f5421-159">并非所有扩展名为 `.PSD1` 的文件都是模块清单。</span><span class="sxs-lookup"><span data-stu-id="f5421-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="f5421-160">它们还可用于存储 DSC 配置的环境部分等用途。</span><span class="sxs-lookup"><span data-stu-id="f5421-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="f5421-161">`New-ModuleManifest` 用于创建模块清单。</span><span class="sxs-lookup"><span data-stu-id="f5421-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="f5421-162">Path 是所需的唯一值。</span><span class="sxs-lookup"><span data-stu-id="f5421-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="f5421-163">但是，如果未指定 RootModule，则该模块将不起作用。</span><span class="sxs-lookup"><span data-stu-id="f5421-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="f5421-164">如果决定使用 PowerShellGet 将模块上传到 NuGet 存储库，最好指定 Author 和 Description，因为该情况需要这些值 。</span><span class="sxs-lookup"><span data-stu-id="f5421-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="f5421-165">不带清单的模块版本为 0.0。</span><span class="sxs-lookup"><span data-stu-id="f5421-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="f5421-166">模块没有清单是一个致命的漏洞。</span><span class="sxs-lookup"><span data-stu-id="f5421-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="f5421-167">可以使用所有建议的信息创建模块清单。</span><span class="sxs-lookup"><span data-stu-id="f5421-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="f5421-168">如果在模块清单初始创建期间丢失了任何此信息，则可稍后使用 `Update-ModuleManifest` 添加或更新该信息。</span><span class="sxs-lookup"><span data-stu-id="f5421-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="f5421-169">已创建清单后，请勿使用 `New-ModuleManifest` 重新创建清单，因为 GUID 将更改。</span><span class="sxs-lookup"><span data-stu-id="f5421-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="f5421-170">定义公共和专用函数</span><span class="sxs-lookup"><span data-stu-id="f5421-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="f5421-171">你可能想要将帮助程序函数用作私有函数，仅允许模块中的其他函数访问，</span><span class="sxs-lookup"><span data-stu-id="f5421-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="f5421-172">而不允许模块的用户访问。</span><span class="sxs-lookup"><span data-stu-id="f5421-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="f5421-173">可以通过几种不同方法实现此目的。</span><span class="sxs-lookup"><span data-stu-id="f5421-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="f5421-174">如果未遵循最佳做法并且只有一个 `.PSM1` 文件，则唯一的选择是使用 `Export-ModuleMember` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5421-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="f5421-175">在上面的示例中，只有 `Get-MrPSVersion` 函数可供模块的用户使用，但 `Get-MrComputerName` 函数可供模块本身包含的其他函数使用。</span><span class="sxs-lookup"><span data-stu-id="f5421-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="f5421-176">如果已将模块清单添加到模块（且应该这样做），建议在模块清单的 FunctionsToExport 部分中指定要导出的各个函数。</span><span class="sxs-lookup"><span data-stu-id="f5421-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="f5421-177">不需要在 `.PSM1` 文件和模块清单的 FunctionsToExport 部分同时使用两个 `Export-ModuleMember`。</span><span class="sxs-lookup"><span data-stu-id="f5421-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="f5421-178">使用其中一个已足够。</span><span class="sxs-lookup"><span data-stu-id="f5421-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="f5421-179">总结</span><span class="sxs-lookup"><span data-stu-id="f5421-179">Summary</span></span>

<span data-ttu-id="f5421-180">在本章中，你已了解如何在 PowerShell 中将函数转换为脚本模块。</span><span class="sxs-lookup"><span data-stu-id="f5421-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="f5421-181">还了解了一些用于创建脚本模块的最佳做法，例如，为脚本模块创建模块清单。</span><span class="sxs-lookup"><span data-stu-id="f5421-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="f5421-182">审阅</span><span class="sxs-lookup"><span data-stu-id="f5421-182">Review</span></span>

1. <span data-ttu-id="f5421-183">如何在 PowerShell 中创建脚本模块？</span><span class="sxs-lookup"><span data-stu-id="f5421-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="f5421-184">为什么函数必须使用已批准的谓词？</span><span class="sxs-lookup"><span data-stu-id="f5421-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="f5421-185">如何在 PowerShell 中创建模块清单？</span><span class="sxs-lookup"><span data-stu-id="f5421-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="f5421-186">哪两个选项仅用于导出模块中的特定函数？</span><span class="sxs-lookup"><span data-stu-id="f5421-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="f5421-187">调用命令时，自动加载模块需要执行哪些操作？</span><span class="sxs-lookup"><span data-stu-id="f5421-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="f5421-188">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="f5421-188">Recommended Reading</span></span>

- <span data-ttu-id="f5421-189">[如何创建 PowerShell 脚本模块和模块清单][]</span><span class="sxs-lookup"><span data-stu-id="f5421-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="f5421-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="f5421-190">[about_Modules][]</span></span>
- <span data-ttu-id="f5421-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="f5421-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="f5421-192">[Export-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="f5421-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[如何创建 PowerShell 脚本模块和模块清单]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
