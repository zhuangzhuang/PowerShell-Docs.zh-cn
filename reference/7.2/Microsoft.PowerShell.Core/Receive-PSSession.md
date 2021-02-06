---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 4bc7ba3a8129dd332b13bee30e386dd459d92226
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596436"
---
# <span data-ttu-id="8ac06-102">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-102">Receive-PSSession</span></span>

## <span data-ttu-id="8ac06-103">摘要</span><span class="sxs-lookup"><span data-stu-id="8ac06-103">SYNOPSIS</span></span>

<span data-ttu-id="8ac06-104">获取断开连接的会话中的命令的结果</span><span class="sxs-lookup"><span data-stu-id="8ac06-104">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="8ac06-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ac06-105">SYNTAX</span></span>

### <span data-ttu-id="8ac06-106">会话（默认）</span><span class="sxs-lookup"><span data-stu-id="8ac06-106">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-107">ID</span><span class="sxs-lookup"><span data-stu-id="8ac06-107">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="8ac06-108">ComputerSessionName</span><span class="sxs-lookup"><span data-stu-id="8ac06-108">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="8ac06-109">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-110">ConnectionUriSessionName</span><span class="sxs-lookup"><span data-stu-id="8ac06-110">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-111">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="8ac06-111">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8ac06-112">InstanceId</span></span>

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8ac06-113">SessionName</span><span class="sxs-lookup"><span data-stu-id="8ac06-113">SessionName</span></span>

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="8ac06-114">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8ac06-114">DESCRIPTION</span></span>

<span data-ttu-id="8ac06-115">该 `Receive-PSSession` cmdlet 将获取已断开连接 (**PSSession**) 在 PowerShell 会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-115">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions (**PSSession**) that were disconnected.</span></span> <span data-ttu-id="8ac06-116">如果会话当前已连接，则 `Receive-PSSession` 获取在断开会话连接时正在运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-116">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="8ac06-117">如果会话仍处于断开连接状态，将 `Receive-PSSession` 连接到该会话，恢复已挂起的任何命令，并获取在该会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-117">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="8ac06-118">此 cmdlet 是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="8ac06-118">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="8ac06-119">除命令外，还可以使用 `Receive-PSSession` 或而不是 `Connect-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-119">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="8ac06-120">`Receive-PSSession` 可以连接到在其他会话中或在其他计算机上启动的任何断开连接或重新连接的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-120">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="8ac06-121">`Receive-PSSession`适用于使用 `Disconnect-PSSession` cmdlet 或 `Invoke-Command` **InDisconnectedSession** 参数故意断开连接的 pssession。</span><span class="sxs-lookup"><span data-stu-id="8ac06-121">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="8ac06-122">或无意中断开了网络中断。</span><span class="sxs-lookup"><span data-stu-id="8ac06-122">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="8ac06-123">如果使用 `Receive-PSSession` cmdlet 连接到没有运行或挂起的命令的会话，将 `Receive-PSSession` 连接到该会话，但不会返回任何输出或错误。</span><span class="sxs-lookup"><span data-stu-id="8ac06-123">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="8ac06-124">有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-124">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="8ac06-125">一些示例使用展开缩短行长度，提高可读性。</span><span class="sxs-lookup"><span data-stu-id="8ac06-125">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="8ac06-126">有关详细信息，请参阅 [about_Splatting](./About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-126">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="8ac06-127">示例</span><span class="sxs-lookup"><span data-stu-id="8ac06-127">EXAMPLES</span></span>

### <span data-ttu-id="8ac06-128">示例1：连接到 PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-128">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="8ac06-129">此示例连接到远程计算机上的会话，并获取正在会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-129">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="8ac06-130">`Receive-PSSession`用 **ComputerName** 参数指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-130">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="8ac06-131">**Name** 参数标识 Server01 计算机上的 ITTask 会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-131">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="8ac06-132">该示例获取在 ITTask 会话中运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-132">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="8ac06-133">由于该命令不使用 **OutTarget** 参数，因此结果将显示在命令行上。</span><span class="sxs-lookup"><span data-stu-id="8ac06-133">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="8ac06-134">示例2：获取断开连接的会话上的所有命令的结果</span><span class="sxs-lookup"><span data-stu-id="8ac06-134">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="8ac06-135">此示例获取在两台远程计算机上的所有已断开连接的会话中运行的所有命令的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-135">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="8ac06-136">如果任何会话未断开连接或未运行命令，则 `Receive-PSSession` 不会连接到会话，并且不会返回任何输出或错误。</span><span class="sxs-lookup"><span data-stu-id="8ac06-136">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="8ac06-137">`Get-PSSession` 使用 **ComputerName** 参数来指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-137">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="8ac06-138">对象将向下发送到 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-138">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="8ac06-139">示例3：获取会话中运行的脚本的结果</span><span class="sxs-lookup"><span data-stu-id="8ac06-139">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="8ac06-140">此示例使用 `Receive-PSSession` cmdlet 获取在远程计算机的会话中运行的脚本的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-140">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="8ac06-141">该命令使用 **ComputerName** 和 **Name** 参数来标识断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-141">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="8ac06-142">它将 **OutTarget** 参数与的值一起使用，以指示将 `Receive-PSSession` 结果作为作业返回。</span><span class="sxs-lookup"><span data-stu-id="8ac06-142">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="8ac06-143">**JobName** 参数在重新连接的会话中指定作业的名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-143">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="8ac06-144">**Credential** 参数 `Receive-PSSession` 使用域管理员的权限运行命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-144">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="8ac06-145">输出显示将 `Receive-PSSession` 结果作为作业返回到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-145">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="8ac06-146">若要获取作业结果，请使用 `Receive-Job` 命令</span><span class="sxs-lookup"><span data-stu-id="8ac06-146">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="8ac06-147">示例4：在网络中断后获取结果</span><span class="sxs-lookup"><span data-stu-id="8ac06-147">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="8ac06-148">此示例在 `Receive-PSSession` 网络中断中断会话连接后，使用 cmdlet 来获取作业的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-148">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="8ac06-149">PowerShell 会在接下来的4分钟内自动尝试重新连接会话一次，并且仅当四分钟时间间隔内的所有尝试均失败时，才放弃工作。</span><span class="sxs-lookup"><span data-stu-id="8ac06-149">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="8ac06-150">`New-PSSession`Cmdlet 在 Server01 计算机上创建会话，并将会话保存在变量中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-150">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="8ac06-151">`$s`变量显示 **状态** 为已打开且 **可用性** 可用。</span><span class="sxs-lookup"><span data-stu-id="8ac06-151">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="8ac06-152">这些值表明你已连接到该会话，并且可以在该会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-152">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="8ac06-153">Cmdlet 在该 `Invoke-Command` 变量的会话中运行脚本 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-153">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="8ac06-154">该脚本开始运行并返回数据，但如果出现网络故障，可能会中断该会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-154">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="8ac06-155">用户必须退出该会话并重新启动本地计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-155">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="8ac06-156">当计算机重新启动时，用户启动 PowerShell 并运行 `Get-PSSession` 命令来获取 Server01 计算机上的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-156">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="8ac06-157">此输出显示 **AD** 会话仍存在于 Server01 计算机上。</span><span class="sxs-lookup"><span data-stu-id="8ac06-157">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="8ac06-158">该 **状态** 指示 **AD** 会话已断开连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-158">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="8ac06-159">"无" 的 **可用性** 值指示该会话未连接到任何客户端会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-159">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="8ac06-160">`Receive-PSSession`Cmdlet 可重新连接到 **AD** 会话，并获取在该会话中运行的脚本的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-160">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="8ac06-161">该命令使用 **OutTarget** 参数来请求名为 **ADJob** 的作业中的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-161">The command uses the **OutTarget** parameter to request the results in a job named **ADJob**.</span></span> <span data-ttu-id="8ac06-162">该命令返回一个作业对象，输出指示该脚本仍在运行。</span><span class="sxs-lookup"><span data-stu-id="8ac06-162">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="8ac06-163">`Get-PSSession`Cmdlet 用于检查作业状态。</span><span class="sxs-lookup"><span data-stu-id="8ac06-163">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="8ac06-164">输出确认 `Receive-PSSession` cmdlet 已重新连接到 **AD** 会话，后者现在已打开且可用于命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-164">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="8ac06-165">而且，该脚本将继续执行并获得脚本结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-165">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="8ac06-166">示例5：重新连接到断开连接的会话</span><span class="sxs-lookup"><span data-stu-id="8ac06-166">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="8ac06-167">此示例使用 `Receive-PSSession` cmdlet 重新连接到有意断开连接的会话，并获取正在会话中运行的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-167">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="8ac06-168">`Invoke-Command`Cmdlet 在三台远程计算机上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="8ac06-168">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="8ac06-169">由于该脚本收集并汇总多个数据库中的数据，因此它通常会延长脚本的时间。</span><span class="sxs-lookup"><span data-stu-id="8ac06-169">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="8ac06-170">该命令使用 **InDisconnectedSession** 参数，该参数可启动脚本，然后立即断开会话连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-170">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="8ac06-171">**SessionOption** 参数扩展已断开连接的会话的 **IdleTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-171">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="8ac06-172">断开连接的会话在断开连接后被视为处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="8ac06-172">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="8ac06-173">务必将空闲超时设置为足够长的时间，以便这些命令可以完成，你可以重新连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-173">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="8ac06-174">仅当你创建 **PSSession** 并在断开连接时进行更改时才可以设置 **IdleTimeout** 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-174">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="8ac06-175">当你连接到 **PSSession** 或接收其结果时，无法更改 **IdleTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-175">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="8ac06-176">运行该命令后，用户将退出 PowerShell 并关闭计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-176">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="8ac06-177">接下来，用户恢复 Windows，启动 PowerShell，并使用 `Get-PSSession` 来获取运行脚本的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-177">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="8ac06-178">此命令通过计算机名称、会话名称和会话配置的名称来标识会话，并将会话保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-178">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="8ac06-179">将显示变量的值， `$s` 并显示会话已断开连接，但不会处于繁忙状态。</span><span class="sxs-lookup"><span data-stu-id="8ac06-179">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="8ac06-180">`Receive-PSSession`Cmdlet 连接到变量中的会话 `$s` 并获取其结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-180">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="8ac06-181">该命令将结果保存在 `$Results` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-181">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="8ac06-182">将 `$s` 显示变量，并显示会话已连接并且可用于命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-182">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="8ac06-183">在 `$Results` PowerShell 控制台中显示变量中的脚本结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-183">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="8ac06-184">如果任何结果是意外的，则用户可以在会话中运行命令来调查根本原因。</span><span class="sxs-lookup"><span data-stu-id="8ac06-184">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="8ac06-185">示例6：在断开连接的会话中运行作业</span><span class="sxs-lookup"><span data-stu-id="8ac06-185">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="8ac06-186">此示例显示在断开连接的会话中运行的作业会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="8ac06-186">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="8ac06-187">`New-PSSession`Cmdlet 在 Server01 计算机上创建测试会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-187">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="8ac06-188">该命令将该会话保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-188">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="8ac06-189">`Invoke-Command`Cmdlet 在该变量的会话中运行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-189">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="8ac06-190">该命令使用 **AsJob** 参数将命令作为作业运行，并在当前会话中创建作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-190">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="8ac06-191">命令返回保存在变量中的作业对象 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-191">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="8ac06-192">`$j`变量显示作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-192">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="8ac06-193">变量中的 session 对象 `$s` 会向下发送到管道 `Disconnect-PSSession` ，并且会话将断开连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-193">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="8ac06-194">将 `$j` 显示变量并显示断开变量中的作业对象的影响 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-194">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="8ac06-195">现在，该作业状态为“Disconnected”。</span><span class="sxs-lookup"><span data-stu-id="8ac06-195">The job state is now Disconnected.</span></span>

<span data-ttu-id="8ac06-196">对 `Receive-Job` 变量中的作业运行 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-196">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="8ac06-197">输出显示作业开始在会话之前返回输出，而作业已断开连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-197">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="8ac06-198">`Connect-PSSession`Cmdlet 在同一客户端会话中运行。</span><span class="sxs-lookup"><span data-stu-id="8ac06-198">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="8ac06-199">命令重新连接到 Server01 计算机上的测试会话，并将会话保存在 `$s2` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-199">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="8ac06-200">`Receive-PSSession`Cmdlet 可获取会话中正在运行的作业的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-200">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="8ac06-201">由于此命令在同一会话中运行，因此 `Receive-PSSession` 默认情况下会将结果作为作业返回，并重复使用同一作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-201">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="8ac06-202">该命令将作业保存在 `$j2` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-202">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="8ac06-203">`Receive-Job`Cmdlet 将获取该作业在变量中的结果 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-203">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="8ac06-204">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ac06-204">PARAMETERS</span></span>

### <span data-ttu-id="8ac06-205">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="8ac06-205">-AllowRedirection</span></span>

<span data-ttu-id="8ac06-206">指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。</span><span class="sxs-lookup"><span data-stu-id="8ac06-206">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="8ac06-207">使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。</span><span class="sxs-lookup"><span data-stu-id="8ac06-207">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="8ac06-208">默认情况下，PowerShell 不会重定向连接，但你可以使用此参数使其重定向连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-208">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="8ac06-209">你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。</span><span class="sxs-lookup"><span data-stu-id="8ac06-209">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="8ac06-210">使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置首选项变量的 **MaximumConnectionRedirectionCount** 属性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-210">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="8ac06-211">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="8ac06-211">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-212">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="8ac06-212">-ApplicationName</span></span>

<span data-ttu-id="8ac06-213">指定应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ac06-213">Specifies an application.</span></span> <span data-ttu-id="8ac06-214">此 cmdlet 仅连接到使用指定应用程序的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-214">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="8ac06-215">输入连接 URI 的应用程序名称段。</span><span class="sxs-lookup"><span data-stu-id="8ac06-215">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="8ac06-216">例如，在以下连接 URI 中，WSMan 为应用程序名称： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-216">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="8ac06-217">会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-217">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="8ac06-218">参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-218">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="8ac06-219">它不会更改会话使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ac06-219">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-220">-Authentication</span><span class="sxs-lookup"><span data-stu-id="8ac06-220">-Authentication</span></span>

<span data-ttu-id="8ac06-221">指定用于对命令中的用户凭据进行身份验证的机制，以便重新连接到断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-221">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="8ac06-222">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="8ac06-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8ac06-223">默认</span><span class="sxs-lookup"><span data-stu-id="8ac06-223">Default</span></span>
- <span data-ttu-id="8ac06-224">基本</span><span class="sxs-lookup"><span data-stu-id="8ac06-224">Basic</span></span>
- <span data-ttu-id="8ac06-225">Credssp</span><span class="sxs-lookup"><span data-stu-id="8ac06-225">Credssp</span></span>
- <span data-ttu-id="8ac06-226">摘要</span><span class="sxs-lookup"><span data-stu-id="8ac06-226">Digest</span></span>
- <span data-ttu-id="8ac06-227">Kerberos</span><span class="sxs-lookup"><span data-stu-id="8ac06-227">Kerberos</span></span>
- <span data-ttu-id="8ac06-228">Negotiate</span><span class="sxs-lookup"><span data-stu-id="8ac06-228">Negotiate</span></span>
- <span data-ttu-id="8ac06-229">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="8ac06-229">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="8ac06-230">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="8ac06-230">The default value is Default.</span></span>

<span data-ttu-id="8ac06-231">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-231">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="8ac06-232">凭据安全支持提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-232">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="8ac06-233">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="8ac06-233">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="8ac06-234">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-234">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-235">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="8ac06-235">-CertificateThumbprint</span></span>

<span data-ttu-id="8ac06-236">指定有权连接到断开连接的会话的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-236">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="8ac06-237">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="8ac06-237">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="8ac06-238">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="8ac06-238">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="8ac06-239">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="8ac06-239">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="8ac06-240">若要获取证书指纹，请 `Get-Item` `Get-ChildItem` 在 PowerShell 驱动器中使用或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-240">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-241">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8ac06-241">-ComputerName</span></span>

<span data-ttu-id="8ac06-242">指定在其中存储断开连接的会话的计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-242">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="8ac06-243">会话存储在位于服务器端或接收到连接的计算机上的计算机上。</span><span class="sxs-lookup"><span data-stu-id="8ac06-243">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="8ac06-244">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="8ac06-244">The default is the local computer.</span></span>

<span data-ttu-id="8ac06-245">键入一台计算机 (FQDN) 的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="8ac06-245">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="8ac06-246">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="8ac06-246">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="8ac06-247">若要指定本地计算机，请键入计算机名、点 (`.`) 、 `$env:COMPUTERNAME` 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="8ac06-247">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-248">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="8ac06-248">-ConfigurationName</span></span>

<span data-ttu-id="8ac06-249">指定会话配置的名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-249">Specifies the name of a session configuration.</span></span> <span data-ttu-id="8ac06-250">此 cmdlet 仅连接到使用指定会话配置的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-250">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="8ac06-251">输入会话配置的配置名称或完全限定的资源 URI。</span><span class="sxs-lookup"><span data-stu-id="8ac06-251">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="8ac06-252">如果只指定配置名称，则将在其前面预置以下架构 URI：</span><span class="sxs-lookup"><span data-stu-id="8ac06-252">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="8ac06-253">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="8ac06-253">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="8ac06-254">会话的配置名称存储在该会话的 **ConfigurationName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-254">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="8ac06-255">参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-255">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="8ac06-256">它不会更改会话使用的会话配置。</span><span class="sxs-lookup"><span data-stu-id="8ac06-256">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="8ac06-257">有关会话配置的详细信息，请参阅 [about_Session_Configurations](./About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-257">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-258">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8ac06-258">-ConnectionUri</span></span>

<span data-ttu-id="8ac06-259">指定一个 URI，该 URI 定义用于重新连接到断开连接的会话的连接终结点。</span><span class="sxs-lookup"><span data-stu-id="8ac06-259">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="8ac06-260">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="8ac06-260">The URI must be fully qualified.</span></span> <span data-ttu-id="8ac06-261">此字符串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="8ac06-261">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="8ac06-262">默认值如下：</span><span class="sxs-lookup"><span data-stu-id="8ac06-262">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="8ac06-263">如果未指定连接 URI，则可以使用 **UseSSL**、 **ComputerName**、 **Port** 和 **ApplicationName** 参数来指定连接 uri 值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-263">If you don't specify a connection URI, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="8ac06-264">URI 的 **Transport** 段的有效值为 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="8ac06-264">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="8ac06-265">如果使用传输段指定连接 URI，但未指定端口，则将使用标准端口80创建会话，并使用标准端口（用于 HTTP）和443（用于 HTTPS）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-265">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="8ac06-266">若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。</span><span class="sxs-lookup"><span data-stu-id="8ac06-266">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="8ac06-267">如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。</span><span class="sxs-lookup"><span data-stu-id="8ac06-267">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-268">-Credential</span><span class="sxs-lookup"><span data-stu-id="8ac06-268">-Credential</span></span>

<span data-ttu-id="8ac06-269">指定有权连接到断开连接的会话的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8ac06-269">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="8ac06-270">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="8ac06-270">The default is the current user.</span></span>

<span data-ttu-id="8ac06-271">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-271">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8ac06-272">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="8ac06-272">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="8ac06-273">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-273">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8ac06-274">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-274">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-275">-Id</span><span class="sxs-lookup"><span data-stu-id="8ac06-275">-Id</span></span>

<span data-ttu-id="8ac06-276">指定断开连接的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="8ac06-276">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="8ac06-277">仅当断开连接的会话之前已连接到当前会话时， **Id** 参数才有效。</span><span class="sxs-lookup"><span data-stu-id="8ac06-277">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="8ac06-278">如果会话存储在本地计算机上，但未连接到当前会话，则此参数有效但无效。</span><span class="sxs-lookup"><span data-stu-id="8ac06-278">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-279">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="8ac06-279">-InstanceId</span></span>

<span data-ttu-id="8ac06-280">指定断开连接的会话的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="8ac06-280">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="8ac06-281">实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-281">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="8ac06-282">实例 ID 存储在 **PSSession** 的 **InstanceID** 属性中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-282">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-283">-JobName</span><span class="sxs-lookup"><span data-stu-id="8ac06-283">-JobName</span></span>

<span data-ttu-id="8ac06-284">为返回的作业指定一个友好名称 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-284">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="8ac06-285">`Receive-PSSession` 如果 **OutTarget** 参数的值为作业，或在断开连接的会话中运行的作业已在当前会话中启动，则返回一个作业。</span><span class="sxs-lookup"><span data-stu-id="8ac06-285">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="8ac06-286">如果在断开连接的会话中运行的作业已在当前会话中启动，则 PowerShell 将重用会话中的原始作业对象，并忽略 **JobName** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-286">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="8ac06-287">如果在断开连接的会话中运行的作业已在其他会话中启动，则 PowerShell 会创建一个新的作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-287">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="8ac06-288">它使用默认名称，但你可以使用此参数来更改名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-288">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="8ac06-289">如果 **OutTarget** 参数的默认值或显式值不是 "作业"，则该命令将成功，但 **JobName** 参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="8ac06-289">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-290">-Name</span><span class="sxs-lookup"><span data-stu-id="8ac06-290">-Name</span></span>

<span data-ttu-id="8ac06-291">指定断开连接的会话的友好名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-291">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-292">-OutTarget</span><span class="sxs-lookup"><span data-stu-id="8ac06-292">-OutTarget</span></span>

<span data-ttu-id="8ac06-293">确定如何返回会话结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-293">Determines how the session results are returned.</span></span> <span data-ttu-id="8ac06-294">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="8ac06-294">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8ac06-295">**作业**。</span><span class="sxs-lookup"><span data-stu-id="8ac06-295">**Job**.</span></span> <span data-ttu-id="8ac06-296">在作业对象中异步返回结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-296">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="8ac06-297">你可以使用 **JobName** 参数来指定作业的名称或新名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-297">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="8ac06-298">**主机**。</span><span class="sxs-lookup"><span data-stu-id="8ac06-298">**Host**.</span></span> <span data-ttu-id="8ac06-299">将结果返回到命令行（同步）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-299">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="8ac06-300">如果正在恢复该命令或者结果由大量对象组成，则可能会延迟响应。</span><span class="sxs-lookup"><span data-stu-id="8ac06-300">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="8ac06-301">**OutTarget** 参数的默认值为 Host。</span><span class="sxs-lookup"><span data-stu-id="8ac06-301">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="8ac06-302">如果在断开连接的会话中接收的命令是在当前会话中启动的，则 **OutTarget** 参数的默认值是命令的启动形式。</span><span class="sxs-lookup"><span data-stu-id="8ac06-302">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="8ac06-303">如果命令作为作业启动，则默认情况下，它作为作业返回。</span><span class="sxs-lookup"><span data-stu-id="8ac06-303">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="8ac06-304">否则，默认情况下，它将返回到主机程序。</span><span class="sxs-lookup"><span data-stu-id="8ac06-304">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="8ac06-305">通常，主机程序会立即在命令行中显示返回的对象，但是此行为会有所不同。</span><span class="sxs-lookup"><span data-stu-id="8ac06-305">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-306">-Port</span><span class="sxs-lookup"><span data-stu-id="8ac06-306">-Port</span></span>

<span data-ttu-id="8ac06-307">指定用于重新连接到会话的远程计算机的网络端口。</span><span class="sxs-lookup"><span data-stu-id="8ac06-307">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="8ac06-308">若要连接到远程计算机，它必须侦听连接使用的端口。</span><span class="sxs-lookup"><span data-stu-id="8ac06-308">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="8ac06-309">默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-309">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="8ac06-310">使用备用端口之前，必须在远程计算机上配置 WinRM 侦听器，以便侦听该端口。</span><span class="sxs-lookup"><span data-stu-id="8ac06-310">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="8ac06-311">若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：</span><span class="sxs-lookup"><span data-stu-id="8ac06-311">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="8ac06-312">除非有必要，否则不要使用 **Port** 参数。</span><span class="sxs-lookup"><span data-stu-id="8ac06-312">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="8ac06-313">命令中设置的端口适用于运行该命令的所有计算机或会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-313">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="8ac06-314">备用端口设置可能会阻止在所有计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-314">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-315">-Session</span><span class="sxs-lookup"><span data-stu-id="8ac06-315">-Session</span></span>

<span data-ttu-id="8ac06-316">指定断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-316">Specifies the disconnected session.</span></span> <span data-ttu-id="8ac06-317">输入包含 **pssession** 的变量或者创建或获取 **pssession** 的命令（如 `Get-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-317">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-318">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="8ac06-318">-SessionOption</span></span>

<span data-ttu-id="8ac06-319">为该会话指定高级选项。</span><span class="sxs-lookup"><span data-stu-id="8ac06-319">Specifies advanced options for the session.</span></span> <span data-ttu-id="8ac06-320">输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-320">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="8ac06-321">选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-321">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="8ac06-322">否则，通过在会话配置中设置的选项创建默认值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-322">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="8ac06-323">会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-323">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="8ac06-324">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="8ac06-324">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="8ac06-325">有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-325">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="8ac06-326">有关 **$PSSessionOption** 首选项变量的信息，请参阅 [about_Preference_Variables](./About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-326">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="8ac06-327">有关会话配置的详细信息，请参阅 [about_Session_Configurations](./About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-327">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-328">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="8ac06-328">-UseSSL</span></span>

<span data-ttu-id="8ac06-329">指示此 cmdlet 使用安全套接字层 (SSL) 协议连接到断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-329">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="8ac06-330">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="8ac06-330">By default, SSL isn't used.</span></span>

<span data-ttu-id="8ac06-331">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="8ac06-331">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="8ac06-332">**UseSSL** 是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。</span><span class="sxs-lookup"><span data-stu-id="8ac06-332">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="8ac06-333">如果使用此参数，并且 SSL 在用于命令的端口上不可用，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="8ac06-333">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-334">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8ac06-334">-Confirm</span></span>

<span data-ttu-id="8ac06-335">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="8ac06-335">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-336">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8ac06-336">-WhatIf</span></span>

<span data-ttu-id="8ac06-337">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="8ac06-337">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8ac06-338">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="8ac06-338">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ac06-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ac06-339">CommonParameters</span></span>

<span data-ttu-id="8ac06-340">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8ac06-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ac06-341">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ac06-342">输入</span><span class="sxs-lookup"><span data-stu-id="8ac06-342">INPUTS</span></span>

### <span data-ttu-id="8ac06-343">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-343">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="8ac06-344">你可以通过管道将会话对象传递给此 cmdlet，例如 cmdlet 返回的对象 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-344">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="8ac06-345">System.Int32</span><span class="sxs-lookup"><span data-stu-id="8ac06-345">System.Int32</span></span>

<span data-ttu-id="8ac06-346">可以将会话 Id 通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ac06-346">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="8ac06-347">System.Guid</span><span class="sxs-lookup"><span data-stu-id="8ac06-347">System.Guid</span></span>

<span data-ttu-id="8ac06-348">可以通过管道将会话的实例 Id 传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ac06-348">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="8ac06-349">System.String</span><span class="sxs-lookup"><span data-stu-id="8ac06-349">System.String</span></span>

<span data-ttu-id="8ac06-350">可以通过管道将会话名称传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ac06-350">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="8ac06-351">输出</span><span class="sxs-lookup"><span data-stu-id="8ac06-351">OUTPUTS</span></span>

### <span data-ttu-id="8ac06-352">System.web、或 PSObject</span><span class="sxs-lookup"><span data-stu-id="8ac06-352">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="8ac06-353">此 cmdlet 将返回在断开连接的会话中运行的命令的结果（如果有）。</span><span class="sxs-lookup"><span data-stu-id="8ac06-353">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="8ac06-354">如果 **OutTarget** 参数的值或默认值为 job，则 `Receive-PSSession` 返回一个作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-354">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="8ac06-355">否则，它将返回表示命令结果的对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-355">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="8ac06-356">注释</span><span class="sxs-lookup"><span data-stu-id="8ac06-356">NOTES</span></span>

<span data-ttu-id="8ac06-357">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="8ac06-357">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="8ac06-358">`Receive-PSSession` 仅从已断开连接的会话中获取结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-358">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="8ac06-359">只有连接到或终止运行 PowerShell 3.0 或更高版本的计算机的会话才能断开和重新连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-359">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="8ac06-360">如果在断开连接的会话中运行的命令未生成结果，或结果已返回到另一个会话，则 `Receive-PSSession` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="8ac06-360">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="8ac06-361">会话的输出缓冲模式确定会话断开连接时会话中的命令如何管理输出。</span><span class="sxs-lookup"><span data-stu-id="8ac06-361">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="8ac06-362">当删除会话的 **OutputBufferingMode** 选项的值并且输出缓冲区已满时，该命令将开始删除输出。</span><span class="sxs-lookup"><span data-stu-id="8ac06-362">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="8ac06-363">`Receive-PSSession` 无法恢复此输出。</span><span class="sxs-lookup"><span data-stu-id="8ac06-363">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="8ac06-364">有关输出缓冲模式选项的详细信息，请参阅 [PSSessionOption](New-PSSessionOption.md) 和 [new-pstransportoption](New-PSTransportOption.md) cmdlet 的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="8ac06-364">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="8ac06-365">当你连接到 **pssession** 或接收结果时，你无法更改 **PSSession** 的空闲超时值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-365">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="8ac06-366">的 **SessionOption** 参数 `Receive-PSSession` 采用具有 **IdleTimeout** 值的 **SessionOption** 对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-366">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="8ac06-367">但是，在   `$PSSessionOption` 连接到 **PSSession** 或接收结果时，将忽略 SessionOption 对象的 idletimeout 值和该变量的 idletimeout 值。</span><span class="sxs-lookup"><span data-stu-id="8ac06-367">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="8ac06-368">您可以在创建 **pssession** 时，通过使用 `New-PSSession` 或 `Invoke-Command` cmdlet 以及从 **Pssession** 断开连接来设置和更改 pssession 的空闲超时。</span><span class="sxs-lookup"><span data-stu-id="8ac06-368">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>
- <span data-ttu-id="8ac06-369">**PSSession** 的 **IdleTimeout** 属性对断开连接的会话至关重要，因为它确定断开连接的会话在远程计算机上保留的时间。</span><span class="sxs-lookup"><span data-stu-id="8ac06-369">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="8ac06-370">断开连接的会话从其断开连接的时刻起就被视为空闲，即使命令正在断开连接的会话中运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="8ac06-370">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="8ac06-371">如果使用 cmdlet 的 **AsJob** 参数在远程会话中启动作业 `Invoke-Command` ，则会在当前会话中创建作业对象，即使该作业在远程会话中运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="8ac06-371">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="8ac06-372">如果断开与远程会话的连接，则当前会话中的作业对象会断开与该作业的连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-372">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="8ac06-373">作业对象包含返回给它的任何结果，但不会从已断开连接的会话中的作业接收到新结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-373">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="8ac06-374">如果其他客户端连接到包含正在运行的作业的会话，则在新连接的会话中，传递给原始会话中的原始作业对象的结果不可用。</span><span class="sxs-lookup"><span data-stu-id="8ac06-374">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="8ac06-375">在重新连接的会话中只能使用未传递给原始作业对象的结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-375">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="8ac06-376">同样，如果在会话中启动脚本，然后断开与该会话的连接，则该脚本在断开连接之前传递给该会话的所有结果都不能用于连接到该会话的其他客户端。</span><span class="sxs-lookup"><span data-stu-id="8ac06-376">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="8ac06-377">若要防止要断开连接的会话中的数据丢失，请使用 cmdlet 的 **InDisconnectedSession** 参数 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="8ac06-377">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="8ac06-378">由于此参数会阻止结果返回到当前会话，因此在重新连接该会话后所有结果均可用。</span><span class="sxs-lookup"><span data-stu-id="8ac06-378">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="8ac06-379">还可以通过使用 `Invoke-Command` cmdlet `Start-Job` 在远程会话中运行命令来防止数据丢失。</span><span class="sxs-lookup"><span data-stu-id="8ac06-379">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="8ac06-380">在此情况下，将在远程会话中创建作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-380">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="8ac06-381">不能使用 `Receive-PSSession` cmdlet 来获取作业结果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-381">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="8ac06-382">请改用 `Connect-PSSession` cmdlet 连接到会话，然后使用 `Invoke-Command` cmdlet `Receive-Job` 在会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="8ac06-382">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="8ac06-383">当包含正在运行的作业的会话断开连接，然后重新连接后，仅当该作业断开连接并重新连接到同一会话时才会重新使用原始作业对象，并且用于重新连接的命令不指定新的作业名称。</span><span class="sxs-lookup"><span data-stu-id="8ac06-383">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="8ac06-384">如果会话重新连接到其他客户端会话或者指定了新的作业名称，PowerShell 将为新会话创建一个新的作业对象。</span><span class="sxs-lookup"><span data-stu-id="8ac06-384">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="8ac06-385">断开 **PSSession** 的连接时，会话状态将断开连接，并且可用性为 None。</span><span class="sxs-lookup"><span data-stu-id="8ac06-385">When you disconnect a **PSSession**, the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="8ac06-386">**State** 属性的值是相对于当前会话的。</span><span class="sxs-lookup"><span data-stu-id="8ac06-386">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="8ac06-387">如果值为 "已断开连接"，则意味着 **PSSession** 未连接到当前会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-387">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="8ac06-388">但是，它并不意味着 **PSSession** 会与所有会话断开连接。</span><span class="sxs-lookup"><span data-stu-id="8ac06-388">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="8ac06-389">它可能连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-389">It might be connected to a different session.</span></span>
  <span data-ttu-id="8ac06-390">若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。</span><span class="sxs-lookup"><span data-stu-id="8ac06-390">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="8ac06-391">**Availability** 的 None 值指示可连接会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-391">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="8ac06-392">值为 "忙碌" 表示无法连接到 **PSSession** ，因为它已连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="8ac06-392">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="8ac06-393">有关会话 **状态** 属性的值的详细信息，请参阅 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-393">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>
- <span data-ttu-id="8ac06-394">有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-394">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="8ac06-395">相关链接</span><span class="sxs-lookup"><span data-stu-id="8ac06-395">RELATED LINKS</span></span>

[<span data-ttu-id="8ac06-396">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8ac06-396">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="8ac06-397">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8ac06-397">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="8ac06-398">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="8ac06-398">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="8ac06-399">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="8ac06-399">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="8ac06-400">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-400">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="8ac06-401">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-401">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="8ac06-402">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-402">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="8ac06-403">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-403">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="8ac06-404">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8ac06-404">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="8ac06-405">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-405">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="8ac06-406">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="8ac06-406">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="8ac06-407">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="8ac06-407">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="8ac06-408">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ac06-408">Remove-PSSession</span></span>](Remove-PSSession.md)
