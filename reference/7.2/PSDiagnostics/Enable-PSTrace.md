---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596222"
---
# Enable-PSTrace

## 摘要
启用 Microsoft Windows PowerShell 事件提供程序日志。

## SYNTAX

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 将启用 Microsoft Windows PowerShell 事件提供程序的操作和分析事件日志。

必须从提升的 PowerShell 会话中运行此 cmdlet。

## 示例

### 示例1：为 PowerShell 启用分析事件日志

下面的示例仅启用 Microsoft Windows PowerShell 提供程序的分析事件日志。

```powershell
Enable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

使用此参数时，该 cmdlet 将启用 Microsoft Windows PowerShell 提供程序的分析事件日志。 不会更改操作事件日志。

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

### -Force

用于在不提示的情况下强制更改。

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

### 无

## 输出

### 无

## 注释

此 cmdlet 使用 `Get-LogProperties` 和 `Set-LogProperties` cmdlet。

必须从提升的 PowerShell 会话中运行此 cmdlet。

## 相关链接

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Disable-PSTrace](Disable-PSTrace.md)

