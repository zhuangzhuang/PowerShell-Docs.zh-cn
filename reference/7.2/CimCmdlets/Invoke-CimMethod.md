---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 1217e07d09213d7c0e223129207c085b9ba2d48d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597851"
---
# <span data-ttu-id="cbd13-102">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="cbd13-102">Invoke-CimMethod</span></span>

## <span data-ttu-id="cbd13-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cbd13-103">SYNOPSIS</span></span>
<span data-ttu-id="cbd13-104">调用 CIM 类的方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-104">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="cbd13-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbd13-105">SYNTAX</span></span>

### <span data-ttu-id="cbd13-106">ClassNameComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="cbd13-106">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd13-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-107">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd13-108">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-108">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd13-109">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-109">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cbd13-110">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-110">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cbd13-111">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-111">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd13-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-112">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cbd13-113">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-113">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cbd13-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-114">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cbd13-115">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="cbd13-115">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cbd13-116">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cbd13-116">DESCRIPTION</span></span>

<span data-ttu-id="cbd13-117">该 `Invoke-CimMethod` cmdlet 使用由 **Arguments** 参数指定的名称/值对来调用 CIM 类或 cim 实例的方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-117">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="cbd13-118">如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="cbd13-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="cbd13-119">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。</span><span class="sxs-lookup"><span data-stu-id="cbd13-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="cbd13-120">如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="cbd13-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="cbd13-121">如果指定了 **InputObject** 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="cbd13-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="cbd13-122">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将使用输入对象中的 CIM 会话或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="cbd13-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="cbd13-123">如果指定了 **ComputerName** 参数或 **CimSession** 参数，则此 cmdlet 将使用 **CimSession** 参数值或 **ComputerName** 参数值。</span><span class="sxs-lookup"><span data-stu-id="cbd13-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="cbd13-124">这种情况并不常见。</span><span class="sxs-lookup"><span data-stu-id="cbd13-124">This is not a common scenario.</span></span>

## <span data-ttu-id="cbd13-125">示例</span><span class="sxs-lookup"><span data-stu-id="cbd13-125">EXAMPLES</span></span>

### <span data-ttu-id="cbd13-126">示例1：调用方法</span><span class="sxs-lookup"><span data-stu-id="cbd13-126">Example 1: Invoke a method</span></span>

<span data-ttu-id="cbd13-127">此示例调用 **Win32_Process** 类的 **Terminate** 方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-127">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="cbd13-128">示例2：使用 CIM 实例对象调用方法</span><span class="sxs-lookup"><span data-stu-id="cbd13-128">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="cbd13-129">此示例将检索 CIM 实例对象，并使用 cmdlet 将其存储在一个名为的变量中 `$x` `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="cbd13-129">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="cbd13-130">然后，将该变量的内容用作该 cmdlet 的 **InputObject** `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="cbd13-130">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="cbd13-131">为 **CimInstance** 调用 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-131">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="cbd13-132">示例3：使用参数调用静态方法</span><span class="sxs-lookup"><span data-stu-id="cbd13-132">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="cbd13-133">此示例使用 **Arguments** 参数调用名为的 **Create** 方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-133">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="cbd13-134">示例4：客户端验证</span><span class="sxs-lookup"><span data-stu-id="cbd13-134">Example 4: Client-side validation</span></span>

<span data-ttu-id="cbd13-135">此示例通过将 **CimClass** 对象传递给，为 **xyz** 方法执行客户端验证 `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="cbd13-135">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="cbd13-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbd13-136">PARAMETERS</span></span>

### <span data-ttu-id="cbd13-137">-Arguments</span><span class="sxs-lookup"><span data-stu-id="cbd13-137">-Arguments</span></span>

<span data-ttu-id="cbd13-138">指定要传递给被调用方法的参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-138">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="cbd13-139">将此参数的值指定为名称-值对，存储在哈希表中。</span><span class="sxs-lookup"><span data-stu-id="cbd13-139">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="cbd13-140">输入的值的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="cbd13-140">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-141">-CimClass</span><span class="sxs-lookup"><span data-stu-id="cbd13-141">-CimClass</span></span>

<span data-ttu-id="cbd13-142">指定一个 CIM 类对象，该对象表示服务器上的 CIM 类定义。</span><span class="sxs-lookup"><span data-stu-id="cbd13-142">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="cbd13-143">调用类的静态方法时，请使用此参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-143">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="cbd13-144">可以使用 `Get-CimClass` cmdlet 从服务器中检索类定义。</span><span class="sxs-lookup"><span data-stu-id="cbd13-144">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="cbd13-145">使用此参数将导致更好的客户端架构验证。</span><span class="sxs-lookup"><span data-stu-id="cbd13-145">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-146">-CimSession</span><span class="sxs-lookup"><span data-stu-id="cbd13-146">-CimSession</span></span>

<span data-ttu-id="cbd13-147">使用指定的 CIM 会话运行该命令。</span><span class="sxs-lookup"><span data-stu-id="cbd13-147">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="cbd13-148">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="cbd13-148">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="cbd13-149">有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="cbd13-149">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-150">-ClassName</span><span class="sxs-lookup"><span data-stu-id="cbd13-150">-ClassName</span></span>

<span data-ttu-id="cbd13-151">指定要对其执行操作的 CIM 类的名称。</span><span class="sxs-lookup"><span data-stu-id="cbd13-151">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="cbd13-152">此参数仅用于静态方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-152">This parameter is only used for static methods.</span></span> <span data-ttu-id="cbd13-153">您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。</span><span class="sxs-lookup"><span data-stu-id="cbd13-153">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cbd13-154">-ComputerName</span></span>

<span data-ttu-id="cbd13-155">指定要在其上运行 CIM 操作的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="cbd13-155">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="cbd13-156">可以指定完全限定的域名 (FQDN) 、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cbd13-156">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="cbd13-157">使用此参数时，该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="cbd13-157">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="cbd13-158">否则，此 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行该操作。</span><span class="sxs-lookup"><span data-stu-id="cbd13-158">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="cbd13-159">当在同一台计算机上执行多个操作时，使用 CIM 会话进行连接以获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="cbd13-159">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cbd13-160">-InputObject</span></span>

<span data-ttu-id="cbd13-161">指定要用作调用方法的输入的 CIM 实例对象。</span><span class="sxs-lookup"><span data-stu-id="cbd13-161">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="cbd13-162">此参数仅可用于调用实例方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-162">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="cbd13-163">若要调用类静态方法，请使用 **类** 参数或 **CimClass** 参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-163">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="cbd13-164">-方法名称</span><span class="sxs-lookup"><span data-stu-id="cbd13-164">-MethodName</span></span>

<span data-ttu-id="cbd13-165">指定要调用的 CIM 方法的名称。</span><span class="sxs-lookup"><span data-stu-id="cbd13-165">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="cbd13-166">此参数是必需的，不能为 null 或为空。</span><span class="sxs-lookup"><span data-stu-id="cbd13-166">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="cbd13-167">若要调用 CIM 类的静态方法，请使用 **ClassName** 或 **CimClass** 参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-167">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-168">-Namespace</span><span class="sxs-lookup"><span data-stu-id="cbd13-168">-Namespace</span></span>

<span data-ttu-id="cbd13-169">指定 CIM 操作的命名空间。</span><span class="sxs-lookup"><span data-stu-id="cbd13-169">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="cbd13-170">默认命名空间为 **root/cimv2**。</span><span class="sxs-lookup"><span data-stu-id="cbd13-170">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="cbd13-171">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="cbd13-171">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-172">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="cbd13-172">-OperationTimeoutSec</span></span>

<span data-ttu-id="cbd13-173">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="cbd13-173">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="cbd13-174">默认情况下，此值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="cbd13-174">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="cbd13-175">如果将 **OperationTimeoutSec** 参数设置为小于默认连接重试超时值3分钟的值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障。</span><span class="sxs-lookup"><span data-stu-id="cbd13-175">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="cbd13-176">-Query</span><span class="sxs-lookup"><span data-stu-id="cbd13-176">-Query</span></span>

<span data-ttu-id="cbd13-177">指定要在 CIM 服务器上运行的查询。</span><span class="sxs-lookup"><span data-stu-id="cbd13-177">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="cbd13-178">在作为查询结果收到的实例上调用方法。</span><span class="sxs-lookup"><span data-stu-id="cbd13-178">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="cbd13-179">您可以使用 **QueryDialect** 参数指定查询方言。</span><span class="sxs-lookup"><span data-stu-id="cbd13-179">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="cbd13-180">如果指定的值包含双引号 (`"`) 、单引号 (`'`) 或反斜杠 (`\`) ，则必须使用反斜杠 () 字符作为前缀，来对这些字符进行转义 `\` 。</span><span class="sxs-lookup"><span data-stu-id="cbd13-180">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="cbd13-181">如果指定的值使用 WQL LIKE 运算符，则必须通过将以下字符括在方括号中来对其进行转义 (`[]`) ：百分比 (`%`) 、下划线 (`_`) 或左方括号 (`[`) 。</span><span class="sxs-lookup"><span data-stu-id="cbd13-181">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="cbd13-182">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="cbd13-182">-QueryDialect</span></span>

<span data-ttu-id="cbd13-183">指定用于查询参数的查询语言。</span><span class="sxs-lookup"><span data-stu-id="cbd13-183">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="cbd13-184">此参数的可接受值为： **WQL** 或 **CQL**。</span><span class="sxs-lookup"><span data-stu-id="cbd13-184">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="cbd13-185">默认值为 **WQL**。</span><span class="sxs-lookup"><span data-stu-id="cbd13-185">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="cbd13-186">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="cbd13-186">-ResourceUri</span></span>

<span data-ttu-id="cbd13-187">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="cbd13-187">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="cbd13-188">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="cbd13-188">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="cbd13-189">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="cbd13-189">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="cbd13-190">例如：</span><span class="sxs-lookup"><span data-stu-id="cbd13-190">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="cbd13-191">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="cbd13-191">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="cbd13-192">**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。</span><span class="sxs-lookup"><span data-stu-id="cbd13-192">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="cbd13-193">如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，会收到错误。</span><span class="sxs-lookup"><span data-stu-id="cbd13-193">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="cbd13-194">DCOM 协议不支持 **ResourceURI** 参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-194">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="cbd13-195">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="cbd13-195">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd13-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cbd13-196">-Confirm</span></span>

<span data-ttu-id="cbd13-197">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cbd13-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cbd13-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cbd13-198">-WhatIf</span></span>

<span data-ttu-id="cbd13-199">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cbd13-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cbd13-200">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cbd13-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cbd13-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbd13-201">CommonParameters</span></span>

<span data-ttu-id="cbd13-202">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cbd13-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbd13-203">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cbd13-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cbd13-204">输入</span><span class="sxs-lookup"><span data-stu-id="cbd13-204">INPUTS</span></span>

### <span data-ttu-id="cbd13-205">CIM 类</span><span class="sxs-lookup"><span data-stu-id="cbd13-205">CIM class</span></span>

<span data-ttu-id="cbd13-206">此 cmdlet 将 CIM 类作为输入对象接受。</span><span class="sxs-lookup"><span data-stu-id="cbd13-206">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="cbd13-207">CIM 实例</span><span class="sxs-lookup"><span data-stu-id="cbd13-207">CIM instance</span></span>

<span data-ttu-id="cbd13-208">此 cmdlet 将 CIM 实例作为输入对象接受。</span><span class="sxs-lookup"><span data-stu-id="cbd13-208">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="cbd13-209">输出</span><span class="sxs-lookup"><span data-stu-id="cbd13-209">OUTPUTS</span></span>

### <span data-ttu-id="cbd13-210">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="cbd13-210">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="cbd13-211">此 cmdlet 将返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="cbd13-211">This cmdlet returns an object.</span></span>

## <span data-ttu-id="cbd13-212">注释</span><span class="sxs-lookup"><span data-stu-id="cbd13-212">NOTES</span></span>

## <span data-ttu-id="cbd13-213">相关链接</span><span class="sxs-lookup"><span data-stu-id="cbd13-213">RELATED LINKS</span></span>

[<span data-ttu-id="cbd13-214">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="cbd13-214">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="cbd13-215">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="cbd13-215">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="cbd13-216">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="cbd13-216">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="cbd13-217">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="cbd13-217">New-CimSession</span></span>](New-CimSession.md)

