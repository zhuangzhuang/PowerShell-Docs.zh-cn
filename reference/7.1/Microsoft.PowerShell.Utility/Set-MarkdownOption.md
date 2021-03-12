---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-MarkdownOption
ms.openlocfilehash: 5e19dc25d0b10888f6ce2f915926610f0780daf6
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195321"
---
# Set-MarkdownOption

## 摘要
设置用于在控制台中呈现 Markdown 内容的颜色和样式。

## SYNTAX

### IndividualSetting (默认值) 

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### 主题

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### InputObject

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## 说明

设置用于在控制台中呈现 Markdown 内容的颜色和样式。 使用 ANSI 转义代码定义这些样式，这些代码将更改要呈现的 Markdown 文本的颜色和样式。

有关 Markdown 的详细信息，请参阅 [CommonMark](https://commonmark.org/) 网站。

> [!NOTE]
> 设置中使用的字符串值是位于 **转义** 符后面的字符，该字符用于 `[char]0x1B` ANSI 转义序列 () 。 不要在字符串中包含 **转义** 字符。 有关 ANSI 转义代码工作的详细信息，请参阅 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。

## 示例

### 示例 1-切换到浅色主题

此示例选择 **浅** 主题，并使用 **PassThru** 参数显示新配置。

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### 示例 2-自定义颜色和样式设置

此示例更改 Markdown 标头的转义码。 标头的默认配置将其呈现为各种颜色的带下划线的文本。 此更改将删除下划线样式。

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## PARAMETERS

### -BoldForegroundColor

设置用于呈现粗体显示的 Markdown 文本的前景色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -代码

设置在 Markdown 文本中呈现代码块和范围的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header1Color

设置用于在 Markdown 文本中呈现 Header1 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header2Color

设置用于在 Markdown 文本中呈现 .Header2 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header3Color

设置用于在 Markdown 文本中呈现 Header3 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header4Color

设置用于在 Markdown 文本中呈现 Header4 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header5Color

设置用于在 Markdown 文本中呈现 Header5 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header6Color

设置用于在 Markdown 文本中呈现 Header6 块的颜色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImageAltTextForegroundColor

设置用于呈现 Markdown 文本中图像元素的备用文本的前景色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

包含要设置的配置的 **PSMarkdownOptionInfo** 对象。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ItalicsForegroundColor

设置用于呈现 Markdown 文本中斜体的前景色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LinkForegroundColor

设置用于呈现 Markdown 文本中的超链接的前景色。

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

使 cmdlet 输出包含新配置的 **PSMarkdownOptionInfo** 对象。

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

### -主题

选择包含预定义颜色设置的主题。 可能的值为 **深色** 和 **浅色**。

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

## 输出

### MarkdownRender. PSMarkdownOptionInfo

## 注释

用于定义颜色和样式的字符串值必须与正则表达式匹配 `^\[*[0-9;]*?m{1}` 。

## 相关链接

[Get-MarkdownOption](Get-MarkdownOption.md)

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

[Show-Markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)

