---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: abc820bd6f8f5c8cd8c6301aacee268c82161d7e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596027"
---
# <span data-ttu-id="39536-102">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="39536-102">Get-ComputerInfo</span></span>

## <span data-ttu-id="39536-103">摘要</span><span class="sxs-lookup"><span data-stu-id="39536-103">SYNOPSIS</span></span>
<span data-ttu-id="39536-104">获取系统属性和操作系统属性的合并对象。</span><span class="sxs-lookup"><span data-stu-id="39536-104">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="39536-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="39536-105">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="39536-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="39536-106">DESCRIPTION</span></span>

<span data-ttu-id="39536-107">`Get-ComputerInfo`Cmdlet 将获取系统属性和操作系统属性的合并对象。</span><span class="sxs-lookup"><span data-stu-id="39536-107">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="39536-108">此 cmdlet 是在 Windows PowerShell 5.1 中引入的。</span><span class="sxs-lookup"><span data-stu-id="39536-108">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="39536-109">示例</span><span class="sxs-lookup"><span data-stu-id="39536-109">EXAMPLES</span></span>

### <span data-ttu-id="39536-110">示例1：获取所有计算机属性</span><span class="sxs-lookup"><span data-stu-id="39536-110">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="39536-111">此命令从计算机中获取所有系统属性和操作系统属性。</span><span class="sxs-lookup"><span data-stu-id="39536-111">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="39536-112">示例2：获取所有计算机操作系统属性</span><span class="sxs-lookup"><span data-stu-id="39536-112">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="39536-113">此命令从计算机中获取所有操作系统属性。</span><span class="sxs-lookup"><span data-stu-id="39536-113">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="39536-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="39536-114">PARAMETERS</span></span>

### <span data-ttu-id="39536-115">-Property</span><span class="sxs-lookup"><span data-stu-id="39536-115">-Property</span></span>

<span data-ttu-id="39536-116">以字符串数组的形式指定此 cmdlet 显示的计算机属性。</span><span class="sxs-lookup"><span data-stu-id="39536-116">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="39536-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="39536-117">CommonParameters</span></span>

<span data-ttu-id="39536-118">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="39536-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="39536-119">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="39536-119">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="39536-120">输入</span><span class="sxs-lookup"><span data-stu-id="39536-120">INPUTS</span></span>

### <span data-ttu-id="39536-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="39536-121">System.String[]</span></span>

## <span data-ttu-id="39536-122">输出</span><span class="sxs-lookup"><span data-stu-id="39536-122">OUTPUTS</span></span>

### <span data-ttu-id="39536-123">ComputerInfo。</span><span class="sxs-lookup"><span data-stu-id="39536-123">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="39536-124">注释</span><span class="sxs-lookup"><span data-stu-id="39536-124">NOTES</span></span>

<span data-ttu-id="39536-125">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="39536-125">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="39536-126">相关链接</span><span class="sxs-lookup"><span data-stu-id="39536-126">RELATED LINKS</span></span>
