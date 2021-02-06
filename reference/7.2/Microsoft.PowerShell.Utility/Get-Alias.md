---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 7b6f639d1c5685e341260c056a1dd0a17fe9f46d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597656"
---
# Get-Alias

## 摘要
获取当前会话的别名。

## SYNTAX

### Default（默认值）

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### 定义

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**获取别名** cmdlet 获取当前会话中的别名。
这包括内置别名、已设置或导入的别名，以及已添加到 PowerShell 配置文件中的别名。

默认情况下， **获取** 别名会获得一个别名并返回命令名称。
当你使用 *定义* 参数时， **Get-Alias** 将使用命令名称并返回其别名。

从 Windows PowerShell 3.0 开始，" **获取别名** " 以格式显示不带连字符的别名， `<alias> -> <definition>` 以便更轻松地找到所需的信息。

## 示例

### 示例1：获取当前会话中的所有别名

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

此命令获取当前会话中的所有别名。

输出显示了 `<alias> -> <definition>` 在 Windows PowerShell 3.0 中引入的格式。
此格式仅适用于不含有连字符的别名，因为带有连字符的别名通常为 cmdlet 和函数（而不是昵称）的首选名称。

### 示例2：按名称获取别名

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

此命令获取以 gp 或 sp 开头的所有别名（以 ps 结尾的别名除外）。

### 示例3：获取 cmdlet 的别名

```powershell
Get-Alias -Definition Get-ChildItem
```

此命令获取 Get-childitem cmdlet 的别名。

默认情况下， **获取** 别名时会获取项名称。
*定义* 参数会在你知道项名称时获取别名。

### 示例4：按属性获取别名

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

此命令获取 Options 属性值为 ReadOnly 的所有别名。
此命令提供了一种快速方法来查找 PowerShell 内置的别名，因为它们具有 ReadOnly 选项。

Options 只 **是获取 system.management.automation.aliasinfo** 对象的一个属性。
若要查找 System.management.automation.aliasinfo 对象的所有属性和方法，请键入 `Get-Alias | get-member` 。

### 示例5：按名称获取别名并按开始字母筛选

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

此示例获取所有以“-PSSession”结尾的命令别名，但以“e”开头的别名除外。

该命令使用 *Scope* 参数将命令应用到全局作用域中。
当你想要获取会话中的别名时，这对脚本比较有用。

## PARAMETERS

### -Definition

获取指定项的别名。
输入 cmdlet、函数、脚本、文件或可执行文件的名称。

此参数名为 *definition*，因为它在别名对象的 Definition 属性中搜索项目名称。

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

忽略指定项。
此参数的值对 Name 和 Definition 参数进行限定。
输入名称、定义或模式，例如“s*”。
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

指定此 cmdlet 获取的别名。
允许使用通配符。
默认情况下， `Get-Alias` 检索为当前会话定义的所有别名。
参数名称 **名称** 是可选的。
还可以通过管道将别名命名为 `Get-Alias` 。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Scope

指定此 cmdlet 为其获取别名的作用域。
此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字（0 到作用域数，其中 0 是指当前作用域，1 是指其父作用域）

默认值为 Local。
有关详细信息，请参阅 about_Scopes。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将别名命名为 **获取别名**。

## 输出

### System.Management.Automation.AliasInfo

**Get-Alias** 返回表示每个别名的对象。
**Get-alias** 为每个别名返回相同的对象，但 PowerShell 使用基于箭头的格式来显示不带连字符的别名的名称。

## 注释

- 若要创建新的别名，请使用 Set-Alias 或 New-Alias。 若要删除别名，请使用 Remove-Item。
- 基于箭头的别名名称格式不适用于含有连字符的别名。 这些很可能是 cmdlet 和函数（而不是典型的缩写或昵称）的首选替代名。

## 相关链接

[Export-Alias](Export-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Alias 提供程序](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

