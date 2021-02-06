---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 7f226af3cb221543cdae88930f661e2343d954b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603814"
---
# <span data-ttu-id="80ddb-102">New-Alias</span><span class="sxs-lookup"><span data-stu-id="80ddb-102">New-Alias</span></span>

## <span data-ttu-id="80ddb-103">摘要</span><span class="sxs-lookup"><span data-stu-id="80ddb-103">SYNOPSIS</span></span>
<span data-ttu-id="80ddb-104">创建新别名。</span><span class="sxs-lookup"><span data-stu-id="80ddb-104">Creates a new alias.</span></span>

## <span data-ttu-id="80ddb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80ddb-105">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="80ddb-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="80ddb-106">DESCRIPTION</span></span>

<span data-ttu-id="80ddb-107">**新别名** cmdlet 在当前 PowerShell 会话中创建新别名。</span><span class="sxs-lookup"><span data-stu-id="80ddb-107">The **New-Alias** cmdlet creates a new alias in the current PowerShell session.</span></span>
<span data-ttu-id="80ddb-108">退出会话或关闭 PowerShell 后，不会保存使用 **新别名** 创建的别名。</span><span class="sxs-lookup"><span data-stu-id="80ddb-108">Aliases created by using **New-Alias** are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="80ddb-109">可以使用 Export-Alias cmdlet 来将你的别名信息保存到文件。</span><span class="sxs-lookup"><span data-stu-id="80ddb-109">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="80ddb-110">以后可以使用 **Import-Alias** 来检索已保存的别名信息。</span><span class="sxs-lookup"><span data-stu-id="80ddb-110">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="80ddb-111">示例</span><span class="sxs-lookup"><span data-stu-id="80ddb-111">EXAMPLES</span></span>

### <span data-ttu-id="80ddb-112">示例 1：创建 cmdlet 的别名</span><span class="sxs-lookup"><span data-stu-id="80ddb-112">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="80ddb-113">此命令创建名为“List”的别名来表示 Get-ChildItem cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80ddb-113">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="80ddb-114">示例 2：创建 cmdlet 的只读别名</span><span class="sxs-lookup"><span data-stu-id="80ddb-114">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="80ddb-115">此命令创建名为 W 的别名来表示 Get-WMIObject cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80ddb-115">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="80ddb-116">它为该别名创建了说明、快速 wmi 别名，并使其只读。</span><span class="sxs-lookup"><span data-stu-id="80ddb-116">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="80ddb-117">该命令的最后一行使用 Get-Alias 来获取新别名，并通过管道将其传递给 Format-List 以显示有关它的所有信息。</span><span class="sxs-lookup"><span data-stu-id="80ddb-117">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="80ddb-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="80ddb-118">PARAMETERS</span></span>

### <span data-ttu-id="80ddb-119">-Description</span><span class="sxs-lookup"><span data-stu-id="80ddb-119">-Description</span></span>

<span data-ttu-id="80ddb-120">指定对别名的描述。</span><span class="sxs-lookup"><span data-stu-id="80ddb-120">Specifies a description of the alias.</span></span>
<span data-ttu-id="80ddb-121">你可以键入任意字符串。</span><span class="sxs-lookup"><span data-stu-id="80ddb-121">You can type any string.</span></span>
<span data-ttu-id="80ddb-122">如果描述包含空格，则请将其括在引号中。</span><span class="sxs-lookup"><span data-stu-id="80ddb-122">If the description includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80ddb-123">-Force</span><span class="sxs-lookup"><span data-stu-id="80ddb-123">-Force</span></span>

<span data-ttu-id="80ddb-124">如果命名的别名已存在，则指示该 cmdlet 用作 Set-Alias。</span><span class="sxs-lookup"><span data-stu-id="80ddb-124">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="80ddb-125">-Name</span><span class="sxs-lookup"><span data-stu-id="80ddb-125">-Name</span></span>

<span data-ttu-id="80ddb-126">指定新的别名。</span><span class="sxs-lookup"><span data-stu-id="80ddb-126">Specifies the new alias.</span></span>
<span data-ttu-id="80ddb-127">可以在别名中使用任何字母数字字符，但第一个字符不能为数字。</span><span class="sxs-lookup"><span data-stu-id="80ddb-127">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="80ddb-128">-Option</span><span class="sxs-lookup"><span data-stu-id="80ddb-128">-Option</span></span>

<span data-ttu-id="80ddb-129">指定别名的 **Options** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="80ddb-129">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="80ddb-130">有效值是：</span><span class="sxs-lookup"><span data-stu-id="80ddb-130">Valid values are:</span></span>

- <span data-ttu-id="80ddb-131">无：别名没有 (默认值的约束) </span><span class="sxs-lookup"><span data-stu-id="80ddb-131">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="80ddb-132">ReadOnly：可以删除别名，但不能对其进行更改，除非使用 **Force** 参数</span><span class="sxs-lookup"><span data-stu-id="80ddb-132">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="80ddb-133">常量：别名不能删除或更改</span><span class="sxs-lookup"><span data-stu-id="80ddb-133">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="80ddb-134">Private：别名仅在当前作用域内可用</span><span class="sxs-lookup"><span data-stu-id="80ddb-134">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="80ddb-135">AllScope：将别名复制到任何创建的新作用域</span><span class="sxs-lookup"><span data-stu-id="80ddb-135">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="80ddb-136">未指定：未指定选项</span><span class="sxs-lookup"><span data-stu-id="80ddb-136">Unspecified: The option is not specified</span></span>

<span data-ttu-id="80ddb-137">若要查看会话中所有别名的 **Options** 属性，请键入 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 。</span><span class="sxs-lookup"><span data-stu-id="80ddb-137">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80ddb-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="80ddb-138">-PassThru</span></span>

<span data-ttu-id="80ddb-139">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="80ddb-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="80ddb-140">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="80ddb-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="80ddb-141">-Scope</span><span class="sxs-lookup"><span data-stu-id="80ddb-141">-Scope</span></span>

<span data-ttu-id="80ddb-142">指定新别名的范围。</span><span class="sxs-lookup"><span data-stu-id="80ddb-142">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="80ddb-143">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="80ddb-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="80ddb-144">全球</span><span class="sxs-lookup"><span data-stu-id="80ddb-144">Global</span></span>
- <span data-ttu-id="80ddb-145">本地</span><span class="sxs-lookup"><span data-stu-id="80ddb-145">Local</span></span>
- <span data-ttu-id="80ddb-146">Script</span><span class="sxs-lookup"><span data-stu-id="80ddb-146">Script</span></span>
- <span data-ttu-id="80ddb-147">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）。</span><span class="sxs-lookup"><span data-stu-id="80ddb-147">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="80ddb-148">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="80ddb-148">Local is the default.</span></span>
<span data-ttu-id="80ddb-149">有关详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="80ddb-149">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80ddb-150">-Value</span><span class="sxs-lookup"><span data-stu-id="80ddb-150">-Value</span></span>

<span data-ttu-id="80ddb-151">指定作为别名的 cmdlet 或命令元素的名称。</span><span class="sxs-lookup"><span data-stu-id="80ddb-151">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="80ddb-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="80ddb-152">-Confirm</span></span>

<span data-ttu-id="80ddb-153">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="80ddb-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="80ddb-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="80ddb-154">-WhatIf</span></span>

<span data-ttu-id="80ddb-155">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="80ddb-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="80ddb-156">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="80ddb-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="80ddb-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80ddb-157">CommonParameters</span></span>

<span data-ttu-id="80ddb-158">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="80ddb-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80ddb-159">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="80ddb-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="80ddb-160">输入</span><span class="sxs-lookup"><span data-stu-id="80ddb-160">INPUTS</span></span>

### <span data-ttu-id="80ddb-161">无</span><span class="sxs-lookup"><span data-stu-id="80ddb-161">None</span></span>

<span data-ttu-id="80ddb-162">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80ddb-162">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="80ddb-163">输出</span><span class="sxs-lookup"><span data-stu-id="80ddb-163">OUTPUTS</span></span>

### <span data-ttu-id="80ddb-164">无或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="80ddb-164">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="80ddb-165">使用 Passthru 参数时，**New-Alias** 将生成表示新别名的 **System.Management.Automation.AliasInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="80ddb-165">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="80ddb-166">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="80ddb-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="80ddb-167">注释</span><span class="sxs-lookup"><span data-stu-id="80ddb-167">NOTES</span></span>

* <span data-ttu-id="80ddb-168">若要创建新别名，请使用 `Set-Alias` 或 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="80ddb-168">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="80ddb-169">若要更改别名，请使用 `Set-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="80ddb-169">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="80ddb-170">若要删除别名，请使用 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="80ddb-170">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="80ddb-171">相关链接</span><span class="sxs-lookup"><span data-stu-id="80ddb-171">RELATED LINKS</span></span>

[<span data-ttu-id="80ddb-172">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="80ddb-172">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="80ddb-173">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="80ddb-173">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="80ddb-174">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="80ddb-174">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="80ddb-175">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="80ddb-175">Set-Alias</span></span>](Set-Alias.md)

