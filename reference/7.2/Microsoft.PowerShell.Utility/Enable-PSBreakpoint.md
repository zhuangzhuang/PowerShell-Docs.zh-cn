---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 28cda7a2fa4435092b647e43a250222a852114b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597457"
---
# Enable-PSBreakpoint

## 摘要
启用当前控制台中的断点。

## SYNTAX

### ID（默认值）

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 断点

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Enable-PSBreakpoint`Cmdlet 可重新启用已禁用的断点。 您可以通过提供断点对象或 Id，使用它来启用所有断点或特定断点。

断点是脚本中的一个点，其中的执行暂时停止，以便您可以检查脚本的状态。 新创建的断点将自动启用，但可以使用禁用 `Disable-PSBreakpoint` 。

在技术上，此 cmdlet 将断点对象的 **Enabled** 属性值更改为 **True**。

`Enable-PSBreakpoint` 是旨在调试 PowerShell 脚本的多个 cmdlet 之一。 有关 PowerShell 调试器的详细信息，请参阅 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。

## 示例

### 示例1：启用所有断点

此示例将启用当前会话中的所有断点。

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

使用别名，此示例可以缩写为 `gbp | ebp` 。

### 示例2：按 ID 启用断点

此示例使用断点 Id 启用多个断点。

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### 示例3：启用已禁用的断点

此示例将重新启用已禁用的断点。

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint` 在脚本中的 **名称** 变量上创建一个断点，该断点将 `Sample.ps1` 断点对象保存在 `$B` 变量中。 **PassThru** 参数显示断点的 **Enabled** 属性的值为 **False**。

`Enable-PSBreakpoint` 重新启用断点。 再次强调，使用 **PassThru** 参数会看到 **Enabled** 属性的值为 **True**。

### 示例4：使用变量启用断点

此示例使用断点对象启用一组断点。

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` 获取断点，并将它们保存在 `$B` 变量中。 使用 **断点** 参数 `Enable-PSBreakpoint` 启用断点。

此示例等效于运行 `Enable-PSBreakpoint -Id 3, 5` 。

## PARAMETERS

### -Breakpoint

指定要启用的断点。 提供一个包含断点的变量或一个可获取断点对象的命令，例如 `Get-PSBreakpoint` 。 还可以通过管道将断点对象传递给 `Enable-PSBreakpoint` 。

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

指定要启用的断点的 **Id** 号。 默认值为所有断点。
按数字或变量提供 **Id** 。 不能通过管道将 **Id** 号传递给 `Enable-PSBreakpoint` 。 若要查找断点的 **Id** ，请使用 `Get-PSBreakpoint` cmdlet。

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

返回一个对象，该对象表示正在启用的断点。 默认情况下，此 cmdlet 不会生成任何输出。

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

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

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

可以通过管道将断点对象传递给 `Enable-PSBreakpoint` 。

## 输出

### 无或 System.Management.Automation.Breakpoint

当使用 **PassThru** 参数时，将 `Enable-PSBreakpoint` 返回一个断点对象，该对象表示已启用的断点。 否则，此 cmdlet 不会生成任何输出。

## 注释

- `Enable-PSBreakpoint`如果尝试启用已启用的断点，则该 cmdlet 不会生成错误。 因此，即使仅有少数断点处于禁用状态，你也可以启用所有断点而不发生错误。

- 使用 cmdlet 创建断点时，会启用断点 `Set-PSBreakpoint` 。 不需要启用新创建的断点。

## 相关链接

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

