---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 4b40d765002791f45f093c7912b8f9ba58248da9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603415"
---
# <span data-ttu-id="e1a69-102">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-102">New-PSSession</span></span>

## <span data-ttu-id="e1a69-103">摘要</span><span class="sxs-lookup"><span data-stu-id="e1a69-103">SYNOPSIS</span></span>
<span data-ttu-id="e1a69-104">创建与本地或远程计算机的持续性连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-104">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="e1a69-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1a69-105">SYNTAX</span></span>

### <span data-ttu-id="e1a69-106">ComputerName（默认值）</span><span class="sxs-lookup"><span data-stu-id="e1a69-106">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-107">Uri</span><span class="sxs-lookup"><span data-stu-id="e1a69-107">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-108">VMId</span><span class="sxs-lookup"><span data-stu-id="e1a69-108">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-109">VMName</span><span class="sxs-lookup"><span data-stu-id="e1a69-109">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-110">会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-110">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-111">ContainerId</span><span class="sxs-lookup"><span data-stu-id="e1a69-111">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-112">UseWindowsPowerShellParameterSet</span><span class="sxs-lookup"><span data-stu-id="e1a69-112">UseWindowsPowerShellParameterSet</span></span>

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-113">SSHHost</span><span class="sxs-lookup"><span data-stu-id="e1a69-113">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="e1a69-114">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="e1a69-114">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="e1a69-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1a69-115">DESCRIPTION</span></span>

<span data-ttu-id="e1a69-116">`New-PSSession`Cmdlet 在本地或远程计算机上 (**PSSession**) 创建 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-116">The `New-PSSession` cmdlet creates a PowerShell session (**PSSession**) on a local or remote computer.</span></span> <span data-ttu-id="e1a69-117">创建 **PSSession** 时，PowerShell 会建立与远程计算机的持久连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-117">When you create a **PSSession**, PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="e1a69-118">使用 **PSSession** 运行共享数据的多个命令，例如函数或变量的值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-118">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="e1a69-119">若要在 **PSSession** 中运行命令，请使用 `Invoke-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1a69-119">To run commands in a **PSSession**, use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e1a69-120">若要使用 **PSSession** 直接与远程计算机交互，请使用 `Enter-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1a69-120">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="e1a69-121">有关详细信息，请参阅 [about_PSSessions](about/about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-121">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="e1a69-122">您可以在远程计算机上运行命令，而无需使用或的 **ComputerName** 参数创建 `Enter-PSSession` PSSession `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-122">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="e1a69-123">使用 **ComputerName** 参数时，PowerShell 会创建一个临时连接，该连接用于命令，然后关闭。</span><span class="sxs-lookup"><span data-stu-id="e1a69-123">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="e1a69-124">从 PowerShell 6.0 开始，可以使用安全外壳 (SSH) 建立与远程计算机的连接，并在远程计算机上创建会话，如果本地计算机上有 SSH 并且远程计算机配置了 PowerShell SSH 终结点。</span><span class="sxs-lookup"><span data-stu-id="e1a69-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="e1a69-125">基于 SSH 的 PowerShell 远程会话的优点在于，它可以跨多个平台运行 (Windows、Linux、macOS) 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-125">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="e1a69-126">对于基于 SSH 的会话，请使用 **HostName** 或 **SSHConnection** 参数集来指定远程计算机和相关的连接信息。</span><span class="sxs-lookup"><span data-stu-id="e1a69-126">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="e1a69-127">有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="e1a69-128">如果使用的是来自 Linux 或 macOS 客户端的 WSMan 远程处理，并且该终结点的服务器证书不受信任 (例如，自签名证书) 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-128">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="e1a69-129">必须提供 `PSSessionOption` 包含和的， `-SkipCACheck` `-SkipCNCheck` 才能成功建立连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-129">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="e1a69-130">仅当你在可以确定服务器证书和目标系统的网络连接的环境中时，才执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e1a69-130">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="e1a69-131">示例</span><span class="sxs-lookup"><span data-stu-id="e1a69-131">EXAMPLES</span></span>

### <span data-ttu-id="e1a69-132">示例1：在本地计算机上创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-132">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="e1a69-133">此命令在本地计算机上创建新的 **pssession** ，并将 **PSSession** 保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-133">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="e1a69-134">你现在可以使用此 **PSSession** 在本地计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-134">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="e1a69-135">示例2：在远程计算机上创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-135">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="e1a69-136">此命令在 Server01 计算机上创建新的 **PSSession** ，并将其保存在 `$Server01` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-136">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="e1a69-137">创建多个 **PSSession** 对象时，将它们分配给具有有用名称的变量。</span><span class="sxs-lookup"><span data-stu-id="e1a69-137">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="e1a69-138">这将帮助你在后续命令中管理 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="e1a69-138">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="e1a69-139">示例3：在多台计算机上创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-139">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="e1a69-140">此命令在 **ComputerName** 参数指定的每台计算机上创建三个 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="e1a69-140">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="e1a69-141">该命令使用赋值运算符 (=) 将新的 **PSSession** 对象分配给变量： `$s1` 、 `$s2` 、 `$s3` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-141">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="e1a69-142">它将 Server01 **pssession** 分配给 `$s1` ，将 Server02 **pssession** 分配给 `$s2` ，并将 Server03 **pssession** 分配给 `$s3` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-142">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="e1a69-143">将多个对象分配给一系列变量时，PowerShell 会将每个对象分别分配到序列中的变量。</span><span class="sxs-lookup"><span data-stu-id="e1a69-143">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="e1a69-144">如果对象多于变量，则所有剩余对象都将分配给最后一个变量。</span><span class="sxs-lookup"><span data-stu-id="e1a69-144">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="e1a69-145">如果变量多于对象，则剩余变量为空 (null)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-145">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="e1a69-146">示例4：使用指定的端口创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-146">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="e1a69-147">此命令在 Server01 计算机上创建一个新的 **PSSession** ，该计算机连接到服务器端口8081并使用 SSL 协议。</span><span class="sxs-lookup"><span data-stu-id="e1a69-147">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="e1a69-148">新的 **PSSession** 使用名为 E12 的备用会话配置。</span><span class="sxs-lookup"><span data-stu-id="e1a69-148">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="e1a69-149">在设置端口前，你必须将远程计算机上的 WinRM 侦听器配置为侦听端口 8081。</span><span class="sxs-lookup"><span data-stu-id="e1a69-149">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="e1a69-150">有关详细信息，请参阅 **Port** 参数的描述。</span><span class="sxs-lookup"><span data-stu-id="e1a69-150">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="e1a69-151">示例5：基于现有会话创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-151">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="e1a69-152">此命令创建与现有 **pssession** 具有相同属性的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-152">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="e1a69-153">如果现有 **pssession** 的资源耗尽，需要新的 **pssession** 来分担某些需求，则可以使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="e1a69-153">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="e1a69-154">该命令使用的 **Session** 参数 `New-PSSession` 来指定保存在变量中的 PSSession `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-154">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="e1a69-155">它使用 Domain1\Admin01 用户的凭据来完成命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-155">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="e1a69-156">示例6：在不同的域中创建具有全局作用域的会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-156">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="e1a69-157">此示例演示如何在不同域中的计算机上创建具有全局作用域的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-157">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="e1a69-158">默认情况下，在命令行创建的 **pssession** 对象是使用本地范围创建的，并且在脚本中创建的 **pssession** 对象具有脚本作用域。</span><span class="sxs-lookup"><span data-stu-id="e1a69-158">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="e1a69-159">若要创建具有全局作用域的 **pssession** ，请创建一个新的 **pssession** ，然后将该 **pssession** 存储在强制转换为全局作用域的变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-159">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="e1a69-160">在这种情况下， `$s` 变量将强制转换为全局范围。</span><span class="sxs-lookup"><span data-stu-id="e1a69-160">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="e1a69-161">该命令使用 **ComputerName** 参数指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-161">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="e1a69-162">由于计算机与用户帐户在不同的域中，因此会将计算机的全名与用户的凭据一起指定。</span><span class="sxs-lookup"><span data-stu-id="e1a69-162">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="e1a69-163">示例7：创建多台计算机的会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-163">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="e1a69-164">此命令在 Servers.txt 文件中列出的每台200计算机上创建 **PSSession** ，并将生成的 **pssession** 存储在 `$rs` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-164">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="e1a69-165">**PSSession** 对象的中止值限制为50。</span><span class="sxs-lookup"><span data-stu-id="e1a69-165">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="e1a69-166">当计算机名称存储在数据库、电子表格、文件文件中或以其他可转换为文本的格式存储时，可以使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="e1a69-166">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="e1a69-167">示例8：使用 URI 创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-167">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="e1a69-168">此命令在 Server01 计算机上创建 **PSSession** ，并将其存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-168">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="e1a69-169">它使用 **URI** 参数指定传输协议、远程计算机、端口和备用会话配置。</span><span class="sxs-lookup"><span data-stu-id="e1a69-169">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="e1a69-170">它还使用 **Credential** 参数指定有权在远程计算机上创建会话的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1a69-170">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="e1a69-171">示例9：在一组会话中运行后台作业</span><span class="sxs-lookup"><span data-stu-id="e1a69-171">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="e1a69-172">这些命令创建一组 **pssession** 对象，然后在每个 **PSSession** 对象中运行一个后台作业。</span><span class="sxs-lookup"><span data-stu-id="e1a69-172">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="e1a69-173">第一个命令在 Servers.txt 文件中列出的每台计算机上创建一个新的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-173">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="e1a69-174">它使用 `New-PSSession` cmdlet 创建 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="e1a69-174">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="e1a69-175">**ComputerName** 参数的值是一个命令，该命令使用 `Get-Content` cmdlet 来获取 Servers.txt 文件的计算机名称的列表。</span><span class="sxs-lookup"><span data-stu-id="e1a69-175">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="e1a69-176">该命令使用 **Credential** 参数创建具有域管理员权限的 **PSSession** 对象，并使用 **ThrottleLimit** 参数将该命令限制为16个并发连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-176">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="e1a69-177">该命令将 **PSSession** 对象保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-177">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="e1a69-178">第二个命令使用 cmdlet 的 **AsJob** 参数 `Invoke-Command` 启动一个后台作业，该作业在 `Get-Process PowerShell` 中的每个 **PSSession** 对象中运行一个命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-178">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="e1a69-179">有关 PowerShell 后台作业的详细信息，请参阅 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-179">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="e1a69-180">示例10：使用其 URI 为计算机创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-180">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="e1a69-181">此命令创建连接到由 URI （而不是计算机名称）指定的计算机的 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="e1a69-181">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="e1a69-182">示例11：创建会话选项</span><span class="sxs-lookup"><span data-stu-id="e1a69-182">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="e1a69-183">此示例演示如何创建 session 选项对象并使用 **SessionOption** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-183">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="e1a69-184">第一个命令使用 `New-PSSessionOption` cmdlet 来创建会话选项。</span><span class="sxs-lookup"><span data-stu-id="e1a69-184">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="e1a69-185">它将生成的 **SessionOption** 对象保存在 `$so` 变量中。</span><span class="sxs-lookup"><span data-stu-id="e1a69-185">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="e1a69-186">第二个命令在新会话中使用该选项。</span><span class="sxs-lookup"><span data-stu-id="e1a69-186">The second command uses the option in a new session.</span></span> <span data-ttu-id="e1a69-187">该命令使用 `New-PSSession` cmdlet 创建新的会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-187">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="e1a69-188">SessionOption 参数的值是变量中的 **SessionOption** 对象 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-188">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="e1a69-189">示例12：使用 SSH 创建会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-189">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="e1a69-190">此示例演示如何使用安全外壳 (SSH) 创建新的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-190">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="e1a69-191">如果在远程计算机上配置了 SSH 以提示输入密码，则会出现密码提示。</span><span class="sxs-lookup"><span data-stu-id="e1a69-191">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="e1a69-192">否则，你将需要使用基于 SSH 密钥的用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="e1a69-192">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="e1a69-193">示例13：使用 SSH 创建会话并指定端口和用户身份验证密钥</span><span class="sxs-lookup"><span data-stu-id="e1a69-193">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="e1a69-194">此示例演示如何使用安全外壳 (SSH) 创建 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-194">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="e1a69-195">它使用 **port** 参数指定要使用的端口，并使用 **KeyFilePath** 参数来指定用于在远程计算机上标识和验证用户身份的 RSA 密钥。</span><span class="sxs-lookup"><span data-stu-id="e1a69-195">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="e1a69-196">示例14：使用 SSH 创建多个会话</span><span class="sxs-lookup"><span data-stu-id="e1a69-196">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="e1a69-197">此示例演示如何使用安全外壳 (SSH) 和 **SSHConnection** 参数集创建多个会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-197">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="e1a69-198">**SSHConnection** 参数采用包含每个会话的连接信息的哈希表数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-198">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="e1a69-199">请注意，此示例要求目标远程计算机已配置 SSH 以支持基于密钥的用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="e1a69-199">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="e1a69-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1a69-200">PARAMETERS</span></span>

### <span data-ttu-id="e1a69-201">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="e1a69-201">-AllowRedirection</span></span>

<span data-ttu-id="e1a69-202">指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。</span><span class="sxs-lookup"><span data-stu-id="e1a69-202">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="e1a69-203">使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a69-203">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="e1a69-204">默认情况下，PowerShell 不会重定向连接，但你可以使用此参数使其重定向连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-204">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="e1a69-205">你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-205">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="e1a69-206">使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置 **$PSSessionOption** 首选项变量的 **MaximumConnectionRedirectionCount** 属性。</span><span class="sxs-lookup"><span data-stu-id="e1a69-206">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="e1a69-207">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="e1a69-207">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-208">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="e1a69-208">-ApplicationName</span></span>

<span data-ttu-id="e1a69-209">指定连接 URI 的应用程序名称段。</span><span class="sxs-lookup"><span data-stu-id="e1a69-209">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="e1a69-210">当命令中未使用 **ConnectionURI** 参数时，请使用此参数指定应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="e1a69-210">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="e1a69-211">默认值为 `$PSSessionApplicationName` 本地计算机上首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-211">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="e1a69-212">如果未定义此首选项变量，则默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="e1a69-212">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="e1a69-213">该值适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="e1a69-213">This value is appropriate for most uses.</span></span> <span data-ttu-id="e1a69-214">有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-214">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="e1a69-215">WinRM 服务使用应用程序名称来选择为连接请求提供服务的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e1a69-215">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="e1a69-216">此参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值匹配。</span><span class="sxs-lookup"><span data-stu-id="e1a69-216">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-217">-Authentication</span><span class="sxs-lookup"><span data-stu-id="e1a69-217">-Authentication</span></span>

<span data-ttu-id="e1a69-218">指定用于对用户的凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="e1a69-218">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="e1a69-219">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="e1a69-219">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e1a69-220">默认</span><span class="sxs-lookup"><span data-stu-id="e1a69-220">Default</span></span>
- <span data-ttu-id="e1a69-221">基本</span><span class="sxs-lookup"><span data-stu-id="e1a69-221">Basic</span></span>
- <span data-ttu-id="e1a69-222">Credssp</span><span class="sxs-lookup"><span data-stu-id="e1a69-222">Credssp</span></span>
- <span data-ttu-id="e1a69-223">摘要</span><span class="sxs-lookup"><span data-stu-id="e1a69-223">Digest</span></span>
- <span data-ttu-id="e1a69-224">Kerberos</span><span class="sxs-lookup"><span data-stu-id="e1a69-224">Kerberos</span></span>
- <span data-ttu-id="e1a69-225">Negotiate</span><span class="sxs-lookup"><span data-stu-id="e1a69-225">Negotiate</span></span>
- <span data-ttu-id="e1a69-226">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="e1a69-226">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="e1a69-227">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="e1a69-227">The default value is Default.</span></span>

<span data-ttu-id="e1a69-228">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-228">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="e1a69-229">凭据安全支持提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-229">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="e1a69-230">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="e1a69-230">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="e1a69-231">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-231">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-232">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e1a69-232">-CertificateThumbprint</span></span>

<span data-ttu-id="e1a69-233">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-233">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="e1a69-234">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="e1a69-234">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e1a69-235">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="e1a69-235">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="e1a69-236">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="e1a69-236">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="e1a69-237">若要获取证书，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-237">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-238">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e1a69-238">-ComputerName</span></span>

<span data-ttu-id="e1a69-239">指定计算机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-239">Specifies an array of names of computers.</span></span> <span data-ttu-id="e1a69-240">此 cmdlet 创建 (**PSSession**) 到指定计算机的持续性连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-240">This cmdlet creates a persistent connection (**PSSession**) to the specified computer.</span></span> <span data-ttu-id="e1a69-241">如果输入多个计算机名称，则会 `New-PSSession` 创建多个 **PSSession** 对象，每台计算机一个。</span><span class="sxs-lookup"><span data-stu-id="e1a69-241">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="e1a69-242">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-242">The default is the local computer.</span></span>

<span data-ttu-id="e1a69-243">键入一台或多台远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="e1a69-243">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="e1a69-244">若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-244">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="e1a69-245">当计算机与用户处于不同的域中时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="e1a69-245">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="e1a69-246">还可以通过管道将计算机名称传递给 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-246">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="e1a69-247">若要在 **ComputerName** 参数的值中使用 IP 地址，该命令必须包括 **Credential** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-247">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="e1a69-248">此外，必须为计算机配置 HTTPS 传输，或者必须在本地计算机上的 WinRM TrustedHosts 列表中包含远程计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e1a69-248">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="e1a69-249">有关将计算机名称添加到 TrustedHosts 列表的说明，请参阅 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)中的 "如何将计算机添加到受信任的主机列表中"。</span><span class="sxs-lookup"><span data-stu-id="e1a69-249">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="e1a69-250">若要在 **ComputerName** 参数的值中包含本地计算机，请使用 "以管理员身份运行" 选项启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e1a69-250">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-251">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e1a69-251">-ConfigurationName</span></span>

<span data-ttu-id="e1a69-252">指定用于新的 **PSSession** 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="e1a69-252">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="e1a69-253">输入会话配置的配置名称或完全限定的资源 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a69-253">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="e1a69-254">如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-254">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="e1a69-255">会话的会话配置位于远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="e1a69-255">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="e1a69-256">如果远程计算机上不存在指定的会话配置，则该命令会失败。</span><span class="sxs-lookup"><span data-stu-id="e1a69-256">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="e1a69-257">默认值为 `$PSSessionConfigurationName` 本地计算机上首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-257">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="e1a69-258">如果未设置此首选项变量，则默认值为 Microsoft.PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e1a69-258">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="e1a69-259">有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-259">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-260">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="e1a69-260">-ConnectionUri</span></span>

<span data-ttu-id="e1a69-261">指定一个 URI，该 URI 定义会话的连接终结点。</span><span class="sxs-lookup"><span data-stu-id="e1a69-261">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="e1a69-262">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="e1a69-262">The URI must be fully qualified.</span></span> <span data-ttu-id="e1a69-263">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="e1a69-263">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="e1a69-264">默认值如下：</span><span class="sxs-lookup"><span data-stu-id="e1a69-264">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="e1a69-265">如果未指定 **ConnectionURI**，则可以使用 **UseSSL**、**ComputerName**、**Port** 和 **ApplicationName** 参数来指定 **ConnectionURI** 值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-265">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="e1a69-266">URI 的 Transport 段的有效值为 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="e1a69-266">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="e1a69-267">如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="e1a69-267">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="e1a69-268">若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。</span><span class="sxs-lookup"><span data-stu-id="e1a69-268">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="e1a69-269">如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-269">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-270">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="e1a69-270">-ContainerId</span></span>

<span data-ttu-id="e1a69-271">指定容器的 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-271">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="e1a69-272">此 cmdlet 将启动与每个指定容器的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-272">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="e1a69-273">使用 `docker ps` 命令获取容器 id 列表。</span><span class="sxs-lookup"><span data-stu-id="e1a69-273">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="e1a69-274">有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="e1a69-274">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-275">-Credential</span><span class="sxs-lookup"><span data-stu-id="e1a69-275">-Credential</span></span>

<span data-ttu-id="e1a69-276">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1a69-276">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="e1a69-277">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="e1a69-277">The default is the current user.</span></span>

<span data-ttu-id="e1a69-278">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-278">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e1a69-279">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="e1a69-279">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="e1a69-280">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-280">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="e1a69-281">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-281">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-282">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="e1a69-282">-EnableNetworkAccess</span></span>

<span data-ttu-id="e1a69-283">指示此 cmdlet 将交互式安全令牌添加到环回会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-283">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="e1a69-284">通过交互式令牌，你可以在环回会话中运行用于获取其他计算机中的数据的命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-284">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="e1a69-285">例如，你可以在该会话中运行用于将 XML 文件从远程计算机复制到本地计算机的命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-285">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="e1a69-286">环回会话是在同一计算机上开始并终止的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="e1a69-286">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="e1a69-287">若要创建环回会话，请省略 **ComputerName** 参数，或将其值设置为 (. ) 、localhost 或本地计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e1a69-287">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="e1a69-288">默认情况下，此 cmdlet 使用网络令牌创建环回会话，该令牌可能不提供足够的权限来向远程计算机进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="e1a69-288">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="e1a69-289">**EnableNetworkAccess** 参数仅在环回会话中有效。</span><span class="sxs-lookup"><span data-stu-id="e1a69-289">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="e1a69-290">如果在远程计算机上创建会话时使用 **EnableNetworkAccess** ，则该命令将成功，但会忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-290">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="e1a69-291">你还可以通过使用 **Authentication** 参数的 CredSSP 值，在环回会话中启用远程访问，该参数将会话凭据委派给其他计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-291">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="e1a69-292">若要保护计算机免受恶意访问，已断开连接的具有交互式令牌（使用 **EnableNetworkAccess** 参数创建的令牌）的环回会话只能通过创建该会话的计算机重新连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-292">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="e1a69-293">断开连接的使用 CredSSP 身份验证的会话可通过其他计算机重新连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-293">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="e1a69-294">有关详细信息，请参阅 `Disconnect-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="e1a69-294">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="e1a69-295">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-295">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-296">-HostName</span><span class="sxs-lookup"><span data-stu-id="e1a69-296">-HostName</span></span>

<span data-ttu-id="e1a69-297">指定安全外壳 (基于 SSH) 连接的计算机名称的数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-297">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="e1a69-298">这与 ComputerName 参数类似，不同之处在于使用 SSH 而不是 Windows WinRM 建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-298">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="e1a69-299">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-299">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-300">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="e1a69-300">-KeyFilePath</span></span>

<span data-ttu-id="e1a69-301">指定安全外壳 (SSH) 用于对远程计算机上的用户进行身份验证的密钥文件路径。</span><span class="sxs-lookup"><span data-stu-id="e1a69-301">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="e1a69-302">SSH 允许通过私有/公共密钥执行用户身份验证，作为基本密码身份验证的替代方法。</span><span class="sxs-lookup"><span data-stu-id="e1a69-302">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="e1a69-303">如果将远程计算机配置为进行密钥身份验证，则可以使用此参数来提供用于标识用户的密钥。</span><span class="sxs-lookup"><span data-stu-id="e1a69-303">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="e1a69-304">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-304">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-305">-Name</span><span class="sxs-lookup"><span data-stu-id="e1a69-305">-Name</span></span>

<span data-ttu-id="e1a69-306">指定 **PSSession** 的友好名称。</span><span class="sxs-lookup"><span data-stu-id="e1a69-306">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="e1a69-307">使用其他 cmdlet （如和）时，可以使用名称来引用 **PSSession** `Get-PSSession` `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-307">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="e1a69-308">对于计算机或当前会话，该名称无需是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-308">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-309">-Port</span><span class="sxs-lookup"><span data-stu-id="e1a69-309">-Port</span></span>

<span data-ttu-id="e1a69-310">指定远程计算机上用于此连接的网络端口。</span><span class="sxs-lookup"><span data-stu-id="e1a69-310">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="e1a69-311">若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-311">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="e1a69-312">默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。</span><span class="sxs-lookup"><span data-stu-id="e1a69-312">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="e1a69-313">使用其他端口之前，必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="e1a69-313">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="e1a69-314">使用以下命令配置侦听器：</span><span class="sxs-lookup"><span data-stu-id="e1a69-314">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="e1a69-315">除非必要，否则不要使用 **Port** 参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-315">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="e1a69-316">命令中的端口设置适用于运行该命令的所有计算机或会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-316">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="e1a69-317">备用端口设置可能会阻止在所有计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-317">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-318">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="e1a69-318">-RunAsAdministrator</span></span>

<span data-ttu-id="e1a69-319">指示 **PSSession** 以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="e1a69-319">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-320">-Session</span><span class="sxs-lookup"><span data-stu-id="e1a69-320">-Session</span></span>

<span data-ttu-id="e1a69-321">指定一个 **PSSession** 对象数组，此 cmdlet 将其用作新 **PSSession** 的模型。</span><span class="sxs-lookup"><span data-stu-id="e1a69-321">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="e1a69-322">此参数创建与指定的 **pssession** 对象具有相同属性的新 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="e1a69-322">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="e1a69-323">输入包含 **pssession** 对象的变量或创建或获取 **pssession** 对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="e1a69-323">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="e1a69-324">生成的 **PSSession** 对象具有相同的计算机名称、应用程序名称、连接 URI、端口、配置名称、中止值和安全套接字层 (SSL) 值作为原始对象，但它们具有不同的显示名称、id 和实例 ID (GUID) 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-324">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-325">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="e1a69-325">-SessionOption</span></span>

<span data-ttu-id="e1a69-326">为该会话指定高级选项。</span><span class="sxs-lookup"><span data-stu-id="e1a69-326">Specifies advanced options for the session.</span></span> <span data-ttu-id="e1a69-327">输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-327">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="e1a69-328">选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。</span><span class="sxs-lookup"><span data-stu-id="e1a69-328">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="e1a69-329">否则，通过在会话配置中设置的选项创建默认值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-329">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="e1a69-330">会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="e1a69-330">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="e1a69-331">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="e1a69-331">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="e1a69-332">有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-332">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="e1a69-333">有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-333">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="e1a69-334">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-334">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-335">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="e1a69-335">-SSHConnection</span></span>

<span data-ttu-id="e1a69-336">此参数采用哈希表数组，其中每个哈希表都包含一个或多个建立安全外壳 (SSH) 连接 (HostName、Port、UserName、KeyFilePath) 所需的连接参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-336">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="e1a69-337">哈希表连接参数与为 **主机名** 参数集定义的参数相同。</span><span class="sxs-lookup"><span data-stu-id="e1a69-337">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="e1a69-338">**SSHConnection** 参数适用于创建多个会话，其中每个会话需要不同的连接信息。</span><span class="sxs-lookup"><span data-stu-id="e1a69-338">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="e1a69-339">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-340">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="e1a69-340">-SSHTransport</span></span>

<span data-ttu-id="e1a69-341">指示使用安全外壳 (SSH) 建立远程连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-341">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="e1a69-342">默认情况下，PowerShell 使用 Windows WinRM 连接到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-342">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="e1a69-343">此开关强制 PowerShell 使用 HostName 参数集建立基于 SSH 的远程连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-343">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="e1a69-344">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-344">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-345">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e1a69-345">-ThrottleLimit</span></span>

<span data-ttu-id="e1a69-346">指定为运行此命令可建立的并发连接的最大数目。</span><span class="sxs-lookup"><span data-stu-id="e1a69-346">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="e1a69-347">如果省略此参数或输入 0（零）值，则使用默认值 32。</span><span class="sxs-lookup"><span data-stu-id="e1a69-347">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="e1a69-348">节流限制仅适用于当前命令，而不适用于会话或计算机。</span><span class="sxs-lookup"><span data-stu-id="e1a69-348">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-349">-UserName</span><span class="sxs-lookup"><span data-stu-id="e1a69-349">-UserName</span></span>

<span data-ttu-id="e1a69-350">指定用于在远程计算机上创建会话的帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="e1a69-350">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="e1a69-351">用户身份验证方法取决于如何在远程计算机上配置 (SSH) 安全外壳。</span><span class="sxs-lookup"><span data-stu-id="e1a69-351">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="e1a69-352">如果 SSH 配置了基本密码身份验证，则系统将提示你输入用户密码。</span><span class="sxs-lookup"><span data-stu-id="e1a69-352">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="e1a69-353">如果 SSH 配置为基于密钥的用户身份验证，则可以通过 KeyFilePath 参数提供密钥文件路径，并且不会出现密码提示。</span><span class="sxs-lookup"><span data-stu-id="e1a69-353">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="e1a69-354">请注意，如果客户端用户密钥文件位于 SSH 已知位置，则基于密钥的身份验证不需要 KeyFilePath 参数，并且将根据用户名自动进行用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="e1a69-354">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="e1a69-355">有关详细信息，请参阅 SSH 文档关于基于密钥的用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="e1a69-355">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="e1a69-356">这不是必需的参数。</span><span class="sxs-lookup"><span data-stu-id="e1a69-356">This is not a required parameter.</span></span> <span data-ttu-id="e1a69-357">如果未指定用户名参数，则将使用当前登录的用户名作为连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-357">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="e1a69-358">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e1a69-358">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-359">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="e1a69-359">-UseSSL</span></span>

<span data-ttu-id="e1a69-360">指示此 cmdlet 使用 SSL 协议建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="e1a69-360">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="e1a69-361">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="e1a69-361">By default, SSL is not used.</span></span>

<span data-ttu-id="e1a69-362">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="e1a69-362">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="e1a69-363">**UseSSL** 参数提供额外的保护，可通过 HTTPS 连接而不是 HTTP 连接来发送数据。</span><span class="sxs-lookup"><span data-stu-id="e1a69-363">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="e1a69-364">如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="e1a69-364">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-365">-VMId</span><span class="sxs-lookup"><span data-stu-id="e1a69-365">-VMId</span></span>

<span data-ttu-id="e1a69-366">指定虚拟机的 ID 的数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-366">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="e1a69-367">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-367">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="e1a69-368">若要查看可供你使用的虚拟机，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1a69-368">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-369">-VMName</span><span class="sxs-lookup"><span data-stu-id="e1a69-369">-VMName</span></span>

<span data-ttu-id="e1a69-370">指定一个虚拟机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="e1a69-370">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="e1a69-371">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="e1a69-371">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="e1a69-372">若要查看可供你使用的虚拟机，请使用 `Get-VM` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1a69-372">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-373">-子系统</span><span class="sxs-lookup"><span data-stu-id="e1a69-373">-Subsystem</span></span>

<span data-ttu-id="e1a69-374">指定用于新的 **PSSession** 的 SSH 子系统。</span><span class="sxs-lookup"><span data-stu-id="e1a69-374">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="e1a69-375">此项指定要在目标上使用的子系统（如 sshd_config 中所定义）。</span><span class="sxs-lookup"><span data-stu-id="e1a69-375">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="e1a69-376">子系统使用预定义参数启动特定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e1a69-376">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="e1a69-377">如果远程计算机上不存在指定的子系统，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="e1a69-377">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="e1a69-378">如果未使用此参数，则默认值为 "powershell" 子系统。</span><span class="sxs-lookup"><span data-stu-id="e1a69-378">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-379">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="e1a69-379">-UseWindowsPowerShell</span></span>

<span data-ttu-id="e1a69-380">{{填充 UseWindowsPowerShell 说明}}</span><span class="sxs-lookup"><span data-stu-id="e1a69-380">{{ Fill UseWindowsPowerShell Description }}</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1a69-381">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1a69-381">CommonParameters</span></span>

<span data-ttu-id="e1a69-382">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1a69-382">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1a69-383">有关详细信息，请参阅 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216) 。</span><span class="sxs-lookup"><span data-stu-id="e1a69-383">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1a69-384">输入</span><span class="sxs-lookup"><span data-stu-id="e1a69-384">INPUTS</span></span>

### <span data-ttu-id="e1a69-385">System.object、System.string、System.web. （.）</span><span class="sxs-lookup"><span data-stu-id="e1a69-385">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e1a69-386">可以通过管道将 string、URI 或 session 对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1a69-386">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="e1a69-387">输出</span><span class="sxs-lookup"><span data-stu-id="e1a69-387">OUTPUTS</span></span>

### <span data-ttu-id="e1a69-388">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-388">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="e1a69-389">注释</span><span class="sxs-lookup"><span data-stu-id="e1a69-389">NOTES</span></span>

- <span data-ttu-id="e1a69-390">此 cmdlet 使用 PowerShell 远程处理基础结构。</span><span class="sxs-lookup"><span data-stu-id="e1a69-390">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="e1a69-391">若要使用此 cmdlet，必须为本地计算机和任何远程计算机配置 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="e1a69-391">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="e1a69-392">有关详细信息，请参阅 [about_Remote_Requirements](About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-392">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="e1a69-393">若要在本地计算机上创建 **PSSession** ，请使用 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e1a69-393">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="e1a69-394">使用完 **pssession** 后，请使用 `Remove-PSSession` cmdlet 删除 **pssession** ，并释放其资源。</span><span class="sxs-lookup"><span data-stu-id="e1a69-394">When you are finished with the **PSSession**, use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="e1a69-395">从 PowerShell 6.0 开始， **主机名** 和 **SSHConnection** 参数集已包括在内。</span><span class="sxs-lookup"><span data-stu-id="e1a69-395">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="e1a69-396">添加它们是为了提供基于 (SSH) 安全外壳的 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="e1a69-396">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="e1a69-397">SSH 和 PowerShell 在多个平台上都受支持 (Windows、Linux、macOS) ，PowerShell 远程处理将在安装和配置 PowerShell 和 SSH 的这些平台上运行。</span><span class="sxs-lookup"><span data-stu-id="e1a69-397">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="e1a69-398">这不同于以前仅限 Windows 的基于 WinRM 的远程处理，并且很多 WinRM 特定功能和限制不适用。</span><span class="sxs-lookup"><span data-stu-id="e1a69-398">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="e1a69-399">例如，目前不支持基于 WinRM 的配额、会话选项、自定义终结点配置和断开/重新连接功能。</span><span class="sxs-lookup"><span data-stu-id="e1a69-399">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="e1a69-400">有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。</span><span class="sxs-lookup"><span data-stu-id="e1a69-400">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="e1a69-401">相关链接</span><span class="sxs-lookup"><span data-stu-id="e1a69-401">RELATED LINKS</span></span>

[<span data-ttu-id="e1a69-402">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-402">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="e1a69-403">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-403">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="e1a69-404">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-404">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e1a69-405">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-405">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="e1a69-406">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-406">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e1a69-407">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e1a69-407">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e1a69-408">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-408">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="e1a69-409">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1a69-409">Remove-PSSession</span></span>](Remove-PSSession.md)

