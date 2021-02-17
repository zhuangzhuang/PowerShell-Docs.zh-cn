---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 22ad8a33f80ad5f4d75fe23c0c8f6c845a40d748
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563240"
---
# Set-PSReadLineKeyHandler

## 摘要
将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。

## SYNTAX

### 脚本块

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### 功能

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## DESCRIPTION

`Set-PSReadLineKeyHandler`当按下键或键序列时，该 cmdlet 将自定义结果。 使用用户定义的键绑定，可以在 PowerShell 脚本中执行几乎所有的操作。

## 示例

### 示例1：将箭头键绑定到函数

此命令将向上箭头键绑定到 **HistorySearchBackward** 函数。 此函数搜索命令行中以命令行的当前内容开头的命令行的命令历史记录。

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### 示例2：将密钥绑定到脚本块

此示例演示如何使用单个键来运行命令。 命令将键绑定 `Ctrl+B` 到一个清除行的脚本块，插入 "build" 一词，然后接受该行。

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETERS

### -BriefDescription

键绑定的简短说明。 此说明由 `Get-PSReadLineKeyHandler` cmdlet 显示。

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -弦

要绑定到函数或脚本块的键或键序列。 使用单个字符串指定单个绑定。 如果绑定是键序列，请用逗号分隔键，如以下示例中所示：

`Ctrl+X,Ctrl+L`

> [!NOTE]
> 在 PSReadLine 2.0.0 的情况下， **弦** 参数 **区分大小写**。 意思是， `Ctrl+X` 和 `Ctrl+x` 将创建不同的绑定。

此参数接受字符串数组。 每个字符串都是一个单独的绑定，而不是单个绑定的键序列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定在 cmdlet 的输出中可见的键绑定的更详细说明 `Get-PSReadLineKeyHandler` 。

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Function

指定 PSReadLine 提供的现有密钥处理程序的名称。 此参数使你可以重新绑定现有的键绑定，或绑定当前未绑定的处理程序。

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定输入弦时要运行的脚本块值。 PSReadLine 将一个或两个参数传递给此脚本块。 第一个参数是 **ConsoleKeyInfo** 对象，表示按下的键。 第二个参数可以是任意对象，具体取决于上下文。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

指定绑定应用于哪种 vi 模式。

有效值是：

- Insert
- Command

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[PSReadLineOption](Set-PSReadLineOption.md)
