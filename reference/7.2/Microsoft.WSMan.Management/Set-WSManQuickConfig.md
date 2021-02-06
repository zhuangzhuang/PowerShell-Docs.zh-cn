---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596615"
---
# <span data-ttu-id="b03b4-102">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b03b4-102">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="b03b4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b03b4-103">SYNOPSIS</span></span>
<span data-ttu-id="b03b4-104">配置本地计算机以进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="b03b4-104">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="b03b4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b03b4-105">SYNTAX</span></span>

### <span data-ttu-id="b03b4-106">全部</span><span class="sxs-lookup"><span data-stu-id="b03b4-106">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="b03b4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b03b4-107">DESCRIPTION</span></span>

<span data-ttu-id="b03b4-108">`Set-WSManQuickConfig`Cmdlet 将计算机配置为接收使用 Web Services For management (ws-management) 技术发送的 PowerShell 远程命令。</span><span class="sxs-lookup"><span data-stu-id="b03b4-108">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="b03b4-109">`Set-WSManQuickConfig` 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b03b4-109">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="b03b4-110">检查 WinRM 服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="b03b4-110">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="b03b4-111">如果 WinRM 服务未运行，则启动该服务。</span><span class="sxs-lookup"><span data-stu-id="b03b4-111">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="b03b4-112">将 WinRM 服务启动类型设置为自动。</span><span class="sxs-lookup"><span data-stu-id="b03b4-112">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="b03b4-113">创建一个可接受任何 IP 地址上的请求的侦听器。</span><span class="sxs-lookup"><span data-stu-id="b03b4-113">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="b03b4-114">默认传输为 **HTTP**。</span><span class="sxs-lookup"><span data-stu-id="b03b4-114">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="b03b4-115">为 WinRM 通信启用防火墙例外。</span><span class="sxs-lookup"><span data-stu-id="b03b4-115">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="b03b4-116">若要运行 `Set-WSManQuickConfig` ，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b03b4-116">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="b03b4-117">示例</span><span class="sxs-lookup"><span data-stu-id="b03b4-117">EXAMPLES</span></span>

### <span data-ttu-id="b03b4-118">示例 1：通过 HTTP 启用本地计算机的远程管理</span><span class="sxs-lookup"><span data-stu-id="b03b4-118">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="b03b4-119">此示例设置所需的配置以启用本地计算机的远程管理。</span><span class="sxs-lookup"><span data-stu-id="b03b4-119">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="b03b4-120">默认情况下，此命令会在 **HTTP** 上创建 WS-Management 侦听器。</span><span class="sxs-lookup"><span data-stu-id="b03b4-120">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="b03b4-121">示例 2：通过 HTTPS 启用本地计算机的远程管理</span><span class="sxs-lookup"><span data-stu-id="b03b4-121">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="b03b4-122">此示例设置所需的配置以启用本地计算机的远程管理。</span><span class="sxs-lookup"><span data-stu-id="b03b4-122">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="b03b4-123">**UseSSL** 参数指定使用 **HTTPS** 与计算机通信。</span><span class="sxs-lookup"><span data-stu-id="b03b4-123">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="b03b4-124">**HTTPS** 需要手动配置。</span><span class="sxs-lookup"><span data-stu-id="b03b4-124">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="b03b4-125">有关详细信息，请参阅 **UseSSL** 参数的说明。</span><span class="sxs-lookup"><span data-stu-id="b03b4-125">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="b03b4-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b03b4-126">PARAMETERS</span></span>

### <span data-ttu-id="b03b4-127">-Force</span><span class="sxs-lookup"><span data-stu-id="b03b4-127">-Force</span></span>

<span data-ttu-id="b03b4-128">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="b03b4-128">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b03b4-129">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="b03b4-129">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="b03b4-130">当计算机位于公用网络上时，为远程处理配置 Windows 客户端版本。</span><span class="sxs-lookup"><span data-stu-id="b03b4-130">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="b03b4-131">此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。</span><span class="sxs-lookup"><span data-stu-id="b03b4-131">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="b03b4-132">此参数对 Windows 的服务器版本不起作用，默认情况下，该参数具有公用网络的本地子网防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="b03b4-132">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="b03b4-133">如果在 Windows 的服务器版本上禁用了本地子网防火墙规则， `Enable-PSRemoting` 则无论此参数的值是什么，都将其重新启用。</span><span class="sxs-lookup"><span data-stu-id="b03b4-133">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="b03b4-134">若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 **NetSecurity** 模块中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b03b4-134">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="b03b4-135">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="b03b4-135">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b03b4-136">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b03b4-136">-UseSSL</span></span>

<span data-ttu-id="b03b4-137">指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="b03b4-137">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="b03b4-138">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b03b4-138">By default, SSL isn't used.</span></span>

<span data-ttu-id="b03b4-139">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="b03b4-139">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="b03b4-140">**UseSSL** 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="b03b4-140">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="b03b4-141">如果使用此参数，并且 SSL 在用于连接的端口上不可用，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="b03b4-141">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="b03b4-142">**HTTPS** 需要手动配置 WinRM 和防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="b03b4-142">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="b03b4-143">有关详细信息，请参阅 [如何：配置 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)。</span><span class="sxs-lookup"><span data-stu-id="b03b4-143">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b03b4-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b03b4-144">CommonParameters</span></span>

<span data-ttu-id="b03b4-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b03b4-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b03b4-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b03b4-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b03b4-147">输入</span><span class="sxs-lookup"><span data-stu-id="b03b4-147">INPUTS</span></span>

### <span data-ttu-id="b03b4-148">无</span><span class="sxs-lookup"><span data-stu-id="b03b4-148">None</span></span>

<span data-ttu-id="b03b4-149">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="b03b4-149">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="b03b4-150">输出</span><span class="sxs-lookup"><span data-stu-id="b03b4-150">OUTPUTS</span></span>

### <span data-ttu-id="b03b4-151">无</span><span class="sxs-lookup"><span data-stu-id="b03b4-151">None</span></span>

<span data-ttu-id="b03b4-152">此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="b03b4-152">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="b03b4-153">注释</span><span class="sxs-lookup"><span data-stu-id="b03b4-153">NOTES</span></span>

## <span data-ttu-id="b03b4-154">相关链接</span><span class="sxs-lookup"><span data-stu-id="b03b4-154">RELATED LINKS</span></span>

[<span data-ttu-id="b03b4-155">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b03b4-155">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b03b4-156">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b03b4-156">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b03b4-157">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b03b4-157">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b03b4-158">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="b03b4-158">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="b03b4-159">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b03b4-159">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b03b4-160">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b03b4-160">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b03b4-161">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b03b4-161">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b03b4-162">如何：配置 WINRM for HTTPS</span><span class="sxs-lookup"><span data-stu-id="b03b4-162">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="b03b4-163">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b03b4-163">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b03b4-164">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b03b4-164">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="b03b4-165">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b03b4-165">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b03b4-166">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b03b4-166">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b03b4-167">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b03b4-167">Test-WSMan</span></span>](Test-WSMan.md)

