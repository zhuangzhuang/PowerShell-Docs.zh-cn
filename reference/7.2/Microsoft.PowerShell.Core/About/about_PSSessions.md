---
description: 介绍 (Pssession) 的 PowerShell 会话，并说明如何建立与远程计算机的持续连接。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596822"
---
# <a name="about-pssessions"></a>关于 Pssession

## <a name="short-description"></a>简短说明
介绍 (Pssession) 的 PowerShell 会话，并说明如何建立与远程计算机的持续连接。

## <a name="long-description"></a>详细说明

若要在远程计算机上运行 PowerShell 命令，可以使用 cmdlet 的 **ComputerName** 参数，也可以 (pssession) 创建 powershell 会话，并在 pssession 中运行命令。

创建 PSSession 时，PowerShell 会建立与远程计算机的持久连接。 使用 PSSession 在远程计算机上运行一系列相关命令。 在同一 PSSession 中运行的命令可以共享数据，例如变量、别名和函数的值。

你还可以在本地计算机上创建 PSSession，并在其中运行命令。
本地 PSSession 使用 PowerShell 远程处理基础结构来创建和维护 PSSession。

从 Windows PowerShell 3.0 开始，Pssession 独立于在其中创建它们的会话。 活动的 Pssession 在远程计算机 (或远程端的计算机或连接) 的 "服务器端" 进行维护。 因此，你可以断开与 PSSession 的连接，并在以后从同一台计算机或另一台计算机重新连接到它。

本主题介绍如何创建、使用、获取和删除 Pssession。 有关更高级的信息，请参阅 [about_PSSession_Details](about_PSSession_Details.md)。

注意： Pssession 使用 PowerShell 远程处理基础结构。 若要使用 Pssession，必须为本地和远程计算机配置远程处理。
有关详细信息，请参阅 [about_Remote_Requirements](about_Remote_Requirements.md)。

在 Windows Vista 和更高版本的 Windows 中，若要在本地计算机上创建 PSSession，你必须使用 "以管理员身份运行" 选项启动 PowerShell。

## <a name="what-is-a-session"></a>什么是会话？

会话是 PowerShell 运行的环境。

每次启动 PowerShell 时，将为你创建一个会话，并且你可以在该会话中运行命令。 您还可以将项添加到您的会话中，如模块和管理单元，并且可以创建变量、函数和别名等项。 这些项仅存在于会话中，并在会话结束时被删除。

你还可以在本地计算机或远程计算机上创建用户管理的会话，称为 "PowerShell 会话" 或 "Pssession"。 与默认会话一样，你可以在 PSSession 中运行命令并添加和创建项。 但是，与自动启动的会话不同，你可以控制创建的 Pssession。 您可以获取、创建、配置和删除它们、断开连接并重新连接到它们，还可以在同一 PSSession 中运行多个命令。 在删除 PSSession 之前，该 PSSession 将保持可用状态。

通常，你可以创建 PSSession 以在远程计算机上运行一系列相关命令。 在远程计算机上创建 PSSession 时，PowerShell 会建立与远程计算机的持久连接，以支持会话。

如果使用或 cmdlet 的 **ComputerName** 参数 `Invoke-Command` `Enter-PSSession` 运行远程命令或启动交互式会话，则 PowerShell 会在该远程计算机上创建一个临时会话，并在该命令完成后或在交互式会话结束时立即关闭会话。 你无法控制这些临时会话，并且你无法将其用于多个命令或单个交互式会话。

在 PowerShell 中，"当前会话" 是您正在使用的会话。 "当前会话" 可以引用任何会话，包括临时会话或 PSSession。

## <a name="why-use-a-pssession"></a>为什么使用 PSSession？

需要与远程计算机建立持久连接时，请使用 PSSession。
使用 PSSession，你可以运行共享数据的一系列命令，如变量的值、函数的内容或别名的定义。

无需创建 PSSession 即可运行远程命令。 使用启用远程的 cmdlet 的 **ComputerName** 参数在一台或多台计算机上运行单个命令或一系列不相关的命令。

当你使用或的 **ComputerName** 参数时 `Invoke-Command` ，PowerShell 将与 `Enter-PSSession` 远程计算机建立临时连接，然后在该命令完成后立即关闭连接。 连接关闭时，所创建的任何数据元素都将丢失。

具有 **ComputerName** 参数的其他 cmdlet （例如 `Get-Eventlog` 和 `Get-WmiObject` ）使用不同的远程处理技术来收集数据。 无创建一个持久连接，如 PSSession。

## <a name="how-to-create-a-pssession"></a>如何创建 PSSession

若要创建 PSSession，请使用 `New-PSSession` cmdlet。 若要在远程计算机上创建 PSSession，请使用该 cmdlet 的 **ComputerName** 参数 `New-PSSession` 。

例如，以下命令在 Server01 计算机上创建一个新的 PSSession。

```powershell
New-PSSession -ComputerName Server01
```

提交该命令时，将 `New-PSSession` 创建 PSSession 并返回表示 PSSession 的对象。 您可以在创建 PSSession 时将对象保存在变量中，也可以使用 `Get-PSSession` 命令在以后获取 pssession。

例如，以下命令在 Server01 计算机上创建一个新的 PSSession，并将生成的对象保存在 $ps 的变量中。

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>如何在多台计算机上创建 Pssession

若要在多台计算机上创建 Pssession，请使用该 cmdlet 的 **ComputerName** 参数 `New-PSSession` 。 在以逗号分隔的列表中键入远程计算机的名称。

例如，若要在 Server01、Server02 和 Server03 计算机上创建 Pssession，请键入：

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` 在每台远程计算机上创建一个 PSSession。

## <a name="how-to-get-pssessions"></a>如何获取 Pssession

若要获取在当前会话中创建的 Pssession，请使用 `Get-PSSession` 不带 **ComputerName** 参数的 cmdlet。 `Get-PSSession` 返回返回的相同类型的对象 `New-PSSession` 。

以下命令将获取在当前会话中创建的所有 Pssession。

```powershell
Get-PSSession
```

Pssession 的默认显示显示其 ID 和默认显示名称。 您可以在创建会话时分配备用显示名称。

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

你还可以在变量中保存 Pssession。 以下命令将获取 Pssession 并将其保存在 \$ ps123 变量中。

```powershell
$ps123 = Get-PSSession
```

使用 PSSession cmdlet 时，可以按其 ID、其名称或 (GUID) 的实例 ID 来引用 PSSession。 下面的命令通过其 ID 获取 PSSession，并将其保存在 \$ ps01 变量中。

```powershell
$ps01 = Get-PSSession -Id 1
```

从 Windows PowerShell 3.0 开始，Pssession 在远程计算机上维护。 若要获取在特定远程计算机上创建的 Pssession，请使用该 cmdlet 的 **ComputerName** 参数 `Get-PSSession` 。 以下命令将获取在 Server01 远程计算机上创建的 Pssession。 这包括在当前会话和本地计算机或其他计算机上的其他会话中创建的 Pssession。

```powershell
Get-PSSession -ComputerName Server01
```

在 Windows PowerShell 2.0 中， `Get-PSSession` 仅获取在当前会话中创建的 pssession。 它不会获取在其他会话或其他计算机上创建的 Pssession，即使会话连接到并且正在本地计算机上运行命令。

## <a name="how-to-run-commands-in-a-pssession"></a>如何在 PSSession 中运行命令

若要在一个或多个 Pssession 中运行命令，请使用 `Invoke-Command` cmdlet。
使用 Session 参数指定 Pssession，并使用 **ScriptBlock** 参数来指定命令。

例如，若要 `Get-ChildItem` 在 123 $ps 变量中保存的三个 pssession 中的每一个中运行 ( "dir" ) 命令，请键入：

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>如何删除 Pssession

使用完 PSSession 后，请使用 `Remove-PSSession` cmdlet 删除 pssession，并释放所使用的资源。

```powershell
Remove-PSSession -Session $ps
```

或

```powershell
Remove-PSSession -Id 1
```

若要从远程计算机中删除 PSSession，请使用该 cmdlet 的 **ComputerName** 参数 `Remove-PSSession` 。

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

如果不删除 PSSession，则 PSSession 在超时之前仍可供使用。

你还可以使用 cmdlet 的 **IdleTimeout** 参数 `New-PSSessionOption` 设置空闲 PSSession 的过期时间。 有关详细信息，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

## <a name="the-pssession-cmdlets"></a>PSSession Cmdlet

若要获取 PSSession cmdlet 列表，请键入：

```powershell
Get-Help *-PSSession
```

- Connect-PSSession：将 PSSession 连接到当前会话
- Disconnect-PSSession：断开与当前会话的 PSSession 的连接
- Enter-PSSession：启动交互式会话
- Exit-PSSession：结束交互式会话
- Get-help：获取当前会话中的 Pssession
- New-PSSession：在本地或远程计算机上创建新的 PSSession
- Receive-PSSession：获取在断开连接的会话中运行的命令的结果
- Remove-PSSession：删除当前会话中的 Pssession

## <a name="for-more-information"></a>有关详细信息

有关 Pssession 的详细信息，请参阅 [about_PSSession_Details](about_PSSession_Details.md)。

## <a name="see-also"></a>另请参阅

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)

