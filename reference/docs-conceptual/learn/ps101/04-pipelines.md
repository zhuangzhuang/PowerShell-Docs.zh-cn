---
title: 准确描述和管道
description: PowerShell 单行命令是一个用于完成单个任务的连续管道，其中包含多个命令。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 1483ec6b76d17c3dd081356ecff85a929fc43e2c
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99603573"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>第 4 章 - 单行命令和管道

当我第一次开始学习 PowerShell 时，如果无法使用 PowerShell 单行命令完成任务，我会回到 GUI。 随着时间的推移，我逐渐掌握了编写脚本、函数和模块的技能。 不要因在 Internet 上看到的一些更高级示例而不知所措。 没有人一开始就会使用 PowerShell。 我们都曾是初学者。

对于那些仍然使用 GUI 进行管理的人，我有一些建议：在管理工作站上安装管理工具，并远程管理服务器。 这样，服务器运行的是 GUI 还是操作系统的 Server Core 安装就无关紧要了。
它将帮助你准备使用 PowerShell 远程管理服务器。

与上一章一样，请确保在 Windows 10 实验室环境计算机上继续操作。

## <a name="one-liners"></a>单行命令

PowerShell one 命令是一种连续管道，不一定是一条物理线路上的命令。 并非一个物理行上的所有命令都是单行命令。

即使以下命令位于多个物理行上，它也是 PowerShell 单行命令，因为它是一个连续管道。 它可以写在一个物理行上，但我已选择在管道符号处换行。 管道符号是 PowerShell 中允许自然换行处的某个字符。

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

自然换行可以出现在常用字符处，包括逗号 (`,`) 和方左括号 (`[`)、大括号 (`{`) 和圆括号 (`(`)。 其他不太常见的字符包括分号 (`;`)、等于号 (`=`) 以及左单引号和双引号（`'`、`"`）。

将反引号 (`` ` ``) 或重音符用作续行符是一个有争议的话题。 建议尽量避免这样做。 我经常会看到使用反引号编写的 PowerShell 命令紧跟在自然换行符之后。
没有理由把它放在那里。

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

上面两个示例中所示的命令在 PowerShell 控制台中正常工作。 但如果尝试在 PowerShell ISE 的控制台窗格中运行它们，则会出现错误。 PowerShell ISE 的控制台窗格不会等待命令的其余部分在下一行（如 PowerShell 控制台）中输入。 要避免 PowerShell ISE 的控制台窗格中出现此问题，请使用 <kbd>Shift</kbd>+<kbd>Enter</kbd>，而不是只是在继续执行另一行上的命令时按 <kbd>Enter</kbd>。

下一个示例不是 PowerShell 单行命令，因为它不是一个连续管道。 它是一行上的两个单独命令，用分号分隔。

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

许多编程和脚本语言要求在每一行的末尾使用分号。 尽管可以在 PowerShell 中以这种方法使用它们，但不建议这样做，因为它们不是必需的。

## <a name="filtering-left"></a>筛选左侧

本章中所示的命令结果已筛选为一个子集。 例如，`Get-Service` 与 Name 参数一起使用，筛选返回的服务列表，以仅显示 Windows 时间服务。

在管道中，你始终希望尽快将结果筛选为你要查找的内容。 可使用第一个命令或最左侧命令的参数来完成此操作。
这有时称为“筛选左侧”。

下面的示例使用 `Get-Service` 的 Name 参数来立即筛选结果，以仅显示 Windows 时间服务。

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

通过管道将命令传递到 `Where-Object` 来执行筛选的例子很常见。

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

第一个示例筛选源，只返回 Windows 时间服务的结果。
第二个示例返回所有服务，然后通过管道将它们传递到另一个命令来执行筛选。 虽然在本例中这似乎不是什么大问题，但是想象一下，如果你正在查询 Active Directory 用户列表。 你真的想要从 Active Directory 返回数千个用户帐户的信息，而只是通过管道将它们传递到另一个命令，从而筛选出一个很小的子集吗？ 我的建议是始终筛选左侧，即使它似乎并不重要。 你会非常习惯它，并在真正需要时自动筛选左侧。

曾有人告诉我，指定的命令顺序并不重要。 这与事实相差甚远。 执行筛选时，指定命令的顺序确实很重要。 例如，假设你使用 `Select-Object` 仅选择几个属性，并使用 `Where-Object` 筛选不在选择内容中的属性。 在这种情况下，必须首先进行筛选，否则在尝试执行筛选时，该属性将不存在于管道中。

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

上一示例中的命令不会返回任何结果，因为当 `Select-Object` 的结果通过管道传递到 `Where-Object` 时，CanStopAndContinue 属性不存在。 该特定属性未被“选定”。 从本质上讲，它已被筛除了。反转 `Select-Object` 和 `Where-Object` 的顺序将产生所需结果。

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>管道

正如你在本书迄今为止展示的许多示例中所看到的那样，很多时候，一个命令的输出可以用作另一个命令的输入。 在第 3 章中，`Get-Member` 用于确定命令所生成的对象类型。 第 3 章还介绍了如何使用 `Get-Command` 的 ParameterType 参数来确定哪些命令接受该类型的输入，尽管不一定是通过管道输入。

根据命令提供帮助的程度，它可能包含 INPUTS 和 OUTPUTS 部分 。

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

之前的结果中只显示了帮助的相关部分。 正如你所看到的，INPUTS 部分表明，ServiceController 或 String 对象可以通过管道传递到 `Stop-Service` cmdlet  。 它不会告诉你哪些参数接受该类型的输入。 确定该信息的最简单方法之一是查看完整版本的 `Stop-Service` cmdlet 帮助中的不同参数。

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

同样，我仅在以前的结果集中显示了帮助的相关部分。 请注意，DisplayName 参数不接受管道输入，InputObject 参数按 ServiceController 对象的值接受管道输入，而 Name 参数按 String 对象的值接受管道输入      。 它还按属性名称接受管道输入。

当参数按属性名称和按值接受管道输入时，将始终首先尝试按值接受。 如果按值接受管道输入失败，则会尝试按属性名称接受管道输入 。 按值接受管道输入会产生误导。 我更喜欢按类型调用它。 这意味着，如果通过管道将生成 ServiceController 对象类型的命令结果传递到 `Stop-Service`，则会将该输入绑定到 InputObject 参数 。 但如果通过管道将生成 String 输出的命令结果传递到 `Stop-Service`，则将其绑定到 Name 参数 。 如果通过管道将不生成 ServiceController 或 String 对象的命令结果传递到 `Stop-Service`，但该命令确实生成了包含名为 Name 的属性的输出，则它会将输出的 Name 属性绑定到 `Stop-Service` 的 Name 参数    。

确定 `Get-Service` 命令生成的输出类型。

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service` 生成 ServiceController 对象类型。

正如你之前在帮助中看到的那样，`Stop-Service` 的 InputObject 参数通过管道按值（按类型）接受 ServiceController 对象  。 这意味着，当 `Get-Service` cmdlet 的结果通过管道传递到 `Stop-Service` 时，这些结果将绑定到 `Stop-Service` 的 InputObject 参数。

```powershell
Get-Service -Name w32time | Stop-Service
```

现在，尝试字符串输入。 通过管道将 `w32time` 传递到 `Get-Member`，以确认它是一个字符串。

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

如前面的帮助中所示，通过管道将字符串传递到 `Stop-Service` 会将其按值绑定到 `Stop-Service` 的 Name 参数 。 通过管道将 `w32time` 传递到 `Stop-Service`，以进行测试。

```powershell
'w32time' | Stop-Service
```

请注意，在上面的示例中，我在字符串 `w32time` 两侧使用了单引号。 在 PowerShell 中，应始终使用单引号而不是双引号，除非带引号的字符串的内容包含需要扩展为其实际值的变量。 通过使用单引号，PowerShell 不必分析引号中包含的内容，因此可稍微加快代码运行速度。

按 `Stop-Service` 的 Name 参数的属性名称创建自定义对象，以测试管道输入。

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

CustomObject 变量的内容是 PSCustomObject 对象类型，并且它包含名为 Name 的属性  。

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

如果要在 `$CustomObject` 变量两边使用引号，则需要使用双引号。
否则，如果使用单引号，则会将文本字符串 `$CustomObject` 通过管道传递到 `Get-Member`，而不是传递变量包含的值。

尽管将 `$CustomObject` 的内容通过管道传递到 `Stop-Service` cmdlet 会将该内容绑定到 Name 参数，但这次它会按属性名称绑定，而不是按值，因为 `$CustomObject` 的内容是一个具有名为 Name 的属性的对象   。

在此示例中，我使用其他属性名称（如 Service）创建了另一个自定义对象。

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

尝试通过管道将 `$CustomObject` 传递到 `Stop-Service` 时，会产生错误，因为它不会生成 ServiceController 或 String 对象，并且没有名为 Name 的属性  。

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

如果一个命令的输出与另一个命令的管道输入选项不相符，则可以使用 `Select-Object` 重命名属性，以便正确地配置属性。

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

在此示例中，使用 `Select-Object` 将 Service 属性重命名为名为 Name 的属性 。

此示例的语法最初看来可能有点复杂。 我所认识到的是，永远都无法通过复制和粘贴代码学会语法。 花些时间键入代码。 多试几次之后，就可成为第二天性。 拥有多个显示器是一项巨大的优势，因为你可以在一个屏幕上显示示例代码，然后在另一个屏幕上键入该代码。

有时，你可能需要使用不接受管道输入的参数。 下面的示例演示如何使用一个命令的输出作为另一个命令的输入。 首先将几个 Windows 服务的显示名称保存到一个文本文件中。

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

可以运行命令，在括号中提供所需输出，作为需要输入的命令的参数值。

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

这就像代数中的运算顺序（如果你还记得其运算方式）。 括号内的命令始终在外部的命令之前运行。

## <a name="powershellget"></a>PowerShellGet

PowerShellGet 是一个 PowerShell 模块，其中包含用于向/从 NuGet 存储库发现、安装、发布和更新 PowerShell 模块（以及其他项目）的命令。 PowerShellGet 随 PowerShell 版本 5.0 及更高版本提供。 对于 PowerShell 版本 3.0 及更高版本，它可以作为单独的下载提供。

Microsoft 托管称为 [PowerShell 库][]的联机 NuGet 存储库。 尽管此存储库由 Microsoft 托管，但存储库中包含的大多数模块不是由 Microsoft 编写的。 对于从 PowerShell 库获取的任何代码，应先在独立的测试环境中对其进行全面的评审，然后再考虑其是否适用于生产环境。

大多数公司都需要托管自己的内部专用 NuGet 存储库，在这些存储库中，他们可以发布仅供内部使用的模块以及从其他源下载的模块（已验证其并非恶意模块）。

使用 PowerShellGet 模块中包含的 `Find-Module` cmdlet，在 PowerShell 库中查找我编写的名为 MrToolkit 的模块。

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

第一次使用 PowerShellGet 模块中的某个命令时，系统将提示你安装 NuGet 提供程序。

要安装 MrToolkit 模块，请将上一条命令通过管道传递到 `Install-Module`。

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

由于 PowerShell 库是不受信任的存储库，因此系统会提示你同意安装该模块。

## <a name="finding-pipeline-input-the-easy-way"></a>查找管道输入的简单方法

MrToolkit 模块包含一个名为 `Get-MrPipelineInput` 的函数。 此 cmdlet 可用于轻松确定接受管道输入的命令参数、接受的对象类型，以及是按值还是按属性名称接受管道输入 。

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

正如你所看到的那样，我们先前通过筛选帮助内容确定的信息可借助此函数轻松确定。

## <a name="summary"></a>总结

在本章中，你已了解 PowerShell 单行命令。 你已经了解到，命令占据的物理行数与它是否是 PowerShell 单行命令无关。 还了解了筛选左侧、管道和 PowerShellGet。

## <a name="review"></a>审阅

1. PowerShell 单行命令是什么？
1. 在 PowerShell 中，自然换行处的字符有哪些？
1. 为什么要筛选左侧？
1. PowerShell 命令接受管道输入的两种方式是什么？
1. 为什么不应信任 PowerShell 库中找到的命令？

## <a name="recommended-reading"></a>推荐阅读的主题

- [about_pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet：发现、安装和更新 PowerShell 模块的简单方法][psget]

<!-- link references-->
[about_pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell 库]: https://www.powershellgallery.com/
