---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 7b6f639d1c5685e341260c056a1dd0a17fe9f46d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597656"
---
# <span data-ttu-id="6d30e-102">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="6d30e-102">Get-Alias</span></span>

## <span data-ttu-id="6d30e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6d30e-103">SYNOPSIS</span></span>
<span data-ttu-id="6d30e-104">获取当前会话的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-104">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="6d30e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d30e-105">SYNTAX</span></span>

### <span data-ttu-id="6d30e-106">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="6d30e-106">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="6d30e-107">定义</span><span class="sxs-lookup"><span data-stu-id="6d30e-107">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6d30e-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6d30e-108">DESCRIPTION</span></span>

<span data-ttu-id="6d30e-109">**获取别名** cmdlet 获取当前会话中的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-109">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="6d30e-110">这包括内置别名、已设置或导入的别名，以及已添加到 PowerShell 配置文件中的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-110">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="6d30e-111">默认情况下， **获取** 别名会获得一个别名并返回命令名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-111">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="6d30e-112">当你使用 *定义* 参数时， **Get-Alias** 将使用命令名称并返回其别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-112">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="6d30e-113">从 Windows PowerShell 3.0 开始，" **获取别名** " 以格式显示不带连字符的别名， `<alias> -> <definition>` 以便更轻松地找到所需的信息。</span><span class="sxs-lookup"><span data-stu-id="6d30e-113">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="6d30e-114">示例</span><span class="sxs-lookup"><span data-stu-id="6d30e-114">EXAMPLES</span></span>

### <span data-ttu-id="6d30e-115">示例1：获取当前会话中的所有别名</span><span class="sxs-lookup"><span data-stu-id="6d30e-115">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="6d30e-116">此命令获取当前会话中的所有别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-116">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="6d30e-117">输出显示了 `<alias> -> <definition>` 在 Windows PowerShell 3.0 中引入的格式。</span><span class="sxs-lookup"><span data-stu-id="6d30e-117">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="6d30e-118">此格式仅适用于不含有连字符的别名，因为带有连字符的别名通常为 cmdlet 和函数（而不是昵称）的首选名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-118">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="6d30e-119">示例2：按名称获取别名</span><span class="sxs-lookup"><span data-stu-id="6d30e-119">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="6d30e-120">此命令获取以 gp 或 sp 开头的所有别名（以 ps 结尾的别名除外）。</span><span class="sxs-lookup"><span data-stu-id="6d30e-120">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="6d30e-121">示例3：获取 cmdlet 的别名</span><span class="sxs-lookup"><span data-stu-id="6d30e-121">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="6d30e-122">此命令获取 Get-childitem cmdlet 的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-122">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="6d30e-123">默认情况下， **获取** 别名时会获取项名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-123">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="6d30e-124">*定义* 参数会在你知道项名称时获取别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-124">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="6d30e-125">示例4：按属性获取别名</span><span class="sxs-lookup"><span data-stu-id="6d30e-125">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="6d30e-126">此命令获取 Options 属性值为 ReadOnly 的所有别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-126">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="6d30e-127">此命令提供了一种快速方法来查找 PowerShell 内置的别名，因为它们具有 ReadOnly 选项。</span><span class="sxs-lookup"><span data-stu-id="6d30e-127">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="6d30e-128">Options 只 **是获取 system.management.automation.aliasinfo** 对象的一个属性。</span><span class="sxs-lookup"><span data-stu-id="6d30e-128">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="6d30e-129">若要查找 System.management.automation.aliasinfo 对象的所有属性和方法，请键入 `Get-Alias | get-member` 。</span><span class="sxs-lookup"><span data-stu-id="6d30e-129">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="6d30e-130">示例5：按名称获取别名并按开始字母筛选</span><span class="sxs-lookup"><span data-stu-id="6d30e-130">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="6d30e-131">此示例获取所有以“-PSSession”结尾的命令别名，但以“e”开头的别名除外。</span><span class="sxs-lookup"><span data-stu-id="6d30e-131">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="6d30e-132">该命令使用 *Scope* 参数将命令应用到全局作用域中。</span><span class="sxs-lookup"><span data-stu-id="6d30e-132">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="6d30e-133">当你想要获取会话中的别名时，这对脚本比较有用。</span><span class="sxs-lookup"><span data-stu-id="6d30e-133">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="6d30e-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6d30e-134">PARAMETERS</span></span>

### <span data-ttu-id="6d30e-135">-Definition</span><span class="sxs-lookup"><span data-stu-id="6d30e-135">-Definition</span></span>

<span data-ttu-id="6d30e-136">获取指定项的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-136">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="6d30e-137">输入 cmdlet、函数、脚本、文件或可执行文件的名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-137">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="6d30e-138">此参数名为 *definition*，因为它在别名对象的 Definition 属性中搜索项目名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-138">This parameter is called *Definition*, because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6d30e-139">-Exclude</span><span class="sxs-lookup"><span data-stu-id="6d30e-139">-Exclude</span></span>

<span data-ttu-id="6d30e-140">忽略指定项。</span><span class="sxs-lookup"><span data-stu-id="6d30e-140">Omits the specified items.</span></span>
<span data-ttu-id="6d30e-141">此参数的值对 Name 和 Definition 参数进行限定。</span><span class="sxs-lookup"><span data-stu-id="6d30e-141">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="6d30e-142">输入名称、定义或模式，例如“s\*”。</span><span class="sxs-lookup"><span data-stu-id="6d30e-142">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="6d30e-143">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6d30e-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="6d30e-144">-Name</span><span class="sxs-lookup"><span data-stu-id="6d30e-144">-Name</span></span>

<span data-ttu-id="6d30e-145">指定此 cmdlet 获取的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-145">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="6d30e-146">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="6d30e-146">Wildcards are permitted.</span></span>
<span data-ttu-id="6d30e-147">默认情况下， `Get-Alias` 检索为当前会话定义的所有别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-147">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="6d30e-148">参数名称 **名称** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="6d30e-148">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="6d30e-149">还可以通过管道将别名命名为 `Get-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="6d30e-149">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6d30e-150">-Scope</span><span class="sxs-lookup"><span data-stu-id="6d30e-150">-Scope</span></span>

<span data-ttu-id="6d30e-151">指定此 cmdlet 为其获取别名的作用域。</span><span class="sxs-lookup"><span data-stu-id="6d30e-151">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="6d30e-152">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="6d30e-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6d30e-153">全球</span><span class="sxs-lookup"><span data-stu-id="6d30e-153">Global</span></span>
- <span data-ttu-id="6d30e-154">本地</span><span class="sxs-lookup"><span data-stu-id="6d30e-154">Local</span></span>
- <span data-ttu-id="6d30e-155">Script</span><span class="sxs-lookup"><span data-stu-id="6d30e-155">Script</span></span>
- <span data-ttu-id="6d30e-156">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）</span><span class="sxs-lookup"><span data-stu-id="6d30e-156">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="6d30e-157">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="6d30e-157">Local is the default.</span></span>
<span data-ttu-id="6d30e-158">有关详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="6d30e-158">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6d30e-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d30e-159">CommonParameters</span></span>

<span data-ttu-id="6d30e-160">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6d30e-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d30e-161">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6d30e-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d30e-162">输入</span><span class="sxs-lookup"><span data-stu-id="6d30e-162">INPUTS</span></span>

### <span data-ttu-id="6d30e-163">System.String</span><span class="sxs-lookup"><span data-stu-id="6d30e-163">System.String</span></span>

<span data-ttu-id="6d30e-164">可以通过管道将别名命名为 **获取别名**。</span><span class="sxs-lookup"><span data-stu-id="6d30e-164">You can pipe alias names to **Get-Alias**.</span></span>

## <span data-ttu-id="6d30e-165">输出</span><span class="sxs-lookup"><span data-stu-id="6d30e-165">OUTPUTS</span></span>

### <span data-ttu-id="6d30e-166">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="6d30e-166">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="6d30e-167">**Get-Alias** 返回表示每个别名的对象。</span><span class="sxs-lookup"><span data-stu-id="6d30e-167">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="6d30e-168">**Get-alias** 为每个别名返回相同的对象，但 PowerShell 使用基于箭头的格式来显示不带连字符的别名的名称。</span><span class="sxs-lookup"><span data-stu-id="6d30e-168">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="6d30e-169">注释</span><span class="sxs-lookup"><span data-stu-id="6d30e-169">NOTES</span></span>

- <span data-ttu-id="6d30e-170">若要创建新的别名，请使用 Set-Alias 或 New-Alias。</span><span class="sxs-lookup"><span data-stu-id="6d30e-170">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="6d30e-171">若要删除别名，请使用 Remove-Item。</span><span class="sxs-lookup"><span data-stu-id="6d30e-171">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="6d30e-172">基于箭头的别名名称格式不适用于含有连字符的别名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-172">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="6d30e-173">这些很可能是 cmdlet 和函数（而不是典型的缩写或昵称）的首选替代名。</span><span class="sxs-lookup"><span data-stu-id="6d30e-173">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="6d30e-174">相关链接</span><span class="sxs-lookup"><span data-stu-id="6d30e-174">RELATED LINKS</span></span>

[<span data-ttu-id="6d30e-175">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="6d30e-175">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="6d30e-176">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="6d30e-176">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="6d30e-177">New-Alias</span><span class="sxs-lookup"><span data-stu-id="6d30e-177">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="6d30e-178">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="6d30e-178">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="6d30e-179">Alias 提供程序</span><span class="sxs-lookup"><span data-stu-id="6d30e-179">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="6d30e-180">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="6d30e-180">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

