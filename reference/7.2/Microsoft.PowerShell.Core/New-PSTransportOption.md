---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: fa19ee7d1856eee91a6b1d6a8352017457031202
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596835"
---
# <span data-ttu-id="6ab02-102">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="6ab02-102">New-PSTransportOption</span></span>

## <span data-ttu-id="6ab02-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6ab02-103">SYNOPSIS</span></span>
<span data-ttu-id="6ab02-104">创建包含用于会话配置的高级选项的对象。</span><span class="sxs-lookup"><span data-stu-id="6ab02-104">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="6ab02-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ab02-105">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="6ab02-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6ab02-106">DESCRIPTION</span></span>

<span data-ttu-id="6ab02-107">**New-PSTransportOption** cmdlet 创建一个对象，它包含会话配置的传输选项。</span><span class="sxs-lookup"><span data-stu-id="6ab02-107">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="6ab02-108">可将对象用作可创建或更改会话配置的 cmdlet 的 *TransportOption* 参数值，例如 Register-PSSessionConfiguration 和 Set-PSSessionConfiguration cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6ab02-108">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="6ab02-109">还可以通过编辑 WSMan: 驱动器中会话配置属性的值更改传输选项设置。</span><span class="sxs-lookup"><span data-stu-id="6ab02-109">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="6ab02-110">有关详细信息，请参阅“WSMan 提供程序”。</span><span class="sxs-lookup"><span data-stu-id="6ab02-110">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="6ab02-111">会话配置选项表示在服务器端或接收到远程连接时设置的会话值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-111">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="6ab02-112">当创建会话时，或当客户端从会话断开连接或重新连接到会话时，客户端或发送连接端可以设置会话选项值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-112">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="6ab02-113">除非另有说明，当设置值冲突时，客户端的值优先。</span><span class="sxs-lookup"><span data-stu-id="6ab02-113">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="6ab02-114">但是，客户端的值不能与会话配置中设置的最大值和配额发生冲突。</span><span class="sxs-lookup"><span data-stu-id="6ab02-114">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="6ab02-115">如果没有参数，则 **new-pstransportoption** 将生成一个传输选项对象，该对象的所有选项都具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-115">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="6ab02-116">如果省略一个参数，则该对象具有该参数表示的属性的 null 值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-116">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="6ab02-117">空值不影响会话配置。</span><span class="sxs-lookup"><span data-stu-id="6ab02-117">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="6ab02-118">有关会话选项的详细信息，请参阅 New-PSSessionOption。</span><span class="sxs-lookup"><span data-stu-id="6ab02-118">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="6ab02-119">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab02-119">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="6ab02-120">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="6ab02-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6ab02-121">示例</span><span class="sxs-lookup"><span data-stu-id="6ab02-121">EXAMPLES</span></span>

### <span data-ttu-id="6ab02-122">示例1：生成默认传输选项</span><span class="sxs-lookup"><span data-stu-id="6ab02-122">Example 1: Generate a default transport option</span></span>

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="6ab02-123">此命令运行不带参数的 **new-pstransportoption** 。</span><span class="sxs-lookup"><span data-stu-id="6ab02-123">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="6ab02-124">输出显示该 cmdlet 将生成一个传输选项对象，该对象的所有属性都具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-124">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="6ab02-125">示例2：获取会话配置选项</span><span class="sxs-lookup"><span data-stu-id="6ab02-125">Example 2: Get session configuration options</span></span>

<span data-ttu-id="6ab02-126">此示例显示了如何使用传输选项对象来设置会话配置选项。</span><span class="sxs-lookup"><span data-stu-id="6ab02-126">This example shows how to use a transport options object to set session configuration options.</span></span>

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="6ab02-127">第一个命令使用 **New-PSTransportOption** cmdlet 创建传输选项对象，将其保存在 $t 变量中。</span><span class="sxs-lookup"><span data-stu-id="6ab02-127">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="6ab02-128">该命令使用 *MaxSessions* 参数将会话的最大数量增加到 40。</span><span class="sxs-lookup"><span data-stu-id="6ab02-128">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="6ab02-129">第二个命令使用 **Register-PSSessionConfiguration** cmdlet 创建 ITTasks 会话配置。</span><span class="sxs-lookup"><span data-stu-id="6ab02-129">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="6ab02-130">该命令使用 *TransportOption* 参数指定 $t 变量中的传输选项对象。</span><span class="sxs-lookup"><span data-stu-id="6ab02-130">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="6ab02-131">第三个命令使用 Get-PSSessionConfiguration cmdlet 获取 ITTasks 会话配置，并使用 Format-List cmdlet 在列表中显示会话配置对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-131">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="6ab02-132">输出显示会话配置的 **MaxShells** 属性的值为 40。</span><span class="sxs-lookup"><span data-stu-id="6ab02-132">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="6ab02-133">示例3：设置传输选项</span><span class="sxs-lookup"><span data-stu-id="6ab02-133">Example 3: Setting a transport option</span></span>

<span data-ttu-id="6ab02-134">此命令显示在使用会话配置的会话上设置会话配置中的传输选项的效果。</span><span class="sxs-lookup"><span data-stu-id="6ab02-134">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="6ab02-135">第一个命令使用 **New-PSTransportOption** cmdlet 创建传输选项对象。</span><span class="sxs-lookup"><span data-stu-id="6ab02-135">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="6ab02-136">该命令使用 *IdleTimeoutSec* 参数将对象的 **IdleTimeoutSec** 属性值设置为一小时（3600 秒）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-136">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="6ab02-137">此命令将传输对象保存在 $t 变量中。</span><span class="sxs-lookup"><span data-stu-id="6ab02-137">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="6ab02-138">第二个命令使用 Set-PSSessionConfiguration cmdlet 来更改 ITTasks 会话配置的传输选项。</span><span class="sxs-lookup"><span data-stu-id="6ab02-138">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="6ab02-139">该命令使用 *TransportOption* 参数指定 $t 变量中的传输选项对象。</span><span class="sxs-lookup"><span data-stu-id="6ab02-139">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="6ab02-140">第三个命令使用 New-PSSession cmdlet 在本地计算机上创建 MyITTasks 会话。</span><span class="sxs-lookup"><span data-stu-id="6ab02-140">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="6ab02-141">该命令使用 **ConfigurationName** 属性指定 ITTasks 会话配置。</span><span class="sxs-lookup"><span data-stu-id="6ab02-141">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="6ab02-142">该命令将会话保存在 $s 的变量中。请注意，此命令不使用 **新的-PSSession** 的 *SessionOption* 参数为会话设置自定义空闲超时。</span><span class="sxs-lookup"><span data-stu-id="6ab02-142">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="6ab02-143">如果已设置，则会话选项中设置的空闲超时值将优先于在会话配置中设置的空闲超时值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-143">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="6ab02-144">第四个命令使用 Format-List cmdlet 在列表中的 $s 变量中显示会话的所有属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-144">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="6ab02-145">该输出显示会话的空闲超时时间为1小时 (360000 毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="6ab02-145">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="6ab02-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ab02-146">PARAMETERS</span></span>

### <span data-ttu-id="6ab02-147">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6ab02-147">-IdleTimeoutSec</span></span>

<span data-ttu-id="6ab02-148">确定当远程计算机没有从本地计算机接收任何通信时，每个会话保持打开状态的时间。</span><span class="sxs-lookup"><span data-stu-id="6ab02-148">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="6ab02-149">这包括检测信号信号。</span><span class="sxs-lookup"><span data-stu-id="6ab02-149">This includes the heartbeat signal.</span></span>
<span data-ttu-id="6ab02-150">当时间间隔已过时，该会话将关闭。</span><span class="sxs-lookup"><span data-stu-id="6ab02-150">When the interval expires, the session closes.</span></span>

<span data-ttu-id="6ab02-151">当用户打算断开连接并重新连接到会话时，空闲超时值非常重要。</span><span class="sxs-lookup"><span data-stu-id="6ab02-151">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="6ab02-152">仅当会话未超时时，用户才可以重新连接。</span><span class="sxs-lookup"><span data-stu-id="6ab02-152">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="6ab02-153">*IdleTimeoutSec* 参数对应于会话配置的 **IdleTimeoutMs** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-153">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="6ab02-154">输入一个值（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-154">Enter a value in seconds.</span></span>
<span data-ttu-id="6ab02-155">默认值为 7200（2 小时）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-155">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="6ab02-156">最小值为 60（1 分钟）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-156">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="6ab02-157">最大值为 WSMan 配置 () 中 Shell 对象的 **IdleTimeout** 属性的值 `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="6ab02-157">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="6ab02-158">默认值为 7200000 毫秒（2 小时）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-158">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="6ab02-159">如果在会话选项和会话配置中设置空闲超时值，则在会话选项中设置的值优先，但它不能超过会话配置的 **MaxIdleTimeoutMs** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-159">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="6ab02-160">若要设置 **MaxIdleTimeoutMs** 属性的值，请使用 *MaxIdleTimeoutSec* 参数。</span><span class="sxs-lookup"><span data-stu-id="6ab02-160">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-161">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="6ab02-161">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="6ab02-162">将每个会话中可同时运行的命令数限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-162">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="6ab02-163">默认值为 1000。</span><span class="sxs-lookup"><span data-stu-id="6ab02-163">The default value is 1000.</span></span>

<span data-ttu-id="6ab02-164">*MaxConcurrentCommandsPerSession* 参数对应于会话配置的 **MaxConcurrentCommandsPerShell** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-164">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-165">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="6ab02-165">-MaxConcurrentUsers</span></span>

<span data-ttu-id="6ab02-166">将每个会话中可运行命令的用户数限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-166">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="6ab02-167">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="6ab02-167">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-168">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6ab02-168">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="6ab02-169">将每个会话的空闲超时设置限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-169">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="6ab02-170">默认值为 \[Int\]::MaxValue（大约 25 天）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-170">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="6ab02-171">当用户打算断开连接并重新连接到会话时，空闲超时值非常重要。</span><span class="sxs-lookup"><span data-stu-id="6ab02-171">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="6ab02-172">仅当会话未超时时，用户才可以重新连接。</span><span class="sxs-lookup"><span data-stu-id="6ab02-172">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="6ab02-173">*MaxIdleTimeoutSec* 参数对应于会话配置的 **MaxIdleTimeoutMs** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-173">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-174">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="6ab02-174">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="6ab02-175">将每个会话使用的内存限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-175">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="6ab02-176">输入一个值（以兆字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="6ab02-176">Enter a value in megabytes.</span></span>
<span data-ttu-id="6ab02-177">默认值为 1024 兆字节 (1 GB)。</span><span class="sxs-lookup"><span data-stu-id="6ab02-177">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="6ab02-178">*MaxMemoryPerSessionMB* 参数对应于会话配置的 **MaxMemoryPerShellMB** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-178">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-179">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="6ab02-179">-MaxProcessesPerSession</span></span>

<span data-ttu-id="6ab02-180">将在每个会话中运行的进程数限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-180">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="6ab02-181">默认值为 15。</span><span class="sxs-lookup"><span data-stu-id="6ab02-181">The default value is 15.</span></span>

<span data-ttu-id="6ab02-182">*MaxProcessesPerSession* 参数对应于会话配置的 **MaxProcessesPerShell** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-182">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-183">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="6ab02-183">-MaxSessions</span></span>

<span data-ttu-id="6ab02-184">限制使用会话配置的会话数。</span><span class="sxs-lookup"><span data-stu-id="6ab02-184">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="6ab02-185">默认值为 25。</span><span class="sxs-lookup"><span data-stu-id="6ab02-185">The default value is 25.</span></span>

<span data-ttu-id="6ab02-186">*MaxSessions* 参数对应于会话配置的 **MaxShells** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-186">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-187">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="6ab02-187">-MaxSessionsPerUser</span></span>

<span data-ttu-id="6ab02-188">将使用会话配置和使用给定用户的凭据运行的会话数限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-188">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="6ab02-189">默认值为 25。</span><span class="sxs-lookup"><span data-stu-id="6ab02-189">The default value is 25.</span></span>

<span data-ttu-id="6ab02-190">当你指定此值时，请考虑许多用户可能使用运行方式用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="6ab02-190">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="6ab02-191">*MaxSessionsPerUser* 参数对应于会话配置的 **MaxShellsPerUser** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-191">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-192">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="6ab02-192">-OutputBufferingMode</span></span>

<span data-ttu-id="6ab02-193">当输出缓冲区时已满时，确定如何在断开连接的会话中管理命令输出。</span><span class="sxs-lookup"><span data-stu-id="6ab02-193">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="6ab02-194">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="6ab02-194">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6ab02-195">阻止。</span><span class="sxs-lookup"><span data-stu-id="6ab02-195">Block.</span></span>
<span data-ttu-id="6ab02-196">当输出缓冲区已满时，将挂起执行，直到清除此缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6ab02-196">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="6ab02-197">删除。</span><span class="sxs-lookup"><span data-stu-id="6ab02-197">Drop.</span></span>
<span data-ttu-id="6ab02-198">当输出缓冲区已满时，执行将继续。</span><span class="sxs-lookup"><span data-stu-id="6ab02-198">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="6ab02-199">由于已保存新的输出，因此将丢弃最早的输出。</span><span class="sxs-lookup"><span data-stu-id="6ab02-199">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="6ab02-200">无。</span><span class="sxs-lookup"><span data-stu-id="6ab02-200">None.</span></span>
<span data-ttu-id="6ab02-201">未指定任何输出缓冲模式。</span><span class="sxs-lookup"><span data-stu-id="6ab02-201">No output buffering mode is specified.</span></span>

<span data-ttu-id="6ab02-202">会话的 **OutputBufferingMode** 属性的默认值为 Block。</span><span class="sxs-lookup"><span data-stu-id="6ab02-202">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-203">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6ab02-203">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="6ab02-204">将每个主机进程的超时值限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-204">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="6ab02-205">默认值为0，表示进程没有超时值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-205">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="6ab02-206">其他会话配置具有每个进程的超时值。</span><span class="sxs-lookup"><span data-stu-id="6ab02-206">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="6ab02-207">例如，对于每个进程的超时值为28800秒 (8 小时) **，则为。**</span><span class="sxs-lookup"><span data-stu-id="6ab02-207">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab02-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ab02-208">CommonParameters</span></span>

<span data-ttu-id="6ab02-209">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6ab02-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ab02-210">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6ab02-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ab02-211">输入</span><span class="sxs-lookup"><span data-stu-id="6ab02-211">INPUTS</span></span>

### <span data-ttu-id="6ab02-212">无</span><span class="sxs-lookup"><span data-stu-id="6ab02-212">None</span></span>

<span data-ttu-id="6ab02-213">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6ab02-213">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6ab02-214">输出</span><span class="sxs-lookup"><span data-stu-id="6ab02-214">OUTPUTS</span></span>

### <span data-ttu-id="6ab02-215">Microsoft.PowerShell.Commands.WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="6ab02-215">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="6ab02-216">注释</span><span class="sxs-lookup"><span data-stu-id="6ab02-216">NOTES</span></span>

- <span data-ttu-id="6ab02-217">会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="6ab02-217">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="6ab02-218">此外，使用会话配置文件的会话配置还具有其他属性。</span><span class="sxs-lookup"><span data-stu-id="6ab02-218">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="6ab02-219">相关链接</span><span class="sxs-lookup"><span data-stu-id="6ab02-219">RELATED LINKS</span></span>

[<span data-ttu-id="6ab02-220">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6ab02-220">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6ab02-221">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="6ab02-221">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="6ab02-222">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ab02-222">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6ab02-223">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ab02-223">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

