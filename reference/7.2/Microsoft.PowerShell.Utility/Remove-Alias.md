---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 0ce13bef77e9ef9647809336aed650833dab51f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596402"
---
# <span data-ttu-id="0c152-102">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-102">Remove-Alias</span></span>

## <span data-ttu-id="0c152-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0c152-103">SYNOPSIS</span></span>
<span data-ttu-id="0c152-104">删除当前会话中的别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-104">Remove an alias from the current session.</span></span>

## <span data-ttu-id="0c152-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c152-105">SYNTAX</span></span>

### <span data-ttu-id="0c152-106">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="0c152-106">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="0c152-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c152-107">DESCRIPTION</span></span>

<span data-ttu-id="0c152-108">`Remove-Alias`Cmdlet 可从当前 PowerShell 会话中删除别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-108">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="0c152-109">若要删除 **选项** 属性设置为 **ReadOnly** 的别名，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="0c152-109">To remove an alias with the **Option** property set to **ReadOnly**, use the **Force** parameter.</span></span>

<span data-ttu-id="0c152-110">`Remove-Alias`Cmdlet 是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="0c152-110">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="0c152-111">示例</span><span class="sxs-lookup"><span data-stu-id="0c152-111">EXAMPLES</span></span>

### <span data-ttu-id="0c152-112">示例 1-删除别名</span><span class="sxs-lookup"><span data-stu-id="0c152-112">Example 1 - Remove an alias</span></span>

<span data-ttu-id="0c152-113">此示例将删除一个名为 `del` 的别名，该别名表示 `Remove-Item` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c152-113">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="0c152-114">示例 2-删除所有非常量的别名</span><span class="sxs-lookup"><span data-stu-id="0c152-114">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="0c152-115">此示例从当前 PowerShell 会话中删除所有别名，但 " **Options** " 属性设置为 " **常量**" 的别名除外。</span><span class="sxs-lookup"><span data-stu-id="0c152-115">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant**.</span></span> <span data-ttu-id="0c152-116">运行该命令后，可在其他 PowerShell 会话或新的 PowerShell 会话中使用别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-116">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="0c152-117">`Get-Alias` 获取 PowerShell 会话中的所有别名，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="0c152-117">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="0c152-118">`Where-Object` 使用脚本块，自动变量 (`$_`) 和 **选项** 属性表示当前管道对象。</span><span class="sxs-lookup"><span data-stu-id="0c152-118">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="0c152-119">参数 **NE** (不等于) ，则选择未将 **选项** 值设置为 **常量** 的对象。</span><span class="sxs-lookup"><span data-stu-id="0c152-119">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant**.</span></span> <span data-ttu-id="0c152-120">`Remove-Alias` 使用 **Force** 参数从 PowerShell 会话中删除别名，包括只读别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-120">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="0c152-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c152-121">PARAMETERS</span></span>

### <span data-ttu-id="0c152-122">-Force</span><span class="sxs-lookup"><span data-stu-id="0c152-122">-Force</span></span>

<span data-ttu-id="0c152-123">指示该 cmdlet 删除别名，包括 **选项** 属性设置为 **ReadOnly** 的别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-123">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly**.</span></span> <span data-ttu-id="0c152-124">**Force** 参数无法删除 **选项** 属性设置为 **常量** 的别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-124">The **Force** parameter can't remove an alias with an **Option** property set to **Constant**.</span></span>

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

### <span data-ttu-id="0c152-125">-Name</span><span class="sxs-lookup"><span data-stu-id="0c152-125">-Name</span></span>

<span data-ttu-id="0c152-126">指定要删除的别名的名称。</span><span class="sxs-lookup"><span data-stu-id="0c152-126">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0c152-127">-Scope</span><span class="sxs-lookup"><span data-stu-id="0c152-127">-Scope</span></span>

<span data-ttu-id="0c152-128">仅影响指定范围内的别名。</span><span class="sxs-lookup"><span data-stu-id="0c152-128">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="0c152-129">默认作用域为 **本地**。</span><span class="sxs-lookup"><span data-stu-id="0c152-129">The default scope is **Local**.</span></span> <span data-ttu-id="0c152-130">有关详细信息，请参阅 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="0c152-130">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="0c152-131">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0c152-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0c152-132">全球</span><span class="sxs-lookup"><span data-stu-id="0c152-132">Global</span></span>
- <span data-ttu-id="0c152-133">本地</span><span class="sxs-lookup"><span data-stu-id="0c152-133">Local</span></span>
- <span data-ttu-id="0c152-134">Script</span><span class="sxs-lookup"><span data-stu-id="0c152-134">Script</span></span>
- <span data-ttu-id="0c152-135">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）</span><span class="sxs-lookup"><span data-stu-id="0c152-135">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="0c152-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c152-136">CommonParameters</span></span>

<span data-ttu-id="0c152-137">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0c152-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c152-138">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0c152-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c152-139">输入</span><span class="sxs-lookup"><span data-stu-id="0c152-139">INPUTS</span></span>

### <span data-ttu-id="0c152-140">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0c152-140">System.String[]</span></span>

<span data-ttu-id="0c152-141">可以通过管道将别名对象传递给 **删除别名**。</span><span class="sxs-lookup"><span data-stu-id="0c152-141">You can pipe an alias object to **Remove-Alias**.</span></span>

## <span data-ttu-id="0c152-142">输出</span><span class="sxs-lookup"><span data-stu-id="0c152-142">OUTPUTS</span></span>

### <span data-ttu-id="0c152-143">无</span><span class="sxs-lookup"><span data-stu-id="0c152-143">None</span></span>

<span data-ttu-id="0c152-144">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="0c152-144">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="0c152-145">注释</span><span class="sxs-lookup"><span data-stu-id="0c152-145">NOTES</span></span>

<span data-ttu-id="0c152-146">更改仅影响当前作用域。</span><span class="sxs-lookup"><span data-stu-id="0c152-146">Changes only affect the current scope.</span></span> <span data-ttu-id="0c152-147">若要从所有会话中删除别名，请将一个 **删除别名** 命令添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="0c152-147">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="0c152-148">有关详细信息，请参阅 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="0c152-148">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="0c152-149">相关链接</span><span class="sxs-lookup"><span data-stu-id="0c152-149">RELATED LINKS</span></span>

[<span data-ttu-id="0c152-150">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0c152-150">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="0c152-151">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-151">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="0c152-152">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-152">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="0c152-153">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-153">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="0c152-154">New-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-154">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="0c152-155">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="0c152-155">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="0c152-156">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0c152-156">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

