---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: fe28f52088a82b93799724de7a7a3f20ce42e36b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598279"
---
# Out-Null

## 摘要
隐藏输出，而不是将其向下发送或显示。

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

**Out** cmdlet 会将其输出发送到 null，实际上，将其从管道中删除并防止输出显示在屏幕上。

## 示例

### 示例1：删除输出

```powershell
Get-ChildItem | Out-Null
```

此命令获取当前位置/目录中的项，但不会通过管道传递或在命令行中显示其输出。
这对于隐藏不需要的输出很有用。

## PARAMETERS

### -InputObject

指定从管道) 中删除 (要发送到 NULL 的对象。
输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

你可以通过管道将任何对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

*  (**out** cmdlet) 包含 **out** 谓词的 cmdlet 没有用于名称或文件路径的参数。 若要将数据发送到 **Out** cmdlet，请使用管道运算符 (|) 将 PowerShell 命令的输出发送到 cmdlet。 还可以将数据存储在变量中，并使用 *InputObject* 参数将数据传递给 cmdlet。 有关详细信息，请参阅示例。
* **Out-Null** 不返回任何输出对象。 如果通过管道将 **Out-Null** 的输出传递给 Get-Member cmdlet，则 **Get-Member** 将报告未指定任何对象。

## 相关链接

[Out-Default](Out-Default.md)

[Out-Host](Out-Host.md)

