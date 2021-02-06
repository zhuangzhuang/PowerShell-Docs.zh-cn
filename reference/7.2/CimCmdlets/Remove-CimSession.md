---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603579"
---
# <span data-ttu-id="387bf-102">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="387bf-102">Remove-CimSession</span></span>

## <span data-ttu-id="387bf-103">摘要</span><span class="sxs-lookup"><span data-stu-id="387bf-103">SYNOPSIS</span></span>
<span data-ttu-id="387bf-104">删除一个或多个 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="387bf-104">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="387bf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="387bf-105">SYNTAX</span></span>

### <span data-ttu-id="387bf-106">CimSessionSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="387bf-106">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387bf-107">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="387bf-107">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387bf-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="387bf-108">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387bf-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="387bf-109">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387bf-110">NameSet</span><span class="sxs-lookup"><span data-stu-id="387bf-110">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="387bf-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="387bf-111">DESCRIPTION</span></span>

<span data-ttu-id="387bf-112">`Remove-CimSession`Cmdlet 从本地 PowerShell 会话中删除一个或多个 CIM 会话对象。</span><span class="sxs-lookup"><span data-stu-id="387bf-112">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="387bf-113">示例</span><span class="sxs-lookup"><span data-stu-id="387bf-113">EXAMPLES</span></span>

### <span data-ttu-id="387bf-114">示例1：删除所有 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="387bf-114">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="387bf-115">此示例使用 [CimSession](Get-CimSession.md) cmdlet 检索本地计算机上的所有可用 CIM 会话，并使用将其删除 `Remove-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="387bf-115">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="387bf-116">示例2：删除特定 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="387bf-116">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="387bf-117">此示例将删除 **Id** 值为5的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="387bf-117">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="387bf-118">示例3：使用 WhatIf 参数显示要删除的 CIM 会话的列表</span><span class="sxs-lookup"><span data-stu-id="387bf-118">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="387bf-119">此示例使用常见的参数 **WhatIf** 来指定不应执行删除操作，但仅输出完成后会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="387bf-119">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="387bf-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="387bf-120">PARAMETERS</span></span>

### <span data-ttu-id="387bf-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="387bf-121">-CimSession</span></span>

<span data-ttu-id="387bf-122">指定要关闭的 CIM 会话的会话对象。</span><span class="sxs-lookup"><span data-stu-id="387bf-122">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="387bf-123">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 [`New-CimSession`](New-CimSession.md) 或 [`Get-CimSession`](Get-CimSession.md) cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="387bf-123">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="387bf-124">有关详细信息，请参阅 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="387bf-124">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="387bf-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="387bf-125">-ComputerName</span></span>

<span data-ttu-id="387bf-126">指定计算机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="387bf-126">Specifies an array of names of computers.</span></span> <span data-ttu-id="387bf-127">删除连接到指定计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="387bf-127">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="387bf-128">可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="387bf-128">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="387bf-129">-Id</span><span class="sxs-lookup"><span data-stu-id="387bf-129">-Id</span></span>

<span data-ttu-id="387bf-130">指定要删除的 CIM 会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="387bf-130">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="387bf-131">指定一个或多个 Id （以逗号分隔），或使用范围运算符 (`..`) 来指定 id 的范围。</span><span class="sxs-lookup"><span data-stu-id="387bf-131">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="387bf-132">**Id** 是一个整数，用于在当前 PowerShell 会话中唯一标识 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="387bf-132">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="387bf-133">有关范围运算符的详细信息，请参阅 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="387bf-133">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="387bf-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="387bf-134">-InstanceId</span></span>

<span data-ttu-id="387bf-135">指定要删除的 CIM 会话的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="387bf-135">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="387bf-136">**InstanceId** 是唯一标识 CIM 会话 (GUID) 的全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="387bf-136">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="387bf-137">即使在 PowerShell 中运行多个会话， **InstanceId** 也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="387bf-137">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="387bf-138">**Instanceid** 存储在表示 CIM 会话的对象的 **InstanceId** 属性中。</span><span class="sxs-lookup"><span data-stu-id="387bf-138">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="387bf-139">-Name</span><span class="sxs-lookup"><span data-stu-id="387bf-139">-Name</span></span>

<span data-ttu-id="387bf-140">指定要删除的 CIM 会话的友好名称。</span><span class="sxs-lookup"><span data-stu-id="387bf-140">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="387bf-141">可以将通配符用于此参数。</span><span class="sxs-lookup"><span data-stu-id="387bf-141">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="387bf-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="387bf-142">-Confirm</span></span>

<span data-ttu-id="387bf-143">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="387bf-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="387bf-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="387bf-144">-WhatIf</span></span>

<span data-ttu-id="387bf-145">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="387bf-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="387bf-146">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="387bf-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="387bf-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="387bf-147">CommonParameters</span></span>

<span data-ttu-id="387bf-148">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="387bf-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="387bf-149">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="387bf-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="387bf-150">输入</span><span class="sxs-lookup"><span data-stu-id="387bf-150">INPUTS</span></span>

### <span data-ttu-id="387bf-151">无</span><span class="sxs-lookup"><span data-stu-id="387bf-151">None</span></span>

<span data-ttu-id="387bf-152">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="387bf-152">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="387bf-153">输出</span><span class="sxs-lookup"><span data-stu-id="387bf-153">OUTPUTS</span></span>

### <span data-ttu-id="387bf-154">System.Object</span><span class="sxs-lookup"><span data-stu-id="387bf-154">System.Object</span></span>

<span data-ttu-id="387bf-155">此 cmdlet 将返回包含 CIM 会话信息的对象。</span><span class="sxs-lookup"><span data-stu-id="387bf-155">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="387bf-156">注释</span><span class="sxs-lookup"><span data-stu-id="387bf-156">NOTES</span></span>

## <span data-ttu-id="387bf-157">相关链接</span><span class="sxs-lookup"><span data-stu-id="387bf-157">RELATED LINKS</span></span>

[<span data-ttu-id="387bf-158">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="387bf-158">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="387bf-159">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="387bf-159">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="387bf-160">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="387bf-160">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

