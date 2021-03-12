---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 3adfa4be7aae03120d2334a57c39d7e6351bcb16
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196211"
---
# <span data-ttu-id="88e77-103">PSReadLine 模块</span><span class="sxs-lookup"><span data-stu-id="88e77-103">PSReadLine Module</span></span>

## <span data-ttu-id="88e77-104">描述</span><span class="sxs-lookup"><span data-stu-id="88e77-104">Description</span></span>

<span data-ttu-id="88e77-105">PSReadLine 模块包含可用于在 PowerShell 中自定义命令行编辑环境的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="88e77-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="88e77-106">PowerShell 7.1 随附 PSReadLine v 2.1。</span><span class="sxs-lookup"><span data-stu-id="88e77-106">PowerShell 7.1 shipped with PSReadLine v2.1.</span></span> <span data-ttu-id="88e77-107">这些文章介绍了 PSReadLine 2.1 版。</span><span class="sxs-lookup"><span data-stu-id="88e77-107">These articles document PSReadLine v2.1.</span></span>

> [!NOTE]
> <span data-ttu-id="88e77-108">从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="88e77-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="88e77-109">目前，PSReadLine 不能与屏幕阅读器很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="88e77-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="88e77-110">Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。</span><span class="sxs-lookup"><span data-stu-id="88e77-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="88e77-111">如有必要，可以手动加载模块。</span><span class="sxs-lookup"><span data-stu-id="88e77-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="88e77-112">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88e77-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="88e77-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="88e77-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="88e77-114">PSReadLine 的主入口点。</span><span class="sxs-lookup"><span data-stu-id="88e77-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="88e77-115">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88e77-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="88e77-116">获取 PSReadLine 模块的绑定键函数。</span><span class="sxs-lookup"><span data-stu-id="88e77-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="88e77-117">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="88e77-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="88e77-118">获取可配置的选项的值。</span><span class="sxs-lookup"><span data-stu-id="88e77-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="88e77-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="88e77-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="88e77-120">此函数是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="88e77-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="88e77-121">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88e77-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="88e77-122">删除键绑定。</span><span class="sxs-lookup"><span data-stu-id="88e77-122">Removes a key binding.</span></span>

### [<span data-ttu-id="88e77-123">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88e77-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="88e77-124">将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。</span><span class="sxs-lookup"><span data-stu-id="88e77-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="88e77-125">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="88e77-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="88e77-126">自定义 **PSReadLine** 中命令行编辑的行为。</span><span class="sxs-lookup"><span data-stu-id="88e77-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

