---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 2db0a8abe8fbd87b077e40655a06a1db45482ebc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595810"
---
# <span data-ttu-id="9a0a9-102">Format-Table</span><span class="sxs-lookup"><span data-stu-id="9a0a9-102">Format-Table</span></span>

## <span data-ttu-id="9a0a9-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9a0a9-103">SYNOPSIS</span></span>
<span data-ttu-id="9a0a9-104">将输出的格式设置为一个表。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-104">Formats the output as a table.</span></span>

## <span data-ttu-id="9a0a9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a0a9-105">SYNTAX</span></span>

### <span data-ttu-id="9a0a9-106">全部</span><span class="sxs-lookup"><span data-stu-id="9a0a9-106">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="9a0a9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a0a9-107">DESCRIPTION</span></span>

<span data-ttu-id="9a0a9-108">该 `Format-Table` cmdlet 将命令输出的格式设置为表，其中每列中的对象的所选属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-108">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="9a0a9-109">对象类型确定每列中显示的默认布局和属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-109">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="9a0a9-110">您可以使用 **Property** 参数来选择要显示的属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-110">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="9a0a9-111">PowerShell 使用默认格式化程序定义对象类型的显示方式。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-111">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="9a0a9-112">您可以使用 `.ps1xml` 文件创建显示带有指定属性的输出表的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-112">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="9a0a9-113">创建自定义视图后，请使用 **view** 参数显示具有您的自定义视图的表。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-113">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="9a0a9-114">有关视图的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-114">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="9a0a9-115">您可以使用哈希表将计算属性添加到对象，然后再显示该对象并指定表中的列标题。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-115">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="9a0a9-116">若要添加计算属性，请使用 **property** 或 **GroupBy** 参数。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-116">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="9a0a9-117">有关哈希表的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-117">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="9a0a9-118">示例</span><span class="sxs-lookup"><span data-stu-id="9a0a9-118">EXAMPLES</span></span>

### <span data-ttu-id="9a0a9-119">示例1：格式化 PowerShell 主机</span><span class="sxs-lookup"><span data-stu-id="9a0a9-119">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="9a0a9-120">此示例在表中显示有关 PowerShell 主机程序的信息。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-120">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="9a0a9-121">该 `Get-Host` cmdlet 将获取表示该主机的 **system.management.automation.internal.host.internalhost** 对象，。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-121">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="9a0a9-122">对象沿着管道向下发送 `Format-Table` ，并显示在表中。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-122">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="9a0a9-123">**AutoSize** 参数调整列宽以尽可能减少截断。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-123">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="9a0a9-124">示例2：按 BasePriority 设置进程的格式</span><span class="sxs-lookup"><span data-stu-id="9a0a9-124">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="9a0a9-125">在此示例中，进程显示在具有相同 **BasePriority** 属性的组中。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-125">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="9a0a9-126">该 `Get-Process` cmdlet 将获取表示计算机上每个进程的对象，并将它们向下发送到 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-126">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="9a0a9-127">对象按其 **BasePriority** 属性的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-127">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="9a0a9-128">已排序对象将向下发送到 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-128">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="9a0a9-129">**GroupBy** 参数基于其 **BasePriority** 属性的值将流程数据排列成组。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-129">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="9a0a9-130">**Wrap** 参数可确保数据不会被截断。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-130">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="9a0a9-131">示例3：按开始日期设置进程的格式</span><span class="sxs-lookup"><span data-stu-id="9a0a9-131">Example 3: Format processes by start date</span></span>

<span data-ttu-id="9a0a9-132">此示例显示有关在计算机上运行的进程的信息。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-132">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="9a0a9-133">对象经过排序，并 `Format-Table` 使用视图按其开始日期对对象进行分组。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-133">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="9a0a9-134">`Get-Process` 获取表示在计算机上运行的进程的 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-134">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="9a0a9-135">对象按管道向下发送到 `Sort-Object` ，并根据 **StartTime** 属性对其进行排序。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-135">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="9a0a9-136">已排序对象将向下发送到 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-136">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="9a0a9-137">**View** 参数指定在 PowerShell  `DotNetTypes.format.ps1xml` 文件中为 **system.object** 对象定义的 StartTime View。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-137">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="9a0a9-138">**StartTime** view 将每个进程的开始时间转换为短日期，然后按开始日期对进程进行分组。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-138">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="9a0a9-139">此 `DotNetTypes.format.ps1xml` 文件包含进程的 **优先级** 视图。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-139">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="9a0a9-140">您可以 `format.ps1xml` 通过自定义视图创建自己的文件。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-140">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="9a0a9-141">示例4：为表输出使用自定义视图</span><span class="sxs-lookup"><span data-stu-id="9a0a9-141">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="9a0a9-142">在此示例中，自定义视图显示目录的内容。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-142">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="9a0a9-143">自定义视图将 **CreationTime** 列添加到创建的 **DirectoryInfo** 和 **FileInfo** 对象的表输出中 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-143">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="9a0a9-144">此示例中的自定义视图是从 PowerShell 源代码中定义的视图创建的。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-144">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="9a0a9-145">有关用于创建此示例视图的视图和代码的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-145">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="9a0a9-146">`Get-ChildItem` 获取当前目录的内容 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-146">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="9a0a9-147">**DirectoryInfo** 和 **FileInfo** 对象将沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-147">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="9a0a9-148">`Format-Table`使用 **View** 参数指定包含 **CreationTime** 列的自定义视图 **mygciview** 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-148">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="9a0a9-149">的默认 `Format-Table` 输出 `Get-ChildItem` 不包括 **CreationTime** 列。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-149">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="9a0a9-150">示例5：使用表输出的属性</span><span class="sxs-lookup"><span data-stu-id="9a0a9-150">Example 5: Use properties for table output</span></span>

<span data-ttu-id="9a0a9-151">此示例使用 properties **参数在** 两个列表中显示计算机的所有服务，其中显示了 properties **Name** 和 **DependentServices**。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-151">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices**.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="9a0a9-152">`Get-Service` 获取计算机上的所有服务，并沿管道向下发送 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-152">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="9a0a9-153">`Format-Table` 使用 **Property** 参数来指定表中显示的 **Name** 和 **DependentServices** 属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-153">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="9a0a9-154">**Name** 和 **DependentServices** 是对象类型的两个属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-154">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="9a0a9-155">若要查看所有属性： `Get-Service | Get-Member -MemberType Properties` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-155">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="9a0a9-156">示例6：设置进程的格式并计算其运行时间</span><span class="sxs-lookup"><span data-stu-id="9a0a9-156">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="9a0a9-157">此示例显示一个表，其中包含本地计算机的 **记事本** 进程的进程名称和总运行时间。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-157">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="9a0a9-158">总运行时间是通过从当前时间减去每个进程的开始时间而计算出来的。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-158">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="9a0a9-159">`Get-Process` 获取所有本地计算机的 **记事本** 进程，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-159">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="9a0a9-160">`Format-Table` 显示一个表，其中包含两个列： **ProcessName**、 `Get-Process` property 和 **TotalRunningTime**，是计算属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-160">`Format-Table` displays a table with two columns: **ProcessName**, a `Get-Process` property, and **TotalRunningTime**, a calculated property.</span></span>

<span data-ttu-id="9a0a9-161">**TotalRunningTime** 属性由具有两个键（ **Label** 和 **Expression**）的哈希表指定。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-161">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression**.</span></span> <span data-ttu-id="9a0a9-162">**标签** 键指定属性名称。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-162">The **Label** key specifies the property name.</span></span> <span data-ttu-id="9a0a9-163">**表达式** 键指定计算。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-163">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="9a0a9-164">表达式获取每个进程对象的 **StartTime** 属性，并从命令的结果中减去该属性 `Get-Date` ，从而获取当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-164">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="9a0a9-165">示例7：格式化记事本进程</span><span class="sxs-lookup"><span data-stu-id="9a0a9-165">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="9a0a9-166">此示例使用 `Get-CimInstance` 来获取本地计算机上所有 **记事本** 进程的运行时间。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-166">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="9a0a9-167">可以 `Get-CimInstance` 与 **ComputerName** 参数一起使用，以从远程计算机获取信息。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-167">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="9a0a9-168">`Get-CimInstance` 获取 WMI **Win32_Process** 类的实例，该类描述名为 **notepad.exe** 的所有本地计算机的进程。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-168">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe**.</span></span> <span data-ttu-id="9a0a9-169">进程对象存储在 `$Processes` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-169">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="9a0a9-170">变量中的进程对象 `$Processes` 将沿管道向下发送到 `Format-Table` ，这将显示 **ProcessName** 属性和新的计算属性（ **总运行时间**）。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-170">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time**.</span></span>

<span data-ttu-id="9a0a9-171">该命令将新计算属性的名称（ **总运行时间**）分配给 **标签** 键。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-171">The command assigns the name of the new calculated property, **Total Running Time**, to the **Label** key.</span></span> <span data-ttu-id="9a0a9-172">**Expression** 键的脚本块将通过从当前日期中减去进程创建日期来计算进程的运行时间。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-172">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="9a0a9-173">`Get-Date`Cmdlet 获取当前日期。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-173">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="9a0a9-174">创建日期从当前日期中减去。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-174">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="9a0a9-175">结果是 **总运行时间** 的值。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-175">The result is the value of **Total Running Time**.</span></span>

### <span data-ttu-id="9a0a9-176">示例8：疑难解答格式错误</span><span class="sxs-lookup"><span data-stu-id="9a0a9-176">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="9a0a9-177">下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-177">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## <span data-ttu-id="9a0a9-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a0a9-178">PARAMETERS</span></span>

### <span data-ttu-id="9a0a9-179">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="9a0a9-179">-AutoSize</span></span>

<span data-ttu-id="9a0a9-180">指示该 cmdlet 基于数据的宽度来调整列的大小和列数。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-180">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="9a0a9-181">默认情况下，列大小和数量由视图确定。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-181">By default, the column size and number are determined by the view.</span></span>

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

### <span data-ttu-id="9a0a9-182">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="9a0a9-182">-DisplayError</span></span>

<span data-ttu-id="9a0a9-183">指示该 cmdlet 在命令行中显示错误。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-183">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="9a0a9-184">当你在命令中设置表达式的格式 `Format-Table` 并需要对表达式进行故障排除时，可以将此参数用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-184">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

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

### <span data-ttu-id="9a0a9-185">-Expand</span><span class="sxs-lookup"><span data-stu-id="9a0a9-185">-Expand</span></span>

<span data-ttu-id="9a0a9-186">指定集合对象和集合中的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-186">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="9a0a9-187">此参数旨在设置支持 [ICollection](/dotnet/api/system.collections.icollection) [ () ](/dotnet/api/system.collections) 接口的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-187">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="9a0a9-188">默认值为 **EnumOnly**。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-188">The default value is **EnumOnly**.</span></span>
<span data-ttu-id="9a0a9-189">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a0a9-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9a0a9-190">**EnumOnly**：显示集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-190">**EnumOnly**: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="9a0a9-191">**CoreOnly**：显示集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-191">**CoreOnly**: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="9a0a9-192">**Both**：显示集合对象的属性和集合中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-192">**Both**: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a0a9-193">-Force</span><span class="sxs-lookup"><span data-stu-id="9a0a9-193">-Force</span></span>

<span data-ttu-id="9a0a9-194">指示 cmdlet 指示 cmdlet 显示所有错误信息。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-194">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="9a0a9-195">与 **DisplayError** 或 **ShowError** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-195">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="9a0a9-196">默认情况下，当将错误对象写入到错误或显示流时，仅显示部分错误信息。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-196">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="9a0a9-197">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="9a0a9-197">-GroupBy</span></span>

<span data-ttu-id="9a0a9-198">基于属性值在单独的表中指定排序输出。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-198">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="9a0a9-199">例如，您可以使用 **GroupBy** 根据其状态在单独的表中列出服务。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-199">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="9a0a9-200">输入表达式或属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-200">Enter an expression or a property.</span></span> <span data-ttu-id="9a0a9-201">**GroupBy** 参数要求对对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-201">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="9a0a9-202">使用 `Sort-Object` cmdlet 将 `Format-Table` 对象分组。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-202">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="9a0a9-203">**GroupBy** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-203">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="9a0a9-204">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-204">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9a0a9-205">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="9a0a9-205">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9a0a9-206">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-206">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="9a0a9-207">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-207">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="9a0a9-208">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-208">FormatString - `<string>`</span></span>

<span data-ttu-id="9a0a9-209">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a0a9-210">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="9a0a9-210">-HideTableHeaders</span></span>

<span data-ttu-id="9a0a9-211">省略表中的列标题。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-211">Omits the column headings from the table.</span></span>

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

### <span data-ttu-id="9a0a9-212">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9a0a9-212">-InputObject</span></span>

<span data-ttu-id="9a0a9-213">指定要设置格式的对象。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-213">Specifies the objects to format.</span></span> <span data-ttu-id="9a0a9-214">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-214">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="9a0a9-215">-Property</span><span class="sxs-lookup"><span data-stu-id="9a0a9-215">-Property</span></span>

<span data-ttu-id="9a0a9-216">指定要在屏幕上显示的对象属性及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-216">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="9a0a9-217">键入一个或多个属性名称（以逗号分隔），或使用哈希表显示计算属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-217">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="9a0a9-218">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-218">Wildcards are permitted.</span></span>

<span data-ttu-id="9a0a9-219">如果省略此参数，则显示在显示中的属性将取决于第一个对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-219">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="9a0a9-220">例如，如果第一个对象具有 **PropertyA** 和 **PropertyB** ，但后续对象具有 **PropertyA**、 **PropertyB** 和 **PropertyC**，则只会显示 **PropertyA** 和 **PropertyB** 标头。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-220">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA**, **PropertyB**, and **PropertyC**, then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="9a0a9-221">**Property** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-221">The **Property** parameter is optional.</span></span> <span data-ttu-id="9a0a9-222">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-222">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="9a0a9-223">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-223">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="9a0a9-224">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-224">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9a0a9-225">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="9a0a9-225">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9a0a9-226">名称 (或标签) `<string>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-226">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="9a0a9-227">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-227">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="9a0a9-228">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-228">FormatString - `<string>`</span></span>
- <span data-ttu-id="9a0a9-229">Width- `<int32>` -必须大于 `0`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-229">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="9a0a9-230">对齐值可以是 `Left` 、 `Center` 或 `Right`</span><span class="sxs-lookup"><span data-stu-id="9a0a9-230">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="9a0a9-231">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-231">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9a0a9-232">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="9a0a9-232">-RepeatHeader</span></span>

<span data-ttu-id="9a0a9-233">在每个屏幕满后重复显示表的标头。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-233">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="9a0a9-234">当将输出通过管道传递给页导航（如或）或 `less` `more` 使用屏幕阅读器进行分页时，重复标头很有用。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-234">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

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

### <span data-ttu-id="9a0a9-235">-ShowError</span><span class="sxs-lookup"><span data-stu-id="9a0a9-235">-ShowError</span></span>

<span data-ttu-id="9a0a9-236">此参数通过管道发送错误。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-236">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="9a0a9-237">当你在命令中设置表达式的格式 `Format-Table` 并需要对表达式进行故障排除时，可以将此参数用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-237">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

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

### <span data-ttu-id="9a0a9-238">-View</span><span class="sxs-lookup"><span data-stu-id="9a0a9-238">-View</span></span>

<span data-ttu-id="9a0a9-239">从 PowerShell 6 开始，默认视图是在 PowerShell 源代码中定义的 `C#` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-239">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="9a0a9-240">Powershell `*.format.ps1xml` 6 及更高版本中不存在 powershell 5.1 及更早版本中的文件。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-240">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="9a0a9-241">使用 **View** 参数可以指定表的替代格式或自定义视图。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-241">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="9a0a9-242">可以使用默认的 PowerShell 视图或创建自定义视图。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-242">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="9a0a9-243">有关如何创建自定义视图的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-243">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="9a0a9-244">**View** 参数的替代视图和自定义视图必须使用表格式，否则将 `Format-Table` 失败。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-244">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="9a0a9-245">如果替代视图是一个列表，请使用 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-245">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="9a0a9-246">如果替代视图不是列表或表，请使用 `Format-Custom` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-246">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="9a0a9-247">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-247">You can't use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="9a0a9-248">-换行</span><span class="sxs-lookup"><span data-stu-id="9a0a9-248">-Wrap</span></span>

<span data-ttu-id="9a0a9-249">在下一行显示超过列宽的文本。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-249">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="9a0a9-250">默认情况下，超过列宽的文本将被截断。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-250">By default, text that exceeds the column width is truncated.</span></span>

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

### <span data-ttu-id="9a0a9-251">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a0a9-251">CommonParameters</span></span>

<span data-ttu-id="9a0a9-252">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-252">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a0a9-253">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-253">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a0a9-254">输入</span><span class="sxs-lookup"><span data-stu-id="9a0a9-254">INPUTS</span></span>

### <span data-ttu-id="9a0a9-255">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9a0a9-255">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9a0a9-256">可以将任何对象沿管道向下发送到 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-256">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="9a0a9-257">输出</span><span class="sxs-lookup"><span data-stu-id="9a0a9-257">OUTPUTS</span></span>

### <span data-ttu-id="9a0a9-258">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="9a0a9-258">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="9a0a9-259">`Format-Table` 返回表示表的格式对象。</span><span class="sxs-lookup"><span data-stu-id="9a0a9-259">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="9a0a9-260">注释</span><span class="sxs-lookup"><span data-stu-id="9a0a9-260">NOTES</span></span>

## <span data-ttu-id="9a0a9-261">相关链接</span><span class="sxs-lookup"><span data-stu-id="9a0a9-261">RELATED LINKS</span></span>

[<span data-ttu-id="9a0a9-262">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="9a0a9-262">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="9a0a9-263">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="9a0a9-263">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="9a0a9-264">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="9a0a9-264">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="9a0a9-265">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="9a0a9-265">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="9a0a9-266">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="9a0a9-266">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="9a0a9-267">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="9a0a9-267">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="9a0a9-268">Format-List</span><span class="sxs-lookup"><span data-stu-id="9a0a9-268">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="9a0a9-269">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="9a0a9-269">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="9a0a9-270">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="9a0a9-270">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="9a0a9-271">Get-Member</span><span class="sxs-lookup"><span data-stu-id="9a0a9-271">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="9a0a9-272">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="9a0a9-272">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="9a0a9-273">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="9a0a9-273">Update-FormatData</span></span>](Update-FormatData.md)
