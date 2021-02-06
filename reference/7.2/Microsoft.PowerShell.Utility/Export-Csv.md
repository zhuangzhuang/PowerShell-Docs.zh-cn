---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: b0e889b95d2724dfa395b1b4a00b5c9ea878cc82
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99595609"
---
# <span data-ttu-id="37e52-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="37e52-102">Export-Csv</span></span>

## <span data-ttu-id="37e52-103">摘要</span><span class="sxs-lookup"><span data-stu-id="37e52-103">SYNOPSIS</span></span>
<span data-ttu-id="37e52-104">将对象转换为一系列逗号分隔值 (CSV) 字符串，并将字符串保存到文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="37e52-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="37e52-105">SYNTAX</span></span>

### <span data-ttu-id="37e52-106">Delimiter（默认值）</span><span class="sxs-lookup"><span data-stu-id="37e52-106">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="37e52-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="37e52-107">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="37e52-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="37e52-108">DESCRIPTION</span></span>

<span data-ttu-id="37e52-109">`Export-CSV`Cmdlet 可创建你提交的对象的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="37e52-110">每个对象都是一个行，其中包含以逗号分隔的对象属性值列表。</span><span class="sxs-lookup"><span data-stu-id="37e52-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="37e52-111">可以使用 `Export-CSV` cmdlet 创建电子表格并与接受 CSV 文件作为输入的程序共享数据。</span><span class="sxs-lookup"><span data-stu-id="37e52-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="37e52-112">在将对象发送到 cmdlet 之前，请不要设置它们的格式 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="37e52-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="37e52-113">如果 `Export-CSV` 接收格式化对象，则 CSV 文件包含格式属性而不是对象属性。</span><span class="sxs-lookup"><span data-stu-id="37e52-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="37e52-114">若要仅导出对象的选定属性，请使用 `Select-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="37e52-115">示例</span><span class="sxs-lookup"><span data-stu-id="37e52-115">EXAMPLES</span></span>

### <span data-ttu-id="37e52-116">示例1：将进程属性导出到 CSV 文件</span><span class="sxs-lookup"><span data-stu-id="37e52-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="37e52-117">此示例选择具有特定属性的 **进程** 对象，将对象导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="37e52-118">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="37e52-119">**Name** 参数将输出筛选为仅包含 WmiPrvSE 进程对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="37e52-120">进程对象将通过管道向下发送到 `Select-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="37e52-121">`Select-Object` 使用 **Property** 参数选择进程对象属性的子集。</span><span class="sxs-lookup"><span data-stu-id="37e52-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="37e52-122">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-123">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="37e52-124">**Path** 参数指定将 WmiData.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-125">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-126">`Import-Csv`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-127">示例2：将进程导出到逗号分隔的文件</span><span class="sxs-lookup"><span data-stu-id="37e52-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="37e52-128">此示例获取 **进程** 对象并将对象导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="37e52-129">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="37e52-130">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-131">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="37e52-132">**Path** 参数指定将 Processes.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-133">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-134">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-135">示例3：将进程导出为分号分隔的文件</span><span class="sxs-lookup"><span data-stu-id="37e52-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="37e52-136">此示例获取 **进程** 对象并将对象导出到带有分号分隔符的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="37e52-137">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="37e52-138">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-139">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="37e52-140">**Path** 参数指定将 Processes.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-141">**分隔符** 参数指定用分号分隔字符串值。</span><span class="sxs-lookup"><span data-stu-id="37e52-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="37e52-142">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-143">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-144">示例4：使用当前区域性的列表分隔符导出进程</span><span class="sxs-lookup"><span data-stu-id="37e52-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="37e52-145">此示例获取 **进程** 对象并将对象导出到文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="37e52-146">分隔符为当前区域性的列表分隔符。</span><span class="sxs-lookup"><span data-stu-id="37e52-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="37e52-147">该 `Get-Culture` cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** ，并显示当前区域性的默认列表分隔符。</span><span class="sxs-lookup"><span data-stu-id="37e52-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="37e52-148">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="37e52-149">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-150">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="37e52-151">**Path** 参数指定将 Processes.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-152">**UseCulture** 参数使用当前区域性的默认列表分隔符作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="37e52-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="37e52-153">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-154">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-155">示例5：导出具有类型信息的进程</span><span class="sxs-lookup"><span data-stu-id="37e52-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="37e52-156">此示例说明如何将 **#TYPE** 标头信息包含在 CSV 文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="37e52-157">**#TYPE** 标头在 PowerShell 6.0 之前的版本中是默认标头。</span><span class="sxs-lookup"><span data-stu-id="37e52-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="37e52-158">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="37e52-159">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-160">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="37e52-161">**Path** 参数指定将 Processes.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-162">**IncludeTypeInformation** 在 CSV 输出中包含 **#TYPE** 信息标头。</span><span class="sxs-lookup"><span data-stu-id="37e52-162">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="37e52-163">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-164">示例6：将对象导出并追加到 CSV 文件</span><span class="sxs-lookup"><span data-stu-id="37e52-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="37e52-165">此示例说明如何将对象导出到 CSV 文件，并使用 **Append** 参数将对象添加到现有文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="37e52-166">`Get-Service`Cmdlet 将获取服务对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="37e52-167">**DisplayName** 参数返回包含 Word 应用程序的服务。</span><span class="sxs-lookup"><span data-stu-id="37e52-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="37e52-168">服务对象将通过管道向下发送到 `Select-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="37e52-169">`Select-Object` 使用 **Property** 参数来指定 **DisplayName** 和 **Status** 属性。</span><span class="sxs-lookup"><span data-stu-id="37e52-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="37e52-170">`$AppService`变量存储对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="37e52-171">`$AppService`对象通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-172">`Export-Csv` 将服务对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="37e52-173">**Path** 参数指定将 Services.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-174">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-175">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="37e52-176">`Get-Service`和 `Select-Object` cmdlet 对于包含 word Windows 的服务重复。</span><span class="sxs-lookup"><span data-stu-id="37e52-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="37e52-177">`$WinService`变量存储服务对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="37e52-178">`Export-Csv`Cmdlet 使用 **Append** 参数指定将 `$WinService` 对象添加到现有 Services.csv 文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="37e52-179">此 `Get-Content` cmdlet 将重复显示已更新的文件，其中包含追加的数据。</span><span class="sxs-lookup"><span data-stu-id="37e52-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="37e52-180">示例7：管道内的格式 cmdlet 产生意外的结果</span><span class="sxs-lookup"><span data-stu-id="37e52-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="37e52-181">此示例说明为什么不在管道内使用格式 cmdlet 很重要。</span><span class="sxs-lookup"><span data-stu-id="37e52-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="37e52-182">收到意外的输出时，会对管道语法进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="37e52-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="37e52-183">`Get-Date`Cmdlet 将获取 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="37e52-184">对象通过管道向下发送到 `Select-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="37e52-185">`Select-Object` 使用 **Property** 参数来选择对象属性的子集。</span><span class="sxs-lookup"><span data-stu-id="37e52-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="37e52-186">对象通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-187">`Export-Csv` 将对象转换为 CSV 格式。</span><span class="sxs-lookup"><span data-stu-id="37e52-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="37e52-188">**Path** 参数指定将 DateTime.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-189">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-190">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="37e52-191">当在 `Format-Table` 管道中使用 cmdlet 来选择属性时，会收到意外结果。</span><span class="sxs-lookup"><span data-stu-id="37e52-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="37e52-192">`Format-Table` 将表格式对象向下发送到 `Export-Csv` cmdlet，而不是 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="37e52-193">`Export-Csv` 将表格式对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="37e52-194">`Get-Content`Cmdlet 显示包含表格式对象的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="37e52-195">示例8：使用 Force 参数覆盖只读文件</span><span class="sxs-lookup"><span data-stu-id="37e52-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="37e52-196">此示例创建一个空的只读文件，并使用 **Force** 参数更新该文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="37e52-197">`New-Item`Cmdlet 使用 **Path** 和 **ItemType** 参数创建当前目录中的 ReadOnly.csv 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="37e52-198">`Set-ItemProperty`Cmdlet 使用 **Name** 和 **Value** 参数将文件的 **IsReadOnly** 属性更改为 true。</span><span class="sxs-lookup"><span data-stu-id="37e52-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="37e52-199">`Get-Process`Cmdlet 将获取 **进程** 对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="37e52-200">进程对象将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-201">`Export-Csv` 将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="37e52-202">**Path** 参数指定将 ReadOnly.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="37e52-203">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="37e52-204">输出显示该文件未写入，因为访问被拒绝。</span><span class="sxs-lookup"><span data-stu-id="37e52-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="37e52-205">将 **force** 参数添加到 `Export-Csv` cmdlet，以强制将导出写入文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="37e52-206">`Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-207">示例9：将 Force 参数与 Append 一起使用</span><span class="sxs-lookup"><span data-stu-id="37e52-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="37e52-208">此示例演示如何使用 **Force** 和 **Append** 参数。</span><span class="sxs-lookup"><span data-stu-id="37e52-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="37e52-209">如果组合这些参数，则不匹配的对象属性可以写入 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="37e52-210">表达式使用 **Name** 和 **Version** 属性创建 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="37e52-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="37e52-211">值存储在 `$Content` 变量中。</span><span class="sxs-lookup"><span data-stu-id="37e52-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="37e52-212">该 `$Content` 变量将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-213">`Export-Csv` 使用 **Path** 参数，并将 ParmFile.csv 文件保存到当前目录中。</span><span class="sxs-lookup"><span data-stu-id="37e52-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="37e52-214">**NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。</span><span class="sxs-lookup"><span data-stu-id="37e52-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="37e52-215">另一个表达式将创建 **PSCustomObject** ，其 **名称** 和 **版本** 属性为。</span><span class="sxs-lookup"><span data-stu-id="37e52-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="37e52-216">值存储在 `$AdditionalContent` 变量中。</span><span class="sxs-lookup"><span data-stu-id="37e52-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="37e52-217">该 `$AdditionalContent` 变量将通过管道向下发送到 `Export-Csv` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37e52-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="37e52-218">**Append** 参数用于向文件添加数据。</span><span class="sxs-lookup"><span data-stu-id="37e52-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="37e52-219">追加 **失败，因为\*\*\*\*版本** 和版本之间存在属性名称不匹配的情况。</span><span class="sxs-lookup"><span data-stu-id="37e52-219">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="37e52-220">`Export-Csv`Cmdlet **force** 参数用于强制导出写入文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="37e52-221">将丢弃 **Edition** 属性。</span><span class="sxs-lookup"><span data-stu-id="37e52-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="37e52-222">`Import-Csv`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="37e52-223">示例10：导出到 CSV，并在两列两侧加上引号</span><span class="sxs-lookup"><span data-stu-id="37e52-223">Example 10: Export to CSV with quotes around two columns</span></span>

<span data-ttu-id="37e52-224">此示例将 **DateTime** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-224">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="37e52-225">示例11：仅在需要时导出到 CSV 且仅包含引号</span><span class="sxs-lookup"><span data-stu-id="37e52-225">Example 11: Export to CSV with quotes only when needed</span></span>

<span data-ttu-id="37e52-226">此示例将 **DateTime** 对象转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-226">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="37e52-227">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="37e52-227">PARAMETERS</span></span>

### <span data-ttu-id="37e52-228">-Append</span><span class="sxs-lookup"><span data-stu-id="37e52-228">-Append</span></span>

<span data-ttu-id="37e52-229">使用此参数可 `Export-CSV` 将 CSV 输出添加到指定文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="37e52-229">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="37e52-230">如果没有此参数， `Export-CSV` 则替换文件内容而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="37e52-230">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="37e52-231">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="37e52-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="37e52-232">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="37e52-232">-Delimiter</span></span>

<span data-ttu-id="37e52-233">指定分隔符以分隔属性值。</span><span class="sxs-lookup"><span data-stu-id="37e52-233">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="37e52-234">默认值为逗号 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="37e52-234">The default is a comma (`,`).</span></span> <span data-ttu-id="37e52-235">输入一个字符，例如冒号 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="37e52-235">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="37e52-236">若要指定分号 (`;`) ，请将其括在引号中。</span><span class="sxs-lookup"><span data-stu-id="37e52-236">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-237">-Encoding</span><span class="sxs-lookup"><span data-stu-id="37e52-237">-Encoding</span></span>

<span data-ttu-id="37e52-238">为导出的 CSV 文件指定编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-238">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="37e52-239">默认值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="37e52-239">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="37e52-240">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="37e52-240">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="37e52-241">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-241">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="37e52-242">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-242">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="37e52-243">`bigendianutf32`：使用大字节序字节顺序编码为32格式。</span><span class="sxs-lookup"><span data-stu-id="37e52-243">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="37e52-244">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-244">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="37e52-245">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-245">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="37e52-246">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-246">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="37e52-247">`utf8`：以 UTF-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-247">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="37e52-248">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="37e52-248">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="37e52-249">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="37e52-249">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="37e52-250">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="37e52-250">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="37e52-251">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="37e52-251">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="37e52-252">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)</span><span class="sxs-lookup"><span data-stu-id="37e52-252">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="37e52-253">不建议使用 **utf-7** _ _。</span><span class="sxs-lookup"><span data-stu-id="37e52-253">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="37e52-254">在 PowerShell 7.1 中，如果 `utf7` 为 _ *Encoding*\* 参数指定，则会写入警告。</span><span class="sxs-lookup"><span data-stu-id="37e52-254">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-255">-Force</span><span class="sxs-lookup"><span data-stu-id="37e52-255">-Force</span></span>

<span data-ttu-id="37e52-256">此参数允许 `Export-Csv` 覆盖具有 **只读** 属性的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-256">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="37e52-257">合并 **Force** 和 **Append** 参数时，可以将包含不匹配的属性的对象写入 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-257">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="37e52-258">只有与匹配的属性才会写入文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-258">Only the properties that match are written to the file.</span></span> <span data-ttu-id="37e52-259">放弃不匹配的属性。</span><span class="sxs-lookup"><span data-stu-id="37e52-259">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="37e52-260">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="37e52-260">-IncludeTypeInformation</span></span>

<span data-ttu-id="37e52-261">使用此参数时，CSV 输出的第一行包含 **#TYPE** 后跟对象类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="37e52-261">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="37e52-262">例如， **#TYPE**"。</span><span class="sxs-lookup"><span data-stu-id="37e52-262">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="37e52-263">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="37e52-263">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-264">-InputObject</span><span class="sxs-lookup"><span data-stu-id="37e52-264">-InputObject</span></span>

<span data-ttu-id="37e52-265">指定要导出为 CSV 字符串的对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-265">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="37e52-266">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="37e52-266">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="37e52-267">还可以通过管道将对象传递给 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="37e52-267">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-268">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="37e52-268">-LiteralPath</span></span>

<span data-ttu-id="37e52-269">指定指向 CSV 输出文件的路径。</span><span class="sxs-lookup"><span data-stu-id="37e52-269">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="37e52-270">与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="37e52-270">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="37e52-271">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="37e52-271">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="37e52-272">如果路径包含转义符，请使用单引号。</span><span class="sxs-lookup"><span data-stu-id="37e52-272">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="37e52-273">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="37e52-273">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-274">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="37e52-274">-NoClobber</span></span>

<span data-ttu-id="37e52-275">使用此参数，以便不 `Export-CSV` 会覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-275">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="37e52-276">默认情况下，如果文件存在于指定的路径中，则 `Export-CSV` 将覆盖该文件而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="37e52-276">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-277">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="37e52-277">-NoTypeInformation</span></span>

<span data-ttu-id="37e52-278">从输出中删除 **#TYPE** 信息标头。</span><span class="sxs-lookup"><span data-stu-id="37e52-278">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="37e52-279">此参数已成为 PowerShell 6.0 中的默认参数，包含它是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="37e52-279">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-280">-Path</span><span class="sxs-lookup"><span data-stu-id="37e52-280">-Path</span></span>

<span data-ttu-id="37e52-281">一个必需的参数，用于指定要保存 CSV 输出文件的位置。</span><span class="sxs-lookup"><span data-stu-id="37e52-281">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-282">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="37e52-282">-UseCulture</span></span>

<span data-ttu-id="37e52-283">将当前区域性的列表分隔符用作项分隔符。</span><span class="sxs-lookup"><span data-stu-id="37e52-283">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="37e52-284">若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="37e52-284">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-285">-Confirm</span><span class="sxs-lookup"><span data-stu-id="37e52-285">-Confirm</span></span>

<span data-ttu-id="37e52-286">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="37e52-286">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="37e52-287">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="37e52-287">-WhatIf</span></span>

<span data-ttu-id="37e52-288">阻止对 cmdlet 进行处理或更改。</span><span class="sxs-lookup"><span data-stu-id="37e52-288">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="37e52-289">此输出显示了在运行 cmdlet 后将发生的情况。</span><span class="sxs-lookup"><span data-stu-id="37e52-289">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="37e52-290">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="37e52-290">-QuoteFields</span></span>

<span data-ttu-id="37e52-291">指定应括起来的列的名称。</span><span class="sxs-lookup"><span data-stu-id="37e52-291">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="37e52-292">使用此参数时，只有指定的列被括起来。</span><span class="sxs-lookup"><span data-stu-id="37e52-292">When this parameter is used, only the specified columns are quoted.</span></span> <span data-ttu-id="37e52-293">此参数是在 PowerShell 7.0 中添加的。</span><span class="sxs-lookup"><span data-stu-id="37e52-293">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-294">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="37e52-294">-UseQuotes</span></span>

<span data-ttu-id="37e52-295">指定在 CSV 文件中使用引号的时间。</span><span class="sxs-lookup"><span data-stu-id="37e52-295">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="37e52-296">可能的值有：</span><span class="sxs-lookup"><span data-stu-id="37e52-296">Possible values are:</span></span>

- <span data-ttu-id="37e52-297">从不-不引用任何内容</span><span class="sxs-lookup"><span data-stu-id="37e52-297">Never - don't quote anything</span></span>
- <span data-ttu-id="37e52-298">始终将所有内容都括 (默认行为) </span><span class="sxs-lookup"><span data-stu-id="37e52-298">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="37e52-299">AsNeeded-仅包含分隔符字符的引号字段</span><span class="sxs-lookup"><span data-stu-id="37e52-299">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="37e52-300">此参数是在 PowerShell 7.0 中添加的。</span><span class="sxs-lookup"><span data-stu-id="37e52-300">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37e52-301">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37e52-301">CommonParameters</span></span>

<span data-ttu-id="37e52-302">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="37e52-302">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37e52-303">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="37e52-303">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="37e52-304">输入</span><span class="sxs-lookup"><span data-stu-id="37e52-304">INPUTS</span></span>

### <span data-ttu-id="37e52-305">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="37e52-305">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="37e52-306">可以通过管道将具有扩展类型系统 (ETS) 适配器的任何对象传递给 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="37e52-306">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="37e52-307">输出</span><span class="sxs-lookup"><span data-stu-id="37e52-307">OUTPUTS</span></span>

### <span data-ttu-id="37e52-308">System.String</span><span class="sxs-lookup"><span data-stu-id="37e52-308">System.String</span></span>

<span data-ttu-id="37e52-309">CSV 列表将发送到 Path 参数中指定的文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-309">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="37e52-310">注释</span><span class="sxs-lookup"><span data-stu-id="37e52-310">NOTES</span></span>

<span data-ttu-id="37e52-311">`Export-CSV`Cmdlet 将提交的对象转换为一系列 CSV 字符串，并将它们保存在指定的文本文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-311">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="37e52-312">你可以使用将 `Export-CSV -IncludeTypeInformation` 对象保存在 csv 文件中，然后使用 `Import-Csv` CMDLET 从 csv 文件中的文本创建对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-312">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="37e52-313">在 CSV 文件中，通过以逗号分隔的对象属性值列表来表示每个对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-313">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="37e52-314">使用 **ToString ( # B1** 方法将属性值转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-314">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="37e52-315">字符串由属性值名称表示。</span><span class="sxs-lookup"><span data-stu-id="37e52-315">The strings are represented by the property value name.</span></span> <span data-ttu-id="37e52-316">`Export-CSV -IncludeTypeInformation` 不导出对象的方法。</span><span class="sxs-lookup"><span data-stu-id="37e52-316">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="37e52-317">CSV 字符串的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="37e52-317">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="37e52-318">如果使用了 **IncludeTypeInformation** ，则第一个字符串包含后跟对象类型的完全限定名称的 **#TYPE** 信息标头。</span><span class="sxs-lookup"><span data-stu-id="37e52-318">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="37e52-319">例如， **#TYPE**"。</span><span class="sxs-lookup"><span data-stu-id="37e52-319">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="37e52-320">如果未使用 **IncludeTypeInformation** ，则第一个字符串包括列标题。</span><span class="sxs-lookup"><span data-stu-id="37e52-320">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="37e52-321">标头以逗号分隔的列表的形式包含第一个对象的属性名称。</span><span class="sxs-lookup"><span data-stu-id="37e52-321">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="37e52-322">其余字符串包含每个对象的属性值的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="37e52-322">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="37e52-323">从 PowerShell 6.0 开始，的默认行为 `Export-CSV` 是不包括 CSV 中的 **#TYPE** 信息，并且 **NoTypeInformation** 是隐含的。</span><span class="sxs-lookup"><span data-stu-id="37e52-323">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="37e52-324">**IncludeTypeInformation** 可用于包含 **#TYPE** 信息并模拟 `Export-CSV` PowerShell 6.0 之前的默认行为。</span><span class="sxs-lookup"><span data-stu-id="37e52-324">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="37e52-325">当你将多个对象提交到时 `Export-CSV` ，将 `Export-CSV` 根据你提交的第一个对象的属性来组织文件。</span><span class="sxs-lookup"><span data-stu-id="37e52-325">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="37e52-326">如果剩余的对象没有指定的属性之一，则该对象的属性值为 null，由两个连续的逗号表示。</span><span class="sxs-lookup"><span data-stu-id="37e52-326">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="37e52-327">如果剩余的对象有其他属性，这些属性值将不包括在文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-327">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="37e52-328">可以使用 `Import-Csv` cmdlet 从文件中的 CSV 字符串重新创建对象。</span><span class="sxs-lookup"><span data-stu-id="37e52-328">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="37e52-329">生成的对象是原始对象的 CSV 版本，这些版本由属性值的字符串表示形式组成，且不包括方法。</span><span class="sxs-lookup"><span data-stu-id="37e52-329">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="37e52-330">`ConvertTo-Csv`和 `ConvertFrom-Csv` cmdlet 将对象转换为 csv 字符串，并将对象转换为 csv 字符串。</span><span class="sxs-lookup"><span data-stu-id="37e52-330">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="37e52-331">`Export-CSV` 与相同 `ConvertTo-CSV` ，只不过它将 CSV 字符串保存在文件中。</span><span class="sxs-lookup"><span data-stu-id="37e52-331">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="37e52-332">相关链接</span><span class="sxs-lookup"><span data-stu-id="37e52-332">RELATED LINKS</span></span>

[<span data-ttu-id="37e52-333">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="37e52-333">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="37e52-334">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="37e52-334">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="37e52-335">Format-Table</span><span class="sxs-lookup"><span data-stu-id="37e52-335">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="37e52-336">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="37e52-336">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="37e52-337">Select-Object</span><span class="sxs-lookup"><span data-stu-id="37e52-337">Select-Object</span></span>](Select-Object.md)
