---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603810"
---
# Start-Job

## 摘要
启动 PowerShell 后台作业。

## SYNTAX

### ComputerName（默认值）

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### DefinitionName

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

`Start-Job`Cmdlet 在本地计算机上启动 PowerShell 后台作业。

PowerShell 后台作业运行命令，而不与当前会话交互。 启动后台作业时，作业对象会立即返回，即使该作业需要很长时间才能完成。 当该作业运行时，你可以继续在此会话中工作而不会发生中断。

作业对象包含有关该作业的有用信息，但不包含作业结果。
作业完成后，使用 `Receive-Job` cmdlet 获取作业的结果。 有关后台作业的详细信息，请参阅 [about_Jobs](./About/about_Jobs.md)。

若要在远程计算机上运行后台作业，请使用多个 cmdlet 上可用的 **AsJob** 参数，或使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。 有关详细信息，请参阅 [about_Remote_Jobs](./About/about_Remote_Jobs.md)。

从 PowerShell 3.0 开始， `Start-Job` 可以启动自定义作业类型的实例，例如计划作业。 有关如何使用 `Start-Job` 来启动具有自定义类型的作业的信息，请参阅作业类型功能的帮助文档。

从 PowerShell 6.0 开始，可以使用 "and" () background "运算符来启动作业 `&` 。 后台运算符的功能类似于 `Start-Job` 。 用于启动作业的两种方法都创建 **PSRemotingJob** 作业对象。 有关使用与号 () 的详细信息 `&` ，请参阅 [about_Operators](./about/about_operators.md#background-operator-)。

PowerShell 7 引入了 **WorkingDirectory** 参数，该参数指定后台作业的初始工作目录。 如果未指定参数，则 `Start-Job` 默认为启动作业的调用方的当前工作目录。

> [!NOTE]
> 在 `Start-Job` 其他应用程序（例如 powershell Azure Functions）中承载 powershell 的情况下，不支持使用创建进程外后台作业。
>
> 这是由设计 `Start-Job` 决定的，因为它依赖于要 `pwsh` 在下提供的可执行 `$PSHOME` 后台作业，但当应用程序托管 powershell 时，它直接使用 powershell NuGet SDK 包，而不会随 `pwsh` 一起提供。
>
> 该方案中的替代是 `Start-ThreadJob` 从模块 **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**。

## 示例

### 示例1：启动后台作业

此示例启动在本地计算机上运行的后台作业。

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

`Start-Job` 使用 **ScriptBlock** 参数 `Get-Process` 作为后台作业运行。 **Name** 参数指定查找 PowerShell 进程 `pwsh` 。 当作业在后台运行时，将显示作业信息并返回到提示符。

若要查看作业的输出，请使用 `Receive-Job` cmdlet。 例如，`Receive-Job -Id 1`。

### 示例2：使用后台运算符启动后台作业

此示例使用与号 (`&`) 后台运算符在本地计算机上启动后台作业。 该作业的结果与 `Start-Job` 示例1中的结果相同。

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

`Get-Process` 使用 **Name** 参数指定 PowerShell 进程 `pwsh` 。 "与" 符号 (`&`) 将命令作为后台作业运行。 当作业在后台运行时，将显示作业信息并返回到提示符。

若要查看作业的输出，请使用 `Receive-Job` cmdlet。 例如，`Receive-Job -Id 5`。

### 示例3：使用 Invoke-Command 启动作业

此示例在多台计算机上运行作业。 作业存储在一个变量中，并通过使用 PowerShell 命令行上的变量名称来执行。

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

将创建一个使用的作业并将其 `Invoke-Command` 存储在 `$jobWRM` 变量中。 `Invoke-Command` 使用 **ComputerName** 参数来指定运行作业的计算机。 `Get-Content` 从文件中获取服务器名称 `C:\Servers.txt` 。

**ScriptBlock** 参数指定用于 `Get-Service` 获取 **WinRM** 服务的命令。 **JobName** 参数指定作业 **WinRM** 的友好名称。 **ThrottleLimit** 参数将并发命令数限制为16。 **AsJob** 参数启动在服务器上运行命令的后台作业。

### 示例4：获取作业信息

此示例将获取有关作业的信息，并显示在本地计算机上运行的已完成作业的结果。

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 使用 **ScriptBlock** 参数来运行命令，该命令指定 `Get-WinEvent` 获取 **系统** 日志。 **Credential** 参数指定有权在计算机上运行作业的域用户帐户。 作业对象存储在 `$j` 变量中。

变量中的对象将 `$j` 向下发送到 `Select-Object` 。 **Property** 参数指定星号 (`*`) 以显示作业对象的所有属性。

### 示例5：将脚本作为后台作业运行

在此示例中，本地计算机上的脚本作为后台作业运行。

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job` 使用 **FilePath** 参数来指定存储在本地计算机上的脚本文件。

### 示例6：使用后台作业获取进程

此示例使用后台作业按名称获取指定的进程。

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job` 使用 **Name** 参数指定友好的作业名称 **PShellJob**。 **ScriptBlock** 参数指定 `Get-Process` 获取名称为 **PowerShell** 的进程。

### 示例7：使用后台作业收集和保存数据

此示例将启动一个作业，该作业收集大量的地图数据，然后将其保存到 `.tif` 文件中。

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

`Start-Job` 使用 **Name** 参数指定友好的作业名称 **GetMappingFiles**。 **InitializationScript** 参数运行导入 **MapFunctions** 模块的脚本块。 **ScriptBlock** 参数运行 `Get-Map` 并将 `Set-Content` 数据保存在 **Path** 参数指定的位置。

### 示例8：将输入传递到后台作业

此示例使用 `$input` 自动变量来处理输入对象。 使用 `Receive-Job` 查看作业的输出。

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job`使用 `Get-Content` 带有自动变量的 ScriptBlock 参数运行 `$input` 。 `$input`变量从 **InputObject** 参数获取对象。 `Receive-Job` 使用 **Name** 参数指定作业并输出结果。 **Keep** 参数保存作业输出，以便可以在 PowerShell 会话期间再次查看。

### 示例9：为后台作业设置工作目录

**WorkingDirectory** 允许你为作业指定一个备用目录，你可以从该目录中运行脚本或打开的文件。 在此示例中，后台作业指定的工作目录不同于当前目录位置。

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

此示例的当前工作目录为 `C:\Test` 。 `Start-Job` 使用 **WorkingDirectory** 参数来指定作业的工作目录。 **ScriptBlock** 参数用于 `$PWD` 显示作业的工作目录。 `Receive-Job` 显示后台作业的输出。
**AutoRemoveJob** 删除作业并 **等待** 取消命令提示符，直到收到所有结果。

### 示例10：使用 ArgumentList 参数指定数组

此示例使用 **ArgumentList** 参数来指定参数数组。 数组是以逗号分隔的进程名称列表。

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

`Start-Job`Cmdlet 使用 **ScriptBlock** 参数运行命令。 `Get-Process` 使用 **Name** 参数来指定自动变量 `$args` 。 **ArgumentList** 参数将进程名称数组传递给 `$args` 。 进程名称 "powershell"、"pwsh" 和 "记事本" 是在本地计算机上运行的进程。

若要查看作业的输出，请使用 `Receive-Job` cmdlet。 例如，`Receive-Job -Id 1`。

### 示例11：在 Windows PowerShell 5.1 中运行作业

此示例使用值为 **5.1** 的 **PSVersion** 参数在 Windows PowerShell 5.1 会话中运行作业。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## PARAMETERS

### -ArgumentList

指定由 **FilePath** 参数或使用 **ScriptBlock** 参数指定的命令指定的脚本的参数数组或参数值。

参数必须以单维度数组参数的形式传递给 **ArgumentList** 。 例如，以逗号分隔的列表。 有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用于对用户凭据进行身份验证的机制。

此参数可接受的值如下所示：

- 默认
- 基本
- Credssp
- 摘要
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

默认值为 Default。

CredSSP 身份验证仅在 Windows Vista、Windows Server 2008 和更高版本的 Windows 操作系统中可用。

有关此参数的值的详细信息，请参阅 [system.management.automation.runspaces.authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。 此机制增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 如果未指定 **Credential** 参数，则该命令使用当前用户的凭据。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionName

指定此 cmdlet 启动的作业的定义名称。 使用此参数来启动具有定义名称的自定义作业，例如计划作业。

当使用 `Start-Job` 启动计划作业的实例时，将立即启动该作业，而不考虑作业触发器或作业选项。 生成的作业实例是计划作业，但不会将其保存到磁盘上，如触发的计划作业。 不能使用的 **ArgumentList** 参数为 `Start-Job` 在计划作业中运行的脚本的参数提供值。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

指定此 cmdlet 启动的作业的定义路径。 输入定义路径。 **DefinitionPath** 和 **DefinitionName** 参数的值的串联是作业定义的完全限定路径。 使用此参数来启动具有定义路径的自定义作业，例如计划作业。

对于计划作业， **DefinitionPath** 参数的值为 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定 `Start-Job` 作为后台作业运行的本地脚本。 输入脚本的路径和文件名，或使用管道将脚本路径发送到 `Start-Job` 。 脚本必须位于本地计算机上或本地计算机可以访问的文件夹中。

使用此参数时，PowerShell 会将指定脚本文件的内容转换为脚本块，并将该脚本块作为后台作业运行。

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

指定在作业开始前运行的命令。 若要创建脚本块，请将命令括在大括号中， (`{}`) 。

使用此参数可以准备运行作业的会话。 例如，可以使用它将函数、管理单元和模块添加到会话中。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定命令的输入。 请输入包含对象的变量，或者键入可生成对象的命令或表达式。

在 **ScriptBlock** 参数的值中，使用 `$input` 自动变量来表示输入对象。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定此 cmdlet 作为后台作业运行的本地脚本。 在本地计算机上输入脚本的路径。

`Start-Job` 使用 **LiteralPath** 参数的值，与键入的值完全相同。 不会将任何字符解释为通配字符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

为新作业指定一个友好名称。 你可以使用该名称来确定其他作业 cmdlet （如 cmdlet）的作业 `Stop-Job` 。

默认友好名称为 `Job#` ，其中 `#` 是每个作业递增的序号。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSVersion

指定用于运行作业的 PowerShell 版本。
当 **PSVersion** 的值为 **5.1** 时，作业将在 Windows PowerShell 5.1 会话中运行。
对于任何其他值，将使用当前版本的 PowerShell 运行作业。

此参数已在 PowerShell 7 中添加，并且仅适用于 Windows。

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

从 PowerShell 7 开始， **RunAs32** 参数在64位 PowerShell () 上不起作用 `pwsh` 。
如果在64位 PowerShell 中指定了 **RunAs32** ，则会 `Start-Job` 引发终止异常错误。
若要使用 RunAs32 启动32位 PowerShell (`pwsh`) 过程，需要安装32位 powershell。

在32位 PowerShell 中， **RunAs32** 强制作业在32位进程中运行，即使在64位操作系统上也是如此。

在64位版本的 Windows 7 和 Windows Server 2008 R2 上，当 `Start-Job` 命令包括 **RunAs32** 参数时，不能使用 **Credential** 参数来指定另一个用户的凭据。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要在后台作业中运行的命令。 若要创建脚本块，请将命令括在大括号中， (`{}`) 。 使用 `$input` 自动变量访问 **InputObject** 参数的值。 此参数是必需的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

指定由启动的作业的自定义类型 `Start-Job` 。 输入自定义作业类型名称，例如 PSScheduledJob（对于计划作业）或 PSWorkflowJob（对于工作流作业）。 此参数对标准后台作业无效。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkingDirectory

指定后台作业的初始工作目录。 如果未指定该参数，则从默认位置运行该作业。 默认位置是启动作业的调用方的当前工作目录。

此参数是在 PowerShell 7 中引入的。

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以使用管道将具有 **name** 属性的对象发送到 **name** 参数。 例如，可以通过管道将 **FileInfo** 对象从管道 `Get-ChildItem` 管道 `Start-Job` 。

## 输出

### System.Management.Automation.PSRemotingJob

`Start-Job` 返回一个 **PSRemotingJob** 对象，该对象表示其启动的作业。

## 注释

若要在后台运行，请 `Start-Job` 在当前会话中自己的会话中运行。 使用 `Invoke-Command` cmdlet 在 `Start-Job` 远程计算机上的会话中运行命令时，将 `Start-Job` 在远程会话的会话中运行。

## 相关链接

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
