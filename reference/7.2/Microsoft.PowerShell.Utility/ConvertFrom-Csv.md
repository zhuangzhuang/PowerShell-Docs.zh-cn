---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 951a1e4ecc46b401ae066bc3b138f264a4313e65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598678"
---
# ConvertFrom-Csv

## 摘要
将采用逗号分隔值 (CSV) 格式的对象属性转换为原始对象的 CSV 版本。

## SYNTAX

### Delimiter（默认值）

```
ConvertFrom-Csv [[-Delimiter] <Char>] [-InputObject] <PSObject[]> [-Header <String[]>]
 [<CommonParameters>]
```

### UseCulture

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-Csv`Cmdlet 可从 cmdlet 生成的 CSV 可变长度字符串创建对象 `ConvertTo-Csv` 。

您可以使用此 cmdlet 的参数来指定列标题行（它确定生成对象的属性名称），以指定项分隔符，或指示此 cmdlet 将当前区域性的列表分隔符用作分隔符。

创建的对象 `ConvertFrom-Csv` 是原始对象的 CSV 版本。 CSV 对象的属性值是原始对象的属性值的字符串版本。 对象的 CSV 版本不包含任何方法。

你还可以使用 `Export-Csv` 和 `Import-Csv` cmdlet 将对象转换为文件中的 CSV 字符串 (和后) 。 这些 cmdlet 与 `ConvertTo-Csv` 和 `ConvertFrom-Csv` cmdlet 相同，不同之处在于它们会将 CSV 字符串保存在文件中。

## 示例

### 示例1：将本地计算机上的进程转换为 CSV 格式

此示例显示了如何将本地计算机上的进程转换为 CSV 格式，然后将其还原为对象形式。

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

`Get-Process`Cmdlet 将进程向下发送到 `ConvertTo-Csv` 。 `ConvertTo-Csv`Cmdlet 可将进程对象转换为一系列 CSV 字符串。 该 `ConvertFrom-Csv` cmdlet 将 csv 字符串转换为原始进程对象的 csv 版本。 CSV 字符串保存在 `$P` 变量中。

### 示例2：将数据对象转换为 CSV 格式，然后转换为 CSV 对象格式

此示例演示如何将数据对象转换为 CSV 格式，然后再转换为 CSV 对象格式。

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

第一个命令使用将 `Get-Date` 当前日期和时间向下发送到 `ConvertTo-Csv` 。 `ConvertTo-Csv`Cmdlet 将日期对象转换为一系列 CSV 字符串。
**分隔符** 参数用于指定分号分隔符。 字符串保存在 `$Date` 变量中。

### 示例3：使用 header 参数更改属性的名称

此示例演示如何使用的 **Header** 参数 `ConvertFrom-Csv` 来更改生成的导入对象中的属性的名称。

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
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

`Start-Job`Cmdlet 可启动运行的后台作业 `Get-Process` 。 作业对象将向下发送到管道 `ConvertTo-Csv` 并转换为 CSV 字符串。 **NoTypeInformation** 参数从 CSV 输出中删除类型信息标头，在 PowerShell Core 中是可选的。 `$Header`变量包含一个自定义标头，用于替换以下默认值： **HasMoreData**、 **JobStateInfo**、 **PSBeginTime**、 **PSEndTime** 和 **PSJobTypeName**。 该 `$J` 变量包含 CSV 字符串，用于删除默认标头。 该 `ConvertFrom-Csv` cmdlet 将 CSV 字符串转换为 **PSCustomObject** ，并使用 **Header** 参数来应用 `$Header` 变量。

### 示例4：转换服务对象的 CSV 字符串

此示例演示如何将 `ConvertFrom-Csv` cmdlet 与 **UseCulture** 参数一起使用。

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

`Get-Culture`Cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** 获取当前区域性的默认列表分隔符。 `Get-Service`Cmdlet 将服务对象向下发送到 `ConvertTo-Csv` 。 将 `ConvertTo-Csv` 服务对象转换为一系列 CSV 字符串。 CSV 字符串存储在 `$Services` 变量中。 `ConvertFrom-Csv`Cmdlet 使用 **InputObject** 参数，并从变量转换 CSV 字符串 `$Services` 。 **UseCulture** 参数使用当前区域性的默认列表分隔符。

使用 **UseCulture** 参数时，请确保当前区域性的默认列表分隔符与 CSV 字符串中使用的分隔符相匹配。 否则， `ConvertFrom-Csv` 无法从 CSV 字符串生成对象。

## PARAMETERS

### -Delimiter

指定用于分隔 CSV 字符串中的属性值的分隔符。
默认值为逗号 (,)。

输入一个字符，例如冒号 (:)。
若要指定分号 (; ) 将其括在单引号内。

如果在文件中指定了实际字符串分隔符以外的其他字符，则 `ConvertFrom-Csv` 无法从 CSV 字符串创建对象，并将返回 csv 字符串。

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

### -Header

为导入的字符串指定替换列标题行。 列标题确定由创建的对象的属性名称 `ConvertFrom-Csv` 。

以逗号分隔的列表形式输入列标头。 不要将标头字符串括在引号内。 用单引号将每个列标题括起来。

如果输入的列标题少于数据列，则会丢弃剩余的数据列。 如果输入的列标题多于数据列，则将创建包含空数据列的其他列标题。

使用 **Header** 参数时，请省略 CSV 字符串中的列标题字符串。 否则，此 cmdlet 将从标题行中的项创建额外的对象。

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

### -InputObject

指定要转换为对象的 CSV 字符串。 输入一个包含 CSV 字符串的变量，或键入可获取 CSV 字符串的命令或表达式。 还可以通过管道将 CSV 字符串传递给 `ConvertFrom-Csv` 。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
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
Parameter Sets: UseCulture
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

可以通过管道将 CSV 字符串传递给此 cmdlet。

## 输出

### System.Management.Automation.PSObject

此 cmdlet 将返回 CSV 字符串中的属性所描述的对象。

## 注释

由于导入的对象是对象类型的 CSV 版本，因此它们不会被格式化对象类型的非 CSV 版本的 PowerShell 类型格式条目识别和格式化。

在 CSV 格式中，通过以逗号分隔的对象属性值列表来表示每个对象。 属性值使用对象) 的 **ToString ( # B2** 方法转换为字符串 (，因此它们由属性值的名称表示。 此 cmdlet 不会导出对象的方法。

## 相关链接

[ConvertTo-Csv](ConvertTo-Csv.md)

[导出-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)

