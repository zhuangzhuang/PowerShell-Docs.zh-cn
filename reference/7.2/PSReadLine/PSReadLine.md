---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595817"
---
# <span data-ttu-id="7ec45-102">PSReadLine 模块</span><span class="sxs-lookup"><span data-stu-id="7ec45-102">PSReadLine Module</span></span>

## <span data-ttu-id="7ec45-103">说明</span><span class="sxs-lookup"><span data-stu-id="7ec45-103">Description</span></span>

<span data-ttu-id="7ec45-104">PSReadLine 模块包含可用于在 PowerShell 中自定义命令行编辑环境的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ec45-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="7ec45-105">这些文章介绍了 PSReadLine v2.0。</span><span class="sxs-lookup"><span data-stu-id="7ec45-105">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="7ec45-106">此版本随附于 PowerShell v6 和 Windows 10 10 月2018更新 (生成 1809) 。</span><span class="sxs-lookup"><span data-stu-id="7ec45-106">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="7ec45-107">从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="7ec45-107">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="7ec45-108">目前，PSReadLine 不能与屏幕阅读器很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="7ec45-108">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="7ec45-109">Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。</span><span class="sxs-lookup"><span data-stu-id="7ec45-109">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="7ec45-110">如有必要，可以手动加载模块。</span><span class="sxs-lookup"><span data-stu-id="7ec45-110">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="7ec45-111">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ec45-111">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="7ec45-112">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="7ec45-112">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="7ec45-113">PSReadLine 的主入口点。</span><span class="sxs-lookup"><span data-stu-id="7ec45-113">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="7ec45-114">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ec45-114">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="7ec45-115">获取 PSReadLine 模块的绑定键函数。</span><span class="sxs-lookup"><span data-stu-id="7ec45-115">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="7ec45-116">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7ec45-116">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="7ec45-117">获取可配置的选项的值。</span><span class="sxs-lookup"><span data-stu-id="7ec45-117">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="7ec45-118">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="7ec45-118">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="7ec45-119">此函数是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="7ec45-119">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="7ec45-120">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ec45-120">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="7ec45-121">删除键绑定。</span><span class="sxs-lookup"><span data-stu-id="7ec45-121">Removes a key binding.</span></span>

### [<span data-ttu-id="7ec45-122">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ec45-122">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="7ec45-123">将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。</span><span class="sxs-lookup"><span data-stu-id="7ec45-123">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="7ec45-124">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7ec45-124">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="7ec45-125">自定义 **PSReadLine** 中命令行编辑的行为。</span><span class="sxs-lookup"><span data-stu-id="7ec45-125">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

