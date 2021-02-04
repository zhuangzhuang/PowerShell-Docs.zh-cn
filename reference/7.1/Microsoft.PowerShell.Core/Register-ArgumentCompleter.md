---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 5dc681e39a6d4991c4137d106879df8778d3c1fe
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490629"
---
# <span data-ttu-id="b8325-103">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="b8325-103">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="b8325-104">摘要</span><span class="sxs-lookup"><span data-stu-id="b8325-104">SYNOPSIS</span></span>

<span data-ttu-id="b8325-105">注册自定义参数其完成注册。</span><span class="sxs-lookup"><span data-stu-id="b8325-105">Registers a custom argument completer.</span></span>

## <span data-ttu-id="b8325-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8325-106">SYNTAX</span></span>

### <span data-ttu-id="b8325-107">NativeSet</span><span class="sxs-lookup"><span data-stu-id="b8325-107">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="b8325-108">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="b8325-108">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="b8325-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b8325-109">DESCRIPTION</span></span>

<span data-ttu-id="b8325-110">`Register-ArgumentCompleter`Cmdlet 将注册自定义参数其完成注册。</span><span class="sxs-lookup"><span data-stu-id="b8325-110">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="b8325-111">自变量其完成注册允许你为指定的任何命令在运行时提供动态 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="b8325-111">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="b8325-112">示例</span><span class="sxs-lookup"><span data-stu-id="b8325-112">EXAMPLES</span></span>

### <span data-ttu-id="b8325-113">示例1：注册自定义参数其完成注册</span><span class="sxs-lookup"><span data-stu-id="b8325-113">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="b8325-114">下面的示例为 cmdlet 的 **Id** 参数注册参数其完成注册 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="b8325-114">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="b8325-115">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="b8325-115">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="b8325-116">在脚本块中，使用 cmdlet 检索 **Id** 的可用值 `Get-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="b8325-116">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="b8325-117">每个时区的 **Id** 属性将通过管道传递给 `Where-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8325-117">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="b8325-118">`Where-Object`Cmdlet 筛选出不以提供的值开头的所有 id `$wordToComplete` ，表示用户在按<kbd>Tab 键</kbd>之前键入的文本。如果值包含空格，则筛选的 id 将通过管道传递给 `ForEach-Object` cmdlet，将每个值括在引号中。</span><span class="sxs-lookup"><span data-stu-id="b8325-118">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `ForEach-Object` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="b8325-119">第二个命令通过传递 scriptblock、 **ParameterName** **Id** 和 **CommandName** 来注册参数其完成注册 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="b8325-119">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="b8325-120">示例2：将详细信息添加到 tab 自动补全值</span><span class="sxs-lookup"><span data-stu-id="b8325-120">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="b8325-121">下面的示例将覆盖 cmdlet 的 **Name** 参数的 tab 自动补全 `Stop-Service` ，只返回正在运行的服务。</span><span class="sxs-lookup"><span data-stu-id="b8325-121">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="b8325-122">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="b8325-122">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="b8325-123">在脚本块中，第一个命令使用 cmdlet 检索所有正在运行 `Where-Object` 的服务。</span><span class="sxs-lookup"><span data-stu-id="b8325-123">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="b8325-124">服务通过管道传输到 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8325-124">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="b8325-125">该 `ForEach-Object` cmdlet 将创建一个新的 [CompletionResult](/dotnet/api/system.management.automation.completionresult) 对象，并使用当前服务 (的名称填充该对象 `$_.Name`) 。</span><span class="sxs-lookup"><span data-stu-id="b8325-125">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="b8325-126">**CompletionResult** 对象允许你向每个返回的值提供更多详细信息：</span><span class="sxs-lookup"><span data-stu-id="b8325-126">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="b8325-127">**completionText** (字符串) -要用作自动完成结果的文本。</span><span class="sxs-lookup"><span data-stu-id="b8325-127">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="b8325-128">这是发送到命令的值。</span><span class="sxs-lookup"><span data-stu-id="b8325-128">This is the value sent to the command.</span></span>
- <span data-ttu-id="b8325-129">**listItemText** (String) -要在列表中显示的文本，例如当用户按下 <kbd>Ctrl</kbd> + <kbd>空格键</kbd>时。</span><span class="sxs-lookup"><span data-stu-id="b8325-129">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="b8325-130">它仅用于显示，并且在选中时不会传递给命令。</span><span class="sxs-lookup"><span data-stu-id="b8325-130">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="b8325-131">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) -完成结果的类型。</span><span class="sxs-lookup"><span data-stu-id="b8325-131">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="b8325-132">**tooltip** (字符串) -具有要显示的有关对象的详细信息的工具提示文本。</span><span class="sxs-lookup"><span data-stu-id="b8325-132">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="b8325-133">当用户在按下<kbd>Ctrl 键</kbd>的同时选择某一项时，将显示此选项 + <kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="b8325-133">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="b8325-134">最后一个命令演示仍可将停止的服务手动传递到 `Stop-Service` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8325-134">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="b8325-135">选项卡完成是唯一受影响的方面。</span><span class="sxs-lookup"><span data-stu-id="b8325-135">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="b8325-136">示例3：注册自定义本机参数其完成注册</span><span class="sxs-lookup"><span data-stu-id="b8325-136">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="b8325-137">您可以使用 **本机** 参数为本机命令提供 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="b8325-137">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="b8325-138">下面的示例将 `dotnet` (CLI) 的命令行接口的 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="b8325-138">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="b8325-139">`dotnet complete`命令仅适用于2.0 版和更高版本的 dotnet cli。</span><span class="sxs-lookup"><span data-stu-id="b8325-139">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="b8325-140">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="b8325-140">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="b8325-141">在脚本块中， `dotnet complete` 使用命令执行 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="b8325-141">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="b8325-142">结果将通过管道传递给 `ForEach-Object` cmdlet，该 cmdlet 使用 [CompletionResult](/dotnet/api/system.management.automation.completionresult)类的 **新** 静态方法为每个值创建新的 **CompletionResult** 对象。</span><span class="sxs-lookup"><span data-stu-id="b8325-142">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="b8325-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8325-143">PARAMETERS</span></span>

### <span data-ttu-id="b8325-144">-CommandName</span><span class="sxs-lookup"><span data-stu-id="b8325-144">-CommandName</span></span>

<span data-ttu-id="b8325-145">以数组形式指定命令的名称。</span><span class="sxs-lookup"><span data-stu-id="b8325-145">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8325-146">-Native</span><span class="sxs-lookup"><span data-stu-id="b8325-146">-Native</span></span>

<span data-ttu-id="b8325-147">指示参数其完成注册用于本机命令，其中 PowerShell 无法完成参数名称。</span><span class="sxs-lookup"><span data-stu-id="b8325-147">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8325-148">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="b8325-148">-ParameterName</span></span>

<span data-ttu-id="b8325-149">指定要完成其参数的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="b8325-149">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="b8325-150">指定的参数名称不能是枚举值，例如 cmdlet 的 **ForegroundColor** 参数 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="b8325-150">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="b8325-151">有关枚举的详细信息，请参阅 [about_Enum](./About/about_Enum.md)。</span><span class="sxs-lookup"><span data-stu-id="b8325-151">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8325-152">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="b8325-152">-ScriptBlock</span></span>

<span data-ttu-id="b8325-153">指定要运行以执行 tab 自动补全的命令。</span><span class="sxs-lookup"><span data-stu-id="b8325-153">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="b8325-154">提供的脚本块应返回完成输入所需的值。</span><span class="sxs-lookup"><span data-stu-id="b8325-154">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="b8325-155">脚本块必须使用管道 (`ForEach-Object` 、 `Where-Object` ) 或另一个合适的方法来展开值。</span><span class="sxs-lookup"><span data-stu-id="b8325-155">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="b8325-156">返回值数组将导致 PowerShell 将整个数组视为 **一个** 制表符完成值。</span><span class="sxs-lookup"><span data-stu-id="b8325-156">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="b8325-157">脚本块必须按下面指定的顺序接受下列参数。</span><span class="sxs-lookup"><span data-stu-id="b8325-157">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="b8325-158">参数的名称并不重要，因为 PowerShell 按位置传入值。</span><span class="sxs-lookup"><span data-stu-id="b8325-158">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="b8325-159">`$commandName` (位置 0) -此参数设置为脚本块为其提供 tab 自动补全的命令的名称。</span><span class="sxs-lookup"><span data-stu-id="b8325-159">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="b8325-160">`$parameterName` (位置 1) -此参数设置为其值需要 tab 自动补全的参数。</span><span class="sxs-lookup"><span data-stu-id="b8325-160">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="b8325-161">`$wordToComplete` (位置 2) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。</span><span class="sxs-lookup"><span data-stu-id="b8325-161">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="b8325-162">`$commandAst` (位置 3) -此参数设置为当前输入行 (AST) 的抽象语法树。</span><span class="sxs-lookup"><span data-stu-id="b8325-162">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="b8325-163">有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="b8325-163">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="b8325-164">`$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在用户按 <kbd>Tab</kbd>之前，此参数设置为包含 cmdlet 的的哈希表。有关详细信息，请参阅 [about_Automatic_Variables](./About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b8325-164">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="b8325-165">指定 **本机** 参数时，脚本块必须按指定顺序采用以下参数。</span><span class="sxs-lookup"><span data-stu-id="b8325-165">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="b8325-166">参数的名称并不重要，因为 PowerShell 按位置传入值。</span><span class="sxs-lookup"><span data-stu-id="b8325-166">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="b8325-167">`$wordToComplete` (位置 0) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。</span><span class="sxs-lookup"><span data-stu-id="b8325-167">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="b8325-168">`$commandAst` (位置 1) -此参数设置为当前输入行 (AST) 的抽象语法树。</span><span class="sxs-lookup"><span data-stu-id="b8325-168">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="b8325-169">有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="b8325-169">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="b8325-170">`$cursorPosition` (位置 2) -当用户按下 <kbd>Tab</kbd>时，此参数设置为光标位置。</span><span class="sxs-lookup"><span data-stu-id="b8325-170">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="b8325-171">还可以提供 **ArgumentCompleter** 作为参数特性。</span><span class="sxs-lookup"><span data-stu-id="b8325-171">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="b8325-172">有关详细信息，请参阅 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b8325-172">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8325-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8325-173">CommonParameters</span></span>

<span data-ttu-id="b8325-174">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b8325-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8325-175">有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b8325-175">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b8325-176">输入</span><span class="sxs-lookup"><span data-stu-id="b8325-176">INPUTS</span></span>

### <span data-ttu-id="b8325-177">无</span><span class="sxs-lookup"><span data-stu-id="b8325-177">None</span></span>

<span data-ttu-id="b8325-178">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8325-178">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b8325-179">输出</span><span class="sxs-lookup"><span data-stu-id="b8325-179">OUTPUTS</span></span>

### <span data-ttu-id="b8325-180">无</span><span class="sxs-lookup"><span data-stu-id="b8325-180">None</span></span>

<span data-ttu-id="b8325-181">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="b8325-181">This cmdlet returns no output.</span></span>

## <span data-ttu-id="b8325-182">注释</span><span class="sxs-lookup"><span data-stu-id="b8325-182">NOTES</span></span>

## <span data-ttu-id="b8325-183">相关链接</span><span class="sxs-lookup"><span data-stu-id="b8325-183">RELATED LINKS</span></span>

