---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596418"
---
# <span data-ttu-id="6ebfc-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6ebfc-102">New-TemporaryFile</span></span>

## <span data-ttu-id="6ebfc-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6ebfc-103">SYNOPSIS</span></span>
<span data-ttu-id="6ebfc-104">创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-104">Creates a temporary file.</span></span>

## <span data-ttu-id="6ebfc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ebfc-105">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6ebfc-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6ebfc-106">DESCRIPTION</span></span>

<span data-ttu-id="6ebfc-107">此 cmdlet 创建可以在脚本中使用的临时文件。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-107">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="6ebfc-108">`New-TemporaryFile`Cmdlet 将创建一个具有文件扩展名的空文件 `.tmp` 。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-108">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="6ebfc-109">此 cmdlet 将文件命名 `tmp<NNNN>.tmp` 为，其中 `<NNNN>` 是一个随机十六进制数。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-109">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="6ebfc-110">Cmdlet 将在 **临时** 文件夹中创建文件。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-110">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="6ebfc-111">此 cmdlet 使用 [GetTempPath ( # B1](/dotnet/api/system.io.path.gettemppath) 方法查找 **临时** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-111">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="6ebfc-112">此方法按以下顺序检查环境变量是否存在，并使用找到的第一个路径：</span><span class="sxs-lookup"><span data-stu-id="6ebfc-112">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="6ebfc-113">在 Windows 平台上：</span><span class="sxs-lookup"><span data-stu-id="6ebfc-113">On Windows platforms:</span></span>

  1. <span data-ttu-id="6ebfc-114">TMP 环境变量指定的路径。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-114">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="6ebfc-115">由 TEMP 环境变量指定的路径。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-115">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="6ebfc-116">USERPROFILE 环境变量指定的路径。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-116">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="6ebfc-117">Windows 目录。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-117">The Windows directory.</span></span>

- <span data-ttu-id="6ebfc-118">在非 Windows 平台上：使用由 TMPDIR 环境变量指定的路径。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-118">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="6ebfc-119">示例</span><span class="sxs-lookup"><span data-stu-id="6ebfc-119">EXAMPLES</span></span>

### <span data-ttu-id="6ebfc-120">示例 1：创建临时文件</span><span class="sxs-lookup"><span data-stu-id="6ebfc-120">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="6ebfc-121">此命令会 `.tmp` 在临时文件夹中生成文件，然后在变量中存储对文件的引用 `$TempFile` 。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-121">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="6ebfc-122">以后可以在脚本中使用此文件。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-122">You can use this file later in your script.</span></span>

## <span data-ttu-id="6ebfc-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ebfc-123">PARAMETERS</span></span>

### <span data-ttu-id="6ebfc-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6ebfc-124">-Confirm</span></span>

<span data-ttu-id="6ebfc-125">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6ebfc-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6ebfc-126">-WhatIf</span></span>

<span data-ttu-id="6ebfc-127">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6ebfc-128">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6ebfc-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ebfc-129">CommonParameters</span></span>

<span data-ttu-id="6ebfc-130">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ebfc-131">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6ebfc-132">输入</span><span class="sxs-lookup"><span data-stu-id="6ebfc-132">INPUTS</span></span>

## <span data-ttu-id="6ebfc-133">输出</span><span class="sxs-lookup"><span data-stu-id="6ebfc-133">OUTPUTS</span></span>

### <span data-ttu-id="6ebfc-134">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="6ebfc-134">System.IO.FileInfo</span></span>

<span data-ttu-id="6ebfc-135">此 cmdlet 返回表示临时文件的 **FileInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="6ebfc-135">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="6ebfc-136">注释</span><span class="sxs-lookup"><span data-stu-id="6ebfc-136">NOTES</span></span>

## <span data-ttu-id="6ebfc-137">相关链接</span><span class="sxs-lookup"><span data-stu-id="6ebfc-137">RELATED LINKS</span></span>

