---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 8c9e520f1f19444fd538fabee99a48ec08c69992
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598479"
---
# <span data-ttu-id="9e0f7-102">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-102">Stop-Process</span></span>

## <span data-ttu-id="9e0f7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9e0f7-103">SYNOPSIS</span></span>
<span data-ttu-id="9e0f7-104">停止一个或多个正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-104">Stops one or more running processes.</span></span>

## <span data-ttu-id="9e0f7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e0f7-105">SYNTAX</span></span>

### <span data-ttu-id="9e0f7-106">ID（默认值）</span><span class="sxs-lookup"><span data-stu-id="9e0f7-106">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9e0f7-107">名称</span><span class="sxs-lookup"><span data-stu-id="9e0f7-107">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9e0f7-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="9e0f7-108">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9e0f7-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9e0f7-109">DESCRIPTION</span></span>

<span data-ttu-id="9e0f7-110">**停止进程** cmdlet 停止一个或多个正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-110">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="9e0f7-111">可以通过进程名称或进程 ID 指定进程 (PID) ，或将进程对象传递到 **停止进程**。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-111">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="9e0f7-112">**停止-进程** 仅适用于在本地计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-112">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="9e0f7-113">在 Windows Vista 和更高版本的 Windows 操作系统上，若要停止不是由当前用户拥有的进程，则必须使用 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-113">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="9e0f7-114">此外，除非指定 *Confirm* 参数，否则不会提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-114">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="9e0f7-115">示例</span><span class="sxs-lookup"><span data-stu-id="9e0f7-115">EXAMPLES</span></span>

### <span data-ttu-id="9e0f7-116">示例1：停止进程的所有实例</span><span class="sxs-lookup"><span data-stu-id="9e0f7-116">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="9e0f7-117">此命令停止计算机上 Notepad 进程的所有实例。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-117">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="9e0f7-118">记事本的每个实例都在其自己的进程中运行。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-118">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="9e0f7-119">它使用 *Name* 参数来指定进程，所有进程都具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-119">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="9e0f7-120">如果要使用 *Id* 参数来停止相同进程，则必须列出每个 Notepad 实例的进程 id。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-120">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="9e0f7-121">示例2：停止进程的特定实例</span><span class="sxs-lookup"><span data-stu-id="9e0f7-121">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="9e0f7-122">此命令停止 Notepad 进程的特定实例。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-122">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="9e0f7-123">它使用进程 ID 3952 来标识该进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-123">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="9e0f7-124">*Confirm* 参数指示 PowerShell 在停止该进程之前提示您。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-124">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="9e0f7-125">由于提示中包含进程名称的 ID，因此这是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-125">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="9e0f7-126">*PassThru* 参数将进程对象传递给格式化程序以进行显示。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-126">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="9e0f7-127">如果没有此参数，则在 **停止处理** 命令后将不会显示。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-127">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="9e0f7-128">示例3：停止进程并检测它是否已停止</span><span class="sxs-lookup"><span data-stu-id="9e0f7-128">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="9e0f7-129">这一系列命令将启动和停止 Calc 进程，然后检测已停止的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-129">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="9e0f7-130">第一个命令启动一个计算器实例。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-130">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="9e0f7-131">第二个命令使用 **获取进程** 获取一个表示 Calc 过程的对象，然后将该对象存储在 $p 的变量中。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-131">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="9e0f7-132">第三个命令停止计算进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-132">The third command stops the Calc process.</span></span>
<span data-ttu-id="9e0f7-133">它使用 *InputObject* 参数将对象传递到 **停止进程**。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-133">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="9e0f7-134">最后一个命令获取计算机上所有曾经运行但现已停止的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-134">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="9e0f7-135">它使用 **获取进程** 获取计算机上的所有进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-135">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="9e0f7-136">管道运算符 (|) 将结果传递给 Where-Object cmdlet，该 cmdlet 选择 **HasExited** 属性的值 $True 的值。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-136">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="9e0f7-137">**HasExited** 只是进程对象的一个属性。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-137">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="9e0f7-138">若要查找所有属性，请键入 `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-138">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="9e0f7-139">示例4：停止不是由当前用户拥有的进程</span><span class="sxs-lookup"><span data-stu-id="9e0f7-139">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="9e0f7-140">这些命令演示了使用 *Force* 停止用户不拥有的进程的效果。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-140">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="9e0f7-141">第一个命令使用 **Get 进程** 获取 Lsass 进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-141">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="9e0f7-142">管道运算符将进程发送到 **停止进程** 以停止进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-142">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="9e0f7-143">如示例输出中所示，第一个命令失败并出现 "拒绝访问" 消息，因为此进程只能由计算机上的管理员组的成员停止。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-143">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="9e0f7-144">使用 "以管理员身份运行" 选项打开 PowerShell 后，命令重复，PowerShell 会提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-144">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="9e0f7-145">第二个命令指定 *强制* 禁止显示提示。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-145">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="9e0f7-146">因此进程将在不提示确认的情况下停止。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-146">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="9e0f7-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e0f7-147">PARAMETERS</span></span>

### <span data-ttu-id="9e0f7-148">-Force</span><span class="sxs-lookup"><span data-stu-id="9e0f7-148">-Force</span></span>

<span data-ttu-id="9e0f7-149">在不提示确认的情况下停止指定的进程。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-149">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="9e0f7-150">默认情况下，在停止当前用户不拥有的任何进程之前， **停止进程** 提示进行确认。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-150">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="9e0f7-151">若要查找进程的所有者，请使用 `Get-CimInstance` cmdlet 获取表示该进程的 **Win32_Process** 对象，然后使用该对象的 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-151">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="9e0f7-152">-Id</span><span class="sxs-lookup"><span data-stu-id="9e0f7-152">-Id</span></span>

<span data-ttu-id="9e0f7-153">指定要停止的进程的进程 Id。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-153">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="9e0f7-154">若要指定多个 ID，请使用逗号分隔 ID。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-154">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="9e0f7-155">若要查找进程的 PID，请键入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-155">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9e0f7-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9e0f7-156">-InputObject</span></span>

<span data-ttu-id="9e0f7-157">指定要停止的进程对象。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-157">Specifies the process objects to stop.</span></span>
<span data-ttu-id="9e0f7-158">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9e0f7-159">-Name</span><span class="sxs-lookup"><span data-stu-id="9e0f7-159">-Name</span></span>

<span data-ttu-id="9e0f7-160">指定要停止的进程的进程名称。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-160">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="9e0f7-161">可以键入多个进程名称（以逗号分隔）或使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-161">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9e0f7-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9e0f7-162">-PassThru</span></span>

<span data-ttu-id="9e0f7-163">返回一个表示进程的对象。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-163">Returns an object that represents the process.</span></span>
<span data-ttu-id="9e0f7-164">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9e0f7-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9e0f7-165">-Confirm</span></span>

<span data-ttu-id="9e0f7-166">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9e0f7-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9e0f7-167">-WhatIf</span></span>

<span data-ttu-id="9e0f7-168">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9e0f7-169">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9e0f7-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e0f7-170">CommonParameters</span></span>
<span data-ttu-id="9e0f7-171">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e0f7-172">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-172">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e0f7-173">输入</span><span class="sxs-lookup"><span data-stu-id="9e0f7-173">INPUTS</span></span>

### <span data-ttu-id="9e0f7-174">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-174">System.Diagnostics.Process</span></span>

<span data-ttu-id="9e0f7-175">可以将进程对象通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-175">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="9e0f7-176">输出</span><span class="sxs-lookup"><span data-stu-id="9e0f7-176">OUTPUTS</span></span>

### <span data-ttu-id="9e0f7-177">无、System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-177">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="9e0f7-178">如果指定 *PassThru* 参数，则此 cmdlet 将返回一个表示已停止进程的 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-178">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="9e0f7-179">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-179">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9e0f7-180">注释</span><span class="sxs-lookup"><span data-stu-id="9e0f7-180">NOTES</span></span>

* <span data-ttu-id="9e0f7-181">还可以通过其内置别名 " **kill** " 和 " **spps**" 来对 **其进行引用**。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-181">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="9e0f7-182">有关详细信息，请参阅 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-182">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="9e0f7-183">你还可以在 Windows PowerShell 中使用 Windows Management Instrumentation (WMI) **Win32_Process** 对象的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-183">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="9e0f7-184">有关详细信息，请参阅 `Get-CimInstance` 和 WMI SDK。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-184">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="9e0f7-185">停止进程时，请注意停止进程可能会停止依赖该进程的进程和服务。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-185">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="9e0f7-186">在极端情况下，停止进程可能会使 Windows 停止。</span><span class="sxs-lookup"><span data-stu-id="9e0f7-186">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="9e0f7-187">相关链接</span><span class="sxs-lookup"><span data-stu-id="9e0f7-187">RELATED LINKS</span></span>

[<span data-ttu-id="9e0f7-188">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-188">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="9e0f7-189">Get-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-189">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="9e0f7-190">Start-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-190">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="9e0f7-191">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-191">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="9e0f7-192">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="9e0f7-192">Wait-Process</span></span>](Wait-Process.md)

