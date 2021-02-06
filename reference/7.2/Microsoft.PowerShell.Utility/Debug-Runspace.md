---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 3f01b7624ffcbca472b09bdb83a7440f3526db43
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596230"
---
# <span data-ttu-id="cb25d-102">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="cb25d-102">Debug-Runspace</span></span>

## <span data-ttu-id="cb25d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cb25d-103">SYNOPSIS</span></span>
<span data-ttu-id="cb25d-104">启动与运行空间的交互式调试会话。</span><span class="sxs-lookup"><span data-stu-id="cb25d-104">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="cb25d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb25d-105">SYNTAX</span></span>

### <span data-ttu-id="cb25d-106">RunspaceParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="cb25d-106">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cb25d-107">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb25d-107">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cb25d-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb25d-108">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cb25d-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="cb25d-109">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cb25d-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb25d-110">DESCRIPTION</span></span>

<span data-ttu-id="cb25d-111">`Debug-Runspace`Cmdlet 可启动与本地或远程活动运行空间之间的交互式调试会话。</span><span class="sxs-lookup"><span data-stu-id="cb25d-111">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="cb25d-112">你可以查找要通过先运行来进行调试的运行空间， `Get-Process` 以查找与 PowerShell 关联的进程，然后 `Enter-PSHostProcess` 使用 **id** 参数中指定的进程 ID 附加到进程，然后 `Get-Runspace` 列出 PowerShell 主机进程内的运行空间。</span><span class="sxs-lookup"><span data-stu-id="cb25d-112">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="cb25d-113">选择要调试的运行空间后，如果运行空间当前正在运行命令或脚本，或者脚本已在断点处停止，则 PowerShell 将为运行空间打开远程调试器会话。</span><span class="sxs-lookup"><span data-stu-id="cb25d-113">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="cb25d-114">可以采用与调试远程会话脚本相同的方式来调试运行空间脚本。</span><span class="sxs-lookup"><span data-stu-id="cb25d-114">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="cb25d-115">如果你是运行进程的计算机上的管理员，或者正在运行要调试的脚本，则只能附加到 PowerShell 主机进程。</span><span class="sxs-lookup"><span data-stu-id="cb25d-115">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="cb25d-116">此外，不能输入运行当前 PowerShell 会话的主机进程。</span><span class="sxs-lookup"><span data-stu-id="cb25d-116">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="cb25d-117">只能输入运行不同 PowerShell 会话的主机进程。</span><span class="sxs-lookup"><span data-stu-id="cb25d-117">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="cb25d-118">示例</span><span class="sxs-lookup"><span data-stu-id="cb25d-118">EXAMPLES</span></span>

### <span data-ttu-id="cb25d-119">示例1：调试远程运行空间</span><span class="sxs-lookup"><span data-stu-id="cb25d-119">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="cb25d-120">在此示例中，调试在远程计算机上打开的运行空间 WS10TestServer。</span><span class="sxs-lookup"><span data-stu-id="cb25d-120">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="cb25d-121">在该命令的第一行中，你在 `Get-Process` 远程计算机上运行，并筛选 Windows PowerShell 主机进程。</span><span class="sxs-lookup"><span data-stu-id="cb25d-121">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="cb25d-122">在此示例中，你想要调试进程 ID 1152，Windows PowerShell ISE 主机进程。</span><span class="sxs-lookup"><span data-stu-id="cb25d-122">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="cb25d-123">在第二个命令中，运行 `Enter-PSSession` 以打开 WS10TestServer 上的远程会话。</span><span class="sxs-lookup"><span data-stu-id="cb25d-123">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="cb25d-124">在第三个命令中，通过运行连接到在远程服务器上运行的 Windows PowerShell ISE 主机进程 `Enter-PSHostProcess` ，并指定在第一个命令1152中获取的主机进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="cb25d-124">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="cb25d-125">在第四个命令中，可以通过运行来列出进程 ID 1152 的可用运行空间 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="cb25d-125">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="cb25d-126">记下繁忙运行空间的 ID 号;它正在运行您要调试的脚本。</span><span class="sxs-lookup"><span data-stu-id="cb25d-126">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="cb25d-127">在最后一个命令中，通过添加 Id 参数，开始调试正在运行脚本的打开的运行空间，TestWFVar1.ps1，通过运行 `Debug-Runspace` ，并按 id 2 标识运行空间。 </span><span class="sxs-lookup"><span data-stu-id="cb25d-127">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="cb25d-128">由于脚本中存在断点，因此将打开调试器。</span><span class="sxs-lookup"><span data-stu-id="cb25d-128">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="cb25d-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cb25d-129">PARAMETERS</span></span>

### <span data-ttu-id="cb25d-130">-Id</span><span class="sxs-lookup"><span data-stu-id="cb25d-130">-Id</span></span>

<span data-ttu-id="cb25d-131">指定运行空间的 ID 号。</span><span class="sxs-lookup"><span data-stu-id="cb25d-131">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="cb25d-132">您可以运行 `Get-Runspace` 来显示运行空间 id。</span><span class="sxs-lookup"><span data-stu-id="cb25d-132">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-133">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="cb25d-133">-InstanceId</span></span>

<span data-ttu-id="cb25d-134">按其实例 ID 指定运行空间，可通过运行显示该 GUID `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="cb25d-134">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-135">-Name</span><span class="sxs-lookup"><span data-stu-id="cb25d-135">-Name</span></span>

<span data-ttu-id="cb25d-136">按名称指定运行空间。</span><span class="sxs-lookup"><span data-stu-id="cb25d-136">Specifies a runspace by its name.</span></span> <span data-ttu-id="cb25d-137">您可以运行 `Get-Runspace` 来显示运行空间的名称。</span><span class="sxs-lookup"><span data-stu-id="cb25d-137">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-138">-运行空间</span><span class="sxs-lookup"><span data-stu-id="cb25d-138">-Runspace</span></span>

<span data-ttu-id="cb25d-139">指定运行空间对象。</span><span class="sxs-lookup"><span data-stu-id="cb25d-139">Specifies a runspace object.</span></span> <span data-ttu-id="cb25d-140">为此参数提供值的最简单方法是指定包含筛选命令的结果的变量 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="cb25d-140">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cb25d-141">-Confirm</span></span>

<span data-ttu-id="cb25d-142">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cb25d-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cb25d-143">-WhatIf</span></span>

<span data-ttu-id="cb25d-144">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cb25d-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cb25d-145">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cb25d-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb25d-146">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="cb25d-146">-BreakAll</span></span>

<span data-ttu-id="cb25d-147">{{填充 BreakAll 说明}}</span><span class="sxs-lookup"><span data-stu-id="cb25d-147">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="cb25d-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb25d-148">CommonParameters</span></span>

<span data-ttu-id="cb25d-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cb25d-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb25d-150">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cb25d-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb25d-151">输入</span><span class="sxs-lookup"><span data-stu-id="cb25d-151">INPUTS</span></span>

### <span data-ttu-id="cb25d-152">System.web. Management。</span><span class="sxs-lookup"><span data-stu-id="cb25d-152">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="cb25d-153">可以通过管道将命令结果传递 `Get-Runspace` 给 **调试-运行空间。**</span><span class="sxs-lookup"><span data-stu-id="cb25d-153">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="cb25d-154">输出</span><span class="sxs-lookup"><span data-stu-id="cb25d-154">OUTPUTS</span></span>

## <span data-ttu-id="cb25d-155">注释</span><span class="sxs-lookup"><span data-stu-id="cb25d-155">NOTES</span></span>

<span data-ttu-id="cb25d-156">`Debug-Runspace` 适用于处于打开状态的运行空间。</span><span class="sxs-lookup"><span data-stu-id="cb25d-156">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="cb25d-157">如果运行空间状态从 "已打开" 更改为其他状态，则将自动从正在运行的列表中删除该运行空间。</span><span class="sxs-lookup"><span data-stu-id="cb25d-157">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="cb25d-158">只有满足以下条件时，才能将运行空间添加到正在运行的列表。</span><span class="sxs-lookup"><span data-stu-id="cb25d-158">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="cb25d-159">如果它来自调用命令，则为;也就是说，它具有 `Invoke-Command` GUID ID。</span><span class="sxs-lookup"><span data-stu-id="cb25d-159">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="cb25d-160">如果它来自，则为 `Debug-Runspace` ，它具有 `Debug-Runspace` GUID ID。</span><span class="sxs-lookup"><span data-stu-id="cb25d-160">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="cb25d-161">如果它来自 PowerShell 工作流，并且其工作流作业 ID 与当前的活动调试器工作流作业 ID 相同，则为。</span><span class="sxs-lookup"><span data-stu-id="cb25d-161">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="cb25d-162">相关链接</span><span class="sxs-lookup"><span data-stu-id="cb25d-162">RELATED LINKS</span></span>

[<span data-ttu-id="cb25d-163">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="cb25d-163">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="cb25d-164">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="cb25d-164">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="cb25d-165">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="cb25d-165">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="cb25d-166">Get-Process</span><span class="sxs-lookup"><span data-stu-id="cb25d-166">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="cb25d-167">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="cb25d-167">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="cb25d-168">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="cb25d-168">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

