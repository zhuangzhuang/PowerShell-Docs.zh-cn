---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 4c45267113ff7b8a870d5a05bf3e4ab922f7e9c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595628"
---
# <span data-ttu-id="2e3fa-102">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="2e3fa-102">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="2e3fa-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2e3fa-103">SYNOPSIS</span></span>
<span data-ttu-id="2e3fa-104">设置 Windows 计算机的 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-104">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="2e3fa-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e3fa-105">SYNTAX</span></span>

### <span data-ttu-id="2e3fa-106">全部</span><span class="sxs-lookup"><span data-stu-id="2e3fa-106">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2e3fa-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2e3fa-107">DESCRIPTION</span></span>

<span data-ttu-id="2e3fa-108">`Set-ExecutionPolicy`Cmdlet 更改 Windows 计算机的 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-108">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="2e3fa-109">有关详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-109">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="2e3fa-110">从非 Windows 计算机的 PowerShell 6.0 开始，默认的执行策略是不 **受限制** 的，无法更改。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-110">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="2e3fa-111">`Set-ExecutionPolicy`Cmdlet 可用，但 PowerShell 会显示不受支持的控制台消息。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-111">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="2e3fa-112">执行策略是 PowerShell 安全策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-112">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="2e3fa-113">执行策略确定你是否可以加载配置文件（如 PowerShell 配置文件）或运行脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-113">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="2e3fa-114">并且，在运行脚本之前是否必须对其进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-114">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="2e3fa-115">此 `Set-ExecutionPolicy` cmdlet 的默认作用域为 **LocalMachine**，这会影响使用该计算机的每个人。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-115">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine**, which affects everyone who uses the computer.</span></span> <span data-ttu-id="2e3fa-116">若要更改 **LocalMachine** 的执行策略，请以 **管理员身份运行** 启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-116">To change the execution policy for **LocalMachine**, start PowerShell with **Run as Administrator**.</span></span>

<span data-ttu-id="2e3fa-117">若要按优先级顺序显示每个作用域的执行策略，请使用 `Get-ExecutionPolicy -List` 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-117">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="2e3fa-118">若要查看 PowerShell 会话的有效执行策略，请使用 `Get-ExecutionPolicy` 不带参数的。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-118">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="2e3fa-119">示例</span><span class="sxs-lookup"><span data-stu-id="2e3fa-119">EXAMPLES</span></span>

### <span data-ttu-id="2e3fa-120">示例1：设置执行策略</span><span class="sxs-lookup"><span data-stu-id="2e3fa-120">Example 1: Set an execution policy</span></span>

<span data-ttu-id="2e3fa-121">此示例演示如何设置本地计算机的执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-121">This example shows how to set the execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="2e3fa-122">`Set-ExecutionPolicy`Cmdlet 使用 **set-executionpolicy** 参数指定 **RemoteSigned** 策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-122">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="2e3fa-123">**Scope** 参数指定默认作用域值 " **LocalMachine**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-123">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="2e3fa-124">若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-124">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="2e3fa-125">示例2：设置与组策略冲突的执行策略</span><span class="sxs-lookup"><span data-stu-id="2e3fa-125">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="2e3fa-126">此命令尝试将 **LocalMachine** 作用域的执行策略设置为 " **受限**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-126">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted**.</span></span>
<span data-ttu-id="2e3fa-127">**LocalMachine** 的限制更强，但并不是有效的策略，因为它与组策略冲突。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-127">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="2e3fa-128">**受限制** 的策略会写入到 **HKEY_LOCAL_MACHINE** 的注册表配置单元。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-128">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="2e3fa-129">`Set-ExecutionPolicy`Cmdlet 使用 **set-executionpolicy** 参数指定 **受限制** 的策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-129">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="2e3fa-130">**Scope** 参数指定默认作用域值 " **LocalMachine**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-130">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span>
<span data-ttu-id="2e3fa-131">`Get-ChildItem`Cmdlet 将 **Path** 参数与 **HKLM** 提供程序一起使用，以指定注册表位置。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-131">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="2e3fa-132">示例3：将远程计算机上的执行策略应用于本地计算机</span><span class="sxs-lookup"><span data-stu-id="2e3fa-132">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="2e3fa-133">此命令获取远程计算机上的执行策略对象并在本地计算机上设置策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-133">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="2e3fa-134">`Get-ExecutionPolicy` 沿管道向下发送 **Microsoft.PowerShell.ExecutionPolicy** 对象。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-134">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="2e3fa-135">`Set-ExecutionPolicy` 接受管道输入，而不需要 **set-executionpolicy** 参数。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-135">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="2e3fa-136">`Invoke-Command`Cmdlet 在本地计算机上执行，并将 **ScriptBlock** 发送到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-136">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="2e3fa-137">**ComputerName** 参数指定远程计算机 **Server01**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-137">The **ComputerName** parameter specifies the remote computer, **Server01**.</span></span> <span data-ttu-id="2e3fa-138">**ScriptBlock** 参数 `Get-ExecutionPolicy` 在远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-138">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="2e3fa-139">将 `Get-ExecutionPolicy` 对象向下发送到 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-139">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="2e3fa-140">`Set-ExecutionPolicy` 将执行策略应用于本地计算机的默认作用域 " **LocalMachine**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-140">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine**.</span></span>

### <span data-ttu-id="2e3fa-141">示例4：设置执行策略的作用域</span><span class="sxs-lookup"><span data-stu-id="2e3fa-141">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="2e3fa-142">此示例演示如何为指定的作用域 " **CurrentUser**" 设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-142">This example shows how to set an execution policy for a specified scope, **CurrentUser**.</span></span> <span data-ttu-id="2e3fa-143">**CurrentUser** 范围仅影响设置此作用域的用户。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-143">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="2e3fa-144">`Set-ExecutionPolicy` 使用 **set-executionpolicy** 参数指定 **AllSigned** 策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-144">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="2e3fa-145">**Scope** 参数指定 **CurrentUser**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-145">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="2e3fa-146">若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-146">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="2e3fa-147">用户的有效执行策略将变为 " **AllSigned**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-147">The effective execution policy for the user becomes **AllSigned**.</span></span>

### <span data-ttu-id="2e3fa-148">示例5：删除当前用户的执行策略</span><span class="sxs-lookup"><span data-stu-id="2e3fa-148">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="2e3fa-149">此示例演示如何使用 **未定义** 执行策略删除指定作用域的执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-149">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="2e3fa-150">`Set-ExecutionPolicy` 使用 **set-executionpolicy** 参数指定 **未定义** 的策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-150">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="2e3fa-151">**Scope** 参数指定 **CurrentUser**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-151">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="2e3fa-152">若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-152">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="2e3fa-153">示例6：设置当前 PowerShell 会话的执行策略</span><span class="sxs-lookup"><span data-stu-id="2e3fa-153">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="2e3fa-154">**进程** 范围仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-154">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="2e3fa-155">执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，并在会话关闭时删除。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-155">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="2e3fa-156">`Set-ExecutionPolicy`使用 **set-executionpolicy** 参数来指定 **AllSigned** 策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-156">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="2e3fa-157">**Scope** 参数指定值 **进程**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-157">The **Scope** parameter specifies the value **Process**.</span></span> <span data-ttu-id="2e3fa-158">若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-158">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="2e3fa-159">示例7：取消阻止脚本，以便在不更改执行策略的情况下运行该脚本</span><span class="sxs-lookup"><span data-stu-id="2e3fa-159">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="2e3fa-160">此示例演示 **RemoteSigned** 执行策略如何阻止你运行未签名的脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-160">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="2e3fa-161">最佳做法是读取脚本的代码，并在使用 cmdlet **之前** 验证它是否安全 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-161">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="2e3fa-162">`Unblock-File`Cmdlet 取消阻止脚本，以便它们可以运行，但不会更改执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-162">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="2e3fa-163">`Set-ExecutionPolicy`使用 **set-executionpolicy** 参数来指定 **RemoteSigned** 策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-163">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="2e3fa-164">策略设置为默认作用域 " **LocalMachine**"。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-164">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="2e3fa-165">`Get-ExecutionPolicy`Cmdlet 显示 **RemoteSigned** 是当前 PowerShell 会话的有效执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-165">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="2e3fa-166">从当前目录执行 **Start-ActivityTracker.ps1** 脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-166">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="2e3fa-167">由于脚本未进行数字签名，因此脚本被 **RemoteSigned** 阻止。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-167">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="2e3fa-168">在此示例中，脚本的代码已评审并验证为可安全运行。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-168">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="2e3fa-169">`Unblock-File`Cmdlet 使用 **Path** 参数取消阻止脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-169">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="2e3fa-170">若要验证是否 `Unblock-File` 未更改执行策略， `Get-ExecutionPolicy` 则会显示有效的执行策略 **RemoteSigned**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-170">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="2e3fa-171">将从当前目录执行 **Start-ActivityTracker.ps1** 的脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-171">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="2e3fa-172">脚本开始运行，因为它已被 cmdlet 取消阻止 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-172">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="2e3fa-173">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e3fa-173">PARAMETERS</span></span>

### <span data-ttu-id="2e3fa-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2e3fa-174">-Confirm</span></span>

<span data-ttu-id="2e3fa-175">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-175">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e3fa-176">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="2e3fa-176">-ExecutionPolicy</span></span>

<span data-ttu-id="2e3fa-177">指定执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-177">Specifies the execution policy.</span></span> <span data-ttu-id="2e3fa-178">如果没有组策略，并且每个作用域的执行策略设置为 " **未定义**"，则 " **受限制** " 将成为所有用户的有效策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-178">If there are no Group Policies and each scope's execution policy is set to **Undefined**, then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="2e3fa-179">可接受的执行策略值如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e3fa-179">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="2e3fa-180">**AllSigned**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-180">**AllSigned**.</span></span> <span data-ttu-id="2e3fa-181">要求所有脚本和配置文件都由受信任的发布者签名，包括在本地计算机上编写的脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-181">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="2e3fa-182">**绕过**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-182">**Bypass**.</span></span> <span data-ttu-id="2e3fa-183">不阻止任何操作，并且没有任何警告或提示。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-183">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="2e3fa-184">**Default**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-184">**Default**.</span></span> <span data-ttu-id="2e3fa-185">设置默认的执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-185">Sets the default execution policy.</span></span> <span data-ttu-id="2e3fa-186">**适用于 windows** 客户端或 windows 服务器的 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-186">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="2e3fa-187">**RemoteSigned**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-187">**RemoteSigned**.</span></span> <span data-ttu-id="2e3fa-188">要求从 Internet 下载的所有脚本和配置文件都由受信任的发布者进行签名。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-188">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="2e3fa-189">Windows server 计算机的默认执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-189">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="2e3fa-190">**限制**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-190">**Restricted**.</span></span> <span data-ttu-id="2e3fa-191">不加载配置文件或运行脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-191">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="2e3fa-192">默认的执行策略 Windows 客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-192">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="2e3fa-193">**未定义**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-193">**Undefined**.</span></span> <span data-ttu-id="2e3fa-194">未为该作用域设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-194">No execution policy is set for the scope.</span></span> <span data-ttu-id="2e3fa-195">从非组策略设置的作用域中删除已分配的执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-195">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="2e3fa-196">如果所有作用域中的执行策略均未 **定义**，则会 **限制** 有效的执行策略。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-196">If the execution policy in all scopes is **Undefined**, the effective execution policy is **Restricted**.</span></span>
- <span data-ttu-id="2e3fa-197">**无限制**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-197">**Unrestricted**.</span></span> <span data-ttu-id="2e3fa-198">从 PowerShell 6.0 开始，这是非 Windows 计算机的默认执行策略，无法更改。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-198">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="2e3fa-199">加载所有配置文件并运行所有脚本。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-199">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="2e3fa-200">如果运行从 internet 下载的未签名脚本，则会在运行之前提示你提供权限。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-200">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2e3fa-201">-Force</span><span class="sxs-lookup"><span data-stu-id="2e3fa-201">-Force</span></span>

<span data-ttu-id="2e3fa-202">抑制所有确认提示。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-202">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="2e3fa-203">请谨慎使用此参数，以避免意外结果。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-203">Use caution with this parameter to avoid unexpected results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e3fa-204">-Scope</span><span class="sxs-lookup"><span data-stu-id="2e3fa-204">-Scope</span></span>

<span data-ttu-id="2e3fa-205">指定受执行策略影响的作用域。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-205">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="2e3fa-206">默认作用域为 **LocalMachine**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-206">The default scope is **LocalMachine**.</span></span>

<span data-ttu-id="2e3fa-207">有效的执行策略由优先级顺序确定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e3fa-207">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="2e3fa-208">**MachinePolicy**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-208">**MachinePolicy**.</span></span> <span data-ttu-id="2e3fa-209">为计算机的所有用户组策略设置。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-209">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="2e3fa-210">**UserPolicy**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-210">**UserPolicy**.</span></span> <span data-ttu-id="2e3fa-211">为计算机的当前用户组策略设置。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-211">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="2e3fa-212">**进程**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-212">**Process**.</span></span> <span data-ttu-id="2e3fa-213">仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-213">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="2e3fa-214">**CurrentUser**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-214">**CurrentUser**.</span></span> <span data-ttu-id="2e3fa-215">仅影响当前用户。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-215">Affects only the current user.</span></span>
- <span data-ttu-id="2e3fa-216">**LocalMachine**。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-216">**LocalMachine**.</span></span> <span data-ttu-id="2e3fa-217">影响计算机的所有用户的默认作用域。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-217">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="2e3fa-218">**进程** 范围仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-218">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="2e3fa-219">执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，而不是保存在注册表中。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-219">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="2e3fa-220">关闭 PowerShell 会话后，会删除变量和值。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-220">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="2e3fa-221">**CurrentUser** 作用域的执行策略将写入到 **HKEY_LOCAL_USER** 的注册表配置单元中。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-221">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER**.</span></span>

<span data-ttu-id="2e3fa-222">**LocalMachine** 作用域的执行策略将写入到 **HKEY_LOCAL_MACHINE** 的注册表配置单元中。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-222">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e3fa-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2e3fa-223">-WhatIf</span></span>

<span data-ttu-id="2e3fa-224">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-224">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2e3fa-225">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-225">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e3fa-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e3fa-226">CommonParameters</span></span>

<span data-ttu-id="2e3fa-227">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e3fa-228">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e3fa-229">输入</span><span class="sxs-lookup"><span data-stu-id="2e3fa-229">INPUTS</span></span>

### <span data-ttu-id="2e3fa-230">Microsoft.PowerShell.ExecutionPolicy、System.String</span><span class="sxs-lookup"><span data-stu-id="2e3fa-230">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="2e3fa-231">可以通过管道将执行策略对象或包含执行策略名称的字符串传递给 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-231">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="2e3fa-232">输出</span><span class="sxs-lookup"><span data-stu-id="2e3fa-232">OUTPUTS</span></span>

### <span data-ttu-id="2e3fa-233">无</span><span class="sxs-lookup"><span data-stu-id="2e3fa-233">None</span></span>

<span data-ttu-id="2e3fa-234">`Set-ExecutionPolicy` 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-234">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="2e3fa-235">注释</span><span class="sxs-lookup"><span data-stu-id="2e3fa-235">NOTES</span></span>

<span data-ttu-id="2e3fa-236">`Set-ExecutionPolicy` 不会更改 **MachinePolicy** 和 **UserPolicy** 作用域，因为它们由组策略设置。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-236">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="2e3fa-237">`Set-ExecutionPolicy` 不会重写组策略，即使用户首选项比策略更严格。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-237">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="2e3fa-238">如果为计算机或用户启用了组策略 **打开脚本执行** ，则将保存用户首选项，但这不是有效的。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-238">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="2e3fa-239">PowerShell 会显示一条消息，说明冲突。</span><span class="sxs-lookup"><span data-stu-id="2e3fa-239">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="2e3fa-240">相关链接</span><span class="sxs-lookup"><span data-stu-id="2e3fa-240">RELATED LINKS</span></span>

[<span data-ttu-id="2e3fa-241">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="2e3fa-241">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="2e3fa-242">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="2e3fa-242">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="2e3fa-243">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2e3fa-243">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2e3fa-244">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2e3fa-244">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="2e3fa-245">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2e3fa-245">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="2e3fa-246">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="2e3fa-246">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="2e3fa-247">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2e3fa-247">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="2e3fa-248">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2e3fa-248">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="2e3fa-249">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="2e3fa-249">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)

