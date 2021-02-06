---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 4410c8f41fffcaae9c9f447af246f335033d53a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597045"
---
# <span data-ttu-id="53221-102">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="53221-102">Disable-PSRemoting</span></span>

## <span data-ttu-id="53221-103">摘要</span><span class="sxs-lookup"><span data-stu-id="53221-103">SYNOPSIS</span></span>
<span data-ttu-id="53221-104">阻止 PowerShell 终结点接收远程连接。</span><span class="sxs-lookup"><span data-stu-id="53221-104">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="53221-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53221-105">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="53221-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="53221-106">DESCRIPTION</span></span>

<span data-ttu-id="53221-107">该 `Disable-PSRemoting` cmdlet 会阻止远程访问本地计算机上所有 PowerShell 版本6和更高版本的会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-107">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="53221-108">它不会影响 Windows PowerShell 终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-108">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="53221-109">若要禁用 Windows PowerShell 会话终结点配置，请 `Disable-PSRemoting` 在 Windows powershell 会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="53221-109">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="53221-110">若要重新启用对所有 PowerShell 版本6和更高版本的会话终结点配置的远程访问，请使用 `Enable-PSRemoting` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53221-110">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="53221-111">若要重新启用对所有 Windows PowerShell 会话终结点配置的远程访问，请 `Enable-PSRemoting` 从 Windows powershell 会话中运行。</span><span class="sxs-lookup"><span data-stu-id="53221-111">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="53221-112">如果要禁用对本地 Windows 计算机的所有 PowerShell 远程访问，必须在 PowerShell 版本6或更高版本的会话中以及从 Windows PowerShell 会话中运行此命令。</span><span class="sxs-lookup"><span data-stu-id="53221-112">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="53221-113">默认情况下，所有 Windows 计算机上都安装了 windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53221-113">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="53221-114">若要禁用和重新启用对特定会话终结点配置的远程访问，请使用 `Enable-PSSessionConfiguration` 和 `Disable-PSSessionConfiguration` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53221-114">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="53221-115">若要设置单个终结点的特定访问配置，请将 `Set-PSSessionConfiguration` cmdlet 与 **AccessMode** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="53221-115">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="53221-116">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="53221-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="53221-117">即使在运行后 `Disable-PSRemoting` ，仍可在本地计算机上进行环回连接。</span><span class="sxs-lookup"><span data-stu-id="53221-117">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="53221-118">环回连接是源自并连接到同一台本地计算机的 PowerShell 远程会话。</span><span class="sxs-lookup"><span data-stu-id="53221-118">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="53221-119">来自外部源的远程会话将保持阻止。</span><span class="sxs-lookup"><span data-stu-id="53221-119">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="53221-120">对于环回连接，必须使用 **EnableNetworkAccess** 参数的隐式凭据。</span><span class="sxs-lookup"><span data-stu-id="53221-120">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="53221-121">有关环回连接的详细信息，请参阅 [新的 PSSession](New-PSSession.md)。</span><span class="sxs-lookup"><span data-stu-id="53221-121">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="53221-122">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="53221-122">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="53221-123">它在 Linux 或 macOS 版本的 PowerShell 中不可用。</span><span class="sxs-lookup"><span data-stu-id="53221-123">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="53221-124">若要运行此 cmdlet，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53221-124">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="53221-125">示例</span><span class="sxs-lookup"><span data-stu-id="53221-125">EXAMPLES</span></span>

### <span data-ttu-id="53221-126">示例1：阻止远程访问所有 PowerShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="53221-126">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="53221-127">此示例阻止远程访问计算机上的所有 PowerShell 会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-127">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="53221-128">示例2：在没有确认提示的情况下禁止远程访问所有 PowerShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="53221-128">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="53221-129">此示例阻止远程访问计算机上的所有 PowerShell 会话终结点配置，而不会提示。</span><span class="sxs-lookup"><span data-stu-id="53221-129">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="53221-130">示例3：运行此 cmdlet 的效果</span><span class="sxs-lookup"><span data-stu-id="53221-130">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="53221-131">此示例演示如何使用 `Disable-PSRemoting` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53221-131">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="53221-132">若要运行此命令序列，请用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53221-132">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="53221-133">禁用会话配置后，该 `New-PSSession` cmdlet 会尝试创建到本地计算机的远程会话 (也称为 "环回" ) 。</span><span class="sxs-lookup"><span data-stu-id="53221-133">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="53221-134">由于在本地计算机上禁用远程访问，因此该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="53221-134">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="53221-135">示例4：运行此 cmdlet 和 Enable-PSRemoting 的效果</span><span class="sxs-lookup"><span data-stu-id="53221-135">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="53221-136">此示例演示了使用和 cmdlet 对会话配置的影响 `Disable-PSRemoting` `Enable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="53221-136">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="53221-137">`Disable-PSRemoting` 用于禁止远程访问所有 PowerShell 会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-137">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="53221-138">**Force** 参数取消了所有用户提示。</span><span class="sxs-lookup"><span data-stu-id="53221-138">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="53221-139">`Get-PSSessionConfiguration`和 `Format-Table` cmdlet 显示计算机上的会话配置。</span><span class="sxs-lookup"><span data-stu-id="53221-139">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="53221-140">此输出显示，具有网络令牌的所有远程用户均被拒绝访问终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-140">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="53221-141">允许本地计算机上的管理员组访问终结点配置，只要它们本地连接 (也称为环回) 并使用隐式凭据。</span><span class="sxs-lookup"><span data-stu-id="53221-141">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="53221-142">`Enable-PSRemoting`Cmdlet 可重新启用对计算机上所有 PowerShell 会话终结点配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="53221-142">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="53221-143">**Force** 参数取消所有用户提示，并在不提示的情况下重新启动 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="53221-143">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="53221-144">新的输出显示已从所有会话配置中删除 **AccessDenied** 安全描述符。</span><span class="sxs-lookup"><span data-stu-id="53221-144">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="53221-145">示例5：具有已禁用会话终结点配置的环回连接</span><span class="sxs-lookup"><span data-stu-id="53221-145">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="53221-146">此示例演示如何禁用终结点配置，并演示如何成功连接到已禁用的终结点。</span><span class="sxs-lookup"><span data-stu-id="53221-146">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="53221-147">`Disable-PSRemoting` 禁用所有 PowerShell 会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-147">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="53221-148">第一次使用 `New-PSSession` 尝试创建到本地计算机的远程会话。</span><span class="sxs-lookup"><span data-stu-id="53221-148">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="53221-149">**ConfigurationName** 参数用于指定已禁用的 PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="53221-149">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="53221-150">凭据通过 **Credential** 参数显式传递给命令。</span><span class="sxs-lookup"><span data-stu-id="53221-150">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="53221-151">这种类型的连接会通过网络堆栈，并且不是环回。</span><span class="sxs-lookup"><span data-stu-id="53221-151">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="53221-152">因此，尝试连接到已禁用的终结点失败，并出现 " **拒绝访问** " 错误。</span><span class="sxs-lookup"><span data-stu-id="53221-152">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="53221-153">第二次使用时， `New-PSSession` 也会尝试创建到本地计算机的远程会话。</span><span class="sxs-lookup"><span data-stu-id="53221-153">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="53221-154">在这种情况下，它会成功，因为它是绕过网络堆栈的环回连接。</span><span class="sxs-lookup"><span data-stu-id="53221-154">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="53221-155">当满足以下条件时，将创建环回连接：</span><span class="sxs-lookup"><span data-stu-id="53221-155">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="53221-156">要连接到的计算机名称为 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="53221-156">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="53221-157">未传入凭据。</span><span class="sxs-lookup"><span data-stu-id="53221-157">No credentials are passed in.</span></span> <span data-ttu-id="53221-158">当前登录的用户 (用于连接的隐式凭据) 。</span><span class="sxs-lookup"><span data-stu-id="53221-158">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="53221-159">使用 **EnableNetworkAccess** 开关参数。</span><span class="sxs-lookup"><span data-stu-id="53221-159">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="53221-160">有关环回连接的详细信息，请参阅 [新的 PSSession](New-PSSession.md) 文档。</span><span class="sxs-lookup"><span data-stu-id="53221-160">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="53221-161">示例6：禁用所有 PowerShell 远程处理终结点配置</span><span class="sxs-lookup"><span data-stu-id="53221-161">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="53221-162">此示例演示如何运行 `Disable-PSRemoting` 命令不会影响 Windows PowerShell 终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-162">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="53221-163">`Get-PSSessionConfiguration` 在 Windows PowerShell 中运行显示所有终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-163">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="53221-164">我们发现 Windows PowerShell 终结点配置未禁用。</span><span class="sxs-lookup"><span data-stu-id="53221-164">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="53221-165">若要禁用这些终结点配置， `Disable-PSRemoting` 必须从 Windows PowerShell 会话中运行该命令。</span><span class="sxs-lookup"><span data-stu-id="53221-165">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="53221-166">现在，在 `Get-PSSessionConfiguration` Windows PowerShell 中运行会显示禁用所有终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-166">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="53221-167">示例7：阻止远程访问具有自定义安全描述符的会话配置</span><span class="sxs-lookup"><span data-stu-id="53221-167">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="53221-168">此示例演示 `Disable-PSRemoting` cmdlet 禁用对所有会话配置的远程访问，包括具有自定义安全描述符的会话配置。</span><span class="sxs-lookup"><span data-stu-id="53221-168">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="53221-169">`Register-PSSessionConfiguration` 创建 **测试** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="53221-169">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="53221-170">**FilePath** 参数指定自定义会话的会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="53221-170">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="53221-171">**ShowSecurityDescriptorUI** 参数显示为会话配置设置权限的对话框。</span><span class="sxs-lookup"><span data-stu-id="53221-171">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="53221-172">在 "权限" 对话框中，为指定的用户创建自定义的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="53221-172">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="53221-173">`Get-PSSessionConfiguration`和 `Format-Table` cmdlet 显示会话配置及其属性。</span><span class="sxs-lookup"><span data-stu-id="53221-173">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="53221-174">此输出显示 **测试** 会话配置允许所指示的用户的交互式访问和特殊权限。</span><span class="sxs-lookup"><span data-stu-id="53221-174">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="53221-175">`Disable-PSRemoting` 禁用对所有会话配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="53221-175">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="53221-176">现在 `Get-PSSessionConfiguration` ，和 `Format-Table` cmdlet 显示将所有网络用户的 **AccessDenied** 安全描述符添加到所有会话配置，包括 **测试** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="53221-176">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="53221-177">尽管其他安全描述符不会更改，但 "network_deny_all" 安全描述符优先。</span><span class="sxs-lookup"><span data-stu-id="53221-177">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="53221-178">尝试使用 `New-PSSession` 连接到 **测试** 会话配置时，将对此进行说明。</span><span class="sxs-lookup"><span data-stu-id="53221-178">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="53221-179">示例8：重新启用对选定会话配置的远程访问</span><span class="sxs-lookup"><span data-stu-id="53221-179">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="53221-180">此示例演示如何重新启用仅到选定会话配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="53221-180">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="53221-181">禁用所有会话配置后，将重新启用特定会话。</span><span class="sxs-lookup"><span data-stu-id="53221-181">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="53221-182">`Set-PSSessionConfiguration`Cmdlet 用于更改 **PowerShell. 6** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="53221-182">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="53221-183">如果 **AccessMode** 参数的值为 **remote** ，则启用对配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="53221-183">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="53221-184">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53221-184">PARAMETERS</span></span>

### <span data-ttu-id="53221-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="53221-185">-Confirm</span></span>

<span data-ttu-id="53221-186">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="53221-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="53221-187">-Force</span><span class="sxs-lookup"><span data-stu-id="53221-187">-Force</span></span>

<span data-ttu-id="53221-188">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="53221-188">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53221-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="53221-189">-WhatIf</span></span>

<span data-ttu-id="53221-190">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="53221-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="53221-191">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="53221-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="53221-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53221-192">CommonParameters</span></span>

<span data-ttu-id="53221-193">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="53221-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53221-194">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="53221-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53221-195">输入</span><span class="sxs-lookup"><span data-stu-id="53221-195">INPUTS</span></span>

### <span data-ttu-id="53221-196">无</span><span class="sxs-lookup"><span data-stu-id="53221-196">None</span></span>

<span data-ttu-id="53221-197">不能通过管道将任何对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53221-197">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="53221-198">输出</span><span class="sxs-lookup"><span data-stu-id="53221-198">OUTPUTS</span></span>

### <span data-ttu-id="53221-199">无</span><span class="sxs-lookup"><span data-stu-id="53221-199">None</span></span>

<span data-ttu-id="53221-200">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="53221-200">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="53221-201">注释</span><span class="sxs-lookup"><span data-stu-id="53221-201">NOTES</span></span>

<span data-ttu-id="53221-202">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="53221-202">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="53221-203">禁用会话配置不会撤消由或 cmdlet 进行的所有更改 `Enable-PSRemoting` `Enable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="53221-203">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="53221-204">你可能需要手动撤消以下更改。</span><span class="sxs-lookup"><span data-stu-id="53221-204">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="53221-205">停止并禁用 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="53221-205">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="53221-206">删除接受任何 IP 地址上的请求的侦听器。</span><span class="sxs-lookup"><span data-stu-id="53221-206">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="53221-207">禁用 WS-Management 通信的防火墙例外。</span><span class="sxs-lookup"><span data-stu-id="53221-207">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="53221-208">将 LocalAccountTokenFilterPolicy 的值还原为 0，这将限制对计算机上 Administrators 组成员的远程访问。</span><span class="sxs-lookup"><span data-stu-id="53221-208">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="53221-209">会话终结点配置是一组定义会话环境的设置。</span><span class="sxs-lookup"><span data-stu-id="53221-209">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="53221-210">连接到计算机的每个会话必须使用在计算机上注册的某个会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="53221-210">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="53221-211">通过拒绝对所有会话终结点配置的远程访问，你可以有效地阻止远程用户建立连接到计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="53221-211">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="53221-212">相关链接</span><span class="sxs-lookup"><span data-stu-id="53221-212">RELATED LINKS</span></span>

[<span data-ttu-id="53221-213">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53221-213">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="53221-214">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="53221-214">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="53221-215">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53221-215">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="53221-216">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="53221-216">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="53221-217">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53221-217">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="53221-218">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53221-218">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="53221-219">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="53221-219">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="53221-220">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="53221-220">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
