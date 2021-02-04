---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: c90a2f49c95333e45893e186d6e1f1da4b3fe41a
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771830"
---
# <span data-ttu-id="697cb-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="697cb-103">Set-Variable</span></span>

## <span data-ttu-id="697cb-104">摘要</span><span class="sxs-lookup"><span data-stu-id="697cb-104">SYNOPSIS</span></span>
<span data-ttu-id="697cb-105">设置变量的值。</span><span class="sxs-lookup"><span data-stu-id="697cb-105">Sets the value of a variable.</span></span> <span data-ttu-id="697cb-106">如果使用请求的名称的变量不存在，则创建该变量。</span><span class="sxs-lookup"><span data-stu-id="697cb-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="697cb-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="697cb-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="697cb-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="697cb-108">DESCRIPTION</span></span>

<span data-ttu-id="697cb-109">`Set-Variable`Cmdlet 将值分配给指定的变量或更改当前值。</span><span class="sxs-lookup"><span data-stu-id="697cb-109">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="697cb-110">如果该变量不存在，则该 cmdlet 将创建它。</span><span class="sxs-lookup"><span data-stu-id="697cb-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="697cb-111">示例</span><span class="sxs-lookup"><span data-stu-id="697cb-111">EXAMPLES</span></span>

### <span data-ttu-id="697cb-112">示例 1：设置变量并获取其值</span><span class="sxs-lookup"><span data-stu-id="697cb-112">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="697cb-113">这些命令将变量的值设置 `$desc` 为 `A description` ，然后获取该变量的值。</span><span class="sxs-lookup"><span data-stu-id="697cb-113">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="697cb-114">示例 2：设置全局只读变量</span><span class="sxs-lookup"><span data-stu-id="697cb-114">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="697cb-115">此示例将创建一个包含系统上所有进程的全局只读变量，然后显示该变量的所有属性。</span><span class="sxs-lookup"><span data-stu-id="697cb-115">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option Constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="697cb-116">该命令使用 `Set-Variable` cmdlet 来创建变量。</span><span class="sxs-lookup"><span data-stu-id="697cb-116">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="697cb-117">它使用 **PassThru** 参数来创建表示新变量的对象，并使用管道运算符 (`|`) 将对象传递给 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="697cb-117">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="697cb-118">它使用的 **属性** 参数，其 `Format-List` 值为 all (`*`) ，以显示新创建的变量的所有属性。</span><span class="sxs-lookup"><span data-stu-id="697cb-118">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="697cb-119">值 `(Get-Process)` 括在括号中，以确保在将其存储在变量之前执行。</span><span class="sxs-lookup"><span data-stu-id="697cb-119">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="697cb-120">否则，变量将包含单词 "**get-help**"。</span><span class="sxs-lookup"><span data-stu-id="697cb-120">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="697cb-121">示例 3：了解公共与私有变量</span><span class="sxs-lookup"><span data-stu-id="697cb-121">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="697cb-122">此示例演示如何将变量的可见性更改为 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="697cb-122">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="697cb-123">可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。</span><span class="sxs-lookup"><span data-stu-id="697cb-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="697cb-124">此命令显示了如何将变量的可见性更改为 Private。</span><span class="sxs-lookup"><span data-stu-id="697cb-124">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="697cb-125">可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。</span><span class="sxs-lookup"><span data-stu-id="697cb-125">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="697cb-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="697cb-126">PARAMETERS</span></span>

### <span data-ttu-id="697cb-127">-Description</span><span class="sxs-lookup"><span data-stu-id="697cb-127">-Description</span></span>

<span data-ttu-id="697cb-128">指定对变量的描述。</span><span class="sxs-lookup"><span data-stu-id="697cb-128">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="697cb-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="697cb-129">-Exclude</span></span>

<span data-ttu-id="697cb-130">指定此 cmdlet 将从操作中排除的项数组。</span><span class="sxs-lookup"><span data-stu-id="697cb-130">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="697cb-131">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="697cb-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="697cb-132">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="697cb-132">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="697cb-133">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="697cb-133">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="697cb-134">-Force</span><span class="sxs-lookup"><span data-stu-id="697cb-134">-Force</span></span>

<span data-ttu-id="697cb-135">允许你创建一个与现有只读变量同名的变量，或更改只读变量的值。</span><span class="sxs-lookup"><span data-stu-id="697cb-135">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="697cb-136">默认情况下，你可以覆盖某个变量，除非该变量的选项值为 `ReadOnly` 或 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="697cb-136">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="697cb-137">有关详细信息，请参阅 Option 参数。</span><span class="sxs-lookup"><span data-stu-id="697cb-137">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="697cb-138">-Include</span><span class="sxs-lookup"><span data-stu-id="697cb-138">-Include</span></span>

<span data-ttu-id="697cb-139">指定此 cmdlet 将在操作中包含的项数组。</span><span class="sxs-lookup"><span data-stu-id="697cb-139">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="697cb-140">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="697cb-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="697cb-141">输入一个名称或名称模式，例如 `c*`。</span><span class="sxs-lookup"><span data-stu-id="697cb-141">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="697cb-142">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="697cb-142">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="697cb-143">-Name</span><span class="sxs-lookup"><span data-stu-id="697cb-143">-Name</span></span>

<span data-ttu-id="697cb-144">指定变量名称。</span><span class="sxs-lookup"><span data-stu-id="697cb-144">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="697cb-145">-Option</span><span class="sxs-lookup"><span data-stu-id="697cb-145">-Option</span></span>

<span data-ttu-id="697cb-146">指定变量的 **Options** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="697cb-146">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="697cb-147">有效值是：</span><span class="sxs-lookup"><span data-stu-id="697cb-147">Valid values are:</span></span>

- <span data-ttu-id="697cb-148">`None`：不设置任何选项。</span><span class="sxs-lookup"><span data-stu-id="697cb-148">`None`: Sets no options.</span></span> <span data-ttu-id="697cb-149">（默认值为“None”。）</span><span class="sxs-lookup"><span data-stu-id="697cb-149">("None" is the default.)</span></span>
- <span data-ttu-id="697cb-150">`ReadOnly`：可以删除。</span><span class="sxs-lookup"><span data-stu-id="697cb-150">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="697cb-151">不能更改，除非使用 Force 参数。</span><span class="sxs-lookup"><span data-stu-id="697cb-151">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="697cb-152">`Constant`：不能删除或更改。</span><span class="sxs-lookup"><span data-stu-id="697cb-152">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="697cb-153">`Constant` 仅当创建变量时才有效。</span><span class="sxs-lookup"><span data-stu-id="697cb-153">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="697cb-154">不能将现有变量的选项更改为 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="697cb-154">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="697cb-155">`Private`：该变量仅在当前范围内可用。</span><span class="sxs-lookup"><span data-stu-id="697cb-155">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="697cb-156">`AllScope`：该变量将复制到任何创建的新作用域。</span><span class="sxs-lookup"><span data-stu-id="697cb-156">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="697cb-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="697cb-157">-PassThru</span></span>

<span data-ttu-id="697cb-158">返回一个表示新变量的对象。</span><span class="sxs-lookup"><span data-stu-id="697cb-158">Returns an object representing the new variable.</span></span> <span data-ttu-id="697cb-159">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="697cb-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="697cb-160">-Scope</span><span class="sxs-lookup"><span data-stu-id="697cb-160">-Scope</span></span>

<span data-ttu-id="697cb-161">指定变量的作用域。此参数可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="697cb-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="697cb-162">全球</span><span class="sxs-lookup"><span data-stu-id="697cb-162">Global</span></span>
- <span data-ttu-id="697cb-163">本地</span><span class="sxs-lookup"><span data-stu-id="697cb-163">Local</span></span>
- <span data-ttu-id="697cb-164">Script</span><span class="sxs-lookup"><span data-stu-id="697cb-164">Script</span></span>
- <span data-ttu-id="697cb-165">专用</span><span class="sxs-lookup"><span data-stu-id="697cb-165">Private</span></span>
- <span data-ttu-id="697cb-166">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）。</span><span class="sxs-lookup"><span data-stu-id="697cb-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="697cb-167">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="697cb-167">Local is the default.</span></span>

<span data-ttu-id="697cb-168">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="697cb-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="697cb-169">-Value</span><span class="sxs-lookup"><span data-stu-id="697cb-169">-Value</span></span>

<span data-ttu-id="697cb-170">指定变量的值。</span><span class="sxs-lookup"><span data-stu-id="697cb-170">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="697cb-171">-Visibility</span><span class="sxs-lookup"><span data-stu-id="697cb-171">-Visibility</span></span>

<span data-ttu-id="697cb-172">确定变量在创建它的会话之外是否可见。</span><span class="sxs-lookup"><span data-stu-id="697cb-172">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="697cb-173">此参数旨在供传递给其他用户的脚本和命令使用。</span><span class="sxs-lookup"><span data-stu-id="697cb-173">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="697cb-174">有效值是：</span><span class="sxs-lookup"><span data-stu-id="697cb-174">Valid values are:</span></span>

- <span data-ttu-id="697cb-175">Public：该变量可见。</span><span class="sxs-lookup"><span data-stu-id="697cb-175">Public:  The variable is visible.</span></span> <span data-ttu-id="697cb-176">（默认值为“Public”。）</span><span class="sxs-lookup"><span data-stu-id="697cb-176">("Public" is the default.)</span></span>
- <span data-ttu-id="697cb-177">Private：该变量不可见。</span><span class="sxs-lookup"><span data-stu-id="697cb-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="697cb-178">当变量为私有时，它不会显示在变量列表中，如由返回的变量 `Get-Variable` 或 **变量：** 驱动器的显示。</span><span class="sxs-lookup"><span data-stu-id="697cb-178">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="697cb-179">用于读取或更改私有变量的值的命令将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="697cb-179">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="697cb-180">但是，如果已在定义变量的会话中写入可使用私有变量的命令，则用户可以运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="697cb-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="697cb-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="697cb-181">-Confirm</span></span>

<span data-ttu-id="697cb-182">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="697cb-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="697cb-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="697cb-183">-WhatIf</span></span>

<span data-ttu-id="697cb-184">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="697cb-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="697cb-185">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="697cb-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="697cb-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="697cb-186">CommonParameters</span></span>

<span data-ttu-id="697cb-187">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="697cb-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="697cb-188">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="697cb-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="697cb-189">输入</span><span class="sxs-lookup"><span data-stu-id="697cb-189">INPUTS</span></span>

### <span data-ttu-id="697cb-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="697cb-190">System.Object</span></span>

<span data-ttu-id="697cb-191">可以通过管道将表示变量值的对象传递给 `Set-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="697cb-191">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="697cb-192">输出</span><span class="sxs-lookup"><span data-stu-id="697cb-192">OUTPUTS</span></span>

### <span data-ttu-id="697cb-193">无或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="697cb-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="697cb-194">当使用 **PassThru** 参数时，将 `Set-Variable` 生成一个表示新变量或已更改变量的 **system.management.automation.psvariable** 对象。</span><span class="sxs-lookup"><span data-stu-id="697cb-194">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="697cb-195">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="697cb-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="697cb-196">注释</span><span class="sxs-lookup"><span data-stu-id="697cb-196">NOTES</span></span>

## <span data-ttu-id="697cb-197">相关链接</span><span class="sxs-lookup"><span data-stu-id="697cb-197">RELATED LINKS</span></span>

[<span data-ttu-id="697cb-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="697cb-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="697cb-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="697cb-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="697cb-200">New-Variable</span><span class="sxs-lookup"><span data-stu-id="697cb-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="697cb-201">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="697cb-201">Remove-Variable</span></span>](Remove-Variable.md)
