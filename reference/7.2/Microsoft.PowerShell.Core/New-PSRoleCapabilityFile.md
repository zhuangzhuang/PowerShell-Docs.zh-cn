---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3ef54618e065a5fca3d52415897b3042d6ba4c65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597897"
---
# <span data-ttu-id="a5cf5-102">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="a5cf5-102">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="a5cf5-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a5cf5-103">SYNOPSIS</span></span>
<span data-ttu-id="a5cf5-104">创建一个文件，该文件定义要通过会话配置公开的一组功能。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-104">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="a5cf5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a5cf5-105">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="a5cf5-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a5cf5-106">DESCRIPTION</span></span>

<span data-ttu-id="a5cf5-107">`New-PSRoleCapabilityFile`Cmdlet 将创建一个文件，该文件定义可通过会话配置文件公开的一组用户功能。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-107">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="a5cf5-108">这包括确定用户可以使用哪些 cmdlet、函数和脚本。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-108">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="a5cf5-109">此功能文件是一个可读的文本文件，其中包含会话配置属性和值的哈希表。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-109">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="a5cf5-110">该文件的文件扩展名为 .psrc，可供多个会话配置使用。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-110">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="a5cf5-111">`New-PSRoleCapabilityFile`除 **Path** 参数外，所有参数都是可选的，它指定文件的文件路径。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-111">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="a5cf5-112">如果在运行 cmdlet 时不包括参数，则将注释掉会话配置文件中的相应密钥，但参数说明中注明的情况除外。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-112">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="a5cf5-113">例如，如果不包括 **AssembliesToLoad** 参数，则将注释掉会话配置文件的那一部分。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-113">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="a5cf5-114">若要在会话配置中使用角色功能文件，请首先将该文件放在有效 PowerShell 模块文件夹的 **RoleCapabilities** 子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-114">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="a5cf5-115">然后，在 PowerShell 会话 ( 配置的 **RoleDefinitions** 字段中按名称引用该文件) 文件。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-115">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="a5cf5-116">此 cmdlet 是在 Windows PowerShell 5.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-116">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="a5cf5-117">示例</span><span class="sxs-lookup"><span data-stu-id="a5cf5-117">EXAMPLES</span></span>

### <span data-ttu-id="a5cf5-118">示例1：创建空白角色功能文件</span><span class="sxs-lookup"><span data-stu-id="a5cf5-118">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="a5cf5-119">此示例将创建一个新的角色功能文件，该文件使用默认 (空白) 值。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-119">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="a5cf5-120">稍后可以在文本编辑器中编辑该文件以更改这些配置设置。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-120">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="a5cf5-121">示例2：创建角色功能文件，使用户能够重启服务和任何 VDI 计算机</span><span class="sxs-lookup"><span data-stu-id="a5cf5-121">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="a5cf5-122">此示例将创建一个示例角色功能文件，使用户能够重新启动与特定名称模式匹配的服务和计算机。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-122">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="a5cf5-123">通过将 **ValidatePattern** 参数设置为正则表达式来定义名称筛选 `VDI\d+` 。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-123">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="a5cf5-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a5cf5-124">PARAMETERS</span></span>

### <span data-ttu-id="a5cf5-125">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="a5cf5-125">-AliasDefinitions</span></span>

<span data-ttu-id="a5cf5-126">将指定的别名添加到使用角色功能文件的会话。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-126">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-127">输入一个包含以下键的哈希表：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-127">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="a5cf5-128">名称：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-128">Name.</span></span> <span data-ttu-id="a5cf5-129">别名的名称。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-129">Name of the alias.</span></span> <span data-ttu-id="a5cf5-130">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-130">This key is required.</span></span>
- <span data-ttu-id="a5cf5-131">Value。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-131">Value.</span></span> <span data-ttu-id="a5cf5-132">别名所表示的命令。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-132">The command that the alias represents.</span></span> <span data-ttu-id="a5cf5-133">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-133">This key is required.</span></span>
- <span data-ttu-id="a5cf5-134">说明。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-134">Description.</span></span> <span data-ttu-id="a5cf5-135">描述别名的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-135">A text string that describes the alias.</span></span> <span data-ttu-id="a5cf5-136">此键是可选的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-136">This key is optional.</span></span>
- <span data-ttu-id="a5cf5-137">选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-137">Options.</span></span> <span data-ttu-id="a5cf5-138">别名选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-138">Alias options.</span></span> <span data-ttu-id="a5cf5-139">此键是可选的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-139">This key is optional.</span></span> <span data-ttu-id="a5cf5-140">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-140">The default value is None.</span></span> <span data-ttu-id="a5cf5-141">此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-141">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="a5cf5-142">例如： `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="a5cf5-142">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-143">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="a5cf5-143">-AssembliesToLoad</span></span>

<span data-ttu-id="a5cf5-144">指定要加载到使用角色功能文件的会话中的程序集。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-144">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-145">-作者</span><span class="sxs-lookup"><span data-stu-id="a5cf5-145">-Author</span></span>

<span data-ttu-id="a5cf5-146">指定创建角色功能文件的用户。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-146">Specifies the user that created the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-147">-公司名称</span><span class="sxs-lookup"><span data-stu-id="a5cf5-147">-CompanyName</span></span>

<span data-ttu-id="a5cf5-148">标识创建了角色功能文件的公司。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-148">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="a5cf5-149">默认值是“未知”。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-149">The default value is Unknown.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-150">-版权所有</span><span class="sxs-lookup"><span data-stu-id="a5cf5-150">-Copyright</span></span>

<span data-ttu-id="a5cf5-151">指定角色功能文件的版权。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-151">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="a5cf5-152">如果省略此参数，则 `New-PSRoleCapabilityFile` 使用 **Author** 参数的值生成版权声明。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-152">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-153">-Description</span><span class="sxs-lookup"><span data-stu-id="a5cf5-153">-Description</span></span>

<span data-ttu-id="a5cf5-154">指定角色功能文件的描述。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-154">Specifies a description for the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-155">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="a5cf5-155">-EnvironmentVariables</span></span>

<span data-ttu-id="a5cf5-156">指定公开此角色功能文件的会话的环境变量。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-156">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="a5cf5-157">输入一个哈希表，其中的键是环境变量名称，而值是环境变量值。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-157">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="a5cf5-158">例如： `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="a5cf5-158">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-159">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="a5cf5-159">-FormatsToProcess</span></span>

<span data-ttu-id="a5cf5-160">指定格式化文件 ( 在使用角色功能文件的会话中运行的 types.ps1xml) 。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-160">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-161">此参数的值必须是格式设置文件的完整或绝对路径。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-161">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-162">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="a5cf5-162">-FunctionDefinitions</span></span>

<span data-ttu-id="a5cf5-163">向公开角色功能的会话添加指定的函数。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-163">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="a5cf5-164">输入一个包含以下键的哈希表：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-164">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="a5cf5-165">名称：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-165">Name.</span></span> <span data-ttu-id="a5cf5-166">函数的名称。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-166">Name of the function.</span></span> <span data-ttu-id="a5cf5-167">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-167">This key is required.</span></span>
- <span data-ttu-id="a5cf5-168">ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="a5cf5-168">ScriptBlock.</span></span> <span data-ttu-id="a5cf5-169">函数体。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-169">Function body.</span></span> <span data-ttu-id="a5cf5-170">输入一个脚本块。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-170">Enter a script block.</span></span> <span data-ttu-id="a5cf5-171">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-171">This key is required.</span></span>
- <span data-ttu-id="a5cf5-172">选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-172">Options.</span></span> <span data-ttu-id="a5cf5-173">函数选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-173">Function options.</span></span> <span data-ttu-id="a5cf5-174">此键是可选的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-174">This key is optional.</span></span> <span data-ttu-id="a5cf5-175">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-175">The default value is None.</span></span> <span data-ttu-id="a5cf5-176">此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-176">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="a5cf5-177">例如：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-177">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-178">-Guid</span><span class="sxs-lookup"><span data-stu-id="a5cf5-178">-Guid</span></span>

<span data-ttu-id="a5cf5-179">指定角色功能文件的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-179">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="a5cf5-180">如果省略此参数，则 `New-PSRoleCapabilityFile` 将为文件生成 GUID。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-180">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="a5cf5-181">若要在 PowerShell 中创建新的 GUID，请键入 `[guid]::NewGuid()` 。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-181">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-182">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="a5cf5-182">-ModulesToImport</span></span>

<span data-ttu-id="a5cf5-183">指定自动导入到使用角色功能文件的会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-183">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-184">默认情况下，列出的模块中的所有命令均可见。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-184">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="a5cf5-185">与 **VisibleCmdlets** 或 **VisibleFunctions** 一起使用时，可以限制从指定模块中查看的命令。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-185">When used with **VisibleCmdlets** or **VisibleFunctions**, the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="a5cf5-186">此参数的值中使用的每个模块都可以通过字符串或哈希表来表示。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-186">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="a5cf5-187">模块字符串只包含模块的名称。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-187">A module string consists only of the name of the module.</span></span> <span data-ttu-id="a5cf5-188">模块哈希表可以包含 **ModuleName**、 **ModuleVersion** 和 **GUID** 键。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-188">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="a5cf5-189">仅 **ModuleName** 键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-189">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="a5cf5-190">例如，下面的值由字符串和哈希表组成。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-190">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="a5cf5-191">字符串和哈希表的任何组合（采用任何顺序）都是有效的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-191">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-192">-Path</span><span class="sxs-lookup"><span data-stu-id="a5cf5-192">-Path</span></span>

<span data-ttu-id="a5cf5-193">指定角色功能文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-193">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="a5cf5-194">文件必须具有文件 `.psrc` 扩展名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-194">The file must have a `.psrc` filename extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-195">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="a5cf5-195">-ScriptsToProcess</span></span>

<span data-ttu-id="a5cf5-196">指定要添加到使用角色功能文件的会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-196">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-197">请输入脚本的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-197">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="a5cf5-198">此参数的值必须为脚本文件名的完整或绝对路径。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-198">The value of this parameter must be a full or absolute path of the script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-199">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="a5cf5-199">-TypesToProcess</span></span>

<span data-ttu-id="a5cf5-200">指定要添加到使用角色功能文件的会话 () 的类型文件 types.ps1xml。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-200">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-201">输入类型文件名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-201">Enter the type filenames.</span></span> <span data-ttu-id="a5cf5-202">此参数的值必须为类型文件名的完整或绝对路径。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-202">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-203">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="a5cf5-203">-VariableDefinitions</span></span>

<span data-ttu-id="a5cf5-204">指定要添加到使用角色功能文件的会话中的变量。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-204">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="a5cf5-205">输入一个包含以下键的哈希表：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-205">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="a5cf5-206">名称：</span><span class="sxs-lookup"><span data-stu-id="a5cf5-206">Name.</span></span> <span data-ttu-id="a5cf5-207">变量的名称。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-207">Name of the variable.</span></span> <span data-ttu-id="a5cf5-208">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-208">This key is required.</span></span>
- <span data-ttu-id="a5cf5-209">Value。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-209">Value.</span></span> <span data-ttu-id="a5cf5-210">变量值。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-210">Variable value.</span></span> <span data-ttu-id="a5cf5-211">此键是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-211">This key is required.</span></span>
- <span data-ttu-id="a5cf5-212">选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-212">Options.</span></span> <span data-ttu-id="a5cf5-213">变量选项。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-213">Variable options.</span></span> <span data-ttu-id="a5cf5-214">此键是可选的。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-214">This key is optional.</span></span> <span data-ttu-id="a5cf5-215">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-215">The default value is None.</span></span> <span data-ttu-id="a5cf5-216">此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-216">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="a5cf5-217">例如： `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="a5cf5-217">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-218">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="a5cf5-218">-VisibleAliases</span></span>

<span data-ttu-id="a5cf5-219">将会话中的别名限制为在此参数的值中指定的别名，以及在 **AliasDefinition** 参数中定义的所有别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-219">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="a5cf5-220">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-220">Wildcard characters are supported.</span></span>
<span data-ttu-id="a5cf5-221">默认情况下，PowerShell 引擎定义的所有别名和模块导出的所有别名都在会话中可见。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-221">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="a5cf5-222">例如，若要将可用别名限制为 gm 和 gcm，请使用以下语法： `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="a5cf5-222">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="a5cf5-223">当角色功能文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-223">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="a5cf5-224">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="a5cf5-224">-VisibleCmdlets</span></span>

<span data-ttu-id="a5cf5-225">将会话中的 cmdlet 限制为在此参数的值中指定的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-225">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="a5cf5-226">支持通配符和模块限定名称。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-226">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="a5cf5-227">默认情况下，会话中的模块导出的所有 cmdlet 都在该会话中可见。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-227">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="a5cf5-228">使用 **SessionType** 和 **ModulesToImport** 参数来确定哪些模块和管理单元已导入到会话中。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-228">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="a5cf5-229">如果 **ModulesToImport** 中的任何模块都不公开 cmdlet，则会 `New-PSRoleCapabilityFile` 尝试加载相应的模块。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-229">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="a5cf5-230">当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-230">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a5cf5-231">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="a5cf5-231">-VisibleExternalCommands</span></span>

<span data-ttu-id="a5cf5-232">将可以在会话中执行的外部二进制文件、脚本和命令限制为在此参数的值中指定的文件。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-232">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="a5cf5-233">默认情况下，在此会话中不会显示任何外部命令。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-233">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="a5cf5-234">当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-234">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5cf5-235">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="a5cf5-235">-VisibleFunctions</span></span>

<span data-ttu-id="a5cf5-236">将会话中的函数限制为在此参数的值中指定的函数，以及在 **FunctionDefinitions** 参数中定义的任何函数。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-236">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="a5cf5-237">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-237">Wildcard characters are supported.</span></span>

<span data-ttu-id="a5cf5-238">默认情况下，会话中的模块导出的所有函数都在该会话中可见。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-238">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="a5cf5-239">使用 **SessionType** 和 **ModulesToImport** 参数确定导入到会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-239">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="a5cf5-240">当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-240">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a5cf5-241">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="a5cf5-241">-VisibleProviders</span></span>

<span data-ttu-id="a5cf5-242">将会话中的 PowerShell 提供程序限制为在此参数的值中指定的提供程序。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-242">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="a5cf5-243">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-243">Wildcard characters are supported.</span></span>

<span data-ttu-id="a5cf5-244">默认情况下，会话中的模块导出的所有提供程序都在该会话中可见。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-244">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="a5cf5-245">使用 **SessionType** 和 **ModulesToImport** 参数确定导入到会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-245">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="a5cf5-246">当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-246">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="a5cf5-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a5cf5-247">CommonParameters</span></span>

<span data-ttu-id="a5cf5-248">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a5cf5-249">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a5cf5-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a5cf5-250">输入</span><span class="sxs-lookup"><span data-stu-id="a5cf5-250">INPUTS</span></span>

## <span data-ttu-id="a5cf5-251">输出</span><span class="sxs-lookup"><span data-stu-id="a5cf5-251">OUTPUTS</span></span>

## <span data-ttu-id="a5cf5-252">注释</span><span class="sxs-lookup"><span data-stu-id="a5cf5-252">NOTES</span></span>

## <span data-ttu-id="a5cf5-253">相关链接</span><span class="sxs-lookup"><span data-stu-id="a5cf5-253">RELATED LINKS</span></span>

[<span data-ttu-id="a5cf5-254">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a5cf5-254">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="a5cf5-255">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="a5cf5-255">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)

