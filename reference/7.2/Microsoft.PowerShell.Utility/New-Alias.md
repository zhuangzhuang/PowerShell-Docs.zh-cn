---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 7f226af3cb221543cdae88930f661e2343d954b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603814"
---
# New-Alias

## 摘要
创建新别名。

## SYNTAX

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**新别名** cmdlet 在当前 PowerShell 会话中创建新别名。
退出会话或关闭 PowerShell 后，不会保存使用 **新别名** 创建的别名。
可以使用 Export-Alias cmdlet 来将你的别名信息保存到文件。
以后可以使用 **Import-Alias** 来检索已保存的别名信息。

## 示例

### 示例 1：创建 cmdlet 的别名

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

此命令创建名为“List”的别名来表示 Get-ChildItem cmdlet。

### 示例 2：创建 cmdlet 的只读别名

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

此命令创建名为 W 的别名来表示 Get-WMIObject cmdlet。
它为该别名创建了说明、快速 wmi 别名，并使其只读。
该命令的最后一行使用 Get-Alias 来获取新别名，并通过管道将其传递给 Format-List 以显示有关它的所有信息。

## PARAMETERS

### -Description

指定对别名的描述。
你可以键入任意字符串。
如果描述包含空格，则请将其括在引号中。

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

如果命名的别名已存在，则指示该 cmdlet 用作 Set-Alias。

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

指定新的别名。
可以在别名中使用任何字母数字字符，但第一个字符不能为数字。

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

指定别名的 **Options** 属性的值。
有效值是：

- 无：别名没有 (默认值的约束) 
- ReadOnly：可以删除别名，但不能对其进行更改，除非使用 **Force** 参数
- 常量：别名不能删除或更改
- Private：别名仅在当前作用域内可用
- AllScope：将别名复制到任何创建的新作用域
- 未指定：未指定选项

若要查看会话中所有别名的 **Options** 属性，请键入 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 。

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
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

指定新别名的范围。
此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）。

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

### -Value

指定作为别名的 cmdlet 或命令元素的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
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

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### 无或 System.Management.Automation.AliasInfo

使用 Passthru 参数时，**New-Alias** 将生成表示新别名的 **System.Management.Automation.AliasInfo** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

* 若要创建新别名，请使用 `Set-Alias` 或 `New-Alias` 。 若要更改别名，请使用 `Set-Alias` 。 若要删除别名，请使用 `Remove-Item` 。

## 相关链接

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[Set-Alias](Set-Alias.md)

