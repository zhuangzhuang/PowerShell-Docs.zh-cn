---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 0e246a0e3737f4ed693ed31096fc76e878a4af54
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598903"
---
# <span data-ttu-id="d380c-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d380c-102">Disable-PSTrace</span></span>

## <span data-ttu-id="d380c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d380c-103">SYNOPSIS</span></span>
<span data-ttu-id="d380c-104">禁用 Microsoft Windows PowerShell 事件提供程序日志。</span><span class="sxs-lookup"><span data-stu-id="d380c-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="d380c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d380c-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="d380c-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d380c-106">DESCRIPTION</span></span>

<span data-ttu-id="d380c-107">此 cmdlet 将禁用 Microsoft Windows PowerShell 事件提供程序的操作和分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="d380c-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="d380c-108">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d380c-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d380c-109">示例</span><span class="sxs-lookup"><span data-stu-id="d380c-109">EXAMPLES</span></span>

### <span data-ttu-id="d380c-110">示例1：禁用 PowerShell 的分析事件日志</span><span class="sxs-lookup"><span data-stu-id="d380c-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="d380c-111">下面的示例仅禁用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="d380c-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="d380c-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d380c-112">PARAMETERS</span></span>

### <span data-ttu-id="d380c-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="d380c-113">-AnalyticOnly</span></span>

<span data-ttu-id="d380c-114">使用此参数时，该 cmdlet 将禁用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="d380c-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="d380c-115">不会更改操作事件日志。</span><span class="sxs-lookup"><span data-stu-id="d380c-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="d380c-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d380c-116">CommonParameters</span></span>
<span data-ttu-id="d380c-117">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d380c-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d380c-118">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d380c-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d380c-119">输入</span><span class="sxs-lookup"><span data-stu-id="d380c-119">INPUTS</span></span>

### <span data-ttu-id="d380c-120">无</span><span class="sxs-lookup"><span data-stu-id="d380c-120">None</span></span>

## <span data-ttu-id="d380c-121">输出</span><span class="sxs-lookup"><span data-stu-id="d380c-121">OUTPUTS</span></span>

### <span data-ttu-id="d380c-122">无</span><span class="sxs-lookup"><span data-stu-id="d380c-122">None</span></span>

## <span data-ttu-id="d380c-123">注释</span><span class="sxs-lookup"><span data-stu-id="d380c-123">NOTES</span></span>

<span data-ttu-id="d380c-124">此 cmdlet 使用 `Get-LogProperties` 和 `Set-LogProperties` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d380c-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="d380c-125">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d380c-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d380c-126">相关链接</span><span class="sxs-lookup"><span data-stu-id="d380c-126">RELATED LINKS</span></span>

[<span data-ttu-id="d380c-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d380c-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="d380c-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d380c-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="d380c-129">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d380c-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)

