---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597039"
---
# <span data-ttu-id="6e570-102">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="6e570-102">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="6e570-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6e570-103">SYNOPSIS</span></span>
<span data-ttu-id="6e570-104">此函数是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="6e570-104">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="6e570-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6e570-105">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="6e570-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6e570-106">DESCRIPTION</span></span>

<span data-ttu-id="6e570-107">`PSConsoleHostReadLine` 是 PSReadLine 模块的主入口点。</span><span class="sxs-lookup"><span data-stu-id="6e570-107">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="6e570-108">PowerShell 控制台主机会自动加载 PSReadLine 模块并调用此函数。</span><span class="sxs-lookup"><span data-stu-id="6e570-108">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="6e570-109">在正常操作情况下，不应从命令行使用此函数。</span><span class="sxs-lookup"><span data-stu-id="6e570-109">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="6e570-110">扩展点 `PSConsoleHostReadLine` 对于控制台主机是特殊的。</span><span class="sxs-lookup"><span data-stu-id="6e570-110">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="6e570-111">主机将调用具有此名称的任何别名、函数或脚本。</span><span class="sxs-lookup"><span data-stu-id="6e570-111">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="6e570-112">PSReadLine 定义此函数，使其从控制台主机调用。</span><span class="sxs-lookup"><span data-stu-id="6e570-112">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="6e570-113">示例</span><span class="sxs-lookup"><span data-stu-id="6e570-113">EXAMPLES</span></span>

### <span data-ttu-id="6e570-114">示例 1</span><span class="sxs-lookup"><span data-stu-id="6e570-114">Example 1</span></span>

<span data-ttu-id="6e570-115">不应从命令行使用此函数。</span><span class="sxs-lookup"><span data-stu-id="6e570-115">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="6e570-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e570-116">PARAMETERS</span></span>

## <span data-ttu-id="6e570-117">输入</span><span class="sxs-lookup"><span data-stu-id="6e570-117">INPUTS</span></span>

### <span data-ttu-id="6e570-118">无</span><span class="sxs-lookup"><span data-stu-id="6e570-118">None</span></span>

## <span data-ttu-id="6e570-119">输出</span><span class="sxs-lookup"><span data-stu-id="6e570-119">OUTPUTS</span></span>

### <span data-ttu-id="6e570-120">无</span><span class="sxs-lookup"><span data-stu-id="6e570-120">None</span></span>

## <span data-ttu-id="6e570-121">注释</span><span class="sxs-lookup"><span data-stu-id="6e570-121">NOTES</span></span>

## <span data-ttu-id="6e570-122">相关链接</span><span class="sxs-lookup"><span data-stu-id="6e570-122">RELATED LINKS</span></span>

[<span data-ttu-id="6e570-123">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="6e570-123">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

