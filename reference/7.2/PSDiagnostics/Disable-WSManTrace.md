---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 647a7676eddf2175bf29e02b3482cc9c7c4d8ebe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597040"
---
# <span data-ttu-id="c4d34-102">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c4d34-102">Disable-WSManTrace</span></span>

## <span data-ttu-id="c4d34-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c4d34-103">SYNOPSIS</span></span>
<span data-ttu-id="c4d34-104">停止通过 Enable-WSManTrace 启动的 WSMan 日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="c4d34-104">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="c4d34-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4d34-105">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="c4d34-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c4d34-106">DESCRIPTION</span></span>
<span data-ttu-id="c4d34-107">此 cmdlet 将停止通过 Enable-WSManTrace 启动的 WSMan 日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="c4d34-107">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="c4d34-108">此 cmdlet 使用 `Stop-Trace` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4d34-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="c4d34-109">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4d34-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c4d34-110">示例</span><span class="sxs-lookup"><span data-stu-id="c4d34-110">EXAMPLES</span></span>

### <span data-ttu-id="c4d34-111">示例1：停止 WSMan 跟踪</span><span class="sxs-lookup"><span data-stu-id="c4d34-111">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="c4d34-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4d34-112">PARAMETERS</span></span>

### <span data-ttu-id="c4d34-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4d34-113">CommonParameters</span></span>

<span data-ttu-id="c4d34-114">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c4d34-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4d34-115">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c4d34-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4d34-116">输入</span><span class="sxs-lookup"><span data-stu-id="c4d34-116">INPUTS</span></span>

### <span data-ttu-id="c4d34-117">无</span><span class="sxs-lookup"><span data-stu-id="c4d34-117">None</span></span>

## <span data-ttu-id="c4d34-118">输出</span><span class="sxs-lookup"><span data-stu-id="c4d34-118">OUTPUTS</span></span>

### <span data-ttu-id="c4d34-119">无</span><span class="sxs-lookup"><span data-stu-id="c4d34-119">None</span></span>

## <span data-ttu-id="c4d34-120">注释</span><span class="sxs-lookup"><span data-stu-id="c4d34-120">NOTES</span></span>

## <span data-ttu-id="c4d34-121">相关链接</span><span class="sxs-lookup"><span data-stu-id="c4d34-121">RELATED LINKS</span></span>

[<span data-ttu-id="c4d34-122">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="c4d34-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c4d34-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="c4d34-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="c4d34-124">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c4d34-124">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

