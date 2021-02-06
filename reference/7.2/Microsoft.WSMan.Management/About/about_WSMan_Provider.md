---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 提供程序
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597883"
---
# <a name="wsman-provider"></a><span data-ttu-id="9a2bc-103">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="9a2bc-103">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="9a2bc-104">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="9a2bc-104">Provider name</span></span>

<span data-ttu-id="9a2bc-105">WSMan</span><span class="sxs-lookup"><span data-stu-id="9a2bc-105">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="9a2bc-106">驱动器</span><span class="sxs-lookup"><span data-stu-id="9a2bc-106">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="9a2bc-107">简短说明</span><span class="sxs-lookup"><span data-stu-id="9a2bc-107">Short description</span></span>

<span data-ttu-id="9a2bc-108">提供对 Web 服务管理 (WS-Management) 配置信息的访问权限。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-108">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="9a2bc-109">详细说明</span><span class="sxs-lookup"><span data-stu-id="9a2bc-109">Detailed description</span></span>

<span data-ttu-id="9a2bc-110">通过用于 PowerShell 的 **WSMan** 提供程序，你可以在本地或远程计算机上添加、更改、清除和删除 WS-Management 配置数据。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-110">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="9a2bc-111">**WSMan** 提供程序使用与 WS-Management 配置设置的逻辑分组相对应的目录结构公开 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-111">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="9a2bc-112">这些分组称为容器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-112">These groupings are known as containers.</span></span>

<span data-ttu-id="9a2bc-113">从 Windows PowerShell 3.0 开始， **WSMan** 提供程序已更新为支持会话配置的新属性，如 **OutputBufferingMode**。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-113">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="9a2bc-114">会话配置在驱动器的插件目录中显示为项目 `WSMan:` ，并且属性在每个会话配置中显示为项。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-114">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="9a2bc-115">**WSMan** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-115">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="9a2bc-116">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9a2bc-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="9a2bc-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9a2bc-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="9a2bc-118">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="9a2bc-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9a2bc-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="9a2bc-120">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="9a2bc-121">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="9a2bc-122">可以使用驱动器中的命令 `WSMan:` 更改新属性的值。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-122">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="9a2bc-123">但是，不能使用 `WSMan:` PowerShell 2.0 中的驱动器来更改 Windows powershell 3.0 中引入的属性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-123">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="9a2bc-124">尽管不会生成任何错误，但命令对于更改这些设置是无效的，使用 Windows PowerShell 3.0 中的 **WSMan** 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-124">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="9a2bc-125">WSMan：驱动器的组织</span><span class="sxs-lookup"><span data-stu-id="9a2bc-125">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="9a2bc-126">**客户端**：你可以配置 WS-Management 客户端的各个方面。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-126">**Client**: You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="9a2bc-127">配置信息存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-127">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="9a2bc-128">**服务**：可以配置 WS-Management 服务的各个方面。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-128">**Service**: You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="9a2bc-129">配置信息存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-129">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-130">服务配置有时称为服务器配置。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-130">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="9a2bc-131">**Shell**：你可以配置 WS-Management 外壳程序的各个方面，例如允许) 远程 Shell 访问 (**AllowRemoteShellAccess** 和允许的最大并发用户 **数 ()** 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-131">**Shell**: You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access (**AllowRemoteShellAccess**) and the maximum number of concurrent users allowed (**MaxConcurrentUsers**).</span></span>

- <span data-ttu-id="9a2bc-132">**侦听器**：你可以创建和配置侦听器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-132">**Listener**: You can create and configure a listener.</span></span> <span data-ttu-id="9a2bc-133">侦听器是一项用于实现 WS-Management 协议以发送和接收消息的管理服务。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-133">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="9a2bc-134">**插件**：插件由 WS-Management 服务加载和使用，以提供各种功能。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-134">**Plugin**: Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="9a2bc-135">默认情况下，PowerShell 提供三个插件：</span><span class="sxs-lookup"><span data-stu-id="9a2bc-135">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="9a2bc-136">事件转发插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-136">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="9a2bc-137">Microsoft PowerShell 插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-137">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="9a2bc-138"> (WMI) 提供程序插件的 Windows Management Instrumentation。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-138">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="9a2bc-139">这三个插件支持事件转发、配置和 WMI 访问。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-139">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="9a2bc-140">**ClientCertificate**：你可以创建和配置客户端证书。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-140">**ClientCertificate**: You can create and configure a client certificate.</span></span>
  <span data-ttu-id="9a2bc-141">当 WS-Management 客户端配置为使用证书身份验证时，将使用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-141">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="9a2bc-142">WSMan 提供程序的目录层次结构</span><span class="sxs-lookup"><span data-stu-id="9a2bc-142">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="9a2bc-143">本地计算机的 WSMan 提供程序的目录层次结构如下所示。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-143">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="9a2bc-144">远程计算机的 WSMan 提供程序的目录层次结构与本地计算机相同。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-144">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="9a2bc-145">但是，为了访问远程计算机的配置设置，你需要使用 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan) 建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-145">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="9a2bc-146">建立与远程计算机的连接后，远程计算机的名称将显示在提供程序中。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-146">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="9a2bc-147">导航 WSMan：驱动器</span><span class="sxs-lookup"><span data-stu-id="9a2bc-147">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="9a2bc-148">此命令使用 `Set-Location` cmdlet 将当前位置更改为 `WSMan:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-148">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="9a2bc-149">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-149">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="9a2bc-150">例如，键入。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-150">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="9a2bc-151">导航到远程系统存储位置</span><span class="sxs-lookup"><span data-stu-id="9a2bc-151">Navigating to a remote system store location</span></span>

<span data-ttu-id="9a2bc-152">此命令使用 `Set-Location` 命令将当前位置更改为远程系统存储位置中的根位置。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-152">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="9a2bc-153">使用反斜杠 `\` 或正斜杠 `/` 来指示驱动器的级别 `WSMan:` 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-153">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="9a2bc-154">以上命令假定与远程系统的连接已存在。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-154">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="9a2bc-155">显示 WSMan：驱动器的内容</span><span class="sxs-lookup"><span data-stu-id="9a2bc-155">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="9a2bc-156">此命令使用 `Get-Childitem` cmdlet 来显示 Localhost 存储位置中的 WS-Management 存储。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-156">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="9a2bc-157">如果在 `WSMan:` 驱动器中，则可以省略驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-157">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="9a2bc-158">此命令使用 `Get-Childitem` cmdlet 来显示远程计算机 "SERVER01" 存储位置中的 WS-Management 存储。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-158">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="9a2bc-159">以上命令假定与远程系统的连接已存在。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-159">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="9a2bc-160">设置 WSMAN：驱动器中的项的值</span><span class="sxs-lookup"><span data-stu-id="9a2bc-160">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="9a2bc-161">可以使用 `Set-Item` cmdlet 更改驱动器中的配置设置 `WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-161">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="9a2bc-162">下面的示例将 **TrustedHosts** 值设置为接受后缀为 "contoso.com" 的所有主机。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-162">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="9a2bc-163">`Set-Item`Cmdlet 支持附加 `-Concatenate` 一个值而不是对其进行更改的附加参数。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-163">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="9a2bc-164">下面的示例将一个新值 "\* domain2.com" 追加到存储在 `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="9a2bc-164">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="9a2bc-165">在 WSMAN：驱动器中创建项</span><span class="sxs-lookup"><span data-stu-id="9a2bc-165">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="9a2bc-166">创建新侦听器</span><span class="sxs-lookup"><span data-stu-id="9a2bc-166">Creating a new listener</span></span>

<span data-ttu-id="9a2bc-167">`New-Item`Cmdlet 在提供程序驱动器中创建项。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-167">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="9a2bc-168">每个提供程序都具有您可以创建的不同项类型。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-168">Each provider has different item types that you can create.</span></span> <span data-ttu-id="9a2bc-169">在 `WSMAN:` 驱动器中，可以创建可配置为接收和响应远程请求的 *侦听器* 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-169">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="9a2bc-170">以下命令使用 cmdlet 创建新的 HTTP 侦听器 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-170">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="9a2bc-171">创建新插件</span><span class="sxs-lookup"><span data-stu-id="9a2bc-171">Creating a new plug-in</span></span>

<span data-ttu-id="9a2bc-172">此命令将为 WS-Management 服务创建（注册）插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-172">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="9a2bc-173">创建新资源条目</span><span class="sxs-lookup"><span data-stu-id="9a2bc-173">Creating a new resource entry</span></span>

<span data-ttu-id="9a2bc-174">此命令在 TestPlugin 的 Resources 目录中创建资源条目。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-174">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="9a2bc-175">此命令假设已使用单独的命令创建了 TestPlugin。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-175">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="9a2bc-176">为资源创建新的安全条目</span><span class="sxs-lookup"><span data-stu-id="9a2bc-176">Creating a new security entry for a resource</span></span>

<span data-ttu-id="9a2bc-177">此命令将在 Resource_5967683（一种特定资源）的 Security 目录中创建一个安全条目。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-177">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="9a2bc-178">此命令假定资源条目是使用单独的命令创建的。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-178">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="9a2bc-179">创建新的客户端证书</span><span class="sxs-lookup"><span data-stu-id="9a2bc-179">Creating a new Client Certificate</span></span>

<span data-ttu-id="9a2bc-180">此命令创建 WS-Management 客户端可以使用的 **ClientCertificate** 项。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-180">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="9a2bc-181">新的 **ClientCertificate** 将在 **ClientCertificate** 目录下显示为 "ClientCertificate_1234567890"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-181">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="9a2bc-182">所有参数都是必需的。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-182">All of the parameters are mandatory.</span></span> <span data-ttu-id="9a2bc-183">**颁发者** 必须是颁发者证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-183">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="9a2bc-184">创建新的初始化参数</span><span class="sxs-lookup"><span data-stu-id="9a2bc-184">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="9a2bc-185">此命令在 "InitializationParameters" 目录中创建名为 "testparametername" 的初始化参数。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-185">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="9a2bc-186">此命令假设已使用单独的命令创建了 "TestPlugin"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-186">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="9a2bc-187">动态参数</span><span class="sxs-lookup"><span data-stu-id="9a2bc-187">Dynamic parameters</span></span>

<span data-ttu-id="9a2bc-188">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-188">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="9a2bc-189">Address \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-189">Address \<String\></span></span>

<span data-ttu-id="9a2bc-190">指定已为其创建此侦听器的地址。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-190">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="9a2bc-191">值可以是下列任一值：</span><span class="sxs-lookup"><span data-stu-id="9a2bc-191">The value can be one of the following:</span></span>

- <span data-ttu-id="9a2bc-192">文本字符串 "\*"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-192">The literal string "\*".</span></span> <span data-ttu-id="9a2bc-193"> (通配符 (`*`) 使命令绑定所有网络适配器上的所有 IP 地址。 ) </span><span class="sxs-lookup"><span data-stu-id="9a2bc-193">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="9a2bc-194">文本字符串 "IP：" 后跟采用 IPv4 点分十进制格式或 IPv6 克隆十六进制格式的有效 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-194">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="9a2bc-195">文本字符串 "MAC：" 后跟适配器的 MAC 地址。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-195">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="9a2bc-196">例如： MAC： 32-a3-58-90。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-196">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="9a2bc-197">在创建侦听器时设置 Address 值。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-197">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-198">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-198">Cmdlets supported</span></span>

- [<span data-ttu-id="9a2bc-199">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-199">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="9a2bc-200">Capability \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-200">Capability \<Enumeration\></span></span>

<span data-ttu-id="9a2bc-201">使用 *插件* 时，此参数将指定 (URI) 的统一资源标识符所支持的操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-201">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="9a2bc-202">你必须为该 URI 支持的每种类型的操作都创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-202">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="9a2bc-203">如果操作支持给定操作，则可以为该操作指定任何有效的特性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-203">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="9a2bc-204">这些属性包括 **SupportsFiltering** 和 **SupportsFragment**。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-204">These attributes include **SupportsFiltering** and **SupportsFragment**.</span></span>

- <span data-ttu-id="9a2bc-205">**Create**： URI 支持创建操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-205">**Create**: Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-206">如果创建操作支持该概念，则使用 **SupportFragment**  属性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-206">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="9a2bc-207">**SupportFiltering** 特性对于 Create 操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-207">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-208">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-208">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-209">**删除**：支持对 URI 执行删除操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-209">**Delete**: Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-210">如果删除操作支持该概念，则使用 **SupportFragment** 属性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-210">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="9a2bc-211">**SupportFiltering** 特性对于删除操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-211">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-212">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-212">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-213">**枚举**：在 URI 上支持枚举操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-213">**Enumerate**: Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-214">枚举操作不支持 **SupportFragment** 属性，并且应将其设置为 False。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-214">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="9a2bc-215">**SupportFiltering** 属性有效，并且如果插件支持筛选，则应将此属性设置为 "True"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-215">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-216">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-216">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-217">**Get**：对 URI 支持 get 操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-217">**Get**: Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-218">如果 Get 操作支持该概念，则使用 **SupportFragment** 属性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-218">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="9a2bc-219">**SupportFiltering** 特性对于 Get 操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-219">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-220">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-220">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-221">**调用**：对 URI 支持调用操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-221">**Invoke**: Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-222">调用操作不支持 **SupportFragment** 属性，并且应将其设置为 False。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-222">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="9a2bc-223">**SupportFiltering** 特性无效，应将其设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-223">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-224">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-224">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-225">**Put**：对 URI 支持 put 运算。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-225">**Put**: Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-226">如果 Put 操作支持该概念，则使用 **SupportFragment** 属性。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-226">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="9a2bc-227">**SupportFiltering** 特性对于 Put 操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-227">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-228">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-228">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-229">**订阅**： URI 上支持订阅操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-229">**Subscribe**: Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-230">订阅操作不支持 **SupportFragment** 属性，并且应将其设置为 False。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-230">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="9a2bc-231">**SupportFiltering** 属性对订阅操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-231">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-232">如果还支持 Shell 操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-232">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="9a2bc-233">**Shell**： URI 支持 shell 操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-233">**Shell**: Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="9a2bc-234">Shell 操作不支持 **SupportFragment** 属性，并且应将其设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-234">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="9a2bc-235">**SupportFiltering** 特性对 Shell 操作无效，应设置为 "False"。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-235">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-236">如果还支持任何其他操作，则此操作对于 URI 无效。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-236">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="9a2bc-237">如果为 URI 配置了 Shell 操作，则将在 WS-Management (WinRM) 服务中从内部处理 Get、Put、Create、Delete、Invoke 和 Enumerate 操作，以管理 shell。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-237">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="9a2bc-238">因此，插件不能处理这些操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-238">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-239">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-239">Cmdlets supported</span></span>

- [<span data-ttu-id="9a2bc-240">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-240">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="9a2bc-241">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-241">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="9a2bc-242">指定服务证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-242">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="9a2bc-243">此值表示证书的指纹字段中两位十六进制值的字符串。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-243">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="9a2bc-244">它指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-244">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="9a2bc-245">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-245">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9a2bc-246">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-246">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="9a2bc-247">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-247">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-248">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-248">Cmdlets supported</span></span>

- [<span data-ttu-id="9a2bc-249">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-249">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="9a2bc-250">Enabled \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-250">Enabled \<Boolean\></span></span>

<span data-ttu-id="9a2bc-251">指定是启用还是禁用侦听器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-251">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="9a2bc-252">默认值为 True。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-252">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-253">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-253">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-254">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-254">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="9a2bc-255">FileName（插件）\<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-255">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="9a2bc-256">指定操作插件的文件名。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-256">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="9a2bc-257">收到请求时，将在用户的上下文中扩展放置在此项中的任何环境变量。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-257">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="9a2bc-258">由于每个用户可能具有相同环境变量的不同版本，因此每个用户都可以具有不同的插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-258">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="9a2bc-259">此项不能为空，并且必须指向有效的插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-259">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-260">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-260">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-261">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-261">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="9a2bc-262">HostName \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-262">HostName \<String\></span></span>

<span data-ttu-id="9a2bc-263">指定在其上运行 WS-Management (WinRM) 服务的计算机的主机名。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-263">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="9a2bc-264">该值必须是完全限定的域名、IPv4 或 IPv6 文字字符串或通配符。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-264">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-265">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-265">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-266">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-266">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="9a2bc-267">Issuer \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-267">Issuer \<String\></span></span>

<span data-ttu-id="9a2bc-268">指定颁发证书的证书颁发机构名称。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-268">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-269">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-269">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-270">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-270">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="9a2bc-271">插件 \<\> WS-Management 插件是 (dll 的本机动态链接库) </span><span class="sxs-lookup"><span data-stu-id="9a2bc-271">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="9a2bc-272">这会插入并扩展 WS-Management 的功能。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-272">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="9a2bc-273">WSW-Management 插件 API 提供了一项功能，使用户能够通过针对受支持的资源 Uri 和操作实现某些 Api 来编写插件。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-273">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="9a2bc-274">为 WS-Management (WinRM) 服务或 Internet Information Services (IIS) 配置插件后，这些插件将分别在 WS-Management 主机或 IIS 主机中加载。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-274">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="9a2bc-275">远程请求会路由到这些插件的入口点以执行操作。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-275">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-276">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-276">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-277">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-277">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="9a2bc-278">Port \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-278">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="9a2bc-279">指定为其创建此侦听器的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-279">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="9a2bc-280">你可以指定 1 到 65535 之间的任何值。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-280">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-281">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-281">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-282">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-282">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="9a2bc-283">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-283">Resource \<String\></span></span>

<span data-ttu-id="9a2bc-284">指定表示不同类型的管理操作或值的终结点。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-284">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="9a2bc-285">服务将公开一个或多个资源，并且一些资源可以具有多个实例。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-285">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="9a2bc-286">管理资源类似于 WMI 类或数据库表，而实例类似于该类的实例或该表中的行。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-286">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="9a2bc-287">例如， **Win32_LogicalDisk** 类表示一个资源。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-287">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="9a2bc-288">`Win32_LogicalDisk="C:\\"` 是资源的特定实例。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-288">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="9a2bc-289">统一资源标识符 (URI) 包含资源的前缀和路径。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-289">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="9a2bc-290">例如：</span><span class="sxs-lookup"><span data-stu-id="9a2bc-290">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-291">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-291">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-292">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-292">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="9a2bc-293">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-293">Resource \<String\></span></span>

<span data-ttu-id="9a2bc-294">指定用于标识计算机上特定类型的资源（例如磁盘或进程）的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-294">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="9a2bc-295">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-295">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="9a2bc-296">例如：</span><span class="sxs-lookup"><span data-stu-id="9a2bc-296">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-297">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-297">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-298">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-298">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="9a2bc-299">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-299">SDKVersion \<String\></span></span>

<span data-ttu-id="9a2bc-300">指定 WS-Management 插件 SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-300">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="9a2bc-301">唯一有效的值是 </span><span class="sxs-lookup"><span data-stu-id="9a2bc-301">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-302">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-302">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-303">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-303">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="9a2bc-304">Subject \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-304">Subject \<String\></span></span>

<span data-ttu-id="9a2bc-305">指定由证书标识的实体。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-305">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-306">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-306">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-307">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-307">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="9a2bc-308">Transport \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-308">Transport \<String\></span></span>

<span data-ttu-id="9a2bc-309">指定要用于发送和接收 WS-Management 协议请求和响应的传输。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-309">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="9a2bc-310">该值必须为 HTTP 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-310">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="9a2bc-311">注意：传输值在创建侦听器时设置。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-311">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-312">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-312">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-313">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-313">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="9a2bc-314">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-314">URI \<String\></span></span>

<span data-ttu-id="9a2bc-315">标识为其基于 Sddl 参数的值授予访问权限的 URI。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-315">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-316">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-316">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-317">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-317">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="9a2bc-318">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-318">URLPrefix \<String\></span></span>

<span data-ttu-id="9a2bc-319">要在其上接受 HTTP 或 HTTPS 请求的 URL 前缀。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-319">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="9a2bc-320">这是一个字符串，其中仅包含字符 `[a-z]` 、 `[A-Z]` 、 `[9-0]` 、下划线 (`_`) 和反斜杠 (`/`) 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-320">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="9a2bc-321">字符串不能以反斜杠开头或结尾 (`/`) 。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-321">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="9a2bc-322">例如，如果计算机名称为 "SampleComputer"，则 WS-Management 客户端将 `http://SampleMachine/URLPrefix` 在目标地址中指定。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-322">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-323">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-323">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-324">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-324">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="9a2bc-325">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-325">Value \<String\></span></span>

<span data-ttu-id="9a2bc-326">指定初始化参数的值，即一个用于指定配置选项的特定于插件的值。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-326">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-327">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-327">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-328">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-328">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="9a2bc-329">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="9a2bc-329">XMLRenderingType \<String\></span></span>

<span data-ttu-id="9a2bc-330">指定通过 **WSMAN_DATA** 对象将 XML 传递到插件的格式。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-330">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="9a2bc-331">下面是有效的值：</span><span class="sxs-lookup"><span data-stu-id="9a2bc-331">The following are valid values:</span></span>

- <span data-ttu-id="9a2bc-332">文本：传入的 XML 数据包含在 **WSMAN_DATA_TYPE_TEXT** 结构中，该结构将 XML 表示为 **PCWSTR** 内存缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-332">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="9a2bc-333">XMLReader：传入的 XML 数据包含在 **WSMAN_DATA_TYPE_WS_XML_READER** 结构中，该结构将 XML 表示为 **XmlReader** 对象，该对象是在 "WebServices" 标头文件中定义的。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-333">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="9a2bc-334">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a2bc-334">Cmdlets Supported</span></span>

- [<span data-ttu-id="9a2bc-335">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a2bc-335">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="9a2bc-336">使用管道</span><span class="sxs-lookup"><span data-stu-id="9a2bc-336">Using the pipeline</span></span>

<span data-ttu-id="9a2bc-337">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-337">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="9a2bc-338">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-338">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="9a2bc-339">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-339">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="9a2bc-340">获取帮助</span><span class="sxs-lookup"><span data-stu-id="9a2bc-340">Getting help</span></span>

<span data-ttu-id="9a2bc-341">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-341">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="9a2bc-342">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="9a2bc-342">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="9a2bc-343">请参阅</span><span class="sxs-lookup"><span data-stu-id="9a2bc-343">See also</span></span>

[<span data-ttu-id="9a2bc-344">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9a2bc-344">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

