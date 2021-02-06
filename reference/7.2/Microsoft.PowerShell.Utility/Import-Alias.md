---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 20bc5d141b68cab19374afbe44b3472c72bf69bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596211"
---
# <span data-ttu-id="64b9a-102">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="64b9a-102">Import-Alias</span></span>

## <span data-ttu-id="64b9a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="64b9a-103">SYNOPSIS</span></span>
<span data-ttu-id="64b9a-104">从文件导入别名列表。</span><span class="sxs-lookup"><span data-stu-id="64b9a-104">Imports an alias list from a file.</span></span>

## <span data-ttu-id="64b9a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64b9a-105">SYNTAX</span></span>

### <span data-ttu-id="64b9a-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="64b9a-106">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="64b9a-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="64b9a-107">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="64b9a-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64b9a-108">DESCRIPTION</span></span>

<span data-ttu-id="64b9a-109">`Import-Alias`Cmdlet 可从文件导入别名列表。</span><span class="sxs-lookup"><span data-stu-id="64b9a-109">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="64b9a-110">从 Windows PowerShell 3.0 开始，作为一项安全功能， `Import-Alias` 默认情况下不会覆盖现有别名。</span><span class="sxs-lookup"><span data-stu-id="64b9a-110">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="64b9a-111">若要覆盖现有别名，应在使用 **Force** 参数之前先确保该别名文件的内容是安全的。</span><span class="sxs-lookup"><span data-stu-id="64b9a-111">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="64b9a-112">示例</span><span class="sxs-lookup"><span data-stu-id="64b9a-112">EXAMPLES</span></span>

### <span data-ttu-id="64b9a-113">示例 1：从文件导入别名</span><span class="sxs-lookup"><span data-stu-id="64b9a-113">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="64b9a-114">此命令从名为 test.txt 的文件中导入别名信息。</span><span class="sxs-lookup"><span data-stu-id="64b9a-114">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="64b9a-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64b9a-115">PARAMETERS</span></span>

### <span data-ttu-id="64b9a-116">-Force</span><span class="sxs-lookup"><span data-stu-id="64b9a-116">-Force</span></span>

<span data-ttu-id="64b9a-117">允许该 cmdlet 导入已定义的或只读形式的别名。</span><span class="sxs-lookup"><span data-stu-id="64b9a-117">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="64b9a-118">可以使用以下命令显示有关当前定义的别名的信息：</span><span class="sxs-lookup"><span data-stu-id="64b9a-118">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="64b9a-119">如果对应的别名是只读的，则将它显示在 **Options** 属性的值中。</span><span class="sxs-lookup"><span data-stu-id="64b9a-119">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="64b9a-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64b9a-120">-LiteralPath</span></span>

<span data-ttu-id="64b9a-121">指定包含导出的别名信息的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="64b9a-121">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="64b9a-122">与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="64b9a-122">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="64b9a-123">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="64b9a-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="64b9a-124">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="64b9a-124">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="64b9a-125">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="64b9a-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="64b9a-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="64b9a-126">-PassThru</span></span>

<span data-ttu-id="64b9a-127">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="64b9a-127">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="64b9a-128">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="64b9a-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="64b9a-129">-Path</span><span class="sxs-lookup"><span data-stu-id="64b9a-129">-Path</span></span>

<span data-ttu-id="64b9a-130">指定包含导出的别名信息的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="64b9a-130">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="64b9a-131">允许使用通配符，但它们必须解析为单个名称。</span><span class="sxs-lookup"><span data-stu-id="64b9a-131">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="64b9a-132">-Scope</span><span class="sxs-lookup"><span data-stu-id="64b9a-132">-Scope</span></span>

<span data-ttu-id="64b9a-133">指定别名要导入的作用域。</span><span class="sxs-lookup"><span data-stu-id="64b9a-133">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="64b9a-134">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="64b9a-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64b9a-135">全球</span><span class="sxs-lookup"><span data-stu-id="64b9a-135">Global</span></span>
- <span data-ttu-id="64b9a-136">本地</span><span class="sxs-lookup"><span data-stu-id="64b9a-136">Local</span></span>
- <span data-ttu-id="64b9a-137">Script</span><span class="sxs-lookup"><span data-stu-id="64b9a-137">Script</span></span>
- <span data-ttu-id="64b9a-138">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）</span><span class="sxs-lookup"><span data-stu-id="64b9a-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="64b9a-139">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="64b9a-139">The default is Local.</span></span>
<span data-ttu-id="64b9a-140">有关详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="64b9a-140">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="64b9a-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="64b9a-141">-Confirm</span></span>

<span data-ttu-id="64b9a-142">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="64b9a-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="64b9a-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="64b9a-143">-WhatIf</span></span>

<span data-ttu-id="64b9a-144">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="64b9a-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="64b9a-145">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="64b9a-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="64b9a-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64b9a-146">CommonParameters</span></span>

<span data-ttu-id="64b9a-147">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="64b9a-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64b9a-148">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="64b9a-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64b9a-149">输入</span><span class="sxs-lookup"><span data-stu-id="64b9a-149">INPUTS</span></span>

### <span data-ttu-id="64b9a-150">System.String</span><span class="sxs-lookup"><span data-stu-id="64b9a-150">System.String</span></span>

<span data-ttu-id="64b9a-151">可以通过管道将包含路径的字符串传递给 `Import-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="64b9a-151">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="64b9a-152">输出</span><span class="sxs-lookup"><span data-stu-id="64b9a-152">OUTPUTS</span></span>

### <span data-ttu-id="64b9a-153">无或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="64b9a-153">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="64b9a-154">当使用 **Passthru** 参数时，将 `Import-Alias` 返回一个表示别名的 **system.management.automation.aliasinfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="64b9a-154">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="64b9a-155">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="64b9a-155">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="64b9a-156">注释</span><span class="sxs-lookup"><span data-stu-id="64b9a-156">NOTES</span></span>

## <span data-ttu-id="64b9a-157">相关链接</span><span class="sxs-lookup"><span data-stu-id="64b9a-157">RELATED LINKS</span></span>

[<span data-ttu-id="64b9a-158">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="64b9a-158">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="64b9a-159">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="64b9a-159">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="64b9a-160">New-Alias</span><span class="sxs-lookup"><span data-stu-id="64b9a-160">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="64b9a-161">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="64b9a-161">Set-Alias</span></span>](Set-Alias.md)

