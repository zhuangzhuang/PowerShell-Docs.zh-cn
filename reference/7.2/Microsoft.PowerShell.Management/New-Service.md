---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: d3c6d77db88683c134335cf05d0165b542644b7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598877"
---
# <span data-ttu-id="a1221-102">New-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-102">New-Service</span></span>

## <span data-ttu-id="a1221-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a1221-103">SYNOPSIS</span></span>
<span data-ttu-id="a1221-104">创建新的 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="a1221-104">Creates a new Windows service.</span></span>

## <span data-ttu-id="a1221-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1221-105">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a1221-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a1221-106">DESCRIPTION</span></span>

<span data-ttu-id="a1221-107">`New-Service`Cmdlet 在注册表和服务数据库中为 Windows 服务创建一个新条目。</span><span class="sxs-lookup"><span data-stu-id="a1221-107">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="a1221-108">新服务需要在服务过程中运行的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="a1221-108">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="a1221-109">此 cmdlet 的参数用于设置该服务的显示名称、说明、启动类型和依赖项。</span><span class="sxs-lookup"><span data-stu-id="a1221-109">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="a1221-110">示例</span><span class="sxs-lookup"><span data-stu-id="a1221-110">EXAMPLES</span></span>

### <span data-ttu-id="a1221-111">示例1：创建服务</span><span class="sxs-lookup"><span data-stu-id="a1221-111">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="a1221-112">此命令创建名为 TestService 的服务。</span><span class="sxs-lookup"><span data-stu-id="a1221-112">This command creates a service named TestService.</span></span>

### <span data-ttu-id="a1221-113">示例2：创建包含说明、启动类型和显示名称的服务</span><span class="sxs-lookup"><span data-stu-id="a1221-113">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="a1221-114">此命令创建名为 TestService 的服务。</span><span class="sxs-lookup"><span data-stu-id="a1221-114">This command creates a service named TestService.</span></span> <span data-ttu-id="a1221-115">它使用的参数 `New-Service` 来指定新服务的说明、启动类型和显示名称。</span><span class="sxs-lookup"><span data-stu-id="a1221-115">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="a1221-116">示例3：查看新服务</span><span class="sxs-lookup"><span data-stu-id="a1221-116">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="a1221-117">此命令使用 `Get-CimInstance` 获取新服务的 **Win32_Service** 对象。</span><span class="sxs-lookup"><span data-stu-id="a1221-117">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="a1221-118">此对象包含启动模式和服务说明。</span><span class="sxs-lookup"><span data-stu-id="a1221-118">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="a1221-119">示例4：创建服务时设置服务的 SecurityDescriptor。</span><span class="sxs-lookup"><span data-stu-id="a1221-119">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="a1221-120">此示例将添加正在创建的服务的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="a1221-120">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="a1221-121">**SecurityDescriptor** 存储在 `$SDDLToSet` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a1221-121">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="a1221-122">**SecurityDescriptorSddl** 参数用于 `$SDDL` 设置新服务的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="a1221-122">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="a1221-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1221-123">PARAMETERS</span></span>

### <span data-ttu-id="a1221-124">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="a1221-124">-BinaryPathName</span></span>

<span data-ttu-id="a1221-125">指定服务的可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a1221-125">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="a1221-126">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="a1221-126">This parameter is required.</span></span>

<span data-ttu-id="a1221-127">服务二进制文件的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="a1221-127">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="a1221-128">如果路径包含空格，则必须将其括在引号中，以便对其进行正确解释。</span><span class="sxs-lookup"><span data-stu-id="a1221-128">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="a1221-129">例如， `d:\my share\myservice.exe` 应将指定为 `'"d:\my share\myservice.exe"'` 。</span><span class="sxs-lookup"><span data-stu-id="a1221-129">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="a1221-130">该路径还可以包含自动启动服务的参数。</span><span class="sxs-lookup"><span data-stu-id="a1221-130">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="a1221-131">例如，`'"d:\myshare\myservice.exe arg1 arg2"'`。</span><span class="sxs-lookup"><span data-stu-id="a1221-131">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="a1221-132">这些参数将传递到服务入口点。</span><span class="sxs-lookup"><span data-stu-id="a1221-132">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="a1221-133">有关详细信息，请参阅 [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API 的 **lpBinaryPathName** 参数。</span><span class="sxs-lookup"><span data-stu-id="a1221-133">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1221-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="a1221-134">-Credential</span></span>

<span data-ttu-id="a1221-135">将服务使用的帐户指定为 [服务登录帐户](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="a1221-135">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="a1221-136">键入用户名（如 **User01** 或 **Domain01\User01**）或输入 PSCredential 对象，例如由 Cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a1221-136">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a1221-137">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="a1221-137">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a1221-138">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="a1221-138">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a1221-139">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="a1221-139">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="a1221-140">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="a1221-140">-DependsOn</span></span>

<span data-ttu-id="a1221-141">指定新服务所依赖的其他服务的名称。</span><span class="sxs-lookup"><span data-stu-id="a1221-141">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="a1221-142">若要输入多个服务名称，请使用逗号分隔这些名称。</span><span class="sxs-lookup"><span data-stu-id="a1221-142">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="a1221-143">-Description</span><span class="sxs-lookup"><span data-stu-id="a1221-143">-Description</span></span>

<span data-ttu-id="a1221-144">指定服务的描述。</span><span class="sxs-lookup"><span data-stu-id="a1221-144">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="a1221-145">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="a1221-145">-DisplayName</span></span>

<span data-ttu-id="a1221-146">指定服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="a1221-146">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="a1221-147">-Name</span><span class="sxs-lookup"><span data-stu-id="a1221-147">-Name</span></span>

<span data-ttu-id="a1221-148">指定服务的名称。</span><span class="sxs-lookup"><span data-stu-id="a1221-148">Specifies the name of the service.</span></span> <span data-ttu-id="a1221-149">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="a1221-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1221-150">-StartupType</span><span class="sxs-lookup"><span data-stu-id="a1221-150">-StartupType</span></span>

<span data-ttu-id="a1221-151">设置服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="a1221-151">Sets the startup type of the service.</span></span> <span data-ttu-id="a1221-152">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="a1221-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a1221-153">**自动** -服务已启动或由操作系统在系统启动时启动。</span><span class="sxs-lookup"><span data-stu-id="a1221-153">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="a1221-154">如果一个自动启动的服务依赖于手动启动的服务，则该手动启动的服务也会在系统启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="a1221-154">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="a1221-155">**AutomaticDelayedStart** -系统启动后立即启动。</span><span class="sxs-lookup"><span data-stu-id="a1221-155">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="a1221-156">**已禁用** -服务已禁用，无法由用户或应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="a1221-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="a1221-157">**InvalidValue** -不支持此值。</span><span class="sxs-lookup"><span data-stu-id="a1221-157">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="a1221-158">使用此值将导致错误。</span><span class="sxs-lookup"><span data-stu-id="a1221-158">Using this value results in an error.</span></span>
- <span data-ttu-id="a1221-159">**手动** -服务仅通过用户、使用服务控制管理器或应用程序手动启动。</span><span class="sxs-lookup"><span data-stu-id="a1221-159">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="a1221-160">默认值为 " **自动**"。</span><span class="sxs-lookup"><span data-stu-id="a1221-160">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1221-161">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="a1221-161">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="a1221-162">以 **Sddl** 格式指定服务的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="a1221-162">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1221-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a1221-163">-Confirm</span></span>

<span data-ttu-id="a1221-164">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="a1221-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a1221-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a1221-165">-WhatIf</span></span>

<span data-ttu-id="a1221-166">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="a1221-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a1221-167">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="a1221-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a1221-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1221-168">CommonParameters</span></span>

<span data-ttu-id="a1221-169">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a1221-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1221-170">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a1221-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1221-171">输入</span><span class="sxs-lookup"><span data-stu-id="a1221-171">INPUTS</span></span>

### <span data-ttu-id="a1221-172">无</span><span class="sxs-lookup"><span data-stu-id="a1221-172">None</span></span>

<span data-ttu-id="a1221-173">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1221-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a1221-174">输出</span><span class="sxs-lookup"><span data-stu-id="a1221-174">OUTPUTS</span></span>

### <span data-ttu-id="a1221-175">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="a1221-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="a1221-176">此 cmdlet 将返回一个表示新服务的对象。</span><span class="sxs-lookup"><span data-stu-id="a1221-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="a1221-177">注释</span><span class="sxs-lookup"><span data-stu-id="a1221-177">NOTES</span></span>

<span data-ttu-id="a1221-178">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="a1221-178">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="a1221-179">若要运行此 cmdlet，请使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a1221-179">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="a1221-180">相关链接</span><span class="sxs-lookup"><span data-stu-id="a1221-180">RELATED LINKS</span></span>

[<span data-ttu-id="a1221-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="a1221-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="a1221-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="a1221-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="a1221-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="a1221-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="a1221-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="a1221-188">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="a1221-188">Remove-Service</span></span>](Remove-Service.md)
