---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: 819591c6004d6185958376ac8f84c42b9bfbf460
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603374"
---
# Import-Csv

## 摘要
使用逗号分隔值 (CSV) 文件中的项创建类似表的自定义对象。

## SYNTAX

### DelimiterPath (默认值) 

```
Import-Csv [[-Delimiter] <Char>] [-Path] <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### DelimiterLiteralPath

```
Import-Csv [[-Delimiter] <Char>] -LiteralPath <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CulturePath

```
Import-Csv [-Path] <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
Import-Csv -LiteralPath <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

## DESCRIPTION

`Import-Csv`Cmdlet 从 CSV 文件中的项创建类似表的自定义对象。 CSV 文件中的每列将成为自定义对象的属性，行中的项将成为属性值。 `Import-Csv` 适用于任何 CSV 文件，包括由 cmdlet 生成的文件 `Export-Csv` 。

您可以使用 cmdlet 的参数 `Import-Csv` 来指定列标题行和项分隔符，或指示将 `Import-Csv` 当前区域性的列表分隔符用作项分隔符。

你还可以使用 `ConvertTo-Csv` 和 `ConvertFrom-Csv` cmdlet 将对象转换为 CSV 字符串 (和后) 。 这些 cmdlet 与 `Export-CSV` 和 `Import-Csv` cmdlet 相同，不同之处在于它们不处理文件。

如果 CSV 文件中的标题行条目包含空值或 null 值，则 PowerShell 将插入默认标题行名称并显示一条警告消息。

从 PowerShell 6.0 开始， `Import-Csv` 现在支持 W3C 扩展日志文件格式。

## 示例

### 示例1：导入进程对象

此示例显示了如何导出然后导入进程对象的 CSV 文件。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

`Get-Process`Cmdlet 将处理对象向下发送到 `Export-Csv` 。 `Export-Csv`Cmdlet 将进程对象转换为 CSV 字符串，并将这些字符串保存在 Processes.csv 文件中。 `Import-Csv`Cmdlet 从 Processes.csv 文件导入 CSV 字符串。
字符串保存在 `$P` 变量中。 将 `$P` 变量向下发送到 `Get-Member` cmdlet，该 cmdlet 显示导入的 CSV 字符串的属性。 `$P`变量将通过管道向下发送到 `Format-Table` cmdlet 并显示对象。

### 示例2：指定分隔符

此示例演示如何使用 cmdlet 的 **分隔符** 参数 `Import-Csv` 。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

`Get-Process`Cmdlet 将进程对象向下发送到 `Export-Csv` 。 `Export-Csv`Cmdlet 将进程对象转换为 CSV 字符串，并将这些字符串保存在 Processes.csv 文件中。
**分隔符** 参数用于指定冒号分隔符。 `Import-Csv`Cmdlet 从 Processes.csv 文件导入 CSV 字符串。 字符串保存在 `$P` 变量中。 到 `$P` 变量将通过管道向下发送到 `Format-Table` cmdlet。

### 示例3：指定分隔符的当前区域性

此示例演示如何将 `Import-Csv` cmdlet 与 **UseCulture** 参数一起使用。

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

`Get-Culture`Cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** 获取当前区域性的默认列表分隔符。 `Get-Process`Cmdlet 将进程对象向下发送到 `Export-Csv` 。 `Export-Csv`Cmdlet 将进程对象转换为 CSV 字符串，并将这些字符串保存在 Processes.csv 文件中。 **UseCulture** 参数使用当前区域性的默认列表分隔符。 `Import-Csv`Cmdlet 从 Processes.csv 文件导入 CSV 字符串。

### 示例4：更改导入的对象中的属性名称

此示例演示如何使用的 **Header** 参数 `Import-Csv` 来更改生成的导入对象中的属性的名称。

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Cmdlet 可启动运行的后台作业 `Get-Process` 。 作业对象会通过管道向下发送到 `Export-Csv` cmdlet 并转换为 CSV 字符串。 **NoTypeInformation** 参数从 CSV 输出中删除类型信息标头，在 PowerShell Core 中是可选的。
`$Header`变量包含一个自定义标头，用于替换以下默认值： **HasMoreData**、 **JobStateInfo**、 **PSBeginTime**、 **PSEndTime** 和 **PSJobTypeName**。 `$A`变量使用 `Get-Content` cmdlet 从 Jobs.csv 文件获取 CSV 字符串。 `$A`变量用于从文件中移除默认标头。 `Out-File`Cmdlet 将 Jobs.csv 文件的新版本保存在 `$A` 变量中。 `Import-Csv`Cmdlet 将导入 Jobs.csv 文件并使用 **标头** 参数应用该 `$Header` 变量。 `$J`变量包含导入的 **PSCustomObject** ，并在 PowerShell 控制台中显示该对象。

### 示例5：使用 CSV 文件创建自定义对象

此示例演示如何通过使用 CSV 文件在 PowerShell 中创建自定义对象。

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

若要创建 Links.csv 文件，请使用输出中显示的值 `Get-Content` 。

`Get-Content`Cmdlet 将显示 Links.csv 文件。 `Import-Csv`Cmdlet 将导入 Links.csv 文件。 **标头** 参数指定属性名称 **LinkId** 和 **TopicTitle**。 这些对象存储在变量中 `$A` 。 `Get-Member`Cmdlet 显示 **标头** 参数中的属性名称。 `Where-Object`Cmdlet 将选择具有包含 **别名** 的 **TopicTitle** 属性的对象。

### 示例6：导入缺少值的 CSV

此示例演示 `Import-Csv` 当 CSV 文件中的标题行包含 null 值或空值时，PowerShell 中的 cmdlet 是如何响应的。 `Import-Csv` 替换成为返回的对象的属性名称的缺失标题行的默认名称 `Import-Csv` 。

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

若要创建 Projects.csv 文件，请使用示例的输出中所示的值 `Get-Content` 。

`Get-Content`Cmdlet 将显示 Projects.csv 文件。 标题行缺少 **项目名称** 与 **已完成** 的值。 `Import-Csv`Cmdlet 将导入 Projects.csv 文件并显示一条警告消息，因为 **H1** 为默认标头名称。 `(Import-Csv -Path
.\Projects.csv).H1`命令获取 **H1** 属性值并显示警告。

## PARAMETERS

### -Delimiter

指定用于分隔 CSV 文件中的属性值的分隔符。
默认值为逗号 (,)。

输入一个字符，例如冒号 (:)。
若要指定分号 (; ) 将其括在单引号内。

如果在文件中指定了实际字符串分隔符以外的其他字符，则 `Import-Csv` 无法从 CSV 字符串创建对象，并将返回 csv 字符串。

```yaml
Type: System.Char
Parameter Sets: DelimiterPath, DelimiterLiteralPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

为导入的 CSV 文件指定编码。 默认值是 `utf8NoBOM`。

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

### -Header

为导入的文件指定备用列标题行。 列标题确定由创建的对象的属性名称 `Import-Csv` 。

以逗号分隔的列表形式输入列标头。 不要将标头字符串括在引号内。 用单引号将每个列标题括起来。

如果输入的列标题少于数据列，则会丢弃剩余的数据列。 如果输入的列标题多于数据列，则将创建包含空数据列的其他列标题。

使用 Header 参数时，从 CSV 文件中删除原始标题行。 否则，将 `Import-Csv` 从标题行中的项创建额外的对象。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定要导入的 CSV 文件的路径。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: DelimiterLiteralPath, CultureLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要导入的 CSV 文件的路径。
还可以通过管道将路径传递给 `Import-Csv` 。

```yaml
Type: System.String[]
Parameter Sets: DelimiterPath, CulturePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

将当前区域性的列表分隔符用作项分隔符。 若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CulturePath, CultureLiteralPath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给 `Import-Csv` 。

## 输出

### 对象

此 cmdlet 将返回 CSV 文件中的内容所描述的对象。

## 注释

由于导入的对象是对象类型的 CSV 版本，因此它们不会被格式化对象类型的非 CSV 版本的 PowerShell 类型格式条目识别和格式化。

命令的结果 `Import-Csv` 是一个字符串集合，这些字符串构成类似于表的自定义对象。 每行都是单独的字符串，因此可以使用对象的 **count** 属性对表行进行计数。 这些列是对象的属性，行中的项是属性值。

列标题行确定了列数和列名称。 列名称也是对象的属性的名称。 第一行将被解释为列标题，除非使用 **Header** 参数指定列标题。 如果任何行具有的值多于标题行，则忽略额外的值。

如果列标题行缺少值或包含 null 值或空值， `Import-Csv` 则将使用 **H** 后跟一个用于缺少的列标题和属性名称的数字。

在 CSV 文件中，通过以逗号分隔的对象属性值列表来表示每个对象。 使用对象的 **ToString ( # B1** 方法将属性值转换为字符串，因此它们由属性值的名称表示。 `Export-Csv` 不导出对象的方法。

`Import-Csv` 还支持 W3C 扩展日志格式。 以开头的行被 `#` 视为注释并被忽略，除非注释以开头 `#Fields:` 并包含列名称的分隔列表。 在这种情况下，cmdlet 将使用这些列名称。 这是 Windows IIS 和其他 web 服务器日志的标准格式。 有关详细信息，请参阅 [扩展日志文件格式](https://www.w3.org/TR/WD-logfile.html)。

## 相关链接

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[导出-Csv](Export-Csv.md)

[Get-Culture](Get-Culture.md)

