---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193908"
---
# <span data-ttu-id="cffb3-102">PSReadLine 模块</span><span class="sxs-lookup"><span data-stu-id="cffb3-102">PSReadLine Module</span></span>

## <span data-ttu-id="cffb3-103">描述</span><span class="sxs-lookup"><span data-stu-id="cffb3-103">Description</span></span>

<span data-ttu-id="cffb3-104">PSReadLine 模块包含可用于在 PowerShell 中自定义命令行编辑环境的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cffb3-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="cffb3-105">这些文章介绍了 PSReadLine v 2.2.0 的当前 beta 版本。</span><span class="sxs-lookup"><span data-stu-id="cffb3-105">These articles document the current beta version of PSReadLine v2.2.0.</span></span>

> [!NOTE]
> <span data-ttu-id="cffb3-106">从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="cffb3-106">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="cffb3-107">目前，PSReadLine 不能与屏幕阅读器很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="cffb3-107">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="cffb3-108">Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。</span><span class="sxs-lookup"><span data-stu-id="cffb3-108">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="cffb3-109">如有必要，可以手动加载模块。</span><span class="sxs-lookup"><span data-stu-id="cffb3-109">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="cffb3-110">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cffb3-110">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="cffb3-111">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="cffb3-111">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="cffb3-112">PSReadLine 的主入口点。</span><span class="sxs-lookup"><span data-stu-id="cffb3-112">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="cffb3-113">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cffb3-113">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="cffb3-114">获取 PSReadLine 模块的绑定键函数。</span><span class="sxs-lookup"><span data-stu-id="cffb3-114">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="cffb3-115">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="cffb3-115">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="cffb3-116">获取可配置的选项的值。</span><span class="sxs-lookup"><span data-stu-id="cffb3-116">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="cffb3-117">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="cffb3-117">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="cffb3-118">此函数是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="cffb3-118">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="cffb3-119">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cffb3-119">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="cffb3-120">删除键绑定。</span><span class="sxs-lookup"><span data-stu-id="cffb3-120">Removes a key binding.</span></span>

### [<span data-ttu-id="cffb3-121">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cffb3-121">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="cffb3-122">将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。</span><span class="sxs-lookup"><span data-stu-id="cffb3-122">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="cffb3-123">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="cffb3-123">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="cffb3-124">自定义 **PSReadLine** 中命令行编辑的行为。</span><span class="sxs-lookup"><span data-stu-id="cffb3-124">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

