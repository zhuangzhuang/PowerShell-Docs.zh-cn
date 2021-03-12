---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: 0da0c869216fd2a044fe03faad25e3de6f3fb8fd
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195688"
---
# <span data-ttu-id="6fc35-102">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="6fc35-102">Get-MarkdownOption</span></span>

## <span data-ttu-id="6fc35-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6fc35-103">SYNOPSIS</span></span>
<span data-ttu-id="6fc35-104">返回用于在控制台中呈现 Markdown 内容的当前颜色和样式。</span><span class="sxs-lookup"><span data-stu-id="6fc35-104">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="6fc35-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fc35-105">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="6fc35-106">说明</span><span class="sxs-lookup"><span data-stu-id="6fc35-106">DESCRIPTION</span></span>

<span data-ttu-id="6fc35-107">返回用于在控制台中呈现 Markdown 内容的当前颜色和样式。</span><span class="sxs-lookup"><span data-stu-id="6fc35-107">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="6fc35-108">此 cmdlet 的输出中显示的字符串包含用于更改呈现的 Markdown 文本的颜色和样式的 ANSI 转义码。</span><span class="sxs-lookup"><span data-stu-id="6fc35-108">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="6fc35-109">有关 Markdown 的详细信息，请参阅 [CommonMark](https://commonmark.org/) 网站。</span><span class="sxs-lookup"><span data-stu-id="6fc35-109">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="6fc35-110">示例</span><span class="sxs-lookup"><span data-stu-id="6fc35-110">EXAMPLES</span></span>

### <span data-ttu-id="6fc35-111">示例 1-获取当前颜色和样式</span><span class="sxs-lookup"><span data-stu-id="6fc35-111">Example 1 - Get the current colors and style</span></span>

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> <span data-ttu-id="6fc35-112">输出中显示的字符串值为 ANSI 转义序列 () 后面 **的字符** `[char]0x1B` 。</span><span class="sxs-lookup"><span data-stu-id="6fc35-112">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="6fc35-113">有关 ANSI 转义代码工作的详细信息，请参阅 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。</span><span class="sxs-lookup"><span data-stu-id="6fc35-113">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="6fc35-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fc35-114">PARAMETERS</span></span>

### <span data-ttu-id="6fc35-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fc35-115">CommonParameters</span></span>

<span data-ttu-id="6fc35-116">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6fc35-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fc35-117">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6fc35-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fc35-118">输入</span><span class="sxs-lookup"><span data-stu-id="6fc35-118">INPUTS</span></span>

### <span data-ttu-id="6fc35-119">无</span><span class="sxs-lookup"><span data-stu-id="6fc35-119">None</span></span>

## <span data-ttu-id="6fc35-120">输出</span><span class="sxs-lookup"><span data-stu-id="6fc35-120">OUTPUTS</span></span>

### <span data-ttu-id="6fc35-121">MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="6fc35-121">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="6fc35-122">注释</span><span class="sxs-lookup"><span data-stu-id="6fc35-122">NOTES</span></span>

## <span data-ttu-id="6fc35-123">相关链接</span><span class="sxs-lookup"><span data-stu-id="6fc35-123">RELATED LINKS</span></span>

[<span data-ttu-id="6fc35-124">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="6fc35-124">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="6fc35-125">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="6fc35-125">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="6fc35-126">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="6fc35-126">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="6fc35-127">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="6fc35-127">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="6fc35-128">CommonMark</span><span class="sxs-lookup"><span data-stu-id="6fc35-128">CommonMark</span></span>](https://commonmark.org/)

