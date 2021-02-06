---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 0e531b3cc072b7cc1efe0ef06fb741326bf3a72b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595611"
---
# <span data-ttu-id="78de2-102">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="78de2-102">Get-CimSession</span></span>

## <span data-ttu-id="78de2-103">摘要</span><span class="sxs-lookup"><span data-stu-id="78de2-103">SYNOPSIS</span></span>
<span data-ttu-id="78de2-104">获取当前会话中的 CIM 会话对象。</span><span class="sxs-lookup"><span data-stu-id="78de2-104">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="78de2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="78de2-105">SYNTAX</span></span>

### <span data-ttu-id="78de2-106">ComputerNameSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="78de2-106">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="78de2-107">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="78de2-107">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="78de2-108">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="78de2-108">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="78de2-109">NameSet</span><span class="sxs-lookup"><span data-stu-id="78de2-109">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="78de2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="78de2-110">DESCRIPTION</span></span>

<span data-ttu-id="78de2-111">默认情况下，该 cmdlet 将获取在当前 PowerShell 会话中创建的所有 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-111">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="78de2-112">你可以使用的参数 `Get-CimSession` 获取特定计算机的会话，也可以通过其名称或其他标识符来识别会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-112">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="78de2-113">`Get-CimSession` 不会获取在其他 PowerShell 会话中创建的或在其他计算机上创建的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-113">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="78de2-114">有关 CIM 会话的详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="78de2-114">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="78de2-115">示例</span><span class="sxs-lookup"><span data-stu-id="78de2-115">EXAMPLES</span></span>

### <span data-ttu-id="78de2-116">示例1：从当前 PowerShell 会话获取 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="78de2-116">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="78de2-117">此示例使用 [CimSession](New-CimSession.md)创建 cim 会话，然后使用获取 cim 会话 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="78de2-117">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="78de2-118">示例2：获取特定计算机的 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="78de2-118">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="78de2-119">此示例将获取连接到名为 **Server02** 的计算机的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-119">This example gets the CIM sessions that are connected to the computer named **Server02**.</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="78de2-120">示例3：获取 CIM 会话列表，然后设置该列表的格式</span><span class="sxs-lookup"><span data-stu-id="78de2-120">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="78de2-121">此示例获取当前 PowerShell 会话中的所有 CIM 会话，并显示仅包含 **ComputerName** 和 **InstanceID** 属性的表。</span><span class="sxs-lookup"><span data-stu-id="78de2-121">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="78de2-122">示例4：获取具有特定名称的所有 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="78de2-122">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="78de2-123">此示例获取名称以 **serv** 开头的所有 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-123">This example gets all CIM sessions that have names that begin with **serv**.</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="78de2-124">示例5：获取特定 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="78de2-124">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="78de2-125">此示例将获取 **Id** 为2的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-125">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="78de2-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="78de2-126">PARAMETERS</span></span>

### <span data-ttu-id="78de2-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="78de2-127">-ComputerName</span></span>

<span data-ttu-id="78de2-128">指定计算机的名称以获取连接到的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-128">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="78de2-129">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="78de2-129">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="78de2-130">-Id</span><span class="sxs-lookup"><span data-stu-id="78de2-130">-Id</span></span>

<span data-ttu-id="78de2-131">指定要获取的 CIM 会话的标识符。</span><span class="sxs-lookup"><span data-stu-id="78de2-131">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="78de2-132">对于多个 Id，请使用逗号分隔 Id 或使用范围运算符 (`..`) 来指定 id 的范围。</span><span class="sxs-lookup"><span data-stu-id="78de2-132">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="78de2-133">**Id** 是一个整数，用于在当前 PowerShell 会话中唯一标识 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-133">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="78de2-134">有关范围运算符的详细信息，请参阅 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="78de2-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="78de2-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="78de2-135">-InstanceId</span></span>

<span data-ttu-id="78de2-136">指定要获取的 CIM 会话的实例 Id。</span><span class="sxs-lookup"><span data-stu-id="78de2-136">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="78de2-137">**InstanceId** 是唯一标识 CIM 会话 (GUID) 的全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="78de2-137">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="78de2-138">即使在 PowerShell 中运行多个会话， **InstanceId** 也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="78de2-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="78de2-139">**Instanceid** 存储在表示 CIM 会话的对象的 **InstanceId** 属性中。</span><span class="sxs-lookup"><span data-stu-id="78de2-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="78de2-140">-Name</span><span class="sxs-lookup"><span data-stu-id="78de2-140">-Name</span></span>

<span data-ttu-id="78de2-141">获取一个或多个包含指定友好名称的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="78de2-141">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="78de2-142">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="78de2-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="78de2-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78de2-143">CommonParameters</span></span>
<span data-ttu-id="78de2-144">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="78de2-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78de2-145">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="78de2-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78de2-146">输入</span><span class="sxs-lookup"><span data-stu-id="78de2-146">INPUTS</span></span>

### <span data-ttu-id="78de2-147">无</span><span class="sxs-lookup"><span data-stu-id="78de2-147">None</span></span>

## <span data-ttu-id="78de2-148">输出</span><span class="sxs-lookup"><span data-stu-id="78de2-148">OUTPUTS</span></span>

### <span data-ttu-id="78de2-149">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="78de2-149">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="78de2-150">注释</span><span class="sxs-lookup"><span data-stu-id="78de2-150">NOTES</span></span>

## <span data-ttu-id="78de2-151">相关链接</span><span class="sxs-lookup"><span data-stu-id="78de2-151">RELATED LINKS</span></span>

[<span data-ttu-id="78de2-152">Format-Table</span><span class="sxs-lookup"><span data-stu-id="78de2-152">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="78de2-153">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="78de2-153">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="78de2-154">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="78de2-154">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="78de2-155">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="78de2-155">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

