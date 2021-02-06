---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: d14e6332a2da5c86c4f8ada0d110c64e080437e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596229"
---
# Show-Markdown

## 摘要
使用 VT100 转义序列或使用 HTML 在浏览器中以友好方式显示控制台中的 Markdown 文件或字符串。

## SYNTAX

### Path（默认值）

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### InputObject

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## DESCRIPTION

`Show-Markdown`Cmdlet 用于在终端或浏览器中以用户可读格式呈现 Markdown。

`Show-Markdown` 如果支持将 VT100 转义序列)  (，则可以返回一个字符串，其中包含终端呈现的 VT100 转义序列。 这主要用于查看终端中的 Markdown 文件。 还可以通过 `ConvertFrom-Markdown` 指定 **AsVT100EncodedString** 参数获取此字符串。

`Show-Markdown` 还可以打开浏览器并显示 Markdown 的呈现版本。 它通过将其转换为 HTML 并在默认浏览器中打开 HTML 文件来呈现 Markdown。

可以 `Show-Markdown` 通过使用更改在终端中呈现 Markdown 的方式 `Set-MarkdownOption` 。

此 cmdlet 是在 PowerShell 6.1 中引入的。

## 示例

### 示例1：指定路径的简单示例

```powershell
Show-Markdown -Path ./README.md
```

### 示例2：指定字符串的简单示例

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### 示例2：在浏览器中打开 Markdown

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETERS

### -InputObject

将显示在终端中的 Markdown 字符串。 如果未传入受支持的格式， `Show-Markdown` 则将发出错误。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定 Markdown 文件的路径。 与 Path 参数不同，LiteralPath 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要呈现的 Markdown 文件的路径。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

将 Markdown 输入编译为 HTML，并在默认浏览器中打开它。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

### System.String[]

## 输出

### System.String

## 注释

## 相关链接

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

