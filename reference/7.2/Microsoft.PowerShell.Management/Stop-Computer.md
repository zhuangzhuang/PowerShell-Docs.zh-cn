---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597846"
---
# <span data-ttu-id="1c3bd-102">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="1c3bd-102">Stop-Computer</span></span>

## <span data-ttu-id="1c3bd-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1c3bd-103">SYNOPSIS</span></span>
<span data-ttu-id="1c3bd-104">停止（关闭）本地和远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-104">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="1c3bd-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1c3bd-105">SYNTAX</span></span>

### <span data-ttu-id="1c3bd-106">全部</span><span class="sxs-lookup"><span data-stu-id="1c3bd-106">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1c3bd-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1c3bd-107">DESCRIPTION</span></span>

<span data-ttu-id="1c3bd-108">Cmdlet 将关闭 `Stop-Computer` 本地计算机和远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-108">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="1c3bd-109">你可以使用的参数 `Stop-Computer` 来指定身份验证级别和备用凭据，并强制立即关闭。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-109">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="1c3bd-110">在 PowerShell 7.1 中， `Stop-Computer` 为 Linux 和 macOS 添加了。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-110">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="1c3bd-111">参数在这些平台上不起作用。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-111">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="1c3bd-112">该 cmdlet 只调用本机命令 `/sbin/shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-112">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="1c3bd-113">示例</span><span class="sxs-lookup"><span data-stu-id="1c3bd-113">EXAMPLES</span></span>

### <span data-ttu-id="1c3bd-114">示例 1：关闭本地计算机</span><span class="sxs-lookup"><span data-stu-id="1c3bd-114">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="1c3bd-115">此示例关闭本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-115">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="1c3bd-116">示例 2：关闭两台远程计算机和本地计算机</span><span class="sxs-lookup"><span data-stu-id="1c3bd-116">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="1c3bd-117">此示例将停止两台远程计算机和本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-117">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="1c3bd-118">`Stop-Computer` 使用 **ComputerName** 参数指定两台远程计算机和本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-118">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="1c3bd-119">每台计算机都已关闭。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-119">Each computer is shut down.</span></span>

### <span data-ttu-id="1c3bd-120">示例 3：关闭远程计算机，作为后台作业运行</span><span class="sxs-lookup"><span data-stu-id="1c3bd-120">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="1c3bd-121">在此示例中，在 `Stop-Computer` 两台远程计算机上作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-121">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="1c3bd-122">后台运算符将 `&` `Stop-Computer` 命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-122">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="1c3bd-123">有关详细信息，请参阅 [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-123">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="1c3bd-124">`Stop-Computer` 使用 **ComputerName** 参数指定两台远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-124">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="1c3bd-125">`&`后台运算符将命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-125">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="1c3bd-126">作业对象存储在 `$j` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-126">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="1c3bd-127">变量中的作业对象 `$j` 会向下发送到 `Receive-Job` ，后者将获取作业结果。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-127">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="1c3bd-128">这些对象存储在变量中 `$results` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-128">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="1c3bd-129">此 `$results` 变量在 PowerShell 控制台中显示作业信息。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-129">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="1c3bd-130">示例 4：关闭远程计算机</span><span class="sxs-lookup"><span data-stu-id="1c3bd-130">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="1c3bd-131">此示例使用指定的身份验证关闭远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-131">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="1c3bd-132">`Stop-Computer` 使用 **ComputerName** 参数来指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-132">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="1c3bd-133">**WsmanAuthentication** 参数指定使用 Kerberos 建立远程连接。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-133">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="1c3bd-134">示例5：关闭域中的计算机</span><span class="sxs-lookup"><span data-stu-id="1c3bd-134">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="1c3bd-135">在此示例中，这些命令强制立即关闭指定域中的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-135">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="1c3bd-136">`Get-Content` 使用 **Path** 参数获取当前目录中包含域计算机列表的文件。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-136">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="1c3bd-137">这些对象存储在变量中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-137">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="1c3bd-138">`Get-Credential` 使用 **Credential** 参数指定域管理员的凭据。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-138">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="1c3bd-139">凭据存储在 `$c` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-139">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="1c3bd-140">`Stop-Computer` 关闭在变量中用 **ComputerName** 参数的计算机列表指定的计算机 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-140">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="1c3bd-141">**Force** 参数强制立即关闭。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-141">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="1c3bd-142">**Credential** 参数提交保存在变量中的凭据 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-142">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="1c3bd-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1c3bd-143">PARAMETERS</span></span>

### <span data-ttu-id="1c3bd-144">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1c3bd-144">-ComputerName</span></span>

<span data-ttu-id="1c3bd-145">指定要停止的计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-145">Specifies the computers to stop.</span></span> <span data-ttu-id="1c3bd-146">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-146">The default is the local computer.</span></span>

<span data-ttu-id="1c3bd-147">在一个逗号分隔列表中键入一台或多台计算机的 NETBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-147">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="1c3bd-148">若要指定本地计算机，请键入计算机名称或“localhost”。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-148">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="1c3bd-149">此参数不依赖于 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-149">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="1c3bd-150">即使你的计算机未配置为运行远程命令，你也可以使用 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-150">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1c3bd-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c3bd-151">-Confirm</span></span>

<span data-ttu-id="1c3bd-152">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c3bd-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="1c3bd-153">-Credential</span></span>

<span data-ttu-id="1c3bd-154">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-154">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="1c3bd-155">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-155">The default is the current user.</span></span>

<span data-ttu-id="1c3bd-156">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-156">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1c3bd-157">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-157">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="1c3bd-158">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-158">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1c3bd-159">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-159">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="1c3bd-160">-Force</span><span class="sxs-lookup"><span data-stu-id="1c3bd-160">-Force</span></span>

<span data-ttu-id="1c3bd-161">强制立即关闭计算机。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-161">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="1c3bd-162">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="1c3bd-162">-WsmanAuthentication</span></span>

<span data-ttu-id="1c3bd-163">指定此 cmdlet 使用 WSMan 协议时用于对用户的凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-163">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="1c3bd-164">默认值为 **Default**。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-164">The default value is **Default**.</span></span>

<span data-ttu-id="1c3bd-165">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="1c3bd-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1c3bd-166">基本</span><span class="sxs-lookup"><span data-stu-id="1c3bd-166">Basic</span></span>
- <span data-ttu-id="1c3bd-167">CredSSP</span><span class="sxs-lookup"><span data-stu-id="1c3bd-167">CredSSP</span></span>
- <span data-ttu-id="1c3bd-168">默认</span><span class="sxs-lookup"><span data-stu-id="1c3bd-168">Default</span></span>
- <span data-ttu-id="1c3bd-169">摘要</span><span class="sxs-lookup"><span data-stu-id="1c3bd-169">Digest</span></span>
- <span data-ttu-id="1c3bd-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1c3bd-170">Kerberos</span></span>
- <span data-ttu-id="1c3bd-171">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-171">Negotiate.</span></span>

<span data-ttu-id="1c3bd-172">有关此参数的值的详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-172">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="1c3bd-173">凭据安全服务提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-173">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="1c3bd-174">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-174">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="1c3bd-175">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-175">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="1c3bd-176">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-176">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c3bd-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c3bd-177">-WhatIf</span></span>

<span data-ttu-id="1c3bd-178">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1c3bd-179">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-179">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1c3bd-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c3bd-180">CommonParameters</span></span>

<span data-ttu-id="1c3bd-181">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c3bd-182">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c3bd-183">输入</span><span class="sxs-lookup"><span data-stu-id="1c3bd-183">INPUTS</span></span>

### <span data-ttu-id="1c3bd-184">无</span><span class="sxs-lookup"><span data-stu-id="1c3bd-184">None</span></span>

<span data-ttu-id="1c3bd-185">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-185">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1c3bd-186">输出</span><span class="sxs-lookup"><span data-stu-id="1c3bd-186">OUTPUTS</span></span>

### <span data-ttu-id="1c3bd-187">无</span><span class="sxs-lookup"><span data-stu-id="1c3bd-187">None</span></span>

## <span data-ttu-id="1c3bd-188">注释</span><span class="sxs-lookup"><span data-stu-id="1c3bd-188">NOTES</span></span>

<span data-ttu-id="1c3bd-189">此 cmdlet 使用 **Win32_OperatingSystem** WMI 类的 **Win32Shutdown** 方法。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-189">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="1c3bd-190">此方法需要为用于重新启动计算机的用户帐户启用 **SeShutdownPrivilege** 特权。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-190">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="1c3bd-191">在 PowerShell 7.1 中， `Stop-Computer` 为 Linux 和 macOS 添加了。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-191">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="1c3bd-192">对于这些平台，cmdlet 将调用本机命令 `/sbin/shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="1c3bd-192">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="1c3bd-193">相关链接</span><span class="sxs-lookup"><span data-stu-id="1c3bd-193">RELATED LINKS</span></span>

[<span data-ttu-id="1c3bd-194">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="1c3bd-194">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="1c3bd-195">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1c3bd-195">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="1c3bd-196">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="1c3bd-196">Test-Connection</span></span>](Test-Connection.md)

