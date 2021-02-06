---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: f4fcf349c439baf4813c37af4bf56c26a46c7877
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596651"
---
# <span data-ttu-id="b5c03-102">Install-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-102">Install-Module</span></span>

## <span data-ttu-id="b5c03-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b5c03-103">SYNOPSIS</span></span>
<span data-ttu-id="b5c03-104">从存储库中下载一个或多个模块，并将其安装在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="b5c03-104">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="b5c03-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5c03-105">SYNTAX</span></span>

### <span data-ttu-id="b5c03-106">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="b5c03-106">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5c03-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="b5c03-107">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b5c03-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b5c03-108">DESCRIPTION</span></span>

<span data-ttu-id="b5c03-109">`Install-Module`Cmdlet 从联机存储库中获取一个或多个满足指定条件的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-109">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="b5c03-110">Cmdlet 验证搜索结果是否为有效的模块，并将模块文件夹复制到安装位置。</span><span class="sxs-lookup"><span data-stu-id="b5c03-110">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="b5c03-111">安装后，不会自动导入已安装的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-111">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="b5c03-112">您可以根据指定模块的最小、最大和确切版本来筛选安装的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-112">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="b5c03-113">如果正在安装的模块具有相同的名称或版本，或包含现有模块中的命令，则会显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="b5c03-113">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="b5c03-114">确认要安装该模块并覆盖警告后，请使用 `-Force` 和 `-AllowClobber` 参数。</span><span class="sxs-lookup"><span data-stu-id="b5c03-114">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="b5c03-115">取决于存储库设置，你可能需要回答提示以继续安装模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-115">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="b5c03-116">这些示例使用 [PowerShell 库](https://www.powershellgallery.com/) 作为仅已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="b5c03-116">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="b5c03-117">`Get-PSRepository` 显示已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="b5c03-117">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="b5c03-118">如果有多个已注册的存储库，请使用 `-Repository` 参数指定存储库的名称。</span><span class="sxs-lookup"><span data-stu-id="b5c03-118">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="b5c03-119">示例</span><span class="sxs-lookup"><span data-stu-id="b5c03-119">EXAMPLES</span></span>

### <span data-ttu-id="b5c03-120">示例1：查找和安装模块</span><span class="sxs-lookup"><span data-stu-id="b5c03-120">Example 1: Find and install a module</span></span>

<span data-ttu-id="b5c03-121">此示例查找存储库中的模块并安装该模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-121">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="b5c03-122">`Find-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-122">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b5c03-123">默认情况下，将从存储库下载模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-123">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="b5c03-124">对象通过管道向下发送到 `Install-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5c03-124">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="b5c03-125">`Install-Module` 为中的所有用户安装该模块 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-125">`Install-Module` installs the module for all users in `$env:ProgramFiles\PowerShell\Modules`.</span></span>

### <span data-ttu-id="b5c03-126">示例2：按名称安装模块</span><span class="sxs-lookup"><span data-stu-id="b5c03-126">Example 2: Install a module by name</span></span>

<span data-ttu-id="b5c03-127">在此示例中，将安装 **PowerShellGet** 模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-127">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="b5c03-128">`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-128">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b5c03-129">默认情况下，将从存储库下载并安装最新版本的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-129">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="b5c03-130">示例3：使用最低版本安装模块</span><span class="sxs-lookup"><span data-stu-id="b5c03-130">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="b5c03-131">在此示例中，将安装 **PowerShellGet** 模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-131">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="b5c03-132">**MinimumVersion** 参数指定应安装的模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-132">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="b5c03-133">如果模块的更新版本可用，则会为所有用户下载并安装该版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-133">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="b5c03-134">`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-134">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b5c03-135">**MinimumVersion** 参数指定从存储库下载并安装版本 **2.0.1** 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-135">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="b5c03-136">由于版本 **2.0.4** 可用，因此会为所有用户下载和安装该版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-136">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="b5c03-137">示例4：安装特定版本的模块</span><span class="sxs-lookup"><span data-stu-id="b5c03-137">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="b5c03-138">在此示例中，安装了 **PowerShellGet** 模块的特定版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-138">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="b5c03-139">`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-139">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b5c03-140">**RequiredVersion** 参数指定为所有用户下载和安装版本 **2.0.0** 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-140">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="b5c03-141">示例5：仅为当前用户安装模块</span><span class="sxs-lookup"><span data-stu-id="b5c03-141">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="b5c03-142">此示例仅为当前用户下载并安装最新版本的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-142">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="b5c03-143">`Install-Module`使用 **Name** 参数指定 **PowerShellGet** 模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-143">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="b5c03-144">`Install-Module` 下载最新版本的 **PowerShellGet** 并将其安装到当前用户的目录中 `$home\Documents\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-144">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\PowerShell\Modules`.</span></span>

## <span data-ttu-id="b5c03-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5c03-145">PARAMETERS</span></span>

### <span data-ttu-id="b5c03-146">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b5c03-146">-AcceptLicense</span></span>

<span data-ttu-id="b5c03-147">对于需要许可证的模块， **AcceptLicense** 会在安装过程中自动接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="b5c03-147">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="b5c03-148">有关详细信息，请参阅 [需要接受许可证的模块](/powershell/scripting/gallery/concepts/module-license-acceptance)。</span><span class="sxs-lookup"><span data-stu-id="b5c03-148">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="b5c03-149">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="b5c03-149">-AllowClobber</span></span>

<span data-ttu-id="b5c03-150">覆盖有关计算机上的现有命令的安装冲突的警告消息。</span><span class="sxs-lookup"><span data-stu-id="b5c03-150">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="b5c03-151">覆盖与模块安装的命令同名的现有命令。</span><span class="sxs-lookup"><span data-stu-id="b5c03-151">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="b5c03-152">在命令中，可以将 **AllowClobber** 和 **Force** 一起使用 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-152">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="b5c03-153">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b5c03-153">-AllowPrerelease</span></span>

<span data-ttu-id="b5c03-154">允许你安装标记为预发行版的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-154">Allows you to install a module marked as a pre-release.</span></span>

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

### <span data-ttu-id="b5c03-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b5c03-155">-Confirm</span></span>

<span data-ttu-id="b5c03-156">提示你在运行 cmdlet 之前进行确认 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-156">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="b5c03-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="b5c03-157">-Credential</span></span>

<span data-ttu-id="b5c03-158">指定有权为指定的包提供程序或源安装模块的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b5c03-158">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5c03-159">-Force</span><span class="sxs-lookup"><span data-stu-id="b5c03-159">-Force</span></span>

<span data-ttu-id="b5c03-160">安装模块并覆盖有关模块安装冲突的警告消息。</span><span class="sxs-lookup"><span data-stu-id="b5c03-160">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="b5c03-161">如果计算机上已存在具有相同名称的模块，则 **强制** 允许安装多个版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-161">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="b5c03-162">如果存在具有相同名称和版本的现有模块，则 **强制** 覆盖该版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-162">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="b5c03-163">在命令中，可以将 **Force** 和 **AllowClobber** 一起使用 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-163">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="b5c03-164">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b5c03-164">-InputObject</span></span>

<span data-ttu-id="b5c03-165">用于管道输入。</span><span class="sxs-lookup"><span data-stu-id="b5c03-165">Used for pipeline input.</span></span>

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

### <span data-ttu-id="b5c03-166">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b5c03-166">-MaximumVersion</span></span>

<span data-ttu-id="b5c03-167">指定要安装的单个模块的最高版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-167">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="b5c03-168">安装的版本必须小于或等于 **MaximumVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-168">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="b5c03-169">如果要安装多个模块，则不能使用 **MaximumVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-169">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="b5c03-170">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-170">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="b5c03-171">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b5c03-171">-MinimumVersion</span></span>

<span data-ttu-id="b5c03-172">指定要安装的单个模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-172">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="b5c03-173">安装的版本必须大于或等于 **MinimumVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-173">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="b5c03-174">如果模块的更新版本可用，则会安装较新版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-174">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="b5c03-175">如果要安装多个模块，则不能使用 **MinimumVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-175">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="b5c03-176">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-176">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="b5c03-177">-Name</span><span class="sxs-lookup"><span data-stu-id="b5c03-177">-Name</span></span>

<span data-ttu-id="b5c03-178">指定要从联机库中安装的模块的确切名称。</span><span class="sxs-lookup"><span data-stu-id="b5c03-178">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="b5c03-179">接受以逗号分隔的模块名称列表。</span><span class="sxs-lookup"><span data-stu-id="b5c03-179">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="b5c03-180">模块名称必须与存储库中的模块名称匹配。</span><span class="sxs-lookup"><span data-stu-id="b5c03-180">The module name must match the module name in the repository.</span></span> <span data-ttu-id="b5c03-181">使用 `Find-Module` 获取模块名称的列表。</span><span class="sxs-lookup"><span data-stu-id="b5c03-181">Use `Find-Module` to get a list of module names.</span></span>

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

### <span data-ttu-id="b5c03-182">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b5c03-182">-PassThru</span></span>

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

### <span data-ttu-id="b5c03-183">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b5c03-183">-Proxy</span></span>

<span data-ttu-id="b5c03-184">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="b5c03-184">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5c03-185">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b5c03-185">-ProxyCredential</span></span>

<span data-ttu-id="b5c03-186">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b5c03-186">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5c03-187">-Repository</span><span class="sxs-lookup"><span data-stu-id="b5c03-187">-Repository</span></span>

<span data-ttu-id="b5c03-188">使用 **存储库** 参数可指定用于下载和安装模块的存储库。</span><span class="sxs-lookup"><span data-stu-id="b5c03-188">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="b5c03-189">当注册多个存储库时使用。</span><span class="sxs-lookup"><span data-stu-id="b5c03-189">Used when multiple repositories are registered.</span></span> <span data-ttu-id="b5c03-190">在命令中指定已注册的存储库的名称 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-190">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="b5c03-191">若要注册存储库，请使用 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-191">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="b5c03-192">若要显示已注册的存储库，请使用 `Get-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-192">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5c03-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b5c03-193">-RequiredVersion</span></span>

<span data-ttu-id="b5c03-194">指定要安装的单个模块的确切版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-194">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="b5c03-195">如果指定版本的存储库中没有匹配项，则会显示错误。</span><span class="sxs-lookup"><span data-stu-id="b5c03-195">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="b5c03-196">如果要安装多个模块，则不能使用 **RequiredVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-196">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="b5c03-197">对于 `Install-Module` **MinimumVersion** 或 **MaximumVersion**，不能在同一命令中使用 RequiredVersion。</span><span class="sxs-lookup"><span data-stu-id="b5c03-197">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

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

### <span data-ttu-id="b5c03-198">-Scope</span><span class="sxs-lookup"><span data-stu-id="b5c03-198">-Scope</span></span>

<span data-ttu-id="b5c03-199">指定模块的安装范围。</span><span class="sxs-lookup"><span data-stu-id="b5c03-199">Specifies the installation scope of the module.</span></span> <span data-ttu-id="b5c03-200">此参数可接受的值为 **AllUsers** 和 **CurrentUser**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-200">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="b5c03-201">**AllUsers** 作用域在计算机的所有用户都可以访问的位置中安装模块：</span><span class="sxs-lookup"><span data-stu-id="b5c03-201">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="b5c03-202">**CurrentUser** 在只能由计算机的当前用户访问的位置中安装模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-202">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="b5c03-203">例如：</span><span class="sxs-lookup"><span data-stu-id="b5c03-203">For example:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="b5c03-204">如果未定义 **作用域** ，则将根据 PowerShellGet 版本设置默认值。</span><span class="sxs-lookup"><span data-stu-id="b5c03-204">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="b5c03-205">在 PowerShellGet 版本2.0.0 及更高版本中，默认值为 **CurrentUser**，无需进行提升即可安装。</span><span class="sxs-lookup"><span data-stu-id="b5c03-205">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="b5c03-206">在 PowerShellGet 1.x 版本中，默认值为 **AllUsers**，这需要提升才能进行安装。</span><span class="sxs-lookup"><span data-stu-id="b5c03-206">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

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

### <span data-ttu-id="b5c03-207">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="b5c03-207">-SkipPublisherCheck</span></span>

<span data-ttu-id="b5c03-208">允许您安装计算机上已存在的较新版本的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-208">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="b5c03-209">例如，如果现有模块由受信任的发布者进行数字签名，但新版本不由受信任的发布者进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="b5c03-209">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="b5c03-210">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b5c03-210">-WhatIf</span></span>

<span data-ttu-id="b5c03-211">显示运行命令时将发生的情况 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-211">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="b5c03-212">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b5c03-212">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b5c03-213">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5c03-213">CommonParameters</span></span>

<span data-ttu-id="b5c03-214">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b5c03-214">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5c03-215">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b5c03-215">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5c03-216">输入</span><span class="sxs-lookup"><span data-stu-id="b5c03-216">INPUTS</span></span>

### <span data-ttu-id="b5c03-217">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="b5c03-217">PSRepositoryItemInfo</span></span>

<span data-ttu-id="b5c03-218">`Find-Module` 创建可通过管道向下发送的 **PSRepositoryItemInfo** 对象 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-218">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="b5c03-219">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b5c03-219">System.String[]</span></span>

### <span data-ttu-id="b5c03-220">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="b5c03-220">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="b5c03-221">System.String</span><span class="sxs-lookup"><span data-stu-id="b5c03-221">System.String</span></span>

### <span data-ttu-id="b5c03-222">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="b5c03-222">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="b5c03-223">System.Uri</span><span class="sxs-lookup"><span data-stu-id="b5c03-223">System.Uri</span></span>

## <span data-ttu-id="b5c03-224">输出</span><span class="sxs-lookup"><span data-stu-id="b5c03-224">OUTPUTS</span></span>

### <span data-ttu-id="b5c03-225">PSRepositoryItemInfo。</span><span class="sxs-lookup"><span data-stu-id="b5c03-225">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="b5c03-226">当使用 **PassThru** 参数时， `Install-Module` 输出该模块的 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="b5c03-226">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="b5c03-227">这与你从 cmdlet 获取的信息相同 `Find-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-227">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="b5c03-228">注释</span><span class="sxs-lookup"><span data-stu-id="b5c03-228">NOTES</span></span>

<span data-ttu-id="b5c03-229">`Install-Module` 在 Windows 7 或 Windows 2008 R2 及更高版本的 Windows 上的 PowerShell 5.0 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="b5c03-229">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5c03-230">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="b5c03-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b5c03-231">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="b5c03-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b5c03-232">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="b5c03-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b5c03-233">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="b5c03-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="b5c03-234">作为最佳安全方案，请在首次运行任何 cmdlet 或函数之前评估模块的代码。</span><span class="sxs-lookup"><span data-stu-id="b5c03-234">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="b5c03-235">为防止运行包含恶意代码的模块，安装后不会自动导入已安装的模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-235">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="b5c03-236">如果存储库中不存在 **name** 参数指定的模块名称，则会 `Install-Module` 返回错误。</span><span class="sxs-lookup"><span data-stu-id="b5c03-236">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="b5c03-237">若要安装多个模块，请使用 **Name** 参数，并指定一个逗号分隔的模块名称数组。</span><span class="sxs-lookup"><span data-stu-id="b5c03-237">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="b5c03-238">如果指定多个模块名称，则不能使用 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion**。</span><span class="sxs-lookup"><span data-stu-id="b5c03-238">If you specify multiple module names, you cannot use **MinimumVersion**, **MaximumVersion**, or **RequiredVersion**.</span></span> <span data-ttu-id="b5c03-239">`Find-Module` 创建可通过管道向下发送的 **PSRepositoryItemInfo** 对象 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-239">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="b5c03-240">管道是在单个命令中指定要安装的多个模块的另一种方法。</span><span class="sxs-lookup"><span data-stu-id="b5c03-240">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="b5c03-241">默认情况下， **AllUsers** 作用域的模块安装在中 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-241">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\PowerShell\Modules`.</span></span> <span data-ttu-id="b5c03-242">默认情况下，在 (DSC) 资源中安装 PowerShell Desired State Configuration 时，会造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b5c03-242">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="b5c03-243">如果模块安装失败，并且在该 `.psm1` `.psd1` 文件夹内没有相同名称的、或，则无法导入 `.dll` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-243">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="b5c03-244">使用 **Force** 参数安装模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-244">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="b5c03-245">如果现有模块的版本与 **name** 参数指定的名称相匹配，并且未使用 **MinimumVersion** 或 **RequiredVersion** 参数，则将以 `Install-Module` 无提示方式继续，但不会安装该模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-245">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="b5c03-246">如果现有模块的版本大于 **MinimumVersion** 参数的值，或者等于 **RequiredVersion** 参数的值，则会以静默方式继续， `Install-Module` 但不会安装该模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-246">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="b5c03-247">如果现有模块与 **MinimumVersion** 或 **RequiredVersion** 参数指定的值不匹配，则会在命令中出现错误 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b5c03-247">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="b5c03-248">例如，如果现有的已安装模块的版本低于 **MinimumVersion** 值或不等于 **RequiredVersion** 值。</span><span class="sxs-lookup"><span data-stu-id="b5c03-248">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="b5c03-249">模块安装还将安装模块发布程序所需的任何指定的相关模块。</span><span class="sxs-lookup"><span data-stu-id="b5c03-249">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="b5c03-250">发布者将在模块清单中指定必需的模块及其版本。</span><span class="sxs-lookup"><span data-stu-id="b5c03-250">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="b5c03-251">相关链接</span><span class="sxs-lookup"><span data-stu-id="b5c03-251">RELATED LINKS</span></span>

[<span data-ttu-id="b5c03-252">Find-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-252">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="b5c03-253">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5c03-253">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="b5c03-254">Import-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-254">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="b5c03-255">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-255">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="b5c03-256">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5c03-256">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="b5c03-257">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-257">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="b5c03-258">Update-Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-258">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="b5c03-259">about_Module</span><span class="sxs-lookup"><span data-stu-id="b5c03-259">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
