---
description: 描述 PowerShell 的组策略设置
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 5ca13d22c69213dd8bae57a0dd08587c9c2b1541
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598452"
---
# <a name="about-group-policy-settings"></a>关于组策略设置

## <a name="short-description"></a>简短说明
描述 PowerShell 的组策略设置

## <a name="long-description"></a>长说明

PowerShell 包括组策略设置，可帮助你为企业环境中的 Windows 计算机定义一致的配置值。

PowerShell 组策略设置如下组策略路径：

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

用户配置路径中的组策略设置优先于计算机配置路径中组策略设置。

PowerShell 7 在 `$PSHOME` 中添加组策略模板和安装脚本。

组策略工具使用管理模板文件（`.admx`、`.adml`），以在用户界面中填充策略设置。 这样，管理员就能管理基于注册表的策略设置。 `InstallPSCorePolicyDefinitions.ps1`脚本会在本地计算机上安装 **PowerShell Core 管理模板**。

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

安装模板后，你可以在组策略编辑器 () 中编辑这些设置 `gpedit.msc` 。

策略如下：

- 控制台会话配置：设置运行 PowerShell 的配置终结点。
- 启用模块日志记录：设置模块的 **LogPipelineExecutionDetails** 属性。
- 启用 Power Shell 脚本块日志记录：启用所有 PowerShell 脚本的详细日志记录。
- 启用脚本执行：设置 PowerShell 执行策略。
- 启用 PowerShell 脚本：可便于将 PowerShell 命令输入和输出捕获到基于文本的脚本中。
- 设置的默认源路径 `Update-Help` ：将可更新帮助的源设置为目录，而不是 Internet。

每个 PowerShell 组策略设置都有一个选项 ( "使用 Windows PowerShell 策略设置" 字段，) 使用位于以下组策略路径中的类似 Windows PowerShell 组策略设置中的值：

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> 这些 **Powershell Core 管理模板** 不包括适用于 Windows PowerShell 的设置。 有关获取其他模板和配置组策略的详细信息，请参阅 [如何在 Windows 中为组策略管理模板创建和管理中心存储][gpstore]。

## <a name="console-session-configuration"></a>控制台会话配置

**控制台会话配置** 策略设置指定运行 PowerShell 的配置终结点。 这可以是在本地计算机上注册的任何终结点，包括默认 PowerShell 远程处理终结点或具有特定用户角色功能的自定义终结点。

## <a name="turn-on-module-logging"></a>启用模块日志记录

" **打开模块日志记录** " 策略设置为所选 PowerShell 模块启用日志记录。 此设置在所有受影响的计算机上的所有会话中都有效。

如果启用此策略设置并指定一个或多个模块，则会在事件查看器的 Windows PowerShell 日志中记录指定模块的管道执行事件。

如果禁用此策略设置，则会为所有 PowerShell 模块禁用执行事件的日志记录。

如果未配置此策略设置，则每个模块的 **LogPipelineExecutionDetails** 属性将确定是否记录模块的执行事件。 默认情况下，所有模块的 **LogPipelineExecutionDetails** 属性都设置为 False。

若要为模块启用模块日志记录，请使用以下命令格式。 必须将模块导入到会话中，并且该设置仅在当前会话中有效。

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

若要为特定计算机上的所有会话启用模块日志记录，请将前面的命令添加到 "所有用户的 PowerShell 配置文件 (`$Profile.AllUsersAllHosts`) 。

有关模块日志记录的详细信息，请参阅 [about_Modules](about_Modules.md)。

## <a name="turn-on-powershell-script-block-logging"></a>启用 PowerShell 脚本块日志记录

" **打开 Powershell 脚本块日志记录** " 策略设置可将所有 PowerShell 脚本输入的日志记录到 Microsoft Windows PowerShell/操作事件日志中。 如果启用此策略设置，则 PowerShell Core 将记录命令、脚本块、函数和脚本的处理方式，无论是以交互方式调用还是通过自动化来处理。

如果禁用此策略设置，则将禁止记录 PowerShell 脚本输入。 如果启用脚本块调用日志记录，则 PowerShell 在调用命令、脚本块、函数或脚本启动或停止时还会记录事件。 启用调用日志记录时会生成大量事件日志。

## <a name="turn-on-script-execution"></a>启用脚本执行

" **打开脚本执行** " 策略设置可为计算机和用户设置执行策略，这将确定允许运行哪些脚本。

如果启用策略设置，则可以从以下策略设置中进行选择。

- 仅 **允许已签名的脚本** 仅允许脚本通过受信任的发布者签名。 此策略设置等效于 AllSigned 执行策略。

- **允许本地脚本和远程签名的脚本** 允许运行所有本地脚本。 来自 Internet 的脚本必须由受信任的发布者签名。 此策略设置等效于 RemoteSigned 执行策略。

- **允许** 所有脚本都允许运行所有脚本。 此策略设置等效于不受限制的执行策略。

如果禁用此策略设置，则不允许运行脚本。 此策略设置等效于受限制的执行策略。

如果禁用或未配置此策略设置，则由 cmdlet 为计算机或用户设置的执行策略将 `Set-ExecutionPolicy` 确定是否允许运行脚本。 默认值为 Restricted。

有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

## <a name="turn-on-powershell-transcription"></a>启用 powershell 脚本

" **打开 powershell** 脚本" 策略设置允许你将 PowerShell 核心命令的输入和输出捕获到基于文本的脚本中。 如果启用此策略设置，则 PowerShell Core 将为 PowerShell Core 和任何其他利用 PowerShell 核心引擎的应用程序启用脚本日志记录。 默认情况下，PowerShell Core 会将脚本输出记录到每个用户的 "我的文档" 目录中，文件名中包含 "PowerShell_transcript"，以及计算机名称和启动时间。
启用此策略等效于对每个 PowerShell 核心会话调用 Start-Transcript cmdlet。

如果禁用此策略设置，则默认情况下将禁用基于 PowerShell 的应用程序的脚本日志记录，不过，脚本之外仍可通过 Start-Transcript cmdlet 启用。

如果使用 OutputDirectory 设置启用到共享位置的脚本日志记录，请确保限制对该目录的访问，以防止用户查看其他用户或计算机的脚本。

## <a name="set-the-default-source-path-for-update-help"></a>为 Update-Help 设置默认源路径

" **设置 update-help 的默认源路径** " 策略设置为 Cmdlet 的 **SourcePath** 参数设置默认值 `Update-Help` 。
此设置可防止用户使用 `Update-Help` cmdlet 从 Internet 下载帮助文件。

> [!NOTE]
> 此组策略设置将出现在 " **计算机配置** " 和 " **用户配置**" 下。 但是，只有 " **计算机配置** " 下的组策略设置才有效。 " **用户配置** " 下的组策略设置将被忽略。

`Update-Help`Cmdlet 将下载并安装最新的 PowerShell 模块帮助文件，并将它们安装在计算机上。 默认情况下， `Update-Help` 从模块指定的 Internet 位置下载新帮助文件。

但是，可以使用 cmdlet 将 `Save-Help` 最新的帮助文件下载到文件系统位置（如网络共享），然后使用 `Update-Help` cmdlet 从文件系统位置获取帮助文件，并将它们安装在计算机上。 此 cmdlet 的 **SourcePath** 参数 `Update-Help` 指定文件系统位置。

通过为 **SourcePath** 参数提供默认值，此组策略设置会将 **sourcepath** 参数隐式添加到所有 `Update-Help` 命令。 用户可以通过输入其他文件系统位置，替代指定为默认值的特定文件系统位置。
但不能从命令中删除 **SourcePath** 参数 `Update-Help` 。

如果启用此策略设置，则可以为 **SourcePath** 参数指定默认值。 输入文件系统位置。

如果禁用或未配置此策略设置，则不会对此 cmdlet 的 **SourcePath** 参数提供默认值 `Update-Help` 。 用户可以从 Internet 或任何文件系统位置下载帮助。

有关详细信息，请参阅 [about_Updatable_Help](about_Updatable_Help.md)。

## <a name="keywords"></a>关键字

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>请参阅

[PowerShell Core 策略 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

