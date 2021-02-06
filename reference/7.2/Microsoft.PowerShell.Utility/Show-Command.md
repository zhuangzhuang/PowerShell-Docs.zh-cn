---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603806"
---
# <span data-ttu-id="12259-102">Show-Command</span><span class="sxs-lookup"><span data-stu-id="12259-102">Show-Command</span></span>

## <span data-ttu-id="12259-103">摘要</span><span class="sxs-lookup"><span data-stu-id="12259-103">SYNOPSIS</span></span>
<span data-ttu-id="12259-104">在图形窗口中显示 PowerShell 命令信息。</span><span class="sxs-lookup"><span data-stu-id="12259-104">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="12259-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12259-105">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="12259-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12259-106">DESCRIPTION</span></span>

<span data-ttu-id="12259-107">`Show-Command`Cmdlet 可让你在命令窗口中创建 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="12259-107">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="12259-108">你可以使用命令窗口的功能运行命令或使其向你返回命令。</span><span class="sxs-lookup"><span data-stu-id="12259-108">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="12259-109">`Show-Command` 是一个非常有用的教学和学习工具。</span><span class="sxs-lookup"><span data-stu-id="12259-109">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="12259-110">`Show-Command` 适用于所有命令类型，包括 cmdlet、函数、工作流和 CIM 命令。</span><span class="sxs-lookup"><span data-stu-id="12259-110">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="12259-111">如果没有参数，则会 `Show-Command` 显示一个命令窗口，其中列出了所有已安装模块中的所有可用命令。</span><span class="sxs-lookup"><span data-stu-id="12259-111">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="12259-112">若要查找某个模块中的命令，请从“模块”下拉列表中选择该模块。</span><span class="sxs-lookup"><span data-stu-id="12259-112">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="12259-113">若要选择命令，请单击命令名称。</span><span class="sxs-lookup"><span data-stu-id="12259-113">To select a command, click the command name.</span></span>

<span data-ttu-id="12259-114">若要使用命令窗口，请通过使用 Name 或单击 **Commands** 列表中的命令名称选择命令。</span><span class="sxs-lookup"><span data-stu-id="12259-114">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="12259-115">每个参数集都显示在单独的选项卡上。星号表示强制参数。</span><span class="sxs-lookup"><span data-stu-id="12259-115">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="12259-116">若要输入某个参数的值，请在文本框中键入该值或从下拉框中选择值。</span><span class="sxs-lookup"><span data-stu-id="12259-116">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="12259-117">若要添加开关参数，请单击以选中参数复选框。</span><span class="sxs-lookup"><span data-stu-id="12259-117">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="12259-118">当你准备就绪后，可以单击 **Copy**，以将你创建的命令复制到剪贴板，或单击 **Run** 运行该命令。</span><span class="sxs-lookup"><span data-stu-id="12259-118">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="12259-119">你还可以使用 **PassThru** 参数将命令返回到主机程序，如 PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="12259-119">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="12259-120">若要取消命令选择并返回到显示所有命令的视图，请按 Ctrl 并单击所选的命令。</span><span class="sxs-lookup"><span data-stu-id="12259-120">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="12259-121">在 PowerShell 集成脚本环境中 (ISE) ， `Show-Command` 默认情况下会显示窗口的一个变体。</span><span class="sxs-lookup"><span data-stu-id="12259-121">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="12259-122">有关使用此命令窗口的信息，请参阅 PowerShell ISE 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="12259-122">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="12259-123">此 cmdlet 已在 PowerShell 7 中引入。</span><span class="sxs-lookup"><span data-stu-id="12259-123">This cmdlet was reintroduced in PowerShell 7.</span></span>

<span data-ttu-id="12259-124">由于此 cmdlet 需要用户界面，因此它在 Windows Server Core 或 Windows Nano Server 上不起作用。</span><span class="sxs-lookup"><span data-stu-id="12259-124">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="12259-125">此 cmdlet 仅适用于支持 Windows 桌面的 Windows 系统。</span><span class="sxs-lookup"><span data-stu-id="12259-125">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="12259-126">示例</span><span class="sxs-lookup"><span data-stu-id="12259-126">EXAMPLES</span></span>

### <span data-ttu-id="12259-127">示例 1：打开命令窗口</span><span class="sxs-lookup"><span data-stu-id="12259-127">Example 1: Open the Commands window</span></span>

<span data-ttu-id="12259-128">此示例显示了窗口的默认视图 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-128">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="12259-129">" **命令** " 窗口显示计算机上安装的所有模块中的所有命令的列表。</span><span class="sxs-lookup"><span data-stu-id="12259-129">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="12259-130">示例 2：在命令窗口中打开 cmdlet</span><span class="sxs-lookup"><span data-stu-id="12259-130">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="12259-131">此示例 `Invoke-Command` 在 " **命令** " 窗口中显示该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12259-131">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="12259-132">可以使用此显示运行 `Invoke-Command` 命令。</span><span class="sxs-lookup"><span data-stu-id="12259-132">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="12259-133">示例 3：打开具有指定参数的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="12259-133">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="12259-134">此命令打开 `Show-Command` cmdlet 的窗口 `Connect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="12259-134">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="12259-135">**Height** 和 **Width** 参数指定命令窗口的维度。</span><span class="sxs-lookup"><span data-stu-id="12259-135">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="12259-136">**ErrorPopup** 参数显示错误命令窗口。</span><span class="sxs-lookup"><span data-stu-id="12259-136">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="12259-137">单击 " **运行**" 时， `Connect-PSSession` 命令将运行，就像你在 `Connect-PSSession` 命令行中键入命令一样。</span><span class="sxs-lookup"><span data-stu-id="12259-137">When you click **Run**, the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="12259-138">示例 4：为 cmdlet 指定新的默认参数值</span><span class="sxs-lookup"><span data-stu-id="12259-138">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="12259-139">此示例使用 `$PSDefaultParameterValues` 自动变量为 cmdlet 的 **Height**、 **Width** 和 **ErrorPopup** 参数设置新的默认值 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-139">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height**, **Width**, and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="12259-140">现在，运行命令时 `Show-Command` ，将自动应用新的默认值。</span><span class="sxs-lookup"><span data-stu-id="12259-140">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="12259-141">若要在每个 PowerShell 会话中使用这些默认值，请将 `$PSDefaultParameterValues` 变量添加到 powershell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="12259-141">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="12259-142">有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 和 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)。</span><span class="sxs-lookup"><span data-stu-id="12259-142">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="12259-143">示例 5：将输出发送到网格视图</span><span class="sxs-lookup"><span data-stu-id="12259-143">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="12259-144">此命令显示如何 `Show-Command` 一起使用和 `Out-GridView` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12259-144">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="12259-145">该命令使用 `Show-Command` cmdlet 打开 cmdlet 的命令窗口 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="12259-145">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="12259-146">单击 " **运行** " 按钮时，该 `Get-ChildItem` 命令将运行并生成输出。</span><span class="sxs-lookup"><span data-stu-id="12259-146">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="12259-147">管道运算符 ( |) 将命令的输出发送 `Get-ChildItem` 到 `Out-GridView` cmdlet，该 cmdlet 将 `Get-ChildItem` 在交互窗口中显示输出。</span><span class="sxs-lookup"><span data-stu-id="12259-147">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="12259-148">示例 6：显示在命令窗口中创建的命令</span><span class="sxs-lookup"><span data-stu-id="12259-148">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="12259-149">此示例显示了你在窗口中创建的命令 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-149">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="12259-150">该命令使用 **PassThru** 参数，该参数 `Show-Command` 在字符串中返回结果。</span><span class="sxs-lookup"><span data-stu-id="12259-150">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="12259-151">例如，如果使用 `Show-Command` 窗口创建一个 `Get-EventLog` 命令，该命令可获取 Windows PowerShell 事件日志中的五个最新事件，然后单击 **"确定**"，则该命令将返回上面所示的输出。</span><span class="sxs-lookup"><span data-stu-id="12259-151">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK**, the command returns the output shown above.</span></span> <span data-ttu-id="12259-152">查看命令字符串可帮助你了解 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="12259-152">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="12259-153">示例 7：将命令保存到变量</span><span class="sxs-lookup"><span data-stu-id="12259-153">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="12259-154">此示例演示如何运行在使用 cmdlet 的 **PassThru** 参数时获取的命令字符串 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-154">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="12259-155">此策略使你可以查看该命令并使用它。</span><span class="sxs-lookup"><span data-stu-id="12259-155">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="12259-156">第一个命令使用 cmdlet 的 **PassThru** 参数 `Show-Command` ，并将命令的结果保存在变量中 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="12259-156">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="12259-157">在这种情况下，我们将使用 `Show-Command` 窗口来创建一个 `Get-EventLog` 命令，用于获取 Windows PowerShell 事件日志中的五个最新事件。</span><span class="sxs-lookup"><span data-stu-id="12259-157">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="12259-158">单击 **"确定**" 后，将 `Show-Command` 返回保存在变量中的命令字符串 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="12259-158">When you click **OK**, `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="12259-159">示例 8：将命令输出保存到变量</span><span class="sxs-lookup"><span data-stu-id="12259-159">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="12259-160">此示例使用 **ErrorPopup** 参数将命令的输出保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="12259-160">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="12259-161">除了在窗口中显示错误以外，**ErrorPopup** 还会将命令输出返回到当前命令，而不是创建新命令。</span><span class="sxs-lookup"><span data-stu-id="12259-161">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="12259-162">运行此命令时，将 `Show-Command` 打开窗口。</span><span class="sxs-lookup"><span data-stu-id="12259-162">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="12259-163">你可以使用窗口功能来设置参数值。</span><span class="sxs-lookup"><span data-stu-id="12259-163">You can use the window features to set parameter values.</span></span> <span data-ttu-id="12259-164">若要运行该命令，请单击窗口中的 " **运行** " 按钮 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-164">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="12259-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12259-165">PARAMETERS</span></span>

### <span data-ttu-id="12259-166">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="12259-166">-ErrorPopup</span></span>

<span data-ttu-id="12259-167">指示除了在命令行中显示错误以外，该 cmdlet 还在弹出窗口中显示错误。</span><span class="sxs-lookup"><span data-stu-id="12259-167">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="12259-168">默认情况下，如果在窗口中运行的命令 `Show-Command` 生成错误，则该错误仅显示在命令行中。</span><span class="sxs-lookup"><span data-stu-id="12259-168">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="12259-169">此外，在使用窗口) 中的 " **运行** " 按钮运行命令 (时 `Show-Command` ， **ErrorPopup** 参数会将命令结果返回到当前命令，而不是运行该命令并将其输出返回到新的命令。</span><span class="sxs-lookup"><span data-stu-id="12259-169">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="12259-170">你可以使用此功能将命令结果保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="12259-170">You can use this feature to save the command results in a variable.</span></span>

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

### <span data-ttu-id="12259-171">-Height</span><span class="sxs-lookup"><span data-stu-id="12259-171">-Height</span></span>

<span data-ttu-id="12259-172">指定窗口的高度 `Show-Command` （以像素为单位）。</span><span class="sxs-lookup"><span data-stu-id="12259-172">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="12259-173">输入一个介于 300 和屏幕分辨率中的像素数之间的值。</span><span class="sxs-lookup"><span data-stu-id="12259-173">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="12259-174">如果值太大而无法在屏幕上显示命令窗口，则会 `Show-Command` 生成错误。</span><span class="sxs-lookup"><span data-stu-id="12259-174">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="12259-175">默认高度为 600 像素。</span><span class="sxs-lookup"><span data-stu-id="12259-175">The default height is 600 pixels.</span></span> <span data-ttu-id="12259-176">对于 `Show-Command` 包含 **Name** 参数的命令，默认高度为300像素。</span><span class="sxs-lookup"><span data-stu-id="12259-176">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12259-177">-Name</span><span class="sxs-lookup"><span data-stu-id="12259-177">-Name</span></span>

<span data-ttu-id="12259-178">为指定的命令显示命令窗口。</span><span class="sxs-lookup"><span data-stu-id="12259-178">Displays a command window for the specified command.</span></span> <span data-ttu-id="12259-179">输入一个命令的名称，例如 cmdlet、函数或 CIM 命令的名称。</span><span class="sxs-lookup"><span data-stu-id="12259-179">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="12259-180">如果省略此参数，则 `Show-Command` 将显示一个命令窗口，该窗口列出计算机上安装的所有模块中的所有 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="12259-180">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12259-181">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="12259-181">-NoCommonParameter</span></span>

<span data-ttu-id="12259-182">指示此 cmdlet 省略命令显示的“通用参数”部分。</span><span class="sxs-lookup"><span data-stu-id="12259-182">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="12259-183">默认情况下，“通用参数”显示在命令窗口底部的可展开部分中。</span><span class="sxs-lookup"><span data-stu-id="12259-183">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

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

### <span data-ttu-id="12259-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12259-184">-PassThru</span></span>

<span data-ttu-id="12259-185">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="12259-185">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="12259-186">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="12259-186">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="12259-187">若要运行命令字符串，请在命令提示符下复制并粘贴它，或将其保存在变量中，然后使用 `Invoke-Expression` cmdlet 来运行变量中的字符串。</span><span class="sxs-lookup"><span data-stu-id="12259-187">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

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

### <span data-ttu-id="12259-188">-Width</span><span class="sxs-lookup"><span data-stu-id="12259-188">-Width</span></span>

<span data-ttu-id="12259-189">指定窗口的宽度 `Show-Command` （以像素为单位）。</span><span class="sxs-lookup"><span data-stu-id="12259-189">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="12259-190">输入一个介于 300 和屏幕分辨率中的像素数之间的值。</span><span class="sxs-lookup"><span data-stu-id="12259-190">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="12259-191">如果值太大而无法在屏幕上显示命令窗口，则会 `Show-Command` 生成错误。</span><span class="sxs-lookup"><span data-stu-id="12259-191">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="12259-192">默认宽度为 300 像素。</span><span class="sxs-lookup"><span data-stu-id="12259-192">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12259-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12259-193">CommonParameters</span></span>

<span data-ttu-id="12259-194">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12259-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12259-195">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12259-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12259-196">输入</span><span class="sxs-lookup"><span data-stu-id="12259-196">INPUTS</span></span>

### <span data-ttu-id="12259-197">无</span><span class="sxs-lookup"><span data-stu-id="12259-197">None</span></span>

<span data-ttu-id="12259-198">不能通过管道将输入传递给 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="12259-198">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="12259-199">输出</span><span class="sxs-lookup"><span data-stu-id="12259-199">OUTPUTS</span></span>

### <span data-ttu-id="12259-200">None、System.object、System.string</span><span class="sxs-lookup"><span data-stu-id="12259-200">None, System.String, System.Object</span></span>

<span data-ttu-id="12259-201">当使用 **PassThru** 参数时，将 `Show-Command` 返回命令字符串。</span><span class="sxs-lookup"><span data-stu-id="12259-201">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="12259-202">使用 **ErrorPopup** 参数时，将 `Show-Command` (任何对象) 返回命令输出。</span><span class="sxs-lookup"><span data-stu-id="12259-202">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="12259-203">否则，不 `Show-Command` 会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="12259-203">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="12259-204">注释</span><span class="sxs-lookup"><span data-stu-id="12259-204">NOTES</span></span>

<span data-ttu-id="12259-205">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="12259-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="12259-206">`Show-Command` 在远程会话中不起作用。</span><span class="sxs-lookup"><span data-stu-id="12259-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="12259-207">相关链接</span><span class="sxs-lookup"><span data-stu-id="12259-207">RELATED LINKS</span></span>
