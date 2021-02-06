---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: d07942797bad3666a263e017fa8372e672936041
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603815"
---
# <span data-ttu-id="ff60d-102">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ff60d-102">New-PSSessionOption</span></span>

## <span data-ttu-id="ff60d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="ff60d-103">SYNOPSIS</span></span>
<span data-ttu-id="ff60d-104">创建一个包含 PSSession 高级选项的对象。</span><span class="sxs-lookup"><span data-stu-id="ff60d-104">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="ff60d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff60d-105">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="ff60d-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ff60d-106">DESCRIPTION</span></span>

<span data-ttu-id="ff60d-107">`New-PSSessionOption`Cmdlet 将创建一个对象，该对象包含用户托管会话 (**PSSession**) 的高级选项。</span><span class="sxs-lookup"><span data-stu-id="ff60d-107">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session (**PSSession**).</span></span> <span data-ttu-id="ff60d-108">可以使用对象作为创建 **PSSession** 的 Cmdlet 的 **SessionOption** 参数的值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-108">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession**, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="ff60d-109">如果没有参数， `New-PSSessionOption` 则将生成一个对象，该对象包含所有选项的默认值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-109">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="ff60d-110">由于所有属性都是可编辑的，因此你可以将生成的对象用作模板，并为你的企业创建标准选项对象。</span><span class="sxs-lookup"><span data-stu-id="ff60d-110">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="ff60d-111">你还可以将会话选项对象保存在 `$PSSessionOption` 首选项变量中。</span><span class="sxs-lookup"><span data-stu-id="ff60d-111">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="ff60d-112">会话选项的新的默认值由此变量的值建立。</span><span class="sxs-lookup"><span data-stu-id="ff60d-112">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="ff60d-113">在未为该会话设置会话选项时它们是有效的，并且优先于在会话配置中设置的选项，但可以通过在创建会话的 cmdlet 中指定会话选项或会话选项对象来替代它们。</span><span class="sxs-lookup"><span data-stu-id="ff60d-113">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="ff60d-114">有关 `$PSSessionOption` 首选项变量的详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-114">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="ff60d-115">当你在创建会话的 cmdlet 中使用会话选项对象时，会话选项值将优先于在 $PSSessionOption 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-115">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="ff60d-116">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="ff60d-116">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="ff60d-117">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="ff60d-118">示例</span><span class="sxs-lookup"><span data-stu-id="ff60d-118">EXAMPLES</span></span>

### <span data-ttu-id="ff60d-119">示例1：创建默认会话选项</span><span class="sxs-lookup"><span data-stu-id="ff60d-119">Example 1: Create a default session option</span></span>

<span data-ttu-id="ff60d-120">此命令创建具有所有默认值的会话选项对象。</span><span class="sxs-lookup"><span data-stu-id="ff60d-120">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="ff60d-121">示例2：使用会话选项对象配置会话</span><span class="sxs-lookup"><span data-stu-id="ff60d-121">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="ff60d-122">此示例显示了如何使用会话选项对象来配置会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-122">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="ff60d-123">第一个命令创建一个新的会话选项对象，并将其保存在变量的值中 `$pso` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-123">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="ff60d-124">第二个命令使用 `New-PSSession` cmdlet 在 Server01 远程计算机上创建会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-124">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="ff60d-125">该命令使用变量值中的 session 选项对象 `$pso` 作为命令的 **SessionOption** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-125">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="ff60d-126">示例3：启动交互式会话</span><span class="sxs-lookup"><span data-stu-id="ff60d-126">Example 3: Start an interactive session</span></span>

<span data-ttu-id="ff60d-127">此命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-127">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="ff60d-128">**SessionOption** 参数的值是一个 `New-PSSessionOption` 包含 **NoEncryption** 和 **NoCompression** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="ff60d-128">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="ff60d-129">`New-PSSessionOption`命令括在括号中，以确保它在命令之前运行 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-129">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="ff60d-130">示例4：修改会话选项对象</span><span class="sxs-lookup"><span data-stu-id="ff60d-130">Example 4: Modify a session option object</span></span>

<span data-ttu-id="ff60d-131">此示例演示您可以修改 session 选项对象。</span><span class="sxs-lookup"><span data-stu-id="ff60d-131">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="ff60d-132">所有属性都具有读/写值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-132">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="ff60d-133">使用此方法为你的企业创建标准会话对象，然后针对特定用途创建该对象的自定义版本。</span><span class="sxs-lookup"><span data-stu-id="ff60d-133">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="ff60d-134">示例5：创建首选项变量</span><span class="sxs-lookup"><span data-stu-id="ff60d-134">Example 5: Create a preference variable</span></span>

<span data-ttu-id="ff60d-135">此命令创建一个 `$PSSessionOption` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="ff60d-135">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="ff60d-136">如果 `$PSSessionOption` 会话中出现首选项变量，它将使用 `New-PSSession` 、 `Enter-PSSession` 和 cmdlet 为创建的会话中的选项建立默认值 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-136">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="ff60d-137">若要使 `$PSSessionOption` 变量在所有会话中都可用，请将其添加到 powershell 会话和 powershell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="ff60d-137">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="ff60d-138">有关 `$PSSessionOption` 首选项变量的详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-138">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="ff60d-139">有关配置文件的详细信息，请参阅 [about_Profiles](About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-139">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="ff60d-140">示例6：满足远程会话配置的要求</span><span class="sxs-lookup"><span data-stu-id="ff60d-140">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="ff60d-141">此示例显示了如何使用 **SessionOption** 对象来满足远程会话配置的要求。</span><span class="sxs-lookup"><span data-stu-id="ff60d-141">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="ff60d-142">第一个命令使用 `New-PSSessionOption` cmdlet 创建具有 **SkipCNCheck** 属性的会话选项对象。</span><span class="sxs-lookup"><span data-stu-id="ff60d-142">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="ff60d-143">该命令将生成的会话对象保存在 `$skipCN` 变量中。</span><span class="sxs-lookup"><span data-stu-id="ff60d-143">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="ff60d-144">第二个命令使用 `New-PSSession` cmdlet 在远程计算机上创建新会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-144">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="ff60d-145">`$skipCN`Check 变量用于 **SessionOption** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-145">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="ff60d-146">由于计算机通过其 IP 地址进行标识， **ComputerName** 参数的值与用于安全套接字层 (SSL) 的证书中的任何公用名都不匹配。</span><span class="sxs-lookup"><span data-stu-id="ff60d-146">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="ff60d-147">因此，**SkipCNCheck** 选项是必需的。</span><span class="sxs-lookup"><span data-stu-id="ff60d-147">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="ff60d-148">示例7：使参数可用于远程会话</span><span class="sxs-lookup"><span data-stu-id="ff60d-148">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="ff60d-149">此示例演示如何使用 cmdlet 的 **ApplicationArguments** 参数 `New-PSSessionOption` 向远程会话提供其他数据。</span><span class="sxs-lookup"><span data-stu-id="ff60d-149">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="ff60d-150">第一个命令创建一个哈希表，其中包含两个键： " **团队** " 和 " **使用**"。</span><span class="sxs-lookup"><span data-stu-id="ff60d-150">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="ff60d-151">该命令将哈希表保存在 `$team` 变量中。</span><span class="sxs-lookup"><span data-stu-id="ff60d-151">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="ff60d-152">有关哈希表的详细信息，请参阅 [about_Hash_Tables](about/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-152">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="ff60d-153">接下来， `New-PSSessionOption` 使用 **ApplicationArguments** 参数创建一个保存在变量中的会话选项对象 `$team` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-153">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="ff60d-154">当 `New-PSSessionOption` 创建会话选项对象时，它会自动将 **ApplicationArguments** 参数值中的哈希表转换为基元字典，以便可以将数据可靠地传输到远程会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-154">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="ff60d-155">`New-PSSession`Cmdlet 在 Server01 计算机上启动一个会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-155">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="ff60d-156">它使用 **SessionOption** 参数来包括变量中的选项 `$teamOption` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-156">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="ff60d-157">`Invoke-Command`Cmdlet 说明变量中的数据 `$team` 可用于远程会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="ff60d-157">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="ff60d-158">数据显示在自动变量的 **ApplicationArguments** 属性中 `$PSSenderInfo` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-158">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="ff60d-159">最后 `Invoke-Command` 显示了如何使用数据。</span><span class="sxs-lookup"><span data-stu-id="ff60d-159">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="ff60d-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff60d-160">PARAMETERS</span></span>

### <span data-ttu-id="ff60d-161">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="ff60d-161">-ApplicationArguments</span></span>

<span data-ttu-id="ff60d-162">指定将发送到远程会话的基元字典。</span><span class="sxs-lookup"><span data-stu-id="ff60d-162">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="ff60d-163">远程会话中的命令和脚本（包括会话配置中的启动脚本）可以在自动变量的 **ApplicationArguments** 属性中找到此字典 `$PSSenderInfo` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-163">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="ff60d-164">你可以使用此参数来将数据发送到远程会话。</span><span class="sxs-lookup"><span data-stu-id="ff60d-164">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="ff60d-165">有关详细信息，请参阅 [about_Hash_Tables](about/about_Hash_Tables.md)、 [about_Session_Configurations](About/about_Session_Configurations.md)和 [about_Automatic_Variables](about/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-165">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-166">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="ff60d-166">-CancelTimeout</span></span>

<span data-ttu-id="ff60d-167">确定 PowerShell 等待取消操作 (按 CTRL + C) 完成多长时间后才结束。</span><span class="sxs-lookup"><span data-stu-id="ff60d-167">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="ff60d-168">输入一个值（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-168">Enter a value in milliseconds.</span></span>

<span data-ttu-id="ff60d-169">默认值为 60000（1 分钟）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-169">The default value is 60000 (one minute).</span></span> <span data-ttu-id="ff60d-170">值为 0（零）表示无超时；该命令会无限期地继续运行。</span><span class="sxs-lookup"><span data-stu-id="ff60d-170">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-171">-Culture</span><span class="sxs-lookup"><span data-stu-id="ff60d-171">-Culture</span></span>

<span data-ttu-id="ff60d-172">指定要用于会话的区域性。</span><span class="sxs-lookup"><span data-stu-id="ff60d-172">Specifies the culture to use for the session.</span></span> <span data-ttu-id="ff60d-173">在 `<languagecode2>-<country/regioncode2>` 格式 (如 `ja-JP`) 、包含 **cultureinfo** 对象的变量或获取 **CultureInfo** 对象的命令中输入区域性名称。</span><span class="sxs-lookup"><span data-stu-id="ff60d-173">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="ff60d-174">默认值为 `$Null` ，并且在该会话中使用在操作系统中设置的区域性。</span><span class="sxs-lookup"><span data-stu-id="ff60d-174">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-175">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="ff60d-175">-IdleTimeout</span></span>

<span data-ttu-id="ff60d-176">确定当远程计算机没有从本地计算机接收任何通信时，会话保持打开状态的时间。</span><span class="sxs-lookup"><span data-stu-id="ff60d-176">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="ff60d-177">这包括检测信号信号。</span><span class="sxs-lookup"><span data-stu-id="ff60d-177">This includes the heartbeat signal.</span></span> <span data-ttu-id="ff60d-178">当时间间隔已过时，该会话将关闭。</span><span class="sxs-lookup"><span data-stu-id="ff60d-178">When the interval expires, the session closes.</span></span>

<span data-ttu-id="ff60d-179">如果打算断开连接并重新连接到会话，则空闲超时值非常重要。</span><span class="sxs-lookup"><span data-stu-id="ff60d-179">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="ff60d-180">仅当该会话未超时时，才可以重新连接。</span><span class="sxs-lookup"><span data-stu-id="ff60d-180">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="ff60d-181">输入一个值（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-181">Enter a value in milliseconds.</span></span> <span data-ttu-id="ff60d-182">最小值为 60000（1 分钟）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-182">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="ff60d-183">最大值为会话配置的 **MaxIdleTimeoutms** 属性值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-183">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="ff60d-184">默认值-1 未设置空闲超时。</span><span class="sxs-lookup"><span data-stu-id="ff60d-184">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="ff60d-185">会话使用在会话选项中设置的空闲超时（如果有）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-185">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="ff60d-186">如果未设置 (-1) ，则会话将使用会话配置的 **IdleTimeoutMs** 属性的值或 WSMan shell 超时值 (`WSMan:\<ComputerName>\Shell\IdleTimeout`) ，取最短时间。</span><span class="sxs-lookup"><span data-stu-id="ff60d-186">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="ff60d-187">如果在会话选项中设置的空闲超时超出会话配置的 **MaxIdleTimeoutMs** 属性值，则用于创建会话的命令将失败。</span><span class="sxs-lookup"><span data-stu-id="ff60d-187">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="ff60d-188">**默认的** IdleTimeoutMs 会话配置的值为7200000毫秒 (2 小时) 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-188">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="ff60d-189">其 **MaxIdleTimeoutMs** 值为2147483647毫秒 (\> 24 天) 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-189">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="ff60d-190">WSMan shell 空闲超时 () 的默认值 `WSMan:\<ComputerName>\Shell\IdleTimeout` 为7200000毫秒， (2) 小时。</span><span class="sxs-lookup"><span data-stu-id="ff60d-190">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="ff60d-191">从会话断开连接或重新连接到会话时，还可以更改会话的空闲超时值。</span><span class="sxs-lookup"><span data-stu-id="ff60d-191">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="ff60d-192">有关详细信息，请参阅 `Disconnect-PSSession` 和 `Connect-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="ff60d-192">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="ff60d-193">在 Windows PowerShell 2.0 中，**IdleTimeout** 参数的默认值为 240000（4 分钟）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-193">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-194">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="ff60d-194">-IncludePortInSPN</span></span>

<span data-ttu-id="ff60d-195">将端口号包含在用于 Kerberos 身份验证的服务主体名称 (SPN) ，例如， `HTTP://<ComputerName>:5985` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-195">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="ff60d-196">此选项允许客户端使用非默认 SPN 对使用 Kerberos 身份验证的远程计算机进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ff60d-196">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="ff60d-197">该选项旨在用于为在不同的用户帐户下运行的支持 Kerberos 身份验证的多个服务的企业。</span><span class="sxs-lookup"><span data-stu-id="ff60d-197">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="ff60d-198">例如，允许 Kerberos 身份验证的 IIS 应用程序可能需要将默认 SPN 注册到不同于计算机帐户的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="ff60d-198">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="ff60d-199">在这种情况下，PowerShell 远程处理无法使用 Kerberos 进行身份验证，因为它需要一个已注册到计算机帐户的 SPN。</span><span class="sxs-lookup"><span data-stu-id="ff60d-199">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="ff60d-200">若要解决此问题，管理员可以创建不同的 Spn，例如通过使用 **Setspn.exe** 注册到不同用户帐户，并且可以通过将端口号包含在 SPN 中来区分它们。</span><span class="sxs-lookup"><span data-stu-id="ff60d-200">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe**, that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="ff60d-201">有关详细信息，请参阅 [Setspn 概述](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="ff60d-201">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="ff60d-202">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-203">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="ff60d-203">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="ff60d-204">指定在当前尝试因网络问题而失败时，PowerShell 尝试连接到目标计算机的次数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-204">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="ff60d-205">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="ff60d-205">The default value is 5.</span></span>

<span data-ttu-id="ff60d-206">为 PowerShell 版本5.0 添加了此参数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-206">This parameter was added for PowerShell version 5.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-207">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="ff60d-207">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="ff60d-208">指定本地计算机在单个命令中可从远程计算机接收到的最大字节数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-208">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="ff60d-209">输入一个值（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-209">Enter a value in bytes.</span></span> <span data-ttu-id="ff60d-210">默认情况下，没有数据大小限制。</span><span class="sxs-lookup"><span data-stu-id="ff60d-210">By default, there is no data size limit.</span></span>

<span data-ttu-id="ff60d-211">此选项专门用于保护客户端计算机上的资源。</span><span class="sxs-lookup"><span data-stu-id="ff60d-211">This option is designed to protect the resources on the client computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-212">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="ff60d-212">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="ff60d-213">指定本地计算机可从远程计算机接收到的最大对象大小。</span><span class="sxs-lookup"><span data-stu-id="ff60d-213">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="ff60d-214">此选项专门用于保护客户端计算机上的资源。</span><span class="sxs-lookup"><span data-stu-id="ff60d-214">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="ff60d-215">输入一个值（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-215">Enter a value in bytes.</span></span>

<span data-ttu-id="ff60d-216">在 Windows PowerShell 2.0 中，如果省略此参数，则没有对象大小限制。</span><span class="sxs-lookup"><span data-stu-id="ff60d-216">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="ff60d-217">从 Windows PowerShell 3.0 开始，如果省略此参数，则默认值为 200 MB。</span><span class="sxs-lookup"><span data-stu-id="ff60d-217">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-218">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="ff60d-218">-MaximumRedirection</span></span>

<span data-ttu-id="ff60d-219">确定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-219">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="ff60d-220">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="ff60d-220">The default value is 5.</span></span> <span data-ttu-id="ff60d-221">值为 0（零）将阻止所有重定向。</span><span class="sxs-lookup"><span data-stu-id="ff60d-221">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="ff60d-222">仅当在创建会话的命令中使用 **AllowRedirection** 参数时，才会在会话中使用此选项。</span><span class="sxs-lookup"><span data-stu-id="ff60d-222">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-223">-NoCompression</span><span class="sxs-lookup"><span data-stu-id="ff60d-223">-NoCompression</span></span>

<span data-ttu-id="ff60d-224">关闭会话中的数据包压缩。</span><span class="sxs-lookup"><span data-stu-id="ff60d-224">Turns off packet compression in the session.</span></span> <span data-ttu-id="ff60d-225">压缩会占用更多的处理器周期，但可以提高传输速度。</span><span class="sxs-lookup"><span data-stu-id="ff60d-225">Compression uses more processor cycles, but it makes transmission faster.</span></span>

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

### <span data-ttu-id="ff60d-226">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="ff60d-226">-NoEncryption</span></span>

<span data-ttu-id="ff60d-227">关闭数据加密。</span><span class="sxs-lookup"><span data-stu-id="ff60d-227">Turns off data encryption.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-228">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="ff60d-228">-NoMachineProfile</span></span>

<span data-ttu-id="ff60d-229">阻止加载用户的 Windows 用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="ff60d-229">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="ff60d-230">这样做可以加快创建会话的速度，但不能在该会话使用特定于用户的注册表设置、环境变量等项以及证书。</span><span class="sxs-lookup"><span data-stu-id="ff60d-230">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

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

### <span data-ttu-id="ff60d-231">-OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="ff60d-231">-OpenTimeout</span></span>

<span data-ttu-id="ff60d-232">确定客户端计算机等待建立会话连接的时长。</span><span class="sxs-lookup"><span data-stu-id="ff60d-232">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="ff60d-233">当时间间隔到期时，用于建立该连接的命令将失败。</span><span class="sxs-lookup"><span data-stu-id="ff60d-233">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="ff60d-234">输入一个值（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-234">Enter a value in milliseconds.</span></span>

<span data-ttu-id="ff60d-235">默认值为 180000（3 分钟）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-235">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="ff60d-236">值为 0（零）表示无超时；该命令会无限期地继续运行。</span><span class="sxs-lookup"><span data-stu-id="ff60d-236">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-237">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="ff60d-237">-OperationTimeout</span></span>

<span data-ttu-id="ff60d-238">确定任一操作可在会话中运行的最长时间。</span><span class="sxs-lookup"><span data-stu-id="ff60d-238">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="ff60d-239">当时间间隔到期时，该操作将失败。</span><span class="sxs-lookup"><span data-stu-id="ff60d-239">When the interval expires, the operation fails.</span></span> <span data-ttu-id="ff60d-240">输入一个值（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-240">Enter a value in milliseconds.</span></span>

<span data-ttu-id="ff60d-241">默认值为 180000（3 分钟）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-241">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="ff60d-242">值为 0（零）表示无超时；该操作会无限期地继续运行。</span><span class="sxs-lookup"><span data-stu-id="ff60d-242">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-243">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="ff60d-243">-OutputBufferingMode</span></span>

<span data-ttu-id="ff60d-244">当输出缓冲区时已满时，确定如何在断开连接的会话中管理命令输出。</span><span class="sxs-lookup"><span data-stu-id="ff60d-244">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="ff60d-245">如果未在会话或会话配置中设置输出缓冲模式，则默认值为 **Block**。</span><span class="sxs-lookup"><span data-stu-id="ff60d-245">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="ff60d-246">用户还可以在断开会话连接时更改输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="ff60d-246">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="ff60d-247">如果省略此参数，则会话选项对象的 **OutputBufferingMode** 的值为 None。</span><span class="sxs-lookup"><span data-stu-id="ff60d-247">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="ff60d-248">值为 **Block** 或 **Drop** 会覆盖在会话配置中设置的输出缓冲模式传输选项。</span><span class="sxs-lookup"><span data-stu-id="ff60d-248">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="ff60d-249">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="ff60d-249">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ff60d-250">阻止。</span><span class="sxs-lookup"><span data-stu-id="ff60d-250">Block.</span></span> <span data-ttu-id="ff60d-251">当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ff60d-251">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="ff60d-252">删除。</span><span class="sxs-lookup"><span data-stu-id="ff60d-252">Drop.</span></span> <span data-ttu-id="ff60d-253">当输出缓冲区已满时，执行将继续。</span><span class="sxs-lookup"><span data-stu-id="ff60d-253">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="ff60d-254">由于已保存新的输出，因此将丢弃最早的输出。</span><span class="sxs-lookup"><span data-stu-id="ff60d-254">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="ff60d-255">无。</span><span class="sxs-lookup"><span data-stu-id="ff60d-255">None.</span></span> <span data-ttu-id="ff60d-256">未指定任何输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="ff60d-256">No output buffering mode is specified.</span></span>

<span data-ttu-id="ff60d-257">有关输出缓冲模式传输选项的详细信息，请参阅 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-257">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="ff60d-258">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="ff60d-258">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-259">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="ff60d-259">-ProxyAccessType</span></span>

<span data-ttu-id="ff60d-260">确定用于解析主机名的机制。</span><span class="sxs-lookup"><span data-stu-id="ff60d-260">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="ff60d-261">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="ff60d-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ff60d-262">IEConfig</span><span class="sxs-lookup"><span data-stu-id="ff60d-262">IEConfig</span></span>
- <span data-ttu-id="ff60d-263">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="ff60d-263">WinHttpConfig</span></span>
- <span data-ttu-id="ff60d-264">AutoDetect</span><span class="sxs-lookup"><span data-stu-id="ff60d-264">AutoDetect</span></span>
- <span data-ttu-id="ff60d-265">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="ff60d-265">NoProxyServer</span></span>
- <span data-ttu-id="ff60d-266">无</span><span class="sxs-lookup"><span data-stu-id="ff60d-266">None</span></span>

<span data-ttu-id="ff60d-267">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="ff60d-267">The default value is None.</span></span>

<span data-ttu-id="ff60d-268">有关此参数的值的信息，请参阅 [对 system.management.automation.remoting.proxyaccesstype 枚举](/dotnet/api/system.management.automation.remoting.proxyaccesstype)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-268">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-269">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="ff60d-269">-ProxyAuthentication</span></span>

<span data-ttu-id="ff60d-270">指定用于代理解析的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="ff60d-270">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="ff60d-271">此参数可接受的值为： " **基本**"、" **摘要**" 和 " **协商**"。</span><span class="sxs-lookup"><span data-stu-id="ff60d-271">The acceptable values for this parameter are: **Basic**, **Digest**, and **Negotiate**.</span></span> <span data-ttu-id="ff60d-272">默认值为 " **协商**"。</span><span class="sxs-lookup"><span data-stu-id="ff60d-272">The default value is **Negotiate**.</span></span>

<span data-ttu-id="ff60d-273">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-273">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-274">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ff60d-274">-ProxyCredential</span></span>

<span data-ttu-id="ff60d-275">指定用于代理身份验证的凭据。</span><span class="sxs-lookup"><span data-stu-id="ff60d-275">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="ff60d-276">输入包含 **pscredential** 对象的变量或获取 **pscredential** 对象的命令（如 `Get-Credential` 命令）。</span><span class="sxs-lookup"><span data-stu-id="ff60d-276">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="ff60d-277">如果未设置此选项，则不指定任何凭据。</span><span class="sxs-lookup"><span data-stu-id="ff60d-277">If this option is not set, no credentials are specified.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-278">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="ff60d-278">-SkipCACheck</span></span>

<span data-ttu-id="ff60d-279">指定当通过 HTTPS 进行连接时，客户端不会验证服务器证书是否由受信任的证书颁发机构签名 (CA) 。</span><span class="sxs-lookup"><span data-stu-id="ff60d-279">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="ff60d-280">仅当远程计算机通过其他机制受信任（例如远程计算机所属的网络在物理上是安全的并已隔离，或者远程计算机在 WinRM 配置中列为受信任主机）时才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="ff60d-280">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

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

### <span data-ttu-id="ff60d-281">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="ff60d-281">-SkipCNCheck</span></span>

<span data-ttu-id="ff60d-282">指定服务器的证书公用名 (CN) 不必与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="ff60d-282">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="ff60d-283">仅在使用 HTTPS 协议的远程操作中使用此选项。</span><span class="sxs-lookup"><span data-stu-id="ff60d-283">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="ff60d-284">仅将此选项用于受信任的计算机。</span><span class="sxs-lookup"><span data-stu-id="ff60d-284">Use this option only for trusted computers.</span></span>

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

### <span data-ttu-id="ff60d-285">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="ff60d-285">-SkipRevocationCheck</span></span>

<span data-ttu-id="ff60d-286">不验证服务器证书的吊销状态。</span><span class="sxs-lookup"><span data-stu-id="ff60d-286">Does not validate the revocation status of the server certificate.</span></span>

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

### <span data-ttu-id="ff60d-287">-UICulture</span><span class="sxs-lookup"><span data-stu-id="ff60d-287">-UICulture</span></span>

<span data-ttu-id="ff60d-288">指定用于会话的 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="ff60d-288">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="ff60d-289">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="ff60d-289">Valid values include:</span></span>

- <span data-ttu-id="ff60d-290">格式的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="ff60d-290">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="ff60d-291">包含 **CultureInfo** 对象的变量</span><span class="sxs-lookup"><span data-stu-id="ff60d-291">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="ff60d-292">用于获取 **CultureInfo** 对象的命令，例如 `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="ff60d-292">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="ff60d-293">默认值为 `$null` ，在会话中使用在创建会话时在操作系统中设置的 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="ff60d-293">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-294">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="ff60d-294">-UseUTF16</span></span>

<span data-ttu-id="ff60d-295">指示此 cmdlet 以 UTF16 格式而不是 UTF8 格式对请求进行编码。</span><span class="sxs-lookup"><span data-stu-id="ff60d-295">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff60d-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff60d-296">CommonParameters</span></span>

<span data-ttu-id="ff60d-297">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ff60d-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff60d-298">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff60d-299">输入</span><span class="sxs-lookup"><span data-stu-id="ff60d-299">INPUTS</span></span>

### <span data-ttu-id="ff60d-300">无</span><span class="sxs-lookup"><span data-stu-id="ff60d-300">None</span></span>

<span data-ttu-id="ff60d-301">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff60d-301">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ff60d-302">输出</span><span class="sxs-lookup"><span data-stu-id="ff60d-302">OUTPUTS</span></span>

### <span data-ttu-id="ff60d-303">"PSSessionOption"。</span><span class="sxs-lookup"><span data-stu-id="ff60d-303">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="ff60d-304">注释</span><span class="sxs-lookup"><span data-stu-id="ff60d-304">NOTES</span></span>

<span data-ttu-id="ff60d-305">如果在命令中未使用 **SessionOption** 参数来创建 **PSSession**，则会话选项由首选项变量的属性值 `$PSSessionOption` （如果已设置）确定。</span><span class="sxs-lookup"><span data-stu-id="ff60d-305">If the **SessionOption** parameter is not used in a command to create a **PSSession**, the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="ff60d-306">有关变量的详细信息 `$PSSessionOption` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ff60d-306">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="ff60d-307">会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ff60d-307">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="ff60d-308">此外，使用会话配置文件的会话配置还具有其他属性。</span><span class="sxs-lookup"><span data-stu-id="ff60d-308">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="ff60d-309">相关链接</span><span class="sxs-lookup"><span data-stu-id="ff60d-309">RELATED LINKS</span></span>

[<span data-ttu-id="ff60d-310">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="ff60d-310">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="ff60d-311">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ff60d-311">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="ff60d-312">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ff60d-312">New-PSSession</span></span>](New-PSSession.md)
