---
description: 介绍 PowerShell 中的可更新帮助系统。
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: d688448b5aab8ec35ab5d57b444ad9902b8e8ecd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596030"
---
# <a name="about-updatable-help"></a>关于可更新帮助

## <a name="short-description"></a>简短说明
介绍 PowerShell 中的可更新帮助系统。

## <a name="long-description"></a>长说明

PowerShell 提供了几种不同的方法来访问 PowerShell cmdlet 和概念的最新帮助主题。

PowerShell 3.0 中引入的可更新帮助系统旨在确保你始终在本地计算机上具有最新的帮助主题，以便你可以在命令行中读取它们。 它可让你轻松下载和安装帮助文件，并在新的帮助文件可用时更新这些文件。

若要为企业中的多台计算机和无法访问 internet 的计算机提供更新的帮助，可更新帮助允许你将帮助文件下载到文件系统目录或文件共享，然后从文件共享安装帮助文件。

在 PowerShell 4.0 中， **HelpInfoUri** 属性通过 Windows PowerShell 远程处理保留，这允许对 `Save-Help` 远程计算机上安装的模块进行处理，但不一定要在本地计算机上安装。 可以通过在没有 `Export-Clixml` internet 访问权限的计算机上运行，在能够访问 internet 的计算机上导入 **PSModuleInfo** 对象，然后 `Save-Help` 在 **PSModuleInfo** 对象上运行，从而将 PSModuleInfo 对象保存到磁盘或可移动媒体 (例如 USB 驱动器) 。 保存的帮助可以通过使用可移动媒体复制到远程断开连接的计算机，然后通过运行进行安装 `Update-Help` 。 这些功能改进 `Save-Help` 使你可以在没有任何类型网络访问权限的计算机上安装帮助。 有关如何使用新功能的示例 `Save-Help` ，请参阅本主题中的 [如何从文件共享更新帮助](#how-to-update-help-from-a-file-share) 。

即使计算机上没有帮助文件，可更新帮助也支持联机访问最新的帮助主题和 cmdlet 的基本帮助。

PowerShell 3.0 未附带帮助文件。 你可以使用 "可更新的帮助" 功能为默认情况下在 PowerShell 中包含的所有命令和所有 Windows 模块安装帮助文件。

## <a name="updatable-help-cmdlets"></a>可更新帮助 cmdlet

- `Update-Help`：从 internet 或文件共享下载最新的帮助文件，并将其安装在本地计算机上。

- `Save-Help`：从 internet 下载最新的帮助文件，并将它们保存在文件系统目录或文件共享中。 若要在计算机上安装帮助文件，请使用 `Update-Help` 。

- `Get-Help`：在命令行中显示帮助主题。 从计算机上的帮助文件中获取帮助。 显示自动生成的有关不包含帮助文件的 cmdlet 和函数的帮助。 在默认 internet 浏览器中打开有关 cmdlet、函数、脚本和工作流的联机帮助主题。

## <a name="auto-generated-help-help-without-help-files"></a>自动生成的帮助：帮助无帮助文件

如果计算机上没有 cmdlet、函数或工作流的帮助文件，则该 `Get-Help` cmdlet 将显示自动生成的帮助并提示你下载帮助文件或联机阅读这些帮助文件。

自动生成的帮助包括语法和别名，以及说明如何使用可更新的帮助 cmdlet 和访问联机帮助主题的注释。

例如，以下命令获取 cmdlet 的基本帮助 `Get-Culture` 。 输出显示 `Get-Help` 计算机上没有帮助文件时的显示。

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>模块的帮助文件

可更新帮助的最小单位是模块的帮助。 模块帮助包含模块中所有 cmdlet、函数、工作流、提供程序、脚本和概念的帮助。 您可以为计算机上安装的所有模块更新帮助，即使这些模块未导入到当前会话中也是如此。

您可以为整个模块更新帮助，但不能更新单个 cmdlet 的帮助。

若要查找包含特定 cmdlet 的模块，请使用以下命令格式：

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

例如，若要查找包含该 cmdlet 的模块 `Set-ExecutionPolicy` ，请键入：

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

若要为特定模块更新帮助，请键入：

```powershell
Update-Help -Module <ModuleName>
```

例如，若要更新包含 Set-ExecutionPolicy cmdlet 的模块的帮助，请键入：

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>可更新帮助的权限

若要为目录中的模块更新帮助 `$pshome/Modules` ，你必须是计算机上 Administrators 组的成员。

如果您不是 Administrators 组的成员，则不能为这些模块更新帮助;但是，如果您可以访问 internet，则可以联机查看帮助。

为目录中的模块 `$home/Documents/PowerShell/Modules` 或其他子目录中的模块更新帮助 `$home` 不需要特殊权限。

`Update-Help`和 `Save-Help` Cmdlet 具有 **UseDefaultCredentials** 参数，该参数提供当前用户的显式凭据。 此参数设计用于访问安全的 internet 位置。

`Update-Help`和 `Save-Help` cmdlet 还具有一个 **Credential** 参数，该参数使你可以在远程计算机上运行该命令并访问第三台计算机上的文件共享。 仅当使用的 SourcePath 或 **LiteralPath** 参数和的 `Update-Help` **DestinationPath** 或 **LiteralPath** 参数时，Credential 参数才有效 `Save-Help` 。

## <a name="how-to-install-and-update-help-files"></a>如何安装和更新帮助文件

若要首次下载和安装帮助文件，或更新计算机上的帮助文件，请使用 `Update-Help` cmdlet。

`Update-Help`Cmdlet 可为你完成所有的工作，包括以下任务。

- 确定支持可更新帮助的模块。
- 查找每个模块存储其可更新帮助文件的 internet 位置。
- 将计算机上每个模块的帮助文件与可用于每个模块的最新帮助文件进行比较。
- 从 internet 下载新的文件。
- 解包帮助文件包。
- 验证文件是否为有效的帮助文件。
- 将帮助文件安装在模块目录的特定于语言的子目录中。

若要访问新的帮助主题，请使用 `Get-Help` cmdlet。 不需要重新启动 PowerShell。

若要在支持可更新帮助的计算机上安装或更新所有模块的帮助，请键入：

```powershell
Update-Help
```

若要为特定模块更新帮助，请添加的 **Module** 参数 `Update-Help` 。 模块名称中允许使用通配符。

例如，若要更新 ServerManager 模块的帮助，请键入：

```powershell
Update-Help -Module ServerManager
```

如果没有参数， `Update-Help` 则将为会话中的所有模块以及支持可更新帮助的所有已安装模块更新帮助。 要包含的模块必须安装在 PSModulePath 环境变量的值中列出的目录中。 它们也是由 "Get-help-ListAvailable" 命令返回的模块。

如果 **Module** 参数的值 `*` (all) ，则 `Update-Help` 将尝试为所有已安装的模块（包括不支持可更新帮助的模块）更新帮助。 此命令通常会生成许多错误，因为 cmdlet 遇到不支持可更新帮助的模块。

## <a name="how-to-update-help-from-a-file-share"></a>如何从文件共享更新帮助

若要支持未连接到 internet 的计算机，或者若要控制或简化企业中的更新帮助，请使用 `Save-Help` cmdlet。 `Save-Help`Cmdlet 可从 internet 下载帮助文件，并将它们保存在指定的文件系统目录中。

`Save-Help` 将指定目录中的帮助文件与可用于每个模块的最新帮助文件进行比较。 如果目录中没有可用于该模块的帮助文件或更新的帮助文件，则该 `Save-Help` cmdlet 将从 internet 下载新的文件。 但是，它不会解包或安装帮助文件。

若要在计算机上安装或更新保存到文件系统目录的帮助文件，请使用该 cmdlet 的 **SourcePath** 参数 `Update-Help` 。 `Update-Help`Cmdlet 标识最新的帮助文件，对其进行解包和验证，然后将它们安装在模块目录的特定于语言的子目录中。

例如，若要将所有已安装模块的帮助保存到 `\\Server\Share` 目录中，请键入：

```powershell
Save-Help -DestinationPath \\Server\Share
```

然后，若要从目录更新帮助 `\\Server\Share` ，请键入：

```powershell
Update-Help -SourcePath \\Server\Share
```

下面的示例演示 `Save-Help` 如何使用为未安装在本地计算机上的模块保存帮助。 在此示例中，管理员运行 `Save-Help` 从连接了 internet 的客户端计算机保存 DhcpServer 模块的帮助，而无需在本地计算机上安装 DhcpServer 模块或 DHCP 服务器角色。

选项1：运行 `Invoke-Command` 以获取远程模块的 **PSModuleInfo** 对象，将其保存在变量中， `$m` 然后在 `Save-Help` **PSModuleInfo** 对象上运行，方法是将变量指定 `$m` 为模块名称。

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

选项2：在运行 DHCP 服务器模块的计算机上打开以其为目标的 PSSession，若要获取该模块的 **PSModuleInfo** 对象，请将其保存在变量中 `$m` ，然后 `Save-Help` 在保存在变量中的对象上运行 `$m` 。

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

选项3：打开一个 CIM 会话，以运行 DHCP 服务器模块的计算机为目标，获取该模块的 **PSModuleInfo** 对象，将其保存在变量中 `$m` ，然后 `Save-Help` 在保存在变量中的对象上运行 `$m` 。

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

在以下示例中，管理员在没有网络访问权限的计算机上安装 DHCP 服务器模块的帮助。

首先，运行 `Export-Clixml` 将 **PSModuleInfo** 对象导出到共享文件夹或可移动介质。

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

接下来，将可移动媒体传输到可访问 internet 的计算机，然后使用导入 **PSModuleInfo** 对象 `Import-Clixml` 。 运行 `Save-Help` 保存导入的 DhcpServer 模块 **PSModuleInfo** 对象的帮助。

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

最后，将可移动媒体传输回没有网络访问的计算机，然后通过运行安装帮助 `Update-Help` 。

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

如果没有参数， `Save-Help` 则会下载会话中所有模块的帮助以及所有支持可更新帮助的已安装模块。 要包含的模块必须安装在 "环境变量" 的值中列出的目录中，该目录位于 `$env:PSModulePath` 要保存帮助的本地计算机或远程计算机上。 它们也是通过运行命令返回的模块 `Get-Help -ListAvailable` 。

## <a name="how-to-update-help-files-in-different-languages"></a>如何更新不同语言的帮助文件

默认情况下， `Update-Help` 和 `Save-Help` cmdlet 会下载在本地计算机上为 Windows 设置的 UI 区域性和语言的帮助。 如果指定模块的帮助文件在本地 UI 区域性中不可用，则 `Update-Help` `Save-Help` 使用 Windows 语言回退规则查找支持的最佳语言。

但是，你可以使用和 cmdlet 的 **UICulture** 参数 `Update-Help` `Save-Help` 在可用的任意 UI 区域性中下载和安装帮助文件。

例如，若要将该会话中所有模块的最新帮助文件以日语 (Ja-jp) 和法语 (fr) ，请键入：

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

如果在指定的语言中没有可用的模块的帮助文件，则 `Update-Help` 和 cmdlet 会 `Save-Help` 返回一条错误消息，其中列出了每个模块的帮助可用的语言，因此你可以选择最能满足你的需求的替代方法。

> [!NOTE]
> 目前，可更新的帮助内容仅以英语 (en-us) 发布。 在某些非 Windows 系统上，必须使用 **UICulture** 参数显式请求 `en-US` 内容。

## <a name="how-to-use-online-help"></a>如何使用联机帮助

如果无法或不选择更新本地计算机上的帮助文件，仍可以联机获取最新的帮助文件。

若要打开任何 cmdlet 或函数的联机帮助主题，请使用 cmdlet 的 **online** 参数 `Get-Help` 。

例如，以下命令将 `Get-Job` 在默认 internet 浏览器中打开 cmdlet 的联机帮助主题：

```powershell
Get-Help Get-Job -Online
```

若要获取脚本的联机帮助，请使用 **online** 参数和该脚本的完整路径。

**Online** 参数不适用于主题。 若要查看有关 PowerShell 的 "关于" 主题，包括有关 PowerShell 语言的帮助主题，请参阅 [Powershell 相关主题](about.md)。

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>如何最大程度地减少或阻止 internet 下载

若要最大程度地减少 internet 下载并向未连接到 internet 的用户提供可更新帮助，请使用 `Save-Help` cmdlet。 从 internet 下载帮助并将其保存到网络共享。 然后，创建一个 `Update-Help` 在所有计算机上运行命令的组策略设置或计划作业。 将 cmdlet 的 **SourcePath** 参数值设置 `Update-Help` 为网络共享。

若要阻止具有 internet 访问权限的用户从 internet 下载可更新帮助，请使用 **设置 update-help 的默认源路径** 组策略设置。

此组策略设置会将 **SourcePath** 参数（指定的文件系统位置）隐式添加到 `Update-Help` 每个受影响的计算机上的每个命令。 用户可以显式使用 **sourcepath** 参数来指定不同的文件系统位置，但不能排除 **SourcePath** 参数并从 internet 下载帮助。

> [!NOTE]
> " **设置 update-help 的默认源路径** " 组策略设置出现在 " **计算机配置** " 和 " **用户配置**" 下。 但是，只有 " **计算机配置** " 下的策略设置才有效。 " **用户配置** " 下的策略设置被忽略。

有关详细信息，请参阅 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。

## <a name="how-to-update-help-for-non-standard-modules"></a>如何更新非标准模块的帮助

若要更新或保存 cmdlet 的 **ListAvailable** 参数未返回的模块的帮助 `Get-Module` ，请在运行或命令之前将模块导入到当前会话中 `Update-Help` `Save-Help` 。 在远程计算机上运行命令之前，请将 `Save-Help` 模块导入到当前会话中，或导入 `Invoke-Command` 连接到远程计算机的脚本块。

当模块在当前会话中时，请运行 `Update-Help` `Save-Help` 不带参数的或 cmdlet，或者使用 **module** 参数来指定模块名称。

和 cmdlet 的 **模块** 参数 `Update-Help` `Save-Help` 仅接受模块名称。 它们不接受模块文件的路径。

使用此方法来更新或保存 cmdlet 的 **ListAvailable** 参数未返回的任何模块的帮助 `Get-Module` ，如安装在环境变量中未列出的位置的模块 `$env:PSModulePath` ，或模块目录不包含格式不正确的模块 (模块目录不包含至少一个 basename 与目录) 名称相同的文件。

## <a name="how-to-support-updatable-help"></a>如何支持可更新帮助

如果创建模块，则可以支持模块的联机帮助和可更新帮助。 有关详细信息，请参阅 Microsoft Docs 中的 [支持可更新帮助](/powershell/scripting/developer/help/supporting-updatable-help) 和 [支持联机帮助](/powershell/scripting/developer/module/supporting-online-help) 。

适用于 PowerShell 管理单元或基于注释的帮助的可更新帮助。

## <a name="remarks"></a>备注

`Update-Help` `Save-Help` (Windows PE) Windows 预安装环境上不支持和 cmdlet。

## <a name="see-also"></a>请参阅

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
