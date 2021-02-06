---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603802"
---
# <span data-ttu-id="982c7-102">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-102">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="982c7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="982c7-103">SYNOPSIS</span></span>
<span data-ttu-id="982c7-104">禁用本地计算机上的会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-104">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="982c7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="982c7-105">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="982c7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="982c7-106">DESCRIPTION</span></span>

<span data-ttu-id="982c7-107">`Disable-PSSessionConfiguration`Cmdlet 可禁用本地计算机上的会话配置，从而防止所有用户使用会话配置创建用户管理的会话， (本地计算机上的 **pssession**) 。</span><span class="sxs-lookup"><span data-stu-id="982c7-107">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions (**PSSessions**) on the local computer.</span></span> <span data-ttu-id="982c7-108">这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。</span><span class="sxs-lookup"><span data-stu-id="982c7-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="982c7-109">从 PowerShell 3.0 开始， `Disable-PSSessionConfiguration` cmdlet 将会话配置的 **已启用** 设置 () 设置 `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` 为 False。</span><span class="sxs-lookup"><span data-stu-id="982c7-109">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="982c7-110">在 PowerShell 2.0 中， `Disable-PSSessionConfiguration` cmdlet 会将 **Deny_All** 条目添加到一个或多个已注册会话配置的安全描述符中。</span><span class="sxs-lookup"><span data-stu-id="982c7-110">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="982c7-111">如果没有参数， `Disable-PSSessionConfiguration` 则将禁用用于会话的默认配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-111">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="982c7-112">除非用户指定其他配置，否则这将有效阻止本地和远程用户创建任何连接到计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="982c7-112">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="982c7-113">若要禁用计算机上的所有会话配置，请使用 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="982c7-113">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="982c7-114">示例</span><span class="sxs-lookup"><span data-stu-id="982c7-114">EXAMPLES</span></span>

### <span data-ttu-id="982c7-115">示例 1：禁用默认配置</span><span class="sxs-lookup"><span data-stu-id="982c7-115">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="982c7-116">此示例禁用了 Microsoft PowerShell 会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-116">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="982c7-117">示例 2：禁用所有已注册的会话配置</span><span class="sxs-lookup"><span data-stu-id="982c7-117">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="982c7-118">此示例将禁用计算机上所有已注册的会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-118">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="982c7-119">示例 3：按名称禁用会话配置</span><span class="sxs-lookup"><span data-stu-id="982c7-119">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="982c7-120">此示例将禁用名称以 Microsoft 开头的所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-120">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="982c7-121">**Force** 参数取消了 cmdlet 中的所有用户提示。</span><span class="sxs-lookup"><span data-stu-id="982c7-121">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="982c7-122">示例 4：通过使用管道禁用会话配置</span><span class="sxs-lookup"><span data-stu-id="982c7-122">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="982c7-123">此示例将禁用 **MaintenanceShell** 和 **AdminShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-123">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="982c7-124">管道运算符 (|) 将的结果发送 `Get-PSSessionConfiguration` 到 `Disable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="982c7-124">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="982c7-125">示例 5：禁用会话配置的效果</span><span class="sxs-lookup"><span data-stu-id="982c7-125">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="982c7-126">此示例显示在运行之前和之后的权限 `Disable-PSSessionConfiguration` 以及禁用会话配置的效果。</span><span class="sxs-lookup"><span data-stu-id="982c7-126">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="982c7-127">禁用该配置不会阻止你使用 cmdlet 更改配置 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="982c7-127">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="982c7-128">它仅阻止使用该配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-128">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="982c7-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="982c7-129">PARAMETERS</span></span>

### <span data-ttu-id="982c7-130">-Force</span><span class="sxs-lookup"><span data-stu-id="982c7-130">-Force</span></span>

<span data-ttu-id="982c7-131">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="982c7-131">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="982c7-132">-Name</span><span class="sxs-lookup"><span data-stu-id="982c7-132">-Name</span></span>

<span data-ttu-id="982c7-133">指定要禁用的会话配置的名称数组。</span><span class="sxs-lookup"><span data-stu-id="982c7-133">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="982c7-134">输入一个或多个配置名称。</span><span class="sxs-lookup"><span data-stu-id="982c7-134">Enter one or more configuration names.</span></span> <span data-ttu-id="982c7-135">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="982c7-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="982c7-136">还可以通过管道将包含配置名称或会话配置对象的字符串传递给 `Disable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="982c7-136">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="982c7-137">如果省略此参数，则 `Disable-PSSessionConfiguration` 将禁用 Microsoft PowerShell 会话配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-137">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="982c7-138">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="982c7-138">-NoServiceRestart</span></span>

<span data-ttu-id="982c7-139">用于阻止重新启动 WSMan 服务。</span><span class="sxs-lookup"><span data-stu-id="982c7-139">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="982c7-140">不需要重新启动服务来禁用配置。</span><span class="sxs-lookup"><span data-stu-id="982c7-140">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="982c7-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="982c7-141">-Confirm</span></span>

<span data-ttu-id="982c7-142">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="982c7-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="982c7-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="982c7-143">-WhatIf</span></span>

<span data-ttu-id="982c7-144">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="982c7-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="982c7-145">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="982c7-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="982c7-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="982c7-146">CommonParameters</span></span>

<span data-ttu-id="982c7-147">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="982c7-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="982c7-148">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="982c7-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="982c7-149">输入</span><span class="sxs-lookup"><span data-stu-id="982c7-149">INPUTS</span></span>

### <span data-ttu-id="982c7-150">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String</span><span class="sxs-lookup"><span data-stu-id="982c7-150">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="982c7-151">可以通过管道将会话配置对象或包含会话配置名称的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="982c7-151">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="982c7-152">输出</span><span class="sxs-lookup"><span data-stu-id="982c7-152">OUTPUTS</span></span>

### <span data-ttu-id="982c7-153">无</span><span class="sxs-lookup"><span data-stu-id="982c7-153">None</span></span>

<span data-ttu-id="982c7-154">此 cmdlet 不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="982c7-154">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="982c7-155">注释</span><span class="sxs-lookup"><span data-stu-id="982c7-155">NOTES</span></span>

<span data-ttu-id="982c7-156">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="982c7-156">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="982c7-157">若要运行此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="982c7-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="982c7-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="982c7-158">RELATED LINKS</span></span>

[<span data-ttu-id="982c7-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="982c7-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="982c7-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="982c7-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="982c7-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="982c7-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="982c7-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="982c7-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="982c7-165">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="982c7-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="982c7-166">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="982c7-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="982c7-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="982c7-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="982c7-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="982c7-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
