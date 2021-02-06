---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 0df911ad8b1f7b4516eef4a1c2b0180893013e3e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596442"
---
# <span data-ttu-id="dd222-102">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="dd222-102">Uninstall-Module</span></span>

## <span data-ttu-id="dd222-103">摘要</span><span class="sxs-lookup"><span data-stu-id="dd222-103">SYNOPSIS</span></span>
<span data-ttu-id="dd222-104">卸载模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-104">Uninstalls a module.</span></span>

## <span data-ttu-id="dd222-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd222-105">SYNTAX</span></span>

### <span data-ttu-id="dd222-106">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="dd222-106">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="dd222-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="dd222-107">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dd222-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dd222-108">DESCRIPTION</span></span>

<span data-ttu-id="dd222-109">`Uninstall-Module`Cmdlet 从本地计算机中卸载指定的模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-109">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="dd222-110">如果模块有其他模块作为依赖项，则无法卸载该模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-110">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="dd222-111">示例</span><span class="sxs-lookup"><span data-stu-id="dd222-111">EXAMPLES</span></span>

### <span data-ttu-id="dd222-112">示例1：卸载模块</span><span class="sxs-lookup"><span data-stu-id="dd222-112">Example 1: Uninstall a module</span></span>

<span data-ttu-id="dd222-113">此示例将卸载模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-113">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="dd222-114">`Uninstall-Module` 使用 **Name** 参数指定要从本地计算机中卸载的模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-114">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="dd222-115">示例2：使用管道卸载模块</span><span class="sxs-lookup"><span data-stu-id="dd222-115">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="dd222-116">在此示例中，管道用于卸载模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-116">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="dd222-117">`Get-InstalledModule` 使用 **Name** 参数指定模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-117">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="dd222-118">对象沿管道向下发送到 `Uninstall-Module` 并被卸载。</span><span class="sxs-lookup"><span data-stu-id="dd222-118">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="dd222-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd222-119">PARAMETERS</span></span>

### <span data-ttu-id="dd222-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="dd222-120">-AllowPrerelease</span></span>

<span data-ttu-id="dd222-121">允许卸载标记为预发行的模块。</span><span class="sxs-lookup"><span data-stu-id="dd222-121">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="dd222-122">-AllVersions</span></span>

<span data-ttu-id="dd222-123">指定您要包含某个模块的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="dd222-123">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="dd222-124">不能将 **AllVersions** 参数与 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="dd222-124">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dd222-125">-Confirm</span></span>

<span data-ttu-id="dd222-126">提示你在运行之前进行确认 `Uninstall-Module` 。</span><span class="sxs-lookup"><span data-stu-id="dd222-126">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="dd222-127">-Force</span><span class="sxs-lookup"><span data-stu-id="dd222-127">-Force</span></span>

<span data-ttu-id="dd222-128">强制 `Uninstall-Module` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="dd222-128">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="dd222-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dd222-129">-InputObject</span></span>

<span data-ttu-id="dd222-130">接受 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="dd222-130">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="dd222-131">例如，输出 `Get-InstalledModule` 到变量，并将该变量用作 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="dd222-131">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-132">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="dd222-132">-MaximumVersion</span></span>

<span data-ttu-id="dd222-133">指定要卸载的模块的最高或最新版本。</span><span class="sxs-lookup"><span data-stu-id="dd222-133">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="dd222-134">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="dd222-134">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-135">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="dd222-135">-MinimumVersion</span></span>

<span data-ttu-id="dd222-136">指定要卸载的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="dd222-136">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="dd222-137">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="dd222-137">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-138">-Name</span><span class="sxs-lookup"><span data-stu-id="dd222-138">-Name</span></span>

<span data-ttu-id="dd222-139">指定要卸载的模块名称的数组。</span><span class="sxs-lookup"><span data-stu-id="dd222-139">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-140">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="dd222-140">-RequiredVersion</span></span>

<span data-ttu-id="dd222-141">指定要卸载的模块的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="dd222-141">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dd222-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dd222-142">-WhatIf</span></span>

<span data-ttu-id="dd222-143">显示运行时将发生 `Uninstall-Module` 的情况。</span><span class="sxs-lookup"><span data-stu-id="dd222-143">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="dd222-144">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="dd222-144">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="dd222-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd222-145">CommonParameters</span></span>

<span data-ttu-id="dd222-146">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dd222-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd222-147">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dd222-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd222-148">输入</span><span class="sxs-lookup"><span data-stu-id="dd222-148">INPUTS</span></span>

### <span data-ttu-id="dd222-149">System.String[]</span><span class="sxs-lookup"><span data-stu-id="dd222-149">System.String[]</span></span>

### <span data-ttu-id="dd222-150">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="dd222-150">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="dd222-151">System.String</span><span class="sxs-lookup"><span data-stu-id="dd222-151">System.String</span></span>

## <span data-ttu-id="dd222-152">输出</span><span class="sxs-lookup"><span data-stu-id="dd222-152">OUTPUTS</span></span>

### <span data-ttu-id="dd222-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="dd222-153">System.Object</span></span>

## <span data-ttu-id="dd222-154">注释</span><span class="sxs-lookup"><span data-stu-id="dd222-154">NOTES</span></span>

## <span data-ttu-id="dd222-155">相关链接</span><span class="sxs-lookup"><span data-stu-id="dd222-155">RELATED LINKS</span></span>

[<span data-ttu-id="dd222-156">Find-Module</span><span class="sxs-lookup"><span data-stu-id="dd222-156">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="dd222-157">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="dd222-157">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="dd222-158">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="dd222-158">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="dd222-159">Save-Module</span><span class="sxs-lookup"><span data-stu-id="dd222-159">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="dd222-160">Update-Module</span><span class="sxs-lookup"><span data-stu-id="dd222-160">Update-Module</span></span>](Update-Module.md)

