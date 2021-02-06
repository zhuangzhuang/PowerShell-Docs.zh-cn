---
title: 发现对象、属性和方法
description: 无需成为开发人员也能理解和使用对象、属性和方法。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: f226221da7dd3b663f54cf23439dd7f945ed3a2a
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99603572"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="3931f-103">第 3 章 - 发现对象、属性和方法</span><span class="sxs-lookup"><span data-stu-id="3931f-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="3931f-104">我第一次介绍的计算机是 Commodore 64，但我的第一台新式计算机是克隆版的 286 12-Mhz IBM，其内存空间为 1 兆字节，硬盘驱动器大小为 40 兆字节，一个大小为 5-1/4 英寸的软盘驱动器，配置了 CGA 显示器，操作系统是 Microsoft DOS 3.3。</span><span class="sxs-lookup"><span data-stu-id="3931f-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="3931f-105">许多 IT 专业人员（比如我自己）对命令行并不陌生，但论及对象、属性和方法这些主题时，他们就愣住了，并说道：“我不是开发人员。”</span><span class="sxs-lookup"><span data-stu-id="3931f-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="3931f-106">但你知道吗？</span><span class="sxs-lookup"><span data-stu-id="3931f-106">Guess what?</span></span> <span data-ttu-id="3931f-107">即使不是开发人员，也能够成功使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3931f-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="3931f-108">不要被这些术语所困扰。</span><span class="sxs-lookup"><span data-stu-id="3931f-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="3931f-109">一开始或许它们中的有一些并没有太大作用，但是经过一定量的实践之后，你就会在某些时刻突然灵光一现。</span><span class="sxs-lookup"><span data-stu-id="3931f-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="3931f-110">“啊！</span><span class="sxs-lookup"><span data-stu-id="3931f-110">"Aha!</span></span> <span data-ttu-id="3931f-111">这就是那本书里谈论的内容。”</span><span class="sxs-lookup"><span data-stu-id="3931f-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="3931f-112">请一定要在你的计算机上尝试操作这些示例，从而获得一些实践体验。</span><span class="sxs-lookup"><span data-stu-id="3931f-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="3931f-113">要求</span><span class="sxs-lookup"><span data-stu-id="3931f-113">Requirements</span></span>

<span data-ttu-id="3931f-114">本章所述的某些示例需要 Active Directory PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="3931f-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="3931f-115">该模块是 Windows 远程服务器管理工具 (RSAT) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="3931f-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="3931f-116">对于 Windows 1809（或更高版本），需将 RSAT 工具安装为一项 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="3931f-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="3931f-117">有关安装 RSAT 工具的信息，请参阅 [Windows 管理模块][]。</span><span class="sxs-lookup"><span data-stu-id="3931f-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="3931f-118">对于更低版本的 Windows，请参阅[适用于 Windows 的 RSAT][]。</span><span class="sxs-lookup"><span data-stu-id="3931f-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="3931f-119">Get-Member</span><span class="sxs-lookup"><span data-stu-id="3931f-119">Get-Member</span></span>

<span data-ttu-id="3931f-120">`Get-Member` 可帮助发现可用于命令的对象、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3931f-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="3931f-121">任何生成基于对象的输出的命令都可以通过管道传递到 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="3931f-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="3931f-122">属性是有关某个项的特征。</span><span class="sxs-lookup"><span data-stu-id="3931f-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="3931f-123">驾驶证上有一个属性名为“眼睛颜色”，而该属性最常见的值是蓝色和棕色。</span><span class="sxs-lookup"><span data-stu-id="3931f-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="3931f-124">方法是可以对某个项执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3931f-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="3931f-125">以驾驶证为例，方法之一是“吊销”，因为机动车管理部门可以吊销驾驶证。</span><span class="sxs-lookup"><span data-stu-id="3931f-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="3931f-126">属性</span><span class="sxs-lookup"><span data-stu-id="3931f-126">Properties</span></span>

<span data-ttu-id="3931f-127">在下面的示例中，我将检索计算机上运行的 Windows 时间服务的相关信息。</span><span class="sxs-lookup"><span data-stu-id="3931f-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="3931f-128">Status、Name 和 DisplayName 是上一组结果中显示的属性示例  。</span><span class="sxs-lookup"><span data-stu-id="3931f-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="3931f-129">Status 属性的值为 `Running`，Name 属性的值为 `w32time`，而 DisplayName 的值为 `Windows Time`  。</span><span class="sxs-lookup"><span data-stu-id="3931f-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="3931f-130">现在，我通过管道将同一命令传递给 `Get-Member`：</span><span class="sxs-lookup"><span data-stu-id="3931f-130">Now I'll pipe that same command to `Get-Member`:</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="3931f-131">上一个示例中的结果的第一行包含一条非常重要的信息。</span><span class="sxs-lookup"><span data-stu-id="3931f-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="3931f-132">TypeName 指示返回的对象类型。</span><span class="sxs-lookup"><span data-stu-id="3931f-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="3931f-133">在本示例中，返回了 System.ServiceProcess.ServiceController 对象。</span><span class="sxs-lookup"><span data-stu-id="3931f-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="3931f-134">该对象通常缩写为 TypeName 最后一个句点之后的部分；在本示例中，即为 ServiceController 。</span><span class="sxs-lookup"><span data-stu-id="3931f-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="3931f-135">在了解了命令生成的对象类型之后，就可以使用此信息查找接受该类型的对象作为输入的命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

<span data-ttu-id="3931f-136">所有这些命令都有一个参数，该参数通过管道或/和参数输入接受 ServiceController 对象类型。</span><span class="sxs-lookup"><span data-stu-id="3931f-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="3931f-137">请注意，实际的属性数量比默认显示的多。</span><span class="sxs-lookup"><span data-stu-id="3931f-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="3931f-138">尽管默认情况下未显示全部属性，但可以通过将命令通过管道传递到 `Select-Object` cmdlet 并使用 Property 参数，从管道中选择未显示的属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="3931f-139">以下示例通过将 `Get-Service` 的结果通过管道传递到 `Select-Object` 并将 `*` 通配符指定为 Property 参数的值来选择所有属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="3931f-140">也可以使用以逗号分隔的列表，选择特定的属性，作为 Property 参数的值。</span><span class="sxs-lookup"><span data-stu-id="3931f-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="3931f-141">默认情况下，表中会返回四个属性，而列表中会返回五个及以上的属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="3931f-142">一些命令使用自定义格式来覆盖表中默认显示的属性数量。</span><span class="sxs-lookup"><span data-stu-id="3931f-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="3931f-143">有几个 `Format-*` cmdlet 可用于手动覆盖这些默认值。</span><span class="sxs-lookup"><span data-stu-id="3931f-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="3931f-144">下一章将介绍最常见的 `Format-Table` 和 `Format-List` 这两种命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="3931f-145">使用 `Select-Object` 指定属性名称时可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3931f-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="3931f-146">在上一个示例中，`Can*` 被用作 Property 参数的某个值，用于返回所有以 `Can` 开头的属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="3931f-147">其中包括 CanPauseAndContinue、CanShutdown 和 CanStop  。</span><span class="sxs-lookup"><span data-stu-id="3931f-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="3931f-148">方法</span><span class="sxs-lookup"><span data-stu-id="3931f-148">Methods</span></span>

<span data-ttu-id="3931f-149">方法是可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3931f-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="3931f-150">使用 MemberType 参数来缩小 `Get-Member` 的结果范围，使其仅显示 `Get-Service` 的方法。</span><span class="sxs-lookup"><span data-stu-id="3931f-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

<span data-ttu-id="3931f-151">正如所见，存在多种方法。</span><span class="sxs-lookup"><span data-stu-id="3931f-151">As you can see, there are many methods.</span></span> <span data-ttu-id="3931f-152">Stop 方法可用于停止 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="3931f-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="3931f-153">现在可验证 Windows 时间服务确实已停止。</span><span class="sxs-lookup"><span data-stu-id="3931f-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="3931f-154">我很少使用方法，但仍需要注意这些方法。</span><span class="sxs-lookup"><span data-stu-id="3931f-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="3931f-155">有时你会遇到 `Get-*` 命令，却没有相应的命令来修改它。</span><span class="sxs-lookup"><span data-stu-id="3931f-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="3931f-156">通常，可以使用某个方法来修改它。</span><span class="sxs-lookup"><span data-stu-id="3931f-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="3931f-157">SqlServer PowerShell 模块中的 `Get-SqlAgentJob` cmdlet 就是一个很好的例子。</span><span class="sxs-lookup"><span data-stu-id="3931f-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="3931f-158">此模块作为 [SQL Server Management Studio (SMSS)][SMSS] 的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="3931f-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="3931f-159">不存在相应的 `Set-*` cmdlet，但可以使用某种方法来完成同一任务。</span><span class="sxs-lookup"><span data-stu-id="3931f-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="3931f-160">需要了解方法的另一个原因是，许多初学者认为无法使用 `Get-*` 命令进行颠覆性更改。</span><span class="sxs-lookup"><span data-stu-id="3931f-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="3931f-161">但是，如果方法使用不当，也会带来严重后果。</span><span class="sxs-lookup"><span data-stu-id="3931f-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="3931f-162">更好的选择是使用 cmdlet 执行该操作（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="3931f-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="3931f-163">继续操作，并启动 Windows 时间服务，但这次使用 cmdlet 启动服务。</span><span class="sxs-lookup"><span data-stu-id="3931f-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="3931f-164">默认情况下，`Start-Service` 不会像 `Get-Service` 的启动方法那样返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="3931f-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="3931f-165">但使用 cmdlet 的好处之一是，很多时候 cmdlet 提供了方法无法提供的其他功能。</span><span class="sxs-lookup"><span data-stu-id="3931f-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="3931f-166">上一个示例中使用了 PassThru 参数。</span><span class="sxs-lookup"><span data-stu-id="3931f-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="3931f-167">这会导致 cmdlet 生成输出，而它通常不生成输出。</span><span class="sxs-lookup"><span data-stu-id="3931f-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="3931f-168">注意有关 cmdlet 输出的猜想。</span><span class="sxs-lookup"><span data-stu-id="3931f-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="3931f-169">我们都知道人们的猜想会导致什么后果。</span><span class="sxs-lookup"><span data-stu-id="3931f-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="3931f-170">我将检索 Windows 10 实验环境计算机上运行的 PowerShell 进程的相关信息。</span><span class="sxs-lookup"><span data-stu-id="3931f-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="3931f-171">现在，我将同一个命令通过管道传递给 Get-Member：</span><span class="sxs-lookup"><span data-stu-id="3931f-171">Now I'll pipe that same command to Get-Member:</span></span>

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

<span data-ttu-id="3931f-172">请注意，列出的属性比默认显示的属性要多。</span><span class="sxs-lookup"><span data-stu-id="3931f-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="3931f-173">查看 `Get-Member` 的结果时，许多默认属性没有显示为属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="3931f-174">这是因为许多显示的值（例如 `NPM(K)`、`PM(K)`、`WS(K)` 和 `CPU(s)`）都是计算的属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="3931f-175">要确定实际的属性名称，必须通过管道将命令传递到 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="3931f-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="3931f-176">如果命令没有生成输出，则无法通过管道将其传递到 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="3931f-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="3931f-177">由于 `Start-Service` 默认不生成任何输出，在尝试通过管道将其传递到 `Get-Member` 时会生成错误。</span><span class="sxs-lookup"><span data-stu-id="3931f-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

<span data-ttu-id="3931f-178">可以使用 `Start-Service` cmdlet 指定 PassThru 参数，以使其生成输出，然后通过管道将输出传递到 `Get-Member`，这样不会出错。</span><span class="sxs-lookup"><span data-stu-id="3931f-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="3931f-179">若要通过管道将命令传递到 `Get-Member`，命令必须生成基于对象的输出。</span><span class="sxs-lookup"><span data-stu-id="3931f-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

<span data-ttu-id="3931f-180">`Out-Host` 直接写入 PowerShell 主机，但它不会为管道生成基于对象的输出。</span><span class="sxs-lookup"><span data-stu-id="3931f-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="3931f-181">因此无法通过管道将该命令传输到 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="3931f-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="3931f-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="3931f-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="3931f-183">若要完成本节内容，需要使用本章“要求”部分中列出的“远程服务器管理工具”。</span><span class="sxs-lookup"><span data-stu-id="3931f-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="3931f-184">另外，如本书简介中所述，Windows 10 实验环境计算机必须是实验环境域的成员。</span><span class="sxs-lookup"><span data-stu-id="3931f-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="3931f-185">将 `Get-Command` 与 Module 参数一起使用，以确定在安装远程服务器管理工具时，ActiveDirectory PowerShell 模块中添加了什么命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

<span data-ttu-id="3931f-186">ActiveDirectory PowerShell 模块中总共添加了 147 个命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="3931f-187">默认情况下，其中一些命令仅返回部分可用属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="3931f-188">是否注意到此模块中的命令名称有什么不同？</span><span class="sxs-lookup"><span data-stu-id="3931f-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="3931f-189">命令的名词部分具有 AD 前缀。</span><span class="sxs-lookup"><span data-stu-id="3931f-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="3931f-190">在大多数模块的命令中，这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="3931f-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="3931f-191">前缀的作用是防止发生命名冲突。</span><span class="sxs-lookup"><span data-stu-id="3931f-191">The prefix is designed to help prevent naming conflicts.</span></span>

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

<span data-ttu-id="3931f-192">即便不是很熟悉 Active Directory，应该也能察觉得到用户帐户的属性数量比本示例中显示的要多。</span><span class="sxs-lookup"><span data-stu-id="3931f-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="3931f-193">`Get-ADUser` cmdlet 具有 Properties 参数，该参数用于指定要返回的其他（非默认）属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="3931f-194">指定 `*` 通配符可返回所有这些属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-194">Specifying the `*` wildcard character returns all of them.</span></span>

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

<span data-ttu-id="3931f-195">现在看起来更接近了。</span><span class="sxs-lookup"><span data-stu-id="3931f-195">Now that looks more like it.</span></span>

<span data-ttu-id="3931f-196">你能想到为什么默认情况下会这样限制 Active Directory 用户帐户的属性吗？</span><span class="sxs-lookup"><span data-stu-id="3931f-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="3931f-197">假设你在生产 Active Directory 环境中为每个用户帐户返回每个属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="3931f-198">可以想到，这样不仅会导致域控制器本身性能降低，而且还会导致网络性能降低。</span><span class="sxs-lookup"><span data-stu-id="3931f-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="3931f-199">不管怎样，实际上是否需要所有属性是存疑的。</span><span class="sxs-lookup"><span data-stu-id="3931f-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="3931f-200">如果是想确认存在哪些属性，那么返回单个用户帐户的所有属性是完全可以接受的。</span><span class="sxs-lookup"><span data-stu-id="3931f-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="3931f-201">在制作原型时多次运行某个命令，这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="3931f-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="3931f-202">如果要执行一些大型查询，可查询一次并将结果存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="3931f-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="3931f-203">以后便使用变量的内容，而无需重复使用一些开销较高的查询。</span><span class="sxs-lookup"><span data-stu-id="3931f-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="3931f-204">使用 `$Users` 变量的内容，而不是多次运行同一个命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="3931f-205">请记住，在 Active Directory 中对相应的用户进行更改时，变量的内容不会更新。</span><span class="sxs-lookup"><span data-stu-id="3931f-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="3931f-206">可以通过管道将 `$Users` 变量传递给 `Get-Member`，以此发现可用的属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="3931f-207">然后，通过将 `$Users` 通过管道传递到 `Select-Object` 来选择各属性，所有这些操作都只查询 Active Directory 一次。</span><span class="sxs-lookup"><span data-stu-id="3931f-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="3931f-208">如果要多次查询 Active Directory，请使用 Properties 参数指定所需的任何非默认属性。</span><span class="sxs-lookup"><span data-stu-id="3931f-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a><span data-ttu-id="3931f-209">总结</span><span class="sxs-lookup"><span data-stu-id="3931f-209">Summary</span></span>

<span data-ttu-id="3931f-210">在本章中，你了解了如何确定命令生成的对象类型、如何确定命令可用的属性和方法，以及如何使用可限制默认返回的属性的命令。</span><span class="sxs-lookup"><span data-stu-id="3931f-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="3931f-211">审阅</span><span class="sxs-lookup"><span data-stu-id="3931f-211">Review</span></span>

1. <span data-ttu-id="3931f-212">`Get-Process` cmdlet 生成哪种类型的对象？</span><span class="sxs-lookup"><span data-stu-id="3931f-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="3931f-213">如何确定命令的可用属性有哪些？</span><span class="sxs-lookup"><span data-stu-id="3931f-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="3931f-214">如果存在可获取但不设置内容的命令，应检查哪些内容？</span><span class="sxs-lookup"><span data-stu-id="3931f-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="3931f-215">如何使某些默认情况下不生成输出的命令生成输出？</span><span class="sxs-lookup"><span data-stu-id="3931f-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="3931f-216">如果要使用生成大量输出的命令的结果，应考虑执行哪些操作？</span><span class="sxs-lookup"><span data-stu-id="3931f-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="3931f-217">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="3931f-217">Recommended Reading</span></span>

- <span data-ttu-id="3931f-218">[Get-Member][]</span><span class="sxs-lookup"><span data-stu-id="3931f-218">[Get-Member][]</span></span>
- <span data-ttu-id="3931f-219">[查看对象结构 (Get Member)][]</span><span class="sxs-lookup"><span data-stu-id="3931f-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="3931f-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="3931f-220">[about_Objects][]</span></span>
- <span data-ttu-id="3931f-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="3931f-221">[about_Properties][]</span></span>
- <span data-ttu-id="3931f-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="3931f-222">[about_Methods][]</span></span>
- <span data-ttu-id="3931f-223">[没有 PowerShell Cmdlet 可用于启动或停止某些内容？不要忘记在 Get Cmdlet 上检查方法][use-methods]</span><span class="sxs-lookup"><span data-stu-id="3931f-223">[No PowerShell Cmdlet to Start or Stop Something? Don't Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[适用于 Windows 的 RSAT]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Windows 管理模块]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[查看对象结构 (Get Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
