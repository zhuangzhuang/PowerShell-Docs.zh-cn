---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 0775940f210cb028d7a0919bb8e5ca9f256b70d8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598456"
---
# Get-Host

## 摘要
获取表示当前主机程序的对象。

## SYNTAX

```
Get-Host [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Host` cmdlet 将获取一个表示托管 Windows PowerShell 的程序的对象。

默认显示内容包括 Windows PowerShell 版本号以及主机使用的当前区域和语言设置，但是主机对象包含大量信息，其中包括有关当前正在运行的 Windows PowerShell 版本以及 Windows PowerShell 的当前区域性和 UI 区域性的详细信息。 你还可以使用此 cmdlet 自定义主机程序用户界面的功能，如文本和背景色。

## 示例

### 示例1：获取有关 PowerShell 控制台主机的信息

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

此命令显示有关 Windows PowerShell 控制台的信息，在本示例中，该控制台是 Windows PowerShell 的当前主机程序。 它包括主机的名称、主机中正在运行的 Windows PowerShell 版本，以及当前区域性和 UI 区域性。

Version、UI、CurrentCulture、CurrentUICulture、PrivateData 和 Runspace 属性都包含一个具有一些非常有用的属性的对象。 后面的示例将检查这些属性。

### 示例2：调整 PowerShell 窗口的大小

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

此命令将 Windows PowerShell 窗口重新调整为 10 x 10 像素。

### 示例3：获取主机的 PowerShell 版本

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

此命令获取有关主机中运行的 Windows PowerShell 版本的详细信息。
你可以查看这些值，但不能更改它们。

的版本属性 `Get-Host` 包含 **system.object** 对象。 此命令使用管道运算符 (|) 将版本对象发送到 `Format-List` cmdlet。 该 `Format-List` 命令使用 *Property* 参数，其中的值为 all ( * ) ，以显示版本对象的所有属性和属性值。

### 示例4：获取主机的当前区域性

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
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
```

此命令获取有关主机中运行的 Windows PowerShell 的当前区域性设置的详细信息。 这与 cmdlet 返回的信息相同 `Get-Culture` 。

同样， **CurrentUICulture** 属性返回与返回的对象相同的对象 `Get-UICulture` 。

宿主对象的 CurrentCulture 属性包含一个对象 **。** 此命令使用管道运算符 (|) 将 **CultureInfo** 对象发送到 `Format-List` cmdlet。 该 `Format-List` 命令使用值为 all ( * ) 的 *Property* 参数来显示 **CultureInfo** 对象的所有属性和属性值。

### 示例5：获取当前区域性的 DateTimeFormat

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
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
```

此命令返回有关 Windows PowerShell 使用的当前区域性的 DateTimeFormat 的详细信息。

宿主对象的 **CurrentCulture** 属性包含 **CultureInfo** 对象，而该对象又具有许多有用的属性。 其中， **DateTimeFormat** 属性包含一个 **DateTimeFormatInfo** 对象，该对象具有许多有用的属性。

若要查找存储在对象属性中的对象的类型，请使用 `Get-Member` cmdlet。 若要显示对象的属性值，请使用 `Format-List` cmdlet。

### 示例6：获取主机的 RawUI 属性

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

此命令显示主机对象的 **RawUI** 属性的属性。 通过更改这些值，可以更改主机程序的外观。

### 示例7：设置 PowerShell 控制台的背景色

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

这些命令将 Windows PowerShell 控制台的背景色更改为黑色。 **Cls** 命令是函数的别名，该 `Clear-Host` 函数可清除屏幕并将整个屏幕更改为新的颜色。

此更改仅在当前会话中有效。 若要更改所有会话的控制台背景色，请将该命令添加到 Windows PowerShell 配置文件。

### 示例8：设置错误消息的背景色

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

此命令将错误消息的背景色更改为白色。

此命令使用 `$Host` 自动变量，该变量包含当前主机程序的主机对象。 `Get-Host` 返回包含的同一对象 `$Host` ，以便可以将它们互换使用。

此命令使用的 **PrivateData** 属性 `$Host` 作为其 ErrorBackgroundColor 属性。 查看中的对象的所有属性 `$Host` 。PrivateData 属性，请键入 `$host.privatedata | format-list *` 。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无
不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.Internal.Host.InternalHost

`Get-Host` 返回一个 **system.management.automation.internal.host.internalhost** 对象，该对象为。

## 注释

`$Host`自动变量包含返回的同一对象 `Get-Host` ，您可以使用相同的方法来使用它。 同样， `$PSCulture` 和 `$PSUICulture` 自动变量包含的对象与主机对象的 CurrentCulture 和 CurrentUICulture 属性包含的对象相同。 你可以交替使用这些功能。

有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

## 相关链接

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Read-Host](Read-Host.md)

[Write-Host](Write-Host.md)

