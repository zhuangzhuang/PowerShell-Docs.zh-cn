---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: ef44fefe68ef9674eb14ce494341bf04f477d55a
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693008"
---
# Add-Content

## 摘要
向指定的项中添加内容，如向文件中添加字词。

## SYNTAX

### Path（默认值）

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## DESCRIPTION

`Add-Content`Cmdlet 将内容追加到指定项或文件。 可以通过在命令中键入内容或通过指定包含内容的对象来指定内容。

如果需要为以下示例创建文件或目录，请参阅 " [新建项](New-Item.md)"。

## 示例

### 示例1：向所有文本文件添加字符串，但出现异常

此示例将一个值附加到当前目录中的文本文件，但基于文件的文件名排除文件。

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

**Path** 参数指定 `.txt` 当前目录中的所有文件，但 **Exclude** 参数将忽略与指定模式匹配的文件名。 **值** 参数指定写入文件的文本字符串。

### 示例2：将日期添加到指定文件的末尾

此示例将日期附加到当前目录中的文件，并在 PowerShell 控制台中显示日期。

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

`Add-Content`Cmdlet 将在当前目录中创建两个新文件。 **Value** 参数包含 cmdlet 的输出 `Get-Date` 。 **PassThru** 参数将添加的内容输出到管道。
由于没有其他 cmdlet 接收输出，因此它显示在 PowerShell 控制台中。
`Get-Content`Cmdlet 将显示更新后的文件 `DateTimeFile1.log` 。

### 示例3：将指定文件的内容添加到另一个文件

此示例从文件中获取内容，并将内容存储在变量中。 变量用于将内容追加到另一个文件中。

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- `Get-Content`Cmdlet 将获取的内容 `CopyFromFile.txt` ，并将内容存储在 `$From` 变量中。
- `Add-Content`Cmdlet `CopyToFile.txt` 使用变量的内容更新文件 `$From` 。
- `Get-Content`Cmdlet 将显示 CopyToFile.txt。

### 示例4：使用管道将指定文件的内容添加到另一个文件

此示例从文件中获取内容并将其传递给 `Add-Content` cmdlet。

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Cmdlet 将获取的内容 `CopyFromFile.txt` 。 结果将通过管道传递给 `Add-Content` cmdlet，后者会更新 `CopyToFile.txt` 。
最后一个 `Get-Content` cmdlet 显示 `CopyToFile.txt` 。

### 示例5：创建新文件并复制内容

此示例将创建一个新文件，并将现有文件的内容复制到新文件中。

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- `Add-Content`Cmdlet 使用 **Path** 和 **Value** 参数在当前目录中创建一个新文件。
- 该 `Get-Content` cmdlet 将获取现有文件的内容， `CopyFromFile.txt` 并将其传递给 **Value** 参数。 Cmdlet 两边的括号 `Get-Content` 可确保命令在命令开始前完成 `Add-Content` 。
- `Get-Content`Cmdlet 将显示新文件的内容 `NewFile.txt` 。

### 示例6：向只读文件中添加内容

即使 **IsReadOnly** 文件属性设置为 **True**，此命令也会向该文件添加一个值。
示例中包含创建只读文件的步骤。

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- `New-Item`Cmdlet 使用 **Path** 和 **ItemType** 参数 `IsReadOnlyTextFile.txt` 在当前目录中创建文件。
- `Set-ItemProperty`Cmdlet 使用 **Name** 和 **Value** 参数将文件的 **IsReadOnly** 属性更改为 True。
- 该 `Get-ChildItem` cmdlet 显示文件为空 (0) 并且 () 具有只读属性 `r` 。
- `Add-Content`Cmdlet 使用 **Path** 参数指定文件。 **Value** 参数包含要追加到文件中的文本字符串。 **Force** 参数将文本写入只读文件。
- `Get-Content`Cmdlet 使用 **Path** 参数显示文件的内容。

若要删除只读属性，请使用命令， `Set-ItemProperty` 并将 **Value** 参数设置为 `False` 。

### 示例7：使用筛选器与 Add-Content

可以为 cmdlet 指定筛选器 `Add-Content` 。 使用筛选器限定 **路径** 参数时，需要包含一个尾随星号 (`*`) ，以指示路径的内容。

以下命令将目录中所有文件的内容添加到 "完成" 一词 `*.txt` `C:\Temp` 。

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## PARAMETERS

### -AsByteStream

指定应以字节流的形式读取内容。 此参数是在 PowerShell 6.0 中引入的。

将 **AsByteStream** 参数与 **Encoding** 参数一起使用时，将出现警告。 **AsByteStream** 参数将忽略任何编码，并以字节流的形式返回输出。

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

指定目标文件的编码类型。 默认值是 `utf8NoBOM`。

Encoding 是 FileSystem 提供程序添加到 cmdlet 的动态参数 `Add-Content` 。 此参数仅在文件系统驱动器中有效。

此参数可接受的值如下所示：

- `ascii`：使用 ASCII (7 位) 字符集的编码。
- `bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。
- `bigendianutf32`：使用大字节序字节顺序编码为32格式。
- `oem`：使用 MS-DOS 和控制台程序的默认编码。
- `unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。
- `utf7`：以 UTF-7 格式进行编码。
- `utf8`：以 UTF-8 格式进行编码。
- `utf8BOM`：以 UTF-8 格式编码 (BOM) 
- `utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) 
- `utf32`：以32格式编码。

从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。 有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)

> [!NOTE]
> 不建议使用 **utf-7** _ _。 在 PowerShell 7.1 中，如果 `utf7` 为 _ *Encoding** 参数指定，则会写入警告。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
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

覆盖只读属性，从而允许你向只读文件中添加内容。 例如，**Force** 将覆盖只读属性或创建目录来完成文件路径，但它不会尝试更改文件权限。

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

### -NoNewline

指示此 cmdlet 不会将新的行或回车添加到内容。

输入对象的字符串表示形式连接起来以形成输出。 不会在输出字符串之间插入空格或换行符。 在最后一个输出字符串之后不添加任何行。

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

### -PassThru

返回一个表示所添加内容的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### -Path

指定用于接收其他内容的项的路径。
允许使用通配符。
此路径必须是指向该项的路径，而不是容器的路径。
例如，必须指定一个或多个文件的路径，而不是目录的路径。
如果指定多个路径，请使用逗号分隔这些路径。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

> [!NOTE]
> 此参数仅在 Windows 上可用。

指定内容的备用数据流。 如果该流不存在，则此 cmdlet 将创建它。 不支持通配符。

**Stream** 是 FileSystem 提供程序添加到的动态参数 `Add-Content` 。 此参数仅在文件系统驱动器中有效。

可以使用 `Add-Content` cmdlet 更改任何备用数据流的内容，例如 `Zone.Identifier` 。 但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。 如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。

此参数是在 PowerShell 3.0 中引入的。

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

### -Value

指定要添加的内容。 键入带引号的字符串，如 **此数据仅供内部使用**，或指定包含内容的对象，例如生成的 **DateTime** 对象 `Get-Date` 。

不能通过键入文件路径来指定文件内容，因为路径只是一个字符串。
您可以使用 `Get-Content` 命令获取内容并将其传递给 **Value** 参数。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.web、System.web 和 System.object

可以通过管道将值、路径或凭据传递给 `Set-Content` 。

## 输出

### None 或 System.String

当使用 **PassThru** 参数时，将 `Add-Content` 生成表示内容的 **system.string** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

- 将对象通过管道传递给时 `Add-Content` ，对象会在添加到项之前转换为字符串。 对象类型决定字符串格式，但该格式可能不同于该对象的默认显示。 若要控制字符串格式，请使用发送 cmdlet 的格式设置参数。
- 还可以 `Add-Content` 通过其内置别名来引用 `ac` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Add-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Content](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[New-Item](New-Item.md)

[Set-Content](Set-Content.md)
