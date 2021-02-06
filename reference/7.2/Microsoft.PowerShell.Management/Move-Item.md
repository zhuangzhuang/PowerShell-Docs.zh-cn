---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597678"
---
# Move-Item

## 摘要
将项从一个位置移动到另一个位置。

## SYNTAX

### Path（默认值）

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Move-Item`Cmdlet 将项（包括其属性、内容和子项）从一个位置移动到另一个位置。 但这些位置必须由同一提供程序支持。
例如，它可以将文件或子目录从一个目录移动到另一个目录，或将注册表子项从一个项移动到另一个项。
在你移动某个项时，该属性将被添加到新位置，并从其原来的位置删除。

## 示例

### 示例1：将文件移到另一个目录并将其重命名

此命令将 `Test.txt` 文件从驱动器移动 `C:` 到 `E:\Temp` 目录，并将其重命名 `test.txt` 为 `tst.txt` 。

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### 示例2：将目录及其内容移到另一个目录

此命令将 `C:\Temp` 目录及其内容移动到 `C:\Logs` 目录中。
"Temp" 目录及其所有子目录和文件都显示在 "日志" 目录中。

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### 示例3：将指定扩展的所有文件从当前目录移动到另一个目录

此命令会将当前目录中的所有 () 的文本文件移动 `*.txt` (由点 (`.`) # A5 表示为 `C:\Logs` 目录。

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### 示例4：以递归方式将指定扩展名的所有文件从当前目录移动到另一个目录

此命令将所有文本文件从当前目录和所有子目录递归地移动到 "C:\TextFiles" 目录。

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

该命令使用 `Get-ChildItem` cmdlet 来获取当前目录中的所有子项目， (由 \[ \]) 及其子目录（其 *文件扩展名为 ".txt"）表示。它使用 recursive 参数将检索设置为 recursive，并使用 Include 参数将检索限制为 "*.txt" 文件。

管道运算符 (`|`) 将此命令的结果发送到 `Move-Item` ，后者将文本文件移动到 "TextFiles" 目录。

如果要移动到 "C:\Textfiles" 的文件具有相同的名称，将 `Move-Item` 显示错误并继续，但它只会将一个具有每个名称的文件移动到 "C:\Textfiles"。
其他文件仍保留在其原始目录下。

如果 "Textfiles" 目录 (或目标路径) 的任何其他元素不存在，则该命令将失败。
不会为你创建缺少的目录，即使使用 **Force** 参数也是如此。
`Move-Item` 将第一项移到名为 "Textfiles" 的文件中，然后显示一个错误，指出该文件已存在。

而且，默认情况下 `Get-ChildItem` 不会移动隐藏的文件。
若要移动隐藏的文件，请使用 **Force** 参数 `Get-ChildItem` 。

> [!NOTE]
> 在 Windows PowerShell 2.0 中，使用 cmdlet 的 **递归** 参数时 `Get-ChildItem` ， **Path** 参数的值必须是一个容器。
> 使用 **Include** 参数指定 .txt 文件扩展名筛选器 (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`)。

### 示例5：将注册表项和值移动到另一个键

此命令将中 "MyCompany" 注册表项中的注册表项和值移动 `HKLM\Software` 到 "MyNewCompany" 键。
通配符 (`*`) 指示应移动 "MyCompany" 键的内容，而不是键本身。
在此命令中，省略了可选的 **Path** 和 **Destination** 参数名。

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### 示例6：将目录及其内容移动到指定目录的子目录

此命令会将 "日志 \[ 九月 \` 06 \] " 目录 (，并将其内容) 到 "日志 \[ 2006 \] " 目录中。

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

使用 **LiteralPath** 参数而不是 **Path**，因为原始目录名称包含左方括号和右方括号字符 ( " \[ " 和 " \] " ) 。
也可将路径括在单引号 (' ') 中，以便不会曲解倒引号 (\`)。

**Destination** 参数不需要文本路径，因为目标变量也必须括在单引号中，因为它包含可能被误解的方括号。

## PARAMETERS

### -Credential

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。
> 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Destination

指定指向要移动其中的项的位置的路径。
默认为当前目录。
允许使用通配符，但结果必须指定单个位置。

若要重命名要移动的项，请在 **Destination** 参数的值中指定新名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Exclude

指定为字符串数组，此 cmdlet 在操作中排除的项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。 仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。

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

指定用于限定 **路径** 参数的筛选器。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。 可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。
筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。

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

### -Force

强制运行命令而不要求用户确认。
不同提供程序有不同的实现。
有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

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

### -Include

指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `"*.txt"`。 允许使用通配符。 仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。

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

### -LiteralPath

指定一个或多个位置的路径。 **LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

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

### -PassThru

返回一个代表你所处理的项目的对象。
默认情况下，此 cmdlet 将不产生任何输出。

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

### -Path

指定指向项的当前位置的路径。
默认为当前目录。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

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

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet。

## 输出

### 无或表示已移动项的对象

当使用 *PassThru* 参数时，此 cmdlet 将生成一个表示已移动项的对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

- 此 cmdlet 将在同一提供程序支持的驱动器之间移动文件，但它只在同一驱动器内移动目录。
- 因为 `Move-Item` 命令移动项的属性、内容和子项，所以默认情况下，所有移动都是递归的。
- 此 cmdlet 用于处理由任何提供程序公开的数据。
  若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。
  有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

