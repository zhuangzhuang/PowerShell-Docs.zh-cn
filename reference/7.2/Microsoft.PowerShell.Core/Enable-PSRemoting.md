---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: a3d9506a0fd2adbb9cc093fb24f99e922dc8a938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595833"
---
# <span data-ttu-id="90597-102">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="90597-102">Enable-PSRemoting</span></span>

## <span data-ttu-id="90597-103">摘要</span><span class="sxs-lookup"><span data-stu-id="90597-103">SYNOPSIS</span></span>
<span data-ttu-id="90597-104">将计算机配置为接收远程命令。</span><span class="sxs-lookup"><span data-stu-id="90597-104">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="90597-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90597-105">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="90597-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="90597-106">DESCRIPTION</span></span>

<span data-ttu-id="90597-107">`Enable-PSRemoting`Cmdlet 将计算机配置为接收使用 WS-Management 技术发送的 PowerShell 远程命令。</span><span class="sxs-lookup"><span data-stu-id="90597-107">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="90597-108">目前仅在 Windows 平台上支持基于 WS-Management 的 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="90597-108">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="90597-109">默认情况下，在 Windows Server 平台上启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="90597-109">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="90597-110">可以使用 `Enable-PSRemoting` 在其他受支持的 Windows 版本上启用 PowerShell 远程处理，并在禁用远程处理后重新启用它。</span><span class="sxs-lookup"><span data-stu-id="90597-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="90597-111">只需在将接收命令的每台计算机上运行一次此命令。</span><span class="sxs-lookup"><span data-stu-id="90597-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="90597-112">不需要在仅发送命令的计算机上运行它。</span><span class="sxs-lookup"><span data-stu-id="90597-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="90597-113">由于配置启动侦听器来接受远程连接，因此，只需在需要的位置运行侦听器。</span><span class="sxs-lookup"><span data-stu-id="90597-113">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="90597-114">如果计算机位于公用网络上时，在客户端版本的 Windows 上启用 PowerShell 远程处理通常是不允许的，但你可以使用 **SkipNetworkProfileCheck** 参数跳过此限制。</span><span class="sxs-lookup"><span data-stu-id="90597-114">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="90597-115">有关详细信息，请参阅 **SkipNetworkProfileCheck** 参数的说明。</span><span class="sxs-lookup"><span data-stu-id="90597-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="90597-116">一台计算机上可以并行存在多个 PowerShell 安装。</span><span class="sxs-lookup"><span data-stu-id="90597-116">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="90597-117">运行 `Enable-PSRemoting` 将为运行 cmdlet 的特定安装版本配置远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="90597-117">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="90597-118">因此，如果在 `Enable-PSRemoting` 运行 powershell 6.2 时运行，则将配置运行 powershell 6.2 的远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="90597-118">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="90597-119">如果运行 `Enable-PSRemoting` powershell 7-preview 时运行，则将配置一个运行 powershell 7-preview 的远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="90597-119">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="90597-120">`Enable-PSRemoting` 根据需要创建两个远程处理终结点配置。</span><span class="sxs-lookup"><span data-stu-id="90597-120">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="90597-121">如果终结点配置已存在，则只需确保启用。</span><span class="sxs-lookup"><span data-stu-id="90597-121">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="90597-122">创建的配置是相同的，但具有不同的名称。</span><span class="sxs-lookup"><span data-stu-id="90597-122">The created configurations are identical but have different names.</span></span> <span data-ttu-id="90597-123">一个将具有与承载会话的 PowerShell 版本对应的简单名称。</span><span class="sxs-lookup"><span data-stu-id="90597-123">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="90597-124">其他配置名称包含有关托管会话的 PowerShell 版本的详细信息。</span><span class="sxs-lookup"><span data-stu-id="90597-124">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="90597-125">例如， `Enable-PSRemoting` 在 PowerShell 6.2 中运行时，将获取名为 **6.2.2** 的两个已配置的终结点。</span><span class="sxs-lookup"><span data-stu-id="90597-125">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6**, **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="90597-126">这允许你使用简单名称 **powershell. 6** 创建到最新 PowerShell 6 主机版本的连接。</span><span class="sxs-lookup"><span data-stu-id="90597-126">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="90597-127">或者，你可以使用更长的名称 **6.2.2** 连接到特定的 PowerShell 主机版本。</span><span class="sxs-lookup"><span data-stu-id="90597-127">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="90597-128">若要使用新启用的远程处理终结点，则在使用 `Invoke-Command` 、 `New-PSSession` 、cmdlet 创建远程连接时，必须使用 ConfigurationName 参数按名称指定它们 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="90597-128">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="90597-129">有关详细信息，请参阅示例4。</span><span class="sxs-lookup"><span data-stu-id="90597-129">For more information, see Example 4.</span></span>

<span data-ttu-id="90597-130">`Enable-PSRemoting`Cmdlet 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="90597-130">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="90597-131">运行 [set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet，该 cmdlet 将执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="90597-131">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="90597-132">启动 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="90597-132">Starts the WinRM service.</span></span>
  - <span data-ttu-id="90597-133">将 WinRM 服务上的启动类型设置为自动。</span><span class="sxs-lookup"><span data-stu-id="90597-133">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="90597-134">创建一个可接受任何 IP 地址上的请求的侦听器。</span><span class="sxs-lookup"><span data-stu-id="90597-134">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="90597-135">启用 WS-Management 通信的防火墙例外。</span><span class="sxs-lookup"><span data-stu-id="90597-135">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="90597-136">如果需要，创建简单名称会话终结点配置。</span><span class="sxs-lookup"><span data-stu-id="90597-136">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="90597-137">启用所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="90597-137">Enables all session configurations.</span></span>
  - <span data-ttu-id="90597-138">将所有会话配置的安全描述符更改为允许远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-138">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="90597-139">重新启动 WinRM 服务以使上述更改生效。</span><span class="sxs-lookup"><span data-stu-id="90597-139">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="90597-140">若要在 Windows 平台上运行此 cmdlet，请使用 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="90597-140">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="90597-141">此 cmdlet 不能在 Linux 或 MacOS 版本的 PowerShell 上使用。</span><span class="sxs-lookup"><span data-stu-id="90597-141">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="90597-142">此 cmdlet 不会影响 Windows PowerShell 创建的远程终结点配置。</span><span class="sxs-lookup"><span data-stu-id="90597-142">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="90597-143">它仅影响在 PowerShell 版本6和更高版本中创建的终结点。</span><span class="sxs-lookup"><span data-stu-id="90597-143">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="90597-144">若要启用和禁用 Windows PowerShell 承载的 PowerShell 远程处理终结点，请 `Enable-PSRemoting` 从 Windows powershell 会话中运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90597-144">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="90597-145">示例</span><span class="sxs-lookup"><span data-stu-id="90597-145">EXAMPLES</span></span>

### <span data-ttu-id="90597-146">示例1：将计算机配置为接收远程命令</span><span class="sxs-lookup"><span data-stu-id="90597-146">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="90597-147">此命令将计算机配置为接收远程命令。</span><span class="sxs-lookup"><span data-stu-id="90597-147">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="90597-148">示例2：将计算机配置为在没有确认提示的情况下接收远程命令</span><span class="sxs-lookup"><span data-stu-id="90597-148">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="90597-149">此命令将计算机配置为接收远程命令。</span><span class="sxs-lookup"><span data-stu-id="90597-149">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="90597-150">**Force** 参数取消用户提示。</span><span class="sxs-lookup"><span data-stu-id="90597-150">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="90597-151">示例3：允许在客户端上进行远程访问</span><span class="sxs-lookup"><span data-stu-id="90597-151">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="90597-152">此示例演示如何允许在客户端版本的 Windows 操作系统上从公共网络进行远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-152">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="90597-153">不同版本的 Windows 的防火墙规则名称可能不同。</span><span class="sxs-lookup"><span data-stu-id="90597-153">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="90597-154">使用 `Get-NetFirewallRule` 可查看规则列表。</span><span class="sxs-lookup"><span data-stu-id="90597-154">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="90597-155">启用防火墙规则之前，请查看规则中的安全设置，以验证配置是否适合您的环境。</span><span class="sxs-lookup"><span data-stu-id="90597-155">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="90597-156">默认情况下， `Enable-PSRemoting` 会创建允许从专用网络和域网络进行远程访问的网络规则。</span><span class="sxs-lookup"><span data-stu-id="90597-156">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="90597-157">该命令使用 **SkipNetworkProfileCheck** 参数来允许来自相同本地子网中的公用网络的远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-157">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="90597-158">命令指定 **Force** 参数以禁止显示确认消息。</span><span class="sxs-lookup"><span data-stu-id="90597-158">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="90597-159">**SkipNetworkProfileCheck** 参数不影响 Windows 操作系统的服务器版本，默认情况下，它允许从同一本地子网中的公共网络进行远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-159">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="90597-160">`Set-NetFirewallRule` **NetSecurity** 模块中的 cmdlet 添加一个防火墙规则，该规则允许从任何远程位置从公用网络进行远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-160">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="90597-161">这包括不同子网中的位置。</span><span class="sxs-lookup"><span data-stu-id="90597-161">This includes locations in different subnets.</span></span>

### <span data-ttu-id="90597-162">示例4：创建到新启用的终结点配置的远程会话</span><span class="sxs-lookup"><span data-stu-id="90597-162">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="90597-163">此示例演示如何在计算机上启用 PowerShell 远程处理，查找已配置的终结点名称，并创建到一个终结点的远程会话。</span><span class="sxs-lookup"><span data-stu-id="90597-163">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="90597-164">第一个命令在计算机上启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="90597-164">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="90597-165">第二个命令列出终结点配置。</span><span class="sxs-lookup"><span data-stu-id="90597-165">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="90597-166">第三个命令将创建与同一计算机的远程 PowerShell 会话，并按名称指定一个 **powershell。**</span><span class="sxs-lookup"><span data-stu-id="90597-166">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="90597-167">远程会话将托管 (6.2.2) 的最新 PowerShell 6 版本。</span><span class="sxs-lookup"><span data-stu-id="90597-167">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="90597-168">最后一个命令访问 `$PSVersionTable` 远程会话中的变量，以显示托管会话的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="90597-168">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="90597-169">防火墙规则的名称可能不同，具体取决于 Windows 的版本。</span><span class="sxs-lookup"><span data-stu-id="90597-169">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="90597-170">使用 `Get-NetFirewallRule` cmdlet 列出系统上规则的名称。</span><span class="sxs-lookup"><span data-stu-id="90597-170">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="90597-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90597-171">PARAMETERS</span></span>

### <span data-ttu-id="90597-172">-Confirm</span><span class="sxs-lookup"><span data-stu-id="90597-172">-Confirm</span></span>

<span data-ttu-id="90597-173">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="90597-173">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="90597-174">-Force</span><span class="sxs-lookup"><span data-stu-id="90597-174">-Force</span></span>

<span data-ttu-id="90597-175">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="90597-175">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="90597-176">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="90597-176">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="90597-177">指示当计算机位于公用网络上时，此 cmdlet 将在客户端版本的 Windows 操作系统上启用远程处理。</span><span class="sxs-lookup"><span data-stu-id="90597-177">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="90597-178">此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。</span><span class="sxs-lookup"><span data-stu-id="90597-178">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="90597-179">此参数不会影响 Windows 操作系统的服务器版本，默认情况下，它具有公用网络的本地子网防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="90597-179">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="90597-180">如果在服务器版本上禁用了本地子网防火墙规则， `Enable-PSRemoting` 则无论此参数的值是什么，都将其重新启用。</span><span class="sxs-lookup"><span data-stu-id="90597-180">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="90597-181">若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 **NetSecurity** 模块中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90597-181">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="90597-182">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="90597-182">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="90597-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="90597-183">-WhatIf</span></span>

<span data-ttu-id="90597-184">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="90597-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="90597-185">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="90597-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="90597-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90597-186">CommonParameters</span></span>

<span data-ttu-id="90597-187">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="90597-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90597-188">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="90597-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90597-189">输入</span><span class="sxs-lookup"><span data-stu-id="90597-189">INPUTS</span></span>

### <span data-ttu-id="90597-190">无</span><span class="sxs-lookup"><span data-stu-id="90597-190">None</span></span>

<span data-ttu-id="90597-191">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90597-191">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="90597-192">输出</span><span class="sxs-lookup"><span data-stu-id="90597-192">OUTPUTS</span></span>

### <span data-ttu-id="90597-193">System.String</span><span class="sxs-lookup"><span data-stu-id="90597-193">System.String</span></span>

<span data-ttu-id="90597-194">此 cmdlet 将返回描述其结果的字符串。</span><span class="sxs-lookup"><span data-stu-id="90597-194">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="90597-195">注释</span><span class="sxs-lookup"><span data-stu-id="90597-195">NOTES</span></span>

<span data-ttu-id="90597-196">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="90597-196">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="90597-197">在 Windows 操作系统的服务器版本上， `Enable-PSRemoting` 为允许远程访问的专用和域网络创建防火墙规则，并为公用网络创建防火墙规则，该规则仅允许来自同一本地子网中的计算机的远程访问。</span><span class="sxs-lookup"><span data-stu-id="90597-197">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="90597-198">在 Windows 操作系统的客户端版本上， `Enable-PSRemoting` 为允许无限制远程访问的私有和域网络创建防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="90597-198">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="90597-199">若要为公用网络创建防火墙规则，以允许来自相同本地子网的远程访问，请使用 **SkipNetworkProfileCheck** 参数。</span><span class="sxs-lookup"><span data-stu-id="90597-199">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="90597-200">在 Windows 操作系统的客户端或服务器版本上，若要为公用网络创建防火墙规则，以便删除本地子网限制并允许远程访问，请使用 `Set-NetFirewallRule` NetSecurity 模块中的 cmdlet 来运行以下命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="90597-200">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="90597-201">`Enable-PSRemoting` 通过将所有会话配置的 " **已启用** " 属性的值设置为来启用所有会话配置 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="90597-201">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="90597-202">`Enable-PSRemoting` 删除 **Deny_All** 和 **Network_Deny_All** 设置。</span><span class="sxs-lookup"><span data-stu-id="90597-202">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="90597-203">这可以远程访问保留供本地使用的会话配置。</span><span class="sxs-lookup"><span data-stu-id="90597-203">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="90597-204">相关链接</span><span class="sxs-lookup"><span data-stu-id="90597-204">RELATED LINKS</span></span>

[<span data-ttu-id="90597-205">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="90597-205">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="90597-206">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="90597-206">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="90597-207">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="90597-207">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="90597-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="90597-208">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="90597-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="90597-209">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="90597-210">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="90597-210">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="90597-211">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="90597-211">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="90597-212">about_Remote</span><span class="sxs-lookup"><span data-stu-id="90597-212">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="90597-213">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="90597-213">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
