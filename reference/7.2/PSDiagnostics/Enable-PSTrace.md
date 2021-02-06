---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596222"
---
# <span data-ttu-id="43a10-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="43a10-102">Enable-PSTrace</span></span>

## <span data-ttu-id="43a10-103">摘要</span><span class="sxs-lookup"><span data-stu-id="43a10-103">SYNOPSIS</span></span>
<span data-ttu-id="43a10-104">启用 Microsoft Windows PowerShell 事件提供程序日志。</span><span class="sxs-lookup"><span data-stu-id="43a10-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="43a10-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43a10-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="43a10-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43a10-106">DESCRIPTION</span></span>

<span data-ttu-id="43a10-107">此 cmdlet 将启用 Microsoft Windows PowerShell 事件提供程序的操作和分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="43a10-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="43a10-108">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43a10-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="43a10-109">示例</span><span class="sxs-lookup"><span data-stu-id="43a10-109">EXAMPLES</span></span>

### <span data-ttu-id="43a10-110">示例1：为 PowerShell 启用分析事件日志</span><span class="sxs-lookup"><span data-stu-id="43a10-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="43a10-111">下面的示例仅启用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="43a10-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="43a10-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43a10-112">PARAMETERS</span></span>

### <span data-ttu-id="43a10-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="43a10-113">-AnalyticOnly</span></span>

<span data-ttu-id="43a10-114">使用此参数时，该 cmdlet 将启用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="43a10-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="43a10-115">不会更改操作事件日志。</span><span class="sxs-lookup"><span data-stu-id="43a10-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="43a10-116">-Force</span><span class="sxs-lookup"><span data-stu-id="43a10-116">-Force</span></span>

<span data-ttu-id="43a10-117">用于在不提示的情况下强制更改。</span><span class="sxs-lookup"><span data-stu-id="43a10-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="43a10-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43a10-118">CommonParameters</span></span>
<span data-ttu-id="43a10-119">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43a10-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43a10-120">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="43a10-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43a10-121">输入</span><span class="sxs-lookup"><span data-stu-id="43a10-121">INPUTS</span></span>

### <span data-ttu-id="43a10-122">无</span><span class="sxs-lookup"><span data-stu-id="43a10-122">None</span></span>

## <span data-ttu-id="43a10-123">输出</span><span class="sxs-lookup"><span data-stu-id="43a10-123">OUTPUTS</span></span>

### <span data-ttu-id="43a10-124">无</span><span class="sxs-lookup"><span data-stu-id="43a10-124">None</span></span>

## <span data-ttu-id="43a10-125">注释</span><span class="sxs-lookup"><span data-stu-id="43a10-125">NOTES</span></span>

<span data-ttu-id="43a10-126">此 cmdlet 使用 `Get-LogProperties` 和 `Set-LogProperties` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43a10-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="43a10-127">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43a10-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="43a10-128">相关链接</span><span class="sxs-lookup"><span data-stu-id="43a10-128">RELATED LINKS</span></span>

[<span data-ttu-id="43a10-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="43a10-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="43a10-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="43a10-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="43a10-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="43a10-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

