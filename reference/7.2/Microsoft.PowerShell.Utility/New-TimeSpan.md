---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597877"
---
# <span data-ttu-id="a2f52-102">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="a2f52-102">New-TimeSpan</span></span>

## <span data-ttu-id="a2f52-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a2f52-103">SYNOPSIS</span></span>
<span data-ttu-id="a2f52-104">创建 TimeSpan 对象。</span><span class="sxs-lookup"><span data-stu-id="a2f52-104">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="a2f52-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a2f52-105">SYNTAX</span></span>

### <span data-ttu-id="a2f52-106">Date（默认值）</span><span class="sxs-lookup"><span data-stu-id="a2f52-106">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="a2f52-107">时间</span><span class="sxs-lookup"><span data-stu-id="a2f52-107">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="a2f52-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a2f52-108">DESCRIPTION</span></span>

<span data-ttu-id="a2f52-109">`New-TimeSpan`Cmdlet 可创建表示时间间隔的 **TimeSpan** 对象。</span><span class="sxs-lookup"><span data-stu-id="a2f52-109">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="a2f52-110">可以使用 **TimeSpan** 对象在 **DateTime** 对象中加减时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-110">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="a2f52-111">如果没有参数，则 `New-TimeSpan` 命令将返回表示时间间隔零的 **TimeSpan** 对象。</span><span class="sxs-lookup"><span data-stu-id="a2f52-111">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="a2f52-112">示例</span><span class="sxs-lookup"><span data-stu-id="a2f52-112">EXAMPLES</span></span>

### <span data-ttu-id="a2f52-113">示例 1：创建指定持续时间的 TimeSpan 对象</span><span class="sxs-lookup"><span data-stu-id="a2f52-113">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="a2f52-114">此命令将创建一个持续时间为1小时25分钟的 **TimeSpan** 对象，并将其存储在一个名为的变量中 `$TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="a2f52-114">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="a2f52-115">它将显示 **TimeSpan** 对象的表示形式。</span><span class="sxs-lookup"><span data-stu-id="a2f52-115">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="a2f52-116">示例 2：创建时间间隔的 TimeSpan 对象</span><span class="sxs-lookup"><span data-stu-id="a2f52-116">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="a2f52-117">此示例将创建一个新的 **TimeSpan** 对象，用于表示从运行该命令到 2010 年 1 月 1 日之间的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="a2f52-117">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="a2f52-118">此命令不需要 Start 参数，因为 Start 参数的默认值为当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-118">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="a2f52-119">示例 3：获取从当前日期起 90 天的日期</span><span class="sxs-lookup"><span data-stu-id="a2f52-119">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="a2f52-120">这些命令将返回当前日期之后的 90 天的日期。</span><span class="sxs-lookup"><span data-stu-id="a2f52-120">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="a2f52-121">示例 4：发现自更新文件以后的 TimeSpan</span><span class="sxs-lookup"><span data-stu-id="a2f52-121">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="a2f52-122">此命令告诉您自上次更新 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 帮助文件以来该文件的持续时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-122">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="a2f52-123">可以在任何文件或任何其他具有 **LastWriteTime** 属性的对象上使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="a2f52-123">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="a2f52-124">此命令有效，因为的 **Start** 参数的 `New-TimeSpan` 别名为 **LastWriteTime**。</span><span class="sxs-lookup"><span data-stu-id="a2f52-124">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="a2f52-125">当你通过管道将具有 **LastWriteTime** 属性的对象传递给时 `New-TimeSpan` ，PowerShell 会将 **LastWriteTime** 属性的值用作 **Start** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="a2f52-125">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="a2f52-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a2f52-126">PARAMETERS</span></span>

### <span data-ttu-id="a2f52-127">-Days</span><span class="sxs-lookup"><span data-stu-id="a2f52-127">-Days</span></span>

<span data-ttu-id="a2f52-128">指定时间跨度（以天为单位）。</span><span class="sxs-lookup"><span data-stu-id="a2f52-128">Specifies the days in the time span.</span></span>
<span data-ttu-id="a2f52-129">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="a2f52-129">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-130">-End</span><span class="sxs-lookup"><span data-stu-id="a2f52-130">-End</span></span>

<span data-ttu-id="a2f52-131">指定时间跨度的结束时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-131">Specifies the end of a time span.</span></span>
<span data-ttu-id="a2f52-132">默认值为当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-132">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-133">-Hours</span><span class="sxs-lookup"><span data-stu-id="a2f52-133">-Hours</span></span>

<span data-ttu-id="a2f52-134">指定时间跨度（以小时为单位）。</span><span class="sxs-lookup"><span data-stu-id="a2f52-134">Specifies the hours in the time span.</span></span>
<span data-ttu-id="a2f52-135">默认值为零。</span><span class="sxs-lookup"><span data-stu-id="a2f52-135">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-136">-Minutes</span><span class="sxs-lookup"><span data-stu-id="a2f52-136">-Minutes</span></span>

<span data-ttu-id="a2f52-137">指定时间跨度（以分钟为单位）。</span><span class="sxs-lookup"><span data-stu-id="a2f52-137">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="a2f52-138">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="a2f52-138">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-139">-Seconds</span><span class="sxs-lookup"><span data-stu-id="a2f52-139">-Seconds</span></span>

<span data-ttu-id="a2f52-140">指定时间跨度的长度（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="a2f52-140">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="a2f52-141">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="a2f52-141">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-142">-Start</span><span class="sxs-lookup"><span data-stu-id="a2f52-142">-Start</span></span>

<span data-ttu-id="a2f52-143">指定时间跨度的开始时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-143">Specifies the start of a time span.</span></span>
<span data-ttu-id="a2f52-144">输入一个表示日期和时间的字符串，例如 "3/15/09" 或日期 **时间** 对象，例如命令中的一个 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="a2f52-144">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="a2f52-145">默认值为当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a2f52-145">The default value is the current date and time.</span></span>

<span data-ttu-id="a2f52-146">你可以使用 **Start** 或其别名 **LastWriteTime**。</span><span class="sxs-lookup"><span data-stu-id="a2f52-146">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="a2f52-147">**LastWriteTime** 别名使你可以通过管道将具有 **LastWriteTime** 属性的对象（如文件系统中的文件 `[System.Io.FileIO]` ）传递给的 **启动** 参数 `New-TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="a2f52-147">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a2f52-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2f52-148">CommonParameters</span></span>

<span data-ttu-id="a2f52-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a2f52-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a2f52-150">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a2f52-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a2f52-151">输入</span><span class="sxs-lookup"><span data-stu-id="a2f52-151">INPUTS</span></span>

### <span data-ttu-id="a2f52-152">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="a2f52-152">System.DateTime</span></span>

<span data-ttu-id="a2f52-153">可以通过管道将表示开始时间的 **DateTime** 对象传递给 `New-TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="a2f52-153">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="a2f52-154">输出</span><span class="sxs-lookup"><span data-stu-id="a2f52-154">OUTPUTS</span></span>

### <span data-ttu-id="a2f52-155">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="a2f52-155">System.TimeSpan</span></span>

<span data-ttu-id="a2f52-156">`New-TimeSpan` 返回一个表示时间跨度的对象。</span><span class="sxs-lookup"><span data-stu-id="a2f52-156">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="a2f52-157">注释</span><span class="sxs-lookup"><span data-stu-id="a2f52-157">NOTES</span></span>

## <span data-ttu-id="a2f52-158">相关链接</span><span class="sxs-lookup"><span data-stu-id="a2f52-158">RELATED LINKS</span></span>

[<span data-ttu-id="a2f52-159">获取日期</span><span class="sxs-lookup"><span data-stu-id="a2f52-159">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="a2f52-160">Set-Date</span><span class="sxs-lookup"><span data-stu-id="a2f52-160">Set-Date</span></span>](Set-Date.md)

