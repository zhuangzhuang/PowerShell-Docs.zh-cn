---
description: 说明如何断开连接并重新连接到 PowerShell 会话 (PSSession) 。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 0756e110b1058915f6280e2ea59ee915bedb2c75
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598450"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="55e15-103">关于远程断开连接的会话</span><span class="sxs-lookup"><span data-stu-id="55e15-103">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="55e15-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="55e15-104">Short description</span></span>

<span data-ttu-id="55e15-105">说明如何断开连接并重新连接到 PowerShell 会话 (PSSession) 。</span><span class="sxs-lookup"><span data-stu-id="55e15-105">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="55e15-106">长说明</span><span class="sxs-lookup"><span data-stu-id="55e15-106">Long description</span></span>

<span data-ttu-id="55e15-107">从 PowerShell 3.0 开始，你可以断开与 PSSession 的连接，然后重新连接到同一台计算机或不同计算机上的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="55e15-107">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="55e15-108">当会话断开连接时，将维护会话状态，并且 PSSession 中的命令将继续运行。</span><span class="sxs-lookup"><span data-stu-id="55e15-108">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="55e15-109">仅当远程计算机运行 PowerShell 3.0 或更高版本时，"断开连接的会话" 功能才可用。</span><span class="sxs-lookup"><span data-stu-id="55e15-109">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="55e15-110">使用 "断开连接的会话" 功能，可以关闭在其中创建 PSSession 的会话，甚至可以关闭 PowerShell 并关闭计算机，而不会中断在 PSSession 中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="55e15-110">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="55e15-111">断开连接的会话适用于运行需要延长时间完成的命令，并提供 IT 专业人员所需的时间和设备灵活性。</span><span class="sxs-lookup"><span data-stu-id="55e15-111">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="55e15-112">不能从使用 cmdlet 启动的交互式会话断开连接 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-112">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="55e15-113">你可以使用断开连接的会话来管理由于计算机或网络中断而无意间断开连接的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-113">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="55e15-114">在实际使用中，通过 "断开连接的会话" 功能，您可以开始解决问题，将注意力转换为更高的优先级问题，然后在解决方案上恢复工作，即使在不同的计算机上的其他位置也是如此。</span><span class="sxs-lookup"><span data-stu-id="55e15-114">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="55e15-115">断开连接的会话 cmdlet</span><span class="sxs-lookup"><span data-stu-id="55e15-115">Disconnected session cmdlets</span></span>

<span data-ttu-id="55e15-116">以下 cmdlet 支持 "断开连接的会话" 功能：</span><span class="sxs-lookup"><span data-stu-id="55e15-116">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="55e15-117">`Connect-PSSession`：连接到断开连接的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="55e15-117">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="55e15-118">`Disconnect-PSSession`：断开 PSSession 的连接。</span><span class="sxs-lookup"><span data-stu-id="55e15-118">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="55e15-119">`Get-PSSession`：获取本地计算机或远程计算机上的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-119">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="55e15-120">`Receive-PSSession`：获取在断开连接的会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-120">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="55e15-121">`Invoke-Command`： **InDisconnectedSession** 参数创建 PSSession 并立即断开连接。</span><span class="sxs-lookup"><span data-stu-id="55e15-121">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="55e15-122">断开连接的会话功能的工作原理</span><span class="sxs-lookup"><span data-stu-id="55e15-122">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="55e15-123">从 PowerShell 3.0 开始，Pssession 独立于创建它们的会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-123">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="55e15-124">活动的 Pssession 在连接的远程计算机或 **服务器端** 保持，即使在其中创建 PSSession 的会话已关闭，并且源计算机已关闭或断开与网络的连接。</span><span class="sxs-lookup"><span data-stu-id="55e15-124">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="55e15-125">在 PowerShell 2.0 中，当从远程计算机断开连接时，该 PSSession 将从远程计算机中删除，或从该会话中创建的会话结束。</span><span class="sxs-lookup"><span data-stu-id="55e15-125">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="55e15-126">断开 PSSession 的连接时，PSSession 将保持活动状态并在远程计算机上维护。</span><span class="sxs-lookup"><span data-stu-id="55e15-126">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="55e15-127">会话状态从 " **正在运行** " 更改为 "已 **断开连接**"。</span><span class="sxs-lookup"><span data-stu-id="55e15-127">The session state changes from **Running** to **Disconnected**.</span></span> <span data-ttu-id="55e15-128">可以从当前会话或同一计算机上的其他会话或其他计算机重新连接到断开连接的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="55e15-128">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="55e15-129">维护会话的远程计算机必须正在运行并连接到网络。</span><span class="sxs-lookup"><span data-stu-id="55e15-129">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="55e15-130">断开连接的 PSSession 中的命令将继续在远程计算机上无中断运行，直到命令完成或输出缓冲区已满。</span><span class="sxs-lookup"><span data-stu-id="55e15-130">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="55e15-131">若要防止完整输出缓冲区暂停命令，请使用 `Disconnect-PSSession` 、 `New-PSSessionOption` 或 cmdlet 的 OutputBufferingMode 参数 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-131">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="55e15-132">断开连接的会话在远程计算机上保持为断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="55e15-132">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="55e15-133">它们可用于重新连接，直到你删除 PSSession （如使用 `Remove-PSSession` cmdlet）或直到 PSSession 的空闲超时过期。</span><span class="sxs-lookup"><span data-stu-id="55e15-133">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="55e15-134">你可以使用 、  `Disconnect-PSSession` `New-PSSessionOption` 或 cmdlet 的 IdleTimeoutSec 或 IdleTimeout 参数调整 PSSession 的空闲超时 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-134">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="55e15-135">其他用户可以连接到你创建的 Pssession，但前提是这些用户可以提供用于创建会话的凭据，或使用 `RunAs` 会话配置的凭据。</span><span class="sxs-lookup"><span data-stu-id="55e15-135">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="55e15-136">如何获取 Pssession</span><span class="sxs-lookup"><span data-stu-id="55e15-136">How to get PSSessions</span></span>

<span data-ttu-id="55e15-137">从 PowerShell 3.0 开始，该 `Get-PSSession` cmdlet 将获取本地计算机和远程计算机上的 pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-137">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="55e15-138">它还可获取在当前会话中创建的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-138">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="55e15-139">若要在本地计算机或远程计算机上获取 Pssession，请使用 **ComputerName** 或 **ConnectionUri** 参数。</span><span class="sxs-lookup"><span data-stu-id="55e15-139">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="55e15-140">如果没有参数，则 `Get-PSSession` 将获取在本地会话中创建的 PSSession，而不考虑它们终止的位置。</span><span class="sxs-lookup"><span data-stu-id="55e15-140">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="55e15-141">获取 Pssession 时，请记住在维护它们的计算机（即远程计算机或 **服务器端** 计算机）上查找它们。</span><span class="sxs-lookup"><span data-stu-id="55e15-141">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="55e15-142">例如，如果创建 Server01 计算机的 PSSession，请从 Server01 计算机获取会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-142">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="55e15-143">如果从另一台计算机向本地计算机创建 PSSession，请从本地计算机获取会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-143">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="55e15-144">以下命令序列显示了如何 `Get-PSSession` 工作。</span><span class="sxs-lookup"><span data-stu-id="55e15-144">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="55e15-145">第一个命令创建一个与 Server01 计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-145">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="55e15-146">该会话驻留在 Server01 计算机上。</span><span class="sxs-lookup"><span data-stu-id="55e15-146">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="55e15-147">若要获取会话，请使用值为 Server01 的 **ComputerName** 参数 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-147">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="55e15-148">如果的 **ComputerName** 参数的值 `Get-PSSession` 为 localhost，将 `Get-PSSession` 获取在本地计算机上维护并在其上维护的 pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-148">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="55e15-149">即使它们是在本地计算机上启动的，它也不会在 Server01 计算机上 Pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-149">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="55e15-150">若要获取在当前会话中创建的会话，请使用 `Get-PSSession` 不带参数的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-150">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="55e15-151">在此示例中， `Get-PSSession` 将获取在当前会话中创建的 PSSession 并连接到 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="55e15-151">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="55e15-152">如何断开会话连接</span><span class="sxs-lookup"><span data-stu-id="55e15-152">How to disconnect sessions</span></span>

<span data-ttu-id="55e15-153">若要断开 PSSession 的连接，请使用 `Disconnect-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-153">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="55e15-154">若要标识 PSSession，请使用 **Session** 参数，或从 `New-PSSession` 或 cmdlet 到的管道 `Get-PSSession` `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-154">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="55e15-155">以下命令将 PSSession 断开连接到 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="55e15-155">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="55e15-156">请注意， **State** 属性的值已 **断开连接** ，并且 **可用性** 为 **None**。</span><span class="sxs-lookup"><span data-stu-id="55e15-156">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None**.</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="55e15-157">若要创建断开连接的会话，请使用 cmdlet 的 **InDisconnectedSession** 参数 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-157">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="55e15-158">它将创建一个会话，启动命令，并立即断开连接，然后该命令才能返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="55e15-158">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="55e15-159">以下命令 `Get-WinEvent` 在 Server02 远程计算机上的已断开连接的会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="55e15-159">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="55e15-160">如何连接到断开连接的会话</span><span class="sxs-lookup"><span data-stu-id="55e15-160">How to connect to disconnected sessions</span></span>

<span data-ttu-id="55e15-161">可以从在其中创建 PSSession 的会话或本地计算机或其他计算机上的其他会话连接到任何可用的断开连接的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="55e15-161">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="55e15-162">你可以创建 PSSession，在 PSSession 中运行命令，断开与 PSSession 的连接，关闭 PowerShell，然后关闭计算机。</span><span class="sxs-lookup"><span data-stu-id="55e15-162">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="55e15-163">小时之后，您可以打开另一台计算机，获取 PSSession，连接到该计算机，并获得在连接断开连接时在 PSSession 中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-163">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="55e15-164">然后，你可以在该会话中运行更多命令。</span><span class="sxs-lookup"><span data-stu-id="55e15-164">Then you can run more commands in the session.</span></span>

<span data-ttu-id="55e15-165">若要连接已断开连接的 PSSession，请使用 `Connect-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-165">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="55e15-166">使用 **ComputerName** 或 **ConnectionUri** 参数来标识 pssession，或从到的 pssession 管道 `Get-PSSession` `Connect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-166">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="55e15-167">以下命令获取 Server02 计算机上的会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-167">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="55e15-168">输出包括两个断开连接的会话，两者都可用。</span><span class="sxs-lookup"><span data-stu-id="55e15-168">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="55e15-169">以下命令将连接到 Session2。</span><span class="sxs-lookup"><span data-stu-id="55e15-169">The following command connects to Session2.</span></span> <span data-ttu-id="55e15-170">PSSession 现在已打开且可用。</span><span class="sxs-lookup"><span data-stu-id="55e15-170">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="55e15-171">如何获取结果</span><span class="sxs-lookup"><span data-stu-id="55e15-171">How to get the results</span></span>

<span data-ttu-id="55e15-172">若要获取在断开连接的 PSSession 中运行的命令的结果，请使用 `Receive-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-172">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="55e15-173">你可以使用 `Receive-PSSession` 而不是使用 `Connect-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-173">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="55e15-174">如果会话已重新连接，则 `Receive-PSSession` 获取在断开会话连接时运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-174">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="55e15-175">如果 PSSession 仍处于断开连接状态，则 `Receive-PSSession` 连接到它，然后获取断开连接时运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-175">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="55e15-176">`Receive-PSSession` 可以 (异步方式将结果返回到) 或 (同步) 到主机程序。</span><span class="sxs-lookup"><span data-stu-id="55e15-176">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="55e15-177">使用 **OutTarget** 参数选择 " **作业** " 或 " **主机**"。</span><span class="sxs-lookup"><span data-stu-id="55e15-177">Use the **OutTarget** parameter to select **Job** or **Host**.</span></span> <span data-ttu-id="55e15-178">默认值为 **Host**。</span><span class="sxs-lookup"><span data-stu-id="55e15-178">The default value is **Host**.</span></span> <span data-ttu-id="55e15-179">但是，如果正在接收的命令在当前会话中作为 **作业** 启动，则默认情况下，它作为 **作业** 返回。</span><span class="sxs-lookup"><span data-stu-id="55e15-179">However, if the command that's being received was started in the current session as a **Job**, it's returned as a **Job** by default.</span></span>

<span data-ttu-id="55e15-180">以下命令使用 `Receive-PSSession` cmdlet 连接到 Server02 计算机上的 PSSession，并获取 `Get-WinEvent` 在 Session3 会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-180">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="55e15-181">该命令使用 **OutTarget** 参数来获取 **作业** 中的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-181">The command uses the **OutTarget** parameter to get the results in a **Job**.</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="55e15-182">若要获取作业结果，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55e15-182">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="55e15-183">状态和可用性属性</span><span class="sxs-lookup"><span data-stu-id="55e15-183">State and Availability properties</span></span>

<span data-ttu-id="55e15-184">断开连接的 PSSession 的 " **状态** " 和 " **可用性** " 属性告诉你是否可以重新连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-184">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="55e15-185">当 PSSession 连接到当前会话时，它的状态为 "已 **打开** "，并 **提供** 其可用性。</span><span class="sxs-lookup"><span data-stu-id="55e15-185">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available**.</span></span> <span data-ttu-id="55e15-186">当断开与 PSSession 的连接时，PSSession 状态将 **断开连接** ，并且其可用性为 **None**。</span><span class="sxs-lookup"><span data-stu-id="55e15-186">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None**.</span></span>

<span data-ttu-id="55e15-187">**State** 属性的值是相对于当前会话的。</span><span class="sxs-lookup"><span data-stu-id="55e15-187">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="55e15-188">如果值为 "已 **断开连接** "，则意味着 PSSession 未连接到当前会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-188">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="55e15-189">但这并不意味着 PSSession 会与所有会话断开连接。</span><span class="sxs-lookup"><span data-stu-id="55e15-189">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="55e15-190">它可能连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-190">It might be connected to a different session.</span></span>

<span data-ttu-id="55e15-191">若要确定是否可以连接或重新连接到 PSSession，请使用 **Availability** 属性。</span><span class="sxs-lookup"><span data-stu-id="55e15-191">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="55e15-192">如果值为 " **无** "，则指示你可以连接到会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-192">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="55e15-193">值为 " **忙碌** " 表示无法连接到 PSSession，因为它已连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-193">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="55e15-194">下面的示例在同一台计算机上的两个 PowerShell 会话中运行。</span><span class="sxs-lookup"><span data-stu-id="55e15-194">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="55e15-195">请注意，当 PSSession 断开连接并重新连接时，每个会话中的 " **状态** " 和 " **可用性** " 属性值会发生变化。</span><span class="sxs-lookup"><span data-stu-id="55e15-195">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="55e15-196">断开连接的会话将一直保留在远程计算机上，直到你将其删除（如使用 `Remove-PSSession` cmdlet）或超时。PSSession 的 **IdleTimeout** 属性确定已断开连接的会话在被删除之前保留多长时间。</span><span class="sxs-lookup"><span data-stu-id="55e15-196">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="55e15-197">当 **检测信号线程** 未收到响应时，pssession 处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="55e15-197">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="55e15-198">断开会话后，即使已断开连接的会话中的命令仍在运行，它也会使其处于空闲状态并启动 **IdleTimeout** 时钟。</span><span class="sxs-lookup"><span data-stu-id="55e15-198">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="55e15-199">PowerShell 将断开连接的会话视为处于活动状态，但处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="55e15-199">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="55e15-200">当创建和断开连接会话时，请验证 PSSession 中的空闲超时是否足够长，以根据需要维护会话，但不太长，因为它会在远程计算机上使用不必要的资源。</span><span class="sxs-lookup"><span data-stu-id="55e15-200">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="55e15-201">会话配置的 **IdleTimeoutMs** 属性确定使用会话配置的会话的默认空闲超时。</span><span class="sxs-lookup"><span data-stu-id="55e15-201">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="55e15-202">您可以重写默认值，但使用的值不能超过会话配置的 **MaxIdleTimeoutMs** 属性。</span><span class="sxs-lookup"><span data-stu-id="55e15-202">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="55e15-203">若要查找会话配置的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 值，请使用以下命令格式。</span><span class="sxs-lookup"><span data-stu-id="55e15-203">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="55e15-204">您可以覆盖会话配置中的默认值，并在创建 PSSession 和断开连接时设置 PSSession 的空闲超时。</span><span class="sxs-lookup"><span data-stu-id="55e15-204">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="55e15-205">如果你是远程计算机上 Administrators 组的成员，则可以创建和更改会话配置的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 属性。</span><span class="sxs-lookup"><span data-stu-id="55e15-205">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="55e15-206">空闲超时值</span><span class="sxs-lookup"><span data-stu-id="55e15-206">Idle timeout values</span></span>

<span data-ttu-id="55e15-207">会话配置和会话选项的空闲超时值以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="55e15-207">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="55e15-208">会话和会话配置选项的空闲超时值以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="55e15-208">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="55e15-209">您可以在创建 PSSession (时设置 PSSession 的空闲超时 `New-PSSession` ， `Invoke-Command`) 并在从其 () 时断开连接 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-209">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="55e15-210">但是，在连接到 PSSession  (`Connect-PSSession`) 或 () 获取结果时，无法更改 IdleTimeout 值 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-210">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="55e15-211">`Connect-PSSession`和 `Receive-PSSession` Cmdlet 具有 **SessionOption** 参数，该参数采用 **SessionOption** 对象，例如 cmdlet 返回的对象 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-211">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="55e15-212">**SessionOption** 对象中的 **idletimeout** 值和首选项变量中的 **idletimeout** 值 `$PSSessionOption` 不会更改或命令中 PSSession 的 **idletimeout** 值 `Connect-PSSession` `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-212">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="55e15-213">若要创建具有特定空闲超时值的 PSSession，请创建一个 `$PSSessionOption` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="55e15-213">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="55e15-214">将 **IdleTimeout** 属性的值设置为所需的值 (以毫秒为单位) 。</span><span class="sxs-lookup"><span data-stu-id="55e15-214">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="55e15-215">当您创建 Pssession 时，变量中的值 `$PSSessionOption` 优先于会话配置中的值。</span><span class="sxs-lookup"><span data-stu-id="55e15-215">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="55e15-216">例如，以下命令会将空闲超时设置为48小时：</span><span class="sxs-lookup"><span data-stu-id="55e15-216">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="55e15-217">若要创建具有特定空闲超时值的 PSSession，请使用 cmdlet 的 **IdleTimeoutMSec** 参数 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-217">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="55e15-218">然后，在或 cmdlet 的 **SessionOption** 参数的值中使用 session 选项 `New-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-218">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="55e15-219">创建会话时设置的值优先于 `$PSSessionOption` 首选项变量和会话配置中设置的值。</span><span class="sxs-lookup"><span data-stu-id="55e15-219">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="55e15-220">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-220">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="55e15-221">若要在断开连接时更改 PSSession 的空闲超时，请使用 cmdlet 的 **IdleTimeoutSec** 参数 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-221">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="55e15-222">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-222">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="55e15-223">若要创建具有特定空闲超时和最大空闲超时的会话配置，请使用 cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 参数 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-223">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="55e15-224">然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-224">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="55e15-225">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-225">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="55e15-226">若要更改会话配置的默认空闲超时和最大空闲超时时间，请使用 cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 参数 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-226">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="55e15-227">然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-227">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="55e15-228">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-228">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="55e15-229">输出缓冲模式</span><span class="sxs-lookup"><span data-stu-id="55e15-229">Output buffering mode</span></span>

<span data-ttu-id="55e15-230">PSSession 的输出缓冲模式决定当 PSSession 的输出缓冲区已满时如何管理命令输出。</span><span class="sxs-lookup"><span data-stu-id="55e15-230">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="55e15-231">在断开连接的会话中，输出缓冲模式可以有效地确定当会话断开连接时该命令是否继续运行。</span><span class="sxs-lookup"><span data-stu-id="55e15-231">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="55e15-232">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="55e15-232">The valid values as follows:</span></span>

- <span data-ttu-id="55e15-233">**块**。</span><span class="sxs-lookup"><span data-stu-id="55e15-233">**Block**.</span></span> <span data-ttu-id="55e15-234">当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。</span><span class="sxs-lookup"><span data-stu-id="55e15-234">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="55e15-235">默认值。</span><span class="sxs-lookup"><span data-stu-id="55e15-235">The default value.</span></span>
- <span data-ttu-id="55e15-236">**删除**。</span><span class="sxs-lookup"><span data-stu-id="55e15-236">**Drop**.</span></span> <span data-ttu-id="55e15-237">当输出缓冲区已满时，执行将继续。</span><span class="sxs-lookup"><span data-stu-id="55e15-237">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="55e15-238">随着新输出的生成，会丢弃最早的输出。</span><span class="sxs-lookup"><span data-stu-id="55e15-238">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="55e15-239">**块** 保留数据，但可能会中断命令。</span><span class="sxs-lookup"><span data-stu-id="55e15-239">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="55e15-240">值 **Drop** 允许命令完成，但是可能会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="55e15-240">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="55e15-241">当使用 **Drop** 值时，请将命令输出重定向到磁盘上的文件。</span><span class="sxs-lookup"><span data-stu-id="55e15-241">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="55e15-242">对于断开连接的会话，建议使用此值。</span><span class="sxs-lookup"><span data-stu-id="55e15-242">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="55e15-243">会话配置的 **OutputBufferingMode** 属性确定使用会话配置的会话的默认输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="55e15-243">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="55e15-244">若要查找会话配置的 **OutputBufferingMode** 值，可以使用以下任一命令格式：</span><span class="sxs-lookup"><span data-stu-id="55e15-244">To find a session configuration's value of the **OutputBufferingMode**, you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="55e15-245">您可以重写会话配置中的默认值，并在创建 PSSession、断开连接以及重新连接时设置 PSSession 的输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="55e15-245">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="55e15-246">如果你是远程计算机上 Administrators 组的成员，则可以创建和更改会话配置的输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="55e15-246">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="55e15-247">若要创建具有 **drop** 的输出缓冲模式的 PSSession，请创建一个 `$PSSessionOption` 首选项变量，其中 **OutputBufferingMode** 属性的值将被 **删除**。</span><span class="sxs-lookup"><span data-stu-id="55e15-247">To create a PSSession with an output buffering mode of **Drop**, create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop**.</span></span>

<span data-ttu-id="55e15-248">当您创建 Pssession 时，变量中的值 `$PSSessionOption` 优先于会话配置中的值。</span><span class="sxs-lookup"><span data-stu-id="55e15-248">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="55e15-249">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-249">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="55e15-250">若要创建具有 **drop** 的输出缓冲模式的 PSSession，请使用 Cmdlet 的 **OutputBufferingMode** 参数 `New-PSSessionOption` 创建具有 **drop** 值的 session 选项。</span><span class="sxs-lookup"><span data-stu-id="55e15-250">To create a PSSession with an output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="55e15-251">然后，在或 cmdlet 的 **SessionOption** 参数的值中使用 session 选项 `New-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-251">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="55e15-252">创建会话时设置的值优先于 `$PSSessionOption` 首选项变量和会话配置中设置的值。</span><span class="sxs-lookup"><span data-stu-id="55e15-252">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="55e15-253">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-253">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="55e15-254">若要在断开连接时更改 PSSession 的输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-254">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="55e15-255">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-255">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="55e15-256">若要在重新连接时更改 PSSession 的输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `New-PSSessionOption` 创建具有 **Drop** 值的 session 选项。</span><span class="sxs-lookup"><span data-stu-id="55e15-256">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="55e15-257">然后，在或的 **SessionOption** 参数的值中使用 session 选项 `Connect-PSSession` `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-257">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="55e15-258">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-258">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="55e15-259">若要创建具有 **drop** 的默认输出缓冲模式的会话配置，请使用 Cmdlet 的 **OutputBufferingMode** 参数 `New-PSTransportOption` 创建具有 **drop** 值的传输选项对象。</span><span class="sxs-lookup"><span data-stu-id="55e15-259">To create a session configuration with a default output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop**.</span></span> <span data-ttu-id="55e15-260">然后，在的 **TransportOption** 参数的值中使用 transport 选项 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-260">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="55e15-261">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-261">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="55e15-262">若要更改会话配置的默认输出缓冲模式，请使用 cmdlet 的 **OutputBufferingMode** 参数 `New-PSTransportOption` 创建具有 **Drop** 值的传输选项。</span><span class="sxs-lookup"><span data-stu-id="55e15-262">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop**.</span></span> <span data-ttu-id="55e15-263">然后，在的 **SessionOption** 参数的值中使用 Transport 选项 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="55e15-263">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="55e15-264">例如：</span><span class="sxs-lookup"><span data-stu-id="55e15-264">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="55e15-265">断开环回会话连接</span><span class="sxs-lookup"><span data-stu-id="55e15-265">Disconnecting loopback sessions</span></span>

<span data-ttu-id="55e15-266">环回会话（或本地会话）是在同一台计算机上发起和终止的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-266">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="55e15-267">与其他 Pssession 一样，活动环回会话在连接的远程端上的计算机上保持 (本地计算机) ，因此你可以断开与环回会话的连接并重新连接到环回会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-267">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="55e15-268">默认情况下，使用网络安全令牌创建环回会话，该令牌不允许在会话中运行命令来访问其他计算机。</span><span class="sxs-lookup"><span data-stu-id="55e15-268">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="55e15-269">你可以从本地计算机或远程计算机上的任何会话中重新连接到具有网络安全令牌的环回会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-269">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="55e15-270">但是，如果使用、或 cmdlet 的 **EnableNetworkAccess** 参数 `New-PSSession` ，则将 `Enter-PSSession` `Invoke-Command` 使用交互式安全令牌创建环回会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-270">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="55e15-271">交互式令牌允许在环回会话中运行的命令从其他计算机中获取数据。</span><span class="sxs-lookup"><span data-stu-id="55e15-271">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="55e15-272">可以将环回会话与交互式令牌断开连接，然后从同一台计算机上的同一会话或不同会话重新连接到这些会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-272">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="55e15-273">但是，若要防止恶意访问，你可以使用交互式令牌仅从创建它们的计算机重新连接到环回会话。</span><span class="sxs-lookup"><span data-stu-id="55e15-273">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="55e15-274">在断开连接的会话中等待作业</span><span class="sxs-lookup"><span data-stu-id="55e15-274">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="55e15-275">该 `Wait-Job` cmdlet 将等待作业完成，然后返回到命令提示符或下一个命令。</span><span class="sxs-lookup"><span data-stu-id="55e15-275">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="55e15-276">默认情况下， `Wait-Job` 如果正在运行作业的会话断开连接，则返回。</span><span class="sxs-lookup"><span data-stu-id="55e15-276">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="55e15-277">若要指示 `Wait-Job` cmdlet 等到会话重新连接，请在 "已 **打开** " 状态中使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="55e15-277">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="55e15-278">有关详细信息，请参阅 [等待作业](xref:Microsoft.PowerShell.Core.Wait-Job)。</span><span class="sxs-lookup"><span data-stu-id="55e15-278">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="55e15-279">可靠会话和无意断开连接</span><span class="sxs-lookup"><span data-stu-id="55e15-279">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="55e15-280">由于计算机故障或网络中断，PSSession 可能会无意中断开连接。</span><span class="sxs-lookup"><span data-stu-id="55e15-280">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="55e15-281">PowerShell 尝试恢复 PSSession，但其成功与否取决于原因的严重性和持续时间。</span><span class="sxs-lookup"><span data-stu-id="55e15-281">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="55e15-282">无意间断开连接的 PSSession 的状态可能会 **断开** 或 **关闭**，但也可能会 **断开连接**。</span><span class="sxs-lookup"><span data-stu-id="55e15-282">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed**, but it might also be **Disconnected**.</span></span> <span data-ttu-id="55e15-283">如果 " **状态** " 的值为 "已 **断开连接**"，则可以使用相同的方法来管理 PSSession，就像在有意断开会话的情况下一样。</span><span class="sxs-lookup"><span data-stu-id="55e15-283">If the value of **State** is **Disconnected**, you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="55e15-284">例如，你可以使用 `Connect-PSSession` cmdlet 重新连接到会话和 `Receive-PSSession` cmdlet，以获取在断开会话时运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="55e15-284">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="55e15-285">如果关闭 (exit) 在 PSSession 中运行命令时创建了 PSSession 的会话，则 PowerShell 会在远程计算机上以 **断开连接** 状态维护 pssession。</span><span class="sxs-lookup"><span data-stu-id="55e15-285">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="55e15-286">如果关闭了 (exit) 在其中创建了 PSSession 的会话，但未在 PSSession 中运行命令，则 PowerShell 不会尝试维护 PSSession。</span><span class="sxs-lookup"><span data-stu-id="55e15-286">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="55e15-287">请参阅</span><span class="sxs-lookup"><span data-stu-id="55e15-287">See also</span></span>

[<span data-ttu-id="55e15-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="55e15-288">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="55e15-289">about_Remote</span><span class="sxs-lookup"><span data-stu-id="55e15-289">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="55e15-290">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="55e15-290">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="55e15-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="55e15-291">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="55e15-292">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="55e15-292">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="55e15-293">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="55e15-293">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="55e15-294">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="55e15-294">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="55e15-295">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="55e15-295">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="55e15-296">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="55e15-296">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="55e15-297">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="55e15-297">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

