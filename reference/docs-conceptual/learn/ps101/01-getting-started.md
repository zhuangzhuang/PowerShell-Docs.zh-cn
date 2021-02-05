---
title: 开始使用 PowerShell
description: 在哪里可以找到 PowerShell 以及如何为新用户启动它。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598240"
---
# <a name="chapter-1---getting-started-with-powershell"></a>第 1 章 - 开始使用 PowerShell

我经常发现，在会议和用户组会议上，许多没有多少经验的新用户已经开始在演示时使用 PowerShell 了。 本书首先回答了那些之前在上述会议中未使用过 PowerShell 的与会者所提出的相关问题。

具体而言，本章重点介绍如何查找和启动 PowerShell，以及如何解决新用户在刚开始使用 PowerShell 时遇到的一些难点。 请务必在 Windows 10 实验环境计算机上逐步完成本章中展示的示例。

## <a name="what-do-i-need-to-get-started-with-powershell"></a>若要开始使用 PowerShell，需要作哪些准备？

所有新式版本的 Windows 操作系统均安装了 PowerShell。 如果运行的版本低于 5.1，应安装最新版本。

- 要升级到 Windows PowerShell 5.1，请参阅[升级现有的 Windows PowerShell][]
- 要安装最新版本的 PowerShell，请参阅[安装 PowerShell][]

## <a name="where-do-i-find-powershell"></a>在哪里可以找到 PowerShell？

在 Windows 10 上查找 PowerShell 的最简单方法是在搜索栏中键入“PowerShell”，如图 1-1 所示。

![图 1-1 - 在“开始”菜单中搜索 PowerShell](media/figure1-1.png)

请注意，图 1-1 显示了四种不同的 PowerShell 快捷方式。 本书中用于演示的计算机运行的是 64 位版本的 Windows 10，如快捷方式上的 (x86) 后缀所示，分别有 64 位以及 32 位版本的 PowerShell 控制台和 PowerShell ISE（集成脚本环境）。 如果运行的是 32 位版本的 Windows 10，则只有两种快捷方式。 这些项没有 (x86) 后缀，但为 32 位版本。 如果使用的是 64 位操作系统，建议运行 64 位版本的 PowerShell，除非出于特殊原因才运行 32 位版本。

有关在其他 Windows 版本上启动 PowerShell 的信息，请参阅[启动 Windows PowerShell][]。

## <a name="how-do-i-launch-powershell"></a>如何启动 PowerShell？

在支持的生产企业环境中，我使用三个不同的 Active Directory 用户帐户。 我已在本书使用的实验环境中对这些帐户执行了镜像操作。 我以非域或非本地管理员的域用户身份登录 Windows 10 计算机。

我通过单击“Windows PowerShell”快捷方式启动了 PowerShell 控制台，如图 1-1 所示。

![图 1-4 - PowerShell 窗口的标题栏](media/figure1-4.png)

请注意，PowerShell 控制台的标题栏显示为“Windows PowerShell”，如图 1-4 所示。 一些命令运行正常，但 PowerShell 无法参与用户访问控制 (UAC)。 这意味着它无法提示用户对需要管理员批准的任务进行提升。
生成以下错误消息：

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

解决此问题的方法是以作为域用户的本地管理员身份运行 PowerShell。
这是配置第二个域用户帐户的方式。 由于使用权限最低的主体，此帐户不能为域管理员，或不能在域中具有任何提升的权限。

关闭 PowerShell。 重启 PowerShell 控制台，但这次需要右键单击 Windows PowerShell 快捷方式，然后选择“以管理员身份运行”，如图 1-5 所示 。

![图 1-5 - 上下文菜单 - 以管理员身份运行](media/figure1-5.png)

如果以普通用户身份登录 Windows，系统将提示你输入凭据。 我将输入我的用户帐户的凭据，其身份是域用户和本地管理员，如图 1-6 所示。

![图 1-6](media/figure1-6.png)

以管理员身份重启 PowerShell 后，标题栏应显示“管理员：Windows PowerShell”，如图 1-7 所示。

![图 1-7](media/figure1-7.png)

现在，由于以本地管理员身份运行了提升的 PowerShell，因此，当在本地计算机上运行某个命令且需要给予提升提示时，不会再产生 UAC 问题。 请记住，通过这个经过提升的 PowerShell 控制台实例运行的所有命令在运行时也会得到提升。

为了简化查找 PowerShell 并以管理员身份启动它的过程，建议将其固定在任务栏上，并将其设置为在每次运行时自动以管理员身份启动。

再次搜索 PowerShell，但这次要右键单击它，然后选择“固定到任务栏”，如图 1-8 所示。

![图 1-8](media/figure1-8.png)

右键单击当前固定在任务栏上的 PowerShell 快捷方式，然后选择属性，如图 1-9 所示。

![图 1-9 - 用户帐户控制 - 输入凭据](media/figure1-9.png)

单击图 1-10 中的 #1 所表示的“高级”，然后选中图 1-10 中的 #2 所表示的“以管理员身份运行”复选框，然后双击“确定”，以接受更改并退出这两个对话框。

![图 1-10 - 显示“管理员”的标题栏](media/figure1-10.png)

无需再次查找 PowerShell 或再次担心它是否以管理员身份运行。

为防止 UAC 出现问题而以管理员身份运行提升的 PowerShell 仅影响针对本地计算机运行的命令。 它不影响以远程计算机为目标的命令。

## <a name="what-version-of-powershell-am-i-running"></a>正在运行的是哪个版本的 PowerShell？

PowerShell 中有许多用于存储状态信息的自动变量。 其中某个变量是 `$PSVersionTable`，它包含可用于显示相关 PowerShell 版本信息的哈希表：

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

较新版本的 Windows PowerShell 作为 Windows Management Framework (WMF) 的一部分分发。 WMF 的版决定了要使用哪个特定版本的 .NET Framework。 要升级到 Windows PowerShell 5.1，请参阅[升级现有的 Windows PowerShell][]。

## <a name="execution-policy"></a>执行策略

与通常的看法相反，PowerShell 中的执行策略不是安全边界。 它的作用是防止用户无意间运行脚本。 已确定的用户可以轻松绕过 PowerShell 中的执行策略。 表 1-2 显示当前 Windows 操作系统的默认执行策略。

| Windows 操作系统版本 | 默认执行策略 |
| -------------------------------- | ------------------------ |
| Server 2019                      | 远程签名            |
| Server 2016                      | 远程签名            |
| Windows 10                       | 受限               |

无论采用怎样的执行策略设置，任何 PowerShell 命令都可以通过交互方式运行。 执行策略仅影响脚本中运行的命令。 `Get-ExecutionPolicy` cmdlet 用于确定当前的执行策略设置，而 `Set-ExecutionPolicy` cmdlet 用于更改执行策略。 建议使用 RemoteSigned 策略，该策略要求下载的脚本必须由受信任的发布者签名才能运行。

检查当前的执行策略：

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

当执行策略设置为“受限”时，PowerShell 脚本根本无法运行。 这是所有 Windows 客户端操作系统上的默认设置。 为了演示该问题，将以下代码另存为名为 `Stop-TimeService.ps1` 的 `.ps1` 文件。

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

只要以管理员身份运行提升的 PowerShell，该命令就可通过交互方式运行而不会出错。 不过，一旦将其保存为脚本文件并尝试执行该脚本，就会生成错误：

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

请注意，上一组结果中显示的错误明确指示了发生了什么问题（在此系统上禁用了运行脚本）。 在 PowerShell 中运行命令后如果生成错误消息，请确保阅读该错误消息，而不是只重新运行该命令并希望它成功运行。

将 PowerShell 执行策略更改为远程签名。

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

务必阅读更改执行策略时显示的警告。 另外建议查看 [about_Execution_Policies][] 帮助主题，确保已了解更改执行策略带来的安全影响。

由于已将执行策略设置为 RemoteSigned，`Stop-TimeService.ps1` 脚本将正常运行。

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

在继续之前，请务必启动 Windows 时间服务，否则可能会遇到无法预料的问题。

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>总结

在本章中，你了解了如何查找和启动 PowerShell，以及如何创建以管理员身份启动 PowerShell 的快捷方式。 你还了解了默认执行策略及其更改方式。

## <a name="review"></a>审阅

1. 如何确定计算机正在运行的 PowerShell 版本？
1. 为什么以管理员身份启动提升的 PowerShell 至关重要？
1. 如何确定当前的 PowerShell 执行策略？
1. Windows 客户端计算机上的默认 PowerShell 执行策略可以防止发生什么情况？
1. 如何更改 PowerShell 执行策略？

## <a name="recommended-reading"></a>推荐阅读的主题

如果想详细了解本章所介绍的主题，建议阅读以下 PowerShell 帮助主题。

- [about_Automatic_Variables][]
- [about_Hash_Tables][]
- [about_Execution_Policies][]

在下一章中，你将了解 PowerShell 中命令的可发现性。 下一章将介绍的内容之一是如何更新 PowerShell，以便可以直接在 PowerShell 内部查看这些帮助主题，而不必在 Internet 上查看它们。

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[升级现有的 Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[安装 PowerShell]: /powershell/scripting/install/installing-powershell
[启动 Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
