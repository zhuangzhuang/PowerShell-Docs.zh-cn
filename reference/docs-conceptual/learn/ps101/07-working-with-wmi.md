---
title: 使用 WMI
description: 从一开始，PowerShell 就具有可处理 WMI 的 cmdlet。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 119bb3381ee55c70340da89d1c0690d84b3e70d2
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99597844"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="1038e-103">第 7 章 - 使用 WMI</span><span class="sxs-lookup"><span data-stu-id="1038e-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="1038e-104">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="1038e-104">WMI and CIM</span></span>

<span data-ttu-id="1038e-105">默认情况下，PowerShell 附带可处理 Windows Management Instrumentation (WMI) 等其他技术的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1038e-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="1038e-106">PowerShell 中存在多个本机 WMI cmdlet，且无需安装任何其他软件或模块。</span><span class="sxs-lookup"><span data-stu-id="1038e-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="1038e-107">从一开始，PowerShell 就具有可处理 WMI 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1038e-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="1038e-108">`Get-Command` 可用于确定 PowerShell 中存在哪些 WMI cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1038e-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="1038e-109">以下结果来自运行 5.1 版 PowerShell 的 Windows 10 实验环境计算机。</span><span class="sxs-lookup"><span data-stu-id="1038e-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="1038e-110">结果因运行的 PowerShell 版本而异。</span><span class="sxs-lookup"><span data-stu-id="1038e-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="1038e-111">PowerShell 版本 3.0 中引入了通用信息模型 (CIM) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1038e-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="1038e-112">CIM cmdlet 的设计目的是使其可以同时在 Windows 和非 Windows 计算机上使用。</span><span class="sxs-lookup"><span data-stu-id="1038e-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="1038e-113">由于 WMI cmdlet 已弃用，因此建议使用 CIM cmdlet 代替 WMI cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1038e-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="1038e-114">所有 CIM cmdlet 都包含在一个模块中。</span><span class="sxs-lookup"><span data-stu-id="1038e-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="1038e-115">若要获取 CIM cmdlet 的列表，请结合使用 `Get-Command` 与 Module 参数，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1038e-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="1038e-116">如果使用 CIM cmdlet，仍可使用 WMI，因此当有人说出“当我使用 PowerShell CIM cmdlet 查询 WMI 时...”这样的话时，请不要感到疑惑</span><span class="sxs-lookup"><span data-stu-id="1038e-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="1038e-117">如前所述，WMI 是一项独立于 PowerShell 的技术，现在不过是使用 CIM cmdlet 来访问 WMI 而已。</span><span class="sxs-lookup"><span data-stu-id="1038e-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="1038e-118">你可能会发现一个旧的 VBScript，它使用 WMI 查询语言 (WQL) 来查询 WMI，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="1038e-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="1038e-119">可以从该 VBScript 中获取 WQL 查询，并将其与 `Get-CimInstance` cmdlet 一起使用，而无需进行任何修改。</span><span class="sxs-lookup"><span data-stu-id="1038e-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="1038e-120">这并不是我使用 PowerShell 查询 WMI 的常用方式。</span><span class="sxs-lookup"><span data-stu-id="1038e-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="1038e-121">但是该方法确实有效，通过该方法，可以轻松地将现有 VBScript 迁移到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1038e-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="1038e-122">当我开始编写用于查询 WMI 的单项时，我使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="1038e-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="1038e-123">如果只需要序列号，则可以通过管道将输出传递给 `Select-Object` 并仅指定 SerialNumber 属性。</span><span class="sxs-lookup"><span data-stu-id="1038e-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="1038e-124">默认情况下，系统会在后台检索一些从不使用的属性。</span><span class="sxs-lookup"><span data-stu-id="1038e-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="1038e-125">在本地计算机上查询 WMI 时，这可能不会产生什么影响。</span><span class="sxs-lookup"><span data-stu-id="1038e-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="1038e-126">但是，如果开始查询远程计算机，前述检索不仅要花费更多的处理时间来返回相关信息，还会在网络中拉取不必要的额外信息。</span><span class="sxs-lookup"><span data-stu-id="1038e-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="1038e-127">`Get-CimInstance` 有一个可以限制检索到的信息的 Property 参数。</span><span class="sxs-lookup"><span data-stu-id="1038e-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="1038e-128">这会提升 WMI 查询的效率。</span><span class="sxs-lookup"><span data-stu-id="1038e-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="1038e-129">之前的结果返回了一个对象。</span><span class="sxs-lookup"><span data-stu-id="1038e-129">The previous results returned an object.</span></span> <span data-ttu-id="1038e-130">若要返回简单字符串，请使用 ExpandProperty 参数。</span><span class="sxs-lookup"><span data-stu-id="1038e-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="1038e-131">也可以使用点式语法返回简单字符串。</span><span class="sxs-lookup"><span data-stu-id="1038e-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="1038e-132">这样就无需通过管道传递到 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="1038e-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="1038e-133">使用 CIM cmdlet 查询远程计算机</span><span class="sxs-lookup"><span data-stu-id="1038e-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="1038e-134">我仍以作为域用户的本地管理员身份运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1038e-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="1038e-135">当我尝试使用 `Get-CimInstance` cmdlet 从远程计算机查询信息时，我收到一条“拒绝访问”的错误消息。</span><span class="sxs-lookup"><span data-stu-id="1038e-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="1038e-136">在谈到 PowerShell 时，很多人都担心安全性，但事实是，你在 PowerShell 中拥有与在 GUI 中完全相同的权限。</span><span class="sxs-lookup"><span data-stu-id="1038e-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="1038e-137">不多不少刚刚好。</span><span class="sxs-lookup"><span data-stu-id="1038e-137">No more and no less.</span></span> <span data-ttu-id="1038e-138">上一个示例中的问题是，运行 PowerShell 的用户不具有通过 DC01 服务器查询 WMI 信息的权限。</span><span class="sxs-lookup"><span data-stu-id="1038e-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="1038e-139">由于 `Get-CimInstance` 没有 Credential 参数，我能够以域管理员的身份重启 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1038e-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="1038e-140">但请相信我，这不是一个好主意，因为从 PowerShell 中运行的所有内容都将以域管理员身份运行。从安全性的角度来看，这可能并不安全，这取决于具体情况。</span><span class="sxs-lookup"><span data-stu-id="1038e-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="1038e-141">基于最低特权原则，在每个命令的基础上，我使用 Credential 参数（如果命令包含该参数）提升到我的域管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="1038e-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="1038e-142">`Get-CimInstance` 没有 Credential 参数，因此在这种情况下，解决方案是先创建一个 CimSession 。</span><span class="sxs-lookup"><span data-stu-id="1038e-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="1038e-143">然后，使用 CimSession（而不是计算机名）查询远程计算机上的 WMI。</span><span class="sxs-lookup"><span data-stu-id="1038e-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="1038e-144">CIM 会话存储在名为 `$CimSession` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="1038e-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="1038e-145">请注意，我还在括号中指定了 `Get-Credential` cmdlet，以便在创建新会话之前先执行该 cmdlet，提示我输入备用凭据。</span><span class="sxs-lookup"><span data-stu-id="1038e-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="1038e-146">本章的后面部分将介绍另一种更为有效的方式来指定备用凭据，但在深入介绍相关概念及更复杂的内容之前，请务必先了解这一基本概念。</span><span class="sxs-lookup"><span data-stu-id="1038e-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="1038e-147">现在可以将上一个示例中创建的 CIM 会话与 `Get-CimInstance` cmdlet 一起使用，从远程计算机上的 WMI 查询 BIOS 信息。</span><span class="sxs-lookup"><span data-stu-id="1038e-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="1038e-148">使用 CIM 会话还有其他好处，而不仅仅是指定计算机名。</span><span class="sxs-lookup"><span data-stu-id="1038e-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="1038e-149">在同一台计算机上运行多个查询时，为每个查询使用 CIM 会话比使用计算机名更有效。</span><span class="sxs-lookup"><span data-stu-id="1038e-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="1038e-150">创建 CIM 会话时只需建立一次连接。</span><span class="sxs-lookup"><span data-stu-id="1038e-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="1038e-151">然后，多个查询使用此同一会话检索信息。</span><span class="sxs-lookup"><span data-stu-id="1038e-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="1038e-152">如果使用计算机名，cmdlet 需要建立和断开与每个查询的连接。</span><span class="sxs-lookup"><span data-stu-id="1038e-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="1038e-153">`Get-CimInstance` cmdlet 默认使用 WSMan 协议，这意味着远程计算机需要 PowerShell 3.0 或更高版本才能进行连接。</span><span class="sxs-lookup"><span data-stu-id="1038e-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="1038e-154">实际上，PowerShell 版本并不那么重要，重要的是堆栈版本。</span><span class="sxs-lookup"><span data-stu-id="1038e-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="1038e-155">可以使用 `Test-WSMan` cmdlet 确定堆栈版本。</span><span class="sxs-lookup"><span data-stu-id="1038e-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="1038e-156">堆栈版本需为 3.0。</span><span class="sxs-lookup"><span data-stu-id="1038e-156">It needs to be version 3.0.</span></span> <span data-ttu-id="1038e-157">PowerShell 3.0 及更高版本提供该版本的堆栈。</span><span class="sxs-lookup"><span data-stu-id="1038e-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="1038e-158">较旧的 WMI cmdlet 使用 DCOM 协议，该协议与较低版本的 Windows 兼容。</span><span class="sxs-lookup"><span data-stu-id="1038e-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="1038e-159">而较新 Windows 版本上的防火墙通常会阻止 DCOM。</span><span class="sxs-lookup"><span data-stu-id="1038e-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="1038e-160">可使用 `New-CimSessionOption` cmdlet 创建可与 `New-CimSession` 一起使用的 DCOM 协议连接。</span><span class="sxs-lookup"><span data-stu-id="1038e-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="1038e-161">这样便可使用 `Get-CimInstance` cmdlet 与低至 Windows Server 2000 的 Windows 版本进行通信。</span><span class="sxs-lookup"><span data-stu-id="1038e-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="1038e-162">这也意味着，将 `Get-CimInstance` cmdlet 与配置为使用 DCOM 协议的 CimSession 一起使用时，远程计算机上不需要 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1038e-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="1038e-163">使用 `New-CimSessionOption` cmdlet 创建 DCOM 协议选项，并将其存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="1038e-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="1038e-164">为了提高效率，可以将域管理员凭据或提升的凭据存储在变量中，这样就不必一直为每个命令输入这些信息。</span><span class="sxs-lookup"><span data-stu-id="1038e-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="1038e-165">我有一台名为 SQL03 的服务器，该服务器运行 Windows Server 2008（非 R2）。</span><span class="sxs-lookup"><span data-stu-id="1038e-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="1038e-166">它是默认情况下未安装 PowerShell 的最新 Windows Server 操作系统。</span><span class="sxs-lookup"><span data-stu-id="1038e-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="1038e-167">使用 DCOM 协议在 SQL03 上创建 CimSession。</span><span class="sxs-lookup"><span data-stu-id="1038e-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="1038e-168">请注意，在上一条命令中，我将名为 `$Cred` 的变量指定为 Credential 参数的值，这样就不必再次手动输入这些值。</span><span class="sxs-lookup"><span data-stu-id="1038e-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="1038e-169">无论使用哪种基础协议，查询的输出都是相同的。</span><span class="sxs-lookup"><span data-stu-id="1038e-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="1038e-170">`Get-CimSession` cmdlet 用于查看当前连接的 CimSessions 及其正在使用的协议。</span><span class="sxs-lookup"><span data-stu-id="1038e-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="1038e-171">检索两个先前创建的 CimSession 并将其存储在名为 `$CimSession` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="1038e-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="1038e-172">使用一个命令同时查询这两台计算机，它们分别使用 WSMan 协议和 DCOM。</span><span class="sxs-lookup"><span data-stu-id="1038e-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="1038e-173">我写了许多有关 WMI 和 CIM cmdlet 的博客文章。</span><span class="sxs-lookup"><span data-stu-id="1038e-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="1038e-174">其中最有用的一篇文章与我创建的一个函数有关，该函数自动确定应使用 WSMan 还是 DCOM 并自动设置 CIM 会话，而无需手动查找是哪一个。</span><span class="sxs-lookup"><span data-stu-id="1038e-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="1038e-175">该博客文章的标题为[用于在远程计算机上创建 CimSession 并将其回退到 Dcom 的 PowerShell 函数][]。</span><span class="sxs-lookup"><span data-stu-id="1038e-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="1038e-176">完成 CIM 会话后，应使用 `Remove-CimSession` cmdlet 将其删除。</span><span class="sxs-lookup"><span data-stu-id="1038e-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="1038e-177">要删除所有 CIM 会话，只需通过管道将 `Get-CimSession` 传递到 `Remove-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="1038e-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="1038e-178">总结</span><span class="sxs-lookup"><span data-stu-id="1038e-178">Summary</span></span>

<span data-ttu-id="1038e-179">在本章中，你了解了如何通过 PowerShell 在本地和远程计算机上使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="1038e-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="1038e-180">你还了解了如何使用 CIM cmdlet 分别处理具有 WSMan 和 DCOM 协议的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="1038e-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="1038e-181">审阅</span><span class="sxs-lookup"><span data-stu-id="1038e-181">Review</span></span>

1. <span data-ttu-id="1038e-182">WMI 和 CIM cmdlet 有何区别？</span><span class="sxs-lookup"><span data-stu-id="1038e-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="1038e-183">默认情况下，`Get-CimInstance` cmdlet 使用哪种协议？</span><span class="sxs-lookup"><span data-stu-id="1038e-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="1038e-184">使用 CIM 会话而不使用 `Get-CimInstance` 指定计算机名有哪些好处？</span><span class="sxs-lookup"><span data-stu-id="1038e-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="1038e-185">如何指定与 `Get-CimInstance` 一起使用的备用协议而不使用默认协议？</span><span class="sxs-lookup"><span data-stu-id="1038e-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="1038e-186">如何克隆或删除 CIM 会话？</span><span class="sxs-lookup"><span data-stu-id="1038e-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="1038e-187">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="1038e-187">Recommended Reading</span></span>

- <span data-ttu-id="1038e-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="1038e-188">[about_WMI][]</span></span>
- <span data-ttu-id="1038e-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="1038e-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="1038e-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="1038e-190">[about_WQL][]</span></span>
- <span data-ttu-id="1038e-191">[CimCmdlet 模块][]</span><span class="sxs-lookup"><span data-stu-id="1038e-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="1038e-192">[视频：使用 CIM Cmdlet 和 CIM 会话][]</span><span class="sxs-lookup"><span data-stu-id="1038e-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlet 模块]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[视频：使用 CIM Cmdlet 和 CIM 会话]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[用于在远程计算机上创建 CimSession 并将其回退到 Dcom 的 PowerShell 函数]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
