---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595638"
---
# Split-Path

## 摘要
返回指定的路径部分。

## SYNTAX

### ParentSet（默认值）

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LeafSet

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### ExtensionSet

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### QualifierSet

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### NoQualifierSet

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

`Split-Path`Cmdlet 仅返回路径的指定部分，如父文件夹、子文件夹或文件名。 它也可以获取拆分路径所引用的项，并指示该路径是相对路径还是绝对路径。

使用此 cmdlet 可以只获取或只提交路径的选定部分。

## 示例

### 示例1：获取路径的限定符

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

此命令只返回路径的限定符。 限定符是驱动器。

### 示例2：显示文件名

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

此命令显示拆分路径所引用的文件。 由于此路径拆分为最后一项，也称为叶，因此该命令只显示文件名。

**Resolve** 参数指示 `Split-Path` 显示拆分路径所引用的项，而不是显示拆分路径。

与所有 `Split-Path` 命令一样，此命令将返回字符串。 它不返回表示文件的 **FileInfo** 对象。

### 示例3：获取父容器

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

此命令只返回路径的父容器。 由于它不包括任何用于指定拆分的参数，因此将 `Split-Path` 使用默认的拆分位置默认值。

### 示例4：确定路径是否为绝对路径

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

此命令确定路径是相对路径还是绝对路径。 在这种情况下，因为路径是当前文件夹的相对路径，而该文件夹由点 `.`)  (，则返回 `$False` 。

### 示例5：将位置更改为指定路径

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

此命令将你的位置更改为包含 PowerShell 配置文件的文件夹。

括号中的命令使用 `Split-Path` 来仅返回内置变量中存储的路径的父级 `$Profile` 。 **Parent** 参数是默认的拆分位置参数。
因此，你可以从命令中省略它。 圆括号直接 PowerShell 以首先运行命令。 这是一种移动到具有长路径名称的文件夹的有效方法。

### 示例6：使用管道拆分路径

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

此命令使用管道运算符 (`|`) 将路径发送到 `Split-Path` 。 路径用引号引起以指示它是一个标记。

## PARAMETERS

### -Credential

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -扩展

指示此 cmdlet 仅返回叶的扩展。 例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `.log` 。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

指示如果路径为绝对路径，则此 cmdlet 返回 $True; 如果路径是相对路径，则为 $False。 绝对路径的长度大于零，并且不使用点 (`.`) 来指示当前路径。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Leaf

指示此 cmdlet 仅返回路径中的最后一项或容器。 例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 pass1.log。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

指示此 cmdlet 仅返回叶的基名称。 例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `Pass1` 。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

指定要拆分的路径。 不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoQualifier

指示此 cmdlet 返回无限定符的路径。 对于文件系统或注册表提供程序，限定符是提供程序路径的驱动器，例如 `C:` 或 `HKCU:` 。 例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `\Test\Logs\Pass1.log` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Parent

指示此 cmdlet 仅返回项或路径指定的容器的父容器。 例如，在路径中 `C:\Test\Logs\Pass1.log` ，它返回 `C:\Test\Logs` 。
**Parent** 参数是默认的拆分位置参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要拆分的路径。 允许使用通配符。 如果路径包括空格，请将其括在引号中。 还可以通过管道将路径传递给此 cmdlet。

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Qualifier

指示此 cmdlet 仅返回指定路径的限定符。 对于文件系统或注册表提供程序，限定符是提供程序路径的驱动器，例如 `C:` 或 `HKCU:` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Resolve

指示此 cmdlet 显示生成的拆分路径所引用的项，而不是显示路径元素。

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

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet。

## 输出

### System.String、System.Boolean

`Split-Path` 返回文本字符串。 当你指定 **Resolve** 参数时，将 `Split-Path` 返回描述项位置的字符串; 它不返回表示项的对象，如 **FileInfo** 或 **RegistryKey** 对象。

指定 **IsAbsolute** 参数时，将 `Split-Path` 返回一个 **布尔** 值。

## 注释

-  (**限定符**、 **Parent**、 **Extension**、 **叶**、 **LeafBase** 和 **NoQualifier**) 的拆分位置参数是互斥的。 在每个命令中只能使用一个参数。

- 包含路径 cmdlet (路径 **名词的** cmdlet) **使用路径名，** 并以所有 PowerShell 提供程序可解释的简洁格式返回名称。 这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。 使用 **Dirname**、 **Normpath**、 **Realpath**、 **Join** 或其他路径操控器的方式来使用它们。

- 可以将 **路径** cmdlet 与多个提供程序一起使用。 其中包括 FileSystem、Registry 和 Certificate 提供程序。

- `Split-Path` 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 about_Providers。

## 相关链接

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Test-Path](Test-Path.md)
