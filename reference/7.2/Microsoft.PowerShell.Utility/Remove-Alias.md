---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 0ce13bef77e9ef9647809336aed650833dab51f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596402"
---
# Remove-Alias

## 摘要
删除当前会话中的别名。

## SYNTAX

### Default（默认值）

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## DESCRIPTION

`Remove-Alias`Cmdlet 可从当前 PowerShell 会话中删除别名。 若要删除 **选项** 属性设置为 **ReadOnly** 的别名，请使用 **Force** 参数。

`Remove-Alias`Cmdlet 是在 PowerShell 6.0 中引入的。

## 示例

### 示例 1-删除别名

此示例将删除一个名为 `del` 的别名，该别名表示 `Remove-Item` cmdlet。

```powershell
Remove-Alias -Name del
```

### 示例 2-删除所有非常量的别名

此示例从当前 PowerShell 会话中删除所有别名，但 " **Options** " 属性设置为 " **常量**" 的别名除外。 运行该命令后，可在其他 PowerShell 会话或新的 PowerShell 会话中使用别名。

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` 获取 PowerShell 会话中的所有别名，并沿管道向下发送对象。
`Where-Object` 使用脚本块，自动变量 (`$_`) 和 **选项** 属性表示当前管道对象。 参数 **NE** (不等于) ，则选择未将 **选项** 值设置为 **常量** 的对象。 `Remove-Alias` 使用 **Force** 参数从 PowerShell 会话中删除别名，包括只读别名。

## PARAMETERS

### -Force

指示该 cmdlet 删除别名，包括 **选项** 属性设置为 **ReadOnly** 的别名。 **Force** 参数无法删除 **选项** 属性设置为 **常量** 的别名。

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

### -Name

指定要删除的别名的名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Scope

仅影响指定范围内的别名。 默认作用域为 **本地**。 有关详细信息，请参阅 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)。

此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

可以通过管道将别名对象传递给 **删除别名**。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

更改仅影响当前作用域。 若要从所有会话中删除别名，请将一个 **删除别名** 命令添加到 PowerShell 配置文件中。

有关详细信息，请参阅 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)。

## 相关链接

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

