---
description: 介绍 PowerShell 执行策略并说明如何管理它们。
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 1a2b8458b39233f96d47a52e3fea21b31e9b3c42
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603608"
---
# <a name="about-execution-policies"></a><span data-ttu-id="e82ea-103">关于执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-103">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="e82ea-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="e82ea-104">Short Description</span></span>
<span data-ttu-id="e82ea-105">介绍 PowerShell 执行策略并说明如何管理它们。</span><span class="sxs-lookup"><span data-stu-id="e82ea-105">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="e82ea-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="e82ea-106">Long Description</span></span>

<span data-ttu-id="e82ea-107">PowerShell 执行策略是一项安全功能，用于控制 PowerShell 加载配置文件和运行脚本的条件。</span><span class="sxs-lookup"><span data-stu-id="e82ea-107">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="e82ea-108">此功能有助于防止恶意脚本的执行。</span><span class="sxs-lookup"><span data-stu-id="e82ea-108">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="e82ea-109">在 Windows 计算机上，可以为本地计算机、当前用户或特定会话设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-109">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="e82ea-110">你还可以使用组策略设置为计算机和用户设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-110">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="e82ea-111">本地计算机和当前用户的执行策略存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-111">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="e82ea-112">不需要在 PowerShell 配置文件中设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-112">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="e82ea-113">特定会话的执行策略仅存储在内存中，并在会话关闭时丢失。</span><span class="sxs-lookup"><span data-stu-id="e82ea-113">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="e82ea-114">执行策略不是限制用户操作的安全系统。</span><span class="sxs-lookup"><span data-stu-id="e82ea-114">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="e82ea-115">例如，当用户无法运行脚本时，可以通过在命令行中键入脚本内容来轻松地绕过策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-115">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="e82ea-116">相反，执行策略可帮助用户设置基本规则并防止无意中违反它们。</span><span class="sxs-lookup"><span data-stu-id="e82ea-116">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

<span data-ttu-id="e82ea-117">在非 Windows 计算机上，默认的执行策略是不 **受限制** 的，无法更改。</span><span class="sxs-lookup"><span data-stu-id="e82ea-117">On non-Windows computers, the default execution policy is **Unrestricted** and cannot be changed.</span></span> <span data-ttu-id="e82ea-118">`Set-ExecutionPolicy`Cmdlet 可用，但 PowerShell 会显示不受支持的控制台消息。</span><span class="sxs-lookup"><span data-stu-id="e82ea-118">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span> <span data-ttu-id="e82ea-119">虽然 `Get-ExecutionPolicy` 在非 windows 平台上返回不 **受限制** ，但行为确实与 **回避** 匹配，因为这些平台不实现 Windows 安全区域。</span><span class="sxs-lookup"><span data-stu-id="e82ea-119">While `Get-ExecutionPolicy` returns **Unrestricted** on non-Windows platforms, the behavior really matches **Bypass** because those platforms do not implement the Windows Security Zones.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="e82ea-120">PowerShell 执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-120">PowerShell execution policies</span></span>

<span data-ttu-id="e82ea-121">这些策略的强制仅在 Windows 平台上发生。</span><span class="sxs-lookup"><span data-stu-id="e82ea-121">Enforcement of these policies only occurs on Windows platforms.</span></span> <span data-ttu-id="e82ea-122">PowerShell 执行策略如下所示：</span><span class="sxs-lookup"><span data-stu-id="e82ea-122">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="e82ea-123">AllSigned</span><span class="sxs-lookup"><span data-stu-id="e82ea-123">AllSigned</span></span>

- <span data-ttu-id="e82ea-124">脚本可以运行。</span><span class="sxs-lookup"><span data-stu-id="e82ea-124">Scripts can run.</span></span>
- <span data-ttu-id="e82ea-125">要求所有脚本和配置文件都由受信任的发布者签名，包括在本地计算机上编写的脚本。</span><span class="sxs-lookup"><span data-stu-id="e82ea-125">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="e82ea-126">在从尚未归类为受信任或不受信任的发布者运行脚本之前，将提示您。</span><span class="sxs-lookup"><span data-stu-id="e82ea-126">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="e82ea-127">运行已签名但恶意脚本的风险。</span><span class="sxs-lookup"><span data-stu-id="e82ea-127">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="e82ea-128">免验证</span><span class="sxs-lookup"><span data-stu-id="e82ea-128">Bypass</span></span>

- <span data-ttu-id="e82ea-129">不阻止任何操作，并且没有任何警告或提示。</span><span class="sxs-lookup"><span data-stu-id="e82ea-129">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="e82ea-130">此执行策略适用于以下配置：将 PowerShell 脚本内置于更大的应用程序或配置，其中 PowerShell 是具有其自己的安全模型的程序的基础。</span><span class="sxs-lookup"><span data-stu-id="e82ea-130">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="e82ea-131">默认</span><span class="sxs-lookup"><span data-stu-id="e82ea-131">Default</span></span>

- <span data-ttu-id="e82ea-132">设置默认的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-132">Sets the default execution policy.</span></span>
- <span data-ttu-id="e82ea-133">Windows 客户端 **限制**。</span><span class="sxs-lookup"><span data-stu-id="e82ea-133">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="e82ea-134">适用于 Windows server 的 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="e82ea-134">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="e82ea-135">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="e82ea-135">RemoteSigned</span></span>

- <span data-ttu-id="e82ea-136">Windows server 计算机的默认执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-136">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="e82ea-137">脚本可以运行。</span><span class="sxs-lookup"><span data-stu-id="e82ea-137">Scripts can run.</span></span>
- <span data-ttu-id="e82ea-138">要求来自受信任的发布者的脚本和配置文件的数字签名，这些脚本和配置文件是从 internet 下载的，其中包括电子邮件和即时消息程序。</span><span class="sxs-lookup"><span data-stu-id="e82ea-138">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="e82ea-139">不需要在本地计算机上编写的脚本上的数字签名，也不需要从 internet 下载。</span><span class="sxs-lookup"><span data-stu-id="e82ea-139">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="e82ea-140">如果未对脚本进行阻止，则运行从 internet 下载的脚本，而不是未签名的脚本，例如通过使用 `Unblock-File` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e82ea-140">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="e82ea-141">从 internet 以外的源运行未签名脚本的风险，以及可能是恶意的签名脚本。</span><span class="sxs-lookup"><span data-stu-id="e82ea-141">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="e82ea-142">受限制</span><span class="sxs-lookup"><span data-stu-id="e82ea-142">Restricted</span></span>

- <span data-ttu-id="e82ea-143">Windows 客户端计算机的默认执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-143">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="e82ea-144">允许单独的命令，但不允许脚本。</span><span class="sxs-lookup"><span data-stu-id="e82ea-144">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="e82ea-145">阻止运行所有脚本文件，包括格式设置和配置文件 (`.ps1xml`) 、模块脚本文件 (`.psm1`) 和 PowerShell 配置文件 (`.ps1`) 。</span><span class="sxs-lookup"><span data-stu-id="e82ea-145">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="e82ea-146">Undefined</span><span class="sxs-lookup"><span data-stu-id="e82ea-146">Undefined</span></span>

- <span data-ttu-id="e82ea-147">当前作用域中没有设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-147">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="e82ea-148">如果所有作用域中的执行策略均未 **定义**，则对 windows 客户端和 Windows Server **RemoteSigned** 的有效执行策略将 **受到限制**。</span><span class="sxs-lookup"><span data-stu-id="e82ea-148">If the execution policy in all scopes is **Undefined**, the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="e82ea-149">非受限</span><span class="sxs-lookup"><span data-stu-id="e82ea-149">Unrestricted</span></span>

- <span data-ttu-id="e82ea-150">非 Windows 计算机的默认执行策略无法更改。</span><span class="sxs-lookup"><span data-stu-id="e82ea-150">The default execution policy for non-Windows computers and cannot be changed.</span></span>
- <span data-ttu-id="e82ea-151">未签名的脚本可以运行。</span><span class="sxs-lookup"><span data-stu-id="e82ea-151">Unsigned scripts can run.</span></span> <span data-ttu-id="e82ea-152">存在运行恶意脚本的风险。</span><span class="sxs-lookup"><span data-stu-id="e82ea-152">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="e82ea-153">在运行不在本地 intranet 区域中的脚本和配置文件之前警告用户。</span><span class="sxs-lookup"><span data-stu-id="e82ea-153">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="e82ea-154">在不区分通用命名约定 (UNC) 路径与 internet 路径的系统上，可能无法使用 **RemoteSigned** 执行策略来运行 unc 路径标识的脚本。</span><span class="sxs-lookup"><span data-stu-id="e82ea-154">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="e82ea-155">执行策略作用域</span><span class="sxs-lookup"><span data-stu-id="e82ea-155">Execution policy scope</span></span>

<span data-ttu-id="e82ea-156">可以设置仅在特定作用域内有效的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-156">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="e82ea-157">**作用域** 的有效值为 **MachinePolicy**、 **UserPolicy**、 **Process**、 **CurrentUser** 和 **LocalMachine**。</span><span class="sxs-lookup"><span data-stu-id="e82ea-157">The valid values for **Scope** are **MachinePolicy**, **UserPolicy**, **Process**, **CurrentUser**, and **LocalMachine**.</span></span> <span data-ttu-id="e82ea-158">设置执行策略时， **LocalMachine** 为默认值。</span><span class="sxs-lookup"><span data-stu-id="e82ea-158">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="e82ea-159">**作用域** 值按优先级顺序列出。</span><span class="sxs-lookup"><span data-stu-id="e82ea-159">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="e82ea-160">优先级相同的策略在当前会话中有效，即使在优先级较低的情况下设置了限制性更强的策略也是如此。</span><span class="sxs-lookup"><span data-stu-id="e82ea-160">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="e82ea-161">有关详细信息，请参阅 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)。</span><span class="sxs-lookup"><span data-stu-id="e82ea-161">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="e82ea-162">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-162">MachinePolicy</span></span>

<span data-ttu-id="e82ea-163">为计算机的所有用户组策略设置。</span><span class="sxs-lookup"><span data-stu-id="e82ea-163">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="e82ea-164">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-164">UserPolicy</span></span>

<span data-ttu-id="e82ea-165">为计算机的当前用户组策略设置。</span><span class="sxs-lookup"><span data-stu-id="e82ea-165">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="e82ea-166">过程</span><span class="sxs-lookup"><span data-stu-id="e82ea-166">Process</span></span>

<span data-ttu-id="e82ea-167">**进程** 范围仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="e82ea-167">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="e82ea-168">执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，而不是保存在注册表中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-168">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="e82ea-169">关闭 PowerShell 会话后，会删除变量和值。</span><span class="sxs-lookup"><span data-stu-id="e82ea-169">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="e82ea-170">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="e82ea-170">CurrentUser</span></span>

<span data-ttu-id="e82ea-171">执行策略仅影响当前用户。</span><span class="sxs-lookup"><span data-stu-id="e82ea-171">The execution policy affects only the current user.</span></span> <span data-ttu-id="e82ea-172">它存储在 **HKEY_CURRENT_USER** 注册表子项中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-172">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="e82ea-173">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="e82ea-173">LocalMachine</span></span>

<span data-ttu-id="e82ea-174">执行策略会影响当前计算机上的所有用户。</span><span class="sxs-lookup"><span data-stu-id="e82ea-174">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="e82ea-175">它存储在 **HKEY_LOCAL_MACHINE** 注册表子项中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-175">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="e82ea-176">通过 PowerShell 管理执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-176">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="e82ea-177">若要获取当前 PowerShell 会话的有效执行策略，请使用 `Get-ExecutionPolicy` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e82ea-177">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="e82ea-178">以下命令将获取有效的执行策略：</span><span class="sxs-lookup"><span data-stu-id="e82ea-178">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="e82ea-179">若要获取影响当前会话的所有执行策略，并按优先顺序显示它们：</span><span class="sxs-lookup"><span data-stu-id="e82ea-179">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="e82ea-180">结果与以下示例输出类似：</span><span class="sxs-lookup"><span data-stu-id="e82ea-180">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="e82ea-181">在这种情况下，有效的执行策略是 **RemoteSigned** ，因为当前用户的执行策略优先于为本地计算机设置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-181">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="e82ea-182">若要获取为特定作用域设置的执行策略，请使用的 **作用域** 参数 `Get-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="e82ea-182">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="e82ea-183">例如，以下命令将获取 **CurrentUser** 作用域的执行策略：</span><span class="sxs-lookup"><span data-stu-id="e82ea-183">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="e82ea-184">更改执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-184">Change the execution policy</span></span>

<span data-ttu-id="e82ea-185">若要更改 Windows 计算机上的 PowerShell 执行策略，请使用 `Set-ExecutionPolicy` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e82ea-185">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="e82ea-186">更改立即生效。</span><span class="sxs-lookup"><span data-stu-id="e82ea-186">The change is effective immediately.</span></span> <span data-ttu-id="e82ea-187">不需要重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e82ea-187">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="e82ea-188">如果设置作用域 **LocalMachine** 或 **CurrentUser** 的执行策略，则更改将保存在注册表中并保持有效，直到再次更改。</span><span class="sxs-lookup"><span data-stu-id="e82ea-188">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser**, the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="e82ea-189">如果为 **进程** 范围设置了执行策略，则它不会保存在注册表中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-189">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="e82ea-190">将保留执行策略，直到关闭当前进程和任何子进程。</span><span class="sxs-lookup"><span data-stu-id="e82ea-190">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="e82ea-191">在 Windows Vista 和更高版本的 Windows 中，若要运行更改本地计算机的执行策略的命令 **，则** 可以通过 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e82ea-191">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="e82ea-192">更改执行策略：</span><span class="sxs-lookup"><span data-stu-id="e82ea-192">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="e82ea-193">例如：</span><span class="sxs-lookup"><span data-stu-id="e82ea-193">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="e82ea-194">若要设置特定范围中的执行策略，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e82ea-194">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="e82ea-195">例如：</span><span class="sxs-lookup"><span data-stu-id="e82ea-195">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="e82ea-196">用于更改执行策略的命令可以成功，但仍不会更改有效的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-196">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="e82ea-197">例如，为本地计算机设置执行策略的命令可能会成功，但会被当前用户的执行策略覆盖。</span><span class="sxs-lookup"><span data-stu-id="e82ea-197">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="e82ea-198">删除执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-198">Remove the execution policy</span></span>

<span data-ttu-id="e82ea-199">若要删除特定作用域的执行策略，请将执行策略设置为 **Undefined**。</span><span class="sxs-lookup"><span data-stu-id="e82ea-199">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="e82ea-200">例如，要为本地计算机的所有用户删除执行策略，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e82ea-200">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="e82ea-201">删除 **作用域** 的执行策略：</span><span class="sxs-lookup"><span data-stu-id="e82ea-201">To remove the execution policy for a **Scope**:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="e82ea-202">如果未在任何范围内设置执行策略，则会 **限制** 有效执行策略，这是 Windows 客户端的默认设置。</span><span class="sxs-lookup"><span data-stu-id="e82ea-202">If no execution policy is set in any scope, the effective execution policy is **Restricted**, which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="e82ea-203">为一个会话设置不同的策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-203">Set a different policy for one session</span></span>

<span data-ttu-id="e82ea-204">你可以使用 **pwsh.exe** 的 **set-executionpolicy** 参数为新的 PowerShell 会话设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-204">You can use the **ExecutionPolicy** parameter of **pwsh.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="e82ea-205">策略只影响当前会话和子会话。</span><span class="sxs-lookup"><span data-stu-id="e82ea-205">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="e82ea-206">若要为新会话设置执行策略，请在命令行中启动 PowerShell，如 **cmd.exe** 或 powershell，然后使用 **pwsh.exe** 的 **set-executionpolicy** 参数设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-206">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **pwsh.exe** to set the execution policy.</span></span>

<span data-ttu-id="e82ea-207">例如：</span><span class="sxs-lookup"><span data-stu-id="e82ea-207">For example:</span></span>

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="e82ea-208">你设置的执行策略未存储在注册表中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-208">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="e82ea-209">相反，它存储在 `$env:PSExecutionPolicyPreference` 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-209">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="e82ea-210">关闭设置了策略的会话时，将删除该变量。</span><span class="sxs-lookup"><span data-stu-id="e82ea-210">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="e82ea-211">不能通过编辑变量值来更改策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-211">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="e82ea-212">在会话期间，为会话设置的执行策略优先于在注册表中为本地计算机或当前用户设置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-212">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="e82ea-213">但是，它不会优先于通过使用组策略设置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-213">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="e82ea-214">使用组策略来管理执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-214">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="e82ea-215">您可以使用 " **打开脚本执行** 组策略" 设置来管理企业中的计算机的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-215">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="e82ea-216">组策略设置将替代在所有作用域中在 PowerShell 中设置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-216">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="e82ea-217">" **打开脚本执行** " 策略设置如下所示：</span><span class="sxs-lookup"><span data-stu-id="e82ea-217">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="e82ea-218">如果禁用 " **启用脚本执行**"，脚本将不会运行。</span><span class="sxs-lookup"><span data-stu-id="e82ea-218">If you disable **Turn on Script Execution**, scripts do not run.</span></span> <span data-ttu-id="e82ea-219">这等效于 **受限制** 的执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-219">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="e82ea-220">如果启用 "启用 **脚本执行**"，则可以选择执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-220">If you enable **Turn on Script Execution**, you can select an execution policy.</span></span> <span data-ttu-id="e82ea-221">组策略设置等效于以下执行策略设置：</span><span class="sxs-lookup"><span data-stu-id="e82ea-221">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="e82ea-222">组策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-222">Group Policy</span></span>                                  | <span data-ttu-id="e82ea-223">执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-223">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="e82ea-224">允许所有脚本</span><span class="sxs-lookup"><span data-stu-id="e82ea-224">Allow all scripts</span></span>                             | <span data-ttu-id="e82ea-225">非受限</span><span class="sxs-lookup"><span data-stu-id="e82ea-225">Unrestricted</span></span>     |
  | <span data-ttu-id="e82ea-226">允许本地脚本和远程签名的脚本</span><span class="sxs-lookup"><span data-stu-id="e82ea-226">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="e82ea-227">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="e82ea-227">RemoteSigned</span></span>     |
  | <span data-ttu-id="e82ea-228">仅允许签名脚本</span><span class="sxs-lookup"><span data-stu-id="e82ea-228">Allow only signed scripts</span></span>                     | <span data-ttu-id="e82ea-229">AllSigned</span><span class="sxs-lookup"><span data-stu-id="e82ea-229">AllSigned</span></span>        |

- <span data-ttu-id="e82ea-230">如果未配置 " **启用脚本执行** "，则它不起作用。</span><span class="sxs-lookup"><span data-stu-id="e82ea-230">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="e82ea-231">在 PowerShell 中设置的执行策略是有效的。</span><span class="sxs-lookup"><span data-stu-id="e82ea-231">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="e82ea-232">PowerShellExecutionPolicy 和 PowerShellExecutionPolicy 文件将 **打开脚本执行** 策略添加到组策略编辑器中的 "计算机配置" 和 "用户配置" 节点，路径如下。</span><span class="sxs-lookup"><span data-stu-id="e82ea-232">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="e82ea-233">对于 Windows XP 和 Windows Server 2003：</span><span class="sxs-lookup"><span data-stu-id="e82ea-233">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="e82ea-234">管理 \Windows 组件 \Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e82ea-234">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="e82ea-235">对于 Windows Vista 和更高版本的 Windows：</span><span class="sxs-lookup"><span data-stu-id="e82ea-235">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="e82ea-236">管理 Templates\Classic 管理模板 </span><span class="sxs-lookup"><span data-stu-id="e82ea-236">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="e82ea-237">Windows \Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e82ea-237">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="e82ea-238">"计算机配置" 节点中设置的策略优先于 "用户配置" 节点中设置的策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-238">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="e82ea-239">有关详细信息，请参阅 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e82ea-239">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="e82ea-240">执行策略优先级</span><span class="sxs-lookup"><span data-stu-id="e82ea-240">Execution policy precedence</span></span>

<span data-ttu-id="e82ea-241">在确定会话的有效执行策略时，PowerShell 将按以下优先顺序评估执行策略：</span><span class="sxs-lookup"><span data-stu-id="e82ea-241">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="e82ea-242">组策略： MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-242">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="e82ea-243">组策略： UserPolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-243">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="e82ea-244">执行策略：处理 (或 `pwsh.exe -ExecutionPolicy`) </span><span class="sxs-lookup"><span data-stu-id="e82ea-244">Execution Policy: Process (or `pwsh.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="e82ea-245">执行策略： CurrentUser</span><span class="sxs-lookup"><span data-stu-id="e82ea-245">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="e82ea-246">执行策略： LocalMachine</span><span class="sxs-lookup"><span data-stu-id="e82ea-246">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="e82ea-247">管理签名和未签名的脚本</span><span class="sxs-lookup"><span data-stu-id="e82ea-247">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="e82ea-248">在 Windows 中，Internet Explorer 和 Microsoft Edge 等程序将备用数据流添加到下载的文件中。</span><span class="sxs-lookup"><span data-stu-id="e82ea-248">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="e82ea-249">这会将该文件标记为 "来自 Internet"。</span><span class="sxs-lookup"><span data-stu-id="e82ea-249">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="e82ea-250">如果 PowerShell 执行策略是 **RemoteSigned**，则 powershell 不会运行从 internet 下载的未签名脚本，其中包括电子邮件和即时消息程序。</span><span class="sxs-lookup"><span data-stu-id="e82ea-250">If your PowerShell execution policy is **RemoteSigned**, PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="e82ea-251">你可以对脚本进行签名，或选择运行未签名的脚本，而无需更改执行策略。</span><span class="sxs-lookup"><span data-stu-id="e82ea-251">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="e82ea-252">从 PowerShell 3.0 开始，可以使用 cmdlet 的 **Stream** 参数 `Get-Item` 来检测因从 internet 下载而被阻止的文件。</span><span class="sxs-lookup"><span data-stu-id="e82ea-252">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="e82ea-253">使用 `Unblock-File` cmdlet 取消阻止脚本，以便可以在 PowerShell 中运行它们。</span><span class="sxs-lookup"><span data-stu-id="e82ea-253">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="e82ea-254">有关详细信息，请参阅 [about_Signing](about_Signing.md)、 [获取项](xref:Microsoft.PowerShell.Management.Get-Item)和 [取消阻止文件](xref:Microsoft.PowerShell.Utility.Unblock-File)。</span><span class="sxs-lookup"><span data-stu-id="e82ea-254">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="e82ea-255">下载文件的其他方法可能不会将文件标记为来自 Internet 区域。</span><span class="sxs-lookup"><span data-stu-id="e82ea-255">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="e82ea-256">示例包括：</span><span class="sxs-lookup"><span data-stu-id="e82ea-256">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="e82ea-257">Windows Server Core 和 Window Nano Server 上的执行策略</span><span class="sxs-lookup"><span data-stu-id="e82ea-257">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="e82ea-258">在某些情况下，当 PowerShell 6 在 Windows Server Core 或 Windows Nano Server 上运行时，执行策略可能会失败并出现以下错误：</span><span class="sxs-lookup"><span data-stu-id="e82ea-258">When PowerShell 6 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="e82ea-259">PowerShell 使用 Windows Desktop Shell 中的 Api (`explorer.exe`) 验证脚本文件的区域。</span><span class="sxs-lookup"><span data-stu-id="e82ea-259">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="e82ea-260">Windows Shell 在 Windows Server Core 和 Windows Nano Server 上不可用。</span><span class="sxs-lookup"><span data-stu-id="e82ea-260">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="e82ea-261">如果 Windows 桌面 Shell 不可用或无响应，也可能会在任何 Windows 系统上收到此错误。</span><span class="sxs-lookup"><span data-stu-id="e82ea-261">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="e82ea-262">例如，在登录过程中，PowerShell 登录脚本可以在 Windows 桌面准备就绪之前开始执行，从而导致失败。</span><span class="sxs-lookup"><span data-stu-id="e82ea-262">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="e82ea-263">使用 **绕过** 或 **AllSigned** 的执行策略不需要区域检查来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="e82ea-263">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="e82ea-264">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e82ea-264">See Also</span></span>

[<span data-ttu-id="e82ea-265">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="e82ea-265">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="e82ea-266">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="e82ea-266">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="e82ea-267">about_Signing</span><span class="sxs-lookup"><span data-stu-id="e82ea-267">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="e82ea-268">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-268">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="e82ea-269">Get-Item</span><span class="sxs-lookup"><span data-stu-id="e82ea-269">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="e82ea-270">Pwsh 控制台帮助</span><span class="sxs-lookup"><span data-stu-id="e82ea-270">Pwsh Console Help</span></span>](about_pwsh.md)

[<span data-ttu-id="e82ea-271">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e82ea-271">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="e82ea-272">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="e82ea-272">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)

