---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: b87db1af49ae293225f417fd4bec85e346c79f28
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597033"
---
# Disconnect-PSSession

## 摘要
断开与会话的连接。

## SYNTAX

### 会话（默认）

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 名称

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ID

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Disconnect-PSSession`Cmdlet `New-PSSession` 从当前会话将 PowerShell 会话 ( "PSSession" ) （如使用 cmdlet 启动的会话）断开连接。 因此，PSSession 将处于已断开连接状态。 可以从当前会话或者本地计算机或另一台计算机上的另一个会话连接已断开的 PSSession。

该 `Disconnect-PSSession` cmdlet 仅断开连接到当前会话的打开的 pssession。 `Disconnect-PSSession` 无法断开中断或关闭的 Pssession 或使用 cmdlet 启动的交互式 Pssession，也 `Enter-PSSession` 无法断开连接到其他会话的 pssession。

若要重新连接到已断开连接的 PSSession，请使用 `Connect-PSSession` 或 `Receive-PSSession` cmdlet。

当断开与 PSSession 的连接时，PSSession 中的命令将继续运行直到完成，除非 PSSession 超时或完整输出缓冲区阻止了 PSSession 中的命令。 若要更改空闲超时，请使用 **IdleTimeoutSec** 参数。 若要更改输出缓冲模式，请使用 **OutputBufferingMode** 参数，还可以使用 Cmdlet 的 **InDisconnectedSession** 参数 `Invoke-Command` 在断开连接的会话中运行命令。

有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例 1-按名称断开会话连接

此命令将断开 Server01 计算机上的 UpdateSession PSSession 与当前会话的连接。 该命令使用 **Name** 参数来标识 PSSession。

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

输出显示断开连接的尝试已成功。 会话状态为 Disconnected，可用性为 None，它表示会话不处于忙碌状态，可以重新连接该回话。

### 示例 2-从特定计算机断开会话连接

此命令将断开 Server12 计算机上的 ITTask PSSession 与当前会话的连接。
在当前会话中创建 ITTask 会话并将其连接到 Server12 计算机。 该命令使用 `Get-PSSession` cmdlet 来获取会话，并使用 `Disconnect-PSSession` cmdlet 断开连接。

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

该 `Disconnect-PSSession` 命令使用 **OutputBufferingMode** 参数将输出模式设置为 **Drop**。 此设置确保会话中运行的脚本可以继续运行，即使会话输出缓冲区已满也是如此。 因为该脚本将其输出写入文件共享上的报告，所以其他输出可能在不产生后果的情况下丢失。

该命令还使用 **IdleTimeoutSec** 参数来将会话的空闲超时扩展到 24 小时。 此设置为此管理员或其他管理员重新连接到会话，以验证脚本是否已运行和解决问题（如果需要）提供了时间。

### 示例 3-在多台计算机上使用多个 Pssession

这一系列命令显示了如何 `Disconnect-PSSession` 在企业方案中使用 cmdlet。 在这种情况下，新的技术人员在远程计算机上的会话中启动一个脚本并遇到了问题。 该技术人员将断开到该会话的连接，以便更有经验的经理可以连接到该会话并解决该问题。

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

该技术人员首先在多台远程计算机上创建会话并在每个会话中运行脚本。 第一个命令使用 `New-PSSession` cmdlet 在三台远程计算机上创建 ITTask 会话。 该命令将会话保存在 $s 变量中。 第二个命令使用 cmdlet 的 **FilePath** 参数在 `Invoke-Command` $s 变量的会话中运行脚本。

在 Srv1 计算机上运行的脚本生成了意外的错误。 技术人员联系经理并请求协助。 经理指示技术人员断开与会话的连接，以便他可以进行调查。第二个命令使用 `Get-PSSession` cmdlet 来获取 Srv1 计算机上的 ITTask 会话，并使用 `Disconnect-PSSession` cmdlet 断开它的连接。 此命令不会影响其他计算机上的 ITTask 会话。

第三个命令使用 `Get-PSSession` cmdlet 来获取 ITTask 会话。 输出显示 Srv2 和 Srv30 计算机上的 ITTask 会话并未受用于断开连接的命令的影响。

管理器登录到他的家庭计算机，连接到其公司网络，启动 PowerShell，并使用 `Get-PSSession` cmdlet 来获取 Srv1 计算机上的 ITTask 会话。 他使用技术人员的凭据来访问该会话。

接下来，管理器使用 `Connect-PSSession` cmdlet 连接到 Srv1 计算机上的 ITTask 会话。 该命令将该会话保存在 $s 变量中。

管理器使用 `Invoke-Command` cmdlet 在变量中的会话中运行一些诊断命令 `$s` 。 他认识到脚本失败是因为脚本找不到所需目录。
管理器使用 `MkDir` 函数创建目录，然后重新启动 `Get-PatchStatus.ps1` 脚本并断开与会话的连接。Manager 向技术人员报告他的调查结果，建议他重新连接到该会话以完成任务，并要求他向脚本添加一个命令，以 `Get-PatchStatus.ps1` 创建所需的目录（如果不存在）。

### 示例 4-更改 PSSession 的超时值

此示例演示如何更正会话的 **IdleTimeout** 属性的值，以便可以断开到它的连接。

会话的空闲超时属性对已断开连接的会话至关重要，因为它将确定在删除已断开连接的会话之前维护该会话多长时间。 当你创建会话以及断开到它的连接时，可以设置空闲超时选项。 会话空闲超时的默认值是在 `$PSSessionOption` 本地计算机上的首选项变量和远程计算机上的会话配置中设置的。 为会话设置的值优先于在会话配置中设置的值，但会话值不能超过会话配置中的配额设置，如 **MaxIdleTimeoutMs** 值。

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

第一个命令使用 `New-PSSessionOption` cmdlet 来创建会话选项对象。 它使用 **IdleTimeout** 参数将空闲超时设置为 48 小时（172800000 毫秒）。 该命令将会话选项对象保存在 $Timeout 变量中。

第二个命令使用 `New-PSSession` cmdlet 在 Server01 计算机上创建 ITTask 会话。 该命令将会话保存在 $s 变量中。 **SessionOption** 参数的值是 $Timeout 变量中的 48 小时空闲超时。

第三个命令将断开与 $s 变量中的 ITTask 会话的连接。 该命令失败是因为会话的空闲超时值超出会话配置中的 **MaxIdleTimeoutMs** 配额。 由于断开此会话之前未使用空闲超时，因此当会话在使用中时可能检测不到此超额行为。

第四个命令使用 `Invoke-Command` cmdlet `Get-PSSessionConfiguration` 在 Server01 计算机上为 Microsoft PowerShell 会话配置运行命令。 该命令使用 `Format-List` cmdlet 来显示列表中会话配置的所有属性。输出显示了 **MaxIdleTimeoutMS** 属性，该属性为使用会话配置的会话建立最大允许的 **IdleTimeout** 值43200000，)  (12 小时。

第五个命令将获取 $s 变量中的会话的会话选项值。 许多会话选项的值是会话的 **运行空间** 属性的 **ConnectionInfo** 属性的属性。此输出显示会话的 **IdleTimeout** 属性值为172800000毫秒 (48 小时) ，这违反了会话配置中的 **MaxIdleTimeoutMs** 配额（12小时）。若要解决此冲突，可以使用 **ConfigurationName** 参数来选择不同的会话配置，或使用 **IdleTimeout** 参数来减小会话的空闲超时。

第六个命令将断开到会话的连接。 该命令使用 **IdleTimeoutSec** 参数将最大空闲超时设置为 12 小时。

第七个命令将获取已断开连接的会话的 **IdleTimeout** 属性的值（以毫秒为单位）。 输出确认命令已成功。

## PARAMETERS

### -Id

断开与具有指定会话 ID 的会话的连接。 键入一个或多个 ID（以逗号分隔），或使用范围运算符 (..) 来指定 ID 的范围。

若要获取会话的 ID，请使用 `Get-PSSession` cmdlet。 将实例 ID 存储在会话的 **ID** 属性中。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

更改已断开连接的 PSSession 的空闲超时值。 输入一个值（以秒为单位）。 最小值为 60（1 分钟）。

空闲超时确定已断开连接的 PSSession 在远程计算机上保留多长时间。 当超时到期时，将删除 PSSession。

从已断开连接的 PSSession 断开连接那一刻起，就将其视为空闲，即使命令是在已断开连接的会话中运行也是如此。

会话的空闲超时默认值由会话配置的 **IdleTimeoutMs** 属性的值设置。 默认值为 7200000 毫秒（2 小时）。

此参数的值优先于 $PSSessionOption 首选项变量的 **IdleTimeout** 属性的值和会话配置中的默认空闲超时值。 但是，此值不能超过会话配置的 **MaxIdleTimeoutMs** 属性的值。 **MaxIdleTimeoutMs** 的默认值为 12 小时（43200000 毫秒）。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

断开与具有指定实例 ID 的会话的连接。

实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识某个会话。 实例 ID 是唯一的，即使在多台计算机上跨多个会话也是如此。

若要获取会话的实例 ID，请使用 `Get-PSSession` cmdlet。 实例 ID 存储在会话的 **InstanceID** 属性中。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

断开与具有指定友好名称的会话的连接。 允许使用通配符。

若要获取会话的友好名称，请使用 `Get-PSSession` cmdlet。 友好名称存储在会话的 **Name** 属性中。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

断开与指定的 PSSession 的连接。 输入 PSSession 对象，例如 cmdlet 返回的对象 `New-PSSession` 。 还可以通过管道将 PSSession 对象传递给 `Disconnect-PSSession` 。

`Get-PSSession`Cmdlet 可以获取在远程计算机上终止的所有 pssession，包括已断开连接的 pssession 和连接到其他计算机上其他会话的 pssession。 `Disconnect-PSSession` 仅断开连接到当前会话的 PSSession。 如果通过管道将其他 Pssession 传递给 `Disconnect-PSSession` ，则该 `Disconnect-PSSession` 命令将失败。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

设置命令的限制 `Disconnect-PSSession` 。

中止值为运行此命令可建立的并发连接的最大数目。 如果省略此参数或输入 0 值，则使用默认值 32。

节流限制仅适用于当前命令，而不适用于会话或计算机。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

确定输出缓冲区已满时如何在已断开连接的会话中管理命令输出。 默认值为 **Block**。

如果已断开连接的会话中的命令返回输出时输出缓冲区已满，则此参数的值将有效地确定当会话已断开连接时该命令是否继续运行。 值 **Block** 将挂起命令，直到重新连接会话。 值 **Drop** 允许命令完成，但是可能会丢失数据。 当使用 **Drop** 值时，请将命令输出重定向到磁盘上的文件。

有效值是：

- **Block**：当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。
- **Drop**：当输出缓冲区已满时，执行将继续。 由于已保存新的输出，因此将丢弃最早的输出。
- **None**：未指定任何输出缓冲模式。 会话配置的 **OutputBufferingMode** 属性的值用于已断开连接的会话。

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。

## 输入

### System.Management.Automation.Runspaces.PSSession

可以通过管道将会话传递给 `Disconnect-PSSession` 。

## 输出

### System.Management.Automation.Runspaces.PSSession

`Disconnect-PSSession` 返回一个对象，该对象表示其已断开连接的会话。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- `Disconnect-PSSession`仅当本地计算机和远程计算机运行 PowerShell 3.0 或更高版本时，此 cmdlet 才有效。
- 如果在 `Disconnect-PSSession` 断开连接的会话上使用 cmdlet，则该命令对该会话不起作用，并且不会生成错误。
- 对于具有交互式安全令牌（使用 **EnableNetworkAccess** 参数创建的安全令牌）的已断开连接的环回会话，只可以从创建该会话的计算机上重新连接该会话。 此限制可使计算机免遭恶意访问。
- 断开到 PSSession 的连接后，会话状态为 **Disconnected**，可用性为 **None**。

  **State** 属性的值是相对于当前会话的。 因此，值 **Disconnected** 意味着 PSSession 未连接到当前会话。 但是，它并不意味着 PSSession 会与所有会话断开连接。 它可能连接到另一个会话。 若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。

  **Availability** 的 **None** 值指示可连接到 PSSession。 值 **Busy** 指示你无法连接到 PSSession，因为它已连接到另一个会话。

  有关会话的 **State** 属性的值的详细信息，请参阅 [RunspaceState 枚举](/dotnet/api/system.management.automation.runspaces.runspacestate)。

  有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate 枚举](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)
