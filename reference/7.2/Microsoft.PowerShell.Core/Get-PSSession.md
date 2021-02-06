---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: e06eaaa3b6042a2105462adfc2ba8f0a4867f045
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595393"
---
# <span data-ttu-id="504fe-102">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-102">Get-PSSession</span></span>

## <span data-ttu-id="504fe-103">摘要</span><span class="sxs-lookup"><span data-stu-id="504fe-103">SYNOPSIS</span></span>
<span data-ttu-id="504fe-104">获取本地和远程计算机上的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-104">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="504fe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="504fe-105">SYNTAX</span></span>

### <span data-ttu-id="504fe-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="504fe-106">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-107">计算机名</span><span class="sxs-lookup"><span data-stu-id="504fe-107">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-108">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-108">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-109">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="504fe-109">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-110">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-110">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-111">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-111">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="504fe-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="504fe-112">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="504fe-113">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-113">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="504fe-114">VMId</span><span class="sxs-lookup"><span data-stu-id="504fe-114">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="504fe-115">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-115">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="504fe-116">VMName</span><span class="sxs-lookup"><span data-stu-id="504fe-116">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="504fe-117">InstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-117">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="504fe-118">ID</span><span class="sxs-lookup"><span data-stu-id="504fe-118">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="504fe-119">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="504fe-119">DESCRIPTION</span></span>

<span data-ttu-id="504fe-120">该 `Get-PSSession` cmdlet 将获取本地和远程计算机上的用户管理的 PowerShell 会话 (**pssession**) 。</span><span class="sxs-lookup"><span data-stu-id="504fe-120">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions (**PSSessions**) on local and remote computers.</span></span>

<span data-ttu-id="504fe-121">从 Windows PowerShell 3.0 开始，会话将存储在每个连接远端的计算机上。</span><span class="sxs-lookup"><span data-stu-id="504fe-121">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="504fe-122">您可以使用的 **ComputerName** 或 **ConnectionUri** 参数 `Get-PSSession` 来获取连接到本地计算机或远程计算机的会话，即使它们不是在当前会话中创建的。</span><span class="sxs-lookup"><span data-stu-id="504fe-122">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="504fe-123">如果没有参数， `Get-PSSession` 则将获取在当前会话中创建的所有会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-123">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="504fe-124">使用筛选参数，包括 **名称**、 **ID**、 **InstanceID**、 **State**、 **ApplicationName** 和 **ConfigurationName** 从返回的会话中进行选择 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-124">Use the filtering parameters, including **Name**, **ID**, **InstanceID**, **State**, **ApplicationName**, and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="504fe-125">使用剩余的参数配置在 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数时运行命令的临时连接。</span><span class="sxs-lookup"><span data-stu-id="504fe-125">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="504fe-126">注意：在不带参数的 Windows PowerShell 2.0 中， `Get-PSSession` 将获取在当前会话中创建的所有会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-126">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="504fe-127">**ComputerName** 参数获取在当前会话中创建并连接到指定计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-127">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="504fe-128">有关 PowerShell 会话的详细信息，请参阅 [about_PSSessions](about/about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="504fe-128">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="504fe-129">示例</span><span class="sxs-lookup"><span data-stu-id="504fe-129">EXAMPLES</span></span>

### <span data-ttu-id="504fe-130">示例1：获取在当前会话中创建的会话</span><span class="sxs-lookup"><span data-stu-id="504fe-130">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="504fe-131">此命令将获取在当前会话中创建的所有 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-131">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="504fe-132">即使它们连接到此计算机，它也不会获取在其他会话或其他计算机上创建的 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-132">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="504fe-133">示例2：获取连接到本地计算机的会话</span><span class="sxs-lookup"><span data-stu-id="504fe-133">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="504fe-134">此命令获取连接到本地计算机的 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-134">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="504fe-135">若要指示本地计算机，请键入计算机名称、localhost 或点 (。 ) </span><span class="sxs-lookup"><span data-stu-id="504fe-135">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="504fe-136">此命令返回本地计算机上的所有会话，即使它们是在不同会话中或不同计算机上创建的，也是如此。</span><span class="sxs-lookup"><span data-stu-id="504fe-136">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="504fe-137">示例3：获取连接到计算机的会话</span><span class="sxs-lookup"><span data-stu-id="504fe-137">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="504fe-138">此命令获取连接到 Server02 计算机的 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-138">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="504fe-139">此命令返回 Server02 上的所有会话，即使它们是在不同会话中或不同计算机上创建的，也是如此。</span><span class="sxs-lookup"><span data-stu-id="504fe-139">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="504fe-140">此输出显示了两个具有 Disconnected 状态的会话，这些会话的可用性为 Busy。</span><span class="sxs-lookup"><span data-stu-id="504fe-140">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="504fe-141">它们是在不同的会话中创建的，并且当前正在使用它们。</span><span class="sxs-lookup"><span data-stu-id="504fe-141">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="504fe-142">在当前会话中创建了已打开且可用的 ScheduledJobs 会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-142">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="504fe-143">示例4：保存此命令的结果</span><span class="sxs-lookup"><span data-stu-id="504fe-143">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="504fe-144">此示例演示如何将命令的结果保存 `Get-PSSession` 在多个变量中。</span><span class="sxs-lookup"><span data-stu-id="504fe-144">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="504fe-145">第一个命令使用 `New-PSSession` cmdlet 在三台远程计算机上创建 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-145">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="504fe-146">第二个命令使用 `Get-PSSession` cmdlet 来获取三个 **pssession**。</span><span class="sxs-lookup"><span data-stu-id="504fe-146">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions**.</span></span> <span data-ttu-id="504fe-147">然后，它将每个 **pssession** 保存在一个单独的变量中。</span><span class="sxs-lookup"><span data-stu-id="504fe-147">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="504fe-148">当 PowerShell 将对象数组分配给变量数组时，它会将第一个对象分配给第一个变量，将第二个对象分配给第二个变量，依此类推。</span><span class="sxs-lookup"><span data-stu-id="504fe-148">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="504fe-149">如果对象多于变量，则会将数组中所有剩余的对象都分配给最后一个变量。</span><span class="sxs-lookup"><span data-stu-id="504fe-149">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="504fe-150">如果变量多于对象，则弃用额外的变量。</span><span class="sxs-lookup"><span data-stu-id="504fe-150">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="504fe-151">示例5：使用实例 ID 删除会话</span><span class="sxs-lookup"><span data-stu-id="504fe-151">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="504fe-152">此示例演示如何通过使用其实例 ID 获取 **pssession** ，然后再删除 **pssession**。</span><span class="sxs-lookup"><span data-stu-id="504fe-152">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession**.</span></span>

<span data-ttu-id="504fe-153">第一个命令获取在当前会话中创建的所有 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-153">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="504fe-154">它将 **pssession** 发送到 Format-Table cmdlet，后者将显示每个 **PSSession** 的 **ComputerName** 和 **InstanceID** 属性。</span><span class="sxs-lookup"><span data-stu-id="504fe-154">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession**.</span></span>

<span data-ttu-id="504fe-155">第二个命令使用 `Get-PSSession` cmdlet 来获取特定的 **PSSession** ，并将其保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="504fe-155">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="504fe-156">该命令使用 **InstanceID** 参数来标识 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="504fe-156">The command uses the **InstanceID** parameter to identify the **PSSession**.</span></span>

<span data-ttu-id="504fe-157">第三个命令使用 Remove-PSSession cmdlet 删除变量中的 **PSSession** `$s` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-157">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="504fe-158">示例6：获取具有特定名称的会话</span><span class="sxs-lookup"><span data-stu-id="504fe-158">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="504fe-159">此示例中的命令将查找具有特定名称格式且使用特定会话配置的会话，然后将连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-159">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="504fe-160">你可以使用此类命令来查找同事在其中启动任务的会话，然后连接该会话以完成该任务。</span><span class="sxs-lookup"><span data-stu-id="504fe-160">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="504fe-161">第一个命令获取名称以 BackupJob 开头并使用 ITTasks 会话配置的 Server02 和 Server12 远程计算机上的会话。该命令使用 **name** 参数来指定名称模式，并使用 **ConfigurationName** 参数来指定会话配置。</span><span class="sxs-lookup"><span data-stu-id="504fe-161">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="504fe-162">**SessionOption** 参数值是一个哈希表，可将 **OperationTimeout** 值设置为 240000 毫秒（4 分钟）。</span><span class="sxs-lookup"><span data-stu-id="504fe-162">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="504fe-163">此设置提供了更多的时间来完成命令。 **ConfigurationName** 和 **SessionOption** 参数用于配置在 `Get-PSSession` 每台计算机上运行 cmdlet 的临时会话。输出显示该命令返回 BackupJob04 会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-163">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="504fe-164">会话已断开连接，并且 **可用性** 为 "无"，这表示未在使用。</span><span class="sxs-lookup"><span data-stu-id="504fe-164">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="504fe-165">第二个命令使用 `Get-PSSession` cmdlet 来访问 BackupJob04 会话，并使用 Connect-PSSession cmdlet 连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-165">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="504fe-166">该命令将该会话保存在 $s 变量中。</span><span class="sxs-lookup"><span data-stu-id="504fe-166">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="504fe-167">第三个命令获取 $s 变量中的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-167">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="504fe-168">输出显示该 `Connect-PSSession` 命令已成功。</span><span class="sxs-lookup"><span data-stu-id="504fe-168">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="504fe-169">此会话处于 **Opened** 状态且可用。</span><span class="sxs-lookup"><span data-stu-id="504fe-169">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="504fe-170">示例7：使用 ID 获取会话</span><span class="sxs-lookup"><span data-stu-id="504fe-170">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="504fe-171">此命令获取 ID 为2的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="504fe-171">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="504fe-172">由于 **id** 属性的值仅在当前会话中是唯一的，因此 **id** 参数仅对本地命令有效。</span><span class="sxs-lookup"><span data-stu-id="504fe-172">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="504fe-173">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="504fe-173">PARAMETERS</span></span>

### <span data-ttu-id="504fe-174">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="504fe-174">-AllowRedirection</span></span>

<span data-ttu-id="504fe-175">指示此 cmdlet 允许将此连接重定向到备用统一资源标识符)  (URI。</span><span class="sxs-lookup"><span data-stu-id="504fe-175">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="504fe-176">默认情况下，PowerShell 不会重定向连接。</span><span class="sxs-lookup"><span data-stu-id="504fe-176">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="504fe-177">此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ConnectionUri** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-177">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-178">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-179">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="504fe-179">-ApplicationName</span></span>

<span data-ttu-id="504fe-180">指定应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="504fe-180">Specifies the name of an application.</span></span> <span data-ttu-id="504fe-181">此 cmdlet 仅连接到使用指定应用程序的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-181">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="504fe-182">输入连接 URI 的应用程序名称段。</span><span class="sxs-lookup"><span data-stu-id="504fe-182">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="504fe-183">例如，在以下连接 URI 中，应用程序名称为 WSMan：`http://localhost:5985/WSMAN`。</span><span class="sxs-lookup"><span data-stu-id="504fe-183">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="504fe-184">会话的应用程序名称存储在该会话的 **Runspace.ConnectionInfo.AppName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-184">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="504fe-185">此参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-185">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="504fe-186">它不会更改会话使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="504fe-186">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-187">-Authentication</span><span class="sxs-lookup"><span data-stu-id="504fe-187">-Authentication</span></span>

<span data-ttu-id="504fe-188">指定用于对运行命令的会话的凭据进行身份验证的机制 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-188">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="504fe-189">此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 或 **ConnectionUri** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-189">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-190">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="504fe-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="504fe-191">默认</span><span class="sxs-lookup"><span data-stu-id="504fe-191">Default</span></span>
- <span data-ttu-id="504fe-192">基本</span><span class="sxs-lookup"><span data-stu-id="504fe-192">Basic</span></span>
- <span data-ttu-id="504fe-193">Credssp</span><span class="sxs-lookup"><span data-stu-id="504fe-193">Credssp</span></span>
- <span data-ttu-id="504fe-194">摘要</span><span class="sxs-lookup"><span data-stu-id="504fe-194">Digest</span></span>
- <span data-ttu-id="504fe-195">Kerberos</span><span class="sxs-lookup"><span data-stu-id="504fe-195">Kerberos</span></span>
- <span data-ttu-id="504fe-196">Negotiate</span><span class="sxs-lookup"><span data-stu-id="504fe-196">Negotiate</span></span>
- <span data-ttu-id="504fe-197">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="504fe-197">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="504fe-198">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="504fe-198">The default value is Default.</span></span>

<span data-ttu-id="504fe-199">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="504fe-199">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="504fe-200">注意：在凭据安全支持提供程序 (CredSSP) 身份验证中，用户凭据传递到远程计算机中以进行验证，这种验证用于要求对多个资源（例如访问远程网络共享）进行验证的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-200">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="504fe-201">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="504fe-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="504fe-202">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="504fe-203">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-204">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="504fe-204">-CertificateThumbprint</span></span>

<span data-ttu-id="504fe-205">指定有权创建在其中运行命令的会话的用户帐户的数字公钥证书 (X509) `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-205">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="504fe-206">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="504fe-206">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="504fe-207">此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 或 **ConnectionUri** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-207">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-208">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="504fe-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="504fe-209">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="504fe-209">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="504fe-210">若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-210">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="504fe-211">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-211">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-212">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="504fe-212">-ComputerName</span></span>

<span data-ttu-id="504fe-213">指定计算机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-213">Specifies an array of names of computers.</span></span> <span data-ttu-id="504fe-214">获取连接到指定计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-214">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="504fe-215">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="504fe-215">Wildcard characters are not permitted.</span></span> <span data-ttu-id="504fe-216">没有默认值。</span><span class="sxs-lookup"><span data-stu-id="504fe-216">There is no default value.</span></span>

<span data-ttu-id="504fe-217">从 Windows PowerShell 3.0 开始， **PSSession** 对象存储在每个连接远端的计算机上。</span><span class="sxs-lookup"><span data-stu-id="504fe-217">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="504fe-218">为了获取指定计算机上的会话，PowerShell 会创建与每台计算机的临时连接并运行 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-218">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="504fe-219">键入一台或多台计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="504fe-219">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="504fe-220">若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。</span><span class="sxs-lookup"><span data-stu-id="504fe-220">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="504fe-221">注意：此参数仅从运行 Windows PowerShell 3.0 或更高版本的 PowerShell 的计算机获取会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-221">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="504fe-222">早期版本不存储会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-222">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-223">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="504fe-223">-ConfigurationName</span></span>

<span data-ttu-id="504fe-224">指定配置的名称。</span><span class="sxs-lookup"><span data-stu-id="504fe-224">Specifies the name of a configuration.</span></span> <span data-ttu-id="504fe-225">此 cmdlet 仅获取使用指定会话配置的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-225">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="504fe-226">输入会话配置的配置名称或完全限定的资源 URI。</span><span class="sxs-lookup"><span data-stu-id="504fe-226">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="504fe-227">如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-227">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="504fe-228">会话的配置名称存储在该会话的 **ConfigurationName** 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-228">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="504fe-229">此参数的值用于选择和筛选会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-229">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="504fe-230">它不会更改会话使用的会话配置。</span><span class="sxs-lookup"><span data-stu-id="504fe-230">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="504fe-231">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="504fe-231">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-232">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="504fe-232">-ConnectionUri</span></span>

<span data-ttu-id="504fe-233">指定一个 URI，该 URI 定义运行命令的临时会话的连接终结点 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-233">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="504fe-234">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="504fe-234">The URI must be fully qualified.</span></span>

<span data-ttu-id="504fe-235">此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ConnectionUri** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-235">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-236">此字符串的格式为：</span><span class="sxs-lookup"><span data-stu-id="504fe-236">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="504fe-237">默认值为： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-237">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="504fe-238">如果未指定 **ConnectionUri**，则可以使用 **UseSSL**、 **ComputerName**、 **Port** 和 **ApplicationName** 参数来指定 **ConnectionUri** 值。</span><span class="sxs-lookup"><span data-stu-id="504fe-238">If you do not specify a **ConnectionUri**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="504fe-239">URI 的 Transport 段的有效值为 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="504fe-239">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="504fe-240">如果使用 Transport 段指定连接 URI，但不指定端口，将使用以下标准端口来创建会话：80 用于 HTTP，443 用于 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="504fe-240">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="504fe-241">若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。</span><span class="sxs-lookup"><span data-stu-id="504fe-241">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="504fe-242">如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-242">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="504fe-243">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="504fe-244">此参数仅从运行 Windows PowerShell 3.0 或更高版本的 Windows PowerShell 的计算机获取会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-244">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="504fe-245">早期版本不存储会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-245">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-246">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="504fe-246">-ContainerId</span></span>

<span data-ttu-id="504fe-247">指定容器的 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-247">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="504fe-248">此 cmdlet 将启动与每个指定容器的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-248">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="504fe-249">使用 `docker ps` 命令获取容器 id 列表。</span><span class="sxs-lookup"><span data-stu-id="504fe-249">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="504fe-250">有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="504fe-250">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-251">-Credential</span><span class="sxs-lookup"><span data-stu-id="504fe-251">-Credential</span></span>

<span data-ttu-id="504fe-252">指定用户凭据。</span><span class="sxs-lookup"><span data-stu-id="504fe-252">Specifies a user credential.</span></span> <span data-ttu-id="504fe-253">此 cmdlet 将运行具有指定用户的权限的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-253">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="504fe-254">指定有权连接到远程计算机并运行命令的用户帐户 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-254">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="504fe-255">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="504fe-255">The default is the current user.</span></span>

<span data-ttu-id="504fe-256">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-256">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="504fe-257">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="504fe-257">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="504fe-258">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="504fe-258">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="504fe-259">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="504fe-259">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="504fe-260">此参数将创建的临时连接配置为 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数运行命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-260">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-261">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-262">-Id</span><span class="sxs-lookup"><span data-stu-id="504fe-262">-Id</span></span>

<span data-ttu-id="504fe-263">指定会话 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-263">Specifies an array of session IDs.</span></span> <span data-ttu-id="504fe-264">此 cmdlet 仅获取具有指定 Id 的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-264">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="504fe-265">键入一个或多个 ID（以逗号分隔），或使用范围运算符 (..) 来指定 ID 的范围。</span><span class="sxs-lookup"><span data-stu-id="504fe-265">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="504fe-266">不能将 ID 参数与 **ComputerName** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="504fe-266">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="504fe-267">ID 是一个整数，用于在当前会话中唯一标识用户托管的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-267">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="504fe-268">它比 **InstanceId** 更容易记住和键入，但它仅在当前会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="504fe-268">It is easier to remember and type than the **InstanceId**, but it is unique only within the current session.</span></span> <span data-ttu-id="504fe-269">会话 ID 存储在该会话的 ID 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-269">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-270">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="504fe-270">-InstanceId</span></span>

<span data-ttu-id="504fe-271">指定会话的实例 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-271">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="504fe-272">此 cmdlet 仅获取具有指定实例 Id 的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-272">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="504fe-273">实例 ID 是一个 GUID，用于在本地或远程计算机上唯一标识某个会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-273">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="504fe-274">即使在 PowerShell 中运行多个会话， **InstanceID** 也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="504fe-274">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="504fe-275">会话的实例 ID 存储在该会话的 **InstanceID** 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-275">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-276">-Name</span><span class="sxs-lookup"><span data-stu-id="504fe-276">-Name</span></span>

<span data-ttu-id="504fe-277">指定会话名称的数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-277">Specifies an array of session names.</span></span> <span data-ttu-id="504fe-278">此 cmdlet 仅获取具有指定友好名称的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-278">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="504fe-279">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="504fe-279">Wildcard characters are permitted.</span></span>

<span data-ttu-id="504fe-280">会话的友好名称存储在该会话的 **Name** 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-280">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="504fe-281">-Port</span><span class="sxs-lookup"><span data-stu-id="504fe-281">-Port</span></span>

<span data-ttu-id="504fe-282">指定用于运行命令的临时连接的指定网络端口 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-282">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="504fe-283">若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。</span><span class="sxs-lookup"><span data-stu-id="504fe-283">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="504fe-284">默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。</span><span class="sxs-lookup"><span data-stu-id="504fe-284">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="504fe-285">使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="504fe-285">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="504fe-286">若要配置侦听器，请在 PowerShell 提示符下键入以下两个命令：</span><span class="sxs-lookup"><span data-stu-id="504fe-286">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="504fe-287">此参数将创建的临时连接配置为 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 参数运行命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-287">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="504fe-288">除非必要，否则不要使用 **Port** 参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-288">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="504fe-289">命令中设置的 **端口** 适用于运行该命令的所有计算机或会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-289">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="504fe-290">备用端口设置可能会阻止在所有计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-290">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="504fe-291">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-292">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="504fe-292">-SessionOption</span></span>

<span data-ttu-id="504fe-293">为该会话指定高级选项。</span><span class="sxs-lookup"><span data-stu-id="504fe-293">Specifies advanced options for the session.</span></span> <span data-ttu-id="504fe-294">输入 **SessionOption** 对象（例如使用 New-PSSessionOption cmdlet 创建的对象），或输入哈希表，其中的键是会话选项名称，而值是会话选项值。</span><span class="sxs-lookup"><span data-stu-id="504fe-294">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="504fe-295">这些选项的默认值由 $PSSessionOption 首选项变量的值（如果已设置）确定。</span><span class="sxs-lookup"><span data-stu-id="504fe-295">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="504fe-296">否则，通过在会话配置中设置的选项创建默认值。</span><span class="sxs-lookup"><span data-stu-id="504fe-296">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="504fe-297">会话选项值优先于在 $PSSessionOption 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="504fe-297">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="504fe-298">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="504fe-298">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="504fe-299">有关会话选项（包括默认值）的说明，请参阅 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-299">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="504fe-300">有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="504fe-300">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="504fe-301">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="504fe-301">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-302">-State</span><span class="sxs-lookup"><span data-stu-id="504fe-302">-State</span></span>

<span data-ttu-id="504fe-303">指定会话状态。</span><span class="sxs-lookup"><span data-stu-id="504fe-303">Specifies a session state.</span></span> <span data-ttu-id="504fe-304">此 cmdlet 仅获取处于指定状态的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-304">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="504fe-305">此参数可接受的值包括：所有、打开、断开连接、已关闭和已中断。</span><span class="sxs-lookup"><span data-stu-id="504fe-305">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="504fe-306">默认值为 All。</span><span class="sxs-lookup"><span data-stu-id="504fe-306">The default value is All.</span></span>

<span data-ttu-id="504fe-307">会话状态值相对于当前会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-307">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="504fe-308">没有在当前会话中创建的会话以及没有连接到当前会话的会话的状态为 Disconnected，即使它们连接到不同的会话也是如此。</span><span class="sxs-lookup"><span data-stu-id="504fe-308">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="504fe-309">会话的状态存储在该会话的 **State** 属性中。</span><span class="sxs-lookup"><span data-stu-id="504fe-309">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="504fe-310">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-311">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="504fe-311">-ThrottleLimit</span></span>

<span data-ttu-id="504fe-312">指定可建立的并发连接的最大数量，以运行该 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-312">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="504fe-313">如果省略此参数或输入 0（零）值，则使用默认值 32。</span><span class="sxs-lookup"><span data-stu-id="504fe-313">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="504fe-314">节流限制仅适用于当前命令，而不适用于会话或计算机。</span><span class="sxs-lookup"><span data-stu-id="504fe-314">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="504fe-315">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-315">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-316">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="504fe-316">-UseSSL</span></span>

<span data-ttu-id="504fe-317">指示此 cmdlet 使用安全套接字层 (SSL) 协议来建立运行该命令的连接 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-317">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="504fe-318">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="504fe-318">By default, SSL is not used.</span></span> <span data-ttu-id="504fe-319">如果你使用此参数，但 SSL 在用于此命令的端口上不可用，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="504fe-319">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="504fe-320">此参数将创建的临时连接配置为运行 `Get-PSSession` 带有 **ComputerName** 参数的命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-320">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="504fe-321">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-322">-VMId</span><span class="sxs-lookup"><span data-stu-id="504fe-322">-VMId</span></span>

<span data-ttu-id="504fe-323">指定虚拟机的 ID 的数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-323">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="504fe-324">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-324">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="504fe-325">若要查看可供你使用的虚拟机，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="504fe-325">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-326">-VMName</span><span class="sxs-lookup"><span data-stu-id="504fe-326">-VMName</span></span>

<span data-ttu-id="504fe-327">指定一个虚拟机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="504fe-327">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="504fe-328">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-328">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="504fe-329">若要查看可供你使用的虚拟机，请使用 `Get-VM` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="504fe-329">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="504fe-330">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="504fe-330">CommonParameters</span></span>

<span data-ttu-id="504fe-331">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="504fe-331">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="504fe-332">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="504fe-332">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="504fe-333">输入</span><span class="sxs-lookup"><span data-stu-id="504fe-333">INPUTS</span></span>

### <span data-ttu-id="504fe-334">无</span><span class="sxs-lookup"><span data-stu-id="504fe-334">None</span></span>

<span data-ttu-id="504fe-335">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="504fe-335">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="504fe-336">输出</span><span class="sxs-lookup"><span data-stu-id="504fe-336">OUTPUTS</span></span>

### <span data-ttu-id="504fe-337">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-337">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="504fe-338">注释</span><span class="sxs-lookup"><span data-stu-id="504fe-338">NOTES</span></span>

- <span data-ttu-id="504fe-339">此 cmdlet 将获取用户托管的会话 **PSSession** 对象，例如使用新的 PSSession、 `Enter-PSSession` 和 Invoke-Command cmdlet 创建的对象。</span><span class="sxs-lookup"><span data-stu-id="504fe-339">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="504fe-340">它不会获取启动 PowerShell 时所创建的系统托管会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-340">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="504fe-341">从 Windows PowerShell 3.0 开始， **PSSession** 对象存储在连接的服务器端或接收端的计算机上。</span><span class="sxs-lookup"><span data-stu-id="504fe-341">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="504fe-342">若要获取存储在本地计算机或远程计算机上的会话，PowerShell 将建立与指定计算机的临时会话，并在该会话中运行查询命令。</span><span class="sxs-lookup"><span data-stu-id="504fe-342">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="504fe-343">若要获取连接到远程计算机的会话，请使用 **ComputerName** 或 **ConnectionUri** 参数来指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="504fe-343">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="504fe-344">若要筛选获取的会话 `Get-PSSession` ，请使用 **Name**、 **ID**、 **InstanceID** 和 **State** 参数。</span><span class="sxs-lookup"><span data-stu-id="504fe-344">To filter the sessions that `Get-PSSession` gets, use the **Name**, **ID**, **InstanceID**, and **State** parameters.</span></span> <span data-ttu-id="504fe-345">使用剩余的参数配置使用的临时会话 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="504fe-345">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="504fe-346">当你使用 **ComputerName** 或 **ConnectionUri** 参数时， `Get-PSSession` 仅获取来自运行 Windows powershell 3.0 和更高版本的 PowerShell 的计算机的会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-346">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="504fe-347">**PSSession** 的 **State** 属性值相对于当前会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-347">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="504fe-348">因此，值 "已 **断开连接** " 意味着 **PSSession** 未连接到当前会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-348">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="504fe-349">但是，它并不意味着 **PSSession** 会与所有会话断开连接。</span><span class="sxs-lookup"><span data-stu-id="504fe-349">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="504fe-350">它可能连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-350">It might be connected to a different session.</span></span> <span data-ttu-id="504fe-351">若要确定是否可以从当前会话连接或重新连接到 **PSSession** ，请使用 **Availability** 属性。</span><span class="sxs-lookup"><span data-stu-id="504fe-351">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="504fe-352">**Availability** 的 **None** 值指示可连接到 PSSession。</span><span class="sxs-lookup"><span data-stu-id="504fe-352">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="504fe-353">值为 " **忙碌** " 指示你无法连接到 **PSSession** ，因为它已连接到另一个会话。</span><span class="sxs-lookup"><span data-stu-id="504fe-353">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="504fe-354">有关会话的 **State** 属性的值的详细信息，请参阅 [RunspaceState 枚举](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="504fe-354">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="504fe-355">有关会话的 **可用性** 属性值的详细信息，请参阅 [runspacestate 枚举](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="504fe-355">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="504fe-356">相关链接</span><span class="sxs-lookup"><span data-stu-id="504fe-356">RELATED LINKS</span></span>

[<span data-ttu-id="504fe-357">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-357">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="504fe-358">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-358">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="504fe-359">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-359">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="504fe-360">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-360">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="504fe-361">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-361">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="504fe-362">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="504fe-362">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="504fe-363">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-363">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="504fe-364">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="504fe-364">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="504fe-365">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="504fe-365">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="504fe-366">about_Remote</span><span class="sxs-lookup"><span data-stu-id="504fe-366">about_Remote</span></span>](About/about_Remote.md)

