---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: af8a953536bb9683ba737522ad738348c5c695e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597674"
---
# <span data-ttu-id="a5258-102">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="a5258-102">Test-Connection</span></span>

## <span data-ttu-id="a5258-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a5258-103">SYNOPSIS</span></span>
<span data-ttu-id="a5258-104">将 ICMP 回显请求数据包或 ping 发送到一台或多台计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-104">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="a5258-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a5258-105">SYNTAX</span></span>

### <span data-ttu-id="a5258-106">DefaultPing (默认值) </span><span class="sxs-lookup"><span data-stu-id="a5258-106">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="a5258-107">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="a5258-107">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="a5258-108">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="a5258-108">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="a5258-109">TraceRoute</span><span class="sxs-lookup"><span data-stu-id="a5258-109">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="a5258-110">TcpPort</span><span class="sxs-lookup"><span data-stu-id="a5258-110">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="a5258-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a5258-111">DESCRIPTION</span></span>

<span data-ttu-id="a5258-112">`Test-Connection`Cmdlet 将 Internet 控制消息协议 () ICMP 发送到一台或多台远程计算机并返回回显响应回复。</span><span class="sxs-lookup"><span data-stu-id="a5258-112">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="a5258-113">可以使用此 cmdlet 来确定是否可以通过 IP 网络联系特定的计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-113">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="a5258-114">您可以使用的参数 `Test-Connection` 同时指定发送计算机和接收计算机，将该命令作为后台作业运行，设置超时和 ping 数目，以及配置连接和身份验证。</span><span class="sxs-lookup"><span data-stu-id="a5258-114">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="a5258-115">与熟悉的 **ping** 命令不同， `Test-Connection` 返回可以在 PowerShell 中调查的 **TestConnectionCommand + PingStatus** 对象。</span><span class="sxs-lookup"><span data-stu-id="a5258-115">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="a5258-116">**Quiet** 参数为每个已测试的连接返回 **system.object** 对象中的 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="a5258-116">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="a5258-117">如果测试了多个连接，则返回 **布尔** 值的数组。</span><span class="sxs-lookup"><span data-stu-id="a5258-117">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="a5258-118">示例</span><span class="sxs-lookup"><span data-stu-id="a5258-118">EXAMPLES</span></span>

### <span data-ttu-id="a5258-119">示例1：向远程计算机发送回显请求</span><span class="sxs-lookup"><span data-stu-id="a5258-119">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="a5258-120">此示例将来自本地计算机的回显请求数据包发送到 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-120">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

<span data-ttu-id="a5258-121">`Test-Connection` 使用 **TargetName** 参数指定 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-121">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="a5258-122">**IPv4** 参数指定测试的协议。</span><span class="sxs-lookup"><span data-stu-id="a5258-122">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="a5258-123">一系列 **TestConnectionCommand + PingStatus** 对象将发送到输出流，来自目标计算机的每个 ping 回复一个对象。</span><span class="sxs-lookup"><span data-stu-id="a5258-123">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="a5258-124">示例2：将回显请求发送到多台计算机</span><span class="sxs-lookup"><span data-stu-id="a5258-124">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="a5258-125">此示例将来自本地计算机的 ping 发送到多台远程计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-125">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="a5258-126">示例3：使用参数自定义测试命令</span><span class="sxs-lookup"><span data-stu-id="a5258-126">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="a5258-127">此示例使用的参数 `Test-Connection` 自定义命令。</span><span class="sxs-lookup"><span data-stu-id="a5258-127">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="a5258-128">本地计算机将 ping 测试发送到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-128">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="a5258-129">`Test-Connection` 使用 **TargetName** 参数指定 Server01。</span><span class="sxs-lookup"><span data-stu-id="a5258-129">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="a5258-130">**Count** 参数指定三个 ping 发送到 Server01 计算机，**延迟** 为2秒的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="a5258-130">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="a5258-131">当 ping 响应预计需要比平时更长的时间（因为有扩展的跃点数或高流量网络条件）时，可以使用这些选项。</span><span class="sxs-lookup"><span data-stu-id="a5258-131">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="a5258-132">示例4：将测试作为后台作业运行</span><span class="sxs-lookup"><span data-stu-id="a5258-132">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="a5258-133">此示例演示如何将 `Test-Connection` 命令作为 PowerShell 后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="a5258-133">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="a5258-134">该 `Start-Job` 命令使用 `Test-Connection` cmdlet 对企业中的多台计算机执行 ping 操作。</span><span class="sxs-lookup"><span data-stu-id="a5258-134">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="a5258-135">**TargetName** 参数的值是一个 `Get-Content` 命令，该命令从文件中读取计算机名称的列表 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="a5258-135">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="a5258-136">该命令使用 `Start-Job` cmdlet 将命令作为后台作业运行，并将作业保存在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a5258-136">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="a5258-137">在 `Receive-Job` `-Wait` 作业完成之前指示命令完成，然后获取结果并将其存储在 `$Results` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a5258-137">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="a5258-138">示例5：仅在连接测试成功时创建会话</span><span class="sxs-lookup"><span data-stu-id="a5258-138">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="a5258-139">仅当至少一个发送到计算机的 ping 成功时，此示例才会在 Server01 计算机上创建一个会话。</span><span class="sxs-lookup"><span data-stu-id="a5258-139">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="a5258-140">Cmdlet 会对 `Test-Connection` `Server01` 计算机进行 ping 操作，并提供 **Quiet** 参数。</span><span class="sxs-lookup"><span data-stu-id="a5258-140">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="a5258-141">`$True`如果四个 ping 中有任何一个成功，则生成的值为。</span><span class="sxs-lookup"><span data-stu-id="a5258-141">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="a5258-142">如果没有任何 ping 成功，则该值为 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="a5258-142">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="a5258-143">如果 `Test-Connection` 命令返回的值 `$True` ，则该命令将使用 `New-PSSession` cmdlet 创建 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="a5258-143">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="a5258-144">示例6：使用 Traceroute 参数</span><span class="sxs-lookup"><span data-stu-id="a5258-144">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="a5258-145">**Traceroute** 参数是在 PowerShell 6.0 中引入的，它在本地计算机与你指定的远程目标与 **TargetName** 参数之间映射路由。</span><span class="sxs-lookup"><span data-stu-id="a5258-145">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

<span data-ttu-id="a5258-146">`Test-Connection`命令是通过 **Traceroute** 参数调用的。</span><span class="sxs-lookup"><span data-stu-id="a5258-146">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="a5258-147">结果（是 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` 对象）将输出到 **成功** 输出流中。</span><span class="sxs-lookup"><span data-stu-id="a5258-147">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="a5258-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a5258-148">PARAMETERS</span></span>

### <span data-ttu-id="a5258-149">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="a5258-149">-BufferSize</span></span>

<span data-ttu-id="a5258-150">指定使用此命令发送的缓冲区的大小，以字节为单位。</span><span class="sxs-lookup"><span data-stu-id="a5258-150">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="a5258-151">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="a5258-151">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-152">-重复</span><span class="sxs-lookup"><span data-stu-id="a5258-152">-Repeat</span></span>

<span data-ttu-id="a5258-153">使 cmdlet 持续发送 ping 请求。</span><span class="sxs-lookup"><span data-stu-id="a5258-153">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="a5258-154">此参数不能与 **Count** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="a5258-154">This parameter can't be used with the **Count** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-155">-Count</span><span class="sxs-lookup"><span data-stu-id="a5258-155">-Count</span></span>

<span data-ttu-id="a5258-156">指定要发送的回显请求数。</span><span class="sxs-lookup"><span data-stu-id="a5258-156">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="a5258-157">默认值为 4。</span><span class="sxs-lookup"><span data-stu-id="a5258-157">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-158">-Delay</span><span class="sxs-lookup"><span data-stu-id="a5258-158">-Delay</span></span>

<span data-ttu-id="a5258-159">指定两次 ping 操作之间的间隔时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="a5258-159">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-160">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="a5258-160">-DontFragment</span></span>

<span data-ttu-id="a5258-161">此参数设置 IP 标头中的 " **不分段** " 标志。</span><span class="sxs-lookup"><span data-stu-id="a5258-161">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="a5258-162">可以将此参数与 **BufferSize** 参数一起使用来测试路径 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="a5258-162">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="a5258-163">有关路径 MTU 的详细信息，请参阅维基百科中的 [PATH Mtu 发现](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="a5258-163">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-164">-IPv4</span><span class="sxs-lookup"><span data-stu-id="a5258-164">-IPv4</span></span>

<span data-ttu-id="a5258-165">强制 cmdlet 使用 IPv4 协议进行测试。</span><span class="sxs-lookup"><span data-stu-id="a5258-165">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-166">-IPv6</span><span class="sxs-lookup"><span data-stu-id="a5258-166">-IPv6</span></span>

<span data-ttu-id="a5258-167">强制 cmdlet 使用 IPv6 协议进行测试。</span><span class="sxs-lookup"><span data-stu-id="a5258-167">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-168">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="a5258-168">-MaxHops</span></span>

<span data-ttu-id="a5258-169">设置可发送 ICMP 请求消息的最大跃点数。</span><span class="sxs-lookup"><span data-stu-id="a5258-169">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="a5258-170">默认值由操作系统控制。</span><span class="sxs-lookup"><span data-stu-id="a5258-170">The default value is controlled by the operating system.</span></span> <span data-ttu-id="a5258-171">Windows 10 的默认值为128跃点。</span><span class="sxs-lookup"><span data-stu-id="a5258-171">The default value for Windows 10 is 128 hops.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-172">-Ping</span><span class="sxs-lookup"><span data-stu-id="a5258-172">-Ping</span></span>

<span data-ttu-id="a5258-173">导致 cmdlet 执行 ping 测试。</span><span class="sxs-lookup"><span data-stu-id="a5258-173">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="a5258-174">这是 cmdlet 的默认模式 `Test-Connection` 。</span><span class="sxs-lookup"><span data-stu-id="a5258-174">This is the default mode for the `Test-Connection` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-175">-Quiet</span><span class="sxs-lookup"><span data-stu-id="a5258-175">-Quiet</span></span>

<span data-ttu-id="a5258-176">**Quiet** 参数将返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="a5258-176">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="a5258-177">使用此参数将取消所有错误。</span><span class="sxs-lookup"><span data-stu-id="a5258-177">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="a5258-178">所测试的每个连接都将返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="a5258-178">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="a5258-179">如果 **TargetName** 参数指定了多台计算机，则返回 **布尔** 值的数组。</span><span class="sxs-lookup"><span data-stu-id="a5258-179">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="a5258-180">如果对给定目标的 **任何** ping 操作成功， `$True` 则返回。</span><span class="sxs-lookup"><span data-stu-id="a5258-180">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="a5258-181">如果对给定目标的 **所有** ping `$False` 操作都失败，则返回。</span><span class="sxs-lookup"><span data-stu-id="a5258-181">If **all** pings to a given target fail, `$False` is returned.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-182">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="a5258-182">-ResolveDestination</span></span>

<span data-ttu-id="a5258-183">导致 cmdlet 尝试解析目标的 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="a5258-183">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="a5258-184">当与 **Traceroute** 参数结合使用时，还将检索所有中间主机的 DNS 名称（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="a5258-184">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-185">-Source</span><span class="sxs-lookup"><span data-stu-id="a5258-185">-Source</span></span>

<span data-ttu-id="a5258-186">指定发出 ping 请求的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="a5258-186">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="a5258-187">请输入以逗号分隔的计算机名称的列表。</span><span class="sxs-lookup"><span data-stu-id="a5258-187">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="a5258-188">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="a5258-188">The default is the local computer.</span></span>

<span data-ttu-id="a5258-189">**注意：** 此参数在 PowerShell 版本6和更高版本中不起作用。</span><span class="sxs-lookup"><span data-stu-id="a5258-189">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="a5258-190">提供此参数不会对命令产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="a5258-190">Supplying this parameter will have no effect on the command.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-191">-TargetName</span><span class="sxs-lookup"><span data-stu-id="a5258-191">-TargetName</span></span>

<span data-ttu-id="a5258-192">指定要测试的计算机 () 。</span><span class="sxs-lookup"><span data-stu-id="a5258-192">Specifies the computer(s) to test.</span></span> <span data-ttu-id="a5258-193">请键入计算机名称或者以 IPv4 或 IPv6 格式键入 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a5258-193">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-194">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="a5258-194">-TimeoutSeconds</span></span>

<span data-ttu-id="a5258-195">设置测试的超时值。</span><span class="sxs-lookup"><span data-stu-id="a5258-195">Sets the timeout value for the test.</span></span> <span data-ttu-id="a5258-196">如果在超时过期之前未收到响应，则测试失败。</span><span class="sxs-lookup"><span data-stu-id="a5258-196">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="a5258-197">默认值为 5 秒。</span><span class="sxs-lookup"><span data-stu-id="a5258-197">The default is five seconds.</span></span>

<span data-ttu-id="a5258-198">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a5258-198">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-199">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="a5258-199">-Traceroute</span></span>

<span data-ttu-id="a5258-200">导致 cmdlet 执行 traceroute 测试。</span><span class="sxs-lookup"><span data-stu-id="a5258-200">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="a5258-201">使用此参数时，该 cmdlet 将返回一个 `TestConnectionCommand+TraceStatus` 对象。</span><span class="sxs-lookup"><span data-stu-id="a5258-201">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-202">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="a5258-202">-MtuSize</span></span>

<span data-ttu-id="a5258-203">此参数用于发现路径 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="a5258-203">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="a5258-204">Cmdlet 将返回 **PingReply # MTUSize** 对象，其中包含目标的路径 MTU 大小。</span><span class="sxs-lookup"><span data-stu-id="a5258-204">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="a5258-205">有关路径 MTU 的详细信息，请参阅维基百科中的 [PATH Mtu 发现](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。</span><span class="sxs-lookup"><span data-stu-id="a5258-205">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-206">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="a5258-206">-TcpPort</span></span>

<span data-ttu-id="a5258-207">指定要在 TCP 连接测试中使用的目标上的 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="a5258-207">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="a5258-208">Cmdlet 将尝试与目标上的指定端口建立 TCP 连接。</span><span class="sxs-lookup"><span data-stu-id="a5258-208">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="a5258-209">如果可以建立连接， `$True` 则将返回。</span><span class="sxs-lookup"><span data-stu-id="a5258-209">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="a5258-210">如果无法建立连接， `$False` 则将返回。</span><span class="sxs-lookup"><span data-stu-id="a5258-210">If a connection cannot be made, `$False` will be returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a5258-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a5258-211">CommonParameters</span></span>

<span data-ttu-id="a5258-212">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a5258-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a5258-213">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a5258-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a5258-214">输入</span><span class="sxs-lookup"><span data-stu-id="a5258-214">INPUTS</span></span>

### <span data-ttu-id="a5258-215">无</span><span class="sxs-lookup"><span data-stu-id="a5258-215">None</span></span>

<span data-ttu-id="a5258-216">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a5258-216">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a5258-217">输出</span><span class="sxs-lookup"><span data-stu-id="a5258-217">OUTPUTS</span></span>

### <span data-ttu-id="a5258-218">TestConnectionCommand + PingStatus、TestConnectionCommand + TraceStatus、Boolean、TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="a5258-218">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="a5258-219">默认情况下， `Test-Connection` 将为每个 ping 答复返回一个 **TestConnectionCommand + PingStatus** 对象。</span><span class="sxs-lookup"><span data-stu-id="a5258-219">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="a5258-220">如果指定 **Traceroute** 参数，则该 cmdlet 将为沿路由的每个 ping 答复返回 **TestConnectionCommand + TraceStatus** 对象。</span><span class="sxs-lookup"><span data-stu-id="a5258-220">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="a5258-221">如果指定 **Quiet** 或 **TcpPort** 参数，则将返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="a5258-221">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="a5258-222">如果测试了多个连接，则返回 **布尔** 值的数组。</span><span class="sxs-lookup"><span data-stu-id="a5258-222">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="a5258-223">注释</span><span class="sxs-lookup"><span data-stu-id="a5258-223">NOTES</span></span>

## <span data-ttu-id="a5258-224">相关链接</span><span class="sxs-lookup"><span data-stu-id="a5258-224">RELATED LINKS</span></span>

[<span data-ttu-id="a5258-225">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="a5258-225">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="a5258-226">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="a5258-226">Stop-Computer</span></span>](Stop-Computer.md)

