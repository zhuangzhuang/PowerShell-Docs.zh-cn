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
# <a name="about-group-policy-settings"></a><span data-ttu-id="ad9a8-103">关于组策略设置</span><span class="sxs-lookup"><span data-stu-id="ad9a8-103">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="ad9a8-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="ad9a8-104">Short description</span></span>
<span data-ttu-id="ad9a8-105">描述 PowerShell 的组策略设置</span><span class="sxs-lookup"><span data-stu-id="ad9a8-105">Describes the Group Policy settings for PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="ad9a8-106">长说明</span><span class="sxs-lookup"><span data-stu-id="ad9a8-106">Long description</span></span>

<span data-ttu-id="ad9a8-107">PowerShell 包括组策略设置，可帮助你为企业环境中的 Windows 计算机定义一致的配置值。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-107">PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="ad9a8-108">PowerShell 组策略设置如下组策略路径：</span><span class="sxs-lookup"><span data-stu-id="ad9a8-108">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

<span data-ttu-id="ad9a8-109">用户配置路径中的组策略设置优先于计算机配置路径中组策略设置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-109">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="ad9a8-110">PowerShell 7 在 `$PSHOME` 中添加组策略模板和安装脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-110">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="ad9a8-111">组策略工具使用管理模板文件（`.admx`、`.adml`），以在用户界面中填充策略设置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-111">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="ad9a8-112">这样，管理员就能管理基于注册表的策略设置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-112">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="ad9a8-113">`InstallPSCorePolicyDefinitions.ps1`脚本会在本地计算机上安装 **PowerShell Core 管理模板**。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-113">The `InstallPSCorePolicyDefinitions.ps1` script installs **PowerShell Core Administrative Templates** on the local machine.</span></span>

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

<span data-ttu-id="ad9a8-114">安装模板后，你可以在组策略编辑器 () 中编辑这些设置 `gpedit.msc` 。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-114">After installing the templates, you can edit these settings in the Group Policy editor (`gpedit.msc`).</span></span>

<span data-ttu-id="ad9a8-115">策略如下：</span><span class="sxs-lookup"><span data-stu-id="ad9a8-115">The policies are as follows:</span></span>

- <span data-ttu-id="ad9a8-116">控制台会话配置：设置运行 PowerShell 的配置终结点。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-116">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="ad9a8-117">启用模块日志记录：设置模块的 **LogPipelineExecutionDetails** 属性。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-117">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="ad9a8-118">启用 Power Shell 脚本块日志记录：启用所有 PowerShell 脚本的详细日志记录。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-118">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="ad9a8-119">启用脚本执行：设置 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-119">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="ad9a8-120">启用 PowerShell 脚本：可便于将 PowerShell 命令输入和输出捕获到基于文本的脚本中。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-120">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="ad9a8-121">设置的默认源路径 `Update-Help` ：将可更新帮助的源设置为目录，而不是 Internet。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-121">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="ad9a8-122">每个 PowerShell 组策略设置都有一个选项 ( "使用 Windows PowerShell 策略设置" 字段，) 使用位于以下组策略路径中的类似 Windows PowerShell 组策略设置中的值：</span><span class="sxs-lookup"><span data-stu-id="ad9a8-122">Each PowerShell Group Policy setting has an option ('Use Windows PowerShell Policy setting' field) to use the value from a similar Windows PowerShell Group Policy setting that is located in the following Group Policy paths:</span></span>

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
> <span data-ttu-id="ad9a8-123">这些 **Powershell Core 管理模板** 不包括适用于 Windows PowerShell 的设置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-123">These **PowerShell Core Administrative Templates** do not include settings for Windows PowerShell.</span></span> <span data-ttu-id="ad9a8-124">有关获取其他模板和配置组策略的详细信息，请参阅 [如何在 Windows 中为组策略管理模板创建和管理中心存储][gpstore]。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-124">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="console-session-configuration"></a><span data-ttu-id="ad9a8-125">控制台会话配置</span><span class="sxs-lookup"><span data-stu-id="ad9a8-125">Console session configuration</span></span>

<span data-ttu-id="ad9a8-126">**控制台会话配置** 策略设置指定运行 PowerShell 的配置终结点。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-126">The **Console session configuration** policy setting specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="ad9a8-127">这可以是在本地计算机上注册的任何终结点，包括默认 PowerShell 远程处理终结点或具有特定用户角色功能的自定义终结点。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-127">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="ad9a8-128">启用模块日志记录</span><span class="sxs-lookup"><span data-stu-id="ad9a8-128">Turn on module logging</span></span>

<span data-ttu-id="ad9a8-129">" **打开模块日志记录** " 策略设置为所选 PowerShell 模块启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-129">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="ad9a8-130">此设置在所有受影响的计算机上的所有会话中都有效。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-130">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="ad9a8-131">如果启用此策略设置并指定一个或多个模块，则会在事件查看器的 Windows PowerShell 日志中记录指定模块的管道执行事件。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-131">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="ad9a8-132">如果禁用此策略设置，则会为所有 PowerShell 模块禁用执行事件的日志记录。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-132">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="ad9a8-133">如果未配置此策略设置，则每个模块的 **LogPipelineExecutionDetails** 属性将确定是否记录模块的执行事件。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-133">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="ad9a8-134">默认情况下，所有模块的 **LogPipelineExecutionDetails** 属性都设置为 False。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-134">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="ad9a8-135">若要为模块启用模块日志记录，请使用以下命令格式。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-135">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="ad9a8-136">必须将模块导入到会话中，并且该设置仅在当前会话中有效。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-136">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="ad9a8-137">若要为特定计算机上的所有会话启用模块日志记录，请将前面的命令添加到 "所有用户的 PowerShell 配置文件 (`$Profile.AllUsersAllHosts`) 。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-137">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="ad9a8-138">有关模块日志记录的详细信息，请参阅 [about_Modules](about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-138">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="ad9a8-139">启用 PowerShell 脚本块日志记录</span><span class="sxs-lookup"><span data-stu-id="ad9a8-139">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="ad9a8-140">" **打开 Powershell 脚本块日志记录** " 策略设置可将所有 PowerShell 脚本输入的日志记录到 Microsoft Windows PowerShell/操作事件日志中。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-140">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="ad9a8-141">如果启用此策略设置，则 PowerShell Core 将记录命令、脚本块、函数和脚本的处理方式，无论是以交互方式调用还是通过自动化来处理。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-141">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="ad9a8-142">如果禁用此策略设置，则将禁止记录 PowerShell 脚本输入。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-142">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="ad9a8-143">如果启用脚本块调用日志记录，则 PowerShell 在调用命令、脚本块、函数或脚本启动或停止时还会记录事件。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-143">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="ad9a8-144">启用调用日志记录时会生成大量事件日志。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-144">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="ad9a8-145">启用脚本执行</span><span class="sxs-lookup"><span data-stu-id="ad9a8-145">Turn on script execution</span></span>

<span data-ttu-id="ad9a8-146">" **打开脚本执行** " 策略设置可为计算机和用户设置执行策略，这将确定允许运行哪些脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-146">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="ad9a8-147">如果启用策略设置，则可以从以下策略设置中进行选择。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-147">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="ad9a8-148">仅 **允许已签名的脚本** 仅允许脚本通过受信任的发布者签名。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-148">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="ad9a8-149">此策略设置等效于 AllSigned 执行策略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-149">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="ad9a8-150">**允许本地脚本和远程签名的脚本** 允许运行所有本地脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-150">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="ad9a8-151">来自 Internet 的脚本必须由受信任的发布者签名。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-151">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="ad9a8-152">此策略设置等效于 RemoteSigned 执行策略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-152">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="ad9a8-153">**允许** 所有脚本都允许运行所有脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-153">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="ad9a8-154">此策略设置等效于不受限制的执行策略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-154">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="ad9a8-155">如果禁用此策略设置，则不允许运行脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-155">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="ad9a8-156">此策略设置等效于受限制的执行策略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-156">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="ad9a8-157">如果禁用或未配置此策略设置，则由 cmdlet 为计算机或用户设置的执行策略将 `Set-ExecutionPolicy` 确定是否允许运行脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-157">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="ad9a8-158">默认值为 Restricted。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-158">The default value is Restricted.</span></span>

<span data-ttu-id="ad9a8-159">有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-159">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="ad9a8-160">启用 powershell 脚本</span><span class="sxs-lookup"><span data-stu-id="ad9a8-160">Turn on powershell transcription</span></span>

<span data-ttu-id="ad9a8-161">" **打开 powershell** 脚本" 策略设置允许你将 PowerShell 核心命令的输入和输出捕获到基于文本的脚本中。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-161">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="ad9a8-162">如果启用此策略设置，则 PowerShell Core 将为 PowerShell Core 和任何其他利用 PowerShell 核心引擎的应用程序启用脚本日志记录。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-162">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="ad9a8-163">默认情况下，PowerShell Core 会将脚本输出记录到每个用户的 "我的文档" 目录中，文件名中包含 "PowerShell_transcript"，以及计算机名称和启动时间。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-163">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="ad9a8-164">启用此策略等效于对每个 PowerShell 核心会话调用 Start-Transcript cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-164">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="ad9a8-165">如果禁用此策略设置，则默认情况下将禁用基于 PowerShell 的应用程序的脚本日志记录，不过，脚本之外仍可通过 Start-Transcript cmdlet 启用。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-165">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="ad9a8-166">如果使用 OutputDirectory 设置启用到共享位置的脚本日志记录，请确保限制对该目录的访问，以防止用户查看其他用户或计算机的脚本。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-166">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="ad9a8-167">为 Update-Help 设置默认源路径</span><span class="sxs-lookup"><span data-stu-id="ad9a8-167">Set the default source path for Update-Help</span></span>

<span data-ttu-id="ad9a8-168">" **设置 update-help 的默认源路径** " 策略设置为 Cmdlet 的 **SourcePath** 参数设置默认值 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-168">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="ad9a8-169">此设置可防止用户使用 `Update-Help` cmdlet 从 Internet 下载帮助文件。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-169">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="ad9a8-170">此组策略设置将出现在 " **计算机配置** " 和 " **用户配置**" 下。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-170">This Group Policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="ad9a8-171">但是，只有 " **计算机配置** " 下的组策略设置才有效。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-171">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="ad9a8-172">" **用户配置** " 下的组策略设置将被忽略。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-172">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="ad9a8-173">`Update-Help`Cmdlet 将下载并安装最新的 PowerShell 模块帮助文件，并将它们安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-173">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="ad9a8-174">默认情况下， `Update-Help` 从模块指定的 Internet 位置下载新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-174">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="ad9a8-175">但是，可以使用 cmdlet 将 `Save-Help` 最新的帮助文件下载到文件系统位置（如网络共享），然后使用 `Update-Help` cmdlet 从文件系统位置获取帮助文件，并将它们安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-175">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="ad9a8-176">此 cmdlet 的 **SourcePath** 参数 `Update-Help` 指定文件系统位置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-176">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="ad9a8-177">通过为 **SourcePath** 参数提供默认值，此组策略设置会将 **sourcepath** 参数隐式添加到所有 `Update-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-177">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="ad9a8-178">用户可以通过输入其他文件系统位置，替代指定为默认值的特定文件系统位置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-178">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="ad9a8-179">但不能从命令中删除 **SourcePath** 参数 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-179">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="ad9a8-180">如果启用此策略设置，则可以为 **SourcePath** 参数指定默认值。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-180">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="ad9a8-181">输入文件系统位置。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-181">Enter a file system location.</span></span>

<span data-ttu-id="ad9a8-182">如果禁用或未配置此策略设置，则不会对此 cmdlet 的 **SourcePath** 参数提供默认值 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-182">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="ad9a8-183">用户可以从 Internet 或任何文件系统位置下载帮助。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-183">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="ad9a8-184">有关详细信息，请参阅 [about_Updatable_Help](about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9a8-184">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="ad9a8-185">关键字</span><span class="sxs-lookup"><span data-stu-id="ad9a8-185">Keywords</span></span>

<span data-ttu-id="ad9a8-186">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="ad9a8-186">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="ad9a8-187">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad9a8-187">See also</span></span>

[<span data-ttu-id="ad9a8-188">PowerShell Core 策略 RFC</span><span class="sxs-lookup"><span data-stu-id="ad9a8-188">PowerShell Core Policy RFC</span></span>](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[<span data-ttu-id="ad9a8-189">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="ad9a8-189">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="ad9a8-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="ad9a8-190">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="ad9a8-191">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="ad9a8-191">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="ad9a8-192">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ad9a8-192">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="ad9a8-193">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ad9a8-193">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="ad9a8-194">Get-Module</span><span class="sxs-lookup"><span data-stu-id="ad9a8-194">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="ad9a8-195">Update-Help</span><span class="sxs-lookup"><span data-stu-id="ad9a8-195">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="ad9a8-196">Save-Help</span><span class="sxs-lookup"><span data-stu-id="ad9a8-196">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

