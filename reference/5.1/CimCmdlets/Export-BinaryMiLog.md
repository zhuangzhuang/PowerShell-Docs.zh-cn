---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194367"
---
# Export-BinaryMiLog

## 摘要
创建对象或对象的二进制编码表示形式，并将其存储在文件中。

## SYNTAX

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## 说明

`Export-BinaryMILog`Cmdlet 创建对象或对象的基于二进制的表示形式，并将其存储在文件中。 然后，可以使用 `Import-BinaryMiLog` cmdlet 基于该文件的内容重新创建已保存的对象。

此 cmdlet 类似于 `Import-Clixml` ，不同之处在于将 `Export-BinaryMILog` 生成的对象存储在二进制编码的文件中。

## 示例

### 示例 1-创建 CimInstances 的二进制表示形式

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

此命令将 **CimInstances** 导出到 Path 参数所指定的二进制 MI 日志文件。 请参阅 Import-BinaryMiLog 的示例，了解如何通过导入此文件来重新创建 **CimInstances** 。

## PARAMETERS

### -InputObject

指定此 cmdlet 的输入。 可以使用此参数，也可以通过管道传送此 cmdlet 的输入。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path

指定要在其中存储对象的二进制表示形式的文件的路径。 **Path** 参数支持通配符和相对路径。 如果路径解析为多个文件，则此 cmdlet 将生成错误。

```yaml
Type: System.String
Parameter Sets: (All)
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

### Microsoft.Management.Infrastructure.CimInstance

## 输出

### System.Object

## 注释

## 相关链接

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)
