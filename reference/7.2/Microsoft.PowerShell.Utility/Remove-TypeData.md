---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 8ede1375faa1287b70eeb49689ec7fe1bb800d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603601"
---
# <span data-ttu-id="a186b-102">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="a186b-102">Remove-TypeData</span></span>

## <span data-ttu-id="a186b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a186b-103">Synopsis</span></span>
<span data-ttu-id="a186b-104">从当前会话中删除扩展的类型。</span><span class="sxs-lookup"><span data-stu-id="a186b-104">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="a186b-105">语法</span><span class="sxs-lookup"><span data-stu-id="a186b-105">Syntax</span></span>

### <span data-ttu-id="a186b-106">RemoveTypeDataSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="a186b-106">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a186b-107">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="a186b-107">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a186b-108">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="a186b-108">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a186b-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a186b-109">DESCRIPTION</span></span>

<span data-ttu-id="a186b-110">`Remove-TypeData`Cmdlet 从当前会话中删除扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-110">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="a186b-111">此 cmdlet 只影响当前会话和当前会话中创建的会话。</span><span class="sxs-lookup"><span data-stu-id="a186b-111">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="a186b-112">可以通过在命令和文件中定义来向 PowerShell 中的对象添加属性和方法 `Update-TypeData` `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-112">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="a186b-113">`Remove-TypeData` 从当前会话中删除这些扩展属性和方法。</span><span class="sxs-lookup"><span data-stu-id="a186b-113">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="a186b-114">`Remove-TypeData` 不会删除 `Types.ps1xml` 文件或从文件中删除任何扩展类型定义 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-114">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="a186b-115">有关文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a186b-115">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="a186b-116">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a186b-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a186b-117">示例</span><span class="sxs-lookup"><span data-stu-id="a186b-117">Examples</span></span>

### <span data-ttu-id="a186b-118">示例 1：删除指定类型的类型数据</span><span class="sxs-lookup"><span data-stu-id="a186b-118">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="a186b-119">此示例将从会话中删除 **system.object** 类型的所有类型数据，包括通过 `Types.ps1xml` 使用 cmdlet 添加到会话中的文件和动态类型数据添加的类型数据 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-119">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="a186b-120">示例 2：从会话中删除扩展数据类型</span><span class="sxs-lookup"><span data-stu-id="a186b-120">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="a186b-121">此示例演示了从会话中删除扩展类型数据的效果。</span><span class="sxs-lookup"><span data-stu-id="a186b-121">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="a186b-122">第一 `Get-TypeData` 种是为 system.string 类型获取扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-122">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="a186b-123">输出显示已将 **datetime** 属性添加到 PowerShell 中的所有 **system.web** 对象。</span><span class="sxs-lookup"><span data-stu-id="a186b-123">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="a186b-124">`Get-Date`Cmdlet 将返回 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="a186b-124">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="a186b-125">该命令使用点表示法来获取返回的 **system.object** 对象的 **datetime** 属性的值 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-125">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="a186b-126">下一个 `Get-TypeData` cmdlet，用于获取 **system.web** 类型的所有扩展类型数据，并通过管道将其用于 `Remove-TypeData` 删除扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-126">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="a186b-127">最后一个 `Get-Date` cmdlet 显示删除 **system.object** 类型的扩展类型数据的效果。</span><span class="sxs-lookup"><span data-stu-id="a186b-127">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="a186b-128">由于不存在 **system.web** 属性，因此用于获取其值的命令不会返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="a186b-128">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="a186b-129">示例 3：删除模块的扩展类型</span><span class="sxs-lookup"><span data-stu-id="a186b-129">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="a186b-130">此示例将删除模块对象的所有扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-130">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="a186b-131">将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取该对象类型的名称，并删除该类型的所有对象的所有类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-131">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="a186b-132">示例 4：删除指定模块中的扩展类型</span><span class="sxs-lookup"><span data-stu-id="a186b-132">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="a186b-133">此示例使用 cmdlet 的 **Path** 参数 `Remove-TypeData` 删除 `Types.ps1xml` **PSScheduledJob** 和 **PSWorkflow** 模块添加的文件中定义的扩展类型。</span><span class="sxs-lookup"><span data-stu-id="a186b-133">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="a186b-134">此命令不会影响使用 cmdlet 添加的动态类型数据 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-134">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="a186b-135">仅当已将模块导入当前会话时，此命令才能够成功执行。</span><span class="sxs-lookup"><span data-stu-id="a186b-135">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="a186b-136">有关模块的详细信息，请参阅 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="a186b-136">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="a186b-137">示例 5：从远程会话中删除扩展类型</span><span class="sxs-lookup"><span data-stu-id="a186b-137">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="a186b-138">此示例将从远程会话中删除扩展类型。</span><span class="sxs-lookup"><span data-stu-id="a186b-138">This example removes extended types from a remote session.</span></span> <span data-ttu-id="a186b-139">该命令使用 `Invoke-Command` cmdlet 删除变量的会话中的所有 CIM 类型的扩展类型数据 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-139">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="a186b-140">参数</span><span class="sxs-lookup"><span data-stu-id="a186b-140">Parameters</span></span>

### <span data-ttu-id="a186b-141">-Path</span><span class="sxs-lookup"><span data-stu-id="a186b-141">-Path</span></span>

<span data-ttu-id="a186b-142">指定此 cmdlet 将从会话扩展类型数据中删除的文件数组。</span><span class="sxs-lookup"><span data-stu-id="a186b-142">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="a186b-143">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="a186b-143">This parameter is required.</span></span>

<span data-ttu-id="a186b-144">输入一个或多个文件的路径和文件名 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-144">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="a186b-145">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="a186b-145">Wildcards are not supported.</span></span> <span data-ttu-id="a186b-146">如果省略路径，则默认位置为当前目录。</span><span class="sxs-lookup"><span data-stu-id="a186b-146">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a186b-147">-TypeData</span><span class="sxs-lookup"><span data-stu-id="a186b-147">-TypeData</span></span>

<span data-ttu-id="a186b-148">指定此 cmdlet 将从会话中删除的类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-148">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="a186b-149">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="a186b-149">This parameter is required.</span></span> <span data-ttu-id="a186b-150">输入包含 **update-typedata** 对象的变量， (**update-typedata**) 或获取 **update-typedata** 对象的命令（如命令）。 `Get-TypeData`</span><span class="sxs-lookup"><span data-stu-id="a186b-150">Enter a variable that contains **TypeData** objects (**System.Management.Automation.Runspaces.TypeData**) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="a186b-151">还可以通过管道将 **update-typedata** 对象传递给 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-151">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a186b-152">-TypeName</span><span class="sxs-lookup"><span data-stu-id="a186b-152">-TypeName</span></span>

<span data-ttu-id="a186b-153">指定此 cmdlet 将删除其所有扩展类型数据的类型。</span><span class="sxs-lookup"><span data-stu-id="a186b-153">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="a186b-154">对于 System 命名空间中的类型，请输入其短名称。</span><span class="sxs-lookup"><span data-stu-id="a186b-154">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="a186b-155">否则，必须输入完整类型名称。</span><span class="sxs-lookup"><span data-stu-id="a186b-155">Otherwise, the full type name is required.</span></span> <span data-ttu-id="a186b-156">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="a186b-156">Wildcards are not supported.</span></span>

<span data-ttu-id="a186b-157">可以通过管道将类型命名为 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-157">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="a186b-158">将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取对象的类型名称，并移除该对象类型的所有类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-158">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a186b-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a186b-159">-Confirm</span></span>

<span data-ttu-id="a186b-160">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="a186b-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a186b-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a186b-161">-WhatIf</span></span>

<span data-ttu-id="a186b-162">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="a186b-162">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a186b-163">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="a186b-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a186b-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a186b-164">CommonParameters</span></span>

<span data-ttu-id="a186b-165">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a186b-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a186b-166">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a186b-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a186b-167">输入</span><span class="sxs-lookup"><span data-stu-id="a186b-167">Inputs</span></span>

### <span data-ttu-id="a186b-168">System.Management.Automation.Runspaces.TypeData</span><span class="sxs-lookup"><span data-stu-id="a186b-168">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="a186b-169">可以通过管道将 **update-typedata** 对象（例如 cmdlet 返回的对象）传递 `Get-TypeData` 给 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-169">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="a186b-170">System.String</span><span class="sxs-lookup"><span data-stu-id="a186b-170">System.String</span></span>

<span data-ttu-id="a186b-171">可以通过管道将类型名称传递给 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="a186b-171">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="a186b-172">将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取对象的类型名称，并移除该对象类型的所有类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-172">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="a186b-173">输出</span><span class="sxs-lookup"><span data-stu-id="a186b-173">Outputs</span></span>

### <span data-ttu-id="a186b-174">无</span><span class="sxs-lookup"><span data-stu-id="a186b-174">None</span></span>

<span data-ttu-id="a186b-175">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="a186b-175">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a186b-176">说明</span><span class="sxs-lookup"><span data-stu-id="a186b-176">Notes</span></span>

<span data-ttu-id="a186b-177">`Remove-TypeData` 只能删除当前会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-177">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="a186b-178">它无法删除位于计算机上的但未添加到当前会话的扩展类型数据，例如模块中定义的但未导入到当前会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="a186b-178">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="a186b-179">相关链接</span><span class="sxs-lookup"><span data-stu-id="a186b-179">Related links</span></span>

[<span data-ttu-id="a186b-180">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="a186b-180">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="a186b-181">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="a186b-181">Update-TypeData</span></span>](Update-TypeData.md)

