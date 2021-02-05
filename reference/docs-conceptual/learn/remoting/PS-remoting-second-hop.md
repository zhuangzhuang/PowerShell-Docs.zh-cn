---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: 在 PowerShell 远程处理中形成第二个跃点
description: 本文介绍为 PowerShell 远程处理配置第二跃点身份验证的各种方法，包括安全隐患和建议。
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501365"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>在 PowerShell 远程处理中形成第二个跃点

“第二个跃点问题”是指如下所示的情况：

1. 已登录到 _ServerA_。
2. 在 _ServerA_ 中，启动远程 PowerShell 会话，以连接到 _ServerB_。
3. 通过 PowerShell 远程处理会话在 _ServerB_ 上运行的命令尝试访问 _ServerC_ 上的资源。
4. 已拒绝访问 _ServerC_ 上的资源，因为用于创建 PowerShell 远程处理会话的凭据未从 _ServerB_ 传递到 _ServerC_。

有几种方法可以解决此问题： 下表按优先级列出了方法。

|                      配置                       |                                  注意                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| CredSSP                                                  | 在易用性和安全性之间达到平衡                                      |
| 基于资源的 Kerberos 约束委派           | 增强安全性并简化配置                             |
| Kerberos 约束委派                          | 高安全性，但需要域管理员                         |
| Kerberos 委派（非约束）                      | 不推荐                                                        |
| Just Enough Administration (JEA)                         | 可提供最佳安全性，但需要更详细的配置 |
| 使用 RunAs 的 PSSessionConfiguration                       | 配置更简单，但需要管理凭据                |
| 在 `Invoke-Command` 脚本块内传递凭据 | 最易操作，但必须提供凭据                       |

## <a name="credssp"></a>CredSSP

可以使用[凭据安全支持提供程序(CredSSP)][credssp] 进行身份验证。
CredSSP 会将凭据缓存在远程服务器 (_ServerB_) 上，因此使用它会给你带来凭据被盗攻击的风险。 如果远程计算机被攻破，攻击者将有权访问用户的凭据。 默认情况下，CredSSP 在客户端和服务器计算机上都处于禁用状态。 应该仅在最受信任的环境中启用 CredSSP。 例如，连接到域控制器的域管理员，因为域控制器是高度可信任的。

若要详细了解在使用 CredSSP 进行 PowerShell 远程处理时需要注意的安全问题，请参阅[非蓄意破坏：当心 CredSSP][beware]。

有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗][pth]。

有关如何启用和使用 CredSSP 进行 PowerShell 远程处理的示例，请参阅[使用 CredSSP 启用 PowerShell“第二个跃点”功能][credssp-psblog]。

**优点**

- 它适用于运行 Windows Server 2008 或更高版本的所有服务器。

**缺点**

- 可能会造成安全漏洞。
- 需要客户端和服务器角色的配置。
- 不适用于受保护的用户组。 有关详细信息，请参阅[受保护的用户安全组][protected-users]。

## <a name="kerberos-constrained-delegation"></a>Kerberos 约束委派

可以使用旧的约束委派（而非基于资源的委派）形成第二个跃点。 “使用任何身份验证协议”选项配置 Kerberos 约束委派以允许协议转换。

**优点**

- 无需特殊编码
- 不存储凭据。

**缺点**

- 不支持 WinRM 的第二个跃点。
- 需要域管理员访问权限才能配置。
- 必须对远程服务器 (ServerB) 的 Active Directory 对象进行配置。
- 限于一个域。 不能跨域或林。
- 需要权限才能更新对象和服务主体名称 (SPN)。
- ServerB 可代表用户获取针对 ServerC 的 Kerberos 票证，而不需用户干预 。

> [!NOTE]
> 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户。 有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”][blog]和 [Kerberos 身份验证工具和设置][ktools]。

## <a name="resource-based-kerberos-constrained-delegation"></a>基于资源的 Kerberos 约束委派

通过使用（Windows Server 2012 中引入的）基于资源的 Kerberos 约束委派，在资源驻留的服务器对象上配置凭据委派。 在上述第二个跃点场景中，配置 ServerC 以指定从何处接受委派凭据。

**优点**

- 不存储凭据。
- 已使用 PowerShell cmdlet 进行配置。 无需特殊编码。
- 无需域管理员访问权限就能配置。
- 可跨域和林使用。

**缺点**

- 要求 Windows Server 2012 或更高版本。
- 不支持 WinRM 的第二个跃点。
- 需要权限才能更新对象和服务主体名称 (SPN)。

> [!NOTE]
> 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户。 有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”][blog]和 [Kerberos 身份验证工具和设置][ktools]。

### <a name="example"></a>示例

让我们看看 PowerShell 示例，它在 ServerC 上配置基于资源的约束委派，以允许来自 ServerB 的委派凭据 。 此示例假定所有服务器都运行 Windows Server 2012 或更高版本，并且任一服务器所属的每个域具有至少一个 Windows Server 2012 域控制器。

在配置约束委派前，必须先添加 `RSAT-AD-PowerShell` 功能以安装 Active Directory PowerShell 模块，然后将该模块导入会话：

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

现在多个可用的 cmdlet 具有 **PrincipalsAllowedToDelegateToAccount** 参数：

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

PrincipalsAllowedToDelegateToAccount 参数可设置 Active Directory 对象属性 msDS-AllowedToActOnBehalfOfOtherIdentity，其中包含一份访问控制列表 (ACL)，指定了哪些帐户有权向关联帐户委派凭据（在本示例中，该帐户为 ServerA 的计算机帐户） 。

现在，我们来设置用于表示服务器的变量：

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

默认情况下，WinRM（由此还有 PowerShell 远程处理）作为计算机帐户运行。 可通过查看 `winrm` 服务的 **StartName** 属性看到：

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

为使 ServerC 允许来自 ServerB 上的 PowerShell 远程处理会话的委派，我们必须将 ServerC 上的 PrincipalsAllowedToDelegateToAccount 参数设置为 ServerB 的计算机对象  ：

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [密钥分发中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 将拒绝访问尝试（负缓存）缓存保留 15 分钟。 如果 _ServerB_ 先前已尝试访问 _ServerC_，则需要通过调用以下命令清除 _ServerB_ 上的缓存：

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

还可以重启计算机，或等待至少 15 分钟，以清除缓存。

清除缓存之后，可以通过 _ServerB_ 到 _ServerC_ 成功运行来自 _ServerA_ 的代码：

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

在本示例中，`$using` 变量用于使 `$ServerC` 变量对 _ServerB_ 可见。
有关 `$using` 变量的详细信息，请参阅 [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables)。

若要允许多个服务器向 _ServerC_ 委派凭据，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为数组：

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

如果想要跨域形成第二个跃点，添加 _ServerB_ 所属域的域控制器的完全限定域名 (FQDN)：

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

若要删除向 ServerC 委派凭据的功能，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为 `$null`：

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>基于资源的 Kerberos 约束委派的相关信息

- [Kerberos 身份验证的中的新功能][whats-new]
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 1 部分）
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 2 部分）
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]（了解 Kerberos 约束委派，以使用集成的 Windows 身份验证进行 Azure Active Directory 应用程序代理部署）
- [[MS-ADA2] Active Directory 架构属性 M2.210 属性 msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]
- [[MS-SFU] Kerberos 协议扩展：用户服务和约束委派协议 1.3.2 S4U2proxy][MS-SFU]
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]（在不使用约束委派的情况下，使用 PrincipalsAllowedToDelegateToAccount 进行远程管理）

## <a name="kerberos-delegation-unconstrained"></a>Kerberos 委派（非约束）

还可以使用 Kerberos 非约束委派来形成第二个跃点。 与所有 Kerberos 方案一样，不会存储凭据。 此方法不支持 WinRM 的第二个跃点。

> [!WARNING]
> 此方法无法控制使用委派凭据的位置。 它的安全性比 CredSSP 低。 此方法应仅用于测试方案。

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA 允许限制管理员在 PowerShell 会话期间可以运行的命令。 它可用于解决第二个跃点问题。

有关 JEA 的信息，请参阅 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。

**优点**

- 使用虚拟帐户时无需密码维护。

**缺点**

- 需要 WMF 5.0 或更高版本。
- 需要在每个中间服务器 (_ServerB_) 上进行配置。

## <a name="pssessionconfiguration-using-runas"></a>使用 RunAs 的 PSSessionConfiguration

可以在 _ServerB_ 上创建会话配置并设置其 **RunAsCredential** 参数。

要了解如何结合使用 PSSessionConfiguration 和 RunAs 来解决第二个跃点问题，请参阅[多跃点 PowerShell 远程处理的另一种解决方案][pssessionconfig] 。

**优点**

- 兼容任何运行 WMF 3.0 或更高版本的服务器。

**缺点**

- 需要在每个中间服务器 (_ServerB_) 上配置 **PSSessionConfiguration** 和 **RunAs**。
- 使用域 **RunAs** 帐户时要求密码维护

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>在 Invoke-Command 脚本块内传递凭据

可以在对 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet 的调用的 **ScriptBlock** 参数内传递凭据。

**优点**

- 无需特殊服务器配置。
- 适用于任何运行 WMF 2.0 或更高版本的服务器。

**缺点**

- 需要繁琐的代码技术。
- 运行 WMF 2.0 时，需要不同的语法将参数传递到远程会话。

### <a name="example"></a>示例

以下示例演示了如何在 **Invoke-command** 脚本块中传递凭据：

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>另请参阅

[PowerShell 远程处理安全注意事项](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
