---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: d81117ad6885d660e31f031bd8134096db91b7da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598864"
---
# <span data-ttu-id="b4663-102">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="b4663-102">New-CimInstance</span></span>

## <span data-ttu-id="b4663-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b4663-103">SYNOPSIS</span></span>
<span data-ttu-id="b4663-104">创建 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-104">Creates a CIM instance.</span></span>

## <span data-ttu-id="b4663-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4663-105">SYNTAX</span></span>

### <span data-ttu-id="b4663-106">ClassNameComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="b4663-106">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4663-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="b4663-107">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4663-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="b4663-108">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4663-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="b4663-109">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4663-110">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="b4663-110">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b4663-111">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="b4663-111">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b4663-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b4663-112">DESCRIPTION</span></span>

<span data-ttu-id="b4663-113">该 `New-CimInstance` cmdlet 根据本地计算机或远程计算机上的类定义创建 CIM 类的实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-113">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="b4663-114">默认情况下，该 `New-CimInstance` cmdlet 在本地计算机上创建一个实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-114">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="b4663-115">示例</span><span class="sxs-lookup"><span data-stu-id="b4663-115">EXAMPLES</span></span>

### <span data-ttu-id="b4663-116">示例1：创建 CIM 类的实例</span><span class="sxs-lookup"><span data-stu-id="b4663-116">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="b4663-117">此示例在计算机上的根/cimv2 命名空间中创建名为 win32_environment 的 CIM 类的实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-117">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="b4663-118">如果类不存在、属性错误或服务器拒绝调用，则不会执行客户端验证。</span><span class="sxs-lookup"><span data-stu-id="b4663-118">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="b4663-119">如果成功创建实例，则该 cmdlet 将输出新创建的实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-119">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="b4663-120">示例2：使用类架构创建 CIM 类的实例</span><span class="sxs-lookup"><span data-stu-id="b4663-120">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="b4663-121">此示例将检索一个 CIM 类对象，并将其存储在一个名为的变量中 `$class` 。</span><span class="sxs-lookup"><span data-stu-id="b4663-121">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="b4663-122">然后，将变量的内容传递给 `New-CimInstance` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b4663-122">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="b4663-123">示例3：在客户端上创建动态实例</span><span class="sxs-lookup"><span data-stu-id="b4663-123">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="b4663-124">此示例在客户端计算机上创建名为 **Win32_Process** 的 CIM 类的动态实例，而无需从服务器中获取实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-124">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="b4663-125">新实例存储在变量中 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="b4663-125">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="b4663-126">如果具有此密钥的实例存在于服务器上，则可以使用此动态实例执行操作。</span><span class="sxs-lookup"><span data-stu-id="b4663-126">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="b4663-127">然后，该 `Get-CimInstance` cmdlet 将检索特定的单个实例。</span><span class="sxs-lookup"><span data-stu-id="b4663-127">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="b4663-128">此 `Invoke-CimMethod` cmdlet 将对检索到的实例调用 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="b4663-128">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="b4663-129">示例4：为特定命名空间的 CIM 类创建实例</span><span class="sxs-lookup"><span data-stu-id="b4663-129">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="b4663-130">此示例获取命名空间 **root/某个位置** 名为 **MSFT_Something** 的 CIM 类的实例，并将其存储在一个名为的变量中 `$class` 。</span><span class="sxs-lookup"><span data-stu-id="b4663-130">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="b4663-131">将变量传递给 cmdlet， `New-CimInstance` 以创建新的 CIM 实例，并在新的实例上执行客户端验证。</span><span class="sxs-lookup"><span data-stu-id="b4663-131">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="b4663-132">在此示例中，使用 **CimClass** 参数而不是 **ClassName** 参数来验证 **Prop1** 和 **Prop2** 是否确实存在，并确保已正确标记键。</span><span class="sxs-lookup"><span data-stu-id="b4663-132">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="b4663-133">不能将 **ComputerName** 或 **CimSession** 参数与 **ClientOnly** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="b4663-133">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="b4663-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b4663-134">PARAMETERS</span></span>

### <span data-ttu-id="b4663-135">-CimClass</span><span class="sxs-lookup"><span data-stu-id="b4663-135">-CimClass</span></span>

<span data-ttu-id="b4663-136">指定一个 CIM 类对象，该对象表示实例的类型。</span><span class="sxs-lookup"><span data-stu-id="b4663-136">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="b4663-137">使用 `Get-CimClass` cmdlet 从计算机中检索类声明。</span><span class="sxs-lookup"><span data-stu-id="b4663-137">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="b4663-138">使用此参数将导致更好的客户端架构验证。</span><span class="sxs-lookup"><span data-stu-id="b4663-138">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-139">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b4663-139">-CimSession</span></span>

<span data-ttu-id="b4663-140">使用指定的 CIM 会话运行该命令。</span><span class="sxs-lookup"><span data-stu-id="b4663-140">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="b4663-141">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="b4663-141">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="b4663-142">有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="b4663-142">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-143">-ClassName</span><span class="sxs-lookup"><span data-stu-id="b4663-143">-ClassName</span></span>

<span data-ttu-id="b4663-144">指定操作为其创建实例的 CIM 类的名称。</span><span class="sxs-lookup"><span data-stu-id="b4663-144">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="b4663-145">注意：可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。</span><span class="sxs-lookup"><span data-stu-id="b4663-145">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="b4663-146">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="b4663-146">-ClientOnly</span></span>

<span data-ttu-id="b4663-147">指示仅在 PowerShell 中创建实例，而不转到 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="b4663-147">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="b4663-148">你可以使用此参数创建内存中 CIM 实例，以供在后续 PowerShell 操作中使用。</span><span class="sxs-lookup"><span data-stu-id="b4663-148">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b4663-149">-ComputerName</span></span>

<span data-ttu-id="b4663-150">指定要在其上运行 CIM 操作的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="b4663-150">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="b4663-151">可以指定完全限定的域名 (FQDN) 、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b4663-151">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="b4663-152">如果指定此参数，则该 cmdlet 将使用 WSMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="b4663-152">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="b4663-153">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="b4663-153">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="b4663-154">如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="b4663-154">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-155">-Key</span><span class="sxs-lookup"><span data-stu-id="b4663-155">-Key</span></span>

<span data-ttu-id="b4663-156">指定用作键的属性。</span><span class="sxs-lookup"><span data-stu-id="b4663-156">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="b4663-157">指定 **键** 后，不能使用 **CimSession** 和 **ComputerName** 。</span><span class="sxs-lookup"><span data-stu-id="b4663-157">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-158">-Namespace</span><span class="sxs-lookup"><span data-stu-id="b4663-158">-Namespace</span></span>

<span data-ttu-id="b4663-159">为新实例指定类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="b4663-159">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="b4663-160">默认命名空间为 **root/cimv2**。</span><span class="sxs-lookup"><span data-stu-id="b4663-160">The default namespace is **root/cimv2**.</span></span>
<span data-ttu-id="b4663-161">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="b4663-161">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-162">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b4663-162">-OperationTimeoutSec</span></span>

<span data-ttu-id="b4663-163">指定 cmdlet 等待 CIM 服务器的响应的时间长度。</span><span class="sxs-lookup"><span data-stu-id="b4663-163">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="b4663-164">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="b4663-164">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="b4663-165">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="b4663-165">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="b4663-166">-Property</span><span class="sxs-lookup"><span data-stu-id="b4663-166">-Property</span></span>

<span data-ttu-id="b4663-167">使用)  (名称-值对的哈希表指定 CIM 实例的属性。</span><span class="sxs-lookup"><span data-stu-id="b4663-167">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="b4663-168">如果指定 **CimClass** 参数，则该 cmdlet 将 `New-CimInstance` 在客户端上执行属性验证，以确保指定的属性与服务器上的类声明一致。</span><span class="sxs-lookup"><span data-stu-id="b4663-168">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="b4663-169">如果未指定 **CimClass** 参数，则将在服务器上执行属性验证。</span><span class="sxs-lookup"><span data-stu-id="b4663-169">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-170">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="b4663-170">-ResourceUri</span></span>

<span data-ttu-id="b4663-171">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="b4663-171">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="b4663-172">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="b4663-172">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="b4663-173">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="b4663-173">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="b4663-174">例如：</span><span class="sxs-lookup"><span data-stu-id="b4663-174">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="b4663-175">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="b4663-175">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="b4663-176">**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。</span><span class="sxs-lookup"><span data-stu-id="b4663-176">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="b4663-177">如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则将收到错误，因为 DCOM 协议不支持 **ResourceURI** 参数。</span><span class="sxs-lookup"><span data-stu-id="b4663-177">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="b4663-178">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="b4663-178">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b4663-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b4663-179">-Confirm</span></span>

<span data-ttu-id="b4663-180">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="b4663-180">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b4663-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b4663-181">-WhatIf</span></span>

<span data-ttu-id="b4663-182">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="b4663-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b4663-183">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b4663-183">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b4663-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4663-184">CommonParameters</span></span>

<span data-ttu-id="b4663-185">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b4663-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4663-186">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b4663-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b4663-187">输入</span><span class="sxs-lookup"><span data-stu-id="b4663-187">INPUTS</span></span>

### <span data-ttu-id="b4663-188">无</span><span class="sxs-lookup"><span data-stu-id="b4663-188">None</span></span>

<span data-ttu-id="b4663-189">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="b4663-189">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="b4663-190">输出</span><span class="sxs-lookup"><span data-stu-id="b4663-190">OUTPUTS</span></span>

### <span data-ttu-id="b4663-191">System.Object</span><span class="sxs-lookup"><span data-stu-id="b4663-191">System.Object</span></span>

<span data-ttu-id="b4663-192">此 cmdlet 将返回一个对象，其中包含 CIM 实例信息。</span><span class="sxs-lookup"><span data-stu-id="b4663-192">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="b4663-193">注释</span><span class="sxs-lookup"><span data-stu-id="b4663-193">NOTES</span></span>

## <span data-ttu-id="b4663-194">相关链接</span><span class="sxs-lookup"><span data-stu-id="b4663-194">RELATED LINKS</span></span>

[<span data-ttu-id="b4663-195">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="b4663-195">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="b4663-196">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="b4663-196">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="b4663-197">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="b4663-197">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="b4663-198">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="b4663-198">Set-CimInstance</span></span>](Set-CimInstance.md)

