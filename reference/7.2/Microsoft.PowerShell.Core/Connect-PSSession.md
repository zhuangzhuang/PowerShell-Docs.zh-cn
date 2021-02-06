---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: fda672ba4f6dafc9f955ef8025c386f7732d81bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596427"
---
# <span data-ttu-id="6e9c5-102">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-102">Connect-PSSession</span></span>

## <span data-ttu-id="6e9c5-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6e9c5-103">SYNOPSIS</span></span>
<span data-ttu-id="6e9c5-104">重新连接到已断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-104">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="6e9c5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6e9c5-105">SYNTAX</span></span>

### <span data-ttu-id="6e9c5-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="6e9c5-106">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-107">会话</span><span class="sxs-lookup"><span data-stu-id="6e9c5-107">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-108">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="6e9c5-108">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-109">计算机名</span><span class="sxs-lookup"><span data-stu-id="6e9c5-109">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-110">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="6e9c5-110">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6e9c5-111">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6e9c5-112">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e9c5-113">ID</span><span class="sxs-lookup"><span data-stu-id="6e9c5-113">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6e9c5-114">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6e9c5-114">DESCRIPTION</span></span>

<span data-ttu-id="6e9c5-115">此 `Connect-PSSession` Cmdlet 会重新连接到已断开连接 (**Pssession**) 的用户管理的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-115">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions (**PSSessions**) that were disconnected.</span></span> <span data-ttu-id="6e9c5-116">它适用于有意断开连接的会话（例如通过使用 cmdlet `Disconnect-PSSession` 或 cmdlet 的 **InDisconnectedSession** 参数） `Invoke-Command` 以及无意中断开连接的会话（如临时网络中断）。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-116">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="6e9c5-117">`Connect-PSSession` 可以连接到由同一用户启动的任何断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-117">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="6e9c5-118">其中包括通过其他计算机上的其他会话启动或断开连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-118">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="6e9c5-119">但是， `Connect-PSSession` 无法连接到已损坏或已关闭的会话，或使用 cmdlet 启动的交互式会话 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-119">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="6e9c5-120">此外，也无法将会话连接到由其他用户启动的会话，除非你能提供创建会话的用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-120">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="6e9c5-121">有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="6e9c5-122">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-122">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6e9c5-123">示例</span><span class="sxs-lookup"><span data-stu-id="6e9c5-123">EXAMPLES</span></span>

### <span data-ttu-id="6e9c5-124">示例1：重新连接到会话</span><span class="sxs-lookup"><span data-stu-id="6e9c5-124">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="6e9c5-125">此命令重新连接到 Server01 计算机上的 ITTask 会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-125">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="6e9c5-126">该输出显示此命令已成功。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-126">The output shows that the command was successful.</span></span> <span data-ttu-id="6e9c5-127">此时将打开会话的 **状态** ，并且 **可用性** 可用，这表示你可以在该会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-127">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="6e9c5-128">示例2：断开连接和重新连接的影响</span><span class="sxs-lookup"><span data-stu-id="6e9c5-128">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="6e9c5-129">此示例显示了断开某一会话的连接又重新连接到该会话的效果。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-129">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="6e9c5-130">第一个命令使用 `Get-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-130">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="6e9c5-131">在没有 **ComputerName** 参数的情况下，该命令仅获取已在当前会话中创建的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-131">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="6e9c5-132">该输出显示此命令可获取本地计算机上的 Backup 会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-132">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="6e9c5-133">会话 **状态** 已打开且 **可用性** 可用。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-133">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="6e9c5-134">第二个命令使用 `Get-PSSession` cmdlet 获取在当前会话中创建的 **PSSession** 对象，并使用 `Disconnect-PSSession` cmdlet 来断开会话连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-134">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="6e9c5-135">该输出显示 Backup 会话已断开连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-135">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="6e9c5-136">会话的 **状态** 为 "已断开连接" 且 **可用性** 为 "无"。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-136">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="6e9c5-137">第三个命令使用 `Get-PSSession` cmdlet 获取在当前会话中创建的 **PSSession** 对象，并使用 `Connect-PSSession` cmdlet 来重新连接会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-137">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="6e9c5-138">该输出显示 Backup 会话已重新连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-138">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="6e9c5-139">会话 **状态** 已打开且 **可用性** 可用。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-139">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="6e9c5-140">如果在 `Connect-PSSession` 未断开连接的会话上使用 cmdlet，则该命令不会影响会话，并且不会生成任何错误。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-140">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="6e9c5-141">示例3：企业方案中的一系列命令</span><span class="sxs-lookup"><span data-stu-id="6e9c5-141">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="6e9c5-142">这一系列命令显示了如何 `Connect-PSSession` 在企业方案中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-142">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="6e9c5-143">在此示例中，系统管理员将在远程计算机上的会话中启动长时间运行的作业。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-143">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="6e9c5-144">启动该作业后，管理员将断开与该会话的连接，然后下班回家。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-144">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="6e9c5-145">在晚上晚，管理员登录到她的家庭计算机，并验证作业是否已完成。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-145">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="6e9c5-146">管理员首先在远程计算机上创建会话，并在该会话中运行脚本。第一个命令使用 `New-PSSession` cmdlet 在 Server01 远程计算机上创建 ITTask 会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-146">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="6e9c5-147">该命令使用 **ConfigurationName** 参数来指定 ITTask 会话配置。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-147">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="6e9c5-148">该命令将会话保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-148">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="6e9c5-149">第二个命令 `Invoke-Command` cmdlet 用于在变量中的会话中启动后台作业 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-149">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="6e9c5-150">它使用 **FilePath** 参数在该后台作业中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-150">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="6e9c5-151">第三个命令使用 `Disconnect-PSSession` cmdlet 断开与变量中的会话的连接 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-151">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="6e9c5-152">该命令使用值为 Drop 的 **OutputBufferingMode** 参数，以防止通过将输出传递到会话来阻止脚本被阻止。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-152">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="6e9c5-153">它使用 **IdleTimeoutSec** 参数将会话超时时间延长至15小时。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-153">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="6e9c5-154">完成该命令后，管理员会锁定她的计算机并在家回家。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-154">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="6e9c5-155">此后，管理员将启动她的家庭计算机，登录到公司网络，并启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-155">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="6e9c5-156">第四个命令使用 `Get-PSSession` cmdlet 来获取 Server01 计算机上的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-156">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="6e9c5-157">命令查找 ITTask 会话。第五个命令使用 `Connect-PSSession` cmdlet 连接到 ITTask 会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-157">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="6e9c5-158">该命令将该会话保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-158">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="6e9c5-159">第六个命令使用 `Invoke-Command` cmdlet 在 `Get-Job` 变量中的会话中运行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-159">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="6e9c5-160">输出显示该作业已成功完成。第七个命令使用 cmdlet 在会话中的 `Invoke-Command` 变量的会话中运行 `Receive-Job` 命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-160">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="6e9c5-161">该命令将结果保存在 `$BackupSpecs` 变量中。第八个命令使用 `Invoke-Command` cmdlet 在会话中运行另一个脚本。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-161">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="6e9c5-162">该命令使用 `$BackupSpecs` 会话中变量的值作为脚本的输入。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-162">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="6e9c5-163">第九个命令从变量中的会话断开连接 `$s` 。管理员关闭 PowerShell 并关闭计算机。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-163">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="6e9c5-164">第二天，她可以通过自己的工作计算机重新连接到该会话，并检查该脚本状态。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-164">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="6e9c5-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e9c5-165">PARAMETERS</span></span>

### <span data-ttu-id="6e9c5-166">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="6e9c5-166">-AllowRedirection</span></span>

<span data-ttu-id="6e9c5-167">指示此 cmdlet 允许将此连接重定向到备用 URI。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-167">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="6e9c5-168">使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-168">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="6e9c5-169">默认情况下，PowerShell 不会重定向连接，但你可以使用此参数允许它重定向连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-169">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="6e9c5-170">你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-170">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="6e9c5-171">使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置 **$PSSessionOption** 首选项变量的 **MaximumConnectionRedirectionCount** 属性。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-171">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="6e9c5-172">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-172">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-173">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="6e9c5-173">-ApplicationName</span></span>

<span data-ttu-id="6e9c5-174">指定应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-174">Specifies the name of an application.</span></span> <span data-ttu-id="6e9c5-175">此 cmdlet 仅连接到使用指定应用程序的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-175">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="6e9c5-176">输入连接 URI 的应用程序名称段。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-176">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="6e9c5-177">例如，在以下连接 URI 中，应用程序名称为 WSMan：`http://localhost:5985/WSMAN`。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-177">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="6e9c5-178">会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-178">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="6e9c5-179">此参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-179">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6e9c5-180">它不会更改会话使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-180">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-181">-Authentication</span><span class="sxs-lookup"><span data-stu-id="6e9c5-181">-Authentication</span></span>

<span data-ttu-id="6e9c5-182">指定用于对命令中的用户凭据进行身份验证的机制，以便重新连接到断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-182">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="6e9c5-183">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="6e9c5-183">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6e9c5-184">默认</span><span class="sxs-lookup"><span data-stu-id="6e9c5-184">Default</span></span>
- <span data-ttu-id="6e9c5-185">基本</span><span class="sxs-lookup"><span data-stu-id="6e9c5-185">Basic</span></span>
- <span data-ttu-id="6e9c5-186">Credssp</span><span class="sxs-lookup"><span data-stu-id="6e9c5-186">Credssp</span></span>
- <span data-ttu-id="6e9c5-187">摘要</span><span class="sxs-lookup"><span data-stu-id="6e9c5-187">Digest</span></span>
- <span data-ttu-id="6e9c5-188">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6e9c5-188">Kerberos</span></span>
- <span data-ttu-id="6e9c5-189">Negotiate</span><span class="sxs-lookup"><span data-stu-id="6e9c5-189">Negotiate</span></span>
- <span data-ttu-id="6e9c5-190">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="6e9c5-190">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="6e9c5-191">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-191">The default value is Default.</span></span>

<span data-ttu-id="6e9c5-192">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-192">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="6e9c5-193">在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-193">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6e9c5-194">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-194">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6e9c5-195">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-195">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-196">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6e9c5-196">-CertificateThumbprint</span></span>

<span data-ttu-id="6e9c5-197">指定有权连接到断开连接的会话的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-197">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="6e9c5-198">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-198">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6e9c5-199">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-199">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6e9c5-200">它们只能映射到本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-200">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="6e9c5-201">它们不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-201">They do not work with domain accounts.</span></span>

<span data-ttu-id="6e9c5-202">若要获取证书指纹，请 `Get-Item` `Get-ChildItem` 在 PowerShell Cert：驱动器中使用或命令。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-202">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6e9c5-203">-ComputerName</span></span>

<span data-ttu-id="6e9c5-204">指定在其中存储断开连接的会话的计算机。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-204">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="6e9c5-205">会话存储在位于连接的服务器端或接收端的计算机上。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-205">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="6e9c5-206">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-206">The default is the local computer.</span></span>

<span data-ttu-id="6e9c5-207">键入计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-207">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="6e9c5-208">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-208">Wildcard characters are not permitted.</span></span> <span data-ttu-id="6e9c5-209">若要指定本地计算机，请键入计算机名称、localhost 或点 (。 ) </span><span class="sxs-lookup"><span data-stu-id="6e9c5-209">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-210">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6e9c5-210">-ConfigurationName</span></span>

<span data-ttu-id="6e9c5-211">只连接到使用指定会话配置的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-211">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="6e9c5-212">输入会话配置的配置名称或完全限定的资源 URI。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-212">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="6e9c5-213">如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-213">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="6e9c5-214">会话的配置名称存储在该会话的 **ConfigurationName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-214">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="6e9c5-215">此参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-215">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6e9c5-216">它不会更改会话使用的会话配置。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-216">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="6e9c5-217">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-217">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-218">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6e9c5-218">-ConnectionUri</span></span>

<span data-ttu-id="6e9c5-219">为断开连接的会话指定连接终结点的 Uri。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-219">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="6e9c5-220">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-220">The URI must be fully qualified.</span></span> <span data-ttu-id="6e9c5-221">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="6e9c5-221">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="6e9c5-222">默认值如下：</span><span class="sxs-lookup"><span data-stu-id="6e9c5-222">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="6e9c5-223">如果未指定连接 URI，则可以使用 **UseSSL** 和 **Port** 参数指定连接 uri 值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-223">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="6e9c5-224">URI 的 **Transport** 段的有效值为 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-224">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="6e9c5-225">如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-225">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="6e9c5-226">若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-226">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="6e9c5-227">如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-227">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-228">-Credential</span><span class="sxs-lookup"><span data-stu-id="6e9c5-228">-Credential</span></span>

<span data-ttu-id="6e9c5-229">指定有权连接到断开连接的会话的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-229">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="6e9c5-230">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-230">The default is the current user.</span></span>

<span data-ttu-id="6e9c5-231">键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 `PSCredential` 由 cmdlet 生成的对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-231">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6e9c5-232">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-232">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6e9c5-233">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-233">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6e9c5-234">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-234">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-235">-Id</span><span class="sxs-lookup"><span data-stu-id="6e9c5-235">-Id</span></span>

<span data-ttu-id="6e9c5-236">指定断开连接的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-236">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="6e9c5-237">仅当断开连接的会话之前已连接到当前会话时， **Id** 参数才有效。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-237">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="6e9c5-238">如果会话存储在本地计算机上，但未连接到当前会话，则此参数是有效的，但并未生效。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-238">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-239">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6e9c5-239">-InstanceId</span></span>

<span data-ttu-id="6e9c5-240">指定断开连接的会话的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-240">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="6e9c5-241">实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-241">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="6e9c5-242">实例 ID 存储在 **PSSession** 的 **InstanceID** 属性中。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-242">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-243">-Name</span><span class="sxs-lookup"><span data-stu-id="6e9c5-243">-Name</span></span>

<span data-ttu-id="6e9c5-244">指定断开连接的会话的友好名称。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-244">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-245">-Port</span><span class="sxs-lookup"><span data-stu-id="6e9c5-245">-Port</span></span>

<span data-ttu-id="6e9c5-246">指定远程计算机上用于重新连接到会话的网络端口。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-246">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="6e9c5-247">若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-247">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="6e9c5-248">默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-248">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="6e9c5-249">使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-249">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="6e9c5-250">若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：</span><span class="sxs-lookup"><span data-stu-id="6e9c5-250">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="6e9c5-251">除非必要，否则不要使用 **Port** 参数。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-251">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="6e9c5-252">在命令中设置的端口适用于运行该命令的所有计算机或会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-252">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="6e9c5-253">备用端口设置可能会阻止在所有计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-253">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-254">-Session</span><span class="sxs-lookup"><span data-stu-id="6e9c5-254">-Session</span></span>

<span data-ttu-id="6e9c5-255">指定断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-255">Specifies the disconnected sessions.</span></span> <span data-ttu-id="6e9c5-256">输入包含 **pssession** 对象的变量或创建或获取 **pssession** 对象的命令（如 `Get-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-256">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-257">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="6e9c5-257">-SessionOption</span></span>

<span data-ttu-id="6e9c5-258">为该会话指定高级选项。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-258">Specifies advanced options for the session.</span></span> <span data-ttu-id="6e9c5-259">输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-259">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="6e9c5-260">选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-260">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="6e9c5-261">否则，通过在会话配置中设置的选项创建默认值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-261">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="6e9c5-262">会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-262">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="6e9c5-263">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-263">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="6e9c5-264">有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-264">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="6e9c5-265">有关 **$PSSessionOption** 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-265">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="6e9c5-266">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-266">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-267">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6e9c5-267">-ThrottleLimit</span></span>

<span data-ttu-id="6e9c5-268">指定为运行此命令可建立的并发连接的最大数目。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-268">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="6e9c5-269">如果省略此参数或输入 0 值，则使用默认值 32。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-269">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="6e9c5-270">节流限制仅适用于当前命令，而不适用于会话或计算机。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-270">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-271">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6e9c5-271">-UseSSL</span></span>

<span data-ttu-id="6e9c5-272">指示此 cmdlet 使用安全套接字层 (SSL) 协议连接到断开连接的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-272">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="6e9c5-273">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-273">By default, SSL is not used.</span></span>

<span data-ttu-id="6e9c5-274">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-274">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="6e9c5-275">**UseSSL** 参数是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-275">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="6e9c5-276">如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-276">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e9c5-277">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6e9c5-277">-Confirm</span></span>

<span data-ttu-id="6e9c5-278">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-278">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6e9c5-279">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6e9c5-279">-WhatIf</span></span>

<span data-ttu-id="6e9c5-280">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-280">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6e9c5-281">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-281">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6e9c5-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e9c5-282">CommonParameters</span></span>

<span data-ttu-id="6e9c5-283">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e9c5-284">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e9c5-285">输入</span><span class="sxs-lookup"><span data-stu-id="6e9c5-285">INPUTS</span></span>

### <span data-ttu-id="6e9c5-286">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-286">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="6e9c5-287">可以通过管道将会话 (**PSSession**) 传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-287">You can pipe a session (**PSSession**) to this cmdlet.</span></span>

## <span data-ttu-id="6e9c5-288">输出</span><span class="sxs-lookup"><span data-stu-id="6e9c5-288">OUTPUTS</span></span>

### <span data-ttu-id="6e9c5-289">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-289">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="6e9c5-290">此 cmdlet 将返回一个对象，该对象表示其重新连接到的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-290">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="6e9c5-291">注释</span><span class="sxs-lookup"><span data-stu-id="6e9c5-291">NOTES</span></span>

- <span data-ttu-id="6e9c5-292">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-292">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="6e9c5-293">`Connect-PSSession` 仅重新连接到已断开连接的会话，即， **状态** 属性的值为 "已断开连接" 的会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-293">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="6e9c5-294">只有连接到或结束运行 Windows PowerShell 3.0 或更高版本的计算机的会话才能断开和重新连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-294">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="6e9c5-295">如果 `Connect-PSSession` 在未断开连接的会话上使用，则该命令不会影响会话，并且不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-295">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="6e9c5-296">与使用 **EnableNetworkAccess** 参数创建的交互式令牌断开连接的环回会话只能通过创建该会话的计算机重新连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-296">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="6e9c5-297">此限制可使计算机免遭恶意访问。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-297">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="6e9c5-298">**PSSession** 的 **State** 属性值相对于当前会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-298">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="6e9c5-299">因此，值 "已 **断开连接** " 意味着 **PSSession** 未连接到当前会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-299">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="6e9c5-300">但是，它并不意味着 **PSSession** 会与所有会话断开连接。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-300">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="6e9c5-301">它可能连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-301">It might be connected to a different session.</span></span> <span data-ttu-id="6e9c5-302">若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-302">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="6e9c5-303">**Availability** 的 None 值指示可连接会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-303">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="6e9c5-304">值为 "忙碌" 指示你无法连接到 **PSSession** ，因为它已连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-304">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="6e9c5-305">有关会话的 **State** 属性的值的详细信息，请参阅 [RunspaceState 枚举](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-305">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="6e9c5-306">有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate 枚举](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-306">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

- <span data-ttu-id="6e9c5-307">当你连接到 **pssession** 时，你无法更改 **PSSession** 的空闲超时值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-307">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="6e9c5-308">的 **SessionOption** 参数 `Connect-PSSession` 采用具有 **IdleTimeout** 值的 **SessionOption** 对象。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-308">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="6e9c5-309">但是，在   `$PSSessionOption` 连接到 **PSSession** 时，将忽略 SessionOption 对象的 idletimeout 值和该变量的 idletimeout 值。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-309">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="6e9c5-310">您可以在创建 **pssession** 时，通过使用 `New-PSSession` 或 `Invoke-Command` cmdlet 以及从 **Pssession** 断开连接来设置和更改 pssession 的空闲超时。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-310">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="6e9c5-311">**PSSession** 的 **IdleTimeout** 属性对断开连接的会话至关重要，因为它确定断开连接的会话在远程计算机上保留的时间。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-311">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="6e9c5-312">断开连接的会话从其断开连接的时刻起就被视为空闲，即使命令正在断开连接的会话中运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="6e9c5-312">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="6e9c5-313">相关链接</span><span class="sxs-lookup"><span data-stu-id="6e9c5-313">RELATED LINKS</span></span>

[<span data-ttu-id="6e9c5-314">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-314">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6e9c5-315">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-315">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="6e9c5-316">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-316">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="6e9c5-317">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-317">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="6e9c5-318">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6e9c5-318">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="6e9c5-319">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-319">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6e9c5-320">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="6e9c5-320">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="6e9c5-321">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="6e9c5-321">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="6e9c5-322">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-322">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6e9c5-323">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6e9c5-323">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6e9c5-324">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e9c5-324">Remove-PSSession</span></span>](Remove-PSSession.md)
