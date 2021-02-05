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
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="a2625-104">JEA 审核和报告</span><span class="sxs-lookup"><span data-stu-id="a2625-104">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="a2625-105">部署 JEA 后，需要定期审核 JEA 配置。</span><span class="sxs-lookup"><span data-stu-id="a2625-105">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="a2625-106">审核可帮助你评估适当的人员是否有权访问 JEA 终结点，以及向其分配的角色是否仍适用。</span><span class="sxs-lookup"><span data-stu-id="a2625-106">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="a2625-107">查找计算机上已注册的 JEA 会话</span><span class="sxs-lookup"><span data-stu-id="a2625-107">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="a2625-108">若要查看计算机上注册了哪些 JEA 会话，可使用 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2625-108">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="a2625-109">“权限”属性中列出了终结点的有效权限。</span><span class="sxs-lookup"><span data-stu-id="a2625-109">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="a2625-110">这些用户有权连接到 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="a2625-110">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="a2625-111">但他们有权访问的角色和命令却是由用于注册终结点的[会话配置文件](session-configurations.md)中的 RoleDefinitions 属性决定。</span><span class="sxs-lookup"><span data-stu-id="a2625-111">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="a2625-112">扩展 RoleDefinitions 属性，评估已注册的 JEA 终结点中的角色映射。</span><span class="sxs-lookup"><span data-stu-id="a2625-112">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="a2625-113">查找计算机上可用的角色功能</span><span class="sxs-lookup"><span data-stu-id="a2625-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="a2625-114">JEA 从 PowerShell 模块内“RoleCapabilities”文件夹中存储的 `.psrc` 文件获取角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2625-114">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="a2625-115">下面的函数会查找计算机上提供的所有角色功能。</span><span class="sxs-lookup"><span data-stu-id="a2625-115">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="a2625-116">如果多个角色功能共享同一名称，则此函数的结果顺序无需是选择角色功能的顺序。</span><span class="sxs-lookup"><span data-stu-id="a2625-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="a2625-117">查看特定用户的有效权限</span><span class="sxs-lookup"><span data-stu-id="a2625-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="a2625-118">[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet 根据用户的组成员资格枚举 JEA 终结点上可用的所有命令。</span><span class="sxs-lookup"><span data-stu-id="a2625-118">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="a2625-119">`Get-PSSessionCapability` 的输出与 JEA 会话中运行 `Get-Command -CommandType All` 的指定用户的输出完全相同。</span><span class="sxs-lookup"><span data-stu-id="a2625-119">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="a2625-120">如果用户不是将向其授予其他 JEA 权限的组的永久成员，则此 cmdlet 可能不会反映这些额外权限。</span><span class="sxs-lookup"><span data-stu-id="a2625-120">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="a2625-121">使用实时特权访问管理系统让用户能够临时隶属于安全组时，会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="a2625-121">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="a2625-122">请仔细评估用户到角色和功能的映射，确保用户仅获得成功完成其作业所需的访问级别。</span><span class="sxs-lookup"><span data-stu-id="a2625-122">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="a2625-123">PowerShell 事件日志</span><span class="sxs-lookup"><span data-stu-id="a2625-123">PowerShell event logs</span></span>

<span data-ttu-id="a2625-124">如果在系统上启用了模块或脚本块日志记录，则针对用户在 JEA 会话中运行的每条命令，可在 Windows 事件日志中看到相应事件。</span><span class="sxs-lookup"><span data-stu-id="a2625-124">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="a2625-125">要查找这些事件，请打开“Microsoft-Windows-PowerShell/Operational”事件日志，然后查找事件 ID 为 4104 的事件。</span><span class="sxs-lookup"><span data-stu-id="a2625-125">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="a2625-126">每个事件日志项目都包括在其中运行命令的会话的相关信息。</span><span class="sxs-lookup"><span data-stu-id="a2625-126">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="a2625-127">对于 JEA 会话，该事件包含 ConnectedUser 和 RunAsUser 的相关信息。</span><span class="sxs-lookup"><span data-stu-id="a2625-127">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="a2625-128">ConnectedUser 是实际创建 JEA 会话的用户。</span><span class="sxs-lookup"><span data-stu-id="a2625-128">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="a2625-129">RunAsUser 是 JEA 用于执行该命令的帐户。</span><span class="sxs-lookup"><span data-stu-id="a2625-129">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="a2625-130">应用程序事件日志显示了 RunAsUser 所做的更改。</span><span class="sxs-lookup"><span data-stu-id="a2625-130">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="a2625-131">因此需要启用模块和脚本日志记录才能将特定的命令调用回 ConnectedUser。</span><span class="sxs-lookup"><span data-stu-id="a2625-131">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="a2625-132">应用程序事件日志</span><span class="sxs-lookup"><span data-stu-id="a2625-132">Application event logs</span></span>

<span data-ttu-id="a2625-133">与外部应用程序或服务交互的 JEA 会话中运行的命令可能会将事件记录到其自己的事件日志中。</span><span class="sxs-lookup"><span data-stu-id="a2625-133">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="a2625-134">与 PowerShell 日志和脚本不同，其他日志记录机制不会捕获 JEA 会话已连接的用户。</span><span class="sxs-lookup"><span data-stu-id="a2625-134">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="a2625-135">相反，这些应用程序只记录虚拟运行身份用户。</span><span class="sxs-lookup"><span data-stu-id="a2625-135">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="a2625-136">要确定运行该命令的用户，需要参考[会话脚本](#session-transcripts)或相关 PowerShell 事件日志（其中时间和用户显示在应用程序事件日志中）。</span><span class="sxs-lookup"><span data-stu-id="a2625-136">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="a2625-137">WinRM 日志还可帮你将运行身份用户与应用程序事件日志中的连接用户联系起来。</span><span class="sxs-lookup"><span data-stu-id="a2625-137">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="a2625-138">Microsoft-Windows-Windows Remote Management/Operational 日志中 ID 为 193 的事件记录了每个新的 JEA 会话中连接用户和运行身份用户的安全标识符 (SID) 和帐户名称。</span><span class="sxs-lookup"><span data-stu-id="a2625-138">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="a2625-139">会话脚本</span><span class="sxs-lookup"><span data-stu-id="a2625-139">Session transcripts</span></span>

<span data-ttu-id="a2625-140">如果已将 JEA 配置为创建每个用户会话的脚本，则每位用户的操作文本副本将存储在指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a2625-140">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="a2625-141">以下命令（以管理员身份运行）可查找所有脚本目录。</span><span class="sxs-lookup"><span data-stu-id="a2625-141">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="a2625-142">每个脚本的开头部分都包含以下内容：会话开始时间、连接到会话的用户和分配给用户的 JEA 标识。</span><span class="sxs-lookup"><span data-stu-id="a2625-142">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="a2625-143">脚本的正文包含用户调用的每个命令的相关信息。</span><span class="sxs-lookup"><span data-stu-id="a2625-143">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="a2625-144">由于 PowerShell 远程处理的命令转换方式，所使用的命令的确切语法在 JEA 会话中不可用。</span><span class="sxs-lookup"><span data-stu-id="a2625-144">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="a2625-145">但是，仍可确定已执行的有效命令。</span><span class="sxs-lookup"><span data-stu-id="a2625-145">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="a2625-146">以下示例是来自 JEA 会话中运行 `Get-Service Dns` 的用户的脚本代码段：</span><span class="sxs-lookup"><span data-stu-id="a2625-146">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="a2625-147">CommandInvocation 行是为用户运行的每个命令编写的。</span><span class="sxs-lookup"><span data-stu-id="a2625-147">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="a2625-148">ParameterBindings 会记录随附该命令提供的每个参数和值。</span><span class="sxs-lookup"><span data-stu-id="a2625-148">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="a2625-149">在上一示例中，可看到针对 `Get-Service` cmdlet 向 Name 参数提供了值 Dns。</span><span class="sxs-lookup"><span data-stu-id="a2625-149">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="a2625-150">每个命令的输出通常还会对 `Out-Default` 触发 CommandInvocation。</span><span class="sxs-lookup"><span data-stu-id="a2625-150">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="a2625-151">`Out-Default` 的 InputObject 是从命令返回的 PowerShell 对象。</span><span class="sxs-lookup"><span data-stu-id="a2625-151">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="a2625-152">该对象的详细信息如下面几行所示，严格模拟用户将看到的内容。</span><span class="sxs-lookup"><span data-stu-id="a2625-152">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2625-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2625-153">See also</span></span>

[<span data-ttu-id="a2625-154">PowerShell ♥ the Blue Team 关于安全的博客文章</span><span class="sxs-lookup"><span data-stu-id="a2625-154">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
