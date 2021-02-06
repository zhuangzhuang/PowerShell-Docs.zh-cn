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
# <span data-ttu-id="3a196-102">Get-Host</span><span class="sxs-lookup"><span data-stu-id="3a196-102">Get-Host</span></span>

## <span data-ttu-id="3a196-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3a196-103">SYNOPSIS</span></span>
<span data-ttu-id="3a196-104">获取表示当前主机程序的对象。</span><span class="sxs-lookup"><span data-stu-id="3a196-104">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="3a196-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3a196-105">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="3a196-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a196-106">DESCRIPTION</span></span>

<span data-ttu-id="3a196-107">该 `Get-Host` cmdlet 将获取一个表示托管 Windows PowerShell 的程序的对象。</span><span class="sxs-lookup"><span data-stu-id="3a196-107">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="3a196-108">默认显示内容包括 Windows PowerShell 版本号以及主机使用的当前区域和语言设置，但是主机对象包含大量信息，其中包括有关当前正在运行的 Windows PowerShell 版本以及 Windows PowerShell 的当前区域性和 UI 区域性的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a196-108">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="3a196-109">你还可以使用此 cmdlet 自定义主机程序用户界面的功能，如文本和背景色。</span><span class="sxs-lookup"><span data-stu-id="3a196-109">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="3a196-110">示例</span><span class="sxs-lookup"><span data-stu-id="3a196-110">EXAMPLES</span></span>

### <span data-ttu-id="3a196-111">示例1：获取有关 PowerShell 控制台主机的信息</span><span class="sxs-lookup"><span data-stu-id="3a196-111">Example 1: Get information about the PowerShell console host</span></span>

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

<span data-ttu-id="3a196-112">此命令显示有关 Windows PowerShell 控制台的信息，在本示例中，该控制台是 Windows PowerShell 的当前主机程序。</span><span class="sxs-lookup"><span data-stu-id="3a196-112">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="3a196-113">它包括主机的名称、主机中正在运行的 Windows PowerShell 版本，以及当前区域性和 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="3a196-113">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="3a196-114">Version、UI、CurrentCulture、CurrentUICulture、PrivateData 和 Runspace 属性都包含一个具有一些非常有用的属性的对象。</span><span class="sxs-lookup"><span data-stu-id="3a196-114">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="3a196-115">后面的示例将检查这些属性。</span><span class="sxs-lookup"><span data-stu-id="3a196-115">Later examples examine these properties.</span></span>

### <span data-ttu-id="3a196-116">示例2：调整 PowerShell 窗口的大小</span><span class="sxs-lookup"><span data-stu-id="3a196-116">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="3a196-117">此命令将 Windows PowerShell 窗口重新调整为 10 x 10 像素。</span><span class="sxs-lookup"><span data-stu-id="3a196-117">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="3a196-118">示例3：获取主机的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="3a196-118">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="3a196-119">此命令获取有关主机中运行的 Windows PowerShell 版本的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a196-119">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="3a196-120">你可以查看这些值，但不能更改它们。</span><span class="sxs-lookup"><span data-stu-id="3a196-120">You can view, but not change, these values.</span></span>

<span data-ttu-id="3a196-121">的版本属性 `Get-Host` 包含 **system.object** 对象。</span><span class="sxs-lookup"><span data-stu-id="3a196-121">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="3a196-122">此命令使用管道运算符 (|) 将版本对象发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a196-122">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="3a196-123">该 `Format-List` 命令使用 *Property* 参数，其中的值为 all ( \* ) ，以显示版本对象的所有属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="3a196-123">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="3a196-124">示例4：获取主机的当前区域性</span><span class="sxs-lookup"><span data-stu-id="3a196-124">Example 4: Get the current culture for the host</span></span>

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

<span data-ttu-id="3a196-125">此命令获取有关主机中运行的 Windows PowerShell 的当前区域性设置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a196-125">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="3a196-126">这与 cmdlet 返回的信息相同 `Get-Culture` 。</span><span class="sxs-lookup"><span data-stu-id="3a196-126">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="3a196-127">同样， **CurrentUICulture** 属性返回与返回的对象相同的对象 `Get-UICulture` 。</span><span class="sxs-lookup"><span data-stu-id="3a196-127">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="3a196-128">宿主对象的 CurrentCulture 属性包含一个对象 **。**</span><span class="sxs-lookup"><span data-stu-id="3a196-128">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="3a196-129">此命令使用管道运算符 (|) 将 **CultureInfo** 对象发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a196-129">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="3a196-130">该 `Format-List` 命令使用值为 all ( \* ) 的 *Property* 参数来显示 **CultureInfo** 对象的所有属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="3a196-130">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="3a196-131">示例5：获取当前区域性的 DateTimeFormat</span><span class="sxs-lookup"><span data-stu-id="3a196-131">Example 5: Get the DateTimeFormat for the current culture</span></span>

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

<span data-ttu-id="3a196-132">此命令返回有关 Windows PowerShell 使用的当前区域性的 DateTimeFormat 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a196-132">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="3a196-133">宿主对象的 **CurrentCulture** 属性包含 **CultureInfo** 对象，而该对象又具有许多有用的属性。</span><span class="sxs-lookup"><span data-stu-id="3a196-133">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="3a196-134">其中， **DateTimeFormat** 属性包含一个 **DateTimeFormatInfo** 对象，该对象具有许多有用的属性。</span><span class="sxs-lookup"><span data-stu-id="3a196-134">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="3a196-135">若要查找存储在对象属性中的对象的类型，请使用 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a196-135">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="3a196-136">若要显示对象的属性值，请使用 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a196-136">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="3a196-137">示例6：获取主机的 RawUI 属性</span><span class="sxs-lookup"><span data-stu-id="3a196-137">Example 6: Get the RawUI property for the host</span></span>

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

<span data-ttu-id="3a196-138">此命令显示主机对象的 **RawUI** 属性的属性。</span><span class="sxs-lookup"><span data-stu-id="3a196-138">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="3a196-139">通过更改这些值，可以更改主机程序的外观。</span><span class="sxs-lookup"><span data-stu-id="3a196-139">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="3a196-140">示例7：设置 PowerShell 控制台的背景色</span><span class="sxs-lookup"><span data-stu-id="3a196-140">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="3a196-141">这些命令将 Windows PowerShell 控制台的背景色更改为黑色。</span><span class="sxs-lookup"><span data-stu-id="3a196-141">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="3a196-142">**Cls** 命令是函数的别名，该 `Clear-Host` 函数可清除屏幕并将整个屏幕更改为新的颜色。</span><span class="sxs-lookup"><span data-stu-id="3a196-142">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="3a196-143">此更改仅在当前会话中有效。</span><span class="sxs-lookup"><span data-stu-id="3a196-143">This change is effective only in the current session.</span></span> <span data-ttu-id="3a196-144">若要更改所有会话的控制台背景色，请将该命令添加到 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="3a196-144">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="3a196-145">示例8：设置错误消息的背景色</span><span class="sxs-lookup"><span data-stu-id="3a196-145">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="3a196-146">此命令将错误消息的背景色更改为白色。</span><span class="sxs-lookup"><span data-stu-id="3a196-146">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="3a196-147">此命令使用 `$Host` 自动变量，该变量包含当前主机程序的主机对象。</span><span class="sxs-lookup"><span data-stu-id="3a196-147">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="3a196-148">`Get-Host` 返回包含的同一对象 `$Host` ，以便可以将它们互换使用。</span><span class="sxs-lookup"><span data-stu-id="3a196-148">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="3a196-149">此命令使用的 **PrivateData** 属性 `$Host` 作为其 ErrorBackgroundColor 属性。</span><span class="sxs-lookup"><span data-stu-id="3a196-149">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="3a196-150">查看中的对象的所有属性 `$Host` 。PrivateData 属性，请键入 `$host.privatedata | format-list *` 。</span><span class="sxs-lookup"><span data-stu-id="3a196-150">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="3a196-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3a196-151">PARAMETERS</span></span>

### <span data-ttu-id="3a196-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a196-152">CommonParameters</span></span>

<span data-ttu-id="3a196-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3a196-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a196-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3a196-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a196-155">输入</span><span class="sxs-lookup"><span data-stu-id="3a196-155">INPUTS</span></span>

### <span data-ttu-id="3a196-156">无</span><span class="sxs-lookup"><span data-stu-id="3a196-156">None</span></span>
<span data-ttu-id="3a196-157">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a196-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3a196-158">输出</span><span class="sxs-lookup"><span data-stu-id="3a196-158">OUTPUTS</span></span>

### <span data-ttu-id="3a196-159">System.Management.Automation.Internal.Host.InternalHost</span><span class="sxs-lookup"><span data-stu-id="3a196-159">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="3a196-160">`Get-Host` 返回一个 **system.management.automation.internal.host.internalhost** 对象，该对象为。</span><span class="sxs-lookup"><span data-stu-id="3a196-160">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="3a196-161">注释</span><span class="sxs-lookup"><span data-stu-id="3a196-161">NOTES</span></span>

<span data-ttu-id="3a196-162">`$Host`自动变量包含返回的同一对象 `Get-Host` ，您可以使用相同的方法来使用它。</span><span class="sxs-lookup"><span data-stu-id="3a196-162">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="3a196-163">同样， `$PSCulture` 和 `$PSUICulture` 自动变量包含的对象与主机对象的 CurrentCulture 和 CurrentUICulture 属性包含的对象相同。</span><span class="sxs-lookup"><span data-stu-id="3a196-163">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="3a196-164">你可以交替使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="3a196-164">You can use these features interchangeably.</span></span>

<span data-ttu-id="3a196-165">有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3a196-165">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="3a196-166">相关链接</span><span class="sxs-lookup"><span data-stu-id="3a196-166">RELATED LINKS</span></span>

[<span data-ttu-id="3a196-167">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="3a196-167">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="3a196-168">Read-Host</span><span class="sxs-lookup"><span data-stu-id="3a196-168">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="3a196-169">Write-Host</span><span class="sxs-lookup"><span data-stu-id="3a196-169">Write-Host</span></span>](Write-Host.md)

