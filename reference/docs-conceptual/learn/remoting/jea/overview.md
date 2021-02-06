---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: Just Enough Administration (JEA) 概述
description: JEA 是一项安全技术，通过它可以对 PowerShell 管理的任何内容进行委托管理。
ms.openlocfilehash: cc1c49960e274b58635c1ca4e6769a54c3c7ded6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501705"
---
# <a name="just-enough-administration"></a><span data-ttu-id="3e968-104">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="3e968-104">Just Enough Administration</span></span>

<span data-ttu-id="3e968-105">Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行由 PowerShell 管理的任意操作。</span><span class="sxs-lookup"><span data-stu-id="3e968-105">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything managed by PowerShell.</span></span> <span data-ttu-id="3e968-106">使用 JEA，你可以：</span><span class="sxs-lookup"><span data-stu-id="3e968-106">With JEA, you can:</span></span>

- <span data-ttu-id="3e968-107">减少计算机上的管理员数量，使用虚拟帐户或组托管服务帐户代表普通用户执行特权操作。</span><span class="sxs-lookup"><span data-stu-id="3e968-107">**Reduce the number of administrators on your machines** using virtual accounts or group-managed service accounts to perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="3e968-108">通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。</span><span class="sxs-lookup"><span data-stu-id="3e968-108">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="3e968-109">使用准确显示用户在会话中所执行命令的脚本和日志，**更好地了解你的用户进行的操作**。</span><span class="sxs-lookup"><span data-stu-id="3e968-109">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="3e968-110">**JEA 为何很重要？**</span><span class="sxs-lookup"><span data-stu-id="3e968-110">**Why is JEA important?**</span></span>

<span data-ttu-id="3e968-111">用于管理服务器的高特权帐户会造成严重的安全风险。</span><span class="sxs-lookup"><span data-stu-id="3e968-111">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span> <span data-ttu-id="3e968-112">如果攻击者破坏这些帐户其中之一，他们可在组织中启动[横向攻击](https://aka.ms/pth)。</span><span class="sxs-lookup"><span data-stu-id="3e968-112">Should an attacker compromise one of these accounts, they could launch [lateral attacks](https://aka.ms/pth) across your organization.</span></span> <span data-ttu-id="3e968-113">每个遭到入侵的帐户都会向攻击者提供访问更多帐户和资源的权限，使他们离窃取公司机密、发起拒绝服务攻击等更近一步。</span><span class="sxs-lookup"><span data-stu-id="3e968-113">Each compromised account gives an attacker access to even more accounts and resources, and puts them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="3e968-114">而且，删除管理特权有时也并不容易。</span><span class="sxs-lookup"><span data-stu-id="3e968-114">It's not always easy to remove administrative privileges, either.</span></span> <span data-ttu-id="3e968-115">考虑以下常见场景，即在与 Active Directory 域控制器相同的计算机上安装了 DNS 角色。</span><span class="sxs-lookup"><span data-stu-id="3e968-115">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span> <span data-ttu-id="3e968-116">DNS 管理员需要本地管理员特权才能解决 DNS 服务器方面的问题。</span><span class="sxs-lookup"><span data-stu-id="3e968-116">Your DNS administrators require local administrator privileges to fix issues with the DNS server.</span></span> <span data-ttu-id="3e968-117">但为此，你必须让这些管理员成为权限较高的域管理员安全组的成员。</span><span class="sxs-lookup"><span data-stu-id="3e968-117">But to do so, you must make them members of the highly privileged **Domain Admins** security group.</span></span> <span data-ttu-id="3e968-118">该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。</span><span class="sxs-lookup"><span data-stu-id="3e968-118">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="3e968-119">JEA 通过“最小特权”原则来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="3e968-119">JEA addresses this problem through the principle of **Least Privilege**.</span></span> <span data-ttu-id="3e968-120">通过 JEA，可为 DNS 管理员配置管理终结点，使其仅能够访问完成工作所需的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="3e968-120">With JEA, you can configure a management endpoint for DNS administrators that gives them access only to the PowerShell commands they need to get their job done.</span></span> <span data-ttu-id="3e968-121">这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存或重启 DNS 服务器，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。</span><span class="sxs-lookup"><span data-stu-id="3e968-121">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span> <span data-ttu-id="3e968-122">更棒的是，将 JEA 会话配置为使用具有临时特权的虚拟帐户时，DNS 管理员可使用非管理员凭据连接到服务器，而且仍可运行通常需要管理员特权的命令。</span><span class="sxs-lookup"><span data-stu-id="3e968-122">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using **non-admin** credentials and still run commands that typically require admin privileges.</span></span> <span data-ttu-id="3e968-123">JEA 使你能够从具有广泛权限的本地/域管理员角色中删除用户，并谨慎控制他们可在每台计算机上执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3e968-123">JEA enables you to remove users from widely privileged local/domain administrator roles and carefully control what they can do on each machine.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3e968-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3e968-124">Next steps</span></span>

<span data-ttu-id="3e968-125">要详细了解 JEA 的使用要求，请参阅[先决条件](prerequisites.md)一文。</span><span class="sxs-lookup"><span data-stu-id="3e968-125">To learn more about the requirements to use JEA, see the [Prerequisites](prerequisites.md) article.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="3e968-126">示例和 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="3e968-126">Samples and DSC resource</span></span>

<span data-ttu-id="3e968-127">示例 JEA 配置和 JEA DSC 资源可以在 [JEA GitHub 存储库](https://github.com/PowerShell/JEA)中找到。</span><span class="sxs-lookup"><span data-stu-id="3e968-127">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>
