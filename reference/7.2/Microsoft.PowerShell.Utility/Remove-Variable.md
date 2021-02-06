---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 6b9d351b5092d96d7698a28d3de63a493d566c6d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597884"
---
# <span data-ttu-id="5d516-102">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="5d516-102">Remove-Variable</span></span>

## <span data-ttu-id="5d516-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5d516-103">SYNOPSIS</span></span>
<span data-ttu-id="5d516-104">删除变量及其值。</span><span class="sxs-lookup"><span data-stu-id="5d516-104">Deletes a variable and its value.</span></span>

## <span data-ttu-id="5d516-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d516-105">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5d516-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5d516-106">DESCRIPTION</span></span>

<span data-ttu-id="5d516-107">`Remove-Variable`Cmdlet 从定义变量的作用域中删除变量及其值，如当前会话。</span><span class="sxs-lookup"><span data-stu-id="5d516-107">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="5d516-108">你不能使用此 cmdlet 删除设置为常量或由系统所拥有的变量。</span><span class="sxs-lookup"><span data-stu-id="5d516-108">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="5d516-109">示例</span><span class="sxs-lookup"><span data-stu-id="5d516-109">EXAMPLES</span></span>

### <span data-ttu-id="5d516-110">示例1：删除变量</span><span class="sxs-lookup"><span data-stu-id="5d516-110">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="5d516-111">此命令删除 `$Smp` 变量。</span><span class="sxs-lookup"><span data-stu-id="5d516-111">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="5d516-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5d516-112">PARAMETERS</span></span>

### <span data-ttu-id="5d516-113">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5d516-113">-Exclude</span></span>

<span data-ttu-id="5d516-114">指定此 cmdlet 从操作中省略的项的数组。</span><span class="sxs-lookup"><span data-stu-id="5d516-114">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="5d516-115">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="5d516-115">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="5d516-116">请输入名称元素或模式，例如“s\*”。</span><span class="sxs-lookup"><span data-stu-id="5d516-116">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="5d516-117">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5d516-117">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="5d516-118">-Force</span><span class="sxs-lookup"><span data-stu-id="5d516-118">-Force</span></span>

<span data-ttu-id="5d516-119">指示该 cmdlet 删除变量，即使该变量是只读的。</span><span class="sxs-lookup"><span data-stu-id="5d516-119">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="5d516-120">即使使用 **Force** 参数，cmdlet 也无法删除常量。</span><span class="sxs-lookup"><span data-stu-id="5d516-120">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="5d516-121">-Include</span><span class="sxs-lookup"><span data-stu-id="5d516-121">-Include</span></span>

<span data-ttu-id="5d516-122">指定此 cmdlet 在操作中删除的项的数组。</span><span class="sxs-lookup"><span data-stu-id="5d516-122">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="5d516-123">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="5d516-123">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="5d516-124">输入名称元素或模式，例如 "s \*"。</span><span class="sxs-lookup"><span data-stu-id="5d516-124">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="5d516-125">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5d516-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="5d516-126">-Name</span><span class="sxs-lookup"><span data-stu-id="5d516-126">-Name</span></span>

<span data-ttu-id="5d516-127">指定要删除的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="5d516-127">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="5d516-128"> (**名称**) 的参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="5d516-128">The parameter name (**Name**) is optional.</span></span>
<span data-ttu-id="5d516-129">允许使用通配符</span><span class="sxs-lookup"><span data-stu-id="5d516-129">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="5d516-130">-Scope</span><span class="sxs-lookup"><span data-stu-id="5d516-130">-Scope</span></span>

<span data-ttu-id="5d516-131">仅获取指定作用域中的变量。</span><span class="sxs-lookup"><span data-stu-id="5d516-131">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="5d516-132">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="5d516-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5d516-133">全球</span><span class="sxs-lookup"><span data-stu-id="5d516-133">Global</span></span>
- <span data-ttu-id="5d516-134">本地</span><span class="sxs-lookup"><span data-stu-id="5d516-134">Local</span></span>
- <span data-ttu-id="5d516-135">Script</span><span class="sxs-lookup"><span data-stu-id="5d516-135">Script</span></span>
- <span data-ttu-id="5d516-136">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）</span><span class="sxs-lookup"><span data-stu-id="5d516-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="5d516-137">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="5d516-137">Local is the default.</span></span> <span data-ttu-id="5d516-138">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="5d516-138">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="5d516-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5d516-139">-Confirm</span></span>

<span data-ttu-id="5d516-140">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="5d516-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5d516-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5d516-141">-WhatIf</span></span>

<span data-ttu-id="5d516-142">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="5d516-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5d516-143">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="5d516-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5d516-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d516-144">CommonParameters</span></span>

<span data-ttu-id="5d516-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5d516-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d516-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5d516-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d516-147">输入</span><span class="sxs-lookup"><span data-stu-id="5d516-147">INPUTS</span></span>

### <span data-ttu-id="5d516-148">System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="5d516-148">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="5d516-149">可以通过管道将变量对象传递给 `Remove-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="5d516-149">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="5d516-150">输出</span><span class="sxs-lookup"><span data-stu-id="5d516-150">OUTPUTS</span></span>

### <span data-ttu-id="5d516-151">无</span><span class="sxs-lookup"><span data-stu-id="5d516-151">None</span></span>

<span data-ttu-id="5d516-152">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="5d516-152">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="5d516-153">注释</span><span class="sxs-lookup"><span data-stu-id="5d516-153">NOTES</span></span>

- <span data-ttu-id="5d516-154">更改仅影响当前作用域，例如会话。</span><span class="sxs-lookup"><span data-stu-id="5d516-154">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="5d516-155">若要从所有会话中删除某个变量，请将 `Remove-Variable` 命令添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="5d516-155">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="5d516-156">还可以 `Remove-Variable` 通过其内置别名来引用 `rv` 。</span><span class="sxs-lookup"><span data-stu-id="5d516-156">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="5d516-157">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="5d516-157">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="5d516-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="5d516-158">RELATED LINKS</span></span>

[<span data-ttu-id="5d516-159">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="5d516-159">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="5d516-160">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="5d516-160">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="5d516-161">New-Variable</span><span class="sxs-lookup"><span data-stu-id="5d516-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="5d516-162">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="5d516-162">Set-Variable</span></span>](Set-Variable.md)
