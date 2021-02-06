---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: c694e73e69c1e51ecf88f445684923ef5f19113f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598693"
---
# ConvertFrom-Markdown

## 摘要
将字符串或文件的内容转换为 **MarkdownInfo** 对象。

## SYNTAX

### PathParamSet (默认值) 

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 将指定的内容转换为 **MarkdownInfo**。 如果为 **path** 参数指定了文件路径，则会转换文件中的内容。 Output 对象具有三个属性：

- **标记** 属性的抽象语法树 (转换对象的 AST) 
- **Html** 属性具有指定输入的 html 转换
- 如果指定 **AsVT100EncodedString** 参数，则 **VT100ENCODEDSTRING** 属性具有 ANSI (VT100) 转义序列的转换后的字符串

此 cmdlet 是在 PowerShell 6.1 中引入的。

## 示例

### 示例1：将包含 Markdown 内容的文件转换为 HTML

```powershell
ConvertFrom-Markdown -Path .\README.md
```

返回 **MarkdownInfo** 对象。 **标记** 属性包含文件的已转换内容的 AST `README.md` 。 **Html** 属性包含文件的 html 转换内容 `README.md` 。

### 示例2：将包含 Markdown 内容的文件转换为 VT100 编码的字符串

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

返回 **MarkdownInfo** 对象。 **标记** 属性包含文件的已转换内容的 AST `README.md` 。 **VT100EncodedString** 属性具有 FILE 的 VT100 编码的字符串转换后的内容 `README.md` 。

### 示例3：将包含 Markdown 内容的输入对象转换为 VT100 编码的字符串

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

返回 **MarkdownInfo** 对象。 中的 **FileInfo** 对象 `Get-Item` 将转换为 VT100 编码的字符串。 **标记** 属性包含文件的已转换内容的 AST `README.md` 。 **VT100EncodedString** 属性具有 FILE 的 VT100 编码的字符串转换后的内容 `README.md` 。

### 示例4：将包含 Markdown 内容的字符串转换为 VT100 编码的字符串

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

返回 **MarkdownInfo** 对象。 指定的字符串 `**Bold text**` 转换为 VT100 编码的字符串，并在 **VT100EncodedString** 属性中提供。

## PARAMETERS

### -AsVT100EncodedString

指定是否应使用 VT100 转义代码将输出编码为字符串。

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

### -InputObject

指定要转换的对象。 指定 **string 类型的对象时，** 将转换字符串。 如果指定了类型为 **FileInfo** 的对象，则将转换由该对象指定的文件的内容。 任何其他类型的对象都会导致错误。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定要转换的文件的路径。

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要转换的文件的路径。

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

## 输出

### MarkdownRender. MarkdownInfo

## 注释

## 相关链接

[Markdown 分析器](https://github.com/lunet-io/markdig)

[ANSI 转义码](https://wikipedia.org/wiki/ANSI_escape_code)

