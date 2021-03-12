---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 6b7541fba77c4160cf8d5c2dd36a4bad0bf99c5f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195182"
---
# Clear-Host

## 摘要

清除主机程序中的显示内容。

## SYNTAX

```
Clear-Host [<CommonParameters>]
```

## 说明

`Clear-Host`函数将从当前显示内容中删除所有文本，包括可能已累积的命令和输出。 删除完成后，它将显示命令提示符。 您可以使用函数名称或其别名 `cls` 。

`Clear-Host` 仅影响当前显示。 它不会删除已保存的结果或从会话中删除任何项。 特定于会话的项（例如变量和函数）不会受该函数影响。

由于函数的行为由 `Clear-Host` 主机程序确定，因此 `Clear-Host` 在不同的主机程序中可能会以不同的方式工作。

## 示例

### 示例 1

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

此命令使用的 `cls` 别名 `Clear-Host` 清除当前显示。

## PARAMETERS

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给 `Clear-Host` 。

## 输出

### 无

`Clear-Host` 不会生成任何输出

## 注释

`Clear-Host` 是简单函数，而不是高级函数。 因此，不能在命令中使用通用参数，例如 **Debug** `Clear-Host` 。

## 相关链接

[Get-Host](../Microsoft.PowerShell.Utility/Get-Host.md)

[Out-Host](Out-Host.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)

