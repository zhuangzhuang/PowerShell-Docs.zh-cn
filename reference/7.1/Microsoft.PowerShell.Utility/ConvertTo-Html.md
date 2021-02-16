---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 1eade078765f93713da1f665e3ad6f062a1826d9
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529934"
---
# <span data-ttu-id="7845e-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="7845e-103">ConvertTo-Html</span></span>

## <span data-ttu-id="7845e-104">摘要</span><span class="sxs-lookup"><span data-stu-id="7845e-104">SYNOPSIS</span></span>
<span data-ttu-id="7845e-105">将.NET 对象转换为可以在 Web 浏览器中显示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="7845e-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="7845e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7845e-106">SYNTAX</span></span>

### <span data-ttu-id="7845e-107">Page（默认值）</span><span class="sxs-lookup"><span data-stu-id="7845e-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="7845e-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="7845e-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7845e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7845e-109">DESCRIPTION</span></span>

<span data-ttu-id="7845e-110">`ConvertTo-Html`Cmdlet 可将 .net 对象转换为可在 Web 浏览器中显示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="7845e-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="7845e-111">可使用此 cmdlet 在网页上显示命令的输出内容。</span><span class="sxs-lookup"><span data-stu-id="7845e-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="7845e-112">您可以使用的参数来 `ConvertTo-Html` 选择对象属性、指定表格或列表格式、指定 HTML 页面标题、在对象前后添加文本，以及仅返回表格或列表片段，而不是严格的 DTD 页面。</span><span class="sxs-lookup"><span data-stu-id="7845e-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="7845e-113">当你将多个对象提交到时 `ConvertTo-Html` ，PowerShell 会根据你提交的第一个对象的属性， (或列出) 。</span><span class="sxs-lookup"><span data-stu-id="7845e-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="7845e-114">如果剩余的对象不具有所指定的属性之一，则该对象的属性值为空单元。</span><span class="sxs-lookup"><span data-stu-id="7845e-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="7845e-115">如果剩余的对象有其他属性，这些属性值将不包括在文件中。</span><span class="sxs-lookup"><span data-stu-id="7845e-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="7845e-116">示例</span><span class="sxs-lookup"><span data-stu-id="7845e-116">EXAMPLES</span></span>

### <span data-ttu-id="7845e-117">示例1：创建显示日期的网页</span><span class="sxs-lookup"><span data-stu-id="7845e-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="7845e-118">此命令创建用来显示当前日期的属性的 HTML 页。</span><span class="sxs-lookup"><span data-stu-id="7845e-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="7845e-119">它使用 **InputObject** 参数将命令的结果提交 `Get-Date` 给 `ConvertTo-Html` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="7845e-120">示例2：创建显示 PowerShell 别名的网页</span><span class="sxs-lookup"><span data-stu-id="7845e-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="7845e-121">此命令创建一个 HTML 页面，其中列出了当前控制台中的 PowerShell 别名。</span><span class="sxs-lookup"><span data-stu-id="7845e-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="7845e-122">该命令使用 `Get-Alias` cmdlet 来获取别名。</span><span class="sxs-lookup"><span data-stu-id="7845e-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="7845e-123">它使用管道运算符 (`|`) 将别名发送到 `ConvertTo-Html` cmdlet，该 cmdlet 将创建 HTML 页。</span><span class="sxs-lookup"><span data-stu-id="7845e-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="7845e-124">该命令还使用 `Out-File` cmdlet 将 HTML 代码发送到该 `aliases.htm` 文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="7845e-125">示例3：创建网页以显示 PowerShell 事件</span><span class="sxs-lookup"><span data-stu-id="7845e-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="7845e-126">此命令会创建一个名为 `pslog.htm` 的 HTML 页面，用于显示本地计算机上 Windows PowerShell 事件日志中的事件。</span><span class="sxs-lookup"><span data-stu-id="7845e-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="7845e-127">它使用 `Get-EventLog` cmdlet 获取 Windows PowerShell 日志中的事件，然后使用管道运算符 (`|`) 将事件发送到 `ConvertTo-Html` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="7845e-128">该命令还使用 `Out-File` cmdlet 将 HTML 代码发送到该 `pslog.htm` 文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="7845e-129">该命令还使用 `Out-File` cmdlet 将 HTML 代码发送到该 `pslog.htm` 文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="7845e-130">示例4：创建显示进程的网页</span><span class="sxs-lookup"><span data-stu-id="7845e-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="7845e-131">这些命令创建并打开一个 HTML 页，该页列出了本地计算机上进程的名称、路径和所属公司。</span><span class="sxs-lookup"><span data-stu-id="7845e-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="7845e-132">第一个命令使用 `Get-Process` cmdlet 来获取表示在计算机上运行的进程的对象。</span><span class="sxs-lookup"><span data-stu-id="7845e-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="7845e-133">该命令使用管道运算符 (`|`) 将进程对象发送到 `ConvertTo-Html` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="7845e-134">该命令使用 **Property** 参数来选择要包括在表中的进程对象的三个属性。</span><span class="sxs-lookup"><span data-stu-id="7845e-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="7845e-135">该命令使用 **title** 参数来指定 HTML 页的标题。</span><span class="sxs-lookup"><span data-stu-id="7845e-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="7845e-136">该命令还使用 `Out-File` cmdlet 将生成的 HTML 发送到名为 Proc.htm 的文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="7845e-137">第二个命令使用 `Invoke-Item` cmdlet `Proc.htm` 在默认浏览器中打开。</span><span class="sxs-lookup"><span data-stu-id="7845e-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="7845e-138">示例5：创建网页以显示服务对象</span><span class="sxs-lookup"><span data-stu-id="7845e-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="7845e-139">此命令创建 cmdlet 返回的服务对象的 HTML 页 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="7845e-140">该命令使用 **CssUri** 参数来指定 HTML 页的级联样式表。</span><span class="sxs-lookup"><span data-stu-id="7845e-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="7845e-141">**CssUri** 参数向 `<link rel="stylesheet" type="text/css" href="test.css">` 生成的 HTML 添加其他标记。</span><span class="sxs-lookup"><span data-stu-id="7845e-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="7845e-142">标记中的 HREF 属性包含该样式表的名称。</span><span class="sxs-lookup"><span data-stu-id="7845e-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="7845e-143">示例6：创建网页以显示服务对象</span><span class="sxs-lookup"><span data-stu-id="7845e-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="7845e-144">此命令创建 cmdlet 返回的服务对象的 HTML 页 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="7845e-145">该命令使用 **As** 参数来指定列表格式。</span><span class="sxs-lookup"><span data-stu-id="7845e-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="7845e-146">Cmdlet `Out-File` 将生成的 HTML 发送到该 `Services.htm` 文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="7845e-147">示例7：为当前日期创建 web 表</span><span class="sxs-lookup"><span data-stu-id="7845e-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="7845e-148">此命令使用 `ConvertTo-Html` 生成当前日期的 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="7845e-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="7845e-149">该命令使用 `Get-Date` cmdlet 来获取当前日期。</span><span class="sxs-lookup"><span data-stu-id="7845e-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="7845e-150">它使用管道运算符 (|) 将结果发送到 `ConvertTo-Html` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="7845e-151">此 `ConvertTo-Html` 命令包含 **片段** 参数，该参数将输出限制为 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="7845e-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="7845e-152">因此，将忽略 HTML 页的其他元素，如 `<HEAD>` 和 `<BODY>` 标记。</span><span class="sxs-lookup"><span data-stu-id="7845e-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="7845e-153">示例8：创建网页以显示 PowerShell 事件</span><span class="sxs-lookup"><span data-stu-id="7845e-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="7845e-154">此命令使用 `Get-EventLog` cmdlet 从 Windows PowerShell 事件日志中获取事件。</span><span class="sxs-lookup"><span data-stu-id="7845e-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="7845e-155">它使用管道运算符 (`|`) 将事件发送到 `ConvertTo-Html` cmdlet，后者将事件转换为 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="7845e-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="7845e-156">该 `ConvertTo-Html` 命令使用 **Property** 参数来仅选择事件的 **ID**、 **Level** 和 **Task** 属性。</span><span class="sxs-lookup"><span data-stu-id="7845e-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID**, **Level**, and **Task** properties of the event.</span></span>

### <span data-ttu-id="7845e-157">示例9：创建显示指定服务的网页</span><span class="sxs-lookup"><span data-stu-id="7845e-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="7845e-158">此命令创建并打开一个网页，其中显示了计算机上以开头的服务。它使用的 **Title**、 **Body**、 **PreContent** 和 **PostContent** 参数 `ConvertTo-Html` 来自定义输出。</span><span class="sxs-lookup"><span data-stu-id="7845e-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title**, **Body**, **PreContent**, and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="7845e-159">该命令的第一部分使用 `Get-Service` cmdlet 来获取计算机上以开头的服务。该命令使用管道运算符 (`|`) 将结果发送到 `ConvertTo-Html` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="7845e-160">该命令还使用 `Out-File` cmdlet 将输出发送到 Services.htm 文件中。</span><span class="sxs-lookup"><span data-stu-id="7845e-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="7845e-161">分号 (`;`) 结束第一个命令并启动第二个命令，该命令使用 `Invoke-Item` cmdlet `Services.htm` 在默认浏览器中打开文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="7845e-162">示例10：设置 HTML 的元属性和字符集</span><span class="sxs-lookup"><span data-stu-id="7845e-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="7845e-163">此命令为网页创建 HTML，其中包含用于刷新、创作和关键字的元标记。</span><span class="sxs-lookup"><span data-stu-id="7845e-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="7845e-164">该页的字符集设置为 UTF-8</span><span class="sxs-lookup"><span data-stu-id="7845e-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="7845e-165">示例11：将 HTML 设置为 XHTML 过渡 DTD</span><span class="sxs-lookup"><span data-stu-id="7845e-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="7845e-166">此命令将返回的 HTML 的 DOCTYPE 设置为 XHTML 过渡 DTD</span><span class="sxs-lookup"><span data-stu-id="7845e-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="7845e-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7845e-167">PARAMETERS</span></span>

### <span data-ttu-id="7845e-168">-As</span><span class="sxs-lookup"><span data-stu-id="7845e-168">-As</span></span>

<span data-ttu-id="7845e-169">确定将对象设置为表格格式还是列表格式。</span><span class="sxs-lookup"><span data-stu-id="7845e-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="7845e-170">有效值为 **Table** 和 **List**。</span><span class="sxs-lookup"><span data-stu-id="7845e-170">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="7845e-171">默认值为 **Table**。</span><span class="sxs-lookup"><span data-stu-id="7845e-171">The default value is **Table**.</span></span>

<span data-ttu-id="7845e-172">**Table** 值会生成一个类似于 PowerShell 表格格式的 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="7845e-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="7845e-173">标题行显示属性名称。</span><span class="sxs-lookup"><span data-stu-id="7845e-173">The header row displays the property names.</span></span> <span data-ttu-id="7845e-174">表格的每一行表示一个对象，并显示该对象的每个属性值。</span><span class="sxs-lookup"><span data-stu-id="7845e-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="7845e-175">**列表** 值为每个对象生成一个两列的 HTML 表，其中每个对象都类似于 PowerShell 列表格式。</span><span class="sxs-lookup"><span data-stu-id="7845e-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="7845e-176">第一列显示属性名称。</span><span class="sxs-lookup"><span data-stu-id="7845e-176">The first column displays the property name.</span></span> <span data-ttu-id="7845e-177">第二列显示属性值。</span><span class="sxs-lookup"><span data-stu-id="7845e-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-178">-Body</span><span class="sxs-lookup"><span data-stu-id="7845e-178">-Body</span></span>

<span data-ttu-id="7845e-179">指定要在左 `<BODY>` 标记之后添加的文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="7845e-180">默认情况下，该位置没有文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-181">-字符集</span><span class="sxs-lookup"><span data-stu-id="7845e-181">-Charset</span></span>

<span data-ttu-id="7845e-182">指定要添加到开始标记的文本 `<charset>` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="7845e-183">默认情况下，该位置没有文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="7845e-184">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="7845e-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="7845e-185">-CssUri</span></span>

<span data-ttu-id="7845e-186">指定级联样式表 (CSS) 的统一资源标识符 (URI)，该 URI 适用于 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="7845e-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="7845e-187">输出中的样式表链接中包含该 URI。</span><span class="sxs-lookup"><span data-stu-id="7845e-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-188">-Fragment</span><span class="sxs-lookup"><span data-stu-id="7845e-188">-Fragment</span></span>

<span data-ttu-id="7845e-189">仅生成一个 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="7845e-189">Generates only an HTML table.</span></span> <span data-ttu-id="7845e-190">省略了 HTML、HEAD、TITLE 和 BODY 标记。</span><span class="sxs-lookup"><span data-stu-id="7845e-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-191">-Head</span><span class="sxs-lookup"><span data-stu-id="7845e-191">-Head</span></span>

<span data-ttu-id="7845e-192">指定 `<HEAD>` 标记的内容。</span><span class="sxs-lookup"><span data-stu-id="7845e-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="7845e-193">默认值为 `<title\>HTML TABLE</title>`。</span><span class="sxs-lookup"><span data-stu-id="7845e-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="7845e-194">如果使用 **Head** 参数，则将忽略 **Title** 参数。</span><span class="sxs-lookup"><span data-stu-id="7845e-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7845e-195">-InputObject</span></span>

<span data-ttu-id="7845e-196">指定要用 HTML 表示的对象。</span><span class="sxs-lookup"><span data-stu-id="7845e-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="7845e-197">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="7845e-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="7845e-198">如果使用此参数提交多个对象（如计算机上的所有服务），则将 `ConvertTo-Html` 创建一个表，该表显示集合的属性或对象的数组。</span><span class="sxs-lookup"><span data-stu-id="7845e-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="7845e-199">若要创建单个对象的表，请使用管道运算符通过管道将对象传递给 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="7845e-200">-元</span><span class="sxs-lookup"><span data-stu-id="7845e-200">-Meta</span></span>

<span data-ttu-id="7845e-201">指定要添加到开始标记的文本 `<meta>` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="7845e-202">默认情况下，该位置没有文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="7845e-203">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="7845e-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="7845e-204">-PostContent</span></span>

<span data-ttu-id="7845e-205">指定要在右 `</TABLE>` 标记之后添加的文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="7845e-206">默认情况下，该位置没有文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-206">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-207">-PreContent</span><span class="sxs-lookup"><span data-stu-id="7845e-207">-PreContent</span></span>

<span data-ttu-id="7845e-208">指定要在左 `<TABLE>` 标记之前添加的文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="7845e-209">默认情况下，该位置没有文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-209">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-210">-Property</span><span class="sxs-lookup"><span data-stu-id="7845e-210">-Property</span></span>

<span data-ttu-id="7845e-211">在 HTML 中包括所指定的对象属性。</span><span class="sxs-lookup"><span data-stu-id="7845e-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="7845e-212">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="7845e-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="7845e-213">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="7845e-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="7845e-214">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="7845e-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="7845e-215">在 PowerShell 3.x 中添加的名称 (或标签) `<string>` () </span><span class="sxs-lookup"><span data-stu-id="7845e-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="7845e-216">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="7845e-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="7845e-217">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="7845e-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="7845e-218">Width- `<int32>` -必须大于 `0`</span><span class="sxs-lookup"><span data-stu-id="7845e-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="7845e-219">对齐值可以是 `Left` 、 `Center` 或 `Right`</span><span class="sxs-lookup"><span data-stu-id="7845e-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="7845e-220">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7845e-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-221">-Title</span><span class="sxs-lookup"><span data-stu-id="7845e-221">-Title</span></span>

<span data-ttu-id="7845e-222">指定 HTML 文件的标题，即在 `<TITLE>` 标记之间显示的文本。</span><span class="sxs-lookup"><span data-stu-id="7845e-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-223">-过渡</span><span class="sxs-lookup"><span data-stu-id="7845e-223">-Transitional</span></span>

<span data-ttu-id="7845e-224">将 **doctype** 更改为 **xhtml 过渡 Dtd**，默认 **doctype** 为 **xhtml 严格 DTD**。</span><span class="sxs-lookup"><span data-stu-id="7845e-224">Changes the **DOCTYPE** to **XHTML Transitional DTD**, Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="7845e-225">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="7845e-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7845e-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7845e-226">CommonParameters</span></span>

<span data-ttu-id="7845e-227">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7845e-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7845e-228">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7845e-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7845e-229">输入</span><span class="sxs-lookup"><span data-stu-id="7845e-229">INPUTS</span></span>

### <span data-ttu-id="7845e-230">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="7845e-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7845e-231">可以通过管道将任何 .NET 对象传递给 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="7845e-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="7845e-232">输出</span><span class="sxs-lookup"><span data-stu-id="7845e-232">OUTPUTS</span></span>

### <span data-ttu-id="7845e-233">System.object 或 System.Xml.Xml文档</span><span class="sxs-lookup"><span data-stu-id="7845e-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="7845e-234">`ConvertTo-Html` 返回包含有效 HTML 的字符串序列。</span><span class="sxs-lookup"><span data-stu-id="7845e-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="7845e-235">注释</span><span class="sxs-lookup"><span data-stu-id="7845e-235">NOTES</span></span>

<span data-ttu-id="7845e-236">若要使用此 cmdlet，请通过管道将一个或多个对象传递给 cmdlet，或使用 **InputObject** 参数来指定对象。</span><span class="sxs-lookup"><span data-stu-id="7845e-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="7845e-237">当输入由多个对象组成时，这两种方法的输出将完全不同。</span><span class="sxs-lookup"><span data-stu-id="7845e-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="7845e-238">通过管道将多个对象传递给 cmdlet 时，PowerShell 会一次将对象发送到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7845e-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="7845e-239">因此， `ConvertTo-Html` 将创建一个显示单个对象的表。</span><span class="sxs-lookup"><span data-stu-id="7845e-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="7845e-240">例如，如果通过管道将计算机上的进程传递给 `ConvertTo-Html` ，则生成的表将显示所有进程。</span><span class="sxs-lookup"><span data-stu-id="7845e-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="7845e-241">当使用 **InputObject** 参数提交多个对象时，将 `ConvertTo-Html` 以集合或数组的形式接收这些对象。</span><span class="sxs-lookup"><span data-stu-id="7845e-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="7845e-242">因此，它会创建一个表格，该表格将显示数组及其属性，而非数组中的项。</span><span class="sxs-lookup"><span data-stu-id="7845e-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="7845e-243">例如，如果使用 **InputObject** 将计算机上的进程提交到 `ConvertTo-Html` ，则生成的表将显示对象数组及其属性。</span><span class="sxs-lookup"><span data-stu-id="7845e-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="7845e-244">为了符合 XHTML 严格 DTD 的要求，会相应地修改 DOCTYPE 标记：</span><span class="sxs-lookup"><span data-stu-id="7845e-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="7845e-245">相关链接</span><span class="sxs-lookup"><span data-stu-id="7845e-245">RELATED LINKS</span></span>

[<span data-ttu-id="7845e-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="7845e-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="7845e-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="7845e-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="7845e-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="7845e-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="7845e-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="7845e-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="7845e-250">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="7845e-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="7845e-251">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="7845e-251">Import-Clixml</span></span>](Import-Clixml.md)
