---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: e81302a442294a7eeab81c6e8e1c6b7fd0cfb5fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598280"
---
# Get-PSSessionCapability

## 摘要
获取受约束的会话配置上的特定用户的功能。

## SYNTAX

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## DESCRIPTION

**PSSessionCapability** cmdlet 获取特定用户对受约束会话配置的功能。
使用此 cmdlet 审核用户的自定义会话配置。

从 Windows PowerShell 5.0 开始，你可以使用会话配置中的 **RoleDefinitions** 属性) 文件 (。
使用此属性，你可以基于组成员身份向用户授予针对单个受约束的终结点的不同功能。
通过让你确定授予用户的确切功能， **PSSessionCapability** cmdlet 可降低审核这些终结点时的复杂性。

默认情况下， **PSSessionCapability** cmdlet 返回指定用户可在指定终结点中运行的命令的列表。
这等效于指定终结点中运行 **Get 命令** 的用户。
当使用 *Full* 参数运行时，此 cmdlet 将返回 **InitialSessionState** 对象。
此对象包含有关指定的用户将与指定的终结点交互的 PowerShell 运行空间的详细信息。
它包括语言模式、执行策略和环境变量等信息。

## 示例

### 示例1：获取可用于用户的命令

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

当连接到本地计算机上的 Endpoint1 约束终结点时，此示例将返回可供用户 CONTOSO\User 使用的命令。

### 示例2：获取有关用户的运行空间的详细信息

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

此示例返回有关用户 CONTOSO\User 连接到 Endpoint1 约束终结点时将与之交互的运行空间的详细信息。

## PARAMETERS

### -ConfigurationName

指定正在检查)  (终结点的受约束的会话配置。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

指示此 cmdlet 返回指定的约束终结点上指定用户的整个初始会话状态。

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

### -Username

指定正在检查其功能的用户。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

### System.Management.Automation.AliasInfo

### System.web. FunctionInfo

### System.Management.Automation.Runspaces.InitialSessionState

## 注释

## 相关链接

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)

