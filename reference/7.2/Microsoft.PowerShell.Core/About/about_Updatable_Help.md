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
# <a name="about-updatable-help"></a><span data-ttu-id="90c95-103">关于可更新帮助</span><span class="sxs-lookup"><span data-stu-id="90c95-103">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="90c95-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="90c95-104">Short description</span></span>
<span data-ttu-id="90c95-105">介绍 PowerShell 中的可更新帮助系统。</span><span class="sxs-lookup"><span data-stu-id="90c95-105">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="90c95-106">长说明</span><span class="sxs-lookup"><span data-stu-id="90c95-106">Long description</span></span>

<span data-ttu-id="90c95-107">PowerShell 提供了几种不同的方法来访问 PowerShell cmdlet 和概念的最新帮助主题。</span><span class="sxs-lookup"><span data-stu-id="90c95-107">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="90c95-108">PowerShell 3.0 中引入的可更新帮助系统旨在确保你始终在本地计算机上具有最新的帮助主题，以便你可以在命令行中读取它们。</span><span class="sxs-lookup"><span data-stu-id="90c95-108">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="90c95-109">它可让你轻松下载和安装帮助文件，并在新的帮助文件可用时更新这些文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-109">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="90c95-110">若要为企业中的多台计算机和无法访问 internet 的计算机提供更新的帮助，可更新帮助允许你将帮助文件下载到文件系统目录或文件共享，然后从文件共享安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-110">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="90c95-111">在 PowerShell 4.0 中， **HelpInfoUri** 属性通过 Windows PowerShell 远程处理保留，这允许对 `Save-Help` 远程计算机上安装的模块进行处理，但不一定要在本地计算机上安装。</span><span class="sxs-lookup"><span data-stu-id="90c95-111">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="90c95-112">可以通过在没有 `Export-Clixml` internet 访问权限的计算机上运行，在能够访问 internet 的计算机上导入 **PSModuleInfo** 对象，然后 `Save-Help` 在 **PSModuleInfo** 对象上运行，从而将 PSModuleInfo 对象保存到磁盘或可移动媒体 (例如 USB 驱动器) 。</span><span class="sxs-lookup"><span data-stu-id="90c95-112">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="90c95-113">保存的帮助可以通过使用可移动媒体复制到远程断开连接的计算机，然后通过运行进行安装 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-113">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="90c95-114">这些功能改进 `Save-Help` 使你可以在没有任何类型网络访问权限的计算机上安装帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-114">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="90c95-115">有关如何使用新功能的示例 `Save-Help` ，请参阅本主题中的 [如何从文件共享更新帮助](#how-to-update-help-from-a-file-share) 。</span><span class="sxs-lookup"><span data-stu-id="90c95-115">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="90c95-116">即使计算机上没有帮助文件，可更新帮助也支持联机访问最新的帮助主题和 cmdlet 的基本帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-116">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="90c95-117">PowerShell 3.0 未附带帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-117">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="90c95-118">你可以使用 "可更新的帮助" 功能为默认情况下在 PowerShell 中包含的所有命令和所有 Windows 模块安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-118">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="90c95-119">可更新帮助 cmdlet</span><span class="sxs-lookup"><span data-stu-id="90c95-119">Updatable help cmdlets</span></span>

- <span data-ttu-id="90c95-120">`Update-Help`：从 internet 或文件共享下载最新的帮助文件，并将其安装在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="90c95-120">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="90c95-121">`Save-Help`：从 internet 下载最新的帮助文件，并将它们保存在文件系统目录或文件共享中。</span><span class="sxs-lookup"><span data-stu-id="90c95-121">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="90c95-122">若要在计算机上安装帮助文件，请使用 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-122">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="90c95-123">`Get-Help`：在命令行中显示帮助主题。</span><span class="sxs-lookup"><span data-stu-id="90c95-123">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="90c95-124">从计算机上的帮助文件中获取帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-124">Gets help from the help files on the computer.</span></span> <span data-ttu-id="90c95-125">显示自动生成的有关不包含帮助文件的 cmdlet 和函数的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-125">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="90c95-126">在默认 internet 浏览器中打开有关 cmdlet、函数、脚本和工作流的联机帮助主题。</span><span class="sxs-lookup"><span data-stu-id="90c95-126">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="90c95-127">自动生成的帮助：帮助无帮助文件</span><span class="sxs-lookup"><span data-stu-id="90c95-127">Auto-generated help: help without help files</span></span>

<span data-ttu-id="90c95-128">如果计算机上没有 cmdlet、函数或工作流的帮助文件，则该 `Get-Help` cmdlet 将显示自动生成的帮助并提示你下载帮助文件或联机阅读这些帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-128">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="90c95-129">自动生成的帮助包括语法和别名，以及说明如何使用可更新的帮助 cmdlet 和访问联机帮助主题的注释。</span><span class="sxs-lookup"><span data-stu-id="90c95-129">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="90c95-130">例如，以下命令获取 cmdlet 的基本帮助 `Get-Culture` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-130">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="90c95-131">输出显示 `Get-Help` 计算机上没有帮助文件时的显示。</span><span class="sxs-lookup"><span data-stu-id="90c95-131">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

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

## <a name="help-files-for-modules"></a><span data-ttu-id="90c95-132">模块的帮助文件</span><span class="sxs-lookup"><span data-stu-id="90c95-132">Help files for modules</span></span>

<span data-ttu-id="90c95-133">可更新帮助的最小单位是模块的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-133">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="90c95-134">模块帮助包含模块中所有 cmdlet、函数、工作流、提供程序、脚本和概念的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-134">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="90c95-135">您可以为计算机上安装的所有模块更新帮助，即使这些模块未导入到当前会话中也是如此。</span><span class="sxs-lookup"><span data-stu-id="90c95-135">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="90c95-136">您可以为整个模块更新帮助，但不能更新单个 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-136">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="90c95-137">若要查找包含特定 cmdlet 的模块，请使用以下命令格式：</span><span class="sxs-lookup"><span data-stu-id="90c95-137">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="90c95-138">例如，若要查找包含该 cmdlet 的模块 `Set-ExecutionPolicy` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-138">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="90c95-139">若要为特定模块更新帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-139">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="90c95-140">例如，若要更新包含 Set-ExecutionPolicy cmdlet 的模块的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-140">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="90c95-141">可更新帮助的权限</span><span class="sxs-lookup"><span data-stu-id="90c95-141">Permissions for updatable help</span></span>

<span data-ttu-id="90c95-142">若要为目录中的模块更新帮助 `$pshome/Modules` ，你必须是计算机上 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="90c95-142">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="90c95-143">如果您不是 Administrators 组的成员，则不能为这些模块更新帮助;但是，如果您可以访问 internet，则可以联机查看帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-143">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="90c95-144">为目录中的模块 `$home/Documents/PowerShell/Modules` 或其他子目录中的模块更新帮助 `$home` 不需要特殊权限。</span><span class="sxs-lookup"><span data-stu-id="90c95-144">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="90c95-145">`Update-Help`和 `Save-Help` Cmdlet 具有 **UseDefaultCredentials** 参数，该参数提供当前用户的显式凭据。</span><span class="sxs-lookup"><span data-stu-id="90c95-145">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="90c95-146">此参数设计用于访问安全的 internet 位置。</span><span class="sxs-lookup"><span data-stu-id="90c95-146">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="90c95-147">`Update-Help`和 `Save-Help` cmdlet 还具有一个 **Credential** 参数，该参数使你可以在远程计算机上运行该命令并访问第三台计算机上的文件共享。</span><span class="sxs-lookup"><span data-stu-id="90c95-147">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="90c95-148">仅当使用的 SourcePath 或 **LiteralPath** 参数和的 `Update-Help` **DestinationPath** 或 **LiteralPath** 参数时，Credential 参数才有效 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-148">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="90c95-149">如何安装和更新帮助文件</span><span class="sxs-lookup"><span data-stu-id="90c95-149">How to install and update help files</span></span>

<span data-ttu-id="90c95-150">若要首次下载和安装帮助文件，或更新计算机上的帮助文件，请使用 `Update-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c95-150">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="90c95-151">`Update-Help`Cmdlet 可为你完成所有的工作，包括以下任务。</span><span class="sxs-lookup"><span data-stu-id="90c95-151">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="90c95-152">确定支持可更新帮助的模块。</span><span class="sxs-lookup"><span data-stu-id="90c95-152">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="90c95-153">查找每个模块存储其可更新帮助文件的 internet 位置。</span><span class="sxs-lookup"><span data-stu-id="90c95-153">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="90c95-154">将计算机上每个模块的帮助文件与可用于每个模块的最新帮助文件进行比较。</span><span class="sxs-lookup"><span data-stu-id="90c95-154">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="90c95-155">从 internet 下载新的文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-155">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="90c95-156">解包帮助文件包。</span><span class="sxs-lookup"><span data-stu-id="90c95-156">Unwraps the help file package.</span></span>
- <span data-ttu-id="90c95-157">验证文件是否为有效的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-157">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="90c95-158">将帮助文件安装在模块目录的特定于语言的子目录中。</span><span class="sxs-lookup"><span data-stu-id="90c95-158">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="90c95-159">若要访问新的帮助主题，请使用 `Get-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c95-159">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="90c95-160">不需要重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="90c95-160">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="90c95-161">若要在支持可更新帮助的计算机上安装或更新所有模块的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-161">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="90c95-162">若要为特定模块更新帮助，请添加的 **Module** 参数 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-162">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="90c95-163">模块名称中允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="90c95-163">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="90c95-164">例如，若要更新 ServerManager 模块的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-164">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="90c95-165">如果没有参数， `Update-Help` 则将为会话中的所有模块以及支持可更新帮助的所有已安装模块更新帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-165">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="90c95-166">要包含的模块必须安装在 PSModulePath 环境变量的值中列出的目录中。</span><span class="sxs-lookup"><span data-stu-id="90c95-166">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="90c95-167">它们也是由 "Get-help-ListAvailable" 命令返回的模块。</span><span class="sxs-lookup"><span data-stu-id="90c95-167">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="90c95-168">如果 **Module** 参数的值 `*` (all) ，则 `Update-Help` 将尝试为所有已安装的模块（包括不支持可更新帮助的模块）更新帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-168">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="90c95-169">此命令通常会生成许多错误，因为 cmdlet 遇到不支持可更新帮助的模块。</span><span class="sxs-lookup"><span data-stu-id="90c95-169">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="90c95-170">如何从文件共享更新帮助</span><span class="sxs-lookup"><span data-stu-id="90c95-170">How to update help from a file share</span></span>

<span data-ttu-id="90c95-171">若要支持未连接到 internet 的计算机，或者若要控制或简化企业中的更新帮助，请使用 `Save-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c95-171">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="90c95-172">`Save-Help`Cmdlet 可从 internet 下载帮助文件，并将它们保存在指定的文件系统目录中。</span><span class="sxs-lookup"><span data-stu-id="90c95-172">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="90c95-173">`Save-Help` 将指定目录中的帮助文件与可用于每个模块的最新帮助文件进行比较。</span><span class="sxs-lookup"><span data-stu-id="90c95-173">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="90c95-174">如果目录中没有可用于该模块的帮助文件或更新的帮助文件，则该 `Save-Help` cmdlet 将从 internet 下载新的文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-174">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="90c95-175">但是，它不会解包或安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-175">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="90c95-176">若要在计算机上安装或更新保存到文件系统目录的帮助文件，请使用该 cmdlet 的 **SourcePath** 参数 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-176">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="90c95-177">`Update-Help`Cmdlet 标识最新的帮助文件，对其进行解包和验证，然后将它们安装在模块目录的特定于语言的子目录中。</span><span class="sxs-lookup"><span data-stu-id="90c95-177">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="90c95-178">例如，若要将所有已安装模块的帮助保存到 `\\Server\Share` 目录中，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-178">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="90c95-179">然后，若要从目录更新帮助 `\\Server\Share` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-179">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="90c95-180">下面的示例演示 `Save-Help` 如何使用为未安装在本地计算机上的模块保存帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-180">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="90c95-181">在此示例中，管理员运行 `Save-Help` 从连接了 internet 的客户端计算机保存 DhcpServer 模块的帮助，而无需在本地计算机上安装 DhcpServer 模块或 DHCP 服务器角色。</span><span class="sxs-lookup"><span data-stu-id="90c95-181">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="90c95-182">选项1：运行 `Invoke-Command` 以获取远程模块的 **PSModuleInfo** 对象，将其保存在变量中， `$m` 然后在 `Save-Help` **PSModuleInfo** 对象上运行，方法是将变量指定 `$m` 为模块名称。</span><span class="sxs-lookup"><span data-stu-id="90c95-182">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="90c95-183">选项2：在运行 DHCP 服务器模块的计算机上打开以其为目标的 PSSession，若要获取该模块的 **PSModuleInfo** 对象，请将其保存在变量中 `$m` ，然后 `Save-Help` 在保存在变量中的对象上运行 `$m` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-183">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="90c95-184">选项3：打开一个 CIM 会话，以运行 DHCP 服务器模块的计算机为目标，获取该模块的 **PSModuleInfo** 对象，将其保存在变量中 `$m` ，然后 `Save-Help` 在保存在变量中的对象上运行 `$m` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-184">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="90c95-185">在以下示例中，管理员在没有网络访问权限的计算机上安装 DHCP 服务器模块的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-185">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="90c95-186">首先，运行 `Export-Clixml` 将 **PSModuleInfo** 对象导出到共享文件夹或可移动介质。</span><span class="sxs-lookup"><span data-stu-id="90c95-186">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="90c95-187">接下来，将可移动媒体传输到可访问 internet 的计算机，然后使用导入 **PSModuleInfo** 对象 `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-187">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="90c95-188">运行 `Save-Help` 保存导入的 DhcpServer 模块 **PSModuleInfo** 对象的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-188">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="90c95-189">最后，将可移动媒体传输回没有网络访问的计算机，然后通过运行安装帮助 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-189">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="90c95-190">如果没有参数， `Save-Help` 则会下载会话中所有模块的帮助以及所有支持可更新帮助的已安装模块。</span><span class="sxs-lookup"><span data-stu-id="90c95-190">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="90c95-191">要包含的模块必须安装在 "环境变量" 的值中列出的目录中，该目录位于 `$env:PSModulePath` 要保存帮助的本地计算机或远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="90c95-191">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="90c95-192">它们也是通过运行命令返回的模块 `Get-Help -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-192">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="90c95-193">如何更新不同语言的帮助文件</span><span class="sxs-lookup"><span data-stu-id="90c95-193">How to update help files in different languages</span></span>

<span data-ttu-id="90c95-194">默认情况下， `Update-Help` 和 `Save-Help` cmdlet 会下载在本地计算机上为 Windows 设置的 UI 区域性和语言的帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-194">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="90c95-195">如果指定模块的帮助文件在本地 UI 区域性中不可用，则 `Update-Help` `Save-Help` 使用 Windows 语言回退规则查找支持的最佳语言。</span><span class="sxs-lookup"><span data-stu-id="90c95-195">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="90c95-196">但是，你可以使用和 cmdlet 的 **UICulture** 参数 `Update-Help` `Save-Help` 在可用的任意 UI 区域性中下载和安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-196">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="90c95-197">例如，若要将该会话中所有模块的最新帮助文件以日语 (Ja-jp) 和法语 (fr) ，请键入：</span><span class="sxs-lookup"><span data-stu-id="90c95-197">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="90c95-198">如果在指定的语言中没有可用的模块的帮助文件，则 `Update-Help` 和 cmdlet 会 `Save-Help` 返回一条错误消息，其中列出了每个模块的帮助可用的语言，因此你可以选择最能满足你的需求的替代方法。</span><span class="sxs-lookup"><span data-stu-id="90c95-198">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="90c95-199">目前，可更新的帮助内容仅以英语 (en-us) 发布。</span><span class="sxs-lookup"><span data-stu-id="90c95-199">Currently, Updateable Help content is only published in English (en-US).</span></span> <span data-ttu-id="90c95-200">在某些非 Windows 系统上，必须使用 **UICulture** 参数显式请求 `en-US` 内容。</span><span class="sxs-lookup"><span data-stu-id="90c95-200">On some non-Windows systems you must use the **UICulture** parameter to explicitly request the `en-US` content.</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="90c95-201">如何使用联机帮助</span><span class="sxs-lookup"><span data-stu-id="90c95-201">How to use online help</span></span>

<span data-ttu-id="90c95-202">如果无法或不选择更新本地计算机上的帮助文件，仍可以联机获取最新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-202">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="90c95-203">若要打开任何 cmdlet 或函数的联机帮助主题，请使用 cmdlet 的 **online** 参数 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-203">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="90c95-204">例如，以下命令将 `Get-Job` 在默认 internet 浏览器中打开 cmdlet 的联机帮助主题：</span><span class="sxs-lookup"><span data-stu-id="90c95-204">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="90c95-205">若要获取脚本的联机帮助，请使用 **online** 参数和该脚本的完整路径。</span><span class="sxs-lookup"><span data-stu-id="90c95-205">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="90c95-206">**Online** 参数不适用于主题。</span><span class="sxs-lookup"><span data-stu-id="90c95-206">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="90c95-207">若要查看有关 PowerShell 的 "关于" 主题，包括有关 PowerShell 语言的帮助主题，请参阅 [Powershell 相关主题](about.md)。</span><span class="sxs-lookup"><span data-stu-id="90c95-207">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="90c95-208">如何最大程度地减少或阻止 internet 下载</span><span class="sxs-lookup"><span data-stu-id="90c95-208">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="90c95-209">若要最大程度地减少 internet 下载并向未连接到 internet 的用户提供可更新帮助，请使用 `Save-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c95-209">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="90c95-210">从 internet 下载帮助并将其保存到网络共享。</span><span class="sxs-lookup"><span data-stu-id="90c95-210">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="90c95-211">然后，创建一个 `Update-Help` 在所有计算机上运行命令的组策略设置或计划作业。</span><span class="sxs-lookup"><span data-stu-id="90c95-211">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="90c95-212">将 cmdlet 的 **SourcePath** 参数值设置 `Update-Help` 为网络共享。</span><span class="sxs-lookup"><span data-stu-id="90c95-212">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="90c95-213">若要阻止具有 internet 访问权限的用户从 internet 下载可更新帮助，请使用 **设置 update-help 的默认源路径** 组策略设置。</span><span class="sxs-lookup"><span data-stu-id="90c95-213">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="90c95-214">此组策略设置会将 **SourcePath** 参数（指定的文件系统位置）隐式添加到 `Update-Help` 每个受影响的计算机上的每个命令。</span><span class="sxs-lookup"><span data-stu-id="90c95-214">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="90c95-215">用户可以显式使用 **sourcepath** 参数来指定不同的文件系统位置，但不能排除 **SourcePath** 参数并从 internet 下载帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-215">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="90c95-216">" **设置 update-help 的默认源路径** " 组策略设置出现在 " **计算机配置** " 和 " **用户配置**" 下。</span><span class="sxs-lookup"><span data-stu-id="90c95-216">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="90c95-217">但是，只有 " **计算机配置** " 下的策略设置才有效。</span><span class="sxs-lookup"><span data-stu-id="90c95-217">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="90c95-218">" **用户配置** " 下的策略设置被忽略。</span><span class="sxs-lookup"><span data-stu-id="90c95-218">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="90c95-219">有关详细信息，请参阅 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。</span><span class="sxs-lookup"><span data-stu-id="90c95-219">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="90c95-220">如何更新非标准模块的帮助</span><span class="sxs-lookup"><span data-stu-id="90c95-220">How to update help for non-standard modules</span></span>

<span data-ttu-id="90c95-221">若要更新或保存 cmdlet 的 **ListAvailable** 参数未返回的模块的帮助 `Get-Module` ，请在运行或命令之前将模块导入到当前会话中 `Update-Help` `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="90c95-221">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="90c95-222">在远程计算机上运行命令之前，请将 `Save-Help` 模块导入到当前会话中，或导入 `Invoke-Command` 连接到远程计算机的脚本块。</span><span class="sxs-lookup"><span data-stu-id="90c95-222">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="90c95-223">当模块在当前会话中时，请运行 `Update-Help` `Save-Help` 不带参数的或 cmdlet，或者使用 **module** 参数来指定模块名称。</span><span class="sxs-lookup"><span data-stu-id="90c95-223">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="90c95-224">和 cmdlet 的 **模块** 参数 `Update-Help` `Save-Help` 仅接受模块名称。</span><span class="sxs-lookup"><span data-stu-id="90c95-224">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="90c95-225">它们不接受模块文件的路径。</span><span class="sxs-lookup"><span data-stu-id="90c95-225">They do not accept the path to a module file.</span></span>

<span data-ttu-id="90c95-226">使用此方法来更新或保存 cmdlet 的 **ListAvailable** 参数未返回的任何模块的帮助 `Get-Module` ，如安装在环境变量中未列出的位置的模块 `$env:PSModulePath` ，或模块目录不包含格式不正确的模块 (模块目录不包含至少一个 basename 与目录) 名称相同的文件。</span><span class="sxs-lookup"><span data-stu-id="90c95-226">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="90c95-227">如何支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="90c95-227">How to support updatable help</span></span>

<span data-ttu-id="90c95-228">如果创建模块，则可以支持模块的联机帮助和可更新帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-228">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="90c95-229">有关详细信息，请参阅 Microsoft Docs 中的 [支持可更新帮助](/powershell/scripting/developer/help/supporting-updatable-help) 和 [支持联机帮助](/powershell/scripting/developer/module/supporting-online-help) 。</span><span class="sxs-lookup"><span data-stu-id="90c95-229">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="90c95-230">适用于 PowerShell 管理单元或基于注释的帮助的可更新帮助。</span><span class="sxs-lookup"><span data-stu-id="90c95-230">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="90c95-231">备注</span><span class="sxs-lookup"><span data-stu-id="90c95-231">Remarks</span></span>

<span data-ttu-id="90c95-232">`Update-Help` `Save-Help` (Windows PE) Windows 预安装环境上不支持和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c95-232">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="90c95-233">请参阅</span><span class="sxs-lookup"><span data-stu-id="90c95-233">See also</span></span>

[<span data-ttu-id="90c95-234">Get-Help</span><span class="sxs-lookup"><span data-stu-id="90c95-234">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="90c95-235">Save-Help</span><span class="sxs-lookup"><span data-stu-id="90c95-235">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="90c95-236">Update-Help</span><span class="sxs-lookup"><span data-stu-id="90c95-236">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
