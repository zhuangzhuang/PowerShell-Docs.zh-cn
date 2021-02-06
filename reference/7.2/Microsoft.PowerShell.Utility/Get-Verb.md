---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 6aba1c87a5d711cbfe84f9f6f6d1051acbcd524a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596661"
---
# Get-Verb

## 摘要
获取已批准的 PowerShell 谓词。

## SYNTAX

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Verb`函数获取已批准在 PowerShell 命令中使用的谓词。

建议 PowerShell cmdlet 和函数名称采用 `Verb-Noun` 格式，并包含已批准的谓词。 这种做法使命令名称更一致、可预测且更易于使用。

使用未经批准的谓词的命令仍在 PowerShell 中运行。 但是，当导入的模块的名称中包含未批准的谓词的命令时，该 `Import-Module` 命令将显示一条警告消息。

> [!NOTE]
> 返回的谓词列表 `Get-Verb` 可能不完整。 有关包含说明的已批准 PowerShell 动词的更新列表，请参阅 Microsoft Docs 中的 [批准的动词](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 。

## 示例

### 示例 1-获取所有谓词的列表

```powershell
Get-Verb
```

### 示例 2-获取以 "un" 开头的已批准谓词的列表

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### 示例 3-获取安全组中所有已批准的谓词

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### 示例 4-查找模块中具有未经批准的谓词的所有命令

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETERS

### -Verb

仅获取指定的谓词。 输入谓词的名称或名称模式。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Group

仅获取指定的组。 输入组的名称。 不允许使用通配符。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

## 输出

### System.web. VerbInfo

## 注释

根据最常见的用途，将 PowerShell 谓词分配给某个组。 谓词组旨在简化谓词的查找和比较，而不会限制谓词的使用。 对于任意类型的命令，均可使用任何批准的谓词。

每个 PowerShell 谓词分配给以下组之一。

- 常见：定义可应用于几乎任何 cmdlet 的常规操作，例如 Add。
- 通信：定义适用于通信的操作，例如 "连接"。
- 数据：定义适用于数据处理的操作，例如备份。
- 诊断：定义适用于诊断的操作，例如 "调试"。
- 生命周期：定义适用于 cmdlet 生命周期的操作，如 "完成"。
- 安全性：定义适用于安全的操作，例如 Revoke。
- 其他：定义其他类型的操作。

与 PowerShell 一起安装的一些 cmdlet （例如 `Tee-Object` 和 `Where-Object` ）使用未经批准的谓词。 这些 cmdlet 是历史例外，它们的动词归类为 **reserved**。

## 相关链接

[Import-Module](../microsoft.powershell.core/import-module.md)

