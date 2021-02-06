---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596418"
---
# New-TemporaryFile

## 摘要
创建临时文件。

## SYNTAX

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 创建可以在脚本中使用的临时文件。

`New-TemporaryFile`Cmdlet 将创建一个具有文件扩展名的空文件 `.tmp` 。
此 cmdlet 将文件命名 `tmp<NNNN>.tmp` 为，其中 `<NNNN>` 是一个随机十六进制数。
Cmdlet 将在 **临时** 文件夹中创建文件。

此 cmdlet 使用 [GetTempPath ( # B1](/dotnet/api/system.io.path.gettemppath) 方法查找 **临时** 文件夹。 此方法按以下顺序检查环境变量是否存在，并使用找到的第一个路径：

- 在 Windows 平台上：

  1. TMP 环境变量指定的路径。
  1. 由 TEMP 环境变量指定的路径。
  1. USERPROFILE 环境变量指定的路径。
  1. Windows 目录。

- 在非 Windows 平台上：使用由 TMPDIR 环境变量指定的路径。

## 示例

### 示例 1：创建临时文件

```powershell
$TempFile = New-TemporaryFile
```

此命令会 `.tmp` 在临时文件夹中生成文件，然后在变量中存储对文件的引用 `$TempFile` 。 以后可以在脚本中使用此文件。

## PARAMETERS

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

## 输出

### System.IO.FileInfo

此 cmdlet 返回表示临时文件的 **FileInfo** 对象。

## 注释

## 相关链接

