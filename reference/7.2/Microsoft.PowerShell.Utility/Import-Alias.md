---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 20bc5d141b68cab19374afbe44b3472c72bf69bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596211"
---
# Import-Alias

## 摘要
从文件导入别名列表。

## SYNTAX

### ByPath（默认值）

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Import-Alias`Cmdlet 可从文件导入别名列表。

从 Windows PowerShell 3.0 开始，作为一项安全功能， `Import-Alias` 默认情况下不会覆盖现有别名。
若要覆盖现有别名，应在使用 **Force** 参数之前先确保该别名文件的内容是安全的。

## 示例

### 示例 1：从文件导入别名

```powershell
Import-Alias test.txt
```

此命令从名为 test.txt 的文件中导入别名信息。

## PARAMETERS

### -Force

允许该 cmdlet 导入已定义的或只读形式的别名。
可以使用以下命令显示有关当前定义的别名的信息：

`Get-Alias | Select-Object Name, Options`

如果对应的别名是只读的，则将它显示在 **Options** 属性的值中。

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

### -LiteralPath

指定包含导出的别名信息的文件的路径。
与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。
不会将任何字符解释为通配符。
如果路径包括转义符，请将其括在单引号中。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### -Path

指定包含导出的别名信息的文件的路径。
允许使用通配符，但它们必须解析为单个名称。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Scope

指定别名要导入的作用域。
此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）

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

### System.String

可以通过管道将包含路径的字符串传递给 `Import-Alias` 。

## 输出

### 无或 System.Management.Automation.AliasInfo

当使用 **Passthru** 参数时，将 `Import-Alias` 返回一个表示别名的 **system.management.automation.aliasinfo** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

