---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: e9e80b4bf558dcf1e225868a1138979270ea304f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595382"
---
# Set-Alias

## 摘要
在当前 PowerShell 会话中为 cmdlet 或其他命令创建或更改别名。

## SYNTAX

### Default（默认值）

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Alias`Cmdlet 可为 cmdlet 或命令创建或更改别名，例如函数、脚本、文件或其他可执行文件。 别名是引用 cmdlet 或命令的替代名称。
例如， `sal` 是 cmdlet 的别名 `Set-Alias` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

一个 cmdlet 可以具有多个别名，但一个别名只能与一个 cmdlet 关联。 你可以使用 `Set-Alias` 将现有别名重新分配给另一个 cmdlet，或更改别名的属性，如描述。

由创建或更改的别名 `Set-Alias` 不是永久性的，并且仅在当前 PowerShell 会话中可用。 关闭 PowerShell 会话后，会删除该别名。

## 示例

### 示例 1：创建 cmdlet 的别名

此命令在当前 PowerShell 会话中为 cmdlet 创建别名。

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。 **Name** 参数指定别名的名称 `list` 。 **Value** 参数指定别名运行的 cmdlet。

若要运行别名，请 `list` 在 PowerShell 命令行上键入。

### 示例2：将现有别名重新分配给其他 cmdlet

此命令将重新分配现有别名以运行不同的 cmdlet。

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

`Get-Alias`Cmdlet 使用 **Name** 参数显示 `list` 别名。 `list`别名与 `Get-ChildItem` cmdlet 关联。 `list`运行别名时，会显示当前目录中的项。

`Set-Alias`Cmdlet 使用 **Name** 参数来指定 `list` 别名。 **Value** 参数将别名与 `Get-Location` cmdlet 关联。

`Get-Alias`Cmdlet 使用 **Name** 参数显示 `list` 别名。 `list`别名与 `Get-Location` cmdlet 关联。 `list`运行别名时，会显示当前目录的位置。

### 示例3：创建和更改只读别名

此命令创建只读别名。 只读选项可防止对别名所做的意外更改。 若要更改或删除只读别名，请使用 **Force** 参数。

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。 **Name** 参数指定别名的名称 `loc` 。 **Value** 参数指定 `Get-Location` 别名运行的 cmdlet。 **选项** 参数指定 **ReadOnly** 值。 **PassThru** 参数表示 alias 对象，并将对象向下发送到 `Format-List` cmdlet。 `Format-List` 使用带有星号 (的 **属性** 参数 `*`) 以便显示所有属性。 示例输出显示了这些属性的部分列表。

`loc`通过添加两个参数来更改该别名。 **说明** 添加文本以说明别名的用途。 因为别名是只读的，所以需要 **Force** 参数 `loc` 。 如果未使用 **Force** 参数，则更改将失败。

### 示例4：创建可执行文件的别名

此示例为本地计算机上的可执行文件创建别名。

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。 **Name** 参数指定别名的名称 `np` 。 **Value** 参数指定路径和应用程序名称 **C:\Windows\notepad.exe**。 `Get-Alias`Cmdlet 使用 **Name** 参数显示该 `np` 别名与 **notepad.exe** 相关联。

若要运行别名，请 `np` 在 PowerShell 命令行上键入以打开 **notepad.exe**。

### 示例5：为带有参数的命令创建别名

此示例演示如何为带有参数的命令分配别名。

你可以为 cmdlet 创建别名，例如 `Set-Location` 。 不能为带有参数和值的命令创建别名，例如 `Set-Location -Path C:\Windows\System32` 。 若要为某个命令创建别名，请创建一个包括该命令的函数，然后为此函数创建别名。 有关详细信息，请参阅 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)。

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

创建名为的函数 `CD32` 。 函数将 `Set-Location` cmdlet 与 **Path** 参数一起使用以指定目录 **C:\Windows\System32**。

`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建函数的别名。 **Name** 参数指定别名的名称 `Go` 。 **Value** 参数指定函数的名称， `CD32` 。

若要运行别名，请 `Go` 在 PowerShell 命令行上键入。 `CD32`函数会运行并更改目录 **C:\Windows\System32**。

## PARAMETERS

### -Description

指定对别名的描述。 你可以键入任意字符串。 如果描述包含空格，则将其括在单引号中。

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

### -Force

使用 **Force** 参数可更改或删除将 **选项** 参数设置为 **ReadOnly** 的别名。

**Force** 参数无法更改或删除 **选项** 参数设置为 **常量** 的别名。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定新别名的名称。 别名可以包含字母数字字符和连字符。 别名不能为数字，如123。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

设置别名的 **选项** 属性值。 值（如 **ReadOnly** 和 **常量** ）可防止意外更改的别名。 若要查看会话中所有别名的 **选项** 属性，请键入 `Get-Alias | Format-Table -Property Name, Options -Autosize` 。

此参数可接受的值如下所示：

- **AllScope** 将别名复制到任何创建的新作用域。
- **常量** 不能更改或删除。
- **无** 不设置任何选项，是默认值。
- **私有** 别名仅在当前作用域中可用。
- **ReadOnly** 除非使用 **Force** 参数，否则无法对其进行更改或删除。
- **Unspecified**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回一个表示别名的对象。 使用格式 cmdlet （例如） `Format-List` 来显示对象。 默认情况下，不 `Set-Alias` 会生成任何输出。

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

### -Scope

指定此别名的有效作用域。 默认值为 " **本地**"。 有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

可接受的值如下所示：

- 全球
- 本地
- 专用
- 编号范围
- Script

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定别名运行的 cmdlet 或命令的名称。 **值** 参数是别名的 **定义** 属性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

`Set-Alias` 不接受来自管道的输入。

## 输出

### 无或 System.Management.Automation.AliasInfo

当使用 **PassThru** 参数时，将 `Set-Alias` 生成一个表示别名的 **system.management.automation.aliasinfo** 对象。 否则，不 `Set-Alias` 会生成任何输出。

## 注释

PowerShell 包括每个 PowerShell 会话中提供的内置别名。 `Get-Alias`Cmdlet 显示 PowerShell 会话中可用的别名。

若要创建别名，请使用 cmdlet `Set-Alias` 或 `New-Alias` 。 在 PowerShell 6 中，若要删除别名，请使用 `Remove-Alias` cmdlet。 `Remove-Item` 接受以实现向后兼容性，如用于在以前版本的 PowerShell 中创建的脚本。 使用命令（如） `Remove-Item -Path Alias:aliasname` 。

若要创建在每个 PowerShell 会话中都可用的别名，请将其添加到 PowerShell 配置文件中。
有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

可以通过执行 "导出" 和 "导入"，在另一个 PowerShell 会话中保存和重复使用别名。 若要将别名保存到文件，请使用 `Export-Alias` 。 若要将保存的别名添加到新的 PowerShell 会话，请使用 `Import-Alias` 。

## 相关链接

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Remove-Alias](Remove-Alias.md)

[Remove-Item](../Microsoft.PowerShell.Management/Remove-Item.md)

