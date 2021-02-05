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
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="c59a7-104">在 PowerShell 远程处理中形成第二个跃点</span><span class="sxs-lookup"><span data-stu-id="c59a7-104">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="c59a7-105">“第二个跃点问题”是指如下所示的情况：</span><span class="sxs-lookup"><span data-stu-id="c59a7-105">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="c59a7-106">已登录到 _ServerA_。</span><span class="sxs-lookup"><span data-stu-id="c59a7-106">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="c59a7-107">在 _ServerA_ 中，启动远程 PowerShell 会话，以连接到 _ServerB_。</span><span class="sxs-lookup"><span data-stu-id="c59a7-107">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="c59a7-108">通过 PowerShell 远程处理会话在 _ServerB_ 上运行的命令尝试访问 _ServerC_ 上的资源。</span><span class="sxs-lookup"><span data-stu-id="c59a7-108">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="c59a7-109">已拒绝访问 _ServerC_ 上的资源，因为用于创建 PowerShell 远程处理会话的凭据未从 _ServerB_ 传递到 _ServerC_。</span><span class="sxs-lookup"><span data-stu-id="c59a7-109">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="c59a7-110">有几种方法可以解决此问题：</span><span class="sxs-lookup"><span data-stu-id="c59a7-110">There are several ways to address this problem.</span></span> <span data-ttu-id="c59a7-111">下表按优先级列出了方法。</span><span class="sxs-lookup"><span data-stu-id="c59a7-111">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="c59a7-112">配置</span><span class="sxs-lookup"><span data-stu-id="c59a7-112">Configuration</span></span>                       |                                  <span data-ttu-id="c59a7-113">注意</span><span class="sxs-lookup"><span data-stu-id="c59a7-113">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="c59a7-114">CredSSP</span><span class="sxs-lookup"><span data-stu-id="c59a7-114">CredSSP</span></span>                                                  | <span data-ttu-id="c59a7-115">在易用性和安全性之间达到平衡</span><span class="sxs-lookup"><span data-stu-id="c59a7-115">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="c59a7-116">基于资源的 Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="c59a7-116">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="c59a7-117">增强安全性并简化配置</span><span class="sxs-lookup"><span data-stu-id="c59a7-117">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="c59a7-118">Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="c59a7-118">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="c59a7-119">高安全性，但需要域管理员</span><span class="sxs-lookup"><span data-stu-id="c59a7-119">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="c59a7-120">Kerberos 委派（非约束）</span><span class="sxs-lookup"><span data-stu-id="c59a7-120">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="c59a7-121">不推荐</span><span class="sxs-lookup"><span data-stu-id="c59a7-121">Not recommended</span></span>                                                        |
| <span data-ttu-id="c59a7-122">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="c59a7-122">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="c59a7-123">可提供最佳安全性，但需要更详细的配置</span><span class="sxs-lookup"><span data-stu-id="c59a7-123">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="c59a7-124">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c59a7-124">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="c59a7-125">配置更简单，但需要管理凭据</span><span class="sxs-lookup"><span data-stu-id="c59a7-125">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="c59a7-126">在 `Invoke-Command` 脚本块内传递凭据</span><span class="sxs-lookup"><span data-stu-id="c59a7-126">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="c59a7-127">最易操作，但必须提供凭据</span><span class="sxs-lookup"><span data-stu-id="c59a7-127">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="c59a7-128">CredSSP</span><span class="sxs-lookup"><span data-stu-id="c59a7-128">CredSSP</span></span>

<span data-ttu-id="c59a7-129">可以使用[凭据安全支持提供程序(CredSSP)][credssp] 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c59a7-129">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="c59a7-130">CredSSP 会将凭据缓存在远程服务器 (_ServerB_) 上，因此使用它会给你带来凭据被盗攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="c59a7-130">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="c59a7-131">如果远程计算机被攻破，攻击者将有权访问用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-131">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="c59a7-132">默认情况下，CredSSP 在客户端和服务器计算机上都处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="c59a7-132">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="c59a7-133">应该仅在最受信任的环境中启用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="c59a7-133">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="c59a7-134">例如，连接到域控制器的域管理员，因为域控制器是高度可信任的。</span><span class="sxs-lookup"><span data-stu-id="c59a7-134">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="c59a7-135">若要详细了解在使用 CredSSP 进行 PowerShell 远程处理时需要注意的安全问题，请参阅[非蓄意破坏：当心 CredSSP][beware]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-135">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="c59a7-136">有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗][pth]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-136">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="c59a7-137">有关如何启用和使用 CredSSP 进行 PowerShell 远程处理的示例，请参阅[使用 CredSSP 启用 PowerShell“第二个跃点”功能][credssp-psblog]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-137">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="c59a7-138">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-138">**Pros**</span></span>

- <span data-ttu-id="c59a7-139">它适用于运行 Windows Server 2008 或更高版本的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="c59a7-139">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="c59a7-140">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-140">**Cons**</span></span>

- <span data-ttu-id="c59a7-141">可能会造成安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="c59a7-141">Has security vulnerabilities.</span></span>
- <span data-ttu-id="c59a7-142">需要客户端和服务器角色的配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-142">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="c59a7-143">不适用于受保护的用户组。</span><span class="sxs-lookup"><span data-stu-id="c59a7-143">Does not work with the Protected Users group.</span></span> <span data-ttu-id="c59a7-144">有关详细信息，请参阅[受保护的用户安全组][protected-users]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-144">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="c59a7-145">Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="c59a7-145">Kerberos constrained delegation</span></span>

<span data-ttu-id="c59a7-146">可以使用旧的约束委派（而非基于资源的委派）形成第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="c59a7-146">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="c59a7-147">“使用任何身份验证协议”选项配置 Kerberos 约束委派以允许协议转换。</span><span class="sxs-lookup"><span data-stu-id="c59a7-147">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="c59a7-148">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-148">**Pros**</span></span>

- <span data-ttu-id="c59a7-149">无需特殊编码</span><span class="sxs-lookup"><span data-stu-id="c59a7-149">Requires no special coding</span></span>
- <span data-ttu-id="c59a7-150">不存储凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-150">Credentials are not stored.</span></span>

<span data-ttu-id="c59a7-151">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-151">**Cons**</span></span>

- <span data-ttu-id="c59a7-152">不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="c59a7-152">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="c59a7-153">需要域管理员访问权限才能配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-153">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="c59a7-154">必须对远程服务器 (ServerB) 的 Active Directory 对象进行配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-154">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="c59a7-155">限于一个域。</span><span class="sxs-lookup"><span data-stu-id="c59a7-155">Limited to one domain.</span></span> <span data-ttu-id="c59a7-156">不能跨域或林。</span><span class="sxs-lookup"><span data-stu-id="c59a7-156">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="c59a7-157">需要权限才能更新对象和服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="c59a7-157">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="c59a7-158">ServerB 可代表用户获取针对 ServerC 的 Kerberos 票证，而不需用户干预 。</span><span class="sxs-lookup"><span data-stu-id="c59a7-158">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="c59a7-159">无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户。</span><span class="sxs-lookup"><span data-stu-id="c59a7-159">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="c59a7-160">有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”][blog]和 [Kerberos 身份验证工具和设置][ktools]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-160">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="c59a7-161">基于资源的 Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="c59a7-161">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="c59a7-162">通过使用（Windows Server 2012 中引入的）基于资源的 Kerberos 约束委派，在资源驻留的服务器对象上配置凭据委派。</span><span class="sxs-lookup"><span data-stu-id="c59a7-162">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="c59a7-163">在上述第二个跃点场景中，配置 ServerC 以指定从何处接受委派凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-163">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="c59a7-164">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-164">**Pros**</span></span>

- <span data-ttu-id="c59a7-165">不存储凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-165">Credentials are not stored.</span></span>
- <span data-ttu-id="c59a7-166">已使用 PowerShell cmdlet 进行配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-166">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="c59a7-167">无需特殊编码。</span><span class="sxs-lookup"><span data-stu-id="c59a7-167">No special coding required.</span></span>
- <span data-ttu-id="c59a7-168">无需域管理员访问权限就能配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-168">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="c59a7-169">可跨域和林使用。</span><span class="sxs-lookup"><span data-stu-id="c59a7-169">Works across domains and forests.</span></span>

<span data-ttu-id="c59a7-170">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-170">**Cons**</span></span>

- <span data-ttu-id="c59a7-171">要求 Windows Server 2012 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="c59a7-171">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="c59a7-172">不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="c59a7-172">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="c59a7-173">需要权限才能更新对象和服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="c59a7-173">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="c59a7-174">无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户。</span><span class="sxs-lookup"><span data-stu-id="c59a7-174">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="c59a7-175">有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”][blog]和 [Kerberos 身份验证工具和设置][ktools]。</span><span class="sxs-lookup"><span data-stu-id="c59a7-175">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="c59a7-176">示例</span><span class="sxs-lookup"><span data-stu-id="c59a7-176">Example</span></span>

<span data-ttu-id="c59a7-177">让我们看看 PowerShell 示例，它在 ServerC 上配置基于资源的约束委派，以允许来自 ServerB 的委派凭据 。</span><span class="sxs-lookup"><span data-stu-id="c59a7-177">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="c59a7-178">此示例假定所有服务器都运行 Windows Server 2012 或更高版本，并且任一服务器所属的每个域具有至少一个 Windows Server 2012 域控制器。</span><span class="sxs-lookup"><span data-stu-id="c59a7-178">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="c59a7-179">在配置约束委派前，必须先添加 `RSAT-AD-PowerShell` 功能以安装 Active Directory PowerShell 模块，然后将该模块导入会话：</span><span class="sxs-lookup"><span data-stu-id="c59a7-179">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="c59a7-180">现在多个可用的 cmdlet 具有 **PrincipalsAllowedToDelegateToAccount** 参数：</span><span class="sxs-lookup"><span data-stu-id="c59a7-180">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="c59a7-181">PrincipalsAllowedToDelegateToAccount 参数可设置 Active Directory 对象属性 msDS-AllowedToActOnBehalfOfOtherIdentity，其中包含一份访问控制列表 (ACL)，指定了哪些帐户有权向关联帐户委派凭据（在本示例中，该帐户为 ServerA 的计算机帐户） 。</span><span class="sxs-lookup"><span data-stu-id="c59a7-181">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_).</span></span>

<span data-ttu-id="c59a7-182">现在，我们来设置用于表示服务器的变量：</span><span class="sxs-lookup"><span data-stu-id="c59a7-182">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="c59a7-183">默认情况下，WinRM（由此还有 PowerShell 远程处理）作为计算机帐户运行。</span><span class="sxs-lookup"><span data-stu-id="c59a7-183">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="c59a7-184">可通过查看 `winrm` 服务的 **StartName** 属性看到：</span><span class="sxs-lookup"><span data-stu-id="c59a7-184">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="c59a7-185">为使 ServerC 允许来自 ServerB 上的 PowerShell 远程处理会话的委派，我们必须将 ServerC 上的 PrincipalsAllowedToDelegateToAccount 参数设置为 ServerB 的计算机对象  ：</span><span class="sxs-lookup"><span data-stu-id="c59a7-185">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="c59a7-186">Kerberos [密钥分发中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 将拒绝访问尝试（负缓存）缓存保留 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="c59a7-186">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="c59a7-187">如果 _ServerB_ 先前已尝试访问 _ServerC_，则需要通过调用以下命令清除 _ServerB_ 上的缓存：</span><span class="sxs-lookup"><span data-stu-id="c59a7-187">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="c59a7-188">还可以重启计算机，或等待至少 15 分钟，以清除缓存。</span><span class="sxs-lookup"><span data-stu-id="c59a7-188">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="c59a7-189">清除缓存之后，可以通过 _ServerB_ 到 _ServerC_ 成功运行来自 _ServerA_ 的代码：</span><span class="sxs-lookup"><span data-stu-id="c59a7-189">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="c59a7-190">在本示例中，`$using` 变量用于使 `$ServerC` 变量对 _ServerB_ 可见。</span><span class="sxs-lookup"><span data-stu-id="c59a7-190">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="c59a7-191">有关 `$using` 变量的详细信息，请参阅 [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables)。</span><span class="sxs-lookup"><span data-stu-id="c59a7-191">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="c59a7-192">若要允许多个服务器向 _ServerC_ 委派凭据，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为数组：</span><span class="sxs-lookup"><span data-stu-id="c59a7-192">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="c59a7-193">如果想要跨域形成第二个跃点，添加 _ServerB_ 所属域的域控制器的完全限定域名 (FQDN)：</span><span class="sxs-lookup"><span data-stu-id="c59a7-193">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="c59a7-194">若要删除向 ServerC 委派凭据的功能，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为 `$null`：</span><span class="sxs-lookup"><span data-stu-id="c59a7-194">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="c59a7-195">基于资源的 Kerberos 约束委派的相关信息</span><span class="sxs-lookup"><span data-stu-id="c59a7-195">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="c59a7-196">[Kerberos 身份验证的中的新功能][whats-new]</span><span class="sxs-lookup"><span data-stu-id="c59a7-196">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="c59a7-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 1 部分）</span><span class="sxs-lookup"><span data-stu-id="c59a7-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="c59a7-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 2 部分）</span><span class="sxs-lookup"><span data-stu-id="c59a7-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="c59a7-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]（了解 Kerberos 约束委派，以使用集成的 Windows 身份验证进行 Azure Active Directory 应用程序代理部署）</span><span class="sxs-lookup"><span data-stu-id="c59a7-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="c59a7-200">[[MS-ADA2] Active Directory 架构属性 M2.210 属性 msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="c59a7-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="c59a7-201">[[MS-SFU] Kerberos 协议扩展：用户服务和约束委派协议 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="c59a7-201">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="c59a7-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]（在不使用约束委派的情况下，使用 PrincipalsAllowedToDelegateToAccount 进行远程管理）</span><span class="sxs-lookup"><span data-stu-id="c59a7-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="c59a7-203">Kerberos 委派（非约束）</span><span class="sxs-lookup"><span data-stu-id="c59a7-203">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="c59a7-204">还可以使用 Kerberos 非约束委派来形成第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="c59a7-204">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="c59a7-205">与所有 Kerberos 方案一样，不会存储凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-205">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="c59a7-206">此方法不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="c59a7-206">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="c59a7-207">此方法无法控制使用委派凭据的位置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-207">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="c59a7-208">它的安全性比 CredSSP 低。</span><span class="sxs-lookup"><span data-stu-id="c59a7-208">It is less secure than CredSSP.</span></span> <span data-ttu-id="c59a7-209">此方法应仅用于测试方案。</span><span class="sxs-lookup"><span data-stu-id="c59a7-209">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="c59a7-210">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="c59a7-210">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="c59a7-211">JEA 允许限制管理员在 PowerShell 会话期间可以运行的命令。</span><span class="sxs-lookup"><span data-stu-id="c59a7-211">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="c59a7-212">它可用于解决第二个跃点问题。</span><span class="sxs-lookup"><span data-stu-id="c59a7-212">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="c59a7-213">有关 JEA 的信息，请参阅 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。</span><span class="sxs-lookup"><span data-stu-id="c59a7-213">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="c59a7-214">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-214">**Pros**</span></span>

- <span data-ttu-id="c59a7-215">使用虚拟帐户时无需密码维护。</span><span class="sxs-lookup"><span data-stu-id="c59a7-215">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="c59a7-216">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-216">**Cons**</span></span>

- <span data-ttu-id="c59a7-217">需要 WMF 5.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="c59a7-217">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="c59a7-218">需要在每个中间服务器 (_ServerB_) 上进行配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-218">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="c59a7-219">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c59a7-219">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="c59a7-220">可以在 _ServerB_ 上创建会话配置并设置其 **RunAsCredential** 参数。</span><span class="sxs-lookup"><span data-stu-id="c59a7-220">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="c59a7-221">要了解如何结合使用 PSSessionConfiguration 和 RunAs 来解决第二个跃点问题，请参阅[多跃点 PowerShell 远程处理的另一种解决方案][pssessionconfig] 。</span><span class="sxs-lookup"><span data-stu-id="c59a7-221">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="c59a7-222">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-222">**Pros**</span></span>

- <span data-ttu-id="c59a7-223">兼容任何运行 WMF 3.0 或更高版本的服务器。</span><span class="sxs-lookup"><span data-stu-id="c59a7-223">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="c59a7-224">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-224">**Cons**</span></span>

- <span data-ttu-id="c59a7-225">需要在每个中间服务器 (_ServerB_) 上配置 **PSSessionConfiguration** 和 **RunAs**。</span><span class="sxs-lookup"><span data-stu-id="c59a7-225">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="c59a7-226">使用域 **RunAs** 帐户时要求密码维护</span><span class="sxs-lookup"><span data-stu-id="c59a7-226">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="c59a7-227">在 Invoke-Command 脚本块内传递凭据</span><span class="sxs-lookup"><span data-stu-id="c59a7-227">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="c59a7-228">可以在对 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet 的调用的 **ScriptBlock** 参数内传递凭据。</span><span class="sxs-lookup"><span data-stu-id="c59a7-228">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="c59a7-229">**优点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-229">**Pros**</span></span>

- <span data-ttu-id="c59a7-230">无需特殊服务器配置。</span><span class="sxs-lookup"><span data-stu-id="c59a7-230">Does not require special server configuration.</span></span>
- <span data-ttu-id="c59a7-231">适用于任何运行 WMF 2.0 或更高版本的服务器。</span><span class="sxs-lookup"><span data-stu-id="c59a7-231">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="c59a7-232">**缺点**</span><span class="sxs-lookup"><span data-stu-id="c59a7-232">**Cons**</span></span>

- <span data-ttu-id="c59a7-233">需要繁琐的代码技术。</span><span class="sxs-lookup"><span data-stu-id="c59a7-233">Requires an awkward code technique.</span></span>
- <span data-ttu-id="c59a7-234">运行 WMF 2.0 时，需要不同的语法将参数传递到远程会话。</span><span class="sxs-lookup"><span data-stu-id="c59a7-234">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="c59a7-235">示例</span><span class="sxs-lookup"><span data-stu-id="c59a7-235">Example</span></span>

<span data-ttu-id="c59a7-236">以下示例演示了如何在 **Invoke-command** 脚本块中传递凭据：</span><span class="sxs-lookup"><span data-stu-id="c59a7-236">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="c59a7-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c59a7-237">See also</span></span>

[<span data-ttu-id="c59a7-238">PowerShell 远程处理安全注意事项</span><span class="sxs-lookup"><span data-stu-id="c59a7-238">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

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
