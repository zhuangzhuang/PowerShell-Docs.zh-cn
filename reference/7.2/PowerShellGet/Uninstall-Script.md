---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596023"
---
# <span data-ttu-id="fdb27-102">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-102">Uninstall-Script</span></span>

## <span data-ttu-id="fdb27-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fdb27-103">SYNOPSIS</span></span>
<span data-ttu-id="fdb27-104">卸载脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-104">Uninstalls a script.</span></span>

## <span data-ttu-id="fdb27-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fdb27-105">SYNTAX</span></span>

### <span data-ttu-id="fdb27-106">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="fdb27-106">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fdb27-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="fdb27-107">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fdb27-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fdb27-108">DESCRIPTION</span></span>

<span data-ttu-id="fdb27-109">`Uninstall-Script`Cmdlet 从本地计算机中卸载指定的脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-109">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="fdb27-110">示例</span><span class="sxs-lookup"><span data-stu-id="fdb27-110">EXAMPLES</span></span>

### <span data-ttu-id="fdb27-111">示例1：卸载脚本</span><span class="sxs-lookup"><span data-stu-id="fdb27-111">Example 1: Uninstall a script</span></span>

<span data-ttu-id="fdb27-112">此示例将卸载脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-112">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="fdb27-113">`Uninstall-Script` 使用 **Name** 参数指定要从本地计算机中卸载的脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-113">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="fdb27-114">示例2：使用管道卸载脚本</span><span class="sxs-lookup"><span data-stu-id="fdb27-114">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="fdb27-115">在此示例中，管道用于卸载脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-115">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="fdb27-116">`Get-InstalledScript` 使用 **Name** 参数指定脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-116">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="fdb27-117">将对象向下发送到 `Uninstall-Script` ，并卸载脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-117">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="fdb27-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fdb27-118">PARAMETERS</span></span>

### <span data-ttu-id="fdb27-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="fdb27-119">-AllowPrerelease</span></span>

<span data-ttu-id="fdb27-120">允许卸载标记为预发行版的脚本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-120">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="fdb27-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fdb27-121">-Confirm</span></span>

<span data-ttu-id="fdb27-122">在运行之前提示你进行确认 `Uninstall-Script` 。</span><span class="sxs-lookup"><span data-stu-id="fdb27-122">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="fdb27-123">-Force</span><span class="sxs-lookup"><span data-stu-id="fdb27-123">-Force</span></span>

<span data-ttu-id="fdb27-124">强制 `Uninstall-Script` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="fdb27-124">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="fdb27-125">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fdb27-125">-InputObject</span></span>

<span data-ttu-id="fdb27-126">接受 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="fdb27-126">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="fdb27-127">例如，输出 `Get-InstalledScript` 到变量，并将该变量用作 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="fdb27-127">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="fdb27-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fdb27-128">-MaximumVersion</span></span>

<span data-ttu-id="fdb27-129">指定要卸载的脚本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-129">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="fdb27-130">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="fdb27-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="fdb27-131">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fdb27-131">-MinimumVersion</span></span>

<span data-ttu-id="fdb27-132">指定要卸载的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="fdb27-132">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="fdb27-133">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="fdb27-133">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="fdb27-134">-Name</span><span class="sxs-lookup"><span data-stu-id="fdb27-134">-Name</span></span>

<span data-ttu-id="fdb27-135">指定要卸载的脚本名称的数组。</span><span class="sxs-lookup"><span data-stu-id="fdb27-135">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="fdb27-136">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fdb27-136">-RequiredVersion</span></span>

<span data-ttu-id="fdb27-137">指定要卸载的脚本的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="fdb27-137">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="fdb27-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fdb27-138">-WhatIf</span></span>

<span data-ttu-id="fdb27-139">显示运行时将发生 `Uninstall-Script` 的情况。</span><span class="sxs-lookup"><span data-stu-id="fdb27-139">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="fdb27-140">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fdb27-140">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="fdb27-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fdb27-141">CommonParameters</span></span>

<span data-ttu-id="fdb27-142">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fdb27-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fdb27-143">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fdb27-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fdb27-144">输入</span><span class="sxs-lookup"><span data-stu-id="fdb27-144">INPUTS</span></span>

### <span data-ttu-id="fdb27-145">System.String[]</span><span class="sxs-lookup"><span data-stu-id="fdb27-145">System.String[]</span></span>

### <span data-ttu-id="fdb27-146">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="fdb27-146">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="fdb27-147">System.String</span><span class="sxs-lookup"><span data-stu-id="fdb27-147">System.String</span></span>

## <span data-ttu-id="fdb27-148">输出</span><span class="sxs-lookup"><span data-stu-id="fdb27-148">OUTPUTS</span></span>

### <span data-ttu-id="fdb27-149">System.Object</span><span class="sxs-lookup"><span data-stu-id="fdb27-149">System.Object</span></span>

## <span data-ttu-id="fdb27-150">注释</span><span class="sxs-lookup"><span data-stu-id="fdb27-150">NOTES</span></span>

## <span data-ttu-id="fdb27-151">相关链接</span><span class="sxs-lookup"><span data-stu-id="fdb27-151">RELATED LINKS</span></span>

[<span data-ttu-id="fdb27-152">Find-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-152">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="fdb27-153">Install-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-153">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="fdb27-154">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-154">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="fdb27-155">Save-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-155">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="fdb27-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="fdb27-156">Update-Script</span></span>](Update-Script.md)

