---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 070a428530f4f3eecceb0ae3f520ad565097c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598475"
---
# <span data-ttu-id="12f49-102">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="12f49-102">Rename-Computer</span></span>

## <span data-ttu-id="12f49-103">摘要</span><span class="sxs-lookup"><span data-stu-id="12f49-103">SYNOPSIS</span></span>
<span data-ttu-id="12f49-104">重命名计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-104">Renames a computer.</span></span>

## <span data-ttu-id="12f49-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12f49-105">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12f49-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12f49-106">DESCRIPTION</span></span>

<span data-ttu-id="12f49-107">该 `Rename-Computer` cmdlet 将重命名本地计算机或远程计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-107">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="12f49-108">在一个命令中可重命名一台计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-108">It renames one computer in each command.</span></span>

<span data-ttu-id="12f49-109">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="12f49-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="12f49-110">示例</span><span class="sxs-lookup"><span data-stu-id="12f49-110">EXAMPLES</span></span>

### <span data-ttu-id="12f49-111">示例1：重命名本地计算机</span><span class="sxs-lookup"><span data-stu-id="12f49-111">Example 1: Rename the local computer</span></span>

<span data-ttu-id="12f49-112">此命令将本地计算机重命名为 `Server044` ，然后重新启动它以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="12f49-112">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="12f49-113">示例2：重命名远程计算机</span><span class="sxs-lookup"><span data-stu-id="12f49-113">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="12f49-114">此命令将计算机重命名 `Srv01` 为 `Server001` 。</span><span class="sxs-lookup"><span data-stu-id="12f49-114">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="12f49-115">计算机不会重新启动。</span><span class="sxs-lookup"><span data-stu-id="12f49-115">The computer is not restarted.</span></span>

<span data-ttu-id="12f49-116">**DomainCredential** 参数指定有权对域中的计算机进行重命名的用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="12f49-116">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="12f49-117">**Force** 参数取消显示确认提示。</span><span class="sxs-lookup"><span data-stu-id="12f49-117">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="12f49-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12f49-118">PARAMETERS</span></span>

### <span data-ttu-id="12f49-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="12f49-119">-ComputerName</span></span>

<span data-ttu-id="12f49-120">重命名指定的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-120">Renames the specified remote computer.</span></span>
<span data-ttu-id="12f49-121">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-121">The default is the local computer.</span></span>

<span data-ttu-id="12f49-122">键入远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="12f49-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="12f49-123">若要指定本地计算机，请键入计算机名、点 (`.`) 或 `localhost` 。</span><span class="sxs-lookup"><span data-stu-id="12f49-123">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="12f49-124">此参数不依赖于 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="12f49-124">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="12f49-125"> `Rename-Computer` 即使你的计算机未配置为运行远程命令，你也可以使用 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="12f49-125">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12f49-126">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="12f49-126">-DomainCredential</span></span>

<span data-ttu-id="12f49-127">指定有权连接到域的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="12f49-127">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="12f49-128">需要显式凭据才可重命名加入到域的计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-128">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="12f49-129">键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="12f49-129">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="12f49-130">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="12f49-130">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="12f49-131">若要指定有权连接到由 **ComputerName** 参数指定的计算机的用户帐户，请使用 **LocalCredential** 参数。</span><span class="sxs-lookup"><span data-stu-id="12f49-131">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12f49-132">-Force</span><span class="sxs-lookup"><span data-stu-id="12f49-132">-Force</span></span>

<span data-ttu-id="12f49-133">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="12f49-133">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="12f49-134">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="12f49-134">-LocalCredential</span></span>

<span data-ttu-id="12f49-135">指定有权连接到由 **ComputerName** 参数指定的计算机的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="12f49-135">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="12f49-136">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="12f49-136">The default is the current user.</span></span>

<span data-ttu-id="12f49-137">键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="12f49-137">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="12f49-138">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="12f49-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="12f49-139">若要指定有权连接到域的用户帐户，请使用 **DomainCredential** 参数。</span><span class="sxs-lookup"><span data-stu-id="12f49-139">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12f49-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="12f49-140">-NewName</span></span>

<span data-ttu-id="12f49-141">为计算机指定一个新名称。</span><span class="sxs-lookup"><span data-stu-id="12f49-141">Specifies a new name for the computer.</span></span>
<span data-ttu-id="12f49-142">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="12f49-142">This parameter is required.</span></span>

<span data-ttu-id="12f49-143">标准名称可能包含 (`a-z`) 、 (`A-Z`) 、数字 (`0-9`)  (和连字符) 的字母，但不 () `-` 空格或句点 `.` 。</span><span class="sxs-lookup"><span data-stu-id="12f49-143">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="12f49-144">名称不能完全由数字组成，且长度不得超过63个字符</span><span class="sxs-lookup"><span data-stu-id="12f49-144">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12f49-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12f49-145">-PassThru</span></span>

<span data-ttu-id="12f49-146">返回命令的结果。</span><span class="sxs-lookup"><span data-stu-id="12f49-146">Returns the results of the command.</span></span>
<span data-ttu-id="12f49-147">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="12f49-147">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="12f49-148">-Restart</span><span class="sxs-lookup"><span data-stu-id="12f49-148">-Restart</span></span>

<span data-ttu-id="12f49-149">指示此 cmdlet 重启已重命名的计算机。</span><span class="sxs-lookup"><span data-stu-id="12f49-149">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="12f49-150">若要更改生效，通常需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="12f49-150">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="12f49-151">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="12f49-151">-WsmanAuthentication</span></span>

<span data-ttu-id="12f49-152">指定此 cmdlet 使用 WSMan 协议时用于对用户的凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="12f49-152">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="12f49-153">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="12f49-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12f49-154">**基本**</span><span class="sxs-lookup"><span data-stu-id="12f49-154">**Basic**</span></span>
- <span data-ttu-id="12f49-155">CredSSP</span><span class="sxs-lookup"><span data-stu-id="12f49-155">**CredSSP**</span></span>
- <span data-ttu-id="12f49-156">**默认**</span><span class="sxs-lookup"><span data-stu-id="12f49-156">**Default**</span></span>
- <span data-ttu-id="12f49-157">摘要式</span><span class="sxs-lookup"><span data-stu-id="12f49-157">**Digest**</span></span>
- <span data-ttu-id="12f49-158">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="12f49-158">**Kerberos**</span></span>
- <span data-ttu-id="12f49-159">**Negotiate**</span><span class="sxs-lookup"><span data-stu-id="12f49-159">**Negotiate**</span></span>

<span data-ttu-id="12f49-160">默认值为 **Default**。</span><span class="sxs-lookup"><span data-stu-id="12f49-160">The default value is **Default**.</span></span>

<span data-ttu-id="12f49-161">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="12f49-161">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="12f49-162">凭据安全服务提供程序 (CredSSP) 身份验证，在此身份验证中，用户凭据传递到远程计算机进行身份验证时，需要对多个资源（例如访问远程网络共享）进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="12f49-162">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="12f49-163">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="12f49-163">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="12f49-164">如果远程计算机被泄露，则传递到该计算机的凭据可用于控制网络会话 >。</span><span class="sxs-lookup"><span data-stu-id="12f49-164">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="12f49-165">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="12f49-165">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12f49-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12f49-166">-Confirm</span></span>

<span data-ttu-id="12f49-167">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="12f49-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="12f49-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12f49-168">-WhatIf</span></span>

<span data-ttu-id="12f49-169">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="12f49-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="12f49-170">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="12f49-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="12f49-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12f49-171">CommonParameters</span></span>

<span data-ttu-id="12f49-172">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12f49-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12f49-173">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="12f49-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="12f49-174">输入</span><span class="sxs-lookup"><span data-stu-id="12f49-174">INPUTS</span></span>

### <span data-ttu-id="12f49-175">无</span><span class="sxs-lookup"><span data-stu-id="12f49-175">None</span></span>

<span data-ttu-id="12f49-176">此 cmdlet 不具有按值获取输入的参数。</span><span class="sxs-lookup"><span data-stu-id="12f49-176">This cmdlet does not have parameters that take input by value.</span></span> <span data-ttu-id="12f49-177">但是，你可以通过管道将对象的 **ComputerName** 和 **NewName** 属性的值传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12f49-177">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="12f49-178">输出</span><span class="sxs-lookup"><span data-stu-id="12f49-178">OUTPUTS</span></span>

### <span data-ttu-id="12f49-179">Microsoft.PowerShell.Commands.ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="12f49-179">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="12f49-180">如果指定 **PassThru** 参数，则此 cmdlet 将返回 **ComputerChangeInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="12f49-180">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="12f49-181">否则，将不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="12f49-181">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="12f49-182">注释</span><span class="sxs-lookup"><span data-stu-id="12f49-182">NOTES</span></span>

<span data-ttu-id="12f49-183">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="12f49-183">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="12f49-184">相关链接</span><span class="sxs-lookup"><span data-stu-id="12f49-184">RELATED LINKS</span></span>

[<span data-ttu-id="12f49-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="12f49-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="12f49-186">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="12f49-186">Stop-Computer</span></span>](Stop-Computer.md)
