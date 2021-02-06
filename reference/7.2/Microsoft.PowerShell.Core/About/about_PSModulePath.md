---
description: PSModulePath 环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: ce77005d816f49c0a6353bd7b3e0580293b05d23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597237"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="9b603-103">关于 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="9b603-103">About PSModulePath</span></span>

<span data-ttu-id="9b603-104">`$env:PSModulePath`环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。</span><span class="sxs-lookup"><span data-stu-id="9b603-104">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span> <span data-ttu-id="9b603-105">PowerShell 会以递归方式在每个文件夹中搜索模块 (`.psd1` 或 `.psm1`) 文件。</span><span class="sxs-lookup"><span data-stu-id="9b603-105">PowerShell recursively searches each folder for module (`.psd1` or `.psm1`) files.</span></span>

<span data-ttu-id="9b603-106">默认情况下，分配到的有效位置 `$env:PSModulePath` 为：</span><span class="sxs-lookup"><span data-stu-id="9b603-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="9b603-107">系统范围的位置：这些文件夹包含 PowerShell 附带的模块。</span><span class="sxs-lookup"><span data-stu-id="9b603-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="9b603-108">这些模块存储在文件夹中 `$PSHOME\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="9b603-109">这也是安装 Windows 管理模块的位置。</span><span class="sxs-lookup"><span data-stu-id="9b603-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="9b603-110">用户安装的模块：这些是用户安装的模块。</span><span class="sxs-lookup"><span data-stu-id="9b603-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="9b603-111">`Install-Module` 具有 **作用域** 参数，该参数可用于指定是为当前用户还是为所有用户安装该模块。</span><span class="sxs-lookup"><span data-stu-id="9b603-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="9b603-112">有关详细信息，请参阅 [Install-Module](xref:PowerShellGet.Install-Module)。</span><span class="sxs-lookup"><span data-stu-id="9b603-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="9b603-113">在 Windows 上，特定于用户的 **CurrentUser** 范围是 `$HOME\Documents\PowerShell\Modules` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b603-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="9b603-114">**AllUsers** 作用域的位置为 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="9b603-115">在非 Windows 系统上，特定于用户的 **CurrentUser** 范围是 `$HOME/.local/share/powershell/Modules` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b603-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="9b603-116">**AllUsers** 作用域的位置为 `/usr/local/share/powershell/Modules` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="9b603-117">此外，在其他目录中安装模块的安装程序（如 Program Files 目录）可以将它们的位置附加到的值 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="9b603-118">在 Windows 上，用户特定的位置是 `PowerShell\Modules` 位于用户配置文件中的 **Documents** 文件夹中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b603-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="9b603-119">该位置的特定路径因 Windows 版本而异，无论是否正在使用文件夹重定向。</span><span class="sxs-lookup"><span data-stu-id="9b603-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="9b603-120">Microsoft OneDrive 还可以更改 **文档** 文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="9b603-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="9b603-121">可以使用以下命令来验证 **Documents** 文件夹的位置： `[Environment]::GetFolderPath('MyDocuments')` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="9b603-122">修改 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="9b603-122">Modifying PSModulePath</span></span>

<span data-ttu-id="9b603-123">若要更改当前会话的默认模块目录，请使用以下命令格式来更改 `PSModulePath` 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="9b603-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="9b603-124">例如，若要将 `C:\Program Files\Fabrikam\Modules` 目录添加到 PSModulePath 环境变量的值，请键入：</span><span class="sxs-lookup"><span data-stu-id="9b603-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="9b603-125">命令中的分号 (`;`) 将新路径与列表中其前面的路径分隔开。</span><span class="sxs-lookup"><span data-stu-id="9b603-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="9b603-126">在非 Windows 平台上，冒号 (`:`) 将环境变量中的路径位置隔开。</span><span class="sxs-lookup"><span data-stu-id="9b603-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="9b603-127">若要 `PSModulePath` 在每个会话中更改的值，请将上一个命令添加到 PowerShell 配置文件，或使用 **环境** 类的 **SetEnvironmentVariable** 方法。</span><span class="sxs-lookup"><span data-stu-id="9b603-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="9b603-128">下面的命令使用 **GetEnvironmentVariable** 方法来获取的计算机设置 `PSModulePath` ，并使用 **SetEnvironmentVariable** 方法将 `C:\Program Files\Fabrikam\Modules` 路径添加到值中。</span><span class="sxs-lookup"><span data-stu-id="9b603-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="9b603-129">若要将路径添加到用户设置，请将 "目标" 值更改为 " **用户**"。</span><span class="sxs-lookup"><span data-stu-id="9b603-129">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="9b603-130">有关 **system.web** 类的方法的详细信息，请参阅 [环境方法](/dotnet/api/system.environment)。</span><span class="sxs-lookup"><span data-stu-id="9b603-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="9b603-131">PowerShell PSModulePath 构造</span><span class="sxs-lookup"><span data-stu-id="9b603-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="9b603-132">`$env:PSModulePath`每次启动 PowerShell 时，都会构造的值。</span><span class="sxs-lookup"><span data-stu-id="9b603-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="9b603-133">该值因 PowerShell 版本和启动方式而异。</span><span class="sxs-lookup"><span data-stu-id="9b603-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="9b603-134">Windows PowerShell 启动</span><span class="sxs-lookup"><span data-stu-id="9b603-134">Windows PowerShell startup</span></span>

<span data-ttu-id="9b603-135">Windows PowerShell 在启动时使用以下逻辑来构造 `PSModulePath` ：</span><span class="sxs-lookup"><span data-stu-id="9b603-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="9b603-136">如果 `PSModulePath` 不存在，则将 **CurrentUser**、 **AllUsers** 和 `$PSHOME` 模块路径组合在一起</span><span class="sxs-lookup"><span data-stu-id="9b603-136">If `PSModulePath` doesn't exist, combine **CurrentUser**, **AllUsers**, and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="9b603-137">如果 `PSModulePath` 存在，则：</span><span class="sxs-lookup"><span data-stu-id="9b603-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="9b603-138">如果 `PSModulePath` 包含 `$PSHOME` 模块路径：</span><span class="sxs-lookup"><span data-stu-id="9b603-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="9b603-139">在模块路径之前插入 **AllUsers** 模块路径 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="9b603-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="9b603-140">else:</span><span class="sxs-lookup"><span data-stu-id="9b603-140">else:</span></span>
    - <span data-ttu-id="9b603-141">只需使用 `PSModulePath` 自用户特意删除位置后定义 `$PSHOME` 的</span><span class="sxs-lookup"><span data-stu-id="9b603-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="9b603-142">仅当用户范围不存在时， **CurrentUser** 模块路径才带有前缀 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="9b603-143">否则，将 `$env:PSModulePath` 按定义使用用户作用域。</span><span class="sxs-lookup"><span data-stu-id="9b603-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="9b603-144">PowerShell Core 6 启动</span><span class="sxs-lookup"><span data-stu-id="9b603-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="9b603-145">如果 PowerShell Core 6 `$env:PSModulePath` 检测到它是从 PowerShell 启动的，则不使用的内容。</span><span class="sxs-lookup"><span data-stu-id="9b603-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="9b603-146">它将覆盖它：</span><span class="sxs-lookup"><span data-stu-id="9b603-146">It overwrites it with:</span></span>

- <span data-ttu-id="9b603-147">**CurrentUser** 模块路径 + **AllUsers** 模块路径 + `$PSHOME` 模块路径 + Windows PowerShell `$PSHOME` 模块路径。</span><span class="sxs-lookup"><span data-stu-id="9b603-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="9b603-148">PowerShell 7 启动</span><span class="sxs-lookup"><span data-stu-id="9b603-148">PowerShell 7 startup</span></span>

<span data-ttu-id="9b603-149">在 Windows 中，对于大多数环境变量，如果存在用户范围的变量，新进程将仅使用该值，即使存在同名的计算机范围的变量。</span><span class="sxs-lookup"><span data-stu-id="9b603-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="9b603-150">在 PowerShell 7 中， `PSModulePath` 的处理方式类似于 `Path` Windows 上环境变量的处理方式。</span><span class="sxs-lookup"><span data-stu-id="9b603-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="9b603-151">在 Windows 上，的 `Path` 处理方式与其他环境变量不同。</span><span class="sxs-lookup"><span data-stu-id="9b603-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="9b603-152">当进程启动时，Windows 会将用户范围 `Path` 与计算机范围合并 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="9b603-153">检索用户范围 `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="9b603-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="9b603-154">与处理继承的 `PSModulePath` 环境变量比较</span><span class="sxs-lookup"><span data-stu-id="9b603-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="9b603-155">如果相同：</span><span class="sxs-lookup"><span data-stu-id="9b603-155">If the same:</span></span>
    - <span data-ttu-id="9b603-156">在 `PSModulePath` `Path` 环境变量的语义后面追加 AllUsers 到末尾</span><span class="sxs-lookup"><span data-stu-id="9b603-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="9b603-157">Windows `System32` 路径来自定义的计算机 `PSModulePath` ，因此无需显式添加</span><span class="sxs-lookup"><span data-stu-id="9b603-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="9b603-158">如果不同，则视为用户显式修改了它，并且不追加 **AllUsers**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="9b603-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="9b603-159">按顺序为 PS7 用户、系统和 `$PSHOME` 路径提供前缀</span><span class="sxs-lookup"><span data-stu-id="9b603-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="9b603-160">如果 `powershell.config.json` 包含用户范围的 `PSModulePath` ，请使用它，而不是用户的默认值</span><span class="sxs-lookup"><span data-stu-id="9b603-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="9b603-161">如果 `powershell.config.json` 包含系统范围 `PSModulePath` ，请使用此值，而不使用系统的默认值</span><span class="sxs-lookup"><span data-stu-id="9b603-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="9b603-162">Unix 系统没有隔离用户和系统环境变量。</span><span class="sxs-lookup"><span data-stu-id="9b603-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="9b603-163">`PSModulePath` 是继承的，如果尚未定义 PS7 特定路径，则会将其作为前缀。</span><span class="sxs-lookup"><span data-stu-id="9b603-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="9b603-164">从 PowerShell 7 启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b603-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="9b603-165">对于此讨论， _Windows PowerShell_ 既表示 `powershell.exe` 又是 `powershell_ise.exe` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="9b603-166">将的值 `$env:PSModulePath` 复制到， `WinPSModulePath` 并进行以下修改：</span><span class="sxs-lookup"><span data-stu-id="9b603-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="9b603-167">删除用户模块路径 PS7</span><span class="sxs-lookup"><span data-stu-id="9b603-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="9b603-168">删除系统模块路径 PS7</span><span class="sxs-lookup"><span data-stu-id="9b603-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="9b603-169">删除模块路径中的 PS7 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="9b603-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="9b603-170">删除 PS7 路径，以便不会在 Windows PowerShell 中加载 PS7 模块。</span><span class="sxs-lookup"><span data-stu-id="9b603-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="9b603-171">`WinPSModulePath`启动 Windows PowerShell 时使用该值。</span><span class="sxs-lookup"><span data-stu-id="9b603-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="9b603-172">从 Windows PowerShell 启动 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="9b603-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="9b603-173">PowerShell 7 启动将按原样继续，并添加 Windows PowerShell 添加的继承路径。</span><span class="sxs-lookup"><span data-stu-id="9b603-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="9b603-174">由于 PS7 特定的路径带有前缀，因此不存在功能问题。</span><span class="sxs-lookup"><span data-stu-id="9b603-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="9b603-175">从 PowerShell 7 启动 PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="9b603-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="9b603-176">PowerShell Core 6 将覆盖 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="9b603-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="9b603-177">未进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="9b603-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="9b603-178">从 PowerShell 6 启动 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="9b603-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="9b603-179">PowerShell 7 启动将按原样继续，并添加 PowerShell Core 6 添加的继承路径。</span><span class="sxs-lookup"><span data-stu-id="9b603-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="9b603-180">由于 PS7 特定的路径带有前缀，因此不存在功能问题。</span><span class="sxs-lookup"><span data-stu-id="9b603-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="module-search-behavior"></a><span data-ttu-id="9b603-181">模块搜索行为</span><span class="sxs-lookup"><span data-stu-id="9b603-181">Module search behavior</span></span>

<span data-ttu-id="9b603-182">PowerShell 会以递归方式搜索 **PSModulePath** 中的每个文件夹 (`.psd1` 或 `.psm1`) 文件。</span><span class="sxs-lookup"><span data-stu-id="9b603-182">PowerShell recursively searches each folder in the **PSModulePath** for module (`.psd1` or `.psm1`) files.</span></span> <span data-ttu-id="9b603-183">此搜索模式允许在不同的文件夹中安装相同模块的多个版本。</span><span class="sxs-lookup"><span data-stu-id="9b603-183">This search pattern allows multiple versions of the same module to be installed in different folders.</span></span> <span data-ttu-id="9b603-184">例如：</span><span class="sxs-lookup"><span data-stu-id="9b603-184">For example:</span></span>

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

<span data-ttu-id="9b603-185">默认情况下，当找到多个版本时，PowerShell 将加载模块的最高版本号。</span><span class="sxs-lookup"><span data-stu-id="9b603-185">By default, PowerShell loads the highest version number of a module when multiple versions are found.</span></span> <span data-ttu-id="9b603-186">若要加载特定版本，请使用 `Import-Module` With **FullyQualifiedName** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b603-186">To load a specific version, use `Import-Module` with the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="9b603-187">有关详细信息，请参阅 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="9b603-187">For more information, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b603-188">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b603-188">See also</span></span>

- [<span data-ttu-id="9b603-189">about_Modules</span><span class="sxs-lookup"><span data-stu-id="9b603-189">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="9b603-190">环境方法</span><span class="sxs-lookup"><span data-stu-id="9b603-190">Environment Methods</span></span>](/dotnet/api/system.environment)
