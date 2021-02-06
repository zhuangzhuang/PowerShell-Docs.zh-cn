---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: a4cf8970156f524578f7c9747aef1ffbf9f3eb58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598275"
---
# Expand-Archive

## 摘要
 (zipped) 文件从指定的存档中提取文件。

## SYNTAX

### Path（默认值）

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Expand-Archive`Cmdlet 可将指定的压缩存档文件中的文件提取到指定的目标文件夹。 存档文件允许将多个文件打包，还可选择性地将其压缩为单个压缩文件以便分发和存储。

## 示例

### 示例1：提取存档内容

此示例将现有存档文件的内容提取到 **DestinationPath** 参数指定的文件夹中。

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

在此示例中，使用了 **LiteralPath** 参数，因为文件名中包含可解释为通配符的字符。

### 示例2：提取当前文件夹中的存档内容

此示例将当前文件夹中现有存档文件的内容提取到 **DestinationPath** 参数指定的文件夹中。

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETERS

### -DestinationPath

默认情况下，将 `Expand-Archive` 在当前位置创建与 ZIP 文件同名的文件夹。 使用参数可以指定其他文件夹的路径。 如果目标文件夹不存在，则创建它。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

强制运行命令而不要求用户确认。

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

指定存档文件的路径。 与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。 不支持通配符。 如果路径包含转义符，请将每个转义符括在单引号内，以指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

使 cmdlet 输出从存档扩展的文件的列表。

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

指定存档文件的路径。

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

可以通过管道将包含路径的字符串传递给现有存档文件。

## 输出

### FileSystemInfo

`-PassThru`使用参数时，该 cmdlet 将输出从存档扩展的文件的列表。

## 注释

[ZIP 文件规范](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)未指定对包含非 ASCII 字符的文件名进行编码的标准方法。 `Compress-Archive`Cmdlet 使用 utf-8 编码。 其他 ZIP 存档工具可以使用其他编码方案。 当使用不是使用 UTF-8 编码存储的文件名提取文件时， `Expand-Archive` 将使用存档中找到的原始值。 这可能会导致文件名不同于存储在存档中的源文件名。

## 相关链接

[Compress-Archive](compress-archive.md)
