---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194520"
---
# <span data-ttu-id="48104-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="48104-102">Disable-PSTrace</span></span>

## <span data-ttu-id="48104-103">摘要</span><span class="sxs-lookup"><span data-stu-id="48104-103">SYNOPSIS</span></span>
<span data-ttu-id="48104-104">禁用 Microsoft Windows PowerShell 事件提供程序日志。</span><span class="sxs-lookup"><span data-stu-id="48104-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="48104-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="48104-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="48104-106">说明</span><span class="sxs-lookup"><span data-stu-id="48104-106">DESCRIPTION</span></span>

<span data-ttu-id="48104-107">此 cmdlet 将禁用 Microsoft Windows PowerShell 事件提供程序的操作和分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="48104-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="48104-108">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="48104-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="48104-109">示例</span><span class="sxs-lookup"><span data-stu-id="48104-109">EXAMPLES</span></span>

### <span data-ttu-id="48104-110">示例1：禁用 PowerShell 的分析事件日志</span><span class="sxs-lookup"><span data-stu-id="48104-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="48104-111">下面的示例仅禁用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="48104-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="48104-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="48104-112">PARAMETERS</span></span>

### <span data-ttu-id="48104-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="48104-113">-AnalyticOnly</span></span>

<span data-ttu-id="48104-114">使用此参数时，该 cmdlet 将禁用 Microsoft Windows PowerShell 提供程序的分析事件日志。</span><span class="sxs-lookup"><span data-stu-id="48104-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="48104-115">不会更改操作事件日志。</span><span class="sxs-lookup"><span data-stu-id="48104-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="48104-116">输入</span><span class="sxs-lookup"><span data-stu-id="48104-116">INPUTS</span></span>

### <span data-ttu-id="48104-117">无</span><span class="sxs-lookup"><span data-stu-id="48104-117">None</span></span>

## <span data-ttu-id="48104-118">输出</span><span class="sxs-lookup"><span data-stu-id="48104-118">OUTPUTS</span></span>

### <span data-ttu-id="48104-119">System.Object</span><span class="sxs-lookup"><span data-stu-id="48104-119">System.Object</span></span>

## <span data-ttu-id="48104-120">注释</span><span class="sxs-lookup"><span data-stu-id="48104-120">NOTES</span></span>

<span data-ttu-id="48104-121">此 cmdlet 使用 `Get-LogProperties` 和 `Set-LogProperties` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="48104-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="48104-122">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="48104-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="48104-123">相关链接</span><span class="sxs-lookup"><span data-stu-id="48104-123">RELATED LINKS</span></span>

[<span data-ttu-id="48104-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="48104-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="48104-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="48104-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="48104-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="48104-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
