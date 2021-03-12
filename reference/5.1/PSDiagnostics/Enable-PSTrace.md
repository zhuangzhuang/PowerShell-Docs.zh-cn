---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 2ec01393a46de84b59f06995473bdff6bd5b2b4f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195030"
---
# <span data-ttu-id="045d5-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="045d5-102">Enable-PSTrace</span></span>

## <span data-ttu-id="045d5-103">摘要</span><span class="sxs-lookup"><span data-stu-id="045d5-103">SYNOPSIS</span></span>
<span data-ttu-id="045d5-104">启用 Microsoft Windows PowerShell 事件提供程序日志。</span><span class="sxs-lookup"><span data-stu-id="045d5-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="045d5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="045d5-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="045d5-106">说明</span><span class="sxs-lookup"><span data-stu-id="045d5-106">DESCRIPTION</span></span>

<span data-ttu-id="045d5-107">此 cmdlet 将启用 Microsoft Windows PowerShell 事件提供程序的操作和分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="045d5-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="045d5-108">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="045d5-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="045d5-109">示例</span><span class="sxs-lookup"><span data-stu-id="045d5-109">EXAMPLES</span></span>

### <span data-ttu-id="045d5-110">示例1：为 PowerShell 启用分析事件日志</span><span class="sxs-lookup"><span data-stu-id="045d5-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="045d5-111">下面的示例仅启用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="045d5-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="045d5-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="045d5-112">PARAMETERS</span></span>

### <span data-ttu-id="045d5-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="045d5-113">-AnalyticOnly</span></span>

<span data-ttu-id="045d5-114">使用此参数时，该 cmdlet 将启用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="045d5-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="045d5-115">不会更改操作事件日志。</span><span class="sxs-lookup"><span data-stu-id="045d5-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="045d5-116">-Force</span><span class="sxs-lookup"><span data-stu-id="045d5-116">-Force</span></span>

<span data-ttu-id="045d5-117">用于在不提示的情况下强制更改。</span><span class="sxs-lookup"><span data-stu-id="045d5-117">Used to force the change without prompting.</span></span>

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

## <span data-ttu-id="045d5-118">输入</span><span class="sxs-lookup"><span data-stu-id="045d5-118">INPUTS</span></span>

### <span data-ttu-id="045d5-119">无</span><span class="sxs-lookup"><span data-stu-id="045d5-119">None</span></span>

## <span data-ttu-id="045d5-120">输出</span><span class="sxs-lookup"><span data-stu-id="045d5-120">OUTPUTS</span></span>

### <span data-ttu-id="045d5-121">System.Object</span><span class="sxs-lookup"><span data-stu-id="045d5-121">System.Object</span></span>

## <span data-ttu-id="045d5-122">注释</span><span class="sxs-lookup"><span data-stu-id="045d5-122">NOTES</span></span>

<span data-ttu-id="045d5-123">此 cmdlet 使用 `Get-LogProperties` 和 `Set-LogProperties` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="045d5-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="045d5-124">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="045d5-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="045d5-125">相关链接</span><span class="sxs-lookup"><span data-stu-id="045d5-125">RELATED LINKS</span></span>

[<span data-ttu-id="045d5-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="045d5-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="045d5-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="045d5-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="045d5-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="045d5-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)
