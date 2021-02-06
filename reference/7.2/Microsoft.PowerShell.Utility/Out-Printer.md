---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-printer
ms.openlocfilehash: f2b3e20685ee52a7f9ca1bfd23af5fc5bca24001
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596646"
---
# Out-printer

## 摘要
将输出发送到打印机。

## SYNTAX

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`Out-Printer`Cmdlet 将输出发送到默认打印机或备用打印机（如果已指定）。

> [!NOTE]
> 此 cmdlet 已在 PowerShell 7 中引入。 此 cmdlet 仅适用于支持 Windows 桌面的 Windows 系统。

## 示例

### 示例 1-发送要在默认打印机上打印的文件

此示例演示如何打印文件，即使没有 `Out-Printer` **路径** 参数。

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content`获取 `readme.txt` 当前目录中文件的内容，并将其传递给 `Out-Printer` 默认打印机。

### 示例2：将字符串打印到远程打印机

此示例将打印 `Hello, World` 到 Server01 上的 **Prt-6b 彩色** 打印机。

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

**Name** 参数选择特定打印机，而不是默认打印机。

### 示例 3-将帮助主题打印到默认打印机

此示例将打印的帮助主题的完整版本 `Get-CimInstance` 。

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` 获取帮助主题的完整版本 `Get-CimInstance` ，并将其存储在变量中 `$H` 。 **InputObject** 参数将值传递 `$H` 给 `Out-Printer` 。

## PARAMETERS

### -InputObject

指定要发送到打印机的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

### -Name

将输出发送到指定打印机。 参数名称 **名称** 是可选的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Out-Printer` 。

## 输出

### 无

`Out-Printer` 不返回任何对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

包含谓词的 cmdlet `Out` 不对对象进行格式设置。 它们只是渲染它们并将其发送到指定的显示目标。 如果将无格式对象发送到 `Out` cmdlet，则该 cmdlet 会在呈现该对象之前将其发送到格式设置 cmdlet。

`Out-Printer` 将数据发送到打印机，但不向管道发出任何输出对象。 如果通过管道将输出传递 `Out-Printer` 给 `Get-Member` ，则会 `Get-Member` 报告未指定任何对象。

## 相关链接

[Out-File](Out-File.md)

[Out-String](Out-String.md)
