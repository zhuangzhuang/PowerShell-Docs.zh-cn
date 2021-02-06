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
# <span data-ttu-id="d57a4-102">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="d57a4-102">Get-Culture</span></span>

## <span data-ttu-id="d57a4-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d57a4-103">SYNOPSIS</span></span>
<span data-ttu-id="d57a4-104">获取操作系统中设置的当前区域性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-104">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="d57a4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d57a4-105">SYNTAX</span></span>

### <span data-ttu-id="d57a4-106">CurrentCulture (默认值) </span><span class="sxs-lookup"><span data-stu-id="d57a4-106">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="d57a4-107">名称</span><span class="sxs-lookup"><span data-stu-id="d57a4-107">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="d57a4-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d57a4-108">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="d57a4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d57a4-109">DESCRIPTION</span></span>

<span data-ttu-id="d57a4-110">`Get-Culture`Cmdlet 获取有关当前区域性设置的信息。</span><span class="sxs-lookup"><span data-stu-id="d57a4-110">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span> <span data-ttu-id="d57a4-111">这包括有关系统上的当前语言设置的信息（例如键盘布局）以及项的显示格式（例如数字、货币和日期）。</span><span class="sxs-lookup"><span data-stu-id="d57a4-111">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="d57a4-112">你还可以使用 `Get-UICulture` cmdlet 来获取系统上的当前用户界面区域性，并使用国际模块中的 [集区域性](/powershell/module/international/set-culture) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d57a4-112">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture) cmdlet in the International module.</span></span> <span data-ttu-id="d57a4-113">用户界面 UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。</span><span class="sxs-lookup"><span data-stu-id="d57a4-113">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="d57a4-114">示例</span><span class="sxs-lookup"><span data-stu-id="d57a4-114">EXAMPLES</span></span>

### <span data-ttu-id="d57a4-115">示例1：获取区域性设置</span><span class="sxs-lookup"><span data-stu-id="d57a4-115">Example 1: Get culture settings</span></span>

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="d57a4-116">此命令显示有关计算机上的区域设置的信息。</span><span class="sxs-lookup"><span data-stu-id="d57a4-116">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="d57a4-117">示例2：设置区域性对象属性的格式</span><span class="sxs-lookup"><span data-stu-id="d57a4-117">Example 2: Format the properties of a culture object</span></span>

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

<span data-ttu-id="d57a4-118">此示例演示区域性对象中的大量数据。</span><span class="sxs-lookup"><span data-stu-id="d57a4-118">This example demonstrates the vast amount of data in the culture object.</span></span> <span data-ttu-id="d57a4-119">它演示如何显示对象的属性和子属性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-119">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="d57a4-120">第一个命令使用 `Get-Culture` cmdlet 来获取计算机上的当前区域性设置。</span><span class="sxs-lookup"><span data-stu-id="d57a4-120">The first command uses the `Get-Culture` cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="d57a4-121">它将生成的区域性对象存储在 `$C` 变量中。</span><span class="sxs-lookup"><span data-stu-id="d57a4-121">It stores the resulting culture object in the `$C` variable.</span></span>

<span data-ttu-id="d57a4-122">第二个命令显示区域性对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-122">The second command displays all of the properties of the culture object.</span></span> <span data-ttu-id="d57a4-123">它使用管道运算符 (`|`) 将中的区域性对象发送 `$C` 到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d57a4-123">It uses a pipeline operator (`|`) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span> <span data-ttu-id="d57a4-124">它使用 **Property** 参数显示对象的所有 (`*`) 属性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-124">It uses the **Property** parameter to display all (`*`) properties of the object.</span></span> <span data-ttu-id="d57a4-125">此命令可以缩写为 `$c | fl *` 。</span><span class="sxs-lookup"><span data-stu-id="d57a4-125">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="d57a4-126">剩余的命令使用点表示法来显示对象属性的值，从而探索区域性对象的属性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-126">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span> <span data-ttu-id="d57a4-127">你可以使用此表示法显示对象的任何属性的值。</span><span class="sxs-lookup"><span data-stu-id="d57a4-127">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="d57a4-128">第三个命令使用点表示法显示区域性对象的 **Calendar** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d57a4-128">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="d57a4-129">第四个命令使用点表示法显示区域性对象的 **DataTimeFormat** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d57a4-129">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="d57a4-130">许多对象属性具有属性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-130">Many object properties have properties.</span></span> <span data-ttu-id="d57a4-131">第五个命令使用点表示法显示 **DateTimeFormat** 属性的 **FirstDayOfWeek** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d57a4-131">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="d57a4-132">示例3：获取特定区域性</span><span class="sxs-lookup"><span data-stu-id="d57a4-132">Example 3: Get a specific culture</span></span>

<span data-ttu-id="d57a4-133">获取法国法语的 CultureInfo 对象。</span><span class="sxs-lookup"><span data-stu-id="d57a4-133">Get the CultureInfo object for French in France.</span></span>

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## <span data-ttu-id="d57a4-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d57a4-134">PARAMETERS</span></span>

### <span data-ttu-id="d57a4-135">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d57a4-135">-ListAvailable</span></span>

<span data-ttu-id="d57a4-136">检索当前操作系统支持的所有区域性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-136">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="d57a4-137">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="d57a4-137">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="d57a4-138">-Name</span><span class="sxs-lookup"><span data-stu-id="d57a4-138">-Name</span></span>

<span data-ttu-id="d57a4-139">基于名称检索特定区域性。</span><span class="sxs-lookup"><span data-stu-id="d57a4-139">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="d57a4-140">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="d57a4-140">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="d57a4-141">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="d57a4-141">-NoUserOverrides</span></span>

<span data-ttu-id="d57a4-142">忽略当前区域性的用户更改。</span><span class="sxs-lookup"><span data-stu-id="d57a4-142">Ignore user changes for current culture.</span></span>

<span data-ttu-id="d57a4-143">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="d57a4-143">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="d57a4-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d57a4-144">CommonParameters</span></span>

<span data-ttu-id="d57a4-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d57a4-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d57a4-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d57a4-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d57a4-147">输入</span><span class="sxs-lookup"><span data-stu-id="d57a4-147">INPUTS</span></span>

### <span data-ttu-id="d57a4-148">无</span><span class="sxs-lookup"><span data-stu-id="d57a4-148">None</span></span>

<span data-ttu-id="d57a4-149">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d57a4-149">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d57a4-150">输出</span><span class="sxs-lookup"><span data-stu-id="d57a4-150">OUTPUTS</span></span>

### <span data-ttu-id="d57a4-151">System.Globalization.CultureInfo</span><span class="sxs-lookup"><span data-stu-id="d57a4-151">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="d57a4-152">`Get-Culture` 返回表示当前区域性的对象。</span><span class="sxs-lookup"><span data-stu-id="d57a4-152">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="d57a4-153">注释</span><span class="sxs-lookup"><span data-stu-id="d57a4-153">NOTES</span></span>

<span data-ttu-id="d57a4-154">你还可以使用 `$PsCulture` 和 `$PsUICulture` 变量。</span><span class="sxs-lookup"><span data-stu-id="d57a4-154">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="d57a4-155">`$PsCulture`变量存储当前区域性的名称， `$PsUICulture` 变量存储当前 UI 区域性的名称。</span><span class="sxs-lookup"><span data-stu-id="d57a4-155">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="d57a4-156">相关链接</span><span class="sxs-lookup"><span data-stu-id="d57a4-156">RELATED LINKS</span></span>

[<span data-ttu-id="d57a4-157">Set-Culture</span><span class="sxs-lookup"><span data-stu-id="d57a4-157">Set-Culture</span></span>](/powershell/module/international/set-culture)

[<span data-ttu-id="d57a4-158">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="d57a4-158">Get-UICulture</span></span>](Get-UICulture.md)
