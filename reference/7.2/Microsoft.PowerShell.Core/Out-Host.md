---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 4fefb133416b3db6c19c71a916d73fe00f86f3a4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596833"
---
# <span data-ttu-id="84280-102">Out-Host</span><span class="sxs-lookup"><span data-stu-id="84280-102">Out-Host</span></span>

## <span data-ttu-id="84280-103">摘要</span><span class="sxs-lookup"><span data-stu-id="84280-103">SYNOPSIS</span></span>
<span data-ttu-id="84280-104">将输出发送到命令行。</span><span class="sxs-lookup"><span data-stu-id="84280-104">Sends output to the command line.</span></span>

## <span data-ttu-id="84280-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84280-105">SYNTAX</span></span>

### <span data-ttu-id="84280-106">全部</span><span class="sxs-lookup"><span data-stu-id="84280-106">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="84280-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="84280-107">DESCRIPTION</span></span>

<span data-ttu-id="84280-108">`Out-Host`Cmdlet 将输出发送到 PowerShell 主机以供显示。</span><span class="sxs-lookup"><span data-stu-id="84280-108">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="84280-109">该主机在命令行上显示输出。</span><span class="sxs-lookup"><span data-stu-id="84280-109">The host displays the output at the command line.</span></span> <span data-ttu-id="84280-110">由于 `Out-Host` 是默认值，因此除非你想要使用其参数，否则无需指定它。</span><span class="sxs-lookup"><span data-stu-id="84280-110">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="84280-111">`Out-Host` 将自动追加到每个执行的命令。</span><span class="sxs-lookup"><span data-stu-id="84280-111">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="84280-112">它将管道的输出传递给执行命令的主机。</span><span class="sxs-lookup"><span data-stu-id="84280-112">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="84280-113">`Out-Host` 忽略 ANSI 转义序列。</span><span class="sxs-lookup"><span data-stu-id="84280-113">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="84280-114">转义序列由主机处理。</span><span class="sxs-lookup"><span data-stu-id="84280-114">The escape sequences are handled by the host.</span></span> <span data-ttu-id="84280-115">`Out-Host` 将 ANSI 转义序列传递到主机，而不尝试解释或更改它们。</span><span class="sxs-lookup"><span data-stu-id="84280-115">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="84280-116">示例</span><span class="sxs-lookup"><span data-stu-id="84280-116">EXAMPLES</span></span>

### <span data-ttu-id="84280-117">示例1：每次显示一页输出</span><span class="sxs-lookup"><span data-stu-id="84280-117">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="84280-118">此示例显示系统每次处理一页。</span><span class="sxs-lookup"><span data-stu-id="84280-118">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="84280-119">`Get-Process` 获取系统进程，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="84280-119">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="84280-120">`Out-Host` 使用 **分页** 参数一次显示一页数据。</span><span class="sxs-lookup"><span data-stu-id="84280-120">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="84280-121">示例2：使用变量作为输入</span><span class="sxs-lookup"><span data-stu-id="84280-121">Example 2: Use a variable as input</span></span>

<span data-ttu-id="84280-122">此示例使用变量中存储的对象作为的输入 `Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="84280-122">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="84280-123">`Get-History` 获取 PowerShell 会话的历史记录，并将对象存储在 `$io` 变量中。</span><span class="sxs-lookup"><span data-stu-id="84280-123">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="84280-124">`Out-Host` 使用 **InputObject** 参数指定 `$io` 变量并显示历史记录。</span><span class="sxs-lookup"><span data-stu-id="84280-124">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="84280-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84280-125">PARAMETERS</span></span>

### <span data-ttu-id="84280-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="84280-126">-InputObject</span></span>

<span data-ttu-id="84280-127">指定要写入控制台的对象。</span><span class="sxs-lookup"><span data-stu-id="84280-127">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="84280-128">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="84280-128">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="84280-129">-Paging</span><span class="sxs-lookup"><span data-stu-id="84280-129">-Paging</span></span>

<span data-ttu-id="84280-130">指示 `Out-Host` 每次显示一个输出页，并等待用户输入，然后显示剩余页面。</span><span class="sxs-lookup"><span data-stu-id="84280-130">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="84280-131">默认情况下，所有输出都显示在单个页面上。</span><span class="sxs-lookup"><span data-stu-id="84280-131">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="84280-132">页大小由主机的特征确定。</span><span class="sxs-lookup"><span data-stu-id="84280-132">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="84280-133">按 <kbd>空格键</kbd> 显示下一页输出，或按 <kbd>enter</kbd> 键查看下一个输出行。</span><span class="sxs-lookup"><span data-stu-id="84280-133">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="84280-134">按 <kbd>Q</kbd> 退出。</span><span class="sxs-lookup"><span data-stu-id="84280-134">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="84280-135">**分页** 类似于 " **更多** " 命令。</span><span class="sxs-lookup"><span data-stu-id="84280-135">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="84280-136">PowerShell ISE 主机不支持 **分页** 参数。</span><span class="sxs-lookup"><span data-stu-id="84280-136">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="84280-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84280-137">CommonParameters</span></span>

<span data-ttu-id="84280-138">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="84280-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84280-139">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="84280-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84280-140">输入</span><span class="sxs-lookup"><span data-stu-id="84280-140">INPUTS</span></span>

### <span data-ttu-id="84280-141">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="84280-141">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="84280-142">可以将对象向下发送到 `Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="84280-142">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="84280-143">输出</span><span class="sxs-lookup"><span data-stu-id="84280-143">OUTPUTS</span></span>

### <span data-ttu-id="84280-144">无</span><span class="sxs-lookup"><span data-stu-id="84280-144">None</span></span>

<span data-ttu-id="84280-145">`Out-Host` 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="84280-145">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="84280-146">它将对象发送到主机以便显示。</span><span class="sxs-lookup"><span data-stu-id="84280-146">It sends objects to the host for display.</span></span>

## <span data-ttu-id="84280-147">注释</span><span class="sxs-lookup"><span data-stu-id="84280-147">NOTES</span></span>

<span data-ttu-id="84280-148">所有 PowerShell 主机均不支持 **分页** 参数。</span><span class="sxs-lookup"><span data-stu-id="84280-148">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="84280-149">例如，如果在 PowerShell ISE 中使用 **寻呼** 参数，则会显示以下错误： `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="84280-149">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="84280-150">包含 **Out** 谓词的 cmdlet `Out-` 不设置对象的格式。</span><span class="sxs-lookup"><span data-stu-id="84280-150">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="84280-151">它们呈现对象并将其发送到指定的显示目标。</span><span class="sxs-lookup"><span data-stu-id="84280-151">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="84280-152">如果将无格式对象发送到 `Out-` cmdlet，则该 cmdlet 会在呈现该对象之前将其发送到格式设置 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84280-152">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="84280-153">`Out-`Cmdlet 没有用于名称或文件路径的参数。</span><span class="sxs-lookup"><span data-stu-id="84280-153">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="84280-154">若要将数据发送到 `Out-` cmdlet，请使用管道将 PowerShell 命令的输出发送到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84280-154">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="84280-155">或者，可以将数据存储在变量中，并使用 **InputObject** 参数将数据传递给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84280-155">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="84280-156">`Out-Host` 发送数据，但不生成任何输出对象。</span><span class="sxs-lookup"><span data-stu-id="84280-156">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="84280-157">如果将的输出通过管道 `Out-Host` 进行管道 `Get-Member` ，则会 `Get-Member` 报告未指定任何对象。</span><span class="sxs-lookup"><span data-stu-id="84280-157">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="84280-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="84280-158">RELATED LINKS</span></span>

[<span data-ttu-id="84280-159">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="84280-159">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="84280-160">Out-Default</span><span class="sxs-lookup"><span data-stu-id="84280-160">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="84280-161">Out-File</span><span class="sxs-lookup"><span data-stu-id="84280-161">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="84280-162">Out-Null</span><span class="sxs-lookup"><span data-stu-id="84280-162">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="84280-163">Out-printer</span><span class="sxs-lookup"><span data-stu-id="84280-163">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="84280-164">Out-String</span><span class="sxs-lookup"><span data-stu-id="84280-164">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="84280-165">Write-Host</span><span class="sxs-lookup"><span data-stu-id="84280-165">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

