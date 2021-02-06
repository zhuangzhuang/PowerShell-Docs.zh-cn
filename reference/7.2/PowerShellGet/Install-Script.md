---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: e2574121cc6b8500f0c5e9e0f76ac25d1c081a8c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598890"
---
# <span data-ttu-id="a0b84-102">Install-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-102">Install-Script</span></span>

## <span data-ttu-id="a0b84-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a0b84-103">SYNOPSIS</span></span>
<span data-ttu-id="a0b84-104">安装脚本。</span><span class="sxs-lookup"><span data-stu-id="a0b84-104">Installs a script.</span></span>

## <span data-ttu-id="a0b84-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0b84-105">SYNTAX</span></span>

### <span data-ttu-id="a0b84-106">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="a0b84-106">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0b84-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="a0b84-107">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a0b84-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a0b84-108">DESCRIPTION</span></span>

<span data-ttu-id="a0b84-109">`Install-Script`Cmdlet 从存储库获取脚本负载，验证负载是否为有效的 PowerShell 脚本，并将脚本文件复制到指定的安装位置。</span><span class="sxs-lookup"><span data-stu-id="a0b84-109">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="a0b84-110">针对的默认存储库 `Install-Script` 操作可通过 `Register-PSRepository` 、 `Set-PSRepository` 、 `Unregister-PSRepository` 和 `Get-PSRepository` cmdlet 进行配置。</span><span class="sxs-lookup"><span data-stu-id="a0b84-110">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="a0b84-111">针对多个存储库进行操作时， `Install-Script` 将从第一个存储库中的 (**名称**、 **MinimumVersion** 或 **MaximumVersion**) 中安装与指定搜索条件相匹配的第一个脚本，而不会出现任何错误。</span><span class="sxs-lookup"><span data-stu-id="a0b84-111">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria (**Name**, **MinimumVersion**, or **MaximumVersion**) from the first repository without any error.</span></span>

## <span data-ttu-id="a0b84-112">示例</span><span class="sxs-lookup"><span data-stu-id="a0b84-112">EXAMPLES</span></span>

### <span data-ttu-id="a0b84-113">示例1：查找并安装脚本</span><span class="sxs-lookup"><span data-stu-id="a0b84-113">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="a0b84-114">第一个命令 `Required-Script2` 从 Local1 存储库中查找名为的脚本，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-114">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="a0b84-115">第二个命令查找 `Required-Script2` 脚本，然后使用管道运算符将其传递给 `Install-Script` cmdlet 来安装它。</span><span class="sxs-lookup"><span data-stu-id="a0b84-115">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="a0b84-116">第三个命令使用 `Get-Command` cmdlet 来获取 `Required-Script2` ，然后显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-116">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="a0b84-117">第四个命令使用 `Get-InstalledScript` cmdlet 来获取 `Required-Script2` 并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-117">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="a0b84-118">第五个命令获取 `Required-Script2` 并使用管道运算符将其传递给 `Format-List` cmdlet 以格式化输出。</span><span class="sxs-lookup"><span data-stu-id="a0b84-118">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="a0b84-119">示例2：使用 AllUsers 范围安装脚本</span><span class="sxs-lookup"><span data-stu-id="a0b84-119">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="a0b84-120">第一个命令安装名为的脚本 `Required-Script3` ，并为其分配 AllUsers 作用域。</span><span class="sxs-lookup"><span data-stu-id="a0b84-120">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="a0b84-121">第二个命令获取已安装的脚本 `Required-Script3` 并显示其相关信息。</span><span class="sxs-lookup"><span data-stu-id="a0b84-121">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="a0b84-122">第三个命令获取 `Required-Script3` 并使用管道运算符将其传递给 `Format-List` cmdlet 以格式化输出。</span><span class="sxs-lookup"><span data-stu-id="a0b84-122">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="a0b84-123">示例3：安装脚本及其依赖项</span><span class="sxs-lookup"><span data-stu-id="a0b84-123">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="a0b84-124">第一个命令 `Script-WithDependencies2` 在 Local1 存储库中查找名为的脚本及其依赖项，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-124">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="a0b84-125">安装第二个命令 `Script-WithDependencies2` 。</span><span class="sxs-lookup"><span data-stu-id="a0b84-125">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="a0b84-126">第三个命令使用 `Get-InstalledScript` script cmdlet 获取安装的脚本并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-126">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="a0b84-127">第四个命令使用 `Get-InstalledModule` cmdlet 来获取已安装的模块并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-127">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="a0b84-128">第五个命令使用 `Find-Script` cmdlet 查找名称以开头的脚本 `Required-Script` ，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-128">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="a0b84-129">第六个命令将在 `Required-Script` Local1 存储库中安装名称以开头的脚本。</span><span class="sxs-lookup"><span data-stu-id="a0b84-129">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="a0b84-130">最后一个命令将获取已安装的脚本并显示结果。</span><span class="sxs-lookup"><span data-stu-id="a0b84-130">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="a0b84-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0b84-131">PARAMETERS</span></span>

### <span data-ttu-id="a0b84-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="a0b84-132">-AcceptLicense</span></span>

<span data-ttu-id="a0b84-133">如果模块需要许可协议，则在安装过程中自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="a0b84-133">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="a0b84-134">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a0b84-134">-AllowPrerelease</span></span>

<span data-ttu-id="a0b84-135">允许安装标记为预发行的脚本。</span><span class="sxs-lookup"><span data-stu-id="a0b84-135">Allows you to install a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="a0b84-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a0b84-136">-Confirm</span></span>

<span data-ttu-id="a0b84-137">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="a0b84-137">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a0b84-138">-Credential</span><span class="sxs-lookup"><span data-stu-id="a0b84-138">-Credential</span></span>

<span data-ttu-id="a0b84-139">指定有权为指定的包提供程序或源安装脚本的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a0b84-139">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="a0b84-140">-Force</span><span class="sxs-lookup"><span data-stu-id="a0b84-140">-Force</span></span>

<span data-ttu-id="a0b84-141">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="a0b84-141">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a0b84-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a0b84-142">-InputObject</span></span>

<span data-ttu-id="a0b84-143">用于管道输入。</span><span class="sxs-lookup"><span data-stu-id="a0b84-143">Used for pipeline input.</span></span>

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

### <span data-ttu-id="a0b84-144">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a0b84-144">-MaximumVersion</span></span>

<span data-ttu-id="a0b84-145">指定要安装的单个脚本的最高版本。</span><span class="sxs-lookup"><span data-stu-id="a0b84-145">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="a0b84-146">如果尝试安装多个脚本，则无法添加此参数。</span><span class="sxs-lookup"><span data-stu-id="a0b84-146">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="a0b84-147">**MaximumVersion** 和 **RequiredVersion** 参数相互排斥;不能在同一命令中同时使用这两个参数。</span><span class="sxs-lookup"><span data-stu-id="a0b84-147">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="a0b84-148">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a0b84-148">-MinimumVersion</span></span>

<span data-ttu-id="a0b84-149">指定要安装的单个脚本的最低版本。</span><span class="sxs-lookup"><span data-stu-id="a0b84-149">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="a0b84-150">如果尝试安装多个脚本，则无法添加此参数。</span><span class="sxs-lookup"><span data-stu-id="a0b84-150">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="a0b84-151">MinimumVersion 和 RequiredVersion 参数互斥，不能在同一命令中使用这两个参数。</span><span class="sxs-lookup"><span data-stu-id="a0b84-151">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="a0b84-152">-Name</span><span class="sxs-lookup"><span data-stu-id="a0b84-152">-Name</span></span>

<span data-ttu-id="a0b84-153">指定要安装的脚本的名称数组。</span><span class="sxs-lookup"><span data-stu-id="a0b84-153">Specifies an array of names of scripts to install.</span></span>

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

### <span data-ttu-id="a0b84-154">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="a0b84-154">-NoPathUpdate</span></span>

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

### <span data-ttu-id="a0b84-155">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a0b84-155">-PassThru</span></span>

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

### <span data-ttu-id="a0b84-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a0b84-156">-Proxy</span></span>

<span data-ttu-id="a0b84-157">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="a0b84-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="a0b84-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a0b84-158">-ProxyCredential</span></span>

<span data-ttu-id="a0b84-159">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a0b84-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a0b84-160">-Repository</span><span class="sxs-lookup"><span data-stu-id="a0b84-160">-Repository</span></span>

<span data-ttu-id="a0b84-161">指定已向 cmdlet 注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="a0b84-161">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="a0b84-162">默认值为所有已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="a0b84-162">The default is all registered repositories.</span></span>

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

### <span data-ttu-id="a0b84-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a0b84-163">-RequiredVersion</span></span>

<span data-ttu-id="a0b84-164">指定要安装的脚本的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="a0b84-164">Specifies the exact version number of the script to install.</span></span>

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

### <span data-ttu-id="a0b84-165">-Scope</span><span class="sxs-lookup"><span data-stu-id="a0b84-165">-Scope</span></span>

<span data-ttu-id="a0b84-166">指定脚本的安装范围。</span><span class="sxs-lookup"><span data-stu-id="a0b84-166">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="a0b84-167">有效值为：AllUsers 和 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="a0b84-167">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="a0b84-168">AllUsers 作用域允许将模块安装在计算机的所有用户都可访问的位置，即 `$env:ProgramFiles\WindowsPowerShell\Scripts` 。</span><span class="sxs-lookup"><span data-stu-id="a0b84-168">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="a0b84-169">CurrentUser 范围仅允许将模块安装到 `$home\Documents\WindowsPowerShell\Scripts` ，以便仅向当前用户提供该模块。</span><span class="sxs-lookup"><span data-stu-id="a0b84-169">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="a0b84-170">如果未定义 **作用域** ，将基于当前会话设置默认值：</span><span class="sxs-lookup"><span data-stu-id="a0b84-170">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="a0b84-171">对于提升的 PowerShell 会话， **范围** 默认为 AllUsers;</span><span class="sxs-lookup"><span data-stu-id="a0b84-171">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="a0b84-172">对于 [PowerShellGet 版本 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) 及更高版本中未提升的 PowerShell 会话， **范围** 为 CurrentUser;</span><span class="sxs-lookup"><span data-stu-id="a0b84-172">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="a0b84-173">对于在 PowerShellGet 版本1.6.7 和更早版本中未提升的 PowerShell 会话， **范围** 是不确定的，并且 `Install-Module` 失败。</span><span class="sxs-lookup"><span data-stu-id="a0b84-173">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

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

### <span data-ttu-id="a0b84-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a0b84-174">-WhatIf</span></span>

<span data-ttu-id="a0b84-175">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="a0b84-175">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a0b84-176">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="a0b84-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a0b84-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0b84-177">CommonParameters</span></span>

<span data-ttu-id="a0b84-178">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a0b84-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0b84-179">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a0b84-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0b84-180">输入</span><span class="sxs-lookup"><span data-stu-id="a0b84-180">INPUTS</span></span>

### <span data-ttu-id="a0b84-181">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a0b84-181">System.String[]</span></span>

### <span data-ttu-id="a0b84-182">System.web. system.exception []</span><span class="sxs-lookup"><span data-stu-id="a0b84-182">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="a0b84-183">System.String</span><span class="sxs-lookup"><span data-stu-id="a0b84-183">System.String</span></span>

### <span data-ttu-id="a0b84-184">System.Uri</span><span class="sxs-lookup"><span data-stu-id="a0b84-184">System.Uri</span></span>

### <span data-ttu-id="a0b84-185">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="a0b84-185">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="a0b84-186">输出</span><span class="sxs-lookup"><span data-stu-id="a0b84-186">OUTPUTS</span></span>

### <span data-ttu-id="a0b84-187">System.Object</span><span class="sxs-lookup"><span data-stu-id="a0b84-187">System.Object</span></span>

## <span data-ttu-id="a0b84-188">注释</span><span class="sxs-lookup"><span data-stu-id="a0b84-188">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0b84-189">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="a0b84-189">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a0b84-190">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="a0b84-190">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a0b84-191">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="a0b84-191">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a0b84-192">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="a0b84-192">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a0b84-193">相关链接</span><span class="sxs-lookup"><span data-stu-id="a0b84-193">RELATED LINKS</span></span>

[<span data-ttu-id="a0b84-194">Find-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-194">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="a0b84-195">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-195">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="a0b84-196">Save-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-196">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="a0b84-197">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-197">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="a0b84-198">Update-Script</span><span class="sxs-lookup"><span data-stu-id="a0b84-198">Update-Script</span></span>](Update-Script.md)
