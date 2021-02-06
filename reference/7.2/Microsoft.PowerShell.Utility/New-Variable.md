---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: c77eb9c64022d028c3c4b2de6bf4551886b940e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596620"
---
# New-Variable

## 摘要
创建新变量。

## SYNTAX

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**新变量** Cmdlet 在 PowerShell 中创建新变量。
可以在创建变量时为该变量分配值，也可以在创建变量之后再为该变量分配值或更改其值。

可以使用 **New-Variable** 参数设置变量的属性和作用域以及确定变量为公共变量还是私有变量。

通常，通过键入变量名称及其值（如 `$Var = 3`）来创建新变量，但你可以使用 **New-Variable** cmdlet 来使用其参数。

## 示例

### 示例 1：创建一个变量

```
PS C:\> New-Variable days
```

此命令将创建一个名为 days 的新变量。
无需键入 Name 参数。

### 示例 2：创建一个变量并为其分配一个值

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

此命令将创建一个名为 zipcode 的变量，并为其分配值 98033。

### 示例 3：使用 ReadOnly 选项创建一个变量

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

此示例显示了如何使用 **New-Variable** 的 ReadOnly 选项来防止变量被覆盖。

第一个命令将创建一个名为 Max 的新变量，并将其值设置为 256。
它使用值为 ReadOnly 的 Option 参数。

第二个命令尝试创建另一个具有相同名称的变量。
此命令将返回一个错误，因为已在变量上设置只读选项。

第三个命令使用 Force 参数来覆盖该变量上的只读保护。
在此示例中，用于创建具有相同名称的新变量的命令将成功。

### 示例 4：创建一个私有变量

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

此命令演示了模块中的私有变量的行为。
该模块包含 Get-Counter cmdlet，它具有一个名为 Counter 的私有变量。
该命令使用值为 Private 的 Visibility 参数来创建变量。

示例输出显示了私有变量的行为。
已加载该模块的用户无法查看或更改 Counter 变量的值，但可以通过该模块中的命令来读取和更改 Counter 变量。

### 示例5：创建带空格的变量

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

此命令演示如何创建带有空格的变量。
可以使用 " **获取变量** " cmdlet 或直接通过用大括号分隔变量来访问这些变量。

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

### -Force
指示该 cmdlet 创建一个与现有只读变量具有相同名称的变量。

默认情况下，可以覆盖某个变量，除非该变量的选项值为 ReadOnly 或 Constant。
有关详细信息，请参阅 Option 参数。

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

### -Name
指定新变量的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option
指定变量的 **Options** 属性的值。此参数可接受的值包括：

- 无。
不设置任何选项。
（默认值为 None。）
- ReadOnly。
可以删除。
不能更改，除非使用 *Force* 参数。
- Private。
该变量仅在当前作用域中可用。
- AllScope。
变量将复制到创建的所有新作用域中。
- Constant。
无法删除或更改。
Constant 仅在创建变量时才有效。
不能将现有变量的选项更改为 Constant。

若要查看会话中所有变量的 **Options** 属性，请键入 `Get-Variable | Format-Table -Property name, options -autosize`。

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
返回一个代表你所处理的项目的对象。
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

### -Scope
指定新变量的作用域。
此参数的可接受值为：

- 全局。
在全局范围内创建的变量在 PowerShell 进程中的任何位置都是可访问的。
- Local。
本地作用域是指当前作用域，这可以是任何范围，具体取决于上下文。
- 脚本。
在脚本作用域中创建的变量只能在创建它们的脚本文件或模块内访问。
- Private。
在私有范围内创建的变量不能在它们所在的作用域之外访问。
你可以使用 "专用范围" 在另一个范围中创建具有相同名称的项的私有版本。
- 一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父级，2父作用域的父级，依此类推) 。
不能使用负数。

当未指定作用域参数时，Local 为默认作用域。

有关详细信息，请参阅 about_Scopes。

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

### -Value
指定变量初始值。

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
确定变量在创建它的会话之外是否可见。
此参数旨在供传递给其他用户的脚本和命令使用。
此参数的可接受值为：

- Public。
该变量可见。
（默认值为 Public。）
- Private。
该变量不可见。

当变量为私有时，它不会显示在变量的列表（例如，由 Get-Variable 返回的变量）中或 Variable: 驱动器的显示内容中。
用于读取或更改私有变量的值的命令将返回一个错误。
但是，如果已在定义变量的会话中写入可使用私有变量的命令，则用户可以运行这些命令。

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

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

### System.Object
可以通过管道将值传递给 **New-Variable**。

## 输出

### 无或 System.Management.Automation.PSVariable
使用 PassThru 参数时，**New-Variable** 将生成一个表示新变量的 **System.Management.Automation.PSVariable** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

