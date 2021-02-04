---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: f59cc9ff4e6d1b6579292c84f440bbbdd156b65c
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098557"
---
# <span data-ttu-id="968ec-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="968ec-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="968ec-103">摘要</span><span class="sxs-lookup"><span data-stu-id="968ec-103">SYNOPSIS</span></span>
<span data-ttu-id="968ec-104">清除回收站的内容。</span><span class="sxs-lookup"><span data-stu-id="968ec-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="968ec-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="968ec-105">SYNTAX</span></span>

### <span data-ttu-id="968ec-106">全部</span><span class="sxs-lookup"><span data-stu-id="968ec-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="968ec-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="968ec-107">DESCRIPTION</span></span>

<span data-ttu-id="968ec-108">`Clear-RecycleBin`Cmdlet 删除计算机回收站的内容。</span><span class="sxs-lookup"><span data-stu-id="968ec-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="968ec-109">此操作类似于使用 Windows **空回收站**。</span><span class="sxs-lookup"><span data-stu-id="968ec-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

## <span data-ttu-id="968ec-110">示例</span><span class="sxs-lookup"><span data-stu-id="968ec-110">EXAMPLES</span></span>

### <span data-ttu-id="968ec-111">1：清除所有回收站</span><span class="sxs-lookup"><span data-stu-id="968ec-111">1: Clear all recycle bins</span></span>

<span data-ttu-id="968ec-112">在此示例中，所有本地计算机的回收站都将被清除。</span><span class="sxs-lookup"><span data-stu-id="968ec-112">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="968ec-113">`Clear-RecycleBin` 提示用户确认是否要清除本地计算机上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-113">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="968ec-114">2：清除指定的回收站</span><span class="sxs-lookup"><span data-stu-id="968ec-114">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="968ec-115">此示例将为指定驱动器号清除回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-115">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="968ec-116">`Clear-RecycleBin` 使用 **驱动器号** 参数在 **C** 卷上指定回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-116">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="968ec-117">系统将提示用户进行确认以运行该命令。</span><span class="sxs-lookup"><span data-stu-id="968ec-117">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="968ec-118">3：清除所有回收站而不进行确认</span><span class="sxs-lookup"><span data-stu-id="968ec-118">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="968ec-119">此示例不会提示确认是否要清除本地计算机的回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-119">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="968ec-120">`Clear-RecycleBin` 使用 **Force** 参数，而不提示用户确认清除本地计算机上的所有回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-120">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="968ec-121">替代方法是将替换 `-Force` 为 `-Confirm:$false` 。</span><span class="sxs-lookup"><span data-stu-id="968ec-121">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="968ec-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="968ec-122">PARAMETERS</span></span>

### <span data-ttu-id="968ec-123">-驱动器号</span><span class="sxs-lookup"><span data-stu-id="968ec-123">-DriveLetter</span></span>

<span data-ttu-id="968ec-124">指定为单个驱动器号或驱动器号数组清除的回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-124">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="968ec-125">-Force</span><span class="sxs-lookup"><span data-stu-id="968ec-125">-Force</span></span>

<span data-ttu-id="968ec-126">指定不提示用户确认是否要清除回收站。</span><span class="sxs-lookup"><span data-stu-id="968ec-126">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="968ec-127">**Force** 参数还会替代 **WhatIf** 和 **Confirm** 参数。</span><span class="sxs-lookup"><span data-stu-id="968ec-127">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="968ec-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="968ec-128">-Confirm</span></span>

<span data-ttu-id="968ec-129">在运行 cmdlet 之前提示用户进行确认。</span><span class="sxs-lookup"><span data-stu-id="968ec-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="968ec-130">即使未指定 **Confirm** 参数，也会提示用户进行确认。</span><span class="sxs-lookup"><span data-stu-id="968ec-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="968ec-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="968ec-131">-WhatIf</span></span>

<span data-ttu-id="968ec-132">显示运行时将发生 `Clear-RecycleBin` 的情况。</span><span class="sxs-lookup"><span data-stu-id="968ec-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="968ec-133">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="968ec-133">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="968ec-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="968ec-134">CommonParameters</span></span>

<span data-ttu-id="968ec-135">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="968ec-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="968ec-136">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="968ec-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="968ec-137">输入</span><span class="sxs-lookup"><span data-stu-id="968ec-137">INPUTS</span></span>

## <span data-ttu-id="968ec-138">输出</span><span class="sxs-lookup"><span data-stu-id="968ec-138">OUTPUTS</span></span>

### <span data-ttu-id="968ec-139">无</span><span class="sxs-lookup"><span data-stu-id="968ec-139">None</span></span>

## <span data-ttu-id="968ec-140">注释</span><span class="sxs-lookup"><span data-stu-id="968ec-140">NOTES</span></span>

## <span data-ttu-id="968ec-141">相关链接</span><span class="sxs-lookup"><span data-stu-id="968ec-141">RELATED LINKS</span></span>
