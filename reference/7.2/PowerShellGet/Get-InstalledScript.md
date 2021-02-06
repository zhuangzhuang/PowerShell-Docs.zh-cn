---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: fe5fc0feb34fda87dab987f33140992a346017a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603610"
---
# <span data-ttu-id="c3d42-102">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="c3d42-102">Get-InstalledScript</span></span>

## <span data-ttu-id="c3d42-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c3d42-103">SYNOPSIS</span></span>
<span data-ttu-id="c3d42-104">获取已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-104">Gets an installed script.</span></span>

## <span data-ttu-id="c3d42-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3d42-105">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="c3d42-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c3d42-106">DESCRIPTION</span></span>

<span data-ttu-id="c3d42-107">**Get-installedscript** cmdlet 将获取 CurrentUser 和 AllUsers 作用域的安装脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-107">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="c3d42-108">示例</span><span class="sxs-lookup"><span data-stu-id="c3d42-108">EXAMPLES</span></span>

### <span data-ttu-id="c3d42-109">示例1：获取所有已安装的脚本</span><span class="sxs-lookup"><span data-stu-id="c3d42-109">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="c3d42-110">此命令将获取所有已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-110">This command gets all installed scripts.</span></span>

### <span data-ttu-id="c3d42-111">示例2：按名称获取安装的脚本</span><span class="sxs-lookup"><span data-stu-id="c3d42-111">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="c3d42-112">此命令将获取名称以编写开头的脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-112">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="c3d42-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3d42-113">PARAMETERS</span></span>

### <span data-ttu-id="c3d42-114">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c3d42-114">-AllowPrerelease</span></span>

<span data-ttu-id="c3d42-115">包括标记为预发行的结果脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-115">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="c3d42-116">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c3d42-116">-MaximumVersion</span></span>

<span data-ttu-id="c3d42-117">指定要获取的最大或最新版本的脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-117">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="c3d42-118">MaximumVersion 和 RequiredVersion 参数互斥，不能在同一命令中使用这两个参数。</span><span class="sxs-lookup"><span data-stu-id="c3d42-118">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3d42-119">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c3d42-119">-MinimumVersion</span></span>

<span data-ttu-id="c3d42-120">指定要获取的脚本的最低版本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-120">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="c3d42-121">MinimumVersion 和 RequiredVersion 参数互斥，不能在同一命令中使用这两个参数。</span><span class="sxs-lookup"><span data-stu-id="c3d42-121">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3d42-122">-Name</span><span class="sxs-lookup"><span data-stu-id="c3d42-122">-Name</span></span>

<span data-ttu-id="c3d42-123">指定要获取的脚本的名称数组。</span><span class="sxs-lookup"><span data-stu-id="c3d42-123">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="c3d42-124">可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c3d42-124">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c3d42-125">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c3d42-125">-RequiredVersion</span></span>

<span data-ttu-id="c3d42-126">指定要获取的脚本的确切版本。</span><span class="sxs-lookup"><span data-stu-id="c3d42-126">Specifies the exact version of a script to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3d42-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3d42-127">CommonParameters</span></span>

<span data-ttu-id="c3d42-128">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c3d42-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3d42-129">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c3d42-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3d42-130">输入</span><span class="sxs-lookup"><span data-stu-id="c3d42-130">INPUTS</span></span>

### <span data-ttu-id="c3d42-131">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c3d42-131">System.String[]</span></span>

### <span data-ttu-id="c3d42-132">System.String</span><span class="sxs-lookup"><span data-stu-id="c3d42-132">System.String</span></span>

## <span data-ttu-id="c3d42-133">输出</span><span class="sxs-lookup"><span data-stu-id="c3d42-133">OUTPUTS</span></span>

### <span data-ttu-id="c3d42-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="c3d42-134">System.Object</span></span>

## <span data-ttu-id="c3d42-135">注释</span><span class="sxs-lookup"><span data-stu-id="c3d42-135">NOTES</span></span>

## <span data-ttu-id="c3d42-136">相关链接</span><span class="sxs-lookup"><span data-stu-id="c3d42-136">RELATED LINKS</span></span>

[<span data-ttu-id="c3d42-137">Install-Script</span><span class="sxs-lookup"><span data-stu-id="c3d42-137">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="c3d42-138">卸载-脚本</span><span class="sxs-lookup"><span data-stu-id="c3d42-138">Uninstall-Script</span></span>](Uninstall-Script.md)

