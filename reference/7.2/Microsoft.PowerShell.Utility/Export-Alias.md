---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 9da204513ed4a17eb8dc20481b878a4a783534f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598458"
---
# Export-Alias

## 摘要
将有关当前定义的别名的信息导出到文件中。

## SYNTAX

### ByPath（默认值）

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Export-Alias`Cmdlet 将当前会话中的别名导出到文件。
如果输出文件不存在，则该 cmdlet 将创建它。

`Export-Alias` 可以导出特定作用域或所有作用域中的别名，它可以生成 CSV 格式的数据，或者作为一系列可添加到会话或 PowerShell 配置文件的 Set-Alias 命令生成数据。

## 示例

### 示例1：导出别名

```powershell
Export-Alias -Path "alias.csv"
```

此命令将当前的别名信息导出到当前目录中名为 Alias.csv 的文件。

### 示例2：除非导出文件已存在，否则导出别名

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

此命令将当前会话中的别名导出到 Alias.csv 文件。

由于指定了 **NoClobber** 参数，因此如果 Alias.csv 文件已存在于当前目录中，则该命令将失败。

### 示例3：将别名追加到文件

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

此命令将当前会话中的别名附加到 Alias.csv 文件。

此命令使用 **description** 参数将描述添加到文件顶部的注释。

该命令还使用 **Force** 参数覆盖任何现有 Alias.csv 文件，即使它们具有只读属性也是如此。

### 示例4：将别名导出为脚本

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

此示例演示如何使用生成的脚本文件格式 `Export-Alias` 。

第一个命令将会话中的别名导出到 Alias.ps1 文件。
它将 **As** 参数与 Script 值一起使用，以生成包含每个别名的 Set-Alias 命令的文件。

第二个命令将 Alias.ps1 文件中的别名添加到 CurrentUser-CurrentHost 配置文件中。
配置文件的路径保存在 `$Profile` 变量中。
该命令使用 `Get-Content` cmdlet 来获取 Alias.ps1 文件中的别名，并使用 `Add-Content` cmdlet 将它们添加到配置文件中。
有关详细信息，请参阅 about_Profiles。

第三个和第四个命令将 Alias.ps1 文件中的别名添加到 Server01 计算机上的远程会话。
第三个命令使用 `New-PSSession` cmdlet 来创建会话。
第四个命令使用 cmdlet 的 **FilePath** 参数 `Invoke-Command` 在新会话中运行 Alias.ps1 文件。

## PARAMETERS

### -Append

指示此 cmdlet 将输出追加到指定的文件，而不是覆盖该文件的现有内容。

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

### -As

指定输出格式。
CSV 是默认值。
此参数的可接受值为：

- CSV
以逗号分隔值 (CSV) 格式。
- 脚本。
`Set-Alias`为每个导出的别名创建一个命令。
如果你使用 .ps1 文件扩展命名输出文件，则可以将它作为脚本运行，以将别名添加到任何会话中。

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定导出文件的说明。
该描述显示为该文件顶部的注释，位于标头信息之后。

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

强制运行命令而不要求用户确认。

即使在文件上设置了只读属性，也将覆盖输出文件。

默认情况下， `Export-Alias` 除非设置了只读或隐藏属性，或者命令中使用了 **NoClobber** 参数，否则，将在不发出警告的情况下覆盖文件。
当命令中同时使用 **NoClobber** 参数时，该参数优先于 **Force** 参数。

**Force** 参数不能强制 `Export-Alias` 覆盖具有隐藏特性的文件。

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

指定输出文件的路径。
与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

将名称指定为要导出的别名的数组。
允许使用通配符。

默认情况下， `Export-Alias` 将导出会话或作用域中的所有别名。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

指示此 cmdlet 防止 `Export-Alias` 覆盖任何文件，即使在该命令中使用了 **Force** 参数也是如此。

如果省略 **NoClobber** 参数，则 `Export-Alias` 将覆盖现有文件而不发出警告，除非在该文件上设置了只读特性。
*NoClobber* 优先于 **Force** 参数，这将允许 `Export-Alias` 使用只读属性覆盖文件。

*NoClobber* 不会阻止 **Append** 参数将内容添加到现有文件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

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

### -Path

指定输出文件的路径。
允许使用通配符，但所得到的路径值必须解析为单个文件名称。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Scope

指定应从其导出别名的作用域。
此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父级) 

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

### 无。

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无或 System.Management.Automation.AliasInfo

当使用 **Passthru** 参数时，将 `Export-Alias` 返回一个表示别名的 **system.management.automation.aliasinfo** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

* 可以仅将别名导出到文件。

## 相关链接

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

