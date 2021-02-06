---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: dc49f153adc22b7c2c943a4cc529ac155561228a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603397"
---
# Get-Culture

## 摘要
获取操作系统中设置的当前区域性。

## SYNTAX

### CurrentCulture (默认值) 

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### 名称

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### ListAvailable

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## DESCRIPTION

`Get-Culture`Cmdlet 获取有关当前区域性设置的信息。 这包括有关系统上的当前语言设置的信息（例如键盘布局）以及项的显示格式（例如数字、货币和日期）。

你还可以使用 `Get-UICulture` cmdlet 来获取系统上的当前用户界面区域性，并使用国际模块中的 [集区域性](/powershell/module/international/set-culture) cmdlet。 用户界面 UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。

## 示例

### 示例1：获取区域性设置

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

此命令显示有关计算机上的区域设置的信息。

### 示例2：设置区域性对象属性的格式

```powershell
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...}

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

此示例演示区域性对象中的大量数据。 它演示如何显示对象的属性和子属性。

第一个命令使用 `Get-Culture` cmdlet 来获取计算机上的当前区域性设置。
它将生成的区域性对象存储在 `$C` 变量中。

第二个命令显示区域性对象的所有属性。 它使用管道运算符 (`|`) 将中的区域性对象发送 `$C` 到 `Format-List` cmdlet。 它使用 **Property** 参数显示对象的所有 (`*`) 属性。 此命令可以缩写为 `$c | fl *` 。

剩余的命令使用点表示法来显示对象属性的值，从而探索区域性对象的属性。 你可以使用此表示法显示对象的任何属性的值。

第三个命令使用点表示法显示区域性对象的 **Calendar** 属性的值。

第四个命令使用点表示法显示区域性对象的 **DataTimeFormat** 属性的值。

许多对象属性具有属性。 第五个命令使用点表示法显示 **DateTimeFormat** 属性的 **FirstDayOfWeek** 属性的值。

### 示例3：获取特定区域性

获取法国法语的 CultureInfo 对象。

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## PARAMETERS

### -ListAvailable

检索当前操作系统支持的所有区域性。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

基于名称检索特定区域性。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoUserOverrides

忽略当前区域性的用户更改。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Globalization.CultureInfo

`Get-Culture` 返回表示当前区域性的对象。

## 注释

你还可以使用 `$PsCulture` 和 `$PsUICulture` 变量。 `$PsCulture`变量存储当前区域性的名称， `$PsUICulture` 变量存储当前 UI 区域性的名称。

## 相关链接

[Set-Culture](/powershell/module/international/set-culture)

[Get-UICulture](Get-UICulture.md)
