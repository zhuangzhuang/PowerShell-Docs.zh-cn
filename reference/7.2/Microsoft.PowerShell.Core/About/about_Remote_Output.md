---
description: 描述如何解释和格式化远程命令的输出。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595805"
---
# <a name="about-remote-output"></a><span data-ttu-id="e5b7d-103">关于远程输出</span><span class="sxs-lookup"><span data-stu-id="e5b7d-103">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="e5b7d-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="e5b7d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e5b7d-105">描述如何解释和格式化远程命令的输出。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-105">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="e5b7d-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="e5b7d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="e5b7d-107">在远程计算机上运行的命令的输出可能类似于在本地计算机上运行的同一个命令的输出，但存在一些重要的差异。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-107">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="e5b7d-108">本主题说明如何解释、格式化和显示在远程计算机上运行的命令的输出。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-108">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="e5b7d-109">显示计算机名称</span><span class="sxs-lookup"><span data-stu-id="e5b7d-109">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="e5b7d-110">使用 Invoke-Command cmdlet 在远程计算机上运行命令时，该命令将返回一个对象，该对象包含生成数据的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-110">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="e5b7d-111">远程计算机名称存储在 PSComputerName 属性中。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-111">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="e5b7d-112">对于许多命令，默认情况下会显示 PSComputerName。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-112">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="e5b7d-113">例如，以下命令在两台远程计算机 Server01 和 Server02 上运行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-113">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="e5b7d-114">输出如下所示，其中包含运行命令的远程计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-114">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="e5b7d-115">您可以使用 Invoke-Command 的 HideComputerName 参数来隐藏 PSComputerName 属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-115">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="e5b7d-116">此参数专为从一台远程计算机收集数据的命令而设计。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-116">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="e5b7d-117">以下命令在 Server01 远程计算机上运行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-117">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="e5b7d-118">它使用 HideComputerName 参数来隐藏 PSComputerName 属性和相关属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-118">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="e5b7d-119">如果默认情况下不显示 PSComputerName 属性，还可以显示该属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-119">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="e5b7d-120">例如，以下命令使用 Format-Table cmdlet 将 PSComputerName 属性添加到远程 Get-Date 命令的输出中。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-120">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="e5b7d-121">显示 MACHINENAME 属性</span><span class="sxs-lookup"><span data-stu-id="e5b7d-121">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="e5b7d-122">多个 cmdlet （包括获取进程、获取服务和获取事件日志）都具有一个用于获取远程计算机上的对象的 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-122">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="e5b7d-123">这些 cmdlet 不使用 PowerShell 远程处理，因此即使在未配置为在 Windows PowerShell 中进行远程处理的计算机上，也可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-123">These cmdlets do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="e5b7d-124">这些 cmdlet 返回的对象在 MachineName 属性中存储远程计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-124">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="e5b7d-125"> (这些对象没有 PSComputerName 属性。 ) </span><span class="sxs-lookup"><span data-stu-id="e5b7d-125">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="e5b7d-126">例如，此命令将获取 Server01 和 Server02 远程计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-126">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="e5b7d-127">默认显示不包括 MachineName 属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-127">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="e5b7d-128">可以使用 Format-Table cmdlet 显示进程对象的 MachineName 属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-128">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="e5b7d-129">例如，以下命令将进程保存在 $p 变量中，然后使用管道运算符 (|) 将 $p 中的进程发送到 Format-Table 命令。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-129">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="e5b7d-130">该命令使用 Format-Table 的属性参数在显示中包括 MachineName 属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-130">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="e5b7d-131">下面更复杂的命令将 MachineName 属性添加到默认进程显示。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-131">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="e5b7d-132">它使用哈希表来指定计算属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-132">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="e5b7d-133">幸运的是，您不必理解它来使用它。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-133">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="e5b7d-134"> (请注意，反撇号 ['] 是继续符。 ) </span><span class="sxs-lookup"><span data-stu-id="e5b7d-134">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="e5b7d-135">反序列化对象</span><span class="sxs-lookup"><span data-stu-id="e5b7d-135">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="e5b7d-136">当运行生成输出的远程命令时，命令输出会通过网络传输回本地计算机。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-136">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="e5b7d-137">由于大多数实时 Microsoft .NET 框架对象 (例如 PowerShell cmdlet 返回) 的对象无法通过网络进行传输，因此活动对象将 "序列化"。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-137">Because most live Microsoft .NET Framework objects (such as the objects that PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="e5b7d-138">换句话说，活动对象将转换为对象及其属性的 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-138">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="e5b7d-139">然后，基于 XML 的序列化对象通过网络传输。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-139">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="e5b7d-140">在本地计算机上，PowerShell 接收基于 XML 的序列化对象，并通过将基于 XML 的对象转换为标准 .NET Framework 对象来进行 "反序列化"。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-140">On the local computer, PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="e5b7d-141">但是，反序列化的对象不是活动对象。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-141">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="e5b7d-142">它是对象在序列化时的快照，它包含属性，但没有方法。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-142">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="e5b7d-143">可以在 PowerShell 中使用和管理这些对象，这些对象包括在管道中传递它们、显示所选属性以及设置它们的格式。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-143">You can use and manage these objects in PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="e5b7d-144">大多数反序列化对象会自动设置格式，以供 Types.ps1xml 或 Format.ps1xml 文件中的项显示。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-144">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="e5b7d-145">但是，本地计算机可能没有对远程计算机上生成的所有反序列化对象的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-145">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="e5b7d-146">如果未设置对象的格式，则每个对象的所有属性都将显示在控制台中的流列表中。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-146">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="e5b7d-147">如果未自动设置对象的格式，则可以使用格式设置 cmdlet （如 Format-Table 或格式列表）来设置所选属性的格式并显示这些属性。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-147">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="e5b7d-148">或者，可以使用 Out-GridView cmdlet 显示表中的对象。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-148">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="e5b7d-149">此外，如果你在远程计算机上运行的命令所使用的 cmdlet 不在本地计算机上，则该命令返回的对象的格式可能不正确，因为你的计算机上没有这些对象的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-149">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="e5b7d-150">若要从另一台计算机获取格式设置数据，请使用 Get-FormatData 和 Export-FormatData cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-150">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="e5b7d-151">某些对象类型（如 DirectoryInfo 对象和 Guid）在收到时转换回活动对象。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-151">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="e5b7d-152">这些对象不需要任何特殊的处理或格式。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-152">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="e5b7d-153">对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="e5b7d-153">ORDERING THE RESULTS</span></span>

<span data-ttu-id="e5b7d-154">Cmdlet 的 ComputerName 参数中计算机名称的顺序决定了 PowerShell 连接到远程计算机的顺序。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-154">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which PowerShell connects to the remote computers.</span></span> <span data-ttu-id="e5b7d-155">但是，结果以本地计算机接收它们的顺序显示，这可能是不同的顺序。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-155">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="e5b7d-156">若要更改结果的顺序，请使用 Sort-Object cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-156">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="e5b7d-157">可以按 PSComputerName 或 MachineName 属性进行排序。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-157">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="e5b7d-158">您还可以对对象的另一个属性进行排序，以使不同计算机的结果交错。</span><span class="sxs-lookup"><span data-stu-id="e5b7d-158">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5b7d-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5b7d-159">SEE ALSO</span></span>

[<span data-ttu-id="e5b7d-160">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e5b7d-160">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="e5b7d-161">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="e5b7d-161">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="e5b7d-162">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e5b7d-162">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="e5b7d-163">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e5b7d-163">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="e5b7d-164">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e5b7d-164">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="e5b7d-165">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e5b7d-165">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="e5b7d-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e5b7d-166">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

