---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 2b6bbc6e3e0c535d777509a545edfe10fed7d727
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194941"
---
# Get-ExperimentalFeature

## 摘要
获取实验性功能。

## SYNTAX

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## 说明

`Get-ExperimentalFeature`Cmdlet 将返回 PowerShell 发现的所有实验性功能。
实验功能可以来自模块或 PowerShell 引擎。 利用实验功能，用户可以安全地测试新功能，并通过 GitHub) 提供反馈 (在将设计视为已完成之前，任何更改都可能会成为重大更改。

## 示例

### 示例 1

获取当前注册的实验功能及其当前状态的列表。

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETERS

### -Name

要返回的特定实验功能的名称或名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

要返回的实验功能的名称或名称。

## 输出

### System.web. ExperimentalFeature

如果未指定名称，则返回与请求的名称或所有实验性功能匹配的实例。

## 相关链接

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)
