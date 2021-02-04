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
# Register-ArgumentCompleter

## 摘要

注册自定义参数其完成注册。

## SYNTAX

### NativeSet

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### PowerShellSet

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## DESCRIPTION

`Register-ArgumentCompleter`Cmdlet 将注册自定义参数其完成注册。 自变量其完成注册允许你为指定的任何命令在运行时提供动态 tab 自动补全。

## 示例

### 示例1：注册自定义参数其完成注册

下面的示例为 cmdlet 的 **Id** 参数注册参数其完成注册 `Set-TimeZone` 。

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

第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。

在脚本块中，使用 cmdlet 检索 **Id** 的可用值 `Get-TimeZone` 。 每个时区的 **Id** 属性将通过管道传递给 `Where-Object` cmdlet。 `Where-Object`Cmdlet 筛选出不以提供的值开头的所有 id `$wordToComplete` ，表示用户在按<kbd>Tab 键</kbd>之前键入的文本。如果值包含空格，则筛选的 id 将通过管道传递给 `ForEach-Object` cmdlet，将每个值括在引号中。

第二个命令通过传递 scriptblock、 **ParameterName** **Id** 和 **CommandName** 来注册参数其完成注册 `Set-TimeZone` 。

### 示例2：将详细信息添加到 tab 自动补全值

下面的示例将覆盖 cmdlet 的 **Name** 参数的 tab 自动补全 `Stop-Service` ，只返回正在运行的服务。

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

第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。

在脚本块中，第一个命令使用 cmdlet 检索所有正在运行 `Where-Object` 的服务。 服务通过管道传输到 `ForEach-Object` cmdlet。 该 `ForEach-Object` cmdlet 将创建一个新的 [CompletionResult](/dotnet/api/system.management.automation.completionresult) 对象，并使用当前服务 (的名称填充该对象 `$_.Name`) 。

**CompletionResult** 对象允许你向每个返回的值提供更多详细信息：

- **completionText** (字符串) -要用作自动完成结果的文本。 这是发送到命令的值。
- **listItemText** (String) -要在列表中显示的文本，例如当用户按下 <kbd>Ctrl</kbd> + <kbd>空格键</kbd>时。 它仅用于显示，并且在选中时不会传递给命令。
- **resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) -完成结果的类型。
- **tooltip** (字符串) -具有要显示的有关对象的详细信息的工具提示文本。
  当用户在按下<kbd>Ctrl 键</kbd>的同时选择某一项时，将显示此选项 + <kbd></kbd>。

最后一个命令演示仍可将停止的服务手动传递到 `Stop-Service` cmdlet。 选项卡完成是唯一受影响的方面。

### 示例3：注册自定义本机参数其完成注册

您可以使用 **本机** 参数为本机命令提供 tab 自动补全。 下面的示例将 `dotnet` (CLI) 的命令行接口的 tab 自动补全。

> [!NOTE]
> `dotnet complete`命令仅适用于2.0 版和更高版本的 dotnet cli。

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

第一个命令创建一个脚本块，该脚本块采用用户按 <kbd>Tab</kbd>时传入的必需参数。有关详细信息，请参阅 **ScriptBlock** 参数说明。

在脚本块中， `dotnet complete` 使用命令执行 tab 自动补全。
结果将通过管道传递给 `ForEach-Object` cmdlet，该 cmdlet 使用 [CompletionResult](/dotnet/api/system.management.automation.completionresult)类的 **新** 静态方法为每个值创建新的 **CompletionResult** 对象。

## PARAMETERS

### -CommandName

以数组形式指定命令的名称。

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

### -Native

指示参数其完成注册用于本机命令，其中 PowerShell 无法完成参数名称。

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

### -ParameterName

指定要完成其参数的参数的名称。 指定的参数名称不能是枚举值，例如 cmdlet 的 **ForegroundColor** 参数 `Write-Host` 。

有关枚举的详细信息，请参阅 [about_Enum](./About/about_Enum.md)。

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

### -ScriptBlock

指定要运行以执行 tab 自动补全的命令。 提供的脚本块应返回完成输入所需的值。 脚本块必须使用管道 (`ForEach-Object` 、 `Where-Object` ) 或另一个合适的方法来展开值。 返回值数组将导致 PowerShell 将整个数组视为 **一个** 制表符完成值。

脚本块必须按下面指定的顺序接受下列参数。 参数的名称并不重要，因为 PowerShell 按位置传入值。

- `$commandName` (位置 0) -此参数设置为脚本块为其提供 tab 自动补全的命令的名称。
- `$parameterName` (位置 1) -此参数设置为其值需要 tab 自动补全的参数。
- `$wordToComplete` (位置 2) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。
- `$commandAst` (位置 3) -此参数设置为当前输入行 (AST) 的抽象语法树。 有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。
- `$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在用户按 <kbd>Tab</kbd>之前，此参数设置为包含 cmdlet 的的哈希表。有关详细信息，请参阅 [about_Automatic_Variables](./About/about_Automatic_Variables.md)。

指定 **本机** 参数时，脚本块必须按指定顺序采用以下参数。 参数的名称并不重要，因为 PowerShell 按位置传入值。

- `$wordToComplete` (位置 0) -此参数设置为用户在按 <kbd>Tab 键</kbd>之前提供的值。脚本块应使用此值来确定 tab 填写值。
- `$commandAst` (位置 1) -此参数设置为当前输入行 (AST) 的抽象语法树。 有关详细信息，请参阅 [Ast 类](/dotnet/api/system.management.automation.language.ast)。
- `$cursorPosition` (位置 2) -当用户按下 <kbd>Tab</kbd>时，此参数设置为光标位置。

还可以提供 **ArgumentCompleter** 作为参数特性。 有关详细信息，请参阅 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

## 相关链接

