---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 59b7ea7f675d72dd90d970306c60107bd3f1de87
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596825"
---
# <span data-ttu-id="5032d-102">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-102">New-ItemProperty</span></span>

## <span data-ttu-id="5032d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5032d-103">SYNOPSIS</span></span>
<span data-ttu-id="5032d-104">为项创建新属性并设置该属性的值。</span><span class="sxs-lookup"><span data-stu-id="5032d-104">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="5032d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5032d-105">SYNTAX</span></span>

### <span data-ttu-id="5032d-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="5032d-106">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5032d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5032d-107">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5032d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5032d-108">DESCRIPTION</span></span>

<span data-ttu-id="5032d-109">`New-ItemProperty`Cmdlet 为指定项创建新属性并设置其值。</span><span class="sxs-lookup"><span data-stu-id="5032d-109">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="5032d-110">此 cmdlet 通常用于创建新注册表值，因为注册表值是注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="5032d-110">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="5032d-111">此 cmdlet 不能向对象添加属性。</span><span class="sxs-lookup"><span data-stu-id="5032d-111">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="5032d-112">若要将属性添加到对象的实例，请使用 `Add-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5032d-112">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="5032d-113">若要向特定类型的所有对象添加属性，请修改 Types.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="5032d-113">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="5032d-114">示例</span><span class="sxs-lookup"><span data-stu-id="5032d-114">EXAMPLES</span></span>

### <span data-ttu-id="5032d-115">示例 1：添加注册表项</span><span class="sxs-lookup"><span data-stu-id="5032d-115">Example 1: Add a registry entry</span></span>

<span data-ttu-id="5032d-116">此命令将新的注册表项 "NoOfEmployees" 添加到 "HKLM： \ 软件 hive" 的 "MyCompany" 键。</span><span class="sxs-lookup"><span data-stu-id="5032d-116">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="5032d-117">第一个命令使用 **Path** 参数来指定 "MyCompany" 注册表项的路径。</span><span class="sxs-lookup"><span data-stu-id="5032d-117">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="5032d-118">它使用 **name** 参数指定该条目的名称，使用 **value** 参数指定其值。</span><span class="sxs-lookup"><span data-stu-id="5032d-118">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="5032d-119">第二个命令使用 `Get-ItemProperty` cmdlet 查看新的注册表项。</span><span class="sxs-lookup"><span data-stu-id="5032d-119">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="5032d-120">示例 2：将注册表项添加到键</span><span class="sxs-lookup"><span data-stu-id="5032d-120">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="5032d-121">此命令向注册表项添加新的注册表条目。</span><span class="sxs-lookup"><span data-stu-id="5032d-121">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="5032d-122">为了指定密钥，它使用管道运算符 () 将 `|` 表示密钥的对象发送到 `New-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="5032d-122">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="5032d-123">该命令的第一部分使用 `Get-Item` cmdlet 来获取 "MyCompany" 注册表项。</span><span class="sxs-lookup"><span data-stu-id="5032d-123">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="5032d-124">管道运算符将命令的结果发送到 `New-ItemProperty` ，这会将新的注册表项 ( "NoOfLocations" ) ，并将其值 (3) 添加到 "MyCompany" 键。</span><span class="sxs-lookup"><span data-stu-id="5032d-124">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="5032d-125">此命令有效，因为 PowerShell 的参数绑定功能将返回的对象的路径 `RegistryKey` 与的 `Get-Item` **LiteralPath** 参数相关联 `New-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="5032d-125">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="5032d-126">有关详细信息，请参阅 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-126">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="5032d-127">示例3：使用 Here-String 在注册表中创建多字符串值</span><span class="sxs-lookup"><span data-stu-id="5032d-127">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="5032d-128">此示例使用多字符串创建一个值。</span><span class="sxs-lookup"><span data-stu-id="5032d-128">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="5032d-129">示例4：使用数组在注册表中创建多字符串值</span><span class="sxs-lookup"><span data-stu-id="5032d-129">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="5032d-130">该示例演示如何使用值数组创建 `MultiString` 值。</span><span class="sxs-lookup"><span data-stu-id="5032d-130">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="5032d-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5032d-131">PARAMETERS</span></span>

### <span data-ttu-id="5032d-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="5032d-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5032d-133">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="5032d-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="5032d-134">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-135">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5032d-135">-Exclude</span></span>

<span data-ttu-id="5032d-136">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="5032d-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="5032d-137">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="5032d-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5032d-138">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="5032d-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="5032d-139">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5032d-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="5032d-140">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5032d-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5032d-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="5032d-141">-Filter</span></span>

<span data-ttu-id="5032d-142">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="5032d-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="5032d-143">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="5032d-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="5032d-144">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="5032d-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="5032d-145">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="5032d-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5032d-146">-Force</span><span class="sxs-lookup"><span data-stu-id="5032d-146">-Force</span></span>

<span data-ttu-id="5032d-147">强制 cmdlet 创建用户非此不能访问的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="5032d-147">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="5032d-148">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="5032d-148">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="5032d-149">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-149">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-150">-Include</span><span class="sxs-lookup"><span data-stu-id="5032d-150">-Include</span></span>

<span data-ttu-id="5032d-151">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="5032d-151">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="5032d-152">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="5032d-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5032d-153">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="5032d-153">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="5032d-154">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5032d-154">Wildcard characters are permitted.</span></span> <span data-ttu-id="5032d-155">仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="5032d-155">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5032d-156">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5032d-156">-LiteralPath</span></span>

<span data-ttu-id="5032d-157">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="5032d-157">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5032d-158">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="5032d-158">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5032d-159">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="5032d-159">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5032d-160">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="5032d-160">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5032d-161">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="5032d-161">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5032d-162">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-163">-Name</span><span class="sxs-lookup"><span data-stu-id="5032d-163">-Name</span></span>

<span data-ttu-id="5032d-164">指定新属性的名称。</span><span class="sxs-lookup"><span data-stu-id="5032d-164">Specifies a name for the new property.</span></span>
<span data-ttu-id="5032d-165">如果该属性是注册表条目，则此参数指定该条目的名称。</span><span class="sxs-lookup"><span data-stu-id="5032d-165">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-166">-Path</span><span class="sxs-lookup"><span data-stu-id="5032d-166">-Path</span></span>

<span data-ttu-id="5032d-167">指定项的路径。</span><span class="sxs-lookup"><span data-stu-id="5032d-167">Specifies the path of the item.</span></span>
<span data-ttu-id="5032d-168">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5032d-168">Wildcard characters are permitted.</span></span>
<span data-ttu-id="5032d-169">此参数标识此 cmdlet 要向其添加新属性的项。</span><span class="sxs-lookup"><span data-stu-id="5032d-169">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5032d-170">-PropertyType</span><span class="sxs-lookup"><span data-stu-id="5032d-170">-PropertyType</span></span>

<span data-ttu-id="5032d-171">指定此 cmdlet 添加的属性类型。</span><span class="sxs-lookup"><span data-stu-id="5032d-171">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="5032d-172">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="5032d-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5032d-173">**String**：指定以 null 结尾的字符串。</span><span class="sxs-lookup"><span data-stu-id="5032d-173">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="5032d-174">等效于 **REG_SZ**。</span><span class="sxs-lookup"><span data-stu-id="5032d-174">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="5032d-175">**ExpandString**：指定一个以 null 结尾的字符串，该字符串包含对在检索值时扩展的环境变量的未展开引用。</span><span class="sxs-lookup"><span data-stu-id="5032d-175">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="5032d-176">等效于 **REG_EXPAND_SZ**。</span><span class="sxs-lookup"><span data-stu-id="5032d-176">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="5032d-177">**Binary**：指定任意格式的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="5032d-177">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="5032d-178">等效于 **REG_BINARY**。</span><span class="sxs-lookup"><span data-stu-id="5032d-178">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="5032d-179">**DWord**：指定32位二进制数。</span><span class="sxs-lookup"><span data-stu-id="5032d-179">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="5032d-180">等效于 **REG_DWORD**。</span><span class="sxs-lookup"><span data-stu-id="5032d-180">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="5032d-181">**多字符串**：指定以 null 结尾的字符串的数组，该数组以两个 null 字符结尾。</span><span class="sxs-lookup"><span data-stu-id="5032d-181">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="5032d-182">等效于 **REG_MULTI_SZ**。</span><span class="sxs-lookup"><span data-stu-id="5032d-182">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="5032d-183">**Qword**：指定64位二进制数。</span><span class="sxs-lookup"><span data-stu-id="5032d-183">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="5032d-184">等效于 **REG_QWORD**。</span><span class="sxs-lookup"><span data-stu-id="5032d-184">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="5032d-185">**未知**：指示不受支持的注册表数据类型，如 **REG_RESOURCE_LIST**。</span><span class="sxs-lookup"><span data-stu-id="5032d-185">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-186">-Value</span><span class="sxs-lookup"><span data-stu-id="5032d-186">-Value</span></span>

<span data-ttu-id="5032d-187">指定属性值。</span><span class="sxs-lookup"><span data-stu-id="5032d-187">Specifies the property value.</span></span>
<span data-ttu-id="5032d-188">如果该属性是注册表条目，则此参数指定该条目的值。</span><span class="sxs-lookup"><span data-stu-id="5032d-188">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5032d-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5032d-189">-Confirm</span></span>

<span data-ttu-id="5032d-190">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="5032d-190">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5032d-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5032d-191">-WhatIf</span></span>

<span data-ttu-id="5032d-192">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="5032d-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5032d-193">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="5032d-193">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5032d-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5032d-194">CommonParameters</span></span>

<span data-ttu-id="5032d-195">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="5032d-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="5032d-196">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5032d-197">输入</span><span class="sxs-lookup"><span data-stu-id="5032d-197">INPUTS</span></span>

### <span data-ttu-id="5032d-198">无</span><span class="sxs-lookup"><span data-stu-id="5032d-198">None</span></span>

<span data-ttu-id="5032d-199">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5032d-199">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5032d-200">输出</span><span class="sxs-lookup"><span data-stu-id="5032d-200">OUTPUTS</span></span>

### <span data-ttu-id="5032d-201">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="5032d-201">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="5032d-202">`New-ItemProperty` 返回一个包含新属性的自定义对象。</span><span class="sxs-lookup"><span data-stu-id="5032d-202">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="5032d-203">注释</span><span class="sxs-lookup"><span data-stu-id="5032d-203">NOTES</span></span>

<span data-ttu-id="5032d-204">`New-ItemProperty` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="5032d-204">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5032d-205">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="5032d-205">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="5032d-206">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5032d-206">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5032d-207">相关链接</span><span class="sxs-lookup"><span data-stu-id="5032d-207">RELATED LINKS</span></span>

[<span data-ttu-id="5032d-208">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-208">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="5032d-209">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-209">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="5032d-210">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-210">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="5032d-211">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-211">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="5032d-212">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-212">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="5032d-213">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-213">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="5032d-214">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5032d-214">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="5032d-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5032d-215">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

