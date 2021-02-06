---
description: 介绍如何在 PowerShell 中访问 Windows 环境变量。
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 66d2bcd76651a7231a670ee5b02b99d6edd63a72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597890"
---
# <a name="about-environment-variables"></a><span data-ttu-id="fd1ad-103">关于环境变量</span><span class="sxs-lookup"><span data-stu-id="fd1ad-103">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="fd1ad-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="fd1ad-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fd1ad-105">介绍如何在 PowerShell 中访问 Windows 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-105">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="fd1ad-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="fd1ad-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="fd1ad-107">环境变量存储有关操作系统环境的信息。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-107">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="fd1ad-108">此信息包括各种详细信息，如操作系统路径、操作系统使用的处理器数量以及临时文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-108">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="fd1ad-109">环境变量存储操作系统和其他程序使用的数据。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-109">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="fd1ad-110">例如， `WINDIR` 环境变量包含 Windows 安装目录的位置。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-110">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="fd1ad-111">程序可以查询此变量的值，以确定 Windows 操作系统文件所在的位置。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-111">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="fd1ad-112">PowerShell 可以访问和管理任何受支持的操作系统平台中的环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-112">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="fd1ad-113">PowerShell 环境提供程序可以轻松地查看和更改环境变量，从而简化了此过程。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-113">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="fd1ad-114">与 PowerShell 中其他类型的变量不同，环境变量由子进程继承，如本地后台作业和模块成员运行的会话。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-114">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="fd1ad-115">这使得环境变量非常适合存储在父进程和子进程中所需的值。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-115">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="fd1ad-116">使用和更改环境变量</span><span class="sxs-lookup"><span data-stu-id="fd1ad-116">Using and changing environment variables</span></span>

<span data-ttu-id="fd1ad-117">在 Windows 上，可以在三个作用域中定义环境变量：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-117">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="fd1ad-118">计算机 (或系统) 范围</span><span class="sxs-lookup"><span data-stu-id="fd1ad-118">Machine (or System) scope</span></span>
- <span data-ttu-id="fd1ad-119">用户范围</span><span class="sxs-lookup"><span data-stu-id="fd1ad-119">User scope</span></span>
- <span data-ttu-id="fd1ad-120">进程范围</span><span class="sxs-lookup"><span data-stu-id="fd1ad-120">Process scope</span></span>

<span data-ttu-id="fd1ad-121">_进程_ 范围包含当前进程或 PowerShell 会话中可用的环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-121">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="fd1ad-122">此变量列表继承自父进程，并由 _计算机_ 和 _用户_ 作用域中的变量构造。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-122">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span> <span data-ttu-id="fd1ad-123">基于 Unix 的平台仅具有 _进程_ 范围。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-123">Unix-based platforms only have the _Process_ scope.</span></span>

<span data-ttu-id="fd1ad-124">可以通过将变量语法与环境提供程序结合使用来显示和更改环境变量的值，而无需使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="fd1ad-125">若要显示环境变量的值，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="fd1ad-126">例如，若要显示环境变量的值 `WINDIR` ，请在 PowerShell 命令提示符下键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="fd1ad-127">在此语法中，美元符号 (`$`) 表示一个变量， () 的驱动器名称 `Env:` 表示一个环境变量后跟变量名称 (`windir`) 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="fd1ad-128">更改 PowerShell 中的环境变量时，更改只会影响当前会话。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="fd1ad-129">此行为类似于 `Set` Windows 命令行界面中的命令行为和 `Setenv` 基于 UNIX 的环境中的命令。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="fd1ad-130">若要更改计算机或用户作用域中的值，则必须使用 **system.web** 类的方法。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="fd1ad-131">若要更改计算机范围的变量，还必须具有权限。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="fd1ad-132">如果尝试在没有足够权限的情况下更改值，则该命令将失败，并且 PowerShell 将显示错误。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="fd1ad-133">您可以更改变量的值，而无需使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="fd1ad-134">例如，若要将附加 `;c:\temp` 到 `Path` 环境变量的值，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="fd1ad-135">在 Linux 或 MacOS 上，命令中的冒号 (`:`) 将新路径与列表中其前面的路径分隔开。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-135">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

```powershell
$Env:PATH += ":/usr/local/temp"
```

<span data-ttu-id="fd1ad-136">你还可以使用项 cmdlet （如 `Set-Item` 、和） `Remove-Item` `Copy-Item` 来更改环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-136">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="fd1ad-137">例如，若要使用 `Set-Item` cmdlet 追加 `;c:\temp` 到 `Path` 环境变量的值，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-137">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="fd1ad-138">在此命令中，值括在括号中，以便将其解释为一个单元。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-138">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="fd1ad-139">存储首选项的环境变量</span><span class="sxs-lookup"><span data-stu-id="fd1ad-139">Environment variables that store preferences</span></span>

<span data-ttu-id="fd1ad-140">PowerShell 功能可以使用环境变量来存储用户首选项。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-140">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="fd1ad-141">这些变量的工作方式类似于首选项变量，但它们由创建它们的会话的子会话继承。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-141">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="fd1ad-142">有关首选项变量的详细信息，请参阅 [about_preference_variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-142">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="fd1ad-143">存储首选项的环境变量包括：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-143">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="fd1ad-144">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="fd1ad-144">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="fd1ad-145">存储为当前会话设置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-145">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="fd1ad-146">仅当为单一会话设置执行策略时，才存在此环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-146">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="fd1ad-147">可以通过两种不同的方式来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-147">You can do this in two different ways.</span></span>

  - <span data-ttu-id="fd1ad-148">使用 **set-executionpolicy** 参数从命令行启动会话，以便为会话设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-148">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="fd1ad-149">使用 `Set-ExecutionPolicy` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-149">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="fd1ad-150">使用值为 "Process" 的作用域参数。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-150">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="fd1ad-151">有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-151">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="fd1ad-152">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="fd1ad-152">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="fd1ad-153">PowerShell 提供对文件的控制，该文件用于缓存有关模块及其 cmdlet 的数据。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-153">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="fd1ad-154">缓存将在启动时读取，并在导入模块后在后台线程上写入。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-154">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="fd1ad-155">缓存的默认位置为：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-155">Default location of the cache is:</span></span>

  - <span data-ttu-id="fd1ad-156">Windows PowerShell 5.1：`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="fd1ad-156">Windows PowerShell 5.1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`</span></span>
  - <span data-ttu-id="fd1ad-157">PowerShell 6.0 和更高版本： `$env:LOCALAPPDATA\Microsoft\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="fd1ad-157">PowerShell 6.0 and higher: `$env:LOCALAPPDATA\Microsoft\PowerShell`</span></span>
  - <span data-ttu-id="fd1ad-158">非 Windows 默认值： `~/.cache/powershell`</span><span class="sxs-lookup"><span data-stu-id="fd1ad-158">Non-Windows default: `~/.cache/powershell`</span></span>

  <span data-ttu-id="fd1ad-159">缓存的默认文件名为 `ModuleAnalysisCache` 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-159">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="fd1ad-160">如果安装了多个 PowerShell 实例，则文件名包含十六进制后缀，以便每次安装时都有唯一的文件名。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-160">When you have multiple instances of PowerShell installed, the filename includes a hexadecimal suffix so that there is a a unique filename per installation.</span></span>

  > [!NOTE]
  > <span data-ttu-id="fd1ad-161">如果命令发现不能正常运行，例如 Intellisense 显示了不存在的命令，则可以删除缓存文件。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-161">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="fd1ad-162">下次启动 PowerShell 时，将重新创建缓存。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-162">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="fd1ad-163">若要更改缓存的默认位置，请在启动 PowerShell 之前设置环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-163">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="fd1ad-164">对此环境变量所做的更改只会影响子进程。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-164">Changes to this environment variable only affect child processes.</span></span> <span data-ttu-id="fd1ad-165">值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-165">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  <span data-ttu-id="fd1ad-166">若要禁用文件缓存，请将此值设置为无效位置，例如：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-166">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="fd1ad-167">这会设置 **NUL** 设备的路径。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-167">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="fd1ad-168">PowerShell 不能写入路径，但不会返回任何错误。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-168">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="fd1ad-169">您可以查看使用跟踪器报告的错误：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-169">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="fd1ad-170">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="fd1ad-170">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="fd1ad-171">编写模块分析缓存时，PowerShell 会检查不再存在的模块，以避免不必要的大型缓存。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-171">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="fd1ad-172">有时不需要这些检查，在这种情况下，您可以通过将此环境变量值设置为来关闭它们 `1` 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-172">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="fd1ad-173">设置此环境变量将在当前进程中立即生效。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-173">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="fd1ad-174">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fd1ad-174">PSModulePath</span></span>

  <span data-ttu-id="fd1ad-175">`$env:PSModulePath`环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-175">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="fd1ad-176">默认情况下，分配到的有效位置 `$env:PSModulePath` 为：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-176">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="fd1ad-177">系统范围的位置：这些文件夹包含 PowerShell 附带的模块。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-177">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="fd1ad-178">模块存储在 `$PSHOME\Modules` 位置。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-178">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="fd1ad-179">此外，这是安装 Windows 管理模块的位置。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-179">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="fd1ad-180">用户安装的模块：这些是用户安装的模块。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-180">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="fd1ad-181">`Install-Module` 具有 **作用域** 参数，该参数可用于指定是为当前用户还是为所有用户安装该模块。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-181">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="fd1ad-182">有关详细信息，请参阅 [Install-Module](xref:PowerShellGet.Install-Module)。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-182">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="fd1ad-183">在 Windows 上，特定于用户的 **CurrentUser** 范围是 `$HOME\Documents\PowerShell\Modules` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-183">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="fd1ad-184">**AllUsers** 作用域的位置为 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-184">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
    - <span data-ttu-id="fd1ad-185">在非 Windows 系统上，特定于用户的 **CurrentUser** 范围是 `$HOME/.local/share/powershell/Modules` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-185">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="fd1ad-186">**AllUsers** 作用域的位置为 `/usr/local/share/powershell/Modules` 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-186">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

  <span data-ttu-id="fd1ad-187">此外，在其他目录中安装模块的安装程序（如 Program Files 目录）可以将它们的位置附加到的值 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-187">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="fd1ad-188">有关详细信息，请参阅 [about_PSModulePath](about_PSModulePath.md)。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-188">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="fd1ad-189">管理环境变量</span><span class="sxs-lookup"><span data-stu-id="fd1ad-189">Managing environment variables</span></span>

<span data-ttu-id="fd1ad-190">PowerShell 提供了几种不同的方法来管理环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-190">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="fd1ad-191">环境提供程序驱动器</span><span class="sxs-lookup"><span data-stu-id="fd1ad-191">The Environment provider drive</span></span>
- <span data-ttu-id="fd1ad-192">项 cmdlet</span><span class="sxs-lookup"><span data-stu-id="fd1ad-192">The Item cmdlets</span></span>
- <span data-ttu-id="fd1ad-193">.NET **system.web** 类</span><span class="sxs-lookup"><span data-stu-id="fd1ad-193">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="fd1ad-194">在 Windows 上，系统控制面板</span><span class="sxs-lookup"><span data-stu-id="fd1ad-194">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="fd1ad-195">使用环境提供程序</span><span class="sxs-lookup"><span data-stu-id="fd1ad-195">Using the Environment provider</span></span>

<span data-ttu-id="fd1ad-196">每个环境变量由 **DictionaryEntry** 类的实例表示。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-196">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="fd1ad-197">在每个 **DictionaryEntry** 对象中，环境变量的名称是字典键。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-197">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="fd1ad-198">变量的值是字典值。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-198">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="fd1ad-199">若要在 PowerShell 中显示表示环境变量的对象的属性和方法，请使用 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-199">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="fd1ad-200">例如，若要显示驱动器中所有对象的方法和属性 `Env:` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-200">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="fd1ad-201">PowerShell 环境提供程序允许你访问 PowerShell 驱动器中的环境变量， (`Env:` 驱动器) 。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-201">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="fd1ad-202">此驱动器非常类似于文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-202">This drive looks much like a file system drive.</span></span> <span data-ttu-id="fd1ad-203">若要前往 `Env:` 驱动器，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-203">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="fd1ad-204">使用 Content cmdlet 获取或设置环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-204">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="fd1ad-205">你可以 `Env:` 从任何其他 PowerShell 驱动器查看驱动器中的环境变量，并且可以进入 `Env:` 驱动器以查看和更改环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-205">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="fd1ad-206">使用项 cmdlet</span><span class="sxs-lookup"><span data-stu-id="fd1ad-206">Using Item cmdlets</span></span>

<span data-ttu-id="fd1ad-207">引用环境变量时，键入 `Env:` 驱动器名称，后跟变量的名称。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-207">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="fd1ad-208">例如，若要显示环境变量的值 `COMPUTERNAME` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-208">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="fd1ad-209">若要显示所有环境变量的值，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-209">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="fd1ad-210">由于环境变量没有子项，因此和的输出 `Get-Item` `Get-ChildItem` 是相同的。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-210">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="fd1ad-211">默认情况下，PowerShell 按其检索环境变量的顺序显示这些环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-211">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="fd1ad-212">若要按变量名称对环境变量的列表进行排序，请通过管道将命令的输出传递 `Get-ChildItem` 给 `Sort-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-212">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="fd1ad-213">例如，在任何 PowerShell 驱动器上，键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-213">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="fd1ad-214">你还可以 `Env:` 使用 cmdlet 进入驱动器 `Set-Location` ：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-214">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="fd1ad-215">如果位于 `Env:` 驱动器中，则可以省略路径中的 `Env:` 驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-215">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="fd1ad-216">例如，若要显示所有环境变量，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-216">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="fd1ad-217">若要显示 `COMPUTERNAME` 驱动器中变量的值 `Env:` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="fd1ad-217">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="fd1ad-218">保存对环境变量所做的更改</span><span class="sxs-lookup"><span data-stu-id="fd1ad-218">Saving changes to environment variables</span></span>

<span data-ttu-id="fd1ad-219">若要对 Windows 上的环境变量进行持久更改，请使用系统控制面板。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-219">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="fd1ad-220">选择 " **高级系统设置**"。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-220">Select **Advanced System Settings**.</span></span> <span data-ttu-id="fd1ad-221">在 " **高级** " 选项卡上，单击 " **环境变量 ...**"。你可以在 **用户** 和 **系统** (计算机) 范围中添加或编辑现有环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-221">On the **Advanced** tab, click **Environment Variable...**. You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="fd1ad-222">Windows 将这些值写入注册表，以便它们在会话和系统重启之间保持不变。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-222">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="fd1ad-223">或者，可以在 PowerShell 配置文件中添加或更改环境变量。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-223">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="fd1ad-224">此方法适用于任何受支持平台上的任何版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-224">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="fd1ad-225">使用 System.object 方法</span><span class="sxs-lookup"><span data-stu-id="fd1ad-225">Using System.Environment methods</span></span>

<span data-ttu-id="fd1ad-226">**System.web** 类提供 **GetEnvironmentVariable** 和 **SetEnvironmentVariable** 方法，使你可以指定变量的作用域。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-226">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="fd1ad-227">下面的示例使用 **GetEnvironmentVariable** 方法来获取的计算机设置 `PSModulePath` ，并使用 **SetEnvironmentVariable** 方法将 `C:\Program Files\Fabrikam\Modules` 路径添加到值中。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-227">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="fd1ad-228">有关 **system.web** 类的方法的详细信息，请参阅 [环境方法](/dotnet/api/system.environment)。</span><span class="sxs-lookup"><span data-stu-id="fd1ad-228">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd1ad-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd1ad-229">SEE ALSO</span></span>

- [<span data-ttu-id="fd1ad-230">环境 (提供程序) </span><span class="sxs-lookup"><span data-stu-id="fd1ad-230">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="fd1ad-231">about_Modules</span><span class="sxs-lookup"><span data-stu-id="fd1ad-231">about_Modules</span></span>](about_Modules.md)

