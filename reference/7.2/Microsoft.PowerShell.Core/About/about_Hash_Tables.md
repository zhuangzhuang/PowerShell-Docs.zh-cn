---
description: 介绍如何在 PowerShell 中创建、使用和排序哈希表。
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: dec2683acfa4fcf79419beea9e0840387d3d43d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597434"
---
# <a name="about-hash-tables"></a><span data-ttu-id="62632-103">关于哈希表</span><span class="sxs-lookup"><span data-stu-id="62632-103">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="62632-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="62632-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="62632-105">介绍如何在 PowerShell 中创建、使用和排序哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-105">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="62632-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="62632-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="62632-107">哈希表也称为字典或关联数组，是存储一个或多个键/值对的压缩数据结构。</span><span class="sxs-lookup"><span data-stu-id="62632-107">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="62632-108">例如，哈希表可能包含一系列 IP 地址和计算机名称，其中 IP 地址是密钥，计算机名称是值，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="62632-108">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="62632-109">在 PowerShell 中，每个哈希表都是一个 () 对象的哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-109">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="62632-110">可以在 PowerShell 中使用哈希表对象的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="62632-110">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="62632-111">从 PowerShell 3.0 开始，可以使用 [有序] 属性在 PowerShell 中创建一个 () 的排序字典。</span><span class="sxs-lookup"><span data-stu-id="62632-111">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="62632-112">顺序字典不同于哈希表，因为键始终按列出它们的顺序出现。</span><span class="sxs-lookup"><span data-stu-id="62632-112">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="62632-113">哈希表中的键顺序不确定。</span><span class="sxs-lookup"><span data-stu-id="62632-113">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="62632-114">哈希表中的键和值也是 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="62632-114">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="62632-115">它们最常见的是字符串或整数，但它们可以有任何对象类型。</span><span class="sxs-lookup"><span data-stu-id="62632-115">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="62632-116">您还可以创建嵌套哈希表，其中键的值为另一个哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-116">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="62632-117">通常使用哈希表，因为它们非常适合用于查找和检索数据。</span><span class="sxs-lookup"><span data-stu-id="62632-117">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="62632-118">您可以使用哈希表来存储列表，并在 PowerShell 中创建计算属性。</span><span class="sxs-lookup"><span data-stu-id="62632-118">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="62632-119">而且，PowerShell 有一个 cmdlet Convertfrom-csv-Convertfrom-stringdata，它将字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-119">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="62632-120">语法</span><span class="sxs-lookup"><span data-stu-id="62632-120">Syntax</span></span>

<span data-ttu-id="62632-121">哈希表的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="62632-121">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="62632-122">排序字典的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="62632-122">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="62632-123">PowerShell 3.0 中引入了 [有序] 属性。</span><span class="sxs-lookup"><span data-stu-id="62632-123">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="62632-124">创建哈希表</span><span class="sxs-lookup"><span data-stu-id="62632-124">Creating Hash Tables</span></span>

<span data-ttu-id="62632-125">若要创建哈希表，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="62632-125">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="62632-126">以 at 符号 ( @ ) 开始哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-126">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="62632-127">将哈希表括在大括号中， ({}) 。</span><span class="sxs-lookup"><span data-stu-id="62632-127">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="62632-128">为哈希表的内容输入一个或多个键/值对。</span><span class="sxs-lookup"><span data-stu-id="62632-128">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="62632-129">使用等号 (=) 将每个键与其值分隔开。</span><span class="sxs-lookup"><span data-stu-id="62632-129">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="62632-130">使用分号 (; ) 或换行以分隔键/值对。</span><span class="sxs-lookup"><span data-stu-id="62632-130">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="62632-131">包含空格的键必须用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="62632-131">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="62632-132">值必须是有效的 PowerShell 表达式。</span><span class="sxs-lookup"><span data-stu-id="62632-132">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="62632-133">字符串必须用引号引起来，即使它们不包含空格也是如此。</span><span class="sxs-lookup"><span data-stu-id="62632-133">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="62632-134">若要管理哈希表，请将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="62632-134">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="62632-135">将有序哈希表分配给变量时，请将 [有序] 特性置于 "@" 符号之前。</span><span class="sxs-lookup"><span data-stu-id="62632-135">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="62632-136">如果将其放在变量名称之前，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="62632-136">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="62632-137">若要在 $hash 的值中创建空的哈希表，请键入：</span><span class="sxs-lookup"><span data-stu-id="62632-137">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="62632-138">您还可以在创建哈希表时将其添加到哈希表中。</span><span class="sxs-lookup"><span data-stu-id="62632-138">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="62632-139">例如，下面的语句创建一个包含三个键的哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-139">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="62632-140">创建有序字典</span><span class="sxs-lookup"><span data-stu-id="62632-140">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="62632-141">您可以通过添加一个 OrderedDictionary 类型的对象来创建一个排序的字典，但创建排序的字典最简单的方法是使用 [有序] 特性。</span><span class="sxs-lookup"><span data-stu-id="62632-141">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="62632-142">PowerShell 3.0 中引入了 [有序] 属性。</span><span class="sxs-lookup"><span data-stu-id="62632-142">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="62632-143">紧靠在 "@" 符号前面放置属性。</span><span class="sxs-lookup"><span data-stu-id="62632-143">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="62632-144">您可以使用按顺序字典的相同方式使用哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-144">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="62632-145">任一类型都可用作参数的值，这些参数采用哈希表或字典 (iDictionary) 。</span><span class="sxs-lookup"><span data-stu-id="62632-145">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="62632-146">不能使用 [有序] 特性来转换或强制转换哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-146">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="62632-147">如果将已排序的属性放在变量名称之前，则该命令将失败，并出现以下错误消息。</span><span class="sxs-lookup"><span data-stu-id="62632-147">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="62632-148">若要更正该表达式，请移动 [有序] 特性。</span><span class="sxs-lookup"><span data-stu-id="62632-148">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="62632-149">您可以将有序的字典转换为哈希表，但不能恢复已排序的属性，即使您清除该变量并输入新值。</span><span class="sxs-lookup"><span data-stu-id="62632-149">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="62632-150">若要重新建立顺序，必须删除并重新创建变量。</span><span class="sxs-lookup"><span data-stu-id="62632-150">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="62632-151">显示哈希表</span><span class="sxs-lookup"><span data-stu-id="62632-151">Displaying Hash Tables</span></span>

<span data-ttu-id="62632-152">若要显示保存在变量中的哈希表，请键入变量名称。</span><span class="sxs-lookup"><span data-stu-id="62632-152">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="62632-153">默认情况下，哈希表显示为一个表，其中包含一个键列和一个用于值的列。</span><span class="sxs-lookup"><span data-stu-id="62632-153">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="62632-154">哈希表具有关键字和值属性。</span><span class="sxs-lookup"><span data-stu-id="62632-154">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="62632-155">使用点表示法显示所有键或所有值。</span><span class="sxs-lookup"><span data-stu-id="62632-155">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="62632-156">每个密钥名称也是哈希表的属性，其值为键-名称属性的值。</span><span class="sxs-lookup"><span data-stu-id="62632-156">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="62632-157">使用以下格式来显示属性值。</span><span class="sxs-lookup"><span data-stu-id="62632-157">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="62632-158">例如：</span><span class="sxs-lookup"><span data-stu-id="62632-158">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="62632-159">如果密钥名称与哈希表类型的某个属性名称冲突，则可以使用 `PSBase` 来访问这些属性。</span><span class="sxs-lookup"><span data-stu-id="62632-159">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="62632-160">例如，如果密钥名称为， `keys` 并且你想要返回密钥的集合，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="62632-160">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="62632-161">哈希表具有一个 Count 属性，该属性指示哈希表中的键/值对的数目。</span><span class="sxs-lookup"><span data-stu-id="62632-161">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="62632-162">哈希表表不是数组，因此不能将整数用作哈希表中的索引，但可以使用键名来索引到哈希表中。</span><span class="sxs-lookup"><span data-stu-id="62632-162">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="62632-163">如果该密钥是一个字符串值，则将该键名称用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="62632-163">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="62632-164">例如：</span><span class="sxs-lookup"><span data-stu-id="62632-164">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="62632-165">添加和删除键和值</span><span class="sxs-lookup"><span data-stu-id="62632-165">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="62632-166">若要将键和值添加到哈希表，请使用以下命令格式。</span><span class="sxs-lookup"><span data-stu-id="62632-166">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="62632-167">例如，若要将值为 "Now" 的 "Time" 键添加到哈希表，请使用以下语句格式。</span><span class="sxs-lookup"><span data-stu-id="62632-167">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="62632-168">还可以通过使用 system.exception 对象的 Add 方法，将键和值添加到哈希表中。</span><span class="sxs-lookup"><span data-stu-id="62632-168">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="62632-169">Add 方法具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="62632-169">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="62632-170">例如，若要将值为 "Now" 的 "Time" 键添加到哈希表，请使用以下语句格式。</span><span class="sxs-lookup"><span data-stu-id="62632-170">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="62632-171">而且，您可以通过使用加法运算符 (+) 向现有哈希表添加一个哈希表来向哈希表添加键和值。</span><span class="sxs-lookup"><span data-stu-id="62632-171">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="62632-172">例如，下面的语句将值为 "Now" 的 "Time" 键添加到 $hash 变量的哈希表中。</span><span class="sxs-lookup"><span data-stu-id="62632-172">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="62632-173">您还可以添加变量中存储的值。</span><span class="sxs-lookup"><span data-stu-id="62632-173">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="62632-174">不能使用减法运算符从哈希表中删除键/值对，但可以使用哈希表对象的 Remove 方法。</span><span class="sxs-lookup"><span data-stu-id="62632-174">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="62632-175">Remove 方法使用键作为其值。</span><span class="sxs-lookup"><span data-stu-id="62632-175">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="62632-176">Remove 方法具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="62632-176">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="62632-177">例如，若要从 $hash 变量的值中的哈希表中删除时间 = Now 键/值对，请键入：</span><span class="sxs-lookup"><span data-stu-id="62632-177">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="62632-178">可以在 PowerShell 中使用哈希表对象的所有属性和方法，包括 Contains、Clear、Clone 和 CopyTo。</span><span class="sxs-lookup"><span data-stu-id="62632-178">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="62632-179">有关哈希表对象的详细信息，请参阅 [system.object](/dotnet/api/system.collections.hashtable)。</span><span class="sxs-lookup"><span data-stu-id="62632-179">For more information about Hashtable objects, see [System.Collections.Hashtable](/dotnet/api/system.collections.hashtable).</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="62632-180">哈希表中的对象类型</span><span class="sxs-lookup"><span data-stu-id="62632-180">Object Types in HashTables</span></span>

<span data-ttu-id="62632-181">哈希表中的键和值可具有任何 .NET 对象类型，而单个哈希表可以具有多个类型的键和值。</span><span class="sxs-lookup"><span data-stu-id="62632-181">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="62632-182">下面的语句创建进程名称字符串的哈希表和进程对象值，并将其保存在 `$p` 变量中。</span><span class="sxs-lookup"><span data-stu-id="62632-182">The following statement creates a hash table of process name strings and process object values and saves it in the `$p` variable.</span></span>

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

<span data-ttu-id="62632-183">您可以在中显示哈希表 `$p` ，并使用键名属性来显示这些值。</span><span class="sxs-lookup"><span data-stu-id="62632-183">You can display the hash table in `$p` and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="62632-184">哈希表中的键还可以是任意 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="62632-184">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="62632-185">下面的语句将一个键/值对添加到变量中的哈希表 `$p` 。</span><span class="sxs-lookup"><span data-stu-id="62632-185">The following statement adds a key/value pair to the hash table in the `$p` variable.</span></span> <span data-ttu-id="62632-186">密钥是表示 WinRM 服务的服务对象，值是该服务的当前状态。</span><span class="sxs-lookup"><span data-stu-id="62632-186">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="62632-187">您可以使用在哈希表中用于其他对的相同方法来显示和访问新的键/值对。</span><span class="sxs-lookup"><span data-stu-id="62632-187">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="62632-188">哈希表中的键和值也可以是哈希表对象。</span><span class="sxs-lookup"><span data-stu-id="62632-188">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="62632-189">下面的语句将键/值对添加到哈希表中的哈希表中，该 `$p` 变量中的键是字符串 Hash2，而值是具有三个键/值对的哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-189">The following statement adds key/value pair to the hash table in the `$p` variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="62632-190">您可以通过使用相同的方法来显示和访问新值。</span><span class="sxs-lookup"><span data-stu-id="62632-190">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="62632-191">对键和值进行排序</span><span class="sxs-lookup"><span data-stu-id="62632-191">Sorting Keys and Values</span></span>

<span data-ttu-id="62632-192">哈希表中的项在本质上是无序的。</span><span class="sxs-lookup"><span data-stu-id="62632-192">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="62632-193">每次显示键/值对时，它们的显示顺序可能不同。</span><span class="sxs-lookup"><span data-stu-id="62632-193">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="62632-194">尽管不能对哈希表进行排序，但可以使用哈希表的 GetEnumerator 方法枚举键和值，然后使用 Sort-Object cmdlet 对要显示的枚举值进行排序。</span><span class="sxs-lookup"><span data-stu-id="62632-194">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="62632-195">例如，以下命令枚举变量的哈希表中的键和值 `$p` ，然后按字母顺序对键进行排序。</span><span class="sxs-lookup"><span data-stu-id="62632-195">For example, the following commands enumerate the keys and values in the hash table in the `$p` variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="62632-196">以下命令使用相同的过程来按降序对哈希值进行排序。</span><span class="sxs-lookup"><span data-stu-id="62632-196">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="62632-197">从哈希表创建对象</span><span class="sxs-lookup"><span data-stu-id="62632-197">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="62632-198">从 PowerShell 3.0 开始，可以从属性和属性值的哈希表创建对象。</span><span class="sxs-lookup"><span data-stu-id="62632-198">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="62632-199">语法如下：</span><span class="sxs-lookup"><span data-stu-id="62632-199">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="62632-200">此方法仅适用于具有 null 构造函数（即，没有参数的构造函数）的类。</span><span class="sxs-lookup"><span data-stu-id="62632-200">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="62632-201">对象属性必须是公共且可设置的。</span><span class="sxs-lookup"><span data-stu-id="62632-201">The object properties must be public and settable.</span></span>

<span data-ttu-id="62632-202">有关详细信息，请参阅 [about_Object_Creation](about_Object_Creation.md)。</span><span class="sxs-lookup"><span data-stu-id="62632-202">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="62632-203">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="62632-203">ConvertFrom-StringData</span></span>

<span data-ttu-id="62632-204">`ConvertFrom-StringData`Cmdlet 将一个字符串或键/值对的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-204">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="62632-205">可以 `ConvertFrom-StringData` 在脚本的数据部分中安全地使用 cmdlet，并将其与 cmdlet 一起使用， `Import-LocalizedData` 以在用户界面中显示用户消息 (UI) 当前用户的区域性。</span><span class="sxs-lookup"><span data-stu-id="62632-205">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="62632-206">此处-当哈希表中的值包含引号时，字符串特别有用。</span><span class="sxs-lookup"><span data-stu-id="62632-206">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="62632-207">有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="62632-207">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="62632-208">下面的示例演示如何在上一个示例中创建用户消息的下一个字符串，以及如何使用将 `ConvertFrom-StringData` 它们从字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-208">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="62632-209">下面的命令创建一个键/值对的字符串，然后将其保存在 \$ 字符串变量中。</span><span class="sxs-lookup"><span data-stu-id="62632-209">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="62632-210">此命令使用 ConvertFrom-StringData cmdlet 将此处的字符串转换为哈希表。</span><span class="sxs-lookup"><span data-stu-id="62632-210">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="62632-211">有关字符串的详细信息，请参阅 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="62632-211">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62632-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62632-212">SEE ALSO</span></span>

[<span data-ttu-id="62632-213">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="62632-213">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="62632-214">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="62632-214">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="62632-215">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="62632-215">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="62632-216">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="62632-216">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="62632-217">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="62632-217">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="62632-218">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="62632-218">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="62632-219">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="62632-219">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)
