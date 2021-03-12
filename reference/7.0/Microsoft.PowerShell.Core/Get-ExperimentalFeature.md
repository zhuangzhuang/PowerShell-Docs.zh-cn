---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 22e1b21f304129d6912557a5dbc825bc4e6202a1
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193919"
---
# <span data-ttu-id="7787e-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="7787e-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="7787e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="7787e-103">SYNOPSIS</span></span>
<span data-ttu-id="7787e-104">获取实验性功能。</span><span class="sxs-lookup"><span data-stu-id="7787e-104">Gets experimental features.</span></span>

## <span data-ttu-id="7787e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7787e-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7787e-106">说明</span><span class="sxs-lookup"><span data-stu-id="7787e-106">DESCRIPTION</span></span>

<span data-ttu-id="7787e-107">`Get-ExperimentalFeature`Cmdlet 将返回 PowerShell 发现的所有实验性功能。</span><span class="sxs-lookup"><span data-stu-id="7787e-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="7787e-108">实验功能可以来自模块或 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="7787e-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="7787e-109">利用实验功能，用户可以安全地测试新功能，并通过 GitHub) 提供反馈 (在将设计视为已完成之前，任何更改都可能会成为重大更改。</span><span class="sxs-lookup"><span data-stu-id="7787e-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="7787e-110">示例</span><span class="sxs-lookup"><span data-stu-id="7787e-110">EXAMPLES</span></span>

### <span data-ttu-id="7787e-111">示例 1</span><span class="sxs-lookup"><span data-stu-id="7787e-111">Example 1</span></span>

<span data-ttu-id="7787e-112">获取当前注册的实验功能及其当前状态的列表。</span><span class="sxs-lookup"><span data-stu-id="7787e-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="7787e-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7787e-113">PARAMETERS</span></span>

### <span data-ttu-id="7787e-114">-Name</span><span class="sxs-lookup"><span data-stu-id="7787e-114">-Name</span></span>

<span data-ttu-id="7787e-115">要返回的特定实验功能的名称或名称。</span><span class="sxs-lookup"><span data-stu-id="7787e-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7787e-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7787e-116">CommonParameters</span></span>

<span data-ttu-id="7787e-117">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7787e-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7787e-118">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7787e-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7787e-119">输入</span><span class="sxs-lookup"><span data-stu-id="7787e-119">INPUTS</span></span>

### <span data-ttu-id="7787e-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="7787e-120">System.String[]</span></span>

<span data-ttu-id="7787e-121">要返回的实验功能的名称或名称。</span><span class="sxs-lookup"><span data-stu-id="7787e-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="7787e-122">输出</span><span class="sxs-lookup"><span data-stu-id="7787e-122">OUTPUTS</span></span>

### <span data-ttu-id="7787e-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="7787e-123">ExperimentalFeature</span></span>

<span data-ttu-id="7787e-124">如果未指定名称，则返回与请求的名称或所有实验性功能匹配的实例。</span><span class="sxs-lookup"><span data-stu-id="7787e-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="7787e-125">注释</span><span class="sxs-lookup"><span data-stu-id="7787e-125">NOTES</span></span>

## <span data-ttu-id="7787e-126">相关链接</span><span class="sxs-lookup"><span data-stu-id="7787e-126">RELATED LINKS</span></span>

[<span data-ttu-id="7787e-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="7787e-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="7787e-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="7787e-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
