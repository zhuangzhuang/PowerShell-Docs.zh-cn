---
description: 介绍如何使用 `Try` 、 `Catch` 和 `Finally` 块处理终止错误。
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596631"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="84f9d-103">关于 Try Catch Finally</span><span class="sxs-lookup"><span data-stu-id="84f9d-103">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="84f9d-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="84f9d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="84f9d-105">介绍如何使用 `Try` 、 `Catch` 和 `Finally` 块处理终止错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-105">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="84f9d-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="84f9d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="84f9d-107">使用 `Try` 、 `Catch` 和 `Finally` 块来响应或处理脚本中的终止错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-107">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="84f9d-108">`Trap`语句还可用于处理脚本中的终止错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-108">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="84f9d-109">有关详细信息，请参阅 [about_Trap](about_Trap.md)。</span><span class="sxs-lookup"><span data-stu-id="84f9d-109">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="84f9d-110">终止错误阻止语句运行。</span><span class="sxs-lookup"><span data-stu-id="84f9d-110">A terminating error stops a statement from running.</span></span> <span data-ttu-id="84f9d-111">如果 PowerShell 在某种程度上未处理终止错误，则 PowerShell 还会停止使用当前管道运行函数或脚本。</span><span class="sxs-lookup"><span data-stu-id="84f9d-111">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="84f9d-112">在其他语言（如 C）中， \# 终止错误称为 "异常"。</span><span class="sxs-lookup"><span data-stu-id="84f9d-112">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="84f9d-113">使用 " `Try` 块" 定义脚本中您希望 PowerShell 监视错误的部分。</span><span class="sxs-lookup"><span data-stu-id="84f9d-113">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="84f9d-114">当在块中发生错误时 `Try` ，该错误首先保存到 `$Error` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="84f9d-114">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="84f9d-115">然后，PowerShell 会搜索 `Catch` 块以处理错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-115">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="84f9d-116">如果该 `Try` 语句没有匹配的 `Catch` 块，则 PowerShell 将继续 `Catch` 在父范围内搜索适当的块或 `Trap` 语句。</span><span class="sxs-lookup"><span data-stu-id="84f9d-116">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="84f9d-117">`Catch`块完成后，或者如果找不到适当的 `Catch` 块或 `Trap` 语句，则 `Finally` 运行该块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-117">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="84f9d-118">如果无法处理错误，则会将错误写入错误流。</span><span class="sxs-lookup"><span data-stu-id="84f9d-118">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="84f9d-119">`Catch`块可以包含用于跟踪错误或恢复预期流的命令。</span><span class="sxs-lookup"><span data-stu-id="84f9d-119">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="84f9d-120">`Catch`块可以指定它所捕获的错误类型。</span><span class="sxs-lookup"><span data-stu-id="84f9d-120">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="84f9d-121">`Try` `Catch` 对于不同类型的错误，语句可以包含多个块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-121">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="84f9d-122">`Finally`块可用于释放脚本不再需要的任何资源。</span><span class="sxs-lookup"><span data-stu-id="84f9d-122">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="84f9d-123">`Try`、 `Catch` 和与 `Finally` `Try` `Catch` `Finally` C 编程语言中使用的、和关键字类似 \# 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-123">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="84f9d-124">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84f9d-124">SYNTAX</span></span>

<span data-ttu-id="84f9d-125">`Try`语句包含 `Try` 块、零个或多个 `Catch` 块以及零个或一个 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-125">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="84f9d-126">`Try`语句必须至少具有一个 `Catch` 块或一个 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-126">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="84f9d-127">下面显示了 `Try` 块语法：</span><span class="sxs-lookup"><span data-stu-id="84f9d-127">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="84f9d-128">`Try`关键字后跟括在大括号中的语句列表。</span><span class="sxs-lookup"><span data-stu-id="84f9d-128">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="84f9d-129">如果在语句列表中的语句正在运行时出现终止错误，则该脚本会将错误对象从块传递 `Try` 到适当的 `Catch` 块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-129">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="84f9d-130">下面显示了 `Catch` 块语法：</span><span class="sxs-lookup"><span data-stu-id="84f9d-130">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="84f9d-131">错误类型出现在括号中。</span><span class="sxs-lookup"><span data-stu-id="84f9d-131">Error types appear in brackets.</span></span> <span data-ttu-id="84f9d-132">最外面的括号指示元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="84f9d-132">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="84f9d-133">`Catch`关键字后跟一个可选的错误类型规范列表和一个语句列表。</span><span class="sxs-lookup"><span data-stu-id="84f9d-133">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="84f9d-134">如果块中发生终止错误 `Try` ，则 PowerShell 会搜索适当的 `Catch` 块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-134">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="84f9d-135">如果找到，则执行块中的语句 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-135">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="84f9d-136">`Catch`块可以指定一个或多个错误类型。</span><span class="sxs-lookup"><span data-stu-id="84f9d-136">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="84f9d-137">错误类型是 Microsoft .NET 框架异常或派生自 .NET Framework 异常的异常。</span><span class="sxs-lookup"><span data-stu-id="84f9d-137">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="84f9d-138">`Catch`块处理指定 .NET Framework 异常类或从指定类派生的任何类的错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-138">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="84f9d-139">如果 `Catch` 块指定错误类型，则该 `Catch` 块将处理该类型的错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-139">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="84f9d-140">如果 `Catch` 块未指定错误类型，则该块 `Catch` 处理在块中遇到的任何错误 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-140">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="84f9d-141">`Try`语句可以包含 `Catch` 不同指定错误类型的多个块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-141">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="84f9d-142">下面显示了 `Finally` 块语法：</span><span class="sxs-lookup"><span data-stu-id="84f9d-142">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="84f9d-143">`Finally`关键字后跟在每次运行脚本时都运行的语句列表，即使该语句在运行时 `Try` 没有错误或语句中捕获到错误 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-143">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="84f9d-144">请注意，按<kbd>CTRL</kbd> + <kbd>C</kbd>将停止管道。</span><span class="sxs-lookup"><span data-stu-id="84f9d-144">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="84f9d-145">发送到管道的对象将不会显示为输出。</span><span class="sxs-lookup"><span data-stu-id="84f9d-145">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="84f9d-146">因此，如果包括要显示的语句（如 "Finally block 已运行"），则在按下<kbd>CTRL</kbd>C 后将不会显示该语句（ + <kbd></kbd>即使该 `Finally` 块已运行）。</span><span class="sxs-lookup"><span data-stu-id="84f9d-146">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="84f9d-147">捕获错误</span><span class="sxs-lookup"><span data-stu-id="84f9d-147">CATCHING ERRORS</span></span>

<span data-ttu-id="84f9d-148">下面的示例脚本显示了一个块 `Try` `Catch` ：</span><span class="sxs-lookup"><span data-stu-id="84f9d-148">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="84f9d-149">`Catch`关键字必须紧跟在 `Try` 块或其他块之后 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-149">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="84f9d-150">PowerShell 无法将 "NonsenseString" 识别为 cmdlet 或其他项。</span><span class="sxs-lookup"><span data-stu-id="84f9d-150">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="84f9d-151">运行此脚本将返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="84f9d-151">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="84f9d-152">当脚本遇到 "NonsenseString" 时，会导致终止错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-152">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="84f9d-153">`Catch`块通过在块内运行语句列表来处理错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-153">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="84f9d-154">使用多个 CATCH 语句</span><span class="sxs-lookup"><span data-stu-id="84f9d-154">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="84f9d-155">`Try`语句可以有任意数量的 `Catch` 块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-155">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="84f9d-156">例如，以下脚本有一个下载的 `Try` 块 `MyDoc.doc` ，其中包含两个 `Catch` 块：</span><span class="sxs-lookup"><span data-stu-id="84f9d-156">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="84f9d-157">第一个 `Catch` 块处理 **系统 WebException** 和 **IOException** 类型的错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-157">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="84f9d-158">第二个 `Catch` 块未指定错误类型。</span><span class="sxs-lookup"><span data-stu-id="84f9d-158">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="84f9d-159">第二个 `Catch` 块处理发生的任何其他终止错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-159">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="84f9d-160">PowerShell 通过继承匹配错误类型。</span><span class="sxs-lookup"><span data-stu-id="84f9d-160">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="84f9d-161">`Catch`块处理指定 .NET Framework 异常类或从指定类派生的任何类的错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-161">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="84f9d-162">下面的示例包含 `Catch` 捕获 "找不到命令" 错误的块：</span><span class="sxs-lookup"><span data-stu-id="84f9d-162">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="84f9d-163">指定的错误类型 **system.management.automation.commandnotfoundexception** 继承自 **System.SystemException** 类型。</span><span class="sxs-lookup"><span data-stu-id="84f9d-163">The specified error type, **CommandNotFoundException**, inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="84f9d-164">以下示例还捕获了 "找不到命令" 错误：</span><span class="sxs-lookup"><span data-stu-id="84f9d-164">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="84f9d-165">此 `Catch` 块处理 "找不到命令" 错误以及从 **SystemException** 类型继承的其他错误。</span><span class="sxs-lookup"><span data-stu-id="84f9d-165">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="84f9d-166">如果指定错误类及其派生类之一，请将 `Catch` 派生类的块放在 `Catch` 常规类的块之前。</span><span class="sxs-lookup"><span data-stu-id="84f9d-166">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="84f9d-167">在 Try Catch 中使用陷阱</span><span class="sxs-lookup"><span data-stu-id="84f9d-167">Using Traps in a Try Catch</span></span>

<span data-ttu-id="84f9d-168">如果终止错误发生在块中 `Try` 定义的块中 `Trap` `Try` ，即使存在匹配的 `Catch` 块， `Trap` 语句也会获得控制权。</span><span class="sxs-lookup"><span data-stu-id="84f9d-168">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="84f9d-169">如果在 `Trap` 较高的块上存在 `Try` ，并且在当前范围内不存在匹配的 `Catch` 块，则 `Trap` 即使任何父作用域具有匹配的 `Catch` 块，也不会进行控制。</span><span class="sxs-lookup"><span data-stu-id="84f9d-169">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="84f9d-170">访问异常信息</span><span class="sxs-lookup"><span data-stu-id="84f9d-170">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="84f9d-171">在 `Catch` 块中，可以使用访问当前错误 `$_` ，这也称为 `$PSItem` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-171">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="84f9d-172">对象的类型为 **ErrorRecord**。</span><span class="sxs-lookup"><span data-stu-id="84f9d-172">The object is of type **ErrorRecord**.</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="84f9d-173">运行此脚本将返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="84f9d-173">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="84f9d-174">还可以访问其他属性，例如 **ScriptStackTrace**、 **Exception** 和 **ErrorDetails**。</span><span class="sxs-lookup"><span data-stu-id="84f9d-174">There are additional properties that can be accessed, such as **ScriptStackTrace**, **Exception**, and **ErrorDetails**.</span></span>  <span data-ttu-id="84f9d-175">例如，如果将脚本更改为以下内容：</span><span class="sxs-lookup"><span data-stu-id="84f9d-175">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="84f9d-176">结果将类似于：</span><span class="sxs-lookup"><span data-stu-id="84f9d-176">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="84f9d-177">使用 FINALLY 释放资源</span><span class="sxs-lookup"><span data-stu-id="84f9d-177">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="84f9d-178">若要释放脚本使用的资源，请在 `Finally` 和块后面添加块 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-178">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="84f9d-179">`Finally`不管 `Try` 块是否遇到终止错误，block 语句都将运行。</span><span class="sxs-lookup"><span data-stu-id="84f9d-179">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="84f9d-180">PowerShell 在 `Finally` 脚本终止之前或在当前块超出范围之前运行块。</span><span class="sxs-lookup"><span data-stu-id="84f9d-180">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="84f9d-181">`Finally`即使使用<kbd>CTRL</kbd> + <kbd>C</kbd>来停止脚本，块也会运行。</span><span class="sxs-lookup"><span data-stu-id="84f9d-181">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="84f9d-182">`Finally`如果 Exit 关键字从块内停止脚本，也会运行块 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="84f9d-182">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="84f9d-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84f9d-183">SEE ALSO</span></span>

[<span data-ttu-id="84f9d-184">about_Break</span><span class="sxs-lookup"><span data-stu-id="84f9d-184">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="84f9d-185">about_Continue</span><span class="sxs-lookup"><span data-stu-id="84f9d-185">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="84f9d-186">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="84f9d-186">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="84f9d-187">about_Throw</span><span class="sxs-lookup"><span data-stu-id="84f9d-187">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="84f9d-188">about_Trap</span><span class="sxs-lookup"><span data-stu-id="84f9d-188">about_Trap</span></span>](about_Trap.md)

