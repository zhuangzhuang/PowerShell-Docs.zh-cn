---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: a79f12739643a873703b39d9d07e8b7db01dfbb4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597879"
---
# Test-Path

## 摘要
确定路径的所有元素是否存在。

## SYNTAX

### Path（默认值）

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## DESCRIPTION

`Test-Path`Cmdlet 确定路径的所有元素是否存在。 `$True`如果所有元素都存在，则返回，否则返回 `$False` 。 它还可以指示路径语法是否有效，以及路径是指向容器还是终结或叶元素。 如果 `Path` 为空字符串，则 `$False` 返回。 如果 `Path` 为 `$null` 、数组 `$null` 或空数组，则返回一个非终止错误。

## 示例

### 示例1：测试路径

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

此命令检查路径中的所有元素是否都存在（即 C：目录、文档和设置目录）以及 DavidC 目录。 如果缺少任何，cmdlet 将返回 `$False` 。
否则，它将返回 `$True`。

### 示例2：测试配置文件的路径

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

这些命令测试 PowerShell 配置文件的路径。

第一个命令确定路径中的所有元素是否都存在。 第二个命令确定路径的语法是否正确。 在这种情况下，路径为 `$False` ，但语法正确 `$True` 。 即使配置文件不存在，这些命令 `$profile` 也使用自动变量，该变量指向配置文件的位置。

有关自动变量的详细信息，请参阅 about_Automatic_Variables。

### 示例3：检查是否存在除指定类型之外的任何文件

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

此命令检查商业大楼目录中是否存在除 dwg 文件之外的任何文件。

该命令使用 **path** 参数来指定路径。 由于路径包含空格，因此该路径用引号引起来。 该路径末尾的星号指示 Commercial Building 目录的内容。 使用长路径（如此类），键入路径的前几个字母，然后使用 TAB 键完成路径。

命令指定 **Exclude** 参数，以指定将在计算中省略的文件。

在这种情况下，由于目录只包含 dwg 文件，因此结果为 `$False` 。

### 示例4：检查文件

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

此命令检查变量中存储的路径是否会 `$profile` 导致文件。 在这种情况下，由于 PowerShell 配置文件是一个 `.ps1` 文件，因此该 cmdlet 将返回 `$True` 。

### 示例5：检查注册表中的路径

这些命令 `Test-Path` 与 PowerShell 注册表提供程序一起使用。

第一个命令测试系统上的 **Microsoft PowerShell** 注册表项的注册表路径是否正确。 如果 PowerShell 安装正确，则该 cmdlet 将返回 `$True` 。

> [!IMPORTANT]
> `Test-Path` 不适用于所有 PowerShell 提供程序。 例如，你可以使用 `Test-Path` 来测试注册表项的路径，但如果你使用它来测试注册表项的路径，它将始终返回 `$False` ，即使存在该注册表项。

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### 示例6：测试文件是否比指定日期新

此命令使用 **NewerThan** 动态参数来确定计算机上的 "PowerShell.exe" 文件是否比 "7 月13日 2009" 新。

NewerThan 参数仅在文件系统驱动器中有效。

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### 示例7：使用 null 作为值测试路径

为返回的错误 `null` 、数组 `null` 或空数组为非终止错误。 可以通过使用将其取消 `-ErrorAction SilentlyContinue` 。 下面的示例显示返回错误的所有情况 `NullPathNotPermitted` 。

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### 示例8：测试带有空格作为值的路径

如果为参数提供了空白或空字符串 `-Path` ，则返回 **False**。
下面的示例显示了空白和空字符串。

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

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

### -Exclude

指定此 cmdlet 省略的项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如“*.txt”。 允许使用通配符。

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

以提供程序的格式或语言指定筛选器。 此参数值使 **Path** 参数有效。 筛选器的语法（包括通配符字符的使用），具体取决于提供程序。 筛选器比其他参数更有效，因为提供程序在检索对象时应用筛选器，而不是在检索对象后再对其进行筛选。

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

指定此 cmdlet 测试的路径。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如“*.txt”。 允许使用通配符。

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

### -IsValid

指示此 cmdlet 测试路径的语法，而不考虑路径的元素是否存在。 `$True`如果路径语法有效，则此 cmdlet 将返回 `$False` 。

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

### -LiteralPath

指定要测试的路径。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径中包含可以由 PowerShell 解释为转义序列的字符，则必须将路径括在单引号中，以便不会解释它们。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewerThan

指定时间作为 **DateTime** 对象。

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan

指定时间作为 **DateTime** 对象。

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要测试的路径。 允许使用通配符。 如果路径包括空格，请将其括在引号中。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PathType

指定路径中最后一个元素的类型。 `$True`如果元素为指定的类型，则此 cmdlet 将返回，如果不是，则返回 `$False` 。 此参数的可接受值为：

- 容器。
  -- 包含其他元素的元素，例如目录或注册表项。
- 片.
  -- 不包含其他元素的元素，例如文件。
- 随时.
  container 或 leaf。

指示路径中的最后一个元素是否为特定类型。

> [!CAUTION]
>
> 最多 PowerShell 版本6.1.2，当 **IsValid** 和 **PathType** 开关一起指定时，该 `Test-Path` cmdlet 将忽略 **PathType** 开关，并且仅验证句法路径，而不验证路径类型。
>
> 根据 [问题 #8607](https://github.com/PowerShell/PowerShell/issues/8607)，修复此行为可能是将来版本中的重大更改，其中 **IsValid** 和 **PathType** 开关属于单独的参数集，因此不能共同使用来避免这种混淆。

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含路径（但不是文本路径）的字符串传递给此 cmdlet。

## 输出

### System.Boolean

该 cmdlet 将返回一个 **布尔** 值。

## 注释

包含路径 cmdlet (路径 **名词的** cmdlet) **使用路径名，** 并以所有 PowerShell 提供程序可解释的简洁格式返回名称。 这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。
使用 **Dirname**、 **Normpath**、 **Realpath**、 **Join** 或其他路径操控器。

`Test-Path`设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)
