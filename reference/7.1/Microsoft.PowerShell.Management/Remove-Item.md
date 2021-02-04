---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: c4a0243c528cbe1a28cad99cf6fa8d91018d9b3c
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692690"
---
# Remove-Item

## 摘要
删除指定项。

## SYNTAX

### Path（默认值）

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

`Remove-Item`Cmdlet 删除一个或多个项。 由于许多提供程序都支持它，因此它可以删除多种不同类型的项，其中包括文件、文件夹、注册表项、变量、别名和函数。

## 示例

### 示例1：删除具有任何文件扩展名的文件

此示例将从文件夹中删除所有名称中包含点)  (的文件 `.` `C:\Test` 。 由于该命令指定一个点，因此该命令不删除没有文件扩展名的文件夹或文件。

```powershell
Remove-Item C:\Test\*.*
```

### 示例2：删除文件夹中的某些文档文件

此示例从当前文件夹中删除所有具有 `.doc` 文件扩展名的文件和不包含的名称 `*1*` 。

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

它使用通配符 (`*`) 来指定当前文件夹的内容。 它使用 **Include** 和 **Exclude** 参数来指定要删除的文件。

### 示例3：删除隐藏的只读文件

此命令删除 *隐藏* 和 *只读* 文件。

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

它使用 **Path** 参数指定文件。 它使用 **Force** 参数将其删除。 如果没有 **强制**，则无法删除 _只读_ 或 _隐藏_ 文件。

### 示例4：以递归方式删除子文件夹中的文件

此命令将以递归方式删除当前文件夹和所有子文件夹中的所有 CSV 文件。

因为中的 **递归** 参数 `Remove-Item` 有一个已知的问题，所以本示例中的命令使用 `Get-ChildItem` 来获取所需的文件，然后使用管道运算符将其传递给 `Remove-Item` 。

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

在 `Get-ChildItem` 命令中， **路径** 的值为 (`*`) ，表示当前文件夹的内容。 它使用 **Include** 来指定 CSV 文件类型，并使用 **递归** 来使检索递归。 如果尝试指定文件类型（如 `-Path *.csv` ），则该 cmdlet 会将搜索的使用者解释为没有子项的文件，而 **递归** 会失败。

### 示例5：以递归方式删除子项

此命令删除 "OldApp" 注册表项及其所有子项和值。 它使用 `Remove-Item` 删除密钥。 指定了路径，但省略了可选的参数名称 (**路径**) 。

**递归** 参数会以递归方式删除 "OldApp" 项的所有内容。 如果该注册表项包含子项并且省略了 **递归** 参数，系统会提示您确认是否要删除该注册表项的内容。

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### 示例6：删除包含特殊字符的文件

下面的示例演示如何删除包含特殊字符（如方括号或圆括号）的文件。

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### 示例7：删除备用数据流

此示例演示如何使用 cmdlet 的 **Stream** 动态参数 `Remove-Item` 删除备用数据流。 流参数是在 Windows PowerShell 3.0 中引入的。

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

**Stream** 参数 `Get-Item` 获取文件的 `Zone.Identifier` 流 `Copy-Script.ps1` 。 `Remove-Item` 使用 **stream** 参数删除 `Zone.Identifier` 文件的流。 最后，该 `Get-Item` cmdlet 会显示 `Zone.Identifier` 已删除流。

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

指定用于限定 **路径** 参数的筛选器。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。 可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。 筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。

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

强制 cmdlet 删除不能更改的项，如隐藏文件或只读文件，或者只读别名或变量。 该 cmdlet 不能删除常量别名或变量。
不同提供程序有不同的实现。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。 即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。

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

### -Path

指定要删除的项的路径。
允许使用通配符。

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

### -Recurse

指示此 cmdlet 删除指定位置和位置的所有子项中的项。

如果与 **Include** 参数一起使用，则 **递归** 参数可能不会删除所有子文件夹或所有子项。 这是一个已知问题。 作为一种解决方法，请尝试 `Get-ChildItem -Recurse` 将命令结果传递给 `Remove-Item` ，如本主题中的 "示例 4" 中所述。

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

### -Stream

> [!NOTE]
> 此参数仅在 Windows 上可用。

**Stream** 参数是 FileSystem 提供程序添加到的动态参数 `Remove-Item` 。
此参数仅在文件系统驱动器中有效。

您可以使用 `Remove-Item` 删除备用数据流，如 `Zone.Identifier` 。
但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。 如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -Confirm

提示你在运行 cmdlet 之前进行确认。 有关详细信息，请参阅下列文章：

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### System.String

可以通过管道将包含路径（但不是文本路径）的字符串传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

`Remove-Item`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

如果在不使用 **递归** 参数的情况下尝试删除包含项的文件夹，该 cmdlet 会提示确认。 使用不 `-Confirm:$false` 会禁止显示提示。 这是设计的结果。

## 相关链接

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
