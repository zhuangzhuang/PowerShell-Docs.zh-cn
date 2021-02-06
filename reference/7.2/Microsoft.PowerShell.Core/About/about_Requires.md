---
description: 禁止运行脚本而不使用所需的元素。
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: d340de615923437bb3e29c1984ef8849fe03a40e
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "99598060"
---
# <a name="about-requires"></a><span data-ttu-id="3de46-103">关于要求</span><span class="sxs-lookup"><span data-stu-id="3de46-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="3de46-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="3de46-104">Short description</span></span>
<span data-ttu-id="3de46-105">禁止运行脚本而不使用所需的元素。</span><span class="sxs-lookup"><span data-stu-id="3de46-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="3de46-106">长说明</span><span class="sxs-lookup"><span data-stu-id="3de46-106">Long description</span></span>

<span data-ttu-id="3de46-107">`#Requires`语句阻止脚本运行，除非 PowerShell 版本、模块 (和版本) 或管理单元 (和版本) ，并满足版本先决条件。</span><span class="sxs-lookup"><span data-stu-id="3de46-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="3de46-108">如果不满足先决条件，PowerShell 不会运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="3de46-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="3de46-109">语法</span><span class="sxs-lookup"><span data-stu-id="3de46-109">Syntax</span></span>

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="3de46-110">有关语法的详细信息，请参阅 [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)。</span><span class="sxs-lookup"><span data-stu-id="3de46-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="3de46-111">使用规则</span><span class="sxs-lookup"><span data-stu-id="3de46-111">Rules for use</span></span>

<span data-ttu-id="3de46-112">脚本可包含多个 `#Requires` 语句。</span><span class="sxs-lookup"><span data-stu-id="3de46-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="3de46-113">`#Requires`语句可以显示在脚本中的任何一行上。</span><span class="sxs-lookup"><span data-stu-id="3de46-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="3de46-114">将 `#Requires` 语句放在函数内不会限制其作用域。</span><span class="sxs-lookup"><span data-stu-id="3de46-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="3de46-115">所有 `#Requires` 语句始终都是全局应用的，并且必须满足后，才能执行脚本。</span><span class="sxs-lookup"><span data-stu-id="3de46-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="3de46-116">尽管 `#Requires` 语句可以出现在脚本中的任何行上，但其在脚本中的位置并不会影响其应用程序的顺序。</span><span class="sxs-lookup"><span data-stu-id="3de46-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="3de46-117">在 `#Requires` 执行脚本之前，必须满足语句提供的全局状态。</span><span class="sxs-lookup"><span data-stu-id="3de46-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="3de46-118">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="3de46-119">您可能认为上述代码不应运行，因为所需的模块已在语句之前删除 `#Requires` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="3de46-120">但是， `#Requires` 必须先满足状态，然后才能执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="3de46-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="3de46-121">然后，该脚本的第一行会使所需状态失效。</span><span class="sxs-lookup"><span data-stu-id="3de46-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="3de46-122">参数</span><span class="sxs-lookup"><span data-stu-id="3de46-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="3de46-123">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="3de46-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

> [!IMPORTANT]
> <span data-ttu-id="3de46-124">`-Assembly`语法已弃用。</span><span class="sxs-lookup"><span data-stu-id="3de46-124">The `-Assembly` syntax is deprecated.</span></span> <span data-ttu-id="3de46-125">它不提供任何功能。</span><span class="sxs-lookup"><span data-stu-id="3de46-125">It serves no function.</span></span> <span data-ttu-id="3de46-126">已在 PowerShell 5.1 中添加语法，但从未实现支持代码。</span><span class="sxs-lookup"><span data-stu-id="3de46-126">The syntax was added in PowerShell 5.1 but the supporting code was never implemented.</span></span> <span data-ttu-id="3de46-127">为了向后兼容，仍接受语法。</span><span class="sxs-lookup"><span data-stu-id="3de46-127">The syntax is still accepted for backward compatibility.</span></span>

<span data-ttu-id="3de46-128">指定程序集 DLL 文件或 .NET 程序集名称的路径。</span><span class="sxs-lookup"><span data-stu-id="3de46-128">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="3de46-129">在 PowerShell 5.0 中引入了 **Assembly** 参数。</span><span class="sxs-lookup"><span data-stu-id="3de46-129">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="3de46-130">有关 .NET 程序集的详细信息，请参阅 [程序集名称](/dotnet/standard/assembly/names)。</span><span class="sxs-lookup"><span data-stu-id="3de46-130">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="3de46-131">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-131">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="3de46-132">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="3de46-132">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="3de46-133">指定脚本所需的 PowerShell 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="3de46-133">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="3de46-134">输入主版本号和可选的次版本号。</span><span class="sxs-lookup"><span data-stu-id="3de46-134">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="3de46-135">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-135">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="3de46-136">-Add-pssnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="3de46-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="3de46-137">指定脚本需要的 PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="3de46-137">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="3de46-138">输入管理单元名称和可选版本号。</span><span class="sxs-lookup"><span data-stu-id="3de46-138">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="3de46-139">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-139">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="3de46-140">-模块 \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="3de46-140">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="3de46-141">指定脚本所需的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="3de46-141">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="3de46-142">输入模块名称和可选版本号。</span><span class="sxs-lookup"><span data-stu-id="3de46-142">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="3de46-143">如果所需模块不在当前会话中，则 PowerShell 会将其导入。</span><span class="sxs-lookup"><span data-stu-id="3de46-143">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="3de46-144">如果无法导入模块，则 PowerShell 将引发一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="3de46-144">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="3de46-145">对于每个模块，键入模块名称 (\<String\>) 或哈希表。</span><span class="sxs-lookup"><span data-stu-id="3de46-145">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="3de46-146">值可以是字符串和哈希表的组合。</span><span class="sxs-lookup"><span data-stu-id="3de46-146">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="3de46-147">此哈希表具有以下键。</span><span class="sxs-lookup"><span data-stu-id="3de46-147">The hash table has the following keys.</span></span>

- <span data-ttu-id="3de46-148">`ModuleName` - **必需** 指定模块名称。</span><span class="sxs-lookup"><span data-stu-id="3de46-148">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="3de46-149">`GUID` - **可选** 指定模块的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3de46-149">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="3de46-150">还 **需要** 指定以下三个键中的一个。</span><span class="sxs-lookup"><span data-stu-id="3de46-150">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="3de46-151">这些密钥不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="3de46-151">These keys can't be used together.</span></span>
  - <span data-ttu-id="3de46-152">`ModuleVersion` -指定模块的最低可接受版本。</span><span class="sxs-lookup"><span data-stu-id="3de46-152">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="3de46-153">`RequiredVersion` -指定模块的准确的必需版本。</span><span class="sxs-lookup"><span data-stu-id="3de46-153">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="3de46-154">`MaximumVersion` -指定模块可接受的最大版本。</span><span class="sxs-lookup"><span data-stu-id="3de46-154">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="3de46-155">`RequiredVersion` 已在 Windows PowerShell 5.0 中添加。</span><span class="sxs-lookup"><span data-stu-id="3de46-155">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="3de46-156">`MaximumVersion` 已在 Windows PowerShell 5.1 中添加。</span><span class="sxs-lookup"><span data-stu-id="3de46-156">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="3de46-157">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-157">For example:</span></span>

<span data-ttu-id="3de46-158">要求 `AzureRM.Netcore` 安装 (版本 `0.12.0` 或更高版本的) 。</span><span class="sxs-lookup"><span data-stu-id="3de46-158">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="3de46-159">要求 `AzureRM.Netcore` **仅** 安装版本 `0.12.0`)  (。</span><span class="sxs-lookup"><span data-stu-id="3de46-159">Require that `AzureRM.Netcore` (**only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="3de46-160">要求 `AzureRM.Netcore` 安装 (版本 `0.12.0` 或更低) 。</span><span class="sxs-lookup"><span data-stu-id="3de46-160">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="3de46-161">要求安装和的任何 `AzureRM.Netcore` 版本 `PowerShellGet` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-161">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="3de46-162">使用密钥时 `RequiredVersion` ，请确保版本字符串与所需的版本字符串完全匹配。</span><span class="sxs-lookup"><span data-stu-id="3de46-162">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="3de46-163">下面的示例失败，因为 **0.12** 与 **0.12.0** 不完全匹配。</span><span class="sxs-lookup"><span data-stu-id="3de46-163">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="3de46-164">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="3de46-164">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="3de46-165">指定脚本所需的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="3de46-165">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="3de46-166">有效值为适用于 PowerShell Core 的 **核心** 和适用于 Windows PowerShell 的 **桌面** 。</span><span class="sxs-lookup"><span data-stu-id="3de46-166">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="3de46-167">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-167">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="3de46-168">-ShellId</span><span class="sxs-lookup"><span data-stu-id="3de46-168">-ShellId</span></span>

<span data-ttu-id="3de46-169">指定脚本所需的 shell。</span><span class="sxs-lookup"><span data-stu-id="3de46-169">Specifies the shell that the script requires.</span></span> <span data-ttu-id="3de46-170">输入 shell ID。</span><span class="sxs-lookup"><span data-stu-id="3de46-170">Enter the shell ID.</span></span> <span data-ttu-id="3de46-171">如果使用 **ShellId** 参数，则还必须包含 **add-pssnapin** 参数。</span><span class="sxs-lookup"><span data-stu-id="3de46-171">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="3de46-172">可以通过查询自动变量找到当前 **ShellId** `$ShellId` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-172">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="3de46-173">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-173">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="3de46-174">此参数旨在用于不推荐使用的微型外壳程序。</span><span class="sxs-lookup"><span data-stu-id="3de46-174">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="3de46-175">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="3de46-175">-RunAsAdministrator</span></span>

<span data-ttu-id="3de46-176">将此开关参数添加到语句时 `#Requires` ，它会指定你在其中运行脚本的 PowerShell 会话必须以提升的用户权限启动。</span><span class="sxs-lookup"><span data-stu-id="3de46-176">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="3de46-177">**RunAsAdministrator** 参数在非 Windows 操作系统上被忽略。</span><span class="sxs-lookup"><span data-stu-id="3de46-177">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="3de46-178">PowerShell 4.0 中引入了 **RunAsAdministrator** 参数。</span><span class="sxs-lookup"><span data-stu-id="3de46-178">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="3de46-179">例如：</span><span class="sxs-lookup"><span data-stu-id="3de46-179">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="3de46-180">示例</span><span class="sxs-lookup"><span data-stu-id="3de46-180">Examples</span></span>

<span data-ttu-id="3de46-181">下面的脚本包含两个 `#Requires` 语句。</span><span class="sxs-lookup"><span data-stu-id="3de46-181">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="3de46-182">如果不满足这两个语句中指定的要求，则脚本不会运行。</span><span class="sxs-lookup"><span data-stu-id="3de46-182">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="3de46-183">每个 `#Requires` 语句都必须是一行上的第一项：</span><span class="sxs-lookup"><span data-stu-id="3de46-183">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="3de46-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="3de46-184">See also</span></span>

[<span data-ttu-id="3de46-185">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="3de46-185">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="3de46-186">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="3de46-186">about_Language_Keywords</span></span>](about_Language_Keywords.md)
