---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 0d4e5e26184558055a17f99bd5321aaf3f3789f7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597675"
---
# <span data-ttu-id="a1e93-102">PowerShellGet 模块</span><span class="sxs-lookup"><span data-stu-id="a1e93-102">PowerShellGet Module</span></span>

## <span data-ttu-id="a1e93-103">说明</span><span class="sxs-lookup"><span data-stu-id="a1e93-103">Description</span></span>

<span data-ttu-id="a1e93-104">PowerShellGet 是一个模块，其中包含用于发现、安装、更新和发布 PowerShell 项目（如模块、DSC 资源、角色功能和脚本）的命令。</span><span class="sxs-lookup"><span data-stu-id="a1e93-104">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1e93-105">自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="a1e93-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a1e93-106">如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="a1e93-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a1e93-107">使用以下命令可以确定使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="a1e93-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a1e93-108">有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。</span><span class="sxs-lookup"><span data-stu-id="a1e93-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a1e93-109">PowerShellGet Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a1e93-109">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="a1e93-110">Find-Command</span><span class="sxs-lookup"><span data-stu-id="a1e93-110">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="a1e93-111">查找模块中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="a1e93-111">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="a1e93-112">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="a1e93-112">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="a1e93-113"> (DSC) 资源中查找所需的状态配置。</span><span class="sxs-lookup"><span data-stu-id="a1e93-113">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="a1e93-114">Find-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-114">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="a1e93-115">查找存储库中与指定条件匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="a1e93-115">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="a1e93-116">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a1e93-116">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="a1e93-117">在模块中查找角色功能。</span><span class="sxs-lookup"><span data-stu-id="a1e93-117">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="a1e93-118">Find-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-118">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="a1e93-119">查找脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-119">Finds a script.</span></span>

### [<span data-ttu-id="a1e93-120">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a1e93-120">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="a1e93-121">获取由 PowerShellGet 安装的计算机上的模块列表。</span><span class="sxs-lookup"><span data-stu-id="a1e93-121">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="a1e93-122">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="a1e93-122">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="a1e93-123">获取已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-123">Gets an installed script.</span></span>

### [<span data-ttu-id="a1e93-124">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a1e93-124">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="a1e93-125">获取 PowerShell 存储库。</span><span class="sxs-lookup"><span data-stu-id="a1e93-125">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="a1e93-126">Install-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-126">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="a1e93-127">从存储库中下载一个或多个模块，并将其安装在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="a1e93-127">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="a1e93-128">Install-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-128">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="a1e93-129">安装脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-129">Installs a script.</span></span>

### [<span data-ttu-id="a1e93-130">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a1e93-130">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="a1e93-131">使用元数据创建脚本文件。</span><span class="sxs-lookup"><span data-stu-id="a1e93-131">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="a1e93-132">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-132">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="a1e93-133">将指定模块从本机计算机发布到联机库。</span><span class="sxs-lookup"><span data-stu-id="a1e93-133">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="a1e93-134">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-134">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="a1e93-135">发布脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-135">Publishes a script.</span></span>

### [<span data-ttu-id="a1e93-136">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a1e93-136">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="a1e93-137">注册 PowerShell 存储库。</span><span class="sxs-lookup"><span data-stu-id="a1e93-137">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="a1e93-138">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-138">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="a1e93-139">将模块及其依赖项保存在本地计算机上，但不会安装该模块。</span><span class="sxs-lookup"><span data-stu-id="a1e93-139">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="a1e93-140">Save-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-140">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="a1e93-141">保存脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-141">Saves a script.</span></span>

### [<span data-ttu-id="a1e93-142">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a1e93-142">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="a1e93-143">为已注册的存储库设置值。</span><span class="sxs-lookup"><span data-stu-id="a1e93-143">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="a1e93-144">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a1e93-144">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="a1e93-145">验证脚本的注释块。</span><span class="sxs-lookup"><span data-stu-id="a1e93-145">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="a1e93-146">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-146">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="a1e93-147">卸载模块。</span><span class="sxs-lookup"><span data-stu-id="a1e93-147">Uninstalls a module.</span></span>

### [<span data-ttu-id="a1e93-148">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-148">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="a1e93-149">卸载脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-149">Uninstalls a script.</span></span>

### [<span data-ttu-id="a1e93-150">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a1e93-150">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="a1e93-151">取消注册存储库。</span><span class="sxs-lookup"><span data-stu-id="a1e93-151">Unregisters a repository.</span></span>

### [<span data-ttu-id="a1e93-152">Update-Module</span><span class="sxs-lookup"><span data-stu-id="a1e93-152">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="a1e93-153">从联机库中下载指定模块的最新版本，并将其安装到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="a1e93-153">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="a1e93-154">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a1e93-154">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="a1e93-155">更新模块清单文件。</span><span class="sxs-lookup"><span data-stu-id="a1e93-155">Updates a module manifest file.</span></span>

### [<span data-ttu-id="a1e93-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="a1e93-156">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="a1e93-157">更新脚本。</span><span class="sxs-lookup"><span data-stu-id="a1e93-157">Updates a script.</span></span>

### [<span data-ttu-id="a1e93-158">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a1e93-158">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="a1e93-159">更新脚本的信息。</span><span class="sxs-lookup"><span data-stu-id="a1e93-159">Updates information for a script.</span></span>
