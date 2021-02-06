---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595409"
---
# Get-RunspaceDebug

## 摘要
显示运行空间调试选项。

## SYNTAX

### RunspaceNameParameterSet (默认值) 

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### RunspaceParameterSet

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### RunspaceIdParameterSet

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### RunspaceInstanceIdParameterSet

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### ProcessNameParameterSet

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-RunspaceDebug`Cmdlet 显示运行空间调试选项。

## 示例

### 1：显示默认运行空间调试程序的状态

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## PARAMETERS

### -AppDomainName

承载 PowerShell 运行空间的应用程序域的名称。

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessName

承载 PowerShell 运行空间的进程的名称。

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -运行空间

要禁用的一个或多个 **运行空间** 对象。

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -RunspaceId

要禁用的一个或多个 **运行空间** Id 号。

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunspaceInstanceId

要禁用的一个或多个 **运行空间** guid。

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunspaceName

要禁用的一个或多个 **运行空间** 名称。

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
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

[Disable-RunspaceDebug](Disable-RunspaceDebug.md)

[Enable-RunspaceDebug](Enable-RunspaceDebug.md)

