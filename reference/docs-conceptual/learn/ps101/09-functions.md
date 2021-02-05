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
# <a name="chapter-9---functions"></a><span data-ttu-id="557bb-103">第 9 章 - 函数</span><span class="sxs-lookup"><span data-stu-id="557bb-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="557bb-104">如果你正在编写 PowerShell 单行程序或脚本，并发现你经常需要针对不同的场景对其进行修改，则可以考虑将其转换为可重用的函数。</span><span class="sxs-lookup"><span data-stu-id="557bb-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="557bb-105">只要有可能，我更喜欢编写函数，因为它们更具有工具导向性。</span><span class="sxs-lookup"><span data-stu-id="557bb-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="557bb-106">我可以将函数放在脚本模块中，将该模块放在 `$env:PSModulePath` 中，然后调用这些函数，而无需查找它们的实际保存位置。</span><span class="sxs-lookup"><span data-stu-id="557bb-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="557bb-107">使用 PowerShellGet 模块，可以轻松地在 NuGet 存储库中共享这些模块。</span><span class="sxs-lookup"><span data-stu-id="557bb-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="557bb-108">PowerShellGet 随 PowerShell 版本 5.0 及更高版本提供。</span><span class="sxs-lookup"><span data-stu-id="557bb-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="557bb-109">对于 PowerShell 版本 3.0 及更高版本，它可以作为单独的下载提供。</span><span class="sxs-lookup"><span data-stu-id="557bb-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="557bb-110">不要将事情复杂化。</span><span class="sxs-lookup"><span data-stu-id="557bb-110">Don't over complicate things.</span></span> <span data-ttu-id="557bb-111">保持简单，并使用最直接的方式完成任务。</span><span class="sxs-lookup"><span data-stu-id="557bb-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="557bb-112">避免在重用的任何代码中使用别名和位置参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="557bb-113">设置代码的格式以提高可读性。</span><span class="sxs-lookup"><span data-stu-id="557bb-113">Format your code for readability.</span></span> <span data-ttu-id="557bb-114">不要对值进行硬编码；使用参数和变量。</span><span class="sxs-lookup"><span data-stu-id="557bb-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="557bb-115">不要编写不必要的代码，即使它不会造成任何损害。</span><span class="sxs-lookup"><span data-stu-id="557bb-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="557bb-116">它增加了不必要的复杂性。</span><span class="sxs-lookup"><span data-stu-id="557bb-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="557bb-117">编写任何 PowerShell 代码时，请注意细节。</span><span class="sxs-lookup"><span data-stu-id="557bb-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="557bb-118">命名</span><span class="sxs-lookup"><span data-stu-id="557bb-118">Naming</span></span>

<span data-ttu-id="557bb-119">在 PowerShell 中命名函数时，结合使用[帕斯卡拼写法][]名称和已批准的谓词和单数名词。</span><span class="sxs-lookup"><span data-stu-id="557bb-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="557bb-120">我还建议在名词前面加上前缀。</span><span class="sxs-lookup"><span data-stu-id="557bb-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="557bb-121">例如：`<ApprovedVerb>-<Prefix><SingularNoun>`。</span><span class="sxs-lookup"><span data-stu-id="557bb-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="557bb-122">PowerShell 中有一个批准的谓词的特定列表，可通过运行 `Get-Verb` 获取这些谓词。</span><span class="sxs-lookup"><span data-stu-id="557bb-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

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

<span data-ttu-id="557bb-123">在前面的示例中，我已按照“谓词”列对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="557bb-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="557bb-124">通过“组”列，你可以了解这些谓词的用法。</span><span class="sxs-lookup"><span data-stu-id="557bb-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="557bb-125">将函数添加到模块时，请务必在 PowerShell 中选择一个批准的谓词。</span><span class="sxs-lookup"><span data-stu-id="557bb-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="557bb-126">如果选择未批准的谓词，模块将在加载时生成警告消息。</span><span class="sxs-lookup"><span data-stu-id="557bb-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="557bb-127">该警告消息使函数看起来不专业。</span><span class="sxs-lookup"><span data-stu-id="557bb-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="557bb-128">未批准的谓词还会限制函数的可发现性。</span><span class="sxs-lookup"><span data-stu-id="557bb-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="557bb-129">简单函数</span><span class="sxs-lookup"><span data-stu-id="557bb-129">A simple function</span></span>

<span data-ttu-id="557bb-130">PowerShell 中的函数使用函数关键字声明，后面依次跟函数名称、左大括号和右大括号。</span><span class="sxs-lookup"><span data-stu-id="557bb-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="557bb-131">函数将执行的代码包含在这些大括号中。</span><span class="sxs-lookup"><span data-stu-id="557bb-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="557bb-132">显示的函数是返回 PowerShell 版本的简单示例。</span><span class="sxs-lookup"><span data-stu-id="557bb-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="557bb-133">名称很可能与名称类似于 `Get-Version` 的函数以及 PowerShell 中的默认命令或其他人可能编写的命令发生冲突。</span><span class="sxs-lookup"><span data-stu-id="557bb-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="557bb-134">因此，我建议为函数的名词部分加上前缀以防止命名冲突。</span><span class="sxs-lookup"><span data-stu-id="557bb-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="557bb-135">在下面的示例中，我将使用前缀“PS”。</span><span class="sxs-lookup"><span data-stu-id="557bb-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="557bb-136">除了名称外，此函数与上一个函数相同。</span><span class="sxs-lookup"><span data-stu-id="557bb-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="557bb-137">即使在名词前面加上前缀（如 PS），仍可能出现名称冲突。</span><span class="sxs-lookup"><span data-stu-id="557bb-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="557bb-138">我通常使用我的姓名缩写作为函数名词的前缀。</span><span class="sxs-lookup"><span data-stu-id="557bb-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="557bb-139">制定标准并坚持遵循。</span><span class="sxs-lookup"><span data-stu-id="557bb-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="557bb-140">此函数与前两个函数没有什么不同，唯一区别是它使用更合理的名称，以防止与其他 PowerShell 命令发生命名冲突。</span><span class="sxs-lookup"><span data-stu-id="557bb-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="557bb-141">加载到内存后，可在函数 PSDrive 上查看函数。</span><span class="sxs-lookup"><span data-stu-id="557bb-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

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

<span data-ttu-id="557bb-142">如果要从当前会话中删除这些函数，则必须从函数 PSDrive 中将其删除，或关闭之后再重新打开 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="557bb-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="557bb-143">验证是否确实删除了函数。</span><span class="sxs-lookup"><span data-stu-id="557bb-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="557bb-144">如果函数是作为模块的一部分加载的，则可以卸载模块以删除它们。</span><span class="sxs-lookup"><span data-stu-id="557bb-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="557bb-145">`Remove-Module` cmdlet 从当前 PowerShell 会话中的内存中删除模块，不会从系统或磁盘中删除模块。</span><span class="sxs-lookup"><span data-stu-id="557bb-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="557bb-146">参数</span><span class="sxs-lookup"><span data-stu-id="557bb-146">Parameters</span></span>

<span data-ttu-id="557bb-147">请勿静态分配值！</span><span class="sxs-lookup"><span data-stu-id="557bb-147">Don't statically assign values!</span></span> <span data-ttu-id="557bb-148">使用参数和变量。</span><span class="sxs-lookup"><span data-stu-id="557bb-148">Use parameters and variables.</span></span> <span data-ttu-id="557bb-149">命名参数时，请尽可能使用与默认 cmdlet 相同的名称作为参数名称。</span><span class="sxs-lookup"><span data-stu-id="557bb-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="557bb-150">我为什么使用 ComputerName 而不是 Computer、ServerName 或 Host 作为参数名称   ？</span><span class="sxs-lookup"><span data-stu-id="557bb-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="557bb-151">这是因为我希望函数像默认 cmdlet 一样标准化。</span><span class="sxs-lookup"><span data-stu-id="557bb-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="557bb-152">我将创建一个函数，用于查询系统上的所有命令并返回具有特定参数名称的命令数量。</span><span class="sxs-lookup"><span data-stu-id="557bb-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

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

<span data-ttu-id="557bb-153">正如下面的结果所示，有 39 个命令具有 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="557bb-154">没有任何 cmdlet 具有 Computer、ServerName、Host 或 Machine 这样的参数   。</span><span class="sxs-lookup"><span data-stu-id="557bb-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

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

<span data-ttu-id="557bb-155">我还建议对参数名称使用与默认 cmdlet 相同的大小写。</span><span class="sxs-lookup"><span data-stu-id="557bb-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="557bb-156">使用 `ComputerName`，而不是 `computername`。</span><span class="sxs-lookup"><span data-stu-id="557bb-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="557bb-157">这会使你的函数看起来像默认 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="557bb-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="557bb-158">已经熟悉 PowerShell 的用户会感到得心应手。</span><span class="sxs-lookup"><span data-stu-id="557bb-158">People who are already familiar with PowerShell will feel right at home.</span></span>

<span data-ttu-id="557bb-159">`param`语句允许您定义一个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-159">The `param` statement allows you to define one or more parameters.</span></span> <span data-ttu-id="557bb-160">参数定义由逗号分隔 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="557bb-160">The parameter definitions are separated by a comma (`,`).</span></span> <span data-ttu-id="557bb-161">有关详细信息，请参阅 [about_Functions_Advanced_Parameters][]。</span><span class="sxs-lookup"><span data-stu-id="557bb-161">For more information, see [about_Functions_Advanced_Parameters][].</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="557bb-162">高级函数</span><span class="sxs-lookup"><span data-stu-id="557bb-162">Advanced Functions</span></span>

<span data-ttu-id="557bb-163">将 PowerShell 中的函数转换为高级函数非常简单。</span><span class="sxs-lookup"><span data-stu-id="557bb-163">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="557bb-164">函数与高级函数之间的一个区别是，高级函数具有多个自动添加到函数的通用参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-164">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="557bb-165">这些通用参数包括 Verbose 和 Debug 。</span><span class="sxs-lookup"><span data-stu-id="557bb-165">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="557bb-166">我将从上一部分中使用的 `Test-MrParameter` 函数开始介绍。</span><span class="sxs-lookup"><span data-stu-id="557bb-166">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="557bb-167">请注意，`Test-MrParameter` 函数没有任何通用参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-167">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="557bb-168">可以通过多种不同的方法来查看通用参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-168">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="557bb-169">其中一种方法是使用 `Get-Command` 查看语法。</span><span class="sxs-lookup"><span data-stu-id="557bb-169">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="557bb-170">另一种方法是通过 `Get-Command` 向下钻取参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-170">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="557bb-171">添加 `CmdletBinding` 以将函数转换为高级函数。</span><span class="sxs-lookup"><span data-stu-id="557bb-171">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="557bb-172">添加 `CmdletBinding` 会自动添加通用参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-172">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="557bb-173">`CmdletBinding` 需要一个 `param` 块，但 `param` 块可以为空。</span><span class="sxs-lookup"><span data-stu-id="557bb-173">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="557bb-174">通过 `Get-Command` 向下钻取参数会显示实际参数名称，包括常见参数名称。</span><span class="sxs-lookup"><span data-stu-id="557bb-174">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

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

## <a name="supportsshouldprocess"></a><span data-ttu-id="557bb-175">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="557bb-175">SupportsShouldProcess</span></span>

<span data-ttu-id="557bb-176">`SupportsShouldProcess` 会添加 WhatIf 和 Confirm 参数 。</span><span class="sxs-lookup"><span data-stu-id="557bb-176">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="557bb-177">只有做出更改的命令需要这些参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-177">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="557bb-178">请注意，现在有 WhatIf 和 Confirm 参数 。</span><span class="sxs-lookup"><span data-stu-id="557bb-178">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="557bb-179">同样，还可以使用 `Get-Command` 返回实际参数名称列表，其中包括常见参数名称以及 WhatIf 和 Confirm。</span><span class="sxs-lookup"><span data-stu-id="557bb-179">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

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

## <a name="parameter-validation"></a><span data-ttu-id="557bb-180">参数验证</span><span class="sxs-lookup"><span data-stu-id="557bb-180">Parameter Validation</span></span>

<span data-ttu-id="557bb-181">尽早验证输入。</span><span class="sxs-lookup"><span data-stu-id="557bb-181">Validate input early on.</span></span> <span data-ttu-id="557bb-182">如果不可能在没有有效输入的情况下运行代码，那为什么允许代码在某路径上继续运行？</span><span class="sxs-lookup"><span data-stu-id="557bb-182">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="557bb-183">始终键入要用于参数的变量（指定数据类型）。</span><span class="sxs-lookup"><span data-stu-id="557bb-183">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="557bb-184">在前面的示例中，我指定了 String 作为 ComputerName 参数的数据类型 。</span><span class="sxs-lookup"><span data-stu-id="557bb-184">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="557bb-185">这将导致它只允许指定一个计算机名。</span><span class="sxs-lookup"><span data-stu-id="557bb-185">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="557bb-186">如果通过以逗号分隔的列表指定了多个计算机名，则会生成错误。</span><span class="sxs-lookup"><span data-stu-id="557bb-186">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

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

<span data-ttu-id="557bb-187">当前定义的问题在于省略 ComputerName 参数的值是有效的，但需要一个值才能成功完成该函数。</span><span class="sxs-lookup"><span data-stu-id="557bb-187">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="557bb-188">这时 `Mandatory` 参数属性就发挥作用了。</span><span class="sxs-lookup"><span data-stu-id="557bb-188">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

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

<span data-ttu-id="557bb-189">前面的示例中使用的语法为 PowerShell 版本 3.0 及更高兼容版本。</span><span class="sxs-lookup"><span data-stu-id="557bb-189">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="557bb-190">可以改为指定 `[Parameter(Mandatory=$true)]`，以使函数与 PowerShell 版本 2.0 及更高版本兼容。</span><span class="sxs-lookup"><span data-stu-id="557bb-190">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="557bb-191">现在 ComputerName 是必需的，如果未指定，该函数将提示输入名称。</span><span class="sxs-lookup"><span data-stu-id="557bb-191">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="557bb-192">如果要允许 ComputerName 参数具有多个值，请使用 String 数据类型，但应向该数据类型添加左方括号和右方括号以允许字符串数组 。</span><span class="sxs-lookup"><span data-stu-id="557bb-192">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

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

<span data-ttu-id="557bb-193">也许你想为 ComputerName 参数指定一个默认值（如果未指定）。</span><span class="sxs-lookup"><span data-stu-id="557bb-193">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="557bb-194">问题在于，默认值不能与必需参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="557bb-194">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="557bb-195">你需要将 `ValidateNotNullOrEmpty` 参数验证属性与默认值一起使用。</span><span class="sxs-lookup"><span data-stu-id="557bb-195">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

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

<span data-ttu-id="557bb-196">即使在设置默认值时，也不要使用静态值。</span><span class="sxs-lookup"><span data-stu-id="557bb-196">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="557bb-197">在上面的示例中，`$env:COMPUTERNAME` 用作默认值，如果未提供值，该默认值将自动转换为本地计算机名。</span><span class="sxs-lookup"><span data-stu-id="557bb-197">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="557bb-198">详细输出</span><span class="sxs-lookup"><span data-stu-id="557bb-198">Verbose Output</span></span>

<span data-ttu-id="557bb-199">尽管内联注释非常有用（尤其是在编写一些复杂的代码时），但用户不会看到这些注释，除非他们查看代码本身。</span><span class="sxs-lookup"><span data-stu-id="557bb-199">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="557bb-200">下面的示例中显示的函数在 `foreach` 循环中具有内联注释。</span><span class="sxs-lookup"><span data-stu-id="557bb-200">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="557bb-201">虽然这种特定注释可能并不难找到，但如果函数包含数百个代码行，就很麻烦。</span><span class="sxs-lookup"><span data-stu-id="557bb-201">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

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

<span data-ttu-id="557bb-202">一种更好的选择是使用 `Write-Verbose` 而不是内联注释。</span><span class="sxs-lookup"><span data-stu-id="557bb-202">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

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

<span data-ttu-id="557bb-203">如果在没有 Verbose 参数的情况下调用函数，则不会显示详细输出。</span><span class="sxs-lookup"><span data-stu-id="557bb-203">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="557bb-204">通过 Verbose 参数调用函数时，会显示详细输出。</span><span class="sxs-lookup"><span data-stu-id="557bb-204">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="557bb-205">管道输入</span><span class="sxs-lookup"><span data-stu-id="557bb-205">Pipeline Input</span></span>

<span data-ttu-id="557bb-206">如果希望函数接受管道输入，则需要进行一些额外的编码。</span><span class="sxs-lookup"><span data-stu-id="557bb-206">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="557bb-207">如本书前面所述，命令可以接受按值（按类型）或按属性名称显示的管道输入 。</span><span class="sxs-lookup"><span data-stu-id="557bb-207">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="557bb-208">可以像编写本机命令那样编写函数，以便它们接受其中一种或两种类型的输入。</span><span class="sxs-lookup"><span data-stu-id="557bb-208">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="557bb-209">若要接受按值显示管道输入，请为该特定参数指定 `ValueFromPipeline` 参数属性。</span><span class="sxs-lookup"><span data-stu-id="557bb-209">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="557bb-210">请记住，只能接受每种数据类型中按值显示的管道输入。</span><span class="sxs-lookup"><span data-stu-id="557bb-210">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="557bb-211">例如，如果有两个接受字符串输入的参数，则只有其中一个参数可以接受按值显示的管道输入，因为如果为两个字符串参数都指定了管道输入，则该管道输入不知道该绑定到哪个参数。</span><span class="sxs-lookup"><span data-stu-id="557bb-211">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="557bb-212">这就是我调用此类型的按类型显示的管道输入（而不是按值显示的管道输入）的另一个原因。</span><span class="sxs-lookup"><span data-stu-id="557bb-212">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="557bb-213">管道输入一次输入一个项，这类似于在 `foreach` 循环中处理项的方式。</span><span class="sxs-lookup"><span data-stu-id="557bb-213">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="557bb-214">如果要接受数组作为输入，则至少需要一个 `process` 块才能处理所有项。</span><span class="sxs-lookup"><span data-stu-id="557bb-214">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="557bb-215">如果只接受单个值作为输入，则不需要 `process` 块，但仍建议指定它以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="557bb-215">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

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

<span data-ttu-id="557bb-216">接受按属性名称显示的管道输入是类似的，但它是使用 `ValueFromPipelineByPropertyName` 参数属性指定的，并且可为任意数量的参数指定该输入，无需考虑数据类型。</span><span class="sxs-lookup"><span data-stu-id="557bb-216">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="557bb-217">关键在于，通过管道传送的命令输出必须具有与参数名称或函数的参数别名匹配的属性名称。</span><span class="sxs-lookup"><span data-stu-id="557bb-217">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

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

<span data-ttu-id="557bb-218">`BEGIN` 和 `END` 块是可选的。</span><span class="sxs-lookup"><span data-stu-id="557bb-218">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="557bb-219">`BEGIN` 在 `PROCESS` 块之前指定，用于在从管道接收项之前执行任何初始工作。</span><span class="sxs-lookup"><span data-stu-id="557bb-219">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="557bb-220">了解这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="557bb-220">This is important to understand.</span></span> <span data-ttu-id="557bb-221">在 `BEGIN` 块中无法访问通过管道传入的值。</span><span class="sxs-lookup"><span data-stu-id="557bb-221">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="557bb-222">`END` 块将在 `PROCESS` 块之后指定，用于在处理完通过管道传入的所有值之后进行清理。</span><span class="sxs-lookup"><span data-stu-id="557bb-222">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="557bb-223">错误处理</span><span class="sxs-lookup"><span data-stu-id="557bb-223">Error Handling</span></span>

<span data-ttu-id="557bb-224">当无法联系计算机时，以下示例中显示的函数会生成未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="557bb-224">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

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

<span data-ttu-id="557bb-225">可采用多种不同的方法在 PowerShell 中处理错误。</span><span class="sxs-lookup"><span data-stu-id="557bb-225">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="557bb-226">`Try/Catch` 是处理错误的较新式的方法。</span><span class="sxs-lookup"><span data-stu-id="557bb-226">`Try/Catch` is the more modern way to handle errors.</span></span>

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

<span data-ttu-id="557bb-227">尽管上面的示例中显示的函数使用错误处理，但它也会生成未经处理的异常，因为该命令不会生成终止错误。</span><span class="sxs-lookup"><span data-stu-id="557bb-227">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="557bb-228">了解这一点也很重要。</span><span class="sxs-lookup"><span data-stu-id="557bb-228">This is also important to understand.</span></span> <span data-ttu-id="557bb-229">仅捕获终止错误。</span><span class="sxs-lookup"><span data-stu-id="557bb-229">Only terminating errors are caught.</span></span> <span data-ttu-id="557bb-230">将 ErrorAction 参数的值指定为 Stop，将非终止错误转换为终止错误 。</span><span class="sxs-lookup"><span data-stu-id="557bb-230">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

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

<span data-ttu-id="557bb-231">除非确实有必要，否则请勿修改全局 `$ErrorActionPreference` 变量。</span><span class="sxs-lookup"><span data-stu-id="557bb-231">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="557bb-232">如果直接从 PowerShell 函数内使用 .NET 之类的内容，则不能针对命令本身指定 ErrorAction。</span><span class="sxs-lookup"><span data-stu-id="557bb-232">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="557bb-233">在这种情况下，你可能需要更改全局 `$ErrorActionPreference` 变量，但如果确实要更改它，请在尝试执行命令后立即将其更改回来。</span><span class="sxs-lookup"><span data-stu-id="557bb-233">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="557bb-234">基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="557bb-234">Comment-Based Help</span></span>

<span data-ttu-id="557bb-235">最佳做法是将基于注释的帮助添加到函数，以便你与之共享函数的人知道如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="557bb-235">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

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

<span data-ttu-id="557bb-236">如果将基于注释的帮助添加到函数，可以像默认的内置命令一样为他们检索帮助。</span><span class="sxs-lookup"><span data-stu-id="557bb-236">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="557bb-237">用于在 PowerShell 中编写函数的所有语法似乎过于复杂，尤其是对于刚入门的用户。</span><span class="sxs-lookup"><span data-stu-id="557bb-237">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="557bb-238">通常，如果我不记得语法的某些内容，我会在单独的监视器上打开 ISE 的第二个副本，并在键入函数代码时查看“Cmdlet (高级函数) - 完成”代码片段。</span><span class="sxs-lookup"><span data-stu-id="557bb-238">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="557bb-239">可以使用 <kbd>Ctrl</kbd>+<kbd>J</kbd> 组合键在 PowerShell ISE 中访问代码片段。</span><span class="sxs-lookup"><span data-stu-id="557bb-239">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="557bb-240">总结</span><span class="sxs-lookup"><span data-stu-id="557bb-240">Summary</span></span>

<span data-ttu-id="557bb-241">在本章中，你已了解有关在 PowerShell 中编写函数的基本知识，其中包括如何将函数转变为高级函数，以及在编写 PowerShell 函数（如参数验证、详细输出、管道输入、错误处理和基于注释的帮助）时应考虑的一些较重要的要素。</span><span class="sxs-lookup"><span data-stu-id="557bb-241">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="557bb-242">审阅</span><span class="sxs-lookup"><span data-stu-id="557bb-242">Review</span></span>

1. <span data-ttu-id="557bb-243">如何在 PowerShell 中获取批准的谓词的列表？</span><span class="sxs-lookup"><span data-stu-id="557bb-243">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="557bb-244">如何将 PowerShell 函数转换为高级函数？</span><span class="sxs-lookup"><span data-stu-id="557bb-244">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="557bb-245">应在何时将 WhatIf 和 Confirm 参数添加到 PowerShell 函数 ？</span><span class="sxs-lookup"><span data-stu-id="557bb-245">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="557bb-246">如何将非终止错误转换为终止错误？</span><span class="sxs-lookup"><span data-stu-id="557bb-246">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="557bb-247">为什么应该将基于注释的帮助添加到函数？</span><span class="sxs-lookup"><span data-stu-id="557bb-247">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="557bb-248">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="557bb-248">Recommended Reading</span></span>

- <span data-ttu-id="557bb-249">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="557bb-249">[about_Functions][]</span></span>
- <span data-ttu-id="557bb-250">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="557bb-250">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="557bb-251">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="557bb-251">[about_CommonParameters][]</span></span>
- <span data-ttu-id="557bb-252">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="557bb-252">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="557bb-253">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="557bb-253">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="557bb-254">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="557bb-254">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="557bb-255">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="557bb-255">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="557bb-256">[视频：使用高级函数和脚本模块的 PowerShell 工具制作][]</span><span class="sxs-lookup"><span data-stu-id="557bb-256">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[视频：使用高级函数和脚本模块的 PowerShell 工具制作]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[帕斯卡拼写法]: /dotnet/standard/design-guidelines/capitalization-conventions
[Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventions
