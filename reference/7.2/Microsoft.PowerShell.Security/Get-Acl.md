---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596429"
---
# <span data-ttu-id="3d5bd-102">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="3d5bd-102">Get-Acl</span></span>

## <span data-ttu-id="3d5bd-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3d5bd-103">SYNOPSIS</span></span>
<span data-ttu-id="3d5bd-104">获取某个资源（如文件或注册表项）的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-104">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="3d5bd-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d5bd-105">SYNTAX</span></span>

### <span data-ttu-id="3d5bd-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="3d5bd-106">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="3d5bd-107">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="3d5bd-107">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3d5bd-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3d5bd-108">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3d5bd-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3d5bd-109">DESCRIPTION</span></span>

<span data-ttu-id="3d5bd-110">`Get-Acl`Cmdlet 可获取表示文件或资源的安全描述符的对象。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-110">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="3d5bd-111">安全描述符包含资源的访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-111">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="3d5bd-112">ACL 可指定用户和用户组访问资源所需的权限。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-112">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="3d5bd-113">从 Windows PowerShell 3.0 开始，可以使用的 **InputObject** 参数 `Get-Acl` 来获取不具有路径的对象的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-113">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="3d5bd-114">示例</span><span class="sxs-lookup"><span data-stu-id="3d5bd-114">EXAMPLES</span></span>

### <span data-ttu-id="3d5bd-115">示例 1-获取文件夹的 ACL</span><span class="sxs-lookup"><span data-stu-id="3d5bd-115">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="3d5bd-116">此示例获取目录的安全描述符 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-116">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="3d5bd-117">示例 2-使用通配符获取文件夹的 ACL</span><span class="sxs-lookup"><span data-stu-id="3d5bd-117">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="3d5bd-118">此示例获取 `.log` `C:\Windows` 目录中名称以开头的所有文件的 PowerShell 路径和 SDDL `s` 。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-118">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="3d5bd-119">该命令使用 `Get-Acl` cmdlet 来获取表示每个日志文件的安全描述符的对象。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-119">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="3d5bd-120">它使用管道运算符 (`|`) 将结果发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-120">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="3d5bd-121">命令使用的 **属性** 参数 `Format-List` 来仅显示每个安全描述符对象的 **PsPath** 和 **SDDL** 属性。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-121">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="3d5bd-122">通常在 PowerShell 中使用列表，因为在表中，长值会被截断。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-122">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="3d5bd-123">**SDDL** 值对系统管理员很有价值，因为它们是包含安全描述符中所有信息的简单文本字符串。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-123">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="3d5bd-124">正因如此，它们易于传递和存储，并且可在需要时对它们进行分析。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-124">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="3d5bd-125">示例 3-获取 ACL 审核条目计数</span><span class="sxs-lookup"><span data-stu-id="3d5bd-125">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="3d5bd-126">此示例获取 `.log` 目录中名称以开头的文件的安全描述符 `C:\Windows` `s` 。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-126">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="3d5bd-127">它使用 **Audit** 参数从安全描述符中的 SACL 获取审核记录。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-127">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="3d5bd-128">然后，它使用 `ForEach-Object` cmdlet 来计算与每个文件相关联的审核记录的数目。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-128">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="3d5bd-129">结果是一个表示每个日志文件的审核记录数的数字列表。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-129">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="3d5bd-130">示例 4-获取注册表项的 ACL</span><span class="sxs-lookup"><span data-stu-id="3d5bd-130">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="3d5bd-131">此示例使用 `Get-Acl` cmdlet 来获取控件子项 (`HKLM:\SYSTEM\CurrentControlSet\Control` 注册表) 的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-131">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="3d5bd-132">Path 参数指定 Control 子项。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-132">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="3d5bd-133">管道运算符 (`|`) 传递指向命令的安全描述符 `Get-Acl` `Format-List` ，该命令将安全描述符的属性设置为列表格式，使其易于读取。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-133">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="3d5bd-134">示例 5-使用 **InputObject** 获取 ACL</span><span class="sxs-lookup"><span data-stu-id="3d5bd-134">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="3d5bd-135">此示例使用的 **InputObject** 参数 `Get-Acl` 来获取存储子系统对象的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-135">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="3d5bd-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d5bd-136">PARAMETERS</span></span>

### <span data-ttu-id="3d5bd-137">-Audit</span><span class="sxs-lookup"><span data-stu-id="3d5bd-137">-Audit</span></span>

<span data-ttu-id="3d5bd-138">从系统访问控制列表 (SACL) 获取安全描述符的审核数据。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-138">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="3d5bd-139">-Exclude</span><span class="sxs-lookup"><span data-stu-id="3d5bd-139">-Exclude</span></span>

<span data-ttu-id="3d5bd-140">忽略指定项。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-140">Omits the specified items.</span></span> <span data-ttu-id="3d5bd-141">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-141">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3d5bd-142">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-142">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="3d5bd-143">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="3d5bd-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="3d5bd-144">-Filter</span></span>

<span data-ttu-id="3d5bd-145">以提供程序的格式或语言指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-145">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="3d5bd-146">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-146">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3d5bd-147">筛选器的语法（包括通配符的使用）取决于提供程序。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-147">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="3d5bd-148">筛选器比其他参数更有效，因为提供程序是在获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-148">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="3d5bd-149">-Include</span><span class="sxs-lookup"><span data-stu-id="3d5bd-149">-Include</span></span>

<span data-ttu-id="3d5bd-150">仅获取指定项。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-150">Gets only the specified items.</span></span> <span data-ttu-id="3d5bd-151">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3d5bd-152">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="3d5bd-153">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="3d5bd-154">-Path</span><span class="sxs-lookup"><span data-stu-id="3d5bd-154">-Path</span></span>

<span data-ttu-id="3d5bd-155">指定资源的路径。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-155">Specifies the path to a resource.</span></span> <span data-ttu-id="3d5bd-156">`Get-Acl` 获取由路径指示的资源的安全说明符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-156">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="3d5bd-157">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-157">Wildcards are permitted.</span></span> <span data-ttu-id="3d5bd-158">如果省略 **Path** 参数，将 `Get-Acl` 获取当前目录的安全说明符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-158">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="3d5bd-159">参数名（“Path”）为可选项。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-159">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3d5bd-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3d5bd-160">-InputObject</span></span>

<span data-ttu-id="3d5bd-161">获取指定对象的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-161">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="3d5bd-162">请输入包含对象的变量或可获取该对象的命令。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-162">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="3d5bd-163">不能将路径以外的对象传递给 `Get-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-163">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="3d5bd-164">而应该在命令中显式使用 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-164">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="3d5bd-165">此参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d5bd-166">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3d5bd-166">-LiteralPath</span></span>

<span data-ttu-id="3d5bd-167">指定资源的路径。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-167">Specifies the path to a resource.</span></span> <span data-ttu-id="3d5bd-168">与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-168">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="3d5bd-169">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-169">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="3d5bd-170">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-170">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3d5bd-171">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-171">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="3d5bd-172">此参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-172">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3d5bd-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d5bd-173">CommonParameters</span></span>

<span data-ttu-id="3d5bd-174">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d5bd-175">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d5bd-176">输入</span><span class="sxs-lookup"><span data-stu-id="3d5bd-176">INPUTS</span></span>

### <span data-ttu-id="3d5bd-177">System.String</span><span class="sxs-lookup"><span data-stu-id="3d5bd-177">System.String</span></span>

<span data-ttu-id="3d5bd-178">可以通过管道将包含路径的字符串传递给 `Get-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-178">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="3d5bd-179">输出</span><span class="sxs-lookup"><span data-stu-id="3d5bd-179">OUTPUTS</span></span>

### <span data-ttu-id="3d5bd-180">Accesscontrol-namespace. Accesscontrol-namespace. System.security.accesscontrol.directorysecurity，，accesscontrol-namespace. RegistrySecurity.。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-180">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="3d5bd-181">`Get-Acl` 返回一个对象，该对象表示其获取的 Acl。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-181">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="3d5bd-182">对象类型取决于 ACL 类型。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-182">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="3d5bd-183">注释</span><span class="sxs-lookup"><span data-stu-id="3d5bd-183">NOTES</span></span>

<span data-ttu-id="3d5bd-184">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="3d5bd-185">默认情况下，会 `Get-Acl` 显示资源的 PowerShell 路径 (`<provider>::<resource-path>`) 、资源的所有者和 "访问权限"、"自定义" 访问控制列表中的访问控制项的列表 (数组)  (资源的 "DACL) "。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="3d5bd-186">DACL 列表由资源所有者控制。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="3d5bd-187">将结果的格式设置为列表时， (`Get-Acl | Format-List`) 除了路径、所有者和访问列表外，PowerShell 还会显示以下属性和属性值：</span><span class="sxs-lookup"><span data-stu-id="3d5bd-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="3d5bd-188">**Group**：所有者的安全组。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-188">**Group**: The security group of the owner.</span></span>
- <span data-ttu-id="3d5bd-189">**Audit**：系统访问控制列表 (SACL) 中项的列表（数组）。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-189">**Audit**:  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="3d5bd-190">SACL 指定 Windows 为其生成审核记录的访问尝试的类型。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="3d5bd-191">**Sddl**：在单个文本字符串中以安全描述符定义语言格式显示的资源的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-191">**Sddl**: The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="3d5bd-192">PowerShell 使用安全描述符的 **GetSddlForm** 方法来获取此数据。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="3d5bd-193">由于 `Get-Acl` 文件系统和注册表提供程序支持，因此你可以使用 `Get-Acl` 查看文件系统对象（如文件和目录）的 ACL 和注册表对象（如注册表项和条目）。</span><span class="sxs-lookup"><span data-stu-id="3d5bd-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="3d5bd-194">相关链接</span><span class="sxs-lookup"><span data-stu-id="3d5bd-194">RELATED LINKS</span></span>

[<span data-ttu-id="3d5bd-195">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="3d5bd-195">Set-Acl</span></span>](Set-Acl.md)
