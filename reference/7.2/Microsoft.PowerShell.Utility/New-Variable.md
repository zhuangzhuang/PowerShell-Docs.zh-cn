---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: c77eb9c64022d028c3c4b2de6bf4551886b940e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596620"
---
# <span data-ttu-id="689ac-102">New-Variable</span><span class="sxs-lookup"><span data-stu-id="689ac-102">New-Variable</span></span>

## <span data-ttu-id="689ac-103">摘要</span><span class="sxs-lookup"><span data-stu-id="689ac-103">SYNOPSIS</span></span>
<span data-ttu-id="689ac-104">创建新变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-104">Creates a new variable.</span></span>

## <span data-ttu-id="689ac-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="689ac-105">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="689ac-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="689ac-106">DESCRIPTION</span></span>
<span data-ttu-id="689ac-107">**新变量** Cmdlet 在 PowerShell 中创建新变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-107">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="689ac-108">可以在创建变量时为该变量分配值，也可以在创建变量之后再为该变量分配值或更改其值。</span><span class="sxs-lookup"><span data-stu-id="689ac-108">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="689ac-109">可以使用 **New-Variable** 参数设置变量的属性和作用域以及确定变量为公共变量还是私有变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-109">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="689ac-110">通常，通过键入变量名称及其值（如 `$Var = 3`）来创建新变量，但你可以使用 **New-Variable** cmdlet 来使用其参数。</span><span class="sxs-lookup"><span data-stu-id="689ac-110">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="689ac-111">示例</span><span class="sxs-lookup"><span data-stu-id="689ac-111">EXAMPLES</span></span>

### <span data-ttu-id="689ac-112">示例 1：创建一个变量</span><span class="sxs-lookup"><span data-stu-id="689ac-112">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="689ac-113">此命令将创建一个名为 days 的新变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-113">This command creates a new variable named days.</span></span>
<span data-ttu-id="689ac-114">无需键入 Name 参数。</span><span class="sxs-lookup"><span data-stu-id="689ac-114">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="689ac-115">示例 2：创建一个变量并为其分配一个值</span><span class="sxs-lookup"><span data-stu-id="689ac-115">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="689ac-116">此命令将创建一个名为 zipcode 的变量，并为其分配值 98033。</span><span class="sxs-lookup"><span data-stu-id="689ac-116">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="689ac-117">示例 3：使用 ReadOnly 选项创建一个变量</span><span class="sxs-lookup"><span data-stu-id="689ac-117">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="689ac-118">此示例显示了如何使用 **New-Variable** 的 ReadOnly 选项来防止变量被覆盖。</span><span class="sxs-lookup"><span data-stu-id="689ac-118">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="689ac-119">第一个命令将创建一个名为 Max 的新变量，并将其值设置为 256。</span><span class="sxs-lookup"><span data-stu-id="689ac-119">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="689ac-120">它使用值为 ReadOnly 的 Option 参数。</span><span class="sxs-lookup"><span data-stu-id="689ac-120">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="689ac-121">第二个命令尝试创建另一个具有相同名称的变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-121">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="689ac-122">此命令将返回一个错误，因为已在变量上设置只读选项。</span><span class="sxs-lookup"><span data-stu-id="689ac-122">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="689ac-123">第三个命令使用 Force 参数来覆盖该变量上的只读保护。</span><span class="sxs-lookup"><span data-stu-id="689ac-123">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="689ac-124">在此示例中，用于创建具有相同名称的新变量的命令将成功。</span><span class="sxs-lookup"><span data-stu-id="689ac-124">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="689ac-125">示例 4：创建一个私有变量</span><span class="sxs-lookup"><span data-stu-id="689ac-125">Example 4: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="689ac-126">此命令演示了模块中的私有变量的行为。</span><span class="sxs-lookup"><span data-stu-id="689ac-126">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="689ac-127">该模块包含 Get-Counter cmdlet，它具有一个名为 Counter 的私有变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-127">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="689ac-128">该命令使用值为 Private 的 Visibility 参数来创建变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-128">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="689ac-129">示例输出显示了私有变量的行为。</span><span class="sxs-lookup"><span data-stu-id="689ac-129">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="689ac-130">已加载该模块的用户无法查看或更改 Counter 变量的值，但可以通过该模块中的命令来读取和更改 Counter 变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-130">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="689ac-131">示例5：创建带空格的变量</span><span class="sxs-lookup"><span data-stu-id="689ac-131">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="689ac-132">此命令演示如何创建带有空格的变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-132">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="689ac-133">可以使用 " **获取变量** " cmdlet 或直接通过用大括号分隔变量来访问这些变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-133">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="689ac-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="689ac-134">PARAMETERS</span></span>

### <span data-ttu-id="689ac-135">-Description</span><span class="sxs-lookup"><span data-stu-id="689ac-135">-Description</span></span>
<span data-ttu-id="689ac-136">指定对变量的描述。</span><span class="sxs-lookup"><span data-stu-id="689ac-136">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="689ac-137">-Force</span><span class="sxs-lookup"><span data-stu-id="689ac-137">-Force</span></span>
<span data-ttu-id="689ac-138">指示该 cmdlet 创建一个与现有只读变量具有相同名称的变量。</span><span class="sxs-lookup"><span data-stu-id="689ac-138">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="689ac-139">默认情况下，可以覆盖某个变量，除非该变量的选项值为 ReadOnly 或 Constant。</span><span class="sxs-lookup"><span data-stu-id="689ac-139">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="689ac-140">有关详细信息，请参阅 Option 参数。</span><span class="sxs-lookup"><span data-stu-id="689ac-140">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="689ac-141">-Name</span><span class="sxs-lookup"><span data-stu-id="689ac-141">-Name</span></span>
<span data-ttu-id="689ac-142">指定新变量的名称。</span><span class="sxs-lookup"><span data-stu-id="689ac-142">Specifies a name for the new variable.</span></span>

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

### <span data-ttu-id="689ac-143">-Option</span><span class="sxs-lookup"><span data-stu-id="689ac-143">-Option</span></span>
<span data-ttu-id="689ac-144">指定变量的 **Options** 属性的值。此参数可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="689ac-144">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="689ac-145">无。</span><span class="sxs-lookup"><span data-stu-id="689ac-145">None.</span></span>
<span data-ttu-id="689ac-146">不设置任何选项。</span><span class="sxs-lookup"><span data-stu-id="689ac-146">Sets no options.</span></span>
<span data-ttu-id="689ac-147">（默认值为 None。）</span><span class="sxs-lookup"><span data-stu-id="689ac-147">(None is the default.)</span></span>
- <span data-ttu-id="689ac-148">ReadOnly。</span><span class="sxs-lookup"><span data-stu-id="689ac-148">ReadOnly.</span></span>
<span data-ttu-id="689ac-149">可以删除。</span><span class="sxs-lookup"><span data-stu-id="689ac-149">Can be deleted.</span></span>
<span data-ttu-id="689ac-150">不能更改，除非使用 *Force* 参数。</span><span class="sxs-lookup"><span data-stu-id="689ac-150">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="689ac-151">Private。</span><span class="sxs-lookup"><span data-stu-id="689ac-151">Private.</span></span>
<span data-ttu-id="689ac-152">该变量仅在当前作用域中可用。</span><span class="sxs-lookup"><span data-stu-id="689ac-152">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="689ac-153">AllScope。</span><span class="sxs-lookup"><span data-stu-id="689ac-153">AllScope.</span></span>
<span data-ttu-id="689ac-154">变量将复制到创建的所有新作用域中。</span><span class="sxs-lookup"><span data-stu-id="689ac-154">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="689ac-155">Constant。</span><span class="sxs-lookup"><span data-stu-id="689ac-155">Constant.</span></span>
<span data-ttu-id="689ac-156">无法删除或更改。</span><span class="sxs-lookup"><span data-stu-id="689ac-156">Cannot be deleted or changed.</span></span>
<span data-ttu-id="689ac-157">Constant 仅在创建变量时才有效。</span><span class="sxs-lookup"><span data-stu-id="689ac-157">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="689ac-158">不能将现有变量的选项更改为 Constant。</span><span class="sxs-lookup"><span data-stu-id="689ac-158">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="689ac-159">若要查看会话中所有变量的 **Options** 属性，请键入 `Get-Variable | Format-Table -Property name, options -autosize`。</span><span class="sxs-lookup"><span data-stu-id="689ac-159">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="689ac-160">-PassThru</span><span class="sxs-lookup"><span data-stu-id="689ac-160">-PassThru</span></span>
<span data-ttu-id="689ac-161">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="689ac-161">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="689ac-162">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="689ac-162">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="689ac-163">-Scope</span><span class="sxs-lookup"><span data-stu-id="689ac-163">-Scope</span></span>
<span data-ttu-id="689ac-164">指定新变量的作用域。</span><span class="sxs-lookup"><span data-stu-id="689ac-164">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="689ac-165">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="689ac-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="689ac-166">全局。</span><span class="sxs-lookup"><span data-stu-id="689ac-166">Global.</span></span>
<span data-ttu-id="689ac-167">在全局范围内创建的变量在 PowerShell 进程中的任何位置都是可访问的。</span><span class="sxs-lookup"><span data-stu-id="689ac-167">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="689ac-168">Local。</span><span class="sxs-lookup"><span data-stu-id="689ac-168">Local.</span></span>
<span data-ttu-id="689ac-169">本地作用域是指当前作用域，这可以是任何范围，具体取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="689ac-169">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="689ac-170">脚本。</span><span class="sxs-lookup"><span data-stu-id="689ac-170">Script.</span></span>
<span data-ttu-id="689ac-171">在脚本作用域中创建的变量只能在创建它们的脚本文件或模块内访问。</span><span class="sxs-lookup"><span data-stu-id="689ac-171">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="689ac-172">Private。</span><span class="sxs-lookup"><span data-stu-id="689ac-172">Private.</span></span>
<span data-ttu-id="689ac-173">在私有范围内创建的变量不能在它们所在的作用域之外访问。</span><span class="sxs-lookup"><span data-stu-id="689ac-173">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="689ac-174">你可以使用 "专用范围" 在另一个范围中创建具有相同名称的项的私有版本。</span><span class="sxs-lookup"><span data-stu-id="689ac-174">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="689ac-175">一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父级，2父作用域的父级，依此类推) 。</span><span class="sxs-lookup"><span data-stu-id="689ac-175">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="689ac-176">不能使用负数。</span><span class="sxs-lookup"><span data-stu-id="689ac-176">Negative numbers cannot be used.</span></span>

<span data-ttu-id="689ac-177">当未指定作用域参数时，Local 为默认作用域。</span><span class="sxs-lookup"><span data-stu-id="689ac-177">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="689ac-178">有关详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="689ac-178">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="689ac-179">-Value</span><span class="sxs-lookup"><span data-stu-id="689ac-179">-Value</span></span>
<span data-ttu-id="689ac-180">指定变量初始值。</span><span class="sxs-lookup"><span data-stu-id="689ac-180">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="689ac-181">-Visibility</span><span class="sxs-lookup"><span data-stu-id="689ac-181">-Visibility</span></span>
<span data-ttu-id="689ac-182">确定变量在创建它的会话之外是否可见。</span><span class="sxs-lookup"><span data-stu-id="689ac-182">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="689ac-183">此参数旨在供传递给其他用户的脚本和命令使用。</span><span class="sxs-lookup"><span data-stu-id="689ac-183">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="689ac-184">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="689ac-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="689ac-185">Public。</span><span class="sxs-lookup"><span data-stu-id="689ac-185">Public.</span></span>
<span data-ttu-id="689ac-186">该变量可见。</span><span class="sxs-lookup"><span data-stu-id="689ac-186">The variable is visible.</span></span>
<span data-ttu-id="689ac-187">（默认值为 Public。）</span><span class="sxs-lookup"><span data-stu-id="689ac-187">(Public is the default.)</span></span>
- <span data-ttu-id="689ac-188">Private。</span><span class="sxs-lookup"><span data-stu-id="689ac-188">Private.</span></span>
<span data-ttu-id="689ac-189">该变量不可见。</span><span class="sxs-lookup"><span data-stu-id="689ac-189">The variable is not visible.</span></span>

<span data-ttu-id="689ac-190">当变量为私有时，它不会显示在变量的列表（例如，由 Get-Variable 返回的变量）中或 Variable: 驱动器的显示内容中。</span><span class="sxs-lookup"><span data-stu-id="689ac-190">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="689ac-191">用于读取或更改私有变量的值的命令将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="689ac-191">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="689ac-192">但是，如果已在定义变量的会话中写入可使用私有变量的命令，则用户可以运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="689ac-192">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="689ac-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="689ac-193">-Confirm</span></span>
<span data-ttu-id="689ac-194">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="689ac-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="689ac-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="689ac-195">-WhatIf</span></span>
<span data-ttu-id="689ac-196">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="689ac-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="689ac-197">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="689ac-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="689ac-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="689ac-198">CommonParameters</span></span>
<span data-ttu-id="689ac-199">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="689ac-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="689ac-200">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="689ac-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="689ac-201">输入</span><span class="sxs-lookup"><span data-stu-id="689ac-201">INPUTS</span></span>

### <span data-ttu-id="689ac-202">System.Object</span><span class="sxs-lookup"><span data-stu-id="689ac-202">System.Object</span></span>
<span data-ttu-id="689ac-203">可以通过管道将值传递给 **New-Variable**。</span><span class="sxs-lookup"><span data-stu-id="689ac-203">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="689ac-204">输出</span><span class="sxs-lookup"><span data-stu-id="689ac-204">OUTPUTS</span></span>

### <span data-ttu-id="689ac-205">无或 System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="689ac-205">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="689ac-206">使用 PassThru 参数时，**New-Variable** 将生成一个表示新变量的 **System.Management.Automation.PSVariable** 对象。</span><span class="sxs-lookup"><span data-stu-id="689ac-206">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="689ac-207">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="689ac-207">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="689ac-208">注释</span><span class="sxs-lookup"><span data-stu-id="689ac-208">NOTES</span></span>

## <span data-ttu-id="689ac-209">相关链接</span><span class="sxs-lookup"><span data-stu-id="689ac-209">RELATED LINKS</span></span>

[<span data-ttu-id="689ac-210">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="689ac-210">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="689ac-211">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="689ac-211">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="689ac-212">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="689ac-212">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="689ac-213">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="689ac-213">Set-Variable</span></span>](Set-Variable.md)

