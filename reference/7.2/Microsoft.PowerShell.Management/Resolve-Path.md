---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598474"
---
# Resolve-Path

## 摘要
解析路径中的通配符并显示路径内容。

## SYNTAX

### Path（默认值）

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

`Resolve-Path`Cmdlet 将在指定位置显示与通配符模式匹配的项和容器。 匹配可以包括文件、文件夹、注册表项或可从 New-psdrive 提供程序访问的任何其他对象。

## 示例

### 示例1：解析主文件夹路径

颚化符 (~) 是当前用户的主文件夹的速记表示法。 此示例显示了如何 `Resolve-Path` 返回完全限定的路径值。

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### 示例2：解析 Windows 文件夹的路径

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

从 C：驱动器的根目录运行时，此命令将返回 C：驱动器中 Windows 文件夹的路径。

### 示例3：获取 Windows 文件夹中的所有路径

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

此命令返回 C：\Windows 文件夹中的所有文件夹。 该命令使用管道运算符 (|) 将路径字符串发送到 `Resolve-Path` 。

### 示例4：解析 UNC 路径

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

此命令解析通用命名约定 (UNC) 路径并返回路径中的共享部分。

### 示例5：获取相对路径

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

此命令返回 C: 驱动器根目录中目录的相对路径。

### 示例6：解析包含括号的路径

此示例使用 **LiteralPath** 参数解析测试 \[ xml \] 子文件夹的路径。
使用 **LiteralPath** 会导致将方括号视为普通字符，而不是正则表达式。

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETERS

### -Credential

指定有权执行此操作的用户帐户。
默认为当前用户。

键入用户名（如 User01 或 Domain01\User01）或传递 **PSCredential** 对象。 可以使用 cmdlet 创建 **PSCredential** 对象 `Get-Credential` 。 键入用户名时，此 cmdlet 会提示输入密码。

随 PowerShell 一起安装的任何提供程序都不支持此参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

指定要解析的路径。
**LiteralPath** 参数的值完全按类型使用。
不会将任何字符解释为通配字符。
如果路径包括转义符，请将其括在单引号中。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

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

指定要解析的 PowerShell 路径。
此参数是必需的。
还可以通过管道将路径字符串传递给 `Resolve-Path` 。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Relative

指示此 cmdlet 返回相对路径。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet

## 输出

### PathInfo，System.web. String

返回 **PathInfo** 对象。 如果指定 **相对** 参数，则返回解析的路径的字符串值。

## 注释

这些 `*-Path` cmdlet 适用于 FileSystem、Registry 和 Certificate 提供程序。

`Resolve-Path` 适用于任何提供程序。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_providers](../microsoft.powershell.core/about/about_providers.md)。

`Resolve-Path` 仅解析现有路径。 它无法用于解析尚不存在的位置。

## 相关链接

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

