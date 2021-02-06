---
title: PowerShell-Docs 风格指南
description: 本文介绍用于撰写 PowerShell 文档的风格规则。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99596816"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="ab43d-103">PowerShell-Docs 风格指南</span><span class="sxs-lookup"><span data-stu-id="ab43d-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="ab43d-104">本文介绍特定于 PowerShell-Docs 内容的风格指南。</span><span class="sxs-lookup"><span data-stu-id="ab43d-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="ab43d-105">它以 [概述](overview.md#get-started-writing-docs)中概述的信息为基础。</span><span class="sxs-lookup"><span data-stu-id="ab43d-105">It builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="ab43d-106">产品术语</span><span class="sxs-lookup"><span data-stu-id="ab43d-106">Product Terminology</span></span>

<span data-ttu-id="ab43d-107">PowerShell 有多个变体。</span><span class="sxs-lookup"><span data-stu-id="ab43d-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="ab43d-108">**PowerShell** - 这是默认名称。</span><span class="sxs-lookup"><span data-stu-id="ab43d-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="ab43d-109">我们将 PowerShell 7 和更高版本视为真实的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ab43d-109">We consider PowerShell 7 and beyond to be the one, true PowerShell.</span></span>
- <span data-ttu-id="ab43d-110">**PowerShell Core** - 基于 .NET Core 生成的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ab43d-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="ab43d-111">术语 " **核心** " 的使用应限制为需要在 Windows PowerShell 中区分它的情况。</span><span class="sxs-lookup"><span data-stu-id="ab43d-111">Usage of the term **Core** should be limited to cases where it's necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="ab43d-112">**Windows PowerShell** - 基于 .NET Framework 生成的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ab43d-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="ab43d-113">Windows PowerShell 仅对 Windows 提供，并且需要完整的 Framework。</span><span class="sxs-lookup"><span data-stu-id="ab43d-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="ab43d-114">通常，可以将文档中的 "Windows PowerShell" 的引用更改为 _PowerShell_。</span><span class="sxs-lookup"><span data-stu-id="ab43d-114">In general, references to "Windows PowerShell" in documentation can be changed to _PowerShell_.</span></span>
  <span data-ttu-id="ab43d-115">讨论特定于 _Windows powershell_ 的行为时应使用 "windows powershell"。</span><span class="sxs-lookup"><span data-stu-id="ab43d-115">"Windows PowerShell" should be used when _Windows PowerShell_-specific behavior is being discussed.</span></span>

<span data-ttu-id="ab43d-116">相关产品</span><span class="sxs-lookup"><span data-stu-id="ab43d-116">Related products</span></span>

- <span data-ttu-id="ab43d-117">**) Visual Studio Code (VS Code** -这是 Microsoft 的免费开源编辑器。</span><span class="sxs-lookup"><span data-stu-id="ab43d-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open-source editor.</span></span> <span data-ttu-id="ab43d-118">首次提及时，应使用完整名称。</span><span class="sxs-lookup"><span data-stu-id="ab43d-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="ab43d-119">之后，可以使用 VS Code  。</span><span class="sxs-lookup"><span data-stu-id="ab43d-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="ab43d-120">不要使用 "VSCode"。</span><span class="sxs-lookup"><span data-stu-id="ab43d-120">Don't use "VSCode".</span></span>
- <span data-ttu-id="ab43d-121">适用于 Visual Studio Code 的 PowerShell 扩展  - 此扩展会将 VS Code 转换为适用于 PowerShell 的首选 IDE。</span><span class="sxs-lookup"><span data-stu-id="ab43d-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="ab43d-122">首次提及时，应使用完整名称。</span><span class="sxs-lookup"><span data-stu-id="ab43d-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="ab43d-123">之后，可以使用 PowerShell 扩展  。</span><span class="sxs-lookup"><span data-stu-id="ab43d-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="ab43d-124">Azure PowerShell  - 这是用于管理 Azure 服务的 PowerShell 模块的集合。</span><span class="sxs-lookup"><span data-stu-id="ab43d-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="ab43d-125">Azure Stack PowerShell  - 这是用于管理 Microsoft 混合云解决方案的 PowerShell 模块的集合。</span><span class="sxs-lookup"><span data-stu-id="ab43d-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="ab43d-126">Markdown 详情</span><span class="sxs-lookup"><span data-stu-id="ab43d-126">Markdown specifics</span></span>

<span data-ttu-id="ab43d-127">用于生成文档的 Microsoft 开放发布系统 (OPS) 使用 [markdig][] 处理 Markdown 文档。</span><span class="sxs-lookup"><span data-stu-id="ab43d-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="ab43d-128">Markdig 根据最新 [CommonMark][] 规范的规则分析文档。</span><span class="sxs-lookup"><span data-stu-id="ab43d-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="ab43d-129">新的 CommonMark 规范比某些 Markdown 元素的构造要严格得多。</span><span class="sxs-lookup"><span data-stu-id="ab43d-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="ab43d-130">请密切关注本文档中提供的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ab43d-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="ab43d-131">空白行、空格和制表符</span><span class="sxs-lookup"><span data-stu-id="ab43d-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="ab43d-132">在 Markdown 中，空白行还表示块的末尾。</span><span class="sxs-lookup"><span data-stu-id="ab43d-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="ab43d-133">在不同类型的 Markdown 块之间（例如，在段落和列表或标题之间）应该有一个空白行。</span><span class="sxs-lookup"><span data-stu-id="ab43d-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="ab43d-134">在 HTML 中，多个连续的空行呈现为一个空白行。</span><span class="sxs-lookup"><span data-stu-id="ab43d-134">Multiple consecutive blank lines render as a single blank line in HTML.</span></span> <span data-ttu-id="ab43d-135">它们不起作用。</span><span class="sxs-lookup"><span data-stu-id="ab43d-135">They serve no purpose.</span></span>
<span data-ttu-id="ab43d-136">在代码块中，连续的空行中断代码块。</span><span class="sxs-lookup"><span data-stu-id="ab43d-136">Within a code block, consecutive blank lines break the code block.</span></span>

<span data-ttu-id="ab43d-137">删除行尾的多余空格。</span><span class="sxs-lookup"><span data-stu-id="ab43d-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="ab43d-138">间距在 Markdown 中非常重要。</span><span class="sxs-lookup"><span data-stu-id="ab43d-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="ab43d-139">始终使用空格而不是硬制表符。</span><span class="sxs-lookup"><span data-stu-id="ab43d-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="ab43d-140">尾随空格可更改 Markdown 的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="ab43d-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="ab43d-141">标题</span><span class="sxs-lookup"><span data-stu-id="ab43d-141">Titles and headings</span></span>

<span data-ttu-id="ab43d-142">只使用 [ATX 标题][atx]（# 样式，不用 `=` 或 `-` 样式标题）。</span><span class="sxs-lookup"><span data-stu-id="ab43d-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="ab43d-143">使用句首大写形式 - 只对专有名词和标题的首个字母使用大写形式</span><span class="sxs-lookup"><span data-stu-id="ab43d-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="ab43d-144">`#` 与标题的首个字母之间必须有一个空格</span><span class="sxs-lookup"><span data-stu-id="ab43d-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="ab43d-145">标题前后应该都留有一个空白行</span><span class="sxs-lookup"><span data-stu-id="ab43d-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="ab43d-146">每个文档只有 1 个 H1</span><span class="sxs-lookup"><span data-stu-id="ab43d-146">Only one H1 per document</span></span>
- <span data-ttu-id="ab43d-147">标题级别应按 1 递增。</span><span class="sxs-lookup"><span data-stu-id="ab43d-147">Header levels should increment by one.</span></span> <span data-ttu-id="ab43d-148">不跳过级别</span><span class="sxs-lookup"><span data-stu-id="ab43d-148">Don't skip levels</span></span>
- <span data-ttu-id="ab43d-149">请勿在标头中使用粗体或其他标记</span><span class="sxs-lookup"><span data-stu-id="ab43d-149">Don't use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="ab43d-150">将行长度限制为 100 个字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="ab43d-151">这适用于概念性文章和 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="ab43d-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="ab43d-152">限制行长度可以改进 git diff 和历史记录的可读性。</span><span class="sxs-lookup"><span data-stu-id="ab43d-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="ab43d-153">同时也便于其他作者参与撰写文档。</span><span class="sxs-lookup"><span data-stu-id="ab43d-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="ab43d-154">在 Visual Studio Code 中使用 [Reflow Markdown][reflow] 扩展可以轻松地重排段落以适应指定的行长度。</span><span class="sxs-lookup"><span data-stu-id="ab43d-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="ab43d-155">About_topics 限制为 80 个字符。</span><span class="sxs-lookup"><span data-stu-id="ab43d-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="ab43d-156">有关更具体的信息，请参阅 [格式 About_ 文件](#formatting-about_-files)。</span><span class="sxs-lookup"><span data-stu-id="ab43d-156">For more specific information, see [Formatting About_ files](#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="ab43d-157">列表</span><span class="sxs-lookup"><span data-stu-id="ab43d-157">Lists</span></span>

<span data-ttu-id="ab43d-158">如果列表包含多个句子或段落，请考虑使用子层标题而不是列表。</span><span class="sxs-lookup"><span data-stu-id="ab43d-158">If your list contains multiple sentences or paragraphs, consider using a sublevel header rather than a list.</span></span>

<span data-ttu-id="ab43d-159">列表前后应该都留有一个空白行。</span><span class="sxs-lookup"><span data-stu-id="ab43d-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="ab43d-160">未排序列表</span><span class="sxs-lookup"><span data-stu-id="ab43d-160">Unordered lists</span></span>

<span data-ttu-id="ab43d-161">不要以句点结尾列出项，除非它们包含多个句子。</span><span class="sxs-lookup"><span data-stu-id="ab43d-161">Don't end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="ab43d-162">对于列表项项目符号，使用连字符 (`-`)。</span><span class="sxs-lookup"><span data-stu-id="ab43d-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="ab43d-163">这样可以避免与使用星号 [`*`] 的粗体或斜体标记混淆。</span><span class="sxs-lookup"><span data-stu-id="ab43d-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="ab43d-164">若要在项目符号项下添加段落或其他元素，请插入一个换行符，并使缩进与项目符号后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="ab43d-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="ab43d-165">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-165">For example:</span></span>

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="ab43d-166">这是一个列表，其中包含项目符号项下的子元素。</span><span class="sxs-lookup"><span data-stu-id="ab43d-166">This is a list that contains child elements under a bullet item.</span></span>

- <span data-ttu-id="ab43d-167">第一个项目符号项</span><span class="sxs-lookup"><span data-stu-id="ab43d-167">First bullet item</span></span>

  <span data-ttu-id="ab43d-168">说明第一个项目符号的句子。</span><span class="sxs-lookup"><span data-stu-id="ab43d-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="ab43d-169">子项目符号项</span><span class="sxs-lookup"><span data-stu-id="ab43d-169">Child bullet item</span></span>

    <span data-ttu-id="ab43d-170">解释子项目符号的句子。</span><span class="sxs-lookup"><span data-stu-id="ab43d-170">Sentence explaining the child bullet.</span></span>

- <span data-ttu-id="ab43d-171">第二个项目符号项</span><span class="sxs-lookup"><span data-stu-id="ab43d-171">Second bullet item</span></span>
- <span data-ttu-id="ab43d-172">第三个项目符号项</span><span class="sxs-lookup"><span data-stu-id="ab43d-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="ab43d-173">已排序列表</span><span class="sxs-lookup"><span data-stu-id="ab43d-173">Ordered lists</span></span>

<span data-ttu-id="ab43d-174">若要在带编号的项下添加段落或其他元素，请使缩进与项编号后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="ab43d-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="ab43d-175">编号列表中的所有项均应使用数字 `1.`，而不是递增每个项的编号数字值。</span><span class="sxs-lookup"><span data-stu-id="ab43d-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="ab43d-176">Markdown 呈现会自动递增该值。</span><span class="sxs-lookup"><span data-stu-id="ab43d-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="ab43d-177">这使重新排序项目变得更加容易，并使下级内容的缩进标准化。</span><span class="sxs-lookup"><span data-stu-id="ab43d-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="ab43d-178">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="ab43d-179">最终呈现的 Markdown 如下：</span><span class="sxs-lookup"><span data-stu-id="ab43d-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="ab43d-180">对于第一个元素，在 1 之后插入一个空格。</span><span class="sxs-lookup"><span data-stu-id="ab43d-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="ab43d-181">长句应换行到下一行，并且必须与编号列表标记后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="ab43d-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="ab43d-182">若要包括第二个元素（如本例所示），请在第一个元素后插入一个换行符，并对齐缩进。</span><span class="sxs-lookup"><span data-stu-id="ab43d-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="ab43d-183">第二个元素的缩进必须与编号列表标记后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="ab43d-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="ab43d-184">对于这样的一位数的项，缩进到第 4 列。</span><span class="sxs-lookup"><span data-stu-id="ab43d-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="ab43d-185">对于两位数的项（例如项编号 10），缩进到第 5 列。</span><span class="sxs-lookup"><span data-stu-id="ab43d-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="ab43d-186">下一个带编号的项从此处开始。</span><span class="sxs-lookup"><span data-stu-id="ab43d-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="ab43d-187">映像</span><span class="sxs-lookup"><span data-stu-id="ab43d-187">Images</span></span>

<span data-ttu-id="ab43d-188">用于添加图像的语法如下：</span><span class="sxs-lookup"><span data-stu-id="ab43d-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="ab43d-189">其中 `alt text` 是图像的简要说明，`<folder path>` 是图像的相对路径。</span><span class="sxs-lookup"><span data-stu-id="ab43d-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="ab43d-190">必须为视觉障碍人士的屏幕阅读器使用替代文本。</span><span class="sxs-lookup"><span data-stu-id="ab43d-190">Alternate text is required for screen readers for the visually impaired.</span></span>

<span data-ttu-id="ab43d-191">图像应存储在 `media/<article-name>` 包含项目的文件夹中的文件夹内。</span><span class="sxs-lookup"><span data-stu-id="ab43d-191">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="ab43d-192">不要在项目之间共享图像。</span><span class="sxs-lookup"><span data-stu-id="ab43d-192">Don't share images between articles.</span></span> <span data-ttu-id="ab43d-193">在 `media` 文件夹下创建与文章的文件名相匹配的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ab43d-193">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="ab43d-194">将该文章的图像复制到该新文件夹。</span><span class="sxs-lookup"><span data-stu-id="ab43d-194">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="ab43d-195">如果多个文章使用一个图像，则每个图像文件夹都必须具有该图像文件的副本。</span><span class="sxs-lookup"><span data-stu-id="ab43d-195">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="ab43d-196">这种做法可防止更改一篇文章的图像影响到另一篇文章。</span><span class="sxs-lookup"><span data-stu-id="ab43d-196">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="ab43d-197">支持下列图像文件类型： `*.png` 、 `*.gif` 、 `*.jpeg` 、 `*.jpg` 、 `*.svg`</span><span class="sxs-lookup"><span data-stu-id="ab43d-197">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="ab43d-198">公开发布支持 Markdown 扩展</span><span class="sxs-lookup"><span data-stu-id="ab43d-198">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="ab43d-199">[Microsoft Docs 创作包](/contribute/how-to-write-docs-auth-pack)包含的工具支持发布系统独有的功能。</span><span class="sxs-lookup"><span data-stu-id="ab43d-199">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="ab43d-200">警报是一种 Markdown 扩展，用于创建在 docs.microsoft.com 上呈现的 blockquotes，颜色和图标突出显示内容的重要性。</span><span class="sxs-lookup"><span data-stu-id="ab43d-200">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="ab43d-201">支持以下警报类型：</span><span class="sxs-lookup"><span data-stu-id="ab43d-201">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="ab43d-202">这些警报在 docs.microsoft.com 上如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab43d-202">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="ab43d-203">备注块</span><span class="sxs-lookup"><span data-stu-id="ab43d-203">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="ab43d-204">Information the user should notice even if skimming.</span><span class="sxs-lookup"><span data-stu-id="ab43d-204">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="ab43d-205">Tip 块</span><span class="sxs-lookup"><span data-stu-id="ab43d-205">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="ab43d-206">Optional information to help a user be more successful.</span><span class="sxs-lookup"><span data-stu-id="ab43d-206">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="ab43d-207">重要块</span><span class="sxs-lookup"><span data-stu-id="ab43d-207">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab43d-208">Essential information required for user success.</span><span class="sxs-lookup"><span data-stu-id="ab43d-208">Essential information required for user success.</span></span>

<span data-ttu-id="ab43d-209">警告块</span><span class="sxs-lookup"><span data-stu-id="ab43d-209">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="ab43d-210">Negative potential consequences of an action.</span><span class="sxs-lookup"><span data-stu-id="ab43d-210">Negative potential consequences of an action.</span></span>

<span data-ttu-id="ab43d-211">警告块</span><span class="sxs-lookup"><span data-stu-id="ab43d-211">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="ab43d-212">操作必然造成的危险后果。</span><span class="sxs-lookup"><span data-stu-id="ab43d-212">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="ab43d-213">超链接</span><span class="sxs-lookup"><span data-stu-id="ab43d-213">Hyperlinks</span></span>

- <span data-ttu-id="ab43d-214">超链接必须使用 Markdown 语法 `[friendlyname](url-or-path)` 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-214">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`.</span></span> <span data-ttu-id="ab43d-215">支持[链接引用][linkref]。</span><span class="sxs-lookup"><span data-stu-id="ab43d-215">[Link references][linkref] are supported.</span></span>
- <span data-ttu-id="ab43d-216">发布系统支持三种类型的链接：</span><span class="sxs-lookup"><span data-stu-id="ab43d-216">The publishing system supports three types of links:</span></span>
  - <span data-ttu-id="ab43d-217">URL 链接</span><span class="sxs-lookup"><span data-stu-id="ab43d-217">URL links</span></span>
  - <span data-ttu-id="ab43d-218">文件链接</span><span class="sxs-lookup"><span data-stu-id="ab43d-218">File links</span></span>
  - <span data-ttu-id="ab43d-219">交叉引用链接</span><span class="sxs-lookup"><span data-stu-id="ab43d-219">Cross-reference links</span></span>
- <span data-ttu-id="ab43d-220">指向 docs.microsoft.com 上的其他文章的链接必须是站点相对路径</span><span class="sxs-lookup"><span data-stu-id="ab43d-220">Links to other articles on docs.microsoft.com must be site-relative paths</span></span>
- <span data-ttu-id="ab43d-221">除非对于目标站点无效，否则外部网站的所有 Url 都应使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ab43d-221">All URLs to external websites should use HTTPS unless that isn't valid for the target site.</span></span>
- <span data-ttu-id="ab43d-222">链接必须具有友好名称，通常为链接项目的标题</span><span class="sxs-lookup"><span data-stu-id="ab43d-222">Links must have a friendly name, usually the title of the linked article</span></span>
- <span data-ttu-id="ab43d-223">底部的 " _相关链接_ " 部分中的所有项都应为超链接</span><span class="sxs-lookup"><span data-stu-id="ab43d-223">All items in the _Related links_ section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="ab43d-224">请勿在超链接的方括号内使用反撇号、粗体或其他标记。</span><span class="sxs-lookup"><span data-stu-id="ab43d-224">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="ab43d-225">当你记录特定的 URI 时，可以使用 Bare Url。</span><span class="sxs-lookup"><span data-stu-id="ab43d-225">Bare URLs may be used when you're documenting a specific URI.</span></span> <span data-ttu-id="ab43d-226">此 URI 必须包含在反撇号中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-226">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="ab43d-227">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-227">For example:</span></span>

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a><span data-ttu-id="ab43d-228">链接到 docs.microsoft.com 上的其他内容</span><span class="sxs-lookup"><span data-stu-id="ab43d-228">Linking to other content on docs.microsoft.com</span></span>

- <span data-ttu-id="ab43d-229">指向 docs.microsoft.com 上的其他文章的 **URL 链接** 必须是站点相对路径。</span><span class="sxs-lookup"><span data-stu-id="ab43d-229">**URL links** to other articles on docs.microsoft.com must be site-relative paths.</span></span> <span data-ttu-id="ab43d-230">创建相对链接的最简单方法是从浏览器复制 URL，然后 `https://docs.microsoft.com/en-us` 从粘贴到 markdown 中的值中删除。</span><span class="sxs-lookup"><span data-stu-id="ab43d-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span> <span data-ttu-id="ab43d-231">请勿在 Microsoft 属性的 Url 中包含区域设置 (`/en-us` 从 URL) 中删除。</span><span class="sxs-lookup"><span data-stu-id="ab43d-231">Don't include locales in URLs on Microsoft properties (remove `/en-us` from URL).</span></span> <span data-ttu-id="ab43d-232">从 URL 中删除任何不必要的查询参数。</span><span class="sxs-lookup"><span data-stu-id="ab43d-232">Remove any unnecessary query parameters from the URL.</span></span> <span data-ttu-id="ab43d-233">应删除的示例：</span><span class="sxs-lookup"><span data-stu-id="ab43d-233">Examples that should be removed:</span></span>

  - <span data-ttu-id="ab43d-234">`?view=powershell-5.1` -用于链接到特定版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab43d-234">`?view=powershell-5.1` - used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="ab43d-235">`?redirectedfrom=MSDN` -从旧文章重定向到新位置时添加到 URL</span><span class="sxs-lookup"><span data-stu-id="ab43d-235">`?redirectedfrom=MSDN` - added to the URL when you get redirected from an old article to its new location</span></span>

  <span data-ttu-id="ab43d-236">如果需要链接到文档的特定版本，则需要将 `&preserve_view=true` 参数添加到查询字符串。</span><span class="sxs-lookup"><span data-stu-id="ab43d-236">If you need to link to a specific version of a document, then you need to add the `&preserve_view=true` parameter to the query string.</span></span> <span data-ttu-id="ab43d-237">例如： `?view=powershell-5.1&preserve_view=true`</span><span class="sxs-lookup"><span data-stu-id="ab43d-237">For example: `?view=powershell-5.1&preserve_view=true`</span></span>

- <span data-ttu-id="ab43d-238">**文件链接** 用于从一个引用文章链接到另一个引用文章，或从一个概念文章链接到另一个。</span><span class="sxs-lookup"><span data-stu-id="ab43d-238">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="ab43d-239">如果需要链接到特定版本的 PowerShell 的参考文章，则必须使用 URL 链接。</span><span class="sxs-lookup"><span data-stu-id="ab43d-239">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

  - <span data-ttu-id="ab43d-240">文件链接包含相对文件路径 (例如： `../folder/file.md`) </span><span class="sxs-lookup"><span data-stu-id="ab43d-240">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
  - <span data-ttu-id="ab43d-241">所有文件路径使用正斜杠 (`/`) 字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-241">All file paths use forward-slash (`/`) characters</span></span>

- <span data-ttu-id="ab43d-242">**交叉引用链接** 是发布系统支持的一项特殊功能。</span><span class="sxs-lookup"><span data-stu-id="ab43d-242">**Cross-reference links** are a special feature supported by the publishing system.</span></span> <span data-ttu-id="ab43d-243">您可以使用概念文章中的交叉引用链接链接到 .NET API 或 cmdlet 引用。</span><span class="sxs-lookup"><span data-stu-id="ab43d-243">You can use cross-reference links in conceptual articles to link to .NET API or cmdlet reference.</span></span>

  <span data-ttu-id="ab43d-244">有关 .NET API 参考的链接，请参阅中心参与者指南中的 [使用文档](/contribute/how-to-write-links#xref-cross-reference-links) 中的链接。</span><span class="sxs-lookup"><span data-stu-id="ab43d-244">For links to .NET API reference, see [Use links in documentation](/contribute/how-to-write-links#xref-cross-reference-links) in the central Contributor Guide.</span></span>

  <span data-ttu-id="ab43d-245">指向 cmdlet 引用的链接具有以下格式： `xref:<module-name>.<cmdlet-name>` 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-245">Links to cmdlet reference have the following format: `xref:<module-name>.<cmdlet-name>`.</span></span> <span data-ttu-id="ab43d-246">例如，若要链接到位于 `Get-Content` **Microsoft 的 PowerShell** 模块中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab43d-246">For example, to link to the `Get-Content` cmdlet in the **Microsoft.PowerShell.Management** module.</span></span>

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

<span data-ttu-id="ab43d-247">URL 和文件链接上都允许深层链接。</span><span class="sxs-lookup"><span data-stu-id="ab43d-247">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="ab43d-248">将定位点添加到目标路径的末尾。</span><span class="sxs-lookup"><span data-stu-id="ab43d-248">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="ab43d-249">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-249">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="ab43d-250">有关详细信息，请参阅 [使用文档中的链接](/contribute/how-to-write-links)。</span><span class="sxs-lookup"><span data-stu-id="ab43d-250">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="ab43d-251">设置命令语法元素的格式</span><span class="sxs-lookup"><span data-stu-id="ab43d-251">Formatting command syntax elements</span></span>

- <span data-ttu-id="ab43d-252">始终将全名用于 cmdlet 和参数。</span><span class="sxs-lookup"><span data-stu-id="ab43d-252">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="ab43d-253">除非您专门演示别名，否则请避免使用别名。</span><span class="sxs-lookup"><span data-stu-id="ab43d-253">Avoid using aliases unless you're specifically demonstrating the alias.</span></span>

- <span data-ttu-id="ab43d-254">属性、参数、对象、类型名称、类名称和类方法应为 **粗体**。</span><span class="sxs-lookup"><span data-stu-id="ab43d-254">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="ab43d-255">应将属性和参数值包装在反撇号 (`` ` ``) 中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-255">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="ab43d-256">使用括号式样式引用类型时，请使用反撇号。</span><span class="sxs-lookup"><span data-stu-id="ab43d-256">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="ab43d-257">例如： `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="ab43d-257">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="ab43d-258">语言关键字、cmdlet 名称、函数、变量、本机 Exe、文件路径和内联语法示例应包装在反撇号中 (`` ` ``) 字符。</span><span class="sxs-lookup"><span data-stu-id="ab43d-258">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="ab43d-259">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-259">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="ab43d-260">按名称引用参数时，该名称应采用粗体。</span><span class="sxs-lookup"><span data-stu-id="ab43d-260">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="ab43d-261">演示使用带有连字符前缀的参数时，应使用反引号将参数引起来。</span><span class="sxs-lookup"><span data-stu-id="ab43d-261">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="ab43d-262">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-262">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="ab43d-263">演示外部命令的示例用法时，示例应由反引号引起来。</span><span class="sxs-lookup"><span data-stu-id="ab43d-263">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="ab43d-264">始终在本机命令中包含文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="ab43d-264">Always include the file extension in the native command.</span></span> <span data-ttu-id="ab43d-265">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-265">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="ab43d-266">包括文件扩展名可确保根据 PowerShell 的命令优先级执行正确的命令。</span><span class="sxs-lookup"><span data-stu-id="ab43d-266">Including the file extension ensures that the correct command is executed according to PowerShell's command precedence.</span></span>

- <span data-ttu-id="ab43d-267">编写概念性文章（而非引用内容）时，cmdlet 名称的第一个实例应超链接到 cmdlet 文档中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-267">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="ab43d-268">请勿在超链接的方括号内使用反撇号、粗体或其他标记。</span><span class="sxs-lookup"><span data-stu-id="ab43d-268">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="ab43d-269">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-269">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="ab43d-270">有关详细信息，请参阅本文中的 [超链接](#hyperlinks) 部分。</span><span class="sxs-lookup"><span data-stu-id="ab43d-270">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="ab43d-271">Markdown 代码示例</span><span class="sxs-lookup"><span data-stu-id="ab43d-271">Markdown for code samples</span></span>

<span data-ttu-id="ab43d-272">Markdown 支持两种不同的代码样式：</span><span class="sxs-lookup"><span data-stu-id="ab43d-272">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="ab43d-273">**代码跨越 (内联)** 由单个反撇号 (`` ` ``) 字符标记。</span><span class="sxs-lookup"><span data-stu-id="ab43d-273">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="ab43d-274">在段落内而不是作为独立的块中使用。</span><span class="sxs-lookup"><span data-stu-id="ab43d-274">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="ab43d-275">**代码块** -由三反撇号 () 字符串括起来的多行块 `` ``` `` 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-275">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="ab43d-276">代码块还可能在反撇号后面有一个语言标签。</span><span class="sxs-lookup"><span data-stu-id="ab43d-276">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="ab43d-277">语言标签对代码块的内容启用语法突出显示。</span><span class="sxs-lookup"><span data-stu-id="ab43d-277">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="ab43d-278">所有代码块都应包含在代码隔离区中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-278">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="ab43d-279">不要对代码块使用缩进。</span><span class="sxs-lookup"><span data-stu-id="ab43d-279">Never use indentation for code blocks.</span></span> <span data-ttu-id="ab43d-280">Markdown 允许此模式，但它可能会出现问题，应避免此模式。</span><span class="sxs-lookup"><span data-stu-id="ab43d-280">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="ab43d-281">代码块是一个或多个代码行，反撇号 (`` ``` ``) 代码隔离区。</span><span class="sxs-lookup"><span data-stu-id="ab43d-281">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="ab43d-282">代码隔离区标记必须位于代码示例前后其自己的行上。</span><span class="sxs-lookup"><span data-stu-id="ab43d-282">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="ab43d-283">代码块开头的标记可能具有可选的语言标签。</span><span class="sxs-lookup"><span data-stu-id="ab43d-283">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="ab43d-284">Microsoft 的开放发布系统 (OPS) 使用语言标签来支持语法突出显示功能。</span><span class="sxs-lookup"><span data-stu-id="ab43d-284">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="ab43d-285">有关支持的语言标记的完整列表，请参阅集中参与者指南中的 [隔离代码块](/contribute/code-in-docs#fenced-code-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-285">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="ab43d-286">OPS 还添加了可将代码块的内容复制到剪贴板的“复制”按钮。</span><span class="sxs-lookup"><span data-stu-id="ab43d-286">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="ab43d-287">这使你可以快速将代码粘贴到脚本中，以测试代码示例。</span><span class="sxs-lookup"><span data-stu-id="ab43d-287">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="ab43d-288">但是，并非我们文档中的所有示例都应按原样运行。</span><span class="sxs-lookup"><span data-stu-id="ab43d-288">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="ab43d-289">一些代码块是 PowerShell 概念的简单阐释。</span><span class="sxs-lookup"><span data-stu-id="ab43d-289">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="ab43d-290">文档中使用三种类型的代码块：</span><span class="sxs-lookup"><span data-stu-id="ab43d-290">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="ab43d-291">语法块</span><span class="sxs-lookup"><span data-stu-id="ab43d-291">Syntax blocks</span></span>
1. <span data-ttu-id="ab43d-292">说明性示例</span><span class="sxs-lookup"><span data-stu-id="ab43d-292">Illustrative examples</span></span>
1. <span data-ttu-id="ab43d-293">可执行示例</span><span class="sxs-lookup"><span data-stu-id="ab43d-293">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="ab43d-294">语法代码块</span><span class="sxs-lookup"><span data-stu-id="ab43d-294">Syntax code blocks</span></span>

<span data-ttu-id="ab43d-295">语法代码块用于描述命令的语法结构。</span><span class="sxs-lookup"><span data-stu-id="ab43d-295">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="ab43d-296">不要在代码隔离上使用语言标记。</span><span class="sxs-lookup"><span data-stu-id="ab43d-296">Don't use a language tag on the code fence.</span></span> <span data-ttu-id="ab43d-297">此示例演示 `Get-Command` cmdlet 所有可能的参数。</span><span class="sxs-lookup"><span data-stu-id="ab43d-297">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="ab43d-298">此示例以通用术语描述 `for` 语句：</span><span class="sxs-lookup"><span data-stu-id="ab43d-298">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="ab43d-299">演示示例</span><span class="sxs-lookup"><span data-stu-id="ab43d-299">Illustrative examples</span></span>

<span data-ttu-id="ab43d-300">演示示例用于解释 PowerShell 概念。</span><span class="sxs-lookup"><span data-stu-id="ab43d-300">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="ab43d-301">它们不会被复制到剪贴板上以执行。</span><span class="sxs-lookup"><span data-stu-id="ab43d-301">They aren't meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="ab43d-302">它们最常用于易于键入并易于理解的简单示例。</span><span class="sxs-lookup"><span data-stu-id="ab43d-302">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="ab43d-303">代码块可以包括 PowerShell 提示符和示例输出。</span><span class="sxs-lookup"><span data-stu-id="ab43d-303">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="ab43d-304">以下简单示例演示了 PowerShell 比较运算符。</span><span class="sxs-lookup"><span data-stu-id="ab43d-304">Here's a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="ab43d-305">在这种情况下，我们不希望读者复制并运行此示例。</span><span class="sxs-lookup"><span data-stu-id="ab43d-305">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="ab43d-306">可执行示例</span><span class="sxs-lookup"><span data-stu-id="ab43d-306">Executable examples</span></span>

<span data-ttu-id="ab43d-307">要复制和执行的复杂示例或示例应使用以下块样式标记：</span><span class="sxs-lookup"><span data-stu-id="ab43d-307">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="ab43d-308">PowerShell 命令显示的输出应包含在 Output 代码块中，以防止语法突出显示。</span><span class="sxs-lookup"><span data-stu-id="ab43d-308">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="ab43d-309">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-309">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="ab43d-310">" **输出** 代码" 标签不是语法突出显示系统支持的官方 "语言"。</span><span class="sxs-lookup"><span data-stu-id="ab43d-310">The **Output** code label isn't an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="ab43d-311">但是，此标签非常有用，因为 OPS 会将 "输出" 标签添加到网页上的代码框框架中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-311">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="ab43d-312">"输出" 代码框没有突出显示的语法。</span><span class="sxs-lookup"><span data-stu-id="ab43d-312">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="ab43d-313">编码样式规则</span><span class="sxs-lookup"><span data-stu-id="ab43d-313">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="ab43d-314">避免在代码示例中出现行继续符</span><span class="sxs-lookup"><span data-stu-id="ab43d-314">Avoid line continuation in code samples</span></span>

<span data-ttu-id="ab43d-315">避免在 PowerShell 代码示例中使用行继续符 (`` ` ``)。</span><span class="sxs-lookup"><span data-stu-id="ab43d-315">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="ab43d-316">如果行尾出现多余的空格，则很难看到行继续符，并且可能会引发问题。</span><span class="sxs-lookup"><span data-stu-id="ab43d-316">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="ab43d-317">使用 PowerShell 展开缩短具有多个参数的 cmdlet 的行长度。</span><span class="sxs-lookup"><span data-stu-id="ab43d-317">Use PowerShell splatting to reduce line length for cmdlets that have several parameters.</span></span>
- <span data-ttu-id="ab43d-318">利用 PowerShell 的自然换行机会，如管道 (`|`) 字符、左大括号 (`{`) 、括号 (`(`) 和方括号 (`[`) 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-318">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces (`{`), parentheses (`(`), and brackets (`[`).</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="ab43d-319">避免在示例中使用 PowerShell 提示</span><span class="sxs-lookup"><span data-stu-id="ab43d-319">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="ab43d-320">不建议使用提示字符串，因此应将其限制为旨在说明命令行用法的方案。</span><span class="sxs-lookup"><span data-stu-id="ab43d-320">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command-line usage.</span></span> <span data-ttu-id="ab43d-321">对于其中的大多数示例，提示字符串应为 `PS>` 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-321">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="ab43d-322">此提示与特定于 OS 的指示器无关。</span><span class="sxs-lookup"><span data-stu-id="ab43d-322">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="ab43d-323">在示例中需要提示，以说明更改提示的命令或显示的路径对于方案非常重要。</span><span class="sxs-lookup"><span data-stu-id="ab43d-323">Prompts are required in examples to illustrate commands that alter the prompt or when the path displayed is significant to the scenario.</span></span> <span data-ttu-id="ab43d-324">下面的示例演示使用注册表提供程序时提示的变化。</span><span class="sxs-lookup"><span data-stu-id="ab43d-324">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="dont-use-aliases-in-examples"></a><span data-ttu-id="ab43d-325">不要在示例中使用别名</span><span class="sxs-lookup"><span data-stu-id="ab43d-325">Don't use aliases in examples</span></span>

<span data-ttu-id="ab43d-326">使用所有 cmdlet 和参数的完整名称，除非专门记录别名。</span><span class="sxs-lookup"><span data-stu-id="ab43d-326">Use the full name of all cmdlets and parameters unless you're specifically documenting the alias.</span></span>
<span data-ttu-id="ab43d-327">Cmdlet 和参数名称必须使用正确的 [Pascal 大小写][] 名称。</span><span class="sxs-lookup"><span data-stu-id="ab43d-327">Cmdlet and parameter names must use the proper [Pascal-cased][] names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="ab43d-328">在示例中使用参数</span><span class="sxs-lookup"><span data-stu-id="ab43d-328">Using parameters in examples</span></span>

<span data-ttu-id="ab43d-329">避免使用位置参数。</span><span class="sxs-lookup"><span data-stu-id="ab43d-329">Avoid using positional parameters.</span></span> <span data-ttu-id="ab43d-330">通常，应始终在示例中包含参数名称，即使参数是位置。</span><span class="sxs-lookup"><span data-stu-id="ab43d-330">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="ab43d-331">这样可减少在示例中产生混淆的可能性。</span><span class="sxs-lookup"><span data-stu-id="ab43d-331">This reduces the chance of confusion in your examples.</span></span>

## <a name="formatting-cmdlet-reference-articles"></a><span data-ttu-id="ab43d-332">格式化 cmdlet 参考文章</span><span class="sxs-lookup"><span data-stu-id="ab43d-332">Formatting cmdlet reference articles</span></span>

<span data-ttu-id="ab43d-333">Cmdlet 引用文章具有特定的结构。</span><span class="sxs-lookup"><span data-stu-id="ab43d-333">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="ab43d-334">此结构由 PlatyPS 定义[][]。</span><span class="sxs-lookup"><span data-stu-id="ab43d-334">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="ab43d-335">Platypus 为 Markdown 中的 PowerShell 模块生成 cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="ab43d-335">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="ab43d-336">编辑 Markdown 文件后，使用 PlatyPS 创建 `Get-Help` cmdlet 使用的 MAML 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="ab43d-336">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="ab43d-337">PlatyPS 具有用于 cmdlet 引用的硬编码架构，并且已写入代码中。</span><span class="sxs-lookup"><span data-stu-id="ab43d-337">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="ab43d-338">[platyPS.schema.md][] 文档尝试描述此结构。</span><span class="sxs-lookup"><span data-stu-id="ab43d-338">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="ab43d-339">架构冲突会导致生成错误，必须先修复这些错误然后才能接受你撰写的内容。</span><span class="sxs-lookup"><span data-stu-id="ab43d-339">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

- <span data-ttu-id="ab43d-340">请勿删除任何 ATX 标头结构。</span><span class="sxs-lookup"><span data-stu-id="ab43d-340">Don't remove any of the ATX header structures.</span></span> <span data-ttu-id="ab43d-341">PlatyPS 需要一组特定的标头。</span><span class="sxs-lookup"><span data-stu-id="ab43d-341">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="ab43d-342">输入类型和输出类型标头必须具有类型。</span><span class="sxs-lookup"><span data-stu-id="ab43d-342">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="ab43d-343">如果该 cmdlet 不接受输入或返回值，则使用值 `None` 。</span><span class="sxs-lookup"><span data-stu-id="ab43d-343">If the cmdlet doesn't take input or return a value, then use the value `None`.</span></span>
- <span data-ttu-id="ab43d-344">任何段落都可使用内联代码范围。</span><span class="sxs-lookup"><span data-stu-id="ab43d-344">Inline code spans can be used in any paragraph.</span></span>
- <span data-ttu-id="ab43d-345">仅在 " **示例** " 部分中允许隔离代码块。</span><span class="sxs-lookup"><span data-stu-id="ab43d-345">Fenced code blocks are only allowed in the **EXAMPLES** section.</span></span>

<span data-ttu-id="ab43d-346">在 Platypus 架构中， **示例** 是 H2 标头。</span><span class="sxs-lookup"><span data-stu-id="ab43d-346">In the PlatyPS schema, **EXAMPLES** is an H2 header.</span></span> <span data-ttu-id="ab43d-347">每个示例都是一个 H3 标头。</span><span class="sxs-lookup"><span data-stu-id="ab43d-347">Each example is an H3 header.</span></span> <span data-ttu-id="ab43d-348">在示例中，该架构不允许按段落分隔代码块。</span><span class="sxs-lookup"><span data-stu-id="ab43d-348">Within an example, the schema doesn't allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="ab43d-349">架构允许以下结构：</span><span class="sxs-lookup"><span data-stu-id="ab43d-349">The schema allows the following structure:</span></span>

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="ab43d-350">为每个示例编号并添加简短标题。</span><span class="sxs-lookup"><span data-stu-id="ab43d-350">Number each example and add a brief title.</span></span>

<span data-ttu-id="ab43d-351">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-351">For example:</span></span>

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a><span data-ttu-id="ab43d-352">设置 About_ 文件的格式</span><span class="sxs-lookup"><span data-stu-id="ab43d-352">Formatting About_ files</span></span>

<span data-ttu-id="ab43d-353">`About_*` 文件是以 Markdown 编写的，但以纯文本文件的形式提供。</span><span class="sxs-lookup"><span data-stu-id="ab43d-353">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="ab43d-354">我们使用 [Pandoc][] 将 Markdown 转换为纯文本。</span><span class="sxs-lookup"><span data-stu-id="ab43d-354">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="ab43d-355">`About_*` 在所有版本的 PowerShell 和发布工具中，文件的格式都是最兼容的。</span><span class="sxs-lookup"><span data-stu-id="ab43d-355">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="ab43d-356">基本格式设置指南：</span><span class="sxs-lookup"><span data-stu-id="ab43d-356">Basic formatting guidelines:</span></span>

- <span data-ttu-id="ab43d-357">将普通行限制为80个字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-357">Limit normal lines to 80 characters</span></span>
- <span data-ttu-id="ab43d-358">代码块限制为76个字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-358">Code blocks are limited to 76 characters</span></span>
- <span data-ttu-id="ab43d-359">Blockquotes (和警报) 的范围限制为78个字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-359">Blockquotes (and Alerts) are limited 78 characters</span></span>
- <span data-ttu-id="ab43d-360">使用这些特殊的元字符时 `\` ， `$` 和 `<` ：</span><span class="sxs-lookup"><span data-stu-id="ab43d-360">When using these special meta-characters `\`,`$`, and `<`:</span></span>
  - <span data-ttu-id="ab43d-361">在标头中，这些字符必须使用前导字符进行转义， `\` 或使用反撇号 (包含在代码中 `` ` ``) </span><span class="sxs-lookup"><span data-stu-id="ab43d-361">Within a header, these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="ab43d-362">在段落中，应将这些字符放入代码跨越。</span><span class="sxs-lookup"><span data-stu-id="ab43d-362">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="ab43d-363">例如：</span><span class="sxs-lookup"><span data-stu-id="ab43d-363">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="ab43d-364">表格需要超过76个字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-364">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="ab43d-365">手动将单元格内容换到多行</span><span class="sxs-lookup"><span data-stu-id="ab43d-365">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="ab43d-366">在每一行上使用开始和结束 `|` 字符</span><span class="sxs-lookup"><span data-stu-id="ab43d-366">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="ab43d-367">下面的示例说明了如何正确构造一个表，该表包含在单元内的多个行上进行换行的信息。</span><span class="sxs-lookup"><span data-stu-id="ab43d-367">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="ab43d-368">76列限制仅适用于 `About_*` 主题。</span><span class="sxs-lookup"><span data-stu-id="ab43d-368">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="ab43d-369">你可以使用概念或 cmdlet 参考文章中的宽列。</span><span class="sxs-lookup"><span data-stu-id="ab43d-369">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab43d-370">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ab43d-370">Next steps</span></span>

[<span data-ttu-id="ab43d-371">编辑清单</span><span class="sxs-lookup"><span data-stu-id="ab43d-371">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Pascal 大小写]: https://en.wikipedia.org/wiki/PascalCase
[Pascal-cased]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
