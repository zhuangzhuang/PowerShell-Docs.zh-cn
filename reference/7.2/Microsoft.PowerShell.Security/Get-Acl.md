---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596429"
---
# Get-Acl

## 摘要
获取某个资源（如文件或注册表项）的安全描述符。

## SYNTAX

### ByPath（默认值）

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Acl`Cmdlet 可获取表示文件或资源的安全描述符的对象。 安全描述符包含资源的访问控制列表 (ACL)。 ACL 可指定用户和用户组访问资源所需的权限。

从 Windows PowerShell 3.0 开始，可以使用的 **InputObject** 参数 `Get-Acl` 来获取不具有路径的对象的安全描述符。

## 示例

### 示例 1-获取文件夹的 ACL

此示例获取目录的安全描述符 `C:\Windows` 。

```powershell
Get-Acl C:\Windows
```

### 示例 2-使用通配符获取文件夹的 ACL

此示例获取 `.log` `C:\Windows` 目录中名称以开头的所有文件的 PowerShell 路径和 SDDL `s` 。

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

该命令使用 `Get-Acl` cmdlet 来获取表示每个日志文件的安全描述符的对象。 它使用管道运算符 (`|`) 将结果发送到 `Format-List` cmdlet。 命令使用的 **属性** 参数 `Format-List` 来仅显示每个安全描述符对象的 **PsPath** 和 **SDDL** 属性。

通常在 PowerShell 中使用列表，因为在表中，长值会被截断。

**SDDL** 值对系统管理员很有价值，因为它们是包含安全描述符中所有信息的简单文本字符串。 正因如此，它们易于传递和存储，并且可在需要时对它们进行分析。

### 示例 3-获取 ACL 审核条目计数

此示例获取 `.log` 目录中名称以开头的文件的安全描述符 `C:\Windows` `s` 。

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

它使用 **Audit** 参数从安全描述符中的 SACL 获取审核记录。
然后，它使用 `ForEach-Object` cmdlet 来计算与每个文件相关联的审核记录的数目。 结果是一个表示每个日志文件的审核记录数的数字列表。

### 示例 4-获取注册表项的 ACL

此示例使用 `Get-Acl` cmdlet 来获取控件子项 (`HKLM:\SYSTEM\CurrentControlSet\Control` 注册表) 的安全描述符。

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

Path 参数指定 Control 子项。 管道运算符 (`|`) 传递指向命令的安全描述符 `Get-Acl` `Format-List` ，该命令将安全描述符的属性设置为列表格式，使其易于读取。

### 示例 5-使用 **InputObject** 获取 ACL

此示例使用的 **InputObject** 参数 `Get-Acl` 来获取存储子系统对象的安全描述符。

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETERS

### -Audit

从系统访问控制列表 (SACL) 获取安全描述符的审核数据。

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

### -Exclude

忽略指定项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

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

### -Filter

以提供程序的格式或语言指定筛选器。 此参数值使 **Path** 参数有效。 筛选器的语法（包括通配符的使用）取决于提供程序。 筛选器比其他参数更有效，因为提供程序是在获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

仅获取指定项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

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

### -Path

指定资源的路径。 `Get-Acl` 获取由路径指示的资源的安全说明符。 允许使用通配符。 如果省略 **Path** 参数，将 `Get-Acl` 获取当前目录的安全说明符。

参数名（“Path”）为可选项。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -InputObject

获取指定对象的安全描述符。 请输入包含对象的变量或可获取该对象的命令。

不能将路径以外的对象传递给 `Get-Acl` 。 而应该在命令中显式使用 **InputObject** 参数。

此参数是在 Windows PowerShell 3.0 中引入的。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定资源的路径。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

此参数是在 Windows PowerShell 3.0 中引入的。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给 `Get-Acl` 。

## 输出

### Accesscontrol-namespace. Accesscontrol-namespace. System.security.accesscontrol.directorysecurity，，accesscontrol-namespace. RegistrySecurity.。

`Get-Acl` 返回一个对象，该对象表示其获取的 Acl。 对象类型取决于 ACL 类型。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

默认情况下，会 `Get-Acl` 显示资源的 PowerShell 路径 (`<provider>::<resource-path>`) 、资源的所有者和 "访问权限"、"自定义" 访问控制列表中的访问控制项的列表 (数组)  (资源的 "DACL) "。 DACL 列表由资源所有者控制。

将结果的格式设置为列表时， (`Get-Acl | Format-List`) 除了路径、所有者和访问列表外，PowerShell 还会显示以下属性和属性值：

- **Group**：所有者的安全组。
- **Audit**：系统访问控制列表 (SACL) 中项的列表（数组）。 SACL 指定 Windows 为其生成审核记录的访问尝试的类型。
- **Sddl**：在单个文本字符串中以安全描述符定义语言格式显示的资源的安全描述符。 PowerShell 使用安全描述符的 **GetSddlForm** 方法来获取此数据。

由于 `Get-Acl` 文件系统和注册表提供程序支持，因此你可以使用 `Get-Acl` 查看文件系统对象（如文件和目录）的 ACL 和注册表对象（如注册表项和条目）。

## 相关链接

[Set-Acl](Set-Acl.md)
