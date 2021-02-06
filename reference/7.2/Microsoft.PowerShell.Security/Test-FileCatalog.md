---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 0a990b1c0c46cda06c5239a4c8fde55b29296376
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "99597243"
---
# <span data-ttu-id="4b979-102">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4b979-102">Test-FileCatalog</span></span>

## <span data-ttu-id="4b979-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4b979-103">SYNOPSIS</span></span>
<span data-ttu-id="4b979-104">`Test-FileCatalog` 验证)  ( 的目录文件中包含的哈希是否与实际文件的哈希值相匹配，以便验证其真实性。</span><span class="sxs-lookup"><span data-stu-id="4b979-104">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="4b979-105">此 cmdlet 仅在 Windows 上受支持。</span><span class="sxs-lookup"><span data-stu-id="4b979-105">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="4b979-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4b979-106">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4b979-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4b979-107">DESCRIPTION</span></span>

<span data-ttu-id="4b979-108">`Test-FileCatalog` 通过将目录文件)  ( 的文件哈希与磁盘上实际文件的哈希进行比较来验证文件的真实性。</span><span class="sxs-lookup"><span data-stu-id="4b979-108">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="4b979-109">如果它检测到任何不匹配，它将以 ValidationFailed 的形式返回状态。</span><span class="sxs-lookup"><span data-stu-id="4b979-109">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="4b979-110">用户可通过使用 -Detailed 参数检索所有这些信息。</span><span class="sxs-lookup"><span data-stu-id="4b979-110">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="4b979-111">它还在签名属性中显示目录的签名状态，该状态等效于对 `Get-AuthenticodeSignature` 目录文件调用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b979-111">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="4b979-112">用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。</span><span class="sxs-lookup"><span data-stu-id="4b979-112">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="4b979-113">此 cmdlet 仅在 Windows 上受支持。</span><span class="sxs-lookup"><span data-stu-id="4b979-113">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="4b979-114">示例</span><span class="sxs-lookup"><span data-stu-id="4b979-114">EXAMPLES</span></span>

### <span data-ttu-id="4b979-115">示例1：创建和验证文件目录</span><span class="sxs-lookup"><span data-stu-id="4b979-115">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="4b979-116">示例2：使用详细输出验证文件目录</span><span class="sxs-lookup"><span data-stu-id="4b979-116">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="4b979-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b979-117">PARAMETERS</span></span>

### <span data-ttu-id="4b979-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="4b979-118">-CatalogFilePath</span></span>

<span data-ttu-id="4b979-119">目录文件的路径 ( .cat) ，其中包含要用于验证的哈希值。</span><span class="sxs-lookup"><span data-stu-id="4b979-119">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4b979-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4b979-120">-Confirm</span></span>

<span data-ttu-id="4b979-121">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="4b979-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4b979-122">-Detailed</span><span class="sxs-lookup"><span data-stu-id="4b979-122">-Detailed</span></span>

<span data-ttu-id="4b979-123">返回更详细的信息 `CatalogInformation` ，其中包含经过测试的文件、其预期/实际哈希以及目录文件（如果已签名）的 Authenticode 签名。</span><span class="sxs-lookup"><span data-stu-id="4b979-123">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="4b979-124">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="4b979-124">-FilesToSkip</span></span>

<span data-ttu-id="4b979-125">不应在验证过程中测试的路径的数组。</span><span class="sxs-lookup"><span data-stu-id="4b979-125">An array of paths that should not be tested as part of the validation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b979-126">-Path</span><span class="sxs-lookup"><span data-stu-id="4b979-126">-Path</span></span>

<span data-ttu-id="4b979-127">应该针对目录文件验证的一个或一组文件。</span><span class="sxs-lookup"><span data-stu-id="4b979-127">A folder or array of files that should be validated against the catalog file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4b979-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4b979-128">-WhatIf</span></span>

<span data-ttu-id="4b979-129">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="4b979-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4b979-130">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="4b979-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4b979-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b979-131">CommonParameters</span></span>

<span data-ttu-id="4b979-132">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4b979-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b979-133">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4b979-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b979-134">输入</span><span class="sxs-lookup"><span data-stu-id="4b979-134">INPUTS</span></span>

### <span data-ttu-id="4b979-135">DirectoryInfo []，System.string []</span><span class="sxs-lookup"><span data-stu-id="4b979-135">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="4b979-136">管道接受一个字符串或 `DirectoryInfo` 对象的数组，这些字符串或对象表示需要验证的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="4b979-136">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="4b979-137">输出</span><span class="sxs-lookup"><span data-stu-id="4b979-137">OUTPUTS</span></span>

### <span data-ttu-id="4b979-138">System.web. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="4b979-138">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="4b979-139">包含或的值的默认返回类型 `Valid` `ValidationFailed` 。</span><span class="sxs-lookup"><span data-stu-id="4b979-139">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="4b979-140">System.web. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="4b979-140">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="4b979-141">当使用时返回更详细的对象 `-Detailed` ，该对象可用于分析可能已通过或可能未通过验证的特定文件，这是预期的哈希值与发现的，以及在目录中使用的算法。</span><span class="sxs-lookup"><span data-stu-id="4b979-141">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="4b979-142">注释</span><span class="sxs-lookup"><span data-stu-id="4b979-142">NOTES</span></span>

<span data-ttu-id="4b979-143">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="4b979-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="4b979-144">相关链接</span><span class="sxs-lookup"><span data-stu-id="4b979-144">RELATED LINKS</span></span>

[<span data-ttu-id="4b979-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4b979-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="4b979-146">立即</span><span class="sxs-lookup"><span data-stu-id="4b979-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
