---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 0f35eea0dfca76b535aad3bdb663d55c224a11d2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595603"
---
# <span data-ttu-id="2011c-102">Set-Date</span><span class="sxs-lookup"><span data-stu-id="2011c-102">Set-Date</span></span>

## <span data-ttu-id="2011c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="2011c-103">SYNOPSIS</span></span>
<span data-ttu-id="2011c-104">将计算机上的系统时间更改为你指定的时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-104">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="2011c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2011c-105">SYNTAX</span></span>

### <span data-ttu-id="2011c-106">Date（默认值）</span><span class="sxs-lookup"><span data-stu-id="2011c-106">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2011c-107">Adjust</span><span class="sxs-lookup"><span data-stu-id="2011c-107">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2011c-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2011c-108">DESCRIPTION</span></span>

<span data-ttu-id="2011c-109">`Set-Date`Cmdlet 将计算机上的系统日期和时间更改为指定的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-109">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="2011c-110">可以通过键入字符串或将 **DateTime** 或 **TimeSpan** 对象传递到来指定新的日期和/或时间 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-110">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="2011c-111">若要指定新的日期或时间，请使用 **date** 参数。</span><span class="sxs-lookup"><span data-stu-id="2011c-111">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="2011c-112">若要指定更改间隔，请使用 " **调整** " 参数。</span><span class="sxs-lookup"><span data-stu-id="2011c-112">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="2011c-113">示例</span><span class="sxs-lookup"><span data-stu-id="2011c-113">EXAMPLES</span></span>

### <span data-ttu-id="2011c-114">示例1：向系统日期加上三天</span><span class="sxs-lookup"><span data-stu-id="2011c-114">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="2011c-115">此命令将在当前系统日期上加上三天。</span><span class="sxs-lookup"><span data-stu-id="2011c-115">This command adds three days to the current system date.</span></span>
<span data-ttu-id="2011c-116">它不影响时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-116">It does not affect the time.</span></span>
<span data-ttu-id="2011c-117">此命令使用 **date** 参数来指定日期。</span><span class="sxs-lookup"><span data-stu-id="2011c-117">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="2011c-118">`Get-Date`Cmdlet 将当前日期返回为 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="2011c-118">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="2011c-119">**DateTime** 对象的 **AddDays** 方法将指定的天数 (3) 添加到当前 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="2011c-119">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="2011c-120">示例2：将系统时钟改回10分钟</span><span class="sxs-lookup"><span data-stu-id="2011c-120">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="2011c-121">此示例将当前系统时间设置为10分钟。</span><span class="sxs-lookup"><span data-stu-id="2011c-121">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="2011c-122">使用 " **调整** " 参数可以指定区域设置的标准时间格式的更改间隔 (减去十分钟) 。</span><span class="sxs-lookup"><span data-stu-id="2011c-122">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="2011c-123">**DisplayHint** 参数指示 PowerShell 仅显示时间，但不影响返回的 **DateTime** 对象 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-123">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="2011c-124">示例3：将日期和时间设置为变量值</span><span class="sxs-lookup"><span data-stu-id="2011c-124">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="2011c-125">这些命令将本地计算机上的系统日期和时间更改为保存在变量中的日期和时间 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-125">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="2011c-126">第一个命令获取日期并将其存储在中 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-126">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="2011c-127">第二个命令使用 **Date** 参数将 **DateTime** 对象传递 `$T` 给 `Set-Date` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2011c-127">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="2011c-128">示例4：将90分钟添加到系统时钟</span><span class="sxs-lookup"><span data-stu-id="2011c-128">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="2011c-129">这些命令将本地计算机上的系统时间前调 90 分钟。</span><span class="sxs-lookup"><span data-stu-id="2011c-129">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="2011c-130">第一个命令使用 `New-TimeSpan` cmdlet 创建一个具有90分钟间隔的 **TimeSpan** 对象，并将其保存在 `$90mins` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2011c-130">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="2011c-131">第二个命令使用的 **调整** 参数 `Set-Date` ，通过变量中的 **TimeSpan** 对象值来调整日期 `$90mins` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-131">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="2011c-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2011c-132">PARAMETERS</span></span>

### <span data-ttu-id="2011c-133">-Adjust</span><span class="sxs-lookup"><span data-stu-id="2011c-133">-Adjust</span></span>

<span data-ttu-id="2011c-134">指定此 cmdlet 在当前日期和时间中添加或减去的值。</span><span class="sxs-lookup"><span data-stu-id="2011c-134">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="2011c-135">可以在标准日期和时间格式中键入区域设置的调整，或使用 " **调整** " 参数将 **TimeSpan** 对象从传递 `New-TimeSpan` 到 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-135">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2011c-136">-Date</span><span class="sxs-lookup"><span data-stu-id="2011c-136">-Date</span></span>

<span data-ttu-id="2011c-137">将日期和时间更改为指定值。</span><span class="sxs-lookup"><span data-stu-id="2011c-137">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="2011c-138">你可以采用短日期格式键入新日期，并以你的区域设置的标准时间格式键入时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-138">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="2011c-139">或者，您可以从传递 **日期时间** 对象 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-139">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="2011c-140">如果指定日期，但不指定时间，则会将 `Set-Date` 时间更改为指定日期的午夜。</span><span class="sxs-lookup"><span data-stu-id="2011c-140">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="2011c-141">如果仅指定了时间，则不会更改日期。</span><span class="sxs-lookup"><span data-stu-id="2011c-141">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2011c-142">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="2011c-142">-DisplayHint</span></span>

<span data-ttu-id="2011c-143">指定显示日期和时间的哪些元素。此参数可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="2011c-143">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2011c-144">**日期** -仅显示日期。</span><span class="sxs-lookup"><span data-stu-id="2011c-144">**Date** - displays only the date.</span></span>
- <span data-ttu-id="2011c-145">**时间** -仅显示时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-145">**Time** - displays only the time.</span></span>
- <span data-ttu-id="2011c-146">**DateTime** -显示日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2011c-146">**DateTime** - displays the date and time.</span></span>

<span data-ttu-id="2011c-147">此参数仅影响显示内容。</span><span class="sxs-lookup"><span data-stu-id="2011c-147">This parameter affects only the display.</span></span>
<span data-ttu-id="2011c-148">它不会影响检索的 **DateTime** 对象 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-148">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

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

### <span data-ttu-id="2011c-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2011c-149">-Confirm</span></span>

<span data-ttu-id="2011c-150">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="2011c-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2011c-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2011c-151">-WhatIf</span></span>

<span data-ttu-id="2011c-152">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="2011c-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2011c-153">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="2011c-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2011c-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2011c-154">CommonParameters</span></span>

<span data-ttu-id="2011c-155">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2011c-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2011c-156">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2011c-156">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2011c-157">输入</span><span class="sxs-lookup"><span data-stu-id="2011c-157">INPUTS</span></span>

### <span data-ttu-id="2011c-158">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2011c-158">System.DateTime</span></span>

<span data-ttu-id="2011c-159">可以通过管道将日期传递给 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="2011c-159">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="2011c-160">输出</span><span class="sxs-lookup"><span data-stu-id="2011c-160">OUTPUTS</span></span>

### <span data-ttu-id="2011c-161">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2011c-161">System.DateTime</span></span>

<span data-ttu-id="2011c-162">`Set-Date` 返回一个对象，该对象表示其设置的日期。</span><span class="sxs-lookup"><span data-stu-id="2011c-162">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="2011c-163">注释</span><span class="sxs-lookup"><span data-stu-id="2011c-163">NOTES</span></span>

- <span data-ttu-id="2011c-164">更改计算机上的日期和时间时，请慎重使用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2011c-164">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="2011c-165">此更改可能会使计算机无法接收由日期或时间触发的系统范围内的事件和更新。</span><span class="sxs-lookup"><span data-stu-id="2011c-165">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="2011c-166">使用 **WhatIf** 和 **Confirm** 参数可避免出现错误。</span><span class="sxs-lookup"><span data-stu-id="2011c-166">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="2011c-167">可以将标准 .NET 方法用于与一起使用的 **DateTime** 和 **TimeSpan** 对象 `Set-Date` ，例如 **AddDays**、 **AddMonths** 和 **FromFileTime**。</span><span class="sxs-lookup"><span data-stu-id="2011c-167">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays**, **AddMonths**, and **FromFileTime**.</span></span> <span data-ttu-id="2011c-168">有关详细信息，请参阅 [DateTime 方法](/dotnet/api/system.datetime) 和</span><span class="sxs-lookup"><span data-stu-id="2011c-168">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="2011c-169">.NET SDK 中的[TimeSpan 方法](/dotnet/api/system.timespan)。</span><span class="sxs-lookup"><span data-stu-id="2011c-169">[TimeSpan Methods](/dotnet/api/system.timespan) in the .NET SDK.</span></span>

## <span data-ttu-id="2011c-170">相关链接</span><span class="sxs-lookup"><span data-stu-id="2011c-170">RELATED LINKS</span></span>

[<span data-ttu-id="2011c-171">获取日期</span><span class="sxs-lookup"><span data-stu-id="2011c-171">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="2011c-172">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="2011c-172">New-TimeSpan</span></span>](New-TimeSpan.md)
