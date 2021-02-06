---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: 646f3e0990ce451300a28ca0de58576c70c55a9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597858"
---
# Import-BinaryMiLog

## 摘要
用于根据导出文件的内容重新创建已保存的对象。

## SYNTAX

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

使用此 cmdlet 可根据创建的导出文件的内容重新创建已保存的对象 `Export-BinaryMILog` 。 此 cmdlet 类似于 `Import-Clixml` ，不同之处在于将 `Export-BinaryMILog` 生成的对象存储在二进制编码的文件中。

## 示例

### 示例 1-还原导出到文件的对象

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## PARAMETERS

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

### 无

## 输出

### System.Object

## 注释

## 相关链接
