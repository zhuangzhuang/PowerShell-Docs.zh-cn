---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: ee2d8b8a3b736a59b5af4a81710a0d29dd2238d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596018"
---
# Copy-Item

## 摘要
将项从一个位置复制到另一个位置。

## SYNTAX

### Path（默认值）

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## DESCRIPTION

`Copy-Item`Cmdlet 将项从一个位置复制到同一命名空间中的另一个位置。
例如，它可以将文件复制到文件夹，但无法将文件复制到证书驱动器。

此 cmdlet 不会剪切或删除要复制的项。 Cmdlet 可复制的特定项取决于公开该项的 PowerShell 提供程序。 例如，它可以复制文件系统驱动器中的文件和目录以及注册表驱动器中的注册表项和条目。

此 cmdlet 可以复制和重命名同一命令中的项。 若要重命名某个项，请在 **Destination** 参数的值中输入新名称。 若要重命名某个项而不复制该项，请使用 `Rename-Item` cmdlet。

## 示例

### 示例1：将文件复制到指定的目录

此示例将 `mar1604.log.txt` 文件复制到 `C:\Presentation` 目录。 不会删除原始文件。

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### 示例2：将目录内容复制到现有目录

此示例将目录的内容复制 `C:\Logfiles` 到现有目录中 `C:\Drawings` 。 `Logfiles`不复制此目录。

如果 `Logfiles` 目录在子目录中包含文件，则会将这些子目录原样复制到其文件树中。 默认情况下， **Container** 参数设置为 **True**，这将保留目录结构。

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> 如果需要 `Logfiles` 在副本中包含目录，请 `\*` 从 **路径** 中删除。
> 例如：
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### 示例3：将目录和内容复制到新目录

此示例将复制 `C:\Logfiles` 源目录的内容并创建一个新的目标目录。 在中创建新的目标目录 `\Logs` `C:\Drawings` 。

若要包括源目录的名称，请复制到现有目标目录，如 **示例 2** 所示。 或者，将新的目标目录命名为与源目录相同。

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> 如果 **路径** 包含 `\*` ，则会将目录的所有文件内容（包括子目录树）复制到新的目标目录。 例如：
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### 示例4：将文件复制到指定的目录并重命名文件

此示例使用 `Copy-Item` cmdlet 将 `Get-Widget.ps1` 脚本从 `\\Server01\Share` 目录复制到 `\\Server12\ScriptArchive` 目录。 作为复制操作的一部分，该命令会将项名称从更改 `Get-Widget.ps1` 为 `Get-Widget.ps1.txt` ，以便可以将其附加到电子邮件中。

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### 示例5：将文件复制到远程计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

该 `Copy-Item` cmdlet `test.log` `D:\Folder001` 使用存储在变量中的会话信息，将文件夹中的文件夹复制到 `C:\Folder001_Copy` 远程计算机上的文件夹 `$Session` 。 不会删除原始文件。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### 示例6：将文件夹复制到远程计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

`Copy-Item`Cmdlet `D:\Folder002` `C:\Folder002_Copy` 使用存储在变量中的会话信息将文件夹复制到远程计算机上的目录中 `$Session` 。 不使用 **递归** 开关复制任何子文件夹或文件。
如果文件夹尚不存在，则该操作将创建该 `Folder002_Copy` 文件夹。

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### 示例7：以递归方式将文件夹的全部内容复制到远程计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

`Copy-Item`Cmdlet `D:\Folder003` `C:\Folder003_Copy` 使用存储在变量中的会话信息，将文件夹中的全部内容复制到远程计算机上的目录中 `$Session` 。 子文件夹将会原样复制到其文件树中。 如果文件夹尚不存在，则该操作将创建该 `Folder003_Copy` 文件夹。

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### 示例8：将文件复制到远程计算机，然后重命名该文件

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

该 `Copy-Item` cmdlet `scriptingexample.ps1` `D:\Folder004` 使用存储在变量中的会话信息，将文件夹中的文件夹复制到 `C:\Folder004_Copy` 远程计算机上的文件夹 `$Session` 。 作为复制操作的一部分，该命令会将项名称从更改 `scriptingexample.ps1` 为 `scriptingexample_copy.ps1` ，以便可以将其附加到电子邮件中。 不会删除原始文件。

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### 示例9：将远程文件复制到本地计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

该 `Copy-Item` cmdlet `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 使用存储在变量中的会话信息从远程文件夹复制到本地文件夹 `$Session` 。 不会删除原始文件。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 示例10：将远程文件夹的全部内容复制到本地计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

`Copy-Item`Cmdlet `C:\MyRemoteData\scripts` `D:\MyLocalData` 使用变量中存储的会话信息将远程文件夹中的全部内容复制到本地文件夹 `$Session` 。 如果 "脚本" 文件夹的子文件夹中包含文件，则会将这些子文件夹原样复制到其文件树中。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 示例11：以递归方式将远程文件夹的全部内容复制到本地计算机

使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。

`Copy-Item`Cmdlet `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 使用变量中存储的会话信息将远程文件夹中的全部内容复制到本地文件夹 `$Session` 。 由于使用了 **递归** 参数，因此，如果脚本文件夹尚不存在，则该操作将创建它们。 如果 "脚本" 文件夹的子文件夹中包含文件，则会将这些子文件夹原样复制到其文件树中。

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### 示例12：以递归方式将文件从文件夹树复制到当前文件夹中

此示例演示如何将文件从多级文件夹结构复制到单个平面文件夹中。
前三个命令显示现有文件夹结构和两个文件的内容，两个文件都是名称 `file3.txt` 。

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

`Copy-Item`Cmdlet 将 **容器** 参数设置为 `$false` 。 这会导致复制源文件夹的内容，但不会保留文件夹结构。 请注意，具有相同名称的文件在目标文件夹中被覆盖。

## PARAMETERS

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

### -Container

指示此 cmdlet 在复制操作期间保留容器对象。 默认情况下， **Container** 参数设置为 **True**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

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

指定新位置的路径。 默认为当前目录。

若要重命名要复制的项，请在 **Destination** 参数的值中指定新名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
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

指示此 cmdlet 将复制不能更改的项，如复制只读文件或别名。

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

### -FromSession

指定要从中复制远程文件的 **PSSession** 对象。 使用此参数时， **路径** 和 **LiteralPath** 参数将引用远程计算机上的本地路径。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

返回一个对象，该对象表示正在处理的项。 默认情况下，此 cmdlet 不会生成任何输出。

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

指定为要复制的项的路径（作为字符串数组）。 允许使用通配符。

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

指示此 cmdlet 执行递归复制。

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

### -ToSession

指定远程文件要复制到的 **PSSession** 对象。 如果使用此参数，则 **目标** 参数会引用远程计算机上的本地路径。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

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

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet。

## 输出

### 无或表示复制的项的对象

当使用 **PassThru** 参数时，此 cmdlet 将返回一个对象，该对象表示复制的项。 否则，此 cmdlet 不会生成任何输出。

## 注释

此 cmdlet 用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Item](Clear-Item.md)

[Get-Item](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

