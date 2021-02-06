---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: afc08b263d75f8a728ce6d64cc7ede0a639df196
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596844"
---
# Trace-Command

## 摘要
配置并启动对指定表达式或命令的跟踪。

## SYNTAX

### expressionSet（默认值）

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### commandSet

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## DESCRIPTION
`Trace-Command`Cmdlet 配置并启动对指定表达式或命令的跟踪。
其工作方式与 Set-TraceSource 相似，但仅适用于指定的命令。

## 示例

### 示例 1：跟踪元数据处理、参数绑定和表达式

此示例启动对表达式的元数据处理、参数绑定以及 cmdlet 创建和析构的跟踪 `Get-Process Notepad` 。

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

它使用 **Name** 参数来指定跟踪源，使用 **Expression** 参数指定命令，并使用 **PSHost** 参数将输出发送到控制台。 由于该命令未指定任何跟踪选项或侦听器选项，因此该命令使用默认值：

- 跟踪选项的所有
- 侦听器选项均无

### 示例 2：跟踪 ParameterBinding 操作

此示例在处理 `Get-Alias` 从管道中获取输入的表达式时，跟踪 PowerShell 的 ParameterBinding 操作的操作。

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

在中 `Trace-Command` ， **InputObject** 参数将对象传递给要在跟踪期间处理的表达式。

第一个命令将字符串存储 `i*` 在 `$A` 变量中。 第二个命令将 `Trace-Command` cmdlet 与 ParameterBinding 跟踪源一起使用。 **PSHost** 参数将输出发送到控制台。

正在处理的表达式为 `Get-Alias $Input` ，其中的 `$Input` 变量与 **InputObject** 参数关联。 **InputObject** 参数将变量传递 `$A` 给表达式。 实际上，在跟踪期间处理的命令是 `Get-Alias -InputObject $A" or "$A | Get-Alias`。

## PARAMETERS

### -ArgumentList

为要跟踪的命令指定参数和参数值。 **ArgumentList** 的别名是 **Args**。 对于调试动态参数，此功能尤其有用。

有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

指定要在跟踪期间处理的命令。

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Debugger

指示 cmdlet 将跟踪输出发送到调试程序。 可以在任何用户模式或内核模式调试程序或者 Visual Studio 中查看输出。 此参数还将选择默认的跟踪侦听器。

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

### -Expression

指定要在跟踪期间处理的表达式。 将表达式括在大括号中， (`{}`) 。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定 cmdlet 将跟踪输出发送到的文件。 此参数还将选择文件跟踪侦听器。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

强制运行命令而不要求用户确认。 与 **FilePath** 参数一起使用。 即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。

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

### -InputObject

为要在跟踪期间处理的表达式指定输入。 可以输入表示表达式接受的输入的变量，或通过管道传递对象。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ListenerOption

向输出中的每条跟踪消息的前缀指定可选数据。 此参数的可接受值为：

- 无
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Callstack

默认值为“无”。

若要指定多个选项，请使用逗号分隔这些选项，但不要带有空格，并将这些选项括在引号中，例如“ProcessID,ThreadID”。

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定所跟踪的 PowerShell 组件的数组。 请输入各个组件的跟踪源的名称。 允许使用通配符。 若要在计算机上查找跟踪源，请键入 `Get-TraceSource`。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Option

确定要跟踪的事件的类型。 此参数的可接受值为：

- 无
- 构造函数
- 释放
- 终结器
- 方法
- 属性
- 委托
- 事件
- 异常
- Lock
- 错误
- 错误
- 警告
- 详细
- WriteLine
- 数据
- 范围
- ExecutionFlow
- Assert
- 全部

默认值为“All”。

以下值是其他值的组合：

- ExecutionFlow：（Constructor、Dispose、Finalizer、Method、Delegates、Events 和 Scope）
- Data：（Constructor、Dispose、Finalizer、Property、Verbose 和 WriteLine）
- Errors：（Error 和 Exception）。

若要指定多个选项，请使用逗号分隔这些选项，但不要带有空格，并将这些选项括在引号中，例如“Constructor,Dispose”。

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

指示 cmdlet 将跟踪输出发送到 PowerShell 主机。 此参数还将选择 PSHost 跟踪侦听器。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将表示表达式输入的对象传递给 `Trace-Command` 。

## 输出

### System.Management.Automation.PSObject

在调试流中返回命令跟踪。

## 注释

- 跟踪是开发人员用于调试和优化程序的一种方法。 在跟踪过程中，程序将生成有关其内部处理过程中每个步骤的详细消息。

- PowerShell 跟踪 cmdlet 专为帮助 PowerShell 开发人员而设计，但是它们可供所有用户使用。 使用这些 cmdlet，你可以监视 shell 功能的几乎每个方面。

- 若要查找为跟踪启用的 PowerShell 组件，请键入 `Get-Help Get-TraceSource` 。

  跟踪源是每个 PowerShell 组件的一部分，用于管理跟踪并为组件生成跟踪消息。 若要跟踪某个组件，你应标识其跟踪源。

  跟踪侦听器接收跟踪的输出并将其显示给用户。 你可以选择将跟踪数据发送到用户模式或内核模式调试程序、主机或控制台、文件或从 **TraceListener** 类派生的自定义侦听器。

- 当你使用 commandSet 参数集时，PowerShell 将处理命令，就像在管道中处理此命令一样。 例如，不对每个传入对象重复执行命令发现。

- **Name**、 **Expression**、 **Option** 和 **Command** 参数的名称是可选的。 如果省略参数名称，则未命名参数值必须按以下顺序出现：Name、Expression、Option 或 Name、Command、Option。 如果包括参数名称，则参数能够以任何顺序出现。

## 相关链接

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)

