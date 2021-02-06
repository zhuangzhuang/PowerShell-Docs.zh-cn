---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e461c07360b3d9eaf7d9a3c8875d34cd1fc841e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596648"
---
# ConvertTo-Xml

## 摘要
创建对象的基于 XML 的表示形式。

## SYNTAX

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-Xml`Cmdlet 可创建一个或多个更多 .net 对象的[基于 XML](/dotnet/api/system.xml.xmldocument)的表示形式。 若要使用此 cmdlet，请通过管道将一个或多个对象传递给 cmdlet，或使用 **InputObject** 参数来指定对象。

当通过管道将多个对象传递给 `ConvertTo-Xml` 或使用 **InputObject** 参数提交多个对象时，将 `ConvertTo-Xml` 返回一个内存中 XML 文档，其中包含所有对象的表示形式。

此 cmdlet 类似于 [export-clixml](./Export-Clixml.md) ，但前者将 `Export-Clixml` 生成的 XML 存储在 [公共语言基础结构中 (CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 文件，该文件可以重新导入为包含 [export-clixml](./Import-Clixml.md)的对象。 `ConvertTo-Xml` 返回 XML 文档的内存中表示形式，以便您可以继续在 PowerShell 中处理它。 `ConvertTo-Xml` 没有将对象转换为 CLI XML 的选项。

## 示例

### 示例1：将日期转换为 XML

```
PS C:\> Get-Date | ConvertTo-Xml
```

此命令将 **DateTime** 对象) 的当前日期转换为 XML (。

### 示例2：将进程转换为 XML

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

此命令可将表示计算机上所有进程的进程对象转换为一个 XML 文档。 这些对象的级别深度将扩展至三。

## PARAMETERS

### -As

确定输出格式。
此参数的可接受值为：

- 字符串。
返回单个字符串。
- 流。
返回一个字符串数组。
- Document。
返回一个 **xml** 对象。

默认值为 Document。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

指定 XML 表示形式中所包含的包含对象的级别数。 默认值为 1。

例如，如果对象的属性还包含对象，若要保存所包含对象的属性的 XML 表示形式，则必须将深度指定为 2。

可以覆盖 Types.ps1xml 文件中对象类型的默认值。 有关详细信息，请参阅 about_Types.ps1xml。

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

### -InputObject

指定要转换的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 还可以通过管道将对象传递给 **convertto-html**。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

省略对象节点中的 Type 属性。

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

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 **convertto-html**。

## 输出

### System.object 或 System.Xml.Xml文档

*As* 参数的值确定 **convertto-html** 返回的对象的类型。

## 注释

## 相关链接

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Export-Clixml](Export-Clixml.md)

[获取日期](Get-Date.md)

[Import-Clixml](Import-Clixml.md)

