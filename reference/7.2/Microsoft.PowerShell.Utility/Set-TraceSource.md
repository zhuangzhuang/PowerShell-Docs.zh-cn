---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 6e7fd1c6eb3551906b4dd9d947b5e551cd05d30a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598489"
---
# Set-TraceSource

## 摘要
配置、启动和停止 PowerShell 组件的跟踪。

## SYNTAX

### optionsSet（默认值）

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**TraceSource** cmdlet 配置、启动和停止 PowerShell 组件的跟踪。
你可以使用它来指定要跟踪的组件以及将跟踪输出发送到的位置。

## 示例

### 示例1：跟踪 ParameterBinding 组件

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

此命令启动对 PowerShell 的 ParameterBinding 组件的跟踪。
它使用 *Name* 参数来指定跟踪源、使用 *Option* 参数选择 ExecutionFlow 跟踪事件，并使用 *PSHost* 参数选择 PowerShell 主机侦听器，该侦听器会将输出发送到控制台。
*ListenerOption* 参数将 ProcessID 和 TimeStamp 值添加到跟踪消息前缀。

### 示例2：停止跟踪

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

此命令停止跟踪 PowerShell 的 ParameterBinding 组件。
它使用 *Name* 参数来标识要跟踪的组件，并使用 *RemoveListener* 参数来标识跟踪侦听器。

## PARAMETERS

### -Debugger

指示 cmdlet 将跟踪输出发送到调试程序。
可以在任何用户模式或内核模式调试程序或者 Microsoft Visual Studio 中查看输出。
此参数还将选择默认的跟踪侦听器。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定此 cmdlet 将跟踪输出发送到的文件。
此参数还将选择文件跟踪侦听器。
如果使用此参数启动跟踪，请使用 *RemoveFileListener* 参数停止跟踪。

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示该 cmdlet 将覆盖只读文件。
与 *FilePath* 参数一起使用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

向输出中的每条跟踪消息的前缀指定可选数据。
此参数的可接受值为：

- 无
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Callstack

默认值为“None”。

若要指定多个选项，请使用逗号分隔这些选项，但不要带有空格，并将这些选项括在引号中，例如“ProcessID,ThreadID”。

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要跟踪的组件。
请输入各个组件的跟踪源的名称。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Option

指定要跟踪的事件类型。
此参数的可接受值为：

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
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

返回一个代表你所处理的项目的对象。
默认情况下，此 cmdlet 将不产生任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

指示，此 cmdlet 将跟踪输出发送到 PowerShell 主机。
此参数还将选择 PSHost 跟踪侦听器。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

通过删除与指定文件关联的文件跟踪侦听器来停止跟踪。
输入跟踪输出文件的路径和文件名。

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

通过删除跟踪侦听器来停止跟踪。

对 *RemoveListener* 使用以下值：

- 若要删除 PSHost (console) ，请键入 `Host` 。
- 若要删除调试程序，请键入 `Debug` 。
- 若要删除所有跟踪侦听器，请键入 `*` 。

若要删除文件跟踪侦听器，请使用 *RemoveFileListener* 参数。

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
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

### System.String

可以通过管道将包含名称的字符串传递给 **TraceSource**。

## 输出

### 无或 System.Management.Automation.PSTraceSource

当使用 *PassThru* 参数时， **TraceSource 将** 生成一个表示跟踪会话的 **system.management.automation.pstracesource** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

* 跟踪是开发人员用于调试和优化程序的一种方法。 在跟踪过程中，程序将生成有关其内部处理过程中每个步骤的详细消息。

  PowerShell 跟踪 cmdlet 专为帮助 PowerShell 开发人员而设计，但是它们可供所有用户使用。
它们允许你监视 PowerShell 功能的几乎每个方面。

  跟踪源是每个 PowerShell 组件的一部分，用于管理跟踪并为组件生成跟踪消息。
若要跟踪某个组件，你应标识其跟踪源。

  跟踪侦听器接收跟踪的输出并将其显示给用户。
你可以选择将跟踪数据发送给用户模式或内核模式调试程序、控制台、文件或从 **TraceListener** 类派生的自定义侦听器。。

* 若要启动跟踪，请使用 *Name* 参数指定跟踪源、 *FilePath*、 *调试器* 或 *PSHost* 参数，以指定 (输出) 的目标侦听器。 使用 *Options* 参数确定要跟踪的事件类型，并使用 *ListenerOption* 参数配置跟踪输出。
* 若要更改跟踪的配置，请输入 **TraceSource** 命令来启动跟踪。 PowerShell 可识别跟踪源已被跟踪。 它将停止跟踪、添加新配置，然后启动或重新启动该跟踪。
* 若要停止跟踪，请使用 *RemoveListener* 参数。 若要停止使用文件侦听器的跟踪 (使用 *FilePath* 参数) 启动的跟踪，请使用 *RemoveFileListener* 参数。 删除该侦听器后，跟踪将停止。
* 若要确定可以跟踪哪些组件，请使用 Get-TraceSource。 当组件正在使用时，将自动加载每个模块的跟踪源，并且它们显示在 **TraceSource** 的输出中。

## 相关链接

[Get-TraceSource](Get-TraceSource.md)

[Trace-Command](Trace-Command.md)

