---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596638"
---
# <span data-ttu-id="cbf20-102">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="cbf20-102">Enter-PSHostProcess</span></span>

## <span data-ttu-id="cbf20-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cbf20-103">SYNOPSIS</span></span>
<span data-ttu-id="cbf20-104">连接到并进入与本地进程的交互会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-104">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="cbf20-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbf20-105">SYNTAX</span></span>

### <span data-ttu-id="cbf20-106">ProcessIdParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="cbf20-106">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="cbf20-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="cbf20-107">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="cbf20-108">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cbf20-108">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="cbf20-109">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="cbf20-109">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="cbf20-110">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cbf20-110">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="cbf20-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cbf20-111">DESCRIPTION</span></span>

<span data-ttu-id="cbf20-112">`Enter-PSHostProcess`Cmdlet 使用本地进程连接到交互式会话并进入交互会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-112">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="cbf20-113">从 PowerShell 6.2 开始，非 Windows 平台上支持此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbf20-113">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="cbf20-114">远程交互式会话在已运行 PowerShell 的现有进程中运行，而不是创建一个新进程来托管 PowerShell 并运行远程会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-114">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="cbf20-115">如果要与指定进程上的远程会话交互，可以枚举正在运行的运行空间，然后通过运行或来选择要调试的运行 `Debug-Runspace` 空间 `Enable-RunspaceDebug` 。</span><span class="sxs-lookup"><span data-stu-id="cbf20-115">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="cbf20-116">要输入的进程必须承载 PowerShell ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="cbf20-116">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="cbf20-117">而你必须是发现该进程的计算机上“管理员”组的成员，或必须是运行启动进程的脚本的用户。</span><span class="sxs-lookup"><span data-stu-id="cbf20-117">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="cbf20-118">选择要调试的运行空间后，无论该运行空间当前是正在运行某个命令还是在调试器中已停止运行，都将为该运行空间打开一个远程调试会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-118">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="cbf20-119">你可以在其中按照调试其他远程会话脚本的相同方式调试该运行空间脚本。</span><span class="sxs-lookup"><span data-stu-id="cbf20-119">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="cbf20-120">运行两次 exit，先后离开调试会话和进程的交互会话，或通过运行现有调试器 Quit 命令停止脚本执行。</span><span class="sxs-lookup"><span data-stu-id="cbf20-120">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="cbf20-121">如果使用 Name 参数指定进程，并且只找到一个具有指定名称的进程，则进入该进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-121">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="cbf20-122">如果找到多个具有指定名称的进程，则 PowerShell 将返回错误，并列出所有使用指定名称找到的进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-122">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="cbf20-123">若要支持附加到远程计算机上的进程， `Enter-PSHostProcess` 可以在指定的远程计算机中启用该 cmdlet，以便在远程 PowerShell 会话中附加到本地进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-123">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="cbf20-124">示例</span><span class="sxs-lookup"><span data-stu-id="cbf20-124">EXAMPLES</span></span>

### <span data-ttu-id="cbf20-125">示例1：在 PowerShell ISE 进程内开始调试运行空间</span><span class="sxs-lookup"><span data-stu-id="cbf20-125">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="cbf20-126">在此示例中， `Enter-PSHostProcess` 从 PowerShell 控制台内运行以进入 POWERSHELL ISE 进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-126">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="cbf20-127">在生成的交互式会话中，可以通过运行来查找要调试的运行空间， `Get-Runspace` 然后调试运行空间。</span><span class="sxs-lookup"><span data-stu-id="cbf20-127">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="cbf20-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbf20-128">PARAMETERS</span></span>

### <span data-ttu-id="cbf20-129">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="cbf20-129">-AppDomainName</span></span>

<span data-ttu-id="cbf20-130">如果省略，则指定要连接到的应用程序域名，使用 **DefaultAppDomain**。</span><span class="sxs-lookup"><span data-stu-id="cbf20-130">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="cbf20-131">用于 `Get-PSHostProcessInfo` 显示应用程序域名。</span><span class="sxs-lookup"><span data-stu-id="cbf20-131">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-132">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="cbf20-132">-HostProcessInfo</span></span>

<span data-ttu-id="cbf20-133">指定可与 PowerShell 连接的 **get-pshostprocessinfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="cbf20-133">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="cbf20-134">使用 `Get-PSHostProcessInfo` 可获取对象。</span><span class="sxs-lookup"><span data-stu-id="cbf20-134">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-135">-Id</span><span class="sxs-lookup"><span data-stu-id="cbf20-135">-Id</span></span>

<span data-ttu-id="cbf20-136">按进程 ID 指定进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-136">Specifies a process by the process ID.</span></span> <span data-ttu-id="cbf20-137">若要获取进程 ID，请运行 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbf20-137">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-138">-Name</span><span class="sxs-lookup"><span data-stu-id="cbf20-138">-Name</span></span>

<span data-ttu-id="cbf20-139">按进程名称指定进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-139">Specifies a process by the process name.</span></span> <span data-ttu-id="cbf20-140">若要获取进程名称，请运行 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbf20-140">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="cbf20-141">还可以在“任务管理器”中通过进程的“属性”对话框获取进程名称。</span><span class="sxs-lookup"><span data-stu-id="cbf20-141">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-142">-Process</span><span class="sxs-lookup"><span data-stu-id="cbf20-142">-Process</span></span>

<span data-ttu-id="cbf20-143">按进程对象指定进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-143">Specifies a process by the process object.</span></span> <span data-ttu-id="cbf20-144">使用此参数的最简单方法是 `Get-Process` ：保存返回要在变量中输入的进程的命令的结果，然后将该变量指定为此参数的值。</span><span class="sxs-lookup"><span data-stu-id="cbf20-144">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-145">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="cbf20-145">-CustomPipeName</span></span>

<span data-ttu-id="cbf20-146">获取或设置要连接到的自定义命名管道名称。</span><span class="sxs-lookup"><span data-stu-id="cbf20-146">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="cbf20-147">这通常与一起使用 `pwsh -CustomPipeName` 。</span><span class="sxs-lookup"><span data-stu-id="cbf20-147">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="cbf20-148">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="cbf20-148">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbf20-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbf20-149">CommonParameters</span></span>

<span data-ttu-id="cbf20-150">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cbf20-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbf20-151">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cbf20-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbf20-152">输入</span><span class="sxs-lookup"><span data-stu-id="cbf20-152">INPUTS</span></span>

### <span data-ttu-id="cbf20-153">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="cbf20-153">System.Diagnostics.Process</span></span>

## <span data-ttu-id="cbf20-154">输出</span><span class="sxs-lookup"><span data-stu-id="cbf20-154">OUTPUTS</span></span>

## <span data-ttu-id="cbf20-155">注释</span><span class="sxs-lookup"><span data-stu-id="cbf20-155">NOTES</span></span>

<span data-ttu-id="cbf20-156">`Enter-PSHostProcess` 无法输入运行命令的 PowerShell 会话的进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-156">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="cbf20-157">但是，可以输入另一个 PowerShell 会话的进程，或输入与正在运行的会话同时运行的 PowerShell ISE 会话 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="cbf20-157">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="cbf20-158">`Enter-PSHostProcess` 只能输入托管 PowerShell 的进程。</span><span class="sxs-lookup"><span data-stu-id="cbf20-158">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="cbf20-159">也就是说，它们已加载 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="cbf20-159">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="cbf20-160">若要从进程内退出进程，请键入 **exit**，然后按 <kbd>enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cbf20-160">To exit a process from within the process, type **exit**, and then press <kbd>Enter</kbd>.</span></span>

<span data-ttu-id="cbf20-161">在 PowerShell 7.1 之前，通过 SSH 进行远程处理不支持第二个跃点的远程会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-161">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="cbf20-162">此功能仅限于使用 WinRM 的会话。</span><span class="sxs-lookup"><span data-stu-id="cbf20-162">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="cbf20-163">PowerShell 7.1 允许 `Enter-PSSession` 和 `Enter-PSHostProcess` 在任何交互式远程会话中工作。</span><span class="sxs-lookup"><span data-stu-id="cbf20-163">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="cbf20-164">相关链接</span><span class="sxs-lookup"><span data-stu-id="cbf20-164">RELATED LINKS</span></span>

[<span data-ttu-id="cbf20-165">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="cbf20-165">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="cbf20-166">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="cbf20-166">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)

