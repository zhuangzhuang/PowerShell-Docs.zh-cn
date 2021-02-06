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
# Test-Connection

## 摘要
将 ICMP 回显请求数据包或 ping 发送到一台或多台计算机。

## SYNTAX

### DefaultPing (默认值) 

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### RepeatPing

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TraceRoute

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## DESCRIPTION

`Test-Connection`Cmdlet 将 Internet 控制消息协议 () ICMP 发送到一台或多台远程计算机并返回回显响应回复。 可以使用此 cmdlet 来确定是否可以通过 IP 网络联系特定的计算机。

您可以使用的参数 `Test-Connection` 同时指定发送计算机和接收计算机，将该命令作为后台作业运行，设置超时和 ping 数目，以及配置连接和身份验证。

与熟悉的 **ping** 命令不同， `Test-Connection` 返回可以在 PowerShell 中调查的 **TestConnectionCommand + PingStatus** 对象。 **Quiet** 参数为每个已测试的连接返回 **system.object** 对象中的 **布尔** 值。 如果测试了多个连接，则返回 **布尔** 值的数组。

## 示例

### 示例1：向远程计算机发送回显请求

此示例将来自本地计算机的回显请求数据包发送到 Server01 计算机。

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

`Test-Connection` 使用 **TargetName** 参数指定 Server01 计算机。 **IPv4** 参数指定测试的协议。

一系列 **TestConnectionCommand + PingStatus** 对象将发送到输出流，来自目标计算机的每个 ping 回复一个对象。

### 示例2：将回显请求发送到多台计算机

此示例将来自本地计算机的 ping 发送到多台远程计算机。

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### 示例3：使用参数自定义测试命令

此示例使用的参数 `Test-Connection` 自定义命令。 本地计算机将 ping 测试发送到远程计算机。

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` 使用 **TargetName** 参数指定 Server01。 **Count** 参数指定三个 ping 发送到 Server01 计算机，**延迟** 为2秒的时间间隔。

当 ping 响应预计需要比平时更长的时间（因为有扩展的跃点数或高流量网络条件）时，可以使用这些选项。

### 示例4：将测试作为后台作业运行

此示例演示如何将 `Test-Connection` 命令作为 PowerShell 后台作业运行。

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

该 `Start-Job` 命令使用 `Test-Connection` cmdlet 对企业中的多台计算机执行 ping 操作。
**TargetName** 参数的值是一个 `Get-Content` 命令，该命令从文件中读取计算机名称的列表 `Servers.txt` 。 该命令使用 `Start-Job` cmdlet 将命令作为后台作业运行，并将作业保存在 `$job` 变量中。

在 `Receive-Job` `-Wait` 作业完成之前指示命令完成，然后获取结果并将其存储在 `$Results` 变量中。

### 示例5：仅在连接测试成功时创建会话

仅当至少一个发送到计算机的 ping 成功时，此示例才会在 Server01 计算机上创建一个会话。

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

Cmdlet 会对 `Test-Connection` `Server01` 计算机进行 ping 操作，并提供 **Quiet** 参数。
`$True`如果四个 ping 中有任何一个成功，则生成的值为。 如果没有任何 ping 成功，则该值为 `$False` 。

如果 `Test-Connection` 命令返回的值 `$True` ，则该命令将使用 `New-PSSession` cmdlet 创建 **PSSession**。

### 示例6：使用 Traceroute 参数

**Traceroute** 参数是在 PowerShell 6.0 中引入的，它在本地计算机与你指定的远程目标与 **TargetName** 参数之间映射路由。

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

`Test-Connection`命令是通过 **Traceroute** 参数调用的。 结果（是 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` 对象）将输出到 **成功** 输出流中。

## PARAMETERS

### -BufferSize

指定使用此命令发送的缓冲区的大小，以字节为单位。 默认值为 32。

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

### -重复

使 cmdlet 持续发送 ping 请求。 此参数不能与 **Count** 参数一起使用。

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

### -Count

指定要发送的回显请求数。 默认值为 4。

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

### -Delay

指定两次 ping 操作之间的间隔时间，以秒为单位。

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

### -DontFragment

此参数设置 IP 标头中的 " **不分段** " 标志。 可以将此参数与 **BufferSize** 参数一起使用来测试路径 MTU 大小。 有关路径 MTU 的详细信息，请参阅维基百科中的 [PATH Mtu 发现](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。

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

### -IPv4

强制 cmdlet 使用 IPv4 协议进行测试。

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

### -IPv6

强制 cmdlet 使用 IPv6 协议进行测试。

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

### -MaxHops

设置可发送 ICMP 请求消息的最大跃点数。 默认值由操作系统控制。 Windows 10 的默认值为128跃点。

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

### -Ping

导致 cmdlet 执行 ping 测试。 这是 cmdlet 的默认模式 `Test-Connection` 。

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

### -Quiet

**Quiet** 参数将返回一个 **布尔** 值。 使用此参数将取消所有错误。

所测试的每个连接都将返回一个 **布尔** 值。 如果 **TargetName** 参数指定了多台计算机，则返回 **布尔** 值的数组。

如果对给定目标的 **任何** ping 操作成功， `$True` 则返回。

如果对给定目标的 **所有** ping `$False` 操作都失败，则返回。

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

### -ResolveDestination

导致 cmdlet 尝试解析目标的 DNS 名称。 当与 **Traceroute** 参数结合使用时，还将检索所有中间主机的 DNS 名称（如果可能）。

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

### -Source

指定发出 ping 请求的计算机的名称。 请输入以逗号分隔的计算机名称的列表。 默认为本地计算机。

**注意：** 此参数在 PowerShell 版本6和更高版本中不起作用。
提供此参数不会对命令产生任何影响。

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

### -TargetName

指定要测试的计算机 () 。 请键入计算机名称或者以 IPv4 或 IPv6 格式键入 IP 地址。

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

### -TimeoutSeconds

设置测试的超时值。 如果在超时过期之前未收到响应，则测试失败。 默认值为 5 秒。

此参数是在 PowerShell 6.0 中引入的。

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

### -Traceroute

导致 cmdlet 执行 traceroute 测试。 使用此参数时，该 cmdlet 将返回一个 `TestConnectionCommand+TraceStatus` 对象。

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

### -MtuSize

此参数用于发现路径 MTU 大小。 Cmdlet 将返回 **PingReply # MTUSize** 对象，其中包含目标的路径 MTU 大小。 有关路径 MTU 的详细信息，请参阅维基百科中的 [PATH Mtu 发现](https://wikipedia.org/wiki/Path_MTU_Discovery) 文章。

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

### -TcpPort

指定要在 TCP 连接测试中使用的目标上的 TCP 端口号。 Cmdlet 将尝试与目标上的指定端口建立 TCP 连接。

如果可以建立连接， `$True` 则将返回。

如果无法建立连接， `$False` 则将返回。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### TestConnectionCommand + PingStatus、TestConnectionCommand + TraceStatus、Boolean、TestConnectionCommand + PingMtuStatus

默认情况下， `Test-Connection` 将为每个 ping 答复返回一个 **TestConnectionCommand + PingStatus** 对象。

如果指定 **Traceroute** 参数，则该 cmdlet 将为沿路由的每个 ping 答复返回 **TestConnectionCommand + TraceStatus** 对象。

如果指定 **Quiet** 或 **TcpPort** 参数，则将返回一个 **布尔** 值。 如果测试了多个连接，则返回 **布尔** 值的数组。

## 注释

## 相关链接

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)

