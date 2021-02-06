---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e3a066957ab1e6935049003f8ccf55aee8bb7c94
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598873"
---
# Out-File

## 摘要
将输出发送到文件。

## SYNTAX

### ByPath（默认值）

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Out-File`Cmdlet 可将输出发送到文件。 它会隐式使用 PowerShell 的格式化系统以写入文件。 文件接收与终端相同的显示表示形式。 这意味着，如果所有输入对象都是字符串，则输出可能不适合进行编程处理。
需要为输出指定参数时，请使用 `Out-File` （而不是重定向运算符） (`>`) 。 有关重定向的详细信息，请参阅 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)。

## 示例

### 示例1：发送输出并创建文件

此示例显示了如何将本地计算机的进程的列表发送给文件。 如果文件不存在，则 `Out-File` 在指定的路径中创建文件。

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

`Get-Process`Cmdlet 将获取在本地计算机上运行的进程的列表。 **进程** 对象将通过管道向下发送到 `Out-File` cmdlet。 `Out-File` 使用 **FilePath** 参数，并在当前目录中创建一个名为 **Process.txt** 的文件。 此 `Get-Content` 命令从文件中获取内容，并在 PowerShell 控制台中显示内容。

### 示例2：防止覆盖现有文件

此示例可防止覆盖现有文件。 默认情况下，将 `Out-File` 覆盖现有文件。

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

`Get-Process`Cmdlet 将获取在本地计算机上运行的进程的列表。 **进程** 对象将通过管道向下发送到 `Out-File` cmdlet。 `Out-File` 使用 **FilePath** 参数，并尝试写入当前目录中名为 **Process.txt** 的文件。 **NoClobber** 参数可防止文件被覆盖，并显示一条消息，指出该文件已存在。

### 示例3：将输出发送到 ASCII 格式的文件

此示例演示如何使用特定的编码类型对输出进行编码。

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

`Get-Process`Cmdlet 将获取在本地计算机上运行的进程的列表。 **进程** 对象存储在变量中 `$Procs` 。 `Out-File` 使用 **FilePath** 参数，并在当前目录中创建一个名为 **Process.txt** 的文件。 **InputObject** 参数将中的进程对象传递 `$Procs` 给 **Process.txt** 的文件。 **Encoding** 参数将输出转换为 **ASCII** 格式。 **Width** 参数将文件中的每一行限制为50个字符，因此某些数据可能会被截断。

### 示例4：使用提供程序并将输出发送到文件

此示例演示 `Out-File` 当你不在 **FileSystem** 提供程序驱动器中时如何使用 cmdlet。 使用 `Get-PSProvider` cmdlet 查看本地计算机上的提供程序。 有关详细信息，请参阅 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)。

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

该 `Set-Location` 命令使用 **Path** 参数将当前位置设置为注册表提供程序 `Alias:` 。 `Get-Location`Cmdlet 显示的完整路径 `Alias:` 。
`Get-ChildItem` 将对象向下发送到 `Out-File` cmdlet。 `Out-File` 使用 **FilePath** 参数指定输出的完整路径和文件名， **C:\TestDir\AliasNames.txt**。 `Get-Content`Cmdlet 使用 **Path** 参数，并在 PowerShell 控制台中显示文件的内容。

## PARAMETERS

### -Append

将输出添加到现有文件的末尾。

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

### -Encoding

指定目标文件的编码类型。 默认值是 `utf8NoBOM`。

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
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定输出文件的路径。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

重写只读特性并覆盖现有的只读文件。 **Force** 参数不会覆盖安全限制。

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

### -InputObject

指定要写入文件的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定输出文件的路径。 **LiteralPath** 参数的使用方式与键入的完全相同。
不接受通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。 有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

**NoClobber** 可防止覆盖现有文件，并显示一条消息，指出该文件已存在。 默认情况下，如果指定路径中存在文件，则 `Out-File` 将覆盖该文件而不发出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

指定写入文件的内容不以换行符结尾。 输入对象的字符串表示形式连接起来以形成输出。 不会在输出字符串之间插入空格或换行符。 在最后一个输出字符串之后不添加任何行。

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

### -Width

指定输出的每一行中的字符数。 将截断任何额外字符，不换行。 如果未使用此参数，则由主机的特征确定宽度。 PowerShell 控制台的默认值为80个字符。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Out-File` 。

## 输出

### 无

`Out-File` 不会生成任何输出。

## 注释

输入对象将自动设置为在终端中的格式，但你可以使用 `Format-*` cmdlet 显式控制输出到文件的格式。 例如，`Get-Date | Format-List | Out-File out.txt`

若要将 PowerShell 命令的输出发送到 `Out-File` cmdlet，请使用管道。 另外，还可以将数据存储在变量中，并使用 **InputObject** 参数将数据传递给 `Out-File` cmdlet。

`Out-File` 将数据保存到文件，但不会向管道生成任何输出对象。

## 相关链接

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-String](Out-String.md)

[Tee-Object](Tee-Object.md)

