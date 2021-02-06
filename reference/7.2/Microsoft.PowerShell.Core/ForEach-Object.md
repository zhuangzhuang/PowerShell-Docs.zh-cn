---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 8a79dcf9c2af7aed0c52c361467cab23f880a893
ms.sourcegitcommit: fb9bafd041e3615b9dc9fb77c9245581b705cd02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "99603589"
---
# <span data-ttu-id="fc66b-102">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-102">ForEach-Object</span></span>

## <span data-ttu-id="fc66b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fc66b-103">Synopsis</span></span>
<span data-ttu-id="fc66b-104">针对输入对象集合中的每个项执行操作。</span><span class="sxs-lookup"><span data-stu-id="fc66b-104">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="fc66b-105">语法</span><span class="sxs-lookup"><span data-stu-id="fc66b-105">Syntax</span></span>

### <span data-ttu-id="fc66b-106">ScriptBlockSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="fc66b-106">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fc66b-107">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="fc66b-107">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fc66b-108">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="fc66b-108">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fc66b-109">说明</span><span class="sxs-lookup"><span data-stu-id="fc66b-109">Description</span></span>

<span data-ttu-id="fc66b-110">`ForEach-Object`Cmdlet 对输入对象集合中的每个项执行操作。</span><span class="sxs-lookup"><span data-stu-id="fc66b-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="fc66b-111">可以通过管道将输入对象传递给 cmdlet，或使用 **InputObject** 参数指定。</span><span class="sxs-lookup"><span data-stu-id="fc66b-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="fc66b-112">从 Windows PowerShell 3.0 开始，可以使用两种不同的方法来构造 `ForEach-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="fc66b-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="fc66b-113">**脚本块**。</span><span class="sxs-lookup"><span data-stu-id="fc66b-113">**Script block**.</span></span> <span data-ttu-id="fc66b-114">你可以使用某个脚本块来指定操作。</span><span class="sxs-lookup"><span data-stu-id="fc66b-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="fc66b-115">在脚本块中，使用 `$_` 变量来表示当前对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="fc66b-116">脚本块是 **Process** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="fc66b-117">脚本块可以包含任何 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="fc66b-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="fc66b-118">例如，以下命令将获取计算机上每个进程的 **ProcessName** 属性值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="fc66b-119">`ForEach-Object` 支持 `begin` 、 `process` 和块， `end` 如 [about_functions](about/about_functions.md#piping-objects-to-functions)中所述。</span><span class="sxs-lookup"><span data-stu-id="fc66b-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="fc66b-120">脚本块在调用方的作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="fc66b-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="fc66b-121">因此，这些块有权访问该范围内的变量，并且可以创建在 cmdlet 完成后在该范围内持久保留的新变量。</span><span class="sxs-lookup"><span data-stu-id="fc66b-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="fc66b-122">**操作语句**。</span><span class="sxs-lookup"><span data-stu-id="fc66b-122">**Operation statement**.</span></span> <span data-ttu-id="fc66b-123">你还可以编写操作语句，它更像自然语言。</span><span class="sxs-lookup"><span data-stu-id="fc66b-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="fc66b-124">你可以使用该操作语句来指定属性值或调用方法。</span><span class="sxs-lookup"><span data-stu-id="fc66b-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="fc66b-125">Windows PowerShell 3.0 中引入了操作语句。</span><span class="sxs-lookup"><span data-stu-id="fc66b-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="fc66b-126">例如，以下命令还将获取计算机上每个进程的 **ProcessName** 属性值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="fc66b-127">**并行运行的脚本块**。</span><span class="sxs-lookup"><span data-stu-id="fc66b-127">**Parallel running script block**.</span></span> <span data-ttu-id="fc66b-128">从 PowerShell 7.0 开始，第三个参数集可用于并行运行每个脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-128">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="fc66b-129">**ThrottleLimit** 参数限制一次运行的并行脚本的数量。</span><span class="sxs-lookup"><span data-stu-id="fc66b-129">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="fc66b-130">与前面一样，使用 `$_` 变量表示脚本块中的当前输入对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-130">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="fc66b-131">使用 `$using:` 关键字可将变量引用传递给正在运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="fc66b-131">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="fc66b-132">在 PowerShell 7 中，为每个循环迭代创建新的运行空间，以确保最大程度的隔离。</span><span class="sxs-lookup"><span data-stu-id="fc66b-132">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="fc66b-133">如果要执行的工作比创建新的运行空间少，或者有大量迭代执行重要的工作，则这可能会造成较大的性能和资源的损失。</span><span class="sxs-lookup"><span data-stu-id="fc66b-133">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="fc66b-134">从 PowerShell 7.1 开始，默认情况下会重复使用运行空间池中的运行空间。</span><span class="sxs-lookup"><span data-stu-id="fc66b-134">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="fc66b-135">运行空间池大小由 **ThrottleLimit** 参数指定。</span><span class="sxs-lookup"><span data-stu-id="fc66b-135">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="fc66b-136">默认的运行空间池大小为5。</span><span class="sxs-lookup"><span data-stu-id="fc66b-136">The default runspace pool size is 5.</span></span> <span data-ttu-id="fc66b-137">你仍可以使用 **UseNewRunspace** 开关为每个迭代创建新的运行空间。</span><span class="sxs-lookup"><span data-stu-id="fc66b-137">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="fc66b-138">默认情况下，并行 scriptblocks 使用启动并行任务的调用方的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="fc66b-138">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="fc66b-139">如果在并行运行的 scriptblocks 中发生了非终止错误，则会将这些错误写入到 cmdlet 错误流中。</span><span class="sxs-lookup"><span data-stu-id="fc66b-139">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="fc66b-140">由于无法确定并行 scriptblock 执行顺序，错误流中出现错误的顺序是随机的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-140">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="fc66b-141">同样，写入其他数据流的消息（如警告、详细或信息）将按不确定的顺序写入这些数据流。</span><span class="sxs-lookup"><span data-stu-id="fc66b-141">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="fc66b-142">终止错误（如异常）将终止发生 scriptblocks 的单个并行实例。</span><span class="sxs-lookup"><span data-stu-id="fc66b-142">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="fc66b-143">一个 scriptblocks 中的终止错误不会导致 `Foreach-Object` cmdlet 终止。</span><span class="sxs-lookup"><span data-stu-id="fc66b-143">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="fc66b-144">同时运行的其他 scriptblocks 将继续运行，除非它们也遇到终止错误。</span><span class="sxs-lookup"><span data-stu-id="fc66b-144">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="fc66b-145">终止错误将作为 **ErrorRecord** ，以 **FullyQualifiedErrorId** 的形式写入错误数据流 `PSTaskException` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-145">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="fc66b-146">使用 PowerShell try/catch 块或 catch 块可将终止错误转换为非终止错误。</span><span class="sxs-lookup"><span data-stu-id="fc66b-146">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="fc66b-147">示例</span><span class="sxs-lookup"><span data-stu-id="fc66b-147">Examples</span></span>

### <span data-ttu-id="fc66b-148">示例1：分割数组中的整数</span><span class="sxs-lookup"><span data-stu-id="fc66b-148">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="fc66b-149">此示例使用一个包含三个整数的数组，并将每个整数除以1024。</span><span class="sxs-lookup"><span data-stu-id="fc66b-149">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="fc66b-150">示例2：获取目录中所有文件的长度</span><span class="sxs-lookup"><span data-stu-id="fc66b-150">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="fc66b-151">此示例处理 PowerShell 安装目录中的文件和目录 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-151">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="fc66b-152">如果该对象不是一个目录，则脚本块将获取该文件的名称，将其 **Length** 属性的值除以1024，并添加一个空格 ( "" ) 以便将它与下一项隔开。</span><span class="sxs-lookup"><span data-stu-id="fc66b-152">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="fc66b-153">Cmdlet 使用 **PSISContainer** 属性来确定对象是否为目录。</span><span class="sxs-lookup"><span data-stu-id="fc66b-153">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="fc66b-154">示例3：对最新系统事件进行操作</span><span class="sxs-lookup"><span data-stu-id="fc66b-154">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="fc66b-155">此示例将系统事件日志中的最新事件1000写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="fc66b-155">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="fc66b-156">当前时间在处理事件之前和之后显示。</span><span class="sxs-lookup"><span data-stu-id="fc66b-156">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="fc66b-157">`Get-EventLog` 获取系统事件日志中的最新事件1000，并将其存储在 `$Events` 变量中。</span><span class="sxs-lookup"><span data-stu-id="fc66b-157">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="fc66b-158">`$Events` 然后，将管道传递给 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fc66b-158">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="fc66b-159">**Begin** 参数将显示当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fc66b-159">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="fc66b-160">接下来， **Process** 参数使用 `Out-File` cmdlet 创建一个名为 events.txt 的文本文件，并将每个事件的消息属性存储在该文件中。</span><span class="sxs-lookup"><span data-stu-id="fc66b-160">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="fc66b-161">最后，在完成所有处理之后，使用 **End** 参数显示日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fc66b-161">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="fc66b-162">示例4：更改注册表项的值</span><span class="sxs-lookup"><span data-stu-id="fc66b-162">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="fc66b-163">此示例将 "密钥" 下的所有子项中的 **RemotePath** 注册表项的值更改 `HKCU:\Network` 为大写文本。</span><span class="sxs-lookup"><span data-stu-id="fc66b-163">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="fc66b-164">可以使用此格式更改注册表条目值的形式或内容。</span><span class="sxs-lookup"><span data-stu-id="fc66b-164">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="fc66b-165">**网络** 密钥中的每个子项表示在登录时重新连接的映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="fc66b-165">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="fc66b-166">**RemotePath** 项包含连接的驱动器的 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="fc66b-166">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="fc66b-167">例如，如果将 E：驱动器映射到 `\\Server\Share` ，则会在中创建一个 **e** 子项， `HKCU:\Network` 并将 **RemotePath** 注册表值设置为 `\\Server\Share` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-167">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="fc66b-168">该命令使用 `Get-ItemProperty` cmdlet 来获取 **网络** 密钥的所有子项，并使用 `Set-ItemProperty` cmdlet 来更改每个密钥中的 **RemotePath** 注册表项的值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-168">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="fc66b-169">在 `Set-ItemProperty` 命令中，路径是注册表项的 **PSPath** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-169">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="fc66b-170">这是表示注册表项的 Microsoft .NET Framework 对象的属性，而不是注册表项。</span><span class="sxs-lookup"><span data-stu-id="fc66b-170">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="fc66b-171">该命令使用 **RemotePath** 值的 **ToUpper ( # B1** 方法，这是 REG_SZ)  (字符串。</span><span class="sxs-lookup"><span data-stu-id="fc66b-171">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="fc66b-172">由于 `Set-ItemProperty` 正在更改每个键的属性，因此 `ForEach-Object` 需要使用 cmdlet 来访问属性。</span><span class="sxs-lookup"><span data-stu-id="fc66b-172">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="fc66b-173">示例5：使用 $Null 自动变量</span><span class="sxs-lookup"><span data-stu-id="fc66b-173">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="fc66b-174">此示例演示如何通过管道将 `$Null` 自动变量传递给 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fc66b-174">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="fc66b-175">因为 PowerShell 将 null 视为显式占位符，所以该 `ForEach-Object` cmdlet 会生成一个值 `$Null` ，就像对管道传递给它的其他对象一样。</span><span class="sxs-lookup"><span data-stu-id="fc66b-175">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="fc66b-176">示例6：获取属性值</span><span class="sxs-lookup"><span data-stu-id="fc66b-176">Example 6: Get property values</span></span>

<span data-ttu-id="fc66b-177">此示例通过使用 cmdlet 的 **成员名称** 参数获取所有已安装的 PowerShell 模块的 **Path** 属性的值 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-177">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="fc66b-178">第二个命令等效于第一个命令。</span><span class="sxs-lookup"><span data-stu-id="fc66b-178">The second command is equivalent to the first.</span></span> <span data-ttu-id="fc66b-179">它使用 `Foreach` cmdlet 的别名， `ForEach-Object` 并忽略 **成员** 名称参数的名称，此参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-179">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="fc66b-180">此 `ForEach-Object` cmdlet 对于获取属性值非常有用，因为它在不更改类型的情况下获取值， 而不是更改 `Select-Object` 属性值类型。</span><span class="sxs-lookup"><span data-stu-id="fc66b-180">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="fc66b-181">示例7：将模块名称拆分为组件名称</span><span class="sxs-lookup"><span data-stu-id="fc66b-181">Example 7: Split module names into component names</span></span>

<span data-ttu-id="fc66b-182">此示例显示了将两个以句点分隔的模块名称拆分为其组件名称的三种方法。</span><span class="sxs-lookup"><span data-stu-id="fc66b-182">This example shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="fc66b-183">这些命令调用字符串的 **Split** 方法。</span><span class="sxs-lookup"><span data-stu-id="fc66b-183">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="fc66b-184">这三个命令使用不同的语法，但它们是等效且可互换的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-184">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="fc66b-185">第一个命令使用传统语法，包括脚本块和当前的对象运算符 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-185">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="fc66b-186">它使用句点语法来指定该方法，并使用括号将分隔符参数括起来。</span><span class="sxs-lookup"><span data-stu-id="fc66b-186">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="fc66b-187">第二个命令使用 **MemberName** 参数来指定 **Split** 方法，并使用 **ArgumentName** 参数将句点 (".") 标识为拆分分隔符。</span><span class="sxs-lookup"><span data-stu-id="fc66b-187">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="fc66b-188">第三个命令使用 cmdlet 的 **Foreach** 别名， `ForEach-Object` 并省略 **成员** 名称和 **ArgumentList** 参数的名称，这些参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-188">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="fc66b-189">示例8：将 ForEach-Object 用于两个脚本块</span><span class="sxs-lookup"><span data-stu-id="fc66b-189">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="fc66b-190">在此示例中，我们传递两个脚本块按位置。</span><span class="sxs-lookup"><span data-stu-id="fc66b-190">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="fc66b-191">所有脚本块都绑定到 **Process** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-191">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="fc66b-192">但是，它们被视为已传递到 **Begin** 和 **Process** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-192">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="fc66b-193">示例9：使用包含两个以上脚本块的 ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-193">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="fc66b-194">在此示例中，我们传递两个脚本块按位置。</span><span class="sxs-lookup"><span data-stu-id="fc66b-194">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="fc66b-195">所有脚本块都绑定到 **Process** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-195">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="fc66b-196">但是，它们被视为已传递到 **Begin**、 **Process** 和 **End** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-196">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="fc66b-197">第一个脚本块始终映射到 `begin` 块，最后一个块映射到 `end` 块，中间的块全部映射到 `process` 块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-197">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="fc66b-198">示例10：运行每个管道项的多个脚本块</span><span class="sxs-lookup"><span data-stu-id="fc66b-198">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="fc66b-199">如前面的示例所示，使用 **Process** 参数传递的多个脚本块将映射到 **Begin** 和 **End** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-199">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="fc66b-200">若要避免此映射，必须为 **Begin** 和 **End** 参数提供显式值。</span><span class="sxs-lookup"><span data-stu-id="fc66b-200">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### <span data-ttu-id="fc66b-201">示例11：并行运行缓慢脚本</span><span class="sxs-lookup"><span data-stu-id="fc66b-201">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="fc66b-202">此示例运行一个简单的脚本块，该脚本块可计算字符串并休眠一秒钟。</span><span class="sxs-lookup"><span data-stu-id="fc66b-202">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="fc66b-203">**ThrottleLimit** 参数值设置为4，以便按四个批处理对输入进行处理。</span><span class="sxs-lookup"><span data-stu-id="fc66b-203">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="fc66b-204">`$using:`关键字用于将 `$Message` 变量传递到每个并行脚本块中。</span><span class="sxs-lookup"><span data-stu-id="fc66b-204">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="fc66b-205">示例12：并行检索日志条目</span><span class="sxs-lookup"><span data-stu-id="fc66b-205">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="fc66b-206">此示例从本地 Windows 计算机上的5个系统日志中检索50000日志条目。</span><span class="sxs-lookup"><span data-stu-id="fc66b-206">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="fc66b-207">Parallel 参数指定为每个输入日志名称并行运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-207">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="fc66b-208">**ThrottleLimit** 参数可确保同时运行所有五个脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-208">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="fc66b-209">示例13：作为作业并行运行</span><span class="sxs-lookup"><span data-stu-id="fc66b-209">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="fc66b-210">此示例将并行运行简单的脚本块，同时创建两个后台作业。</span><span class="sxs-lookup"><span data-stu-id="fc66b-210">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="fc66b-211">`$job`变量接收收集输出数据并监视正在运行状态的作业对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-211">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="fc66b-212">作业对象 `Receive-Job` 与 **Wait** 开关参数一起传递给。</span><span class="sxs-lookup"><span data-stu-id="fc66b-212">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="fc66b-213">这会流输出到控制台，就好像是在 `ForEach-Object -Parallel` 没有 **AsJob** 的情况下运行一样。</span><span class="sxs-lookup"><span data-stu-id="fc66b-213">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="fc66b-214">示例14：使用线程安全变量引用</span><span class="sxs-lookup"><span data-stu-id="fc66b-214">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="fc66b-215">此示例将并行调用脚本块以收集唯一命名的进程对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-215">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="fc66b-216">**ConcurrentDictionary** 对象的单个实例会传递给每个脚本块，以收集对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-216">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="fc66b-217">由于 **ConcurrentDictionary** 是线程安全的，因此可以安全地通过每个并行脚本进行修改。</span><span class="sxs-lookup"><span data-stu-id="fc66b-217">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="fc66b-218">在此处使用非线程安全的对象（如 **system.object**）将是不安全的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-218">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="fc66b-219">此示例非常低效地使用了 **并行** 参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-219">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="fc66b-220">此脚本只是将输入对象添加到并发字典对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-220">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="fc66b-221">这种方法很简单，不值得在单独的线程中调用每个脚本的系统开销。</span><span class="sxs-lookup"><span data-stu-id="fc66b-221">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="fc66b-222">`ForEach-Object`在没有 **并行** 交换机的情况下正常运行更高效、更快。</span><span class="sxs-lookup"><span data-stu-id="fc66b-222">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="fc66b-223">此示例仅用于演示如何使用线程安全变量。</span><span class="sxs-lookup"><span data-stu-id="fc66b-223">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="fc66b-224">示例15：编写并行执行的错误</span><span class="sxs-lookup"><span data-stu-id="fc66b-224">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="fc66b-225">此示例将并行写入错误流，其中写入错误的顺序是随机的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-225">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="fc66b-226">示例16：在并行执行中终止错误</span><span class="sxs-lookup"><span data-stu-id="fc66b-226">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="fc66b-227">此示例演示一个并行运行的 scriptblock 中的终止错误。</span><span class="sxs-lookup"><span data-stu-id="fc66b-227">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="fc66b-228">`Output: 3` 永远不会编写，因为该迭代的并行 scriptblock 已终止。</span><span class="sxs-lookup"><span data-stu-id="fc66b-228">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

## <span data-ttu-id="fc66b-229">参数</span><span class="sxs-lookup"><span data-stu-id="fc66b-229">Parameters</span></span>

### <span data-ttu-id="fc66b-230">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="fc66b-230">-ArgumentList</span></span>

<span data-ttu-id="fc66b-231">指定方法调用的参数数组。</span><span class="sxs-lookup"><span data-stu-id="fc66b-231">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="fc66b-232">有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-232">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="fc66b-233">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-234">-Begin</span><span class="sxs-lookup"><span data-stu-id="fc66b-234">-Begin</span></span>

<span data-ttu-id="fc66b-235">指定在此 cmdlet 处理任何输入对象之前运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-235">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="fc66b-236">此脚本块仅对整个管道运行一次。</span><span class="sxs-lookup"><span data-stu-id="fc66b-236">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="fc66b-237">有关块的详细信息 `begin` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-237">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-238">-End</span><span class="sxs-lookup"><span data-stu-id="fc66b-238">-End</span></span>

<span data-ttu-id="fc66b-239">指定在此 cmdlet 处理所有输入对象之后运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-239">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="fc66b-240">此脚本块仅对整个管道运行一次。</span><span class="sxs-lookup"><span data-stu-id="fc66b-240">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="fc66b-241">有关块的详细信息 `end` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-241">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-242">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fc66b-242">-InputObject</span></span>

<span data-ttu-id="fc66b-243">指定输入对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-243">Specifies the input objects.</span></span> <span data-ttu-id="fc66b-244">`ForEach-Object` 在每个输入对象上运行脚本块或操作语句。</span><span class="sxs-lookup"><span data-stu-id="fc66b-244">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="fc66b-245">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="fc66b-245">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="fc66b-246">当你将 **inputobject** 参数与一起使用时 `ForEach-Object` ， `ForEach-Object` **inputobject** 值将被视为单个对象，而不是管道将命令结果传递给。</span><span class="sxs-lookup"><span data-stu-id="fc66b-246">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="fc66b-247">即使该值是作为命令结果的集合（如），也是如此 `-InputObject (Get-Process)` 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-247">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="fc66b-248">由于 **InputObject** 无法从数组或对象的集合返回各个属性，因此，如果您使用在 `ForEach-Object` 已定义的属性中具有特定值的那些对象的对象集合上执行操作，则建议您 `ForEach-Object` 在管道中使用，如本主题的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="fc66b-248">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="fc66b-249">-MemberName</span><span class="sxs-lookup"><span data-stu-id="fc66b-249">-MemberName</span></span>

<span data-ttu-id="fc66b-250">指定要获取的属性或要调用的方法。</span><span class="sxs-lookup"><span data-stu-id="fc66b-250">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="fc66b-251">允许使用通配符，但仅在生成的字符串解析为唯一值时才有效。</span><span class="sxs-lookup"><span data-stu-id="fc66b-251">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="fc66b-252">例如，如果运行 `Get-Process | ForEach -MemberName *Name` ，通配符模式将匹配多个成员，导致命令失败。</span><span class="sxs-lookup"><span data-stu-id="fc66b-252">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="fc66b-253">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fc66b-254">-Process</span><span class="sxs-lookup"><span data-stu-id="fc66b-254">-Process</span></span>

<span data-ttu-id="fc66b-255">指定对每个输入对象所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fc66b-255">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="fc66b-256">为管道中的每个对象运行此脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-256">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="fc66b-257">有关块的详细信息 `process` ，请参阅 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-257">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="fc66b-258">向 **Process** 参数提供多个脚本块时，第一个脚本块将始终映射到 `begin` 块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-258">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="fc66b-259">如果只有两个脚本块，则第二个块映射到 `process` 块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-259">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="fc66b-260">如果有三个或更多脚本块，则第一个脚本块始终映射到 `begin` 块，最后一个块映射到块 `end` ，而介于之间的块全部映射到 `process` 块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-260">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-261">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="fc66b-261">-RemainingScripts</span></span>

<span data-ttu-id="fc66b-262">指定 **进程** 参数不会使用的所有脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-262">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="fc66b-263">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-264">-Parallel</span><span class="sxs-lookup"><span data-stu-id="fc66b-264">-Parallel</span></span>

<span data-ttu-id="fc66b-265">指定要用于对输入对象进行并行处理的脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-265">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="fc66b-266">输入描述该操作的脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-266">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="fc66b-267">此参数是在 PowerShell 7.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-267">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-268">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="fc66b-268">-ThrottleLimit</span></span>

<span data-ttu-id="fc66b-269">指定并行的脚本块的数量。</span><span class="sxs-lookup"><span data-stu-id="fc66b-269">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="fc66b-270">在正在运行的脚本块计数低于 **ThrottleLimit** 之前，输入对象将被阻止。</span><span class="sxs-lookup"><span data-stu-id="fc66b-270">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="fc66b-271">默认值是 `5`。</span><span class="sxs-lookup"><span data-stu-id="fc66b-271">The default value is `5`.</span></span>

<span data-ttu-id="fc66b-272">此参数是在 PowerShell 7.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-272">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-273">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="fc66b-273">-TimeoutSeconds</span></span>

<span data-ttu-id="fc66b-274">指定以并行方式处理所有输入所等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="fc66b-274">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="fc66b-275">在指定的超时时间后，将停止所有正在运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="fc66b-275">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="fc66b-276">以及要处理的其余输入对象将被忽略。</span><span class="sxs-lookup"><span data-stu-id="fc66b-276">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="fc66b-277">默认值为 `0` "禁用超时"， `ForEach-Object -Parallel` 可以无限期运行。</span><span class="sxs-lookup"><span data-stu-id="fc66b-277">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="fc66b-278"><kbd></kbd> + 在命令行中键入 Ctrl<kbd>C</kbd>会停止正在运行的 `ForEach-Object -Parallel` 命令。</span><span class="sxs-lookup"><span data-stu-id="fc66b-278">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="fc66b-279">此参数不能与 **AsJob** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="fc66b-279">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="fc66b-280">此参数是在 PowerShell 7.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-280">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-281">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="fc66b-281">-UseNewRunspace</span></span>

<span data-ttu-id="fc66b-282">导致并行调用为每个循环迭代创建新的运行空间，而不是从运行空间池中重复使用运行空间。</span><span class="sxs-lookup"><span data-stu-id="fc66b-282">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="fc66b-283">PowerShell 7.1 中引入了此参数</span><span class="sxs-lookup"><span data-stu-id="fc66b-283">This parameter was introduced in PowerShell 7.1</span></span>

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-284">-AsJob</span><span class="sxs-lookup"><span data-stu-id="fc66b-284">-AsJob</span></span>

<span data-ttu-id="fc66b-285">导致并行调用作为 PowerShell 作业运行。</span><span class="sxs-lookup"><span data-stu-id="fc66b-285">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="fc66b-286">返回一个作业对象，而不是运行的脚本块的输出。</span><span class="sxs-lookup"><span data-stu-id="fc66b-286">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="fc66b-287">作业对象包含运行的每个并行脚本块的子作业。</span><span class="sxs-lookup"><span data-stu-id="fc66b-287">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="fc66b-288">所有 PowerShell 作业 cmdlet 都可以使用作业对象来监视正在运行的状态和检索数据。</span><span class="sxs-lookup"><span data-stu-id="fc66b-288">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="fc66b-289">此参数是在 PowerShell 7.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fc66b-289">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-290">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fc66b-290">-Confirm</span></span>

<span data-ttu-id="fc66b-291">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="fc66b-291">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-292">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fc66b-292">-WhatIf</span></span>

<span data-ttu-id="fc66b-293">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="fc66b-293">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fc66b-294">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="fc66b-294">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc66b-295">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc66b-295">CommonParameters</span></span>

<span data-ttu-id="fc66b-296">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fc66b-296">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc66b-297">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-297">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc66b-298">输入</span><span class="sxs-lookup"><span data-stu-id="fc66b-298">Inputs</span></span>

### <span data-ttu-id="fc66b-299">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="fc66b-299">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fc66b-300">你可以通过管道将任何对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fc66b-300">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="fc66b-301">输出</span><span class="sxs-lookup"><span data-stu-id="fc66b-301">Outputs</span></span>

### <span data-ttu-id="fc66b-302">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="fc66b-302">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fc66b-303">此 cmdlet 将返回由输入确定的对象。</span><span class="sxs-lookup"><span data-stu-id="fc66b-303">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="fc66b-304">说明</span><span class="sxs-lookup"><span data-stu-id="fc66b-304">Notes</span></span>

- <span data-ttu-id="fc66b-305">此 `ForEach-Object` cmdlet 的工作方式与 **foreach** 语句非常相似，不同之处在于你不能通过管道将输入传递给 **foreach** 语句。</span><span class="sxs-lookup"><span data-stu-id="fc66b-305">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="fc66b-306">有关 **Foreach** 语句的详细信息，请参阅 [about_Foreach](./About/about_Foreach.md)。</span><span class="sxs-lookup"><span data-stu-id="fc66b-306">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="fc66b-307">从 PowerShell 4.0 开始， `Where` `ForEach` 添加了方法以与集合一起使用。</span><span class="sxs-lookup"><span data-stu-id="fc66b-307">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="fc66b-308">可在此处阅读有关这些新方法的详细信息 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="fc66b-308">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="fc66b-309">`ForEach-Object -Parallel`参数集使用 PowerShell 的内部 API 来运行每个脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-309">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="fc66b-310">这比 `ForEach-Object` 以顺序处理正常运行的开销要大得多。</span><span class="sxs-lookup"><span data-stu-id="fc66b-310">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="fc66b-311">与脚本块执行的工作相比 **，并行运行** 的开销很小，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="fc66b-311">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="fc66b-312">例如：</span><span class="sxs-lookup"><span data-stu-id="fc66b-312">For example:</span></span>

  - <span data-ttu-id="fc66b-313">多核计算机上的计算密集型脚本</span><span class="sxs-lookup"><span data-stu-id="fc66b-313">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="fc66b-314">花费时间等待结果或执行文件操作的脚本</span><span class="sxs-lookup"><span data-stu-id="fc66b-314">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="fc66b-315">使用 **Parallel** 参数可能会导致脚本的运行速度慢于正常。</span><span class="sxs-lookup"><span data-stu-id="fc66b-315">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="fc66b-316">尤其是当并行脚本很简单时。</span><span class="sxs-lookup"><span data-stu-id="fc66b-316">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="fc66b-317">进行 **并行** 试验，以发现它的好处。</span><span class="sxs-lookup"><span data-stu-id="fc66b-317">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="fc66b-318">`ForEach-Object -Parallel`参数集在单独的进程线程上并行运行脚本块。</span><span class="sxs-lookup"><span data-stu-id="fc66b-318">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="fc66b-319">`$using:`关键字允许将来自 cmdlet 调用线程的变量引用传递到每个正在运行的脚本块线程。</span><span class="sxs-lookup"><span data-stu-id="fc66b-319">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="fc66b-320">由于脚本块在不同的线程中运行，因此必须安全地使用由引用传递的对象变量。</span><span class="sxs-lookup"><span data-stu-id="fc66b-320">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="fc66b-321">通常，可以安全地从不会更改的引用对象中进行读取。</span><span class="sxs-lookup"><span data-stu-id="fc66b-321">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="fc66b-322">但如果对象状态正在修改，则必须使用线程安全对象， **如 .net system.string** 类型 (参见示例 11) 。</span><span class="sxs-lookup"><span data-stu-id="fc66b-322">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="fc66b-323">相关链接</span><span class="sxs-lookup"><span data-stu-id="fc66b-323">Related links</span></span>

[<span data-ttu-id="fc66b-324">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-324">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="fc66b-325">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-325">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="fc66b-326">Group-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-326">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="fc66b-327">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-327">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="fc66b-328">New-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-328">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="fc66b-329">Select-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-329">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="fc66b-330">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-330">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="fc66b-331">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="fc66b-331">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
