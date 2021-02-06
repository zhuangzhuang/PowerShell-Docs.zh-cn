---
description: 提供有关 PowerShell 会话以及它们在远程命令中扮演的角色的详细信息。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 79340e5d0ae1fe047f1f37bdfdbb1bebe920d851
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596838"
---
# <a name="about-pssession-details"></a><span data-ttu-id="c137f-103">关于 PSSession 详细信息</span><span class="sxs-lookup"><span data-stu-id="c137f-103">About PSSession Details</span></span>

## <a name="short-description"></a><span data-ttu-id="c137f-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="c137f-104">Short Description</span></span>
<span data-ttu-id="c137f-105">提供有关 PowerShell 会话以及它们在远程命令中扮演的角色的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c137f-105">Provides detailed information about PowerShell sessions and the role they play in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="c137f-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="c137f-106">Long Description</span></span>

<span data-ttu-id="c137f-107">会话是 PowerShell 运行的环境。</span><span class="sxs-lookup"><span data-stu-id="c137f-107">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="c137f-108">每次启动 PowerShell 时都会创建一个会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-108">A session is created for you whenever you start PowerShell.</span></span> <span data-ttu-id="c137f-109">你可以在你的计算机或另一台计算机上创建名为 "PowerShell 会话" 或 "Pssession" 的其他会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-109">You can create additional sessions, called "PowerShell sessions" or "PSSessions" on your computer or another computer.</span></span>

<span data-ttu-id="c137f-110">与 PowerShell 为你创建的会话不同，你可以控制和管理你创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-110">Unlike the sessions that PowerShell creates for you, you control and manage the PSSessions that you create.</span></span>

<span data-ttu-id="c137f-111">Pssession 在远程计算中扮演着重要的角色。</span><span class="sxs-lookup"><span data-stu-id="c137f-111">PSSessions play an important role in remote computing.</span></span> <span data-ttu-id="c137f-112">创建连接到远程计算机的 PSSession 时，PowerShell 将建立与远程计算机的持久连接，以支持 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-112">When you create a PSSession that is connected to a remote computer, PowerShell establishes a persistent connection to the remote computer to support the PSSession.</span></span> <span data-ttu-id="c137f-113">可以使用 PSSession 运行一系列用于共享数据的命令、函数和脚本。</span><span class="sxs-lookup"><span data-stu-id="c137f-113">You can use the PSSession to run a series of commands, functions, and scripts that share data.</span></span>

<span data-ttu-id="c137f-114">本主题提供有关 PowerShell 中的会话和 Pssession 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c137f-114">This topic provides detailed information about sessions and PSSessions in PowerShell.</span></span> <span data-ttu-id="c137f-115">有关可对会话执行的任务的基本信息，请参阅 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="c137f-115">For basic information about the tasks that you can perform with sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="about-sessions"></a><span data-ttu-id="c137f-116">关于会话</span><span class="sxs-lookup"><span data-stu-id="c137f-116">About Sessions</span></span>

<span data-ttu-id="c137f-117">从技术上讲，会话是运行 PowerShell 的执行环境。</span><span class="sxs-lookup"><span data-stu-id="c137f-117">Technically, a session is an execution environment in which PowerShell runs.</span></span> <span data-ttu-id="c137f-118">每个会话都包括一个系统管理组件的实例和一个 PowerShell 运行的主机程序。</span><span class="sxs-lookup"><span data-stu-id="c137f-118">Each session includes an instance of the System.Management.Automation engine and a host program in which PowerShell runs.</span></span> <span data-ttu-id="c137f-119">主机可以是熟悉的 PowerShell 控制台，也可以是运行命令的其他程序，如 Cmd.exe 或生成的程序（例如 Windows PowerShell 集成脚本环境 (ISE) ）。</span><span class="sxs-lookup"><span data-stu-id="c137f-119">The host can be the familiar PowerShell console or another program that runs commands, such as Cmd.exe, or a program built to host PowerShell, such as Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c137f-120">从 Windows 的角度来看，会话是目标计算机上的 Windows 进程。</span><span class="sxs-lookup"><span data-stu-id="c137f-120">From a Windows perspective, a session is a Windows process on the target computer.</span></span>

<span data-ttu-id="c137f-121">每个会话都是单独配置的。</span><span class="sxs-lookup"><span data-stu-id="c137f-121">Each session is configured independently.</span></span> <span data-ttu-id="c137f-122">它包含其自身的属性、其自身的执行策略和自己的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c137f-122">It includes its own properties, its own execution policy, and its own profiles.</span></span> <span data-ttu-id="c137f-123">即使您在计算机上更改了环境，在创建会话时存在的环境仍会持续保持其生存期。</span><span class="sxs-lookup"><span data-stu-id="c137f-123">The environment that exists when the session is created persists for its lifetime even if you change the environment on the computer.</span></span> <span data-ttu-id="c137f-124">所有会话都在全局作用域中创建，甚至是在脚本中创建的会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-124">All sessions are created in a global scope, even sessions that you create in a script.</span></span>

<span data-ttu-id="c137f-125">一次只能在一个会话中运行一个命令 (或命令管道) 。</span><span class="sxs-lookup"><span data-stu-id="c137f-125">You can run only one command (or command pipeline) in a session at one time.</span></span> <span data-ttu-id="c137f-126">第二个命令 (同步运行一次，) 最多需要四分钟才能完成第一个命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-126">A second command run synchronously (one at a time) waits up to four minutes for the first command to be completed.</span></span> <span data-ttu-id="c137f-127">第二个命令异步运行 (同时) 失败。</span><span class="sxs-lookup"><span data-stu-id="c137f-127">A second command run asynchronously (concurrently) fails.</span></span>

## <a name="about-pssessions"></a><span data-ttu-id="c137f-128">关于 Pssession</span><span class="sxs-lookup"><span data-stu-id="c137f-128">About PSSessions</span></span>

<span data-ttu-id="c137f-129">每次启动 PowerShell 时都会创建一个会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-129">A session is created each time that you start PowerShell.</span></span> <span data-ttu-id="c137f-130">PowerShell 会创建临时会话来运行单个命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-130">And, PowerShell creates temporary sessions to run individual commands.</span></span>
<span data-ttu-id="c137f-131">但是，你还可以创建 (名为 "PowerShell 会话" 或 "Pssession" ) 的会话，你可以对其进行控制和管理。</span><span class="sxs-lookup"><span data-stu-id="c137f-131">However, you can also create sessions (called "PowerShell sessions" or "PSSessions") that you control and manage.</span></span>

<span data-ttu-id="c137f-132">Pssession 对于远程命令至关重要。</span><span class="sxs-lookup"><span data-stu-id="c137f-132">PSSessions are critical to remote commands.</span></span> <span data-ttu-id="c137f-133">如果使用或 cmdlet 的 **ComputerName** 参数 `Invoke-Command` ，则 `Enter-PSSession` PowerShell 会建立一个临时会话来运行命令，然后在命令或交互式会话完成后立即关闭会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-133">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlets, PowerShell establishes a temporary session to run the command and then closes the session as soon as the command or the interactive session is complete.</span></span>

<span data-ttu-id="c137f-134">但是，如果使用 `New-PSSession` cmdlet 创建 PSSession，则 PowerShell 将在远程计算机上建立一个持久会话，在该会话中可以运行多个命令或交互会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-134">However, if you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent session on the remote computer in which you can run multiple commands or interactive sessions.</span></span> <span data-ttu-id="c137f-135">你创建的 Pssession 将保持打开状态并可供使用，直到你将其删除或在你关闭创建它们的会话之前使用。</span><span class="sxs-lookup"><span data-stu-id="c137f-135">The PSSessions that you create remain open and available for use until you delete them or until you close the session in which they were created.</span></span>

<span data-ttu-id="c137f-136">在远程计算机上创建 PSSession 时，系统会在远程计算机上创建一个 PowerShell 进程，并建立从本地计算机到远程计算机上的进程的连接。</span><span class="sxs-lookup"><span data-stu-id="c137f-136">When you create a PSSession on a remote computer, the system creates a PowerShell process on the remote computer and establishes a connection from the local computer to the process on the remote computer.</span></span> <span data-ttu-id="c137f-137">在本地计算机上创建 PSSession 时，将在本地计算机上创建新的进程和连接。</span><span class="sxs-lookup"><span data-stu-id="c137f-137">When you create a PSSession on the local computer, both the new process and the connections are created on the local computer.</span></span>

## <a name="when-do-i-need-a-pssession"></a><span data-ttu-id="c137f-138">何时需要 PSSession？</span><span class="sxs-lookup"><span data-stu-id="c137f-138">When Do I Need a PSSession?</span></span>

<span data-ttu-id="c137f-139">`Invoke-Command`和 `Enter-PSSession` Cmdlet 具有 **ComputerName** 和 **Session** 参数。</span><span class="sxs-lookup"><span data-stu-id="c137f-139">The `Invoke-Command` and `Enter-PSSession` cmdlets have both **ComputerName** and **Session** parameters.</span></span> <span data-ttu-id="c137f-140">可以使用运行远程命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-140">You can use either to run a remote command.</span></span>

<span data-ttu-id="c137f-141">使用 **ComputerName** 参数在一台或多台计算机上运行单个命令或一系列不相关的命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-141">Use the **ComputerName** parameter to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="c137f-142">若要运行共享数据的命令，需要与远程计算机建立持久连接。</span><span class="sxs-lookup"><span data-stu-id="c137f-142">To run commands that share data, you need a persistent connection to the remote computer.</span></span> <span data-ttu-id="c137f-143">在这种情况下，创建 PSSession，然后使用 **Session** 参数在 PSSession 中运行命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-143">In that case, create a PSSession, and then use the **Session** parameter to run commands in the PSSession.</span></span>

<span data-ttu-id="c137f-144">从远程计算机获取数据的许多其他 cmdlet （如 `Get-Process` 、、 `Get-Service` 和） `Get-EventLog` `Get-WmiObject` 只包含 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="c137f-144">Many other cmdlets that get data from remote computers, such as `Get-Process`, `Get-Service`, `Get-EventLog`, and `Get-WmiObject` have only a **ComputerName** parameter.</span></span> <span data-ttu-id="c137f-145">它们使用 PowerShell 远程处理以外的技术来远程收集数据。</span><span class="sxs-lookup"><span data-stu-id="c137f-145">They use technologies other than PowerShell remoting to gather data remotely.</span></span> <span data-ttu-id="c137f-146">这些 cmdlet 没有 **Session** 参数，但你可以使用 `Invoke-Command` cmdlet 在 PSSession 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-146">These cmdlets do not have a **Session** parameter, but you can use the `Invoke-Command` cmdlet to run these commands in a PSSession.</span></span>

## <a name="how-do-i-create-a-pssession"></a><span data-ttu-id="c137f-147">如何创建 PSSession？</span><span class="sxs-lookup"><span data-stu-id="c137f-147">How Do I Create a PSSession?</span></span>

<span data-ttu-id="c137f-148">若要创建 PSSession，请使用 `New-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137f-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="c137f-149">您可以使用 `New-PSSession` 在本地或远程计算机上创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-149">You can use `New-PSSession` to create a PSSession on a local or remote computer.</span></span>

## <a name="can-i-create-a-pssession-on-any-computer"></a><span data-ttu-id="c137f-150">是否可以在任何计算机上创建 PSSession？</span><span class="sxs-lookup"><span data-stu-id="c137f-150">Can I Create a PSSession on Any Computer?</span></span>

<span data-ttu-id="c137f-151">若要创建连接到远程计算机的 PSSession，计算机必须配置为在 PowerShell 中进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="c137f-151">To create a PSSession that is connected to a remote computer, the computer must be configured for remoting in PowerShell.</span></span> <span data-ttu-id="c137f-152">当前用户必须是远程计算机上 Administrators 组的成员，或者当前用户必须能够提供 Administrators 组的成员的凭据。</span><span class="sxs-lookup"><span data-stu-id="c137f-152">The current user must be a member of the Administrators group on the remote computer, or the current user must be able to supply the credentials of a member of the Administrators group.</span></span> <span data-ttu-id="c137f-153">有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c137f-153">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="can-i-see-my-pssessions-in-other-sessions"></a><span data-ttu-id="c137f-154">我是否能在其他会话中看到我的 Pssession？</span><span class="sxs-lookup"><span data-stu-id="c137f-154">Can I See My PSSessions in Other Sessions?</span></span>

<span data-ttu-id="c137f-155">从 Windows PowerShell 3.0 开始，cmdlet 的 **ComputerName** 参数将 `Get-PSSession` 获取你在指定的远程计算机上创建的 pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-155">Beginning in Windows PowerShell 3.0, the **ComputerName** parameter of the `Get-PSSession` cmdlet gets PSSessions that you created on the specified remote computers.</span></span>

<span data-ttu-id="c137f-156">Active Pssession 在远程计算机上保持 (连接) 的 "服务器端"，可以从任何计算机上的任何会话获取它们。</span><span class="sxs-lookup"><span data-stu-id="c137f-156">Active PSSessions are maintained on the remote computer (the "server-side" of a connection) and you can get them from any session on any computer.</span></span>

<span data-ttu-id="c137f-157">例如，如果您创建从 Server01 计算机到 Server02 计算机的 PSSession，然后切换到 Server03 计算机，则可以使用类似于下面的命令来获取会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-157">For example, if you create a PSSession from the Server01 computer to the Server02 computer, and then switch to the Server03 computer, you can use a command like the following one to get the session.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

<span data-ttu-id="c137f-158">即使断开与会话的连接，也会在远程计算机上保留会话，直到将其删除或超时。</span><span class="sxs-lookup"><span data-stu-id="c137f-158">Even if you disconnect from the session, the session is maintained on the remote computer until you delete it or it times out.</span></span>

<span data-ttu-id="c137f-159">在 Windows PowerShell 2.0 中，只能获取在当前会话中创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-159">In Windows PowerShell 2.0, you can get only the PSSessions that you have created in the current session.</span></span> <span data-ttu-id="c137f-160">无法获取在其他会话中创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-160">You cannot get PSSessions that you created in other sessions.</span></span>

<span data-ttu-id="c137f-161">有关详细信息，请参阅 [get-help](xref:Microsoft.PowerShell.Core.Get-PSSession)。</span><span class="sxs-lookup"><span data-stu-id="c137f-161">For more information, see [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession).</span></span>

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a><span data-ttu-id="c137f-162">是否可以看到其他人在我的电脑上创建的 Pssession？</span><span class="sxs-lookup"><span data-stu-id="c137f-162">Can I See the PSSessions That Others Have Created on My Computer?</span></span>

<span data-ttu-id="c137f-163">仅当你可以提供创建 PSSession 的用户的凭据或 PSSession 使用的会话配置包含 RunAs 凭据时，才能获取和管理其他人已创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-163">You can get and manage only the PSSessions that others have created only if you can supply the credentials of the user who created the PSSession or the session configuration that the PSSession uses includes RunAs credentials.</span></span> <span data-ttu-id="c137f-164">否则，你可以获取、连接、使用和管理你创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-164">Otherwise, you can get, connect to, use, and manage only the PSSessions that you created.</span></span>

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a><span data-ttu-id="c137f-165">是否可以从其他计算机连接到 PSSession？</span><span class="sxs-lookup"><span data-stu-id="c137f-165">Can I Connect to a PSSession From a Different Computer?</span></span>

<span data-ttu-id="c137f-166">从 Windows PowerShell 3.0 开始，Pssession 独立于创建它们的会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-166">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="c137f-167">在远程或连接的 "服务器端" 的计算机上维护活动的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-167">Active PSSessions are maintained on the computer at the remote or "server-side" of a connection.</span></span>

<span data-ttu-id="c137f-168">可以使用 `Disconnect-PSSession` cmdlet 断开与 PSSession 的连接。</span><span class="sxs-lookup"><span data-stu-id="c137f-168">You can use the `Disconnect-PSSession` cmdlet to disconnect from a PSSession.</span></span> <span data-ttu-id="c137f-169">PSSession 断开与本地会话的连接，但在远程计算机上维护。</span><span class="sxs-lookup"><span data-stu-id="c137f-169">The PSSession is disconnected from the local session, but is maintained on the remote computer.</span></span>
<span data-ttu-id="c137f-170">命令继续在断开连接的 PSSession 中运行。</span><span class="sxs-lookup"><span data-stu-id="c137f-170">Commands continue to run in the disconnected PSSession.</span></span> <span data-ttu-id="c137f-171">可以关闭 PowerShell 并关闭源计算机，而不会中断 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-171">You can close PowerShell and shut down the originating computer without interrupting the PSSession.</span></span>

<span data-ttu-id="c137f-172">稍后，甚至几个小时，你可以使用 `Get-PSSession` cmdlet 来获取 pssession 和 cmdlet， `Connect-PSSession` 以从另一台计算机上的新会话连接到 pssession。</span><span class="sxs-lookup"><span data-stu-id="c137f-172">Then, even hours later, you can use the `Get-PSSession` cmdlet to get the PSSession and the `Connect-PSSession` cmdlet to connect to the PSSession from a new session on a different computer.</span></span>

<span data-ttu-id="c137f-173">有关详细信息，请参阅 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="c137f-173">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a><span data-ttu-id="c137f-174">如果我的电脑停止，PSSession 会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="c137f-174">What Happens to My PSSession if My Computer Stops?</span></span>

<span data-ttu-id="c137f-175">断开连接的 Pssession 独立于创建它们的会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-175">Disconnected PSSessions are independent of the sessions in which they were created.</span></span> <span data-ttu-id="c137f-176">如果断开 PSSession 的连接然后关闭源计算机，则将在远程计算机上维护 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-176">If you disconnect a PSSession and then close the originating computer, the PSSession is maintained on the remote computer.</span></span>

<span data-ttu-id="c137f-177">此外，PowerShell 还尝试恢复无意中断开连接的活动 Pssession，如计算机重启、暂时停电或网络中断。</span><span class="sxs-lookup"><span data-stu-id="c137f-177">In addition, PowerShell attempts to recover active PSSessions that are disconnected unintentionally, such as by a computer reboot, a temporary power outage or network disruption.</span></span> <span data-ttu-id="c137f-178">如果源会话仍可用，则 PowerShell 将尝试维护 PSSession，或将其恢复为已打开状态，如果不是，则为断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="c137f-178">PowerShell attempts to maintain or recover the PSSession to an Opened state, if the originating session is still available, or to a disconnected state if it is not.</span></span>

<span data-ttu-id="c137f-179">"Active" PSSession 是运行命令的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-179">An "active" PSSession is one that is running commands.</span></span> <span data-ttu-id="c137f-180">如果已连接 PSSession (未断开连接) 并且命令在连接的会话关闭时在 PSSession 中运行，则 PowerShell 将尝试维护远程计算机上的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-180">If a PSSession is connected (not disconnected) and commands are running in the PSSession when the connected session closes, PowerShell attempts to maintain the PSSession on the remote computer.</span></span> <span data-ttu-id="c137f-181">但是，如果未在 PSSession 中运行任何命令，则在连接的会话关闭时，PowerShell 会关闭 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-181">However, if no commands are running in the PSSession, PowerShell closes the PSSession when the connected session closes.</span></span>

<span data-ttu-id="c137f-182">有关详细信息，请参阅 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="c137f-182">For more information, see [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).</span></span>

## <a name="can-i-run-a-background-job-in-a-pssession"></a><span data-ttu-id="c137f-183">能否在 PSSession 中运行后台作业？</span><span class="sxs-lookup"><span data-stu-id="c137f-183">Can I Run a Background Job in a PSSession?</span></span>

<span data-ttu-id="c137f-184">是的。</span><span class="sxs-lookup"><span data-stu-id="c137f-184">Yes.</span></span> <span data-ttu-id="c137f-185">后台作业是在后台异步运行的命令，不与当前会话交互。</span><span class="sxs-lookup"><span data-stu-id="c137f-185">A background job is a command that runs asynchronously in the background without interacting with the current session.</span></span> <span data-ttu-id="c137f-186">提交用于启动作业的命令时，该命令将返回一个作业对象，但该作业将继续在后台运行，直到完成。</span><span class="sxs-lookup"><span data-stu-id="c137f-186">When you submit a command to start a job, the command returns a job object, but the job continues to run in the background until it is complete.</span></span>

<span data-ttu-id="c137f-187">若要在本地计算机上启动后台作业，请使用 `Start-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-187">To start a background job on a local computer, use the `Start-Job` command.</span></span>
<span data-ttu-id="c137f-188">可以通过使用 **ComputerName** 参数) 或在 PSSession (中使用 **Session** 参数) 来运行后台作业 (。</span><span class="sxs-lookup"><span data-stu-id="c137f-188">You can run the background job in a temporary connection (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>

<span data-ttu-id="c137f-189">若要在远程计算机上启动后台作业，请使用 `Invoke-Command` cmdlet 及其 **AsJob** 参数，或使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-189">To start a background job on a remote computer, use the `Invoke-Command` cmdlet with its **AsJob** parameter, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="c137f-190">使用 **AsJob** 参数时，可以使用 **ComputerName** 或 **Session** 参数。</span><span class="sxs-lookup"><span data-stu-id="c137f-190">When using the **AsJob** parameter, you can use the **ComputerName** or **Session** parameters.</span></span>

<span data-ttu-id="c137f-191">使用 `Invoke-Command` 运行 `Start-Job` 命令时，必须在 PSSession 中运行该命令。</span><span class="sxs-lookup"><span data-stu-id="c137f-191">When using `Invoke-Command` to run a `Start-Job` command, you must run the command in a PSSession.</span></span> <span data-ttu-id="c137f-192">如果使用 **ComputerName** 参数，则当作业对象返回时，PowerShell 将结束连接，并且该作业将中断。</span><span class="sxs-lookup"><span data-stu-id="c137f-192">If you use the **ComputerName** parameter, PowerShell ends the connection when the job object returns, and the job is interrupted.</span></span>

<span data-ttu-id="c137f-193">有关详细信息，请参阅 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="c137f-193">For more information, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="can-i-run-an-interactive-session"></a><span data-ttu-id="c137f-194">能否运行交互式会话？</span><span class="sxs-lookup"><span data-stu-id="c137f-194">Can I Run an Interactive Session?</span></span>

<span data-ttu-id="c137f-195">是的。</span><span class="sxs-lookup"><span data-stu-id="c137f-195">Yes.</span></span> <span data-ttu-id="c137f-196">若要启动与远程计算机的交互式会话，请使用 `Enter-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137f-196">To start an interactive session with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="c137f-197">在交互式会话中，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。</span><span class="sxs-lookup"><span data-stu-id="c137f-197">In an interactive session, the commands that you type run on the remote computer, just as if you typed them directly on the remote computer.</span></span>

<span data-ttu-id="c137f-198">您可以通过使用 **ComputerName** 参数) 在临时会话 (中运行交互式会话，或使用 **session** 参数) 在 PSSession (中运行。</span><span class="sxs-lookup"><span data-stu-id="c137f-198">You can run an interactive session in a temporary session (by using the **ComputerName** parameter) or in a PSSession (by using the **Session** parameter).</span></span>
<span data-ttu-id="c137f-199">如果使用 PSSession，PSSession 将保留以前的命令中的数据，而 PSSession 将保留在交互式会话过程中生成的所有数据，以便在以后的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="c137f-199">If you use a PSSession, the PSSession retains the data from previous commands, and the PSSession retains any data generated during the interactive session for use in later commands.</span></span>

<span data-ttu-id="c137f-200">结束交互式会话时，PSSession 将保持打开状态并可供使用。</span><span class="sxs-lookup"><span data-stu-id="c137f-200">When you end the interactive session, the PSSession remains open and available for use.</span></span>

<span data-ttu-id="c137f-201">有关详细信息，请参阅 [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 和 [Exit-pssession](xref:Microsoft.PowerShell.Core.Exit-PSSession)。</span><span class="sxs-lookup"><span data-stu-id="c137f-201">For more information, see [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) and [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession).</span></span>

## <a name="must-i-delete-the-pssessions"></a><span data-ttu-id="c137f-202">是否必须删除 Pssession？</span><span class="sxs-lookup"><span data-stu-id="c137f-202">Must I Delete the PSSessions?</span></span>

<span data-ttu-id="c137f-203">是的。</span><span class="sxs-lookup"><span data-stu-id="c137f-203">Yes.</span></span> <span data-ttu-id="c137f-204">PSSession 是一个独立的环境，该环境使用内存和其他资源，即使未使用它也是如此。</span><span class="sxs-lookup"><span data-stu-id="c137f-204">A PSSession is a process, which is a self-contained environment that uses memory and other resources even when you are not using it.</span></span> <span data-ttu-id="c137f-205">完成 PSSession 后，请将其删除。</span><span class="sxs-lookup"><span data-stu-id="c137f-205">When you are finished with a PSSession, delete it.</span></span> <span data-ttu-id="c137f-206">如果创建多个 Pssession，请关闭未使用的文件，并仅保留当前正在使用的文件。</span><span class="sxs-lookup"><span data-stu-id="c137f-206">If you create multiple PSSessions, close the ones that you are not using, and maintain only the ones currently in use.</span></span>

<span data-ttu-id="c137f-207">若要删除 Pssession，请使用 `Remove-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137f-207">To delete PSSessions, use the `Remove-PSSession` cmdlet.</span></span> <span data-ttu-id="c137f-208">它删除 Pssession 并释放它们使用的所有资源。</span><span class="sxs-lookup"><span data-stu-id="c137f-208">It deletes the PSSessions and releases all of the resources that they were using.</span></span>

<span data-ttu-id="c137f-209">你还可以使用的 **IdleTimeOut** 参数 `New-PSSessionOption` ，在指定的时间间隔后关闭空闲 PSSession。</span><span class="sxs-lookup"><span data-stu-id="c137f-209">You can also use the **IdleTimeOut** parameter of `New-PSSessionOption` to close an idle PSSession after an interval that you specify.</span></span> <span data-ttu-id="c137f-210">有关详细信息，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。</span><span class="sxs-lookup"><span data-stu-id="c137f-210">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="c137f-211">如果将 PSSession 对象保存在变量中，然后删除 PSSession 或使其超时，则该变量仍包含 PSSession 对象，但 PSSession 不处于活动状态，并且不能使用或修复。</span><span class="sxs-lookup"><span data-stu-id="c137f-211">If you save a PSSession object in a variable and then delete the PSSession or let it time out, the variable still contains the PSSession object, but the PSSession is not active and cannot be used or repaired.</span></span>

## <a name="are-all-sessions-and-pssessions-alike"></a><span data-ttu-id="c137f-212">是否所有会话和 Pssession 都是相同的？</span><span class="sxs-lookup"><span data-stu-id="c137f-212">Are All Sessions and PSSessions Alike?</span></span>

<span data-ttu-id="c137f-213">不能。</span><span class="sxs-lookup"><span data-stu-id="c137f-213">No.</span></span> <span data-ttu-id="c137f-214">开发人员可以创建只包括所选提供程序和 cmdlet 的自定义会话。</span><span class="sxs-lookup"><span data-stu-id="c137f-214">Developers can create custom sessions that include only selected providers and cmdlets.</span></span> <span data-ttu-id="c137f-215">如果命令在一个会话中工作而不是在另一个会话中工作，则可能是因为会话受到限制。</span><span class="sxs-lookup"><span data-stu-id="c137f-215">If a command works in one session but not in another, it might be because the session is restricted.</span></span>

## <a name="see-also"></a><span data-ttu-id="c137f-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c137f-216">See Also</span></span>

[<span data-ttu-id="c137f-217">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="c137f-217">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="c137f-218">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="c137f-218">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="c137f-219">about_Remote</span><span class="sxs-lookup"><span data-stu-id="c137f-219">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="c137f-220">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="c137f-220">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="c137f-221">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="c137f-221">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="c137f-222">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c137f-222">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="c137f-223">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="c137f-223">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="c137f-224">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="c137f-224">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="c137f-225">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="c137f-225">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="c137f-226">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c137f-226">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="c137f-227">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c137f-227">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)

