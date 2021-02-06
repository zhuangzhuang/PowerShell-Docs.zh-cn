---
description: 介绍如何使用 "使用 PowerShell 运行" 功能从文件系统驱动器运行脚本。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596663"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="b8630-103">关于在 PowerShell 中运行</span><span class="sxs-lookup"><span data-stu-id="b8630-103">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="b8630-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="b8630-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b8630-105">介绍如何使用 "使用 PowerShell 运行" 功能从文件系统驱动器运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b8630-105">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="b8630-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="b8630-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b8630-107">从 Windows PowerShell 3.0 开始，你可以使用 "使用 PowerShell 运行" 功能，通过 Windows 8 和 Windows Server 2012 和 windows 资源管理器中的 windows 资源管理器在 windows 的早期版本中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b8630-107">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="b8630-108">"使用 PowerShell 运行" 功能旨在运行没有必需参数的脚本，不会将输出返回到命令提示符。</span><span class="sxs-lookup"><span data-stu-id="b8630-108">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="b8630-109">当你使用 "使用 PowerShell 运行" 功能时，PowerShell 控制台窗口仅出现短暂的情况（如果有）。</span><span class="sxs-lookup"><span data-stu-id="b8630-109">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="b8630-110">你无法与它交互。</span><span class="sxs-lookup"><span data-stu-id="b8630-110">You cannot interact with it.</span></span>

<span data-ttu-id="b8630-111">若要使用 "使用 PowerShell 运行" 功能：</span><span class="sxs-lookup"><span data-stu-id="b8630-111">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="b8630-112">在文件资源管理器 (或 Windows 资源管理器) 中，右键单击脚本文件名，然后选择 "用 PowerShell 运行"。</span><span class="sxs-lookup"><span data-stu-id="b8630-112">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="b8630-113">"使用 PowerShell 运行" 功能将启动具有 "绕过" 执行策略的 PowerShell 会话，运行该脚本并关闭会话。</span><span class="sxs-lookup"><span data-stu-id="b8630-113">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="b8630-114">它运行以下格式的命令：</span><span class="sxs-lookup"><span data-stu-id="b8630-114">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="b8630-115">"使用 PowerShell 运行" 设置仅对会话 () 在其中运行脚本的 PowerShell 进程的当前实例的绕过执行策略。</span><span class="sxs-lookup"><span data-stu-id="b8630-115">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="b8630-116">此功能不会更改计算机或用户的执行策略。</span><span class="sxs-lookup"><span data-stu-id="b8630-116">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="b8630-117">"使用 PowerShell 运行" 功能仅受 AllSigned 执行策略的影响。</span><span class="sxs-lookup"><span data-stu-id="b8630-117">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="b8630-118">如果 AllSigned 执行策略对计算机或用户有效，则 "通过 PowerShell 运行" 仅运行签名脚本。</span><span class="sxs-lookup"><span data-stu-id="b8630-118">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="b8630-119">任何其他执行策略都不会影响 "使用 PowerShell 运行"。</span><span class="sxs-lookup"><span data-stu-id="b8630-119">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="b8630-120">有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="b8630-120">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="b8630-121">疑难解答说明： "用 PowerShell 运行" 命令可能会提示您确认执行策略更改。</span><span class="sxs-lookup"><span data-stu-id="b8630-121">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8630-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8630-122">SEE ALSO</span></span>

[<span data-ttu-id="b8630-123">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="b8630-123">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="b8630-124">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="b8630-124">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="b8630-125">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="b8630-125">about_Scripts</span></span>](about_Scripts.md)

