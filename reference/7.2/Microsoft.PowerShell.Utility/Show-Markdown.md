---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: d14e6332a2da5c86c4f8ada0d110c64e080437e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596229"
---
# <span data-ttu-id="a9deb-102">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="a9deb-102">Show-Markdown</span></span>

## <span data-ttu-id="a9deb-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a9deb-103">SYNOPSIS</span></span>
<span data-ttu-id="a9deb-104">使用 VT100 转义序列或使用 HTML 在浏览器中以友好方式显示控制台中的 Markdown 文件或字符串。</span><span class="sxs-lookup"><span data-stu-id="a9deb-104">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="a9deb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9deb-105">SYNTAX</span></span>

### <span data-ttu-id="a9deb-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="a9deb-106">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="a9deb-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="a9deb-107">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="a9deb-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a9deb-108">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="a9deb-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a9deb-109">DESCRIPTION</span></span>

<span data-ttu-id="a9deb-110">`Show-Markdown`Cmdlet 用于在终端或浏览器中以用户可读格式呈现 Markdown。</span><span class="sxs-lookup"><span data-stu-id="a9deb-110">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="a9deb-111">`Show-Markdown` 如果支持将 VT100 转义序列)  (，则可以返回一个字符串，其中包含终端呈现的 VT100 转义序列。</span><span class="sxs-lookup"><span data-stu-id="a9deb-111">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="a9deb-112">这主要用于查看终端中的 Markdown 文件。</span><span class="sxs-lookup"><span data-stu-id="a9deb-112">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="a9deb-113">还可以通过 `ConvertFrom-Markdown` 指定 **AsVT100EncodedString** 参数获取此字符串。</span><span class="sxs-lookup"><span data-stu-id="a9deb-113">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="a9deb-114">`Show-Markdown` 还可以打开浏览器并显示 Markdown 的呈现版本。</span><span class="sxs-lookup"><span data-stu-id="a9deb-114">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="a9deb-115">它通过将其转换为 HTML 并在默认浏览器中打开 HTML 文件来呈现 Markdown。</span><span class="sxs-lookup"><span data-stu-id="a9deb-115">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="a9deb-116">可以 `Show-Markdown` 通过使用更改在终端中呈现 Markdown 的方式 `Set-MarkdownOption` 。</span><span class="sxs-lookup"><span data-stu-id="a9deb-116">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="a9deb-117">此 cmdlet 是在 PowerShell 6.1 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a9deb-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="a9deb-118">示例</span><span class="sxs-lookup"><span data-stu-id="a9deb-118">EXAMPLES</span></span>

### <span data-ttu-id="a9deb-119">示例1：指定路径的简单示例</span><span class="sxs-lookup"><span data-stu-id="a9deb-119">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="a9deb-120">示例2：指定字符串的简单示例</span><span class="sxs-lookup"><span data-stu-id="a9deb-120">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="a9deb-121">示例2：在浏览器中打开 Markdown</span><span class="sxs-lookup"><span data-stu-id="a9deb-121">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="a9deb-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9deb-122">PARAMETERS</span></span>

### <span data-ttu-id="a9deb-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a9deb-123">-InputObject</span></span>

<span data-ttu-id="a9deb-124">将显示在终端中的 Markdown 字符串。</span><span class="sxs-lookup"><span data-stu-id="a9deb-124">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="a9deb-125">如果未传入受支持的格式， `Show-Markdown` 则将发出错误。</span><span class="sxs-lookup"><span data-stu-id="a9deb-125">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a9deb-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a9deb-126">-LiteralPath</span></span>

<span data-ttu-id="a9deb-127">指定 Markdown 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a9deb-127">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="a9deb-128">与 Path 参数不同，LiteralPath 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="a9deb-128">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="a9deb-129">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="a9deb-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a9deb-130">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="a9deb-130">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a9deb-131">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="a9deb-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9deb-132">-Path</span><span class="sxs-lookup"><span data-stu-id="a9deb-132">-Path</span></span>

<span data-ttu-id="a9deb-133">指定要呈现的 Markdown 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a9deb-133">Specifies the path to a Markdown file to be rendered.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a9deb-134">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="a9deb-134">-UseBrowser</span></span>

<span data-ttu-id="a9deb-135">将 Markdown 输入编译为 HTML，并在默认浏览器中打开它。</span><span class="sxs-lookup"><span data-stu-id="a9deb-135">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9deb-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9deb-136">CommonParameters</span></span>

<span data-ttu-id="a9deb-137">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a9deb-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9deb-138">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a9deb-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9deb-139">输入</span><span class="sxs-lookup"><span data-stu-id="a9deb-139">INPUTS</span></span>

### <span data-ttu-id="a9deb-140">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="a9deb-140">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="a9deb-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a9deb-141">System.String[]</span></span>

## <span data-ttu-id="a9deb-142">输出</span><span class="sxs-lookup"><span data-stu-id="a9deb-142">OUTPUTS</span></span>

### <span data-ttu-id="a9deb-143">System.String</span><span class="sxs-lookup"><span data-stu-id="a9deb-143">System.String</span></span>

## <span data-ttu-id="a9deb-144">注释</span><span class="sxs-lookup"><span data-stu-id="a9deb-144">NOTES</span></span>

## <span data-ttu-id="a9deb-145">相关链接</span><span class="sxs-lookup"><span data-stu-id="a9deb-145">RELATED LINKS</span></span>

[<span data-ttu-id="a9deb-146">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="a9deb-146">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

