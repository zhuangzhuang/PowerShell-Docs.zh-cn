---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "99595808"
---
# Import-PowerShellDataFile

## 摘要
从文件中导入值 `.PSD1` ，而不调用其内容。

## SYNTAX

### ByPath（默认值）

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## DESCRIPTION

`Import-PowerShellDataFile`Cmdlet 从文件中定义的哈希表中安全地导入键值对 `.PSD1` 。 可以使用文件内容导入这些值 `Invoke-Expression` 。
但会 `Invoke-Expression` 运行文件中包含的任何代码。 这可能会产生不需要的结果或执行不安全的代码。 `Import-PowerShellDataFile` 导入数据而不调用代码。 默认情况下，会出现500键限制，但 **SkipLimitCheck** 开关可能会绕过此限制。

## 示例

### 示例1：从 PSD1 检索值

此示例检索存储在存储在文件中的哈希表中的键/值对 `Configuration.psd1` 。 `Get-Content` 用于显示文件的内容 `Configuration.psd1` 。

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETERS

### -LiteralPath

要导入的文件的路径。 路径中的所有字符都被视为文本值。
不处理通配符。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

要导入的文件的路径。 允许使用通配符，但只导入第一个匹配文件。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -SkipLimitCheck

默认情况下， `Import-PowerShellDataFile` 仅从文件中导入500键 `.psd1` 。 使用 **SkipLimitCheck** 导入超过500个键。

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

## 输出

### System.Collections.Hashtable

## 注释

## 相关链接

[Invoke-Expression](Invoke-Expression.md)

[Import-LocalizedData](Import-LocalizedData.md)
