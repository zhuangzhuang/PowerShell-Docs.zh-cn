---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: d650a9280982703e09ec22698c3848a616abb067
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597445"
---
# Out-Default

## 摘要
将输出发送到默认的格式化程序和默认的输出 cmdlet。

## SYNTAX

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

PowerShell 会自动添加 `Out-Default` 到每个管道的末尾。 `Out-Default` 确定如何格式化和输出对象流。 如果对象流是字符串流，则 `Out-Default` 直接将这些对象传递给 `Out-Host` 调用主机提供的相应 api 的管道。 如果对象流不包含字符串，将 `Out-Default` 检查对象以确定要执行的操作。
首先，它将查看对象类型并确定是否有此对象类型的已注册 _视图_ 。

PowerShell 定义 (cmdlet) 的 XML 架构和机制， `Update-FormatData` 任何人都可以在其中注册对象类型的视图。 您可以为任何对象类型指定 " **宽**"、" **列表**"、" **表**" 或 " **自定义** " 视图。 视图指定要显示的属性以及显示方式。 如果已注册视图，它将定义要使用的格式化程序。 因此，如果已注册的视图是 **表** 视图，则将 `Out-Default` 对象流式传输到 `Format-Table | Out-Host` 。 `Format-Table` 将对象转换为 (由视图) 定义中的数据驱动的格式设置记录流，并 `Out-Host` 将格式设置记录转换为主机接口上的调用。

## 示例

### 示例 1

尽管此 cmdlet 不应由最终用户直接运行，但也可以是。

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETERS

### -InputObject

接受 cmdlet 的输入。

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

### -脚本

确定是否应将输出发送到 PowerShell 的脚本服务。

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

## 输出

## 注释

## 相关链接

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1xml](About/about_Format.ps1xml.md)

[PowerShell 格式设置和输出的实际工作原理](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

