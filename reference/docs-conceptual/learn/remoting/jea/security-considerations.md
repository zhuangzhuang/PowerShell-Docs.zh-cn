---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 安全注意事项
description: 由于 JEA 允许这些用户在没有拥有完整管理员权限的情况下运行管理员命令，因此你可从高特权安全组中删除这些用户。
ms.openlocfilehash: f65f9d6c6620261de0a9c8de7812637565ca1806
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501569"
---
# <a name="jea-security-considerations"></a>JEA 安全注意事项

JEA 通过减少计算机上的永久管理员数量来帮助改善安全状况。 JEA 使用 PowerShell 会话配置来创建用户管理系统的新入口点。 如果用户需要提升（但受限）的计算机访问权限来执行管理任务，则可向他们授予访问 JEA 终结点的权限。 由于 JEA 允许这些用户在没有拥有完整管理员权限的情况下运行管理员命令，因此你可从高特权安全组中删除这些用户。

## <a name="run-as-account"></a>运行身份帐户

每个 JEA 终结点都具有指定的运行身份帐户。 这是执行连接用户的操作时使用的帐户。 此帐户在[会话配置文件](session-configurations.md)中是可配置的，并且你选择的帐户对终结点的安全性意义重大。

建议使用虚拟帐户来配置运行身份帐户。 虚拟帐户是临时创建的一次性本地帐户，便于连接用户在 JEA 会话期间使用。 一旦用户的会话终止，虚拟帐户即废弃且不得再次使用。 连接用户不知道虚拟帐户的凭据。 虚拟帐户不能用于通过远程桌面或不受约束的 PowerShell 终结点等其他方式访问系统。

默认情况下，虚拟帐户属于计算机上的本地管理员组。 这将授予他们管理系统中所有内容的全部权限，但这些帐户无权管理网络中的资源。
在向其他计算机进行身份验证时，用户上下文针对本地计算机帐户，而非虚拟帐户。

域控制器是一种特殊情况，因为不存在本地管理员组。 然而，虚拟帐户属于域管理员，可管理域控制器上的目录服务。 域标识在实例化 JEA 会话的域控制器上的使用仍然受限。 任何网络访问似乎都来自域控制器计算机对象。

在这两种情况下，可显式定义虚拟帐户应属于哪些安全组。 无需本地或域管理员权限即可完成任务时，这是一个很合适的做法。 如果已为管理员定义了安全组，则向该组授予虚拟帐户成员资格。 虚拟帐户组成员资格仅限于工作站和成员服务器上的本地安全组。 在域控制器上，虚拟帐户必须是域安全组的成员。
将虚拟帐户添加到一个或多个安全组后，该帐户将不再属于默认组（本地或域管理员）。

下表总结了虚拟帐户可能的配置选项和所得到的权限：

|        计算机类型         | 虚拟帐户组配置 |                   本地用户上下文                    | 网络用户上下文 |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| 域控制器            | 默认                             | 域用户，“*DOMAIN*\Domain Admins”的成员         | 计算机帐户     |
| 域控制器            | 域组 A 和域组 B               | 域用户，“*DOMAIN*\A”、“*DOMAIN*\B”的成员       | 计算机帐户     |
| 成员服务器或工作站 | 默认                             | 本地用户、“*BUILTIN*\Administrators”的成员        | 计算机帐户     |
| 成员服务器或工作站 | 本地组 C 和 D                | 本地用户、“*COMPUTER*\C”和“*COMPUTER*\D”的成员 | 计算机帐户     |

查看安全审核事件和应用程序事件日志时，可发现每个 JEA 用户会话都有唯一的虚拟帐户。 此唯一帐户有助于将 JEA 终结点中的用户操作追溯回运行该命令的原始用户。 虚拟帐户名称遵循 `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` 格式。例如，域 Contoso 中的用户 Alice 在 JEA 终结点中重启服务时，与任何服务控制管理器事件关联的用户名将为 `WinRM Virtual Users\WinRM_VA_1_contoso_alice`。

当成员服务器需要对 JEA 会话中的网络资源具有访问权限时，组托管服务帐户 (gMSA) 十分有用。 例如，JEA 终结点用于控制对其他计算机上托管的 REST API 服务的访问时。 可轻松编写函数来调用 REST API，但需要使用网络标识对 API 进行身份验证。 使用组托管服务帐户可实现第二个跃点，同时持续控制哪些计算机可使用此帐户。 gMSA 帐户所属的安全组（本地或域）定义 gMSA 的有效权限。

JEA 终结点配置为使用 gMSA 时，所有 JEA 用户的操作似乎来自同一个 gMSA。 要将操作追溯回特定用户，唯一方法是确定在 PowerShell 会话脚本中运行的命令集。

未指定运行身份帐户时使用传递凭据。 PowerShell 使用连接用户的凭据在远程服务器上运行命令。 这需要你向连接用户授予对特权管理组的直接访问权限。 对于 JEA，不推荐此配置。 如果连接用户已有管理员权限，则无需使用 JEA，并可通过其他不受约束的方式管理系统。 有关详细信息，请参阅下一部分来了解如何使 [JEA 不阻止管理员](#jea-doesnt-protect-against-admins)。

通过标准运行身份帐户，可指定运行整个 PowerShell 会话所采用的用户帐户。 JEA 不支持使用固定运行身份帐户（具有 `-RunAsCredential` 参数）的’会话配置。 角色定义不再按预期方式运行。 有权访问该终结点的每位用户都分配到同一角色。

由于很难将操作追溯回特定用户并且缺少将用户映射到角色的支持，因此不得对 JEA 终结点使用 RunAsCredential。

## <a name="winrm-endpoint-acl"></a>WinRM 终结点 ACL

与常规 PowerShell 远程处理终结点一样，每个 JEA 终结点都有单独的访问控制列表 (ACL)，它用于控制哪些用户可通过 JEA 终结点进行身份验证。 如果配置错误，受信任的用户可能无法访问 JEA 终结点，而不受信任的用户可能获得访问权限。 WinRM ACL 不影响用户到 JEA 角色的映射。 映射由用于注册终结点的会话配置文件中的“RoleDefinitions”字段控制。

默认情况下，当 JEA 终结点具有多个角色功能时，WinRM ACL 配置为允许访问所有映射的用户。 例如，使用以下命令配置的 JEA 会话授予对 `CONTOSO\JEA_Lev1` 和 `CONTOSO\JEA_Lev2` 的完全访问权限。

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

可以使用 [Get-pssessionconfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 审核用户权限。

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

若要更改哪些用户具有访问权限，请运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 进行交互式提示或运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 来更新权限。 用户至少需要调用权限才能访问 JEA 终结点。

可创建未将已定义角色映射到有权访问的每个用户的 JEA 终结点。 这些用户可发起 JEA 会话，但仅有权访问默认 cmdlet。 可以通过运行 `Get-PSSessionCapability` 来审核 JEA 终结点中的用户权限。 有关详细信息，请参阅 [JEA 审核和报告](audit-and-report.md)。

## <a name="least-privilege-roles"></a>最小特权角色

设计 JEA 角色时，请务必记住后台运行的虚拟帐户或组托管服务帐户可不受限制地访问本地计算机。 JEA 角色功能有助于限制可在该特权上下文中运行的命令和应用程序。
设计不当的角色可允许运行危险命令，该命令可能允许用户冲破 JEA 边界或获得对敏感信息的访问权限。

例如，考虑以下角色功能事项：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

通过此角色功能，用户可从 Microsoft.PowerShell.Management 模块使用 Process 名词运行任何 PowerShell cmdlet 。 用户可能需要访问一些 cmdlet，例如访问 `Get-Process` 来了解系统上正在运行哪些应用程序，以及访问 `Stop-Process` 来终止未响应的应用程序。 但是，此项还允许访问 `Start-Process`，以用于启动具有完全管理员权限的任意程序。 该程序不需要在系统上进行本地安装。 已连接的用户可从文件共享启动程序，这向用户提供本地管理员权限，还会运行恶意软件等等。

此相同角色功能的更安全版本如下所示：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

不要在角色功能中使用通配符。 请务必定期[审计有效用户权限](audit-and-report.md#check-effective-rights-for-a-specific-user)，了解用户可访问哪些命令。

## <a name="jea-doesnt-protect-against-admins"></a>JEA 不阻止管理员

JEA 的核心原则之一是允许非管理员执行某些管理员任务。 JEA 不阻止已具有管理员特权的用户。 属于域管理员、本地管理员或其他高权限组的用户可通过其他方式规避 JEA 的保护。 例如，他们可使用 RDP 进行登录、使用远程 MMC 控制台，或连接到不受约束的 PowerShell 终结点。 此外，系统上的本地管理员还可修改 JEA 配置以允许其他用户，或者更改角色功能，以扩大其 JEA 会话中用户可执行的操作范围。 请务必评估 JEA 用户的延伸权限，了解他们是否可通过其他方式获得对系统的特许访问权限。

一种常见做法是使用 JEA 进行常规的日常维护，并且获得实时特许访问管理解决方案，使用户在紧急情况下能够临时成为本地管理员。 这有助于确保用户不会成为系统的永久管理员，只有当且仅当他们完成记录这些权限使用情况的工作流时，才能获得这些权限。
