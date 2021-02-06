---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 80882d27c9c8fa2d7f9e1c8ca00a02cf73ae94e6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597651"
---
# <span data-ttu-id="cd06a-102">Select-Object</span><span class="sxs-lookup"><span data-stu-id="cd06a-102">Select-Object</span></span>

## <span data-ttu-id="cd06a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cd06a-103">SYNOPSIS</span></span>
<span data-ttu-id="cd06a-104">选择对象或对象属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-104">Selects objects or object properties.</span></span>

## <span data-ttu-id="cd06a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd06a-105">SYNTAX</span></span>

### <span data-ttu-id="cd06a-106">DefaultParameter (默认值) </span><span class="sxs-lookup"><span data-stu-id="cd06a-106">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="cd06a-107">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="cd06a-107">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="cd06a-108">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="cd06a-108">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="cd06a-109">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="cd06a-109">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="cd06a-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cd06a-110">DESCRIPTION</span></span>

<span data-ttu-id="cd06a-111">`Select-Object`Cmdlet 可选择对象或对象集的指定属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-111">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="cd06a-112">它还可以从数组中选择唯一对象、指定数目的对象或指定位置中的对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-112">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="cd06a-113">若要从集合中选择对象，请使用 **First**、**Last**、**Unique**、**Skip** 和 **Index** 参数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-113">To select objects from a collection, use the **First**, **Last**, **Unique**, **Skip**, and **Index** parameters.</span></span> <span data-ttu-id="cd06a-114">若要选择对象属性，请使用 **Property** 参数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-114">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="cd06a-115">选择 "属性" 时， `Select-Object` 将返回只具有指定属性的新对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-115">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="cd06a-116">从 Windows PowerShell 3.0 开始， `Select-Object` 包含一项优化功能，可防止命令创建和处理未使用的对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-116">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="cd06a-117">如果在 `Select-Object` 命令管道中包含带有 **第一个** 或 **索引** 参数的命令，则在生成所选数目的对象之后，PowerShell 将停止生成对象，即使生成对象的命令出现在 `Select-Object` 管道中的命令之前。</span><span class="sxs-lookup"><span data-stu-id="cd06a-117">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="cd06a-118">若要禁用此优化行为，请使用 **Wait** 参数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-118">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="cd06a-119">示例</span><span class="sxs-lookup"><span data-stu-id="cd06a-119">EXAMPLES</span></span>

### <span data-ttu-id="cd06a-120">示例1：按属性选择对象</span><span class="sxs-lookup"><span data-stu-id="cd06a-120">Example 1: Select objects by property</span></span>

<span data-ttu-id="cd06a-121">此示例将创建具有进程对象的 **Name**、 **ID** 和工作集 (**WS**) 属性的对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-121">This example creates objects that have the **Name**, **ID**, and working set (**WS**) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="cd06a-122">示例2：按属性选择对象并设置结果格式</span><span class="sxs-lookup"><span data-stu-id="cd06a-122">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="cd06a-123">此示例将获取有关计算机上的进程所使用的模块的信息。</span><span class="sxs-lookup"><span data-stu-id="cd06a-123">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="cd06a-124">它使用 `Get-Process` cmdlet 来获取计算机上的进程。</span><span class="sxs-lookup"><span data-stu-id="cd06a-124">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="cd06a-125">它使用 `Select-Object` cmdlet 输出实例的数组， `[System.Diagnostics.ProcessModule]` 该数组包含在每个实例输出的 **模块** 属性中 `System.Diagnostics.Process` `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-125">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="cd06a-126">Cmdlet 的 **Property** 参数 `Select-Object` 选择进程名称。</span><span class="sxs-lookup"><span data-stu-id="cd06a-126">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="cd06a-127">这会将 `ProcessName` **NoteProperty** 添加到每个 `[System.Diagnostics.ProcessModule]` 实例中，并用当前进程的 **ProcessName** 属性的值填充该实例。</span><span class="sxs-lookup"><span data-stu-id="cd06a-127">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="cd06a-128">最后， `Format-List` 使用 cmdlet 在列表中显示每个进程的名称和模块。</span><span class="sxs-lookup"><span data-stu-id="cd06a-128">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="cd06a-129">示例3：选择使用最多内存的进程</span><span class="sxs-lookup"><span data-stu-id="cd06a-129">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="cd06a-130">此示例获取使用最多内存的五个进程。</span><span class="sxs-lookup"><span data-stu-id="cd06a-130">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="cd06a-131">`Get-Process`Cmdlet 将获取计算机上的进程。</span><span class="sxs-lookup"><span data-stu-id="cd06a-131">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="cd06a-132">该 `Sort-Object` cmdlet 根据内存 (工作集) 使用情况对进程进行排序，并且该 `Select-Object` cmdlet 仅选择生成的对象数组的最后五个成员。</span><span class="sxs-lookup"><span data-stu-id="cd06a-132">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="cd06a-133">包含 cmdlet 的命令中不需要 **Wait** 参数， `Sort-Object` 因为 `Sort-Object` 处理所有对象，然后返回集合。</span><span class="sxs-lookup"><span data-stu-id="cd06a-133">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="cd06a-134">`Select-Object`优化仅可用于在处理对象时单独返回对象的命令。</span><span class="sxs-lookup"><span data-stu-id="cd06a-134">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="cd06a-135">示例4：选择数组中的唯一字符</span><span class="sxs-lookup"><span data-stu-id="cd06a-135">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="cd06a-136">此示例使用的 **唯一** 参数 `Select-Object` 从字符数组中获取唯一字符。</span><span class="sxs-lookup"><span data-stu-id="cd06a-136">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="cd06a-137">示例5：选择事件日志中的最新和最旧的事件</span><span class="sxs-lookup"><span data-stu-id="cd06a-137">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="cd06a-138">此示例获取 Windows PowerShell 事件日志中的第一个 (最新) 和最后一个 (最早的) 事件。</span><span class="sxs-lookup"><span data-stu-id="cd06a-138">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="cd06a-139">`Get-EventLog` 获取 Windows PowerShell 日志中的所有事件，并将其保存在 `$a` 变量中。</span><span class="sxs-lookup"><span data-stu-id="cd06a-139">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="cd06a-140">然后， `$a` 将管道传递给 `Select-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cd06a-140">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="cd06a-141">该 `Select-Object` 命令使用 **Index** 参数从变量中的事件数组中选择事件 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-141">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="cd06a-142">第一个事件的索引为 0。</span><span class="sxs-lookup"><span data-stu-id="cd06a-142">The index of the first event is 0.</span></span> <span data-ttu-id="cd06a-143">最后一个事件的索引为减1中的项数 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-143">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="cd06a-144">示例6：选择除第一个对象之外的所有对象</span><span class="sxs-lookup"><span data-stu-id="cd06a-144">Example 6: Select all but the first object</span></span>

<span data-ttu-id="cd06a-145">此示例在 Servers.txt 文件中列出的每台计算机上创建新的 PSSession，第一台计算机除外。</span><span class="sxs-lookup"><span data-stu-id="cd06a-145">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="cd06a-146">`Select-Object` 选择计算机名称列表中除第一台计算机之外的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="cd06a-146">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="cd06a-147">生成的计算机列表被设置为该 cmdlet 的 **ComputerName** 参数的值 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-147">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="cd06a-148">示例7：重命名文件并选择多个进行审阅</span><span class="sxs-lookup"><span data-stu-id="cd06a-148">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="cd06a-149">此示例将 "-ro" 后缀添加到具有只读属性的文本文件的基名称中，然后显示前五个文件，以便用户可以看到该效果的示例。</span><span class="sxs-lookup"><span data-stu-id="cd06a-149">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="cd06a-150">`Get-ChildItem` 使用 **ReadOnly** 动态参数获取只读文件。</span><span class="sxs-lookup"><span data-stu-id="cd06a-150">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="cd06a-151">生成的文件将通过管道传输到 `Rename-Item` cmdlet，这会重命名该文件。</span><span class="sxs-lookup"><span data-stu-id="cd06a-151">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="cd06a-152">它使用的 **Passthru** 参数将 `Rename-Item` 重命名的文件发送到 `Select-Object` cmdlet，后者将选择前5个进行显示。</span><span class="sxs-lookup"><span data-stu-id="cd06a-152">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="cd06a-153">的 **Wait** 参数 `Select-Object` 可防止 PowerShell 在 `Get-ChildItem` 获取前五个只读文本文件后停止该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cd06a-153">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="cd06a-154">如果不使用此参数，则只有前五个只读文件会被重命名。</span><span class="sxs-lookup"><span data-stu-id="cd06a-154">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="cd06a-155">示例8：演示-ExpandProperty 参数的复杂性</span><span class="sxs-lookup"><span data-stu-id="cd06a-155">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="cd06a-156">此示例演示了 **ExpandProperty** 参数的复杂性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-156">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="cd06a-157">请注意，生成的输出是实例的数组 `[System.Int32]` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-157">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="cd06a-158">实例符合 **输出视图** 的标准格式设置规则。</span><span class="sxs-lookup"><span data-stu-id="cd06a-158">The instances conform to standard formatting rules of the **Output View**.</span></span> <span data-ttu-id="cd06a-159">对于 *扩展* 的属性，这是正确的。</span><span class="sxs-lookup"><span data-stu-id="cd06a-159">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="cd06a-160">如果输出对象具有特定的标准格式，则扩展属性可能不可见。</span><span class="sxs-lookup"><span data-stu-id="cd06a-160">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="cd06a-161">示例9：在对象上创建自定义属性</span><span class="sxs-lookup"><span data-stu-id="cd06a-161">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="cd06a-162">下面的示例演示如何使用 `Select-Object` 将自定义属性添加到任何对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-162">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="cd06a-163">如果指定不存在的属性名称，则会 `Select-Object` 在传递的每个对象上将该属性创建为 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-163">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="cd06a-164">示例10：为每个 InputObject 创建计算属性</span><span class="sxs-lookup"><span data-stu-id="cd06a-164">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="cd06a-165">此示例演示如何使用向 `Select-Object` 输入添加计算属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-165">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="cd06a-166">将 **ScriptBlock** 传递给 **属性** 参数会导致 `Select-Object` 计算每个传递对象的表达式，并将结果添加到输出。</span><span class="sxs-lookup"><span data-stu-id="cd06a-166">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="cd06a-167">在 **ScriptBlock** 内，可以使用 `$_` 变量来引用管道中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-167">Within the **ScriptBlock**, you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="cd06a-168">默认情况下， `Select-Object` 将使用 **ScriptBlock** 字符串作为属性的名称。</span><span class="sxs-lookup"><span data-stu-id="cd06a-168">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="cd06a-169">使用 **哈希表**，你可以将 **ScriptBlock** 的输出标记为添加到每个对象的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-169">Using a **Hashtable**, you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="cd06a-170">您可以向传递到的每个对象添加多个计算属性 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-170">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="cd06a-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd06a-171">PARAMETERS</span></span>

### <span data-ttu-id="cd06a-172">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="cd06a-172">-ExcludeProperty</span></span>

<span data-ttu-id="cd06a-173">指定此 cmdlet 从操作中排除的属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-173">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="cd06a-174">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="cd06a-174">Wildcards are permitted.</span></span>

<span data-ttu-id="cd06a-175">从 PowerShell 6 开始，不再需要包含 **Property** 参数即可使用 **ExcludeProperty** 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-175">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cd06a-176">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="cd06a-176">-ExpandProperty</span></span>

<span data-ttu-id="cd06a-177">指定要选择的属性，并指示应当尝试展开该属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-177">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="cd06a-178">如果指定的属性是数组，则数组的每个值都包含在输出中。</span><span class="sxs-lookup"><span data-stu-id="cd06a-178">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="cd06a-179">如果指定的属性是一个对象，则为每个 **InputObject** 展开对象属性</span><span class="sxs-lookup"><span data-stu-id="cd06a-179">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="cd06a-180">在任一情况下，输出的对象 **类型** 都将与扩展属性的 **类型** 匹配。</span><span class="sxs-lookup"><span data-stu-id="cd06a-180">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="cd06a-181">如果指定了 **Property** 参数， `Select-Object` 将尝试将每个选定的属性作为 **NoteProperty** 添加到每个输出对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-181">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="cd06a-182">如果收到错误： Select：无法处理属性，因为属性 `<PropertyName>` 已经存在，请注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="cd06a-182">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="cd06a-183">请注意，使用时 `-ExpandProperty` ， `Select-Object` 不能替换现有属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-183">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="cd06a-184">这意味着：</span><span class="sxs-lookup"><span data-stu-id="cd06a-184">This means:</span></span>
>
> - <span data-ttu-id="cd06a-185">如果展开的对象具有相同名称的属性，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="cd06a-185">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="cd06a-186">如果 *所选* 对象的属性与 *展开* 的对象属性的名称相同，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="cd06a-186">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-187">-第一个</span><span class="sxs-lookup"><span data-stu-id="cd06a-187">-First</span></span>

<span data-ttu-id="cd06a-188">指定要从输入对象的数组的开头选择的对象数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-188">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-189">-Index</span><span class="sxs-lookup"><span data-stu-id="cd06a-189">-Index</span></span>

<span data-ttu-id="cd06a-190">基于对象的索引值从数组中选择对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-190">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="cd06a-191">以逗号分隔的列表形式输入索引。</span><span class="sxs-lookup"><span data-stu-id="cd06a-191">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="cd06a-192">数组中的索引从 0 开始，0 表示第一个值，(n-1) 表示最后一个值。</span><span class="sxs-lookup"><span data-stu-id="cd06a-192">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-193">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cd06a-193">-InputObject</span></span>

<span data-ttu-id="cd06a-194">指定要通过管道发送到 cmdlet 的对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-194">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="cd06a-195">此参数使你能够将对象传递给 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-195">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="cd06a-196">将对象传递到 **inputobject** 参数时，不使用管道将 `Select-Object` **InputObject** 视为单个对象，即使该值是集合也是如此。</span><span class="sxs-lookup"><span data-stu-id="cd06a-196">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="cd06a-197">建议在将集合传递到时使用管道 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-197">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

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

### <span data-ttu-id="cd06a-198">-Last</span><span class="sxs-lookup"><span data-stu-id="cd06a-198">-Last</span></span>

<span data-ttu-id="cd06a-199">指定要从输入对象的数组的末尾选择的对象数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-199">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-200">-Property</span><span class="sxs-lookup"><span data-stu-id="cd06a-200">-Property</span></span>

<span data-ttu-id="cd06a-201">指定要选择的属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-201">Specifies the properties to select.</span></span> <span data-ttu-id="cd06a-202">这些属性作为 **NoteProperty** 成员添加到输出对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-202">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="cd06a-203">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="cd06a-203">Wildcards are permitted.</span></span>

<span data-ttu-id="cd06a-204">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="cd06a-204">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="cd06a-205">若要创建计算属性，请使用哈希表。</span><span class="sxs-lookup"><span data-stu-id="cd06a-205">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="cd06a-206">有效键包括：</span><span class="sxs-lookup"><span data-stu-id="cd06a-206">Valid keys are:</span></span>

- <span data-ttu-id="cd06a-207">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="cd06a-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="cd06a-208">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="cd06a-208">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="cd06a-209">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cd06a-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cd06a-210">-Skip</span><span class="sxs-lookup"><span data-stu-id="cd06a-210">-Skip</span></span>

<span data-ttu-id="cd06a-211">跳过（不选择）指定数目的项目。</span><span class="sxs-lookup"><span data-stu-id="cd06a-211">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="cd06a-212">默认情况下， **Skip** 参数会从数组或对象列表的开头开始计数，但如果命令使用 **最后一个** 参数，则会从列表或数组的末尾开始计数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-212">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="cd06a-213">与从 0 开始计数的 **Index** 参数不同，**Skip** 参数从 1 开始计数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-213">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-214">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="cd06a-214">-SkipLast</span></span>

<span data-ttu-id="cd06a-215">跳过 (不选择从列表或数组的末尾) 指定数目的项。</span><span class="sxs-lookup"><span data-stu-id="cd06a-215">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="cd06a-216">的工作方式与结合使用 **Skip** 和 **Last** 参数相同。</span><span class="sxs-lookup"><span data-stu-id="cd06a-216">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="cd06a-217">与从0开始计数的 **Index** 参数不同， **SkipLast** 参数从1开始计数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-217">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-218">-Unique</span><span class="sxs-lookup"><span data-stu-id="cd06a-218">-Unique</span></span>

<span data-ttu-id="cd06a-219">指定如果输入对象的子集有相同的属性和值，则只选择该子集的一个成员。</span><span class="sxs-lookup"><span data-stu-id="cd06a-219">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="cd06a-220">此参数区分大小写。</span><span class="sxs-lookup"><span data-stu-id="cd06a-220">This parameter is case-sensitive.</span></span> <span data-ttu-id="cd06a-221">因此，会将仅大小写不同的字符串视为唯一项。</span><span class="sxs-lookup"><span data-stu-id="cd06a-221">As a result, strings that differ only in character casing are considered to be unique.</span></span>

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

### <span data-ttu-id="cd06a-222">-Wait</span><span class="sxs-lookup"><span data-stu-id="cd06a-222">-Wait</span></span>

<span data-ttu-id="cd06a-223">指示该 cmdlet 禁用优化。</span><span class="sxs-lookup"><span data-stu-id="cd06a-223">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="cd06a-224">PowerShell 会按照命令在命令管道中出现的顺序运行命令，并允许它们生成所有对象。</span><span class="sxs-lookup"><span data-stu-id="cd06a-224">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="cd06a-225">默认情况下，如果在 `Select-Object` 命令管道中包含带有 **第一个** 或 **索引** 参数的命令，则在生成所选数量的对象之后，PowerShell 会立即停止生成对象的命令。</span><span class="sxs-lookup"><span data-stu-id="cd06a-225">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="cd06a-226">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="cd06a-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-227">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="cd06a-227">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd06a-228">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd06a-228">CommonParameters</span></span>

<span data-ttu-id="cd06a-229">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cd06a-229">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd06a-230">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cd06a-230">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cd06a-231">输入</span><span class="sxs-lookup"><span data-stu-id="cd06a-231">INPUTS</span></span>

### <span data-ttu-id="cd06a-232">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="cd06a-232">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="cd06a-233">可以通过管道将任何对象传递给 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-233">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="cd06a-234">输出</span><span class="sxs-lookup"><span data-stu-id="cd06a-234">OUTPUTS</span></span>

### <span data-ttu-id="cd06a-235">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="cd06a-235">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="cd06a-236">注释</span><span class="sxs-lookup"><span data-stu-id="cd06a-236">NOTES</span></span>

- <span data-ttu-id="cd06a-237">还可以 `Select-Object` 通过其内置别名来引用 cmdlet `select` 。</span><span class="sxs-lookup"><span data-stu-id="cd06a-237">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="cd06a-238">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="cd06a-238">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="cd06a-239">的优化功能 `Select-Object` 仅适用于在处理管道时将对象写入管道的命令。</span><span class="sxs-lookup"><span data-stu-id="cd06a-239">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="cd06a-240">它对用于缓冲处理的对象并将其作为集合写入的命令不起作用。</span><span class="sxs-lookup"><span data-stu-id="cd06a-240">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="cd06a-241">立即写入对象是 cmdlet 设计的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="cd06a-241">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="cd06a-242">有关详细信息，请参阅 [强烈建议开发指南](/powershell/scripting/developer/windows-powershell)中 _的将单个记录写入管道_。</span><span class="sxs-lookup"><span data-stu-id="cd06a-242">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="cd06a-243">相关链接</span><span class="sxs-lookup"><span data-stu-id="cd06a-243">RELATED LINKS</span></span>

[<span data-ttu-id="cd06a-244">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="cd06a-244">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="cd06a-245">Group-Object</span><span class="sxs-lookup"><span data-stu-id="cd06a-245">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="cd06a-246">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="cd06a-246">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="cd06a-247">Where-Object</span><span class="sxs-lookup"><span data-stu-id="cd06a-247">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
