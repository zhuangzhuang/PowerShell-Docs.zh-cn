---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 8b8d0c545cdb36b6184a0670a52a5a30aa33a465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603590"
---
# New-DscChecksum

## 摘要
创建 DSC 文档和 DSC 资源的校验和文件。

## SYNTAX

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**New-dscchecksum** Cmdlet 为 PowerShell 所需状态配置生成校验和文件 (DSC) 文档和压缩的 DSC 资源。
此 cmdlet 为每个要在拉取模式下使用的配置和资源生成校验和文件。
DSC 服务使用校验和，以确保目标节点上存在正确的配置和资源。
将校验和与关联的 DSC 文档以及 DSC 服务存储中的压缩 DSC 资源放置在一起。

## 示例

### 示例1：为特定路径中的所有配置创建校验和文件

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

此命令为路径 C:\DSC\Configurations 中的所有配置创建校验和文件。
将跳过任何已存在的校验和文件。

### 示例2：为特定路径中的所有配置创建校验和文件，并覆盖现有的校验和文件

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

此命令为路径 C:\DSC\Configurations 中的所有配置创建新的校验和文件。
指定 *Force* 参数会使命令覆盖已存在的任何校验和文件。

## PARAMETERS

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示该 cmdlet 将覆盖指定的输出文件（如果它已存在）。

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

### -OutPath

指定输出校验和文件的路径和文件名。

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

### -Path

指定输入文件的路径。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

## 输出

### System.Object

## 注释

## 相关链接

[Windows PowerShell Desired State Configuration 概述](/powershell/scripting/dsc/overview/dscforengineers)

