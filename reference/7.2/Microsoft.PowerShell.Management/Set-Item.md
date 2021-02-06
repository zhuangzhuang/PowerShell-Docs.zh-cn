---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c617f4554c8e61ed6cf54b0faf0cd7d79be84595
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596430"
---
# <span data-ttu-id="7fac4-102">Set-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-102">Set-Item</span></span>

## <span data-ttu-id="7fac4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="7fac4-103">SYNOPSIS</span></span>
<span data-ttu-id="7fac4-104">将项的值更改为命令中指定的值。</span><span class="sxs-lookup"><span data-stu-id="7fac4-104">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="7fac4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7fac4-105">SYNTAX</span></span>

### <span data-ttu-id="7fac4-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="7fac4-106">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fac4-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7fac4-107">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7fac4-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7fac4-108">DESCRIPTION</span></span>

<span data-ttu-id="7fac4-109">`Set-Item`Cmdlet 将项的值（如变量或注册表项）更改为命令中指定的值。</span><span class="sxs-lookup"><span data-stu-id="7fac4-109">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="7fac4-110">示例</span><span class="sxs-lookup"><span data-stu-id="7fac4-110">EXAMPLES</span></span>

### <span data-ttu-id="7fac4-111">示例1：创建别名</span><span class="sxs-lookup"><span data-stu-id="7fac4-111">Example 1: Create an alias</span></span>

<span data-ttu-id="7fac4-112">此命令为 Notepad 创建一个别名。</span><span class="sxs-lookup"><span data-stu-id="7fac4-112">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="7fac4-113">示例2：更改环境变量的值</span><span class="sxs-lookup"><span data-stu-id="7fac4-113">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="7fac4-114">此命令将 UserRole 环境变量的值更改为 Administrator。</span><span class="sxs-lookup"><span data-stu-id="7fac4-114">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="7fac4-115">示例3：修改提示函数</span><span class="sxs-lookup"><span data-stu-id="7fac4-115">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="7fac4-116">此命令更改 prompt 函数，使其显示路径前面的时间。</span><span class="sxs-lookup"><span data-stu-id="7fac4-116">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="7fac4-117">示例4：设置提示函数的选项</span><span class="sxs-lookup"><span data-stu-id="7fac4-117">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="7fac4-118">此命令为 prompt 函数设置 **AllScope** 和 **ReadOnly** 选项。</span><span class="sxs-lookup"><span data-stu-id="7fac4-118">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="7fac4-119">此命令使用的 **Options** 动态参数 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="7fac4-119">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="7fac4-120">**Options** 参数 `Set-Item` 仅在与 **Alias** 或 **Function** 提供程序一起使用时才可用。</span><span class="sxs-lookup"><span data-stu-id="7fac4-120">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="7fac4-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fac4-121">PARAMETERS</span></span>

### <span data-ttu-id="7fac4-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="7fac4-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7fac4-123">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="7fac4-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="7fac4-124">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac4-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7fac4-125">-Exclude</span><span class="sxs-lookup"><span data-stu-id="7fac4-125">-Exclude</span></span>

<span data-ttu-id="7fac4-126">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="7fac4-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="7fac4-127">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="7fac4-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7fac4-128">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="7fac4-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7fac4-129">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7fac4-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="7fac4-130">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="7fac4-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7fac4-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="7fac4-131">-Filter</span></span>

<span data-ttu-id="7fac4-132">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="7fac4-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="7fac4-133">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="7fac4-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="7fac4-134">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="7fac4-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="7fac4-135">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="7fac4-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="7fac4-136">-Force</span><span class="sxs-lookup"><span data-stu-id="7fac4-136">-Force</span></span>

<span data-ttu-id="7fac4-137">强制 cmdlet 设置无法以其他方式更改的项，如只读别名或变量。</span><span class="sxs-lookup"><span data-stu-id="7fac4-137">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="7fac4-138">该 cmdlet 不能更改常量别名或变量。</span><span class="sxs-lookup"><span data-stu-id="7fac4-138">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="7fac4-139">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="7fac4-139">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="7fac4-140">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac4-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="7fac4-141">即使使用 *Force* 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="7fac4-141">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="7fac4-142">-Include</span><span class="sxs-lookup"><span data-stu-id="7fac4-142">-Include</span></span>

<span data-ttu-id="7fac4-143">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="7fac4-143">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="7fac4-144">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="7fac4-144">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7fac4-145">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="7fac4-145">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="7fac4-146">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7fac4-146">Wildcard characters are permitted.</span></span> <span data-ttu-id="7fac4-147">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="7fac4-147">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7fac4-148">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7fac4-148">-LiteralPath</span></span>

<span data-ttu-id="7fac4-149">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="7fac4-149">Specifies a path to one or more locations.</span></span> <span data-ttu-id="7fac4-150">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="7fac4-150">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7fac4-151">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="7fac4-151">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7fac4-152">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="7fac4-152">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7fac4-153">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="7fac4-153">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="7fac4-154">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac4-154">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="7fac4-155">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7fac4-155">-PassThru</span></span>

<span data-ttu-id="7fac4-156">将表示项的对象传递到管道。</span><span class="sxs-lookup"><span data-stu-id="7fac4-156">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="7fac4-157">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="7fac4-157">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7fac4-158">-Path</span><span class="sxs-lookup"><span data-stu-id="7fac4-158">-Path</span></span>

<span data-ttu-id="7fac4-159">指定项位置的路径。</span><span class="sxs-lookup"><span data-stu-id="7fac4-159">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="7fac4-160">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7fac4-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7fac4-161">-Value</span><span class="sxs-lookup"><span data-stu-id="7fac4-161">-Value</span></span>

<span data-ttu-id="7fac4-162">为项指定新值。</span><span class="sxs-lookup"><span data-stu-id="7fac4-162">Specifies a new value for the item.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7fac4-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7fac4-163">-Confirm</span></span>

<span data-ttu-id="7fac4-164">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="7fac4-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7fac4-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7fac4-165">-WhatIf</span></span>

<span data-ttu-id="7fac4-166">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="7fac4-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7fac4-167">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="7fac4-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7fac4-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fac4-168">CommonParameters</span></span>

<span data-ttu-id="7fac4-169">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="7fac4-169">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7fac4-170">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac4-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7fac4-171">输入</span><span class="sxs-lookup"><span data-stu-id="7fac4-171">INPUTS</span></span>

### <span data-ttu-id="7fac4-172">System.Object</span><span class="sxs-lookup"><span data-stu-id="7fac4-172">System.Object</span></span>

<span data-ttu-id="7fac4-173">可以通过管道将表示项的新值的对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7fac4-173">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="7fac4-174">输出</span><span class="sxs-lookup"><span data-stu-id="7fac4-174">OUTPUTS</span></span>

### <span data-ttu-id="7fac4-175">无或表示新的或更改项的对象。</span><span class="sxs-lookup"><span data-stu-id="7fac4-175">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="7fac4-176">如果指定 *PassThru* 参数，则此 cmdlet 将生成一个表示该项的对象。</span><span class="sxs-lookup"><span data-stu-id="7fac4-176">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="7fac4-177">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="7fac4-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7fac4-178">注释</span><span class="sxs-lookup"><span data-stu-id="7fac4-178">NOTES</span></span>

- <span data-ttu-id="7fac4-179">`Set-Item` PowerShell FileSystem 提供程序不支持。</span><span class="sxs-lookup"><span data-stu-id="7fac4-179">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="7fac4-180">若要更改文件系统中的项的值，请使用 `Set-Content` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7fac4-180">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="7fac4-181">在注册表驱动器和中 `HKLM:` ， `HKCU:` `Set-Item` 更改注册表项 (默认) 值中的数据。</span><span class="sxs-lookup"><span data-stu-id="7fac4-181">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="7fac4-182">若要创建和更改注册表项的名称，请使用 `New-Item` 和 `Rename-Item` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7fac4-182">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="7fac4-183">若要更改注册表值中的名称和数据，请使用 `New-ItemProperty` 、 `Set-ItemProperty` 和 `Rename-ItemProperty` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7fac4-183">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="7fac4-184">`Set-Item` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="7fac4-184">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="7fac4-185">若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="7fac4-185">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="7fac4-186">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac4-186">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7fac4-187">相关链接</span><span class="sxs-lookup"><span data-stu-id="7fac4-187">RELATED LINKS</span></span>

[<span data-ttu-id="7fac4-188">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-188">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="7fac4-189">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-189">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="7fac4-190">Get-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-190">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="7fac4-191">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-191">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="7fac4-192">Move-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-192">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="7fac4-193">New-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-193">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="7fac4-194">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-194">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="7fac4-195">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="7fac4-195">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="7fac4-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7fac4-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

