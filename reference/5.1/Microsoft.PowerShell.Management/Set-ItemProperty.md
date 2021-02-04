---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: cbd1229721650823d9780517934c40a2287f4227
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692669"
---
# <span data-ttu-id="fd2ac-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-103">Set-ItemProperty</span></span>

## <span data-ttu-id="fd2ac-104">摘要</span><span class="sxs-lookup"><span data-stu-id="fd2ac-104">SYNOPSIS</span></span>
<span data-ttu-id="fd2ac-105">创建或更改某一项的属性值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="fd2ac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd2ac-106">SYNTAX</span></span>

### <span data-ttu-id="fd2ac-107">propertyValuePathSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="fd2ac-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="fd2ac-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="fd2ac-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="fd2ac-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="fd2ac-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="fd2ac-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="fd2ac-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="fd2ac-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fd2ac-111">DESCRIPTION</span></span>

<span data-ttu-id="fd2ac-112">`Set-ItemProperty`Cmdlet 更改指定项的属性的值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span> <span data-ttu-id="fd2ac-113">可以使用该 cmdlet 设定或更改项的属性。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-113">You can use the cmdlet to establish or change the properties of items.</span></span> <span data-ttu-id="fd2ac-114">例如，可以使用 `Set-ItemProperty` 将文件对象的 **IsReadOnly** 属性的值设置为 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="fd2ac-115">你还可以使用 `Set-ItemProperty` 来创建和更改注册表值和数据。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="fd2ac-116">例如，可以向注册表项中添加新的注册表条目以及设定或更改该条目的值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="fd2ac-117">示例</span><span class="sxs-lookup"><span data-stu-id="fd2ac-117">EXAMPLES</span></span>

### <span data-ttu-id="fd2ac-118">示例1：设置文件的属性</span><span class="sxs-lookup"><span data-stu-id="fd2ac-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="fd2ac-119">此命令将 "final.doc" 文件的 " **IsReadOnly** " 属性的值设置为 "true"。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span> <span data-ttu-id="fd2ac-120">它使用 **路径** 指定文件的名称，使用 **name** 指定属性的名称，并使用 **Value** 参数指定新值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="fd2ac-121">文件是 **FileInfo** 对象，而 **IsReadOnly** 只是它的一个属性。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="fd2ac-122">若要查看所有属性，请键入 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property`.</span></span>

<span data-ttu-id="fd2ac-123">`$true`自动变量表示值 "TRUE"。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="fd2ac-124">有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="fd2ac-125">示例2：创建注册表项和值</span><span class="sxs-lookup"><span data-stu-id="fd2ac-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="fd2ac-126">此示例演示如何使用 `Set-ItemProperty` 来创建新的注册表项，并为该项分配值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="fd2ac-127">它在 "HKLM\Software" 键中的 "ContosoCompany" 键内创建 "NoOfEmployees" 条目，并将其值设置为823。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in "HKLM\Software" key and sets its value to 823.</span></span>

<span data-ttu-id="fd2ac-128">因为注册表项被视为注册表项的属性（这些项是项），您可以使用这些项 `Set-ItemProperty` 创建注册表项，并建立和更改它们的值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

<span data-ttu-id="fd2ac-129">第一个命令创建注册表项。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="fd2ac-130">它使用 **path** 来指定驱动器的路径 `HKLM:` 和 "Software\MyCompany" 项。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="fd2ac-131">该命令使用 **name** 来指定输入值的名称和 **值** 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="fd2ac-132">第二个命令使用 `Get-ItemProperty` cmdlet 查看新的注册表项。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span> <span data-ttu-id="fd2ac-133">如果使用 `Get-Item` 或 `Get-ChildItem` cmdlet，则这些项将不会显示，因为它们是键的属性，而不是项或子项的属性。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="fd2ac-134">第三个命令将 **NoOfEmployees** 条目的值更改为824。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="fd2ac-135">你还可以使用 `New-ItemProperty` cmdlet 来创建注册表项及其值，并使用 `Set-ItemProperty` 来更改值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="fd2ac-136">有关驱动器的详细信息 `HKLM:` ，请键入 `Get-Help Get-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="fd2ac-137">有关如何使用 PowerShell 管理注册表的详细信息，请键入 `Get-Help Registry` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### <span data-ttu-id="fd2ac-138">示例3：使用管道修改项</span><span class="sxs-lookup"><span data-stu-id="fd2ac-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="fd2ac-139">这些命令演示如何使用管道运算符 () 将 `|` 项发送到 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="fd2ac-140">该命令的第一部分使用 `Get-ChildItem` 来获取表示 "Weekly.txt" 文件的对象。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span>
<span data-ttu-id="fd2ac-141">该命令使用管道运算符将文件对象发送到 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="fd2ac-142">该 `Set-ItemProperty` 命令使用 **Name** 和 **Value** 参数来指定属性及其新值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="fd2ac-143">此命令等效于使用 **InputObject** 参数指定获取的对象 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="fd2ac-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd2ac-144">PARAMETERS</span></span>

### <span data-ttu-id="fd2ac-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="fd2ac-145">-Credential</span></span>

<span data-ttu-id="fd2ac-146">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-146">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="fd2ac-147">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-147">The default is the current user.</span></span>

<span data-ttu-id="fd2ac-148">键入用户名，如“User01”或“Domain01\User01”；或输入 **PSCredential** 对象，如 `Get-Credential` cmdlet 生成的一个 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-148">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="fd2ac-149">如果键入用户名，则将提示你输入密码。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-149">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="fd2ac-150">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-150">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fd2ac-151">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="fd2ac-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fd2ac-152">-Exclude</span></span>

<span data-ttu-id="fd2ac-153">指定 cmdlet 不起作用的那些项，并包括所有其他项。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-153">Specifies those items upon which the cmdlet does not act, and includes all others.</span></span>
<span data-ttu-id="fd2ac-154">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="fd2ac-155">请输入路径元素或模式，例如“\*.txt”。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="fd2ac-156">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-156">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="fd2ac-157">-Filter</span></span>

<span data-ttu-id="fd2ac-158">以提供程序的格式或语言指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="fd2ac-159">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="fd2ac-160">筛选器的语法（包括通配符字符的使用），具体取决于提供程序。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="fd2ac-161">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="fd2ac-162">-Force</span><span class="sxs-lookup"><span data-stu-id="fd2ac-162">-Force</span></span>

<span data-ttu-id="fd2ac-163">强制 cmdlet 设置用户不能访问的项的属性。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-163">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="fd2ac-164">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-164">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="fd2ac-165">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="fd2ac-166">-Include</span><span class="sxs-lookup"><span data-stu-id="fd2ac-166">-Include</span></span>

<span data-ttu-id="fd2ac-167">仅指定 cmdlet 操作的那些项，排除所有其他项。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-167">Specifies only those items upon which the cmdlet acts, which excludes all others.</span></span>
<span data-ttu-id="fd2ac-168">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-168">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="fd2ac-169">请输入路径元素或模式，例如“\*.txt”。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-169">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="fd2ac-170">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-170">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-171">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fd2ac-171">-InputObject</span></span>

<span data-ttu-id="fd2ac-172">指定具有此 cmdlet 更改的属性的对象。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-172">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="fd2ac-173">请输入包含对象的变量或可获取该对象的命令。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-173">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fd2ac-174">-LiteralPath</span></span>

<span data-ttu-id="fd2ac-175">指定项属性的路径。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-175">Specifies a path of the item property.</span></span>
<span data-ttu-id="fd2ac-176">与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-176">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="fd2ac-177">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-177">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="fd2ac-178">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-178">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="fd2ac-179">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-180">-Name</span><span class="sxs-lookup"><span data-stu-id="fd2ac-180">-Name</span></span>

<span data-ttu-id="fd2ac-181">指定属性的名称。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-181">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-182">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fd2ac-182">-PassThru</span></span>

<span data-ttu-id="fd2ac-183">返回一个表示项属性的对象。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-183">Returns an object that represents the item property.</span></span>
<span data-ttu-id="fd2ac-184">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-184">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fd2ac-185">-Path</span><span class="sxs-lookup"><span data-stu-id="fd2ac-185">-Path</span></span>

<span data-ttu-id="fd2ac-186">指定包含要修改的属性的项的路径。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-186">Specifies the path of the items with the property to modify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-187">-Type</span><span class="sxs-lookup"><span data-stu-id="fd2ac-187">-Type</span></span>

<span data-ttu-id="fd2ac-188">**类型** 是注册表提供程序添加到 cmdlet 的动态参数 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="fd2ac-189">此参数仅适用于注册表驱动器。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="fd2ac-190">指定此 cmdlet 添加的属性类型。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="fd2ac-191">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="fd2ac-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fd2ac-192">**String**：指定以 null 结尾的字符串。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-192">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="fd2ac-193">等效于 **REG_SZ**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-193">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="fd2ac-194">**ExpandString**：指定一个以 null 结尾的字符串，该字符串包含对在检索值时扩展的环境变量的未展开引用。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-194">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="fd2ac-195">等效于 **REG_EXPAND_SZ**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-195">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="fd2ac-196">**Binary**：指定任意格式的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-196">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="fd2ac-197">等效于 **REG_BINARY**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-197">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="fd2ac-198">**DWord**：指定32位二进制数。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-198">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="fd2ac-199">等效于 **REG_DWORD**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-199">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="fd2ac-200">**多字符串**：指定以 null 结尾的字符串的数组，该数组以两个 null 字符结尾。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-200">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="fd2ac-201">等效于 **REG_MULTI_SZ**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-201">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="fd2ac-202">**Qword**：指定64位二进制数。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-202">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="fd2ac-203">等效于 **REG_QWORD**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-203">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="fd2ac-204">**未知**：指示不受支持的注册表数据类型，如 **REG_RESOURCE_LIST**。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-204">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-205">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="fd2ac-205">-UseTransaction</span></span>

<span data-ttu-id="fd2ac-206">在活动事务中使用该命令。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-206">Includes the command in the active transaction.</span></span>
<span data-ttu-id="fd2ac-207">仅当正在执行事务时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-207">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="fd2ac-208">有关详细信息，请参阅 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-208">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-209">-Value</span><span class="sxs-lookup"><span data-stu-id="fd2ac-209">-Value</span></span>

<span data-ttu-id="fd2ac-210">指定属性的值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-210">Specifies the value of the property.</span></span>

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fd2ac-211">-Confirm</span></span>

<span data-ttu-id="fd2ac-212">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fd2ac-213">-WhatIf</span></span>

<span data-ttu-id="fd2ac-214">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-214">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fd2ac-215">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-215">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd2ac-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd2ac-216">CommonParameters</span></span>

<span data-ttu-id="fd2ac-217">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-217">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fd2ac-218">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-218">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fd2ac-219">输入</span><span class="sxs-lookup"><span data-stu-id="fd2ac-219">INPUTS</span></span>

### <span data-ttu-id="fd2ac-220">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="fd2ac-220">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fd2ac-221">可以通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-221">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="fd2ac-222">输出</span><span class="sxs-lookup"><span data-stu-id="fd2ac-222">OUTPUTS</span></span>

### <span data-ttu-id="fd2ac-223">PSCustomObject （无）</span><span class="sxs-lookup"><span data-stu-id="fd2ac-223">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="fd2ac-224">如果指定 **PassThru** 参数，则此 cmdlet 将生成一个 **PSCustomObject** 对象，该对象表示已更改的项及其新的属性值。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-224">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="fd2ac-225">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-225">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fd2ac-226">注释</span><span class="sxs-lookup"><span data-stu-id="fd2ac-226">NOTES</span></span>

<span data-ttu-id="fd2ac-227">`Set-ItemProperty` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-227">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fd2ac-228">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-228">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fd2ac-229">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="fd2ac-229">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fd2ac-230">相关链接</span><span class="sxs-lookup"><span data-stu-id="fd2ac-230">RELATED LINKS</span></span>

[<span data-ttu-id="fd2ac-231">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-231">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="fd2ac-232">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-232">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="fd2ac-233">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-233">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="fd2ac-234">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-234">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="fd2ac-235">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-235">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="fd2ac-236">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-236">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="fd2ac-237">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fd2ac-237">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)
