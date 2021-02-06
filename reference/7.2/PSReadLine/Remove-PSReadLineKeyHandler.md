---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597663"
---
# <span data-ttu-id="5a6db-102">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5a6db-102">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="5a6db-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5a6db-103">SYNOPSIS</span></span>
<span data-ttu-id="5a6db-104">删除键绑定。</span><span class="sxs-lookup"><span data-stu-id="5a6db-104">Removes a key binding.</span></span>

## <span data-ttu-id="5a6db-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a6db-105">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="5a6db-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5a6db-106">DESCRIPTION</span></span>

<span data-ttu-id="5a6db-107">`Remove-PSReadLineKeyHandler`Cmdlet 将删除指定的键绑定。</span><span class="sxs-lookup"><span data-stu-id="5a6db-107">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="5a6db-108">示例</span><span class="sxs-lookup"><span data-stu-id="5a6db-108">EXAMPLES</span></span>

### <span data-ttu-id="5a6db-109">示例1：删除绑定</span><span class="sxs-lookup"><span data-stu-id="5a6db-109">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="5a6db-110">此命令从键组合或弦形中删除绑定 `Ctrl+B` 。</span><span class="sxs-lookup"><span data-stu-id="5a6db-110">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="5a6db-111">`Ctrl+B`在项目中创建了弦 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="5a6db-111">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="5a6db-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a6db-112">PARAMETERS</span></span>

### <span data-ttu-id="5a6db-113">-弦</span><span class="sxs-lookup"><span data-stu-id="5a6db-113">-Chord</span></span>

<span data-ttu-id="5a6db-114">指定要删除的键或键序列的数组。</span><span class="sxs-lookup"><span data-stu-id="5a6db-114">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="5a6db-115">单个绑定使用单个字符串指定。</span><span class="sxs-lookup"><span data-stu-id="5a6db-115">A single binding is specified by using a single string.</span></span> <span data-ttu-id="5a6db-116">如果绑定是键序列，请用逗号分隔键，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="5a6db-116">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="5a6db-117">此参数接受字符串数组。</span><span class="sxs-lookup"><span data-stu-id="5a6db-117">This parameter accepts an array of strings.</span></span> <span data-ttu-id="5a6db-118">每个字符串都是一个单独的绑定，而不是单个绑定的键序列。</span><span class="sxs-lookup"><span data-stu-id="5a6db-118">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6db-119">-ViMode</span><span class="sxs-lookup"><span data-stu-id="5a6db-119">-ViMode</span></span>

<span data-ttu-id="5a6db-120">指定绑定应用于哪种 vi 模式。</span><span class="sxs-lookup"><span data-stu-id="5a6db-120">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="5a6db-121">可能的值为： Insert、Command。</span><span class="sxs-lookup"><span data-stu-id="5a6db-121">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a6db-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a6db-122">CommonParameters</span></span>

<span data-ttu-id="5a6db-123">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5a6db-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a6db-124">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5a6db-124">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a6db-125">输入</span><span class="sxs-lookup"><span data-stu-id="5a6db-125">INPUTS</span></span>

### <span data-ttu-id="5a6db-126">无</span><span class="sxs-lookup"><span data-stu-id="5a6db-126">None</span></span>

<span data-ttu-id="5a6db-127">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a6db-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5a6db-128">输出</span><span class="sxs-lookup"><span data-stu-id="5a6db-128">OUTPUTS</span></span>

### <span data-ttu-id="5a6db-129">无</span><span class="sxs-lookup"><span data-stu-id="5a6db-129">None</span></span>

## <span data-ttu-id="5a6db-130">注释</span><span class="sxs-lookup"><span data-stu-id="5a6db-130">NOTES</span></span>

## <span data-ttu-id="5a6db-131">相关链接</span><span class="sxs-lookup"><span data-stu-id="5a6db-131">RELATED LINKS</span></span>

[<span data-ttu-id="5a6db-132">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5a6db-132">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="5a6db-133">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5a6db-133">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="5a6db-134">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5a6db-134">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="5a6db-135">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5a6db-135">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

