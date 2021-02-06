---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596023"
---
# Uninstall-Script

## 摘要
卸载脚本。

## SYNTAX

### NameParameterSet（默认值）

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Uninstall-Script`Cmdlet 从本地计算机中卸载指定的脚本。

## 示例

### 示例1：卸载脚本

此示例将卸载脚本。

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

`Uninstall-Script` 使用 **Name** 参数指定要从本地计算机中卸载的脚本。

### 示例2：使用管道卸载脚本

在此示例中，管道用于卸载脚本。

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

`Get-InstalledScript` 使用 **Name** 参数指定脚本。 将对象向下发送到 `Uninstall-Script` ，并卸载脚本。

## PARAMETERS

### -AllowPrerelease

允许卸载标记为预发行版的脚本。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在运行之前提示你进行确认 `Uninstall-Script` 。

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

强制 `Uninstall-Script` 运行而不请求用户确认。

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

### -InputObject

接受 **PSRepositoryItemInfo** 对象。 例如，输出 `Get-InstalledScript` 到变量，并将该变量用作 **InputObject** 参数。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

指定要卸载的脚本的最大或最新版本。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要卸载的模块的最低版本。 不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要卸载的脚本名称的数组。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定要卸载的脚本的确切版本号。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

显示运行时将发生 `Uninstall-Script` 的情况。 cmdlet 未运行。

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

### System.String[]

### System.web. system.exception []

### System.String

## 输出

### System.Object

## 注释

## 相关链接

[Find-Script](Find-Script.md)

[Install-Script](Install-Script.md)

[Publish-Script](Publish-Script.md)

[Save-Script](Save-Script.md)

[Update-Script](Update-Script.md)

