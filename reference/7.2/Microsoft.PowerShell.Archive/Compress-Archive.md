---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 58807ba0745a6b09e7956547425c489b427d4f4b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596209"
---
# Compress-Archive

## 摘要
从指定的文件和目录创建压缩的存档文件或压缩文件。

## SYNTAX

### Path（默认值）

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Compress-Archive`Cmdlet 从一个或多个指定的文件或目录创建压缩文件或压缩文件。 存档将多个文件（具有可选压缩）打包到一个压缩文件中，以便于分发和存储。 可以使用 **CompressionLevel** 参数指定的压缩算法来压缩存档文件。

`Compress-Archive`Cmdlet 使用 MICROSOFT .NET API [System.IO.Compression.Zip存档](/dotnet/api/system.io.compression.ziparchive)来压缩文件。
最大文件大小为 2 GB，因为存在基础 API 限制。

一些示例使用展开来减少代码示例的行长度。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 示例

### 示例1：压缩文件以创建存档文件

此示例压缩来自不同目录的文件，并创建存档文件。 通配符用于获取具有特定文件扩展名的所有文件。 存档文件中没有目录结构，因为该 **路径** 仅指定文件名。

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

**Path** 参数接受带有通配符的特定文件名和文件名 `*.vsd` 。 **路径** 使用以逗号分隔的列表从不同的目录中获取文件。 压缩级别是 **最快** 的，可减少处理时间。 **DestinationPath** 参数指定文件的位置 `Draft.zip` 。 `Draft.zip`文件包含扩展名为的文件 `Draftdoc.docx` 以及所有文件 `.vsd` 。

### 示例2：使用 LiteralPath 压缩文件

此示例将压缩特定的命名文件并创建一个新的存档文件。 存档文件中没有目录结构，因为该 **路径** 仅指定文件名。

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

使用绝对路径和文件名，因为 **LiteralPath** 参数不接受通配符。 **路径** 使用以逗号分隔的列表从不同的目录中获取文件。 压缩级别是 **最快** 的，可减少处理时间。 **DestinationPath** 参数指定文件的位置 `Draft.zip` 。 `Draft.zip`文件仅包含 `Draftdoc.docx` 和 `diagram2.vsd` 。

### 示例3：压缩包含根目录的目录

此示例将压缩目录，并创建 **包含** 根目录及其所有文件和子目录的存档文件。 存档文件具有目录结构，因为 **路径** 指定了根目录。

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 参数指定根目录 `C:\Reference` 。 **DestinationPath** 参数指定存档文件的位置。 `Draft.zip`存档包括 `Reference` 根目录及其所有文件和子目录。

### 示例4：压缩排除根目录的目录

此示例将压缩目录，并创建一个 **排除** 根目录的存档文件，因为 **路径** 使用的星号 (`*`) 通配符。 存档包含包含根目录文件和子目录的目录结构。

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 参数指定根目录， `C:\Reference` 其中星号 (`*`) 通配符。 **DestinationPath** 参数指定存档文件的位置。 `Draft.zip`存档包含根目录的文件和子目录。 `Reference`从存档中排除了根目录。

### 示例5：仅压缩根目录中的文件

此示例仅压缩根目录中的文件，并创建存档文件。 存档中没有目录结构，因为只有文件被压缩。

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 参数指定根目录， `C:\Reference` 并将 **星形** (`*.*`) 通配符。 **DestinationPath** 参数指定存档文件的位置。 `Draft.zip`存档只包含 `Reference` 根目录文件，并排除根目录。

### 示例6：使用管道对文件进行存档

此示例将文件沿管道向下发送，以创建存档。 存档文件中没有目录结构，因为该 **路径** 仅指定文件名。

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem` 使用 **Path** 参数指定不同目录中的两个文件。 每个文件由一个 **FileInfo** 对象表示，并沿管道向下发送到 `Compress-Archive` 。
在中存档两个指定的文件 `PipelineFiles.zip` 。

### 示例7：使用管道将目录存档

此示例向下发送目录，以创建存档。 文件作为 **FileInfo** 对象和目录作为 **DirectoryInfo** 对象发送。 存档的目录结构不包含根目录，但其文件和子目录都包括在存档中。

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem` 使用 **Path** 参数指定 `C:\LogFiles` 根目录。 每个 **FileInfo** 和 **DirectoryInfo** 对象都沿管道向下发送。

`Compress-Archive` 将每个对象添加到 `PipelineDir.zip` 存档。 未指定 **Path** 参数，因为管道对象收到参数位置0。

### 示例8：递归如何影响存档

此示例演示递归如何在存档中复制文件。 例如，如果将 `Get-ChildItem` 与 **递归** 参数一起使用。 作为递归过程，每个 **FileInfo** 和 **DirectoryInfo** 对象都向下发送到该管道并添加到存档。

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

`C:\TestLog`目录不包含任何文件。 它包含一个 `testsub` 包含文件的名为的子目录 `testlog.txt` 。

`Get-ChildItem` 使用 **Path** 参数指定根目录 `C:\TestLog` 。 **递归** 参数处理文件和目录。 为 `testsub` 和 **FileInfo** 对象创建 DirectoryInfo 对象 `testlog.txt` 。

每个对象都向下发送到 `Compress-Archive` 。 **DestinationPath** 指定存档文件的位置。 未指定 **Path** 参数，因为管道对象收到参数位置0。

以下摘要说明了 `PipelineRecurse.zip` 包含重复文件的存档内容：

- **DirectoryInfo** 对象创建 `testsub` 目录并包含 `testlog.txt` 文件，该文件反映了原始目录结构。
- **FileInfo** 对象 `testlog.txt` 在存档的根中创建一个重复项。 由于递归将文件对象发送到，因此会创建重复的文件 `Compress-Archive` 。 此行为是预期行为，因为管道下发送的每个对象都会添加到存档。

### 示例9：更新现有存档文件

此示例将更新目录中的现有存档文件 `Draft.Zip` `C:\Archives` 。 在此示例中，现有存档文件包含根目录及其文件和子目录。

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

命令会更新 `Draft.Zip` 目录及其子目录中的现有文件的较新版本 `C:\Reference` 。 而且，已添加到 `C:\Reference` 或其子目录中的新文件将包含在更新的 `Draft.Zip` 存档中。

## PARAMETERS

### -CompressionLevel

指定创建存档文件时要应用的压缩量。 较快的压缩需要的文件创建时间较少，但可能导致文件大小较大。

如果未指定此参数，则该命令将使用默认值 " **最佳**"。

以下是此参数可接受的值：

- **最快**。 使用最快的压缩方法可减少处理时间。 更快的压缩可能导致文件大小较大。
- **NoCompression**。 不压缩源文件。
- **最佳**： 处理时间取决于文件大小。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
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

### -DestinationPath

此参数是必需的，它指定存档输出文件的路径。 **DestinationPath** 应包含压缩文件的名称，以及压缩文件的绝对或相对路径。

如果 **DestinationPath** 中的文件名没有 `.zip` 文件扩展名，则该 cmdlet 将添加 `.zip` 文件扩展名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

强制运行命令而不要求用户确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定想要添加到存档压缩文件的文件的路径。 与 **Path** 参数不同， **LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包含转义符，请将每个转义符括在单引号内，以指示 PowerShell 不要将任何字符解释为转义序列。
若要指定多个路径，并将文件包括在输出压缩文件的多个位置中，请使用逗号分隔这些路径。

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

使 cmdlet 输出一个表示已创建的存档文件的文件对象。

此参数是在 PowerShell 6.0 中引入的。

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

指定想要添加到存档压缩文件的文件的路径。 若要指定多个路径，并将文件包含在多个位置，请使用逗号分隔这些路径。

此参数接受通配符。 通配符用于将目录中的所有文件添加到存档文件。

将通配符用于根目录会影响存档内容：

- 若要创建 **包含** 根目录及其所有文件和子目录的存档，请在不带通配符的 **路径** 中指定根目录。 例如： `-Path C:\Reference`
- 若要创建 **排除** 根目录的存档，但 zips 所有文件和子目录，请使用星号 (`*`) 通配符。 例如： `-Path C:\Reference\*`
- 若要创建仅 zips 根目录中的文件的存档，请使用) 通配符 (**星形** `*.*` 。 根中的子目录不包括在存档中。 例如： `-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Update

通过使用具有相同名称的较新文件版本替换存档中较旧的文件版本来更新指定的存档。 此外，还可添加此参数，将文件添加到现有存档。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给一个或多个文件。

## 输出

### System.IO.FileInfo

当使用 **PassThru** 参数时，该 cmdlet 仅返回 **FileInfo** 对象。

## 注释

使用递归并沿管道向下发送对象可以在存档中复制文件。 例如，如果将 `Get-ChildItem` 与 **递归** 参数一起使用，则在管道中发送的每个 **FileInfo** 和 **DirectoryInfo** 对象将添加到存档。

[ZIP 文件规范](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)未指定对包含非 ASCII 字符的文件名进行编码的标准方法。 `Compress-Archive`Cmdlet 使用 utf-8 编码。 其他 ZIP 存档工具可以使用其他编码方案。 当使用不是使用 UTF-8 编码存储的文件名提取文件时， `Expand-Archive` 将使用存档中找到的原始值。 这可能会导致文件名不同于存储在存档中的源文件名。

## 相关链接

[Expand-Archive](Expand-Archive.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

