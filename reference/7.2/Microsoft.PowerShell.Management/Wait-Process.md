---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: c469a4e9cf17b03a33bc8b9ff9b06aa95773fc02
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603393"
---
# <span data-ttu-id="06c89-102">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-102">Wait-Process</span></span>

## <span data-ttu-id="06c89-103">摘要</span><span class="sxs-lookup"><span data-stu-id="06c89-103">SYNOPSIS</span></span>
<span data-ttu-id="06c89-104">等到进程停止后再接受更多输入。</span><span class="sxs-lookup"><span data-stu-id="06c89-104">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="06c89-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06c89-105">SYNTAX</span></span>

### <span data-ttu-id="06c89-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="06c89-106">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="06c89-107">ID</span><span class="sxs-lookup"><span data-stu-id="06c89-107">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="06c89-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="06c89-108">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="06c89-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="06c89-109">DESCRIPTION</span></span>

<span data-ttu-id="06c89-110">**Wait-Process** cmdlet 等到一个或多个运行的进程停止后再接受输入。</span><span class="sxs-lookup"><span data-stu-id="06c89-110">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="06c89-111">在 PowerShell 控制台中，此 cmdlet 禁止显示命令提示符，直到进程停止。</span><span class="sxs-lookup"><span data-stu-id="06c89-111">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="06c89-112">可以通过进程名称或进程 ID (PID) 来指定进程，也可以通过管道将进程对象传递给 **Wait-Process**。</span><span class="sxs-lookup"><span data-stu-id="06c89-112">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process**.</span></span>

<span data-ttu-id="06c89-113">**Wait-Process** 仅对在本地计算机上运行的进程有效。</span><span class="sxs-lookup"><span data-stu-id="06c89-113">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="06c89-114">示例</span><span class="sxs-lookup"><span data-stu-id="06c89-114">EXAMPLES</span></span>

### <span data-ttu-id="06c89-115">示例 1：停止进程并等待</span><span class="sxs-lookup"><span data-stu-id="06c89-115">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="06c89-116">此示例停止 Notepad 进程，然后等到该进程停止后，再继续下一个命令。</span><span class="sxs-lookup"><span data-stu-id="06c89-116">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="06c89-117">第一个命令使用 **Get-Process** cmdlet 获取 Notepad 进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="06c89-117">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="06c89-118">它将 ID 存储在 $nid 变量中。</span><span class="sxs-lookup"><span data-stu-id="06c89-118">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="06c89-119">第二个命令使用 Stop-Process cmdlet 停止具有存储在 $nid 中的 ID 的进程。</span><span class="sxs-lookup"><span data-stu-id="06c89-119">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="06c89-120">第三个命令使用 **Wait-Process** 等待 Notepad 进程停止。</span><span class="sxs-lookup"><span data-stu-id="06c89-120">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="06c89-121">它使用 **Wait-Process** 的 ID 参数标识该进程。</span><span class="sxs-lookup"><span data-stu-id="06c89-121">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="06c89-122">示例 2：指定进程</span><span class="sxs-lookup"><span data-stu-id="06c89-122">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="06c89-123">这些命令演示了为 **Wait-Process** 指定进程的三种不同方法。</span><span class="sxs-lookup"><span data-stu-id="06c89-123">These commands show three different methods of specifying a process to **Wait-Process**.</span></span>
<span data-ttu-id="06c89-124">第一个命令获取 Notepad 进程并将它存储在 $p 变量中。</span><span class="sxs-lookup"><span data-stu-id="06c89-124">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="06c89-125">第二个命令使用 Id 参数，第三个命令使用 Name 参数，第四个命令使用 InputObject 参数。</span><span class="sxs-lookup"><span data-stu-id="06c89-125">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="06c89-126">这些命令的结果相同，因此可以互换。</span><span class="sxs-lookup"><span data-stu-id="06c89-126">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="06c89-127">示例 3：在指定时间内等待进程</span><span class="sxs-lookup"><span data-stu-id="06c89-127">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="06c89-128">此命令用 30 秒的时间等待 Outlook 和 Winword 进程停止。</span><span class="sxs-lookup"><span data-stu-id="06c89-128">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="06c89-129">如果这两个进程均未停止，则该 cmdlet 会显示非终止错误以及命令提示符。</span><span class="sxs-lookup"><span data-stu-id="06c89-129">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="06c89-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06c89-130">PARAMETERS</span></span>

### <span data-ttu-id="06c89-131">-Id</span><span class="sxs-lookup"><span data-stu-id="06c89-131">-Id</span></span>

<span data-ttu-id="06c89-132">指定进程的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="06c89-132">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="06c89-133">若要指定多个 ID，请使用逗号分隔 ID。</span><span class="sxs-lookup"><span data-stu-id="06c89-133">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="06c89-134">若要查找进程的 PID，请键入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="06c89-134">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="06c89-135">-InputObject</span><span class="sxs-lookup"><span data-stu-id="06c89-135">-InputObject</span></span>

<span data-ttu-id="06c89-136">通过提交进程对象来指定进程。</span><span class="sxs-lookup"><span data-stu-id="06c89-136">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="06c89-137">输入包含进程对象的变量，或键入获取进程对象的命令或表达式（如 Get-Process cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="06c89-137">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="06c89-138">-Name</span><span class="sxs-lookup"><span data-stu-id="06c89-138">-Name</span></span>

<span data-ttu-id="06c89-139">指定进程的进程名称。</span><span class="sxs-lookup"><span data-stu-id="06c89-139">Specifies the process names of the processes.</span></span>
<span data-ttu-id="06c89-140">若要指定多个名称，请使用逗号分隔这些名称。</span><span class="sxs-lookup"><span data-stu-id="06c89-140">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="06c89-141">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="06c89-141">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="06c89-142">-Timeout</span><span class="sxs-lookup"><span data-stu-id="06c89-142">-Timeout</span></span>

<span data-ttu-id="06c89-143">指定此 cmdlet 等待指定进程停止的最长时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="06c89-143">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="06c89-144">当此时间间隔到期时，该命令会显示一个非终止错误（列出仍在运行的进程）并结束等待。</span><span class="sxs-lookup"><span data-stu-id="06c89-144">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="06c89-145">默认情况下没有任何超时。</span><span class="sxs-lookup"><span data-stu-id="06c89-145">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="06c89-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06c89-146">CommonParameters</span></span>

<span data-ttu-id="06c89-147">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="06c89-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06c89-148">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="06c89-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06c89-149">输入</span><span class="sxs-lookup"><span data-stu-id="06c89-149">INPUTS</span></span>

### <span data-ttu-id="06c89-150">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="06c89-150">System.Diagnostics.Process</span></span>

<span data-ttu-id="06c89-151">可以将进程对象通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06c89-151">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="06c89-152">输出</span><span class="sxs-lookup"><span data-stu-id="06c89-152">OUTPUTS</span></span>

### <span data-ttu-id="06c89-153">无</span><span class="sxs-lookup"><span data-stu-id="06c89-153">None</span></span>

<span data-ttu-id="06c89-154">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="06c89-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="06c89-155">注释</span><span class="sxs-lookup"><span data-stu-id="06c89-155">NOTES</span></span>

<span data-ttu-id="06c89-156">只有 Windows 平台支持 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="06c89-156">The cmdlet is only supported on Windows platforms.</span></span>

<span data-ttu-id="06c89-157">此 cmdlet 使用 WaitForExit 类的方法 **。**</span><span class="sxs-lookup"><span data-stu-id="06c89-157">This cmdlet uses the **WaitForExit** method of the **System.Diagnostics.Process** class.</span></span>

## <span data-ttu-id="06c89-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="06c89-158">RELATED LINKS</span></span>

[<span data-ttu-id="06c89-159">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-159">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="06c89-160">Get-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-160">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="06c89-161">Start-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-161">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="06c89-162">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-162">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="06c89-163">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="06c89-163">Wait-Process</span></span>](Wait-Process.md)
