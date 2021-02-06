---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3ef54618e065a5fca3d52415897b3042d6ba4c65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597897"
---
# New-PSRoleCapabilityFile

## 摘要
创建一个文件，该文件定义要通过会话配置公开的一组功能。

## SYNTAX

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

`New-PSRoleCapabilityFile`Cmdlet 将创建一个文件，该文件定义可通过会话配置文件公开的一组用户功能。 这包括确定用户可以使用哪些 cmdlet、函数和脚本。 此功能文件是一个可读的文本文件，其中包含会话配置属性和值的哈希表。 该文件的文件扩展名为 .psrc，可供多个会话配置使用。

`New-PSRoleCapabilityFile`除 **Path** 参数外，所有参数都是可选的，它指定文件的文件路径。 如果在运行 cmdlet 时不包括参数，则将注释掉会话配置文件中的相应密钥，但参数说明中注明的情况除外。 例如，如果不包括 **AssembliesToLoad** 参数，则将注释掉会话配置文件的那一部分。

若要在会话配置中使用角色功能文件，请首先将该文件放在有效 PowerShell 模块文件夹的 **RoleCapabilities** 子文件夹中。 然后，在 PowerShell 会话 ( 配置的 **RoleDefinitions** 字段中按名称引用该文件) 文件。

此 cmdlet 是在 Windows PowerShell 5.0 中引入的。

## 示例

### 示例1：创建空白角色功能文件

此示例将创建一个新的角色功能文件，该文件使用默认 (空白) 值。 稍后可以在文本编辑器中编辑该文件以更改这些配置设置。

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### 示例2：创建角色功能文件，使用户能够重启服务和任何 VDI 计算机

此示例将创建一个示例角色功能文件，使用户能够重新启动与特定名称模式匹配的服务和计算机。 通过将 **ValidatePattern** 参数设置为正则表达式来定义名称筛选 `VDI\d+` 。

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETERS

### -AliasDefinitions

将指定的别名添加到使用角色功能文件的会话。 输入一个包含以下键的哈希表：

- 名称： 别名的名称。 此键是必需的。
- Value。 别名所表示的命令。 此键是必需的。
- 说明。 描述别名的文本字符串。 此键是可选的。
- 选项。 别名选项。 此键是可选的。 默认值为 None。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如： `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

指定要加载到使用角色功能文件的会话中的程序集。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -作者

指定创建角色功能文件的用户。

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

### -公司名称

标识创建了角色功能文件的公司。
默认值是“未知”。

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

### -版权所有

指定角色功能文件的版权。 如果省略此参数，则 `New-PSRoleCapabilityFile` 使用 **Author** 参数的值生成版权声明。

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

### -Description

指定角色功能文件的描述。

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

### -EnvironmentVariables

指定公开此角色功能文件的会话的环境变量。 输入一个哈希表，其中的键是环境变量名称，而值是环境变量值。

例如： `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

指定格式化文件 ( 在使用角色功能文件的会话中运行的 types.ps1xml) 。 此参数的值必须是格式设置文件的完整或绝对路径。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionDefinitions

向公开角色功能的会话添加指定的函数。 输入一个包含以下键的哈希表：

- 名称： 函数的名称。 此键是必需的。
- ScriptBlock. 函数体。 输入一个脚本块。 此键是必需的。
- 选项。 函数选项。 此键是可选的。 默认值为 None。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如：

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Guid

指定角色功能文件的唯一标识符。 如果省略此参数，则 `New-PSRoleCapabilityFile` 将为文件生成 GUID。 若要在 PowerShell 中创建新的 GUID，请键入 `[guid]::NewGuid()` 。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定自动导入到使用角色功能文件的会话中的模块。 默认情况下，列出的模块中的所有命令均可见。 与 **VisibleCmdlets** 或 **VisibleFunctions** 一起使用时，可以限制从指定模块中查看的命令。

此参数的值中使用的每个模块都可以通过字符串或哈希表来表示。 模块字符串只包含模块的名称。 模块哈希表可以包含 **ModuleName**、 **ModuleVersion** 和 **GUID** 键。 仅 **ModuleName** 键是必需的。

例如，下面的值由字符串和哈希表组成。 字符串和哈希表的任何组合（采用任何顺序）都是有效的。

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定角色功能文件的路径和文件名。 文件必须具有文件 `.psrc` 扩展名。

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

### -ScriptsToProcess

指定要添加到使用角色功能文件的会话的脚本。 请输入脚本的路径和文件名。 此参数的值必须为脚本文件名的完整或绝对路径。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

指定要添加到使用角色功能文件的会话 () 的类型文件 types.ps1xml。 输入类型文件名。 此参数的值必须为类型文件名的完整或绝对路径。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

指定要添加到使用角色功能文件的会话中的变量。 输入一个包含以下键的哈希表：

- 名称： 变量的名称。 此键是必需的。
- Value。 变量值。 此键是必需的。
- 选项。 变量选项。 此键是可选的。 默认值为 None。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如： `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

将会话中的别名限制为在此参数的值中指定的别名，以及在 **AliasDefinition** 参数中定义的所有别名。 支持使用通配符。
默认情况下，PowerShell 引擎定义的所有别名和模块导出的所有别名都在会话中可见。

例如，若要将可用别名限制为 gm 和 gcm，请使用以下语法： `VisibleAliases="gcm", "gp"`

当角色功能文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

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

### -VisibleCmdlets

将会话中的 cmdlet 限制为在此参数的值中指定的 cmdlet。 支持通配符和模块限定名称。

默认情况下，会话中的模块导出的所有 cmdlet 都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数来确定哪些模块和管理单元已导入到会话中。 如果 **ModulesToImport** 中的任何模块都不公开 cmdlet，则会 `New-PSRoleCapabilityFile` 尝试加载相应的模块。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleExternalCommands

将可以在会话中执行的外部二进制文件、脚本和命令限制为在此参数的值中指定的文件。

默认情况下，在此会话中不会显示任何外部命令。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleFunctions

将会话中的函数限制为在此参数的值中指定的函数，以及在 **FunctionDefinitions** 参数中定义的任何函数。 支持使用通配符。

默认情况下，会话中的模块导出的所有函数都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数确定导入到会话中的模块。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

将会话中的 PowerShell 提供程序限制为在此参数的值中指定的提供程序。
支持使用通配符。

默认情况下，会话中的模块导出的所有提供程序都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数确定导入到会话中的模块。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

## 注释

## 相关链接

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)

