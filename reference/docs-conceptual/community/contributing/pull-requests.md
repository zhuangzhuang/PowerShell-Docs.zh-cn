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
# <a name="how-to-submit-pull-requests"></a>如何提交拉取请求

若要更改内容，请从你的分支提交拉取请求 (PR)。 必须先查看拉取请求，然后才能合并该请求。 请先查看[编辑清单](editorial-checklist.md)，然后再提交拉取请求，以获得最佳结果。

## <a name="using-git-branches"></a>使用 git 分支

PowerShell-Docs 的默认分支为 `staging` 分支。 在发布之前，对工作分支所做的更改将合并到 `staging` 分支中。 在 `staging` `live` 太平洋时间) ，分支每个工作日的上午 (3:00 合并到分支中。 `live`分支包含发布到 docs.microsoft.com 的内容。

在开始任何更改之前，在 PowerShell-Docs 存储库的本地副本中创建工作分支。 在本地工作时，请确保在创建工作分支之前同步本地存储库。 应从分支的更新到最新副本创建工作分支 `staging` 。

所有拉取请求均应面向 `staging` 分支。 不要将更改提交到 `live` 分支。
`staging` 分支中的更改会合并到 `live`，重写对 `live` 所做的任何更改。

## <a name="make-the-pull-request-process-work-better-for-everyone"></a>使拉取请求过程更易于所有人使用

PR 越简单明确，就能越快地对其进行审核和合并。

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a>避免更新大量文件或包含不相关更改的拉取请求

避免创建包含无关更改的 PR。 将对现有文章的次要更新与新文章或主要重写区分开来。 在单独的工作分支中处理这些更改。

批量更改会创建包含大量已更改文件的 PR。 将 PR 限制为最多 50 个已更改的文件。 大型 PR 难以审阅，并且更容易包含错误。

### <a name="renaming-or-deleting-files"></a>重命名或删除文件

重命名或删除文件时，必须存在与 PR 相关的问题。 该问题必须探讨重命名或删除文件的必要性。

避免将内容添加或更改与文件重命名和删除混淆。 重命名或删除的任何文件都必须添加到全局重定向文件中。 如果可能，请更新链接到已重命名或已删除内容的任何文件，包括任何 TOC 文件。

## <a name="docs-pr-validation-service"></a>文档 PR 验证服务

文档 PR 验证服务是用于对更改运行验证规则的 GitHub 应用程序。 您必须修复验证服务报告的任何错误或警告。

你将看到以下行为：

1. 提交 PR。
1. 指示 PR 状态的 GitHub 备注将显示以下状态：存储库已启用“检查”。 在此示例中，启用了两个检查（"提交验证" 和 ".Openpublishing.publish.config.json"）：

   ![验证状态 - 一些检查失败](media/pull-requests/validation-failed.png)

   即使提交验证失败，生成也可以过关。

1. 有关更多信息，请单击“详细信息”  。
1. “详细信息”页将显示所有已失败的验证检查，并包含关于如何解决问题的信息。
1. 验证成功后，会将以下注释会添加到 PR：

   ![验证状态：成功](media/pull-requests/build-validation.png)

> [!NOTE]
> 若你是外部（非 Microsoft 员工）参与者，则无权访问详细的生成报告或预览链接。

查看 PR 时，系统可能会要求你进行更改或修复验证警告消息。 PowerShell-Docs 团队可以帮助你了解验证错误和编辑要求。

## <a name="next-steps"></a>后续步骤

[PowerShell-Docs 风格指南](powershell-style-guide.md)

## <a name="additional-resources"></a>其他资源

[如何管理拉取请求](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
