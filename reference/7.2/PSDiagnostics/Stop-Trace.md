---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597436"
---
# <span data-ttu-id="080a0-102">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="080a0-102">Stop-Trace</span></span>

## <span data-ttu-id="080a0-103">摘要</span><span class="sxs-lookup"><span data-stu-id="080a0-103">SYNOPSIS</span></span>
<span data-ttu-id="080a0-104">停止事件跟踪日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="080a0-104">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="080a0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="080a0-105">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="080a0-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="080a0-106">DESCRIPTION</span></span>

<span data-ttu-id="080a0-107">此 cmdlet 将停止一个 Windows 事件跟踪日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="080a0-107">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="080a0-108">以下 cmdlet 使用此 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="080a0-108">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="080a0-109">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="080a0-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="080a0-110">示例</span><span class="sxs-lookup"><span data-stu-id="080a0-110">EXAMPLES</span></span>

### <span data-ttu-id="080a0-111">示例1：停止 WSMan 跟踪日志记录会话</span><span class="sxs-lookup"><span data-stu-id="080a0-111">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="080a0-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="080a0-112">PARAMETERS</span></span>

### <span data-ttu-id="080a0-113">-ETS</span><span class="sxs-lookup"><span data-stu-id="080a0-113">-ETS</span></span>
<span data-ttu-id="080a0-114">直接将命令发送到事件跟踪会话，无需保存或计划。</span><span class="sxs-lookup"><span data-stu-id="080a0-114">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="080a0-115">-SessionName</span><span class="sxs-lookup"><span data-stu-id="080a0-115">-SessionName</span></span>
<span data-ttu-id="080a0-116">要停止的事件跟踪会话的名称。</span><span class="sxs-lookup"><span data-stu-id="080a0-116">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="080a0-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="080a0-117">CommonParameters</span></span>
<span data-ttu-id="080a0-118">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="080a0-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="080a0-119">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="080a0-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="080a0-120">输入</span><span class="sxs-lookup"><span data-stu-id="080a0-120">INPUTS</span></span>

### <span data-ttu-id="080a0-121">无</span><span class="sxs-lookup"><span data-stu-id="080a0-121">None</span></span>

## <span data-ttu-id="080a0-122">输出</span><span class="sxs-lookup"><span data-stu-id="080a0-122">OUTPUTS</span></span>

### <span data-ttu-id="080a0-123">无</span><span class="sxs-lookup"><span data-stu-id="080a0-123">None</span></span>

## <span data-ttu-id="080a0-124">注释</span><span class="sxs-lookup"><span data-stu-id="080a0-124">NOTES</span></span>

## <span data-ttu-id="080a0-125">相关链接</span><span class="sxs-lookup"><span data-stu-id="080a0-125">RELATED LINKS</span></span>

[<span data-ttu-id="080a0-126">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="080a0-126">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="080a0-127">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="080a0-127">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="080a0-128">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="080a0-128">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="080a0-129">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="080a0-129">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="080a0-130">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="080a0-130">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="080a0-131">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="080a0-131">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

