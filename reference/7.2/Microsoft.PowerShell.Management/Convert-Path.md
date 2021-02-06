---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 3d39ea9498cec2669fa075d4630b7691671fea32
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596637"
---
# Convert-Path

## 摘要
将路径从 PowerShell 路径转换为 PowerShell 提供程序路径。

## SYNTAX

### Path（默认值）

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## DESCRIPTION

`Convert-Path`Cmdlet 可将路径从 powershell 路径转换为 powershell 提供程序路径。

## 示例

### 示例 1：将工作目录转换为标准文件系统路径

此示例将当前工作目录（由点 (`.`) 表示）转换为标准文件系统路径。

```
PS C:\> Convert-Path .
C:\
```

### 示例 2：将提供程序路径转换为标准注册表路径

此示例将 PowerShell 提供程序路径转换为标准的注册表路径。

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### 示例 3：将路径转换为字符串

此示例将当前提供程序（FileSystem 提供程序）主目录的路径转换为字符串。

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETERS

### -LiteralPath

指定要转换的路径（作为一个字符串数组）。 **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

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

指定要转换的 PowerShell 路径。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将路径（但不是文本路径）传递给此 cmdlet。

## 输出

### System.String

此 cmdlet 返回一个包含已转换的路径的字符串。

## 注释

包含 Path 名词的 cmdlet 操作路径名称，并以所有 PowerShell 提供程序可解释的简明格式返回名称。 这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。 像使用 **Dirname**、 **Normpath**、 **Realpath**、 **Join** 或其他路径操控器一样使用它们。

可以将路径 cmdlet 与某些提供程序一起使用，包括 FileSystem、Registry 和 Certificate 提供程序。

此 cmdlet 用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

`Convert-Path` 仅转换现有路径。 它不能用于转换尚不存在的位置。

## 相关链接

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

