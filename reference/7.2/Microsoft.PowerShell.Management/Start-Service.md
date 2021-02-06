---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: b1df4490da501111ccb44dea2645a333fdf5c27e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603407"
---
# <span data-ttu-id="617cf-102">Start-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-102">Start-Service</span></span>

## <span data-ttu-id="617cf-103">摘要</span><span class="sxs-lookup"><span data-stu-id="617cf-103">SYNOPSIS</span></span>
<span data-ttu-id="617cf-104">启动一个或多个已停止的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-104">Starts one or more stopped services.</span></span>

## <span data-ttu-id="617cf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="617cf-105">SYNTAX</span></span>

### <span data-ttu-id="617cf-106">InputObject（默认值）</span><span class="sxs-lookup"><span data-stu-id="617cf-106">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="617cf-107">默认</span><span class="sxs-lookup"><span data-stu-id="617cf-107">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="617cf-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="617cf-108">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="617cf-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="617cf-109">DESCRIPTION</span></span>

<span data-ttu-id="617cf-110">`Start-Service`Cmdlet 为每个指定的服务向 Windows 服务控制器发送一条启动消息。</span><span class="sxs-lookup"><span data-stu-id="617cf-110">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="617cf-111">如果服务已在运行，则无错误忽略该消息。</span><span class="sxs-lookup"><span data-stu-id="617cf-111">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="617cf-112">可以通过服务名称或显示名称指定服务，也可使用 InputObject 参数提供一个服务对象，表示要启动的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="617cf-113">示例</span><span class="sxs-lookup"><span data-stu-id="617cf-113">EXAMPLES</span></span>

### <span data-ttu-id="617cf-114">示例 1：通过使用服务名称启动服务</span><span class="sxs-lookup"><span data-stu-id="617cf-114">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="617cf-115">此示例启动本地计算机上的 EventLog 服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-115">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="617cf-116">**Name** 参数通过服务名称来标识服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-116">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="617cf-117">示例 2：在不启动服务的情况下显示信息</span><span class="sxs-lookup"><span data-stu-id="617cf-117">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="617cf-118">此示例显示了启动显示名称中包含 "remote" 的服务后会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="617cf-118">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="617cf-119">**DisplayName** 参数通过显示名称而不是服务名称来标识服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-119">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="617cf-120">**WhatIf** 参数会使 cmdlet 显示运行命令时所发生的情况，但不会发生更改。</span><span class="sxs-lookup"><span data-stu-id="617cf-120">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="617cf-121">示例 3：启动服务，并将操作记录到文本文件中</span><span class="sxs-lookup"><span data-stu-id="617cf-121">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="617cf-122">此示例启动计算机上的 Windows Management Instrumentation (WMI) 服务，并将操作的记录添加到 services.txt 文件中。</span><span class="sxs-lookup"><span data-stu-id="617cf-122">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="617cf-123">首先，我们使用 `Get-Service` 来获取表示 WMI 服务的对象，并将其存储在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="617cf-123">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="617cf-124">接下来，我们启动该服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-124">Next, we start the service.</span></span> <span data-ttu-id="617cf-125">如果没有 **PassThru** 参数，则不 `Start-Service` 会创建任何输出。</span><span class="sxs-lookup"><span data-stu-id="617cf-125">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="617cf-126">管道运算符 (|) 将对象输出传递 `Start-Service` 给 cmdlet， `Format-List` 以将对象的格式设置为其属性列表。</span><span class="sxs-lookup"><span data-stu-id="617cf-126">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="617cf-127">追加重定向运算符 (将 \> \> 输出重定向到 services.txt 文件) 。</span><span class="sxs-lookup"><span data-stu-id="617cf-127">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="617cf-128">将输出添加到现有文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="617cf-128">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="617cf-129">示例 4：启动禁用的服务</span><span class="sxs-lookup"><span data-stu-id="617cf-129">Example 4: Start a disabled service</span></span>

<span data-ttu-id="617cf-130">此示例演示如何在 **禁用** 服务的启动类型时启动服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-130">This example shows how to start a service when the start type of the service is **Disabled**.</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="617cf-131">第一次尝试启动 Telnet 服务 (tlntsvr) 失败。</span><span class="sxs-lookup"><span data-stu-id="617cf-131">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="617cf-132">该 `Get-CimInstance` 命令显示 Tlntsvr 服务的 **StartMode** 属性已 **禁用**。</span><span class="sxs-lookup"><span data-stu-id="617cf-132">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled**.</span></span> <span data-ttu-id="617cf-133">`Set-Service`Cmdlet 将启动类型更改为 "**手动**"。</span><span class="sxs-lookup"><span data-stu-id="617cf-133">The `Set-Service` cmdlet changes the start type to **Manual**.</span></span> <span data-ttu-id="617cf-134">现在，我们可以重新提交 `Start-Service` 命令。</span><span class="sxs-lookup"><span data-stu-id="617cf-134">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="617cf-135">这次，该命令执行成功。</span><span class="sxs-lookup"><span data-stu-id="617cf-135">This time, the command succeeds.</span></span> <span data-ttu-id="617cf-136">若要验证命令是否成功，请运行 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="617cf-136">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="617cf-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="617cf-137">PARAMETERS</span></span>

### <span data-ttu-id="617cf-138">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="617cf-138">-DisplayName</span></span>

<span data-ttu-id="617cf-139">指定要启动的服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="617cf-139">Specifies the display names of the services to start.</span></span> <span data-ttu-id="617cf-140">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="617cf-140">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="617cf-141">-Exclude</span><span class="sxs-lookup"><span data-stu-id="617cf-141">-Exclude</span></span>

<span data-ttu-id="617cf-142">指定此 cmdlet 省略的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-142">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="617cf-143">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="617cf-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="617cf-144">输入名称元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="617cf-144">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="617cf-145">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="617cf-145">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="617cf-146">-Include</span><span class="sxs-lookup"><span data-stu-id="617cf-146">-Include</span></span>

<span data-ttu-id="617cf-147">指定此 cmdlet 启动的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-147">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="617cf-148">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="617cf-148">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="617cf-149">输入名称元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="617cf-149">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="617cf-150">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="617cf-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="617cf-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="617cf-151">-InputObject</span></span>

<span data-ttu-id="617cf-152">指定表示要启动的服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="617cf-152">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="617cf-153">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="617cf-153">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="617cf-154">-Name</span><span class="sxs-lookup"><span data-stu-id="617cf-154">-Name</span></span>

<span data-ttu-id="617cf-155">指定要启动的服务的服务名称。</span><span class="sxs-lookup"><span data-stu-id="617cf-155">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="617cf-156">参数名为可选项。</span><span class="sxs-lookup"><span data-stu-id="617cf-156">The parameter name is optional.</span></span> <span data-ttu-id="617cf-157">您可以使用 **Name** 或其 **别名，也** 可以省略参数名称。</span><span class="sxs-lookup"><span data-stu-id="617cf-157">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="617cf-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="617cf-158">-PassThru</span></span>

<span data-ttu-id="617cf-159">返回一个表示服务的对象。</span><span class="sxs-lookup"><span data-stu-id="617cf-159">Returns an object that represents the service.</span></span> <span data-ttu-id="617cf-160">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="617cf-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="617cf-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="617cf-161">-Confirm</span></span>

<span data-ttu-id="617cf-162">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="617cf-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="617cf-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="617cf-163">-WhatIf</span></span>

<span data-ttu-id="617cf-164">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="617cf-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="617cf-165">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="617cf-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="617cf-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="617cf-166">CommonParameters</span></span>

<span data-ttu-id="617cf-167">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="617cf-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="617cf-168">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="617cf-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="617cf-169">输入</span><span class="sxs-lookup"><span data-stu-id="617cf-169">INPUTS</span></span>

### <span data-ttu-id="617cf-170">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="617cf-170">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="617cf-171">可以通过管道将对象（该对象表示包含服务名称的服务或字符串）传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="617cf-171">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="617cf-172">输出</span><span class="sxs-lookup"><span data-stu-id="617cf-172">OUTPUTS</span></span>

### <span data-ttu-id="617cf-173">无、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="617cf-173">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="617cf-174">如果指定 PassThru，此 cmdlet 会生成表示服务的 **System.ServiceProcess.ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="617cf-174">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru**.</span></span> <span data-ttu-id="617cf-175">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="617cf-175">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="617cf-176">注释</span><span class="sxs-lookup"><span data-stu-id="617cf-176">NOTES</span></span>

<span data-ttu-id="617cf-177">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="617cf-177">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="617cf-178">还可以 `Start-Service` 通过其内置别名来引用 `sasv` 。</span><span class="sxs-lookup"><span data-stu-id="617cf-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="617cf-179">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="617cf-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="617cf-180">`Start-Service` 只有在当前用户有权执行此操作的情况下，才能控制服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="617cf-181">如果某个命令不能正常工作，则可能你不具有所需的权限。</span><span class="sxs-lookup"><span data-stu-id="617cf-181">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="617cf-182">若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="617cf-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="617cf-183">服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。</span><span class="sxs-lookup"><span data-stu-id="617cf-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
- <span data-ttu-id="617cf-184">只能启动启动类型为 "手动"、"自动" 或 "自动" (延迟启动) 的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="617cf-185">无法启动启动类型为 Disabled 的服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="617cf-186">如果 `Start-Service` 命令失败，并出现消息 `Cannot start service \<service-name\> on computer` ，请使用 `Get-CimInstance` 查找服务的启动类型，如果需要，请使用 `Set-Service` cmdlet 更改服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="617cf-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
- <span data-ttu-id="617cf-187">某些服务在没有工作时将自动停止，例如性能日志和警报 (SysmonLog) 服务。</span><span class="sxs-lookup"><span data-stu-id="617cf-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="617cf-188">当 PowerShell 启动一项几乎立即停止的服务时，它会显示以下消息： `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="617cf-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="617cf-189">相关链接</span><span class="sxs-lookup"><span data-stu-id="617cf-189">RELATED LINKS</span></span>

[<span data-ttu-id="617cf-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="617cf-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="617cf-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="617cf-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="617cf-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="617cf-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="617cf-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-196">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="617cf-197">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="617cf-197">Remove-Service</span></span>](Remove-Service.md)
