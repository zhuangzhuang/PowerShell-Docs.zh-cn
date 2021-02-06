---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: df7f9000cf66cebce83e3146cd5c95a7d1a78bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595408"
---
# <span data-ttu-id="410a5-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="410a5-102">New-Guid</span></span>

## <span data-ttu-id="410a5-103">摘要</span><span class="sxs-lookup"><span data-stu-id="410a5-103">SYNOPSIS</span></span>
<span data-ttu-id="410a5-104">创建 GUID。</span><span class="sxs-lookup"><span data-stu-id="410a5-104">Creates a GUID.</span></span>

## <span data-ttu-id="410a5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="410a5-105">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="410a5-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="410a5-106">DESCRIPTION</span></span>

<span data-ttu-id="410a5-107">Guid **)** (guid 创建随机全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="410a5-107">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="410a5-108">如果需要在脚本中使用唯一的 ID，可以根据需要创建一个 GUID。</span><span class="sxs-lookup"><span data-stu-id="410a5-108">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="410a5-109">示例</span><span class="sxs-lookup"><span data-stu-id="410a5-109">EXAMPLES</span></span>

### <span data-ttu-id="410a5-110">示例1：创建 GUID</span><span class="sxs-lookup"><span data-stu-id="410a5-110">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="410a5-111">此命令创建随机 GUID。</span><span class="sxs-lookup"><span data-stu-id="410a5-111">This command creates a random GUID.</span></span>
<span data-ttu-id="410a5-112">或者，你可以将此 cmdlet 的输出存储在一个变量中，以在脚本中的其他位置使用。</span><span class="sxs-lookup"><span data-stu-id="410a5-112">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="410a5-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="410a5-113">PARAMETERS</span></span>

### <span data-ttu-id="410a5-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="410a5-114">CommonParameters</span></span>

<span data-ttu-id="410a5-115">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="410a5-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="410a5-116">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="410a5-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="410a5-117">输入</span><span class="sxs-lookup"><span data-stu-id="410a5-117">INPUTS</span></span>

## <span data-ttu-id="410a5-118">输出</span><span class="sxs-lookup"><span data-stu-id="410a5-118">OUTPUTS</span></span>

### <span data-ttu-id="410a5-119">System.Guid</span><span class="sxs-lookup"><span data-stu-id="410a5-119">System.Guid</span></span>

<span data-ttu-id="410a5-120">此 cmdlet 将返回 GUID。</span><span class="sxs-lookup"><span data-stu-id="410a5-120">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="410a5-121">注释</span><span class="sxs-lookup"><span data-stu-id="410a5-121">NOTES</span></span>

## <span data-ttu-id="410a5-122">相关链接</span><span class="sxs-lookup"><span data-stu-id="410a5-122">RELATED LINKS</span></span>

