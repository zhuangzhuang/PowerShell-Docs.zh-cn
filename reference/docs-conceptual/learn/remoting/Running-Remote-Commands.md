---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: 运行远程命令
description: 介绍使用 PowerShell 在远程系统上运行命令的方法。
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391402"
---
# <a name="running-remote-commands"></a><span data-ttu-id="5331a-104">运行远程命令</span><span class="sxs-lookup"><span data-stu-id="5331a-104">Running Remote Commands</span></span>

<span data-ttu-id="5331a-105">可以使用单个 PowerShell 命令在一台或数百台计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="5331a-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="5331a-106">Windows PowerShell 通过使用各种技术（包括 WMI、RPC 和 WS-Management）支持远程计算。</span><span class="sxs-lookup"><span data-stu-id="5331a-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="5331a-107">PowerShell Core 支持 WMI、WS-Management 和 SSH 远程处理。</span><span class="sxs-lookup"><span data-stu-id="5331a-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="5331a-108">在 PowerShell 6 中，RPC 不再受支持。</span><span class="sxs-lookup"><span data-stu-id="5331a-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="5331a-109">在 PowerShell 7 及更高版本中，RPC 仅在 Windows 中受支持。</span><span class="sxs-lookup"><span data-stu-id="5331a-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="5331a-110">有关在 PowerShell Core 中进行远程处理的详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="5331a-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="5331a-111">[在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5331a-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="5331a-112">[在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5331a-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="5331a-113">无需配置即可进行 Windows PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="5331a-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="5331a-114">许多 Windows PowerShell cmdlet 都具有 ComputerName 参数，此参数可使你在一台或多台远程计算机上收集数据和更改设置。</span><span class="sxs-lookup"><span data-stu-id="5331a-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="5331a-115">这些 cmdlet 使用不同的通信协议，无需进行任何特殊配置即可在所有 Windows 操作系统上工作。</span><span class="sxs-lookup"><span data-stu-id="5331a-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="5331a-116">这些 cmdlet 包括：</span><span class="sxs-lookup"><span data-stu-id="5331a-116">These cmdlets include:</span></span>

- [<span data-ttu-id="5331a-117">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5331a-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="5331a-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="5331a-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="5331a-119">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="5331a-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="5331a-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="5331a-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="5331a-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="5331a-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="5331a-122">Get-Process</span><span class="sxs-lookup"><span data-stu-id="5331a-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="5331a-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="5331a-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="5331a-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="5331a-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="5331a-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="5331a-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="5331a-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="5331a-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="5331a-127">通常情况下，支持无需特殊配置即可进行远程处理的 cmdlet 具有 ComputerName 参数，但不具有 Session 参数。</span><span class="sxs-lookup"><span data-stu-id="5331a-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="5331a-128">若要在会话中查找这些 cmdlet，请键入：</span><span class="sxs-lookup"><span data-stu-id="5331a-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="5331a-129">Windows PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="5331a-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="5331a-130">使用 WS-Management 协议，Windows PowerShell 远程处理使你可以在一台或多台远程计算机上运行任何 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="5331a-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="5331a-131">你可以建立持久连接、启动交互会话并在远程计算机上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="5331a-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="5331a-132">若要使用 Windows PowerShell 远程处理，必须配置远程计算机以进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="5331a-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="5331a-133">有关详细信息（包括说明），请参阅[关于远程要求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。</span><span class="sxs-lookup"><span data-stu-id="5331a-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="5331a-134">一旦配置了 Windows PowerShell 远程处理，就会有许多远程处理策略可供你使用。</span><span class="sxs-lookup"><span data-stu-id="5331a-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="5331a-135">本文只列出了其中的几个策略。</span><span class="sxs-lookup"><span data-stu-id="5331a-135">This article lists just a few of them.</span></span> <span data-ttu-id="5331a-136">有关详细信息，请参阅[关于远程](/powershell/module/microsoft.powershell.core/about/about_remote)。</span><span class="sxs-lookup"><span data-stu-id="5331a-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="5331a-137">启动交互会话</span><span class="sxs-lookup"><span data-stu-id="5331a-137">Start an Interactive Session</span></span>

<span data-ttu-id="5331a-138">若要使用单台远程计算机启动交互会话，请使用 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5331a-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="5331a-139">例如，若要使用 Server01 远程计算器启动交互会话，请键入：</span><span class="sxs-lookup"><span data-stu-id="5331a-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="5331a-140">命令提示符更改为显示远程计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="5331a-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="5331a-141">你在提示符中键入的任何命令都将在远程计算机上运行，并且结果将显示在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="5331a-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="5331a-142">若要结束交互会话，请键入：</span><span class="sxs-lookup"><span data-stu-id="5331a-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="5331a-143">有关 Enter-PSSession 和 Exit-PSSession cmdlet 的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5331a-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="5331a-144">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="5331a-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="5331a-145">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="5331a-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="5331a-146">运行远程命令</span><span class="sxs-lookup"><span data-stu-id="5331a-146">Run a Remote Command</span></span>

<span data-ttu-id="5331a-147">若要在一台或多台计算机上运行一个命令，请使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5331a-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="5331a-148">例如，若要在 Server01 和 Server02 远程计算机上运行 [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) 命令，请键入：</span><span class="sxs-lookup"><span data-stu-id="5331a-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="5331a-149">输出将返回到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="5331a-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="5331a-150">运行脚本</span><span class="sxs-lookup"><span data-stu-id="5331a-150">Run a Script</span></span>

<span data-ttu-id="5331a-151">若要在一台或多台远程计算机上运行脚本，请使用 `Invoke-Command` cmdlet 的 FilePath 参数。</span><span class="sxs-lookup"><span data-stu-id="5331a-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="5331a-152">该脚本必须在你的本地计算机上或可由其访问。</span><span class="sxs-lookup"><span data-stu-id="5331a-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="5331a-153">结果将返回到你的本地计算机。</span><span class="sxs-lookup"><span data-stu-id="5331a-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="5331a-154">例如，以下命令在远程计算机 Server01 和 Server02 上运行 DiskCollect.ps1 脚本。</span><span class="sxs-lookup"><span data-stu-id="5331a-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="5331a-155">建立持久连接</span><span class="sxs-lookup"><span data-stu-id="5331a-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="5331a-156">使用 `New-PSSession` cmdlet 在远程计算机上创建一个持久会话。</span><span class="sxs-lookup"><span data-stu-id="5331a-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="5331a-157">以下示例在 Server01 和 Server02 上创建远程会话。</span><span class="sxs-lookup"><span data-stu-id="5331a-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="5331a-158">会话对象存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="5331a-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="5331a-159">建立会话后，你可以在这些会话中运行任何命令。</span><span class="sxs-lookup"><span data-stu-id="5331a-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="5331a-160">此外，由于会话是持久的，因此你可以从一个命令收集数据，并在另一个命令中使用它。</span><span class="sxs-lookup"><span data-stu-id="5331a-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="5331a-161">例如，下面的命令在 $s 变量中的会话中运行 Get-Hotfix 命令，并且它将结果保存在 $h 变量中。</span><span class="sxs-lookup"><span data-stu-id="5331a-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="5331a-162">将在 $s 中的每个会话中创建 $h 变量，但它不会存在于本地会话中。</span><span class="sxs-lookup"><span data-stu-id="5331a-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="5331a-163">现在，可以将 `$h` 变量中的数据与同一会话中的其他命令一起使用。</span><span class="sxs-lookup"><span data-stu-id="5331a-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="5331a-164">结果将显示在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="5331a-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="5331a-165">例如：</span><span class="sxs-lookup"><span data-stu-id="5331a-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="5331a-166">高级远程处理</span><span class="sxs-lookup"><span data-stu-id="5331a-166">Advanced Remoting</span></span>

<span data-ttu-id="5331a-167">Windows PowerShell 远程管理就在此处开始。</span><span class="sxs-lookup"><span data-stu-id="5331a-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="5331a-168">通过使用随 Windows PowerShell 一起安装的 cmdlet，你可以从本地和远程端点建立和配置远程会话、创建自定义和受限制的会话、允许用户从实际在远程会话上隐式运行的远程会话中导入命令、配置远程会话的安全性等。</span><span class="sxs-lookup"><span data-stu-id="5331a-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="5331a-169">Windows PowerShell 包含一个 WSMan 提供程序。</span><span class="sxs-lookup"><span data-stu-id="5331a-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="5331a-170">提供程序创建 `WSMAN:` 驱动器，允许你在本地计算机和远程计算机上的配置设置层次结构之间导航。</span><span class="sxs-lookup"><span data-stu-id="5331a-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="5331a-171">有关 WSMan 提供程序的详细信息，请参阅 [WSMan 提供程序](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)和[关于 WS-Management Cmdlet](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)，或在 Windows PowerShell 控制台中键入 `Get-Help wsman`。</span><span class="sxs-lookup"><span data-stu-id="5331a-171">For more information about the WSMan provider, see [WSMan Provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="5331a-172">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5331a-172">For more information, see:</span></span>

- [<span data-ttu-id="5331a-173">关于远程 FAQ</span><span class="sxs-lookup"><span data-stu-id="5331a-173">About Remote FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="5331a-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5331a-174">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="5331a-175">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5331a-175">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

<span data-ttu-id="5331a-176">有关远程处理错误的帮助，请参阅 [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)。</span><span class="sxs-lookup"><span data-stu-id="5331a-176">For help with remoting errors, see [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span></span>

## <a name="see-also"></a><span data-ttu-id="5331a-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5331a-177">See Also</span></span>

- [<span data-ttu-id="5331a-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5331a-178">about_Remote</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="5331a-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="5331a-179">about_Remote_FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="5331a-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="5331a-180">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [<span data-ttu-id="5331a-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="5331a-181">about_Remote_Troubleshooting</span></span>](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [<span data-ttu-id="5331a-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5331a-182">about_PSSessions</span></span>](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [<span data-ttu-id="5331a-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5331a-183">about_WS-Management_Cmdlets</span></span>](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [<span data-ttu-id="5331a-184">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="5331a-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="5331a-185">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5331a-185">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [<span data-ttu-id="5331a-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5331a-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="5331a-187">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5331a-187">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="5331a-188">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="5331a-188">WSMan Provider</span></span>](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
