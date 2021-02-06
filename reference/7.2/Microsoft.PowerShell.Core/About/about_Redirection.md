---
description: 说明如何将输出从 PowerShell 重定向到文本文件。
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 91eb3f524ddeeb729ce53749c9b0ae922ce21f18
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "99598900"
---
# <a name="about-redirection"></a><span data-ttu-id="b5602-103">关于重定向</span><span class="sxs-lookup"><span data-stu-id="b5602-103">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="b5602-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="b5602-104">Short description</span></span>
<span data-ttu-id="b5602-105">说明如何将输出从 PowerShell 重定向到文本文件。</span><span class="sxs-lookup"><span data-stu-id="b5602-105">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="b5602-106">长说明</span><span class="sxs-lookup"><span data-stu-id="b5602-106">Long description</span></span>

<span data-ttu-id="b5602-107">默认情况下，PowerShell 会将输出发送到 PowerShell 主机。</span><span class="sxs-lookup"><span data-stu-id="b5602-107">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="b5602-108">通常，这是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="b5602-108">Usually this is the console application.</span></span> <span data-ttu-id="b5602-109">但是，您可以将输出定向到一个文本文件，您可以将错误输出重定向到常规输出流。</span><span class="sxs-lookup"><span data-stu-id="b5602-109">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="b5602-110">您可以使用以下方法来重定向输出：</span><span class="sxs-lookup"><span data-stu-id="b5602-110">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="b5602-111">使用 `Out-File` cmdlet，该 cmdlet 将命令输出发送到文本文件。</span><span class="sxs-lookup"><span data-stu-id="b5602-111">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="b5602-112">通常， `Out-File` 需要使用 cmdlet （如 `Encoding` 、 `Force` 、 `Width` 或参数）时，请使用 cmdlet `NoClobber` 。</span><span class="sxs-lookup"><span data-stu-id="b5602-112">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="b5602-113">使用 `Tee-Object` cmdlet，该 cmdlet 将命令输出发送到文本文件，然后将其发送到管道。</span><span class="sxs-lookup"><span data-stu-id="b5602-113">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="b5602-114">使用 PowerShell 重定向运算符。</span><span class="sxs-lookup"><span data-stu-id="b5602-114">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="b5602-115">使用带有文件目标的重定向运算符在功能上等效于 `Out-File` 无额外参数的管道。</span><span class="sxs-lookup"><span data-stu-id="b5602-115">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="b5602-116">有关流的详细信息，请参阅 [about_Output_Streams](about_Output_Streams.md)。</span><span class="sxs-lookup"><span data-stu-id="b5602-116">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="b5602-117">可重定向输出流</span><span class="sxs-lookup"><span data-stu-id="b5602-117">Redirectable output streams</span></span>

<span data-ttu-id="b5602-118">PowerShell 支持以下输出流的重定向。</span><span class="sxs-lookup"><span data-stu-id="b5602-118">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="b5602-119">流#</span><span class="sxs-lookup"><span data-stu-id="b5602-119">Stream #</span></span> |      <span data-ttu-id="b5602-120">说明</span><span class="sxs-lookup"><span data-stu-id="b5602-120">Description</span></span>       | <span data-ttu-id="b5602-121">引入</span><span class="sxs-lookup"><span data-stu-id="b5602-121">Introduced in</span></span>  |    <span data-ttu-id="b5602-122">写入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5602-122">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="b5602-123">1</span><span class="sxs-lookup"><span data-stu-id="b5602-123">1</span></span>        | <span data-ttu-id="b5602-124">**成功** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-124">**Success** Stream</span></span>     | <span data-ttu-id="b5602-125">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="b5602-125">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="b5602-126">2</span><span class="sxs-lookup"><span data-stu-id="b5602-126">2</span></span>        | <span data-ttu-id="b5602-127">**错误** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-127">**Error** Stream</span></span>       | <span data-ttu-id="b5602-128">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="b5602-128">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="b5602-129">3</span><span class="sxs-lookup"><span data-stu-id="b5602-129">3</span></span>        | <span data-ttu-id="b5602-130">**警告** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-130">**Warning** Stream</span></span>     | <span data-ttu-id="b5602-131">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="b5602-131">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="b5602-132">4</span><span class="sxs-lookup"><span data-stu-id="b5602-132">4</span></span>        | <span data-ttu-id="b5602-133">**详细** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-133">**Verbose** Stream</span></span>     | <span data-ttu-id="b5602-134">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="b5602-134">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="b5602-135">5</span><span class="sxs-lookup"><span data-stu-id="b5602-135">5</span></span>        | <span data-ttu-id="b5602-136">**调试** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-136">**Debug** Stream</span></span>       | <span data-ttu-id="b5602-137">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="b5602-137">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="b5602-138">6</span><span class="sxs-lookup"><span data-stu-id="b5602-138">6</span></span>        | <span data-ttu-id="b5602-139">**信息** 流</span><span class="sxs-lookup"><span data-stu-id="b5602-139">**Information** Stream</span></span> | <span data-ttu-id="b5602-140">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b5602-140">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="b5602-141">所有流</span><span class="sxs-lookup"><span data-stu-id="b5602-141">All Streams</span></span>            | <span data-ttu-id="b5602-142">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="b5602-142">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="b5602-143">PowerShell 中还有一个 **进度** 流，但它不支持重定向。</span><span class="sxs-lookup"><span data-stu-id="b5602-143">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="b5602-144">PowerShell 重定向运算符</span><span class="sxs-lookup"><span data-stu-id="b5602-144">PowerShell redirection operators</span></span>

<span data-ttu-id="b5602-145">PowerShell 重定向运算符如下所示，其中 `n` 表示流号。</span><span class="sxs-lookup"><span data-stu-id="b5602-145">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="b5602-146"> `1` 如果未指定流，则 ( ) 的成功流为默认值。</span><span class="sxs-lookup"><span data-stu-id="b5602-146">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="b5602-147">操作员</span><span class="sxs-lookup"><span data-stu-id="b5602-147">Operator</span></span> |                         <span data-ttu-id="b5602-148">说明</span><span class="sxs-lookup"><span data-stu-id="b5602-148">Description</span></span>                         | <span data-ttu-id="b5602-149">语法</span><span class="sxs-lookup"><span data-stu-id="b5602-149">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="b5602-150">向文件发送指定的流。</span><span class="sxs-lookup"><span data-stu-id="b5602-150">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="b5602-151">将指定的流 **追加** 到文件中。</span><span class="sxs-lookup"><span data-stu-id="b5602-151">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="b5602-152">将指定的流 _重定向_ 到 **成功** 流。</span><span class="sxs-lookup"><span data-stu-id="b5602-152">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="b5602-153">与某些 Unix shell 不同，只能将其他流重定向到 **成功** 流。</span><span class="sxs-lookup"><span data-stu-id="b5602-153">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="b5602-154">示例</span><span class="sxs-lookup"><span data-stu-id="b5602-154">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="b5602-155">示例1：将错误和输出重定向到文件</span><span class="sxs-lookup"><span data-stu-id="b5602-155">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="b5602-156">此示例 `dir` 在一个将成功的项和一个将出错的项上运行。</span><span class="sxs-lookup"><span data-stu-id="b5602-156">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="b5602-157">它使用 `2>&1` 将 **错误** 流重定向到 **成功** 流，并将 `>` 结果 **成功** 流发送到名为的文件 `dir.log`</span><span class="sxs-lookup"><span data-stu-id="b5602-157">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="b5602-158">示例2：将所有成功流数据发送到文件</span><span class="sxs-lookup"><span data-stu-id="b5602-158">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="b5602-159">此示例将所有 **成功** 流数据发送到名为的文件 `script.log` 。</span><span class="sxs-lookup"><span data-stu-id="b5602-159">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="b5602-160">示例3：将成功、警告和错误流发送到文件</span><span class="sxs-lookup"><span data-stu-id="b5602-160">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="b5602-161">此示例演示如何组合重定向运算符以获得所需的结果。</span><span class="sxs-lookup"><span data-stu-id="b5602-161">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- <span data-ttu-id="b5602-162">`3>&1` 将 **警告** 流重定向到 **成功** 流。</span><span class="sxs-lookup"><span data-stu-id="b5602-162">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="b5602-163">`2>&1` 将 **错误** 流重定向到 **成功** 流 (后者现在同时包含所有 **警告** 流数据) </span><span class="sxs-lookup"><span data-stu-id="b5602-163">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="b5602-164">`>` 重定向 **成功** 流， (现在包含) 到名为的文件的 **警告** 和 **错误** 流 `C:\temp\redirection.log`) </span><span class="sxs-lookup"><span data-stu-id="b5602-164">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="b5602-165">示例4：将所有流重定向到文件</span><span class="sxs-lookup"><span data-stu-id="b5602-165">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="b5602-166">此示例将一个名为的脚本输出从一个名 `script.ps1` 为 `script.log`</span><span class="sxs-lookup"><span data-stu-id="b5602-166">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="b5602-167">示例5：禁止显示所有 Write-Host 和信息流数据</span><span class="sxs-lookup"><span data-stu-id="b5602-167">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="b5602-168">此示例将禁止显示所有信息流数据。</span><span class="sxs-lookup"><span data-stu-id="b5602-168">This example suppresses all information stream data.</span></span> <span data-ttu-id="b5602-169">若要了解有关 **信息流** cmdlet 的详细信息，请参阅 [写入主机](xref:Microsoft.PowerShell.Utility.Write-Host) 和 [写入信息](xref:Microsoft.PowerShell.Utility.Write-Information)</span><span class="sxs-lookup"><span data-stu-id="b5602-169">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="b5602-170">示例6：显示操作首选项的效果</span><span class="sxs-lookup"><span data-stu-id="b5602-170">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="b5602-171">操作首选项变量和参数可以更改写入特定流的内容。</span><span class="sxs-lookup"><span data-stu-id="b5602-171">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="b5602-172">此示例中的脚本显示的值如何 `$ErrorActionPreference` 影响写入 **错误** 流的内容。</span><span class="sxs-lookup"><span data-stu-id="b5602-172">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="b5602-173">当我们运行此脚本时 `$ErrorActionPreference` ，将在设置为时收到提示 `Inquire` 。</span><span class="sxs-lookup"><span data-stu-id="b5602-173">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="b5602-174">当我们检查日志文件时，将看到以下内容：</span><span class="sxs-lookup"><span data-stu-id="b5602-174">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="b5602-175">说明</span><span class="sxs-lookup"><span data-stu-id="b5602-175">Notes</span></span>

<span data-ttu-id="b5602-176">不会在不发出警告的情况下将数据追加 (`>` 和 `n>`) 覆盖指定文件的当前内容的重定向运算符。</span><span class="sxs-lookup"><span data-stu-id="b5602-176">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="b5602-177">但是，如果该文件是只读文件、隐藏文件或系统文件，则重定向 **会失败**。</span><span class="sxs-lookup"><span data-stu-id="b5602-177">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="b5602-178">追加重定向运算符 (`>>` 和 `n>>`) 不写入只读文件，但会将内容附加到系统文件或隐藏文件。</span><span class="sxs-lookup"><span data-stu-id="b5602-178">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="b5602-179">若要强制将内容重定向到只读、隐藏或系统文件，请使用 `Out-File` cmdlet 及其 `Force` 参数。</span><span class="sxs-lookup"><span data-stu-id="b5602-179">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="b5602-180">写入文件时，重定向运算符使用 `UTF8NoBOM` 编码。</span><span class="sxs-lookup"><span data-stu-id="b5602-180">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="b5602-181">如果文件具有不同的编码，则输出的格式可能不正确。</span><span class="sxs-lookup"><span data-stu-id="b5602-181">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="b5602-182">若要使用不同的编码写入文件，请使用 `Out-File` cmdlet 及其 `Encoding` 参数。</span><span class="sxs-lookup"><span data-stu-id="b5602-182">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="b5602-183">比较运算符可能产生混淆</span><span class="sxs-lookup"><span data-stu-id="b5602-183">Potential confusion with comparison operators</span></span>

<span data-ttu-id="b5602-184">`>`运算符不会与[大于](about_Comparison_Operators.md#-gt--ge--lt-and--le)比较运算符混淆， (通常 `>`) 的其他编程语言中表示为。</span><span class="sxs-lookup"><span data-stu-id="b5602-184">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt--ge--lt-and--le) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="b5602-185">根据所比较的对象，使用的输出 `>` 可能看起来是正确的 (因为36不大于 42) 。</span><span class="sxs-lookup"><span data-stu-id="b5602-185">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="b5602-186">但是，对本地文件系统的检查可以看到名为的文件 `42` 是用内容编写的 `36` 。</span><span class="sxs-lookup"><span data-stu-id="b5602-186">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="b5602-187">尝试使用反向比较 `<` (小于) 时，会产生系统错误：</span><span class="sxs-lookup"><span data-stu-id="b5602-187">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="b5602-188">如果数字比较是必需的操作， `-lt` 则 `-gt` 应使用。</span><span class="sxs-lookup"><span data-stu-id="b5602-188">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="b5602-189">有关详细信息，请参阅 `-gt` [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le)中的运算符。</span><span class="sxs-lookup"><span data-stu-id="b5602-189">For more information, see the `-gt` operator in [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5602-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="b5602-190">See also</span></span>

- [<span data-ttu-id="b5602-191">Out-File</span><span class="sxs-lookup"><span data-stu-id="b5602-191">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="b5602-192">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="b5602-192">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="b5602-193">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="b5602-193">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="b5602-194">Write-Error</span><span class="sxs-lookup"><span data-stu-id="b5602-194">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="b5602-195">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b5602-195">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="b5602-196">Write-Information</span><span class="sxs-lookup"><span data-stu-id="b5602-196">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="b5602-197">Write-Output</span><span class="sxs-lookup"><span data-stu-id="b5602-197">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="b5602-198">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="b5602-198">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="b5602-199">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="b5602-199">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="b5602-200">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="b5602-200">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="b5602-201">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="b5602-201">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="b5602-202">about_Operators</span><span class="sxs-lookup"><span data-stu-id="b5602-202">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="b5602-203">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="b5602-203">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="b5602-204">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="b5602-204">about_Path_Syntax</span></span>](about_Path_Syntax.md)
