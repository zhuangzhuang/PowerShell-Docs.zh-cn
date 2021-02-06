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
# <a name="using-jea"></a>使用 JEA

本文介绍连接和使用 JEA 终结点的各种方式。

## <a name="using-jea-interactively"></a>以交互方式使用 JEA

如果你正在测试 JEA 配置或需要用户执行简单任务，可采用与进行常规 PowerShell 远程处理会话相同的方式使用 JEA。 对于复杂的远程处理任务，建议使用[隐式远程处理](#using-jea-with-implicit-remoting)。 通过隐式远程处理，用户可在本地处理数据对象。

若要以交互方式使用 JEA，需要提供以下信息：

- 要连接到的计算机的名称（可以是本地计算机）
- 在该计算机上注册的 JEA 终结点名称
- 在该计算机上有权访问 JEA 终结点的凭据

考虑到该信息，可使用 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 开始 JEA 会话。

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

如果当前用户帐户有权访问 JEA 终结点，则可省略 Credential 参数。

PowerShell 提示更改为 `[localhost]: PS>` 时，即表示你正在与远程 JEA 会话交互。 可以运行 `Get-Command` 检查哪些命令可用。 咨询管理员，了解可用参数或允许的参数值是否存在任何限制。

请记住，JEA 会话在 NoLanguage 模式下运行。 可能无法使用某些常用的 PowerShell 用法。 例如，无法使用变量来存储数据或检查从 cmdlet 返回的对象的属性。 以下示例显示了为在 NoLanguage 模式下工作而获取相同命令的两种方法。

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

对于让此方法变难的更复杂的命令调用，请考虑使用[隐式远程处理](#using-jea-with-implicit-remoting)或[创建自定义函数](role-capabilities.md#creating-custom-functions)（其中包含所需功能）。

## <a name="using-jea-with-implicit-remoting"></a>将 JEA 与隐式远程处理配合使用

PowerShell 具有隐式远程处理模型，让你能够从远程计算机导入代理 cmdlet，并如同本地命令一样与之交互。 有关隐式远程处理的解释，请参阅“你好，脚本专家！” [博客文章](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)。
当隐式远程处理配合 JEA 使用时非常有用，因为它允许在完整语言模式下使用 JEA cmdlet。 你可使用 Tab 自动补全、变量、操作对象，甚至使用本地脚本对 JEA 终结点自动执行任务。 每次调用代理命令时，数据都会发送到远程计算机上的 JEA 终结点并在此执行。

隐式远程处理工作时，从现有 PowerShell 会话中导入 cmdlet。 可以有选择性地选择使用所选字符串作为每个代理 cmdlet 的名词前缀。 通过前缀，可区分哪些命令适用于远程系统。 系统会创建包含所有代理命令的临时脚本模块，该模块可在本地 PowerShell 会话期间导入。

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> 由于默认 JEA cmdlet 中存在约束，某些系统可能无法导入整个 JEA 会话。 为避免这一问题，请向 `-CommandName` 参数显示提供名称，从 JEA 会话仅导入所需的命令。 将来的更新会解决在受影响的系统上导入整个 JEA 会话方面的问题。

如果由于默认参数存在 JEA 约束而无法导入 JEA 会话，请按照以下步骤操作，从导入的集中筛选出默认命令。 你仍可使用 `Select-Object` 等命令，但只能使用安装在计算机上的本地版本，而非从远程 JEA 会话导入的版本。

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

还可以使用 [Export-pssession](/powershell/module/microsoft.powershell.utility/Export-PSSession) 通过隐式远程处理保留代理 cmdlet。
有关隐式远程处理的详细信息，请参阅 [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) 和 [Import-Module](/powershell/module/microsoft.powershell.core/import-module) 的文档。

## <a name="using-jea-programmatically"></a>以编程方式使用 JEA

JEA 还可用于自动化系统和用户应用程序，例如内部的支持人员应用和网站。 方法和构建与不受约束的 PowerShell 终结点进行通信的应用时采用的方法相同。 请确保该程序的设计符合由 JEA 施加的限制。

对于简单的一次性任务，可使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) 在 JEA 会话中运行命令。

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

若要检查连接到 JEA 会话时哪些命令可用，请运行 `Get-Command` 并循环访问结果以查看允许的参数。

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

要构建 C# 应用，可通过在 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 对象中指定配置名称来创建与 JEA 会话连接的 PowerShell 运行空间。

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

## <a name="using-jea-with-powershell-direct"></a>将 JEA 与 PowerShell Direct 配合使用

Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)；借助此功能，无论虚拟机上的网络配置或远程管理设置如何，Hyper-V 管理员都能使用 PowerShell 管理虚拟机。

可将 PowerShell Direct 与 JEA 结合使用，为 Hyper-V 管理员提供对 VM 的有限访问权限。
如果断开与 VM 的网络连接，并且需要数据中心管理员来修复网络设置，这会非常有用。

无需其他配置即可在 PowerShell Direct 上使用 JEA。 但是，在虚拟机内运行的来宾操作系统必须是 Windows 10、Windows Server 2016 或更高版本。 Hyper-V 管理员可以使用 PSRemoting cmdlet 的 `-VMName` 或 `-VMId` 参数连接到 JEA 终结点：

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

建议创建具有管理系统所需的最低权限的专用用户帐户，供 Hyper-V 管理员使用。 请记住，默认情况下，即使是没有特权的用户，也可通过使用不受约束的 PowerShell 等方式登录到 Windows 计算机。 这使他们能够浏览文件系统，并深入了解操作系统环境。 若要锁定 Hyper-V 管理员并限制其只能通过结合使用 PowerShell Direct 和 JEA 来访问 VM，则必须拒绝向 Hyper-V 管理员的 JEA 帐户授予本地登录权限。
