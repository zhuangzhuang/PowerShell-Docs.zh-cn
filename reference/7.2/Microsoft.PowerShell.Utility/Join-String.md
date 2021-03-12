---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: 96f4385c899a50a361fb6df55b40d1ce77225a5b
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196299"
---
# Join-String

## 摘要
将管道中的对象合并为一个字符串。

## SYNTAX

### Default（默认值）

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### 格式

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## 说明

`Join-String`Cmdlet 将管道对象中的文本联接或组合成单个字符串。

如果未指定任何参数，则管道对象将转换为字符串，并使用默认分隔符进行联接 `$OFS` 。

通过指定属性名称，将属性的值转换为字符串，并将其联接到字符串中。

可以使用脚本块，而不是属性名称。 脚本块的结果在联接之前将转换为字符串，以形成结果。 它可以将对象的属性的文本或已转换为字符串的对象的结果合并在一起。

此 cmdlet 是在 PowerShell 6.2 中引入的。

## 示例

### 示例1：联接目录名称

<!-- markdownlint-disable MD038 -->
此示例将目录名称连接起来，用双引号将输出进行包装，并使用逗号和空格分隔目录名称 (`, `) 。 输出是一个字符串对象。

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem` 使用 **Directory** 参数获取驱动器的所有目录名称 `C:\` 。
对象将向下发送到 `Join-String` 。 **Property** 参数指定目录名称。 **DoubleQuote** 参数将目录名称用双引号引起来。
**Separator** 参数指定使用逗号和空格 (`, `) 分隔目录名称。

`Get-ChildItem`对象为 **DirectoryInfo** ，并 `Join-String` 将对象转换为 **system.string**。

### 示例2：使用属性子字符串来联接目录名称

此示例使用 substring 方法获取目录名称的前四个字母，将输出包装在单引号内，并用分号分隔目录名称 (`;`) 。

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem` 使用 **Directory** 参数获取驱动器的所有目录名称 `C:\` 。
对象将向下发送到 `Join-String` 。

**属性** 参数脚本块使用自动变量 (`$_`) 来指定每个对象的 **Name** 属性子字符串。 子字符串获取每个目录名称的前四个字母。 子字符串指定字符的开始位置和结束位置。 **SingleQuote** 参数将目录名称用单引号引起来。 **Separator** 参数指定使用分号 (`;`) 来分隔目录名称。

有关自动变量和子字符串的详细信息，请参阅 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 和 [Substring](/dotnet/api/system.string.substring)。

### 示例3：在单独的行上显示联接输出

此示例将服务名称与每个服务联接在单独的行上，并通过选项卡进行缩进。

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` 将 **Name** 参数与结合使用来指定以开头的服务 `se*` 。 星号 (`*`) 是任何字符的通配符。

对象通过管道向下发送 `Join-String` ，后者使用 **Property** 参数来指定服务名称。 **Separator** 参数指定三个特殊字符，这些字符表示 (`` `r ``) 、换行符 (`` `n ``) 和制表符 () 的回车符 `` `t `` 。 **OutputPrefix** 插入标签 **服务：** 在输出的第一行之前添加新行和制表符。

有关特殊字符的详细信息，请参阅 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)。

### 示例4：从对象创建类定义

此示例使用现有对象作为模板生成 PowerShell 类定义。

此代码示例使用展开缩短行长度，提高可读性。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETERS

### -DoubleQuote

用双引号将每个管道对象的字符串值括起来。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -格式字符串

指定如何设置每个项的格式的格式字符串。

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要联接的文本。 输入包含文本的变量，或键入获取要联接到字符串中的对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

在输出字符串之前插入的文本。 字符串可以包含特殊字符，如回车符 (`` `r ``) 、换行符 (`` `n ``) 和制表符 (`` `t ``) 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

追加到输出字符串的文本。 字符串可以包含特殊字符，如回车符 (`` `r ``) 、换行符 (`` `n ``) 和制表符 (`` `t ``) 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

将管道对象投影到文本的属性名称或属性表达式。

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Separator

在每个管道对象的文本之间插入的文本或字符，如逗号或分号。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

用单引号将每个管道对象的字符串值包装。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

将当前区域性的列表分隔符用作项分隔符。 若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

## 输出

### System.String

## 注释

## 相关链接

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[个子](/dotnet/api/system.string.substring)

