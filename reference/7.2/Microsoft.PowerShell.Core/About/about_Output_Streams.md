---
description: 说明 PowerShell 中输出流的可用性和用途。
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 1dd6424ea14aa241b084a0a2c97a7e9bf6927518
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595842"
---
# <a name="about-output-streams"></a><span data-ttu-id="6b3a5-103">关于输出流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-103">About output streams</span></span>

## <a name="short-description"></a><span data-ttu-id="6b3a5-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="6b3a5-104">Short description</span></span>
<span data-ttu-id="6b3a5-105">说明 PowerShell 中输出流的可用性和用途。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-105">Explains the availability and purpose of output streams in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="6b3a5-106">长说明</span><span class="sxs-lookup"><span data-stu-id="6b3a5-106">Long description</span></span>

<span data-ttu-id="6b3a5-107">PowerShell 提供多个输出流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-107">PowerShell provides multiple output streams.</span></span> <span data-ttu-id="6b3a5-108">流为不同类型的消息提供通道。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-108">The streams provide channels for different types of messages.</span></span> <span data-ttu-id="6b3a5-109">你可以使用关联的 cmdlet 或重定向写入这些流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-109">You can write to these streams using the associated cmdlet or redirection.</span></span> <span data-ttu-id="6b3a5-110">有关详细信息，请参阅 [about_Redirection](about_Redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-110">For more information, see [about_Redirection](about_Redirection.md).</span></span>

<span data-ttu-id="6b3a5-111">PowerShell 支持以下输出流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-111">PowerShell supports the following output streams.</span></span>

| <span data-ttu-id="6b3a5-112">流#</span><span class="sxs-lookup"><span data-stu-id="6b3a5-112">Stream #</span></span> |      <span data-ttu-id="6b3a5-113">说明</span><span class="sxs-lookup"><span data-stu-id="6b3a5-113">Description</span></span>       | <span data-ttu-id="6b3a5-114">引入</span><span class="sxs-lookup"><span data-stu-id="6b3a5-114">Introduced in</span></span>  |    <span data-ttu-id="6b3a5-115">写入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b3a5-115">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="6b3a5-116">1</span><span class="sxs-lookup"><span data-stu-id="6b3a5-116">1</span></span>        | <span data-ttu-id="6b3a5-117">**成功** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-117">**Success** stream</span></span>     | <span data-ttu-id="6b3a5-118">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-118">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="6b3a5-119">2</span><span class="sxs-lookup"><span data-stu-id="6b3a5-119">2</span></span>        | <span data-ttu-id="6b3a5-120">**错误** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-120">**Error** stream</span></span>       | <span data-ttu-id="6b3a5-121">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-121">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="6b3a5-122">3</span><span class="sxs-lookup"><span data-stu-id="6b3a5-122">3</span></span>        | <span data-ttu-id="6b3a5-123">**警告** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-123">**Warning** stream</span></span>     | <span data-ttu-id="6b3a5-124">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-124">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="6b3a5-125">4</span><span class="sxs-lookup"><span data-stu-id="6b3a5-125">4</span></span>        | <span data-ttu-id="6b3a5-126">**详细** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-126">**Verbose** stream</span></span>     | <span data-ttu-id="6b3a5-127">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-127">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="6b3a5-128">5</span><span class="sxs-lookup"><span data-stu-id="6b3a5-128">5</span></span>        | <span data-ttu-id="6b3a5-129">**调试** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-129">**Debug** stream</span></span>       | <span data-ttu-id="6b3a5-130">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-130">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="6b3a5-131">6</span><span class="sxs-lookup"><span data-stu-id="6b3a5-131">6</span></span>        | <span data-ttu-id="6b3a5-132">**信息流**</span><span class="sxs-lookup"><span data-stu-id="6b3a5-132">**Information** stream</span></span> | <span data-ttu-id="6b3a5-133">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-133">PowerShell 5.0</span></span> | `Write-Information` |
| <span data-ttu-id="6b3a5-134">不适用</span><span class="sxs-lookup"><span data-stu-id="6b3a5-134">n/a</span></span>      | <span data-ttu-id="6b3a5-135">**进度** 流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-135">**Progress** stream</span></span>    | <span data-ttu-id="6b3a5-136">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="6b3a5-136">PowerShell 3.0</span></span> | `Write-Progress`    |

> [!NOTE]
> <span data-ttu-id="6b3a5-137">**进度** 流不支持重定向。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-137">The **Progress** stream does not support redirection.</span></span>

## <a name="success-stream"></a><span data-ttu-id="6b3a5-138">成功流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-138">Success stream</span></span>

<span data-ttu-id="6b3a5-139">**成功** 流是正常、成功结果的默认流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-139">The **Success** stream is the default stream for normal, successful results.</span></span>
<span data-ttu-id="6b3a5-140">使用 `Write-Output` cmdlet 将对象显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-140">Use the `Write-Output` cmdlet to explicitly write objects to this stream.</span></span> <span data-ttu-id="6b3a5-141">此流用于通过 PowerShell 管道传递对象。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-141">This stream is used for passing objects through the PowerShell pipeline.</span></span> <span data-ttu-id="6b3a5-142">**成功** 流连接到本机应用程序的 **stdout** 流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-142">The **Success** stream is connected to the **stdout** stream for native applications.</span></span>

## <a name="error-stream"></a><span data-ttu-id="6b3a5-143">错误流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-143">Error stream</span></span>

<span data-ttu-id="6b3a5-144">**错误** 流是错误结果的默认流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-144">The **Error** stream is the default stream for error results.</span></span> <span data-ttu-id="6b3a5-145">使用 `Write-Error` cmdlet 显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-145">Use the `Write-Error` cmdlet to explicitly write to this stream.</span></span> <span data-ttu-id="6b3a5-146">**错误** 流连接到本机应用程序的 **stderr** 流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-146">The **Error** stream is connected to the **stderr** stream for native applications.</span></span> <span data-ttu-id="6b3a5-147">在大多数情况下，这些错误可能会终止执行管道。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-147">Under most conditions, these errors can terminate the execution pipeline.</span></span> <span data-ttu-id="6b3a5-148">写入到此流的错误也会添加到 `$Error` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-148">Errors written to this stream are also added the the `$Error` automatic variable.</span></span> <span data-ttu-id="6b3a5-149">有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-149">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

## <a name="warning-stream"></a><span data-ttu-id="6b3a5-150">警告流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-150">Warning stream</span></span>

<span data-ttu-id="6b3a5-151">**警告** 流适用于不符合写入 **错误** 流的错误的错误条件。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-151">The **Warning** stream is intended for error conditions that are less severe than errors written to the **Error** stream.</span></span> <span data-ttu-id="6b3a5-152">正常情况下，这些警告不会终止执行。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-152">Under normal conditions, these warnings do not terminate execution.</span></span> <span data-ttu-id="6b3a5-153">警告不会写入 `$Error` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-153">Warnings are not written to the `$Error` automatic variable.</span></span> <span data-ttu-id="6b3a5-154">使用 `Write-Warning` cmdlet 显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-154">Use the `Write-Warning` cmdlet to explicitly write to this stream.</span></span>

## <a name="verbose-stream"></a><span data-ttu-id="6b3a5-155">详细流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-155">Verbose stream</span></span>

<span data-ttu-id="6b3a5-156">**详细** 流用于帮助用户在交互运行或从脚本中运行命令时排除其故障的消息。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-156">The **Verbose** stream is intended for messages that help users troubleshoot commands as they are run interactively or from a script.</span></span> <span data-ttu-id="6b3a5-157">使用 `Write-Verbose` cmdlet 将消息显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-157">Use the `Write-Verbose` cmdlet to explicitly write messages to this stream.</span></span> <span data-ttu-id="6b3a5-158">许多 cmdlet 提供详细的输出，有助于了解 cmdlet 的内部工作原理。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-158">Many cmdlets provide verbose output that is useful for understanding the internal workings of the cmdlet.</span></span> <span data-ttu-id="6b3a5-159">仅当使用 common 参数时，才会输出详细消息 `-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-159">The verbose messages are output only when you use the `-Verbose` common parameter.</span></span> <span data-ttu-id="6b3a5-160">有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-160">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="debug-stream"></a><span data-ttu-id="6b3a5-161">调试流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-161">Debug stream</span></span>

<span data-ttu-id="6b3a5-162">**调试** 流用于帮助脚本理解其代码失败的原因的消息。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-162">The **Debug** stream is used for messages that help scripters understand why their code is failing.</span></span> <span data-ttu-id="6b3a5-163">使用 `Write-Debug` cmdlet 显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-163">Use the `Write-Debug` cmdlet to explicitly write to this stream.</span></span> <span data-ttu-id="6b3a5-164">仅当使用 common 参数时，才会输出调试消息 `-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-164">The debug messages are output only when you use the `-Debug` common parameter.</span></span> <span data-ttu-id="6b3a5-165">有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-165">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="6b3a5-166">调试消息适用于比最终用户更多的脚本和 cmdlet 开发人员。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-166">Debug messages are intended for script and cmdlet developers more than end users.</span></span> <span data-ttu-id="6b3a5-167">这些调试消息可能包含深层故障排除所需的内部详细信息。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-167">These debug messages can contain internal details necessary for deep troubleshooting.</span></span>

## <a name="information-stream"></a><span data-ttu-id="6b3a5-168">信息流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-168">Information stream</span></span>

<span data-ttu-id="6b3a5-169">**信息流** 旨在提供帮助用户了解脚本正在执行的操作的消息。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-169">The **Information** stream is intended to provide message that help a user understand what a script is doing.</span></span> <span data-ttu-id="6b3a5-170">开发人员也可以使用它作为通过 PowerShell 传递信息的附加流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-170">It can also be used by developers as an additional stream used to pass information through PowerShell.</span></span> <span data-ttu-id="6b3a5-171">开发人员可以标记流数据，并对该流进行特定的处理。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-171">The developer can tag stream data and have specific handling for that stream.</span></span> <span data-ttu-id="6b3a5-172">使用 `Write-Information` cmdlet 显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-172">Use the `Write-Information` cmdlet to explicitly write to this stream.</span></span>

## <a name="progress-stream"></a><span data-ttu-id="6b3a5-173">进度流</span><span class="sxs-lookup"><span data-stu-id="6b3a5-173">Progress stream</span></span>

<span data-ttu-id="6b3a5-174">**进度** 流用于传达更长时间运行命令和脚本的进度的消息。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-174">The **Progress** stream is used for messages that communicate progress in longer running commands and scripts.</span></span> <span data-ttu-id="6b3a5-175">使用 `Write-Progress` cmdlet 将消息显式写入此流。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-175">Use the `Write-Progress` cmdlet to explicitly write messages to this stream.</span></span> <span data-ttu-id="6b3a5-176">**进度** 流不支持重定向。</span><span class="sxs-lookup"><span data-stu-id="6b3a5-176">The **Progress** stream does not support redirection.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b3a5-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b3a5-177">See also</span></span>

- [<span data-ttu-id="6b3a5-178">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="6b3a5-178">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="6b3a5-179">Write-Error</span><span class="sxs-lookup"><span data-stu-id="6b3a5-179">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="6b3a5-180">Write-Host</span><span class="sxs-lookup"><span data-stu-id="6b3a5-180">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="6b3a5-181">Write-Information</span><span class="sxs-lookup"><span data-stu-id="6b3a5-181">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="6b3a5-182">Write-Output</span><span class="sxs-lookup"><span data-stu-id="6b3a5-182">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="6b3a5-183">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="6b3a5-183">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="6b3a5-184">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="6b3a5-184">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="6b3a5-185">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="6b3a5-185">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="6b3a5-186">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b3a5-186">about_CommonParameters</span></span>](about_CommonParameters.md)
- [<span data-ttu-id="6b3a5-187">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="6b3a5-187">about_Redirection</span></span>](about_Redirection.md)
