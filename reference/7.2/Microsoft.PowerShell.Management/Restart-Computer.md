---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 0e6df859a19f2281cc835b725fbc52c232042e56
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596021"
---
# <span data-ttu-id="acf00-102">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="acf00-102">Restart-Computer</span></span>

## <span data-ttu-id="acf00-103">摘要</span><span class="sxs-lookup"><span data-stu-id="acf00-103">SYNOPSIS</span></span>
<span data-ttu-id="acf00-104">重新启动本地和远程计算机上的操作系统。</span><span class="sxs-lookup"><span data-stu-id="acf00-104">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="acf00-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="acf00-105">SYNTAX</span></span>

### <span data-ttu-id="acf00-106">DefaultSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="acf00-106">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="acf00-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="acf00-107">DESCRIPTION</span></span>

<span data-ttu-id="acf00-108">`Restart-Computer`Cmdlet 将重新启动本地和远程计算机上的操作系统。</span><span class="sxs-lookup"><span data-stu-id="acf00-108">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="acf00-109">你可以使用的参数 `Restart-Computer` 来运行重新启动操作，指定身份验证级别和备用凭据，限制同时运行的操作，并强制立即重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-109">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="acf00-110">从 Windows PowerShell 3.0 开始，可以等待重新启动完成，然后再运行下一个命令。</span><span class="sxs-lookup"><span data-stu-id="acf00-110">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="acf00-111">指定等待超时和查询间隔，并等待特定服务在重新启动的计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="acf00-111">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="acf00-112">此功能使 `Restart-Computer` 在脚本和函数中使用成为现实。</span><span class="sxs-lookup"><span data-stu-id="acf00-112">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="acf00-113">示例</span><span class="sxs-lookup"><span data-stu-id="acf00-113">EXAMPLES</span></span>

### <span data-ttu-id="acf00-114">示例1：重新启动本地计算机</span><span class="sxs-lookup"><span data-stu-id="acf00-114">Example 1: Restart the local computer</span></span>

<span data-ttu-id="acf00-115">`Restart-Computer` 重新启动本地计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-115">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="acf00-116">示例2：重新启动多台计算机</span><span class="sxs-lookup"><span data-stu-id="acf00-116">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="acf00-117">`Restart-Computer` 可以重新启动远程和本地计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-117">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="acf00-118">**ComputerName** 参数接受计算机名称的数组。</span><span class="sxs-lookup"><span data-stu-id="acf00-118">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="acf00-119">示例3：从文本文件获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="acf00-119">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="acf00-120">`Restart-Computer` 从文本文件获取计算机名称的列表，并重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-120">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="acf00-121">未指定 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-121">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="acf00-122">但是，因为它是第一个位置参数，所以它接受从管道中发送的文本文件中的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="acf00-122">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="acf00-123">`Get-Content` 使用 **Path** 参数从文本文件获取计算机名称的列表， **Domain01.txt**。</span><span class="sxs-lookup"><span data-stu-id="acf00-123">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="acf00-124">计算机名称将沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="acf00-124">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="acf00-125">`Restart-Computer` 重新启动每台计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-125">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="acf00-126">示例4：强制重新启动文本文件中列出的计算机</span><span class="sxs-lookup"><span data-stu-id="acf00-126">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="acf00-127">此示例强制立即重新启动文件中列出的计算机 `Domain01.txt` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-127">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="acf00-128">文本文件中的计算机名称存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="acf00-128">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="acf00-129">**Force** 参数强制立即重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-129">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="acf00-130">`Get-Content` 使用 **Path** 参数从文本文件获取计算机名称的列表， **Domain01.txt**。</span><span class="sxs-lookup"><span data-stu-id="acf00-130">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="acf00-131">计算机名称存储在变量中 `$Names` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-131">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="acf00-132">`Get-Credential` 提示输入用户名和密码，并将值存储在变量中 `$Creds` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-132">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="acf00-133">`Restart-Computer` 将 **ComputerName** 和 **Credential** 参数与其变量一起使用。</span><span class="sxs-lookup"><span data-stu-id="acf00-133">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="acf00-134">**Force** 参数将导致立即重新启动每台计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-134">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="acf00-135">示例6：重新启动远程计算机并等待 PowerShell</span><span class="sxs-lookup"><span data-stu-id="acf00-135">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="acf00-136">`Restart-Computer` 重新启动远程计算机，然后最多等待5分钟 (300 秒) ，以便 PowerShell 在重新启动的计算机上变为可用状态，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="acf00-136">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="acf00-137">`Restart-Computer` 使用 **ComputerName** 参数指定 **Server01**。</span><span class="sxs-lookup"><span data-stu-id="acf00-137">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="acf00-138">**Wait** 参数等待重新启动完成。</span><span class="sxs-lookup"><span data-stu-id="acf00-138">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="acf00-139">的 **指定 PowerShell** 可以在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="acf00-139">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="acf00-140">**Timeout** 参数指定5分钟等待。</span><span class="sxs-lookup"><span data-stu-id="acf00-140">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="acf00-141">**Delay** 参数每两秒钟查询一次远程计算机，以确定它是否已重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-141">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="acf00-142">示例7：使用 WsmanAuthentication 重启计算机</span><span class="sxs-lookup"><span data-stu-id="acf00-142">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="acf00-143">`Restart-Computer` 使用 **WsmanAuthentication** 机制重新启动远程计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-143">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="acf00-144">Kerberos 身份验证确定当前用户是否有权重新启动远程计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-144">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="acf00-145">有关详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="acf00-145">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="acf00-146">`Restart-Computer` 使用 **ComputerName** 参数指定远程计算机 **Server01**。</span><span class="sxs-lookup"><span data-stu-id="acf00-146">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="acf00-147">**WsmanAuthentication** 参数将身份验证方法指定为 **Kerberos**。</span><span class="sxs-lookup"><span data-stu-id="acf00-147">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="acf00-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="acf00-148">PARAMETERS</span></span>

### <span data-ttu-id="acf00-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="acf00-149">-ComputerName</span></span>

<span data-ttu-id="acf00-150">指定一个计算机名称或以逗号分隔的计算机名称数组。</span><span class="sxs-lookup"><span data-stu-id="acf00-150">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="acf00-151">`Restart-Computer` 接受管道或变量中的 **ComputerName** 对象。</span><span class="sxs-lookup"><span data-stu-id="acf00-151">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="acf00-152">键入远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="acf00-152">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="acf00-153">若要指定本地计算机，请键入计算机名、点 `.` 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="acf00-153">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="acf00-154">此参数不依赖于 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="acf00-154">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="acf00-155">即使你的计算机未配置为运行远程命令，你也可以使用 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-155">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="acf00-156">如果未指定 **ComputerName** 参数，则 `Restart-Computer` 重新启动本地计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-156">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="acf00-157">-Credential</span></span>

<span data-ttu-id="acf00-158">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="acf00-158">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="acf00-159">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="acf00-159">The default is the current user.</span></span>

<span data-ttu-id="acf00-160">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-160">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="acf00-161">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="acf00-161">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="acf00-162">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="acf00-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="acf00-163">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="acf00-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-164">-Delay</span><span class="sxs-lookup"><span data-stu-id="acf00-164">-Delay</span></span>

<span data-ttu-id="acf00-165">指定查询的频率（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="acf00-165">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="acf00-166">PowerShell 查询由 **For** 参数指定的服务，以确定该服务是否在计算机重新启动之后可用。</span><span class="sxs-lookup"><span data-stu-id="acf00-166">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="acf00-167">此参数仅适用于 **Wait** **和参数** 。</span><span class="sxs-lookup"><span data-stu-id="acf00-167">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="acf00-168">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-168">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="acf00-169">如果未指定 **Delay** 参数， `Restart-Computer` 将使用5秒钟的延迟。</span><span class="sxs-lookup"><span data-stu-id="acf00-169">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-170">-对于</span><span class="sxs-lookup"><span data-stu-id="acf00-170">-For</span></span>

<span data-ttu-id="acf00-171">指定 PowerShell 的行为，因为它会等待指定的服务或功能在计算机重新启动后变得可用。</span><span class="sxs-lookup"><span data-stu-id="acf00-171">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="acf00-172">此参数仅对 **Wait** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="acf00-172">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="acf00-173">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="acf00-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="acf00-174">**默认**：等待 PowerShell 重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-174">**Default**: Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="acf00-175">**Powershell**：可在计算机上的 powershell 远程会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="acf00-175">**PowerShell**: Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="acf00-176">**WMI**：接收对计算机 Win32_ComputerSystem 查询的答复。</span><span class="sxs-lookup"><span data-stu-id="acf00-176">**WMI**: Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="acf00-177">**WinRM**：可以使用 ws-management 建立与计算机的远程会话。</span><span class="sxs-lookup"><span data-stu-id="acf00-177">**WinRM**: Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="acf00-178">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-179">-Force</span><span class="sxs-lookup"><span data-stu-id="acf00-179">-Force</span></span>

<span data-ttu-id="acf00-180">强制立即重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="acf00-180">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-181">-Timeout</span><span class="sxs-lookup"><span data-stu-id="acf00-181">-Timeout</span></span>

<span data-ttu-id="acf00-182">指定等待的持续时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="acf00-182">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="acf00-183">超时到期后，将 `Restart-Computer` 返回到命令提示符，即使计算机未重启也是如此。</span><span class="sxs-lookup"><span data-stu-id="acf00-183">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="acf00-184">**Timeout** 参数仅对 **Wait** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="acf00-184">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="acf00-185">**Timeout** 替代 **等待** 参数的无限等待期。</span><span class="sxs-lookup"><span data-stu-id="acf00-185">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="acf00-186">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-187">-Wait</span><span class="sxs-lookup"><span data-stu-id="acf00-187">-Wait</span></span>

<span data-ttu-id="acf00-188">`Restart-Computer` 取消 PowerShell 提示符并阻止管道，直到计算机重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-188">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="acf00-189">您可以在脚本中使用此参数来重新启动计算机，然后在重新启动完成后继续处理。</span><span class="sxs-lookup"><span data-stu-id="acf00-189">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="acf00-190">**等待** 参数会无限期地等待计算机重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-190">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="acf00-191">你可以使用 **超时** 调整计时，并使用和 **延迟\*\*\*\*参数，以** 等待特定服务在重新启动的计算机上变为可用。</span><span class="sxs-lookup"><span data-stu-id="acf00-191">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="acf00-192">当你重新启动本地计算机时， **等待** 参数无效。</span><span class="sxs-lookup"><span data-stu-id="acf00-192">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="acf00-193">如果 **ComputerName** 参数的值包含远程计算机和本地计算机的名称，则会 `Restart-Computer` 在本地计算机上生成 **等待等待** 的非终止错误，但会等待远程计算机重新启动。</span><span class="sxs-lookup"><span data-stu-id="acf00-193">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="acf00-194">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="acf00-195">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="acf00-195">-WsmanAuthentication</span></span>

<span data-ttu-id="acf00-196">指定用于对用户的凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="acf00-196">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="acf00-197">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="acf00-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="acf00-198">此参数可接受的值为： **Basic**、 **CredSSP**、 **Default**、 **Digest**、 **Kerberos** 和 **Negotiate**。</span><span class="sxs-lookup"><span data-stu-id="acf00-198">The acceptable values for this parameter are: **Basic**, **CredSSP**, **Default**, **Digest**, **Kerberos**, and **Negotiate**.</span></span>

<span data-ttu-id="acf00-199">有关详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="acf00-199">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="acf00-200">凭据安全服务提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="acf00-200">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="acf00-201">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="acf00-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="acf00-202">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="acf00-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acf00-203">-Confirm</span><span class="sxs-lookup"><span data-stu-id="acf00-203">-Confirm</span></span>

<span data-ttu-id="acf00-204">在运行之前提示你进行确认 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-204">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="acf00-205">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="acf00-205">-WhatIf</span></span>

<span data-ttu-id="acf00-206">显示运行时将发生的情况 `Restart-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="acf00-206">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="acf00-207">`Restart-Computer`Cmdlet 不会运行。</span><span class="sxs-lookup"><span data-stu-id="acf00-207">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="acf00-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="acf00-208">CommonParameters</span></span>

<span data-ttu-id="acf00-209">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="acf00-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="acf00-210">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="acf00-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="acf00-211">输入</span><span class="sxs-lookup"><span data-stu-id="acf00-211">INPUTS</span></span>

### <span data-ttu-id="acf00-212">System.String</span><span class="sxs-lookup"><span data-stu-id="acf00-212">System.String</span></span>

<span data-ttu-id="acf00-213">`Restart-Computer` 接受管道或变量中的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="acf00-213">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="acf00-214">输出</span><span class="sxs-lookup"><span data-stu-id="acf00-214">OUTPUTS</span></span>

### <span data-ttu-id="acf00-215">无</span><span class="sxs-lookup"><span data-stu-id="acf00-215">None</span></span>

<span data-ttu-id="acf00-216">`Restart-Computer` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="acf00-216">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="acf00-217">注释</span><span class="sxs-lookup"><span data-stu-id="acf00-217">NOTES</span></span>

- <span data-ttu-id="acf00-218">在 Windows 中， `Restart-Computer` 使用 Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem)类的[Win32Shutdown 方法](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem)。</span><span class="sxs-lookup"><span data-stu-id="acf00-218">In Windows, `Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="acf00-219">此方法需要为用于重新启动计算机的用户帐户启用 **SeShutdownPrivilege** 特权。</span><span class="sxs-lookup"><span data-stu-id="acf00-219">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>
- <span data-ttu-id="acf00-220">在 Linux 和 Mac OS 上， `Restart-Computer` 使用 `/sbin/shutdown` bash 工具。</span><span class="sxs-lookup"><span data-stu-id="acf00-220">On Linux and Mac OS, `Restart-Computer` uses the `/sbin/shutdown` bash tool.</span></span>

## <span data-ttu-id="acf00-221">相关链接</span><span class="sxs-lookup"><span data-stu-id="acf00-221">RELATED LINKS</span></span>

[<span data-ttu-id="acf00-222">关于 Windows 远程管理</span><span class="sxs-lookup"><span data-stu-id="acf00-222">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="acf00-223">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="acf00-223">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="acf00-224">WS-Management 协议</span><span class="sxs-lookup"><span data-stu-id="acf00-224">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
