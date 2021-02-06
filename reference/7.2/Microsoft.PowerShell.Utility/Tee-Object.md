---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598467"
---
# Tee-Object

## 摘要
将命令输出保存在文件或变量中，同时通过管道向下发送。

## SYNTAX

### File（默认值）

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### 变量

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## DESCRIPTION

`Tee-Object`Cmdlet 将重定向输出，即它以两个方向发送命令的输出 (如字母 T) 。 它将输出存储在文件或变量中，同时通过管道向下发送。 如果 `Tee-Object` 是管道中的最后一个命令，则命令输出将显示在提示符处。

## 示例

### 示例1：向文件和控制台输出进程

此示例获取计算机上运行的进程的列表，并将结果发送到文件。
由于未指定第二个路径，因此进程也会显示在控制台中。

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### 示例2：将进程输出到变量并 `Select-Object`

此示例获取在计算机上运行的进程的列表，将其保存到 `$proc` 变量，然后将其传递给 `Select-Object` 。

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

`Select-Object`Cmdlet 将选择 **ProcessName** 并 **处理** 属性。 请注意， `$proc` 变量包括返回的默认信息 `Get-Process` 。

### 示例3：将系统文件输出到两个日志文件

此示例将系统文件的列表保存在两个日志文件中，即累计文件和当前文件。

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

该命令使用 `Get-ChildItem` cmdlet 对 D：驱动器上的系统文件执行递归搜索。 管道运算符 (|) 会将列表发送到 `Tee-Object` ，后者会将列表追加到 AllSystemFiles.txt 文件，并将该列表向下传递到 `Out-File` cmdlet，这会将列表保存在 NewSystemFiles.txt 文件中。

## PARAMETERS

### -Append

指示 cmdlet 将输出追加到指定的文件。 在没有此参数的情况下，新内容将替换文件中的所有现有内容，而不显示警告。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定一个文件，此 cmdlet 允许将对象保存到通配符，但必须解析为单个文件。

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

指定要保存和显示的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 还可以通过管道将对象传递给 `Tee-Object` 。

当你将 **inputobject** 参数与一起使用时 `Tee-Object` ， `Tee-Object` **inputobject** 值将被视为单个对象（即使该值是集合）。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定此 cmdlet 将对象保存到的文件。 与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定该 cmdlet 将对象保存到的变量。 输入一个变量名称，其中不含前面的美元符号 (`$`) 。

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将对象传递给 `Tee-Object` 。

## 输出

### System.Management.Automation.PSObject

`Tee-Object` 返回它重定向的对象。

## 注释

你还可以使用 `Out-File` cmdlet 或重定向运算符，这两个运算符都将输出保存在文件中，但不会向下发送管道。

从 PowerShell 6 开始，在 `Tee-Object` 写入文件时，使用不带 BOM 的 utf-8 编码。 如果需要其他编码，请将 `Out-File` cmdlet 与 **encoding** 参数一起使用。

## 相关链接

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

