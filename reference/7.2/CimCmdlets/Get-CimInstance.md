---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 0e4a148601f3ef2212f9c97128c54258906106d7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597659"
---
# <span data-ttu-id="bee7b-102">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bee7b-102">Get-CimInstance</span></span>

## <span data-ttu-id="bee7b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="bee7b-103">SYNOPSIS</span></span>
<span data-ttu-id="bee7b-104">从 CIM 服务器获取类的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-104">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="bee7b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bee7b-105">SYNTAX</span></span>

### <span data-ttu-id="bee7b-106">ClassNameComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="bee7b-106">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bee7b-107">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-107">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="bee7b-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-108">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="bee7b-109">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-109">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bee7b-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-110">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="bee7b-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-111">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="bee7b-112">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-112">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="bee7b-113">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="bee7b-113">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="bee7b-114">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bee7b-114">DESCRIPTION</span></span>

<span data-ttu-id="bee7b-115">`Get-CimInstance`Cmdlet 从 cim 服务器获取类的 cim 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-115">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="bee7b-116">可以为此 cmdlet 指定类名或查询。</span><span class="sxs-lookup"><span data-stu-id="bee7b-116">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="bee7b-117">此 cmdlet 将返回一个或多个 CIM 实例对象，这些对象表示 CIM 服务器上存在的 CIM 实例的快照。</span><span class="sxs-lookup"><span data-stu-id="bee7b-117">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="bee7b-118">如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="bee7b-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="bee7b-119">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。</span><span class="sxs-lookup"><span data-stu-id="bee7b-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="bee7b-120">如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="bee7b-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="bee7b-121">如果指定了 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="bee7b-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="bee7b-122">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将使用输入对象中的 CIM 会话或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="bee7b-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="bee7b-123">如果指定了 **ComputerName** 参数或 **CimSession** 参数，则此 cmdlet 将使用 CimSession 参数值或 **ComputerName** 参数值。</span><span class="sxs-lookup"><span data-stu-id="bee7b-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="bee7b-124">示例</span><span class="sxs-lookup"><span data-stu-id="bee7b-124">EXAMPLES</span></span>

### <span data-ttu-id="bee7b-125">示例1：获取指定类的 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-125">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="bee7b-126">此示例将检索名为 **Win32_Process** 的类的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-126">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="bee7b-127">示例2：从 WMI 服务器获取命名空间列表</span><span class="sxs-lookup"><span data-stu-id="bee7b-127">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="bee7b-128">此示例在 WMI 服务器上的 **根** 命名空间下检索命名空间的列表。</span><span class="sxs-lookup"><span data-stu-id="bee7b-128">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="bee7b-129">示例3：获取使用查询筛选的类的实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-129">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="bee7b-130">此示例使用 **查询** 参数指定的查询，检索以名为 **Win32_Process** 的类的字母 **P** 开头的所有 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-130">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="bee7b-131">示例4：获取通过使用类名称和筛选器表达式筛选的类的实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-131">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="bee7b-132">此示例使用 Filter 参数检索以名为 **Win32_Process** 的类的字母 **P** 开头的所有 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-132">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="bee7b-133">示例5：获取仅填充了密钥属性的 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-133">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="bee7b-134">此示例在内存中为名为 **Win32_Process** 的类创建一个名为的新 CIM 实例，该实例具有键属性 `@{ "Handle"=0 }` ，并将其存储在名为的变量中 `$x` 。</span><span class="sxs-lookup"><span data-stu-id="bee7b-134">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="bee7b-135">变量作为 CIM 实例传递到 `Get-CimInstance` cmdlet 以获取特定的实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-135">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="bee7b-136">示例6：检索并重复使用 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-136">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="bee7b-137">此示例将获取名为 **Win32_Process** 的类的 CIM 实例，并将其存储在变量 `$x` 和中 `$y` 。</span><span class="sxs-lookup"><span data-stu-id="bee7b-137">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="bee7b-138">然后，将变量设置为 `$x` 仅包含 **Name** 和 **KernelModeTime** 属性的表，并将该表设置为 "自动 **调整大小**"。</span><span class="sxs-lookup"><span data-stu-id="bee7b-138">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="bee7b-139">示例7：从远程计算机获取 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-139">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="bee7b-140">此示例从名为 **Server01** 和 **Server02** 的远程计算机中检索名为 **Win32_ComputerSystem** 的类的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-140">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="bee7b-141">示例8：仅获取密钥属性，而不是所有属性</span><span class="sxs-lookup"><span data-stu-id="bee7b-141">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="bee7b-142">此示例仅检索密钥属性，这会减少对象和网络流量的大小。</span><span class="sxs-lookup"><span data-stu-id="bee7b-142">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="bee7b-143">示例9：仅获取属性的子集，而不是所有属性</span><span class="sxs-lookup"><span data-stu-id="bee7b-143">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="bee7b-144">此示例仅检索部分属性，这会减少对象和网络流量的大小。</span><span class="sxs-lookup"><span data-stu-id="bee7b-144">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="bee7b-145">使用 **属性** 参数检索到的实例可用于执行其他 CIM 操作，例如 `Set-CimInstance` 或 `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="bee7b-145">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="bee7b-146">示例10：使用 CIM 会话获取 CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-146">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="bee7b-147">此示例使用 cmdlet 在名为 **Server01** 和 **Server02** 的计算机上创建 CIM 会话 `New-CimSession` ，并将会话信息存储在名为的变量中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="bee7b-147">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="bee7b-148">然后，使用 CimSession 参数将变量的内容传递到 `Get-CimInstance` ， 以获取名为 **WIN32_COMPUTERSYSTEM** 的类的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-148">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="bee7b-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bee7b-149">PARAMETERS</span></span>

### <span data-ttu-id="bee7b-150">-CimSession</span><span class="sxs-lookup"><span data-stu-id="bee7b-150">-CimSession</span></span>

<span data-ttu-id="bee7b-151">指定要用于此 cmdlet 的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="bee7b-151">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="bee7b-152">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="bee7b-152">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="bee7b-153">有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="bee7b-153">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-154">-ClassName</span><span class="sxs-lookup"><span data-stu-id="bee7b-154">-ClassName</span></span>

<span data-ttu-id="bee7b-155">指定要为其检索 CIM 实例的 CIM 类的名称。</span><span class="sxs-lookup"><span data-stu-id="bee7b-155">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="bee7b-156">您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。</span><span class="sxs-lookup"><span data-stu-id="bee7b-156">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-157">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bee7b-157">-ComputerName</span></span>

<span data-ttu-id="bee7b-158">指定要在其上运行 CIM 操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="bee7b-158">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="bee7b-159">可以指定完全限定的域名 (FQDN) 、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bee7b-159">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="bee7b-160">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="bee7b-160">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="bee7b-161">如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="bee7b-161">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="bee7b-162">如果在同一台计算机上执行多个操作，请使用 CIM 会话进行连接以获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="bee7b-162">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="bee7b-163">-Filter</span></span>

<span data-ttu-id="bee7b-164">指定要用作筛选器的 where 子句。</span><span class="sxs-lookup"><span data-stu-id="bee7b-164">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="bee7b-165">指定 **WQL** 或 **CQL** 查询语言中的子句。</span><span class="sxs-lookup"><span data-stu-id="bee7b-165">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="bee7b-166">不要 `WHERE` 在参数的值中包含关键字。</span><span class="sxs-lookup"><span data-stu-id="bee7b-166">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bee7b-167">-InputObject</span></span>

<span data-ttu-id="bee7b-168">指定要用作输入的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="bee7b-168">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="bee7b-169">如果已在使用 CIM 实例对象，则可以使用此参数传递 CIM 实例对象，以便从 CIM 服务器获取最新的快照。</span><span class="sxs-lookup"><span data-stu-id="bee7b-169">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="bee7b-170">将 CIM 实例对象作为输入传递时，将 `Get-CimInstance` 从服务器使用 GET CIM 操作（而不是枚举或查询操作）返回对象。</span><span class="sxs-lookup"><span data-stu-id="bee7b-170">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="bee7b-171">使用 get CIM 操作比检索所有实例并筛选它们更有效。</span><span class="sxs-lookup"><span data-stu-id="bee7b-171">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="bee7b-172">如果 CIM 类未实现 get 操作，则指定 **InputObject** 参数将返回错误。</span><span class="sxs-lookup"><span data-stu-id="bee7b-172">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-173">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="bee7b-173">-KeyOnly</span></span>

<span data-ttu-id="bee7b-174">指示只返回填充了键属性的对象。</span><span class="sxs-lookup"><span data-stu-id="bee7b-174">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="bee7b-175">指定 **KeyOnly** 参数将减少通过网络传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="bee7b-175">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="bee7b-176">使用 **KeyOnly** 参数可仅返回对象的一小部分，该对象可用于其他操作，例如 `Set-CimInstance` 或 `Get-CimAssociatedInstance` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bee7b-176">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-177">-Namespace</span><span class="sxs-lookup"><span data-stu-id="bee7b-177">-Namespace</span></span>

<span data-ttu-id="bee7b-178">指定 CIM 类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="bee7b-178">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="bee7b-179">默认命名空间为 **root/cimv2**。</span><span class="sxs-lookup"><span data-stu-id="bee7b-179">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="bee7b-180">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="bee7b-180">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-181">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="bee7b-181">-OperationTimeoutSec</span></span>

<span data-ttu-id="bee7b-182">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="bee7b-182">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="bee7b-183">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="bee7b-183">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="bee7b-184">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="bee7b-184">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="bee7b-185">-Property</span><span class="sxs-lookup"><span data-stu-id="bee7b-185">-Property</span></span>

<span data-ttu-id="bee7b-186">指定要检索的实例属性集。</span><span class="sxs-lookup"><span data-stu-id="bee7b-186">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="bee7b-187">如果需要减小返回对象的大小（在内存中或网络上），请使用此参数。</span><span class="sxs-lookup"><span data-stu-id="bee7b-187">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="bee7b-188">返回的对象还包含键属性，即使您未使用 **Property** 参数列出它们也是如此。</span><span class="sxs-lookup"><span data-stu-id="bee7b-188">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="bee7b-189">类的其他属性存在，但未填充它们。</span><span class="sxs-lookup"><span data-stu-id="bee7b-189">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-190">-Query</span><span class="sxs-lookup"><span data-stu-id="bee7b-190">-Query</span></span>

<span data-ttu-id="bee7b-191">指定要在 CIM 服务器上运行的查询。</span><span class="sxs-lookup"><span data-stu-id="bee7b-191">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="bee7b-192">如果指定的值包含双引号 `"` 、单引号 `'` 或反斜杠 `\` ，则必须通过在它们前面加上反斜杠字符来对这些字符进行转义。</span><span class="sxs-lookup"><span data-stu-id="bee7b-192">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="bee7b-193">如果指定的值使用 WQL **LIKE** 运算符，则必须通过将以下字符括在方括号中来对其进行转义 `[]` ：百分比 `%` 、下划线 `_` 或左方括号 `[` 。</span><span class="sxs-lookup"><span data-stu-id="bee7b-193">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="bee7b-194">不能使用元数据查询来检索类或事件查询的列表。</span><span class="sxs-lookup"><span data-stu-id="bee7b-194">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="bee7b-195">若要检索类的列表，请使用 `Get-CimClass` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bee7b-195">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="bee7b-196">若要检索事件查询，请使用 `Register-CimIndicationEvent` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bee7b-196">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="bee7b-197">您可以使用 **QueryDialect** 参数指定查询方言。</span><span class="sxs-lookup"><span data-stu-id="bee7b-197">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-198">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="bee7b-198">-QueryDialect</span></span>

<span data-ttu-id="bee7b-199">指定用于查询参数的查询语言。</span><span class="sxs-lookup"><span data-stu-id="bee7b-199">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="bee7b-200">此参数的可接受值为： **WQL** 或 **CQL**。</span><span class="sxs-lookup"><span data-stu-id="bee7b-200">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="bee7b-201">默认值为 **WQL**。</span><span class="sxs-lookup"><span data-stu-id="bee7b-201">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-202">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="bee7b-202">-ResourceUri</span></span>

<span data-ttu-id="bee7b-203">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="bee7b-203">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="bee7b-204">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="bee7b-204">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="bee7b-205">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="bee7b-205">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="bee7b-206">例如：</span><span class="sxs-lookup"><span data-stu-id="bee7b-206">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="bee7b-207">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="bee7b-207">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="bee7b-208">**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。</span><span class="sxs-lookup"><span data-stu-id="bee7b-208">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="bee7b-209">如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则将收到错误，因为 DCOM 协议不支持 **ResourceURI** 参数。</span><span class="sxs-lookup"><span data-stu-id="bee7b-209">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="bee7b-210">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="bee7b-210">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-211">-浅</span><span class="sxs-lookup"><span data-stu-id="bee7b-211">-Shallow</span></span>

<span data-ttu-id="bee7b-212">指示返回类的实例，但不包含任何子类的实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-212">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="bee7b-213">默认情况下，该 cmdlet 将返回类及其子类的实例。</span><span class="sxs-lookup"><span data-stu-id="bee7b-213">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bee7b-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bee7b-214">CommonParameters</span></span>

<span data-ttu-id="bee7b-215">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bee7b-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bee7b-216">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bee7b-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bee7b-217">输入</span><span class="sxs-lookup"><span data-stu-id="bee7b-217">INPUTS</span></span>

### <span data-ttu-id="bee7b-218">CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-218">CIM Instance</span></span>

<span data-ttu-id="bee7b-219">此 cmdlet 接受使用 InputObject 参数指定的输入对象。</span><span class="sxs-lookup"><span data-stu-id="bee7b-219">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="bee7b-220">输出</span><span class="sxs-lookup"><span data-stu-id="bee7b-220">OUTPUTS</span></span>

### <span data-ttu-id="bee7b-221">CIM 实例</span><span class="sxs-lookup"><span data-stu-id="bee7b-221">CIM Instance</span></span>

<span data-ttu-id="bee7b-222">此 cmdlet 将返回一个或多个 CIM 实例对象，这些对象表示 CIM 服务器上 CIM 实例的快照。</span><span class="sxs-lookup"><span data-stu-id="bee7b-222">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="bee7b-223">注释</span><span class="sxs-lookup"><span data-stu-id="bee7b-223">NOTES</span></span>

## <span data-ttu-id="bee7b-224">相关链接</span><span class="sxs-lookup"><span data-stu-id="bee7b-224">RELATED LINKS</span></span>

[<span data-ttu-id="bee7b-225">Format-Table</span><span class="sxs-lookup"><span data-stu-id="bee7b-225">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="bee7b-226">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="bee7b-226">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="bee7b-227">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="bee7b-227">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="bee7b-228">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="bee7b-228">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="bee7b-229">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bee7b-229">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="bee7b-230">Register-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="bee7b-230">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="bee7b-231">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bee7b-231">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="bee7b-232">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bee7b-232">Set-CimInstance</span></span>](Set-CimInstance.md)

