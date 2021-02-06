---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 20820d2d194f41d43048c9617b63b9acb3fbb4f8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598879"
---
# <span data-ttu-id="2fc9a-102">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2fc9a-102">Get-PSProvider</span></span>

## <span data-ttu-id="2fc9a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2fc9a-103">SYNOPSIS</span></span>
<span data-ttu-id="2fc9a-104">获取有关指定 PowerShell 提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-104">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="2fc9a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2fc9a-105">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2fc9a-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2fc9a-106">DESCRIPTION</span></span>

<span data-ttu-id="2fc9a-107">`Get-PSProvider`Cmdlet 将获取当前会话中的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-107">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="2fc9a-108">可以获取会话中的特定驱动器或所有驱动器。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-108">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="2fc9a-109">PowerShell 提供程序使你可以访问各种数据存储，就好像它们是文件系统驱动器一样。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-109">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="2fc9a-110">有关 PowerShell 提供程序的信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-110">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2fc9a-111">示例</span><span class="sxs-lookup"><span data-stu-id="2fc9a-111">EXAMPLES</span></span>

### <span data-ttu-id="2fc9a-112">示例1：显示所有可用提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="2fc9a-112">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="2fc9a-113">此命令显示所有可用 PowerShell 提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-113">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="2fc9a-114">示例2：显示以指定字母开头的所有 PowerShell 提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="2fc9a-114">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="2fc9a-115">此命令显示其名称以字母 "f" 或 "r" 开头的所有 PowerShell 提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-115">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="2fc9a-116">示例3：查找将提供程序添加到会话的管理单元或模块</span><span class="sxs-lookup"><span data-stu-id="2fc9a-116">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="2fc9a-117">这些命令将查找向会话添加提供程序的 PowerShell 管理单元或模块。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-117">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="2fc9a-118">所有 PowerShell 元素（包括提供程序）均源自管理单元或模块。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-118">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="2fc9a-119">这些命令使用返回的 **ProviderInfo** 对象的 Add-pssnapin 和 Module 属性 `Get-PSProvider` 。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-119">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="2fc9a-120">这些属性的值包含添加提供程序的管理单元或模块的名称。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-120">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="2fc9a-121">第一个命令获取会话中的所有提供程序，并将它们的格式设置为表，其中显示其 Name、Module 和 PSSnapin 属性的值。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-121">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="2fc9a-122">第二个命令使用 `Where-Object` cmdlet 来获取来自 **Microsoft. Security** 管理单元的提供程序。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-122">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="2fc9a-123">示例4：解析文件系统提供程序的 Home 属性的路径</span><span class="sxs-lookup"><span data-stu-id="2fc9a-123">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="2fc9a-124">此示例显示波形符 (~) 表示 FileSystem 提供程序的 **Home** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-124">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="2fc9a-125">**Home** 属性值是可选的，但对于 **FileSystem** 提供程序，其定义为 `$env:homedrive\$env:homepath` 或 `$home` 。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-125">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="2fc9a-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2fc9a-126">PARAMETERS</span></span>

### <span data-ttu-id="2fc9a-127">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2fc9a-127">-PSProvider</span></span>

<span data-ttu-id="2fc9a-128">指定此 cmdlet 从中获取信息的 PowerShell 提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-128">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2fc9a-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2fc9a-129">CommonParameters</span></span>

<span data-ttu-id="2fc9a-130">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2fc9a-131">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2fc9a-132">输入</span><span class="sxs-lookup"><span data-stu-id="2fc9a-132">INPUTS</span></span>

### <span data-ttu-id="2fc9a-133">String[]</span><span class="sxs-lookup"><span data-stu-id="2fc9a-133">String[]</span></span>

<span data-ttu-id="2fc9a-134">可以通过管道将一个或多个提供程序名称字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-134">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="2fc9a-135">输出</span><span class="sxs-lookup"><span data-stu-id="2fc9a-135">OUTPUTS</span></span>

### <span data-ttu-id="2fc9a-136">System.web. ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="2fc9a-136">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="2fc9a-137">此 cmdlet 返回表示会话中 PowerShell 提供程序的对象。</span><span class="sxs-lookup"><span data-stu-id="2fc9a-137">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="2fc9a-138">注释</span><span class="sxs-lookup"><span data-stu-id="2fc9a-138">NOTES</span></span>

## <span data-ttu-id="2fc9a-139">相关链接</span><span class="sxs-lookup"><span data-stu-id="2fc9a-139">RELATED LINKS</span></span>

