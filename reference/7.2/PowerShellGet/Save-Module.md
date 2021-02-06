---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: df5056b4402664602409388825c8b2b8acd4e02f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598052"
---
# <span data-ttu-id="b04b3-102">Save-Module</span><span class="sxs-lookup"><span data-stu-id="b04b3-102">Save-Module</span></span>

## <span data-ttu-id="b04b3-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b04b3-103">SYNOPSIS</span></span>
<span data-ttu-id="b04b3-104">将模块及其依赖项保存在本地计算机上，但不会安装该模块。</span><span class="sxs-lookup"><span data-stu-id="b04b3-104">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="b04b3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b04b3-105">SYNTAX</span></span>

### <span data-ttu-id="b04b3-106">NameAndPathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="b04b3-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b04b3-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b04b3-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b04b3-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b04b3-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b04b3-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b04b3-109">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b04b3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b04b3-110">DESCRIPTION</span></span>

<span data-ttu-id="b04b3-111">`Save-Module`Cmdlet 从已注册的存储库下载模块和任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="b04b3-111">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="b04b3-112">`Save-Module` 下载并保存模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b04b3-112">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="b04b3-113">文件将保存到本地计算机上的指定路径。</span><span class="sxs-lookup"><span data-stu-id="b04b3-113">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="b04b3-114">未安装该模块，但可以由管理员检查内容。</span><span class="sxs-lookup"><span data-stu-id="b04b3-114">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="b04b3-115">然后，可以将保存的模块复制到 `$env:PSModulePath` 脱机计算机的相应位置。</span><span class="sxs-lookup"><span data-stu-id="b04b3-115">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="b04b3-116">`Get-PSRepository` 显示本地计算机的已注册存储库。</span><span class="sxs-lookup"><span data-stu-id="b04b3-116">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="b04b3-117">你可以使用 `Find-Module` cmdlet 来搜索已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="b04b3-117">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="b04b3-118">示例</span><span class="sxs-lookup"><span data-stu-id="b04b3-118">EXAMPLES</span></span>

### <span data-ttu-id="b04b3-119">示例1：保存模块</span><span class="sxs-lookup"><span data-stu-id="b04b3-119">Example 1: Save a module</span></span>

<span data-ttu-id="b04b3-120">在此示例中，模块及其依赖项保存到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b04b3-120">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="b04b3-121">`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-121">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="b04b3-122">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="b04b3-122">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="b04b3-123">**存储库** 参数指定已注册的存储库 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-123">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="b04b3-124">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="b04b3-124">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="b04b3-125">示例2：保存模块的特定版本</span><span class="sxs-lookup"><span data-stu-id="b04b3-125">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="b04b3-126">此示例演示如何使用参数（如 **MaximumVersion**）或 **RequiredVersion** 来指定模块版本。</span><span class="sxs-lookup"><span data-stu-id="b04b3-126">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="b04b3-127">`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-127">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="b04b3-128">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="b04b3-128">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="b04b3-129">**存储库** 参数指定已注册的存储库 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-129">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="b04b3-130">**MaximumVersion** 指定下载并保存版本 **2.1.0** 。</span><span class="sxs-lookup"><span data-stu-id="b04b3-130">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="b04b3-131">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="b04b3-131">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="b04b3-132">示例3：查找并保存模块的特定版本</span><span class="sxs-lookup"><span data-stu-id="b04b3-132">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="b04b3-133">在此示例中，在存储库中找到所需的模块版本，并将其保存到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b04b3-133">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="b04b3-134">`Find-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-134">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="b04b3-135">**存储库** 参数指定已注册的存储库 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-135">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="b04b3-136">**RequiredVersion** 指定版本 **1.6.5**。</span><span class="sxs-lookup"><span data-stu-id="b04b3-136">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="b04b3-137">将对象向下发送到 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b04b3-137">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="b04b3-138">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="b04b3-138">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="b04b3-139">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="b04b3-139">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="b04b3-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b04b3-140">PARAMETERS</span></span>

### <span data-ttu-id="b04b3-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b04b3-141">-AcceptLicense</span></span>

<span data-ttu-id="b04b3-142">如果包需要许可协议，则自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="b04b3-142">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="b04b3-143">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b04b3-143">-AllowPrerelease</span></span>

<span data-ttu-id="b04b3-144">允许您保存标记为预发行的模块。</span><span class="sxs-lookup"><span data-stu-id="b04b3-144">Allows you to save a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b04b3-145">-Confirm</span></span>

<span data-ttu-id="b04b3-146">提示你在运行之前进行确认 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b04b3-146">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="b04b3-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="b04b3-147">-Credential</span></span>

<span data-ttu-id="b04b3-148">指定有权保存模块的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b04b3-148">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="b04b3-149">-Force</span><span class="sxs-lookup"><span data-stu-id="b04b3-149">-Force</span></span>

<span data-ttu-id="b04b3-150">强制 `Save-Module` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="b04b3-150">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b04b3-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b04b3-151">-InputObject</span></span>

<span data-ttu-id="b04b3-152">接受 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="b04b3-152">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="b04b3-153">例如，输出 `Find-Module` 到变量，并将该变量用作 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="b04b3-153">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b04b3-154">-LiteralPath</span></span>

<span data-ttu-id="b04b3-155">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="b04b3-155">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b04b3-156">**LiteralPath** 参数的值完全按输入方式使用。</span><span class="sxs-lookup"><span data-stu-id="b04b3-156">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="b04b3-157">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="b04b3-157">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b04b3-158">如果路径包含转义符，请将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="b04b3-158">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="b04b3-159">PowerShell 不会将括在单引号中的任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="b04b3-159">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-160">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b04b3-160">-MaximumVersion</span></span>

<span data-ttu-id="b04b3-161">指定要保存的模块的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="b04b3-161">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="b04b3-162">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="b04b3-162">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-163">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b04b3-163">-MinimumVersion</span></span>

<span data-ttu-id="b04b3-164">指定要保存的单个模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="b04b3-164">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="b04b3-165">如果尝试安装多个模块，则无法添加此参数。</span><span class="sxs-lookup"><span data-stu-id="b04b3-165">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="b04b3-166">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="b04b3-166">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-167">-Name</span><span class="sxs-lookup"><span data-stu-id="b04b3-167">-Name</span></span>

<span data-ttu-id="b04b3-168">指定要保存的模块的名称数组。</span><span class="sxs-lookup"><span data-stu-id="b04b3-168">Specifies an array of names of modules to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-169">-Path</span><span class="sxs-lookup"><span data-stu-id="b04b3-169">-Path</span></span>

<span data-ttu-id="b04b3-170">指定本地计算机上存储已保存模块的位置。</span><span class="sxs-lookup"><span data-stu-id="b04b3-170">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="b04b3-171">接受通配符。</span><span class="sxs-lookup"><span data-stu-id="b04b3-171">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b04b3-172">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b04b3-172">-Proxy</span></span>

<span data-ttu-id="b04b3-173">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="b04b3-173">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="b04b3-174">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b04b3-174">-ProxyCredential</span></span>

<span data-ttu-id="b04b3-175">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b04b3-175">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b04b3-176">-Repository</span><span class="sxs-lookup"><span data-stu-id="b04b3-176">-Repository</span></span>

<span data-ttu-id="b04b3-177">指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="b04b3-177">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="b04b3-178">用于 `Get-PSRepository` 显示已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="b04b3-178">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-179">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b04b3-179">-RequiredVersion</span></span>

<span data-ttu-id="b04b3-180">指定要保存的模块的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="b04b3-180">Specifies the exact version number of the module to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b04b3-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b04b3-181">-WhatIf</span></span>

<span data-ttu-id="b04b3-182">显示运行时将发生的情况 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="b04b3-182">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="b04b3-183">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b04b3-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b04b3-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b04b3-184">CommonParameters</span></span>

<span data-ttu-id="b04b3-185">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b04b3-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b04b3-186">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b04b3-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b04b3-187">输入</span><span class="sxs-lookup"><span data-stu-id="b04b3-187">INPUTS</span></span>

### <span data-ttu-id="b04b3-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b04b3-188">System.String[]</span></span>

### <span data-ttu-id="b04b3-189">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="b04b3-189">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="b04b3-190">System.String</span><span class="sxs-lookup"><span data-stu-id="b04b3-190">System.String</span></span>

### <span data-ttu-id="b04b3-191">System.Uri</span><span class="sxs-lookup"><span data-stu-id="b04b3-191">System.Uri</span></span>

### <span data-ttu-id="b04b3-192">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="b04b3-192">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="b04b3-193">输出</span><span class="sxs-lookup"><span data-stu-id="b04b3-193">OUTPUTS</span></span>

### <span data-ttu-id="b04b3-194">System.Object</span><span class="sxs-lookup"><span data-stu-id="b04b3-194">System.Object</span></span>

## <span data-ttu-id="b04b3-195">注释</span><span class="sxs-lookup"><span data-stu-id="b04b3-195">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b04b3-196">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="b04b3-196">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b04b3-197">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="b04b3-197">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b04b3-198">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="b04b3-198">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b04b3-199">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="b04b3-199">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="b04b3-200">相关链接</span><span class="sxs-lookup"><span data-stu-id="b04b3-200">RELATED LINKS</span></span>
