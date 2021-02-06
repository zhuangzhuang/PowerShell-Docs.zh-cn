---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 28f343ddc6021e129d3eae007114b93ed17d5e95
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598077"
---
# <span data-ttu-id="9aafe-102">Start-Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-102">Start-Process</span></span>

## <span data-ttu-id="9aafe-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9aafe-103">SYNOPSIS</span></span>
<span data-ttu-id="9aafe-104">启动本地计算机上的一个或多个进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-104">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="9aafe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9aafe-105">SYNTAX</span></span>

### <span data-ttu-id="9aafe-106">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="9aafe-106">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9aafe-107">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="9aafe-107">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9aafe-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9aafe-108">DESCRIPTION</span></span>

<span data-ttu-id="9aafe-109">`Start-Process`Cmdlet 启动本地计算机上的一个或多个进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-109">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="9aafe-110">默认情况下， `Start-Process` 将创建一个新进程，该进程继承在当前进程中定义的所有环境变量。</span><span class="sxs-lookup"><span data-stu-id="9aafe-110">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="9aafe-111">若要指定在进程中运行的程序，请输入可执行文件或脚本文件，或者可使用计算机上的程序打开的文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-111">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="9aafe-112">如果指定不可执行文件，则将 `Start-Process` 启动与该文件关联的程序，类似于 `Invoke-Item` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9aafe-112">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="9aafe-113">您可以使用的参数 `Start-Process` 指定选项，例如加载用户配置文件、在新窗口中启动进程或使用备用凭据。</span><span class="sxs-lookup"><span data-stu-id="9aafe-113">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="9aafe-114">示例</span><span class="sxs-lookup"><span data-stu-id="9aafe-114">EXAMPLES</span></span>

### <span data-ttu-id="9aafe-115">示例 1：启动使用默认值的进程</span><span class="sxs-lookup"><span data-stu-id="9aafe-115">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="9aafe-116">此示例将启动一个进程，该进程使用 `Sort.exe` 当前文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-116">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="9aafe-117">此命令使用所有默认值，包括默认窗口样式、工作文件夹和凭据。</span><span class="sxs-lookup"><span data-stu-id="9aafe-117">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="9aafe-118">示例 2：打印文本文件</span><span class="sxs-lookup"><span data-stu-id="9aafe-118">Example 2: Print a text file</span></span>

<span data-ttu-id="9aafe-119">此示例启动打印文件的进程 `C:\PS-Test\MyFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-119">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="9aafe-120">示例 3：启动一个进程，以对项进行排序并返回到新文件</span><span class="sxs-lookup"><span data-stu-id="9aafe-120">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="9aafe-121">此示例启动一个进程，该进程对文件中的项进行排序 `Testsort.txt` ，并返回文件中的已排序项 `Sorted.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-121">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="9aafe-122">任何错误都将写入 `SortError.txt` 文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-122">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="9aafe-123">**UseNewEnvironment** 参数指定进程以其自己的环境变量运行。</span><span class="sxs-lookup"><span data-stu-id="9aafe-123">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="9aafe-124">示例 4：在最大化窗口中启动进程</span><span class="sxs-lookup"><span data-stu-id="9aafe-124">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="9aafe-125">此示例将启动 `Notepad.exe` 进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-125">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="9aafe-126">它将最大化窗口并在该进程完成之前一直保留该窗口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-126">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="9aafe-127">示例5：以管理员身份启动 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9aafe-127">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="9aafe-128">此示例使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9aafe-128">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="9aafe-129">示例 6：使用不同动词来启动进程</span><span class="sxs-lookup"><span data-stu-id="9aafe-129">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="9aafe-130">此示例显示了如何查找启动进程时可以使用的谓词。</span><span class="sxs-lookup"><span data-stu-id="9aafe-130">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="9aafe-131">可用谓词由进程中运行的文件的文件扩展名确定。</span><span class="sxs-lookup"><span data-stu-id="9aafe-131">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="9aafe-132">该示例使用 `New-Object` 为 **PowerShell.exe**（在 PowerShell 进程中运行的文件）创建 **ProcessStartInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="9aafe-132">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe**, the file that runs in the PowerShell process.</span></span> <span data-ttu-id="9aafe-133">**ProcessStartInfo** 对象的 **谓词** 属性显示，您可以将 **Open** 和 **RunAs** 谓词与一起使用 `PowerShell.exe` ，也可以与运行文件的任何进程一起使用 `.exe` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-133">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="9aafe-134">示例7：指定进程的参数</span><span class="sxs-lookup"><span data-stu-id="9aafe-134">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="9aafe-135">这两个命令都启动 Windows 命令解释器，并对 `dir` 该文件夹发出命令 `Program Files` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-135">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="9aafe-136">由于此文件夹名包含空格，因此值需要用转义引号括起来。</span><span class="sxs-lookup"><span data-stu-id="9aafe-136">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="9aafe-137">请注意，第一个命令将字符串指定为 **ArgumentList**。</span><span class="sxs-lookup"><span data-stu-id="9aafe-137">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="9aafe-138">第二个命令是字符串数组。</span><span class="sxs-lookup"><span data-stu-id="9aafe-138">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

### <span data-ttu-id="9aafe-139">示例8：在 Linux 上创建分离的进程</span><span class="sxs-lookup"><span data-stu-id="9aafe-139">Example 8: Create a detached process on Linux</span></span>

<span data-ttu-id="9aafe-140">在 Windows 上， `Start-Process` 创建独立于启动 shell 的独立进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-140">On Windows, `Start-Process` creates an independent process that remains running independently of the launching shell.</span></span> <span data-ttu-id="9aafe-141">在非 Windows 平台上，新启动的进程会附加到启动的 shell。</span><span class="sxs-lookup"><span data-stu-id="9aafe-141">On non-Windows platforms, the newly started process is attached to the shell that launched.</span></span> <span data-ttu-id="9aafe-142">如果关闭了启动 shell，则会终止子进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-142">If the launching shell is closed, the child process is terminated.</span></span>

<span data-ttu-id="9aafe-143">若要避免在类似 Unix 的平台上终止子进程，可以将 `Start-Process` 与结合 `nohup` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-143">To avoid terminating the child process on Unix-like platforms, you can combine `Start-Process` with `nohup`.</span></span> <span data-ttu-id="9aafe-144">下面的示例将在 Linux 上启动 PowerShell 的后台实例，即使在关闭启动会话之后仍保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="9aafe-144">The following example launches a background instance of PowerShell on Linux that stays alive even after you close the launching session.</span></span> <span data-ttu-id="9aafe-145">`nohup`命令收集 `nohup.out` 当前目录中的输出文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-145">The `nohup` command collects output in file `nohup.out` in the current directory.</span></span>

```powershell
# Runs for 2 minutes and appends output to ./nohup.out
Start-Process nohup 'pwsh -noprofile -c "1..120 | % { Write-Host . -NoNewline; sleep 1 }"'
```

<span data-ttu-id="9aafe-146">在此示例中， `Start-Process` 运行 Linux `nohup` 命令，该命令将 `pwsh` 作为分离的进程启动。</span><span class="sxs-lookup"><span data-stu-id="9aafe-146">In this example, `Start-Process` is running the Linux `nohup` command, which launches `pwsh` as a detached process.</span></span> <span data-ttu-id="9aafe-147">有关详细信息，请参阅 [nohup](https://linux.die.net/man/1/nohup)的手册页。</span><span class="sxs-lookup"><span data-stu-id="9aafe-147">For more information, see the man page for [nohup](https://linux.die.net/man/1/nohup).</span></span>

## <span data-ttu-id="9aafe-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9aafe-148">PARAMETERS</span></span>

### <span data-ttu-id="9aafe-149">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9aafe-149">-ArgumentList</span></span>

<span data-ttu-id="9aafe-150">指定此 cmdlet 启动进程时要使用的参数或参数值。</span><span class="sxs-lookup"><span data-stu-id="9aafe-150">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="9aafe-151">参数可以作为单个字符串接受，其中的参数由空格分隔，或者作为以逗号分隔的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="9aafe-151">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="9aafe-152">如果参数或参数值包含空格，则必须用转义双引号将其引起来。</span><span class="sxs-lookup"><span data-stu-id="9aafe-152">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="9aafe-153">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-153">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="9aafe-154">-Credential</span></span>

<span data-ttu-id="9aafe-155">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9aafe-155">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9aafe-156">默认情况下，该 cmdlet 使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="9aafe-156">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="9aafe-157">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-157">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9aafe-158">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="9aafe-158">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9aafe-159">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-159">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9aafe-160">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-160">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-161">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9aafe-161">-FilePath</span></span>

<span data-ttu-id="9aafe-162">指定在进程中运行的程序的可选路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9aafe-162">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="9aafe-163">输入 `.txt` `.doc` 与计算机上的程序相关联的可执行文件或文档（如或文件）的名称。</span><span class="sxs-lookup"><span data-stu-id="9aafe-163">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="9aafe-164">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9aafe-164">This parameter is required.</span></span>

<span data-ttu-id="9aafe-165">如果仅指定文件名，请使用 **WorkingDirectory** 参数来指定路径。</span><span class="sxs-lookup"><span data-stu-id="9aafe-165">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-166">-LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="9aafe-166">-LoadUserProfile</span></span>

<span data-ttu-id="9aafe-167">指示此 cmdlet 为当前用户加载存储在注册表项中的 Windows 用户配置文件 `HKEY_USERS` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-167">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="9aafe-168">参数不适用于非 Windows 系统。</span><span class="sxs-lookup"><span data-stu-id="9aafe-168">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="9aafe-169">此参数不会影响 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-169">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="9aafe-170">有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-170">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-171">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="9aafe-171">-NoNewWindow</span></span>

<span data-ttu-id="9aafe-172">在当前控制台窗口中启动新进程。</span><span class="sxs-lookup"><span data-stu-id="9aafe-172">Start the new process in the current console window.</span></span> <span data-ttu-id="9aafe-173">默认情况下，在 Windows 上，PowerShell 会打开一个新窗口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-173">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="9aafe-174">在非 Windows 系统上，你永远不会收到新的终端窗口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-174">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="9aafe-175">不能在同一命令中使用 **NoNewWindow** 参数和 **WindowStyle** 参数。</span><span class="sxs-lookup"><span data-stu-id="9aafe-175">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="9aafe-176">参数不适用于非 Windows 系统。</span><span class="sxs-lookup"><span data-stu-id="9aafe-176">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-177">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9aafe-177">-PassThru</span></span>

<span data-ttu-id="9aafe-178">为 cmdlet 启动的每个进程返回一个进程对象。</span><span class="sxs-lookup"><span data-stu-id="9aafe-178">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="9aafe-179">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="9aafe-179">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9aafe-180">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="9aafe-180">-RedirectStandardError</span></span>

<span data-ttu-id="9aafe-181">指定文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-181">Specifies a file.</span></span> <span data-ttu-id="9aafe-182">此 cmdlet 将进程产生的所有错误发送给指定的文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-182">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="9aafe-183">输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9aafe-183">Enter the path and filename.</span></span> <span data-ttu-id="9aafe-184">默认情况下，在控制台中显示这些错误。</span><span class="sxs-lookup"><span data-stu-id="9aafe-184">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-185">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="9aafe-185">-RedirectStandardInput</span></span>

<span data-ttu-id="9aafe-186">指定文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-186">Specifies a file.</span></span> <span data-ttu-id="9aafe-187">此 cmdlet 从指定文件读取输入。</span><span class="sxs-lookup"><span data-stu-id="9aafe-187">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="9aafe-188">输入输入文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9aafe-188">Enter the path and filename of the input file.</span></span> <span data-ttu-id="9aafe-189">默认情况下，进程从键盘获取其输入。</span><span class="sxs-lookup"><span data-stu-id="9aafe-189">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-190">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="9aafe-190">-RedirectStandardOutput</span></span>

<span data-ttu-id="9aafe-191">指定文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-191">Specifies a file.</span></span> <span data-ttu-id="9aafe-192">此 cmdlet 将进程产生的输出发送给指定的文件。</span><span class="sxs-lookup"><span data-stu-id="9aafe-192">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="9aafe-193">输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9aafe-193">Enter the path and filename.</span></span> <span data-ttu-id="9aafe-194">默认情况下，在控制台中显示该输出。</span><span class="sxs-lookup"><span data-stu-id="9aafe-194">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-195">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="9aafe-195">-UseNewEnvironment</span></span>

<span data-ttu-id="9aafe-196">指示此 cmdlet 使用为进程指定的新环境变量。</span><span class="sxs-lookup"><span data-stu-id="9aafe-196">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="9aafe-197">默认情况下，启动的进程使用继承自父进程的环境变量运行。</span><span class="sxs-lookup"><span data-stu-id="9aafe-197">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-198">-Verb</span><span class="sxs-lookup"><span data-stu-id="9aafe-198">-Verb</span></span>

<span data-ttu-id="9aafe-199">指定此 cmdlet 启动进程时要使用的动词。</span><span class="sxs-lookup"><span data-stu-id="9aafe-199">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="9aafe-200">可用的动词取决于进程中运行的文件的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="9aafe-200">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="9aafe-201">下表列出了适用于某些常用进程文件类型的动词。</span><span class="sxs-lookup"><span data-stu-id="9aafe-201">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="9aafe-202">文件类型</span><span class="sxs-lookup"><span data-stu-id="9aafe-202">File type</span></span> |                <span data-ttu-id="9aafe-203">谓词</span><span class="sxs-lookup"><span data-stu-id="9aafe-203">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="9aafe-204">.cmd</span><span class="sxs-lookup"><span data-stu-id="9aafe-204">.cmd</span></span>      | <span data-ttu-id="9aafe-205">Edit、Open、Print、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="9aafe-205">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="9aafe-206">.exe</span><span class="sxs-lookup"><span data-stu-id="9aafe-206">.exe</span></span>      | <span data-ttu-id="9aafe-207">Open、RunAs、RunAsUser</span><span class="sxs-lookup"><span data-stu-id="9aafe-207">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="9aafe-208">.txt</span><span class="sxs-lookup"><span data-stu-id="9aafe-208">.txt</span></span>      | <span data-ttu-id="9aafe-209">Open、Print、PrintTo</span><span class="sxs-lookup"><span data-stu-id="9aafe-209">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="9aafe-210">.wav</span><span class="sxs-lookup"><span data-stu-id="9aafe-210">.wav</span></span>      | <span data-ttu-id="9aafe-211">打开、播放</span><span class="sxs-lookup"><span data-stu-id="9aafe-211">Open, Play</span></span>                          |

<span data-ttu-id="9aafe-212">若要查找可用于进程中运行的文件的谓词，请使用 `New-Object` cmdlet 为该文件创建 **ProcessStartInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="9aafe-212">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="9aafe-213">可用谓词位于 **ProcessStartInfo** 对象的 **谓词** 属性中。</span><span class="sxs-lookup"><span data-stu-id="9aafe-213">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="9aafe-214">有关详细信息，请参阅示例。</span><span class="sxs-lookup"><span data-stu-id="9aafe-214">For details, see the examples.</span></span>

<span data-ttu-id="9aafe-215">参数不适用于非 Windows 系统。</span><span class="sxs-lookup"><span data-stu-id="9aafe-215">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-216">-Wait</span><span class="sxs-lookup"><span data-stu-id="9aafe-216">-Wait</span></span>

<span data-ttu-id="9aafe-217">指示此 cmdlet 等待指定的进程及其子代完成，然后再接受更多输入。</span><span class="sxs-lookup"><span data-stu-id="9aafe-217">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="9aafe-218">此参数禁止显示命令提示符，或在进程完成之前一直保留窗口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-218">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="9aafe-219">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="9aafe-219">-WindowStyle</span></span>

<span data-ttu-id="9aafe-220">指定用于新进程的窗口的状态。</span><span class="sxs-lookup"><span data-stu-id="9aafe-220">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="9aafe-221">此参数可接受的值包括： **普通**、 **隐藏**、 **最小化** 和 **最大化**。</span><span class="sxs-lookup"><span data-stu-id="9aafe-221">The acceptable values for this parameter are: **Normal**, **Hidden**, **Minimized**, and **Maximized**.</span></span> <span data-ttu-id="9aafe-222">默认值为 " **正常**"。</span><span class="sxs-lookup"><span data-stu-id="9aafe-222">The default value is **Normal**.</span></span>

<span data-ttu-id="9aafe-223">不能在同一命令中使用 **WindowStyle** 参数和 **NoNewWindow** 参数。</span><span class="sxs-lookup"><span data-stu-id="9aafe-223">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="9aafe-224">参数不适用于非 Windows 系统。</span><span class="sxs-lookup"><span data-stu-id="9aafe-224">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-225">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="9aafe-225">-WorkingDirectory</span></span>

<span data-ttu-id="9aafe-226">指定新进程的开始位置。</span><span class="sxs-lookup"><span data-stu-id="9aafe-226">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="9aafe-227">默认值是要启动的可执行文件或文档的位置。</span><span class="sxs-lookup"><span data-stu-id="9aafe-227">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="9aafe-228">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="9aafe-228">Wildcards are not supported.</span></span> <span data-ttu-id="9aafe-229">路径名不能包含将解释为通配符的字符。</span><span class="sxs-lookup"><span data-stu-id="9aafe-229">The path name must not contain characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-230">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9aafe-230">-Confirm</span></span>

<span data-ttu-id="9aafe-231">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="9aafe-231">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-232">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9aafe-232">-WhatIf</span></span>

<span data-ttu-id="9aafe-233">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9aafe-233">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9aafe-234">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="9aafe-234">The cmdlet is not run.</span></span>

<span data-ttu-id="9aafe-235">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="9aafe-235">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aafe-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9aafe-236">CommonParameters</span></span>

<span data-ttu-id="9aafe-237">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9aafe-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9aafe-238">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-238">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9aafe-239">输入</span><span class="sxs-lookup"><span data-stu-id="9aafe-239">INPUTS</span></span>

### <span data-ttu-id="9aafe-240">无</span><span class="sxs-lookup"><span data-stu-id="9aafe-240">None</span></span>

<span data-ttu-id="9aafe-241">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9aafe-241">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9aafe-242">输出</span><span class="sxs-lookup"><span data-stu-id="9aafe-242">OUTPUTS</span></span>

### <span data-ttu-id="9aafe-243">无、System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-243">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="9aafe-244">如果指定 PassThru 参数，则此 cmdlet 会生成 **System.Diagnostics.Process**。</span><span class="sxs-lookup"><span data-stu-id="9aafe-244">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="9aafe-245">否则，此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="9aafe-245">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="9aafe-246">注释</span><span class="sxs-lookup"><span data-stu-id="9aafe-246">NOTES</span></span>

- <span data-ttu-id="9aafe-247">此 cmdlet 通过使用 system.exception 类的 **Start** 方法来实现 **。**</span><span class="sxs-lookup"><span data-stu-id="9aafe-247">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="9aafe-248">有关此方法的详细信息，请参阅 [Process： Start 方法](/dotnet/api/system.diagnostics.process.start#overloads)。</span><span class="sxs-lookup"><span data-stu-id="9aafe-248">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="9aafe-249">在 Windows 上，当你使用 **UseNewEnvironment** 时，新进程将仅开始包含为 **计算机** 范围定义的默认环境变量。</span><span class="sxs-lookup"><span data-stu-id="9aafe-249">On Windows, when you use **UseNewEnvironment**, the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="9aafe-250">这会影响 `$env:USERNAME` 设置为 **SYSTEM**。</span><span class="sxs-lookup"><span data-stu-id="9aafe-250">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="9aafe-251">不包含 **用户** 范围中的任何变量。</span><span class="sxs-lookup"><span data-stu-id="9aafe-251">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="9aafe-252">在 Windows 上，最常见的用例 `Start-Process` 是使用 **Wait** 参数来阻止进度，直到新进程退出。</span><span class="sxs-lookup"><span data-stu-id="9aafe-252">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="9aafe-253">在非 Windows 系统上，很少需要这样做，因为命令行应用程序的默认行为等效于 `Start-Process -Wait` 。</span><span class="sxs-lookup"><span data-stu-id="9aafe-253">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="9aafe-254">在 `Start-Process` 非 Windows 系统上使用时，你永远不会收到新的终端窗口。</span><span class="sxs-lookup"><span data-stu-id="9aafe-254">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="9aafe-255">相关链接</span><span class="sxs-lookup"><span data-stu-id="9aafe-255">RELATED LINKS</span></span>

[<span data-ttu-id="9aafe-256">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="9aafe-256">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="9aafe-257">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-257">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="9aafe-258">Get-Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-258">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="9aafe-259">Start-Service</span><span class="sxs-lookup"><span data-stu-id="9aafe-259">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="9aafe-260">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-260">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="9aafe-261">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="9aafe-261">Wait-Process</span></span>](Wait-Process.md)
