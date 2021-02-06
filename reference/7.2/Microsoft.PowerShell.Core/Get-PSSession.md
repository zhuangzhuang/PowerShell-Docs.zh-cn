---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: e06eaaa3b6042a2105462adfc2ba8f0a4867f045
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595393"
---
# Get-PSSession

## 摘要
获取本地和远程计算机上的 PowerShell 会话。

## SYNTAX

### Name（默认值）

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### 计算机名

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### ContainerId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### ID

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

该 `Get-PSSession` cmdlet 将获取本地和远程计算机上的用户管理的 PowerShell 会话 (**pssession**) 。

从 Windows PowerShell 3.0 开始，会话将存储在每个连接远端的计算机上。 您可以使用的 **ComputerName** 或 **ConnectionUri** 参数 `Get-PSSession` 来获取连接到本地计算机或远程计算机的会话，即使它们不是在当前会话中创建的。

如果没有参数， `Get-PSSession` 则将获取在当前会话中创建的所有会话。

使用筛选参数，包括 **名称**、 **ID**、 **InstanceID**、 **State**、 **ApplicationName** 和 **ConfigurationName** 从返回的会话中进行选择 `Get-PSSession` 。

使用剩余的参数配置在 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数时运行命令的临时连接。

注意：在不带参数的 Windows PowerShell 2.0 中， `Get-PSSession` 将获取在当前会话中创建的所有会话。 **ComputerName** 参数获取在当前会话中创建并连接到指定计算机的会话。

有关 PowerShell 会话的详细信息，请参阅 [about_PSSessions](about/about_PSSessions.md)。

## 示例

### 示例1：获取在当前会话中创建的会话

```powershell
Get-PSSession
```

此命令将获取在当前会话中创建的所有 **pssession** 。 即使它们连接到此计算机，它也不会获取在其他会话或其他计算机上创建的 **pssession** 。

### 示例2：获取连接到本地计算机的会话

```powershell
Get-PSSession -ComputerName "localhost"
```

此命令获取连接到本地计算机的 **pssession** 。 若要指示本地计算机，请键入计算机名称、localhost 或点 (。 ) 

此命令返回本地计算机上的所有会话，即使它们是在不同会话中或不同计算机上创建的，也是如此。

### 示例3：获取连接到计算机的会话

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

此命令获取连接到 Server02 计算机的 **pssession** 。

此命令返回 Server02 上的所有会话，即使它们是在不同会话中或不同计算机上创建的，也是如此。

此输出显示了两个具有 Disconnected 状态的会话，这些会话的可用性为 Busy。 它们是在不同的会话中创建的，并且当前正在使用它们。 在当前会话中创建了已打开且可用的 ScheduledJobs 会话。

### 示例4：保存此命令的结果

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

此示例演示如何将命令的结果保存 `Get-PSSession` 在多个变量中。

第一个命令使用 `New-PSSession` cmdlet 在三台远程计算机上创建 **pssession** 。

第二个命令使用 `Get-PSSession` cmdlet 来获取三个 **pssession**。 然后，它将每个 **pssession** 保存在一个单独的变量中。

当 PowerShell 将对象数组分配给变量数组时，它会将第一个对象分配给第一个变量，将第二个对象分配给第二个变量，依此类推。 如果对象多于变量，则会将数组中所有剩余的对象都分配给最后一个变量。 如果变量多于对象，则弃用额外的变量。

### 示例5：使用实例 ID 删除会话

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

此示例演示如何通过使用其实例 ID 获取 **pssession** ，然后再删除 **pssession**。

第一个命令获取在当前会话中创建的所有 **pssession** 。 它将 **pssession** 发送到 Format-Table cmdlet，后者将显示每个 **PSSession** 的 **ComputerName** 和 **InstanceID** 属性。

第二个命令使用 `Get-PSSession` cmdlet 来获取特定的 **PSSession** ，并将其保存在 `$s` 变量中。 该命令使用 **InstanceID** 参数来标识 **PSSession**。

第三个命令使用 Remove-PSSession cmdlet 删除变量中的 **PSSession** `$s` 。

### 示例6：获取具有特定名称的会话

此示例中的命令将查找具有特定名称格式且使用特定会话配置的会话，然后将连接到该会话。 你可以使用此类命令来查找同事在其中启动任务的会话，然后连接该会话以完成该任务。

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

第一个命令获取名称以 BackupJob 开头并使用 ITTasks 会话配置的 Server02 和 Server12 远程计算机上的会话。该命令使用 **name** 参数来指定名称模式，并使用 **ConfigurationName** 参数来指定会话配置。 **SessionOption** 参数值是一个哈希表，可将 **OperationTimeout** 值设置为 240000 毫秒（4 分钟）。 此设置提供了更多的时间来完成命令。 **ConfigurationName** 和 **SessionOption** 参数用于配置在 `Get-PSSession` 每台计算机上运行 cmdlet 的临时会话。输出显示该命令返回 BackupJob04 会话。 会话已断开连接，并且 **可用性** 为 "无"，这表示未在使用。

第二个命令使用 `Get-PSSession` cmdlet 来访问 BackupJob04 会话，并使用 Connect-PSSession cmdlet 连接到该会话。 该命令将该会话保存在 $s 变量中。

第三个命令获取 $s 变量中的会话。 输出显示该 `Connect-PSSession` 命令已成功。 此会话处于 **Opened** 状态且可用。

### 示例7：使用 ID 获取会话

```powershell
Get-PSSession -Id 2
```

此命令获取 ID 为2的 **PSSession** 。 由于 **id** 属性的值仅在当前会话中是唯一的，因此 **id** 参数仅对本地命令有效。

## PARAMETERS

### -AllowRedirection

指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。 默认情况下，PowerShell 不会重定向连接。

此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ConnectionUri** 参数的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定应用程序的名称。 此 cmdlet 仅连接到使用指定应用程序的会话。

输入连接 URI 的应用程序名称段。 例如，在以下连接 URI 中，应用程序名称为 WSMan：`http://localhost:5985/WSMAN`。 会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。

此参数的值用于选择和筛选会话。 它不会更改会话使用的应用程序。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定用于对运行命令的会话的凭据进行身份验证的机制 `Get-PSSession` 。

此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 或 **ConnectionUri** 参数的命令。

此参数的可接受值为：

- 默认
- 基本
- Credssp
- 摘要
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential.

默认值为 Default。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

注意：在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权创建在其中运行命令的会话的用户帐户的数字公钥证书 (X509) `Get-PSSession` 。 输入证书的证书指纹。

此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 或 **ConnectionUri** 参数的命令。

在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定计算机的名称数组。 获取连接到指定计算机的会话。
不允许使用通配符。 没有默认值。

从 Windows PowerShell 3.0 开始， **PSSession** 对象存储在每个连接远端的计算机上。 为了获取指定计算机上的会话，PowerShell 会创建与每台计算机的临时连接并运行 `Get-PSSession` 命令。

键入一台或多台计算机的 NetBIOS 名称、IP 地址或完全限定的域名。 若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。

注意：此参数仅从运行 Windows PowerShell 3.0 或更高版本的 PowerShell 的计算机获取会话。 早期版本不存储会话。

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

指定配置的名称。 此 cmdlet 仅获取使用指定会话配置的会话。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。 会话的配置名称存储在该会话的 **ConfigurationName** 属性中。

此参数的值用于选择和筛选会话。 它不会更改会话使用的会话配置。

有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定一个 URI，该 URI 定义运行命令的临时会话的连接终结点 `Get-PSSession` 。 URI 必须完全限定。

此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ConnectionUri** 参数的命令。

此字符串的格式为：

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

默认值为： `http://localhost:5985/WSMAN` 。

如果未指定 **ConnectionUri**，则可以使用 **UseSSL**、 **ComputerName**、 **Port** 和 **ApplicationName** 参数来指定 **ConnectionUri** 值。 URI 的 Transport 段的有效值为 HTTP 和 HTTPS。 如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

已在 Windows PowerShell 3.0 中引入了此参数。

此参数仅从运行 Windows PowerShell 3.0 或更高版本的 Windows PowerShell 的计算机获取会话。 早期版本不存储会话。

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的 Id 的数组。 此 cmdlet 将启动与每个指定容器的交互式会话。 使用 `docker ps` 命令获取容器 id 列表。 有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定用户凭据。 此 cmdlet 将运行具有指定用户的权限的命令。 指定有权连接到远程计算机并运行命令的用户帐户 `Get-PSSession` 。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

此参数将创建的临时连接配置为 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数运行命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定会话 Id 的数组。 此 cmdlet 仅获取具有指定 Id 的会话。 键入一个或多个 ID（以逗号分隔），或使用范围运算符 (..) 来指定 ID 的范围。 不能将 ID 参数与 **ComputerName** 参数一起使用。

ID 是一个整数，用于在当前会话中唯一标识用户托管的会话。 它比 **InstanceId** 更容易记住和键入，但它仅在当前会话中是唯一的。 会话 ID 存储在该会话的 ID 属性中。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定会话的实例 Id 的数组。 此 cmdlet 仅获取具有指定实例 Id 的会话。

实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识某个会话。 即使在 PowerShell 中运行多个会话， **InstanceID** 也是唯一的。

会话的实例 ID 存储在该会话的 **InstanceID** 属性中。

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定会话名称的数组。 此 cmdlet 仅获取具有指定友好名称的会话。 允许使用通配符。

会话的友好名称存储在该会话的 **Name** 属性中。

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

指定用于运行命令的临时连接的指定网络端口 `Get-PSSession` 。 若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。

使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。 若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

此参数将创建的临时连接配置为 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数运行命令。

除非必要，否则不要使用 **Port** 参数。 命令中设置的 **端口** 适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

为该会话指定高级选项。 输入 **SessionOption** 对象（例如使用 New-PSSessionOption cmdlet 创建的对象），或输入哈希表，其中的键是会话选项名称，而值是会话选项值。

这些选项的默认值由 $PSSessionOption 首选项变量的值（如果已设置）确定。 否则，通过在会话配置中设置的选项创建默认值。

会话选项值优先于在 $PSSessionOption 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。

有关会话选项（包括默认值）的说明，请参阅 `New-PSSessionOption` 。
有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State

指定会话状态。 此 cmdlet 仅获取处于指定状态的会话。 此参数可接受的值包括：所有、打开、断开连接、已关闭和已中断。 默认值为 All。

会话状态值相对于当前会话。 没有在当前会话中创建的会话以及没有连接到当前会话的会话的状态为 Disconnected，即使它们连接到不同的会话也是如此。

会话的状态存储在该会话的 **State** 属性中。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定可建立的并发连接的最大数量，以运行该 `Get-PSSession` 命令。 如果省略此参数或输入 0（零）值，则使用默认值 32。 节流限制仅适用于当前命令，而不适用于会话或计算机。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指示此 cmdlet 使用安全套接字层 (SSL) 协议来建立运行该命令的连接 `Get-PSSession` 。 默认情况下，不使用 SSL。 如果你使用此参数，但 SSL 在用于此命令的端口上不可用，则命令将失败。

此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 参数的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

指定虚拟机的 ID 的数组。 此 cmdlet 与每个指定的虚拟机启动交互会话。 若要查看可供你使用的虚拟机，请使用以下命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定一个虚拟机的名称数组。 此 cmdlet 与每个指定的虚拟机启动交互会话。 若要查看可供你使用的虚拟机，请使用 `Get-VM` cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.Runspaces.PSSession

## 注释

- 此 cmdlet 将获取用户托管的会话 **PSSession** 对象，例如使用新的 PSSession、 `Enter-PSSession` 和 Invoke-Command cmdlet 创建的对象。 它不会获取启动 PowerShell 时所创建的系统托管会话。
- 从 Windows PowerShell 3.0 开始， **PSSession** 对象存储在连接的服务器端或接收端的计算机上。 若要获取存储在本地计算机或远程计算机上的会话，PowerShell 将建立与指定计算机的临时会话，并在该会话中运行查询命令。
- 若要获取连接到远程计算机的会话，请使用 **ComputerName** 或 **ConnectionUri** 参数来指定远程计算机。 若要筛选获取的会话 `Get-PSSession` ，请使用 **Name**、 **ID**、 **InstanceID** 和 **State** 参数。 使用剩余的参数配置使用的临时会话 `Get-PSSession` 。
- 当你使用 **ComputerName** 或 **ConnectionUri** 参数时， `Get-PSSession` 仅获取来自运行 Windows powershell 3.0 和更高版本的 PowerShell 的计算机的会话。
- **PSSession** 的 **State** 属性值相对于当前会话。
  因此，值 "已 **断开连接** " 意味着 **PSSession** 未连接到当前会话。 但是，它并不意味着 **PSSession** 会与所有会话断开连接。 它可能连接到另一个会话。 若要确定是否可以从当前会话连接或重新连接到 **PSSession** ，请使用 **Availability** 属性。

**Availability** 的 **None** 值指示可连接到 PSSession。 值为 " **忙碌** " 指示你无法连接到 **PSSession** ，因为它已连接到另一个会话。

有关会话的 **State** 属性的值的详细信息，请参阅 [RunspaceState 枚举](/dotnet/api/system.management.automation.runspaces.runspacestate)。

有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate 枚举](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

