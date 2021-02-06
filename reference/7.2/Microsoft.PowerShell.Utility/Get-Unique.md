---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596848"
---
# <span data-ttu-id="3315f-102">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="3315f-102">Get-Unique</span></span>

## <span data-ttu-id="3315f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3315f-103">SYNOPSIS</span></span>
<span data-ttu-id="3315f-104">从排序列表中返回唯一项。</span><span class="sxs-lookup"><span data-stu-id="3315f-104">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="3315f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3315f-105">SYNTAX</span></span>

### <span data-ttu-id="3315f-106">AsString（默认值）</span><span class="sxs-lookup"><span data-stu-id="3315f-106">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="3315f-107">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="3315f-107">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="3315f-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3315f-108">DESCRIPTION</span></span>

<span data-ttu-id="3315f-109">该 `Get-Unique` cmdlet 将排序列表中的每个项与下一项进行比较，消除重复项并仅返回每个项的一个实例。</span><span class="sxs-lookup"><span data-stu-id="3315f-109">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="3315f-110">必须对该列表进行排序，才能使该 cmdlet 正常运行。</span><span class="sxs-lookup"><span data-stu-id="3315f-110">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="3315f-111">`Get-Unique` 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3315f-111">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="3315f-112">因此，会将仅大小写不同的字符串视为唯一项。</span><span class="sxs-lookup"><span data-stu-id="3315f-112">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="3315f-113">示例</span><span class="sxs-lookup"><span data-stu-id="3315f-113">EXAMPLES</span></span>

### <span data-ttu-id="3315f-114">示例 1：获取文本文件中的唯一单词</span><span class="sxs-lookup"><span data-stu-id="3315f-114">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="3315f-115">这些命令将查找文本文件中唯一单词的数目。</span><span class="sxs-lookup"><span data-stu-id="3315f-115">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="3315f-116">第一个命令获取 File.txt 文件的内容。</span><span class="sxs-lookup"><span data-stu-id="3315f-116">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="3315f-117">它将文本的每一行转换为小写字母，然后在空格处（“ ”）将每个单词拆分到单独的行上。</span><span class="sxs-lookup"><span data-stu-id="3315f-117">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="3315f-118">然后，它将按字母顺序对结果列表进行排序 (默认) 并使用 `Get-Unique` cmdlet 来消除任何重复单词。</span><span class="sxs-lookup"><span data-stu-id="3315f-118">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="3315f-119">结果存储在 `$A` 变量中。</span><span class="sxs-lookup"><span data-stu-id="3315f-119">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="3315f-120">第二个命令使用中的字符串集合的 **Count** 属性 `$A` 来确定中有多少项 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="3315f-120">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="3315f-121">示例 2：获取数组中的唯一整数</span><span class="sxs-lookup"><span data-stu-id="3315f-121">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="3315f-122">此命令将查找整数组的唯一成员。</span><span class="sxs-lookup"><span data-stu-id="3315f-122">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="3315f-123">第一个命令采用在命令行中键入的整数数组，将它们传递给要 `Sort-Object` 排序的 cmdlet，然后通过管道将其传递到 `Get-Unique` ，从而消除重复项。</span><span class="sxs-lookup"><span data-stu-id="3315f-123">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="3315f-124">示例 3：获取目录中的唯一对象类型</span><span class="sxs-lookup"><span data-stu-id="3315f-124">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="3315f-125">此命令使用 `Get-ChildItem` cmdlet 检索本地目录的内容，其中包括文件和目录。</span><span class="sxs-lookup"><span data-stu-id="3315f-125">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="3315f-126">管道运算符 (|) 将结果发送到 `Sort-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3315f-126">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3315f-127">`$_.GetType()`语句将 **GetType** 方法应用到每个文件或目录。</span><span class="sxs-lookup"><span data-stu-id="3315f-127">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="3315f-128">然后， `Sort-Object` 按类型对项进行排序。</span><span class="sxs-lookup"><span data-stu-id="3315f-128">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="3315f-129">另一个管道运算符将结果发送到 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="3315f-129">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="3315f-130">**OnType** 参数定向 `Get-Unique` 到仅返回每种类型的一个对象。</span><span class="sxs-lookup"><span data-stu-id="3315f-130">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="3315f-131">示例 4：获取唯一进程</span><span class="sxs-lookup"><span data-stu-id="3315f-131">Example 4: Get unique processes</span></span>

<span data-ttu-id="3315f-132">此命令将获取在计算机上运行的进程的名称，并消除重复项。</span><span class="sxs-lookup"><span data-stu-id="3315f-132">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="3315f-133">此 `Get-Process` 命令获取计算机上的所有进程。</span><span class="sxs-lookup"><span data-stu-id="3315f-133">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="3315f-134">管道运算符 (|) 将结果传递给 `Sort-Object` ，默认情况下，将按 ProcessName 的字母顺序对进程进行排序。</span><span class="sxs-lookup"><span data-stu-id="3315f-134">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="3315f-135">结果将通过管道传递给 `Select-Object` cmdlet，后者只选择每个对象的 ProcessName 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3315f-135">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="3315f-136">然后，将结果输送到 `Get-Unique` 以消除重复项。</span><span class="sxs-lookup"><span data-stu-id="3315f-136">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="3315f-137">**AsString** 参数指示 `Get-Unique` 将 **ProcessName** 值视为字符串。</span><span class="sxs-lookup"><span data-stu-id="3315f-137">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="3315f-138">如果没有此参数，则 `Get-Unique` 将 **ProcessName** 值视为对象，并仅返回对象的一个实例，即列表中的第一个进程名称。</span><span class="sxs-lookup"><span data-stu-id="3315f-138">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="3315f-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3315f-139">PARAMETERS</span></span>

### <span data-ttu-id="3315f-140">-AsString</span><span class="sxs-lookup"><span data-stu-id="3315f-140">-AsString</span></span>

<span data-ttu-id="3315f-141">指示此 cmdlet 将数据用作字符串。</span><span class="sxs-lookup"><span data-stu-id="3315f-141">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="3315f-142">如果没有此参数，则数据将被视为对象，因此在将相同类型的对象集合（ `Get-Unique` 如文件集合）提交到时，它只会返回一个 (第一个) 。</span><span class="sxs-lookup"><span data-stu-id="3315f-142">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="3315f-143">可以使用此参数来查找对象属性的唯一值，如文件名。</span><span class="sxs-lookup"><span data-stu-id="3315f-143">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3315f-144">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3315f-144">-InputObject</span></span>

<span data-ttu-id="3315f-145">指定的输入 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="3315f-145">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="3315f-146">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="3315f-146">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="3315f-147">此 cmdlet 将使用 **InputObject** 提交的输入视为集合。</span><span class="sxs-lookup"><span data-stu-id="3315f-147">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="3315f-148">它不枚举集合中的各个项。</span><span class="sxs-lookup"><span data-stu-id="3315f-148">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="3315f-149">因为集合是单个项，所以通过使用 InputObject 提交的输入始终按原样返回。</span><span class="sxs-lookup"><span data-stu-id="3315f-149">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3315f-150">-OnType</span><span class="sxs-lookup"><span data-stu-id="3315f-150">-OnType</span></span>

<span data-ttu-id="3315f-151">指示此 cmdlet 仅返回每种类型的一个对象。</span><span class="sxs-lookup"><span data-stu-id="3315f-151">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3315f-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3315f-152">CommonParameters</span></span>

<span data-ttu-id="3315f-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3315f-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3315f-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3315f-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3315f-155">输入</span><span class="sxs-lookup"><span data-stu-id="3315f-155">INPUTS</span></span>

### <span data-ttu-id="3315f-156">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3315f-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3315f-157">可以通过管道将任何类型的对象传递给 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="3315f-157">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="3315f-158">输出</span><span class="sxs-lookup"><span data-stu-id="3315f-158">OUTPUTS</span></span>

### <span data-ttu-id="3315f-159">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3315f-159">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3315f-160">返回的对象的类型由 `Get-Unique` 输入确定。</span><span class="sxs-lookup"><span data-stu-id="3315f-160">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="3315f-161">注释</span><span class="sxs-lookup"><span data-stu-id="3315f-161">NOTES</span></span>

<span data-ttu-id="3315f-162">还可以 `Get-Unique` 通过其内置别名来引用 `gu` 。</span><span class="sxs-lookup"><span data-stu-id="3315f-162">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="3315f-163">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="3315f-163">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="3315f-164">若要对列表进行排序，请使用 Sort-Object。</span><span class="sxs-lookup"><span data-stu-id="3315f-164">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="3315f-165">你还可以使用的 **唯一** 参数 `Sort-Object` 在列表中查找唯一项。</span><span class="sxs-lookup"><span data-stu-id="3315f-165">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="3315f-166">相关链接</span><span class="sxs-lookup"><span data-stu-id="3315f-166">RELATED LINKS</span></span>

[<span data-ttu-id="3315f-167">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3315f-167">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="3315f-168">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="3315f-168">Sort-Object</span></span>](Sort-Object.md)

