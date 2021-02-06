---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: e35e164f3116304efd52c71c1715ba70711f6253
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597453"
---
# Disable-ExperimentalFeature

## 摘要
在启动 PowerShell 的新实例时禁用实验功能。

## SYNTAX

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Disable-ExperimentalFeature`Cmdlet 将通过从 `powershell.config.json` PowerShell 启动时读取的设置文件中删除命名实验功能，来禁用实验性功能。

此 cmdlet 是在 PowerShell 6.2 中引入的。

> [!NOTE]
> 对实验性功能状态所做的任何更改仅会在重新启动 PowerShell 时生效

## 示例

### 示例1：禁用实验性功能

在此示例中，如果之前已启用此实验功能，则在 `powershell.config.json` PowerShell 重新启动后，该文件将被更新，以使该用户不会启用该功能。
如果成功，则不会输出到管道，并且只显示一条警告消息。

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETERS

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

要禁用的实验功能的名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

确定 `powershell.config.json` 要更新哪个用户是否影响所有用户或仅影响当前用户。

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### ExperimentalFeature

要禁用的 ExperimentalFeature 从 cmdlet 发送的管道实例 `Get-ExperimentalFeature` 。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

对实验功能的状态的更改仅在重新启动 PowerShell 时才会生效。

## 相关链接

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

