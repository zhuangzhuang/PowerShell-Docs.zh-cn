---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597450"
---
# <span data-ttu-id="42ab8-102">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="42ab8-102">Get-TimeZone</span></span>

## <span data-ttu-id="42ab8-103">摘要</span><span class="sxs-lookup"><span data-stu-id="42ab8-103">SYNOPSIS</span></span>
<span data-ttu-id="42ab8-104">获取当前时区或可用时区的列表。</span><span class="sxs-lookup"><span data-stu-id="42ab8-104">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="42ab8-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42ab8-105">SYNTAX</span></span>

### <span data-ttu-id="42ab8-106">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="42ab8-106">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="42ab8-107">ID</span><span class="sxs-lookup"><span data-stu-id="42ab8-107">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="42ab8-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="42ab8-108">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="42ab8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="42ab8-109">DESCRIPTION</span></span>

<span data-ttu-id="42ab8-110">**获取时区** cmdlet 获取当前时区或可用时区的列表。</span><span class="sxs-lookup"><span data-stu-id="42ab8-110">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="42ab8-111">示例</span><span class="sxs-lookup"><span data-stu-id="42ab8-111">EXAMPLES</span></span>

### <span data-ttu-id="42ab8-112">示例1：获取当前时区</span><span class="sxs-lookup"><span data-stu-id="42ab8-112">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="42ab8-113">此命令获取当前时区。</span><span class="sxs-lookup"><span data-stu-id="42ab8-113">This command gets the current time zone.</span></span>

### <span data-ttu-id="42ab8-114">示例2：获取与指定的字符串匹配的时区</span><span class="sxs-lookup"><span data-stu-id="42ab8-114">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="42ab8-115">此命令将获取与指定的通配符匹配的所有时区。</span><span class="sxs-lookup"><span data-stu-id="42ab8-115">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="42ab8-116">示例3：获取所有可用时区</span><span class="sxs-lookup"><span data-stu-id="42ab8-116">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="42ab8-117">此命令将获取所有可用时区。</span><span class="sxs-lookup"><span data-stu-id="42ab8-117">This command gets all available time zones.</span></span>

## <span data-ttu-id="42ab8-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42ab8-118">PARAMETERS</span></span>

### <span data-ttu-id="42ab8-119">-Id</span><span class="sxs-lookup"><span data-stu-id="42ab8-119">-Id</span></span>

<span data-ttu-id="42ab8-120">指定为字符串数组，此 cmdlet 获取的时区的 ID 或 id。</span><span class="sxs-lookup"><span data-stu-id="42ab8-120">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="42ab8-121">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="42ab8-121">-ListAvailable</span></span>

<span data-ttu-id="42ab8-122">指示此 cmdlet 获取所有可用时区。</span><span class="sxs-lookup"><span data-stu-id="42ab8-122">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42ab8-123">-Name</span><span class="sxs-lookup"><span data-stu-id="42ab8-123">-Name</span></span>

<span data-ttu-id="42ab8-124">以字符串数组的形式指定此 cmdlet 获取的时区的名称。</span><span class="sxs-lookup"><span data-stu-id="42ab8-124">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="42ab8-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42ab8-125">CommonParameters</span></span>

<span data-ttu-id="42ab8-126">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="42ab8-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42ab8-127">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="42ab8-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42ab8-128">输入</span><span class="sxs-lookup"><span data-stu-id="42ab8-128">INPUTS</span></span>

### <span data-ttu-id="42ab8-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="42ab8-129">System.String[]</span></span>

## <span data-ttu-id="42ab8-130">输出</span><span class="sxs-lookup"><span data-stu-id="42ab8-130">OUTPUTS</span></span>

### <span data-ttu-id="42ab8-131">TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="42ab8-131">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="42ab8-132">注释</span><span class="sxs-lookup"><span data-stu-id="42ab8-132">NOTES</span></span>

<span data-ttu-id="42ab8-133">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="42ab8-133">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="42ab8-134">相关链接</span><span class="sxs-lookup"><span data-stu-id="42ab8-134">RELATED LINKS</span></span>

[<span data-ttu-id="42ab8-135">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="42ab8-135">Set-TimeZone</span></span>](Set-TimeZone.md)
