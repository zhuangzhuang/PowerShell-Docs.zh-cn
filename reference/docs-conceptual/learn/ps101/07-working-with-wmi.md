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
# <a name="chapter-7---working-with-wmi"></a>第 7 章 - 使用 WMI

## <a name="wmi-and-cim"></a>WMI 和 CIM

默认情况下，PowerShell 附带可处理 Windows Management Instrumentation (WMI) 等其他技术的 cmdlet。 PowerShell 中存在多个本机 WMI cmdlet，且无需安装任何其他软件或模块。

从一开始，PowerShell 就具有可处理 WMI 的 cmdlet。 `Get-Command` 可用于确定 PowerShell 中存在哪些 WMI cmdlet。 以下结果来自运行 5.1 版 PowerShell 的 Windows 10 实验环境计算机。 结果因运行的 PowerShell 版本而异。

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

PowerShell 版本 3.0 中引入了通用信息模型 (CIM) cmdlet。 CIM cmdlet 的设计目的是使其可以同时在 Windows 和非 Windows 计算机上使用。 由于 WMI cmdlet 已弃用，因此建议使用 CIM cmdlet 代替 WMI cmdlet。

所有 CIM cmdlet 都包含在一个模块中。 若要获取 CIM cmdlet 的列表，请结合使用 `Get-Command` 与 Module 参数，如以下示例中所示。

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

如果使用 CIM cmdlet，仍可使用 WMI，因此当有人说出“当我使用 PowerShell CIM cmdlet 查询 WMI 时...”这样的话时，请不要感到疑惑

如前所述，WMI 是一项独立于 PowerShell 的技术，现在不过是使用 CIM cmdlet 来访问 WMI 而已。 你可能会发现一个旧的 VBScript，它使用 WMI 查询语言 (WQL) 来查询 WMI，如以下示例所示。

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

可以从该 VBScript 中获取 WQL 查询，并将其与 `Get-CimInstance` cmdlet 一起使用，而无需进行任何修改。

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

这并不是我使用 PowerShell 查询 WMI 的常用方式。 但是该方法确实有效，通过该方法，可以轻松地将现有 VBScript 迁移到 PowerShell。 当我开始编写用于查询 WMI 的单项时，我使用以下语法。

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

如果只需要序列号，则可以通过管道将输出传递给 `Select-Object` 并仅指定 SerialNumber 属性。

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

默认情况下，系统会在后台检索一些从不使用的属性。
在本地计算机上查询 WMI 时，这可能不会产生什么影响。 但是，如果开始查询远程计算机，前述检索不仅要花费更多的处理时间来返回相关信息，还会在网络中拉取不必要的额外信息。 `Get-CimInstance` 有一个可以限制检索到的信息的 Property 参数。 这会提升 WMI 查询的效率。

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

之前的结果返回了一个对象。 若要返回简单字符串，请使用 ExpandProperty 参数。

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

也可以使用点式语法返回简单字符串。 这样就无需通过管道传递到 `Select-Object`。

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>使用 CIM cmdlet 查询远程计算机

我仍以作为域用户的本地管理员身份运行 PowerShell。 当我尝试使用 `Get-CimInstance` cmdlet 从远程计算机查询信息时，我收到一条“拒绝访问”的错误消息。

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

在谈到 PowerShell 时，很多人都担心安全性，但事实是，你在 PowerShell 中拥有与在 GUI 中完全相同的权限。 不多不少刚刚好。 上一个示例中的问题是，运行 PowerShell 的用户不具有通过 DC01 服务器查询 WMI 信息的权限。 由于 `Get-CimInstance` 没有 Credential 参数，我能够以域管理员的身份重启 PowerShell。 但请相信我，这不是一个好主意，因为从 PowerShell 中运行的所有内容都将以域管理员身份运行。从安全性的角度来看，这可能并不安全，这取决于具体情况。

基于最低特权原则，在每个命令的基础上，我使用 Credential 参数（如果命令包含该参数）提升到我的域管理员帐户。 `Get-CimInstance` 没有 Credential 参数，因此在这种情况下，解决方案是先创建一个 CimSession 。 然后，使用 CimSession（而不是计算机名）查询远程计算机上的 WMI。

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

CIM 会话存储在名为 `$CimSession` 的变量中。 请注意，我还在括号中指定了 `Get-Credential` cmdlet，以便在创建新会话之前先执行该 cmdlet，提示我输入备用凭据。 本章的后面部分将介绍另一种更为有效的方式来指定备用凭据，但在深入介绍相关概念及更复杂的内容之前，请务必先了解这一基本概念。

现在可以将上一个示例中创建的 CIM 会话与 `Get-CimInstance` cmdlet 一起使用，从远程计算机上的 WMI 查询 BIOS 信息。

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

使用 CIM 会话还有其他好处，而不仅仅是指定计算机名。 在同一台计算机上运行多个查询时，为每个查询使用 CIM 会话比使用计算机名更有效。 创建 CIM 会话时只需建立一次连接。
然后，多个查询使用此同一会话检索信息。 如果使用计算机名，cmdlet 需要建立和断开与每个查询的连接。

`Get-CimInstance` cmdlet 默认使用 WSMan 协议，这意味着远程计算机需要 PowerShell 3.0 或更高版本才能进行连接。 实际上，PowerShell 版本并不那么重要，重要的是堆栈版本。 可以使用 `Test-WSMan` cmdlet 确定堆栈版本。
堆栈版本需为 3.0。 PowerShell 3.0 及更高版本提供该版本的堆栈。

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

较旧的 WMI cmdlet 使用 DCOM 协议，该协议与较低版本的 Windows 兼容。 而较新 Windows 版本上的防火墙通常会阻止 DCOM。 可使用 `New-CimSessionOption` cmdlet 创建可与 `New-CimSession` 一起使用的 DCOM 协议连接。 这样便可使用 `Get-CimInstance` cmdlet 与低至 Windows Server 2000 的 Windows 版本进行通信。 这也意味着，将 `Get-CimInstance` cmdlet 与配置为使用 DCOM 协议的 CimSession 一起使用时，远程计算机上不需要 PowerShell。

使用 `New-CimSessionOption` cmdlet 创建 DCOM 协议选项，并将其存储在变量中。

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

为了提高效率，可以将域管理员凭据或提升的凭据存储在变量中，这样就不必一直为每个命令输入这些信息。

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

我有一台名为 SQL03 的服务器，该服务器运行 Windows Server 2008（非 R2）。 它是默认情况下未安装 PowerShell 的最新 Windows Server 操作系统。

使用 DCOM 协议在 SQL03 上创建 CimSession。

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

请注意，在上一条命令中，我将名为 `$Cred` 的变量指定为 Credential 参数的值，这样就不必再次手动输入这些值。

无论使用哪种基础协议，查询的输出都是相同的。

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

`Get-CimSession` cmdlet 用于查看当前连接的 CimSessions 及其正在使用的协议。

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

检索两个先前创建的 CimSession 并将其存储在名为 `$CimSession` 的变量中。

```powershell
$CimSession = Get-CimSession
```

使用一个命令同时查询这两台计算机，它们分别使用 WSMan 协议和 DCOM。

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

我写了许多有关 WMI 和 CIM cmdlet 的博客文章。 其中最有用的一篇文章与我创建的一个函数有关，该函数自动确定应使用 WSMan 还是 DCOM 并自动设置 CIM 会话，而无需手动查找是哪一个。 该博客文章的标题为[用于在远程计算机上创建 CimSession 并将其回退到 Dcom 的 PowerShell 函数][]。

完成 CIM 会话后，应使用 `Remove-CimSession` cmdlet 将其删除。 要删除所有 CIM 会话，只需通过管道将 `Get-CimSession` 传递到 `Remove-CimSession`。

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>总结

在本章中，你了解了如何通过 PowerShell 在本地和远程计算机上使用 WMI。 你还了解了如何使用 CIM cmdlet 分别处理具有 WSMan 和 DCOM 协议的远程计算机。

## <a name="review"></a>审阅

1. WMI 和 CIM cmdlet 有何区别？
1. 默认情况下，`Get-CimInstance` cmdlet 使用哪种协议？
1. 使用 CIM 会话而不使用 `Get-CimInstance` 指定计算机名有哪些好处？
1. 如何指定与 `Get-CimInstance` 一起使用的备用协议而不使用默认协议？
1. 如何克隆或删除 CIM 会话？

## <a name="recommended-reading"></a>推荐阅读的主题

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlet 模块][]
- [视频：使用 CIM Cmdlet 和 CIM 会话][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlet 模块]: /powershell/module/cimcmdlets/
[视频：使用 CIM Cmdlet 和 CIM 会话]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[用于在远程计算机上创建 CimSession 并将其回退到 Dcom 的 PowerShell 函数]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
