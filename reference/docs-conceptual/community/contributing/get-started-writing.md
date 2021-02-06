---
title: 开始参与撰写 PowerShell 文档
description: 本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597841"
---
# <a name="get-started-contributing-to-powershell-documentation"></a><span data-ttu-id="1528a-103">开始参与撰写 PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="1528a-103">Get started contributing to PowerShell documentation</span></span>

<span data-ttu-id="1528a-104">本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。</span><span class="sxs-lookup"><span data-stu-id="1528a-104">This article is an overview of how to get started as a contributor to the PowerShell documentation.</span></span>

## <a name="powershell-docs-structure"></a><span data-ttu-id="1528a-105">PowerShell-Docs 结构</span><span class="sxs-lookup"><span data-stu-id="1528a-105">PowerShell-Docs structure</span></span>

<span data-ttu-id="1528a-106">[PowerShell 文档存储库][psdocs]分为两组内容：引用和概念。</span><span class="sxs-lookup"><span data-stu-id="1528a-106">The [PowerShell-Docs repository][psdocs] is divided into two groups of content: reference and conceptual.</span></span>

### <a name="reference-content"></a><span data-ttu-id="1528a-107">参考内容</span><span class="sxs-lookup"><span data-stu-id="1528a-107">Reference content</span></span>

<span data-ttu-id="1528a-108">参考内容是 PowerShell cmdlet 参考，适用于 PowerShell 中提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1528a-108">The reference content is the PowerShell cmdlet reference for the cmdlets that ship in PowerShell.</span></span>
<span data-ttu-id="1528a-109">在版本文件夹 (5.1、7.0、7.1 和 7.2) 中收集 [引用][ref] 。</span><span class="sxs-lookup"><span data-stu-id="1528a-109">The [reference][ref] is collected in versions folders (5.1, 7.0, 7.1, and 7.2).</span></span> <span data-ttu-id="1528a-110">此内容仅包含 PowerShell 随附的模块的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="1528a-110">This content contains cmdlet reference only for the modules that ship with PowerShell.</span></span> <span data-ttu-id="1528a-111">此内容还用于创建由 cmdlet 显示的帮助信息 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="1528a-111">This content is also used to create the help information displayed by the `Get-Help` cmdlet.</span></span>

### <a name="conceptual-content"></a><span data-ttu-id="1528a-112">概念内容</span><span class="sxs-lookup"><span data-stu-id="1528a-112">Conceptual content</span></span>

<span data-ttu-id="1528a-113">概念性文档包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="1528a-113">The conceptual documentation includes the following content:</span></span>

- <span data-ttu-id="1528a-114">发行说明</span><span class="sxs-lookup"><span data-stu-id="1528a-114">Release notes</span></span>
- <span data-ttu-id="1528a-115">设置说明</span><span class="sxs-lookup"><span data-stu-id="1528a-115">Setup instructions</span></span>
- <span data-ttu-id="1528a-116">示例脚本和操作指南文章</span><span class="sxs-lookup"><span data-stu-id="1528a-116">Sample scripts and how-to articles</span></span>
- <span data-ttu-id="1528a-117">DSC 文档</span><span class="sxs-lookup"><span data-stu-id="1528a-117">DSC documentation</span></span>
- <span data-ttu-id="1528a-118">SDK 文档</span><span class="sxs-lookup"><span data-stu-id="1528a-118">SDK documentation</span></span>

<span data-ttu-id="1528a-119">[概念文档][conceptual]不按版本进行组织。</span><span class="sxs-lookup"><span data-stu-id="1528a-119">The [conceptual documentation][conceptual] is not organized by version.</span></span> <span data-ttu-id="1528a-120">每个 PowerShell 版本都将显示所有项目。</span><span class="sxs-lookup"><span data-stu-id="1528a-120">All articles are displayed for every version of PowerShell.</span></span> <span data-ttu-id="1528a-121">我们正在努力创建特定版本的文章。</span><span class="sxs-lookup"><span data-stu-id="1528a-121">We're working to create version-specific articles.</span></span> <span data-ttu-id="1528a-122">如果文档中提供了该功能，则将使用相应的信息更新本指南。</span><span class="sxs-lookup"><span data-stu-id="1528a-122">When that feature is available in our documentation, this guide will be update with the appropriate information.</span></span>

> [!NOTE]
> <span data-ttu-id="1528a-123">在添加、删除或重命名概念项目时，必须更新和包含在拉取请求中的目录。</span><span class="sxs-lookup"><span data-stu-id="1528a-123">Anytime a conceptual article is added, removed, or renamed, the TOC must be updated and included in the pull request.</span></span>

## <a name="creating-new-articles"></a><span data-ttu-id="1528a-124">创建新项目</span><span class="sxs-lookup"><span data-stu-id="1528a-124">Creating new articles</span></span>

<span data-ttu-id="1528a-125">必须为要提供的任何新文档创建 GitHub 问题。</span><span class="sxs-lookup"><span data-stu-id="1528a-125">A GitHub issue must be created for any new document you want to contribute.</span></span> <span data-ttu-id="1528a-126">检查现有问题，确保不会重复工作。</span><span class="sxs-lookup"><span data-stu-id="1528a-126">Check for existing issues to make sure you're not duplicating efforts.</span></span> <span data-ttu-id="1528a-127">已分配的问题被视为 `in progress` 。</span><span class="sxs-lookup"><span data-stu-id="1528a-127">Assigned issues are considered to be `in progress`.</span></span> <span data-ttu-id="1528a-128">如果你想要协作解决某个问题，请联系分配给该问题的人员。</span><span class="sxs-lookup"><span data-stu-id="1528a-128">If you wish to collaborate on an issue, contact the person assigned to the issue.</span></span>

<span data-ttu-id="1528a-129">类似于 PowerShell [RFC 过程][rfc]，在编写内容之前创建问题。</span><span class="sxs-lookup"><span data-stu-id="1528a-129">Similar to the PowerShell [RFC process][rfc], create an issue before you write the content.</span></span> <span data-ttu-id="1528a-130">此问题可确保不会浪费时间和精力处理 PowerShell-Docs 团队拒绝的工作。</span><span class="sxs-lookup"><span data-stu-id="1528a-130">The issue ensures you don't waste time and effort on work that gets rejected by the PowerShell-Docs team.</span></span> <span data-ttu-id="1528a-131">此问题使我们能够与你联系，以确定内容的范围以及它在 PowerShell 文档中的位置。</span><span class="sxs-lookup"><span data-stu-id="1528a-131">The issue allows us to consult with you on the scope of the content and where it fits in the PowerShell documentation.</span></span> <span data-ttu-id="1528a-132">所有文章都必须包含在目录中 (TOC) 。</span><span class="sxs-lookup"><span data-stu-id="1528a-132">All articles must be included in the Table of Contents (TOC).</span></span> <span data-ttu-id="1528a-133">建议的目录位置应包含在问题讨论中。</span><span class="sxs-lookup"><span data-stu-id="1528a-133">The proposed TOC location should be included in the issue discussion.</span></span>

> [!NOTE]
> <span data-ttu-id="1528a-134">引用内容的目录由发布系统自动生成。</span><span class="sxs-lookup"><span data-stu-id="1528a-134">The TOC for reference content is autogenerated by the publishing system.</span></span> <span data-ttu-id="1528a-135">无需更新目录。</span><span class="sxs-lookup"><span data-stu-id="1528a-135">You don't have to update the TOC.</span></span>

## <a name="updating-existing-articles"></a><span data-ttu-id="1528a-136">更新现有项目</span><span class="sxs-lookup"><span data-stu-id="1528a-136">Updating existing articles</span></span>

<span data-ttu-id="1528a-137">在适用的情况下，在此存储库中维护的所有 PowerShell 版本中复制 cmdlet 引用文章。</span><span class="sxs-lookup"><span data-stu-id="1528a-137">Where applicable, cmdlet reference articles are duplicated across all versions of PowerShell maintained in this repository.</span></span> <span data-ttu-id="1528a-138">在报告有关 cmdlet 引用或项目的问题时 `About_` ，你必须指定此问题影响的版本。</span><span class="sxs-lookup"><span data-stu-id="1528a-138">When reporting an issue about a cmdlet reference or an `About_` article, you must specify which versions are affected by the issue.</span></span> <span data-ttu-id="1528a-139">GitHub 中的问题模板包含版本的清单。</span><span class="sxs-lookup"><span data-stu-id="1528a-139">The issue template in GitHub includes a checklist of versions.</span></span> <span data-ttu-id="1528a-140">使用此复选框可指定受影响的内容版本。</span><span class="sxs-lookup"><span data-stu-id="1528a-140">Use the checkboxes to specify which versions of the content are affected.</span></span>

<span data-ttu-id="1528a-141">查看文章的所有版本，查看其他版本是否需要相同的更改。</span><span class="sxs-lookup"><span data-stu-id="1528a-141">Check all version of the article to see if the same change is needed in the other versions.</span></span> <span data-ttu-id="1528a-142">对文件的每个版本应用相应的更改。</span><span class="sxs-lookup"><span data-stu-id="1528a-142">Apply the appropriate change to each version of the file.</span></span>

## <a name="localized-content"></a><span data-ttu-id="1528a-143">本地化内容</span><span class="sxs-lookup"><span data-stu-id="1528a-143">Localized content</span></span>

<span data-ttu-id="1528a-144">PowerShell 文档以英文编写，翻译为17个其他语言。</span><span class="sxs-lookup"><span data-stu-id="1528a-144">The PowerShell documentation is written in English and translated into 17 other languages.</span></span> <span data-ttu-id="1528a-145">英语内容存储在名为的 GitHub 存储库中 `MicrosoftDocs/PowerShell-Docs` 。</span><span class="sxs-lookup"><span data-stu-id="1528a-145">The English content is stored in the GitHub repository named `MicrosoftDocs/PowerShell-Docs`.</span></span> <span data-ttu-id="1528a-146">对于每种语言，本地化内容都存储在单独的存储库中。</span><span class="sxs-lookup"><span data-stu-id="1528a-146">The localized content is stored in a separate repository for each language.</span></span> <span data-ttu-id="1528a-147">存储库使用相同的 basename，但将区域设置名称添加到结尾。</span><span class="sxs-lookup"><span data-stu-id="1528a-147">The repositories use the same basename but add the locale name to the end.</span></span> <span data-ttu-id="1528a-148">例如， `MicrosoftDocs/PowerShell-Docs.de-de` 包含转换为德语的内容。</span><span class="sxs-lookup"><span data-stu-id="1528a-148">For example, `MicrosoftDocs/PowerShell-Docs.de-de` contains the content that was translated to German.</span></span>

<span data-ttu-id="1528a-149">通常，问题和更改应提交到英语存储库。</span><span class="sxs-lookup"><span data-stu-id="1528a-149">In general, issues and changes should be submitted to the English repository.</span></span> <span data-ttu-id="1528a-150">所有翻译首先从英语内容开始。</span><span class="sxs-lookup"><span data-stu-id="1528a-150">All translations start from the English content first.</span></span> <span data-ttu-id="1528a-151">我们同时使用人工翻译和机器翻译。</span><span class="sxs-lookup"><span data-stu-id="1528a-151">We use both human and machine translation.</span></span>

| <span data-ttu-id="1528a-152">转换方法</span><span class="sxs-lookup"><span data-stu-id="1528a-152">Translation method</span></span>  |                              <span data-ttu-id="1528a-153">语言</span><span class="sxs-lookup"><span data-stu-id="1528a-153">Languages</span></span>                               |
| ------------------- | -------------------------------------------------------------------- |
| <span data-ttu-id="1528a-154">人工翻译</span><span class="sxs-lookup"><span data-stu-id="1528a-154">Human translation</span></span>   | <span data-ttu-id="1528a-155">反 DE，es，fr-fr，it，a，ja-jp，ko-KR，pt-BR，ru-RU，zh-chs，zh-chs</span><span class="sxs-lookup"><span data-stu-id="1528a-155">de-DE, es-ES, fr-FR, it-IT, ja-JP, ko-KR, pt-BR, ru-RU, zh-CN, zh-TW</span></span> |
| <span data-ttu-id="1528a-156">机器翻译</span><span class="sxs-lookup"><span data-stu-id="1528a-156">Machine translation</span></span> | <span data-ttu-id="1528a-157">cs-CZ、hu-HU、nl-NL、pl、pt、sv-SE、tr-TR</span><span class="sxs-lookup"><span data-stu-id="1528a-157">cs-CZ, hu-HU, nl-NL, pl-PL, pt-PT, sv-SE, tr-TR</span></span>                      |

<span data-ttu-id="1528a-158">计算机翻译翻译的内容可能并不总是产生正确的词选择和语法。</span><span class="sxs-lookup"><span data-stu-id="1528a-158">The content translated by machine translation may not always result in correct word choices and grammar.</span></span> <span data-ttu-id="1528a-159">如果你在翻译时发现任何语言出现错误，而不是本文的技术细节，请在本地化存储库中提出问题。</span><span class="sxs-lookup"><span data-stu-id="1528a-159">If you find an error in translation for any language, rather than in the technical details of the article, open an issue in the localized repository.</span></span> <span data-ttu-id="1528a-160">说明为什么您认为翻译不正确。</span><span class="sxs-lookup"><span data-stu-id="1528a-160">Explain why you think the translation is incorrect.</span></span> <span data-ttu-id="1528a-161">我们的本地化团队查看并响应这些问题。</span><span class="sxs-lookup"><span data-stu-id="1528a-161">Our localization team reviews and responds to these issues.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1528a-162">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1528a-162">Next steps</span></span>

<span data-ttu-id="1528a-163">可以通过两种常见方式在 GitHub 中提交更改。</span><span class="sxs-lookup"><span data-stu-id="1528a-163">There are two common ways of submitting changes in GitHub.</span></span> <span data-ttu-id="1528a-164">以下两种方法都在中心参与者指南中进行了介绍：</span><span class="sxs-lookup"><span data-stu-id="1528a-164">Both methods are described in the central Contributor's Guide:</span></span>

1. <span data-ttu-id="1528a-165">可以快速编辑 GitHub web 界面中的 [现有文档](/contribute/#quick-edits-to-existing-documents) 。</span><span class="sxs-lookup"><span data-stu-id="1528a-165">You can make [quick edits to existing documents](/contribute/#quick-edits-to-existing-documents) in the GitHub web interface.</span></span>
1. <span data-ttu-id="1528a-166">使用 [完整 GitHub 工作流][making-changes] 来添加新项目、更新多个文件或其他大更改。</span><span class="sxs-lookup"><span data-stu-id="1528a-166">Use the [full GitHub workflow][making-changes] for adding new articles, updating multiple files, or other large changes.</span></span>

<span data-ttu-id="1528a-167">在开始任何更改之前，应创建 PowerShell-Docs 存储库的分支。</span><span class="sxs-lookup"><span data-stu-id="1528a-167">Before starting any changes, you should create a fork of the PowerShell-Docs repository.</span></span> <span data-ttu-id="1528a-168">应在复制 PowerShell 文档的工作分支中进行更改。如果使用 GitHub 中的 **快速编辑** 方法，则会为你处理这些步骤。</span><span class="sxs-lookup"><span data-stu-id="1528a-168">The changes should be made in a working branch in you copy of the PowerShell-Docs. If you're using the **quick edit** method in GitHub, these steps are handled for you.</span></span> <span data-ttu-id="1528a-169">如果使用的是 **完整 GitHub 工作流**，则必须将设置为在 [本地运行][fork]。</span><span class="sxs-lookup"><span data-stu-id="1528a-169">If you're using the **full GitHub workflow**, you must be set up to [work locally][fork].</span></span>

<span data-ttu-id="1528a-170">两种方法都是通过创建拉取请求 (PR) 结束。</span><span class="sxs-lookup"><span data-stu-id="1528a-170">Both methods end with the creation of a Pull Request (PR).</span></span> <span data-ttu-id="1528a-171">有关详细信息和最佳实践，请参阅 [提交拉取请求](pull-requests.md) 。</span><span class="sxs-lookup"><span data-stu-id="1528a-171">See [Submitting a pull request](pull-requests.md) for more information and best practices.</span></span>

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
