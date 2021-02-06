---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 573bb0054b60e8c17b79da72ebc712c6ef5575a5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595641"
---
# <span data-ttu-id="4755e-102">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="4755e-102">Set-Variable</span></span>

## <span data-ttu-id="4755e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4755e-103">SYNOPSIS</span></span>
<span data-ttu-id="4755e-104">设置变量的值。</span><span class="sxs-lookup"><span data-stu-id="4755e-104">Sets the value of a variable.</span></span> <span data-ttu-id="4755e-105">如果使用请求的名称的变量不存在，则创建该变量。</span><span class="sxs-lookup"><span data-stu-id="4755e-105">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="4755e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4755e-106">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4755e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4755e-107">DESCRIPTION</span></span>

<span data-ttu-id="4755e-108">`Set-Variable`Cmdlet 将值分配给指定的变量或更改当前值。</span><span class="sxs-lookup"><span data-stu-id="4755e-108">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="4755e-109">如果该变量不存在，则该 cmdlet 将创建它。</span><span class="sxs-lookup"><span data-stu-id="4755e-109">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="4755e-110">示例</span><span class="sxs-lookup"><span data-stu-id="4755e-110">EXAMPLES</span></span>

### <span data-ttu-id="4755e-111">示例 1：设置变量并获取其值</span><span class="sxs-lookup"><span data-stu-id="4755e-111">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="4755e-112">这些命令将变量的值设置 `$desc` 为 `A description` ，然后获取该变量的值。</span><span class="sxs-lookup"><span data-stu-id="4755e-112">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="4755e-113">示例 2：设置全局只读变量</span><span class="sxs-lookup"><span data-stu-id="4755e-113">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="4755e-114">此示例将创建一个包含系统上所有进程的全局只读变量，然后显示该变量的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4755e-114">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="4755e-115">该命令使用 `Set-Variable` cmdlet 来创建变量。</span><span class="sxs-lookup"><span data-stu-id="4755e-115">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="4755e-116">它使用 **PassThru** 参数来创建表示新变量的对象，并使用管道运算符 (`|`) 将对象传递给 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4755e-116">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="4755e-117">它使用的 **属性** 参数，其 `Format-List` 值为 all (`*`) ，以显示新创建的变量的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4755e-117">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="4755e-118">值 `(Get-Process)` 括在括号中，以确保在将其存储在变量之前执行。</span><span class="sxs-lookup"><span data-stu-id="4755e-118">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="4755e-119">否则，变量将包含单词 "**get-help**"。</span><span class="sxs-lookup"><span data-stu-id="4755e-119">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="4755e-120">示例 3：了解公共与私有变量</span><span class="sxs-lookup"><span data-stu-id="4755e-120">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="4755e-121">此示例演示如何将变量的可见性更改为 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="4755e-121">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="4755e-122">可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。</span><span class="sxs-lookup"><span data-stu-id="4755e-122">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

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

<span data-ttu-id="4755e-123">此命令显示了如何将变量的可见性更改为 Private。</span><span class="sxs-lookup"><span data-stu-id="4755e-123">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="4755e-124">可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。</span><span class="sxs-lookup"><span data-stu-id="4755e-124">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="4755e-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4755e-125">PARAMETERS</span></span>

### <span data-ttu-id="4755e-126">-Description</span><span class="sxs-lookup"><span data-stu-id="4755e-126">-Description</span></span>

<span data-ttu-id="4755e-127">指定对变量的描述。</span><span class="sxs-lookup"><span data-stu-id="4755e-127">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="4755e-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4755e-128">-Exclude</span></span>

<span data-ttu-id="4755e-129">指定此 cmdlet 将从操作中排除的项数组。</span><span class="sxs-lookup"><span data-stu-id="4755e-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="4755e-130">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="4755e-130">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4755e-131">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="4755e-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="4755e-132">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4755e-132">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4755e-133">-Force</span><span class="sxs-lookup"><span data-stu-id="4755e-133">-Force</span></span>

<span data-ttu-id="4755e-134">允许你创建一个与现有只读变量同名的变量，或更改只读变量的值。</span><span class="sxs-lookup"><span data-stu-id="4755e-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="4755e-135">默认情况下，你可以覆盖某个变量，除非该变量的选项值为 `ReadOnly` 或 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="4755e-135">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="4755e-136">有关详细信息，请参阅 Option 参数。</span><span class="sxs-lookup"><span data-stu-id="4755e-136">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="4755e-137">-Include</span><span class="sxs-lookup"><span data-stu-id="4755e-137">-Include</span></span>

<span data-ttu-id="4755e-138">指定此 cmdlet 将在操作中包含的项数组。</span><span class="sxs-lookup"><span data-stu-id="4755e-138">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="4755e-139">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="4755e-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="4755e-140">输入一个名称或名称模式，例如 `c*`。</span><span class="sxs-lookup"><span data-stu-id="4755e-140">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="4755e-141">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4755e-141">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4755e-142">-Name</span><span class="sxs-lookup"><span data-stu-id="4755e-142">-Name</span></span>

<span data-ttu-id="4755e-143">指定变量名称。</span><span class="sxs-lookup"><span data-stu-id="4755e-143">Specifies the variable name.</span></span>

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

### <span data-ttu-id="4755e-144">-Option</span><span class="sxs-lookup"><span data-stu-id="4755e-144">-Option</span></span>

<span data-ttu-id="4755e-145">指定变量的 **Options** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="4755e-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="4755e-146">有效值是：</span><span class="sxs-lookup"><span data-stu-id="4755e-146">Valid values are:</span></span>

- <span data-ttu-id="4755e-147">`None`：不设置任何选项。</span><span class="sxs-lookup"><span data-stu-id="4755e-147">`None`: Sets no options.</span></span> <span data-ttu-id="4755e-148">（默认值为“None”。）</span><span class="sxs-lookup"><span data-stu-id="4755e-148">("None" is the default.)</span></span>
- <span data-ttu-id="4755e-149">`ReadOnly`：可以删除。</span><span class="sxs-lookup"><span data-stu-id="4755e-149">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="4755e-150">不能更改，除非使用 Force 参数。</span><span class="sxs-lookup"><span data-stu-id="4755e-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="4755e-151">`Constant`：不能删除或更改。</span><span class="sxs-lookup"><span data-stu-id="4755e-151">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="4755e-152">`Constant` 仅当创建变量时才有效。</span><span class="sxs-lookup"><span data-stu-id="4755e-152">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="4755e-153">不能将现有变量的选项更改为 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="4755e-153">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="4755e-154">`Private`：该变量仅在当前范围内可用。</span><span class="sxs-lookup"><span data-stu-id="4755e-154">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="4755e-155">`AllScope`：该变量将复制到任何创建的新作用域。</span><span class="sxs-lookup"><span data-stu-id="4755e-155">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

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

### <span data-ttu-id="4755e-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4755e-156">-PassThru</span></span>

<span data-ttu-id="4755e-157">返回一个表示新变量的对象。</span><span class="sxs-lookup"><span data-stu-id="4755e-157">Returns an object representing the new variable.</span></span> <span data-ttu-id="4755e-158">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="4755e-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4755e-159">-Scope</span><span class="sxs-lookup"><span data-stu-id="4755e-159">-Scope</span></span>

<span data-ttu-id="4755e-160">指定变量的作用域。此参数可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="4755e-160">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4755e-161">全球</span><span class="sxs-lookup"><span data-stu-id="4755e-161">Global</span></span>
- <span data-ttu-id="4755e-162">本地</span><span class="sxs-lookup"><span data-stu-id="4755e-162">Local</span></span>
- <span data-ttu-id="4755e-163">Script</span><span class="sxs-lookup"><span data-stu-id="4755e-163">Script</span></span>
- <span data-ttu-id="4755e-164">专用</span><span class="sxs-lookup"><span data-stu-id="4755e-164">Private</span></span>
- <span data-ttu-id="4755e-165">一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）。</span><span class="sxs-lookup"><span data-stu-id="4755e-165">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="4755e-166">默认值为 Local。</span><span class="sxs-lookup"><span data-stu-id="4755e-166">Local is the default.</span></span>

<span data-ttu-id="4755e-167">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="4755e-167">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="4755e-168">-Value</span><span class="sxs-lookup"><span data-stu-id="4755e-168">-Value</span></span>

<span data-ttu-id="4755e-169">指定变量的值。</span><span class="sxs-lookup"><span data-stu-id="4755e-169">Specifies the value of the variable.</span></span>

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

### <span data-ttu-id="4755e-170">-Visibility</span><span class="sxs-lookup"><span data-stu-id="4755e-170">-Visibility</span></span>

<span data-ttu-id="4755e-171">确定变量在创建它的会话之外是否可见。</span><span class="sxs-lookup"><span data-stu-id="4755e-171">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="4755e-172">此参数旨在供传递给其他用户的脚本和命令使用。</span><span class="sxs-lookup"><span data-stu-id="4755e-172">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="4755e-173">有效值是：</span><span class="sxs-lookup"><span data-stu-id="4755e-173">Valid values are:</span></span>

- <span data-ttu-id="4755e-174">Public：该变量可见。</span><span class="sxs-lookup"><span data-stu-id="4755e-174">Public:  The variable is visible.</span></span> <span data-ttu-id="4755e-175">（默认值为“Public”。）</span><span class="sxs-lookup"><span data-stu-id="4755e-175">("Public" is the default.)</span></span>
- <span data-ttu-id="4755e-176">Private：该变量不可见。</span><span class="sxs-lookup"><span data-stu-id="4755e-176">Private: The variable is not visible.</span></span>

<span data-ttu-id="4755e-177">当变量为私有时，它不会显示在变量列表中，如由返回的变量 `Get-Variable` 或 **变量：** 驱动器的显示。</span><span class="sxs-lookup"><span data-stu-id="4755e-177">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="4755e-178">用于读取或更改私有变量的值的命令将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="4755e-178">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="4755e-179">但是，如果已在定义变量的会话中写入可使用私有变量的命令，则用户可以运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="4755e-179">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="4755e-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4755e-180">-Confirm</span></span>

<span data-ttu-id="4755e-181">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="4755e-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4755e-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4755e-182">-WhatIf</span></span>

<span data-ttu-id="4755e-183">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="4755e-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4755e-184">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="4755e-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4755e-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4755e-185">CommonParameters</span></span>

<span data-ttu-id="4755e-186">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4755e-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4755e-187">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4755e-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4755e-188">输入</span><span class="sxs-lookup"><span data-stu-id="4755e-188">INPUTS</span></span>

### <span data-ttu-id="4755e-189">System.Object</span><span class="sxs-lookup"><span data-stu-id="4755e-189">System.Object</span></span>

<span data-ttu-id="4755e-190">可以通过管道将表示变量值的对象传递给 `Set-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="4755e-190">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="4755e-191">输出</span><span class="sxs-lookup"><span data-stu-id="4755e-191">OUTPUTS</span></span>

### <span data-ttu-id="4755e-192">无或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="4755e-192">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="4755e-193">当使用 **PassThru** 参数时，将 `Set-Variable` 生成一个表示新变量或已更改变量的 **system.management.automation.psvariable** 对象。</span><span class="sxs-lookup"><span data-stu-id="4755e-193">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="4755e-194">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="4755e-194">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4755e-195">注释</span><span class="sxs-lookup"><span data-stu-id="4755e-195">NOTES</span></span>

## <span data-ttu-id="4755e-196">相关链接</span><span class="sxs-lookup"><span data-stu-id="4755e-196">RELATED LINKS</span></span>

[<span data-ttu-id="4755e-197">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="4755e-197">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="4755e-198">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="4755e-198">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="4755e-199">New-Variable</span><span class="sxs-lookup"><span data-stu-id="4755e-199">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="4755e-200">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="4755e-200">Remove-Variable</span></span>](Remove-Variable.md)
