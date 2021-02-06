---
title: 如何提交拉取请求
description: 本文介绍如何向 PowerShell-Docs 存储库提交拉取请求。
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "99599048"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="a80ab-103">如何提交拉取请求</span><span class="sxs-lookup"><span data-stu-id="a80ab-103">How to submit pull requests</span></span>

<span data-ttu-id="a80ab-104">若要更改内容，请从你的分支提交拉取请求 (PR)。</span><span class="sxs-lookup"><span data-stu-id="a80ab-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="a80ab-105">必须先查看拉取请求，然后才能合并该请求。</span><span class="sxs-lookup"><span data-stu-id="a80ab-105">A pull request must be reviewed before it can be merged.</span></span> <span data-ttu-id="a80ab-106">请先查看[编辑清单](editorial-checklist.md)，然后再提交拉取请求，以获得最佳结果。</span><span class="sxs-lookup"><span data-stu-id="a80ab-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="using-git-branches"></a><span data-ttu-id="a80ab-107">使用 git 分支</span><span class="sxs-lookup"><span data-stu-id="a80ab-107">Using git branches</span></span>

<span data-ttu-id="a80ab-108">PowerShell-Docs 的默认分支为 `staging` 分支。</span><span class="sxs-lookup"><span data-stu-id="a80ab-108">The default branch for PowerShell-Docs is the `staging` branch.</span></span> <span data-ttu-id="a80ab-109">在发布之前，对工作分支所做的更改将合并到 `staging` 分支中。</span><span class="sxs-lookup"><span data-stu-id="a80ab-109">Changes made in working branches are merged into the `staging` branch before then being published.</span></span> <span data-ttu-id="a80ab-110">在 `staging` `live` 太平洋时间) ，分支每个工作日的上午 (3:00 合并到分支中。</span><span class="sxs-lookup"><span data-stu-id="a80ab-110">The `staging` branch is merged into the `live` branch every weekday at 3:00 PM (Pacific Time).</span></span> <span data-ttu-id="a80ab-111">`live`分支包含发布到 docs.microsoft.com 的内容。</span><span class="sxs-lookup"><span data-stu-id="a80ab-111">The `live` branch contains the content that is published to docs.microsoft.com.</span></span>

<span data-ttu-id="a80ab-112">在开始任何更改之前，在 PowerShell-Docs 存储库的本地副本中创建工作分支。</span><span class="sxs-lookup"><span data-stu-id="a80ab-112">Before starting any changes, create a working branch in your local copy of the PowerShell-Docs repository.</span></span> <span data-ttu-id="a80ab-113">在本地工作时，请确保在创建工作分支之前同步本地存储库。</span><span class="sxs-lookup"><span data-stu-id="a80ab-113">When working locally, be sure to synchronize your local repository before creating your working branch.</span></span> <span data-ttu-id="a80ab-114">应从分支的更新到最新副本创建工作分支 `staging` 。</span><span class="sxs-lookup"><span data-stu-id="a80ab-114">The working branch should be created from an update-to-date copy of the `staging` branch.</span></span>

<span data-ttu-id="a80ab-115">所有拉取请求均应面向 `staging` 分支。</span><span class="sxs-lookup"><span data-stu-id="a80ab-115">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="a80ab-116">不要将更改提交到 `live` 分支。</span><span class="sxs-lookup"><span data-stu-id="a80ab-116">Don't submit change to the `live` branch.</span></span>
<span data-ttu-id="a80ab-117">`staging` 分支中的更改会合并到 `live`，重写对 `live` 所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="a80ab-117">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="a80ab-118">使拉取请求过程更易于所有人使用</span><span class="sxs-lookup"><span data-stu-id="a80ab-118">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="a80ab-119">PR 越简单明确，就能越快地对其进行审核和合并。</span><span class="sxs-lookup"><span data-stu-id="a80ab-119">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="a80ab-120">避免更新大量文件或包含不相关更改的拉取请求</span><span class="sxs-lookup"><span data-stu-id="a80ab-120">Avoid pull requests that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="a80ab-121">避免创建包含无关更改的 PR。</span><span class="sxs-lookup"><span data-stu-id="a80ab-121">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="a80ab-122">将对现有文章的次要更新与新文章或主要重写区分开来。</span><span class="sxs-lookup"><span data-stu-id="a80ab-122">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="a80ab-123">在单独的工作分支中处理这些更改。</span><span class="sxs-lookup"><span data-stu-id="a80ab-123">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="a80ab-124">批量更改会创建包含大量已更改文件的 PR。</span><span class="sxs-lookup"><span data-stu-id="a80ab-124">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="a80ab-125">将 PR 限制为最多 50 个已更改的文件。</span><span class="sxs-lookup"><span data-stu-id="a80ab-125">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="a80ab-126">大型 PR 难以审阅，并且更容易包含错误。</span><span class="sxs-lookup"><span data-stu-id="a80ab-126">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="a80ab-127">重命名或删除文件</span><span class="sxs-lookup"><span data-stu-id="a80ab-127">Renaming or deleting files</span></span>

<span data-ttu-id="a80ab-128">重命名或删除文件时，必须存在与 PR 相关的问题。</span><span class="sxs-lookup"><span data-stu-id="a80ab-128">When renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="a80ab-129">该问题必须探讨重命名或删除文件的必要性。</span><span class="sxs-lookup"><span data-stu-id="a80ab-129">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="a80ab-130">避免将内容添加或更改与文件重命名和删除混淆。</span><span class="sxs-lookup"><span data-stu-id="a80ab-130">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="a80ab-131">重命名或删除的任何文件都必须添加到全局重定向文件中。</span><span class="sxs-lookup"><span data-stu-id="a80ab-131">Any file that is renamed or deleted must be added to the global redirection file.</span></span> <span data-ttu-id="a80ab-132">如果可能，请更新链接到已重命名或已删除内容的任何文件，包括任何 TOC 文件。</span><span class="sxs-lookup"><span data-stu-id="a80ab-132">When possible, update any files that link to the renamed or deleted content, including any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="a80ab-133">文档 PR 验证服务</span><span class="sxs-lookup"><span data-stu-id="a80ab-133">Docs PR validation service</span></span>

<span data-ttu-id="a80ab-134">文档 PR 验证服务是用于对更改运行验证规则的 GitHub 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a80ab-134">The Docs PR validation service is a GitHub app that runs validation rules on your changes.</span></span> <span data-ttu-id="a80ab-135">您必须修复验证服务报告的任何错误或警告。</span><span class="sxs-lookup"><span data-stu-id="a80ab-135">You must fix any errors or warnings reported by the validation service.</span></span>

<span data-ttu-id="a80ab-136">你将看到以下行为：</span><span class="sxs-lookup"><span data-stu-id="a80ab-136">You'll see the following behavior:</span></span>

1. <span data-ttu-id="a80ab-137">提交 PR。</span><span class="sxs-lookup"><span data-stu-id="a80ab-137">You submit a PR.</span></span>
1. <span data-ttu-id="a80ab-138">指示 PR 状态的 GitHub 备注将显示以下状态：存储库已启用“检查”。</span><span class="sxs-lookup"><span data-stu-id="a80ab-138">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="a80ab-139">在此示例中，启用了两个检查（"提交验证" 和 ".Openpublishing.publish.config.json"）：</span><span class="sxs-lookup"><span data-stu-id="a80ab-139">In this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![验证状态 - 一些检查失败](media/pull-requests/validation-failed.png)

   <span data-ttu-id="a80ab-141">即使提交验证失败，生成也可以过关。</span><span class="sxs-lookup"><span data-stu-id="a80ab-141">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="a80ab-142">有关更多信息，请单击“详细信息”  。</span><span class="sxs-lookup"><span data-stu-id="a80ab-142">Click **Details** for more information.</span></span>
1. <span data-ttu-id="a80ab-143">“详细信息”页将显示所有已失败的验证检查，并包含关于如何解决问题的信息。</span><span class="sxs-lookup"><span data-stu-id="a80ab-143">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="a80ab-144">验证成功后，会将以下注释会添加到 PR：</span><span class="sxs-lookup"><span data-stu-id="a80ab-144">When validation succeeds, the following comment is added to the PR:</span></span>

   ![验证状态：成功](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="a80ab-146">若你是外部（非 Microsoft 员工）参与者，则无权访问详细的生成报告或预览链接。</span><span class="sxs-lookup"><span data-stu-id="a80ab-146">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="a80ab-147">查看 PR 时，系统可能会要求你进行更改或修复验证警告消息。</span><span class="sxs-lookup"><span data-stu-id="a80ab-147">When the PR is reviewed, you may be asked to make changes or fix validation warning messages.</span></span> <span data-ttu-id="a80ab-148">PowerShell-Docs 团队可以帮助你了解验证错误和编辑要求。</span><span class="sxs-lookup"><span data-stu-id="a80ab-148">The PowerShell-Docs team can help you understand validation errors and editorial requirements.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a80ab-149">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a80ab-149">Next steps</span></span>

[<span data-ttu-id="a80ab-150">PowerShell-Docs 风格指南</span><span class="sxs-lookup"><span data-stu-id="a80ab-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="a80ab-151">其他资源</span><span class="sxs-lookup"><span data-stu-id="a80ab-151">Additional resources</span></span>

[<span data-ttu-id="a80ab-152">如何管理拉取请求</span><span class="sxs-lookup"><span data-stu-id="a80ab-152">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
