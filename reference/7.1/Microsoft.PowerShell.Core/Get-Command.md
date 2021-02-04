---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5f2752f53fb5f74b6436548c3bd4fa731d2b02d5
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879229"
---
# <span data-ttu-id="9b402-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="9b402-103">Get-Command</span></span>

## <span data-ttu-id="9b402-104">摘要</span><span class="sxs-lookup"><span data-stu-id="9b402-104">SYNOPSIS</span></span>
<span data-ttu-id="9b402-105">获取所有命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-105">Gets all commands.</span></span>

## <span data-ttu-id="9b402-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b402-106">SYNTAX</span></span>

### <span data-ttu-id="9b402-107">CmdletSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="9b402-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="9b402-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="9b402-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="9b402-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9b402-109">DESCRIPTION</span></span>

<span data-ttu-id="9b402-110">该 `Get-Command` cmdlet 将获取安装在计算机上的所有命令，包括 cmdlet、别名、函数、筛选器、脚本和应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b402-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="9b402-111">`Get-Command` 从 PowerShell 模块中获取命令，以及从其他会话导入的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="9b402-112">若要仅获取已导入到当前会话中的命令，请使用 **ListImported** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="9b402-113">如果没有参数，则将 `Get-Command` 获取计算机上安装的所有 cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="9b402-114">`Get-Command *` 获取所有类型的命令，包括 Path 环境变量中的所有非 PowerShell 文件 (`$env:Path`) ，它将在应用程序命令类型中列出。</span><span class="sxs-lookup"><span data-stu-id="9b402-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="9b402-115">`Get-Command` 如果使用命令的确切名称（不包含通配符），则会自动导入包含命令的模块，以便你可以立即使用命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="9b402-116">若要启用、禁用和配置模块的自动导入，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="9b402-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="9b402-117">有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9b402-118">`Get-Command` 直接从命令代码获取其数据，这不同于 `Get-Help` ，它从帮助主题中获取其信息。</span><span class="sxs-lookup"><span data-stu-id="9b402-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="9b402-119">从 Windows PowerShell 5.0 开始， `Get-Command` 默认情况下，cmdlet 的结果显示 **版本** 列。</span><span class="sxs-lookup"><span data-stu-id="9b402-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="9b402-120">新 **版本** 属性已添加到 **CommandInfo** 类。</span><span class="sxs-lookup"><span data-stu-id="9b402-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="9b402-121">示例</span><span class="sxs-lookup"><span data-stu-id="9b402-121">EXAMPLES</span></span>

### <span data-ttu-id="9b402-122">示例1：获取 cmdlet、函数和别名</span><span class="sxs-lookup"><span data-stu-id="9b402-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="9b402-123">此命令将获取安装在计算机上的 PowerShell cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="9b402-124">示例2：获取当前会话中的命令</span><span class="sxs-lookup"><span data-stu-id="9b402-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="9b402-125">此命令使用 **ListImported** 参数来仅获取当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="9b402-126">示例3：获取 cmdlet 并按顺序显示</span><span class="sxs-lookup"><span data-stu-id="9b402-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="9b402-127">此命令将获取所有的 cmdlet、通过 cmdlet 名称中的名词按字母顺序对其进行排序，然后将其显示在基于名词的组中。</span><span class="sxs-lookup"><span data-stu-id="9b402-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="9b402-128">此显示内容可帮助你在任务中查找 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="9b402-129">示例4：获取模块中的命令</span><span class="sxs-lookup"><span data-stu-id="9b402-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="9b402-130">此命令使用 **Module** 参数来获取 Microsoft. Security 和 Microsoft. Utility 模块中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="9b402-131">示例5：获取有关 cmdlet 的信息</span><span class="sxs-lookup"><span data-stu-id="9b402-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="9b402-132">此命令获取有关 cmdlet 的信息 `Get-AppLockerPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="9b402-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="9b402-133">它还会导入 **AppLocker** 模块，该模块可将 **AppLocker** 模块中的所有命令添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="9b402-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="9b402-134">自动导入模块后，效果与使用 Import-Module cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="9b402-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="9b402-135">该模块可以添加命令、类型和格式设置文件，并在会话中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="9b402-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="9b402-136">若要启用、禁用和配置自动导入模块，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="9b402-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="9b402-137">有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="9b402-138">示例6：获取 cmdlet 的语法</span><span class="sxs-lookup"><span data-stu-id="9b402-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="9b402-139">当在 Cert：  `Get-ChildItem` 驱动器中使用 cmdlet 时，此命令将使用 ArgumentList 和句法参数获取该 cmdlet 的语法。</span><span class="sxs-lookup"><span data-stu-id="9b402-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="9b402-140">Cert：驱动器是证书提供程序添加到会话中的 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9b402-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="9b402-141">当你将输出中显示的语法与省略 **Args** (**ArgumentList**) 参数时显示的语法进行比较时，你会看到 **证书提供程序** 将动态参数 **CodeSigningCert** 添加到 `Get-ChildItem` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="9b402-142">有关证书提供程序的详细信息，请参阅 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="9b402-143">示例7：获取动态参数</span><span class="sxs-lookup"><span data-stu-id="9b402-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="9b402-144">该示例中的命令使用 `Get-DynamicParameters` 函数获取证书提供程序在证书 `Get-ChildItem` ：驱动器中使用时添加到 cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="9b402-145">`Get-DynamicParameters`此示例中的函数获取 cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="9b402-146">这是上一示例中所用方法的替代方法。</span><span class="sxs-lookup"><span data-stu-id="9b402-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="9b402-147">可以通过另一个 cmdlet 或提供程序将 Dynamic 参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="9b402-148">示例8：获取所有类型的所有命令</span><span class="sxs-lookup"><span data-stu-id="9b402-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="9b402-149">此命令将获取本地计算机上所有类型的所有命令，包括 **Path** 环境变量路径中的可执行文件 (`$env:path`) 。</span><span class="sxs-lookup"><span data-stu-id="9b402-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="9b402-150">它将为每个文件返回一个 **ApplicationInfo** 对象 (System.Management.Automation.ApplicationInfo)，而不是 **FileInfo** 对象 (System.IO.FileInfo)。</span><span class="sxs-lookup"><span data-stu-id="9b402-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="9b402-151">示例9：使用参数名称和类型获取 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9b402-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="9b402-152">此命令将获取其名称包含 authentication 且类型为 **system.management.automation.runspaces.authenticationmechanism** 的参数的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="9b402-153">可以使用类似此命令的命令查找允许你指定用于对用户进行身份验证的方法的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="9b402-154">即使采用 **AuthenticationMechanism** 值的参数和采用 **AuthenticationLevel** 参数的参数具有类似名称，**ParameterType** 参数也可区分它们。</span><span class="sxs-lookup"><span data-stu-id="9b402-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="9b402-155">示例10：获取别名</span><span class="sxs-lookup"><span data-stu-id="9b402-155">Example 10: Get an alias</span></span>

<span data-ttu-id="9b402-156">此示例演示如何使用 `Get-Command` 带有别名的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="9b402-157">虽然它通常用于 cmdlet 和函数，但 `Get-Command` 也可获取脚本、函数、别名和可执行文件。</span><span class="sxs-lookup"><span data-stu-id="9b402-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="9b402-158">命令的输出将显示别名的 **Name** 属性值的特殊视图。</span><span class="sxs-lookup"><span data-stu-id="9b402-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="9b402-159">该视图将显示别名以及完整的命令名称。</span><span class="sxs-lookup"><span data-stu-id="9b402-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="9b402-160">示例11：从别名获取语法</span><span class="sxs-lookup"><span data-stu-id="9b402-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="9b402-161">此示例演示如何获取语法以及别名的标准名称。</span><span class="sxs-lookup"><span data-stu-id="9b402-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="9b402-162">该命令的输出显示带有标准名称的标记别名，后跟语法。</span><span class="sxs-lookup"><span data-stu-id="9b402-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="9b402-163">示例12：获取记事本命令的所有实例</span><span class="sxs-lookup"><span data-stu-id="9b402-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="9b402-164">此示例使用 cmdlet 的 **all** 参数 `Get-Command` `Notepad` 在本地计算机上显示该命令的所有实例。</span><span class="sxs-lookup"><span data-stu-id="9b402-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="9b402-165">当会话中的多个命令具有相同名称时，**All** 参数非常有用。</span><span class="sxs-lookup"><span data-stu-id="9b402-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="9b402-166">从 Windows PowerShell 3.0 开始，默认情况下，当会话中包含具有相同名称的多个命令时， `Get-Command` 仅获取键入命令名称时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="9b402-167">对于 **all** 参数， `Get-Command` 获取具有指定名称的所有命令，并按执行优先级顺序返回它们。</span><span class="sxs-lookup"><span data-stu-id="9b402-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="9b402-168">若要运行除列表中第一个命令以外的某个命令，请键入该命令的完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="9b402-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="9b402-169">有关命令优先级的详细信息，请参阅 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="9b402-170">示例13：获取包含 cmdlet 的模块的名称</span><span class="sxs-lookup"><span data-stu-id="9b402-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="9b402-171">此命令获取该 cmdlet 所源自的模块的名称 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="9b402-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="9b402-172">该命令使用所有命令的 **ModuleName** 属性。</span><span class="sxs-lookup"><span data-stu-id="9b402-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="9b402-173">此命令格式适用于 PowerShell 模块中的命令，即使未将它们导入到会话中也是如此。</span><span class="sxs-lookup"><span data-stu-id="9b402-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="9b402-174">示例14：获取具有输出类型的 cmdlet 和函数</span><span class="sxs-lookup"><span data-stu-id="9b402-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="9b402-175">此命令将获取具有输出类型及其返回的对象类型的 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="9b402-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="9b402-176">该命令的第一部分将获取所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="9b402-177">管道运算符 (`|`) 将 cmdlet 发送到 `Where-Object` cmdlet，该 cmdlet 只选择在其中填充 **OutputType** 属性的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="9b402-178">另一个管道运算符将选定的 cmdlet 对象发送到 `Format-List` cmdlet，该 cmdlet 将在列表中显示每个 cmdlet 的名称和输出类型。</span><span class="sxs-lookup"><span data-stu-id="9b402-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="9b402-179">仅当 cmdlet 代码为 cmdlet 定义了 **OutputType** 属性时，**CommandInfo** 对象的 **OutputType** 属性的值才为非 null。</span><span class="sxs-lookup"><span data-stu-id="9b402-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="9b402-180">示例15：获取采用特定对象类型作为输入的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9b402-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="9b402-181">此命令可查找将网络适配器对象用作输入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="9b402-182">可以使用此命令格式查找接受任何命令返回的对象类型的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="9b402-183">该命令使用所有对象的 **PSTypeNames** 内部属性，它将获取用于描述该对象的类型。</span><span class="sxs-lookup"><span data-stu-id="9b402-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="9b402-184">若要获取网络适配器的 **PSTypeNames** 属性，而不是网络适配器集合的 **PSTypeNames** 属性，该命令将使用数组表示法来获取该 cmdlet 返回的第一个网络适配器。</span><span class="sxs-lookup"><span data-stu-id="9b402-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="9b402-185">示例16：使用模糊匹配获取命令</span><span class="sxs-lookup"><span data-stu-id="9b402-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="9b402-186">在此示例中，该命令的名称特意将错误键入为 "commnd"。</span><span class="sxs-lookup"><span data-stu-id="9b402-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="9b402-187">通过使用 `-UseFuzzyMatching` 开关，cmdlet 确定最佳匹配项 `Get-Command` 后跟系统上具有类似匹配项的其他本机命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="9b402-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b402-188">PARAMETERS</span></span>

### <span data-ttu-id="9b402-189">-All</span><span class="sxs-lookup"><span data-stu-id="9b402-189">-All</span></span>

<span data-ttu-id="9b402-190">指示此 cmdlet 获取所有命令，包括具有相同名称的相同类型的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="9b402-191">默认情况下， `Get-Command` 仅获取键入命令名称时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="9b402-192">有关当多个命令具有相同名称时 PowerShell 用于选择要运行的命令的方法的详细信息，请参阅 [about_Command_Precedence](About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="9b402-193">有关由于名称冲突而默认情况下不会运行的模块限定命令名称和运行命令的信息，请参阅 [about_Modules](About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="9b402-194">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="9b402-195">在 Windows PowerShell 2.0 中， `Get-Command` 默认情况下获取所有命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-196">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9b402-196">-ArgumentList</span></span>

<span data-ttu-id="9b402-197">指定参数数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-197">Specifies an array of arguments.</span></span> <span data-ttu-id="9b402-198">此 cmdlet 将获取有关 cmdlet 或函数的信息，与指定参数一起使用时， ( "arguments" ) 。</span><span class="sxs-lookup"><span data-stu-id="9b402-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="9b402-199">**ArgumentList** 的别名是 **Args**。</span><span class="sxs-lookup"><span data-stu-id="9b402-199">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="9b402-200">若要检测仅当使用某些其他参数时才可用的动态参数，请将 **ArgumentList** 的值设置为触发动态参数的参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="9b402-201">若要检测提供程序添加到 cmdlet 的动态参数，请将 **ArgumentList** 参数的值设置为提供程序驱动器中的路径，例如 WSMan：、HKLM：或 Cert：。</span><span class="sxs-lookup"><span data-stu-id="9b402-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="9b402-202">如果命令是 PowerShell 提供程序 cmdlet，请在每个命令中仅输入一个路径。</span><span class="sxs-lookup"><span data-stu-id="9b402-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="9b402-203">提供程序 cmdlet 只为第一个路径返回值为 **ArgumentList** 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="9b402-204">有关提供程序 cmdlet 的信息，请参阅 [about_Providers](About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="9b402-205">-CommandType</span></span>

<span data-ttu-id="9b402-206">指定此 cmdlet 获取的命令类型。</span><span class="sxs-lookup"><span data-stu-id="9b402-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="9b402-207">输入一个或多个命令类型。</span><span class="sxs-lookup"><span data-stu-id="9b402-207">Enter one or more command types.</span></span> <span data-ttu-id="9b402-208">使用 **CommandType** 或其别名 **Type**。</span><span class="sxs-lookup"><span data-stu-id="9b402-208">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="9b402-209">默认情况下，将 `Get-Command` 获取所有 cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="9b402-210">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="9b402-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9b402-211">A.</span><span class="sxs-lookup"><span data-stu-id="9b402-211">Alias.</span></span> <span data-ttu-id="9b402-212">获取所有 PowerShell 命令的别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-212">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="9b402-213">有关详细信息，请参阅 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-213">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="9b402-214">全部。</span><span class="sxs-lookup"><span data-stu-id="9b402-214">All.</span></span> <span data-ttu-id="9b402-215">获取所有命令类型。</span><span class="sxs-lookup"><span data-stu-id="9b402-215">Gets all command types.</span></span> <span data-ttu-id="9b402-216">此参数值等效于 `Get-Command *` 。</span><span class="sxs-lookup"><span data-stu-id="9b402-216">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="9b402-217">应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b402-217">Application.</span></span> <span data-ttu-id="9b402-218">获取 **Path** 环境变量中列出的路径中的非 PowerShell 文件 ($env:p a) ，包括 .txt、.exe 和 .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="9b402-218">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="9b402-219">有关 **Path** 环境变量的详细信息，请参阅 about_Environment_Variables。</span><span class="sxs-lookup"><span data-stu-id="9b402-219">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="9b402-220">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b402-220">Cmdlet.</span></span> <span data-ttu-id="9b402-221">获取所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-221">Gets all cmdlets.</span></span>
- <span data-ttu-id="9b402-222">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="9b402-222">ExternalScript.</span></span> <span data-ttu-id="9b402-223">获取在 **Path** 环境变量 ($env:path) 中列出的路径中的所有 .ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="9b402-223">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="9b402-224">Filter 和 Function。</span><span class="sxs-lookup"><span data-stu-id="9b402-224">Filter and Function.</span></span> <span data-ttu-id="9b402-225">获取所有 PowerShell 高级和简单函数和筛选器。</span><span class="sxs-lookup"><span data-stu-id="9b402-225">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="9b402-226">脚本。</span><span class="sxs-lookup"><span data-stu-id="9b402-226">Script.</span></span> <span data-ttu-id="9b402-227">获取所有脚本块。</span><span class="sxs-lookup"><span data-stu-id="9b402-227">Gets all script blocks.</span></span> <span data-ttu-id="9b402-228">若要)  ( ps1 文件获取 PowerShell 脚本，请使用 ExternalScript 值。</span><span class="sxs-lookup"><span data-stu-id="9b402-228">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-229">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="9b402-229">-FullyQualifiedModule</span></span>

<span data-ttu-id="9b402-230">指定以 **ModuleSpecification** 对象的形式指定的模块，在 ModuleSpecification 构造函数的 " **备注** " 部分中介绍 [ (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。</span><span class="sxs-lookup"><span data-stu-id="9b402-230">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="9b402-231">例如， **FullyQualifiedModule** 参数接受以下格式之一指定的模块名称：</span><span class="sxs-lookup"><span data-stu-id="9b402-231">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="9b402-232">**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="9b402-232">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="9b402-233">不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-233">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="9b402-234">这两个参数是互斥的。</span><span class="sxs-lookup"><span data-stu-id="9b402-234">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-235">-ListImported</span><span class="sxs-lookup"><span data-stu-id="9b402-235">-ListImported</span></span>

<span data-ttu-id="9b402-236">指示此 cmdlet 仅获取当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-236">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="9b402-237">从 PowerShell 3.0 开始，默认情况下， `Get-Command` 会获取所有已安装的命令，包括但不限于当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-237">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="9b402-238">在 PowerShell 2.0 中，它只获取当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-238">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="9b402-239">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-240">-Module</span><span class="sxs-lookup"><span data-stu-id="9b402-240">-Module</span></span>

<span data-ttu-id="9b402-241">指定模块的数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-241">Specifies an array of modules.</span></span> <span data-ttu-id="9b402-242">此 cmdlet 将获取来自指定模块的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-242">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="9b402-243">输入模块或模块对象的名称。</span><span class="sxs-lookup"><span data-stu-id="9b402-243">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="9b402-244">此参数采用字符串值，但此参数的值还可以是 **PSModuleInfo** 对象，例如 `Get-Module` 和 `Import-PSSession` cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="9b402-244">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-245">-Name</span><span class="sxs-lookup"><span data-stu-id="9b402-245">-Name</span></span>

<span data-ttu-id="9b402-246">指定一个名称数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-246">Specifies an array of names.</span></span> <span data-ttu-id="9b402-247">此 cmdlet 仅获取具有指定名称的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-247">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="9b402-248">输入一个名称或名称模式。</span><span class="sxs-lookup"><span data-stu-id="9b402-248">Enter a name or name pattern.</span></span> <span data-ttu-id="9b402-249">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9b402-249">Wildcard characters are permitted.</span></span>

<span data-ttu-id="9b402-250">若要获取具有相同名称的命令，请使用 **All** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-250">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="9b402-251">如果两个命令具有相同的名称，则默认情况下，将 `Get-Command` 获取键入命令名称时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-251">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-252">-名词</span><span class="sxs-lookup"><span data-stu-id="9b402-252">-Noun</span></span>

<span data-ttu-id="9b402-253">指定一个命令名词的数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-253">Specifies an array of command nouns.</span></span> <span data-ttu-id="9b402-254">此 cmdlet 将获取包含具有指定名词的名称的命令，其中包括 cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-254">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="9b402-255">输入一个或多个名词或名词模式。</span><span class="sxs-lookup"><span data-stu-id="9b402-255">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="9b402-256">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9b402-256">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-257">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="9b402-257">-ParameterName</span></span>

<span data-ttu-id="9b402-258">指定参数名称的数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-258">Specifies an array of parameter names.</span></span> <span data-ttu-id="9b402-259">此 cmdlet 将获取会话中具有指定参数的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-259">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="9b402-260">输入参数名称或参数别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-260">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="9b402-261">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9b402-261">Wildcard characters are supported.</span></span>

<span data-ttu-id="9b402-262">**ParameterName** 和 **ParameterType** 参数仅搜索当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-262">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="9b402-263">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-264">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="9b402-264">-ParameterType</span></span>

<span data-ttu-id="9b402-265">指定参数名称的数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-265">Specifies an array of parameter names.</span></span> <span data-ttu-id="9b402-266">此 cmdlet 将获取会话中具有指定类型的参数的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-266">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="9b402-267">输入参数类型的全名或部分名称。</span><span class="sxs-lookup"><span data-stu-id="9b402-267">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="9b402-268">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9b402-268">Wildcard characters are supported.</span></span>

<span data-ttu-id="9b402-269">**ParameterName** 和 **ParameterType** 参数仅搜索当前会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-269">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="9b402-270">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-271">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-271">-ShowCommandInfo</span></span>

<span data-ttu-id="9b402-272">指示此 cmdlet 显示命令信息。</span><span class="sxs-lookup"><span data-stu-id="9b402-272">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="9b402-273">此参数是在 Windows PowerShell 5.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="9b402-273">This parameter was introduced in Windows PowerShell 5.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-274">-语法</span><span class="sxs-lookup"><span data-stu-id="9b402-274">-Syntax</span></span>

<span data-ttu-id="9b402-275">指示此 cmdlet 仅获取有关该命令的下列指定数据：</span><span class="sxs-lookup"><span data-stu-id="9b402-275">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="9b402-276">别名.</span><span class="sxs-lookup"><span data-stu-id="9b402-276">Aliases.</span></span> <span data-ttu-id="9b402-277">获取标准名称和语法。</span><span class="sxs-lookup"><span data-stu-id="9b402-277">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="9b402-278">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b402-278">Cmdlets.</span></span> <span data-ttu-id="9b402-279">获取语法。</span><span class="sxs-lookup"><span data-stu-id="9b402-279">Gets the syntax.</span></span>
- <span data-ttu-id="9b402-280">函数和筛选器。</span><span class="sxs-lookup"><span data-stu-id="9b402-280">Functions and filters.</span></span> <span data-ttu-id="9b402-281">获取函数定义。</span><span class="sxs-lookup"><span data-stu-id="9b402-281">Gets the function definition.</span></span>
- <span data-ttu-id="9b402-282">脚本和应用程序或文件。</span><span class="sxs-lookup"><span data-stu-id="9b402-282">Scripts and applications or files.</span></span> <span data-ttu-id="9b402-283">获取路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9b402-283">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-284">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="9b402-284">-TotalCount</span></span>

<span data-ttu-id="9b402-285">指定要获取的命令数。</span><span class="sxs-lookup"><span data-stu-id="9b402-285">Specifies the number of commands to get.</span></span> <span data-ttu-id="9b402-286">可以使用此参数来限制命令的输出。</span><span class="sxs-lookup"><span data-stu-id="9b402-286">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-287">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="9b402-287">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="9b402-288">指示使用命令中的匹配字符在命令中查找大写字符。</span><span class="sxs-lookup"><span data-stu-id="9b402-288">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="9b402-289">例如， `i-psdf` 将匹配， `Import-PowerShellDataFile` 因为要查找的每个字符都匹配结果中的大写字符。</span><span class="sxs-lookup"><span data-stu-id="9b402-289">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="9b402-290">当使用这种类型的匹配时，任何通配符将导致不匹配。</span><span class="sxs-lookup"><span data-stu-id="9b402-290">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-291">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="9b402-291">-UseFuzzyMatching</span></span>

<span data-ttu-id="9b402-292">指示在查找命令时使用模糊匹配算法。</span><span class="sxs-lookup"><span data-stu-id="9b402-292">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="9b402-293">输出的顺序是从最接近的匹配到最小的可能匹配。</span><span class="sxs-lookup"><span data-stu-id="9b402-293">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="9b402-294">不应将通配符与模糊匹配一起使用，因为它会尝试匹配可能包含这些通配符字符的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-294">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b402-295">-Verb</span><span class="sxs-lookup"><span data-stu-id="9b402-295">-Verb</span></span>

<span data-ttu-id="9b402-296">指定命令谓词的数组。</span><span class="sxs-lookup"><span data-stu-id="9b402-296">Specifies an array of command verbs.</span></span> <span data-ttu-id="9b402-297">此 cmdlet 将获取包含包含指定谓词的名称的命令，其中包括 cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-297">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="9b402-298">输入一个或多个谓词或谓词模式。</span><span class="sxs-lookup"><span data-stu-id="9b402-298">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="9b402-299">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9b402-299">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9b402-300">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b402-300">CommonParameters</span></span>

<span data-ttu-id="9b402-301">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9b402-301">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b402-302">有关详细信息，请参阅 [about_CommonParameters](About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-302">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9b402-303">输入</span><span class="sxs-lookup"><span data-stu-id="9b402-303">INPUTS</span></span>

### <span data-ttu-id="9b402-304">System.String</span><span class="sxs-lookup"><span data-stu-id="9b402-304">System.String</span></span>

<span data-ttu-id="9b402-305">可以通过管道将命令名称传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-305">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="9b402-306">输出</span><span class="sxs-lookup"><span data-stu-id="9b402-306">OUTPUTS</span></span>

### <span data-ttu-id="9b402-307">System.web. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-307">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="9b402-308">此 cmdlet 返回派生自 **CommandInfo** 类的对象。</span><span class="sxs-lookup"><span data-stu-id="9b402-308">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="9b402-309">返回的对象类型取决于获取的命令类型 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="9b402-309">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="9b402-310">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-310">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="9b402-311">表示别名。</span><span class="sxs-lookup"><span data-stu-id="9b402-311">Represents aliases.</span></span>

### <span data-ttu-id="9b402-312">System.web. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-312">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="9b402-313">表示应用程序和文件。</span><span class="sxs-lookup"><span data-stu-id="9b402-313">Represents applications and files.</span></span>

### <span data-ttu-id="9b402-314">System.web. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-314">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="9b402-315">表示 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b402-315">Represents cmdlets.</span></span>

### <span data-ttu-id="9b402-316">System.web. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="9b402-316">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="9b402-317">表示函数和筛选器。</span><span class="sxs-lookup"><span data-stu-id="9b402-317">Represents functions and filters.</span></span>

## <span data-ttu-id="9b402-318">注释</span><span class="sxs-lookup"><span data-stu-id="9b402-318">NOTES</span></span>

* <span data-ttu-id="9b402-319">当具有相同名称的多个命令可用于会话时，将返回在 `Get-Command` 键入命令名称时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="9b402-319">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="9b402-320">若要获取具有相同名称的命令（按运行顺序列出），请使用 **All** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b402-320">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="9b402-321">有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-321">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="9b402-322">自动导入模块后，效果与使用 `Import-Module` cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="9b402-322">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="9b402-323">该模块可以添加命令、类型和格式设置文件，并在会话中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="9b402-323">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="9b402-324">若要启用、禁用和配置自动导入模块，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="9b402-324">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="9b402-325">有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-325">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="9b402-326">相关链接</span><span class="sxs-lookup"><span data-stu-id="9b402-326">RELATED LINKS</span></span>

[<span data-ttu-id="9b402-327">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="9b402-327">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="9b402-328">Get-Help</span><span class="sxs-lookup"><span data-stu-id="9b402-328">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="9b402-329">Get-Member</span><span class="sxs-lookup"><span data-stu-id="9b402-329">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="9b402-330">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="9b402-330">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="9b402-331">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="9b402-331">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="9b402-332">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="9b402-332">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)

