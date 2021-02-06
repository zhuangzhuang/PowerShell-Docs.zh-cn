---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: a56b9041c0ae70def7df619f2a4d265cb631fe7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595383"
---
# Remove-PSBreakpoint

## 摘要
从当前控制台中删除断点。

## SYNTAX

### Breakpoint（默认值）

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ID

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Remove-PSBreakpoint** cmdlet 可删除断点。
输入一个断点对象或断点 ID。

当你删除断点时，断点对象将不再可用或无法正常工作。
如果你已将断点对象保存在变量中，则引用仍然存在，但该断点无法正常工作。

**Set-psbreakpoint** 是设计用于调试 PowerShell 脚本的多个 cmdlet 之一。
有关 PowerShell 调试器的详细信息，请参阅 about_Debuggers。

## 示例

### 示例 1：删除所有断点

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

此命令将删除当前控制台中的所有断点。

### 示例 2：删除指定断点

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

此命令将删除断点。

第一个命令使用 Set-PSBreakpoint cmdlet 在 Sample.ps1 脚本中的 Name 变量上创建断点。
然后，它将断点对象保存在 $B 变量中。

第二个命令使用 **Remove-PSBreakpoint** cmdlet 删除新断点。
它使用管道运算符 (|) 将 $B 变量中的断点对象发送到 **Remove-PSBreakpoint** cmdlet。

此命令的结果是：如果你运行该脚本，则它将一直运行直至完成。
此外，**Get-PSBreakpoint** 不会返回此断点。

### 示例 3：按 ID 删除断点

```
PS C:\> Remove-PSBreakpoint -Id 2
```

此命令将删除断点 ID 为 2 的断点。

### 示例 4：使用函数删除所有断点

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

此简单函数将删除当前控制台中的所有断点。
它使用 Get-PSBreakpoint 来获取这些断点。
然后，它使用管道运算符 (|) 将这些断点发送到 **Remove-PSBreakpoint** cmdlet，后者再将删除它们。

因此，你可以输入 `del-psb`，而不是输入更长的命令。

若要保存该函数，请将其添加到 PowerShell 配置文件中。

## PARAMETERS

### -Breakpoint
指定要删除的断点。
输入一个包含断点对象的变量，或可获取断点对象的命令（如 **Get-PSBreakpoint** 命令）。
你还可以通过管道将断点对象传递给 **Remove-PSBreakpoint**。

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
指定此 cmdlet 为其删除断点的断点 ID。

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
可以通过管道将断点对象传递给 **Remove-PSBreakpoint**。

## 输出

### 无
该 cmdlet 不生成任何输出。

## 注释

## 相关链接

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

