---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 注册 JEA 配置
description: 向系统注册 JEA 终结点，使终结点可供用户和自动化引擎使用。
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92499903"
---
# <a name="registering-jea-configurations"></a>注册 JEA 配置

创建[角色功能](role-capabilities.md)和[会话配置文件](session-configurations.md)后，最后一步是注册 JEA 终结点。 向系统注册 JEA 终结点，使终结点可供用户和自动化引擎使用。

## <a name="single-machine-configuration"></a>单个计算机配置

对于小型环境，可以通过使用 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 注册会话配置文件来部署 JEA。

在开始之前，请确保已满足以下先决条件：

- 已创建一个或多个角色，且已将其放置在 PowerShell 模块的“RoleCapabilities”文件夹中。
- 已创建并测试会话配置文件。
- 注册 JEA 配置的用户在系统上具有管理员权限。
- 已选择 JEA 终结点的名称。

用户使用 JEA 连接到系统时，将需要 JEA 终结点名称。 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 列出系统上终结点的名称。 Windows 通常随附以 `microsoft` 开头的终结点。 `microsoft.powershell` 终结点是连接到远程 PowerShell 终结点时使用的默认终结点。

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

运行以下命令来注册终结点。

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 上一命令将在系统上重启 WinRM 服务。 这将终止所有 PowerShell 远程处理会话，以及所有正在进行的 DSC 配置。 建议先将生产计算机脱机，然后再运行命令，以避免中断业务操作。

注册后即可[使用 JEA](using-jea.md) 了。 可随时删除会话配置文件。 注册终结点后不再使用该配置文件。

## <a name="multi-machine-configuration-with-dsc"></a>使用 DSC 的多台计算机配置

在多台计算机上部署 JEA 时，最简单的部署模型使用 JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) 资源，在每台计算机上快速且一致地部署 JEA。

要使用 DSC 部署 JEA，请确保满足以下先决条件：

- 已创作一个或多个角色功能并已将其添加到 PowerShell 模块。
- 包含角色的 PowerShell 模块存储在每台计算机可访问的（只读）文件共享中。
- 已确定会话配置设置。 使用 JEA DSC 资源时，无需创建会话配置文件。
- 已获得允许在每台计算机上执行管理操作的凭据，或有权访问用于管理计算机的 DSC 拉取服务器。
- 已下载 [JEA DSC 资源](https://github.com/powershell/JEA/tree/master/DSC%20Resource)。

在目标计算机或拉取服务器上创建 JEA 终结点的 DSC 配置。 在此配置中，JustEnoughAdministration DSC 资源定义会话配置文件，文件资源从文件共享复制角色功能。

下列属性可使用 DSC 资源进行配置：

- 角色定义
- 虚拟帐户组
- 组托管服务帐户名称
- 脚本目录
- 用户驱动器
- 条件访问规则
- JEA 会话的启动脚本

DSC 配置中的每个属性的语法都与 PowerShell 会话配置文件一致。

以下示例是常规服务器维护模块的 DSC 配置。 它假定包含角色功能的有效 PowerShell 模块位于 `\\myfileshare\JEA` 文件共享中。

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

接下来，可在系统上直接调用[本地配置管理器](/powershell/scripting/dsc/managing-nodes/metaConfig)或更新[拉取服务器配置](/powershell/scripting/dsc/pull-server/pullServer)来应用此配置。

通过 DSC 资源，还可替换默认的 Microsoft.PowerShell 终结点。 替换时，资源会自动注册一个名为 Microsoft.PowerShell.Restricted 的备份终结点。 备份终结点具有默认 WinRM ACL，允许远程管理用户和本地管理员组成员对其进行访问。

## <a name="unregistering-jea-configurations"></a>注销 JEA 配置

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet 删除 JEA 终结点。 注销 JEA 终结点将阻止新用户在系统上创建新的 JEA 会话。 它还可以使用相同的终结点名称来重新注册更新后的会话配置文件，从而更新 JEA 配置。

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> 注销 JEA 终结点将导致 WinRM 服务重启。 这将中断正在进行的大多数远程管理操作，包括其他 PowerShell 会话、WMI 调用和某些管理工具。 请仅在计划的维护时段注销 PowerShell 终结点。

## <a name="next-steps"></a>后续步骤

[测试 JEA 终结点](using-jea.md)
