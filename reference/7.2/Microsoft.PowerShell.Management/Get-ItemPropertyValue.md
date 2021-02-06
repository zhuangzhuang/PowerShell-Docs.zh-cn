---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: b8980febb80a4e7dfaefba46649ac49b5b41b427
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596821"
---
# <span data-ttu-id="7a4ec-102">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="7a4ec-102">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="7a4ec-103">摘要</span><span class="sxs-lookup"><span data-stu-id="7a4ec-103">SYNOPSIS</span></span>
<span data-ttu-id="7a4ec-104">获取指定项的一个或多个属性的值。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-104">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="7a4ec-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a4ec-105">SYNTAX</span></span>

### <span data-ttu-id="7a4ec-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="7a4ec-106">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="7a4ec-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a4ec-107">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="7a4ec-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7a4ec-108">DESCRIPTION</span></span>

<span data-ttu-id="7a4ec-109">`Get-ItemPropertyValue`当你使用 *Name* 参数时，获取指定的属性的当前值，该属性位于你使用 *path* 或 *LiteralPath* 参数指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-109">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="7a4ec-110">示例</span><span class="sxs-lookup"><span data-stu-id="7a4ec-110">EXAMPLES</span></span>

### <span data-ttu-id="7a4ec-111">示例 1：获取 ProductID 属性的值</span><span class="sxs-lookup"><span data-stu-id="7a4ec-111">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="7a4ec-112">此命令获取 Windows 注册表提供程序中 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 对象的 **ProductID** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-112">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="7a4ec-113">示例 2：获取文件或文件夹的上次写入时间</span><span class="sxs-lookup"><span data-stu-id="7a4ec-113">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="7a4ec-114">此命令将获取 **LastWriteTime** 属性的值，或上次更改文件或文件夹的时间，从 "C:\Users\Test\Documents\ModuleToAssembly" 文件夹，在 FileSystem 提供程序中工作。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-114">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="7a4ec-115">示例 3：获取文件或文件夹的多个属性的值</span><span class="sxs-lookup"><span data-stu-id="7a4ec-115">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="7a4ec-116">此命令用于获取文件夹的 **LastWriteTime**、**CreationTime** 和 **Root** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-116">This command gets the values of the **LastWriteTime**, **CreationTime**, and **Root** properties of a folder.</span></span> <span data-ttu-id="7a4ec-117">这些属性值按照属性名称的指定顺序返回。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-117">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="7a4ec-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a4ec-118">PARAMETERS</span></span>

### <span data-ttu-id="7a4ec-119">-Credential</span><span class="sxs-lookup"><span data-stu-id="7a4ec-119">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7a4ec-120">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-120">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="7a4ec-121">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-121">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7a4ec-122">-Exclude</span><span class="sxs-lookup"><span data-stu-id="7a4ec-122">-Exclude</span></span>

<span data-ttu-id="7a4ec-123">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="7a4ec-124">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7a4ec-125">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7a4ec-126">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="7a4ec-127">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7a4ec-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="7a4ec-128">-Filter</span></span>

<span data-ttu-id="7a4ec-129">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="7a4ec-130">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="7a4ec-131">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="7a4ec-132">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="7a4ec-133">-Include</span><span class="sxs-lookup"><span data-stu-id="7a4ec-133">-Include</span></span>

<span data-ttu-id="7a4ec-134">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-134">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="7a4ec-135">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-135">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7a4ec-136">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-136">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="7a4ec-137">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-137">Wildcard characters are permitted.</span></span> <span data-ttu-id="7a4ec-138">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-138">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7a4ec-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a4ec-139">-LiteralPath</span></span>

<span data-ttu-id="7a4ec-140">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-140">Specifies a path to one or more locations.</span></span> <span data-ttu-id="7a4ec-141">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-141">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7a4ec-142">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7a4ec-143">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7a4ec-144">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-144">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="7a4ec-145">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-145">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="7a4ec-146">-Name</span><span class="sxs-lookup"><span data-stu-id="7a4ec-146">-Name</span></span>

<span data-ttu-id="7a4ec-147">指定要检索的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-147">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="7a4ec-148">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-148">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7a4ec-149">-Path</span><span class="sxs-lookup"><span data-stu-id="7a4ec-149">-Path</span></span>

<span data-ttu-id="7a4ec-150">指定一个或多个项的路径。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-150">Specifies the path to the item or items.</span></span>
<span data-ttu-id="7a4ec-151">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="7a4ec-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a4ec-152">CommonParameters</span></span>

<span data-ttu-id="7a4ec-153">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-153">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7a4ec-154">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7a4ec-155">输入</span><span class="sxs-lookup"><span data-stu-id="7a4ec-155">INPUTS</span></span>

### <span data-ttu-id="7a4ec-156">System.String</span><span class="sxs-lookup"><span data-stu-id="7a4ec-156">System.String</span></span>

<span data-ttu-id="7a4ec-157">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-157">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="7a4ec-158">输出</span><span class="sxs-lookup"><span data-stu-id="7a4ec-158">OUTPUTS</span></span>

### <span data-ttu-id="7a4ec-159">System.Boolean、System.String、System.DateTime</span><span class="sxs-lookup"><span data-stu-id="7a4ec-159">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="7a4ec-160">此 cmdlet 为其所获取的每个项属性返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-160">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="7a4ec-161">对象类型取决于检索的属性值。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-161">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="7a4ec-162">例如，在文件系统驱动器中，该 cmdlet 可能会返回一个文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-162">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="7a4ec-163">注释</span><span class="sxs-lookup"><span data-stu-id="7a4ec-163">NOTES</span></span>

<span data-ttu-id="7a4ec-164">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-164">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="7a4ec-165">若要列出会话中可用的提供程序，请运行 `Get-PSProvider` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-165">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="7a4ec-166">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4ec-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7a4ec-167">相关链接</span><span class="sxs-lookup"><span data-stu-id="7a4ec-167">RELATED LINKS</span></span>

[<span data-ttu-id="7a4ec-168">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-168">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="7a4ec-169">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-169">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="7a4ec-170">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-170">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="7a4ec-171">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="7a4ec-171">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="7a4ec-172">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-172">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="7a4ec-173">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-173">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="7a4ec-174">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-174">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="7a4ec-175">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-175">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="7a4ec-176">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7a4ec-176">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="7a4ec-177">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7a4ec-177">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

