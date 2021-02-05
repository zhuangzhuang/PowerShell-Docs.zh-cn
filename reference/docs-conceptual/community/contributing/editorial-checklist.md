---
title: 编辑清单
description: 这是用于编辑 PowerShell 文档的规则的汇总列表。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b5baf7366239084779d34e23f218e5e6222ed1a3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "81624731"
---
# <a name="editors-checklist"></a><span data-ttu-id="363ad-103">编辑器的清单</span><span class="sxs-lookup"><span data-stu-id="363ad-103">Editor's checklist</span></span>

<span data-ttu-id="363ad-104">这是在撰写新文章或更新现有文章时要应用的规则的摘要。</span><span class="sxs-lookup"><span data-stu-id="363ad-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="363ad-105">有关这些规则的详细说明和示例，请参阅参与者指南中的其他文章。</span><span class="sxs-lookup"><span data-stu-id="363ad-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="363ad-106">元数据</span><span class="sxs-lookup"><span data-stu-id="363ad-106">Metadata</span></span>

- <span data-ttu-id="363ad-107">`ms.date`：格式必须为 MM/DD/YYYY </span><span class="sxs-lookup"><span data-stu-id="363ad-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="363ad-108">更改有重大更新或真实更新时的日期</span><span class="sxs-lookup"><span data-stu-id="363ad-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="363ad-109">重新组织文章</span><span class="sxs-lookup"><span data-stu-id="363ad-109">Reorganizing the article</span></span>
    - <span data-ttu-id="363ad-110">修复事实错误</span><span class="sxs-lookup"><span data-stu-id="363ad-110">Fixing factual errors</span></span>
    - <span data-ttu-id="363ad-111">添加新信息</span><span class="sxs-lookup"><span data-stu-id="363ad-111">Adding new information</span></span>
  - <span data-ttu-id="363ad-112">如果更新无意义，请不要更改日期</span><span class="sxs-lookup"><span data-stu-id="363ad-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="363ad-113">修复拼写错误和格式设置</span><span class="sxs-lookup"><span data-stu-id="363ad-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="363ad-114">`title`：包含空格的 43-59 个字符的唯一字符串</span><span class="sxs-lookup"><span data-stu-id="363ad-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="363ad-115">不包括站点标识符（它是自动生成的）</span><span class="sxs-lookup"><span data-stu-id="363ad-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="363ad-116">使用句首大写形式 - 仅大写第一个单词和所有专有名词</span><span class="sxs-lookup"><span data-stu-id="363ad-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="363ad-117">`description`设置用户帐户 ：包含空格的 115-145 个字符 - 此摘要显示在搜索结果中</span><span class="sxs-lookup"><span data-stu-id="363ad-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="363ad-118">格式设置</span><span class="sxs-lookup"><span data-stu-id="363ad-118">Formatting</span></span>

- <span data-ttu-id="363ad-119">段落中内联显示的反引号语法元素</span><span class="sxs-lookup"><span data-stu-id="363ad-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="363ad-120">Cmdlet 名称 `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="363ad-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="363ad-121">变量 `$counter`</span><span class="sxs-lookup"><span data-stu-id="363ad-121">Variable `$counter`</span></span>
  - <span data-ttu-id="363ad-122">语法示例 `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="363ad-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="363ad-123">文件路径 `C:\Program Files\PowerShell`、`/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="363ad-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="363ad-124">不应在文档中单击的 URL</span><span class="sxs-lookup"><span data-stu-id="363ad-124">URLs that are not meant to be clickable in the document</span></span>
  - <span data-ttu-id="363ad-125">属性值或参数值</span><span class="sxs-lookup"><span data-stu-id="363ad-125">Property or parameter values</span></span>
- <span data-ttu-id="363ad-126">对属性名称、参数名称、类名称、模块名称、实体名称、对象或类型名称使用粗体</span><span class="sxs-lookup"><span data-stu-id="363ad-126">Use bold for property names, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="363ad-127">粗体用于语义标记，而不用于强调</span><span class="sxs-lookup"><span data-stu-id="363ad-127">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="363ad-128">粗体 - 使用星号 `**`</span><span class="sxs-lookup"><span data-stu-id="363ad-128">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="363ad-129">斜体 - 使用下划线 `_`</span><span class="sxs-lookup"><span data-stu-id="363ad-129">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="363ad-130">仅用于强调，而不用于语义标记</span><span class="sxs-lookup"><span data-stu-id="363ad-130">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="363ad-131">100 列处的换行符（对于 about_Topics  ，则为 80）</span><span class="sxs-lookup"><span data-stu-id="363ad-131">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="363ad-132">无硬 Tab - 仅使用空格</span><span class="sxs-lookup"><span data-stu-id="363ad-132">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="363ad-133">行中无尾随空格</span><span class="sxs-lookup"><span data-stu-id="363ad-133">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="363ad-134">头文件</span><span class="sxs-lookup"><span data-stu-id="363ad-134">Headers</span></span>

- <span data-ttu-id="363ad-135">H1 是第一个 - 每篇文章中只有一个 H1</span><span class="sxs-lookup"><span data-stu-id="363ad-135">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="363ad-136">仅使用 [ATX 标头](https://github.github.com/gfm/#atx-headings)</span><span class="sxs-lookup"><span data-stu-id="363ad-136">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="363ad-137">对所有标头使用句首大写形式</span><span class="sxs-lookup"><span data-stu-id="363ad-137">Use sentence case for all headers</span></span>
- <span data-ttu-id="363ad-138">不要跨级别 - 如果没有 H2，则没有 H3</span><span class="sxs-lookup"><span data-stu-id="363ad-138">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="363ad-139">H3 或 H4 的最大深度</span><span class="sxs-lookup"><span data-stu-id="363ad-139">Max depth of H3 or H4</span></span>
- <span data-ttu-id="363ad-140">前后空行</span><span class="sxs-lookup"><span data-stu-id="363ad-140">Blank line before and after</span></span>
- <span data-ttu-id="363ad-141">PlatyPS 强制执行其架构中的特定标头 - 不要添加或删除标头</span><span class="sxs-lookup"><span data-stu-id="363ad-141">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="363ad-142">代码块</span><span class="sxs-lookup"><span data-stu-id="363ad-142">Code blocks</span></span>

- <span data-ttu-id="363ad-143">前后空行</span><span class="sxs-lookup"><span data-stu-id="363ad-143">Blank line before and after</span></span>
- <span data-ttu-id="363ad-144">使用已标记的代码栅栏 - powershell、输出或其他相应的语言 ID  </span><span class="sxs-lookup"><span data-stu-id="363ad-144">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="363ad-145">未标记的栅栏 - 语法块或其他 shell</span><span class="sxs-lookup"><span data-stu-id="363ad-145">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="363ad-146">将输出置于单独的代码块中，除了一些简单的示例，在这些示例中，你不打算让读者使用“复制”按钮 </span><span class="sxs-lookup"><span data-stu-id="363ad-146">Put output in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="363ad-147">请参阅[支持的语言](/contribute/code-in-docs#supported-languages)的列表</span><span class="sxs-lookup"><span data-stu-id="363ad-147">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="363ad-148">列表</span><span class="sxs-lookup"><span data-stu-id="363ad-148">Lists</span></span>

- <span data-ttu-id="363ad-149">正确缩进</span><span class="sxs-lookup"><span data-stu-id="363ad-149">Indented properly</span></span>
- <span data-ttu-id="363ad-150">第一项之前和最后一项之后的空行</span><span class="sxs-lookup"><span data-stu-id="363ad-150">Blank line before first item and after last item</span></span>
- <span data-ttu-id="363ad-151">项目符号 - 使用连字符 (`-`)，而不是星号 (`*`) - 很容易与强调混淆</span><span class="sxs-lookup"><span data-stu-id="363ad-151">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="363ad-152">对于带编号的列表，所有数字都为“1.”</span><span class="sxs-lookup"><span data-stu-id="363ad-152">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="363ad-153">术语</span><span class="sxs-lookup"><span data-stu-id="363ad-153">Terminology</span></span>

- <span data-ttu-id="363ad-154">PowerShell 与Windows PowerShell 与PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="363ad-154">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="363ad-155">请参阅[产品术语](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="363ad-155">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="363ad-156">Cmdlet 参考示例</span><span class="sxs-lookup"><span data-stu-id="363ad-156">Cmdlet reference examples</span></span>

- <span data-ttu-id="363ad-157">cmdlet 参考中必须至少有一个示例</span><span class="sxs-lookup"><span data-stu-id="363ad-157">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="363ad-158">示例应仅是足以演示用法的代码</span><span class="sxs-lookup"><span data-stu-id="363ad-158">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="363ad-159">PowerShell 语法</span><span class="sxs-lookup"><span data-stu-id="363ad-159">PowerShell syntax</span></span>
  - <span data-ttu-id="363ad-160">使用 cmdlet 和参数的全名 - 无别名</span><span class="sxs-lookup"><span data-stu-id="363ad-160">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="363ad-161">当命令行太长时，展开参数</span><span class="sxs-lookup"><span data-stu-id="363ad-161">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="363ad-162">避免使用续行符反引号 - 仅在必要时使用</span><span class="sxs-lookup"><span data-stu-id="363ad-162">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="363ad-163">删除或简化 PowerShell 提示符 (`PS>`)（示例需要时除外）</span><span class="sxs-lookup"><span data-stu-id="363ad-163">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="363ad-164">Cmdlet 参考示例必须遵循以下 PlatyPS 架构</span><span class="sxs-lookup"><span data-stu-id="363ad-164">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="363ad-165">不要在代码块之间放置段落。</span><span class="sxs-lookup"><span data-stu-id="363ad-165">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="363ad-166">所有描述性内容必须位于代码块之前或之后。</span><span class="sxs-lookup"><span data-stu-id="363ad-166">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="363ad-167">链接到其他文档</span><span class="sxs-lookup"><span data-stu-id="363ad-167">Linking to other documents</span></span>

- <span data-ttu-id="363ad-168">在 docset 之外或在 cmdlet 参考和概念之间链接</span><span class="sxs-lookup"><span data-stu-id="363ad-168">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="363ad-169">链接到 docs.microsoft.com 时使用相对 URL（删除 `https://docs.microsoft.com/en-us`）</span><span class="sxs-lookup"><span data-stu-id="363ad-169">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="363ad-170">不在 Microsoft 属性的 URL 中包含区域设置（例如，</span><span class="sxs-lookup"><span data-stu-id="363ad-170">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="363ad-171">从 URL 中删除 `/en-us`）</span><span class="sxs-lookup"><span data-stu-id="363ad-171">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="363ad-172">外部网站的所有 URL 都应使用 HTTPS，除非它对目标站点无效</span><span class="sxs-lookup"><span data-stu-id="363ad-172">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="363ad-173">在 docset 中</span><span class="sxs-lookup"><span data-stu-id="363ad-173">Within docset</span></span>
  - <span data-ttu-id="363ad-174">链接到文件路径（例如 `../folder/file.md`）</span><span class="sxs-lookup"><span data-stu-id="363ad-174">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="363ad-175">所有文件路径都使用正斜杠 (`/`) 字符</span><span class="sxs-lookup"><span data-stu-id="363ad-175">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="363ad-176">图像链接应包含唯一的替换文字</span><span class="sxs-lookup"><span data-stu-id="363ad-176">Image links should have unique alt text</span></span>
