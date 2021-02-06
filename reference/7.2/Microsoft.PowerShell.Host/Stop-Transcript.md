---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595626"
---
# <span data-ttu-id="1d28b-102">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="1d28b-102">Stop-Transcript</span></span>

## <span data-ttu-id="1d28b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1d28b-103">SYNOPSIS</span></span>
<span data-ttu-id="1d28b-104">停止脚本。</span><span class="sxs-lookup"><span data-stu-id="1d28b-104">Stops a transcript.</span></span>

## <span data-ttu-id="1d28b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1d28b-105">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="1d28b-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1d28b-106">DESCRIPTION</span></span>

<span data-ttu-id="1d28b-107">`Stop-Transcript`Cmdlet 可停止 cmdlet 启动的脚本 `Start-Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="1d28b-107">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="1d28b-108">或者，您可以结束会话来停止脚本。</span><span class="sxs-lookup"><span data-stu-id="1d28b-108">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="1d28b-109">示例</span><span class="sxs-lookup"><span data-stu-id="1d28b-109">EXAMPLES</span></span>

### <span data-ttu-id="1d28b-110">示例1：停止所有脚本</span><span class="sxs-lookup"><span data-stu-id="1d28b-110">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="1d28b-111">此命令停止所有脚本。</span><span class="sxs-lookup"><span data-stu-id="1d28b-111">This command stops all transcripts.</span></span>

## <span data-ttu-id="1d28b-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d28b-112">PARAMETERS</span></span>

### <span data-ttu-id="1d28b-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d28b-113">CommonParameters</span></span>

<span data-ttu-id="1d28b-114">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1d28b-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d28b-115">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1d28b-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d28b-116">输入</span><span class="sxs-lookup"><span data-stu-id="1d28b-116">INPUTS</span></span>

### <span data-ttu-id="1d28b-117">无</span><span class="sxs-lookup"><span data-stu-id="1d28b-117">None</span></span>

<span data-ttu-id="1d28b-118">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1d28b-118">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1d28b-119">输出</span><span class="sxs-lookup"><span data-stu-id="1d28b-119">OUTPUTS</span></span>

### <span data-ttu-id="1d28b-120">System.String</span><span class="sxs-lookup"><span data-stu-id="1d28b-120">System.String</span></span>

<span data-ttu-id="1d28b-121">此 cmdlet 将返回一个字符串，其中包含状态消息和输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="1d28b-121">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="1d28b-122">注释</span><span class="sxs-lookup"><span data-stu-id="1d28b-122">NOTES</span></span>

* <span data-ttu-id="1d28b-123">如果尚未启动脚本，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="1d28b-123">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="1d28b-124">相关链接</span><span class="sxs-lookup"><span data-stu-id="1d28b-124">RELATED LINKS</span></span>

[<span data-ttu-id="1d28b-125">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="1d28b-125">Start-Transcript</span></span>](Start-Transcript.md)

