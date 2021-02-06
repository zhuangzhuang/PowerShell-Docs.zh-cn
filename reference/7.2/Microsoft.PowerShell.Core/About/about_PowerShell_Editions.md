---
description: 不同版本的 PowerShell 在不同的基础运行时上运行。
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 3b1b938874b36919a1a0627f3b492cbc961e4a2f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603822"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="4f91d-103">关于 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="4f91d-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="4f91d-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="4f91d-104">Short Description</span></span>
<span data-ttu-id="4f91d-105">不同版本的 PowerShell 在不同的基础运行时上运行。</span><span class="sxs-lookup"><span data-stu-id="4f91d-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="4f91d-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="4f91d-106">Long Description</span></span>

<span data-ttu-id="4f91d-107">在 PowerShell 5.1 中，每个 *版本* 的 powershell 都在不同的 .net 运行时上运行。</span><span class="sxs-lookup"><span data-stu-id="4f91d-107">From PowerShell 5.1, there are multiple *editions* of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="4f91d-108">在 PowerShell 6.2 中，有两个版本的 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="4f91d-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="4f91d-109">在 .NET Framework 上运行的 **桌面**。</span><span class="sxs-lookup"><span data-stu-id="4f91d-109">**Desktop**, which runs on .NET Framework.</span></span> <span data-ttu-id="4f91d-110">Windows 桌面、Windows Server、Windows Server Core 和大多数其他 Windows 操作系统等功能齐全的 Windows 版本（例如5.1，Windows 桌面、Windows Server、Windows Server Core 和大多数其他 Windows 操作系统）都是桌面版。</span><span class="sxs-lookup"><span data-stu-id="4f91d-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span>
  <span data-ttu-id="4f91d-111">这是原始 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="4f91d-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="4f91d-112">**核心**，它在 .net Core 上运行。</span><span class="sxs-lookup"><span data-stu-id="4f91d-112">**Core**, which runs on .NET Core.</span></span> <span data-ttu-id="4f91d-113">PowerShell 6.0 及更高版本，以及 PowerShell 5.1 上一些降低的 Windows 版本（如 Windows Nano Server 和 Windows IoT，其中 .NET Framework 不可用）。</span><span class="sxs-lookup"><span data-stu-id="4f91d-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="4f91d-114">因为 PowerShell 版本对应于其 .NET 运行时，所以它是 .NET API 和 PowerShell 模块兼容性的主要指标;一些 .NET Api、类型或方法在 .NET 运行时中均不可用，这会影响依赖于它们的 PowerShell 脚本和模块。</span><span class="sxs-lookup"><span data-stu-id="4f91d-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="4f91d-115">`$PSEdition`自动变量</span><span class="sxs-lookup"><span data-stu-id="4f91d-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="4f91d-116">在 PowerShell 5.1 及更高版本中，可以通过自动变量了解正在运行的版本 `$PSEdition` ：</span><span class="sxs-lookup"><span data-stu-id="4f91d-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="4f91d-117">在 PowerShell 4 和更低的中，此变量不存在。</span><span class="sxs-lookup"><span data-stu-id="4f91d-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="4f91d-118">`$PSEdition` 应将 null 视为与具有值的相同 `Desktop` 。</span><span class="sxs-lookup"><span data-stu-id="4f91d-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="4f91d-119">版本 `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="4f91d-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="4f91d-120">`$PSVersionTable`自动变量在 PowerShell 5.1 和更高版本中还包含版本信息：</span><span class="sxs-lookup"><span data-stu-id="4f91d-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

<span data-ttu-id="4f91d-121">该 `PSEdition` 字段将具有与自动变量相同的值 `$PSEdition` 。</span><span class="sxs-lookup"><span data-stu-id="4f91d-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="4f91d-122">`CompatiblePSEditions`模块清单字段</span><span class="sxs-lookup"><span data-stu-id="4f91d-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="4f91d-123">PowerShell 模块可以声明与使用模块清单的字段兼容的 PowerShell 版本 `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="4f91d-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="4f91d-124">例如，声明与 `Desktop` PowerShell 和版本的兼容性的模块清单 `Core` ：</span><span class="sxs-lookup"><span data-stu-id="4f91d-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="4f91d-125">仅具有兼容性的模块清单示例 `Desktop` ：</span><span class="sxs-lookup"><span data-stu-id="4f91d-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="4f91d-126">省略 `CompatiblePSEditions` 模块清单中的字段将具有与将其设置为相同的效果 `Desktop` ，因为引入此字段之前创建的模块是为此版本隐式编写的。</span><span class="sxs-lookup"><span data-stu-id="4f91d-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="4f91d-127">对于在 Windows (（即从库中编写或安装的模块）中未随附的模块) ，此字段只是信息性的;PowerShell 不会根据字段更改行为 `CompatiblePSEditions` ，但会在 `PSModuleInfo` `Get-Module`) 为自己的逻辑返回的对象 (公开它：</span><span class="sxs-lookup"><span data-stu-id="4f91d-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> <span data-ttu-id="4f91d-128">`CompatiblePSEditions`模块字段仅与 PowerShell 5.1 和更高版本兼容。</span><span class="sxs-lookup"><span data-stu-id="4f91d-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span>
> <span data-ttu-id="4f91d-129">包含此字段将导致模块与 PowerShell 4 和更低的模块不兼容。</span><span class="sxs-lookup"><span data-stu-id="4f91d-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span>
> <span data-ttu-id="4f91d-130">因为字段只是信息性的，所以可以在以后的 PowerShell 版本中安全地省略。</span><span class="sxs-lookup"><span data-stu-id="4f91d-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="4f91d-131">在 PowerShell 6.1 中， `Get-Module -ListAvailable` 已更新其格式化程序以显示每个模块的版本兼容性：</span><span class="sxs-lookup"><span data-stu-id="4f91d-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="4f91d-132">版本-Windows 附带的模块的兼容性</span><span class="sxs-lookup"><span data-stu-id="4f91d-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="4f91d-133">对于作为 Windows (的一部分，或者作为角色或功能的一部分安装的模块) ，PowerShell 6.1 和更高版本会以不同的方式来处理该 `CompatiblePSEditions` 字段。</span><span class="sxs-lookup"><span data-stu-id="4f91d-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="4f91d-134">此类模块位于 Windows PowerShell 系统模块目录中 (`%windir%\System\WindowsPowerShell\v1.0\Modules`) 中。</span><span class="sxs-lookup"><span data-stu-id="4f91d-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="4f91d-135">对于从或在此目录中找到的模块，PowerShell 6.1 和更高版本使用 `CompatiblePSEditions` 字段来确定模块是否将与当前会话兼容并相应地进行处理。</span><span class="sxs-lookup"><span data-stu-id="4f91d-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="4f91d-136">`Import-Module`使用时，不会导入不包含在中的模块， `Core` `CompatiblePSEditions` 并将显示错误：</span><span class="sxs-lookup"><span data-stu-id="4f91d-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

<span data-ttu-id="4f91d-137">`Get-Module -ListAvailable`使用时， `Core` 不会显示不在中的模块 `CompatiblePSEditions` ：</span><span class="sxs-lookup"><span data-stu-id="4f91d-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="4f91d-138">在这两种情况下， `-SkipEditionCheck` 开关参数均可用于重写此行为：</span><span class="sxs-lookup"><span data-stu-id="4f91d-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> <span data-ttu-id="4f91d-139">`Import-Module -SkipEditionCheck` 模块可能看起来是成功的，但使用该模块会在以后遇到不兼容的风险。尽管加载模块最初会成功，但后面的命令可能会调用不兼容的 API，并自发地失败。</span><span class="sxs-lookup"><span data-stu-id="4f91d-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="4f91d-140">创作用于版本互兼容性的 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="4f91d-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="4f91d-141">编写 PowerShell 模块以面向 `Desktop` 和 `Core` 版本的 powershell 时，可以执行一些操作来确保跨版本兼容性。</span><span class="sxs-lookup"><span data-stu-id="4f91d-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="4f91d-142">确认和持续验证兼容性的唯一真正的方法是为脚本或模块编写测试，并在需要与兼容的所有 PowerShell 版本和版本上运行这些测试。</span><span class="sxs-lookup"><span data-stu-id="4f91d-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="4f91d-143">为此，建议的测试框架是 [Pester][]。</span><span class="sxs-lookup"><span data-stu-id="4f91d-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4f91d-144">PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="4f91d-144">PowerShell script</span></span>

<span data-ttu-id="4f91d-145">作为一种语言，PowerShell 在不同版本之间的工作方式相同;它是你使用的、受版本兼容性影响的 cmdlet、模块和 .NET Api。</span><span class="sxs-lookup"><span data-stu-id="4f91d-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="4f91d-146">通常，在 PowerShell 6.1 及更高版本中使用的脚本将适用于 Windows PowerShell 5.1，但有一些例外情况。</span><span class="sxs-lookup"><span data-stu-id="4f91d-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="4f91d-147">版本 1.18.0 [PSScriptAnalyzer][] 模块具有 [`PSUseCompatibleCommands`][] 和等规则，这些规则 [`PSUseCompatibleTypes`][] 能够检测到 PowerShell 脚本中可能不兼容的命令和 .net api 的用法。</span><span class="sxs-lookup"><span data-stu-id="4f91d-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [`PSUseCompatibleCommands`][] and [`PSUseCompatibleTypes`][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="4f91d-148">.NET 程序集</span><span class="sxs-lookup"><span data-stu-id="4f91d-148">.NET assemblies</span></span>

<span data-ttu-id="4f91d-149">如果要编写包含 .NET 程序集的二进制模块或模块 (Dll) 从源代码生成的，则应根据 .NET 和 PowerShell API 兼容性的编译时兼容性验证 [.NET Standard][] 和 [powershell 标准][] 进行编译。</span><span class="sxs-lookup"><span data-stu-id="4f91d-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="4f91d-150">尽管这些库能够在编译时检查某些兼容性，但它们无法捕获各个版本之间的可能行为差异。</span><span class="sxs-lookup"><span data-stu-id="4f91d-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span> <span data-ttu-id="4f91d-151">为此，你仍必须编写测试。</span><span class="sxs-lookup"><span data-stu-id="4f91d-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f91d-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="4f91d-152">See also</span></span>

- [<span data-ttu-id="4f91d-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4f91d-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="4f91d-154">Import-Module</span><span class="sxs-lookup"><span data-stu-id="4f91d-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="4f91d-155">Get-Module</span><span class="sxs-lookup"><span data-stu-id="4f91d-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="4f91d-156">具有兼容的 PowerShell 版本的模块</span><span class="sxs-lookup"><span data-stu-id="4f91d-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[`PSUseCompatibleCommands`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[`PSUseCompatibleTypes`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
