---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 6cd7a4611f6118ed1f0846d9c11a8fe8edc69ef0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598254"
---
# Get-Variable

## 摘要
获取当前控制台中的变量。

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-Variable`Cmdlet 将获取当前控制台中的 PowerShell 变量。
通过指定 **ValueOnly** 参数可以只检索这些变量的值，还可以按名称筛选返回的变量。

## 示例

### 示例 1：按字母获取变量

此命令将获取名称以字母 m 开头的变量。
该命令还将获取这些变量的值。

```powershell
Get-Variable m*
```

### 示例 2：按字母获取变量值

此命令仅获取名称以 m 开头的变量的值。

```powershell
Get-Variable m* -ValueOnly
```

### 示例 3：按两个字母获取变量

此命令将获取有关以字母 M 或字母 P 开头的变量的信息。

```powershell
Get-Variable -Include M*,P*
```

### 示例 4：按作用域获取变量

第一个命令仅获取在本地作用域中定义的变量。
它等效于 `Get-Variable -Scope Local`，可以缩写为 `gv -s 0`。

第二个命令使用 `Compare-Object` cmdlet 来查找在父作用域中定义的变量 (作用域 1) ，但仅在本地作用域 (范围 0) 中可见。

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETERS

### -Exclude

指定此 cmdlet 将从操作中排除的项数组。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

指定此 cmdlet 会对其执行操作的项的数组（排除所有其他项）。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

指定变量的名称。
允许使用通配符。
还可以通过管道将变量名传递给 `Get-Variable` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Scope

指定作用域中的变量。此参数可接受的值包括：

- **全球**
- 本地
- **脚本**
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）

默认值为 **Local** 。
有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueOnly

指示此 cmdlet 仅获取变量的值。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含变量名称的字符串传递给 `Get-Variable` 。

## 输出

### System.Management.Automation.PSVariable

此 cmdlet 为它所获取的每个变量返回一个 **System.Management.AutomationPSVariable** 对象。 对象类型取决于变量。

### System.object []

当指定 **ValueOnly** 参数时，如果指定变量的值为集合，则 `Get-Variable` 返回 `[System.Object[]]` 。 此行为可防止正常管道操作一次处理一个变量的值。 强制集合枚举的一种解决方法是将 `Get-Variable` 命令括在括号中。

## 注释

- 此 cmdlet 不管理环境变量。 若要管理环境变量，可以使用环境变量提供程序。

## 相关链接

[Clear-Variable](Clear-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

