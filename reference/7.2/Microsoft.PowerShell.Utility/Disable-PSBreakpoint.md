---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2bd1a48d2075950cdb337063a100bf31534ac6fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599066"
---
# Disable-PSBreakpoint

## 摘要
禁用当前控制台中的断点。

## SYNTAX

### Breakpoint（默认值）

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ID

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**Set-psbreakpoint** cmdlet 禁用断点，以确保在脚本运行时不会命中断点。
可使用它来禁用所有断点，或者可通过提交断点对象或断点 ID 来指定断点。

在技术上，该 cmdlet 将断点对象的 Enabled 属性值更改为 False。
若要重新启用断点，请使用 Enable-PSBreakpoint cmdlet。
当使用 Set-PSBreakpoint cmdlet 来创建断点时，将默认启用断点。

断点是脚本中的一个点，将在其中暂时停止执行脚本，从而使你可以检查脚本中的指令。
**Set-psbreakpoint** 是设计用于调试 PowerShell 脚本的多个 cmdlet 之一。
有关 PowerShell 调试器的详细信息，请参阅 about_Debuggers。

## 示例

### 示例1：设置断点并禁用它

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

这些命令禁用新创建的断点。

第一个命令使用 Set-PSBreakpoint cmdlet 在 Sample.ps1 脚本中的 *Name* 变量上创建断点。
然后，它将断点对象保存在 $B 变量中。

第二个命令使用 **set-psbreakpoint** cmdlet 来禁用新断点。
它使用管道运算符 (|) 将 $B 中的断点对象发送到 **set-psbreakpoint** cmdlet。

此命令的结果是，$B 中的断点对象的 Enabled 属性的值为 False。

### 示例2：禁用断点

```
PS C:\> Disable-PSBreakpoint -Id 0
```

此命令禁用断点 ID 为 0 的断点。

### 示例3：创建已禁用的断点

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

此命令创建新断点，在你启用该断点之前，该断点将一直禁用。

它使用 **set-psbreakpoint** cmdlet 禁用断点。
*断点* 参数的值是一个 Set-PSBreakpoint 命令，该命令设置新断点，生成一个断点对象，并将该对象保存在 $B 变量中。

Cmdlet 参数将对象用作值，可接受包含对象的变量或者可获取或生成对象的命令。
在这种情况下，因为 **Set-psbreakpoint 将** 生成一个断点对象，所以它可用作 *断点* 参数的值。

第二个命令在 $B 变量的值中显示断点对象。

### 示例4：禁用当前控制台中的所有断点

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

此命令禁用当前控制台中的所有断点。
可将此命令缩写为：“gbp | dbp”。

## PARAMETERS

### -Breakpoint

指定要禁用的断点。
输入一个包含断点对象的变量，或可获取断点对象的命令（如 Get-PSBreakpoint 命令）。
还可以通过管道将断点对象传递到 **set-psbreakpoint** cmdlet。

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

禁用具有指定断点 ID 的断点。
输入 ID 或包含 ID 的变量。
不能通过管道将 Id 传递到 **set-psbreakpoint**。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

返回表示已启用的断点的对象。
默认情况下，此 cmdlet 将不产生任何输出。

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

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.Breakpoint

可以通过管道将断点对象传递给 **set-psbreakpoint**。

## 输出

### 无或 System.Management.Automation.Breakpoint

当使用 *PassThru* 参数时， **set-psbreakpoint** 将返回一个表示已禁用的断点的对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

