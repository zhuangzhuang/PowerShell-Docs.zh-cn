---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: d07942797bad3666a263e017fa8372e672936041
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603815"
---
# New-PSSessionOption

## 摘要
创建一个包含 PSSession 高级选项的对象。

## SYNTAX

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## DESCRIPTION

`New-PSSessionOption`Cmdlet 将创建一个对象，该对象包含用户托管会话 (**PSSession**) 的高级选项。 可以使用对象作为创建 **PSSession** 的 Cmdlet 的 **SessionOption** 参数的值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。

如果没有参数， `New-PSSessionOption` 则将生成一个对象，该对象包含所有选项的默认值。 由于所有属性都是可编辑的，因此你可以将生成的对象用作模板，并为你的企业创建标准选项对象。

你还可以将会话选项对象保存在 `$PSSessionOption` 首选项变量中。 会话选项的新的默认值由此变量的值建立。 在未为该会话设置会话选项时它们是有效的，并且优先于在会话配置中设置的选项，但可以通过在创建会话的 cmdlet 中指定会话选项或会话选项对象来替代它们。 有关 `$PSSessionOption` 首选项变量的详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

当你在创建会话的 cmdlet 中使用会话选项对象时，会话选项值将优先于在 $PSSessionOption 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 示例

### 示例1：创建默认会话选项

此命令创建具有所有默认值的会话选项对象。

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### 示例2：使用会话选项对象配置会话

此示例显示了如何使用会话选项对象来配置会话。

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

第一个命令创建一个新的会话选项对象，并将其保存在变量的值中 `$pso` 。 第二个命令使用 `New-PSSession` cmdlet 在 Server01 远程计算机上创建会话。 该命令使用变量值中的 session 选项对象 `$pso` 作为命令的 **SessionOption** 参数的值。

### 示例3：启动交互式会话

此命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 计算机的交互式会话。

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

**SessionOption** 参数的值是一个 `New-PSSessionOption` 包含 **NoEncryption** 和 **NoCompression** 参数的命令。

`New-PSSessionOption`命令括在括号中，以确保它在命令之前运行 `Enter-PSSession` 。

### 示例4：修改会话选项对象

此示例演示您可以修改 session 选项对象。 所有属性都具有读/写值。

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

使用此方法为你的企业创建标准会话对象，然后针对特定用途创建该对象的自定义版本。

### 示例5：创建首选项变量

此命令创建一个 `$PSSessionOption` 首选项变量。

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

如果 `$PSSessionOption` 会话中出现首选项变量，它将使用 `New-PSSession` 、 `Enter-PSSession` 和 cmdlet 为创建的会话中的选项建立默认值 `Invoke-Command` 。

若要使 `$PSSessionOption` 变量在所有会话中都可用，请将其添加到 powershell 会话和 powershell 配置文件。

有关 `$PSSessionOption` 首选项变量的详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。
有关配置文件的详细信息，请参阅 [about_Profiles](About/about_Profiles.md)。

### 示例6：满足远程会话配置的要求

此示例显示了如何使用 **SessionOption** 对象来满足远程会话配置的要求。

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

第一个命令使用 `New-PSSessionOption` cmdlet 创建具有 **SkipCNCheck** 属性的会话选项对象。 该命令将生成的会话对象保存在 `$skipCN` 变量中。

第二个命令使用 `New-PSSession` cmdlet 在远程计算机上创建新会话。 `$skipCN`Check 变量用于 **SessionOption** 参数的值。

由于计算机通过其 IP 地址进行标识， **ComputerName** 参数的值与用于安全套接字层 (SSL) 的证书中的任何公用名都不匹配。 因此，**SkipCNCheck** 选项是必需的。

### 示例7：使参数可用于远程会话

此示例演示如何使用 cmdlet 的 **ApplicationArguments** 参数 `New-PSSessionOption` 向远程会话提供其他数据。

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

第一个命令创建一个哈希表，其中包含两个键： " **团队** " 和 " **使用**"。 该命令将哈希表保存在 `$team` 变量中。 有关哈希表的详细信息，请参阅 [about_Hash_Tables](about/about_Hash_Tables.md)。

接下来， `New-PSSessionOption` 使用 **ApplicationArguments** 参数创建一个保存在变量中的会话选项对象 `$team` 。 当 `New-PSSessionOption` 创建会话选项对象时，它会自动将 **ApplicationArguments** 参数值中的哈希表转换为基元字典，以便可以将数据可靠地传输到远程会话。

`New-PSSession`Cmdlet 在 Server01 计算机上启动一个会话。 它使用 **SessionOption** 参数来包括变量中的选项 `$teamOption` 。

`Invoke-Command`Cmdlet 说明变量中的数据 `$team` 可用于远程会话中的命令。 数据显示在自动变量的 **ApplicationArguments** 属性中 `$PSSenderInfo` 。

最后 `Invoke-Command` 显示了如何使用数据。

## PARAMETERS

### -ApplicationArguments

指定将发送到远程会话的基元字典。 远程会话中的命令和脚本（包括会话配置中的启动脚本）可以在自动变量的 **ApplicationArguments** 属性中找到此字典 `$PSSenderInfo` 。 你可以使用此参数来将数据发送到远程会话。

有关详细信息，请参阅 [about_Hash_Tables](about/about_Hash_Tables.md)、 [about_Session_Configurations](About/about_Session_Configurations.md)和 [about_Automatic_Variables](about/about_Automatic_Variables.md)。

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

确定 PowerShell 等待取消操作 (按 CTRL + C) 完成多长时间后才结束。
输入一个值（以毫秒为单位）。

默认值为 60000（1 分钟）。 值为 0（零）表示无超时；该命令会无限期地继续运行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

指定要用于会话的区域性。 在 `<languagecode2>-<country/regioncode2>` 格式 (如 `ja-JP`) 、包含 **cultureinfo** 对象的变量或获取 **CultureInfo** 对象的命令中输入区域性名称。

默认值为 `$Null` ，并且在该会话中使用在操作系统中设置的区域性。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

确定当远程计算机没有从本地计算机接收任何通信时，会话保持打开状态的时间。 这包括检测信号信号。 当时间间隔已过时，该会话将关闭。

如果打算断开连接并重新连接到会话，则空闲超时值非常重要。 仅当该会话未超时时，才可以重新连接。

输入一个值（以毫秒为单位）。 最小值为 60000（1 分钟）。 最大值为会话配置的 **MaxIdleTimeoutms** 属性值。 默认值-1 未设置空闲超时。

会话使用在会话选项中设置的空闲超时（如果有）。 如果未设置 (-1) ，则会话将使用会话配置的 **IdleTimeoutMs** 属性的值或 WSMan shell 超时值 (`WSMan:\<ComputerName>\Shell\IdleTimeout`) ，取最短时间。

如果在会话选项中设置的空闲超时超出会话配置的 **MaxIdleTimeoutMs** 属性值，则用于创建会话的命令将失败。

**默认的** IdleTimeoutMs 会话配置的值为7200000毫秒 (2 小时) 。 其 **MaxIdleTimeoutMs** 值为2147483647毫秒 (\> 24 天) 。 WSMan shell 空闲超时 () 的默认值 `WSMan:\<ComputerName>\Shell\IdleTimeout` 为7200000毫秒， (2) 小时。

从会话断开连接或重新连接到会话时，还可以更改会话的空闲超时值。 有关详细信息，请参阅 `Disconnect-PSSession` 和 `Connect-PSSession`。

在 Windows PowerShell 2.0 中，**IdleTimeout** 参数的默认值为 240000（4 分钟）。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

将端口号包含在用于 Kerberos 身份验证的服务主体名称 (SPN) ，例如， `HTTP://<ComputerName>:5985` 。 此选项允许客户端使用非默认 SPN 对使用 Kerberos 身份验证的远程计算机进行身份验证。

该选项旨在用于为在不同的用户帐户下运行的支持 Kerberos 身份验证的多个服务的企业。 例如，允许 Kerberos 身份验证的 IIS 应用程序可能需要将默认 SPN 注册到不同于计算机帐户的用户帐户。 在这种情况下，PowerShell 远程处理无法使用 Kerberos 进行身份验证，因为它需要一个已注册到计算机帐户的 SPN。 若要解决此问题，管理员可以创建不同的 Spn，例如通过使用 **Setspn.exe** 注册到不同用户帐户，并且可以通过将端口号包含在 SPN 中来区分它们。

有关详细信息，请参阅 [Setspn 概述](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -MaxConnectionRetryCount

指定在当前尝试因网络问题而失败时，PowerShell 尝试连接到目标计算机的次数。 默认值为 5。

为 PowerShell 版本5.0 添加了此参数。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedDataSizePerCommand

指定本地计算机在单个命令中可从远程计算机接收到的最大字节数。 输入一个值（以字节为单位）。 默认情况下，没有数据大小限制。

此选项专门用于保护客户端计算机上的资源。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSize

指定本地计算机可从远程计算机接收到的最大对象大小。 此选项专门用于保护客户端计算机上的资源。 输入一个值（以字节为单位）。

在 Windows PowerShell 2.0 中，如果省略此参数，则没有对象大小限制。 从 Windows PowerShell 3.0 开始，如果省略此参数，则默认值为 200 MB。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

确定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。 默认值为 5。 值为 0（零）将阻止所有重定向。

仅当在创建会话的命令中使用 **AllowRedirection** 参数时，才会在会话中使用此选项。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCompression

关闭会话中的数据包压缩。 压缩会占用更多的处理器周期，但可以提高传输速度。

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

### -NoEncryption

关闭数据加密。

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

### -NoMachineProfile

阻止加载用户的 Windows 用户配置文件。 这样做可以加快创建会话的速度，但不能在该会话使用特定于用户的注册表设置、环境变量等项以及证书。

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

### -OpenTimeout

确定客户端计算机等待建立会话连接的时长。 当时间间隔到期时，用于建立该连接的命令将失败。 输入一个值（以毫秒为单位）。

默认值为 180000（3 分钟）。 值为 0（零）表示无超时；该命令会无限期地继续运行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

确定任一操作可在会话中运行的最长时间。 当时间间隔到期时，该操作将失败。 输入一个值（以毫秒为单位）。

默认值为 180000（3 分钟）。 值为 0（零）表示无超时；该操作会无限期地继续运行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

当输出缓冲区时已满时，确定如何在断开连接的会话中管理命令输出。

如果未在会话或会话配置中设置输出缓冲模式，则默认值为 **Block**。 用户还可以在断开会话连接时更改输出缓冲模式。

如果省略此参数，则会话选项对象的 **OutputBufferingMode** 的值为 None。 值为 **Block** 或 **Drop** 会覆盖在会话配置中设置的输出缓冲模式传输选项。 此参数的可接受值为：

- 阻止。 当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。
- 删除。 当输出缓冲区已满时，执行将继续。 由于已保存新的输出，因此将丢弃最早的输出。
- 无。 未指定任何输出缓冲模式。

有关输出缓冲模式传输选项的详细信息，请参阅 `New-PSTransportOption` 。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType

确定用于解析主机名的机制。 此参数的可接受值为：

- IEConfig
- WinHttpConfig
- AutoDetect
- NoProxyServer
- 无

默认值为 None。

有关此参数的值的信息，请参阅 [对 system.management.automation.remoting.proxyaccesstype 枚举](/dotnet/api/system.management.automation.remoting.proxyaccesstype)。

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

指定用于代理解析的身份验证方法。 此参数可接受的值为： " **基本**"、" **摘要**" 和 " **协商**"。 默认值为 " **协商**"。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定用于代理身份验证的凭据。 输入包含 **pscredential** 对象的变量或获取 **pscredential** 对象的命令（如 `Get-Credential` 命令）。 如果未设置此选项，则不指定任何凭据。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck

指定当通过 HTTPS 进行连接时，客户端不会验证服务器证书是否由受信任的证书颁发机构签名 (CA) 。

仅当远程计算机通过其他机制受信任（例如远程计算机所属的网络在物理上是安全的并已隔离，或者远程计算机在 WinRM 配置中列为受信任主机）时才使用此选项。

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

### -SkipCNCheck

指定服务器的证书公用名 (CN) 不必与服务器的主机名匹配。 仅在使用 HTTPS 协议的远程操作中使用此选项。

仅将此选项用于受信任的计算机。

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

### -SkipRevocationCheck

不验证服务器证书的吊销状态。

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

### -UICulture

指定用于会话的 UI 区域性。

有效值包括：

- 格式的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 `ja-JP`
- 包含 **CultureInfo** 对象的变量
- 用于获取 **CultureInfo** 对象的命令，例如 `Get-Culture`

默认值为 `$null` ，在会话中使用在创建会话时在操作系统中设置的 UI 区域性。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

指示此 cmdlet 以 UTF16 格式而不是 UTF8 格式对请求进行编码。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### "PSSessionOption"。

## 注释

如果在命令中未使用 **SessionOption** 参数来创建 **PSSession**，则会话选项由首选项变量的属性值 `$PSSessionOption` （如果已设置）确定。 有关变量的详细信息 `$PSSessionOption` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。 此外，使用会话配置文件的会话配置还具有其他属性。

## 相关链接

[Enter-PSSession](Enter-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)
