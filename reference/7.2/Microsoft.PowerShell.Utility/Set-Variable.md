---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 573bb0054b60e8c17b79da72ebc712c6ef5575a5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595641"
---
# Set-Variable

## 摘要
设置变量的值。 如果使用请求的名称的变量不存在，则创建该变量。

## SYNTAX

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Variable`Cmdlet 将值分配给指定的变量或更改当前值。 如果该变量不存在，则该 cmdlet 将创建它。

## 示例

### 示例 1：设置变量并获取其值

这些命令将变量的值设置 `$desc` 为 `A description` ，然后获取该变量的值。

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### 示例 2：设置全局只读变量

此示例将创建一个包含系统上所有进程的全局只读变量，然后显示该变量的所有属性。

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

该命令使用 `Set-Variable` cmdlet 来创建变量。 它使用 **PassThru** 参数来创建表示新变量的对象，并使用管道运算符 (`|`) 将对象传递给 `Format-List` cmdlet。 它使用的 **属性** 参数，其 `Format-List` 值为 all (`*`) ，以显示新创建的变量的所有属性。

值 `(Get-Process)` 括在括号中，以确保在将其存储在变量之前执行。 否则，变量将包含单词 "**get-help**"。

### 示例 3：了解公共与私有变量

此示例演示如何将变量的可见性更改为 `Private` 。 可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

此命令显示了如何将变量的可见性更改为 Private。 可以使用所需权限通过脚本读取和更改此变量，但它对于用户不可见。

## PARAMETERS

### -Description

指定对变量的描述。

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

### -Exclude

指定此 cmdlet 将从操作中排除的项数组。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

允许你创建一个与现有只读变量同名的变量，或更改只读变量的值。

默认情况下，你可以覆盖某个变量，除非该变量的选项值为 `ReadOnly` 或 `Constant` 。 有关详细信息，请参阅 Option 参数。

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

### -Include

指定此 cmdlet 将在操作中包含的项数组。 此参数值使 **Name** 参数有效。 输入一个名称或名称模式，例如 `c*`。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

指定变量名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

指定变量的 **Options** 属性的值。

有效值是：

- `None`：不设置任何选项。 （默认值为“None”。）
- `ReadOnly`：可以删除。 不能更改，除非使用 Force 参数。
- `Constant`：不能删除或更改。 `Constant` 仅当创建变量时才有效。 不能将现有变量的选项更改为 `Constant` 。
- `Private`：该变量仅在当前范围内可用。
- `AllScope`：该变量将复制到任何创建的新作用域。

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回一个表示新变量的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### -Scope

指定变量的作用域。此参数可接受的值包括：

- 全球
- 本地
- Script
- 专用
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）。

默认值为 Local。

有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定变量的值。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Visibility

确定变量在创建它的会话之外是否可见。 此参数旨在供传递给其他用户的脚本和命令使用。

有效值是：

- Public：该变量可见。 （默认值为“Public”。）
- Private：该变量不可见。

当变量为私有时，它不会显示在变量列表中，如由返回的变量 `Get-Variable` 或 **变量：** 驱动器的显示。 用于读取或更改私有变量的值的命令将返回一个错误。 但是，如果已在定义变量的会话中写入可使用私有变量的命令，则用户可以运行这些命令。

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
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

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

### System.Object

可以通过管道将表示变量值的对象传递给 `Set-Variable` 。

## 输出

### 无或 System.Management.Automation.PSVariable

当使用 **PassThru** 参数时，将 `Set-Variable` 生成一个表示新变量或已更改变量的 **system.management.automation.psvariable** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)
