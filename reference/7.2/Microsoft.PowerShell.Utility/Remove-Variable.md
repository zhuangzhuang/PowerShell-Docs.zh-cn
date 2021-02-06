---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 6b9d351b5092d96d7698a28d3de63a493d566c6d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597884"
---
# Remove-Variable

## 摘要
删除变量及其值。

## SYNTAX

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-Variable`Cmdlet 从定义变量的作用域中删除变量及其值，如当前会话。 你不能使用此 cmdlet 删除设置为常量或由系统所拥有的变量。

## 示例

### 示例1：删除变量

```powershell
Remove-Variable Smp
```

此命令删除 `$Smp` 变量。

## PARAMETERS

### -Exclude

指定此 cmdlet 从操作中省略的项的数组。 此参数值使 **Name** 参数有效。 请输入名称元素或模式，例如“s*”。 允许使用通配符。

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

指示该 cmdlet 删除变量，即使该变量是只读的。 即使使用 **Force** 参数，cmdlet 也无法删除常量。

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

指定此 cmdlet 在操作中删除的项的数组。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

指定要删除的变量的名称。  (**名称**) 的参数名称是可选的。
允许使用通配符

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

### -Scope

仅获取指定作用域中的变量。 此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）

默认值为 Local。 有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

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

### System.Management.Automation.PSVariable

可以通过管道将变量对象传递给 `Remove-Variable` 。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

- 更改仅影响当前作用域，例如会话。 若要从所有会话中删除某个变量，请将 `Remove-Variable` 命令添加到 PowerShell 配置文件。

- 还可以 `Remove-Variable` 通过其内置别名来引用 `rv` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

## 相关链接

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Set-Variable](Set-Variable.md)
