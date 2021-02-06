---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 58261830ca65da295aeb85cda22d0a78762e2502
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603614"
---
# <span data-ttu-id="89132-102">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="89132-102">Set-StrictMode</span></span>

## <span data-ttu-id="89132-103">摘要</span><span class="sxs-lookup"><span data-stu-id="89132-103">SYNOPSIS</span></span>
<span data-ttu-id="89132-104">建立并强制执行表达式、脚本和脚本块中的编码规则。</span><span class="sxs-lookup"><span data-stu-id="89132-104">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="89132-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89132-105">SYNTAX</span></span>

### <span data-ttu-id="89132-106">版本 (默认值) </span><span class="sxs-lookup"><span data-stu-id="89132-106">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="89132-107">关</span><span class="sxs-lookup"><span data-stu-id="89132-107">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="89132-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="89132-108">DESCRIPTION</span></span>

<span data-ttu-id="89132-109">`Set-StrictMode`Cmdlet 将为当前作用域和所有子作用域配置严格模式，并将其打开或关闭。</span><span class="sxs-lookup"><span data-stu-id="89132-109">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="89132-110">当 strict 模式处于开启状态时，如果表达式、脚本或脚本块的内容违反了基本的最佳实践编码规则，PowerShell 将生成终止错误。</span><span class="sxs-lookup"><span data-stu-id="89132-110">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="89132-111">使用 **Version** 参数确定强制执行哪些编码规则。</span><span class="sxs-lookup"><span data-stu-id="89132-111">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="89132-112">`Set-PSDebug -Strict` cmdlet 将为全局范围启用严格模式。</span><span class="sxs-lookup"><span data-stu-id="89132-112">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="89132-113">`Set-StrictMode` 仅影响当前作用域及其子作用域。</span><span class="sxs-lookup"><span data-stu-id="89132-113">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="89132-114">因此，你可以在脚本或函数中使用它来重写从全局作用域继承的设置。</span><span class="sxs-lookup"><span data-stu-id="89132-114">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="89132-115">当 `Set-StrictMode` 为 off 时，PowerShell 具有以下行为：</span><span class="sxs-lookup"><span data-stu-id="89132-115">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="89132-116">假定未初始化的变量的值为 0 (零) 或 `$Null` ，具体取决于类型</span><span class="sxs-lookup"><span data-stu-id="89132-116">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="89132-117">对不存在的属性的引用返回 `$Null`</span><span class="sxs-lookup"><span data-stu-id="89132-117">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="89132-118">不正确的函数语法的结果因错误条件而异</span><span class="sxs-lookup"><span data-stu-id="89132-118">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="89132-119">尝试使用数组中的无效索引检索值返回 `$Null`</span><span class="sxs-lookup"><span data-stu-id="89132-119">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="89132-120">示例</span><span class="sxs-lookup"><span data-stu-id="89132-120">EXAMPLES</span></span>

### <span data-ttu-id="89132-121">示例1：将严格模式启用为版本1。0</span><span class="sxs-lookup"><span data-stu-id="89132-121">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

<span data-ttu-id="89132-122">如果将 strict 模式设置为版本1.0，则将尝试引用未初始化的变量失败。</span><span class="sxs-lookup"><span data-stu-id="89132-122">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="89132-123">示例2：将严格模式启用为版本2。0</span><span class="sxs-lookup"><span data-stu-id="89132-123">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

<span data-ttu-id="89132-124">此命令打开严格模式并将其设置为版本2.0。</span><span class="sxs-lookup"><span data-stu-id="89132-124">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="89132-125">因此，如果使用用于函数调用的方法语法（使用括号和逗号）或引用未初始化的变量或不存在的属性，则 PowerShell 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="89132-125">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="89132-126">示例输出显示2.0 版严格模式的效果。</span><span class="sxs-lookup"><span data-stu-id="89132-126">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="89132-127">如果不使用版本 2.0 严格模式，则将值“(3,4)”解释为未向其中添加任何值的单个数组对象。</span><span class="sxs-lookup"><span data-stu-id="89132-127">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="89132-128">使用2.0 版严格模式，会正确地将其解释为用于提交两个值的错误语法。</span><span class="sxs-lookup"><span data-stu-id="89132-128">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="89132-129">如果没有版本2.0，则对字符串的不存在的 **Month** 属性的引用仅返回 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="89132-129">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="89132-130">通过使用版本2.0，该版本被正确解释为引用错误。</span><span class="sxs-lookup"><span data-stu-id="89132-130">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="89132-131">示例3：将严格模式启用为版本3。0</span><span class="sxs-lookup"><span data-stu-id="89132-131">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="89132-132">当 strict 模式设置为 **Off** 时，无效或超出界限索引结果将返回 null 值。</span><span class="sxs-lookup"><span data-stu-id="89132-132">With strict mode set to **Off**, invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

<span data-ttu-id="89132-133">将 strict 模式设置为版本3或更高版本时，无效或超出界限索引会导致错误。</span><span class="sxs-lookup"><span data-stu-id="89132-133">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="89132-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89132-134">PARAMETERS</span></span>

### <span data-ttu-id="89132-135">-Off</span><span class="sxs-lookup"><span data-stu-id="89132-135">-Off</span></span>

<span data-ttu-id="89132-136">指示此 cmdlet 为当前作用域和所有子作用域关闭严格模式。</span><span class="sxs-lookup"><span data-stu-id="89132-136">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89132-137">-Version</span><span class="sxs-lookup"><span data-stu-id="89132-137">-Version</span></span>

<span data-ttu-id="89132-138">指定在严格模式下导致错误的条件。</span><span class="sxs-lookup"><span data-stu-id="89132-138">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="89132-139">此参数接受任何有效的 PowerShell 版本号。</span><span class="sxs-lookup"><span data-stu-id="89132-139">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="89132-140">大于3的任何数字均视为 **最新** 值。</span><span class="sxs-lookup"><span data-stu-id="89132-140">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="89132-141">此参数的有效值为：</span><span class="sxs-lookup"><span data-stu-id="89132-141">The effective values for this parameter are:</span></span>

- <span data-ttu-id="89132-142">1.0</span><span class="sxs-lookup"><span data-stu-id="89132-142">1.0</span></span>
  - <span data-ttu-id="89132-143">禁止对未初始化的变量的引用，不包括字符串中的未初始化变量。</span><span class="sxs-lookup"><span data-stu-id="89132-143">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="89132-144">2.0</span><span class="sxs-lookup"><span data-stu-id="89132-144">2.0</span></span>
  - <span data-ttu-id="89132-145">禁止引用未初始化的变量。</span><span class="sxs-lookup"><span data-stu-id="89132-145">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="89132-146">这包括字符串中的未初始化变量。</span><span class="sxs-lookup"><span data-stu-id="89132-146">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="89132-147">禁止引用对象的不存在的属性。</span><span class="sxs-lookup"><span data-stu-id="89132-147">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="89132-148">禁止使用语法调用方法的函数调用。</span><span class="sxs-lookup"><span data-stu-id="89132-148">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="89132-149">3.0</span><span class="sxs-lookup"><span data-stu-id="89132-149">3.0</span></span>
  - <span data-ttu-id="89132-150">禁止引用未初始化的变量。</span><span class="sxs-lookup"><span data-stu-id="89132-150">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="89132-151">这包括字符串中的未初始化变量。</span><span class="sxs-lookup"><span data-stu-id="89132-151">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="89132-152">禁止引用对象的不存在的属性。</span><span class="sxs-lookup"><span data-stu-id="89132-152">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="89132-153">禁止使用语法调用方法的函数调用。</span><span class="sxs-lookup"><span data-stu-id="89132-153">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="89132-154">禁止范围外或无法解析的数组索引。</span><span class="sxs-lookup"><span data-stu-id="89132-154">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="89132-155">最新</span><span class="sxs-lookup"><span data-stu-id="89132-155">Latest</span></span>
  - <span data-ttu-id="89132-156">选择可用的最新版本。</span><span class="sxs-lookup"><span data-stu-id="89132-156">Selects the latest version available.</span></span> <span data-ttu-id="89132-157">最新版本最严格。</span><span class="sxs-lookup"><span data-stu-id="89132-157">The latest version is the most strict.</span></span> <span data-ttu-id="89132-158">使用此值以确保脚本使用最严格的可用版本，即使在将新版本添加到 PowerShell 时也是如此。</span><span class="sxs-lookup"><span data-stu-id="89132-158">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="89132-159">使用脚本中的 **最新\*\*\*\*版本**。</span><span class="sxs-lookup"><span data-stu-id="89132-159">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="89132-160">**最** 新的含义在 PowerShell 的新版本中可能会发生变化。</span><span class="sxs-lookup"><span data-stu-id="89132-160">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="89132-161">因此，在较新版本的 PowerShell 中运行时，为使用的较旧版本的 PowerShell 编写的脚本 `Set-StrictMode -Version Latest` 将受到更严格的规则的限制。</span><span class="sxs-lookup"><span data-stu-id="89132-161">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89132-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89132-162">CommonParameters</span></span>

<span data-ttu-id="89132-163">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="89132-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89132-164">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="89132-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89132-165">输入</span><span class="sxs-lookup"><span data-stu-id="89132-165">INPUTS</span></span>

### <span data-ttu-id="89132-166">无</span><span class="sxs-lookup"><span data-stu-id="89132-166">None</span></span>

<span data-ttu-id="89132-167">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89132-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="89132-168">输出</span><span class="sxs-lookup"><span data-stu-id="89132-168">OUTPUTS</span></span>

### <span data-ttu-id="89132-169">无</span><span class="sxs-lookup"><span data-stu-id="89132-169">None</span></span>

<span data-ttu-id="89132-170">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="89132-170">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="89132-171">注释</span><span class="sxs-lookup"><span data-stu-id="89132-171">NOTES</span></span>

<span data-ttu-id="89132-172">`Set-StrictMode` 仅在设置它的范围及其子范围内有效。</span><span class="sxs-lookup"><span data-stu-id="89132-172">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="89132-173">有关 PowerShell 中的作用域的详细信息，请参阅 [about_Scopes](about/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="89132-173">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="89132-174">相关链接</span><span class="sxs-lookup"><span data-stu-id="89132-174">RELATED LINKS</span></span>

[<span data-ttu-id="89132-175">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="89132-175">Set-PSDebug</span></span>](Set-PSDebug.md)
