---
title: PowerShell 远程处理
description: 可以通过多种不同的方式在 PowerShell 中对远程计算机运行命令。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0e467a41282b261c56a89578dbc841725f59a6e0
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596205"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="1edc9-103">第 8 章 - PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="1edc9-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="1edc9-104">PowerShell 提供多种不同的方法对远程计算机运行命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="1edc9-105">在上一章中，你已了解如何使用 CIM cmdlet 远程查询 WMI。</span><span class="sxs-lookup"><span data-stu-id="1edc9-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="1edc9-106">PowerShell 还包括多个具有内置 ComputerName 参数的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1edc9-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="1edc9-107">如下面的示例中所示，可以配合使用 `Get-Command` 和 ParameterName 参数，以确定哪些命令具有 ComputerName 参数 。</span><span class="sxs-lookup"><span data-stu-id="1edc9-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

<span data-ttu-id="1edc9-108">`Get-Process` 和 `Get-Hotfix` 之类的命令具有 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="1edc9-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="1edc9-109">这并非 Microsoft 针对远程计算机运行命令的长期方向。</span><span class="sxs-lookup"><span data-stu-id="1edc9-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="1edc9-110">即使你找到的命令具有 ComputerName 参数，也可能需要指定备用凭据，并且它没有 Credential 参数 。</span><span class="sxs-lookup"><span data-stu-id="1edc9-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="1edc9-111">如果决定从提升的帐户运行 PowerShell，则你与远程计算机之间的防火墙可能会阻止请求。</span><span class="sxs-lookup"><span data-stu-id="1edc9-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="1edc9-112">要使用本章中演示的 PowerShell 远程处理命令，必须在远程计算机上启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="1edc9-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="1edc9-113">使用 `Enable-PSRemoting` cmdlet 启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="1edc9-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a><span data-ttu-id="1edc9-114">一对一远程处理</span><span class="sxs-lookup"><span data-stu-id="1edc9-114">One-To-One Remoting</span></span>

<span data-ttu-id="1edc9-115">如果要使远程会话成为交互式会话，则需要一对一远程处理。</span><span class="sxs-lookup"><span data-stu-id="1edc9-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="1edc9-116">这种类型的远程处理是通过 `Enter-PSSession` cmdlet 提供的。</span><span class="sxs-lookup"><span data-stu-id="1edc9-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="1edc9-117">在上一章中，我将我的域管理员凭据存储在名为 `$Cred` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="1edc9-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="1edc9-118">如果尚未执行此操作，请继续将域管理员凭据存储在 `$Cred` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1edc9-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="1edc9-119">这允许输入一次凭据，并在当前 PowerShell 会话处于活动状态时，按命令使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="1edc9-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="1edc9-120">创建与名为 dc01 的域控制器的一对一 PowerShell 远程处理会话。</span><span class="sxs-lookup"><span data-stu-id="1edc9-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="1edc9-121">请注意，在上一个示例中，PowerShell 提示符的前缀是 `[dc01]`。</span><span class="sxs-lookup"><span data-stu-id="1edc9-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="1edc9-122">这意味着你处于与名为 dc01 的远程计算机的交互式 PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="1edc9-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="1edc9-123">在 dc01 上而不是在本地计算机上执行的任何命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="1edc9-124">另外，请记住，你只能访问远程计算机上存在的 PowerShell 命令，而不是本地计算机上的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="1edc9-125">换句话说，如果你已在计算机上安装了其他模块，则无法在远程计算机上访问它们。</span><span class="sxs-lookup"><span data-stu-id="1edc9-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="1edc9-126">通过一对一交互式 PowerShell 远程处理会话连接到远程计算机时，实际上就是在使用远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1edc9-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="1edc9-127">相关对象是普通对象，就像你在整本书中使用的对象一样。</span><span class="sxs-lookup"><span data-stu-id="1edc9-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

```powershell
[dc01]:  Get-Process | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
[dc01]:
```

<span data-ttu-id="1edc9-128">使用完远程计算机后，请使用 `Exit-PSSession` cmdlet 退出一对一远程处理会话。</span><span class="sxs-lookup"><span data-stu-id="1edc9-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="1edc9-129">一对多远程处理</span><span class="sxs-lookup"><span data-stu-id="1edc9-129">One-To-Many Remoting</span></span>

<span data-ttu-id="1edc9-130">有时，你可能需要在远程计算机上以交互方式执行任务。</span><span class="sxs-lookup"><span data-stu-id="1edc9-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="1edc9-131">但在多台远程计算机上同时执行一项任务时，远程处理功能要强大得多。</span><span class="sxs-lookup"><span data-stu-id="1edc9-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="1edc9-132">使用 `Invoke-Command` cmdlet 对一台或多台远程计算机同时运行命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="1edc9-133">在上面的示例中，查询了三台服务器的 Windows 时间服务状态。</span><span class="sxs-lookup"><span data-stu-id="1edc9-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="1edc9-134">`Get-Service` cmdlet 位于 `Invoke-Command` 的脚本块内。</span><span class="sxs-lookup"><span data-stu-id="1edc9-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="1edc9-135">`Get-Service` 实际上在远程计算机上运行，而结果作为反序列化的对象返回到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1edc9-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="1edc9-136">通过将上一条命令通过管道传递到 `Get-Member`，可表明结果确实是反序列化的对象。</span><span class="sxs-lookup"><span data-stu-id="1edc9-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

<span data-ttu-id="1edc9-137">请注意，反序列化的对象上缺少大多数方法。</span><span class="sxs-lookup"><span data-stu-id="1edc9-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="1edc9-138">这意味着它们不是活动对象；而是静态对象。</span><span class="sxs-lookup"><span data-stu-id="1edc9-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="1edc9-139">无法使用反序列化的对象启动或停止服务，因为它是命令在远程计算机上运行时，该对象所处状态的快照。</span><span class="sxs-lookup"><span data-stu-id="1edc9-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="1edc9-140">但这并不意味着无法使用带有 `Invoke-Command` 的方法来启动或停止服务。</span><span class="sxs-lookup"><span data-stu-id="1edc9-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="1edc9-141">这只意味着必须在远程会话中调用该方法。</span><span class="sxs-lookup"><span data-stu-id="1edc9-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="1edc9-142">我将使用 Stop() 方法停止全部三台远程服务器上的 Windows 时间服务，以证明这一点。</span><span class="sxs-lookup"><span data-stu-id="1edc9-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="1edc9-143">如前一章中所述，如果存在用于完成任务的 cmdlet，则建议使用它，而不是使用方法。</span><span class="sxs-lookup"><span data-stu-id="1edc9-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="1edc9-144">在前面的情况中，建议使用 `Stop-Service` cmdlet，而不是停止方法。</span><span class="sxs-lookup"><span data-stu-id="1edc9-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="1edc9-145">我选择使用 Stop() 方法来证明这一点，因为很多人都误认为在使用 PowerShell 远程处理时不能调用方法。</span><span class="sxs-lookup"><span data-stu-id="1edc9-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="1edc9-146">无法在返回的对象上调用方法（因为返回的是反序列化的对象），但可以在远程会话本身之中调用它们。</span><span class="sxs-lookup"><span data-stu-id="1edc9-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="1edc9-147">PowerShell 会话</span><span class="sxs-lookup"><span data-stu-id="1edc9-147">PowerShell Sessions</span></span>

<span data-ttu-id="1edc9-148">在上一节的最后一个示例中，我使用 `Invoke-Command` cmdlet 运行了两个命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="1edc9-149">这意味着必须设置两个单独的会话，并进行拆解以运行这两个命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="1edc9-150">与第 7 章中讨论的 CIM 会话类似，可以使用与远程计算机的 PowerShell 会话对远程计算机运行多个命令，而不会产生每个单独命令的新会话开销。</span><span class="sxs-lookup"><span data-stu-id="1edc9-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="1edc9-151">为本章中使用的三台计算机 DC01、SQL02 和 WEB01 分别创建一个 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="1edc9-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="1edc9-152">现在，使用名为 `$Session` 的变量通过某个方法启动 Windows 时间服务，并检查服务的状态。</span><span class="sxs-lookup"><span data-stu-id="1edc9-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="1edc9-153">使用备用凭据创建会话后，每次运行命令时，都不再需要指定凭据。</span><span class="sxs-lookup"><span data-stu-id="1edc9-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="1edc9-154">使用完会话后，请确保将其删除。</span><span class="sxs-lookup"><span data-stu-id="1edc9-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="1edc9-155">总结</span><span class="sxs-lookup"><span data-stu-id="1edc9-155">Summary</span></span>

<span data-ttu-id="1edc9-156">在本章中，你已了解 PowerShell 远程处理、如何在与一台远程计算机的交互式会话中运行命令，以及如何使用一对多远程处理对多台计算机运行命令。</span><span class="sxs-lookup"><span data-stu-id="1edc9-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="1edc9-157">你还了解了对同一台远程计算机运行多个命令时，使用 PowerShell 会话的好处。</span><span class="sxs-lookup"><span data-stu-id="1edc9-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="1edc9-158">审阅</span><span class="sxs-lookup"><span data-stu-id="1edc9-158">Review</span></span>

1. <span data-ttu-id="1edc9-159">如何启用 PowerShell 远程处理？</span><span class="sxs-lookup"><span data-stu-id="1edc9-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="1edc9-160">用于启动与远程计算机的交互式会话的 PowerShell 命令是什么？</span><span class="sxs-lookup"><span data-stu-id="1edc9-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="1edc9-161">与仅使用每个命令指定计算机名相比，使用 PowerShell 远程处理会话有何优势？</span><span class="sxs-lookup"><span data-stu-id="1edc9-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="1edc9-162">PowerShell 远程处理会话是否可以与一对一远程处理会话一起使用？</span><span class="sxs-lookup"><span data-stu-id="1edc9-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="1edc9-163">Cmdlet 返回的对象类型与使用 `Invoke-Command` 对远程计算机运行相同 cmdlet 时返回的对象类型有什么不同？</span><span class="sxs-lookup"><span data-stu-id="1edc9-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="1edc9-164">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="1edc9-164">Recommended Reading</span></span>

- <span data-ttu-id="1edc9-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-165">[about_Remote][]</span></span>
- <span data-ttu-id="1edc9-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="1edc9-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="1edc9-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="1edc9-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="1edc9-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="1edc9-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
