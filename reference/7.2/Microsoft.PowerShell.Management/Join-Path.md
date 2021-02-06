---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 08107eecce316c3799315b1d91a0e7cdab64579f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596644"
---
# Join-Path

## 摘要
将路径和子路径合并到单个路径中。

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

`Join-Path`Cmdlet 将路径和子路径合并到单个路径中。
提供程序将提供路径分隔符。

## 示例

### 示例1：将路径与子路径组合

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

此命令使用 `Join-Path` 将路径与 childpath 进行组合。

由于命令是从 `FileSystem` 提供程序执行的，因此提供了 `\` 分隔符来联接路径。

### 示例2：合并已包含目录分隔符的路径

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

现有的目录分隔符 `\` 和已处理，因此与之间只有一个分隔符 `Path``ChildPath`

### 示例3：通过将路径与子路径联接来显示文件和文件夹

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

此命令显示通过联接 C:\Win \* 路径和系统子路径而引用的文件和文件夹 \* 。
它显示与相同的文件和文件夹 `Get-ChildItem` ，但它显示每个项目的完全限定路径。
在此命令中， `Path` 省略了和 `ChildPath` 可选的参数名称。

### 示例4：将 Join-Path 与 PowerShell 注册表提供程序一起使用

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

此命令显示注册表子项中包含的注册表项 `HKLM\System` `ControlSet` 。

`Resolve`参数尝试解析联接的路径，包括当前提供程序路径中的通配符`HKLM:\`

### 示例5：将多个路径根与一个子路径组合在一起

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

此命令使用 `Join-Path` 将多个路径根与一个子路径组合在一起。

> [!NOTE]
> 指定的驱动器 `Path` 必须存在，否则该条目的联接将失败。

### 示例6：合并带有子路径的文件系统驱动器的根

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

此命令将控制台中每个 PowerShell 文件系统驱动器的根与 Subdir 子路径组合在一起。

该命令使用 `Get-PSDrive` cmdlet 来获取 FileSystem 提供程序支持的 PowerShell 驱动器。
`ForEach-Object`语句仅选择对象的根属性 `PSDriveInfo` ，并将其与指定的子路径组合在一起。

输出显示计算机上的 PowerShell 驱动器包含映射到 C:\Program Files 目录的驱动器。

### 示例7：合并无数个路径

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

`AdditionalChildPath`参数允许联接无限数量的路径。

在此示例中，不使用任何参数名称，因此 "a" 将绑定到，将 " `Path` b" 绑定到，将 `ChildPath` "c-g" 绑定到 `AdditionalChildPath`

## PARAMETERS

### -AdditionalChildPath

指定要追加到 *Path* 参数值的其他元素。 `ChildPath`参数仍是必需的，并且还必须指定。

此参数是使用属性指定的，该 `ValueFromRemainingArguments` 属性允许联接无限数量的路径。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

指定要追加到参数值的元素 `Path` 。
允许使用通配符。
`ChildPath`参数是必需的，但参数名称 ( "ChildPath" ) 是可选的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Credential

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。
> 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

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

### -Path

指定子路径追加到的主路径。
允许使用通配符。

的值 `Path` 确定哪些提供程序联接路径并添加路径分隔符。
`Path`尽管参数名称 ( "Path" ) 是可选的，但参数是必需的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Resolve

指示此 cmdlet 应尝试解析来自当前提供程序的联接路径。

- 如果使用通配符，则该 cmdlet 将返回与联接路径匹配的所有路径。
- 如果 **不使用通配符，** 则如果路径不存在，则该 cmdlet 将出错。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet。

## 输出

### System.String

此 cmdlet 将返回包含生成的路径的字符串。

## 注释

在路径 cmdlet (包含 Path 名词的 cmdlet) 操作路径名，并以所有 PowerShell 提供程序可解释的简明格式返回名称。 这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。 你可以像使用 Dirname、Normpath、Realpath、Join 或其他路径操作程序那样使用这些 cmdlet。

可以将路径 cmdlet 用于多个提供程序，包括 `FileSystem` 、 `Registry` 和 `Certificate` 提供程序。

此 cmdlet 用于处理由任何提供程序公开的数据。
若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。
有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Convert-Path](Convert-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)

