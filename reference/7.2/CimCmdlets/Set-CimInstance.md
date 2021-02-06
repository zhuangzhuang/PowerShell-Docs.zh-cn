---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595606"
---
# <span data-ttu-id="93908-102">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-102">Set-CimInstance</span></span>

## <span data-ttu-id="93908-103">摘要</span><span class="sxs-lookup"><span data-stu-id="93908-103">SYNOPSIS</span></span>
<span data-ttu-id="93908-104">通过调用 CIM 类的 ModifyInstance 方法，修改 CIM 服务器上的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="93908-104">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="93908-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93908-105">SYNTAX</span></span>

### <span data-ttu-id="93908-106">CimInstanceComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="93908-106">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="93908-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="93908-107">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="93908-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="93908-108">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="93908-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="93908-109">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="93908-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="93908-110">DESCRIPTION</span></span>

<span data-ttu-id="93908-111">此 cmdlet 修改 CIM 服务器上的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="93908-111">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="93908-112">如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="93908-112">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="93908-113">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。</span><span class="sxs-lookup"><span data-stu-id="93908-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="93908-114">如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="93908-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="93908-115">如果指定了 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="93908-115">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="93908-116">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将使用输入对象中的 CIM 会话或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="93908-116">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="93908-117">如果指定了 **ComputerName** 参数或 **CimSession** 参数，则此 cmdlet 将使用 **CimSession** 参数值或 **ComputerName** 参数值。</span><span class="sxs-lookup"><span data-stu-id="93908-117">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="93908-118">这并不是很常见。</span><span class="sxs-lookup"><span data-stu-id="93908-118">This is not very common.</span></span>

## <span data-ttu-id="93908-119">示例</span><span class="sxs-lookup"><span data-stu-id="93908-119">EXAMPLES</span></span>

### <span data-ttu-id="93908-120">示例1：设置 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="93908-120">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="93908-121">此示例使用 **Query** 参数将 **VariableValue** 属性的值设置为 **abcd** 。</span><span class="sxs-lookup"><span data-stu-id="93908-121">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="93908-122">您可以 (WQL) 查询中修改匹配 Windows Management Instrumentation 查询语言的实例。</span><span class="sxs-lookup"><span data-stu-id="93908-122">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="93908-123">示例2：使用管道设置 CIM 实例属性</span><span class="sxs-lookup"><span data-stu-id="93908-123">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="93908-124">此示例使用 cmdlet 检索由 **查询** 参数筛选的 CIM 实例对象 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="93908-124">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="93908-125">`Set-CimInstance`Cmdlet 将 **VariableValue** 属性的值修改为 **abcd**。</span><span class="sxs-lookup"><span data-stu-id="93908-125">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="93908-126">示例3：使用输入对象设置 CIM 实例属性</span><span class="sxs-lookup"><span data-stu-id="93908-126">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="93908-127">此示例使用在中将查询参数筛选的 CIM 实例对象检索到变量 `$x` `Get-CimInstance` ，然后将该变量的内容传递给 `Set-CimInstance` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93908-127">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="93908-128">`Set-CimInstance` 然后将 **VariableValue** 属性修改为 **somevalue**。</span><span class="sxs-lookup"><span data-stu-id="93908-128">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="93908-129">由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="93908-129">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="93908-130">示例4：设置 CIM 实例属性</span><span class="sxs-lookup"><span data-stu-id="93908-130">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="93908-131">此示例使用 cmdlet 将 **查询** 参数中指定的 CIM 实例对象检索到变量中 `$x` `Get-CimInstance` ，并更改要更改的对象的 **VariableValue** 属性值。</span><span class="sxs-lookup"><span data-stu-id="93908-131">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="93908-132">然后，使用 cmdlet 保存 CIM 实例对象 `Set-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="93908-132">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="93908-133">由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="93908-133">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="93908-134">示例5：显示要使用 WhatIf 修改的 CIM 实例列表</span><span class="sxs-lookup"><span data-stu-id="93908-134">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="93908-135">此示例使用通用参数 **WhatIf** 来指定不应完成修改，但仅输出在完成后会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="93908-135">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="93908-136">示例6：在用户确认后设置 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="93908-136">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="93908-137">此示例使用 common 参数 **Confirm** 来指定仅应在用户确认后进行修改。</span><span class="sxs-lookup"><span data-stu-id="93908-137">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="93908-138">示例7：设置创建的 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="93908-138">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="93908-139">此示例使用 cmdlet 创建具有指定属性的 CIM 实例 `New-CimInstance` ，并将其内容检索到变量中 `$x` 。</span><span class="sxs-lookup"><span data-stu-id="93908-139">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="93908-140">然后，将变量传递给 `Set-CimInstance` cmdlet，这会将 **VariableValue** 属性的值修改为 **somevalue**。</span><span class="sxs-lookup"><span data-stu-id="93908-140">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="93908-141">由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="93908-141">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="93908-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93908-142">PARAMETERS</span></span>

### <span data-ttu-id="93908-143">-CimSession</span><span class="sxs-lookup"><span data-stu-id="93908-143">-CimSession</span></span>

<span data-ttu-id="93908-144">在远程计算机上运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93908-144">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="93908-145">输入计算机名或会话对象，例如 `New-CimSession` 或 cmdlet 的输出 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="93908-145">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="93908-146">-ComputerName</span></span>

<span data-ttu-id="93908-147">指定要在其上运行 CIM 操作的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="93908-147">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="93908-148">可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="93908-148">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="93908-149">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="93908-149">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="93908-150">如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="93908-150">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="93908-151">如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="93908-151">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93908-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="93908-152">-InputObject</span></span>

<span data-ttu-id="93908-153">指定要用作输入的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="93908-153">Specifies a CIM instance object to use as input.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-154">-Namespace</span><span class="sxs-lookup"><span data-stu-id="93908-154">-Namespace</span></span>

<span data-ttu-id="93908-155">指定 CIM 操作的命名空间。</span><span class="sxs-lookup"><span data-stu-id="93908-155">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="93908-156">默认命名空间为 root/cimv2。</span><span class="sxs-lookup"><span data-stu-id="93908-156">The default namespace is root/cimv2.</span></span> <span data-ttu-id="93908-157">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="93908-157">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-158">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="93908-158">-OperationTimeoutSec</span></span>

<span data-ttu-id="93908-159">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="93908-159">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="93908-160">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="93908-160">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="93908-161">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="93908-161">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93908-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="93908-162">-PassThru</span></span>

<span data-ttu-id="93908-163">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="93908-163">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="93908-164">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="93908-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="93908-165">-Property</span><span class="sxs-lookup"><span data-stu-id="93908-165">-Property</span></span>

<span data-ttu-id="93908-166">使用) 的名称-值对将 CIM 实例的属性指定为哈希表 (。</span><span class="sxs-lookup"><span data-stu-id="93908-166">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="93908-167">仅更改使用此参数指定的属性。</span><span class="sxs-lookup"><span data-stu-id="93908-167">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="93908-168">CIM 实例的其他属性不会更改。</span><span class="sxs-lookup"><span data-stu-id="93908-168">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-169">-Query</span><span class="sxs-lookup"><span data-stu-id="93908-169">-Query</span></span>

<span data-ttu-id="93908-170">指定要在 CIM 服务器上运行的查询，以检索要在其上运行 cmdlet 的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="93908-170">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="93908-171">您可以使用 QueryDialect 参数指定查询方言。</span><span class="sxs-lookup"><span data-stu-id="93908-171">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="93908-172">如果指定的值包含双引号 (`"`) 、单引号 (`'`) 或反斜杠 (`\`) ，则必须使用反斜杠 () 字符作为前缀，来对这些字符进行转义 `\` 。</span><span class="sxs-lookup"><span data-stu-id="93908-172">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="93908-173">如果指定的值使用 WQL **LIKE** 运算符，则必须通过将以下字符括在方括号中来对其进行转义 (`[]`) ：百分比 (`%`) 、下划线 (`_`) 或左方括号 (`[`) 。</span><span class="sxs-lookup"><span data-stu-id="93908-173">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-174">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="93908-174">-QueryDialect</span></span>

<span data-ttu-id="93908-175">指定用于查询参数的查询语言。</span><span class="sxs-lookup"><span data-stu-id="93908-175">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="93908-176">此参数的可接受值为： **WQL** 或 **CQL**。</span><span class="sxs-lookup"><span data-stu-id="93908-176">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="93908-177">默认值为 **WQL**。</span><span class="sxs-lookup"><span data-stu-id="93908-177">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-178">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="93908-178">-ResourceUri</span></span>

<span data-ttu-id="93908-179">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="93908-179">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="93908-180">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="93908-180">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="93908-181">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="93908-181">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="93908-182">例如：</span><span class="sxs-lookup"><span data-stu-id="93908-182">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="93908-183">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="93908-183">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="93908-184">ResourceURI 只能与使用 WSMan 协议创建的 CIM 会话一起使用，也可以在指定 ComputerName 参数时使用，后者使用 WSMan 创建 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="93908-184">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="93908-185">如果在不指定 ComputerName 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则将收到错误，因为 DCOM 协议不支持 ResourceURI 参数。</span><span class="sxs-lookup"><span data-stu-id="93908-185">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="93908-186">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="93908-186">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93908-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93908-187">-Confirm</span></span>

<span data-ttu-id="93908-188">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="93908-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="93908-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93908-189">-WhatIf</span></span>

<span data-ttu-id="93908-190">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="93908-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="93908-191">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="93908-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="93908-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93908-192">CommonParameters</span></span>

<span data-ttu-id="93908-193">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="93908-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93908-194">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="93908-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="93908-195">输入</span><span class="sxs-lookup"><span data-stu-id="93908-195">INPUTS</span></span>

### <span data-ttu-id="93908-196">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-196">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="93908-197">输出</span><span class="sxs-lookup"><span data-stu-id="93908-197">OUTPUTS</span></span>

### <span data-ttu-id="93908-198">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-198">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="93908-199">当指定 **Passthru** 参数时，此 cmdlet 将返回已修改的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="93908-199">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="93908-200">注释</span><span class="sxs-lookup"><span data-stu-id="93908-200">NOTES</span></span>

## <span data-ttu-id="93908-201">相关链接</span><span class="sxs-lookup"><span data-stu-id="93908-201">RELATED LINKS</span></span>

[<span data-ttu-id="93908-202">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-202">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="93908-203">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-203">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="93908-204">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="93908-204">Remove-CimInstance</span></span>](remove-ciminstance.md)

