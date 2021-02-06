---
description: 介绍如何安装、导入和使用 PowerShell 模块。
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: b98c8b27b68c213ac43fbd350ecd920f813dec6b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2020
ms.locfileid: "99599071"
---
# <a name="about-modules"></a>关于模块

## <a name="short-description"></a>简短说明
介绍如何安装、导入和使用 PowerShell 模块。

## <a name="long-description"></a>详细说明

模块是一个包，其中包含 PowerShell 成员，例如 cmdlet、提供程序、函数、工作流、变量和别名。

编写命令的人可以使用模块来组织其命令并与他人共享。 接收模块的人可以将模块中的命令添加到其 PowerShell 会话，并像使用内置命令一样使用它们。

本主题介绍如何使用 PowerShell 模块。 有关如何编写 PowerShell 模块的详细信息，请参阅 [编写 Powershell 模块](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。

## <a name="what-is-a-module"></a>什么是模块？

模块是一个包，其中包含 PowerShell 成员，例如 cmdlet、提供程序、函数、工作流、变量和别名。 此包的成员可以在 PowerShell 脚本、已编译的 DLL 或二者的组合中实现。 这些文件通常在单个目录中组合在一起。 有关详细信息，请参阅 SDK 文档中的 [了解 Windows PowerShell 模块](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) 。

## <a name="module-auto-loading"></a>模块自动加载

从 PowerShell 3.0 开始，在已安装的模块中首次运行任何命令时，PowerShell 会自动导入模块。 现在，你可以在没有任何设置或配置文件配置的情况下使用模块中的命令，因此在计算机上安装模块后，无需再对其进行管理。

模块中的命令也更易于查找。 该 `Get-Command` cmdlet 现在获取所有已安装模块中的所有命令，即使它们尚未处于会话中也是如此。 你可以找到命令并使用它，而无需首先导入模块。

下面的每个示例都将使包含的 CimCmdlets 模块 `Get-CimInstance` 导入到会话中。

- 运行命令

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- 获取命令

  ```powershell
  Get-Command Get-CimInstance
  ```

- 获取有关命令的帮助

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` 包含通配符的命令 (`*`) 视为用于发现，不使用，不导入任何模块。

仅自动导入存储在由 PSModulePath 环境变量指定的位置中的模块。 必须通过运行 cmdlet 来导入其他位置中的模块 `Import-Module` 。

此外，使用 PowerShell 提供程序的命令不会自动导入模块。 例如，如果你使用需要 WSMan：驱动器的命令（如 `Get-PSSessionConfiguration` cmdlet），则可能需要运行 `Import-Module` cmdlet 以导入包含驱动器的 **Microsoft. 管理** 模块 `WSMan:` 。

你仍可以运行 `Import-Module` 命令来导入模块，并使用该 `$PSModuleAutoloadingPreference` 变量来启用、禁用和配置模块的自动导入。 有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

## <a name="how-to-use-a-module"></a>如何使用模块

若要使用模块，请执行以下任务：

1. 安装模块。 （通常已为你完成这一步。）
1. 找到模块所添加的命令。
1. 使用模块所添加的命令。

本主题介绍了如何执行这些任务。 它还包括有关管理模块的其他有用信息。

## <a name="how-to-install-a-module"></a>如何安装模块

如果接收到的模块中包含文件，则需要将其安装到计算机上，然后才能在 PowerShell 中使用它。

已为你安装好大多数模块。 PowerShell 附带几个预安装的模块，有时称为 _核心_ 模块。 在基于 Windows 的计算机上，如果操作系统附带的功能具有用于管理它们的 cmdlet，则会预安装这些模块。 在安装 Windows 功能时，可以使用服务器管理器中的 "添加角色和功能向导"，或在 "控制面板" 的 "打开或关闭 Windows 功能" 对话框中安装所有作为功能组成部分的 PowerShell 模块。 许多其他模块随附在用于安装模块的安装程序中。

使用以下命令为当前用户创建 **模块** 目录：

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

将整个模块文件夹复制到 Modules 目录中。 可以使用任何方法复制文件夹，包括 Windows 资源管理器和 Cmd.exe，以及 PowerShell。 在 PowerShell 中使用 `Copy-Item` cmdlet。 例如，要将中的 MyModule 文件夹复制 `C:\ps-test\MyModule` 到模块目录，请键入：

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

你可以在任何位置上安装模块，但在默认模块位置中安装模块可使其更易于管理。 有关默认模块位置的详细信息，请参阅 [module 和 DSC 资源位置和 PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) 部分。

## <a name="how-to-find-installed-modules"></a>如何查找已安装的模块

若要查找已安装在默认模块位置中但尚未导入到会话中的模块，请键入：

```powershell
Get-Module -ListAvailable
```

若要查找已导入到会话中的模块，请在 PowerShell 提示符下键入：

```powershell
Get-Module
```

有关 cmdlet 的详细信息 `Get-Module` ，请参阅 [get-help](xref:Microsoft.PowerShell.Core.Get-Module)。

## <a name="how-to-find-the-commands-in-a-module"></a>如何查找模块中的命令

使用 `Get-Command` cmdlet 查找所有可用的命令。 可以使用 cmdlet 的参数 `Get-Command` 按模块、名称和名词来筛选命令。

若要查找模块中的所有命令，请键入：

```powershell
Get-Command -Module <module-name>
```

例如，若要查找 BitsTransfer 模块中的命令，请键入：

```powershell
Get-Command -Module BitsTransfer
```

有关 cmdlet 的详细信息 `Get-Command` ，请参阅 [获取-命令](xref:Microsoft.PowerShell.Core.Get-Command)。

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>如何获取有关模块中的命令的帮助

如果模块包含它所导出的命令的帮助文件，则该 `Get-Help` cmdlet 将显示帮助主题。 使用用于 `Get-Help` 获取 PowerShell 中任何命令的帮助的相同命令格式。

从 PowerShell 3.0 开始，你可以下载模块的帮助文件，并下载帮助文件的更新，以使它们永远不会过时。

若要获取有关模块中的命令的帮助，请键入：

```powershell
Get-Help <command-name>
```

若要获取模块中命令的联机帮助，请键入：

```powershell
Get-Help <command-name> -Online
```

若要下载并安装模块中的命令的帮助文件，请键入：

```powershell
Update-Help -Module <module-name>
```

有关详细信息，请参阅 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 和 [update-help](xref:Microsoft.PowerShell.Core.Update-Help)。

## <a name="how-to-import-a-module"></a>如何导入模块

你可能需要导入模块或导入模块文件。 如果模块未安装在由 **PSModulePath** 环境变量指定的位置， `$env:PSModulePath` 或者模块包含文件（例如 .dll 或 hbase-runner.psm1 文件），而不是作为文件夹传递的典型模块，则需要导入。

你还可以选择导入模块，以便可以使用命令的参数 `Import-Module` ，如 Prefix 参数，该参数可将一个特殊前缀添加到所有已导入命令的名词名称中，或 **NoClobber** 参数，这会阻止模块添加会隐藏或替换会话中的现有命令的命令。

若要导入模块，请使用 `Import-Module` cmdlet。

若要将 PSModulePath 位置中的模块导入到当前会话中，请使用以下命令格式。

```powershell
Import-Module <module-name>
```

例如，以下命令将 BitsTransfer 模块导入到当前会话中。

```powershell
Import-Module BitsTransfer
```

若要导入不在默认模块位置中的模块，请使用指向命令中的模块文件夹的完全限定的路径。

例如，若要将目录中的 TestCmdlets 模块添加 `C:\ps-test` 到会话中，请键入：

```powershell
Import-Module C:\ps-test\TestCmdlets
```

若要导入未包含在模块文件夹中的模块文件，请使用指向命令中的模块文件的完全限定的路径。

例如，若要将目录中的 TestCmdlets.dll 模块添加 `C:\ps-test` 到会话中，请键入：

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

有关向会话添加模块的详细信息，请参阅 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)。

## <a name="how-to-import-a-module-into-every-session"></a>如何将模块导入到每个会话中

`Import-Module`命令将模块导入当前 PowerShell 会话。 若要将模块导入到启动的每个 PowerShell 会话，请将 `Import-Module` 命令添加到 powershell 配置文件。

有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。

## <a name="how-to-remove-a-module"></a>如何删除模块

当你删除模块时，该模块所添加的命令将从会话中删除。

若要从会话中删除模块，请使用以下命令格式。

```powershell
Remove-Module <module-name>
```

例如，以下命令将从当前会话中删除 BitsTransfer 模块。

```powershell
Remove-Module BitsTransfer
```

删除模块与导入模块的操作相反。 删除模块不会卸载该模块。 有关详细信息，请参阅 [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module)。

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>模块和 DSC 资源位置以及 PSModulePath

`$env:PSModulePath`环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。

默认情况下，分配到的有效位置 `$env:PSModulePath` 为：

- 系统范围内的位置： `$PSHOME\Modules`

  这些文件夹包含 Windows 和 PowerShell 附带的模块。

  PowerShell 附带的 DSC 资源存储在 `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` 文件夹中。

- 特定于用户的模块：这些是用户在用户范围中安装的模块。 `Install-Module` 具有 **作用域** 参数，该参数可用于指定是为当前用户还是为所有用户安装该模块。 有关详细信息，请参阅 [Install-Module](xref:PowerShellGet.Install-Module)。

  Windows 上用户特定的 **CurrentUser** 位置是 `PowerShell\Modules` 位于用户配置文件的 " **文档** " 位置中的文件夹。 该位置的特定路径因 Windows 版本而异，无论是否正在使用文件夹重定向。 Microsoft OneDrive 还可以更改 **文档** 文件夹的位置。

  默认情况下，在 Windows 10 上，该位置是 `$HOME\Documents\PowerShell\Modules` 。 在 Linux 或 Mac 上， **CurrentUser** 位置是 `$HOME/.local/share/powershell/Modules` 。

  > [!NOTE]
  > 可以使用以下命令来验证 **Documents** 文件夹的位置： `[Environment]::GetFolderPath('MyDocuments')` 。

- **AllUsers** 位置 `$env:PROGRAMFILES\PowerShell\Modules` 在 Windows 上。 在 Linux 或 Mac 上，模块存储在中 `/usr/local/share/powershell/Modules` 。

> [!NOTE]
> 若要在目录中添加或更改文件 `$env:Windir\System32` ，请以 "以 **管理员身份运行** " 选项启动 PowerShell。

可以通过更改 **PSModulePath** 环境变量的值来更改系统上的默认模块位置 `$Env:PSModulePath` 。 **PSModulePath** 环境变量在 Path 环境变量上建模，具有相同的格式。

若要查看默认模块位置，请键入：

```powershell
$Env:PSModulePath
```

若要添加默认模块位置，请使用以下命令格式。

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

命令中的分号 (`;`) 将新路径与列表中其前面的路径分隔开。

例如，若要添加 `C:\ps-test\Modules` 目录，请键入：

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

若要在 Linux 或 MacOS 上添加默认模块位置，请使用以下命令格式：

```powershell
$Env:PSModulePath += ":<path>"
```

例如，若要将 `/usr/local/Fabrikam/Modules` 目录添加到 **PSModulePath** 环境变量的值，请键入：

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

在 Linux 或 MacOS 上，命令中的冒号 (`:`) 将新路径与列表中其前面的路径分隔开。

将路径添加到 **PSModulePath** 时， `Get-Module` 和 `Import-Module` 命令包括该路径中的模块。

你所设置的值仅影响当前会话。 要使更改保持不变，请将命令添加到 PowerShell 配置文件，或使用控制面板中的 "系统" 来更改注册表中的 **PSModulePath** 环境变量的值。

此外，若要使更改保持不变，还可以使用 **SetEnvironmentVariable** **类的** 方法将路径添加到 **PSModulePath** 环境变量。

有关 **PSModulePath** 变量的详细信息，请参阅 [about_Environment_Variables](about_Environment_Variables.md)。

## <a name="modules-and-name-conflicts"></a>模块和名称冲突

当会话中的多个命令具有相同的名称时，会发生名称冲突。 当模块中的命令与会话中的命令或项具有相同名称时，导入模块将引起名称冲突。

名称冲突可能会导致命令被隐藏或替换。

### <a name="hidden"></a>Hidden

当某个命令不是键入命令名称后所运行的命令时，该命令将隐藏，但你可以使用另一种方法来运行它，例如通过使用模块名称或创建它的管理单元的名称来限定命令名称。

### <a name="replaced"></a>已替换

当由于具有相同名称的命令已覆盖某个命令而无法运行该命令时，该命令即被替换。 即使删除导致冲突的模块，也无法运行替换的命令，除非重新启动该会话。

`Import-Module` 可以添加用于隐藏和替换当前会话中的命令的命令。 此外，你的会话中的命令可以隐藏模块所添加的命令。

若要检测名称冲突，请使用 cmdlet 的 **All** 参数 `Get-Command` 。 从 PowerShell 3.0 开始， `Get-Command` 仅获取键入命令名称时运行的命令。 **All** 参数获取会话中具有特定名称的所有命令。

若要防止名称冲突，请使用 cmdlet 的 **NoClobber** 或 **Prefix** 参数 `Import-Module` 。 **Prefix** 参数将前缀添加到已导入命令的名称，以便它们在会话中是唯一的。 **NoClobber** 参数不会导入任何将隐藏或替换会话中的现有命令的命令。

你还可以使用的 **Alias**、 **Cmdlet**、 **Function** 和 **Variable** 参数 `Import-Module` 来仅选择要导入的命令，并且可以排除在会话中引起名称冲突的命令。

模块作者可以通过使用模块清单的 **DefaultCommandPrefix** 属性来将默认前缀添加到所有命令名称，从而防止名称冲突。
**Prefix** 参数的值优先于 **DefaultCommandPrefix** 的值。

即使命令处于隐藏状态，你也可以通过使用模块名称或创建该模块的管理单元名称来限定命令名称，从而运行该命令。

PowerShell 命令优先规则确定当会话中包含具有相同名称的命令时运行哪个命令。

例如，当会话中包含具有相同名称的函数和 cmdlet 时，默认情况下，PowerShell 将运行该函数。 当会话中包含同一类型的同名命令时（例如具有相同名称的两个 cmdlet），它将在默认情况下运行最新添加的命令。

有关详细信息，包括优先规则的说明和运行隐藏命令的说明，请参阅 [about_Command_Precedence](about_Command_Precedence.md)。

## <a name="modules-and-snap-ins"></a>模块和管理单元

你可以从模块和管理单元向会话中添加命令。模块可以添加所有类型的命令，包括 cmdlet、提供程序、函数和项（例如变量、别名和 PowerShell 驱动器）。 管理单元只可以添加 cmdlet 和提供程序。

在从会话中删除模块或管理单元之前，请使用以下命令来确定将删除哪些命令。

若要在会话中查找某个 cmdlet 的源，请使用以下命令格式：

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

例如，若要查找 cmdlet 的源 `Get-Date` ，请键入：

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a>与模块相关的警告和错误

模块导出的命令应遵循 PowerShell 命令命名规则。 如果导入的模块导出名称中包含未经批准的谓词的 cmdlet 或函数，则该 `Import-Module` cmdlet 将显示以下警告消息。

> 警告：某些导入的命令名称包括未经批准的动词，这可能会使它们更易发现。 请使用 Verbose 参数获取详细信息或者键入 Get-Verb 以查看批准的谓词列表。

此消息只是一个警告。 仍将导入完整的模块，其中包括非一致性的命令。 尽管会向模块用户显示消息，但是模块作者应修复命名问题。

若要禁止显示警告消息，请使用 cmdlet 的 **DisableNameChecking** 参数 `Import-Module` 。

## <a name="built-in-modules-and-snap-ins"></a>内置模块和管理单元

在 PowerShell 2.0 和 PowerShell 3.0 和更高版本的旧式主机程序中，随 PowerShell 一起安装的核心命令打包在自动添加到每个 PowerShell 会话的管理单元中。

从 PowerShell 3.0 开始，对于实现 `InitialSessionState.CreateDefault2` 初始会话状态 API 的主机程序，默认情况下会将 "Microsoft" 管理单元添加到每个会话中。 首次使用时，模块会自动加载。

> [!NOTE]
> 远程会话（包括使用 cmdlet 启动的会话） `New-PSSession` 是旧样式的会话，其中内置命令打包在管理单元中。

以下模块 (或与 PowerShell 一起安装) 的管理单元。

- CimCmdlet
- Microsoft.PowerShell.Archive
- Microsoft.PowerShell.Core
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSReadline

## <a name="logging-module-events"></a>记录模块事件

从 PowerShell 3.0 开始，你可以通过将模块和管理单元的 **LogPipelineExecutionDetails** 属性设置为来记录 powershell 模块和管理单元中的 cmdlet 和函数的执行事件 `$True` 。
你还可以使用组策略设置，启用模块日志记录，以便在所有 PowerShell 会话中启用模块日志记录。 有关详细信息，请参阅日志记录和组策略文章。

## <a name="see-also"></a>另请参阅

[about_Logging_Windows](about_Logging_Windows.md)

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)

[Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module)
