---
description: PowerShell 的配置文件，替换注册表配置。
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: 80ff02200b066c6f4f5eb355d5ed08894235e986
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412875"
---
# <a name="about-powershell-config"></a><span data-ttu-id="43982-103">关于 PowerShell 配置</span><span class="sxs-lookup"><span data-stu-id="43982-103">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="43982-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="43982-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="43982-105">PowerShell Core 的配置文件，替换注册表配置。</span><span class="sxs-lookup"><span data-stu-id="43982-105">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="43982-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="43982-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="43982-107">此 `powershell.config.json` 文件包含 PowerShell Core 的配置设置。</span><span class="sxs-lookup"><span data-stu-id="43982-107">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="43982-108">PowerShell 会在启动时加载此配置。</span><span class="sxs-lookup"><span data-stu-id="43982-108">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="43982-109">还可以在运行时修改这些设置。</span><span class="sxs-lookup"><span data-stu-id="43982-109">The settings can also be modified at runtime.</span></span> <span data-ttu-id="43982-110">以前，这些设置存储在 PowerShell 的 Windows 注册表中，但现在包含在文件中，可在 macOS 和 Linux 上启用配置。</span><span class="sxs-lookup"><span data-stu-id="43982-110">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="43982-111">无法识别的密钥或配置文件中的无效值将以无提示方式忽略。</span><span class="sxs-lookup"><span data-stu-id="43982-111">Unrecognized keys or invalid values in the configuration file are silently ignored.</span></span> <span data-ttu-id="43982-112">如果 `powershell.config.json` 文件包含无效的 JSON，则 PowerShell 无法启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="43982-112">If the `powershell.config.json` file contains invalid JSON, PowerShell cannot start an interactive session.</span></span> <span data-ttu-id="43982-113">如果出现这种情况，则必须修复配置文件。</span><span class="sxs-lookup"><span data-stu-id="43982-113">If this occurs, you must fix the configuration file.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="43982-114">AllUsers (共享) 配置</span><span class="sxs-lookup"><span data-stu-id="43982-114">AllUsers (shared) configuration</span></span>

<span data-ttu-id="43982-115">`powershell.config.json`目录中的文件 `$PSHOME` 定义了从该 PowerShell core 安装中运行的所有 powershell core 会话的配置。</span><span class="sxs-lookup"><span data-stu-id="43982-115">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="43982-116">此 `$PSHOME` 位置定义为与执行 System.Management.Automation.dll 程序集相同的目录。</span><span class="sxs-lookup"><span data-stu-id="43982-116">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="43982-117">这也适用于托管的 PowerShell SDK 实例。</span><span class="sxs-lookup"><span data-stu-id="43982-117">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="43982-118">CurrentUser (每用户) 配置</span><span class="sxs-lookup"><span data-stu-id="43982-118">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="43982-119">还可以通过将文件放在用户范围配置目录中，按用户配置 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="43982-119">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="43982-120">可以通过命令跨平台找到用户配置目录 `Split-Path $PROFILE.CurrentUserCurrentHost` 。</span><span class="sxs-lookup"><span data-stu-id="43982-120">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="43982-121">常规配置设置</span><span class="sxs-lookup"><span data-stu-id="43982-121">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="43982-122">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="43982-122">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-123">此配置仅适用于 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="43982-123">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="43982-124">为 PowerShell 会话配置执行策略，确定可运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="43982-124">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="43982-125">默认情况下，PowerShell 使用现有的执行策略。</span><span class="sxs-lookup"><span data-stu-id="43982-125">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="43982-126">对于 AllUsers 配置，这将设置 **LocalMachine** 执行策略。</span><span class="sxs-lookup"><span data-stu-id="43982-126">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="43982-127">对于 CurrentUser 配置，此设置为 **currentuser** 执行策略。</span><span class="sxs-lookup"><span data-stu-id="43982-127">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="43982-128">[`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)Cmdlet 在调用时修改 AllUsers 配置文件中的此设置 `-Scope LocalMachine` ，并在调用时修改 CurrentUser 配置文件中的此设置 `-Scope CurrentUser` 。</span><span class="sxs-lookup"><span data-stu-id="43982-128">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="43982-129">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-129">Where:</span></span>

- <span data-ttu-id="43982-130">`<shell-id>` 引用当前 PowerShell 主机的 ID。</span><span class="sxs-lookup"><span data-stu-id="43982-130">`<shell-id>` refers to the ID of the current PowerShell host.</span></span> <span data-ttu-id="43982-131">对于普通的 PowerShell 核心，这是 `Microsoft.PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="43982-131">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span> <span data-ttu-id="43982-132">在任何 PowerShell 会话中，你都可以通过发现它 `$ShellId` 。</span><span class="sxs-lookup"><span data-stu-id="43982-132">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="43982-133">`<execution-policy>` 引用有效的执行策略名称。</span><span class="sxs-lookup"><span data-stu-id="43982-133">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="43982-134">下面的示例将 PowerShell 的执行策略设置为 `RemoteSigned` 。</span><span class="sxs-lookup"><span data-stu-id="43982-134">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="43982-135">在 Windows 中，可在和中找到等效的注册表项 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` 。</span><span class="sxs-lookup"><span data-stu-id="43982-135">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="43982-136">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="43982-136">PSModulePath</span></span>

<span data-ttu-id="43982-137">替代 `PSModulePath` 此 PowerShell 会话的设置。</span><span class="sxs-lookup"><span data-stu-id="43982-137">Overrides the `PSModulePath` settings for this PowerShell session.</span></span> <span data-ttu-id="43982-138">如果配置针对当前用户，则设置 **CurrentUser** 模块路径。</span><span class="sxs-lookup"><span data-stu-id="43982-138">If the configuration is for the current user, sets the **CurrentUser** module path.</span></span> <span data-ttu-id="43982-139">如果为所有用户配置，则会设置 **AllUsers** 模块路径。</span><span class="sxs-lookup"><span data-stu-id="43982-139">If the configuration is for all users, sets the **AllUsers** module path.</span></span>

> [!WARNING]
> <span data-ttu-id="43982-140">如果在此处配置 **AllUsers** 或 **CurrentUser** 模块路径，则不会更改 PowerShellGet cmdlet （如 [Install-module）](/powershell/module/powershellget/install-module)的作用域安装位置。</span><span class="sxs-lookup"><span data-stu-id="43982-140">Configuring an **AllUsers** or **CurrentUser** module path here does not change the scoped installation location for PowerShellGet cmdlets like [Install-Module](/powershell/module/powershellget/install-module).</span></span> <span data-ttu-id="43982-141">这些 cmdlet 始终使用 _默认_ 模块路径。</span><span class="sxs-lookup"><span data-stu-id="43982-141">These cmdlets always use the _default_ module paths.</span></span>

<span data-ttu-id="43982-142">如果未设置任何值，则 PowerShell 将使用各自模块路径设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="43982-142">If no value is set, PowerShell uses the default value for the respective module path setting.</span></span> <span data-ttu-id="43982-143">有关这些默认设置的详细信息，请参阅 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath)。</span><span class="sxs-lookup"><span data-stu-id="43982-143">For more information about these defaults, see [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath).</span></span>

<span data-ttu-id="43982-144">此设置允许使用环境变量，方法是在字符之间嵌入它们 `%` ，就像使用 `"%HOME%\Documents\PowerShell\Modules"` CMD 所允许的相同方式。</span><span class="sxs-lookup"><span data-stu-id="43982-144">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way that CMD allows.</span></span> <span data-ttu-id="43982-145">此语法还适用于 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="43982-145">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="43982-146">有关示例，请参阅下面的示例。</span><span class="sxs-lookup"><span data-stu-id="43982-146">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="43982-147">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-147">Where:</span></span>

- <span data-ttu-id="43982-148">`<ps-module-path>` 模块目录的绝对路径。</span><span class="sxs-lookup"><span data-stu-id="43982-148">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="43982-149">对于所有用户配置，这是 AllUsers 共享模块目录。</span><span class="sxs-lookup"><span data-stu-id="43982-149">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="43982-150">对于当前用户配置，此为 CurrentUser 模块目录。</span><span class="sxs-lookup"><span data-stu-id="43982-150">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="43982-151">此示例演示 `PSModulePath` Windows 环境的配置：</span><span class="sxs-lookup"><span data-stu-id="43982-151">This example shows a `PSModulePath` configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="43982-152">此示例显示了 `PSModulePath` macOS 或 Linux 环境的配置：</span><span class="sxs-lookup"><span data-stu-id="43982-152">This example shows a `PSModulePath` configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="43982-153">此示例演示如何在配置中嵌入环境变量 `PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="43982-153">This example shows embedding an environment variable in a `PSModulePath` configuration.</span></span> <span data-ttu-id="43982-154">请注意，使用 `HOME` 环境变量和 `/` 目录分隔符时，这将适用于 Windows、MacOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-154">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="43982-155">此示例演示如何将环境变量嵌入到 `PSModulePath` 仅适用于 macOS 和 Linux 的配置中：</span><span class="sxs-lookup"><span data-stu-id="43982-155">This example shows embedding an environment variable in a `PSModulePath` configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="43982-156">PowerShell 变量不能嵌入到 `PSModulePath` 配置中。</span><span class="sxs-lookup"><span data-stu-id="43982-156">PowerShell variables cannot be embedded in `PSModulePath` configurations.</span></span>
> <span data-ttu-id="43982-157">`PSModulePath` Linux 和 macOS 上的配置区分大小写。</span><span class="sxs-lookup"><span data-stu-id="43982-157">`PSModulePath` configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="43982-158">`PSModulePath`配置必须为平台使用有效的目录分隔符。</span><span class="sxs-lookup"><span data-stu-id="43982-158">A `PSModulePath` configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="43982-159">在 macOS 和 Linux 上，这表示 `/` 。</span><span class="sxs-lookup"><span data-stu-id="43982-159">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="43982-160">在 Windows 上， `/` 和都 `\` 适用。</span><span class="sxs-lookup"><span data-stu-id="43982-160">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="43982-161">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="43982-161">ExperimentalFeatures</span></span>

<span data-ttu-id="43982-162">要在 PowerShell 中启用的实验功能的名称。</span><span class="sxs-lookup"><span data-stu-id="43982-162">The names of the experimental features to enable in PowerShell.</span></span> <span data-ttu-id="43982-163">默认情况下，不启用实验性功能。</span><span class="sxs-lookup"><span data-stu-id="43982-163">By default, no experimental features are enabled.</span></span> <span data-ttu-id="43982-164">默认值为空数组。</span><span class="sxs-lookup"><span data-stu-id="43982-164">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="43982-165">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-165">Where:</span></span>

- <span data-ttu-id="43982-166">`<experimental-feature-name>` 要启用的实验功能的名称。</span><span class="sxs-lookup"><span data-stu-id="43982-166">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="43982-167">以下示例在 PowerShell 启动时启用 **PSImplicitRemoting** 和 **PSUseAbbreviationExpansion** 实验功能。</span><span class="sxs-lookup"><span data-stu-id="43982-167">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="43982-168">有关实验功能的详细信息，请参阅 [使用实验性功能](/powershell/scripting/learn/experimental-features)。</span><span class="sxs-lookup"><span data-stu-id="43982-168">For more information on experimental features, see [Using experimental features](/powershell/scripting/learn/experimental-features).</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="43982-169">非 Windows 日志记录配置</span><span class="sxs-lookup"><span data-stu-id="43982-169">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-170">本部分中的配置选项仅适用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-170">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="43982-171">Windows 的日志记录由 Windows 事件查看器管理。</span><span class="sxs-lookup"><span data-stu-id="43982-171">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="43982-172">可以在 PowerShell 配置文件中配置 PowerShell 在 macOS 和 Linux 上的日志记录。</span><span class="sxs-lookup"><span data-stu-id="43982-172">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="43982-173">有关非 Windows 系统的 PowerShell 日志记录的完整说明，请参阅 [关于日志记录](./about_Logging_Non-Windows.md)。</span><span class="sxs-lookup"><span data-stu-id="43982-173">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="43982-174">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="43982-174">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-175">此设置仅可用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-175">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="43982-176">设置用于写入系统日志的标识名称。</span><span class="sxs-lookup"><span data-stu-id="43982-176">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="43982-177">默认值为 "powershell"。</span><span class="sxs-lookup"><span data-stu-id="43982-177">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="43982-178">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-178">Where:</span></span>

- <span data-ttu-id="43982-179">`<log-identity>` PowerShell 应用于写入 syslog 的字符串标识。</span><span class="sxs-lookup"><span data-stu-id="43982-179">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="43982-180">对于已安装的每个不同的 PowerShell 实例，你可能想要使用不同的 **LogIdentity** 值。</span><span class="sxs-lookup"><span data-stu-id="43982-180">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="43982-181">在此示例中，我们将配置 **LogIdentity** 用于 PowerShell 的预览版本。</span><span class="sxs-lookup"><span data-stu-id="43982-181">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="43982-182">LogLevel</span><span class="sxs-lookup"><span data-stu-id="43982-182">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-183">此设置仅可用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-183">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="43982-184">指定 PowerShell 应记录的最小严重性级别。</span><span class="sxs-lookup"><span data-stu-id="43982-184">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="43982-185">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-185">Where:</span></span>

- <span data-ttu-id="43982-186">`<log-level>` 是下列项之一：</span><span class="sxs-lookup"><span data-stu-id="43982-186">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="43982-187">始终</span><span class="sxs-lookup"><span data-stu-id="43982-187">Always</span></span>
  - <span data-ttu-id="43982-188">严重</span><span class="sxs-lookup"><span data-stu-id="43982-188">Critical</span></span>
  - <span data-ttu-id="43982-189">错误</span><span class="sxs-lookup"><span data-stu-id="43982-189">Error</span></span>
  - <span data-ttu-id="43982-190">警告</span><span class="sxs-lookup"><span data-stu-id="43982-190">Warning</span></span>
  - <span data-ttu-id="43982-191">信息</span><span class="sxs-lookup"><span data-stu-id="43982-191">Informational</span></span>
  - <span data-ttu-id="43982-192">详细</span><span class="sxs-lookup"><span data-stu-id="43982-192">Verbose</span></span>
  - <span data-ttu-id="43982-193">调试</span><span class="sxs-lookup"><span data-stu-id="43982-193">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="43982-194">设置日志级别会启用其上方的所有日志级别。</span><span class="sxs-lookup"><span data-stu-id="43982-194">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="43982-195">将此设置设置为 " **默认** 值" 将被解释为默认值。</span><span class="sxs-lookup"><span data-stu-id="43982-195">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="43982-196">默认值为 " **信息**"。</span><span class="sxs-lookup"><span data-stu-id="43982-196">The default value is **Informational**.</span></span>

<span data-ttu-id="43982-197">下面的示例将值设置为 **Verbose**。</span><span class="sxs-lookup"><span data-stu-id="43982-197">The following example sets the value to **Verbose**.</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="43982-198">LogChannels</span><span class="sxs-lookup"><span data-stu-id="43982-198">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-199">此设置仅可用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-199">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="43982-200">确定启用了哪些日志记录通道。</span><span class="sxs-lookup"><span data-stu-id="43982-200">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="43982-201">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-201">Where:</span></span>

- <span data-ttu-id="43982-202">`<log-channel>` 是下列项之一：</span><span class="sxs-lookup"><span data-stu-id="43982-202">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="43982-203">操作-记录有关 PowerShell 活动的基本信息</span><span class="sxs-lookup"><span data-stu-id="43982-203">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="43982-204">分析-记录更详细的诊断信息</span><span class="sxs-lookup"><span data-stu-id="43982-204">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="43982-205">默认值为 " **运行**"。</span><span class="sxs-lookup"><span data-stu-id="43982-205">The default value is **Operational**.</span></span> <span data-ttu-id="43982-206">若要同时启用这两个通道，请将这两个值作为一个逗号分隔的字符串。</span><span class="sxs-lookup"><span data-stu-id="43982-206">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="43982-207">例如：</span><span class="sxs-lookup"><span data-stu-id="43982-207">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="43982-208">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="43982-208">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43982-209">此设置仅可用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="43982-209">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="43982-210">确定要记录的 PowerShell 部分。</span><span class="sxs-lookup"><span data-stu-id="43982-210">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="43982-211">默认情况下，所有日志关键字均已启用。</span><span class="sxs-lookup"><span data-stu-id="43982-211">By default, all log keywords are enabled.</span></span> <span data-ttu-id="43982-212">若要启用多个关键字，请在一个逗号分隔的字符串中列出这些值。</span><span class="sxs-lookup"><span data-stu-id="43982-212">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="43982-213">其中：</span><span class="sxs-lookup"><span data-stu-id="43982-213">Where:</span></span>

- <span data-ttu-id="43982-214">`<log-keyword>` 是下列项之一：</span><span class="sxs-lookup"><span data-stu-id="43982-214">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="43982-215">运行空间管理</span><span class="sxs-lookup"><span data-stu-id="43982-215">Runspace - runspace management</span></span>
  - <span data-ttu-id="43982-216">管道管道操作</span><span class="sxs-lookup"><span data-stu-id="43982-216">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="43982-217">协议通信协议处理，如 PSRP</span><span class="sxs-lookup"><span data-stu-id="43982-217">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="43982-218">传输层支持，如 SSH</span><span class="sxs-lookup"><span data-stu-id="43982-218">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="43982-219">主机 PowerShell 主机功能，例如控制台交互</span><span class="sxs-lookup"><span data-stu-id="43982-219">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="43982-220">Cmdlet-PowerShell 内置 cmdlet</span><span class="sxs-lookup"><span data-stu-id="43982-220">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="43982-221">序列化程序序列化逻辑</span><span class="sxs-lookup"><span data-stu-id="43982-221">Serializer - serialization logic</span></span>
  - <span data-ttu-id="43982-222">会话-PowerShell 会话状态</span><span class="sxs-lookup"><span data-stu-id="43982-222">Session - PowerShell session state</span></span>
  - <span data-ttu-id="43982-223">ManagedPlugin-WSMan 插件</span><span class="sxs-lookup"><span data-stu-id="43982-223">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="43982-224">通常建议不要设置此值，除非您尝试在 PowerShell 的已知部分中诊断特定行为。</span><span class="sxs-lookup"><span data-stu-id="43982-224">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span> <span data-ttu-id="43982-225">更改此值只会减少记录的信息量。</span><span class="sxs-lookup"><span data-stu-id="43982-225">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="43982-226">此示例将日志记录限制为运行空间操作、管道逻辑和 cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="43982-226">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="43982-227">将忽略所有其他日志记录。</span><span class="sxs-lookup"><span data-stu-id="43982-227">All other logging will be omitted.</span></span>

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

## <a name="more-example-configurations"></a><span data-ttu-id="43982-228">更多示例配置</span><span class="sxs-lookup"><span data-stu-id="43982-228">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="43982-229">Windows 配置示例</span><span class="sxs-lookup"><span data-stu-id="43982-229">Example Windows configuration</span></span>

<span data-ttu-id="43982-230">此配置明确设置了更多的设置：</span><span class="sxs-lookup"><span data-stu-id="43982-230">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="43982-231">此 PowerShell 安装的执行策略是 `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="43982-231">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="43982-232">CurrentUser 模块路径设置为共享驱动器上的模块目录</span><span class="sxs-lookup"><span data-stu-id="43982-232">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="43982-233">`PSImplicitRemotingBatching`已启用实验性功能</span><span class="sxs-lookup"><span data-stu-id="43982-233">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="43982-234">`ExecutionPolicy`此处的和 `PSModulePath` 设置仅适用于 Windows 平台，因为模块路径使用 `\` 和 `;` 分隔符字符，而执行策略不 `Unrestricted` (在类似于 UNIX 的平台上允许的唯一策略) 。</span><span class="sxs-lookup"><span data-stu-id="43982-234">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="43982-235">非 Windows 配置示例</span><span class="sxs-lookup"><span data-stu-id="43982-235">Example non-Windows configuration</span></span>

<span data-ttu-id="43982-236">此配置设置仅适用于 macOS 或 Linux 的多种选项：</span><span class="sxs-lookup"><span data-stu-id="43982-236">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="43982-237">CurrentUser 模块路径已设置为中的自定义模块目录 `$HOME`</span><span class="sxs-lookup"><span data-stu-id="43982-237">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="43982-238">**PSImplicitRemotingBatching** 实验功能已启用</span><span class="sxs-lookup"><span data-stu-id="43982-238">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="43982-239">PowerShell 日志记录级别设置为 " **详细**"，以提供更多日志记录</span><span class="sxs-lookup"><span data-stu-id="43982-239">The PowerShell logging level is set to **Verbose**, for more logging</span></span>
- <span data-ttu-id="43982-240">此 PowerShell 安装使用 **home PowerShell** 标识写入日志。</span><span class="sxs-lookup"><span data-stu-id="43982-240">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="43982-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43982-241">See also</span></span>

[<span data-ttu-id="43982-242">关于执行策略</span><span class="sxs-lookup"><span data-stu-id="43982-242">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="43982-243">关于自动变量</span><span class="sxs-lookup"><span data-stu-id="43982-243">About Automatic Variables</span></span>](./about_Automatic_Variables.md)
