---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: df4091609f403a58749a6821044d768089cdc03c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194574"
---
# <span data-ttu-id="b12a2-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="b12a2-102">Get-Uptime</span></span>

## <span data-ttu-id="b12a2-103">摘要</span><span class="sxs-lookup"><span data-stu-id="b12a2-103">SYNOPSIS</span></span>
<span data-ttu-id="b12a2-104">获取自上次启动以来的时间 **跨度** 。</span><span class="sxs-lookup"><span data-stu-id="b12a2-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="b12a2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b12a2-105">SYNTAX</span></span>

### <span data-ttu-id="b12a2-106">Timespan (默认值) </span><span class="sxs-lookup"><span data-stu-id="b12a2-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="b12a2-107">因此</span><span class="sxs-lookup"><span data-stu-id="b12a2-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="b12a2-108">说明</span><span class="sxs-lookup"><span data-stu-id="b12a2-108">DESCRIPTION</span></span>

<span data-ttu-id="b12a2-109">此 cmdlet 将返回自上次启动操作系统后所经过的时间。</span><span class="sxs-lookup"><span data-stu-id="b12a2-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="b12a2-110">`Get-Uptime`Cmdlet 是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="b12a2-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="b12a2-111">示例</span><span class="sxs-lookup"><span data-stu-id="b12a2-111">EXAMPLES</span></span>

### <span data-ttu-id="b12a2-112">示例 1-显示自上次启动以来的时间</span><span class="sxs-lookup"><span data-stu-id="b12a2-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="b12a2-113">示例 2-显示上次启动的时间</span><span class="sxs-lookup"><span data-stu-id="b12a2-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="b12a2-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b12a2-114">PARAMETERS</span></span>

### <span data-ttu-id="b12a2-115">-自</span><span class="sxs-lookup"><span data-stu-id="b12a2-115">-Since</span></span>

<span data-ttu-id="b12a2-116">导致 cmdlet 返回表示操作系统上次启动时间的 **DateTime** 对象。</span><span class="sxs-lookup"><span data-stu-id="b12a2-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b12a2-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b12a2-117">CommonParameters</span></span>

<span data-ttu-id="b12a2-118">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b12a2-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b12a2-119">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b12a2-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b12a2-120">输入</span><span class="sxs-lookup"><span data-stu-id="b12a2-120">INPUTS</span></span>

### <span data-ttu-id="b12a2-121">无</span><span class="sxs-lookup"><span data-stu-id="b12a2-121">None</span></span>

## <span data-ttu-id="b12a2-122">输出</span><span class="sxs-lookup"><span data-stu-id="b12a2-122">OUTPUTS</span></span>

### <span data-ttu-id="b12a2-123">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b12a2-123">System.TimeSpan</span></span>

<span data-ttu-id="b12a2-124">这是未使用任何参数时的默认返回类型。</span><span class="sxs-lookup"><span data-stu-id="b12a2-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="b12a2-125">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="b12a2-125">System.DateTime</span></span>

<span data-ttu-id="b12a2-126">使用 **自** 参数时返回此类型。</span><span class="sxs-lookup"><span data-stu-id="b12a2-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="b12a2-127">如果启用了 Windows 快速启动，则 Windows 不会更新存储在 **LastBootUpTime** 中的值。</span><span class="sxs-lookup"><span data-stu-id="b12a2-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime**.</span></span> <span data-ttu-id="b12a2-128">若要禁用快速启动，请运行以下命令： `Powercfg -h off` 。</span><span class="sxs-lookup"><span data-stu-id="b12a2-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="b12a2-129">有关 Windows 快速启动的详细信息，请参阅将 [快速启动从休眠状态中唤醒](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)。</span><span class="sxs-lookup"><span data-stu-id="b12a2-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="b12a2-130">注释</span><span class="sxs-lookup"><span data-stu-id="b12a2-130">NOTES</span></span>

<span data-ttu-id="b12a2-131">在 Windows 上，返回的值与 WMI 中 **Win32_OperatingSystem** 类的 **LastBootUpTime** 属性相同。</span><span class="sxs-lookup"><span data-stu-id="b12a2-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="b12a2-132">相关链接</span><span class="sxs-lookup"><span data-stu-id="b12a2-132">RELATED LINKS</span></span>

[<span data-ttu-id="b12a2-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="b12a2-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
