---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: e98de608630a59ff77ca701876986ffb29780a4a
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "99596431"
---
# <span data-ttu-id="66e3a-102">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="66e3a-102">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="66e3a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="66e3a-103">SYNOPSIS</span></span>

<span data-ttu-id="66e3a-104">注册自定义参数其完成注册。</span><span class="sxs-lookup"><span data-stu-id="66e3a-104">Registers a custom argument completer.</span></span>

## <span data-ttu-id="66e3a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="66e3a-105">SYNTAX</span></span>

### <span data-ttu-id="66e3a-106">NativeSet</span><span class="sxs-lookup"><span data-stu-id="66e3a-106">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="66e3a-107">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="66e3a-107">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="66e3a-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="66e3a-108">DESCRIPTION</span></span>

<span data-ttu-id="66e3a-109">`Register-ArgumentCompleter`Cmdlet 将注册自定义参数其完成注册。</span><span class="sxs-lookup"><span data-stu-id="66e3a-109">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="66e3a-110">自变量其完成注册允许你为指定的任何命令在运行时提供动态 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="66e3a-110">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="66e3a-111">示例</span><span class="sxs-lookup"><span data-stu-id="66e3a-111">EXAMPLES</span></span>

### <span data-ttu-id="66e3a-112">示例1：注册自定义参数其完成注册</span><span class="sxs-lookup"><span data-stu-id="66e3a-112">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="66e3a-113">下面的示例为 cmdlet 的 **Id** 参数注册参数其完成注册 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="66e3a-113">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

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

<span data-ttu-id="66e3a-114">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="66e3a-114">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="66e3a-115">在脚本块中，使用 cmdlet 检索 **Id** 的可用值 `Get-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="66e3a-115">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="66e3a-116">每个时区的 **Id** 属性将通过管道传递给 `Where-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66e3a-116">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="66e3a-117">`Where-Object`Cmdlet 筛选出不以提供的值开头的所有 id `$wordToComplete` ，表示用户在按<kbd>Tab 键</kbd>之前键入的文本。如果值包含空格，则筛选的 id 将通过管道传递给 `ForEach-Object` cmdlet，将每个值括在引号中。</span><span class="sxs-lookup"><span data-stu-id="66e3a-117">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `ForEach-Object` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="66e3a-118">第二个命令通过传递 scriptblock、 **ParameterName** **Id** 和 **CommandName** 来注册参数其完成注册 `Set-TimeZone` 。</span><span class="sxs-lookup"><span data-stu-id="66e3a-118">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="66e3a-119">示例2：将详细信息添加到 tab 自动补全值</span><span class="sxs-lookup"><span data-stu-id="66e3a-119">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="66e3a-120">下面的示例将覆盖 cmdlet 的 **Name** 参数的 tab 自动补全 `Stop-Service` ，只返回正在运行的服务。</span><span class="sxs-lookup"><span data-stu-id="66e3a-120">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

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

<span data-ttu-id="66e3a-121">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="66e3a-121">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="66e3a-122">在脚本块中，第一个命令使用 cmdlet 检索所有正在运行 `Where-Object` 的服务。</span><span class="sxs-lookup"><span data-stu-id="66e3a-122">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="66e3a-123">服务通过管道传输到 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66e3a-123">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="66e3a-124">该 `ForEach-Object` cmdlet 将创建一个新的 [CompletionResult](/dotnet/api/system.management.automation.completionresult) 对象，并使用当前服务 (的名称填充该对象 `$_.Name`) 。</span><span class="sxs-lookup"><span data-stu-id="66e3a-124">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="66e3a-125">**CompletionResult** 对象允许你向每个返回的值提供更多详细信息：</span><span class="sxs-lookup"><span data-stu-id="66e3a-125">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="66e3a-126">**completionText** (字符串) -要用作自动完成结果的文本。</span><span class="sxs-lookup"><span data-stu-id="66e3a-126">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="66e3a-127">这是发送到命令的值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-127">This is the value sent to the command.</span></span>
- <span data-ttu-id="66e3a-128">**listItemText** (String) -要在列表中显示的文本，例如当用户按下 <kbd>Ctrl</kbd> + <kbd>空格键</kbd>时。</span><span class="sxs-lookup"><span data-stu-id="66e3a-128">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="66e3a-129">它仅用于显示，并且在选中时不会传递给命令。</span><span class="sxs-lookup"><span data-stu-id="66e3a-129">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="66e3a-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) -完成结果的类型。</span><span class="sxs-lookup"><span data-stu-id="66e3a-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="66e3a-131">**tooltip** (字符串) -具有要显示的有关对象的详细信息的工具提示文本。</span><span class="sxs-lookup"><span data-stu-id="66e3a-131">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="66e3a-132">当用户在按下<kbd>Ctrl 键</kbd>的同时选择某一项时，将显示此选项 + <kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="66e3a-132">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="66e3a-133">最后一个命令演示仍可将停止的服务手动传递到 `Stop-Service` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66e3a-133">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="66e3a-134">选项卡完成是唯一受影响的方面。</span><span class="sxs-lookup"><span data-stu-id="66e3a-134">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="66e3a-135">示例3：注册自定义本机参数其完成注册</span><span class="sxs-lookup"><span data-stu-id="66e3a-135">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="66e3a-136">您可以使用 **本机** 参数为本机命令提供 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="66e3a-136">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="66e3a-137">下面的示例将 `dotnet` (CLI) 的命令行接口的 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="66e3a-137">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="66e3a-138">`dotnet complete`命令仅适用于2.0 版和更高版本的 dotnet cli。</span><span class="sxs-lookup"><span data-stu-id="66e3a-138">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="66e3a-139">第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="66e3a-139">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="66e3a-140">在脚本块中， `dotnet complete` 使用命令执行 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="66e3a-140">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="66e3a-141">结果将通过管道传递给 `ForEach-Object` cmdlet，该 cmdlet 使用 [CompletionResult](/dotnet/api/system.management.automation.completionresult)类的 **新** 静态方法为每个值创建新的 **CompletionResult** 对象。</span><span class="sxs-lookup"><span data-stu-id="66e3a-141">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="66e3a-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="66e3a-142">PARAMETERS</span></span>

### <span data-ttu-id="66e3a-143">-CommandName</span><span class="sxs-lookup"><span data-stu-id="66e3a-143">-CommandName</span></span>

<span data-ttu-id="66e3a-144">以数组形式指定命令的名称。</span><span class="sxs-lookup"><span data-stu-id="66e3a-144">Specifies the name of the commands as an array.</span></span>

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

### <span data-ttu-id="66e3a-145">-Native</span><span class="sxs-lookup"><span data-stu-id="66e3a-145">-Native</span></span>

<span data-ttu-id="66e3a-146">指示参数其完成注册用于本机命令，其中 PowerShell 无法完成参数名称。</span><span class="sxs-lookup"><span data-stu-id="66e3a-146">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

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

### <span data-ttu-id="66e3a-147">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="66e3a-147">-ParameterName</span></span>

<span data-ttu-id="66e3a-148">指定要完成其参数的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="66e3a-148">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="66e3a-149">指定的参数名称不能是枚举值，例如 cmdlet 的 **ForegroundColor** 参数 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="66e3a-149">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="66e3a-150">有关枚举的详细信息，请参阅 [about_Enum](./About/about_Enum.md)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-150">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

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

### <span data-ttu-id="66e3a-151">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="66e3a-151">-ScriptBlock</span></span>

<span data-ttu-id="66e3a-152">指定要运行以执行 tab 自动补全的命令。</span><span class="sxs-lookup"><span data-stu-id="66e3a-152">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="66e3a-153">提供的脚本块应返回完成输入所需的值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-153">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="66e3a-154">脚本块必须使用管道 (`ForEach-Object` 、 `Where-Object` ) 或另一个合适的方法来展开值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-154">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="66e3a-155">返回值数组将导致 PowerShell 将整个数组视为 **一个** 制表符完成值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-155">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="66e3a-156">脚本块必须按下面指定的顺序接受下列参数。</span><span class="sxs-lookup"><span data-stu-id="66e3a-156">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="66e3a-157">参数的名称并不重要，因为 PowerShell 按位置传入值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-157">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="66e3a-158">`$commandName` (位置 0) -此参数设置为脚本块为其提供 tab 自动补全的命令的名称。</span><span class="sxs-lookup"><span data-stu-id="66e3a-158">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="66e3a-159">`$parameterName` (位置 1) -此参数设置为其值需要 tab 自动补全的参数。</span><span class="sxs-lookup"><span data-stu-id="66e3a-159">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="66e3a-160">`$wordToComplete` (位置 2) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-160">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="66e3a-161">`$commandAst` (位置 3) -此参数设置为当前输入行 (AST) 的抽象语法树。</span><span class="sxs-lookup"><span data-stu-id="66e3a-161">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="66e3a-162">有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-162">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="66e3a-163">`$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在用户按 <kbd>Tab</kbd>之前，此参数设置为包含 cmdlet 的的哈希表。有关详细信息，请参阅 [about_Automatic_Variables](./About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-163">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="66e3a-164">指定 **本机** 参数时，脚本块必须按指定顺序采用以下参数。</span><span class="sxs-lookup"><span data-stu-id="66e3a-164">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="66e3a-165">参数的名称并不重要，因为 PowerShell 按位置传入值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-165">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="66e3a-166">`$wordToComplete` (位置 0) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。</span><span class="sxs-lookup"><span data-stu-id="66e3a-166">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="66e3a-167">`$commandAst` (位置 1) -此参数设置为当前输入行 (AST) 的抽象语法树。</span><span class="sxs-lookup"><span data-stu-id="66e3a-167">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="66e3a-168">有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-168">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="66e3a-169">`$cursorPosition` (位置 2) -当用户按下 <kbd>Tab</kbd>时，此参数设置为光标位置。</span><span class="sxs-lookup"><span data-stu-id="66e3a-169">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="66e3a-170">还可以提供 **ArgumentCompleter** 作为参数特性。</span><span class="sxs-lookup"><span data-stu-id="66e3a-170">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="66e3a-171">有关详细信息，请参阅 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-171">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

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

### <span data-ttu-id="66e3a-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66e3a-172">CommonParameters</span></span>

<span data-ttu-id="66e3a-173">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="66e3a-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66e3a-174">有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="66e3a-174">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="66e3a-175">输入</span><span class="sxs-lookup"><span data-stu-id="66e3a-175">INPUTS</span></span>

### <span data-ttu-id="66e3a-176">无</span><span class="sxs-lookup"><span data-stu-id="66e3a-176">None</span></span>

<span data-ttu-id="66e3a-177">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="66e3a-177">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="66e3a-178">输出</span><span class="sxs-lookup"><span data-stu-id="66e3a-178">OUTPUTS</span></span>

### <span data-ttu-id="66e3a-179">无</span><span class="sxs-lookup"><span data-stu-id="66e3a-179">None</span></span>

<span data-ttu-id="66e3a-180">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="66e3a-180">This cmdlet returns no output.</span></span>

## <span data-ttu-id="66e3a-181">注释</span><span class="sxs-lookup"><span data-stu-id="66e3a-181">NOTES</span></span>

## <span data-ttu-id="66e3a-182">相关链接</span><span class="sxs-lookup"><span data-stu-id="66e3a-182">RELATED LINKS</span></span>

