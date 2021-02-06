---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 645efc2d271a3b95801c8d0d264ee33ed788f15f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598886"
---
# <span data-ttu-id="f028d-102">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-102">Remove-Service</span></span>

## <span data-ttu-id="f028d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f028d-103">SYNOPSIS</span></span>
<span data-ttu-id="f028d-104">删除 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="f028d-104">Removes a Windows service.</span></span>

## <span data-ttu-id="f028d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f028d-105">SYNTAX</span></span>

### <span data-ttu-id="f028d-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="f028d-106">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f028d-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="f028d-107">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f028d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f028d-108">DESCRIPTION</span></span>

<span data-ttu-id="f028d-109">`Remove-Service`Cmdlet 将在注册表和服务数据库中删除 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="f028d-109">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="f028d-110">`Remove-Service`Cmdlet 是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f028d-110">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="f028d-111">示例</span><span class="sxs-lookup"><span data-stu-id="f028d-111">EXAMPLES</span></span>

### <span data-ttu-id="f028d-112">示例1：删除服务</span><span class="sxs-lookup"><span data-stu-id="f028d-112">Example 1: Remove a service</span></span>

<span data-ttu-id="f028d-113">这会删除名为 TestService 的服务。</span><span class="sxs-lookup"><span data-stu-id="f028d-113">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="f028d-114">示例2：使用显示名称删除服务</span><span class="sxs-lookup"><span data-stu-id="f028d-114">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="f028d-115">此示例删除名为 TestService 的服务。</span><span class="sxs-lookup"><span data-stu-id="f028d-115">This example removes a service named TestService.</span></span> <span data-ttu-id="f028d-116">该命令使用 `Get-Service` 来获取使用显示名称表示 TestService 服务的对象。</span><span class="sxs-lookup"><span data-stu-id="f028d-116">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="f028d-117">管道运算符 (将 `|` 对象) 管道 `Remove-Service` ，这将删除服务。</span><span class="sxs-lookup"><span data-stu-id="f028d-117">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="f028d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f028d-118">PARAMETERS</span></span>

### <span data-ttu-id="f028d-119">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f028d-119">-InputObject</span></span>

<span data-ttu-id="f028d-120">指定表示要删除的服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="f028d-120">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="f028d-121">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="f028d-121">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f028d-122">-Name</span><span class="sxs-lookup"><span data-stu-id="f028d-122">-Name</span></span>

<span data-ttu-id="f028d-123">指定要删除的服务的服务名称。</span><span class="sxs-lookup"><span data-stu-id="f028d-123">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="f028d-124">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="f028d-124">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f028d-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f028d-125">-Confirm</span></span>

<span data-ttu-id="f028d-126">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="f028d-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f028d-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f028d-127">-WhatIf</span></span>

<span data-ttu-id="f028d-128">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="f028d-128">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f028d-129">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="f028d-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f028d-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f028d-130">CommonParameters</span></span>

<span data-ttu-id="f028d-131">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f028d-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f028d-132">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f028d-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f028d-133">输入</span><span class="sxs-lookup"><span data-stu-id="f028d-133">INPUTS</span></span>

### <span data-ttu-id="f028d-134">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="f028d-134">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="f028d-135">可以通过管道将服务对象或包含服务名称的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f028d-135">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="f028d-136">输出</span><span class="sxs-lookup"><span data-stu-id="f028d-136">OUTPUTS</span></span>

### <span data-ttu-id="f028d-137">无</span><span class="sxs-lookup"><span data-stu-id="f028d-137">None</span></span>

<span data-ttu-id="f028d-138">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="f028d-138">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f028d-139">注释</span><span class="sxs-lookup"><span data-stu-id="f028d-139">NOTES</span></span>

<span data-ttu-id="f028d-140">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="f028d-140">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="f028d-141">若要运行此 cmdlet，请使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f028d-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="f028d-142">相关链接</span><span class="sxs-lookup"><span data-stu-id="f028d-142">RELATED LINKS</span></span>

[<span data-ttu-id="f028d-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="f028d-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="f028d-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="f028d-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="f028d-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="f028d-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="f028d-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="f028d-149">Suspend-Service</span></span>](Suspend-Service.md)
