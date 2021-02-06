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
# <a name="about-powershell-editions"></a>关于 PowerShell 版本

## <a name="short-description"></a>简短说明
不同版本的 PowerShell 在不同的基础运行时上运行。

## <a name="long-description"></a>详细说明

在 PowerShell 5.1 中，每个 *版本* 的 powershell 都在不同的 .net 运行时上运行。 在 PowerShell 6.2 中，有两个版本的 PowerShell：

- 在 .NET Framework 上运行的 **桌面**。 Windows 桌面、Windows Server、Windows Server Core 和大多数其他 Windows 操作系统等功能齐全的 Windows 版本（例如5.1，Windows 桌面、Windows Server、Windows Server Core 和大多数其他 Windows 操作系统）都是桌面版。
  这是原始 PowerShell 版本。
- **核心**，它在 .net Core 上运行。 PowerShell 6.0 及更高版本，以及 PowerShell 5.1 上一些降低的 Windows 版本（如 Windows Nano Server 和 Windows IoT，其中 .NET Framework 不可用）。

因为 PowerShell 版本对应于其 .NET 运行时，所以它是 .NET API 和 PowerShell 模块兼容性的主要指标;一些 .NET Api、类型或方法在 .NET 运行时中均不可用，这会影响依赖于它们的 PowerShell 脚本和模块。

## <a name="the-psedition-automatic-variable"></a>`$PSEdition`自动变量

在 PowerShell 5.1 及更高版本中，可以通过自动变量了解正在运行的版本 `$PSEdition` ：

```powershell
$PSEdition
```

```Output
Core
```

在 PowerShell 4 和更低的中，此变量不存在。 `$PSEdition` 应将 null 视为与具有值的相同 `Desktop` 。

### <a name="edition-in-psversiontable"></a>版本 `$PSVersionTable`

`$PSVersionTable`自动变量在 PowerShell 5.1 和更高版本中还包含版本信息：

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

该 `PSEdition` 字段将具有与自动变量相同的值 `$PSEdition` 。

## <a name="the-compatiblepseditions-module-manifest-field"></a>`CompatiblePSEditions`模块清单字段

PowerShell 模块可以声明与使用模块清单的字段兼容的 PowerShell 版本 `CompatiblePSEditions` 。

例如，声明与 `Desktop` PowerShell 和版本的兼容性的模块清单 `Core` ：

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

仅具有兼容性的模块清单示例 `Desktop` ：

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

省略 `CompatiblePSEditions` 模块清单中的字段将具有与将其设置为相同的效果 `Desktop` ，因为引入此字段之前创建的模块是为此版本隐式编写的。

对于在 Windows (（即从库中编写或安装的模块）中未随附的模块) ，此字段只是信息性的;PowerShell 不会根据字段更改行为 `CompatiblePSEditions` ，但会在 `PSModuleInfo` `Get-Module`) 为自己的逻辑返回的对象 (公开它：

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
> `CompatiblePSEditions`模块字段仅与 PowerShell 5.1 和更高版本兼容。
> 包含此字段将导致模块与 PowerShell 4 和更低的模块不兼容。
> 因为字段只是信息性的，所以可以在以后的 PowerShell 版本中安全地省略。

在 PowerShell 6.1 中， `Get-Module -ListAvailable` 已更新其格式化程序以显示每个模块的版本兼容性：

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

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>版本-Windows 附带的模块的兼容性

对于作为 Windows (的一部分，或者作为角色或功能的一部分安装的模块) ，PowerShell 6.1 和更高版本会以不同的方式来处理该 `CompatiblePSEditions` 字段。 此类模块位于 Windows PowerShell 系统模块目录中 (`%windir%\System\WindowsPowerShell\v1.0\Modules`) 中。

对于从或在此目录中找到的模块，PowerShell 6.1 和更高版本使用 `CompatiblePSEditions` 字段来确定模块是否将与当前会话兼容并相应地进行处理。

`Import-Module`使用时，不会导入不包含在中的模块， `Core` `CompatiblePSEditions` 并将显示错误：

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

`Get-Module -ListAvailable`使用时， `Core` 不会显示不在中的模块 `CompatiblePSEditions` ：

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

在这两种情况下， `-SkipEditionCheck` 开关参数均可用于重写此行为：

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
> `Import-Module -SkipEditionCheck` 模块可能看起来是成功的，但使用该模块会在以后遇到不兼容的风险。尽管加载模块最初会成功，但后面的命令可能会调用不兼容的 API，并自发地失败。

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>创作用于版本互兼容性的 PowerShell 模块

编写 PowerShell 模块以面向 `Desktop` 和 `Core` 版本的 powershell 时，可以执行一些操作来确保跨版本兼容性。

确认和持续验证兼容性的唯一真正的方法是为脚本或模块编写测试，并在需要与兼容的所有 PowerShell 版本和版本上运行这些测试。 为此，建议的测试框架是 [Pester][]。

### <a name="powershell-script"></a>PowerShell 脚本

作为一种语言，PowerShell 在不同版本之间的工作方式相同;它是你使用的、受版本兼容性影响的 cmdlet、模块和 .NET Api。

通常，在 PowerShell 6.1 及更高版本中使用的脚本将适用于 Windows PowerShell 5.1，但有一些例外情况。

版本 1.18.0 [PSScriptAnalyzer][] 模块具有 [`PSUseCompatibleCommands`][] 和等规则，这些规则 [`PSUseCompatibleTypes`][] 能够检测到 PowerShell 脚本中可能不兼容的命令和 .net api 的用法。

### <a name="net-assemblies"></a>.NET 程序集

如果要编写包含 .NET 程序集的二进制模块或模块 (Dll) 从源代码生成的，则应根据 .NET 和 PowerShell API 兼容性的编译时兼容性验证 [.NET Standard][] 和 [powershell 标准][] 进行编译。

尽管这些库能够在编译时检查某些兼容性，但它们无法捕获各个版本之间的可能行为差异。 为此，你仍必须编写测试。

## <a name="see-also"></a>请参阅

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)
- [具有兼容的 PowerShell 版本的模块](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
