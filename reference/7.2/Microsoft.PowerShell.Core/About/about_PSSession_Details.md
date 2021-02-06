---
description: 提供有关 PowerShell 会话以及它们在远程命令中扮演的角色的详细信息。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 79340e5d0ae1fe047f1f37bdfdbb1bebe920d851
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596838"
---
# <a name="about-pssession-details"></a>关于 PSSession 详细信息

## <a name="short-description"></a>简短说明
提供有关 PowerShell 会话以及它们在远程命令中扮演的角色的详细信息。

## <a name="long-description"></a>详细说明

会话是 PowerShell 运行的环境。 每次启动 PowerShell 时都会创建一个会话。 你可以在你的计算机或另一台计算机上创建名为 "PowerShell 会话" 或 "Pssession" 的其他会话。

与 PowerShell 为你创建的会话不同，你可以控制和管理你创建的 Pssession。

Pssession 在远程计算中扮演着重要的角色。 创建连接到远程计算机的 PSSession 时，PowerShell 将建立与远程计算机的持久连接，以支持 PSSession。 可以使用 PSSession 运行一系列用于共享数据的命令、函数和脚本。

本主题提供有关 PowerShell 中的会话和 Pssession 的详细信息。 有关可对会话执行的任务的基本信息，请参阅 [about_PSSessions](about_PSSessions.md)。

## <a name="about-sessions"></a>关于会话

从技术上讲，会话是运行 PowerShell 的执行环境。 每个会话都包括一个系统管理组件的实例和一个 PowerShell 运行的主机程序。 主机可以是熟悉的 PowerShell 控制台，也可以是运行命令的其他程序，如 Cmd.exe 或生成的程序（例如 Windows PowerShell 集成脚本环境 (ISE) ）。 从 Windows 的角度来看，会话是目标计算机上的 Windows 进程。

每个会话都是单独配置的。 它包含其自身的属性、其自身的执行策略和自己的配置文件。 即使您在计算机上更改了环境，在创建会话时存在的环境仍会持续保持其生存期。 所有会话都在全局作用域中创建，甚至是在脚本中创建的会话。

一次只能在一个会话中运行一个命令 (或命令管道) 。 第二个命令 (同步运行一次，) 最多需要四分钟才能完成第一个命令。 第二个命令异步运行 (同时) 失败。

## <a name="about-pssessions"></a>关于 Pssession

每次启动 PowerShell 时都会创建一个会话。 PowerShell 会创建临时会话来运行单个命令。
但是，你还可以创建 (名为 "PowerShell 会话" 或 "Pssession" ) 的会话，你可以对其进行控制和管理。

Pssession 对于远程命令至关重要。 如果使用或 cmdlet 的 **ComputerName** 参数 `Invoke-Command` ，则 `Enter-PSSession` PowerShell 会建立一个临时会话来运行命令，然后在命令或交互式会话完成后立即关闭会话。

但是，如果使用 `New-PSSession` cmdlet 创建 PSSession，则 PowerShell 将在远程计算机上建立一个持久会话，在该会话中可以运行多个命令或交互会话。 你创建的 Pssession 将保持打开状态并可供使用，直到你将其删除或在你关闭创建它们的会话之前使用。

在远程计算机上创建 PSSession 时，系统会在远程计算机上创建一个 PowerShell 进程，并建立从本地计算机到远程计算机上的进程的连接。 在本地计算机上创建 PSSession 时，将在本地计算机上创建新的进程和连接。

## <a name="when-do-i-need-a-pssession"></a>何时需要 PSSession？

`Invoke-Command`和 `Enter-PSSession` Cmdlet 具有 **ComputerName** 和 **Session** 参数。 可以使用运行远程命令。

使用 **ComputerName** 参数在一台或多台计算机上运行单个命令或一系列不相关的命令。

若要运行共享数据的命令，需要与远程计算机建立持久连接。 在这种情况下，创建 PSSession，然后使用 **Session** 参数在 PSSession 中运行命令。

从远程计算机获取数据的许多其他 cmdlet （如 `Get-Process` 、、 `Get-Service` 和） `Get-EventLog` `Get-WmiObject` 只包含 **ComputerName** 参数。 它们使用 PowerShell 远程处理以外的技术来远程收集数据。 这些 cmdlet 没有 **Session** 参数，但你可以使用 `Invoke-Command` cmdlet 在 PSSession 中运行这些命令。

## <a name="how-do-i-create-a-pssession"></a>如何创建 PSSession？

若要创建 PSSession，请使用 `New-PSSession` cmdlet。 您可以使用 `New-PSSession` 在本地或远程计算机上创建 PSSession。

## <a name="can-i-create-a-pssession-on-any-computer"></a>是否可以在任何计算机上创建 PSSession？

若要创建连接到远程计算机的 PSSession，计算机必须配置为在 PowerShell 中进行远程处理。 当前用户必须是远程计算机上 Administrators 组的成员，或者当前用户必须能够提供 Administrators 组的成员的凭据。 有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

## <a name="can-i-see-my-pssessions-in-other-sessions"></a>我是否能在其他会话中看到我的 Pssession？

从 Windows PowerShell 3.0 开始，cmdlet 的 **ComputerName** 参数将 `Get-PSSession` 获取你在指定的远程计算机上创建的 pssession。

Active Pssession 在远程计算机上保持 (连接) 的 "服务器端"，可以从任何计算机上的任何会话获取它们。

例如，如果您创建从 Server01 计算机到 Server02 计算机的 PSSession，然后切换到 Server03 计算机，则可以使用类似于下面的命令来获取会话。

```powershell
Get-PSSession -ComputerName Server02
```

即使断开与会话的连接，也会在远程计算机上保留会话，直到将其删除或超时。

在 Windows PowerShell 2.0 中，只能获取在当前会话中创建的 Pssession。 无法获取在其他会话中创建的 Pssession。

有关详细信息，请参阅 [get-help](xref:Microsoft.PowerShell.Core.Get-PSSession)。

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a>是否可以看到其他人在我的电脑上创建的 Pssession？

仅当你可以提供创建 PSSession 的用户的凭据或 PSSession 使用的会话配置包含 RunAs 凭据时，才能获取和管理其他人已创建的 Pssession。 否则，你可以获取、连接、使用和管理你创建的 Pssession。

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a>是否可以从其他计算机连接到 PSSession？

从 Windows PowerShell 3.0 开始，Pssession 独立于创建它们的会话。 在远程或连接的 "服务器端" 的计算机上维护活动的 Pssession。

可以使用 `Disconnect-PSSession` cmdlet 断开与 PSSession 的连接。 PSSession 断开与本地会话的连接，但在远程计算机上维护。
命令继续在断开连接的 PSSession 中运行。 可以关闭 PowerShell 并关闭源计算机，而不会中断 PSSession。

稍后，甚至几个小时，你可以使用 `Get-PSSession` cmdlet 来获取 pssession 和 cmdlet， `Connect-PSSession` 以从另一台计算机上的新会话连接到 pssession。

有关详细信息，请参阅 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)。

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a>如果我的电脑停止，PSSession 会发生什么情况？

断开连接的 Pssession 独立于创建它们的会话。 如果断开 PSSession 的连接然后关闭源计算机，则将在远程计算机上维护 PSSession。

此外，PowerShell 还尝试恢复无意中断开连接的活动 Pssession，如计算机重启、暂时停电或网络中断。 如果源会话仍可用，则 PowerShell 将尝试维护 PSSession，或将其恢复为已打开状态，如果不是，则为断开连接状态。

"Active" PSSession 是运行命令的 PSSession。 如果已连接 PSSession (未断开连接) 并且命令在连接的会话关闭时在 PSSession 中运行，则 PowerShell 将尝试维护远程计算机上的 PSSession。 但是，如果未在 PSSession 中运行任何命令，则在连接的会话关闭时，PowerShell 会关闭 PSSession。

有关详细信息，请参阅 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)。

## <a name="can-i-run-a-background-job-in-a-pssession"></a>能否在 PSSession 中运行后台作业？

是的。 后台作业是在后台异步运行的命令，不与当前会话交互。 提交用于启动作业的命令时，该命令将返回一个作业对象，但该作业将继续在后台运行，直到完成。

若要在本地计算机上启动后台作业，请使用 `Start-Job` 命令。
可以通过使用 **ComputerName** 参数) 或在 PSSession (中使用 **Session** 参数) 来运行后台作业 (。

若要在远程计算机上启动后台作业，请使用 `Invoke-Command` cmdlet 及其 **AsJob** 参数，或使用 `Invoke-Command` cmdlet `Start-Job` 在远程计算机上运行命令。 使用 **AsJob** 参数时，可以使用 **ComputerName** 或 **Session** 参数。

使用 `Invoke-Command` 运行 `Start-Job` 命令时，必须在 PSSession 中运行该命令。 如果使用 **ComputerName** 参数，则当作业对象返回时，PowerShell 将结束连接，并且该作业将中断。

有关详细信息，请参阅 [about_Jobs](about_Jobs.md)。

## <a name="can-i-run-an-interactive-session"></a>能否运行交互式会话？

是的。 若要启动与远程计算机的交互式会话，请使用 `Enter-PSSession` cmdlet。 在交互式会话中，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。

您可以通过使用 **ComputerName** 参数) 在临时会话 (中运行交互式会话，或使用 **session** 参数) 在 PSSession (中运行。
如果使用 PSSession，PSSession 将保留以前的命令中的数据，而 PSSession 将保留在交互式会话过程中生成的所有数据，以便在以后的命令中使用。

结束交互式会话时，PSSession 将保持打开状态并可供使用。

有关详细信息，请参阅 [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 和 [Exit-pssession](xref:Microsoft.PowerShell.Core.Exit-PSSession)。

## <a name="must-i-delete-the-pssessions"></a>是否必须删除 Pssession？

是的。 PSSession 是一个独立的环境，该环境使用内存和其他资源，即使未使用它也是如此。 完成 PSSession 后，请将其删除。 如果创建多个 Pssession，请关闭未使用的文件，并仅保留当前正在使用的文件。

若要删除 Pssession，请使用 `Remove-PSSession` cmdlet。 它删除 Pssession 并释放它们使用的所有资源。

你还可以使用的 **IdleTimeOut** 参数 `New-PSSessionOption` ，在指定的时间间隔后关闭空闲 PSSession。 有关详细信息，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

如果将 PSSession 对象保存在变量中，然后删除 PSSession 或使其超时，则该变量仍包含 PSSession 对象，但 PSSession 不处于活动状态，并且不能使用或修复。

## <a name="are-all-sessions-and-pssessions-alike"></a>是否所有会话和 Pssession 都是相同的？

不能。 开发人员可以创建只包括所选提供程序和 cmdlet 的自定义会话。 如果命令在一个会话中工作而不是在另一个会话中工作，则可能是因为会话受到限制。

## <a name="see-also"></a>另请参阅

[about_Jobs](about_Jobs.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)

