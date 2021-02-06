---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597668"
---
# Update-FormatData

## 摘要
更新当前会话中的格式设置数据。

## SYNTAX

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 将格式设置 `Update-FormatData` 文件中的格式设置数据重新加载到当前会话中。 此 cmdlet 允许你更新格式设置数据而无需重新启动 PowerShell。

如果没有参数， `Update-FormatData` 将重新加载它先前加载的格式设置文件。
您可以使用的参数 `Update-FormatData` 将新的格式化文件添加到会话中。

格式设置文件是 XML 格式的文本文件，其 `format.ps1xml` 文件扩展名为。 文件中的格式设置数据定义了会话中 Microsoft .NET Framework 对象的显示。

当 PowerShell 启动时，它会从 PowerShell 源代码加载格式数据。 但是，您可以创建自定义 format.ps1xml 文件，以更新当前会话中的格式设置。 你可以使用 `Update-FormatData` 将格式设置数据重新加载到当前会话中，而无需重新启动 PowerShell。 当你已添加或更改格式设置文件，但不希望中断会话时，这将非常有用。

有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 示例

### 示例 1：重新加载以前加载的格式设置文件

```powershell
Update-FormatData
```

此命令将重新加载它先前加载的格式设置文件。

### 示例 2：重新加载格式设置文件以及跟踪和记录格式设置文件

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

此命令将格式设置文件重新加载到会话中，包括两个新文件：Trace.format.ps1xml 和 Log.format.ps1xml。

由于该命令使用了 AppendPath 参数，因此新文件中的格式设置数据将在内置文件的格式设置数据之后加载。

使用 AppendPath 参数是因为新文件中包含内置文件中未引用的用于对象的格式设置数据。

### 示例 3：编辑格式文件并重新加载它

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

此示例演示如何在编辑格式设置文件之后重新加载该文件。

第一个命令将 NewFiles.format.ps1xml 文件添加到会话。 它使用 PrependPath 参数，因为该文件包含在内置文件中引用的对象的格式设置数据。

在添加 NewFiles.format.ps1xml 文件并在这些会话中对该文件进行测试之后，作者可编辑该文件。

第二个命令使用 `Update-FormatData` cmdlet 来重新加载格式设置文件。 由于之前已加载 NewFiles.format.ps1xml 文件，因此 `Update-FormatData` 会自动重新加载该文件，而不使用参数。

## PARAMETERS

### -AppendPath

指定此 cmdlet 添加到会话的格式设置文件。 在 PowerShell 加载内置的格式设置文件后加载这些文件。

在对 .NET 对象进行格式设置时，PowerShell 将使用它为每个 .NET 类型找到的第一个格式设置定义。 如果使用 **AppendPath** 参数，则 PowerShell 将在遇到你要添加的格式设置数据之前，先从内置文件中搜索数据。

使用此参数可添加一个文件，该文件用于对内置格式设置文件中未引用的 .NET 对象进行格式设置。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

指定此 cmdlet 添加到会话的格式设置文件。 在 PowerShell 加载内置的格式设置文件之前加载这些文件。

在对 .NET 对象进行格式设置时，PowerShell 将使用它为每个 .NET 类型找到的第一个格式设置定义。 如果使用 **PrependPath** 参数，则 PowerShell 将在遇到内置文件中的格式设置数据之前，先从要添加的文件中搜索数据。

使用此参数可添加一个文件，该文件用于对也在内置格式设置文件中引用的 .NET 对象进行格式设置。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含追加路径的字符串传递给 `Update-FormatData` 。

## 输出

### 无

该 cmdlet 不返回任何输出。

## 注释

- `Update-FormatData` 还会更新会话中从模块导入的命令的格式设置数据。 如果模块的格式化文件发生更改，则可以运行 `Update-FormatData` 命令来更新导入命令的格式设置数据。 不需要再次导入该模块。

## 相关链接

[Get-FormatData](Get-FormatData.md)

[Export-FormatData](Export-FormatData.md)
