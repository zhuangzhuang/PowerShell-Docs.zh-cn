---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: b0e889b95d2724dfa395b1b4a00b5c9ea878cc82
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99595609"
---
# Export-Csv

## 摘要
将对象转换为一系列逗号分隔值 (CSV) 字符串，并将字符串保存到文件。

## SYNTAX

### Delimiter（默认值）

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseCulture

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## DESCRIPTION

`Export-CSV`Cmdlet 可创建你提交的对象的 CSV 文件。 每个对象都是一个行，其中包含以逗号分隔的对象属性值列表。 可以使用 `Export-CSV` cmdlet 创建电子表格并与接受 CSV 文件作为输入的程序共享数据。

在将对象发送到 cmdlet 之前，请不要设置它们的格式 `Export-CSV` 。 如果 `Export-CSV` 接收格式化对象，则 CSV 文件包含格式属性而不是对象属性。 若要仅导出对象的选定属性，请使用 `Select-Object` cmdlet。

## 示例

### 示例1：将进程属性导出到 CSV 文件

此示例选择具有特定属性的 **进程** 对象，将对象导出到 CSV 文件。

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

`Get-Process`Cmdlet 将获取 **进程** 对象。 **Name** 参数将输出筛选为仅包含 WmiPrvSE 进程对象。 进程对象将通过管道向下发送到 `Select-Object` cmdlet。 `Select-Object` 使用 **Property** 参数选择进程对象属性的子集。 进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。 **Path** 参数指定将 WmiData.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Import-Csv`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例2：将进程导出到逗号分隔的文件

此示例获取 **进程** 对象并将对象导出到 CSV 文件。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Process`Cmdlet 将获取 **进程** 对象。 进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。
**Path** 参数指定将 Processes.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例3：将进程导出为分号分隔的文件

此示例获取 **进程** 对象并将对象导出到带有分号分隔符的文件。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`Get-Process`Cmdlet 将获取 **进程** 对象。 进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。
**Path** 参数指定将 Processes.csv 文件保存到当前目录中。 **分隔符** 参数指定用分号分隔字符串值。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例4：使用当前区域性的列表分隔符导出进程

此示例获取 **进程** 对象并将对象导出到文件。 分隔符为当前区域性的列表分隔符。

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

该 `Get-Culture` cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** ，并显示当前区域性的默认列表分隔符。 `Get-Process`Cmdlet 将获取 **进程** 对象。
进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。 **Path** 参数指定将 Processes.csv 文件保存到当前目录中。 **UseCulture** 参数使用当前区域性的默认列表分隔符作为分隔符。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例5：导出具有类型信息的进程

此示例说明如何将 **#TYPE** 标头信息包含在 CSV 文件中。 **#TYPE** 标头在 PowerShell 6.0 之前的版本中是默认标头。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

`Get-Process`Cmdlet 将获取 **进程** 对象。 进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。
**Path** 参数指定将 Processes.csv 文件保存到当前目录中。 **IncludeTypeInformation** 在 CSV 输出中包含 **#TYPE** 信息标头。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例6：将对象导出并追加到 CSV 文件

此示例说明如何将对象导出到 CSV 文件，并使用 **Append** 参数将对象添加到现有文件中。

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

`Get-Service`Cmdlet 将获取服务对象。 **DisplayName** 参数返回包含 Word 应用程序的服务。 服务对象将通过管道向下发送到 `Select-Object` cmdlet。 `Select-Object` 使用 **Property** 参数来指定 **DisplayName** 和 **Status** 属性。 `$AppService`变量存储对象。

`$AppService`对象通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将服务对象转换为一系列 CSV 字符串。 **Path** 参数指定将 Services.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

`Get-Service`和 `Select-Object` cmdlet 对于包含 word Windows 的服务重复。 `$WinService`变量存储服务对象。 `Export-Csv`Cmdlet 使用 **Append** 参数指定将 `$WinService` 对象添加到现有 Services.csv 文件中。 此 `Get-Content` cmdlet 将重复显示已更新的文件，其中包含追加的数据。

### 示例7：管道内的格式 cmdlet 产生意外的结果

此示例说明为什么不在管道内使用格式 cmdlet 很重要。 收到意外的输出时，会对管道语法进行故障排除。

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

`Get-Date`Cmdlet 将获取 **DateTime** 对象。 对象通过管道向下发送到 `Select-Object` cmdlet。 `Select-Object` 使用 **Property** 参数来选择对象属性的子集。 对象通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将对象转换为 CSV 格式。 **Path** 参数指定将 DateTime.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的 CSV 文件。

当在 `Format-Table` 管道中使用 cmdlet 来选择属性时，会收到意外结果。 `Format-Table` 将表格式对象向下发送到 `Export-Csv` cmdlet，而不是 **DateTime** 对象。 `Export-Csv` 将表格式对象转换为一系列 CSV 字符串。 `Get-Content`Cmdlet 显示包含表格式对象的 CSV 文件。

### 示例8：使用 Force 参数覆盖只读文件

此示例创建一个空的只读文件，并使用 **Force** 参数更新该文件。

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`New-Item`Cmdlet 使用 **Path** 和 **ItemType** 参数创建当前目录中的 ReadOnly.csv 文件。 `Set-ItemProperty`Cmdlet 使用 **Name** 和 **Value** 参数将文件的 **IsReadOnly** 属性更改为 true。 `Get-Process`Cmdlet 将获取 **进程** 对象。 进程对象将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 将进程对象转换为一系列 CSV 字符串。 **Path** 参数指定将 ReadOnly.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。 输出显示该文件未写入，因为访问被拒绝。

将 **force** 参数添加到 `Export-Csv` cmdlet，以强制将导出写入文件。 `Get-Content`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例9：将 Force 参数与 Append 一起使用

此示例演示如何使用 **Force** 和 **Append** 参数。 如果组合这些参数，则不匹配的对象属性可以写入 CSV 文件。

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

表达式使用 **Name** 和 **Version** 属性创建 **PSCustomObject** 。 值存储在 `$Content` 变量中。 该 `$Content` 变量将通过管道向下发送到 `Export-Csv` cmdlet。 `Export-Csv` 使用 **Path** 参数，并将 ParmFile.csv 文件保存到当前目录中。 **NoTypeInformation** 参数从 CSV 输出中删除 **#TYPE** 信息标头，而在 PowerShell 6 中则不需要。

另一个表达式将创建 **PSCustomObject** ，其 **名称** 和 **版本** 属性为。 值存储在 `$AdditionalContent` 变量中。 该 `$AdditionalContent` 变量将通过管道向下发送到 `Export-Csv` cmdlet。 **Append** 参数用于向文件添加数据。 追加 **失败，因为****版本** 和版本之间存在属性名称不匹配的情况。

`Export-Csv`Cmdlet **force** 参数用于强制导出写入文件。 将丢弃 **Edition** 属性。 `Import-Csv`Cmdlet 使用 **Path** 参数显示位于当前目录中的文件。

### 示例10：导出到 CSV，并在两列两侧加上引号

此示例将 **DateTime** 对象转换为 CSV 字符串。

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### 示例11：仅在需要时导出到 CSV 且仅包含引号

此示例将 **DateTime** 对象转换为 CSV 字符串。

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## PARAMETERS

### -Append

使用此参数可 `Export-CSV` 将 CSV 输出添加到指定文件的末尾。 如果没有此参数， `Export-CSV` 则替换文件内容而不发出警告。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -Delimiter

指定分隔符以分隔属性值。 默认值为逗号 (`,`) 。 输入一个字符，例如冒号 (`:`) 。 若要指定分号 (`;`) ，请将其括在引号中。

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

为导出的 CSV 文件指定编码。 默认值是 `utf8NoBOM`。

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

### -Force

此参数允许 `Export-Csv` 覆盖具有 **只读** 属性的文件。

合并 **Force** 和 **Append** 参数时，可以将包含不匹配的属性的对象写入 CSV 文件。 只有与匹配的属性才会写入文件。 放弃不匹配的属性。

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

### -IncludeTypeInformation

使用此参数时，CSV 输出的第一行包含 **#TYPE** 后跟对象类型的完全限定名称。 例如， **#TYPE**"。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要导出为 CSV 字符串的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 还可以通过管道将对象传递给 `Export-CSV` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定指向 CSV 输出文件的路径。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包含转义符，请使用单引号。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

使用此参数，以便不 `Export-CSV` 会覆盖现有文件。 默认情况下，如果文件存在于指定的路径中，则 `Export-CSV` 将覆盖该文件而不发出警告。

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

### -NoTypeInformation

从输出中删除 **#TYPE** 信息标头。 此参数已成为 PowerShell 6.0 中的默认参数，包含它是为了向后兼容。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

一个必需的参数，用于指定要保存 CSV 输出文件的位置。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

将当前区域性的列表分隔符用作项分隔符。 若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

阻止对 cmdlet 进行处理或更改。 此输出显示了在运行 cmdlet 后将发生的情况。

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

### -QuoteFields

指定应括起来的列的名称。 使用此参数时，只有指定的列被括起来。 此参数是在 PowerShell 7.0 中添加的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseQuotes

指定在 CSV 文件中使用引号的时间。 可能的值有：

- 从不-不引用任何内容
- 始终将所有内容都括 (默认行为) 
- AsNeeded-仅包含分隔符字符的引号字段

此参数是在 PowerShell 7.0 中添加的。

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将具有扩展类型系统 (ETS) 适配器的任何对象传递给 `Export-CSV` 。

## 输出

### System.String

CSV 列表将发送到 Path 参数中指定的文件。

## 注释

`Export-CSV`Cmdlet 将提交的对象转换为一系列 CSV 字符串，并将它们保存在指定的文本文件中。 你可以使用将 `Export-CSV -IncludeTypeInformation` 对象保存在 csv 文件中，然后使用 `Import-Csv` CMDLET 从 csv 文件中的文本创建对象。

在 CSV 文件中，通过以逗号分隔的对象属性值列表来表示每个对象。 使用 **ToString ( # B1** 方法将属性值转换为字符串。 字符串由属性值名称表示。 `Export-CSV -IncludeTypeInformation` 不导出对象的方法。

CSV 字符串的输出如下所示：

- 如果使用了 **IncludeTypeInformation** ，则第一个字符串包含后跟对象类型的完全限定名称的 **#TYPE** 信息标头。
  例如， **#TYPE**"。
- 如果未使用 **IncludeTypeInformation** ，则第一个字符串包括列标题。 标头以逗号分隔的列表的形式包含第一个对象的属性名称。
- 其余字符串包含每个对象的属性值的逗号分隔列表。

从 PowerShell 6.0 开始，的默认行为 `Export-CSV` 是不包括 CSV 中的 **#TYPE** 信息，并且 **NoTypeInformation** 是隐含的。 **IncludeTypeInformation** 可用于包含 **#TYPE** 信息并模拟 `Export-CSV` PowerShell 6.0 之前的默认行为。

当你将多个对象提交到时 `Export-CSV` ，将 `Export-CSV` 根据你提交的第一个对象的属性来组织文件。 如果剩余的对象没有指定的属性之一，则该对象的属性值为 null，由两个连续的逗号表示。 如果剩余的对象有其他属性，这些属性值将不包括在文件中。

可以使用 `Import-Csv` cmdlet 从文件中的 CSV 字符串重新创建对象。 生成的对象是原始对象的 CSV 版本，这些版本由属性值的字符串表示形式组成，且不包括方法。

`ConvertTo-Csv`和 `ConvertFrom-Csv` cmdlet 将对象转换为 csv 字符串，并将对象转换为 csv 字符串。 `Export-CSV` 与相同 `ConvertTo-CSV` ，只不过它将 CSV 字符串保存在文件中。

## 相关链接

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
