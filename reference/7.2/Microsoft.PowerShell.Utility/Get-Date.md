---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "99603594"
---
# Get-Date

## 摘要
获取当前日期和时间。

## SYNTAX

### Date（默认值）

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### DateUFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### UnixTimeSeconds

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### UnixTimeSecondsUFormat

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Date` cmdlet 将获取表示当前日期或指定日期的 **DateTime** 对象。 `Get-Date` 可以采用多种 .NET 和 UNIX 格式设置日期和时间的格式。 您可以使用 `Get-Date` 生成日期或时间字符串，然后将字符串发送到其他 cmdlet 或程序。

`Get-Date` 使用计算机的区域性设置来确定输出的格式。 若要查看计算机的设置，请使用 `(Get-Culture).DateTimeFormat` 。

## 示例

### 示例1：获取当前日期和时间

在此示例中， `Get-Date` 显示当前的系统日期和时间。 输出采用长日期和长时间格式。

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### 示例2：获取当前日期和时间的元素

此示例演示如何使用 `Get-Date` 获取日期或时间元素。 参数使用参数 **Date**、 **Time** 或 **DateTime**。

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date` 将 **DisplayHint** 参数与 **date** 参数一起使用，以仅获取日期。

### 示例3：使用 .NET 格式说明符获取日期和时间

在此示例中，.NET 格式说明符用于自定义输出的格式。 输出是一个 **字符串** 对象。

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date` 使用 **format** 参数指定若干格式说明符。

本示例中使用的 .NET 格式说明符定义如下：

| 说明符 |                      定义                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | 一周中的某一天-全名                           |
| `MM`      | 月份                                          |
| `dd`      | 每月的第几天-2 位数                           |
| `yyyy`    | 年份采用4位格式                                |
| `HH:mm`   | 时间采用24小时格式-无秒                    |
| `K`       | 与通用时间坐标 (UTC 的时区偏移量)  |

有关 .NET 格式说明符的详细信息，请参阅 [自定义日期和时间格式字符串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。

### 示例4：使用 UFormat 说明符获取日期和时间

在此示例中，使用了多个 **UFormat** 格式说明符来自定义输出的格式。
输出是一个 **字符串** 对象。

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date` 使用 **UFormat** 参数来指定若干格式说明符。

本示例中使用的 **UFormat** 格式说明符定义如下：

| 说明符 |                      定义                       |
| --------- | ----------------------------------------------------- |
| `%A`      | 一周中的某一天-全名                           |
| `%m`      | 月份                                          |
| `%d`      | 每月的第几天-2 位数                           |
| `%Y`      | 年份采用4位格式                                |
| `%R`      | 时间采用24小时格式-无秒                    |
| `%Z`      | 与通用时间坐标 (UTC 的时区偏移量)  |

有关有效 **UFormat** 格式说明符的列表，请参见 [注释](#notes) 部分。

### 示例5：获取日期是一年中的某一天

在此示例中，使用了一个属性来获取该年份中的数字日期。

公历的日期为365天，但闰年为366天。 例如，2020年12月31日为366。

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` 使用三个参数指定日期： **Year**、 **Month** 和 **Day**。 命令用括号括起来，以便 **DayofYear** 属性计算结果。

### 示例6：检查是否为夏令时调整了日期

此示例使用布尔方法来验证日期是否按夏令时进行调整。

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

变量 `$DST` 存储的结果 `Get-Date` 。 `$DST` 使用 **IsDaylightSavingTime** 方法来测试日期是否针对夏令时进行调整。

### 示例7：将当前时间转换为 UTC 时间

在此示例中，当前时间转换为 UTC 时间。 系统区域设置的 UTC 偏移量用于转换时间。 " [注释](#notes) " 部分中的表列出了有效的 **UFormat** 格式说明符。

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` 使用带有格式说明符的 **UFormat** 参数显示当前系统日期和时间。 格式说明符 **% Z** 表示 UTC 偏移量 **07**。

`$Time`变量存储当前的系统日期和时间。 `$Time` 使用 **ToUniversalTime ( # B1** 方法，根据计算机的 UTC 偏移量转换时间。

### 示例8：创建时间戳

在此示例中，格式说明符为目录名称创建时间戳 **字符串** 对象。 时间戳包含日期、时间和 UTC 的偏移量。

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

`$timestamp`变量存储命令的结果 `Get-Date` 。 `Get-Date` 使用带有小写格式说明符的 **format** 参数 `o` 创建时间戳 **字符串** 对象。 将对象向下发送到 `ForEach-Object` 。 **ScriptBlock** 包含 `$_` 表示当前管道对象的变量。 时间戳字符串由用句点替换的冒号分隔。

`New-Item` 使用 **Path** 参数指定新目录的位置。 路径包含 `$timestamp` 变量作为目录名称。 **类型** 参数指定创建目录。

### 示例9：转换 Unix 时间戳

此示例将 (从 1970-01-01 0:00:00) 到 DateTime 的秒数表示的 Unix 时间转换为。

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### 示例10：返回解释为 UTC 的日期值

此示例演示如何将日期值解释为其 UTC 等效值。 在此示例中，此计算机设置为 **太平洋标准时间**。 默认情况下， `Get-Date` 返回该时区的值。 使用 **AsUTC** 参数将值转换为 UTC 等效时间。

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## PARAMETERS

### -AsUTC

以 UTC 格式将日期值转换为等效的时间。

此参数是在 PowerShell 7.1 中引入的。

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

### -Date

指定日期和时间。 时间是可选的，如果未指定，则返回00:00:00。

输入日期和时间，格式为标准的系统区域设置。

例如，在美国英语中：

`Get-Date -Date "6/25/2019 12:30:22"` 返回 2019 12:30:22 的星期二6月25日

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -日

指定显示月份中的某一天。 输入一个介于 1 到 31 之间的值。

如果指定的值大于每月的天数，则 PowerShell 会将天数添加到月份。 例如， `Get-Date -Month 2 -Day 31` 显示 3 **月 3** 日，而不是 **2 月31日**。

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

### -DisplayHint

确定要显示日期和时间的哪些元素。

接受的值如下所示：

- **Date**：仅显示日期
- **Time**：仅显示时间
- **DateTime**：显示日期和时间

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Format

采用格式说明符指示的 Microsoft .NET Framework 格式显示日期和时间。
**Format** 参数输出 **String** 对象。

有关可用的 .NET 格式说明符的列表，请参阅 [自定义日期和时间格式字符串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。

使用 **Format** 参数时， `Get-Date` 仅获取显示日期所需的 **DateTime** 对象的属性。 因此，**DateTime** 对象的某些属性和方法可能不可用。

从 PowerShell 5.0 开始，可以使用以下附加格式作为 **Format** 参数的值。

- **FileDate**。 以本地时间表示的当前日期的文件或路径友好表示形式。 格式 `yyyyMMdd` (区分大小写，使用四位数年份、2位数月和两位数表示的日期) 。 例如：
  20190627.

- **FileDateUniversal**。 在通用时间 (UTC) 的当前日期的文件或路径友好表示形式。 格式 `yyyyMMddZ` (区分大小写，使用四位数的年份、2位数的月份、2位数的日期和字母 `Z` 作为 UTC 指示器) 。 例如：20190627Z。

- **FileDateTime**。 以24小时格式表示的当前日期和时间的文件或路径友好表示形式。 格式 `yyyyMMddTHHmmssffff` (区分大小写，使用四位数的年份、2位数的月份、2位数的日期、字母作为时间分隔符、2位数小时、2位数字 `T` 分钟、2位数秒和4位数毫秒) 。 例如：20190627T0840107271。

- **FileDateTimeUniversal**。 以24小时格式 (UTC) 的当前日期和时间的文件或路径友好表示形式。 格式 `yyyyMMddTHHmmssffffZ` (区分大小写，使用四位数的年份、2位数的月份、2位数的日期、字母 `T` 作为时间分隔符、2位数的小时、2位数字的分钟、2位秒、4位数的毫秒以及与 `Z` UTC 指示器) 的字母。 例如：20190627T1540500718Z。

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -小时

指定要显示的小时。 输入一个介于0到23之间的值。

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

### -毫秒

指定日期中的毫秒。 输入一个介于0到999之间的值。

此参数是在 PowerShell 3.0 中引入的。

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

### -分钟

指定要显示的分钟。 输入一个介于0到59之间的值。

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

### -月

指定要显示的月份。 输入一个介于1和12之间的值。

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

### -秒

指定要显示的秒。 输入一个介于0到59之间的值。

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

### -UFormat

采用 UNIX 格式显示日期和时间。 **UFormat** 参数输出 string 对象。

**UFormat** 说明符前面有一个百分号 (`%`) ，例如，、 `%m` `%d` 和 `%Y` 。 " [注释](#notes) " 部分包含有效 **UFormat 说明符** 的表。

使用 **UFormat** 参数时， `Get-Date` 仅获取显示日期所需的 **DateTime** 对象的属性。 因此，**DateTime** 对象的某些属性和方法可能不可用。

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnixTimeSeconds

自1970年1月1日起0:00:00，以秒表示的日期和时间。

此参数是在 PowerShell 7.1 中引入的。

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Year

指定要显示的年份。 输入一个介于1到9999之间的值。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 管道输入

`Get-Date` 接受管道输入。 例如，`Get-ChildItem | Get-Date`。

## 输出

### System.object 或 System.string

`Get-Date` 返回 **DateTime** 对象，但使用 **Format** 和 **UFormat** 参数。 **Format** 或 **UFormat** 参数返回 **String** 对象。

如果将 **DateTime** 对象向下发送到 `Add-Content` 需要字符串输入的 cmdlet （如），则 PowerShell 会将对象转换为 **字符串** 对象。

方法 `(Get-Date).ToString()` 将 **DateTime** 对象转换为 **String** 对象。

若要显示对象的属性和方法，请将对象向下发送到 `Get-Member` 。
例如，`Get-Date | Get-Member`。

## 注释

**DateTime** 对象采用系统区域设置的长日期和长时间格式。

下表显示了有效的 **UFormat 说明符** ：

| 格式说明符 |                                 含义                     |         示例          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | 一周中的某一天-全名                                             | 星期一                   |
| `%a` | 星期几-缩写名称                                      | Mon                      |
| `%B` | 月份名称-完整                                                       | 1 月                  |
| `%b` | 月份名称-缩写                                                | 一月                      |
| `%C` | 纪元                                                                 | 20 2019              |
| `%c` | 日期和时间-缩写                                             | Thu 27 08:44:18 2019 年6月 |
| `%D` | 日期采用 mm/dd/yy 格式                                                 | 06/27/19                 |
| `%d` | 每月的第几天-2 位数                                             | 05                       |
| `%e` | 月份中的第几天，如果只有单个数字，则以空格开头           | \<space\>5               |
| `%F` | 采用 YYYY-MM-DD 格式的日期，等于% Y-% m-% d (ISO 8601 日期格式)  | 2019-06-27               |
| `%G` | 与 "Y" 相同                                                             |                          |
| `%g` | 与 "y" 相同                                                             |                          |
| `%H` | 24小时制格式的小时                                                  | 17                       |
| `%h` | 与 "b" 相同                                                             |                          |
| `%I` | 12小时制格式                                                  | 05                       |
| `%j` | 一年中的第几天                                                         | 1-366                    |
| `%k` | 与 "H" 相同                                                             |                          |
| `%l` | 与 (大写的 "I" 相同)                                               | 05                       |
| `%M` | 分钟数                                                                 | 35                       |
| `%m` | 月份                                                            | 06                       |
| `%n` | 换行符                                                       |                          |
| `%p` | AM 或 PM                                                                |                          |
| `%R` | 时间采用24小时格式-无秒                                      | 17:45                    |
| `%r` | 采用12小时格式的时间                                                  | 上午09:15:36              |
| `%S` | 秒                                                                 | 05                       |
| `%s` | 自 00:00:00 1970 年1月1日起经过的秒数                          | 1150451174               |
| `%t` | 水平制表符                                                |                          |
| `%T` | 24 小时格式的时间                                                  | 17:45:52                 |
| `%U` | 与 "W" 相同                                                             |                          |
| `%u` | 周日期-数字                                                | 星期日 = 0               |
| `%V` | 一年中的某一周                                                        | 01-53                    |
| `%w` | 与 "u" 相同                                                             |                          |
| `%W` | 一年中的某一周                                                        | 00-52                    |
| `%X` | 与 "t" 相同                                                             |                          |
| `%x` | 区域设置的标准格式日期                                      | 美国英语06/27/19  |
| `%Y` | 年份采用4位格式                                                  | 2019                     |
| `%y` | 年份（2位数字格式）                                                  | 19                       |
| `%Z` | 与通用时间坐标 (UTC 的时区偏移量)                    | -07                      |

## 相关链接

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Culture](Get-Culture.md)

[Get-Member](Get-Member.md)

[New-Item](../Microsoft.PowerShell.Management/New-Item.md)

[New-TimeSpan](New-TimeSpan.md)

[Set-Date](Set-Date.md)
