---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598674"
---
# <span data-ttu-id="1e6fb-102">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1e6fb-102">Unregister-PackageSource</span></span>

## <span data-ttu-id="1e6fb-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1e6fb-103">SYNOPSIS</span></span>
<span data-ttu-id="1e6fb-104">删除已注册的包源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-104">Removes a registered package source.</span></span>

## <span data-ttu-id="1e6fb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e6fb-105">SYNTAX</span></span>

### <span data-ttu-id="1e6fb-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="1e6fb-106">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="1e6fb-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="1e6fb-107">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1e6fb-108">NuGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="1e6fb-108">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="1e6fb-109">NuGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="1e6fb-109">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="1e6fb-110">PowerShellGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="1e6fb-110">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="1e6fb-111">PowerShellGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="1e6fb-111">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="1e6fb-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1e6fb-112">DESCRIPTION</span></span>

<span data-ttu-id="1e6fb-113">`Unregister-PackageSource`Cmdlet 将删除已注册的包源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-113">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="1e6fb-114">包源始终由包提供程序进行管理。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-114">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="1e6fb-115">若要查找包源，请使用 `Get-PackageSource` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-115">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="1e6fb-116">示例</span><span class="sxs-lookup"><span data-stu-id="1e6fb-116">EXAMPLES</span></span>

### <span data-ttu-id="1e6fb-117">示例1：为 Nuget 提供程序取消注册包源</span><span class="sxs-lookup"><span data-stu-id="1e6fb-117">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="1e6fb-118">`Unregister-PackageSource`Cmdlet 将从本地计算机中注销包源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-118">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="1e6fb-119">**Location** 和 **Provider** 参数可用于进一步指定要删除的源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-119">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="1e6fb-120">`Unregister-PackageSource`Cmdlet 使用 **source** 参数指定要删除的源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-120">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="1e6fb-121">示例2：使用 Register-packagesource 对象取消注册包</span><span class="sxs-lookup"><span data-stu-id="1e6fb-121">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="1e6fb-122">此示例使用 `Get-PackageSource` 和 `Unregister-PackageSource` 取消注册包源。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-122">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="1e6fb-123">**Register-packagesource** 对象存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-123">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="1e6fb-124">`$pkgsource`变量存储由 cmdlet 创建的 **register-packagesource** `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-124">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="1e6fb-125">`Unregister-PackageSource` 使用 `$pkgsource` 作为 **InputObject** 参数的输入。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-125">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="1e6fb-126">作为替代方法，该 `Unregister-PackageSource` cmdlet 可以为 **InputObject** 参数指定值：</span><span class="sxs-lookup"><span data-stu-id="1e6fb-126">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="1e6fb-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e6fb-127">PARAMETERS</span></span>

### <span data-ttu-id="1e6fb-128">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="1e6fb-128">-ConfigFile</span></span>

<span data-ttu-id="1e6fb-129">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-129">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="1e6fb-130">-Credential</span></span>

<span data-ttu-id="1e6fb-131">指定有权访问计算机并运行命令的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-131">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="1e6fb-132">键入用户名，如 **User01**、 **Domain01\User01** 或输入由 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-132">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1e6fb-133">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-133">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="1e6fb-134">如果未指定 **Credential** 参数，将使用当前用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-134">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-135">-Force</span><span class="sxs-lookup"><span data-stu-id="1e6fb-135">-Force</span></span>

<span data-ttu-id="1e6fb-136">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-136">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="1e6fb-137">覆盖阻止成功的限制 `Unregister-PackageSource` ，但安全性除外。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-137">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="1e6fb-138">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="1e6fb-138">-ForceBootstrap</span></span>

<span data-ttu-id="1e6fb-139">指示 `Unregister-PackageSource` 强制 **PackageManagement** 为指定的包源自动卸载包提供程序。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-139">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="1e6fb-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1e6fb-140">-InputObject</span></span>

<span data-ttu-id="1e6fb-141">接受从 cmdlet 指定 **register-packagesource** 对象的管道输入 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-141">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="1e6fb-142">**InputObject** 接受 **register-packagesource** 对象作为 `Get-PackageSource` 值或包含该对象的变量。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-142">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-143">-Location</span><span class="sxs-lookup"><span data-stu-id="1e6fb-143">-Location</span></span>

<span data-ttu-id="1e6fb-144">指定包源指向的位置。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-144">Specifies the location to which a package source points.</span></span> <span data-ttu-id="1e6fb-145">此参数的值可以是 URI、文件路径或包提供程序支持的任何其他目标格式。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-145">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-146">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1e6fb-146">-PackageManagementProvider</span></span>

<span data-ttu-id="1e6fb-147">指定 **PackageManagement** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-147">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-148">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="1e6fb-148">-ProviderName</span></span>

<span data-ttu-id="1e6fb-149">指定提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-149">Specifies the provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1e6fb-150">-PublishLocation</span></span>

<span data-ttu-id="1e6fb-151">指定发布位置。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="1e6fb-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="1e6fb-153">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1e6fb-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="1e6fb-155">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="1e6fb-156">-SkipValidate</span></span>

<span data-ttu-id="1e6fb-157">跳过验证包源凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-158">-Source</span><span class="sxs-lookup"><span data-stu-id="1e6fb-158">-Source</span></span>

<span data-ttu-id="1e6fb-159">指定包源的友好名称。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-159">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e6fb-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1e6fb-160">-Confirm</span></span>

<span data-ttu-id="1e6fb-161">在运行之前提示你进行确认 `Unregister-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-161">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="1e6fb-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1e6fb-162">-WhatIf</span></span>

<span data-ttu-id="1e6fb-163">显示在 `Unregister-PackageSource` 运行 cmdlet 时会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-163">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="1e6fb-164">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-164">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1e6fb-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e6fb-165">CommonParameters</span></span>

<span data-ttu-id="1e6fb-166">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e6fb-167">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e6fb-168">输入</span><span class="sxs-lookup"><span data-stu-id="1e6fb-168">INPUTS</span></span>

### <span data-ttu-id="1e6fb-169">`Unregister-PackageSource` 接受管道中的 **register-packagesource** 对象作为输入。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-169">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="1e6fb-170">输出</span><span class="sxs-lookup"><span data-stu-id="1e6fb-170">OUTPUTS</span></span>

### <span data-ttu-id="1e6fb-171">`Unregister-PackageSource` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-171">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="1e6fb-172">注释</span><span class="sxs-lookup"><span data-stu-id="1e6fb-172">NOTES</span></span>

<span data-ttu-id="1e6fb-173">在命令中包含包提供程序可以使动态参数可用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-173">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="1e6fb-174">动态参数特定于包提供程序。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-174">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="1e6fb-175">`Get-Help`Cmdlet 列出 cmdlet 的参数集，并包括提供程序的参数集。</span><span class="sxs-lookup"><span data-stu-id="1e6fb-175">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="1e6fb-176">相关链接</span><span class="sxs-lookup"><span data-stu-id="1e6fb-176">RELATED LINKS</span></span>

[<span data-ttu-id="1e6fb-177">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1e6fb-177">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="1e6fb-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1e6fb-178">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="1e6fb-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1e6fb-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="1e6fb-180">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1e6fb-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="1e6fb-181">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1e6fb-181">Set-PackageSource</span></span>](Set-PackageSource.md)

