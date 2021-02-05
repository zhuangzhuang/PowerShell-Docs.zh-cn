---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 审核和报告
description: 审核可帮助你评估适当的人员是否有权访问 JEA 终结点，以及向其分配的角色是否仍适用。
ms.openlocfilehash: 2140d6b756ae38d82e4943c373e8a75beea30e28
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92500005"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA 审核和报告

部署 JEA 后，需要定期审核 JEA 配置。 审核可帮助你评估适当的人员是否有权访问 JEA 终结点，以及向其分配的角色是否仍适用。

## <a name="find-registered-jea-sessions-on-a-machine"></a>查找计算机上已注册的 JEA 会话

若要查看计算机上注册了哪些 JEA 会话，可使用 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet。

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

“权限”属性中列出了终结点的有效权限。 这些用户有权连接到 JEA 终结点。 但他们有权访问的角色和命令却是由用于注册终结点的[会话配置文件](session-configurations.md)中的 RoleDefinitions 属性决定。 扩展 RoleDefinitions 属性，评估已注册的 JEA 终结点中的角色映射。

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>查找计算机上可用的角色功能

JEA 从 PowerShell 模块内“RoleCapabilities”文件夹中存储的 `.psrc` 文件获取角色功能。 下面的函数会查找计算机上提供的所有角色功能。

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> 如果多个角色功能共享同一名称，则此函数的结果顺序无需是选择角色功能的顺序。

## <a name="check-effective-rights-for-a-specific-user"></a>查看特定用户的有效权限

[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet 根据用户的组成员资格枚举 JEA 终结点上可用的所有命令。
`Get-PSSessionCapability` 的输出与 JEA 会话中运行 `Get-Command -CommandType All` 的指定用户的输出完全相同。

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

如果用户不是将向其授予其他 JEA 权限的组的永久成员，则此 cmdlet 可能不会反映这些额外权限。 使用实时特权访问管理系统让用户能够临时隶属于安全组时，会发生此情况。 请仔细评估用户到角色和功能的映射，确保用户仅获得成功完成其作业所需的访问级别。

## <a name="powershell-event-logs"></a>PowerShell 事件日志

如果在系统上启用了模块或脚本块日志记录，则针对用户在 JEA 会话中运行的每条命令，可在 Windows 事件日志中看到相应事件。 要查找这些事件，请打开“Microsoft-Windows-PowerShell/Operational”事件日志，然后查找事件 ID 为 4104 的事件。

每个事件日志项目都包括在其中运行命令的会话的相关信息。 对于 JEA 会话，该事件包含 ConnectedUser 和 RunAsUser 的相关信息。 ConnectedUser 是实际创建 JEA 会话的用户。 RunAsUser 是 JEA 用于执行该命令的帐户。

应用程序事件日志显示了 RunAsUser 所做的更改。 因此需要启用模块和脚本日志记录才能将特定的命令调用回 ConnectedUser。

## <a name="application-event-logs"></a>应用程序事件日志

与外部应用程序或服务交互的 JEA 会话中运行的命令可能会将事件记录到其自己的事件日志中。 与 PowerShell 日志和脚本不同，其他日志记录机制不会捕获 JEA 会话已连接的用户。 相反，这些应用程序只记录虚拟运行身份用户。
要确定运行该命令的用户，需要参考[会话脚本](#session-transcripts)或相关 PowerShell 事件日志（其中时间和用户显示在应用程序事件日志中）。

WinRM 日志还可帮你将运行身份用户与应用程序事件日志中的连接用户联系起来。 Microsoft-Windows-Windows Remote Management/Operational 日志中 ID 为 193 的事件记录了每个新的 JEA 会话中连接用户和运行身份用户的安全标识符 (SID) 和帐户名称。

## <a name="session-transcripts"></a>会话脚本

如果已将 JEA 配置为创建每个用户会话的脚本，则每位用户的操作文本副本将存储在指定的文件夹中。

以下命令（以管理员身份运行）可查找所有脚本目录。

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

每个脚本的开头部分都包含以下内容：会话开始时间、连接到会话的用户和分配给用户的 JEA 标识。

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

脚本的正文包含用户调用的每个命令的相关信息。 由于 PowerShell 远程处理的命令转换方式，所使用的命令的确切语法在 JEA 会话中不可用。 但是，仍可确定已执行的有效命令。 以下示例是来自 JEA 会话中运行 `Get-Service Dns` 的用户的脚本代码段：

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

CommandInvocation 行是为用户运行的每个命令编写的。 ParameterBindings 会记录随附该命令提供的每个参数和值。 在上一示例中，可看到针对 `Get-Service` cmdlet 向 Name 参数提供了值 Dns。

每个命令的输出通常还会对 `Out-Default` 触发 CommandInvocation。 `Out-Default` 的 InputObject 是从命令返回的 PowerShell 对象。 该对象的详细信息如下面几行所示，严格模拟用户将看到的内容。

## <a name="see-also"></a>另请参阅

[PowerShell ♥ the Blue Team 关于安全的博客文章](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
