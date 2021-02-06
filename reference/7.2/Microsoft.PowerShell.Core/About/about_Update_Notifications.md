---
description: 启动 PowerShell 时，通知用户已发布新版本的 PowerShell。
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598673"
---
# <a name="about-update-notifications"></a><span data-ttu-id="bc7fe-103">关于更新通知</span><span class="sxs-lookup"><span data-stu-id="bc7fe-103">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="bc7fe-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="bc7fe-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="bc7fe-105">启动 PowerShell 时，通知用户已发布新版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-105">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="bc7fe-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="bc7fe-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="bc7fe-107">从 PowerShell 7.0 开始，PowerShell 使用更新通知来提醒用户是否存在 PowerShell 更新。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-107">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="bc7fe-108">PowerShell 每天查询一次联机服务，以确定是否提供较新版本。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-108">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="bc7fe-109">虽然在给定的24小时内第一次会话期间进行更新检查，但出于性能原因，该通知仅会显示在后续会话开始时。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-109">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="bc7fe-110">此外，出于性能方面的考虑，在会话开始之前至少3秒钟后，检查才会开始。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-110">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="bc7fe-111">默认情况下，PowerShell 订阅两个不同通知通道之一，具体取决于其版本/分支。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-111">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="bc7fe-112">受支持的正式发布 (GA) 版 PowerShell 仅返回已更新 GA 版本的通知。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-112">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="bc7fe-113">预览版和候选发布 (RC) 版本会通知预览版、RC 和 GA 版本的更新。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-113">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="bc7fe-114">可以使用 `POWERSHELL_UPDATECHECK` 环境变量更改更新通知行为。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-114">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="bc7fe-115">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="bc7fe-115">The following values are supported:</span></span>

- <span data-ttu-id="bc7fe-116">`Off` 关闭更新通知功能</span><span class="sxs-lookup"><span data-stu-id="bc7fe-116">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="bc7fe-117">`Default` 与不定义相同 `POWERSHELL_UPDATECHECK` ：</span><span class="sxs-lookup"><span data-stu-id="bc7fe-117">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="bc7fe-118">GA 版本通知 GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="bc7fe-118">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="bc7fe-119">预览版/RC 版本通知 GA 版本和预览版的更新</span><span class="sxs-lookup"><span data-stu-id="bc7fe-119">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="bc7fe-120">`LTS` 仅通知长期服务 (LTS) GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="bc7fe-120">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="bc7fe-121">以下终结点当前用于确定每个通道的最新版本：</span><span class="sxs-lookup"><span data-stu-id="bc7fe-121">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="bc7fe-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="bc7fe-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="bc7fe-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="bc7fe-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="bc7fe-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="bc7fe-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="bc7fe-125">更新通知并不提供自动更新 PowerShell 的任何方式。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-125">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="bc7fe-126">将来，可能有更多指令或功能可从 PowerShell 内部更新，但目前，你应该使用用于安装 PowerShell 的相同安装机制来更新它。</span><span class="sxs-lookup"><span data-stu-id="bc7fe-126">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

