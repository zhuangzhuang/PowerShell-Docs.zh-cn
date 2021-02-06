---
description: 描述变量如何存储可在 PowerShell 中使用的值。
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 8d8c8d3098d33980c9c802bf00846a21e8baeb40
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596415"
---
# <a name="about-variables"></a><span data-ttu-id="68d85-103">关于变量</span><span class="sxs-lookup"><span data-stu-id="68d85-103">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="68d85-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="68d85-104">Short description</span></span>

<span data-ttu-id="68d85-105">描述变量如何存储可在 PowerShell 中使用的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-105">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="68d85-106">长说明</span><span class="sxs-lookup"><span data-stu-id="68d85-106">Long description</span></span>

<span data-ttu-id="68d85-107">可以在 PowerShell 变量中存储所有类型的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-107">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="68d85-108">例如，存储命令的结果，并存储命令和表达式中使用的元素，例如名称、路径、设置和值。</span><span class="sxs-lookup"><span data-stu-id="68d85-108">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="68d85-109">变量是存储值的内存单位。</span><span class="sxs-lookup"><span data-stu-id="68d85-109">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="68d85-110">在 PowerShell 中，变量由以美元符号开头的文本字符串表示 (`$`) ，如 `$a` 、 `$process` 或 `$my_var` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-110">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="68d85-111">变量名称不区分大小写，并且可以包含空格和特殊字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-111">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="68d85-112">但是，包含特殊字符和空格的变量名称难以使用，应避免使用。</span><span class="sxs-lookup"><span data-stu-id="68d85-112">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="68d85-113">有关详细信息，请参阅 [包含特殊字符的变量名称](#variable-names-that-include-special-characters)。</span><span class="sxs-lookup"><span data-stu-id="68d85-113">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="68d85-114">在 PowerShell 中有几种不同类型的变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-114">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="68d85-115">用户创建的变量：用户创建的变量由用户创建和维护。</span><span class="sxs-lookup"><span data-stu-id="68d85-115">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="68d85-116">默认情况下，在 powershell 命令行中创建的变量仅在 PowerShell 窗口处于打开状态时才存在。</span><span class="sxs-lookup"><span data-stu-id="68d85-116">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="68d85-117">当 PowerShell 窗口关闭时，这些变量将被删除。</span><span class="sxs-lookup"><span data-stu-id="68d85-117">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="68d85-118">若要保存某个变量，请将其添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="68d85-118">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="68d85-119">你还可以在具有全局、脚本或本地范围的脚本中创建变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-119">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="68d85-120">自动变量：自动变量存储 PowerShell 的状态。</span><span class="sxs-lookup"><span data-stu-id="68d85-120">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="68d85-121">这些变量由 PowerShell 创建，PowerShell 会根据需要更改它们的值以保持其准确性。</span><span class="sxs-lookup"><span data-stu-id="68d85-121">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="68d85-122">用户不能更改这些变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-122">Users can't change the value of these variables.</span></span> <span data-ttu-id="68d85-123">例如， `$PSHOME` 变量存储 PowerShell 安装目录的路径。</span><span class="sxs-lookup"><span data-stu-id="68d85-123">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="68d85-124">有关自动变量的详细信息、列表和说明，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-124">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="68d85-125">首选项变量：首选项为 PowerShell 存储用户首选项。</span><span class="sxs-lookup"><span data-stu-id="68d85-125">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="68d85-126">这些变量由 PowerShell 创建，并使用默认值进行填充。</span><span class="sxs-lookup"><span data-stu-id="68d85-126">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="68d85-127">用户可以更改这些变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-127">Users can change the values of these variables.</span></span> <span data-ttu-id="68d85-128">例如， `$MaximumHistoryCount` 变量确定会话历史记录中的最大项数。</span><span class="sxs-lookup"><span data-stu-id="68d85-128">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="68d85-129">有关首选项变量的详细信息、列表和说明，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-129">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="68d85-130">使用变量</span><span class="sxs-lookup"><span data-stu-id="68d85-130">Working with variables</span></span>

<span data-ttu-id="68d85-131">若要创建新变量，请使用赋值语句为变量赋值。</span><span class="sxs-lookup"><span data-stu-id="68d85-131">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="68d85-132">不需要在使用变量之前先对其进行声明。</span><span class="sxs-lookup"><span data-stu-id="68d85-132">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="68d85-133">所有变量的默认值为 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-133">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="68d85-134">若要获取 PowerShell 会话中所有变量的列表，请键入 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-134">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="68d85-135">将显示变量名称，其中不含前面的货币 (`$` 用于引用变量的) 符号。</span><span class="sxs-lookup"><span data-stu-id="68d85-135">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="68d85-136">例如：</span><span class="sxs-lookup"><span data-stu-id="68d85-136">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="68d85-137">变量用于存储命令的结果。</span><span class="sxs-lookup"><span data-stu-id="68d85-137">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="68d85-138">例如：</span><span class="sxs-lookup"><span data-stu-id="68d85-138">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="68d85-139">若要显示变量的值，请键入变量名称，其前面带有美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="68d85-139">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="68d85-140">例如：</span><span class="sxs-lookup"><span data-stu-id="68d85-140">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="68d85-141">若要更改变量的值，请将新值分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-141">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="68d85-142">下面的示例显示变量的值 `$MyVariable` ，更改变量的值，然后显示新值。</span><span class="sxs-lookup"><span data-stu-id="68d85-142">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="68d85-143">若要删除变量的值，请使用 `Clear-Variable` cmdlet 或将值更改为 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-143">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="68d85-144">若要删除变量，请使用 " [删除变量](xref:Microsoft.PowerShell.Utility.Remove-Variable) " 或 " [删除项](xref:Microsoft.PowerShell.Management.Remove-Item)"。</span><span class="sxs-lookup"><span data-stu-id="68d85-144">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="68d85-145">变量类型</span><span class="sxs-lookup"><span data-stu-id="68d85-145">Types of variables</span></span>

<span data-ttu-id="68d85-146">可以在变量中存储任何类型的对象，包括整数、字符串、数组和哈希表。</span><span class="sxs-lookup"><span data-stu-id="68d85-146">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="68d85-147">和表示进程、服务、事件日志和计算机的对象。</span><span class="sxs-lookup"><span data-stu-id="68d85-147">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="68d85-148">PowerShell 变量是松散类型化的，这意味着它们并不限于特定类型的对象。</span><span class="sxs-lookup"><span data-stu-id="68d85-148">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="68d85-149">单个变量甚至可以同时包含不同类型的对象的集合或数组。</span><span class="sxs-lookup"><span data-stu-id="68d85-149">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="68d85-150">变量的数据类型由变量值的 .NET 类型决定。</span><span class="sxs-lookup"><span data-stu-id="68d85-150">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="68d85-151">若要查看变量的对象类型，请使用 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member)。</span><span class="sxs-lookup"><span data-stu-id="68d85-151">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="68d85-152">例如：</span><span class="sxs-lookup"><span data-stu-id="68d85-152">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="68d85-153">您可以使用类型属性和强制转换表示法来确保变量只能包含特定的对象类型或可转换为该类型的对象。</span><span class="sxs-lookup"><span data-stu-id="68d85-153">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="68d85-154">如果尝试分配另一个类型的值，则 PowerShell 会尝试将值转换为其类型。</span><span class="sxs-lookup"><span data-stu-id="68d85-154">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="68d85-155">如果无法转换类型，赋值语句将失败。</span><span class="sxs-lookup"><span data-stu-id="68d85-155">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="68d85-156">若要使用强制转换表示法，请在赋值语句左侧)  (的变量名称之前输入类型名称（括在括号中）。</span><span class="sxs-lookup"><span data-stu-id="68d85-156">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="68d85-157">下面的示例创建一个 `$number` 变量，该变量只能包含整数、只能包含字符串的变量 `$words` ，以及只能 `$dates` 包含 **DateTime** 对象的变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-157">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="68d85-158">在命令和表达式中使用变量</span><span class="sxs-lookup"><span data-stu-id="68d85-158">Using variables in commands and expressions</span></span>

<span data-ttu-id="68d85-159">若要在命令或表达式中使用变量，请键入变量名称，前面加上美元 (`$`) 符号。</span><span class="sxs-lookup"><span data-stu-id="68d85-159">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="68d85-160">如果变量名和美元符号没有用引号引起来，或者它们括在双引号 (`"`) 标记中，则在命令或表达式中使用该变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-160">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="68d85-161">如果变量名和美元符号用单引号引起 (`'`) 标记，则在表达式中使用变量名。</span><span class="sxs-lookup"><span data-stu-id="68d85-161">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="68d85-162">有关在 PowerShell 中使用引号的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-162">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="68d85-163">此示例获取变量的值 `$PROFILE` ，它是 powershell 控制台中 powershell 用户配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="68d85-163">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="68d85-164">在此示例中，显示了两个命令，可在 **notepad.exe** 中打开 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="68d85-164">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="68d85-165">带有双引号 () 标记的示例 `"` 使用变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-165">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="68d85-166">下面的示例使用单引号 (将 `'` 变量视为文本的) 标记。</span><span class="sxs-lookup"><span data-stu-id="68d85-166">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="68d85-167">包含特殊字符的变量名称</span><span class="sxs-lookup"><span data-stu-id="68d85-167">Variable names that include special characters</span></span>

<span data-ttu-id="68d85-168">变量名称以美元 (`$`) 符号开头，可以包含字母数字字符和特殊字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-168">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="68d85-169">变量名称长度仅受可用内存的限制。</span><span class="sxs-lookup"><span data-stu-id="68d85-169">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="68d85-170">最佳做法是，变量名称只能包含字母数字字符和下划线 (`_`) 字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-170">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="68d85-171">包含空格和其他特殊字符的变量名称难以使用，应避免使用。</span><span class="sxs-lookup"><span data-stu-id="68d85-171">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="68d85-172">字母数字变量名可以包含以下字符：</span><span class="sxs-lookup"><span data-stu-id="68d85-172">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="68d85-173">这些类别中的 Unicode 字符： **Lu**、 **Ll**、 **Lt**、 **Lm**、 **Lo** 或 **Nd**。</span><span class="sxs-lookup"><span data-stu-id="68d85-173">Unicode characters from these categories: **Lu**, **Ll**, **Lt**, **Lm**, **Lo**, or **Nd**.</span></span>
- <span data-ttu-id="68d85-174">下划线 (`_`) 字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-174">Underscore (`_`) character.</span></span>
- <span data-ttu-id="68d85-175">问号 (`?`) 字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-175">Question mark (`?`) character.</span></span>

<span data-ttu-id="68d85-176">下面的列表包含 Unicode 类别说明。</span><span class="sxs-lookup"><span data-stu-id="68d85-176">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="68d85-177">有关详细信息，请参阅 [system.globalization.unicodecategory](/dotnet/api/system.globalization.unicodecategory)。</span><span class="sxs-lookup"><span data-stu-id="68d85-177">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="68d85-178">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="68d85-178">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="68d85-179">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="68d85-179">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="68d85-180">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="68d85-180">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="68d85-181">**Lm** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="68d85-181">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="68d85-182">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="68d85-182">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="68d85-183">**Nd** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="68d85-183">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="68d85-184">若要创建或显示包含空格或特殊字符的变量名称，请使用大括号将该变量名称括 (`{}`) 字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-184">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="68d85-185">大括号直接 PowerShell 将变量名称的字符解释为文本。</span><span class="sxs-lookup"><span data-stu-id="68d85-185">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="68d85-186">特殊字符变量名称可以包含以下字符：</span><span class="sxs-lookup"><span data-stu-id="68d85-186">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="68d85-187">任何 Unicode 字符，但以下情况除外：</span><span class="sxs-lookup"><span data-stu-id="68d85-187">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="68d85-188">右大括号 (`}`) 字符 (U + 007D) 。</span><span class="sxs-lookup"><span data-stu-id="68d85-188">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="68d85-189">反撇号 (`` ` ``) 字符 (U + 0060) 。</span><span class="sxs-lookup"><span data-stu-id="68d85-189">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="68d85-190">反撇号用于对 Unicode 字符进行转义，以使它们被视为文本。</span><span class="sxs-lookup"><span data-stu-id="68d85-190">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="68d85-191">PowerShell 包含 `$$` `$?` `$^` `$_` 包含字母数字字符和特殊字符的保留变量，如、、和。</span><span class="sxs-lookup"><span data-stu-id="68d85-191">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="68d85-192">有关详细信息，请参阅 [about_Automatic_Variables](about_automatic_variables.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-192">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="68d85-193">例如，以下命令将创建名为的变量 `save-items` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-193">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="68d85-194">需要大括号 (`{}`) ，因为变量名称包含连字符 (`-`) 特殊字符。</span><span class="sxs-lookup"><span data-stu-id="68d85-194">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="68d85-195">以下命令将获取由环境变量表示的目录中的子项目 `ProgramFiles(x86)` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-195">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="68d85-196">若要引用包含大括号的变量名，请将变量名称括在大括号中，并使用反撇号字符来转义大括号。</span><span class="sxs-lookup"><span data-stu-id="68d85-196">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="68d85-197">例如，若要创建名为 type 的变量 `this{value}is` ：</span><span class="sxs-lookup"><span data-stu-id="68d85-197">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="68d85-198">变量和范围</span><span class="sxs-lookup"><span data-stu-id="68d85-198">Variables and scope</span></span>

<span data-ttu-id="68d85-199">默认情况下，变量仅在创建它们的范围内可用。</span><span class="sxs-lookup"><span data-stu-id="68d85-199">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="68d85-200">例如，在函数中创建的变量仅在函数内可用。</span><span class="sxs-lookup"><span data-stu-id="68d85-200">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="68d85-201">在脚本中创建的变量仅在脚本内可用。</span><span class="sxs-lookup"><span data-stu-id="68d85-201">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="68d85-202">如果脚本为点，则将变量添加到当前作用域。</span><span class="sxs-lookup"><span data-stu-id="68d85-202">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="68d85-203">有关详细信息，请参阅 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-203">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="68d85-204">您可以使用作用域修饰符来更改变量的默认作用域。</span><span class="sxs-lookup"><span data-stu-id="68d85-204">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="68d85-205">下面的表达式创建一个名为的变量 `Computers` 。</span><span class="sxs-lookup"><span data-stu-id="68d85-205">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="68d85-206">尽管变量是在脚本或函数中创建的，但它也具有全局作用域。</span><span class="sxs-lookup"><span data-stu-id="68d85-206">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="68d85-207">对于任何执行进程外的脚本或命令，都需要 `Using` 范围修饰符来嵌入调用会话范围内的变量值，以便使会话代码不能访问它们。</span><span class="sxs-lookup"><span data-stu-id="68d85-207">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="68d85-208">有关详细信息，请参阅 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-208">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="68d85-209">保存变量</span><span class="sxs-lookup"><span data-stu-id="68d85-209">Saving variables</span></span>

<span data-ttu-id="68d85-210">你创建的变量仅在创建它们的会话中可用。</span><span class="sxs-lookup"><span data-stu-id="68d85-210">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="68d85-211">关闭会话时，它们会丢失。</span><span class="sxs-lookup"><span data-stu-id="68d85-211">They're lost when you close your session.</span></span>

<span data-ttu-id="68d85-212">若要在启动的每个 PowerShell 会话中创建变量，请将变量添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="68d85-212">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="68d85-213">例如，若要 `$VerbosePreference` 在每个 powershell 会话中更改变量的值，请将以下命令添加到 powershell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="68d85-213">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="68d85-214">可以通过 `$PROFILE` 在文本编辑器中打开文件（如 **notepad.exe**），将此命令添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="68d85-214">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="68d85-215">有关 PowerShell 配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="68d85-215">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="68d85-216">变量：驱动器</span><span class="sxs-lookup"><span data-stu-id="68d85-216">The Variable: drive</span></span>

<span data-ttu-id="68d85-217">PowerShell 变量提供程序创建的 `Variable:` 驱动器的外观和行为类似于文件系统驱动器，但它包含会话中的变量及其值。</span><span class="sxs-lookup"><span data-stu-id="68d85-217">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="68d85-218">若要切换到 `Variable:` 驱动器，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="68d85-218">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="68d85-219">若要列出驱动器中的项和变量 `Variable:` ，请使用 `Get-Item` 或 `Get-ChildItem` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d85-219">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="68d85-220">若要获取特定变量的值，请使用文件系统表示法指定驱动器名称和变量名称。</span><span class="sxs-lookup"><span data-stu-id="68d85-220">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="68d85-221">例如，若要获取 `$PSCulture` 自动变量，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="68d85-221">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="68d85-222">若要显示有关 `Variable:` 驱动器和 PowerShell Variable 提供程序的详细信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="68d85-222">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="68d85-223">具有提供程序路径的变量语法</span><span class="sxs-lookup"><span data-stu-id="68d85-223">Variable syntax with provider paths</span></span>

<span data-ttu-id="68d85-224">你可以为提供程序路径加上前缀 (`$`) 符号，并访问实现 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 接口的任何提供程序的内容。</span><span class="sxs-lookup"><span data-stu-id="68d85-224">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="68d85-225">以下内置 PowerShell 提供程序支持此表示法：</span><span class="sxs-lookup"><span data-stu-id="68d85-225">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="68d85-226">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="68d85-226">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="68d85-227">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="68d85-227">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="68d85-228">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="68d85-228">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="68d85-229">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="68d85-229">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="68d85-230">变量 cmdlet</span><span class="sxs-lookup"><span data-stu-id="68d85-230">The variable cmdlets</span></span>

<span data-ttu-id="68d85-231">PowerShell 包括一组旨在管理变量的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68d85-231">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="68d85-232">若要列出这些 cmdlet，请键入：</span><span class="sxs-lookup"><span data-stu-id="68d85-232">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="68d85-233">若要获取特定 cmdlet 的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="68d85-233">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="68d85-234">Cmdlet 名称</span><span class="sxs-lookup"><span data-stu-id="68d85-234">Cmdlet Name</span></span>       | <span data-ttu-id="68d85-235">说明</span><span class="sxs-lookup"><span data-stu-id="68d85-235">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="68d85-236">删除变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-236">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="68d85-237">获取当前控制台中的变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-237">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="68d85-238">创建新变量。</span><span class="sxs-lookup"><span data-stu-id="68d85-238">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="68d85-239">删除变量及其值。</span><span class="sxs-lookup"><span data-stu-id="68d85-239">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="68d85-240">更改变量的值。</span><span class="sxs-lookup"><span data-stu-id="68d85-240">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="68d85-241">请参阅</span><span class="sxs-lookup"><span data-stu-id="68d85-241">See also</span></span>

[<span data-ttu-id="68d85-242">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="68d85-242">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="68d85-243">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="68d85-243">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="68d85-244">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="68d85-244">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="68d85-245">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="68d85-245">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="68d85-246">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="68d85-246">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="68d85-247">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="68d85-247">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="68d85-248">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="68d85-248">about_Remote_Variables</span></span>](about_Remote_Variables.md)

