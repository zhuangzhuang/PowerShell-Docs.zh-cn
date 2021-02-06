---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595838"
---
# <span data-ttu-id="46b6c-102">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="46b6c-102">Remove-Module</span></span>

## <span data-ttu-id="46b6c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="46b6c-103">SYNOPSIS</span></span>
<span data-ttu-id="46b6c-104">删除当前会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-104">Removes modules from the current session.</span></span>

## <span data-ttu-id="46b6c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46b6c-105">SYNTAX</span></span>

### <span data-ttu-id="46b6c-106">name</span><span class="sxs-lookup"><span data-stu-id="46b6c-106">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46b6c-107">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="46b6c-107">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46b6c-108">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="46b6c-108">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="46b6c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="46b6c-109">DESCRIPTION</span></span>

<span data-ttu-id="46b6c-110">**Remove-Module** cmdlet 将从当前会话中删除模块的成员，如 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="46b6c-110">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="46b6c-111">如果模块包含某个程序集 (.dll)，则将删除由该程序集实现的所有成员，但不会卸载该程序集。</span><span class="sxs-lookup"><span data-stu-id="46b6c-111">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="46b6c-112">此 cmdlet 不会将该模块从计算机中卸载或删除。</span><span class="sxs-lookup"><span data-stu-id="46b6c-112">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="46b6c-113">它仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="46b6c-113">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="46b6c-114">示例</span><span class="sxs-lookup"><span data-stu-id="46b6c-114">EXAMPLES</span></span>

### <span data-ttu-id="46b6c-115">示例 1：删除模块</span><span class="sxs-lookup"><span data-stu-id="46b6c-115">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="46b6c-116">此命令将从当前会话中删除 BitsTransfer 模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-116">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="46b6c-117">示例 2：删除所有模块</span><span class="sxs-lookup"><span data-stu-id="46b6c-117">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="46b6c-118">此命令将从当前会话中删除所有模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-118">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="46b6c-119">示例 3：通过使用管道删除模块</span><span class="sxs-lookup"><span data-stu-id="46b6c-119">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="46b6c-120">此命令将从当前会话中删除 BitsTransfer 和 PSDiagnostics 模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-120">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="46b6c-121">该命令使用管道运算符 (|) 将模块名称发送到 **Remove-Module**。</span><span class="sxs-lookup"><span data-stu-id="46b6c-121">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="46b6c-122">它使用 *Verbose* 通用参数来获取有关要删除的成员的详细信息。</span><span class="sxs-lookup"><span data-stu-id="46b6c-122">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="46b6c-123">Verbose 消息显示所删除的项。</span><span class="sxs-lookup"><span data-stu-id="46b6c-123">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="46b6c-124">这些消息会有所不同，因为 BitsTransfer 模块包含一个实现其 cmdlet 的程序集，以及一个拥有自己的程序集的嵌套模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-124">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="46b6c-125">PSDiagnostics 模块包含用于导出函数的模块脚本文件 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="46b6c-125">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="46b6c-126">示例 4：通过使用 ModuleInfo 删除模块</span><span class="sxs-lookup"><span data-stu-id="46b6c-126">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="46b6c-127">此命令使用 ModuleInfo 参数删除 BitsTransfer 模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-127">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="46b6c-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46b6c-128">PARAMETERS</span></span>

### <span data-ttu-id="46b6c-129">-Force</span><span class="sxs-lookup"><span data-stu-id="46b6c-129">-Force</span></span>

<span data-ttu-id="46b6c-130">指示此 cmdlet 将删除只读模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-130">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="46b6c-131">默认情况下，**Remove-Module** 只删除读写模块。</span><span class="sxs-lookup"><span data-stu-id="46b6c-131">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="46b6c-132">**ReadOnly** 和 **ReadWrite** 值存储在模块的 **AccessMode** 属性中。</span><span class="sxs-lookup"><span data-stu-id="46b6c-132">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="46b6c-133">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="46b6c-133">-FullyQualifiedName</span></span>

<span data-ttu-id="46b6c-134">指定要删除的模块的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="46b6c-134">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46b6c-135">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="46b6c-135">-ModuleInfo</span></span>

<span data-ttu-id="46b6c-136">指定要删除的模块对象。</span><span class="sxs-lookup"><span data-stu-id="46b6c-136">Specifies the module objects to remove.</span></span>
<span data-ttu-id="46b6c-137">输入包含模块对象 (**PSModuleInfo**) 的变量，或输入可获取模块对象的命令，如 Get-Module 命令。</span><span class="sxs-lookup"><span data-stu-id="46b6c-137">Enter a variable that contains a module object (**PSModuleInfo**) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="46b6c-138">你还可以通过管道将模块对象传递给 **Remove-Module**。</span><span class="sxs-lookup"><span data-stu-id="46b6c-138">You can also pipe module objects to **Remove-Module**.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46b6c-139">-Name</span><span class="sxs-lookup"><span data-stu-id="46b6c-139">-Name</span></span>

<span data-ttu-id="46b6c-140">指定要删除的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="46b6c-140">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="46b6c-141">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="46b6c-141">Wildcard characters are permitted.</span></span>
<span data-ttu-id="46b6c-142">还可以通过管道将名称字符串传递给 **Remove-Module**。</span><span class="sxs-lookup"><span data-stu-id="46b6c-142">You can also pipe name strings to **Remove-Module**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="46b6c-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46b6c-143">-Confirm</span></span>

<span data-ttu-id="46b6c-144">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="46b6c-144">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46b6c-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46b6c-145">-WhatIf</span></span>

<span data-ttu-id="46b6c-146">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="46b6c-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="46b6c-147">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="46b6c-147">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46b6c-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46b6c-148">CommonParameters</span></span>

<span data-ttu-id="46b6c-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="46b6c-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46b6c-150">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="46b6c-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46b6c-151">输入</span><span class="sxs-lookup"><span data-stu-id="46b6c-151">INPUTS</span></span>

### <span data-ttu-id="46b6c-152">System.String, System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="46b6c-152">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="46b6c-153">可以通过管道将模块名称和模块对象传递给 **Remove-Module**。</span><span class="sxs-lookup"><span data-stu-id="46b6c-153">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="46b6c-154">输出</span><span class="sxs-lookup"><span data-stu-id="46b6c-154">OUTPUTS</span></span>

### <span data-ttu-id="46b6c-155">无</span><span class="sxs-lookup"><span data-stu-id="46b6c-155">None</span></span>

<span data-ttu-id="46b6c-156">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="46b6c-156">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="46b6c-157">注释</span><span class="sxs-lookup"><span data-stu-id="46b6c-157">NOTES</span></span>

<span data-ttu-id="46b6c-158">删除模块时，将执行的模块上有一个事件。</span><span class="sxs-lookup"><span data-stu-id="46b6c-158">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="46b6c-159">此事件允许模块响应被删除并执行一些清理，如释放资源。</span><span class="sxs-lookup"><span data-stu-id="46b6c-159">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="46b6c-160">例如：</span><span class="sxs-lookup"><span data-stu-id="46b6c-160">Example:</span></span>

<span data-ttu-id="46b6c-161">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="46b6c-161">$OnRemoveScript = {</span></span>

  <span data-ttu-id="46b6c-162">\# 执行清理</span><span class="sxs-lookup"><span data-stu-id="46b6c-162">\# perform cleanup</span></span>

  <span data-ttu-id="46b6c-163">$cachedSessions |Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="46b6c-163">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="46b6c-164">}</span><span class="sxs-lookup"><span data-stu-id="46b6c-164">}</span></span>

<span data-ttu-id="46b6c-165">SessionState. OnRemove + = $OnRemoveScript $ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="46b6c-165">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="46b6c-166">为了完全保持一致性，响应 PowerShell 进程的关闭可能也很有用：</span><span class="sxs-lookup"><span data-stu-id="46b6c-166">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="46b6c-167">Register-EngineEvent ( [PsEngineEvent]：：正在退出) -操作 $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="46b6c-167">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="46b6c-168">相关链接</span><span class="sxs-lookup"><span data-stu-id="46b6c-168">RELATED LINKS</span></span>

[<span data-ttu-id="46b6c-169">Get-Module</span><span class="sxs-lookup"><span data-stu-id="46b6c-169">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="46b6c-170">Import-Module</span><span class="sxs-lookup"><span data-stu-id="46b6c-170">Import-Module</span></span>](Import-Module.md)

