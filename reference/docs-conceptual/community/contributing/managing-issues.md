---
title: 如何管理问题
description: 本文介绍 PowerShell-Docs 团队如何管理问题。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597429"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="27148-103">如何管理问题</span><span class="sxs-lookup"><span data-stu-id="27148-103">How we manage issues</span></span>

<span data-ttu-id="27148-104">本文记录了如何管理 PowerShell-Docs 存储库中的问题。</span><span class="sxs-lookup"><span data-stu-id="27148-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="27148-105">本文旨在为 PowerShell-Docs 团队成员提供帮助。</span><span class="sxs-lookup"><span data-stu-id="27148-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="27148-106">它在此处发布，为公共参与者提供流程透明性。</span><span class="sxs-lookup"><span data-stu-id="27148-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="27148-107">问题源</span><span class="sxs-lookup"><span data-stu-id="27148-107">Sources of issues</span></span>

- <span data-ttu-id="27148-108">社区参与者</span><span class="sxs-lookup"><span data-stu-id="27148-108">Community contributors</span></span>
- <span data-ttu-id="27148-109">内部参与者</span><span class="sxs-lookup"><span data-stu-id="27148-109">Internal contributors</span></span>
- <span data-ttu-id="27148-110">来自社交媒体渠道的注释转录</span><span class="sxs-lookup"><span data-stu-id="27148-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="27148-111">通过 Docs 反馈窗体提供的反馈</span><span class="sxs-lookup"><span data-stu-id="27148-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="27148-112">响应时间目标</span><span class="sxs-lookup"><span data-stu-id="27148-112">Response time targets</span></span>

<span data-ttu-id="27148-113">80% 的新问题将在3个工作日内结束。</span><span class="sxs-lookup"><span data-stu-id="27148-113">80% of new issues are closed within 3 business days.</span></span>

- <span data-ttu-id="27148-114">已会审-1 个工作日内</span><span class="sxs-lookup"><span data-stu-id="27148-114">Triaged - 1 business days</span></span>
- <span data-ttu-id="27148-115">修复或更改-10 个工作日内</span><span class="sxs-lookup"><span data-stu-id="27148-115">Fix or change - 10 business days</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="27148-116">标记和里程碑</span><span class="sxs-lookup"><span data-stu-id="27148-116">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="27148-117">标签类型</span><span class="sxs-lookup"><span data-stu-id="27148-117">Label Types</span></span>

|   <span data-ttu-id="27148-118">类型</span><span class="sxs-lookup"><span data-stu-id="27148-118">Type</span></span>   | <span data-ttu-id="27148-119">说明</span><span class="sxs-lookup"><span data-stu-id="27148-119">Description</span></span>                                                         |
| -------- | ------------------------------------------------------------------- |
| <span data-ttu-id="27148-120">区域</span><span class="sxs-lookup"><span data-stu-id="27148-120">Area</span></span>     | <span data-ttu-id="27148-121">用于指示问题正在讨论哪个部分的 PowerShell 或文档。</span><span class="sxs-lookup"><span data-stu-id="27148-121">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="27148-122">有助于功能所有者查找其功能的问题。</span><span class="sxs-lookup"><span data-stu-id="27148-122">Useful for feature owners to find issues for their feature.</span></span> |
| <span data-ttu-id="27148-123">问题</span><span class="sxs-lookup"><span data-stu-id="27148-123">Issue</span></span>    | <span data-ttu-id="27148-124">指示问题的类型</span><span class="sxs-lookup"><span data-stu-id="27148-124">Indicates the type of issue</span></span>                                         |
| <span data-ttu-id="27148-125">优先级</span><span class="sxs-lookup"><span data-stu-id="27148-125">Priority</span></span> | <span data-ttu-id="27148-126">指示问题的优先级。</span><span class="sxs-lookup"><span data-stu-id="27148-126">Indicates the priority of the issue.</span></span> <span data-ttu-id="27148-127">值范围 0 (高) -4 (低) </span><span class="sxs-lookup"><span data-stu-id="27148-127">Value range 0 (high) -4 (low)</span></span>  |
| <span data-ttu-id="27148-128">状态</span><span class="sxs-lookup"><span data-stu-id="27148-128">Status</span></span>   | <span data-ttu-id="27148-129">指示工作项的状态或它的关闭原因</span><span class="sxs-lookup"><span data-stu-id="27148-129">Indicates the status of the work item or why it was closed</span></span>          |
| <span data-ttu-id="27148-130">标记</span><span class="sxs-lookup"><span data-stu-id="27148-130">Tag</span></span>      | <span data-ttu-id="27148-131">用于附加分类的标签</span><span class="sxs-lookup"><span data-stu-id="27148-131">Labels used to for additional classification</span></span>                        |
| <span data-ttu-id="27148-132">等待</span><span class="sxs-lookup"><span data-stu-id="27148-132">Waiting</span></span>  | <span data-ttu-id="27148-133">指示我们正在等待某人或某个其他事件</span><span class="sxs-lookup"><span data-stu-id="27148-133">Indicates that we're waiting on someone or some other event</span></span>         |

#### <a name="milestones"></a><span data-ttu-id="27148-134">里程碑</span><span class="sxs-lookup"><span data-stu-id="27148-134">Milestones</span></span>

<span data-ttu-id="27148-135">应使用相应的里程碑标记的问题和 PR。</span><span class="sxs-lookup"><span data-stu-id="27148-135">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="27148-136">如果此问题不适用于特定版本，则不会使用里程碑。</span><span class="sxs-lookup"><span data-stu-id="27148-136">If the issue doesn't apply to a specific version, then no milestone is used.</span></span> <span data-ttu-id="27148-137">应将尚未合并到 PowerShell 代码库中的更改的 Pr 和相关问题分配给 **未来** 里程碑。</span><span class="sxs-lookup"><span data-stu-id="27148-137">PRs and related issues for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="27148-138">合并代码更改后，将里程碑更改为相应的版本。</span><span class="sxs-lookup"><span data-stu-id="27148-138">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="27148-139">里程碑</span><span class="sxs-lookup"><span data-stu-id="27148-139">Milestone</span></span>     |                    <span data-ttu-id="27148-140">说明</span><span class="sxs-lookup"><span data-stu-id="27148-140">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="27148-141">7.0.0</span><span class="sxs-lookup"><span data-stu-id="27148-141">7.0.0</span></span>            | <span data-ttu-id="27148-142">与 PowerShell 7.0 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="27148-142">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="27148-143">7.1.0</span><span class="sxs-lookup"><span data-stu-id="27148-143">7.1.0</span></span>            | <span data-ttu-id="27148-144">与 PowerShell 7.1 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="27148-144">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="27148-145">7.2.0</span><span class="sxs-lookup"><span data-stu-id="27148-145">7.2.0</span></span>            | <span data-ttu-id="27148-146">与 PowerShell 7.2 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="27148-146">Work items related to PowerShell 7.2</span></span>               |
| <span data-ttu-id="27148-147">未来</span><span class="sxs-lookup"><span data-stu-id="27148-147">Future</span></span>           | <span data-ttu-id="27148-148">工作项 PowerShell 的未来版本</span><span class="sxs-lookup"><span data-stu-id="27148-148">Work items a future version of PowerShell</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="27148-149">会审过程</span><span class="sxs-lookup"><span data-stu-id="27148-149">Triage process</span></span>

<span data-ttu-id="27148-150">PowerShell 文档团队成员每天查看问题，并在遇到新问题时对其进行会审。</span><span class="sxs-lookup"><span data-stu-id="27148-150">PowerShell docs team members review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="27148-151">团队每周都要讨论需要会审或保持未解决的问题。</span><span class="sxs-lookup"><span data-stu-id="27148-151">The team meets weekly to discuss issues that need triage or remain unresolved.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="27148-152">错放的产品反馈</span><span class="sxs-lookup"><span data-stu-id="27148-152">Misplaced product feedback</span></span>

- <span data-ttu-id="27148-153">输入将客户重定向到正确反馈通道的注释。</span><span class="sxs-lookup"><span data-stu-id="27148-153">Enter a comment redirecting the customer to the correct feedback channel.</span></span>
- <span data-ttu-id="27148-154">可选：将问题复制到相应的产品反馈位置，将链接添加到复制的项，并关闭问题。</span><span class="sxs-lookup"><span data-stu-id="27148-154">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="27148-155">请勿将问题复制到 UserVoice。</span><span class="sxs-lookup"><span data-stu-id="27148-155">DO NOT copy issues to UserVoice.</span></span>

  <span data-ttu-id="27148-156">PowerShell 问题的默认位置是 [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="27148-156">The default location for PowerShell issues is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

  <span data-ttu-id="27148-157">以下主题区域对于问题有不同的位置：</span><span class="sxs-lookup"><span data-stu-id="27148-157">The following subject areas have different locations for issues:</span></span>

  | <span data-ttu-id="27148-158">主题</span><span class="sxs-lookup"><span data-stu-id="27148-158">Subjects</span></span> |                                                     <span data-ttu-id="27148-159">产品反馈 URL</span><span class="sxs-lookup"><span data-stu-id="27148-159">Product Feedback URL</span></span>                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | <span data-ttu-id="27148-160">dsc</span><span class="sxs-lookup"><span data-stu-id="27148-160">dsc</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | <span data-ttu-id="27148-161">库</span><span class="sxs-lookup"><span data-stu-id="27148-161">gallery</span></span>  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | <span data-ttu-id="27148-162">jea</span><span class="sxs-lookup"><span data-stu-id="27148-162">jea</span></span>      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | <span data-ttu-id="27148-163">wmf</span><span class="sxs-lookup"><span data-stu-id="27148-163">wmf</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a><span data-ttu-id="27148-164">支持请求</span><span class="sxs-lookup"><span data-stu-id="27148-164">Support requests</span></span>

- <span data-ttu-id="27148-165">如果支持问题很简单，请礼貌答复并关闭问题。</span><span class="sxs-lookup"><span data-stu-id="27148-165">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="27148-166">如果问题较为复杂，或者提交者回复了更多问题，请将这些问题重定向到论坛和支持渠道。</span><span class="sxs-lookup"><span data-stu-id="27148-166">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="27148-167">用于重定向到论坛的建议文本：</span><span class="sxs-lookup"><span data-stu-id="27148-167">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="27148-168">行为准则冲突</span><span class="sxs-lookup"><span data-stu-id="27148-168">Code of conduct violations</span></span>

- <span data-ttu-id="27148-169">编辑问题以删除任何冒犯性内容（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="27148-169">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="27148-170">输入一条注释，指示此问题是垃圾邮件，关闭问题，然后将其锁定以防止进一步注释。</span><span class="sxs-lookup"><span data-stu-id="27148-170">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="27148-171">每周的会审中都应该讨论每个冲突，以确定需要进一步操作 (向 GitHub 或 Microsoft 合法) 报告。</span><span class="sxs-lookup"><span data-stu-id="27148-171">Each violation should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
