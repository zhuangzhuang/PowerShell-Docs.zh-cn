---
description: 介绍会话配置，用于确定可远程连接到计算机的用户以及他们可以运行的命令。
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603821"
---
# <a name="about-session-configurations"></a><span data-ttu-id="5f4ee-103">关于会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-103">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="5f4ee-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="5f4ee-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="5f4ee-105">介绍会话配置，用于确定可远程连接到计算机的用户以及他们可以运行的命令。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-105">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="5f4ee-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="5f4ee-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="5f4ee-107">会话配置（也称为 "终结点"）是本地计算机上的一组设置，用于定义在远程或本地用户连接到本地计算机上的 PowerShell 时所创建的 PowerShell 会话的环境。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-107">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="5f4ee-108">计算机管理员可以使用会话配置来保护计算机，并为连接到计算机的用户定义自定义环境。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-108">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="5f4ee-109">管理员还可以使用会话配置来确定连接到计算机所需的权限。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-109">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="5f4ee-110">默认情况下，只有 Administrators 组的成员才有权使用会话配置进行远程连接，但你可以更改默认设置，以允许所有用户或所选用户远程连接到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-110">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="5f4ee-111">从 PowerShell 3.0 开始，你可以使用会话配置文件来定义会话配置的元素。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-111">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="5f4ee-112">使用此功能可以轻松地自定义会话，而无需编写代码和发现会话配置的属性。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-112">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="5f4ee-113">若要创建会话配置文件，请使用 New-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-113">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-114">有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-114">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="5f4ee-115">会话配置是 Web 服务的一项功能，用于管理 (WS-MANAGEMENT) 的 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-115">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="5f4ee-116">仅当你使用新的-PSSession、Invoke 命令或 Enter-PSSession cmdlet 连接到远程计算机时，才使用它们。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-116">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="5f4ee-117">注意：若要管理会话配置，请以 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-117">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="5f4ee-118">关于会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-118">About Session Configurations</span></span>

<span data-ttu-id="5f4ee-119">每个 PowerShell 会话都使用会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-119">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="5f4ee-120">这包括你使用 New-PSSession 或 Enter-PSSession cmdlet 创建的持久会话，以及 PowerShell 在你使用使用基于 WS-MANAGEMENT 的远程处理技术（如调用-Command）的 cmdlet 的 ComputerName 参数时创建的临时会话。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-120">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="5f4ee-121">管理员可以使用会话配置来保护计算机的资源，并为连接到计算机的用户创建自定义环境。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-121">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="5f4ee-122">例如，你可以使用会话配置来限制计算机在会话中接收的对象的大小，定义会话的语言模式，以及指定会话中可用的 cmdlet、提供程序和功能。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-122">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="5f4ee-123">通过配置会话配置的安全描述符，你可以确定哪些用户可以使用会话配置来连接到计算机。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-123">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="5f4ee-124">用户必须具有会话配置的 "执行" 权限才能在会话中使用该会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-124">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="5f4ee-125">如果用户没有在计算机上使用任何会话配置所需的权限，则该用户无法远程连接到该计算机。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-125">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="5f4ee-126">默认情况下，只有计算机的管理员才有权使用默认的会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-126">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="5f4ee-127">但是，可以更改安全描述符，以允许所有人、没有用户或仅选定的用户使用计算机上的会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-127">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="5f4ee-128">内置会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-128">Built-in Session Configurations</span></span>

<span data-ttu-id="5f4ee-129">PowerShell 3.0 包括名为 Microsoft PowerShell 和 Microsoft PowerShell 的内置会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-129">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="5f4ee-130">在运行64位版本 Windows 的计算机上，PowerShell 还提供 Microsoft.powershell32，即32位会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-130">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="5f4ee-131">默认情况下，Microsoft PowerShell 会话配置用于会话，即，当创建会话的命令不包含新的 PSSession、ConfigurationName 或 Invoke-Command cmdlet 的参数时。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-131">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="5f4ee-132">默认会话配置的安全描述符仅允许本地计算机上 Administrators 组的成员使用这些配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-132">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="5f4ee-133">因此，只有 Administrators 组的成员才能远程连接到计算机，除非更改默认设置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-133">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="5f4ee-134">您可以使用 $PSSessionConfigurationName 首选项变量来更改默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-134">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="5f4ee-135">有关详细信息，请参阅 about_Preference_Variables。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-135">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="5f4ee-136">查看本地计算机上的会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-136">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="5f4ee-137">若要获取本地计算机上的会话配置，请使用 Get-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-137">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="5f4ee-138">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-138">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="5f4ee-139">会话配置对象在 PowerShell 3.0 中展开，以显示使用会话配置文件配置的会话配置的属性。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-139">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="5f4ee-140">例如，若要查看会话配置对象的所有属性，请键入：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-140">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="5f4ee-141">你还可以在 PowerShell 中使用 WSMan 提供程序来查看会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-141">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="5f4ee-142">WSMan 提供程序在会话中创建 WSMAN：驱动器。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-142">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="5f4ee-143">在 WSMAN：驱动器中，会话配置在 "插件" 节点中。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-143">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="5f4ee-144"> (所有会话配置都在 "插件" 节点中，但在 "插件" 节点中有一些不是会话配置的项。 ) </span><span class="sxs-lookup"><span data-stu-id="5f4ee-144">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="5f4ee-145">例如，若要查看本地计算机上的会话配置，请键入：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-145">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="5f4ee-146">查看远程计算机上的会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-146">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="5f4ee-147">若要查看远程计算机上的会话配置，请使用 Connect-WSMan cmdlet 将远程计算机的备注添加到本地计算机上的 WSMAN：驱动器中，然后使用 WSMAN：驱动器查看会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-147">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="5f4ee-148">例如，以下命令将 Server01 远程计算机的节点添加到本地计算机上的 WSMAN：驱动器。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-148">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="5f4ee-149">完成该命令后，可以导航到 Server01 计算机的节点，以查看会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-149">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="5f4ee-150">例如：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-150">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="5f4ee-151">更改会话配置的安全描述符</span><span class="sxs-lookup"><span data-stu-id="5f4ee-151">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="5f4ee-152">在 Windows Server 2012 和更新版本的 Windows Server 中，默认情况下为远程用户启用内置会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-152">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="5f4ee-153">在其他受支持的 Windows 版本中，你必须将会话配置的安全描述符更改为允许远程访问。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-153">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="5f4ee-154">若要启用对计算机上的会话配置的远程访问，请使用 Enable-PSRemoting cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-154">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="5f4ee-155">此 cmdlet 将创建两个会话配置：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-155">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="5f4ee-156">名称定义为： "PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-156">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="5f4ee-157">+ "当前 PowerShell 版本"</span><span class="sxs-lookup"><span data-stu-id="5f4ee-157">+ "current PowerShell version"</span></span>
- <span data-ttu-id="5f4ee-158">对于任何特定 PowerShell 版本，名称为 "untied"。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-158">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="5f4ee-159">另外，默认情况下，只有计算机上 Administrators 组的成员才具有对默认会话配置的 Execute 权限，但你可以更改默认会话配置和你创建的任何会话配置上的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-159">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="5f4ee-160">若要授予其他用户远程连接到计算机的权限，请使用 Set-PSSessionConfiguration cmdlet 将这些用户的 "执行" 权限添加到 Microsoft PowerShell 和 Microsoft.powershell32 会话配置的安全描述符中。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-160">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="5f4ee-161">例如，下面的命令将打开一个属性页，您可以使用该属性页更改 Microsoft PowerShell 默认会话配置的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-161">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="5f4ee-162">若要拒绝每个人对计算机上所有会话配置的权限，请使用 Disable-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-162">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-163">例如，以下命令禁用计算机上的默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-163">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="5f4ee-164">若要防止远程用户连接到计算机，但允许本地用户进行连接，请使用 Disable-PSRemoting cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-164">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="5f4ee-165">Disable-PSRemoting 将 "Network_Deny_All" 条目添加到计算机上的所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-165">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="5f4ee-166">若要允许远程用户使用计算机上的所有会话配置，请使用 Enable-PSRemoting 或 Enable-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-166">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-167">例如，以下命令启用对内置会话配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-167">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="5f4ee-168">若要对会话配置的安全描述符进行其他更改，请使用 Set-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-168">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-169">使用 SecurityDescriptorSDDL 参数提交 SDDL 字符串值。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-169">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="5f4ee-170">使用 ShowSecurityDescriptorUI 参数显示可帮助你创建新 SDDL 的 "用户界面" 属性表。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-170">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="5f4ee-171">例如：</span><span class="sxs-lookup"><span data-stu-id="5f4ee-171">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="5f4ee-172">创建新的会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-172">Creating a New Session Configuration</span></span>

<span data-ttu-id="5f4ee-173">若要在本地计算机上创建新的会话配置，请使用 Register-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-173">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-174">若要定义新的会话配置，可以使用 c # 程序集、PowerShell 脚本和 Register-PSSessionConfiguration cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-174">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="5f4ee-175">例如，以下命令将创建一个与 Microsoft PowerShell 会话配置相同的会话配置，只不过它会将从远程命令收到的数据限制为 20 mb (MB) 。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-175">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="5f4ee-176"> (默认值为 50 MB) 。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-176">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="5f4ee-177">当你创建会话配置时，你可以使用其他会话配置 cmdlet 来管理它，并显示在 WSMAN：驱动器中。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-177">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="5f4ee-178">有关详细信息，请参阅 Set-pssessionconfiguration。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-178">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="5f4ee-179">删除会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-179">Removing a Session Configuration</span></span>

<span data-ttu-id="5f4ee-180">若要从本地计算机中删除会话配置，请使用 Unregister-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-180">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="5f4ee-181">例如，以下命令将从计算机中删除 Newconfig.json 会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-181">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="5f4ee-182">有关详细信息，请参阅 Set-pssessionconfiguration。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-182">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="5f4ee-183">还原会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-183">Restoring a Session Configuration</span></span>

<span data-ttu-id="5f4ee-184">若要还原 (取消注册) 意外删除的默认会话配置，请使用 Enable-PSRemoting cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-184">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="5f4ee-185">Enable-PSRemoting cmdlet 将重新创建计算机上不存在的所有默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-185">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="5f4ee-186">它不会覆盖或更改现有会话配置的属性值。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-186">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="5f4ee-187">若要还原默认会话配置的原始属性值，请使用 Unregister-PSSessionConfiguration 删除会话配置，然后使用 Enable-PSRemoting cmdlet 重新创建它。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-187">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="5f4ee-188">选择会话配置</span><span class="sxs-lookup"><span data-stu-id="5f4ee-188">Selecting a Session Configuration</span></span>

<span data-ttu-id="5f4ee-189">若要为会话选择特定的会话配置，请使用新的-PSSession、Enter-PSSession 或 ConfigurationName 参数。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-189">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="5f4ee-190">例如，此命令使用 New-PSSession cmdlet 来启动 Server01 计算机上的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-190">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="5f4ee-191">该命令使用 ConfigurationName 参数来选择 Server01 计算机上的 WithProfile 配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-191">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="5f4ee-192">仅当当前用户有权使用 WithProfile 会话配置或可以提供具有所需权限的用户的凭据时，此命令才会成功。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-192">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="5f4ee-193">你还可以使用 $PSSessionConfigurationName 首选项变量来更改计算机上的默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-193">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="5f4ee-194">有关 $PSSessionConfigurationName 首选项变量的详细信息，请参阅 about_Preference_Variables。</span><span class="sxs-lookup"><span data-stu-id="5f4ee-194">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="5f4ee-195">字</span><span class="sxs-lookup"><span data-stu-id="5f4ee-195">KEYWORDS</span></span>

<span data-ttu-id="5f4ee-196">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="5f4ee-196">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="5f4ee-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f4ee-197">SEE ALSO</span></span>

[<span data-ttu-id="5f4ee-198">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="5f4ee-198">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="5f4ee-199">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5f4ee-199">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="5f4ee-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5f4ee-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="5f4ee-201">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="5f4ee-201">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="5f4ee-202">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5f4ee-202">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="5f4ee-203">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-203">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="5f4ee-204">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-204">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="5f4ee-205">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-205">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="5f4ee-206">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5f4ee-206">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="5f4ee-207">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-207">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="5f4ee-208">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-208">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="5f4ee-209">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5f4ee-209">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="5f4ee-210">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f4ee-210">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

