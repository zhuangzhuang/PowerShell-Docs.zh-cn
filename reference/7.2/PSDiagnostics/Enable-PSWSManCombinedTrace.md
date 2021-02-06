---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603596"
---
# <span data-ttu-id="29f14-102">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="29f14-102">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="29f14-103">摘要</span><span class="sxs-lookup"><span data-stu-id="29f14-103">SYNOPSIS</span></span>
<span data-ttu-id="29f14-104">启用启用了 WSMan 和 PowerShell 提供程序的日志记录会话。</span><span class="sxs-lookup"><span data-stu-id="29f14-104">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="29f14-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29f14-105">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="29f14-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="29f14-106">DESCRIPTION</span></span>

<span data-ttu-id="29f14-107">此 cmdlet 将启动启用以下 PowerShell 提供程序的日志记录会话：</span><span class="sxs-lookup"><span data-stu-id="29f14-107">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="29f14-108">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="29f14-108">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="29f14-109">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="29f14-109">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="29f14-110">会话名为 "PSTrace"。</span><span class="sxs-lookup"><span data-stu-id="29f14-110">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="29f14-111">此 cmdlet 使用 `Start-Trace` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29f14-111">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="29f14-112">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29f14-112">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="29f14-113">示例</span><span class="sxs-lookup"><span data-stu-id="29f14-113">EXAMPLES</span></span>

### <span data-ttu-id="29f14-114">示例1：启动合并的日志记录会话</span><span class="sxs-lookup"><span data-stu-id="29f14-114">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="29f14-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29f14-115">PARAMETERS</span></span>

### <span data-ttu-id="29f14-116">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="29f14-116">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="29f14-117">默认情况下，事件写入 "$pshome \Traces\PSTrace.etl"。</span><span class="sxs-lookup"><span data-stu-id="29f14-117">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="29f14-118">使用此参数时，该 cmdlet 将创建一个唯一的文件名： "$pshome \Traces\ PSTrace_ {guid} .etl"</span><span class="sxs-lookup"><span data-stu-id="29f14-118">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="29f14-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29f14-119">CommonParameters</span></span>

<span data-ttu-id="29f14-120">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="29f14-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29f14-121">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="29f14-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29f14-122">输入</span><span class="sxs-lookup"><span data-stu-id="29f14-122">INPUTS</span></span>

### <span data-ttu-id="29f14-123">无</span><span class="sxs-lookup"><span data-stu-id="29f14-123">None</span></span>

## <span data-ttu-id="29f14-124">输出</span><span class="sxs-lookup"><span data-stu-id="29f14-124">OUTPUTS</span></span>

### <span data-ttu-id="29f14-125">无</span><span class="sxs-lookup"><span data-stu-id="29f14-125">None</span></span>

## <span data-ttu-id="29f14-126">注释</span><span class="sxs-lookup"><span data-stu-id="29f14-126">NOTES</span></span>

## <span data-ttu-id="29f14-127">相关链接</span><span class="sxs-lookup"><span data-stu-id="29f14-127">RELATED LINKS</span></span>

[<span data-ttu-id="29f14-128">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="29f14-128">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="29f14-129">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="29f14-129">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="29f14-130">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="29f14-130">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

