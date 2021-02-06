---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597050"
---
# <span data-ttu-id="34de3-102">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="34de3-102">Get-UICulture</span></span>

## <span data-ttu-id="34de3-103">摘要</span><span class="sxs-lookup"><span data-stu-id="34de3-103">SYNOPSIS</span></span>
<span data-ttu-id="34de3-104">获取操作系统中的当前 UI 区域性设置。</span><span class="sxs-lookup"><span data-stu-id="34de3-104">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="34de3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34de3-105">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="34de3-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="34de3-106">DESCRIPTION</span></span>

<span data-ttu-id="34de3-107">`Get-UICulture`Cmdlet 将获取有关 Windows (UI) 区域性设置的当前用户界面的信息。</span><span class="sxs-lookup"><span data-stu-id="34de3-107">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="34de3-108">UI 区域性确定哪些文本字符串用于用户界面元素，例如菜单和消息。</span><span class="sxs-lookup"><span data-stu-id="34de3-108">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="34de3-109">你还可以使用 `Get-Culture` cmdlet 来获取系统上的当前区域性。</span><span class="sxs-lookup"><span data-stu-id="34de3-109">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="34de3-110">区域性确定项的显示格式，例如数字、货币和日期。</span><span class="sxs-lookup"><span data-stu-id="34de3-110">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="34de3-111">示例</span><span class="sxs-lookup"><span data-stu-id="34de3-111">EXAMPLES</span></span>

### <span data-ttu-id="34de3-112">示例1：获取 UI 区域性</span><span class="sxs-lookup"><span data-stu-id="34de3-112">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="34de3-113">此命令获取当前 UI 区域性信息。</span><span class="sxs-lookup"><span data-stu-id="34de3-113">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="34de3-114">示例2：获取 UI 区域性并设置结果格式</span><span class="sxs-lookup"><span data-stu-id="34de3-114">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="34de3-115">此命令在列表中显示当前 UI 区域性的所有属性的值。</span><span class="sxs-lookup"><span data-stu-id="34de3-115">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="34de3-116">示例3：获取 Calendar 属性的值</span><span class="sxs-lookup"><span data-stu-id="34de3-116">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="34de3-117">此命令显示当前 UI 区域性的 **Calendar** 属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="34de3-117">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="34de3-118">Calendar 只是 UI 区域性的一个属性。</span><span class="sxs-lookup"><span data-stu-id="34de3-118">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="34de3-119">若要查看所有属性，请键入 `Get-UICulture | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="34de3-119">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="34de3-120">示例4：获取短日期模式</span><span class="sxs-lookup"><span data-stu-id="34de3-120">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="34de3-121">此命令显示当前 UI 区域性的短日期模式。</span><span class="sxs-lookup"><span data-stu-id="34de3-121">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="34de3-122">若要查看 UI 区域性的 **DateTimeFormat** 属性的所有子属性，请键入 `(Get-UICulture).DateTimeFormat | gm` 。</span><span class="sxs-lookup"><span data-stu-id="34de3-122">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="34de3-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34de3-123">PARAMETERS</span></span>

### <span data-ttu-id="34de3-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34de3-124">CommonParameters</span></span>

<span data-ttu-id="34de3-125">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="34de3-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34de3-126">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="34de3-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="34de3-127">输入</span><span class="sxs-lookup"><span data-stu-id="34de3-127">INPUTS</span></span>

### <span data-ttu-id="34de3-128">无</span><span class="sxs-lookup"><span data-stu-id="34de3-128">None</span></span>

<span data-ttu-id="34de3-129">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="34de3-129">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="34de3-130">输出</span><span class="sxs-lookup"><span data-stu-id="34de3-130">OUTPUTS</span></span>

### <span data-ttu-id="34de3-131">System.Globalization.CultureInfo、Microsoft.PowerShell.VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="34de3-131">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="34de3-132">`Get-UICulture` 返回表示当前 UI 区域性的对象。</span><span class="sxs-lookup"><span data-stu-id="34de3-132">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="34de3-133">在 Windows PowerShell 3.0 中，它返回 **CultureInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="34de3-133">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="34de3-134">在 Windows PowerShell 2.0 中，它返回 **VistaCultureInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="34de3-134">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="34de3-135">注释</span><span class="sxs-lookup"><span data-stu-id="34de3-135">NOTES</span></span>

- <span data-ttu-id="34de3-136">你还可以使用 `$PsCulture` 和 `$PsUICulture` 变量。</span><span class="sxs-lookup"><span data-stu-id="34de3-136">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="34de3-137">`$PsCulture`变量存储当前区域性的名称， `$PsUICulture` 变量存储当前 UI 区域性的名称。</span><span class="sxs-lookup"><span data-stu-id="34de3-137">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="34de3-138">相关链接</span><span class="sxs-lookup"><span data-stu-id="34de3-138">RELATED LINKS</span></span>

