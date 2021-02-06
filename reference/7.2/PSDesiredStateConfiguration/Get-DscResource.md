---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598680"
---
# Get-DscResource

## 摘要
获取计算机上存在的 (DSC) 资源的所需状态配置。

## SYNTAX

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## DESCRIPTION

`Get-DscResource`Cmdlet 检索计算机上存在的 POWERSHELL DSC 资源。 此 cmdlet 仅发现 PSModulePath 中安装的资源。 其中显示了有关由用户创建的内置和自定义提供程序的详细信息。 此 cmdlet 还显示有关复合资源的详细信息，复合资源是打包为模块或在运行时在会话中创建的其他配置。

## 示例

### 示例1：获取本地计算机上的所有资源

```powershell
Get-DscResource
```

此命令将获取本地计算机上的所有资源。

### 示例2：通过指定名称获取资源

```powershell
Get-DscResource -Name "WindowsFeature"
```

此命令将获取 WindowsFeature 资源。

### 示例3：获取模块中的所有资源

```powershell
Get-DscResource -Module "xHyper-V"
```

此命令从 xHyper-V 模块获取所有资源。

### 示例4：使用通配符获取资源

```powershell
Get-DscResource -Name P*,r*
```

此命令将获取与 **Name** 参数指定的通配符模式匹配的所有资源。

### 示例5：获取资源语法

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

此命令将获取 WindowsFeature 资源，并显示该资源的语法。

### 示例6：获取资源的所有属性

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

此命令将获取 User 资源，然后使用管道运算符返回 User 资源的所有属性。

### 示例7：从指定的模块中获取具有指定版本的所有资源

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

此命令从 xHyper-V 模块获取版本3.0.0.0 的所有资源。

## PARAMETERS

### -Module

指定要为其查看 DSC 资源的模块的名称或完全限定名称。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

指定要查看的 DSC 资源的名称数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -语法

指示该 cmdlet 返回指定 DSC 资源的语法视图。 返回的语法演示了如何使用 PowerShell 脚本中的资源。

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

### System.String[]

### System.Object

## 输出

### DesiredStateConfiguration. DscResourceInfo []

### string[]

## 注释

## 相关链接

[PowerShell Desired State Configuration 概述](/powershell/scripting/dsc/overview/overview)

[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

