---
description: 描述如何在 PowerShell 中运行远程命令。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: b47efbaaebdd75be5f15be449e194113a0d6ebd7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598664"
---
# <a name="about-remote"></a><span data-ttu-id="dafac-103">关于远程</span><span class="sxs-lookup"><span data-stu-id="dafac-103">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="dafac-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="dafac-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="dafac-105">描述如何在 PowerShell 中运行远程命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-105">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dafac-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="dafac-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="dafac-107">您可以通过使用临时或永久连接在一台计算机或多台计算机上运行远程命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-107">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="dafac-108">你还可以使用单台远程计算机启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="dafac-108">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="dafac-109">本主题提供了一系列示例，说明如何运行不同类型的远程命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-109">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="dafac-110">尝试这些基本命令后，请阅读描述这些命令中使用的每个 cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="dafac-110">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="dafac-111">这些主题提供详细信息，并说明如何修改这些命令以满足你的需求。</span><span class="sxs-lookup"><span data-stu-id="dafac-111">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="dafac-112">注意：若要使用 PowerShell 远程处理，必须为本地和远程计算机配置远程处理。</span><span class="sxs-lookup"><span data-stu-id="dafac-112">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="dafac-113">有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-113">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="dafac-114">如何启动交互式会话 (ENTER-PSSESSION) </span><span class="sxs-lookup"><span data-stu-id="dafac-114">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="dafac-115">运行远程命令的最简单方法是启动与远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="dafac-115">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="dafac-116">会话启动时，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。</span><span class="sxs-lookup"><span data-stu-id="dafac-116">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="dafac-117">每个交互会话中只能连接到一台计算机。</span><span class="sxs-lookup"><span data-stu-id="dafac-117">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="dafac-118">若要启动交互式会话，请使用 Enter-PSSession cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dafac-118">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="dafac-119">以下命令将启动与 Server01 计算机的交互式会话：</span><span class="sxs-lookup"><span data-stu-id="dafac-119">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="dafac-120">命令提示符将发生更改，以指示你已连接到 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="dafac-120">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="dafac-121">现在，可以在 Server01 计算机上键入命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-121">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="dafac-122">若要结束交互会话，请键入：</span><span class="sxs-lookup"><span data-stu-id="dafac-122">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="dafac-123">有关详细信息，请参阅 Enter-PSSession。</span><span class="sxs-lookup"><span data-stu-id="dafac-123">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="dafac-124">如何使用具有 COMPUTERNAME 参数的 CMDLET 来获取远程数据</span><span class="sxs-lookup"><span data-stu-id="dafac-124">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="dafac-125">多个 cmdlet 具有 ComputerName 参数，可让你从远程计算机获取对象。</span><span class="sxs-lookup"><span data-stu-id="dafac-125">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="dafac-126">由于这些 cmdlet 不使用基于 WS-MANAGEMENT 的 PowerShell 远程处理，因此可以在任何运行 PowerShell 的计算机上使用这些 cmdlet 的 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="dafac-126">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="dafac-127">无需为 PowerShell 远程处理配置计算机，并且计算机无需满足远程处理的系统要求。</span><span class="sxs-lookup"><span data-stu-id="dafac-127">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="dafac-128">以下 cmdlet 具有 ComputerName 参数：</span><span class="sxs-lookup"><span data-stu-id="dafac-128">The following cmdlets have a ComputerName parameter:</span></span>

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

<span data-ttu-id="dafac-129">例如，以下命令将获取 Server01 远程计算机上的服务：</span><span class="sxs-lookup"><span data-stu-id="dafac-129">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="dafac-130">通常，支持无需特殊配置的远程处理的 cmdlet 具有 **ComputerName** 参数，但不具有 **Session** 参数。</span><span class="sxs-lookup"><span data-stu-id="dafac-130">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="dafac-131">若要在会话中查找这些 cmdlet，请键入：</span><span class="sxs-lookup"><span data-stu-id="dafac-131">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="dafac-132">如何运行远程命令</span><span class="sxs-lookup"><span data-stu-id="dafac-132">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="dafac-133">若要在远程计算机上运行其他命令，请使用 Invoke-Command cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dafac-133">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="dafac-134">若要运行单个命令或几个不相关的命令，请使用 Invoke-Command 的 ComputerName 参数来指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="dafac-134">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="dafac-135">使用 ScriptBlock 参数来指定命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-135">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="dafac-136">例如，以下命令在 Server01 计算机上运行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-136">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="dafac-137">ComputerName 参数适用于在一台或多台计算机上运行单个命令或多个不相关的命令的情况。</span><span class="sxs-lookup"><span data-stu-id="dafac-137">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="dafac-138">若要建立与远程计算机的持续性连接，请使用 Session 参数。</span><span class="sxs-lookup"><span data-stu-id="dafac-138">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="dafac-139">如何创建 (PSSESSION) 的持久连接</span><span class="sxs-lookup"><span data-stu-id="dafac-139">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="dafac-140">使用 Invoke-Command cmdlet 的 ComputerName 参数时，Windows PowerShell 只为命令建立连接。</span><span class="sxs-lookup"><span data-stu-id="dafac-140">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="dafac-141">然后，在命令完成后，它将关闭该连接。</span><span class="sxs-lookup"><span data-stu-id="dafac-141">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="dafac-142">命令中定义的任何变量或函数都将丢失。</span><span class="sxs-lookup"><span data-stu-id="dafac-142">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="dafac-143">若要创建与远程计算机的持久连接，请使用 New-PSSession cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dafac-143">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="dafac-144">例如，以下命令在 Server01 和 Server02 计算机上创建 Pssession，然后将 Pssession 保存在 $s 的变量中。</span><span class="sxs-lookup"><span data-stu-id="dafac-144">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="dafac-145">如何在 PSSESSION 中运行命令</span><span class="sxs-lookup"><span data-stu-id="dafac-145">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="dafac-146">使用 PSSession，可运行一系列共享数据的远程命令，如函数、别名和变量的值。</span><span class="sxs-lookup"><span data-stu-id="dafac-146">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="dafac-147">若要在 PSSession 中运行命令，请使用 Invoke-Command cmdlet 的 Session 参数。</span><span class="sxs-lookup"><span data-stu-id="dafac-147">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="dafac-148">例如，以下命令使用 Invoke-Command cmdlet 在 Server01 和 Server02 计算机上的 Pssession 中运行 Get-Process 命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-148">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="dafac-149">该命令将进程保存在每个 PSSession 的 $p 变量中。</span><span class="sxs-lookup"><span data-stu-id="dafac-149">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="dafac-150">由于 PSSession 使用持久性连接，因此您可以在使用 $p 变量的同一 PSSession 中运行另一个命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-150">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="dafac-151">以下命令将计算 $p 中保存的进程数。</span><span class="sxs-lookup"><span data-stu-id="dafac-151">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="dafac-152">如何在多台计算机上运行远程命令</span><span class="sxs-lookup"><span data-stu-id="dafac-152">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="dafac-153">若要在多台计算机上运行远程命令，请在 Invoke-Command 的 ComputerName 参数的值中键入所有计算机名称。</span><span class="sxs-lookup"><span data-stu-id="dafac-153">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="dafac-154">用逗号分隔名称。</span><span class="sxs-lookup"><span data-stu-id="dafac-154">Separate the names with commas.</span></span>

<span data-ttu-id="dafac-155">例如，以下命令在三台计算机上运行 Get-Culture 命令：</span><span class="sxs-lookup"><span data-stu-id="dafac-155">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="dafac-156">你还可以在多个 Pssession 中运行命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-156">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="dafac-157">以下命令在 Server01、Server02 和 Server03 计算机上创建 Pssession，然后在每个 Pssession 中运行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-157">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="dafac-158">若要包含计算机的 "本地计算机" 列表，请键入本地计算机的名称，键入点 ( ) ，或键入 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="dafac-158">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="dafac-159">如何在远程计算机上运行脚本</span><span class="sxs-lookup"><span data-stu-id="dafac-159">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="dafac-160">若要在远程计算机上运行本地脚本，请使用 Invoke 命令的 FilePath 参数。</span><span class="sxs-lookup"><span data-stu-id="dafac-160">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="dafac-161">例如，以下命令在 S1 和 S2 计算机上运行 Sample.ps1 脚本：</span><span class="sxs-lookup"><span data-stu-id="dafac-161">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="dafac-162">脚本的结果返回到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="dafac-162">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="dafac-163">不需要复制任何文件。</span><span class="sxs-lookup"><span data-stu-id="dafac-163">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="dafac-164">如何停止远程命令</span><span class="sxs-lookup"><span data-stu-id="dafac-164">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="dafac-165">若要中断命令，请按 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="dafac-165">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="dafac-166">中断请求会传递到远程计算机，并在该位置终止远程命令。</span><span class="sxs-lookup"><span data-stu-id="dafac-166">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="dafac-167">详细信息</span><span class="sxs-lookup"><span data-stu-id="dafac-167">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="dafac-168">有关远程处理的系统要求的信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-168">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="dafac-169">有关设置远程输出格式的帮助，请参阅 [about_Remote_Output](about_Remote_Output.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-169">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="dafac-170">有关远程处理的工作原理、如何管理远程数据、特殊配置、安全问题和其他常见问题的信息，请参阅 [about_Remote_FAQ](about_Remote_FAQ.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-170">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="dafac-171">有关解决远程处理错误的帮助，请参阅 about_Remote_Troubleshooting。</span><span class="sxs-lookup"><span data-stu-id="dafac-171">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="dafac-172">有关 Pssession 和持续连接的信息，请参阅 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-172">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="dafac-173">有关 PowerShell 后台作业的信息，请参阅 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="dafac-173">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="dafac-174">字</span><span class="sxs-lookup"><span data-stu-id="dafac-174">KEYWORDS</span></span>

<span data-ttu-id="dafac-175">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="dafac-175">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="dafac-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dafac-176">SEE ALSO</span></span>

[<span data-ttu-id="dafac-177">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="dafac-177">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="dafac-178">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="dafac-178">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="dafac-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="dafac-179">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="dafac-180">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="dafac-180">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="dafac-181">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="dafac-181">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="dafac-182">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="dafac-182">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="dafac-183">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="dafac-183">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="dafac-184">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="dafac-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="dafac-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dafac-185">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

