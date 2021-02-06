---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: 5a23aaa59eb10ff35ecefb7365d3294cdb06f781
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597231"
---
# <span data-ttu-id="a1729-102">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a1729-102">Remove-CimInstance</span></span>

## <span data-ttu-id="a1729-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a1729-103">SYNOPSIS</span></span>
<span data-ttu-id="a1729-104">从计算机中删除 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="a1729-104">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="a1729-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1729-105">SYNTAX</span></span>

### <span data-ttu-id="a1729-106">CimInstanceComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="a1729-106">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a1729-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="a1729-107">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a1729-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="a1729-108">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a1729-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="a1729-109">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a1729-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a1729-110">DESCRIPTION</span></span>

<span data-ttu-id="a1729-111">此 cmdlet 将从 CIM 服务器中删除 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="a1729-111">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="a1729-112">您可以使用 cmdlet 检索到的 CIM 实例对象或指定查询来指定要删除的 CIM 实例 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a1729-112">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="a1729-113">如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="a1729-113">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="a1729-114">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。</span><span class="sxs-lookup"><span data-stu-id="a1729-114">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="a1729-115">如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="a1729-115">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="a1729-116">示例</span><span class="sxs-lookup"><span data-stu-id="a1729-116">EXAMPLES</span></span>

### <span data-ttu-id="a1729-117">示例1：删除 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="a1729-117">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="a1729-118">此示例使用 **Query** 参数从名为 **Win32_Environment** 的类中删除 CIM 实例，该类以字符串 **testvar** 开头。</span><span class="sxs-lookup"><span data-stu-id="a1729-118">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="a1729-119">示例2：使用 CIM 实例对象删除 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="a1729-119">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="a1729-120">此示例检索按 **查询** 参数筛选的 CIM 实例对象，并 `$var` 使用 cmdlet 将它们存储在名为的变量中 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a1729-120">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="a1729-121">然后将变量的内容传递给 `Remove-CimInstance` cmdlet，后者将删除 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="a1729-121">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="a1729-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1729-122">PARAMETERS</span></span>

### <span data-ttu-id="a1729-123">-CimSession</span><span class="sxs-lookup"><span data-stu-id="a1729-123">-CimSession</span></span>

<span data-ttu-id="a1729-124">使用指定的 CIM 会话运行该命令。</span><span class="sxs-lookup"><span data-stu-id="a1729-124">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="a1729-125">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="a1729-125">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="a1729-126">有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="a1729-126">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="a1729-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a1729-127">-ComputerName</span></span>

<span data-ttu-id="a1729-128">指定要在其上运行 CIM 操作的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="a1729-128">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="a1729-129">可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="a1729-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="a1729-130">如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="a1729-130">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="a1729-131">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="a1729-131">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="a1729-132">如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="a1729-132">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="a1729-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a1729-133">-InputObject</span></span>

<span data-ttu-id="a1729-134">指定要从 CIM 服务器中删除的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="a1729-134">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="a1729-135">传递给 cmdlet 的对象未更改，只会删除 CIM 服务器中的实例。</span><span class="sxs-lookup"><span data-stu-id="a1729-135">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a1729-136">-Namespace</span><span class="sxs-lookup"><span data-stu-id="a1729-136">-Namespace</span></span>

<span data-ttu-id="a1729-137">指定 CIM 操作的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a1729-137">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="a1729-138">默认命名空间为 **root/cimv2**。</span><span class="sxs-lookup"><span data-stu-id="a1729-138">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="a1729-139">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="a1729-139">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a1729-140">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a1729-140">-OperationTimeoutSec</span></span>

<span data-ttu-id="a1729-141">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="a1729-141">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="a1729-142">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="a1729-142">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="a1729-143">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="a1729-143">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="a1729-144">-Query</span><span class="sxs-lookup"><span data-stu-id="a1729-144">-Query</span></span>

<span data-ttu-id="a1729-145">指定要在 CIM 服务器上运行的查询。</span><span class="sxs-lookup"><span data-stu-id="a1729-145">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="a1729-146">您可以使用 **QueryDialect** 参数指定查询方言。</span><span class="sxs-lookup"><span data-stu-id="a1729-146">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="a1729-147">如果指定的值包含双引号 (`"`) 、单引号 (`'`) 或反斜杠 (`\`) ，则必须使用反斜杠 () 字符作为前缀，来对这些字符进行转义 `\` 。</span><span class="sxs-lookup"><span data-stu-id="a1729-147">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="a1729-148">如果指定的值使用 WQL LIKE 运算符，则必须通过将以下字符括在方括号中来对其进行转义 (`[]`) ：百分比 (`%`) 、下划线 (`_`) 或左方括号 (`[`) 。</span><span class="sxs-lookup"><span data-stu-id="a1729-148">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a1729-149">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="a1729-149">-QueryDialect</span></span>

<span data-ttu-id="a1729-150">指定用于查询参数的查询语言。</span><span class="sxs-lookup"><span data-stu-id="a1729-150">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="a1729-151">此参数的可接受值为： **WQL** 或 **CQL**。</span><span class="sxs-lookup"><span data-stu-id="a1729-151">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="a1729-152">默认值为 **WQL**。</span><span class="sxs-lookup"><span data-stu-id="a1729-152">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a1729-153">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="a1729-153">-ResourceUri</span></span>

<span data-ttu-id="a1729-154">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="a1729-154">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="a1729-155">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="a1729-155">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a1729-156">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="a1729-156">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="a1729-157">例如：</span><span class="sxs-lookup"><span data-stu-id="a1729-157">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="a1729-158">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="a1729-158">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="a1729-159">ResourceURI 只能与使用 WSMan 协议创建的 CIM 会话一起使用，也可以在指定 ComputerName 参数时使用，后者使用 WSMan 创建 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="a1729-159">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="a1729-160">如果在不指定 ComputerName 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则会出现错误，因为 DCOM 协议不支持 ResourceURI 参数。</span><span class="sxs-lookup"><span data-stu-id="a1729-160">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="a1729-161">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="a1729-161">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="a1729-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a1729-162">-Confirm</span></span>

<span data-ttu-id="a1729-163">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="a1729-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a1729-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a1729-164">-WhatIf</span></span>

<span data-ttu-id="a1729-165">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="a1729-165">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a1729-166">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="a1729-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a1729-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1729-167">CommonParameters</span></span>

<span data-ttu-id="a1729-168">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a1729-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1729-169">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a1729-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1729-170">输入</span><span class="sxs-lookup"><span data-stu-id="a1729-170">INPUTS</span></span>

### <span data-ttu-id="a1729-171">无</span><span class="sxs-lookup"><span data-stu-id="a1729-171">None</span></span>

<span data-ttu-id="a1729-172">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="a1729-172">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="a1729-173">输出</span><span class="sxs-lookup"><span data-stu-id="a1729-173">OUTPUTS</span></span>

### <span data-ttu-id="a1729-174">无</span><span class="sxs-lookup"><span data-stu-id="a1729-174">None</span></span>

<span data-ttu-id="a1729-175">此 cmdlet 不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="a1729-175">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="a1729-176">注释</span><span class="sxs-lookup"><span data-stu-id="a1729-176">NOTES</span></span>

## <span data-ttu-id="a1729-177">相关链接</span><span class="sxs-lookup"><span data-stu-id="a1729-177">RELATED LINKS</span></span>

[<span data-ttu-id="a1729-178">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a1729-178">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="a1729-179">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a1729-179">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="a1729-180">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a1729-180">Set-CimInstance</span></span>](Set-CimInstance.md)

