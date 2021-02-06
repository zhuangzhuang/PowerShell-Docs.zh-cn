---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 6996decc6b2f8b99ab9c04d96c487c37f2609c9e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603372"
---
# <span data-ttu-id="5d5c2-102">Save-Help</span><span class="sxs-lookup"><span data-stu-id="5d5c2-102">Save-Help</span></span>

## <span data-ttu-id="5d5c2-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5d5c2-103">SYNOPSIS</span></span>
<span data-ttu-id="5d5c2-104">下载最新的帮助文件，并将其保存到文件系统目录。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-104">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="5d5c2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d5c2-105">SYNTAX</span></span>

### <span data-ttu-id="5d5c2-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="5d5c2-106">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### <span data-ttu-id="5d5c2-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5d5c2-107">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## <span data-ttu-id="5d5c2-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5d5c2-108">DESCRIPTION</span></span>

<span data-ttu-id="5d5c2-109">`Save-Help`Cmdlet 将为 PowerShell 模块下载最新的帮助文件，并将其保存到你指定的目录中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-109">The `Save-Help` cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span> <span data-ttu-id="5d5c2-110">此功能允许你更新不能访问 Internet 的计算机上的帮助文件，并使得更新多台计算机上的帮助文件更加方便。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-110">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="5d5c2-111">在 Windows PowerShell 3.0 中， `Save-Help` 仅适用于在本地计算机上安装的模块。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-111">In Windows PowerShell 3.0, `Save-Help` worked only for modules that are installed on the local computer.</span></span> <span data-ttu-id="5d5c2-112">尽管可以从远程计算机导入模块，或通过使用 PowerShell 远程处理从远程计算机获取对 **PSModuleInfo** 对象的引用，但不会保留 **HelpInfoUri** 属性，并且 `Save-Help` 不能用于远程模块帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-112">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and `Save-Help` would not work for remote module Help.</span></span>

<span data-ttu-id="5d5c2-113">在 Windows PowerShell 4.0 中， **HelpInfoUri** 属性是通过 PowerShell 远程处理保留的，这使 `Save-Help` 可以使用远程计算机上安装的模块。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-113">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables `Save-Help` to work for modules that are installed on remote computers.</span></span> <span data-ttu-id="5d5c2-114">还可以通过在不能访问 Internet 的计算机上运行来将 **PSModuleInfo** 对象保存到磁盘或可移动介质 `Export-Clixml` ，在能够访问 internet 的计算机上导入对象，然后 `Save-Help` 在 **PSModuleInfo** 对象上运行。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-114">It is also possible to save a **PSModuleInfo** object to disk or removable media by running `Export-Clixml` on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="5d5c2-115">通过使用可移动存储媒体（例如 USB 驱动器），可以将保存的帮助传输到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-115">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span> <span data-ttu-id="5d5c2-116">可以通过运行在远程计算机上安装帮助 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-116">The help can be installed on the remote computer by running `Update-Help`.</span></span> <span data-ttu-id="5d5c2-117">此过程可用于在不具有任何类型的网络访问的计算机上安装帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-117">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="5d5c2-118">若要安装保存的帮助文件，请运行 `Update-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-118">To install saved help files, run the `Update-Help` cmdlet.</span></span> <span data-ttu-id="5d5c2-119">添加其 **SourcePath** 参数以指定保存帮助文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-119">Add its **SourcePath** parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="5d5c2-120">如果没有参数，则命令将为 `Save-Help` 会话中的所有模块以及在 **PSModulePath** 环境变量中列出的位置中安装的模块下载最新帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-120">Without parameters, a `Save-Help` command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="5d5c2-121">此操作跳过不支持可更新帮助的模块，而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-121">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="5d5c2-122">`Save-Help`Cmdlet 检查目标文件夹中任何帮助文件的版本。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-122">The `Save-Help` cmdlet checks the version of any help files in the destination folder.</span></span> <span data-ttu-id="5d5c2-123">如果有较新的帮助文件，则此 cmdlet 将从 Internet 下载最新的帮助文件，然后将它们保存在文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-123">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span> <span data-ttu-id="5d5c2-124">`Save-Help`Cmdlet 的工作方式与 `Update-Help` cmdlet 相同，不同之处在于它将下载的 cabinet ( .cab) 文件，而不是从 cabinet 文件中提取帮助文件并将其安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-124">The `Save-Help` cmdlet works just like the `Update-Help` cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="5d5c2-125">为每个模块保存的帮助都包括一个帮助信息 (HelpInfo XML) 文件和一个适用于帮助文件各种 UI 区域性的 Cabinet (.cab) 文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-125">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="5d5c2-126">你不必从 cabinet 文件中提取帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-126">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="5d5c2-127">该 `Update-Help` cmdlet 将提取帮助文件、验证 XML 是否安全，然后将帮助文件和帮助信息文件安装在 module 文件夹的特定于语言的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-127">The `Update-Help` cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="5d5c2-128">若要将 PowerShell 安装文件夹中的模块的帮助文件保存 (`$pshome\Modules`) ，请使用 "以管理员身份运行" 选项启动 powershell。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-128">To save the help files for modules in the PowerShell installation folder (`$pshome\Modules`), start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="5d5c2-129">你必须是计算机上 Administrators 组的成员，才能为这些模块下载帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-129">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="5d5c2-130">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-130">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5d5c2-131">示例</span><span class="sxs-lookup"><span data-stu-id="5d5c2-131">EXAMPLES</span></span>

### <span data-ttu-id="5d5c2-132">示例 1：为 DhcpServer 模块保存帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-132">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="5d5c2-133">此示例显示了三种不同的方法，可用于 `Save-Help` 从连接 Internet 的客户端计算机保存 **DhcpServer** 模块的帮助，而无需在本地计算机上安装 **DhcpServer** 模块或 DHCP 服务器角色。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-133">This example shows three different ways to use `Save-Help` to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="5d5c2-134">示例 2：为 DhcpServer 模块安装帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-134">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="5d5c2-135">此示例演示如何在不能访问 Internet 的计算机上为 **DhcpServer** 模块安装你在示例1中保存的帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-135">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="5d5c2-136">示例 3：为所有模块保存帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-136">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="5d5c2-137">此命令将为本地计算机上针对 Windows 所设置的 UI 区域性中的所有模块下载最新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-137">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span> <span data-ttu-id="5d5c2-138">它将帮助文件保存在 `\\Server01\Fileshare01` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-138">It saves the help files in the `\\Server01\Fileshare01` folder.</span></span>

### <span data-ttu-id="5d5c2-139">示例 4：为计算机上的模块保存帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-139">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="5d5c2-140">此命令将为 **ServerManager** 模块下载最新的帮助文件，然后将它们保存在 `\\Server01\Fileshare01` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-140">This command downloads the newest help files for the **ServerManager** module, and then saves them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="5d5c2-141">如果模块已安装在计算机上，你可以键入该模块名称作为 **Module** 参数的值，即使该模块未导入到当前会话中也是如此。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-141">When a module is installed on the computer, you can type the module name as the value of the **Module** parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="5d5c2-142">该命令使用 **Credential** 参数来提供有权写入文件共享的用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-142">The command uses the **Credential** parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="5d5c2-143">示例 5：为其他计算机上的模块保存帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-143">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="5d5c2-144">这些命令将为 **CustomSQL** 模块下载最新的帮助文件，并将它们保存在 `\\Server01\Fileshare01` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-144">These commands download the newest help files for the **CustomSQL** module and save them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="5d5c2-145">由于 **CustomSQL** 模块未安装在计算机上，因此序列包含一个 `Invoke-Command` 命令，该命令从 Server02 计算机获取 CustomSQL 模块的模块对象，然后通过管道将模块对象传递给 `Save-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-145">Because the **CustomSQL** module is not installed on the computer, the sequence includes an `Invoke-Command` command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the `Save-Help` cmdlet.</span></span>

<span data-ttu-id="5d5c2-146">如果未在计算机上安装模块， `Save-Help` 则需要 module 对象，其中包括有关最新帮助文件位置的信息。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-146">When a module is not installed on the computer, `Save-Help` needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="5d5c2-147">示例 6：为采用多种语言的模块保存帮助</span><span class="sxs-lookup"><span data-stu-id="5d5c2-147">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="5d5c2-148">此命令在四个不同的 UI 区域性中为 PowerShell Core 模块保存帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-148">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span> <span data-ttu-id="5d5c2-149">这些区域设置的语言包不必安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-149">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="5d5c2-150">`Save-Help` 仅当模块所有者使翻译后的文件在 Internet 上可用时，才能为不同 UI 区域性中的模块下载帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-150">`Save-Help` can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="5d5c2-151">示例7：每天保存帮助一次以上</span><span class="sxs-lookup"><span data-stu-id="5d5c2-151">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="5d5c2-152">此命令将为安装在计算机上的所有模块保存帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-152">This command saves help for all modules that are installed on the computer.</span></span> <span data-ttu-id="5d5c2-153">命令指定 **Force** 参数以替代规则，该规则阻止 `Save-Help` cmdlet 在每24小时内下载帮助多次。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-153">The command specifies the **Force** parameter to override the rule that prevents the `Save-Help` cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="5d5c2-154">**Force** 参数还会重写 1 GB 限制并绕过版本检查。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-154">The **Force** parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="5d5c2-155">因此，你可以下载文件，即使版本不高于目标文件夹中的版本。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-155">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="5d5c2-156">该命令使用 `Save-Help` cmdlet 将帮助文件下载并保存到指定的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-156">The command uses the `Save-Help` cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="5d5c2-157">需要多次运行命令时， **Force** 参数是必需的 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-157">The **Force** parameter is required when you have to run a `Save-Help` command more than one time each day.</span></span>

## <span data-ttu-id="5d5c2-158">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5d5c2-158">PARAMETERS</span></span>

### <span data-ttu-id="5d5c2-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="5d5c2-159">-Credential</span></span>

<span data-ttu-id="5d5c2-160">指定用户凭据。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-160">Specifies a user credential.</span></span> <span data-ttu-id="5d5c2-161">此 cmdlet 使用有权访问 **DestinationPath** 参数指定的文件系统位置的用户的凭据运行该命令。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-161">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="5d5c2-162">仅当命令中使用了 **DestinationPath** 或 **LiteralPath** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-162">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="5d5c2-163">此参数使你可以 `Save-Help` 在远程计算机上运行使用 **DestinationPath** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-163">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="5d5c2-164">通过提供显式凭据，你可以在远程计算机上运行该命令并访问第三台计算机上的文件共享，而不会遇到 "拒绝访问" 错误或使用 CredSSP 身份验证委派凭据。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-164">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="5d5c2-165">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-165">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="5d5c2-166">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-166">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="5d5c2-167">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-167">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="5d5c2-168">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-168">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-169">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="5d5c2-169">-DestinationPath</span></span>

<span data-ttu-id="5d5c2-170">指定保存帮助文件的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-170">Specifies the path of the folder in which the help files are saved.</span></span> <span data-ttu-id="5d5c2-171">不要指定文件名或文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-171">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-172">-Force</span><span class="sxs-lookup"><span data-stu-id="5d5c2-172">-Force</span></span>

<span data-ttu-id="5d5c2-173">指示此 cmdlet 不遵循每日一次的限制，跳过版本检查，并下载超出 1 GB 限制的文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-173">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="5d5c2-174">如果不使用此参数， `Save-Help` 则每24小时内只允许使用每个模块一个命令，每个模块的下载限制为每个模块 1 GB 的未压缩内容，并且仅当版本比计算机上的文件更新时，才会安装模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-174">Without this parameter, only one `Save-Help` command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="5d5c2-175">每日一次限制会保护托管帮助文件的服务器，并使你能够将 `Save-Help` 命令添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-175">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a `Save-Help` command to your PowerShell profile.</span></span>

<span data-ttu-id="5d5c2-176">若要在没有 **Force** 参数的情况下，为多个 UI 区域性中的模块保存帮助，请将所有 UI 区域性包括在同一命令中，例如：`Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="5d5c2-176">To save help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-177">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="5d5c2-177">-FullyQualifiedModule</span></span>

<span data-ttu-id="5d5c2-178">指定名称以 **ModuleSpecification** 对象的形式指定的模块。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-178">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="5d5c2-179">请参阅 ModuleSpecification 构造函数的 "备注" 部分 [ (哈希表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-179">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="5d5c2-180">例如， **FullyQualifiedModule** 参数接受以下任何一种格式指定的模块名称：</span><span class="sxs-lookup"><span data-stu-id="5d5c2-180">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="5d5c2-181">**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-181">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="5d5c2-182">不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-182">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="5d5c2-183">这两个参数是互斥的。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-183">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5d5c2-184">-LiteralPath</span></span>

<span data-ttu-id="5d5c2-185">指定目标文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-185">Specifies a path of the destination folder.</span></span> <span data-ttu-id="5d5c2-186">与 **DestinationPath** 参数的值不同，**LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-186">Unlike the value of the **DestinationPath** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="5d5c2-187">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-187">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="5d5c2-188">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5d5c2-189">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-190">-Module</span><span class="sxs-lookup"><span data-stu-id="5d5c2-190">-Module</span></span>

<span data-ttu-id="5d5c2-191">指定此 cmdlet 为其下载帮助的模块。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-191">Specifies modules for which this cmdlet downloads help.</span></span> <span data-ttu-id="5d5c2-192">在以逗号分隔的列表中输入一个或多个模块名称或名称模式，或在每行上有一个模块名称的文件中输入。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-192">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span> <span data-ttu-id="5d5c2-193">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="5d5c2-194">还可以通过管道将模块对象从 `Get-Module` cmdlet 传递给 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-194">You can also pipe module objects from the `Get-Module` cmdlet to `Save-Help`.</span></span>

<span data-ttu-id="5d5c2-195">默认情况下， `Save-Help` 为所有支持可更新帮助的模块下载帮助，并将其安装在本地计算机上的 **PSModulePath** 环境变量中列出的位置。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-195">By default, `Save-Help` downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="5d5c2-196">若要为未安装在计算机上的模块保存帮助，请 `Get-Module` 在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-196">To save help for modules that are not installed on the computer, run a `Get-Module` command on a remote computer.</span></span> <span data-ttu-id="5d5c2-197">然后，通过管道将生成的模块对象传递给 `Save-Help` cmdlet，或将 module 对象提交为 **模块** 或 **InputObject** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-197">Then pipe the resulting module objects to the `Save-Help` cmdlet or submit the module objects as the value of the **Module** or **InputObject** parameters.</span></span>

<span data-ttu-id="5d5c2-198">如果你指定的模块安装在计算机上，你可以输入模块名称或模块对象。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-198">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span> <span data-ttu-id="5d5c2-199">如果该模块未安装在计算机上，则必须输入一个模块对象，例如 cmdlet 返回的模块对象 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-199">If the module is not installed on the computer, you must enter a module object, such as one returned by the `Get-Module` cmdlet.</span></span>

<span data-ttu-id="5d5c2-200">Cmdlet 的 **module** 参数 `Save-Help` 不接受模块文件或模块清单文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-200">The **Module** parameter of the `Save-Help` cmdlet does not accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="5d5c2-201">若要为不在 **PSModulePath** 位置的模块保存帮助，请在运行该命令之前将模块导入到当前会话中 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-201">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the `Save-Help` command.</span></span>

<span data-ttu-id="5d5c2-202">值为 "\*" (所有) 尝试为计算机上安装的所有模块更新帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-202">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="5d5c2-203">这包括不支持可更新帮助的模块。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-203">This includes modules that do not support Updatable Help.</span></span> <span data-ttu-id="5d5c2-204">当该命令遇到不支持可更新帮助的模块时，此值可能会生成错误。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-204">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5d5c2-205">-UICulture</span><span class="sxs-lookup"><span data-stu-id="5d5c2-205">-UICulture</span></span>

<span data-ttu-id="5d5c2-206">指定此 cmdlet 为其获取更新的帮助文件的 UI 区域性值。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-206">Specifies UI culture values for which this cmdlet gets updated help files.</span></span> <span data-ttu-id="5d5c2-207">输入一个或多个语言代码（如 `es-ES` ）、包含区域性对象的变量或用于获取区域性对象的命令，例如 `Get-Culture` 或 `Get-UICulture` 命令。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-207">Enter one or more language codes, such as `es-ES`, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span>

<span data-ttu-id="5d5c2-208">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-208">Wildcard characters are not permitted.</span></span> <span data-ttu-id="5d5c2-209">不要指定部分语言代码，例如 "de"。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-209">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="5d5c2-210">默认情况下， `Save-Help` 将在为 Windows 设置的 UI 区域性或其回退区域性中获取帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-210">By default, `Save-Help` gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="5d5c2-211">如果指定 **UICulture** 参数，则 `Save-Help` 仅为指定的 UI 区域性查找帮助，而不会在任何回退区域性中查找帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-211">If you specify the **UICulture** parameter, `Save-Help` looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-212">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="5d5c2-212">-UseDefaultCredentials</span></span>

<span data-ttu-id="5d5c2-213">指示此 cmdlet 用当前用户的凭据运行命令，包括 web 下载。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-213">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span> <span data-ttu-id="5d5c2-214">默认情况下，在没有显式凭据的情况下运行该命令。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-214">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="5d5c2-215">仅当 Web 下载使用 NTLM、协商或基于 Kerberos 的身份验证时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-215">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-216">-Scope</span><span class="sxs-lookup"><span data-stu-id="5d5c2-216">-Scope</span></span>

<span data-ttu-id="5d5c2-217">此参数不在此 cmdlet 中执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-217">This paramater does nothing in this cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5d5c2-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d5c2-218">CommonParameters</span></span>

<span data-ttu-id="5d5c2-219">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d5c2-220">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d5c2-221">输入</span><span class="sxs-lookup"><span data-stu-id="5d5c2-221">INPUTS</span></span>

### <span data-ttu-id="5d5c2-222">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="5d5c2-222">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="5d5c2-223">可以通过管道将模块对象从 `Get-Module` cmdlet 传递给的 **module** 参数 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-223">You can pipe a module object from the `Get-Module` cmdlet to the **Module** parameter of `Save-Help`.</span></span>

## <span data-ttu-id="5d5c2-224">输出</span><span class="sxs-lookup"><span data-stu-id="5d5c2-224">OUTPUTS</span></span>

### <span data-ttu-id="5d5c2-225">无</span><span class="sxs-lookup"><span data-stu-id="5d5c2-225">None</span></span>

<span data-ttu-id="5d5c2-226">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5d5c2-227">注释</span><span class="sxs-lookup"><span data-stu-id="5d5c2-227">NOTES</span></span>

- <span data-ttu-id="5d5c2-228">若要为 $pshome \Modules 文件夹中的模块保存帮助，请使用 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-228">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="5d5c2-229">只有计算机上 Administrators 组的成员才能为 $pshome \Modules 文件夹中的模块下载帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-229">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
- <span data-ttu-id="5d5c2-230">为每个模块保存的帮助都包括一个帮助信息 (HelpInfo XML) 文件和一个适用于帮助文件各种 UI 区域性的 Cabinet (.cab) 文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-230">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="5d5c2-231">你不必从 cabinet 文件中提取帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-231">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="5d5c2-232">`Update-Help`Cmdlet 将提取帮助文件、验证 XML，然后将帮助文件和帮助信息文件安装在 module 文件夹的特定于语言的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-232">The `Update-Help` cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
- <span data-ttu-id="5d5c2-233">`Save-Help`Cmdlet 可以为未安装在计算机上的模块保存帮助。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-233">The `Save-Help` cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="5d5c2-234">但是，由于帮助文件安装在模块文件夹中，因此 `Update-Help` cmdlet 只能为计算机上安装的模块安装更新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-234">However, because help files are installed in the module folder, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
- <span data-ttu-id="5d5c2-235">如果找 `Save-Help` 不到模块的更新帮助文件，或者找不到指定语言的更新帮助文件，它将以无提示方式继续，而不显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-235">If `Save-Help` cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="5d5c2-236">若要查看命令保存了哪些文件，请指定 **详细** 参数。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-236">To see which files were saved by the command, specify the **Verbose** parameter.</span></span>
- <span data-ttu-id="5d5c2-237">模块是可更新帮助的最小单位。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-237">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="5d5c2-238">不能为特定 cmdlet 保存帮助，只保存模块中的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-238">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="5d5c2-239">若要查找包含特定 cmdlet 的模块，请结合使用 **ModuleName** 属性和 `Get-Command` cmdlet，例如 `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="5d5c2-239">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the `Get-Command` cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
- <span data-ttu-id="5d5c2-240">`Save-Help` 支持所有模块和 PowerShell Core 管理单元。它不支持任何其他管理单元。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-240">`Save-Help` supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
- <span data-ttu-id="5d5c2-241">`Update-Help`和 `Save-Help` cmdlet 使用以下端口下载帮助文件：针对 HTTP 使用端口80，为 HTTPS 使用端口443。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-241">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
- <span data-ttu-id="5d5c2-242">`Update-Help` `Save-Help` (Windows PE) Windows 预安装环境上不支持和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5d5c2-242">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="5d5c2-243">相关链接</span><span class="sxs-lookup"><span data-stu-id="5d5c2-243">RELATED LINKS</span></span>

[<span data-ttu-id="5d5c2-244">Get-Help</span><span class="sxs-lookup"><span data-stu-id="5d5c2-244">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="5d5c2-245">Get-Module</span><span class="sxs-lookup"><span data-stu-id="5d5c2-245">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="5d5c2-246">Update-Help</span><span class="sxs-lookup"><span data-stu-id="5d5c2-246">Update-Help</span></span>](Update-Help.md)
