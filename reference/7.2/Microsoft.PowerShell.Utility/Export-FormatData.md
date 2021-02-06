---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d42b108d469ed8989628a6c0b4214af4afc0db00
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603584"
---
# Export-FormatData

## 摘要
将当前会话中的格式设置数据保存在格式设置文件中。

## SYNTAX

### ByPath（默认值）

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## DESCRIPTION

`Export-FormatData`Cmdlet 从当前会话中的格式对象 ( # B0 xml) 创建 PowerShell 格式设置文件。 它获取返回的 **ExtendedTypeDefinition** 对象 `Get-FormatData` ，并将其保存到 XML 格式的文件中。

PowerShell 使用 ( # B0 xml) 格式设置文件中的数据来生成会话中 Microsoft .NET 框架对象的默认显示。 你可以查看和编辑这些格式设置文件，并使用 Update-FormatData cmdlet 将格式设置数据添加到会话中。

有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 示例

### 示例1：导出会话格式数据

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

此命令将会话中的所有格式数据导出到 AllFormat.ps1xml 文件中。

该命令使用 `Get-FormatData` cmdlet 来获取会话中的格式数据。 如果为 `*` **TypeName** 参数 (所有) ，则值为，指示该 cmdlet 获取会话中的所有数据。

该命令使用管道运算符 (`|`) 将格式数据从 `Get-FormatData` 命令发送到 `Export-FormatData` cmdlet，后者将格式数据导出到 AllFormat.ps1 文件中。

该 `Export-FormatData` 命令使用 **IncludeScriptBlock** 参数将脚本块包含在文件中的格式数据。

### 示例2：导出类型的格式数据

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

这些命令将 **HelpInfoShort** 类型的格式数据导出到 Help.format.ps1xml 文件。

第一个命令使用 `Get-FormatData` cmdlet 来获取 **HelpInfoShort** 类型的格式数据，并将其保存在 `$F` 变量中。

第二个命令使用 cmdlet 的 **InputObject** 参数 `Export-FormatData` 来输入保存在变量中的格式数据 `$F` 。 它还使用 **IncludeScriptBlock** 参数将脚本块包括在输出中。

### 示例3：在不使用脚本块的情况下导出格式数据

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

此示例演示省略命令中的 **IncludeScriptBlock** 参数的效果 `Export-FormatData` 。

第一个命令使用 `Get-FormatData` cmdlet 来获取 Get-Process cmdlet 返回的 **system.object** 对象的格式数据。 该命令使用管道运算符 (`|`) 将格式设置数据发送到 `Export-FormatData` cmdlet，该 cmdlet 将其导出到当前目录中的 Process.format.ps1xml 文件。

在这种情况下，该 `Export-FormatData` 命令不使用 **IncludeScriptBlock** 参数。

第二个命令使用 `Update-FormatData` cmdlet 将 Process.format.ps1xml 文件添加到当前会话中。 该命令使用 **PrependPath** 参数来确保在进程对象的标准格式设置数据之前找到 Process.format.ps1xml 文件中的进程对象的格式设置数据。

第三个命令显示此更改的效果。 该命令使用 `Get-Process` cmdlet 来获取名称以 P 开头的进程。此输出显示，显示中缺少使用脚本块计算的属性值。

## PARAMETERS

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

### -IncludeScriptBlock

指示是否导出格式数据中的脚本块。

因为脚本块包含代码且可被恶意使用，所以在默认情况下不导出它们。

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

### -InputObject

指定要导出的格式数据对象。 输入包含对象的变量或获取对象的命令（如 `Get-FormatData` 命令）。 还可以通过管道将对象传递 `Get-FormatData` 给 `Export-FormatData` 。

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定输出文件的位置。 与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

指示该 cmdlet 不会覆盖现有文件。 默认情况下， `Export-FormatData` 除非文件具有只读属性，否则将覆盖文件而不发出警告。

若要指示 `Export-FormatData` 覆盖只读文件，请使用 **Force** 参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定输出文件的位置。
输入路径（可选）和具有 format.ps1xml 文件扩展名的文件名。
如果省略路径，则将 `Export-FormatData` 在当前目录中创建文件。

如果使用 types.ps1xml 之外的文件扩展名，则该 `Update-FormatData` cmdlet 将不会识别该文件。

如果指定了现有文件，则将 `Export-FormatData` 覆盖该文件而不发出警告，除非该文件具有只读属性。 若要覆盖只读文件，请使用 **Force** 参数。 若要防止文件被覆盖，请使用 **NoClobber** 参数。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.ExtendedTypeDefinition

可以通过管道将 **ExtendedTypeDefinition** 对象发送 `Get-FormatData` 到 `Export-FormatData` 。

## 输出

### 无

`Export-FormatData` 不返回任何对象。
它将生成一个文件并将其保存在指定的路径中。

## 注释

- 若要使用任何格式设置文件（包括已导出的格式设置文件），会话的执行策略必须允许运行脚本和配置文件。 有关详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。

## 相关链接

[Get-FormatData](Get-FormatData.md)

[Update-FormatData](Update-FormatData.md)
