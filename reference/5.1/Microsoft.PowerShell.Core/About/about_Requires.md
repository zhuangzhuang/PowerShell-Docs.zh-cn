---
description: 禁止运行脚本而不使用所需的元素。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: f8ff922fcf8deb710008bbd9bab619f137d6c831
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490697"
---
# <a name="about-requires"></a>关于要求

## <a name="short-description"></a>简短说明
禁止运行脚本而不使用所需的元素。

## <a name="long-description"></a>长说明

`#Requires`语句阻止脚本运行，除非 PowerShell 版本、模块 (和版本) 或管理单元 (和版本) ，并满足版本先决条件。 如果不满足先决条件，PowerShell 不会运行该脚本。

### <a name="syntax"></a>语法

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

有关语法的详细信息，请参阅 [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)。

### <a name="rules-for-use"></a>使用规则

脚本可包含多个 `#Requires` 语句。 `#Requires`语句可以显示在脚本中的任何一行上。

将 `#Requires` 语句放在函数内不会限制其作用域。 所有 `#Requires` 语句始终都是全局应用的，并且必须满足后，才能执行脚本。

> [!WARNING]
> 尽管 `#Requires` 语句可以出现在脚本中的任何行上，但其在脚本中的位置并不会影响其应用程序的顺序。 在 `#Requires` 执行脚本之前，必须满足语句提供的全局状态。

例如：

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

您可能认为上述代码不应运行，因为所需的模块已在语句之前删除 `#Requires` 。 但是， `#Requires` 必须先满足状态，然后才能执行该脚本。 然后，该脚本的第一行会使所需状态失效。

### <a name="parameters"></a>参数

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>-Assembly \<Assembly path> |\<.NET assembly specification>

> [!IMPORTANT]
> `-Assembly`语法已弃用。 它不提供任何功能。 已在 PowerShell 5.1 中添加语法，但从未实现支持代码。 为了向后兼容，仍接受语法。

指定程序集 DLL 文件或 .NET 程序集名称的路径。 在 PowerShell 5.0 中引入了 **Assembly** 参数。 有关 .NET 程序集的详细信息，请参阅 [程序集名称](/dotnet/standard/assembly/names)。

例如：

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Version \<N\> [. \<n\> ]

指定脚本所需的 PowerShell 的最低版本。 输入主版本号和可选的次版本号。

例如：

```powershell
#Requires -Version 5.1
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-Add-pssnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]

指定脚本需要的 PowerShell 管理单元。 输入管理单元名称和可选版本号。

例如：

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>-模块 \<Module-Name\> |\<Hashtable\>

指定脚本所需的 PowerShell 模块。 输入模块名称和可选版本号。

如果所需模块不在当前会话中，则 PowerShell 会将其导入。
如果无法导入模块，则 PowerShell 将引发一个终止错误。

对于每个模块，键入模块名称 (\<String\>) 或哈希表。 值可以是字符串和哈希表的组合。 此哈希表具有以下键。

- `ModuleName` - **必需** 指定模块名称。
- `GUID` - **可选** 指定模块的 GUID。
- 还 **需要** 指定以下三个键中的一个。 这些密钥不能一起使用。
  - `ModuleVersion` -指定模块的最低可接受版本。
  - `RequiredVersion` -指定模块的准确的必需版本。
  - `MaximumVersion` -指定模块可接受的最大版本。

> [!NOTE]
> `RequiredVersion` 已在 Windows PowerShell 5.0 中添加。
> `MaximumVersion` 已在 Windows PowerShell 5.1 中添加。

例如：

要求 `Hyper-V` 安装 (版本 `1.1` 或更高版本的) 。

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; ModuleVersion="1.1" }
```

要求 `Hyper-V` **仅** 安装版本 `1.1`)  (。

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="1.1" }
```

要求 `Hyper-V` 安装 (版本 `1.1` 或更低) 。

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; MaximumVersion="1.1" }
```

要求安装和的任何 `PSScheduledJob` 版本 `PSWorkflow` 。

```powershell
#Requires -Modules PSWorkflow, PSScheduledJob
```

使用该 `RequiredVersion` 密钥时，请确保版本字符串与你希望需要的版本字符串完全匹配。

```powershell
Get-Module Hyper-V
```

```Output
ModuleType Version    Name     ExportedCommands
---------- -------    ----     ------------------
Binary     2.0.0.0    hyper-v  {Add-VMAssignableDevice, ...}
```

下面的示例失败，因为 **2.0.0** 与 **2.0.0.0** 不完全匹配。

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="2.0.0" }
```

#### <a name="-psedition-psedition-name"></a>-PSEdition \<PSEdition-Name\>

指定脚本所需的 PowerShell 版本。 有效值为适用于 PowerShell Core 的 **核心** 和适用于 Windows PowerShell 的 **桌面** 。

例如：

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

指定脚本所需的 shell。 输入 shell ID。 如果使用 **ShellId** 参数，则还必须包含 **add-pssnapin** 参数。
可以通过查询自动变量找到当前 **ShellId** `$ShellId` 。

例如：

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> 此参数旨在用于不推荐使用的微型外壳程序。

#### <a name="-runasadministrator"></a>-RunAsAdministrator

将此开关参数添加到语句时 `#Requires` ，它会指定你在其中运行脚本的 PowerShell 会话必须以提升的用户权限启动。 **RunAsAdministrator** 参数在非 Windows 操作系统上被忽略。 PowerShell 4.0 中引入了 **RunAsAdministrator** 参数。

例如：

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>示例

下面的脚本包含两个 `#Requires` 语句。 如果不满足这两个语句中指定的要求，则脚本不会运行。 每个 `#Requires` 语句都必须是一行上的第一项：

```powershell
#Requires -Modules PSWorkflow
#Requires -Version 3
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>另请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_PSSnapins](about_PSSnapins.md)

[Get-PSSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)
