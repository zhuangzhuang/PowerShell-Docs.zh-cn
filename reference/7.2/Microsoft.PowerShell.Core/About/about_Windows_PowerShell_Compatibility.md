---
description: 介绍 PowerShell 7 的 Windows PowerShell 兼容性功能。
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 3a7605765da8c17bad2d98a1d3fc3f7cc96f57b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598690"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="a4702-103">关于 Windows PowerShell 兼容性</span><span class="sxs-lookup"><span data-stu-id="a4702-103">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="a4702-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="a4702-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="a4702-105">介绍 PowerShell 7 的 Windows PowerShell 兼容性功能。</span><span class="sxs-lookup"><span data-stu-id="a4702-105">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4702-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="a4702-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a4702-107">除非模块清单指示模块与 PowerShell Core 兼容，否则，将 `%windir%\system32\WindowsPowerShell\v1.0\Modules` 通过 Windows Powershell 兼容性功能在后台 Windows powershell 5.1 进程中加载文件夹中的模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-107">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="a4702-108">使用兼容性功能</span><span class="sxs-lookup"><span data-stu-id="a4702-108">Using the Compatibility feature</span></span>

<span data-ttu-id="a4702-109">使用 Windows PowerShell 兼容性功能导入第一个模块时，PowerShell 会创建一个名为的远程会话， `WinPSCompatSession` 该会话在后台 Windows PowerShell 5.1 进程中运行。</span><span class="sxs-lookup"><span data-stu-id="a4702-109">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="a4702-110">此过程是在兼容性功能导入第一个模块时创建的。</span><span class="sxs-lookup"><span data-stu-id="a4702-110">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="a4702-111"> (使用 `Remove-Module`) 或 PowerShell 进程退出时，将关闭上一个此类模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-111">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="a4702-112">`WinPSCompatSession`通过隐式远程处理使用加载到会话中的模块，并将其反射到当前的 PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="a4702-112">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="a4702-113">这与用于 PowerShell 作业的传输方法相同。</span><span class="sxs-lookup"><span data-stu-id="a4702-113">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="a4702-114">当模块导入到会话中时 `WinPSCompatSession` ，隐式远程处理会在用户的目录中生成一个代理模块 `$env:Temp` ，并将此代理模块导入到当前的 PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="a4702-114">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="a4702-115">这允许 PowerShell 检测使用 Windows PowerShell 兼容性功能加载的模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-115">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="a4702-116">创建会话后，可以将其用于在反序列化的对象上无法正常工作的操作。</span><span class="sxs-lookup"><span data-stu-id="a4702-116">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="a4702-117">整个管道在 Windows PowerShell 中执行，只返回最终结果。</span><span class="sxs-lookup"><span data-stu-id="a4702-117">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="a4702-118">例如：</span><span class="sxs-lookup"><span data-stu-id="a4702-118">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="a4702-119">可以通过两种方法调用兼容性功能：</span><span class="sxs-lookup"><span data-stu-id="a4702-119">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="a4702-120">使用 **UseWindowsPowerShell** 参数通过导入模块显式</span><span class="sxs-lookup"><span data-stu-id="a4702-120">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="a4702-121">通过命令发现以模块名称、路径或自动加载的方式隐式导入 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-121">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="a4702-122">如果尚未加载，则在运行时会加载 AppLocker 模块  `Get-AppLockerPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="a4702-122">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="a4702-123">Windows PowerShell 兼容性会阻止加载 `WindowsPowerShellCompatibilityModuleDenyList` PowerShell 配置文件中的设置中列出的模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-123">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="a4702-124">此设置的默认值为：</span><span class="sxs-lookup"><span data-stu-id="a4702-124">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="a4702-125">管理隐式模块加载</span><span class="sxs-lookup"><span data-stu-id="a4702-125">Managing implicit module loading</span></span>

<span data-ttu-id="a4702-126">若要禁用 Windows PowerShell 兼容功能的隐式导入行为，请使用 `DisableImplicitWinCompat` PowerShell 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="a4702-126">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="a4702-127">此设置可以添加到 `powershell.config.json` 文件中。</span><span class="sxs-lookup"><span data-stu-id="a4702-127">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="a4702-128">有关详细信息，请参阅 [about_powershell_config](about_powershell_config.md)。</span><span class="sxs-lookup"><span data-stu-id="a4702-128">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="a4702-129">此示例演示如何创建一个配置文件，该文件禁用 Windows PowerShell 兼容性的隐式模块加载功能。</span><span class="sxs-lookup"><span data-stu-id="a4702-129">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="a4702-130">有关模块兼容性的最新信息，请参阅 [PowerShell 7 模块兼容性](https://aka.ms/PSModuleCompat) 列表。</span><span class="sxs-lookup"><span data-stu-id="a4702-130">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="a4702-131">管理 cmdlet clobbering</span><span class="sxs-lookup"><span data-stu-id="a4702-131">Managing cmdlet clobbering</span></span>

<span data-ttu-id="a4702-132">Windows PowerShell 兼容性功能使用隐式远程处理在兼容模式下加载模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-132">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="a4702-133">结果就是，模块导出的命令优先于当前 PowerShell 7 会话中名称相同的命令。</span><span class="sxs-lookup"><span data-stu-id="a4702-133">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="a4702-134">PowerShell 7.0.0 版包含 PowerShell 随附的核心模块。</span><span class="sxs-lookup"><span data-stu-id="a4702-134">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="a4702-135">在 PowerShell 7.1 中，此行为已更改，因此不 clobbered 以下核心 PowerShell 模块：</span><span class="sxs-lookup"><span data-stu-id="a4702-135">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="a4702-136">ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="a4702-136">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="a4702-137">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="a4702-137">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="a4702-138">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="a4702-138">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="a4702-139">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="a4702-139">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="a4702-140">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="a4702-140">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="a4702-141">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="a4702-141">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="a4702-142">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="a4702-142">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="a4702-143">PowerShell 7.1 还添加了列出不应在兼容模式下 clobbered 的其他模块的功能。</span><span class="sxs-lookup"><span data-stu-id="a4702-143">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="a4702-144">你可以将 `WindowsPowerShellCompatibilityNoClobberModuleList` 设置添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="a4702-144">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="a4702-145">此设置的值是以逗号分隔的模块名称列表。</span><span class="sxs-lookup"><span data-stu-id="a4702-145">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="a4702-146">此设置的默认值为：</span><span class="sxs-lookup"><span data-stu-id="a4702-146">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="a4702-147">限制</span><span class="sxs-lookup"><span data-stu-id="a4702-147">Limitations</span></span>

<span data-ttu-id="a4702-148">Windows PowerShell 兼容性功能：</span><span class="sxs-lookup"><span data-stu-id="a4702-148">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="a4702-149">仅在 Windows 计算机上以本地方式运行</span><span class="sxs-lookup"><span data-stu-id="a4702-149">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="a4702-150">要求 Windows PowerShell 5。1</span><span class="sxs-lookup"><span data-stu-id="a4702-150">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="a4702-151">对序列化 cmdlet 参数和返回值进行操作，而不是对活动对象进行操作</span><span class="sxs-lookup"><span data-stu-id="a4702-151">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="a4702-152">导入到 Windows PowerShell 远程处理会话的所有模块共享同一运行空间。</span><span class="sxs-lookup"><span data-stu-id="a4702-152">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="a4702-153">关键字</span><span class="sxs-lookup"><span data-stu-id="a4702-153">Keywords</span></span>

<span data-ttu-id="a4702-154">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="a4702-154">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="a4702-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="a4702-155">See also</span></span>

[<span data-ttu-id="a4702-156">about_Modules</span><span class="sxs-lookup"><span data-stu-id="a4702-156">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="a4702-157">Import-Module</span><span class="sxs-lookup"><span data-stu-id="a4702-157">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

