---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 230f027a021017e948c8c53e5e6d0c092127ad85
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603809"
---
# New-FileCatalog

## 摘要
`New-FileCatalog` 创建文件哈希的目录文件，这些文件哈希可用于验证文件的真实性。

## SYNTAX

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`New-FileCatalog` 为一组文件夹和文件创建 [Windows 目录文件](/windows-hardware/drivers/install/catalog-files) 。 此目录文件包含提供的路径中的所有文件的哈希值。 然后，用户可以使用其文件分发目录，以便用户可以验证自目录创建后是否对文件夹进行了任何更改。

支持目录版本 1 和 2。 版本1使用 (弃用) SHA1 哈希算法来创建文件哈希，版本2使用 SHA256。 Windows Server 2008 R2 或 Windows 7 不支持目录版本 2。 你应在 Windows 8、Windows Server 2012 及更高版本的操作系统上使用目录版本 2。

## 示例

### 示例1：为创建文件目录 `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETERS

### -CatalogFilePath

应放置目录文件)  ( 的文件或文件夹的路径。 如果指定了文件夹路径，则 `catalog.cat` 将使用默认文件名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

接受 `1.0` 或 `2.0` 作为指定目录版本的可能值。 `1.0` 应尽可能避免使用，因为它使用不安全的 SHA-1 哈希算法，而 `2.0` 使用 SECURE sha-256 算法，但在 `1.0` Windows 7 和 Server 2008R2 上是唯一受支持的算法。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

接受包含在目录文件中的文件或文件夹的路径或路径的数组。 如果指定了文件夹，将同时包含该文件夹中的所有文件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

管道采用用作目录文件名的字符串。

## 输出

### System.IO.FileInfo

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[Test-FileCatalog](Test-FileCatalog.md)

[立即](/powerShell/module/powershellget)
