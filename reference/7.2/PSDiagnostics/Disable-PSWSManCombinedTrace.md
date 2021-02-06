---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 690a8b050fd0e16033a585df210db340f41a83a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596400"
---
# <span data-ttu-id="68018-102">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="68018-102">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="68018-103">摘要</span><span class="sxs-lookup"><span data-stu-id="68018-103">SYNOPSIS</span></span>
<span data-ttu-id="68018-104">停止通过 Enable-PSWSManCombinedTrace 启动的日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="68018-104">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="68018-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="68018-105">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="68018-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="68018-106">DESCRIPTION</span></span>

<span data-ttu-id="68018-107">此 cmdlet 将停止启动的日志记录会话 `Enable-PSWSManCombinedTrace` 。</span><span class="sxs-lookup"><span data-stu-id="68018-107">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="68018-108">此 cmdlet 使用 `Stop-Trace` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68018-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="68018-109">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68018-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="68018-110">示例</span><span class="sxs-lookup"><span data-stu-id="68018-110">EXAMPLES</span></span>

### <span data-ttu-id="68018-111">示例1：禁用合并的日志记录会话</span><span class="sxs-lookup"><span data-stu-id="68018-111">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="68018-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68018-112">PARAMETERS</span></span>

### <span data-ttu-id="68018-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68018-113">CommonParameters</span></span>

<span data-ttu-id="68018-114">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="68018-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="68018-115">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="68018-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="68018-116">输入</span><span class="sxs-lookup"><span data-stu-id="68018-116">INPUTS</span></span>

### <span data-ttu-id="68018-117">无</span><span class="sxs-lookup"><span data-stu-id="68018-117">None</span></span>

## <span data-ttu-id="68018-118">输出</span><span class="sxs-lookup"><span data-stu-id="68018-118">OUTPUTS</span></span>

### <span data-ttu-id="68018-119">无</span><span class="sxs-lookup"><span data-stu-id="68018-119">None</span></span>

## <span data-ttu-id="68018-120">注释</span><span class="sxs-lookup"><span data-stu-id="68018-120">NOTES</span></span>

## <span data-ttu-id="68018-121">相关链接</span><span class="sxs-lookup"><span data-stu-id="68018-121">RELATED LINKS</span></span>

[<span data-ttu-id="68018-122">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="68018-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="68018-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="68018-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="68018-124">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="68018-124">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

