---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 0381b48097f75d3195a82a67225cd8d6759e7433
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597242"
---
# Clear-Variable

## 摘要
删除变量的值。

## SYNTAX

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**Clear variable** cmdlet 删除存储在变量中的数据，但不删除该变量。
因此，该变量的值为 NULL（空）。
如果该变量具有指定的数据或对象类型，则此 cmdlet 将保留存储在变量中的对象的类型。

## 示例

### 示例1：删除以搜索字符串开头的全局变量的值

```
PS C:\> Clear-Variable my* -Scope Global
```

此命令删除名称以 "my" 开头的全局变量的值。

### 示例2：清除子范围中的变量，而不是父作用域中的变量

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

这些命令演示了清除子作用域中的变量并不会清除父作用域中的值。
第一个命令将变量的值 $A 设置为3。
第二个命令使用调用运算符 ( # A0) 在新的作用域中运行 **明文** 。
在子作用域中清除该变量（尽管它不存在），但不会在本地作用域中清除它。
第三个命令（获取 $A 的值）显示值3不受影响。

### 示例3：删除指定变量的值

```
PS C:\> Clear-Variable -Name "Processes"
```

此命令删除名为进程的变量的值。
Cmdlet 完成操作后，名为 "进程" 的变量仍存在，但值为 null。

## PARAMETERS

### -Exclude

指定此 cmdlet 在操作中省略的项的数组。
此参数值使 *Name* 参数有效。
请输入名称元素或模式，例如“s*”。
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

允许 cmdlet 清除变量，即使该变量是只读的。
即使使用 Force 参数，该 cmdlet 也无法清除常量。

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

### -Include

指定此 cmdlet 将在操作中包含的项数组。
此参数值使 *Name* 参数有效。
请输入名称元素或模式，例如“s*”。
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

### -Name

指定要清除的变量的名称。
允许使用通配符。
此参数为必需参数，但参数名（“名称”）为可选项。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

指定此别名的有效作用域。

此参数的可接受值为：

- 全球
- 本地
- Script

你还可以使用相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父) 。
默认值为 Local。
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

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无或 System.Management.Automation.PSVariable

当使用 *PassThru* 参数时，此 cmdlet 将生成表示已清除变量的 **system.management.automation.psvariable** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

* 若要删除变量及其值，请使用删除 Remove-Variable 或 Remove-Item。

  此 cmdlet 不会删除设置为常量或系统所拥有的变量的值，即使使用 *Force* 参数也是如此。

  如果你清除的变量不存在，则此 cmdlet 无效。
它不会创建具有 null 值的变量。

  还可以通过其内置别名 clv 来引用 **Clear 变量** 。
有关详细信息，请参阅 about_Aliases。

*

## 相关链接

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

