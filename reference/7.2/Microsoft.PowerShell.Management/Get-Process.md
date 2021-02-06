---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 93db9ab1c8d70306fbf7243ac045ff0aa455dac6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597867"
---
# <span data-ttu-id="9f342-102">Get-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-102">Get-Process</span></span>

## <span data-ttu-id="9f342-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9f342-103">SYNOPSIS</span></span>
<span data-ttu-id="9f342-104">获取在本地计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-104">Gets the processes that are running on the local computer.</span></span>

## <span data-ttu-id="9f342-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9f342-105">SYNTAX</span></span>

### <span data-ttu-id="9f342-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="9f342-106">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="9f342-107">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="9f342-107">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="9f342-108">ID</span><span class="sxs-lookup"><span data-stu-id="9f342-108">Id</span></span>

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="9f342-109">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="9f342-109">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="9f342-110">InputObject</span><span class="sxs-lookup"><span data-stu-id="9f342-110">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="9f342-111">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="9f342-111">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## <span data-ttu-id="9f342-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9f342-112">DESCRIPTION</span></span>

<span data-ttu-id="9f342-113">`Get-Process`Cmdlet 将获取本地或远程计算机上的进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-113">The `Get-Process` cmdlet gets the processes on a local or remote computer.</span></span>

<span data-ttu-id="9f342-114">如果没有参数，此 cmdlet 将获取本地计算机上的所有进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-114">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span> <span data-ttu-id="9f342-115">还可以通过进程名称或进程 ID (PID) 指定特定进程，或将进程对象通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f342-115">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="9f342-116">默认情况下，此 cmdlet 将返回一个进程对象，该对象包含有关进程的详细信息，并支持使你能够启动和停止进程的方法。</span><span class="sxs-lookup"><span data-stu-id="9f342-116">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span> <span data-ttu-id="9f342-117">你还可以使用 cmdlet 的参数 `Get-Process` 来获取进程中运行的程序的文件版本信息，并获取进程加载的模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-117">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="9f342-118">示例</span><span class="sxs-lookup"><span data-stu-id="9f342-118">EXAMPLES</span></span>

### <span data-ttu-id="9f342-119">示例1：获取本地计算机上所有活动进程的列表</span><span class="sxs-lookup"><span data-stu-id="9f342-119">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="9f342-120">此命令将获取在本地计算机上运行的所有活动进程的列表。</span><span class="sxs-lookup"><span data-stu-id="9f342-120">This command gets a list of all active processes running on the local computer.</span></span> <span data-ttu-id="9f342-121">有关每列的定义，请参阅 [注释](#notes) 部分。</span><span class="sxs-lookup"><span data-stu-id="9f342-121">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="9f342-122">示例2：获取有关一个或多个进程的所有可用数据</span><span class="sxs-lookup"><span data-stu-id="9f342-122">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="9f342-123">此命令获取计算机上的有关 Winword 和 Explorer 进程的所有可用的数据。</span><span class="sxs-lookup"><span data-stu-id="9f342-123">This command gets all available data about the Winword and Explorer processes on the computer.</span></span> <span data-ttu-id="9f342-124">它使用 **Name** 参数来指定进程，但它省略了可选的参数名称。</span><span class="sxs-lookup"><span data-stu-id="9f342-124">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span> <span data-ttu-id="9f342-125">管道运算符将 `|` 数据传递给 `Format-List` cmdlet，后者显示 `*` Winword 和资源管理器进程对象的所有可用属性。</span><span class="sxs-lookup"><span data-stu-id="9f342-125">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="9f342-126">也可通过其进程 ID 来标识这些进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-126">You can also identify the processes by their process IDs.</span></span> <span data-ttu-id="9f342-127">例如：`Get-Process -Id 664, 2060`。</span><span class="sxs-lookup"><span data-stu-id="9f342-127">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="9f342-128">示例3：获取工作集大于指定大小的所有进程</span><span class="sxs-lookup"><span data-stu-id="9f342-128">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="9f342-129">此命令获取所有工作集大于 20 MB 的进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-129">This command gets all processes that have a working set greater than 20 MB.</span></span> <span data-ttu-id="9f342-130">它使用 `Get-Process` cmdlet 来获取所有正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-130">It uses the `Get-Process` cmdlet to get all running processes.</span></span> <span data-ttu-id="9f342-131">管道运算符将 `|` 进程对象传递给 `Where-Object` cmdlet，该 cmdlet 只选择其值大于20000000字节的工作集属性的对象。 </span><span class="sxs-lookup"><span data-stu-id="9f342-131">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="9f342-132">集 **是进程** 对象的许多属性之一。</span><span class="sxs-lookup"><span data-stu-id="9f342-132">**WorkingSet** is one of many properties of process objects.</span></span> <span data-ttu-id="9f342-133">若要查看所有属性，请键入 `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-133">To see all of the properties, type `Get-Process | Get-Member`.</span></span> <span data-ttu-id="9f342-134">默认情况下，所有数量属性的值以字节为单位，尽管默认显示以千字节和兆字节为单位列出这些值。</span><span class="sxs-lookup"><span data-stu-id="9f342-134">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="9f342-135">示例4：根据优先级列出计算机上的进程</span><span class="sxs-lookup"><span data-stu-id="9f342-135">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="9f342-136">这些命令基于其优先级类在计算机上列出进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-136">These commands list the processes on the computer in groups based on their priority class.</span></span> <span data-ttu-id="9f342-137">第一个命令获取计算机上的所有进程，然后将其存储在 `$A` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9f342-137">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="9f342-138">第二个命令将存储在变量中的 **进程** 对象通过管道传递 `$A` 给 `Get-Process` cmdlet，然后传递给 `Format-Table` cmdlet，后者使用 **优先级** 视图设置进程的格式。</span><span class="sxs-lookup"><span data-stu-id="9f342-138">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="9f342-139">**优先级** 视图和其他视图在 PowerShell home directory () 中的 types.ps1xml 格式文件中定义 `$pshome` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-139">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="9f342-140">示例5：向标准 Get-Process 输出显示添加属性</span><span class="sxs-lookup"><span data-stu-id="9f342-140">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

<span data-ttu-id="9f342-141">此示例从本地计算机和远程计算机 (S1) 中检索进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-141">This example retrieves processes from the local computer and a remote computer (S1).</span></span> <span data-ttu-id="9f342-142">检索到的进程将通过管道传递给 `Format-Table` 将 **MachineName** 属性添加到标准 `Get-Process` 输出显示的命令。</span><span class="sxs-lookup"><span data-stu-id="9f342-142">The retrieved processes are piped to the `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="9f342-143">示例6：获取进程的版本信息</span><span class="sxs-lookup"><span data-stu-id="9f342-143">Example 6: Get version information for a process</span></span>

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

<span data-ttu-id="9f342-144">此命令使用 **FileVersionInfo** 参数获取 pwsh.exe 文件的版本信息，该文件是 PowerShell 进程的主模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-144">This command uses the **FileVersionInfo** parameter to get the version information for the pwsh.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="9f342-145">若要在 Windows Vista 和更高版本的 Windows 上运行此命令，你必须以 "以管理员身份运行" 选项打开 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9f342-145">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="9f342-146">示例7：获取用指定进程加载的模块</span><span class="sxs-lookup"><span data-stu-id="9f342-146">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="9f342-147">此命令使用 **Module** 参数来获取已由进程加载的模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-147">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="9f342-148">此命令获取名称以 SQL 开头的进程的模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-148">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="9f342-149">若要在 Windows Vista 和更高版本的 Windows 上对你不拥有的进程运行此命令，必须通过 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9f342-149">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="9f342-150">示例8：查找进程的所有者</span><span class="sxs-lookup"><span data-stu-id="9f342-150">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

<span data-ttu-id="9f342-151">此命令演示如何查找进程的所有者。</span><span class="sxs-lookup"><span data-stu-id="9f342-151">This command shows how to find the owner of a process.</span></span>
<span data-ttu-id="9f342-152">在 Windows 上， **: includeusername** 参数需要提升的用户权限 (以管理员身份运行) 。</span><span class="sxs-lookup"><span data-stu-id="9f342-152">On Windows, the **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span>
<span data-ttu-id="9f342-153">输出显示所有者为 Domain01\user01。</span><span class="sxs-lookup"><span data-stu-id="9f342-153">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="9f342-154">示例9：使用自动变量标识托管当前会话的进程</span><span class="sxs-lookup"><span data-stu-id="9f342-154">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

<span data-ttu-id="9f342-155">这些命令演示如何使用 `$PID` 自动变量来标识承载当前 PowerShell 会话的进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-155">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="9f342-156">可以使用此方法将宿主进程与可能要停止或关闭的其他 PowerShell 进程区分开来。</span><span class="sxs-lookup"><span data-stu-id="9f342-156">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="9f342-157">第一个命令获取当前会话中的所有 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-157">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="9f342-158">第二个命令获取托管当前会话的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-158">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="9f342-159">示例10：获取具有主窗口标题的所有进程，并在表中显示这些进程</span><span class="sxs-lookup"><span data-stu-id="9f342-159">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="9f342-160">此命令获取具有主窗口标题的所有进程，并在表中显示这些进程及其进程 ID 和进程名称。</span><span class="sxs-lookup"><span data-stu-id="9f342-160">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="9f342-161">**MainWindowTitle** 属性只是返回的 **进程** 对象的许多有用属性之一 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-161">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span> <span data-ttu-id="9f342-162">若要查看所有属性，请通过管道将命令结果传递 `Get-Process` 给 `Get-Member` cmdlet `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-162">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="9f342-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f342-163">PARAMETERS</span></span>

### <span data-ttu-id="9f342-164">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="9f342-164">-FileVersionInfo</span></span>

<span data-ttu-id="9f342-165">指示此 cmdlet 获取进程中运行的程序的文件版本信息。</span><span class="sxs-lookup"><span data-stu-id="9f342-165">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="9f342-166">在 Windows Vista 和更高版本的 Windows 上，必须使用 "以管理员身份运行" 选项打开 PowerShell，才能对你不具有所有权的进程使用此参数。</span><span class="sxs-lookup"><span data-stu-id="9f342-166">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="9f342-167">若要获取远程计算机上某个进程的文件版本信息，请使用 `Invoke-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f342-167">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="9f342-168">使用此参数等效于获取每个进程对象的 **Mainmodule.fileversioninfo FileVersionInfo** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f342-168">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span> <span data-ttu-id="9f342-169">使用此参数时，将 `Get-Process` 返回 **FileVersionInfo** 对象 **FileVersionInfo**，而不是进程对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-169">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo**, not a process object.</span></span> <span data-ttu-id="9f342-170">因此，不能通过管道将命令输出传递到需要进程对象的 cmdlet，例如 `Stop-Process` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-170">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f342-171">-Id</span><span class="sxs-lookup"><span data-stu-id="9f342-171">-Id</span></span>

<span data-ttu-id="9f342-172">通过进程 ID (PID) 指定一个或多个进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-172">Specifies one or more processes by process ID (PID).</span></span> <span data-ttu-id="9f342-173">若要指定多个 ID，请使用逗号分隔 ID。</span><span class="sxs-lookup"><span data-stu-id="9f342-173">To specify multiple IDs, use commas to separate the IDs.</span></span> <span data-ttu-id="9f342-174">若要查找进程的 PID，请键入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="9f342-174">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f342-175">-: Includeusername</span><span class="sxs-lookup"><span data-stu-id="9f342-175">-IncludeUserName</span></span>

<span data-ttu-id="9f342-176">指示随命令的结果一起返回 **进程** 对象的用户名值。</span><span class="sxs-lookup"><span data-stu-id="9f342-176">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f342-177">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9f342-177">-InputObject</span></span>

<span data-ttu-id="9f342-178">指定一个或多个进程对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-178">Specifies one or more process objects.</span></span> <span data-ttu-id="9f342-179">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="9f342-179">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9f342-180">-Module</span><span class="sxs-lookup"><span data-stu-id="9f342-180">-Module</span></span>

<span data-ttu-id="9f342-181">指示此 cmdlet 获取由进程加载的模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-181">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="9f342-182">在 Windows Vista 和更高版本的 Windows 上，必须使用 "以 **管理员身份运行** " 选项打开 PowerShell，才能对你不具有所有权的进程使用此参数。</span><span class="sxs-lookup"><span data-stu-id="9f342-182">On Windows Vista and later versions of Windows, you must open PowerShell with the **Run as administrator** option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="9f342-183">若要获取远程计算机上由进程加载的模块，请使用 `Invoke-Command` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f342-183">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="9f342-184">此参数等效于获取每个进程对象的 **模块** 属性。</span><span class="sxs-lookup"><span data-stu-id="9f342-184">This parameter is equivalent to getting the **Modules** property of each process object.</span></span> <span data-ttu-id="9f342-185">使用此参数时，此 cmdlet 将返回 **system.diagnostics.processmodule** 对象 **system.diagnostics.processmodule**，而不是进程对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-185">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule**, not a process object.</span></span> <span data-ttu-id="9f342-186">因此，不能通过管道将命令输出传递到需要进程对象的 cmdlet，例如 `Stop-Process` 。</span><span class="sxs-lookup"><span data-stu-id="9f342-186">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="9f342-187">在同一命令中同时使用 *Module* 和 **FileVersionInfo** 参数时，此 Cmdlet 将返回一个 **FileVersionInfo** 对象，其中包含有关所有模块的文件版本的信息。</span><span class="sxs-lookup"><span data-stu-id="9f342-187">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f342-188">-Name</span><span class="sxs-lookup"><span data-stu-id="9f342-188">-Name</span></span>

<span data-ttu-id="9f342-189">通过进程名称指定一个或多个进程。</span><span class="sxs-lookup"><span data-stu-id="9f342-189">Specifies one or more processes by process name.</span></span> <span data-ttu-id="9f342-190">可以键入多个进程名称（以逗号分隔），并可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9f342-190">You can type multiple process names (separated by commas) and use wildcard characters.</span></span> <span data-ttu-id="9f342-191">参数名（“Name”）为可选项。</span><span class="sxs-lookup"><span data-stu-id="9f342-191">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9f342-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f342-192">CommonParameters</span></span>

<span data-ttu-id="9f342-193">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9f342-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f342-194">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9f342-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9f342-195">输入</span><span class="sxs-lookup"><span data-stu-id="9f342-195">INPUTS</span></span>

### <span data-ttu-id="9f342-196">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="9f342-196">System.Diagnostics.Process</span></span>

<span data-ttu-id="9f342-197">可以将进程对象通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f342-197">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="9f342-198">输出</span><span class="sxs-lookup"><span data-stu-id="9f342-198">OUTPUTS</span></span>

### <span data-ttu-id="9f342-199">"FileVersionInfo"、"System.diagnostics.processmodule" 和 "</span><span class="sxs-lookup"><span data-stu-id="9f342-199">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="9f342-200">默认情况下，此 cmdlet 将返回一个 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-200">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span> <span data-ttu-id="9f342-201">如果使用 **FileVersionInfo** 参数，它将返回 **FileVersionInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-201">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span> <span data-ttu-id="9f342-202">如果使用 **Module** 参数（不带 **FileVersionInfo** 参数），则它将返回 **system.diagnostics.processmodule** 对象。</span><span class="sxs-lookup"><span data-stu-id="9f342-202">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="9f342-203">注释</span><span class="sxs-lookup"><span data-stu-id="9f342-203">NOTES</span></span>

- <span data-ttu-id="9f342-204">还可以通过其内置别名、ps 和 gps 来引用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f342-204">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="9f342-205">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="9f342-205">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="9f342-206">在运行64位版本的 Windows 的计算机上，64位版本的 PowerShell 仅获取64位进程模块，而版本的 PowerShell 32 的版本仅适用于32位进程模块。</span><span class="sxs-lookup"><span data-stu-id="9f342-206">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="9f342-207">可以在 PowerShell 中使用 Windows Management Instrumentation (WMI) Win32_Process 对象的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9f342-207">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="9f342-208">有关信息，请参阅 `Get-WmiObject` 和 WMI SDK。</span><span class="sxs-lookup"><span data-stu-id="9f342-208">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="9f342-209">进程的默认显示为包括以下列的表。</span><span class="sxs-lookup"><span data-stu-id="9f342-209">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="9f342-210">有关进程对象的所有属性的说明，请参阅 [处理属性](/dotnet/api/system.diagnostics.process)。</span><span class="sxs-lookup"><span data-stu-id="9f342-210">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process).</span></span>
  - <span data-ttu-id="9f342-211">Handles：进程打开的句柄数。</span><span class="sxs-lookup"><span data-stu-id="9f342-211">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="9f342-212">NPM (K) ：进程正在使用的非分页内存量（kb）。</span><span class="sxs-lookup"><span data-stu-id="9f342-212">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="9f342-213">PM (K) ：进程正在使用的可分页内存量（kb）。</span><span class="sxs-lookup"><span data-stu-id="9f342-213">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="9f342-214">WS (K) ：进程工作集的大小（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="9f342-214">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="9f342-215">工作集包括进程最近引用的内存的页面。</span><span class="sxs-lookup"><span data-stu-id="9f342-215">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="9f342-216">VM (M) ：进程正在使用的虚拟内存量（以 mb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="9f342-216">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="9f342-217">虚拟内存包括磁盘上分页文件中的存储。</span><span class="sxs-lookup"><span data-stu-id="9f342-217">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="9f342-218">CPU () ：进程使用的处理器时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="9f342-218">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="9f342-219">ID：进程的进程 ID (PID) 。</span><span class="sxs-lookup"><span data-stu-id="9f342-219">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="9f342-220">ProcessName：进程的名称。</span><span class="sxs-lookup"><span data-stu-id="9f342-220">ProcessName: The name of the process.</span></span> <span data-ttu-id="9f342-221">有关与进程相关的概念的解释，请参阅帮助和支持中心中的词汇表以及任务管理器帮助。</span><span class="sxs-lookup"><span data-stu-id="9f342-221">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="9f342-222">你还可以使用中提供的进程的内置替代视图 `Format-Table` ，例如 **StartTime** 和 **Priority**，还可以设计你自己的视图。</span><span class="sxs-lookup"><span data-stu-id="9f342-222">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority**, and you can design your own views.</span></span>

## <span data-ttu-id="9f342-223">相关链接</span><span class="sxs-lookup"><span data-stu-id="9f342-223">RELATED LINKS</span></span>

[<span data-ttu-id="9f342-224">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-224">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="9f342-225">Get-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-225">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="9f342-226">Start-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-226">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="9f342-227">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-227">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="9f342-228">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="9f342-228">Wait-Process</span></span>](Wait-Process.md)
