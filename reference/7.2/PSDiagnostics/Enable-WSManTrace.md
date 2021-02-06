---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595619"
---
# <span data-ttu-id="0cb21-102">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="0cb21-102">Enable-WSManTrace</span></span>

## <span data-ttu-id="0cb21-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0cb21-103">SYNOPSIS</span></span>
<span data-ttu-id="0cb21-104">启动启用了 WSMan 提供程序的日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="0cb21-104">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="0cb21-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0cb21-105">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="0cb21-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0cb21-106">DESCRIPTION</span></span>
<span data-ttu-id="0cb21-107">此 cmdlet 将启动启用了 WSMan 提供程序的日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="0cb21-107">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="0cb21-108">启用以下事件提供程序：</span><span class="sxs-lookup"><span data-stu-id="0cb21-108">The following event providers are enabled:</span></span>

- <span data-ttu-id="0cb21-109">事件转发</span><span class="sxs-lookup"><span data-stu-id="0cb21-109">Event Forwarding</span></span>
- <span data-ttu-id="0cb21-110">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="0cb21-110">IpmiDrv</span></span>
- <span data-ttu-id="0cb21-111">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="0cb21-111">IPMIPrv</span></span>
- <span data-ttu-id="0cb21-112">WinRM</span><span class="sxs-lookup"><span data-stu-id="0cb21-112">WinRM</span></span>
- <span data-ttu-id="0cb21-113">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="0cb21-113">WinrsCmd</span></span>
- <span data-ttu-id="0cb21-114">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="0cb21-114">WinrsExe</span></span>
- <span data-ttu-id="0cb21-115">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="0cb21-115">WinrsMgr</span></span>
- <span data-ttu-id="0cb21-116">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="0cb21-116">WSManProvHost</span></span>

<span data-ttu-id="0cb21-117">会话名为 "wsmlog"。</span><span class="sxs-lookup"><span data-stu-id="0cb21-117">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="0cb21-118">此 cmdlet 使用 `Start-Trace` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0cb21-118">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="0cb21-119">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0cb21-119">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="0cb21-120">示例</span><span class="sxs-lookup"><span data-stu-id="0cb21-120">EXAMPLES</span></span>

### <span data-ttu-id="0cb21-121">示例1：启动 WSMan 日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="0cb21-121">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="0cb21-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0cb21-122">PARAMETERS</span></span>

### <span data-ttu-id="0cb21-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0cb21-123">CommonParameters</span></span>

<span data-ttu-id="0cb21-124">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0cb21-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0cb21-125">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0cb21-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0cb21-126">输入</span><span class="sxs-lookup"><span data-stu-id="0cb21-126">INPUTS</span></span>

### <span data-ttu-id="0cb21-127">无</span><span class="sxs-lookup"><span data-stu-id="0cb21-127">None</span></span>

## <span data-ttu-id="0cb21-128">输出</span><span class="sxs-lookup"><span data-stu-id="0cb21-128">OUTPUTS</span></span>

### <span data-ttu-id="0cb21-129">无</span><span class="sxs-lookup"><span data-stu-id="0cb21-129">None</span></span>

## <span data-ttu-id="0cb21-130">注释</span><span class="sxs-lookup"><span data-stu-id="0cb21-130">NOTES</span></span>

## <span data-ttu-id="0cb21-131">相关链接</span><span class="sxs-lookup"><span data-stu-id="0cb21-131">RELATED LINKS</span></span>

[<span data-ttu-id="0cb21-132">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="0cb21-132">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="0cb21-133">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="0cb21-133">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="0cb21-134">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="0cb21-134">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

