---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: d8f0a8a56792a39371a307166788f047fec99a9a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595403"
---
# Invoke-Command

## 摘要
在本地和远程计算机上运行命令。

## SYNTAX

### 进程内 (默认) 

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### 会话

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### 计算机名

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### Uri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### ContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-Command`Cmdlet 在本地或远程计算机上运行命令，并返回命令中的所有输出，包括错误。 使用单个 `Invoke-Command` 命令，可以在多台计算机上运行命令。

若要在远程计算机上运行单个命令，请使用 **ComputerName** 参数。 若要运行一系列共享数据的相关命令，请使用 `New-PSSession` cmdlet 在远程计算机上创建 **一个与** (持久连接) ，然后使用的 **Session** 参数 `Invoke-Command` 在 **PSSession** 中运行该命令。 若要在断开连接的会话中运行命令，请使用 **InDisconnectedSession** 参数。 若要在后台作业中运行命令，请使用 **AsJob** 参数。

你还可以使用 `Invoke-Command` 本地计算机上的脚本块作为命令。 PowerShell 会立即在当前作用域的子范围内运行脚本块。

在使用 `Invoke-Command` 在远程计算机上运行命令之前，请阅读 [about_Remote](./About/about_Remote.md)。

从 PowerShell 6.0 开始，你可以使用安全外壳 (SSH) 与远程计算机上的命令建立连接和调用命令。 SSH 必须安装在本地计算机上，并且必须将远程计算机配置为使用 PowerShell SSH 终结点。 基于 SSH 的 PowerShell 远程会话的优点在于，它可以跨多个平台 (Windows、Linux、macOS) 。 对于基于 SSH 的会话，请使用 **HostName** 或 **SSHConnection** 参数来指定远程计算机和相关的连接信息。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

一些代码示例使用展开来减小行长度。 有关详细信息，请参阅 [about_Splatting](./About/about_Splatting.md)。

## 示例

### 示例1：在服务器上运行脚本

此示例在 `Test.ps1` Server01 计算机上运行脚本。

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

**FilePath** 参数指定位于本地计算机上的脚本。 该脚本在远程计算机上运行，并将结果返回到本地计算机。

### 示例2：在远程服务器上运行命令

此示例在 `Get-Culture` Server01 远程计算机上运行命令。

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

**ComputerName** 参数指定远程计算机的名称。 **Credential** 参数用于在 Domain01\User01 （有权运行命令的用户）的安全上下文中运行该命令。 **ScriptBlock** 参数指定要在远程计算机上运行的命令。

在响应中，PowerShell 请求 User01 帐户的密码和身份验证方法。
然后，它将在 Server01 计算机上运行该命令并返回结果。

### 示例3：在永久连接中运行命令

此示例在 `Get-Culture` 名为 Server02 的远程计算机上使用持久性连接在会话中运行相同的命令。

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

`New-PSSession`Cmdlet 在 Server02 远程计算机上创建一个会话，并将其保存在 `$s` 变量中。 通常，仅当在远程计算机上运行一系列命令时，才会创建一个会话。

`Invoke-Command`Cmdlet `Get-Culture` 在 Server02 上运行命令。 **Session** 参数指定保存在变量中的会话 `$s` 。

作为响应，PowerShell 将在 Server02 计算机上的会话中运行命令。

### 示例4：使用会话运行共享数据的一系列命令

此示例比较了使用 **ComputerName** 和的 **会话** 参数的影响 `Invoke-Command` 。 它显示了如何使用一个会话来运行共享相同数据的一系列命令。

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

前两个命令使用的 **ComputerName** 参数在 `Invoke-Command` Server02 远程计算机上运行命令。 第一个命令使用 `Get-Process` cmdlet 来获取远程计算机上的 PowerShell 进程，并将其保存在变量中 `$p` 。 第二个命令将获取 PowerShell 进程的 **VirtualMemorySize** 属性的值。

使用 **ComputerName** 参数时，PowerShell 会创建一个新会话来运行该命令。
命令完成后，会话将关闭。 `$p`变量是在一个连接中创建的，但它在为第二个命令创建的连接中不存在。

此问题的解决方法是：在远程计算机上创建一个持久会话，然后在同一会话中运行这两个命令。

该 `New-PSSession` cmdlet 会在计算机 Server02 上创建一个持久会话，并将会话保存在 `$s` 变量中。 `Invoke-Command`接下来的行使用 **Session** 参数在同一会话中运行这两个命令。 由于两个命令在同一会话中运行，因此 `$p` 值保持活动状态。

### 示例5：输入存储在局部变量中的命令

此示例演示如何创建一个命令，该命令以脚本块的形式存储在本地变量中。
当脚本块保存在本地变量中时，可以将该变量指定为 **ScriptBlock** 参数的值。

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

`$command`变量存储 `Get-WinEvent` 设置为脚本块格式的命令。 `Invoke-Command`运行在 `$command` S1 和 S2 远程计算机上存储的命令。

### 示例6：在多台计算机上运行单个命令

此示例演示如何使用 `Invoke-Command` 在多台计算机上运行单个命令。

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

**ComputerName** 参数指定以逗号分隔的计算机名称列表。 计算机列表包括表示本地计算机的 "localhost" 值。 **ConfigurationName** 参数指定备用会话配置。 **ScriptBlock** 参数将运行 `Get-WinEvent` ，以获取每台计算机的 powershellcore.format.ps1xml/操作事件日志。

### 示例7：获取多台计算机上的主机程序版本

此示例获取在200远程计算机上运行的 PowerShell 主机程序的版本。

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

由于只运行一个命令，因此不需要创建与每台计算机的持久连接。 而是由此命令使用 **ComputerName** 参数来指示计算机。 若要指定计算机，它将使用 `Get-Content` cmdlet 来获取 Machine.txt 文件（计算机名称的文件）的内容。

`Invoke-Command`Cmdlet `Get-Host` 在远程计算机上运行命令。 它使用点表示法来获取 PowerShell 主机的 **版本** 属性。

这些命令一次运行一个。 命令完成后，所有计算机的命令输出都将保存在 `$version` 变量中。 输出包括数据来源计算机的名称。

### 示例8：在多台远程计算机上运行后台作业

此示例在两台远程计算机上运行命令。 该 `Invoke-Command` 命令使用 **AsJob** 参数，以便该命令作为后台作业运行。 这些命令在远程计算机上运行，但该作业存在于本地计算机上。 结果传输到本地计算机。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

`New-PSSession`Cmdlet 将在 Server01 和 Server02 远程计算机上创建会话。 `Invoke-Command`Cmdlet 在每个会话中运行一个后台作业。 该命令使用 **AsJob** 参数将命令作为后台作业运行。 此命令将返回一个包含两个子作业对象的作业对象，每个子作业对象分别对应于在两台远程计算机上运行的每个作业。

该 `Get-Job` 命令将作业对象保存在 `$j` 变量中。 然后，将 `$j` 变量传递给 `Format-List` cmdlet，以在列表中显示作业对象的所有属性。 最后一个命令将获取作业的结果。 它通过管道将作业对象传递 `$j` 给 `Receive-Job` cmdlet，并将结果存储在 `$results` 变量中。

### 示例9：在远程计算机上运行的命令中包括局部变量

本示例显示了如何将局部变量的值包括在运行于远程计算机上的命令中。 该命令使用 `Using` 作用域修饰符来标识远程命令中的局部变量。 默认情况下，假定所有变量均已在远程会话中定义。 `Using`PowerShell 3.0 中引入了作用域修饰符。 有关 `Using` 作用域修饰符的详细信息，请参阅 [about_Remote_Variables](./About/about_Remote_Variables.md) 和 [about_Scopes](./about/about_scopes.md)。

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

`$Log`变量存储事件日志的名称 powershellcore.format.ps1xml/操作。 `Invoke-Command`Cmdlet `Get-WinEvent` 在 Server01 上运行，以获取事件日志中的10个最新事件。 **LogName** 参数的值是 `$Log` 以作用域修饰符为前缀的变量， `Using` 用于指示该变量是在本地会话中创建的，而不是在远程会话中创建的。

### 示例10：隐藏计算机名称

此示例演示使用的 **HideComputerName** 参数的效果 `Invoke-Command` 。
**HideComputerName** 不会更改此 cmdlet 返回的对象。 它仅更改显示。 你仍可以使用 **Format** cmdlet 显示任何受影响的对象的 **PsComputerName** 属性。

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

前两个命令用于为 `Invoke-Command` `Get-Process` PowerShell 进程运行命令。 第一个命令的输出包括 **PsComputerName** 属性，此属性包含运行该命令的计算机的名称。 使用 **HideComputerName** 的第二个命令的输出不包括 **PsComputerName** 列。

### 示例11：在脚本块中使用 Param 关键字

`Param`关键字和 **ArgumentList** 参数用于将变量值传递到脚本块中的命名参数。 此示例显示以字母开头 `a` 并具有扩展名的文件名 `.pdf` 。

有关关键字的详细信息 `Param` ，请参阅 [about_Language_Keywords](./about/about_language_keywords.md#param)。

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` 使用定义两个变量的 **ScriptBlock** 参数 `$param1` 和 `$param2` 。 `Get-ChildItem` 使用命名参数、 **名称** 和 **包含** 变量名称。 **ArgumentList** 将值传递给这些变量。

### 示例12：使用脚本块中的 $args 自动变量

`$args`自动变量和 **ArgumentList** 参数用于将数组值传递到脚本块中的参数位置。 此示例显示服务器的目录内容 `.txt` 。 `Get-ChildItem` **Path** 参数的位置为0，**筛选器** 参数为 position
1.

有关变量的详细信息 `$args` ，请参阅 [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command` 使用 **ScriptBlock** 参数并 `Get-ChildItem` 指定 `$args[0]` 和 `$args[1]` 数组值。 **ArgumentList** 将 `$args` 数组值传递给 `Get-ChildItem` **Path** 和 **Filter** 的参数位置。

### 示例13：在文本文件中列出的所有计算机上运行脚本

此示例使用 `Invoke-Command` cmdlet `Sample.ps1` 在文件中列出的所有计算机上运行该脚本 `Servers.txt` 。 该命令使用 **FilePath** 参数来指定脚本文件。 利用此命令，你可以在远程计算机上运行脚本，即使远程计算机无法访问脚本文件也是如此。

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

提交该命令时，该文件的内容 `Sample.ps1` 将复制到脚本块中，并且脚本块将在每台远程计算机上运行。 此步骤等效于使用 **ScriptBlock** 参数来提交脚本的内容。

### 示例14：使用 URI 在远程计算机上运行命令

此示例演示如何在由 (URI) 的统一资源标识符标识的远程计算机上运行命令。 此特定示例 `Set-Mailbox` 在远程 Exchange 服务器上运行命令。

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

第一行使用 cmdlet 将 `Get-Credential` Windows LIVE ID 凭据存储在 `$LiveCred` 变量中。 PowerShell 会提示用户输入 Windows Live ID 凭据。

`$parameters`变量是包含要传递到 cmdlet 的参数的哈希表 `Invoke-Command` 。 `Invoke-Command`Cmdlet `Set-Mailbox` 使用 **Microsoft. Exchange** 会话配置运行命令。 **ConnectionURI** 参数指定 Exchange 服务器终结点的 URL。 **Credential** 参数指定变量中存储的凭据 `$LiveCred` 。 **AuthenticationMechanism** 参数指定基本身份验证的使用。 **ScriptBlock** 参数指定包含该命令的脚本块。

### 示例15：使用 session 选项

此示例演示如何创建和使用 **SessionOption** 参数。

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

`New-PSSessionOption`Cmdlet 创建一个会话选项对象，该对象会导致远程端在评估传入 HTTPS 连接时不会验证证书颁发机构、规范名称和吊销列表。 **SessionOption** 对象保存在 `$so` 变量中。

> [!NOTE]
> 禁用这些检查有助于进行故障排除，但明显并不安全。

`Invoke-Command`Cmdlet 用于远程运行 `Get-HotFix` 命令。 为 **SessionOption** 参数提供 `$so` 变量。

### 示例16：在远程命令中管理 URI 重定向

此示例演示如何在远程命令中使用 **AllowRedirection** 和 **SESSIONOPTION** 参数管理 URI 重定向。

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

`New-PSSessionOption`Cmdlet 将创建一个保存在变量中的 **PSSessionOption** 对象 `$max` 。 该命令使用 **MaximumRedirection** 参数将 **PSSessionOption** 对象的 **MaximumConnectionRedirectionCount** 属性设置为 1。

`Invoke-Command`Cmdlet `Get-Mailbox` 在远程 Microsoft Exchange 服务器上运行命令。 **AllowRedirection** 参数提供了用于将连接重定向到备用终结点的显式权限。 **SessionOption** 参数使用变量中存储的会话对象 `$max` 。

因此，如果 **ConnectionURI** 指定的远程计算机返回重定向消息，则 PowerShell 将重定向连接，但如果新目标返回另一个重定向消息，则将超出重定向计数值1，并 `Invoke-Command` 返回一个非终止错误。

### 示例17：访问远程会话中的网络共享

此示例演示如何从远程会话访问网络共享。 三台计算机用于演示示例。 Server01 是本地计算机，Server02 是远程计算机，Net03 包含网络共享。 Server01 连接到 Server02，然后 Server02 执行第二个跃点以访问网络共享。 有关 PowerShell 远程处理如何支持计算机之间的跃点的详细信息，请参阅 [在 PowerShell 远程处理中创建第二个跃点](/powershell/scripting/learn/remoting/ps-remoting-second-hop)。

在本地计算机上的客户端设置中以及远程计算机上的服务设置中启用了所需的凭据安全支持提供程序 (CredSSP) 委托。 若要运行此示例中的命令，您必须是本地计算机和远程计算机上的 **Administrators** 组的成员。

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

`Enable-WSManCredSSP`Cmdlet 可启用从 Server01 本地计算机到 Server02 远程计算机的 CredSSP 委托。 **Role** 参数指定 **客户端** 以在本地计算机上配置 CredSSP 客户端设置。

`New-PSSession` 创建 Server02 的 **PSSession** 对象并将该对象存储在 `$s` 变量中。

`Invoke-Command`Cmdlet 使用该 `$s` 变量连接到远程计算机 Server02。 **ScriptBlock** 参数 `Enable-WSManCredSSP` 在远程计算机上运行。 **Role** 参数指定 **服务器** 以在远程计算机上配置 CredSSP 服务器设置。

`$parameters`变量包含用于连接到网络共享的参数值。 `Invoke-Command`Cmdlet `Get-Item` 在中的会话中运行命令 `$s` 。 此命令从网络共享获取脚本 `\\Net03\Scripts` 。 该命令使用值为 **CredSSP** 的 **Authentication** 参数，并使用值为 **Domain01\Admin01** 的 **Credential** 参数。

### 示例18：在多台远程计算机上启动脚本

此示例在一百多台计算机上运行脚本。 若要最大程度地降低对本地计算机的影响，它会连接到每台计算机、启动脚本，然后从每台计算机断开连接。
脚本将继续在断开连接的会话中运行。

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

命令使用 `Invoke-Command` 来运行脚本。 **ComputerName** 参数的值是一个 `Get-Content` 命令，该命令从文本文件获取远程计算机的名称。 **InDisconnectedSession** 参数将在启动该命令后立即断开与会话的连接。 **FilePath** 参数的值是 `Invoke-Command` 在每台计算机上运行的脚本。

**SessionOption** 的值是一个哈希表。 **OutputBufferingMode** 值设置为 **Drop** ，并且 **IdleTimeout** 值设置为 **43200000** 毫秒 (12 小时) 。

若要获取在断开连接的会话中运行的命令和脚本的结果，请使用 `Receive-PSSession` cmdlet。

### 示例19：使用 SSH 在远程计算机上运行命令

此示例演示如何使用 (SSH) 安全外壳在远程计算机上运行命令。 如果在远程计算机上配置了 SSH 以提示输入密码，则会出现密码提示。
否则，必须使用基于 SSH 密钥的用户身份验证。

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### 示例20：使用 SSH 在远程计算机上运行命令并指定用户身份验证密钥

此示例演示如何使用 SSH 在远程计算机上运行命令，并指定用于用户身份验证的密钥文件。 不会提示你输入密码，除非密钥身份验证失败并且远程计算机配置为允许基本密码身份验证。

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### 示例21：使用 SSH 作为作业在多台远程计算机上运行脚本文件

此示例演示如何使用 SSH 和 **SSHConnection** 参数集在多台远程计算机上运行脚本文件。 **SSHConnection** 参数采用包含每台计算机的连接信息的哈希表的数组。 此示例要求目标远程计算机将 SSH 配置为支持基于密钥的用户身份验证。

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETERS

### -AllowRedirection

允许将此连接重定向到备用统一资源标识符 (URI)。

使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。 默认情况下，PowerShell 不会重定向连接，但你可以使用此参数允许它重定向连接。

你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。 使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置首选项变量的 **MaximumConnectionRedirectionCount** 属性 `$PSSessionOption` 。 默认值为 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定连接 URI 的应用程序名称段。 当你未在命令中使用 **ConnectionURI** 参数时，请使用此参数指定应用程序名称。

默认值为 `$PSSessionApplicationName` 本地计算机上首选项变量的值。 如果未定义此首选项变量，则默认值为 WSMAN。 该值适用于大多数使用情况。 有关详细信息，请参阅 [about_Preference_Variables](./About/about_Preference_Variables.md)。

WinRM 服务使用应用程序名称来选择为连接请求提供服务的侦听器。
此参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值匹配。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

提供命令中的局部变量的值。 在远程计算机上运行命令之前，该命令中的变量将替换为这些值。 以逗号分隔的列表形式输入值。 值按其列出顺序与变量关联。 **ArgumentList** 的别名为 Args。

**ArgumentList** 参数中的值可以是实际值（例如1024），也可以是对局部变量（如）的引用 `$max` 。

若要在命令中使用局部变量，请使用以下命令格式：

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` - 或 - `<local-variable>`

**Param** 关键字列出命令中使用的局部变量。 **ArgumentList** 按它们列出的顺序提供变量的值。 有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

指示此 cmdlet 在远程计算机上将命令作为后台作业运行。 使用此参数可运行需要很长时间才能完成的命令。

使用 **AsJob** 参数时，该命令将返回一个表示作业的对象，然后显示命令提示符。 当作业完成时，你可以继续在此会话中工作。 若要管理作业，请使用 `*-Job` cmdlet。 若要获取作业结果，请使用 `Receive-Job` cmdlet。

**AsJob** 参数类似于使用 `Invoke-Command` cmdlet 来 `Start-Job` 远程运行 cmdlet。 但是，对于 **AsJob**，作业是在本地计算机上创建的，即使作业运行在远程计算机上也是如此。 远程作业的结果将自动返回到本地计算机。

有关 PowerShell 后台作业的详细信息，请参阅 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用于对用户凭据进行身份验证的机制。 CredSSP 身份验证仅在 Windows Vista、Windows Server 2008 和更高版本的 Windows 操作系统中可用。

此参数可接受的值如下所示：

- 默认
- 基本
- Credssp
- 摘要
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

默认值为 Default。

有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。 有关详细信息，请参阅 [凭据安全支持提供程序](/windows/win32/secauthn/credential-security-support-provider)。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权连接到断开连接的会话的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 它们只能映射到本地用户帐户，而不能与域帐户一起使用。

若要获取证书指纹，请 `Get-Item` `Get-ChildItem` 在 PowerShell Cert：驱动器中使用或命令。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定运行该命令的计算机。 默认为本地计算机。

使用 **ComputerName** 参数时，PowerShell 会创建一个临时连接，此连接仅用于运行指定的命令，然后关闭。 如果需要持续性连接，请使用 **Session** 参数。

在一个逗号分隔列表中键入一台或多台计算机的 NETBIOS 名称、IP 地址或完全限定的域名。 若要指定本地计算机，请键入计算机名、localhost 或 () 的点 `.` 。

若要在 **ComputerName** 的值中使用 IP 地址，该命令必须包括 **Credential** 参数。 必须为计算机配置 HTTPS 传输，或者必须在本地计算机的 WinRM **TrustedHosts** 列表中包含远程计算机的 IP 地址。 有关将计算机名称添加到 **TrustedHosts** 列表的说明，请参阅 [如何将计算机添加到受信任的主机列表](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)。

在 Windows Vista 和更高版本的 Windows 操作系统上，若要将本地计算机包含在 **ComputerName** 的值中，则必须使用 "以 **管理员身份运行** " 选项运行 PowerShell。

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

指定用于新的 **PSSession** 的会话配置。

输入会话配置的配置名称或完全限定的资源 URI。 如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/PowerShell` 。

与 SSH 一起使用时，此参数指定要在目标上使用的子系统，如中所定义 `sshd_config` 。 SSH 的默认值为 `powershell` 子系统。

会话的会话配置位于远程计算机上。 如果远程计算机上不存在指定的会话配置，则该命令将失败。

默认值为 `$PSSessionConfigurationName` 本地计算机上首选项变量的值。 如果未设置此首选项变量，则默认值为 " **Microsoft PowerShell**"。 有关详细信息，请参阅 [about_Preference_Variables](about/about_Preference_Variables.md)。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定定义会话的连接终结点的统一资源标识符 (URI)。
URI 必须完全限定。

此字符串的格式如下：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

默认值如下：

`http://localhost:5985/WSMAN`

如果未指定连接 URI，则可以使用 **UseSSL** 和 **Port** 参数指定连接 uri 值。

URI 的 **Transport** 段的有效值为 HTTP 和 HTTPS。 如果使用传输段指定连接 URI，但未指定端口，则将使用标准端口：80用于 HTTP，443用于 HTTPS。 若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。

如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

指定容器 Id 的数组。

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指示此 cmdlet 将交互式安全令牌添加到环回会话。 通过交互式令牌，你可以在环回会话中运行用于获取其他计算机中的数据的命令。 例如，你可以在该会话中运行用于将 XML 文件从远程计算机复制到本地计算机的命令。

环回会话是在同一计算机上开始并终止的 **PSSession**。 若要创建环回会话，请省略 **ComputerName** 参数，或将其值设置为点 (`.`) 、localhost 或本地计算机的名称。

默认情况下，使用网络令牌创建环回会话，该令牌可能不提供足够的权限来对远程计算机进行身份验证。

**EnableNetworkAccess** 参数仅在环回会话中有效。 如果在远程计算机上创建会话时使用 **EnableNetworkAccess** ，则该命令将成功，但会忽略此参数。

你可以使用 **Authentication** 参数的 **CredSSP** 值（它将会话凭据委派给其他计算机）允许在环回会话中进行远程访问。

若要防止计算机受到恶意访问，具有交互式令牌（使用 **EnableNetworkAccess** 创建的令牌）的断开连接环回会话只能从创建会话的计算机重新连接。 断开连接的使用 CredSSP 身份验证的会话可通过其他计算机重新连接。 有关详细信息，请参阅 `Disconnect-PSSession`。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定此 cmdlet 在一台或多台远程计算机上运行的本地脚本。 输入脚本的路径和文件名，或通过管道将脚本路径传递给 `Invoke-Command` 。 脚本必须位于本地计算机或本地计算机可以访问的目录中。 使用 **ArgumentList** 指定脚本中参数的值。

当你使用此参数时，PowerShell 会将指定脚本文件的内容转换为脚本块，将脚本块传输到远程计算机，然后在远程计算机上运行它。

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

指示此 cmdlet 省略输出显示中每个对象的计算机名称。 默认情况下，生成该对象的计算机名称会出现在显示内容中。

此参数仅影响输出显示。 它不会更改对象。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

指定安全外壳 (基于 SSH) 连接的计算机名称的数组。 这与 **ComputerName** 参数类似，不同之处在于使用 SSH 而不是 Windows WinRM 建立与远程计算机的连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

指示此 cmdlet 在断开连接的会话中运行命令或脚本。

使用 **InDisconnectedSession** 参数时，将 `Invoke-Command` 在每台远程计算机上创建一个持久会话，启动由 **ScriptBlock** 或 **FilePath** 参数指定的命令，然后断开与该会话的连接。 这些命令将继续在断开连接的会话中运行。 **InDisconnectedSession** 使你能够在不保持与远程会话的连接的情况下运行命令。 而且，因为在返回任何结果之前会话已断开连接， **InDisconnectedSession** 确保所有命令结果都返回到重新连接的会话，而不是在会话之间拆分。

不能将 **InDisconnectedSession** 与 **Session** 参数或 **AsJob** 参数一起使用。

使用 **InDisconnectedSession** 的命令返回表示已断开连接的会话的 **PSSession** 对象。 它们不会返回命令输出。 若要连接到断开连接的会话，请使用 `Connect-PSSession` 或 `Receive-PSSession` cmdlet。 若要获取在会话中运行的命令的结果，请使用 `Receive-PSSession` cmdlet。 若要运行在断开连接的会话中生成输出的命令，请将 **OutputBufferingMode** session 选项的值设置为 **Drop**。 如果打算连接到断开连接的会话，请在会话中设置空闲超时，以便在删除会话之前可以提供足够的时间进行连接。

可以在 **SessionOption** 参数或 `$PSSessionOption` 首选项变量中设置输出缓冲模式和空闲超时。 有关会话选项的详细信息，请参阅 `New-PSSessionOption` 和 [about_Preference_Variables](./about/about_preference_variables.md)。

有关断开连接会话的功能的详细信息，请参阅 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定命令的输入。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

使用 **InputObject** 参数时，请使用 `$Input` **ScriptBlock** 参数的值中的自动变量来表示输入对象。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobName

为后台作业指定友好名称。 默认情况下，作业名为 `Job<n>` ，其中 `<n>` 是一个序号。

如果你在命令中使用 **JobName** 参数，则该命令将作为作业运行，并 `Invoke-Command` 返回一个作业对象，即使未在命令中包含 **AsJob** 也是如此。

有关 PowerShell 后台作业的详细信息，请参阅 [about_Jobs](./About/about_Jobs.md)。

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

指定安全外壳 (SSH) 用于对远程计算机上的用户进行身份验证的密钥文件路径。

SSH 允许通过私有密钥和公钥执行用户身份验证，作为基本密码身份验证的替代方法。 如果将远程计算机配置为进行密钥身份验证，则可以使用此参数来提供用于标识用户的密钥。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

指示此 cmdlet 在当前作用域中运行指定的命令。 默认情况下， `Invoke-Command` 在其自己的作用域中运行命令。

此参数仅在当前会话中运行的命令（即同时省略 **ComputerName** 和 **Session** 参数的命令）中有效。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定远程计算机上用于此命令的网络端口。 若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。 对于 HTTP) ，默认端口为 5985 (WinRM 端口5986， (HTTPS 的 WinRM 端口) 。

使用备用端口之前，请在远程计算机上配置 WinRM 侦听器，以便侦听该端口。 若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

不要使用 **Port** 参数，除非必须这样做。 在命令中设置的端口适用于运行该命令的所有计算机或会话。 备用端口设置可能会阻止在所有计算机上运行该命令。

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteDebug

用于在远程 PowerShell 会话中以调试模式运行已调用的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

指示此 cmdlet 以管理员身份调用命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要运行的命令。 将命令括在大括号中 `{ }` ，以创建脚本块。
此参数是必需的。

默认情况下，将在远程计算机上评估命令中的所有变量。 若要在命令中包括局部变量，请使用 **ArgumentList**。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定此 cmdlet 在其中运行命令的会话的数组。 输入包含 **pssession** 对象的变量或创建或获取 **pssession** 对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。

创建 **PSSession** 时，PowerShell 会建立与远程计算机的持久连接。 使用 **PSSession** 运行共享数据的一系列相关命令。 若要运行单个命令或一系列不相关的命令，请使用 **ComputerName** 参数。 有关详细信息，请参阅 [about_PSSessions](./About/about_PSSessions.md)。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionName

为断开连接的会话指定一个友好名称。 可以在后续命令中使用此名称来引用会话，例如 `Get-PSSession` 命令。 此参数只有在与 **InDisconnectedSession** 参数一起使用时才有效。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

为该会话指定高级选项。 输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。

选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。 否则，通过在会话配置中设置的选项创建默认值。

会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。 但是，它们不优先于在会话配置中设置的最大值、配额或限制。

有关包括默认值的会话选项的说明，请参阅 `New-PSSessionOption` 。 有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。
有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

此参数采用哈希表数组，其中每个哈希表都包含一个或多个建立安全外壳 (SSH) 连接所需的连接参数。 **SSHConnection** 参数适用于创建多个会话，其中每个会话需要不同的连接信息。

哈希表具有以下成员：

- **ComputerName** (或 **主机名**) 
- **端口**
- **UserName**
- **KeyFilePath** (或 **IdentityFilePath**) 

**ComputerName** (或 **HostName**) 是所需的唯一键值对。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

指示使用安全外壳 (SSH) 建立远程连接。

默认情况下，PowerShell 使用 Windows WinRM 连接到远程计算机。 此开关强制 PowerShell 使用 **HostName** 参数建立基于 SSH 的远程连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定为运行此命令可建立的并发连接的最大数目。
如果省略此参数或输入 0 值，则使用默认值 32。

节流限制仅适用于当前命令，而不适用于会话或计算机。

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

指定用于在远程计算机上运行命令的帐户的用户名。 用户身份验证方法取决于如何在远程计算机上配置 (SSH) 安全外壳。

如果 SSH 配置了基本密码身份验证，则系统将提示你输入用户密码。

如果 SSH 配置为基于密钥的用户身份验证，则可以通过 **KeyFilePath** 参数提供密钥文件路径，并且不会出现密码提示。 如果客户端用户密钥文件位于 SSH 已知位置，则基于密钥的身份验证不需要 **KeyFilePath** 参数，并且根据用户名自动进行用户身份验证。 有关详细信息，请参阅平台的 SSH 文档，了解基于密钥的用户身份验证。

这不是必需的参数。 如果未指定 **UserName** 参数，则将使用当前登录的用户名进行连接。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指示此 cmdlet 使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。 默认情况下，不使用 SSL。

WS-Management 加密通过网络传输的所有 PowerShell 内容。 **UseSSL** 参数是一种额外的保护措施，它通过 HTTPS 而不是 HTTP 来发送数据。

如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

指定虚拟机的 Id 的数组。

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定一个虚拟机的名称数组。

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -子系统

指定用于新的 **PSSession** 的 SSH 子系统。

此项指定要在目标上使用的子系统（如 sshd_config 中所定义）。
子系统使用预定义参数启动特定版本的 PowerShell。
如果远程计算机上不存在指定的子系统，则该命令将失败。

如果未使用此参数，则默认值为 "powershell" 子系统。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.object。

可以通过管道将脚本块中的命令传递给 `Invoke-Command` 。 使用 `$Input` 自动变量来表示命令中的输入对象。

## 输出

### PSRemotingJob、、或调用的命令的输出中的命令的输出。

如果使用 **AsJob** 参数，则此 cmdlet 将返回一个作业对象。 如果指定 **InDisconnectedSession** 参数，则 `Invoke-Command` 将返回 **PSSession** 对象。 否则，它将返回调用的命令的输出，这是 **ScriptBlock** 参数的值。

## 注释

在 Windows Vista 和更高版本的 Windows 操作系统上，若要使用的 **ComputerName** 参数 `Invoke-Command` 在本地计算机上运行命令，则必须使用 "以 **管理员身份运行** " 选项运行 PowerShell。

在多台计算机上运行命令时，PowerShell 会按照它们在列表中的显示顺序连接到这些计算机。 但是，命令输出会按从远程计算机接收的顺序显示，这可能会有所不同。

命令结果中将包含由运行的命令产生的错误 `Invoke-Command` 。
在本地命令中可能是终止错误的错误在远程命令中将视作非终止错误。 此策略可确保一台计算机上的终止错误不会在运行它的所有计算机上关闭该命令。 即使在一台计算机上运行远程命令，也使用这种做法。

如果远程计算机不在本地计算机信任的域中，则计算机可能无法对用户的凭据进行身份验证。 若要将远程计算机添加到 WS-MANAGEMENT 中的受信任主机列表中，请在提供程序中使用以下命令 `WSMAN` ，其中， `<Remote-Computer-Name>` 是远程计算机的名称：

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

当你使用 **InDisconnectedSession** 参数断开 **PSSession** 的连接时，会话状态将 **断开连接**，并且可用性为 **None**。 **State** 属性的值是相对于当前会话的。 如果值为 "已 **断开连接** "，则意味着 **PSSession** 未连接到当前会话。 但是，它并不意味着 **PSSession** 会与所有会话断开连接。 它可能连接到另一个会话。 若要确定是否可以连接或重新连接到该会话，请使用 **Availability** 属性。

**Availability** 的 **None** 值指示可连接到 PSSession。 值为 " **忙碌** " 表示无法连接到 **PSSession** ，因为它已连接到另一个会话。 有关会话 **状态** 属性的值的详细信息，请参阅 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)。 有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

从 PowerShell 6.0 开始包括 **HostName** 和 **SSHConnection** 参数。 添加它们是为了提供基于 (SSH) 安全外壳的 PowerShell 远程处理。 在多个平台上支持 PowerShell 和 SSH (Windows、Linux、macOS) 和 PowerShell 远程处理在安装和配置 PowerShell 和 SSH 的这些平台上运行。 这不同于以前仅限 Windows 的远程处理，该远程处理基于 WinRM，许多 WinRM 特定功能和限制不适用。 例如，目前不支持基于 WinRM 的配额、会话选项、自定义终结点配置和断开/重新连接功能。 有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

## 相关链接

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

