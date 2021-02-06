---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 1b465779f56c6bd71d7adfa7ffb5b391f5402656
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603417"
---
# Clear-History

## 摘要
从 PowerShell 会话命令历史记录中删除条目。

## SYNTAX

### IDParameter (默认值) 

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## DESCRIPTION

`Clear-History` 从 PowerShell 会话中删除命令历史记录。 每个 PowerShell 会话都有自己的命令历史记录。 若要显示命令历史记录，请使用 `Get-History` cmdlet。

默认情况下， `Clear-History` 从 PowerShell 会话中删除整个命令历史记录。 可以使用参数 `Clear-History` 来删除选定的命令。

`Clear-History` 不清除 `PSReadLine` 命令历史记录文件。 该 `PSReadLine` 模块存储包含每个 powershell 会话中每个 powershell 命令的历史文件。 在 PowerShell 提示符下，使用键盘上的向上键和向下键滚动浏览命令历史记录。 若要显示 `PSReadLine` 命令历史记录的配置，请使用 `Get-PSReadLineOption` 。
`PSReadLine` 随附 PowerShell 5.0 和更高版本。 有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 示例

### 示例1：从 PowerShell 会话中删除命令历史记录

此命令从 PowerShell 会话的历史记录中删除所有命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。 `Clear-History` 删除整个命令历史记录。 `Get-History` 显示更新的命令历史记录，并确认之前的历史记录已删除。

### 示例2：删除最新命令

此命令使用 **Count** 和 **最新** 参数从 PowerShell 会话的历史记录中删除最新的命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。 `Clear-History` 用于删除命令历史记录。 **Count** 参数指定要删除的命令数，包括指定的 **Id**。**最新** 参数指定从历史记录中清除最新的命令。 `Get-History`显示更新的命令历史记录，并确认已删除5个最新命令（ **id 6**  -  **id 10**）。

### 示例3：删除符合特定条件的命令

此命令删除与命令 **行** 参数所定义的特定条件匹配的命令。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。 `Clear-History` 删除命令历史记录。 **命令行** 参数指定包含 "**帮助**" 或 "以 **语法** 结尾" 的命令。 `Get-History` 显示更新的命令历史记录，并确认已删除命令 **Id 3**、 **id 5**、 **id 6** 和 **id 7** 。

### 示例4：按 Id 号删除命令

此命令删除使用 **Id** 的特定历史记录项。若要删除多个命令，请提交一个逗号分隔列表，其中列出了 **Id** 号。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。 `Clear-History` 删除命令历史记录。 **Id** 参数指定要删除的命令。 `Get-History` 显示更新的命令历史记录，并确认已删除 **id 3** 和 **id 5** 。

### 示例5：按 Id 号和计数删除命令

此命令使用 **Id** 和 **Count** 参数来删除命令历史记录。 命令从指定的 **Id** 按相反顺序从最新到最旧的顺序删除。

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

`Get-History`Cmdlet 将显示 PowerShell 会话的历史记录。 `Clear-History` 删除命令历史记录。 **Id** 参数指定以 **id 7** 开头。 **Count** 参数指定删除包含指定 **Id** 的五个命令。`Get-History`显示更新的命令历史记录，并确认已删除5个命令， **id 3**  -  **id 7**。

## PARAMETERS

### -命令行

从 PowerShell 会话中删除命令历史记录。 字符串必须是完全匹配项，或者使用通配符匹配显示的 PowerShell 会话历史记录中的命令 `Get-History` 。 如果输入多个字符串，则会 `Clear-History` 删除与任何字符串匹配的命令。 **命令行** 参数可与 **Count** 一起使用。

对于带有空格的字符串，请使用单引号。 有关详细信息，请参阅 [about_Quoting_Rules](About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Count

指定要删除的历史记录条目数 `Clear-History` 。 从历史记录中最旧的条目开始，按顺序删除命令。

**Count** 和 **Id** 参数可以一起使用。 **Count** 参数指定要删除的命令数，包括指定的 **Id**。从指定的 **Id** 开始，将按顺序反向删除命令。 例如，如果 **Id** 为30， **计数** 为10，则 `Clear-History` 删除项目21到30。

**Count** 和 **命令行** 参数可以一起使用。 **计数** 指定与 **命令行** 参数值匹配的要删除的命令数。 命令按顺序删除。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定要删除的命令历史记录 **Id** `Clear-History` 。 若要显示 **Id** 号，请使用 `Get-History` cmdlet。 **Id** 号是连续的，命令在 PowerShell 会话中保留其 **Id** 号。 **Id** 参数可用于 **计数** 和 **最新**。

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Newest

使用 **最新** 的参数时，会 `Clear-History` 删除历史记录中的最新条目。 默认情况下，会 `Clear-History` 删除历史记录中最旧的条目。

**最新** 参数可以与 **Id** 和 **计数** 一起使用。 **Count** 参数指定要删除的命令数，包括指定的 **Id**。从指定的 **Id** 开始，按顺序删除命令。 例如，如果 **Id** 为30， **计数** 为10，则会 `Clear-History` 删除30到39项。

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

提示你在运行 cmdlet 之前进行确认 `Clear-History` 。

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

显示在 cmdlet 运行时将发生 `Clear-History` 的情况。 此 cmdlet 未运行。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### 无

不能通过管道将对象传递给 `Clear-History` 。

## 输出

### 无

`Clear-History` 不会生成任何输出。

## 注释

PowerShell 会话历史记录是在 PowerShell 会话期间输入的命令的列表。 可以查看历史记录、添加和删除命令以及运行历史记录中的命令。 有关详细信息，请参阅 [about_History](About/about_History.md)。

会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。
在加载 **PSReadLine** 的会话中提供两个历史记录。 此 cmdlet 仅适用于会话历史记录。 有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 相关链接

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Add-History](Add-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)

