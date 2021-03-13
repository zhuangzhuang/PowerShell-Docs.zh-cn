---
description: PowerShell 的配置文件，替换注册表配置。
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: e6688e91f0cf14ae54a0585ae199f098e98e1146
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412958"
---
# <a name="about-powershell-config"></a>关于 PowerShell 配置

## <a name="short-description"></a>简短说明
PowerShell Core 的配置文件，替换注册表配置。

## <a name="long-description"></a>详细说明

此 `powershell.config.json` 文件包含 PowerShell Core 的配置设置。 PowerShell 会在启动时加载此配置。 还可以在运行时修改这些设置。 以前，这些设置存储在 PowerShell 的 Windows 注册表中，但现在包含在文件中，可在 macOS 和 Linux 上启用配置。

> [!WARNING]
> 无法识别的密钥或配置文件中的无效值将以无提示方式忽略。 如果 `powershell.config.json` 文件包含无效的 JSON，则 PowerShell 无法启动交互式会话。 如果出现这种情况，则必须修复配置文件。

### <a name="allusers-shared-configuration"></a>AllUsers (共享) 配置

`powershell.config.json`目录中的文件 `$PSHOME` 定义了从该 PowerShell core 安装中运行的所有 powershell core 会话的配置。

> [!NOTE]
> 此 `$PSHOME` 位置定义为与执行 System.Management.Automation.dll 程序集相同的目录。 这也适用于托管的 PowerShell SDK 实例。

### <a name="currentuser-per-user-configurations"></a>CurrentUser (每用户) 配置

还可以通过将文件放在用户范围配置目录中，按用户配置 PowerShell。 可以通过命令跨平台找到用户配置目录 `Split-Path $PROFILE.CurrentUserCurrentHost` 。

## <a name="general-configuration-settings"></a>常规配置设置

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> 此配置仅适用于 Windows 平台。

为 PowerShell 会话配置执行策略，确定可运行的脚本。 默认情况下，PowerShell 使用现有的执行策略。

对于 AllUsers 配置，这将设置 **LocalMachine** 执行策略。
对于 CurrentUser 配置，此设置为 **currentuser** 执行策略。

> [!NOTE]
> [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)Cmdlet 在调用时修改 AllUsers 配置文件中的此设置 `-Scope LocalMachine` ，并在调用时修改 CurrentUser 配置文件中的此设置 `-Scope CurrentUser` 。

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

其中：

- `<shell-id>` 引用当前 PowerShell 主机的 ID。 对于普通的 PowerShell 核心，这是 `Microsoft.PowerShell` 。 在任何 PowerShell 会话中，你都可以通过发现它 `$ShellId` 。
- `<execution-policy>` 引用有效的执行策略名称。

下面的示例将 PowerShell 的执行策略设置为 `RemoteSigned` 。

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

在 Windows 中，可在和中找到等效的注册表项 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` 。

### <a name="psmodulepath"></a>PSModulePath

替代 `PSModulePath` 此 PowerShell 会话的设置。 如果配置针对当前用户，则设置 **CurrentUser** 模块路径。 如果为所有用户配置，则会设置 **AllUsers** 模块路径。

> [!WARNING]
> 如果在此处配置 **AllUsers** 或 **CurrentUser** 模块路径，则不会更改 PowerShellGet cmdlet （如 [Install-module）](/powershell/module/powershellget/install-module)的作用域安装位置。 这些 cmdlet 始终使用 _默认_ 模块路径。

如果未设置任何值，则 PowerShell 将使用各自模块路径设置的默认值。 有关这些默认设置的详细信息，请参阅 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath)。

此设置允许使用环境变量，方法是在字符之间嵌入它们 `%` ，就像使用 `"%HOME%\Documents\PowerShell\Modules"` CMD 所允许的相同方式。 此语法还适用于 Linux 和 macOS。 有关示例，请参阅下面的示例。

```Schema
"PSModulePath": "<ps-module-path>"
```

其中：

- `<ps-module-path>` 模块目录的绝对路径。 对于所有用户配置，这是 AllUsers 共享模块目录。 对于当前用户配置，此为 CurrentUser 模块目录。

此示例演示 `PSModulePath` Windows 环境的配置：

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

此示例显示了 `PSModulePath` macOS 或 Linux 环境的配置：

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

此示例演示如何在配置中嵌入环境变量 `PSModulePath` 。 请注意，使用 `HOME` 环境变量和 `/` 目录分隔符时，这将适用于 Windows、MacOS 和 Linux。

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

此示例演示如何将环境变量嵌入到 `PSModulePath` 仅适用于 macOS 和 Linux 的配置中：

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> PowerShell 变量不能嵌入到 `PSModulePath` 配置中。
> `PSModulePath` Linux 和 macOS 上的配置区分大小写。 `PSModulePath`配置必须为平台使用有效的目录分隔符。 在 macOS 和 Linux 上，这表示 `/` 。 在 Windows 上， `/` 和都 `\` 适用。

### <a name="experimentalfeatures"></a>ExperimentalFeatures

要在 PowerShell 中启用的实验功能的名称。 默认情况下，不启用实验性功能。 默认值为空数组。

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

其中：

- `<experimental-feature-name>` 要启用的实验功能的名称。

以下示例在 PowerShell 启动时启用 **PSImplicitRemoting** 和 **PSUseAbbreviationExpansion** 实验功能。

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

有关实验功能的详细信息，请参阅 [使用实验性功能](/powershell/scripting/learn/experimental-features)。

## <a name="non-windows-logging-configuration"></a>非 Windows 日志记录配置

> [!IMPORTANT]
> 本部分中的配置选项仅适用于 macOS 和 Linux。
> Windows 的日志记录由 Windows 事件查看器管理。

可以在 PowerShell 配置文件中配置 PowerShell 在 macOS 和 Linux 上的日志记录。 有关非 Windows 系统的 PowerShell 日志记录的完整说明，请参阅 [关于日志记录](./about_Logging_Non-Windows.md)。

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> 此设置仅可用于 macOS 和 Linux。

设置用于写入系统日志的标识名称。 默认值为 "powershell"。

```Schema
"LogIdentity": "<log-identity>"
```

其中：

- `<log-identity>` PowerShell 应用于写入 syslog 的字符串标识。

> [!NOTE]
> 对于已安装的每个不同的 PowerShell 实例，你可能想要使用不同的 **LogIdentity** 值。

在此示例中，我们将配置 **LogIdentity** 用于 PowerShell 的预览版本。

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>LogLevel

> [!IMPORTANT]
> 此设置仅可用于 macOS 和 Linux。

指定 PowerShell 应记录的最小严重性级别。

```Schema
"LogLevel": "<log-level>|default"
```

其中：

- `<log-level>` 是下列项之一：
  - 始终
  - 严重
  - 错误
  - 警告
  - 信息
  - 详细
  - 调试

> [!NOTE]
> 设置日志级别会启用其上方的所有日志级别。

将此设置设置为 " **默认** 值" 将被解释为默认值。
默认值为 " **信息**"。

下面的示例将值设置为 **Verbose**。

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> 此设置仅可用于 macOS 和 Linux。

确定启用了哪些日志记录通道。

```Schema
"LogChannels": "<log-channel>,..."
```

其中：

- `<log-channel>` 是下列项之一：
  - 操作-记录有关 PowerShell 活动的基本信息
  - 分析-记录更详细的诊断信息

默认值为 " **运行**"。 若要同时启用这两个通道，请将这两个值作为一个逗号分隔的字符串。 例如：

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> 此设置仅可用于 macOS 和 Linux。

确定要记录的 PowerShell 部分。 默认情况下，所有日志关键字均已启用。 若要启用多个关键字，请在一个逗号分隔的字符串中列出这些值。

```Schema
"LogKeywords": "<log-keyword>,..."
```

其中：

- `<log-keyword>` 是下列项之一：
  - 运行空间管理
  - 管道管道操作
  - 协议通信协议处理，如 PSRP
  - 传输层支持，如 SSH
  - 主机 PowerShell 主机功能，例如控制台交互
  - Cmdlet-PowerShell 内置 cmdlet
  - 序列化程序序列化逻辑
  - 会话-PowerShell 会话状态
  - ManagedPlugin-WSMan 插件

> [!NOTE]
> 通常建议不要设置此值，除非您尝试在 PowerShell 的已知部分中诊断特定行为。 更改此值只会减少记录的信息量。

此示例将日志记录限制为运行空间操作、管道逻辑和 cmdlet 使用。 将忽略所有其他日志记录。

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>更多示例配置

### <a name="example-windows-configuration"></a>Windows 配置示例

此配置明确设置了更多的设置：

- 此 PowerShell 安装的执行策略是 `AllSigned`
- CurrentUser 模块路径设置为共享驱动器上的模块目录
- `PSImplicitRemotingBatching`已启用实验性功能

> [!NOTE]
> `ExecutionPolicy`此处的和 `PSModulePath` 设置仅适用于 Windows 平台，因为模块路径使用 `\` 和 `;` 分隔符字符，而执行策略不 `Unrestricted` (在类似于 UNIX 的平台上允许的唯一策略) 。

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>非 Windows 配置示例

此配置设置仅适用于 macOS 或 Linux 的多种选项：

- CurrentUser 模块路径已设置为中的自定义模块目录 `$HOME`
- **PSImplicitRemotingBatching** 实验功能已启用
- PowerShell 日志记录级别设置为 " **详细**"，以提供更多日志记录
- 此 PowerShell 安装使用 **home PowerShell** 标识写入日志。

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>另请参阅

[关于执行策略](./about_Execution_Policies.md)

[关于自动变量](./about_Automatic_Variables.md)
