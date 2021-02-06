---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 683329aac35744697d80e22efff5ec53bae74830
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603411"
---
# <span data-ttu-id="fb50d-102">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fb50d-102">Install-PackageProvider</span></span>

## <span data-ttu-id="fb50d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fb50d-103">SYNOPSIS</span></span>
<span data-ttu-id="fb50d-104">安装一个或多个包管理包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-104">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="fb50d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb50d-105">SYNTAX</span></span>

### <span data-ttu-id="fb50d-106">PackageBySearch（默认值）</span><span class="sxs-lookup"><span data-stu-id="fb50d-106">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="fb50d-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="fb50d-107">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="fb50d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fb50d-108">DESCRIPTION</span></span>

<span data-ttu-id="fb50d-109">`Install-PackageProvider`Cmdlet 安装在使用 **PowerShellGet** 注册的包源中可用的匹配包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-109">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="fb50d-110">默认情况下，这包括 Windows PowerShell 库中使用 **PackageManagement** 标记的可用模块。</span><span class="sxs-lookup"><span data-stu-id="fb50d-110">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="fb50d-111">**PowerShellGet** 包管理提供程序用于查找这些存储库中的提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-111">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="fb50d-112">此 cmdlet 还会安装可使用包管理引导应用程序进行匹配包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-112">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="fb50d-113">此 cmdlet 还会安装包管理 Azure Blob 存储中提供的匹配包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-113">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="fb50d-114">使用引导程序提供程序查找并安装它们。</span><span class="sxs-lookup"><span data-stu-id="fb50d-114">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="fb50d-115">为了首次执行，PackageManagement 需要 internet 连接才能下载 NuGet 包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-115">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="fb50d-116">但是，如果您的计算机没有 internet 连接并且您需要使用 NuGet 或 PowerShellGet 提供程序，则可以将其下载到其他计算机上，然后将它们复制到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="fb50d-116">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="fb50d-117">使用以下步骤来执行此操作：</span><span class="sxs-lookup"><span data-stu-id="fb50d-117">Use the following steps to do this:</span></span>

1. <span data-ttu-id="fb50d-118">运行 `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` 从具有 internet 连接的计算机上安装提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-118">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="fb50d-119">安装后，可以在或中找到安装的提供 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` 程序 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` 。</span><span class="sxs-lookup"><span data-stu-id="fb50d-119">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="fb50d-120">将 `<ProviderName>` 该文件夹（在本例中为 NuGet 文件夹）放置在目标计算机上的相应位置。</span><span class="sxs-lookup"><span data-stu-id="fb50d-120">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="fb50d-121">如果目标计算机是 Nano server，则需要 `Install-PackageProvider` 从 Nano server 运行以下载正确的 NuGet 二进制文件。</span><span class="sxs-lookup"><span data-stu-id="fb50d-121">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="fb50d-122">重新启动 PowerShell 以自动加载包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-122">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="fb50d-123">或者，运行 `Get-PackageProvider -ListAvailable` 以列出计算机上可用的所有包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-123">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="fb50d-124">然后，使用 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 将提供程序导入到当前的 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="fb50d-124">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="fb50d-125">示例</span><span class="sxs-lookup"><span data-stu-id="fb50d-125">EXAMPLES</span></span>

### <span data-ttu-id="fb50d-126">示例1：从 PowerShell 库安装包提供程序</span><span class="sxs-lookup"><span data-stu-id="fb50d-126">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="fb50d-127">此命令从 PowerShell 库安装 GistProvider 包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-127">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="fb50d-128">示例2：安装包提供程序的指定版本</span><span class="sxs-lookup"><span data-stu-id="fb50d-128">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="fb50d-129">此示例将安装 NuGet 包提供程序的指定版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-129">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="fb50d-130">第一个命令将查找名为 NuGet 的包提供程序的所有版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-130">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="fb50d-131">第二个命令安装 NuGet 包提供程序的指定版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-131">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="fb50d-132">示例3：查找提供程序并安装它</span><span class="sxs-lookup"><span data-stu-id="fb50d-132">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="fb50d-133">此示例使用 `Find-PackageProvider` 和管道搜索 Gist 提供程序并安装它。</span><span class="sxs-lookup"><span data-stu-id="fb50d-133">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="fb50d-134">示例4：将提供程序安装到当前用户的模块文件夹</span><span class="sxs-lookup"><span data-stu-id="fb50d-134">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="fb50d-135">此命令将包提供程序安装到， `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` 以便只有当前用户可以使用它。</span><span class="sxs-lookup"><span data-stu-id="fb50d-135">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="fb50d-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb50d-136">PARAMETERS</span></span>

### <span data-ttu-id="fb50d-137">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="fb50d-137">-AllVersions</span></span>

<span data-ttu-id="fb50d-138">指示此 cmdlet 安装包提供程序的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-138">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="fb50d-139">默认情况下， `Install-PackageProvider` 仅返回可用的最高版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-139">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="fb50d-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="fb50d-140">-Credential</span></span>

<span data-ttu-id="fb50d-141">指定有权安装包提供程序的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fb50d-141">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-142">-Force</span><span class="sxs-lookup"><span data-stu-id="fb50d-142">-Force</span></span>

<span data-ttu-id="fb50d-143">指示此 cmdlet 强制执行可强制执行的与此 cmdlet 的所有操作。</span><span class="sxs-lookup"><span data-stu-id="fb50d-143">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="fb50d-144">目前，这意味着 **Force** 参数的作用与 **ForceBootstrap** 参数相同。</span><span class="sxs-lookup"><span data-stu-id="fb50d-144">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="fb50d-145">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="fb50d-145">-ForceBootstrap</span></span>

<span data-ttu-id="fb50d-146">指示此 cmdlet 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-146">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="fb50d-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fb50d-147">-InputObject</span></span>

<span data-ttu-id="fb50d-148">指定 **softwareidentity.revisionnumber** 对象。</span><span class="sxs-lookup"><span data-stu-id="fb50d-148">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="fb50d-149">使用 `Find-PackageProvider` cmdlet 获取要通过管道传入的 **softwareidentity.revisionnumber** 对象 `Install-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="fb50d-149">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-150">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fb50d-150">-MaximumVersion</span></span>

<span data-ttu-id="fb50d-151">指定要安装的包提供程序的最大允许版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-151">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="fb50d-152">如果不添加此参数，则 `Install-PackageProvider` 安装提供程序的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-152">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-153">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fb50d-153">-MinimumVersion</span></span>

<span data-ttu-id="fb50d-154">指定要安装的包提供程序的最小允许版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-154">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="fb50d-155">如果未添加此参数，将 `Install-PackageProvider` 安装包的最高可用版本，同时满足 *MaximumVersion* 参数指定的任何要求。</span><span class="sxs-lookup"><span data-stu-id="fb50d-155">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-156">-Name</span><span class="sxs-lookup"><span data-stu-id="fb50d-156">-Name</span></span>

<span data-ttu-id="fb50d-157">指定一个或多个包提供程序模块名称。</span><span class="sxs-lookup"><span data-stu-id="fb50d-157">Specifies one or more package provider module names.</span></span> <span data-ttu-id="fb50d-158">用逗号分隔多个包名称。</span><span class="sxs-lookup"><span data-stu-id="fb50d-158">Separate multiple package names with commas.</span></span>
<span data-ttu-id="fb50d-159">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="fb50d-159">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="fb50d-160">-Proxy</span></span>

<span data-ttu-id="fb50d-161">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="fb50d-161">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="fb50d-162">-ProxyCredential</span></span>

<span data-ttu-id="fb50d-163">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fb50d-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="fb50d-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fb50d-164">-RequiredVersion</span></span>

<span data-ttu-id="fb50d-165">指定要安装的包提供程序的确切允许版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-165">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="fb50d-166">如果不添加此参数，将 `Install-PackageProvider` 安装提供程序的最高可用版本，该版本还满足 **MaximumVersion** 参数指定的任何最高版本。</span><span class="sxs-lookup"><span data-stu-id="fb50d-166">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-167">-Scope</span><span class="sxs-lookup"><span data-stu-id="fb50d-167">-Scope</span></span>

<span data-ttu-id="fb50d-168">指定提供程序的安装范围。</span><span class="sxs-lookup"><span data-stu-id="fb50d-168">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="fb50d-169">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="fb50d-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fb50d-170">**AllUsers** -在计算机的所有用户都可以访问的位置中安装提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-170">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="fb50d-171">默认情况下，这是 **$env:P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="fb50d-171">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="fb50d-172">**CurrentUser** -在只能由当前用户访问的位置上安装提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb50d-172">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="fb50d-173">默认情况下，这是 **$env： LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="fb50d-173">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-174">-Source</span><span class="sxs-lookup"><span data-stu-id="fb50d-174">-Source</span></span>

<span data-ttu-id="fb50d-175">指定一个或多个包源。</span><span class="sxs-lookup"><span data-stu-id="fb50d-175">Specifies one or more package sources.</span></span> <span data-ttu-id="fb50d-176">使用 `Get-PackageSource` cmdlet 获取可用包源的列表。</span><span class="sxs-lookup"><span data-stu-id="fb50d-176">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb50d-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fb50d-177">-Confirm</span></span>

<span data-ttu-id="fb50d-178">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="fb50d-178">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fb50d-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fb50d-179">-WhatIf</span></span>

<span data-ttu-id="fb50d-180">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="fb50d-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fb50d-181">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fb50d-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fb50d-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb50d-182">CommonParameters</span></span>

<span data-ttu-id="fb50d-183">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fb50d-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb50d-184">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fb50d-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb50d-185">输入</span><span class="sxs-lookup"><span data-stu-id="fb50d-185">INPUTS</span></span>

### <span data-ttu-id="fb50d-186">Softwareidentity.revisionnumber。</span><span class="sxs-lookup"><span data-stu-id="fb50d-186">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="fb50d-187">可以通过管道将 **softwareidentity.revisionnumber** 对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fb50d-187">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="fb50d-188">用于 `Find-PackageProvider` 获取可通过管道传递到的 **softwareidentity.revisionnumber** 对象 `Install-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="fb50d-188">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="fb50d-189">输出</span><span class="sxs-lookup"><span data-stu-id="fb50d-189">OUTPUTS</span></span>

## <span data-ttu-id="fb50d-190">注释</span><span class="sxs-lookup"><span data-stu-id="fb50d-190">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb50d-191">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="fb50d-191">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="fb50d-192">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="fb50d-192">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="fb50d-193">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="fb50d-193">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="fb50d-194">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="fb50d-194">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="fb50d-195">相关链接</span><span class="sxs-lookup"><span data-stu-id="fb50d-195">RELATED LINKS</span></span>

[<span data-ttu-id="fb50d-196">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fb50d-196">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="fb50d-197">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fb50d-197">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="fb50d-198">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fb50d-198">Import-PackageProvider</span></span>](Import-PackageProvider.md)
