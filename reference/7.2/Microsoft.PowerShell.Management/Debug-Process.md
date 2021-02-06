---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 660d2b4845df8091ff8b69b28c4e7695af557122
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597669"
---
# <span data-ttu-id="7bc1d-102">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-102">Debug-Process</span></span>

## <span data-ttu-id="7bc1d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="7bc1d-103">SYNOPSIS</span></span>
<span data-ttu-id="7bc1d-104">调试在本地计算机上运行的一个或多个进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-104">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="7bc1d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7bc1d-105">SYNTAX</span></span>

### <span data-ttu-id="7bc1d-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="7bc1d-106">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7bc1d-107">ID</span><span class="sxs-lookup"><span data-stu-id="7bc1d-107">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7bc1d-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="7bc1d-108">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7bc1d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7bc1d-109">DESCRIPTION</span></span>

<span data-ttu-id="7bc1d-110">`Debug-Process`Cmdlet 可将调试程序附加到本地计算机上的一个或多个正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-110">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="7bc1d-111">可以通过进程名称或进程 ID (PID) 来指定进程，也可以将进程对象通过管道传送给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-111">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="7bc1d-112">此 cmdlet 将附加当前为该进程注册的调试程序。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-112">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="7bc1d-113">使用此 cmdlet 之前，请先验证调试程序是否已下载并正确配置。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-113">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="7bc1d-114">示例</span><span class="sxs-lookup"><span data-stu-id="7bc1d-114">EXAMPLES</span></span>

### <span data-ttu-id="7bc1d-115">示例 1：将调试程序附加到计算机上的进程</span><span class="sxs-lookup"><span data-stu-id="7bc1d-115">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="7bc1d-116">此命令将调试程序附加到计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-116">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="7bc1d-117">示例 2：将调试程序附加到以指定字符串开头的所有进程</span><span class="sxs-lookup"><span data-stu-id="7bc1d-117">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="7bc1d-118">此命令将调试程序附加到名称以 SQL 开头的所有进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-118">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="7bc1d-119">示例 3：将调试程序附加到多个进程</span><span class="sxs-lookup"><span data-stu-id="7bc1d-119">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="7bc1d-120">此命令将调试程序附加到 Winlogon、Explorer 和 Outlook 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-120">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="7bc1d-121">示例 4：将调试程序附加到多个进程 ID</span><span class="sxs-lookup"><span data-stu-id="7bc1d-121">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="7bc1d-122">此命令将调试程序附加到进程 ID 为 1132 和 2028 的进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-122">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="7bc1d-123">示例 5：使用 Get-Process 获取进程，然后将调试程序附加到它</span><span class="sxs-lookup"><span data-stu-id="7bc1d-123">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="7bc1d-124">此命令将调试程序附加到计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-124">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="7bc1d-125">它使用 `Get-Process` cmdlet 获取计算机上的 PowerShell 进程，并使用管道操作员 (`|`) 将进程发送到 `Debug-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-125">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="7bc1d-126">若要指定特定的 PowerShell 进程，请使用的 ID 参数 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-126">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="7bc1d-127">示例 6：将调试程序附加到本地计算机上的当前进程</span><span class="sxs-lookup"><span data-stu-id="7bc1d-127">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="7bc1d-128">此命令将调试程序附加到计算机上的当前 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-128">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="7bc1d-129">该命令使用 `$PID` 自动变量，其中包含当前 PowerShell 进程的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-129">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="7bc1d-130">然后，它使用管道运算符 (`|`) 将进程 ID 发送到 `Debug-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-130">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="7bc1d-131">有关自动变量的详细信息 `$PID` ，请参阅 about_Automatic_Variables。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-131">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="7bc1d-132">示例7：将调试程序附加到使用 InputObject 参数的进程</span><span class="sxs-lookup"><span data-stu-id="7bc1d-132">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="7bc1d-133">此命令将调试程序附加到本地计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-133">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="7bc1d-134">第一个命令使用 `Get-Process` cmdlet 来获取计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-134">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="7bc1d-135">它将生成的进程对象保存在变量中 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-135">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="7bc1d-136">第二个命令使用 cmdlet 的 **InputObject** 参数 `Debug-Process` 来提交变量中的进程对象 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-136">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="7bc1d-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7bc1d-137">PARAMETERS</span></span>

### <span data-ttu-id="7bc1d-138">-Id</span><span class="sxs-lookup"><span data-stu-id="7bc1d-138">-Id</span></span>

<span data-ttu-id="7bc1d-139">指定要调试的进程的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-139">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="7bc1d-140">Id 参数名为可选项。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-140">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="7bc1d-141">要查找进程的进程 ID，请键入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-141">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="7bc1d-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7bc1d-142">-InputObject</span></span>

<span data-ttu-id="7bc1d-143">指定表示要调试的进程的进程对象。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-143">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="7bc1d-144">输入包含进程对象的变量或获取进程对象的命令（如 `Get-Process` cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-144">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="7bc1d-145">还可以将进程对象通过管道传送给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-145">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="7bc1d-146">-Name</span><span class="sxs-lookup"><span data-stu-id="7bc1d-146">-Name</span></span>

<span data-ttu-id="7bc1d-147">指定要调试的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-147">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="7bc1d-148">如果存在多个同名进程，则此 cmdlet 会将调试程序附加到所有该名称的进程。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-148">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="7bc1d-149">**Name** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-149">The **Name** parameter is optional.</span></span>

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

### <span data-ttu-id="7bc1d-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7bc1d-150">-Confirm</span></span>

<span data-ttu-id="7bc1d-151">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7bc1d-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7bc1d-152">-WhatIf</span></span>

<span data-ttu-id="7bc1d-153">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7bc1d-154">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7bc1d-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7bc1d-155">CommonParameters</span></span>

<span data-ttu-id="7bc1d-156">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7bc1d-157">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7bc1d-158">输入</span><span class="sxs-lookup"><span data-stu-id="7bc1d-158">INPUTS</span></span>

### <span data-ttu-id="7bc1d-159">System.Int32、System.Diagnostics.Process、System.String</span><span class="sxs-lookup"><span data-stu-id="7bc1d-159">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="7bc1d-160">可以通过管道将进程 ID (Int32)、进程对象 (System.Diagnostics.Process) 或进程名称 (String) 传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-160">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="7bc1d-161">输出</span><span class="sxs-lookup"><span data-stu-id="7bc1d-161">OUTPUTS</span></span>

### <span data-ttu-id="7bc1d-162">无</span><span class="sxs-lookup"><span data-stu-id="7bc1d-162">None</span></span>

<span data-ttu-id="7bc1d-163">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-163">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7bc1d-164">注释</span><span class="sxs-lookup"><span data-stu-id="7bc1d-164">NOTES</span></span>

<span data-ttu-id="7bc1d-165">此 cmdlet 使用 Windows Management Instrumentation (WMI) Win32_Process 类的 AttachDebugger 方法。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-165">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="7bc1d-166">有关此方法的详细信息，请参阅 MSDN library 中的 [AttachDebugger 方法](https://go.microsoft.com/fwlink/?LinkId=143640) 。</span><span class="sxs-lookup"><span data-stu-id="7bc1d-166">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="7bc1d-167">相关链接</span><span class="sxs-lookup"><span data-stu-id="7bc1d-167">RELATED LINKS</span></span>

[<span data-ttu-id="7bc1d-168">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-168">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="7bc1d-169">Get-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-169">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="7bc1d-170">Start-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-170">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="7bc1d-171">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-171">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="7bc1d-172">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="7bc1d-172">Wait-Process</span></span>](Wait-Process.md)
