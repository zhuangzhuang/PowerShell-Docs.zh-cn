---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 使用 JEA
description: 本文介绍连接和使用 JEA 终结点的各种方式。
ms.openlocfilehash: b3d81cc0aa76549c81136e5a1a5af28df9c6fa7a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501535"
---
# <a name="using-jea"></a><span data-ttu-id="5b7f6-104">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b7f6-104">Using JEA</span></span>

<span data-ttu-id="5b7f6-105">本文介绍连接和使用 JEA 终结点的各种方式。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-105">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="5b7f6-106">以交互方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b7f6-106">Using JEA interactively</span></span>

<span data-ttu-id="5b7f6-107">如果你正在测试 JEA 配置或需要用户执行简单任务，可采用与进行常规 PowerShell 远程处理会话相同的方式使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-107">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="5b7f6-108">对于复杂的远程处理任务，建议使用[隐式远程处理](#using-jea-with-implicit-remoting)。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-108">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="5b7f6-109">通过隐式远程处理，用户可在本地处理数据对象。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-109">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="5b7f6-110">若要以交互方式使用 JEA，需要提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="5b7f6-110">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="5b7f6-111">要连接到的计算机的名称（可以是本地计算机）</span><span class="sxs-lookup"><span data-stu-id="5b7f6-111">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="5b7f6-112">在该计算机上注册的 JEA 终结点名称</span><span class="sxs-lookup"><span data-stu-id="5b7f6-112">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="5b7f6-113">在该计算机上有权访问 JEA 终结点的凭据</span><span class="sxs-lookup"><span data-stu-id="5b7f6-113">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="5b7f6-114">考虑到该信息，可使用 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 开始 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-114">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="5b7f6-115">如果当前用户帐户有权访问 JEA 终结点，则可省略 Credential 参数。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-115">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="5b7f6-116">PowerShell 提示更改为 `[localhost]: PS>` 时，即表示你正在与远程 JEA 会话交互。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-116">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="5b7f6-117">可以运行 `Get-Command` 检查哪些命令可用。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-117">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="5b7f6-118">咨询管理员，了解可用参数或允许的参数值是否存在任何限制。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-118">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="5b7f6-119">请记住，JEA 会话在 NoLanguage 模式下运行。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-119">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="5b7f6-120">可能无法使用某些常用的 PowerShell 用法。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-120">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="5b7f6-121">例如，无法使用变量来存储数据或检查从 cmdlet 返回的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-121">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="5b7f6-122">以下示例显示了为在 NoLanguage 模式下工作而获取相同命令的两种方法。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-122">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="5b7f6-123">对于让此方法变难的更复杂的命令调用，请考虑使用[隐式远程处理](#using-jea-with-implicit-remoting)或[创建自定义函数](role-capabilities.md#creating-custom-functions)（其中包含所需功能）。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-123">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="5b7f6-124">将 JEA 与隐式远程处理配合使用</span><span class="sxs-lookup"><span data-stu-id="5b7f6-124">Using JEA with implicit remoting</span></span>

<span data-ttu-id="5b7f6-125">PowerShell 具有隐式远程处理模型，让你能够从远程计算机导入代理 cmdlet，并如同本地命令一样与之交互。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-125">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="5b7f6-126">有关隐式远程处理的解释，请参阅“你好，脚本专家！”</span><span class="sxs-lookup"><span data-stu-id="5b7f6-126">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="5b7f6-127">[博客文章](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-127">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="5b7f6-128">当隐式远程处理配合 JEA 使用时非常有用，因为它允许在完整语言模式下使用 JEA cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-128">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="5b7f6-129">你可使用 Tab 自动补全、变量、操作对象，甚至使用本地脚本对 JEA 终结点自动执行任务。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-129">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="5b7f6-130">每次调用代理命令时，数据都会发送到远程计算机上的 JEA 终结点并在此执行。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-130">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="5b7f6-131">隐式远程处理工作时，从现有 PowerShell 会话中导入 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-131">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="5b7f6-132">可以有选择性地选择使用所选字符串作为每个代理 cmdlet 的名词前缀。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-132">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="5b7f6-133">通过前缀，可区分哪些命令适用于远程系统。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-133">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="5b7f6-134">系统会创建包含所有代理命令的临时脚本模块，该模块可在本地 PowerShell 会话期间导入。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-134">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="5b7f6-135">由于默认 JEA cmdlet 中存在约束，某些系统可能无法导入整个 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-135">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="5b7f6-136">为避免这一问题，请向 `-CommandName` 参数显示提供名称，从 JEA 会话仅导入所需的命令。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-136">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="5b7f6-137">将来的更新会解决在受影响的系统上导入整个 JEA 会话方面的问题。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-137">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="5b7f6-138">如果由于默认参数存在 JEA 约束而无法导入 JEA 会话，请按照以下步骤操作，从导入的集中筛选出默认命令。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-138">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="5b7f6-139">你仍可使用 `Select-Object` 等命令，但只能使用安装在计算机上的本地版本，而非从远程 JEA 会话导入的版本。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-139">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="5b7f6-140">还可以使用 [Export-pssession](/powershell/module/microsoft.powershell.utility/Export-PSSession) 通过隐式远程处理保留代理 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-140">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="5b7f6-141">有关隐式远程处理的详细信息，请参阅 [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) 和 [Import-Module](/powershell/module/microsoft.powershell.core/import-module) 的文档。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-141">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/module/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="5b7f6-142">以编程方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b7f6-142">Using JEA programmatically</span></span>

<span data-ttu-id="5b7f6-143">JEA 还可用于自动化系统和用户应用程序，例如内部的支持人员应用和网站。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-143">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="5b7f6-144">方法和构建与不受约束的 PowerShell 终结点进行通信的应用时采用的方法相同。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-144">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="5b7f6-145">请确保该程序的设计符合由 JEA 施加的限制。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-145">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="5b7f6-146">对于简单的一次性任务，可使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) 在 JEA 会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-146">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="5b7f6-147">若要检查连接到 JEA 会话时哪些命令可用，请运行 `Get-Command` 并循环访问结果以查看允许的参数。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-147">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="5b7f6-148">要构建 C# 应用，可通过在 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 对象中指定配置名称来创建与 JEA 会话连接的 PowerShell 运行空间。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-148">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="5b7f6-149">将 JEA 与 PowerShell Direct 配合使用</span><span class="sxs-lookup"><span data-stu-id="5b7f6-149">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="5b7f6-150">Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)；借助此功能，无论虚拟机上的网络配置或远程管理设置如何，Hyper-V 管理员都能使用 PowerShell 管理虚拟机。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-150">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="5b7f6-151">可将 PowerShell Direct 与 JEA 结合使用，为 Hyper-V 管理员提供对 VM 的有限访问权限。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-151">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="5b7f6-152">如果断开与 VM 的网络连接，并且需要数据中心管理员来修复网络设置，这会非常有用。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-152">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="5b7f6-153">无需其他配置即可在 PowerShell Direct 上使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-153">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="5b7f6-154">但是，在虚拟机内运行的来宾操作系统必须是 Windows 10、Windows Server 2016 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-154">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="5b7f6-155">Hyper-V 管理员可以使用 PSRemoting cmdlet 的 `-VMName` 或 `-VMId` 参数连接到 JEA 终结点：</span><span class="sxs-lookup"><span data-stu-id="5b7f6-155">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="5b7f6-156">建议创建具有管理系统所需的最低权限的专用用户帐户，供 Hyper-V 管理员使用。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-156">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="5b7f6-157">请记住，默认情况下，即使是没有特权的用户，也可通过使用不受约束的 PowerShell 等方式登录到 Windows 计算机。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-157">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="5b7f6-158">这使他们能够浏览文件系统，并深入了解操作系统环境。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-158">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="5b7f6-159">若要锁定 Hyper-V 管理员并限制其只能通过结合使用 PowerShell Direct 和 JEA 来访问 VM，则必须拒绝向 Hyper-V 管理员的 JEA 帐户授予本地登录权限。</span><span class="sxs-lookup"><span data-stu-id="5b7f6-159">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
