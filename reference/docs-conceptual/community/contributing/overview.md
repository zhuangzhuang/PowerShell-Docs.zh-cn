---
title: 参与 PowerShell 文档撰写
description: 本文概述了参与 PowerShell 文档撰写所需的步骤。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 9fbdafa023eac80340437f30d2d6925a1a4ed3cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "99596610"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="50619-103">参与 PowerShell 文档撰写</span><span class="sxs-lookup"><span data-stu-id="50619-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="50619-104">感谢你对 PowerShell 的支持！</span><span class="sxs-lookup"><span data-stu-id="50619-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="50619-105">参与者指南是一系列文章，介绍了在 Microsoft 创建文档时使用的工具和过程。</span><span class="sxs-lookup"><span data-stu-id="50619-105">The Contributor's Guide is a collection of articles that describe the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="50619-106">其中一些指南涵盖了发布到 [docs.microsoft.com][docs] 的任何文档集共有的信息。</span><span class="sxs-lookup"><span data-stu-id="50619-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="50619-107">一些指南专门介绍如何编写 PowerShell 文档。</span><span class="sxs-lookup"><span data-stu-id="50619-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="50619-108">在汇总的[参与者指南][contribute]中提供了一些常见文章。</span><span class="sxs-lookup"><span data-stu-id="50619-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="50619-109">本文介绍特定于 PowerShell 的指南。</span><span class="sxs-lookup"><span data-stu-id="50619-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="50619-110">供稿途径</span><span class="sxs-lookup"><span data-stu-id="50619-110">Ways to contribute</span></span>

<span data-ttu-id="50619-111">有两种供稿途径。</span><span class="sxs-lookup"><span data-stu-id="50619-111">There are two ways to contribute.</span></span> <span data-ttu-id="50619-112">无论你使用哪种途径，我们都深表感谢。</span><span class="sxs-lookup"><span data-stu-id="50619-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="50619-113">[提出问题][file-an-issue]有助于我们发现文档中的问题和缺陷。</span><span class="sxs-lookup"><span data-stu-id="50619-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="50619-114">有时，这些问题比较棘手，需要进一步调查研究。</span><span class="sxs-lookup"><span data-stu-id="50619-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="50619-115">在解决问题的过程中，我们能够针对问题展开讨论，并制定满意的解决方法。</span><span class="sxs-lookup"><span data-stu-id="50619-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="50619-116">将[拉取请求提交](pull-requests.md)到添加或更改内容是一个更复杂的过程。</span><span class="sxs-lookup"><span data-stu-id="50619-116">[Submitting a pull request](pull-requests.md) to add or change content is a more involved process.</span></span>
  <span data-ttu-id="50619-117">以下信息概述了将内容提交到文档会用到的工具、流程和标准。</span><span class="sxs-lookup"><span data-stu-id="50619-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="50619-118">准备参与撰写文档</span><span class="sxs-lookup"><span data-stu-id="50619-118">Prepare to make a contribution</span></span>

<span data-ttu-id="50619-119">参与撰写文档需要一个 GitHub 帐户。</span><span class="sxs-lookup"><span data-stu-id="50619-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="50619-120">使用下列清单来安装和配置发布所需的工具。</span><span class="sxs-lookup"><span data-stu-id="50619-120">Use the following checklist to install and configure the tools you need to make contributions.</span></span>

1. [<span data-ttu-id="50619-121">注册 GitHub</span><span class="sxs-lookup"><span data-stu-id="50619-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="50619-122">安装 Git 和 Markdown 工具</span><span class="sxs-lookup"><span data-stu-id="50619-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="50619-123">安装 Docs 创作包</span><span class="sxs-lookup"><span data-stu-id="50619-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="50619-124">[安装 Posh-Git][posh-git] - 不是必需的，但建议安装</span><span class="sxs-lookup"><span data-stu-id="50619-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="50619-125">设置本地 Git 存储库</span><span class="sxs-lookup"><span data-stu-id="50619-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="50619-126">巩固 Git 和 GitHub 基础知识</span><span class="sxs-lookup"><span data-stu-id="50619-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="50619-127">开始编写代码</span><span class="sxs-lookup"><span data-stu-id="50619-127">Get started writing docs</span></span>

<span data-ttu-id="50619-128">可以通过两种方法来参与文档更改：</span><span class="sxs-lookup"><span data-stu-id="50619-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="50619-129">快速编辑现有文档</span><span class="sxs-lookup"><span data-stu-id="50619-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="50619-130">少量更正、修正错别字或添加少量内容</span><span class="sxs-lookup"><span data-stu-id="50619-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="50619-131">文档的完整 GitHub 工作流</span><span class="sxs-lookup"><span data-stu-id="50619-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="50619-132">大篇幅更改、多个版本、添加或更改图像或撰写新文章</span><span class="sxs-lookup"><span data-stu-id="50619-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="50619-133">另外，请阅读汇总的《参与者指南》中的[撰写要领](/contribute/style-quick-start)部分。</span><span class="sxs-lookup"><span data-stu-id="50619-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="50619-134">另一个不错的资源是 [Microsoft 写作风格指南][style-guide]。</span><span class="sxs-lookup"><span data-stu-id="50619-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="50619-135">《Microsoft 写作风格指南》旨在帮助编辑人员、技术作者、开发人员、市场营销人员以及 IT 部门中的其他任何人编写更好的内容。</span><span class="sxs-lookup"><span data-stu-id="50619-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="50619-136">docs.microsoft.com [使用条款][terms-of-use]涵盖了公共存储库中对文档和代码示例所做的较小的更改和说明。</span><span class="sxs-lookup"><span data-stu-id="50619-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="50619-137">进行重大更改时，请使用完整的 GitHub 工作流。</span><span class="sxs-lookup"><span data-stu-id="50619-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="50619-138">如果你不是 Microsoft 的员工，重大更改会在拉取请求中生成一个注释，要求你提交在线[供稿许可协议 (CLA)][cla]。</span><span class="sxs-lookup"><span data-stu-id="50619-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="50619-139">你需要先填写这份在线表单，然后我们才能查看或接受拉取请求。</span><span class="sxs-lookup"><span data-stu-id="50619-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="50619-140">行为准则</span><span class="sxs-lookup"><span data-stu-id="50619-140">Code of conduct</span></span>

<span data-ttu-id="50619-141">发布到 docs.microsoft.com 的所有存储库均采用 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)或 [.NET Foundation 行为准则](https://dotnetfoundation.org/code-of-conduct)。</span><span class="sxs-lookup"><span data-stu-id="50619-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="50619-142">有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)。</span><span class="sxs-lookup"><span data-stu-id="50619-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="50619-143">后续步骤</span><span class="sxs-lookup"><span data-stu-id="50619-143">Next steps</span></span>

<span data-ttu-id="50619-144">以下文章涵盖特定于 PowerShell 文档的信息。</span><span class="sxs-lookup"><span data-stu-id="50619-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="50619-145">对于与汇总的《参与者指南》中的指南重叠之处，我们将说明这些规则对于 PowerShell 内容有何不同。</span><span class="sxs-lookup"><span data-stu-id="50619-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="50619-146">请参阅以下文档：</span><span class="sxs-lookup"><span data-stu-id="50619-146">Review the following documents:</span></span>

- [<span data-ttu-id="50619-147">如何提出问题</span><span class="sxs-lookup"><span data-stu-id="50619-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="50619-148">开始编写文档</span><span class="sxs-lookup"><span data-stu-id="50619-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="50619-149">提交拉取请求</span><span class="sxs-lookup"><span data-stu-id="50619-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="50619-150">PowerShell-Docs 风格指南</span><span class="sxs-lookup"><span data-stu-id="50619-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

<span data-ttu-id="50619-151">其他资源</span><span class="sxs-lookup"><span data-stu-id="50619-151">Additional resources</span></span>

- [<span data-ttu-id="50619-152">编辑清单</span><span class="sxs-lookup"><span data-stu-id="50619-152">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="50619-153">如何管理问题</span><span class="sxs-lookup"><span data-stu-id="50619-153">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="50619-154">如何管理拉取请求</span><span class="sxs-lookup"><span data-stu-id="50619-154">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
