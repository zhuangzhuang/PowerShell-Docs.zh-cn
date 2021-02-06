---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: d6dd6d21d7c0022e8ca1ea7dbd8e1cab8a680de6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595401"
---
# <span data-ttu-id="fba22-102">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-102">Copy-ItemProperty</span></span>

## <span data-ttu-id="fba22-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fba22-103">SYNOPSIS</span></span>
<span data-ttu-id="fba22-104">将属性和值从指定的位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="fba22-104">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="fba22-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fba22-105">SYNTAX</span></span>

### <span data-ttu-id="fba22-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="fba22-106">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fba22-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fba22-107">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fba22-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fba22-108">DESCRIPTION</span></span>

<span data-ttu-id="fba22-109">`Copy-ItemProperty`Cmdlet 将属性和值从指定的位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="fba22-109">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="fba22-110">例如，可以使用此 cmdlet 将一个或多个注册表条目从一个注册表项复制到另一个注册表项。</span><span class="sxs-lookup"><span data-stu-id="fba22-110">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="fba22-111">示例</span><span class="sxs-lookup"><span data-stu-id="fba22-111">EXAMPLES</span></span>

### <span data-ttu-id="fba22-112">示例 1：将属性从一个注册表项复制到另一个注册表项</span><span class="sxs-lookup"><span data-stu-id="fba22-112">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="fba22-113">此命令会将名为 "T.myproperty" 的属性从 "MyApplication" 注册表项复制到 "MyApplicationRev2" 注册表项。</span><span class="sxs-lookup"><span data-stu-id="fba22-113">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="fba22-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fba22-114">PARAMETERS</span></span>

### <span data-ttu-id="fba22-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="fba22-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fba22-116">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="fba22-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fba22-117">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="fba22-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fba22-118">-Destination</span><span class="sxs-lookup"><span data-stu-id="fba22-118">-Destination</span></span>

<span data-ttu-id="fba22-119">指定目标位置的路径。</span><span class="sxs-lookup"><span data-stu-id="fba22-119">Specifies the path to the destination location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fba22-120">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fba22-120">-Exclude</span></span>

<span data-ttu-id="fba22-121">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="fba22-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fba22-122">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fba22-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fba22-123">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="fba22-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fba22-124">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fba22-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="fba22-125">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="fba22-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fba22-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="fba22-126">-Filter</span></span>

<span data-ttu-id="fba22-127">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="fba22-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fba22-128">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="fba22-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fba22-129">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="fba22-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fba22-130">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="fba22-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fba22-131">-Force</span><span class="sxs-lookup"><span data-stu-id="fba22-131">-Force</span></span>

<span data-ttu-id="fba22-132">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="fba22-132">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="fba22-133">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="fba22-133">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="fba22-134">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="fba22-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fba22-135">-Include</span><span class="sxs-lookup"><span data-stu-id="fba22-135">-Include</span></span>

<span data-ttu-id="fba22-136">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="fba22-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fba22-137">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fba22-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fba22-138">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="fba22-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fba22-139">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fba22-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="fba22-140">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="fba22-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fba22-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fba22-141">-LiteralPath</span></span>

<span data-ttu-id="fba22-142">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="fba22-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fba22-143">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="fba22-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="fba22-144">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="fba22-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fba22-145">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="fba22-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fba22-146">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="fba22-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fba22-147">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="fba22-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fba22-148">-Name</span><span class="sxs-lookup"><span data-stu-id="fba22-148">-Name</span></span>

<span data-ttu-id="fba22-149">指定要复制的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="fba22-149">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fba22-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fba22-150">-PassThru</span></span>

<span data-ttu-id="fba22-151">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="fba22-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="fba22-152">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="fba22-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fba22-153">-Path</span><span class="sxs-lookup"><span data-stu-id="fba22-153">-Path</span></span>

<span data-ttu-id="fba22-154">指定要复制的属性的路径（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="fba22-154">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="fba22-155">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fba22-155">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="fba22-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fba22-156">-Confirm</span></span>

<span data-ttu-id="fba22-157">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="fba22-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fba22-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fba22-158">-WhatIf</span></span>

<span data-ttu-id="fba22-159">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="fba22-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fba22-160">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fba22-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fba22-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fba22-161">CommonParameters</span></span>

<span data-ttu-id="fba22-162">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="fba22-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fba22-163">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fba22-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fba22-164">输入</span><span class="sxs-lookup"><span data-stu-id="fba22-164">INPUTS</span></span>

### <span data-ttu-id="fba22-165">System.String</span><span class="sxs-lookup"><span data-stu-id="fba22-165">System.String</span></span>

<span data-ttu-id="fba22-166">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fba22-166">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="fba22-167">输出</span><span class="sxs-lookup"><span data-stu-id="fba22-167">OUTPUTS</span></span>

### <span data-ttu-id="fba22-168">无或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fba22-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="fba22-169">如果使用 Passthru 参数，则此 cmdlet 生成一个 **PsCustomObject** 对象，该对象表示已复制的项属性。</span><span class="sxs-lookup"><span data-stu-id="fba22-169">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="fba22-170">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="fba22-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fba22-171">注释</span><span class="sxs-lookup"><span data-stu-id="fba22-171">NOTES</span></span>

<span data-ttu-id="fba22-172">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="fba22-172">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fba22-173">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="fba22-173">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fba22-174">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="fba22-174">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fba22-175">相关链接</span><span class="sxs-lookup"><span data-stu-id="fba22-175">RELATED LINKS</span></span>

[<span data-ttu-id="fba22-176">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-176">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="fba22-177">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-177">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="fba22-178">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-178">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="fba22-179">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-179">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="fba22-180">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-180">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="fba22-181">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fba22-181">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="fba22-182">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="fba22-182">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="fba22-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fba22-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

