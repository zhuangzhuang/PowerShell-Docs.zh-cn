---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597255"
---
# <span data-ttu-id="dd9bc-102">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-102">Resume-Service</span></span>

## <span data-ttu-id="dd9bc-103">摘要</span><span class="sxs-lookup"><span data-stu-id="dd9bc-103">SYNOPSIS</span></span>
<span data-ttu-id="dd9bc-104">恢复一项或多项挂起（暂停的）服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-104">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="dd9bc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd9bc-105">SYNTAX</span></span>

### <span data-ttu-id="dd9bc-106">InputObject（默认值）</span><span class="sxs-lookup"><span data-stu-id="dd9bc-106">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dd9bc-107">默认</span><span class="sxs-lookup"><span data-stu-id="dd9bc-107">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="dd9bc-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="dd9bc-108">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dd9bc-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dd9bc-109">DESCRIPTION</span></span>

<span data-ttu-id="dd9bc-110">`Resume-Service`Cmdlet 为每个指定的服务向 Windows 服务控制器发送一条恢复消息。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-110">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="dd9bc-111">如果服务已挂起，则会恢复。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-111">If a service is suspended, it resumes.</span></span> <span data-ttu-id="dd9bc-112">如果当前正在运行，则忽略该消息。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-112">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="dd9bc-113">你可以通过服务名称或显示名称来指定服务，也可以使用 **InputObject** 参数传递表示要恢复的服务的服务对象。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="dd9bc-114">示例</span><span class="sxs-lookup"><span data-stu-id="dd9bc-114">EXAMPLES</span></span>

### <span data-ttu-id="dd9bc-115">示例1：在本地计算机上恢复服务</span><span class="sxs-lookup"><span data-stu-id="dd9bc-115">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="dd9bc-116">此命令在本地计算机上恢复系统事件通知服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-116">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="dd9bc-117">服务名称在命令中由 sens 表示。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-117">The service name is represented in the command by sens.</span></span> <span data-ttu-id="dd9bc-118">该命令使用 **name** 参数来指定服务的服务名称，但该命令省略了参数名称，因为参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-118">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="dd9bc-119">示例2：恢复所有挂起的服务</span><span class="sxs-lookup"><span data-stu-id="dd9bc-119">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="dd9bc-120">此命令恢复计算机上所有挂起的服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-120">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="dd9bc-121">`Get-Service`Cmdlet 命令获取计算机上的所有服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-121">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="dd9bc-122">管道运算符 (`|`) 将结果传递给 `Where-Object` cmdlet，后者选择 **状态** 属性为 "已暂停" 的服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-122">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="dd9bc-123">下一个管道运算符将结果发送到 `Resume-Service` ，后者将恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-123">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="dd9bc-124">在实际操作中，你将使用 **WhatIf** 参数来确定该命令的影响，然后再运行该命令。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="dd9bc-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd9bc-125">PARAMETERS</span></span>

### <span data-ttu-id="dd9bc-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="dd9bc-126">-DisplayName</span></span>

<span data-ttu-id="dd9bc-127">指定要恢复的服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-127">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="dd9bc-128">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dd9bc-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="dd9bc-129">-Exclude</span></span>

<span data-ttu-id="dd9bc-130">指定此 cmdlet 省略的服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="dd9bc-131">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="dd9bc-132">输入名称元素或模式，例如 "s \*"。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="dd9bc-133">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dd9bc-134">-Include</span><span class="sxs-lookup"><span data-stu-id="dd9bc-134">-Include</span></span>

<span data-ttu-id="dd9bc-135">指定要恢复的服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-135">Specifies services to resume.</span></span> <span data-ttu-id="dd9bc-136">此参数的值限定 **Name** 参数。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-136">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="dd9bc-137">输入名称元素或模式，例如 "s \*"。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="dd9bc-138">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dd9bc-139">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dd9bc-139">-InputObject</span></span>

<span data-ttu-id="dd9bc-140">指定表示要恢复的服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-140">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="dd9bc-141">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-141">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="dd9bc-142">-Name</span><span class="sxs-lookup"><span data-stu-id="dd9bc-142">-Name</span></span>

<span data-ttu-id="dd9bc-143">指定要恢复的服务的服务名称。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-143">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="dd9bc-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="dd9bc-144">-PassThru</span></span>

<span data-ttu-id="dd9bc-145">返回一个表示服务的对象。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-145">Returns an object that represents the service.</span></span> <span data-ttu-id="dd9bc-146">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-146">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="dd9bc-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dd9bc-147">-Confirm</span></span>

<span data-ttu-id="dd9bc-148">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dd9bc-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dd9bc-149">-WhatIf</span></span>

<span data-ttu-id="dd9bc-150">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="dd9bc-151">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-151">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dd9bc-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd9bc-152">CommonParameters</span></span>

<span data-ttu-id="dd9bc-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd9bc-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd9bc-155">输入</span><span class="sxs-lookup"><span data-stu-id="dd9bc-155">INPUTS</span></span>

### <span data-ttu-id="dd9bc-156">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="dd9bc-156">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="dd9bc-157">可以通过管道将服务对象或包含服务名称的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-157">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="dd9bc-158">输出</span><span class="sxs-lookup"><span data-stu-id="dd9bc-158">OUTPUTS</span></span>

### <span data-ttu-id="dd9bc-159">无、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="dd9bc-159">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="dd9bc-160">如果指定 **PassThru** 参数，则此 cmdlet 将生成表示已恢复服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-160">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="dd9bc-161">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dd9bc-162">注释</span><span class="sxs-lookup"><span data-stu-id="dd9bc-162">NOTES</span></span>

<span data-ttu-id="dd9bc-163">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-163">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="dd9bc-164">已暂停的服务的状态为 "已暂停"。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="dd9bc-165">当服务恢复后，其状态为 "正在运行"。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-165">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="dd9bc-166">`Resume-Service` 仅当当前用户有权执行此操作时，才能控制服务。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-166">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="dd9bc-167">如果某个命令不能正常工作，则可能你不具有所需的权限。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="dd9bc-168">若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="dd9bc-169">服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。</span><span class="sxs-lookup"><span data-stu-id="dd9bc-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="dd9bc-170">相关链接</span><span class="sxs-lookup"><span data-stu-id="dd9bc-170">RELATED LINKS</span></span>

[<span data-ttu-id="dd9bc-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="dd9bc-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="dd9bc-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="dd9bc-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="dd9bc-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="dd9bc-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="dd9bc-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="dd9bc-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="dd9bc-178">Remove-Service</span></span>](Remove-Service.md)
