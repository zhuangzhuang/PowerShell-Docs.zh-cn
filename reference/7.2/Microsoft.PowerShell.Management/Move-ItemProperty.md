---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 92a14e4bd165efd4721e3802cade827744c9c056
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596649"
---
# <span data-ttu-id="1545a-102">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-102">Move-ItemProperty</span></span>

## <span data-ttu-id="1545a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1545a-103">Synopsis</span></span>
<span data-ttu-id="1545a-104">将属性从一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="1545a-104">Moves a property from one location to another.</span></span>

## <span data-ttu-id="1545a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1545a-105">SYNTAX</span></span>

### <span data-ttu-id="1545a-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="1545a-106">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1545a-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1545a-107">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1545a-108">说明</span><span class="sxs-lookup"><span data-stu-id="1545a-108">Description</span></span>

<span data-ttu-id="1545a-109">`Move-ItemProperty`Cmdlet 将项的属性从一个项移动到另一个项。</span><span class="sxs-lookup"><span data-stu-id="1545a-109">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="1545a-110">例如，它可以将注册表条目从一个注册表项移到另一个注册表项。</span><span class="sxs-lookup"><span data-stu-id="1545a-110">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="1545a-111">在你移动某个项属性时，该属性将被添加到新位置，并从其原来的位置删除。</span><span class="sxs-lookup"><span data-stu-id="1545a-111">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="1545a-112">示例</span><span class="sxs-lookup"><span data-stu-id="1545a-112">EXAMPLES</span></span>

### <span data-ttu-id="1545a-113">示例1：将注册表值及其数据移动到另一个键</span><span class="sxs-lookup"><span data-stu-id="1545a-113">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="1545a-114">此命令将版本注册表值及其数据从 "MyApp" 子项移动到注册表项的 Newapp.siteconfig.numberofworkers 子项 `HKLM\Software\MyCompany` 。</span><span class="sxs-lookup"><span data-stu-id="1545a-114">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="1545a-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1545a-115">PARAMETERS</span></span>

### <span data-ttu-id="1545a-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="1545a-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1545a-117">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="1545a-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="1545a-118">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="1545a-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1545a-119">-Destination</span><span class="sxs-lookup"><span data-stu-id="1545a-119">-Destination</span></span>

<span data-ttu-id="1545a-120">指定目标位置的路径。</span><span class="sxs-lookup"><span data-stu-id="1545a-120">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="1545a-121">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1545a-121">-Exclude</span></span>

<span data-ttu-id="1545a-122">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="1545a-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="1545a-123">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1545a-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1545a-124">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="1545a-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1545a-125">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1545a-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="1545a-126">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="1545a-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1545a-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="1545a-127">-Filter</span></span>

<span data-ttu-id="1545a-128">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="1545a-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="1545a-129">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1545a-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="1545a-130">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="1545a-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="1545a-131">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1545a-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="1545a-132">-Force</span><span class="sxs-lookup"><span data-stu-id="1545a-132">-Force</span></span>

<span data-ttu-id="1545a-133">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="1545a-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="1545a-134">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="1545a-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="1545a-135">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1545a-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="1545a-136">-Include</span><span class="sxs-lookup"><span data-stu-id="1545a-136">-Include</span></span>

<span data-ttu-id="1545a-137">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="1545a-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1545a-138">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1545a-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1545a-139">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="1545a-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="1545a-140">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1545a-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="1545a-141">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="1545a-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1545a-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1545a-142">-LiteralPath</span></span>

<span data-ttu-id="1545a-143">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="1545a-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1545a-144">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="1545a-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1545a-145">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="1545a-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1545a-146">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="1545a-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1545a-147">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="1545a-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1545a-148">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="1545a-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="1545a-149">-Name</span><span class="sxs-lookup"><span data-stu-id="1545a-149">-Name</span></span>

<span data-ttu-id="1545a-150">指定要移动的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1545a-150">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1545a-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1545a-151">-PassThru</span></span>

<span data-ttu-id="1545a-152">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="1545a-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="1545a-153">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="1545a-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1545a-154">-Path</span><span class="sxs-lookup"><span data-stu-id="1545a-154">-Path</span></span>

<span data-ttu-id="1545a-155">指定此属性的当前位置的路径。</span><span class="sxs-lookup"><span data-stu-id="1545a-155">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="1545a-156">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1545a-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1545a-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1545a-157">-Confirm</span></span>

<span data-ttu-id="1545a-158">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="1545a-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1545a-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1545a-159">-WhatIf</span></span>

<span data-ttu-id="1545a-160">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="1545a-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1545a-161">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1545a-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1545a-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1545a-162">CommonParameters</span></span>

<span data-ttu-id="1545a-163">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="1545a-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="1545a-164">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1545a-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1545a-165">输入</span><span class="sxs-lookup"><span data-stu-id="1545a-165">INPUTS</span></span>

### <span data-ttu-id="1545a-166">System.String</span><span class="sxs-lookup"><span data-stu-id="1545a-166">System.String</span></span>

<span data-ttu-id="1545a-167">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1545a-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="1545a-168">输出</span><span class="sxs-lookup"><span data-stu-id="1545a-168">OUTPUTS</span></span>

### <span data-ttu-id="1545a-169">无或 System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="1545a-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="1545a-170">当使用 **PassThru** 参数时，此 cmdlet 将生成一个表示已移动项属性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="1545a-170">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="1545a-171">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="1545a-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1545a-172">注释</span><span class="sxs-lookup"><span data-stu-id="1545a-172">NOTES</span></span>

<span data-ttu-id="1545a-173">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="1545a-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="1545a-174">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="1545a-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="1545a-175">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1545a-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1545a-176">相关链接</span><span class="sxs-lookup"><span data-stu-id="1545a-176">RELATED LINKS</span></span>

[<span data-ttu-id="1545a-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="1545a-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="1545a-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="1545a-180">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="1545a-181">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-181">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="1545a-182">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-182">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="1545a-183">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1545a-183">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="1545a-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1545a-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

