---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 先决条件
description: 本文介绍使用 JEA 前必须满足的先决条件。
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501722"
---
# <a name="prerequisites"></a><span data-ttu-id="e38d1-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="e38d1-104">Prerequisites</span></span>

<span data-ttu-id="e38d1-105">Just Enough Administration 是 PowerShell 5.0 及更高版本随附的功能。</span><span class="sxs-lookup"><span data-stu-id="e38d1-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="e38d1-106">本文介绍使用 JEA 前必须满足的先决条件。</span><span class="sxs-lookup"><span data-stu-id="e38d1-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="e38d1-107">查看安装的 PowerShell 版本类型</span><span class="sxs-lookup"><span data-stu-id="e38d1-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="e38d1-108">若要查看系统上安装的 PowerShell 版本类型，请查看 Windows PowerShell 提示符中的 `$PSVersionTable` 变量。</span><span class="sxs-lookup"><span data-stu-id="e38d1-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="e38d1-109">JEA 适用于 PowerShell 5.0 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="e38d1-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="e38d1-110">要使用完整功能，建议安装适用于系统的 PowerShell 最新版。</span><span class="sxs-lookup"><span data-stu-id="e38d1-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="e38d1-111">下表介绍了 JEA 在 Windows Server 上的可用性：</span><span class="sxs-lookup"><span data-stu-id="e38d1-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="e38d1-112">服务器操作系统</span><span class="sxs-lookup"><span data-stu-id="e38d1-112">Server Operating System</span></span> |                <span data-ttu-id="e38d1-113">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="e38d1-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="e38d1-114">Windows Server 2016 及更高版本</span><span class="sxs-lookup"><span data-stu-id="e38d1-114">Windows Server 2016+</span></span>    | <span data-ttu-id="e38d1-115">已预安装</span><span class="sxs-lookup"><span data-stu-id="e38d1-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="e38d1-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e38d1-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="e38d1-117">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="e38d1-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="e38d1-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e38d1-118">Windows Server 2012</span></span>     | <span data-ttu-id="e38d1-119">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="e38d1-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="e38d1-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e38d1-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="e38d1-121">减少了功能<sup>1</sup>（如果 WMF 5.1 已安装）</span><span class="sxs-lookup"><span data-stu-id="e38d1-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="e38d1-122">此外，还可以在家庭或工作计算机上使用 JEA：</span><span class="sxs-lookup"><span data-stu-id="e38d1-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="e38d1-123">客户端操作系统</span><span class="sxs-lookup"><span data-stu-id="e38d1-123">Client Operating System</span></span> |                   <span data-ttu-id="e38d1-124">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="e38d1-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="e38d1-125">Windows 10 1607 及更高版本</span><span class="sxs-lookup"><span data-stu-id="e38d1-125">Windows 10 1607+</span></span>        | <span data-ttu-id="e38d1-126">已预安装</span><span class="sxs-lookup"><span data-stu-id="e38d1-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="e38d1-127">Windows 10 1603 版、1511 版</span><span class="sxs-lookup"><span data-stu-id="e38d1-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="e38d1-128">已预安装，但减少了功能<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e38d1-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="e38d1-129">Windows 10 1507 版</span><span class="sxs-lookup"><span data-stu-id="e38d1-129">Windows 10 1507</span></span>         | <span data-ttu-id="e38d1-130">不可用</span><span class="sxs-lookup"><span data-stu-id="e38d1-130">Not available</span></span>                                        |
| <span data-ttu-id="e38d1-131">Windows 8、8.1</span><span class="sxs-lookup"><span data-stu-id="e38d1-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="e38d1-132">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="e38d1-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="e38d1-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="e38d1-133">Windows 7</span></span>               | <span data-ttu-id="e38d1-134">减少了功能<sup>1</sup>（如果 WMF 5.1 已安装）</span><span class="sxs-lookup"><span data-stu-id="e38d1-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="e38d1-135"><sup>1</sup> 无法将 JEA 配置为在 Windows Server 2008 R2 或 Windows 7 上使用组托管服务帐户。</span><span class="sxs-lookup"><span data-stu-id="e38d1-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="e38d1-136">*支持* 虚拟帐户和其他 JEA 功能。</span><span class="sxs-lookup"><span data-stu-id="e38d1-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="e38d1-137"><sup>2</sup> Windows 10 版本 1511 和 1603 不支持以下 JEA 功能：</span><span class="sxs-lookup"><span data-stu-id="e38d1-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="e38d1-138">作为组托管服务帐户运行</span><span class="sxs-lookup"><span data-stu-id="e38d1-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="e38d1-139">会话配置中的条件访问规则</span><span class="sxs-lookup"><span data-stu-id="e38d1-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="e38d1-140">用户驱动器</span><span class="sxs-lookup"><span data-stu-id="e38d1-140">The user drive</span></span>
  - <span data-ttu-id="e38d1-141">授予对本地用户帐户的访问权限</span><span class="sxs-lookup"><span data-stu-id="e38d1-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="e38d1-142">若要获取对这些功能的支持，请将 Windows 更新到 1607 版（周年更新）或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e38d1-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="e38d1-143">安装 Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="e38d1-143">Install Windows Management Framework</span></span>

<span data-ttu-id="e38d1-144">如果运行的是较旧版本的 PowerShell，则可能需要使用最新的 Windows Management Framework (WMF) 更新来更新系统。</span><span class="sxs-lookup"><span data-stu-id="e38d1-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="e38d1-145">有关详细信息，请参阅 [WMF 文档](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="e38d1-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="e38d1-146">建议在升级所有服务器之前，测试工作负载与 WMF 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="e38d1-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="e38d1-147">Windows 10 用户需安装最新功能更新才能获取当前版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e38d1-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="e38d1-148">启用 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="e38d1-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="e38d1-149">PowerShell 远程处理提供了构建 JEA 的基础。</span><span class="sxs-lookup"><span data-stu-id="e38d1-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="e38d1-150">必须先确保 PowerShell 远程处理功能已启用且受到适当保护，然后才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="e38d1-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="e38d1-151">有关详细信息，请参阅 [WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)。</span><span class="sxs-lookup"><span data-stu-id="e38d1-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="e38d1-152">在 Windows Server 2012、2012 R2 和 2016 中，默认启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="e38d1-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="e38d1-153">可通过在提升的 PowerShell 窗口中运行以下命令来启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="e38d1-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="e38d1-154">启用 PowerShell 模块和脚本块日志记录（可选）</span><span class="sxs-lookup"><span data-stu-id="e38d1-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="e38d1-155">执行以下步骤将为系统上的所有 PowerShell 操作启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="e38d1-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="e38d1-156">PowerShell 模块日志记录不是 JEA 必需的，但建议启用日志记录，以确保在中心位置记录用户运行的命令。</span><span class="sxs-lookup"><span data-stu-id="e38d1-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="e38d1-157">可使用组策略配置 PowerShell 模块日志记录策略。</span><span class="sxs-lookup"><span data-stu-id="e38d1-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="e38d1-158">在工作站上打开“本地组策略编辑器”，或在 Active Directory 域控制器中，打开“组策略管理控制台”中的“组策略对象”</span><span class="sxs-lookup"><span data-stu-id="e38d1-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="e38d1-159">导航到“计算机配置\\管理模板\\Windows 组件\\Windows PowerShell”</span><span class="sxs-lookup"><span data-stu-id="e38d1-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="e38d1-160">双击“打开模块日志记录”</span><span class="sxs-lookup"><span data-stu-id="e38d1-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="e38d1-161">单击“启用”</span><span class="sxs-lookup"><span data-stu-id="e38d1-161">Click **Enabled**</span></span>
5. <span data-ttu-id="e38d1-162">在“选项”部分中，单击“模块名称”旁的“显示”</span><span class="sxs-lookup"><span data-stu-id="e38d1-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="e38d1-163">在弹出窗口中键入 `*`，记录所有模块的命令。</span><span class="sxs-lookup"><span data-stu-id="e38d1-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="e38d1-164">单击“确定”设置策略</span><span class="sxs-lookup"><span data-stu-id="e38d1-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="e38d1-165">双击“打开 PowerShell 脚本块日志记录”</span><span class="sxs-lookup"><span data-stu-id="e38d1-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="e38d1-166">单击“启用”</span><span class="sxs-lookup"><span data-stu-id="e38d1-166">Click **Enabled**</span></span>
10. <span data-ttu-id="e38d1-167">单击“确定”设置策略</span><span class="sxs-lookup"><span data-stu-id="e38d1-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="e38d1-168">（仅在已加入域的计算机上）运行 `gpupdate` 或等待组策略处理更新后的策略，然后应用相应设置</span><span class="sxs-lookup"><span data-stu-id="e38d1-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="e38d1-169">也可通过“组策略”启用系统范围的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="e38d1-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e38d1-170">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e38d1-170">Next steps</span></span>

[<span data-ttu-id="e38d1-171">创建角色功能文件</span><span class="sxs-lookup"><span data-stu-id="e38d1-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="e38d1-172">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="e38d1-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="e38d1-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e38d1-173">See also</span></span>

[<span data-ttu-id="e38d1-174">WinRM 安全性</span><span class="sxs-lookup"><span data-stu-id="e38d1-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="e38d1-175">PowerShell ♥ 蓝队</span><span class="sxs-lookup"><span data-stu-id="e38d1-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
